---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 28fb50118e3a37aa0ee7b84aac356f7e8b6f2578
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387561"
---
# <span data-ttu-id="f72ec-103">Get-Job</span><span class="sxs-lookup"><span data-stu-id="f72ec-103">Get-Job</span></span>

## <span data-ttu-id="f72ec-104">概要</span><span class="sxs-lookup"><span data-stu-id="f72ec-104">SYNOPSIS</span></span>
<span data-ttu-id="f72ec-105">取得目前會話中正在執行的 PowerShell 背景工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-105">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="f72ec-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f72ec-106">SYNTAX</span></span>

### <span data-ttu-id="f72ec-107">SessionIdParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="f72ec-107">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="f72ec-108">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f72ec-108">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="f72ec-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="f72ec-109">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="f72ec-110">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="f72ec-110">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="f72ec-111">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="f72ec-111">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f72ec-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="f72ec-112">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="f72ec-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f72ec-113">DESCRIPTION</span></span>

<span data-ttu-id="f72ec-114">`Get-Job`Cmdlet 會取得物件，這些物件代表在目前會話中啟動的背景工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-114">The `Get-Job` cmdlet gets objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="f72ec-115">您可以使用 `Get-Job` 來取得使用 Cmdlet 啟動的作業 `Start-Job` ，或使用任何 Cmdlet 的 **AsJob** 參數。</span><span class="sxs-lookup"><span data-stu-id="f72ec-115">You can use `Get-Job` to get jobs that were started by using the `Start-Job` cmdlet, or by using the **AsJob** parameter of any cmdlet.</span></span>

<span data-ttu-id="f72ec-116">如果沒有參數， `Get-Job` 命令就會取得目前會話中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-116">Without parameters, a `Get-Job` command gets all jobs in the current session.</span></span> <span data-ttu-id="f72ec-117">您可以使用的參數 `Get-Job` 來取得特定工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-117">You can use the parameters of `Get-Job` to get particular jobs.</span></span>

<span data-ttu-id="f72ec-118">傳回的工作物件 `Get-Job` 包含工作的相關實用資訊，但是不包含工作結果。</span><span class="sxs-lookup"><span data-stu-id="f72ec-118">The job object that `Get-Job` returns contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="f72ec-119">若要取得結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f72ec-119">To get the results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="f72ec-120">Windows PowerShell 背景工作是在背景執行的命令，而不會與目前的會話互動。</span><span class="sxs-lookup"><span data-stu-id="f72ec-120">A Windows PowerShell background job is a command that runs in the background without interacting with the current session.</span></span> <span data-ttu-id="f72ec-121">一般而言，您會使用背景工作來執行複雜的命令，此命令需要很長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="f72ec-121">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span> <span data-ttu-id="f72ec-122">如需有關 Windows PowerShell 中背景工作的詳細資訊，請參閱 [about_Jobs](./about/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="f72ec-122">For more information about background jobs in Windows PowerShell, see [about_Jobs](./about/about_Jobs.md).</span></span>

<span data-ttu-id="f72ec-123">從 Windows PowerShell 3.0 開始，此 `Get-Job` Cmdlet 也會取得自訂工作類型，例如工作流程工作和排程工作的實例。</span><span class="sxs-lookup"><span data-stu-id="f72ec-123">Beginning in Windows PowerShell 3.0, the `Get-Job` cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="f72ec-124">若要尋找工作的工作類型，可使用工作的 **PSJobTypeName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="f72ec-124">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="f72ec-125">若要啟用 `Get-Job` 以取得自訂工作類型，請先將支援自訂工作類型的模組匯入到會話中 `Get-Job` ，再執行命令，方法是使用 `Import-Module` Cmdlet 或使用或取得模組中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f72ec-125">To enable `Get-Job` to get a custom job type, import the module that supports the custom job type into the session before you run a `Get-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="f72ec-126">如需有關特定自訂工作類型的資訊，請參閱自訂工作類型功能的文件。</span><span class="sxs-lookup"><span data-stu-id="f72ec-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="f72ec-127">範例</span><span class="sxs-lookup"><span data-stu-id="f72ec-127">EXAMPLES</span></span>

### <span data-ttu-id="f72ec-128">範例1：取得在目前會話中啟動的所有背景工作</span><span class="sxs-lookup"><span data-stu-id="f72ec-128">Example 1: Get all background jobs started in the current session</span></span>

<span data-ttu-id="f72ec-129">這個命令會取得目前工作階段中啟動的所有背景工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-129">This command gets all background jobs started in the current session.</span></span> <span data-ttu-id="f72ec-130">它不會包含在其他工作階段中建立的工作，即使這類工作是在本機電腦上執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="f72ec-130">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

```
PS C:\> Get-Job
```

### <span data-ttu-id="f72ec-131">範例2：使用實例識別碼停止作業</span><span class="sxs-lookup"><span data-stu-id="f72ec-131">Example 2: Stop a job by using an instance ID</span></span>

<span data-ttu-id="f72ec-132">這些命令示範如何取得工作的執行個體識別碼，然後使用它來停止工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-132">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span> <span data-ttu-id="f72ec-133">與工作名稱 (這不是唯一的) 不同，執行個體識別碼是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f72ec-133">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

