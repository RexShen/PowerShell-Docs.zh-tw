---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: f4740bca33bd70d4d8eca51ed45ba6204b5d2acb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202171"
---
# <span data-ttu-id="2d8f9-103">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="2d8f9-103">Show-Markdown</span></span>

## <span data-ttu-id="2d8f9-104">概要</span><span class="sxs-lookup"><span data-stu-id="2d8f9-104">SYNOPSIS</span></span>
<span data-ttu-id="2d8f9-105">使用 VT100 escape 序列或在瀏覽器中使用 HTML，以易記的方式顯示主控台中的 Markdown 檔案或字串。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-105">Shows a Markdown file or string in the console in a friendly way using VT100 escape sequences or in a browser using HTML.</span></span>

## <span data-ttu-id="2d8f9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2d8f9-106">SYNTAX</span></span>

### <span data-ttu-id="2d8f9-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="2d8f9-107">Path (Default)</span></span>

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="2d8f9-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="2d8f9-108">InputObject</span></span>

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="2d8f9-109">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2d8f9-109">LiteralPath</span></span>

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## <span data-ttu-id="2d8f9-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2d8f9-110">DESCRIPTION</span></span>

<span data-ttu-id="2d8f9-111">此 `Show-Markdown` Cmdlet 是用來在終端機或瀏覽器中，以人類看得懂的格式來呈現 Markdown。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-111">The `Show-Markdown` cmdlet is used to render Markdown in a human readable format either in a terminal or in a browser.</span></span>

<span data-ttu-id="2d8f9-112">`Show-Markdown` 可以傳回字串，其中包含當終端機 (的 vt100 escape 序列) 時，它所呈現的 VT100 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-112">`Show-Markdown` can return a string that includes the VT100 escape sequences which the terminal renders (if it supports VT100 escape sequences).</span></span> <span data-ttu-id="2d8f9-113">這主要是用來查看終端機中的 Markdown 檔案。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-113">This is primarily used for viewing Markdown files in a terminal.</span></span> <span data-ttu-id="2d8f9-114">您也可以藉 `ConvertFrom-Markdown` 由指定 **AsVT100EncodedString** 參數，透過來取得這個字串。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-114">You can also get this string via the `ConvertFrom-Markdown` by specifying the **AsVT100EncodedString** parameter.</span></span>

<span data-ttu-id="2d8f9-115">`Show-Markdown` 也可以開啟瀏覽器，並顯示轉譯過的 Markdown 版本。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-115">`Show-Markdown` also has the ability to open a browser and show you a rendered version of the Markdown.</span></span> <span data-ttu-id="2d8f9-116">它會將 Markdown 轉換成 HTML，並在您的預設瀏覽器中開啟 HTML 檔案，以轉譯。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-116">It renders the Markdown by turning it into HTML and opening the HTML file in your default browser.</span></span>

<span data-ttu-id="2d8f9-117">您可以使用來變更 `Show-Markdown` Markdown 在終端機中的呈現方式 `Set-MarkdownOption` 。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-117">You can change how `Show-Markdown` renders Markdown in a terminal by using `Set-MarkdownOption`.</span></span>

<span data-ttu-id="2d8f9-118">此 Cmdlet 是在 PowerShell 6.1 中引進。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-118">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="2d8f9-119">範例</span><span class="sxs-lookup"><span data-stu-id="2d8f9-119">EXAMPLES</span></span>

### <span data-ttu-id="2d8f9-120">範例1：指定路徑的簡單範例</span><span class="sxs-lookup"><span data-stu-id="2d8f9-120">Example 1: Simple example specifying a path</span></span>

```powershell
Show-Markdown -Path ./README.md
```

### <span data-ttu-id="2d8f9-121">範例2：指定字串的簡單範例</span><span class="sxs-lookup"><span data-stu-id="2d8f9-121">Example 2: Simple example specifying a string</span></span>

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### <span data-ttu-id="2d8f9-122">範例2：在瀏覽器中開啟 Markdown</span><span class="sxs-lookup"><span data-stu-id="2d8f9-122">Example 2: Opening Markdown in a browser</span></span>

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## <span data-ttu-id="2d8f9-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2d8f9-123">PARAMETERS</span></span>

### <span data-ttu-id="2d8f9-124">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2d8f9-124">-InputObject</span></span>

<span data-ttu-id="2d8f9-125">將顯示在終端機中的 Markdown 字串。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-125">A Markdown string that will be shown in the terminal.</span></span> <span data-ttu-id="2d8f9-126">如果您未傳入支援的格式， `Show-Markdown` 將會發出錯誤。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-126">If you do not pass in a supported format, `Show-Markdown` will emit an error.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2d8f9-127">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2d8f9-127">-LiteralPath</span></span>

<span data-ttu-id="2d8f9-128">指定 Markdown 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-128">Specifies the path to a Markdown file.</span></span> <span data-ttu-id="2d8f9-129">與 Path 參數不同，LiteralPath 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-129">Unlike the Path parameter, the value of LiteralPath is used exactly as it is typed.</span></span> <span data-ttu-id="2d8f9-130">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-130">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="2d8f9-131">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-131">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2d8f9-132">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-132">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2d8f9-133">-Path</span><span class="sxs-lookup"><span data-stu-id="2d8f9-133">-Path</span></span>

<span data-ttu-id="2d8f9-134">指定要呈現之 Markdown 檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-134">Specifies the path to a Markdown file to be rendered.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="2d8f9-135">-UseBrowser</span><span class="sxs-lookup"><span data-stu-id="2d8f9-135">-UseBrowser</span></span>

<span data-ttu-id="2d8f9-136">將 Markdown 輸入編譯為 HTML，並在您的預設瀏覽器中開啟。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-136">Compiles the Markdown input as HTML and opens it in your default browser.</span></span>

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

### <span data-ttu-id="2d8f9-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2d8f9-137">CommonParameters</span></span>

<span data-ttu-id="2d8f9-138">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2d8f9-139">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2d8f9-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2d8f9-140">輸入</span><span class="sxs-lookup"><span data-stu-id="2d8f9-140">INPUTS</span></span>

### <span data-ttu-id="2d8f9-141">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="2d8f9-141">System.Management.Automation.PSObject</span></span>

### <span data-ttu-id="2d8f9-142">System.String[]</span><span class="sxs-lookup"><span data-stu-id="2d8f9-142">System.String[]</span></span>

## <span data-ttu-id="2d8f9-143">輸出</span><span class="sxs-lookup"><span data-stu-id="2d8f9-143">OUTPUTS</span></span>

### <span data-ttu-id="2d8f9-144">System.String</span><span class="sxs-lookup"><span data-stu-id="2d8f9-144">System.String</span></span>

## <span data-ttu-id="2d8f9-145">注意</span><span class="sxs-lookup"><span data-stu-id="2d8f9-145">NOTES</span></span>

## <span data-ttu-id="2d8f9-146">相關連結</span><span class="sxs-lookup"><span data-stu-id="2d8f9-146">RELATED LINKS</span></span>

[<span data-ttu-id="2d8f9-147">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="2d8f9-147">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

