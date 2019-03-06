---
title: 了解 VSCode 與 PowerShell 中的檔案編碼
description: 設定檔案的編碼方式在 VSCode 和 PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: f3b133b4bee7688821a5960429e2f26b69b01e12
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251468"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>了解 VSCode 與 PowerShell 中的檔案編碼

當使用 VS Code 來建立和編輯 PowerShell 指令碼時，務必檔案使用正確的字元編碼格式儲存。

## <a name="what-is-file-encoding-and-why-is-it-important"></a>什麼是檔案的編碼方式，以及它為何如此重要？

VSCode 會管理人力的輸入字串的緩衝區的字元與位元組到檔案系統讀取/寫入區塊之間的介面。 當 VSCode 儲存檔案時，它會使用文字編碼來執行這項操作。

同樣地，PowerShell 執行指令碼時它必須將檔案中的位元組轉換為字元來重建檔案到 PowerShell 程式。 因為 VSCode 將檔案寫入，且 PowerShell 會讀取檔案，他們需要使用相同的編碼系統。 剖析的 PowerShell 指令碼的這個程序發生：*位元組* -> *字元* -> *權杖* ->  *抽象語法樹狀結構* -> *執行*。

VSCode 和 PowerShell 會安裝以合理的預設編碼設定。 不過，使用 PowerShell 的預設編碼方式已變更的 PowerShell Core (v6.x) 版本。 若要確保在 VSCode 中使用 PowerShell 或 PowerShell 延伸模組時沒有發生問題，您需要設定 VSCode 和 PowerShell 設定正確。

## <a name="common-causes-of-encoding-issues"></a>編碼問題常見原因

VSCode 或指令碼檔案的編碼方式不符合預期的編碼的 PowerShell 時，會發生編碼的問題。 沒有任何方法，適用於 PowerShell 來自動判斷檔案的編碼方式。

