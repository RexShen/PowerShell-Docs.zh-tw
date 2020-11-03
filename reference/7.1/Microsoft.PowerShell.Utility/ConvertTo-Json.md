---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: b4d65b5013ba3e3f172d0780e7c8a3ad31c740a1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204219"
---
# <span data-ttu-id="22575-103">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="22575-103">ConvertTo-Json</span></span>

## <span data-ttu-id="22575-104">概要</span><span class="sxs-lookup"><span data-stu-id="22575-104">SYNOPSIS</span></span>
<span data-ttu-id="22575-105">將物件轉換成 JSON 格式的字串。</span><span class="sxs-lookup"><span data-stu-id="22575-105">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="22575-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="22575-106">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## <span data-ttu-id="22575-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="22575-107">DESCRIPTION</span></span>

<span data-ttu-id="22575-108">`ConvertTo-Json`Cmdlet 會將任何 .net 物件轉換成 JavaScript 物件標記法 (JSON) 格式的字串。</span><span class="sxs-lookup"><span data-stu-id="22575-108">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="22575-109">屬性會轉換成欄位名稱、欄位值會轉換成屬性值，而方法會被移除。</span><span class="sxs-lookup"><span data-stu-id="22575-109">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="22575-110">然後，您可以使用指令 `ConvertFrom-Json` 程式，將 json 格式的字串轉換成 json 物件，在 PowerShell 中輕鬆地加以管理。</span><span class="sxs-lookup"><span data-stu-id="22575-110">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="22575-111">許多網站都使用 JSON 而不是 XML 來將資料序列化，以便在伺服器與 Web 應用程式之間進行通訊。</span><span class="sxs-lookup"><span data-stu-id="22575-111">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="22575-112">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="22575-112">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="22575-113">範例</span><span class="sxs-lookup"><span data-stu-id="22575-113">EXAMPLES</span></span>

### <span data-ttu-id="22575-114">範例 1</span><span class="sxs-lookup"><span data-stu-id="22575-114">Example 1</span></span>

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
  "MinSupportedDateTime": "0001-01-01T00:00:00",
  "MaxSupportedDateTime": "9999-12-31T23:59:59.9999999",
  "AlgorithmType": 1,
  "CalendarType": 1,
  "Eras": [
    1
  ],
  "TwoDigitYearMax": 2029,
  "IsReadOnly": true
}
```

<span data-ttu-id="22575-115">此命令會使用 `ConvertTo-Json` Cmdlet 將 GregorianCalendar 物件轉換成 JSON 格式的字串。</span><span class="sxs-lookup"><span data-stu-id="22575-115">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="22575-116">範例 2</span><span class="sxs-lookup"><span data-stu-id="22575-116">Example 2</span></span>

```powershell
Get-Date | ConvertTo-Json; Get-Date | ConvertTo-Json -AsArray
```

```Output
{
  "value": "2018-10-12T23:07:18.8450248-05:00",
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 11:07:18 PM"
}
[
  {
    "value": "2018-10-12T23:07:18.8480668-05:00",
    "DisplayHint": 2,
    "DateTime": "October 12, 2018 11:07:18 PM"
  }
]
```

<span data-ttu-id="22575-117">此範例會顯示 Cmdlet 的輸出， `ConvertTo-Json` 以及不含 **AsArray** 交換器參數的和。</span><span class="sxs-lookup"><span data-stu-id="22575-117">This example shows the output from `ConvertTo-Json` cmdlet with and without the **AsArray** switch parameter.</span></span> <span data-ttu-id="22575-118">您可以看到輸出的第二個部分是以陣列括弧括住。</span><span class="sxs-lookup"><span data-stu-id="22575-118">You can see the second portion of the output is wrapped in array brackets.</span></span>

### <span data-ttu-id="22575-119">範例 3</span><span class="sxs-lookup"><span data-stu-id="22575-119">Example 3</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="22575-120">此命令會顯示使用 **壓縮** 參數的效果 `ConvertTo-Json` 。</span><span class="sxs-lookup"><span data-stu-id="22575-120">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="22575-121">壓縮只會影響字串的外觀，不會影響其有效性。</span><span class="sxs-lookup"><span data-stu-id="22575-121">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="22575-122">範例 4</span><span class="sxs-lookup"><span data-stu-id="22575-122">Example 4</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 10:55:32 PM",
  "Date": "2018-10-12T00:00:00-05:00",
  "Day": 12,
  "DayOfWeek": 5,
  "DayOfYear": 285,
  "Hour": 22,
  "Kind": 2,
  "Millisecond": 639,
  "Minute": 55,
  "Month": 10,
  "Second": 32,
  "Ticks": 636749817326397744,
  "TimeOfDay": {
    "Ticks": 825326397744,
    "Days": 0,
    "Hours": 22,
    "Milliseconds": 639,
    "Minutes": 55,
    "Seconds": 32,
    "TotalDays": 0.95523888627777775,
    "TotalHours": 22.925733270666665,
    "TotalMilliseconds": 82532639.774400011,
    "TotalMinutes": 1375.54399624,
    "TotalSeconds": 82532.6397744
  },
  "Year": 2018
}
```

