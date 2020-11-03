---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: 5d4a27f1a1949056ca63b9b6a2340bf1226592e0
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205895"
---
# <span data-ttu-id="0eb02-103">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="0eb02-103">Measure-Object</span></span>

## <span data-ttu-id="0eb02-104">概要</span><span class="sxs-lookup"><span data-stu-id="0eb02-104">SYNOPSIS</span></span>
<span data-ttu-id="0eb02-105">計算物件的數值屬性，以及字串物件 (例如文字檔案) 中的字元數、文字數和行數。</span><span class="sxs-lookup"><span data-stu-id="0eb02-105">Calculates the numeric properties of objects, and the characters, words, and lines in string objects, such as files of text.</span></span>

## <span data-ttu-id="0eb02-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0eb02-106">SYNTAX</span></span>

### <span data-ttu-id="0eb02-107">GenericMeasure (預設值)</span><span class="sxs-lookup"><span data-stu-id="0eb02-107">GenericMeasure (Default)</span></span>

```
Measure-Object [-InputObject <PSObject>] [[-Property] <String[]>] [-Sum] [-Average] [-Maximum] [-Minimum]
 [<CommonParameters>]
```

### <span data-ttu-id="0eb02-108">TextMeasure</span><span class="sxs-lookup"><span data-stu-id="0eb02-108">TextMeasure</span></span>

```
Measure-Object [-InputObject <PSObject>] [[-Property] <String[]>] [-Line] [-Word] [-Character]
 [-IgnoreWhiteSpace] [<CommonParameters>]
```

## <span data-ttu-id="0eb02-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0eb02-109">DESCRIPTION</span></span>

<span data-ttu-id="0eb02-110">`Measure-Object`Cmdlet 會計算特定物件類型的屬性值。</span><span class="sxs-lookup"><span data-stu-id="0eb02-110">The `Measure-Object` cmdlet calculates the property values of certain types of object.</span></span>
<span data-ttu-id="0eb02-111">`Measure-Object` 根據命令中的參數，執行三種類型的度量。</span><span class="sxs-lookup"><span data-stu-id="0eb02-111">`Measure-Object` performs three types of measurements, depending on the parameters in the command.</span></span>

<span data-ttu-id="0eb02-112">此 `Measure-Object` Cmdlet 會在物件的屬性值上執行計算。</span><span class="sxs-lookup"><span data-stu-id="0eb02-112">The `Measure-Object` cmdlet performs calculations on the property values of objects.</span></span> <span data-ttu-id="0eb02-113">您可以使用 `Measure-Object` 來計算物件或計算具有指定 **屬性** 的物件。</span><span class="sxs-lookup"><span data-stu-id="0eb02-113">You can use `Measure-Object` to count objects or count objects with a specified **Property** .</span></span> <span data-ttu-id="0eb02-114">您也可以使用 `Measure-Object` 來計算數值的 **最小** 值、 **最大** 值、 **總和** 、 **list.standarddeviation** 和 **平均值** 。</span><span class="sxs-lookup"><span data-stu-id="0eb02-114">You can also use `Measure-Object` to calculate the **Minimum** , **Maximum** , **Sum** , **StandardDeviation** and **Average** of numeric values.</span></span> <span data-ttu-id="0eb02-115">針對 **字串** 物件，您也可以使用 `Measure-Object` 來計算行數、字組和字元數。</span><span class="sxs-lookup"><span data-stu-id="0eb02-115">For **String** objects, you can also use `Measure-Object` to count the number of lines, words, and characters.</span></span>

## <span data-ttu-id="0eb02-116">範例</span><span class="sxs-lookup"><span data-stu-id="0eb02-116">EXAMPLES</span></span>

### <span data-ttu-id="0eb02-117">範例 1︰計算目錄中的檔案和資料夾數目</span><span class="sxs-lookup"><span data-stu-id="0eb02-117">Example 1: Count the files and folders in a directory</span></span>

