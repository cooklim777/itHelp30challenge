Day06 如何註冊 Make.com 帳戶、頁面簡介

可以直接點選以下連結註冊，可使用 Google, Facebook, Github 直耶第三方登入。
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)

Hosting Region 可以選擇 US 或 EU，這個之後無法更改，若是台灣用戶建議選擇 US，還是相對較近一點，連線還是會較快速。

登入後到 make.com 的首頁
![https://ithelp.ithome.com.tw/upload/images/20240911/20169163OUcSiS5Vza.png](https://ithelp.ithome.com.tw/upload/images/20240911/20169163OUcSiS5Vza.png)

左上方有工作區的選擇，我們主要 focus 在個人，且需要較高級的方案才能創造更多工作區，這主要目的是要讓企業的不同部門的使用者分到不同的工作區，控制資料、流程的權限。

而面板上最主要是有你的方案，和使用量，和執行中的 scenario 場景數量。這些在 free 權限下，每個月場景可以同時開啟兩個，而使用量為 1000。

那來介紹一下什麼是 scenario 場景、模組、operations

##### **scenario 場景**：

每個場景都是一個自動化工作流程，由一系列的操作模組組成，用來完成特定的任務或達成某種目標。可以將 Scenario 理解為一個完整的自動化「劇本」，它包含了從觸發器開始到最後執行各種動作的整個過程。

- **可視化設計**：Scenario 通常使用直觀的拖放介面來設計，用戶可以通過將不同的模組串聯起來，設計出複雜的自動化流程。
- **觸發器**：每個 Scenario 都從一個觸發器開始，觸發器是用來啟動這個場景的條件。例如，可以設置在收到新電子郵件時觸發、API 觸發、手動觸發、時間觸發等等。
- **模組連接**：在觸發器之後，Scenario 會依次執行各種操作，這些操作由模組來執行。模組之間可以傳遞資料，形成完整的流程。
- **條件和分支**：Scenario 支持在流程中加入條件和分支，讓你可以根據不同的情況執行不同的操作，提升自動化流程的靈活性。

##### **module 模組**

module 是 Scenario 中的具體動作或步驟，例如去抓取某個 google sheet 的欄位，使用到 Google sheet 的模組。

##### **Operations**

主要是計算你的花費使用

- **單位執行**：每個操作通常是一個單一的動作，如創建一條新資料、發送電子郵件、更新數據庫等。

- **模組操作**：Operations 是由模組（Modules）來執行的，每個模組可以有多種不同的操作類型。例如，Gmail 模組可以執行的操作包括發送郵件、標記郵件等。

- **消耗計量**：在 Make 的計價模型中，每執行一次操作都會計算為一次 Operations。當 Scenario 越複雜，所需的操作次數也越多，這會影響到你的資源使用量和計費情況。

operations 跟 module 有點雷同，但有些些微的差異，而舉一個例子：有個流程要幫我將 google sheet 的客戶資料同步到 notion 中，假設現在有新的 10 個客戶，我要做的是
得到資料 > 做迭代（將資料一比一比送進 notion）> notion 新建資料
而這其中包含的模組就是 google sheet、迭代、notion，但使用到的 operation 不是 3 個，因為有迭代所以是 1+10+1 共 12 個 operations。
可能會發現這樣消耗的 operation 好像蠻大的，這部分要看是什麼流程，若你的資料是很多筆，且要迭代，這確實可能是個問題，但也有一些進階技巧能夠讓你的 operation 降低，但是能達到同樣的事情，這之後也會做一些介紹。

---

再看一次這張圖
![https://ithelp.ithome.com.tw/upload/images/20240911/20169163OUcSiS5Vza.png](https://ithelp.ithome.com.tw/upload/images/20240911/20169163OUcSiS5Vza.png)
上方有一些選項，也簡單介紹一下，TEAMS 和 USERS 就是多帳號時公司管理可以使用，而 SUBSCRIPTION、PAYMENTS 就是訂閱方案的內容，若是個人應該只會使用到 Core 方案，就能夠有一個月 10000 operation 的額度，且只需要 9 美金，另外可存的量變成 100MB，啟動的場景也沒有限制。

再來是 INSTALLED APPS 是別人開發一些組合的模組，或是原本 make 上沒有串接的服務，讓你更方便使用，就有點像是遊戲中的插件，是由其他玩家開發的，例如 [make.fan 的自動化模組](https://make.fan/operation-store/)就是有一些特別的模組功能。

VARIABLES 是變數的設置，這個要升級到 Pro 方案才會有，主要就是全域變數的設置，若你的流程很多，有時候設定全域變數，需要更改某個變數時可以一起更改，會比較快速。

明天應該就能夠進入場景的建置

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
