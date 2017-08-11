---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEOptions 物件"
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 56bdd5999b46b6e29e762c2d9a2060cebe3a1299
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="40932-103">ISEOptions 物件</span><span class="sxs-lookup"><span data-stu-id="40932-103">The ISEOptions Object</span></span>
  <span data-ttu-id="40932-104">**ISEOptions** 物件代表適用於 Windows PowerShell ISE 的各種設定。</span><span class="sxs-lookup"><span data-stu-id="40932-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="40932-105">它是 **Microsoft.PowerShell.Host.ISE.ISEOptions** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="40932-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="40932-106">**ISEOptions** 物件提供下列方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="40932-106">The **ISEOptions** object provides the following methods and properties.</span></span>

 <span data-ttu-id="40932-107">**方法**</span><span class="sxs-lookup"><span data-stu-id="40932-107">**Methods**</span></span>

-   [<span data-ttu-id="40932-108">RestoreDefaultConsoleTokenColors()</span><span class="sxs-lookup"><span data-stu-id="40932-108">RestoreDefaultConsoleTokenColors()</span></span>](#rdctc)

-   [<span data-ttu-id="40932-109">RestoreDefaults()</span><span class="sxs-lookup"><span data-stu-id="40932-109">RestoreDefaults()</span></span>](#rd)

-   [<span data-ttu-id="40932-110">RestoreDefaultTokenColors()</span><span class="sxs-lookup"><span data-stu-id="40932-110">RestoreDefaultTokenColors()</span></span>](#rdtc)

-   [<span data-ttu-id="40932-111">RestoreDefaultXmlTokenColors()</span><span class="sxs-lookup"><span data-stu-id="40932-111">RestoreDefaultXmlTokenColors()</span></span>](#rdxtc)

 <span data-ttu-id="40932-112">**內容**</span><span class="sxs-lookup"><span data-stu-id="40932-112">**Properties**</span></span>

-   [<span data-ttu-id="40932-113">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="40932-113">AutoSaveMinuteInterval</span></span>](#asmi)

-   [<span data-ttu-id="40932-114">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-114">CommandPaneBackgroundColor</span></span>](#cpbc)

-   [<span data-ttu-id="40932-115">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="40932-115">CommandPaneUp</span></span>](#cpu)

-   [<span data-ttu-id="40932-116">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-116">ConsolePaneBackgroundColor</span></span>](#conpbc)

-   [<span data-ttu-id="40932-117">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-117">ConsolePaneForegroundColor</span></span>](#conpfc)

-   [<span data-ttu-id="40932-118">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-118">ConsolePaneTextBackgroundColor</span></span>](#conptbc)

-   [<span data-ttu-id="40932-119">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="40932-119">ConsoleTokenColors</span></span>](#contc)

-   [<span data-ttu-id="40932-120">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-120">DebugBackgroundColor</span></span>](#dbc)

-   [<span data-ttu-id="40932-121">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-121">DebugForegroundColor</span></span>](#dfc)

-   [<span data-ttu-id="40932-122">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="40932-122">DefaultOptions</span></span>](#do)

-   [<span data-ttu-id="40932-123">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-123">ErrorBackgroundColor</span></span>](#ebc)

-   [<span data-ttu-id="40932-124">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-124">ErrorForegroundColor</span></span>](#efc)

-   [<span data-ttu-id="40932-125">FontName</span><span class="sxs-lookup"><span data-stu-id="40932-125">FontName</span></span>](#fn)

-   [<span data-ttu-id="40932-126">FontSize</span><span class="sxs-lookup"><span data-stu-id="40932-126">FontSize</span></span>](#fs)

-   [<span data-ttu-id="40932-127">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="40932-127">IntellisenseTimeoutInSeconds</span></span>](#itis)

-   [<span data-ttu-id="40932-128">MruCount</span><span class="sxs-lookup"><span data-stu-id="40932-128">MruCount</span></span>](#mc)

-   [<span data-ttu-id="40932-129">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-129">OutputPaneBackgroundColor</span></span>](#opbc)

-   [<span data-ttu-id="40932-130">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-130">OutputPaneTextForegroundColor</span></span>](#optfc)

-   [<span data-ttu-id="40932-131">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-131">OutputPaneTextBackgroundColor</span></span>](#optbc)

-   [<span data-ttu-id="40932-132">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-132">ScriptPaneBackgroundColor</span></span>](#spbc)

-   [<span data-ttu-id="40932-133">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-133">ScriptPaneForegroundColor</span></span>](#spfc)

-   [<span data-ttu-id="40932-134">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="40932-134">SelectedScriptPaneState</span></span>](#ssps)

-   [<span data-ttu-id="40932-135">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="40932-135">ShowDefaultSnippets</span></span>](#sds)

-   [<span data-ttu-id="40932-136">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="40932-136">ShowIntellisenseInConsolePane</span></span>](#siicp)

-   [<span data-ttu-id="40932-137">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="40932-137">ShowIntellisenseInScriptPane</span></span>](#siisp)

-   [<span data-ttu-id="40932-138">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="40932-138">ShowLineNumbers</span></span>](#sln)

-   [<span data-ttu-id="40932-139">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="40932-139">ShowOutlining</span></span>](#so)

-   [<span data-ttu-id="40932-140">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="40932-140">ShowToolBar</span></span>](#stb)

-   [<span data-ttu-id="40932-141">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="40932-141">ShowWarningBeforeSavingOnRun</span></span>](#swbsor)

-   [<span data-ttu-id="40932-142">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="40932-142">ShowWarningForDuplicateFiles</span></span>](#swfdf)

-   [<span data-ttu-id="40932-143">TokenColors</span><span class="sxs-lookup"><span data-stu-id="40932-143">TokenColors</span></span>](#tc)

-   [<span data-ttu-id="40932-144">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="40932-144">UseEnterToSelectInConsolePaneIntellisense</span></span>](#uetsicpi)

-   [<span data-ttu-id="40932-145">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="40932-145">UseEnterToSelectInScriptPaneIntellisense</span></span>](#uetsispi)

-   [<span data-ttu-id="40932-146">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="40932-146">UseLocalHelp</span></span>](#ulh)

-   [<span data-ttu-id="40932-147">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-147">VerboseBackgroundColor</span></span>](#vbc)

-   [<span data-ttu-id="40932-148">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-148">VerboseForegroundColor</span></span>](#vfc)

-   [<span data-ttu-id="40932-149">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-149">WarningBackgroundColor</span></span>](#wbc)

-   [<span data-ttu-id="40932-150">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-150">WarningForegroundColor</span></span>](#wfc)

-   [<span data-ttu-id="40932-151">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="40932-151">XmlTokenColors</span></span>](#xtc)

-   [<span data-ttu-id="40932-152">Zoom</span><span class="sxs-lookup"><span data-stu-id="40932-152">Zoom</span></span>](#z)

## <a name="methods"></a><span data-ttu-id="40932-153">方法</span><span class="sxs-lookup"><span data-stu-id="40932-153">Methods</span></span>

###  <span data-ttu-id="40932-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="40932-154"><a name="rdctc"></a> RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="40932-155">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-156">還原主控台窗格中語彙基元色彩的預設值。</span><span class="sxs-lookup"><span data-stu-id="40932-156">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

###  <span data-ttu-id="40932-157"><a name="rd"></a> RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="40932-157"><a name="rd"></a> RestoreDefaults\(\)</span></span>
  <span data-ttu-id="40932-158">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-159">還原主控台窗格中所有選項設定的預設值。</span><span class="sxs-lookup"><span data-stu-id="40932-159">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="40932-160">它也會重設各種警告訊息的行為，提供標準的核取方塊來防止再次顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="40932-160">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

###  <span data-ttu-id="40932-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="40932-161"><a name="rdtc"></a> RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="40932-162">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-163">還原指令碼窗格中語彙基元色彩的預設值。</span><span class="sxs-lookup"><span data-stu-id="40932-163">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

###  <span data-ttu-id="40932-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="40932-164"><a name="rdxtc"></a> RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="40932-165">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-165">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-166">針對顯示於 Windows PowerShell ISE 中的 XML 項目，還原語彙基元色彩的預設值。</span><span class="sxs-lookup"><span data-stu-id="40932-166">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="40932-167">另請參閱 [XmlTokenColors](#xtc)。</span><span class="sxs-lookup"><span data-stu-id="40932-167">Also see [XmlTokenColors](#xtc).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="40932-168">[內容]</span><span class="sxs-lookup"><span data-stu-id="40932-168">Properties</span></span>

###  <span data-ttu-id="40932-169"><a name="asmi"></a> AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="40932-169"><a name="asmi"></a> AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="40932-170">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-170">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-171">指定由 Windows PowerShell ISE 自動執行儲存檔案作業之間的分鐘數。</span><span class="sxs-lookup"><span data-stu-id="40932-171">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="40932-172">預設值是 2 分鐘。</span><span class="sxs-lookup"><span data-stu-id="40932-172">The default value is 2 minutes.</span></span> <span data-ttu-id="40932-173">值為整數。</span><span class="sxs-lookup"><span data-stu-id="40932-173">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

###  <span data-ttu-id="40932-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-174"><a name="cpbc"></a> CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="40932-175">此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。</span><span class="sxs-lookup"><span data-stu-id="40932-175">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="40932-176">如需更新版本，請參閱 [ConsolePaneBackgroundColor](#conpbc)。</span><span class="sxs-lookup"><span data-stu-id="40932-176">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="40932-177">指定命令窗格的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-177">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="40932-178">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="40932-178">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

###  <span data-ttu-id="40932-179"><a name="cpu"></a> CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="40932-179"><a name="cpu"></a> CommandPaneUp</span></span>
  <span data-ttu-id="40932-180">此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。</span><span class="sxs-lookup"><span data-stu-id="40932-180">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="40932-181">指定命令窗格是否要位於輸出窗格上方。</span><span class="sxs-lookup"><span data-stu-id="40932-181">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

###  <span data-ttu-id="40932-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-182"><a name="conpbc"></a> ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="40932-183">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-183">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-184">指定主控台窗格的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-184">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="40932-185">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="40932-185">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

###  <span data-ttu-id="40932-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-186"><a name="conpfc"></a> ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="40932-187">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-188">指定主控台窗格中文字的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-188">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

###  <span data-ttu-id="40932-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-189"><a name="conptbc"></a> ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="40932-190">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-190">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-191">指定主控台窗格中文字的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-191">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="40932-192"><a name="contc"></a> ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="40932-192"><a name="contc"></a> ConsoleTokenColors</span></span>
  <span data-ttu-id="40932-193">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-193">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-194">在 Windows PowerShell ISE 主控台窗格中，指定 IntelliSense 語彙基元的色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-194">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="40932-195">這個屬性是一個字典物件，其中包含適用於主控台窗格的語彙基元類型及色彩的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="40932-195">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="40932-196">若要變更指令碼窗格中 IntelliSense 語彙基元的色彩，請參閱 [TokenColors](#tc)。</span><span class="sxs-lookup"><span data-stu-id="40932-196">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tc).</span></span> <span data-ttu-id="40932-197">若要將色彩重設為預設值，請參閱 [RestoreDefaultConsoleTokenColors()](#rdctc)。</span><span class="sxs-lookup"><span data-stu-id="40932-197">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors()](#rdctc).</span></span> <span data-ttu-id="40932-198">您可以為下列各項設定語彙基元色彩：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。</span><span class="sxs-lookup"><span data-stu-id="40932-198">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="40932-199"><a name="dbc"></a> DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-199"><a name="dbc"></a> DebugBackgroundColor</span></span>
  <span data-ttu-id="40932-200">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-200">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-201">針對出現在主控台窗格中的偵錯文字指定背景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-201">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="40932-202">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="40932-202">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="40932-203"><a name="dfc"></a> DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-203"><a name="dfc"></a> DebugForegroundColor</span></span>
  <span data-ttu-id="40932-204">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-204">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-205">針對出現在主控台窗格中的偵錯文字指定前景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-205">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="40932-206">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="40932-206">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

###  <span data-ttu-id="40932-207"><a name="do"></a> DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="40932-207"><a name="do"></a> DefaultOptions</span></span>
  <span data-ttu-id="40932-208">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-208">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-209">一個屬性集合，可指定使用重設方法時要使用的預設值。</span><span class="sxs-lookup"><span data-stu-id="40932-209">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

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

###  <span data-ttu-id="40932-210"><a name="ebc"></a> ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-210"><a name="ebc"></a> ErrorBackgroundColor</span></span>
  <span data-ttu-id="40932-211">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-211">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-212">針對出現在主控台窗格中的錯誤文字指定背景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-212">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="40932-213">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="40932-213">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

###  <span data-ttu-id="40932-214"><a name="efc"></a> ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-214"><a name="efc"></a> ErrorForegroundColor</span></span>
  <span data-ttu-id="40932-215">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-215">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-216">針對出現在主控台窗格中的錯誤文字指定前景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-216">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="40932-217">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="40932-217">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

###  <span data-ttu-id="40932-218"><a name="fn"></a> FontName</span><span class="sxs-lookup"><span data-stu-id="40932-218"><a name="fn"></a> FontName</span></span>
  <span data-ttu-id="40932-219">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-219">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-220">指定目前在指令碼窗格和主控台窗格中使用的字型名稱。</span><span class="sxs-lookup"><span data-stu-id="40932-220">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

###  <span data-ttu-id="40932-221"><a name="fs"></a> FontSize</span><span class="sxs-lookup"><span data-stu-id="40932-221"><a name="fs"></a> FontSize</span></span>
  <span data-ttu-id="40932-222">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-222">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-223">以整數形式指定字型大小。</span><span class="sxs-lookup"><span data-stu-id="40932-223">Specifies the font size as an integer.</span></span> <span data-ttu-id="40932-224">其會用於指令碼窗格、命令窗格及輸出窗格中。</span><span class="sxs-lookup"><span data-stu-id="40932-224">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="40932-225">有效值範圍是 8 到 32。</span><span class="sxs-lookup"><span data-stu-id="40932-225">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

###  <span data-ttu-id="40932-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="40932-226"><a name="itis"></a> IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="40932-227">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-227">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-228">指定 IntelliSense 用來解析目前輸入文字的秒數。</span><span class="sxs-lookup"><span data-stu-id="40932-228">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="40932-229">經過此秒數之後，IntelliSense 即會逾時，並可讓您繼續輸入。</span><span class="sxs-lookup"><span data-stu-id="40932-229">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="40932-230">預設值為 3 秒。</span><span class="sxs-lookup"><span data-stu-id="40932-230">The default value is 3 seconds.</span></span> <span data-ttu-id="40932-231">值為整數。</span><span class="sxs-lookup"><span data-stu-id="40932-231">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

###  <span data-ttu-id="40932-232"><a name="mc"></a> MruCount</span><span class="sxs-lookup"><span data-stu-id="40932-232"><a name="mc"></a> MruCount</span></span>
  <span data-ttu-id="40932-233">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-233">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-234">指定 Windows PowerShell ISE 所追蹤之最近開啟的檔案個數，並顯示於 [開啟舊檔] 功能表底部。</span><span class="sxs-lookup"><span data-stu-id="40932-234">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="40932-235">預設值是 10。</span><span class="sxs-lookup"><span data-stu-id="40932-235">The default value is 10.</span></span> <span data-ttu-id="40932-236">值為整數。</span><span class="sxs-lookup"><span data-stu-id="40932-236">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

###  <span data-ttu-id="40932-237"><a name="opbc"></a> OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-237"><a name="opbc"></a> OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="40932-238">此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。</span><span class="sxs-lookup"><span data-stu-id="40932-238">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="40932-239">如需更新版本，請參閱 [ConsolePaneBackgroundColor](#conpbc)。</span><span class="sxs-lookup"><span data-stu-id="40932-239">For later versions, see [ConsolePaneBackgroundColor](#conpbc).</span></span>

 <span data-ttu-id="40932-240">讀取/寫入屬性，可取得或設定輸出窗格本身的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-240">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="40932-241">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="40932-241">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

###  <span data-ttu-id="40932-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-242"><a name="optfc"></a> OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="40932-243">此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。</span><span class="sxs-lookup"><span data-stu-id="40932-243">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="40932-244">如需更新版本，請參閱 [ConsolePaneForegroundColor](#conpfc)。</span><span class="sxs-lookup"><span data-stu-id="40932-244">For later versions, see [ConsolePaneForegroundColor](#conpfc).</span></span>

 <span data-ttu-id="40932-245">讀取/寫入屬性，可在 Windows PowerShell ISE 2.0 中變更輸出窗格中文字的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-245">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

###  <span data-ttu-id="40932-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-246"><a name="optbc"></a> OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="40932-247">此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。</span><span class="sxs-lookup"><span data-stu-id="40932-247">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="40932-248">如需更新版本，請參閱 [ConsolePaneTextBackgroundColor](#conptbc)。</span><span class="sxs-lookup"><span data-stu-id="40932-248">For later versions, see [ConsolePaneTextBackgroundColor](#conptbc).</span></span>

 <span data-ttu-id="40932-249">讀取/寫入屬性，可變更輸出窗格中文字的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-249">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

###  <span data-ttu-id="40932-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-250"><a name="spbc"></a> ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="40932-251">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-251">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-252">讀取/寫入屬性，可取得或設定檔案的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-252">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="40932-253">它是 **System.Windows.Media.Color** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="40932-253">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = ”yellow”

```

###  <span data-ttu-id="40932-254"><a name="spfc"></a> ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-254"><a name="spfc"></a> ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="40932-255">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-255">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-256">讀取/寫入屬性，可取得或設定指令碼窗格中非指令碼檔案的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-256">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="40932-257">若要設定指令碼檔案的前景色彩，請使用 [TokenColors](The-ISEOptions-Object.md#tc) 屬性。</span><span class="sxs-lookup"><span data-stu-id="40932-257">To set the foreground color for script files, use the [TokenColors](The-ISEOptions-Object.md#tc) property.</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

###  <span data-ttu-id="40932-258"><a name="ssps"></a> SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="40932-258"><a name="ssps"></a> SelectedScriptPaneState</span></span>
  <span data-ttu-id="40932-259">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-259">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-260">讀取/寫入屬性，可在顯示器上取得或設定指令碼窗格的位置。</span><span class="sxs-lookup"><span data-stu-id="40932-260">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="40932-261">字串可以是 "Maximized"、"Top" 或 "Right"。</span><span class="sxs-lookup"><span data-stu-id="40932-261">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

###  <span data-ttu-id="40932-262"><a name="sds"></a> ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="40932-262"><a name="sds"></a> ShowDefaultSnippets</span></span>
  <span data-ttu-id="40932-263">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-264">指定程式碼片段的 **CTRL+J** 清單是否包括隨附於 Windows PowerShell 的入門集。</span><span class="sxs-lookup"><span data-stu-id="40932-264">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="40932-265">設定為 **$false** 時，只有使用者定義的程式碼片段會出現在 **CTRL+J** 清單中。</span><span class="sxs-lookup"><span data-stu-id="40932-265">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="40932-266">預設值為 **$true**。</span><span class="sxs-lookup"><span data-stu-id="40932-266">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

###  <span data-ttu-id="40932-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="40932-267"><a name="siicp"></a> ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="40932-268">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-268">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-269">指定 IntelliSense 是否會在主控台窗格中提供語法、參數和值的建議。</span><span class="sxs-lookup"><span data-stu-id="40932-269">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="40932-270">預設值為 **$true**。</span><span class="sxs-lookup"><span data-stu-id="40932-270">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

###  <span data-ttu-id="40932-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="40932-271"><a name="siisp"></a> ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="40932-272">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-272">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-273">指定 IntelliSense 是否會在指令碼窗格中提供語法、參數和值的建議。</span><span class="sxs-lookup"><span data-stu-id="40932-273">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="40932-274">預設值為 **$true**。</span><span class="sxs-lookup"><span data-stu-id="40932-274">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

###  <span data-ttu-id="40932-275"><a name="sln"></a> ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="40932-275"><a name="sln"></a> ShowLineNumbers</span></span>
  <span data-ttu-id="40932-276">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-276">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-277">指定指令碼窗格是否會在左邊界中顯示行號。</span><span class="sxs-lookup"><span data-stu-id="40932-277">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="40932-278">預設值為 **$true**。</span><span class="sxs-lookup"><span data-stu-id="40932-278">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

###  <span data-ttu-id="40932-279"><a name="so"></a> ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="40932-279"><a name="so"></a> ShowOutlining</span></span>
  <span data-ttu-id="40932-280">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-280">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-281">指定指令碼窗格是否會在左邊界中的程式碼區段旁邊顯示可展開和可摺疊的括弧。</span><span class="sxs-lookup"><span data-stu-id="40932-281">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="40932-282">如果顯示，您可以按一下文字區塊旁邊的減號 \(-\) 圖示來摺疊它，或按一下加號 \(+\) 圖示來展開文字區塊。</span><span class="sxs-lookup"><span data-stu-id="40932-282">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="40932-283">預設值為 **$true**。</span><span class="sxs-lookup"><span data-stu-id="40932-283">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

###  <span data-ttu-id="40932-284"><a name="stb"></a> ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="40932-284"><a name="stb"></a> ShowToolBar</span></span>
  <span data-ttu-id="40932-285">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-286">指定 ISE 工具列是否會出現在 Windows PowerShell ISE 視窗的頂端。</span><span class="sxs-lookup"><span data-stu-id="40932-286">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="40932-287">預設值為 **$true**。</span><span class="sxs-lookup"><span data-stu-id="40932-287">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

###  <span data-ttu-id="40932-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="40932-288"><a name="swbsor"></a> ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="40932-289">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-289">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-290">指定若指令碼在執行之前自動儲存，是否會出現警告訊息。</span><span class="sxs-lookup"><span data-stu-id="40932-290">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="40932-291">預設值為 **$true**。</span><span class="sxs-lookup"><span data-stu-id="40932-291">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

###  <span data-ttu-id="40932-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="40932-292"><a name="swfdf"></a> ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="40932-293">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-293">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-294">指定在不同的 PowerShell 索引標籤中開啟同一個檔案時，是否會出現警告訊息。</span><span class="sxs-lookup"><span data-stu-id="40932-294">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="40932-295">如果設定為 **$true**，則在多個索引標籤中開啟同一個檔案，會顯示此訊息：「已在另一個 Windows PowerShell 索引標籤中開啟這個檔案的副本。</span><span class="sxs-lookup"><span data-stu-id="40932-295">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab.</span></span> <span data-ttu-id="40932-296">變更這個檔案將會影響所有已開啟的副本。」</span><span class="sxs-lookup"><span data-stu-id="40932-296">Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="40932-297">預設值為 **$true**。</span><span class="sxs-lookup"><span data-stu-id="40932-297">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

###  <span data-ttu-id="40932-298"><a name="tc"></a> TokenColors</span><span class="sxs-lookup"><span data-stu-id="40932-298"><a name="tc"></a> TokenColors</span></span>
  <span data-ttu-id="40932-299">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-299">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-300">在 Windows PowerShell ISE 指令碼窗格中，指定 IntelliSense 語彙基元的色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-300">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="40932-301">這個屬性是一個字典物件，其中包含適用於指令碼窗格的語彙基元類型及色彩的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="40932-301">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="40932-302">若要變更主控台窗格中 IntelliSense 語彙基元的色彩，請參閱 [ConsoleTokenColors](#contc)。</span><span class="sxs-lookup"><span data-stu-id="40932-302">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#contc).</span></span> <span data-ttu-id="40932-303">若要將色彩重設為預設值，請參閱 [RestoreDefaultTokenColors()](#rdtc)。</span><span class="sxs-lookup"><span data-stu-id="40932-303">To reset the colors to the default values, see [RestoreDefaultTokenColors()](#rdtc).</span></span> <span data-ttu-id="40932-304">您可以為下列各項設定語彙基元色彩：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。</span><span class="sxs-lookup"><span data-stu-id="40932-304">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

###  <span data-ttu-id="40932-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="40932-305"><a name="uetsicpi"></a> UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="40932-306">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-306">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-307">指定您是否可以使用 Enter 鍵來選取主控台窗格中 IntelliSense 提供的選項。</span><span class="sxs-lookup"><span data-stu-id="40932-307">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="40932-308">預設值為 **$true**。</span><span class="sxs-lookup"><span data-stu-id="40932-308">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

###  <span data-ttu-id="40932-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="40932-309"><a name="uetsispi"></a> UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="40932-310">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-310">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-311">指定您是否可以使用 Enter 鍵來選取指令碼窗格中 IntelliSense 提供的選項。</span><span class="sxs-lookup"><span data-stu-id="40932-311">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="40932-312">預設值為 **$true**。</span><span class="sxs-lookup"><span data-stu-id="40932-312">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

###  <span data-ttu-id="40932-313"><a name="ulh"></a> UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="40932-313"><a name="ulh"></a> UseLocalHelp</span></span>
  <span data-ttu-id="40932-314">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-314">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-315">指定當您將游標放置於關鍵字中並按下 F1 時，是否要顯示本機安裝的說明或線上 TechNet Library 說明。</span><span class="sxs-lookup"><span data-stu-id="40932-315">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="40932-316">如果設定為 **$true**，則快顯視窗會顯示本機安裝的說明內容。</span><span class="sxs-lookup"><span data-stu-id="40932-316">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="40932-317">您可以執行 `Update-Help` 命令來安裝說明檔。</span><span class="sxs-lookup"><span data-stu-id="40932-317">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="40932-318">如果設定為 **$false**，則您的瀏覽器會開啟至 TechNet Library 中的頁面。</span><span class="sxs-lookup"><span data-stu-id="40932-318">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

###  <span data-ttu-id="40932-319"><a name="vbc"></a> VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-319"><a name="vbc"></a> VerboseBackgroundColor</span></span>
  <span data-ttu-id="40932-320">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-320">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-321">針對出現在主控台窗格中的詳細資訊文字指定背景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-321">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="40932-322">它是 **System.Windows.Media.Color** 物件。</span><span class="sxs-lookup"><span data-stu-id="40932-322">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="40932-323"><a name="vfc"></a> VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-323"><a name="vfc"></a> VerboseForegroundColor</span></span>
  <span data-ttu-id="40932-324">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-324">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-325">針對出現在主控台窗格中的詳細資訊文字指定前景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-325">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="40932-326">它是 **System.Windows.Media.Color** 物件。</span><span class="sxs-lookup"><span data-stu-id="40932-326">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor =”yellow”
```

###  <span data-ttu-id="40932-327"><a name="wbc"></a> WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-327"><a name="wbc"></a> WarningBackgroundColor</span></span>
  <span data-ttu-id="40932-328">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-328">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-329">針對出現在主控台窗格中的警告文字指定背景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-329">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="40932-330">它是 **System.Windows.Media.Color** 物件。</span><span class="sxs-lookup"><span data-stu-id="40932-330">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

###  <span data-ttu-id="40932-331"><a name="wfc"></a> WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="40932-331"><a name="wfc"></a> WarningForegroundColor</span></span>
  <span data-ttu-id="40932-332">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="40932-332">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="40932-333">針對出現在輸出窗格中的警告文字指定前景色彩。</span><span class="sxs-lookup"><span data-stu-id="40932-333">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="40932-334">它是 **System.Windows.Media.Color** 物件。</span><span class="sxs-lookup"><span data-stu-id="40932-334">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor =”yellow”
```

###  <span data-ttu-id="40932-335"><a name="xtc"></a> XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="40932-335"><a name="xtc"></a> XmlTokenColors</span></span>
  <span data-ttu-id="40932-336">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-336">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-337">指定一個字典物件，其中包含適用於 Windows PowerShell ISE 中所顯示之 XML 內容的語彙基元類型和色彩的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="40932-337">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="40932-338">您可以為下列各項設定語彙基元色彩：Attribute、Command、CommandArgument、CommandParameter、Comment、GroupEnd、GroupStart、Keyword、LineContinuation、LoopLabel、Member、NewLine、Number、Operator、Position、StatementSeparator、String、Type、Unknown、Variable。</span><span class="sxs-lookup"><span data-stu-id="40932-338">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="40932-339">另請參閱 [RestoreDefaultXmlTokenColors()](#rdxtc)。</span><span class="sxs-lookup"><span data-stu-id="40932-339">Also see [RestoreDefaultXmlTokenColors()](#rdxtc).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

###  <span data-ttu-id="40932-340"><a name="z"></a> Zoom</span><span class="sxs-lookup"><span data-stu-id="40932-340"><a name="z"></a> Zoom</span></span>
  <span data-ttu-id="40932-341">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="40932-341">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="40932-342">在主控台和指令碼窗格中指定文字的相對大小。</span><span class="sxs-lookup"><span data-stu-id="40932-342">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="40932-343">預設值是 100。</span><span class="sxs-lookup"><span data-stu-id="40932-343">The default value is 100.</span></span> <span data-ttu-id="40932-344">值越小，在 Windows PowerShell ISE 中出現的文字就越小，而值越大，出現的文字就越大。</span><span class="sxs-lookup"><span data-stu-id="40932-344">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="40932-345">值為整數，範圍可從 20 到 400。</span><span class="sxs-lookup"><span data-stu-id="40932-345">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="40932-346">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40932-346">See Also</span></span>
- [<span data-ttu-id="40932-347">Windows PowerShell ISE 指令碼物件模型</span><span class="sxs-lookup"><span data-stu-id="40932-347">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="40932-348">Windows PowerShell ISE 物件模型參考</span><span class="sxs-lookup"><span data-stu-id="40932-348">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

