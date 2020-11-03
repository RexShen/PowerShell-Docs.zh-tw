---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 0b9c76ca1e26adaa244473366c2eabdaaa28452c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202303"
---
# Get-Job

## 概要
取得目前會話中正在執行的 PowerShell 背景工作。

## SYNTAX

### SessionIdParameterSet (預設值)

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### CommandParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### NameParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### StateParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### FilterParameterSet

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## DESCRIPTION

**Get-Job** Cmdlet 會取得物件，這類物件代表已在目前工作階段中啟動的背景工作。
您可以使用「 **取得作業** 」來取得使用 Start-Job Cmdlet 或使用任何 Cmdlet 之 *AsJob* 參數啟動的工作。

如果沒有參數， **取得工作** 命令會取得目前會話中的所有工作。
您可以使用 **Get-Job** 的參數取得特定工作。

**Get-Job** 傳回的工作物件包含關於工作的有用資訊，但是不包含工作結果。
若要取得結果，請使用 Receive-Job Cmdlet。

Windows PowerShell 背景工作是在背景執行的命令，而不會與目前的會話互動。
一般而言，您會使用背景工作來執行複雜的命令，此命令需要很長的時間才能完成。
如需 Windows PowerShell 中背景工作的詳細資訊，請參閱 about_Jobs。

從 Windows PowerShell 3.0 開始， **Get-Job** Cmdlet 也可取得自訂工作類型 (例如工作流程工作和排程工作的執行個體)。
若要尋找工作的工作類型，可使用工作的 **PSJobTypeName** 屬性。

若要啟用 **Get 工作** 以取得自訂工作類型，請使用 Import-Module Cmdlet 或使用或取得模組中的 Cmdlet，先將支援自訂工作類型的模組匯入會話中，再執行 [ **取得工作** ] 命令。
如需有關特定自訂工作類型的資訊，請參閱自訂工作類型功能的文件。

## 範例

### 範例1：取得在目前會話中啟動的所有背景工作

```
PS C:\> Get-Job
```

這個命令會取得目前工作階段中啟動的所有背景工作。
它不會包含在其他工作階段中建立的工作，即使這類工作是在本機電腦上執行也一樣。

### 範例2：使用實例識別碼停止作業

```
The first command uses the **Get-Job** cmdlet to get a job. It uses the *Name* parameter to identify the job. The command stores the job object that **Get-Job** returns in the $j variable. In this example, there is only one job with the specified name.
PS C:\> $j = Get-Job -Name Job1

The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.
PS C:\> $ID = $j.InstanceID

The third command displays the value of the $ID variable.
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

The fourth command uses Stop-Job cmdlet to stop the job. It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.
PS C:\> Stop-Job -InstanceId $ID
```

這些命令示範如何取得工作的執行個體識別碼，然後使用它來停止工作。
與工作名稱 (這不是唯一的) 不同，執行個體識別碼是唯一的。

### 範例3：取得包含特定命令的工作

```
PS C:\> Get-Job -Command "*get-process*"
```

此命令會取得系統上包含 Get-Process 命令的工作。
命令使用 *Get-Job* 的 **Command** 參數限制抓取的工作。
命令使用萬用字元 ( * ) 來取得命令字串中任何位置包含 **取得處理** 程式命令的作業。

### 範例4：使用管線取得包含特定命令的作業

```
PS C:\> "*get-process*" | Get-Job
```

如同上一個範例中的命令，此命令會取得系統上包含 **Get 進程** 命令的工作。
命令使用管線運算子 (|) 將字串（以引號括住）傳送至「 **取得工作** 」 Cmdlet。
它等同於前一個命令。

### 範例5：取得尚未啟動的工作

```
PS C:\> Get-Job -State NotStarted
```

這個命令只會取得已建立但尚未啟動的工作。
這包括已排定在未來執行的工作以及尚未排程的工作。

### 範例6：取得尚未指派名稱的工作

```
PS C:\> Get-Job -Name Job*
```

此命令會取得工作名稱以 job 開頭的所有工作。
因為 job \<number\> 是作業的預設名稱，所以此命令會取得所有沒有明確指派名稱的工作。

### 範例7：使用工作物件來代表命令中的工作

