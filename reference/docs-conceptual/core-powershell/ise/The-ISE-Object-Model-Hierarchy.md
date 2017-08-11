---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISE 物件模型階層"
ms.assetid: bc3300e4-9c17-4f00-a621-c8867126e3b3
ms.openlocfilehash: 0d0370ed9f64464038e643ae2cd241891fa74f33
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="9fe91-103">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="9fe91-103">The ISE Object Model Hierarchy</span></span>
  <span data-ttu-id="9fe91-104">本主題說明隸屬於 Windows PowerShell 整合式指令碼環境 (ISE) 一部分的物件階層。</span><span class="sxs-lookup"><span data-stu-id="9fe91-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="9fe91-105">Windows PowerShell ISE 隨附於 Windows PowerShell 3.0 和 Windows PowerShell 4.0。</span><span class="sxs-lookup"><span data-stu-id="9fe91-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span> <span data-ttu-id="9fe91-106">按一下物件，即會帶領您進入定義物件之類別的參考文件。</span><span class="sxs-lookup"><span data-stu-id="9fe91-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

##  <span data-ttu-id="9fe91-107"><a name="psISE"></a> **$psISE 物件**</span><span class="sxs-lookup"><span data-stu-id="9fe91-107"><a name="psISE"></a> **$psISE Object**</span></span>
 <span data-ttu-id="9fe91-108">**$psISE** 物件是 Windows PowerShell ISE 物件階層的[根物件](The-ObjectModelRoot-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="9fe91-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="9fe91-109">它位於最上層，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="9fe91-109">Located at the top level, it makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="9fe91-110">**[$psISE.CurrentFile](#currentfile)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-110">**[$psISE.CurrentFile](#currentfile)**</span></span>

-   <span data-ttu-id="9fe91-111">**[$psISE.CurrentPowerShellTab](#currentpowershelltab)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-111">**[$psISE.CurrentPowerShellTab](#currentpowershelltab)**</span></span>

-   <span data-ttu-id="9fe91-112">**[$psISE.CurrentVisibleHorizontalTool](#CurrentVisibleHorizontalTool)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-112">**[$psISE.CurrentVisibleHorizontalTool](#CurrentVisibleHorizontalTool)**</span></span>

-   <span data-ttu-id="9fe91-113">**[$psISE.CurrentVisibleVerticalTool](#CurrentVisibleVerticalTool)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-113">**[$psISE.CurrentVisibleVerticalTool](#CurrentVisibleVerticalTool)**</span></span>

-   <span data-ttu-id="9fe91-114">**[$psISE.Options](#options)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-114">**[$psISE.Options](#options)**</span></span>

-   <span data-ttu-id="9fe91-115">**[$psISE.PowerShellTabs](#powershelltabs)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-115">**[$psISE.PowerShellTabs](#powershelltabs)**</span></span>

##  <span data-ttu-id="9fe91-116"><a name="CurrentFile"></a> **[$psISE.CurrentFile](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-116"><a name="CurrentFile"></a> **[$psISE.CurrentFile](The-ISEFile-Object.md)**</span></span>
 <span data-ttu-id="9fe91-117">**$psISE.CurrentFile** 物件是 [ISEFile](The-ISEFile-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="9fe91-117">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="9fe91-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md#Displayname)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md#Displayname)**</span></span>

-   <span data-ttu-id="9fe91-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)** 這個物件是 [ISEEditor](The-ISEEditor-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="9fe91-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="9fe91-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md#CanGoToMatch)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md#CanGoToMatch)**</span></span>

    -   <span data-ttu-id="9fe91-121">**[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-121">**[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**</span></span>

    -   <span data-ttu-id="9fe91-122">**[CaretLine](The-ISEEditor-Object.md#CaretLine)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-122">**[CaretLine](The-ISEEditor-Object.md#CaretLine)**</span></span>

    -   <span data-ttu-id="9fe91-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**</span></span>

    -   <span data-ttu-id="9fe91-124">**[LineCount](The-ISEEditor-Object.md#LineCount)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-124">**[LineCount](The-ISEEditor-Object.md#LineCount)**</span></span>

    -   <span data-ttu-id="9fe91-125">**[SelectedText](The-ISEEditor-Object.md#SelectedText)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-125">**[SelectedText](The-ISEEditor-Object.md#SelectedText)**</span></span>

    -   <span data-ttu-id="9fe91-126">**[Text](The-ISEEditor-Object.md#Text)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-126">**[Text](The-ISEEditor-Object.md#Text)**</span></span>

-   <span data-ttu-id="9fe91-127">**[Encoding](The-ISEFile-Object.md#Encoding)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-127">**[Encoding](The-ISEFile-Object.md#Encoding)**</span></span>

-   <span data-ttu-id="9fe91-128">**[FullPath](The-ISEFile-Object.md#FullPath)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-128">**[FullPath](The-ISEFile-Object.md#FullPath)**</span></span>

-   <span data-ttu-id="9fe91-129">**[IsSaved](The-ISEFile-Object.md#IsSaved)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-129">**[IsSaved](The-ISEFile-Object.md#IsSaved)**</span></span>

-   <span data-ttu-id="9fe91-130">**[IsUntitled](The-ISEFile-Object.md#IsUntitled)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-130">**[IsUntitled](The-ISEFile-Object.md#IsUntitled)**</span></span>

##  <span data-ttu-id="9fe91-131"><a name="CurrentPowerShellTab"></a> **[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-131"><a name="CurrentPowerShellTab"></a> **[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span></span>
 <span data-ttu-id="9fe91-132">**$psISE.CurrentPowerShellTab** 物件是 [PowerShellTab](The-PowerShellTab-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="9fe91-132">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="9fe91-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)** 這個物件是 [ISEMenuItem](The-ISEMenuItem-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="9fe91-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**  This object is an instance of the [ISEMenuItem](The-ISEMenuItem-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="9fe91-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Action](The-ISEMenuItem-Object.md#Action)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Action](The-ISEMenuItem-Object.md#Action)**</span></span>

    -   <span data-ttu-id="9fe91-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName](The-ISEMenuItem-Object.md#DisplayName)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName](The-ISEMenuItem-Object.md#DisplayName)**</span></span>

    -   <span data-ttu-id="9fe91-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Shortcut](The-ISEMenuItem-Object.md#Shortcut)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Shortcut](The-ISEMenuItem-Object.md#Shortcut)**</span></span>

    -   <span data-ttu-id="9fe91-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span></span>

-   <span data-ttu-id="9fe91-138">**[$psISE.CurrentPowerShellTab.CanInvoke](The-PowerShellTab-Object.md#CanExecute)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-138">**[$psISE.CurrentPowerShellTab.CanInvoke](The-PowerShellTab-Object.md#CanExecute)**</span></span>

-   <span data-ttu-id="9fe91-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)** 這個物件是 [ISEEditor](The-ISEEditor-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="9fe91-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="9fe91-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatch](The-ISEEditor-Object.md#CanGoToMatch)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatch](The-ISEEditor-Object.md#CanGoToMatch)**</span></span>

    -   <span data-ttu-id="9fe91-141">**[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-141">**[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**</span></span>

    -   <span data-ttu-id="9fe91-142">**[CaretLine](The-ISEEditor-Object.md#CaretLine)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-142">**[CaretLine](The-ISEEditor-Object.md#CaretLine)**</span></span>

    -   <span data-ttu-id="9fe91-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**</span></span>

    -   <span data-ttu-id="9fe91-144">**[LineCount](The-ISEEditor-Object.md#LineCount)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-144">**[LineCount](The-ISEEditor-Object.md#LineCount)**</span></span>

    -   <span data-ttu-id="9fe91-145">**[SelectedText](The-ISEEditor-Object.md#SelectedText)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-145">**[SelectedText](The-ISEEditor-Object.md#SelectedText)**</span></span>

    -   <span data-ttu-id="9fe91-146">**[Text](The-ISEEditor-Object.md#Text)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-146">**[Text](The-ISEEditor-Object.md#Text)**</span></span>

-   <span data-ttu-id="9fe91-147">**[$psISE.CurrentPowerShellTab.DisplayName](The-PowerShellTab-Object.md#Displayname)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-147">**[$psISE.CurrentPowerShellTab.DisplayName](The-PowerShellTab-Object.md#Displayname)**</span></span>

-   <span data-ttu-id="9fe91-148">**[$psISE.CurrentPowerShellTab.ExpandedScript](The-PowerShellTab-Object.md#ExpandedScript)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-148">**[$psISE.CurrentPowerShellTab.ExpandedScript](The-PowerShellTab-Object.md#ExpandedScript)**</span></span>

-   <span data-ttu-id="9fe91-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span></span>

-   <span data-ttu-id="9fe91-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="9fe91-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#HorizontalAddOnToolsPaneOpened)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#HorizontalAddOnToolsPaneOpened)**</span></span>

-   <span data-ttu-id="9fe91-152">**[$psISE.CurrentPowerShellTab.Prompt](The-PowerShellTab-Object.md#Prompt)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-152">**[$psISE.CurrentPowerShellTab.Prompt](The-PowerShellTab-Object.md#Prompt)**</span></span>

-   <span data-ttu-id="9fe91-153">**[$psISE.CurrentPowerShellTab.ShowCommands](The-PowerShellTab-Object.md#ShowCommands)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-153">**[$psISE.CurrentPowerShellTab.ShowCommands](The-PowerShellTab-Object.md#ShowCommands)**</span></span>

-   <span data-ttu-id="9fe91-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span></span>

-   <span data-ttu-id="9fe91-155">**[$psISE.CurrentPowerShellTab.StatusText](The-PowerShellTab-Object.md#StatusText)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-155">**[$psISE.CurrentPowerShellTab.StatusText](The-PowerShellTab-Object.md#StatusText)**</span></span>

-   <span data-ttu-id="9fe91-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="9fe91-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#VerticalAddOnToolsPaneOpened)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#VerticalAddOnToolsPaneOpened)**</span></span>

-   <span data-ttu-id="9fe91-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="9fe91-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

##  <span data-ttu-id="9fe91-160"><a name="CurrentVisibleHorizontalTool"></a> **$psISE.CurrentVisibleHorizontalTool**</span><span class="sxs-lookup"><span data-stu-id="9fe91-160"><a name="CurrentVisibleHorizontalTool"></a> **$psISE.CurrentVisibleHorizontalTool**</span></span>
 <span data-ttu-id="9fe91-161">**$psISE.CurrentVisibleHorizontalTool** 物件是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9fe91-161">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="9fe91-162">它代表目前停駐於 Windows PowerShell ISE 視窗頂端的已安裝附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="9fe91-162">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="9fe91-163">這個物件可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="9fe91-163">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="9fe91-164">**[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#Control)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-164">**[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#Control)**</span></span>

-   <span data-ttu-id="9fe91-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#IsVisible)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#IsVisible)**</span></span>

-   <span data-ttu-id="9fe91-166">**[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-166">**[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**</span></span>

##  <span data-ttu-id="9fe91-167"><a name="CurrentVisibleVerticalTool"></a> **$psISE.CurrentVisibleVerticalTool**</span><span class="sxs-lookup"><span data-stu-id="9fe91-167"><a name="CurrentVisibleVerticalTool"></a> **$psISE.CurrentVisibleVerticalTool**</span></span>
 <span data-ttu-id="9fe91-168">**$psISE.CurrentVisibleHorizontalTool** 物件是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9fe91-168">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="9fe91-169">它代表目前停駐於 Windows PowerShell ISE 視窗右邊的已安裝附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="9fe91-169">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="9fe91-170">這個物件可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="9fe91-170">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="9fe91-171">**[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#Control)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-171">**[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#Control)**</span></span>

-   <span data-ttu-id="9fe91-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#IsVisible)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#IsVisible)**</span></span>

-   <span data-ttu-id="9fe91-173">**[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-173">**[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**</span></span>

##  <span data-ttu-id="9fe91-174"><a name="Options"></a> **$psISE.Options**</span><span class="sxs-lookup"><span data-stu-id="9fe91-174"><a name="Options"></a> **$psISE.Options**</span></span>
 <span data-ttu-id="9fe91-175">**$psISE.Options** 物件可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="9fe91-175">The **$psISE.Options** object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="9fe91-176">**[$psISE.Options.AutoSaveMinuteInterval](The-ISEOptions-Object.md#asmi)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-176">**[$psISE.Options.AutoSaveMinuteInterval](The-ISEOptions-Object.md#asmi)**</span></span>

-   <span data-ttu-id="9fe91-177">**[$psISE.Options.ConsolePaneBackgroundColor](The-ISEOptions-Object.md#cpbc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-177">**[$psISE.Options.ConsolePaneBackgroundColor](The-ISEOptions-Object.md#cpbc)**</span></span>

-   <span data-ttu-id="9fe91-178">**[$psISE.Options.ConsolePaneTextForegroundColor](The-ISEOptions-Object.md#conpfc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-178">**[$psISE.Options.ConsolePaneTextForegroundColor](The-ISEOptions-Object.md#conpfc)**</span></span>

-   <span data-ttu-id="9fe91-179">**[$psISE.Options.ConsolePaneTextBackgroundColor](The-ISEOptions-Object.md#conptbc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-179">**[$psISE.Options.ConsolePaneTextBackgroundColor](The-ISEOptions-Object.md#conptbc)**</span></span>

-   <span data-ttu-id="9fe91-180">**[$psISE.Options.ConsoleTokenColors](The-ISEOptions-Object.md#contc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-180">**[$psISE.Options.ConsoleTokenColors](The-ISEOptions-Object.md#contc)**</span></span>

-   <span data-ttu-id="9fe91-181">**[$psISE.Options.DebugBackgroundColor](The-ISEOptions-Object.md#dbc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-181">**[$psISE.Options.DebugBackgroundColor](The-ISEOptions-Object.md#dbc)**</span></span>

-   <span data-ttu-id="9fe91-182">**[$psISE.Options.DebugForegroundColor](The-ISEOptions-Object.md#dfc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-182">**[$psISE.Options.DebugForegroundColor](The-ISEOptions-Object.md#dfc)**</span></span>

-   <span data-ttu-id="9fe91-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span></span>

-   <span data-ttu-id="9fe91-184">**[$psISE.Options.ErrorBackgroundColor](The-ISEOptions-Object.md#ebc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-184">**[$psISE.Options.ErrorBackgroundColor](The-ISEOptions-Object.md#ebc)**</span></span>

-   <span data-ttu-id="9fe91-185">**[$psISE.Options.ErrorForegroundColor](The-ISEOptions-Object.md#efc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-185">**[$psISE.Options.ErrorForegroundColor](The-ISEOptions-Object.md#efc)**</span></span>

-   <span data-ttu-id="9fe91-186">**[$psISE.Options.FontName](The-ISEOptions-Object.md#fn)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-186">**[$psISE.Options.FontName](The-ISEOptions-Object.md#fn)**</span></span>

-   <span data-ttu-id="9fe91-187">**[$psISE.Options.Fontsize](The-ISEOptions-Object.md#fs)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-187">**[$psISE.Options.Fontsize](The-ISEOptions-Object.md#fs)**</span></span>

-   <span data-ttu-id="9fe91-188">**[$psISE.Options.IntellisenseTimeoutInSeconds](The-ISEOptions-Object.md#itis)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-188">**[$psISE.Options.IntellisenseTimeoutInSeconds](The-ISEOptions-Object.md#itis)**</span></span>

-   <span data-ttu-id="9fe91-189">**[$psISE.Options.MRUCount](The-ISEOptions-Object.md#mc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-189">**[$psISE.Options.MRUCount](The-ISEOptions-Object.md#mc)**</span></span>

-   <span data-ttu-id="9fe91-190">**[$psISE.Options.ScriptPaneBackgroundColor](The-ISEOptions-Object.md#spbc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-190">**[$psISE.Options.ScriptPaneBackgroundColor](The-ISEOptions-Object.md#spbc)**</span></span>

-   <span data-ttu-id="9fe91-191">**[$psISE.Options.ScriptPaneForegroundColor](The-ISEOptions-Object.md#spfc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-191">**[$psISE.Options.ScriptPaneForegroundColor](The-ISEOptions-Object.md#spfc)**</span></span>

-   <span data-ttu-id="9fe91-192">**[$psISE.Options.SelectedScriptPaneState](The-ISEOptions-Object.md#ssps)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-192">**[$psISE.Options.SelectedScriptPaneState](The-ISEOptions-Object.md#ssps)**</span></span>

-   <span data-ttu-id="9fe91-193">**[$psISE.Options.ShowDefaultSnippets](The-ISEOptions-Object.md#sds)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-193">**[$psISE.Options.ShowDefaultSnippets](The-ISEOptions-Object.md#sds)**</span></span>

-   <span data-ttu-id="9fe91-194">**[$psISE.Options.ShowIntellisenseInConsolePane](The-ISEOptions-Object.md#siicp)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-194">**[$psISE.Options.ShowIntellisenseInConsolePane](The-ISEOptions-Object.md#siicp)**</span></span>

-   <span data-ttu-id="9fe91-195">**[$psISE.Options.ShowIntellisenseInScriptPane](The-ISEOptions-Object.md#siisp)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-195">**[$psISE.Options.ShowIntellisenseInScriptPane](The-ISEOptions-Object.md#siisp)**</span></span>

-   <span data-ttu-id="9fe91-196">**[$psISE.Options.ShowLineNumbers](The-ISEOptions-Object.md#sln)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-196">**[$psISE.Options.ShowLineNumbers](The-ISEOptions-Object.md#sln)**</span></span>

-   <span data-ttu-id="9fe91-197">**[$psISE.Options.ShowOutlining](The-ISEOptions-Object.md#so)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-197">**[$psISE.Options.ShowOutlining](The-ISEOptions-Object.md#so)**</span></span>

-   <span data-ttu-id="9fe91-198">**[$psISE.Options.ShowToolBar](The-ISEOptions-Object.md#stb)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-198">**[$psISE.Options.ShowToolBar](The-ISEOptions-Object.md#stb)**</span></span>

-   <span data-ttu-id="9fe91-199">**[$psISE.Options.ShowWarningBeforeSavingOnRun](The-ISEOptions-Object.md#swbsor)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-199">**[$psISE.Options.ShowWarningBeforeSavingOnRun](The-ISEOptions-Object.md#swbsor)**</span></span>

-   <span data-ttu-id="9fe91-200">**[$psISE.Options.ShowWarningForDuplicateFiles](The-ISEOptions-Object.md#swfdf)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-200">**[$psISE.Options.ShowWarningForDuplicateFiles](The-ISEOptions-Object.md#swfdf)**</span></span>

-   <span data-ttu-id="9fe91-201">**[$psISE.Options.TokenColors](The-ISEOptions-Object.md#tc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-201">**[$psISE.Options.TokenColors](The-ISEOptions-Object.md#tc)**</span></span>

-   <span data-ttu-id="9fe91-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisense](The-ISEOptions-Object.md#uetsicpi)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisense](The-ISEOptions-Object.md#uetsicpi)**</span></span>

-   <span data-ttu-id="9fe91-203">**[$psISE.Options.UseEnterToSelectScriptPaneIntellisense](The-ISEOptions-Object.md#uetsispi)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisense](The-ISEOptions-Object.md#uetsispi)**</span></span>

-   <span data-ttu-id="9fe91-204">**[$psISE.Options.UseLocalHelp](The-ISEOptions-Object.md#ulh)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-204">**[$psISE.Options.UseLocalHelp](The-ISEOptions-Object.md#ulh)**</span></span>

-   <span data-ttu-id="9fe91-205">**[$psISE.Options.VerboseBackgroundColor](The-ISEOptions-Object.md#vbc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-205">**[$psISE.Options.VerboseBackgroundColor](The-ISEOptions-Object.md#vbc)**</span></span>

-   <span data-ttu-id="9fe91-206">**[$psISE.Options.VerboseForegroundColor](The-ISEOptions-Object.md#vfc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-206">**[$psISE.Options.VerboseForegroundColor](The-ISEOptions-Object.md#vfc)**</span></span>

-   <span data-ttu-id="9fe91-207">**[$psISE.Options.WarningBackgroundColor](The-ISEOptions-Object.md#wbc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-207">**[$psISE.Options.WarningBackgroundColor](The-ISEOptions-Object.md#wbc)**</span></span>

-   <span data-ttu-id="9fe91-208">**[$psISE.Options.WarningForegroundColor](The-ISEOptions-Object.md#wfc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-208">**[$psISE.Options.WarningForegroundColor](The-ISEOptions-Object.md#wfc)**</span></span>

-   <span data-ttu-id="9fe91-209">**[$psISE.Options.XmlTokenColors](The-ISEOptions-Object.md#xtc)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-209">**[$psISE.Options.XmlTokenColors](The-ISEOptions-Object.md#xtc)**</span></span>

-   <span data-ttu-id="9fe91-210">**[$psISE.Options.Zoom](The-ISEOptions-Object.md#z)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-210">**[$psISE.Options.Zoom](The-ISEOptions-Object.md#z)**</span></span>

##  <span data-ttu-id="9fe91-211"><a name="PowerShellTabs"></a> **[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="9fe91-211"><a name="PowerShellTabs"></a> **[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span></span>
 <span data-ttu-id="9fe91-212">**$psISE.PowerShellTabs** 物件是 [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9fe91-212">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="9fe91-213">它是所有目前開啟的 PowerShell 索引標籤集合，代表本機電腦上或連線的遠端電腦上可用的 Windows PowerShell 執行環境。</span><span class="sxs-lookup"><span data-stu-id="9fe91-213">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="9fe91-214">集合中的每個成員都是 [PowerShellTab](The-PowerShellTab-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9fe91-214">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fe91-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fe91-215">See Also</span></span>
- [<span data-ttu-id="9fe91-216">Windows PowerShell ISE 指令碼物件模型</span><span class="sxs-lookup"><span data-stu-id="9fe91-216">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="9fe91-217">Windows PowerShell ISE 物件模型參考</span><span class="sxs-lookup"><span data-stu-id="9fe91-217">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

