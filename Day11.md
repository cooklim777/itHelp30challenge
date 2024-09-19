Day11 如何將參數傳遞至下一個模組

實作是最好的練習，且有概念需要實做、操作才能更了解，我這邊會提供藍圖來做下載，可以當作每天的練習，匯入並且嘗試看看效果，下載我的[藍圖](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)，匯入進去操作看看。
匯入方法 [Day09 使用藍圖](https://ithelp.ithome.com.tw/articles/10352992)

---

昨天講一個模組如何運行，Input/Output，還有資料的型態，那今天講如何串接，還有將變數使用在接下來的模組中。

先看下圖，我一樣使用 search row 得到 google sheet 的資料，然後要做寄信的動作，他會將我所搜尋到的資料都做寄信，那可以看到我的最後內文寫：
氣溫為 5.氣溫(A)，這個你只要直接打上你的純文字在點擊你右邊想要使用的變數就可以了，他就會將它自動替換成變數。
這樣就會自動替換成你的模板，做寄信的動作。

![https://ithelp.ithome.com.tw/upload/images/20240918/20169163pVd7reQXU8.png](https://ithelp.ithome.com.tw/upload/images/20240918/20169163pVd7reQXU8.png)

**Key 的 Raw 和 顯示的不同**
這可能需要操作才能更理解，可以的話可以下載我的[藍圖]()，匯入進去操作看看。
在我的 content 中，氣溫為 {{5.氣溫(A)}} 但實際上是為 氣溫為 {{5.`0`}}，這可能直接看有點難理解，但你在操作時，如果你直接複製我這個 content 在其他地方做貼上會發現變成 {{5.`0`}}，那這個原因是因為原始的 key 其實是叫做 `0`，但是 Make 為了讓你好瞭解，將它換成的 header 的氣溫，而也能從上圖指上去變數中，他會顯示他的型態、Raw 是什麼，這個 Raw 就是原始的 key 值。這個概念之後再寫公式時會用到。

接下來看一下執行結果，google sheet 一樣得到資訊，而目前有三個資料，在昨天的介紹中有說 google sheet 有許多的 bundle 而 output 是一個 array，所以當你跑下一個模組時，他會一個 bundle 跑一次，跑到下一個模組，也可以看到下一個 gmail 寄信右上角的泡泡顯示 3，那這就是他跑了 3 次流程，就跟迴圈的概念一樣，所以整個流程共消耗 4 個 operation。
那就會收到三封信，也可以打開 gmail 右上角的泡泡，看詳細資訊，就能看到他有三個 Operation，而分別的時間、天氣、氣溫也是各列得值。
![https://ithelp.ithome.com.tw/upload/images/20240918/20169163oA3vmbEi7V.png](https://ithelp.ithome.com.tw/upload/images/20240918/20169163oA3vmbEi7V.png)

所以要傳遞參數其實非常簡單，只需要在你下一個模組中的 input 點擊，他就會出現可以讓你選擇前面參數的資料（要先讓前面的模組運行過一次），然後做點擊他就會自己帶入了。

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
