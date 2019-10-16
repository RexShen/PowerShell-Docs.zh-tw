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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359627"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="627a4-102">透過 Windows PowerShell 活動建立工作流程</span><span class="sxs-lookup"><span data-stu-id="627a4-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="627a4-103">您可以從 [Visual Studio 工具箱] 選取 [活動]，並將其拖曳至 [工作流程設計工具] 視窗，以建立 Windows PowerShell 工作流程。</span><span class="sxs-lookup"><span data-stu-id="627a4-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="627a4-104">如需將 Windows PowerShell 活動新增至 Visual Studio 工具箱的詳細資訊，請參閱[將 Windows Powershell 活動新增至 Visual Studio 工具箱](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)。</span><span class="sxs-lookup"><span data-stu-id="627a4-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="627a4-105">下列程式說明如何建立可檢查使用者指定之電腦群組的網域狀態的工作流程、將它們加入網域（如果尚未聯結），然後重新檢查狀態。</span><span class="sxs-lookup"><span data-stu-id="627a4-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="627a4-106">設定專案</span><span class="sxs-lookup"><span data-stu-id="627a4-106">Setting up the Project</span></span>

1. <span data-ttu-id="627a4-107">依照[將 Windows PowerShell 活動新增至 Visual Studio 工具箱](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)中的程式，建立工作流程專案，並從[microsoft. powershell](/dotnet/api/Microsoft.PowerShell.Activities) . 活動和[microsoft. powershell 中新增活動。](/dotnet/api/Microsoft.PowerShell.Management.Activities)元件加入 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="627a4-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="627a4-108">將 [管理]、[microsoft]、[系統管理]、[]、[microsoft]、[管理] 和 [] 專案新增為 [參考元件]。</span><span class="sxs-lookup"><span data-stu-id="627a4-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="627a4-109">將活動新增至工作流程</span><span class="sxs-lookup"><span data-stu-id="627a4-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="627a4-110">將 [**序列**] 活動新增至工作流程。</span><span class="sxs-lookup"><span data-stu-id="627a4-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="627a4-111">建立名為 `ComputerName` 的引數，其引數類型為 `String[]`。</span><span class="sxs-lookup"><span data-stu-id="627a4-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="627a4-112">這個引數代表要檢查和聯結的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="627a4-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="627a4-113">建立名為 `DomainCred` 的引數，其類型為[system.web](/dotnet/api/System.Management.Automation.PSCredential)。</span><span class="sxs-lookup"><span data-stu-id="627a4-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="627a4-114">此引數代表已獲授權將電腦加入網域之網域帳戶的網域認證。</span><span class="sxs-lookup"><span data-stu-id="627a4-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="627a4-115">建立名為 `MachineCred` 的引數，其類型為[system.web](/dotnet/api/System.Management.Automation.PSCredential)。</span><span class="sxs-lookup"><span data-stu-id="627a4-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="627a4-116">此引數代表要檢查和聯結之電腦上系統管理員的認證。</span><span class="sxs-lookup"><span data-stu-id="627a4-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="627a4-117">在 [**序列**] 活動內新增**ParallelForEach**活動。</span><span class="sxs-lookup"><span data-stu-id="627a4-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="627a4-118">在文字方塊中輸入 `comp` 並 `ComputerName`，讓迴圈逐一查看 `ComputerName` 陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="627a4-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="627a4-119">將 [**序列**] 活動新增至**ParallelForEach**活動的主體。</span><span class="sxs-lookup"><span data-stu-id="627a4-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="627a4-120">將序列的**DisplayName**屬性設定為 `JoinDomain`。</span><span class="sxs-lookup"><span data-stu-id="627a4-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="627a4-121">將**GetWmiObject**活動新增至**JoinDomain**序列。</span><span class="sxs-lookup"><span data-stu-id="627a4-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="627a4-122">編輯**GetWmiObject**活動的屬性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="627a4-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="627a4-123">Property</span><span class="sxs-lookup"><span data-stu-id="627a4-123">Property</span></span>|<span data-ttu-id="627a4-124">值</span><span class="sxs-lookup"><span data-stu-id="627a4-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="627a4-125">**課堂**</span><span class="sxs-lookup"><span data-stu-id="627a4-125">**Class**</span></span>|<span data-ttu-id="627a4-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="627a4-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="627a4-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="627a4-127">**PSComputerName**</span></span>|<span data-ttu-id="627a4-128">背光</span><span class="sxs-lookup"><span data-stu-id="627a4-128">{comp}</span></span>|
   |<span data-ttu-id="627a4-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="627a4-129">**PSCredential**</span></span>|<span data-ttu-id="627a4-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="627a4-130">MachineCred</span></span>|

