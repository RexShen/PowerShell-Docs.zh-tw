---
title: "PowerShellTabCollection 物件"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: 79edc4e41522b187cd6421be0bd897663b42bb44
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="the-powershelltabcollection-object"></a>PowerShellTabCollection 物件
  **PowerShellTab** 集合物件是 **PowerShellTab** 物件的集合。 每個 **PowerShellTab** 物件功能都可做為個別的執行階段環境。 它是 Microsoft.PowerShell.Host.ISE.PowerShellTabs 類別的執行個體。 範例是 **$psISE.PowerShellTabs** 物件。

## <a name="methods"></a>方法

### <a name="add"></a>Add\(\)
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 將新的 PowerShell 索引標籤新增到集合。 它會傳回新加入的索引標籤。

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a>Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 移除 **psTab** 參數指定的索引標籤。

 **psTab**
 要移除的 PowerShell 索引標籤。

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a>SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  在 Windows PowerShell ISE 2.0 與更新的版本中支援。 

 選取 **psTab** 參數指定的 PowerShell 索引標籤，使其成為目前作用中的 PowerShell 索引標籤。

 **psTab**
 要選取的 PowerShell 索引標籤。

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a>另請參閱
- [PowerShellTab 物件](The-PowerShellTab-Object.md) 
- [Windows PowerShell ISE 指令碼物件模型](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE 物件模型參考](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [ISE 物件模型階層](../ise/The-ISE-Object-Model-Hierarchy.md)

  
