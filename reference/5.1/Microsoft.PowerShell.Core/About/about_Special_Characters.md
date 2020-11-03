---
description: 描述控制 PowerShell 如何解讀序列中下一個字元的特殊字元序列。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: 875a1c3c63e759151c3c64b5396312b030955cb7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207547"
---
# <a name="about-special-characters"></a><span data-ttu-id="39720-104">關於特殊字元</span><span class="sxs-lookup"><span data-stu-id="39720-104">About Special Characters</span></span>

## <a name="short-description"></a><span data-ttu-id="39720-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="39720-105">Short description</span></span>

<span data-ttu-id="39720-106">描述控制 PowerShell 如何解讀序列中下一個字元的特殊字元序列。</span><span class="sxs-lookup"><span data-stu-id="39720-106">Describes the special character sequences that control how PowerShell interprets the next characters in the sequence.</span></span>

## <a name="long-description"></a><span data-ttu-id="39720-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="39720-107">Long description</span></span>

<span data-ttu-id="39720-108">PowerShell 支援一組特殊字元序列，用來代表不屬於標準字元集的字元。</span><span class="sxs-lookup"><span data-stu-id="39720-108">PowerShell supports a set of special character sequences that are used to represent characters that aren't part of the standard character set.</span></span> <span data-ttu-id="39720-109">這些序列通常稱為「 _escape 序列_ 」。</span><span class="sxs-lookup"><span data-stu-id="39720-109">The sequences are commonly known as _escape sequences_ .</span></span>

<span data-ttu-id="39720-110">Escape sequence 的開頭是倒引號字元，也就是字元，稱為「音符號」 (ASCII 96) ，而且會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="39720-110">Escape sequences begin with the backtick character, known as the grave accent (ASCII 96), and are case-sensitive.</span></span> <span data-ttu-id="39720-111">倒引號字元也可以稱為「escape 字元」（ _escape character_ ）。</span><span class="sxs-lookup"><span data-stu-id="39720-111">The backtick character can also be referred to as the _escape character_ .</span></span>

<span data-ttu-id="39720-112">只有在包含于以雙引號括住的 () 字串時，才會解讀 Escape 序列 `"` 。</span><span class="sxs-lookup"><span data-stu-id="39720-112">Escape sequences are only interpreted when contained in double-quoted (`"`) strings.</span></span>

<span data-ttu-id="39720-113">PowerShell 會辨識這些 escape 序列：</span><span class="sxs-lookup"><span data-stu-id="39720-113">PowerShell recognizes these escape sequences:</span></span>

|  <span data-ttu-id="39720-114">順序</span><span class="sxs-lookup"><span data-stu-id="39720-114">Sequence</span></span>   |       <span data-ttu-id="39720-115">描述</span><span class="sxs-lookup"><span data-stu-id="39720-115">Description</span></span>       |
| ----------- | ----------------------- |
| `` `0 ``    | <span data-ttu-id="39720-116">Null</span><span class="sxs-lookup"><span data-stu-id="39720-116">Null</span></span>                    |
| `` `a ``    | <span data-ttu-id="39720-117">警示</span><span class="sxs-lookup"><span data-stu-id="39720-117">Alert</span></span>                   |
| `` `b ``    | <span data-ttu-id="39720-118">退格鍵</span><span class="sxs-lookup"><span data-stu-id="39720-118">Backspace</span></span>               |
| `` `f ``    | <span data-ttu-id="39720-119">換頁字元</span><span class="sxs-lookup"><span data-stu-id="39720-119">Form feed</span></span>               |
| `` `n ``    | <span data-ttu-id="39720-120">新行</span><span class="sxs-lookup"><span data-stu-id="39720-120">New line</span></span>                |
| `` `r ``    | <span data-ttu-id="39720-121">歸位字元</span><span class="sxs-lookup"><span data-stu-id="39720-121">Carriage return</span></span>         |
| `` `t ``    | <span data-ttu-id="39720-122">水平 Tab 鍵</span><span class="sxs-lookup"><span data-stu-id="39720-122">Horizontal tab</span></span>          |
| `` `v ``    | <span data-ttu-id="39720-123">垂直 Tab 鍵</span><span class="sxs-lookup"><span data-stu-id="39720-123">Vertical tab</span></span>            |

