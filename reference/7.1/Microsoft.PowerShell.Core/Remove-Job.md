---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: b65e990c8d03858705b167bd1712ab6fde305a82
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204799"
---
# Remove-Job

## 概要
刪除 PowerShell 背景工作。

## SYNTAX

### SessionIdParameterSet (預設值)

```
Remove-Job [-Force] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Remove-Job [-Force] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Remove-Job [-Force] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Remove-Job [-Force] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CommandParameterSet

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Remove-Job` Cmdlet 會刪除 Cmdlet 或 Cmdlet 所啟動的 PowerShell 背景工作， `Start-Job` 例如 `Invoke-Command` 支援 **AsJob** 參數。

您可以使用 `Remove-Job` 刪除所有作業，或刪除選取的作業。 作業是由其 **名稱** 、 **識別碼** 、 **實例識別碼** 、 **命令** 或 **狀態** 來識別。 或者，您可以將工作物件向下傳送至 `Remove-Job` 。 如果沒有參數或參數值， `Remove-Job` 就不會有任何作用。

從 PowerShell 3.0 開始， `Remove-Job` 可以刪除自訂工作類型，例如排程工作和工作流程工作。 例如， `Remove-Job` 刪除排程工作、磁片上排程工作的所有實例，以及所有觸發之工作實例的結果。

如果您嘗試刪除執行中的作業，就 `Remove-Job` 會失敗。 使用 `Stop-Job` Cmdlet 來停止執行中的作業。 或者，使用 `Remove-Job` With **Force** 參數來刪除執行中的作業。

作業會保留在全域工作快取中，直到您移除背景工作或關閉 PowerShell 會話為止。

## 範例

### 範例1：使用其名稱刪除作業

此範例會使用變數和管線來依名稱刪除工作。

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

`Get-Job` 使用 **Name** 參數來指定作業 **BatchJob** 。 工作物件會儲存在變數中 `$batch` 。 中的物件 `$batch` 會向下傳送到管線 `Remove-Job` 。

替代方法是使用 **工作** 參數，例如 `Remove-Job -Job $batch` 。

### 範例2：刪除會話中的所有工作

在此範例中，會刪除目前 PowerShell 會話中的所有工作。

```powershell
Get-job | Remove-Job
```

`Get-Job` 取得目前 PowerShell 會話中的所有工作。 工作物件會向下傳送到管線 `Remove-Job` 。

### 範例3：刪除 NotStarted 作業

此範例會從目前未啟動的 PowerShell 會話中刪除所有作業。

```powershell
Remove-Job -State NotStarted
```

`Remove-Job` 使用 **State** 參數指定工作狀態。

### 範例4：使用易記名稱刪除作業

此範例會從目前會話中刪除以 * batch * * 結尾的易記名稱，包括正在執行的作業。

```powershell
Remove-Job -Name *batch -Force
```

`Remove-Job` 使用 **name** 參數來指定工作名稱模式。 此模式包含星號 (`*`) 萬用字元來尋找以 **批次** 結尾的所有工作名稱。 **Force** 參數會刪除執行中的作業。

### 範例5：刪除 Invoke-Command 所建立的作業

此範例會使用 AsJob 參數，移除在遠端電腦上啟動的工作 `Invoke-Command` 。 **AsJob**

因為此範例使用 **AsJob** 參數，所以會在本機電腦上建立工作物件。
但是，工作會在遠端電腦上執行。 因此，您是使用本機命令來管理工作。

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

`Invoke-Command` 在 **Server01** 電腦上執行工作。 **AsJob** 參數會將 **ScriptBlock** 以背景工作的形式執行。 工作物件會儲存在變數中 `$job` 。 `$job`變數物件會向下傳送到管線 `Remove-Job` 。

### 範例6：刪除 Invoke-Command 和 Start-Job 所建立的作業

這個範例示範如何在使用執行的遠端電腦上移除作業 `Invoke-Command` `Start-Job` 。 系統會在遠端電腦上建立工作物件，並使用遠端命令來管理作業。 執行遠端命令時，需要持續性連接 `Start-Job` 。

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

`New-PSSession`建立 **Server01** 電腦的 **PSSession** （持續連線）。 連接會儲存在變數中 `$S` 。

