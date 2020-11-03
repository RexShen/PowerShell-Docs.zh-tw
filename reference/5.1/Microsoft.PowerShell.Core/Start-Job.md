---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 116e007cc28a91e3c97fd980cc27461932390b7c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202655"
---
# <span data-ttu-id="53949-103">Start-Job</span><span class="sxs-lookup"><span data-stu-id="53949-103">Start-Job</span></span>

## <span data-ttu-id="53949-104">概要</span><span class="sxs-lookup"><span data-stu-id="53949-104">SYNOPSIS</span></span>
<span data-ttu-id="53949-105">啟動 PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="53949-105">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="53949-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="53949-106">SYNTAX</span></span>

### <span data-ttu-id="53949-107">ComputerName (預設值)</span><span class="sxs-lookup"><span data-stu-id="53949-107">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="53949-108">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="53949-108">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="53949-109">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="53949-109">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="53949-110">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="53949-110">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="53949-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="53949-111">DESCRIPTION</span></span>

<span data-ttu-id="53949-112">`Start-Job`Cmdlet 會在本機電腦上啟動 PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="53949-112">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="53949-113">PowerShell 背景工作會執行命令，而不會與目前的會話互動。</span><span class="sxs-lookup"><span data-stu-id="53949-113">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="53949-114">當您啟動背景工作時，工作物件會立即傳回，即使作業需要花費很長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="53949-114">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="53949-115">工作執行時，您可以在工作階段中繼續工作，而不需中斷。</span><span class="sxs-lookup"><span data-stu-id="53949-115">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="53949-116">工作物件包含工作的相關實用資訊，但是不包含工作結果。</span><span class="sxs-lookup"><span data-stu-id="53949-116">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="53949-117">當作業完成時，請使用 `Receive-Job` Cmdlet 來取得作業的結果。</span><span class="sxs-lookup"><span data-stu-id="53949-117">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="53949-118">如需背景工作的詳細資訊，請參閱 [about_Jobs](./About/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="53949-118">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="53949-119">若要在遠端電腦上執行背景工作，請使用可在許多 Cmdlet 上使用的 **AsJob** 參數，或使用 `Invoke-Command` Cmdlet 在 `Start-Job` 遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="53949-119">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="53949-120">如需詳細資訊，請參閱 [about_Remote_Jobs](./About/about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="53949-120">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="53949-121">從 PowerShell 3.0 開始， `Start-Job` 可以啟動自訂工作類型的實例，例如排程工作。</span><span class="sxs-lookup"><span data-stu-id="53949-121">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="53949-122">如需如何使用 `Start-Job` 以自訂類型啟動作業的詳細資訊，請參閱工作類型功能的說明文件。</span><span class="sxs-lookup"><span data-stu-id="53949-122">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="53949-123">工作的預設工作目錄會進行硬式編碼。</span><span class="sxs-lookup"><span data-stu-id="53949-123">The default working directory for jobs is hardcoded.</span></span> <span data-ttu-id="53949-124">Windows 預設值為 `$HOME\Documents` ，而 Linux 或 macOS 上的預設值為 `$HOME` 。</span><span class="sxs-lookup"><span data-stu-id="53949-124">The Windows default is `$HOME\Documents` and on Linux or macOS the default is `$HOME`.</span></span> <span data-ttu-id="53949-125">在背景工作中執行的腳本程式碼需要視需要管理工作目錄。</span><span class="sxs-lookup"><span data-stu-id="53949-125">The script code running in the background job needs to manage the working directory as needed.</span></span>

## <span data-ttu-id="53949-126">範例</span><span class="sxs-lookup"><span data-stu-id="53949-126">EXAMPLES</span></span>

### <span data-ttu-id="53949-127">範例1：啟動背景工作</span><span class="sxs-lookup"><span data-stu-id="53949-127">Example 1: Start a background job</span></span>

<span data-ttu-id="53949-128">此範例會啟動在本機電腦上執行的背景工作。</span><span class="sxs-lookup"><span data-stu-id="53949-128">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name powershell }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name powershell
```

<span data-ttu-id="53949-129">`Start-Job` 使用 **ScriptBlock** 參數，以 `Get-Process` 背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="53949-129">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="53949-130">**Name** 參數指定尋找 PowerShell 處理常式 `powershell` 。</span><span class="sxs-lookup"><span data-stu-id="53949-130">The **Name** parameter specifies to find PowerShell processes, `powershell`.</span></span> <span data-ttu-id="53949-131">當工作在背景中執行時，會顯示工作資訊，並將 PowerShell 返回提示。</span><span class="sxs-lookup"><span data-stu-id="53949-131">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="53949-132">若要查看作業的輸出，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53949-132">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="53949-133">例如： `Receive-Job -Id 1` 。</span><span class="sxs-lookup"><span data-stu-id="53949-133">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="53949-134">範例2：使用 Invoke-Command 啟動作業</span><span class="sxs-lookup"><span data-stu-id="53949-134">Example 2: Start a job using Invoke-Command</span></span>

<span data-ttu-id="53949-135">此範例會在多部電腦上執行工作。</span><span class="sxs-lookup"><span data-stu-id="53949-135">This example runs a job on multiple computers.</span></span> <span data-ttu-id="53949-136">作業會儲存在變數中，並使用 PowerShell 命令列上的變數名稱來執行。</span><span class="sxs-lookup"><span data-stu-id="53949-136">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="53949-137">使用的作業 `Invoke-Command` 會建立並儲存在變數中 `$jobWRM` 。</span><span class="sxs-lookup"><span data-stu-id="53949-137">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="53949-138">`Invoke-Command` 使用 **ComputerName** 參數來指定執行作業的電腦。</span><span class="sxs-lookup"><span data-stu-id="53949-138">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="53949-139">`Get-Content` 從檔案取得伺服器名稱 `C:\Servers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="53949-139">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="53949-140">**ScriptBlock** 參數指定可 `Get-Service` 取得 **WinRM** 服務的命令。</span><span class="sxs-lookup"><span data-stu-id="53949-140">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="53949-141">**JobName** 參數會指定作業的易記名稱，也就是 **WinRM** 。</span><span class="sxs-lookup"><span data-stu-id="53949-141">The **JobName** parameter specifies a friendly name for the job, **WinRM** .</span></span> <span data-ttu-id="53949-142">**ThrottleLimit** 參數會將並行命令的數目限制為16。</span><span class="sxs-lookup"><span data-stu-id="53949-142">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="53949-143">**AsJob** 參數會啟動在伺服器上執行命令的背景工作。</span><span class="sxs-lookup"><span data-stu-id="53949-143">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="53949-144">範例3：取得作業資訊</span><span class="sxs-lookup"><span data-stu-id="53949-144">Example 3: Get job information</span></span>

<span data-ttu-id="53949-145">此範例會取得作業的相關資訊，並顯示在本機電腦上執行之已完成工作的結果。</span><span class="sxs-lookup"><span data-stu-id="53949-145">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

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

<span data-ttu-id="53949-146">`Start-Job` 使用 **ScriptBlock** 參數來執行命令，以指定 `Get-WinEvent` 要取得 **系統** 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="53949-146">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="53949-147">**Credential** 參數指定具有在電腦上執行作業許可權的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="53949-147">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="53949-148">工作物件會儲存在變數中 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="53949-148">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="53949-149">變數中的物件 `$j` 會向下傳送到管線 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="53949-149">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="53949-150">**Property** 參數會指定星號 (`*`) 來顯示所有工作物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="53949-150">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="53949-151">範例4：以背景工作的形式執行腳本</span><span class="sxs-lookup"><span data-stu-id="53949-151">Example 4: Run a script as a background job</span></span>

<span data-ttu-id="53949-152">在此範例中，本機電腦上的腳本會以背景工作的形式執行。</span><span class="sxs-lookup"><span data-stu-id="53949-152">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="53949-153">`Start-Job` 使用 **FilePath** 參數來指定儲存在本機電腦上的腳本檔案。</span><span class="sxs-lookup"><span data-stu-id="53949-153">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="53949-154">範例5：使用背景工作取得處理常式</span><span class="sxs-lookup"><span data-stu-id="53949-154">Example 5: Get a process using a background job</span></span>

<span data-ttu-id="53949-155">這個範例會使用背景工作，依名稱取得指定的進程。</span><span class="sxs-lookup"><span data-stu-id="53949-155">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="53949-156">`Start-Job` 使用 **Name** 參數來指定易記的作業名稱 **PShellJob** 。</span><span class="sxs-lookup"><span data-stu-id="53949-156">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob** .</span></span> <span data-ttu-id="53949-157">**ScriptBlock** 參數指定 `Get-Process` 要取得名稱為 **PowerShell** 的進程。</span><span class="sxs-lookup"><span data-stu-id="53949-157">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell** .</span></span>

### <span data-ttu-id="53949-158">範例6：使用背景工作來收集和儲存資料</span><span class="sxs-lookup"><span data-stu-id="53949-158">Example 6: Collect and save data by using a background job</span></span>

<span data-ttu-id="53949-159">此範例會啟動一個作業來收集大量的地圖資料，然後將它儲存在檔案中 `.tif` 。</span><span class="sxs-lookup"><span data-stu-id="53949-159">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif } -RunAs32
```

<span data-ttu-id="53949-160">`Start-Job` 使用 **Name** 參數來指定易記的作業名稱 **GetMappingFiles** 。</span><span class="sxs-lookup"><span data-stu-id="53949-160">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles** .</span></span> <span data-ttu-id="53949-161">**InitializationScript** 參數會執行匯入 **MapFunctions** 模組的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="53949-161">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="53949-162">**ScriptBlock** 參數會執行 `Get-Map` ，並將 `Set-Content` 資料儲存在 **Path** 參數所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="53949-162">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="53949-163">**RunAs32** 參數會以32位的形式執行程式，即使是在64位的作業系統上也一樣。</span><span class="sxs-lookup"><span data-stu-id="53949-163">The **RunAs32** parameter runs the process as 32-bit, even on a 64-bit operating system.</span></span>

### <span data-ttu-id="53949-164">範例7：將輸入傳遞給背景工作</span><span class="sxs-lookup"><span data-stu-id="53949-164">Example 7: Pass input to a background job</span></span>

<span data-ttu-id="53949-165">這個範例會使用 `$input` 自動變數來處理輸入物件。</span><span class="sxs-lookup"><span data-stu-id="53949-165">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="53949-166">用 `Receive-Job` 來查看作業的輸出。</span><span class="sxs-lookup"><span data-stu-id="53949-166">Use `Receive-Job` to view the job's output.</span></span>

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

<span data-ttu-id="53949-167">`Start-Job` 使用 **ScriptBlock** 參數搭配 `Get-Content` `$input` 自動變數執行。</span><span class="sxs-lookup"><span data-stu-id="53949-167">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="53949-168">`$input`變數會從 **InputObject** 參數取得物件。</span><span class="sxs-lookup"><span data-stu-id="53949-168">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="53949-169">`Receive-Job` 使用 **Name** 參數來指定作業並輸出結果。</span><span class="sxs-lookup"><span data-stu-id="53949-169">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="53949-170">**Keep** 參數會儲存工作輸出，以便在 PowerShell 會話期間再次查看。</span><span class="sxs-lookup"><span data-stu-id="53949-170">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="53949-171">範例8：使用 ArgumentList 參數來指定陣列</span><span class="sxs-lookup"><span data-stu-id="53949-171">Example 8: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="53949-172">此範例使用 **ArgumentList** 參數來指定引數陣列。</span><span class="sxs-lookup"><span data-stu-id="53949-172">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="53949-173">陣列是以逗號分隔的進程名稱清單。</span><span class="sxs-lookup"><span data-stu-id="53949-173">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="53949-174">此 `Start-Job` Cmdlet 會使用 **ScriptBlock** 參數來執行命令。</span><span class="sxs-lookup"><span data-stu-id="53949-174">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="53949-175">`Get-Process` 使用 **Name** 參數來指定自動變數 `$args` 。</span><span class="sxs-lookup"><span data-stu-id="53949-175">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="53949-176">**ArgumentList** 參數會將處理常式名稱的陣列傳遞至 `$args` 。</span><span class="sxs-lookup"><span data-stu-id="53949-176">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="53949-177">程式會將 powershell、pwsh 和 notepad 等程式命名為在本機電腦上執行的處理常式。</span><span class="sxs-lookup"><span data-stu-id="53949-177">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="53949-178">若要查看作業的輸出，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53949-178">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="53949-179">例如： `Receive-Job -Id 1` 。</span><span class="sxs-lookup"><span data-stu-id="53949-179">For example, `Receive-Job -Id 1`.</span></span>

## <span data-ttu-id="53949-180">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="53949-180">PARAMETERS</span></span>

### <span data-ttu-id="53949-181">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="53949-181">-ArgumentList</span></span>

<span data-ttu-id="53949-182">針對 **FilePath** 參數所指定的腳本或使用 **ScriptBlock** 參數指定的命令，指定引數或參數值的陣列。</span><span class="sxs-lookup"><span data-stu-id="53949-182">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="53949-183">引數必須以單一維度陣列引數的形式傳遞至 **ArgumentList** 。</span><span class="sxs-lookup"><span data-stu-id="53949-183">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="53949-184">例如，以逗號分隔的清單。</span><span class="sxs-lookup"><span data-stu-id="53949-184">For example, a comma-separated list.</span></span> <span data-ttu-id="53949-185">如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="53949-185">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53949-186">-Authentication</span><span class="sxs-lookup"><span data-stu-id="53949-186">-Authentication</span></span>

<span data-ttu-id="53949-187">指定用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="53949-187">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="53949-188">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="53949-188">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="53949-189">預設</span><span class="sxs-lookup"><span data-stu-id="53949-189">Default</span></span>
- <span data-ttu-id="53949-190">基本</span><span class="sxs-lookup"><span data-stu-id="53949-190">Basic</span></span>
- <span data-ttu-id="53949-191">Credssp</span><span class="sxs-lookup"><span data-stu-id="53949-191">Credssp</span></span>
- <span data-ttu-id="53949-192">Digest</span><span class="sxs-lookup"><span data-stu-id="53949-192">Digest</span></span>
- <span data-ttu-id="53949-193">Kerberos</span><span class="sxs-lookup"><span data-stu-id="53949-193">Kerberos</span></span>
- <span data-ttu-id="53949-194">交涉</span><span class="sxs-lookup"><span data-stu-id="53949-194">Negotiate</span></span>
- <span data-ttu-id="53949-195">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="53949-195">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="53949-196">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="53949-196">The default value is Default.</span></span>

<span data-ttu-id="53949-197">CredSSP 驗證僅適用于 Windows Vista、Windows Server 2008 和更新版本的 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="53949-197">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="53949-198">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="53949-198">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="53949-199">使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="53949-199">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="53949-200">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="53949-200">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="53949-201">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="53949-201">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53949-202">-Credential</span><span class="sxs-lookup"><span data-stu-id="53949-202">-Credential</span></span>

<span data-ttu-id="53949-203">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="53949-203">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="53949-204">如果未指定 **Credential** 參數，此命令會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="53949-204">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="53949-205">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="53949-205">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="53949-206">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="53949-206">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="53949-207">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="53949-207">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="53949-208">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="53949-208">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53949-209">-DefinitionName</span><span class="sxs-lookup"><span data-stu-id="53949-209">-DefinitionName</span></span>

<span data-ttu-id="53949-210">指定此 Cmdlet 啟動之作業的定義名稱。</span><span class="sxs-lookup"><span data-stu-id="53949-210">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="53949-211">使用這個參數來啟動具有定義名稱的自訂工作類型，例如已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="53949-211">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="53949-212">當您使用 `Start-Job` 來啟動排程工作的實例時，該作業會立即啟動，不論工作觸發程式或工作選項為何。</span><span class="sxs-lookup"><span data-stu-id="53949-212">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="53949-213">產生的工作實例是已排程的工作，但不會儲存到磁片，例如觸發的排程工作。</span><span class="sxs-lookup"><span data-stu-id="53949-213">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="53949-214">您無法使用的 **ArgumentList** 參數 `Start-Job` 來提供在排程工作中執行的腳本參數值。</span><span class="sxs-lookup"><span data-stu-id="53949-214">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span> <span data-ttu-id="53949-215">如需詳細資訊，請參閱 [about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="53949-215">For more information, see [about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md).</span></span>

<span data-ttu-id="53949-216">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="53949-216">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53949-217">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="53949-217">-DefinitionPath</span></span>

<span data-ttu-id="53949-218">指定此 Cmdlet 啟動之作業的定義路徑。</span><span class="sxs-lookup"><span data-stu-id="53949-218">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="53949-219">輸入定義路徑。</span><span class="sxs-lookup"><span data-stu-id="53949-219">Enter the definition path.</span></span> <span data-ttu-id="53949-220">**DefinitionPath** 和 **DefinitionName** 參數的值串連是作業定義的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="53949-220">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="53949-221">使用這個參數來啟動具有定義路徑的自訂工作類型，例如已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="53949-221">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="53949-222">針對排程工作， **DefinitionPath** 參數的值為 `$home\AppData\Local\Windows\PowerShell\ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="53949-222">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="53949-223">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="53949-223">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53949-224">-FilePath</span><span class="sxs-lookup"><span data-stu-id="53949-224">-FilePath</span></span>

