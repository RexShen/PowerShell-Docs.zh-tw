---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/save-help?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Help
ms.openlocfilehash: 4b7e74d7b83dbf5128b30e1bbf2c51d69c3a235a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204872"
---
# Save-Help

## 概要
下載最新的說明檔並儲存至檔案系統目錄。

## SYNTAX

### 路徑 (預設值)

```
Save-Help [-DestinationPath] <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

### LiteralPath

```
Save-Help -LiteralPath <String[]> [[-Module] <PSModuleInfo[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-UICulture] <CultureInfo[]>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>]
 [<CommonParameters>]
```

## DESCRIPTION

**Save-Help** Cmdlet 會下載適用于 PowerShell 模組的最新說明檔案，並將它們儲存至您指定的目錄。
此功能可讓您在無法存取網際網路的電腦上更新說明檔案，並輕鬆地在多部電腦上更新說明檔案。

在 Windows PowerShell 3.0 中， **Save-Help** 只適用于安裝在本機電腦上的模組。
雖然可以從遠端電腦匯入模組，或使用 PowerShell 遠端處理從遠端電腦取得 **PSModuleInfo** 物件的參考，但 **HelpInfoUri** 屬性不會保留，而且 **儲存** 說明不適用於遠端模組說明。

在 Windows PowerShell 4.0 中， **HelpInfoUri** 屬性會透過 PowerShell 遠端處理來保留，如此可讓您在遠端電腦上安裝的模組中使用 **Save-Help** 。
您也可以將 **PSModuleInfo** 物件儲存至磁片或卸載式媒體，方法是在無法存取網際網路的電腦上執行 Export-Clixml、在可存取網際網路的電腦上匯入物件，然後在 **PSModuleInfo** 物件上執行 **儲存** 說明。
已儲存的說明可以使用卸除式存放裝置媒體（例如 USB 磁片磁碟機）傳輸到遠端電腦。
您可以藉由執行 **update-help** ，在遠端電腦上安裝說明。
此程序可用來在沒有任何存取網路方式的電腦上安裝說明。

若要安裝已儲存的說明檔，請執行 Update-Help Cmdlet。
新增其 *SourcePath* 參數，以指定您儲存說明檔的資料夾。

若未指定參數， **Save-Help** 命令會為工作階段中的所有模組以及安裝在電腦上之 **PSModulePath** 環境變數所列位置中的模組下載最新的說明。
此動作會略過不支援「可更新的說明」的模組，而不發出警告。

**Get-help** Cmdlet 會檢查目的地資料夾中任何說明檔的版本。
如果有較新的說明檔，此 Cmdlet 會從網際網路下載最新的說明檔，然後將它們儲存在資料夾中。
**Save-Help** Cmdlet 的運作方式與 Update-Help Cmdlet 相同，不同之處在于它會將下載的封包 ( .cab) 檔案中，而不是從封包檔解壓縮說明檔，並將它們安裝在電腦上。

每個模組的已儲存說明都包含說明資訊 (HelpInfo XML) 檔案和包含每個 UI 文化特性說明檔案的封包 (.cab) 檔。
您不需要從封包檔解壓縮說明檔案。
**Update-help** Cmdlet 會解壓縮說明檔案、驗證 XML 是否安全，然後將說明檔和說明資訊檔安裝在模組資料夾的特定語言子資料夾中。

若要儲存 PowerShell 安裝資料夾中模組的說明檔 ($pshome \Modules) ，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。
您必須為電腦上 Administrators 群組的成員才能下載這些模組的說明檔。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：儲存 DhcpServer 模組的說明

```powershell
# Option 1: Run Invoke-Command to get the PSModuleInfo object for the remote DHCP Server module, save the PSModuleInfo object in the variable $m, and then run Save-Help.

$m = Invoke-Command -ComputerName RemoteServer -ScriptBlock { Get-Module -Name DhcpServer -ListAvailable }
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 2: Open a PSSession--targeted at the remote computer that is running the DhcpServer module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$s = New-PSSession -ComputerName "RemoteServer"
$m = Get-Module -PSSession $s -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"


