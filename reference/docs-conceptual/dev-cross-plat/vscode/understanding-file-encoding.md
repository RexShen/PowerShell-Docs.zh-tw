---
title: 了解 VS Code 及 PowerShell 中的檔案編碼
description: 設定 VS Code 及 PowerShell 中的檔案編碼
ms.date: 02/28/2019
ms.openlocfilehash: afad189ff20a4e73d25f15c48d6c4982b18f29a3
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142543"
---
# <a name="understanding-file-encoding-in-vs-code-and-powershell"></a>了解 VS Code 及 PowerShell 中的檔案編碼

使用 VS Code 建立和編輯 PowerShell 指令碼時，請務必使用正確的字元編碼格式來儲存檔案。

## <a name="what-is-file-encoding-and-why-is-it-important"></a>什麼是檔案編碼，以及它為何如此重要？

VS Code 會管理緩衝區中人工輸入的字元字串與檔案系統位元組之讀取/寫入區塊間的介面。 當 VS Code 儲存檔案時，其會使用文字編碼來決定每個字元會變成多少位元組。 如需詳細資訊，請參閱 [about_Character_Encoding](/powershell/module/microsoft.powershell.core/about/about_character_encoding)。

同樣地，當 PowerShell 執行指令碼時，它必須將檔案中的位元組轉換成字元，以在 PowerShell 程式中重建檔案。 因為 VS Code 寫入檔案，而 PowerShell 讀取檔案，所以兩者需要使用相同的編碼系統。 這個剖析 PowerShell 指令碼的程序為： _位元組_ -> _字元_ -> _權杖_ -> _抽象語法樹_ -> _執行_ 。

VS Code 與 PowerShell 都使用合理的預設編碼設定來安裝。 不過，PowerShell 使用的預設編碼已隨著 PowerShell Core (v6.x) 發行而變更。 為確保在 VS Code 中使用 PowerShell 或 PowerShell 擴充功能時沒有任何問題，您需要正確設定 VS Code 與 PowerShell 設定。

## <a name="common-causes-of-encoding-issues"></a>編碼問題常見原因

當 VS Code 或指令碼檔案編碼不符 PowerShell 的預期編碼時，會發生編碼問題。 PowerShell 無法自動判斷檔案編碼。

