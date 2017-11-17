---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用處理程序 Cmdlet 管理處理程序"
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: 3786fb77167746d6a477dffdd4ea13e863c99964
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="3269f-103">使用處理程序 Cmdlet 管理處理程序</span><span class="sxs-lookup"><span data-stu-id="3269f-103">Managing Processes with Process Cmdlets</span></span>
<span data-ttu-id="3269f-104">您可以使用 Windows PowerShell 中的處理程序 Cmdlet，管理 Windows PowerShell 中的本機和遠端處理程序。</span><span class="sxs-lookup"><span data-stu-id="3269f-104">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="3269f-105">取得處理程序 (Get-Process)</span><span class="sxs-lookup"><span data-stu-id="3269f-105">Getting Processes (Get-Process)</span></span>
<span data-ttu-id="3269f-106">若要取得在本機電腦上執行的處理程序，請在不使用參數的情況下執行 **Get-Process**。</span><span class="sxs-lookup"><span data-stu-id="3269f-106">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="3269f-107">您可以藉由指定處理程序的名稱或識別碼，來取得特定處理程序。</span><span class="sxs-lookup"><span data-stu-id="3269f-107">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="3269f-108">下列命令會取得閒置處理程序︰</span><span class="sxs-lookup"><span data-stu-id="3269f-108">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="3269f-109">雖然 Cmdlet 在某些情況下未傳回任何資料是正常的，但是當您依處理程序的 ProcessId 指定處理程序時，由於一般目的是擷取已知的執行中處理程序，因此如果 **Get-Process** 找不到任何相符項目，則會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3269f-109">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="3269f-110">如果沒有該識別碼的處理程序，很可能是識別碼不正確，或感興趣的處理程序已經結束：</span><span class="sxs-lookup"><span data-stu-id="3269f-110">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99
Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="3269f-111">您可以使用 Get-Process Cmdlet 的 Name 參數，根據處理序名稱指定處理程序的子集。</span><span class="sxs-lookup"><span data-stu-id="3269f-111">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="3269f-112">Name 參數可以接受以逗號分隔的多個名稱清單，而且支援使用萬用字元，因此您可以輸入名稱模式。</span><span class="sxs-lookup"><span data-stu-id="3269f-112">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="3269f-113">例如，下列命令會取得名稱開頭為 "ex" 的處理程序。</span><span class="sxs-lookup"><span data-stu-id="3269f-113">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="3269f-114">因為 .NET System.Diagnostics.Process 類別是 Windows PowerShell 處理程序的基礎，所以它會遵循 System.Diagnostics.Process 所使用的一些慣例。</span><span class="sxs-lookup"><span data-stu-id="3269f-114">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="3269f-115">其中一個慣例是可執行檔的處理程序名稱，絕對不可以在可執行檔名稱結尾包含 ".exe"。</span><span class="sxs-lookup"><span data-stu-id="3269f-115">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="3269f-116">**Get-Process** 也接受 Name 參數有多個值。</span><span class="sxs-lookup"><span data-stu-id="3269f-116">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power* 
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="3269f-117">您可以使用 Get-Process 的 ComputerName 參數取得遠端電腦上的處理程序。</span><span class="sxs-lookup"><span data-stu-id="3269f-117">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="3269f-118">例如，下列命令會取得本機電腦 (以 "localhost" 表示) 和兩部遠端電腦上的 PowerShell 處理程序。</span><span class="sxs-lookup"><span data-stu-id="3269f-118">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="3269f-119">電腦名稱雖然未出現在此顯示中，但儲存在 Get-Process 所傳回之處理程序物件的 MachineName 屬性中。</span><span class="sxs-lookup"><span data-stu-id="3269f-119">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="3269f-120">下列命令會使用 Format-Table Cmdlet 顯示處理程序物件的處理程序 ID、ProcessName 和 MachineName (ComputerName) 屬性。</span><span class="sxs-lookup"><span data-stu-id="3269f-120">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName
  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="3269f-121">這個更複雜的命令會將 MachineName 屬性新增至標準 Get-Process 顯示。</span><span class="sxs-lookup"><span data-stu-id="3269f-121">This more complex command adds the MachineName property to the standard Get-Process display.</span></span> <span data-ttu-id="3269f-122">倒單引號 (\\`)(ASCII 96) 是 Windows PowerShell 接續字元。</span><span class="sxs-lookup"><span data-stu-id="3269f-122">The backtick (\\`)(ASCII 96) is the Windows PowerShell continuation character.</span></span>

