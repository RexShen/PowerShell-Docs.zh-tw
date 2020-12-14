---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: 9638577ef63a6f5d81fa1f84aee355c080ab6538
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913371"
---
# <span data-ttu-id="e92ec-102">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="e92ec-102">ConvertTo-Csv</span></span>

## <span data-ttu-id="e92ec-103">概要</span><span class="sxs-lookup"><span data-stu-id="e92ec-103">SYNOPSIS</span></span>
<span data-ttu-id="e92ec-104">將 .NET 物件轉換成一系列的字元分隔值， (CSV) 字串。</span><span class="sxs-lookup"><span data-stu-id="e92ec-104">Converts .NET objects into a series of character-separated value (CSV) strings.</span></span>

## <span data-ttu-id="e92ec-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e92ec-105">SYNTAX</span></span>

### <span data-ttu-id="e92ec-106">Delimiter (預設值)</span><span class="sxs-lookup"><span data-stu-id="e92ec-106">Delimiter (Default)</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

### <span data-ttu-id="e92ec-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="e92ec-107">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

## <span data-ttu-id="e92ec-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e92ec-108">DESCRIPTION</span></span>

<span data-ttu-id="e92ec-109">`ConvertTo-CSV`Cmdlet 會傳回一系列以逗號分隔的值， (CSV) 字串，代表您提交的物件。</span><span class="sxs-lookup"><span data-stu-id="e92ec-109">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="e92ec-110">然後，您可以使用 `ConvertFrom-Csv` Cmdlet 從 CSV 字串重新建立物件。</span><span class="sxs-lookup"><span data-stu-id="e92ec-110">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="e92ec-111">從 CSV 轉換的物件是原始物件的字串值，這些物件包含屬性值且沒有任何方法。</span><span class="sxs-lookup"><span data-stu-id="e92ec-111">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="e92ec-112">您可以使用 `Export-Csv` Cmdlet，將物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="e92ec-112">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="e92ec-113">`Export-CSV` 類似于 `ConvertTo-CSV` ，不同之處在于它會將 CSV 字串儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="e92ec-113">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="e92ec-114">`ConvertTo-CSV`Cmdlet 有參數可指定逗號以外的分隔符號，或使用目前的文化特性做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e92ec-114">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="e92ec-115">範例</span><span class="sxs-lookup"><span data-stu-id="e92ec-115">EXAMPLES</span></span>

### <span data-ttu-id="e92ec-116">範例1：將物件轉換為 CSV</span><span class="sxs-lookup"><span data-stu-id="e92ec-116">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="e92ec-117">這個範例會將 **處理** 程式物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="e92ec-117">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name pwsh | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"pwsh","8","950","2204001161216","100925440","59686912","67104", ...
```

<span data-ttu-id="e92ec-118">`Get-Process`Cmdlet 會取得 **處理** 程式物件，並使用 **Name** 參數來指定 PowerShell 處理常式。</span><span class="sxs-lookup"><span data-stu-id="e92ec-118">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="e92ec-119">進程物件會向下傳送至 `ConvertTo-CSV` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e92ec-119">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="e92ec-120">`ConvertTo-CSV`Cmdlet 會將物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="e92ec-120">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="e92ec-121">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="e92ec-121">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="e92ec-122">範例2：將 DateTime 物件轉換成 CSV</span><span class="sxs-lookup"><span data-stu-id="e92ec-122">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="e92ec-123">這個範例會將 **DateTime** 物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="e92ec-123">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="e92ec-124">`Get-Date`Cmdlet 會取得 **DateTime** 物件，並將它儲存在 `$Date` 變數中。</span><span class="sxs-lookup"><span data-stu-id="e92ec-124">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="e92ec-125">`ConvertTo-Csv`Cmdlet 會將 **DateTime** 物件轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="e92ec-125">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="e92ec-126">**InputObject** 參數會使用儲存在變數中的 **DateTime** 物件 `$Date` 。</span><span class="sxs-lookup"><span data-stu-id="e92ec-126">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="e92ec-127">**分隔符號** 參數會指定分號來分隔字串值。</span><span class="sxs-lookup"><span data-stu-id="e92ec-127">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="e92ec-128">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="e92ec-128">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="e92ec-129">範例3：將 PowerShell 事件記錄檔轉換成 CSV</span><span class="sxs-lookup"><span data-stu-id="e92ec-129">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="e92ec-130">此範例會將 PowerShell 的 Windows 事件記錄檔轉換成一系列 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="e92ec-130">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'PowerShellCore/Operational' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error""4100","1",,"3","106","19","0","31716","PowerShellCore", ...
```

