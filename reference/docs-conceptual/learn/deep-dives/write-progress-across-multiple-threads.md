---
title: 在多重執行緒處理時顯示進度
description: 透過 Foreach-Object -Parallel 在多個執行緒之間使用 Write-Progress 的方法
ms.date: 08/02/2020
ms.openlocfilehash: 909fc1bbdeded8845b1955e3384fb55db7173030
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "89410837"
---
# <a name="writing-progress-across-multiple-threads-with-foreach-parallel"></a>使用 Foreach Parallel 在多個執行緒之間寫入進度

從 PowerShell 7.0 開始，即可使用 [Foreach-Object](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object) Cmdlet 中的 **Parallel** 參數，同時處理多個執行緒。 不過，同時監視這些執行緒的進度可能會相當具有挑戰性。 一般而言，您可使用 [Write-Progress](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress) 來監視處理序的進度。
不過，因為在使用 **Parallel** 時，PowerShell 會針對每個執行緒使用個別的 Runspace，所以將進度回報給主機並不像一般使用 `Write-Progress` 時那樣的簡單。

## <a name="using-a-synced-hashtable-to-track-progress"></a>使用同步雜湊表來追蹤進度

寫入多個執行緒的進度時，追蹤會變得相當棘手，因為在 PowerShell 中執行平行處理序時，每個處理序都有自身的 Runspace。 若要解決此情況，您可使用[同步雜湊表](/dotnet/api/system.collections.hashtable.synchronized)。 同步雜湊表是一種安全執行緒的資料結構，可由多個執行緒同時修改，而不會擲回錯誤。

### <a name="set-up"></a>設定

這種方法的其中一個缺點是，為了確保所有處理序都能順利執行而不會發生錯誤，該方法所採用的設定稍嫌複雜。

```powershell
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)
```

這個區段會針對三個不同目的建立三種不同的資料結構。

`$dataSet` 變數會儲存用來協調後續步驟的雜湊表陣列，以避免需要修改的風險。 如果在逐一查看集合時修改了物件集合，則 PowerShell 會擲回錯誤。 您必須讓迴圈中的物件集合與所要修改物件分開。 每個雜湊表中的 `Id` 索引鍵都是模擬處理序的識別碼。 `Wait` 索引鍵會模擬每個受追蹤模擬處理序的工作負載。

`$origin` 變數會儲存巢狀雜湊表，此雜湊表中每個索引鍵都屬於模擬處理序識別碼之一。
然後，該變數會用來將儲存在 `$sync` 變數中的同步雜湊表序列化。 `$sync` 變數會負責將進度回報給父 Runspace，藉此顯示進度。

### <a name="running-the-processes"></a>執行處理序

本區段會執行多重執行緒處理序，並建立部分用來顯示進度的輸出。

```powershell
$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}
```

模擬處理序會傳送至 `Foreach-Object` 並作為作業啟動。 **ThrottleLimit** 設定為 **3**，以表示在佇列中執行多個處理序。 這些作業會儲存在 `$job` 變數中，並提供稍後所有處理序完成時間的資訊。

使用 `using:` 陳述式來參考 PowerShell 中的父範圍變數時，您無法透過運算式使其動態化。 例如，如果嘗試建立 `$process` 變數 (如同 `$process = $using:sync.$($PSItem.id)`)，則會發生錯誤，指出無法在該處使用運算式。 因此，我們要建立 `$syncCopy` 變數，以便在沒有失敗風險的情況下，參考和修改 `$sync` 變數。

接下來，我們會藉由參考同步雜湊表索引鍵，使用 `$process` 變數建置雜湊表來表示目前迴圈中的處理序進度。 **Activity** 與 **Status** 索引鍵會用作為 `Write-Progress` 的參數值，以便在下一區段中顯示指定模擬處理序的狀態。

`foreach` 迴圈只是一種模擬處理序運作的方式，且是根據 `$dataSet` **Wait** 屬性將該迴圈隨機化來設定 `Start-Sleep` (以毫秒為單位)。 您計算處理序進度的方式可能會有所不同。

### <a name="displaying-the-progress-of-multiple-processes"></a>顯示多個處理序的進度

既然模擬處理序是以作業的形式執行，我們即可開始將處理序進度寫入 PowerShell 視窗。

```powershell
while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

`$job` 變數包含父 **作業**，並具有每個模擬處理序的子 **作業**。 當任一子作業仍在執行時，父作業的 **State** 就會維持在 "Running"。 這可供使用 `while` 迴圈來持續更新每個處理序的進度，直到所有處理序都完成為止。

在 while 迴圈中，我們會針對 `$sync` 變數中的每個索引鍵進行迴圈。 因為是同步雜湊表，所以仍然可在不斷更新的狀態下存取，且不會擲回任何錯誤。

有一種檢查可確保所回報的處理序確實是使用 `IsNullOrEmpty()` 方法執行。 如果處理序尚未啟動，迴圈就不會回報該處理序，而會繼續進行，直到迴圈到達已啟動的處理序為止。 如果處理序已啟動，則會使用目前索引鍵的雜湊表將參數展開至 `Write-Progress`。

### <a name="full-example"></a>完整範例

```powershell
# Example workload
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)

$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}

while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

## <a name="related-links"></a>相關連結

- [about_Jobs](/powershell/module/Microsoft.PowerShell.Core/About/about_Jobs)
- [about_Scopes](/powershell/module/Microsoft.PowerShell.Core/About/about_Scopes)
- [about_Splatting](/powershell/module/Microsoft.PowerShell.Core/About/about_Splatting)
