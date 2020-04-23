---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEAddOnToolCollection 物件
ms.openlocfilehash: e07a47169381307b50ac190165307c926b4ad94e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737010"
---
# <a name="the-iseaddontoolcollection-object"></a>ISEAddOnToolCollection 物件

**ISEAddOnToolCollection** 物件是 **ISEAddOnTool** 物件的集合。 例如，`$psISE.CurrentPowerShellTab.VerticalAddOnTools` 物件。

## <a name="methods"></a>方法

### <a name="add-name-controltype-isvisible-"></a>Add\( Name, ControlType, \[IsVisible\] \)

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

將新的附加元件工具加入到集合。 它會傳回新加入的附加元件工具。 執行此命令之前，您必須在本機電腦上安裝附加元件工具並載入組件。

**Name** - 字串：指定要新增至 Windows PowerShell ISE 的附加元件工具顯示名稱。

**ControlType** - 類型：指定新增的控制項。

**\[IsVisible\]** - 選用的布林值：如果設定為 `$true`，附加元件工具會立即顯示在相關聯的工具窗格中。

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a>Remove\( Item \)

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

從集合中移除指定的附加元件工具。

**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool：指定要從 Windows PowerShell ISE 移除的物件。

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a>SetSelectedPowerShellTab\( psTab \)

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

選取 **psTab** 參數指定的 PowerShell 索引標籤。

**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab：要選取的 PowerShell 索引標籤。

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a>Remove\( psTab \)

在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

移除 **psTab** 參數指定的 PowerShell 索引標籤。

**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab：要移除的 PowerShell 索引標籤。

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a>另請參閱

- [PowerShellTab 物件](The-PowerShellTab-Object.md)
- [Windows PowerShell ISE 指令碼物件模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)
