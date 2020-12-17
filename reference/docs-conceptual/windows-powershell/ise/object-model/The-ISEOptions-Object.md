---
ms.date: 12/31/2019
title: ISEOptions 物件
description: ISEOptions 物件代表適用於 Windows PowerShell ISE 的各種設定。
ms.openlocfilehash: 9823a4a0ea32420d830735a0a61a6c03a6458fb7
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391505"
---
# <a name="the-iseoptions-object"></a>ISEOptions 物件

**ISEOptions** 物件代表適用於 Windows PowerShell ISE 的各種設定。 它是 **Microsoft.PowerShell.Host.ISE.ISEOptions** 類別的執行個體。

**ISEOptions** 物件提供下列方法和屬性。

## <a name="methods"></a>方法

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

還原主控台窗格中語彙基元色彩的預設值。

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

還原主控台窗格中所有選項設定的預設值。 它也會重設各種警告訊息的行為，提供標準的核取方塊來防止再次顯示訊息。

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

還原指令碼窗格中語彙基元色彩的預設值。

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

針對顯示於 Windows PowerShell ISE 中的 XML 項目，還原語彙基元色彩的預設值。 另請參閱 [XmlTokenColors](#xmltokencolors)。

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>屬性

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定由 Windows PowerShell ISE 自動執行儲存檔案作業之間的分鐘數。 預設值是 2 分鐘。 值為整數。

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor

此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。 如需更新版本，請參閱 [ConsolePaneBackgroundColor](#consolepanebackgroundcolor)。

指定命令窗格的背景色彩。 它是 **System.Windows.Media.Color** 類別的執行個體。

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a>CommandPaneUp

此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。

指定命令窗格是否要位於輸出窗格上方。

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a>ConsolePaneBackgroundColor

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定主控台窗格的背景色彩。 它是 **System.Windows.Media.Color** 類別的執行個體。

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定主控台窗格中文字的前景色彩。

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定主控台窗格中文字的背景色彩。

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a>ConsoleTokenColors

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

在 Windows PowerShell ISE 主控台窗格中，指定 IntelliSense 語彙基元的色彩。 這個屬性是一個字典物件，其中包含適用於主控台窗格的語彙基元類型及色彩的名稱/值組。 若要變更指令碼窗格中 IntelliSense 語彙基元的色彩，請參閱 [TokenColors](#tokencolors)。
若要將色彩重設為預設值，請參閱 [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors)。
您可以為下列各項設定語彙基元色彩：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

針對出現在主控台窗格中的偵錯文字指定背景色彩。 它是 **System.Windows.Media.Color** 類別的執行個體。

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

針對出現在主控台窗格中的偵錯文字指定前景色彩。 它是 **System.Windows.Media.Color** 類別的執行個體。

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a>DefaultOptions

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

一個屬性集合，可指定使用重設方法時要使用的預設值。

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions
```

```Output
SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a>ErrorBackgroundColor

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

針對出現在主控台窗格中的錯誤文字指定背景色彩。 它是 **System.Windows.Media.Color** 類別的執行個體。

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

針對出現在主控台窗格中的錯誤文字指定前景色彩。 它是 **System.Windows.Media.Color** 類別的執行個體。

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a>FontName

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

指定目前在指令碼窗格和主控台窗格中使用的字型名稱。

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a>FontSize

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

以整數形式指定字型大小。 其會用於指令碼窗格、命令窗格及輸出窗格中。 有效值範圍是 8 到 32。

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定 IntelliSense 用來解析目前輸入文字的秒數。
經過此秒數之後，IntelliSense 即會逾時，並可讓您繼續輸入。 預設值為 3 秒。 值為整數。

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定 Windows PowerShell ISE 所追蹤之最近開啟的檔案個數，並顯示於 [開啟舊檔]  功能表底部。 預設值是 10。 值為整數。

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor

此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。 如需更新版本，請參閱 [ConsolePaneBackgroundColor](#consolepanebackgroundcolor)。

讀取/寫入屬性，可取得或設定輸出窗格本身的背景色彩。 它是 **System.Windows.Media.Color** 類別的執行個體。

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor

此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。 如需更新版本，請參閱 [ConsolePaneForegroundColor](#consolepaneforegroundcolor)。

讀取/寫入屬性，可在 Windows PowerShell ISE 2.0 中變更輸出窗格中文字的前景色彩。

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor

此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。 如需更新版本，請參閱 [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor)。

讀取/寫入屬性，可變更輸出窗格中文字的背景色彩。

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

讀取/寫入屬性，可取得或設定檔案的背景色彩。 它是 **System.Windows.Media.Color** 類別的執行個體。

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

讀取/寫入屬性，可取得或設定指令碼窗格中非指令碼檔案的前景色彩。
若要設定指令碼檔案的前景色彩，請使用 [TokenColors](#tokencolors)。

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

讀取/寫入屬性，可在顯示器上取得或設定指令碼窗格的位置。 字串可以是 'Maximized'、'Top' 或 'Right'。

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定程式碼片段的 <kbd>CTRL</kbd>+<kbd>J</kbd> 清單是否包括隨附於 Windows PowerShell 的入門集。 設定為 `$false` 時，只有使用者定義的程式碼片段會出現在 <kbd>CTRL</kbd>+<kbd>J</kbd> 清單中。
預設值是 `$true`。

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定 IntelliSense 是否會在主控台窗格中提供語法、參數和值的建議。
預設值是 `$true`。

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定 IntelliSense 是否會在指令碼窗格中提供語法、參數和值的建議。
預設值是 `$true`。

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定指令碼窗格是否會在左邊界中顯示行號。 預設值是 `$true`。

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定指令碼窗格是否會在左邊界中的程式碼區段旁邊顯示可展開和可摺疊的括弧。 如果顯示，您可以按一下文字區塊旁邊的減號 `-` 圖示來摺疊它，或按一下加號 `+` 圖示來展開文字區塊。 預設值是 `$true`。

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>ShowToolBar

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

指定 ISE 工具列是否會出現在 Windows PowerShell ISE 視窗的頂端。 預設值是 `$true`。

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

指定若指令碼在執行之前自動儲存，是否會出現警告訊息。
預設值是 `$true`。

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

指定在不同的 PowerShell 索引標籤中開啟同一個檔案時，是否會出現警告訊息。 如果設定為 `$true`，在多個索引標籤中開啟相同檔案會顯示下列訊息：「已在另一個 PowerShell 索引標籤中開啟這個檔案的副本。變更這個檔案將會影響所有已開啟的副本。」 預設值是 `$true`。

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a>TokenColors

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

在 Windows PowerShell ISE 指令碼窗格中，指定 IntelliSense 語彙基元的色彩。 這個屬性是一個字典物件，其中包含適用於指令碼窗格的語彙基元類型及色彩的名稱/值組。 若要變更主控台窗格中 IntelliSense 語彙基元的色彩，請參閱 [ConsoleTokenColors](#consoletokencolors)。
若要將色彩重設為預設值，請參閱 [RestoreDefaultTokenColors](#restoredefaulttokencolors)。
您可以為下列各項設定語彙基元色彩：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定您是否可以使用 Enter 鍵來選取主控台窗格中 IntelliSense 提供的選項。 預設值是 `$true`。

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定您是否可以使用 Enter 鍵來選取指令碼窗格中 IntelliSense 提供的選項。 預設值是 `$true`。

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a>UseLocalHelp

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定當您將游標放置於關鍵字中並按下 <kbd>F1</kbd> 時，要顯示本機安裝的說明或線上說明。 如果設定為 `$true`，則快顯視窗會顯示本機安裝的說明內容。 您可以執行 `Update-Help` 命令來安裝說明檔。 如果設定為 `$false`，則您的瀏覽器會開啟 docs.microsoft.com 上的頁面。

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a>VerboseBackgroundColor

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

針對出現在主控台窗格中的詳細資訊文字指定背景色彩。 它是 **System.Windows.Media.Color** 物件。

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a>VerboseForegroundColor

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

針對出現在主控台窗格中的詳細資訊文字指定前景色彩。 它是 **System.Windows.Media.Color** 物件。

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a>WarningBackgroundColor

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

針對出現在主控台窗格中的警告文字指定背景色彩。 它是 **System.Windows.Media.Color** 物件。

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a>WarningForegroundColor

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

針對出現在輸出窗格中的警告文字指定前景色彩。 它是 **System.Windows.Media.Color** 物件。

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a>XmlTokenColors

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

指定一個字典物件，其中包含適用於 Windows PowerShell ISE 中所顯示之 XML 內容的語彙基元類型和色彩的名稱/值組。 您可以為下列各項設定語彙基元色彩：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。 另請參閱 [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors)。

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a>Zoom

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

在主控台和指令碼窗格中指定文字的相對大小。 預設值是 100。
值越小，在 Windows PowerShell ISE 中出現的文字就越小，而值越大，出現的文字就越大。 值為整數，範圍可從 20 到 400。

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>另請參閱

- [Windows PowerShell ISE 指令碼物件模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)
