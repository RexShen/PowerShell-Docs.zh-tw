---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEMenuItem 物件"
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 33de866d706ec2b0894c5bfe49e07fee142b95c0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="36782-103">ISEMenuItem 物件</span><span class="sxs-lookup"><span data-stu-id="36782-103">The ISEMenuItem Object</span></span>
  <span data-ttu-id="36782-104">**ISEMenuItem** 物件是 Microsoft.PowerShell.Host.ISE.ISEMenuItem 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="36782-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="36782-105">[附加元件] 功能表上的所有功能表物件都是 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="36782-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="36782-106">[內容]</span><span class="sxs-lookup"><span data-stu-id="36782-106">Properties</span></span>

###  <span data-ttu-id="36782-107"><a name="DisplayName"></a> DisplayName</span><span class="sxs-lookup"><span data-stu-id="36782-107"><a name="DisplayName"></a> DisplayName</span></span>
  <span data-ttu-id="36782-108">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="36782-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="36782-109">唯讀屬性，可取得功能表項目的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="36782-109">The read-only property that gets the display name of the menu item.</span></span>

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

###  <span data-ttu-id="36782-110"><a name="Action"></a> Action</span><span class="sxs-lookup"><span data-stu-id="36782-110"><a name="Action"></a> Action</span></span>
  <span data-ttu-id="36782-111">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="36782-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="36782-112">唯讀屬性，可取得指令碼的區塊。</span><span class="sxs-lookup"><span data-stu-id="36782-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="36782-113">當您按一下功能表項目，它會叫用動作。</span><span class="sxs-lookup"><span data-stu-id="36782-113">It invokes the action when you click the menu item.</span></span>

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

###  <span data-ttu-id="36782-114"><a name="Shortcut"></a> Shortcut</span><span class="sxs-lookup"><span data-stu-id="36782-114"><a name="Shortcut"></a> Shortcut</span></span>
  <span data-ttu-id="36782-115">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="36782-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="36782-116">唯讀屬性，可取得功能表項目的 Windows 輸入鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="36782-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

###  <span data-ttu-id="36782-117"><a name="Submenus"></a> Submenus</span><span class="sxs-lookup"><span data-stu-id="36782-117"><a name="Submenus"></a> Submenus</span></span>
  <span data-ttu-id="36782-118">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="36782-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="36782-119">唯讀屬性，可取得功能表項目的[子功能表清單](The-ISEMenuItemCollection-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="36782-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="36782-120">指令碼範例</span><span class="sxs-lookup"><span data-stu-id="36782-120">Scripting example</span></span>
 <span data-ttu-id="36782-121">若要進一步了解使用附加元件功能表及其可編寫指令碼的屬性，請仔細閱讀以下的指令碼範例。</span><span class="sxs-lookup"><span data-stu-id="36782-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## <a name="see-also"></a><span data-ttu-id="36782-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36782-122">See Also</span></span>
- [<span data-ttu-id="36782-123">ISEMenuItemCollection 物件</span><span class="sxs-lookup"><span data-stu-id="36782-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md) 
- [<span data-ttu-id="36782-124">Windows PowerShell ISE 指令碼物件模型</span><span class="sxs-lookup"><span data-stu-id="36782-124">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="36782-125">Windows PowerShell ISE 物件模型參考</span><span class="sxs-lookup"><span data-stu-id="36782-125">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="36782-126">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="36782-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
