---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: f2159a2de3432aec14fb395b93ed476f349616a8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203359"
---
# <span data-ttu-id="09a0e-103">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="09a0e-103">ConvertFrom-Json</span></span>

## <span data-ttu-id="09a0e-104">概要</span><span class="sxs-lookup"><span data-stu-id="09a0e-104">SYNOPSIS</span></span>
<span data-ttu-id="09a0e-105">將 JSON 格式的字串轉換成自訂物件。</span><span class="sxs-lookup"><span data-stu-id="09a0e-105">Converts a JSON-formatted string to a custom object.</span></span>

## <span data-ttu-id="09a0e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="09a0e-106">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [<CommonParameters>]
```

## <span data-ttu-id="09a0e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="09a0e-107">DESCRIPTION</span></span>

<span data-ttu-id="09a0e-108">`ConvertFrom-Json`Cmdlet 會將 JavaScript 物件標記法 (json) 格式化的字串轉換成自訂 **PSCustomObject** 物件，該物件具有 json 字串中每個欄位的屬性。</span><span class="sxs-lookup"><span data-stu-id="09a0e-108">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="09a0e-109">JSON 一般由網站用於提供物件的文字表示方式。</span><span class="sxs-lookup"><span data-stu-id="09a0e-109">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="09a0e-110">JSON 標準不會禁止 **PSCustomObject** 禁止使用。</span><span class="sxs-lookup"><span data-stu-id="09a0e-110">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject** .</span></span> <span data-ttu-id="09a0e-111">例如，如果 JSON 字串包含重複的索引鍵，則這個 Cmdlet 只會使用最後一個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="09a0e-111">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="09a0e-112">請參閱下列其他範例。</span><span class="sxs-lookup"><span data-stu-id="09a0e-112">See other examples below.</span></span>

<span data-ttu-id="09a0e-113">若要從任何物件產生 JSON 字串，請使用 `ConvertTo-Json` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="09a0e-113">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="09a0e-114">此 Cmdlet 是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="09a0e-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="09a0e-115">此 Cmdlet 不支援具有批註的 JSON。</span><span class="sxs-lookup"><span data-stu-id="09a0e-115">This cmdlet doesn't support JSON with comments.</span></span>

## <span data-ttu-id="09a0e-116">範例</span><span class="sxs-lookup"><span data-stu-id="09a0e-116">EXAMPLES</span></span>

### <span data-ttu-id="09a0e-117">範例1：將 DateTime 物件轉換成 JSON 物件</span><span class="sxs-lookup"><span data-stu-id="09a0e-117">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="09a0e-118">此命令會使用 `ConvertTo-Json` 和 `ConvertFrom-Json` Cmdlet，將 **DateTime** 物件從 Cmdlet 轉換成 `Get-Date` JSON 物件，再轉換為 **PSCustomObject** 。</span><span class="sxs-lookup"><span data-stu-id="09a0e-118">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject** .</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : Friday, January 13, 2012 8:06:31 PM
Date        : 1/13/2012 8:00:00 AM
Day         : 13
DayOfWeek   : 5
DayOfYear   : 13
Hour        : 20
Kind        : 2
Millisecond : 400
Minute      : 6
Month       : 1
Second      : 31
Ticks       : 634620819914009002
TimeOfDay   : @{Ticks=723914009002; Days=0; Hours=20; Milliseconds=400; Minutes=6; Seconds=31; TotalDays=0.83786343634490734; TotalHours=20.108722472277776; TotalMilliseconds=72391400.900200009; TotalMinutes=1206.5233483366667;TotalSeconds=72391.4009002}
Year        : 2012
```

