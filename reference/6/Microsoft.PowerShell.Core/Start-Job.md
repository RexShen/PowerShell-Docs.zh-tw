---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 69cebe735e413b226bd40539df075bf3a49bce95
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204868"
---
# <span data-ttu-id="b0e03-103">Start-Job</span><span class="sxs-lookup"><span data-stu-id="b0e03-103">Start-Job</span></span>

## <span data-ttu-id="b0e03-104">概要</span><span class="sxs-lookup"><span data-stu-id="b0e03-104">SYNOPSIS</span></span>
<span data-ttu-id="b0e03-105">啟動 PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="b0e03-105">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="b0e03-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b0e03-106">SYNTAX</span></span>

### <span data-ttu-id="b0e03-107">ComputerName (預設值)</span><span class="sxs-lookup"><span data-stu-id="b0e03-107">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="b0e03-108">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="b0e03-108">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="b0e03-109">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="b0e03-109">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="b0e03-110">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="b0e03-110">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="b0e03-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b0e03-111">DESCRIPTION</span></span>

<span data-ttu-id="b0e03-112">`Start-Job`Cmdlet 會在本機電腦上啟動 PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="b0e03-112">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="b0e03-113">PowerShell 背景工作會執行命令，而不會與目前的會話互動。</span><span class="sxs-lookup"><span data-stu-id="b0e03-113">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="b0e03-114">當您啟動背景工作時，工作物件會立即傳回，即使作業需要花費很長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="b0e03-114">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="b0e03-115">工作執行時，您可以在工作階段中繼續工作，而不需中斷。</span><span class="sxs-lookup"><span data-stu-id="b0e03-115">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="b0e03-116">工作物件包含工作的相關實用資訊，但是不包含工作結果。</span><span class="sxs-lookup"><span data-stu-id="b0e03-116">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="b0e03-117">當作業完成時，請使用 `Receive-Job` Cmdlet 來取得作業的結果。</span><span class="sxs-lookup"><span data-stu-id="b0e03-117">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="b0e03-118">如需背景工作的詳細資訊，請參閱 [about_Jobs](./About/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="b0e03-118">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="b0e03-119">若要在遠端電腦上執行背景工作，請使用可在許多 Cmdlet 上使用的 **AsJob** 參數，或使用 `Invoke-Command` Cmdlet 在 `Start-Job` 遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="b0e03-119">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="b0e03-120">如需詳細資訊，請參閱 [about_Remote_Jobs](./About/about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="b0e03-120">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="b0e03-121">從 PowerShell 3.0 開始， `Start-Job` 可以啟動自訂工作類型的實例，例如排程工作。</span><span class="sxs-lookup"><span data-stu-id="b0e03-121">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="b0e03-122">如需如何使用 `Start-Job` 以自訂類型啟動作業的詳細資訊，請參閱工作類型功能的說明文件。</span><span class="sxs-lookup"><span data-stu-id="b0e03-122">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="b0e03-123">從 PowerShell 6.0 開始，您可以使用連字號 (`&`) 背景運算子來啟動作業。</span><span class="sxs-lookup"><span data-stu-id="b0e03-123">Beginning in PowerShell 6.0, you can start jobs using the ampersand (`&`) background operator.</span></span> <span data-ttu-id="b0e03-124">背景運算子的功能類似于 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-124">The functionality of the background operator is similar to `Start-Job`.</span></span> <span data-ttu-id="b0e03-125">這兩種啟動作業的方法都會建立 **PSRemotingJob** 工作物件。</span><span class="sxs-lookup"><span data-stu-id="b0e03-125">Both methods to start a job create a **PSRemotingJob** job object.</span></span> <span data-ttu-id="b0e03-126">如需使用連字號 () 的詳細資訊 `&` ，請參閱 [about_Operators](./about/about_operators.md#background-operator-)。</span><span class="sxs-lookup"><span data-stu-id="b0e03-126">For more information about using the ampersand (`&`), see [about_Operators](./about/about_operators.md#background-operator-).</span></span>

<span data-ttu-id="b0e03-127">工作的預設工作目錄會進行硬式編碼。</span><span class="sxs-lookup"><span data-stu-id="b0e03-127">The default working directory for jobs is hardcoded.</span></span> <span data-ttu-id="b0e03-128">Windows 預設值為 `$HOME\Documents` ，而 Linux 或 macOS 上的預設值為 `$HOME` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-128">The Windows default is `$HOME\Documents` and on Linux or macOS the default is `$HOME`.</span></span> <span data-ttu-id="b0e03-129">在背景工作中執行的腳本程式碼需要視需要管理工作目錄。</span><span class="sxs-lookup"><span data-stu-id="b0e03-129">The script code running in the background job needs to manage the working directory as needed.</span></span>

> [!NOTE]
> <span data-ttu-id="b0e03-130">`Start-Job`在 powershell 裝載于其他應用程式（例如 powershell Azure Functions）的案例中，不支援使用建立跨進程背景工作。</span><span class="sxs-lookup"><span data-stu-id="b0e03-130">Creating an out-of-process background job with `Start-Job` is not supported in the scenario where PowerShell is being hosted in other applications, such as the PowerShell Azure Functions.</span></span>
>
> <span data-ttu-id="b0e03-131">這是設計的原因 `Start-Job` ，取決於 `pwsh` 在下可執行檔可執行檔 `$PSHOME` 背景工作，但是當應用程式裝載 powershell 時，它會直接使用 powershell NuGet SDK 套件，且不會隨之出 `pwsh` 貨。</span><span class="sxs-lookup"><span data-stu-id="b0e03-131">This is by design because `Start-Job` depends on the `pwsh` executable to be available under `$PSHOME` to start an out-of-process background job, but when an application is hosting PowerShell, it's directly using the PowerShell NuGet SDK packages and won't have `pwsh` shipped along.</span></span>
>
> <span data-ttu-id="b0e03-132">此案例中的替代方式是 `Start-ThreadJob` 從模組 **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)** 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-132">The substitute in that scenario is `Start-ThreadJob` from the module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)** .</span></span>

## <span data-ttu-id="b0e03-133">範例</span><span class="sxs-lookup"><span data-stu-id="b0e03-133">EXAMPLES</span></span>

### <span data-ttu-id="b0e03-134">範例1：啟動背景工作</span><span class="sxs-lookup"><span data-stu-id="b0e03-134">Example 1: Start a background job</span></span>

<span data-ttu-id="b0e03-135">此範例會啟動在本機電腦上執行的背景工作。</span><span class="sxs-lookup"><span data-stu-id="b0e03-135">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name pwsh }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name pwsh
```

<span data-ttu-id="b0e03-136">`Start-Job` 使用 **ScriptBlock** 參數，以 `Get-Process` 背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="b0e03-136">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="b0e03-137">**Name** 參數指定尋找 PowerShell 處理常式 `pwsh` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-137">The **Name** parameter specifies to find PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="b0e03-138">當工作在背景中執行時，會顯示工作資訊，並將 PowerShell 返回提示。</span><span class="sxs-lookup"><span data-stu-id="b0e03-138">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="b0e03-139">若要查看作業的輸出，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b0e03-139">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="b0e03-140">例如： `Receive-Job -Id 1` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-140">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="b0e03-141">範例2：使用背景運算子來啟動背景工作</span><span class="sxs-lookup"><span data-stu-id="b0e03-141">Example 2: Use the background operator to start a background job</span></span>

<span data-ttu-id="b0e03-142">這個範例會使用連字號 (`&`) 背景運算子，在本機電腦上啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="b0e03-142">This example uses the ampersand (`&`) background operator to start a background job on the local computer.</span></span> <span data-ttu-id="b0e03-143">作業取得的結果與 `Start-Job` 範例1相同。</span><span class="sxs-lookup"><span data-stu-id="b0e03-143">The job gets the same result as `Start-Job` in Example 1.</span></span>

```powershell
Get-Process -Name pwsh &
```

```Output
Id    Name   PSJobTypeName   State       HasMoreData     Location      Command
--    ----   -------------   -----       -----------     --------      -------
5     Job5   BackgroundJob   Running     True            localhost     Microsoft.PowerShell.Man...
```

<span data-ttu-id="b0e03-144">`Get-Process` 使用 **Name** 參數來指定 PowerShell 處理常式 `pwsh` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-144">`Get-Process` uses the **Name** parameter to specify PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="b0e03-145">& 符號 (`&`) 會以背景工作的方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="b0e03-145">The ampersand (`&`) runs the command as a background job.</span></span> <span data-ttu-id="b0e03-146">當工作在背景中執行時，會顯示工作資訊，並將 PowerShell 返回提示。</span><span class="sxs-lookup"><span data-stu-id="b0e03-146">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="b0e03-147">若要查看作業的輸出，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b0e03-147">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="b0e03-148">例如： `Receive-Job -Id 5` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-148">For example, `Receive-Job -Id 5`.</span></span>

### <span data-ttu-id="b0e03-149">範例3：使用 Invoke-Command 啟動作業</span><span class="sxs-lookup"><span data-stu-id="b0e03-149">Example 3: Start a job using Invoke-Command</span></span>

<span data-ttu-id="b0e03-150">此範例會在多部電腦上執行工作。</span><span class="sxs-lookup"><span data-stu-id="b0e03-150">This example runs a job on multiple computers.</span></span> <span data-ttu-id="b0e03-151">作業會儲存在變數中，並使用 PowerShell 命令列上的變數名稱來執行。</span><span class="sxs-lookup"><span data-stu-id="b0e03-151">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="b0e03-152">使用的作業 `Invoke-Command` 會建立並儲存在變數中 `$jobWRM` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-152">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="b0e03-153">`Invoke-Command` 使用 **ComputerName** 參數來指定執行作業的電腦。</span><span class="sxs-lookup"><span data-stu-id="b0e03-153">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="b0e03-154">`Get-Content` 從檔案取得伺服器名稱 `C:\Servers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-154">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="b0e03-155">**ScriptBlock** 參數指定可 `Get-Service` 取得 **WinRM** 服務的命令。</span><span class="sxs-lookup"><span data-stu-id="b0e03-155">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="b0e03-156">**JobName** 參數會指定作業的易記名稱，也就是 **WinRM** 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-156">The **JobName** parameter specifies a friendly name for the job, **WinRM** .</span></span> <span data-ttu-id="b0e03-157">**ThrottleLimit** 參數會將並行命令的數目限制為16。</span><span class="sxs-lookup"><span data-stu-id="b0e03-157">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="b0e03-158">**AsJob** 參數會啟動在伺服器上執行命令的背景工作。</span><span class="sxs-lookup"><span data-stu-id="b0e03-158">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="b0e03-159">範例4：取得作業資訊</span><span class="sxs-lookup"><span data-stu-id="b0e03-159">Example 4: Get job information</span></span>