使用非 [7 位元 ASCII 字元集](https://ascii.cl/)字元時，最可能發生編碼問題。 例如：

<!-- markdownlint-disable MD038 -->
- 擴充的非字母字元，例如長破折號 (`—`)、不分行空格 (` `) 或左雙引號 (`"`)
- 有重音符號的拉丁字元 (`É`、`ü`)
- 斯拉夫文等非拉丁字元 (`Д`、`Ц`)
- CJK 字元 (`本`、`화`、`が`)

編碼問題的常見原因如下：

- 未變更 VS Code 與 PowerShell 的預設編碼。 PowerShell 5.1 與之前的版本，其預設編碼與 VS Code 不同。
- 另一個編輯器已開啟，並以新的編碼覆寫檔案。 這通常發生在 ISE。
- 檔案已簽入與 VS Code 或 PowerShell 預期不同之編碼的原始程式碼控制中。 當共同作業者使用不同編碼設定的編輯器時，就會發生這種情況。

### <a name="how-to-tell-when-you-have-encoding-issues"></a>如何分辨發生編碼問題

編碼錯誤通常會顯示為指令碼的剖析錯誤。 如果您發現指令碼中有奇怪的字元序列，這可能就是問題。 在下列範例中，短破折號 (`–`) 顯示為字元 `â&euro;"`：

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â&euro;"From $from â&euro;"To $recipient1 â&euro;"Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

此問題發生的原因是 VS Code 將 `–` 字元以 UTF-8 編碼為位元組 `0xE2 0x80 0x93`。 當這些位元組解碼為 Windows-1252 時，它們就會解譯為字元 `â&euro;"`。

您可能看到的一些奇怪字元序列包括：

<!-- markdownlint-disable MD038 -->
- `â&euro;"`，而非`–`
- `â&euro;"`，而非`—`
- `Ã„2`，而非`Ä`
- `Â`，而非 ` ` (不分行空格)
- `Ã&copy;`，而非`é`
<!-- markdownlint-enable MD038 -->

這份方便的[參考](https://www.i18nqa.com/debug/utf8-debug.html)列出指出 UTF-8/Windows-1252 編碼問題的常見模式。

## <a name="how-the-powershell-extension-in-vs-code-interacts-with-encodings"></a>VS Code 中的 PowerShell 擴充功能如何與編碼互動

PowerShell 延伸模組與指令碼互動的幾種方式：

1. 使用 VS Code 編輯指令碼時，VS Code 就會將內容傳送至擴充功能。 [語言伺服器通訊協定][]規定使用 UTF-8 傳送此內容。 因此，延伸模組不可能取得錯誤的編碼。
1. 當指令碼直接在整合式主控台中執行時，PowerShell 會直接從檔案讀取它們。 如果 PowerShell 的編碼與 VS Code 的編碼不同，這裡就會出錯。
1. 當使用 VS Code 開啟之指令碼參考另一個非以 VS Code 開啟的指令碼時，擴充功能會回復成從檔案系統載入該指令碼內容。 PowerShell 延伸模組預設為 UTF-8 編碼，但會使用[位元組順序標記][] (或稱 BOM) 偵測選取正確的編碼。

假設編碼無 BOM 格式時，就會發生問題 (例如 [UTF-8][] 不使用 BOM 和 [Windows-1252][])。 PowerShell 延伸模組預設使用 UTF-8。 擴充功能不能變更 VS Code 的編碼設定。 如需詳細資訊，請參閱[問題 #824](https://github.com/Microsoft/VSCode/issues/824)。

## <a name="choosing-the-right-encoding"></a>選擇正確的編碼

不同的系統和應用程式可以使用不同編碼：

- 在 .NET Standard (網路) 和 Linux 環境中，UTF-8 目前是主流編碼。
- 許多 .NET Framework 應用程式使用 [UTF-16][]。 基於歷史原因，這有時稱為 "Unicode"，這個詞彙現在意指包含 UTF-8 和 UTF-16 的廣義[標準](https://en.wikipedia.org/wiki/Unicode)。
- 在 Windows 中，許多比 Unicode 更早的原生應用程式，根據預設仍繼續使用 Windows-1252。

Unicode 編碼方式也有位元組順序標記 (BOM) 的概念。 BOM 發生在文字的開頭，告訴解碼器該文字使用哪種編碼。 針對多位元組編碼，BOM 也會指出編碼的[字節順序](https://en.wikipedia.org/wiki/Endianness)。 BOM 設計為很少出現在非 Unicode 文字中的位元組，在有 BOM 時，讓人合理猜測文字是 Unicode。

BOM 為選擇性，且使用情況不像在 Linux 環境中那麼熱門，因為各處普遍使用可靠的 UTF-8 慣例。 大部分的 Linux 應用程式假設文字輸入使用 UTF-8 編碼。 雖然許多 Linux 應用程式會辨識並正確處理 BOM，但也有很多不能，以致要使用這些應用程式操作文字中的成品。

**因此** ：

- 如果您主要使用 Windows 應用程式和 Windows PowerShell，您應該會比較偏好使用 BOM 的 UTF-8 或 UTF-16 這類編碼。
- 如果您跨平台工作，您應該會偏好使用 BOM 的 UTF-8。
- 如果您主要是在與 Linux 相關聯的環境中工作，您應該會偏好不使用 BOM 的 UTF-8。
- Windows-1252 和拉丁文-1 基本是舊版的編碼，如果可能，應該避免。
  不過，有些較舊的 Windows 應用程式可能依賴它們。
- 另外值得一提的是，指令碼簽署為[編碼相依](https://github.com/PowerShell/PowerShell/issues/3466)，這表示變更已簽署指令碼的編碼將需要重新簽署。

## <a name="configuring-vs-code"></a>設定 VS Code

VS Code 的預設編碼為不使用 BOM 的 UTF-8。

若要設定 [VS Code 的編碼][]，請移至 VS Code 設定 (<kbd>Ctrl</kbd>+<kbd>,</kbd>)，並設定 `"files.encoding"` 設定：

```json
"files.encoding": "utf8bom"
```

可能的值為：

- `utf8`:[UTF-8] 不使用 BOM
- `utf8bom`:[UTF-8] 使用 BOM
- `utf16le`:位元組由小到大的 [UTF-16]
- `utf16be`:位元組由大到小的 [UTF-16]
- `windows1252`:[Windows-1252]

您應該會在 GUI 檢視中取得它的下拉式清單，或在 JSON 檢視中自動完成它。

您也可以在有可能時，將下列項目新增至自動偵測編碼：

```json
"files.autoGuessEncoding": true
```

如果您不希望這些設定影響所有檔案類型，VS Code 也允許遵循個別語言設定。 將設定放入 `[<language-name>]` 欄位，建立語言特定設定。 例如：

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

建議您考慮安裝適用於 Visual Studio Code 的 [Gremlins 追蹤器][]。 此延伸模組會顯示某些容易損毀的 Unicode 字元，因為其不可見或是看起來像其他一般字元。

## <a name="configuring-powershell"></a>設定 PowerShell

PowerShell 的預設編碼隨版本而異：

- 在 PowerShell 6+ 中，所有平台的預設編碼都是不使用 BOM 的 UTF-8。
- 在 Windows PowerShell 中，預設編碼通常是 Windows-1252，即[拉丁文-1][] 的延伸模組，也稱為 ISO 8859-1。

在 PowerShell 5+ 中，您可以使用下列內容找到您的預設編碼：

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

下列[指令碼](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e)可用來判斷 PowerShell 工作階段會針對不使用 BOM 的指令碼推斷何種編碼。

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

您可以使用設定檔設定，設定 PowerShell 更廣泛使用指定的編碼。
查看下列文章：

- StackOverflow 上有關 PowerShell 編碼之 [@mklement0] 的[解答](https://stackoverflow.com/a/40098904)。
- 在 PowerShell 中處理無 BOM UTF-8 輸入之 [@rkeithhill][ 的部落格文章](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)。

您無法強制 PowerShell 使用特定的輸入編碼。 在地區設定為 en-us 的 Windows 上執行 PowerShell 5.1 及更低版本時，如果沒有 BOM，則預設會使用 Windows-1252 編碼。 其他地區設定可能會使用不同的編碼。 為確保互通性，最好使用 BOM 來儲存 Unicode 格式的指令碼。

> [!IMPORTANT]
> 您能接觸到 PowerShell 指令碼的任何其他工具，都可能會受到您的編碼選擇影響，或將您的指令碼重新編碼成其他編碼。

### <a name="existing-scripts"></a>現有的指令碼

檔案系統中現有指令碼可能需要重新編碼成您新選擇的編碼。 在 VS Code 的底部列中，您將會看到 UTF-8 標籤。 按一下它開啟動作列，然後選取 **以編碼方式儲存** 。 您現在可為該檔案選擇新的編碼。 如需完整指示，請參閱 [VS Code 的編碼][]。

如果您需要重新編碼多個檔案，您可以使用下列指令碼：

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell 整合式指令碼環境 (ISE)

如果您也使用 PowerShell ISE 來編輯指令碼，您需要同步該處的編碼設定。

ISE 應該會接受 BOM，但它也可能使用反映來[設定編碼](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)。
請注意，這不會在啟動之間保存。

### <a name="source-control-software"></a>原始檔控制軟體

有些原始檔控制工具，例如 GIT，會忽略編碼；GIT 只追蹤位元組。 其他工具，例如 Azure DevOps 或 Mercurial，則不然。 有些以 GIT 為基礎的工具甚至依賴解碼文字。

發生這種情況時，請務必：

- 在原始程式碼控制中設定文字編碼，以符合您的 VS Code 設定。
- 確定所有檔案皆已使用相關的編碼簽入原始檔控制。
- 請小心透過原始檔控制所收到的編碼變更。 此項目的鑰匙符號指出有變更差異，卻又似乎沒有任何變更 (因為位元組變更，但字元未變更)。

### <a name="collaborators-environments"></a>共同作業者的環境

在設定原始檔控制的最上層，確定您共用之任何檔案的共同作業者沒有設定，無法透過重新編碼 PowerShell 檔案來覆寫您的編碼。

### <a name="other-programs"></a>其他程式

可讀取或寫入 PowerShell 指令碼的任何其他程式都能夠對它重新編碼。

部份範例如下：

- 使用剪貼簿複製並貼上指令碼。 這是常見的案例，例如：
  - 將指令碼複製到 VM
  - 複製電子郵件或網頁的指令碼
  - Microsoft Word 或 PowerPoint 文件為指令碼的複製來源或目標
- 其他文字編輯器，例如：
  - [記事本]
  - vim
  - 任何其他 PowerShell 指令碼編輯器
- 文字編輯公用程式，例如：
  - `Get-Content`/`Set-Content`/`Out-File`
  - PowerShell 重新導向運算子，例如 `>` 和 `>>`
  - `sed`/`awk`
- 檔案傳輸程式，例如：
  - 網頁瀏覽器，下載指令碼時
  - 檔案共用

這些工具有些會處理位元組而不處理文字，有些則提供編碼設定。 在您需要設定編碼的這些情況下，您需要讓它和您的編輯器編碼一樣，以免發生問題。

## <a name="other-resources-on-encoding-in-powershell"></a>在 PowerShell 中編碼的其他資源

有幾篇關於編碼和 PowerShell 設定編碼的文章值得閱讀：

- [about_Character_Encoding](/powershell/module/microsoft.powershell.core/about/about_character_encoding)
- [StackOverflow 上有關 PowerShell 編碼之 [@mklement0] 的摘要 ](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- 之前提出有關 VS Code-PowerShell 的編碼問題：
  - [#1308](https://github.com/PowerShell/VSCode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/VSCode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/VSCode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/VSCode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/VSCode-powershell/issues/1751)
- [傳統「約耳談軟體」  有關 Unicode 的文章](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [.NET Standard 中的編碼](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)

[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[拉丁文-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[位元組順序標記]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[語言伺服器通訊協定]: https://microsoft.github.io/language-server-protocol/
[VS Code 的編碼]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[Gremlins 追蹤器]: https://marketplace.visualstudio.com/items?itemName=nhoizey.gremlins \(英文\)