9. <span data-ttu-id="627a4-131">將**AddComputer**活動新增至**GetWmiObject**活動後面的**JoinDomain**序列。</span><span class="sxs-lookup"><span data-stu-id="627a4-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="627a4-132">編輯**AddComputer**活動的屬性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="627a4-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="627a4-133">Property</span><span class="sxs-lookup"><span data-stu-id="627a4-133">Property</span></span>|<span data-ttu-id="627a4-134">值</span><span class="sxs-lookup"><span data-stu-id="627a4-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="627a4-135">**名稱**</span><span class="sxs-lookup"><span data-stu-id="627a4-135">**ComputerName**</span></span>|<span data-ttu-id="627a4-136">背光</span><span class="sxs-lookup"><span data-stu-id="627a4-136">{comp}</span></span>|
    |<span data-ttu-id="627a4-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="627a4-137">**DomainCredential**</span></span>|<span data-ttu-id="627a4-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="627a4-138">DomainCred</span></span>|

11. <span data-ttu-id="627a4-139">將**RestartComputer**活動新增至**AddComputer**活動後面的**JoinDomain**序列。</span><span class="sxs-lookup"><span data-stu-id="627a4-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="627a4-140">編輯**RestartComputer**活動的屬性，如下所示。</span><span class="sxs-lookup"><span data-stu-id="627a4-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="627a4-141">Property</span><span class="sxs-lookup"><span data-stu-id="627a4-141">Property</span></span>|<span data-ttu-id="627a4-142">值</span><span class="sxs-lookup"><span data-stu-id="627a4-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="627a4-143">**名稱**</span><span class="sxs-lookup"><span data-stu-id="627a4-143">**ComputerName**</span></span>|<span data-ttu-id="627a4-144">背光</span><span class="sxs-lookup"><span data-stu-id="627a4-144">{comp}</span></span>|
    |<span data-ttu-id="627a4-145">**證書**</span><span class="sxs-lookup"><span data-stu-id="627a4-145">**Credential**</span></span>|<span data-ttu-id="627a4-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="627a4-146">MachineCred</span></span>|
    |<span data-ttu-id="627a4-147">**對於**</span><span class="sxs-lookup"><span data-stu-id="627a4-147">**For**</span></span>|<span data-ttu-id="627a4-148">WaitForServiceTypes 的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="627a4-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="627a4-149">**使**</span><span class="sxs-lookup"><span data-stu-id="627a4-149">**Force**</span></span>|<span data-ttu-id="627a4-150">True</span><span class="sxs-lookup"><span data-stu-id="627a4-150">True</span></span>|
    |<span data-ttu-id="627a4-151">Wait</span><span class="sxs-lookup"><span data-stu-id="627a4-151">Wait</span></span>|<span data-ttu-id="627a4-152">True</span><span class="sxs-lookup"><span data-stu-id="627a4-152">True</span></span>|
    |<span data-ttu-id="627a4-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="627a4-153">PSComputerName</span></span>|<span data-ttu-id="627a4-154">{""}</span><span class="sxs-lookup"><span data-stu-id="627a4-154">{""}</span></span>|

13. <span data-ttu-id="627a4-155">將**GetWmiObject**活動新增至**RestartComputer**活動後面的**JoinDomain**序列。</span><span class="sxs-lookup"><span data-stu-id="627a4-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="627a4-156">編輯其屬性，以與先前的**GetWmiObject**活動相同。</span><span class="sxs-lookup"><span data-stu-id="627a4-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="627a4-157">當您完成程式時，工作流程設計視窗看起來應該像這樣。</span><span class="sxs-lookup"><span data-stu-id="627a4-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="627a4-158">在工作流程設計工具中 @no__t 0JoinDomain XAML @ no__t-1![JOINDOMAIN xaml （在工作流程設計]工具(../media/joindomainworkflow.png "JoinDomainWorkflow")中）</span><span class="sxs-lookup"><span data-stu-id="627a4-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
    ![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>