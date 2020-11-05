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
# <a name="the-isemenuitem-object"></a>ISEMenuItem 物件

**ISEMenuItem** 物件是 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 類別的執行個體。
[附加元件] 功能表上的所有功能表物件都是 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 類別的執行個體。

## <a name="properties"></a>屬性

### <a name="displayname"></a>DisplayName

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得功能表項目的顯示名稱。

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a>動作

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得指令碼的區塊。 當您按一下功能表項目，它會叫用動作。

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>快速鍵

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得功能表項目的 Windows 輸入鍵盤快速鍵。

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>子功能表

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

唯讀屬性，可取得功能表項目的[子功能表清單](The-ISEMenuItemCollection-Object.md)。

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>指令碼範例

若要進一步了解使用附加元件功能表及其可編寫指令碼的屬性，請仔細閱讀以下的指令碼範例。

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

## <a name="see-also"></a>另請參閱

- [ISEMenuItemCollection 物件](The-ISEMenuItemCollection-Object.md)
- [Windows PowerShell ISE 指令碼物件模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)
