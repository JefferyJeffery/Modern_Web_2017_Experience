[⬅ Modern Web 2017](https://hackmd.io/KwFgRsAMAcCMCmBaaA2AnAJkeFlEEMMMBmZdAMzDRTHMkliA?view)
# 關於 Javascript 非同步的那些事兒

###### tags: `ModernWeb2017`

[投影片](https://www.facebook.com/init.kobeengineer/photos/a.1416496745064002.1073741828.1309707529076258/1469754986404844/?type=3)

---

## Javascript與非同步

### Javascript

#### 單執行緒
- 瀏覽器導向
- 避免複雜性
- 核心特徵
- Html5 web worker(:new:)

#### 非阻塞式
- 阻塞...
```javascript=
  while(true){
      console.log("run run run");
  }
  console.log("finish!");  <--never show

```

#### 非同步
- Event Loop
```javascript=
console.log('Hello');

setTimeout(function cb(){
    console.log('2017');
},2000);
console.log('ModernWeb);
```
Show Result=>
```javascript=
Hello
ModernWeb
2017
```
[Loupe](http://latentflip.com/loupe/)



## callback vs promise

##### What is callback?
- callback
    - 非同步
    - 滿足情境時觸發
    - 複雜邏輯不好維護
    - 較難處理錯誤
![Callback Hell](https://brunolm.files.wordpress.com/2017/01/hadouken-code.jpg)

##### What is promise?
- promise
    - 兼容性
    - 狀態明確
    - 可以連續執行
    - 更好閱讀

#### Run everywhere




## generator的出現 及 設計精神

### Iterator(迭代器)
- 佔記憶體空間
- 記憶體讀寫花時間
- 處理10000個物件

### Generator(產生器)
- 一次一個
- 停在上次執行之處
- 節省記憶體
- 時間暫停(類似這種概念)
- 使用yield關鍵字(表示暫時交出執行權)
- 封裝非同步任務,處理Promise
- 邏輯清楚好理解
- 讓Generator自動執行
- 回傳為Promise
- [co](https://github.com/tj/co)
  - The ultimate generator based flow-control goodness for nodejs (supports thunks, promises, etc)

```js
function* GetDataList(){
    var i=0;
    
    while(i<100){
        yield i;    //使用時回傳ref,then stop and wait next()
        i++;
    }
}

var dataList = GetDataList();
console.log(dataList.next().value);   //0
console.log(dataList.next().value);   //1
console.log(dataList.next().value);   //2
```

```js
co(function* () {   // co 是 co-library， 會自己去處理戳generator的事情，而不需要自己去用next()
    const a = yield request('api.com/a');
    const b = yield request('api.com/b');
    
    console.log(a);
    console.log(b);
})
.then(
    () => console.log('success'), 
    (err) => console.log(err)
)
```

## 使用async與await會讓非同步程式更簡潔

### async / await
- 結合Promise與Generator
- 不需要第三方套件
- 非同步程式同步化
- 直覺化的邏輯思考
- ES7,TypeScript支援
- async - 標註在function前面
- await - 標註在promise前面
- 一定要用function包裝
- 回傳為Promise類型


```js
async function Main(){
    const a = await request('api.com/a');
    const b = await request('api.com/b');
    
    console.log(a);
    console.log(b);
}
```

## 演進

![Homersapien](https://vignette3.wikia.nocookie.net/simpsons/images/5/53/Homersapien.jpg/revision/latest?cb=20111213145916)
![Too busy to improve?](https://pbs.twimg.com/media/CqOpbQBWcAA7Urg.jpg)

## 總結
- 善用非同步
- 學習新寫法
- 理解運作機制
- 節省開發時間
- 做一個努力的司機 (工程師)



jobs.kktix.cc

投影片裡的連結(網上找的)
* [Philip Roberts: Help, I’m stuck in an event-loop.](https://www.youtube.com/watch?v=8aGhZQkoFbQ)
* [JavaScript 運行機制詳解：再談Event Loop](http://www.ruanyifeng.com/blog/2014/10/event-loop.html)
* [Going Async With ES6 Generators](https://davidwalsh.name/async-generators)
* [JavaScript 非同步程式革命－async、await 與TypeScript 2.1 - 黑暗執行緒](http://blog.darkthread.net/post-2016-12-23-typescript-async-await.aspx)