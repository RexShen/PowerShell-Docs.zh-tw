---
ms.date: 12/31/2019
title: ISEOptions 物件
description: ISEOptions 物件代表適用於 Windows PowerShell ISE 的各種設定。
ms.openlocfilehash: 4f790550796f40c7a2d4882cc0444fa7a55eeee9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661027"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="b4a5b-103">ISEOptions 物件</span><span class="sxs-lookup"><span data-stu-id="b4a5b-103">The ISEOptions Object</span></span>

<span data-ttu-id="b4a5b-104">**ISEOptions** 物件代表適用於 Windows PowerShell ISE 的各種設定。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="b4a5b-105">它是 **Microsoft.PowerShell.Host.ISE.ISEOptions** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="b4a5b-106">**ISEOptions** 物件提供下列方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="b4a5b-107">方法</span><span class="sxs-lookup"><span data-stu-id="b4a5b-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="b4a5b-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="b4a5b-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="b4a5b-109">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-110">還原主控台窗格中語彙基元色彩的預設值。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="b4a5b-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="b4a5b-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="b4a5b-112">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-113">還原主控台窗格中所有選項設定的預設值。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="b4a5b-114">它也會重設各種警告訊息的行為，提供標準的核取方塊來防止再次顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="b4a5b-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="b4a5b-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="b4a5b-116">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-117">還原指令碼窗格中語彙基元色彩的預設值。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="b4a5b-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="b4a5b-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="b4a5b-119">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-120">針對顯示於 Windows PowerShell ISE 中的 XML 項目，還原語彙基元色彩的預設值。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="b4a5b-121">另請參閱 [XmlTokenColors](#xmltokencolors)。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="b4a5b-122">屬性</span><span class="sxs-lookup"><span data-stu-id="b4a5b-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="b4a5b-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="b4a5b-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="b4a5b-124">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-125">指定由 Windows PowerShell ISE 自動執行儲存檔案作業之間的分鐘數。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="b4a5b-126">預設值是 2 分鐘。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-126">The default value is 2 minutes.</span></span> <span data-ttu-id="b4a5b-127">值為整數。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="b4a5b-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="b4a5b-129">此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="b4a5b-130">如需更新版本，請參閱 [ConsolePaneBackgroundColor](#consolepanebackgroundcolor)。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="b4a5b-131">指定命令窗格的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="b4a5b-132">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="b4a5b-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="b4a5b-133">CommandPaneUp</span></span>

<span data-ttu-id="b4a5b-134">此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="b4a5b-135">指定命令窗格是否要位於輸出窗格上方。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="b4a5b-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="b4a5b-137">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-138">指定主控台窗格的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="b4a5b-139">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="b4a5b-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="b4a5b-141">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-142">指定主控台窗格中文字的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="b4a5b-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="b4a5b-144">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-145">指定主控台窗格中文字的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="b4a5b-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="b4a5b-146">ConsoleTokenColors</span></span>

<span data-ttu-id="b4a5b-147">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-148">在 Windows PowerShell ISE 主控台窗格中，指定 IntelliSense 語彙基元的色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="b4a5b-149">這個屬性是一個字典物件，其中包含適用於主控台窗格的語彙基元類型及色彩的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="b4a5b-150">若要變更指令碼窗格中 IntelliSense 語彙基元的色彩，請參閱 [TokenColors](#tokencolors)。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span>
<span data-ttu-id="b4a5b-151">若要將色彩重設為預設值，請參閱 [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors)。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span>
<span data-ttu-id="b4a5b-152">您可以為下列各項設定語彙基元色彩：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="b4a5b-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-153">DebugBackgroundColor</span></span>

<span data-ttu-id="b4a5b-154">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-155">針對出現在主控台窗格中的偵錯文字指定背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="b4a5b-156">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="b4a5b-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-157">DebugForegroundColor</span></span>

<span data-ttu-id="b4a5b-158">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-159">針對出現在主控台窗格中的偵錯文字指定前景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="b4a5b-160">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="b4a5b-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="b4a5b-161">DefaultOptions</span></span>

<span data-ttu-id="b4a5b-162">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-163">一個屬性集合，可指定使用重設方法時要使用的預設值。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="b4a5b-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="b4a5b-165">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-166">針對出現在主控台窗格中的錯誤文字指定背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="b4a5b-167">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="b4a5b-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-168">ErrorForegroundColor</span></span>

<span data-ttu-id="b4a5b-169">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-170">針對出現在主控台窗格中的錯誤文字指定前景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="b4a5b-171">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="b4a5b-172">FontName</span><span class="sxs-lookup"><span data-stu-id="b4a5b-172">FontName</span></span>

<span data-ttu-id="b4a5b-173">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-174">指定目前在指令碼窗格和主控台窗格中使用的字型名稱。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="b4a5b-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="b4a5b-175">FontSize</span></span>