<span data-ttu-id="b0e03-160">此範例會取得作業的相關資訊，並顯示在本機電腦上執行之已完成工作的結果。</span><span class="sxs-lookup"><span data-stu-id="b0e03-160">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

```powershell
$j = Start-Job -ScriptBlock { Get-WinEvent -Log System } -Credential Domain01\User01
$j | Select-Object -Property *
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-WinEvent -Log System
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : 27ce3fd9-40ed-488a-99e5-679cd91b9dd3
Id            : 18
Name          : Job18
ChildJobs     : {Job19}
PSBeginTime   : 8/8/2019 14:41:57
PSEndTime     : 8/8/2019 14:42:07
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

<span data-ttu-id="b0e03-161">`Start-Job` 使用 **ScriptBlock** 參數來執行命令，以指定 `Get-WinEvent` 要取得 **系統** 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b0e03-161">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="b0e03-162">**Credential** 參數指定具有在電腦上執行作業許可權的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="b0e03-162">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="b0e03-163">工作物件會儲存在變數中 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-163">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="b0e03-164">變數中的物件 `$j` 會向下傳送到管線 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-164">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="b0e03-165">**Property** 參數會指定星號 (`*`) 來顯示所有工作物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="b0e03-165">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="b0e03-166">範例5：以背景工作的形式執行腳本</span><span class="sxs-lookup"><span data-stu-id="b0e03-166">Example 5: Run a script as a background job</span></span>

<span data-ttu-id="b0e03-167">在此範例中，本機電腦上的腳本會以背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="b0e03-167">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="b0e03-168">`Start-Job` 使用 **FilePath** 參數來指定儲存在本機電腦上的腳本檔案。</span><span class="sxs-lookup"><span data-stu-id="b0e03-168">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="b0e03-169">範例6：使用背景工作取得處理常式</span><span class="sxs-lookup"><span data-stu-id="b0e03-169">Example 6: Get a process using a background job</span></span>

<span data-ttu-id="b0e03-170">這個範例會使用背景工作，依名稱取得指定的進程。</span><span class="sxs-lookup"><span data-stu-id="b0e03-170">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="b0e03-171">`Start-Job` 使用 **Name** 參數來指定易記的作業名稱 **PShellJob** 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-171">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob** .</span></span> <span data-ttu-id="b0e03-172">**ScriptBlock** 參數指定 `Get-Process` 要取得名稱為 **PowerShell** 的進程。</span><span class="sxs-lookup"><span data-stu-id="b0e03-172">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell** .</span></span>

### <span data-ttu-id="b0e03-173">範例7：使用背景工作來收集和儲存資料</span><span class="sxs-lookup"><span data-stu-id="b0e03-173">Example 7: Collect and save data by using a background job</span></span>

<span data-ttu-id="b0e03-174">此範例會啟動一個作業來收集大量的地圖資料，然後將它儲存在檔案中 `.tif` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-174">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif } -RunAs32
```

