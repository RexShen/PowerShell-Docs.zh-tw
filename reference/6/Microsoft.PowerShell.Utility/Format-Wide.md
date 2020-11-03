---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: 820835065e73cdabb07e47b238041d0b8e375d2f
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205963"
---
# <span data-ttu-id="bf7ca-103">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="bf7ca-103">Format-Wide</span></span>

## <span data-ttu-id="bf7ca-104">概要</span><span class="sxs-lookup"><span data-stu-id="bf7ca-104">SYNOPSIS</span></span>
<span data-ttu-id="bf7ca-105">將物件以每個物件只顯示一個屬性的寬型表格方式格式化。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-105">Formats objects as a wide table that displays only one property of each object.</span></span>

## <span data-ttu-id="bf7ca-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bf7ca-106">SYNTAX</span></span>

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## <span data-ttu-id="bf7ca-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bf7ca-107">DESCRIPTION</span></span>

<span data-ttu-id="bf7ca-108">`Format-Wide`Cmdlet 會將物件格式化為寬型資料表，只顯示每個物件的一個屬性。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-108">The `Format-Wide` cmdlet formats objects as a wide table that displays only one property of each object.</span></span> <span data-ttu-id="bf7ca-109">您可以使用 **property** 參數來決定要顯示哪一個屬性。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-109">You can use the **Property** parameter to determine which property is displayed.</span></span>

## <span data-ttu-id="bf7ca-110">範例</span><span class="sxs-lookup"><span data-stu-id="bf7ca-110">EXAMPLES</span></span>

### <span data-ttu-id="bf7ca-111">範例1：在目前的目錄中格式化檔案的名稱</span><span class="sxs-lookup"><span data-stu-id="bf7ca-111">Example 1: Format names of files in the current directory</span></span>

<span data-ttu-id="bf7ca-112">這個命令會在螢幕上以三欄顯示目前目錄中檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-112">This command displays the names of files in the current directory in three columns across the screen.</span></span>

```powershell
Get-ChildItem | Format-Wide -Column 3
```

<span data-ttu-id="bf7ca-113">Get-ChildItem Cmdlet 會取得代表目錄中每個檔案的物件。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-113">The Get-ChildItem cmdlet gets objects representing each file in the directory.</span></span> <span data-ttu-id="bf7ca-114">管線運算子 (|) 透過管線將檔案物件傳遞給，以將 `Format-Wide` 它們格式化以進行輸出。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-114">The pipeline operator (|) passes the file objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="bf7ca-115">**Column** 參數會指定資料行的數目。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-115">The **Column** parameter specifies the number of columns.</span></span>

### <span data-ttu-id="bf7ca-116">範例2：登錄機碼的格式名稱</span><span class="sxs-lookup"><span data-stu-id="bf7ca-116">Example 2: Format names of registry keys</span></span>

<span data-ttu-id="bf7ca-117">這個命令會顯示 HKEY_CURRENT_USER\Software\Microsoft 機碼中登錄機碼的名稱。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-117">This command displays the names of registry keys in the HKEY_CURRENT_USER\Software\Microsoft key.</span></span>

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

<span data-ttu-id="bf7ca-118">Get-ChildItem Cmdlet 會取得代表機碼的物件。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-118">The Get-ChildItem cmdlet gets objects representing the keys.</span></span> <span data-ttu-id="bf7ca-119">路徑會指定為 HKCU：、PowerShell 登錄提供者所公開的其中一個磁片磁碟機，後面接著機碼路徑。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-119">The path is specified as HKCU:, one of the drives exposed by the PowerShell Registry provider, followed by the key path.</span></span> <span data-ttu-id="bf7ca-120">管線運算子 (|) 透過管線將登錄機碼物件傳遞給 `Format-Wide` ，以將它們格式化以進行輸出。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-120">The pipeline operator (|) passes the registry key objects through the pipeline to `Format-Wide`, which formats them for output.</span></span> <span data-ttu-id="bf7ca-121">**Property** 參數會指定屬性的名稱，而 **AutoSize** 參數則會調整資料行的可讀性。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-121">The **Property** parameter specifies the name of the property, and the **AutoSize** parameter adjusts the columns for readability.</span></span>