<span data-ttu-id="39720-124">PowerShell 也有特殊標記可標示您想要剖析停止的位置。</span><span class="sxs-lookup"><span data-stu-id="39720-124">PowerShell also has a special token to mark where you want parsing to stop.</span></span> <span data-ttu-id="39720-125">緊接在此標記後面的所有字元都是用來做為不會解讀的常值。</span><span class="sxs-lookup"><span data-stu-id="39720-125">All characters that follow this token are used as literal values that aren't interpreted.</span></span>

<span data-ttu-id="39720-126">特殊剖析權杖：</span><span class="sxs-lookup"><span data-stu-id="39720-126">Special parsing token:</span></span>

| <span data-ttu-id="39720-127">順序</span><span class="sxs-lookup"><span data-stu-id="39720-127">Sequence</span></span> |            <span data-ttu-id="39720-128">描述</span><span class="sxs-lookup"><span data-stu-id="39720-128">Description</span></span>             |
| -------- | ---------------------------------- |
| `--%`    | <span data-ttu-id="39720-129">停止剖析下列任何事項</span><span class="sxs-lookup"><span data-stu-id="39720-129">Stop parsing anything that follows</span></span> |

## <a name="null-0"></a><span data-ttu-id="39720-130">Null (' 0) </span><span class="sxs-lookup"><span data-stu-id="39720-130">Null (\`0)</span></span>

<span data-ttu-id="39720-131">Null (`` `0 ``) 字元在 PowerShell 輸出中會顯示為空白空間。</span><span class="sxs-lookup"><span data-stu-id="39720-131">The null (`` `0 ``) character appears as an empty space in PowerShell output.</span></span>
<span data-ttu-id="39720-132">此功能可讓您使用 PowerShell 來讀取和處理使用 null 字元的文字檔，例如字串終止或記錄終止指標。</span><span class="sxs-lookup"><span data-stu-id="39720-132">This functionality allows you to use PowerShell to read and process text files that use null characters, such as string termination or record termination indicators.</span></span> <span data-ttu-id="39720-133">Null 特殊字元不等於 `$null` 變數，它會儲存 **null** 值。</span><span class="sxs-lookup"><span data-stu-id="39720-133">The null special character isn't equivalent to the `$null` variable, which stores a **null** value.</span></span>

## <a name="alert-a"></a><span data-ttu-id="39720-134">警示 (' a) </span><span class="sxs-lookup"><span data-stu-id="39720-134">Alert (\`a)</span></span>

