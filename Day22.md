Day22 進階介面說明

實作是最好的練習，且有概念需要實做、操作才能更了解，我這邊會提供藍圖來做下載，可以當作每天的練習，匯入並且嘗試看看效果，下載我的[藍圖](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)，匯入進去操作看看。
匯入方法 [Day09 使用藍圖](https://ithelp.ithome.com.tw/articles/10352992)

---

#### Webhook

左方的選單列其實還有蠻多功能沒有做說明，例如 Webhook，點擊進去就可以看到這是所有我們有在 Make.com 中開的 Webhook，可以看到我有一個是紅色自己客製化的 webhook，就是我們前幾天講 webhook 時製作的。
而其他有我們製作個人 Line 助理新增的。
![https://ithelp.ithome.com.tw/upload/images/20240927/20169163KkTmEalB74.png](https://ithelp.ithome.com.tw/upload/images/20240927/20169163KkTmEalB74.png)

這些 webhook 可以開關，直接從這裡管理，當然如果將它關掉，你原本場景若有使用到，就會無法使用。
Webhook 通常都是場景中第一個觸發的，觸發該場景，還記得我們場景是可以開關的，如果持續開起來，只要該 webhook 有被呼叫到，就會做場景的事情，但是如果我們將場景關閉會怎樣呢？
這邊的 webhook 還是會收訊息歐，而他收到的訊息就會存在右邊有一個車子的圖案，我的方案目前是可以存 50 筆資料。
那也可以利用這個，就算你可能在開發中，或是調整場景，這時候 webhook 還是會收到，而使用者的需求你就能在開發完成後，幫他將需求都送出去。

下圖的話就是我賴的 webhook，因為我在關閉場景後，還是有傳送訊息給個人助理，那他就會將這些訊息放在這邊。
![https://ithelp.ithome.com.tw/upload/images/20240927/20169163scOUbNADt7.png](https://ithelp.ithome.com.tw/upload/images/20240927/20169163scOUbNADt7.png)

那我們點擊 detail 就可以看見你這些 webhook 所收到的訊息，例如果這個就是傳送一個「嗨」給我的助理，他就先將訊息存在這邊。
![https://ithelp.ithome.com.tw/upload/images/20240927/20169163U6HV6iz8xr.png](https://ithelp.ithome.com.tw/upload/images/20240927/20169163U6HV6iz8xr.png)

#### Connection

另外就是 Connection 更常會使用到，因為 Make 就是來串工作流，那我們說其他 SASS 服務我們要操作都是需要權限去連接，例如最容易接觸到的 google 服務，我們當然要先 Make Google 的權限，就像我們在其他網頁做第三方登入的感覺。

那這些連接要開提供服務的是否會需要一段時間要重新驗證，例如有些網站登入一段時間會踢出去，需要你重新登入，也就是 Reauthorize，那 Make 也是這麼做，我們的場景非常多，如果要點到各個場景去做 Reauthorize 會非常麻煩，所以我們都會直接從 Connection 這邊直接點擊你相對應的服務，來做 Reauthorize。

所以就可以簡單地直接到該頁面做 Reauthorize 和 Verify，如果當你開發一個場景，發現他出現一些錯誤，那檢查後可能就是需要重新授權，授權後就可以繼續讓流程自動化完成了！

![https://ithelp.ithome.com.tw/upload/images/20240927/20169163QAhdqhVSgM.png](https://ithelp.ithome.com.tw/upload/images/20240927/20169163QAhdqhVSgM.png)

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
