---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: a64b11206a0755cedabad2894ecc330fac95a8d5
ms.sourcegitcommit: c8d1ffeab215e74e87ea1b0af8cd606c1a6a80ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "93206355"
---
# <span data-ttu-id="b1f42-103">Out-String</span><span class="sxs-lookup"><span data-stu-id="b1f42-103">Out-String</span></span>

## <span data-ttu-id="b1f42-104">概要</span><span class="sxs-lookup"><span data-stu-id="b1f42-104">SYNOPSIS</span></span>
<span data-ttu-id="b1f42-105">以字串形式輸出輸入物件。</span><span class="sxs-lookup"><span data-stu-id="b1f42-105">Outputs input objects as a strings.</span></span>

## <span data-ttu-id="b1f42-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b1f42-106">SYNTAX</span></span>

### <span data-ttu-id="b1f42-107">NoNewLineFormatting (預設) </span><span class="sxs-lookup"><span data-stu-id="b1f42-107">NoNewLineFormatting (Default)</span></span>

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### <span data-ttu-id="b1f42-108">StreamFormatting</span><span class="sxs-lookup"><span data-stu-id="b1f42-108">StreamFormatting</span></span>

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="b1f42-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b1f42-109">DESCRIPTION</span></span>

<span data-ttu-id="b1f42-110">`Out-String`Cmdlet 會將輸入物件轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="b1f42-110">The `Out-String` cmdlet converts input objects into strings.</span></span> <span data-ttu-id="b1f42-111">依預設， `Out-String` 會累積字串並將它們當作單一字串傳回，但您可以使用 **資料流程** 參數來指示 `Out-String` 一次傳回一行或建立字串陣列。</span><span class="sxs-lookup"><span data-stu-id="b1f42-111">By default, `Out-String` accumulates the strings and returns them as a single string, but you can use the **Stream** parameter to direct `Out-String` to return one line at a time or create and array of strings.</span></span> <span data-ttu-id="b1f42-112">此 Cmdlet 可讓您搜尋和操作字串輸出，比在傳統殼層中的物件操作更便利。</span><span class="sxs-lookup"><span data-stu-id="b1f42-112">This cmdlet lets you search and manipulate string output as you would in traditional shells when object manipulation is less convenient.</span></span>

## <span data-ttu-id="b1f42-113">範例</span><span class="sxs-lookup"><span data-stu-id="b1f42-113">EXAMPLES</span></span>

### <span data-ttu-id="b1f42-114">範例1：取得目前的文化特性，並將資料轉換成字串</span><span class="sxs-lookup"><span data-stu-id="b1f42-114">Example 1: Get the current culture and convert the data to strings</span></span>

<span data-ttu-id="b1f42-115">這個範例會取得目前使用者的區域設定，並將物件資料轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="b1f42-115">This example gets the regional settings for the current user and converts the object data to strings.</span></span>

```powershell
$C = Get-Culture | Select-Object -Property *
Out-String -InputObject $C -Width 100
```