```
The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer. The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob

The second command uses Get-Job to get the job. It uses the *Name* parameter of **Get-Job** to identify the job. The command saves the resulting job object in the $j variable.
PS C:\> $j = Get-Job -Name MyJob

The third command displays the value of the job object in the $j variable. The value of the **State** property shows that the job is completed. The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

The fourth command uses the **Receive-Job** cmdlet to get the results of the job. It uses the job object in the $j variable to represent the job. You can also use a pipeline operator to send a job object to **Receive-Job**.
PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

這個範例示範如何使用 **Get-Job** 取得工作物件，然後示範如何使用該工作物件來代表命令中的工作。

### 範例8：取得所有工作，包括其他方法啟動的作業

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer.
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}

The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer. Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob

The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer. By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}

The fourth command uses **Get-Job** to get the jobs stored on the local computer. The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command. On the S2 computer, the job appears to be a local job. The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see about_Remote_Jobs.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

這個範例示範，即使是使用不同的方法啟動， **Get 工作** Cmdlet 也可以取得在目前會話中啟動的所有工作。

### 範例9：調查失敗的作業

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer. The job object that **Start-Job** returns shows that the job failed. The value of the **State** property is Failed.
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

The second command uses the **Get-Job** cmdlet to get the job. The command uses the dot method to get the value of the **JobStateInfo** property of the object. It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.
PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

The third command investigates more. It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.
PS C:\> Get-Job | Format-List -Property *
HasMoreData   : False
StatusMessage :
Location      : localhost
Command       : get-process
JobStateInfo  : Failed
Finished      : System.Threading.ManualReset
EventInstanceId    : fb792295-1318-4f5d-8ac8-8a89c5261507
Id            : 1
Name          : Job1
ChildJobs     : {Job2}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :

The fourth command uses **Get-Job** to get the job object that represents the Job2 child job. This is the job in which the command actually ran. It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error. In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see about_Remote_Requirements. For troubleshooting tips, see about_Remote_Troubleshooting.
PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.
```

此命令示範如何使用工作物件，該工作物件會傳回工作物件來調查工作 **失敗的原因** 。
它也會示範如何取得每個工作的子工作。

### 範例10：取得篩選的結果

```
The first command uses the **Workflow** keyword to create the WFProcess workflow.
PS C:\> Workflow WFProcess {Get-Process}

The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job. It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}

The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

這個範例示範如何使用 *Filter* 參數取得工作流程工作。
*Filter* 參數 (在 Windows PowerShell 3.0 中引進) 只適用於自訂工作類型，例如，工作流程工作和已排程的工作。

### 範例11：取得子作業的相關資訊

```
The first command gets the jobs in the current session. The output includes a background job, a remote job and several instances of a scheduled job. The remote job, Job4, appears to have failed.
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The second command uses the *IncludeChildJob* parameter of **Get-Job**. The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.
PS C:\> Get-Job -IncludeChildJob
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
3      Job3                            Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
6      Job6                            Completed     True            Server02            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.
PS C:\> Get-Job -Name Job4 -ChildJobState Failed
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.
PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

這個範例示範使用 *Get-Job* Cmdlet 的 *IncludeChildJob* 和 **ChildJobState** 參數的效果。

## PARAMETERS

### -After

取得在指定日期和時間之後結束的已完成工作。
輸入 **datetime** 物件，例如 Get-Date Cmdlet 所傳回的物件，或是可轉換成 **DateTime** 物件的字串，例如 `Dec 1, 2012 2:00 AM` 或 `11/06` 。

這個參數只適用於含有 **EndTime** 屬性的自訂工作類型，例如，工作流程工作和已排程的工作。
它無法在標準背景工作上運作，例如使用 **啟動工作** Cmdlet 所建立的工作。
如需支援此參數的詳細資訊，請參閱工作類型的說明主題。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Before

取得在指定日期和時間之前結束的已完成工作。
輸入 **DateTime** 物件。

這個參數只適用於含有 **EndTime** 屬性的自訂工作類型，例如，工作流程工作和已排程的工作。
它無法在標準背景工作上運作，例如使用 **啟動工作** Cmdlet 所建立的工作。
如需支援此參數的詳細資訊，請參閱工作類型的說明主題。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ChildJobState

只取得具有指定狀態的子工作。
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

根據預設， **Get-Job** 無法取得子工作。
藉由使用 *IncludeChildJob* 參數， **取得工作會取得** 所有子工作。
如果您使用 *ChildJobState* 參數， *IncludeChildJob* 參數就沒有任何作用。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

