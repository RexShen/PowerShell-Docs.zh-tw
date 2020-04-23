---
ms.date: 09/13/2019
title: 使用 FilterHashtable 建立 Get-WinEvent 查詢
ms.openlocfilehash: 35d18dc894d90e698b38395b79ff4cf395515909
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "73444380"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="175eb-102">使用 FilterHashtable 建立 Get-WinEvent 查詢</span><span class="sxs-lookup"><span data-stu-id="175eb-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="175eb-103">若要閱讀原始的 2014 年 6 月 3 日 **Scripting Guy** 部落格文章，請參閱[使用 FilterHashTable 搭配 PowerShell 篩選事件記錄檔](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="175eb-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="175eb-104">本文是原始部落格文章的摘錄，並說明如何使用 `Get-WinEvent` Cmdlet 的 **FilterHashtable** 參數來篩選事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="175eb-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="175eb-105">PowerShell 的 `Get-WinEvent` Cmdlet 是一種功能強大的方法，可篩選 Windows 事件和診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="175eb-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="175eb-106">`Get-WinEvent` 查詢使用 **FilterHashtable** 參數時，效能會提高。</span><span class="sxs-lookup"><span data-stu-id="175eb-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="175eb-107">當您使用大型事件記錄檔時，將管線中的物件傳送到 `Where-Object` 命令不是有效率的方式。</span><span class="sxs-lookup"><span data-stu-id="175eb-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="175eb-108">在 PowerShell 6 之前，`Get-EventLog` Cmdlet 是取得記錄資料的另一個選項。</span><span class="sxs-lookup"><span data-stu-id="175eb-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="175eb-109">例如，下列命令篩選 **Microsoft-Windows-Defrag** 記錄檔的效率不佳：</span><span class="sxs-lookup"><span data-stu-id="175eb-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

```powershell
Get-EventLog -LogName Application | Where-Object Source -Match defrag

Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }
```

<span data-ttu-id="175eb-110">下列命令會使用雜湊表，可改善效能：</span><span class="sxs-lookup"><span data-stu-id="175eb-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="175eb-111">關於列舉的部落格文章</span><span class="sxs-lookup"><span data-stu-id="175eb-111">Blog posts about enumeration</span></span>

<span data-ttu-id="175eb-112">本文介紹有關如何在雜湊表中使用列舉值的資訊。</span><span class="sxs-lookup"><span data-stu-id="175eb-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="175eb-113">如需有關列舉的詳細資訊，請參閱這些 **Scripting Guy** 部落格文章。</span><span class="sxs-lookup"><span data-stu-id="175eb-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="175eb-114">若要建立傳回列舉值的函式，請參閱[列舉和值](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values)。</span><span class="sxs-lookup"><span data-stu-id="175eb-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="175eb-115">如需詳細資訊，請參閱[有關列舉的 Scripting Guy 部落格系列文章](https://devblogs.microsoft.com/scripting/?s=about+enumeration)。</span><span class="sxs-lookup"><span data-stu-id="175eb-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-key-value-pairs"></a><span data-ttu-id="175eb-116">雜湊表機碼-值組</span><span class="sxs-lookup"><span data-stu-id="175eb-116">Hash table key-value pairs</span></span>

