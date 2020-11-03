---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: 6bcda4d1796f2a2ccd61469523443f90ddde5e29
ms.sourcegitcommit: c8d1ffeab215e74e87ea1b0af8cd606c1a6a80ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "93206347"
---
# <span data-ttu-id="b0aa4-103">Out-String</span><span class="sxs-lookup"><span data-stu-id="b0aa4-103">Out-String</span></span>

## <span data-ttu-id="b0aa4-104">概要</span><span class="sxs-lookup"><span data-stu-id="b0aa4-104">SYNOPSIS</span></span>
<span data-ttu-id="b0aa4-105">以字串形式輸出輸入物件。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-105">Outputs input objects as a strings.</span></span>

## <span data-ttu-id="b0aa4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b0aa4-106">SYNTAX</span></span>

### <span data-ttu-id="b0aa4-107">全部</span><span class="sxs-lookup"><span data-stu-id="b0aa4-107">All</span></span>

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="b0aa4-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b0aa4-108">DESCRIPTION</span></span>

<span data-ttu-id="b0aa4-109">`Out-String`Cmdlet 會將輸入物件轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-109">The `Out-String` cmdlet converts input objects into strings.</span></span> <span data-ttu-id="b0aa4-110">依預設， `Out-String` 會累積字串並將它們當作單一字串傳回，但您可以使用 **資料流程** 參數來指示 `Out-String` 一次傳回一行或建立字串陣列。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-110">By default, `Out-String` accumulates the strings and returns them as a single string, but you can use the **Stream** parameter to direct `Out-String` to return one line at a time or create and array of strings.</span></span> <span data-ttu-id="b0aa4-111">此 Cmdlet 可讓您搜尋和操作字串輸出，比在傳統殼層中的物件操作更便利。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-111">This cmdlet lets you search and manipulate string output as you would in traditional shells when object manipulation is less convenient.</span></span>

## <span data-ttu-id="b0aa4-112">範例</span><span class="sxs-lookup"><span data-stu-id="b0aa4-112">EXAMPLES</span></span>

### <span data-ttu-id="b0aa4-113">範例1：取得目前的文化特性，並將資料轉換成字串</span><span class="sxs-lookup"><span data-stu-id="b0aa4-113">Example 1: Get the current culture and convert the data to strings</span></span>

<span data-ttu-id="b0aa4-114">這個範例會取得目前使用者的區域設定，並將物件資料轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-114">This example gets the regional settings for the current user and converts the object data to strings.</span></span>

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

<span data-ttu-id="b0aa4-115">`$C`變數會儲存 **Selected.System。全球化 CultureInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-115">The `$C` variable stores a **Selected.System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="b0aa4-116">物件是將 `Get-Culture` 輸出向下傳送至的結果 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-116">The object is the result of `Get-Culture` sending output down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="b0aa4-117">**Property** 參數會使用星號 (`*`) 萬用字元來指定所有屬性都包含在物件中。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-117">The **Property** parameter uses an asterisk (`*`) wildcard to specify all properties are contained in the object.</span></span>

<span data-ttu-id="b0aa4-118">`Out-String` 使用 **InputObject** 參數來指定儲存在變數中的 **CultureInfo** 物件 `$C` 。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-118">`Out-String` uses the **InputObject** parameter to specify the **CultureInfo** object stored in the `$C` variable.</span></span> <span data-ttu-id="b0aa4-119">中的物件 `$C` 會轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-119">The objects in `$C` are converted to a string.</span></span>

> [!NOTE]
> <span data-ttu-id="b0aa4-120">若要查看 `Out-String` 陣列，請將輸出儲存至變數，並使用陣列索引來查看元素。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-120">To view the `Out-String` array, store the output to a variable and use an array index to view the elements.</span></span> <span data-ttu-id="b0aa4-121">如需陣列索引的詳細資訊，請參閱 [about_Arrays](../microsoft.powershell.core/about/about_arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-121">For more information about the array index, see [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).</span></span>
>
> `$str = Out-String -InputObject $C -Width 100`

### <span data-ttu-id="b0aa4-122">範例2：處理物件</span><span class="sxs-lookup"><span data-stu-id="b0aa4-122">Example 2: Working with objects</span></span>

<span data-ttu-id="b0aa4-123">此範例示範使用物件和使用字串之間的差異。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-123">This example demonstrates the difference between working with objects and working with strings.</span></span> <span data-ttu-id="b0aa4-124">此命令會顯示包含文字 **gcm** （別名）的別名 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-124">The command displays an alias that includes the text **gcm** , the alias for `Get-Command`.</span></span>

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

<span data-ttu-id="b0aa4-125">`Get-Alias` 取得 **system.management.automation.aliasinfo** 物件，每個別名各一個，並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-125">`Get-Alias` gets the **System.Management.Automation.AliasInfo** objects, one for each alias, and sends the objects down the pipeline.</span></span> <span data-ttu-id="b0aa4-126">`Out-String` 使用 **資料流程** 參數將每個物件轉換成字串，而不將所有物件串連成單一字串。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-126">`Out-String` uses the **Stream** parameter to convert each object to a string rather concatenating all the objects into a single string.</span></span> <span data-ttu-id="b0aa4-127">**System.string** 物件會向下傳送管線，並 `Select-String` 使用 **Pattern** 參數尋找文字 **gcm** 的相符專案。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-127">The **System.String** objects are sent down the pipeline and `Select-String` uses the **Pattern** parameter to find matches for the text **gcm** .</span></span>

