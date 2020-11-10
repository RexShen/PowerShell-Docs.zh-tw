---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: e93a46d863fb560c70d9257270af1e6f43d3f248
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391182"
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

### CommandParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### FilterParameterSet

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## DESCRIPTION

`Get-Job`Cmdlet 會取得物件，這些物件代表在目前會話中啟動的背景工作。 您可以使用 `Get-Job` 來取得使用 Cmdlet 啟動的作業 `Start-Job` ，或使用任何 Cmdlet 的 **AsJob** 參數。

如果沒有參數， `Get-Job` 命令就會取得目前會話中的所有工作。 您可以使用的參數 `Get-Job` 來取得特定工作。

傳回的工作物件 `Get-Job` 包含工作的相關實用資訊，但是不包含工作結果。 若要取得結果，請使用 `Receive-Job` Cmdlet。

Windows PowerShell 背景工作是在背景執行的命令，而不會與目前的會話互動。 一般而言，您會使用背景工作來執行複雜的命令，此命令需要很長的時間才能完成。 如需有關 Windows PowerShell 中背景工作的詳細資訊，請參閱 [about_Jobs](./about/about_Jobs.md)。

從 Windows PowerShell 3.0 開始，此 `Get-Job` Cmdlet 也會取得自訂工作類型，例如工作流程工作和排程工作的實例。 若要尋找工作的工作類型，可使用工作的 **PSJobTypeName** 屬性。

若要啟用 `Get-Job` 以取得自訂工作類型，請先將支援自訂工作類型的模組匯入到會話中 `Get-Job` ，再執行命令，方法是使用 `Import-Module` Cmdlet 或使用或取得模組中的 Cmdlet。 如需有關特定自訂工作類型的資訊，請參閱自訂工作類型功能的文件。

## 範例

### 範例1：取得在目前會話中啟動的所有背景工作

這個命令會取得目前工作階段中啟動的所有背景工作。 它不會包含在其他工作階段中建立的工作，即使這類工作是在本機電腦上執行也一樣。

```
PS C:\> Get-Job
```

### 範例2：使用實例識別碼停止作業

這些命令示範如何取得工作的執行個體識別碼，然後使用它來停止工作。 與工作名稱 (這不是唯一的) 不同，執行個體識別碼是唯一的。

第一個命令會使用 `Get-Job` Cmdlet 來取得工作。 它會使用 **Name** 參數來識別工作。 此命令會儲存在變數中傳回的工作物件 `Get-Job` `$j` 。 在這個範例中，只有一個具有指定名稱的工作。 第二個命令會取得變數中物件的 **InstanceId** 屬性 `$j` ，並將它儲存在 `$ID` 變數中。 第三個命令會顯示變數的值 `$ID` 。 第四個命令會使用 `Stop-Job` Cmdlet 來停止工作。
它會使用 **InstanceId** 參數來識別工作和 `$ID` 變數，以代表工作的實例識別碼。

```
PS C:\> $j = Get-Job -Name Job1
PS C:\> $ID = $j.InstanceID
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

PS C:\> Stop-Job -InstanceId $ID
```

### 範例3：取得包含特定命令的工作

此命令會取得系統上包含命令的工作 `Get-Process` 。 命令使用的 **命令** 參數 `Get-Job` 來限制抓取的工作。 命令使用萬用字元 (`*`) 來取得 `Get-Process` 命令字串中任何位置包含命令的作業。

```
PS C:\> Get-Job -Command "*get-process*"
```

### 範例4：使用管線取得包含特定命令的作業

如同上一個範例中的命令，此命令會取得系統上包含命令的工作 `Get-Process` 。 此命令會使用管線運算子 (`|`) 將字串（以引號括住）傳送至 `Get-Job` Cmdlet。 它等同於前一個命令。

```
PS C:\> "*get-process*" | Get-Job
```

### 範例5：取得尚未啟動的工作

這個命令只會取得已建立但尚未啟動的工作。 這包括已排定在未來執行的工作以及尚未排程的工作。

```
PS C:\> Get-Job -State NotStarted
```

