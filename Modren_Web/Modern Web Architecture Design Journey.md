[⬅ Modern Web 2017](https://hackmd.io/KwFgRsAMAcCMCmBaaA2AnAJkeFlEEMMMBmZdAMzDRTHMkliA?view)
# Modern Web Architecture Design Journey

###### tags: `ModernWeb2017`

## 技術選型: 通常是關鍵人物定的偏好 CTO or 架構師
有時解決問題的人，是提出問題的人

架構與公司文化、與組織有關係

說服藝術 
- 偶爾任性是可愛，常常任性是妖孽
- 沒有完美的架構，只有最適的架構


You are **not** Google Facebook Amazon: 要思考自己的公司資源到底是不適合大公司的玩法
> 你只是個玩具!!
> [name=Lego]

Good architecture brings Agility 好的架構帶來敏捷

Minimum Viable Product(MVP)最小可行性產品

$$
\mathrm{Error} = (\mathrm{more\ code})^2
$$

最後廢碼定理
> 愈接近專案死期，產生的廢碼會愈多

Conceptual Integrity (概念完整性)
降低每個人的概念落差

> 知道是借的才是技術債，否則只是你寫的爛code!
> [name=somebody]

## 技術債
- 需求的坑
- 設計的坑
- 程式的坑

### 需求坑

- 需求永遠是不明確，但我們能做的是讓架構更具彈性

依賴反轉原則(除了需求方給開發方需求，開發方反過來主動給需求方建議)

> 使用者不知道自己要什麼
> [name=賈柏斯]

- 預想但不過早調優

*Premature optimization is the root of all evil.
Do some { Architectural optimizations, Algorithms, ...} early.*

手拿菜刀砍電線、一路火花帶閃電

#### Elastic business

- 工程師就是要把需求抽象化(e.g. 量化)
    - e.g. 受眾在**M**時間內不要看到**N**則廣告

### 設計坑

設計是 權衡需求與實踐的藝術

> 名言：最慘的不是瓶頸，而是瓶頸之後還有瓶蓋

### 程式坑

### Workload
千萬人同時在線

低延遲回應

- 廣告: 30ms
- 高頻交易: 0.5~3ms
- 遊戲:
    - 30fps: 100~150ms
    - 60fps: 60~70ms

Scale-out(加機器，可增加through-put) 會增加 latency
（Scale-out 解決的是 through-put 的問題，而不會解決 latency 的問題）

- Monolithic
    - eg: Rails, Laravel, Django...
- Micro service
- Nanoservice
- SOA
- picoservice

> 有沒有能力駕馭微服務？奈米服務、微微服務？

#### MonolithFirst
> 單體 優先的技術選型
> [name=martin fowler Thoughtworks]

Thoughtworks: 顧問公司

- 幾乎所有成功的為服務案例，都是從過大的單體**拆分**的
- 幾乎所有一開始就投入微服務的都出現不小的問題
- 架構是演化來的，不是一開始就選用微服務

小公司 不建議微服務
大公司 有助於解構組織....

> 也有可能是顧問公司的盲點，成功的公司並不需要找顧問公司？（存活者偏差）

**架構促進敏捷**

- [MonolithFirst](https://martinfowler.com/bliki/MonolithFirst.html) - Martin Fowler
  - [MonolithFirst](https://news.ycombinator.com/item?id=9652893)
  - [Monolith First (2015)](https://news.ycombinator.com/item?id=14778685)
- [Towards complex adaptive architectures](https://www.slideshare.net/ufried/towards-complex-adaptive-architectures)

組織會影響架構

幾個scrum team 會決定可以拆成幾個微服務

救世主 serverless

serverless ≠ Architectureless


### Summary
- 架構先決
- 沒有完美的架構 只有適合的架構
- 架構是演進的，預想但不過早調優（從組織是什麼反推架構要是什麼）

### Sacrificial Architecture(犧牲的架構)
重構未必是失敗的事
重點是 **為什麼**, **新架構怎麼執行**, **何時執行**

簡言之，如果清楚明白**打掉重練**比較好，那就勇敢執行吧！

### Author
- Mail: yftzeng@gmail.com
- Facebook: https://www.facebook.com/yftzeng.tw
- 裝備明細: 先google過我的名字再來跟我說話
- [LOGOless \- 團體服,個性化T恤,客製化T恤,印T恤,設計自己的T\-shirt，一件T恤也能做 \- LOGOless \- 設計自己的T\-shirt，一件T恤也能做 \-先Google過我名字\-Ant](https://www.logoless.com.tw/design/m_preview_single_new4.asp?ver=4&id=33675736978154)




