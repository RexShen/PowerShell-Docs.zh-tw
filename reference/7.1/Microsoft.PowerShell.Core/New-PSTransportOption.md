---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: 7b7734c60a6a13d86f398418aeefce932e91a363
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205443"
---
# New-PSTransportOption

## 概要
建立包含工作階段設定之進階選項的物件。

## SYNTAX

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## DESCRIPTION

**New-PSTransportOption** Cmdlet 建立包含工作階段設定之傳輸選項的物件。
您可以使用該物件做為建立或變更工作階段設定之 Cmdlet 的 *TransportOption* 參數值，例如 Register-PSSessionConfiguration 和 Set-PSSessionConfiguration Cmdlet。

您也可以透過編輯工作階段設定屬性的 WSMan: 磁碟機的值來變更傳輸選項設定。
如需詳細資訊，請參閱＜WSMan 提供者＞。

會話設定選項代表伺服器端上設定的會話值，或是遠端連線的接收端。
用戶端或連接結束時，可以在建立會話時，或者用戶端與會話中斷連線或重新連接時，設定會話選項值。
除非另有說明，否則當設定值衝突時，用戶端值的優先順序較高。
不過，用戶端值不能違反工作階段設定中設定的最大值與配額。

如果沒有參數， **>new-pstransportoption** 會產生一個傳輸選項物件，其所有選項都有 null 值。
如果您省略參數，該參數代表的物件屬性就會是 Null 值。
Null 值不會影響會話設定。

如需工作階段選項的詳細資訊，請參閱 New-PSSessionOption。
如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：產生預設傳輸選項

```powershell
New-PSTransportOption
```

```Output
ProcessIdleTimeoutSec           :
MaxIdleTimeoutSec               :
MaxSessions                     :
MaxConcurrentCommandsPerSession :
MaxSessionsPerUser              :
MaxMemoryPerSessionMB           :
MaxProcessesPerSession          :
MaxConcurrentUsers              :
IdleTimeoutSec                  :
OutputBufferingMode             :
```

此命令會執行不含參數的 **新 >new-pstransportoption** 。
輸出顯示此 Cmdlet 會產生所有屬性都是 null 值的傳輸選項物件。

### 範例2：取得會話設定選項

此範例示範如何使用傳輸選項物件設定會話設定選項。

```powershell
$t = New-PSTransportOption -MaxSessions 40
Register-PSSessionConfiguration -Name ITTasks -TransportOption $t
Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITTasks
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
MaxShells                     : 40
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 2
Name                          : ITTasks
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
Enabled                       : True
MaxShellsPerUser              : 25
Permission                    :
```

第一個命令使用 **New-PSTransportOption** Cmdlet 建立一個傳輸選項物件，它會儲存在 $t 變數中。 命令使用 *MaxSessions* 參數將工作階段數目上限增加為 40。

第二個命令使用 **Register-PSSessionConfiguration** Cmdlet 建立 ITTasks 工作階段設定。 命令使用 *TransportOption* 參數指定 $t 變數中的傳輸選項物件。

第三個命令會使用 Get-PSSessionConfiguration Cmdlet 來取得 ITTasks 會話設定，並使用 Format-List Cmdlet 將會話設定物件的所有屬性顯示在清單中。 輸出顯示工作階段設定的 **MaxShells** 屬性值為 40。

### 範例3：設定傳輸選項

此命令示範在工作階段設定中設定傳輸選項對使用工作階段設定的工作階段的效果。

```powershell
$t = New-PSTransportOption -IdleTimeoutSec 3600
Set-PSSessionConfiguration -Name ITTasks -TransportOption $t
$s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks
$s | Format-List -Property *
```

```Output
State                  : Opened
IdleTimeout            : 3600000
OutputBufferingMode    : Block
ComputerName           : localhost
ConfigurationName      : ITTasks
InstanceId             : 4110c3f5-68ea-40fa-9bbf-04a433dbb02d
Id                     : 1
Name                   : MyITTasks
Availability           : Available
ApplicationPrivateData : {PSVersionTable}
Runspace               : System.Management.Automation.RemoteRunspace
```

第一個命令使用 **New-PSTransportOption** Cmdlet 建立傳輸選項物件。 命令使用 *IdleTimeoutSec* 參數設定物件的 **IdleTimeoutSec** 屬性值為 1 小時 (3600 秒)。 命令會將傳輸選項物件儲存在 $t 變數中。

第二個命令使用 Set-PSSessionConfiguration Cmdlet 來變更 ITTasks 會話設定的傳輸選項。 命令使用 *TransportOption* 參數指定 $t 變數中的傳輸選項物件。

