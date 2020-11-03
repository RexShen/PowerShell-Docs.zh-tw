---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: a025432e8aed93f6668c676161c21377d0ba225c
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93206023"
---
# <span data-ttu-id="9832e-103">Format-List</span><span class="sxs-lookup"><span data-stu-id="9832e-103">Format-List</span></span>

## <span data-ttu-id="9832e-104">概要</span><span class="sxs-lookup"><span data-stu-id="9832e-104">SYNOPSIS</span></span>
<span data-ttu-id="9832e-105">將輸出格式化為屬性清單，其中每個屬性會顯示在新的一行上。</span><span class="sxs-lookup"><span data-stu-id="9832e-105">Formats the output as a list of properties in which each property appears on a new line.</span></span>

## <span data-ttu-id="9832e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9832e-106">SYNTAX</span></span>

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## <span data-ttu-id="9832e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9832e-107">DESCRIPTION</span></span>

<span data-ttu-id="9832e-108">`Format-List`Cmdlet 會將命令的輸出格式化為屬性清單，其中每個屬性都會顯示在個別的行上。</span><span class="sxs-lookup"><span data-stu-id="9832e-108">The `Format-List` cmdlet formats the output of a command as a list of properties in which each property is displayed on a separate line.</span></span> <span data-ttu-id="9832e-109">您可以使用 `Format-List` ，將物件的所有或選取屬性格式化並顯示為清單 (格式清單 \* ) 。</span><span class="sxs-lookup"><span data-stu-id="9832e-109">You can use `Format-List` to format and display all or selected properties of an object as a list (format-list \*).</span></span>

<span data-ttu-id="9832e-110">由於清單中的每個專案都有更多可用空間，而不是在資料表中，因此 PowerShell 會在清單中顯示更多物件屬性，且屬性值較不可能被截斷。</span><span class="sxs-lookup"><span data-stu-id="9832e-110">Because more space is available for each item in a list than in a table, PowerShell displays more properties of the object in the list, and the property values are less likely to be truncated.</span></span>

## <span data-ttu-id="9832e-111">範例</span><span class="sxs-lookup"><span data-stu-id="9832e-111">EXAMPLES</span></span>

### <span data-ttu-id="9832e-112">範例1：格式化電腦服務</span><span class="sxs-lookup"><span data-stu-id="9832e-112">Example 1: Format computer services</span></span>

```powershell
Get-Service | Format-List
```

<span data-ttu-id="9832e-113">此命令將電腦上關於服務的資訊格式化為清單。</span><span class="sxs-lookup"><span data-stu-id="9832e-113">This command formats information about services on the computer as a list.</span></span> <span data-ttu-id="9832e-114">根據預設，服務會格式化為表格。</span><span class="sxs-lookup"><span data-stu-id="9832e-114">By default, the services are formatted as a table.</span></span> <span data-ttu-id="9832e-115">`Get-Service`Cmdlet 會取得代表電腦上之服務的物件。</span><span class="sxs-lookup"><span data-stu-id="9832e-115">The `Get-Service` cmdlet gets objects representing the services on the computer.</span></span> <span data-ttu-id="9832e-116">管線運算子 (|) 透過管線將結果傳遞給 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="9832e-116">The pipeline operator (|) passes the results through the pipeline to `Format-List`.</span></span>
<span data-ttu-id="9832e-117">然後，此 `Format-List` 命令會格式化清單中的服務資訊，並將其傳送至預設的輸出 Cmdlet 以供顯示。</span><span class="sxs-lookup"><span data-stu-id="9832e-117">Then, the `Format-List` command formats the service information in a list and sends it to the default output cmdlet for display.</span></span>

### <span data-ttu-id="9832e-118">範例2：格式化 .PS1XML 檔案</span><span class="sxs-lookup"><span data-stu-id="9832e-118">Example 2: Format PS1XML files</span></span>

<span data-ttu-id="9832e-119">這些命令會以清單形式顯示 PowerShell 目錄中 .PS1XML 檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9832e-119">These commands display information about the PS1XML files in the PowerShell directory as a list.</span></span>

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