<span data-ttu-id="53949-225">指定以 `Start-Job` 背景工作方式執行的本機腳本。</span><span class="sxs-lookup"><span data-stu-id="53949-225">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="53949-226">輸入腳本的路徑和檔案名，或使用管線將腳本路徑傳送至 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="53949-226">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="53949-227">腳本必須位於本機電腦或本機電腦可以存取的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="53949-227">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="53949-228">當您使用此參數時，PowerShell 會將指定之指令檔的內容轉換為腳本區塊，並以背景工作的形式執行腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="53949-228">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

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

### <span data-ttu-id="53949-229">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="53949-229">-InitializationScript</span></span>

<span data-ttu-id="53949-230">指定要在工作開始之前執行的命令。</span><span class="sxs-lookup"><span data-stu-id="53949-230">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="53949-231">若要建立腳本區塊，請以大括弧括住命令 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="53949-231">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="53949-232">使用這個參數來準備執行工作的工作階段。</span><span class="sxs-lookup"><span data-stu-id="53949-232">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="53949-233">例如，您可以使用它來新增函式、嵌入式管理單元和模組到工作階段。</span><span class="sxs-lookup"><span data-stu-id="53949-233">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53949-234">-InputObject</span><span class="sxs-lookup"><span data-stu-id="53949-234">-InputObject</span></span>