<span data-ttu-id="0eb02-118">此命令計算目前目錄中的檔案數目和資料夾數目。</span><span class="sxs-lookup"><span data-stu-id="0eb02-118">This command counts the files and folders in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object
```

### <span data-ttu-id="0eb02-119">範例 2︰測量目錄中的檔案</span><span class="sxs-lookup"><span data-stu-id="0eb02-119">Example 2: Measure the files in a directory</span></span>

<span data-ttu-id="0eb02-120">此命令會顯示目前目錄中所有檔案大小的 **最小值** 、 **最大值** 和 **總和** ，以及目錄中檔案的平均大小。</span><span class="sxs-lookup"><span data-stu-id="0eb02-120">This command displays the **Minimum** , **Maximum** , and **Sum** of the sizes of all files in the current directory, and the average size of a file in the directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### <span data-ttu-id="0eb02-121">範例 3︰測量文字檔中的文字</span><span class="sxs-lookup"><span data-stu-id="0eb02-121">Example 3: Measure text in a text file</span></span>

<span data-ttu-id="0eb02-122">此命令顯示 Text.txt 檔案中的字元數、文字數和行數。</span><span class="sxs-lookup"><span data-stu-id="0eb02-122">This command displays the number of characters, words, and lines in the Text.txt file.</span></span>
<span data-ttu-id="0eb02-123">如果沒有 **Raw** 參數，請將檔案 `Get-Content` 輸出為行的陣列。</span><span class="sxs-lookup"><span data-stu-id="0eb02-123">Without the **Raw** parameter, `Get-Content` outputs the file as an array of lines.</span></span>

<span data-ttu-id="0eb02-124">第一個命令會使用將 `Set-Content` 一些預設文字新增至檔案。</span><span class="sxs-lookup"><span data-stu-id="0eb02-124">The first command uses `Set-Content` to add some default text to a file.</span></span>

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### <span data-ttu-id="0eb02-125">範例4：量值物件包含指定的屬性</span><span class="sxs-lookup"><span data-stu-id="0eb02-125">Example 4: Measure objects containing a specified Property</span></span>

<span data-ttu-id="0eb02-126">此範例會計算具有 **DisplayName** 屬性的物件數目。</span><span class="sxs-lookup"><span data-stu-id="0eb02-126">This example counts the number of objects that have a **DisplayName** property.</span></span> <span data-ttu-id="0eb02-127">前兩個命令會取得本機電腦上的所有服務和進程。</span><span class="sxs-lookup"><span data-stu-id="0eb02-127">The first two commands retrieve all the services and processes on the local machine.</span></span> <span data-ttu-id="0eb02-128">第三個命令會計算服務和進程的組合數目。</span><span class="sxs-lookup"><span data-stu-id="0eb02-128">The third command counts the combined number of services and processes.</span></span> <span data-ttu-id="0eb02-129">最後一個命令會結合兩個集合，並將結果輸送至 `Measure-Object` 。</span><span class="sxs-lookup"><span data-stu-id="0eb02-129">The last command combines the two collections and pipes the result to `Measure-Object`.</span></span>

<span data-ttu-id="0eb02-130">System.servicemodel **物件沒有** **DisplayName** 屬性，而且會保留在最後一個計數中。</span><span class="sxs-lookup"><span data-stu-id="0eb02-130">The **System.Diagnostics.Process** object does not have a **DisplayName** property, and is left out of the final count.</span></span>

```powershell
$services = Get-Service
$processes = Get-Process
$services + $processes | Measure-Object
$services + $processes | Measure-Object -Property DisplayName
```

```Output
Count    : 682
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

