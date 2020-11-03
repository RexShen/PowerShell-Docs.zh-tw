---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSSessionConfiguration
ms.openlocfilehash: c0dd413e315d5905467d5591ed64eb971cbb0dbe
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201488"
---
# Register-PSSessionConfiguration

## 概要
建立並登錄新的工作階段設定。

## SYNTAX

### NameParameterSet (預設值)

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-ApplicationBase <String>]
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AssemblyNameParameterSet

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-AssemblyName] <String>
 [-ApplicationBase <String>] [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionConfigurationFile

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String>
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Register-PSSessionConfiguration` Cmdlet 會在本機電腦上建立並註冊新的會話設定。 這是您可以用來為遠端使用者建立自訂會話的 advanced Cmdlet。

每個 PowerShell 會話 ( **PSSession** ) 都會使用會話設定，也稱為端點。
當使用者建立連線到電腦的會話時，他們可以選取會話設定，或使用當您啟用 PowerShell 遠端功能時所註冊的預設會話設定。
使用者也可以設定 $PSSessionConfigurationName 喜好設定變數，指定目前工作階段中所建立的遠端工作階段預設設定。

工作階段設定定義遠端工作階段的環境。 設定可以決定哪些命令和語言元素可用於工作階段，並且可包含用來保護電腦的設定，例如工作階段在單一物件或命令中可以遠端接收的資料量限制。 會話設定的安全描述項會決定哪些使用者有權使用會話設定。

您可以使用實作新設定類別的組件，以及使用在工作階段中執行的指令碼來定義設定元素。 從 PowerShell 3.0 開始，您也可以使用會話設定檔來定義會話設定。

如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。
如需會話設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。

## 範例

### 範例1：註冊 NewShell 會話設定

在此範例中，我們會註冊 **NewShell** 會話設定。 **AssemblyName** 和 **ApplicationBase** 參數會指定 **MyShell.dll** 檔的位置，以指定會話設定中的 Cmdlet 和提供者。 **ConfigurationTypeName** 參數會指定要從元件使用的設定類別。

```powershell
$sessionConfiguration = @{
    Name='NewShell'
    ApplicationBase='c:\MyShells\'
    AssemblyName='MyShell.dll'
    ConfigurationTypeName='MyClass'
}
Register-PSSessionConfiguration @sessionConfiguration
```

若要使用此設定，請輸入 `New-PSSession -ConfigurationName newshell` 。

### 範例2：註冊 MaintenanceShell 會話設定

此範例會在本機電腦上註冊 **MaintenanceShell** 會話設定。 **StartupScript** 參數會指定 `Maintenance.ps1` 腳本。

```powershell
Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
```

當使用者使用 `New-PSSession` 命令並選取 **MaintenanceShell** 設定時， `Maintenance.ps1` 腳本會在新的會話中執行。 腳本可以設定會話。 這包括匯入模組，以及設定會話的執行原則。 如果腳本產生任何錯誤（包括非終止錯誤），則 `New-PSSession` 命令會失敗。

### 範例3：註冊會話設定

此範例會註冊 **AdminShell** 會話設定。

`$sessionParams`變數是包含所有參數值的雜湊表。 此雜湊表會使用 PowerShell 展開傳遞給 Cmdlet。 此 `Register-PSSessionConfiguration` 命令會使用 **SecurityDescritorSDDL** 參數在變數的值中指定 SDDL `$sddl` ，並使用 **MaximumReceivedObjectSizeMB** 參數來增加物件大小限制。 它也使用 **StartupScript** 參數，指定設定工作階段的指令碼。

```powershell
$sddl = "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;FA;SA;GWGX;;WD)"
$sessionParams = @{
    Name="AdminShell"
    SecurityDescriptorSDDL=$sddl
    MaximumReceivedObjectSizeMB=20
    StartupScript="C:\scripts\AdminShell.ps1"
}
Register-PSSessionConfiguration @sessionParams
```

### 範例4：傳回設定容器元素

此範例說明如何註冊 **MaintenanceShell** 設定。
`Register-PSSessionConfiguration` 傳回儲存在變數中的 **WSManConfigContainerElement** 物件 `$s` 。 `Format-List` 顯示傳回物件的所有屬性。 **PSPath** 屬性顯示物件會儲存在 WSMan: 磁碟機的目錄中。 `Get-ChildItem` (別名 `dir`) 顯示路徑中的專案 `WSMan:\LocalHost\PlugIn` 。 其中包括新的 **MaintenanceShell** 設定，以及 PowerShell 隨附的兩個預設設定。

```powershell
$s = Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
$s | Format-List -Property *
dir WSMan:\LocalHost\Plugin
```

```Output
PSPath            : Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell
PSParentPath      : Microsoft.WSMan.Management\WSMan::localhost\Plugin
PSChildName       : MaintenanceShell
PSDrive           : WSMan
PSProvider        : Microsoft.WSMan.Management\WSMan
PSIsContainer     : True
Keys              : {Name=MaintenanceShell}
Name              : MaintenanceShell
TypeNameOfElement : Container

Name                      Type                 Keys
----                      ----                 ----
MaintenanceShell          Container            {Name=MaintenanceShell}
microsoft.powershell      Container            {Name=microsoft.powershell}
microsoft.powershell32    Container            {Name=microsoft.powershell32}
```

### 範例5：使用啟動腳本註冊會話設定

在此範例中，我們會建立並註冊 **WithProfile** 會話設定。 **StartupScript** 參數會指示 PowerShell 針對任何使用會話設定的會話執行指定的腳本。

```powershell
Register-PSSessionConfiguration -Name WithProfile -StartupScript Add-Profile.ps1
```

指令碼包含在目前工作階段範圍內使用點執行來執行使用者 **CurrentUserAllHosts** 設定檔的單一命令。

如需設定檔的詳細資訊，請參閱 [about_Profiles](./About/about_Profiles.md)。 如需點執行的詳細資訊，請參閱 [about_Scopes](./About/about_Scopes.md)。

## PARAMETERS

### -AccessMode

啟用和停用工作階段設定，並判斷是否可以用於電腦上的遠端或本機工作階段。 此參數可接受的值為：

- 停用。 停用工作階段設定。 它不能用於電腦的遠端或本機存取。
- 本機。 允許本機電腦的使用者使用會話設定在同一部電腦上建立本機回送會話，但拒絕遠端使用者的存取。
- 遠端。 允許本機和遠端使用者使用工作階段設定，在此電腦上建立工作階段與執行命令。

預設值為 [遠端]。

其他 Cmdlet 稍後可以覆寫這個參數的值。 例如，此 Cmdlet 可讓您從 `Enable-PSRemoting` 遠端存取所有會話設定，此 `Enable-PSSessionConfiguration` Cmdlet 會啟用會話設定，而此 `Disable-PSRemoting` Cmdlet 會防止遠端存取所有會話設定。

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

指定 \* 在 **AssemblyName** 參數的值中指定之元件檔 (.dll) 的路徑。 當 **AssemblyName** 參數值不包含路徑時使用此參數。 預設值是目前的目錄。

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

指定定義設定類型之組件檔 (\*.dll) 的名稱。 您可以在此參數或 **ApplicationBase** 參數的值中指定 .dll 的路徑。

當您指定 **ConfigurationTypeName** 參數時，此參數為必要參數。

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

指定用於此設定之 Microsoft .NET Framework 類型的完整名稱。 您指定的類型必須實作 **System.Management.Automation.Remoting.PSSessionConfiguration** 類別。

若要指定可執行設定類型的元件檔 (\* .dll) ，請指定 **AssemblyName** 和 **ApplicationBase** 參數。

建立類型可讓您控制更多方面的會話設定，例如公開或隱藏 Cmdlet 的特定參數，或設定使用者無法覆寫的資料大小和物件大小限制。

如果您省略這個參數， **DefaultRemotePowerShellConfiguration** 類別會用於工作階段設定。

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

若要防止重新開機並抑制重新開機提示，請指定 **NoServiceRestart** 參數。

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

如果資料大小限制定義於 **ConfigurationTypeName** 參數中指定的設定類型，則會使用設定類型中的限制並忽略此參數的值。

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

如果物件大小限制定義於 **ConfigurationTypeName** 參數中指定的設定類型，則會使用設定類型中的限制並忽略此參數的值。

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

指定自動匯入至使用會話設定之會話的模組。

依預設，只會將 **Microsoft. Core** 匯入會話。 除非已排除 Cmdlet，否則您可以使用將 `Import-Module` 模組加入至會話。

此參數值中指定的模組會匯入至 **SessionType** 參數所指定的模組新增中，以及在會話設定檔中的 **ModulesToImport** 索引鍵中列出的模組 (`New-PSSessionConfigurationFile`) 。 不過，工作階段設定檔中的設定可以隱藏模組所匯出的命令，或是防止使用者使用它們。

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

指定工作階段設定的名稱。 這是必要參數。

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

依預設，當您執行 `Register-PSSessionConfiguration` 命令時，系統會提示您重新開機 **WinRM** 服務，讓新的會話設定生效。 在 **WinRM** 服務重新開機之前，新的會話設定不會生效。

若要重新啟動 **WinRM** 服務而不提示，請指定 **Force** 參數。 若要手動重新開機 **WinRM** 服務，請使用 `Restart-Service` Cmdlet。

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

指定會話設定檔的路徑和檔案名 (. .pssc) ，例如所建立的檔案 `New-PSSessionConfigurationFile` 。 若省略路徑，則預設為目前目錄。

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

### -ProcessorArchitecture

判斷在使用此會話設定的會話中，是否已啟動32位或64位版本的 PowerShell 進程。 此參數可接受的值為： x86 (32 位) 和 AMD64 (64 位) 。 預設值是由裝載工作階段設定之電腦的處理器架構決定。

您可以使用此參數，在 64 位元電腦上建立 32 位元的工作階段。 嘗試在 32 位元電腦上建立 64 位元處理程序將會失敗。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PA
Accepted values: x86, amd64

Required: False
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

指定設定的 Security Descriptor Definition Language (SDDL) 字串。

此字串會決定使用新工作階段設定的必要權限。 若要在會話中使用會話設定，使用者至少必須有設定的 Execute (Invoke) 許可權。

如果安全性描述元很複雜，請考慮使用 **ShowSecurityDescriptorUI** 參數而非此參數。 您無法在相同的命令中使用這兩個參數。

如果您省略這個參數， **WinRM** 服務的根 SDDL 會用於此設定。
若要檢視或變更根 SDDL，請使用 WSMan 提供者。 例如 `Get-Item wsman:\localhost\service\rootSDDL` 。 如需 WSMan 提供者的詳細資訊，請輸入 `Get-Help wsman` 。

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

指出此 Cmdlet 會顯示可協助您建立會話設定之 SDDL 的屬性工作表。 當您輸入 `Register-PSSessionConfiguration` 命令並重新啟動 **WinRM** 服務之後，就會顯示內容表。

設定設定的許可權時，請記住，使用者必須至少擁有 Execute (Invoke) 許可權，才能在會話中使用會話設定。

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

指定 PowerShell 腳本的完整路徑。 指定的指令碼會在使用工作階段設定的新工作階段中執行。

您可以使用腳本來額外設定會話。 如果腳本產生錯誤（即使是非終止錯誤），則不會建立會話，且 `New-PSSession` 命令會失敗。

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

指定當命令在會話中執行時，如何建立及使用執行緒。 此參數可接受的值為：

- 預設
- ReuseThread
- UseCurrentThread
- UseNewThread

預設值為 **UseCurrentThread** 。

如需詳細資訊，請參閱 [ Psthreadoptions 列舉](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0)。

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

指定傳輸選項。

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

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

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

### -ThreadApartmentState

指定要使用之執行緒模組的單元狀態。 可接受的值如下：

- Unknown
- MTA
- STA

```yaml
Type: System.Threading.ApartmentState
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### Microsoft.WSMan.Management.WSManConfigContainerElement

## 注意

若要執行此 Cmdlet，您必須使用 [ **以系統管理員身分執行** ] 選項啟動 PowerShell。

此 Cmdlet 會產生代表 Management (WS-MANAGEMENT) 外掛程式設定之 Web 服務的 XML，並將 XML 傳送至 WS-MANAGEMENT，以在本機電腦上註冊外掛程式 (`New-Item wsman:\localhost\plugin`) 。

工作階段設定物件的屬性取決於工作階段設定所設定的選項，以及這些選項的值。 此外，使用工作階段設定檔的工作階段設定會有額外的屬性。

## 相關連結

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Unregister-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan 提供者](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
