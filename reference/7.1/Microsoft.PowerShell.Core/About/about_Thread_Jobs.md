---
description: 提供 PowerShell 執行緒型作業的相關資訊。 執行緒作業是背景工作的類型，會在目前會話進程內的不同執行緒中執行命令或運算式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: d3f7c2754a2e54bc1b6f9fb95d1cf6ce2fed5b9b
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "93208583"
---
# <a name="about-thread-jobs"></a>關於執行緒作業

## <a name="short-description"></a>簡短描述

提供 PowerShell 執行緒型作業的相關資訊。 執行緒作業是背景工作的類型，會在目前會話進程內的不同執行緒中執行命令或運算式。

## <a name="long-description"></a>完整描述

本文說明如何在本機電腦上的 PowerShell 中執行執行緒作業。
如需在本機電腦上執行背景工作的詳細資訊，請參閱 [about_Jobs](about_Jobs.md)。

您可以使用兩種方式之一來啟動執行緒作業。

第一種方式是使用 `Start-ThreadJob` Cmdlet。 此 Cmdlet 適用于 PowerShell 隨附的 **ThreadJob** 模組。 `Start-ThreadJob` 傳回單一工作物件，該物件會封裝執行中的命令或腳本，並可與所有 PowerShell 作業操作 Cmdlet 一起使用。

第二種方式是使用 `ForEach-Object` Cmdlet， `-Parallel` 搭配參數腳本區塊引數和 `-AsJob` 參數參數。 這個 Cmdlet 會傳回單一 (父) 工作物件，其中包含每個以管線傳送至 Cmdlet 的輸入子工作。 每個子工作會在不同的執行緒中執行腳本，並 (`-ThrottleLimit`) 限制在指定時間執行的子工作數目。

## <a name="the-job-cmdlets"></a>作業 CMDLET

|Cmdlet           |描述                                            |
|-----------------|-------------------------------------------------------|
|`Start-ThreadJob`|在本機電腦上啟動執行緒作業。               |
|`ForEach-Object` |啟動每個管道輸入物件的執行緒作業（當   |
|                 |搭配-Parallel 和-AsJob 參數使用。             |
|`Get-Job`        |取得在目前會話中啟動的工作。|
|`Receive-Job`    |取得工作的結果。                              |
|`Stop-Job`       |停止正在執行的作業。                                   |
|`Wait-Job`       |抑制命令提示字元，直到其中一個或所有工作為|
|                 |完成。                                              |
|`Remove-Job`     |刪除作業。                                         |

## <a name="how-to-start-a-thread-job-on-the-local-computer"></a>如何在本機電腦上啟動執行緒作業

若要在本機電腦上啟動執行緒作業，請使用 `Start-ThreadJob` Cmdlet。

若要撰寫 `Start-ThreadJob` 命令，請以大括弧括住命令或腳本 (`{ }`) 。

下列命令會啟動在 `Get-Process` 本機電腦上執行命令的執行緒作業。

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

此 `Start-ThreadJob` 命令會傳回 `ThreadJob` 代表正在執行之作業的物件。 工作物件包含工作的相關實用資訊，包括其目前正在執行的狀態。 它會在產生結果時收集工作結果。

若要撰寫 `ForEach-Object -Parallel` 命令，請使用管線將資料傳送至命令，並將工作以大括弧括住的命令或腳本 (`{}`) 。 使用 `-AsJob` 參數參數，以傳回工作物件。

下列命令會啟動一個工作，其中包含以管道傳送至命令的每個輸入值的子工作。 每個子作業都會以 `Write-Output` 輸送的輸入值做為引數來執行命令。

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

此 `ForEach-Object -Parallel` 命令會傳回 `PSTaskJob` 物件，其中包含每個管道輸入值的子工作。 工作物件包含有關子工作執行狀態的有用資訊。 它會在產生結果時收集子工作的結果。

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a>如何等候工作完成並取出工作結果

您可以使用 PowerShell 工作 Cmdlet （例如 `Wait-Job` 和） `Receive-Job` 來等候作業完成，然後傳回作業所產生的所有結果。

下列命令會啟動執行命令的執行緒作業 `Get-Process` ，然後等候命令完成，最後傳回命令所產生的所有資料結果。

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

下列命令會啟動執行 `Write-Output` 每個輸送輸入之命令的作業，然後等候所有子工作完成，最後傳回子工作所產生的所有資料結果。

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

Cmdlet 會傳回 `Receive-Job` 子工作的結果。

```powershell
1
3
2
4
5
```

由於每個子工作都平行執行，因此不保證產生的結果順序。

## <a name="powershell-concurrency-and-jobs"></a>PowerShell 並行和作業

PowerShell 會透過作業同時執行命令和腳本。 PowerShell 提供三個以工作為基礎的解決方案，以支援平行存取。

