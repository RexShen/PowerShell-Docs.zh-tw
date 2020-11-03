---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: 0c26103f47a39cb1dbd0a9f0374f7622389329a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202651"
---
# Stop-Job

## 概要
停止 PowerShell 背景工作。

## SYNTAX

### SessionIdParameterSet (預設值)

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**停止工作** Cmdlet 會停止進行中的 PowerShell 背景工作。
您可以使用這個 Cmdlet 來停止所有工作，或根據其名稱、識別碼、實例識別碼或狀態來停止選取的工作，或將工作物件傳遞給 **停止工作** 。

您可以使用 **Stop-Job** Cmdlet 停止背景工作，例如使用 Start-Job Cmdlet 或任何 Cmdlet 的 *AsJob* 參數啟動的工作。
當您停止背景工作時，PowerShell 會完成該工作佇列中所有擱置中的工作，然後結束該工作。
在送出這個命令之後，就不會再新增任何新工作到佇列中。

此 Cmdlet 不會刪除背景工作。
若要刪除工作，使用 Remove-Job Cmdlet。

從 Windows PowerShell 3.0 開始， **Stop-Job** 也可停止自訂工作類型，例如工作流程工作和排程工作的執行個體。
若要讓 **Stop-Job** 停止具自訂工作類型的工作，請使用 Import-Module cmdlet 或是使用或取得模組中的 Cmdlet，先將支援自訂工作類型的模組匯入工作階段，然後執行 **Stop-Job** 命令。
如需有關特定自訂工作類型的資訊，請參閱自訂工作類型功能的文件。

## 範例

### 範例 1︰使用 Invoke-Command 停止遠端電腦上的工作

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

此範例示範如何使用 **Stop-Job** Cmdlet，停止在遠端電腦上執行的工作。

由於工作是使用 Invoke-Command Cmdlet 從遠端執行 **Start-Job** 命令啟動，所以工作物件會儲存在遠端電腦上。
您必須使用另一個 **Invoke-Command** 命令從遠端執行 **Stop-Job** 命令。
如需有關遠端背景工作的詳細資訊，請參閱 about_Remote_Jobs。

第一個命令會在 Server01 電腦上建立 ( **PSSession** ) 的 PowerShell 會話，然後將會話物件儲存在 $s 變數中。
命令使用網域系統管理員的認證。

第二個命令使用 **Invoke-Command** Cmdlet 在工作階段中執行 **Start-Job** 命令。
工作中的命令取得 System 事件記錄檔中的所有事件。
產生的工作物件會儲存在 $j 變數中。

第三個命令停止工作。
它使用 **Invoke-Command** Cmdlet 在 Server01 上的 **PSSession** 中執行 **Stop-Job** 命令。
由於工作物件是儲存在本機電腦上的 $j 變數中，因此命令會使用 Using 範圍修飾符來將 $j 識別為區域變數。
如需 Using 範圍修飾符的詳細資訊，請參閱 [about_Remote_Variables](about/about_Remote_Variables.md)。

當命令完成時，工作會停止，而 $s 中的 **PSSession** 就可供使用。

### 範例 2︰停止背景工作

```powershell
Stop-Job -Name "Job1"
```

此命令停止 Job1 背景工作。

### 範例 3︰停止幾個背景工作

```powershell
Stop-Job -Id 1, 3, 4
```

此命令停止三個工作。
它會依其識別碼來識別它們。

### 範例 4︰停止所有背景工作

```powershell
Get-Job | Stop-Job
```

此命令停止目前工作階段中的所有背景工作。

### 範例 5︰停止所有已封鎖的背景工作

```powershell
Stop-Job -State Blocked
```

此命令停止所有已封鎖的工作。

### 範例 6︰使用執行個體識別碼停止工作

```powershell
Get-Job | Format-Table ID, Name, Command, @{Label="State";Expression={$_.JobStateInfo.State}},
InstanceID -Auto
```

```Output
Id Name Command                 State  InstanceId
-- ---- -------                 -----  ----------
1 Job1 start-service schedule Running 05abb67a-2932-4bd5-b331-c0254b8d9146
3 Job3 start-service schedule Running c03cbd45-19f3-4558-ba94-ebe41b68ad03
5 Job5 get-service s*         Blocked e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

```powershell
Stop-Job -InstanceId e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

這些命令示範如何根據工作的執行個體識別碼來停止工作。

