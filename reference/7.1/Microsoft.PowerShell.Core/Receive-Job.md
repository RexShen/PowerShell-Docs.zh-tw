---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 51cf0abc1a6362122f18812cd90e59a6ca7dc4ab
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204823"
---
# Receive-Job

## 概要
取得目前會話中 PowerShell 背景工作的結果。

## SYNTAX

### Location (預設值)

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### ComputerName

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### 工作階段

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### NameParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### SessionIdParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## DESCRIPTION

`Receive-Job`Cmdlet 會取得 PowerShell 背景工作的結果，例如使用 `Start-Job` Cmdlet 或任何 Cmdlet 的 **AsJob** 參數啟動的工作。
您可以取得所有工作的結果，或是依據工作的名稱、識別碼、執行個體識別碼、電腦名稱、位置或工作階段，或藉由送出工作物件，來識別工作。

當您啟動 PowerShell 背景工作時，工作會啟動，但是結果不會立即出現。 取而代之的是，命令會傳回代表背景工作的物件。
工作物件包含工作的相關實用資訊，但是不包含結果。
此方法可讓您在工作執行時繼續在會話中工作。
如需有關 PowerShell 中背景工作的詳細資訊，請參閱 [about_Jobs](./About/about_Jobs.md)。

此 `Receive-Job` Cmdlet 會取得提交命令時所產生的結果 `Receive-Job` 。
如果結果尚未完成，您可以執行其他 `Receive-Job` 命令來取得剩餘的結果。

根據預設，在您收到工作結果之後，工作結果就會自系統中刪除，但是您可以使用 **Keep** 參數來儲存結果，以便再次接收這些結果。
若要刪除工作結果，請 `Receive-Job` 再次執行命令，而不要使用 **Keep** 參數、關閉會話，或使用 `Remove-Job` Cmdlet 來刪除會話中的作業。

從 Windows PowerShell 3.0 開始， `Receive-Job` 也會取得自訂工作類型（例如工作流程工作和排程工作的實例）的結果。
若要讓 `Receive-Job` 能夠取得自訂工作類型的結果，請 `Receive-Job` 使用 `Import-Module` Cmdlet 或使用或取得模組中的 Cmdlet，先將支援自訂工作類型的模組匯入到會話中，再執行命令。
如需有關特定自訂工作類型的資訊，請參閱自訂工作類型功能的文件。

## 範例

### 範例1：取得特定作業的結果

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

這些命令會使用的 **Job** 參數 `Receive-Job` 來取得特定工作的結果。

第一個命令會使用來啟動作業 `Start-Job` ，並將工作物件儲存在 `$job` 變數中。

第二個命令會使用 `Receive-Job` Cmdlet 來取得作業的結果。
它使用 **Job** 參數來指定工作。

### 範例2：使用 Keep 參數

```powershell
$job = Start-Job -ScriptBlock {Get-Service dhcp, fakeservice}
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

```powershell
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

此範例會將工作儲存在 `$job` 變數中，然後使用管線將工作傳送至 `Receive-Job` Cmdlet。 此 `-Keep` 參數也會用來允許在第一次視圖之後再次取出所有匯總的資料流程資料。

### 範例3：取得數個背景工作的結果

當您使用的 **AsJob** 參數 `Invoke-Command` 啟動作業時，會在本機電腦上建立工作物件，即使工作是在遠端電腦上執行也一樣。
因此，您是使用本機命令來管理工作。

此外，當您使用 **AsJob** 時，PowerShell 會傳回一個工作物件，其中包含每個已啟動工作的子工作。 在此情況下，此工作物件包含三個子工作，分別用於每部遠端電腦上的每個工作。

```powershell
# Use the Invoke-Command cmdlet with the -AsJob parameter to start a background job that runs a Get-Service command on three remote computers.
# Store the resulting job object in the $j variable
$j = Invoke-Command -ComputerName Server01, Server02, Server03 -ScriptBlock {Get-Service} -AsJob
# Display the value of the **ChildJobs** property of the job object in $j.
# The display shows that the command created three child jobs, one for the job on each remote computer.
# You could also use the -IncludeChildJobs parameter of the Get-Job cmdlet.
$j.ChildJobs
```

