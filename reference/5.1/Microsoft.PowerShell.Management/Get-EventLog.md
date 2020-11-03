---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 3/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventLog
ms.openlocfilehash: ab1a97dc3c78bbfdcc239fd573ef3b1f839e2b21
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204020"
---
# <span data-ttu-id="37da2-103">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="37da2-103">Get-EventLog</span></span>

## <span data-ttu-id="37da2-104">概要</span><span class="sxs-lookup"><span data-stu-id="37da2-104">SYNOPSIS</span></span>
<span data-ttu-id="37da2-105">取得本機電腦或遠端電腦上事件記錄檔中的事件，或事件記錄檔的清單。</span><span class="sxs-lookup"><span data-stu-id="37da2-105">Gets the events in an event log, or a list of the event logs, on the local computer or remote computers.</span></span>

## <span data-ttu-id="37da2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="37da2-106">SYNTAX</span></span>

### <span data-ttu-id="37da2-107">LogName (預設值)</span><span class="sxs-lookup"><span data-stu-id="37da2-107">LogName (Default)</span></span>

```
Get-EventLog [-LogName] <String> [-ComputerName <String[]>] [-Newest <Int32>] [-After <DateTime>]
 [-Before <DateTime>] [-UserName <String[]>] [[-InstanceId] <Int64[]>] [-Index <Int32[]>]
 [-EntryType <String[]>] [-Source <String[]>] [-Message <String>] [-AsBaseObject]
 [<CommonParameters>]
```

### <span data-ttu-id="37da2-108">清單</span><span class="sxs-lookup"><span data-stu-id="37da2-108">List</span></span>

```
Get-EventLog [-ComputerName <String[]>] [-List] [-AsString] [<CommonParameters>]
```

## <span data-ttu-id="37da2-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="37da2-109">DESCRIPTION</span></span>

<span data-ttu-id="37da2-110">`Get-EventLog`Cmdlet 會從本機和遠端電腦取得事件和事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37da2-110">The `Get-EventLog` cmdlet gets events and event logs from local and remote computers.</span></span> <span data-ttu-id="37da2-111">根據預設，會 `Get-EventLog` 從本機電腦取得記錄。</span><span class="sxs-lookup"><span data-stu-id="37da2-111">By default, `Get-EventLog` gets logs from the local computer.</span></span> <span data-ttu-id="37da2-112">若要從遠端電腦取得記錄，請使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="37da2-112">To get logs from remote computers, use the **ComputerName** parameter.</span></span>

<span data-ttu-id="37da2-113">您可以使用 `Get-EventLog` 參數和屬性值來搜尋事件。</span><span class="sxs-lookup"><span data-stu-id="37da2-113">You can use the `Get-EventLog` parameters and property values to search for events.</span></span> <span data-ttu-id="37da2-114">Cmdlet 會取得符合指定屬性值的事件。</span><span class="sxs-lookup"><span data-stu-id="37da2-114">The cmdlet gets events that match the specified property values.</span></span>

<span data-ttu-id="37da2-115">包含名詞的 PowerShell Cmdlet `EventLog` 僅適用于 Windows 傳統事件記錄檔，例如應用程式、系統或安全性。</span><span class="sxs-lookup"><span data-stu-id="37da2-115">PowerShell cmdlets that contain the `EventLog` noun work only on Windows classic event logs such as Application, System, or Security.</span></span> <span data-ttu-id="37da2-116">若要在 Windows Vista 和更新版本的 Windows 中取得使用 Windows 事件記錄檔技術的記錄，請使用 `Get-WinEvent` 。</span><span class="sxs-lookup"><span data-stu-id="37da2-116">To get logs that use the Windows Event Log technology in Windows Vista and later Windows versions, use `Get-WinEvent`.</span></span>

> [!NOTE]
> <span data-ttu-id="37da2-117">`Get-EventLog` 使用已被取代的 WIN32 API。</span><span class="sxs-lookup"><span data-stu-id="37da2-117">`Get-EventLog` uses a Win32 API that is deprecated.</span></span> <span data-ttu-id="37da2-118">結果可能不正確。</span><span class="sxs-lookup"><span data-stu-id="37da2-118">The results may not be accurate.</span></span> <span data-ttu-id="37da2-119">請改用 `Get-WinEvent` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37da2-119">Use the `Get-WinEvent` cmdlet instead.</span></span>

## <span data-ttu-id="37da2-120">範例</span><span class="sxs-lookup"><span data-stu-id="37da2-120">EXAMPLES</span></span>

### <span data-ttu-id="37da2-121">範例1：取得本機電腦上的事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="37da2-121">Example 1: Get event logs on the local computer</span></span>

