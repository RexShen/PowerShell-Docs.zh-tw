---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: a299b04c8e041819ef2870abe263fae381b1d5dc
ms.sourcegitcommit: ea9270bacee7dd1b9df2519384de277576357ce2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "93206151"
---
# <span data-ttu-id="63cea-103">Get-Date</span><span class="sxs-lookup"><span data-stu-id="63cea-103">Get-Date</span></span>

## <span data-ttu-id="63cea-104">概要</span><span class="sxs-lookup"><span data-stu-id="63cea-104">SYNOPSIS</span></span>
<span data-ttu-id="63cea-105">取得目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-105">Gets the current date and time.</span></span>

## <span data-ttu-id="63cea-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="63cea-106">SYNTAX</span></span>

### <span data-ttu-id="63cea-107">Date (預設值)</span><span class="sxs-lookup"><span data-stu-id="63cea-107">Date (Default)</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="63cea-108">DateUFormat</span><span class="sxs-lookup"><span data-stu-id="63cea-108">DateUFormat</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

### <span data-ttu-id="63cea-109">UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="63cea-109">UnixTimeSeconds</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="63cea-110">UnixTimeSecondsUFormat</span><span class="sxs-lookup"><span data-stu-id="63cea-110">UnixTimeSecondsUFormat</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

## <span data-ttu-id="63cea-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="63cea-111">DESCRIPTION</span></span>

<span data-ttu-id="63cea-112">`Get-Date`Cmdlet 會取得代表目前日期或您所指定日期的 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="63cea-112">The `Get-Date` cmdlet gets a **DateTime** object that represents the current date or a date that you specify.</span></span> <span data-ttu-id="63cea-113">`Get-Date` 可以用數種 .NET 和 UNIX 格式來格式化日期和時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-113">`Get-Date` can format the date and time in several .NET and UNIX formats.</span></span> <span data-ttu-id="63cea-114">您可以使用 `Get-Date` 來產生日期或時間字元字串，然後將字串傳送到其他 Cmdlet 或程式。</span><span class="sxs-lookup"><span data-stu-id="63cea-114">You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.</span></span>

<span data-ttu-id="63cea-115">`Get-Date` 使用電腦的文化特性設定來決定如何格式化輸出。</span><span class="sxs-lookup"><span data-stu-id="63cea-115">`Get-Date` uses the computer's culture settings to determine how the output is formatted.</span></span> <span data-ttu-id="63cea-116">若要查看電腦的設定，請使用 `(Get-Culture).DateTimeFormat` 。</span><span class="sxs-lookup"><span data-stu-id="63cea-116">To view your computer's settings, use `(Get-Culture).DateTimeFormat`.</span></span>

## <span data-ttu-id="63cea-117">範例</span><span class="sxs-lookup"><span data-stu-id="63cea-117">EXAMPLES</span></span>

### <span data-ttu-id="63cea-118">範例1：取得目前的日期和時間</span><span class="sxs-lookup"><span data-stu-id="63cea-118">Example 1: Get the current date and time</span></span>

<span data-ttu-id="63cea-119">在此範例中，會 `Get-Date` 顯示目前的系統日期和時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-119">In this example, `Get-Date` displays the current system date and time.</span></span> <span data-ttu-id="63cea-120">輸出會是完整日期和完整時間格式。</span><span class="sxs-lookup"><span data-stu-id="63cea-120">The output is in the long-date and long-time formats.</span></span>

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### <span data-ttu-id="63cea-121">範例2：取得目前日期和時間的元素</span><span class="sxs-lookup"><span data-stu-id="63cea-121">Example 2: Get elements of the current date and time</span></span>

<span data-ttu-id="63cea-122">這個範例會示範如何使用 `Get-Date` 來取得日期或時間元素。</span><span class="sxs-lookup"><span data-stu-id="63cea-122">This example shows how to use `Get-Date` to get either the date or time element.</span></span> <span data-ttu-id="63cea-123">參數會使用引數 **Date** 、 **Time** 或 **DateTime** 。</span><span class="sxs-lookup"><span data-stu-id="63cea-123">The parameter uses the arguments **Date** , **Time** , or **DateTime** .</span></span>

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

<span data-ttu-id="63cea-124">`Get-Date` 使用 **DisplayHint** 參數搭配 **date** 引數，以只取得日期。</span><span class="sxs-lookup"><span data-stu-id="63cea-124">`Get-Date` uses the **DisplayHint** parameter with the **Date** argument to get only the date.</span></span>

### <span data-ttu-id="63cea-125">範例3：使用 .NET 格式規範取得日期和時間</span><span class="sxs-lookup"><span data-stu-id="63cea-125">Example 3: Get the date and time with a .NET format specifier</span></span>

<span data-ttu-id="63cea-126">在此範例中，會使用 .NET 格式規範來自訂輸出的格式。</span><span class="sxs-lookup"><span data-stu-id="63cea-126">In this example, a .NET format specifier is used to customize the output's format.</span></span> <span data-ttu-id="63cea-127">輸出是 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="63cea-127">The output is a **String** object.</span></span>

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

<span data-ttu-id="63cea-128">`Get-Date` 使用 **Format** 參數來指定數個格式規範。</span><span class="sxs-lookup"><span data-stu-id="63cea-128">`Get-Date` uses the **Format** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="63cea-129">此範例中使用的 .NET 格式規範定義如下：</span><span class="sxs-lookup"><span data-stu-id="63cea-129">The .NET format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="63cea-130">規範</span><span class="sxs-lookup"><span data-stu-id="63cea-130">Specifier</span></span> |                      <span data-ttu-id="63cea-131">定義</span><span class="sxs-lookup"><span data-stu-id="63cea-131">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `dddd`    | <span data-ttu-id="63cea-132">一周中的日-完整名稱</span><span class="sxs-lookup"><span data-stu-id="63cea-132">Day of the week - full name</span></span>                           |
| `MM`      | <span data-ttu-id="63cea-133">月份數</span><span class="sxs-lookup"><span data-stu-id="63cea-133">Month number</span></span>                                          |
| `dd`      | <span data-ttu-id="63cea-134">月中的日-2 位數</span><span class="sxs-lookup"><span data-stu-id="63cea-134">Day of the month - 2 digits</span></span>                           |
| `yyyy`    | <span data-ttu-id="63cea-135">以4位數格式表示的年份</span><span class="sxs-lookup"><span data-stu-id="63cea-135">Year in 4-digit format</span></span>                                |
| `HH:mm`   | <span data-ttu-id="63cea-136">時間（24小時制）-無秒數</span><span class="sxs-lookup"><span data-stu-id="63cea-136">Time in 24-hour format - no seconds</span></span>                    |
| `K`       | <span data-ttu-id="63cea-137">從通用時間座標 (UTC) 的時區位移</span><span class="sxs-lookup"><span data-stu-id="63cea-137">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="63cea-138">如需 .NET 格式規範的詳細資訊，請參閱 [自訂日期和時間格式字串](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)。</span><span class="sxs-lookup"><span data-stu-id="63cea-138">For more information about .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

