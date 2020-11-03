---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disconnect-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-PSSession
ms.openlocfilehash: b3ee9ce8f699e66a091a017eb8c1b0c49f1b7636
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205543"
---
# Disconnect-PSSession

## 概要
從工作階段中斷連線。

## SYNTAX

### 工作階段 (預設)

```
Disconnect-PSSession [-Session] <PSSession[]> [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Name

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Disconnect-PSSession`Cmdlet 會 `New-PSSession` 從目前的會話中斷 ( "PSSession" ) 的 PowerShell 會話連線，例如使用 Cmdlet 啟動的會話。 如此一來，PSSession 就處於中斷連線的狀態。 您可以從目前的工作階段，或從本機電腦或另一部電腦的另一個工作階段，連線到中斷連線的 PSSession。

此 `Disconnect-PSSession` Cmdlet 只會中斷連接到目前會話的開啟 pssession。 `Disconnect-PSSession` 無法中斷中斷或關閉的 Pssession，或使用 Cmdlet 啟動的互動式 Pssession， `Enter-PSSession` 而且無法中斷連接到其他會話的 pssession。

若要重新連線到中斷連線的 PSSession，請使用 `Connect-PSSession` 或 `Receive-PSSession` Cmdlet。

當 PSSession 已中斷連線時，PSSession 中的命令會繼續執行，直到它們完成為止，除非 PSSession 逾時或 PSSession 中的命令被已滿的輸出緩衝區封鎖。 若要變更閒置逾時，請使用 **IdleTimeoutSec** 參數。 若要變更輸出緩衝處理模式，請使用 **OutputBufferingMode** 參數。您也可以使用 Cmdlet 的 **InDisconnectedSession** 參數，在中斷連線的 `Invoke-Command` 會話中執行命令。

如需中斷連線工作階段功能的詳細資訊，請參閱 [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)。

此 Cmdlet 是在 Windows PowerShell 3.0 引進。

## 範例

### 範例 1-依名稱中斷會話的連線

此命令中斷 Server01 電腦上 UpdateSession PSSession 與目前工作階段的連線。 命令使用 **Name** 參數來識別 PSSession。

```
PS> Disconnect-PSSession -Name UpdateSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  UpdateSession   Server01        Disconnected  Microsoft.PowerShell          None
```

輸出顯示中斷連線的嘗試成功。 工作階段狀態是 Disconnected 且可用性是 None，表示工作階段並非忙碌中，且可以重新連線。

### 範例 2-中斷會話與特定電腦的連線

此命令中斷 Server12 電腦上 ITTask PSSession 與目前工作階段的連線。
ITTask 工作階段是在目前的工作階段中建立，並連線 Server12 電腦。 此命令會使用 `Get-PSSession` Cmdlet 來取得會話，並使用 `Disconnect-PSSession` Cmdlet 將它中斷連接。

```
PS> Get-PSSession -ComputerName Server12 -Name ITTask |
  Disconnect-PSSession -OutputBufferingMode Drop -IdleTimeoutSec 86400
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  ITTask          Server12        Disconnected  ITTasks               None
```

此 `Disconnect-PSSession` 命令會使用 **OutputBufferingMode** 參數，將輸出模式設定為 **Drop** 。 此設定確保即使工作階段輸出緩衝區已滿，工作階段中執行的指令碼仍可繼續執行。 因為指令碼會將其輸出寫入檔案共用上的報表，所以其他輸出即使遺失也不會受影響。

此命令也使用 **IdleTimeoutSec** 參數將工作階段的閒置逾時延長為 24 小時。 此設定可以讓此系統管理員或其他系統管理員有時間重新連線到工作階段，確認指令碼有執行和進行疑難排解 (如果需要)。

### 範例 3-在多部電腦上使用多個 Pssession

這一系列的命令會示範如何 `Disconnect-PSSession` 在企業案例中使用此 Cmdlet。 在本例中，新的技術人員在遠端電腦的工作階段中啟動一個指令碼，執行時產生了問題。 技術人員中斷工作階段的連線，讓較有經驗的管理員可以連線到工作階段並解決問題。

```
PS> $s = New-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
PS> Invoke-Command $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Get-PSSession -Name ITTask -ComputerName Srv1 | Disconnect-PSSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1 ITTask           Srv1            Disconnected  Microsoft.PowerShell          None

PS> Get-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None
 2 ITTask          Srv2            Opened        Microsoft.PowerShell     Available
 3 ITTask          Srv30           Opened        Microsoft.PowerShell     Available

PS> Get-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None

PS> $s = Connect-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
PS> Invoke-Command -Session $s {dir $home\Scripts\PatchStatusOutput.ps1}
PS> Invoke-Command -Session $s {mkdir $home\Scripts\PatchStatusOutput}
PS> Invoke-Command -Session $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Disconnect-PSSession -Session $s
```

