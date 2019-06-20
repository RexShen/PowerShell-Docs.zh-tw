---
title: Windows PowerShell 概念 |Microsoft Docs
ms.custom: ''
ms.date: 6/12/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: 4410b1f9c80afefd5479fa68154f9947b805edcf
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263854"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="ac9af-102">Windows PowerShell 概念</span><span class="sxs-lookup"><span data-stu-id="ac9af-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="ac9af-103">本節包含可協助您了解 PowerShell，從開發人員的觀點來看的概念性資訊。</span><span class="sxs-lookup"><span data-stu-id="ac9af-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="ac9af-104">主題名稱</span><span class="sxs-lookup"><span data-stu-id="ac9af-104">Topic Name</span></span>|<span data-ttu-id="ac9af-105">描述</span><span class="sxs-lookup"><span data-stu-id="ac9af-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="ac9af-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="ac9af-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="ac9af-107">PowerShell 物件的描述。</span><span class="sxs-lookup"><span data-stu-id="ac9af-107">Description of PowerShell objects.</span></span> <span data-ttu-id="ac9af-108">如需詳細資訊，請參閱[關於建立物件](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span><span class="sxs-lookup"><span data-stu-id="ac9af-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="ac9af-109">建立 Runspace</span><span class="sxs-lookup"><span data-stu-id="ac9af-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="ac9af-110">作業的環境，其中可以處理命令。</span><span class="sxs-lookup"><span data-stu-id="ac9af-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="ac9af-111">如需詳細資訊，請參閱 < [Runspace 類別](/dotnet/api/system.management.automation.runspaces.runspace)。</span><span class="sxs-lookup"><span data-stu-id="ac9af-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="ac9af-112">擴充的輸出物件</span><span class="sxs-lookup"><span data-stu-id="ac9af-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="ac9af-113">如何擴充 PowerShell 物件。</span><span class="sxs-lookup"><span data-stu-id="ac9af-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="ac9af-114">如需詳細資訊，請參閱[需 Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="ac9af-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="ac9af-115">註冊 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ac9af-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="ac9af-116">如何將模組和嵌入式管理單元的 PowerShell 中提供。</span><span class="sxs-lookup"><span data-stu-id="ac9af-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="ac9af-117">如需詳細資訊，請參閱 <<c0> [ 模組和嵌入式管理單元](../cmdlet/modules-and-snap-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="ac9af-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="ac9af-118">Cmdlet 從要求確認</span><span class="sxs-lookup"><span data-stu-id="ac9af-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="ac9af-119">如何 cmdlet 與提供者的意見反應向使用者要求之前採取動作。</span><span class="sxs-lookup"><span data-stu-id="ac9af-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="ac9af-120">RuntimeDefinedParameter 類別</span><span class="sxs-lookup"><span data-stu-id="ac9af-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="ac9af-121">執行階段參數宣告。</span><span class="sxs-lookup"><span data-stu-id="ac9af-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="ac9af-122">System.Management.Automation 命名空間</span><span class="sxs-lookup"><span data-stu-id="ac9af-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="ac9af-123">PowerShell API 命名空間的概觀。</span><span class="sxs-lookup"><span data-stu-id="ac9af-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="ac9af-124">Windows PowerShell 提供者概觀</span><span class="sxs-lookup"><span data-stu-id="ac9af-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="ac9af-125">會儲存有關用來存取資料的 PowerShell 提供者的概觀。</span><span class="sxs-lookup"><span data-stu-id="ac9af-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="ac9af-126">適用於 PowerShell Cmdlet 撰寫說明</span><span class="sxs-lookup"><span data-stu-id="ac9af-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="ac9af-127">如何撰寫 PowerShell 指令程式說明。</span><span class="sxs-lookup"><span data-stu-id="ac9af-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ac9af-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac9af-128">See also</span></span>

[<span data-ttu-id="ac9af-129">PowerShell 類別</span><span class="sxs-lookup"><span data-stu-id="ac9af-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="ac9af-130">PowerShell Core API 參考</span><span class="sxs-lookup"><span data-stu-id="ac9af-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="ac9af-131">Windows PowerShell 程式設計人員指南</span><span class="sxs-lookup"><span data-stu-id="ac9af-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ac9af-132">撰寫 Windows PowerShell 模組的說明</span><span class="sxs-lookup"><span data-stu-id="ac9af-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="ac9af-133">撰寫 Windows Powershell 提供者</span><span class="sxs-lookup"><span data-stu-id="ac9af-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="ac9af-134">Windows PowerShell API 參考</span><span class="sxs-lookup"><span data-stu-id="ac9af-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="ac9af-135">Windows PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="ac9af-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)