---
ms.date: 12/31/2019
title: ISEEditor 物件
description: ISEEditor 物件是 Microsoft.PowerShell.Host.ISE.ISEEditor 類別的執行個體。 主控台窗格是 ISEEditor 物件。
ms.openlocfilehash: ffcb6e35e1160beab6efb29cc84847fa9ffd012b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654051"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="6155c-104">ISEEditor 物件</span><span class="sxs-lookup"><span data-stu-id="6155c-104">The ISEEditor Object</span></span>

<span data-ttu-id="6155c-105">**ISEEditor** 物件是 Microsoft.PowerShell.Host.ISE.ISEEditor 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6155c-105">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="6155c-106">主控台窗格是 **ISEEditor** 物件。</span><span class="sxs-lookup"><span data-stu-id="6155c-106">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="6155c-107">每個 [ISEFile](The-ISEFile-Object.md) 物件都有相關聯的 **ISEEditor** 物件。</span><span class="sxs-lookup"><span data-stu-id="6155c-107">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="6155c-108">下列各節將列出 **ISEEditor** 物件的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="6155c-108">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="6155c-109">方法</span><span class="sxs-lookup"><span data-stu-id="6155c-109">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="6155c-110">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="6155c-110">Clear\(\)</span></span>

<span data-ttu-id="6155c-111">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-112">清除編輯器中的文字。</span><span class="sxs-lookup"><span data-stu-id="6155c-112">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="6155c-113">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="6155c-113">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="6155c-114">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-115">捲動編輯器，即會看見對應至指定 **lineNumber** 參數值的行。</span><span class="sxs-lookup"><span data-stu-id="6155c-115">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="6155c-116">如果指定的行號不在 1 到最後一個定義有效行數的行號範圍內，即會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6155c-116">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="6155c-117">**lineNumber** 要顯示的行號。</span><span class="sxs-lookup"><span data-stu-id="6155c-117">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="6155c-118">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="6155c-118">Focus\(\)</span></span>

<span data-ttu-id="6155c-119">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-120">將焦點設定到編輯器。</span><span class="sxs-lookup"><span data-stu-id="6155c-120">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="6155c-121">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="6155c-121">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="6155c-122">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-123">針對行號所指定的行，以整數形式設定行的長度。</span><span class="sxs-lookup"><span data-stu-id="6155c-123">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="6155c-124">**lineNumber** 要取得長度的行號。</span><span class="sxs-lookup"><span data-stu-id="6155c-124">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="6155c-125">**Returns** 位於指定行號之行的行長度。</span><span class="sxs-lookup"><span data-stu-id="6155c-125">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="6155c-126">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="6155c-126">GoToMatch\(\)</span></span>

<span data-ttu-id="6155c-127">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="6155c-127">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="6155c-128">如果編輯器物件的 **CanGoToMatch** 屬性是 `$true`，就會將插入點移到相符的字元，當插入點位於左括弧、中括弧或大括弧 - `(`、`[`、`{` - 正前方，或者在右括弧、中括弧或大括弧 - `)`、`]`、`}` - 正後方時即會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="6155c-128">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is `$true`, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - `(`,`[`,`{` - or immediately after a closing parenthesis, bracket, or brace - `)`,`]`,`}`.</span></span> <span data-ttu-id="6155c-129">插入號會放置於開端字元之前或結尾字元之後。</span><span class="sxs-lookup"><span data-stu-id="6155c-129">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="6155c-130">如果 **CanGoToMatch** 屬性是 `$false`，則這個方法不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="6155c-130">If the **CanGoToMatch** property is `$false`, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="6155c-131">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="6155c-131">InsertText\( text \)</span></span>

<span data-ttu-id="6155c-132">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-132">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-133">使用文字取代選取範圍，或在目前插入號位置插入文字。</span><span class="sxs-lookup"><span data-stu-id="6155c-133">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="6155c-134">**text** - 字串：要插入的文字。</span><span class="sxs-lookup"><span data-stu-id="6155c-134">**text** - String The text to insert.</span></span>

