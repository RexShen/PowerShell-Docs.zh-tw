---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEMenuItem 物件
ms.openlocfilehash: c3ffe6e8f0b28987543fe0a873c552292dc5158a
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736976"
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="7d596-103">ISEMenuItem 物件</span><span class="sxs-lookup"><span data-stu-id="7d596-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="7d596-104">**ISEMenuItem** 物件是 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7d596-104">An **ISEMenuItem** object is an instance of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>
<span data-ttu-id="7d596-105">[附加元件]  功能表上的所有功能表物件都是 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7d596-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="7d596-106">屬性</span><span class="sxs-lookup"><span data-stu-id="7d596-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="7d596-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7d596-107">DisplayName</span></span>

<span data-ttu-id="7d596-108">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="7d596-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7d596-109">唯讀屬性，可取得功能表項目的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="7d596-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="7d596-110">動作</span><span class="sxs-lookup"><span data-stu-id="7d596-110">Action</span></span>

<span data-ttu-id="7d596-111">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="7d596-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7d596-112">唯讀屬性，可取得指令碼的區塊。</span><span class="sxs-lookup"><span data-stu-id="7d596-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="7d596-113">當您按一下功能表項目，它會叫用動作。</span><span class="sxs-lookup"><span data-stu-id="7d596-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="7d596-114">快速鍵</span><span class="sxs-lookup"><span data-stu-id="7d596-114">Shortcut</span></span>

<span data-ttu-id="7d596-115">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="7d596-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7d596-116">唯讀屬性，可取得功能表項目的 Windows 輸入鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="7d596-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="7d596-117">子功能表</span><span class="sxs-lookup"><span data-stu-id="7d596-117">Submenus</span></span>

<span data-ttu-id="7d596-118">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="7d596-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7d596-119">唯讀屬性，可取得功能表項目的[子功能表清單](The-ISEMenuItemCollection-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="7d596-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="7d596-120">指令碼範例</span><span class="sxs-lookup"><span data-stu-id="7d596-120">Scripting example</span></span>

<span data-ttu-id="7d596-121">若要進一步了解使用附加元件功能表及其可編寫指令碼的屬性，請仔細閱讀以下的指令碼範例。</span><span class="sxs-lookup"><span data-stu-id="7d596-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a><span data-ttu-id="7d596-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d596-122">See Also</span></span>

- [<span data-ttu-id="7d596-123">ISEMenuItemCollection 物件</span><span class="sxs-lookup"><span data-stu-id="7d596-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="7d596-124">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="7d596-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="7d596-125">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="7d596-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
