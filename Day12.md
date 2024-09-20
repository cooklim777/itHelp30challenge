Day12 處理和轉換數據(1)：數據過濾與格式化

實作是最好的練習，且有概念需要實做、操作才能更了解，我這邊會提供藍圖來做下載，可以當作每天的練習，匯入並且嘗試看看效果，下載我的[藍圖](https://drive.google.com/drive/folders/1Dpz4c-BdeMZziNrlVK3hQkyCx_q8_rE9?usp=sharing)，匯入進去操作看看。
匯入方法 [Day09 使用藍圖](https://ithelp.ithome.com.tw/articles/10352992)

---

延續昨天的部分，我們要來談論 array 如何運作，還有函數的部分，Make 中有需多函數可以做資料的處理。
我們將原本只有 Google Sheet 和 Gmail，再新增一個 Tool 為 set variable，那我們要如何運行 google sheet 後要同時運興 Gmail 和這個工具呢，我們只要將 tool 左方的點連至前面的模組(Google sheet)他就會自動幫我們製造一個 router，來達到這個效果。
不過這也不太算是同時的運作，他還是有先後順序的，他會先運行你一開始連接的模組，在運行後連接的，那也可以點選下方的 auto-align 會幫你排列好，回先運行上方的模組再運行下方的，在連接處其實他也有提示 1st 和 2nd。

![https://ithelp.ithome.com.tw/upload/images/20240919/20169163sVOmHLFo2m.png](https://ithelp.ithome.com.tw/upload/images/20240919/20169163sVOmHLFo2m.png)

那我們因為現在要嘗試下方的 set variable 而已，可以將不需要用到的模組先關閉，我們在連接處點右鍵，就會出現選單，可以選擇 Disable，讓他不運行，也有其他的選項，例如 set up a filter 也很常使用到。

![https://ithelp.ithome.com.tw/upload/images/20240919/20169163K4pNSeBe8n.png](https://ithelp.ithome.com.tw/upload/images/20240919/20169163K4pNSeBe8n.png)

那我們再看一次 google sheet 產生的資料，有三筆資訊，現在想要做的是將 Status 為 Cloud 才是需要的資料，所以我們就必須使用 filter 來做過濾，那我們直接在連接 router 的線點擊，就可以設定 filter 了

![https://ithelp.ithome.com.tw/upload/images/20240919/20169163IzYSuO8mAJ.png](https://ithelp.ithome.com.tw/upload/images/20240919/20169163IzYSuO8mAJ.png)

**設定 filter**
點擊連接模組的線，就會出現 filter 的設定，那我們就是選擇最簡單的 equal to，等於 Clouds 的會通過這個連接點，一樣上方的 Status 就是直接靠選單做選擇就可以，然後再執行一次，就會發現這個漏斗顯示 2，代表只有兩個資料通過，在點擊漏斗，他會顯示哪些資料有通過，哪些沒有。
![https://ithelp.ithome.com.tw/upload/images/20240919/20169163E5bCxL0PjP.png](https://ithelp.ithome.com.tw/upload/images/20240919/20169163E5bCxL0PjP.png)

接下來我們要得到的是 filter 後的資料，氣溫最高的那一天所有資料。
因為我們得到的還是一個 array，就是有好幾筆類似的資料排列著，所以我們要使用 Aggregate 聚合，可以看到下圖，聚合就像是好幾筆的資料一起進來，然後只有一條線出去，所以這也只會消耗掉一個 Operation，他是將一個 array 中很多個資訊聚合成一個 collection。
那我們選擇 Source Module 因為原本的 Array 是 Google sheet 所以就選擇這個模組，然後下方是你需要者些 array 的什麼資訊，我們勾選需要的就好，原本還有一些空白的欄位我們就不勾選。

![https://ithelp.ithome.com.tw/upload/images/20240919/20169163A875Kpt3Rg.png](https://ithelp.ithome.com.tw/upload/images/20240919/20169163A875Kpt3Rg.png)

那再來看一下結果，看到 input 有兩個 collection 就是通過 filter 的兩筆資料，而 output 就是將這兩筆資料聚合了，所以可以看到它是一個 bundle 裡面有一筆的 array，array 中就是剛剛兩個 collection。
![https://ithelp.ithome.com.tw/upload/images/20240919/201691635kkFJDI7GC.png](https://ithelp.ithome.com.tw/upload/images/20240919/201691635kkFJDI7GC.png)

接下來連接一個 set variable 模組，這模組主要就是可以將變數取名，之後會用到，也能利用這個先做一點函數的計算，那我們先最簡單的將氣溫設定為前面 array 中的氣溫，那可以看到 array[] 這個 []內就是可以打你需要的是第幾筆資料（也就是上圖的 array 中的 1,2），若空白就是第一筆。

![https://ithelp.ithome.com.tw/upload/images/20240919/20169163wlGwJJ6bLN.png](https://ithelp.ithome.com.tw/upload/images/20240919/20169163wlGwJJ6bLN.png)

那接下來我們要教怎麼使用函數來得到這些資料中最高的氣溫。
看到下圖，就是我們在設定傳遞參數的部分，他其實還有好幾個部分可以選擇，有許多函數運算可以使用，那最主要有分為數字、文字、日期、Array 相關的
![https://ithelp.ithome.com.tw/upload/images/20240919/20169163AztXHyeVCI.png](https://ithelp.ithome.com.tw/upload/images/20240919/20169163AztXHyeVCI.png)

那我們就先使用 Array 中的 map，而他也會給相應的提示，跟你說這個 function 是幹嘛用的，那 map 簡單來說是將一個複雜的 array，而我只需要取得裡面的哪一個屬性，那我只需要的是氣溫這個，那昨天有說過 data 中 raw 和顯示的不同，我們要找到真的 key，我們要保留的是 array 中裡面 key 為 0 的這個部分，key 不是氣溫，可以看到我紅色框選的部分。

![https://ithelp.ithome.com.tw/upload/images/20240919/20169163v2F3WT40kM.png](https://ithelp.ithome.com.tw/upload/images/20240919/20169163v2F3WT40kM.png)

那來看一下執行結果，output 就只有一個 collection 裡面是氣溫(我們設定 variable 的名稱)，裡面的資料就是 value 我們剛剛使用 map 得到乾淨的氣溫資訊而已。

![https://ithelp.ithome.com.tw/upload/images/20240919/20169163NDvTTajfl5.png](https://ithelp.ithome.com.tw/upload/images/20240919/20169163NDvTTajfl5.png)

再來我們就可以對這個氣溫資訊為 [ 29.29 , 31.28 ] 這樣的資訊，做 max 的函數處理，得到最大值，因為 map 為[ 29.29 , 31.28 ] => max([ 29.29 , 31.28 ])=31.28，使用這種方式得到最大值。

![https://ithelp.ithome.com.tw/upload/images/20240919/20169163BegSrnzFWO.png](https://ithelp.ithome.com.tw/upload/images/20240919/20169163BegSrnzFWO.png)

可能會覺得稍微有點麻煩，但因為 Make 這種流程自動化都是已經包好的工具，主要為 No-code，但是數據處理當然還是需要一點 code，而也因為這樣，會導致數據處理在這些工具其實都是相對劣勢，會需要一些技巧、方法，來達成，因為沒有所有大家所習慣使用的函數，所以就是只能使用它提供的這些來拼湊出你想要的功能。
但其實使用起來比較常用的組合也那幾種，用習慣就發現會了，甚至就把它存成藍圖或是使用模板，也都拿達到提示的效果。

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
