---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/get-psreadlinekeyhandler?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSReadLineKeyHandler
ms.openlocfilehash: 54e1345e949107427f5cd042bbcc253f9ad3416b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203739"
---
# <span data-ttu-id="2e4ca-103">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="2e4ca-103">Get-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="2e4ca-104">概要</span><span class="sxs-lookup"><span data-stu-id="2e4ca-104">SYNOPSIS</span></span>
<span data-ttu-id="2e4ca-105">取得 PSReadLine 模組的索引鍵系結。</span><span class="sxs-lookup"><span data-stu-id="2e4ca-105">Gets the key bindings for the PSReadLine module.</span></span>

## <span data-ttu-id="2e4ca-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2e4ca-106">SYNTAX</span></span>

```
Get-PSReadLineKeyHandler [-Bound] [-Unbound] [<CommonParameters>]
```

## <span data-ttu-id="2e4ca-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2e4ca-107">DESCRIPTION</span></span>

<span data-ttu-id="2e4ca-108">**PSReadLineKeyHandler** 指令 Cmdlet 會傳回目前系結的索引鍵系結。</span><span class="sxs-lookup"><span data-stu-id="2e4ca-108">The **Get-PSReadLineKeyHandler** cmdlet returns the currently bound key bindings.</span></span>

## <span data-ttu-id="2e4ca-109">範例</span><span class="sxs-lookup"><span data-stu-id="2e4ca-109">EXAMPLES</span></span>

### <span data-ttu-id="2e4ca-110">範例 1︰ 取得所有索引鍵對應</span><span class="sxs-lookup"><span data-stu-id="2e4ca-110">Example 1: Get all key mappings</span></span>

<span data-ttu-id="2e4ca-111">此命令會傳回所有索引鍵對應 (包括繫結和未繫結)。</span><span class="sxs-lookup"><span data-stu-id="2e4ca-111">This command returns all key mappings, bound and unbound.</span></span>

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

### <span data-ttu-id="2e4ca-112">範例 2︰取得繫結索引鍵</span><span class="sxs-lookup"><span data-stu-id="2e4ca-112">Example 2: Get bound keys</span></span>

<span data-ttu-id="2e4ca-113">此命令僅會傳回繫結的索引鍵和索引鍵組合。</span><span class="sxs-lookup"><span data-stu-id="2e4ca-113">This command returns only bound keys and key combinations.</span></span>

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

## <span data-ttu-id="2e4ca-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2e4ca-114">PARAMETERS</span></span>

### <span data-ttu-id="2e4ca-115">-Bound</span><span class="sxs-lookup"><span data-stu-id="2e4ca-115">-Bound</span></span>

<span data-ttu-id="2e4ca-116">指出此 Cmdlet 會傳回繫結的函式。</span><span class="sxs-lookup"><span data-stu-id="2e4ca-116">Indicates that this cmdlet returns functions that are bound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e4ca-117">-Unbound</span><span class="sxs-lookup"><span data-stu-id="2e4ca-117">-Unbound</span></span>

<span data-ttu-id="2e4ca-118">指出此 Cmdlet 會傳回未繫結的函式。</span><span class="sxs-lookup"><span data-stu-id="2e4ca-118">Indicates that this cmdlet returns functions that are unbound.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e4ca-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2e4ca-119">CommonParameters</span></span>

<span data-ttu-id="2e4ca-120">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2e4ca-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2e4ca-121">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2e4ca-121">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2e4ca-122">輸入</span><span class="sxs-lookup"><span data-stu-id="2e4ca-122">INPUTS</span></span>

### <span data-ttu-id="2e4ca-123">無</span><span class="sxs-lookup"><span data-stu-id="2e4ca-123">None</span></span>

<span data-ttu-id="2e4ca-124">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e4ca-124">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="2e4ca-125">輸出</span><span class="sxs-lookup"><span data-stu-id="2e4ca-125">OUTPUTS</span></span>

### <span data-ttu-id="2e4ca-126">KeyHandler</span><span class="sxs-lookup"><span data-stu-id="2e4ca-126">Microsoft.PowerShell.KeyHandler</span></span>

## <span data-ttu-id="2e4ca-127">注意</span><span class="sxs-lookup"><span data-stu-id="2e4ca-127">NOTES</span></span>

## <span data-ttu-id="2e4ca-128">相關連結</span><span class="sxs-lookup"><span data-stu-id="2e4ca-128">RELATED LINKS</span></span>

[<span data-ttu-id="2e4ca-129">移除-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="2e4ca-129">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="2e4ca-130">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="2e4ca-130">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="2e4ca-131">設定-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="2e4ca-131">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)

[<span data-ttu-id="2e4ca-132">設定-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="2e4ca-132">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
