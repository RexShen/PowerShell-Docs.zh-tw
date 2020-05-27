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
# <a name="the-iseeditor-object"></a>ISEEditor 物件

**ISEEditor** 物件是 Microsoft.PowerShell.Host.ISE.ISEEditor 類別的執行個體。 主控台窗格是 **ISEEditor** 物件。 每個 [ISEFile](The-ISEFile-Object.md) 物件都有相關聯的 **ISEEditor** 物件。 下列各節將列出 **ISEEditor** 物件的方法和屬性。

## <a name="methods"></a>方法

### <a name="clear"></a>Clear\(\)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

清除編輯器中的文字。

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

捲動編輯器，即會看見對應至指定 **lineNumber** 參數值的行。 如果指定的行號不在 1 到最後一個定義有效行數的行號範圍內，即會擲回例外狀況。

**lineNumber** 要顯示的行號。

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Focus\(\)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

將焦點設定到編輯器。

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber \)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

針對行號所指定的行，以整數形式設定行的長度。

**lineNumber** 要取得長度的行號。

**Returns** 位於指定行號的行長度。

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

如果編輯器物件的 **CanGoToMatch** 屬性是 `$true`，就會將插入點移到相符的字元，當插入點位於左括弧、中括弧或大括弧 - `(`、`[`、`{` - 正前方，或者在右括弧、中括弧或大括弧 - `)`、`]`、`}` - 正後方時即會發生此情況。 插入號會放置於開端字元之前或結尾字元之後。 如果 **CanGoToMatch** 屬性是 `$false`，則這個方法不會執行任何動作。

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a>InsertText\( text \)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

使用文字取代選取範圍，或在目前插入號位置插入文字。

**text** - 字串：要插入的文字。

請參閱本主題稍後的[指令碼範例](#scripting-example)。

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Select\( startLine, startColumn, endLine, endColumn \)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

從 **startLine**、**startColumn**、**endLine** 及 **endColumn** 參數選取文字。

**startLine** - 整數：選取範圍開始位置的行。

**startColumn** - 整數：選取範圍開始位置之起始行內的欄。

**endLine** - 整數：選取範圍結束位置的行。

**endColumn** - 整數：選取範圍結束位置之結尾行內的欄。

請參閱本主題稍後的[指令碼範例](#scripting-example)。

### <a name="selectcaretline"></a>SelectCaretLine\(\)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

選取目前包含插入號的整行文字。

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber \)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

在行號和欄號設定插入號位置。 如果插入點行號或插入點欄號不在其各自的有效範圍內，就會擲回例外狀況。

**lineNumber** - 整數：插入號的行號。

**columnNumber** - 整數：插入號的欄號。

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

會展開或摺疊所有大綱區段。

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>屬性

### <a name="cangotomatch"></a>CanGoToMatch

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

唯讀的布林值屬性，可指出插入點是否位於括弧 `()`、中括弧 `[]` 或大括弧 `{}` 旁邊。 如果插入點是在一組開端字元正前方或結尾字元的正後方，則這個屬性值會是 `$true`。 否則，會是 `$false`。

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得對應至插入號位置的欄號。

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得包含插入號的行號。

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得包含插入號的整行文字。

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可從編輯器取得行數。

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可從編輯器取得選取的文字。

請參閱本主題稍後的[指令碼範例](#scripting-example)。

### <a name="text"></a>Text

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可在編輯器中取得或設定文字。

請參閱本主題稍後的[指令碼範例](#scripting-example)。

## <a name="scripting-example"></a>指令碼範例

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

## <a name="see-also"></a>另請參閱

- [ISEFile 物件](The-ISEFile-Object.md)
- [PowerShellTab 物件](The-PowerShellTab-Object.md)
- [Windows PowerShell ISE 指令碼物件模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)
