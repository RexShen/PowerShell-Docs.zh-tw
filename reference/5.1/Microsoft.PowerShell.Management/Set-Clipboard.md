---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: f3230c247296d5fd907d580e719cbbbc560183a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203520"
---
# <span data-ttu-id="8a0d6-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="8a0d6-103">Set-Clipboard</span></span>

## <span data-ttu-id="8a0d6-104">概要</span><span class="sxs-lookup"><span data-stu-id="8a0d6-104">SYNOPSIS</span></span>
<span data-ttu-id="8a0d6-105">設定目前的 Windows 剪貼簿項目。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-105">Sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="8a0d6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8a0d6-106">SYNTAX</span></span>

### <span data-ttu-id="8a0d6-107">String (預設值)</span><span class="sxs-lookup"><span data-stu-id="8a0d6-107">String (Default)</span></span>

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8a0d6-108">值</span><span class="sxs-lookup"><span data-stu-id="8a0d6-108">Value</span></span>

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8a0d6-109">路徑</span><span class="sxs-lookup"><span data-stu-id="8a0d6-109">Path</span></span>

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8a0d6-110">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8a0d6-110">LiteralPath</span></span>

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8a0d6-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8a0d6-111">DESCRIPTION</span></span>

<span data-ttu-id="8a0d6-112">`Set-Clipboard`Cmdlet 會設定目前的 Windows 剪貼簿專案。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-112">The `Set-Clipboard` cmdlet sets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="8a0d6-113">範例</span><span class="sxs-lookup"><span data-stu-id="8a0d6-113">EXAMPLES</span></span>

### <span data-ttu-id="8a0d6-114">範例 1：將文字複製到剪貼簿</span><span class="sxs-lookup"><span data-stu-id="8a0d6-114">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="8a0d6-115">範例 2︰將目錄的內容複製到剪貼簿</span><span class="sxs-lookup"><span data-stu-id="8a0d6-115">Example 2: Copy the contents of a directory to the clipboard</span></span>

<span data-ttu-id="8a0d6-116">此命令會將指定資料夾的內容複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-116">This command copies the content of the specified folder to the clipboard.</span></span>

```powershell
Set-Clipboard -Path "C:\Staging\"
```

## <span data-ttu-id="8a0d6-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8a0d6-117">PARAMETERS</span></span>

### <span data-ttu-id="8a0d6-118">-Append</span><span class="sxs-lookup"><span data-stu-id="8a0d6-118">-Append</span></span>

<span data-ttu-id="8a0d6-119">表示此 Cmdlet 不會清除剪貼簿，會將內容附加上去。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-119">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="8a0d6-120">-AsHtml</span><span class="sxs-lookup"><span data-stu-id="8a0d6-120">-AsHtml</span></span>

<span data-ttu-id="8a0d6-121">指出此 Cmdlet 會將內容以 HTML 呈現至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-121">Indicates that the cmdlet renders the content as HTML to the clipboard.</span></span>

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

### <span data-ttu-id="8a0d6-122">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8a0d6-122">-LiteralPath</span></span>

<span data-ttu-id="8a0d6-123">指定要複製到剪貼簿的項目路徑。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-123">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="8a0d6-124">與 **Path** 不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-124">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="8a0d6-125">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-125">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="8a0d6-126">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-126">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="8a0d6-127">單引號告知 Windows PowerShell 不要將任何字元視為逸出序列。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-127">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="8a0d6-128">-Path</span><span class="sxs-lookup"><span data-stu-id="8a0d6-128">-Path</span></span>

<span data-ttu-id="8a0d6-129">指定要複製到剪貼簿的項目路徑。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-129">Specifies the path to the item that is copied to the clipboard.</span></span> <span data-ttu-id="8a0d6-130">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-130">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="8a0d6-131">-Value</span><span class="sxs-lookup"><span data-stu-id="8a0d6-131">-Value</span></span>

<span data-ttu-id="8a0d6-132">以字串陣列的方式指定要複製到剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-132">Specifies, as a string array, the content to copy to the clipboard.</span></span>

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

### <span data-ttu-id="8a0d6-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8a0d6-133">-Confirm</span></span>

<span data-ttu-id="8a0d6-134">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-134">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8a0d6-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8a0d6-135">-WhatIf</span></span>

<span data-ttu-id="8a0d6-136">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-136">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8a0d6-137">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-137">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8a0d6-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8a0d6-138">CommonParameters</span></span>

<span data-ttu-id="8a0d6-139">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8a0d6-140">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8a0d6-141">輸入</span><span class="sxs-lookup"><span data-stu-id="8a0d6-141">INPUTS</span></span>

### <span data-ttu-id="8a0d6-142">System.String[]</span><span class="sxs-lookup"><span data-stu-id="8a0d6-142">System.String[]</span></span>

## <span data-ttu-id="8a0d6-143">輸出</span><span class="sxs-lookup"><span data-stu-id="8a0d6-143">OUTPUTS</span></span>

## <span data-ttu-id="8a0d6-144">注意</span><span class="sxs-lookup"><span data-stu-id="8a0d6-144">NOTES</span></span>

<span data-ttu-id="8a0d6-145">在很罕見的情況下 `Set-Clipboard` ，如果快速連續地使用具有大量值（例如在迴圈中），您可能偶爾會從剪貼簿取得空白值。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-145">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="8a0d6-146">您可以在迴圈中使用來修正此問題 `Start-Sleep -Milliseconds 1` 。</span><span class="sxs-lookup"><span data-stu-id="8a0d6-146">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="8a0d6-147">相關連結</span><span class="sxs-lookup"><span data-stu-id="8a0d6-147">RELATED LINKS</span></span>

[<span data-ttu-id="8a0d6-148">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="8a0d6-148">Get-Clipboard</span></span>](Get-Clipboard.md)