<span data-ttu-id="f72ec-134">第一個命令會使用 `Get-Job` Cmdlet 來取得工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-134">The first command uses the `Get-Job` cmdlet to get a job.</span></span> <span data-ttu-id="f72ec-135">它會使用 **Name** 參數來識別工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-135">It uses the **Name** parameter to identify the job.</span></span> <span data-ttu-id="f72ec-136">此命令會儲存在變數中傳回的工作物件 `Get-Job` `$j` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-136">The command stores the job object that `Get-Job` returns in the `$j` variable.</span></span> <span data-ttu-id="f72ec-137">在這個範例中，只有一個具有指定名稱的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-137">In this example, there is only one job with the specified name.</span></span> <span data-ttu-id="f72ec-138">第二個命令會取得變數中物件的 **InstanceId** 屬性 `$j` ，並將它儲存在 `$ID` 變數中。</span><span class="sxs-lookup"><span data-stu-id="f72ec-138">The second command gets the **InstanceId** property of the object in the `$j` variable and stores it in the `$ID` variable.</span></span> <span data-ttu-id="f72ec-139">第三個命令會顯示變數的值 `$ID` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-139">The third command displays the value of the `$ID` variable.</span></span> <span data-ttu-id="f72ec-140">第四個命令會使用 `Stop-Job` Cmdlet 來停止工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-140">The fourth command uses `Stop-Job` cmdlet to stop the job.</span></span>
<span data-ttu-id="f72ec-141">它會使用 **InstanceId** 參數來識別工作和 `$ID` 變數，以代表工作的實例識別碼。</span><span class="sxs-lookup"><span data-stu-id="f72ec-141">It uses the **InstanceId** parameter to identify the job and `$ID` variable to represent the instance ID of the job.</span></span>

```
PS C:\> $j = Get-Job -Name Job1
PS C:\> $ID = $j.InstanceID
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

PS C:\> Stop-Job -InstanceId $ID
```

### <span data-ttu-id="f72ec-142">範例3：取得包含特定命令的工作</span><span class="sxs-lookup"><span data-stu-id="f72ec-142">Example 3: Get jobs that include a specific command</span></span>

<span data-ttu-id="f72ec-143">此命令會取得系統上包含命令的工作 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-143">This command gets the jobs on the system that include a `Get-Process` command.</span></span> <span data-ttu-id="f72ec-144">命令使用的 **命令** 參數 `Get-Job` 來限制抓取的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-144">The command uses the **Command** parameter of `Get-Job` to limit the jobs retrieved.</span></span> <span data-ttu-id="f72ec-145">命令使用萬用字元 (`*`) 來取得 `Get-Process` 命令字串中任何位置包含命令的作業。</span><span class="sxs-lookup"><span data-stu-id="f72ec-145">The command uses wildcard characters (`*`) to get jobs that include a `Get-Process` command anywhere in the command string.</span></span>

```
PS C:\> Get-Job -Command "*get-process*"
```

### <span data-ttu-id="f72ec-146">範例4：使用管線取得包含特定命令的作業</span><span class="sxs-lookup"><span data-stu-id="f72ec-146">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

<span data-ttu-id="f72ec-147">如同上一個範例中的命令，此命令會取得系統上包含命令的工作 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-147">Like the command in the previous example, this command gets the jobs on the system that include a `Get-Process` command.</span></span> <span data-ttu-id="f72ec-148">此命令會使用管線運算子 (`|`) 將字串（以引號括住）傳送至 `Get-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f72ec-148">The command uses a pipeline operator (`|`) to send a string, in quotation marks, to the `Get-Job` cmdlet.</span></span> <span data-ttu-id="f72ec-149">它等同於前一個命令。</span><span class="sxs-lookup"><span data-stu-id="f72ec-149">It is the equivalent of the previous command.</span></span>

```
PS C:\> "*get-process*" | Get-Job
```

### <span data-ttu-id="f72ec-150">範例5：取得尚未啟動的工作</span><span class="sxs-lookup"><span data-stu-id="f72ec-150">Example 5: Get jobs that have not been started</span></span>

<span data-ttu-id="f72ec-151">這個命令只會取得已建立但尚未啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-151">This command gets only those jobs that have been created but have not yet been started.</span></span> <span data-ttu-id="f72ec-152">這包括已排定在未來執行的工作以及尚未排程的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-152">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

```
PS C:\> Get-Job -State NotStarted
```

### <span data-ttu-id="f72ec-153">範例6：取得尚未指派名稱的工作</span><span class="sxs-lookup"><span data-stu-id="f72ec-153">Example 6: Get jobs that have not been assigned a name</span></span>

<span data-ttu-id="f72ec-154">此命令會取得工作名稱以 job 開頭的所有工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-154">This command gets all jobs that have job names that begin with job.</span></span> <span data-ttu-id="f72ec-155">由於 `job<number>` 是工作的預設名稱，因此，此命令會取得所有未明確指派名稱的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-155">Because `job<number>` is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

```
PS C:\> Get-Job -Name Job*
```

### <span data-ttu-id="f72ec-156">範例7：使用工作物件來代表命令中的工作</span><span class="sxs-lookup"><span data-stu-id="f72ec-156">Example 7: Use a job object to represent the job in a command</span></span>

<span data-ttu-id="f72ec-157">這個範例示範如何使用 `Get-Job` 來取得工作物件，然後示範如何使用工作物件來代表命令中的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-157">This example shows how to use `Get-Job` to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