<span data-ttu-id="53949-235">指定命令的輸入。</span><span class="sxs-lookup"><span data-stu-id="53949-235">Specifies input to the command.</span></span> <span data-ttu-id="53949-236">輸入包含物件的變數，或輸入可產生物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="53949-236">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="53949-237">在 **ScriptBlock** 參數的值中，使用 `$input` 自動變數來代表輸入物件。</span><span class="sxs-lookup"><span data-stu-id="53949-237">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="53949-238">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="53949-238">-LiteralPath</span></span>

<span data-ttu-id="53949-239">指定此 Cmdlet 以背景工作方式執行的本機腳本。</span><span class="sxs-lookup"><span data-stu-id="53949-239">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="53949-240">輸入本機電腦上腳本的路徑。</span><span class="sxs-lookup"><span data-stu-id="53949-240">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="53949-241">`Start-Job` 使用 **LiteralPath** 參數的值，與其輸入的完全相同。</span><span class="sxs-lookup"><span data-stu-id="53949-241">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="53949-242">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="53949-242">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="53949-243">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="53949-243">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="53949-244">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="53949-244">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53949-245">-Name</span><span class="sxs-lookup"><span data-stu-id="53949-245">-Name</span></span>

<span data-ttu-id="53949-246">指定新工作的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="53949-246">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="53949-247">您可以使用此名稱來識別其他工作 Cmdlet 的作業，例如 `Stop-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="53949-247">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="53949-248">預設的易記名稱是 `Job#` ，其中 `#` 是每個作業的遞增序號。</span><span class="sxs-lookup"><span data-stu-id="53949-248">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="53949-249">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="53949-249">-PSVersion</span></span>