第一個命令使用 Get-Job Cmdlet 取得目前工作階段中的工作。
命令使用管線運算子 (|) 將工作傳送至 Format-Table 命令，這會顯示一個含有每個工作之指定屬性的表格。
此表格包含每個工作的執行個體識別碼。
它使用計算的屬性來顯示工作狀態。

第二個命令使用有 *InstanceID* 參數的 **Stop-Job** 命令來停止選取的工作。

### 範例 7︰停止遠端電腦上的工作

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

此範例示範如何使用 **Stop-Job** Cmdlet，停止在遠端電腦上執行的工作。

由於工作是使用 **Invoke-Command** Cmdlet 的 *AsJob* 參數來啟動，因此即使工作是在遠端電腦上執行，工作物件仍然會位於本機電腦上。
因此，您可以使用本機的 **Stop-Job** 命令來停止該工作。

第一個命令使用 **Invoke-Command** Cmdlet 在 Server01 電腦上啟動背景工作。
命令使用 *AsJob* 參數將遠端命令當作背景工作來執行。

此命令會傳回一個工作物件，與 **Start-Job** Cmdlet 傳回的工作物件相同。
命令將工作物件儲存在 $j 變數中。

第二個命令使用管線運算子將 $j 變數中的工作傳送至 Stop-Job。
命令使用 *PassThru* 參數指示 **Stop-Job** 傳回工作物件。
工作物件顯示會確認工作的狀態為 Stopped。

如需有關遠端背景工作的詳細資訊，請參閱 about_Remote_Jobs。

## PARAMETERS

### -Filter

指定條件的雜湊表。
此 Cmdlet 會停止符合所有條件的工作。
輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。

這個參數只適用於自訂工作類型，例如，工作流程工作和已排程的工作。
它無法在標準背景工作上運作，例如使用 **啟動工作** Cmdlet 所建立的工作。
如需支援此參數的詳細資訊，請參閱工作類型的說明主題。

此參數是在 Windows PowerShell 3.0 引進。

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

### -Id

指定此 Cmdlet 停止之工作的識別碼。
預設為目前工作階段中的所有工作。

識別碼是一個整數，可唯一識別目前工作階段中的工作。
與執行個體識別碼相比，它比較容易記住並輸入，但是它只有在目前的工作階段內是唯一的。
您可以輸入一個或多個識別碼，以逗號分隔。
若要尋找工作的識別碼，請輸入 `Get-Job`。

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

指定此 Cmdlet 停止之工作的執行個體識別碼。
預設為所有工作。

執行個體識別碼是 GUID，可唯一識別電腦上的工作。
若要尋找工作的執行個體識別碼，請使用 Get-Job。

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Job

指定此 Cmdlet 停止的工作。
輸入包含工作的變數，或輸入可取得工作的命令。
您也可以使用管線運算子將作業提交至 **停止工作** Cmdlet。
根據預設， **停止作業** 會刪除在目前會話中啟動的所有工作。

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

指定此 Cmdlet 停止之工作的好記名稱。
請以逗號分隔的清單方式輸入工作名稱，或使用萬用字元 (*) 來輸入工作名稱模式。
根據預設， **停止作業** 會停止在目前會話中建立的所有作業。

由於易記名稱不保證是唯一的，因此請在依名稱停止工作時使用 *WhatIf* 和 *Confirm* 參數。

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

傳回代表您正在使用之項目的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

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

### -State

指定工作狀態。
此 Cmdlet 只停止處於指定狀態的工作。
此參數可接受的值為：

- NotStarted
- 執行中
- Completed
- 失敗
- 已停止
- 封鎖
- 暫止
- 已中斷連接
- Suspending
- 停止中

如需有關工作狀態的詳細資訊，請參閱 MSDN library 中的 [JobState 列舉](https://msdn.microsoft.com/library/system.management.automation.jobstate) 。

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
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

### System.Management.Automation.RemotingJob

您可以使用管線將工作物件傳送至此 Cmdlet。

## 輸出

### 無、System.Management.Automation.PSRemotingJob

如果您指定 *PassThru* 參數，此 Cmdlet 會傳回工作物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Resume-Job](Resume-Job.md)

[Start-Job](Start-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)

[about_Remote_Variables](About/about_Remote_Variables.md)

[about_Jobs](About/about_Jobs.md)

[about_Scopes](About/about_scopes.md)
