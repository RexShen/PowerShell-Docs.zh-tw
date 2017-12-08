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
# <a name="the-isemenuitemcollection-object"></a>ISEMenuItemCollection 物件
  **ISEMenuItemCollection** 物件是 **ISEMenuItem** 物件的集合。 它是 Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection 類別的執行個體。 **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** 物件即為一例，此物件可用來自訂 Windows PowerShell® 整合式指令碼環境 (ISE) 中的 [附加元件] 功能表。

## <a name="method"></a>方法

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 將功能表項目加入至集合。

 **DisplayName** 要新增的功能表顯示名稱。

 **Action** **System.Management.Automation.ScriptBlock** 物件，會指定與此功能表項目相關的動作。

 **Shortcut** 動作的鍵盤快速鍵。

 **Returns** 剛新增的 ISEMenuItem 物件。

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a>Clear\(\)
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 從功能表項目中移除所有的子功能表。

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a>另請參閱
- [ISEMenuItem 物件](The-ISEMenuItem-Object.md) 
- [Windows PowerShell ISE 指令碼物件模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE 物件模型參考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)

  
