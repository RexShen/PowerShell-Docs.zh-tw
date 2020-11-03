---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Set-MarkdownOption?view=powershell-7&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: e18cc8e0f5e547c4418f59b6f55109052b69c220
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "93205264"
---
# <span data-ttu-id="ad131-101">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="ad131-101">Set-MarkdownOption</span></span>

## <span data-ttu-id="ad131-102">概要</span><span class="sxs-lookup"><span data-stu-id="ad131-102">SYNOPSIS</span></span>
<span data-ttu-id="ad131-103">設定在主控台中用來呈現 Markdown 內容的色彩和樣式。</span><span class="sxs-lookup"><span data-stu-id="ad131-103">Sets the colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="ad131-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ad131-104">SYNTAX</span></span>

### <span data-ttu-id="ad131-105">IndividualSetting (預設) </span><span class="sxs-lookup"><span data-stu-id="ad131-105">IndividualSetting (Default)</span></span>

```
Set-MarkdownOption [-Header1Color <String>] [-Header2Color <String>] [-Header3Color <String>]
 [-Header4Color <String>] [-Header5Color <String>] [-Header6Color <String>] [-Code <String>]
 [-ImageAltTextForegroundColor <String>] [-LinkForegroundColor <String>]
 [-ItalicsForegroundColor <String>] [-BoldForegroundColor <String>] [-PassThru]
 [<CommonParameters>]
```

### <span data-ttu-id="ad131-106">佈景主題</span><span class="sxs-lookup"><span data-stu-id="ad131-106">Theme</span></span>

```
Set-MarkdownOption [-PassThru] -Theme <String> [<CommonParameters>]
```

### <span data-ttu-id="ad131-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="ad131-107">InputObject</span></span>

```
Set-MarkdownOption [-PassThru] [-InputObject] <PSObject> [<CommonParameters>]
```

## <span data-ttu-id="ad131-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ad131-108">DESCRIPTION</span></span>

<span data-ttu-id="ad131-109">設定在主控台中用來呈現 Markdown 內容的色彩和樣式。</span><span class="sxs-lookup"><span data-stu-id="ad131-109">Sets the colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="ad131-110">這些樣式是使用 ANSI 轉義碼來定義，此程式碼會變更轉譯的 Markdown 文字的色彩和樣式。</span><span class="sxs-lookup"><span data-stu-id="ad131-110">These styles are defined using ANSI escape codes that change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="ad131-111">如需 Markdown 的詳細資訊，請參閱 [CommonMark](https://commonmark.org/) 網站。</span><span class="sxs-lookup"><span data-stu-id="ad131-111">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

> [!NOTE]
> <span data-ttu-id="ad131-112">設定中使用的字串值， **是在** `[char]0x1B` ANSI escape 序列 () 之後的字元。</span><span class="sxs-lookup"><span data-stu-id="ad131-112">The string values used in the settings are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="ad131-113">請勿在字串中包含 **Escape** 字元。</span><span class="sxs-lookup"><span data-stu-id="ad131-113">Do not include the **Escape** character in the string.</span></span> <span data-ttu-id="ad131-114">如需 ANSI escape 程式碼工作的詳細資訊，請參閱 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)。</span><span class="sxs-lookup"><span data-stu-id="ad131-114">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="ad131-115">範例</span><span class="sxs-lookup"><span data-stu-id="ad131-115">EXAMPLES</span></span>

### <span data-ttu-id="ad131-116">範例 1-切換至淺色主題</span><span class="sxs-lookup"><span data-stu-id="ad131-116">Example 1 - Switch to the Light Theme</span></span>

<span data-ttu-id="ad131-117">此範例會選取 **淺色** 主題，並使用 **PassThru** 參數顯示新的設定。</span><span class="sxs-lookup"><span data-stu-id="ad131-117">This example selects the **Light** theme and displays the new configuration using the **PassThru** parameter.</span></span>

```powershell
Set-MarkdownOption -Theme Light -PassThru
```