Count    : 290
Average  :
Sum      :
Maximum  :
Minimum  :
Property : DisplayName
```

### <span data-ttu-id="0eb02-131">範例 5︰測量 CSV 檔案的內容</span><span class="sxs-lookup"><span data-stu-id="0eb02-131">Example 5: Measure the contents of a CSV file</span></span>

<span data-ttu-id="0eb02-132">此命令計算公司員工的平均服務年資。</span><span class="sxs-lookup"><span data-stu-id="0eb02-132">This command calculates the average years of service of the employees of a company.</span></span>

<span data-ttu-id="0eb02-133">檔案 `ServiceYrs.csv` 是一個 CSV 檔案，其中包含每個員工的員工人數和年度服務。</span><span class="sxs-lookup"><span data-stu-id="0eb02-133">The `ServiceYrs.csv` file is a CSV file that contains the employee number and years of service of each employee.</span></span> <span data-ttu-id="0eb02-134">資料表中的第一個資料列是 **具有 empno** ， **年** 的標頭資料列。</span><span class="sxs-lookup"><span data-stu-id="0eb02-134">The first row in the table is a header row of **EmpNo** , **Years** .</span></span>

<span data-ttu-id="0eb02-135">當您使用匯入檔案時 `Import-Csv` ，結果會是 **PSCustomObject** ，其中包含 **具有 empno** 和 **年** 的附注屬性。</span><span class="sxs-lookup"><span data-stu-id="0eb02-135">When you use `Import-Csv` to import the file, the result is a **PSCustomObject** with note properties of **EmpNo** and **Years** .</span></span>
<span data-ttu-id="0eb02-136">您可以使用 `Measure-Object` 來計算這些屬性的值，就像物件的任何其他屬性一樣。</span><span class="sxs-lookup"><span data-stu-id="0eb02-136">You can use `Measure-Object` to calculate the values of these properties, just like any other property of an object.</span></span>

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### <span data-ttu-id="0eb02-137">範例 6︰測量布林值</span><span class="sxs-lookup"><span data-stu-id="0eb02-137">Example 6: Measure Boolean values</span></span>

<span data-ttu-id="0eb02-138">這個範例會示範如何 `Measure-Object` 測量布林值。</span><span class="sxs-lookup"><span data-stu-id="0eb02-138">This example demonstrates how the `Measure-Object` can measure Boolean values.</span></span>
<span data-ttu-id="0eb02-139">在此情況下，它會使用 **PSIsContainer** **布林** 值屬性來測量目前目錄中) 資料夾 (與檔案的發生情形。</span><span class="sxs-lookup"><span data-stu-id="0eb02-139">In this case, it uses the **PSIsContainer** **Boolean** property to measure the incidence of folders (vs. files) in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property psiscontainer -Maximum -Sum -Minimum -Average
```

```Output
Count             : 126
Average           : 0.0634920634920635
Sum               : 8
Maximum           : 1
Minimum           : 0
StandardDeviation :
Property          : PSIsContainer
```

### <span data-ttu-id="0eb02-140">範例7：量值字串</span><span class="sxs-lookup"><span data-stu-id="0eb02-140">Example 7: Measure strings</span></span>

