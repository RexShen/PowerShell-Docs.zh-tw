---
title: PowerShell-Docs 樣式指南
description: 此文章提供撰寫 PowerShell 文件的樣式規則。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 32df641f7cafa2a5bfcf1bcbf94be594aa77c7d0
ms.sourcegitcommit: 105c69ecedfe5180d8c12e8015d667c5f1a71579
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85837438"
---
# <a name="powershell-docs-style-guide"></a>PowerShell-Docs 樣式指南

此文章提供 PowerShell-Docs 內容專屬的樣式指導方針。 這是根據[概觀](overview.md#get-started-writing-docs)中所述的資訊來建置的。

## <a name="product-terminology"></a>產品術語

PowerShell 有好幾種變體。

- **PowerShell** - 這是預設值。 我們認為 PowerShell 7 及往後版本將是真正的 PowerShell。
- **PowerShell Core** - 以 .NET Core 為基礎建置的 PowerShell。 使用 **Core** 一詞應該僅限於需要與 Windows PowerShell 區別的情況。
- **Windows PowerShell** - 以 .NET Framework 為基礎建置的 PowerShell。 Windows PowerShell 只隨附於 Windows，而且需要完整的 Framework。

  一般而言，文件中提及 "Windows PowerShell" 時可以代換為 "PowerShell"。
  當討論特定於 "Windows PowerShell" 的行為時，應該使用 "Windows PowerShell"。

相關產品

- **Visual Studio Code (VS Code)** - 這是 Microsoft 的免費開放原始碼編輯器。 第一次提及時，應使用完整名稱。 之後，您可以使用 **VS Code**。 請勿使用 "VSCode"。
- **適用於 Visual Studio Code 的 PowerShell 擴充功能** - 擴充功能會將 VS Code 轉換為適合 PowerShell 的 IDE。 第一次提及時，應使用完整名稱。 之後，您可以使用 **PowerShell 擴充功能**。
- **Azure PowerShell** - 這是用來管理 Azure 服務的 PowerShell 模組集合。
- **Azure Stack PowerShell** - 這是用來管理 Microsoft 混合式雲端解決方案的 PowerShell 模組集合。

## <a name="markdown-specifics"></a>Markdown 細節

建置文件的 Microsoft Open Publishing System (OPS) 會使用 [markdig][] 來處理 Markdown 文件。 Markdig 會根據最新的 [CommonMark][] 規格的規則來剖析文件。

新的 CommonMark 規格對某些 Markdown 元素的建構要嚴格得多。 請密切注意此文件中提供的詳細資料。

### <a name="blank-lines-spaces-and-tabs"></a>空白行、空格與定位字元

空白行也表示 Markdown 中區塊的結尾。 不同類型的 Markdown 區塊之間應該有一個空白 (例如，段落與清單或標題之間)。

移除重複的空白行。 多個空白行會轉譯為 HTML 中的單一空白行，因此多個空白行沒有用途。 程式碼區塊內的多個空白行會中斷程式碼區塊。

移除行結尾多餘的空格。

> [!NOTE]
> 間距在 Markdown 中很重要。 一律使用空格，而不是固定定位字元。 尾端空白可以變更 Markdown 轉譯的方式。

### <a name="titles-and-headings"></a>標題 (Title) 與標題 (Heading)

僅使用 [ATX 標題][atx] (# 樣式，而非 `=` 或 `-` 樣式標頭)。

- 使用句子大小寫 - 僅專有名詞與標題或標頭的第一個字母應為大寫
- `#` 與標題的第一個字母之間必須有一個空格
- 標題應該以一條空白行括住
- 每個文件只能有一個 H1
- 標頭層級應該以 1 遞增。 請勿跳級
- 請勿在標頭中使用粗體或其他標記

### <a name="limit-line-length-to-100-characters"></a>將行長度限制為 100 個字元

這適用於概念性文章與 Cmdlet 參考。 限制行長度可改善 git 差異與歷程記錄的可讀性。 這也可以讓其他作者更輕鬆地做出貢獻。

使用 Visual Studio Code 中的 [Reflow Markdown][reflow] 延伸模組，輕鬆地重排段落以符合指定的行長度。

About_topics 限制為 80 個字元。 如需更具體的資訊，請參閱[編輯參考文章](./editing-cmdlet-ref.md#formatting-about_-files)。

### <a name="lists"></a>清單

如果您的清單包含多個句子或段落，請考慮使用子層級標頭，而不是清單。

清單應以單一空白行括住。

#### <a name="unordered-lists"></a>未排序清單

請勿在清單項目的結尾使用句號 (除非它們包含多個句子)。 針對清單項目的項目符號使用連字號字元 (`-`)。 這樣可以避免與使用星號 [`*`] 的粗體或斜體標記混淆。 若要在項目符號項目下包含段落或其他元素，請插入分行符號，並與項目符號後面的第一個字元縮排對齊。

例如：

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

這是一個清單，其中包含項目符號項目下的子元素。

- 第一個項目符號項目

  說明第一個項目符號的句子。

  - 子項目符號項目

    說明子項目符號的句子。

- 第二個項目符號項目
- 第三個項目符號項目

#### <a name="ordered-lists"></a>已排序清單

若要在編號項目底下包含段落或其他元素，請與項目編號後的第一個字元縮排對齊。 列出的所有編號項目都應該使用數字 `1.`，而不是遞增每個項目。 Markdown 轉譯會自動增加值。 這會讓重新排列項目變得更容易，並標準化附屬內容的縮排。

例如：

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

產生的 Markdown 會轉譯如下：

1. 針對第一個元素，在 1 之後插入單一空格。 長句子應該換行到下一行，而且必須與編號清單標記後面的第一個字元對齊。

   若要包含第二個元素 (例如這個)，在第一個之後插入分行符號並對齊縮排。 第二個元素的縮排必須與編號清單標記後面的第一個字元對齊。 針對單位數項目 (例如此處)，您必須縮排到第 4 欄。 若為雙位數項目 (例如項目編號 10)，則必須縮排到第 5 欄。

1. 下一個編號項目會從這裡開始。

### <a name="images"></a>影像

包含影像的語法為：

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

其中 `alt text` 是影像的簡短描述，而 `<folder path>` 是影像的相對路徑。 視障人士的螢幕助讀程式需要替代文字。 如果存在無法轉譯影像的網站錯誤 (Bug)，這也很有用。

影像應儲存在包含文章之資料夾內的 `media/<article-name>` 資料夾中。
不應在文章之間共用影像。 在 `media` 資料夾底下，建立符合您文章檔案名稱的資料夾。 將該文章的影像複製到該新資料夾。 如果某個影像由多個文章使用，每個影像資料夾都必須有該影像檔案的複本。 這種做法可防止變更一篇文章中的影像而影響另一篇文章。

支援下列影像檔案類型：`*.png`、`*.gif`、`*.jpeg`、`*.jpg`、`*.svg`

### <a name="markdown-extensions-supported-by-open-publishing"></a>Open Publishing 支援的 Markdown 延伸模組

[Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) 包含支援我們發佈系統特有功能的工具。 警示是 Markdown 擴充功能，用來建立在 docs.microsoft.com 上轉譯的區塊引述，並以色彩與圖示醒目提示內容的重要性。 支援下列警示類型：

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

這些警示在 docs.microsoft.com 上看起來像這樣：

附註區塊

> [!NOTE]
> 即使略讀，使用者也應該注意的資訊。

提示區塊

> [!TIP]
> 可協助使用者更成功的選擇性資訊。

重要區塊

> [!IMPORTANT]
> 使用者成功所需的基本資訊。

注意區塊

> [!CAUTION]
> 動作的潛在負面後果。

警告區塊

> [!WARNING]
> 動作的危險特定結果。

### <a name="hyperlinks"></a>超連結

- 超連結必須使用 Markdown 語法 `[friendlyname](url-or-path)`
- 連結應盡可能使用 HTTPS。
- 連結必須具有易記名稱，通常是連結主題的標題
- 位於底部＜相關連結＞一節中的所有項目，都應該是超連結
- 請勿在超連結的括弧內使用倒引號、粗體或其他標記。
- 當您在談論特定的 URI 時，可能會使用裸 URL。 URI 必須括在倒引號中。 例如：

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a>連結至其他內容

發佈系統支援兩種類型的超連結：

**URL 連結**可以是相對於 docs.microsoft.com 根目錄的 URL 路徑。 或包含完整 URL 語法的絕對 URL。 例如： `https:/github.com/MicrosoftDocs/PowerShell-Docs`

- 連結至 PowerShell-Docs 以外的內容，或在 Cmdlet 參考與 PowerShell-docs 中的概念性文章之間連結時，請使用 URL 連結。建立相對連結最簡單的方式是從瀏覽器複製 URL，然後從您貼到 Markdown 的值中移除 `https://docs.microsoft.com/en-us`。
- 請勿在 Microsoft 內容的 URL 中包含地區設定 (例如， 從 URL 中移除 `/en-us`)。
- 除非您需要連結至文章的特定版本，否則請從 URL 移除任何非必要的查詢參數。 範例：
  - `?view=powershell-5.1` - 這是用來連結至 PowerShell 的特定版本
  - `?redirectedfrom=MSDN` - 當您從舊文章重新導向至其新位置時，會將此參數新增至 URL
- 針對外部網站的所有 URL 都應該使用 HTTPS，除非目標網站不適用。

**檔案連結**是用來從一篇參考文章連結至另一篇，或從某篇概念性文章連結至另一篇。 如果您需要連結至 PowerShell 特定版本的參考文章，則必須使用 URL 連結。

- 檔案連結包含相對檔案路徑 (例如：`../folder/file.md`)
- 所有檔案路徑都使用正斜線 (`/`) 字元

URL 和檔案連結上都允許深層連結。 將錨點新增至目標路徑的結尾。
例如：

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

如需詳細資訊，請參閱[在文件中使用連結](/contribute/how-to-write-links)。

## <a name="formatting-command-syntax-elements"></a>設定命令語法元素格式

- 請一律使用 Cmdlet 與參數的完整名稱。 除非您特別示範別名，否則請避免使用別名。

- 屬性、參數、物件、類型名稱、類別名稱、類別方法應為**粗體**。
  - 屬性與參數值應括在倒引號 (`` ` ``) 中。
  - 使用括弧樣式提及類型時，請使用倒引號。 例如： `[System.Io.FileInfo]`

- 語言關鍵字、Cmdlet 名稱、函式、變數、原生 EXE、檔案路徑與內嵌語法範例都應該以倒引號 (`` ` ``) 字元括住。

  例如：

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - 依名稱參考參數時，名稱應為**粗體**。 在說明使用連字號前置詞的參數時，應將參數包裝在倒引號中。 例如：

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - 顯示外部命令的範例使用方式時，應將該範例包裝在倒引號中。
    一律在原生命令中包含副檔名。 例如：

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    包含副檔名可確保系統會根據 PowerShell 的命令優先順序執行正確命令。

- 撰寫概念性文章 (而非撰寫參考內容) 時，第一個 Cmdlet 名稱執行個體必須能以超連結方式連到該 Cmdlet 文件。 請勿在超連結的括弧內使用倒引號、粗體或其他標記。

  例如：

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  如需詳細資訊，請參閱此文章的[超連結](#hyperlinks)一節。

## <a name="markdown-for-code-samples"></a>程式碼範例的 Markdown

Markdown 支援兩種不同的程式碼樣式：

- **程式碼範圍 (內嵌)** - 以單一倒引號 (`` ` ``) 字元標記。 用於段落內，而不是作為獨立區塊。
- **程式碼區塊** - 以三倒引號 (`` ``` ``) 字串括住的多行區塊。 程式碼區塊在倒引號之後可能也會有語言標籤。 語言標籤會針對程式碼區塊的內容啟用語法醒目提示。

所有程式碼區塊都應該包含在程式碼柵欄中。 針對程式碼區塊一律不使用縮排。 Markdown 允許此模式，但可能會有問題，應予以避免。

程式碼區塊是以三倒引號 (`` ``` ``) 程式碼柵欄括住的一或多行程式碼。
程式碼柵欄標記本身必須位於程式碼範例前後的一行中。 程式碼區塊開頭的標記可能會有選擇性的語言標籤。 Microsoft 的 Open Publishing System (OPS) 使用語言標籤來支援語法醒目提示功能。

如需所支援語言標記的完整清單，請參閱集中式參與者指南中的[加上柵欄的程式碼區塊](/contribute/code-in-docs#fenced-code-blocks)。

OPS 也新增了 [複製]  按鈕，可將程式碼區塊的內容複製到剪貼簿。 這可讓您快速地將程式碼貼到指令碼中，以測試程式碼範例。 不過，並非文件中的所有範例都是可依原樣執行的。 某些程式碼區塊是 PowerShell 概念的簡單圖解。

我們的文件中使用了三種類型的程式碼區塊：

1. 語法區塊
1. 說明範例
1. 可執行檔範例

### <a name="syntax-code-blocks"></a>語法程式碼區塊

語法程式碼區塊是用來描述命令的語法結構。 請勿在程式碼柵欄使用語言標籤。 此範例說明 `Get-Command` Cmdlet 的所有可能參數。

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

此範例以一般字詞描述 `for` 陳述式：

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a>說明範例

說明範例是用來說明 PowerShell 概念。 它們不應該複製到剪貼簿來執行。 這些最常用於容易輸入且容易了解的簡單範例。 程式碼區塊可以包含 PowerShell 提示字元與範例輸出。

以下是說明 PowerShell 比較運算子的簡單範例。 在此案例中，我們不希望讀者複製並執行此範例。

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS>  1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a>可執行的範例

複雜範例或目的是用來複製並執行的範例，應使用下列區塊樣式標記：

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

PowerShell 命令所顯示的輸出應該包含在 **Output** 程式碼區塊中，以避免語法醒目提示。 例如：

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

**Output** 程式碼標籤不是語法醒目提示系統所支援的官方「語言」。
不過，此標籤很有用，因為 OPS 會將 "Output" 標籤新增至網頁上的程式碼方塊框架。 "Output" 程式碼方塊沒有語法醒目提示。

## <a name="coding-style-rules"></a>程式碼撰寫樣式規則

### <a name="avoid-line-continuation-in-code-samples"></a>避免程式碼範例中的行接續

避免在 PowerShell 程式碼範例中使用行接續字元 (`` ` ``)。 這些字元很難看到，如果行尾有多餘的空格，可能會造成問題。

- 使用 PowerShell 展開來減少具有大量參數之 Cmdlet 的行長度。
- 利用 PowerShell 的自然換行機會，像是管道 (`|`) 字元、左括弧、括弧和方括弧之後。

### <a name="avoid-using-powershell-prompts-in-examples"></a>避免在範例中使用 PowerShell 提示字元

不建議使用提示字元字串，而且應該僅限於用來說明命令列使用方式的情節。 對於大多數這些範例，提示字元字串應該為 `PS>`。 這個提示字元與 OS 特有的指標無關。

如需說明會改變提示字元的命令，或顯示的路徑對所示案例很重要的範例，則需要提示字元。 下列範例說明當使用登錄提供者時，提示字元的變更方式。

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="do-not-use-aliases-in-examples"></a>請勿在範例中使用別名

除非您特別討論別名，否則請一律使用所有 Cmdlet 與參數的完整名稱。 Cmdlet 與參數名稱必須使用正確的 Pascal 大小寫格式名稱。

### <a name="using-parameters-in-examples"></a>在範例中使用參數

避免使用位置參數。 一般來說，即使是位置參數，您也應該一律在範例中包含參數名稱。 這可減少您的範例中產生混淆的機會。

## <a name="next-steps"></a>後續步驟

[編輯 Cmdlet 參考](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
