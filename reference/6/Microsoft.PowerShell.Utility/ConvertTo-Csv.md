---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: 5de6a3bd28b850d3fc1632e26998986f302b78f8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204700"
---
# <span data-ttu-id="de772-103">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="de772-103">ConvertTo-Csv</span></span>

## <span data-ttu-id="de772-104">概要</span><span class="sxs-lookup"><span data-stu-id="de772-104">SYNOPSIS</span></span>
<span data-ttu-id="de772-105">將 .NET 物件轉換成一系列的字元分隔值， (CSV) 字串。</span><span class="sxs-lookup"><span data-stu-id="de772-105">Converts .NET objects into a series of character-separated value (CSV) strings.</span></span>

## <span data-ttu-id="de772-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="de772-106">SYNTAX</span></span>

### <span data-ttu-id="de772-107">DelimiterPath (預設) </span><span class="sxs-lookup"><span data-stu-id="de772-107">DelimiterPath (Default)</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-IncludeTypeInformation] [-NoTypeInformation]
 [<CommonParameters>]
```

### <span data-ttu-id="de772-108">分隔符號</span><span class="sxs-lookup"><span data-stu-id="de772-108">Delimiter</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [<CommonParameters>]
```

### <span data-ttu-id="de772-109">UseCulture</span><span class="sxs-lookup"><span data-stu-id="de772-109">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [<CommonParameters>]
```

## <span data-ttu-id="de772-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="de772-110">DESCRIPTION</span></span>

<span data-ttu-id="de772-111">`ConvertTo-CSV`Cmdlet 會傳回一系列以逗號分隔的值， (CSV) 字串，代表您提交的物件。</span><span class="sxs-lookup"><span data-stu-id="de772-111">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="de772-112">然後，您可以使用 `ConvertFrom-Csv` Cmdlet 從 CSV 字串重新建立物件。</span><span class="sxs-lookup"><span data-stu-id="de772-112">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="de772-113">從 CSV 轉換的物件是原始物件的字串值，這些物件包含屬性值且沒有任何方法。</span><span class="sxs-lookup"><span data-stu-id="de772-113">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="de772-114">您可以使用 `Export-Csv` Cmdlet，將物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="de772-114">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="de772-115">`Export-CSV` 類似于 `ConvertTo-CSV` ，不同之處在于它會將 CSV 字串儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="de772-115">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="de772-116">`ConvertTo-CSV`Cmdlet 有參數可指定逗號以外的分隔符號，或使用目前的文化特性做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="de772-116">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="de772-117">範例</span><span class="sxs-lookup"><span data-stu-id="de772-117">EXAMPLES</span></span>

### <span data-ttu-id="de772-118">範例1：將物件轉換為 CSV</span><span class="sxs-lookup"><span data-stu-id="de772-118">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="de772-119">這個範例會將 **處理** 程式物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="de772-119">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name pwsh | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"pwsh","8","950","2204001161216","100925440","59686912","67104", ...
```