技術人員先在許多遠端電腦上建立工作階段，並且在每個工作階段中執行指令碼。 第一個命令會使用 `New-PSSession` Cmdlet，在三部遠端電腦上建立 ITTask 會話。 命令會將工作階段儲存於 $s 變數中。 第二個命令會使用 Cmdlet 的 **FilePath** 參數 `Invoke-Command` ，在 $s 變數的會話中執行腳本。

在 Srv1 電腦上執行的指令碼產生未預期的錯誤。 技術人員連絡他的管理員並要求協助。 管理員會指示技術人員中斷會話的連線，讓他可以進行調查。第二個命令 `Get-PSSession` 會使用 Cmdlet 取得 Srv1 電腦上的 ITTask 會話，並使用 `Disconnect-PSSession` Cmdlet 將它中斷連接。 此命令不會影響其他電腦上的 ITTask 會話。

第三個命令會使用 `Get-PSSession` Cmdlet 來取得 ITTask 會話。 輸出顯示 Srv2 和 Srv30 電腦上的 ITTask 工作階段並未受到中斷連線命令的影響。

管理員登入家用電腦、連線到他的公司網路、啟動 PowerShell，然後使用 `Get-PSSession` Cmdlet 取得 Srv1 電腦上的 ITTask 會話。 他使用技術人員的認證存取工作階段。

接下來，管理員會使用此 `Connect-PSSession` Cmdlet 來連線到 Srv1 電腦上的 ITTask 會話。 命令會將工作階段儲存於 $s 變數中。

管理員會使用 `Invoke-Command` Cmdlet，在變數中的會話中執行一些診斷命令 `$s` 。 他找出指令碼失敗的原因是因為它找不到必要的目錄。
管理員會使用函式 `MkDir` 來建立目錄，然後重新開機 `Get-PatchStatus.ps1` 腳本並中斷會話的連線。管理員將他的結果回報給技術人員，建議他重新連接到會話以完成工作，並要求他將命令新增至 `Get-PatchStatus.ps1` 腳本，以建立必要的目錄（如果不存在的話）。

### 範例 4-變更 PSSession 的超時值

此範例示範如何更正工作階段的 **IdleTimeout** 屬性值讓它可以中斷連線。

工作階段的閒置逾時屬性對中斷連線的工作階段非常重要，因為它會決定中斷連線的工作階段在被刪除之前會維持多久的時間。 您可以在建立工作階段以及中斷工作階段的連線時，設定閒置逾時選項。 會話閒置時間的預設值是在 `$PSSessionOption` 本機電腦上的喜好設定變數，以及遠端電腦上的會話設定中設定。 為工作階段設定的值優先於工作階段設定中的值，但是工作階段值不能超過工作階段設定中所設定的配額，例如 **MaxIdleTimeoutMs** 值。

```
PS> $Timeout = New-PSSessionOption -IdleTimeout 172800000
PS> $s = New-PSSession -Computer Server01 -Name ITTask -SessionOption $Timeout
PS> Disconnect-PSSession -Session $s
Disconnect-PSSession : The session ITTask cannot be disconnected because the specified
idle timeout value 172800(seconds) is either greater than the server maximum allowed
43200 (seconds) or less that the minimum allowed60(seconds).  Choose an idle time out
value that is within the allowed range and try again.

PS> Invoke-Command -ComputerName Server01 {Get-PSSessionConfiguration Microsoft.PowerShell} |
 Format-List -Property *

Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/microsoft.powershell
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
SecurityDescriptorSddl        : O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GXGW;;;WD)
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 2147483647
Uri                           : http://schemas.microsoft.com/powershell/microsoft.powershell
SDKVersion                    : 2
Name                          : microsoft.powershell
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
ParentResourceUri             : http://schemas.microsoft.com/powershell/microsoft.powershell
Enabled                       : true
MaxShells                     : 25
MaxShellsPerUser              : 25
Permission                    : BUILTIN\Administrators AccessAllowed
PSComputerName                : localhost
RunspaceId                    : aea84310-6dbf-4c21-90ac-13980039925a
PSShowComputerName            : True


PS> $s.Runspace.ConnectionInfo
ConnectionUri                     : http://Server01/wsman
ComputerName                      : Server01
Scheme                            : http
Port                              : 80
AppName                           : /wsman
Credential                        :
ShellUri                          : http://schemas.microsoft.com/powershell/Microsoft.PowerShell
AuthenticationMechanism           : Default
CertificateThumbprint             :
MaximumConnectionRedirectionCount : 5
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
UseCompression                    : True
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
NoEncryption                      : False
UseUTF16                          : False
OutputBufferingMode               : Drop
IncludePortInSPN                  : False
Culture                           : en-US
UICulture                         : en-US
OpenTimeout                       : 180000
CancelTimeout                     : 60000
OperationTimeout                  : 180000
IdleTimeout                       : 172800000

PS> Disconnect-PSSession $s -IdleTimeoutSec 43200
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Disconnected  Microsoft.PowerShell          None

PS> $s.Runspace.ConnectionInfo.IdleTimeout
43200000
```