# Option 3: Open a CIM session--targeted at the remote computer that is running the DhcpServer module--to get the PSModuleInfo object for the remote module, and then run Save-Help.

$c = New-CimSession -ComputerName "RemoteServer"
$m = Get-Module -CimSession $c -Name "DhcpServer" -ListAvailable
Save-Help -Module $m -DestinationPath "C:\SavedHelp"
```

此範例顯示三種不同的方式，可讓您使用 **儲存** 說明從連線到網際網路的用戶端電腦儲存 **DhcpServer** 模組的說明，而不需要在本機電腦上安裝 **DhcpServer** 模組或 DHCP 伺服器角色。

### 範例2：安裝 DhcpServer 模組的說明

```powershell
# First, run Export-CliXml to export the PSModuleInfo object to a shared folder or to removable media.

$m = Get-Module -Name "DhcpServer" -ListAvailable
Export-CliXml -Path "E:\UsbFlashDrive\DhcpModule.xml" -InputObject $m

# Next, transport the removable media to a computer that has Internet access, and then import the PSModuleInfo object with Import-CliXml. Run Save-Help to save the Help for the imported DhcpServer module PSModuleInfo object.

$deserialized_m = Import-CliXml "E:\UsbFlashDrive\DhcpModule.xml"
Save-Help -Module $deserialized_m -DestinationPath "E:\UsbFlashDrive\SavedHelp"

# Finally, transport the removable media back to the computer that does not have network access, and then install the help by running Update-Help.

