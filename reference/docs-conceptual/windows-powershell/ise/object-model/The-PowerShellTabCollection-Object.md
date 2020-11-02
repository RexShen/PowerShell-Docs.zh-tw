---
ms.date: 06/05/2017
title: PowerShellTabCollection 物件
description: PowerShellTab 集合物件是 PowerShellTab 物件的集合。 每個 PowerShellTab 物件功能都可做為個別的執行階段環境。
ms.openlocfilehash: 60f8001f096b50bd8433a5685f1f70a350f07f61
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658266"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="d8a53-104">PowerShellTabCollection 物件</span><span class="sxs-lookup"><span data-stu-id="d8a53-104">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="d8a53-105">**PowerShellTab** 集合物件是 **PowerShellTab** 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="d8a53-105">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="d8a53-106">每個 **PowerShellTab** 物件功能都可做為個別的執行階段環境。</span><span class="sxs-lookup"><span data-stu-id="d8a53-106">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="d8a53-107">它是 Microsoft.PowerShell.Host.ISE.PowerShellTabs 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d8a53-107">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="d8a53-108">例如，`$psISE.PowerShellTabs` 物件。</span><span class="sxs-lookup"><span data-stu-id="d8a53-108">An example is the `$psISE.PowerShellTabs` object.</span></span>

## <a name="methods"></a><span data-ttu-id="d8a53-109">方法</span><span class="sxs-lookup"><span data-stu-id="d8a53-109">Methods</span></span>

### <a name="add"></a><span data-ttu-id="d8a53-110">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="d8a53-110">Add\(\)</span></span>

<span data-ttu-id="d8a53-111">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="d8a53-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d8a53-112">將新的 PowerShell 索引標籤新增到集合。</span><span class="sxs-lookup"><span data-stu-id="d8a53-112">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="d8a53-113">它會傳回新加入的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d8a53-113">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="d8a53-114">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="d8a53-114">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="d8a53-115">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="d8a53-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d8a53-116">移除 **psTab** 參數指定的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d8a53-116">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="d8a53-117">**psTab** 要移除的 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d8a53-117">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="d8a53-118">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="d8a53-118">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="d8a53-119">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="d8a53-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d8a53-120">選取 **psTab** 參數指定的 PowerShell 索引標籤，使其成為目前作用中的 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d8a53-120">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="d8a53-121">**psTab** 要選取的 PowerShell 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d8a53-121">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="d8a53-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8a53-122">See Also</span></span>

- [<span data-ttu-id="d8a53-123">PowerShellTab 物件</span><span class="sxs-lookup"><span data-stu-id="d8a53-123">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="d8a53-124">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="d8a53-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d8a53-125">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="d8a53-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