```
get-process powershell -computername localhost, Server01, Server02 | format-table -property Handles, `
                    @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}}, `
                    @{Label="PM(K)";Expression={[int]($_.PM/1024)}}, `
                    @{Label="WS(K)";Expression={[int]($_.WS/1024)}}, `
                    @{Label="VM(M)";Expression={[int]($_.VM/1MB)}}, `
                    @{Label="CPU(s)";Expression={if ($_.CPU -ne $()` 
                    {$_.CPU.ToString("N")}}}, `                                                                         
                    Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="3269f-123">停止處理程序 (Stop-Process)</span><span class="sxs-lookup"><span data-stu-id="3269f-123">Stopping Processes (Stop-Process)</span></span>
<span data-ttu-id="3269f-124">Windows PowerShell 可讓您彈性地列出處理程序，但停止處理程序又如何？</span><span class="sxs-lookup"><span data-stu-id="3269f-124">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="3269f-125">**Stop-Process** Cmdlet 接受使用 Name 或 Id 指定您要停止的處理程序。</span><span class="sxs-lookup"><span data-stu-id="3269f-125">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="3269f-126">您是否能夠停止處理程序取決於您的權限。</span><span class="sxs-lookup"><span data-stu-id="3269f-126">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="3269f-127">某些處理程序無法停止。</span><span class="sxs-lookup"><span data-stu-id="3269f-127">Some processes cannot be stopped.</span></span> <span data-ttu-id="3269f-128">例如，如果您嘗試停止閒置處理程序，您會收到錯誤︰</span><span class="sxs-lookup"><span data-stu-id="3269f-128">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="3269f-129">您也可以 **Confirm** 參數來強制提示。</span><span class="sxs-lookup"><span data-stu-id="3269f-129">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="3269f-130">如果您在指定處理程序名稱時使用萬用字元，此參數特別有用，因為您可能會不小心比對一些不想停止的處理程序︰</span><span class="sxs-lookup"><span data-stu-id="3269f-130">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

<span data-ttu-id="3269f-131">您可以使用一些物件篩選 Cmdlet 來管理複雜的處理程序。</span><span class="sxs-lookup"><span data-stu-id="3269f-131">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="3269f-132">因為當處理程序物件不再回應時的 Responding 屬性為 true，所以您可以使用下列命令停止所有無回應的應用程式︰</span><span class="sxs-lookup"><span data-stu-id="3269f-132">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="3269f-133">您可以在其他情況下使用相同的方法。</span><span class="sxs-lookup"><span data-stu-id="3269f-133">You can use the same approach in other situations.</span></span> <span data-ttu-id="3269f-134">例如，假設當使用者啟動另一個應用程式時，次要通知區域應用程式會自動執行。</span><span class="sxs-lookup"><span data-stu-id="3269f-134">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="3269f-135">您可能會發現這在終端機服務工作階段中無法正常運作，但您仍然想要在實體電腦主控台上執行的工作階段中予以保留。</span><span class="sxs-lookup"><span data-stu-id="3269f-135">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="3269f-136">連線到實體電腦桌面之工作階段的工作階段識別碼一律為 0，因此您可以使用 **Where-Object** 和處理程序 **SessionId**，停止該處理程序在其他工作階段中的所有執行個體：</span><span class="sxs-lookup"><span data-stu-id="3269f-136">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="3269f-137">Stop-Process Cmdlet 沒有 ComputerName 參數。</span><span class="sxs-lookup"><span data-stu-id="3269f-137">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="3269f-138">因此，若要在遠端電腦上執行停止處理程序命令，您需要使用 Invoke-Command Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3269f-138">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="3269f-139">例如，若要停止 Server01 遠端電腦上的 PowerShell 處理程序，請輸入：</span><span class="sxs-lookup"><span data-stu-id="3269f-139">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="3269f-140">停止所有其他 Windows PowerShell 工作階段</span><span class="sxs-lookup"><span data-stu-id="3269f-140">Stopping All Other Windows PowerShell Sessions</span></span>
<span data-ttu-id="3269f-141">能夠停止目前工作階段以外的所有執行中 PowerShell 工作階段有時可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="3269f-141">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="3269f-142">如果工作階段使用太多資源或無法存取 (可能在遠端執行或在其他桌面工作階段中)，您可能無法直接將它停止。</span><span class="sxs-lookup"><span data-stu-id="3269f-142">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="3269f-143">不過如果您嘗試停止所有執行中的工作階段，可能反而終止目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="3269f-143">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="3269f-144">每個 Windows PowerShell 工作階段都有包含 Windows PowerShell 處理程序識別碼的環境變數 PID。</span><span class="sxs-lookup"><span data-stu-id="3269f-144">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="3269f-145">您可以根據每個工作階段的識別碼檢查 $PID，並只終止具有不同識別碼的 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="3269f-145">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id.</span></span> <span data-ttu-id="3269f-146">下列管線命令會執行這項操作，並傳回終止的工作階段清單 (因為使用了 **PassThru** 參數)：</span><span class="sxs-lookup"><span data-stu-id="3269f-146">The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -
PassThru
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="3269f-147">啟動、偵錯及等候處理程序</span><span class="sxs-lookup"><span data-stu-id="3269f-147">Starting, Debugging, and Waiting for Processes</span></span>
<span data-ttu-id="3269f-148">Windows PowerShell 也提供啟動 (或重新啟動)、偵錯處理程序，以及等候處理程序完成再執行命令的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3269f-148">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="3269f-149">如需這些 Cmdlet 的資訊，請參閱每個 Cmdlet 的 Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="3269f-149">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="3269f-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3269f-150">See Also</span></span>
- <span data-ttu-id="3269f-151">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span><span class="sxs-lookup"><span data-stu-id="3269f-151">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span></span>
- <span data-ttu-id="3269f-152">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span><span class="sxs-lookup"><span data-stu-id="3269f-152">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span></span>
- [<span data-ttu-id="3269f-153">Start-Process</span><span class="sxs-lookup"><span data-stu-id="3269f-153">Start-Process</span></span>](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [<span data-ttu-id="3269f-154">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="3269f-154">Wait-Process</span></span>](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [<span data-ttu-id="3269f-155">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="3269f-155">Debug-Process</span></span>](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [<span data-ttu-id="3269f-156">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="3269f-156">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)