<span data-ttu-id="22575-123">此範例會使用 `ConvertTo-Json` Cmdlet 將 system.string 物件 **System.DateTime** 從 CMDLET 轉換成 `Get-Date` JSON 格式的字串。</span><span class="sxs-lookup"><span data-stu-id="22575-123">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="22575-124">此命令會使用 `Select-Object` Cmdlet 取得 `*` **DateTime** 物件的所有屬性 () 。</span><span class="sxs-lookup"><span data-stu-id="22575-124">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="22575-125">輸出會顯示傳回的 JSON 字串 `ConvertTo-Json` 。</span><span class="sxs-lookup"><span data-stu-id="22575-125">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="22575-126">範例 5</span><span class="sxs-lookup"><span data-stu-id="22575-126">Example 5</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : October 12, 2018 10:55:52 PM
Date        : 2018-10-12 12:00:00 AM
Day         : 12
DayOfWeek   : 5
DayOfYear   : 285
Hour        : 22
Kind        : 2
Millisecond : 768
Minute      : 55
Month       : 10
Second      : 52
Ticks       : 636749817527683372
TimeOfDay   : @{Ticks=825527683372; Days=0; Hours=22; Milliseconds=768; Minutes=55; Seconds=52;
              TotalDays=0.95547185575463; TotalHours=22.9313245381111; TotalMilliseconds=82552768.3372;
              TotalMinutes=1375.87947228667; TotalSeconds=82552.7683372}
Year        : 2018
```

<span data-ttu-id="22575-127">此範例示範如何使用 `ConvertTo-Json` 和 Cmdlet， `ConvertFrom-Json` 將物件轉換成 json 字串和 json 物件。</span><span class="sxs-lookup"><span data-stu-id="22575-127">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="22575-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="22575-128">PARAMETERS</span></span>

### <span data-ttu-id="22575-129">-AsArray</span><span class="sxs-lookup"><span data-stu-id="22575-129">-AsArray</span></span>

<span data-ttu-id="22575-130">將物件輸出在陣列括弧中，即使輸入是單一物件也一樣。</span><span class="sxs-lookup"><span data-stu-id="22575-130">Outputs the object in array brackets, even if the input is a single object.</span></span>

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

### <span data-ttu-id="22575-131">-Compress</span><span class="sxs-lookup"><span data-stu-id="22575-131">-Compress</span></span>

<span data-ttu-id="22575-132">省略輸出字串中的空白字元和縮排格式。</span><span class="sxs-lookup"><span data-stu-id="22575-132">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="22575-133">-Depth</span><span class="sxs-lookup"><span data-stu-id="22575-133">-Depth</span></span>

<span data-ttu-id="22575-134">指定 JSON 表示法中包含多少層的內含物件。</span><span class="sxs-lookup"><span data-stu-id="22575-134">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="22575-135">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="22575-135">The default value is 2.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22575-136">-EnumsAsStrings</span><span class="sxs-lookup"><span data-stu-id="22575-136">-EnumsAsStrings</span></span>

<span data-ttu-id="22575-137">提供將所有列舉轉換為其字串表示的替代序列化選項。</span><span class="sxs-lookup"><span data-stu-id="22575-137">Provides an alternative serialization option that converts all enumerations to their string representation.</span></span>

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

### <span data-ttu-id="22575-138">-EscapeHandling</span><span class="sxs-lookup"><span data-stu-id="22575-138">-EscapeHandling</span></span>

<span data-ttu-id="22575-139">控制在產生的 JSON 輸出中如何將某些字元轉義。</span><span class="sxs-lookup"><span data-stu-id="22575-139">Controls how certain characters are escaped in the resulting JSON output.</span></span> <span data-ttu-id="22575-140">根據預設，只會將控制字元 (例如換行) 。</span><span class="sxs-lookup"><span data-stu-id="22575-140">By default, only control characters (like newline) are escaped.</span></span>

<span data-ttu-id="22575-141">可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="22575-141">Acceptable values are:</span></span>

- <span data-ttu-id="22575-142">僅限預設的控制字元會進行轉義。</span><span class="sxs-lookup"><span data-stu-id="22575-142">Default - Only control characters are escaped.</span></span>
- <span data-ttu-id="22575-143">EscapeNonAscii-所有非 ASCII 字元和控制字元都會進行轉義。</span><span class="sxs-lookup"><span data-stu-id="22575-143">EscapeNonAscii - All non-ASCII and control characters are escaped.</span></span>
- <span data-ttu-id="22575-144">EscapeHtml-HTML (`<` 、 `>` 、 `&` 、 `'` 、 `"`) 和控制字元都經過轉義。</span><span class="sxs-lookup"><span data-stu-id="22575-144">EscapeHtml - HTML (`<`, `>`, `&`, `'`, `"`) and control characters are escaped.</span></span>

