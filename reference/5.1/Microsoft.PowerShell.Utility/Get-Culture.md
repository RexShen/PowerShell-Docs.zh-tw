---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-culture?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Culture
ms.openlocfilehash: 214bdd9296dbdbec166e30ba1da0b7976a664ec8
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239929"
---
# Get-Culture

## 概要
取得作業系統中目前設定的文化特性。

## SYNTAX

```
Get-Culture [<CommonParameters>]
```

## DESCRIPTION

`Get-Culture`Cmdlet 會取得目前文化特性設定的相關資訊。 這包括與系統上目前語言設定相關的資訊，例如鍵盤配置及項目顯示格式，像是數字、貨幣和日期。

您也可以使用 `Get-UICulture` Cmdlet，此 Cmdlet 會取得系統上的目前使用者介面文化特性，以及國際模組中的 [設定文化](/powershell/module/international/set-culture) 特性 Cmdlet。 使用者介面 (UI) 文化特性會決定要將哪些文字字串用於使用者介面元素，例如功能表和訊息。

## 範例

### 範例1：取得文化特性設定

```powershell
Get-Culture
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

這個命令會顯示與電腦上地區設定相關的資訊。

### 範例2：設定文化特性物件的屬性格式

```powershell
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
IsReadOnly                     : False

PS C:\> $C.Calendar
MinSupportedDateTime : 1/1/0001 12:00:00 AM
MaxSupportedDateTime : 12/31/9999 11:59:59 PM
AlgorithmType        : SolarCalendar
CalendarType         : Localized
Eras                 : {1}
TwoDigitYearMax      : 2029
IsReadOnly           : False

PS C:\> $C.DateTimeFormat
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
MonthGenitiveNames               : {January, February, March, April...}

PS C:\> $C.DateTimeFormat.FirstDayOfWeek
Sunday
```

這個範例示範文化特性物件中的大量資料。 它示範如何顯示物件的屬性和子屬性。

第一個命令會使用 `Get-Culture` Cmdlet 來取得電腦上目前的文化特性設定。
它會將產生的文化特性物件儲存在 `$C` 變數中。

第二個命令會顯示文化特性物件的所有屬性。 它使用管線運算子 (`|`) 將文化特性物件傳送 `$C` 至 `Format-List` Cmdlet。 它會使用 **Property** 參數來顯示 `*` 物件的所有 () 屬性。 此命令可以縮寫為 `$c | fl *` 。

剩餘的命令會藉由使用點標記法來顯示物件屬性的值，以探索文化特性物件的屬性。 您可以使用這個標記法來顯示物件的任何屬性值。

第三個命令使用點標記法來顯示文化特性物件之 **Calendar** 屬性的值。

第四個命令會使用點標記法來顯示文化特性物件的 **之 datatimeformat** 屬性值。

許多物件屬性都有屬性。 第五個命令使用點標記法來顯示 **DateTimeFormat** 屬性之 **FirstDayOfWeek** 屬性的值。

## PARAMETERS

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.Globalization.CultureInfo

`Get-Culture` 傳回代表目前文化特性的物件。

## 注意

您也可以使用 `$PsCulture` 和 `$PsUICulture` 變數。 `$PsCulture`變數會儲存目前文化特性的名稱，而 `$PsUICulture` 變數會儲存目前 UI 文化特性的名稱。

## 相關連結

[Set-Culture](/powershell/module/international/set-culture)

[Get-UICulture](Get-UICulture.md)
