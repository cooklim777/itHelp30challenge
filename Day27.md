Day27 RPA 是什麼？ 和 Make.com 的比較

### RPA（機器人流程自動化）

旨在自動化重複性的業務流程，通常是在電腦系統的前端進行操作。像資料輸入、檔案整合、訂單處理等等這類日常任務。RPA 軟體可以被訓練來模仿人類操作應用程式介面（API）和圖形使用者介面（GUI），來完成這些任務。

RPA 和這些工作流程最大的差異是他**不仰賴 API 的串接**（當然若串接簡單也可以使用 API 串接），他可以直接操作你的滑鼠和鍵盤，來操作你的桌面軟體，或是到**各個網站做自動化**，有些網站因為安全性或其他考量，並非都有開放 API 這時候就能使用 RPA 來達成自動化效果。

而且 RPA 不只是有操控網站、桌面軟體的能力，多數的 RPA 軟體都整合各個功能，例如操作 excel、google sheet、壓縮等等的功能，可以想成他是工作流程自動化工具的加強版，他可以串接 API 但並非完全 focus 在這一塊。

而也因為操作網站和地端軟體是較難的技術，且開發維護成本較高一點，所以通常是由企業才用，而訂閱費差距也蠻大的，例如微軟的 Power Automation 約 4000 一個月，而 UiPath 約 7000 一個月，當然也有很多種定價，根據不同的方案。

查詢後發現，欸怎麼變便宜了，跟之前看到的不太相同，那發現是他們現在又把產品更細分化，看到最便宜的方案也大概每個月 400，那其實這些方案就是我們所說的工作流程自動化，就是類似 Make, Zapier 的功能，而沒有包括能夠操作桌面軟體的部分。
我猜想這是為了先吸引一些想自動化的人，那之後發現又有新問題後，加價可以解決，藉此吸引客戶。
![https://ithelp.ithome.com.tw/upload/images/20241005/20169163SRINHrW6lr.png](https://ithelp.ithome.com.tw/upload/images/20241005/20169163SRINHrW6lr.png)
![https://ithelp.ithome.com.tw/upload/images/20241005/20169163JWFffss1AT.png](https://ithelp.ithome.com.tw/upload/images/20241005/20169163JWFffss1AT.png)

還有 RPA 通常是有落地的方案，能夠不連網在企業中，也達到資安的要求，當然不連網就不能使用呼叫外部 API 等等的功能。

RPA 工具的選擇通常基於其功能、整合能力、安全性和可擴展性等因素。而 Make.com 或主要使用在特定的功能、SASS 服務。

若你的需求可能是**規模較小的網站（沒有 API 或是流程自動化平台沒串接）自動化、或是內部的網站系統、地端的軟體**，就得考慮使用 RPA 來達成自動化的效果。

參考：
[Power Automate 價格方案](https://www.microsoft.com/zh-tw/power-platform/products/power-automate/pricing#tabs-pill-bar-ocd242_tab0)
[UiPath 價格方案](https://www.uipath.com/pricing)

---

若對 MAKE 自動化 有興趣的歡迎使用以下連結註冊，可以直接得到免費一個月的 pro 會員資格（不需要綁定信用卡等，只需使用該連結註冊而已）
[免費一個月 pro 會員](https://www.make.com/en/register?pc=automateyoureverydayhttps://www.make.com/en/register?pc=automateyoureveryday)