<span data-ttu-id="6155c-135">請參閱本主題稍後的[指令碼範例](#scripting-example)。</span><span class="sxs-lookup"><span data-stu-id="6155c-135">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="6155c-136">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="6155c-136">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="6155c-137">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-137">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-138">從 **startLine** 、 **startColumn** 、 **endLine** 及 **endColumn** 參數選取文字。</span><span class="sxs-lookup"><span data-stu-id="6155c-138">Selects the text from the **startLine** , **startColumn** , **endLine** , and **endColumn** parameters.</span></span>

<span data-ttu-id="6155c-139">**startLine** - 整數：選取範圍開始位置的行。</span><span class="sxs-lookup"><span data-stu-id="6155c-139">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="6155c-140">**startColumn** - 整數：選取範圍開始位置之起始行內的欄。</span><span class="sxs-lookup"><span data-stu-id="6155c-140">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="6155c-141">**endLine** - 整數：選取範圍結束位置的行。</span><span class="sxs-lookup"><span data-stu-id="6155c-141">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="6155c-142">**endColumn** - 整數：選取範圍結束位置之結尾行內的欄。</span><span class="sxs-lookup"><span data-stu-id="6155c-142">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="6155c-143">請參閱本主題稍後的[指令碼範例](#scripting-example)。</span><span class="sxs-lookup"><span data-stu-id="6155c-143">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="6155c-144">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="6155c-144">SelectCaretLine\(\)</span></span>

<span data-ttu-id="6155c-145">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-145">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-146">選取目前包含插入號的整行文字。</span><span class="sxs-lookup"><span data-stu-id="6155c-146">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="6155c-147">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="6155c-147">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="6155c-148">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-148">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-149">在行號和欄號設定插入號位置。</span><span class="sxs-lookup"><span data-stu-id="6155c-149">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="6155c-150">如果插入點行號或插入點欄號不在其各自的有效範圍內，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6155c-150">It throws an exception if either the caret line number or the caret column number are out of their respective valid ranges.</span></span>

<span data-ttu-id="6155c-151">**lineNumber** - 整數：插入號的行號。</span><span class="sxs-lookup"><span data-stu-id="6155c-151">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="6155c-152">**columnNumber** - 整數：插入號的欄號。</span><span class="sxs-lookup"><span data-stu-id="6155c-152">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="6155c-153">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="6155c-153">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="6155c-154">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="6155c-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="6155c-155">會展開或摺疊所有大綱區段。</span><span class="sxs-lookup"><span data-stu-id="6155c-155">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="6155c-156">屬性</span><span class="sxs-lookup"><span data-stu-id="6155c-156">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="6155c-157">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="6155c-157">CanGoToMatch</span></span>

<span data-ttu-id="6155c-158">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="6155c-158">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="6155c-159">唯讀的布林值屬性，可指出插入點是否位於括弧 `()`、中括弧 `[]` 或大括弧 `{}` 旁邊。</span><span class="sxs-lookup"><span data-stu-id="6155c-159">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - `()`, `[]`, `{}`.</span></span> <span data-ttu-id="6155c-160">如果插入點是在一組開端字元正前方或結尾字元的正後方，則這個屬性值會是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="6155c-160">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is `$true`.</span></span> <span data-ttu-id="6155c-161">否則，會是 `$false`。</span><span class="sxs-lookup"><span data-stu-id="6155c-161">Otherwise, it is `$false`.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="6155c-162">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="6155c-162">CaretColumn</span></span>

<span data-ttu-id="6155c-163">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-163">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-164">唯讀屬性，可取得對應至插入號位置的欄號。</span><span class="sxs-lookup"><span data-stu-id="6155c-164">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="6155c-165">CaretLine</span><span class="sxs-lookup"><span data-stu-id="6155c-165">CaretLine</span></span>

<span data-ttu-id="6155c-166">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-166">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-167">唯讀屬性，可取得包含插入號的行號。</span><span class="sxs-lookup"><span data-stu-id="6155c-167">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="6155c-168">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="6155c-168">CaretLineText</span></span>

<span data-ttu-id="6155c-169">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-170">唯讀屬性，可取得包含插入號的整行文字。</span><span class="sxs-lookup"><span data-stu-id="6155c-170">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="6155c-171">LineCount</span><span class="sxs-lookup"><span data-stu-id="6155c-171">LineCount</span></span>

<span data-ttu-id="6155c-172">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-172">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-173">唯讀屬性，可從編輯器取得行數。</span><span class="sxs-lookup"><span data-stu-id="6155c-173">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="6155c-174">SelectedText</span><span class="sxs-lookup"><span data-stu-id="6155c-174">SelectedText</span></span>

<span data-ttu-id="6155c-175">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-175">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-176">唯讀屬性，可從編輯器取得選取的文字。</span><span class="sxs-lookup"><span data-stu-id="6155c-176">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="6155c-177">請參閱本主題稍後的[指令碼範例](#scripting-example)。</span><span class="sxs-lookup"><span data-stu-id="6155c-177">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="6155c-178">Text</span><span class="sxs-lookup"><span data-stu-id="6155c-178">Text</span></span>

<span data-ttu-id="6155c-179">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="6155c-179">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="6155c-180">唯讀屬性，可在編輯器中取得或設定文字。</span><span class="sxs-lookup"><span data-stu-id="6155c-180">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="6155c-181">請參閱本主題稍後的[指令碼範例](#scripting-example)。</span><span class="sxs-lookup"><span data-stu-id="6155c-181">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="6155c-182">指令碼範例</span><span class="sxs-lookup"><span data-stu-id="6155c-182">Scripting Example</span></span>

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase.
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line.
$endColumn = $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1, 1, 3, $endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="6155c-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6155c-183">See Also</span></span>

- [<span data-ttu-id="6155c-184">ISEFile 物件</span><span class="sxs-lookup"><span data-stu-id="6155c-184">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="6155c-185">PowerShellTab 物件</span><span class="sxs-lookup"><span data-stu-id="6155c-185">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="6155c-186">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="6155c-186">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="6155c-187">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="6155c-187">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
