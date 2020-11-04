---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: e4cc40e7a9a5fdcd12b6a787607e4979ddbb3273
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204239"
---
# <span data-ttu-id="10cdd-103">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="10cdd-103">ConvertTo-Csv</span></span>

## <span data-ttu-id="10cdd-104">概要</span><span class="sxs-lookup"><span data-stu-id="10cdd-104">SYNOPSIS</span></span>
<span data-ttu-id="10cdd-105">將 .NET 物件轉換成一系列的字元分隔值， (CSV) 字串。</span><span class="sxs-lookup"><span data-stu-id="10cdd-105">Converts .NET objects into a series of character-separated value (CSV) strings.</span></span>

## <span data-ttu-id="10cdd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="10cdd-106">SYNTAX</span></span>

### <span data-ttu-id="10cdd-107">分隔符號</span><span class="sxs-lookup"><span data-stu-id="10cdd-107">Delimiter</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

### <span data-ttu-id="10cdd-108">UseCulture</span><span class="sxs-lookup"><span data-stu-id="10cdd-108">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

## <span data-ttu-id="10cdd-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="10cdd-109">DESCRIPTION</span></span>

<span data-ttu-id="10cdd-110">`ConvertTo-CSV`Cmdlet 會傳回一系列以逗號分隔的值， (CSV) 字串，代表您提交的物件。</span><span class="sxs-lookup"><span data-stu-id="10cdd-110">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="10cdd-111">然後，您可以使用 `ConvertFrom-Csv` Cmdlet 從 CSV 字串重新建立物件。</span><span class="sxs-lookup"><span data-stu-id="10cdd-111">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="10cdd-112">從 CSV 轉換的物件是原始物件的字串值，這些物件包含屬性值且沒有任何方法。</span><span class="sxs-lookup"><span data-stu-id="10cdd-112">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="10cdd-113">您可以使用 `Export-Csv` Cmdlet，將物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="10cdd-113">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="10cdd-114">`Export-CSV` 類似于 `ConvertTo-CSV` ，不同之處在于它會將 CSV 字串儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="10cdd-114">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="10cdd-115">`ConvertTo-CSV`Cmdlet 有參數可指定逗號以外的分隔符號，或使用目前的文化特性做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="10cdd-115">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="10cdd-116">範例</span><span class="sxs-lookup"><span data-stu-id="10cdd-116">EXAMPLES</span></span>

### <span data-ttu-id="10cdd-117">範例1：將物件轉換為 CSV</span><span class="sxs-lookup"><span data-stu-id="10cdd-117">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="10cdd-118">這個範例會將 **處理** 程式物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="10cdd-118">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name pwsh | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"pwsh","8","950","2204001161216","100925440","59686912","67104", ...
```

<span data-ttu-id="10cdd-119">`Get-Process`Cmdlet 會取得 **處理** 程式物件，並使用 **Name** 參數來指定 PowerShell 處理常式。</span><span class="sxs-lookup"><span data-stu-id="10cdd-119">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="10cdd-120">進程物件會向下傳送至 `ConvertTo-CSV` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="10cdd-120">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="10cdd-121">`ConvertTo-CSV`Cmdlet 會將物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="10cdd-121">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="10cdd-122">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="10cdd-122">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="10cdd-123">範例2：將 DateTime 物件轉換成 CSV</span><span class="sxs-lookup"><span data-stu-id="10cdd-123">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="10cdd-124">這個範例會將 **DateTime** 物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="10cdd-124">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="10cdd-125">`Get-Date`Cmdlet 會取得 **DateTime** 物件，並將它儲存在 `$Date` 變數中。</span><span class="sxs-lookup"><span data-stu-id="10cdd-125">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="10cdd-126">`ConvertTo-Csv`Cmdlet 會將 **DateTime** 物件轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="10cdd-126">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="10cdd-127">**InputObject** 參數會使用儲存在變數中的 **DateTime** 物件 `$Date` 。</span><span class="sxs-lookup"><span data-stu-id="10cdd-127">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="10cdd-128">**分隔符號** 參數會指定分號來分隔字串值。</span><span class="sxs-lookup"><span data-stu-id="10cdd-128">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="10cdd-129">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="10cdd-129">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="10cdd-130">範例3：將 PowerShell 事件記錄檔轉換成 CSV</span><span class="sxs-lookup"><span data-stu-id="10cdd-130">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="10cdd-131">此範例會將 PowerShell 的 Windows 事件記錄檔轉換成一系列 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="10cdd-131">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'PowerShellCore/Operational' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error""4100","1",,"3","106","19","0","31716","PowerShellCore", ...
```