<span data-ttu-id="e92ec-131">此 `Get-Culture` Cmdlet 會使用 **TextInfo** 和 **ListSeparator** 的 nested 屬性，並顯示目前文化特性的預設清單分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e92ec-131">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="e92ec-132">`Get-WinEvent`Cmdlet 會取得事件記錄檔物件，並使用 **LogName** 參數來指定記錄檔名稱。</span><span class="sxs-lookup"><span data-stu-id="e92ec-132">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="e92ec-133">事件記錄檔物件會以管線傳送至 `ConvertTo-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e92ec-133">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="e92ec-134">指令程式會 `ConvertTo-Csv` 將事件記錄檔物件轉換成一系列的 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="e92ec-134">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="e92ec-135">**UseCulture** 參數會使用目前文化特性的預設清單分隔符號做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e92ec-135">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="e92ec-136">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="e92ec-136">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="e92ec-137">範例4：在兩個數據行周圍轉換成具有引號的 CSV</span><span class="sxs-lookup"><span data-stu-id="e92ec-137">Example 4: Convert to CSV with quotes around two columns</span></span>

<span data-ttu-id="e92ec-138">這個範例會將 **DateTime** 物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="e92ec-138">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -QuoteFields "DateTime","Date"
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### <span data-ttu-id="e92ec-139">範例4：只有在需要時才使用引號轉換成 CSV</span><span class="sxs-lookup"><span data-stu-id="e92ec-139">Example 4: Convert to CSV with quotes only when needed</span></span>

<span data-ttu-id="e92ec-140">這個範例會將 **DateTime** 物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="e92ec-140">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -UseQuotes AsNeeded
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## <span data-ttu-id="e92ec-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e92ec-141">PARAMETERS</span></span>

### <span data-ttu-id="e92ec-142">-Delimiter</span><span class="sxs-lookup"><span data-stu-id="e92ec-142">-Delimiter</span></span>

<span data-ttu-id="e92ec-143">指定分隔符號，以分隔 CSV 字串中的屬性值。</span><span class="sxs-lookup"><span data-stu-id="e92ec-143">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="e92ec-144">預設值是逗號 (`,`) 。</span><span class="sxs-lookup"><span data-stu-id="e92ec-144">The default is a comma (`,`).</span></span> <span data-ttu-id="e92ec-145">輸入字元，例如冒號 (`:`) 。</span><span class="sxs-lookup"><span data-stu-id="e92ec-145">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="e92ec-146">若要指定分號 (`;`) 將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="e92ec-146">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

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

### <span data-ttu-id="e92ec-147">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="e92ec-147">-IncludeTypeInformation</span></span>

<span data-ttu-id="e92ec-148">使用這個參數時，輸出的第一行會包含 **#TYPE** ，後面接著物件類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="e92ec-148">When this parameter is used the first line of the output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="e92ec-149">例如， **#TYPE 的系統診斷**。</span><span class="sxs-lookup"><span data-stu-id="e92ec-149">For example, **#TYPE System.Diagnostics.Process**.</span></span>

<span data-ttu-id="e92ec-150">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="e92ec-150">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="e92ec-151">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e92ec-151">-InputObject</span></span>

<span data-ttu-id="e92ec-152">指定轉換為 CSV 字串的物件。</span><span class="sxs-lookup"><span data-stu-id="e92ec-152">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="e92ec-153">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="e92ec-153">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="e92ec-154">您也可以透過管線將物件傳送至 `ConvertTo-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="e92ec-154">You can also pipe objects to `ConvertTo-CSV`.</span></span>

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

### <span data-ttu-id="e92ec-155">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="e92ec-155">-NoTypeInformation</span></span>

<span data-ttu-id="e92ec-156">從輸出中移除 **#TYPE** 資訊標頭。</span><span class="sxs-lookup"><span data-stu-id="e92ec-156">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="e92ec-157">此參數會成為 PowerShell 6.0 中的預設值，並包含以提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="e92ec-157">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="e92ec-158">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="e92ec-158">-UseCulture</span></span>

<span data-ttu-id="e92ec-159">使用目前文化特性的清單分隔字元做為專案分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e92ec-159">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="e92ec-160">若要尋找文化特性的清單分隔符號，請使用下列命令： `(Get-Culture).TextInfo.ListSeparator` 。</span><span class="sxs-lookup"><span data-stu-id="e92ec-160">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="e92ec-161">-QuoteFields</span><span class="sxs-lookup"><span data-stu-id="e92ec-161">-QuoteFields</span></span>

<span data-ttu-id="e92ec-162">指定應該加上引號的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="e92ec-162">Specifies the names of the columns that should be quoted.</span></span> <span data-ttu-id="e92ec-163">使用這個參數時，只會將指定的資料行加上引號。</span><span class="sxs-lookup"><span data-stu-id="e92ec-163">When this parameter is used only the specified columns are quoted.</span></span> <span data-ttu-id="e92ec-164">此參數已新增至 PowerShell 7.0。</span><span class="sxs-lookup"><span data-stu-id="e92ec-164">This parameter was added in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="e92ec-165">-UseQuotes</span><span class="sxs-lookup"><span data-stu-id="e92ec-165">-UseQuotes</span></span>

<span data-ttu-id="e92ec-166">指定 CSV 檔案中使用引號的時機。</span><span class="sxs-lookup"><span data-stu-id="e92ec-166">Specifies when quotes are used in the CSV files.</span></span> <span data-ttu-id="e92ec-167">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="e92ec-167">Possible values are:</span></span>

- <span data-ttu-id="e92ec-168">永遠不會引述任何事</span><span class="sxs-lookup"><span data-stu-id="e92ec-168">Never - don't quote anything</span></span>
- <span data-ttu-id="e92ec-169">一律將所有專案加上引號 (預設行為) </span><span class="sxs-lookup"><span data-stu-id="e92ec-169">Always - quote everything (default behavior)</span></span>
- <span data-ttu-id="e92ec-170">>asneeded-僅包含分隔符號的引號欄位</span><span class="sxs-lookup"><span data-stu-id="e92ec-170">AsNeeded - only quote fields that contain a delimiter character</span></span>

<span data-ttu-id="e92ec-171">此參數已新增至 PowerShell 7.0。</span><span class="sxs-lookup"><span data-stu-id="e92ec-171">This parameter was added in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="e92ec-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e92ec-172">CommonParameters</span></span>

<span data-ttu-id="e92ec-173">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e92ec-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e92ec-174">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e92ec-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e92ec-175">輸入</span><span class="sxs-lookup"><span data-stu-id="e92ec-175">INPUTS</span></span>

### <span data-ttu-id="e92ec-176">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="e92ec-176">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e92ec-177">您可以使用管線將具有擴充類型系統 (ETS) adapter 的任何物件傳送至 `ConvertTo-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="e92ec-177">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="e92ec-178">輸出</span><span class="sxs-lookup"><span data-stu-id="e92ec-178">OUTPUTS</span></span>

