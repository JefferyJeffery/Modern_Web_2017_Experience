[⬅ Modern Web 2017](https://hackmd.io/KwFgRsAMAcCMCmBaaA2AnAJkeFlEEMMMBmZdAMzDRTHMkliA?view)
# Zookeeper多活實踐 (High Availability)

###### tags: `ModernWeb2017`

[投影片](http://s.itho.me/modernweb/2017/day2/201-2-%E8%B6%99%E5%AD%90%E6%98%8E.pdf)

## 餓了麼簡介
- 餐飲配送
- client
    - 2.6E

## zookeeper簡介
- Apache ZooKeeper is an effort to develop and maintain an open-source server which enables highly reliable distributed coordination.
- based on zab protocal (simplified paxos protocol)

高可靠的分散式協調服務，為分布式而生，使用zab協議（改進版/簡化版的paxos協議）
使用場景：數據發布訂閱（配置管理），命名服務


![](https://zookeeper.apache.org/doc/trunk/images/zkservice.jpg)

### 使用投票機制決定是否發送服務 - Quroum
1. 註冊服務信息
2. 獲取服務註冊信息，監聽變化
3. 調用服務
4. 變更通知

異地多機房數據分片+按POI做流量分發，隨時可容災切換

- 數據：多寫+實時雙向複製
- 流量：按POI做流量分發+可全局切換
- 服務：每個機房提供完整交易服務鏈路，機房內調用閉環

萬台服務器，千個工程師

## 多活下的挑戰
- API Gateway做routing (based on client location)
- 不同機房sync data(讀寫分離)
    - 一個機房寫shard1，另一個寫shard2...etc
    
## 多活下的服務調用
- 任何一個機房出問題，其他機房內的zookeeper都可以調用
- 正常情況下可以跨機房調用

## 方案&組件簡介

常用部署方案
1. 主機房voter 其他機房observer
   - 寫延遲適中
   - observer機器讀延時大
   - **[致命的問題]voter鎖在機房有問題，其他機房zookeeper都不可用**
   - 被挖掘機挖斷網路
2. 多voter部署方案
   - **一個機房有問題，其他兩個機房超過一半機器連接，機器可用**
   - 寫延遲很大
   - 個別機房讀延遲大
- ※voter需要大多數機械投票才可完成

## zookeeper多活方案
- 多機房獨立集群

## 組件簡介
### publisher
- 在zookeeper observer基礎上擴展

### replicator
- 消費消息+寫入zookeeper
- 可訂閱多個topic
- 只寫到固定機器上
- 目標zookeeper需要配置超級權限

### MQ
- 和publisher同機房部署，跨機房sub
- 選運維同學熟悉的mq
- 支持持久化

### [組件第一大難點] 循環複製
在DB1新增一個訊息，會被同步到DB2，對DB2來說，是一筆新的訊息，因此又被同步新增到DB1，如此一般就像迴圈一樣，不停地互相新增
**根據sessionid中的機器號區分內外數據**
其他機房寫入過濾掉
本機房寫入則存入

### [組件第二大難點] 事務連續性

超過500條，觸發leader -> publish之間內存鏡像，會丟失中間訊息！

## 維運技巧
- 連接串Domain > IP (切換方便)
- 最多5個節點，擴充用observer
  - 越多越慢，太少又不太夠用
- 無影響集群擴充：一台台增加myid高於voter集群的observer

客戶端不重啟切集群方案
※避免線上成千上萬個應用重啟
用HAProxy
新集群事務ID > 舊集群事務ID (將服務導向新集群，並保證新集群ID比舊集群ID大？)

http://www.evernote.com/l/AOTLrcnAXMtGY6QV125lCMsSf5C1rruld0E/