<span data-ttu-id="53949-250">指定版本。</span><span class="sxs-lookup"><span data-stu-id="53949-250">Specifies a version.</span></span> <span data-ttu-id="53949-251">`Start-Job` 使用 PowerShell 版本執行作業。</span><span class="sxs-lookup"><span data-stu-id="53949-251">`Start-Job` runs the job with the version of PowerShell.</span></span> <span data-ttu-id="53949-252">此參數可接受的值包括： `2.0` 和 `3.0` 。</span><span class="sxs-lookup"><span data-stu-id="53949-252">The acceptable values for this parameter are: `2.0` and `3.0`.</span></span>

<span data-ttu-id="53949-253">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="53949-253">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53949-254">-RunAs32</span><span class="sxs-lookup"><span data-stu-id="53949-254">-RunAs32</span></span>

<span data-ttu-id="53949-255">表示 `Start-Job` 在32位進程中執行作業。</span><span class="sxs-lookup"><span data-stu-id="53949-255">Indicates that `Start-Job` runs the job in a 32-bit process.</span></span> <span data-ttu-id="53949-256">**RunAs32** 會強制工作在32位的進程中執行，即使是在64位的作業系統上也一樣。</span><span class="sxs-lookup"><span data-stu-id="53949-256">**RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="53949-257">在64位版本的 Windows 7 和 Windows Server 2008 R2 上，當 `Start-Job` 命令包含 **RunAs32** 參數時，您不能使用 **Credential** 參數來指定其他使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="53949-257">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53949-258">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="53949-258">-ScriptBlock</span></span>

