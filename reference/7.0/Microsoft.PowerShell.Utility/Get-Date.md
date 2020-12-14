---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: 4ae3734d0ce41ef2faa7bcf3e07f136b9e9916a2
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514954"
---
# <span data-ttu-id="b11b4-103">Get-Date</span><span class="sxs-lookup"><span data-stu-id="b11b4-103">Get-Date</span></span>

## <span data-ttu-id="b11b4-104">概要</span><span class="sxs-lookup"><span data-stu-id="b11b4-104">SYNOPSIS</span></span>
<span data-ttu-id="b11b4-105">取得目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b11b4-105">Gets the current date and time.</span></span>

## <span data-ttu-id="b11b4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b11b4-106">SYNTAX</span></span>

### <span data-ttu-id="b11b4-107">net (預設) </span><span class="sxs-lookup"><span data-stu-id="b11b4-107">net (Default)</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [<CommonParameters>]
```

### <span data-ttu-id="b11b4-108">UFormat</span><span class="sxs-lookup"><span data-stu-id="b11b4-108">UFormat</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-UFormat <String>] [<CommonParameters>]
```

## <span data-ttu-id="b11b4-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b11b4-109">DESCRIPTION</span></span>

<span data-ttu-id="b11b4-110">`Get-Date`Cmdlet 會取得代表目前日期或您所指定日期的 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="b11b4-110">The `Get-Date` cmdlet gets a **DateTime** object that represents the current date or a date that you specify.</span></span> <span data-ttu-id="b11b4-111">`Get-Date` 可以用數種 .NET 和 UNIX 格式來格式化日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b11b4-111">`Get-Date` can format the date and time in several .NET and UNIX formats.</span></span> <span data-ttu-id="b11b4-112">您可以使用 `Get-Date` 來產生日期或時間字元字串，然後將字串傳送到其他 Cmdlet 或程式。</span><span class="sxs-lookup"><span data-stu-id="b11b4-112">You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.</span></span>

<span data-ttu-id="b11b4-113">`Get-Date` 使用電腦的文化特性設定來決定如何格式化輸出。</span><span class="sxs-lookup"><span data-stu-id="b11b4-113">`Get-Date` uses the computer's culture settings to determine how the output is formatted.</span></span> <span data-ttu-id="b11b4-114">若要查看電腦的設定，請使用 `(Get-Culture).DateTimeFormat` 。</span><span class="sxs-lookup"><span data-stu-id="b11b4-114">To view your computer's settings, use `(Get-Culture).DateTimeFormat`.</span></span>

## <span data-ttu-id="b11b4-115">範例</span><span class="sxs-lookup"><span data-stu-id="b11b4-115">EXAMPLES</span></span>

### <span data-ttu-id="b11b4-116">範例1：取得目前的日期和時間</span><span class="sxs-lookup"><span data-stu-id="b11b4-116">Example 1: Get the current date and time</span></span>

<span data-ttu-id="b11b4-117">在此範例中，會 `Get-Date` 顯示目前的系統日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b11b4-117">In this example, `Get-Date` displays the current system date and time.</span></span> <span data-ttu-id="b11b4-118">輸出會是完整日期和完整時間格式。</span><span class="sxs-lookup"><span data-stu-id="b11b4-118">The output is in the long-date and long-time formats.</span></span>

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### <span data-ttu-id="b11b4-119">範例2：取得目前日期和時間的元素</span><span class="sxs-lookup"><span data-stu-id="b11b4-119">Example 2: Get elements of the current date and time</span></span>

<span data-ttu-id="b11b4-120">這個範例會示範如何使用 `Get-Date` 來取得日期或時間元素。</span><span class="sxs-lookup"><span data-stu-id="b11b4-120">This example shows how to use `Get-Date` to get either the date or time element.</span></span> <span data-ttu-id="b11b4-121">參數會使用引數 **Date**、 **Time** 或 **DateTime**。</span><span class="sxs-lookup"><span data-stu-id="b11b4-121">The parameter uses the arguments **Date**, **Time**, or **DateTime**.</span></span>

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

<span data-ttu-id="b11b4-122">`Get-Date` 使用 **DisplayHint** 參數搭配 **date** 引數，以只取得日期。</span><span class="sxs-lookup"><span data-stu-id="b11b4-122">`Get-Date` uses the **DisplayHint** parameter with the **Date** argument to get only the date.</span></span>

### <span data-ttu-id="b11b4-123">範例3：使用 .NET 格式規範取得日期和時間</span><span class="sxs-lookup"><span data-stu-id="b11b4-123">Example 3: Get the date and time with a .NET format specifier</span></span>

<span data-ttu-id="b11b4-124">在此範例中，會使用 .NET 格式規範來自訂輸出的格式。</span><span class="sxs-lookup"><span data-stu-id="b11b4-124">In this example, a .NET format specifier is used to customize the output's format.</span></span> <span data-ttu-id="b11b4-125">輸出是 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="b11b4-125">The output is a **String** object.</span></span>

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