`Invoke-Command` 連接到儲存在中的會話 `$S` 。 **ScriptBlock** 會使用 `Start-Job` 來啟動遠端作業。 作業會執行 `Get-Process` 命令，並使用 **Name** 參數來指定易記的作業名稱 **>myjob** 。

`Invoke-Command` 使用 `$S` 會話並執行 `Remove-Job` 。 **Name** 參數指定刪除名為 **>myjob** 的作業。

### 範例7：使用其 InstanceId 來刪除作業

此範例會根據其 **InstanceId** 來移除作業。

```powershell
$job = Start-Job -ScriptBlock {Get-Process PowerShell}
$job | Format-List -Property *
Remove-Job -InstanceId ad02b942-8007-4407-87f3-d23e71955872
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-Process PowerShell
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : ad02b942-8007-4407-87f3-d23e71955872
Id            : 3
Name          : Job3
ChildJobs     : {Job4}
PSBeginTime   : 7/26/2019 11:36:56
PSEndTime     : 7/26/2019 11:36:57
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

`Start-Job` 啟動背景工作，並將工作物件儲存在變數中 `$job` 。

中的物件 `$job` 會向下傳送到管線 `Format-List` 。 **Property** 參數使用星號 (`*`) 來指定所有物件的屬性都會顯示在清單中。

`Remove-Job` 使用 **InstanceId** 參數指定要刪除的作業。

## PARAMETERS

### -Command

刪除命令中包含指定字詞的工作。 您可以輸入逗點分隔的陣列。

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

在執行之前提示您確認 `Remove-Job` 。

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

### -Filter

刪除符合在相關聯雜湊表中建立之所有條件的工作。 輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。

這個參數只適用於自訂工作類型，例如，工作流程工作和已排程的工作。 它無法在標準背景工作上運作，例如使用所建立的工作 `Start-Job` 。

此參數在 PowerShell 3.0 中引進。

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

刪除作業，即使作業的狀態為 [ **正在** 執行]。 如果未指定 **Force** 參數，則 `Remove-Job` 不會刪除執行中的作業。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, JobParameterSet, InstanceIdParameterSet, NameParameterSet, FilterParameterSet
Aliases: F

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

刪除具有指定 **識別碼** 的背景工作。您可以輸入逗點分隔的陣列。 作業的 **識別碼** 是唯一的整數，用來識別目前會話中的工作。

若要尋找作業的 **識別碼** ，請使用 `Get-Job` 不含參數的。

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

刪除具有指定 **InstanceId** 的作業。 您可以輸入逗點分隔的陣列。 **InstanceId** 是識別作業的唯一 GUID。

若要尋找作業的 **InstanceId** ，請使用 `Get-Job` 。

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Job

指定要刪除的工作。 輸入包含工作的變數，或輸入可取得工作的命令。 您可以輸入逗點分隔的陣列。

您可以將管線中的工作物件傳送至 `Remove-Job` 。

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

只刪除具有指定易記名稱的工作。 允許使用萬用字元。 您可以輸入逗點分隔的陣列。

工作的易記名稱不保證是唯一的，即使在 PowerShell 會話內也是如此。 當您依名稱刪除檔案時，請使用 **WhatIf** 和 **Confirm** 參數。

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -State

只刪除具有指定狀態的工作。 若要刪除狀態為 [ **正在** 執行] 的工作，請使用 **Force** 參數。

接受的值：

- AtBreakpoint
- 封鎖
- 已完成
- 已中斷連接
- 失敗
- NotStarted
- 執行中
- 已停止
- 停止中
- 暫止
- Suspending

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: AtBreakpoint, Blocked, Completed, Disconnected, Failed, NotStarted, Running, Stopped, Stopping, Suspended, Suspending

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

顯示執行時所發生 `Remove-Job` 的情況。 不會執行此 Cmdlet。

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

### System.Management.Automation.Job

您可以將管線下的工作物件傳送至 `Remove-Job` 。

## 輸出

### 無

`Remove-Job` 不會產生任何輸出。

## 注意

PowerShell 作業會建立新的處理常式。 當作業完成時，進程便會結束。 當 `Remove-Job` 執行時，會移除作業的狀態。

如果作業在完成前停止，而且其進程尚未結束，則會強制終止進程。

## 相關連結

[about_Jobs](./About/about_Jobs.md)

[about_Job_Details](./About/about_Job_Details.md)

[about_Remote_Jobs](./About/about_Remote_Jobs.md)

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)

