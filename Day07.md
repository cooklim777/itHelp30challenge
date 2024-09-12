Day07 探索 Make 自動化 的介面

終於來到製作正題了，當然我認為前幾天的自動化知識其實非常重要，很多自動化不一定是要學好這個工具，而是要從生活、工作中，自己的流程去思考，到底該如何改善、加速，而不是整天被這些事情追著跑，沒時間停下來優化，而事情越來越多更沒辦法停下來，導致越來越惡化，讓自己的時間都花在這些比較沒有產出的事情。

首先到 make 頁面點擊右上角的「+ Create a new scenario」
進到場景的頁面中

![https://ithelp.ithome.com.tw/upload/images/20240911/20169163gubtb9KF0U.png](https://ithelp.ithome.com.tw/upload/images/20240911/20169163gubtb9KF0U.png)

首先看到中間有很多模組可以選擇，例如 LINE、HTTP、SLACK 等等，就是 make 已經串接好的雲端服務，而首先我們要先說 trigger 觸發的部分。

一個場景中只會有一個觸發的條件，那這個條件可以設置很多種，主要有以下
在 Make 中，**觸發器（Triggers）** 是啟動 Scenario（場景）的關鍵元素。觸發器監控指定的應用程式或服務中的某些事件，一旦這些事件發生，觸發器就會自動啟動 Scenario，開始執行預設的操作。以下是 Make 中各種類型觸發器的介紹。

**常見的觸發器類型**

1. **資料變更觸發器**

   - **用途**：當某個應用程式中的資料發生變更時啟動。例如，新增、修改或刪除某個資料項目時觸發。
   - **應用情境**：可以用於監控 CRM 系統中的客戶資料變更，並將更新信息同步到其他系統中。
     - **Google Sheets**：當 Google Sheets 表格中的一行被更新或添加時觸發。
     - **Airtable**：當 Airtable 庫中的一條記錄發生變更時觸發。

2. **時間觸發器**

   - **用途**：基於時間的觸發器，按照設定的時間間隔或特定時間點自動執行，通常不會調非常快的時間就觸發（例如 15 分鐘觸發一次），因為這樣是非常耗 operations 的。
   - **應用情境**：定時執行的任務，例如每天早上自動發送報表，或每小時備份資料。

3. **事件觸發器**

   - **用途**：當某個應用程式中發生特定事件時觸發 Scenario。
   - **應用情境**：當有新郵件、網站表單提交或社交媒體上有新提及時，立即觸發後續動作。例如收到新的特定郵件，或是 Google form 有人填入時。

4. **Webhook 觸發器**
   - **用途**：通過 Webhook 來即時觸發 Scenario。當一個 Webhook 被外部系統調用時，Scenario 會立即啟動。
   - **應用情境**：適合於即時監控或需要與第三方系統實現即時聯動的情境（跟其他的場景連用）。

觸發器是 Make 自動化流程的起點，通過選擇合適的觸發器，靈活地設計各種自動化流程，從即時響應事件到定期執行任務。而這些觸發器也都是個 module。

有了這些觸發當起始點，觸發就就會接續做下一個事情，如下圖
![https://ithelp.ithome.com.tw/upload/images/20240912/201691630RRVyCjYPC.png](https://ithelp.ithome.com.tw/upload/images/20240912/201691630RRVyCjYPC.png)
這個觸發器是 Line，當某個帳號收到訊息時會將得到這些訊息，並且做篩選的動作，看是要走上方還是下方的流程，接下來這些訊息就會進到 GPT 中，來做一些分析，最後回傳給使用者。
而下方的流程可以看到有 google calender，其實就是直接使用賴訊息，幫助建立行事曆，這之後也會教大家如何製作，類似 AI agent 的功能。

同一個模組也可以使用不同的觸發器，以 google sheet 為例，可以看到 Google sheet 模組內有非常多的方法可以取用，包括 sheet、row、cell 相關，每一個都是可以當開頭的（都可以時間觸發、一次觸發等），可以當你點擊觸發時就要新增一個 sheet 也是可以 但就是比較奇怪。通常會當觸發的就是我圈起來的兩個，一個是讀取資料，而一個是觀察資料，當資料有改變時就會被觸發，啟動這個場景。
![https://ithelp.ithome.com.tw/upload/images/20240912/20169163KnWfvkNkRX.png](https://ithelp.ithome.com.tw/upload/images/20240912/20169163KnWfvkNkRX.png)

觸發器就是初始模組的左下角的圖示，裡面也有許多可以選擇，而最常使用的會是 immediate，配合著如上面說的觀察資料，當資料有改變時就會馬上觸發。接下來應該就是使用時間排程，固定每天或幾小時觸發你的場景。再來就是需要時才會手動觸發，就是 on demand 的部分。

![https://ithelp.ithome.com.tw/upload/images/20240912/20169163LW8XP1ZN8f.png](https://ithelp.ithome.com.tw/upload/images/20240912/20169163LW8XP1ZN8f.png)

這就是我們場景中的起點，到底要怎麼設置，明天接續下去。

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
