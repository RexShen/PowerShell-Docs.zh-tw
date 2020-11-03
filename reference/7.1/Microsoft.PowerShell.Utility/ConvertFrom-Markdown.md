---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell、Cmdlet、markdown
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-markdown?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Markdown
ms.openlocfilehash: 9f070819491b87b02868dffdfbe25bf5d72ecab8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204764"
---
# <span data-ttu-id="451c8-103">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="451c8-103">ConvertFrom-Markdown</span></span>

## <span data-ttu-id="451c8-104">概要</span><span class="sxs-lookup"><span data-stu-id="451c8-104">SYNOPSIS</span></span>
<span data-ttu-id="451c8-105">將字串或檔案的內容轉換為 **MarkdownInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="451c8-105">Convert the contents of a string or a file to a **MarkdownInfo** object.</span></span>

## <span data-ttu-id="451c8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="451c8-106">SYNTAX</span></span>

### <span data-ttu-id="451c8-107">PathParamSet (預設) </span><span class="sxs-lookup"><span data-stu-id="451c8-107">PathParamSet (Default)</span></span>

```
ConvertFrom-Markdown [-Path] <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### <span data-ttu-id="451c8-108">LiteralParamSet</span><span class="sxs-lookup"><span data-stu-id="451c8-108">LiteralParamSet</span></span>

```
ConvertFrom-Markdown -LiteralPath <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### <span data-ttu-id="451c8-109">InputObjParamSet</span><span class="sxs-lookup"><span data-stu-id="451c8-109">InputObjParamSet</span></span>

```
ConvertFrom-Markdown -InputObject <PSObject> [-AsVT100EncodedString] [<CommonParameters>]
```

## <span data-ttu-id="451c8-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="451c8-110">DESCRIPTION</span></span>

<span data-ttu-id="451c8-111">此 Cmdlet 會將指定的內容轉換為 **MarkdownInfo** 。</span><span class="sxs-lookup"><span data-stu-id="451c8-111">This cmdlet converts the specified content into a **MarkdownInfo** .</span></span> <span data-ttu-id="451c8-112">針對 **path** 參數指定檔案路徑時，會轉換檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="451c8-112">When a file path is specified for the **Path** parameter, the contents on the file are converted.</span></span> <span data-ttu-id="451c8-113">輸出物件有三個屬性：</span><span class="sxs-lookup"><span data-stu-id="451c8-113">The output object has three properties:</span></span>

- <span data-ttu-id="451c8-114">**Token** 屬性具有已轉換物件 (AST) 的抽象語法樹狀結構</span><span class="sxs-lookup"><span data-stu-id="451c8-114">The **Token** property has the abstract syntax tree (AST) of the the converted object</span></span>
- <span data-ttu-id="451c8-115">**Html** 屬性具有指定輸入的 html 轉換</span><span class="sxs-lookup"><span data-stu-id="451c8-115">The **Html** property has the HTML conversion of the specified input</span></span>
- <span data-ttu-id="451c8-116">如果指定 **AsVT100EncodedString** 參數，則 **VT100ENCODEDSTRING** 屬性具有 ANSI (VT100) escape 序列的已轉換字串</span><span class="sxs-lookup"><span data-stu-id="451c8-116">The **VT100EncodedString** property has the converted string with ANSI (VT100) escape sequences if the **AsVT100EncodedString** parameter was specified</span></span>

<span data-ttu-id="451c8-117">此 Cmdlet 是在 PowerShell 6.1 中引進。</span><span class="sxs-lookup"><span data-stu-id="451c8-117">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="451c8-118">範例</span><span class="sxs-lookup"><span data-stu-id="451c8-118">EXAMPLES</span></span>

### <span data-ttu-id="451c8-119">範例1：將包含 Markdown 內容的檔案轉換成 HTML</span><span class="sxs-lookup"><span data-stu-id="451c8-119">Example 1: Convert a file containing Markdown content to HTML</span></span>

```powershell
ConvertFrom-Markdown -Path .\README.md
```

<span data-ttu-id="451c8-120">傳回 **MarkdownInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="451c8-120">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="451c8-121">Token **屬性具有** 已轉換之檔案內容的 AST `README.md` 。</span><span class="sxs-lookup"><span data-stu-id="451c8-121">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="451c8-122">**Html** 屬性具有 html 轉換的檔案內容 `README.md` 。</span><span class="sxs-lookup"><span data-stu-id="451c8-122">The **Html** property has the HTML converted content of the `README.md` file.</span></span>

### <span data-ttu-id="451c8-123">範例2：將包含 Markdown 內容的檔案轉換成 VT100 編碼的字串</span><span class="sxs-lookup"><span data-stu-id="451c8-123">Example 2: Convert a file containing Markdown content to a VT100-encoded string</span></span>

```powershell
ConvertFrom-Markdown -Path .\README.md -AsVT100EncodedString
```

<span data-ttu-id="451c8-124">傳回 **MarkdownInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="451c8-124">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="451c8-125">Token **屬性具有** 已轉換之檔案內容的 AST `README.md` 。</span><span class="sxs-lookup"><span data-stu-id="451c8-125">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="451c8-126">**VT100EncodedString** 屬性具有已轉換之檔案內容的 VT100 編碼字串 `README.md` 。</span><span class="sxs-lookup"><span data-stu-id="451c8-126">The **VT100EncodedString** property has the VT100-encoded string converted content of the `README.md` file.</span></span>

