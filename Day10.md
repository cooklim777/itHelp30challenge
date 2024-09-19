Day10 Modules, Bundle, 資料型態

工作流程自動化就是使用許多的服務做串接，而每個服務的資料或使用方法可能都不一樣，但都不脫離 Input and Output

#### Input

1. 權限連接
   需要看一下如何連接，通常在 Make 該模組中也都會教做麼做連接，可能需要到該服務的網站去做一些設定，得到金鑰或是 OAuth（備註 1）
2. 參數設定
   例如我們前面使用天氣模組，就要告述他我要哪裡的天氣，或是使用 google sheet 就要知道是要搜尋哪份 sheet 等等。

而 Output 就是看該模組會出什麼資料，那我們需要的是要知道各資料的型態，讓我們能後續使用。

例如我要使用 Notion 和 Google sheet 他首先就是要我們先連接你的帳號，而怎麼連接，這就需要點擊下方的 online help 一步一步跟著做，來做連接，而有些很簡單就可能會直接導入到該服務的網頁做連接，但有些就需要做一些設置，所以都是得看這個 Online help 才準確。
那也不用太害怕很難，文檔都是英文，可以直接使用插件或是翻譯網頁簡單做翻譯，而裡面也都是圖文教學。
![https://ithelp.ithome.com.tw/upload/images/20240917/20169163fCDNs68ljj.png](https://ithelp.ithome.com.tw/upload/images/20240917/20169163fCDNs68ljj.png)

連接完後就像下圖，可以看到已經連接好的帳戶，那也代表該帳戶權限有的 google sheet 你應該是都可以使用的，而看到我選的是 Watch New Rows 的功能，google sheet 模組有非常多的功能（方法），而這些功能實際上有什麼作用，input 要怎麼設定，可以點擊該模組的有上角的「？」來做觀看。
因為每個人要使用的模組和服務都不同，所以主要是講大綱，而細部的模組怎麼使用，還是要靠自己看一下這些文檔，再把你需要的功能拼湊出來。
![https://ithelp.ithome.com.tw/upload/images/20240917/20169163PFBGiBKrJv.png](https://ithelp.ithome.com.tw/upload/images/20240917/20169163PFBGiBKrJv.png)

#### Bundle

接下來我們示範另一個方法，是 search rows，他需要填寫的有你的 sheet ID，sheet name，cols，那還有 filter sort order，這些功能，通常都可以嘗試看看就知道是什麼，若比較難理解的可以再去看文檔，那我 filter 等都留空，所以他就會去幫我把這張表的所有資料吐出來給我。
那我設定 input 完畢，就點選 run once 之後這個模組的右上角就會產生的一泡泡，我們稱作為 bundle，可以看到右方他的 input 其實就是我們剛剛填入的資料，而 output 當然就是我們需要的，得到該張表的資料，因為表裡面有兩列資料，那他就會給我，而這只會消耗掉一個 operations 就算你有 1000 列資料也只會消耗一個，因為他是算使用模組的次數，而非資料量。
![https://ithelp.ithome.com.tw/upload/images/20240917/201691636i6kp6rDer.png](https://ithelp.ithome.com.tw/upload/images/20240917/201691636i6kp6rDer.png)

#### 資料型態

下圖為 Output 的詳細資料
![https://ithelp.ithome.com.tw/upload/images/20240917/20169163fMM2rsr9pe.png](https://ithelp.ithome.com.tw/upload/images/20240917/20169163fMM2rsr9pe.png)

先介紹基本的資料型態

1. Text
   就是基本的文字型態，例如資料中 Status 中的 Clouds 就是文字型態
2. Number
   資料中的 Row number 即是數字
3. Date
   資料中的日落時間為 2024 年 9 月 12 日 18:01，即是日期的型態，那將滑鼠指到這種型態上面，他會出現黑色的部分為 2024-09-12T10:01:45:000Z 這個資料型態屬於 ISO 8601 標準的日期和時間格式，專門用來表示日期和時間資訊
4. Boolean
   就只有 true 和 false 兩種，例如有選項可能說你的資料要排序嗎，你選 No 其實就是 boolean 中的 false，而其他例如條件式 1>2 為 false，之後會介紹到條件式的應用

而另外還有兩個進階的型態是

1. Collection
   可以先看上面例子的 bundle1，他裡面有許多的資料是以 key 和 value 組成，例如 氣溫(A)為 29.29 度， 氣溫(A) 就是他的 key，而 value 就是 29.29，順帶一提這個 29.29 就是剛剛所說基本型態的數字。
   所以 collection 內部可以有多個的 key 和 value，而這個 value 也能夠是一個 Collection 或 Array 不僅只有可能是四個基本型態。

2. Array
   那 Array 就是上述例子的 output，他裡面包含好幾個元素，而這個例子中是 collection，在 Make 中他類似表格，搜集同類型的元素，而這個元素也可能是簡單的基本型態，也有可能是 collection。

依生活例子來形容，Collection 像是廚房中的各種東西，鍋子、碗、菜瓜布等等，完全不同的種類，而 Array 需要是同種類的，例如都是食物類，有蘋果、香蕉等等。

備註：
OAuth（Open Authorization）：是一種開放標準協議，用於授權訪問服務器上的資源，而無需將用戶的認證資訊（例如使用者名稱和密碼）直接透露給服務器。這通常用於允許第三方應用程序以代表用戶訪問服務。被廣泛應用於各種互聯網服務中，例如社交網路、雲端存儲服務等，以確保用戶資料的安全性和隱私保護。通常會過一段時間失效，要重新授權。

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
