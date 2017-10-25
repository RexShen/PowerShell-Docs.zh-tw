---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEMenuItemCollection 物件"
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7ce9132021d4d5e755503e0adb355beb388a625a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="3a253-103">ISEMenuItemCollection 物件</span><span class="sxs-lookup"><span data-stu-id="3a253-103">The ISEMenuItemCollection Object</span></span>
  <span data-ttu-id="3a253-104">**ISEMenuItemCollection** 物件是 **ISEMenuItem** 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="3a253-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="3a253-105">它是 Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3a253-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="3a253-106">**$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** 物件即為一例，此物件可用來自訂 Windows PowerShell® 整合式指令碼環境 (ISE) 中的 [附加元件] 功能表。</span><span class="sxs-lookup"><span data-stu-id="3a253-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="3a253-107">方法</span><span class="sxs-lookup"><span data-stu-id="3a253-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="3a253-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="3a253-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>
  <span data-ttu-id="3a253-109">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="3a253-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="3a253-110">將功能表項目加入至集合。</span><span class="sxs-lookup"><span data-stu-id="3a253-110">Adds a menu item to the collection.</span></span>

 <span data-ttu-id="3a253-111">**DisplayName** 要新增的功能表顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="3a253-111">**DisplayName** The display name of the menu to be added.</span></span>

 <span data-ttu-id="3a253-112">**Action** **System.Management.Automation.ScriptBlock** 物件，會指定與此功能表項目相關的動作。</span><span class="sxs-lookup"><span data-stu-id="3a253-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

 <span data-ttu-id="3a253-113">**Shortcut** 動作的鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="3a253-113">**Shortcut** The keyboard shortcut for the action.</span></span>

 <span data-ttu-id="3a253-114">**Returns** 剛新增的 ISEMenuItem 物件。</span><span class="sxs-lookup"><span data-stu-id="3a253-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a><span data-ttu-id="3a253-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="3a253-115">Clear\(\)</span></span>
  <span data-ttu-id="3a253-116">在 Windows PowerShell ISE 2.0 與更新的版本中支援。</span><span class="sxs-lookup"><span data-stu-id="3a253-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="3a253-117">從功能表項目中移除所有的子功能表。</span><span class="sxs-lookup"><span data-stu-id="3a253-117">Removes all submenus from the menu item.</span></span>

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a><span data-ttu-id="3a253-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a253-118">See Also</span></span>
- [<span data-ttu-id="3a253-119">ISEMenuItem 物件</span><span class="sxs-lookup"><span data-stu-id="3a253-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md) 
- [<span data-ttu-id="3a253-120">Windows PowerShell ISE 指令碼物件模型</span><span class="sxs-lookup"><span data-stu-id="3a253-120">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="3a253-121">Windows PowerShell ISE 物件模型參考</span><span class="sxs-lookup"><span data-stu-id="3a253-121">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="3a253-122">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="3a253-122">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
