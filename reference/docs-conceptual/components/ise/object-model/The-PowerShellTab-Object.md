---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShellTab 物件
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: 577e2aaaddf3071801816d9ae91dbf0006dd5072
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057667"
---
# <a name="the-powershelltab-object"></a>PowerShellTab 物件

**PowerShellTab** 物件代表 Windows PowerShell 執行階段環境。

## <a name="methods"></a>Methods

### <a name="invoke-script-"></a>Invoke\( Script \)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

在 PowerShell 索引標籤中執行指定的指令碼。

> [!NOTE]
> 此方法僅會在其他的 PowerShell 索引標籤上運作，而不會在此方法從中執行的 PowerShell 索引標籤上運作。 它不會傳回任何物件或值。 如果指令碼會修改任何變數，則那些變更將會保存在據以叫用命令的索引標籤上。

**指令碼** - System.Management.Automation.ScriptBlock 或字串：要執行的指令碼區塊。

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

在 PowerShell 索引標籤中執行指定的指令碼。

> [!NOTE]
> 此方法僅會在其他的 PowerShell 索引標籤上運作，而不會在此方法從中執行的 PowerShell 索引標籤上運作。 此指令碼區塊會執行，且從指令碼傳回的任何值會傳回到您從中叫用命令的環境。 如果命令執行的時間比 **millesecondsTimeout** 值指定的時間更長，則該命令會失敗並發生例外狀況：「作業逾時」。

**指令碼** - System.Management.Automation.ScriptBlock 或字串：要執行的指令碼區塊。

**\[useNewScope\]** -  預設為 **$true** 的選擇性布林值，若設定為 **$true**，就會建立一個在其中執行命令的新範圍。 它不會修改由命令指定之 PowerShell 索引標籤的執行階段環境。

**\[millisecondsTimeout\]** - 選用的整數，預設為 **500**。
如果命令沒有在指定的時間內完成，則命令會產生 **TimeoutException** 並顯示「作業逾時」訊息。

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a>Properties

### <a name="addonsmenu"></a>AddOnsMenu

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得 PowerShell 索引標籤的附加元件功能表。

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a>CanInvoke

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，如果指令碼可透過 [Invoke( Script )](#invoke-script-) 方法叫用，則會傳回 **$true** 值。

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a>Consolepane

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。  在 Windows PowerShell ISE 2.0 中，這名為 **CommandPane**。

唯讀屬性，可取得主控台窗格 [editor](The-ISEEditor-Object.md) 物件。

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>DisplayName

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

可讀寫屬性，可取得或設定顯示在 PowerShell 索引標籤上的文字。根據預設，索引標籤會命名為 "PowerShell #"，其中 # 代表數字。

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

可讀寫布林值屬性，可決定 [指令碼] 窗格為展開或隱藏。

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>檔案

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得 PowerShell 索引標籤中開啟的[指令碼檔案集合](The-ISEFileCollection-Object.md)。

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>輸出

此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。  在更新版本的 Windows PowerShell ISE 中，您可以使用 **ConsolePane** 物件達到相同的目的。

唯讀屬性，可取得目前 [editor](The-ISEEditor-Object.md) 的 [輸出] 窗格。

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Prompt

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得目前的提示文字。 注意：**Prompt** 功能可以透過使用者設定檔覆寫。 如果結果不是簡單字串，則此屬性不會傳回任何項目。

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

可讀寫屬性，指出目前是否顯示 [命令] 窗格。

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a>StatusText

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得 **PowerShellTab** 狀態文字。

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

唯讀屬性，指出水平附加元件工具窗格目前是否開啟。

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

唯讀屬性，指出垂直附加元件工具窗格目前是否開啟。

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>另請參閱

- [PowerShellTabCollection 物件](The-PowerShellTabCollection-Object.md)
- [Windows PowerShell ISE 指令碼物件模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)