<span data-ttu-id="37da2-122">此範例會顯示本機電腦上可用的事件記錄檔清單。</span><span class="sxs-lookup"><span data-stu-id="37da2-122">This example displays the list of event logs that are available on the local computer.</span></span> <span data-ttu-id="37da2-123">Log 資料行中的名稱會與 **LogName** 參數搭配使用，以指定要搜尋事件的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37da2-123">The names in the Log column are used with the **LogName** parameter to specify which log is searched for events.</span></span>

```powershell
Get-EventLog -List
```

```Output
Max(K)   Retain   OverflowAction      Entries  Log
------   ------   --------------      -------  ---
15,168        0   OverwriteAsNeeded   20,792   Application
15,168        0   OverwriteAsNeeded   12,559   System
15,360        0   OverwriteAsNeeded   11,173   Windows PowerShell
```

<span data-ttu-id="37da2-124">此 `Get-EventLog` Cmdlet 會使用 **List** 參數來顯示可用的記錄。</span><span class="sxs-lookup"><span data-stu-id="37da2-124">The `Get-EventLog` cmdlet uses the **List** parameter to display the available logs.</span></span>

### <span data-ttu-id="37da2-125">範例2：從本機電腦上的事件記錄檔取得最近的專案</span><span class="sxs-lookup"><span data-stu-id="37da2-125">Example 2: Get recent entries from an event log on the local computer</span></span>

<span data-ttu-id="37da2-126">此範例會從系統事件記錄檔取得最近的專案。</span><span class="sxs-lookup"><span data-stu-id="37da2-126">This example gets recent entries from the System event log.</span></span>

```powershell
Get-EventLog -LogName System -Newest 5
```

```Output
Index   Time          EntryType    Source              InstanceID   Message
-----   ----          ---------    ------              ----------   -------
13820   Jan 17 19:16  Error        DCOM                     10016   The description for Event...
13819   Jan 17 19:08  Error        DCOM                     10016   The description for Event...
13818   Jan 17 19:06  Information  Service Control...  1073748864   The start type of the Back...
13817   Jan 17 19:05  Error        DCOM                     10016   The description for Event...
13815   Jan 17 19:03  Information  Microsoft-Windows...        35   The time service is now sync...
```

<span data-ttu-id="37da2-127">此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37da2-127">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="37da2-128">**最新** 的參數會傳回五個最新的事件。</span><span class="sxs-lookup"><span data-stu-id="37da2-128">The **Newest** parameter returns the five most recent events.</span></span>

### <span data-ttu-id="37da2-129">範例3：在事件記錄檔中尋找特定專案數的所有來源</span><span class="sxs-lookup"><span data-stu-id="37da2-129">Example 3: Find all sources for a specific number of entries in an event log</span></span>

<span data-ttu-id="37da2-130">此範例示範如何尋找 System 事件記錄檔中1000最新專案所包含的所有來源。</span><span class="sxs-lookup"><span data-stu-id="37da2-130">This example shows how to find all of the sources that are included in the 1000 most recent entries in the System event log.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$Events | Group-Object -Property Source -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count   Name
-----   ----
  110   DCOM
   65   Service Control Manager
   51   Microsoft-Windows-Kern...
   14   EventLog
   14   BTHUSB
   13   Win32k
```

<span data-ttu-id="37da2-131">此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37da2-131">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="37da2-132">**最新** 的參數會選取1000的最新事件。</span><span class="sxs-lookup"><span data-stu-id="37da2-132">The **Newest** parameter selects the 1000 most recent events.</span></span> <span data-ttu-id="37da2-133">事件物件會儲存在變數中 `$Events` 。</span><span class="sxs-lookup"><span data-stu-id="37da2-133">The event objects are stored in the `$Events` variable.</span></span> <span data-ttu-id="37da2-134">這些 `$Events` 物件會向下傳送至 `Group-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37da2-134">The `$Events` objects are sent down the pipeline to the `Group-Object` cmdlet.</span></span>
<span data-ttu-id="37da2-135">`Group-Object` 使用 **Property** 參數依來源將物件分組，並計算每個來源的物件數目。</span><span class="sxs-lookup"><span data-stu-id="37da2-135">`Group-Object` uses the **Property** parameter to group the objects by source and counts the number of objects for each source.</span></span> <span data-ttu-id="37da2-136">**NoElement** 參數會從輸出中移除群組成員。</span><span class="sxs-lookup"><span data-stu-id="37da2-136">The **NoElement** parameter removes the group members from the output.</span></span>
<span data-ttu-id="37da2-137">此 `Sort-Object` Cmdlet 會使用 **Property** 參數，依每個來源名稱的計數排序。</span><span class="sxs-lookup"><span data-stu-id="37da2-137">The `Sort-Object` cmdlet uses the **Property** parameter to sort by the count of each source name.</span></span>
<span data-ttu-id="37da2-138">**遞減** 的參數會依計數排序清單（從最高到最低）。</span><span class="sxs-lookup"><span data-stu-id="37da2-138">The **Descending** parameter sorts the list in order by count from highest to lowest.</span></span>

