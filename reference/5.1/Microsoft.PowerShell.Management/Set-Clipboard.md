---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: c1cf126e41a5e918afffbc41d30f957e650efdf5
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564497"
---
# <span data-ttu-id="e4987-102">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="e4987-102">Set-Clipboard</span></span>

## <span data-ttu-id="e4987-103">概要</span><span class="sxs-lookup"><span data-stu-id="e4987-103">SYNOPSIS</span></span>
<span data-ttu-id="e4987-104">設定目前的 Windows 剪貼簿項目。</span><span class="sxs-lookup"><span data-stu-id="e4987-104">Sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="e4987-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e4987-105">SYNTAX</span></span>

### <span data-ttu-id="e4987-106">String (預設值)</span><span class="sxs-lookup"><span data-stu-id="e4987-106">String (Default)</span></span>

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e4987-107">值</span><span class="sxs-lookup"><span data-stu-id="e4987-107">Value</span></span>

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e4987-108">路徑</span><span class="sxs-lookup"><span data-stu-id="e4987-108">Path</span></span>

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e4987-109">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e4987-109">LiteralPath</span></span>

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e4987-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e4987-110">DESCRIPTION</span></span>

<span data-ttu-id="e4987-111">`Set-Clipboard`Cmdlet 會設定目前的 Windows 剪貼簿專案。</span><span class="sxs-lookup"><span data-stu-id="e4987-111">The `Set-Clipboard` cmdlet sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="e4987-112">範例</span><span class="sxs-lookup"><span data-stu-id="e4987-112">EXAMPLES</span></span>

### <span data-ttu-id="e4987-113">範例 1：將文字複製到剪貼簿</span><span class="sxs-lookup"><span data-stu-id="e4987-113">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="e4987-114">範例 2︰將目錄的內容複製到剪貼簿</span><span class="sxs-lookup"><span data-stu-id="e4987-114">Example 2: Copy the contents of a directory to the clipboard</span></span>

<span data-ttu-id="e4987-115">此範例會將指定資料夾的內容複寫到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="e4987-115">This example copies the content of the specified folder to the clipboard.</span></span>

```powershell
Set-Clipboard -Path "C:\Staging\"
```

### <span data-ttu-id="e4987-116">範例3：將檔案的內容複寫到剪貼簿</span><span class="sxs-lookup"><span data-stu-id="e4987-116">Example 3: Copy the contents of a file to the clipboard</span></span>

<span data-ttu-id="e4987-117">這個範例會使用管線將檔案的內容傳送至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="e4987-117">This example pipes the contents of a file to the clipboard.</span></span> <span data-ttu-id="e4987-118">在此範例中，我們會取得公開 ssh 金鑰，讓它可以貼到另一個應用程式，例如 GitHub。</span><span class="sxs-lookup"><span data-stu-id="e4987-118">In this example, we are getting a public ssh key so that it can be pasted into another application, like GitHub.</span></span>

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## <span data-ttu-id="e4987-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e4987-119">PARAMETERS</span></span>

### <span data-ttu-id="e4987-120">-Append</span><span class="sxs-lookup"><span data-stu-id="e4987-120">-Append</span></span>

<span data-ttu-id="e4987-121">表示此 Cmdlet 不會清除剪貼簿，會將內容附加上去。</span><span class="sxs-lookup"><span data-stu-id="e4987-121">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="e4987-122">-AsHtml</span><span class="sxs-lookup"><span data-stu-id="e4987-122">-AsHtml</span></span>

<span data-ttu-id="e4987-123">指出此 Cmdlet 會將內容以 HTML 呈現至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="e4987-123">Indicates that the cmdlet renders the content as HTML to the clipboard.</span></span>

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

### <span data-ttu-id="e4987-124">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e4987-124">-LiteralPath</span></span>

<span data-ttu-id="e4987-125">指定要複製到剪貼簿的項目路徑。</span><span class="sxs-lookup"><span data-stu-id="e4987-125">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="e4987-126">與 **Path** 不同，**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="e4987-126">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="e4987-127">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="e4987-127">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e4987-128">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="e4987-128">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="e4987-129">單引號告知 Windows PowerShell 不要將任何字元視為逸出序列。</span><span class="sxs-lookup"><span data-stu-id="e4987-129">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e4987-130">-Path</span><span class="sxs-lookup"><span data-stu-id="e4987-130">-Path</span></span>

<span data-ttu-id="e4987-131">指定要複製到剪貼簿的項目路徑。</span><span class="sxs-lookup"><span data-stu-id="e4987-131">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="e4987-132">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="e4987-132">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e4987-133">-Value</span><span class="sxs-lookup"><span data-stu-id="e4987-133">-Value</span></span>

<span data-ttu-id="e4987-134">以字串陣列的方式指定要複製到剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="e4987-134">Specifies, as a string array, the content to copy to the clipboard.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Value
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e4987-135">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e4987-135">-Confirm</span></span>

<span data-ttu-id="e4987-136">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="e4987-136">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e4987-137">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e4987-137">-WhatIf</span></span>

<span data-ttu-id="e4987-138">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="e4987-138">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e4987-139">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="e4987-139">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e4987-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e4987-140">CommonParameters</span></span>

<span data-ttu-id="e4987-141">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e4987-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e4987-142">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e4987-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e4987-143">輸入</span><span class="sxs-lookup"><span data-stu-id="e4987-143">INPUTS</span></span>

### <span data-ttu-id="e4987-144">System.String[]</span><span class="sxs-lookup"><span data-stu-id="e4987-144">System.String[]</span></span>

## <span data-ttu-id="e4987-145">輸出</span><span class="sxs-lookup"><span data-stu-id="e4987-145">OUTPUTS</span></span>

## <span data-ttu-id="e4987-146">注意</span><span class="sxs-lookup"><span data-stu-id="e4987-146">NOTES</span></span>

<span data-ttu-id="e4987-147">在很罕見的情況下 `Set-Clipboard` ，如果快速連續地使用具有大量值（例如在迴圈中），您可能偶爾會從剪貼簿取得空白值。</span><span class="sxs-lookup"><span data-stu-id="e4987-147">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="e4987-148">您可以在迴圈中使用來修正此問題 `Start-Sleep -Milliseconds 1` 。</span><span class="sxs-lookup"><span data-stu-id="e4987-148">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="e4987-149">相關連結</span><span class="sxs-lookup"><span data-stu-id="e4987-149">RELATED LINKS</span></span>

[<span data-ttu-id="e4987-150">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="e4987-150">Get-Clipboard</span></span>](Get-Clipboard.md)
