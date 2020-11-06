---
description: PowerShell 會記錄引擎、提供者和 Cmdlet 的內部作業。
keywords: powershell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_non-windows?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging_Non-Windows
ms.openlocfilehash: f70e2cb2c04287e36ecdf21a97dd099fcfd23d65
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355488"
---
# <a name="about-logging-non-windows"></a><span data-ttu-id="06b92-104">關於記錄非 Windows</span><span class="sxs-lookup"><span data-stu-id="06b92-104">About Logging Non-Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="06b92-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="06b92-105">Short description</span></span>
<span data-ttu-id="06b92-106">PowerShell 會記錄引擎、提供者和 Cmdlet 的內部作業。</span><span class="sxs-lookup"><span data-stu-id="06b92-106">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="06b92-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="06b92-107">Long description</span></span>

<span data-ttu-id="06b92-108">Powershell 會記錄 PowerShell 作業的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="06b92-108">PowerShell logs details of PowerShell operations.</span></span> <span data-ttu-id="06b92-109">例如，PowerShell 會記錄作業，例如啟動和停止引擎，以及啟動和停止提供者。</span><span class="sxs-lookup"><span data-stu-id="06b92-109">For example, PowerShell will log operations such as starting and stopping the engine and starting and stopping providers.</span></span> <span data-ttu-id="06b92-110">它也會記錄 PowerShell 命令的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="06b92-110">It will also log details about PowerShell commands.</span></span>

<span data-ttu-id="06b92-111">PowerShell 記錄檔的位置取決於目標平臺。</span><span class="sxs-lookup"><span data-stu-id="06b92-111">The location of PowerShell logs is dependent on the target platform.</span></span> <span data-ttu-id="06b92-112">在 **Linux** 上，您可以使用 PowerShell 記錄到 **syslog** 和 **rsyslog** 。</span><span class="sxs-lookup"><span data-stu-id="06b92-112">On **Linux** , PowerShell logs to **syslog** and **rsyslog.conf** can be used.</span></span> <span data-ttu-id="06b92-113">如需詳細資訊，請參閱 Linux 電腦的本機 `man` 頁面。</span><span class="sxs-lookup"><span data-stu-id="06b92-113">For more information, refer to the Linux computer's local `man` pages.</span></span> <span data-ttu-id="06b92-114">在 **macOS** 上，會使用 **os_log** 記錄系統。</span><span class="sxs-lookup"><span data-stu-id="06b92-114">On **macOS** , the **os_log** logging system is used.</span></span> <span data-ttu-id="06b92-115">如需詳細資訊，請參閱 [os_log 開發人員檔](https://developer.apple.com/documentation/os/os_log)。</span><span class="sxs-lookup"><span data-stu-id="06b92-115">For more information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

## <a name="viewing-powershell-log-output-on-linux"></a><span data-ttu-id="06b92-116">在 Linux 上查看 PowerShell 記錄檔輸出</span><span class="sxs-lookup"><span data-stu-id="06b92-116">Viewing PowerShell log output on Linux</span></span>

<span data-ttu-id="06b92-117">PowerShell 記錄至 Linux 上的 **syslog** 以及通常用來查看 **syslog** 內容的任何工具。</span><span class="sxs-lookup"><span data-stu-id="06b92-117">PowerShell logs to **syslog** on Linux and any of the tools commonly used to view **syslog** contents may be used.</span></span>

