---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 1ee55dfaf4ecd3e46bedd8f356b1f677180c9c62
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564549"
---
# <span data-ttu-id="a1006-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="a1006-103">Set-Clipboard</span></span>

## <span data-ttu-id="a1006-104">概要</span><span class="sxs-lookup"><span data-stu-id="a1006-104">SYNOPSIS</span></span>
<span data-ttu-id="a1006-105">設定剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="a1006-105">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="a1006-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a1006-106">SYNTAX</span></span>

```
Set-Clipboard -Value <String[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a1006-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a1006-107">DESCRIPTION</span></span>

<span data-ttu-id="a1006-108">`Set-Clipboard`Cmdlet 會設定剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="a1006-108">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="a1006-109">在 Linux 上，此 Cmdlet 要求 `xclip` 公用程式必須在路徑中。</span><span class="sxs-lookup"><span data-stu-id="a1006-109">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="a1006-110">範例</span><span class="sxs-lookup"><span data-stu-id="a1006-110">EXAMPLES</span></span>

### <span data-ttu-id="a1006-111">範例 1：將文字複製到剪貼簿</span><span class="sxs-lookup"><span data-stu-id="a1006-111">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

### <span data-ttu-id="a1006-112">範例2：將檔案的內容複寫到剪貼簿</span><span class="sxs-lookup"><span data-stu-id="a1006-112">Example 2: Copy the contents of a file to the clipboard</span></span>

<span data-ttu-id="a1006-113">這個範例會使用管線將檔案的內容傳送至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="a1006-113">This example pipes the contents of a file to the clipboard.</span></span> <span data-ttu-id="a1006-114">在此範例中，我們會取得公開 ssh 金鑰，讓它可以貼到另一個應用程式，例如 GitHub。</span><span class="sxs-lookup"><span data-stu-id="a1006-114">In this example, we are getting a public ssh key so that it can be pasted into another application, like GitHub.</span></span>

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
```

## <span data-ttu-id="a1006-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a1006-115">PARAMETERS</span></span>

### <span data-ttu-id="a1006-116">-Append</span><span class="sxs-lookup"><span data-stu-id="a1006-116">-Append</span></span>

<span data-ttu-id="a1006-117">表示此 Cmdlet 不會清除剪貼簿，會將內容附加上去。</span><span class="sxs-lookup"><span data-stu-id="a1006-117">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="a1006-118">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a1006-118">-Confirm</span></span>

<span data-ttu-id="a1006-119">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="a1006-119">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a1006-120">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a1006-120">-WhatIf</span></span>

<span data-ttu-id="a1006-121">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="a1006-121">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a1006-122">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="a1006-122">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a1006-123">-Value</span><span class="sxs-lookup"><span data-stu-id="a1006-123">-Value</span></span>

<span data-ttu-id="a1006-124">要加入至剪貼簿的字串值。</span><span class="sxs-lookup"><span data-stu-id="a1006-124">The string values to be added to the clipboard.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a1006-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a1006-125">CommonParameters</span></span>

<span data-ttu-id="a1006-126">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a1006-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a1006-127">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a1006-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a1006-128">輸入</span><span class="sxs-lookup"><span data-stu-id="a1006-128">INPUTS</span></span>

### <span data-ttu-id="a1006-129">System.String[]</span><span class="sxs-lookup"><span data-stu-id="a1006-129">System.String[]</span></span>

## <span data-ttu-id="a1006-130">輸出</span><span class="sxs-lookup"><span data-stu-id="a1006-130">OUTPUTS</span></span>

## <span data-ttu-id="a1006-131">注意</span><span class="sxs-lookup"><span data-stu-id="a1006-131">NOTES</span></span>

<span data-ttu-id="a1006-132">在很罕見的情況下 `Set-Clipboard` ，如果快速連續地使用具有大量值（例如在迴圈中），您可能偶爾會從剪貼簿取得空白值。</span><span class="sxs-lookup"><span data-stu-id="a1006-132">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="a1006-133">您可以在迴圈中使用來修正此問題 `Start-Sleep -Milliseconds 1` 。</span><span class="sxs-lookup"><span data-stu-id="a1006-133">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="a1006-134">相關連結</span><span class="sxs-lookup"><span data-stu-id="a1006-134">RELATED LINKS</span></span>

[<span data-ttu-id="a1006-135">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="a1006-135">Get-Clipboard</span></span>](Get-Clipboard.md)