```Output
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - en-US
TextInfo                       : TextInfo - en-US
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar,
                                 System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

<span data-ttu-id="b1f42-116">`$C`變數會儲存 **Selected.System。全球化 CultureInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="b1f42-116">The `$C` variable stores a **Selected.System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="b1f42-117">物件是將 `Get-Culture` 輸出向下傳送至的結果 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="b1f42-117">The object is the result of `Get-Culture` sending output down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="b1f42-118">**Property** 參數會使用星號 (`*`) 萬用字元來指定所有屬性都包含在物件中。</span><span class="sxs-lookup"><span data-stu-id="b1f42-118">The **Property** parameter uses an asterisk (`*`) wildcard to specify all properties are contained in the object.</span></span>

<span data-ttu-id="b1f42-119">`Out-String` 使用 **InputObject** 參數來指定儲存在變數中的 **CultureInfo** 物件 `$C` 。</span><span class="sxs-lookup"><span data-stu-id="b1f42-119">`Out-String` uses the **InputObject** parameter to specify the **CultureInfo** object stored in the `$C` variable.</span></span> <span data-ttu-id="b1f42-120">中的物件 `$C` 會轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="b1f42-120">The objects in `$C` are converted to a string.</span></span>

> [!NOTE]
> <span data-ttu-id="b1f42-121">若要查看 `Out-String` 陣列，請將輸出儲存至變數，並使用陣列索引來查看元素。</span><span class="sxs-lookup"><span data-stu-id="b1f42-121">To view the `Out-String` array, store the output to a variable and use an array index to view the elements.</span></span> <span data-ttu-id="b1f42-122">如需陣列索引的詳細資訊，請參閱 [about_Arrays](../microsoft.powershell.core/about/about_arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f42-122">For more information about the array index, see [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).</span></span>
>
> `$str = Out-String -InputObject $C -Width 100`

### <span data-ttu-id="b1f42-123">範例2：處理物件</span><span class="sxs-lookup"><span data-stu-id="b1f42-123">Example 2: Working with objects</span></span>

<span data-ttu-id="b1f42-124">此範例示範使用物件和使用字串之間的差異。</span><span class="sxs-lookup"><span data-stu-id="b1f42-124">This example demonstrates the difference between working with objects and working with strings.</span></span> <span data-ttu-id="b1f42-125">此命令會顯示包含文字 **gcm** （別名）的別名 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="b1f42-125">The command displays an alias that includes the text **gcm** , the alias for `Get-Command`.</span></span>

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

<span data-ttu-id="b1f42-126">`Get-Alias` 取得 **system.management.automation.aliasinfo** 物件，每個別名各一個，並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="b1f42-126">`Get-Alias` gets the **System.Management.Automation.AliasInfo** objects, one for each alias, and sends the objects down the pipeline.</span></span> <span data-ttu-id="b1f42-127">`Out-String` 使用 **資料流程** 參數將每個物件轉換成字串，而不將所有物件串連成單一字串。</span><span class="sxs-lookup"><span data-stu-id="b1f42-127">`Out-String` uses the **Stream** parameter to convert each object to a string rather concatenating all the objects into a single string.</span></span> <span data-ttu-id="b1f42-128">**System.string** 物件會向下傳送管線，並 `Select-String` 使用 **Pattern** 參數尋找文字 **gcm** 的相符專案。</span><span class="sxs-lookup"><span data-stu-id="b1f42-128">The **System.String** objects are sent down the pipeline and `Select-String` uses the **Pattern** parameter to find matches for the text **gcm** .</span></span>

> [!NOTE]
> <span data-ttu-id="b1f42-129">如果您省略 **資料流程** 參數，此命令會顯示所有別名，因為會 `Select-String` 在傳回的單一字串中尋找文字 **gcm** `Out-String` 。</span><span class="sxs-lookup"><span data-stu-id="b1f42-129">If you omit the **Stream** parameter, the command displays all the aliases because `Select-String` finds the text **gcm** in the single string that `Out-String` returns.</span></span>

### <span data-ttu-id="b1f42-130">範例3：使用 Width 參數以防止截斷。</span><span class="sxs-lookup"><span data-stu-id="b1f42-130">Example 3: Use the Width parameter to prevent truncation.</span></span>

<span data-ttu-id="b1f42-131">雖然大部分的輸出 `Out-String` 都會包裝到下一行，但在某些情況下，格式化系統會在傳遞之前截斷輸出 `Out-String` 。</span><span class="sxs-lookup"><span data-stu-id="b1f42-131">While most output from `Out-String` is wrapped to the next line, there are scenarios where the output is truncated by the formatting system before being passed to `Out-String`.</span></span> <span data-ttu-id="b1f42-132">您可以使用 **Width** 參數避免截斷。</span><span class="sxs-lookup"><span data-stu-id="b1f42-132">You can avoid truncation using the **Width** parameter.</span></span>

```powershell
PS> @{TestKey = ('x' * 200)} | Out-String
Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx...

PS> @{TestKey = ('x' * 200)} | Out-String -Width 250

Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## <span data-ttu-id="b1f42-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b1f42-133">PARAMETERS</span></span>

### <span data-ttu-id="b1f42-134">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b1f42-134">-InputObject</span></span>

<span data-ttu-id="b1f42-135">指定要寫入字串的物件。</span><span class="sxs-lookup"><span data-stu-id="b1f42-135">Specifies the objects to be written to a string.</span></span> <span data-ttu-id="b1f42-136">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="b1f42-136">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="b1f42-137">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="b1f42-137">-NoNewline</span></span>

<span data-ttu-id="b1f42-138">從 PowerShell 格式器產生的輸出中移除所有分行符號。</span><span class="sxs-lookup"><span data-stu-id="b1f42-138">Removes all newlines from output generated by the PowerShell formatter.</span></span> <span data-ttu-id="b1f42-139">包含在字串物件中的分行符號會保留下來。</span><span class="sxs-lookup"><span data-stu-id="b1f42-139">Newlines that are part of the string objects are preserved.</span></span>

<span data-ttu-id="b1f42-140">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b1f42-140">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoNewLineFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1f42-141">-Stream</span><span class="sxs-lookup"><span data-stu-id="b1f42-141">-Stream</span></span>

