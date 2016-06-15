---
title:  ISEMenuItemCollection 物件
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  0c0f5484-3320-408e-8534-5bd1c8e48512
---

# ISEMenuItemCollection 物件
  **ISEMenuItemCollection** 物件是 **ISEMenuItem** 物件的集合。 它是 Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection 類別的執行個體。 **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** 物件即為一例，此物件可用來自訂 Windows PowerShell® 整合式指令碼環境 (ISE) 中的 [附加元件] 功能表。

## 方法

### Add(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut)
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 將功能表項目加入至集合。

 **DisplayName**
 要加入的功能表顯示名稱。

 **Action**
 **System.Management.Automation.ScriptBlock** 物件，可指定與這個功能表項目建立關聯的動作。

 **Shortcut**
 動作的鍵盤快速鍵。

 **Returns**
 剛加入的 ISEMenuItem 物件。

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### Clear()
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 從功能表項目中移除所有的子功能表。

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## 另請參閱
 [ISEMenuItem 物件](The-ISEMenuItem-Object.md) 
 [Windows PowerShell ISE 指令碼物件模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 物件模型參考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