<span data-ttu-id="b11b4-126">`Get-Date` 使用 **Format** 參數來指定數個格式規範。</span><span class="sxs-lookup"><span data-stu-id="b11b4-126">`Get-Date` uses the **Format** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="b11b4-127">此範例中使用的 .NET 格式規範定義如下：</span><span class="sxs-lookup"><span data-stu-id="b11b4-127">The .NET format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="b11b4-128">規範</span><span class="sxs-lookup"><span data-stu-id="b11b4-128">Specifier</span></span> | <span data-ttu-id="b11b4-129">定義</span><span class="sxs-lookup"><span data-stu-id="b11b4-129">Definition</span></span> |
| --- | --- |
| `dddd` | <span data-ttu-id="b11b4-130">一周中的日-完整名稱</span><span class="sxs-lookup"><span data-stu-id="b11b4-130">Day of the week - full name</span></span> |
| `MM` | <span data-ttu-id="b11b4-131">月份數</span><span class="sxs-lookup"><span data-stu-id="b11b4-131">Month number</span></span> |
| `dd` | <span data-ttu-id="b11b4-132">月中的日-2 位數</span><span class="sxs-lookup"><span data-stu-id="b11b4-132">Day of the month - 2 digits</span></span> |
| `yyyy` | <span data-ttu-id="b11b4-133">以4位數格式表示的年份</span><span class="sxs-lookup"><span data-stu-id="b11b4-133">Year in 4-digit format</span></span> |
| `HH:mm` | <span data-ttu-id="b11b4-134">時間（24小時制）-無秒數</span><span class="sxs-lookup"><span data-stu-id="b11b4-134">Time in 24-hour format -no seconds</span></span> |
| `K` | <span data-ttu-id="b11b4-135">從通用時間座標 (UTC) 的時區位移</span><span class="sxs-lookup"><span data-stu-id="b11b4-135">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="b11b4-136">如需 .NET 格式規範的詳細資訊，請參閱 [自訂日期和時間格式字串](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)。</span><span class="sxs-lookup"><span data-stu-id="b11b4-136">For more information about .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

### <span data-ttu-id="b11b4-137">範例4：取得 UFormat 規範的日期和時間</span><span class="sxs-lookup"><span data-stu-id="b11b4-137">Example 4: Get the date and time with a UFormat specifier</span></span>

<span data-ttu-id="b11b4-138">在此範例中，會使用數個 **UFormat** 格式規範來自訂輸出的格式。</span><span class="sxs-lookup"><span data-stu-id="b11b4-138">In this example, several **UFormat** format specifiers are used to customize the output's format.</span></span>
<span data-ttu-id="b11b4-139">輸出是 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="b11b4-139">The output is a **String** object.</span></span>

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