第一個命令會使用 `New-PSSessionOption` Cmdlet 來建立會話選項物件。 它使用 **IdleTimeout** 參數設定 48 小時 (172800000 毫秒) 的閒置逾時。 命令會將工作階段選項物件儲存在 $Timeout 變數中。

第二個命令會使用 `New-PSSession` Cmdlet 在 Server01 電腦上建立 ITTask 會話。 命令會將工作階段儲存在 $s 變數中。 **SessionOption** 參數的值是在 $Timeout 變數中的 48 小時閒置逾時。

第三個命令中斷 $s 變數中 ITTask 工作階段的連線。 此命令會失敗，因為工作階段的閒置逾時值超過工作階段設定中的 **MaxIdleTimeoutMs** 配額。 因為工作階段要在中斷連線之後，才會使用到閒置逾時，所以工作階段在使用中時，可能不會偵測到此違規。

第四個命令會使用 `Invoke-Command` `Get-PSSessionConfiguration` 指令程式在 Server01 電腦上執行 Microsoft PowerShell 會話設定的命令。 此命令會使用 `Format-List` Cmdlet，在清單中顯示會話設定的所有屬性。輸出顯示 **MaxIdleTimeoutMS** 屬性（可為使用會話設定的會話建立最大容許的 **IdleTimeout** 值）是43200000毫秒 (12 小時) 。

第五個命令取得 $s 變數中工作階段的工作階段選項值。 許多會話選項的值是會話之 [ **運行** 時] 屬性的 [ **ConnectionInfo** ] 屬性的屬性。輸出顯示會話的 **IdleTimeout** 屬性值為172800000毫秒 (48 小時) ，這違反會話設定中12小時的 **MaxIdleTimeoutMs** 配額。若要解決此衝突，您可以使用 **ConfigurationName** 參數來選取不同的會話設定，或使用 **IdleTimeout** 參數來減少會話的閒置時間。

第六個命令中斷工作階段的連線。 它使用 **IdleTimeoutSec** 參數設定最大 12 小時的閒置逾時。

第七個命令取得中斷連線工作階段的 **IdleTimeout** 屬性值，以毫秒為單位。 輸出確認命令成功。

## PARAMETERS

### -Id

中斷具指定工作階段識別碼的工作階段連線。 輸入一或多個識別碼 (以逗號分隔)，或使用範圍運算子 (..) 來指定某個範圍的識別碼。

若要取得會話的識別碼，請使用 `Get-PSSession` Cmdlet。 執行個體識別碼儲存在工作階段的 **ID** 屬性中。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IdleTimeoutSec

變更中斷連線 PSSession 的閒置逾時值。 輸入以秒為單位的值。 最小值為 60 (1 分鐘)。

閒置逾時決定中斷連線的 PSSession 在遠端電腦上維持的時間長度。 當逾時過期時，就會刪除 PSSession。

中斷連線的 PSSession 一旦中斷連線，便被視為閒置，即使命令仍然在中斷連線的工作階段中執行也是如此。

工作階段的閒置逾時預設值由工作階段設定的 **IdleTimeoutMs** 屬性所設定。 預設值為 7200000 毫秒 (2 小時)。

此參數的值會優先於 $PSSessionOption 喜好設定變數的 **IdleTimeout** 屬性，以及工作階段設定中的預設閒置逾時值。 不過，這個值不能超過工作階段設定的 **MaxIdleTimeoutMs** 屬性值。 **MaxIdleTimeoutMs** 的預設值為 12 小時 (43200000 毫秒)。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

中斷具指定執行個體識別碼的工作階段連線。

