---
title: 在多重執行緒處理時顯示進度
description: 透過 Foreach-Object -Parallel 在多個執行緒之間使用 Write-Progress 的方法
ms.date: 08/02/2020
ms.openlocfilehash: 909fc1bbdeded8845b1955e3384fb55db7173030
ms.sourcegitcommit: 640646992955116def23d16dd12c221857d37b68
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2020
ms.locfileid: "89410837"
---
# <a name="writing-progress-across-multiple-threads-with-foreach-parallel"></a><span data-ttu-id="15251-103">使用 Foreach Parallel 在多個執行緒之間寫入進度</span><span class="sxs-lookup"><span data-stu-id="15251-103">Writing Progress across multiple threads with Foreach Parallel</span></span>

<span data-ttu-id="15251-104">從 PowerShell 7.0 開始，即可使用 [Foreach-Object](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object) Cmdlet 中的 **Parallel** 參數，同時處理多個執行緒。</span><span class="sxs-lookup"><span data-stu-id="15251-104">Starting in PowerShell 7.0, the ability to work in multiple threads simultaneously is possible using the **Parallel** parameter in the [Foreach-Object](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object) cmdlet.</span></span> <span data-ttu-id="15251-105">不過，同時監視這些執行緒的進度可能會相當具有挑戰性。</span><span class="sxs-lookup"><span data-stu-id="15251-105">Monitoring the progress of these threads can be a challenge though.</span></span> <span data-ttu-id="15251-106">一般而言，您可使用 [Write-Progress](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress) 來監視處理序的進度。</span><span class="sxs-lookup"><span data-stu-id="15251-106">Normally, you can monitor the progress of a process using [Write-Progress](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress).</span></span>
<span data-ttu-id="15251-107">不過，因為在使用 **Parallel** 時，PowerShell 會針對每個執行緒使用個別的 Runspace，所以將進度回報給主機並不像一般使用 `Write-Progress` 時那樣的簡單。</span><span class="sxs-lookup"><span data-stu-id="15251-107">However, since PowerShell uses a separate runspace for each thread when using **Parallel**, reporting the progress back to the host isn't as straight forward as normal use of `Write-Progress`.</span></span>

## <a name="using-a-synced-hashtable-to-track-progress"></a><span data-ttu-id="15251-108">使用同步雜湊表來追蹤進度</span><span class="sxs-lookup"><span data-stu-id="15251-108">Using a synced hashtable to track progress</span></span>

<span data-ttu-id="15251-109">寫入多個執行緒的進度時，追蹤會變得相當棘手，因為在 PowerShell 中執行平行處理序時，每個處理序都有自身的 Runspace。</span><span class="sxs-lookup"><span data-stu-id="15251-109">When writing the progress from multiple threads, tracking becomes difficult because when running parallel processes in PowerShell, each process has it's own runspace.</span></span> <span data-ttu-id="15251-110">若要解決此情況，您可使用[同步雜湊表](/dotnet/api/system.collections.hashtable.synchronized)。</span><span class="sxs-lookup"><span data-stu-id="15251-110">To get around this, you can use a [synchronized hashtable](/dotnet/api/system.collections.hashtable.synchronized).</span></span> <span data-ttu-id="15251-111">同步雜湊表是一種安全執行緒的資料結構，可由多個執行緒同時修改，而不會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="15251-111">A synced hashtable is a thread safe data structure that can be modified by multiple threads simultaneously without throwing an error.</span></span>

### <a name="set-up"></a><span data-ttu-id="15251-112">設定</span><span class="sxs-lookup"><span data-stu-id="15251-112">Set up</span></span>

<span data-ttu-id="15251-113">這種方法的其中一個缺點是，為了確保所有處理序都能順利執行而不會發生錯誤，該方法所採用的設定稍嫌複雜。</span><span class="sxs-lookup"><span data-stu-id="15251-113">One of the downsides to this approach is it takes a, somewhat, complex set up to ensure everything runs without error.</span></span>

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

<span data-ttu-id="15251-114">這個區段會針對三個不同目的建立三種不同的資料結構。</span><span class="sxs-lookup"><span data-stu-id="15251-114">This section creates three different data structures, for three different purposes.</span></span>

