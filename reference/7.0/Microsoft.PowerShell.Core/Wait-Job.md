---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: d364b04bef4a46a086af2b90a71c15f2ab3ddba5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201179"
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

**等候工作** Cmdlet 會等候 PowerShell 背景工作完成，然後才會顯示命令提示字元。
您可以等到任一背景工作完成，或等到所有背景工作都完成，而且可以設定工作的最長等待時間。

當工作中的命令都完成時， **Wait-Job** 就會顯示命令提示字元並傳回工作物件，讓您可以使用管線將它傳送給另一個命令。

您可以使用 **Wait-Job** Cmdlet 等待背景工作，例如使用 Start-Job Cmdlet 或 Invoke-Command Cmdlet 的 *AsJob* 參數。
如需 PowerShell 背景工作的詳細資訊，請參閱 about_Jobs。

從 Windows PowerShell 3.0 開始， **等候工作** Cmdlet 也會等待自訂工作類型，例如工作流程工作和排程工作的實例。
若要讓 **等候工作** 等候特定類型的工作，請先將支援自訂工作類型的模組匯入到會話中，再執行 Get-Job Cmdlet，方法是使用 Import-Module Cmdlet，或使用或取得模組中的 Cmdlet。
如需有關特定自訂工作類型的資訊，請參閱自訂工作類型功能的文件。

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

此範例示範如何使用 **「啟動工作」** Cmdlet，將「 **等候工作** 」 Cmdlet 與遠端電腦上啟動的作業搭配使用。
**啟動作業** 和 **等候工作** 命令都會使用叫用 **命令** Cmdlet 提交至遠端電腦。

此範例會使用 **等候工作** ，判斷在三部不同電腦上以背景工作方式執行的 Get-Date 命令是否已完成。

第一個命令會在三部遠端電腦上建立 ( **PSSession** ) 的 PowerShell 會話，並將它們儲存在 $s 變數中。

第二個命令使用 **Invoke 命令** ，在 $s 的三個會話中執行 **啟動工作** 。
所有的工作都命名為 Date1。

第三個命令使用 **Invoke 命令** 來執行 **等候工作** 。
此命令會等待每一部電腦上的 Date1 工作完成。
它將產生的工作物件集合 (陣列) 儲存在 $done 變數中。

第四個命令會使用 $done 變數中工作物件陣列的 **Count** 屬性來判斷已完成的作業數目。

### 範例3：判斷第一個背景工作完成的時間

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

這則範例會使用 *任何***等候工作** 的參數，來判斷在目前會話中執行的多個背景工作的第一個作業完成的時間。
它也會示範如何使用 **Wait 工作** Cmdlet 來等候遠端工作完成。

第一個命令會在 Machines.txt 檔案中列出的每一部電腦上建立 **pssession** ，並將 **pssession** 物件儲存在 $s 變數中。
命令使用 Get-Content Cmdlet 取得檔案的內容。
**Get Content** 命令會以括弧括住，以確保它會在 New-PSSession 命令之前執行。

第二個命令會在 $c 變數中儲存一個 **Get EventLog** 命令字串（以引號括住）。

第三個命令會使用 Invoke-Command Cmdlet，在 $s 的每個會話中執行 **啟動工作** 。
**Start-Job** 命令會啟動執行 $c 變數中之 **Get-EventLog** 命令的背景工作。

命令使用 **Using** 範圍修飾符指出 $c 變數是在本機電腦上定義。
**Using** 範圍修飾符是在 Windows PowerShell 3.0 中引進。
如需 **Using** 範圍修飾符的詳細資訊，請參閱 [about_Remote_Variables](about/about_Remote_Variables.md)。

第四個命令使用 **Invoke 命令** 在會話中執行 **等候工作** 命令。
它會使用 *Any* 參數來等候，直到遠端電腦上的第一個工作完成為止。

### 範例4：設定遠端電腦上作業的等候時間

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

此範例示範如何使用 **等候工作** 的 *Timeout* 參數，為遠端電腦上執行的作業設定等候時間上限。

第一個命令會在三部遠端電腦上建立 **PSSession** (Server01、Server02 和 Server03) ，然後將 **pssession** 物件儲存在 $s 變數中。

第二個命令使用 **Invoke 命令** ，在 $s 的每個 **PSSession** 物件中執行 **啟動工作** 。
它會將產生的工作物件儲存在 $jobs 變數中。

第三個命令使用 **Invoke 命令** ，在 $s 的每個會話中執行 **等候工作** 。
**等候工作** 命令會判斷所有命令是否已在30秒內完成。
它會使用值為30的 *Timeout* 參數來建立最長等待時間，然後將命令的結果儲存在 $done 變數中。

