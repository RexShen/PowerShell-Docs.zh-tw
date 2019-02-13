---
ms.date: 10/30/2018
keywords: dsc,powershell,設定,安裝
title: 疑難排解 DSC
ms.openlocfilehash: e1f36bbc97569ac0d65f003ee08f52ec174a4520
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676704"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="453f6-103">疑難排解 DSC</span><span class="sxs-lookup"><span data-stu-id="453f6-103">Troubleshooting DSC</span></span>

<span data-ttu-id="453f6-104">_適用於：Windows PowerShell 4.0、Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="453f6-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="453f6-105">本主題會說明問題發生時針對 DSC 進行疑難排解的方法。</span><span class="sxs-lookup"><span data-stu-id="453f6-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="453f6-106">WinRM 相依性</span><span class="sxs-lookup"><span data-stu-id="453f6-106">WinRM Dependency</span></span>

<span data-ttu-id="453f6-107">Windows PowerShell 預期狀態設定 (DSC) 取決於 WinRM。</span><span class="sxs-lookup"><span data-stu-id="453f6-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="453f6-108">在 Windows Server 2008 R2 和 Windows 7 上預設不啟用 WinRM。</span><span class="sxs-lookup"><span data-stu-id="453f6-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="453f6-109">若要啟用 WinRM，請在 Windows PowerShell 提高權限的工作階段中，執行 `Set-WSManQuickConfig`。</span><span class="sxs-lookup"><span data-stu-id="453f6-109">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="453f6-110">使用 Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="453f6-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="453f6-111">[Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) Cmdlet 會從目標節點取得設定狀態的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="453f6-111">The [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="453f6-112">高級物件已傳回，此物件包含關於設定是否順利執行的高等級資訊。</span><span class="sxs-lookup"><span data-stu-id="453f6-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="453f6-113">您可以深入了解此物件，以探索有關設定執行的詳細資料，例如︰</span><span class="sxs-lookup"><span data-stu-id="453f6-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="453f6-114">所有失敗的資源</span><span class="sxs-lookup"><span data-stu-id="453f6-114">All of the resources that failed</span></span>
- <span data-ttu-id="453f6-115">要求重新開機的任何資源</span><span class="sxs-lookup"><span data-stu-id="453f6-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="453f6-116">在設定執行時中繼設定的設定</span><span class="sxs-lookup"><span data-stu-id="453f6-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="453f6-117">等。</span><span class="sxs-lookup"><span data-stu-id="453f6-117">Etc.</span></span>

