---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/19/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/test-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Json
ms.openlocfilehash: 79cf0d9a8107cbf843eba5c58e4b4e9ad30ad285
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202163"
---
# <span data-ttu-id="8f7f6-103">Test-Json</span><span class="sxs-lookup"><span data-stu-id="8f7f6-103">Test-Json</span></span>

## <span data-ttu-id="8f7f6-104">概要</span><span class="sxs-lookup"><span data-stu-id="8f7f6-104">SYNOPSIS</span></span>
<span data-ttu-id="8f7f6-105">測試字串是否為有效的 JSON 檔</span><span class="sxs-lookup"><span data-stu-id="8f7f6-105">Tests whether a string is a valid JSON document</span></span>

## <span data-ttu-id="8f7f6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8f7f6-106">SYNTAX</span></span>

### <span data-ttu-id="8f7f6-107">__AllParameterSets (預設) </span><span class="sxs-lookup"><span data-stu-id="8f7f6-107">__AllParameterSets (Default)</span></span>
```
Test-Json [-Json] <String> [<CommonParameters>]
```

### <span data-ttu-id="8f7f6-108">SchemaString</span><span class="sxs-lookup"><span data-stu-id="8f7f6-108">SchemaString</span></span>
```
Test-Json [-Json] <String> [[-Schema] <String>] [<CommonParameters>]
```

### <span data-ttu-id="8f7f6-109">SchemaFile</span><span class="sxs-lookup"><span data-stu-id="8f7f6-109">SchemaFile</span></span>
```
Test-Json [-Json] <String> [-SchemaFile <String>] [<CommonParameters>]
```

## <span data-ttu-id="8f7f6-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f7f6-110">DESCRIPTION</span></span>

<span data-ttu-id="8f7f6-111">此 `Test-Json` Cmdlet 會測試字串是否為有效的 JavaScript 物件標記法 (JSON) 檔，並且可以選擇性地根據提供的架構來驗證 json 檔。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-111">The `Test-Json` cmdlet tests whether a string is a valid JavaScript Object Notation (JSON) document and can optionally verify that JSON document against a provided schema.</span></span>

<span data-ttu-id="8f7f6-112">然後，已驗證的字串可以與 Cmdlet 搭配使用 `ConvertFrom-Json` ，將 json 格式的字串轉換成 json 物件，此物件可在 PowerShell 中輕鬆管理，或傳送到存取 JSON 輸入的其他程式或 web 服務。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-112">The verified string can then be used with the `ConvertFrom-Json` cmdlet convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell or sent to another program or web service that access JSON input.</span></span>

<span data-ttu-id="8f7f6-113">許多網站都使用 JSON 而不是 XML 來將資料序列化，以便在伺服器與 Web 應用程式之間進行通訊。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-113">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="8f7f6-114">此 Cmdlet 是在 PowerShell 6.1 中引進</span><span class="sxs-lookup"><span data-stu-id="8f7f6-114">This cmdlet was introduced in PowerShell 6.1</span></span>

## <span data-ttu-id="8f7f6-115">範例</span><span class="sxs-lookup"><span data-stu-id="8f7f6-115">EXAMPLES</span></span>

### <span data-ttu-id="8f7f6-116">範例1：測試物件是否為有效的 JSON</span><span class="sxs-lookup"><span data-stu-id="8f7f6-116">Example 1: Test if an object is valid JSON</span></span>

<span data-ttu-id="8f7f6-117">此範例會測試輸入字串是否為有效的 JSON 檔。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-117">This example tests whether the input string is a valid JSON document.</span></span>

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### <span data-ttu-id="8f7f6-118">範例2：針對提供的架構測試物件</span><span class="sxs-lookup"><span data-stu-id="8f7f6-118">Example 2: Test an object against a provided schema</span></span>

<span data-ttu-id="8f7f6-119">此範例會採用包含 JSON 架構的字串，並將它與輸入字串進行比較。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-119">This example takes a string containing a JSON schema and compares it to an input string.</span></span>