### <span data-ttu-id="63cea-139">範例4：取得 UFormat 規範的日期和時間</span><span class="sxs-lookup"><span data-stu-id="63cea-139">Example 4: Get the date and time with a UFormat specifier</span></span>

<span data-ttu-id="63cea-140">在此範例中，會使用數個 **UFormat** 格式規範來自訂輸出的格式。</span><span class="sxs-lookup"><span data-stu-id="63cea-140">In this example, several **UFormat** format specifiers are used to customize the output's format.</span></span>
<span data-ttu-id="63cea-141">輸出是 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="63cea-141">The output is a **String** object.</span></span>

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

<span data-ttu-id="63cea-142">`Get-Date` 使用 **UFormat** 參數來指定數個格式規範。</span><span class="sxs-lookup"><span data-stu-id="63cea-142">`Get-Date` uses the **UFormat** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="63cea-143">此範例中使用的 **UFormat** 格式規範定義如下：</span><span class="sxs-lookup"><span data-stu-id="63cea-143">The **UFormat** format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="63cea-144">規範</span><span class="sxs-lookup"><span data-stu-id="63cea-144">Specifier</span></span> |                      <span data-ttu-id="63cea-145">定義</span><span class="sxs-lookup"><span data-stu-id="63cea-145">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `%A`      | <span data-ttu-id="63cea-146">一周中的日-完整名稱</span><span class="sxs-lookup"><span data-stu-id="63cea-146">Day of the week - full name</span></span>                           |
| `%m`      | <span data-ttu-id="63cea-147">月份數</span><span class="sxs-lookup"><span data-stu-id="63cea-147">Month number</span></span>                                          |
| `%d`      | <span data-ttu-id="63cea-148">月中的日-2 位數</span><span class="sxs-lookup"><span data-stu-id="63cea-148">Day of the month - 2 digits</span></span>                           |
| `%Y`      | <span data-ttu-id="63cea-149">以4位數格式表示的年份</span><span class="sxs-lookup"><span data-stu-id="63cea-149">Year in 4-digit format</span></span>                                |
| `%R`      | <span data-ttu-id="63cea-150">時間（24小時制）-無秒數</span><span class="sxs-lookup"><span data-stu-id="63cea-150">Time in 24-hour format - no seconds</span></span>                    |
| `%Z`      | <span data-ttu-id="63cea-151">從通用時間座標 (UTC) 的時區位移</span><span class="sxs-lookup"><span data-stu-id="63cea-151">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="63cea-152">如需有效 **UFormat** 格式規範的清單，請參閱 [附注](#notes) 一節。</span><span class="sxs-lookup"><span data-stu-id="63cea-152">For a list of valid **UFormat** format specifiers, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="63cea-153">範例5：取得一年中的日期日</span><span class="sxs-lookup"><span data-stu-id="63cea-153">Example 5: Get a date's day of the year</span></span>

<span data-ttu-id="63cea-154">在此範例中，屬性是用來取得年度的數位日。</span><span class="sxs-lookup"><span data-stu-id="63cea-154">In this example, a property is used to get the numeric day of the year.</span></span>

<span data-ttu-id="63cea-155">西曆有365天，但有366天的閏年度除外。</span><span class="sxs-lookup"><span data-stu-id="63cea-155">The Gregorian calendar has 365 days, except for leap years that have 366 days.</span></span> <span data-ttu-id="63cea-156">例如，2020年12月31日是第366天。</span><span class="sxs-lookup"><span data-stu-id="63cea-156">For example, December 31, 2020 is day 366.</span></span>

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

<span data-ttu-id="63cea-157">`Get-Date` 使用三個參數來指定日期： **Year** 、 **Month** 和 **Day** 。</span><span class="sxs-lookup"><span data-stu-id="63cea-157">`Get-Date` uses three parameters to specify the date: **Year** , **Month** , and **Day** .</span></span> <span data-ttu-id="63cea-158">此命令會以括弧括住，以便 **DayofYear** 屬性評估結果。</span><span class="sxs-lookup"><span data-stu-id="63cea-158">The command is wrapped with parentheses so that the result is evaluated by the **DayofYear** property.</span></span>

### <span data-ttu-id="63cea-159">範例6：檢查是否已針對日光節約時間調整日期</span><span class="sxs-lookup"><span data-stu-id="63cea-159">Example 6: Check if a date is adjusted for daylight savings time</span></span>

<span data-ttu-id="63cea-160">此範例會使用布林方法，以確認日期是否以日光節約時間進行調整。</span><span class="sxs-lookup"><span data-stu-id="63cea-160">This example uses a boolean method to verify if a date is adjusted by daylight savings time.</span></span>

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

<span data-ttu-id="63cea-161">變數會 `$DST` 儲存的結果 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="63cea-161">A variable, `$DST` stores the result of `Get-Date`.</span></span> <span data-ttu-id="63cea-162">`$DST` 使用 **IsDaylightSavingTime** 方法來測試是否針對日光節約時間調整日期。</span><span class="sxs-lookup"><span data-stu-id="63cea-162">`$DST` uses the **IsDaylightSavingTime** method to test if the date is adjusted for daylight savings time.</span></span>

### <span data-ttu-id="63cea-163">範例7：將目前時間轉換成 UTC 時間</span><span class="sxs-lookup"><span data-stu-id="63cea-163">Example 7: Convert the current time to UTC time</span></span>

<span data-ttu-id="63cea-164">在此範例中，目前的時間會轉換成 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-164">In this example, the current time is converted to UTC time.</span></span> <span data-ttu-id="63cea-165">系統地區設定的 UTC 時差會用來轉換時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-165">The UTC offset for the system's locale is used to convert the time.</span></span> <span data-ttu-id="63cea-166">[ [附注](#notes) ] 區段中的資料表會列出有效的 **UFormat** 格式規範。</span><span class="sxs-lookup"><span data-stu-id="63cea-166">A table in the [Notes](#notes) section lists the valid **UFormat** format specifiers.</span></span>

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

<span data-ttu-id="63cea-167">`Get-Date` 使用 **UFormat** 參數搭配格式規範，以顯示目前的系統日期和時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-167">`Get-Date` uses the **UFormat** parameter with format specifiers to display the current system date and time.</span></span> <span data-ttu-id="63cea-168">格式規範 **% Z** 代表 **-07** 的 UTC 時差。</span><span class="sxs-lookup"><span data-stu-id="63cea-168">The format specifier **%Z** represents the UTC offset of **-07** .</span></span>

<span data-ttu-id="63cea-169">`$Time`變數會儲存目前的系統日期和時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-169">The `$Time` variable stores the current system date and time.</span></span> <span data-ttu-id="63cea-170">`$Time` 使用 **>datetime.touniversaltime ( # B1** 方法，根據電腦的 UTC 時差來轉換時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-170">`$Time` uses the **ToUniversalTime()** method to convert the time based on the computer's UTC offset.</span></span>

### <span data-ttu-id="63cea-171">範例8：建立時間戳記</span><span class="sxs-lookup"><span data-stu-id="63cea-171">Example 8: Create a timestamp</span></span>

<span data-ttu-id="63cea-172">在此範例中，格式規範會建立目錄名稱的時間戳記 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="63cea-172">In this example, a format specifier creates a timestamp **String** object for a directory name.</span></span> <span data-ttu-id="63cea-173">時間戳記包含日期、時間和 UTC 時差。</span><span class="sxs-lookup"><span data-stu-id="63cea-173">The timestamp includes the date, time, and UTC offset.</span></span>

```powershell
$timestamp = Get-Date -Format o | ForEach-Object { $_ -replace ":", "." }
New-Item -Path C:\Test\$timestamp -Type Directory
```

```Output
Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         6/27/2019    07:59                2019-06-27T07.59.24.4603750-07.00
```

<span data-ttu-id="63cea-174">`$timestamp`變數會儲存命令的結果 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="63cea-174">The `$timestamp` variable stores the results of a `Get-Date` command.</span></span> <span data-ttu-id="63cea-175">`Get-Date` 使用 **格式** 參數搭配小寫的格式規範 `o` 來建立時間戳記 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="63cea-175">`Get-Date` uses the **Format** parameter with the format specifier of lowercase `o` to create a timestamp **String** object.</span></span> <span data-ttu-id="63cea-176">物件會向下傳送到管線 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="63cea-176">The object is sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="63cea-177">**ScriptBlock** 包含 `$_` 表示目前管線物件的變數。</span><span class="sxs-lookup"><span data-stu-id="63cea-177">A **ScriptBlock** contains the `$_` variable that represents the current pipeline object.</span></span> <span data-ttu-id="63cea-178">時間戳記字串是由以句號取代的冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="63cea-178">The timestamp string is delimited by colons that are replaced by periods.</span></span>

<span data-ttu-id="63cea-179">`New-Item` 使用 **Path** 參數指定新目錄的位置。</span><span class="sxs-lookup"><span data-stu-id="63cea-179">`New-Item` uses the **Path** parameter to specify the location for a new directory.</span></span> <span data-ttu-id="63cea-180">路徑包含 `$timestamp` 變數做為目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="63cea-180">The path includes the `$timestamp` variable as the directory name.</span></span> <span data-ttu-id="63cea-181">**Type** 參數會指定建立目錄。</span><span class="sxs-lookup"><span data-stu-id="63cea-181">The **Type** parameter specifies that a directory is created.</span></span>

### <span data-ttu-id="63cea-182">範例9：轉換 Unix 時間戳記</span><span class="sxs-lookup"><span data-stu-id="63cea-182">Example 9: Convert a Unix timestamp</span></span>

<span data-ttu-id="63cea-183">此範例會將 Unix 時間 (以 1970-01-01 0:00:00) 到 DateTime 之後的秒數表示。</span><span class="sxs-lookup"><span data-stu-id="63cea-183">This example converts a Unix time (represented by the number of seconds since 1970-01-01 0:00:00) to DateTime.</span></span>

```powershell
Get-Date -UnixTimeSeconds 1577836800
```

```Output
Wednesday, January 01, 2020 12:00:00 AM
```

### <span data-ttu-id="63cea-184">範例10：傳回以 UTC 格式轉譯的日期值</span><span class="sxs-lookup"><span data-stu-id="63cea-184">Example 10: Return a date value interpreted as UTC</span></span>

<span data-ttu-id="63cea-185">此範例示範如何將日期值解讀為其對等的 UTC。</span><span class="sxs-lookup"><span data-stu-id="63cea-185">This example shows how to interpret a date value as its UTC equivalent.</span></span> <span data-ttu-id="63cea-186">在此範例中，此機器設定為 **太平洋標準時間** 。</span><span class="sxs-lookup"><span data-stu-id="63cea-186">For the example, this machine is set to **Pacific Standard Time** .</span></span> <span data-ttu-id="63cea-187">根據預設， `Get-Date` 會傳回該時區的值。</span><span class="sxs-lookup"><span data-stu-id="63cea-187">By default, `Get-Date` returns values for that timezone.</span></span> <span data-ttu-id="63cea-188">使用 **AsUTC** 參數將值轉換為 UTC 相等時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-188">Use the **AsUTC** parameter to convert the value to the UTC equivalent time.</span></span>

```powershell
PS> Get-TimeZone

Id                         : Pacific Standard Time
DisplayName                : (UTC-08:00) Pacific Time (US & Canada)
StandardName               : Pacific Standard Time
DaylightName               : Pacific Daylight Time
BaseUtcOffset              : -08:00:00
SupportsDaylightSavingTime : True

PS> (Get-Date -Date "2020-01-01T00:00:00").Kind
Unspecified

PS> Get-Date -Date "2020-01-01T00:00:00"

Wednesday, January 1, 2020 12:00:00 AM

PS> (Get-Date -Date "2020-01-01T00:00:00" -AsUTC).Kind
Utc

PS> Get-Date -Date "2020-01-01T00:00:00" -AsUTC

Wednesday, January 1, 2020 8:00:00 AM
```

## <span data-ttu-id="63cea-189">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="63cea-189">PARAMETERS</span></span>

### <span data-ttu-id="63cea-190">-AsUTC</span><span class="sxs-lookup"><span data-stu-id="63cea-190">-AsUTC</span></span>

<span data-ttu-id="63cea-191">將日期值轉換為 UTC 格式的相等時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-191">Converts the date value to the equivalent time in UTC.</span></span>

<span data-ttu-id="63cea-192">此參數是在 PowerShell 7.1 中引進。</span><span class="sxs-lookup"><span data-stu-id="63cea-192">This parameter was introduced in PowerShell 7.1.</span></span>

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

### <span data-ttu-id="63cea-193">-Date</span><span class="sxs-lookup"><span data-stu-id="63cea-193">-Date</span></span>

<span data-ttu-id="63cea-194">指定日期和時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-194">Specifies a date and time.</span></span> <span data-ttu-id="63cea-195">Time 是選擇性的，如果未指定，則會傳回00:00:00。</span><span class="sxs-lookup"><span data-stu-id="63cea-195">Time is optional and if not specified, returns 00:00:00.</span></span>

<span data-ttu-id="63cea-196">以系統地區設定的標準格式輸入日期和時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-196">Enter the date and time in a format that is standard for the system locale.</span></span>

<span data-ttu-id="63cea-197">例如，在美式英文中：</span><span class="sxs-lookup"><span data-stu-id="63cea-197">For example, in US English:</span></span>

<span data-ttu-id="63cea-198">`Get-Date -Date "6/25/2019 12:30:22"` 傳回2019年6月25日星期二的12:30:22</span><span class="sxs-lookup"><span data-stu-id="63cea-198">`Get-Date -Date "6/25/2019 12:30:22"` returns Tuesday, June 25, 2019 12:30:22</span></span>

```yaml
Type: System.DateTime
Parameter Sets: DateAndFormat, DateAndUFormat
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="63cea-199">-日</span><span class="sxs-lookup"><span data-stu-id="63cea-199">-Day</span></span>

<span data-ttu-id="63cea-200">指定要顯示的月份日期。</span><span class="sxs-lookup"><span data-stu-id="63cea-200">Specifies the day of the month that is displayed.</span></span> <span data-ttu-id="63cea-201">輸入從 1 到 31 的值。</span><span class="sxs-lookup"><span data-stu-id="63cea-201">Enter a value from 1 to 31.</span></span>

<span data-ttu-id="63cea-202">如果指定的值大於一個月中的天數，則 PowerShell 會將天數加上月份。</span><span class="sxs-lookup"><span data-stu-id="63cea-202">If the specified value is greater than the number of days in a month, PowerShell adds the number of days to the month.</span></span> <span data-ttu-id="63cea-203">例如， `Get-Date -Month 2 -Day 31` 顯示 3 **月 3** 日，而不是 **2 月31日** 。</span><span class="sxs-lookup"><span data-stu-id="63cea-203">For example, `Get-Date -Month 2 -Day 31` displays **March 3** , not **February 31** .</span></span>

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

### <span data-ttu-id="63cea-204">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="63cea-204">-DisplayHint</span></span>

<span data-ttu-id="63cea-205">決定要顯示日期和時間的哪些元素。</span><span class="sxs-lookup"><span data-stu-id="63cea-205">Determines which elements of the date and time are displayed.</span></span>

<span data-ttu-id="63cea-206">接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="63cea-206">The accepted values are as follows:</span></span>

- <span data-ttu-id="63cea-207">**Date** ：只顯示日期</span><span class="sxs-lookup"><span data-stu-id="63cea-207">**Date** : displays only the date</span></span>
- <span data-ttu-id="63cea-208">**時間** ：只顯示時間</span><span class="sxs-lookup"><span data-stu-id="63cea-208">**Time** : displays only the time</span></span>
- <span data-ttu-id="63cea-209">**DateTime** ：顯示日期和時間</span><span class="sxs-lookup"><span data-stu-id="63cea-209">**DateTime** : displays the date and time</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63cea-210">-Format</span><span class="sxs-lookup"><span data-stu-id="63cea-210">-Format</span></span>

<span data-ttu-id="63cea-211">使用格式規範所指定的 Microsoft .NET Framework 格式來顯示日期和時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-211">Displays the date and time in the Microsoft .NET Framework format indicated by the format specifier.</span></span>
<span data-ttu-id="63cea-212">**Format** 參數會輸出 **String** 物件。</span><span class="sxs-lookup"><span data-stu-id="63cea-212">The **Format** parameter outputs a **String** object.</span></span>

<span data-ttu-id="63cea-213">如需可用 .NET 格式規範的清單，請參閱 [自訂日期和時間格式字串](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)。</span><span class="sxs-lookup"><span data-stu-id="63cea-213">For a list of available .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

<span data-ttu-id="63cea-214">使用 **Format** 參數時，只會 `Get-Date` 取得顯示日期所需的 **DateTime** 物件屬性。</span><span class="sxs-lookup"><span data-stu-id="63cea-214">When the **Format** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="63cea-215">如此一來， **DateTime** 物件的部分屬性和方法可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="63cea-215">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

<span data-ttu-id="63cea-216">從 PowerShell 5.0 開始，您可以使用下列其他格式作為 **Format** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="63cea-216">Starting in PowerShell 5.0, you can use the following additional formats as values for the **Format** parameter.</span></span>

- <span data-ttu-id="63cea-217">**FileDate** 。</span><span class="sxs-lookup"><span data-stu-id="63cea-217">**FileDate** .</span></span> <span data-ttu-id="63cea-218">以本機時程表示的目前日期的檔案或路徑易記表示。</span><span class="sxs-lookup"><span data-stu-id="63cea-218">A file or path-friendly representation of the current date in local time.</span></span> <span data-ttu-id="63cea-219">格式 `yyyyMMdd` (區分大小寫，使用4位數年份、2位數月份和2位數的日) 。</span><span class="sxs-lookup"><span data-stu-id="63cea-219">The format is `yyyyMMdd` (case-sensitive, using a 4-digit year, 2-digit month, and 2-digit day).</span></span> <span data-ttu-id="63cea-220">例如：</span><span class="sxs-lookup"><span data-stu-id="63cea-220">For example:</span></span>
  20190627.

- <span data-ttu-id="63cea-221">**FileDateUniversal** 。</span><span class="sxs-lookup"><span data-stu-id="63cea-221">**FileDateUniversal** .</span></span> <span data-ttu-id="63cea-222">以通用時程表示的目前日期的檔案或路徑易記表示 (UTC) 。</span><span class="sxs-lookup"><span data-stu-id="63cea-222">A file or path-friendly representation of the current date in universal time (UTC).</span></span> <span data-ttu-id="63cea-223">格式 `yyyyMMddZ` (區分大小寫，使用4位數的年份、2位數的月份、2位數的日期，以及 `Z` 做為 UTC 指標) 的字母。</span><span class="sxs-lookup"><span data-stu-id="63cea-223">The format is `yyyyMMddZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="63cea-224">例如：20190627Z。</span><span class="sxs-lookup"><span data-stu-id="63cea-224">For example: 20190627Z.</span></span>

- <span data-ttu-id="63cea-225">**FileDateTime** 。</span><span class="sxs-lookup"><span data-stu-id="63cea-225">**FileDateTime** .</span></span> <span data-ttu-id="63cea-226">以24小時制格式，以本機時程表示的目前日期和時間的檔案或路徑易記表示。</span><span class="sxs-lookup"><span data-stu-id="63cea-226">A file or path-friendly representation of the current date and time in local time, in 24-hour format.</span></span> <span data-ttu-id="63cea-227">格式 `yyyyMMddTHHmmssffff` (區分大小寫、使用4位數的年份、2位數的月份、2位數的日期、 `T` 以時間分隔符號表示的字母、2位數的小時、2位數分鐘、2位數的秒數，以及4位數的毫秒) 。</span><span class="sxs-lookup"><span data-stu-id="63cea-227">The format is `yyyyMMddTHHmmssffff` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, and 4-digit millisecond).</span></span> <span data-ttu-id="63cea-228">例如：20190627T0840107271。</span><span class="sxs-lookup"><span data-stu-id="63cea-228">For example: 20190627T0840107271.</span></span>

