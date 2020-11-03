---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/09/2019
online version: https://go.microsoft.com/fwlink/?linkid=526220
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: 6fbe7b1e5534b1227bcfd73fd58f3602186ef8c5
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239669"
---
# <span data-ttu-id="2a94d-103">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="2a94d-103">Set-Clipboard</span></span>

## <span data-ttu-id="2a94d-104">概要</span><span class="sxs-lookup"><span data-stu-id="2a94d-104">SYNOPSIS</span></span>
<span data-ttu-id="2a94d-105">設定剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="2a94d-105">Sets the contents of the clipboard.</span></span>

## <span data-ttu-id="2a94d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2a94d-106">SYNTAX</span></span>

```
Set-Clipboard -Value <String[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2a94d-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2a94d-107">DESCRIPTION</span></span>

<span data-ttu-id="2a94d-108">`Set-Clipboard`Cmdlet 會設定剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="2a94d-108">The `Set-Clipboard` cmdlet sets the contents of the clipboard.</span></span>

> [!NOTE]
> <span data-ttu-id="2a94d-109">在 Linux 上，此 Cmdlet 要求 `xclip` 公用程式必須在路徑中。</span><span class="sxs-lookup"><span data-stu-id="2a94d-109">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="2a94d-110">範例</span><span class="sxs-lookup"><span data-stu-id="2a94d-110">EXAMPLES</span></span>

### <span data-ttu-id="2a94d-111">範例 1：將文字複製到剪貼簿</span><span class="sxs-lookup"><span data-stu-id="2a94d-111">Example 1: Copy text to the clipboard</span></span>

```powershell
Set-Clipboard -Value "This is a test string"
```

## <span data-ttu-id="2a94d-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2a94d-112">PARAMETERS</span></span>

### <span data-ttu-id="2a94d-113">-Append</span><span class="sxs-lookup"><span data-stu-id="2a94d-113">-Append</span></span>

<span data-ttu-id="2a94d-114">表示此 Cmdlet 不會清除剪貼簿，會將內容附加上去。</span><span class="sxs-lookup"><span data-stu-id="2a94d-114">Indicates that the cmdlet does not clear the clipboard and appends content to it.</span></span>

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

### <span data-ttu-id="2a94d-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2a94d-115">-Confirm</span></span>

<span data-ttu-id="2a94d-116">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="2a94d-116">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2a94d-117">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2a94d-117">-WhatIf</span></span>

<span data-ttu-id="2a94d-118">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="2a94d-118">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2a94d-119">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="2a94d-119">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2a94d-120">-Value</span><span class="sxs-lookup"><span data-stu-id="2a94d-120">-Value</span></span>

<span data-ttu-id="2a94d-121">要加入至剪貼簿的字串值。</span><span class="sxs-lookup"><span data-stu-id="2a94d-121">The string values to be added to the clipboard.</span></span>

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

### <span data-ttu-id="2a94d-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2a94d-122">CommonParameters</span></span>

<span data-ttu-id="2a94d-123">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2a94d-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2a94d-124">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2a94d-124">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2a94d-125">輸入</span><span class="sxs-lookup"><span data-stu-id="2a94d-125">INPUTS</span></span>

### <span data-ttu-id="2a94d-126">System.String[]</span><span class="sxs-lookup"><span data-stu-id="2a94d-126">System.String[]</span></span>

## <span data-ttu-id="2a94d-127">輸出</span><span class="sxs-lookup"><span data-stu-id="2a94d-127">OUTPUTS</span></span>

## <span data-ttu-id="2a94d-128">注意</span><span class="sxs-lookup"><span data-stu-id="2a94d-128">NOTES</span></span>

<span data-ttu-id="2a94d-129">在很罕見的情況下 `Set-Clipboard` ，如果快速連續地使用具有大量值（例如在迴圈中），您可能偶爾會從剪貼簿取得空白值。</span><span class="sxs-lookup"><span data-stu-id="2a94d-129">In rare cases when using `Set-Clipboard` with a high number of values in rapid succession, like in a loop, you might sporadically get a blank value from the clipboard.</span></span> <span data-ttu-id="2a94d-130">您可以在迴圈中使用來修正此問題 `Start-Sleep -Milliseconds 1` 。</span><span class="sxs-lookup"><span data-stu-id="2a94d-130">This can be fixed by using `Start-Sleep -Milliseconds 1` in the loop.</span></span>

## <span data-ttu-id="2a94d-131">相關連結</span><span class="sxs-lookup"><span data-stu-id="2a94d-131">RELATED LINKS</span></span>

[<span data-ttu-id="2a94d-132">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="2a94d-132">Get-Clipboard</span></span>](Get-Clipboard.md)
