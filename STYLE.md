<a id="style-guide-for-powershell-docs" class="xliff"></a>
# PowerShell-Docs 的樣式指南


<a id="titlesheadings" class="xliff"></a>
## 標題/標頭

* 標題/標頭 (任何在前方加上 \# 的項目) 後方應接著新行字元
* 只有標題及該標題中所有專有名詞的第一個字母才應大寫
* 每個文件只能有一個 H1
* 編輯參考內容時，H2 是由 platyPS 所指定，且不應新增或移除，因為那會導致建置中斷
* 僅使用 \# 樣式標頭 (而非 = 或 \- 樣式標頭)

<a id="correct" class="xliff"></a>
### 正確

```
# Header 1

## Header 2

### Header 3

```

<a id="incorrect" class="xliff"></a>
### 錯誤

```
Header 1
========

Header 2
--------

### Header 3
```

<a id="syntax" class="xliff"></a>
## 語法

* 在段落中說明 Cmdlet 時，請使用 \` 以將 Cmdlet 名稱醒目提示
  * 正確的範例：這個 `Write-Host` Cmdlet 可以 ...
  * 不正確的範例：這個 **Write-Host** Cmdlet 可以 ... 並以管線方式處理至 out-file Cmdlet 以 ...
* 撰寫文章 (而非撰寫參考內容) 時，第一個 Cmdlet 名稱實例應該是該 Cmdlet 文件的連結
* 所有的 PowerShell 語法區塊都應該使用 &#96;&#96;&#96;powershell
* PowerShell 命令的開頭請勿使用 "`PS C:\>`"
  * 正確的範例：
  ```powershell
  Get-Process
  ```
  * 不正確的範例：
  ```powershell
  PS C:\> Get-Process
  ```
* PowerShell 命令發出的輸出應該加上註解，以防止它接收語法醒目提示
* 屬性名稱和參數名稱應使用「粗體」
* PowerShell Cmdlet 使用「[帕斯卡命名法 (英文)](https://en.wikipedia.org/wiki/PascalCase)」。 使用連字號分隔動詞和名詞。

<a id="lists" class="xliff"></a>
## 清單

* 清單的結尾請勿使用句號 (除非它們包含多個句子)
* 如果您的清單包含多個句子，請考慮在您的主要想法下使用標頭 3/4/5 (視情況而定)

<a id="links" class="xliff"></a>
## 連結

* 連結一律使用 MarkDown 語法 `[friendlyname](url)` 標記
* 連結應視情況提供易記名稱，通常是所連結之頁面的標題
  * **例外狀況**：非 Microsoft 網站的連結應只使用 URL
* 位於底部＜相關連結＞一節中的所有項目，都應該是超連結。 

<a id="line-breaks" class="xliff"></a>
## 分行符號

* 您必須包含語意分行符號
* 您應該將行的長度限制為 100 個字元 (開放項目：協助我們驗證此項目的工具)
* 您「可以」移除 PS4 及更新版本的額外分行符號，但針對 ps3 則「不可以」(需要驗證)