### <span data-ttu-id="bf7ca-122">範例3：針對格式錯誤進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="bf7ca-122">Example 3: Troubleshooting format errors</span></span>

<span data-ttu-id="bf7ca-123">下列範例顯示使用運算式新增 **DisplayError** 或 **ShowError** 參數的結果。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-123">The following examples show of the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## <span data-ttu-id="bf7ca-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bf7ca-124">PARAMETERS</span></span>

### <span data-ttu-id="bf7ca-125">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="bf7ca-125">-AutoSize</span></span>

<span data-ttu-id="bf7ca-126">根據資料的寬度調整欄大小和欄數。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-126">Adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="bf7ca-127">根據預設，欄大小和欄數是由檢視決定。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-127">By default, the column size and number are determined by the view.</span></span> <span data-ttu-id="bf7ca-128">您無法在同一個命令中使用 **AutoSize** 與 **Column** 參數。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-128">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

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

### <span data-ttu-id="bf7ca-129">-Column</span><span class="sxs-lookup"><span data-stu-id="bf7ca-129">-Column</span></span>

<span data-ttu-id="bf7ca-130">指定畫面上顯示的欄數。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-130">Specifies the number of columns in the display.</span></span> <span data-ttu-id="bf7ca-131">您無法在同一個命令中使用 **AutoSize** 與 **Column** 參數。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-131">You cannot use the **AutoSize** and **Column** parameters in the same command.</span></span>

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

### <span data-ttu-id="bf7ca-132">-DisplayError</span><span class="sxs-lookup"><span data-stu-id="bf7ca-132">-DisplayError</span></span>

<span data-ttu-id="bf7ca-133">在命令列中顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-133">Displays errors at the command line.</span></span> <span data-ttu-id="bf7ca-134">這個參數很少使用，但是當您在命令中將運算式格式化 `Format-Wide` ，而這些運算式似乎沒有作用時，便可以使用這個參數做為偵錯工具的協助工具。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-134">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="bf7ca-135">-Expand</span><span class="sxs-lookup"><span data-stu-id="bf7ca-135">-Expand</span></span>

<span data-ttu-id="bf7ca-136">將集合物件以及集合中的物件格式化。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-136">Formats the collection object, as well as the objects in the collection.</span></span> <span data-ttu-id="bf7ca-137">這個參數是設計來將支援 ICollection (System.Collections) 介面的物件格式化。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-137">This parameter is designed to format objects that support the ICollection (System.Collections) interface.</span></span> <span data-ttu-id="bf7ca-138">預設值為 **EnumOnly** 。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-138">The default value is **EnumOnly** .</span></span>

<span data-ttu-id="bf7ca-139">有效值為：</span><span class="sxs-lookup"><span data-stu-id="bf7ca-139">Valid values are:</span></span>

- <span data-ttu-id="bf7ca-140">EnumOnly：顯示集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-140">EnumOnly: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="bf7ca-141">CoreOnly：顯示集合物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-141">CoreOnly: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="bf7ca-142">Both：顯示集合物件的屬性及集合中物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-142">Both: Displays the properties of the collection object and the properties of objects in the collection.</span></span>

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

### <span data-ttu-id="bf7ca-143">-Force</span><span class="sxs-lookup"><span data-stu-id="bf7ca-143">-Force</span></span>

<span data-ttu-id="bf7ca-144">指出此 Cmdlet 會覆寫導致命令無法成功的限制，因為變更不會危及安全性。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-144">Indicates that this cmdlet overrides restrictions that prevent the command from succeeding, just so the changes do not compromise security.</span></span> <span data-ttu-id="bf7ca-145">例如， **Force** 會覆寫唯讀屬性或建立目錄來完成檔案路徑，但不會嘗試變更檔案權限。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-145">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="bf7ca-146">-GroupBy</span><span class="sxs-lookup"><span data-stu-id="bf7ca-146">-GroupBy</span></span>

