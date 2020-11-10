---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: 062d29d033e0a84837a1593fb96df0c3a00dc392
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389414"
---
# <span data-ttu-id="3cd55-103">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="3cd55-103">ConvertFrom-Json</span></span>

## <span data-ttu-id="3cd55-104">概要</span><span class="sxs-lookup"><span data-stu-id="3cd55-104">SYNOPSIS</span></span>
<span data-ttu-id="3cd55-105">將 JSON 格式的字串轉換成自訂物件或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="3cd55-105">Converts a JSON-formatted string to a custom object or a hash table.</span></span>

## <span data-ttu-id="3cd55-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3cd55-106">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="3cd55-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3cd55-107">DESCRIPTION</span></span>

<span data-ttu-id="3cd55-108">`ConvertFrom-Json`Cmdlet 會將 JavaScript 物件標記法 (json) 格式化的字串轉換成自訂 **PSCustomObject** 物件，該物件具有 json 字串中每個欄位的屬性。</span><span class="sxs-lookup"><span data-stu-id="3cd55-108">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="3cd55-109">JSON 一般由網站用於提供物件的文字表示方式。</span><span class="sxs-lookup"><span data-stu-id="3cd55-109">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="3cd55-110">JSON 標準不會禁止 **PSCustomObject** 禁止使用。</span><span class="sxs-lookup"><span data-stu-id="3cd55-110">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject**.</span></span> <span data-ttu-id="3cd55-111">例如，如果 JSON 字串包含重複的索引鍵，則這個 Cmdlet 只會使用最後一個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="3cd55-111">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="3cd55-112">請參閱下列其他範例。</span><span class="sxs-lookup"><span data-stu-id="3cd55-112">See other examples below.</span></span>

<span data-ttu-id="3cd55-113">若要從任何物件產生 JSON 字串，請使用 `ConvertTo-Json` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3cd55-113">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="3cd55-114">此 Cmdlet 是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="3cd55-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="3cd55-115">從 PowerShell 6 開始，此 Cmdlet 支援具有批註的 JSON。</span><span class="sxs-lookup"><span data-stu-id="3cd55-115">Beginning with PowerShell 6, this cmdlet supports JSON with comments.</span></span> <span data-ttu-id="3cd55-116">接受的批註會以兩個正斜線開始 (`//`) 。</span><span class="sxs-lookup"><span data-stu-id="3cd55-116">Accepted comments are started with two forward slashes (`//`).</span></span> <span data-ttu-id="3cd55-117">批註不會在資料中表示，而且可以在檔案中寫入，而不會損毀資料或擲回錯誤，如同在 PowerShell 5.1 中所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="3cd55-117">The comment will not be represented in the data and can be written in the file without corrupting the data or throwing an error as it did in PowerShell 5.1.</span></span>

## <span data-ttu-id="3cd55-118">範例</span><span class="sxs-lookup"><span data-stu-id="3cd55-118">EXAMPLES</span></span>

