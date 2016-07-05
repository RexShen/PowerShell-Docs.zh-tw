---
title: "ISEMenuItem 物件"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 8b8c960604457fd41f5f7fefe0035003b675e13a

---

# ISEMenuItem 物件
  **ISEMenuItem** 物件是 Microsoft.PowerShell.Host.ISE.ISEMenuItem 類別的執行個體。 **[附加元件]** 功能表上的所有功能表物件都是 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 類別的執行個體。

## [內容]

###  <a name="DisplayName"></a> DisplayName
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 唯讀\-屬性，可取得功能表項目的顯示名稱。

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

###  <a name="Action"></a> 動作
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 唯讀\-屬性，可取得指令碼的區塊。 當您按一下功能表項目，它會叫用動作。

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

###  <a name="Shortcut"></a> 捷徑
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 唯讀屬性，可取得功能表項目的 Windows 輸入鍵盤快速鍵。

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

###  <a name="Submenus"></a> 子功能表
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 唯讀屬性，可取得功能表項目的[子功能表清單](The-ISEMenuItemCollection-Object.md)。

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## 指令碼範例
 若要進一步了解使用附加元件功能表及其可編寫指令碼的屬性，請仔細閱讀以下的指令碼範例。

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu – a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## 另請參閱
 [ISEAddOnToolCollection 物件](The-ISEMenuItemCollection-Object.md) 
 [Windows PowerShell ISE 指令碼物件模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Windows PowerShell ISE 物件模型參考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Jun16_HO4-->


