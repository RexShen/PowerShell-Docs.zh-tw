---
description: 說明如何解決排程工作的問題
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_troubleshooting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Troubleshooting
ms.openlocfilehash: 924205edb9d44724cfef201d84baa304ecde67ad
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207247"
---
# <a name="about-scheduled-jobs-troubleshooting"></a><span data-ttu-id="13f17-104">關於排程工作的疑難排解</span><span class="sxs-lookup"><span data-stu-id="13f17-104">About Scheduled Jobs Troubleshooting</span></span>

## <a name="short-description"></a><span data-ttu-id="13f17-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="13f17-105">Short description</span></span>

<span data-ttu-id="13f17-106">說明如何解決排程工作的問題</span><span class="sxs-lookup"><span data-stu-id="13f17-106">Explains how to resolve problems with scheduled jobs</span></span>

## <a name="long-description"></a><span data-ttu-id="13f17-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="13f17-107">Long description</span></span>

<span data-ttu-id="13f17-108">本檔說明使用 PowerShell 的排程工作功能時，可能會遇到的一些問題，並建議解決這些問題的解決方案。</span><span class="sxs-lookup"><span data-stu-id="13f17-108">This document describes some of the problems that you might experience when using the scheduled job features of PowerShell and it suggests solutions to these problems.</span></span>

<span data-ttu-id="13f17-109">使用 PowerShell 排程工作之前，請參閱 [about_Scheduled_Jobs](about_Scheduled_Jobs.md) 以及相關的排程工作主題。</span><span class="sxs-lookup"><span data-stu-id="13f17-109">Before using PowerShell scheduled jobs, see [about_Scheduled_Jobs](about_Scheduled_Jobs.md) and the related scheduled jobs about topics.</span></span>

<span data-ttu-id="13f17-110">如需 **PSScheduledJob** 模組中所含 Cmdlet 的詳細資訊，請參閱 [PSScheduledJob](xref:PSScheduledJob)。</span><span class="sxs-lookup"><span data-stu-id="13f17-110">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="cant-find-job-results"></a><span data-ttu-id="13f17-111">找不到工作結果</span><span class="sxs-lookup"><span data-stu-id="13f17-111">Can't find job results</span></span>

### <a name="basic-method-for-getting-job-results-in-powershell"></a><span data-ttu-id="13f17-112">在 PowerShell 中取得工作結果的基本方法</span><span class="sxs-lookup"><span data-stu-id="13f17-112">Basic method for getting job results in PowerShell</span></span>

<span data-ttu-id="13f17-113">當排程工作執行時，它會建立排程工作的實例。</span><span class="sxs-lookup"><span data-stu-id="13f17-113">When a scheduled job runs, it creates an instance of the scheduled job.</span></span> <span data-ttu-id="13f17-114">若要查看、管理和取得排程工作實例的結果，請使用 Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="13f17-114">To view, manage, and get the results of scheduled job instances, use the Job cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="13f17-115">若要在排程工作的實例上使用 Job Cmdlet，必須將 **PSScheduledJob** 模組匯入到會話中。</span><span class="sxs-lookup"><span data-stu-id="13f17-115">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="13f17-116">若要匯入 **PSScheduledJob** 模組，請輸入 `Import-Module PSScheduledJob` 或使用任何排程工作 Cmdlet，例如 `Get-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="13f17-116">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="13f17-117">若要取得排程工作的所有實例清單，請使用 `Get-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="13f17-117">To get a list of all instances of a scheduled job, use the `Get-Job` cmdlet.</span></span>

```powershell
Import-Module PSScheduledJob
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State         HasMoreData     Location
--     ----         -------------   -----         -----------     --------
43     ProcessJob   PSScheduledJob  Completed     False           localhost
44     ProcessJob   PSScheduledJob  Completed     False           localhost
45     ProcessJob   PSScheduledJob  Completed     False           localhost
46     ProcessJob   PSScheduledJob  Completed     False           localhost
47     ProcessJob   PSScheduledJob  Completed     False           localhost
48     ProcessJob   PSScheduledJob  Completed     False           localhost
49     ProcessJob   PSScheduledJob  Completed     False           localhost
50     ProcessJob   PSScheduledJob  Completed     False           localhost
```