<span data-ttu-id="10cdd-132">此 `Get-Culture` Cmdlet 會使用 **TextInfo** 和 **ListSeparator** 的 nested 屬性，並顯示目前文化特性的預設清單分隔符號。</span><span class="sxs-lookup"><span data-stu-id="10cdd-132">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="10cdd-133">`Get-WinEvent`Cmdlet 會取得事件記錄檔物件，並使用 **LogName** 參數來指定記錄檔名稱。</span><span class="sxs-lookup"><span data-stu-id="10cdd-133">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="10cdd-134">事件記錄檔物件會以管線傳送至 `ConvertTo-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="10cdd-134">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="10cdd-135">指令程式會 `ConvertTo-Csv` 將事件記錄檔物件轉換成一系列的 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="10cdd-135">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="10cdd-136">**UseCulture** 參數會使用目前文化特性的預設清單分隔符號做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="10cdd-136">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="10cdd-137">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="10cdd-137">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="10cdd-138">範例4：在兩個數據行周圍轉換成具有引號的 CSV</span><span class="sxs-lookup"><span data-stu-id="10cdd-138">Example 4: Convert to CSV with quotes around two columns</span></span>

<span data-ttu-id="10cdd-139">這個範例會將 **DateTime** 物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="10cdd-139">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -QuoteFields "DateTime","Date"
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### <span data-ttu-id="10cdd-140">範例4：只有在需要時才使用引號轉換成 CSV</span><span class="sxs-lookup"><span data-stu-id="10cdd-140">Example 4: Convert to CSV with quotes only when needed</span></span>

<span data-ttu-id="10cdd-141">這個範例會將 **DateTime** 物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="10cdd-141">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -UseQuotes AsNeeded
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## <span data-ttu-id="10cdd-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="10cdd-142">PARAMETERS</span></span>

### <span data-ttu-id="10cdd-143">-Delimiter</span><span class="sxs-lookup"><span data-stu-id="10cdd-143">-Delimiter</span></span>

<span data-ttu-id="10cdd-144">指定分隔符號，以分隔 CSV 字串中的屬性值。</span><span class="sxs-lookup"><span data-stu-id="10cdd-144">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="10cdd-145">預設值是逗號 (`,`) 。</span><span class="sxs-lookup"><span data-stu-id="10cdd-145">The default is a comma (`,`).</span></span> <span data-ttu-id="10cdd-146">輸入字元，例如冒號 (`:`) 。</span><span class="sxs-lookup"><span data-stu-id="10cdd-146">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="10cdd-147">若要指定分號 (`;`) 將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="10cdd-147">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="10cdd-148">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="10cdd-148">-IncludeTypeInformation</span></span>

<span data-ttu-id="10cdd-149">使用這個參數時，輸出的第一行會包含 **#TYPE** ，後面接著物件類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="10cdd-149">When this parameter is used the first line of the output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="10cdd-150">例如， **#TYPE 的系統診斷** 。</span><span class="sxs-lookup"><span data-stu-id="10cdd-150">For example, **#TYPE System.Diagnostics.Process** .</span></span>

<span data-ttu-id="10cdd-151">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="10cdd-151">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="10cdd-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="10cdd-152">-InputObject</span></span>

<span data-ttu-id="10cdd-153">指定轉換為 CSV 字串的物件。</span><span class="sxs-lookup"><span data-stu-id="10cdd-153">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="10cdd-154">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="10cdd-154">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="10cdd-155">您也可以透過管線將物件傳送至 `ConvertTo-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="10cdd-155">You can also pipe objects to `ConvertTo-CSV`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="10cdd-156">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="10cdd-156">-NoTypeInformation</span></span>

<span data-ttu-id="10cdd-157">從輸出中移除 **#TYPE** 資訊標頭。</span><span class="sxs-lookup"><span data-stu-id="10cdd-157">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="10cdd-158">此參數會成為 PowerShell 6.0 中的預設值，並包含以提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="10cdd-158">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="10cdd-159">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="10cdd-159">-UseCulture</span></span>

<span data-ttu-id="10cdd-160">使用目前文化特性的清單分隔字元做為專案分隔符號。</span><span class="sxs-lookup"><span data-stu-id="10cdd-160">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="10cdd-161">若要尋找文化特性的清單分隔符號，請使用下列命令： `(Get-Culture).TextInfo.ListSeparator` 。</span><span class="sxs-lookup"><span data-stu-id="10cdd-161">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="10cdd-162">-QuoteFields</span><span class="sxs-lookup"><span data-stu-id="10cdd-162">-QuoteFields</span></span>

<span data-ttu-id="10cdd-163">指定應該加上引號的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="10cdd-163">Specifies the names of the columns that should be quoted.</span></span> <span data-ttu-id="10cdd-164">使用這個參數時，只會將指定的資料行加上引號。</span><span class="sxs-lookup"><span data-stu-id="10cdd-164">When this parameter is used only the specified columns are quoted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="10cdd-165">-UseQuotes</span><span class="sxs-lookup"><span data-stu-id="10cdd-165">-UseQuotes</span></span>

<span data-ttu-id="10cdd-166">指定 CSV 檔案中使用引號的時機。</span><span class="sxs-lookup"><span data-stu-id="10cdd-166">Specifies when quotes are used in the CSV files.</span></span> <span data-ttu-id="10cdd-167">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="10cdd-167">Possible values are:</span></span>

