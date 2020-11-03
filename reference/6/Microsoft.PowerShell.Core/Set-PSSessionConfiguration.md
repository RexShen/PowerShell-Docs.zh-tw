---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: 8a769959295de0eed7776cc972b007514cfe8734
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205612"
---
# Set-PSSessionConfiguration

## 概要
變更已登錄的工作階段設定屬性。

## SYNTAX

### NameParameterSet (預設值)

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AssemblyNameParameterSet

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionConfigurationFile

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`Set-PSSessionConfiguration`Cmdlet 會變更本機電腦上會話設定的屬性。

使用 **Name** 參數可以識別您想要變更的工作階段設定。 使用其他參數可以為工作階段設定的屬性指定新值。 若要刪除設定中的屬性值，並使用預設值，請輸入空字串 ( "" ) 或對應參數的值 `$Null` 。

從 PowerShell 3.0 開始，您可以使用會話設定檔來定義會話設定。 此功能為使用工作階段設定的工作階段，提供一個簡單且可探索的方法來設定和變更其屬性。 若要指定會話設定檔，請使用的 **Path** 參數 `Set-PSSessionConfiguration` 。 如需會話設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。
如需有關如何建立和修改會話設定檔的詳細資訊，請參閱 `New-PSSessionConfigurationFile` Cmdlet。

會話設定定義遠端會話的環境， ( **pssession** ) 連接到本機電腦。 每個 **PSSession** 都會使用會話設定。 會話設定會決定 **PSSession** 的功能，例如會話中可用的模組、允許執行的 Cmdlet、語言模式、配額和超時。 會話設定的安全描述項會決定可以使用會話設定連接到本機電腦的人員。 如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

若要查看會話設定的屬性，請使用 `Get-PSSessionConfiguration` Cmdlet 或 WSMan 提供者。 如需 WSMan 提供者的詳細資訊，請輸入 `Get-Help WSMan` 。

## 範例

### 範例1：建立和變更會話設定

此範例示範如何在設定中新增和移除啟動腳本。

第一個命令會建立 **AdminShell** 設定。 第二個命令會將 `AdminConfig.ps1` 腳本新增至設定。 當您重新開機 **WinRM** 時，變更會生效。
第三個命令會 `AdminConfig.ps1` 從設定中移除腳本。

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### 範例2：顯示結果

此範例會將 **MaximumReceivedObjectSizeMB** 屬性的值增加為20。 此命令也會提示您重新開機 **WinRM** 服務。 在 **WinRM** 服務重新開機之前，變更將不會生效。

```powershell
Set-PSSessionConfiguration -Name "IncObj" -MaximumReceivedObjectSizeMB 20
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\IncObj\InitializationParameters

ParamName                       ParamValue
---------                       ----------
psmaximumreceivedobjectsizemb   20

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
```

### 範例3：以不同方式顯示結果

在此範例中，會將 `Set-PSSessionConfiguration` **MaintenanceShell** 會話設定中的啟動腳本變更為 `Maintenance.ps1` 。 輸出會顯示變更，並提示您重新開機 **WinRM** 服務。 回應是 "y" (是)。

`Get-PSSessionConfiguration` 取得 **MaintenanceShell** 會話設定。 管線運算子 (|) 將命令的結果傳送至，這會將設定 `Format-List` 物件的所有屬性顯示在清單中。 接下來，使用 WSMan 提供者來查看 **MaintenanceShell** 設定的初始化參數。 `Get-ChildItem` (別名 `dir`) 取得 **MaintenanceShell** 外掛程式 **InitializationParameters** 節點中的子專案。 如需 WSMan 提供者的詳細資訊，請輸入 `Get-Help wsman` 。

```powershell
Set-PSSessionConfiguration -Name "MaintenanceShell" -StartupScript "C:\ps-test\Maintenance.ps1"
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName            ParamValue
---------            ----------
startupscript        c:\ps-test\Mainte...

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run
the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

```

```powershell
Get-PSSessionConfiguration MaintenanceShell | Format-List -Property *
```

```Output
xmlns            : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
Name             : MaintenanceShell
Filename         : %windir%\system32\pwrshplugin.dll
SDKVersion       : 1
XmlRenderingType : text
lang             : en-US
PSVersion        : 2.0
startupscript    : c:\ps-test\Maintenance.ps1
ResourceUri      : http://schemas.microsoft.com/powershell/MaintenanceShell
SupportsOptions  : true
ExactMatch       : true
Capability       : {Shell}
Permission       :
```

```powershell
dir WSMan:\localhost\Plugin\MaintenanceShell\InitializationParameters
```

```Output
ParamName     ParamValue
---------     ----------
PSVersion     2.0
startupscript c:\ps-test\Maintenance.ps1
```

## PARAMETERS

### -AccessMode

