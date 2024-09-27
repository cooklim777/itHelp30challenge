Day21 錯誤處理(2)

實作是最好的練習，且有概念需要實做、操作才能更了解，我這邊會提供藍圖來做下載，可以當作每天的練習，匯入並且嘗試看看效果，下載我的[藍圖](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)，匯入進去操作看看。
匯入方法 [Day09 使用藍圖](https://ithelp.ithome.com.tw/articles/10352992)

---

#### Commit：

確認並保存之前模組的所有變更，即使後續發生錯誤，之前的操作也不會被回退（使用在 ACID 模組）。

**ACID** 指的是資料庫管理系統（Database Management System, DBMS）中的 ACID 屬性。ACID 是四個特性的縮寫，分別是：

1. 原子性 (Atomicity)：指一個事務（transaction）中的所有操作要麼全部完成，要麼全部不執行，不存在部分完成的情況。
1. 一致性 (Consistency)：指事務從一個一致的狀態轉移到另一個一致的狀態，中間過程不會破壞資料的完整性。
1. 隔離性 (Isolation)：指在多個事務同時執行的情況下，每個事務的操作都不會受到其他事務的影響，每個事務似乎是在獨立運行的。
1. 持久性 (Durability)：指一旦事務完成，其對數據庫的變更就應該是永久性的，即使發生系統故障也不應該丟失。

ACID 屬性是設計和實現事務性資料庫系統時非常重要的概念，確保了數據的完整性、一致性和可靠性。可以在模組的右方看到有些就是會標注 ACID，那通常是有關資料庫的模組。

也就是說如果你在 ACID 模組中的 error handle 使用 commit 才有效果，不然就會像是 Ignore 直接忽略這個部分。
所以首先就是 ACID 模組才需要使用到 commit 這個才錯誤處理。
下圖為一個流程，來更改 Database 照理來說就是要全部成功才會做更改，若有失敗的部分就會全部退回來到最初的 Database，因為 ACID 的特性，那當你加了 commit 之後，就會有錯誤時會停止，但他前面沒錯的東西，還是會做提交的動作而不會被退回。

![https://ithelp.ithome.com.tw/upload/images/20240926/20169163Gvn4lta8al.png](https://ithelp.ithome.com.tw/upload/images/20240926/20169163Gvn4lta8al.png)

#### Ignore：

忽略當前的錯誤並繼續執行下一個模組，錯誤不會影響整個工作流的進程。
這就非常單純，直接忽略錯誤這次的錯誤，而這個模組的 bundle 也會直接刪除，下一次會繼續執行。
這可能用在你的流程中這個模組的錯誤可能不重要，或是下次執行又會補上，例如你的流程是將 google sheet 中資料去網站做查詢，並且查詢完會回填做紀錄，所以就算這次有問題發生錯誤（可能網站突然無法查詢），下次也會將查詢的結果補上。

#### Resume:

當錯誤發生後，允許工作流從某個特定的點重新開始運行，這樣可以避免完全從頭執行整個流程。

下圖可以看到 Resume 可以做一些設置，Status 和要回傳的 Data，收到 output 是錯誤時，可以直接將你這邊設定的資料回傳給上一個錯誤的模組，跟他說你吐出來的資料應該是長我給你的樣子才對，而也會繼續執行，跟上面忽略不一樣，忽略遇到錯誤時就會直接把該模組的 bundle 刪除，不會繼續到下一格模組。

![https://ithelp.ithome.com.tw/upload/images/20240926/201691633r6H7ubhj4.png](https://ithelp.ithome.com.tw/upload/images/20240926/201691633r6H7ubhj4.png)

#### Rollback:

回退所有之前的操作，恢復到錯誤發生前的狀態，避免不完整或錯誤的數據提交（這和 Commit 是相對的，也是使用在 ACID 模組之中）

有這些錯誤處理的方式，通常會使用 break 和 ignore 來做處理，break 之後若沒有重新執行成功，就會存到 Incomplete data 再來做處理。
當然你也能當某個模組錯誤時，你可以做 google sheet 直接記錄在你的表格之中，你之後再做處理。例如你是要做訂單的查詢，當查詢有錯誤時，就可以記錄在你的原本訂單的 sheet 中說查詢錯誤，等等的方式。

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