<span data-ttu-id="9832e-120">第一個命令會取得代表檔案的物件，並將它們儲存在 `$A` 變數中。</span><span class="sxs-lookup"><span data-stu-id="9832e-120">The first command gets the objects representing the files and stores them in the `$A` variable.</span></span>

<span data-ttu-id="9832e-121">第二個命令會使用 `Format-List` 來格式化中所儲存之物件的相關資訊 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="9832e-121">The second command uses `Format-List` to format information about objects stored in `$A`.</span></span> <span data-ttu-id="9832e-122">此命令會使用 **InputObject** 參數將變數傳遞給 `Format-List` ，然後將格式化的輸出傳送至預設的 output Cmdlet 以供顯示。</span><span class="sxs-lookup"><span data-stu-id="9832e-122">This command uses the **InputObject** parameter to pass the variable to `Format-List`, which then sends the formatted output to the default output cmdlet for display.</span></span>

### <span data-ttu-id="9832e-123">範例3：依名稱格式化進程屬性</span><span class="sxs-lookup"><span data-stu-id="9832e-123">Example 3: Format process properties by name</span></span>

<span data-ttu-id="9832e-124">此命令顯示電腦上每個處理程序的名稱、基本優先順序和優先順序類別。</span><span class="sxs-lookup"><span data-stu-id="9832e-124">This command displays the name, base priority, and priority class of each process on the computer.</span></span>

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

<span data-ttu-id="9832e-125">它會使用 `Get-Process` Cmdlet 來取得代表每個處理常式的物件。</span><span class="sxs-lookup"><span data-stu-id="9832e-125">It uses the `Get-Process` cmdlet to get an object representing each process.</span></span> <span data-ttu-id="9832e-126">管線運算子 (|) 透過管線將處理常式物件傳遞至 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="9832e-126">The pipeline operator (|) passes the process objects through the pipeline to `Format-List`.</span></span> <span data-ttu-id="9832e-127">`Format-List` 將處理常式格式化為指定屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="9832e-127">`Format-List` formats the processes as a list of the specified properties.</span></span> <span data-ttu-id="9832e-128">*屬性* 參數名稱為選擇性，因此您可以省略它。</span><span class="sxs-lookup"><span data-stu-id="9832e-128">The *Property* parameter name is optional, so you can omit it.</span></span>

### <span data-ttu-id="9832e-129">範例4：格式化進程的所有屬性</span><span class="sxs-lookup"><span data-stu-id="9832e-129">Example 4: Format all properties for a process</span></span>

<span data-ttu-id="9832e-130">此命令顯示 Winlogon 處理程序的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="9832e-130">This command displays all of the properties of the Winlogon process.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="9832e-131">它使用 Get-Process Cmdlet 取得代表 Winlogon 處理程序的物件。</span><span class="sxs-lookup"><span data-stu-id="9832e-131">It uses the Get-Process cmdlet to get an object representing the Winlogon process.</span></span> <span data-ttu-id="9832e-132">管線運算子 (|) 透過管線將 Winlogon 處理常式物件傳遞至 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="9832e-132">The pipeline operator (|) passes the Winlogon process object through the pipeline to `Format-List`.</span></span> <span data-ttu-id="9832e-133">命令使用 *Property* 參數指定屬性，並使用 \* 來指出所有屬性。</span><span class="sxs-lookup"><span data-stu-id="9832e-133">The command uses the *Property* parameter to specify the properties and the \* to indicate all properties.</span></span>
<span data-ttu-id="9832e-134">因為 *Property* 參數的名稱是選擇性的，所以您可以省略它，並將命令輸入為 `Format-List *` 。</span><span class="sxs-lookup"><span data-stu-id="9832e-134">Because the name of the *Property* parameter is optional, you can omit it and type the command as `Format-List *`.</span></span> <span data-ttu-id="9832e-135">`Format-List` 自動將結果傳送至預設的輸出 Cmdlet 以供顯示。</span><span class="sxs-lookup"><span data-stu-id="9832e-135">`Format-List` automatically sends the results to the default output cmdlet for display.</span></span>