<span data-ttu-id="b4a5b-176">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-177">以整數形式指定字型大小。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="b4a5b-178">其會用於指令碼窗格、命令窗格及輸出窗格中。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="b4a5b-179">有效值範圍是 8 到 32。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="b4a5b-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="b4a5b-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="b4a5b-181">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-182">指定 IntelliSense 用來解析目前輸入文字的秒數。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span>
<span data-ttu-id="b4a5b-183">經過此秒數之後，IntelliSense 即會逾時，並可讓您繼續輸入。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="b4a5b-184">預設值為 3 秒。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-184">The default value is 3 seconds.</span></span> <span data-ttu-id="b4a5b-185">值為整數。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="b4a5b-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="b4a5b-186">MruCount</span></span>

<span data-ttu-id="b4a5b-187">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-188">指定 Windows PowerShell ISE 所追蹤之最近開啟的檔案個數，並顯示於 [開啟舊檔]  功能表底部。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="b4a5b-189">預設值是 10。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-189">The default value is 10.</span></span> <span data-ttu-id="b4a5b-190">值為整數。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="b4a5b-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="b4a5b-192">此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="b4a5b-193">如需更新版本，請參閱 [ConsolePaneBackgroundColor](#consolepanebackgroundcolor)。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="b4a5b-194">讀取/寫入屬性，可取得或設定輸出窗格本身的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="b4a5b-195">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="b4a5b-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="b4a5b-197">此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="b4a5b-198">如需更新版本，請參閱 [ConsolePaneForegroundColor](#consolepaneforegroundcolor)。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="b4a5b-199">讀取/寫入屬性，可在 Windows PowerShell ISE 2.0 中變更輸出窗格中文字的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="b4a5b-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="b4a5b-201">此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="b4a5b-202">如需更新版本，請參閱 [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor)。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="b4a5b-203">讀取/寫入屬性，可變更輸出窗格中文字的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="b4a5b-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="b4a5b-205">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-206">讀取/寫入屬性，可取得或設定檔案的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="b4a5b-207">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="b4a5b-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="b4a5b-209">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-210">讀取/寫入屬性，可取得或設定指令碼窗格中非指令碼檔案的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="b4a5b-211">若要設定指令碼檔案的前景色彩，請使用 [TokenColors](#tokencolors)。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="b4a5b-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="b4a5b-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="b4a5b-213">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-214">讀取/寫入屬性，可在顯示器上取得或設定指令碼窗格的位置。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="b4a5b-215">字串可以是 'Maximized'、'Top' 或 'Right'。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="b4a5b-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="b4a5b-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="b4a5b-217">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-218">指定程式碼片段的 <kbd>CTRL</kbd>+<kbd>J</kbd> 清單是否包括隨附於 Windows PowerShell 的入門集。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-218">Specifies whether the <kbd>CTRL</kbd>+<kbd>J</kbd> list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="b4a5b-219">設定為 `$false` 時，只有使用者定義的程式碼片段會出現在 <kbd>CTRL</kbd>+<kbd>J</kbd> 清單中。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-219">When set to `$false`, only user-defined snippets appear in the <kbd>CTRL</kbd>+<kbd>J</kbd> list.</span></span>
<span data-ttu-id="b4a5b-220">預設值是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-220">The default value is `$true`.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="b4a5b-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="b4a5b-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="b4a5b-222">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-223">指定 IntelliSense 是否會在主控台窗格中提供語法、參數和值的建議。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span>
<span data-ttu-id="b4a5b-224">預設值是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-224">The default value is `$true`.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="b4a5b-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="b4a5b-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="b4a5b-226">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-227">指定 IntelliSense 是否會在指令碼窗格中提供語法、參數和值的建議。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span>
<span data-ttu-id="b4a5b-228">預設值是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-228">The default value is `$true`.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="b4a5b-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="b4a5b-229">ShowLineNumbers</span></span>

<span data-ttu-id="b4a5b-230">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-231">指定指令碼窗格是否會在左邊界中顯示行號。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="b4a5b-232">預設值是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-232">The default value is `$true`.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="b4a5b-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="b4a5b-233">ShowOutlining</span></span>

<span data-ttu-id="b4a5b-234">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-235">指定指令碼窗格是否會在左邊界中的程式碼區段旁邊顯示可展開和可摺疊的括弧。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="b4a5b-236">如果顯示，您可以按一下文字區塊旁邊的減號 `-` 圖示來摺疊它，或按一下加號 `+` 圖示來展開文字區塊。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-236">When they are displayed, you can click the minus `-` icons next to a block of text to collapse it or click the plus `+` icon to expand a block of text.</span></span> <span data-ttu-id="b4a5b-237">預設值是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-237">The default value is `$true`.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="b4a5b-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="b4a5b-238">ShowToolBar</span></span>

<span data-ttu-id="b4a5b-239">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-240">指定 ISE 工具列是否會出現在 Windows PowerShell ISE 視窗的頂端。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="b4a5b-241">預設值是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-241">The default value is `$true`.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="b4a5b-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="b4a5b-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="b4a5b-243">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-244">指定若指令碼在執行之前自動儲存，是否會出現警告訊息。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span>
<span data-ttu-id="b4a5b-245">預設值是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-245">The default value is `$true`.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="b4a5b-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="b4a5b-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="b4a5b-247">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-248">指定在不同的 PowerShell 索引標籤中開啟同一個檔案時，是否會出現警告訊息。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="b4a5b-249">如果設定為 `$true`，在多個索引標籤中開啟相同檔案會顯示下列訊息：「已在另一個 PowerShell 索引標籤中開啟這個檔案的副本。變更這個檔案將會影響所有已開啟的副本。」</span><span class="sxs-lookup"><span data-stu-id="b4a5b-249">If set to `$true`, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="b4a5b-250">預設值是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-250">The default value is `$true`.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="b4a5b-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="b4a5b-251">TokenColors</span></span>

<span data-ttu-id="b4a5b-252">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-253">在 Windows PowerShell ISE 指令碼窗格中，指定 IntelliSense 語彙基元的色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="b4a5b-254">這個屬性是一個字典物件，其中包含適用於指令碼窗格的語彙基元類型及色彩的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="b4a5b-255">若要變更主控台窗格中 IntelliSense 語彙基元的色彩，請參閱 [ConsoleTokenColors](#consoletokencolors)。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span>
<span data-ttu-id="b4a5b-256">若要將色彩重設為預設值，請參閱 [RestoreDefaultTokenColors](#restoredefaulttokencolors)。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span>
<span data-ttu-id="b4a5b-257">您可以為下列各項設定語彙基元色彩：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="b4a5b-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="b4a5b-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="b4a5b-259">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-260">指定您是否可以使用 Enter 鍵來選取主控台窗格中 IntelliSense 提供的選項。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="b4a5b-261">預設值是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-261">The default value is `$true`.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="b4a5b-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="b4a5b-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="b4a5b-263">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-264">指定您是否可以使用 Enter 鍵來選取指令碼窗格中 IntelliSense 提供的選項。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="b4a5b-265">預設值是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-265">The default value is `$true`.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="b4a5b-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="b4a5b-266">UseLocalHelp</span></span>

<span data-ttu-id="b4a5b-267">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-268">指定當您將游標放置於關鍵字中並按下 <kbd>F1</kbd> 時，是否要顯示本機安裝的說明或線上 TechNet Library 說明。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press <kbd>F1</kbd> with the cursor positioned in a keyword.</span></span> <span data-ttu-id="b4a5b-269">如果設定為 `$true`，則快顯視窗會顯示本機安裝的說明內容。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-269">If set to `$true`, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="b4a5b-270">您可以執行 `Update-Help` 命令來安裝說明檔。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="b4a5b-271">如果設定為 `$false`，則您的瀏覽器會開啟至 TechNet Library 中的頁面。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-271">If set to `$false`, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="b4a5b-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="b4a5b-273">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-274">針對出現在主控台窗格中的詳細資訊文字指定背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="b4a5b-275">它是 **System.Windows.Media.Color** 物件。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="b4a5b-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-276">VerboseForegroundColor</span></span>

<span data-ttu-id="b4a5b-277">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-278">針對出現在主控台窗格中的詳細資訊文字指定前景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="b4a5b-279">它是 **System.Windows.Media.Color** 物件。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="b4a5b-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-280">WarningBackgroundColor</span></span>

<span data-ttu-id="b4a5b-281">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-282">針對出現在主控台窗格中的警告文字指定背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="b4a5b-283">它是 **System.Windows.Media.Color** 物件。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="b4a5b-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="b4a5b-284">WarningForegroundColor</span></span>

<span data-ttu-id="b4a5b-285">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b4a5b-286">針對出現在輸出窗格中的警告文字指定前景色彩。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="b4a5b-287">它是 **System.Windows.Media.Color** 物件。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="b4a5b-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="b4a5b-288">XmlTokenColors</span></span>

<span data-ttu-id="b4a5b-289">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-290">指定一個字典物件，其中包含適用於 Windows PowerShell ISE 中所顯示之 XML 內容的語彙基元類型和色彩的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="b4a5b-291">您可以為下列各項設定語彙基元色彩：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="b4a5b-292">另請參閱 [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors)。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="b4a5b-293">Zoom</span><span class="sxs-lookup"><span data-stu-id="b4a5b-293">Zoom</span></span>

<span data-ttu-id="b4a5b-294">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="b4a5b-295">在主控台和指令碼窗格中指定文字的相對大小。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="b4a5b-296">預設值是 100。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-296">The default value is 100.</span></span>
<span data-ttu-id="b4a5b-297">值越小，在 Windows PowerShell ISE 中出現的文字就越小，而值越大，出現的文字就越大。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="b4a5b-298">值為整數，範圍可從 20 到 400。</span><span class="sxs-lookup"><span data-stu-id="b4a5b-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="b4a5b-299">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4a5b-299">See Also</span></span>

- [<span data-ttu-id="b4a5b-300">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="b4a5b-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b4a5b-301">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="b4a5b-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