<span data-ttu-id="53949-259">指定要在背景工作執行的命令。</span><span class="sxs-lookup"><span data-stu-id="53949-259">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="53949-260">若要建立腳本區塊，請以大括弧括住命令 (`{}`) 。</span><span class="sxs-lookup"><span data-stu-id="53949-260">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="53949-261">使用 `$input` 自動變數來存取 **InputObject** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="53949-261">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="53949-262">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="53949-262">This parameter is required.</span></span>

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

### <span data-ttu-id="53949-263">-Type</span><span class="sxs-lookup"><span data-stu-id="53949-263">-Type</span></span>

<span data-ttu-id="53949-264">指定所啟動之工作的自訂類型 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="53949-264">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="53949-265">輸入自訂工作類型名稱，例如，已排程工作的 PSScheduledJob 或工作流程工作的 PSWorkflowJob。</span><span class="sxs-lookup"><span data-stu-id="53949-265">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="53949-266">此參數對於標準背景工作無效。</span><span class="sxs-lookup"><span data-stu-id="53949-266">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="53949-267">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="53949-267">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53949-268">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="53949-268">CommonParameters</span></span>

<span data-ttu-id="53949-269">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="53949-269">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="53949-270">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="53949-270">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="53949-271">輸入</span><span class="sxs-lookup"><span data-stu-id="53949-271">INPUTS</span></span>