<span data-ttu-id="15251-115">`$dataSet` 變數會儲存用來協調後續步驟的雜湊表陣列，以避免需要修改的風險。</span><span class="sxs-lookup"><span data-stu-id="15251-115">The `$dataSet` variable stores an array of hashtables that is used to coordinate the next steps without the risk of being modified.</span></span> <span data-ttu-id="15251-116">如果在逐一查看集合時修改了物件集合，則 PowerShell 會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="15251-116">If an object collection is modified while iterating through the collection, PowerShell throws an error.</span></span> <span data-ttu-id="15251-117">您必須讓迴圈中的物件集合與所要修改物件分開。</span><span class="sxs-lookup"><span data-stu-id="15251-117">You must keep the object collection in the loop separate from the objects being modified.</span></span> <span data-ttu-id="15251-118">每個雜湊表中的 `Id` 索引鍵都是模擬處理序的識別碼。</span><span class="sxs-lookup"><span data-stu-id="15251-118">The `Id` key in each hashtable is the identifier for a mock process.</span></span> <span data-ttu-id="15251-119">`Wait` 索引鍵會模擬每個受追蹤模擬處理序的工作負載。</span><span class="sxs-lookup"><span data-stu-id="15251-119">The `Wait` key simulates the workload of each mock process being tracked.</span></span>

<span data-ttu-id="15251-120">`$origin` 變數會儲存巢狀雜湊表，此雜湊表中每個索引鍵都屬於模擬處理序識別碼之一。</span><span class="sxs-lookup"><span data-stu-id="15251-120">The `$origin` variable stores a nested hashtable with each key being one of the mock process id's.</span></span>
<span data-ttu-id="15251-121">然後，該變數會用來將儲存在 `$sync` 變數中的同步雜湊表序列化。</span><span class="sxs-lookup"><span data-stu-id="15251-121">Then, it is used to hydrate the synchronized hashtable stored in the `$sync` variable.</span></span> <span data-ttu-id="15251-122">`$sync` 變數會負責將進度回報給父 Runspace，藉此顯示進度。</span><span class="sxs-lookup"><span data-stu-id="15251-122">The `$sync` variable is responsible for reporting the progress back to the parent runspace, which displays the progress.</span></span>

### <a name="running-the-processes"></a><span data-ttu-id="15251-123">執行處理序</span><span class="sxs-lookup"><span data-stu-id="15251-123">Running the processes</span></span>

<span data-ttu-id="15251-124">本區段會執行多重執行緒處理序，並建立部分用來顯示進度的輸出。</span><span class="sxs-lookup"><span data-stu-id="15251-124">This section runs the multi-threaded processes and creates some of the output used to display progress.</span></span>

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

<span data-ttu-id="15251-125">模擬處理序會傳送至 `Foreach-Object` 並作為作業啟動。</span><span class="sxs-lookup"><span data-stu-id="15251-125">The mock processes are sent to `Foreach-Object` and started as jobs.</span></span> <span data-ttu-id="15251-126">**ThrottleLimit** 設定為 **3**，以表示在佇列中執行多個處理序。</span><span class="sxs-lookup"><span data-stu-id="15251-126">The **ThrottleLimit** is set to **3** to highlight running multiple processes in a queue.</span></span> <span data-ttu-id="15251-127">這些作業會儲存在 `$job` 變數中，並提供稍後所有處理序完成時間的資訊。</span><span class="sxs-lookup"><span data-stu-id="15251-127">The jobs are stored in the `$job` variable and allows us to know when all the processes have finished later on.</span></span>

<span data-ttu-id="15251-128">使用 `using:` 陳述式來參考 PowerShell 中的父範圍變數時，您無法透過運算式使其動態化。</span><span class="sxs-lookup"><span data-stu-id="15251-128">When using the `using:` statement to reference a parent scope variable in PowerShell, you can't use expressions to make it dynamic.</span></span> <span data-ttu-id="15251-129">例如，如果嘗試建立 `$process` 變數 (如同 `$process = $using:sync.$($PSItem.id)`)，則會發生錯誤，指出無法在該處使用運算式。</span><span class="sxs-lookup"><span data-stu-id="15251-129">For example, if you tried to create the `$process` variable like this, `$process = $using:sync.$($PSItem.id)`, you would get an error stating you can't use expressions there.</span></span> <span data-ttu-id="15251-130">因此，我們要建立 `$syncCopy` 變數，以便在沒有失敗風險的情況下，參考和修改 `$sync` 變數。</span><span class="sxs-lookup"><span data-stu-id="15251-130">So, we create the `$syncCopy` variable to be able to reference and modify the `$sync` variable without the risk of it failing.</span></span>

<span data-ttu-id="15251-131">接下來，我們會藉由參考同步雜湊表索引鍵，使用 `$process` 變數建置雜湊表來表示目前迴圈中的處理序進度。</span><span class="sxs-lookup"><span data-stu-id="15251-131">Next, we build out a hashtable to represent the progress of the process currently in the loop using the `$process` variable by referencing the synchronized hashtable keys.</span></span> <span data-ttu-id="15251-132">**Activity** 與 **Status** 索引鍵會用作為 `Write-Progress` 的參數值，以便在下一區段中顯示指定模擬處理序的狀態。</span><span class="sxs-lookup"><span data-stu-id="15251-132">The **Activity** and the **Status** keys are used as parameter values for `Write-Progress` to display the status of a given mock process in the next section.</span></span>

