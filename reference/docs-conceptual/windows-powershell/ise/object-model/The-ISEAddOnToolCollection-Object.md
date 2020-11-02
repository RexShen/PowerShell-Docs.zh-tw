---
ms.date: 12/31/2019
title: ISEAddOnToolCollection 物件
description: ISEAddOnToolCollection 物件是 **ISEAddOnTool** 物件的集合。
ms.openlocfilehash: ba08ffd82a7ff2fa469540a5ea542abee8d4dc82
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658319"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="e43bd-103">ISEAddOnToolCollection 物件</span><span class="sxs-lookup"><span data-stu-id="e43bd-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="e43bd-104">**ISEAddOnToolCollection** 物件是 **ISEAddOnTool** 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="e43bd-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="e43bd-105">例如，`$psISE.CurrentPowerShellTab.VerticalAddOnTools` 物件。</span><span class="sxs-lookup"><span data-stu-id="e43bd-105">An example is the `$psISE.CurrentPowerShellTab.VerticalAddOnTools` object.</span></span>

## <a name="methods"></a><span data-ttu-id="e43bd-106">方法</span><span class="sxs-lookup"><span data-stu-id="e43bd-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="e43bd-107">Add\( Name, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="e43bd-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="e43bd-108">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="e43bd-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e43bd-109">將新的附加元件工具加入到集合。</span><span class="sxs-lookup"><span data-stu-id="e43bd-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="e43bd-110">它會傳回新加入的附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="e43bd-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="e43bd-111">執行此命令之前，您必須在本機電腦上安裝附加元件工具並載入組件。</span><span class="sxs-lookup"><span data-stu-id="e43bd-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="e43bd-112">**Name** - 字串：指定要新增至 Windows PowerShell ISE 的附加元件工具顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="e43bd-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="e43bd-113">**ControlType** - 類型：指定新增的控制項。</span><span class="sxs-lookup"><span data-stu-id="e43bd-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="e43bd-114">**\[IsVisible\]** - 選用的布林值：如果設定為 `$true`，附加元件工具會立即顯示在相關聯的工具窗格中。</span><span class="sxs-lookup"><span data-stu-id="e43bd-114">**\[IsVisible\]** - optional Boolean If set to `$true`, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="e43bd-115">Remove\( Item \)</span><span class="sxs-lookup"><span data-stu-id="e43bd-115">Remove\( Item \)</span></span>

<span data-ttu-id="e43bd-116">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="e43bd-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e43bd-117">從集合中移除指定的附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="e43bd-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="e43bd-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool：指定要從 Windows PowerShell ISE 移除的物件。</span><span class="sxs-lookup"><span data-stu-id="e43bd-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="e43bd-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="e43bd-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="e43bd-120">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="e43bd-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e43bd-121">選取 **psTab** 參數指定的 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e43bd-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="e43bd-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab：要選取的 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e43bd-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="e43bd-123">Remove\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="e43bd-123">Remove\( psTab \)</span></span>

<span data-ttu-id="e43bd-124">在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。</span><span class="sxs-lookup"><span data-stu-id="e43bd-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="e43bd-125">移除 **psTab** 參數指定的 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e43bd-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="e43bd-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab：要移除的 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e43bd-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="e43bd-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e43bd-127">See Also</span></span>

- [<span data-ttu-id="e43bd-128">PowerShellTab 物件</span><span class="sxs-lookup"><span data-stu-id="e43bd-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="e43bd-129">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="e43bd-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="e43bd-130">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="e43bd-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