<span data-ttu-id="39720-135">警示 (`` `a ``) 字元傳送嗶聲信號給電腦的說話者。</span><span class="sxs-lookup"><span data-stu-id="39720-135">The alert (`` `a ``) character sends a beep signal to the computer's speaker.</span></span>
<span data-ttu-id="39720-136">您可以使用此字元來警告使用者即將發生的動作。</span><span class="sxs-lookup"><span data-stu-id="39720-136">You can use this character to warn a user about an impending action.</span></span> <span data-ttu-id="39720-137">下列範例會將兩個嗶聲信號傳送給本機電腦的說話者。</span><span class="sxs-lookup"><span data-stu-id="39720-137">The following example sends two beep signals to the local computer's speaker.</span></span>

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a><span data-ttu-id="39720-138">倒退鍵 (' b) </span><span class="sxs-lookup"><span data-stu-id="39720-138">Backspace (\`b)</span></span>

<span data-ttu-id="39720-139">倒退鍵 (`` `b ``) 字元會將游標移回一個字元，但不會刪除任何字元。</span><span class="sxs-lookup"><span data-stu-id="39720-139">The backspace (`` `b ``) character moves the cursor back one character, but it doesn't delete any characters.</span></span>

<span data-ttu-id="39720-140">此範例會寫入單字 **備份** ，然後將游標移回兩次。</span><span class="sxs-lookup"><span data-stu-id="39720-140">The example writes the word **backup** and then moves the cursor back twice.</span></span>
<span data-ttu-id="39720-141">然後，在新位置寫入一個空格，後面接著 **一個字。**</span><span class="sxs-lookup"><span data-stu-id="39720-141">Then, at the new position, writes a space followed by the word **out** .</span></span>

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="form-feed-f"></a><span data-ttu-id="39720-142">表單摘要 (' f) </span><span class="sxs-lookup"><span data-stu-id="39720-142">Form feed (\`f)</span></span>

<span data-ttu-id="39720-143">表單摘要 (`` `f ``) 字元是一種列印指令，可將目前的頁面彈出並繼續在下一頁進行列印。</span><span class="sxs-lookup"><span data-stu-id="39720-143">The form feed (`` `f ``) character is a print instruction that ejects the current page and continues printing on the next page.</span></span> <span data-ttu-id="39720-144">表單摘要字元只會影響列印的檔。</span><span class="sxs-lookup"><span data-stu-id="39720-144">The form feed character only affects printed documents.</span></span> <span data-ttu-id="39720-145">它不會影響螢幕輸出。</span><span class="sxs-lookup"><span data-stu-id="39720-145">It doesn't affect screen output.</span></span>

## <a name="new-line-n"></a><span data-ttu-id="39720-146">新行 (' n) </span><span class="sxs-lookup"><span data-stu-id="39720-146">New line (\`n)</span></span>

<span data-ttu-id="39720-147">新的行 (`` `n ``) 字元會在字元之後插入分行符號。</span><span class="sxs-lookup"><span data-stu-id="39720-147">The new line (`` `n ``) character inserts a line break immediately after the character.</span></span>

<span data-ttu-id="39720-148">此範例示範如何使用新的行字元，在命令中建立分行符號 `Write-Host` 。</span><span class="sxs-lookup"><span data-stu-id="39720-148">This example shows how to use the new line character to create line breaks in a `Write-Host` command.</span></span>

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a><span data-ttu-id="39720-149">傳回 (' r) 的回車</span><span class="sxs-lookup"><span data-stu-id="39720-149">Carriage return (\`r)</span></span>

<span data-ttu-id="39720-150">「 `` `r `` 換行」 () 字元會將輸出游標移至目前行的開頭，並繼續寫入。</span><span class="sxs-lookup"><span data-stu-id="39720-150">The carriage return (`` `r ``) character moves the output cursor to the beginning of the current line and continues writing.</span></span> <span data-ttu-id="39720-151">目前行上的任何字元都會遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="39720-151">Any characters on the current line are overwritten.</span></span>

<span data-ttu-id="39720-152">在此範例中，會覆寫換行之前的文字。</span><span class="sxs-lookup"><span data-stu-id="39720-152">In this example, the text before the carriage return is overwritten.</span></span>

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

<span data-ttu-id="39720-153">請注意，不會刪除字元之前的文字 `` `r `` ，而是會予以覆寫。</span><span class="sxs-lookup"><span data-stu-id="39720-153">Notice that the text before the `` `r `` character is not deleted, it is overwritten.</span></span>

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a><span data-ttu-id="39720-154">水準索引標籤 (t) </span><span class="sxs-lookup"><span data-stu-id="39720-154">Horizontal tab (\`t)</span></span>

<span data-ttu-id="39720-155">水準 `` `t `` 索引標籤 () 字元前進到下一個索引標籤，然後在該時間點繼續寫入。</span><span class="sxs-lookup"><span data-stu-id="39720-155">The horizontal tab (`` `t ``) character advances to the next tab stop and continues writing at that point.</span></span> <span data-ttu-id="39720-156">根據預設，PowerShell 主控台在每八個空間都有一個 tab 鍵停止。</span><span class="sxs-lookup"><span data-stu-id="39720-156">By default, the PowerShell console has a tab stop at every eighth space.</span></span>

<span data-ttu-id="39720-157">此範例會在每個資料行之間插入兩個索引標籤。</span><span class="sxs-lookup"><span data-stu-id="39720-157">This example inserts two tabs between each column.</span></span>

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="vertical-tab-v"></a><span data-ttu-id="39720-158">垂直索引標籤 (' v) </span><span class="sxs-lookup"><span data-stu-id="39720-158">Vertical tab (\`v)</span></span>

<span data-ttu-id="39720-159">水準 `` `v `` 索引標籤 () 字元前進到下一個垂直定位停駐點，然後寫入該點的剩餘輸出。</span><span class="sxs-lookup"><span data-stu-id="39720-159">The horizontal tab (`` `v ``) character advances to the next vertical tab stop and writes the remaining output at that point.</span></span> <span data-ttu-id="39720-160">這在預設的 Windows 主控台中沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="39720-160">This has no effect in the default Windows console.</span></span>

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

<span data-ttu-id="39720-161">下列範例顯示您會在印表機或不同主控台主機中取得的輸出。</span><span class="sxs-lookup"><span data-stu-id="39720-161">The following example shows the output you would get on a printer or in a different console host.</span></span>

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a><span data-ttu-id="39720-162">停止剖析權杖 (--% ) </span><span class="sxs-lookup"><span data-stu-id="39720-162">Stop-parsing token (--%)</span></span>

<span data-ttu-id="39720-163">停止剖析 (`--%`) token 可防止 powershell 將字串解讀為 powershell 命令和運算式。</span><span class="sxs-lookup"><span data-stu-id="39720-163">The stop-parsing (`--%`) token prevents PowerShell from interpreting strings as PowerShell commands and expressions.</span></span> <span data-ttu-id="39720-164">這可將這些字串傳遞給其他程式以進行解讀。</span><span class="sxs-lookup"><span data-stu-id="39720-164">This allows those strings to be passed to other programs for interpretation.</span></span>

<span data-ttu-id="39720-165">將停止剖析標記放在程式名稱之後，以及可能會造成錯誤的程式引數之前。</span><span class="sxs-lookup"><span data-stu-id="39720-165">Place the stop-parsing token after the program name and before program arguments that might cause errors.</span></span>

<span data-ttu-id="39720-166">在此範例中，此 `Icacls` 命令會使用停止剖析權杖。</span><span class="sxs-lookup"><span data-stu-id="39720-166">In this example, the `Icacls` command uses the stop-parsing token.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="39720-167">PowerShell 會將下列字串傳送給 `Icacls` 。</span><span class="sxs-lookup"><span data-stu-id="39720-167">PowerShell sends the following string to `Icacls`.</span></span>

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="39720-168">以下是另一個範例。</span><span class="sxs-lookup"><span data-stu-id="39720-168">Here is another example.</span></span> <span data-ttu-id="39720-169">**ShowArgs** 函式會輸出傳遞給它的值。</span><span class="sxs-lookup"><span data-stu-id="39720-169">The **showArgs** function outputs the values passed to it.</span></span> <span data-ttu-id="39720-170">在此範例中，我們會將名 `$HOME` 為的變數傳遞給函式兩次。</span><span class="sxs-lookup"><span data-stu-id="39720-170">In this example, we pass the variable named `$HOME` to the function twice.</span></span>

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

您可以在輸出中看到，針對第一個參數，變數 `$HOME` 會由 PowerShell 所解釋，以便將變數的值傳遞至函式。 <span data-ttu-id="39720-172">第二種用途是在 `$HOME` 停止剖析 token 之後，因此字串 "$HOME" 會傳遞至函式，而不需解讀。</span><span class="sxs-lookup"><span data-stu-id="39720-172">The second use of `$HOME` comes after the stop-parsing token, so the string "$HOME" is passed to the function without interpretation.</span></span>

```Output
$args = C:\Users\username|--%|$HOME
```

<span data-ttu-id="39720-173">如需有關停止剖析權杖的詳細資訊，請參閱 [about_Parsing](about_Parsing.md)。</span><span class="sxs-lookup"><span data-stu-id="39720-173">For more information about the stop-parsing token, see [about_Parsing](about_Parsing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="39720-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39720-174">See also</span></span>

[<span data-ttu-id="39720-175">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="39720-175">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