<span data-ttu-id="13f17-118">`Get-Job`Cmdlet 會將 **ProcessJob** 物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="13f17-118">The `Get-Job` cmdlet sends **ProcessJob** objects down the pipeline.</span></span> <span data-ttu-id="13f17-119">此 `Format-Table` Cmdlet 會在資料表中顯示排程工作實例的 **名稱** 、 **識別碼** 和 **PSBeginTime** 屬性。</span><span class="sxs-lookup"><span data-stu-id="13f17-119">The `Format-Table` cmdlet displays the **Name** , **ID** , and **PSBeginTime** properties of a scheduled job instance in a table.</span></span>

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, PSBeginTime -Auto
```

```Output
Name       Id PSBeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

<span data-ttu-id="13f17-120">若要取得排程工作實例的結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="13f17-120">To get the results of an instance of a scheduled job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="13f17-121">下列命令會取得 ProcessJob (ID = 50) 的最新實例的結果。</span><span class="sxs-lookup"><span data-stu-id="13f17-121">The following command gets the results of the newest instance of the ProcessJob (ID = 50).</span></span>

```powershell
Receive-Job -ID 50
```

### <a name="basic-method-for-finding-job-results-on-disk"></a><span data-ttu-id="13f17-122">在磁片上尋找工作結果的基本方法</span><span class="sxs-lookup"><span data-stu-id="13f17-122">Basic method for finding job results on disk</span></span>

<span data-ttu-id="13f17-123">若要管理排程工作，請使用 job Cmdlet，例如 `Get-Job` 和 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="13f17-123">To manage scheduled jobs, use the job cmdlets, such as `Get-Job` and `Receive-Job`.</span></span>

<span data-ttu-id="13f17-124">如果 `Get-Job` 未取得工作實例或未 `Receive-Job` 取得工作結果，您可以在磁片上搜尋作業的執行歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="13f17-124">If `Get-Job` does not get the job instance or `Receive-Job` does not get the job results, you can search the execution history files for the job on disk.</span></span>
<span data-ttu-id="13f17-125">執行歷程記錄包含所有觸發之工作實例的記錄。</span><span class="sxs-lookup"><span data-stu-id="13f17-125">The execution history contains a record of all triggered job instances.</span></span>

<span data-ttu-id="13f17-126">確認在下列路徑中，排程工作的目錄中有時間戳記命名的目錄：</span><span class="sxs-lookup"><span data-stu-id="13f17-126">Verify that there is a timestamp-named directory in the directory for a scheduled job in the following path:</span></span>

`$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

<span data-ttu-id="13f17-127">例如：</span><span class="sxs-lookup"><span data-stu-id="13f17-127">For example:</span></span>

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

<span data-ttu-id="13f17-128">例如，Cmdlet 會 `Get-ChildItem` 取得 **ProcessJob** 排程工作的磁片上執行歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="13f17-128">For example, the `Get-ChildItem` cmdlet gets the on-disk execution history of the **ProcessJob** scheduled job.</span></span>

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

<span data-ttu-id="13f17-129">每個以時間戳記命名的目錄都代表一個工作實例。</span><span class="sxs-lookup"><span data-stu-id="13f17-129">Each timestamp-named directory represents a job instance.</span></span> <span data-ttu-id="13f17-130">每個工作實例的結果會儲存在時間戳記命名目錄的 **Results.xml** 檔案中。</span><span class="sxs-lookup"><span data-stu-id="13f17-130">The results of each job instance are saved in a **Results.xml** file in the timestamp-named directory.</span></span>

<span data-ttu-id="13f17-131">例如，下列命令會取得 **ProcessJob** 排程工作的每個已儲存實例的 **Results.xml** 檔案。</span><span class="sxs-lookup"><span data-stu-id="13f17-131">For example, the following command gets the **Results.xml** files for every saved instance of the **ProcessJob** scheduled job.</span></span> <span data-ttu-id="13f17-132">如果遺失 **Results.xml** 檔案，則 PowerShell 無法傳回或顯示工作結果。</span><span class="sxs-lookup"><span data-stu-id="13f17-132">If the **Results.xml** file is missing, PowerShell cannot return or display the job results.</span></span>

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output\*\Results.xml'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\Appdata\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output
```

<span data-ttu-id="13f17-133">Job Cmdlet 可能無法取得排程工作實例或其結果，因為 **PSScheduledJob** 模組未匯入會話中。</span><span class="sxs-lookup"><span data-stu-id="13f17-133">The job cmdlet might not be able to get scheduled job instances or their results because the **PSScheduledJob** module is not imported into the session.</span></span>