啟用和停用工作階段設定，並判斷是否可以用於電腦上的遠端或本機工作階段。 此參數可接受的值為：

- 停用。 停用工作階段設定。 它不能用於電腦的遠端或本機存取。 此值會將會話設定的 **Enabled** 屬性 (`WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled`) 設定為 **False** 。
- 本機。 將 **Network_Deny_All** 項目新增到工作階段設定的安全性描述元。
  本機電腦的使用者可以使用會話設定在同一部電腦上建立本機回送會話，但是遠端使用者會被拒絕存取。
- 遠端。 將 **Deny_All** 和 **Network_Deny_All** 項目從工作階段設定的安全性描述元中移除。 本機電腦和遠端電腦的使用者可以使用工作階段設定來建立工作階段，並在這部電腦上執行命令。

預設值為 [ **遠端** ]。

其他 Cmdlet 稍後可以覆寫這個參數的值。 例如，Cmdlet 會 `Enable-PSRemoting` 啟用電腦上的所有會話設定，並允許遠端存取，而此 `Disable-PSRemoting` Cmdlet 只允許本機存取電腦上的所有會話設定。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationBase

指定 \* 在 **AssemblyName** 參數的值中指定之元件檔 (.dll) 的路徑。

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssemblyName

指定組件名稱。 此 Cmdlet 會根據元件中定義的類別建立會話設定。

輸入定義會話設定之元件 .dll 檔案的檔案名或完整路徑。 如果您只輸入檔案名，您可以在 **ApplicationBase** 參數的值中輸入路徑。

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationTypeName

指定 **AssemblyName** 參數內的組件中定義的工作階段設定類型。 您指定的類型必須實作 **System.Management.Automation.Remoting.PSSessionConfiguration** 類別。

指定組件名稱時，此參數是必要的。

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

抑制所有使用者提示，並在不提示的情況下重新開機 **WinRM** 服務。 重新啟動服務可讓設定變更生效。

若要避免重新啟動並抑制重新啟動提示，請使用 **NoServiceRestart** 參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedDataSizePerCommandMB

指定可在任何單一遠端命令中傳送給這部電腦的資料量限制。 輸入資料大小 (單位為 MB)。 預設值為 50 MB。

如果資料大小限制定義于 **ConfigurationTypeName** 參數中指定的設定類型，則會使用設定類型中的限制。 此參數的值會被忽略。

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedObjectSizeMB

指定可在任何單一物件中傳送給這部電腦的資料量限制。
輸入資料大小（以 mb 為單位）。 預設值為 10 MB。

如果物件大小限制定義于 **ConfigurationTypeName** 參數中指定的設定類型，則會使用設定類型中的限制。 此參數的值會被忽略。

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

指定要自動匯入使用工作階段設定之工作階段的模組和嵌入式管理單元。 請輸入模組和嵌入式管理單元名稱。

依預設，只有在會話中會匯入 [ **Microsoft** ]，但除非已排除 Cmdlet，否則您可以使用 `Import-Module` 和 Add-PSSnapin Cmdlet，將模組和嵌入式管理單元新增至會話。

此參數值中指定的模組會匯入至會話設定檔中指定的模組新增 (`New-PSSessionConfigurationFile`) 。 不過，工作階段設定檔中的設定可以隱藏模組所匯出的命令，或是防止使用者使用它們。

此參數值中指定的模組會使用 Cmdlet 的 **ModulesToImport** 參數來取代指定的模組清單 `Register-PSSessionConfiguration` 。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定您想要變更之工作階段設定的名稱。

您無法使用這個參數來變更工作階段設定的名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoServiceRestart

不會重新開機 **WinRM** 服務，並抑制重新開機服務的提示。

依預設，當您執行時 `Set-PSSessionConfiguration` ，系統會提示您重新開機 **WinRM** 服務，讓新的會話設定生效。 在 **WinRM** 服務重新開機之前，新的會話設定不會生效。

若要重新開機 **WinRM** 服務而不提示，請使用 **Force** 參數。 若要手動重新開機 **WinRM** 服務，請使用 `Restart-Service` Cmdlet。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定會話設定檔 ( .pssc) 的路徑，例如 Cmdlet 所建立的檔案 `New-PSSessionConfigurationFile` 。 若省略路徑，則預設為目前目錄。

如需有關如何修改會話設定檔的詳細資訊，請參閱 Cmdlet 的說明主題 `New-PSSessionConfigurationFile` 。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSVersion

指定使用此會話設定之會話中的 PowerShell 版本。

此參數的值優先順序高於工作階段設定檔中的 **PowerShellVersion** 索引鍵值。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsCredential

指定會話中命令的認證。 根據預設，命令以目前使用者的權限執行。

此參數是在 PowerShell 3.0 中引進。

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

### -SecurityDescriptorSddl

