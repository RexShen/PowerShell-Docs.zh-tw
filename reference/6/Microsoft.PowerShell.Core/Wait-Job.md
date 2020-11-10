---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: 93673fe82ebb87f160fc0a20acdc5c766a446445
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387170"
---
# Wait-Job

## 概要
抑制命令提示字元，直到會話中正在執行的其中一個或所有 PowerShell 背景工作完成為止。

## SYNTAX

### SessionIdParameterSet (預設值)

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### JobParameterSet

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### NameParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### StateParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### FilterParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## DESCRIPTION

`Wait-Job`Cmdlet 會等候 PowerShell 背景工作完成，然後才會顯示命令提示字元。 您可以等到任一背景工作完成，或等到所有背景工作都完成，而且可以設定工作的最長等待時間。

當工作中的命令完成時，會 `Wait-Job` 顯示命令提示字元並傳回工作物件，讓您可以使用管線將它傳送至另一個命令。

您可以使用 `Wait-Job` Cmdlet 來等候背景工作，例如使用 `Start-Job` Cmdlet 或 Cmdlet 的 **AsJob** 參數啟動的工作 `Invoke-Command` 。 如需 Windows PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](./about/about_Jobs.md)。

從 Windows PowerShell 3.0 開始，此 `Wait-Job` Cmdlet 也會等待自訂工作類型，例如工作流程工作和排程工作的實例。 若要讓 `Wait-Job` 等待特定類型的工作，請 `Get-Job` 使用 `Import-Module` Cmdlet 或使用或取得模組中的 Cmdlet，先將支援自訂工作類型的模組匯入會話中，再執行 Cmdlet。 如需有關特定自訂工作類型的資訊，請參閱自訂工作類型功能的文件。

## 範例

### 範例1：等候所有作業

```powershell
Get-Job | Wait-Job
```

此命令會等待會話中執行的所有背景工作完成。

### 範例2：使用 Start-Job 等候遠端電腦上啟動的工作

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

此範例示範如何使用指令程式搭配使用 `Wait-Job` Cmdlet 在遠端電腦上啟動的作業 `Start-Job` 。 `Start-Job`和 `Wait-Job` 命令都使用 Cmdlet 提交至遠端電腦 `Invoke-Command` 。

這個範例 `Wait-Job` 會使用來判斷 `Get-Date` 在三部不同電腦上以背景工作方式執行的命令是否已完成。

第一個命令會在三部遠端電腦上 ( **PSSession** ) 建立 Windows PowerShell 會話，並將它們儲存在 `$s` 變數中。

第二個命令會使用在中的 `Invoke-Command` `Start-Job` 三個會話中執行 `$s` 。
所有的工作都命名為 Date1。

第三個命令會使用 `Invoke-Command` 來執行 `Wait-Job` 。 此命令會等待每一部電腦上的 Date1 工作完成。 它會將產生的集合 (陣列) 在變數中的工作物件 `$done` 。

第四個命令使用變數中工作物件陣列的 **Count** 屬性 `$done` 來判斷已完成的作業數目。

### 範例3：判斷第一個背景工作完成的時間

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

這個範例會使用的 **Any** 參數 `Wait-Job` ，來判斷在目前的會話中執行的多個背景工作的第一個作業完成的時間。 它也會示範如何使用指令 `Wait-Job` 程式來等候遠端工作完成。

第一個命令會在 Machines.txt 檔案中列出的每一部電腦上建立 **pssession** ，並將 **pssession** 物件儲存在 `$s` 變數中。 此命令會使用 `Get-Content` Cmdlet 來取得檔案的內容。 此 `Get-Content` 命令會以括弧括住，以確保它會在命令之前執行 `New-PSSession` 。

第二個命令會在變數中儲存 `Get-EventLog` 命令字串（以引號括住） `$c` 。

第三個命令會使用 `Invoke-Command` Cmdlet `Start-Job` 在的每個會話中執行 `$s` 。
此 `Start-Job` 命令會啟動在 `Get-EventLog` 變數中執行命令的背景工作 `$c` 。

此命令會使用 **Using** 範圍修飾符來指出 `$c` 變數是在本機電腦上定義。 **Using** 範圍修飾符是在 Windows PowerShell 3.0 中引進。 如需 **Using** 範圍修飾符的詳細資訊，請參閱 [about_Remote_Variables](./about/about_Remote_Variables.md)。

第四個命令會使用在 `Invoke-Command` `Wait-Job` 會話中執行命令。 它會使用 **Any** 參數來等候，直到遠端電腦上的第一個工作完成為止。

### 範例4：設定遠端電腦上作業的等候時間

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

這個範例會示範如何使用的 **Timeout** 參數 `Wait-Job` ，為遠端電腦上執行的作業設定最長等候時間。

第一個命令會在三部遠端電腦上建立 **PSSession** (Server01、Server02 和 Server03) ，然後將 **pssession** 物件儲存在 `$s` 變數中。

第二個命令會使用在 `Invoke-Command` `Start-Job` 中的每個 **PSSession** 物件中執行 `$s` 。 它會將產生的工作物件儲存在 `$jobs` 變數中。

第三個命令會使用在中的 `Invoke-Command` `Wait-Job` 每個會話中執行 `$s` 。 此 `Wait-Job` 命令會判斷所有命令是否已在30秒內完成。 它會使用值為30的 **Timeout** 參數來建立最長等待時間，然後將命令的結果儲存在 `$done` 變數中。

在本例中，30 秒之後，只有 Server02 電腦上的命令已完成。 `Wait-Job` 結束等待、顯示命令提示字元，然後傳回代表已完成作業的物件。

