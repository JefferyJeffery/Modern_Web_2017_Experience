[⬅ Modern Web 2017](https://hackmd.io/KwFgRsAMAcCMCmBaaA2AnAJkeFlEEMMMBmZdAMzDRTHMkliA?view)
# Angular 4 網站開發最佳實務

###### tags: `ModernWeb2017`

### 保哥出品 - vscode 套件
- angular extension pack
https://github.com/doggy8088/angular-extension-pack


### VSCode Windows 快速鍵
- `Alt` + `o` (快速切換元件與範本之間)
- `F12` (移至定義)(可在範本中使用)


### 套件範例

- json-to-ts 套件的快速鍵示範：
https://marketplace.visualstudio.com/items?itemName=MariusAlchimavicius.json-to-ts

- document this(快速鍵：Ctrl + Alt + D，Ctrl和Alt不放再按一次D)
https://marketplace.visualstudio.com/items?itemName=joelday.docthis

- angular style guide
https://angular.io/guide/styleguide

- source-map-explorer: 可看被webpack合併後的js內容
https://github.com/danvk/source-map-explorer
[source-map-explorer的npm安裝方法](https://www.npmjs.com/package/source-map-explorer)


----

### Angular 應用程式狀態

狀態變更原因

- 非同步操作 (async) -> 事件(click...)、HTTPRequest、timer
- 每當非同步操作完成，都會發生變更



- ChangeDectionStrategy.Default
    - 變更偵測在每一次非同步操作變更後執行
- ChangeDectionStrategy.OnPush
    - 變更偵測在非同步操作變更屬性後執行

### 演講簡報

* [Angular 4 網站開發最佳實務](https://www.slideshare.net/WillHuangTW/angular-4-best-practics) - SlideShare