<span data-ttu-id="0eb02-141">下列範例會測量行數、第一個字串，然後在數個字串之間進行測量。</span><span class="sxs-lookup"><span data-stu-id="0eb02-141">The following example measures the number of lines, first a single string, then across several strings.</span></span> <span data-ttu-id="0eb02-142">換行字元會將 <code>\`n</code> 字串分隔成多行。</span><span class="sxs-lookup"><span data-stu-id="0eb02-142">The newline character <code>\`n</code> separates strings into multiple lines.</span></span>

```powershell
# The newline character `n separates the string into separate lines, as shown in the output.
"One`nTwo`nThree"
"One`nTwo`nThree" | Measure-Object -Line
```

```Output
One
Two
Three


Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The first string counts as a single line.
# The second string is separated into two lines by the newline character.
"One", "Two`nThree" | Measure-Object -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The Word switch counts the number of words in each InputObject
# Each InputObject is treated as a single line.
"One, Two", "Three", "Four Five" | Measure-Object -Word -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3     5
```

## <span data-ttu-id="0eb02-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0eb02-143">PARAMETERS</span></span>

### <span data-ttu-id="0eb02-144">-Average</span><span class="sxs-lookup"><span data-stu-id="0eb02-144">-Average</span></span>

<span data-ttu-id="0eb02-145">指出此 Cmdlet 會顯示指定屬性的平均值。</span><span class="sxs-lookup"><span data-stu-id="0eb02-145">Indicates that the cmdlet displays the average value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eb02-146">-Character</span><span class="sxs-lookup"><span data-stu-id="0eb02-146">-Character</span></span>

<span data-ttu-id="0eb02-147">指出此 Cmdlet 會計算輸入物件中的字元數。</span><span class="sxs-lookup"><span data-stu-id="0eb02-147">Indicates that the cmdlet counts the number of characters in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="0eb02-148">**單字** 、 **Char** 和 **Line** 參數會在每個輸入物件 *內* ，以及輸入物件 *之間* 進行計數。</span><span class="sxs-lookup"><span data-stu-id="0eb02-148">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="0eb02-149">請參閱範例7。</span><span class="sxs-lookup"><span data-stu-id="0eb02-149">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eb02-150">-IgnoreWhiteSpace</span><span class="sxs-lookup"><span data-stu-id="0eb02-150">-IgnoreWhiteSpace</span></span>

<span data-ttu-id="0eb02-151">指出此 Cmdlet 會忽略字元計數中的空白字元。</span><span class="sxs-lookup"><span data-stu-id="0eb02-151">Indicates that the cmdlet ignores white space in character counts.</span></span>
<span data-ttu-id="0eb02-152">根據預設，不會忽略空白字元。</span><span class="sxs-lookup"><span data-stu-id="0eb02-152">By default, white space is not ignored.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eb02-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="0eb02-153">-InputObject</span></span>

<span data-ttu-id="0eb02-154">指定要測量的物件。</span><span class="sxs-lookup"><span data-stu-id="0eb02-154">Specifies the objects to be measured.</span></span>
<span data-ttu-id="0eb02-155">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="0eb02-155">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="0eb02-156">當您搭配使用 **inputobject** 參數與時 `Measure-Object` ，不會將命令結果傳送至，而是 `Measure-Object` 會將 **inputobject** 值視為單一物件。</span><span class="sxs-lookup"><span data-stu-id="0eb02-156">When you use the **InputObject** parameter with `Measure-Object`, instead of piping command results to `Measure-Object`, the **InputObject** value is treated as a single object.</span></span>

<span data-ttu-id="0eb02-157">`Measure-Object`如果您想要根據物件是否在已定義屬性中具有特定值來測量物件集合，建議您在管線中使用。</span><span class="sxs-lookup"><span data-stu-id="0eb02-157">It is recommended that you use `Measure-Object` in the pipeline if you want to measure a collection of objects based on whether the objects have specific values in defined properties.</span></span>

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

### <span data-ttu-id="0eb02-158">-Line</span><span class="sxs-lookup"><span data-stu-id="0eb02-158">-Line</span></span>

<span data-ttu-id="0eb02-159">指出此 Cmdlet 會計算輸入物件中的行數。</span><span class="sxs-lookup"><span data-stu-id="0eb02-159">Indicates that the cmdlet counts the number of lines in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="0eb02-160">**單字** 、 **Char** 和 **Line** 參數會在每個輸入物件 *內* ，以及輸入物件 *之間* 進行計數。</span><span class="sxs-lookup"><span data-stu-id="0eb02-160">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="0eb02-161">請參閱範例7。</span><span class="sxs-lookup"><span data-stu-id="0eb02-161">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eb02-162">-Maximum</span><span class="sxs-lookup"><span data-stu-id="0eb02-162">-Maximum</span></span>

<span data-ttu-id="0eb02-163">指出此 Cmdlet 會顯示指定屬性的最大值。</span><span class="sxs-lookup"><span data-stu-id="0eb02-163">Indicates that the cmdlet displays the maximum value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eb02-164">-Minimum</span><span class="sxs-lookup"><span data-stu-id="0eb02-164">-Minimum</span></span>

<span data-ttu-id="0eb02-165">指出此 Cmdlet 會顯示指定屬性的最小值。</span><span class="sxs-lookup"><span data-stu-id="0eb02-165">Indicates that the cmdlet displays the minimum value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eb02-166">-Property</span><span class="sxs-lookup"><span data-stu-id="0eb02-166">-Property</span></span>

<span data-ttu-id="0eb02-167">指定要測量的一或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="0eb02-167">Specifies one or more properties to measure.</span></span> <span data-ttu-id="0eb02-168">如果您未指定任何其他量值，則 `Measure-Object` 會計算具有您指定之屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="0eb02-168">If you do not specify any other measures, `Measure-Object` counts the objects that have the properties you specify.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0eb02-169">-Sum</span><span class="sxs-lookup"><span data-stu-id="0eb02-169">-Sum</span></span>

<span data-ttu-id="0eb02-170">指出此 Cmdlet 會顯示指定屬性的總和。</span><span class="sxs-lookup"><span data-stu-id="0eb02-170">Indicates that the cmdlet displays the sum of the values of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eb02-171">-Word</span><span class="sxs-lookup"><span data-stu-id="0eb02-171">-Word</span></span>

<span data-ttu-id="0eb02-172">指出此 Cmdlet 會計算輸入物件中的文字數目。</span><span class="sxs-lookup"><span data-stu-id="0eb02-172">Indicates that the cmdlet counts the number of words in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="0eb02-173">**單字** 、 **Char** 和 **Line** 參數會在每個輸入物件 *內* ，以及輸入物件 *之間* 進行計數。</span><span class="sxs-lookup"><span data-stu-id="0eb02-173">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="0eb02-174">請參閱範例7。</span><span class="sxs-lookup"><span data-stu-id="0eb02-174">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0eb02-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0eb02-175">CommonParameters</span></span>

<span data-ttu-id="0eb02-176">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0eb02-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0eb02-177">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0eb02-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0eb02-178">輸入</span><span class="sxs-lookup"><span data-stu-id="0eb02-178">INPUTS</span></span>

### <span data-ttu-id="0eb02-179">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="0eb02-179">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="0eb02-180">您可以透過管線將物件傳送至 `Measure-Object` 。</span><span class="sxs-lookup"><span data-stu-id="0eb02-180">You can pipe objects to `Measure-Object`.</span></span>

## <span data-ttu-id="0eb02-181">輸出</span><span class="sxs-lookup"><span data-stu-id="0eb02-181">OUTPUTS</span></span>

### <span data-ttu-id="0eb02-182">GenericMeasureInfo。</span><span class="sxs-lookup"><span data-stu-id="0eb02-182">Microsoft.PowerShell.Commands.GenericMeasureInfo</span></span>

### <span data-ttu-id="0eb02-183">TextMeasureInfo。</span><span class="sxs-lookup"><span data-stu-id="0eb02-183">Microsoft.PowerShell.Commands.TextMeasureInfo</span></span>

<span data-ttu-id="0eb02-184">如果您使用 **Word** 參數，則會傳回 `Measure-Object` **TextMeasureInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="0eb02-184">If you use the **Word** parameter, `Measure-Object` returns a **TextMeasureInfo** object.</span></span>
<span data-ttu-id="0eb02-185">否則，它會傳回 **GenericMeasureInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="0eb02-185">Otherwise, it returns a **GenericMeasureInfo** object.</span></span>

## <span data-ttu-id="0eb02-186">注意</span><span class="sxs-lookup"><span data-stu-id="0eb02-186">NOTES</span></span>

## <span data-ttu-id="0eb02-187">相關連結</span><span class="sxs-lookup"><span data-stu-id="0eb02-187">RELATED LINKS</span></span>

[<span data-ttu-id="0eb02-188">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="0eb02-188">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="0eb02-189">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="0eb02-189">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="0eb02-190">Group-Object</span><span class="sxs-lookup"><span data-stu-id="0eb02-190">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="0eb02-191">New-Object</span><span class="sxs-lookup"><span data-stu-id="0eb02-191">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="0eb02-192">Select-Object</span><span class="sxs-lookup"><span data-stu-id="0eb02-192">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="0eb02-193">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="0eb02-193">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="0eb02-194">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="0eb02-194">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="0eb02-195">Where-Object</span><span class="sxs-lookup"><span data-stu-id="0eb02-195">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