`$done`變數包含代表在 Server02 上執行之工作的工作物件。

### 範例5：等候數個作業的其中一個完成

```powershell
Wait-Job -id 1,2,5 -Any
```

此命令會依識別碼來識別三個工作，並等到其中任何一個工作完成為止。
第一個作業完成時，會傳回命令提示字元。

### 範例6：等候一段時間，然後允許作業在背景中繼續

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

此命令會等候120秒 (兩) 分鐘的時間，DailyLog 作業才會完成。 如果作業未在接下來的兩分鐘內完成，則會傳回命令提示字元，而工作會繼續在背景執行。

### 範例7：依名稱等候工作

```powershell
Wait-Job -Name "Job3"
```

此命令使用工作名稱來識別要等待的工作。

### 範例8：等候本機電腦上的工作以 Start-Job 啟動

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

此範例示範如何使用指令程式搭配在 `Wait-Job` 本機電腦上啟動的工作 `Start-Job` 。

這些命令啟動可取得上週新增或更新之 Windows PowerShell 指令檔的工作。

第一個命令會使用在 `Start-Job` 本機電腦上啟動背景工作。 作業會執行 `Get-ChildItem` 命令，以取得在上一周新增或更新的所有檔案，其副檔名為 ps1。

第三個命令 `Wait-Job` 會使用來等候工作完成。 當作業完成時，此命令會顯示工作物件，其中包含作業的相關資訊。

### 範例9：使用 Invoke-Command 等候遠端電腦上啟動的工作

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

這個範例示範如何使用的 `Wait-Job` **AsJob** 參數，在遠端電腦上使用來執行工作 `Invoke-Command` 。 使用 **AsJob** 時，會在本機電腦上建立工作，而即使工作是在遠端電腦上執行，也會將結果自動傳回到本機電腦。

此範例 `Wait-Job` 會使用來判斷在 `Get-Process` 三部遠端電腦上的會話中執行的命令是否已完成。

第一個命令會在三部電腦上建立 **PSSession** 物件，並將它們儲存在 `$s` 變數中。

第二個命令會使用在中的 `Invoke-Command` `Get-Process` 三個會話中執行 `$s` 。
此命令會使用 **AsJob** 參數，以非同步方式以背景工作方式執行命令。 命令會傳回工作物件，就像使用啟動的工作一樣， `Start-Job` 工作物件也會儲存在 `$j` 變數中。

第三個命令使用管線運算子 (`|`) 將工作物件傳送 `$j` 至 `Wait-Job` Cmdlet。 `Invoke-Command`在此情況下不需要命令，因為作業位於本機電腦上。

### 範例10：等候具有識別碼的作業

```powershell
Get-Job
```

```Output
Id   Name     State      HasMoreData     Location             Command
--   ----     -----      -----------     --------             -------
1    Job1     Completed  True            localhost,Server01.. get-service
4    Job4     Completed  True            localhost            dir | where
```

```powershell
Wait-Job -Id 1
```

此命令等待 ID 值為 1 的工作。

## PARAMETERS

### -Any

指出當任何作業完成時，此 Cmdlet 會顯示命令提示字元，並傳回工作物件。 根據預設， `Wait-Job` 會等到所有指定的工作都完成後，才會顯示提示。

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

### -Filter

指定條件的雜湊表。 此 Cmdlet 會等候符合雜湊表中所有條件的工作。 輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。

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

### -Force

指出此 Cmdlet 會繼續等待處於暫停或已中斷線上狀態的工作。 根據預設， `Wait-Job` 當作業處於下列其中一個狀態時，會傳回或結束等候：

- Completed
- 失敗
- 已停止
- 暫止
- 已中斷連接

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

### -Id

指定此 Cmdlet 等候之作業的識別碼陣列。

識別碼是一個整數，可唯一識別目前工作階段中的工作。 與執行個體識別碼相比，它比較容易記住並輸入，但是它只有在目前的工作階段內是唯一的。 您可以輸入一個或多個識別碼，以逗號分隔。 若要尋找工作的識別碼，請輸入 `Get-Job`。

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

指定此 Cmdlet 等候之作業的實例識別碼陣列。 預設為所有工作。

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

### -Job

指定此 Cmdlet 等候的作業。 輸入包含工作物件的變數，或輸入可取得工作物件的命令。 您也可以使用管線運算子將工作物件傳送至 `Wait-Job` Cmdlet。 根據預設，會 `Wait-Job` 等候目前會話中建立的所有作業。

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

指定此 Cmdlet 等候之作業的易記名稱。

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -State

指定工作狀態。 此 Cmdlet 只會等待處於指定狀態的工作。 此參數可接受的值為：

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

### -Timeout

指定每個背景工作的最長等候時間（以秒為單位）。 預設值-1 表示 Cmdlet 會等候，直到工作完成為止。 當您提交 `Wait-Job` 命令（而不是命令）時，就會開始計時 `Start-Job` 。

如果超過這個時間，即使工作仍在執行，也會結束等待並返回命令提示字元。 此命令不會顯示任何錯誤訊息。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.RemotingJob

您可以使用管線將工作物件傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.PSRemotingJob

此 Cmdlet 會傳回代表已完成之工作的工作物件。 如果因為超過 **Timeout** 參數的值而結束等候，則 `Wait-Job` 不會傳回任何物件。

## 注意

根據預設， `Wait-Job` 當作業處於下列其中一個狀態時，會傳回或結束等候：

- Completed
- 失敗
- 已停止
- 暫止
- 中斷連線以 `Wait-Job` 繼續等候已暫止和已中斷連線的作業，請使用 **Force** 參數。

## 相關連結

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)
