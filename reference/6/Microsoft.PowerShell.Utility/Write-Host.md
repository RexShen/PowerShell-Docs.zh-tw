---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: f0b7542d551fa0dbbdec186980dcdb7ac600b60c
ms.sourcegitcommit: 758e6dbb428295698d4852b3e19f5d03deade037
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "93206255"
---
# <span data-ttu-id="346d3-103">Write-Host</span><span class="sxs-lookup"><span data-stu-id="346d3-103">Write-Host</span></span>

## <span data-ttu-id="346d3-104">概要</span><span class="sxs-lookup"><span data-stu-id="346d3-104">SYNOPSIS</span></span>

<span data-ttu-id="346d3-105">將自訂輸出寫入主機。</span><span class="sxs-lookup"><span data-stu-id="346d3-105">Writes customized output to a host.</span></span>

## <span data-ttu-id="346d3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="346d3-106">SYNTAX</span></span>

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## <span data-ttu-id="346d3-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="346d3-107">DESCRIPTION</span></span>

<span data-ttu-id="346d3-108">指令程式的 `Write-Host` 主要目的是要產生 (的主機) 僅顯示輸出，例如列印彩色文字（例如，在提示使用者輸入與 [讀取主](Read-Host.md)控制項的輸入時）。</span><span class="sxs-lookup"><span data-stu-id="346d3-108">The `Write-Host` cmdlet's primary purpose is to produce for-(host)-display-only output, such as printing colored text like when prompting the user for input in conjunction with [Read-Host](Read-Host.md).</span></span>
<span data-ttu-id="346d3-109">`Write-Host` 使用 [ToString ( # B1 ](/dotnet/api/system.object.tostring) 方法寫入輸出。</span><span class="sxs-lookup"><span data-stu-id="346d3-109">`Write-Host` uses the [ToString()](/dotnet/api/system.object.tostring) method to write the output.</span></span> <span data-ttu-id="346d3-110">相反地，若要將資料輸出到管線，請使用 [寫入輸出](Write-Output.md) 或隱含輸出。</span><span class="sxs-lookup"><span data-stu-id="346d3-110">By contrast, to output data to the pipeline, use [Write-Output](Write-Output.md) or implicit output.</span></span>

<span data-ttu-id="346d3-111">您可以使用參數來指定文字的色彩 `ForegroundColor` ，而且可以使用參數指定背景色彩 `BackgroundColor` 。</span><span class="sxs-lookup"><span data-stu-id="346d3-111">You can specify the color of text by using the `ForegroundColor` parameter, and you can specify the background color by using the `BackgroundColor` parameter.</span></span> <span data-ttu-id="346d3-112">Separator 參數可讓您指定用來區隔顯示之物件的字串。</span><span class="sxs-lookup"><span data-stu-id="346d3-112">The Separator parameter lets you specify a string to use to separate displayed objects.</span></span> <span data-ttu-id="346d3-113">特定的結果取決於裝載 PowerShell 的程式。</span><span class="sxs-lookup"><span data-stu-id="346d3-113">The particular result depends on the program that is hosting PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="346d3-114">從 Windows PowerShell 5.0 開始，是的包裝函式，可 `Write-Host` `Write-Information` 讓您用 `Write-Host` 來發出輸出至資訊串流。</span><span class="sxs-lookup"><span data-stu-id="346d3-114">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="346d3-115">這可讓您 **捕捉** 或 **隱藏** 使用撰寫的資料， `Write-Host` 同時保留回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="346d3-115">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span>
>
> <span data-ttu-id="346d3-116">`$InformationPreference`喜好設定變數和 `InformationAction` 一般參數不會影響 `Write-Host` 訊息。</span><span class="sxs-lookup"><span data-stu-id="346d3-116">The `$InformationPreference` preference variable and `InformationAction` common parameter do not affect `Write-Host` messages.</span></span> <span data-ttu-id="346d3-117">這項規則的例外狀況是 `-InformationAction Ignore` 有效地隱藏 `Write-Host` 輸出。</span><span class="sxs-lookup"><span data-stu-id="346d3-117">The exception to this rule is `-InformationAction Ignore`, which effectively suppresses `Write-Host` output.</span></span> <span data-ttu-id="346d3-118"> (請參閱「範例5」 ) </span><span class="sxs-lookup"><span data-stu-id="346d3-118">(see "Example 5")</span></span>

## <span data-ttu-id="346d3-119">範例</span><span class="sxs-lookup"><span data-stu-id="346d3-119">EXAMPLES</span></span>

### <span data-ttu-id="346d3-120">範例1：寫入主控台而不新增一行</span><span class="sxs-lookup"><span data-stu-id="346d3-120">Example 1: Write to the console without adding a new line</span></span>

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

<span data-ttu-id="346d3-121">此命令會以參數顯示「沒有分行符號測試」字串 `NoNewline` 。</span><span class="sxs-lookup"><span data-stu-id="346d3-121">This command displays the string 'no newline test' with the `NoNewline` parameter.</span></span>

<span data-ttu-id="346d3-122">寫入第二個字串，但它最後會在與第一個字串相同的行上，因為沒有任何分行符號分隔字串。</span><span class="sxs-lookup"><span data-stu-id="346d3-122">A second string is written, but it ends up on the same line as the first due to the absence of a newline separating the strings.</span></span>

### <span data-ttu-id="346d3-123">範例2：寫入主控台並包含分隔符號</span><span class="sxs-lookup"><span data-stu-id="346d3-123">Example 2: Write to the console and include a separator</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

此命令會顯示從2到12的偶數數位。 <span data-ttu-id="346d3-125">**分隔符號** 參數是用來將字串新增 `, +2= ` (逗號、空格、、 `+` 、 `2` `=` 、space) 。</span><span class="sxs-lookup"><span data-stu-id="346d3-125">The **Separator** parameter is used to add the string `, +2= ` (comma, space, `+`, `2`, `=`, space).</span></span>

### <span data-ttu-id="346d3-126">範例3：使用不同的文字和背景色彩進行寫入</span><span class="sxs-lookup"><span data-stu-id="346d3-126">Example 3: Write with different text and background colors</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

<span data-ttu-id="346d3-127">此命令會顯示從2到12的偶數數位。</span><span class="sxs-lookup"><span data-stu-id="346d3-127">This command displays the even numbers from two through twelve.</span></span> <span data-ttu-id="346d3-128">它會使用 `ForegroundColor` 參數來輸出深綠色文字，並使用 `BackgroundColor` 參數來顯示白色背景。</span><span class="sxs-lookup"><span data-stu-id="346d3-128">It uses the `ForegroundColor` parameter to output dark green text and the `BackgroundColor` parameter to display a white background.</span></span>

### <span data-ttu-id="346d3-129">範例4：使用不同的文字和背景色彩進行寫入</span><span class="sxs-lookup"><span data-stu-id="346d3-129">Example 4: Write with different text and background colors</span></span>

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

<span data-ttu-id="346d3-130">此命令會顯示 "Red on white text" 字串。</span><span class="sxs-lookup"><span data-stu-id="346d3-130">This command displays the string "Red on white text."</span></span> <span data-ttu-id="346d3-131">文字是紅色，如參數所定義 `ForegroundColor` 。</span><span class="sxs-lookup"><span data-stu-id="346d3-131">The text is red, as defined by the `ForegroundColor` parameter.</span></span> <span data-ttu-id="346d3-132">背景是白色，如參數所定義 `BackgroundColor` 。</span><span class="sxs-lookup"><span data-stu-id="346d3-132">The background is white, as defined by the `BackgroundColor` parameter.</span></span>

### <span data-ttu-id="346d3-133">範例5：抑制 Write-Host 的輸出</span><span class="sxs-lookup"><span data-stu-id="346d3-133">Example 5: Suppress output from Write-Host</span></span>

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

<span data-ttu-id="346d3-134">這些命令會有效地隱藏 Cmdlet 的輸出 `Write-Host` 。</span><span class="sxs-lookup"><span data-stu-id="346d3-134">These commands effectively suppress output of the `Write-Host` cmdlet.</span></span> <span data-ttu-id="346d3-135">第一個會使用 `InformationAction` 參數搭配 `Ignore` 值來抑制資訊資料流程的輸出。</span><span class="sxs-lookup"><span data-stu-id="346d3-135">The first one uses the `InformationAction` parameter with the `Ignore` Value to suppress output to the information stream.</span></span>
<span data-ttu-id="346d3-136">第二個範例會將命令的資訊資料流程重新導向至變數，藉此將 `$null` 它隱藏。</span><span class="sxs-lookup"><span data-stu-id="346d3-136">The second example redirects the information stream of the command to the `$null` variable and thereby suppresses it.</span></span>

## <span data-ttu-id="346d3-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="346d3-137">PARAMETERS</span></span>

### <span data-ttu-id="346d3-138">-BackgroundColor</span><span class="sxs-lookup"><span data-stu-id="346d3-138">-BackgroundColor</span></span>

<span data-ttu-id="346d3-139">指定背景色彩。</span><span class="sxs-lookup"><span data-stu-id="346d3-139">Specifies the background color.</span></span> <span data-ttu-id="346d3-140">沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="346d3-140">There is no default.</span></span> <span data-ttu-id="346d3-141">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="346d3-141">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="346d3-142">黑色</span><span class="sxs-lookup"><span data-stu-id="346d3-142">Black</span></span>
- <span data-ttu-id="346d3-143">1：深藍色</span><span class="sxs-lookup"><span data-stu-id="346d3-143">DarkBlue</span></span>
- <span data-ttu-id="346d3-144">2：深綠色</span><span class="sxs-lookup"><span data-stu-id="346d3-144">DarkGreen</span></span>
- <span data-ttu-id="346d3-145">3：深青綠色</span><span class="sxs-lookup"><span data-stu-id="346d3-145">DarkCyan</span></span>
- <span data-ttu-id="346d3-146">4：深紅色</span><span class="sxs-lookup"><span data-stu-id="346d3-146">DarkRed</span></span>
- <span data-ttu-id="346d3-147">5：深洋紅色</span><span class="sxs-lookup"><span data-stu-id="346d3-147">DarkMagenta</span></span>
- <span data-ttu-id="346d3-148">6：深黃色</span><span class="sxs-lookup"><span data-stu-id="346d3-148">DarkYellow</span></span>
- <span data-ttu-id="346d3-149">灰色</span><span class="sxs-lookup"><span data-stu-id="346d3-149">Gray</span></span>
- <span data-ttu-id="346d3-150">8：深灰色</span><span class="sxs-lookup"><span data-stu-id="346d3-150">DarkGray</span></span>
- <span data-ttu-id="346d3-151">藍色</span><span class="sxs-lookup"><span data-stu-id="346d3-151">Blue</span></span>
- <span data-ttu-id="346d3-152">綠色</span><span class="sxs-lookup"><span data-stu-id="346d3-152">Green</span></span>
- <span data-ttu-id="346d3-153">11：青色</span><span class="sxs-lookup"><span data-stu-id="346d3-153">Cyan</span></span>
- <span data-ttu-id="346d3-154">紅色</span><span class="sxs-lookup"><span data-stu-id="346d3-154">Red</span></span>
- <span data-ttu-id="346d3-155">桃紅色</span><span class="sxs-lookup"><span data-stu-id="346d3-155">Magenta</span></span>
- <span data-ttu-id="346d3-156">黃色</span><span class="sxs-lookup"><span data-stu-id="346d3-156">Yellow</span></span>
- <span data-ttu-id="346d3-157">白色</span><span class="sxs-lookup"><span data-stu-id="346d3-157">White</span></span>

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="346d3-158">-ForegroundColor</span><span class="sxs-lookup"><span data-stu-id="346d3-158">-ForegroundColor</span></span>

<span data-ttu-id="346d3-159">指定文字色彩。</span><span class="sxs-lookup"><span data-stu-id="346d3-159">Specifies the text color.</span></span> <span data-ttu-id="346d3-160">沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="346d3-160">There is no default.</span></span> <span data-ttu-id="346d3-161">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="346d3-161">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="346d3-162">黑色</span><span class="sxs-lookup"><span data-stu-id="346d3-162">Black</span></span>
- <span data-ttu-id="346d3-163">1：深藍色</span><span class="sxs-lookup"><span data-stu-id="346d3-163">DarkBlue</span></span>
- <span data-ttu-id="346d3-164">2：深綠色</span><span class="sxs-lookup"><span data-stu-id="346d3-164">DarkGreen</span></span>
- <span data-ttu-id="346d3-165">3：深青綠色</span><span class="sxs-lookup"><span data-stu-id="346d3-165">DarkCyan</span></span>
- <span data-ttu-id="346d3-166">4：深紅色</span><span class="sxs-lookup"><span data-stu-id="346d3-166">DarkRed</span></span>
- <span data-ttu-id="346d3-167">5：深洋紅色</span><span class="sxs-lookup"><span data-stu-id="346d3-167">DarkMagenta</span></span>
- <span data-ttu-id="346d3-168">6：深黃色</span><span class="sxs-lookup"><span data-stu-id="346d3-168">DarkYellow</span></span>
- <span data-ttu-id="346d3-169">灰色</span><span class="sxs-lookup"><span data-stu-id="346d3-169">Gray</span></span>
- <span data-ttu-id="346d3-170">8：深灰色</span><span class="sxs-lookup"><span data-stu-id="346d3-170">DarkGray</span></span>
- <span data-ttu-id="346d3-171">藍色</span><span class="sxs-lookup"><span data-stu-id="346d3-171">Blue</span></span>
- <span data-ttu-id="346d3-172">綠色</span><span class="sxs-lookup"><span data-stu-id="346d3-172">Green</span></span>
- <span data-ttu-id="346d3-173">11：青色</span><span class="sxs-lookup"><span data-stu-id="346d3-173">Cyan</span></span>
- <span data-ttu-id="346d3-174">紅色</span><span class="sxs-lookup"><span data-stu-id="346d3-174">Red</span></span>
- <span data-ttu-id="346d3-175">桃紅色</span><span class="sxs-lookup"><span data-stu-id="346d3-175">Magenta</span></span>
- <span data-ttu-id="346d3-176">黃色</span><span class="sxs-lookup"><span data-stu-id="346d3-176">Yellow</span></span>
- <span data-ttu-id="346d3-177">白色</span><span class="sxs-lookup"><span data-stu-id="346d3-177">White</span></span>

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="346d3-178">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="346d3-178">-NoNewline</span></span>

<span data-ttu-id="346d3-179">輸入物件的字串表示會串連以形成輸出。</span><span class="sxs-lookup"><span data-stu-id="346d3-179">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="346d3-180">輸出字串之間不會插入空格或分行符號。</span><span class="sxs-lookup"><span data-stu-id="346d3-180">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="346d3-181">最後一個輸出字串之後不會加入任何新行。</span><span class="sxs-lookup"><span data-stu-id="346d3-181">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="346d3-182">-Object</span><span class="sxs-lookup"><span data-stu-id="346d3-182">-Object</span></span>

<span data-ttu-id="346d3-183">要顯示在主機中的物件。</span><span class="sxs-lookup"><span data-stu-id="346d3-183">Objects to display in the host.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="346d3-184">-Separator</span><span class="sxs-lookup"><span data-stu-id="346d3-184">-Separator</span></span>

<span data-ttu-id="346d3-185">指定要在主機所顯示的物件之間插入的分隔字串。</span><span class="sxs-lookup"><span data-stu-id="346d3-185">Specifies a separator string to insert between objects displayed by the host.</span></span>

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

### <span data-ttu-id="346d3-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="346d3-186">CommonParameters</span></span>
<span data-ttu-id="346d3-187">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="346d3-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="346d3-188">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="346d3-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="346d3-189">輸入</span><span class="sxs-lookup"><span data-stu-id="346d3-189">INPUTS</span></span>

### <span data-ttu-id="346d3-190">System.Object</span><span class="sxs-lookup"><span data-stu-id="346d3-190">System.Object</span></span>

<span data-ttu-id="346d3-191">您可以使用管線來傳送要寫入主機的物件。</span><span class="sxs-lookup"><span data-stu-id="346d3-191">You can pipe objects to be written to the host.</span></span>

## <span data-ttu-id="346d3-192">輸出</span><span class="sxs-lookup"><span data-stu-id="346d3-192">OUTPUTS</span></span>

### <span data-ttu-id="346d3-193">無</span><span class="sxs-lookup"><span data-stu-id="346d3-193">None</span></span>

<span data-ttu-id="346d3-194">`Write-Host` 將物件傳送至主機。</span><span class="sxs-lookup"><span data-stu-id="346d3-194">`Write-Host` sends the objects to the host.</span></span> <span data-ttu-id="346d3-195">它不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="346d3-195">It does not return any objects.</span></span> <span data-ttu-id="346d3-196">但是，主機會顯示傳送 `Write-Host` 給它的物件。</span><span class="sxs-lookup"><span data-stu-id="346d3-196">However, the host displays the objects that `Write-Host` sends to it.</span></span>

## <span data-ttu-id="346d3-197">注意</span><span class="sxs-lookup"><span data-stu-id="346d3-197">NOTES</span></span>

- <span data-ttu-id="346d3-198">將集合寫入至主機時，集合的元素會列印在以單一空格分隔的同一行上。</span><span class="sxs-lookup"><span data-stu-id="346d3-198">When writing a collection to the host, elements of the collection are printed on the same line separated by a single space.</span></span> <span data-ttu-id="346d3-199">這可以使用 **分隔符號** 參數加以覆寫。</span><span class="sxs-lookup"><span data-stu-id="346d3-199">This can be overridden with the **Separator** parameter.</span></span>

- <span data-ttu-id="346d3-200">非基本資料類型（例如具有屬性的物件）可能會導致非預期的結果，而不會提供有意義的輸出。</span><span class="sxs-lookup"><span data-stu-id="346d3-200">Non-primitive data types such as objects with properties can cause unexpected results and not provide meaningful output.</span></span> <span data-ttu-id="346d3-201">例如， `Write-Host @{a = 1; b = 2}` 會列印 `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` 到主機。</span><span class="sxs-lookup"><span data-stu-id="346d3-201">For example, `Write-Host @{a = 1; b = 2}` will print `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` to the host.</span></span>

## <span data-ttu-id="346d3-202">相關連結</span><span class="sxs-lookup"><span data-stu-id="346d3-202">RELATED LINKS</span></span>

[<span data-ttu-id="346d3-203">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="346d3-203">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="346d3-204">Out-Host</span><span class="sxs-lookup"><span data-stu-id="346d3-204">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="346d3-205">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="346d3-205">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="346d3-206">Write-Error</span><span class="sxs-lookup"><span data-stu-id="346d3-206">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="346d3-207">Write-Output</span><span class="sxs-lookup"><span data-stu-id="346d3-207">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="346d3-208">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="346d3-208">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="346d3-209">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="346d3-209">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="346d3-210">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="346d3-210">Write-Warning</span></span>](Write-Warning.md)
