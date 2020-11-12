---
description: 提供 PowerShell 執行緒型作業的相關資訊。 執行緒作業是背景工作的類型，會在目前會話進程內的不同執行緒中執行命令或運算式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: ba6251a195d3efdebd427b3f705386336b069211
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524632"
---
# <a name="about-thread-jobs"></a>關於執行緒作業

## <a name="short-description"></a>簡短描述

提供 PowerShell 執行緒型作業的相關資訊。 執行緒作業是背景工作的類型，會在目前會話進程內的不同執行緒中執行命令或運算式。

## <a name="long-description"></a>完整描述

PowerShell 會透過作業同時執行命令和腳本。 PowerShell 提供三種工作類型來支援平行存取。

- `RemoteJob` -命令和腳本會在遠端會話中執行。 如需詳細資訊，請參閱 [about_Remote_Jobs](about_Remote_Jobs.md)。
- `BackgroundJob` -命令和腳本會在本機電腦上的個別進程中執行。 如需詳細資訊，請參閱 [about_Jobs](about_Jobs.md)。
- `PSTaskJob` 或 `ThreadJob` -命令和腳本會在本機電腦上相同進程內的個別執行緒中執行。

以執行緒為基礎的作業不像遠端和背景工作一樣健全，因為它們在不同執行緒上的相同進程中執行。 如果有一項作業發生嚴重錯誤，導致進程損毀，則會終止進程中的所有其他工作。

不過，以執行緒為基礎的作業需要較少的額外負荷。 它們不會使用遠端層或序列化。 結果物件會傳回做為目前會話中之即時物件的參考。 如果沒有此額外負荷，以執行緒為基礎的作業執行速度會更快，且使用的資源比其他作業類型還要少。

> [!IMPORTANT]
> 建立作業的父會話也會監視作業狀態，並收集管線資料。 當工作達到已完成狀態時，父進程會終止作業子進程。 如果父會話終止，則所有執行中的子工作都會連同其子進程一起終止。

有兩種方法可以解決這種情況：

1. 用 `Invoke-Command` 來建立在已中斷連線的會話中執行的作業。 如需詳細資訊，請參閱 [about_Remote_Jobs](about_Remote_Jobs.md)。
1. 用 `Start-Process` 來建立新的處理常式，而不是作業。 如需詳細資訊，請參閱 [啟動流程](xref:Microsoft.PowerShell.Management.Start-Process)。

## <a name="how-to-start-and-manage-thread-based-jobs"></a>如何啟動及管理以執行緒為基礎的作業

有兩種方式可以啟動以執行緒為基礎的作業：

- `Start-ThreadJob` -從 **ThreadJob** 模組
- `ForEach-Object -Parallel -AsJob` -已在 PowerShell 7.0 中新增平行功能

使用 [about_Jobs](about_Jobs.md)所述的相同 **工作** Cmdlet 來管理以執行緒為基礎的作業。

### <a name="using-start-threadjob"></a>使用 `Start-ThreadJob`

**ThreadJob** 模組第一次隨附于 PowerShell 6。 也可以從 Windows PowerShell 5.1 的 PowerShell 資源庫安裝。

若要在本機電腦上啟動執行緒作業，請使用 `Start-ThreadJob` Cmdlet 搭配以大括弧括住的命令或腳本 (`{ }`) 。

下列範例會啟動在 `Get-Process` 本機電腦上執行命令的執行緒作業。

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

此 `Start-ThreadJob` 命令會傳回 `ThreadJob` 代表正在執行之作業的物件。 工作物件包含工作的相關實用資訊，包括其目前正在執行的狀態。 它會在產生結果時收集工作結果。

### <a name="using-foreach-object--parallel--asjob"></a>使用 `ForEach-Object -Parallel -AsJob`

PowerShell 7.0 已將新的參數集新增至 `ForEach-Object` Cmdlet。 新的參數可讓您在平行線程中以 PowerShell 作業的形式執行腳本區塊。

您可以透過管線將資料傳送至 `ForEach-Object -Parallel` 。 資料會傳遞至平行執行的腳本區塊。 `-AsJob`參數會為每個平行線程建立工作物件。

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
36860.8226

(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
7.1975
```

上述第一個範例顯示一個 foreach 迴圈，該迴圈會建立1000執行緒作業來進行簡單的字串寫入。 因為作業額外負荷，所以需要超過36秒才能完成。

第二個範例會 `ForEach` 執行 Cmdlet 來執行相同的1000作業。
這次 `ForEach-Object` 會在單一線程上循序執行，而不會產生任何作業額外負荷。 它只會在7毫秒內完成。

在下列範例中，會針對10個不同的系統記錄檔收集最多5000個專案。 由於腳本牽涉到讀取一些記錄，因此平行執行作業是有意義的。

```powershell
$logNames.count
10

Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

腳本會在工作以平行方式執行的一半時間內完成。

```powershell
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

## <a name="thread-jobs-and-variables"></a>執行緒作業和變數

有多種方式可將值傳遞至以執行緒為基礎的作業。

`Start-ThreadJob` 可以接受輸送至 Cmdlet 的變數，透過關鍵詞傳遞至腳本區塊， `$using` 或透過 **ArgumentList** 參數傳入。

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

`ForEach-Object -Parallel` 接受變數中的管道，以及透過關鍵詞直接傳遞至腳本區塊的變數 `$using` 。

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

因為執行緒作業是在相同的進程中執行，所以任何傳遞至作業的變數參考型別都必須小心處理。 如果它不是安全線程的物件，則永遠不會將它指派給，而且永遠不應該在其上叫用方法和屬性。

下列範例會將安全線程的 .NET `ConcurrentDictionary` 物件傳遞至所有子工作，以收集唯一的命名進程物件。 由於它是安全線程的物件，因此可以在進程中同時執行工作時安全地使用它。

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