<span data-ttu-id="de772-120">`Get-Process`Cmdlet 會取得 **處理** 程式物件，並使用 **Name** 參數來指定 PowerShell 處理常式。</span><span class="sxs-lookup"><span data-stu-id="de772-120">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="de772-121">進程物件會向下傳送至 `ConvertTo-CSV` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="de772-121">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="de772-122">`ConvertTo-CSV`Cmdlet 會將物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="de772-122">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="de772-123">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="de772-123">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="de772-124">範例2：將 DateTime 物件轉換成 CSV</span><span class="sxs-lookup"><span data-stu-id="de772-124">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="de772-125">這個範例會將 **DateTime** 物件轉換成 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="de772-125">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="de772-126">`Get-Date`Cmdlet 會取得 **DateTime** 物件，並將它儲存在 `$Date` 變數中。</span><span class="sxs-lookup"><span data-stu-id="de772-126">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="de772-127">`ConvertTo-Csv`Cmdlet 會將 **DateTime** 物件轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="de772-127">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="de772-128">**InputObject** 參數會使用儲存在變數中的 **DateTime** 物件 `$Date` 。</span><span class="sxs-lookup"><span data-stu-id="de772-128">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="de772-129">**分隔符號** 參數會指定分號來分隔字串值。</span><span class="sxs-lookup"><span data-stu-id="de772-129">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="de772-130">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="de772-130">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="de772-131">範例3：將 PowerShell 事件記錄檔轉換成 CSV</span><span class="sxs-lookup"><span data-stu-id="de772-131">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="de772-132">此範例會將 PowerShell 的 Windows 事件記錄檔轉換成一系列 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="de772-132">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'PowerShellCore/Operational' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error""4100","1",,"3","106","19","0","31716","PowerShellCore", ...
```

<span data-ttu-id="de772-133">此 `Get-Culture` Cmdlet 會使用 **TextInfo** 和 **ListSeparator** 的 nested 屬性，並顯示目前文化特性的預設清單分隔符號。</span><span class="sxs-lookup"><span data-stu-id="de772-133">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="de772-134">`Get-WinEvent`Cmdlet 會取得事件記錄檔物件，並使用 **LogName** 參數來指定記錄檔名稱。</span><span class="sxs-lookup"><span data-stu-id="de772-134">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="de772-135">事件記錄檔物件會以管線傳送至 `ConvertTo-Csv` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="de772-135">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="de772-136">指令程式會 `ConvertTo-Csv` 將事件記錄檔物件轉換成一系列的 CSV 字串。</span><span class="sxs-lookup"><span data-stu-id="de772-136">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="de772-137">**UseCulture** 參數會使用目前文化特性的預設清單分隔符號做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="de772-137">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="de772-138">**NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。</span><span class="sxs-lookup"><span data-stu-id="de772-138">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

## <span data-ttu-id="de772-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="de772-139">PARAMETERS</span></span>

### <span data-ttu-id="de772-140">-Delimiter</span><span class="sxs-lookup"><span data-stu-id="de772-140">-Delimiter</span></span>

<span data-ttu-id="de772-141">指定分隔符號，以分隔 CSV 字串中的屬性值。</span><span class="sxs-lookup"><span data-stu-id="de772-141">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="de772-142">預設值是逗號 (`,`) 。</span><span class="sxs-lookup"><span data-stu-id="de772-142">The default is a comma (`,`).</span></span> <span data-ttu-id="de772-143">輸入字元，例如冒號 (`:`) 。</span><span class="sxs-lookup"><span data-stu-id="de772-143">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="de772-144">若要指定分號 (`;`) 將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="de772-144">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

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

### <span data-ttu-id="de772-145">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="de772-145">-IncludeTypeInformation</span></span>

<span data-ttu-id="de772-146">使用這個參數時，輸出的第一行會包含 **#TYPE** ，後面接著物件類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="de772-146">When this parameter is used the first line of the output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="de772-147">例如， **#TYPE 的系統診斷** 。</span><span class="sxs-lookup"><span data-stu-id="de772-147">For example, **#TYPE System.Diagnostics.Process** .</span></span>

<span data-ttu-id="de772-148">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="de772-148">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="de772-149">-InputObject</span><span class="sxs-lookup"><span data-stu-id="de772-149">-InputObject</span></span>

<span data-ttu-id="de772-150">指定轉換為 CSV 字串的物件。</span><span class="sxs-lookup"><span data-stu-id="de772-150">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="de772-151">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="de772-151">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="de772-152">您也可以透過管線將物件傳送至 `ConvertTo-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="de772-152">You can also pipe objects to `ConvertTo-CSV`.</span></span>

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

### <span data-ttu-id="de772-153">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="de772-153">-NoTypeInformation</span></span>

<span data-ttu-id="de772-154">從輸出中移除 **#TYPE** 資訊標頭。</span><span class="sxs-lookup"><span data-stu-id="de772-154">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="de772-155">此參數會成為 PowerShell 6.0 中的預設值，並包含以提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="de772-155">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="de772-156">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="de772-156">-UseCulture</span></span>

<span data-ttu-id="de772-157">使用目前文化特性的清單分隔字元做為專案分隔符號。</span><span class="sxs-lookup"><span data-stu-id="de772-157">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="de772-158">若要尋找文化特性的清單分隔符號，請使用下列命令： `(Get-Culture).TextInfo.ListSeparator` 。</span><span class="sxs-lookup"><span data-stu-id="de772-158">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="de772-159">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="de772-159">CommonParameters</span></span>