第三個命令使用 New-PSSession Cmdlet 在本機電腦上建立 MyITTasks 會話。 命令使用 **ConfigurationName** 屬性指定 ITTasks 工作階段設定。 命令會將會話儲存在 $s 變數中。請注意，此命令不會使用 **新的-PSSession** 的 *SessionOption* 參數來設定會話的自訂空閒超時時間。 如果有的話，在會話選項中設定的閒置超時值將會優先于會話設定中的閒置超時設定。

第四個命令使用 Format-List Cmdlet，在清單中顯示 $s 變數中會話的所有屬性。 輸出顯示會話的閒置時間已達一小時， (360000 毫秒) 。

## PARAMETERS

### -IdleTimeoutSec

決定在遠端電腦未收到來自本機電腦的任何通訊時，每個會話保持開啟的時間長度。
這包括了信號信號。
當間隔時間過期時，工作階段就會關閉。

當使用者想要中斷連線並重新連線至會話時，空閒超時值相當重要。
只有當工作階段尚未逾時時，使用者才可以重新連線。

*IdleTimeoutSec* 參數對應工作階段設定的 **IdleTimeoutMs** 屬性。

輸入以秒為單位的值。
預設值為 7200 (2 小時)。
最小值為 60 (1 分鐘)。
最大值是 WSMan 設定中 Shell 物件的 **IdleTimeout** 屬性值 (`WSMan:\\\<ComputerName\>\Shell\IdleTimeout`) 。
預設值為 7200000 毫秒 (2 小時)。

如果在會話選項中與會話設定中設定了閒置的超時值，會話選項中設定的值會優先，但是它不能超過會話設定之 **MaxIdleTimeoutMs** 屬性的值。
若要設定 **MaxIdleTimeoutMs** 屬性的值，請使用 *MaxIdleTimeoutSec* 參數。

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxConcurrentCommandsPerSession

將每個會話中可同時執行的命令數目限制為指定的值。
預設值為 1000。

*MaxConcurrentCommandsPerSession* 參數會對應至工作階段設定的 **MaxConcurrentCommandsPerShell** 屬性。

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxConcurrentUsers

將每個會話中可同時執行命令的使用者數目限制為指定的值。
預設值為 5。

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxIdleTimeoutSec

將每個會話的閒置超時設定限制為指定的值。
預設值為 \[Int\]::MaxValue (~25 天)。

當使用者想要中斷連線並重新連線至會話時，空閒超時值相當重要。
只有當工作階段尚未逾時時，使用者才可以重新連線。

*MaxIdleTimeoutSec* 參數會對應到工作階段設定的 **MaxIdleTimeoutMs** 屬性。

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxMemoryPerSessionMB

限制每個工作階段所使用的記憶體為指定的值。
輸入以 MB 為單位的值。
預設值為 1024 MB (1 GB)。

*MaxMemoryPerSessionMB* 參數會對應到工作階段設定的 **MaxMemoryPerShellMB** 屬性。

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxProcessesPerSession

限制每個工作階段中執行的處理程序數目為指定的值。
預設值為 15。

*MaxProcessesPerSession* 參數會對應到工作階段設定的 **MaxProcessesPerShell** 屬性。

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxSessions

限制使用工作階段設定的工作階段數目。
預設值為 25。

*MaxSessions* 參數會對應到工作階段設定的 **MaxShells** 屬性。

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxSessionsPerUser

限制使用工作階段設定，並使用指定使用者的認證執行的工作階段數目為指定的值。
預設值為 25。

當您指定此值時，請考慮許多使用者可能使用「執行身分」使用者的認證。

*MaxSessionsPerUser* 參數會對應到工作階段設定的 **MaxShellsPerUser** 屬性。

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OutputBufferingMode

決定在輸出緩衝區已滿時，在中斷連線的工作階段中管理命令輸出的方式。
此參數可接受的值為：

- 區塊。
當輸出緩衝區已滿時，會暫停執行直到清除緩衝區為止。
- Drop：
當輸出緩衝區已滿時，會繼續執行。
儲存新的輸出時，會捨棄最舊的輸出。
- 無。
未指定輸出緩衝模式。

會話的 **OutputBufferingMode** 屬性預設值為 Block。

```yaml
Type: System.Nullable`1[System.Management.Automation.Runspaces.OutputBufferingMode]
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProcessIdleTimeoutSec

將每個主機進程的超時時間限制為指定的值。
預設值為0，表示進程沒有超時值。

其他會話設定會有每個進程的超時值。
例如， (8 小時) ，則 **工作流程** 會話設定的每個進程超時值為28800秒。

```yaml
Type: System.Nullable`1[System.Int32]
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

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### Microsoft.PowerShell.Commands.WSManConfigurationOption

## 注意

- 工作階段設定物件的屬性取決於工作階段設定所設定的選項，以及這些選項的值。 此外，使用工作階段設定檔的工作階段設定會有額外的屬性。

## 相關連結

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