- <span data-ttu-id="63cea-229">**FileDateTimeUniversal** 。</span><span class="sxs-lookup"><span data-stu-id="63cea-229">**FileDateTimeUniversal** .</span></span> <span data-ttu-id="63cea-230">以24小時格式表示的目前日期和時間的檔案或路徑易記標記法 (UTC) 。</span><span class="sxs-lookup"><span data-stu-id="63cea-230">A file or path-friendly representation of the current date and time in universal time (UTC), in 24-hour format.</span></span> <span data-ttu-id="63cea-231">格式 `yyyyMMddTHHmmssffffZ` (區分大小寫、使用4位數的年份、2位數的月份、2位數的日期、 `T` 以時間分隔符號表示的字母、2位數的小時、2位數分鐘、2位數秒、4位數毫秒，以及 `Z` 做為 UTC 指標) 的字母。</span><span class="sxs-lookup"><span data-stu-id="63cea-231">The format is `yyyyMMddTHHmmssffffZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, 4-digit millisecond, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="63cea-232">例如：20190627T1540500718Z。</span><span class="sxs-lookup"><span data-stu-id="63cea-232">For example: 20190627T1540500718Z.</span></span>

```yaml
Type: System.String
Parameter Sets: DateAndFormat, UnixTimeSecondsAndFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63cea-233">-小時</span><span class="sxs-lookup"><span data-stu-id="63cea-233">-Hour</span></span>