您是有可能已經編碼問題，當您使用不在字元[7 位元 ASCII 字元集](https://ascii.cl/)。 例如：

- 加重音拉丁字元 (`É`， `ü`)
- 非拉丁字元像是斯拉夫文 (`Д`， `Ц`)
- Han 中文 (`脚`， `本`)

編碼問題的常見原因如下：

- VSCode 和 PowerShell 的編碼不從其預設值已變更。 PowerShell 5.1 及之前的版本的預設編碼是從 VSCode 的不同。
- 另一個編輯器已開啟，並覆寫的檔案，以新的編碼方式。 這通常發生在 ISE。
- 檔案已簽入不同的原始檔控制中的編碼方式從哪些 VSCode 或 PowerShell 預期。 發生此情況的共同作業者使用不同編碼的組態編輯器。

### <a name="how-to-tell-when-you-have-encoding-issues"></a>如何分辨您有編碼的問題

通常編碼錯誤呈現為剖析指令碼中的錯誤。 如果您發現您的指令碼中的奇怪字元序列，這可以是問題。 在下列範例中，短破折號 (`–`) 會顯示為字元`â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

因為 VSCode 編碼字元，就會發生這個問題`–`做為位元組的 utf-8 `0xE2 0x80 0x93`。
這些位元組會解碼時作為 Windows 1252，它們會被解譯為字元`â€“`。

您可能會看到一些奇怪的字元序列包括：

- `â€“`，而非 `–`
- `â€”`，而非`—`
- `Ã„2`，而非`Ä`
- `Â` 而不是` `（不分行空格）
- `Ã©`，而非`é`

這很方便[參考](https://www.i18nqa.com/debug/utf8-debug.html)列出表示 UTF-8/Windows-1252年編碼問題的常見模式。

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>在 VSCode 中的 PowerShell 延伸模組與編碼之間的互動方式

PowerShell 延伸模組互動數種方式中的指令碼：

1. 當在 VSCode 中編輯指令碼時，就會 vscode 將內容傳送至延伸模組。 [語言伺服器通訊協定][]規定，在 utf-8 中傳送此內容。 因此，不可能進行擴充，以取得錯誤的編碼。
2. 當指令碼會直接在整合式主控台中執行時，它們是從檔案讀取 powershell 直接。 從 VSCode 的 Tf PowerShell 的編碼不同，可以發生錯誤了這裡。
3. 當在 VSCode 中開啟的指令碼參考另一個不是在 VSCode 中開啟的指令碼時，延伸模組會回復成從檔案系統載入該指令碼的內容。 PowerShell 延伸模組會預設為 utf-8 編碼，但會使用[位元組順序標記][]，或 BOM，偵測，以選取正確的編碼方式。

假設無 BOM 格式的編碼方式時，就會發生問題 (例如[utf-8][]不含 bom 並[Windows-1252][])。
PowerShell 延伸模組會預設為 utf-8。 延伸模組不能變更 VSCode 的編碼設定。
如需詳細資訊，請參閱 <<c0> [ 發出 #824](https://github.com/Microsoft/vscode/issues/824)。

## <a name="choosing-the-right-encoding"></a>選擇正確的編碼方式

不同系統和應用程式可以使用不同的編碼：

- 在.NET Standard 中，在 web 上，並在 Linux 環境中，utf-8 是現在主控項的編碼方式。
- 許多.NET Framework 應用程式使用[utf-16][]。 基於歷史原因，這有時稱為"Unicode"，現在的詞彙是指網羅[標準](https://en.wikipedia.org/wiki/Unicode)包含 utf-8 和 utf-16。
- Windows 中，許多比 Unicode 的原生應用程式繼續依預設會使用 Windows 1252。

Unicode 編碼方式也有位元組順序標記 (BOM) 的概念。 Bom 會告訴解碼器文字使用哪種編碼文字的開頭發生。 針對多位元組編碼，BOM 也會指出[位元組序](https://en.wikipedia.org/wiki/Endianness)編碼方式。 Bom 被設計成很少會發生在非 Unicode 文字，讓文字在 BOM 存在時，會是 Unicode 合理猜測的位元組。

Bom 是選擇性的其採用不受歡迎 Linux 世界中，因為在各處使用可靠的 utf-8 慣例。 大部分的 Linux 應用程式會假設文字輸入以 utf-8 編碼。 雖然許多 Linux 應用程式會辨識並正確處理 BOM，數字未這麼做，導致操作與這些應用程式的文字中的成品。

**因此**：

- 如果您主要是使用 Windows 應用程式和 Windows PowerShell，您應該會偏好使用如 utf-8 BOM 或 utf-16 編碼方式。
- 如果您使用跨平台，您應該會偏好使用以 BOM 的 utf-8。
- 如果您主要是在 Linux 相關聯的內容中，您應該會偏好使用不具有 BOM 的 utf-8。
- Windows-1252年和拉丁文-1。 如果可能的話，您應該避免基本上是舊版的編碼
  不過，某些較舊的 Windows 應用程式可能取決於它們。
- 也很值得一提，簽署指令碼[編碼相依](https://github.com/PowerShell/PowerShell/issues/3466)，這表示變更已簽署的指令碼的編碼方式，將需要重新簽署。

## <a name="configuring-vscode"></a>設定 VSCode

VSCode 的預設編碼是不具有 BOM 的 utf-8。

若要設定[VSCode 的編碼方式][]，請移至 VSCode 設定 (<kbd>Ctrl<kbd>+</kbd>，</kbd>)，並設定`"files.encoding"`設定：

```json
"files.encoding": "utf8bom"
```

一些可能的值為：

- `utf8`: [Utf-8]不加 BOM
- `utf8bom`: [Utf-8] bom
- `utf16le`: Little endian [utf-16]
- `utf16be`: Big endian [utf-16]
- `windows1252`: [Windows-1252]

應該在下拉式清單中取得，這在 GUI 檢視中，或自動完成，在 JSON 中的檢視。

您也可以將下列加入盡可能的編碼方式的自動偵測中：

```json
"files.autoGuessEncoding": true
```

如果您不想讓這些設定會影響所有的檔案類型，VSCode 也可讓每個語言設定。 建立特定語言的設定將設定放入`[<language-name>]`欄位。 例如：

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>設定 PowerShell

PowerShell 的預設編碼方式會根據版本而有所不同：

- 在 PowerShell 6 + 中，預設的編碼方式是不具有 BOM 的 utf-8 所有平台上。
- 在 Windows PowerShell 中，預設的編碼方式通常是 Windows-1252 的延伸模組[latin-1][]，也稱為 ISO 8859-1。

在 PowerShell 5 + 中，您可以找到與此編碼預設值：

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

下列[指令碼](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e)可用來判斷什麼編碼您的 PowerShell 工作階段會推斷不具有 BOM 的指令碼。

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

可以將 PowerShell 設為使用指定的編碼方式更廣泛使用的設定檔。 查看下列文章：

- [@mklement0][StackOverflow 上的 PowerShell 編碼方式相關的答案](https://stackoverflow.com/a/40098904)。
- [@rkeithhill][有關在 PowerShell 中的無 BOM 的 utf-8 輸入處理的部落格文章](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/)。

您不可能強制 PowerShell 以使用特定的輸入編碼方式。 PowerShell 5.1 和以下版本設為 Windows 1252 時沒有 BOM 編碼的預設值。 基於互通性考量，最好是以包含 BOM 以 Unicode 格式儲存指令碼。

> [!IMPORTANT]
> 任何其他工具您有該觸控式 PowerShell 指令碼可能會受到您的編碼選項，或重新編碼您的指令碼，以其他編碼。

### <a name="existing-scripts"></a>現有的指令碼

已在檔案系統上的指令碼可能需要重新編碼，您新的選擇編碼方式。 下方列的在 VSCode 中，您會看到 [utf-8] 標籤。 按一下以開啟 [動作] 列，然後選取**以編碼方式儲存**。 您現在可以選擇以新的編碼方式，就該檔案。 請參閱[VSCode 的編碼方式][]的完整指示。

如果您需要重新編碼多個檔案，您可以使用下列指令碼：

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell 整合式指令碼環境 (ISE)

如果您也會編輯使用 PowerShell ISE 指令碼，您需要同步處理您的編碼設定。

ISE 應該接受 BOM，但也可以使用反映來[設定的編碼方式](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/)。
請注意這不會在新創公司之間保存。

### <a name="source-control-software"></a>原始檔控制軟體

某些原始檔控制工具，例如 git 忽略編碼;git 只會追蹤位元組。
例如 TFS 或 Mercurial，卻不然。 解碼的文字依賴甚至一些 git 為基礎的工具。

這種情況時，請確定您：

- 設定以符合您的 VSCode 設定原始檔控制中的編碼的文字。
- 請確定您的檔案已簽入原始檔控制相關的編碼方式。
- 請小心變更，以透過原始檔控制所收到的編碼方式。 索引鍵的符號是差異變更，但沒有似乎已變更 （因為有個位元組，但字元不具有） 表示。

### <a name="collaborators-environments"></a>共同作業者的環境

頂端設定原始檔控制，請確定在您共用的任何檔案上共同作業者沒有覆寫編碼方式，藉由重新編碼 PowerShell 檔案的設定。

### <a name="other-programs"></a>其他程式

可讀取或寫入的 PowerShell 指令碼的其他程式可能會重新加以編碼。

以下列出一些範例：

- 使用剪貼簿複製並貼上指令碼。 這是常見的案例，例如：
  - 將指令碼複製到 VM
  - 複製出電子郵件或網頁的指令碼
  - 複製指令碼，傳入或傳出的 Microsoft Word 或 PowerPoint 文件
- 其他文字編輯器，例如：
  - 在 [記事本]
  - vim
  - 任何其他的 PowerShell 指令碼編輯器
- 文字編輯公用程式，例如：
  - `Get-Content`/`Set-Content`/`Out-File`
  - 之類的 PowerShell 重新導向運算子`>`和 `>>`
  - `sed`/`awk`
- 檔案傳輸的程式，例如：
  - Web 瀏覽器中，但是，要下載指令碼時
  - 檔案共用

其中部分工具處理的位元組，而不是文字，但其他人提供編碼的組態。 在這些情況下，您要設定的編碼方式，您需要使其與您的編輯器以避免發生問題的編碼方式相同。

## <a name="other-resources-on-encoding-in-powershell"></a>在 PowerShell 中的編碼方式的其他資源

有幾個其他好用文章有關編碼方式和設定 PowerShell 中的編碼值得讀取：

- [@mklement0][PowerShell 編碼 StackOverflow 上的摘要](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- 在 vscode-PowerShell 編碼問題上，開啟上一個問題：
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [傳統*Joel on Software*寫 Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [.NET Standard 中的編碼](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[位元組順序標記]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[語言伺服器通訊協定]: https://microsoft.github.io/language-server-protocol/
[VSCode 的編碼方式]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support