```Output
Header1         : [7m
Header2         : [4;33m
Header3         : [4;34m
Header4         : [4;35m
Header5         : [4;36m
Header6         : [4;30m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

### <span data-ttu-id="ad131-118">範例 2-自訂色彩和樣式設定</span><span class="sxs-lookup"><span data-stu-id="ad131-118">Example 2 - Customize the color and style settings</span></span>

<span data-ttu-id="ad131-119">此範例會變更 Markdown 標頭的 escape 程式碼。</span><span class="sxs-lookup"><span data-stu-id="ad131-119">This example changes the escape code for the Markdown headers.</span></span> <span data-ttu-id="ad131-120">標頭的預設設定會將它們呈現為各種色彩的底線文字。</span><span class="sxs-lookup"><span data-stu-id="ad131-120">The default configuration for headers renders them as underlined text of various colors.</span></span> <span data-ttu-id="ad131-121">這種變更會移除底線樣式。</span><span class="sxs-lookup"><span data-stu-id="ad131-121">This change removes the underline style.</span></span>

```powershell
$mdOptions = Get-MarkdownOption
$mdOptions.Header2 = '[93m'
$mdOptions.Header3 = '[94m'
$mdOptions.Header4 = '[95m'
$mdOptions.Header5 = '[96m'
$mdOptions.Header6 = '[97m'
Set-MarkdownOption -InputObject $mdOptions -PassThru
```

```Output
Header1         : [7m
Header2         : [93m
Header3         : [94m
Header4         : [95m
Header5         : [96m
Header6         : [97m
Code            : [48;2;155;155;155;38;2;30;30;31m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

## <span data-ttu-id="ad131-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ad131-122">PARAMETERS</span></span>

### <span data-ttu-id="ad131-123">-BoldForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ad131-123">-BoldForegroundColor</span></span>

<span data-ttu-id="ad131-124">設定呈現粗體 Markdown 文字的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="ad131-124">Sets the foreground color for rendering bold Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-125">-Code</span><span class="sxs-lookup"><span data-stu-id="ad131-125">-Code</span></span>

<span data-ttu-id="ad131-126">設定在 Markdown 文字中轉譯程式碼區塊和範圍的色彩。</span><span class="sxs-lookup"><span data-stu-id="ad131-126">Sets the color for rendering code blocks and spans in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-127">-Header1Color</span><span class="sxs-lookup"><span data-stu-id="ad131-127">-Header1Color</span></span>

<span data-ttu-id="ad131-128">設定以 Markdown 文字呈現 Header1.xml 組塊的色彩。</span><span class="sxs-lookup"><span data-stu-id="ad131-128">Sets the color for rendering Header1 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-129">-Header2Color</span><span class="sxs-lookup"><span data-stu-id="ad131-129">-Header2Color</span></span>

<span data-ttu-id="ad131-130">設定以 Markdown 文字呈現 H 2 組塊的色彩。</span><span class="sxs-lookup"><span data-stu-id="ad131-130">Sets the color for rendering Header2 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-131">-Header3Color</span><span class="sxs-lookup"><span data-stu-id="ad131-131">-Header3Color</span></span>

<span data-ttu-id="ad131-132">設定以 Markdown 文字呈現 H 3 組塊的色彩。</span><span class="sxs-lookup"><span data-stu-id="ad131-132">Sets the color for rendering Header3 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-133">-Header4Color</span><span class="sxs-lookup"><span data-stu-id="ad131-133">-Header4Color</span></span>

<span data-ttu-id="ad131-134">設定以 Markdown 文字呈現 Header4 組塊的色彩。</span><span class="sxs-lookup"><span data-stu-id="ad131-134">Sets the color for rendering Header4 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-135">-Header5Color</span><span class="sxs-lookup"><span data-stu-id="ad131-135">-Header5Color</span></span>

<span data-ttu-id="ad131-136">設定以 Markdown 文字呈現 Header5 組塊的色彩。</span><span class="sxs-lookup"><span data-stu-id="ad131-136">Sets the color for rendering Header5 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-137">-Header6Color</span><span class="sxs-lookup"><span data-stu-id="ad131-137">-Header6Color</span></span>

<span data-ttu-id="ad131-138">設定以 Markdown 文字呈現 Header6 組塊的色彩。</span><span class="sxs-lookup"><span data-stu-id="ad131-138">Sets the color for rendering Header6 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-139">-ImageAltTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ad131-139">-ImageAltTextForegroundColor</span></span>

<span data-ttu-id="ad131-140">設定前景色彩，以 Markdown 文字呈現影像元素的替代文字。</span><span class="sxs-lookup"><span data-stu-id="ad131-140">Sets the foreground color for rendering the alternate text of an image element in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ad131-141">-InputObject</span></span>

<span data-ttu-id="ad131-142">包含要設定之設定的 **PSMarkdownOptionInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="ad131-142">A **PSMarkdownOptionInfo** object containing the configuration to be set.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-143">-ItalicsForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ad131-143">-ItalicsForegroundColor</span></span>

<span data-ttu-id="ad131-144">設定用來轉譯斜體 in Markdown 文字的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="ad131-144">Sets the foreground color for rendering the italics in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-145">-LinkForegroundColor</span><span class="sxs-lookup"><span data-stu-id="ad131-145">-LinkForegroundColor</span></span>

<span data-ttu-id="ad131-146">設定在 Markdown 文字中呈現超連結的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="ad131-146">Sets the foreground color for rendering hyperlinks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-147">-PassThru</span><span class="sxs-lookup"><span data-stu-id="ad131-147">-PassThru</span></span>

<span data-ttu-id="ad131-148">讓 Cmdlet 輸出包含新設定的 **PSMarkdownOptionInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="ad131-148">Causes the cmdlet to output a **PSMarkdownOptionInfo** object containing the new configuration.</span></span>

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

### <span data-ttu-id="ad131-149">-主題</span><span class="sxs-lookup"><span data-stu-id="ad131-149">-Theme</span></span>

<span data-ttu-id="ad131-150">選取包含預先定義之色彩設定的主題。</span><span class="sxs-lookup"><span data-stu-id="ad131-150">Selects a theme containing predefined color settings.</span></span> <span data-ttu-id="ad131-151">可能的值為 **深色** 和 **淺色** 。</span><span class="sxs-lookup"><span data-stu-id="ad131-151">The possible values are **Dark** and **Light** .</span></span>

```yaml
Type: System.String
Parameter Sets: Theme
Aliases:
Accepted values: Dark, Light

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ad131-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ad131-152">CommonParameters</span></span>

<span data-ttu-id="ad131-153">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ad131-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ad131-154">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ad131-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ad131-155">輸入</span><span class="sxs-lookup"><span data-stu-id="ad131-155">INPUTS</span></span>

### <span data-ttu-id="ad131-156">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="ad131-156">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="ad131-157">輸出</span><span class="sxs-lookup"><span data-stu-id="ad131-157">OUTPUTS</span></span>

### <span data-ttu-id="ad131-158">MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="ad131-158">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="ad131-159">注意</span><span class="sxs-lookup"><span data-stu-id="ad131-159">NOTES</span></span>

<span data-ttu-id="ad131-160">用來定義色彩和樣式的字串值必須符合正則運算式 `^\[*[0-9;]*?m{1}` 。</span><span class="sxs-lookup"><span data-stu-id="ad131-160">The string values used to define the color and style must match the regular expression `^\[*[0-9;]*?m{1}`.</span></span>

## <span data-ttu-id="ad131-161">相關連結</span><span class="sxs-lookup"><span data-stu-id="ad131-161">RELATED LINKS</span></span>

[<span data-ttu-id="ad131-162">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="ad131-162">Get-MarkdownOption</span></span>](Get-MarkdownOption.md)

[<span data-ttu-id="ad131-163">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="ad131-163">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="ad131-164">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="ad131-164">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="ad131-165">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="ad131-165">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="ad131-166">CommonMark</span><span class="sxs-lookup"><span data-stu-id="ad131-166">CommonMark</span></span>](https://commonmark.org/)