### <span data-ttu-id="9832e-136">範例5：針對格式錯誤進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="9832e-136">Example 5: Troubleshooting format errors</span></span>

<span data-ttu-id="9832e-137">下列範例顯示使用運算式新增 **DisplayError** 或 **ShowError** 參數的結果。</span><span class="sxs-lookup"><span data-stu-id="9832e-137">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -DisplayError

DayOfWeek    : Friday
 $_ / $null  : #ERR

PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -ShowError

DayOfWeek    : Friday
 $_ / $null  :

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 7:59:23 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="9832e-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9832e-138">PARAMETERS</span></span>

### <span data-ttu-id="9832e-139">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="9832e-139">-DisplayError</span></span>

<span data-ttu-id="9832e-140">指出此 Cmdlet 會在命令列顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="9832e-140">Indicates that this cmdlet displays errors at the command line.</span></span> <span data-ttu-id="9832e-141">這個參數很少使用，但是當您在命令中將運算式格式化 `Format-List` ，而這些運算式似乎沒有作用時，便可以使用這個參數做為偵錯工具的協助工具。</span><span class="sxs-lookup"><span data-stu-id="9832e-141">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="9832e-142">-Expand</span><span class="sxs-lookup"><span data-stu-id="9832e-142">-Expand</span></span>

<span data-ttu-id="9832e-143">指定格式化的集合物件，以及集合中的物件。</span><span class="sxs-lookup"><span data-stu-id="9832e-143">Specifies the formatted collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="9832e-144">這個參數是設計來將支援 ICollection (System.Collections) 介面的物件格式化。</span><span class="sxs-lookup"><span data-stu-id="9832e-144">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="9832e-145">預設值為 EnumOnly。</span><span class="sxs-lookup"><span data-stu-id="9832e-145">The default value is EnumOnly.</span></span> <span data-ttu-id="9832e-146">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="9832e-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9832e-147">EnumOnly.</span><span class="sxs-lookup"><span data-stu-id="9832e-147">EnumOnly.</span></span> <span data-ttu-id="9832e-148">顯示集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="9832e-148">Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="9832e-149">CoreOnly.</span><span class="sxs-lookup"><span data-stu-id="9832e-149">CoreOnly.</span></span> <span data-ttu-id="9832e-150">顯示集合物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="9832e-150">Displays the properties of the collection object.</span></span>
- <span data-ttu-id="9832e-151">兩者。</span><span class="sxs-lookup"><span data-stu-id="9832e-151">Both.</span></span> <span data-ttu-id="9832e-152">顯示集合物件的屬性及集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="9832e-152">Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9832e-153">-Force</span><span class="sxs-lookup"><span data-stu-id="9832e-153">-Force</span></span>

<span data-ttu-id="9832e-154">指出此 Cmdlet 會顯示所有錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="9832e-154">Indicates that this cmdlet displays all of the error information.</span></span> <span data-ttu-id="9832e-155">搭配 **DisplayError** 或 **ShowError** 參數使用。</span><span class="sxs-lookup"><span data-stu-id="9832e-155">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="9832e-156">根據預設，將錯誤物件寫入錯誤或顯示串流時，只會顯示某些錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="9832e-156">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

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

### <span data-ttu-id="9832e-157">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="9832e-157">-GroupBy</span></span>

<span data-ttu-id="9832e-158">根據共用屬性或值，指定群組中的輸出。</span><span class="sxs-lookup"><span data-stu-id="9832e-158">Specifies the output in groups based on a shared property or value.</span></span> <span data-ttu-id="9832e-159">輸入輸出的運算式或屬性。</span><span class="sxs-lookup"><span data-stu-id="9832e-159">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="9832e-160">**GroupBy** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="9832e-160">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="9832e-161">計算的屬性可以是腳本區塊或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="9832e-161">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="9832e-162">有效的索引鍵/值組為：</span><span class="sxs-lookup"><span data-stu-id="9832e-162">Valid key-value pairs are:</span></span>