在本例中，30 秒之後，只有 Server02 電腦上的命令已完成。
**等候作業** 結束等候、顯示命令提示字元，然後傳回代表已完成作業的物件。

$done 變數包含代表已在 Server02 上執行之工作的工作物件。

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

此命令會等候120秒 (兩) 分鐘的時間，DailyLog 作業才會完成。
如果作業未在接下來的兩分鐘內完成，則會傳回命令提示字元，而工作會繼續在背景執行。

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

此範例示範如何使用 **啟動工作** ，在本機電腦上使用「 **等候工作** 」 Cmdlet 來啟動工作。

這些命令會啟動作業，以取得上周新增或更新的 PowerShell 腳本檔案。

第一個命令會使用 **啟動工作** ，在本機電腦上啟動背景工作。
作業會執行 Get-ChildItem 命令，以取得在上周新增或更新的所有檔案，其副檔名為 ps1。

第三個命令會使用 **等候工作** 等候工作完成。
當作業完成時，此命令會顯示工作物件，其中包含作業的相關資訊。

### 範例9：使用 Invoke-Command 等候遠端電腦上啟動的工作

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

此範例示範如何使用 **調用命令** 的 *AsJob* 參數，在遠端電腦上使用「 **等待工作** 」啟動作業。
使用 *AsJob* 時，會在本機電腦上建立工作，而即使工作是在遠端電腦上執行，也會將結果自動傳回到本機電腦。

此範例會使用 **等候工作** ，判斷在三部遠端電腦上的會話中執行的 **Get 進程** 命令是否已完成。

第一個命令會在三部電腦上建立 **PSSession** 物件，並將它們儲存在 $s 變數中。

第二個命令會使用 **Invoke 命令** ，在 $s 的三個會話中的每個會話中執行 **取得處理** 程式。
此命令會使用 *AsJob* 參數，以非同步方式以背景工作方式執行命令。
命令會傳回工作物件，就像使用 **啟動工作** 啟動的工作一樣，工作物件會儲存在 $j 變數中。

第三個命令使用管線運算子 (|) 將 $j 中的工作物件傳送至 **Wait 工作** Cmdlet。
在此情況下，不需要使用 **Invoke 命令** 命令，因為作業位於本機電腦上。

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

指出當任何作業完成時，此 Cmdlet 會顯示命令提示字元，並傳回工作物件。
依預設， **等候工作** 會等到所有指定的工作都完成後，才會顯示提示。

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

指定條件的雜湊表。
此 Cmdlet 會等候符合雜湊表中所有條件的工作。
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

### -Force

指出此 Cmdlet 會繼續等待處於暫停或已中斷線上狀態的工作。
依預設，當作業處於下列其中一個狀態時， **等候作業** 會傳回或結束等候：

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
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

指定此 Cmdlet 等候之作業的實例識別碼陣列。
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

### -Job

指定此 Cmdlet 等候的作業。
輸入包含工作物件的變數，或輸入可取得工作物件的命令。
您也可以使用管線運算子將工作物件傳送至 **Wait 工作** Cmdlet。
依預設， **等候工作** 會等候目前會話中建立的所有作業。

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

指定工作狀態。
此 Cmdlet 只會等待處於指定狀態的工作。
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
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Timeout

指定每個背景工作的最長等候時間（以秒為單位）。
預設值-1 表示 Cmdlet 會等候，直到工作完成為止。
當您提交 **等待工作** 命令時（而不是 **啟動工作** 命令），就會開始計時。

如果超過這個時間，即使工作仍在執行，也會結束等待並返回命令提示字元。
此命令不會顯示任何錯誤訊息。

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

此 Cmdlet 會傳回代表已完成之工作的工作物件。
如果因為超過 *Timeout* 參數的值而結束等候，則 **等待作業** 不會傳回任何物件。

## 注意

* 依預設，當作業處於下列其中一個狀態時， **等候作業** 會傳回或結束等候：

- Completed
- 失敗
- 已停止
- 暫止
- 中斷連接直接 **等候工作** ，以繼續等候已暫止和已中斷連線的作業，請使用 *Force* 參數。

## 相關連結

[Get-Job](Get-Job.md)

[Invoke-Command](Invoke-Command.md)

[Receive-Job](Receive-Job.md)

[Remove-Job](Remove-Job.md)

[Start-Job](Start-Job.md)

[Stop-Job](Stop-Job.md)