<span data-ttu-id="de772-160">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="de772-160">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="de772-161">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="de772-161">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="de772-162">輸入</span><span class="sxs-lookup"><span data-stu-id="de772-162">INPUTS</span></span>

### <span data-ttu-id="de772-163">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="de772-163">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="de772-164">您可以使用管線將具有擴充類型系統 (ETS) adapter 的任何物件傳送至 `ConvertTo-CSV` 。</span><span class="sxs-lookup"><span data-stu-id="de772-164">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="de772-165">輸出</span><span class="sxs-lookup"><span data-stu-id="de772-165">OUTPUTS</span></span>

### <span data-ttu-id="de772-166">System.String</span><span class="sxs-lookup"><span data-stu-id="de772-166">System.String</span></span>

<span data-ttu-id="de772-167">CSV 輸出會以字串集合的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="de772-167">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="de772-168">注意</span><span class="sxs-lookup"><span data-stu-id="de772-168">NOTES</span></span>

<span data-ttu-id="de772-169">在 CSV 格式中，每個物件都會以其屬性值的逗號分隔清單表示。</span><span class="sxs-lookup"><span data-stu-id="de772-169">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="de772-170">屬性值會使用物件的 **ToString ( # B1** 方法轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="de772-170">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="de772-171">字串會以屬性值名稱表示。</span><span class="sxs-lookup"><span data-stu-id="de772-171">The strings are represented by the property value name.</span></span> <span data-ttu-id="de772-172">`ConvertTo-CSV` 不會匯出物件的方法。</span><span class="sxs-lookup"><span data-stu-id="de772-172">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="de772-173">CSV 字串的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="de772-173">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="de772-174">如果使用 **IncludeTypeInformation** ，則第一個字串是由 **#TYPE** 後面接著物件類型的完整名稱所組成。</span><span class="sxs-lookup"><span data-stu-id="de772-174">If **IncludeTypeInformation** is used, the first string consists of **#TYPE** followed by the object type's fully qualified name.</span></span> <span data-ttu-id="de772-175">例如， **#TYPE 的系統診斷** 。</span><span class="sxs-lookup"><span data-stu-id="de772-175">For example, **#TYPE System.Diagnostics.Process** .</span></span>
- <span data-ttu-id="de772-176">如果未使用 **IncludeTypeInformation** ，則第一個字串會包含資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="de772-176">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="de772-177">標頭包含第一個物件的屬性名稱，做為逗點分隔清單。</span><span class="sxs-lookup"><span data-stu-id="de772-177">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="de772-178">其餘的字串包含每個物件之屬性值的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="de772-178">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="de772-179">從 PowerShell 6.0 開始，的預設行為 `ConvertTo-CSV` 是不包含 CSV 中的 **#TYPE** 資訊，而且 **NoTypeInformation** 是隱含的。</span><span class="sxs-lookup"><span data-stu-id="de772-179">Beginning with PowerShell 6.0 the default behavior of `ConvertTo-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="de772-180">**IncludeTypeInformation** 可以用來包含 **#TYPE** 資訊，並模擬 `ConvertTo-CSV` PowerShell 6.0 之前的預設行為。</span><span class="sxs-lookup"><span data-stu-id="de772-180">**IncludeTypeInformation** can be used to include the **#TYPE** information and emulate the default behavior of `ConvertTo-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="de772-181">當您將多個物件提交至時 `ConvertTo-CSV` ，會 `ConvertTo-CSV` 根據您提交的第一個物件的屬性來排序字串。</span><span class="sxs-lookup"><span data-stu-id="de772-181">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="de772-182">如果其餘的物件沒有其中一個指定的屬性，則該物件的屬性值會是 Null，以兩個連續的逗號表示。</span><span class="sxs-lookup"><span data-stu-id="de772-182">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="de772-183">如果其餘的物件有其他屬性，則會忽略那些屬性值。</span><span class="sxs-lookup"><span data-stu-id="de772-183">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="de772-184">相關連結</span><span class="sxs-lookup"><span data-stu-id="de772-184">RELATED LINKS</span></span>

[<span data-ttu-id="de772-185">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="de772-185">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="de772-186">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="de772-186">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="de772-187">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="de772-187">Import-Csv</span></span>](Import-Csv.md)