- <span data-ttu-id="9832e-163">名稱 (或標籤) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="9832e-163">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="9832e-164">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="9832e-164">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="9832e-165">字串 `<string>`</span><span class="sxs-lookup"><span data-stu-id="9832e-165">FormatString - `<string>`</span></span>

<span data-ttu-id="9832e-166">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9832e-166">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="9832e-167">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9832e-167">-InputObject</span></span>

<span data-ttu-id="9832e-168">指定要格式化的物件。</span><span class="sxs-lookup"><span data-stu-id="9832e-168">Specifies the objects to be formatted.</span></span> <span data-ttu-id="9832e-169">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="9832e-169">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="9832e-170">-Property</span><span class="sxs-lookup"><span data-stu-id="9832e-170">-Property</span></span>

<span data-ttu-id="9832e-171">指定顯示中出現的物件屬性及其出現順序。</span><span class="sxs-lookup"><span data-stu-id="9832e-171">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="9832e-172">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9832e-172">Wildcards are permitted.</span></span>

<span data-ttu-id="9832e-173">如果省略這個參數，則出現在顯示中的屬性將取決於所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="9832e-173">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="9832e-174">參數名稱 "Property" 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="9832e-174">The parameter name "Property" is optional.</span></span> <span data-ttu-id="9832e-175">您無法在相同的命令中使用 **Property** 與 **View** 參數。</span><span class="sxs-lookup"><span data-stu-id="9832e-175">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="9832e-176">**Property** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="9832e-176">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="9832e-177">計算的屬性可以是腳本區塊或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="9832e-177">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="9832e-178">有效的索引鍵/值組為：</span><span class="sxs-lookup"><span data-stu-id="9832e-178">Valid key-value pairs are:</span></span>

- <span data-ttu-id="9832e-179">名稱 (或標籤) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="9832e-179">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="9832e-180">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="9832e-180">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="9832e-181">字串 `<string>`</span><span class="sxs-lookup"><span data-stu-id="9832e-181">FormatString - `<string>`</span></span>

<span data-ttu-id="9832e-182">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="9832e-182">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="9832e-183">-ShowError</span><span class="sxs-lookup"><span data-stu-id="9832e-183">-ShowError</span></span>