<span data-ttu-id="63cea-234">指定要顯示的小時。</span><span class="sxs-lookup"><span data-stu-id="63cea-234">Specifies the hour that is displayed.</span></span> <span data-ttu-id="63cea-235">輸入0到23之間的值。</span><span class="sxs-lookup"><span data-stu-id="63cea-235">Enter a value from 0 to 23.</span></span>

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

### <span data-ttu-id="63cea-236">-毫秒</span><span class="sxs-lookup"><span data-stu-id="63cea-236">-Millisecond</span></span>

<span data-ttu-id="63cea-237">指定日期中的毫秒。</span><span class="sxs-lookup"><span data-stu-id="63cea-237">Specifies the milliseconds in the date.</span></span> <span data-ttu-id="63cea-238">輸入0到999的值。</span><span class="sxs-lookup"><span data-stu-id="63cea-238">Enter a value from 0 to 999.</span></span>

<span data-ttu-id="63cea-239">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="63cea-239">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="63cea-240">-分鐘</span><span class="sxs-lookup"><span data-stu-id="63cea-240">-Minute</span></span>

<span data-ttu-id="63cea-241">指定要顯示的分鐘。</span><span class="sxs-lookup"><span data-stu-id="63cea-241">Specifies the minute that is displayed.</span></span> <span data-ttu-id="63cea-242">輸入0到59的值。</span><span class="sxs-lookup"><span data-stu-id="63cea-242">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="63cea-243">-月</span><span class="sxs-lookup"><span data-stu-id="63cea-243">-Month</span></span>