<span data-ttu-id="06b92-118">記錄專案的格式會使用下列範本：</span><span class="sxs-lookup"><span data-stu-id="06b92-118">The format of the log entries uses the following template:</span></span>

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|<span data-ttu-id="06b92-119">欄位</span><span class="sxs-lookup"><span data-stu-id="06b92-119">Field</span></span>        |<span data-ttu-id="06b92-120">描述</span><span class="sxs-lookup"><span data-stu-id="06b92-120">Description</span></span>                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |<span data-ttu-id="06b92-121">產生記錄專案的日期/時間。</span><span class="sxs-lookup"><span data-stu-id="06b92-121">A date/time when the log entry was produced.</span></span>            |
|`MACHINENAME`|<span data-ttu-id="06b92-122">產生記錄檔的系統名稱。</span><span class="sxs-lookup"><span data-stu-id="06b92-122">The name of the system where the log was produced.</span></span>      |
|`PID`        |<span data-ttu-id="06b92-123">寫入記錄專案之進程的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="06b92-123">The process ID of the process that wrote the log entry.</span></span> |
|`COMMITID`   |<span data-ttu-id="06b92-124">`git commit`用來產生組建的識別碼或標記。</span><span class="sxs-lookup"><span data-stu-id="06b92-124">The `git commit` ID or tag used to produce the build.</span></span>   |
|`TID`        |<span data-ttu-id="06b92-125">寫入記錄專案之執行緒的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="06b92-125">The thread ID of the thread that wrote the log entry.</span></span>   |
|`CID`        |<span data-ttu-id="06b92-126">記錄專案的十六進位通道識別碼。</span><span class="sxs-lookup"><span data-stu-id="06b92-126">The hex channel identifier of the log entry.</span></span>            |
|             |<span data-ttu-id="06b92-127">10 = 操作，11 = 分析</span><span class="sxs-lookup"><span data-stu-id="06b92-127">10 = Operational, 11 = Analytic</span></span>                         |
|`EVENTID`    |<span data-ttu-id="06b92-128">記錄專案的事件識別碼。</span><span class="sxs-lookup"><span data-stu-id="06b92-128">The event identifier of the log entry.</span></span>                  |
|`TASK`       |<span data-ttu-id="06b92-129">事件專案的工作識別碼</span><span class="sxs-lookup"><span data-stu-id="06b92-129">The task identifier for the event entry</span></span>                 |
|`OPCODE`     |<span data-ttu-id="06b92-130">事件專案的 opcode</span><span class="sxs-lookup"><span data-stu-id="06b92-130">The opcode for the event entry</span></span>                          |
|`LEVEL`      |<span data-ttu-id="06b92-131">事件專案的記錄層級</span><span class="sxs-lookup"><span data-stu-id="06b92-131">The log level for the event entry</span></span>                       |
|`MESSAGE`    |<span data-ttu-id="06b92-132">與事件專案相關聯的訊息</span><span class="sxs-lookup"><span data-stu-id="06b92-132">The message associated with the event entry</span></span>             |

> [!NOTE]
> <span data-ttu-id="06b92-133">`EVENTID`、 `TASK` 、 `OPCODE` 和在 `LEVEL` 記錄至 Windows 事件記錄檔時所使用的值相同。</span><span class="sxs-lookup"><span data-stu-id="06b92-133">`EVENTID`, `TASK`, `OPCODE`, and `LEVEL` are the same values as used when logging to the Windows event log.</span></span>

### <a name="filtering-powershell-log-entries-using-rsyslog"></a><span data-ttu-id="06b92-134">使用 rsyslog 篩選 PowerShell 記錄專案</span><span class="sxs-lookup"><span data-stu-id="06b92-134">Filtering PowerShell log entries using rsyslog</span></span>

<span data-ttu-id="06b92-135">一般來說，PowerShell 記錄檔專案會寫入 syslog 的預設值 `location/file` 。 **syslog**</span><span class="sxs-lookup"><span data-stu-id="06b92-135">Normally, PowerShell log entries are written to the default `location/file` for **syslog**.</span></span> <span data-ttu-id="06b92-136">不過，您可以將專案重新導向至自訂檔案。</span><span class="sxs-lookup"><span data-stu-id="06b92-136">However, it's possible to redirect the entries to a custom file.</span></span>