<span data-ttu-id="15251-133">`foreach` 迴圈只是一種模擬處理序運作的方式，且是根據 `$dataSet` **Wait** 屬性將該迴圈隨機化來設定 `Start-Sleep` (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="15251-133">The `foreach` loop is just a way to simulate the process working and is randomized based on the `$dataSet` **Wait** attribute to set `Start-Sleep` using milliseconds.</span></span> <span data-ttu-id="15251-134">您計算處理序進度的方式可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="15251-134">How you calculate the progress of your process may vary.</span></span>

### <a name="displaying-the-progress-of-multiple-processes"></a><span data-ttu-id="15251-135">顯示多個處理序的進度</span><span class="sxs-lookup"><span data-stu-id="15251-135">Displaying the progress of multiple processes</span></span>

<span data-ttu-id="15251-136">既然模擬處理序是以作業的形式執行，我們即可開始將處理序進度寫入 PowerShell 視窗。</span><span class="sxs-lookup"><span data-stu-id="15251-136">Now that the mock processes are running as jobs, we can start to write the processes progress to the PowerShell window.</span></span>

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

<span data-ttu-id="15251-137">`$job` 變數包含父**作業**，並具有每個模擬處理序的子**作業**。</span><span class="sxs-lookup"><span data-stu-id="15251-137">The `$job` variable contains the parent **job** and has a child **job** for each of the mock processes.</span></span> <span data-ttu-id="15251-138">當任一子作業仍在執行時，父作業的 **State** 就會維持在 "Running"。</span><span class="sxs-lookup"><span data-stu-id="15251-138">While any of the child jobs are still running, the parent job **State** will remain "Running".</span></span> <span data-ttu-id="15251-139">這可供使用 `while` 迴圈來持續更新每個處理序的進度，直到所有處理序都完成為止。</span><span class="sxs-lookup"><span data-stu-id="15251-139">This allows us to use the `while` loop to continually update the progress of every process until all processes are finished.</span></span>

<span data-ttu-id="15251-140">在 while 迴圈中，我們會針對 `$sync` 變數中的每個索引鍵進行迴圈。</span><span class="sxs-lookup"><span data-stu-id="15251-140">Within the while loop, we loop through each of the keys in the `$sync` variable.</span></span> <span data-ttu-id="15251-141">因為是同步雜湊表，所以仍然可在不斷更新的狀態下存取，且不會擲回任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="15251-141">Since this is a synchronized hashtable, it is constantly updated but can still be accessed without throwing any errors.</span></span>

<span data-ttu-id="15251-142">有一種檢查可確保所回報的處理序確實是使用 `IsNullOrEmpty()` 方法執行。</span><span class="sxs-lookup"><span data-stu-id="15251-142">There is a check to ensure that the process being reported is actually running using the `IsNullOrEmpty()` method.</span></span> <span data-ttu-id="15251-143">如果處理序尚未啟動，迴圈就不會回報該處理序，而會繼續進行，直到迴圈到達已啟動的處理序為止。</span><span class="sxs-lookup"><span data-stu-id="15251-143">If the process hasn't been started, the loop won't report on it and move on to the next until it gets to a process that has been started.</span></span> <span data-ttu-id="15251-144">如果處理序已啟動，則會使用目前索引鍵的雜湊表將參數展開至 `Write-Progress`。</span><span class="sxs-lookup"><span data-stu-id="15251-144">If the process is started, the hashtable from the current key is used to splat the parameters to `Write-Progress`.</span></span>

### <a name="full-example"></a><span data-ttu-id="15251-145">完整範例</span><span class="sxs-lookup"><span data-stu-id="15251-145">Full example</span></span>

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

## <a name="related-links"></a><span data-ttu-id="15251-146">相關連結</span><span class="sxs-lookup"><span data-stu-id="15251-146">Related Links</span></span>

- [<span data-ttu-id="15251-147">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="15251-147">about_Jobs</span></span>](/powershell/module/Microsoft.PowerShell.Core/About/about_Jobs)
- [<span data-ttu-id="15251-148">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="15251-148">about_Scopes</span></span>](/powershell/module/Microsoft.PowerShell.Core/About/about_Scopes)
- [<span data-ttu-id="15251-149">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="15251-149">about_Splatting</span></span>](/powershell/module/Microsoft.PowerShell.Core/About/about_Splatting)