### <span data-ttu-id="53949-272">System.String</span><span class="sxs-lookup"><span data-stu-id="53949-272">System.String</span></span>

<span data-ttu-id="53949-273">您可以使用管線將含有 **name** 屬性的物件傳送至 **name** 參數。</span><span class="sxs-lookup"><span data-stu-id="53949-273">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="53949-274">例如，您可以將 **FileInfo** 物件從管線 `Get-ChildItem` 到 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="53949-274">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="53949-275">輸出</span><span class="sxs-lookup"><span data-stu-id="53949-275">OUTPUTS</span></span>

### <span data-ttu-id="53949-276">System.Management.Automation.PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="53949-276">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="53949-277">`Start-Job` 傳回代表其啟動作業的 **PSRemotingJob** 物件。</span><span class="sxs-lookup"><span data-stu-id="53949-277">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="53949-278">注意</span><span class="sxs-lookup"><span data-stu-id="53949-278">NOTES</span></span>

<span data-ttu-id="53949-279">若要在背景中執行，請在 `Start-Job` 目前會話中自己的會話中執行。</span><span class="sxs-lookup"><span data-stu-id="53949-279">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="53949-280">當您使用 `Invoke-Command` Cmdlet 在 `Start-Job` 遠端電腦的會話中執行命令時，會 `Start-Job` 在遠端會話的會話中執行。</span><span class="sxs-lookup"><span data-stu-id="53949-280">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="53949-281">相關連結</span><span class="sxs-lookup"><span data-stu-id="53949-281">RELATED LINKS</span></span>

[<span data-ttu-id="53949-282">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="53949-282">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="53949-283">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="53949-283">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="53949-284">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="53949-284">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="53949-285">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="53949-285">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="53949-286">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="53949-286">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="53949-287">Get-Job</span><span class="sxs-lookup"><span data-stu-id="53949-287">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="53949-288">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="53949-288">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="53949-289">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="53949-289">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="53949-290">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="53949-290">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="53949-291">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="53949-291">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="53949-292">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="53949-292">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="53949-293">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="53949-293">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="53949-294">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="53949-294">Wait-Job</span></span>](Wait-Job.md)
