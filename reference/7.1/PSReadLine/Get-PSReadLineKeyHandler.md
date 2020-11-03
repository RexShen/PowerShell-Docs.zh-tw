---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlinekeyhandler?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineKeyHandler
ms.openlocfilehash: 09a34993df29ab06a9d25e6d66770e5774bd28b0
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208776"
---
# <span data-ttu-id="43c09-103">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="43c09-103">Get-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="43c09-104">概要</span><span class="sxs-lookup"><span data-stu-id="43c09-104">SYNOPSIS</span></span>
<span data-ttu-id="43c09-105">取得 PSReadLine 模組的系結索引鍵函數。</span><span class="sxs-lookup"><span data-stu-id="43c09-105">Gets the bound key functions for the PSReadLine module.</span></span>

## <span data-ttu-id="43c09-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="43c09-106">SYNTAX</span></span>

### <span data-ttu-id="43c09-107">FullListing (預設) </span><span class="sxs-lookup"><span data-stu-id="43c09-107">FullListing (default)</span></span>

```
Get-PSReadLineKeyHandler [-Bound] [-Unbound] [<CommonParameters>]
```

### <span data-ttu-id="43c09-108">SpecificBindings</span><span class="sxs-lookup"><span data-stu-id="43c09-108">SpecificBindings</span></span>