### <span data-ttu-id="37da2-139">範例4：取得特定事件記錄檔中的錯誤事件</span><span class="sxs-lookup"><span data-stu-id="37da2-139">Example 4: Get error events from a specific event log</span></span>

<span data-ttu-id="37da2-140">此範例會從系統事件記錄檔中取得錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="37da2-140">This example gets error events from the System event log.</span></span>

```powershell
Get-EventLog -LogName System -EntryType Error
```

```Output
Index Time          EntryType   Source  InstanceID Message
----- ----          ---------   ------  ---------- -------
13296 Jan 16 13:53  Error       DCOM    10016 The description for Event ID '10016' in Source...
13291 Jan 16 13:51  Error       DCOM    10016 The description for Event ID '10016' in Source...
13245 Jan 16 11:45  Error       DCOM    10016 The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error       DCOM    10016 The description for Event ID '10016' in Source...
```

<span data-ttu-id="37da2-141">此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37da2-141">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="37da2-142">**>entrytype** 參數會篩選事件，只顯示錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="37da2-142">The **EntryType** parameter filters the events to show only Error events.</span></span>

### <span data-ttu-id="37da2-143">範例5：從含有 InstanceId 和來源值的事件記錄檔取得事件</span><span class="sxs-lookup"><span data-stu-id="37da2-143">Example 5: Get events from an event log with an InstanceId and Source value</span></span>

<span data-ttu-id="37da2-144">此範例會從系統記錄檔取得特定 InstanceId 和來源的事件。</span><span class="sxs-lookup"><span data-stu-id="37da2-144">This example gets events from the System log for a specific InstanceId and Source.</span></span>

```powershell
Get-EventLog -LogName System -InstanceId 10016 -Source DCOM
```

```Output
Index Time          EntryType  Source  InstanceID  Message
----- ----          ---------  ------  ----------  -------
13245 Jan 16 11:45  Error      DCOM         10016  The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error      DCOM         10016  The description for Event ID '10016' in Source...
13219 Jan 16 10:00  Error      DCOM         10016  The description for Event ID '10016' in Source...
```

<span data-ttu-id="37da2-145">此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37da2-145">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="37da2-146">**InstanceID** 參數會選取具有指定實例識別碼的事件。</span><span class="sxs-lookup"><span data-stu-id="37da2-146">The **InstanceID** parameter selects the events with the specified Instance ID.</span></span> <span data-ttu-id="37da2-147">**Source** 參數指定事件屬性。</span><span class="sxs-lookup"><span data-stu-id="37da2-147">The **Source** parameter specifies the event property.</span></span>

### <span data-ttu-id="37da2-148">範例6：從多部電腦取得事件</span><span class="sxs-lookup"><span data-stu-id="37da2-148">Example 6: Get events from multiple computers</span></span>

<span data-ttu-id="37da2-149">此命令會從三部電腦上的系統事件記錄檔取得事件： Server01、Server02 和 Server03。</span><span class="sxs-lookup"><span data-stu-id="37da2-149">This command gets the events from the System event log on three computers: Server01, Server02, and Server03.</span></span>

```powershell
Get-EventLog -LogName System -ComputerName Server01, Server02, Server03
```

<span data-ttu-id="37da2-150">此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37da2-150">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="37da2-151">**ComputerName** 參數使用逗點分隔字串來列出您要從中取得事件記錄檔的電腦。</span><span class="sxs-lookup"><span data-stu-id="37da2-151">The **ComputerName** parameter uses a comma-separated string to list the computers from which you want to get the event logs.</span></span>

### <span data-ttu-id="37da2-152">範例7：取得訊息中包含特定單字的所有事件</span><span class="sxs-lookup"><span data-stu-id="37da2-152">Example 7: Get all events that include a specific word in the message</span></span>

<span data-ttu-id="37da2-153">此命令會取得系統事件記錄檔中的所有事件，該事件記錄檔中包含事件訊息中的特定字組。</span><span class="sxs-lookup"><span data-stu-id="37da2-153">This command gets all the events in the System event log that contain a specific word in the event's message.</span></span> <span data-ttu-id="37da2-154">您指定的 **訊息** 參數值可能會包含在訊息的內容中，但不會顯示在 PowerShell 主控台上。</span><span class="sxs-lookup"><span data-stu-id="37da2-154">It's possible that your specified **Message** parameter's value is included in the message's content but isn't displayed on the PowerShell console.</span></span>