```powershell
$schema = @'
{
  "definitions": {},
  "$schema": "http://json-schema.org/draft-07/schema#",
  "$id": "http://example.com/root.json",
  "type": "object",
  "title": "The Root Schema",
  "required": [
    "name",
    "age"
  ],
  "properties": {
    "name": {
      "$id": "#/properties/name",
      "type": "string",
      "title": "The Name Schema",
      "default": "",
      "examples": [
        "Ashley"
      ],
      "pattern": "^(.*)$"
    },
    "age": {
      "$id": "#/properties/age",
      "type": "integer",
      "title": "The Age Schema",
      "default": 0,
      "examples": [
        25
      ]
    }
  }
}
'@
"{'name': 'Ashley', 'age': '25'}" | Test-Json -Schema $schema
```

```Output
Test-Json : IntegerExpected: #/age
At line:1 char:37
+ "{'name': 'Ashley', 'age': '25'}" | Test-Json -Schema $schema
+                                     ~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (:) [Test-Json], Exception
+ FullyQualifiedErrorId : InvalidJsonAgainstSchema,Microsoft.PowerShell.Commands.TestJsonCommand
False
```

<span data-ttu-id="8f7f6-120">在此範例中，我們會收到錯誤，因為架構的 **存留期** 必須是整數，但我們所測試的 JSON 輸入會改為使用字串值。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-120">In this example, we get an error because the schema expects an integer for **age** but the JSON input we tested uses a string value instead.</span></span>