### <span data-ttu-id="e92ec-179">System.String</span><span class="sxs-lookup"><span data-stu-id="e92ec-179">System.String</span></span>

<span data-ttu-id="e92ec-180">CSV 輸出會以字串集合的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="e92ec-180">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="e92ec-181">注意</span><span class="sxs-lookup"><span data-stu-id="e92ec-181">NOTES</span></span>

<span data-ttu-id="e92ec-182">在 CSV 格式中，每個物件都會以其屬性值的逗號分隔清單表示。</span><span class="sxs-lookup"><span data-stu-id="e92ec-182">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="e92ec-183">屬性值會使用物件的 **ToString ( # B1** 方法轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="e92ec-183">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="e92ec-184">字串會以屬性值名稱表示。</span><span class="sxs-lookup"><span data-stu-id="e92ec-184">The strings are represented by the property value name.</span></span> <span data-ttu-id="e92ec-185">`ConvertTo-CSV` 不會匯出物件的方法。</span><span class="sxs-lookup"><span data-stu-id="e92ec-185">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="e92ec-186">CSV 字串的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="e92ec-186">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="e92ec-187">如果使用 **IncludeTypeInformation** ，則第一個字串是由 **#TYPE** 後面接著物件類型的完整名稱所組成。</span><span class="sxs-lookup"><span data-stu-id="e92ec-187">If **IncludeTypeInformation** is used, the first string consists of **#TYPE** followed by the object type's fully qualified name.</span></span> <span data-ttu-id="e92ec-188">例如， **#TYPE 的系統診斷**。</span><span class="sxs-lookup"><span data-stu-id="e92ec-188">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="e92ec-189">如果未使用 **IncludeTypeInformation** ，則第一個字串會包含資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="e92ec-189">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="e92ec-190">標頭包含第一個物件的屬性名稱，做為逗點分隔清單。</span><span class="sxs-lookup"><span data-stu-id="e92ec-190">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="e92ec-191">其餘的字串包含每個物件之屬性值的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="e92ec-191">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="e92ec-192">從 PowerShell 6.0 開始，的預設行為 `ConvertTo-CSV` 是不包含 CSV 中的 **#TYPE** 資訊，而且 **NoTypeInformation** 是隱含的。</span><span class="sxs-lookup"><span data-stu-id="e92ec-192">Beginning with PowerShell 6.0 the default behavior of `ConvertTo-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="e92ec-193">**IncludeTypeInformation** 可以用來包含 **#TYPE** 資訊，並模擬 `ConvertTo-CSV` PowerShell 6.0 之前的預設行為。</span><span class="sxs-lookup"><span data-stu-id="e92ec-193">**IncludeTypeInformation** can be used to include the **#TYPE** information and emulate the default behavior of `ConvertTo-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="e92ec-194">當您將多個物件提交至時 `ConvertTo-CSV` ，會 `ConvertTo-CSV` 根據您提交的第一個物件的屬性來排序字串。</span><span class="sxs-lookup"><span data-stu-id="e92ec-194">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="e92ec-195">如果其餘的物件沒有其中一個指定的屬性，則該物件的屬性值會是 Null，以兩個連續的逗號表示。</span><span class="sxs-lookup"><span data-stu-id="e92ec-195">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="e92ec-196">如果其餘的物件有其他屬性，則會忽略那些屬性值。</span><span class="sxs-lookup"><span data-stu-id="e92ec-196">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="e92ec-197">相關連結</span><span class="sxs-lookup"><span data-stu-id="e92ec-197">RELATED LINKS</span></span>

[<span data-ttu-id="e92ec-198">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="e92ec-198">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="e92ec-199">匯出-Csv</span><span class="sxs-lookup"><span data-stu-id="e92ec-199">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="e92ec-200">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="e92ec-200">Import-Csv</span></span>](Import-Csv.md)
