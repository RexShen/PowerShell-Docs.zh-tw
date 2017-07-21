---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell ISE 物件模型參考"
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: e5d4ae03158d9b5b0efd98db1272bc13872181ac
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="windows-powershell-ise-object-model-reference"></a><span data-ttu-id="f061e-103">Windows PowerShell ISE 物件模型參考</span><span class="sxs-lookup"><span data-stu-id="f061e-103">Windows PowerShell ISE Object Model Reference</span></span>
  
## <a name="object-model-reference"></a><span data-ttu-id="f061e-104">物件模型參考</span><span class="sxs-lookup"><span data-stu-id="f061e-104">Object Model Reference</span></span>
 <span data-ttu-id="f061e-105">本節提供定義 Windows PowerShell® 整合式指令碼環境 (ISE) 中各種物件之基礎類別的參考。</span><span class="sxs-lookup"><span data-stu-id="f061e-105">This section provides a reference on the underlying classes that define the various objects inWindows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="f061e-106">若要依物件階層組織查看物件，請參閱 [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)。</span><span class="sxs-lookup"><span data-stu-id="f061e-106">To see the objects organized in their hierarchy, see [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md).</span></span>

 <span data-ttu-id="f061e-107">[ISEAddOnTool 物件](The-ISEAddOnTool-Object.md)
 範例：$psISE.CurrentVisibleHorizontalTool、$psISE.CurrentVisibleVerticalTool.</span><span class="sxs-lookup"><span data-stu-id="f061e-107">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md)
 Examples: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span></span>

 <span data-ttu-id="f061e-108">[ISEAddOnTool 物件](The-ISEAddOnTool-Object.md)
  [ISEEditor 物件](The-ISEEditor-Object.md)
 範例︰ $psISE.CurrentFile.Editor、$psISE.CurrentPowerShellTab.Output、$psISE.CurrentPowerShellTab.CommandPane。</span><span class="sxs-lookup"><span data-stu-id="f061e-108">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md)
  [The ISEEditor Object](The-ISEEditor-Object.md)
 Examples: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span></span>

 <span data-ttu-id="f061e-109">[ISEFile 物件](The-ISEFile-Object.md)
 範例︰ $psISE.CurrentFile、$psISE.PowerShellTabs.Files\[0\]。</span><span class="sxs-lookup"><span data-stu-id="f061e-109">[The ISEFile Object](The-ISEFile-Object.md)
 Examples: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span></span>

 <span data-ttu-id="f061e-110">[ISEFileCollection 物件](The-ISEFileCollection-Object.md)
 範例︰$psISE.PowerShellTabs.Files。</span><span class="sxs-lookup"><span data-stu-id="f061e-110">[The ISEFileCollection Object](The-ISEFileCollection-Object.md)
 Examples: $psISE.PowerShellTabs.Files.</span></span>

 <span data-ttu-id="f061e-111">[ISEMenuItem 物件](The-ISEMenuItem-Object.md)
 範例︰$psISE.CurrentPowerShellTab.AddOnsMenu、$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\]。</span><span class="sxs-lookup"><span data-stu-id="f061e-111">[The ISEMenuItem Object](The-ISEMenuItem-Object.md)
 Examples: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span></span>

 <span data-ttu-id="f061e-112">[ISEMenuItemCollection 物件](The-ISEMenuItemCollection-Object.md)
 範例︰$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus。</span><span class="sxs-lookup"><span data-stu-id="f061e-112">[The ISEMenuItemCollection Object](The-ISEMenuItemCollection-Object.md)
 Example: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span></span>

 <span data-ttu-id="f061e-113">[ISEOptions 物件](The-ISEOptions-Object.md)
 範例︰$psISE.Options、$psISE.Options.DefaultOptions。</span><span class="sxs-lookup"><span data-stu-id="f061e-113">[The ISEOptions Object](The-ISEOptions-Object.md)
 Examples: $psISE.Options, $psISE.Options.DefaultOptions.</span></span>

 <span data-ttu-id="f061e-114">[ObjectModelRoot 物件](The-ObjectModelRoot-Object.md)
 範例︰$psISE 根物件。</span><span class="sxs-lookup"><span data-stu-id="f061e-114">[The ObjectModelRoot Object](The-ObjectModelRoot-Object.md)
 Example: The root $psISE object.</span></span>

 <span data-ttu-id="f061e-115">[PowerShellTab 物件](The-PowerShellTab-Object.md)
 範例︰$psISE.CurrentPowerShellTab、$psISE.PowerShellTabs\[0\]。</span><span class="sxs-lookup"><span data-stu-id="f061e-115">[The PowerShellTab Object](The-PowerShellTab-Object.md)
 Examples: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span></span>

 <span data-ttu-id="f061e-116">[PowerShellTabCollection 物件](The-PowerShellTabCollection-Object.md)
 範例︰$psISE.PowerShellTabs。</span><span class="sxs-lookup"><span data-stu-id="f061e-116">[The PowerShellTabCollection Object](The-PowerShellTabCollection-Object.md)
 Example: $psISE.PowerShellTabs.</span></span>

## <a name="see-also"></a><span data-ttu-id="f061e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f061e-117">See Also</span></span>
- [<span data-ttu-id="f061e-118">Windows PowerShell ISE 指令碼物件模型</span><span class="sxs-lookup"><span data-stu-id="f061e-118">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