<span data-ttu-id="453f6-118">下列的參數集傳回上次設定執行時的狀態資訊︰</span><span class="sxs-lookup"><span data-stu-id="453f6-118">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
<span data-ttu-id="453f6-119">下列的參數集傳回所有先前設定執行時的狀態資訊︰</span><span class="sxs-lookup"><span data-stu-id="453f6-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="453f6-120">範例</span><span class="sxs-lookup"><span data-stu-id="453f6-120">Example</span></span>

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
ReosurceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="453f6-121">我的指令碼將不會執行：使用 DSC 記錄診斷指令碼錯誤</span><span class="sxs-lookup"><span data-stu-id="453f6-121">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="453f6-122">像所有的 Windows 軟體一樣，DSC 會在[記錄檔](/windows/desktop/EventLog/about-event-logging)中記錄錯誤和事件，[[事件檢視器]](https://support.microsoft.com/hub/4338813/windows-help) 可檢視這些記錄。</span><span class="sxs-lookup"><span data-stu-id="453f6-122">Like all Windows software, DSC records errors and events in [logs](/windows/desktop/EventLog/about-event-logging) that can be viewed from the [Event Viewer](https://support.microsoft.com/hub/4338813/windows-help).</span></span>
<span data-ttu-id="453f6-123">檢查這些記錄檔可以幫助您了解特定作業失敗的原因，以及如何避免失敗再度發生。</span><span class="sxs-lookup"><span data-stu-id="453f6-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="453f6-124">撰寫設定指令碼可能很困難，因此為方便您在撰寫時追蹤錯誤，請使用 DSC 記錄資源在 DSC 分析事件記錄檔中追蹤設定進度。</span><span class="sxs-lookup"><span data-stu-id="453f6-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="453f6-125">DSC 事件記錄檔在哪裡？</span><span class="sxs-lookup"><span data-stu-id="453f6-125">Where are DSC event logs?</span></span>

<span data-ttu-id="453f6-126">在事件檢視器中，DSC 事件位於：**應用程式和服務記錄檔/Microsoft/Windows/Desired State Configuration**</span><span class="sxs-lookup"><span data-stu-id="453f6-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="453f6-127">您也可以執行對應的 PowerShell Cmdlet，[Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)，來檢視事件記錄檔：</span><span class="sxs-lookup"><span data-stu-id="453f6-127">The corresponding PowerShell cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="453f6-128">如上所示，DSC 的主要記錄檔名稱是 **Microsoft->Windows->DSC** (為畫面簡潔起見，這裡不顯示 Windows 下的其他記錄檔名稱)。</span><span class="sxs-lookup"><span data-stu-id="453f6-128">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="453f6-129">主要名稱會附加在通道名稱後面，以建立完整的記錄檔名稱。</span><span class="sxs-lookup"><span data-stu-id="453f6-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="453f6-130">DSC 引擎主要會寫入三種類型的記錄檔：[操作、 分析和偵錯記錄檔](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11))。</span><span class="sxs-lookup"><span data-stu-id="453f6-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span></span> <span data-ttu-id="453f6-131">因為分析和偵錯記錄檔預設是關閉的，您應該在 [事件檢視器] 中啟用它們。</span><span class="sxs-lookup"><span data-stu-id="453f6-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="453f6-132">啟用方法是在 Windows PowerShell 中輸入 Show-EventLog；或依序按一下 **[開始]** 按鈕、**[控制台]**、**[系統管理工具]** 和 **[事件檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="453f6-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span>
<span data-ttu-id="453f6-133">在 [事件檢視器] 的 **[檢視]** 功能表中，按一下 **[顯示分析與偵錯記錄檔]**。</span><span class="sxs-lookup"><span data-stu-id="453f6-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="453f6-134">分析通道的記錄檔名稱是 **Microsoft-Windows-Dsc/Analytic**，偵錯通道則是 **Microsoft-Windows-Dsc/Debug**。</span><span class="sxs-lookup"><span data-stu-id="453f6-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="453f6-135">您也可以使用 [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) 公用程式來啟用記錄檔，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="453f6-135">You could also use the [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="453f6-136">DSC 記錄檔包含哪些內容？</span><span class="sxs-lookup"><span data-stu-id="453f6-136">What do DSC logs contain?</span></span>

<span data-ttu-id="453f6-137">DSC 記錄檔會根據訊息的重要性分成三個記錄檔通道。</span><span class="sxs-lookup"><span data-stu-id="453f6-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="453f6-138">DSC 的作業記錄檔包含所有錯誤訊息，可用來識別問題。</span><span class="sxs-lookup"><span data-stu-id="453f6-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="453f6-139">分析記錄檔掌握巨量的事件，可以識別錯誤發生的位置。</span><span class="sxs-lookup"><span data-stu-id="453f6-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="453f6-140">這個通道也包含詳細資訊訊息 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="453f6-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="453f6-141">偵錯記錄檔包含的記錄可以幫助您了解錯誤是如何發生的。</span><span class="sxs-lookup"><span data-stu-id="453f6-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="453f6-142">DSC 事件訊息的結構為，每個事件訊息的開頭都是唯一代表 DSC 作業的工作識別碼。</span><span class="sxs-lookup"><span data-stu-id="453f6-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="453f6-143">下例嘗試取得記入作業 DSC 記錄檔的第一筆事件的訊息。</span><span class="sxs-lookup"><span data-stu-id="453f6-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="453f6-144">DSC 事件的特定記錄結構，能讓使用者彙總一個 DSC 工作的事件。</span><span class="sxs-lookup"><span data-stu-id="453f6-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="453f6-145">結構如下：</span><span class="sxs-lookup"><span data-stu-id="453f6-145">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="453f6-146">收集單一 DSC 作業的事件</span><span class="sxs-lookup"><span data-stu-id="453f6-146">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="453f6-147">DSC 事件記錄檔包含各種 DSC 作業產生的事件。</span><span class="sxs-lookup"><span data-stu-id="453f6-147">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="453f6-148">不過，您通常只關心某個特定作業的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="453f6-148">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="453f6-149">DSC 的所有記錄都是依照每個 DSC 作業的唯一工作識別碼屬性分組 。</span><span class="sxs-lookup"><span data-stu-id="453f6-149">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="453f6-150">所有 DSC 事件的第一個屬性值都是顯示工作識別碼。</span><span class="sxs-lookup"><span data-stu-id="453f6-150">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="453f6-151">下列步驟說明如何將所有事件累計到分組的陣列結構中。</span><span class="sxs-lookup"><span data-stu-id="453f6-151">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

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

<span data-ttu-id="453f6-152">在此，變數 `$SeparateDscOperations` 包含依工作識別碼分組的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="453f6-152">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="453f6-153">這個變數的每個陣列元素都代表一組依照不同 DSC 作業記錄的事件，讓您存取有關記錄檔的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="453f6-153">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

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

<span data-ttu-id="453f6-154">您可以使用 [Where-Object](/powershell/module/microsoft.powershell.core/where-object) 擷取變數 `$SeparateDscOperations` 中的資料。</span><span class="sxs-lookup"><span data-stu-id="453f6-154">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span> <span data-ttu-id="453f6-155">下面有五個案例，您要擷取其資料以疑難排解 DSC：</span><span class="sxs-lookup"><span data-stu-id="453f6-155">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="453f6-156">1：作業失敗</span><span class="sxs-lookup"><span data-stu-id="453f6-156">1: Operations failures</span></span>

<span data-ttu-id="453f6-157">所有的事件都有[嚴重性層級](/windows/desktop/WES/defining-severity-levels)。</span><span class="sxs-lookup"><span data-stu-id="453f6-157">All events have [severity levels](/windows/desktop/WES/defining-severity-levels).</span></span> <span data-ttu-id="453f6-158">這項資訊可以用來識別錯誤事件：</span><span class="sxs-lookup"><span data-stu-id="453f6-158">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="453f6-159">2：過去半小時內執行的作業詳細資料</span><span class="sxs-lookup"><span data-stu-id="453f6-159">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="453f6-160">`TimeCreated` 是每個 Windows 事件都有的屬性，指出事件的建立時間。</span><span class="sxs-lookup"><span data-stu-id="453f6-160">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="453f6-161">比較這個屬性和特定的日期/時間物件，可用以篩選所有事件：</span><span class="sxs-lookup"><span data-stu-id="453f6-161">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="453f6-162">3：最新作業的訊息</span><span class="sxs-lookup"><span data-stu-id="453f6-162">3: Messages from the latest operation</span></span>

<span data-ttu-id="453f6-163">最新的作業會儲存在陣列群組 `$SeparateDscOperations` 的第一個索引中。</span><span class="sxs-lookup"><span data-stu-id="453f6-163">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="453f6-164">查詢索引 0 的群組訊息會傳回最新作業的所有訊息：</span><span class="sxs-lookup"><span data-stu-id="453f6-164">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

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

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="453f6-165">4：近期的作業失敗錯誤訊息記錄</span><span class="sxs-lookup"><span data-stu-id="453f6-165">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="453f6-166">`$SeparateDscOperations[0].Group` 包含最新作業的事件集。</span><span class="sxs-lookup"><span data-stu-id="453f6-166">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="453f6-167">執行 `Where-Object` Cmdlet 會根據層級顯示名稱篩選事件。</span><span class="sxs-lookup"><span data-stu-id="453f6-167">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="453f6-168">結果儲存在 `$myFailedEvent` 變數中，可進一步解析以取得事件訊息：</span><span class="sxs-lookup"><span data-stu-id="453f6-168">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="453f6-169">5：針對特定工作識別碼產生的所有事件。</span><span class="sxs-lookup"><span data-stu-id="453f6-169">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="453f6-170">`$SeparateDscOperations` 是群組陣列，每一個都有和唯一工作識別碼相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="453f6-170">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="453f6-171">執行 `Where-Object` Cmdlet 就可以擷取這些有特定工作識別碼的事件群組：</span><span class="sxs-lookup"><span data-stu-id="453f6-171">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

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

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="453f6-172">使用 xDscDiagnostics 分析 DSC 記錄</span><span class="sxs-lookup"><span data-stu-id="453f6-172">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="453f6-173">**xDscDiagnostics** 是 PowerShell 模組，由數個可協助分析電腦上 DSC 失敗的函數組成。</span><span class="sxs-lookup"><span data-stu-id="453f6-173">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="453f6-174">這些函式可協助您識別過去 DSC 作業的所有本機事件，或 (具有效認證的) 遠端電腦的 DSC 事件。</span><span class="sxs-lookup"><span data-stu-id="453f6-174">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="453f6-175">本文中，DSC 作業一詞是用來定義從開始到結束的單一唯一 DSC 執行。</span><span class="sxs-lookup"><span data-stu-id="453f6-175">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="453f6-176">例如，`Test-DscConfiguration` 就會是另外一個 DSC 作業。</span><span class="sxs-lookup"><span data-stu-id="453f6-176">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="453f6-177">同樣地，DSC 中每個其他的 Cmdlet (例如 `Get-DscConfiguration`、`Start-DscConfiguration` 等等) 各自都可能被視為個別的 DSC 作業。</span><span class="sxs-lookup"><span data-stu-id="453f6-177">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="453f6-178">[xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics) 會說明函數。</span><span class="sxs-lookup"><span data-stu-id="453f6-178">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="453f6-179">執行 `Get-Help <cmdlet name>` 即可取得說明。</span><span class="sxs-lookup"><span data-stu-id="453f6-179">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="453f6-180">取得 DSC 作業的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="453f6-180">Getting details of DSC operations</span></span>

<span data-ttu-id="453f6-181">`Get-xDscOperation` 函數可讓您尋找在一或多部電腦上執行的 DSC 作業結果，並傳回物件，其中包含每個 DSC 作業產生的事件集合。</span><span class="sxs-lookup"><span data-stu-id="453f6-181">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="453f6-182">例如，在下列輸出中，執行了三個命令。</span><span class="sxs-lookup"><span data-stu-id="453f6-182">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="453f6-183">第一個成功，而其他兩個失敗了。</span><span class="sxs-lookup"><span data-stu-id="453f6-183">The first one passed, and the other two failed.</span></span> <span data-ttu-id="453f6-184">這些結果會摘述在 `Get-xDscOperation` 輸出中。</span><span class="sxs-lookup"><span data-stu-id="453f6-184">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="453f6-185">您也可以使用 `Newest` 參數指定只要最近作業的結果︰</span><span class="sxs-lookup"><span data-stu-id="453f6-185">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

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

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="453f6-186">取得 DSC 事件的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="453f6-186">Getting details of DSC events</span></span>

<span data-ttu-id="453f6-187">`Trace-xDscOperation` Cmdlet 傳回的物件包含了事件集合、其事件類型，以及從特定 DSC 作業產生的訊息輸出。</span><span class="sxs-lookup"><span data-stu-id="453f6-187">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="453f6-188">一般而言，當您使用 `Get-xDscOperation` 在任何作業中發現失敗時，您都可以追蹤該作業，找出導致失敗的事件。</span><span class="sxs-lookup"><span data-stu-id="453f6-188">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="453f6-189">使用 `SequenceID` 參數以取得特定電腦的特定作業事件。</span><span class="sxs-lookup"><span data-stu-id="453f6-189">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="453f6-190">例如，`SequenceID` 如果指定為 9，則 `Trace-xDscOperaion` 就會取得上一個作業的第 9 筆 DSC 作業追蹤記錄︰</span><span class="sxs-lookup"><span data-stu-id="453f6-190">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

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

<span data-ttu-id="453f6-191">傳遞**GUID**指派給特定的 DSC 作業 (如所傳回`Get-xDscOperation`cmdlet) 來取得該 DSC 作業的事件詳細資料：</span><span class="sxs-lookup"><span data-stu-id="453f6-191">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmdlet) to get the event details for that DSC operation:</span></span>

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

<span data-ttu-id="453f6-192">請注意，由於 `Trace-xDscOperation` 會彙總分析、偵錯和作業記錄的事件，所以會提示您啟用這些記錄，如上文所述。</span><span class="sxs-lookup"><span data-stu-id="453f6-192">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="453f6-193">此外，您也可以將 `Trace-xDscOperation` 的輸出存入變數中來收集事件相關資訊。</span><span class="sxs-lookup"><span data-stu-id="453f6-193">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="453f6-194">您可以使用下列命令來顯示特定 DSC 作業的所有事件。</span><span class="sxs-lookup"><span data-stu-id="453f6-194">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="453f6-195">這和 `Get-WinEvent` Cmdlet 會顯示相同的結果，如以下輸出所示：</span><span class="sxs-lookup"><span data-stu-id="453f6-195">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

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

<span data-ttu-id="453f6-196">理想的情況是先使用 `Get-xDscOperation` 列出電腦上執行的最新幾個 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="453f6-196">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="453f6-197">接著使用 `Trace-xDscOperation` 檢查任何單一作業 (使用其 SequenceID 或 JobID)，探索它在幕後的工作內容。</span><span class="sxs-lookup"><span data-stu-id="453f6-197">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="453f6-198">取得遠端電腦的事件</span><span class="sxs-lookup"><span data-stu-id="453f6-198">Getting events for a remote computer</span></span>

<span data-ttu-id="453f6-199">使用 `Trace-xDscOperation` Cmdlet 的 `ComputerName` 參數來取得遠端電腦上的事件詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="453f6-199">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="453f6-200">執行這項作業之前，您必須先建立防火牆規則，允許在遠端電腦上進行遠端系統管理︰</span><span class="sxs-lookup"><span data-stu-id="453f6-200">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="453f6-201">現在，您可以在 `Trace-xDscOperation` 呼叫中指定該部電腦：</span><span class="sxs-lookup"><span data-stu-id="453f6-201">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

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

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="453f6-202">我的資源不更新：如何重設快取</span><span class="sxs-lookup"><span data-stu-id="453f6-202">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="453f6-203">基於效率考量，DSC 引擎會快取實作為 PowerShell 模組的資源。</span><span class="sxs-lookup"><span data-stu-id="453f6-203">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="453f6-204">不過，這可能會在撰寫並同時測試資源時造成問題，因為在程序重新啟動前，DSC 會載入快取的版本。</span><span class="sxs-lookup"><span data-stu-id="453f6-204">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="453f6-205">讓 DSC 載入較新版本的唯一方法，是明確結束主控 DSC 引擎的程序。</span><span class="sxs-lookup"><span data-stu-id="453f6-205">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="453f6-206">同樣地，當您執行 `Start-DscConfiguration`，在新增及修改自訂的資源後，可能要重新啟動電腦才會執行修改的內容。</span><span class="sxs-lookup"><span data-stu-id="453f6-206">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="453f6-207">這是因為 DSC 是在 WMI 提供者主機處理程序 (WmiPrvSE) 中執行，通常一次會執行多個 WmiPrvSE 執行個體。</span><span class="sxs-lookup"><span data-stu-id="453f6-207">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="453f6-208">當您重新開機時，主機處理程序就會重新啟動，而快取也會清除。</span><span class="sxs-lookup"><span data-stu-id="453f6-208">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="453f6-209">若要順利回收設定和清除快取卻不重新開機，您必須停止然後再重新啟動主機處理程序。</span><span class="sxs-lookup"><span data-stu-id="453f6-209">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="453f6-210">您可以對每個執行個體都執行識別、停止和重新啟動程序。</span><span class="sxs-lookup"><span data-stu-id="453f6-210">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="453f6-211">或者如下文所示，使用 `DebugMode` 重新載入 PowerShell DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="453f6-211">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="453f6-212">若要識別出並停止每個執行個體上主控 DSC 引擎的處理程序，您可以列出主控 DSC 引擎的 WmiPrvSE 處理程序識別碼。</span><span class="sxs-lookup"><span data-stu-id="453f6-212">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="453f6-213">然後，更新提供者、使用下列命令停止 WmiPrvSE 處理程序，再執行一次 **Start-DscConfiguration**。</span><span class="sxs-lookup"><span data-stu-id="453f6-213">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

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

## <a name="using-debugmode"></a><span data-ttu-id="453f6-214">使用 DebugMode</span><span class="sxs-lookup"><span data-stu-id="453f6-214">Using DebugMode</span></span>

<span data-ttu-id="453f6-215">您可以設定 DSC 本機設定管理員 (LCM) 使用 `DebugMode` 在重新啟動主機處理程序時，一律清除快取。</span><span class="sxs-lookup"><span data-stu-id="453f6-215">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="453f6-216">設為 **TRUE** 時，會讓引擎一律重新載入 PowerShell DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="453f6-216">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="453f6-217">資源完成撰寫後，您就可以將它設回 **FALSE**，引擎會還原成快取模組行為。</span><span class="sxs-lookup"><span data-stu-id="453f6-217">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="453f6-218">下面的示範會說明 `DebugMode` 如何自動重新整理快取。</span><span class="sxs-lookup"><span data-stu-id="453f6-218">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="453f6-219">首先，我們來看一下預設設定：</span><span class="sxs-lookup"><span data-stu-id="453f6-219">First, let's look at the default configuration:</span></span>

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

<span data-ttu-id="453f6-220">您可以看到 `DebugMode` 設為 **"None"**。</span><span class="sxs-lookup"><span data-stu-id="453f6-220">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="453f6-221">若要安裝 `DebugMode` 示範，請使用下列 PowerShell 資源：</span><span class="sxs-lookup"><span data-stu-id="453f6-221">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

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

<span data-ttu-id="453f6-222">現在，使用上述資源中的 `TestProviderDebugMode` 來撰寫設定：</span><span class="sxs-lookup"><span data-stu-id="453f6-222">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

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

<span data-ttu-id="453f6-223">您將會看到檔案的內容：`$env:SystemDrive\OutputFromTestProviderDebugMode.txt` 是 **1**。</span><span class="sxs-lookup"><span data-stu-id="453f6-223">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="453f6-224">現在使用下列指令碼來更新提供者程式碼：</span><span class="sxs-lookup"><span data-stu-id="453f6-224">Now, update the provider code using the following script:</span></span>

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

<span data-ttu-id="453f6-225">這個指令碼會產生一個隨機數字，以此更新提供者程式碼。</span><span class="sxs-lookup"><span data-stu-id="453f6-225">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="453f6-226">若 `DebugMode` 設定為 false，檔案內容 "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" 就一律不會變更。</span><span class="sxs-lookup"><span data-stu-id="453f6-226">With `DebugMode` set to false, the contents of the file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" are never changed.</span></span>

<span data-ttu-id="453f6-227">現在，在設定指令碼中將 `DebugMode` 設為 **"ForceModuleImport"**：</span><span class="sxs-lookup"><span data-stu-id="453f6-227">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="453f6-228">當您再次執行上述指令碼時，會看到檔案的內容每次都不同。</span><span class="sxs-lookup"><span data-stu-id="453f6-228">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="453f6-229">(您可以執行 `Get-DscConfiguration` 檢查它)。</span><span class="sxs-lookup"><span data-stu-id="453f6-229">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="453f6-230">以下是另外兩次的執行結果 (執行指令碼時您的結果可能不同)：</span><span class="sxs-lookup"><span data-stu-id="453f6-230">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

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

## <a name="see-also"></a><span data-ttu-id="453f6-231">另請參閱</span><span class="sxs-lookup"><span data-stu-id="453f6-231">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="453f6-232">概念</span><span class="sxs-lookup"><span data-stu-id="453f6-232">Concepts</span></span>

- [<span data-ttu-id="453f6-233">建置自訂的 Windows PowerShell 預期狀態設定資源</span><span class="sxs-lookup"><span data-stu-id="453f6-233">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](../resources/authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="453f6-234">其他資源</span><span class="sxs-lookup"><span data-stu-id="453f6-234">Other Resources</span></span>

- [<span data-ttu-id="453f6-235">Windows PowerShell 預期狀態設定 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="453f6-235">Windows PowerShell Desired State Configuration Cmdlets</span></span>](/powershell/module/psdesiredstateconfiguration/)