> [!NOTE]
> <span data-ttu-id="13f17-134">在排程工作實例上使用 job Cmdlet 之前，請確認 **PSScheduledJob** 模組是否包含在會話中。</span><span class="sxs-lookup"><span data-stu-id="13f17-134">Before using a job cmdlet on scheduled job instances, verify that the **PSScheduledJob** module is included in the session.</span></span> <span data-ttu-id="13f17-135">如果沒有 **PSScheduledJob** 模組，則工作 Cmdlet 無法取得排程工作實例或其結果。</span><span class="sxs-lookup"><span data-stu-id="13f17-135">Without the **PSScheduledJob** module, the job cmdlets cannot get scheduled job instances or their results.</span></span>

<span data-ttu-id="13f17-136">若要匯入 **PSScheduledJob** 模組：</span><span class="sxs-lookup"><span data-stu-id="13f17-136">To import the **PSScheduledJob** module:</span></span>

```powershell
Import-Module PSScheduledJob
```

### <a name="receive-job-cmdlet-might-already-have-returned-the-results"></a><span data-ttu-id="13f17-137">Receive-Job Cmdlet 可能已經傳回結果</span><span class="sxs-lookup"><span data-stu-id="13f17-137">Receive-Job cmdlet might already have returned the results</span></span>

<span data-ttu-id="13f17-138">如果沒有傳回 `Receive-Job` 工作實例的結果，可能是因為未 `Receive-Job` 使用 **Keep** 參數在目前會話中執行該工作實例的命令。</span><span class="sxs-lookup"><span data-stu-id="13f17-138">If `Receive-Job` does not return job instance results, it might be because a `Receive-Job` command has been run for that job instance in the current session without the **Keep** parameter.</span></span>

<span data-ttu-id="13f17-139">當您使用 `Receive-Job` 而不使用 **Keep** 參數時，會傳回 `Receive-Job` 工作結果，並將工作實例的 **HasMoreData** 屬性設定為 **False** 。</span><span class="sxs-lookup"><span data-stu-id="13f17-139">When you use `Receive-Job` without the **Keep** parameter, `Receive-Job` returns the job results and sets the job instance's **HasMoreData** property to **False** .</span></span> <span data-ttu-id="13f17-140">**False** 值表示 `Receive-Job` 傳回作業的結果，而實例則不再傳回結果。</span><span class="sxs-lookup"><span data-stu-id="13f17-140">The **False** value means that `Receive-Job` returned the job's results and the instance has no more results to return.</span></span> <span data-ttu-id="13f17-141">這項設定適用于標準背景工作，但不適用於已儲存至磁片的排程工作實例。</span><span class="sxs-lookup"><span data-stu-id="13f17-141">This setting is appropriate for standard background jobs, but not for instances of scheduled jobs, which are saved to disk.</span></span>

<span data-ttu-id="13f17-142">若要再次取得工作實例的結果，請輸入以啟動新的 PowerShell 會話 `PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="13f17-142">To get the job instance results again, start a new PowerShell session by typing `PowerShell`.</span></span> <span data-ttu-id="13f17-143">匯入 **PSScheduledJob** 模組，然後再次嘗試 `Receive-Job` 命令。</span><span class="sxs-lookup"><span data-stu-id="13f17-143">Import the **PSScheduledJob** module, and try the `Receive-Job` command again.</span></span>

```powershell
Receive-Job -ID 50
```

```Output
#No results
```

```powershell
PowerShell.exe
```

```Output
Windows PowerShell
Copyright (C) 2012 Microsoft Corporation. All rights reserved.
```

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="using-keep-parameter-to-get-results-more-than-one-time-in-a-session"></a><span data-ttu-id="13f17-144">在會話中使用 Keep 參數來取得超過一次的結果</span><span class="sxs-lookup"><span data-stu-id="13f17-144">Using Keep parameter to get results more than one time in a session</span></span>

<span data-ttu-id="13f17-145">若要在會話中多次取得工作實例的結果，請使用 Cmdlet 的 **Keep** 參數 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="13f17-145">To get the result of a job instance more than one time in a session, use the **Keep** parameter of the `Receive-Job` cmdlet.</span></span>

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

```powershell
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="the-scheduled-job-might-be-corrupted"></a><span data-ttu-id="13f17-146">排程工作可能已損毀</span><span class="sxs-lookup"><span data-stu-id="13f17-146">The scheduled job might be corrupted</span></span>

