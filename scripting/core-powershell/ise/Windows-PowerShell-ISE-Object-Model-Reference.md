---
title: Windows PowerShell ISE 物件模型參考
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
---
# Windows PowerShell ISE 物件模型參考
  
## 物件模型參考
 本節提供定義 Windows PowerShell® 整合式指令碼環境 (ISE) 中各種物件之基礎類別的參考。 若要查看依物件階層組織的物件，請參閱 [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)。.

 [ISEAddOnTool 物件](The-ISEAddOnTool-Object.md)
 範例：$psISE.CurrentVisibleHorizontalTool、$psISE.CurrentVisibleVerticalTool。

 [ISEAddOnTool 物件](The-ISEAddOnTool-Object.md)
  [ISEEditor 物件](The-ISEEditor-Object.md)
 範例：$psISE.CurrentFile.Editor、$psISE.CurrentPowerShellTab.Output、$psISE.CurrentPowerShellTab.CommandPane。

 [ISEFile 物件](The-ISEFile-Object.md)
 範例：$psISE.CurrentFile、$psISE.PowerShellTabs.Files\[0\]。

 [ISEFileCollection 物件](The-ISEFileCollection-Object.md)
 範例：$psISE.PowerShellTabs.Files。

 [ISEMenuItem 物件](The-ISEMenuItem-Object.md)
 範例：$psISE.CurrentPowerShellTab.AddOnsMenu 、$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\]。

 [ISEMenuItemCollection 物件](The-ISEMenuItemCollection-Object.md)
 範例：$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus。

 [ISEOptions 物件](The-ISEOptions-Object.md)
 範例：$psISE.Options、$psISE.Options.DefaultOptions。

 [ObjectModelRoot 物件](The-ObjectModelRoot-Object.md)
 範例：根 $psISE 物件。

 [PowerShellTab 物件](The-PowerShellTab-Object.md)
 範例：$psISE.CurrentPowerShellTab、$psISE.PowerShellTabs\[0\]。

 [PowerShellTabCollection 物件](The-PowerShellTabCollection-Object.md)
 範例：$psISE.PowerShellTabs。

## 另請參閱
 [Windows PowerShell ISE 指令碼物件模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  


<!--HONumber=May16_HO2-->


