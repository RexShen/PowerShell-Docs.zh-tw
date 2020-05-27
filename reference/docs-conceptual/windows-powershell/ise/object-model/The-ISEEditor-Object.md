---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEEditor 物件
ms.openlocfilehash: cb63acebc1a8bb9fa6cc07199088ae0d5441bc91
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809694"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="f15ce-103">ISEEditor 物件</span><span class="sxs-lookup"><span data-stu-id="f15ce-103">The ISEEditor Object</span></span>

<span data-ttu-id="f15ce-104">**ISEEditor** 物件是 Microsoft.PowerShell.Host.ISE.ISEEditor 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f15ce-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="f15ce-105">主控台窗格是 **ISEEditor** 物件。</span><span class="sxs-lookup"><span data-stu-id="f15ce-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="f15ce-106">每個 [ISEFile](The-ISEFile-Object.md) 物件都有相關聯的 **ISEEditor** 物件。</span><span class="sxs-lookup"><span data-stu-id="f15ce-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="f15ce-107">下列各節將列出 **ISEEditor** 物件的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="f15ce-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="f15ce-108">方法</span><span class="sxs-lookup"><span data-stu-id="f15ce-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="f15ce-109">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="f15ce-109">Clear\(\)</span></span>

<span data-ttu-id="f15ce-110">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-111">清除編輯器中的文字。</span><span class="sxs-lookup"><span data-stu-id="f15ce-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="f15ce-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="f15ce-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="f15ce-113">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-114">捲動編輯器，即會看見對應至指定 **lineNumber** 參數值的行。</span><span class="sxs-lookup"><span data-stu-id="f15ce-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="f15ce-115">如果指定的行號不在 1 到最後一個定義有效行數的行號範圍內，即會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f15ce-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="f15ce-116">**lineNumber** 要顯示的行號。</span><span class="sxs-lookup"><span data-stu-id="f15ce-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="f15ce-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="f15ce-117">Focus\(\)</span></span>

<span data-ttu-id="f15ce-118">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-119">將焦點設定到編輯器。</span><span class="sxs-lookup"><span data-stu-id="f15ce-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="f15ce-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="f15ce-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="f15ce-121">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-122">針對行號所指定的行，以整數形式設定行的長度。</span><span class="sxs-lookup"><span data-stu-id="f15ce-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="f15ce-123">**lineNumber** 要取得長度的行號。</span><span class="sxs-lookup"><span data-stu-id="f15ce-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="f15ce-124">**Returns** 位於指定行號的行長度。</span><span class="sxs-lookup"><span data-stu-id="f15ce-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="f15ce-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="f15ce-125">GoToMatch\(\)</span></span>

<span data-ttu-id="f15ce-126">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="f15ce-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f15ce-127">如果編輯器物件的 **CanGoToMatch** 屬性是 `$true`，就會將插入點移到相符的字元，當插入點位於左括弧、中括弧或大括弧 - `(`、`[`、`{` - 正前方，或者在右括弧、中括弧或大括弧 - `)`、`]`、`}` - 正後方時即會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="f15ce-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is `$true`, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - `(`,`[`,`{` - or immediately after a closing parenthesis, bracket, or brace - `)`,`]`,`}`.</span></span> <span data-ttu-id="f15ce-128">插入號會放置於開端字元之前或結尾字元之後。</span><span class="sxs-lookup"><span data-stu-id="f15ce-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="f15ce-129">如果 **CanGoToMatch** 屬性是 `$false`，則這個方法不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="f15ce-129">If the **CanGoToMatch** property is `$false`, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="f15ce-130">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="f15ce-130">InsertText\( text \)</span></span>

<span data-ttu-id="f15ce-131">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-132">使用文字取代選取範圍，或在目前插入號位置插入文字。</span><span class="sxs-lookup"><span data-stu-id="f15ce-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="f15ce-133">**text** - 字串：要插入的文字。</span><span class="sxs-lookup"><span data-stu-id="f15ce-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="f15ce-134">請參閱本主題稍後的[指令碼範例](#scripting-example)。</span><span class="sxs-lookup"><span data-stu-id="f15ce-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="f15ce-135">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="f15ce-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="f15ce-136">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-137">從 **startLine**、**startColumn**、**endLine** 及 **endColumn** 參數選取文字。</span><span class="sxs-lookup"><span data-stu-id="f15ce-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="f15ce-138">**startLine** - 整數：選取範圍開始位置的行。</span><span class="sxs-lookup"><span data-stu-id="f15ce-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="f15ce-139">**startColumn** - 整數：選取範圍開始位置之起始行內的欄。</span><span class="sxs-lookup"><span data-stu-id="f15ce-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="f15ce-140">**endLine** - 整數：選取範圍結束位置的行。</span><span class="sxs-lookup"><span data-stu-id="f15ce-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="f15ce-141">**endColumn** - 整數：選取範圍結束位置之結尾行內的欄。</span><span class="sxs-lookup"><span data-stu-id="f15ce-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="f15ce-142">請參閱本主題稍後的[指令碼範例](#scripting-example)。</span><span class="sxs-lookup"><span data-stu-id="f15ce-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="f15ce-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="f15ce-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="f15ce-144">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-145">選取目前包含插入號的整行文字。</span><span class="sxs-lookup"><span data-stu-id="f15ce-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="f15ce-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="f15ce-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="f15ce-147">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-148">在行號和欄號設定插入號位置。</span><span class="sxs-lookup"><span data-stu-id="f15ce-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="f15ce-149">如果插入點行號或插入點欄號不在其各自的有效範圍內，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f15ce-149">It throws an exception if either the caret line number or the caret column number are out of their respective valid ranges.</span></span>