<span data-ttu-id="63cea-244">指定要顯示的月份。</span><span class="sxs-lookup"><span data-stu-id="63cea-244">Specifies the month that is displayed.</span></span> <span data-ttu-id="63cea-245">輸入1到12的值。</span><span class="sxs-lookup"><span data-stu-id="63cea-245">Enter a value from 1 to 12.</span></span>

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

### <span data-ttu-id="63cea-246">-秒</span><span class="sxs-lookup"><span data-stu-id="63cea-246">-Second</span></span>

<span data-ttu-id="63cea-247">指定要顯示的秒。</span><span class="sxs-lookup"><span data-stu-id="63cea-247">Specifies the second that is displayed.</span></span> <span data-ttu-id="63cea-248">輸入0到59的值。</span><span class="sxs-lookup"><span data-stu-id="63cea-248">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="63cea-249">-UFormat</span><span class="sxs-lookup"><span data-stu-id="63cea-249">-UFormat</span></span>

<span data-ttu-id="63cea-250">使用 UNIX 格式顯示日期和時間。</span><span class="sxs-lookup"><span data-stu-id="63cea-250">Displays the date and time in UNIX format.</span></span> <span data-ttu-id="63cea-251">**UFormat** 參數會輸出字串物件。</span><span class="sxs-lookup"><span data-stu-id="63cea-251">The **UFormat** parameter outputs a string object.</span></span>

