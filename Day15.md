Day15 實例應用(1) - 表單自動寄信

實作是最好的練習，且有概念需要實做、操作才能更了解，我這邊會提供藍圖來做下載，可以當作每天的練習，匯入並且嘗試看看效果，下載我的[藍圖](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)，匯入進去操作看看。
匯入方法 [Day09 使用藍圖](https://ithelp.ithome.com.tw/articles/10352992)

---

今天來介紹一些實用的案例，常常在一些活動，線上上課、實體上課、展場上、一些資訊收集都會使用到表單，不管是使用 google form, Typeform 等等的表單服務，都可以使用 Make 來做自動化，若你的表單服務 Make 中目前還沒開放，通常表單也都會有 API 可以讓你做串接，而達到自動化。
那我們使用大家最簡單可以接觸到的 Google form，我建立以下的[表單](https://docs.google.com/forms/d/e/1FAIpQLSdARx4qhMlBm4uWqQMHXvFhaYbuXreDDihD9sUtbI5oDnxekQ/viewform)，當我收集表單時，我會知道該用戶是否需要收到未來有關課程的資訊，我們就能做寄信的動作。

![https://ithelp.ithome.com.tw/upload/images/20240921/20169163GJ5xAdgead.png](https://ithelp.ithome.com.tw/upload/images/20240921/20169163GJ5xAdgead.png)

在 Make 中使用 google form 模組中的 Watch Responses，當去看表單有新的填入者時，就會得到這些資訊可以看到得到的資訊有表單內的 answer，他還有關於表單的 ID 和 type 的資訊，但對我們這個流程不重要。

![https://ithelp.ithome.com.tw/upload/images/20240921/20169163eiDfaELxCg.png](https://ithelp.ithome.com.tw/upload/images/20240921/20169163eiDfaELxCg.png)

接下來我們就在 filter 設置，當未來是否想收到資訊的答案為是的時候，我們才要通過通道，做後續的動作。

![https://ithelp.ithome.com.tw/upload/images/20240921/201691632XvLVc3NiJ.png](https://ithelp.ithome.com.tw/upload/images/20240921/201691632XvLVc3NiJ.png)

那有通過通道的，當然就要做寄信的動作，我們寄信就是直接設置寄給 Respondent Email，在內文中我們使用前幾天教的函數來達成取出名稱的效果，例如原本的 Email 為 Gordon@gmail.com而我們只需要的是 @ 前方的名稱 Gordon，那我們就利用 substring + indexOf 來達到該效果。

![https://ithelp.ithome.com.tw/upload/images/20240921/20169163DBk0xeZPdm.png](https://ithelp.ithome.com.tw/upload/images/20240921/20169163DBk0xeZPdm.png)

我們再將這個場景設定排程，每天下午五點執行，就這樣達到有新用戶來填表單，下午五點就會做寄送資訊的動作。
那如果舊客戶也需要寄送的話，就可以使用 Get a Response 而不是 Watch，因為 Watch 只會看新的填單著，那如果是要整份的填單者，就使用 Get 來達到效果，這樣未來有新資訊就可以寄給這些有填過的人。

然而我們也知道 Google form 有一個連接 Google sheet 的功能，那我們也能夠連接後，將第一個模組換成 Google sheet 再做寄信，這樣就能完成一樣的效果。
同一個流程都有很多方法可以完成，可以在中間發揮創意，也能用一些技巧省一些 operation，用較少的 operation 達到相同的事情，這也能為你省一些使用 Make 的額度。

大家可以從最上方下載藍圖來測試看看結果。

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
