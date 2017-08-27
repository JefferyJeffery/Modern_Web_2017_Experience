[⬅ Modern Web 2017](https://hackmd.io/KwFgRsAMAcCMCmBaaA2AnAJkeFlEEMMMBmZdAMzDRTHMkliA?view)
# Snapshot Everything - 從元件測試點燃新一代測試觀念

###### tags: `ModernWeb2017`

[toc]

---
## 前端設計的舊世界

#### 為什麼要寫測試？

* 維持程式碼品質在一定的水準
* 協助開發者改善程式碼的設計
* 配合自動化流程(CI)可以提昇開發品質
* 未來對於重構程式碼有莫大的助益

#### 為什麼討厭寫測試

- 增加開發的時間成本
- 寫測試的過程既繁瑣又無聊
- 需求改變時，常需要修改測試碼
- 設計改變時，常需要修改測試碼
- 資料格式改變，常需要修改測試碼
- 需要持續維護程式碼

### 前端測試的全新革命

* Snapshot test 不只是一種測試方式
* Snapshot 不是你以為的截圖
* Snapshot 不是另一套測試工具
...


### 從人類開始懂得紀錄生活說起

為什麼人類需要紀錄回憶？
![](http://cdn.news.ebc.net.tw/images/2017/05/05/149397168373560x6eebyS1u.jpg)



### 前端測試的新世界
- 拍下每一種情境下的執行結果
- 比較這次與上次的執行結果
- pass表示與上次執行結果相同
- fail 表示與上次執行結果不同

#### Spanshot Test 運作原理

![](https://cdn-images-1.medium.com/max/1345/1*EDPrWEKqMClrMO6zia570w.png)


#### Spanshot Test 的精神

- 減少測試碼的size
- 減少寫測試的時間成本
- 降低更改測試碼的頻率
- 更有效地抓出非預期的影響
- 大幅提昇測試覆蓋率
- 前端工程師變得更快樂！！

#### 安裝

- via yarn

- via npm
```
$ npm i --save-dev jest-cli enzyme enzyme-to-json
```
> [npm install](https://www.npmjs.com/package/snap-shot)
- via react

#### 設定
- Jest 不必寫任何設定即可使用

#### 快速認識

* Assertion
```javascript
expect(shallow(<Foo />)).toMatchSnapshot()
```

- no more `toBe`, `toEq`



#### 測試覆蓋率

* 最少的測試碼，最大的覆蓋率
* 用 branches 作為有效的指標
    * 讓 branches 到達 100%

### 元件測試的竅門

- 每一次造成 re-render 的行為，都需要做一次 snapshot

- 以 branches來看覆蓋率

##  Snapshot Test 的延伸
* Reducer
* Redux-saga
* Utility


## 用 Snaptshot 做 Functional Test
- Snapshot Serializer
- 用serializer來簡化測試碼
- 自己寫一支serializer來自定snap
- 取代functional test
- 更多的可能性...

## Snapshot Everything
- 其實Snapshot Test是一種新概念
- snap 其實就是 expected values 的集合

## 從導入到全面延伸的這一年
- 大幅降低測試的成本
...


## 參考資料
- [Snapshot Testing doc](https://facebook.github.io/jest/docs/snapshot-testing.html)