|工作 (Job)            |Description                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |命令和腳本會在遠端電腦上執行。                 |
|`BackgroundJob`|命令和腳本在本機的個別進程中執行    |
|               |新的虛擬主機。                                                     |
|`ThreadJob`    |命令和腳本在相同的執行緒中執行  |
|               |在本機電腦上處理。                                |

每種類型的作業都有其優點和缺點。 在不同的電腦上或在個別的進程中遠端執行腳本有很大的隔離。 任何錯誤都不會影響其他執行中的工作或啟動作業的用戶端。 但是遠端層會增加額外負荷，包括物件序列化。 在遠端會話中傳遞的所有物件都必須序列化，然後在用戶端與目標會話之間傳遞時還原序列化。 序列化作業可以針對大型複雜資料物件使用許多計算和記憶體資源。

## <a name="powershell-thread-based-jobs"></a>以 PowerShell 執行緒為基礎的作業

以執行緒為基礎的作業不像遠端和背景工作一樣健全，因為它們在不同執行緒上的相同進程中執行。 如果有一項作業發生嚴重錯誤，導致進程損毀，則程式中的所有其他作業也會失敗。

不過，以執行緒為基礎的作業會有較少的額外負荷。 它們不需要使用遠端層或序列化。 結果是，以執行緒為基礎的作業的執行速度通常會比其他工作類型更快，且使用的資源更少。

## <a name="thread-job-performance"></a>執行緒作業效能

執行緒作業比其他類型的作業更快且更輕量。 但是，相較于工作正在進行的工作，它們的負荷仍可能很大。

PowerShell 會在會話中執行命令和腳本。 在會話中，一次只能執行一個命令或腳本。 因此，在執行多個工作時，每個工作會在不同的會話中執行。 每個會話都有額外負荷。

當執行緒作業所執行的工作大於用來執行作業的會話負荷時，會提供最佳效能。 符合此準則的案例有兩種。

- 工作需要大量計算-在多個執行緒工作上執行腳本可利用多個處理器核心並更快完成。

- 工作包含大量等候的腳本，該腳本會花時間等候 i/o 或遠端呼叫的結果。 平行執行的速度通常會比循序執行的速度還要快。

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
10457.962


(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
24.9277
```

上述第一個範例顯示一個 foreach 迴圈，該迴圈會建立1000執行緒作業來進行簡單的字串寫入。 因為作業額外負荷，所以需要超過33秒才能完成。

第二個範例會執行指令 `ForEach` 程式來執行相同的1000作業，並依序執行每個字串寫入，而不會有任何作業額外負荷。 它只會在25毫秒內完成。

```powershell
$logNames.count
10

Measure-Command {
    $logs = $logNames | ForEach {
        Start-ThreadJob {
            Get-WinEvent -LogName $using:_ -MaxEvents 5000 2>$null
        } -ThrottleLimit 10
    } | Wait-Job | Receive-Job
}

TotalMilliseconds : 115994.3 (1 minute 56 seconds)
$logs.Count
50000
```

在上述範例中，會針對10個不同的系統記錄檔收集最多5000個專案。 由於腳本牽涉到讀取一些記錄，因此平行執行作業是有意義的。 而且作業會以順序完成，就像腳本執行時一樣快完成兩次。

```powershell
Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a>執行緒作業和變數

變數會以各種方式傳遞至執行緒作業。

`Start-ThreadJob` 可以接受輸送至 Cmdlet 的變數，透過關鍵詞傳遞至腳本區塊， `$using` 或透過 **ArgumentList** 參數傳入。

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job

`ForEach-Object -Parallel` accepts piped in variables, and variables passed
directly to the script block via the `$using` keyword.

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

因為執行緒作業是在相同的進程中執行，所以任何傳遞至作業的變數參考型別都必須小心處理。 如果它不是安全線程的物件，則永遠不會將它指派給，而且永遠不應該在其上叫用方法和屬性。

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
$jobs = Get-Process | ForEach {
    Start-ThreadJob {
        $proc = $using:_
        $dict = $using:threadSafeDictionary
        $dict.TryAdd($proc.ProcessName, $proc)
    }
}
$jobs | Wait-Job | Receive-Job

$threadSafeDictionary.Count
96

$threadSafeDictionary["pwsh"]

NPM(K)  PM(M)   WS(M) CPU(s)    Id SI ProcessName
------  -----   ----- ------    -- -- -----------
  112  108.25  124.43  69.75 16272  1 pwsh
```

上述範例會將安全線程的 dotNet `ConcurrentDictionary` 物件傳遞至所有子工作，以收集唯一名稱的處理常式物件。 由於它是安全線程的物件，因此可以在進程中同時執行工作時安全地使用它。

## <a name="see-also"></a>另請參閱

- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](about_Thread_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_PSSessions](about_PSSessions.md)
- [Start-Job](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-Job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job)
- [Stop-Job](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Remove-Job](xref:Microsoft.PowerShell.Core.Remove-Job)
