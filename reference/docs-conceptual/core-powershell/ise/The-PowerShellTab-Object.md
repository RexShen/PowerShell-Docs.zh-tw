---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "PowerShellTab 物件"
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: 15d9a7474e4c2cf2a9ff8edb88802106489cdba1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2017
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="99dda-103">PowerShellTab 物件</span><span class="sxs-lookup"><span data-stu-id="99dda-103">The PowerShellTab Object</span></span>
  <span data-ttu-id="99dda-104">**PowerShellTab** 物件代表 Windows PowerShell 執行階段環境。</span><span class="sxs-lookup"><span data-stu-id="99dda-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="99dda-105">方法</span><span class="sxs-lookup"><span data-stu-id="99dda-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="99dda-106">Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="99dda-106">Invoke\( Script \)</span></span>
  <span data-ttu-id="99dda-107">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="99dda-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="99dda-108">在 PowerShell 索引標籤中執行指定的指令碼。</span><span class="sxs-lookup"><span data-stu-id="99dda-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="99dda-109">此方法僅會在其他的 PowerShell 索引標籤上運作，而不會在此方法從中執行的 PowerShell 索引標籤上運作。</span><span class="sxs-lookup"><span data-stu-id="99dda-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="99dda-110">它不會傳回任何物件或值。</span><span class="sxs-lookup"><span data-stu-id="99dda-110">It does not return any object or value.</span></span> <span data-ttu-id="99dda-111">如果指令碼會修改任何變數，則那些變更將會保存在據以叫用命令的索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="99dda-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

 <span data-ttu-id="99dda-112">**指令碼** - System.Management.Automation.ScriptBlock 或字串：要執行的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="99dda-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="99dda-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="99dda-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>
  <span data-ttu-id="99dda-114">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="99dda-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="99dda-115">在 PowerShell 索引標籤中執行指定的指令碼。</span><span class="sxs-lookup"><span data-stu-id="99dda-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="99dda-116">此方法僅會在其他的 PowerShell 索引標籤上運作，而不會在此方法從中執行的 PowerShell 索引標籤上運作。</span><span class="sxs-lookup"><span data-stu-id="99dda-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="99dda-117">此指令碼區塊會執行，且從指令碼傳回的任何值會傳回到您從中叫用命令的環境。</span><span class="sxs-lookup"><span data-stu-id="99dda-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="99dda-118">如果命令執行的時間比 **millesecondsTimeout** 值指定的時間更長，命令就會失敗並發生例外狀況：「作業逾時。」</span><span class="sxs-lookup"><span data-stu-id="99dda-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

 <span data-ttu-id="99dda-119">**指令碼** - System.Management.Automation.ScriptBlock 或字串：要執行的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="99dda-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

 <span data-ttu-id="99dda-120">**\[useNewScope\]** -  預設為 **$true** 的選擇性布林值，若設定為 **$true**，就會建立一個在其中執行命令的新範圍。</span><span class="sxs-lookup"><span data-stu-id="99dda-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true** If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="99dda-121">它不會修改由命令指定之 PowerShell 索引標籤的執行階段環境。</span><span class="sxs-lookup"><span data-stu-id="99dda-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

 <span data-ttu-id="99dda-122">**\[millisecondsTimeout\]** - 選用的整數，預設為 **500**。</span><span class="sxs-lookup"><span data-stu-id="99dda-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="99dda-123">如果命令沒有在指定的時間內完成，則命令會產生 **TimeoutException** 並顯示「作業逾時」訊息。</span><span class="sxs-lookup"><span data-stu-id="99dda-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```
# create a new PowerShell tab and then switch back to the first
$PSise.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0]) 

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1',$false)
# You can switch to the other tab and type 'œ$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope) 
# and returns it through the pipeline to this tab to store in $a
$a=$psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z') 
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
measure-command {$psISE.PowerShellTabs[1].InvokeSynchronous("sleep 10",$false,5000)}

```

## <a name="properties"></a><span data-ttu-id="99dda-124">[內容]</span><span class="sxs-lookup"><span data-stu-id="99dda-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="99dda-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="99dda-125">AddOnsMenu</span></span>
  <span data-ttu-id="99dda-126">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="99dda-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="99dda-127">唯讀屬性，可取得 PowerShell 索引標籤的附加元件功能表。</span><span class="sxs-lookup"><span data-stu-id="99dda-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a><span data-ttu-id="99dda-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="99dda-128">CanInvoke</span></span>
  <span data-ttu-id="99dda-129">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="99dda-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="99dda-130">唯讀屬性，如果指令碼可透過 [Invoke( Script )](#invoke-script-) 方法叫用，則會傳回 **$true** 值。</span><span class="sxs-lookup"><span data-stu-id="99dda-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

```
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab. 
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psise.PowerShellTabs[1] 
$secondTab.CanInvoke 
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke

```