<span data-ttu-id="bf7ca-147">根據共用屬性或值將輸出分組格式化。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-147">Formats the output in groups based on a shared property or value.</span></span> <span data-ttu-id="bf7ca-148">輸入輸出的運算式或屬性。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-148">Enter an expression or a property of the output.</span></span>

<span data-ttu-id="bf7ca-149">**GroupBy** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-149">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="bf7ca-150">計算的屬性可以是腳本區塊或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-150">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="bf7ca-151">有效的索引鍵/值組為：</span><span class="sxs-lookup"><span data-stu-id="bf7ca-151">Valid key-value pairs are:</span></span>

- <span data-ttu-id="bf7ca-152">名稱 (或標籤) - `<string>`</span><span class="sxs-lookup"><span data-stu-id="bf7ca-152">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="bf7ca-153">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="bf7ca-153">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="bf7ca-154">字串 `<string>`</span><span class="sxs-lookup"><span data-stu-id="bf7ca-154">FormatString - `<string>`</span></span>

<span data-ttu-id="bf7ca-155">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-155">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="bf7ca-156">-InputObject</span><span class="sxs-lookup"><span data-stu-id="bf7ca-156">-InputObject</span></span>

<span data-ttu-id="bf7ca-157">指定要格式化的物件。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-157">Specifies the objects to format.</span></span> <span data-ttu-id="bf7ca-158">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-158">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="bf7ca-159">-Property</span><span class="sxs-lookup"><span data-stu-id="bf7ca-159">-Property</span></span>

<span data-ttu-id="bf7ca-160">指定顯示中出現的物件屬性及其出現順序。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-160">Specifies the object properties that appear in the display and the order in which they appear.</span></span>
<span data-ttu-id="bf7ca-161">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-161">Wildcards are permitted.</span></span>

<span data-ttu-id="bf7ca-162">如果省略這個參數，則出現在顯示中的屬性將取決於所顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-162">If you omit this parameter, the properties that appear in the display depend on the object being displayed.</span></span> <span data-ttu-id="bf7ca-163">參數名稱 "Property" 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-163">The parameter name "Property" is optional.</span></span> <span data-ttu-id="bf7ca-164">您無法在相同的命令中使用 **Property** 與 **View** 參數。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-164">You cannot use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="bf7ca-165">**Property** 參數的值可以是新的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-165">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="bf7ca-166">計算的屬性可以是腳本區塊或雜湊表。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-166">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="bf7ca-167">有效的索引鍵/值組為：</span><span class="sxs-lookup"><span data-stu-id="bf7ca-167">Valid key-value pairs are:</span></span>

- <span data-ttu-id="bf7ca-168">運算式 `<string>` 或 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="bf7ca-168">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="bf7ca-169">字串 `<string>`</span><span class="sxs-lookup"><span data-stu-id="bf7ca-169">FormatString - `<string>`</span></span>

<span data-ttu-id="bf7ca-170">如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-170">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bf7ca-171">-ShowError</span><span class="sxs-lookup"><span data-stu-id="bf7ca-171">-ShowError</span></span>

<span data-ttu-id="bf7ca-172">透過管線傳送錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-172">Sends errors through the pipeline.</span></span> <span data-ttu-id="bf7ca-173">這個參數很少使用，但是當您在命令中將運算式格式化 `Format-Wide` ，而這些運算式似乎沒有作用時，便可以使用這個參數做為偵錯工具的協助工具。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-173">This parameter is rarely used, but can be used as a debugging aid when you are formatting expressions in a `Format-Wide` command, and the expressions do not appear to be working.</span></span>

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

### <span data-ttu-id="bf7ca-174">-View</span><span class="sxs-lookup"><span data-stu-id="bf7ca-174">-View</span></span>