<span data-ttu-id="13f17-147">如果排程工作損毀，PowerShell 會刪除損毀的排程工作及其結果。</span><span class="sxs-lookup"><span data-stu-id="13f17-147">If a scheduled job becomes corrupted, PowerShell deletes the corrupted scheduled job and its results.</span></span> <span data-ttu-id="13f17-148">您無法復原損毀的排程工作結果。</span><span class="sxs-lookup"><span data-stu-id="13f17-148">You cannot recover the results of a corrupted scheduled job.</span></span>

<span data-ttu-id="13f17-149">若要判斷排程工作是否仍然存在，請使用 `Get-ScheduledJob` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="13f17-149">To determine if a scheduled job still exists, use the `Get-ScheduledJob` cmdlet.</span></span>

```powershell
Get-ScheduledJob
```

### <a name="the-number-of-results-might-have-exceeded-the-executionhistorylength"></a><span data-ttu-id="13f17-150">結果數目可能已超過 ExecutionHistoryLength</span><span class="sxs-lookup"><span data-stu-id="13f17-150">The number of results might have exceeded the ExecutionHistoryLength</span></span>

<span data-ttu-id="13f17-151">排程工作的 **ExecutionHistoryLength** 屬性會決定要將多少個工作實例和其結果儲存至磁片。</span><span class="sxs-lookup"><span data-stu-id="13f17-151">The **ExecutionHistoryLength** property of a scheduled job determines how many job instances, and their results, are saved to disk.</span></span> <span data-ttu-id="13f17-152">預設值為 32。</span><span class="sxs-lookup"><span data-stu-id="13f17-152">The default value is 32.</span></span>
<span data-ttu-id="13f17-153">當排程工作的實例數目超過此值時，PowerShell 會刪除最舊的工作實例，以騰出空間給每個新的工作實例。</span><span class="sxs-lookup"><span data-stu-id="13f17-153">When the number of instances of a scheduled job exceeds this value, PowerShell deletes the oldest job instance to make room for each new job instance.</span></span>

<span data-ttu-id="13f17-154">若要取得排程工作的 **ExecutionHistoryLength** 屬性值，請使用下列命令格式：</span><span class="sxs-lookup"><span data-stu-id="13f17-154">To get the value of the **ExecutionHistoryLength** property of a scheduled job, use the following command format:</span></span>

```powershell
(Get-ScheduledJob <JobName>).ExecutionHistoryLength
```

<span data-ttu-id="13f17-155">例如，下列命令會取得 **ProcessJob** 排程工作的 **ExecutionHistoryLength** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="13f17-155">For example, the following command gets the value of the **ExecutionHistoryLength** property of the **ProcessJob** scheduled job.</span></span>

```powershell
(Get-ScheduledJob ProcessJob).ExecutionHistoryLength
```

<span data-ttu-id="13f17-156">若要設定或變更 **ExecutionHistoryLength** 屬性的值，請使用和 Cmdlet 的 **MaxResultCount** 參數 `Register-ScheduledJob` `Set-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="13f17-156">To set or change the value of the **ExecutionHistoryLength** property, use the **MaxResultCount** parameter of the `Register-ScheduledJob` and `Set-ScheduledJob` cmdlets.</span></span>

<span data-ttu-id="13f17-157">下列命令會將 **ExecutionHistoryLength** 屬性的值增加為50。</span><span class="sxs-lookup"><span data-stu-id="13f17-157">The following command increases the value of the **ExecutionHistoryLength** property to 50.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 50
```

### <a name="the-job-instance-results-might-have-been-deleted"></a><span data-ttu-id="13f17-158">作業實例的結果可能已刪除</span><span class="sxs-lookup"><span data-stu-id="13f17-158">The job instance results might have been deleted</span></span>

<span data-ttu-id="13f17-159">Cmdlet 的 **ClearExecutionHistory** 參數會 `Set-ScheduledJob` 刪除作業的執行歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="13f17-159">The **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet deletes the execution history of a job.</span></span> <span data-ttu-id="13f17-160">您可以使用這項功能來釋出磁碟空間，或刪除不需要或已經使用、分析或儲存在不同位置的結果。</span><span class="sxs-lookup"><span data-stu-id="13f17-160">You can use this feature to free up disk space or delete results that are not needed, or already used, analyzed or saved in a different location.</span></span>

<span data-ttu-id="13f17-161">若要刪除排程工作的執行歷程記錄，請使用排程工作的 **ClearExecutionHistory** 參數。</span><span class="sxs-lookup"><span data-stu-id="13f17-161">To delete the execution history of a scheduled job, use the **ClearExecutionHistory** parameter of the scheduled job.</span></span>