- <span data-ttu-id="10cdd-168">永遠不會引述任何事</span><span class="sxs-lookup"><span data-stu-id="10cdd-168">Never - don't quote anything</span></span>
- <span data-ttu-id="10cdd-169">一律將所有專案加上引號 (預設行為) </span><span class="sxs-lookup"><span data-stu-id="10cdd-169">Always - quote everything (default behavior)</span></span>
- <span data-ttu-id="10cdd-170">>asneeded-僅包含分隔符號的引號欄位</span><span class="sxs-lookup"><span data-stu-id="10cdd-170">AsNeeded - only quote fields that contain a delimiter character</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="10cdd-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="10cdd-171">CommonParameters</span></span>

<span data-ttu-id="10cdd-172">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="10cdd-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="10cdd-173">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="10cdd-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="10cdd-174">輸入</span><span class="sxs-lookup"><span data-stu-id="10cdd-174">INPUTS</span></span>

### <span data-ttu-id="10cdd-175">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="10cdd-175">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="10cdd-176">您可以使用管線將具有擴充類型系統 (ETS) adapter 的任何物件傳送至 `ConvertTo-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="10cdd-176">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="10cdd-177">輸出</span><span class="sxs-lookup"><span data-stu-id="10cdd-177">OUTPUTS</span></span>

### <span data-ttu-id="10cdd-178">System.String</span><span class="sxs-lookup"><span data-stu-id="10cdd-178">System.String</span></span>

<span data-ttu-id="10cdd-179">CSV 輸出會以字串集合的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="10cdd-179">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="10cdd-180">注意</span><span class="sxs-lookup"><span data-stu-id="10cdd-180">NOTES</span></span>

<span data-ttu-id="10cdd-181">在 CSV 格式中，每個物件都會以其屬性值的逗號分隔清單表示。</span><span class="sxs-lookup"><span data-stu-id="10cdd-181">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="10cdd-182">屬性值會使用物件的 **ToString ( # B1** 方法轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="10cdd-182">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="10cdd-183">字串會以屬性值名稱表示。</span><span class="sxs-lookup"><span data-stu-id="10cdd-183">The strings are represented by the property value name.</span></span> <span data-ttu-id="10cdd-184">`ConvertTo-CSV` 不會匯出物件的方法。</span><span class="sxs-lookup"><span data-stu-id="10cdd-184">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="10cdd-185">CSV 字串的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="10cdd-185">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="10cdd-186">如果使用 **IncludeTypeInformation** ，則第一個字串是由 **#TYPE** 後面接著物件類型的完整名稱所組成。</span><span class="sxs-lookup"><span data-stu-id="10cdd-186">If **IncludeTypeInformation** is used, the first string consists of **#TYPE** followed by the object type's fully qualified name.</span></span> <span data-ttu-id="10cdd-187">例如， **#TYPE 的系統診斷** 。</span><span class="sxs-lookup"><span data-stu-id="10cdd-187">For example, **#TYPE System.Diagnostics.Process** .</span></span>
- <span data-ttu-id="10cdd-188">如果未使用 **IncludeTypeInformation** ，則第一個字串會包含資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="10cdd-188">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="10cdd-189">標頭包含第一個物件的屬性名稱，做為逗點分隔清單。</span><span class="sxs-lookup"><span data-stu-id="10cdd-189">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="10cdd-190">其餘的字串包含每個物件之屬性值的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="10cdd-190">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="10cdd-191">從 PowerShell 6.0 開始，的預設行為 `ConvertTo-CSV` 是不包含 CSV 中的 **#TYPE** 資訊，而且 **NoTypeInformation** 是隱含的。</span><span class="sxs-lookup"><span data-stu-id="10cdd-191">Beginning with PowerShell 6.0 the default behavior of `ConvertTo-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="10cdd-192">**IncludeTypeInformation** 可以用來包含 **#TYPE** 資訊，並模擬 `ConvertTo-CSV` PowerShell 6.0 之前的預設行為。</span><span class="sxs-lookup"><span data-stu-id="10cdd-192">**IncludeTypeInformation** can be used to include the **#TYPE** information and emulate the default behavior of `ConvertTo-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="10cdd-193">當您將多個物件提交至時 `ConvertTo-CSV` ，會 `ConvertTo-CSV` 根據您提交的第一個物件的屬性來排序字串。</span><span class="sxs-lookup"><span data-stu-id="10cdd-193">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="10cdd-194">如果其餘的物件沒有其中一個指定的屬性，則該物件的屬性值會是 Null，以兩個連續的逗號表示。</span><span class="sxs-lookup"><span data-stu-id="10cdd-194">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="10cdd-195">如果其餘的物件有其他屬性，則會忽略那些屬性值。</span><span class="sxs-lookup"><span data-stu-id="10cdd-195">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="10cdd-196">相關連結</span><span class="sxs-lookup"><span data-stu-id="10cdd-196">RELATED LINKS</span></span>

[<span data-ttu-id="10cdd-197">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="10cdd-197">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="10cdd-198">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="10cdd-198">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="10cdd-199">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="10cdd-199">Import-Csv</span></span>](Import-Csv.md)
