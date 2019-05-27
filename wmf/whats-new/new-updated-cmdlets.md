---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: 新增與更新的 Cmdlet
ms.openlocfilehash: 9ec31c89c0bc4b111b40e2d4725fa0782a573204
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855543"
---
# <a name="new-and-updated-cmdlets"></a>新增與更新的 Cmdlet

我們根據社群的意見反應新增了新的 Cmdlet 並更新了現有的 Cmdlet。

## <a name="archive-cmdlets"></a>封存 Cmdlet

兩個新的 Cmdlet `Compress-Archive` 和 `Expand-Archive` 可讓您壓縮和解壓縮 ZIP 檔案。

如需詳細資訊，請參閱 [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) 模組文件。

## <a name="catalog-cmdlets"></a>類別目錄 Cmdlet

Microsoft.PowerShell.Security 模組中新增了兩個新的 Cmdlet。

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

它們會產生並驗證 Windows 目錄檔案。

## <a name="clipboard-cmdlets"></a>剪貼簿 Cmdlet

`Get-Clipboard`和 `Set-Clipboard` 讓您能夠更輕鬆地與 Windows PowerShell 工作階段來回傳送內容。 剪貼簿 Cmdlet 支援影像、音訊檔、檔案清單和文字。

如需詳細資訊，請參閱：

