Day18 實例應用(4) - Line 個人助理自動添加行事曆

實作是最好的練習，且有概念需要實做、操作才能更了解，我這邊會提供藍圖來做下載，可以當作每天的練習，匯入並且嘗試看看效果，下載我的[藍圖](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)，匯入進去操作看看。
匯入方法 [Day09 使用藍圖](https://ithelp.ithome.com.tw/articles/10352992)

---

昨天我們介紹怎麼串接賴 OA 帳號，自己創建一個官方帳號，然後跟 Make 串接，就可以自動回覆訊息了，那我們就能夠在這之間串接各種需要的模組，例如你常常在外面使用手機，或是公司員工需要查詢訂單資訊，而公司所有訂單資料都在某一份 google sheet 之中，那就可以傳送例如訂單:534，給個人助理，他就會回你訂單的想詳細資訊。
或者是公司要統計便當，可以直接傳訊息，然後就會直接新增在 google sheet 也是一種使用方式。

那待會會示範如何自動創建行事曆

就直接在 Line 模組後串接一個 Google Calender

![https://ithelp.ithome.com.tw/upload/images/20240924/20169163PsacvLixeG.png](https://ithelp.ithome.com.tw/upload/images/20240924/20169163PsacvLixeG.png)

那傳訊息時打上 ->
創建行事曆
名稱：聚餐
時間：9/25 17:00
在直接藉由分析字串來得到需要新增日曆的 Event Name, Start Date，就能完成流程了。

等等...
誰會平常傳賴還會乖乖使用模板，我還需要中規中矩的打上名稱，時間，太麻煩了吧，我怎麼不開啟 calender 自己建立還比較快。
沒錯，所以我們要來解決這個問題，在中間再串接一個 GPT 來幫我們做解析就好，這樣我們就能夠叫隨意的打上我們的訊息。

那就在 Line 模組後面先串接 GPT，並給他適合的 prompt，再放上 Line 收到的訊息，我直接傳「創建行事曆 聚餐 9/25 17:00」，他就分析出對應的結果。

![https://ithelp.ithome.com.tw/upload/images/20240924/20169163hQN7j7Glsm.png](https://ithelp.ithome.com.tw/upload/images/20240924/20169163hQN7j7Glsm.png)
![https://ithelp.ithome.com.tw/upload/images/20240924/20169163YYK8E4oIpU.png](https://ithelp.ithome.com.tw/upload/images/20240924/20169163YYK8E4oIpU.png)

接下來就只要放到 calender 模組對應的欄位，就大功告成了，然後最後再加一個 Line 傳訊息回去說創建的結果。

![https://ithelp.ithome.com.tw/upload/images/20240924/20169163BwDIMTicUv.png](https://ithelp.ithome.com.tw/upload/images/20240924/20169163BwDIMTicUv.png)

一樣可以去下載我的藍圖，匯入到你的 Make.com 之中，不過因為是多模組的應用，就得需要開通個模組的金鑰等等，賴要自己去創建帳號，還有 GPT 的 Key 也需要申請，有興趣就可以去嘗試看看！！

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