將命令陣列指定為字串。
此 Cmdlet 會取得包含指定命令的工作。
預設為所有工作。
您可以使用萬用字元來指定命令模式。

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Filter

指定條件的雜湊表。
此 Cmdlet 會取得符合所有條件的工作。
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

### -HasMoreData

指出此 Cmdlet 是否只會取得具有指定之 **HasMoreData** 屬性值的作業。
**HasMoreData** 屬性會指出是否已在目前工作階段中收到所有的工作結果。
若要取得具有更多結果的工作，請指定 $True 的值。
若要取得沒有其他結果的工作，請指定 $False 的值。

若要取得作業的結果，請使用 Receive-Job Cmdlet。

當您使用 **Receive-Job** Cmdlet 時，它會從記憶體內部的會話特定儲存體中刪除它傳回的結果。
當它傳回目前會話中的所有工作結果時，它會將工作的 **HasMoreData** 屬性值設定為 $False) ，以指出它在目前的會話中沒有其他作業的結果。
使用 *Receive-Job* 的 **Keep** 參數，來防止 **Receive-Job** 刪除結果以及變更 **HasMoreData** 屬性的值。
如需詳細資訊，請鍵入 `Get-Help Receive-Job`。

**HasMoreData** 屬性是目前工作階段特定的屬性。
如果自訂工作類型的結果儲存在會話外部，例如將工作結果儲存在磁片上的排程工作類型，您可以在不同的會話中使用 **Receive 作業指令程式** ，以再次取得工作結果，即使 **HasMoreData** 的值為 $False。
如需詳細資訊，請參閱自訂工作類型的說明主題。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定此 Cmdlet 取得之作業的識別碼陣列。

識別碼是一個整數，可唯一識別目前工作階段中的工作。
它比較容易記住並輸入實例識別碼，但是它只有在目前的會話中是唯一的。
您可以輸入一或多個以逗號分隔的識別碼。
若要尋找作業的識別碼，請輸入 `Get-Job` 但不使用參數。

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IncludeChildJob

指出除了父作業之外，此 Cmdlet 會傳回子工作。

此參數特別適用于調查工作流程工作，其中的 **Get 作業** 會傳回容器父工作和作業失敗，因為失敗的原因會儲存于子工作的屬性中。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

指定此 Cmdlet 取得之作業的實例識別碼陣列。
預設為所有工作。

執行個體識別碼是 GUID，可唯一識別電腦上的工作。
若要尋找工作的執行個體識別碼，請使用 **Get-Job** 。

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

### -Name

指定此 Cmdlet 取得之作業的實例易記名稱陣列。
輸入工作名稱，或使用萬用字元來輸入工作名稱模式。
根據預設， **Get-Job** 會取得目前工作階段中的所有工作。

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

### -Newest

指定要取得的作業數。
此 Cmdlet 會取得最近結束的工作。

*Newest* 參數不會依結束時間順序排序或傳回最新的工作。
若要排序輸出，請使用 Sort-Object Cmdlet。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -State

指定工作狀態。
此 Cmdlet 只會取得處於指定狀態的工作。
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

根據預設， **Get-Job** 會取得目前工作階段中的所有工作。

如需有關工作狀態的詳細資訊，請參閱 MSDN library 中的 [JobState 列舉](https://msdn.microsoft.com/library/system.management.automation.jobstate) 。

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
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

### System.Management.Automation.RemotingJob

此 Cmdlet 會傳回代表會話中之作業的物件。

## 注意

* 工作的 **PSJobTypeName** 屬性會指出工作的工作類型。 屬性值是由工作類型作者所決定。 下列清單顯示常見的工作類型。

  - **BackgroundJob** 。
使用 **啟動工作** 啟動的本機作業。

  - **RemoteJob** 。
使用 Invoke-Command Cmdlet 的 *AsJob* 參數在 **PSSession** 中啟動作業。

  - **PSWorkflowJob** 。
使用工作流程 *AsJob* 一般參數啟動的工作。

## 相關連結

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Resume-Job](Resume-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Suspend-Job](Suspend-Job.md)

[Wait-Job](Wait-Job.md)

[about_Jobs](About/about_Jobs.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)

[about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md)