1. <span data-ttu-id="06b92-137">建立適用于 PowerShell 記錄檔設定的會議，並為) 提供小於 50 (的數位 `50-default.conf` ，例如 `40-powershell.conf` 。</span><span class="sxs-lookup"><span data-stu-id="06b92-137">Create a conf for PowerShell log configuration and provide a number that's less than 50 (for `50-default.conf`), such as `40-powershell.conf`.</span></span> <span data-ttu-id="06b92-138">檔案應放置在下方 `/etc/rsyslog.d` 。</span><span class="sxs-lookup"><span data-stu-id="06b92-138">The file should be placed under `/etc/rsyslog.d`.</span></span>

1. <span data-ttu-id="06b92-139">在檔案中新增下列專案：</span><span class="sxs-lookup"><span data-stu-id="06b92-139">Add the following entry to the file:</span></span>

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. <span data-ttu-id="06b92-140">請確定 `/etc/rsyslog.conf` 包含新的檔案。</span><span class="sxs-lookup"><span data-stu-id="06b92-140">Make sure `/etc/rsyslog.conf` includes the new file.</span></span> <span data-ttu-id="06b92-141">通常，它會有類似下列設定的一般 include 語句：</span><span class="sxs-lookup"><span data-stu-id="06b92-141">Often, it will have a generic include statement that looks like following configuration:</span></span>

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   <span data-ttu-id="06b92-142">如果沒有，您必須手動加入 include 語句。</span><span class="sxs-lookup"><span data-stu-id="06b92-142">If it doesn't, you'll need to add an include statement manually.</span></span>

1. <span data-ttu-id="06b92-143">請確定已適當設定屬性和許可權。</span><span class="sxs-lookup"><span data-stu-id="06b92-143">Make sure attributes and permissions are set appropriately.</span></span>

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. <span data-ttu-id="06b92-144">將擁有權設定為 **root** 。</span><span class="sxs-lookup"><span data-stu-id="06b92-144">Set ownership to **root**.</span></span>

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. <span data-ttu-id="06b92-145">設定存取權限： **根** 具有讀取/寫入， **使用者** 已讀取。</span><span class="sxs-lookup"><span data-stu-id="06b92-145">Set access permissions: **root** has read/write, **users** have read.</span></span>

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a><span data-ttu-id="06b92-146">在 macOS 上查看 PowerShell 記錄檔輸出</span><span class="sxs-lookup"><span data-stu-id="06b92-146">Viewing PowerShell log output on macOS</span></span>

<span data-ttu-id="06b92-147">在 macOS 上查看 PowerShell 記錄檔輸出的最簡單方法是使用 **主控台** 應用程式。</span><span class="sxs-lookup"><span data-stu-id="06b92-147">The easiest method for viewing PowerShell log output on macOS is using the **Console** application.</span></span>

1. <span data-ttu-id="06b92-148">搜尋 **主控台** 應用程式並加以啟動。</span><span class="sxs-lookup"><span data-stu-id="06b92-148">Search for the **Console** application and launch it.</span></span>
1. <span data-ttu-id="06b92-149">選取 [ **裝置** ] 下的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="06b92-149">Select the Machine name under **Devices**.</span></span>
1. <span data-ttu-id="06b92-150">在 [ **搜尋** ] 欄位中，輸入 `pwsh` PowerShell 主要二進位檔。</span><span class="sxs-lookup"><span data-stu-id="06b92-150">In the **Search** field, enter `pwsh` for the PowerShell main binary.</span></span>
1. <span data-ttu-id="06b92-151">將搜尋篩選準則從變更 `Any` 為 `Process` 。</span><span class="sxs-lookup"><span data-stu-id="06b92-151">Change the search filter from `Any` to `Process`.</span></span>
1. <span data-ttu-id="06b92-152">執行作業。</span><span class="sxs-lookup"><span data-stu-id="06b92-152">Perform the operations.</span></span>
1. <span data-ttu-id="06b92-153">（選擇性）儲存搜尋以供日後使用。</span><span class="sxs-lookup"><span data-stu-id="06b92-153">Optionally, save the search for future use.</span></span>

<span data-ttu-id="06b92-154">若要在 **主控台** 中篩選特定的 PowerShell 進程實例，變數 `$pid` 包含處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="06b92-154">To filter on a specific process instance of PowerShell in the **Console** , the variable `$pid` contains the process ID.</span></span>

1. <span data-ttu-id="06b92-155">在 [ **搜尋** ] 欄位中輸入 **PID** (處理序識別碼) 。</span><span class="sxs-lookup"><span data-stu-id="06b92-155">Enter the **pid** (Process ID) in the **Search** field.</span></span>
1. <span data-ttu-id="06b92-156">將搜尋篩選準則變更為 `PID` 。</span><span class="sxs-lookup"><span data-stu-id="06b92-156">Change the search filter to `PID`.</span></span>
1. <span data-ttu-id="06b92-157">執行作業。</span><span class="sxs-lookup"><span data-stu-id="06b92-157">Perform the operations.</span></span>

### <a name="viewing-powershell-log-output-from-a-command-line"></a><span data-ttu-id="06b92-158">從命令列查看 PowerShell 記錄檔輸出</span><span class="sxs-lookup"><span data-stu-id="06b92-158">Viewing PowerShell log output from a command line</span></span>

<span data-ttu-id="06b92-159">`log`命令可用於從命令列查看 PowerShell 記錄專案。</span><span class="sxs-lookup"><span data-stu-id="06b92-159">The `log` command can be used to view PowerShell log entries from the command line.</span></span>

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a><span data-ttu-id="06b92-160">保存 PowerShell 記錄檔輸出</span><span class="sxs-lookup"><span data-stu-id="06b92-160">Persisting PowerShell log output</span></span>

<span data-ttu-id="06b92-161">根據預設，PowerShell 會在 macOS 上使用預設僅限記憶體的記錄。</span><span class="sxs-lookup"><span data-stu-id="06b92-161">By default, PowerShell uses the default memory-only logging on macOS.</span></span> <span data-ttu-id="06b92-162">您可以使用命令來變更此行為，以啟用持續性 `log config` 。</span><span class="sxs-lookup"><span data-stu-id="06b92-162">This behavior can be changed to enable persistence using the `log config` command.</span></span>

<span data-ttu-id="06b92-163">下列腳本會啟用資訊層級記錄和持續性：</span><span class="sxs-lookup"><span data-stu-id="06b92-163">The following script enables info level logging and persistence:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

<span data-ttu-id="06b92-164">下列命令會將 PowerShell 記錄還原為預設狀態：</span><span class="sxs-lookup"><span data-stu-id="06b92-164">The following command reverts PowerShell logging to the default state:</span></span>

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

<span data-ttu-id="06b92-165">啟用持續性之後，您 `log show` 可以使用命令來匯出記錄專案。</span><span class="sxs-lookup"><span data-stu-id="06b92-165">After persistence is enabled, the `log show` command can be used to export log items.</span></span> <span data-ttu-id="06b92-166">此命令會提供選項，讓您匯出最後 N 個專案、指定時間之後的專案，或指定時間範圍內的專案。</span><span class="sxs-lookup"><span data-stu-id="06b92-166">The command provides options for exporting the last N items, items since a given time, or items within a given time span.</span></span>

<span data-ttu-id="06b92-167">例如，下列命令會在之後匯出專案 `9am on April 5 of 2018` ：</span><span class="sxs-lookup"><span data-stu-id="06b92-167">For example, the following command exports items since `9am on April 5 of 2018`:</span></span>

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

<span data-ttu-id="06b92-168">您可以藉 `log` 由 `log show --help` 執行以取得其他詳細資料，以取得的說明。</span><span class="sxs-lookup"><span data-stu-id="06b92-168">You can get help for `log` by running `log show --help` for additional details.</span></span>

> [!TIP]
> <span data-ttu-id="06b92-169">從 PowerShell 提示字元或腳本執行任何記錄檔命令時，請使用雙引號括住整個述詞字串和單引號內的單引號。</span><span class="sxs-lookup"><span data-stu-id="06b92-169">When executing any of the log commands from a PowerShell prompt or script, use double quotes around the entire predicate string and single quotes within.</span></span> <span data-ttu-id="06b92-170">這樣就不需要在述詞字串內的雙引號字元之間進行換用。</span><span class="sxs-lookup"><span data-stu-id="06b92-170">This avoids the need to escape double quote characters within the predicate string.</span></span>

<span data-ttu-id="06b92-171">您也可能想要考慮將事件記錄檔儲存至更安全的位置，例如中央事件記錄檔收集器，或 [SIEM][] 匯總工具。</span><span class="sxs-lookup"><span data-stu-id="06b92-171">You may also want to consider saving the event logs to a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="06b92-172">您可以在 Azure 中設定 SIEM。</span><span class="sxs-lookup"><span data-stu-id="06b92-172">You can set up SIEM in Azure.</span></span> <span data-ttu-id="06b92-173">如需詳細資訊，請參閱 [泛型 SIEM 整合](/cloud-app-security/siem)。</span><span class="sxs-lookup"><span data-stu-id="06b92-173">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

## <a name="configuring-logging-on-a-non-windows-system"></a><span data-ttu-id="06b92-174">在非 Windows 系統上設定記錄</span><span class="sxs-lookup"><span data-stu-id="06b92-174">Configuring logging on a non-Windows system</span></span>

<span data-ttu-id="06b92-175">在 Windows 上，您可以藉由建立 ETW 追蹤接聽項或使用事件檢視器來啟用分析記錄來設定記錄。</span><span class="sxs-lookup"><span data-stu-id="06b92-175">On Windows, logging is configured by creating ETW trace listeners or by using the Event Viewer to enable Analytic logging.</span></span> <span data-ttu-id="06b92-176">在 Linux 和 macOS 上，記錄是使用檔案進行設定 `powershell.config.json` 。</span><span class="sxs-lookup"><span data-stu-id="06b92-176">On Linux and macOS, logging is configured using the file `powershell.config.json`.</span></span> <span data-ttu-id="06b92-177">本節的其餘部分將討論如何在非 Windows 系統上設定 PowerShell 記錄。</span><span class="sxs-lookup"><span data-stu-id="06b92-177">The rest of this section will discuss configuring PowerShell logging on a non-Windows system.</span></span>

<span data-ttu-id="06b92-178">PowerShell 預設會啟用操作通道的資訊記錄。</span><span class="sxs-lookup"><span data-stu-id="06b92-178">By default, PowerShell enables informational logging to the operational channel.</span></span> <span data-ttu-id="06b92-179">這表示，PowerShell 所產生的任何記錄輸出，都會標示為可操作，而且會記錄 (追蹤) 層級大於資訊的記錄。</span><span class="sxs-lookup"><span data-stu-id="06b92-179">What this means is any log output produced by PowerShell that is marked as operational and has a log (trace) level greater than informational will be logged.</span></span> <span data-ttu-id="06b92-180">診斷有時可能需要額外的記錄輸出，例如詳細資訊記錄檔輸出或啟用分析記錄檔輸出。</span><span class="sxs-lookup"><span data-stu-id="06b92-180">Occasionally, diagnoses may require additional log output, such as verbose log output or enabling analytic log output.</span></span>

<span data-ttu-id="06b92-181">檔案 `powershell.config.json` 是位於 PowerShell 目錄中的 **JSON** 格式檔案 `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="06b92-181">The file `powershell.config.json` is a **JSON** formatted file residing in the PowerShell `$PSHOME` directory.</span></span> <span data-ttu-id="06b92-182">PowerShell 的每個安裝都會使用自己的此檔案複本。</span><span class="sxs-lookup"><span data-stu-id="06b92-182">Each installation of PowerShell uses its own copy of this file.</span></span> <span data-ttu-id="06b92-183">若為正常操作，此檔案會保持不變。</span><span class="sxs-lookup"><span data-stu-id="06b92-183">For normal operation, this file is left unchanged.</span></span> <span data-ttu-id="06b92-184">雖然它可能很有用，但若要變更檔案中的某些設定，以進行診斷或區分相同系統上的多個 PowerShell 版本，或甚至多個相同版本的複本 (請參閱 `LogIdentity` 下表) 。</span><span class="sxs-lookup"><span data-stu-id="06b92-184">Although it can be useful, to change some of the settings in the file, for diagnosis or for distinguishing between multiple PowerShell versions on the same system or even multiple copies of the same version (See `LogIdentity` in the table below).</span></span>

<span data-ttu-id="06b92-185">下列程式碼是範例設定：</span><span class="sxs-lookup"><span data-stu-id="06b92-185">The following code is an example configuration:</span></span>

```json
{
  "Microsoft.PowerShell:ExecutionPolicy": "RemoteSigned",
  "PowerShellPolicies": {
    "ScriptExecution": {
      "ExecutionPolicy": "RemoteSigned",
      "EnableScripts": true
    },
    "ScriptBlockLogging": {
      "EnableScriptBlockInvocationLogging": true,
      "EnableScriptBlockLogging": true
    },
    "ModuleLogging": {
      "EnableModuleLogging": false,
      "ModuleNames": [
        "PSReadline",
        "PowerShellGet"
      ]
    },
    "ProtectedEventLogging": {
      "EnableProtectedEventLogging": false,
      "EncryptionCertificate": [
        "Joe"
      ]
    },
    "Transcription": {
      "EnableTranscripting": true,
      "EnableInvocationHeader": true,
      "OutputDirectory": "F:\\tmp\\new"
    },
    "UpdatableHelp": {
      "DefaultSourcePath": "f:\\temp"
    },
    "ConsoleSessionConfiguration": {
      "EnableConsoleSessionConfiguration": false,
      "ConsoleSessionConfigurationName": "name"
    }
  },
  "LogLevel": "verbose"
}
```

<span data-ttu-id="06b92-186">下表列出設定 PowerShell 記錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="06b92-186">The properties for configuring PowerShell logging are listed in the following table.</span></span> <span data-ttu-id="06b92-187">以星號標示的值（例如 `Operational*` ）表示檔案中未提供任何值時的預設值。</span><span class="sxs-lookup"><span data-stu-id="06b92-187">Values marked with an asterisk, such as `Operational*`, indicate the default value when no value is provided in the file.</span></span>

|<span data-ttu-id="06b92-188">屬性</span><span class="sxs-lookup"><span data-stu-id="06b92-188">Property</span></span>   |<span data-ttu-id="06b92-189">值</span><span class="sxs-lookup"><span data-stu-id="06b92-189">Values</span></span>        |<span data-ttu-id="06b92-190">描述</span><span class="sxs-lookup"><span data-stu-id="06b92-190">Description</span></span>                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`|<span data-ttu-id="06b92-191"> (字串名稱) </span><span class="sxs-lookup"><span data-stu-id="06b92-191">(string name)</span></span> |<span data-ttu-id="06b92-192">記錄時要使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="06b92-192">The name to use when logging.</span></span> <span data-ttu-id="06b92-193">根據預設，</span><span class="sxs-lookup"><span data-stu-id="06b92-193">By default,</span></span>  |
|           |<span data-ttu-id="06b92-194">powershell</span><span class="sxs-lookup"><span data-stu-id="06b92-194">powershell\*</span></span>   |<span data-ttu-id="06b92-195">powershell 是身分識別。</span><span class="sxs-lookup"><span data-stu-id="06b92-195">powershell is the identity.</span></span> <span data-ttu-id="06b92-196">此值可以是</span><span class="sxs-lookup"><span data-stu-id="06b92-196">This value can be</span></span>|
|           |              |<span data-ttu-id="06b92-197">用來分辨兩者之間的差異</span><span class="sxs-lookup"><span data-stu-id="06b92-197">used to tell the difference between two</span></span>      |
|           |              |<span data-ttu-id="06b92-198">PowerShell 安裝的實例，例如</span><span class="sxs-lookup"><span data-stu-id="06b92-198">instances of a PowerShell installation, such</span></span> |
|           |              |<span data-ttu-id="06b92-199">發行版本和搶鮮版（Beta）。</span><span class="sxs-lookup"><span data-stu-id="06b92-199">as a release and beta version.</span></span> <span data-ttu-id="06b92-200">此值為</span><span class="sxs-lookup"><span data-stu-id="06b92-200">This value is</span></span> |
|           |              |<span data-ttu-id="06b92-201">也可用來將記錄檔輸出重新導向至</span><span class="sxs-lookup"><span data-stu-id="06b92-201">also used to redirect log output to a</span></span>        |
|           |              |<span data-ttu-id="06b92-202">Linux 上的個別檔案。</span><span class="sxs-lookup"><span data-stu-id="06b92-202">separate file on Linux.</span></span> <span data-ttu-id="06b92-203">請參閱</span><span class="sxs-lookup"><span data-stu-id="06b92-203">See the discussion of</span></span>|
|           |              |<span data-ttu-id="06b92-204">**rsyslog** 以上。</span><span class="sxs-lookup"><span data-stu-id="06b92-204">**rsyslog** above.</span></span>                           |
|`LogChannels`|<span data-ttu-id="06b92-205">手術</span><span class="sxs-lookup"><span data-stu-id="06b92-205">Operational\*</span></span>  |<span data-ttu-id="06b92-206">要啟用的通道。</span><span class="sxs-lookup"><span data-stu-id="06b92-206">The channels to enable.</span></span> <span data-ttu-id="06b92-207">分隔值</span><span class="sxs-lookup"><span data-stu-id="06b92-207">Separate the values</span></span>|
|           |<span data-ttu-id="06b92-208">分析</span><span class="sxs-lookup"><span data-stu-id="06b92-208">Analytic</span></span>      |<span data-ttu-id="06b92-209">指定多個時使用逗號。</span><span class="sxs-lookup"><span data-stu-id="06b92-209">with a comma when specifying more than one.</span></span>  |
|`LogLevel`   |<span data-ttu-id="06b92-210">一律</span><span class="sxs-lookup"><span data-stu-id="06b92-210">Always</span></span>        |<span data-ttu-id="06b92-211">指定單一值。</span><span class="sxs-lookup"><span data-stu-id="06b92-211">Specify a single value.</span></span> <span data-ttu-id="06b92-212">值會啟用</span><span class="sxs-lookup"><span data-stu-id="06b92-212">The value enables</span></span>  |
|           |<span data-ttu-id="06b92-213">重大</span><span class="sxs-lookup"><span data-stu-id="06b92-213">Critical</span></span>      |<span data-ttu-id="06b92-214">本身和其上方的所有值</span><span class="sxs-lookup"><span data-stu-id="06b92-214">itself and all values above it in the</span></span>        |
|           |<span data-ttu-id="06b92-215">錯誤</span><span class="sxs-lookup"><span data-stu-id="06b92-215">Error</span></span>         |<span data-ttu-id="06b92-216">列出左邊。</span><span class="sxs-lookup"><span data-stu-id="06b92-216">list to the left.</span></span>                            |
|           |<span data-ttu-id="06b92-217">警告</span><span class="sxs-lookup"><span data-stu-id="06b92-217">Warning</span></span>       |                                             |
|           |<span data-ttu-id="06b92-218">資訊</span><span class="sxs-lookup"><span data-stu-id="06b92-218">Informational\*</span></span>|                                             |
|           |<span data-ttu-id="06b92-219">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="06b92-219">Verbose</span></span>       |                                             |
|           |<span data-ttu-id="06b92-220">偵錯</span><span class="sxs-lookup"><span data-stu-id="06b92-220">Debug</span></span>         |                                             |
|`LogKeywords`|<span data-ttu-id="06b92-221">Runspace</span><span class="sxs-lookup"><span data-stu-id="06b92-221">Runspace</span></span>      |<span data-ttu-id="06b92-222">關鍵字提供限制記錄的功能</span><span class="sxs-lookup"><span data-stu-id="06b92-222">Keywords provide the ability to limit logging</span></span>|
|           |<span data-ttu-id="06b92-223">管線</span><span class="sxs-lookup"><span data-stu-id="06b92-223">Pipeline</span></span>      |<span data-ttu-id="06b92-224">PowerShell 內的特定元件。</span><span class="sxs-lookup"><span data-stu-id="06b92-224">to specific components within PowerShell.</span></span> <span data-ttu-id="06b92-225">依據</span><span class="sxs-lookup"><span data-stu-id="06b92-225">By</span></span> |
|           |<span data-ttu-id="06b92-226">通訊協定</span><span class="sxs-lookup"><span data-stu-id="06b92-226">Protocol</span></span>      |<span data-ttu-id="06b92-227">預設會啟用並變更所有關鍵詞</span><span class="sxs-lookup"><span data-stu-id="06b92-227">default, all keywords are enabled and change</span></span> |
|           |<span data-ttu-id="06b92-228">傳輸</span><span class="sxs-lookup"><span data-stu-id="06b92-228">Transport</span></span>     |<span data-ttu-id="06b92-229">此值僅適用于非常</span><span class="sxs-lookup"><span data-stu-id="06b92-229">this value is only useful for very</span></span>           |
|           |<span data-ttu-id="06b92-230">主機</span><span class="sxs-lookup"><span data-stu-id="06b92-230">Host</span></span>          |<span data-ttu-id="06b92-231">專門的疑難排解。</span><span class="sxs-lookup"><span data-stu-id="06b92-231">specialized troubleshooting.</span></span>                |
|           |<span data-ttu-id="06b92-232">指令程式</span><span class="sxs-lookup"><span data-stu-id="06b92-232">Cmdlets</span></span>       |                                             |
|           |<span data-ttu-id="06b92-233">serializer</span><span class="sxs-lookup"><span data-stu-id="06b92-233">Serializer</span></span>    |                                             |
|           |<span data-ttu-id="06b92-234">工作階段</span><span class="sxs-lookup"><span data-stu-id="06b92-234">Session</span></span>       |                                             |
|           |<span data-ttu-id="06b92-235">ManagedPlugin</span><span class="sxs-lookup"><span data-stu-id="06b92-235">ManagedPlugin</span></span> |                                             |

## <a name="see-also"></a><span data-ttu-id="06b92-236">請參閱</span><span class="sxs-lookup"><span data-stu-id="06b92-236">See also</span></span>

<span data-ttu-id="06b92-237">針對 Linux **syslog** 和 **rsyslog** 資訊，請參閱 linux 電腦的本機 `man` 頁面。</span><span class="sxs-lookup"><span data-stu-id="06b92-237">For Linux **syslog** and **rsyslog.conf** information, refer to the Linux computer's local `man` pages.</span></span>

<span data-ttu-id="06b92-238">如需 macOS **os_log** 資訊，請參閱 [os_log 開發人員檔](https://developer.apple.com/documentation/os/os_log)。</span><span class="sxs-lookup"><span data-stu-id="06b92-238">For macOS **os_log** information, see [os_log developer documentation](https://developer.apple.com/documentation/os/os_log).</span></span>

[<span data-ttu-id="06b92-239">about_Logging_Windows</span><span class="sxs-lookup"><span data-stu-id="06b92-239">about_Logging_Windows</span></span>](about_Logging_Windows.md)

[<span data-ttu-id="06b92-240">一般 SIEM 整合</span><span class="sxs-lookup"><span data-stu-id="06b92-240">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
