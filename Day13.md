Day13 處理和轉換數據(2)：array 的處理、和原始樣態

實作是最好的練習，且有概念需要實做、操作才能更了解，我這邊會提供藍圖來做下載，可以當作每天的練習，匯入並且嘗試看看效果，下載我的[藍圖](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)，匯入進去操作看看。
匯入方法 [Day09 使用藍圖](https://ithelp.ithome.com.tw/articles/10352992)

---

我們使用一樣的資料，另外可以在 Make 中看到的資料右上角，點擊下載 data，就可以將原始資料下載下來。
![資料下載](https://ithelp.ithome.com.tw/upload/images/20240920/20169163uUuJXlgbnB.png)

那我們也可以看見原始資料就是 output 為一個 array 裡面為 三個 object(之前說的 collection)，然後 object 中的 0,1,2,3 就是我們氣溫、日落時間、天氣、記錄時間的資料，也就是我們提到的 Raw 和顯示的不同的關係，這邊就是原始的 Key 為 0,1,2,3，再來可以看到時間上怎麼日落時間是 10 點，那這是因為他是使用原始的時間格式，可以看到最後方為 000Z 表示沒有時區偏移，那 make 因為我們設定是在台灣，時區為 +8，所以他會自動幫我們修正為 +8 時區的時間顯示給你看。
以下是 google sheet raw data

```json
[
  {
    "0": "29.29",
    "1": "2024-09-12T10:01:45.000Z",
    "2": "Clouds",
    "3": "2024-09-12T12:07:04.960Z",
    "__ROW_NUMBER__": 2,
    "__SPREADSHEET_ID__": "1mHMiz2-lshSteHNMeWyhiDkxu78Z1MEyTwq01qTuwX0",
    "__SHEET__": "天氣",
    "__IMTLENGTH__": 3,
    "__IMTINDEX__": 1
  },
  {
    "0": "31.28",
    "1": "2024-09-17T09:56:18.000Z",
    "2": "Clouds",
    "3": "2024-09-17T09:32:02.850Z",
    "__ROW_NUMBER__": 3,
    "__SPREADSHEET_ID__": "1mHMiz2-lshSteHNMeWyhiDkxu78Z1MEyTwq01qTuwX0",
    "__SHEET__": "天氣",
    "__IMTLENGTH__": 3,
    "__IMTINDEX__": 2
  },
  {
    "0": "28.68",
    "1": "2024-09-18T09:55:13.000Z",
    "2": "Rain",
    "3": "2024-09-18T08:53:06.725Z",
    "__ROW_NUMBER__": 4,
    "__SPREADSHEET_ID__": "1mHMiz2-lshSteHNMeWyhiDkxu78Z1MEyTwq01qTuwX0",
    "__SHEET__": "天氣",
    "__IMTLENGTH__": 3,
    "__IMTINDEX__": 3
  }
]
```

那接下來教其他函數的應用，昨天教了先使用 aggregate 模組，然後在使用 map 和 max 兩個搭配起來得到最高的氣溫，那最低的氣溫就使用 min 即可得到。
那我們也觀察一下 aggregate 的 raw data 是什麼。
第一層只有一個{}所以對但裡面也包著 array，對 make 來說裡面算是只有一個東西，所以跑到下一個模組他不會變成循環跑很多次。
這使用 raw data 理解的方式可能對資料格式熟悉的人，會能讓你更了解，但若無法理解也能直接使用 Make 做練習，試過就知道他的方式了。

```
[
    {
        "array": [
            {
                "0": "29.29",
                "1": "2024-09-12T10:01:45.000Z",
                "2": "Clouds",
                "3": "2024-09-12T12:07:04.960Z",
                "__SHEET__": "天氣",
                "__IMTINDEX__": 1,
                "__IMTLENGTH__": 3,
                "__ROW_NUMBER__": 2,
                "__SPREADSHEET_ID__": "1mHMiz2-lshSteHNMeWyhiDkxu78Z1MEyTwq01qTuwX0"
            },
            {
                "0": "31.28",
                "1": "2024-09-17T09:56:18.000Z",
                "2": "Clouds",
                "3": "2024-09-17T09:32:02.850Z",
                "__SHEET__": "天氣",
                "__IMTINDEX__": 2,
                "__IMTLENGTH__": 3,
                "__ROW_NUMBER__": 3,
                "__SPREADSHEET_ID__": "1mHMiz2-lshSteHNMeWyhiDkxu78Z1MEyTwq01qTuwX0"
            }
        ],
        "__IMTAGGLENGTH__": 2
    }
]
```

**get**
get 也是 array 的其中一個方法，他可以讓我們得到需要的資料，需要得到這個 array 的第幾個，get(array[];raw_name)，所以設置 aggregate 模組的 array 也注意圖片 array 他的變數後方也會顯示[] 就可以知道他是 array，那我要取得的是第 1 筆資料，所以設定 1，就會拿到第一筆的資料。
那也可以使用組合技 get(map(array[];0);1)，map 裡面的 0 為氣溫的 raw key，所以這樣我們就只會得到第一筆氣溫資料。

![https://ithelp.ithome.com.tw/upload/images/20240920/201691633srACVnm0d.png](https://ithelp.ithome.com.tw/upload/images/20240920/201691633srACVnm0d.png)

**sort**
sort(array[];asc/desc;raw_name) 這些有關 array 的函數幾乎都是第一個放著你需要處理的 array 後面放要處理的欄位，sort 就是可以做排序的動作，中間參數的 asc/desc 分別是升幕降冪，所以你可以以氣溫排序，然後使用降冪，在使用 get 得到第一個，也能到得到最高溫。

**join**
可以將每個 array 中間插入指定的文字，例如有一個簡單的 array [1,2,3]，join 插入 777，就會變成 177727773。

**slice**
可以將 array 切分，取得你想要的數量，例如 array 原本有 100 個元素，而你只需要 20~80 個，就可以使用。

**merge**
可以將兩個類似格式的 array 合併

**contain**
可以看 array 是否有包含什麼，做條件式的處理。

其他還有蠻多的功能，因為本體其實還是算 JavaScript 所以 JS 有的大部分都有，但是宣告方式有些不同，所以需要再去看一下說明即可。

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