### <span data-ttu-id="451c8-127">範例3：將包含 Markdown 內容的輸入物件轉換成 VT100 編碼的字串</span><span class="sxs-lookup"><span data-stu-id="451c8-127">Example 3: Convert input object containing Markdown content to a VT100-encoded string</span></span>

```powershell
Get-Item .\README.md | ConvertFrom-Markdown -AsVT100EncodedString
```

<span data-ttu-id="451c8-128">傳回 **MarkdownInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="451c8-128">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="451c8-129">的 **FileInfo** 物件 `Get-Item` 會轉換成 VT100 編碼的字串。</span><span class="sxs-lookup"><span data-stu-id="451c8-129">The **FileInfo** object from `Get-Item` is converted to a VT100-encoded string.</span></span> <span data-ttu-id="451c8-130">Token **屬性具有** 已轉換之檔案內容的 AST `README.md` 。</span><span class="sxs-lookup"><span data-stu-id="451c8-130">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="451c8-131">**VT100EncodedString** 屬性具有已轉換之檔案內容的 VT100 編碼字串 `README.md` 。</span><span class="sxs-lookup"><span data-stu-id="451c8-131">The **VT100EncodedString** property has the VT100-encoded string converted content of the `README.md` file.</span></span>

### <span data-ttu-id="451c8-132">範例4：將包含 Markdown 內容的字串轉換成 VT100 編碼的字串</span><span class="sxs-lookup"><span data-stu-id="451c8-132">Example 4: Convert a string containing Markdown content to a VT100-encoded string</span></span>

```powershell
"**Bold text**" | ConvertFrom-Markdown -AsVT100EncodedString
```

<span data-ttu-id="451c8-133">傳回 **MarkdownInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="451c8-133">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="451c8-134">指定的字串 `**Bold text**` 會轉換為 VT100 編碼的字串，並可在 **VT100EncodedString** 屬性中使用。</span><span class="sxs-lookup"><span data-stu-id="451c8-134">The specified string `**Bold text**` is converted to a VT100-encoded string and available in **VT100EncodedString** property.</span></span>

## <span data-ttu-id="451c8-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="451c8-135">PARAMETERS</span></span>

### <span data-ttu-id="451c8-136">-AsVT100EncodedString</span><span class="sxs-lookup"><span data-stu-id="451c8-136">-AsVT100EncodedString</span></span>

<span data-ttu-id="451c8-137">指定是否應將輸出編碼為具有 VT100 escape 代碼的字串。</span><span class="sxs-lookup"><span data-stu-id="451c8-137">Specifies if the output should be encoded as a string with VT100 escape codes.</span></span>

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

### <span data-ttu-id="451c8-138">-InputObject</span><span class="sxs-lookup"><span data-stu-id="451c8-138">-InputObject</span></span>

<span data-ttu-id="451c8-139">指定要轉換的物件。</span><span class="sxs-lookup"><span data-stu-id="451c8-139">Specifies the object to be converted.</span></span> <span data-ttu-id="451c8-140">指定 system.string 類型的物件時 **，會轉換** 字串。</span><span class="sxs-lookup"><span data-stu-id="451c8-140">When an object of type **System.String** is specified, the string is converted.</span></span> <span data-ttu-id="451c8-141">指定 **FileInfo** 類型的物件時，會轉換物件所指定之檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="451c8-141">When an object of type **System.IO.FileInfo** is specified, the contents of the file specified by the object are converted.</span></span> <span data-ttu-id="451c8-142">任何其他類型的物件都會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="451c8-142">Objects of any other type result in an error.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObjParamSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="451c8-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="451c8-143">-LiteralPath</span></span>

<span data-ttu-id="451c8-144">指定要轉換之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="451c8-144">Specifies a path to the file to be converted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralParamSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="451c8-145">-Path</span><span class="sxs-lookup"><span data-stu-id="451c8-145">-Path</span></span>

<span data-ttu-id="451c8-146">指定要轉換之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="451c8-146">Specifies a path to the file to be converted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PathParamSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="451c8-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="451c8-147">CommonParameters</span></span>

<span data-ttu-id="451c8-148">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="451c8-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="451c8-149">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="451c8-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="451c8-150">輸入</span><span class="sxs-lookup"><span data-stu-id="451c8-150">INPUTS</span></span>

### <span data-ttu-id="451c8-151">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="451c8-151">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="451c8-152">輸出</span><span class="sxs-lookup"><span data-stu-id="451c8-152">OUTPUTS</span></span>

### <span data-ttu-id="451c8-153">MarkdownRender. MarkdownInfo</span><span class="sxs-lookup"><span data-stu-id="451c8-153">Microsoft.PowerShell.MarkdownRender.MarkdownInfo</span></span>

## <span data-ttu-id="451c8-154">注意</span><span class="sxs-lookup"><span data-stu-id="451c8-154">NOTES</span></span>

## <span data-ttu-id="451c8-155">相關連結</span><span class="sxs-lookup"><span data-stu-id="451c8-155">RELATED LINKS</span></span>

[<span data-ttu-id="451c8-156">Markdown 剖析器</span><span class="sxs-lookup"><span data-stu-id="451c8-156">Markdown Parser</span></span>](https://github.com/lunet-io/markdig)

[<span data-ttu-id="451c8-157">ANSI 轉義碼</span><span class="sxs-lookup"><span data-stu-id="451c8-157">ANSI escape code</span></span>](https://wikipedia.org/wiki/ANSI_escape_code)