```Output
Id   Name     State      HasMoreData   Location       Command
--   ----     -----      -----------   --------       -------
2    Job2     Completed  True          Server01       Get-Service
3    Job3     Completed  True          Server02       Get-Service
4    Job4     Completed  True          Server03       Get-Service
```

```powershell
# Use the Receive-Job cmdlet to get the results of just the Job3 child job that ran on the Server02 computer.
# Use the *Keep* parameter to allow you to view the aggregated stream data more than once.
Receive-Job -Name Job3 -Keep
```

```Output
Status  Name        DisplayName                        PSComputerName
------  ----------- -----------                        --------------
Running AeLookupSvc Application Experience             Server02
Stopped ALG         Application Layer Gateway Service  Server02
Running Appinfo     Application Information            Server02
Running AppMgmt     Application Management             Server02
```

### 範例4：取得多部遠端電腦上的背景工作結果

```powershell
# Use the New-PSSession cmdlet to create three user-managed PSSessions on three servers, and save the sessions in the $s variable.
$s = New-PSSession -ComputerName Server01, Server02, Server03
# Use Invoke-Command run a Start-Job command in each of the PSSessions in the $s variable.
# The job outputs the ComputerName of each server.
# Save the job objects in the $j variable.
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$env:COMPUTERNAME}}
# To confirm that these job objects are from the remote machines, run Get-Job to show no local jobs running.
Get-Job
```

```Output

```

```powershell
# Display the three job objects in $j.
# Note that the Localhost location is not the local computer, but instead localhost as it relates to the job on each Server.
$j
```

```Output
Id   Name     State      HasMoreData   Location   Command
--   ----     -----      -----------   --------   -------
1    Job1     Completed  True          Localhost  $env:COMPUTERNAME
2    Job2     Completed  True          Localhost  $env:COMPUTERNAME
3    Job3     Completed  True          Localhost  $env:COMPUTERNAME
```

```powershell
# Use Invoke-Command to run a Receive-Job command in each of the sessions in the $s variable and save the results in the $Results variable.
# The Receive-Job command must be run in each session because the jobs were run locally on each server.
$results = Invoke-Command -Session $s -ScriptBlock {Receive-Job -Job $Using:j}
```

```Output
Server01
Server02
Server03
```

這個範例示範如何取得在三部遠端電腦上執行之背景工作的結果。
與先前的範例不同的是，使用 `Invoke-Command` 來執行 `Start-Job` 命令實際上會在三部電腦上啟動三個獨立的工作。 因此，此命令傳回了三個工作物件，分別代表在三部不同電腦的本機執行的三個工作。

> [!NOTE]
> 在最後一個命令中，因為 `$j` 是區域變數，所以腳本區塊會使用 **Using** 範圍修飾符來識別 `$j` 變數。 如需 **Using** 範圍修飾符的詳細資訊，請參閱 [about_Remote_Variables](./About/about_Remote_Variables.md)。

### 範例5：存取子作業

