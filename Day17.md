Day17 實例應用(3) - 自己製作 Line 個人助理(1)

實作是最好的練習，且有概念需要實做、操作才能更了解，我這邊會提供藍圖來做下載，可以當作每天的練習，匯入並且嘗試看看效果，下載我的[藍圖](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)，匯入進去操作看看。
匯入方法 [Day09 使用藍圖](https://ithelp.ithome.com.tw/articles/10352992)

---

今天來介紹 Line 官方帳號傳訊息，能做出自己的小助手，首先要先到 Line OA 來辦一個官方帳號，並加他好友，我自己辦一個叫個人助理的帳號，辦的過程蠻簡單的，就沒有圖文了。 [Line OA 網站](https://tw.linebiz.com/login/)

![https://ithelp.ithome.com.tw/upload/images/20240923/20169163iMwmp380h1.png](https://ithelp.ithome.com.tw/upload/images/20240923/20169163iMwmp380h1.png)

辦好後就，之後要到該帳號的右上角設定，有一左方有個 Messaging API 來做設定，一開始會叫你啟用，並且填入服務提供者，這就有點像管理員，可以填寫你的名字即可，他下方說要到 Line Developer 做另外設定，可以直接點擊連到 [Line Developer](https://developers.line.biz/en/)。下圖的紅色框可以先不用管。

![https://ithelp.ithome.com.tw/upload/images/20240923/20169163SzyBTP0Sni.png](https://ithelp.ithome.com.tw/upload/images/20240923/20169163SzyBTP0Sni.png)

到 Line Developer 的畫面，之後到你剛剛建立的管理員，應該就會看到你的官方帳號，這時候點進去點選上方的 Messenger API，滑到最下方有個 Channel access token，點選 issue，就會給你一串，就有點像密碼，就會有這個 API 服務，之後將這個 token 貼到 Make 的 Line 模組中，我們使用 Watch Event。
![https://ithelp.ithome.com.tw/upload/images/20240923/20169163NobI8H4NsG.png](https://ithelp.ithome.com.tw/upload/images/20240923/20169163NobI8H4NsG.png)

Make 模組連接好後，就可以選擇我的個人助理，之後下方就出現了一個 https://hook....，這就是 Webhook，複製這個再貼到一開始我們在 Line OA 使用 API 的地方
![https://ithelp.ithome.com.tw/upload/images/20240923/20169163b8augtaUVF.png](https://ithelp.ithome.com.tw/upload/images/20240923/20169163b8augtaUVF.png)

貼到下圖的 Webhook URL，最後記得到回應設定將你的 Messaging API 打開來。
![https://ithelp.ithome.com.tw/upload/images/20240923/20169163SzyBTP0Sni.png](https://ithelp.ithome.com.tw/upload/images/20240923/20169163SzyBTP0Sni.png)

這樣我們就可以直接使用 Make 得到有人傳的賴訊息拉～
我們啟動模組後，傳訊息給該帳號，Make 這邊就會動作，得到訊息內容、該用戶 ID 等等。

![https://ithelp.ithome.com.tw/upload/images/20240923/201691636xqIXn2X7L.png](https://ithelp.ithome.com.tw/upload/images/20240923/201691636xqIXn2X7L.png)

那我們簡單接一個 Reply，來做簡單的回應，Reply Token 就在我們收到的 Event 中會有。
執行後傳個訊息過去，就能得到回應了！
![https://ithelp.ithome.com.tw/upload/images/20240923/20169163wv4QT6BZCm.png](https://ithelp.ithome.com.tw/upload/images/20240923/20169163wv4QT6BZCm.png)
![https://ithelp.ithome.com.tw/upload/images/20240923/20169163cJgUeK7sEP.png](https://ithelp.ithome.com.tw/upload/images/20240923/20169163cJgUeK7sEP.png)

那我們串接好 Line 的部分接下來的花樣就可以很多，例如你可以直接傳賴告訴一筆訂單，可能需要做查詢，或是新增資料等等的動作。
那明天我會再串接 GPT 和行事曆，可以達到傳訊息幫我建立行事曆的助理。

備註：
Webhook 是一種在特定事件發生時自動發送訊息或執行程式的機制。通常用於應用程式或服務之間的即時通訊和資料同步。當某個事件（如訂單被創建、用戶註冊等）發生時，系統可以自動向設定的網址（即 webhook URL）發送 HTTP 請求，以通知該事件的發生或傳遞相關數據。這種方式可以實現系統之間的實時互動和數據同步，常見於各種網路應用程式的整合中。
也就是 Line OA 在收到訊息的同時，又發訊息給剛剛連接的 Make，所以 Make 可以得到訊息的內容。

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
