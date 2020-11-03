---
description: Windows PowerShell 會建立名為 "Windows PowerShell" 的 Windows 事件記錄檔，以記錄 Windows PowerShell 事件。 您可以在事件檢視器中或使用取得事件的 Cmdlet （例如 Cmdlet）來查看此記錄檔 `Get-EventLog` 。 根據預設，Windows PowerShell 引擎和提供者事件會記錄在事件記錄檔中，但您可以使用事件記錄檔喜好設定變數來自訂事件記錄檔。 例如，您可以新增有關 Windows PowerShell 命令的事件。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_eventlogs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Eventlogs
ms.openlocfilehash: eb92333c6a6e220e287dcbec1441d2d05aa9275b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208040"
---
# <a name="about-eventlogs"></a><span data-ttu-id="80485-107">關於檢視</span><span class="sxs-lookup"><span data-stu-id="80485-107">About Eventlogs</span></span>

## <a name="short-description"></a><span data-ttu-id="80485-108">簡短描述</span><span class="sxs-lookup"><span data-stu-id="80485-108">Short Description</span></span>

<span data-ttu-id="80485-109">Windows PowerShell 會建立名為 "Windows PowerShell" 的 Windows 事件記錄檔，以記錄 Windows PowerShell 事件。</span><span class="sxs-lookup"><span data-stu-id="80485-109">Windows PowerShell creates a Windows event log that is named "Windows PowerShell" to record Windows PowerShell events.</span></span> <span data-ttu-id="80485-110">您可以在事件檢視器中或使用取得事件的 Cmdlet （例如 Cmdlet）來查看此記錄檔 `Get-EventLog` 。</span><span class="sxs-lookup"><span data-stu-id="80485-110">You can view this log in Event Viewer or by using cmdlets that get events, such as the `Get-EventLog` cmdlet.</span></span> <span data-ttu-id="80485-111">根據預設，Windows PowerShell 引擎和提供者事件會記錄在事件記錄檔中，但您可以使用事件記錄檔喜好設定變數來自訂事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="80485-111">By default, Windows PowerShell engine and provider events are recorded in the event log, but you can use the event log preference variables to customize the event log.</span></span> <span data-ttu-id="80485-112">例如，您可以新增有關 Windows PowerShell 命令的事件。</span><span class="sxs-lookup"><span data-stu-id="80485-112">For example, you can add events about Windows PowerShell commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="80485-113">完整描述</span><span class="sxs-lookup"><span data-stu-id="80485-113">Long Description</span></span>

<span data-ttu-id="80485-114">Windows PowerShell 事件記錄檔會記錄 Windows PowerShell 作業的詳細資料，例如啟動和停止程式引擎，以及啟動和停止 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="80485-114">The Windows PowerShell event log records details of Windows PowerShell operations, such as starting and stopping the program engine and starting and stopping the Windows PowerShell providers.</span></span> <span data-ttu-id="80485-115">您也可以記錄有關 Windows PowerShell 命令的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="80485-115">You can also log details about Windows PowerShell commands.</span></span>

<span data-ttu-id="80485-116">Windows PowerShell 事件記錄檔位於 [應用程式和服務記錄檔] 群組中。</span><span class="sxs-lookup"><span data-stu-id="80485-116">The Windows PowerShell event log is in the Application and Services Logs group.</span></span> <span data-ttu-id="80485-117">Windows PowerShell 記錄是不使用 Windows 事件技術的傳統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="80485-117">The Windows PowerShell log is a classic event log that does not use the Windows Eventing technology.</span></span> <span data-ttu-id="80485-118">若要查看記錄，請使用針對傳統事件記錄檔設計的指令程式，例如 `Get-EventLog` 。</span><span class="sxs-lookup"><span data-stu-id="80485-118">To view the log, use the cmdlets designed for classic event logs, such as `Get-EventLog`.</span></span>

## <a name="viewing-the-windows-powershell-event-log"></a><span data-ttu-id="80485-119">查看 Windows PowerShell 事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="80485-119">Viewing the Windows PowerShell Event Log</span></span>

<span data-ttu-id="80485-120">您可以在事件檢視器中或使用和 Cmdlet 來查看 Windows PowerShell 事件記錄檔 `Get-EventLog` `Get-WmiObject` 。</span><span class="sxs-lookup"><span data-stu-id="80485-120">You can view the Windows PowerShell event log in Event Viewer or by using the `Get-EventLog` and `Get-WmiObject` cmdlets.</span></span> <span data-ttu-id="80485-121">若要查看 Windows PowerShell 記錄檔的內容，請輸入：</span><span class="sxs-lookup"><span data-stu-id="80485-121">To view the contents of the Windows PowerShell log, type:</span></span>

