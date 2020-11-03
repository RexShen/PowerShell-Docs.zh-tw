---
description: 描述 PowerShell 中可更新的說明系統。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_updatable_help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Updatable_Help
ms.openlocfilehash: 03425aef93f3d4bbb06aee87d30f4a441c0b2d86
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207904"
---
# <a name="about-updatable-help"></a>關於可更新的說明

## <a name="short-description"></a>簡短描述
描述 PowerShell 中可更新的說明系統。

## <a name="long-description"></a>完整描述

PowerShell 提供數種不同的方法來存取 PowerShell Cmdlet 和概念的最新說明主題。

PowerShell 3.0 中引進的可更新說明系統是設計來確保您在本機電腦上一律擁有最新的說明主題，讓您可以在命令列中讀取它們。 它可讓您輕鬆地下載和安裝說明檔，並在有較新的說明檔可用時加以更新。

若要為企業中的多部電腦和無法存取網際網路的電腦提供更新的說明，可更新的說明可讓您將說明檔案下載到檔案系統目錄或檔案共用，然後從檔案共用安裝說明檔。

在 PowerShell 4.0 中， **HelpInfoUri** 屬性會保留在 Windows PowerShell 遠端處理，讓您可以 `Save-Help` 使用安裝在遠端電腦上的模組，但不一定會安裝在本機電腦上。 您可以將 **PSModuleInfo** 物件儲存至磁片或卸載式媒體 (例如 USB 磁片磁碟機) ，方法是 `Export-Clixml` 在無法存取網際網路的電腦上執行、在可存取網際網路的電腦上匯入 **PSModuleInfo** 物件，然後 `Save-Help` 在 **PSModuleInfo** 物件上執行。 您可以使用卸載式媒體將儲存的說明複製到遠端的已中斷連線的電腦，然後再執行安裝 `Update-Help` 。 這些功能的增強 `Save-Help` 功能可讓您在沒有任何網路存取的電腦上安裝說明。 如需如何使用新功能的範例 `Save-Help` ，請參閱本主題中的 [如何更新檔案共用的說明](#how-to-update-help-from-a-file-share) 。

「可更新的說明」也支援線上存取最新的說明主題和 Cmdlet 的基本說明，即使電腦上沒有說明檔也一樣。

PowerShell 3.0 並未隨附說明檔。 您可以使用「可更新的說明」功能，針對 PowerShell 和所有 Windows 模組中預設包含的所有命令安裝說明檔。

## <a name="updatable-help-cmdlets"></a>可更新的說明 Cmdlet

- `Update-Help`：從網際網路或檔案共用下載最新的說明檔，並將它們安裝在本機電腦上。

- `Save-Help`：從網際網路下載最新的說明檔，並將它們儲存在檔案系統目錄或檔案共用中。 若要在電腦上安裝說明檔，請使用 `Update-Help` 。

- `Get-Help`：在命令列中顯示說明主題。 從電腦上的說明檔中取得協助。 針對沒有說明檔的 Cmdlet 和函式，顯示自動產生的說明。 在您的預設網際網路瀏覽器中，開啟 Cmdlet、函式、腳本和工作流程的線上說明主題。

## <a name="update-help-in-the-powershell-ise"></a>更新 PowerShell ISE 中的說明

您也可以在 PowerShell 整合式腳本環境 (ISE) 的 [說明] 功能表中，使用 [ **更新 powershell** 說明] 專案來更新說明。

**Update PowerShell** 說明專案 `Update-Help` 會執行不含參數的命令。

## <a name="auto-generated-help-help-without-help-files"></a>自動產生的說明：沒有說明檔的說明

如果您的電腦上沒有 Cmdlet、函式或工作流程的說明檔，此 `Get-Help` Cmdlet 會顯示自動產生的說明，並提示您下載說明檔或在線上閱讀。

自動產生的說明包括語法和別名，以及說明如何使用可更新的說明 Cmdlet 及存取線上說明主題的備註。

例如，下列命令會取得 Cmdlet 的基本說明 `Get-Culture` 。 當電腦上沒有說明檔時，輸出 `Get-Help` 會顯示顯示。

```powershell
Get-Help Get-Culture
```

```output
NAME
    Get-Culture

SYNTAX
    Get-Culture [<CommonParameters>]

ALIASES
    None

REMARKS
    To get the latest Help content including descriptions and examples
    type: Update-Help.
```

## <a name="help-files-for-modules"></a>模組的說明檔

可更新說明的最小單位是模組的說明。 模組說明包含模組中所有 Cmdlet、函數、工作流程、提供者、腳本和概念的說明。 您可以更新安裝在電腦上的所有模組的說明，即使它們未匯入目前的會話中也一樣。

您可以更新整個模組的說明，但無法更新個別 Cmdlet 的說明。

若要尋找包含特定 Cmdlet 的模組，請使用下列命令格式：

```powershell
(Get-Command <cmdlet-name>).ModuleName
```

例如，若要尋找包含 Cmdlet 的模組 `Set-ExecutionPolicy` ，請輸入：

```powershell
(Get-Command Set-ExecutionPolicy).ModuleName
```

若要更新特定模組的說明，請輸入：

```powershell
Update-Help -Module <ModuleName>
```

例如，若要更新包含 Set-ExecutionPolicy Cmdlet 之模組的說明，請輸入：

```powershell
Update-Help -Module Microsoft.PowerShell.Security
```

## <a name="permissions-for-updatable-help"></a>可更新說明的許可權

若要更新目錄中模組的說明 `$pshome/Modules` ，您必須是電腦上 Administrators 群組的成員。

如果您不是 Administrators 群組的成員，您就無法更新這些模組的說明。但是，如果您可以存取網際網路，就可以在線上觀看說明。

針對目錄中的模組 `$home/Documents/PowerShell/Modules` 或目錄其他子目錄中的模組更新說明不 `$home` 需要特殊許可權。

`Update-Help`和 `Save-Help` Cmdlet 具有 **UseDefaultCredentials** 參數，可提供目前使用者的明確認證。 此參數是針對存取安全的網際網路位置所設計。

`Update-Help`和 `Save-Help` Cmdlet 也有一個 **Credential** 參數，可讓您在遠端電腦上執行命令，並存取第三部電腦上的檔案共用。 只有 **Credential** 當您使用的 SourcePath 或 **LiteralPath** 參數 `Update-Help` 以及的 **DestinationPath** 或 **LiteralPath** 參數時，Credential 參數才有效 `Save-Help` 。

## <a name="how-to-install-and-update-help-files"></a>如何安裝和更新說明檔

若要第一次下載和安裝說明檔，或更新您電腦上的說明檔，請使用 `Update-Help` Cmdlet。

此 `Update-Help` Cmdlet 會為您執行所有的困難工作，包括下列工作。

- 判斷哪些模組支援可更新的說明。
- 尋找每個模組儲存其可更新說明檔的網際網路位置。
- 將您電腦上每個模組的說明檔，與每個模組可用的最新說明檔案進行比較。
- 從網際網路下載新的檔案。
- 解除包裝說明檔套件。
- 確認檔案是有效的說明檔。
- 在模組目錄的特定語言子目錄中安裝說明檔。

若要存取新的說明主題，請使用 `Get-Help` Cmdlet。 您不需要重新開機 PowerShell。

若要在支援可更新說明的電腦上安裝或更新所有模組的說明，請輸入：

```powershell
Update-Help
```

若要更新特定模組的說明，請新增的 **模組** 參數 `Update-Help` 。 模組名稱中允許使用萬用字元。

例如，若要更新 ServerManager 模組的說明，請輸入：

```powershell
Update-Help -Module ServerManager
```

如果沒有參數， `Update-Help` 則會針對會話中的所有模組以及所有支援可更新說明的已安裝模組更新說明。 您必須將模組安裝在 PSModulePath 環境變數的值所列的目錄中，才能包含這些模組。 這些也是由 "Get-help-ListAvailable" 命令所傳回的模組。

如果 **Module** 參數的值是 `*` (所有) ，則 `Update-Help` 會嘗試更新所有已安裝模組的說明，包括不支援「可更新的說明」的模組。 此命令通常會在 Cmdlet 遇到不支援「可更新的說明」的模組時產生許多錯誤。

## <a name="how-to-update-help-from-a-file-share"></a>如何從檔案共用更新說明

若要支援未連線至網際網路的電腦，或是要控制或簡化在企業中更新的協助，請使用 `Save-Help` Cmdlet。 `Save-Help`Cmdlet 會從網際網路下載說明檔，並將其儲存在您指定的 filesystem 目錄中。

`Save-Help` 比較指定目錄中的說明檔與每個模組可用的最新說明檔案。 如果目錄沒有說明檔或較新的說明檔可供模組使用，則 `Save-Help` Cmdlet 會從網際網路下載新的檔案。 但是，它不會解除包裝或安裝說明檔。

若要從儲存至檔案系統目錄的說明檔安裝或更新電腦上的說明檔，請使用 Cmdlet 的 **SourcePath** 參數 `Update-Help` 。 此 `Update-Help` Cmdlet 會識別最新的說明檔案、解除包裝並驗證它們，然後將它們安裝在模組目錄的特定語言子目錄中。

例如，若要將所有已安裝模組的說明儲存至 `\\Server\Share` 目錄，請輸入：

```powershell
Save-Help -DestinationPath \\Server\Share
```

然後，若要更新目錄中的說明 `\\Server\Share` ，請輸入：

```powershell
Update-Help -SourcePath \\Server\Share
```

下列範例示範 `Save-Help` 如何使用來儲存未安裝在本機電腦上之模組的說明。 在此範例中，系統管理員 `Save-Help` 會執行，以從連線到網際網路的用戶端電腦儲存 DhcpServer 模組的說明，而不需要在本機電腦上安裝 DhcpServer 模組或 DHCP 伺服器角色。

選項1：執行 `Invoke-Command` 以取得遠端模組的 **PSModuleInfo** 物件，將它儲存在變數中， `$m` 然後在 `Save-Help` **PSModuleInfo** 物件上執行，方法是將變數指定 `$m` 為模組名稱。

```powershell
$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock
{ Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

選項2：開啟以執行 DHCP 伺服器模組的電腦為目標的 PSSession、取得模組的 **PSModuleInfo** 物件、將它儲存在變數中， `$m` 然後 `Save-Help` 在儲存在變數中的物件上執行 `$m` 。

```powershell
$s = New-PSSession -ComputerName RemoteServer
$m = Get-Module -PSSession $s -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

選項3：開啟以執行 DHCP 伺服器模組的電腦為目標的 CIM 會話，若要取得模組的 **PSModuleInfo** 物件，請將它儲存在變數中， `$m` 然後 `Save-Help` 在儲存在變數中的物件上執行 `$m` 。

```powershell
$c = New-CimSession -ComputerName RemoteServer
$m = Get-Module -CimSession $c -Name DhcpServer -ListAvailable
Save-Help -Module $m -DestinationPath C:\SavedHelp
```

在下列範例中，系統管理員會在沒有網路存取的電腦上，安裝 DHCP 伺服器模組的說明。

首先，執行 `Export-Clixml` 以將 **PSModuleInfo** 物件匯出到共用資料夾或卸載式媒體。

```powershell
$m = Get-Module -Name DhcpServer -ListAvailable
Export-Clixml -Path E:\UsbFlashDrive\DhcpModule.xml -InputObject $m
```

接下來，將卸載式媒體傳輸到可存取網際網路的電腦，然後使用匯入 **PSModuleInfo** 物件 `Import-Clixml` 。 執行 `Save-Help` 以儲存已匯入 DhcpServer 模組 **PSModuleInfo** 物件的說明。

```powershell
$deserialized_m = Import-Clixml E:\UsbFlashDrive\DhcpModule.xml
Save-Help -Module $deserialized_m -DestinationPath E:\UsbFlashDrive\SavedHelp
```

最後，將卸載式媒體傳輸回沒有網路存取的電腦，然後執行以安裝說明 `Update-Help` 。

```powershell
Update-Help -Module DhcpServer -SourcePath E:\UsbFlashDrive\SavedHelp
```

如果沒有參數， `Save-Help` 則會為會話中的所有模組以及所有支援可更新說明的已安裝模組下載說明。 您必須將模組安裝在 `$env:PSModulePath` 本機電腦或遠端電腦上（您要儲存說明的環境變數值）中所列的目錄中，才能加入模組。 這些也是藉由執行命令所傳回的模組 `Get-Help -ListAvailable` 。

## <a name="how-to-update-help-files-in-different-languages"></a>如何以不同的語言更新說明檔

根據預設， `Update-Help` 和 `Save-Help` Cmdlet 會以 UI 文化特性和在本機電腦上為 Windows 設定的語言下載說明。 如果在本機 UI 文化特性中無法使用指定模組的說明檔， `Update-Help` 並 `Save-Help` 使用 Windows 語言回復規則來尋找最受支援的語言。

不過，您可以使用和 Cmdlet 的 **UICulture** 參數 `Update-Help` ， `Save-Help` 以在任何可用的 UI 文化特性中下載並安裝說明檔。

例如，若要以日文儲存會話上所有模組的最新說明檔 (Ja-jp) 和法文 (fr-fr) ，請輸入：

```powershell
Save-Help -Path \Server\Share -UICulture ja-jp, fr-fr
```

如果您指定的語言中無法使用模組的說明檔，和 Cmdlet 會傳回 `Update-Help` `Save-Help` 一則錯誤訊息，其中列出每個模組的說明可用的語言，讓您可以選擇最符合您需求的替代方案。

> [!NOTE]
> 目前，可更新的說明內容只會以英文 (en-us) 來發佈。

## <a name="how-to-use-online-help"></a>如何使用線上說明

如果您無法或選擇不更新本機電腦上的說明檔，您仍然可以在線上取得最新的說明檔。

若要開啟任何 Cmdlet 或函式的線上說明主題，請使用 Cmdlet 的 **online** 參數 `Get-Help` 。

例如，下列命令會 `Get-Job` 在您的預設網際網路瀏覽器中開啟 Cmdlet 的線上說明主題：

```powershell
Get-Help Get-Job -Online
```

若要取得腳本的線上說明，請使用 **online** 參數和腳本的完整路徑。

**Online** 參數不適用於「關於」主題。 若要查看 PowerShell 的「關於」主題，包括 PowerShell 語言的相關說明主題，請參閱 [Powershell 關於主題](about.md)。

## <a name="how-to-minimize-or-prevent-internet-downloads"></a>如何最小化或防止網際網路下載

若要將網際網路下載降至最低，並為未連線至網際網路的使用者提供可更新的說明，請使用 `Save-Help` Cmdlet。 從網際網路下載說明，並將其儲存到網路共用。 然後，建立 `Update-Help` 在所有電腦上執行命令的群組原則設定或排程工作。 將 Cmdlet 的 **SourcePath** 參數值設定 `Update-Help` 為網路共用。

若要防止可存取網際網路的使用者從網際網路下載可更新的說明，請使用 **設定 update-help 群組原則設定的預設來源路徑** 。

此群組原則設定會以隱含方式將 **SourcePath** 參數（具有您指定的檔案系統位置）新增至 `Update-Help` 每個受影響電腦上的每個命令。 使用者可以明確地使用 **SourcePath** 參數來指定不同的檔案系統位置，但是無法排除 **sourcepath** 參數並從網際網路下載說明。

> [!NOTE]
> [ **設定 update-help 群組原則的預設來源路徑] 設定** 會出現在 [ **電腦** 設定和 **使用者** 設定] 下。 不過，只有 [ **電腦** 設定] 下的原則設定才會生效。 [ **使用者** 設定] 下的原則設定會被忽略。

如需詳細資訊，請參閱 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)。