<span data-ttu-id="b0e03-175">`Start-Job` 使用 **Name** 參數來指定易記的作業名稱 **GetMappingFiles** 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-175">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles** .</span></span> <span data-ttu-id="b0e03-176">**InitializationScript** 參數會執行匯入 **MapFunctions** 模組的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="b0e03-176">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="b0e03-177">**ScriptBlock** 參數會執行 `Get-Map` ，並將 `Set-Content` 資料儲存在 **Path** 參數所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="b0e03-177">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="b0e03-178">**RunAs32** 參數會以32位的形式執行程式，即使是在64位的作業系統上也一樣。</span><span class="sxs-lookup"><span data-stu-id="b0e03-178">The **RunAs32** parameter runs the process as 32-bit, even on a 64-bit operating system.</span></span>

### <span data-ttu-id="b0e03-179">範例8：將輸入傳遞給背景工作</span><span class="sxs-lookup"><span data-stu-id="b0e03-179">Example 8: Pass input to a background job</span></span>

<span data-ttu-id="b0e03-180">這個範例會使用 `$input` 自動變數來處理輸入物件。</span><span class="sxs-lookup"><span data-stu-id="b0e03-180">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="b0e03-181">用 `Receive-Job` 來查看作業的輸出。</span><span class="sxs-lookup"><span data-stu-id="b0e03-181">Use `Receive-Job` to view the job's output.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Content $input } -InputObject "C:\Servers.txt"
Receive-Job -Name Job45 -Keep
```

```Output
Server01
Server02
Server03
Server04
```

<span data-ttu-id="b0e03-182">`Start-Job` 使用 **ScriptBlock** 參數搭配 `Get-Content` `$input` 自動變數執行。</span><span class="sxs-lookup"><span data-stu-id="b0e03-182">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="b0e03-183">`$input`變數會從 **InputObject** 參數取得物件。</span><span class="sxs-lookup"><span data-stu-id="b0e03-183">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="b0e03-184">`Receive-Job` 使用 **Name** 參數來指定作業並輸出結果。</span><span class="sxs-lookup"><span data-stu-id="b0e03-184">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="b0e03-185">**Keep** 參數會儲存工作輸出，以便在 PowerShell 會話期間再次查看。</span><span class="sxs-lookup"><span data-stu-id="b0e03-185">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="b0e03-186">範例9：使用 ArgumentList 參數來指定陣列</span><span class="sxs-lookup"><span data-stu-id="b0e03-186">Example 9: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="b0e03-187">此範例使用 **ArgumentList** 參數來指定引數陣列。</span><span class="sxs-lookup"><span data-stu-id="b0e03-187">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="b0e03-188">陣列是以逗號分隔的進程名稱清單。</span><span class="sxs-lookup"><span data-stu-id="b0e03-188">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="b0e03-189">此 `Start-Job` Cmdlet 會使用 **ScriptBlock** 參數來執行命令。</span><span class="sxs-lookup"><span data-stu-id="b0e03-189">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="b0e03-190">`Get-Process` 使用 **Name** 參數來指定自動變數 `$args` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-190">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="b0e03-191">**ArgumentList** 參數會將處理常式名稱的陣列傳遞至 `$args` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-191">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="b0e03-192">程式會將 powershell、pwsh 和 notepad 等程式命名為在本機電腦上執行的處理常式。</span><span class="sxs-lookup"><span data-stu-id="b0e03-192">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="b0e03-193">若要查看作業的輸出，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b0e03-193">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="b0e03-194">例如： `Receive-Job -Id 1` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-194">For example, `Receive-Job -Id 1`.</span></span>

## <span data-ttu-id="b0e03-195">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b0e03-195">PARAMETERS</span></span>

### <span data-ttu-id="b0e03-196">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="b0e03-196">-ArgumentList</span></span>

<span data-ttu-id="b0e03-197">針對 **FilePath** 參數所指定的腳本或使用 **ScriptBlock** 參數指定的命令，指定引數或參數值的陣列。</span><span class="sxs-lookup"><span data-stu-id="b0e03-197">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="b0e03-198">引數必須以單一維度陣列引數的形式傳遞至 **ArgumentList** 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-198">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="b0e03-199">例如，以逗號分隔的清單。</span><span class="sxs-lookup"><span data-stu-id="b0e03-199">For example, a comma-separated list.</span></span> <span data-ttu-id="b0e03-200">如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="b0e03-200">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-201">-Authentication</span><span class="sxs-lookup"><span data-stu-id="b0e03-201">-Authentication</span></span>

<span data-ttu-id="b0e03-202">指定用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="b0e03-202">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="b0e03-203">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="b0e03-203">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b0e03-204">預設</span><span class="sxs-lookup"><span data-stu-id="b0e03-204">Default</span></span>
- <span data-ttu-id="b0e03-205">基本</span><span class="sxs-lookup"><span data-stu-id="b0e03-205">Basic</span></span>
- <span data-ttu-id="b0e03-206">Credssp</span><span class="sxs-lookup"><span data-stu-id="b0e03-206">Credssp</span></span>
- <span data-ttu-id="b0e03-207">Digest</span><span class="sxs-lookup"><span data-stu-id="b0e03-207">Digest</span></span>
- <span data-ttu-id="b0e03-208">Kerberos</span><span class="sxs-lookup"><span data-stu-id="b0e03-208">Kerberos</span></span>
- <span data-ttu-id="b0e03-209">交涉</span><span class="sxs-lookup"><span data-stu-id="b0e03-209">Negotiate</span></span>
- <span data-ttu-id="b0e03-210">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="b0e03-210">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="b0e03-211">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="b0e03-211">The default value is Default.</span></span>

<span data-ttu-id="b0e03-212">CredSSP 驗證僅適用于 Windows Vista、Windows Server 2008 和更新版本的 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="b0e03-212">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="b0e03-213">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="b0e03-213">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="b0e03-214">使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="b0e03-214">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="b0e03-215">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="b0e03-215">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="b0e03-216">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="b0e03-216">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-217">-Credential</span><span class="sxs-lookup"><span data-stu-id="b0e03-217">-Credential</span></span>

<span data-ttu-id="b0e03-218">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="b0e03-218">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="b0e03-219">如果未指定 **Credential** 參數，此命令會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="b0e03-219">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="b0e03-220">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-220">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="b0e03-221">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="b0e03-221">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="b0e03-222">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="b0e03-222">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="b0e03-223">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="b0e03-223">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-224">-DefinitionName</span><span class="sxs-lookup"><span data-stu-id="b0e03-224">-DefinitionName</span></span>

<span data-ttu-id="b0e03-225">指定此 Cmdlet 啟動之作業的定義名稱。</span><span class="sxs-lookup"><span data-stu-id="b0e03-225">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="b0e03-226">使用這個參數來啟動具有定義名稱的自訂工作類型，例如已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="b0e03-226">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="b0e03-227">當您使用 `Start-Job` 來啟動排程工作的實例時，該作業會立即啟動，不論工作觸發程式或工作選項為何。</span><span class="sxs-lookup"><span data-stu-id="b0e03-227">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="b0e03-228">產生的工作實例是已排程的工作，但不會儲存到磁片，例如觸發的排程工作。</span><span class="sxs-lookup"><span data-stu-id="b0e03-228">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="b0e03-229">您無法使用的 **ArgumentList** 參數 `Start-Job` 來提供在排程工作中執行的腳本參數值。</span><span class="sxs-lookup"><span data-stu-id="b0e03-229">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span>

<span data-ttu-id="b0e03-230">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b0e03-230">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-231">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="b0e03-231">-DefinitionPath</span></span>

<span data-ttu-id="b0e03-232">指定此 Cmdlet 啟動之作業的定義路徑。</span><span class="sxs-lookup"><span data-stu-id="b0e03-232">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="b0e03-233">輸入定義路徑。</span><span class="sxs-lookup"><span data-stu-id="b0e03-233">Enter the definition path.</span></span> <span data-ttu-id="b0e03-234">**DefinitionPath** 和 **DefinitionName** 參數的值串連是作業定義的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b0e03-234">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="b0e03-235">使用這個參數來啟動具有定義路徑的自訂工作類型，例如已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="b0e03-235">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="b0e03-236">針對排程工作， **DefinitionPath** 參數的值為 `$home\AppData\Local\Windows\PowerShell\ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-236">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="b0e03-237">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b0e03-237">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-238">-FilePath</span><span class="sxs-lookup"><span data-stu-id="b0e03-238">-FilePath</span></span>

