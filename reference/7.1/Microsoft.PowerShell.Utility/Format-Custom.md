---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: c8bf4dfa9077af04e4122672a15a7c768cb49ea2
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205916"
---
# <span data-ttu-id="2e657-103">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="2e657-103">Format-Custom</span></span>

## <span data-ttu-id="2e657-104">概要</span><span class="sxs-lookup"><span data-stu-id="2e657-104">SYNOPSIS</span></span>
<span data-ttu-id="2e657-105">使用自訂檢視來格式化輸出。</span><span class="sxs-lookup"><span data-stu-id="2e657-105">Uses a customized view to format the output.</span></span>

## <span data-ttu-id="2e657-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2e657-106">SYNTAX</span></span>

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## <span data-ttu-id="2e657-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2e657-107">DESCRIPTION</span></span>

<span data-ttu-id="2e657-108">`Format-Custom`Cmdlet 會格式化命令的輸出，如替代視圖中所定義。</span><span class="sxs-lookup"><span data-stu-id="2e657-108">The `Format-Custom` cmdlet formats the output of a command as defined in an alternate view.</span></span>
<span data-ttu-id="2e657-109">`Format-Custom` 的設計目的是要顯示不只是資料表或只是清單的視圖。</span><span class="sxs-lookup"><span data-stu-id="2e657-109">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="2e657-110">您可以使用 PowerShell 中定義的視圖，也可以在新的檔案中建立自己的視圖， `format.ps1xml` 並使用 `Update-FormatData` Cmdlet 將它們新增至 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2e657-110">You can use the views defined in PowerShell, or you can create your own views in a new `format.ps1xml` file and use the `Update-FormatData` cmdlet to add them to PowerShell.</span></span>

## <span data-ttu-id="2e657-111">範例</span><span class="sxs-lookup"><span data-stu-id="2e657-111">EXAMPLES</span></span>

### <span data-ttu-id="2e657-112">範例1：使用自訂視圖格式化輸出</span><span class="sxs-lookup"><span data-stu-id="2e657-112">Example 1: Format output with a custom view</span></span>

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

<span data-ttu-id="2e657-113">此命令會 `Start-Transcript` 以 MyView view （由使用者建立的自訂視圖）所定義的格式來格式化 Cmdlet 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2e657-113">This command formats information about the `Start-Transcript` cmdlet in the format defined by the MyView view, a custom view created by the user.</span></span> <span data-ttu-id="2e657-114">若要成功執行此命令，您必須先建立新的 .PS1XML 檔案、定義 **MyView** 視圖，然後使用 `Update-FormatData` 命令將 .ps1xml 檔案新增至 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2e657-114">To run this command successfully, you must first create a new PS1XML file, define the **MyView** view, and then use the `Update-FormatData` command to add the PS1XML file to PowerShell.</span></span>

### <span data-ttu-id="2e657-115">範例2：使用預設 view 格式化輸出</span><span class="sxs-lookup"><span data-stu-id="2e657-115">Example 2: Format output with the default view</span></span>

```powershell
Get-Process Winlogon | Format-Custom
```

<span data-ttu-id="2e657-116">此命令會在替代自訂視圖中格式化 **Winlogon** 處理常式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2e657-116">This command formats information about the **Winlogon** process in an alternate customized view.</span></span>
<span data-ttu-id="2e657-117">因為命令不使用 **View** 參數，所以會 `Format-Custom` 使用預設的自訂視圖來格式化資料。</span><span class="sxs-lookup"><span data-stu-id="2e657-117">Because the command does not use the **View** parameter, `Format-Custom` uses a default custom view to format the data.</span></span>

### <span data-ttu-id="2e657-118">範例3：針對格式錯誤進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="2e657-118">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="2e657-119">下列範例顯示使用運算式新增 **DisplayError** 或 **ShowError** 參數的結果。</span><span class="sxs-lookup"><span data-stu-id="2e657-119">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -DisplayError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  = #ERR
}


PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -ShowError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  =
}

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:01:04 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="2e657-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2e657-120">PARAMETERS</span></span>

### <span data-ttu-id="2e657-121">-Depth</span><span class="sxs-lookup"><span data-stu-id="2e657-121">-Depth</span></span>

<span data-ttu-id="2e657-122">指定畫面上顯示的欄數。</span><span class="sxs-lookup"><span data-stu-id="2e657-122">Specifies the number of columns in the display.</span></span>

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

### <span data-ttu-id="2e657-123">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="2e657-123">-DisplayError</span></span>

