---
title: 使用 Windows PowerShell 活動建立工作流程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080421"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="a310a-102">透過 Windows PowerShell 活動建立工作流程</span><span class="sxs-lookup"><span data-stu-id="a310a-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="a310a-103">您可以從 Visual Studio 工具箱中選取活動，並將它們拖曳至 [工作流程設計工具] 視窗，以建立 Windows PowerShell 工作流程。</span><span class="sxs-lookup"><span data-stu-id="a310a-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="a310a-104">如需將 Windows PowerShell 活動新增至 Visual Studio 工具箱，請參閱[至 Visual Studio 工具箱中新增 Windows PowerShell 活動](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)。</span><span class="sxs-lookup"><span data-stu-id="a310a-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="a310a-105">下列程序說明如何建立會檢查一組使用者指定電腦的網域狀態、 將它們加入網域，如果他們未已經加入，然後再檢查一次狀態的工作流程。</span><span class="sxs-lookup"><span data-stu-id="a310a-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="a310a-106">設定專案</span><span class="sxs-lookup"><span data-stu-id="a310a-106">Setting up the Project</span></span>

1. <span data-ttu-id="a310a-107">請依照下列中的程序[新增 Windows PowerShell 活動新增到 Visual Studio 工具箱](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)來建立工作流程專案，並將從活動加入[Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities)和[Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)至工具箱的組件。</span><span class="sxs-lookup"><span data-stu-id="a310a-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="a310a-108">加入 System.Management.Automation、 Microsoft.PowerShell.Activities、 System.Management、 Microsoft.PowerShell.Management.Activities 和 Microsoft.PowerShell.Commands.Management 專案來做為參考組件。</span><span class="sxs-lookup"><span data-stu-id="a310a-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="a310a-109">將活動加入至工作流程</span><span class="sxs-lookup"><span data-stu-id="a310a-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="a310a-110">新增**順序**至工作流程的活動。</span><span class="sxs-lookup"><span data-stu-id="a310a-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="a310a-111">建立名為引數`ComputerName`的引數類型`String[]`。</span><span class="sxs-lookup"><span data-stu-id="a310a-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="a310a-112">這個引數表示要檢查和加入的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="a310a-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="a310a-113">建立名為引數`DomainCred`型別的[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)。</span><span class="sxs-lookup"><span data-stu-id="a310a-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="a310a-114">這個引數代表有權將電腦加入網域的網域帳戶的網域認證。</span><span class="sxs-lookup"><span data-stu-id="a310a-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="a310a-115">建立名為引數`MachineCred`型別的[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)。</span><span class="sxs-lookup"><span data-stu-id="a310a-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="a310a-116">這個引數代表檢查，並將 在電腦上的系統管理員的認證。</span><span class="sxs-lookup"><span data-stu-id="a310a-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="a310a-117">新增**ParallelForEach**活動內**順序**活動。</span><span class="sxs-lookup"><span data-stu-id="a310a-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="a310a-118">請輸入`comp`並`ComputerName`中的文字方塊，讓迴圈逐一查看的項目`ComputerName`陣列。</span><span class="sxs-lookup"><span data-stu-id="a310a-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="a310a-119">新增**順序**活動的主體**ParallelForEach**活動。</span><span class="sxs-lookup"><span data-stu-id="a310a-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="a310a-120">設定**DisplayName**屬性的順序`JoinDomain`。</span><span class="sxs-lookup"><span data-stu-id="a310a-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="a310a-121">新增**GetWmiObject**活動**JoinDomain**順序。</span><span class="sxs-lookup"><span data-stu-id="a310a-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="a310a-122">編輯的屬性**GetWmiObject**活動，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a310a-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="a310a-123">屬性</span><span class="sxs-lookup"><span data-stu-id="a310a-123">Property</span></span>|<span data-ttu-id="a310a-124">值</span><span class="sxs-lookup"><span data-stu-id="a310a-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="a310a-125">**類別**</span><span class="sxs-lookup"><span data-stu-id="a310a-125">**Class**</span></span>|<span data-ttu-id="a310a-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="a310a-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="a310a-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="a310a-127">**PSComputerName**</span></span>|<span data-ttu-id="a310a-128">{comp}</span><span class="sxs-lookup"><span data-stu-id="a310a-128">{comp}</span></span>|
   |<span data-ttu-id="a310a-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="a310a-129">**PSCredential**</span></span>|<span data-ttu-id="a310a-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="a310a-130">MachineCred</span></span>|

