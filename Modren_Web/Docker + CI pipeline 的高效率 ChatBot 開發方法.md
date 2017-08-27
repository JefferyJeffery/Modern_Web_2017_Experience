[⬅ Modern Web 2017](https://hackmd.io/KwFgRsAMAcCMCmBaaA2AnAJkeFlEEMMMBmZdAMzDRTHMkliA?view)
# Docker + CI pipeline 的高效率 ChatBot 開發方法

###### tags: `ModernWeb2017`

:::info
:mega: 投影片
[Docker \+ CI pipeline 的高效率 ChatBot 開發方法](https://www.slideshare.net/philipzh/docker-ci-pipeline-chatbot)
:::

### IM+XMPP
[TradingBot](https://www.facebook.com/tradingbot/)

### ChatBot功能
1. 自動交易現況
2. 選擇權策略
3. 金融新聞
4. 商品資訊
5. 每日未平倉量
6. 到價警示(個人化服務)
7. 金融知識問答測試
8. 訂閱服務
9. 託播廣告

### Bot Framework
[Microsoft Bot Framework](https://dev.botframework.com/)
[Microsoft Bot Framework Emulator](https://github.com/Microsoft/BotFramework-Emulator)
[Microsoft Bot Builder SDK](https://docs.microsoft.com/en-us/bot-framework/resources-tools-downloads)
* Bot development tool
* Bot connector
    * Connect bot and third party API
* Bot directory

![](https://f.ch9.ms/wlwimages/ae054c0b4d7b402ab1239e6800c0220f/image%5B6%5D-121.png)

### 利用微軟相關工具

* 整合自動化測試部署流程 - GitLab (GitLab CI和jenkins是一樣的東西)

* Gitlab 也內建了 Container Registry - [GitLab Container Registry administration \- GitLab Documentation](https://docs.gitlab.com/ce/administration/container_registry.html)


### 容器思維

1. 各<span style="color:red;">**階段**</span>如何使用容器
2. <span style="color:red;">**直接**</span>用容器，不再重頭安裝
3. <span style="color:red;">**官方**</span>映像檔或依需要客製
4. <span style="color:red;">**營運**</span>環境亦使用容器
5. 在<span style="color:red;">**易用性**</span>與<span style="color:red;">**尺寸**</span>取得平衡
6. 使用<span style="color:red;">**標籤**</span>(tag)區分版本
7. 擺脫程式語言的<span style="color:red;">**限制**</span>，善用各語言優點