> [!NOTE]
> <span data-ttu-id="b0aa4-128">如果您省略 **資料流程** 參數，此命令會顯示所有別名，因為會 `Select-String` 在傳回的單一字串中尋找文字 **gcm** `Out-String` 。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-128">If you omit the **Stream** parameter, the command displays all the aliases because `Select-String` finds the text **gcm** in the single string that `Out-String` returns.</span></span>

### <span data-ttu-id="b0aa4-129">範例3：使用 Width 參數以防止截斷。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-129">Example 3: Use the Width parameter to prevent truncation.</span></span>

<span data-ttu-id="b0aa4-130">雖然大部分的輸出 `Out-String` 都會包裝到下一行，但在某些情況下，格式化系統會在傳遞之前截斷輸出 `Out-String` 。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-130">While most output from `Out-String` is wrapped to the next line, there are scenarios where the output is truncated by the formatting system before being passed to `Out-String`.</span></span> <span data-ttu-id="b0aa4-131">您可以使用 **Width** 參數避免截斷。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-131">You can avoid truncation using the **Width** parameter.</span></span>

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

## <span data-ttu-id="b0aa4-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b0aa4-132">PARAMETERS</span></span>

### <span data-ttu-id="b0aa4-133">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b0aa4-133">-InputObject</span></span>

<span data-ttu-id="b0aa4-134">指定要寫入字串的物件。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-134">Specifies the objects to be written to a string.</span></span> <span data-ttu-id="b0aa4-135">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-135">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="b0aa4-136">-Stream</span><span class="sxs-lookup"><span data-stu-id="b0aa4-136">-Stream</span></span>

<span data-ttu-id="b0aa4-137">指出此 Cmdlet 會為輸入物件的每一行傳送個別字串。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-137">Indicates that the cmdlet sends a separate string for each line of an input object.</span></span> <span data-ttu-id="b0aa4-138">根據預設，每個物件的字串會累積，並會以單一字串形式傳送。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-138">By default, the strings for each object are accumulated and sent as a single string.</span></span>

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

### <span data-ttu-id="b0aa4-139">-Width</span><span class="sxs-lookup"><span data-stu-id="b0aa4-139">-Width</span></span>

<span data-ttu-id="b0aa4-140">指定每一行輸出的字元數目。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-140">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="b0aa4-141">任何額外的字元都會包裝到下一行，或根據所使用的格式器 Cmdlet 來截斷。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-141">Any additional characters are wrapped to the next line or truncated depending on the formatter cmdlet used.</span></span> <span data-ttu-id="b0aa4-142">**Width** 參數只適用于正在格式化的物件。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-142">The **Width** parameter applies only to objects that are being formatted.</span></span> <span data-ttu-id="b0aa4-143">如果您省略這個參數，則寬度取決於主機程式的特性。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-143">If you omit this parameter, the width is determined by the characteristics of the host program.</span></span> <span data-ttu-id="b0aa4-144">在終端機 (主控台) 視窗中，目前的視窗寬度會用來做為預設值。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-144">In terminal (console) windows, the current window width is used as the default value.</span></span> <span data-ttu-id="b0aa4-145">PowerShell 主控台視窗在安裝時預設為80個字元的寬度。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-145">PowerShell console windows default to a width of 80 characters on installation.</span></span>

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

### <span data-ttu-id="b0aa4-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b0aa4-146">CommonParameters</span></span>

<span data-ttu-id="b0aa4-147">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b0aa4-148">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b0aa4-149">輸入</span><span class="sxs-lookup"><span data-stu-id="b0aa4-149">INPUTS</span></span>

### <span data-ttu-id="b0aa4-150">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="b0aa4-150">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b0aa4-151">您可以將物件沿著管線向下傳送至 `Out-String` 。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-151">You can send objects down the pipeline to `Out-String`.</span></span>

## <span data-ttu-id="b0aa4-152">輸出</span><span class="sxs-lookup"><span data-stu-id="b0aa4-152">OUTPUTS</span></span>

### <span data-ttu-id="b0aa4-153">System.String</span><span class="sxs-lookup"><span data-stu-id="b0aa4-153">System.String</span></span>

<span data-ttu-id="b0aa4-154">`Out-String` 傳回從輸入物件建立的字串。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-154">`Out-String` returns the string that it creates from the input object.</span></span>

## <span data-ttu-id="b0aa4-155">注意</span><span class="sxs-lookup"><span data-stu-id="b0aa4-155">NOTES</span></span>

<span data-ttu-id="b0aa4-156">包含動詞的 Cmdlet 不會將 `Out` 物件格式化。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-156">The cmdlets that contain the `Out` verb don't format objects.</span></span> <span data-ttu-id="b0aa4-157">Cmdlet 會將 `Out` 物件傳送至指定的顯示目的地的格式器。</span><span class="sxs-lookup"><span data-stu-id="b0aa4-157">The `Out` cmdlets send objects to the formatter for the specified display destination.</span></span>

## <span data-ttu-id="b0aa4-158">相關連結</span><span class="sxs-lookup"><span data-stu-id="b0aa4-158">RELATED LINKS</span></span>

[<span data-ttu-id="b0aa4-159">about_Formatting</span><span class="sxs-lookup"><span data-stu-id="b0aa4-159">about_Formatting</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="b0aa4-160">Out-Default</span><span class="sxs-lookup"><span data-stu-id="b0aa4-160">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="b0aa4-161">Out-File</span><span class="sxs-lookup"><span data-stu-id="b0aa4-161">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="b0aa4-162">Out-Host</span><span class="sxs-lookup"><span data-stu-id="b0aa4-162">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="b0aa4-163">Out-Null</span><span class="sxs-lookup"><span data-stu-id="b0aa4-163">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="b0aa4-164">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="b0aa4-164">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="b0aa4-165">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="b0aa4-165">Out-Printer</span></span>](Out-Printer.md)