### 範例6：取得尚未指派名稱的工作

此命令會取得工作名稱以 job 開頭的所有工作。 由於 `job<number>` 是工作的預設名稱，因此，此命令會取得所有未明確指派名稱的工作。

```
PS C:\> Get-Job -Name Job*
```

### 範例7：使用工作物件來代表命令中的工作

這個範例示範如何使用 `Get-Job` 來取得工作物件，然後示範如何使用工作物件來代表命令中的工作。

第一個命令會使用 `Start-Job` Cmdlet 來啟動在 `Get-Process` 本機電腦上執行命令的背景工作。 此命令會使用的 **Name** 參數 `Start-Job` 來指派工作的易記名稱。 第二個命令會使用 `Get-Job` 來取得工作。 它使用的 **Name** 參數 `Get-Job` 來識別工作。 此命令會將產生的工作物件儲存在 `$j` 變數中。 第三個命令顯示變數中工作物件的值 `$j` 。 **State** 屬性的值顯示作業已完成。 **HasMoreData** 屬性的值顯示有來自尚未抓取之工作的可用結果。 第四個命令會使用 `Receive-Job` Cmdlet 來取得工作的結果。 它會使用變數中的工作物件 `$j` 來表示作業。 您也可以使用管線運算子將工作物件傳送至 `Receive-Job` 。

```
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob
PS C:\> $j = Get-Job -Name MyJob
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```


### 範例8：取得所有工作，包括其他方法啟動的作業

此範例示範 `Get-Job` Cmdlet 可以取得在目前會話中啟動的所有作業，即使它們是使用不同的方法啟動的。

第一個命令會使用 `Start-Job` Cmdlet 在本機電腦上啟動作業。 第二個命令會使用 Cmdlet 的 **AsJob** 參數 `Invoke-Command` ，在 S1 電腦上啟動作業。 即使工作中的命令是在遠端電腦上執行，還是會在本機電腦上建立工作物件，因此您可以使用本機命令來管理工作。 第三個命令會使用 `Invoke-Command` Cmdlet `Start-Job` 在 S2 電腦上執行命令。 使用這個方法時，會在遠端電腦上建立工作物件，因此您可以使用遠端命令來管理作業。 第四個命令會使用 `Get-Job` 來取得儲存在本機電腦上的工作。 Windows PowerShell 3.0 中引進之作業的 **PSJobTypeName** 屬性顯示使用指令程式啟動的本機作業 `Start-Job` 是背景工作，而使用 Cmdlet 在遠端會話中啟動的作業 `Invoke-Command` 是遠端作業。 第五個命令會使用在 `Invoke-Command` `Get-Job` S2 電腦上執行命令。範例輸出會顯示命令的結果 `Get-Job` 。 在 S2 電腦上，工作顯示為本機工作。 電腦名稱稱是 localhost，而工作類型是背景工作。如需有關如何在遠端電腦上執行背景工作的詳細資訊，請參閱 [about_Remote_Jobs](./about/about_Remote_Jobs.md)。

```
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

### 範例9：調查失敗的作業

此命令會顯示如何使用傳回的工作物件， `Get-Job` 來調查作業失敗的原因。
它也會示範如何取得每個工作的子工作。

第一個命令會使用 `Start-Job` Cmdlet 在本機電腦上啟動作業。 傳回的工作物件 `Start-Job` 顯示作業失敗。 **State** 屬性的值為 Failed。

第二個命令會使用 `Get-Job` Cmdlet 來取得工作。 命令使用點方法，取得物件的 **JobStateInfo** 屬性值。 它會使用管線運算子將 **JobStateInfo** 屬性中的物件傳送至 `Format-List` Cmdlet，此 Cmdlet 會將物件的所有屬性格式化 (`*` 清單中) 。命令的結果 `Format-List` 顯示作業的 **Reason** 屬性值是空白的。

第三個命令會進一步調查。 它會使用 `Get-Job` 命令來取得工作，然後使用管線運算子將整個工作物件傳送至 `Format-List` Cmdlet，此 Cmdlet 會將工作的所有屬性顯示在清單中。工作物件中所有屬性的顯示會顯示作業包含名為 Job2 的子工作。

第四個命令 `Get-Job` 會使用來取得代表 Job2 子工作的工作物件。 這是命令實際於其中執行的工作。 它會使用點方法來取得 **JobStateInfo** 屬性的 **Reason** 屬性。結果顯示作業因為拒絕存取錯誤而失敗。 在此情況下，使用者在啟動 Windows PowerShell 時忘記使用 [以系統管理員身分執行] 選項。因為背景工作使用 Windows PowerShell 的遠端功能，所以必須將電腦設定為遠端執行作業，即使是在本機電腦上執行工作。如需 Windows PowerShell 中的遠端處理需求的詳細資訊，請參閱 [about_Remote_Requirements](./about/about_Remote_Requirements.md)。 如需疑難排解秘訣，請參閱 [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md)。

```
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

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

PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the
following error message: Access is denied.
```

### 範例10：取得篩選的結果

這個範例示範如何使用 **Filter** 參數取得工作流程工作。 **Filter** 參數 (在 Windows PowerShell 3.0 中引進) 只適用於自訂工作類型，例如，工作流程工作和已排程的工作。

第一個命令會使用 **Workflow** 關鍵字來建立 WFProcess 工作流程。 第二個命令會使用 WFProcess 工作流程的 **AsJob** 參數，以背景工作的形式執行工作流程。 它使用工作流程的 **JobName** 參數指定工作的名稱，以及使用工作流程的 **PSPrivateMetadata** 參數指定自訂識別碼。 第三個命令使用的 **Filter** 參數， `Get-Job` 依 **PSPrivateMetadata** 參數中指定的自訂識別碼取得工作。

```
PS C:\> Workflow WFProcess {Get-Process}
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

### 範例11：取得子作業的相關資訊

此範例顯示使用 Cmdlet 的 **IncludeChildJob** 和 **ChildJobState** 參數的效果 `Get-Job` 。

第一個命令取得目前工作階段中的工作。 輸出包含背景工作、遠端工作，以及已排程工作的數個執行個體。 遠端工作 (Job4) 似乎已失敗。
第二個命令使用的 **IncludeChildJob** 參數 `Get-Job` 。 輸出會加入所有具有子工作的工作的子工作。在此情況下，修改後的輸出會顯示只有 Job4 的 Job5 子工作失敗。 第三個命令使用 **ChildJobState** 參數，其值為 failed。輸出會包含所有父工作，以及只有失敗的子工作。 第五個命令使用工作的 **JobStateInfo** 屬性及其 **Reason** 屬性，來探索 Job5 失敗的原因。

```
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

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

PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
```

如需詳細資訊，請參閱 [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md) 說明主題。

## PARAMETERS

### -After

取得在指定日期和時間之後結束的已完成工作。 輸入 **datetime** 物件（例如 Cmdlet 所傳回的物件） `Get-Date` 或可以轉換成 **DateTime** 物件的字串，例如 `Dec 1, 2012 2:00 AM` 或 `11/06` 。

這個參數只適用於含有 **EndTime** 屬性的自訂工作類型，例如，工作流程工作和已排程的工作。 它無法在標準背景工作上運作，例如使用 Cmdlet 所建立的工作 `Start-Job` 。 如需支援此參數的詳細資訊，請參閱工作類型的說明主題。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Before

取得在指定日期和時間之前結束的已完成工作。 輸入 **DateTime** 物件。

這個參數只適用於含有 **EndTime** 屬性的自訂工作類型，例如，工作流程工作和已排程的工作。 它無法在標準背景工作上運作，例如使用 Cmdlet 所建立的工作 `Start-Job` 。 如需支援此參數的詳細資訊，請參閱工作類型的說明主題。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ChildJobState

只取得具有指定狀態的子工作。 此參數可接受的值為：

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

依預設，不 `Get-Job` 會取得子工作。 藉由使用 **IncludeChildJob** 參數， `Get-Job` 取得所有子工作。 如果您使用 **ChildJobState** 參數， **IncludeChildJob** 參數就沒有任何作用。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