<span data-ttu-id="b0e03-239">指定以 `Start-Job` 背景工作方式執行的本機腳本。</span><span class="sxs-lookup"><span data-stu-id="b0e03-239">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="b0e03-240">輸入腳本的路徑和檔案名，或使用管線將腳本路徑傳送至 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-240">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="b0e03-241">腳本必須位於本機電腦或本機電腦可以存取的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b0e03-241">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="b0e03-242">當您使用此參數時，PowerShell 會將指定之指令檔的內容轉換為腳本區塊，並以背景工作的形式執行腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="b0e03-242">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-243">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="b0e03-243">-InitializationScript</span></span>

<span data-ttu-id="b0e03-244">指定要在工作開始之前執行的命令。</span><span class="sxs-lookup"><span data-stu-id="b0e03-244">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="b0e03-245">若要建立腳本區塊，請以大括弧括住命令 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-245">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="b0e03-246">使用這個參數來準備執行工作的工作階段。</span><span class="sxs-lookup"><span data-stu-id="b0e03-246">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="b0e03-247">例如，您可以使用它來新增函式、嵌入式管理單元和模組到工作階段。</span><span class="sxs-lookup"><span data-stu-id="b0e03-247">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-248">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b0e03-248">-InputObject</span></span>

<span data-ttu-id="b0e03-249">指定命令的輸入。</span><span class="sxs-lookup"><span data-stu-id="b0e03-249">Specifies input to the command.</span></span> <span data-ttu-id="b0e03-250">輸入包含物件的變數，或輸入可產生物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="b0e03-250">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="b0e03-251">在 **ScriptBlock** 參數的值中，使用 `$input` 自動變數來代表輸入物件。</span><span class="sxs-lookup"><span data-stu-id="b0e03-251">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-252">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b0e03-252">-LiteralPath</span></span>

