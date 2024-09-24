Day14 處理和轉換數據(3)：日期、文字、數字處理

實作是最好的練習，且有概念需要實做、操作才能更了解，我這邊會提供藍圖來做下載，可以當作每天的練習，匯入並且嘗試看看效果，下載我的[藍圖](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)，匯入進去操作看看。
匯入方法 [Day09 使用藍圖](https://ithelp.ithome.com.tw/articles/10352992)

---

還記得我們在第八天的練習，將得到的天氣資訊存到 Google sheet 之中，存起來的樣子長下方表格，那我們想要將日落時間顯示格式為 YYYY/MM/DD HH:mm 該如何做，只需要使用函數來做一個轉換即可
| 氣溫 | 日落時間 | Status | 目前時間 |
| ----- | ------------------------ | ------ | ------------------------ |
| 29.29 | 2024-09-12T10:01:45.000Z | Clouds | 2024-09-12T12:07:04.960Z |

**日期處理**
使用 formatDate(日期;需要的格式)，他就會自動做轉換了，而年月日轉換的型態也有很多種，也能得到英文的月份等等，可以再去看他的詳細說明。
可以看到 Input 我們就得到相應的格式，然後寫進 Google sheet 之中了

![https://ithelp.ithome.com.tw/upload/images/20240920/20169163k6agEruyLT.png](https://ithelp.ithome.com.tw/upload/images/20240920/20169163k6agEruyLT.png)

日期的處理還有許多的函數可以使用，例如自己設定年月日為多少，或是將原本有的日期加上幾個月之類的操作，也有 now 的變數可以使用，就是你當下的時間，可以用來當啟動該流程的時間。

**數字處理**
最常使用的就是 round, max, min , average 等等的函數，可以達到四捨五入、最大、平均的運算，特別的是有可以直接算出標準差的函數。
還有 formatNumber，可以將你的數字變成你想要的形式，例如 50000 -> 50,000 這種，或是加上錢的符號等等。

**字串處理**
有 lower, upper 變換大小寫的處理，trim, replace, toString 等等常見的處理，trim 可以將字串中左右兩邊有多餘的空白刪除，toString 是將數字轉換成字串而可以做一些處理。
indexOf 找出該字串是否有包含什麼字，且傳回位子，若沒有找到則回傳 -1。
另外也有 sha1, md5 等等加密的處理方式這些函數都有提供。

利用模組的串接，和函數處理數據，得到想要的數據，來達到自動化的效果。
接下來會先介紹一些實際例子，再來繼續介紹一些功能，包括錯誤處理等等。

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