- [Get-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Set-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>密碼編譯訊息語法 (CMS) Cmdlet

密碼編譯訊息語法 Cmdlet 支援使用 IETF 標準格式加密和解密內容，進行密碼編譯保護訊息，如 [RFC5652](https://tools.ietf.org/html/rfc5652) 所述。

CMS 加密標準會實作公開金錀密碼編譯，其中用於加密內容的金錀 (公開金錀) 與用於解密內容的金錀 (私密金鑰) 不同。

公開金鑰可以廣泛共用，並非機密資料。 任何使用公開金鑰加密的內容只能使用私密金鑰來解密。 如需詳細資訊，請參閱[公開金鑰加密](https://en.wikipedia.org/wiki/Public-key_cryptography)。

如需詳細資訊，請參閱：

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage.md)
- [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage.md)
- [Unprotect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/rotect-CmsMessage.md)

憑證需要唯一的金鑰使用方法識別碼 (EKU) (例如「程式碼簽署」、「加密郵件」)，在 PowerShell 中將它們識別為資料加密憑證。 若要檢視憑證提供者中的文件加密憑證，您可以使用 `Get-ChildItem` 的 **DocumentEncryptionCert** 動態參數︰

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>從字串內容中擷取和剖析結構化物件

### <a name="convertfrom-string"></a>ConvertFrom-String

新的 `ConvertFrom-String` Cmdlet 支援兩種模式：

- 基本的分隔剖析
- 自動產生的範例驅動剖析

根據預設，分隔的剖析將輸入從空白字元位置分割，並將屬性名稱指派給產生的群組。

新的 **UpdateTemplate** 參數可將學習演算法的結果儲存為範本檔案中的註解， 使得學習程序 (最慢的階段) 成為單次成本。 現在幾乎可即時使用包含已編碼學習演算法的範本來執行 `ConvertFrom-String`。

如需詳細資訊，請參閱 [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String)。

### <a name="convert-string"></a>Convert-String

`Convert-String` 讓您能夠提供所需文字外觀的前後範例。 此 Cmdlet 會自動將文字格式化。

如需詳細資訊，請參閱 [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String)。

## <a name="updates-to-fileinfo-object"></a>FileInfo 物件的更新

檔案版本資訊可能產生誤導，特別是在已修補檔案的情況下。 WMF 5.0 會將新的 **FileVersionRaw** 和 **ProductVersionRaw** 指令碼屬性新增至 **FileInfo** 物件。
此處是為 powershell.exe 顯示的屬性 (假設 $pid 是 PowerShell 處理程序的識別碼) ︰

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a>Format-Hex

`Format-Hex` 可讓您以十六進位格式檢視文字或二進位資料。

如需詳細資訊，請參閱 [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex)。

## <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem 具有 -Depth 參數

`Get-ChildItem` 現在提供**Depth** 參數，可搭配 **Recurse** 用來限制遞迴：

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>宣告版本範圍 (1.* 等等) 的模組支援

您現在可以結合 **MinimumVersion** 和 **MaximumVersion** 來匯入特定範圍內的模組。 參數也支援萬用字元。

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a>New-Guid

有許多您需要使用唯一識別碼的案例。 `New-GUID` Cmdlet 提供一個簡單的方式來建立新的 GUID。

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>NoNewLine 參數

`Out-File`、`Add-Content` 及 `Set-Content` 現在提供新的 **NoNewline** 參數來省略輸出之後的新行。 例如：

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt

```Output
This is a single sentence.
```

如未指定 **NoNewline**，每個片段都會放在不同行：

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>使用改進的 Item Cmdlet 與符號連結互動

已擴充 Item Cmdlet 和數個相關的 Cmdlet 來支援符號連結。

### <a name="symbolic-link-files"></a>符號連結檔案

在此範例中，我們會在 C:\Temp 中建立名為 MySymLinkFile.txt 的新符號連結檔案，其會連結至 $pshome\profile.ps1。 這三個範例全都會產生相同的結果。

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>符號連結目錄

在此範例中，我們會在 C:\Temp 中建立名為 MySymLinkDir 的新符號連結目錄，其會連結至 $pshome 資料夾。 這三個範例全都會產生相同的結果。

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>永久連結

允許相同的**路徑**和**名稱**組合，如前所述。

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>目錄接合

允許相同的**路徑**和**名稱**組合，如前所述。

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-ChildItem

`Get-ChildItem` 現在會在 **Mode** 屬性中顯示 'l'，以指出符號連結檔案或目錄。

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a>Remove-Item

移除符號連結的運作方式類似移除任何其他項目類型。

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

使用 **Force** 參數來移除目標目錄中的檔案和符號連結。

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

有時候在您的指令碼中，您必須建立暫存檔案。 您可以使用 `New-TemporaryFile` Cmdlet 來進行此作業：

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>使用 PowerShell 管理網路交換器

網路交換器 Cmdlet，在 WMF 5.0 中引進，可讓您將交換器、虛擬 LAN (VLAN) 和基本層級 2 網路交換器連接埠設定套用至 Windows Server 2012 R2 標誌認證的網路交換器。 使用這些 Cmdlet 可以執行︰

- 全域交換器設定，例如︰
  - 設定主機名稱
  - 設定參數橫幅
  - 保存設定
  - 啟用或停用功能

- VLAN 設定：
  - 建立或移除 VLAN
  - 啟用或停用 VLAN
  - 列舉 VLAN
  - 設定易記的 VLAN 名稱

- 階層 2 連接埠設定：
  - 列舉連接埠
  - 啟用或停用連接埠
  - 設定連接埠模式和屬性
  - 將 VLAN 加入連接埠的主幹或存取或建立關聯性

如需詳細資訊，請參閱 [NetworkSwitchManager](/powershell/module/networkswitchmanager/) 文件。

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>根據具有 ODataUtils 的 OData 端點產生 PowerShell Cmdlet

ODataUtils 模組允許從支援 OData 的 REST 端點產生 PowerShell Cmdlet。 Microsoft.PowerShell.ODataUtils 模組包括下列功能：

- 從伺服器端端點到用戶端的通道其他資訊。
- 用戶端的分頁支援
- 使用 -Select 參數進行伺服器端篩選
- Web 要求標頭的支援

`Export-ODataEndPointProxy` Cmdlet 所產生的 Proxy Cmdlet 可提供來自**資訊**串流上伺服器端 OData 端點的其他資訊。

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

在下列範例中，我們要擷取熱門產品，並擷取 `$infoStream` 變數中的輸出。

藉由指定 **IncludeTotalResponseCount** 參數，我們會取得伺服器上可用之所有**產品**記錄的總計數。

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

您可以使用用戶端分頁支援，以批次方式從伺服器端取得記錄。 當您必須透過網路從伺服器取得大量資料時，這非常有用。

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

產生的 Proxy Cmdlet 支援 **Select** 參數，此參數可用來作為篩選條件，以便只接收用戶端所需的記錄屬性。 篩選會在伺服器上發生，以減少透過網路傳送的資料量。

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

`Export-ODataEndpointProxy` Cmdlet (及其產生的 Proxy Cmdlet) 現在均支援 **Headers** 參數。 標頭可用來傳遞 OData 端點所預期的其他資訊。

在下列範例中，會將包含訂用帳戶金鑰的雜湊表提供給 **Headers** 參數。 這是預期訂用帳戶金鑰進行驗證的典型服務範例。

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