<span data-ttu-id="09a0e-119">此範例會使用 `Select-Object` Cmdlet 來取得 **DateTime** 物件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="09a0e-119">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="09a0e-120">它會使用 `ConvertTo-Json` Cmdlet 將 **DateTime** 物件轉換成格式化為 json 物件的字串，並使用 `ConvertFrom-Json` Cmdlet 將 JSON 格式的字串轉換成 **PSCustomObject** 物件。</span><span class="sxs-lookup"><span data-stu-id="09a0e-120">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="09a0e-121">範例2：從 web 服務取得 JSON 字串，並將其轉換為 PowerShell 物件</span><span class="sxs-lookup"><span data-stu-id="09a0e-121">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="09a0e-122">此命令會使用 `Invoke-WebRequest` Cmdlet 從 web 服務取得 json 字串，然後使用 `ConvertFrom-Json` CMDLET 將 json 內容轉換成可在 PowerShell 中管理的物件。</span><span class="sxs-lookup"><span data-stu-id="09a0e-122">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="09a0e-123">您也可以使用 `Invoke-RestMethod` Cmdlet，它會自動將 JSON 內容轉換成物件。</span><span class="sxs-lookup"><span data-stu-id="09a0e-123">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="09a0e-124">範例3：將 JSON 字串轉換為自訂物件</span><span class="sxs-lookup"><span data-stu-id="09a0e-124">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="09a0e-125">此範例說明如何使用 Cmdlet 將 `ConvertFrom-Json` JSON 檔案轉換成 PowerShell 自訂物件。</span><span class="sxs-lookup"><span data-stu-id="09a0e-125">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="09a0e-126">命令會使用 Get-Content Cmdlet 來取得 JSON 檔案中的字串。</span><span class="sxs-lookup"><span data-stu-id="09a0e-126">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="09a0e-127">然後，它會使用管線運算子將分隔的字串傳送至 `ConvertFrom-Json` Cmdlet，以將它轉換成自訂物件。</span><span class="sxs-lookup"><span data-stu-id="09a0e-127">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

## <span data-ttu-id="09a0e-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="09a0e-128">PARAMETERS</span></span>

### <span data-ttu-id="09a0e-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="09a0e-129">-InputObject</span></span>

<span data-ttu-id="09a0e-130">指定 JSON 字串以轉換成 JSON 物件。</span><span class="sxs-lookup"><span data-stu-id="09a0e-130">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="09a0e-131">輸入包含字串的變數，或輸入可取得字串的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="09a0e-131">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="09a0e-132">您也可以使用管線將字串傳送至 `ConvertFrom-Json` 。</span><span class="sxs-lookup"><span data-stu-id="09a0e-132">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="09a0e-133">**InputObject** 是必要參數，但其值可以是空字串。</span><span class="sxs-lookup"><span data-stu-id="09a0e-133">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="09a0e-134">當輸入物件為空字串時，不 `ConvertFrom-Json` 會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="09a0e-134">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="09a0e-135">**InputObject** 值不能是 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="09a0e-135">The **InputObject** value cannot be `$null`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="09a0e-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="09a0e-136">CommonParameters</span></span>

<span data-ttu-id="09a0e-137">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="09a0e-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="09a0e-138">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="09a0e-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="09a0e-139">輸入</span><span class="sxs-lookup"><span data-stu-id="09a0e-139">INPUTS</span></span>

### <span data-ttu-id="09a0e-140">System.String</span><span class="sxs-lookup"><span data-stu-id="09a0e-140">System.String</span></span>

<span data-ttu-id="09a0e-141">您可以使用管線將 JSON 字串傳送至 `ConvertFrom-Json` 。</span><span class="sxs-lookup"><span data-stu-id="09a0e-141">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="09a0e-142">輸出</span><span class="sxs-lookup"><span data-stu-id="09a0e-142">OUTPUTS</span></span>

### <span data-ttu-id="09a0e-143">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="09a0e-143">PSCustomObject</span></span>

## <span data-ttu-id="09a0e-144">注意</span><span class="sxs-lookup"><span data-stu-id="09a0e-144">NOTES</span></span>

<span data-ttu-id="09a0e-145">此 `ConvertFrom-Json` Cmdlet 會使用 [JavaScriptSerializer 類別](/dotnet/api/system.web.script.serialization.javascriptserializer)來執行。</span><span class="sxs-lookup"><span data-stu-id="09a0e-145">The `ConvertFrom-Json` cmdlet is implemented using the [JavaScriptSerializer class](/dotnet/api/system.web.script.serialization.javascriptserializer).</span></span>

## <span data-ttu-id="09a0e-146">相關連結</span><span class="sxs-lookup"><span data-stu-id="09a0e-146">RELATED LINKS</span></span>

<span data-ttu-id="09a0e-147">[JavaScript 和 .NET 中的 JavaScript 物件標記法 (JSON) 簡介](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="09a0e-147">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="09a0e-148">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="09a0e-148">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="09a0e-149">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="09a0e-149">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="09a0e-150">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="09a0e-150">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