<span data-ttu-id="b0e03-253">指定此 Cmdlet 以背景工作方式執行的本機腳本。</span><span class="sxs-lookup"><span data-stu-id="b0e03-253">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="b0e03-254">輸入本機電腦上腳本的路徑。</span><span class="sxs-lookup"><span data-stu-id="b0e03-254">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="b0e03-255">`Start-Job` 使用 **LiteralPath** 參數的值，與其輸入的完全相同。</span><span class="sxs-lookup"><span data-stu-id="b0e03-255">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="b0e03-256">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b0e03-256">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="b0e03-257">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="b0e03-257">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b0e03-258">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="b0e03-258">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-259">-Name</span><span class="sxs-lookup"><span data-stu-id="b0e03-259">-Name</span></span>

<span data-ttu-id="b0e03-260">指定新工作的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="b0e03-260">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="b0e03-261">您可以使用此名稱來識別其他工作 Cmdlet 的作業，例如 `Stop-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b0e03-261">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="b0e03-262">預設的易記名稱是 `Job#` ，其中 `#` 是每個作業的遞增序號。</span><span class="sxs-lookup"><span data-stu-id="b0e03-262">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-263">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="b0e03-263">-PSVersion</span></span>

<span data-ttu-id="b0e03-264">指定版本。</span><span class="sxs-lookup"><span data-stu-id="b0e03-264">Specifies a version.</span></span> <span data-ttu-id="b0e03-265">`Start-Job` 使用 PowerShell 版本執行作業。</span><span class="sxs-lookup"><span data-stu-id="b0e03-265">`Start-Job` runs the job with the version of PowerShell.</span></span> <span data-ttu-id="b0e03-266">此參數可接受的值包括： `2.0` 和 `3.0` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-266">The acceptable values for this parameter are: `2.0` and `3.0`.</span></span>