將命令陣列指定為字串。 此 Cmdlet 會取得包含指定命令的工作。 預設為所有工作。 您可以使用萬用字元來指定命令模式。

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

指定條件的雜湊表。 此 Cmdlet 會取得符合所有條件的工作。
輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。

這個參數只適用於自訂工作類型，例如，工作流程工作和已排程的工作。 它無法在標準背景工作上運作，例如使用 Cmdlet 所建立的工作 `Start-Job` 。 如需支援此參數的詳細資訊，請參閱工作類型的說明主題。

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
**HasMoreData** 屬性會指出是否已在目前工作階段中收到所有的工作結果。 若要取得具有更多結果的工作，請指定值 `$True` 。 若要取得沒有其他結果的工作，請指定值 `$False` 。

若要取得作業的結果，請使用 `Receive-Job` Cmdlet。

當您使用指令 `Receive-Job` 程式時，它會從記憶體內部的會話特定儲存體中刪除它傳回的結果。 當它傳回目前會話中的所有工作結果時，它會將工作的 **HasMoreData** 屬性值設定為 `$False`) ，以指出它在目前的會話中沒有其他作業的結果。 使用的 [ **保持** 參數] `Receive-Job` 可防止 `Receive-Job` 刪除結果及變更 **HasMoreData** 屬性的值。
如需詳細資訊，請鍵入 `Get-Help Receive-Job`。

**HasMoreData** 屬性是目前工作階段特定的屬性。 如果自訂工作類型的結果儲存在會話外部，例如將工作結果儲存在磁片上的排程工作類型，您可以 `Receive-Job` 在不同的會話中使用此 Cmdlet，以再次取得工作結果，即使 **HasMoreData** 的值為 `$False` 。 如需詳細資訊，請參閱自訂工作類型的說明主題。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定此 Cmdlet 取得之作業的識別碼陣列。

識別碼是一個整數，可唯一識別目前工作階段中的工作。 它比較容易記住並輸入實例識別碼，但是它只有在目前的會話中是唯一的。 您可以輸入一或多個以逗號分隔的識別碼。 若要尋找作業的識別碼，請輸入 `Get-Job` 但不使用參數。

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

這個參數特別適用于調查工作流程工作，其會傳回 `Get-Job` 容器父工作和作業失敗，因為失敗的原因會儲存于子工作的屬性中。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

指定此 Cmdlet 取得之作業的實例識別碼陣列。 預設為所有工作。

執行個體識別碼是 GUID，可唯一識別電腦上的工作。 若要尋找工作的實例識別碼，請使用 `Get-Job` 。

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

指定此 Cmdlet 取得之作業的實例易記名稱陣列。 輸入工作名稱，或使用萬用字元來輸入工作名稱模式。 依預設，會 `Get-Job` 取得目前會話中的所有工作。

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

指定要取得的作業數。 此 Cmdlet 會取得最近結束的工作。

**Newest** 參數不會依結束時間順序排序或傳回最新的工作。 若要排序輸出，請使用 `Sort-Object` Cmdlet。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -State

指定工作狀態。 此 Cmdlet 只會取得處於指定狀態的工作。 此參數可接受的值為：

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

依預設，會 `Get-Job` 取得目前會話中的所有工作。

如需有關工作狀態的詳細資訊，請參閱 [JobState 列舉](/dotnet/api/system.management.automation.jobstate)。

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

工作的 **PSJobTypeName** 屬性會指出工作的工作類型。 屬性值是由工作類型作者所決定。 下列清單顯示常見的工作類型。

- **BackgroundJob** 。 使用啟動的本機作業 `Start-Job` 。
- **RemoteJob** 。 使用 Cmdlet 的 **AsJob** 參數在 **PSSession** 中啟動作業 `Invoke-Command` 。
- **PSWorkflowJob** 。 使用工作流程 **AsJob** 一般參數啟動的工作。

## 相關連結

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)

[about_Jobs](About/about_Jobs.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)