<span data-ttu-id="13f17-162">下列命令會刪除 **ProcessJob** 排程工作的執行歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="13f17-162">The following command deletes the execution history of the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="13f17-163">此外，此 `Remove-Job` Cmdlet 會刪除工作結果。</span><span class="sxs-lookup"><span data-stu-id="13f17-163">Also, the `Remove-Job` cmdlet deletes job results.</span></span> <span data-ttu-id="13f17-164">當您使用 `Remove-Job` 刪除排程工作時，它會刪除磁片上的所有作業實例，包括執行歷程記錄和所有工作結果。</span><span class="sxs-lookup"><span data-stu-id="13f17-164">When you use `Remove-Job` to delete a scheduled job, it deletes all instances of the job on disk, including the execution history and all job results.</span></span>

### <a name="jobs-started-by-using-the-start-job-cmdlet-are-not-saved-to-disk"></a><span data-ttu-id="13f17-165">使用 Start-Job Cmdlet 啟動的作業不會儲存到磁片</span><span class="sxs-lookup"><span data-stu-id="13f17-165">Jobs started by using the Start-Job cmdlet are not saved to disk</span></span>

<span data-ttu-id="13f17-166">當您使用 `Start-Job` 來啟動排程工作（而不是使用工作觸發程式）時，會 `Start-Job` 啟動標準的背景工作。</span><span class="sxs-lookup"><span data-stu-id="13f17-166">When you use `Start-Job` to start a scheduled job, instead of using a job trigger, `Start-Job` starts a standard background job.</span></span> <span data-ttu-id="13f17-167">背景工作及其結果不會儲存在磁片上工作的執行歷程記錄中。</span><span class="sxs-lookup"><span data-stu-id="13f17-167">The background job and its results are not stored in the execution history of the job on disk.</span></span>

<span data-ttu-id="13f17-168">您可以使用指令程式 `Get-Job` 取得作業和 `Receive-Job` Cmdlet 來取得工作結果，但除非您使用指令程式的 Keep 參數，否則只有在收到這些結果時，才可使用這些結果 `Receive-Job` 。</span><span class="sxs-lookup"><span data-stu-id="13f17-168">You can use the `Get-Job` cmdlet to get the job and the `Receive-Job` cmdlet to get the job results, but the results are available only until you receive them, unless you use the Keep parameter of the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="13f17-169">此外，背景工作和其結果都是會話特定的;它們只存在於建立它們的會話中。</span><span class="sxs-lookup"><span data-stu-id="13f17-169">Also, background jobs and their results are session-specific; they exist only in the session in which they are created.</span></span> <span data-ttu-id="13f17-170">如果您刪除此作業 `Remove-Job` ，請關閉會話或關閉 PowerShell，作業實例及其結果會被刪除。</span><span class="sxs-lookup"><span data-stu-id="13f17-170">If you delete the job with `Remove-Job`, close the session or close PowerShell, the job instance and its results are deleted.</span></span>

## <a name="scheduled-job-doesnt-run"></a><span data-ttu-id="13f17-171">排程工作未執行</span><span class="sxs-lookup"><span data-stu-id="13f17-171">Scheduled job doesn't run</span></span>

<span data-ttu-id="13f17-172">如果工作觸發程式或排程工作已停用，則排程工作不會自動執行。</span><span class="sxs-lookup"><span data-stu-id="13f17-172">Scheduled jobs don't run automatically if the job triggers or the scheduled job are disabled.</span></span>