<span data-ttu-id="b1f42-142">指出此 Cmdlet 會為輸入物件的每一行傳送個別字串。</span><span class="sxs-lookup"><span data-stu-id="b1f42-142">Indicates that the cmdlet sends a separate string for each line of an input object.</span></span> <span data-ttu-id="b1f42-143">根據預設，每個物件的字串會累積，並會以單一字串形式傳送。</span><span class="sxs-lookup"><span data-stu-id="b1f42-143">By default, the strings for each object are accumulated and sent as a single string.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StreamFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b1f42-144">-Width</span><span class="sxs-lookup"><span data-stu-id="b1f42-144">-Width</span></span>

<span data-ttu-id="b1f42-145">指定每一行輸出的字元數目。</span><span class="sxs-lookup"><span data-stu-id="b1f42-145">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="b1f42-146">任何額外的字元都會包裝到下一行，或根據所使用的格式器 Cmdlet 來截斷。</span><span class="sxs-lookup"><span data-stu-id="b1f42-146">Any additional characters are wrapped to the next line or truncated depending on the formatter cmdlet used.</span></span> <span data-ttu-id="b1f42-147">**Width** 參數只適用于正在格式化的物件。</span><span class="sxs-lookup"><span data-stu-id="b1f42-147">The **Width** parameter applies only to objects that are being formatted.</span></span> <span data-ttu-id="b1f42-148">如果您省略這個參數，則寬度取決於主機程式的特性。</span><span class="sxs-lookup"><span data-stu-id="b1f42-148">If you omit this parameter, the width is determined by the characteristics of the host program.</span></span> <span data-ttu-id="b1f42-149">在終端機 (主控台) 視窗中，目前的視窗寬度會用來做為預設值。</span><span class="sxs-lookup"><span data-stu-id="b1f42-149">In terminal (console) windows, the current window width is used as the default value.</span></span> <span data-ttu-id="b1f42-150">PowerShell 主控台視窗在安裝時預設為80個字元的寬度。</span><span class="sxs-lookup"><span data-stu-id="b1f42-150">PowerShell console windows default to a width of 80 characters on installation.</span></span>

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

### <span data-ttu-id="b1f42-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b1f42-151">CommonParameters</span></span>

<span data-ttu-id="b1f42-152">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b1f42-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b1f42-153">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b1f42-153">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b1f42-154">輸入</span><span class="sxs-lookup"><span data-stu-id="b1f42-154">INPUTS</span></span>

### <span data-ttu-id="b1f42-155">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="b1f42-155">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b1f42-156">您可以將物件沿著管線向下傳送至 `Out-String` 。</span><span class="sxs-lookup"><span data-stu-id="b1f42-156">You can send objects down the pipeline to `Out-String`.</span></span>

## <span data-ttu-id="b1f42-157">輸出</span><span class="sxs-lookup"><span data-stu-id="b1f42-157">OUTPUTS</span></span>

### <span data-ttu-id="b1f42-158">System.String</span><span class="sxs-lookup"><span data-stu-id="b1f42-158">System.String</span></span>

<span data-ttu-id="b1f42-159">`Out-String` 傳回從輸入物件建立的字串。</span><span class="sxs-lookup"><span data-stu-id="b1f42-159">`Out-String` returns the string that it creates from the input object.</span></span>

## <span data-ttu-id="b1f42-160">注意</span><span class="sxs-lookup"><span data-stu-id="b1f42-160">NOTES</span></span>

<span data-ttu-id="b1f42-161">包含動詞的 Cmdlet 不會將 `Out` 物件格式化。</span><span class="sxs-lookup"><span data-stu-id="b1f42-161">The cmdlets that contain the `Out` verb don't format objects.</span></span> <span data-ttu-id="b1f42-162">Cmdlet 會將 `Out` 物件傳送至指定的顯示目的地的格式器。</span><span class="sxs-lookup"><span data-stu-id="b1f42-162">The `Out` cmdlets send objects to the formatter for the specified display destination.</span></span>

## <span data-ttu-id="b1f42-163">相關連結</span><span class="sxs-lookup"><span data-stu-id="b1f42-163">RELATED LINKS</span></span>

[<span data-ttu-id="b1f42-164">about_Formatting</span><span class="sxs-lookup"><span data-stu-id="b1f42-164">about_Formatting</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="b1f42-165">Out-Default</span><span class="sxs-lookup"><span data-stu-id="b1f42-165">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="b1f42-166">Out-File</span><span class="sxs-lookup"><span data-stu-id="b1f42-166">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="b1f42-167">Out-Host</span><span class="sxs-lookup"><span data-stu-id="b1f42-167">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="b1f42-168">Out-Null</span><span class="sxs-lookup"><span data-stu-id="b1f42-168">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="b1f42-169">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="b1f42-169">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="b1f42-170">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="b1f42-170">Out-Printer</span></span>](Out-Printer.md)
