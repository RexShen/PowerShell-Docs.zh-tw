---
ms.date: 10/30/2018
keywords: dsc,powershell,設定,安裝
title: 疑難排解 DSC
description: 此文章提供常見錯誤的疑難排解指示。
ms.openlocfilehash: 2ac86689fa2695add247995bfb91c0ea85e22d60
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656254"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="5d8a9-104">疑難排解 DSC</span><span class="sxs-lookup"><span data-stu-id="5d8a9-104">Troubleshooting DSC</span></span>

> <span data-ttu-id="5d8a9-105">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5d8a9-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5d8a9-106">此文章提供常見錯誤的疑難排解指示。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-106">This article provides troubleshooting instruction for common errors.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="5d8a9-107">WinRM 相依性</span><span class="sxs-lookup"><span data-stu-id="5d8a9-107">WinRM Dependency</span></span>

<span data-ttu-id="5d8a9-108">Windows PowerShell 預期狀態設定 (DSC) 取決於 WinRM。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-108">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="5d8a9-109">在 Windows Server 2008 R2 和 Windows 7 上預設不啟用 WinRM。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-109">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="5d8a9-110">若要啟用 WinRM，請在 Windows PowerShell 提高權限的工作階段中，執行 `Set-WSManQuickConfig`。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-110">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="5d8a9-111">使用 Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="5d8a9-111">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="5d8a9-112">[Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) Cmdlet 會從目標節點取得設定狀態的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-112">The [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="5d8a9-113">高級物件已傳回，此物件包含關於設定是否順利執行的高等級資訊。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-113">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="5d8a9-114">您可以深入了解此物件，以探索有關設定執行的詳細資料，例如︰</span><span class="sxs-lookup"><span data-stu-id="5d8a9-114">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="5d8a9-115">所有失敗的資源</span><span class="sxs-lookup"><span data-stu-id="5d8a9-115">All of the resources that failed</span></span>
- <span data-ttu-id="5d8a9-116">要求重新開機的任何資源</span><span class="sxs-lookup"><span data-stu-id="5d8a9-116">Any resource that requested a reboot</span></span>
- <span data-ttu-id="5d8a9-117">在設定執行時中繼設定的設定</span><span class="sxs-lookup"><span data-stu-id="5d8a9-117">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="5d8a9-118">等。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-118">Etc.</span></span>

<span data-ttu-id="5d8a9-119">下列的參數集傳回上次設定執行時的狀態資訊︰</span><span class="sxs-lookup"><span data-stu-id="5d8a9-119">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

<span data-ttu-id="5d8a9-120">下列的參數集傳回所有先前設定執行時的狀態資訊︰</span><span class="sxs-lookup"><span data-stu-id="5d8a9-120">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="5d8a9-121">範例</span><span class="sxs-lookup"><span data-stu-id="5d8a9-121">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ResourceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="5d8a9-122">我的指令碼不執行：使用 DSC 記錄診斷指令碼錯誤</span><span class="sxs-lookup"><span data-stu-id="5d8a9-122">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="5d8a9-123">像所有的 Windows 軟體一樣，DSC 會在[記錄](/windows/desktop/EventLog/about-event-logging)中記錄錯誤和事件，並可從[事件檢視器](https://support.microsoft.com/hub/4338813/windows-help)加以檢視。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-123">Like all Windows software, DSC records errors and events in [logs](/windows/desktop/EventLog/about-event-logging) that can be viewed from the [Event Viewer](https://support.microsoft.com/hub/4338813/windows-help).</span></span> <span data-ttu-id="5d8a9-124">檢查這些記錄檔可以幫助您了解特定作業失敗的原因，以及如何避免失敗再度發生。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-124">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span>
<span data-ttu-id="5d8a9-125">撰寫設定指令碼可能很困難，因此為方便您在撰寫時追蹤錯誤，請使用 DSC 記錄資源在 DSC 分析事件記錄檔中追蹤設定進度。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-125">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="5d8a9-126">DSC 事件記錄檔在哪裡？</span><span class="sxs-lookup"><span data-stu-id="5d8a9-126">Where are DSC event logs?</span></span>

<span data-ttu-id="5d8a9-127">在事件檢視器中，DSC 事件位於： **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span><span class="sxs-lookup"><span data-stu-id="5d8a9-127">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="5d8a9-128">您也可以執行對應的 PowerShell Cmdlet [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)，來檢視事件記錄檔：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-128">The corresponding PowerShell cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="5d8a9-129">如上所示，DSC 的主要記錄檔名稱是 **Microsoft->Windows->DSC** (為畫面簡潔起見，這裡不顯示 Windows 下的其他記錄檔名稱)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-129">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="5d8a9-130">主要名稱會附加在通道名稱後面，以建立完整的記錄檔名稱。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-130">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="5d8a9-131">DSC 引擎主要會寫入三種記錄：[作業、分析和偵錯記錄](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11))。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-131">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span></span>
<span data-ttu-id="5d8a9-132">因為分析和偵錯記錄檔預設是關閉的，您應該在 [事件檢視器] 中啟用它們。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-132">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span>
<span data-ttu-id="5d8a9-133">啟用方法是在 Windows PowerShell 中輸入 Show-EventLog；或依序按一下 [開始] 按鈕、[控制台]、[系統管理工具] 和 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-133">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel** , click **Administrative Tools** , and then click **Event Viewer**.</span></span> <span data-ttu-id="5d8a9-134">在事件檢視器的 [檢視] 功能表中，按一下 [顯示分析與偵錯記錄]。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-134">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="5d8a9-135">分析通道的記錄名稱是 **Microsoft-Windows-Dsc/Analytic** ，偵錯通道則是 **Microsoft-Windows-Dsc/Debug** 。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-135">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic** , and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="5d8a9-136">您也可以使用 [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) 公用程式來啟用記錄，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-136">You could also use the [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="5d8a9-137">DSC 記錄檔包含哪些內容？</span><span class="sxs-lookup"><span data-stu-id="5d8a9-137">What do DSC logs contain?</span></span>

<span data-ttu-id="5d8a9-138">DSC 記錄檔會根據訊息的重要性分成三個記錄檔通道。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-138">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="5d8a9-139">DSC 的作業記錄檔包含所有錯誤訊息，可用來識別問題。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-139">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="5d8a9-140">分析記錄檔掌握巨量的事件，可以識別錯誤發生的位置。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-140">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="5d8a9-141">這個通道也包含詳細資訊訊息 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-141">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="5d8a9-142">偵錯記錄檔包含的記錄可以幫助您了解錯誤是如何發生的。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-142">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="5d8a9-143">DSC 事件訊息的結構為，每個事件訊息的開頭都是唯一代表 DSC 作業的工作識別碼。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-143">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="5d8a9-144">下例嘗試取得記入作業 DSC 記錄檔的第一筆事件的訊息。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-144">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="5d8a9-145">DSC 事件的特定記錄結構，能讓使用者彙總一個 DSC 工作的事件。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-145">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="5d8a9-146">其結構如下所示：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-146">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="5d8a9-147">收集單一 DSC 作業的事件</span><span class="sxs-lookup"><span data-stu-id="5d8a9-147">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="5d8a9-148">DSC 事件記錄檔包含各種 DSC 作業產生的事件。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-148">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="5d8a9-149">不過，您通常只關心某個特定作業的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-149">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="5d8a9-150">DSC 的所有記錄都是依照每個 DSC 作業的唯一工作識別碼屬性分組 。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-150">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="5d8a9-151">所有 DSC 事件的第一個屬性值都是顯示工作識別碼。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-151">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="5d8a9-152">下列步驟說明如何將所有事件累計到分組的陣列結構中。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-152">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

<span data-ttu-id="5d8a9-153">在此，變數 `$SeparateDscOperations` 包含依工作識別碼分組的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-153">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="5d8a9-154">這個變數的每個陣列元素都代表一組依照不同 DSC 作業記錄的事件，讓您存取有關記錄檔的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-154">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....

PS C:\> $SeparateDscOperations[0].Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

<span data-ttu-id="5d8a9-155">您可以使用 [Where-Object](/powershell/module/microsoft.powershell.core/where-object) 擷取變數 `$SeparateDscOperations` 中的資料。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-155">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span> <span data-ttu-id="5d8a9-156">下面有五個案例，您要擷取其資料以疑難排解 DSC：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-156">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="5d8a9-157">1：作業失敗</span><span class="sxs-lookup"><span data-stu-id="5d8a9-157">1: Operations failures</span></span>

<span data-ttu-id="5d8a9-158">所有的事件都有[嚴重性等級](/windows/desktop/WES/defining-severity-levels)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-158">All events have [severity levels](/windows/desktop/WES/defining-severity-levels).</span></span> <span data-ttu-id="5d8a9-159">這項資訊可以用來識別錯誤事件：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-159">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="5d8a9-160">2：過去半小時內執行的作業詳細資料</span><span class="sxs-lookup"><span data-stu-id="5d8a9-160">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="5d8a9-161">`TimeCreated` 是每個 Windows 事件都有的屬性，指出事件的建立時間。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-161">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="5d8a9-162">比較這個屬性和特定的日期/時間物件，可用以篩選所有事件：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-162">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="5d8a9-163">3：最新作業的訊息</span><span class="sxs-lookup"><span data-stu-id="5d8a9-163">3: Messages from the latest operation</span></span>

<span data-ttu-id="5d8a9-164">最新的作業會儲存在陣列群組 `$SeparateDscOperations` 的第一個索引中。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-164">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="5d8a9-165">查詢索引 0 的群組訊息會傳回最新作業的所有訊息：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-165">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

```powershell
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="5d8a9-166">4：近期的作業失敗錯誤訊息記錄</span><span class="sxs-lookup"><span data-stu-id="5d8a9-166">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="5d8a9-167">`$SeparateDscOperations[0].Group` 包含最新作業的事件集。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-167">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="5d8a9-168">執行 `Where-Object` Cmdlet 會根據層級顯示名稱篩選事件。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-168">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="5d8a9-169">結果儲存在 `$myFailedEvent` 變數中，可進一步解析以取得事件訊息：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-169">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with
 -Path parameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="5d8a9-170">5：針對特定工作識別碼產生的所有事件。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-170">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="5d8a9-171">`$SeparateDscOperations` 是群組陣列，每一個都有和唯一工作識別碼相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-171">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="5d8a9-172">執行 `Where-Object` Cmdlet 就可以擷取這些有特定工作識別碼的事件群組：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-172">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="5d8a9-173">使用 xDscDiagnostics 分析 DSC 記錄</span><span class="sxs-lookup"><span data-stu-id="5d8a9-173">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="5d8a9-174">**xDscDiagnostics** 是 PowerShell 模組，由數個可協助分析電腦上 DSC 失敗的函數組成。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-174">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="5d8a9-175">這些函式可協助您識別過去 DSC 作業的所有本機事件，或 (具有效認證的) 遠端電腦的 DSC 事件。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-175">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="5d8a9-176">本文中，DSC 作業一詞是用來定義從開始到結束的單一唯一 DSC 執行。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-176">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="5d8a9-177">例如，`Test-DscConfiguration` 就會是另外一個 DSC 作業。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-177">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="5d8a9-178">同樣地，DSC 中每個其他的 Cmdlet (例如 `Get-DscConfiguration`、`Start-DscConfiguration` 等等) 各自都可能被視為個別的 DSC 作業。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-178">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="5d8a9-179">[xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics) 會說明函數。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-179">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="5d8a9-180">執行 `Get-Help <cmdlet name>` 即可取得說明。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-180">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="5d8a9-181">取得 DSC 作業的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="5d8a9-181">Getting details of DSC operations</span></span>

<span data-ttu-id="5d8a9-182">`Get-xDscOperation` 函數可讓您尋找在一或多部電腦上執行的 DSC 作業結果，並傳回物件，其中包含每個 DSC 作業產生的事件集合。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-182">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="5d8a9-183">例如，在下列輸出中，執行了三個命令。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-183">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="5d8a9-184">第一個成功，而其他兩個失敗了。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-184">The first one passed, and the other two failed.</span></span> <span data-ttu-id="5d8a9-185">這些結果會摘述在 `Get-xDscOperation` 輸出中。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-185">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="5d8a9-186">您也可以使用 `Newest` 參數指定只要最近作業的結果︰</span><span class="sxs-lookup"><span data-stu-id="5d8a9-186">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="5d8a9-187">取得 DSC 事件的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="5d8a9-187">Getting details of DSC events</span></span>

<span data-ttu-id="5d8a9-188">`Trace-xDscOperation` Cmdlet 傳回的物件包含了事件集合、其事件類型，以及從特定 DSC 作業產生的訊息輸出。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-188">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="5d8a9-189">一般而言，當您使用 `Get-xDscOperation` 在任何作業中發現失敗時，您都可以追蹤該作業，找出導致失敗的事件。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-189">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="5d8a9-190">使用 `SequenceID` 參數以取得特定電腦的特定作業事件。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-190">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="5d8a9-191">例如，`SequenceID` 如果指定為 9，則 `Trace-xDscOperaion` 就會取得上一個作業的第 9 筆 DSC 作業追蹤記錄︰</span><span class="sxs-lookup"><span data-stu-id="5d8a9-191">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

<span data-ttu-id="5d8a9-192">傳遞指派給特定 DSC 作業的 **GUID** (如 `Get-xDscOperation` Cmdlet 所傳回) 來取得該 DSC 作業的事件詳細資料：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-192">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmdlet) to get the event details for that DSC operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

<span data-ttu-id="5d8a9-193">請注意，由於 `Trace-xDscOperation` 會彙總分析、偵錯和作業記錄的事件，所以會提示您啟用這些記錄，如上文所述。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-193">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="5d8a9-194">此外，您也可以將 `Trace-xDscOperation` 的輸出存入變數中來收集事件相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-194">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="5d8a9-195">您可以使用下列命令來顯示特定 DSC 作業的所有事件。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-195">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="5d8a9-196">這和 `Get-WinEvent` Cmdlet 會顯示相同的結果，如以下輸出所示：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-196">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

<span data-ttu-id="5d8a9-197">理想的情況是先使用 `Get-xDscOperation` 列出電腦上執行的最新幾個 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-197">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="5d8a9-198">接著使用 `Trace-xDscOperation` 檢查任何單一作業 (使用其 SequenceID 或 JobID)，探索它在幕後的工作內容。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-198">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="5d8a9-199">取得遠端電腦的事件</span><span class="sxs-lookup"><span data-stu-id="5d8a9-199">Getting events for a remote computer</span></span>

<span data-ttu-id="5d8a9-200">使用 `Trace-xDscOperation` Cmdlet 的 `ComputerName` 參數來取得遠端電腦上的事件詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-200">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="5d8a9-201">執行這項作業之前，您必須先建立防火牆規則，允許在遠端電腦上進行遠端系統管理︰</span><span class="sxs-lookup"><span data-stu-id="5d8a9-201">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="5d8a9-202">現在，您可以在 `Trace-xDscOperation` 呼叫中指定該部電腦：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-202">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="5d8a9-203">我的資源不更新：如何重設快取</span><span class="sxs-lookup"><span data-stu-id="5d8a9-203">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="5d8a9-204">基於效率考量，DSC 引擎會快取實作為 PowerShell 模組的資源。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-204">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="5d8a9-205">不過，這可能會在撰寫並同時測試資源時造成問題，因為在程序重新啟動前，DSC 會載入快取的版本。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-205">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="5d8a9-206">讓 DSC 載入較新版本的唯一方法，是明確結束主控 DSC 引擎的程序。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-206">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="5d8a9-207">同樣地，當您執行 `Start-DscConfiguration`，在新增及修改自訂的資源後，可能要重新啟動電腦才會執行修改的內容。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-207">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="5d8a9-208">這是因為 DSC 是在 WMI 提供者主機處理程序 (WmiPrvSE) 中執行，通常一次會執行多個 WmiPrvSE 執行個體。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-208">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="5d8a9-209">當您重新開機時，主機處理程序就會重新啟動，而快取也會清除。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-209">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="5d8a9-210">若要順利回收設定和清除快取卻不重新開機，您必須停止然後再重新啟動主機處理程序。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-210">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="5d8a9-211">您可以對每個執行個體都執行識別、停止和重新啟動程序。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-211">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="5d8a9-212">或者如下文所示，使用 `DebugMode` 重新載入 PowerShell DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-212">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="5d8a9-213">若要識別出並停止每個執行個體上主控 DSC 引擎的處理程序，您可以列出主控 DSC 引擎的 WmiPrvSE 處理程序識別碼。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-213">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="5d8a9-214">然後，更新提供者、使用下列命令停止 WmiPrvSE 處理程序，再執行一次 **Start-DscConfiguration** 。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-214">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a><span data-ttu-id="5d8a9-215">使用 DebugMode</span><span class="sxs-lookup"><span data-stu-id="5d8a9-215">Using DebugMode</span></span>

<span data-ttu-id="5d8a9-216">您可以設定 DSC 本機設定管理員 (LCM) 使用 `DebugMode` 在重新啟動主機處理程序時，一律清除快取。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-216">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="5d8a9-217">設為 **TRUE** 時，會讓引擎一律重新載入 PowerShell DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-217">When set to **TRUE** , it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="5d8a9-218">資源完成撰寫後，您就可以將其設回 **FALSE** ，引擎會還原成快取模組行為。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-218">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="5d8a9-219">下面的示範會說明 `DebugMode` 如何自動重新整理快取。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-219">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="5d8a9-220">首先，我們來看一下預設設定：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-220">First, let's look at the default configuration:</span></span>

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

<span data-ttu-id="5d8a9-221">您可以看到 `DebugMode` 設為 **"None"** 。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-221">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="5d8a9-222">若要安裝 `DebugMode` 示範，請使用下列 PowerShell 資源：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-222">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

<span data-ttu-id="5d8a9-223">現在，使用上述資源中的 `TestProviderDebugMode` 來撰寫設定：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-223">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

<span data-ttu-id="5d8a9-224">您將會看到檔案的內容：`$env:SystemDrive\OutputFromTestProviderDebugMode.txt` 是 **1** 。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-224">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="5d8a9-225">現在使用下列指令碼來更新提供者程式碼：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-225">Now, update the provider code using the following script:</span></span>

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

<span data-ttu-id="5d8a9-226">這個指令碼會產生一個隨機數字，以此更新提供者程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-226">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="5d8a9-227">在將 `DebugMode` 設定為 False 的情況下，`$env:SystemDrive\OutputFromTestProviderDebugMode.txt` 檔案的內容一律不會變更。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-227">With `DebugMode` set to false, the contents of the file `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` are never changed.</span></span>

<span data-ttu-id="5d8a9-228">現在，在設定指令碼中將 `DebugMode` 設為 **"ForceModuleImport"** ：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-228">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="5d8a9-229">當您再次執行上述指令碼時，會看到檔案的內容每次都不同。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-229">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="5d8a9-230">(您可以執行 `Get-DscConfiguration` 檢查它)。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-230">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="5d8a9-231">以下是另外兩次的執行結果 (執行指令碼時您的結果可能不同)：</span><span class="sxs-lookup"><span data-stu-id="5d8a9-231">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="dsc-returns-unexpected-response-code-internalservererror-when-registering-with-windows-pull-server"></a><span data-ttu-id="5d8a9-232">DSC 向 Windows 提取伺服器註冊時，傳回了「未預期的回應碼 InternalServerError」</span><span class="sxs-lookup"><span data-stu-id="5d8a9-232">DSC returns "unexpected response code InternalServerError" when registering with Windows Pull Server</span></span>

<span data-ttu-id="5d8a9-233">將中繼設定套用至伺服器，以向 Windows 提取伺服器的執行個體註冊時，您可能會發生下列錯誤。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-233">When applying a metaconfiguration to a server to register it with an instance of Windows Pull Server, you might encounter the following error.</span></span>

```
Registration of the Dsc Agent with the server https://<serverfqdn>:8080/PSDSCPullServer.svc failed. The underlying error is: The attempt to register Dsc Agent with AgentId <ID> with the server
https://<serverfqdn>:8080/PSDSCPullServer.svc/Nodes(AgentId='<ID>') returned unexpected response code InternalServerError. .
    + CategoryInfo          : InvalidResult: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : RegisterDscAgentUnsuccessful,Microsoft.PowerShell.DesiredStateConfiguration.Commands.RegisterDscAgentCommand
    + PSComputerName        : <computername>
```

<span data-ttu-id="5d8a9-234">當伺服器上用來加密流量的憑證通用名稱 (CN) 與節點用來解析 URL 的 DNS 名稱不同時，就可能發生此問題。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-234">This can occur when the certificate used on the server to encrypt traffic has a common name (CN) that is different than the DNS name used by the node to resolve the URL.</span></span> <span data-ttu-id="5d8a9-235">更新 Windows 提取伺服器執行個體，以使用名稱經更正的憑證。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-235">Update the Windows Pull Server instance to use a certificate with a corrected name.</span></span>

## <a name="error-when-running-sysprep-after-applying-a-dsc-configuration"></a><span data-ttu-id="5d8a9-236">在套用 DSC 組態後，執行 Sysprep 時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="5d8a9-236">Error when running Sysprep after applying a DSC Configuration</span></span>

<span data-ttu-id="5d8a9-237">在套用 DSC 組態後，嘗試執行 Sysprep 將 Windows Server 一般化時，您可能會遇到下列錯誤。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-237">When attempting to run Sysprep to generalize a Windows Server after applying a DSC configuration, you might encounter the following error.</span></span>

```
SYSPRP LaunchDll:Failure occurred while executing 'DscCore.dll,SysPrep_Cleanup', returned error code 0x2
```

<span data-ttu-id="5d8a9-238">不支援在使用 Windows PowerShell Desired State Configuration 設定伺服器後將伺服器一般化。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-238">Generalizing a server after it has been configured using Windows PowerShell Desired State Configuration is not a supported scenario.</span></span> <span data-ttu-id="5d8a9-239">請改為在 Windows 安裝程式的特殊化階段完成之後，將組態套用至 Windows。</span><span class="sxs-lookup"><span data-stu-id="5d8a9-239">Instead, apply configurations to Windows after the Specialize phase of Windows Setup has completed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d8a9-240">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d8a9-240">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="5d8a9-241">概念</span><span class="sxs-lookup"><span data-stu-id="5d8a9-241">Concepts</span></span>

- [<span data-ttu-id="5d8a9-242">建置自訂的 Windows PowerShell 預期狀態設定資源</span><span class="sxs-lookup"><span data-stu-id="5d8a9-242">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](../resources/authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="5d8a9-243">其他資源</span><span class="sxs-lookup"><span data-stu-id="5d8a9-243">Other Resources</span></span>

- [<span data-ttu-id="5d8a9-244">Windows PowerShell 預期狀態設定 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5d8a9-244">Windows PowerShell Desired State Configuration Cmdlets</span></span>](/powershell/module/psdesiredstateconfiguration/)
