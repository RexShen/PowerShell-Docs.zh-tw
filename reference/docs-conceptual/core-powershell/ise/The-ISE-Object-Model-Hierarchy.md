---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISE 物件模型階層"
ms.assetid: bc3300e4-9c17-4f00-a621-c8867126e3b3
ms.openlocfilehash: b6e251eac7db56896490362392e0a1c4c10a8d4a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2017
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="6ffbe-103">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="6ffbe-103">The ISE Object Model Hierarchy</span></span>
  <span data-ttu-id="6ffbe-104">本主題說明隸屬於 Windows PowerShell 整合式指令碼環境 (ISE) 一部分的物件階層。</span><span class="sxs-lookup"><span data-stu-id="6ffbe-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="6ffbe-105">Windows PowerShell ISE 隨附於 Windows PowerShell 3.0 和 Windows PowerShell 4.0。</span><span class="sxs-lookup"><span data-stu-id="6ffbe-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span> <span data-ttu-id="6ffbe-106">按一下物件，即會帶領您進入定義物件之類別的參考文件。</span><span class="sxs-lookup"><span data-stu-id="6ffbe-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

##  <a name="psise-object"></a><span data-ttu-id="6ffbe-107">**$psISE 物件**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-107">**$psISE Object**</span></span>
 <span data-ttu-id="6ffbe-108">**$psISE** 物件是 Windows PowerShell ISE 物件階層的[根物件](The-ObjectModelRoot-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="6ffbe-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="6ffbe-109">它位於最上層，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="6ffbe-109">Located at the top level, it makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="6ffbe-110">**[$psISE.CurrentFile]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-110">**[$psISE.CurrentFile]()**</span></span>

-   <span data-ttu-id="6ffbe-111">**[$psISE.CurrentPowerShellTab]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-111">**[$psISE.CurrentPowerShellTab]()**</span></span>

-   <span data-ttu-id="6ffbe-112">**[$psISE.CurrentVisibleHorizontalTool]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-112">**[$psISE.CurrentVisibleHorizontalTool]()**</span></span>

-   <span data-ttu-id="6ffbe-113">**[$psISE.CurrentVisibleVerticalTool]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-113">**[$psISE.CurrentVisibleVerticalTool]()**</span></span>

-   <span data-ttu-id="6ffbe-114">**[$psISE.Options]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-114">**[$psISE.Options]()**</span></span>

-   <span data-ttu-id="6ffbe-115">**[$psISE.PowerShellTabs]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-115">**[$psISE.PowerShellTabs]()**</span></span>

##  <a name="psisecurrentfilethe-isefile-objectmd"></a><span data-ttu-id="6ffbe-116">**[$psISE.CurrentFile](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-116">**[$psISE.CurrentFile](The-ISEFile-Object.md)**</span></span>
 <span data-ttu-id="6ffbe-117">**$psISE.CurrentFile** 物件是 [ISEFile](The-ISEFile-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="6ffbe-117">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="6ffbe-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**</span></span>

-   <span data-ttu-id="6ffbe-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)** 這個物件是 [ISEEditor](The-ISEEditor-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="6ffbe-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="6ffbe-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="6ffbe-121">**[CaretColumn](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-121">**[CaretColumn](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="6ffbe-122">**[CaretLine](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-122">**[CaretLine](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="6ffbe-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="6ffbe-124">**[LineCount](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-124">**[LineCount](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="6ffbe-125">**[SelectedText](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-125">**[SelectedText](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="6ffbe-126">**[Text](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-126">**[Text](The-ISEEditor-Object.md)**</span></span>

-   <span data-ttu-id="6ffbe-127">**[EncodingThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-127">**[EncodingThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-128">**[FullPathThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-128">**[FullPathThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-129">**[IsSavedThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-129">**[IsSavedThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-130">**[IsUntitledThe-ISEFile-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-130">**[IsUntitledThe-ISEFile-Object.md]()**</span></span>

##  <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a><span data-ttu-id="6ffbe-131">**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-131">**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span></span>
 <span data-ttu-id="6ffbe-132">**$psISE.CurrentPowerShellTab** 物件是 [PowerShellTab](The-PowerShellTab-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="6ffbe-132">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="6ffbe-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)** 這個物件是 [ISEMenuItem](The-ISEMenuItem-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="6ffbe-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**  This object is an instance of the [ISEMenuItem](The-ISEMenuItem-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="6ffbe-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="6ffbe-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="6ffbe-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="6ffbe-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span></span>

-   <span data-ttu-id="6ffbe-138">**[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-138">**[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)** 這個物件是 [ISEEditor](The-ISEEditor-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="6ffbe-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="6ffbe-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="6ffbe-141">**[CaretColumnThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-141">**[CaretColumnThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="6ffbe-142">**[CaretLineThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-142">**[CaretLineThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="6ffbe-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="6ffbe-144">**[LineCountThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-144">**[LineCountThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="6ffbe-145">**[SelectedTextThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-145">**[SelectedTextThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="6ffbe-146">**[TextThe-ISEEditor-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-146">**[TextThe-ISEEditor-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-147">**[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-147">**[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-148">**[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-148">**[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span></span>

-   <span data-ttu-id="6ffbe-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="6ffbe-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-152">**[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-152">**[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-153">**[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-153">**[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span></span>

-   <span data-ttu-id="6ffbe-155">**[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-155">**[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="6ffbe-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="6ffbe-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

##  <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="6ffbe-160">**$psISE.CurrentVisibleHorizontalTool**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-160">**$psISE.CurrentVisibleHorizontalTool**</span></span>
 <span data-ttu-id="6ffbe-161">**$psISE.CurrentVisibleHorizontalTool** 物件是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ffbe-161">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="6ffbe-162">它代表目前停駐於 Windows PowerShell ISE 視窗頂端的已安裝附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="6ffbe-162">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="6ffbe-163">這個物件可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="6ffbe-163">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="6ffbe-164">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-164">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-166">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-166">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span></span>

##  <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="6ffbe-167">**$psISE.CurrentVisibleVerticalTool**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-167">**$psISE.CurrentVisibleVerticalTool**</span></span>
 <span data-ttu-id="6ffbe-168">**$psISE.CurrentVisibleHorizontalTool** 物件是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ffbe-168">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="6ffbe-169">它代表目前停駐於 Windows PowerShell ISE 視窗右邊的已安裝附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="6ffbe-169">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="6ffbe-170">這個物件可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="6ffbe-170">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="6ffbe-171">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-171">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-173">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-173">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span></span>

##  <a name="psiseoptions"></a><span data-ttu-id="6ffbe-174">**$psISE.Options**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-174">**$psISE.Options**</span></span>
 <span data-ttu-id="6ffbe-175">**$psISE.Options** 物件可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="6ffbe-175">The **$psISE.Options** object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="6ffbe-176">**[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-176">**[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-177">**[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-177">**[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-178">**[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-178">**[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-179">**[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-179">**[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-180">**[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-180">**[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-181">**[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-181">**[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-182">**[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-182">**[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span></span>

-   <span data-ttu-id="6ffbe-184">**[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-184">**[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-185">**[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-185">**[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-186">**[$psISE.Options.FontNameThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-186">**[$psISE.Options.FontNameThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-187">**[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-187">**[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-188">**[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-188">**[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-189">**[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-189">**[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-190">**[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-190">**[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-191">**[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-191">**[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-192">**[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-192">**[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-193">**[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-193">**[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-194">**[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-194">**[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-195">**[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-195">**[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-196">**[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-196">**[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-197">**[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-197">**[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-198">**[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-198">**[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-199">**[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-199">**[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-200">**[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-200">**[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-201">**[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-201">**[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-203">**[$psISE.Options.UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-204">**[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-204">**[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-205">**[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-205">**[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-206">**[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-206">**[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-207">**[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-207">**[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-208">**[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-208">**[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-209">**[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-209">**[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="6ffbe-210">**[$psISE.Options.ZoomThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-210">**[$psISE.Options.ZoomThe-ISEOptions-Object.md]()**</span></span>

##  <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a><span data-ttu-id="6ffbe-211">**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="6ffbe-211">**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span></span>
 <span data-ttu-id="6ffbe-212">**$psISE.PowerShellTabs** 物件是 [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ffbe-212">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="6ffbe-213">它是所有目前開啟的 PowerShell 索引標籤集合，代表本機電腦上或連線的遠端電腦上可用的 Windows PowerShell 執行環境。</span><span class="sxs-lookup"><span data-stu-id="6ffbe-213">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="6ffbe-214">集合中的每個成員都是 [PowerShellTab](The-PowerShellTab-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ffbe-214">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ffbe-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ffbe-215">See Also</span></span>
- [<span data-ttu-id="6ffbe-216">Windows PowerShell ISE 指令碼物件模型</span><span class="sxs-lookup"><span data-stu-id="6ffbe-216">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="6ffbe-217">Windows PowerShell ISE 物件模型參考</span><span class="sxs-lookup"><span data-stu-id="6ffbe-217">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

