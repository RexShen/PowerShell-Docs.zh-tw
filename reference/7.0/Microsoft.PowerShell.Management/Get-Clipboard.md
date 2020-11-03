---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 9da33bcf0bc1142859d547debedfb242819041aa
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93239629"
---
# <span data-ttu-id="01d4c-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="01d4c-103">Get-Clipboard</span></span>

## <span data-ttu-id="01d4c-104">概要</span><span class="sxs-lookup"><span data-stu-id="01d4c-104">SYNOPSIS</span></span>
<span data-ttu-id="01d4c-105">取得剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="01d4c-105">Gets the contents of the clipboard.</span></span>

## <span data-ttu-id="01d4c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="01d4c-106">SYNTAX</span></span>

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="01d4c-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01d4c-107">DESCRIPTION</span></span>

<span data-ttu-id="01d4c-108">`Get-Clipboard`Cmdlet 會以文字形式取得剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="01d4c-108">The `Get-Clipboard` cmdlet gets the contents of the clipboard as text.</span></span> <span data-ttu-id="01d4c-109">多行文字會以類似于的字串陣列形式傳回 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="01d4c-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

> [!NOTE]
> <span data-ttu-id="01d4c-110">在 Linux 上，此 Cmdlet 要求 `xclip` 公用程式必須在路徑中。</span><span class="sxs-lookup"><span data-stu-id="01d4c-110">On Linux, this cmdlet requires the `xclip` utility to be in the path.</span></span>

## <span data-ttu-id="01d4c-111">範例</span><span class="sxs-lookup"><span data-stu-id="01d4c-111">EXAMPLES</span></span>

### <span data-ttu-id="01d4c-112">範例1：取得剪貼簿的內容，並將它顯示在命令列中</span><span class="sxs-lookup"><span data-stu-id="01d4c-112">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="01d4c-113">在此範例中，我們已將文字 "hello" 複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="01d4c-113">In this example we have copied the text "hello" into the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
hello
```

## <span data-ttu-id="01d4c-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="01d4c-114">PARAMETERS</span></span>

### <span data-ttu-id="01d4c-115">-Raw</span><span class="sxs-lookup"><span data-stu-id="01d4c-115">-Raw</span></span>

<span data-ttu-id="01d4c-116">取得剪貼簿的整個內容。</span><span class="sxs-lookup"><span data-stu-id="01d4c-116">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="01d4c-117">多行文字會以單一多行字串的形式傳回，而不是字串陣列。</span><span class="sxs-lookup"><span data-stu-id="01d4c-117">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="01d4c-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01d4c-118">CommonParameters</span></span>

<span data-ttu-id="01d4c-119">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="01d4c-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="01d4c-120">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="01d4c-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="01d4c-121">輸入</span><span class="sxs-lookup"><span data-stu-id="01d4c-121">INPUTS</span></span>

## <span data-ttu-id="01d4c-122">輸出</span><span class="sxs-lookup"><span data-stu-id="01d4c-122">OUTPUTS</span></span>

### <span data-ttu-id="01d4c-123">System.String</span><span class="sxs-lookup"><span data-stu-id="01d4c-123">System.String</span></span>

## <span data-ttu-id="01d4c-124">注意</span><span class="sxs-lookup"><span data-stu-id="01d4c-124">NOTES</span></span>

## <span data-ttu-id="01d4c-125">相關連結</span><span class="sxs-lookup"><span data-stu-id="01d4c-125">RELATED LINKS</span></span>

[<span data-ttu-id="01d4c-126">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="01d4c-126">Set-Clipboard</span></span>](Set-Clipboard.md)

