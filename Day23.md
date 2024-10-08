Day23 寫複雜函數的小技巧

實作是最好的練習，且有概念需要實做、操作才能更了解，我這邊會提供藍圖來做下載，可以當作每天的練習，匯入並且嘗試看看效果，下載我的[藍圖](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)，匯入進去操作看看。
匯入方法 [Day09 使用藍圖](https://ithelp.ithome.com.tw/articles/10352992)

---

有時候我們需要做一些數據處理，處理使用函式可能較複雜，例如以下的例子，有想要得到 key 1 和 3 的時間差距。我們需要先將 YYYY 年 MM 月 DD 日 HH:mm 做轉換，然後在轉換成時間的 timestamp 相減，在轉換成幾分鐘（因為 make 中沒有快速可以得到 date 差距的函數，所以會很麻煩）
![https://ithelp.ithome.com.tw/upload/images/20240930/20169163lL0Vu6KhEg.png](https://ithelp.ithome.com.tw/upload/images/20240930/20169163lL0Vu6KhEg.png)

而下圖是我寫到一半的函數，整個就會蠻亂也蠻麻煩，如果有實作過就知道，這時候你可以將你寫的東西框選做複製，會得到 `` {{parseDate(20.array[].`1`; "YYYY年MM月DD日 HH:mm")}} -{{parseDate(20.array[].`3`; "YYYY年MM月DD日 HH:mm")}} ``，這算是他的原始樣子吧，而 make 將它變成你看到的樣子，而在原始型態時會更容易讓你編輯，編輯後再貼回即可。

![https://ithelp.ithome.com.tw/upload/images/20240930/201691634Oprncqfzh.png](https://ithelp.ithome.com.tw/upload/images/20240930/201691634Oprncqfzh.png)

然而要處理某些數據還是很麻煩，畢竟這邊只能使用它提供的函數來處理，而且提供的不算太多，比你使用程式語言處理來說還是麻煩許多。

而也能發現這些 no-code 工具會有的缺點，就是複雜的數據處理起來真的不簡單，複雜的流程或許可以做（因為已經幫你串好許多的 SASS 服務，你不需要在自己串）而且不用在重新看這些服務的 API 文件，因為你所用的功能 Make 可能已經串好了也模組化，就能快速得達到你想要的效果。

但是在數據處理這塊，真的不太容易，我們如果使用程式語言讀取 csv 檔案，我們可以很簡單的做 filter, 日期轉換、對照資料、各種數學運算，都是非常容易的，而且現在 AI 極度方便，這種跟程式語言較基礎相關的都是非常容易的寫出來的。

還是一樣，需要知道自己的需求，使用正確的工具。

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