```
Get-PSReadLineKeyHandler [-Chord] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="43c09-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="43c09-109">DESCRIPTION</span></span>

<span data-ttu-id="43c09-110">如果未指定任何參數，則會傳回 PSReadLine 模組目前系結的索引鍵函數。</span><span class="sxs-lookup"><span data-stu-id="43c09-110">If no parameter is specified, returns the currently bound key functions for the PSReadLine module.</span></span>

<span data-ttu-id="43c09-111">如果指定了 **弦** 參數，Cmdlet 會傳回特定的系結索引鍵。</span><span class="sxs-lookup"><span data-stu-id="43c09-111">If **Chord** parameter is specified, the cmdlet returns the specific bound keys.</span></span>

## <span data-ttu-id="43c09-112">範例</span><span class="sxs-lookup"><span data-stu-id="43c09-112">EXAMPLES</span></span>

### <span data-ttu-id="43c09-113">範例 1︰ 取得所有索引鍵對應</span><span class="sxs-lookup"><span data-stu-id="43c09-113">Example 1: Get all key mappings</span></span>

<span data-ttu-id="43c09-114">此命令會傳回所有索引鍵對應 (包括繫結和未繫結)。</span><span class="sxs-lookup"><span data-stu-id="43c09-114">This command returns all key mappings, bound and unbound.</span></span>

```powershell
Get-PSReadLineKeyHandler -Bound -Unbound
```

```Output
Key                   Function                Description
---                   --------                -----------
Enter                 AcceptLine              Accept the input or move to the next line if input is missing a closing token.
Shift+Enter           AddLine                 Move the cursor to the next line without attempting to execute the input
Escape                RevertLine              Equivalent to undo all edits (clears the line except lines imported from history)
LeftArrow             BackwardChar            Move the cursor back one character
RightArrow            ForwardChar             Move the cursor forward one character
Ctrl+LeftArrow        BackwardWord            Move the cursor to the beginning of the current or previous word
Ctrl+RightArrow       NextWord                Move the cursor forward to the start of the next word
Shift+LeftArrow       SelectBackwardChar      Adjust the current selection to include the previous character
Shift+RightArrow      SelectForwardChar       Adjust the current selection to include the next character
Ctrl+Shift+LeftArrow  SelectBackwardWord      Adjust the current selection to include the previous word
Ctrl+Shift+RightArrow SelectNextWord          Adjust the current selection to include the next word
UpArrow               PreviousHistory         Replace the input with the previous item in the history
DownArrow             NextHistory             Replace the input with the next item in the history
Home                  BeginningOfLine         Move the cursor to the beginning of the line
End                   EndOfLine               Move the cursor to the end of the line
Shift+Home            SelectBackwardsLine     Adjust the current selection to include from the cursor to the end of the line
Shift+End             SelectLine              Adjust the current selection to include from the cursor to the start of the line
Delete                DeleteChar              Delete the character under the cursor
Backspace             BackwardDeleteChar      Delete the character before the cursor
Ctrl+Spacebar         MenuComplete            Complete the input if there is a single completion, otherwise complete the input by selecting from a menu o...
Tab                   TabCompleteNext         Complete the input using the next completion
Shift+Tab             TabCompletePrevious     Complete the input using the previous completion
Ctrl+a                SelectAll               Select the entire line. Moves the cursor to the end of the line
Ctrl+c                CopyOrCancelLine        Either copy selected text to the clipboard, or if no text is selected, cancel editing the line with Cancel...
Ctrl+C                Copy                    Copy selected region to the system clipboard.  If no region is selected, copy the whole line
Ctrl+l                ClearScreen             Clear the screen and redraw the current line at the top of the screen
Ctrl+r                ReverseSearchHistory    Search history backwards interactively
...
```

### <span data-ttu-id="43c09-115">範例 2︰取得繫結索引鍵</span><span class="sxs-lookup"><span data-stu-id="43c09-115">Example 2: Get bound keys</span></span>

<span data-ttu-id="43c09-116">此命令僅會傳回繫結的索引鍵和索引鍵組合。</span><span class="sxs-lookup"><span data-stu-id="43c09-116">This command returns only bound keys and key combinations.</span></span>

```powershell
Get-PSReadLineKeyHandler
```

```Output
Key                   Function                Description
---                   --------                -----------
Enter                 AcceptLine              Accept the input or move to the next line if input is missing a closing token.
Shift+Enter           AddLine                 Move the cursor to the next line without attempting to execute the input
Escape                RevertLine              Equivalent to undo all edits (clears the line except lines imported from history)
LeftArrow             BackwardChar            Move the cursor back one character
RightArrow            ForwardChar             Move the cursor forward one character
Ctrl+LeftArrow        BackwardWord            Move the cursor to the beginning of the current or previous word
Ctrl+RightArrow       NextWord                Move the cursor forward to the start of the next word
Shift+LeftArrow       SelectBackwardChar      Adjust the current selection to include the previous character
Shift+RightArrow      SelectForwardChar       Adjust the current selection to include the next character
Ctrl+Shift+LeftArrow  SelectBackwardWord      Adjust the current selection to include the previous word
Ctrl+Shift+RightArrow SelectNextWord          Adjust the current selection to include the next word
UpArrow               PreviousHistory         Replace the input with the previous item in the history
DownArrow             NextHistory             Replace the input with the next item in the history
Home                  BeginningOfLine         Move the cursor to the beginning of the line
End                   EndOfLine               Move the cursor to the end of the line
Shift+Home            SelectBackwardsLine     Adjust the current selection to include from the cursor to the end of the line
Shift+End             SelectLine              Adjust the current selection to include from the cursor to the start of the line
Delete                DeleteChar              Delete the character under the cursor
Backspace             BackwardDeleteChar      Delete the character before the cursor
Ctrl+Spacebar         MenuComplete            Complete the input if there is a single completion, otherwise complete the input by selecting from a menu o...
Tab                   TabCompleteNext         Complete the input using the next completion
...
```

### <span data-ttu-id="43c09-117">範例3：取得特定的索引鍵系結</span><span class="sxs-lookup"><span data-stu-id="43c09-117">Example 3: Get specific key bindings</span></span>

<span data-ttu-id="43c09-118">此命令只會傳回指定之索引鍵的系結。</span><span class="sxs-lookup"><span data-stu-id="43c09-118">This command returns only the bindings for the specified keys.</span></span>

```powershell
Get-PSReadLineKeyHandler -Chord Enter, Shift+Enter
```

```Output
Key         Function   Description
---         --------   -----------
Enter       AcceptLine Accept the input or move to the next line if input is missing a closing token.
Shift+Enter AddLine    Move the cursor to the next line without attempting to execute the input
...
```

## <span data-ttu-id="43c09-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43c09-119">PARAMETERS</span></span>

### <span data-ttu-id="43c09-120">-Bound</span><span class="sxs-lookup"><span data-stu-id="43c09-120">-Bound</span></span>

<span data-ttu-id="43c09-121">指出此 Cmdlet 會傳回繫結的函式。</span><span class="sxs-lookup"><span data-stu-id="43c09-121">Indicates that this cmdlet returns functions that are bound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FullListing
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43c09-122">-Unbound</span><span class="sxs-lookup"><span data-stu-id="43c09-122">-Unbound</span></span>

<span data-ttu-id="43c09-123">指出此 Cmdlet 會傳回未繫結的函式。</span><span class="sxs-lookup"><span data-stu-id="43c09-123">Indicates that this cmdlet returns functions that are unbound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FullListing
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43c09-124">-弦</span><span class="sxs-lookup"><span data-stu-id="43c09-124">-Chord</span></span>

<span data-ttu-id="43c09-125">只傳回系結至特定索引鍵或序列的函式。</span><span class="sxs-lookup"><span data-stu-id="43c09-125">Return only functions bound to specific keys or sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: SpecificBindings
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43c09-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43c09-126">CommonParameters</span></span>

<span data-ttu-id="43c09-127">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="43c09-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43c09-128">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="43c09-128">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="43c09-129">輸入</span><span class="sxs-lookup"><span data-stu-id="43c09-129">INPUTS</span></span>

### <span data-ttu-id="43c09-130">無</span><span class="sxs-lookup"><span data-stu-id="43c09-130">None</span></span>

<span data-ttu-id="43c09-131">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43c09-131">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="43c09-132">輸出</span><span class="sxs-lookup"><span data-stu-id="43c09-132">OUTPUTS</span></span>

### <span data-ttu-id="43c09-133">KeyHandler</span><span class="sxs-lookup"><span data-stu-id="43c09-133">Microsoft.PowerShell.KeyHandler</span></span>

## <span data-ttu-id="43c09-134">注意</span><span class="sxs-lookup"><span data-stu-id="43c09-134">NOTES</span></span>

## <span data-ttu-id="43c09-135">相關連結</span><span class="sxs-lookup"><span data-stu-id="43c09-135">RELATED LINKS</span></span>

[<span data-ttu-id="43c09-136">移除-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="43c09-136">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="43c09-137">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="43c09-137">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="43c09-138">設定-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="43c09-138">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="43c09-139">設定-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="43c09-139">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)