<span data-ttu-id="8f7f6-121">如需詳細資訊，請參閱 [JSON 架構](https://json-schema.org/)。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-121">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

### <span data-ttu-id="8f7f6-122">範例3：根據檔案的架構測試物件</span><span class="sxs-lookup"><span data-stu-id="8f7f6-122">Example 3: Test an object against a schema from file</span></span>

<span data-ttu-id="8f7f6-123">JSON 架構可以參考使用 `$ref` 關鍵字的定義。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-123">JSON schema can reference definitions using `$ref` keyword.</span></span> <span data-ttu-id="8f7f6-124">`$ref`可以解析為參考另一個檔案的 URI。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-124">The `$ref` can resolve to a URI that references another file.</span></span> <span data-ttu-id="8f7f6-125">`SchemaFile`參數接受 json 架構檔案的常值路徑，並允許針對這類架構驗證 json 檔案。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-125">The `SchemaFile` parameter accepts literal path to the JSON schema file and allows JSON files to be validated against such schemas.</span></span>

<span data-ttu-id="8f7f6-126">在此範例中，我們有一個 `schema.json` 參考的檔案 `definitions.json` 。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-126">In this example we have `schema.json` file which references `definitions.json`.</span></span>

```powershell
PS> Get-Content schema.json

{
  "description":"A person",
  "type":"object",
  "properties":{
    "name":{
      "$ref":"definitions.json#/definitions/name"
    },
    "hobbies":{
      "$ref":"definitions.json#/definitions/hobbies"
    }
  }
}

PS> Get-Content definitions.json

{
  "definitions":{
    "name":{
      "type":"string"
    },
    "hobbies":{
      "type":"array",
      "items":{
        "type":"string"
      }
    }
  }
}

'{"name": "James", "hobbies": [".NET", "Blogging"]}' | Test-Json -SchemaFile 'schema.json'
```

```Output
True
```

<span data-ttu-id="8f7f6-127">如需詳細資訊，請參閱 [結構化複雜的架構](https://json-schema.org/understanding-json-schema/structuring.html)。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-127">For more information, see [Structuring a complex schema](https://json-schema.org/understanding-json-schema/structuring.html).</span></span>

## <span data-ttu-id="8f7f6-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8f7f6-128">PARAMETERS</span></span>

### <span data-ttu-id="8f7f6-129">-Json</span><span class="sxs-lookup"><span data-stu-id="8f7f6-129">-Json</span></span>

<span data-ttu-id="8f7f6-130">指定要測試有效性的 JSON 字串。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-130">Specifies the JSON string to test for validity.</span></span> <span data-ttu-id="8f7f6-131">輸入包含字串的變數，或輸入可取得字串的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-131">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="8f7f6-132">您也可以使用管線將字串傳送至 `Test-Json` 。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-132">You can also pipe a string to `Test-Json`.</span></span>

<span data-ttu-id="8f7f6-133">需要 **Json** 參數。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-133">The **Json** parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8f7f6-134">-架構</span><span class="sxs-lookup"><span data-stu-id="8f7f6-134">-Schema</span></span>

<span data-ttu-id="8f7f6-135">指定要對其驗證 JSON 輸入的架構。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-135">Specifies a Schema to validate the JSON input against.</span></span> <span data-ttu-id="8f7f6-136">如果通過，則 `Test-Json` 會驗證 Json 輸入是否符合 **架構** 參數所指定的規格，而且 `$True` 只有在輸入符合提供的架構時，才會傳回。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-136">If passed `Test-Json` will validate that the Json input conforms to the spec specified by the **Schema** parameter and return `$True` only if the input conforms to the provided Schema.</span></span>

<span data-ttu-id="8f7f6-137">如需詳細資訊，請參閱 [JSON 架構](https://json-schema.org/)。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-137">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

```yaml
Type: System.String
Parameter Sets: SchemaString
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f7f6-138">-SchemaFile</span><span class="sxs-lookup"><span data-stu-id="8f7f6-138">-SchemaFile</span></span>

<span data-ttu-id="8f7f6-139">指定用來驗證 JSON 輸入的架構檔案。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-139">Specifies a schema file used to validate the JSON input.</span></span> <span data-ttu-id="8f7f6-140">使用時， `Test-Json` `$True` 只有當 JSON 輸入符合 **SchemaFile** 參數所指定的檔案中所定義的架構時，才會傳回。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-140">When used, the `Test-Json` returns `$True` only if the JSON input conforms to the Schema defined in the file specified by the **SchemaFile** parameter.</span></span>

<span data-ttu-id="8f7f6-141">如需詳細資訊，請參閱 [JSON 架構](https://json-schema.org/)。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-141">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

```yaml
Type: System.String
Parameter Sets: SchemaFile
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8f7f6-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8f7f6-142">CommonParameters</span></span>

<span data-ttu-id="8f7f6-143">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8f7f6-144">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8f7f6-145">輸入</span><span class="sxs-lookup"><span data-stu-id="8f7f6-145">INPUTS</span></span>

### <span data-ttu-id="8f7f6-146">System.String</span><span class="sxs-lookup"><span data-stu-id="8f7f6-146">System.String</span></span>

<span data-ttu-id="8f7f6-147">您可以使用管線將 JSON 字串傳送至 `Test-Json` 。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-147">You can pipe a JSON string to `Test-Json`.</span></span>

## <span data-ttu-id="8f7f6-148">輸出</span><span class="sxs-lookup"><span data-stu-id="8f7f6-148">OUTPUTS</span></span>

### <span data-ttu-id="8f7f6-149">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f7f6-149">Boolean</span></span>

## <span data-ttu-id="8f7f6-150">注意</span><span class="sxs-lookup"><span data-stu-id="8f7f6-150">NOTES</span></span>

<span data-ttu-id="8f7f6-151">此 `Test-Json` Cmdlet 會使用 [NJsonSchema 類別](https://github.com/RSuter/NJsonSchema)來執行。</span><span class="sxs-lookup"><span data-stu-id="8f7f6-151">The `Test-Json` cmdlet is implemented by using the [NJsonSchema Class](https://github.com/RSuter/NJsonSchema).</span></span>

## <span data-ttu-id="8f7f6-152">相關連結</span><span class="sxs-lookup"><span data-stu-id="8f7f6-152">RELATED LINKS</span></span>

<span data-ttu-id="8f7f6-153">[JavaScript 和 .NET 中的 JavaScript 物件標記法 (JSON) 簡介](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="8f7f6-153">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="8f7f6-154">其他 JSON 架構詳細資料</span><span class="sxs-lookup"><span data-stu-id="8f7f6-154">Additional JSON Schema Details</span></span>](https://json-schema.org/)

[<span data-ttu-id="8f7f6-155">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="8f7f6-155">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="8f7f6-156">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="8f7f6-156">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="8f7f6-157">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="8f7f6-157">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