9. <span data-ttu-id="a310a-131">新增**AddComputer**活動**JoinDomain**序列之後**GetWmiObject**活動。</span><span class="sxs-lookup"><span data-stu-id="a310a-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="a310a-132">編輯的屬性**AddComputer**活動，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a310a-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="a310a-133">屬性</span><span class="sxs-lookup"><span data-stu-id="a310a-133">Property</span></span>|<span data-ttu-id="a310a-134">值</span><span class="sxs-lookup"><span data-stu-id="a310a-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="a310a-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="a310a-135">**ComputerName**</span></span>|<span data-ttu-id="a310a-136">{comp}</span><span class="sxs-lookup"><span data-stu-id="a310a-136">{comp}</span></span>|
    |<span data-ttu-id="a310a-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="a310a-137">**DomainCredential**</span></span>|<span data-ttu-id="a310a-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="a310a-138">DomainCred</span></span>|

11. <span data-ttu-id="a310a-139">新增**RestartComputer**活動**JoinDomain**序列之後**AddComputer**活動。</span><span class="sxs-lookup"><span data-stu-id="a310a-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="a310a-140">編輯的屬性**RestartComputer**活動，如下所示。</span><span class="sxs-lookup"><span data-stu-id="a310a-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="a310a-141">屬性</span><span class="sxs-lookup"><span data-stu-id="a310a-141">Property</span></span>|<span data-ttu-id="a310a-142">值</span><span class="sxs-lookup"><span data-stu-id="a310a-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="a310a-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="a310a-143">**ComputerName**</span></span>|<span data-ttu-id="a310a-144">{comp}</span><span class="sxs-lookup"><span data-stu-id="a310a-144">{comp}</span></span>|
    |<span data-ttu-id="a310a-145">**認證**</span><span class="sxs-lookup"><span data-stu-id="a310a-145">**Credential**</span></span>|<span data-ttu-id="a310a-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="a310a-146">MachineCred</span></span>|
    |<span data-ttu-id="a310a-147">**For**</span><span class="sxs-lookup"><span data-stu-id="a310a-147">**For**</span></span>|<span data-ttu-id="a310a-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="a310a-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="a310a-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="a310a-149">**Force**</span></span>|<span data-ttu-id="a310a-150">True</span><span class="sxs-lookup"><span data-stu-id="a310a-150">True</span></span>|
    |<span data-ttu-id="a310a-151">Wait</span><span class="sxs-lookup"><span data-stu-id="a310a-151">Wait</span></span>|<span data-ttu-id="a310a-152">True</span><span class="sxs-lookup"><span data-stu-id="a310a-152">True</span></span>|
    |<span data-ttu-id="a310a-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="a310a-153">PSComputerName</span></span>|<span data-ttu-id="a310a-154">{""}</span><span class="sxs-lookup"><span data-stu-id="a310a-154">{""}</span></span>|

13. <span data-ttu-id="a310a-155">新增**GetWmiObject**活動**JoinDomain**序列之後**RestartComputer**活動。</span><span class="sxs-lookup"><span data-stu-id="a310a-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="a310a-156">編輯其屬性，以與先前相同**GetWmiObject**活動。</span><span class="sxs-lookup"><span data-stu-id="a310a-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="a310a-157">當您完成程序時，工作流程的 [設計] 視窗應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="a310a-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="a310a-158">![在工作流程設計工具中的 JoinDomain XAML](../media/joindomainworkflow.png)
    ![工作流程設計工具中的 JoinDomain XAML](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="a310a-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>