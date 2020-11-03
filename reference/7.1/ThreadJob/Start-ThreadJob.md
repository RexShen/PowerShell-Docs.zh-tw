---
external help file: ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 01/28/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: 9ac0570a5e26de47438a48817785836348de19cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202592"
---
# Start-ThreadJob

## 概要
建立與 Cmdlet 類似的背景工作 `Start-Job` 。

## SYNTAX

### ScriptBlock

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### FilePath

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

## DESCRIPTION

`Start-ThreadJob` 建立與 Cmdlet 類似的背景工作 `Start-Job` 。 主要差異在於建立的工作會在本機進程內的不同執行緒中執行。 根據預設，工作會使用啟動作業之呼叫端的目前工作目錄。

此 Cmdlet 也支援 **ThrottleLimit** 參數，以限制一次執行的作業數目。 當作業啟動時，會將它們排入佇列，並等候目前的作業數目降至低於節流限制。

## 範例

### 範例 1-建立執行緒限制為2的背景工作

```powershell
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } } -ThrottleLimit 2
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Get-Job
```

```Output
Id   Name   PSJobTypeName   State        HasMoreData   Location     Command
--   ----   -------------   -----        -----------   --------     -------
1    Job1   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
2    Job2   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
3    Job3   ThreadJob       NotStarted   False         PowerShell   1..100 | % { sleep 1;...
```

### 範例 2-比較 Start-Job 和 Start-ThreadJob 的效能

這個範例會顯示與之間的差異 `Start-Job` `Start-ThreadJob` 。 作業會執行 `Start-Sleep` Cmdlet 1 秒。 由於工作會以平行方式執行，因此總執行時間大約是1秒，再加上建立作業所需的任何時間。

```powershell
# start five background jobs each running 1 second
Measure-Command {1..5 | % {Start-Job {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
Measure-Command {1..5 | % {Start-ThreadJob {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
```

```Output
TotalSeconds
------------
   5.7665849
   1.5735008
```

在減去1秒的執行時間之後，您會看到 `Start-Job` 大約需要4.8 秒的時間來建立五個作業。 `Start-ThreadJob` 有8倍的速度，大約需要0.6 秒來建立五個作業。 您的環境中可能會有不同的結果，但相對改進應該相同。

### 範例 3-使用 InputObject 建立作業

在此範例中，腳本區塊會使用 `$input` 變數來接收來自 **InputObject** 參數的輸入。 這也可以藉由將物件輸送至來完成 `Start-ThreadJob` 。

```powershell
$j = Start-ThreadJob -InputObject (Get-Process pwsh) -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

```powershell
$j = Get-Process pwsh | Start-ThreadJob -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

## PARAMETERS

### -ArgumentList

針對 **FilePath** 或 **ScriptBlock** 參數所指定的腳本，指定引數或參數值的陣列。

**ArgumentList** 必須是命令列上的最後一個參數。 參數名稱後面的所有值都是引數清單中的解讀值。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定要以背景工作的形式執行的指令檔。 輸入腳本的路徑和檔案名。 腳本必須位於本機電腦或本機電腦可以存取的資料夾中。

當您使用此參數時，PowerShell 會將指定之指令檔的內容轉換為腳本區塊，並以背景工作的形式執行腳本區塊。

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

指定要在工作開始之前執行的命令。 以大括弧括住命令 (`{}`) 來建立腳本區塊。

使用這個參數來準備執行工作的工作階段。 例如，您可以使用它將函式和模組新增至會話。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定用來做為腳本區塊輸入的物件。 它也允許管線輸入。 使用 `$input` 腳本區塊中的自動變數來存取輸入物件。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定新工作的好記名稱。 您可以使用此名稱來識別其他工作 Cmdlet 的作業，例如 `Stop-Job` Cmdlet。

預設的易記名稱是 "Job #"，其中 "#" 是每項作業的遞增序號。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

指定要在背景工作執行的命令。 以大括弧括住命令 (`{}`) 來建立腳本區塊。 使用 `$Input` 自動變數來存取 **InputObject** 參數的值。 這是必要參數。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StreamingHost

此參數提供安全線程的方式，讓 `Write-Host` 輸出直接移至傳遞的 **PSHost** 物件中。 如果沒有它，輸出就會 `Write-Host` 移至作業資訊資料流程集合，而且在作業執行完成之後，才會出現在主機主控台中。

```yaml
Type: System.Management.Automation.Host.PSHost
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

此參數會限制一次執行的作業數目。 當作業啟動時，會將它們排入佇列，並等候執行緒集區中的執行緒可執行作業。 預設限制為5個執行緒。

執行緒集區大小對 PowerShell 會話而言是全域的。 在一個呼叫中指定 **ThrottleLimit** ，就會在相同的會話中設定後續呼叫的限制。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

## 輸出

### ThreadJob.ThreadJob

## 注意

## 相關連結

[Start-Job](../Microsoft.PowerShell.Core/Start-Job.md)

[Stop-Job](../Microsoft.PowerShell.Core/Stop-Job.md)

[Receive-Job](../Microsoft.PowerShell.Core/Receive-Job.md)

