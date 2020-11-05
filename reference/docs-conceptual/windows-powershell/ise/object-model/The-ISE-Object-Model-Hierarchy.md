---
ms.date: 12/31/2019
title: ISE 物件模型階層
description: 此文章說明屬於 Windows PowerShell ISE 一部分的物件階層。
ms.openlocfilehash: 00980cda72f05bc6ccb398079b129de13a98f783
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658332"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="a446e-103">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="a446e-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="a446e-104">此文章說明屬於 Windows PowerShell 整合式指令碼環境 (ISE) 一部分的物件階層。</span><span class="sxs-lookup"><span data-stu-id="a446e-104">This article shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="a446e-105">Windows PowerShell ISE 隨附於 Windows PowerShell 3.0、4.0 和 5.1。</span><span class="sxs-lookup"><span data-stu-id="a446e-105">Windows PowerShell ISE is included in Windows PowerShell 3.0, 4.0, and 5.1.</span></span> <span data-ttu-id="a446e-106">按一下物件，即會帶領您進入定義物件之類別的參考文件。</span><span class="sxs-lookup"><span data-stu-id="a446e-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="a446e-107">$psISE 物件</span><span class="sxs-lookup"><span data-stu-id="a446e-107">$psISE Object</span></span>

<span data-ttu-id="a446e-108">`$psISE` 物件是 Windows PowerShell ISE 物件階層的[根物件](The-ObjectModelRoot-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="a446e-108">The `$psISE` object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="a446e-109">它位於最上層，可提供下列物件來編寫指令碼︰</span><span class="sxs-lookup"><span data-stu-id="a446e-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfile"></a>[<span data-ttu-id="a446e-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="a446e-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="a446e-111">`$psISE.CurrentFile` 物件是 [ISEFile](The-ISEFile-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a446e-111">The `$psISE.CurrentFile` object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltab"></a>[<span data-ttu-id="a446e-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="a446e-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="a446e-113">`$psISE.CurrentPowerShellTab` 物件是 [PowerShellTab](The-PowerShellTab-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a446e-113">The `$psISE.CurrentPowerShellTab` object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="a446e-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="a446e-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="a446e-115">`$psISE.CurrentVisibleHorizontalTool` 物件是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a446e-115">The `$psISE.CurrentVisibleHorizontalTool` object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="a446e-116">它代表目前停駐於 Windows PowerShell ISE 視窗頂端的已安裝附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="a446e-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="a446e-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="a446e-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="a446e-118">`$psISE.CurrentVisibleHorizontalTool` 物件是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a446e-118">The `$psISE.CurrentVisibleHorizontalTool` object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="a446e-119">它代表目前停駐於 Windows PowerShell ISE 視窗右邊的已安裝附加元件工具。</span><span class="sxs-lookup"><span data-stu-id="a446e-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptions"></a>[<span data-ttu-id="a446e-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="a446e-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="a446e-121">`$psISE.Options` 物件是 [ISEOptions](The-ISEOptions-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a446e-121">The `$psISE.Options` object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span> <span data-ttu-id="a446e-122">ISEOptions 物件代表適用於 Windows PowerShell ISE 的各種設定。</span><span class="sxs-lookup"><span data-stu-id="a446e-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="a446e-123">其為 Microsoft.PowerShell.Host.ISE.ISEOptions 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a446e-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabs"></a>[<span data-ttu-id="a446e-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="a446e-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="a446e-125">`$psISE.PowerShellTabs` 物件是 [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a446e-125">The `$psISE.PowerShellTabs` object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="a446e-126">它是所有目前開啟的 PowerShell 索引標籤集合，代表本機電腦上或連線的遠端電腦上可用的 Windows PowerShell 執行環境。</span><span class="sxs-lookup"><span data-stu-id="a446e-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="a446e-127">集合中的每個成員都是 [PowerShellTab](The-PowerShellTab-Object.md) 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a446e-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a446e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a446e-128">See Also</span></span>

- [<span data-ttu-id="a446e-129">Windows PowerShell ISE 指令碼物件模型的用途</span><span class="sxs-lookup"><span data-stu-id="a446e-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="a446e-130">ISE 物件模型階層</span><span class="sxs-lookup"><span data-stu-id="a446e-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