<span data-ttu-id="22575-145">此參數是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="22575-145">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: Newtonsoft.Json.StringEscapeHandling
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="22575-146">-InputObject</span><span class="sxs-lookup"><span data-stu-id="22575-146">-InputObject</span></span>

<span data-ttu-id="22575-147">指定要轉換成 JSON 格式的物件。</span><span class="sxs-lookup"><span data-stu-id="22575-147">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="22575-148">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="22575-148">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="22575-149">您也可以使用管線將物件傳送至 `ConvertTo-Json` 。</span><span class="sxs-lookup"><span data-stu-id="22575-149">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="22575-150">需要 **InputObject** 參數，但其值可以是 null (`$null`) 或空字串。</span><span class="sxs-lookup"><span data-stu-id="22575-150">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="22575-151">當輸入物件是時 `$null` ，不 `ConvertTo-Json` 會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="22575-151">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="22575-152">當輸入物件為空字串時，會傳回 `ConvertTo-Json` 空字串。</span><span class="sxs-lookup"><span data-stu-id="22575-152">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="22575-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="22575-153">CommonParameters</span></span>

<span data-ttu-id="22575-154">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="22575-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="22575-155">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="22575-155">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="22575-156">輸入</span><span class="sxs-lookup"><span data-stu-id="22575-156">INPUTS</span></span>

### <span data-ttu-id="22575-157">System.Object</span><span class="sxs-lookup"><span data-stu-id="22575-157">System.Object</span></span>

<span data-ttu-id="22575-158">您可以透過管線將任何物件傳送至 `ConvertTo-Json` 。</span><span class="sxs-lookup"><span data-stu-id="22575-158">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="22575-159">輸出</span><span class="sxs-lookup"><span data-stu-id="22575-159">OUTPUTS</span></span>

### <span data-ttu-id="22575-160">System.String</span><span class="sxs-lookup"><span data-stu-id="22575-160">System.String</span></span>

## <span data-ttu-id="22575-161">注意</span><span class="sxs-lookup"><span data-stu-id="22575-161">NOTES</span></span>

<span data-ttu-id="22575-162">此 `ConvertTo-Json` Cmdlet 會使用 [Newtonsoft Json.NET](https://www.newtonsoft.com/json)來執行。</span><span class="sxs-lookup"><span data-stu-id="22575-162">The `ConvertTo-Json` cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

## <span data-ttu-id="22575-163">相關連結</span><span class="sxs-lookup"><span data-stu-id="22575-163">RELATED LINKS</span></span>

<span data-ttu-id="22575-164">[JavaScript 和 .NET 中的 JavaScript 物件標記法 (JSON) 簡介](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="22575-164">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="22575-165">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="22575-165">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="22575-166">Get-Content</span><span class="sxs-lookup"><span data-stu-id="22575-166">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="22575-167">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="22575-167">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="22575-168">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="22575-168">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="22575-169">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="22575-169">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="22575-170">NewtonSoft.Js開啟。StringEscapeHandling</span><span class="sxs-lookup"><span data-stu-id="22575-170">NewtonSoft.Json.StringEscapeHandling</span></span>](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)