<span data-ttu-id="63cea-252">**UFormat** 規範的前面會加上百分比符號 (`%`) ，例如、 `%m` `%d` 和 `%Y` 。</span><span class="sxs-lookup"><span data-stu-id="63cea-252">**UFormat** specifiers are preceded by a percent sign (`%`), for example, `%m`, `%d`, and `%Y`.</span></span> <span data-ttu-id="63cea-253">[附注](#notes)區段包含有效 **UFormat** 規範的資料表。</span><span class="sxs-lookup"><span data-stu-id="63cea-253">The [Notes](#notes) section contains a table of valid **UFormat specifiers** .</span></span>

<span data-ttu-id="63cea-254">使用 **UFormat** 參數時，只會 `Get-Date` 取得顯示日期所需的 **DateTime** 物件屬性。</span><span class="sxs-lookup"><span data-stu-id="63cea-254">When the **UFormat** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="63cea-255">如此一來， **DateTime** 物件的部分屬性和方法可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="63cea-255">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

```yaml
Type: System.String
Parameter Sets: DateAndUFormat, UnixTimeSecondsAndUFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63cea-256">-UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="63cea-256">-UnixTimeSeconds</span></span>

<span data-ttu-id="63cea-257">自1970年1月1日起，0:00:00 起的日期和時間，以秒為單位。</span><span class="sxs-lookup"><span data-stu-id="63cea-257">Date and time represented in seconds since January 1, 1970, 0:00:00.</span></span>

<span data-ttu-id="63cea-258">此參數是在 PowerShell 7.1 中引進。</span><span class="sxs-lookup"><span data-stu-id="63cea-258">This parameter was introduced in PowerShell 7.1.</span></span>

```yaml
Type: System.Int64
Parameter Sets: UnixTimeSecondsAndFormat, UnixTimeSecondsAndUFormat
Aliases: UnixTime

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="63cea-259">-年</span><span class="sxs-lookup"><span data-stu-id="63cea-259">-Year</span></span>

<span data-ttu-id="63cea-260">指定要顯示的年份。</span><span class="sxs-lookup"><span data-stu-id="63cea-260">Specifies the year that is displayed.</span></span> <span data-ttu-id="63cea-261">輸入從1到9999的值。</span><span class="sxs-lookup"><span data-stu-id="63cea-261">Enter a value from 1 to 9999.</span></span>

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

### <span data-ttu-id="63cea-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="63cea-262">CommonParameters</span></span>

<span data-ttu-id="63cea-263">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="63cea-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="63cea-264">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="63cea-264">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="63cea-265">輸入</span><span class="sxs-lookup"><span data-stu-id="63cea-265">INPUTS</span></span>

### <span data-ttu-id="63cea-266">管線輸入</span><span class="sxs-lookup"><span data-stu-id="63cea-266">Pipeline input</span></span>

<span data-ttu-id="63cea-267">`Get-Date` 接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="63cea-267">`Get-Date` accepts pipeline input.</span></span> <span data-ttu-id="63cea-268">例如： `Get-ChildItem | Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="63cea-268">For example, `Get-ChildItem | Get-Date`.</span></span>

## <span data-ttu-id="63cea-269">輸出</span><span class="sxs-lookup"><span data-stu-id="63cea-269">OUTPUTS</span></span>

### <span data-ttu-id="63cea-270">System.string 或 System.string</span><span class="sxs-lookup"><span data-stu-id="63cea-270">System.DateTime or System.String</span></span>

<span data-ttu-id="63cea-271">`Get-Date` 傳回 **DateTime** 物件，但使用 **Format** 和 **UFormat** 參數時除外。</span><span class="sxs-lookup"><span data-stu-id="63cea-271">`Get-Date` returns a **DateTime** object except when the **Format** and **UFormat** parameters are used.</span></span> <span data-ttu-id="63cea-272">**Format** 或 **UFormat** 參數會傳回 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="63cea-272">The **Format** or **UFormat** parameters return **String** objects.</span></span>

<span data-ttu-id="63cea-273">將 **DateTime** 物件向下傳送至 `Add-Content` 需要字串輸入的 Cmdlet 時，PowerShell 會將物件轉換成 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="63cea-273">When a **DateTime** object is sent down the pipeline to a cmdlet such as `Add-Content` that expects string input, PowerShell converts the object to a **String** object.</span></span>

<span data-ttu-id="63cea-274">方法會 `(Get-Date).ToString()` 將 **DateTime** 物件轉換成 **String** 物件。</span><span class="sxs-lookup"><span data-stu-id="63cea-274">The method `(Get-Date).ToString()` converts a **DateTime** object a **String** object.</span></span>

<span data-ttu-id="63cea-275">若要顯示物件的屬性和方法，請將物件沿著管線向下傳送至 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="63cea-275">To display an object's properties and methods, send the object down the pipeline to `Get-Member`.</span></span>
<span data-ttu-id="63cea-276">例如： `Get-Date | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="63cea-276">For example, `Get-Date | Get-Member`.</span></span>

## <span data-ttu-id="63cea-277">注意</span><span class="sxs-lookup"><span data-stu-id="63cea-277">NOTES</span></span>

<span data-ttu-id="63cea-278">**DateTime** 物件是適用于系統地區設定的完整日期和完整時間格式。</span><span class="sxs-lookup"><span data-stu-id="63cea-278">**DateTime** objects are in long-date and long-time formats for the system locale.</span></span>

<span data-ttu-id="63cea-279">有效的 **UFormat** 規範會顯示在下表中：</span><span class="sxs-lookup"><span data-stu-id="63cea-279">The valid **UFormat specifiers** are displayed in the following table:</span></span>

| <span data-ttu-id="63cea-280">格式規範</span><span class="sxs-lookup"><span data-stu-id="63cea-280">Format specifier</span></span> |                                 <span data-ttu-id="63cea-281">意義</span><span class="sxs-lookup"><span data-stu-id="63cea-281">Meaning</span></span>                     |         <span data-ttu-id="63cea-282">範例</span><span class="sxs-lookup"><span data-stu-id="63cea-282">Example</span></span>          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | <span data-ttu-id="63cea-283">一周中的日-完整名稱</span><span class="sxs-lookup"><span data-stu-id="63cea-283">Day of the week - full name</span></span>                                             | <span data-ttu-id="63cea-284">星期一</span><span class="sxs-lookup"><span data-stu-id="63cea-284">Monday</span></span>                   |
| `%a` | <span data-ttu-id="63cea-285">一周中的日-縮寫名稱</span><span class="sxs-lookup"><span data-stu-id="63cea-285">Day of the week - abbreviated name</span></span>                                      | <span data-ttu-id="63cea-286">Mon</span><span class="sxs-lookup"><span data-stu-id="63cea-286">Mon</span></span>                      |
| `%B` | <span data-ttu-id="63cea-287">月份名稱-完整</span><span class="sxs-lookup"><span data-stu-id="63cea-287">Month name - full</span></span>                                                       | <span data-ttu-id="63cea-288">一月</span><span class="sxs-lookup"><span data-stu-id="63cea-288">January</span></span>                  |
| `%b` | <span data-ttu-id="63cea-289">月份名稱-縮寫</span><span class="sxs-lookup"><span data-stu-id="63cea-289">Month name - abbreviated</span></span>                                                | <span data-ttu-id="63cea-290">一月</span><span class="sxs-lookup"><span data-stu-id="63cea-290">Jan</span></span>                      |
| `%C` | <span data-ttu-id="63cea-291">世紀</span><span class="sxs-lookup"><span data-stu-id="63cea-291">Century</span></span>                                                                 | <span data-ttu-id="63cea-292">20適用于2019</span><span class="sxs-lookup"><span data-stu-id="63cea-292">20 for 2019</span></span>              |
| `%c` | <span data-ttu-id="63cea-293">日期和時間-縮寫</span><span class="sxs-lookup"><span data-stu-id="63cea-293">Date and time - abbreviated</span></span>                                             | <span data-ttu-id="63cea-294">星期四6月 27 08:44:18 2019</span><span class="sxs-lookup"><span data-stu-id="63cea-294">Thu Jun 27 08:44:18 2019</span></span> |
| `%D` | <span data-ttu-id="63cea-295">日期（mm/dd/yy 格式）</span><span class="sxs-lookup"><span data-stu-id="63cea-295">Date in mm/dd/yy format</span></span>                                                 | <span data-ttu-id="63cea-296">06/27/19</span><span class="sxs-lookup"><span data-stu-id="63cea-296">06/27/19</span></span>                 |
| `%d` | <span data-ttu-id="63cea-297">月中的日-2 位數</span><span class="sxs-lookup"><span data-stu-id="63cea-297">Day of the month - 2 digits</span></span>                                             | <span data-ttu-id="63cea-298">05</span><span class="sxs-lookup"><span data-stu-id="63cea-298">05</span></span>                       |
| `%e` | <span data-ttu-id="63cea-299">月份中的日期-前面加上空格的數位</span><span class="sxs-lookup"><span data-stu-id="63cea-299">Day of the month - digit preceded by a space</span></span>                            | <span data-ttu-id="63cea-300">\<space\>.5</span><span class="sxs-lookup"><span data-stu-id="63cea-300">\<space\>5</span></span>               |
| `%F` | <span data-ttu-id="63cea-301">以 YYYY-MM-DD 格式的日期（等於% Y-% m-% d） (ISO 8601 日期格式) </span><span class="sxs-lookup"><span data-stu-id="63cea-301">Date in YYYY-mm-dd format, equal to %Y-%m-%d (the ISO 8601 date format)</span></span> | <span data-ttu-id="63cea-302">2019-06-27</span><span class="sxs-lookup"><span data-stu-id="63cea-302">2019-06-27</span></span>               |
| `%G` | <span data-ttu-id="63cea-303">與 ' Y ' 相同</span><span class="sxs-lookup"><span data-stu-id="63cea-303">Same as 'Y'</span></span>                                                             |                          |
| `%g` | <span data-ttu-id="63cea-304">與 ' y ' 相同</span><span class="sxs-lookup"><span data-stu-id="63cea-304">Same as 'y'</span></span>                                                             |                          |
| `%H` | <span data-ttu-id="63cea-305">24小時制的小時</span><span class="sxs-lookup"><span data-stu-id="63cea-305">Hour in 24-hour format</span></span>                                                  | <span data-ttu-id="63cea-306">17</span><span class="sxs-lookup"><span data-stu-id="63cea-306">17</span></span>                       |
| `%h` | <span data-ttu-id="63cea-307">與 ' b ' 相同</span><span class="sxs-lookup"><span data-stu-id="63cea-307">Same as 'b'</span></span>                                                             |                          |
| `%I` | <span data-ttu-id="63cea-308">12小時制的小時格式</span><span class="sxs-lookup"><span data-stu-id="63cea-308">Hour in 12-hour format</span></span>                                                  | <span data-ttu-id="63cea-309">05</span><span class="sxs-lookup"><span data-stu-id="63cea-309">05</span></span>                       |
| `%j` | <span data-ttu-id="63cea-310">年中的日</span><span class="sxs-lookup"><span data-stu-id="63cea-310">Day of the year</span></span>                                                         | <span data-ttu-id="63cea-311">1-366</span><span class="sxs-lookup"><span data-stu-id="63cea-311">1-366</span></span>                    |
| `%k` | <span data-ttu-id="63cea-312">與 ' H ' 相同</span><span class="sxs-lookup"><span data-stu-id="63cea-312">Same as 'H'</span></span>                                                             |                          |
| `%l` | <span data-ttu-id="63cea-313">與「I」相同 (我) </span><span class="sxs-lookup"><span data-stu-id="63cea-313">Same as 'I' (Upper-case I)</span></span>                                              | <span data-ttu-id="63cea-314">05</span><span class="sxs-lookup"><span data-stu-id="63cea-314">05</span></span>                       |
| `%M` | <span data-ttu-id="63cea-315">分鐘</span><span class="sxs-lookup"><span data-stu-id="63cea-315">Minutes</span></span>                                                                 | <span data-ttu-id="63cea-316">35</span><span class="sxs-lookup"><span data-stu-id="63cea-316">35</span></span>                       |
| `%m` | <span data-ttu-id="63cea-317">月份數</span><span class="sxs-lookup"><span data-stu-id="63cea-317">Month number</span></span>                                                            | <span data-ttu-id="63cea-318">06</span><span class="sxs-lookup"><span data-stu-id="63cea-318">06</span></span>                       |
| `%n` | <span data-ttu-id="63cea-319">換行字元</span><span class="sxs-lookup"><span data-stu-id="63cea-319">newline character</span></span>                                                       |                          |
| `%p` | <span data-ttu-id="63cea-320">AM 或 PM</span><span class="sxs-lookup"><span data-stu-id="63cea-320">AM or PM</span></span>                                                                |                          |
| `%R` | <span data-ttu-id="63cea-321">時間（24小時制）-無秒數</span><span class="sxs-lookup"><span data-stu-id="63cea-321">Time in 24-hour format -no seconds</span></span>                                      | <span data-ttu-id="63cea-322">17:45</span><span class="sxs-lookup"><span data-stu-id="63cea-322">17:45</span></span>                    |
| `%r` | <span data-ttu-id="63cea-323">12小時制的時間</span><span class="sxs-lookup"><span data-stu-id="63cea-323">Time in 12-hour format</span></span>                                                  | <span data-ttu-id="63cea-324">上午09:15:36</span><span class="sxs-lookup"><span data-stu-id="63cea-324">09:15:36 AM</span></span>              |
| `%S` | <span data-ttu-id="63cea-325">秒</span><span class="sxs-lookup"><span data-stu-id="63cea-325">Seconds</span></span>                                                                 | <span data-ttu-id="63cea-326">05</span><span class="sxs-lookup"><span data-stu-id="63cea-326">05</span></span>                       |
| `%s` | <span data-ttu-id="63cea-327">自 00:00:00 1970 年1月1日起經過的秒數</span><span class="sxs-lookup"><span data-stu-id="63cea-327">Seconds elapsed since January 1, 1970 00:00:00</span></span>                          | <span data-ttu-id="63cea-328">1150451174</span><span class="sxs-lookup"><span data-stu-id="63cea-328">1150451174</span></span>               |
| `%t` | <span data-ttu-id="63cea-329">水準定位字元</span><span class="sxs-lookup"><span data-stu-id="63cea-329">Horizontal tab character</span></span>                                                |                          |
| `%T` | <span data-ttu-id="63cea-330">24 小時制的時間格式</span><span class="sxs-lookup"><span data-stu-id="63cea-330">Time in 24-hour format</span></span>                                                  | <span data-ttu-id="63cea-331">17:45:52</span><span class="sxs-lookup"><span data-stu-id="63cea-331">17:45:52</span></span>                 |
| `%U` | <span data-ttu-id="63cea-332">與 ' W ' 相同</span><span class="sxs-lookup"><span data-stu-id="63cea-332">Same as 'W'</span></span>                                                             |                          |
| `%u` | <span data-ttu-id="63cea-333">周中的日-數位</span><span class="sxs-lookup"><span data-stu-id="63cea-333">Day of the week - number</span></span>                                                | <span data-ttu-id="63cea-334">星期日 = 0</span><span class="sxs-lookup"><span data-stu-id="63cea-334">Sunday = 0</span></span>               |
| `%V` | <span data-ttu-id="63cea-335">年中的周</span><span class="sxs-lookup"><span data-stu-id="63cea-335">Week of the year</span></span>                                                        | <span data-ttu-id="63cea-336">01-53</span><span class="sxs-lookup"><span data-stu-id="63cea-336">01-53</span></span>                    |
| `%w` | <span data-ttu-id="63cea-337">與 ' u ' 相同</span><span class="sxs-lookup"><span data-stu-id="63cea-337">Same as 'u'</span></span>                                                             |                          |
| `%W` | <span data-ttu-id="63cea-338">年中的周</span><span class="sxs-lookup"><span data-stu-id="63cea-338">Week of the year</span></span>                                                        | <span data-ttu-id="63cea-339">00-52</span><span class="sxs-lookup"><span data-stu-id="63cea-339">00-52</span></span>                    |
| `%X` | <span data-ttu-id="63cea-340">與 ' t ' 相同</span><span class="sxs-lookup"><span data-stu-id="63cea-340">Same as 'T'</span></span>                                                             |                          |
| `%x` | <span data-ttu-id="63cea-341">地區設定標準格式的日期</span><span class="sxs-lookup"><span data-stu-id="63cea-341">Date in standard format for locale</span></span>                                      | <span data-ttu-id="63cea-342">06/27/19 （英文）-US</span><span class="sxs-lookup"><span data-stu-id="63cea-342">06/27/19 for English-US</span></span>  |
| `%Y` | <span data-ttu-id="63cea-343">以4位數格式表示的年份</span><span class="sxs-lookup"><span data-stu-id="63cea-343">Year in 4-digit format</span></span>                                                  | <span data-ttu-id="63cea-344">2019</span><span class="sxs-lookup"><span data-stu-id="63cea-344">2019</span></span>                     |
| `%y` | <span data-ttu-id="63cea-345">以2位數格式表示的年份</span><span class="sxs-lookup"><span data-stu-id="63cea-345">Year in 2-digit format</span></span>                                                  | <span data-ttu-id="63cea-346">19</span><span class="sxs-lookup"><span data-stu-id="63cea-346">19</span></span>                       |
| `%Z` | <span data-ttu-id="63cea-347">從通用時間座標 (UTC) 的時區位移</span><span class="sxs-lookup"><span data-stu-id="63cea-347">Time zone offset from Universal Time Coordinate (UTC)</span></span>                   | <span data-ttu-id="63cea-348">-07</span><span class="sxs-lookup"><span data-stu-id="63cea-348">-07</span></span>                      |

## <span data-ttu-id="63cea-349">相關連結</span><span class="sxs-lookup"><span data-stu-id="63cea-349">RELATED LINKS</span></span>

[<span data-ttu-id="63cea-350">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="63cea-350">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="63cea-351">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="63cea-351">Get-Culture</span></span>](Get-Culture.md)

[<span data-ttu-id="63cea-352">Get-Member</span><span class="sxs-lookup"><span data-stu-id="63cea-352">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="63cea-353">New-Item</span><span class="sxs-lookup"><span data-stu-id="63cea-353">New-Item</span></span>](../Microsoft.PowerShell.Management/New-Item.md)

[<span data-ttu-id="63cea-354">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="63cea-354">New-TimeSpan</span></span>](New-TimeSpan.md)

[<span data-ttu-id="63cea-355">Set-Date</span><span class="sxs-lookup"><span data-stu-id="63cea-355">Set-Date</span></span>](Set-Date.md)