為設定指定不同的 Security Descriptor Definition Language (SDDL) 字串。

此字串會決定使用新工作階段設定的必要權限。 若要在會話中使用會話設定，使用者至少必須有設定的 Execute (Invoke) 許可權。

若要使用設定的預設安全描述項，請輸入空字串 ( "" ) 或的值 `$Null` 。 預設值為 WSMan: 磁碟機中的根 SDDL。

如果安全描述項很複雜，請考慮使用 **ShowSecurityDescriptorUI** 參數而非此參數。 您無法在相同的命令中使用這兩個參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionTypeOption

指定會話設定的特定類型選項。 輸入會話類型選項物件，例如 Cmdlet 所傳回的 **new-psworkflowexecutionoption** 物件 `New-PSWorkflowExecutionOption` 。

使用工作階段設定之工作階段的選項，取決於工作階段選項和工作階段設定選項的值。 除非已指定，否則會話中設定的選項（例如使用 `New-PSSessionOption` Cmdlet）優先于會話設定中設定的選項。 不過，工作階段選項值不能超過工作階段設定中設定的最大值。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowSecurityDescriptorUI

指出此 Cmdlet 是可協助您為會話設定建立新 SDDL 的屬性工作表。 當您執行 `Set-PSSessionConfiguration` 命令並重新啟動 **WinRM** 服務之後，就會顯示內容表。

當您將許可權設定為設定時，請記住，使用者必須至少擁有 Execute (Invoke) 許可權，才能在會話中使用會話設定。

您無法在相同的命令中使用 **SecurityDescriptorSDDL** 參數與此參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StartupScript

指定設定的啟動腳本。 輸入 PowerShell 腳本的完整路徑。 指定的指令碼會在使用工作階段設定的新工作階段中執行。

若要將啟動腳本從會話設定中刪除，請輸入空字串 ( "" ) 或的值 `$Null` 。

您可以使用啟動腳本來進一步設定使用者會話。 如果腳本產生錯誤（即使是非終止錯誤），則不會建立會話，且 `New-PSSession` 命令會失敗。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThreadOptions

指定設定中的執行緒選項設定。 此設定會定義在工作階段中執行某個命令時，要如何建立及使用執行緒。 此參數可接受的值為：

- 預設
- ReuseThread
- UseCurrentThread
- UseNewThread

預設值為 **UseCurrentThread** 。

如需詳細資訊，請參閱 [ Psthreadoptions 列舉](/dotnet/api/system.management.automation.runspaces.psthreadoptions)。

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TransportOption

指定會話設定的傳輸選項。 輸入傳輸選項物件，例如 Cmdlet 所傳回的 **WSManConfigurationOption** 物件 `New-PSTransportOption` 。

使用工作階段設定之工作階段的選項，取決於工作階段選項和工作階段設定選項的值。 除非已指定，否則會話中設定的選項（例如使用 `New-PSSessionOption` Cmdlet）優先于會話設定中設定的選項。 不過，工作階段選項值不能超過工作階段設定中設定的最大值。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSharedProcess

只使用一個進程來裝載由相同使用者啟動的所有會話，並使用相同的會話設定。 根據預設，每個工作階段會裝載於自己的處理程序。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### Microsoft.wsman.management.wsmanconfigleafelement。

## 注意

若要執行此 Cmdlet，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。

此 `Set-PSSessionConfiguration` Cmdlet 不會變更設定名稱，且 **WSMan** 提供者不支援此 `Rename-Item` Cmdlet。 若要變更會話設定的名稱，請使用 `Unregister-PSSessionConfiguration` Cmdlet 來刪除設定，然後使用指令程式 `Register-PSSessionConfiguration` 來建立及註冊新的會話設定。

您可以使用 `Set-PSSessionConfiguration` Cmdlet 來變更預設的 microsoft.powershell32 會話設定。 它們並不受保護。 若要還原為預設會話設定的原始版本，請使用 `Unregister-PSSessionConfiguration` Cmdlet 來刪除預設會話設定，然後使用指令程式 `Enable-PSRemoting` 來還原它。

工作階段設定物件的屬性取決於工作階段設定所設定的選項，以及這些選項的值。 此外，使用工作階段設定檔的工作階段設定會有額外的屬性。

您可以使用 WSMan: 磁碟機中的命令來變更工作階段設定的屬性。
不過，您無法使用 PowerShell 2.0 中的 WSMan：磁片磁碟機來變更 PowerShell 3.0 中引進的會話設定屬性，例如 **OutputBufferingMode** 。 Windows PowerShell 2.0 命令不會產生錯誤，但它們沒有效果。 若要變更 PowerShell 3.0 中引進的屬性，請使用 PowerShell 3.0 中的 WSMan：磁片磁碟機。

## 相關連結

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供者](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