```powershell
Get-EventLog -LogName System -Message *description*
```

```Output
Index Time          EntryType   Source       InstanceID   Message
----- ----          ---------   ------       ----------   -------
13821 Jan 17 19:17  Error       DCOM              10016   The description for Event ID '10016'...
13820 Jan 17 19:16  Error       DCOM              10016   The description for Event ID '10016'...
13819 Jan 17 19:08  Error       DCOM              10016   The description for Event ID '10016'...
```

<span data-ttu-id="37da2-155">此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37da2-155">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="37da2-156">**Message** 參數會在每個事件的 message 欄位中指定要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="37da2-156">The **Message** parameter specifies a word to search for in the message field of each event.</span></span>

### <span data-ttu-id="37da2-157">範例8：顯示事件的屬性值</span><span class="sxs-lookup"><span data-stu-id="37da2-157">Example 8: Display the property values of an event</span></span>

<span data-ttu-id="37da2-158">此範例示範如何顯示所有事件的屬性和值。</span><span class="sxs-lookup"><span data-stu-id="37da2-158">This example shows how to display all of an event's properties and values.</span></span>

```powershell
$A = Get-EventLog -LogName System -Newest 1
$A | Select-Object -Property *
```

```Output
EventID            : 10016
MachineName        : localhost
Data               : {}
Index              : 13821
Category           : (0)
CategoryNumber     : 0
EntryType          : Error
Message            : The description for Event ID '10016' in Source 'DCOM'...
Source             : DCOM
ReplacementStrings : {Local,...}
InstanceId         : 10016
TimeGenerated      : 1/17/2019 19:17:23
TimeWritten        : 1/17/2019 19:17:23
UserName           : username
Site               :
Container          :
```

<span data-ttu-id="37da2-159">此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37da2-159">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="37da2-160">**最新** 的參數會選取最新的事件物件。</span><span class="sxs-lookup"><span data-stu-id="37da2-160">The **Newest** parameter selects the most recent event object.</span></span> <span data-ttu-id="37da2-161">物件會儲存在變數中 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="37da2-161">The object is stored in the `$A` variable.</span></span> <span data-ttu-id="37da2-162">變數中的物件 `$A` 會向下傳送至 `Select-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37da2-162">The object in the `$A` variable is sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="37da2-163">`Select-Object` 使用 **Property** 參數搭配星號 (`*`) 來選取物件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="37da2-163">`Select-Object` uses the **Property** parameter with an asterisk (`*`) to select all of the object's properties.</span></span>

### <span data-ttu-id="37da2-164">範例9：使用來源和事件識別碼從事件記錄檔取得事件</span><span class="sxs-lookup"><span data-stu-id="37da2-164">Example 9: Get events from an event log using a source and event ID</span></span>

<span data-ttu-id="37da2-165">這個範例會取得指定之來源和事件識別碼的事件。</span><span class="sxs-lookup"><span data-stu-id="37da2-165">This example gets events for a specified Source and Event ID.</span></span>

```powershell
Get-EventLog -LogName Application -Source Outlook | Where-Object {$_.EventID -eq 63} |
              Select-Object -Property Source, EventID, InstanceId, Message
```

```Output
Source   EventID   InstanceId   Message
------   -------   ----------   -------
Outlook       63   1073741887   The Exchange web service request succeeded.
Outlook       63   1073741887   Outlook detected a change notification.
Outlook       63   1073741887   The Exchange web service request succeeded.
```

<span data-ttu-id="37da2-166">此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37da2-166">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the Application event log.</span></span> <span data-ttu-id="37da2-167">**Source** 參數指定應用程式名稱，Outlook。</span><span class="sxs-lookup"><span data-stu-id="37da2-167">The **Source** parameter specifies the application name, Outlook.</span></span> <span data-ttu-id="37da2-168">這些物件會向下傳送至 `Where-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37da2-168">The objects are sent down the pipeline to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="37da2-169">針對管線中的每個物件，此 `Where-Object` Cmdlet 會使用變數 `$_.EventID` 來比較事件識別碼屬性與指定的值。</span><span class="sxs-lookup"><span data-stu-id="37da2-169">For each object in the pipeline, the `Where-Object` cmdlet uses the variable `$_.EventID` to compare the Event ID property to the specified value.</span></span> <span data-ttu-id="37da2-170">這些物件會向下傳送至 `Select-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37da2-170">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="37da2-171">`Select-Object` 使用 **Property** 參數來選取要在 PowerShell 主控台中顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="37da2-171">`Select-Object` uses the **Property** parameter to select the properties to display in the PowerShell console.</span></span>

### <span data-ttu-id="37da2-172">範例10：依屬性取得事件和群組</span><span class="sxs-lookup"><span data-stu-id="37da2-172">Example 10: Get events and group by a property</span></span>

```powershell
Get-EventLog -LogName System -UserName NT* | Group-Object -Property UserName -NoElement |
              Select-Object -Property Count, Name
