---
ms.date: 3/18/2019
title: 使用 FilterHashtable 建立 Get-WinEvent 查詢
ms.openlocfilehash: 28ba3c99a297944003a28eaba7de34b77d9df536
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058799"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="89ec9-102">使用 FilterHashtable 建立 Get-WinEvent 查詢</span><span class="sxs-lookup"><span data-stu-id="89ec9-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="89ec9-103">若要閱讀原始的 2014 年 6 月 3 日 **Scripting Guy** 部落格文章，請參閱[使用 FilterHashTable 搭配 PowerShell 篩選事件記錄檔](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="89ec9-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="89ec9-104">本文是原始部落格文章的摘錄，並說明如何使用 `Get-WinEvent` Cmdlet 的 **FilterHashtable** 參數來篩選事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="89ec9-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="89ec9-105">PowerShell 的 `Get-WinEvent` Cmdlet 是一種功能強大的方法，可篩選 Windows 事件和診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="89ec9-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="89ec9-106">`Get-WinEvent` 查詢使用 **FilterHashtable** 參數時，效能會提高。</span><span class="sxs-lookup"><span data-stu-id="89ec9-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="89ec9-107">當您使用大型事件記錄檔時，將管線中的物件傳送到 `Where-Object` 命令不是有效率的方式。</span><span class="sxs-lookup"><span data-stu-id="89ec9-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="89ec9-108">在 PowerShell 6 之前，`Get-EventLog` Cmdlet 是取得記錄資料的另一個選項。</span><span class="sxs-lookup"><span data-stu-id="89ec9-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="89ec9-109">例如，下列命令篩選 **Microsoft-Windows-Defrag** 記錄檔的效率不佳：</span><span class="sxs-lookup"><span data-stu-id="89ec9-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

<span data-ttu-id="89ec9-110">下列命令會使用雜湊表，可改善效能：</span><span class="sxs-lookup"><span data-stu-id="89ec9-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="89ec9-111">關於列舉的部落格文章</span><span class="sxs-lookup"><span data-stu-id="89ec9-111">Blog posts about enumeration</span></span>

<span data-ttu-id="89ec9-112">本文介紹有關如何在雜湊表中使用列舉值的資訊。</span><span class="sxs-lookup"><span data-stu-id="89ec9-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="89ec9-113">如需有關列舉的詳細資訊，請參閱這些 **Scripting Guy** 部落格文章。</span><span class="sxs-lookup"><span data-stu-id="89ec9-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="89ec9-114">若要建立傳回列舉值的函式，請參閱[列舉和值](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values)。</span><span class="sxs-lookup"><span data-stu-id="89ec9-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="89ec9-115">如需詳細資訊，請參閱[有關列舉的 Scripting Guy 部落格系列文章](https://devblogs.microsoft.com/scripting/?s=about+enumeration)。</span><span class="sxs-lookup"><span data-stu-id="89ec9-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-keyvalue-pairs"></a><span data-ttu-id="89ec9-116">雜湊資料表索引鍵/值組</span><span class="sxs-lookup"><span data-stu-id="89ec9-116">Hash table key/value pairs</span></span>

<span data-ttu-id="89ec9-117">若要建立有效率的查詢，請將 `Get-WinEvent` Cmdlet 與 **FilterHashtable** 參數一起使用。</span><span class="sxs-lookup"><span data-stu-id="89ec9-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="89ec9-118">**FilterHashtable** 接受雜湊表作為篩選條件，以從 Windows 事件記錄檔中取得特定資訊。</span><span class="sxs-lookup"><span data-stu-id="89ec9-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="89ec9-119">雜湊資料表使用**索引鍵/值**組。</span><span class="sxs-lookup"><span data-stu-id="89ec9-119">A hash table uses **key/value** pairs.</span></span> <span data-ttu-id="89ec9-120">如需雜湊表的相關詳細資訊，請參閱 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)。</span><span class="sxs-lookup"><span data-stu-id="89ec9-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="89ec9-121">如果**索引鍵/值**組位於同一行上，則必須以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="89ec9-121">If the **key/value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="89ec9-122">如果每個**索引鍵/值**組位於不同行上，則不需要分號。</span><span class="sxs-lookup"><span data-stu-id="89ec9-122">If each **key/value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="89ec9-123">例如，本文將**索引鍵/值**組放在不同的行上，且不使用分號。</span><span class="sxs-lookup"><span data-stu-id="89ec9-123">For example, this article places **key/value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="89ec9-124">此範例會使用數個 **FilterHashtable** 參數的**索引鍵/值**組。</span><span class="sxs-lookup"><span data-stu-id="89ec9-124">This sample uses several of the **FilterHashtable** parameter's **key/value** pairs.</span></span> <span data-ttu-id="89ec9-125">已完成的查詢中包括 **LogName**、**ProviderName**、**Keywords**、**ID** 與 **Level**。</span><span class="sxs-lookup"><span data-stu-id="89ec9-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="89ec9-126">接受的**索引鍵/值**組如下表所示，並包含在 [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** 參數的文件中。</span><span class="sxs-lookup"><span data-stu-id="89ec9-126">The accepted **key/value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="89ec9-127">下表顯示索引鍵名稱、資料類型，以及資料值是否接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="89ec9-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

| <span data-ttu-id="89ec9-128">機碼名稱</span><span class="sxs-lookup"><span data-stu-id="89ec9-128">Key name</span></span>     | <span data-ttu-id="89ec9-129">數值資料類型</span><span class="sxs-lookup"><span data-stu-id="89ec9-129">Value data type</span></span>    | <span data-ttu-id="89ec9-130">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="89ec9-130">Accepts wildcard characters?</span></span> |
|------------- | ------------------ | ---------------------------- |
| <span data-ttu-id="89ec9-131">LogName</span><span class="sxs-lookup"><span data-stu-id="89ec9-131">LogName</span></span>      | `<String[]>`       | <span data-ttu-id="89ec9-132">是</span><span class="sxs-lookup"><span data-stu-id="89ec9-132">Yes</span></span> |
| <span data-ttu-id="89ec9-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="89ec9-133">ProviderName</span></span> | `<String[]>`       | <span data-ttu-id="89ec9-134">是</span><span class="sxs-lookup"><span data-stu-id="89ec9-134">Yes</span></span> |
| <span data-ttu-id="89ec9-135">路徑</span><span class="sxs-lookup"><span data-stu-id="89ec9-135">Path</span></span>         | `<String[]>`       | <span data-ttu-id="89ec9-136">否</span><span class="sxs-lookup"><span data-stu-id="89ec9-136">No</span></span>  |
| <span data-ttu-id="89ec9-137">關鍵字</span><span class="sxs-lookup"><span data-stu-id="89ec9-137">Keywords</span></span>     | `<Long[]>`         | <span data-ttu-id="89ec9-138">否</span><span class="sxs-lookup"><span data-stu-id="89ec9-138">No</span></span>  |
| <span data-ttu-id="89ec9-139">ID</span><span class="sxs-lookup"><span data-stu-id="89ec9-139">ID</span></span>           | `<Int32[]>`        | <span data-ttu-id="89ec9-140">否</span><span class="sxs-lookup"><span data-stu-id="89ec9-140">No</span></span>  |
| <span data-ttu-id="89ec9-141">層級</span><span class="sxs-lookup"><span data-stu-id="89ec9-141">Level</span></span>        | `<Int32[]>`        | <span data-ttu-id="89ec9-142">否</span><span class="sxs-lookup"><span data-stu-id="89ec9-142">No</span></span>  |
| <span data-ttu-id="89ec9-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="89ec9-143">StartTime</span></span>    | `<DateTime>`       | <span data-ttu-id="89ec9-144">否</span><span class="sxs-lookup"><span data-stu-id="89ec9-144">No</span></span>  |
| <span data-ttu-id="89ec9-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="89ec9-145">EndTime</span></span>      | `<DateTime>`       | <span data-ttu-id="89ec9-146">否</span><span class="sxs-lookup"><span data-stu-id="89ec9-146">No</span></span>  |
| <span data-ttu-id="89ec9-147">UserID</span><span class="sxs-lookup"><span data-stu-id="89ec9-147">UserID</span></span>       | `<SID>`            | <span data-ttu-id="89ec9-148">否</span><span class="sxs-lookup"><span data-stu-id="89ec9-148">No</span></span>  |
| <span data-ttu-id="89ec9-149">資料</span><span class="sxs-lookup"><span data-stu-id="89ec9-149">Data</span></span>         | `<String[]>`       | <span data-ttu-id="89ec9-150">否</span><span class="sxs-lookup"><span data-stu-id="89ec9-150">No</span></span>  |
| *            | `<String[]>`       | <span data-ttu-id="89ec9-151">否</span><span class="sxs-lookup"><span data-stu-id="89ec9-151">No</span></span>  |

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="89ec9-152">使用雜湊表建立查詢</span><span class="sxs-lookup"><span data-stu-id="89ec9-152">Building a query with a hash table</span></span>

<span data-ttu-id="89ec9-153">若要驗證結果並針對問題進行疑難排解，最好一次一個**索引鍵/值**組來建置雜湊表。</span><span class="sxs-lookup"><span data-stu-id="89ec9-153">To verify results and troubleshoot problems, it helps to build the hash table one **key/value** pair at a time.</span></span> <span data-ttu-id="89ec9-154">該查詢會從**應用程式**記錄檔中取得資料。</span><span class="sxs-lookup"><span data-stu-id="89ec9-154">The query gets data from the **Application** log.</span></span> <span data-ttu-id="89ec9-155">雜湊表就相當於 `Get-WinEvent –LogName Application`。</span><span class="sxs-lookup"><span data-stu-id="89ec9-155">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="89ec9-156">首先，建立 `Get-WinEvent` 查詢。</span><span class="sxs-lookup"><span data-stu-id="89ec9-156">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="89ec9-157">使用 **FilterHashtable** 參數的**索引鍵/值**組，其中索引鍵為 **LogName** 而值為 **Application**。</span><span class="sxs-lookup"><span data-stu-id="89ec9-157">Use the **FilterHashtable** parameter's **key/value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="89ec9-158">繼續使用 **ProviderName** 索引鍵建置雜湊表。</span><span class="sxs-lookup"><span data-stu-id="89ec9-158">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="89ec9-159">**ProviderName** 是 **Windows 事件檢視器**中 [來源] 欄位中顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="89ec9-159">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="89ec9-160">例如，下列螢幕擷取畫面中的 **.NET Runtime**：</span><span class="sxs-lookup"><span data-stu-id="89ec9-160">For example, **.NET Runtime** in the following screenshot:</span></span>

![Windows 事件檢視器來源的影像。](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="89ec9-162">更新雜湊表，並包含**索引鍵/值**組，其中索引鍵為 \*\*ProviderName，而值為 **.NET Runtime**。</span><span class="sxs-lookup"><span data-stu-id="89ec9-162">Update the hash table and include the **key/value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="89ec9-163">如果您的查詢需要從封存事件記錄檔中取得資料，請使用 **Path** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="89ec9-163">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="89ec9-164">**Path** 值會指定記錄檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="89ec9-164">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="89ec9-165">如需詳細資訊，請參閱 **Scripting Guy** 部落格文章[使用 PowerShell 剖析儲存的事件記錄檔以尋找錯誤](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors)。</span><span class="sxs-lookup"><span data-stu-id="89ec9-165">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="89ec9-166">使用雜湊表中的列舉值</span><span class="sxs-lookup"><span data-stu-id="89ec9-166">Using enumerated values in a hash table</span></span>

<span data-ttu-id="89ec9-167">**Keywords** 是雜湊表中的下一個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="89ec9-167">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="89ec9-168">**Keywords** 資料類型是包含大量數字之 `[long]` 實值型別的陣列。</span><span class="sxs-lookup"><span data-stu-id="89ec9-168">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="89ec9-169">使用下列命令來尋找 `[long]` 的最大值：</span><span class="sxs-lookup"><span data-stu-id="89ec9-169">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="89ec9-170">針對 **Keywords** 索引鍵，PowerShell 會使用數字，而不是**安全性**等字串。</span><span class="sxs-lookup"><span data-stu-id="89ec9-170">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="89ec9-171">**Windows 事件檢視器**將 **Keywords** 顯示為字串，但它們是列舉值。</span><span class="sxs-lookup"><span data-stu-id="89ec9-171">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="89ec9-172">在雜湊表中，如果您使用帶有字串值的 **Keywords** 索引鍵，則會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="89ec9-172">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="89ec9-173">開啟 **Windows 事件檢視器**，然後從 [動作] 窗格中，按一下 [篩選目前的記錄]。</span><span class="sxs-lookup"><span data-stu-id="89ec9-173">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="89ec9-174">**Keywords** 下拉式功能表會顯示可用的關鍵字，如下列螢幕擷取畫面所示：</span><span class="sxs-lookup"><span data-stu-id="89ec9-174">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Windows 事件檢視器關鍵字的影像。](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="89ec9-176">使用下列命令來顯示 `StandardEventKeywords` 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="89ec9-176">Use the following command to display the `StandardEventKeywords` property names.</span></span>

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

<span data-ttu-id="89ec9-177">列舉值記錄在 **.NET Framework** 中。</span><span class="sxs-lookup"><span data-stu-id="89ec9-177">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="89ec9-178">如需詳細資訊，請參閱 [StandardEventKeywords 列舉](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2)。</span><span class="sxs-lookup"><span data-stu-id="89ec9-178">For more information, see [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="89ec9-179">**Keywords** 名稱和列舉值如下所示：</span><span class="sxs-lookup"><span data-stu-id="89ec9-179">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="89ec9-180">名稱</span><span class="sxs-lookup"><span data-stu-id="89ec9-180">Name</span></span>             |  <span data-ttu-id="89ec9-181">值</span><span class="sxs-lookup"><span data-stu-id="89ec9-181">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="89ec9-182">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="89ec9-182">AuditFailure</span></span>     | <span data-ttu-id="89ec9-183">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="89ec9-183">4503599627370496</span></span>  |
| <span data-ttu-id="89ec9-184">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="89ec9-184">AuditSuccess</span></span>     | <span data-ttu-id="89ec9-185">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="89ec9-185">9007199254740992</span></span>  |
| <span data-ttu-id="89ec9-186">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="89ec9-186">CorrelationHint2</span></span> | <span data-ttu-id="89ec9-187">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="89ec9-187">18014398509481984</span></span> |
| <span data-ttu-id="89ec9-188">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="89ec9-188">EventLogClassic</span></span>  | <span data-ttu-id="89ec9-189">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="89ec9-189">36028797018963968</span></span> |
| <span data-ttu-id="89ec9-190">Sqm</span><span class="sxs-lookup"><span data-stu-id="89ec9-190">Sqm</span></span>              | <span data-ttu-id="89ec9-191">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="89ec9-191">2251799813685248</span></span>  |
| <span data-ttu-id="89ec9-192">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="89ec9-192">WdiDiagnostic</span></span>    | <span data-ttu-id="89ec9-193">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="89ec9-193">1125899906842624</span></span>  |
| <span data-ttu-id="89ec9-194">WdiContext</span><span class="sxs-lookup"><span data-stu-id="89ec9-194">WdiContext</span></span>       | <span data-ttu-id="89ec9-195">562949953421312</span><span class="sxs-lookup"><span data-stu-id="89ec9-195">562949953421312</span></span>   |
| <span data-ttu-id="89ec9-196">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="89ec9-196">ResponseTime</span></span>     | <span data-ttu-id="89ec9-197">281474976710656</span><span class="sxs-lookup"><span data-stu-id="89ec9-197">281474976710656</span></span>   |
| <span data-ttu-id="89ec9-198">無</span><span class="sxs-lookup"><span data-stu-id="89ec9-198">None</span></span>             | <span data-ttu-id="89ec9-199">0</span><span class="sxs-lookup"><span data-stu-id="89ec9-199">0</span></span>                 |

<span data-ttu-id="89ec9-200">更新雜湊表並包含**索引鍵/值**組，其中索引鍵為 **Keywords**，而 **EventLogClassic** 列舉值為 **36028797018963968**。</span><span class="sxs-lookup"><span data-stu-id="89ec9-200">Update the hash table and include the **key/value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="89ec9-201">關鍵字靜態屬性值 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="89ec9-201">Keywords static property value (optional)</span></span>

<span data-ttu-id="89ec9-202">列舉 **Keywords** 索引鍵，但您可以在雜湊表查詢中使用靜態屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="89ec9-202">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="89ec9-203">必須將屬性名稱轉換為具有 **Value__** 屬性的值，而不是使用傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="89ec9-203">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="89ec9-204">例如，下列指令碼會使用 **Value__** 屬性。</span><span class="sxs-lookup"><span data-stu-id="89ec9-204">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="89ec9-205">依事件識別碼篩選</span><span class="sxs-lookup"><span data-stu-id="89ec9-205">Filtering by Event Id</span></span>

<span data-ttu-id="89ec9-206">若要取得更特定的資料，查詢的結果將依**事件識別碼**進行篩選。雜湊表中將**事件識別碼**作為索引鍵 **ID** 參考，且值為特定**事件識別碼**。**Windows 事件檢視器**會顯示**事件識別碼**。這個範例會使用**事件識別碼 1023**。</span><span class="sxs-lookup"><span data-stu-id="89ec9-206">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="89ec9-207">更新雜湊表，並包含**索引鍵/值**組，其中索引鍵為 **ID**，而值為 **1023**。</span><span class="sxs-lookup"><span data-stu-id="89ec9-207">Update the hash table and include the **key/value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="89ec9-208">依層級篩選</span><span class="sxs-lookup"><span data-stu-id="89ec9-208">Filtering by Level</span></span>

<span data-ttu-id="89ec9-209">若要進一步精簡結果並僅包含錯誤的事件，請使用 **Level** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="89ec9-209">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="89ec9-210">**Windows 事件檢視器**將 **Level** 顯示為字串值，但它們是列舉值。</span><span class="sxs-lookup"><span data-stu-id="89ec9-210">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="89ec9-211">在雜湊表中，如果您使用帶有字串值的 **Level** 索引鍵，則會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="89ec9-211">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="89ec9-212">**Level** 的值包括 **Error**、**Warning** 或 **Informational**。</span><span class="sxs-lookup"><span data-stu-id="89ec9-212">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="89ec9-213">使用下列命令來顯示 `StandardEventLevel` 屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="89ec9-213">Use the following command to display the `StandardEventLevel` property names.</span></span>

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

<span data-ttu-id="89ec9-214">列舉值記錄在 **.NET Framework** 中。</span><span class="sxs-lookup"><span data-stu-id="89ec9-214">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="89ec9-215">如需詳細資訊，請參閱 [StandardEventLevel 列舉](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2)。</span><span class="sxs-lookup"><span data-stu-id="89ec9-215">For more information, see [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="89ec9-216">**Level** 索引鍵的名稱和列舉值如下所示：</span><span class="sxs-lookup"><span data-stu-id="89ec9-216">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="89ec9-217">名稱</span><span class="sxs-lookup"><span data-stu-id="89ec9-217">Name</span></span>           | <span data-ttu-id="89ec9-218">值</span><span class="sxs-lookup"><span data-stu-id="89ec9-218">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="89ec9-219">Verbose</span><span class="sxs-lookup"><span data-stu-id="89ec9-219">Verbose</span></span>        |   <span data-ttu-id="89ec9-220">5</span><span class="sxs-lookup"><span data-stu-id="89ec9-220">5</span></span>   |
| <span data-ttu-id="89ec9-221">資訊</span><span class="sxs-lookup"><span data-stu-id="89ec9-221">Informational</span></span>  |   <span data-ttu-id="89ec9-222">4</span><span class="sxs-lookup"><span data-stu-id="89ec9-222">4</span></span>   |
| <span data-ttu-id="89ec9-223">Warning</span><span class="sxs-lookup"><span data-stu-id="89ec9-223">Warning</span></span>        |   <span data-ttu-id="89ec9-224">3</span><span class="sxs-lookup"><span data-stu-id="89ec9-224">3</span></span>   |
| <span data-ttu-id="89ec9-225">錯誤</span><span class="sxs-lookup"><span data-stu-id="89ec9-225">Error</span></span>          |   <span data-ttu-id="89ec9-226">2</span><span class="sxs-lookup"><span data-stu-id="89ec9-226">2</span></span>   |
| <span data-ttu-id="89ec9-227">重大</span><span class="sxs-lookup"><span data-stu-id="89ec9-227">Critical</span></span>       |   <span data-ttu-id="89ec9-228">1</span><span class="sxs-lookup"><span data-stu-id="89ec9-228">1</span></span>   |
| <span data-ttu-id="89ec9-229">LogAlways</span><span class="sxs-lookup"><span data-stu-id="89ec9-229">LogAlways</span></span>      |   <span data-ttu-id="89ec9-230">0</span><span class="sxs-lookup"><span data-stu-id="89ec9-230">0</span></span>   |

<span data-ttu-id="89ec9-231">已完成查詢的雜湊表包含索引鍵 **Level** 和值 **2**。</span><span class="sxs-lookup"><span data-stu-id="89ec9-231">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="89ec9-232">列舉中的層級靜態屬性 (選用)</span><span class="sxs-lookup"><span data-stu-id="89ec9-232">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="89ec9-233">列舉 **Level** 索引鍵，但您可以在雜湊表查詢中使用靜態屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="89ec9-233">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="89ec9-234">必須將屬性名稱轉換為具有 **Value__** 屬性的值，而不是使用傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="89ec9-234">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="89ec9-235">例如，下列指令碼會使用 **Value__** 屬性。</span><span class="sxs-lookup"><span data-stu-id="89ec9-235">For example, the following script uses the **Value__** property.</span></span>

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