```powershell
Get-EventLog -LogName "Windows PowerShell"
```

<span data-ttu-id="80485-122">若要檢查事件和其屬性，請使用 `Sort-Object` Cmdlet、 `Group-Object` Cmdlet，以及 Cmdlet `Format`)  (指令程式 `Format` 。</span><span class="sxs-lookup"><span data-stu-id="80485-122">To examine the events and their properties, use the `Sort-Object` cmdlet, the `Group-Object` cmdlet, and the cmdlets that contain the `Format` verb (the `Format` cmdlets).</span></span>

<span data-ttu-id="80485-123">例如，若要查看記錄中依事件識別碼分組的事件，請輸入：</span><span class="sxs-lookup"><span data-stu-id="80485-123">For example, to view the events in the log grouped by the event ID, type:</span></span>

```powershell
Get-EventLog "Windows PowerShell" | Format-Table -GroupBy EventID
```

<span data-ttu-id="80485-124">或者，輸入：</span><span class="sxs-lookup"><span data-stu-id="80485-124">Or, type:</span></span>

```powershell
Get-EventLog "Windows PowerShell" |
  Sort-Object EventID |
  Group-Object EventID
```

<span data-ttu-id="80485-125">若要查看所有傳統事件記錄檔，請輸入：</span><span class="sxs-lookup"><span data-stu-id="80485-125">To view all the classic event logs, type:</span></span>

```powershell
Get-EventLog -List
```

<span data-ttu-id="80485-126">您也可以使用 `Get-WmiObject` Cmdlet，以 (WMI) 類別來檢查事件記錄檔，以使用事件相關的 Windows Management Instrumentation。</span><span class="sxs-lookup"><span data-stu-id="80485-126">You can also use the `Get-WmiObject` cmdlet to use the event-related Windows Management Instrumentation (WMI) classes to examine the event log.</span></span> <span data-ttu-id="80485-127">例如，若要查看事件記錄檔的所有屬性，請輸入：</span><span class="sxs-lookup"><span data-stu-id="80485-127">For example, to view all the properties of the event log file, type:</span></span>

```powershell
Get-WmiObject Win32_NTEventlogFile |
  where LogFileName -EQ "Windows PowerShell" |
  Format-List -Property *
```

<span data-ttu-id="80485-128">若要尋找 Win32 事件相關 WMI 類別，請輸入：</span><span class="sxs-lookup"><span data-stu-id="80485-128">To find the Win32 event-related WMI classes, type:</span></span>

```powershell
Get-WmiObject -List | where Name -Like "win32*event*"
```

<span data-ttu-id="80485-129">如需詳細資訊，請輸入 "Get-help Get-EventLog" 和 "Get-help >get-wmiobject"。</span><span class="sxs-lookup"><span data-stu-id="80485-129">For more information, type "Get-Help Get-EventLog" and "Get-Help Get-WmiObject".</span></span>

## <a name="selecting-events-for-the-windows-powershell-event-log"></a><span data-ttu-id="80485-130">選取 Windows PowerShell 事件記錄檔的事件</span><span class="sxs-lookup"><span data-stu-id="80485-130">Selecting Events for the Windows PowerShell Event Log</span></span>

<span data-ttu-id="80485-131">您可以使用事件記錄檔喜好設定變數來判斷 Windows PowerShell 事件記錄檔中記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="80485-131">You can use the event log preference variables to determine which events are recorded in the Windows PowerShell event log.</span></span>

<span data-ttu-id="80485-132">有六個事件記錄檔喜好設定變數：這三個記錄元件各有兩個變數：引擎 (Windows PowerShell 程式) 、提供者及命令。</span><span class="sxs-lookup"><span data-stu-id="80485-132">There are six event log preference variables; two variables for each of the three logging components: the engine (the Windows PowerShell program), the providers, and the commands.</span></span> <span data-ttu-id="80485-133">LifeCycleEvent 變數會記錄正常開始和停止事件。</span><span class="sxs-lookup"><span data-stu-id="80485-133">The LifeCycleEvent variables log normal starting and stopping events.</span></span> <span data-ttu-id="80485-134">健全狀況變數會記錄錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="80485-134">The Health variables log error events.</span></span>

<span data-ttu-id="80485-135">下表列出事件記錄檔喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="80485-135">The following table lists the event log preference variables.</span></span>

|<span data-ttu-id="80485-136">變數</span><span class="sxs-lookup"><span data-stu-id="80485-136">Variable</span></span>                  |<span data-ttu-id="80485-137">描述</span><span class="sxs-lookup"><span data-stu-id="80485-137">Description</span></span>                                    |
|--------------------------|-----------------------------------------------|
|<span data-ttu-id="80485-138">$LogEngineLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="80485-138">$LogEngineLifeCycleEvent</span></span>  |<span data-ttu-id="80485-139">記錄 PowerShell 的啟動和停止</span><span class="sxs-lookup"><span data-stu-id="80485-139">Logs the start and stop of PowerShell</span></span>          |
|<span data-ttu-id="80485-140">$LogEngineHealthEvent</span><span class="sxs-lookup"><span data-stu-id="80485-140">$LogEngineHealthEvent</span></span>     |<span data-ttu-id="80485-141">記錄 PowerShell 程式錯誤</span><span class="sxs-lookup"><span data-stu-id="80485-141">Logs PowerShell program errors</span></span>                 |
|<span data-ttu-id="80485-142">$LogProviderLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="80485-142">$LogProviderLifeCycleEvent</span></span>|<span data-ttu-id="80485-143">記錄 PowerShell 提供者的啟動和停止</span><span class="sxs-lookup"><span data-stu-id="80485-143">Logs the start and stop of PowerShell providers</span></span>|
|<span data-ttu-id="80485-144">$LogProviderHealthEvent</span><span class="sxs-lookup"><span data-stu-id="80485-144">$LogProviderHealthEvent</span></span>   |<span data-ttu-id="80485-145">記錄 PowerShell 提供者錯誤</span><span class="sxs-lookup"><span data-stu-id="80485-145">Logs PowerShell provider errors</span></span>                |
|<span data-ttu-id="80485-146">$LogCommandLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="80485-146">$LogCommandLifeCycleEvent</span></span> |<span data-ttu-id="80485-147">記錄命令的開始和完成</span><span class="sxs-lookup"><span data-stu-id="80485-147">Logs the starting and completion of commands</span></span>   |
|<span data-ttu-id="80485-148">$LogCommandHealthEvent</span><span class="sxs-lookup"><span data-stu-id="80485-148">$LogCommandHealthEvent</span></span>    |<span data-ttu-id="80485-149">記錄命令錯誤</span><span class="sxs-lookup"><span data-stu-id="80485-149">Logs command errors</span></span>                            |

<span data-ttu-id="80485-150"> (如需 Windows PowerShell 提供者的詳細資訊，請參閱 [about_Providers](about_Providers.md)。 ) </span><span class="sxs-lookup"><span data-stu-id="80485-150">(For information about Windows PowerShell providers, see [about_Providers](about_Providers.md).)</span></span>

<span data-ttu-id="80485-151">依預設，只會啟用下列事件種類：</span><span class="sxs-lookup"><span data-stu-id="80485-151">By default, only the following event types are enabled:</span></span>

* <span data-ttu-id="80485-152">$LogEngineLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="80485-152">$LogEngineLifeCycleEvent</span></span>
* <span data-ttu-id="80485-153">$LogEngineHealthEvent</span><span class="sxs-lookup"><span data-stu-id="80485-153">$LogEngineHealthEvent</span></span>
* <span data-ttu-id="80485-154">$LogProviderLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="80485-154">$LogProviderLifeCycleEvent</span></span>
* <span data-ttu-id="80485-155">$LogProviderHealthEvent</span><span class="sxs-lookup"><span data-stu-id="80485-155">$LogProviderHealthEvent</span></span>

<span data-ttu-id="80485-156">若要啟用事件種類，請將該事件種類的喜好設定變數設定為 $true。</span><span class="sxs-lookup"><span data-stu-id="80485-156">To enable an event type, set the preference variable for that event type to $true.</span></span> <span data-ttu-id="80485-157">例如，若要啟用命令生命週期事件，請輸入：</span><span class="sxs-lookup"><span data-stu-id="80485-157">For example, to enable command life-cycle events, type:</span></span>

```powershell
$LogCommandLifeCycleEvent
```

<span data-ttu-id="80485-158">或者，輸入：</span><span class="sxs-lookup"><span data-stu-id="80485-158">Or, type:</span></span>

```powershell
$LogCommandLifeCycleEvent = $true
```

<span data-ttu-id="80485-159">若要停用事件種類，請將該事件種類的喜好設定變數設定為 $false。</span><span class="sxs-lookup"><span data-stu-id="80485-159">To disable an event type, set the preference variable for that event type to $false.</span></span> <span data-ttu-id="80485-160">例如，若要停用命令生命週期事件，請輸入：</span><span class="sxs-lookup"><span data-stu-id="80485-160">For example, to disable command life-cycle events, type:</span></span>

```powershell
$LogProviderLifeCycleEvent = $false
```

<span data-ttu-id="80485-161">除了指出 Windows PowerShell 引擎和核心提供者已啟動的事件之外，您還可以停用任何事件。</span><span class="sxs-lookup"><span data-stu-id="80485-161">You can disable any event, except for the events that indicate that the Windows PowerShell engine and the core providers are started.</span></span> <span data-ttu-id="80485-162">這些事件會在執行 Windows PowerShell 設定檔之前，以及在主機程式準備接受命令之前產生。</span><span class="sxs-lookup"><span data-stu-id="80485-162">These events are generated before the Windows PowerShell profiles are run and before the host program is ready to accept commands.</span></span>

<span data-ttu-id="80485-163">變數設定只適用于目前的 Windows PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="80485-163">The variable settings apply only for the current Windows PowerShell session.</span></span>
<span data-ttu-id="80485-164">若要將它們套用至所有 Windows PowerShell 會話，請將它們新增至您的 Windows PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="80485-164">To apply them to all Windows PowerShell sessions, add them to your Windows PowerShell profile.</span></span>

## <a name="logging-module-events"></a><span data-ttu-id="80485-165">記錄模組事件</span><span class="sxs-lookup"><span data-stu-id="80485-165">Logging Module Events</span></span>

<span data-ttu-id="80485-166">從 Windows PowerShell 3.0 開始，您可以將模組和嵌入式管理單元的 LogPipelineExecutionDetails 屬性設定為 TRUE，以記錄 Windows PowerShell 模組和嵌入式管理單元中的 Cmdlet 和函式的執行事件。</span><span class="sxs-lookup"><span data-stu-id="80485-166">Beginning in Windows PowerShell 3.0, you can record execution events for the cmdlets and functions in Windows PowerShell modules and snap-ins by setting the LogPipelineExecutionDetails property of modules and snap-ins to TRUE.</span></span> <span data-ttu-id="80485-167">在 Windows PowerShell 2.0 中，這項功能僅適用于嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="80485-167">In Windows PowerShell 2.0, this feature is available only for snap-ins.</span></span>

<span data-ttu-id="80485-168">當 LogPipelineExecutionDetails 屬性值為 TRUE (`$true`) 時，Windows PowerShell 會將會話中的 Cmdlet 和函式執行事件寫入事件檢視器中的 Windows PowerShell 記錄。</span><span class="sxs-lookup"><span data-stu-id="80485-168">When the LogPipelineExecutionDetails property value is TRUE (`$true`), Windows PowerShell writes cmdlet and function execution events in the session to the Windows PowerShell log in Event Viewer.</span></span> <span data-ttu-id="80485-169">這項設定只會在目前的會話中生效。</span><span class="sxs-lookup"><span data-stu-id="80485-169">The setting is effective only in the current session.</span></span>

<span data-ttu-id="80485-170">若要啟用模組中的 Cmdlet 和函式的執行事件記錄，請使用下列命令順序。</span><span class="sxs-lookup"><span data-stu-id="80485-170">To enable logging of execution events of cmdlets and functions in a module, use the following command sequence.</span></span>

```powershell
Import-Module <ModuleName>
$m = Get-Module <ModuleName>
$m.LogPipelineExecutionDetails = $true
```

<span data-ttu-id="80485-171">若要在嵌入式管理單元中啟用 Cmdlet 的執行事件記錄，請使用下列命令順序。</span><span class="sxs-lookup"><span data-stu-id="80485-171">To enable logging of execution events of cmdlets in a snap-in, use the following command sequence.</span></span>

```powershell
$m = Get-PSSnapin <SnapInName> [-Registered]
$m.LogPipelineExecutionDetails = $True
```

<span data-ttu-id="80485-172">若要停用記錄，請使用相同的命令順序將屬性值設定為 FALSE (`$false`) 。</span><span class="sxs-lookup"><span data-stu-id="80485-172">To disable logging, use the same command sequence to set the property value to FALSE (`$false`).</span></span>

<span data-ttu-id="80485-173">您也可以使用 [開啟模組記錄] 群組原則設定來啟用和停用模組和嵌入式管理單元記錄。</span><span class="sxs-lookup"><span data-stu-id="80485-173">You can also use the "Turn on Module Logging" Group Policy setting to enable and disable module and snap-in logging.</span></span> <span data-ttu-id="80485-174">原則值包含模組和嵌入式管理單元名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="80485-174">The policy value includes a list of module and snap-in names.</span></span> <span data-ttu-id="80485-175">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="80485-175">Wildcards are supported.</span></span>

<span data-ttu-id="80485-176">針對模組設定 [開啟模組記錄] 時，模組的 LogPipelineExecutionDetails 屬性值在所有會話中都是 TRUE，而且無法變更。</span><span class="sxs-lookup"><span data-stu-id="80485-176">When "Turn on Module Logging" is set for a module, the value of the LogPipelineExecutionDetails property of the module is TRUE in all sessions and it cannot be changed.</span></span>

<span data-ttu-id="80485-177">[開啟模組記錄] 群組原則設定位於下列群組原則路徑：</span><span class="sxs-lookup"><span data-stu-id="80485-177">The Turn On Module Logging group policy setting is located in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
     Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

<span data-ttu-id="80485-178">使用者設定原則的優先順序高於電腦設定原則，而這兩個原則會優先考慮模組和嵌入式管理單元的 LogPipelineExecutionDetails 屬性值。</span><span class="sxs-lookup"><span data-stu-id="80485-178">The User Configuration policy takes precedence over the Computer Configuration policy, and both policies take preference over the value of the LogPipelineExecutionDetails property of modules and snap-ins.</span></span>

<span data-ttu-id="80485-179">如需此群組原則設定的詳細資訊，請參閱 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)。</span><span class="sxs-lookup"><span data-stu-id="80485-179">For more information about this Group Policy setting, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