```

```Output
Count  Name
-----  ----
6031   NT AUTHORITY\SYSTEM
  42   NT AUTHORITY\LOCAL SERVICE
   4   NT AUTHORITY\NETWORK SERVICE
```

<span data-ttu-id="37da2-173">此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37da2-173">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="37da2-174">**UserName** 參數包含星號 (`*`) 萬用字元來指定使用者名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="37da2-174">The **UserName** parameter includes the asterisk (`*`) wildcard to specify a portion of the user name.</span></span> <span data-ttu-id="37da2-175">事件物件會以管線傳送至 `Group-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37da2-175">The event objects are sent down the pipeline to the `Group-Object` cmdlet.</span></span> <span data-ttu-id="37da2-176">`Group-Object` 使用 **Property** 參數來指定 **UserName** 屬性是用來將物件分組，並計算每個使用者名稱的物件數目。</span><span class="sxs-lookup"><span data-stu-id="37da2-176">`Group-Object` uses the **Property** parameter to specify that the **UserName** property is used to group the objects and count the number of objects for each user name.</span></span> <span data-ttu-id="37da2-177">**NoElement** 參數會從輸出中移除群組成員。</span><span class="sxs-lookup"><span data-stu-id="37da2-177">The **NoElement** parameter removes the group members from the output.</span></span> <span data-ttu-id="37da2-178">這些物件會向下傳送至 `Select-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="37da2-178">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="37da2-179">`Select-Object` 使用 **Property** 參數來選取要在 PowerShell 主控台中顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="37da2-179">`Select-Object` uses the **Property** parameter to select the properties to display in the PowerShell console.</span></span>

### <span data-ttu-id="37da2-180">範例11：取得特定日期和時間範圍內發生的事件</span><span class="sxs-lookup"><span data-stu-id="37da2-180">Example 11: Get events that occurred during a specific date and time range</span></span>

<span data-ttu-id="37da2-181">此範例會取得系統事件記錄檔中指定日期和時間範圍的錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="37da2-181">This example gets Error events from the System event log for a specified date and time range.</span></span> <span data-ttu-id="37da2-182">**Before** 和 **After** 參數會設定日期和時間範圍，但會從輸出中排除。</span><span class="sxs-lookup"><span data-stu-id="37da2-182">The **Before** and **After** parameters set the date and time range but are excluded from the output.</span></span>

```powershell
$Begin = Get-Date -Date '1/17/2019 08:00:00'
$End = Get-Date -Date '1/17/2019 17:00:00'
Get-EventLog -LogName System -EntryType Error -After $Begin -Before $End
```

```Output
Index Time          EntryType   Source   InstanceID  Message
----- ----          ---------   ------   ----------  -------
13821 Jan 17 13:40  Error       DCOM          10016  The description for Event ID...
13820 Jan 17 13:11  Error       DCOM          10016  The description for Event ID...
...
12372 Jan 17 10:08  Error       DCOM          10016  The description for Event ID...
12371 Jan 17 09:04  Error       DCOM          10016  The description for Event ID...
```

<span data-ttu-id="37da2-183">此 `Get-Date` Cmdlet 會使用 **date** 參數來指定日期和時間。</span><span class="sxs-lookup"><span data-stu-id="37da2-183">The `Get-Date` cmdlet uses the **Date** parameter to specify a date and time.</span></span> <span data-ttu-id="37da2-184">**DateTime** 物件會儲存在 `$Begin` 和變數中 `$End` 。</span><span class="sxs-lookup"><span data-stu-id="37da2-184">The **DateTime** objects are stored in the `$Begin` and `$End` variables.</span></span> <span data-ttu-id="37da2-185">此 `Get-EventLog` Cmdlet 會使用 **LogName** 參數來指定系統記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37da2-185">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="37da2-186">**>entrytype** 參數會指定錯誤事件種類。</span><span class="sxs-lookup"><span data-stu-id="37da2-186">The **EntryType** parameter specifies the Error event type.</span></span> <span data-ttu-id="37da2-187">日期和時間範圍是由 **After** 參數和 `$Begin` 變數以及 **Before** 參數和變數所設定 `$End` 。</span><span class="sxs-lookup"><span data-stu-id="37da2-187">The date and time range is set by the **After** parameter and `$Begin` variable and the **Before** parameter and `$End` variable.</span></span>