<span data-ttu-id="f15ce-150">**lineNumber** - 整數：插入號的行號。</span><span class="sxs-lookup"><span data-stu-id="f15ce-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="f15ce-151">**columnNumber** - 整數：插入號的欄號。</span><span class="sxs-lookup"><span data-stu-id="f15ce-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="f15ce-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="f15ce-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="f15ce-153">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="f15ce-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f15ce-154">會展開或摺疊所有大綱區段。</span><span class="sxs-lookup"><span data-stu-id="f15ce-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="f15ce-155">屬性</span><span class="sxs-lookup"><span data-stu-id="f15ce-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="f15ce-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="f15ce-156">CanGoToMatch</span></span>

<span data-ttu-id="f15ce-157">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="f15ce-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="f15ce-158">唯讀的布林值屬性，可指出插入點是否位於括弧 `()`、中括弧 `[]` 或大括弧 `{}` 旁邊。</span><span class="sxs-lookup"><span data-stu-id="f15ce-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - `()`, `[]`, `{}`.</span></span> <span data-ttu-id="f15ce-159">如果插入點是在一組開端字元正前方或結尾字元的正後方，則這個屬性值會是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="f15ce-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is `$true`.</span></span> <span data-ttu-id="f15ce-160">否則，會是 `$false`。</span><span class="sxs-lookup"><span data-stu-id="f15ce-160">Otherwise, it is `$false`.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="f15ce-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="f15ce-161">CaretColumn</span></span>

<span data-ttu-id="f15ce-162">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-163">唯讀屬性，可取得對應至插入號位置的欄號。</span><span class="sxs-lookup"><span data-stu-id="f15ce-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="f15ce-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="f15ce-164">CaretLine</span></span>

<span data-ttu-id="f15ce-165">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-166">唯讀屬性，可取得包含插入號的行號。</span><span class="sxs-lookup"><span data-stu-id="f15ce-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="f15ce-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="f15ce-167">CaretLineText</span></span>

<span data-ttu-id="f15ce-168">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-169">唯讀屬性，可取得包含插入號的整行文字。</span><span class="sxs-lookup"><span data-stu-id="f15ce-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="f15ce-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="f15ce-170">LineCount</span></span>

<span data-ttu-id="f15ce-171">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-172">唯讀屬性，可從編輯器取得行數。</span><span class="sxs-lookup"><span data-stu-id="f15ce-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="f15ce-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="f15ce-173">SelectedText</span></span>

<span data-ttu-id="f15ce-174">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-175">唯讀屬性，可從編輯器取得選取的文字。</span><span class="sxs-lookup"><span data-stu-id="f15ce-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="f15ce-176">請參閱本主題稍後的[指令碼範例](#scripting-example)。</span><span class="sxs-lookup"><span data-stu-id="f15ce-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="f15ce-177">Text</span><span class="sxs-lookup"><span data-stu-id="f15ce-177">Text</span></span>

<span data-ttu-id="f15ce-178">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="f15ce-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="f15ce-179">唯讀屬性，可在編輯器中取得或設定文字。</span><span class="sxs-lookup"><span data-stu-id="f15ce-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="f15ce-180">請參閱本主題稍後的[指令碼範例](#scripting-example)。</span><span class="sxs-lookup"><span data-stu-id="f15ce-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="f15ce-181">指令碼範例</span><span class="sxs-lookup"><span data-stu-id="f15ce-181">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f15ce-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f15ce-182">See Also</span></span>

- [<span data-ttu-id="f15ce-183">ISEFile 物件</span><span class="sxs-lookup"><span data-stu-id="f15ce-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="f15ce-184">PowerShellTab 物件</span><span class="sxs-lookup"><span data-stu-id="f15ce-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="f15ce-185">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="f15ce-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="f15ce-186">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="f15ce-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)