---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: b91d3b7cbf86c7ea827539903b2e8373cdfdac72
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203335"
---
# <span data-ttu-id="65257-103">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="65257-103">ConvertTo-Json</span></span>

## <span data-ttu-id="65257-104">概要</span><span class="sxs-lookup"><span data-stu-id="65257-104">SYNOPSIS</span></span>
<span data-ttu-id="65257-105">將物件轉換成 JSON 格式的字串。</span><span class="sxs-lookup"><span data-stu-id="65257-105">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="65257-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="65257-106">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
 [<CommonParameters>]
```

## <span data-ttu-id="65257-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="65257-107">DESCRIPTION</span></span>

<span data-ttu-id="65257-108">`ConvertTo-Json`Cmdlet 會將任何 .net 物件轉換成 JavaScript 物件標記法 (JSON) 格式的字串。</span><span class="sxs-lookup"><span data-stu-id="65257-108">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="65257-109">屬性會轉換成欄位名稱、欄位值會轉換成屬性值，而方法會被移除。</span><span class="sxs-lookup"><span data-stu-id="65257-109">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="65257-110">然後，您可以使用指令 `ConvertFrom-Json` 程式，將 json 格式的字串轉換成 json 物件，在 PowerShell 中輕鬆地加以管理。</span><span class="sxs-lookup"><span data-stu-id="65257-110">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="65257-111">許多網站都使用 JSON 而不是 XML 來將資料序列化，以便在伺服器與 Web 應用程式之間進行通訊。</span><span class="sxs-lookup"><span data-stu-id="65257-111">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="65257-112">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="65257-112">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="65257-113">範例</span><span class="sxs-lookup"><span data-stu-id="65257-113">EXAMPLES</span></span>

### <span data-ttu-id="65257-114">範例 1</span><span class="sxs-lookup"><span data-stu-id="65257-114">Example 1</span></span>

```powershell
PS C:\> (Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
    "MinSupportedDateTime":  "\/Date(-62135596800000)\/",
    "MaxSupportedDateTime":  "\/Date(253402300799999)\/",
    "AlgorithmType":  1,
    "CalendarType":  1,
    "Eras":  [
                 1
             ],
    "TwoDigitYearMax":  2029,
    "IsReadOnly":  false
}
```

<span data-ttu-id="65257-115">此命令會使用 `ConvertTo-Json` Cmdlet 將 GregorianCalendar 物件轉換成 JSON 格式的字串。</span><span class="sxs-lookup"><span data-stu-id="65257-115">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="65257-116">範例 2</span><span class="sxs-lookup"><span data-stu-id="65257-116">Example 2</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="65257-117">此命令會顯示使用 **壓縮** 參數的效果 `ConvertTo-Json` 。</span><span class="sxs-lookup"><span data-stu-id="65257-117">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="65257-118">壓縮只會影響字串的外觀，不會影響其有效性。</span><span class="sxs-lookup"><span data-stu-id="65257-118">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="65257-119">範例 3</span><span class="sxs-lookup"><span data-stu-id="65257-119">Example 3</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
    "DisplayHint":  2,
    "DateTime":  "Friday, January 13, 2012 8:06:16 PM",
    "Date":  "\/Date(1326441600000)\/",
    "Day":  13,
    "DayOfWeek":  5,
    "DayOfYear":  13,
    "Hour":  20,
    "Kind":  2,
    "Millisecond":  221,
    "Minute":  6,
    "Month":  1,
    "Second":  16,
    "Ticks":  634620819762218083,
    "TimeOfDay":  {
                      "Ticks":  723762218083,
                      "Days":  0,
                      "Hours":  20,
                      "Milliseconds":  221,
                      "Minutes":  6,
                      "Seconds":  16,
                      "TotalDays":  0.83768775241087956,
                      "TotalHours":  20.104506057861109,
                      "TotalMilliseconds":  72376221.8083,
                      "TotalMinutes":  1206.2703634716668,
                      "TotalSeconds":  72376.22180829999
                  },
    "Year":  2012
}
```