## <span data-ttu-id="37da2-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="37da2-188">PARAMETERS</span></span>

### <span data-ttu-id="37da2-189">-After</span><span class="sxs-lookup"><span data-stu-id="37da2-189">-After</span></span>

<span data-ttu-id="37da2-190">取得在指定的日期和時間之後發生的事件。</span><span class="sxs-lookup"><span data-stu-id="37da2-190">Gets events that occurred after a specified date and time.</span></span> <span data-ttu-id="37da2-191">**After** 參數日期和時間會從輸出中排除。</span><span class="sxs-lookup"><span data-stu-id="37da2-191">The **After** parameter date and time are excluded from the output.</span></span> <span data-ttu-id="37da2-192">輸入 **DateTime** 物件，例如 Cmdlet 所傳回的值 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="37da2-192">Enter a **DateTime** object, such as the value returned by the `Get-Date` cmdlet.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37da2-193">-AsBaseObject</span><span class="sxs-lookup"><span data-stu-id="37da2-193">-AsBaseObject</span></span>

<span data-ttu-id="37da2-194">指出此 Cmdlet 會傳回每個事件的標準 **EventLogEntry** 物件。</span><span class="sxs-lookup"><span data-stu-id="37da2-194">Indicates that this cmdlet returns a standard **System.Diagnostics.EventLogEntry** object for each event.</span></span> <span data-ttu-id="37da2-195">如果沒有這個參數，則會傳回 `Get-EventLog` 具有其他 **EventLogName** 、 **Source** 和 **InstanceId** 屬性的擴充 **PSObject** 物件。</span><span class="sxs-lookup"><span data-stu-id="37da2-195">Without this parameter, `Get-EventLog` returns an extended **PSObject** object with additional **EventLogName** , **Source** , and **InstanceId** properties.</span></span>

<span data-ttu-id="37da2-196">若要查看這個參數的效果，請透過管線將事件傳送至 `Get-Member` Cmdlet，然後檢查結果中的 **TypeName** 值。</span><span class="sxs-lookup"><span data-stu-id="37da2-196">To see the effect of this parameter, pipe the events to the `Get-Member` cmdlet and examine the **TypeName** value in the result.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37da2-197">-AsString</span><span class="sxs-lookup"><span data-stu-id="37da2-197">-AsString</span></span>

<span data-ttu-id="37da2-198">指出此 Cmdlet 會以字串形式傳回輸出，而不是以物件的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="37da2-198">Indicates that this cmdlet returns the output as strings, instead of objects.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37da2-199">-Before</span><span class="sxs-lookup"><span data-stu-id="37da2-199">-Before</span></span>

<span data-ttu-id="37da2-200">取得在指定的日期和時間之前發生的事件。</span><span class="sxs-lookup"><span data-stu-id="37da2-200">Gets events that occurred before a specified date and time.</span></span> <span data-ttu-id="37da2-201">從輸出中排除 **之前** 的參數日期和時間。</span><span class="sxs-lookup"><span data-stu-id="37da2-201">The **Before** parameter date and time are excluded from the output.</span></span> <span data-ttu-id="37da2-202">輸入 **DateTime** 物件，例如 Cmdlet 所傳回的值 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="37da2-202">Enter a **DateTime** object, such as the value returned by the `Get-Date` cmdlet.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37da2-203">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="37da2-203">-ComputerName</span></span>

<span data-ttu-id="37da2-204">此參數會指定遠端電腦的 NetBIOS 名稱、網際網路通訊協定 (IP) 位址，或 (FQDN) 的完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="37da2-204">This parameter specifies a remote computer's NetBIOS name, Internet Protocol (IP) address, or a fully qualified domain name (FQDN).</span></span>

<span data-ttu-id="37da2-205">如果未指定 **ComputerName** 參數，則 `Get-EventLog` 預設為本機電腦。</span><span class="sxs-lookup"><span data-stu-id="37da2-205">If the **ComputerName** parameter isn't specified, `Get-EventLog` defaults to the local computer.</span></span> <span data-ttu-id="37da2-206">參數也接受點 (`.`) 來指定本機電腦。</span><span class="sxs-lookup"><span data-stu-id="37da2-206">The parameter also accepts a dot (`.`) to specify the local computer.</span></span>

<span data-ttu-id="37da2-207">**ComputerName** 參數不依賴 Windows PowerShell 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="37da2-207">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="37da2-208">`Get-EventLog`即使您的電腦未設定為執行遠端命令，您也可以使用 With **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="37da2-208">You can use `Get-EventLog` with the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37da2-209">-EntryType</span><span class="sxs-lookup"><span data-stu-id="37da2-209">-EntryType</span></span>

