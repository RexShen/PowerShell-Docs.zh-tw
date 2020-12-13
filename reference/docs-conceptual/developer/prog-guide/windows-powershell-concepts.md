---
ms.date: 06/12/2019
ms.topic: reference
title: Windows PowerShell 概念
description: Windows PowerShell 概念
ms.openlocfilehash: a9b88a2e575b7ff7c036ce0fcbc035f0b55d0f5f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355353"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="eebc5-103">Windows PowerShell 概念</span><span class="sxs-lookup"><span data-stu-id="eebc5-103">Windows PowerShell Concepts</span></span>

<span data-ttu-id="eebc5-104">本節包含可協助您從開發人員的觀點瞭解 PowerShell 的概念資訊。</span><span class="sxs-lookup"><span data-stu-id="eebc5-104">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="eebc5-105">主題名稱</span><span class="sxs-lookup"><span data-stu-id="eebc5-105">Topic Name</span></span>|<span data-ttu-id="eebc5-106">說明</span><span class="sxs-lookup"><span data-stu-id="eebc5-106">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="eebc5-107">about_Objects</span><span class="sxs-lookup"><span data-stu-id="eebc5-107">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="eebc5-108">PowerShell 物件的描述。</span><span class="sxs-lookup"><span data-stu-id="eebc5-108">Description of PowerShell objects.</span></span> <span data-ttu-id="eebc5-109">如需詳細資訊，請參閱 [關於建立物件](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span><span class="sxs-lookup"><span data-stu-id="eebc5-109">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="eebc5-110">建立 Runspace</span><span class="sxs-lookup"><span data-stu-id="eebc5-110">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="eebc5-111">處理命令的作業環境。</span><span class="sxs-lookup"><span data-stu-id="eebc5-111">The operating environments where commands are processed.</span></span> <span data-ttu-id="eebc5-112">如需詳細資訊，請參閱 [運行空間類別](/dotnet/api/system.management.automation.runspaces.runspace)。</span><span class="sxs-lookup"><span data-stu-id="eebc5-112">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="eebc5-113">延伸輸出物件</span><span class="sxs-lookup"><span data-stu-id="eebc5-113">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="eebc5-114">如何擴充 PowerShell 物件。</span><span class="sxs-lookup"><span data-stu-id="eebc5-114">How to extend PowerShell objects.</span></span> <span data-ttu-id="eebc5-115">如需詳細資訊，請參閱 [關於 Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="eebc5-115">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="eebc5-116">註冊 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eebc5-116">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="eebc5-117">如何讓模組和嵌入式管理單元可在 PowerShell 中使用。</span><span class="sxs-lookup"><span data-stu-id="eebc5-117">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="eebc5-118">如需詳細資訊，請參閱 [模組和嵌入式管理](../cmdlet/modules-and-snap-ins.md)單元。</span><span class="sxs-lookup"><span data-stu-id="eebc5-118">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="eebc5-119">從 Cmdlet 要求確認</span><span class="sxs-lookup"><span data-stu-id="eebc5-119">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="eebc5-120">Cmdlet 和提供者如何在採取動作之前要求使用者提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="eebc5-120">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="eebc5-121">RuntimeDefinedParameter 類別</span><span class="sxs-lookup"><span data-stu-id="eebc5-121">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="eebc5-122">執行時間參數宣告。</span><span class="sxs-lookup"><span data-stu-id="eebc5-122">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="eebc5-123">System. Management. Automation 命名空間</span><span class="sxs-lookup"><span data-stu-id="eebc5-123">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="eebc5-124">PowerShell API 命名空間的總覽。</span><span class="sxs-lookup"><span data-stu-id="eebc5-124">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="eebc5-125">Windows PowerShell 提供者概觀</span><span class="sxs-lookup"><span data-stu-id="eebc5-125">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="eebc5-126">關於用來存取資料存放區的 PowerShell 提供者總覽。</span><span class="sxs-lookup"><span data-stu-id="eebc5-126">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="eebc5-127">撰寫 PowerShell Cmdlet 的說明</span><span class="sxs-lookup"><span data-stu-id="eebc5-127">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="eebc5-128">如何撰寫 PowerShell Cmdlet 說明。</span><span class="sxs-lookup"><span data-stu-id="eebc5-128">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="eebc5-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="eebc5-129">See also</span></span>

[<span data-ttu-id="eebc5-130">PowerShell 類別</span><span class="sxs-lookup"><span data-stu-id="eebc5-130">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="eebc5-131">PowerShell Core API 參考</span><span class="sxs-lookup"><span data-stu-id="eebc5-131">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0&preserve-view=true)

[<span data-ttu-id="eebc5-132">Windows PowerShell 程式設計人員手冊</span><span class="sxs-lookup"><span data-stu-id="eebc5-132">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="eebc5-133">撰寫 Windows PowerShell 模組的說明</span><span class="sxs-lookup"><span data-stu-id="eebc5-133">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="eebc5-134">撰寫 Windows Powershell 提供者</span><span class="sxs-lookup"><span data-stu-id="eebc5-134">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="eebc5-135">Windows PowerShell API 參考</span><span class="sxs-lookup"><span data-stu-id="eebc5-135">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0&preserve-view=true)

[<span data-ttu-id="eebc5-136">Windows PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="eebc5-136">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)