<span data-ttu-id="2e657-124">在命令列中顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="2e657-124">Displays errors at the command line.</span></span> <span data-ttu-id="2e657-125">這個參數很少使用，但是當您在命令中將運算式格式化 `Format-Custom` ，而這些運算式似乎沒有作用時，便可以使用這個參數做為偵錯工具的協助工具。</span><span class="sxs-lookup"><span data-stu-id="2e657-125">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e657-126">-Expand</span><span class="sxs-lookup"><span data-stu-id="2e657-126">-Expand</span></span>

<span data-ttu-id="2e657-127">將集合物件以及集合中的物件格式化。</span><span class="sxs-lookup"><span data-stu-id="2e657-127">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="2e657-128">這個參數是設計來格式化支援 **system.object** 介面的物件。</span><span class="sxs-lookup"><span data-stu-id="2e657-128">This parameter is designed to format objects that support the **System.Collections.ICollection** interface.</span></span> <span data-ttu-id="2e657-129">預設值為 **EnumOnly** 。</span><span class="sxs-lookup"><span data-stu-id="2e657-129">The default value is **EnumOnly** .</span></span>

<span data-ttu-id="2e657-130">有效值為：</span><span class="sxs-lookup"><span data-stu-id="2e657-130">Valid values are:</span></span>

- <span data-ttu-id="2e657-131">EnumOnly：顯示集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="2e657-131">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="2e657-132">CoreOnly：顯示集合物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="2e657-132">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="2e657-133">Both：顯示集合物件的屬性和集合中的物件。</span><span class="sxs-lookup"><span data-stu-id="2e657-133">Both: Displays the properties of the collection object and the objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e657-134">-Force</span><span class="sxs-lookup"><span data-stu-id="2e657-134">-Force</span></span>

<span data-ttu-id="2e657-135">指示 Cmdlet 顯示所有錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="2e657-135">Directs the cmdlet to display all of the error information.</span></span> <span data-ttu-id="2e657-136">搭配 **DisplayError** 或 **ShowError** 參數使用。</span><span class="sxs-lookup"><span data-stu-id="2e657-136">Use with the **DisplayError** or **ShowError** parameters.</span></span> <span data-ttu-id="2e657-137">根據預設，將錯誤物件寫入錯誤或顯示串流時，只會顯示某些錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="2e657-137">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e657-138">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="2e657-138">-GroupBy</span></span>

<span data-ttu-id="2e657-139">根據共用屬性或值將輸出分組格式化。</span><span class="sxs-lookup"><span data-stu-id="2e657-139">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="2e657-140">輸入輸出的運算式或屬性。</span><span class="sxs-lookup"><span data-stu-id="2e657-140">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="2e657-141">**GroupBy** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="2e657-141">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="2e657-142">計算的屬性可以是腳本區塊或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="2e657-142">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="2e657-143">有效的索引鍵/值組為：</span><span class="sxs-lookup"><span data-stu-id="2e657-143">Valid key-value pairs are:</span></span>

- <span data-ttu-id="2e657-144">名稱 (或標籤) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="2e657-144">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="2e657-145">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="2e657-145">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="2e657-146">字串 `<string>`</span><span class="sxs-lookup"><span data-stu-id="2e657-146">FormatString - `<string>`</span></span>

<span data-ttu-id="2e657-147">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2e657-147">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e657-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2e657-148">-InputObject</span></span>

<span data-ttu-id="2e657-149">指定要格式化的物件。</span><span class="sxs-lookup"><span data-stu-id="2e657-149">Specifies the objects to be formatted.</span></span> <span data-ttu-id="2e657-150">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="2e657-150">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2e657-151">-Property</span><span class="sxs-lookup"><span data-stu-id="2e657-151">-Property</span></span>

<span data-ttu-id="2e657-152">指定顯示中出現的物件屬性及其出現順序。</span><span class="sxs-lookup"><span data-stu-id="2e657-152">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="2e657-153">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2e657-153">Wildcards are permitted.</span></span>

<span data-ttu-id="2e657-154">如果省略這個參數，則出現在顯示中的屬性將取決於所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="2e657-154">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="2e657-155">[參數名稱] **屬性** 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="2e657-155">The parameter name **Property** is optional.</span></span> <span data-ttu-id="2e657-156">您無法在相同的命令中使用 **Property** 與 **View** 參數。</span><span class="sxs-lookup"><span data-stu-id="2e657-156">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="2e657-157">**Property** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="2e657-157">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="2e657-158">計算的屬性可以是腳本區塊或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="2e657-158">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="2e657-159">有效的索引鍵/值組為：</span><span class="sxs-lookup"><span data-stu-id="2e657-159">Valid key-value pairs are:</span></span>

- <span data-ttu-id="2e657-160">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="2e657-160">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="2e657-161">解析度 `<int32>`</span><span class="sxs-lookup"><span data-stu-id="2e657-161">Depth - `<int32>`</span></span>

