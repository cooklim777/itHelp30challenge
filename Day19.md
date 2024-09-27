Day19 Webhook

實作是最好的練習，且有概念需要實做、操作才能更了解，我這邊會提供藍圖來做下載，可以當作每天的練習，匯入並且嘗試看看效果，下載我的[藍圖](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)，匯入進去操作看看。
匯入方法 [Day09 使用藍圖](https://ithelp.ithome.com.tw/articles/10352992)

---

Webhook 是一種在特定事件發生時自動發送訊息或執行程式的機制。通常用於應用程式或服務之間的即時通訊和資料同步。當某個事件（如訂單被創建、用戶註冊等）發生時，系統可以自動向設定的網址（即 webhook URL）發送 HTTP 請求，以通知該事件的發生或傳遞相關數據。這種方式可以實現系統之間的實時互動和數據同步，常見於各種網路應用程式的整合中。

Webhook 和呼叫 API 之間的主要區別在於資料傳遞的觸發方式和時機
**Webhook（被動推送）**：
觸發方式：由事件驅動，當某個事件發生時，伺服器會主動推送資料到你預設的 URL（通常是 HTTP POST 請求）。
資料傳遞方式：自動推送，例如，當支付完成、資料更新時，Webhook 會自動通知接收端。

**API 呼叫（主動請求）**：
觸發方式：由客戶端主動發起。你必須主動向伺服器發出請求，通常是 GET 或 POST 請求，來獲取或提交資料。
資料傳遞方式：必須定期或依需求主動發送請求以獲取最新資料。
即時性：取決於你發送請求的頻率，通常需要間隔一段時間進行輪詢才能獲得更新。

在 Make 中也蠻多 Webhook 的使用，在我們之前 Line 的例子，就有 Webhook 的設置，當我們的官方帳號收到訊息，會自動傳送 API 給 Make 的 Webhook 得到訊息，其實就都是 API 的設置，但看他是被動還是主動，而被動也可能是收到訊息後被觸發再因為觸發主動傳送訊息，這也算是 Webhook。
在 Make 場景中我們的觸發方式之前有說過可以時間觸發、主動觸發，還可以信件觸發、API 觸發等功能都有，那我們就來直接嘗試看看。

可以看下圖，就是設定 Webhook，右邊是這個 Webhook 的設定，主要是要設定他的 IP 限制，這樣當有人傳送訊息到你的 Webhook 時，他還會檢查 IP，不然你的場景就會被知道你網址的人啟動。
設定好後，左方的紅色框就是你的 Webhook 網址，你只要有啟動這個流程，之後傳送這個網址，就能夠啟動該場景，也能使用 get 的方法傳送一些資料到這邊。

![https://ithelp.ithome.com.tw/upload/images/20240925/20169163PuiTkmdm78.png](https://ithelp.ithome.com.tw/upload/images/20240925/20169163PuiTkmdm78.png)

那我們在接一個 response，就簡單回一個 {"response":"Hello"}，所以只要啟動該場景，然後輸入該 URL 的時候，就會收到這個訊息，如下圖。

![https://ithelp.ithome.com.tw/upload/images/20240925/20169163dNQ3jCTtgF.png](https://ithelp.ithome.com.tw/upload/images/20240925/20169163dNQ3jCTtgF.png)

所以我們就可以利用這個方法，直接來啟動某一個場景，例如公司中做出貨的動作，出貨完畢可以直接傳送貨物資料給這個場景，然後就會自動建立 google sheet 的出貨資料，做一個整理，並且傳回去給使用者。
或是我們也能在使用其他場景時，發送 API 給這個 webhook 的場景，以免同一個場景過於複雜，或是該場景有些設置不想給其他人看，只想回覆使用者 output 資料。

那也有 mail 的 webhook，會指定某一個信箱，當信箱的主旨、內文規則符合你的設定，就會執行該場景，例如每個月會收到銀行的對帳資訊，那當收到 XXX 銀行明細，就啟動整理銀行明細的場景，直接達成自動化的效果。

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