<span data-ttu-id="13f17-173">使用 `Get-ScheduledJob` Cmdlet 來取得排程工作。</span><span class="sxs-lookup"><span data-stu-id="13f17-173">Use the `Get-ScheduledJob` cmdlet to get the scheduled job.</span></span> <span data-ttu-id="13f17-174">確認排程工作的 [ **已啟用** ] 屬性值為 [ **True** ]。</span><span class="sxs-lookup"><span data-stu-id="13f17-174">Verify that the value of the **Enabled** property of the scheduled job is **True** .</span></span>

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command         Enabled
--         ----            --------        -------         -------
4          ProcessJob      {1, 2}          Get-Process     True
```

```powershell
(Get-ScheduledJob ProcessJob).Enabled
```

```Output
True
```

<span data-ttu-id="13f17-175">使用 `Get-JobTrigger` Cmdlet 來取得排程工作的工作觸發程式。</span><span class="sxs-lookup"><span data-stu-id="13f17-175">Use the `Get-JobTrigger` cmdlet to get the job triggers of the scheduled job.</span></span>
<span data-ttu-id="13f17-176">確認工作觸發程式的 **Enabled** 屬性值為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="13f17-176">Verify that the value of the **Enabled** property of the job trigger is **True** .</span></span>

```powershell
Get-ScheduledJob ProcessJob | Get-JobTrigger
```

```Output
Id      Frequency    Time                   DaysOfWeek            Enabled
--      ---------    ----                   ----------            -------
1       Weekly       11/7/2011 5:00:00 AM   {Monday, Thursday}    True
2       Daily        11/7/2011 3:00:00 PM                         True
```

```powershell
Get-ScheduledJob ProcessJob|Get-JobTrigger|Format-Table ID, Enabled -Auto
```

```Output
Id Enabled
-- -------
1    True
2    True
```

### <a name="scheduled-jobs-dont-run-automatically-if-job-triggers-are-invalid"></a><span data-ttu-id="13f17-177">如果工作觸發程式無效，則排程工作不會自動執行</span><span class="sxs-lookup"><span data-stu-id="13f17-177">Scheduled jobs don't run automatically if job triggers are invalid</span></span>

<span data-ttu-id="13f17-178">例如，工作觸發程式可能會指定過去的日期或未發生的日期，例如當月的5星期一。</span><span class="sxs-lookup"><span data-stu-id="13f17-178">For example, a job trigger might specify a date in the past or a date that does not occur, such as the 5th Monday of the month.</span></span>

<span data-ttu-id="13f17-179">如果未滿足工作觸發程式或工作選項的條件，則排程工作不會自動執行。</span><span class="sxs-lookup"><span data-stu-id="13f17-179">Scheduled jobs do not run automatically if the conditions of the job trigger or the job options are not satisfied.</span></span>

<span data-ttu-id="13f17-180">例如，只有在特定使用者登入電腦時才會執行的排程工作，如果該使用者沒有登入或只連接遠端，就不會執行。</span><span class="sxs-lookup"><span data-stu-id="13f17-180">For example, a scheduled job that runs only when a particular user logs on to the computer will not run if that user does not log on or only connects remotely.</span></span>

<span data-ttu-id="13f17-181">檢查排程工作的選項，並確定已滿足這些選項。</span><span class="sxs-lookup"><span data-stu-id="13f17-181">Examine the options of the scheduled job and make sure that they are satisfied.</span></span>
<span data-ttu-id="13f17-182">例如，需要電腦閒置或需要網路連接，或有長 **IdleDuration** 或簡短 **IdleTimeout** 的排程工作可能永遠不會執行。</span><span class="sxs-lookup"><span data-stu-id="13f17-182">For example, a scheduled job that requires that the computer be idle or requires a network connection, or has a long **IdleDuration** or a brief **IdleTimeout** might never run.</span></span>

<span data-ttu-id="13f17-183">使用 `Get-ScheduledJobOption` Cmdlet 來檢查工作選項和其值。</span><span class="sxs-lookup"><span data-stu-id="13f17-183">Use the `Get-ScheduledJobOption` cmdlet to examine the job options and their values.</span></span>

```powershell
Get-ScheduledJob -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="13f17-184">如需排程工作選項的描述，請參閱 [ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption)。</span><span class="sxs-lookup"><span data-stu-id="13f17-184">For descriptions of the scheduled job options, see [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span></span>

### <a name="the-scheduled-job-instance-might-have-failed"></a><span data-ttu-id="13f17-185">排程工作實例可能已失敗</span><span class="sxs-lookup"><span data-stu-id="13f17-185">The scheduled job instance might have failed</span></span>

<span data-ttu-id="13f17-186">如果排程工作命令失敗，PowerShell 會產生錯誤訊息來立即報告。</span><span class="sxs-lookup"><span data-stu-id="13f17-186">If a scheduled job command fails, PowerShell reports it immediately by generating an error message.</span></span> <span data-ttu-id="13f17-187">但是，如果工作排程器嘗試執行作業失敗，PowerShell 就無法使用此錯誤。</span><span class="sxs-lookup"><span data-stu-id="13f17-187">However, if the job fails when Task Scheduler tries to run it, the error is not available to PowerShell.</span></span>

<span data-ttu-id="13f17-188">使用下列方法來偵測並更正作業失敗：</span><span class="sxs-lookup"><span data-stu-id="13f17-188">Use the following methods to detect and correct job failures:</span></span>

<span data-ttu-id="13f17-189">檢查工作排程器事件記錄檔中是否有錯誤。</span><span class="sxs-lookup"><span data-stu-id="13f17-189">Check the Task Scheduler event log for errors.</span></span> <span data-ttu-id="13f17-190">若要檢查記錄檔，請使用事件檢視器或 PowerShell 命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="13f17-190">To check the log, use Event Viewer or a PowerShell command such as the following:</span></span>

```powershell
Get-WinEvent -LogName Microsoft-Windows-TaskScheduler/Operational |
 Where {$_.Message -like "fail"}
```

<span data-ttu-id="13f17-191">檢查工作排程器中的作業記錄。</span><span class="sxs-lookup"><span data-stu-id="13f17-191">Check the job record in Task Scheduler.</span></span> <span data-ttu-id="13f17-192">PowerShell 排程工作會儲存在下列工作排程資料夾中：</span><span class="sxs-lookup"><span data-stu-id="13f17-192">PowerShell scheduled jobs are stored in the following Task Scheduled folder:</span></span>

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`

### <a name="the-scheduled-job-might-not-run-because-of-insufficient-permission"></a><span data-ttu-id="13f17-193">排程工作可能因為許可權不足而無法執行</span><span class="sxs-lookup"><span data-stu-id="13f17-193">The scheduled job might not run because of insufficient permission</span></span>

<span data-ttu-id="13f17-194">排程工作是以建立工作之使用者的許可權，或是或命令中 **Credential** 參數所指定之使用者的許可權來執行 `Register-ScheduledJob` `Set-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="13f17-194">Scheduled jobs run with the permissions of the user who created the job or the permissions of the user who is specified by the **Credential** parameter in the `Register-ScheduledJob` or `Set-ScheduledJob` command.</span></span>

<span data-ttu-id="13f17-195">如果該使用者沒有執行命令或腳本的許可權，作業就會失敗。</span><span class="sxs-lookup"><span data-stu-id="13f17-195">If that user does not have permission to run the commands or scripts, the job fails.</span></span>

## <a name="cant-get-scheduled-job-or-scheduled-job-is-corrupted"></a><span data-ttu-id="13f17-196">無法取得排程工作或排程工作已損毀</span><span class="sxs-lookup"><span data-stu-id="13f17-196">Can't get scheduled job or scheduled job is corrupted</span></span>

<span data-ttu-id="13f17-197">在罕見的情況下，排程工作可能會損毀，或包含無法解決的內部您一致。</span><span class="sxs-lookup"><span data-stu-id="13f17-197">On rare occasions, scheduled jobs can become corrupted or contain internal contradictions that cannot be resolved.</span></span> <span data-ttu-id="13f17-198">一般來說，當排程工作的 XML 檔案以手動方式編輯，導致 XML 無效時，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="13f17-198">Typically, this happens when the XML files for the scheduled job are manually edited, resulting in invalid XML.</span></span>

<span data-ttu-id="13f17-199">當排程工作損毀時，PowerShell 會嘗試刪除排程工作、其執行歷程記錄，以及來自磁片的結果。</span><span class="sxs-lookup"><span data-stu-id="13f17-199">When a scheduled job is corrupted, PowerShell attempts to delete the scheduled job, its execution history, and its results from disk.</span></span>

<span data-ttu-id="13f17-200">如果無法移除排程工作，每次執行 Cmdlet 時，您都會收到損毀的工作錯誤訊息 `Get-ScheduledJob` 。</span><span class="sxs-lookup"><span data-stu-id="13f17-200">If it cannot remove the scheduled job, you will get a corrupted job error message each time you run the `Get-ScheduledJob` cmdlet.</span></span>

<span data-ttu-id="13f17-201">若要移除損毀的排程工作，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="13f17-201">To remove a corrupted scheduled job, use either one of the following methods:</span></span>

<span data-ttu-id="13f17-202">刪除 `<ScheduledJobName>` 排程工作的目錄。</span><span class="sxs-lookup"><span data-stu-id="13f17-202">Delete the `<ScheduledJobName>` directory for the scheduled job.</span></span> <span data-ttu-id="13f17-203">請勿刪除 **register-scheduledjob** 目錄。</span><span class="sxs-lookup"><span data-stu-id="13f17-203">Don't delete the **ScheduledJob** directory.</span></span>

<span data-ttu-id="13f17-204">目錄的位置：</span><span class="sxs-lookup"><span data-stu-id="13f17-204">The directory's location:</span></span>

`$env:UserProfile\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

<span data-ttu-id="13f17-205">例如：</span><span class="sxs-lookup"><span data-stu-id="13f17-205">For example:</span></span>

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>.`

<span data-ttu-id="13f17-206">使用工作排程器來刪除排程工作。</span><span class="sxs-lookup"><span data-stu-id="13f17-206">Use Task Scheduler to delete the scheduled job.</span></span> <span data-ttu-id="13f17-207">PowerShell 排程工作會出現在下列工作排程器路徑中：</span><span class="sxs-lookup"><span data-stu-id="13f17-207">PowerShell scheduled tasks appear in the following Task Scheduler path:</span></span>

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

## <a name="job-cmdlets-cant-consistently-find-scheduled-jobs"></a><span data-ttu-id="13f17-208">作業 Cmdlet 無法一致地找到排程工作</span><span class="sxs-lookup"><span data-stu-id="13f17-208">Job cmdlets can't consistently find scheduled jobs</span></span>

<span data-ttu-id="13f17-209">當 **PSScheduledJob** 模組不在目前的會話中時，作業 Cmdlet 無法取得排程的工作、啟動它們或取得其結果。</span><span class="sxs-lookup"><span data-stu-id="13f17-209">When the **PSScheduledJob** module isn't in the current session, the job cmdlets cannot get scheduled jobs, start them, or get their results.</span></span>

<span data-ttu-id="13f17-210">若要匯入 **PSScheduledJob** 模組，請 `Import-Module PSScheduledJob` 在模組中輸入或執行或取得任何 Cmdlet，例如 `Get-ScheduledJob` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="13f17-210">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or run or get any cmdlet in the module, such as the `Get-ScheduledJob` cmdlet.</span></span>
<span data-ttu-id="13f17-211">從 PowerShell 3.0 開始，當您取得或使用模組中的任何 Cmdlet 時，會自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="13f17-211">Beginning in PowerShell 3.0, modules are imported automatically when you get or use any cmdlet in the module.</span></span>

<span data-ttu-id="13f17-212">當 **PSScheduledJob** 模組不在目前的會話中時，可能會有下列命令順序。</span><span class="sxs-lookup"><span data-stu-id="13f17-212">When the **PSScheduledJob** module isn't in the current session, the following command sequence is possible.</span></span>

```powershell
Get-Job ProcessJob
```

```Output
Get-Job : The command cannot find the job because the job name
ProcessJob was not found.
Verify the value of the Name parameter, and then try the command again.
+ CategoryInfo          : ObjectNotFound: (ProcessJob:String) [Get-Job],
PSArgumentException
+ FullyQualifiedErrorId : JobWithSpecifiedNameNotFound,Microsoft.PowerShell.
Commands.GetJobCommand
```

```powershell
Get-Job
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command      Enabled
--         ----            --------        -------      -------
4          ProcessJob      {1}             Get-Process  True
```

```powershell
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State       HasMoreData     Location
--     ----         -------------   -----       -----------     --------
43     ProcessJob   PSScheduledJob  Completed   True            localhost
44     ProcessJob   PSScheduledJob  Completed   True            localhost
45     ProcessJob   PSScheduledJob  Completed   True            localhost
46     ProcessJob   PSScheduledJob  Completed   True            localhost
47     ProcessJob   PSScheduledJob  Completed   True            localhost
48     ProcessJob   PSScheduledJob  Completed   True            localhost
49     ProcessJob   PSScheduledJob  Completed   True            localhost
50     ProcessJob   PSScheduledJob  Completed   True            localhost
```

<span data-ttu-id="13f17-213">發生此行為的原因是 `Get-ScheduledJob` 命令自動匯入 **PSScheduledJob** 模組，然後執行命令。</span><span class="sxs-lookup"><span data-stu-id="13f17-213">This behavior occurs because the `Get-ScheduledJob` command automatically imports the **PSScheduledJob** module, and then runs the command.</span></span>

## <a name="see-also"></a><span data-ttu-id="13f17-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13f17-214">See also</span></span>

[<span data-ttu-id="13f17-215">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="13f17-215">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="13f17-216">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="13f17-216">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="13f17-217">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="13f17-217">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

<span data-ttu-id="13f17-218">[PSScheduledJob](xref:PSScheduledJob) 模組 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="13f17-218">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="13f17-219">工作排程器</span><span class="sxs-lookup"><span data-stu-id="13f17-219">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