<span data-ttu-id="f72ec-158">第一個命令會使用 `Start-Job` Cmdlet 來啟動在 `Get-Process` 本機電腦上執行命令的背景工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-158">The first command uses the `Start-Job` cmdlet to start a background job that runs a `Get-Process` command on the local computer.</span></span> <span data-ttu-id="f72ec-159">此命令會使用的 **Name** 參數 `Start-Job` 來指派工作的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="f72ec-159">The command uses the **Name** parameter of `Start-Job` to assign a friendly name to the job.</span></span> <span data-ttu-id="f72ec-160">第二個命令會使用 `Get-Job` 來取得工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-160">The second command uses `Get-Job` to get the job.</span></span> <span data-ttu-id="f72ec-161">它使用的 **Name** 參數 `Get-Job` 來識別工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-161">It uses the **Name** parameter of `Get-Job` to identify the job.</span></span> <span data-ttu-id="f72ec-162">此命令會將產生的工作物件儲存在 `$j` 變數中。</span><span class="sxs-lookup"><span data-stu-id="f72ec-162">The command saves the resulting job object in the `$j` variable.</span></span> <span data-ttu-id="f72ec-163">第三個命令顯示變數中工作物件的值 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-163">The third command displays the value of the job object in the `$j` variable.</span></span> <span data-ttu-id="f72ec-164">**State** 屬性的值顯示作業已完成。</span><span class="sxs-lookup"><span data-stu-id="f72ec-164">The value of the **State** property shows that the job is completed.</span></span> <span data-ttu-id="f72ec-165">**HasMoreData** 屬性的值顯示有來自尚未抓取之工作的可用結果。</span><span class="sxs-lookup"><span data-stu-id="f72ec-165">The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.</span></span> <span data-ttu-id="f72ec-166">第四個命令會使用 `Receive-Job` Cmdlet 來取得工作的結果。</span><span class="sxs-lookup"><span data-stu-id="f72ec-166">The fourth command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="f72ec-167">它會使用變數中的工作物件 `$j` 來表示作業。</span><span class="sxs-lookup"><span data-stu-id="f72ec-167">It uses the job object in the `$j` variable to represent the job.</span></span> <span data-ttu-id="f72ec-168">您也可以使用管線運算子將工作物件傳送至 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-168">You can also use a pipeline operator to send a job object to `Receive-Job`.</span></span>

```
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob
PS C:\> $j = Get-Job -Name MyJob
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```


### <span data-ttu-id="f72ec-169">範例8：取得所有工作，包括其他方法啟動的作業</span><span class="sxs-lookup"><span data-stu-id="f72ec-169">Example 8: Get all jobs including jobs started by a different method</span></span>

<span data-ttu-id="f72ec-170">此範例示範 `Get-Job` Cmdlet 可以取得在目前會話中啟動的所有作業，即使它們是使用不同的方法啟動的。</span><span class="sxs-lookup"><span data-stu-id="f72ec-170">This example demonstrates that the `Get-Job` cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