<span data-ttu-id="65257-120">此範例會使用 `ConvertTo-Json` Cmdlet 將 system.string 物件 **System.DateTime** 從 CMDLET 轉換成 `Get-Date` JSON 格式的字串。</span><span class="sxs-lookup"><span data-stu-id="65257-120">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="65257-121">此命令會使用 `Select-Object` Cmdlet 取得 `*` **DateTime** 物件的所有屬性 () 。</span><span class="sxs-lookup"><span data-stu-id="65257-121">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="65257-122">輸出會顯示傳回的 JSON 字串 `ConvertTo-Json` 。</span><span class="sxs-lookup"><span data-stu-id="65257-122">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="65257-123">範例 4</span><span class="sxs-lookup"><span data-stu-id="65257-123">Example 4</span></span>

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

<span data-ttu-id="65257-124">此範例示範如何使用 `ConvertTo-Json` 和 Cmdlet， `ConvertFrom-Json` 將物件轉換成 json 字串和 json 物件。</span><span class="sxs-lookup"><span data-stu-id="65257-124">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="65257-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="65257-125">PARAMETERS</span></span>

### <span data-ttu-id="65257-126">-Compress</span><span class="sxs-lookup"><span data-stu-id="65257-126">-Compress</span></span>

<span data-ttu-id="65257-127">省略輸出字串中的空白字元和縮排格式。</span><span class="sxs-lookup"><span data-stu-id="65257-127">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="65257-128">-Depth</span><span class="sxs-lookup"><span data-stu-id="65257-128">-Depth</span></span>

<span data-ttu-id="65257-129">指定 JSON 表示法中包含多少層的內含物件。</span><span class="sxs-lookup"><span data-stu-id="65257-129">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="65257-130">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="65257-130">The default value is 2.</span></span>

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

### <span data-ttu-id="65257-131">-InputObject</span><span class="sxs-lookup"><span data-stu-id="65257-131">-InputObject</span></span>

<span data-ttu-id="65257-132">指定要轉換成 JSON 格式的物件。</span><span class="sxs-lookup"><span data-stu-id="65257-132">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="65257-133">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="65257-133">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="65257-134">您也可以使用管線將物件傳送至 `ConvertTo-Json` 。</span><span class="sxs-lookup"><span data-stu-id="65257-134">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="65257-135">需要 **InputObject** 參數，但其值可以是 null (`$null`) 或空字串。</span><span class="sxs-lookup"><span data-stu-id="65257-135">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="65257-136">當輸入物件是時 `$null` ，不 `ConvertTo-Json` 會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="65257-136">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="65257-137">當輸入物件為空字串時，會傳回 `ConvertTo-Json` 空字串。</span><span class="sxs-lookup"><span data-stu-id="65257-137">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

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

### <span data-ttu-id="65257-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="65257-138">CommonParameters</span></span>

<span data-ttu-id="65257-139">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="65257-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="65257-140">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="65257-140">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="65257-141">輸入</span><span class="sxs-lookup"><span data-stu-id="65257-141">INPUTS</span></span>

### <span data-ttu-id="65257-142">System.Object</span><span class="sxs-lookup"><span data-stu-id="65257-142">System.Object</span></span>

<span data-ttu-id="65257-143">您可以透過管線將任何物件傳送至 `ConvertTo-Json` 。</span><span class="sxs-lookup"><span data-stu-id="65257-143">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="65257-144">輸出</span><span class="sxs-lookup"><span data-stu-id="65257-144">OUTPUTS</span></span>

### <span data-ttu-id="65257-145">System.String</span><span class="sxs-lookup"><span data-stu-id="65257-145">System.String</span></span>

## <span data-ttu-id="65257-146">注意</span><span class="sxs-lookup"><span data-stu-id="65257-146">NOTES</span></span>

<span data-ttu-id="65257-147">此 `ConvertTo-Json` Cmdlet 會使用 [JavaScriptSerializer 類別](/dotnet/api/system.web.script.serialization.javascriptserializer)來執行。</span><span class="sxs-lookup"><span data-stu-id="65257-147">The `ConvertTo-Json` cmdlet is implemented using the [JavaScriptSerializer class](/dotnet/api/system.web.script.serialization.javascriptserializer).</span></span>

## <span data-ttu-id="65257-148">相關連結</span><span class="sxs-lookup"><span data-stu-id="65257-148">RELATED LINKS</span></span>

<span data-ttu-id="65257-149">[JavaScript 和 .NET 中的 JavaScript 物件標記法 (JSON) 簡介](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="65257-149">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="65257-150">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="65257-150">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="65257-151">Get-Content</span><span class="sxs-lookup"><span data-stu-id="65257-151">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="65257-152">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="65257-152">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="65257-153">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="65257-153">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="65257-154">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="65257-154">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