<span data-ttu-id="b0e03-267">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b0e03-267">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-268">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="b0e03-268">-RunAs32</span></span>

<span data-ttu-id="b0e03-269">表示 `Start-Job` 在32位進程中執行作業。</span><span class="sxs-lookup"><span data-stu-id="b0e03-269">Indicates that `Start-Job` runs the job in a 32-bit process.</span></span> <span data-ttu-id="b0e03-270">**RunAs32** 會強制工作在32位的進程中執行，即使是在64位的作業系統上也一樣。</span><span class="sxs-lookup"><span data-stu-id="b0e03-270">**RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="b0e03-271">在64位版本的 Windows 7 和 Windows Server 2008 R2 上，當 `Start-Job` 命令包含 **RunAs32** 參數時，您不能使用 **Credential** 參數來指定其他使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="b0e03-271">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-272">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="b0e03-272">-ScriptBlock</span></span>

<span data-ttu-id="b0e03-273">指定要在背景工作執行的命令。</span><span class="sxs-lookup"><span data-stu-id="b0e03-273">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="b0e03-274">若要建立腳本區塊，請以大括弧括住命令 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-274">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="b0e03-275">使用 `$input` 自動變數來存取 **InputObject** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="b0e03-275">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="b0e03-276">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="b0e03-276">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-277">-Type</span><span class="sxs-lookup"><span data-stu-id="b0e03-277">-Type</span></span>