<span data-ttu-id="b11b4-140">`Get-Date` 使用 **UFormat** 參數來指定數個格式規範。</span><span class="sxs-lookup"><span data-stu-id="b11b4-140">`Get-Date` uses the **UFormat** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="b11b4-141">此範例中使用的 **UFormat** 格式規範定義如下：</span><span class="sxs-lookup"><span data-stu-id="b11b4-141">The **UFormat** format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="b11b4-142">規範</span><span class="sxs-lookup"><span data-stu-id="b11b4-142">Specifier</span></span> | <span data-ttu-id="b11b4-143">定義</span><span class="sxs-lookup"><span data-stu-id="b11b4-143">Definition</span></span> |
| --- | --- |
| `%A` | <span data-ttu-id="b11b4-144">一周中的日-完整名稱</span><span class="sxs-lookup"><span data-stu-id="b11b4-144">Day of the week - full name</span></span> |
| `%m` | <span data-ttu-id="b11b4-145">月份數</span><span class="sxs-lookup"><span data-stu-id="b11b4-145">Month number</span></span> |
| `%d` | <span data-ttu-id="b11b4-146">月中的日-2 位數</span><span class="sxs-lookup"><span data-stu-id="b11b4-146">Day of the month - 2 digits</span></span> |
| `%Y` | <span data-ttu-id="b11b4-147">以4位數格式表示的年份</span><span class="sxs-lookup"><span data-stu-id="b11b4-147">Year in 4-digit format</span></span> |
| `%R` | <span data-ttu-id="b11b4-148">時間（24小時制）-無秒數</span><span class="sxs-lookup"><span data-stu-id="b11b4-148">Time in 24-hour format -no seconds</span></span> |
| `%Z` | <span data-ttu-id="b11b4-149">從通用時間座標 (UTC) 的時區位移</span><span class="sxs-lookup"><span data-stu-id="b11b4-149">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="b11b4-150">如需有效 **UFormat** 格式規範的清單，請參閱 [附注](#notes) 一節。</span><span class="sxs-lookup"><span data-stu-id="b11b4-150">For a list of valid **UFormat** format specifiers, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="b11b4-151">範例5：取得一年中的日期日</span><span class="sxs-lookup"><span data-stu-id="b11b4-151">Example 5: Get a date's day of the year</span></span>

<span data-ttu-id="b11b4-152">在此範例中，屬性是用來取得年度的數位日。</span><span class="sxs-lookup"><span data-stu-id="b11b4-152">In this example, a property is used to get the numeric day of the year.</span></span>

<span data-ttu-id="b11b4-153">西曆有365天，但有366天的閏年度除外。</span><span class="sxs-lookup"><span data-stu-id="b11b4-153">The Gregorian calendar has 365 days, except for leap years that have 366 days.</span></span> <span data-ttu-id="b11b4-154">例如，2020年12月31日是第366天。</span><span class="sxs-lookup"><span data-stu-id="b11b4-154">For example, December 31, 2020 is day 366.</span></span>

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

<span data-ttu-id="b11b4-155">`Get-Date` 使用三個參數來指定日期： **Year**、 **Month** 和 **Day**。</span><span class="sxs-lookup"><span data-stu-id="b11b4-155">`Get-Date` uses three parameters to specify the date: **Year**, **Month**, and **Day**.</span></span> <span data-ttu-id="b11b4-156">此命令會以括弧括住，以便 **DayofYear** 屬性評估結果。</span><span class="sxs-lookup"><span data-stu-id="b11b4-156">The command is wrapped with parentheses so that the result is evaluated by the **DayofYear** property.</span></span>

### <span data-ttu-id="b11b4-157">範例6：檢查是否已針對日光節約時間調整日期</span><span class="sxs-lookup"><span data-stu-id="b11b4-157">Example 6: Check if a date is adjusted for daylight savings time</span></span>

<span data-ttu-id="b11b4-158">此範例會使用布林方法，以確認日期是否以日光節約時間進行調整。</span><span class="sxs-lookup"><span data-stu-id="b11b4-158">This example uses a boolean method to verify if a date is adjusted by daylight savings time.</span></span>

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

<span data-ttu-id="b11b4-159">變數會 `$DST` 儲存的結果 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="b11b4-159">A variable, `$DST` stores the result of `Get-Date`.</span></span> <span data-ttu-id="b11b4-160">`$DST` 使用 **IsDaylightSavingTime** 方法來測試是否針對日光節約時間調整日期。</span><span class="sxs-lookup"><span data-stu-id="b11b4-160">`$DST` uses the **IsDaylightSavingTime** method to test if the date is adjusted for daylight savings time.</span></span>

### <span data-ttu-id="b11b4-161">範例7：將目前時間轉換成 UTC 時間</span><span class="sxs-lookup"><span data-stu-id="b11b4-161">Example 7: Convert the current time to UTC time</span></span>

<span data-ttu-id="b11b4-162">在此範例中，目前的時間會轉換成 UTC 時間。</span><span class="sxs-lookup"><span data-stu-id="b11b4-162">In this example, the current time is converted to UTC time.</span></span> <span data-ttu-id="b11b4-163">系統地區設定的 UTC 時差會用來轉換時間。</span><span class="sxs-lookup"><span data-stu-id="b11b4-163">The UTC offset for the system's locale is used to convert the time.</span></span> <span data-ttu-id="b11b4-164">[ [附注](#notes) ] 區段中的資料表會列出有效的 **UFormat** 格式規範。</span><span class="sxs-lookup"><span data-stu-id="b11b4-164">A table in the [Notes](#notes) section lists the valid **UFormat** format specifiers.</span></span>

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

<span data-ttu-id="b11b4-165">`Get-Date` 使用 **UFormat** 參數搭配格式規範，以顯示目前的系統日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b11b4-165">`Get-Date` uses the **UFormat** parameter with format specifiers to display the current system date and time.</span></span> <span data-ttu-id="b11b4-166">格式規範 **% Z** 代表 **-07** 的 UTC 時差。</span><span class="sxs-lookup"><span data-stu-id="b11b4-166">The format specifier **%Z** represents the UTC offset of **-07**.</span></span>

<span data-ttu-id="b11b4-167">`$Time`變數會儲存目前的系統日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b11b4-167">The `$Time` variable stores the current system date and time.</span></span> <span data-ttu-id="b11b4-168">`$Time` 使用 **>datetime.touniversaltime ( # B1** 方法，根據電腦的 UTC 時差來轉換時間。</span><span class="sxs-lookup"><span data-stu-id="b11b4-168">`$Time` uses the **ToUniversalTime()** method to convert the time based on the computer's UTC offset.</span></span>

### <span data-ttu-id="b11b4-169">範例8：建立時間戳記</span><span class="sxs-lookup"><span data-stu-id="b11b4-169">Example 8: Create a timestamp</span></span>

<span data-ttu-id="b11b4-170">在此範例中，格式規範會建立目錄名稱的時間戳記 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="b11b4-170">In this example, a format specifier creates a timestamp **String** object for a directory name.</span></span> <span data-ttu-id="b11b4-171">時間戳記包含日期、時間和 UTC 時差。</span><span class="sxs-lookup"><span data-stu-id="b11b4-171">The timestamp includes the date, time, and UTC offset.</span></span>

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

<span data-ttu-id="b11b4-172">`$timestamp`變數會儲存命令的結果 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="b11b4-172">The `$timestamp` variable stores the results of a `Get-Date` command.</span></span> <span data-ttu-id="b11b4-173">`Get-Date` 使用 **格式** 參數搭配小寫的格式規範 `o` 來建立時間戳記 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="b11b4-173">`Get-Date` uses the **Format** parameter with the format specifier of lowercase `o` to create a timestamp **String** object.</span></span> <span data-ttu-id="b11b4-174">物件會向下傳送到管線 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="b11b4-174">The object is sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="b11b4-175">**ScriptBlock** 包含 `$_` 表示目前管線物件的變數。</span><span class="sxs-lookup"><span data-stu-id="b11b4-175">A **ScriptBlock** contains the `$_` variable that represents the current pipeline object.</span></span> <span data-ttu-id="b11b4-176">時間戳記字串是由以句號取代的冒號分隔。</span><span class="sxs-lookup"><span data-stu-id="b11b4-176">The timestamp string is delimited by colons that are replaced by periods.</span></span>

<span data-ttu-id="b11b4-177">`New-Item` 使用 **Path** 參數指定新目錄的位置。</span><span class="sxs-lookup"><span data-stu-id="b11b4-177">`New-Item` uses the **Path** parameter to specify the location for a new directory.</span></span> <span data-ttu-id="b11b4-178">路徑包含 `$timestamp` 變數做為目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="b11b4-178">The path includes the `$timestamp` variable as the directory name.</span></span> <span data-ttu-id="b11b4-179">**Type** 參數會指定建立目錄。</span><span class="sxs-lookup"><span data-stu-id="b11b4-179">The **Type** parameter specifies that a directory is created.</span></span>

## <span data-ttu-id="b11b4-180">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b11b4-180">PARAMETERS</span></span>

### <span data-ttu-id="b11b4-181">-Date</span><span class="sxs-lookup"><span data-stu-id="b11b4-181">-Date</span></span>

<span data-ttu-id="b11b4-182">指定日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b11b4-182">Specifies a date and time.</span></span> <span data-ttu-id="b11b4-183">Time 是選擇性的，如果未指定，則會傳回00:00:00。</span><span class="sxs-lookup"><span data-stu-id="b11b4-183">Time is optional and if not specified, returns 00:00:00.</span></span>

<span data-ttu-id="b11b4-184">以系統地區設定的標準格式輸入日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b11b4-184">Enter the date and time in a format that is standard for the system locale.</span></span>

<span data-ttu-id="b11b4-185">例如，在美式英文中：</span><span class="sxs-lookup"><span data-stu-id="b11b4-185">For example, in US English:</span></span>

<span data-ttu-id="b11b4-186">`Get-Date -Date "6/25/2019 12:30:22"` 傳回2019年6月25日星期二的12:30:22</span><span class="sxs-lookup"><span data-stu-id="b11b4-186">`Get-Date -Date "6/25/2019 12:30:22"` returns Tuesday, June 25, 2019 12:30:22</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b11b4-187">-日</span><span class="sxs-lookup"><span data-stu-id="b11b4-187">-Day</span></span>

<span data-ttu-id="b11b4-188">指定要顯示的月份日期。</span><span class="sxs-lookup"><span data-stu-id="b11b4-188">Specifies the day of the month that is displayed.</span></span> <span data-ttu-id="b11b4-189">輸入從 1 到 31 的值。</span><span class="sxs-lookup"><span data-stu-id="b11b4-189">Enter a value from 1 to 31.</span></span>

<span data-ttu-id="b11b4-190">如果指定的值大於一個月中的天數，則 PowerShell 會將天數加上月份。</span><span class="sxs-lookup"><span data-stu-id="b11b4-190">If the specified value is greater than the number of days in a month, PowerShell adds the number of days to the month.</span></span> <span data-ttu-id="b11b4-191">例如， `Get-Date -Month 2 -Day 31` 顯示 3 **月 3** 日，而不是 **2 月31日**。</span><span class="sxs-lookup"><span data-stu-id="b11b4-191">For example, `Get-Date -Month 2 -Day 31` displays **March 3**, not **February 31**.</span></span>

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

### <span data-ttu-id="b11b4-192">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="b11b4-192">-DisplayHint</span></span>

<span data-ttu-id="b11b4-193">決定要顯示日期和時間的哪些元素。</span><span class="sxs-lookup"><span data-stu-id="b11b4-193">Determines which elements of the date and time are displayed.</span></span>

<span data-ttu-id="b11b4-194">接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="b11b4-194">The accepted values are as follows:</span></span>

- <span data-ttu-id="b11b4-195">**Date**：只顯示日期</span><span class="sxs-lookup"><span data-stu-id="b11b4-195">**Date**: displays only the date</span></span>
- <span data-ttu-id="b11b4-196">**時間**：只顯示時間</span><span class="sxs-lookup"><span data-stu-id="b11b4-196">**Time**: displays only the time</span></span>
- <span data-ttu-id="b11b4-197">**DateTime**：顯示日期和時間</span><span class="sxs-lookup"><span data-stu-id="b11b4-197">**DateTime**: displays the date and time</span></span>

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

### <span data-ttu-id="b11b4-198">-Format</span><span class="sxs-lookup"><span data-stu-id="b11b4-198">-Format</span></span>

<span data-ttu-id="b11b4-199">使用格式規範所指定的 Microsoft .NET Framework 格式來顯示日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b11b4-199">Displays the date and time in the Microsoft .NET Framework format indicated by the format specifier.</span></span>
<span data-ttu-id="b11b4-200">**Format** 參數會輸出 **String** 物件。</span><span class="sxs-lookup"><span data-stu-id="b11b4-200">The **Format** parameter outputs a **String** object.</span></span>

<span data-ttu-id="b11b4-201">如需可用 .NET 格式規範的清單，請參閱 [自訂日期和時間格式字串](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)。</span><span class="sxs-lookup"><span data-stu-id="b11b4-201">For a list of available .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

<span data-ttu-id="b11b4-202">使用 **Format** 參數時，只會 `Get-Date` 取得顯示日期所需的 **DateTime** 物件屬性。</span><span class="sxs-lookup"><span data-stu-id="b11b4-202">When the **Format** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="b11b4-203">如此一來，**DateTime** 物件的部分屬性和方法可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="b11b4-203">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

<span data-ttu-id="b11b4-204">從 PowerShell 5.0 開始，您可以使用下列其他格式作為 **Format** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="b11b4-204">Starting in PowerShell 5.0, you can use the following additional formats as values for the **Format** parameter.</span></span>

- <span data-ttu-id="b11b4-205">**FileDate**。</span><span class="sxs-lookup"><span data-stu-id="b11b4-205">**FileDate**.</span></span> <span data-ttu-id="b11b4-206">以本機時程表示的目前日期的檔案或路徑易記表示。</span><span class="sxs-lookup"><span data-stu-id="b11b4-206">A file or path-friendly representation of the current date in local time.</span></span> <span data-ttu-id="b11b4-207">格式 `yyyyMMdd` (區分大小寫，使用4位數年份、2位數月份和2位數的日) 。</span><span class="sxs-lookup"><span data-stu-id="b11b4-207">The format is `yyyyMMdd` (case-sensitive, using a 4-digit year, 2-digit month, and 2-digit day).</span></span> <span data-ttu-id="b11b4-208">例如：</span><span class="sxs-lookup"><span data-stu-id="b11b4-208">For example:</span></span>
  20190627.

- <span data-ttu-id="b11b4-209">**FileDateUniversal**。</span><span class="sxs-lookup"><span data-stu-id="b11b4-209">**FileDateUniversal**.</span></span> <span data-ttu-id="b11b4-210">以通用時程表示的目前日期的檔案或路徑易記表示 (UTC) 。</span><span class="sxs-lookup"><span data-stu-id="b11b4-210">A file or path-friendly representation of the current date in universal time (UTC).</span></span> <span data-ttu-id="b11b4-211">格式 `yyyyMMddZ` (區分大小寫，使用4位數的年份、2位數的月份、2位數的日期，以及 `Z` 做為 UTC 指標) 的字母。</span><span class="sxs-lookup"><span data-stu-id="b11b4-211">The format is `yyyyMMddZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="b11b4-212">例如：20190627Z。</span><span class="sxs-lookup"><span data-stu-id="b11b4-212">For example: 20190627Z.</span></span>

- <span data-ttu-id="b11b4-213">**FileDateTime**。</span><span class="sxs-lookup"><span data-stu-id="b11b4-213">**FileDateTime**.</span></span> <span data-ttu-id="b11b4-214">以24小時制格式，以本機時程表示的目前日期和時間的檔案或路徑易記表示。</span><span class="sxs-lookup"><span data-stu-id="b11b4-214">A file or path-friendly representation of the current date and time in local time, in 24-hour format.</span></span> <span data-ttu-id="b11b4-215">格式 `yyyyMMddTHHmmssffff` (區分大小寫、使用4位數的年份、2位數的月份、2位數的日期、 `T` 以時間分隔符號表示的字母、2位數的小時、2位數分鐘、2位數的秒數，以及4位數的毫秒) 。</span><span class="sxs-lookup"><span data-stu-id="b11b4-215">The format is `yyyyMMddTHHmmssffff` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, and 4-digit millisecond).</span></span> <span data-ttu-id="b11b4-216">例如：20190627T0840107271。</span><span class="sxs-lookup"><span data-stu-id="b11b4-216">For example: 20190627T0840107271.</span></span>

- <span data-ttu-id="b11b4-217">**FileDateTimeUniversal**。</span><span class="sxs-lookup"><span data-stu-id="b11b4-217">**FileDateTimeUniversal**.</span></span> <span data-ttu-id="b11b4-218">以24小時格式表示的目前日期和時間的檔案或路徑易記標記法 (UTC) 。</span><span class="sxs-lookup"><span data-stu-id="b11b4-218">A file or path-friendly representation of the current date and time in universal time (UTC), in 24-hour format.</span></span> <span data-ttu-id="b11b4-219">格式 `yyyyMMddTHHmmssffffZ` (區分大小寫、使用4位數的年份、2位數的月份、2位數的日期、 `T` 以時間分隔符號表示的字母、2位數的小時、2位數分鐘、2位數秒、4位數毫秒，以及 `Z` 做為 UTC 指標) 的字母。</span><span class="sxs-lookup"><span data-stu-id="b11b4-219">The format is `yyyyMMddTHHmmssffffZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, 4-digit millisecond, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="b11b4-220">例如：20190627T1540500718Z。</span><span class="sxs-lookup"><span data-stu-id="b11b4-220">For example: 20190627T1540500718Z.</span></span>

```yaml
Type: System.String
Parameter Sets: net
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b11b4-221">-小時</span><span class="sxs-lookup"><span data-stu-id="b11b4-221">-Hour</span></span>

<span data-ttu-id="b11b4-222">指定要顯示的小時。</span><span class="sxs-lookup"><span data-stu-id="b11b4-222">Specifies the hour that is displayed.</span></span> <span data-ttu-id="b11b4-223">輸入0到23之間的值。</span><span class="sxs-lookup"><span data-stu-id="b11b4-223">Enter a value from 0 to 23.</span></span>

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

### <span data-ttu-id="b11b4-224">-毫秒</span><span class="sxs-lookup"><span data-stu-id="b11b4-224">-Millisecond</span></span>

<span data-ttu-id="b11b4-225">指定日期中的毫秒。</span><span class="sxs-lookup"><span data-stu-id="b11b4-225">Specifies the milliseconds in the date.</span></span> <span data-ttu-id="b11b4-226">輸入0到999的值。</span><span class="sxs-lookup"><span data-stu-id="b11b4-226">Enter a value from 0 to 999.</span></span>

<span data-ttu-id="b11b4-227">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b11b4-227">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="b11b4-228">-分鐘</span><span class="sxs-lookup"><span data-stu-id="b11b4-228">-Minute</span></span>

<span data-ttu-id="b11b4-229">指定要顯示的分鐘。</span><span class="sxs-lookup"><span data-stu-id="b11b4-229">Specifies the minute that is displayed.</span></span> <span data-ttu-id="b11b4-230">輸入0到59的值。</span><span class="sxs-lookup"><span data-stu-id="b11b4-230">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="b11b4-231">-月</span><span class="sxs-lookup"><span data-stu-id="b11b4-231">-Month</span></span>

<span data-ttu-id="b11b4-232">指定要顯示的月份。</span><span class="sxs-lookup"><span data-stu-id="b11b4-232">Specifies the month that is displayed.</span></span> <span data-ttu-id="b11b4-233">輸入1到12的值。</span><span class="sxs-lookup"><span data-stu-id="b11b4-233">Enter a value from 1 to 12.</span></span>

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

### <span data-ttu-id="b11b4-234">-秒</span><span class="sxs-lookup"><span data-stu-id="b11b4-234">-Second</span></span>

<span data-ttu-id="b11b4-235">指定要顯示的秒。</span><span class="sxs-lookup"><span data-stu-id="b11b4-235">Specifies the second that is displayed.</span></span> <span data-ttu-id="b11b4-236">輸入0到59的值。</span><span class="sxs-lookup"><span data-stu-id="b11b4-236">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="b11b4-237">-UFormat</span><span class="sxs-lookup"><span data-stu-id="b11b4-237">-UFormat</span></span>

<span data-ttu-id="b11b4-238">使用 UNIX 格式顯示日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b11b4-238">Displays the date and time in UNIX format.</span></span> <span data-ttu-id="b11b4-239">**UFormat** 參數會輸出字串物件。</span><span class="sxs-lookup"><span data-stu-id="b11b4-239">The **UFormat** parameter outputs a string object.</span></span>

<span data-ttu-id="b11b4-240">**UFormat** 規範的前面會加上百分比符號 (`%`) ，例如、 `%m` `%d` 和 `%Y` 。</span><span class="sxs-lookup"><span data-stu-id="b11b4-240">**UFormat** specifiers are preceded by a percent sign (`%`), for example, `%m`, `%d`, and `%Y`.</span></span> <span data-ttu-id="b11b4-241">[附注](#notes)區段包含有效 **UFormat** 規範的資料表。</span><span class="sxs-lookup"><span data-stu-id="b11b4-241">The [Notes](#notes) section contains a table of valid **UFormat specifiers**.</span></span>

<span data-ttu-id="b11b4-242">使用 **UFormat** 參數時，只會 `Get-Date` 取得顯示日期所需的 **DateTime** 物件屬性。</span><span class="sxs-lookup"><span data-stu-id="b11b4-242">When the **UFormat** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="b11b4-243">如此一來，**DateTime** 物件的部分屬性和方法可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="b11b4-243">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

```yaml
Type: System.String
Parameter Sets: UFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b11b4-244">-年</span><span class="sxs-lookup"><span data-stu-id="b11b4-244">-Year</span></span>

<span data-ttu-id="b11b4-245">指定要顯示的年份。</span><span class="sxs-lookup"><span data-stu-id="b11b4-245">Specifies the year that is displayed.</span></span> <span data-ttu-id="b11b4-246">輸入從1到9999的值。</span><span class="sxs-lookup"><span data-stu-id="b11b4-246">Enter a value from 1 to 9999.</span></span>

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

### <span data-ttu-id="b11b4-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b11b4-247">CommonParameters</span></span>

<span data-ttu-id="b11b4-248">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b11b4-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b11b4-249">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b11b4-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b11b4-250">輸入</span><span class="sxs-lookup"><span data-stu-id="b11b4-250">INPUTS</span></span>

### <span data-ttu-id="b11b4-251">管線輸入</span><span class="sxs-lookup"><span data-stu-id="b11b4-251">Pipeline input</span></span>

<span data-ttu-id="b11b4-252">`Get-Date` 接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="b11b4-252">`Get-Date` accepts pipeline input.</span></span> <span data-ttu-id="b11b4-253">例如 `Get-ChildItem | Get-Date`。</span><span class="sxs-lookup"><span data-stu-id="b11b4-253">For example, `Get-ChildItem | Get-Date`.</span></span>

## <span data-ttu-id="b11b4-254">輸出</span><span class="sxs-lookup"><span data-stu-id="b11b4-254">OUTPUTS</span></span>

### <span data-ttu-id="b11b4-255">System.string 或 System.string</span><span class="sxs-lookup"><span data-stu-id="b11b4-255">System.DateTime or System.String</span></span>

<span data-ttu-id="b11b4-256">`Get-Date` 傳回 **DateTime** 物件，但使用 **Format** 和 **UFormat** 參數時除外。</span><span class="sxs-lookup"><span data-stu-id="b11b4-256">`Get-Date` returns a **DateTime** object except when the **Format** and **UFormat** parameters are used.</span></span> <span data-ttu-id="b11b4-257">**Format** 或 **UFormat** 參數會傳回 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="b11b4-257">The **Format** or **UFormat** parameters return **String** objects.</span></span>

<span data-ttu-id="b11b4-258">將 **DateTime** 物件向下傳送至 `Add-Content` 需要字串輸入的 Cmdlet 時，PowerShell 會將物件轉換成 **字串** 物件。</span><span class="sxs-lookup"><span data-stu-id="b11b4-258">When a **DateTime** object is sent down the pipeline to a cmdlet such as `Add-Content` that expects string input, PowerShell converts the object to a **String** object.</span></span>

<span data-ttu-id="b11b4-259">方法會 `(Get-Date).ToString()` 將 **DateTime** 物件轉換成 **String** 物件。</span><span class="sxs-lookup"><span data-stu-id="b11b4-259">The method `(Get-Date).ToString()` converts a **DateTime** object a **String** object.</span></span>

<span data-ttu-id="b11b4-260">若要顯示物件的屬性和方法，請將物件沿著管線向下傳送至 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="b11b4-260">To display an object's properties and methods, send the object down the pipeline to `Get-Member`.</span></span>
<span data-ttu-id="b11b4-261">例如 `Get-Date | Get-Member`。</span><span class="sxs-lookup"><span data-stu-id="b11b4-261">For example, `Get-Date | Get-Member`.</span></span>

## <span data-ttu-id="b11b4-262">注意</span><span class="sxs-lookup"><span data-stu-id="b11b4-262">NOTES</span></span>

<span data-ttu-id="b11b4-263">**DateTime** 物件是適用于系統地區設定的完整日期和完整時間格式。</span><span class="sxs-lookup"><span data-stu-id="b11b4-263">**DateTime** objects are in long-date and long-time formats for the system locale.</span></span>

<span data-ttu-id="b11b4-264">有效的 **UFormat** 規範會顯示在下表中：</span><span class="sxs-lookup"><span data-stu-id="b11b4-264">The valid **UFormat specifiers** are displayed in the following table:</span></span>

| <span data-ttu-id="b11b4-265">格式規範</span><span class="sxs-lookup"><span data-stu-id="b11b4-265">Format specifier</span></span> |                                 <span data-ttu-id="b11b4-266">意義</span><span class="sxs-lookup"><span data-stu-id="b11b4-266">Meaning</span></span>                     |         <span data-ttu-id="b11b4-267">範例</span><span class="sxs-lookup"><span data-stu-id="b11b4-267">Example</span></span>          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | <span data-ttu-id="b11b4-268">一周中的日-完整名稱</span><span class="sxs-lookup"><span data-stu-id="b11b4-268">Day of the week - full name</span></span>                                             | <span data-ttu-id="b11b4-269">星期一</span><span class="sxs-lookup"><span data-stu-id="b11b4-269">Monday</span></span>                   |
| `%a` | <span data-ttu-id="b11b4-270">一周中的日-縮寫名稱</span><span class="sxs-lookup"><span data-stu-id="b11b4-270">Day of the week - abbreviated name</span></span>                                      | <span data-ttu-id="b11b4-271">Mon</span><span class="sxs-lookup"><span data-stu-id="b11b4-271">Mon</span></span>                      |
| `%B` | <span data-ttu-id="b11b4-272">月份名稱-完整</span><span class="sxs-lookup"><span data-stu-id="b11b4-272">Month name - full</span></span>                                                       | <span data-ttu-id="b11b4-273">一月</span><span class="sxs-lookup"><span data-stu-id="b11b4-273">January</span></span>                  |
| `%b` | <span data-ttu-id="b11b4-274">月份名稱-縮寫</span><span class="sxs-lookup"><span data-stu-id="b11b4-274">Month name - abbreviated</span></span>                                                | <span data-ttu-id="b11b4-275">一月</span><span class="sxs-lookup"><span data-stu-id="b11b4-275">Jan</span></span>                      |
| `%C` | <span data-ttu-id="b11b4-276">世紀</span><span class="sxs-lookup"><span data-stu-id="b11b4-276">Century</span></span>                                                                 | <span data-ttu-id="b11b4-277">20適用于2019</span><span class="sxs-lookup"><span data-stu-id="b11b4-277">20 for 2019</span></span>              |
| `%c` | <span data-ttu-id="b11b4-278">日期和時間-縮寫</span><span class="sxs-lookup"><span data-stu-id="b11b4-278">Date and time - abbreviated</span></span>                                             | <span data-ttu-id="b11b4-279">星期四6月 27 08:44:18 2019</span><span class="sxs-lookup"><span data-stu-id="b11b4-279">Thu Jun 27 08:44:18 2019</span></span> |
| `%D` | <span data-ttu-id="b11b4-280">日期（mm/dd/yy 格式）</span><span class="sxs-lookup"><span data-stu-id="b11b4-280">Date in mm/dd/yy format</span></span>                                                 | <span data-ttu-id="b11b4-281">06/27/19</span><span class="sxs-lookup"><span data-stu-id="b11b4-281">06/27/19</span></span>                 |
| `%d` | <span data-ttu-id="b11b4-282">月中的日-2 位數</span><span class="sxs-lookup"><span data-stu-id="b11b4-282">Day of the month - 2 digits</span></span>                                             | <span data-ttu-id="b11b4-283">05</span><span class="sxs-lookup"><span data-stu-id="b11b4-283">05</span></span>                       |
| `%e` | <span data-ttu-id="b11b4-284">月中的日-如果只有一個數位，則前面加上一個空格</span><span class="sxs-lookup"><span data-stu-id="b11b4-284">Day of the month - preceded by a space if only a single digit</span></span>           | <span data-ttu-id="b11b4-285">\<space\>.5</span><span class="sxs-lookup"><span data-stu-id="b11b4-285">\<space\>5</span></span>               |
| `%F` | <span data-ttu-id="b11b4-286">以 YYYY-MM-DD 格式的日期（等於% Y-% m-% d） (ISO 8601 日期格式) </span><span class="sxs-lookup"><span data-stu-id="b11b4-286">Date in YYYY-mm-dd format, equal to %Y-%m-%d (the ISO 8601 date format)</span></span> | <span data-ttu-id="b11b4-287">2019-06-27</span><span class="sxs-lookup"><span data-stu-id="b11b4-287">2019-06-27</span></span>               |
| `%G` | <span data-ttu-id="b11b4-288">與 ' Y ' 相同</span><span class="sxs-lookup"><span data-stu-id="b11b4-288">Same as 'Y'</span></span>                                                             |                          |
| `%g` | <span data-ttu-id="b11b4-289">與 ' y ' 相同</span><span class="sxs-lookup"><span data-stu-id="b11b4-289">Same as 'y'</span></span>                                                             |                          |
| `%H` | <span data-ttu-id="b11b4-290">24小時制的小時</span><span class="sxs-lookup"><span data-stu-id="b11b4-290">Hour in 24-hour format</span></span>                                                  | <span data-ttu-id="b11b4-291">17</span><span class="sxs-lookup"><span data-stu-id="b11b4-291">17</span></span>                       |
| `%h` | <span data-ttu-id="b11b4-292">與 ' b ' 相同</span><span class="sxs-lookup"><span data-stu-id="b11b4-292">Same as 'b'</span></span>                                                             |                          |
| `%I` | <span data-ttu-id="b11b4-293">12小時制的小時格式</span><span class="sxs-lookup"><span data-stu-id="b11b4-293">Hour in 12-hour format</span></span>                                                  | <span data-ttu-id="b11b4-294">05</span><span class="sxs-lookup"><span data-stu-id="b11b4-294">05</span></span>                       |
| `%j` | <span data-ttu-id="b11b4-295">年中的日</span><span class="sxs-lookup"><span data-stu-id="b11b4-295">Day of the year</span></span>                                                         | <span data-ttu-id="b11b4-296">1-366</span><span class="sxs-lookup"><span data-stu-id="b11b4-296">1-366</span></span>                    |
| `%k` | <span data-ttu-id="b11b4-297">與 ' H ' 相同</span><span class="sxs-lookup"><span data-stu-id="b11b4-297">Same as 'H'</span></span>                                                             |                          |
| `%l` | <span data-ttu-id="b11b4-298">與「I」相同 (我) </span><span class="sxs-lookup"><span data-stu-id="b11b4-298">Same as 'I' (Upper-case I)</span></span>                                              | <span data-ttu-id="b11b4-299">05</span><span class="sxs-lookup"><span data-stu-id="b11b4-299">05</span></span>                       |
| `%M` | <span data-ttu-id="b11b4-300">分鐘</span><span class="sxs-lookup"><span data-stu-id="b11b4-300">Minutes</span></span>                                                                 | <span data-ttu-id="b11b4-301">35</span><span class="sxs-lookup"><span data-stu-id="b11b4-301">35</span></span>                       |
| `%m` | <span data-ttu-id="b11b4-302">月份數</span><span class="sxs-lookup"><span data-stu-id="b11b4-302">Month number</span></span>                                                            | <span data-ttu-id="b11b4-303">06</span><span class="sxs-lookup"><span data-stu-id="b11b4-303">06</span></span>                       |
| `%n` | <span data-ttu-id="b11b4-304">換行字元</span><span class="sxs-lookup"><span data-stu-id="b11b4-304">newline character</span></span>                                                       |                          |
| `%p` | <span data-ttu-id="b11b4-305">AM 或 PM</span><span class="sxs-lookup"><span data-stu-id="b11b4-305">AM or PM</span></span>                                                                |                          |
| `%R` | <span data-ttu-id="b11b4-306">時間（24小時制）-無秒數</span><span class="sxs-lookup"><span data-stu-id="b11b4-306">Time in 24-hour format -no seconds</span></span>                                      | <span data-ttu-id="b11b4-307">17:45</span><span class="sxs-lookup"><span data-stu-id="b11b4-307">17:45</span></span>                    |
| `%r` | <span data-ttu-id="b11b4-308">12小時制的時間</span><span class="sxs-lookup"><span data-stu-id="b11b4-308">Time in 12-hour format</span></span>                                                  | <span data-ttu-id="b11b4-309">上午09:15:36</span><span class="sxs-lookup"><span data-stu-id="b11b4-309">09:15:36 AM</span></span>              |
| `%S` | <span data-ttu-id="b11b4-310">秒</span><span class="sxs-lookup"><span data-stu-id="b11b4-310">Seconds</span></span>                                                                 | <span data-ttu-id="b11b4-311">05</span><span class="sxs-lookup"><span data-stu-id="b11b4-311">05</span></span>                       |
| `%s` | <span data-ttu-id="b11b4-312">自 00:00:00 1970 年1月1日起經過的秒數</span><span class="sxs-lookup"><span data-stu-id="b11b4-312">Seconds elapsed since January 1, 1970 00:00:00</span></span>                          | <span data-ttu-id="b11b4-313">1150451174</span><span class="sxs-lookup"><span data-stu-id="b11b4-313">1150451174</span></span>               |
| `%t` | <span data-ttu-id="b11b4-314">水準定位字元</span><span class="sxs-lookup"><span data-stu-id="b11b4-314">Horizontal tab character</span></span>                                                |                          |
| `%T` | <span data-ttu-id="b11b4-315">24 小時制的時間格式</span><span class="sxs-lookup"><span data-stu-id="b11b4-315">Time in 24-hour format</span></span>                                                  | <span data-ttu-id="b11b4-316">17:45:52</span><span class="sxs-lookup"><span data-stu-id="b11b4-316">17:45:52</span></span>                 |
| `%U` | <span data-ttu-id="b11b4-317">與 ' W ' 相同</span><span class="sxs-lookup"><span data-stu-id="b11b4-317">Same as 'W'</span></span>                                                             |                          |
| `%u` | <span data-ttu-id="b11b4-318">周中的日-數位</span><span class="sxs-lookup"><span data-stu-id="b11b4-318">Day of the week - number</span></span>                                                | <span data-ttu-id="b11b4-319">星期日 = 0</span><span class="sxs-lookup"><span data-stu-id="b11b4-319">Sunday = 0</span></span>               |
| `%V` | <span data-ttu-id="b11b4-320">年中的周</span><span class="sxs-lookup"><span data-stu-id="b11b4-320">Week of the year</span></span>                                                        | <span data-ttu-id="b11b4-321">01-53</span><span class="sxs-lookup"><span data-stu-id="b11b4-321">01-53</span></span>                    |
| `%w` | <span data-ttu-id="b11b4-322">與 ' u ' 相同</span><span class="sxs-lookup"><span data-stu-id="b11b4-322">Same as 'u'</span></span>                                                             |                          |
| `%W` | <span data-ttu-id="b11b4-323">年中的周</span><span class="sxs-lookup"><span data-stu-id="b11b4-323">Week of the year</span></span>                                                        | <span data-ttu-id="b11b4-324">00-52</span><span class="sxs-lookup"><span data-stu-id="b11b4-324">00-52</span></span>                    |
| `%X` | <span data-ttu-id="b11b4-325">與 ' t ' 相同</span><span class="sxs-lookup"><span data-stu-id="b11b4-325">Same as 'T'</span></span>                                                             |                          |
| `%x` | <span data-ttu-id="b11b4-326">地區設定標準格式的日期</span><span class="sxs-lookup"><span data-stu-id="b11b4-326">Date in standard format for locale</span></span>                                      | <span data-ttu-id="b11b4-327">06/27/19 （英文）-US</span><span class="sxs-lookup"><span data-stu-id="b11b4-327">06/27/19 for English-US</span></span>  |
| `%Y` | <span data-ttu-id="b11b4-328">以4位數格式表示的年份</span><span class="sxs-lookup"><span data-stu-id="b11b4-328">Year in 4-digit format</span></span>                                                  | <span data-ttu-id="b11b4-329">2019</span><span class="sxs-lookup"><span data-stu-id="b11b4-329">2019</span></span>                     |
| `%y` | <span data-ttu-id="b11b4-330">以2位數格式表示的年份</span><span class="sxs-lookup"><span data-stu-id="b11b4-330">Year in 2-digit format</span></span>                                                  | <span data-ttu-id="b11b4-331">19</span><span class="sxs-lookup"><span data-stu-id="b11b4-331">19</span></span>                       |
| `%Z` | <span data-ttu-id="b11b4-332">從通用時間座標 (UTC) 的時區位移</span><span class="sxs-lookup"><span data-stu-id="b11b4-332">Time zone offset from Universal Time Coordinate (UTC)</span></span>                   | <span data-ttu-id="b11b4-333">-07</span><span class="sxs-lookup"><span data-stu-id="b11b4-333">-07</span></span>                      |

## <span data-ttu-id="b11b4-334">相關連結</span><span class="sxs-lookup"><span data-stu-id="b11b4-334">RELATED LINKS</span></span>

[<span data-ttu-id="b11b4-335">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="b11b4-335">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="b11b4-336">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="b11b4-336">Get-Culture</span></span>](Get-Culture.md)

[<span data-ttu-id="b11b4-337">Get-Member</span><span class="sxs-lookup"><span data-stu-id="b11b4-337">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="b11b4-338">New-Item</span><span class="sxs-lookup"><span data-stu-id="b11b4-338">New-Item</span></span>](../Microsoft.PowerShell.Management/New-Item.md)

[<span data-ttu-id="b11b4-339">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="b11b4-339">New-TimeSpan</span></span>](New-TimeSpan.md)

[<span data-ttu-id="b11b4-340">Set-Date</span><span class="sxs-lookup"><span data-stu-id="b11b4-340">Set-Date</span></span>](Set-Date.md)
