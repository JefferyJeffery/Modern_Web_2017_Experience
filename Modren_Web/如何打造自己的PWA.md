[⬅ Modern Web 2017](https://hackmd.io/KwFgRsAMAcCMCmBaaA2AnAJkeFlEEMMMBmZdAMzDRTHMkliA?view)
# 如何打造自己的PWA

﹣ 演讲稿：[如何打造自己的 PWA](https://ppt.baomitu.com/d/25ac95be)

###### tags: `ModernWeb2017`

## PWA

打造媲美原生應用的 app

serviceWorker
  - 常駐在背景

cacheStorage
  - request / response
  - stream

## 如何打造自己的 PWA

离线应用需求

- serviceWorker
    - 事件驅動式腳本
    - Working Draft
    - 可離線
    - 可緩存加速
    - 
- appCache：
    - 应用不能主动移除缓存
    - 不支持跨域

- 步驟：
    - 註冊serviceWorker
    - 攔截請求
    - 有網時緩存響應
    - 無網時返回緩存

優化代碼：

﹣ 只緩存請求成功的響應
﹣ 使用 online/offline 事件當有網路的時候傳送數據
﹣ backgroundSync 允許代碼在後台同步數據

離線操作後的數據如何上傳：
- 使用online/offline事件
- 每次打開頁面的時候上傳最新數據
- 嘗試使用可靠的的傳輸方式 backgroundSync

Service Worker 無法訪問 localStorage，只能訪問 indexedDB 和 cacheStorage。

**backgroundSync !== request** 
這個生命週期裡面可以做非常多的事情


兩步驟讓你的 web app 更靠譜
- 離線可用
- backgroundSync 上傳檔案


使用 cache 來做頁面性能優化，加速頁面。

瀏覽器四層緩存：
- memory cache（當前會話期有效）
- serviceWorker cache（可以手動更新緩存）
- http cache（可能存在的問題，是否強制清除了？）
- push cache

第一次加速：
- JS 預存：
    - 線程佔用
    - 緩存時間的問題
﹣ precache：
    - dns-prefetch
    - preconnect
    - prefetch
    - prerender
    - preload
    
ServiceWorker 緩存存儲空間：1G 多



