<span data-ttu-id="37da2-210">以字串陣列指定此 Cmdlet 所取得事件的專案類型。</span><span class="sxs-lookup"><span data-stu-id="37da2-210">Specifies, as a string array, the entry type of the events that this cmdlet gets.</span></span>

<span data-ttu-id="37da2-211">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="37da2-211">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="37da2-212">錯誤</span><span class="sxs-lookup"><span data-stu-id="37da2-212">Error</span></span>
- <span data-ttu-id="37da2-213">資訊</span><span class="sxs-lookup"><span data-stu-id="37da2-213">Information</span></span>
- <span data-ttu-id="37da2-214">FailureAudit</span><span class="sxs-lookup"><span data-stu-id="37da2-214">FailureAudit</span></span>
- <span data-ttu-id="37da2-215">SuccessAudit</span><span class="sxs-lookup"><span data-stu-id="37da2-215">SuccessAudit</span></span>
- <span data-ttu-id="37da2-216">警告</span><span class="sxs-lookup"><span data-stu-id="37da2-216">Warning</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37da2-217">-Index</span><span class="sxs-lookup"><span data-stu-id="37da2-217">-Index</span></span>

<span data-ttu-id="37da2-218">指定要從事件記錄檔中取得的索引值。</span><span class="sxs-lookup"><span data-stu-id="37da2-218">Specifies the index values to get from the event log.</span></span> <span data-ttu-id="37da2-219">參數接受以逗號分隔的值字串。</span><span class="sxs-lookup"><span data-stu-id="37da2-219">The parameter accepts a comma-separated string of values.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37da2-220">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="37da2-220">-InstanceId</span></span>

<span data-ttu-id="37da2-221">指定要從事件記錄檔取得的實例識別碼。</span><span class="sxs-lookup"><span data-stu-id="37da2-221">Specifies the Instance IDs to get from the event log.</span></span> <span data-ttu-id="37da2-222">參數接受以逗號分隔的值字串。</span><span class="sxs-lookup"><span data-stu-id="37da2-222">The parameter accepts a comma-separated string of values.</span></span>

```yaml
Type: System.Int64[]
Parameter Sets: LogName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37da2-223">-List</span><span class="sxs-lookup"><span data-stu-id="37da2-223">-List</span></span>

<span data-ttu-id="37da2-224">顯示電腦上的事件記錄檔清單。</span><span class="sxs-lookup"><span data-stu-id="37da2-224">Displays the list of event logs on the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37da2-225">-LogName</span><span class="sxs-lookup"><span data-stu-id="37da2-225">-LogName</span></span>

<span data-ttu-id="37da2-226">指定一個事件記錄檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="37da2-226">Specifies the name of one event log.</span></span> <span data-ttu-id="37da2-227">以尋找記錄檔名稱的使用 `Get-EventLog -List` 。</span><span class="sxs-lookup"><span data-stu-id="37da2-227">To find the log names use `Get-EventLog -List`.</span></span> <span data-ttu-id="37da2-228">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="37da2-228">Wildcard characters are permitted.</span></span> <span data-ttu-id="37da2-229">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="37da2-229">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="37da2-230">-Message</span><span class="sxs-lookup"><span data-stu-id="37da2-230">-Message</span></span>

<span data-ttu-id="37da2-231">指定事件訊息中的字串。</span><span class="sxs-lookup"><span data-stu-id="37da2-231">Specifies a string in the event message.</span></span> <span data-ttu-id="37da2-232">您可以使用這個參數來搜尋包含特定單字或片語的訊息。</span><span class="sxs-lookup"><span data-stu-id="37da2-232">You can use this parameter to search for messages that contain certain words or phrases.</span></span> <span data-ttu-id="37da2-233">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="37da2-233">Wildcards are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: MSG

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="37da2-234">-Newest</span><span class="sxs-lookup"><span data-stu-id="37da2-234">-Newest</span></span>

<span data-ttu-id="37da2-235">開頭為最新的事件，並取得指定的事件數目。</span><span class="sxs-lookup"><span data-stu-id="37da2-235">Begins with the newest events and gets the specified number of events.</span></span> <span data-ttu-id="37da2-236">例如，需要事件的數目 `-Newest 100` 。</span><span class="sxs-lookup"><span data-stu-id="37da2-236">The number of events is required, for example `-Newest 100`.</span></span> <span data-ttu-id="37da2-237">指定傳回的最大事件數目。</span><span class="sxs-lookup"><span data-stu-id="37da2-237">Specifies the maximum number of events that are returned.</span></span>

```yaml
Type: System.Int32
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="37da2-238">-Source</span><span class="sxs-lookup"><span data-stu-id="37da2-238">-Source</span></span>