<span data-ttu-id="175eb-117">若要建立有效率的查詢，請將 `Get-WinEvent` Cmdlet 與 **FilterHashtable** 參數一起使用。</span><span class="sxs-lookup"><span data-stu-id="175eb-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="175eb-118">**FilterHashtable** 接受雜湊表作為篩選條件，以從 Windows 事件記錄檔中取得特定資訊。</span><span class="sxs-lookup"><span data-stu-id="175eb-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="175eb-119">雜湊表使用**機碼-值**組。</span><span class="sxs-lookup"><span data-stu-id="175eb-119">A hash table uses **key-value** pairs.</span></span> <span data-ttu-id="175eb-120">如需雜湊表的相關詳細資訊，請參閱 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)。</span><span class="sxs-lookup"><span data-stu-id="175eb-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="175eb-121">如果有多個**機碼-值**組位於同一行，則必須以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="175eb-121">If the **key-value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="175eb-122">如果每個**機碼-值**組位於不同行上，則不需要分號。</span><span class="sxs-lookup"><span data-stu-id="175eb-122">If each **key-value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="175eb-123">例如，此文章將**機碼-值**組放在不同的行上，且不使用分號。</span><span class="sxs-lookup"><span data-stu-id="175eb-123">For example, this article places **key-value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="175eb-124">此範例使用數個 **FilterHashtable** 參數的**機碼-值**組。</span><span class="sxs-lookup"><span data-stu-id="175eb-124">This sample uses several of the **FilterHashtable** parameter's **key-value** pairs.</span></span> <span data-ttu-id="175eb-125">已完成的查詢中包括 **LogName**、**ProviderName**、**Keywords**、**ID** 與 **Level**。</span><span class="sxs-lookup"><span data-stu-id="175eb-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="175eb-126">接受的**機碼-值**組如下表所示，並包含在 [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** 參數的文件中。</span><span class="sxs-lookup"><span data-stu-id="175eb-126">The accepted **key-value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="175eb-127">下表顯示機碼名稱、資料類型，以及資料值是否接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="175eb-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

|    <span data-ttu-id="175eb-128">機碼名稱</span><span class="sxs-lookup"><span data-stu-id="175eb-128">Key name</span></span>    | <span data-ttu-id="175eb-129">值資料類型</span><span class="sxs-lookup"><span data-stu-id="175eb-129">Value data type</span></span> | <span data-ttu-id="175eb-130">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="175eb-130">Accepts wildcard characters?</span></span> |
| -------------- | --------------- | ---------------------------- |
| <span data-ttu-id="175eb-131">LogName</span><span class="sxs-lookup"><span data-stu-id="175eb-131">LogName</span></span>        | `<String[]>`    | <span data-ttu-id="175eb-132">是</span><span class="sxs-lookup"><span data-stu-id="175eb-132">Yes</span></span>                          |
| <span data-ttu-id="175eb-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="175eb-133">ProviderName</span></span>   | `<String[]>`    | <span data-ttu-id="175eb-134">是</span><span class="sxs-lookup"><span data-stu-id="175eb-134">Yes</span></span>                          |
| <span data-ttu-id="175eb-135">Path</span><span class="sxs-lookup"><span data-stu-id="175eb-135">Path</span></span>           | `<String[]>`    | <span data-ttu-id="175eb-136">否</span><span class="sxs-lookup"><span data-stu-id="175eb-136">No</span></span>                           |
| <span data-ttu-id="175eb-137">關鍵字</span><span class="sxs-lookup"><span data-stu-id="175eb-137">Keywords</span></span>       | `<Long[]>`      | <span data-ttu-id="175eb-138">否</span><span class="sxs-lookup"><span data-stu-id="175eb-138">No</span></span>                           |
| <span data-ttu-id="175eb-139">ID</span><span class="sxs-lookup"><span data-stu-id="175eb-139">ID</span></span>             | `<Int32[]>`     | <span data-ttu-id="175eb-140">否</span><span class="sxs-lookup"><span data-stu-id="175eb-140">No</span></span>                           |
| <span data-ttu-id="175eb-141">層級</span><span class="sxs-lookup"><span data-stu-id="175eb-141">Level</span></span>          | `<Int32[]>`     | <span data-ttu-id="175eb-142">否</span><span class="sxs-lookup"><span data-stu-id="175eb-142">No</span></span>                           |
| <span data-ttu-id="175eb-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="175eb-143">StartTime</span></span>      | `<DateTime>`    | <span data-ttu-id="175eb-144">否</span><span class="sxs-lookup"><span data-stu-id="175eb-144">No</span></span>                           |
| <span data-ttu-id="175eb-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="175eb-145">EndTime</span></span>        | `<DateTime>`    | <span data-ttu-id="175eb-146">否</span><span class="sxs-lookup"><span data-stu-id="175eb-146">No</span></span>                           |
| <span data-ttu-id="175eb-147">UserID</span><span class="sxs-lookup"><span data-stu-id="175eb-147">UserID</span></span>         | `<SID>`         | <span data-ttu-id="175eb-148">否</span><span class="sxs-lookup"><span data-stu-id="175eb-148">No</span></span>                           |
| <span data-ttu-id="175eb-149">資料</span><span class="sxs-lookup"><span data-stu-id="175eb-149">Data</span></span>           | `<String[]>`    | <span data-ttu-id="175eb-150">否</span><span class="sxs-lookup"><span data-stu-id="175eb-150">No</span></span>                           |
| `<named-data>` | `<String[]>`    | <span data-ttu-id="175eb-151">否</span><span class="sxs-lookup"><span data-stu-id="175eb-151">No</span></span>                           |

<span data-ttu-id="175eb-152">`<named-data>` 機碼代表具名事件資料欄位。</span><span class="sxs-lookup"><span data-stu-id="175eb-152">The `<named-data>` key represents a named event data field.</span></span> <span data-ttu-id="175eb-153">例如，Perflib 事件 1008 可以包含下列事件資料：</span><span class="sxs-lookup"><span data-stu-id="175eb-153">For example, the Perflib event 1008 can contain the following event data:</span></span>

```xml
<EventData>
  <Data Name="Service">BITS</Data>
  <Data Name="Library">C:\Windows\System32\bitsperf.dll</Data>
  <Data Name="Win32Error">2</Data>
</EventData>
```

<span data-ttu-id="175eb-154">您可以使用下列命令查詢這些事件：</span><span class="sxs-lookup"><span data-stu-id="175eb-154">You can query for these events using the following command:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{LogName='Application'; 'Service'='Bits'}
```

> [!NOTE]
> <span data-ttu-id="175eb-155">PowerShell 6 中已加入查詢 `<named-data>` 的功能。</span><span class="sxs-lookup"><span data-stu-id="175eb-155">The ability to query for `<named-data>` was added in PowerShell 6.</span></span>

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="175eb-156">使用雜湊表建立查詢</span><span class="sxs-lookup"><span data-stu-id="175eb-156">Building a query with a hash table</span></span>

<span data-ttu-id="175eb-157">若要驗證結果並針對問題進行疑難排解，最好一次一個**機碼-值**組來建置雜湊表。</span><span class="sxs-lookup"><span data-stu-id="175eb-157">To verify results and troubleshoot problems, it helps to build the hash table one **key-value** pair at a time.</span></span> <span data-ttu-id="175eb-158">該查詢會從**應用程式**記錄檔中取得資料。</span><span class="sxs-lookup"><span data-stu-id="175eb-158">The query gets data from the **Application** log.</span></span> <span data-ttu-id="175eb-159">雜湊表就相當於 `Get-WinEvent –LogName Application`。</span><span class="sxs-lookup"><span data-stu-id="175eb-159">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="175eb-160">首先，建立 `Get-WinEvent` 查詢。</span><span class="sxs-lookup"><span data-stu-id="175eb-160">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="175eb-161">使用 **FilterHashtable** 參數的**機碼-值**組，其中機碼為 **LogName** 而值為 **Application**。</span><span class="sxs-lookup"><span data-stu-id="175eb-161">Use the **FilterHashtable** parameter's **key-value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="175eb-162">繼續使用 **ProviderName** 機碼建置雜湊表。</span><span class="sxs-lookup"><span data-stu-id="175eb-162">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="175eb-163">**ProviderName** 是 **Windows 事件檢視器**中 [來源]  欄位中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="175eb-163">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="175eb-164">例如，下列螢幕擷取畫面中的 **.NET Runtime**：</span><span class="sxs-lookup"><span data-stu-id="175eb-164">For example, **.NET Runtime** in the following screenshot:</span></span>

![Windows 事件檢視器來源的影像。](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="175eb-166">更新雜湊表，並包含**機碼-值**組，其中機碼為 \*\*ProviderName，而值為 **.NET Runtime**。</span><span class="sxs-lookup"><span data-stu-id="175eb-166">Update the hash table and include the **key-value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="175eb-167">如果您的查詢需要從封存事件記錄檔中取得資料，請使用 **Path** 機碼。</span><span class="sxs-lookup"><span data-stu-id="175eb-167">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="175eb-168">**Path** 值會指定記錄檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="175eb-168">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="175eb-169">如需詳細資訊，請參閱 **Scripting Guy** 部落格文章[使用 PowerShell 剖析儲存的事件記錄檔以尋找錯誤](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors)。</span><span class="sxs-lookup"><span data-stu-id="175eb-169">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="175eb-170">使用雜湊表中的列舉值</span><span class="sxs-lookup"><span data-stu-id="175eb-170">Using enumerated values in a hash table</span></span>

<span data-ttu-id="175eb-171">**Keywords** 是雜湊表中的下一個機碼。</span><span class="sxs-lookup"><span data-stu-id="175eb-171">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="175eb-172">**Keywords** 資料類型是包含大量數字之 `[long]` 實值型別的陣列。</span><span class="sxs-lookup"><span data-stu-id="175eb-172">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="175eb-173">使用下列命令來尋找 `[long]` 的最大值：</span><span class="sxs-lookup"><span data-stu-id="175eb-173">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="175eb-174">針對 **Keywords** 機碼，PowerShell 會使用數字，而不是**安全性**等字串。</span><span class="sxs-lookup"><span data-stu-id="175eb-174">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="175eb-175">**Windows 事件檢視器**將 **Keywords** 顯示為字串，但它們是列舉值。</span><span class="sxs-lookup"><span data-stu-id="175eb-175">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="175eb-176">在雜湊表中，如果您使用帶有字串值的 **Keywords** 機碼，則會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="175eb-176">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="175eb-177">開啟 **Windows 事件檢視器**，然後從 [動作]  窗格中，按一下 [篩選目前的記錄]  。</span><span class="sxs-lookup"><span data-stu-id="175eb-177">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="175eb-178">**Keywords** 下拉式功能表會顯示可用的關鍵字，如下列螢幕擷取畫面所示：</span><span class="sxs-lookup"><span data-stu-id="175eb-178">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Windows 事件檢視器關鍵字的影像。](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="175eb-180">使用下列命令來顯示 `StandardEventKeywords` 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="175eb-180">Use the following command to display the `StandardEventKeywords` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

<span data-ttu-id="175eb-181">列舉值記錄在 **.NET Framework** 中。</span><span class="sxs-lookup"><span data-stu-id="175eb-181">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="175eb-182">如需詳細資訊，請參閱 [StandardEventKeywords 列舉](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2)。</span><span class="sxs-lookup"><span data-stu-id="175eb-182">For more information, see [StandardEventKeywords Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="175eb-183">**Keywords** 名稱和列舉值如下所示：</span><span class="sxs-lookup"><span data-stu-id="175eb-183">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="175eb-184">名稱</span><span class="sxs-lookup"><span data-stu-id="175eb-184">Name</span></span>             |  <span data-ttu-id="175eb-185">值</span><span class="sxs-lookup"><span data-stu-id="175eb-185">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="175eb-186">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="175eb-186">AuditFailure</span></span>     | <span data-ttu-id="175eb-187">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="175eb-187">4503599627370496</span></span>  |
| <span data-ttu-id="175eb-188">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="175eb-188">AuditSuccess</span></span>     | <span data-ttu-id="175eb-189">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="175eb-189">9007199254740992</span></span>  |
| <span data-ttu-id="175eb-190">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="175eb-190">CorrelationHint2</span></span> | <span data-ttu-id="175eb-191">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="175eb-191">18014398509481984</span></span> |
| <span data-ttu-id="175eb-192">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="175eb-192">EventLogClassic</span></span>  | <span data-ttu-id="175eb-193">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="175eb-193">36028797018963968</span></span> |
| <span data-ttu-id="175eb-194">Sqm</span><span class="sxs-lookup"><span data-stu-id="175eb-194">Sqm</span></span>              | <span data-ttu-id="175eb-195">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="175eb-195">2251799813685248</span></span>  |
| <span data-ttu-id="175eb-196">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="175eb-196">WdiDiagnostic</span></span>    | <span data-ttu-id="175eb-197">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="175eb-197">1125899906842624</span></span>  |
| <span data-ttu-id="175eb-198">WdiContext</span><span class="sxs-lookup"><span data-stu-id="175eb-198">WdiContext</span></span>       | <span data-ttu-id="175eb-199">562949953421312</span><span class="sxs-lookup"><span data-stu-id="175eb-199">562949953421312</span></span>   |
| <span data-ttu-id="175eb-200">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="175eb-200">ResponseTime</span></span>     | <span data-ttu-id="175eb-201">281474976710656</span><span class="sxs-lookup"><span data-stu-id="175eb-201">281474976710656</span></span>   |
| <span data-ttu-id="175eb-202">None</span><span class="sxs-lookup"><span data-stu-id="175eb-202">None</span></span>             | <span data-ttu-id="175eb-203">0</span><span class="sxs-lookup"><span data-stu-id="175eb-203">0</span></span>                 |

<span data-ttu-id="175eb-204">更新雜湊表並包含**機碼-值**組，其中機碼為 **Keywords**，而 **EventLogClassic** 列舉值為 **36028797018963968**。</span><span class="sxs-lookup"><span data-stu-id="175eb-204">Update the hash table and include the **key-value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="175eb-205">關鍵字靜態屬性值 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="175eb-205">Keywords static property value (optional)</span></span>

<span data-ttu-id="175eb-206">列舉 **Keywords** 機碼，但您可以在雜湊表查詢中使用靜態屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="175eb-206">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="175eb-207">必須將屬性名稱轉換為具有 **Value__** 屬性的值，而不是使用傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="175eb-207">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="175eb-208">例如，下列指令碼會使用 **Value__** 屬性。</span><span class="sxs-lookup"><span data-stu-id="175eb-208">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="175eb-209">依事件識別碼篩選</span><span class="sxs-lookup"><span data-stu-id="175eb-209">Filtering by Event Id</span></span>

<span data-ttu-id="175eb-210">若要取得更特定的資料，查詢的結果將依**事件識別碼**進行篩選。雜湊表中將**事件識別碼**作為機碼 **ID** 參考，且值為特定**事件識別碼**。**Windows 事件檢視器**會顯示**事件識別碼**。這個範例會使用**事件識別碼 1023**。</span><span class="sxs-lookup"><span data-stu-id="175eb-210">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="175eb-211">更新雜湊表，並包含**機碼-值**組，其中機碼為 **ID**，而值為 **1023**。</span><span class="sxs-lookup"><span data-stu-id="175eb-211">Update the hash table and include the **key-value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="175eb-212">依層級篩選</span><span class="sxs-lookup"><span data-stu-id="175eb-212">Filtering by Level</span></span>

<span data-ttu-id="175eb-213">若要進一步精簡結果並僅包含錯誤的事件，請使用 **Level** 機碼。</span><span class="sxs-lookup"><span data-stu-id="175eb-213">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="175eb-214">**Windows 事件檢視器**將 **Level** 顯示為字串值，但它們是列舉值。</span><span class="sxs-lookup"><span data-stu-id="175eb-214">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="175eb-215">在雜湊表中，如果您使用帶有字串值的 **Level** 機碼，則會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="175eb-215">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="175eb-216">**Level** 的值包括 **Error**、**Warning** 或 **Informational**。</span><span class="sxs-lookup"><span data-stu-id="175eb-216">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="175eb-217">使用下列命令來顯示 `StandardEventLevel` 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="175eb-217">Use the following command to display the `StandardEventLevel` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

<span data-ttu-id="175eb-218">列舉值記錄在 **.NET Framework** 中。</span><span class="sxs-lookup"><span data-stu-id="175eb-218">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="175eb-219">如需詳細資訊，請參閱 [StandardEventLevel 列舉](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2)。</span><span class="sxs-lookup"><span data-stu-id="175eb-219">For more information, see [StandardEventLevel Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="175eb-220">**Level** 機碼的名稱和列舉值如下所示：</span><span class="sxs-lookup"><span data-stu-id="175eb-220">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="175eb-221">名稱</span><span class="sxs-lookup"><span data-stu-id="175eb-221">Name</span></span>           | <span data-ttu-id="175eb-222">值</span><span class="sxs-lookup"><span data-stu-id="175eb-222">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="175eb-223">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="175eb-223">Verbose</span></span>        |   <span data-ttu-id="175eb-224">5</span><span class="sxs-lookup"><span data-stu-id="175eb-224">5</span></span>   |
| <span data-ttu-id="175eb-225">資訊</span><span class="sxs-lookup"><span data-stu-id="175eb-225">Informational</span></span>  |   <span data-ttu-id="175eb-226">4</span><span class="sxs-lookup"><span data-stu-id="175eb-226">4</span></span>   |
| <span data-ttu-id="175eb-227">警告</span><span class="sxs-lookup"><span data-stu-id="175eb-227">Warning</span></span>        |   <span data-ttu-id="175eb-228">3</span><span class="sxs-lookup"><span data-stu-id="175eb-228">3</span></span>   |
| <span data-ttu-id="175eb-229">錯誤</span><span class="sxs-lookup"><span data-stu-id="175eb-229">Error</span></span>          |   <span data-ttu-id="175eb-230">2</span><span class="sxs-lookup"><span data-stu-id="175eb-230">2</span></span>   |
| <span data-ttu-id="175eb-231">重大</span><span class="sxs-lookup"><span data-stu-id="175eb-231">Critical</span></span>       |   <span data-ttu-id="175eb-232">1</span><span class="sxs-lookup"><span data-stu-id="175eb-232">1</span></span>   |
| <span data-ttu-id="175eb-233">LogAlways</span><span class="sxs-lookup"><span data-stu-id="175eb-233">LogAlways</span></span>      |   <span data-ttu-id="175eb-234">0</span><span class="sxs-lookup"><span data-stu-id="175eb-234">0</span></span>   |

<span data-ttu-id="175eb-235">已完成查詢的雜湊表包含機碼 **Level** 和值 **2**。</span><span class="sxs-lookup"><span data-stu-id="175eb-235">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="175eb-236">列舉中的層級靜態屬性 (選用)</span><span class="sxs-lookup"><span data-stu-id="175eb-236">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="175eb-237">列舉 **Level** 機碼，但您可以在雜湊表查詢中使用靜態屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="175eb-237">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="175eb-238">必須將屬性名稱轉換為具有 **Value__** 屬性的值，而不是使用傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="175eb-238">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="175eb-239">例如，下列指令碼會使用 **Value__** 屬性。</span><span class="sxs-lookup"><span data-stu-id="175eb-239">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```