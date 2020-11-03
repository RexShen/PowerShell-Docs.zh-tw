---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowexecutionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowExecutionOption
ms.openlocfilehash: db5d19396f555a41ad14552823c57f3b11c79321
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205431"
---
# New-PSWorkflowExecutionOption

## 概要

建立包含工作流程工作階段之工作階段設定選項的物件。

## SYNTAX

```
New-PSWorkflowExecutionOption [-PersistencePath <String>] [-MaxPersistenceStoreSizeGB <Int64>]
 [-PersistWithEncryption] [-MaxRunningWorkflows <Int32>] [-AllowedActivity <String[]>]
 [-OutOfProcessActivity <String[]>] [-EnableValidation] [-MaxDisconnectedSessions <Int32>]
 [-MaxConnectedSessions <Int32>] [-MaxSessionsPerWorkflow <Int32>] [-MaxSessionsPerRemoteNode <Int32>]
 [-MaxActivityProcesses <Int32>] [-ActivityProcessIdleTimeoutSec <Int32>]
 [-RemoteNodeSessionIdleTimeoutSec <Int32>] [-SessionThrottleLimit <Int32>]
 [-WorkflowShutdownTimeoutMSec <Int32>] [<CommonParameters>]
```

## DESCRIPTION

此 `New-PSWorkflowExecutionOption` Cmdlet 會建立一個物件，其中包含工作流程會話設定的 advanced 選項，也就是設計來執行 Windows PowerShell 工作流程工作流程的會話設定。

您可以使用 **new-psworkflowexecutionoption** 物件，它會 `New-PSWorkflowExecutionOption` 產生做為建立或變更會話設定之 Cmdlet 的 **SessionTypeOption** 參數值，例如 `Register-PSSessionConfiguration` 和 `Set-PSSessionConfiguration` Cmdlet。

Cmdlet 的每個參數都 `New-PSWorkflowExecutionOption` 代表 Cmdlet 所傳回之工作流程會話設定選項物件的屬性。 若省略參數，Cmdlet 會使用屬性的預設值來建立物件。

此 `New-PSWorkflowExecutionOption` Cmdlet 是 Windows PowerShell 工作流程功能的一部分。

您也可以新增工作流程一般參數到此命令。 如需工作流程一般參數的詳細資訊，請參閱 [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)。

此 Cmdlet 是在 Windows PowerShell 3.0 引進。

## 範例

### 範例1：建立工作流程選項物件

```powershell
New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
```

```Output
SessionThrottleLimit                       : 100
PersistencePath                            : C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell\WF\PS
MaxPersistenceStoreSizeGB                  : 10
PersistWithEncryption                      : False
MaxRunningWorkflows                        : 30
AllowedActivity                            : {PSDefaultActivities}
OutOfProcessActivity                       : {InlineScript}
EnableValidation                           : True
MaxDisconnectedSessions                    : 200
MaxConnectedSessions                       : 100
MaxSessionsPerWorkflow                     : 10
MaxSessionsPerRemoteNode                   : 5
MaxActivityProcesses                       : 5
ActivityProcessIdleTimeoutSec              : 60
RemoteNodeSessionIdleTimeoutSec            : 60
WorkflowShutdownTimeoutMSec                : 500
```

此命令會使用 `New-PSWorkflowExecutionOption` Cmdlet 將 **MaxSessionsPerWorkflow** 值增加為10，並將 **MaxDisconnectedSessions** 值減少為200。

輸出會顯示 Cmdlet 傳回的物件。

### 範例2：使用工作流程選項物件

```powershell
# Create a Workflow Options object and save it in a variable
$wo = New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
# Create the ITWorkflow session configuration
Register-PSSessionConfiguration -Name ITWorkflows -SessionTypeOption $wo -Force
```

```Output
    WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=ITWorkflows}                  ITWorkflows
```

```powershell
Get-PSSessionConfiguration ITWorkflows | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITWorkflows
MaxConcurrentCommandsPerShell : 1000
allowedactivity               : PSDefaultActivities
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
maxsessionsperworkflow        : 10
lang                          : en-US
sessionconfigurationdata      : <SessionConfigurationData>
                                    <Param Name='PrivateData'>
                                        <PrivateData>
                                            <ParamName='enablevalidation' Value='True'/>
                                            <Param Name='allowedactivity'Value='PSDefaultActivities' />
                                            <Param Name='outofprocessactivity' Value='InlineScript'/>
                                            <Param Name='maxdisconnectedsessions' Value='200' />
                                            <ParamName='maxsessionsperworkflow' Value='10'/>
                                        </PrivateData>
                                    </Param>
                                </SessionConfigurationData>
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 25
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
outofprocessactivity          : InlineScript
SDKVersion                    : 2
Name                          : ITWorkflows
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
enablevalidation              : True
Enabled                       : True
maxdisconnectedsessions       : 200
MaxShellsPerUser              : 25
Permission                    :
```

