---
ms.date: 12/31/2019
title: ISEMenuItemCollection 物件
description: ISEMenuItemCollection 物件是 ISEMenuItem 物件的集合。
ms.openlocfilehash: cd86768d13b1326a8f35c44f0391ab60669cee4f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655988"
---
# <a name="the-isemenuitemcollection-object"></a>ISEMenuItemCollection 物件

**ISEMenuItemCollection** 物件是 **ISEMenuItem** 物件的集合。 它是 **Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection** 類別的執行個體。 `$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus` 物件即為一例，此物件可用來自訂 Windows PowerShell&reg; 整合式指令碼環境 (ISE) 中的 [附加元件] 功能表。

## <a name="method"></a>方法

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

將功能表項目加入至集合。

**DisplayName** 要新增的功能表顯示名稱。

**Action** **System.Management.Automation.ScriptBlock** 物件，會指定與此功能表項目相關的動作。

**Shortcut** 動作的鍵盤快速鍵。

**Returns** 剛新增的 **ISEMenuItem** 物件。

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Clear\(\)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

從功能表項目中移除所有的子功能表。

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>另請參閱

- [ISEMenuItem 物件](The-ISEMenuItem-Object.md)
- [Windows PowerShell ISE 指令碼物件模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)