<span data-ttu-id="bf7ca-175">指定替代資料表格式或視圖的名稱。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-175">Specifies the name of an alternate table format or view.</span></span> <span data-ttu-id="bf7ca-176">您無法在相同的命令中使用 **Property** 與 **View** 參數。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-176">You cannot use the **Property** and **View** parameters in the same command.</span></span>

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

### <span data-ttu-id="bf7ca-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bf7ca-177">CommonParameters</span></span>

<span data-ttu-id="bf7ca-178">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bf7ca-179">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bf7ca-180">輸入</span><span class="sxs-lookup"><span data-stu-id="bf7ca-180">INPUTS</span></span>

### <span data-ttu-id="bf7ca-181">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="bf7ca-181">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="bf7ca-182">您可以透過管線將任何物件傳送至 `Format-Wide` 。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-182">You can pipe any object to `Format-Wide`.</span></span>

## <span data-ttu-id="bf7ca-183">輸出</span><span class="sxs-lookup"><span data-stu-id="bf7ca-183">OUTPUTS</span></span>

### <span data-ttu-id="bf7ca-184">Microsoft.PowerShell.Commands.Internal.Format</span><span class="sxs-lookup"><span data-stu-id="bf7ca-184">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="bf7ca-185">`Format-Wide` 傳回代表資料表的格式物件。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-185">`Format-Wide` returns format objects that represent the table.</span></span>

## <span data-ttu-id="bf7ca-186">注意</span><span class="sxs-lookup"><span data-stu-id="bf7ca-186">NOTES</span></span>

<span data-ttu-id="bf7ca-187">您也可以 `Format-Wide` 使用內建的別名來參考 `fw` 。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-187">You can also refer to `Format-Wide` by its built-in alias, `fw`.</span></span> <span data-ttu-id="bf7ca-188">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-188">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="bf7ca-189">**GroupBy** 參數假設物件已排序。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-189">The **GroupBy** parameter assumes that the objects are sorted.</span></span> <span data-ttu-id="bf7ca-190">使用 `Sort-Object` 之前，請先使用 `Format-Custom` 來將物件分組。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-190">Use `Sort-Object` before using `Format-Custom` to group the objects.</span></span>

<span data-ttu-id="bf7ca-191">**View** 參數可讓您指定表格的替代格式。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-191">The **View** parameter lets you specify an alternate format for the table.</span></span> <span data-ttu-id="bf7ca-192">您可以使用 PowerShell 目錄的檔案中所定義的視圖，也 `*.format.PS1XML` 可以在新的 .ps1xml 檔案中建立自己的視圖，並使用 `Update-FormatData` Cmdlet 將它們包含在 powershell 中。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-192">You can use the views defined in the `*.format.PS1XML` files in the PowerShell directory or you can create your own views in new PS1XML files and use the `Update-FormatData` cmdlet to include them in PowerShell.</span></span>

<span data-ttu-id="bf7ca-193">**View** 參數的替代視圖必須使用表格格式;如果沒有，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-193">The alternate view for the **View** parameter must use table format; if it does not, the command fails.</span></span> <span data-ttu-id="bf7ca-194">如果替代視圖是清單，請使用 `Format-List` 。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-194">If the alternate view is a list, use `Format-List`.</span></span> <span data-ttu-id="bf7ca-195">如果替代檢視既非清單也非表格，請使用 Format-Custom。</span><span class="sxs-lookup"><span data-stu-id="bf7ca-195">If the alternate view is neither a list nor a table, use Format-Custom.</span></span>

## <span data-ttu-id="bf7ca-196">相關連結</span><span class="sxs-lookup"><span data-stu-id="bf7ca-196">RELATED LINKS</span></span>

[<span data-ttu-id="bf7ca-197">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="bf7ca-197">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="bf7ca-198">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="bf7ca-198">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="bf7ca-199">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="bf7ca-199">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="bf7ca-200">Format-List</span><span class="sxs-lookup"><span data-stu-id="bf7ca-200">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="bf7ca-201">Format-Table</span><span class="sxs-lookup"><span data-stu-id="bf7ca-201">Format-Table</span></span>](Format-Table.md)
