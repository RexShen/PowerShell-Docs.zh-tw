---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: ed56dc5655f640dae1d80c66850581ff12dbb7ee
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347596"
---
# <span data-ttu-id="f7a51-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="f7a51-103">Get-Clipboard</span></span>

## <span data-ttu-id="f7a51-104">概要</span><span class="sxs-lookup"><span data-stu-id="f7a51-104">SYNOPSIS</span></span>
<span data-ttu-id="f7a51-105">取得剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="f7a51-105">Gets the contents of the clipboard.</span></span>

## <span data-ttu-id="f7a51-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f7a51-106">SYNTAX</span></span>

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="f7a51-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f7a51-107">DESCRIPTION</span></span>

<span data-ttu-id="f7a51-108">`Get-Clipboard`Cmdlet 會以文字形式取得剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="f7a51-108">The `Get-Clipboard` cmdlet gets the contents of the clipboard as text.</span></span> <span data-ttu-id="f7a51-109">多行文字會以類似于的字串陣列形式傳回 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="f7a51-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

> [!NOTE]
> <span data-ttu-id="f7a51-110">在 Linux 上，此 Cmdlet 要求 `xclip` 公用程式必須在路徑中。</span><span class="sxs-lookup"><span data-stu-id="f7a51-110">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span> <span data-ttu-id="f7a51-111">MacOS 不支援此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f7a51-111">This cmdlet is not supported on macOS.</span></span>

## <span data-ttu-id="f7a51-112">範例</span><span class="sxs-lookup"><span data-stu-id="f7a51-112">EXAMPLES</span></span>

### <span data-ttu-id="f7a51-113">範例1：取得剪貼簿的內容，並將它顯示在命令列中</span><span class="sxs-lookup"><span data-stu-id="f7a51-113">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="f7a51-114">在此範例中，我們已將文字 "hello" 複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="f7a51-114">In this example we have copied the text "hello" into the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
hello
```

## <span data-ttu-id="f7a51-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7a51-115">PARAMETERS</span></span>

### <span data-ttu-id="f7a51-116">-Raw</span><span class="sxs-lookup"><span data-stu-id="f7a51-116">-Raw</span></span>

<span data-ttu-id="f7a51-117">取得剪貼簿的整個內容。</span><span class="sxs-lookup"><span data-stu-id="f7a51-117">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="f7a51-118">多行文字會以單一多行字串的形式傳回，而不是字串陣列。</span><span class="sxs-lookup"><span data-stu-id="f7a51-118">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="f7a51-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7a51-119">CommonParameters</span></span>

<span data-ttu-id="f7a51-120">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f7a51-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7a51-121">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f7a51-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7a51-122">輸入</span><span class="sxs-lookup"><span data-stu-id="f7a51-122">INPUTS</span></span>

## <span data-ttu-id="f7a51-123">輸出</span><span class="sxs-lookup"><span data-stu-id="f7a51-123">OUTPUTS</span></span>

### <span data-ttu-id="f7a51-124">System.String</span><span class="sxs-lookup"><span data-stu-id="f7a51-124">System.String</span></span>

## <span data-ttu-id="f7a51-125">注意</span><span class="sxs-lookup"><span data-stu-id="f7a51-125">NOTES</span></span>

## <span data-ttu-id="f7a51-126">相關連結</span><span class="sxs-lookup"><span data-stu-id="f7a51-126">RELATED LINKS</span></span>

[<span data-ttu-id="f7a51-127">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="f7a51-127">Set-Clipboard</span></span>](Set-Clipboard.md)
