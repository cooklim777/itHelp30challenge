Day16 實例應用(2) - 表單預約會議室

實作是最好的練習，且有概念需要實做、操作才能更了解，我這邊會提供
藍圖來做下載，可以當作每天的練習，匯入並且嘗試看看效果，下載我的[藍圖](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)，匯入進去操作看看。
匯入方法 [Day09 使用藍圖](https://ithelp.ithome.com.tw/articles/10352992)

---

今天流程是使用表單來做預約公司會議室的動作，預約後會直接建立在公司的 calender 上面，供人員觀看。另外也能連接寄信模組，再加上邀請會議，也能做到預約個人時間等動作，就像現在有些做預約 meeting 等服務的流程，自己製作將其自動化。

首先我們有下列表單，並將其連接 google sheet 來達到同步。
![https://ithelp.ithome.com.tw/upload/images/20240922/201691637zxFfBsInE.png](https://ithelp.ithome.com.tw/upload/images/20240922/201691637zxFfBsInE.png)

跟昨天的動作相同，我們使用 Google form 的 Watch 來找新填寫的內容。

![https://ithelp.ithome.com.tw/upload/images/20240922/20169163SJaaq3U1aR.png](https://ithelp.ithome.com.tw/upload/images/20240922/20169163SJaaq3U1aR.png)

然後將有填寫的內容新增到 Google Calender，這時我們就要連接 Calender，連接的方法比 google sheet 和 form 較麻煩些，可以看下方的 Online help 來做連接，若為免費的 google 帳號，需要到 GCP 平台做連接才可以。
連接後我們就能選擇對應的日曆來創建事件，我們就將前一個模組預約的會議室＋預約人作為標題，然後時間設定 Start time 的部分，因為他要求要使用標準格式，所以我們要使用 parseDate 來達成此效果，我們要將原本的 2024-09-24 和 11:00 一起轉換成正確格式，所以使用 YYYY-MM-DDHHmm 來做一個轉換。

![https://ithelp.ithome.com.tw/upload/images/20240922/20169163VS4q9EiAGh.png](https://ithelp.ithome.com.tw/upload/images/20240922/20169163VS4q9EiAGh.png)

這樣我們就能夠完成了日曆的建立了，當我們啟動場景是，就會找到新的填入資訊，然後做日曆的新增。

![https://ithelp.ithome.com.tw/upload/images/20240922/201691638zyuyhxCAK.png](https://ithelp.ithome.com.tw/upload/images/20240922/201691638zyuyhxCAK.png)

這流程可能會有一些問題，我們在設計流程是可能會預想的比較簡單，但這也沒關係，遇到問題時再來做修正，一步一步修正完畢，達到需要的功能。
這也帶到我前面說的自動化概念，養成後可能會更容易知道會遇到什麼問題，資料要整理成怎樣，流程要怎麼設計，這些有時候會跟你所使用的工具有關，但更多的是有一些通則。

例如這個流程來說，可能會發現，有沒有可能會有重複的事件呢？或是填單者不小心填寫兩次，重複預約等等，這些都可以做考慮，然後再做流程的修改和優化。
例如大會議室在同一時間不能有兩個人同時預約，而這個要怎麼解決也有很多方法，例如找一個表單服務可以排除這個部分，當有人預約時該時間就不能做選擇。那如果是依 google form 可能沒這功能，那可以將它連接到 Google sheet，有新的事件時，我們還要再來看整份 Google sheet 的資訊，若新事件是 9/24 11 點要預約大會議室，就要對照一下是否有相同的資料在 Google sheet 之中，那如果有相同可能就可以寄信給預約者，跟他說已經被預約等等方式。
就是由自己去做構想，或是原本公司就有一定的方式，那就是用流程自動化工具將它自動化，讓大家更方便。

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