## <a name="security-and-auditing"></a><span data-ttu-id="80485-180">安全性和審核</span><span class="sxs-lookup"><span data-stu-id="80485-180">Security and Auditing</span></span>

<span data-ttu-id="80485-181">Windows PowerShell 事件記錄檔的設計目的是要指出活動並提供作業詳細資料來進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="80485-181">The Windows PowerShell event log is designed to indicate activity and to provide operational details for troubleshooting.</span></span>

<span data-ttu-id="80485-182">不過，就像大部分的 Windows 應用程式事件記錄一樣，Windows PowerShell 的事件記錄檔並非設計成安全的。</span><span class="sxs-lookup"><span data-stu-id="80485-182">However, like most Windows-based application event logs, the Windows PowerShell event log is not designed to be secure.</span></span> <span data-ttu-id="80485-183">它不應該用來審核安全性或記錄機密或專屬資訊。</span><span class="sxs-lookup"><span data-stu-id="80485-183">It should not be used to audit security or to record confidential or proprietary information.</span></span>

<span data-ttu-id="80485-184">事件記錄檔是設計來供使用者讀取和瞭解。</span><span class="sxs-lookup"><span data-stu-id="80485-184">Event logs are designed to be read and understood by users.</span></span> <span data-ttu-id="80485-185">使用者可以讀取和寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="80485-185">Users can read from and write to the log.</span></span> <span data-ttu-id="80485-186">惡意使用者可以讀取本機或遠端電腦上的事件記錄檔、記錄 false 資料，然後防止記錄其活動。</span><span class="sxs-lookup"><span data-stu-id="80485-186">A malicious user could read an event log on a local or remote computer, record false data, and then prevent the logging of their activities.</span></span>

## <a name="notes"></a><span data-ttu-id="80485-187">備忘稿</span><span class="sxs-lookup"><span data-stu-id="80485-187">Notes</span></span>

<span data-ttu-id="80485-188">模組作者的作者可以將記錄功能新增至其模組。</span><span class="sxs-lookup"><span data-stu-id="80485-188">Authors of module authors can add logging features to their modules.</span></span> <span data-ttu-id="80485-189">如需詳細資訊，請參閱 [撰寫 Windows PowerShell 模組](/powershell/scripting/developer/module/writing-a-windows-powershell-module)。</span><span class="sxs-lookup"><span data-stu-id="80485-189">For more information, see [Writing a Windows PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

## <a name="see-also"></a><span data-ttu-id="80485-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80485-190">See Also</span></span>

[<span data-ttu-id="80485-191">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="80485-191">Get-EventLog</span></span>](xref:Microsoft.PowerShell.Management.Get-EventLog)

[<span data-ttu-id="80485-192">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="80485-192">Get-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[<span data-ttu-id="80485-193">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="80485-193">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="80485-194">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="80485-194">about_Preference_Variables</span></span>](about_Preference_Variables.md)