### <a name="consolepane"></a><span data-ttu-id="99dda-131">Consolepane</span><span class="sxs-lookup"><span data-stu-id="99dda-131">Consolepane</span></span>
  <span data-ttu-id="99dda-132">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="99dda-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="99dda-133">在 Windows PowerShell ISE 2.0 中，這名為 **CommandPane**。</span><span class="sxs-lookup"><span data-stu-id="99dda-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

 <span data-ttu-id="99dda-134">唯讀屬性，可取得主控台窗格 [editor](../ise/The-ISEEditor-Object.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="99dda-134">The read-only property that gets the Console pane [editor](../ise/The-ISEEditor-Object.md) object.</span></span>

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

### <a name="displayname"></a><span data-ttu-id="99dda-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="99dda-135">DisplayName</span></span>
  <span data-ttu-id="99dda-136">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="99dda-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="99dda-137">可讀寫屬性，可取得或設定顯示在 PowerShell 索引標籤上的文字。根據預設，索引標籤會命名為 "PowerShell #"，其中 # 代表數字。</span><span class="sxs-lookup"><span data-stu-id="99dda-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="expandedscript"></a><span data-ttu-id="99dda-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="99dda-138">ExpandedScript</span></span>
  <span data-ttu-id="99dda-139">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="99dda-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="99dda-140">可讀寫布林值屬性，可決定 [指令碼] 窗格為展開或隱藏。</span><span class="sxs-lookup"><span data-stu-id="99dda-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

### <a name="files"></a><span data-ttu-id="99dda-141">檔案</span><span class="sxs-lookup"><span data-stu-id="99dda-141">Files</span></span>
  <span data-ttu-id="99dda-142">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="99dda-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="99dda-143">唯讀屬性，可取得 PowerShell 索引標籤中開啟的[指令碼檔案集合](../ise/The-ISEFileCollection-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="99dda-143">The read-only property that gets the [collection of script files](../ise/The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="99dda-144">輸出</span><span class="sxs-lookup"><span data-stu-id="99dda-144">Output</span></span>
  <span data-ttu-id="99dda-145">此功能存在於 Windows PowerShell ISE 2.0，但在之後的 ISE 中已移除或重新命名。</span><span class="sxs-lookup"><span data-stu-id="99dda-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="99dda-146">在更新版本的 Windows PowerShell ISE 中，您可以使用 **ConsolePane** 物件達到相同的目的。</span><span class="sxs-lookup"><span data-stu-id="99dda-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

 <span data-ttu-id="99dda-147">唯讀屬性，可取得目前 [editor](../ise/The-ISEEditor-Object.md) 的 [輸出] 窗格。</span><span class="sxs-lookup"><span data-stu-id="99dda-147">The read-only property that gets the Output pane of the current [editor](../ise/The-ISEEditor-Object.md).</span></span>

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="99dda-148">Prompt</span><span class="sxs-lookup"><span data-stu-id="99dda-148">Prompt</span></span>
  <span data-ttu-id="99dda-149">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="99dda-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="99dda-150">唯讀屬性，可取得目前的提示文字。</span><span class="sxs-lookup"><span data-stu-id="99dda-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="99dda-151">注意：**Prompt** 功能可以透過使用者設定檔覆寫。</span><span class="sxs-lookup"><span data-stu-id="99dda-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="99dda-152">如果結果不是簡單字串，則此屬性不會傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="99dda-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="99dda-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="99dda-153">ShowCommands</span></span>
  <span data-ttu-id="99dda-154">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="99dda-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="99dda-155">可讀寫屬性，指出目前是否顯示 [命令] 窗格。</span><span class="sxs-lookup"><span data-stu-id="99dda-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

### <a name="statustext"></a><span data-ttu-id="99dda-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="99dda-156">StatusText</span></span>
  <span data-ttu-id="99dda-157">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="99dda-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="99dda-158">唯讀屬性，可取得 **PowerShellTab** 狀態文字。</span><span class="sxs-lookup"><span data-stu-id="99dda-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="99dda-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="99dda-159">HorizontalAddOnToolsPaneOpened</span></span>
  <span data-ttu-id="99dda-160">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="99dda-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="99dda-161">唯讀屬性，指出水平附加元件工具窗格目前是否開啟。</span><span class="sxs-lookup"><span data-stu-id="99dda-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="99dda-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="99dda-162">VerticalAddOnToolsPaneOpened</span></span>
  <span data-ttu-id="99dda-163">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="99dda-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="99dda-164">唯讀屬性，指出垂直附加元件工具窗格目前是否開啟。</span><span class="sxs-lookup"><span data-stu-id="99dda-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="99dda-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99dda-165">See Also</span></span>
- [<span data-ttu-id="99dda-166">PowerShellTabCollection 物件</span><span class="sxs-lookup"><span data-stu-id="99dda-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md) 
- [<span data-ttu-id="99dda-167">Windows PowerShell ISE 指令碼物件模型</span><span class="sxs-lookup"><span data-stu-id="99dda-167">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="99dda-168">Windows PowerShell ISE 物件模型參考</span><span class="sxs-lookup"><span data-stu-id="99dda-168">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="99dda-169">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="99dda-169">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
