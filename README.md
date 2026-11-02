# 筆記印刷機

把 Markdown 筆記排成跟 TwinMind 一樣的版面（同樣的字色、表格、引言、程式碼區塊），自動分頁，存成 PDF 放進 GoodNotes，或存成 EPUB 放進電子閱讀器。

整個工具只有一個 `index.html`，在瀏覽器裡執行，筆記不會上傳到任何伺服器。

## 功能

- 即時預覽，自動分頁；表格太長會帶著表頭接到下一頁，標題不會孤零零留在頁尾
- 頁面尺寸：A4（GoodNotes、列印）、3:4（iPad 全螢幕、Kindle Scribe、reMarkable、Boox 10.3 吋）、6–7 吋電子書（Kindle、Kobo）
- 字級四段、配色三種（原色、純白、電子紙高對比）、頁碼開關
- 「製作 PDF」：每頁跟預覽一模一樣；iPad 上可以直接分享到 GoodNotes
- 「列印／存成可選取文字的 PDF」：用瀏覽器列印存檔，文字可以搜尋、選取
- 「製作 EPUB 電子書」：在閱讀器裡重新排版、可以調字級，每個 📌 段落是一章，有目錄；Kindle 用 Send to Kindle，Kobo、Boox 直接放進去；可選擇拿掉 emoji
- 貼上的內容裡有 `~~~~markdown` 區塊時，只取區塊裡面的內容；整則回答全選複製也可以
- 從網頁複製有格式的內容會自動轉回 Markdown；純文字會依 📌 這類符號推測標題（表格救不回來）

## 放到 GitHub Pages（用 iPad 也能做）

1. 登入 [github.com](https://github.com)，右上角 **＋** → **New repository**。名稱例如 `notepress`，選 **Public**，按 **Create repository**。
2. 在新的 repo 頁面點 **uploading an existing file**，把 `index.html`（和這份 `README.md`）選進去，按 **Commit changes**。
3. 進 **Settings** → 左側 **Pages** → Source 選 **Deploy from a branch**，Branch 選 **main**、資料夾 **/ (root)**，按 **Save**。
4. 等一兩分鐘，網址會是 `https://你的帳號.github.io/notepress/`。在 Safari 按分享 → **加入主畫面**，就會像一個 App。

之後要更新工具，只要在 repo 裡打開 `index.html` → 右上角 **⋯** → **Upload files** 覆蓋同名檔案即可。

## 讓 TwinMind 同時給好看的版面和 Markdown

把這段加進 TwinMind 的個人化設定：

```
當我請你整理筆記、摘要或課堂重點時：
1. 先照平常的方式完整回答，正常顯示排版。
2. 回答最後另起一行寫「📋 Markdown 原始碼（複製用）」，接著把上面整份內容原封不動放進一個程式碼區塊：第一行寫 ~~~~markdown，最後一行寫 ~~~~。
3. 程式碼區塊裡的內容要和上方一字不差，保留所有標題、emoji、清單、表格（用 | 語法）和程式碼區塊，不要省略、不要另外加說明。
一般閒聊或簡短問答不用附原始碼。
```

之後複製回答最後的區塊（或整則回答）貼進工具就好。

## 使用的開源套件

都從 CDN 載入：[marked](https://github.com/markedjs/marked)、[JSZip](https://github.com/Stuk/jszip)、[DOMPurify](https://github.com/cure53/DOMPurify)、[Turndown](https://github.com/mixmark-io/turndown)、[html2canvas](https://github.com/niklasvh/html2canvas)、[jsPDF](https://github.com/parallax/jsPDF)。