### <span data-ttu-id="3cd55-119">範例1：將 DateTime 物件轉換成 JSON 物件</span><span class="sxs-lookup"><span data-stu-id="3cd55-119">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="3cd55-120">此命令會使用 `ConvertTo-Json` 和 `ConvertFrom-Json` Cmdlet，將 **DateTime** 物件從 Cmdlet 轉換成 `Get-Date` JSON 物件，再轉換為 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="3cd55-120">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject**.</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : Friday, January 13, 2012 8:06:31 PM
Date        : 1/13/2012 8:00:00 AM
Day         : 13
DayOfWeek   : 5
DayOfYear   : 13
Hour        : 20
Kind        : 2
Millisecond : 400
Minute      : 6
Month       : 1
Second      : 31
Ticks       : 634620819914009002
TimeOfDay   : @{Ticks=723914009002; Days=0; Hours=20; Milliseconds=400; Minutes=6; Seconds=31; TotalDays=0.83786343634490734; TotalHours=20.108722472277776; TotalMilliseconds=72391400.900200009; TotalMinutes=1206.5233483366667;TotalSeconds=72391.4009002}
Year        : 2012
```

<span data-ttu-id="3cd55-121">此範例會使用 `Select-Object` Cmdlet 來取得 **DateTime** 物件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="3cd55-121">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="3cd55-122">它會使用 `ConvertTo-Json` Cmdlet 將 **DateTime** 物件轉換成格式化為 json 物件的字串，並使用 `ConvertFrom-Json` Cmdlet 將 JSON 格式的字串轉換成 **PSCustomObject** 物件。</span><span class="sxs-lookup"><span data-stu-id="3cd55-122">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="3cd55-123">範例2：從 web 服務取得 JSON 字串，並將其轉換為 PowerShell 物件</span><span class="sxs-lookup"><span data-stu-id="3cd55-123">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="3cd55-124">此命令會使用 `Invoke-WebRequest` Cmdlet 從 web 服務取得 json 字串，然後使用 `ConvertFrom-Json` CMDLET 將 json 內容轉換成可在 PowerShell 中管理的物件。</span><span class="sxs-lookup"><span data-stu-id="3cd55-124">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="3cd55-125">您也可以使用 `Invoke-RestMethod` Cmdlet，它會自動將 JSON 內容轉換成物件。</span><span class="sxs-lookup"><span data-stu-id="3cd55-125">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="3cd55-126">範例3：將 JSON 字串轉換為自訂物件</span><span class="sxs-lookup"><span data-stu-id="3cd55-126">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="3cd55-127">此範例說明如何使用 Cmdlet 將 `ConvertFrom-Json` JSON 檔案轉換成 PowerShell 自訂物件。</span><span class="sxs-lookup"><span data-stu-id="3cd55-127">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="3cd55-128">命令會使用 Get-Content Cmdlet 來取得 JSON 檔案中的字串。</span><span class="sxs-lookup"><span data-stu-id="3cd55-128">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="3cd55-129">然後，它會使用管線運算子將分隔的字串傳送至 `ConvertFrom-Json` Cmdlet，以將它轉換成自訂物件。</span><span class="sxs-lookup"><span data-stu-id="3cd55-129">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

### <span data-ttu-id="3cd55-130">範例4：將 JSON 字串轉換成雜湊表</span><span class="sxs-lookup"><span data-stu-id="3cd55-130">Example 4: Convert a JSON string to a hash table</span></span>

<span data-ttu-id="3cd55-131">此命令會顯示一個範例，其中的 `-AsHashtable` switch 可以克服命令的限制。</span><span class="sxs-lookup"><span data-stu-id="3cd55-131">This command shows an example where the `-AsHashtable` switch can overcome limitations of the command.</span></span>

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

<span data-ttu-id="3cd55-132">JSON 字串包含兩個索引鍵值組，其中的索引鍵只有大小寫不同。</span><span class="sxs-lookup"><span data-stu-id="3cd55-132">The JSON string contains two key value pairs with keys that differ only in casing.</span></span> <span data-ttu-id="3cd55-133">如果沒有參數，命令就會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="3cd55-133">Without the switch, the command would have thrown an error.</span></span>

### <span data-ttu-id="3cd55-134">範例5：對單一元素陣列進行來回行程</span><span class="sxs-lookup"><span data-stu-id="3cd55-134">Example 5: Round-trip a single element array</span></span>

<span data-ttu-id="3cd55-135">此命令會顯示一個範例，其中 `-NoEnumerate` 會使用參數來反復存取單一元素的 JSON 陣列。</span><span class="sxs-lookup"><span data-stu-id="3cd55-135">This command shows an example where the `-NoEnumerate` switch is used to round-trip a single element JSON array.</span></span>

```powershell
Write-Output "With -NoEnumerate: $('[1]' | ConvertFrom-Json -NoEnumerate | ConvertTo-Json -Compress)"
Write-Output "Without -NoEnumerate: $('[1]' | ConvertFrom-Json | ConvertTo-Json -Compress)"
```

```Output
With -NoEnumerate: [1]
Without -NoEnumerate: 1
```

<span data-ttu-id="3cd55-136">JSON 字串包含具有單一元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="3cd55-136">The JSON string contains an array with a single element.</span></span> <span data-ttu-id="3cd55-137">如果沒有參數，請將 JSON 轉換成 PSObject，然後使用命令將它轉換回一個 `ConvertTo-Json` 整數。</span><span class="sxs-lookup"><span data-stu-id="3cd55-137">Without the switch, converting the JSON to a PSObject and then converting it back with the `ConvertTo-Json` command results in a single integer.</span></span>

## <span data-ttu-id="3cd55-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3cd55-138">PARAMETERS</span></span>

### <span data-ttu-id="3cd55-139">-AsHashtable</span><span class="sxs-lookup"><span data-stu-id="3cd55-139">-AsHashtable</span></span>

<span data-ttu-id="3cd55-140">將 JSON 轉換成雜湊表物件。</span><span class="sxs-lookup"><span data-stu-id="3cd55-140">Converts the JSON to a hash table object.</span></span> <span data-ttu-id="3cd55-141">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="3cd55-141">This switch was introduced in PowerShell 6.0.</span></span> <span data-ttu-id="3cd55-142">在幾個案例中，它可以克服 Cmdlet 的一些限制 `ConvertFrom-Json` 。</span><span class="sxs-lookup"><span data-stu-id="3cd55-142">There are several scenarios where it can overcome some limitations of the `ConvertFrom-Json` cmdlet.</span></span>

- <span data-ttu-id="3cd55-143">如果 JSON 包含的清單中，索引鍵的大小寫不同。</span><span class="sxs-lookup"><span data-stu-id="3cd55-143">If the JSON contains a list with keys that only differ in casing.</span></span> <span data-ttu-id="3cd55-144">如果沒有參數，則會將這些機碼視為相同的索引鍵，因此只會使用最後一個金鑰。</span><span class="sxs-lookup"><span data-stu-id="3cd55-144">Without the switch, those keys would be seen as identical keys and therefore only the last one would get used.</span></span>
- <span data-ttu-id="3cd55-145">如果 JSON 包含索引鍵，則為空字串。</span><span class="sxs-lookup"><span data-stu-id="3cd55-145">If the JSON contains a key that is an empty string.</span></span> <span data-ttu-id="3cd55-146">如果沒有參數，Cmdlet 會擲回錯誤，因為不 `PSCustomObject` 允許，但雜湊表的確有此錯誤。</span><span class="sxs-lookup"><span data-stu-id="3cd55-146">Without the switch, the cmdlet would throw an error since a `PSCustomObject` does not allow for that but a hash table does.</span></span> <span data-ttu-id="3cd55-147">可能發生這種情況的範例使用案例為檔案 `project.lock.json` 。</span><span class="sxs-lookup"><span data-stu-id="3cd55-147">An example use case where this can occurs are `project.lock.json` files.</span></span>
- <span data-ttu-id="3cd55-148">雜湊表可針對特定資料結構更快速地處理。</span><span class="sxs-lookup"><span data-stu-id="3cd55-148">Hash tables can be processed faster for certain data structures.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cd55-149">-Depth</span><span class="sxs-lookup"><span data-stu-id="3cd55-149">-Depth</span></span>

<span data-ttu-id="3cd55-150">取得或設定 JSON 輸入允許的最大深度。</span><span class="sxs-lookup"><span data-stu-id="3cd55-150">Gets or sets the maximum depth the JSON input is allowed to have.</span></span> <span data-ttu-id="3cd55-151">預設為1024。</span><span class="sxs-lookup"><span data-stu-id="3cd55-151">By default, it is 1024.</span></span>

<span data-ttu-id="3cd55-152">此參數是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="3cd55-152">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cd55-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3cd55-153">-InputObject</span></span>

<span data-ttu-id="3cd55-154">指定 JSON 字串以轉換成 JSON 物件。</span><span class="sxs-lookup"><span data-stu-id="3cd55-154">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="3cd55-155">輸入包含字串的變數，或輸入可取得字串的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="3cd55-155">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="3cd55-156">您也可以使用管線將字串傳送至 `ConvertFrom-Json` 。</span><span class="sxs-lookup"><span data-stu-id="3cd55-156">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="3cd55-157">**InputObject** 是必要參數，但其值可以是空字串。</span><span class="sxs-lookup"><span data-stu-id="3cd55-157">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="3cd55-158">當輸入物件為空字串時，不 `ConvertFrom-Json` 會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="3cd55-158">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="3cd55-159">**InputObject** 值不能是 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="3cd55-159">The **InputObject** value cannot be `$null`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3cd55-160">-NoEnumerate</span><span class="sxs-lookup"><span data-stu-id="3cd55-160">-NoEnumerate</span></span>

<span data-ttu-id="3cd55-161">指定不列舉輸出。</span><span class="sxs-lookup"><span data-stu-id="3cd55-161">Specifies that output is not enumerated.</span></span>

<span data-ttu-id="3cd55-162">設定這個參數會讓陣列以單一物件的形式傳送，而不是個別傳送每個元素。</span><span class="sxs-lookup"><span data-stu-id="3cd55-162">Setting this parameter causes arrays to be sent as a single object instead of sending every element separately.</span></span> <span data-ttu-id="3cd55-163">這可保證 JSON 可以透過進行往返 `ConvertTo-Json` 。</span><span class="sxs-lookup"><span data-stu-id="3cd55-163">This guarantees that JSON can be round-tripped via `ConvertTo-Json`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3cd55-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3cd55-164">CommonParameters</span></span>

<span data-ttu-id="3cd55-165">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3cd55-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3cd55-166">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3cd55-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3cd55-167">輸入</span><span class="sxs-lookup"><span data-stu-id="3cd55-167">INPUTS</span></span>

### <span data-ttu-id="3cd55-168">System.String</span><span class="sxs-lookup"><span data-stu-id="3cd55-168">System.String</span></span>

<span data-ttu-id="3cd55-169">您可以使用管線將 JSON 字串傳送至 `ConvertFrom-Json` 。</span><span class="sxs-lookup"><span data-stu-id="3cd55-169">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="3cd55-170">輸出</span><span class="sxs-lookup"><span data-stu-id="3cd55-170">OUTPUTS</span></span>

### <span data-ttu-id="3cd55-171">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="3cd55-171">PSCustomObject</span></span>

### <span data-ttu-id="3cd55-172">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="3cd55-172">System.Collections.Hashtable</span></span>

## <span data-ttu-id="3cd55-173">注意</span><span class="sxs-lookup"><span data-stu-id="3cd55-173">NOTES</span></span>

<span data-ttu-id="3cd55-174">此 Cmdlet 會使用 [Newtonsoft Json.NET](https://www.newtonsoft.com/json)來執行。</span><span class="sxs-lookup"><span data-stu-id="3cd55-174">This cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

<span data-ttu-id="3cd55-175">從 PowerShell 6 開始， `ConvertTo-Json` 會嘗試將格式化為時間戳記的字串轉換成 **DateTime** 值。</span><span class="sxs-lookup"><span data-stu-id="3cd55-175">Beginning in PowerShell 6, `ConvertTo-Json` attempts to convert strings formatted as timestamps to **DateTime** values.</span></span> <span data-ttu-id="3cd55-176">轉換的值是 `[datetime]` 具有屬性設定的實例，如下 `Kind` 所示：</span><span class="sxs-lookup"><span data-stu-id="3cd55-176">The converted value is a `[datetime]` instance with a `Kind` property set as follows:</span></span>

- <span data-ttu-id="3cd55-177">`Unspecified`如果輸入字串中沒有時區資訊，則為。</span><span class="sxs-lookup"><span data-stu-id="3cd55-177">`Unspecified`, if there is no time zone information in the input string.</span></span>
- <span data-ttu-id="3cd55-178">`Utc`如果時區資訊是尾端的，則為 `Z` 。</span><span class="sxs-lookup"><span data-stu-id="3cd55-178">`Utc`, if the time zone information is a trailing `Z`.</span></span>
- <span data-ttu-id="3cd55-179">`Local`，如果將時區資訊指定為尾端的 UTC _時差_ （例如） `+02:00` 。</span><span class="sxs-lookup"><span data-stu-id="3cd55-179">`Local`, if the time zone information is given as a trailing UTC _offset_ like `+02:00`.</span></span> <span data-ttu-id="3cd55-180">位移會正確地轉換為呼叫端的設定時區。</span><span class="sxs-lookup"><span data-stu-id="3cd55-180">The offset is properly converted to the caller's configured time zone.</span></span> <span data-ttu-id="3cd55-181">預設的輸出格式不表示原始時區位移。</span><span class="sxs-lookup"><span data-stu-id="3cd55-181">The default output formatting does not indicate the original time zone offset.</span></span>

## <span data-ttu-id="3cd55-182">相關連結</span><span class="sxs-lookup"><span data-stu-id="3cd55-182">RELATED LINKS</span></span>

<span data-ttu-id="3cd55-183">[JavaScript 和 .NET 中的 JavaScript 物件標記法 (JSON) 簡介](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="3cd55-183">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="3cd55-184">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="3cd55-184">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="3cd55-185">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="3cd55-185">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="3cd55-186">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="3cd55-186">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