## <a name="how-to-update-help-for-non-standard-modules"></a>如何更新非標準模組的說明

若要更新或儲存指令程式的 **ListAvailable** 參數未傳回的模組說明 `Get-Module` ，請將模組匯入到目前的會話，然後再執行 `Update-Help` 或 `Save-Help` 命令。 在遠端電腦上執行 `Save-Help` 命令之前，請將模組匯入目前的會話，或 `Invoke-Command` 連接到遠端電腦的腳本區塊。

當模組在目前的會話中時，請執行 `Update-Help` 或 `Save-Help` 不含參數的 Cmdlet，或使用 **module** 參數指定模組名稱。

和 Cmdlet 的 **模組** 參數 `Update-Help` `Save-Help` 只接受模組名稱。 它們不接受模組檔案的路徑。

使用這項技術來更新或儲存任何不是由 Cmdlet 的 **ListAvailable** 參數所傳回之模組的說明 `Get-Module` ，例如安裝在環境變數未列出之位置中的模組 `$env:PSModulePath` ，或不是格式正確的模組 (模組目錄不包含至少一個檔案，其 basename 與目錄名稱相同) 。

## <a name="how-to-support-updatable-help"></a>如何支援可更新的說明

如果您撰寫模組，您可以支援模組的線上說明和可更新說明。 如需詳細資訊，請參閱 Microsoft Docs 中的 [支援可更新](/powershell/scripting/developer/help/supporting-updatable-help) 的說明和 [支援線上說明](/powershell/scripting/developer/module/supporting-online-help) 。

PowerShell 嵌入式管理單元或以批註為基礎的說明無法使用可更新的說明。

## <a name="remarks"></a>備註

`Update-Help` `Save-Help` Windows 預先安裝環境 (Windows PE) 不支援和 Cmdlet。

## <a name="see-also"></a>另請參閱

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Save-Help](xref:Microsoft.PowerShell.Core.Save-Help)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)
