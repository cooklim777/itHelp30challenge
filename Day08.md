Day08 第一個工作流程：從零開始設計

我們一樣從觸發器開始，設置 Watch new Rows，所以他會觀看這個 sheet，如果有新增 Row 就會觸發該流程，那設置如下，先連結你的 google 帳號，然後選擇你要觀看的 sheet，那我通常第二個 Search Method 我會選擇 Select from all 這樣就可以直接貼上 sheetID 比較快速。
![https://ithelp.ithome.com.tw/upload/images/20240912/20169163LN0hBKTFgR.png](https://ithelp.ithome.com.tw/upload/images/20240912/20169163LN0hBKTFgR.png)

![https://ithelp.ithome.com.tw/upload/images/20240912/20169163DmY2dqH1UY.png](https://ithelp.ithome.com.tw/upload/images/20240912/20169163DmY2dqH1UY.png)

點擊 OK 後看到這個，這是指說哪些資料才算是新資料的起始點，我們目前資料都沒有跑過，所以就設定所有都是新資料。
![https://ithelp.ithome.com.tw/upload/images/20240912/20169163D0DE6kA6V3.png](https://ithelp.ithome.com.tw/upload/images/20240912/20169163D0DE6kA6V3.png)

而我們的資料如下
| 學生名單 | 入學日期 |
| -------- | -------- |
| Candy | 11 月 |
| Sam | 12 月 |

點擊 Make 左下方的 Run once，可以看到模組右上角就會出現一個泡泡，裡面的資料可以看到寫 bundle1 bundle2，裡面就是存放這次模組讀取到的資料。而因為我們目前只有兩筆，而這次執行就代表，這兩筆新資料已經跑完，若再按一次 Run once 就不會有資料了，除非你在 google sheet 中新增資料。
![https://ithelp.ithome.com.tw/upload/images/20240912/2016916309UzYR9ljn.png](https://ithelp.ithome.com.tw/upload/images/20240912/2016916309UzYR9ljn.png)

而這個觸發器的應用可能就是每天觸發一次，若有新資料就代表我們會有這些 Bundle，那再看要將這些資料後續做什麼事情，例如建立學生名單等等。
這些 output 的資料都可以拿到後續的模組來使用，例如我接下來要在 Notion 建立學生名單，那我就使用 Notion 中的 create，連接好，選擇設置好對應的資料即可。
有些模組會有 input 和 output，例如下圖我在天氣模組設置，他需要設置 Input，才能從他那邊的資料庫拿到資訊，給我 output 的結果。

![https://ithelp.ithome.com.tw/upload/images/20240912/20169163zYXEOf7AZE.png](https://ithelp.ithome.com.tw/upload/images/20240912/20169163zYXEOf7AZE.png)

另外可以看到他在 Wind 的左方有一個 +，右方寫著(Collection)，裡面的內容為
"Speed":6.17 , "Wind direction, degrees":80，這個形式就像是 JavaScript 中的 Object，像是生活中的字典，Wind 裡面的 Speed 為 6.17，而 Wind 又是我們 Bundle 的其中一個元素，層層包起，這就是在 Make 中的資料樣態。

接下來我們來做一個簡單的自動化，每天我們要早上得到天氣，然後記錄在 google sheet 當中，所以在得到天氣的下一個要使用 Google sheet add row 的部分，可以看到我先將我的 google sheet 表頭設定好，接下來就是增加的列需要為什麽值，那我點擊 A 列時，他就會出現前面模組跑出的 bundle 資料，我們就可以取用這些變數。
![https://ithelp.ithome.com.tw/upload/images/20240912/20169163W2bh2BI4Y4.png](https://ithelp.ithome.com.tw/upload/images/20240912/20169163W2bh2BI4Y4.png)

Run once 再回到 google sheet 中，就可以看到下方資料了，那我們再從昨天的觸發器說明，將觸發器設定為每天早上 8 點啟動，那就可以得到每天記錄的表格了。
而這個時間的格式好像有點醜，之後也會教大家如何更改他。

| 氣溫  | 日落時間                 | Status | 目前時間                 |
| ----- | ------------------------ | ------ | ------------------------ |
| 29.29 | 2024-09-12T10:01:45.000Z | Clouds | 2024-09-12T12:07:04.960Z |

那我這裡也提供這個範本，雖然是個沒什麼用的場景 XD，也還沒教如何導入範本，那這就當作是明天的教學好了！
[Day08 天氣記錄到 google sheet 範本](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
