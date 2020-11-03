---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-culture?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Culture
ms.openlocfilehash: 00f27b6b50c2c34be21e1c6f6bbef186243660aa
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204644"
---
# <span data-ttu-id="26434-103">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="26434-103">Get-Culture</span></span>

## <span data-ttu-id="26434-104">概要</span><span class="sxs-lookup"><span data-stu-id="26434-104">SYNOPSIS</span></span>
<span data-ttu-id="26434-105">取得作業系統中目前設定的文化特性。</span><span class="sxs-lookup"><span data-stu-id="26434-105">Gets the current culture set in the operating system.</span></span>

## <span data-ttu-id="26434-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="26434-106">SYNTAX</span></span>

### <span data-ttu-id="26434-107">CurrentCulture (預設) </span><span class="sxs-lookup"><span data-stu-id="26434-107">CurrentCulture (Default)</span></span>

```
Get-Culture [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="26434-108">Name</span><span class="sxs-lookup"><span data-stu-id="26434-108">Name</span></span>

```
Get-Culture [-Name <String[]>] [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="26434-109">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="26434-109">ListAvailable</span></span>

```
Get-Culture [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="26434-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="26434-110">DESCRIPTION</span></span>

<span data-ttu-id="26434-111">`Get-Culture`Cmdlet 會取得目前文化特性設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="26434-111">The `Get-Culture` cmdlet gets information about the current culture settings.</span></span>
<span data-ttu-id="26434-112">這包括與系統上目前語言設定相關的資訊，例如鍵盤配置及項目顯示格式，像是數字、貨幣和日期。</span><span class="sxs-lookup"><span data-stu-id="26434-112">This includes information about the current language settings on the system, such as the keyboard layout, and the display format of items such as numbers, currency, and dates.</span></span>

<span data-ttu-id="26434-113">您也可以使用 `Get-UICulture` Cmdlet，此 Cmdlet 會取得系統上的目前使用者介面文化特性，以及國際模組中的 [設定文化](/powershell/module/international/set-culture?view=win10-ps) 特性 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26434-113">You can also use the `Get-UICulture` cmdlet, which gets the current user interface culture on the system, and the [Set-Culture](/powershell/module/international/set-culture?view=win10-ps) cmdlet in the International module.</span></span>
<span data-ttu-id="26434-114">使用者介面 (UI) 文化特性會決定要將哪些文字字串用於使用者介面元素，例如功能表和訊息。</span><span class="sxs-lookup"><span data-stu-id="26434-114">The user-interface (UI) culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

## <span data-ttu-id="26434-115">範例</span><span class="sxs-lookup"><span data-stu-id="26434-115">EXAMPLES</span></span>

### <span data-ttu-id="26434-116">範例1：取得文化特性設定</span><span class="sxs-lookup"><span data-stu-id="26434-116">Example 1: Get culture settings</span></span>

```
PS C:\> Get-Culture
```

<span data-ttu-id="26434-117">這個命令會顯示與電腦上地區設定相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="26434-117">This command displays information about the regional settings on the computer.</span></span>

### <span data-ttu-id="26434-118">範例2：設定文化特性物件的屬性格式</span><span class="sxs-lookup"><span data-stu-id="26434-118">Example 2: Format the properties of a culture object</span></span>

```
PS C:\> $C = Get-Culture
PS C:\> $C | Format-List -Property *
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
CompareInfo                    : CompareInfo - 1033
TextInfo                       : TextInfo - 1033
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar, System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False PS C:\> $C.Calendar
MinSupportedDateTime : 1/1/0001 12:00:00 AM
MaxSupportedDateTime : 12/31/9999 11:59:59 PM
AlgorithmType        : SolarCalendar
CalendarType         : Localized
Eras                 : {1}
TwoDigitYearMax      : 2029
IsReadOnly           : False PS C:\> $C.DateTimeFormat
AMDesignator                     : AM
Calendar                         : System.Globalization.GregorianCalendar
DateSeparator                    : /
FirstDayOfWeek                   : Sunday
CalendarWeekRule                 : FirstDay
FullDateTimePattern              : dddd, MMMM dd, yyyy h:mm:ss tt
LongDatePattern                  : dddd, MMMM dd, yyyy
LongTimePattern                  : h:mm:ss tt
MonthDayPattern                  : MMMM dd
PMDesignator                     : PM
RFC1123Pattern                   : ddd, dd MMM yyyy HH':'mm':'ss 'GMT'
ShortDatePattern                 : M/d/yyyy
ShortTimePattern                 : h:mm tt
SortableDateTimePattern          : yyyy'-'MM'-'dd'T'HH':'mm':'ss
TimeSeparator                    : :
UniversalSortableDateTimePattern : yyyy'-'MM'-'dd HH':'mm':'ss'Z'
YearMonthPattern                 : MMMM, yyyy
AbbreviatedDayNames              : {Sun, Mon, Tue, Wed...}
ShortestDayNames                 : {Su, Mo, Tu, We...}
DayNames                         : {Sunday, Monday, Tuesday, Wednesday...}
AbbreviatedMonthNames            : {Jan, Feb, Mar, Apr...}
MonthNames                       : {January, February, March, April...}
IsReadOnly                       : False
NativeCalendarName               : Gregorian Calendar
AbbreviatedMonthGenitiveNames    : {Jan, Feb, Mar, Apr...}
MonthGenitiveNames               : {January, February, March, April...} PS C:\> $C.DateTimeFormat.FirstDayOfWeek
Sunday
```

<span data-ttu-id="26434-119">這個範例示範文化特性物件中的大量資料。</span><span class="sxs-lookup"><span data-stu-id="26434-119">This example demonstrates the vast amount of data in the culture object.</span></span>
<span data-ttu-id="26434-120">它示範如何顯示物件的屬性和子屬性。</span><span class="sxs-lookup"><span data-stu-id="26434-120">It shows how to display the properties and sub-properties of the object.</span></span>

<span data-ttu-id="26434-121">第一個命令會使用「 **取得文化** 特性」 Cmdlet 來取得電腦上目前的文化特性設定。</span><span class="sxs-lookup"><span data-stu-id="26434-121">The first command uses the **Get-Culture** cmdlet to get the current culture settings on the computer.</span></span>
<span data-ttu-id="26434-122">它會將產生的文化特性物件儲存在 $C 變數中。</span><span class="sxs-lookup"><span data-stu-id="26434-122">It stores the resulting culture object in the $C variable.</span></span>

<span data-ttu-id="26434-123">第二個命令會顯示文化特性物件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="26434-123">The second command displays all of the properties of the culture object.</span></span>
<span data-ttu-id="26434-124">它使用管線運算子 (|) 將文化特性物件傳送 `$C` 至 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26434-124">It uses a pipeline operator (|) to send the culture object in `$C` to the `Format-List` cmdlet.</span></span>
<span data-ttu-id="26434-125">它會使用 **Property** 參數來顯示 \* 物件的所有 () 屬性。</span><span class="sxs-lookup"><span data-stu-id="26434-125">It uses the **Property** parameter to display all (\*) properties of the object.</span></span>
<span data-ttu-id="26434-126">此命令可以縮寫為 `$c | fl *` 。</span><span class="sxs-lookup"><span data-stu-id="26434-126">This command can be abbreviated as `$c | fl *`.</span></span>

<span data-ttu-id="26434-127">剩餘的命令會藉由使用點標記法來顯示物件屬性的值，以探索文化特性物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="26434-127">The remaining commands explore the properties of the culture object by using dot notation to display the values of the object properties.</span></span>
<span data-ttu-id="26434-128">您可以使用這個標記法來顯示物件的任何屬性值。</span><span class="sxs-lookup"><span data-stu-id="26434-128">You can use this notation to display the value of any property of the object.</span></span>

<span data-ttu-id="26434-129">第三個命令使用點標記法來顯示文化特性物件之 **Calendar** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="26434-129">The third command uses dot notation to display the value of the **Calendar** property of the culture object.</span></span>

<span data-ttu-id="26434-130">第四個命令會使用點標記法來顯示文化特性物件的 **之 datatimeformat** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="26434-130">The fourth command uses dot notation to display the value of the **DataTimeFormat** property of the culture object.</span></span>

<span data-ttu-id="26434-131">許多物件屬性都有屬性。</span><span class="sxs-lookup"><span data-stu-id="26434-131">Many object properties have properties.</span></span>
<span data-ttu-id="26434-132">第五個命令使用點標記法來顯示 **DateTimeFormat** 屬性之 **FirstDayOfWeek** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="26434-132">The fifth command uses dot notation to display the value of the **FirstDayOfWeek** property of the **DateTimeFormat** property.</span></span>

### <span data-ttu-id="26434-133">範例3：取得特定文化特性</span><span class="sxs-lookup"><span data-stu-id="26434-133">Example 3: Get a specific culture</span></span>

<span data-ttu-id="26434-134">取得美國英文的 CultureInfo 物件。</span><span class="sxs-lookup"><span data-stu-id="26434-134">Get the CultureInfo object for English in the United States.</span></span>

```powershell
Get-Culture -Name en-US
```

```output
LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

## <span data-ttu-id="26434-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="26434-135">PARAMETERS</span></span>

### <span data-ttu-id="26434-136">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="26434-136">-ListAvailable</span></span>

<span data-ttu-id="26434-137">抓取目前作業系統支援的所有文化特性。</span><span class="sxs-lookup"><span data-stu-id="26434-137">Retrieves all cultures supported by the current operating system.</span></span>

<span data-ttu-id="26434-138">此參數是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="26434-138">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="26434-139">-Name</span><span class="sxs-lookup"><span data-stu-id="26434-139">-Name</span></span>

<span data-ttu-id="26434-140">根據名稱取出特定文化特性。</span><span class="sxs-lookup"><span data-stu-id="26434-140">Retrieve a specific culture based on the name.</span></span>

<span data-ttu-id="26434-141">此參數是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="26434-141">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="26434-142">-NoUserOverrides</span><span class="sxs-lookup"><span data-stu-id="26434-142">-NoUserOverrides</span></span>

<span data-ttu-id="26434-143">略過目前文化特性的使用者變更。</span><span class="sxs-lookup"><span data-stu-id="26434-143">Ignore user changes for current culture.</span></span>

<span data-ttu-id="26434-144">此參數是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="26434-144">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CurrentCulture, Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="26434-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="26434-145">CommonParameters</span></span>

<span data-ttu-id="26434-146">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="26434-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="26434-147">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="26434-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="26434-148">輸入</span><span class="sxs-lookup"><span data-stu-id="26434-148">INPUTS</span></span>

### <span data-ttu-id="26434-149">無</span><span class="sxs-lookup"><span data-stu-id="26434-149">None</span></span>

<span data-ttu-id="26434-150">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26434-150">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="26434-151">輸出</span><span class="sxs-lookup"><span data-stu-id="26434-151">OUTPUTS</span></span>

### <span data-ttu-id="26434-152">System.Globalization.CultureInfo</span><span class="sxs-lookup"><span data-stu-id="26434-152">System.Globalization.CultureInfo</span></span>

<span data-ttu-id="26434-153">`Get-Culture` 傳回代表目前文化特性的物件。</span><span class="sxs-lookup"><span data-stu-id="26434-153">`Get-Culture` returns an object that represents the current culture.</span></span>

## <span data-ttu-id="26434-154">注意</span><span class="sxs-lookup"><span data-stu-id="26434-154">NOTES</span></span>

<span data-ttu-id="26434-155">您也可以使用 `$PsCulture` 和 `$PsUICulture` 變數。</span><span class="sxs-lookup"><span data-stu-id="26434-155">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="26434-156">`$PsCulture`變數會儲存目前文化特性的名稱，而 `$PsUICulture` 變數會儲存目前 UI 文化特性的名稱。</span><span class="sxs-lookup"><span data-stu-id="26434-156">The `$PsCulture` variable stores the name of the current culture and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="26434-157">相關連結</span><span class="sxs-lookup"><span data-stu-id="26434-157">RELATED LINKS</span></span>

[<span data-ttu-id="26434-158">Set-Culture</span><span class="sxs-lookup"><span data-stu-id="26434-158">Set-Culture</span></span>](/powershell/module/international/set-culture?view=win10-ps)

[<span data-ttu-id="26434-159">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="26434-159">Get-UICulture</span></span>](Get-UICulture.md)