`-Keep`參數會保留作業的匯總資料流程狀態，以便再次查看。 如果沒有這個參數，則會在接收到作業時清除所有匯總的資料流程資料。 如需詳細資訊，請參閱 [about_Job_Details](About/about_Job_Details.md#child-jobs)

> [!NOTE]
> 匯總的資料流程包含所有子作業的資料流程。 您仍然可以透過工作物件和子工作物件來觸及個別的資料串流。

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```Output
    Directory: C:\

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-r---        1/24/2019   7:11 AM                Program Files
d-r---        2/13/2019   8:32 AM                Program Files (x86)
d-r---        10/3/2018  11:47 AM                Users
d-----         2/7/2019   1:52 AM                Windows
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

```powershell
# It would seem that the child job data is gone.
Receive-Job -Name TestJob
```

```Output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```Output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## PARAMETERS

### -AutoRemoveJob

指出此 Cmdlet 會在傳回工作結果之後刪除工作。
如果工作有更多結果，作業仍會被刪除，但會 `Receive-Job` 顯示一則訊息。

這個參數只適用於自訂工作類型。
它是專為儲存工作的工作類型執行個體或工作階段外的類型 (例如排程工作的執行個體) 而設計。

如果沒有 **Wait** 參數，就不能使用這個參數。

此參數是在 Windows PowerShell 3.0 引進。

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

### -ComputerName

指定電腦名稱的陣列。

這個參數會從儲存在本機電腦上的工作結果中選取。
它不會取得在遠端電腦上執行之作業的資料。
若要取得儲存在遠端電腦上的工作結果，請使用 `Invoke-Command` Cmdlet `Receive-Job` 從遠端執行命令。

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 1
Default value: All computers available
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Force

指出當工作處於已 **暫停** 或已 **中斷** 連線的狀態時，此 Cmdlet 會繼續等候。 根據預設， **Wait** `Receive-Job` 當作業處於下列其中一種狀態時，的 wait 參數會傳回或結束等候：

- Completed
- 失敗
- 已停止
- 暫止
- 已中斷連接

只有當命令中也使用 **Wait** 參數時， **Force** 參數才有效。

此參數是在 Windows PowerShell 3.0 引進。

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

### -Id

指定識別碼的陣列。
此 Cmdlet 會取得具有指定識別碼之工作的結果。

識別碼是一個整數，可唯一識別目前工作階段中的工作。
與執行個體識別碼相比，它比較容易記住並輸入，但是它只有在目前的工作階段內是唯一的。 您可以輸入一或多個以逗號分隔的識別碼。
若要尋找工作的識別碼，請使用 `Get-Job` 。

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

指定執行階段識別碼的陣列。
此 Cmdlet 會取得具有指定實例識別碼之工作的結果。

執行個體識別碼是 GUID，可唯一識別電腦上的工作。
若要尋找工作的實例識別碼，請使用 `Get-Job` Cmdlet。

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All instances
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Job

指定要為其抓取結果的工作。

請輸入包含工作的變數，或輸入可取得工作的命令。
您也可以使用管線將工作物件傳送至 `Receive-Job` 。

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: Location, Session, ComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Keep

指出此 Cmdlet 會將匯總的資料流程資料儲存在系統中，即使在您收到它們之後也是如此。 依預設，會在使用之後清除匯總的資料流程資料 `Receive-Job` 。

關閉會話，或使用 Cmdlet 移除作業也會 `Remove-Job` 刪除匯總的資料流程資料。

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

### -Location

指定位置的陣列。
此 Cmdlet 只會取得指定位置中的工作結果。

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: 1
Default value: All locations
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定好記名稱的陣列。
此 Cmdlet 會取得具有指定之名稱的工作結果。
支援使用萬用字元。

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

### -NoRecurse

指出此 Cmdlet 只會從指定的工作取得結果。
根據預設， `Receive-Job` 也會取得指定之工作的所有子工作的結果。

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

### -Session

指定會話的陣列。
此 Cmdlet 會取得在指定的 PowerShell 會話中執行 ( **PSSession** ) 的工作結果。
輸入包含 **pssession** 的變數，或輸入可取得 **pssession** 的命令，例如 `Get-PSSession` 命令。

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 1
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Wait

指出此 Cmdlet 會抑制命令提示字元，直到收到所有工作結果為止。
根據預設，會 `Receive-Job` 立即傳回可用的結果。

**Wait** 參數預設會等到工作處於下列其中一種狀態：

- Completed
- 失敗
- 已停止
- 暫止
- 已中斷連接

若要指示 **wait** 參數在工作狀態為 [已暫停] 或 [已中斷連線] 時繼續等待，請使用 **Force** 參數搭配 **Wait** 參數。

此參數是在 Windows PowerShell 3.0 引進。

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

### -WriteEvents

指出此 Cmdlet 會在等候工作完成時，回報工作狀態中的變更。

只有當命令中使用了 **Wait** 參數並且省略了 **Keep** 參數時，這個參數才有效。

此參數是在 Windows PowerShell 3.0 引進。

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

### -WriteJobInResults

指出此 Cmdlet 會傳回工作物件，後面接著結果。

只有當命令中使用了 **Wait** 參數並且省略了 **Keep** 參數時，這個參數才有效。

此參數是在 Windows PowerShell 3.0 引進。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](./About/about_CommonParameters.md)。

## 輸入

### System.Management.Automation.Job

您可以透過管線將工作物件傳送至此 Cmdlet。

## 輸出

### PSObject

此 Cmdlet 會傳回工作中命令的結果。

## 注意

## 相關連結

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)

[Wait-Job](Wait-Job.md)