Update-Help -Module DhcpServer -SourcePath "E:\UsbFlashDrive\SavedHelp"
```

此範例示範如何在無法存取網際網路的電腦上，安裝您在範例1中為 **DhcpServer** 模組儲存的說明。

### 範例3：儲存所有模組的說明

```powershell
Save-Help -DestinationPath "\\Server01\FileShare01"
```

此命令會根據為本機電腦上 Windows 設定的 UI 文化特性下載所有模組的最新說明檔案。
它會將說明檔案儲存在 \\ \\ Server01\Fileshare01 資料夾中。

### 範例4：儲存電腦上模組的說明

```powershell
Save-Help -Module ServerManager -DestinationPath "\\Server01\FileShare01" -Credential Domain01/Admin01
```

此命令會下載 **ServerManager** 模組的最新說明檔，然後將它們儲存在 \\ \\ Server01\Fileshare01 資料夾中。

當在電腦上安裝某個模組時，即使該模組不會匯入到目前的工作階段中，您也可以輸入模組名稱當做 *Module* 參數的值。

命令使用 *Credential* 參數提供具權限在檔案共用進行寫入之使用者的認證。

### 範例5：儲存不同電腦上模組的說明

```powershell
Invoke-Command -ComputerName Server02 {Get-Module -Name CustomSQL -ListAvailable} | Save-Help -DestinationPath \\Server01\FileShare01 -Credential Domain01\Admin01
```

這些命令會下載 **CustomSQL** 模組的最新說明檔案，並將它們儲存在 \\ \\ Server01\Fileshare01 資料夾中。

由於 **CustomSQL** 模組未安裝在電腦上，因此序列包含 Invoke-Command 命令，可從 Server02 電腦取得 CustomSQL 模組的模組物件，然後使用管線將模組物件傳送至 **儲存-** 說明 Cmdlet。

當電腦未安裝模組時， **Save-Help** 需要模組物件，其中包含最新說明檔案位置的相關資訊。

### 範例6：儲存多種語言的模組說明

```powershell
Save-Help -Module Microsoft.PowerShell* -UICulture de-DE, en-US, fr-FR, ja-JP -DestinationPath "D:\Help"
```

此命令會以四種不同的 UI 文化特性來儲存 PowerShell Core 模組的說明。
這些地區設定的語言套件不需要安裝在電腦上。

只有在當模組擁有者在網際網路上提供翻譯的檔案時， **Save-Help** 才可以為模組下載不同 UI 文化特性的說明檔案。

### 範例7：每天儲存說明一次以上

```powershell
Save-Help -Force -DestinationPath "\\Server3\AdminShare\Help"
```

此命令會為安裝在電腦上所有的模組儲存說明。
此命令會指定 *Force* 參數來覆寫規則，以避免 **在每24小時的期間** 內多次下載說明。

*Force* 參數也會覆寫 1 GB 的限制和規避版本檢查。
因此，即使版本不晚于目的資料夾中的版本，您也可以下載檔案。

此命令會使用 **update-help Cmdlet 來** 下載說明檔，並將其儲存至指定的資料夾。
當您每天必須執行 **Save-Help** 命令一次以上時，就必須使用 *Force* 參數。

## PARAMETERS

### -Credential

指定使用者認證。 此 Cmdlet 會使用具有存取 **DestinationPath** 參數所指定之檔案系統位置之許可權的使用者認證來執行命令。 只有當命令中使用 **DestinationPath** 或 **LiteralPath** 參數時，此參數才有效。

此參數可讓您 `Save-Help` 在遠端電腦上執行使用 **DestinationPath** 參數的命令。 藉由提供明確的認證，您可以在遠端電腦上執行命令，並存取第三部電腦上的檔案共用，而不會遇到拒絕存取錯誤，或使用 CredSSP 驗證來委派認證。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DestinationPath

指定用來儲存說明檔的資料夾路徑。
不要指定檔案名稱或副檔名。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指出此 Cmdlet 不會遵循每天一次的限制、略過版本檢查，以及下載超過 1 GB 限制的檔案。

若未指定參數，在每 24 小時期間內每個模組只會允許一個 **Save-Help** 命令、每個模組的下載限制為 1 GB 的未壓縮內容，並且只有當模組的說明檔案比電腦上的檔案新時，才會進行安裝。

每日一次的限制可保護裝載說明檔的伺服器，並讓您可以將 **Save-help** 命令新增至您的 PowerShell 設定檔。

若要不使用 *Force* 參數來儲存多重 UI 文化特性中的模組說明，請在同一個命令中包含所有 UI 文化特性，例如：`Save-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedModule

指定以 ModuleSpecification 物件形式指定之名稱的模組。
這會在 MSDN library 中的 ModuleSpecification 函式 [ (雜湊表) ](https://msdn.microsoft.com/library/jj136290) 的「備註」一節中加以說明。
例如， *FullyQualifiedModule* 參數會接受以 @ {ModuleName = "modulename" 格式指定的模組名稱;ModuleVersion = "version_number"} 或 @ {ModuleName = "modulename";ModuleVersion = "version_number";Guid = "GUID"}。
**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。

您無法在與 *模組* 參數相同的命令中指定 *FullyQualifiedModule* 參數。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

指定目的資料夾的路徑。
與 *DestinationPath* 參數的值不同， *LiteralPath* 參數的值將完全依照其輸入值來使用。
沒有字元會被視為萬用字元。
如果路徑包含逸出字元，請將它括在單引號中。
單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Module

指定此 Cmdlet 下載說明的模組。
在以逗號分隔的清單中輸入一或多個模組名稱或名稱模式，或是在每一行有一個模組名稱的檔案中輸入一或多個模組名稱或名稱。
允許使用萬用字元。
您也可以使用管線將模組物件從 Get-Module Cmdlet 傳送至 **Save-Help** 。

根據預設， **Save-Help** 會為支援 Updatable Help 與已安裝在本機電腦上 **PSModulePath** 環境變數所列位置中的所有模組下載說明。

若要為未安裝在電腦上的模組儲存說明，請在遠端電腦上執行 **取得模組** 命令。
然後將產生的模組物件透過管線傳送至 **Save-Help** Cmdlet 或提交模組物件為 *Module* 或 *InputObject* 參數的值。

如果您指定的模組已安裝在電腦上，您可以輸入模組名稱或模組物件。
如果該模組未安裝在電腦上，您必須輸入模組物件，例如由 **Get-Module** Cmdlet 傳回的物件。

**Save-Help** Cmdlet 的 *Module* 參數不接受模組檔案或模組資訊清單檔案的完整路徑。
若要儲存不在 **PSModulePath** 位置之模組的說明，請將模組匯入到目前的會話，然後再執行 **save-help** 命令。

"*" 的值 (所有) 嘗試更新電腦上所安裝之所有模組的說明。
這包括不支援「可更新的說明」的模組。
當命令遇到不支援「可更新的說明」的模組時，這個值可能會產生錯誤。

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -UICulture

指定此 Cmdlet 取得已更新說明檔的 UI 文化特性值。
輸入一或多個語言代碼（例如 es）、包含文化特性物件的變數，或可取得文化特性物件的命令，例如 Get-Culture 或 Get-UICulture 命令。

不允許使用萬用字元。
請勿指定部分語言代碼，例如 "de"。

根據預設， **Save-Help** 會取得針對 Windows 設定之 UI 文化特性或其後援文化特性中的說明檔。
如果您指定 *UICulture* 參數， **儲存-** 說明只會尋找所指定 UI 文化特性的說明，而不會尋找任何回溯文化特性中的說明。

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: Current UI culture
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredentials

指出此 Cmdlet 會使用目前使用者的認證來執行命令，包括 web 下載。
根據預設，該命令執行時不會使用明確宣告的認證。

此參數只在網路下載是使用 NTLM、交涉或 Kerberos 驗證時有效。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope

此辨識不會在此 Cmdlet 中執行任何動作。

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSModuleInfo

您可以使用管線將模組物件從 **get-help** Cmdlet 傳送至 **儲存-** 說明的 *模組* 參數。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

* 若要為 $pshome \Modules 資料夾中的模組儲存說明，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。 只有電腦上 Administrators 群組的成員可以為 $pshome \Modules 資料夾中的模組下載說明。
* 每個模組的已儲存說明都包含說明資訊 (HelpInfo XML) 檔案和包含每個 UI 文化特性說明檔案的封包 (.cab) 檔。 您不需要從封包檔解壓縮說明檔案。 Update-Help Cmdlet 會解壓縮說明檔案、驗證 XML，然後在模組資料夾的特定語言子資料夾中安裝說明檔和說明資訊檔案。
* **Save-Help** Cmdlet 可以儲存未安裝在電腦上之模組的說明。 不過，因為說明檔是安裝在模組資料夾中，所以 **update-help** Cmdlet 只能針對安裝在電腦上的模組安裝已更新的說明檔。
* 如果 **Save-Help** 找不到模組的已更新說明檔，或找不到指定語言的已更新說明檔，它會繼續作業而不會顯示錯誤訊息。 若要查看命令已儲存哪些檔案，請指定 *Verbose* 參數。
* 模組是可更新的說明之最小單位。 您無法儲存特定 Cmdlet 的說明，僅適用于模組中的所有 Cmdlet。 若要尋找包含特定 Cmdlet 的模組，請使用 **ModuleName** 屬性搭配 Get-Command Cmdlet，例如 `(Get-Command \<cmdlet-name\>).ModuleName`
* **Save-Help** 支援所有模組和 PowerShell Core 嵌入式管理單元。它不支援任何其他嵌入式管理單元。
* **Update-help** 和 **Save-help** Cmdlet 使用下列埠下載說明檔：適用于 HTTP 的埠80和 HTTPS 的埠443。
* Windows 預先安裝環境 (Windows PE) 不支援 **Update-Help** 和 **Save-Help** Cmdlet。

## 相關連結

[Get-Help](Get-Help.md)

[Get-Module](Get-Module.md)

[Update-Help](Update-Help.md)