<span data-ttu-id="2e657-162">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="2e657-162">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2e657-163">-ShowError</span><span class="sxs-lookup"><span data-stu-id="2e657-163">-ShowError</span></span>

<span data-ttu-id="2e657-164">透過管線傳送錯誤。</span><span class="sxs-lookup"><span data-stu-id="2e657-164">Sends errors through the pipeline.</span></span> <span data-ttu-id="2e657-165">這個參數很少使用，但是當您在命令中將運算式格式化 `Format-Custom` ，而這些運算式似乎沒有作用時，便可以使用這個參數做為偵錯工具的協助工具。</span><span class="sxs-lookup"><span data-stu-id="2e657-165">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Custom` command, and the expressions do not appear to be working.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e657-166">-View</span><span class="sxs-lookup"><span data-stu-id="2e657-166">-View</span></span>

<span data-ttu-id="2e657-167">指定替代格式或視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="2e657-167">Specifies the name of an alternate format or view.</span></span> <span data-ttu-id="2e657-168">如果您省略此參數，則會 `Format-Custom` 使用預設的自訂視圖。</span><span class="sxs-lookup"><span data-stu-id="2e657-168">If you omit this parameter, `Format-Custom` uses a default custom view.</span></span> <span data-ttu-id="2e657-169">您無法在相同的命令中使用 **Property** 與 **View** 參數。</span><span class="sxs-lookup"><span data-stu-id="2e657-169">You cannot use the **Property** and **View** parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e657-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2e657-170">CommonParameters</span></span>

<span data-ttu-id="2e657-171">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2e657-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2e657-172">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2e657-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2e657-173">輸入</span><span class="sxs-lookup"><span data-stu-id="2e657-173">INPUTS</span></span>

### <span data-ttu-id="2e657-174">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="2e657-174">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="2e657-175">您可以透過管線將任何物件傳送至 `Format-Custom` 。</span><span class="sxs-lookup"><span data-stu-id="2e657-175">You can pipe any object to `Format-Custom`.</span></span>

## <span data-ttu-id="2e657-176">輸出</span><span class="sxs-lookup"><span data-stu-id="2e657-176">OUTPUTS</span></span>

### <span data-ttu-id="2e657-177">Microsoft.PowerShell.Commands.Internal.Format</span><span class="sxs-lookup"><span data-stu-id="2e657-177">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="2e657-178">`Format-Custom` 傳回代表顯示的格式物件。</span><span class="sxs-lookup"><span data-stu-id="2e657-178">`Format-Custom` returns the format objects that represent the display.</span></span>

## <span data-ttu-id="2e657-179">注意</span><span class="sxs-lookup"><span data-stu-id="2e657-179">NOTES</span></span>

<span data-ttu-id="2e657-180">`Format-Custom` 的設計目的是要顯示不只是資料表或只是清單的視圖。</span><span class="sxs-lookup"><span data-stu-id="2e657-180">`Format-Custom` is designed to display views that are not just tables or just lists.</span></span> <span data-ttu-id="2e657-181">若要顯示替代資料表視圖，請使用 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="2e657-181">To display an alternate table view, use `Format-Table`.</span></span> <span data-ttu-id="2e657-182">若要顯示替代清單視圖，請使用 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="2e657-182">To display an alternate list view, use `Format-List`.</span></span>

<span data-ttu-id="2e657-183">您也可以 `Format-Custom` 使用內建的別名來參考 `fc` 。</span><span class="sxs-lookup"><span data-stu-id="2e657-183">You can also refer to `Format-Custom` by its built-in alias, `fc`.</span></span> <span data-ttu-id="2e657-184">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="2e657-184">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="2e657-185">**GroupBy** 參數假設物件已排序。</span><span class="sxs-lookup"><span data-stu-id="2e657-185">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="2e657-186">使用 `Format-Custom` 來群組物件之前，請使用 `Sort-Object` 來排序物件。</span><span class="sxs-lookup"><span data-stu-id="2e657-186">Before using `Format-Custom` to group the objects, use `Sort-Object` to sort them.</span></span>

## <span data-ttu-id="2e657-187">相關連結</span><span class="sxs-lookup"><span data-stu-id="2e657-187">RELATED LINKS</span></span>

[<span data-ttu-id="2e657-188">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="2e657-188">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="2e657-189">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="2e657-189">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="2e657-190">Format-List</span><span class="sxs-lookup"><span data-stu-id="2e657-190">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="2e657-191">Format-Table</span><span class="sxs-lookup"><span data-stu-id="2e657-191">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="2e657-192">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="2e657-192">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="2e657-193">Get-Process</span><span class="sxs-lookup"><span data-stu-id="2e657-193">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