<span data-ttu-id="9832e-184">指出此 Cmdlet 會透過管線傳送錯誤。</span><span class="sxs-lookup"><span data-stu-id="9832e-184">Indicates that the cmdlet sends errors through the pipeline.</span></span> <span data-ttu-id="9832e-185">這個參數很少使用，但是當您在命令中將運算式格式化 `Format-List` ，而這些運算式似乎沒有作用時，便可以使用這個參數做為偵錯工具的協助工具。</span><span class="sxs-lookup"><span data-stu-id="9832e-185">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-List` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="9832e-186">-View</span><span class="sxs-lookup"><span data-stu-id="9832e-186">-View</span></span>

<span data-ttu-id="9832e-187">指定替代清單格式或視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="9832e-187">Specifies the name of an alternate list format or view.</span></span> <span data-ttu-id="9832e-188">您無法在相同的命令中使用 **Property** 與 **View** 參數。</span><span class="sxs-lookup"><span data-stu-id="9832e-188">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="9832e-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9832e-189">CommonParameters</span></span>

<span data-ttu-id="9832e-190">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9832e-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9832e-191">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9832e-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9832e-192">輸入</span><span class="sxs-lookup"><span data-stu-id="9832e-192">INPUTS</span></span>

### <span data-ttu-id="9832e-193">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="9832e-193">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9832e-194">您可以透過管線將任何物件傳送至 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="9832e-194">You can pipe any object to `Format-List`.</span></span>

## <span data-ttu-id="9832e-195">輸出</span><span class="sxs-lookup"><span data-stu-id="9832e-195">OUTPUTS</span></span>

### <span data-ttu-id="9832e-196">Microsoft.PowerShell.Commands.Internal.Format</span><span class="sxs-lookup"><span data-stu-id="9832e-196">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="9832e-197">`Format-List` 傳回代表清單的格式物件。</span><span class="sxs-lookup"><span data-stu-id="9832e-197">`Format-List` returns the format objects that represent the list.</span></span>

## <span data-ttu-id="9832e-198">注意</span><span class="sxs-lookup"><span data-stu-id="9832e-198">NOTES</span></span>

<span data-ttu-id="9832e-199">您也可以使用內建的別名（FL）來參考 Format-List。</span><span class="sxs-lookup"><span data-stu-id="9832e-199">You can also refer to Format-List by its built-in alias, FL.</span></span> <span data-ttu-id="9832e-200">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="9832e-200">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="9832e-201">格式 Cmdlet （例如 `Format-List` ）會排列要顯示的資料，但不會顯示它。</span><span class="sxs-lookup"><span data-stu-id="9832e-201">The format cmdlets, such as `Format-List`, arrange the data to be displayed but do not display it.</span></span>
<span data-ttu-id="9832e-202">PowerShell 的輸出功能和包含 Out 動詞 (Out Cmdlet 的 Cmdlet 會顯示資料) ，例如 `Out-Host` 或 `Out-File` 。</span><span class="sxs-lookup"><span data-stu-id="9832e-202">The data is displayed by the output features of PowerShell and by the cmdlets that contain the Out verb (the Out cmdlets), such as `Out-Host` or `Out-File`.</span></span>

<span data-ttu-id="9832e-203">如果您未使用 format Cmdlet，則 PowerShell 會針對它所顯示的每個物件套用該預設格式。</span><span class="sxs-lookup"><span data-stu-id="9832e-203">If you do not use a format cmdlet, PowerShell applies that default format for each object that it displays.</span></span>

<span data-ttu-id="9832e-204">**GroupBy** 參數假設物件已排序。</span><span class="sxs-lookup"><span data-stu-id="9832e-204">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="9832e-205">使用 Sort-Object 之前，請先使用 `Format-List` 來將物件分組。</span><span class="sxs-lookup"><span data-stu-id="9832e-205">Use Sort-Object before using `Format-List` to group the objects.</span></span>

<span data-ttu-id="9832e-206">**View** 參數可讓您指定表格的替代格式。</span><span class="sxs-lookup"><span data-stu-id="9832e-206">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="9832e-207">您可以使用 PowerShell 目錄的檔案中所定義的視圖 `*.format.PS1XML` ，也可以在新的 .ps1xml 檔案中建立自己的視圖，並使用 Update-FormatData Cmdlet 將它們包含在 powershell 中。</span><span class="sxs-lookup"><span data-stu-id="9832e-207">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory, or you can create your own views in new PS1XML files and use the Update-FormatData cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="9832e-208">**View** 參數的替代視圖必須使用清單格式，否則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="9832e-208">The alternate view for the **View** parameter must use the list format, otherwise, the command fails.</span></span> <span data-ttu-id="9832e-209">如果替代視圖為數據表，請使用 `Format-Table` 。</span><span class="sxs-lookup"><span data-stu-id="9832e-209">If the alternate view is a table, use `Format-Table`.</span></span> <span data-ttu-id="9832e-210">如果替代視圖不是清單或資料表，請使用 `Format-Custom` 。</span><span class="sxs-lookup"><span data-stu-id="9832e-210">If the alternate view is not a list or a table, use `Format-Custom`.</span></span>

## <span data-ttu-id="9832e-211">相關連結</span><span class="sxs-lookup"><span data-stu-id="9832e-211">RELATED LINKS</span></span>

[<span data-ttu-id="9832e-212">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="9832e-212">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="9832e-213">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="9832e-213">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="9832e-214">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="9832e-214">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="9832e-215">Format-Table</span><span class="sxs-lookup"><span data-stu-id="9832e-215">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="9832e-216">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="9832e-216">Format-Wide</span></span>](Format-Wide.md)