執行個體識別碼是 GUID，可唯一識別本機或遠端電腦上的某個階段作業。 執行個體識別碼是唯一的，甚至可跨多部電腦上的多個工作階段。

若要取得會話的實例識別碼，請使用 `Get-PSSession` Cmdlet。 實例識別碼儲存在會話的 **InstanceID** 屬性中。

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

中斷具指定易記名稱的工作階段連線。 允許使用萬用字元。

若要取得會話的易記名稱，請使用 `Get-PSSession` Cmdlet。 好記名稱儲存在工作階段的 **Name** 屬性中。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Session

中斷指定 PSSessions 的連線。 輸入 PSSession 物件，例如 Cmdlet 所傳回的物件 `New-PSSession` 。 您也可以使用管線將 PSSession 物件傳送至 `Disconnect-PSSession` 。

此 `Get-PSSession` Cmdlet 可以取得在遠端電腦上終止的所有 pssession，包括已中斷連線的 pssession，以及連線至其他電腦上其他會話的 pssession。 `Disconnect-PSSession` 只中斷連接到目前會話的 PSSession。 如果您以管線將其他 Pssession 傳送至 `Disconnect-PSSession` ，則 `Disconnect-PSSession` 命令會失敗。

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ThrottleLimit

設定命令的節流限制 `Disconnect-PSSession` 。

節流限制是可建立以執行此命令的最大同時連線數。 若省略此參數，或輸入值為 0，則會使用預設值 32。

節流限制僅適用於目前命令，不適用於工作階段或電腦。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputBufferingMode

決定當輸出緩衝區已滿時，如何管理中斷連線工作階段中的命令輸出。 預設值為 **Block** 。

如果中斷連線工作階段中的命令傳回輸出，且輸出緩衝區填滿，此參數的值可有效決定此命令是否要在工作階段中斷連線的情況下繼續執行。 **Block** 值會暫停命令，直到工作階段重新連線為止。 **Drop** 值允許命令完成，但可能會遺失資料。 使用 **Drop** 值時，請將命令輸出重新導向至磁碟上的檔案。

有效值為：

- **Block** ：當輸出緩衝區已滿時，會暫停執行直到清除緩衝區為止。
- **Drop** ：當輸出緩衝區已滿時，會繼續執行。 儲存新的輸出時，會捨棄最舊的輸出。
- **None** ：未指定輸出緩衝模式。 對於中斷連線的工作階段，則使用工作階段設定的 **OutputBufferingMode** 屬性值。

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Block
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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](./About/about_CommonParameters.md)。

## 輸入

### System.Management.Automation.Runspaces.PSSession

您可以使用管線將會話傳送至 `Disconnect-PSSession` 。

## 輸出

### System.Management.Automation.Runspaces.PSSession

`Disconnect-PSSession` 傳回代表其中斷連接之會話的物件。

## 注意

- `Disconnect-PSSession`只有當本機和遠端電腦執行 PowerShell 3.0 或更新版本時，此 Cmdlet 才會運作。
- 如果您在已 `Disconnect-PSSession` 中斷連線的會話上使用此 Cmdlet，此命令對會話沒有任何作用，且不會產生錯誤。
- 具有互動式安全性權杖 (使用 **EnableNetworkAccess** 參數所建立) 且已中斷連線的回送工作階段只能從當初建立該工作階段的電腦重新連線。 此限制可防止電腦遭受惡意存取。
- 當您中斷連線 PSSession 時，工作階段狀態為 **Disconnected** 且可用性為 **None** 。

  **State** 屬性的值是相對於目前工作階段。 因此，值為 **Disconnected** 表示 PSSession 並未連線目前工作階段。 不過，它並不表示 PSSession 中斷所有工作階段的連線。 它可能連線不同的工作階段。 若要判斷是否可以連線或重新連線工作階段，請使用 **Availability** 屬性。

  **Availability** 值為 **None** 表示您可以連線工作階段。 值為 **Busy** 表示您無法連線 PSSession，因為它已連線另一個工作階段。

  如需會話的 **State** 屬性值的詳細資訊，請參閱 [ runspacestate 列舉](/dotnet/api/system.management.automation.runspaces.runspacestate)。

  如需會話的 **Availability** 屬性值的詳細資訊，請參閱 [RunspaceAvailability 列舉](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。

## 相關連結

[Connect-PSSession](Connect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Receive-PSSession](Receive-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Remove-PSSession](Remove-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)

[about_Remote_Disconnected_Sessions](About/about_Remote_Disconnected_Sessions.md)