<span data-ttu-id="f72ec-171">第一個命令會使用 `Start-Job` Cmdlet 在本機電腦上啟動作業。</span><span class="sxs-lookup"><span data-stu-id="f72ec-171">The first command uses the `Start-Job` cmdlet to start a job on the local computer.</span></span> <span data-ttu-id="f72ec-172">第二個命令會使用 Cmdlet 的 **AsJob** 參數 `Invoke-Command` ，在 S1 電腦上啟動作業。</span><span class="sxs-lookup"><span data-stu-id="f72ec-172">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a job on the S1 computer.</span></span> <span data-ttu-id="f72ec-173">即使工作中的命令是在遠端電腦上執行，還是會在本機電腦上建立工作物件，因此您可以使用本機命令來管理工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-173">Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.</span></span> <span data-ttu-id="f72ec-174">第三個命令會使用 `Invoke-Command` Cmdlet `Start-Job` 在 S2 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="f72ec-174">The third command uses the `Invoke-Command` cmdlet to run a `Start-Job` command on the S2 computer.</span></span> <span data-ttu-id="f72ec-175">使用這個方法時，會在遠端電腦上建立工作物件，因此您可以使用遠端命令來管理作業。</span><span class="sxs-lookup"><span data-stu-id="f72ec-175">By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.</span></span> <span data-ttu-id="f72ec-176">第四個命令會使用 `Get-Job` 來取得儲存在本機電腦上的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-176">The fourth command uses `Get-Job` to get the jobs stored on the local computer.</span></span> <span data-ttu-id="f72ec-177">Windows PowerShell 3.0 中引進之作業的 **PSJobTypeName** 屬性顯示使用指令程式啟動的本機作業 `Start-Job` 是背景工作，而使用 Cmdlet 在遠端會話中啟動的作業 `Invoke-Command` 是遠端作業。</span><span class="sxs-lookup"><span data-stu-id="f72ec-177">The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the `Start-Job` cmdlet is a background job and the job started in a remote session by using the `Invoke-Command` cmdlet is a remote job.</span></span> <span data-ttu-id="f72ec-178">第五個命令會使用在 `Invoke-Command` `Get-Job` S2 電腦上執行命令。範例輸出會顯示命令的結果 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-178">The fifth command uses `Invoke-Command` to run a `Get-Job` command on the S2 computer.The sample output shows the results of the `Get-Job` command.</span></span> <span data-ttu-id="f72ec-179">在 S2 電腦上，工作顯示為本機工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-179">On the S2 computer, the job appears to be a local job.</span></span> <span data-ttu-id="f72ec-180">電腦名稱稱是 localhost，而工作類型是背景工作。如需有關如何在遠端電腦上執行背景工作的詳細資訊，請參閱 [about_Remote_Jobs](./about/about_Remote_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="f72ec-180">The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see [about_Remote_Jobs](./about/about_Remote_Jobs.md).</span></span>

```
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

### <span data-ttu-id="f72ec-181">範例9：調查失敗的作業</span><span class="sxs-lookup"><span data-stu-id="f72ec-181">Example 9: Investigate a failed job</span></span>

<span data-ttu-id="f72ec-182">此命令會顯示如何使用傳回的工作物件， `Get-Job` 來調查作業失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="f72ec-182">This command shows how to use the job object that `Get-Job` returns to investigate why a job failed.</span></span>
<span data-ttu-id="f72ec-183">它也會示範如何取得每個工作的子工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-183">It also shows how to get the child jobs of each job.</span></span>

<span data-ttu-id="f72ec-184">第一個命令會使用 `Start-Job` Cmdlet 在本機電腦上啟動作業。</span><span class="sxs-lookup"><span data-stu-id="f72ec-184">The first command uses the `Start-Job` cmdlet to start a job on the local computer.</span></span> <span data-ttu-id="f72ec-185">傳回的工作物件 `Start-Job` 顯示作業失敗。</span><span class="sxs-lookup"><span data-stu-id="f72ec-185">The job object that `Start-Job` returns shows that the job failed.</span></span> <span data-ttu-id="f72ec-186">**State** 屬性的值為 Failed。</span><span class="sxs-lookup"><span data-stu-id="f72ec-186">The value of the **State** property is Failed.</span></span>

<span data-ttu-id="f72ec-187">第二個命令會使用 `Get-Job` Cmdlet 來取得工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-187">The second command uses the `Get-Job` cmdlet to get the job.</span></span> <span data-ttu-id="f72ec-188">命令使用點方法，取得物件的 **JobStateInfo** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="f72ec-188">The command uses the dot method to get the value of the **JobStateInfo** property of the object.</span></span> <span data-ttu-id="f72ec-189">它會使用管線運算子將 **JobStateInfo** 屬性中的物件傳送至 `Format-List` Cmdlet，此 Cmdlet 會將物件的所有屬性格式化 (`*` 清單中) 。命令的結果 `Format-List` 顯示作業的 **Reason** 屬性值是空白的。</span><span class="sxs-lookup"><span data-stu-id="f72ec-189">It uses a pipeline operator to send the object in the **JobStateInfo** property to the `Format-List` cmdlet, which formats all of the properties of the object (`*`) in a list.The result of the `Format-List` command shows that the value of the **Reason** property of the job is blank.</span></span>

<span data-ttu-id="f72ec-190">第三個命令會進一步調查。</span><span class="sxs-lookup"><span data-stu-id="f72ec-190">The third command investigates more.</span></span> <span data-ttu-id="f72ec-191">它會使用 `Get-Job` 命令來取得工作，然後使用管線運算子將整個工作物件傳送至 `Format-List` Cmdlet，此 Cmdlet 會將工作的所有屬性顯示在清單中。工作物件中所有屬性的顯示會顯示作業包含名為 Job2 的子工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-191">It uses a `Get-Job` command to get the job and then uses a pipeline operator to send the whole job object to the `Format-List` cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.</span></span>

<span data-ttu-id="f72ec-192">第四個命令 `Get-Job` 會使用來取得代表 Job2 子工作的工作物件。</span><span class="sxs-lookup"><span data-stu-id="f72ec-192">The fourth command uses `Get-Job` to get the job object that represents the Job2 child job.</span></span> <span data-ttu-id="f72ec-193">這是命令實際於其中執行的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-193">This is the job in which the command actually ran.</span></span> <span data-ttu-id="f72ec-194">它會使用點方法來取得 **JobStateInfo** 屬性的 **Reason** 屬性。結果顯示作業因為拒絕存取錯誤而失敗。</span><span class="sxs-lookup"><span data-stu-id="f72ec-194">It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error.</span></span> <span data-ttu-id="f72ec-195">在此情況下，使用者在啟動 Windows PowerShell 時忘記使用 [以系統管理員身分執行] 選項。因為背景工作使用 Windows PowerShell 的遠端功能，所以必須將電腦設定為遠端執行作業，即使是在本機電腦上執行工作。如需 Windows PowerShell 中的遠端處理需求的詳細資訊，請參閱 [about_Remote_Requirements](./about/about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f72ec-195">In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see [about_Remote_Requirements](./about/about_Remote_Requirements.md).</span></span> <span data-ttu-id="f72ec-196">如需疑難排解秘訣，請參閱 [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="f72ec-196">For troubleshooting tips, see [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md).</span></span>

```
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

PS C:\> Get-Job | Format-List -Property *
HasMoreData   : False
StatusMessage :
Location      : localhost
Command       : get-process
JobStateInfo  : Failed
Finished      : System.Threading.ManualReset
EventInstanceId    : fb792295-1318-4f5d-8ac8-8a89c5261507
Id            : 1
Name          : Job1
ChildJobs     : {Job2}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :

PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the
following error message: Access is denied.
```

### <span data-ttu-id="f72ec-197">範例10：取得篩選的結果</span><span class="sxs-lookup"><span data-stu-id="f72ec-197">Example 10: Get filtered results</span></span>

<span data-ttu-id="f72ec-198">這個範例示範如何使用 **Filter** 參數取得工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-198">This example shows how to use the **Filter** parameter to get a workflow job.</span></span> <span data-ttu-id="f72ec-199">**Filter** 參數 (在 Windows PowerShell 3.0 中引進) 只適用於自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-199">The **Filter** parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

<span data-ttu-id="f72ec-200">第一個命令會使用 **Workflow** 關鍵字來建立 WFProcess 工作流程。</span><span class="sxs-lookup"><span data-stu-id="f72ec-200">The first command uses the **Workflow** keyword to create the WFProcess workflow.</span></span> <span data-ttu-id="f72ec-201">第二個命令會使用 WFProcess 工作流程的 **AsJob** 參數，以背景工作的形式執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="f72ec-201">The second command uses the **AsJob** parameter of the WFProcess workflow to run the workflow as a background job.</span></span> <span data-ttu-id="f72ec-202">它使用工作流程的 **JobName** 參數指定工作的名稱，以及使用工作流程的 **PSPrivateMetadata** 參數指定自訂識別碼。</span><span class="sxs-lookup"><span data-stu-id="f72ec-202">It uses the **JobName** parameter of the workflow to specify a name for the job, and the **PSPrivateMetadata** parameter of the workflow to specify a custom ID.</span></span> <span data-ttu-id="f72ec-203">第三個命令使用的 **Filter** 參數， `Get-Job` 依 **PSPrivateMetadata** 參數中指定的自訂識別碼取得工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-203">The third command uses the **Filter** parameter of `Get-Job` to get the job by custom ID that was specified in the **PSPrivateMetadata** parameter.</span></span>

```
PS C:\> Workflow WFProcess {Get-Process}
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

### <span data-ttu-id="f72ec-204">範例11：取得子作業的相關資訊</span><span class="sxs-lookup"><span data-stu-id="f72ec-204">Example 11: Get information about child jobs</span></span>

<span data-ttu-id="f72ec-205">此範例顯示使用 Cmdlet 的 **IncludeChildJob** 和 **ChildJobState** 參數的效果 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-205">This example shows the effect of using the **IncludeChildJob** and **ChildJobState** parameters of the `Get-Job` cmdlet.</span></span>

<span data-ttu-id="f72ec-206">第一個命令取得目前工作階段中的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-206">The first command gets the jobs in the current session.</span></span> <span data-ttu-id="f72ec-207">輸出包含背景工作、遠端工作，以及已排程工作的數個執行個體。</span><span class="sxs-lookup"><span data-stu-id="f72ec-207">The output includes a background job, a remote job and several instances of a scheduled job.</span></span> <span data-ttu-id="f72ec-208">遠端工作 (Job4) 似乎已失敗。</span><span class="sxs-lookup"><span data-stu-id="f72ec-208">The remote job, Job4, appears to have failed.</span></span>
<span data-ttu-id="f72ec-209">第二個命令使用的 **IncludeChildJob** 參數 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-209">The second command uses the **IncludeChildJob** parameter of `Get-Job`.</span></span> <span data-ttu-id="f72ec-210">輸出會加入所有具有子工作的工作的子工作。在此情況下，修改後的輸出會顯示只有 Job4 的 Job5 子工作失敗。</span><span class="sxs-lookup"><span data-stu-id="f72ec-210">The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.</span></span> <span data-ttu-id="f72ec-211">第三個命令使用 **ChildJobState** 參數，其值為 failed。輸出會包含所有父工作，以及只有失敗的子工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-211">The third command uses the **ChildJobState** parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.</span></span> <span data-ttu-id="f72ec-212">第五個命令使用工作的 **JobStateInfo** 屬性及其 **Reason** 屬性，來探索 Job5 失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="f72ec-212">The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.</span></span>

```
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

PS C:\> Get-Job -IncludeChildJob
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
3      Job3                            Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
6      Job6                            Completed     True            Server02            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

PS C:\> Get-Job -Name Job4 -ChildJobState Failed
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
```

<span data-ttu-id="f72ec-213">如需詳細資訊，請參閱 [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md) 說明主題。</span><span class="sxs-lookup"><span data-stu-id="f72ec-213">For more information, see the [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md) Help topic.</span></span>

## <span data-ttu-id="f72ec-214">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f72ec-214">PARAMETERS</span></span>

### <span data-ttu-id="f72ec-215">-After</span><span class="sxs-lookup"><span data-stu-id="f72ec-215">-After</span></span>

<span data-ttu-id="f72ec-216">取得在指定日期和時間之後結束的已完成工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-216">Gets completed jobs that ended after the specified date and time.</span></span> <span data-ttu-id="f72ec-217">輸入 **datetime** 物件（例如 Cmdlet 所傳回的物件） `Get-Date` 或可以轉換成 **DateTime** 物件的字串，例如 `Dec 1, 2012 2:00 AM` 或 `11/06` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-217">Enter a **DateTime** object, such as one returned by the `Get-Date` cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="f72ec-218">這個參數只適用於含有 **EndTime** 屬性的自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-218">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="f72ec-219">它無法在標準背景工作上運作，例如使用 Cmdlet 所建立的工作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-219">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="f72ec-220">如需支援此參數的詳細資訊，請參閱工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="f72ec-220">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="f72ec-221">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="f72ec-221">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f72ec-222">-Before</span><span class="sxs-lookup"><span data-stu-id="f72ec-222">-Before</span></span>

<span data-ttu-id="f72ec-223">取得在指定日期和時間之前結束的已完成工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-223">Gets completed jobs that ended before the specified date and time.</span></span> <span data-ttu-id="f72ec-224">輸入 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="f72ec-224">Enter a **DateTime** object.</span></span>

<span data-ttu-id="f72ec-225">這個參數只適用於含有 **EndTime** 屬性的自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-225">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="f72ec-226">它無法在標準背景工作上運作，例如使用 Cmdlet 所建立的工作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-226">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="f72ec-227">如需支援此參數的詳細資訊，請參閱工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="f72ec-227">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="f72ec-228">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="f72ec-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f72ec-229">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="f72ec-229">-ChildJobState</span></span>

<span data-ttu-id="f72ec-230">只取得具有指定狀態的子工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-230">Gets only the child jobs that have the specified state.</span></span> <span data-ttu-id="f72ec-231">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="f72ec-231">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f72ec-232">NotStarted</span><span class="sxs-lookup"><span data-stu-id="f72ec-232">NotStarted</span></span>
- <span data-ttu-id="f72ec-233">執行中</span><span class="sxs-lookup"><span data-stu-id="f72ec-233">Running</span></span>
- <span data-ttu-id="f72ec-234">Completed</span><span class="sxs-lookup"><span data-stu-id="f72ec-234">Completed</span></span>
- <span data-ttu-id="f72ec-235">失敗</span><span class="sxs-lookup"><span data-stu-id="f72ec-235">Failed</span></span>
- <span data-ttu-id="f72ec-236">已停止</span><span class="sxs-lookup"><span data-stu-id="f72ec-236">Stopped</span></span>
- <span data-ttu-id="f72ec-237">封鎖</span><span class="sxs-lookup"><span data-stu-id="f72ec-237">Blocked</span></span>
- <span data-ttu-id="f72ec-238">暫止</span><span class="sxs-lookup"><span data-stu-id="f72ec-238">Suspended</span></span>
- <span data-ttu-id="f72ec-239">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="f72ec-239">Disconnected</span></span>
- <span data-ttu-id="f72ec-240">Suspending</span><span class="sxs-lookup"><span data-stu-id="f72ec-240">Suspending</span></span>
- <span data-ttu-id="f72ec-241">停止中</span><span class="sxs-lookup"><span data-stu-id="f72ec-241">Stopping</span></span>

<span data-ttu-id="f72ec-242">依預設，不 `Get-Job` 會取得子工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-242">By default, `Get-Job` does not get child jobs.</span></span> <span data-ttu-id="f72ec-243">藉由使用 **IncludeChildJob** 參數， `Get-Job` 取得所有子工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-243">By using the **IncludeChildJob** parameter, `Get-Job` gets all child jobs.</span></span> <span data-ttu-id="f72ec-244">如果您使用 **ChildJobState** 參數， **IncludeChildJob** 參數就沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="f72ec-244">If you use the **ChildJobState** parameter, the **IncludeChildJob** parameter has no effect.</span></span>

<span data-ttu-id="f72ec-245">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="f72ec-245">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f72ec-246">-Command</span><span class="sxs-lookup"><span data-stu-id="f72ec-246">-Command</span></span>

<span data-ttu-id="f72ec-247">將命令陣列指定為字串。</span><span class="sxs-lookup"><span data-stu-id="f72ec-247">Specifies an array of commands as strings.</span></span> <span data-ttu-id="f72ec-248">此 Cmdlet 會取得包含指定命令的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-248">This cmdlet gets the jobs that include the specified commands.</span></span> <span data-ttu-id="f72ec-249">預設為所有工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-249">The default is all jobs.</span></span> <span data-ttu-id="f72ec-250">您可以使用萬用字元來指定命令模式。</span><span class="sxs-lookup"><span data-stu-id="f72ec-250">You can use wildcard characters to specify a command pattern.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="f72ec-251">-Filter</span><span class="sxs-lookup"><span data-stu-id="f72ec-251">-Filter</span></span>

<span data-ttu-id="f72ec-252">指定條件的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="f72ec-252">Specifies a hash table of conditions.</span></span> <span data-ttu-id="f72ec-253">此 Cmdlet 會取得符合所有條件的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-253">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="f72ec-254">輸入索引鍵為工作屬性且值為工作屬性值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="f72ec-254">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="f72ec-255">這個參數只適用於自訂工作類型，例如，工作流程工作和已排程的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-255">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="f72ec-256">它無法在標準背景工作上運作，例如使用 Cmdlet 所建立的工作 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-256">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="f72ec-257">如需支援此參數的詳細資訊，請參閱工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="f72ec-257">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="f72ec-258">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="f72ec-258">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f72ec-259">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="f72ec-259">-HasMoreData</span></span>

<span data-ttu-id="f72ec-260">指出此 Cmdlet 是否只會取得具有指定之 **HasMoreData** 屬性值的作業。</span><span class="sxs-lookup"><span data-stu-id="f72ec-260">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="f72ec-261">**HasMoreData** 屬性會指出是否已在目前工作階段中收到所有的工作結果。</span><span class="sxs-lookup"><span data-stu-id="f72ec-261">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span> <span data-ttu-id="f72ec-262">若要取得具有更多結果的工作，請指定值 `$True` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-262">To get jobs that have more results, specify a value of `$True`.</span></span> <span data-ttu-id="f72ec-263">若要取得沒有其他結果的工作，請指定值 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-263">To get jobs that do not have more results, specify a value of `$False`.</span></span>

<span data-ttu-id="f72ec-264">若要取得作業的結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f72ec-264">To get the results of a job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="f72ec-265">當您使用指令 `Receive-Job` 程式時，它會從記憶體內部的會話特定儲存體中刪除它傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="f72ec-265">When you use the `Receive-Job` cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span> <span data-ttu-id="f72ec-266">當它傳回目前會話中的所有工作結果時，它會將工作的 **HasMoreData** 屬性值設定為 `$False`) ，以指出它在目前的會話中沒有其他作業的結果。</span><span class="sxs-lookup"><span data-stu-id="f72ec-266">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to `$False`) to indicate that it has no more results for the job in the current session.</span></span> <span data-ttu-id="f72ec-267">使用的 [ **保持** 參數] `Receive-Job` 可防止 `Receive-Job` 刪除結果及變更 **HasMoreData** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f72ec-267">Use the **Keep** parameter of `Receive-Job` to prevent `Receive-Job` from deleting results and changing the value of the **HasMoreData** property.</span></span>
<span data-ttu-id="f72ec-268">如需詳細資訊，請鍵入 `Get-Help Receive-Job`。</span><span class="sxs-lookup"><span data-stu-id="f72ec-268">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="f72ec-269">**HasMoreData** 屬性是目前工作階段特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="f72ec-269">The **HasMoreData** property is specific to the current session.</span></span> <span data-ttu-id="f72ec-270">如果自訂工作類型的結果儲存在會話外部，例如將工作結果儲存在磁片上的排程工作類型，您可以 `Receive-Job` 在不同的會話中使用此 Cmdlet，以再次取得工作結果，即使 **HasMoreData** 的值為 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-270">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the `Receive-Job` cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is `$False`.</span></span> <span data-ttu-id="f72ec-271">如需詳細資訊，請參閱自訂工作類型的說明主題。</span><span class="sxs-lookup"><span data-stu-id="f72ec-271">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="f72ec-272">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="f72ec-272">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f72ec-273">-Id</span><span class="sxs-lookup"><span data-stu-id="f72ec-273">-Id</span></span>

<span data-ttu-id="f72ec-274">指定此 Cmdlet 取得之作業的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="f72ec-274">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="f72ec-275">識別碼是一個整數，可唯一識別目前工作階段中的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-275">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="f72ec-276">它比較容易記住並輸入實例識別碼，但是它只有在目前的會話中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f72ec-276">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="f72ec-277">您可以輸入一或多個以逗號分隔的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f72ec-277">You can type one or more IDs separated by commas.</span></span> <span data-ttu-id="f72ec-278">若要尋找作業的識別碼，請輸入 `Get-Job` 但不使用參數。</span><span class="sxs-lookup"><span data-stu-id="f72ec-278">To find the ID of a job, type `Get-Job` without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f72ec-279">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="f72ec-279">-IncludeChildJob</span></span>

<span data-ttu-id="f72ec-280">指出除了父作業之外，此 Cmdlet 會傳回子工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-280">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="f72ec-281">這個參數特別適用于調查工作流程工作，其會傳回 `Get-Job` 容器父工作和作業失敗，因為失敗的原因會儲存于子工作的屬性中。</span><span class="sxs-lookup"><span data-stu-id="f72ec-281">This parameter is especially useful for investigating workflow jobs, for which `Get-Job` returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="f72ec-282">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="f72ec-282">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f72ec-283">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="f72ec-283">-InstanceId</span></span>

<span data-ttu-id="f72ec-284">指定此 Cmdlet 取得之作業的實例識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="f72ec-284">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span> <span data-ttu-id="f72ec-285">預設為所有工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-285">The default is all jobs.</span></span>

<span data-ttu-id="f72ec-286">執行個體識別碼是 GUID，可唯一識別電腦上的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-286">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="f72ec-287">若要尋找工作的實例識別碼，請使用 `Get-Job` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-287">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="f72ec-288">-Name</span><span class="sxs-lookup"><span data-stu-id="f72ec-288">-Name</span></span>

<span data-ttu-id="f72ec-289">指定此 Cmdlet 取得之作業的實例易記名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="f72ec-289">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span> <span data-ttu-id="f72ec-290">輸入工作名稱，或使用萬用字元來輸入工作名稱模式。</span><span class="sxs-lookup"><span data-stu-id="f72ec-290">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span> <span data-ttu-id="f72ec-291">依預設，會 `Get-Job` 取得目前會話中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-291">By default, `Get-Job` gets all jobs in the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="f72ec-292">-Newest</span><span class="sxs-lookup"><span data-stu-id="f72ec-292">-Newest</span></span>

<span data-ttu-id="f72ec-293">指定要取得的作業數。</span><span class="sxs-lookup"><span data-stu-id="f72ec-293">Specifies a number of jobs to get.</span></span> <span data-ttu-id="f72ec-294">此 Cmdlet 會取得最近結束的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-294">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="f72ec-295">**Newest** 參數不會依結束時間順序排序或傳回最新的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-295">The **Newest** parameter does not sort or return the newest jobs in end-time order.</span></span> <span data-ttu-id="f72ec-296">若要排序輸出，請使用 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f72ec-296">To sort the output, use the `Sort-Object` cmdlet.</span></span>

<span data-ttu-id="f72ec-297">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="f72ec-297">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f72ec-298">-State</span><span class="sxs-lookup"><span data-stu-id="f72ec-298">-State</span></span>

<span data-ttu-id="f72ec-299">指定工作狀態。</span><span class="sxs-lookup"><span data-stu-id="f72ec-299">Specifies a job state.</span></span> <span data-ttu-id="f72ec-300">此 Cmdlet 只會取得處於指定狀態的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-300">This cmdlet gets only jobs in the specified state.</span></span> <span data-ttu-id="f72ec-301">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="f72ec-301">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f72ec-302">NotStarted</span><span class="sxs-lookup"><span data-stu-id="f72ec-302">NotStarted</span></span>
- <span data-ttu-id="f72ec-303">執行中</span><span class="sxs-lookup"><span data-stu-id="f72ec-303">Running</span></span>
- <span data-ttu-id="f72ec-304">Completed</span><span class="sxs-lookup"><span data-stu-id="f72ec-304">Completed</span></span>
- <span data-ttu-id="f72ec-305">失敗</span><span class="sxs-lookup"><span data-stu-id="f72ec-305">Failed</span></span>
- <span data-ttu-id="f72ec-306">已停止</span><span class="sxs-lookup"><span data-stu-id="f72ec-306">Stopped</span></span>
- <span data-ttu-id="f72ec-307">封鎖</span><span class="sxs-lookup"><span data-stu-id="f72ec-307">Blocked</span></span>
- <span data-ttu-id="f72ec-308">暫止</span><span class="sxs-lookup"><span data-stu-id="f72ec-308">Suspended</span></span>
- <span data-ttu-id="f72ec-309">已中斷連接</span><span class="sxs-lookup"><span data-stu-id="f72ec-309">Disconnected</span></span>
- <span data-ttu-id="f72ec-310">Suspending</span><span class="sxs-lookup"><span data-stu-id="f72ec-310">Suspending</span></span>
- <span data-ttu-id="f72ec-311">停止中</span><span class="sxs-lookup"><span data-stu-id="f72ec-311">Stopping</span></span>

<span data-ttu-id="f72ec-312">依預設，會 `Get-Job` 取得目前會話中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-312">By default, `Get-Job` gets all the jobs in the current session.</span></span>

<span data-ttu-id="f72ec-313">如需有關工作狀態的詳細資訊，請參閱 [JobState 列舉](/dotnet/api/system.management.automation.jobstate)。</span><span class="sxs-lookup"><span data-stu-id="f72ec-313">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="f72ec-314">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f72ec-314">CommonParameters</span></span>

<span data-ttu-id="f72ec-315">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f72ec-315">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f72ec-316">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f72ec-316">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f72ec-317">輸入</span><span class="sxs-lookup"><span data-stu-id="f72ec-317">INPUTS</span></span>

### <span data-ttu-id="f72ec-318">無</span><span class="sxs-lookup"><span data-stu-id="f72ec-318">None</span></span>

<span data-ttu-id="f72ec-319">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f72ec-319">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f72ec-320">輸出</span><span class="sxs-lookup"><span data-stu-id="f72ec-320">OUTPUTS</span></span>

### <span data-ttu-id="f72ec-321">System.Management.Automation.RemotingJob</span><span class="sxs-lookup"><span data-stu-id="f72ec-321">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="f72ec-322">此 Cmdlet 會傳回代表會話中之作業的物件。</span><span class="sxs-lookup"><span data-stu-id="f72ec-322">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="f72ec-323">注意</span><span class="sxs-lookup"><span data-stu-id="f72ec-323">NOTES</span></span>

<span data-ttu-id="f72ec-324">工作的 **PSJobTypeName** 屬性會指出工作的工作類型。</span><span class="sxs-lookup"><span data-stu-id="f72ec-324">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="f72ec-325">屬性值是由工作類型作者所決定。</span><span class="sxs-lookup"><span data-stu-id="f72ec-325">The property value is determined by the job type author.</span></span> <span data-ttu-id="f72ec-326">下列清單顯示常見的工作類型。</span><span class="sxs-lookup"><span data-stu-id="f72ec-326">The following list shows common job types.</span></span>

- <span data-ttu-id="f72ec-327">**BackgroundJob** 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-327">**BackgroundJob**.</span></span> <span data-ttu-id="f72ec-328">使用啟動的本機作業 `Start-Job` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-328">Local job started by using `Start-Job`.</span></span>
- <span data-ttu-id="f72ec-329">**RemoteJob** 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-329">**RemoteJob**.</span></span> <span data-ttu-id="f72ec-330">使用 Cmdlet 的 **AsJob** 參數在 **PSSession** 中啟動作業 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-330">Job started in a **PSSession** by using the **AsJob** parameter of the `Invoke-Command` cmdlet.</span></span>
- <span data-ttu-id="f72ec-331">**PSWorkflowJob** 。</span><span class="sxs-lookup"><span data-stu-id="f72ec-331">**PSWorkflowJob**.</span></span> <span data-ttu-id="f72ec-332">使用工作流程 **AsJob** 一般參數啟動的工作。</span><span class="sxs-lookup"><span data-stu-id="f72ec-332">Job started by using the **AsJob** common parameter of workflows.</span></span>

## <span data-ttu-id="f72ec-333">相關連結</span><span class="sxs-lookup"><span data-stu-id="f72ec-333">RELATED LINKS</span></span>

[<span data-ttu-id="f72ec-334">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="f72ec-334">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="f72ec-335">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="f72ec-335">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="f72ec-336">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="f72ec-336">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="f72ec-337">Start-Job</span><span class="sxs-lookup"><span data-stu-id="f72ec-337">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="f72ec-338">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="f72ec-338">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="f72ec-339">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="f72ec-339">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="f72ec-340">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="f72ec-340">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="f72ec-341">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="f72ec-341">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="f72ec-342">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="f72ec-342">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)