<span data-ttu-id="b0e03-278">指定所啟動之工作的自訂類型 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-278">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="b0e03-279">輸入自訂工作類型名稱，例如，已排程工作的 PSScheduledJob 或工作流程工作的 PSWorkflowJob。</span><span class="sxs-lookup"><span data-stu-id="b0e03-279">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="b0e03-280">此參數對於標準背景工作無效。</span><span class="sxs-lookup"><span data-stu-id="b0e03-280">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="b0e03-281">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b0e03-281">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b0e03-282">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b0e03-282">CommonParameters</span></span>

<span data-ttu-id="b0e03-283">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b0e03-283">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b0e03-284">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b0e03-284">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b0e03-285">輸入</span><span class="sxs-lookup"><span data-stu-id="b0e03-285">INPUTS</span></span>

### <span data-ttu-id="b0e03-286">System.String</span><span class="sxs-lookup"><span data-stu-id="b0e03-286">System.String</span></span>

<span data-ttu-id="b0e03-287">您可以使用管線將含有 **name** 屬性的物件傳送至 **name** 參數。</span><span class="sxs-lookup"><span data-stu-id="b0e03-287">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="b0e03-288">例如，您可以將 **FileInfo** 物件從管線 `Get-ChildItem` 到 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="b0e03-288">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="b0e03-289">輸出</span><span class="sxs-lookup"><span data-stu-id="b0e03-289">OUTPUTS</span></span>

### <span data-ttu-id="b0e03-290">System.Management.Automation.PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="b0e03-290">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="b0e03-291">`Start-Job` 傳回代表其啟動作業的 **PSRemotingJob** 物件。</span><span class="sxs-lookup"><span data-stu-id="b0e03-291">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="b0e03-292">注意</span><span class="sxs-lookup"><span data-stu-id="b0e03-292">NOTES</span></span>

<span data-ttu-id="b0e03-293">若要在背景中執行，請在 `Start-Job` 目前會話中自己的會話中執行。</span><span class="sxs-lookup"><span data-stu-id="b0e03-293">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="b0e03-294">當您使用 `Invoke-Command` Cmdlet 在 `Start-Job` 遠端電腦的會話中執行命令時，會 `Start-Job` 在遠端會話的會話中執行。</span><span class="sxs-lookup"><span data-stu-id="b0e03-294">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="b0e03-295">相關連結</span><span class="sxs-lookup"><span data-stu-id="b0e03-295">RELATED LINKS</span></span>

[<span data-ttu-id="b0e03-296">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="b0e03-296">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="b0e03-297">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="b0e03-297">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="b0e03-298">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="b0e03-298">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="b0e03-299">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="b0e03-299">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="b0e03-300">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="b0e03-300">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="b0e03-301">Get-Job</span><span class="sxs-lookup"><span data-stu-id="b0e03-301">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="b0e03-302">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="b0e03-302">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="b0e03-303">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="b0e03-303">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="b0e03-304">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="b0e03-304">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="b0e03-305">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="b0e03-305">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="b0e03-306">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="b0e03-306">Wait-Job</span></span>](Wait-Job.md)
