---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShellTabCollection 物件
ms.openlocfilehash: 5a1318534ddce19c2f5faa0d2013e2b38d8b79e5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030479"
---
# <a name="the-powershelltabcollection-object"></a>PowerShellTabCollection 物件

**PowerShellTab** 集合物件是 **PowerShellTab** 物件的集合。 每個 **PowerShellTab** 物件功能都可做為個別的執行階段環境。 它是 Microsoft.PowerShell.Host.ISE.PowerShellTabs 類別的執行個體。 範例是 **$psISE.PowerShellTabs** 物件。

## <a name="methods"></a>Methods

### <a name="add"></a>Add\(\)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

將新的 PowerShell 索引標籤新增到集合。 它會傳回新加入的索引標籤。

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

移除 **psTab** 參數指定的索引標籤。

**psTab** 要移除的 PowerShell 索引標籤。

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)

在 Windows PowerShell ISE 2.0 與更新的版本中支援。

選取 **psTab** 參數指定的 PowerShell 索引標籤，使其成為目前作用中的 PowerShell 索引標籤。

**psTab** 要選取的 PowerShell 索引標籤。

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a>另請參閱

- [PowerShellTab 物件](The-PowerShellTab-Object.md)
- [Windows PowerShell ISE 指令碼物件模型的用途](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)