前兩個命令會建立新的會話設定物件，並加以註冊。

第三個命令會使用 `Get-PSSessionConfiguration` Cmdlet 來取得 ITWorkflows 會話設定，並使用 `Format-List` 來顯示清單中會話設定的所有屬性。輸出會顯示會話設定中的工作流程選項。 特別是，工作階段設定具有值為 10 的 **MaxSessionsPerWorkflow** 屬性，以及值為 200 的 **MaxDisconnectedSessions** 屬性。

## PARAMETERS

### -ActivityProcessIdleTimeoutSec

指定當處理程序成為閒置之後，每個活動主機處理程序的保留時間。 當間隔時間過期時，處理程序就會關閉。

輸入以秒為單位的值。 預設值為 60。

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

### -AllowedActivity

指定允許在工作階段中執行的活動。

輸入符合命名空間的活動名稱，例如 `Microsoft.Powershell.HyperV.Activities.*` 。
支援使用萬用字元。 預設值 **PSDefaultActivities** 包含內建的 Windows Workflow Foundation 活動與代表 Windows PowerShell Core Cmdlet 的活動。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: PSDefaultActivities
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableValidation

確認工作階段中的所有工作流程活動都已包含在允許活動清單中。

預設值為 true。 若要停用驗證，請使用下列命令格式： `-EnableValidation:$false` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxActivityProcesses

指定可在工作階段中建立以支援工作流程活動的處理程序數目上限。 預設值為 5。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxConnectedSessions

指定處於操作狀態的遠端工作階段數目上限。 此配額會套用到連線到所有遠端節點 (目標電腦) 的工作階段。 預設值是 100。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxDisconnectedSessions

指定處於中斷連線狀態的遠端工作階段數目上限。 此配額會套用到連線到所有遠端節點 (目標電腦) 的工作階段。 預設值為 1000。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1000
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxPersistenceStoreSizeGB

指定配置給在工作階段中執行之工作流程的持續性儲存區大小上限 (單位為 GB)。 超過該大小時，會擴充持續性儲存區以儲存所有持續性資料，但會顯示警告並寫入一個訊息到工作流程事件記錄檔。 預設值是 10。

持續性儲存區包含所有工作流程工作的資料。 儲存資料的能力可讓工作繼續執行，而不會遺失狀態。

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxRunningWorkflows

指定可以同時在工作階段中執行的工作流程數目上限。
預設值是 30。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 30
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxSessionsPerRemoteNode

指定可以連線到每個遠端節點 (目標電腦) 的工作階段數目上限。 預設值為 5。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxSessionsPerWorkflow

指定可以建立以支援每個工作流程的工作階段數目上限。 預設值為 5。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutOfProcessActivity

決定哪些允許的活動 (由 **AllowedActivities** 參數指定) 可跨處理序執行。 預設值為 **InlineScript** 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineScript
Accept pipeline input: False
Accept wildcard characters: False
```

### -PersistencePath

指定用來儲存工作流程狀態與資料的磁碟位置。 儲存工作流程狀態與資料可讓工作流程暫停並繼續，以及在發生中斷或網路故障時復原。

預設值是 `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PersistWithEncryption

表示工作流程會將持續性存放區中的資料加密。 將持續性資料儲存在網路共用時，請考慮使用此功能。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoteNodeSessionIdleTimeoutSec

指定當連線到遠端節點 (目標電腦) 的工作階段成為閒置時，應該保留該工作階段多久。

輸入以秒為單位的值。 預設值為 60。

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

### -SessionThrottleLimit

指定要建立多少操作以支援在工作階段中啟動的所有工作流程。 預設值是 100。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkflowShutdownTimeoutMSec

指定強制暫停工作階段中的所有工作流程之後，應該保留該工作階段多久。 逾時期間經過之後，Windows PowerShell 會關閉該工作階段 (即使並非所有工作流程都已暫停)。

輸入以毫秒為單位的值。
預設值為 500。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 500
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### New-psworkflowexecutionoption。

## 注意

超過此選項所設定的最大值時，用來在工作階段中建立另一個執行個體的命令會失敗，除非在參數描述中另有設定。 例如，若 **MaxConnectedSessions** 的值是 100。 用來建立 101st 工作階段以連線到遠端節點 (目標電腦) 的命令會失敗。

工作階段設定物件的屬性取決於工作階段設定所設定的選項，以及這些選項的值。 此外，使用工作階段設定檔的工作階段設定會有額外的屬性。

特別是，包含 **PSWorkflowExecutionOptions** 物件的工作階段設定屬性視工作流程選項值而異。 例如，若工作階段設定包含會為 **SessionThrottleLimit** 屬性設定非預設值的 **PSWorkflowExecutionOptions** 物件，則該工作階段設定具有 **SessionThrottleLimit** 屬性。 否則，則沒有。

## 相關連結

[New-PSWorkflowSession](New-PSWorkflowSession.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)