<span data-ttu-id="37da2-239">以字串陣列的形式指定寫入至這個 Cmdlet 取得之記錄檔的來源。</span><span class="sxs-lookup"><span data-stu-id="37da2-239">Specifies, as a string array, sources that were written to the log that this cmdlet gets.</span></span> <span data-ttu-id="37da2-240">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="37da2-240">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ABO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="37da2-241">-UserName</span><span class="sxs-lookup"><span data-stu-id="37da2-241">-UserName</span></span>

<span data-ttu-id="37da2-242">將與事件相關聯的使用者名稱指定為字串陣列。</span><span class="sxs-lookup"><span data-stu-id="37da2-242">Specifies, as a string array, user names that are associated with events.</span></span> <span data-ttu-id="37da2-243">輸入名稱或名稱模式，例如 `User01` 、 `User*` 或 `Domain01\User*` 。</span><span class="sxs-lookup"><span data-stu-id="37da2-243">Enter names or name patterns, such as `User01`, `User*`, or `Domain01\User*`.</span></span> <span data-ttu-id="37da2-244">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="37da2-244">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="37da2-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="37da2-245">CommonParameters</span></span>

<span data-ttu-id="37da2-246">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="37da2-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="37da2-247">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="37da2-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="37da2-248">輸入</span><span class="sxs-lookup"><span data-stu-id="37da2-248">INPUTS</span></span>

### <span data-ttu-id="37da2-249">無</span><span class="sxs-lookup"><span data-stu-id="37da2-249">None</span></span>

<span data-ttu-id="37da2-250">您無法透過管道傳送輸入 `Get-EventLog` 。</span><span class="sxs-lookup"><span data-stu-id="37da2-250">You cannot pipe input to `Get-EventLog`.</span></span>

## <span data-ttu-id="37da2-251">輸出</span><span class="sxs-lookup"><span data-stu-id="37da2-251">OUTPUTS</span></span>

### <span data-ttu-id="37da2-252">System.Diagnostics.EventLogEntry。</span><span class="sxs-lookup"><span data-stu-id="37da2-252">System.Diagnostics.EventLogEntry.</span></span> <span data-ttu-id="37da2-253">System.Diagnostics.EventLog。</span><span class="sxs-lookup"><span data-stu-id="37da2-253">System.Diagnostics.EventLog.</span></span> <span data-ttu-id="37da2-254">System.String</span><span class="sxs-lookup"><span data-stu-id="37da2-254">System.String</span></span>

<span data-ttu-id="37da2-255">如果指定了 **LogName** 參數，輸出就會是 **EventLogEntry** 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="37da2-255">If the **LogName** parameter is specified, the output is a collection of **System.Diagnostics.EventLogEntry** objects.</span></span>

<span data-ttu-id="37da2-256">如果只指定 **List** 參數，則輸出會是 **系統** 記錄檔物件的集合。</span><span class="sxs-lookup"><span data-stu-id="37da2-256">If only the **List** parameter is specified, the output is a collection of **System.Diagnostics.EventLog** objects.</span></span>

<span data-ttu-id="37da2-257">如果同時指定 **List** 和 **AsString** 參數，則輸出會是 **system.string** 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="37da2-257">If both the **List** and **AsString** parameters are specified, the output is a collection of **System.String** objects.</span></span>

## <span data-ttu-id="37da2-258">注意</span><span class="sxs-lookup"><span data-stu-id="37da2-258">NOTES</span></span>

<span data-ttu-id="37da2-259">`Get-EventLog` `Get-WinEvent` Windows 預先安裝環境 (Windows PE) 不支援 Cmdlet 和。</span><span class="sxs-lookup"><span data-stu-id="37da2-259">The cmdlets `Get-EventLog` and `Get-WinEvent` are not supported in the Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="37da2-260">相關連結</span><span class="sxs-lookup"><span data-stu-id="37da2-260">RELATED LINKS</span></span>

[<span data-ttu-id="37da2-261">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="37da2-261">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="37da2-262">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="37da2-262">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="37da2-263">Group-Object</span><span class="sxs-lookup"><span data-stu-id="37da2-263">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="37da2-264">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="37da2-264">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="37da2-265">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="37da2-265">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="37da2-266">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="37da2-266">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="37da2-267">Select-Object</span><span class="sxs-lookup"><span data-stu-id="37da2-267">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="37da2-268">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="37da2-268">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="37da2-269">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="37da2-269">Write-EventLog</span></span>](Write-EventLog.md)
