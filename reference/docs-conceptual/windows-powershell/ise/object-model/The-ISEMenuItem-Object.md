---
ms.date: 12/31/2019
title: ISEMenuItem 物件
description: ISEMenuItem 物件是 Microsoft.PowerShell.Host.ISE.ISEMenuItem 類別的執行個體。 [附加元件] 功能表上的所有功能表物件都是 ISEMenuItem 類別的執行個體。
ms.openlocfilehash: 15036e3551687a21dfbe50834a89247c80949656
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663447"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="2a6c6-104">ISEMenuItem 物件</span><span class="sxs-lookup"><span data-stu-id="2a6c6-104">The ISEMenuItem Object</span></span>

<span data-ttu-id="2a6c6-105">**ISEMenuItem** 物件是 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-105">An **ISEMenuItem** object is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>
<span data-ttu-id="2a6c6-106">[附加元件] 功能表上的所有功能表物件都是 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-106">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="2a6c6-107">屬性</span><span class="sxs-lookup"><span data-stu-id="2a6c6-107">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="2a6c6-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2a6c6-108">DisplayName</span></span>

<span data-ttu-id="2a6c6-109">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2a6c6-110">唯讀屬性，可取得功能表項目的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-110">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="2a6c6-111">動作</span><span class="sxs-lookup"><span data-stu-id="2a6c6-111">Action</span></span>

<span data-ttu-id="2a6c6-112">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2a6c6-113">唯讀屬性，可取得指令碼的區塊。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-113">The read-only property that gets the block of script.</span></span> <span data-ttu-id="2a6c6-114">當您按一下功能表項目，它會叫用動作。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-114">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="2a6c6-115">快速鍵</span><span class="sxs-lookup"><span data-stu-id="2a6c6-115">Shortcut</span></span>

<span data-ttu-id="2a6c6-116">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2a6c6-117">唯讀屬性，可取得功能表項目的 Windows 輸入鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-117">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="2a6c6-118">子功能表</span><span class="sxs-lookup"><span data-stu-id="2a6c6-118">Submenus</span></span>

<span data-ttu-id="2a6c6-119">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2a6c6-120">唯讀屬性，可取得功能表項目的[子功能表清單](The-ISEMenuItemCollection-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-120">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="2a6c6-121">指令碼範例</span><span class="sxs-lookup"><span data-stu-id="2a6c6-121">Scripting example</span></span>

<span data-ttu-id="2a6c6-122">若要進一步了解使用附加元件功能表及其可編寫指令碼的屬性，請仔細閱讀以下的指令碼範例。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-122">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="2a6c6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a6c6-123">See Also</span></span>

- [<span data-ttu-id="2a6c6-124">ISEMenuItemCollection 物件</span><span class="sxs-lookup"><span data-stu-id="2a6c6-124">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="2a6c6-125">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="2a6c6-125">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="2a6c6-126">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="2a6c6-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
