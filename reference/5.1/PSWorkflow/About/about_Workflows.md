---
description: 提供 PowerShell 工作流程功能的簡介。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Workflows
ms.openlocfilehash: fbd8ee62b1e9c6969d489c5024c33f5cca883dc6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207211"
---
# <a name="about-workflows"></a><span data-ttu-id="ef054-104">關於工作流程</span><span class="sxs-lookup"><span data-stu-id="ef054-104">About Workflows</span></span>

## <a name="short-description"></a><span data-ttu-id="ef054-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="ef054-105">Short description</span></span>

<span data-ttu-id="ef054-106">提供 PowerShell 工作流程功能的簡介。</span><span class="sxs-lookup"><span data-stu-id="ef054-106">Provides a brief introduction to the PowerShell Workflow feature.</span></span>

## <a name="long-description"></a><span data-ttu-id="ef054-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="ef054-107">Long description</span></span>

<span data-ttu-id="ef054-108">PowerShell 工作流程帶來了 [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) 到 powershell 的優點，並可讓您撰寫和執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="ef054-108">PowerShell Workflow brings the benefits of the [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) to PowerShell and enables you to write and run workflows.</span></span>

<span data-ttu-id="ef054-109">Powershell 工作流程是在 PowerShell 3.0 中引進，且模組最多可供 PowerShell 5.1 使用。</span><span class="sxs-lookup"><span data-stu-id="ef054-109">PowerShell Workflow was introduced in PowerShell 3.0 and the module is available up to PowerShell 5.1.</span></span> <span data-ttu-id="ef054-110">如需 PowerShell 工作流程的詳細資訊，請參閱 [工作流程指南](/previous-versions/powershell/scripting/components/workflows-guide) 和 [撰寫 Windows PowerShell 工作流程](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)。</span><span class="sxs-lookup"><span data-stu-id="ef054-110">For more information about PowerShell Workflow, see the [Workflows Guide](/previous-versions/powershell/scripting/components/workflows-guide) and [Writing a Windows PowerShell Workflow](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow).</span></span>

## <a name="about-workflows"></a><span data-ttu-id="ef054-111">關於工作流程</span><span class="sxs-lookup"><span data-stu-id="ef054-111">About workflows</span></span>

<span data-ttu-id="ef054-112">工作流程是由一系列順序的相關活動所組成的命令。</span><span class="sxs-lookup"><span data-stu-id="ef054-112">Workflows are commands that consist of an ordered sequence of related activities.</span></span> <span data-ttu-id="ef054-113">通常，它們會執行一段很長的時間、收集資料，以及對數百部電腦進行變更，通常是在不同的環境中。</span><span class="sxs-lookup"><span data-stu-id="ef054-113">Typically, they run for an extended period of time, gathering data from and making changes to hundreds of computers, often in heterogeneous environments.</span></span>

<span data-ttu-id="ef054-114">您可以使用 XAML、Windows Workflow Foundation 中所使用的語言或 PowerShell 語言來撰寫工作流程。</span><span class="sxs-lookup"><span data-stu-id="ef054-114">Workflows can be written in XAML, the language used in Windows Workflow Foundation, or in the PowerShell language.</span></span> <span data-ttu-id="ef054-115">工作流程通常封裝在模組中，並包含說明主題。</span><span class="sxs-lookup"><span data-stu-id="ef054-115">Workflows are typically packaged in modules and include help topics.</span></span> <span data-ttu-id="ef054-116">如需詳細資訊，請參閱 [XAML 總覽 (WPF) ](/dotnet/framework/wpf/advanced/xaml-overview-wpf)。</span><span class="sxs-lookup"><span data-stu-id="ef054-116">For more information, see [XAML Overview (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf).</span></span>

<span data-ttu-id="ef054-117">工作流程在 IT 環境中是很重要的，因為它們可以在重新開機後繼續進行，而不會從常見的失敗</span><span class="sxs-lookup"><span data-stu-id="ef054-117">Workflows are critical in an IT environment because they can survive reboots and recover automatically from common failures.</span></span> <span data-ttu-id="ef054-118">您可以中斷連線，並從執行工作流程的電腦中斷連線，而不會中斷工作流程處理，並以透明方式暫停和繼續工作流程，而不會遺失</span><span class="sxs-lookup"><span data-stu-id="ef054-118">You can disconnect and reconnect from sessions and computers running workflows without interrupting workflow processing, and suspend and resume workflows transparently without data loss.</span></span> <span data-ttu-id="ef054-119">您可以記錄和審核工作流程中的每個活動，以供參考。</span><span class="sxs-lookup"><span data-stu-id="ef054-119">Each activity in a workflow can be logged and audited for reference.</span></span>
<span data-ttu-id="ef054-120">工作流程可作為工作執行，而且可以使用 PowerShell 的排程工作功能進行排程。</span><span class="sxs-lookup"><span data-stu-id="ef054-120">Workflows can run as jobs and can be scheduled by using the Scheduled Jobs feature of PowerShell.</span></span>

<span data-ttu-id="ef054-121">工作流程中的狀態和資料會在工作流程的開頭和結尾，以及您指定的點儲存或保存。</span><span class="sxs-lookup"><span data-stu-id="ef054-121">The state and data in a workflow is saved or persisted at the beginning and end of the workflow and at points that you specify.</span></span> <span data-ttu-id="ef054-122">工作流程持續點的運作方式就像是資料庫快照集或程式檢查點，可保護工作流程免于中斷和失敗的影響。</span><span class="sxs-lookup"><span data-stu-id="ef054-122">Workflow persistence points work like database snapshots or program checkpoints to protect the workflow from the effects of interruptions and failures.</span></span> <span data-ttu-id="ef054-123">如果工作流程無法從失敗中復原，您可以使用保存的資料並從最後一個持續點繼續，而不是從頭重新執行廣泛的工作流程。</span><span class="sxs-lookup"><span data-stu-id="ef054-123">If the workflow is unable to recover from a failure, you can use the persisted data and resume from the last persistence point, instead of rerunning an extensive workflow from the beginning.</span></span>

## <a name="workflow-requirements-and-configuration"></a><span data-ttu-id="ef054-124">工作流程需求和設定</span><span class="sxs-lookup"><span data-stu-id="ef054-124">Workflow requirements and configuration</span></span>

<span data-ttu-id="ef054-125">PowerShell 工作流程設定是由下列元素所組成：</span><span class="sxs-lookup"><span data-stu-id="ef054-125">A PowerShell Workflow configuration consists of the following elements:</span></span>

- <span data-ttu-id="ef054-126">執行工作流程的用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="ef054-126">A client computer, which runs the workflow.</span></span>
- <span data-ttu-id="ef054-127">用戶端電腦或遠端電腦上的工作流程會話（ **PSSession** ）。</span><span class="sxs-lookup"><span data-stu-id="ef054-127">A workflow session, **PSSession** , on the client computer or on a remote computer.</span></span>
- <span data-ttu-id="ef054-128">受管理的節點，受工作流程活動影響的目的電腦。</span><span class="sxs-lookup"><span data-stu-id="ef054-128">Managed nodes, the target computers that are affected by the workflow activities.</span></span>

<span data-ttu-id="ef054-129">工作流程會話並非必要，但建議使用。</span><span class="sxs-lookup"><span data-stu-id="ef054-129">The workflow session isn't required, but is recommended.</span></span> <span data-ttu-id="ef054-130">**Pssession** 可以利用 PowerShell 的健全修復和中斷連線會話功能來復原中斷連線的工作流程會話。</span><span class="sxs-lookup"><span data-stu-id="ef054-130">**PSSessions** can take advantage of the robust recovery and Disconnected Sessions features of PowerShell to recover disconnected workflow sessions.</span></span> <span data-ttu-id="ef054-131">如需詳細資訊，請參閱 [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md)</span><span class="sxs-lookup"><span data-stu-id="ef054-131">For more information, see [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md)</span></span>

<span data-ttu-id="ef054-132">由於用戶端電腦和執行工作流程會話的電腦可以是受管理的節點，因此您可以在單一電腦上執行工作流程來滿足所有角色。</span><span class="sxs-lookup"><span data-stu-id="ef054-132">Because the client computer and the computer on which the workflow session runs can be managed nodes, you can run a workflow on a single computer that fulfills all roles.</span></span>

<span data-ttu-id="ef054-133">用戶端電腦和執行工作流程會話的電腦必須執行 PowerShell 3.0。</span><span class="sxs-lookup"><span data-stu-id="ef054-133">The client computer and the computer on which the workflow session runs must be running PowerShell 3.0.</span></span> <span data-ttu-id="ef054-134">支援所有符合條件的系統，包括 Windows Server 作業系統的 Server Core 安裝選項。</span><span class="sxs-lookup"><span data-stu-id="ef054-134">All eligible systems are supported, including the Server Core installation options of Windows Server operating systems.</span></span>

<span data-ttu-id="ef054-135">若要執行包含 Cmdlet 的工作流程，受管理的節點必須有 Windows PowerShell 2.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="ef054-135">To run workflows that include cmdlets, the managed nodes must have Windows PowerShell 2.0 or later.</span></span> <span data-ttu-id="ef054-136">除非工作流程包含 Cmdlet，否則受管理的節點不需要 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ef054-136">Managed nodes don't require PowerShell unless the workflow includes cmdlets.</span></span> <span data-ttu-id="ef054-137">您可以在沒有 PowerShell 的電腦上執行包含 Windows Management Instrumentation (WMI) 和通用訊息模型 (CIM) 命令的工作流程。</span><span class="sxs-lookup"><span data-stu-id="ef054-137">You can run workflows that include Windows Management Instrumentation (WMI) and Common Information Model (CIM) commands on computers that don't have PowerShell.</span></span>

## <a name="how-to-get-workflows"></a><span data-ttu-id="ef054-138">如何取得工作流程</span><span class="sxs-lookup"><span data-stu-id="ef054-138">How to get workflows</span></span>

<span data-ttu-id="ef054-139">工作流程通常封裝在模組中。</span><span class="sxs-lookup"><span data-stu-id="ef054-139">Workflows are typically packaged in modules.</span></span> <span data-ttu-id="ef054-140">若要匯入包含工作流程的模組，請使用模組中的任何命令或使用 `Import-Module` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ef054-140">To import the module that includes a workflow, use any command in the module or use the `Import-Module` cmdlet.</span></span>
<span data-ttu-id="ef054-141">在模組中第一次使用任何命令時，會自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="ef054-141">Modules are imported automatically on first use of any command in the module.</span></span>

<span data-ttu-id="ef054-142">若要在電腦上安裝的模組中尋找工作流程，請使用 `Get-Command` Cmdlet 的 **CommandType** 參數。</span><span class="sxs-lookup"><span data-stu-id="ef054-142">To find the workflows in modules installed on your computer, use the `Get-Command` cmdlet's **CommandType** parameter.</span></span>

```powershell
Get-Command -CommandType Workflow
```

## <a name="how-to-run-workflows"></a><span data-ttu-id="ef054-143">如何執行工作流程</span><span class="sxs-lookup"><span data-stu-id="ef054-143">How to run workflows</span></span>

<span data-ttu-id="ef054-144">若要執行工作流程，請使用下列程式。</span><span class="sxs-lookup"><span data-stu-id="ef054-144">To run a workflow, use the following procedure.</span></span>

1. <span data-ttu-id="ef054-145">當受管理的節點為本機電腦時，不需要執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="ef054-145">When the managed node is the local computer, this step isn't required.</span></span>
   <span data-ttu-id="ef054-146">否則，請在用戶端電腦上使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ef054-146">Otherwise, on the client computer, start PowerShell with the **Run as administrator** option.</span></span>

   ```powershell
   Start-Process PowerShell -Verb RunAs
   ```

1. <span data-ttu-id="ef054-147">在執行工作流程會話的電腦和包含 Cmdlet 的工作流程所影響的受管理節點上啟用 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="ef054-147">Enable PowerShell remoting on the computer that runs the workflow session and on managed nodes affected by workflows that include cmdlets.</span></span>

   <span data-ttu-id="ef054-148">您只需要在每一部參與的電腦上執行此步驟一次。</span><span class="sxs-lookup"><span data-stu-id="ef054-148">You only need to do this step once on each participating computer.</span></span>

   <span data-ttu-id="ef054-149">只有在執行包含 Cmdlet 的工作流程時，才需要執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="ef054-149">This step is required only when running workflows that include cmdlets.</span></span> <span data-ttu-id="ef054-150">除非工作流程會話是在用戶端電腦上執行，或是在任何執行 PowerShell 3.0 的受管理節點上執行，否則您不需要在用戶端電腦上啟用遠端功能。</span><span class="sxs-lookup"><span data-stu-id="ef054-150">You don't need to enable remoting on the client computer, unless the workflows session runs on the client computer, or on any managed nodes that are running PowerShell 3.0.</span></span>

   <span data-ttu-id="ef054-151">若要啟用遠端功能，請使用 `Enable-PSRemoting` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ef054-151">To enable remoting, use the `Enable-PSRemoting` cmdlet.</span></span>

   ```powershell
   Enable-PSRemoting -Force
   ```

   <span data-ttu-id="ef054-152">您可以使用 [ **開啟腳本執行** ] 群組原則設定來啟用遠端功能。</span><span class="sxs-lookup"><span data-stu-id="ef054-152">You can enable remoting by using the **Turn on Script Execution** Group Policy setting.</span></span> <span data-ttu-id="ef054-153">如需詳細資訊，請參閱 [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) 和 [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="ef054-153">For more information, see [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) and [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

1. <span data-ttu-id="ef054-154">使用 `New-PSWorkflowSession` 或 `New-PSSession` Cmdlet 來建立工作流程會話。</span><span class="sxs-lookup"><span data-stu-id="ef054-154">Use the `New-PSWorkflowSession` or `New-PSSession` cmdlets to create the workflow session.</span></span>

   <span data-ttu-id="ef054-155">此 `New-PSWorkflowSession` Cmdlet 會啟動一個會話，該會話會在目的地電腦上使用內建的 **Microsoft PowerShell. 工作流程** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="ef054-155">The `New-PSWorkflowSession` cmdlet starts a session that uses the built-in **Microsoft.PowerShell.Workflow** session configuration on the destination computer.</span></span> <span data-ttu-id="ef054-156">此會話設定包括腳本、類型和格式化檔案，以及針對工作流程設計的選項。</span><span class="sxs-lookup"><span data-stu-id="ef054-156">This session configuration includes scripts, type and formatting files, and options that are designed for workflows.</span></span>

   <span data-ttu-id="ef054-157">或者，使用 `New-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ef054-157">Or, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="ef054-158">使用 **ConfigurationName** 參數來指定 **Microsoft PowerShell. 工作流程** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="ef054-158">Use the **ConfigurationName** parameter to specify the **Microsoft.PowerShell.Workflow** session configuration.</span></span> <span data-ttu-id="ef054-159">此命令與使用 `New-PSWorkflowSession` Cmdlet 相同。</span><span class="sxs-lookup"><span data-stu-id="ef054-159">This command is the same as using the `New-PSWorkflowSession` cmdlet.</span></span>

   <span data-ttu-id="ef054-160">替代方法是使用 `New-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ef054-160">An alternative is to use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="ef054-161">使用 **ConfigurationName** 參數來指定 **Microsoft PowerShell. 工作流程** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="ef054-161">Use the **ConfigurationName** parameter to specify the **Microsoft.PowerShell.Workflow** session configuration.</span></span>

   <span data-ttu-id="ef054-162">在本機電腦上：</span><span class="sxs-lookup"><span data-stu-id="ef054-162">On the local computer:</span></span>

   ```powershell
   $ws = New-PSWorkflowSession
   ```

   <span data-ttu-id="ef054-163">在遠端電腦上：</span><span class="sxs-lookup"><span data-stu-id="ef054-163">On a remote computer:</span></span>

   ```powershell
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

   <span data-ttu-id="ef054-164">如果您是工作流程會話電腦的系統管理員，您可以使用 `New-PSWorkflowExecutionOption` Cmdlet 來建立工作流程會話設定的自訂選項設定。</span><span class="sxs-lookup"><span data-stu-id="ef054-164">If you are an Administrator on the workflow session computer, you can use the `New-PSWorkflowExecutionOption` cmdlet to create custom option settings for the workflow session configuration.</span></span> <span data-ttu-id="ef054-165">而且，使用 `Set-PSSessionConfiguration` Cmdlet 來變更會話設定。</span><span class="sxs-lookup"><span data-stu-id="ef054-165">And, use the `Set-PSSessionConfiguration` cmdlet to change the session configuration.</span></span>

   ```powershell
   $sto = New-PSWorkflowExecutionOption -MaxConnectedSessions 150
   Invoke-Command -ComputerName Server01 `
   {Set-PSSessionConfiguration Microsoft.PowerShell.Workflow `
   -SessionTypeOption $Using:sto}
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

1. <span data-ttu-id="ef054-166">在工作流程會話中執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="ef054-166">Run the workflow in the workflow session.</span></span> <span data-ttu-id="ef054-167">若要指定受管理的節點（目的電腦）的名稱，請使用 **PSComputerName** 工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="ef054-167">To specify the names of the managed nodes, target computers, use the **PSComputerName** workflow common parameter.</span></span>

   <span data-ttu-id="ef054-168">下列範例會執行名為「 **測試-工作流程** 」的工作流程。</span><span class="sxs-lookup"><span data-stu-id="ef054-168">The following examples run the workflow named **Test-Workflow** .</span></span>

   <span data-ttu-id="ef054-169">其中受管理的節點是裝載工作流程會話的電腦：</span><span class="sxs-lookup"><span data-stu-id="ef054-169">Where the managed node is the computer that hosts the workflow session:</span></span>

   ```powershell
   Invoke-Command -Session $ws {Test-Workflow}
   ```

   <span data-ttu-id="ef054-170">受管理的節點是遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="ef054-170">Where the managed nodes are remote computers.</span></span>

   ```powershell
   Invoke-Command -Session $ws{
   Test-Workflow -PSComputerName Server01, Server02 }
   ```

   <span data-ttu-id="ef054-171">下列範例會在數百部電腦上執行 **測試工作流程** 。</span><span class="sxs-lookup"><span data-stu-id="ef054-171">The following example runs the **Test-Workflow** on hundreds of computers.</span></span> <span data-ttu-id="ef054-172">`Get-Content`Cmdlet 會從文字檔中取得電腦名稱稱，並將它們儲存在 `$Servers` 本機電腦上的變數中。</span><span class="sxs-lookup"><span data-stu-id="ef054-172">The `Get-Content` cmdlet gets the computer names from a text file and saves them in the `$Servers` variable on the local computer.</span></span>

   <span data-ttu-id="ef054-173">`Invoke-Command` 使用 `$Using` 範圍修飾符， `$Servers` 在本機會話中定義變數。</span><span class="sxs-lookup"><span data-stu-id="ef054-173">`Invoke-Command` uses the `$Using` scope modifier to define the `$Servers` variable in the local session.</span></span> <span data-ttu-id="ef054-174">如需範圍修飾符的詳細資訊 `$Using` ，請參閱 [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="ef054-174">For more information about the `$Using` scope modifier, see [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span></span>

   ```powershell
   $Servers = Get-Content Servers.txt
   Invoke-Command -Session $ws {Test-Workflow -PSComputerName $Using:Servers }
   ```

## <a name="using-workflow-common-parameters"></a><span data-ttu-id="ef054-175">使用工作流程一般參數</span><span class="sxs-lookup"><span data-stu-id="ef054-175">Using workflow common parameters</span></span>

<span data-ttu-id="ef054-176">工作流程一般參數是 PowerShell 自動新增至所有工作流程的一組參數。</span><span class="sxs-lookup"><span data-stu-id="ef054-176">The workflow common parameters are a set of parameters that PowerShell adds automatically to all workflows.</span></span> <span data-ttu-id="ef054-177">PowerShell 會將 Cmdlet 一般參數新增至所有工作流程，即使工作流程不使用 **CmdletBinding** 屬性。</span><span class="sxs-lookup"><span data-stu-id="ef054-177">PowerShell adds the cmdlet common parameters to all workflows, even if the workflow doesn't use the **CmdletBinding** attribute.</span></span>

<span data-ttu-id="ef054-178">例如，下列工作流程不會定義任何參數。</span><span class="sxs-lookup"><span data-stu-id="ef054-178">For example, the following workflow defines no parameters.</span></span> <span data-ttu-id="ef054-179">不過，當您執行工作流程時，它會同時具有 **CommonParameters** 和 **WorkflowCommonParameters** 。</span><span class="sxs-lookup"><span data-stu-id="ef054-179">However, when you run the workflow, it has both the **CommonParameters** and **WorkflowCommonParameters** .</span></span>

```powershell
workflow Test-Workflow {Get-Process}
Get-Command Test-Workflow -Syntax
```

```powershell
Test-Workflow [<WorkflowCommonParameters>] [<CommonParameters>]
```

<span data-ttu-id="ef054-180">工作流程一般參數包含多個執行工作流程的必要參數。</span><span class="sxs-lookup"><span data-stu-id="ef054-180">The workflow common parameters include several parameters that are essential to running workflows.</span></span> <span data-ttu-id="ef054-181">例如， **PSComputerName** 一般參數會指定工作流程影響的受管理節點。</span><span class="sxs-lookup"><span data-stu-id="ef054-181">For example, the **PSComputerName** common parameter specifies the managed nodes that the workflow affects.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02
}
```

<span data-ttu-id="ef054-182">**PSPersist** 工作流程一般參數會決定保存工作流程資料的時間。</span><span class="sxs-lookup"><span data-stu-id="ef054-182">The **PSPersist** workflow common parameter determines when workflow data is persisted.</span></span> <span data-ttu-id="ef054-183">它可讓您將活動之間的持續點新增至未定義持續點的工作流程。</span><span class="sxs-lookup"><span data-stu-id="ef054-183">It enables you to add persistence point between activities to workflows that don't define persistence points.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPersist:$True
}
```

<span data-ttu-id="ef054-184">其他工作流程一般參數可讓您指定受管理節點的遠端連線特性。</span><span class="sxs-lookup"><span data-stu-id="ef054-184">Other workflow common parameters let you specify the characteristics of the remote connection to the managed nodes.</span></span> <span data-ttu-id="ef054-185">它們的名稱和功能與遠端 Cmdlet 的參數類似，包括 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="ef054-185">Their names and functionality are similar to the parameters of remoting cmdlets, including `Invoke-Command`.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPort 443
}
```

<span data-ttu-id="ef054-186">請小心將為工作流程會話定義連接的遠端參數，與定義受管理節點連線的 **PS** 前置工作流程一般參數進行區分。</span><span class="sxs-lookup"><span data-stu-id="ef054-186">Take care to distinguish the remoting parameters that define the connection for the workflow session from the **PS-prefixed** workflow common parameters that define the connection to the managed nodes.</span></span>

```powershell
$ws = New-PSSession -ComputerName Server01 -ConfigurationName Microsoft.PowerShell.Workflow

Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSConfigurationName Microsoft.PowerShell.Workflow
}
```

<span data-ttu-id="ef054-187">某些工作流程一般參數對工作流程而言是唯一的，例如 **PSParameterCollection** 參數，可讓您為不同的遠端節點指定不同的工作流程一般參數值。</span><span class="sxs-lookup"><span data-stu-id="ef054-187">Some workflow common parameters are unique to workflows, such as the **PSParameterCollection** parameter that lets you specify different workflow common parameter values for different remote nodes.</span></span> <span data-ttu-id="ef054-188">如需工作流程一般參數的清單和說明，請參閱 [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="ef054-188">For a list and description of the workflow common parameters, see [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef054-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef054-189">See also</span></span>

[<span data-ttu-id="ef054-190">Invoke-AsWorkflow</span><span class="sxs-lookup"><span data-stu-id="ef054-190">Invoke-AsWorkflow</span></span>](xref:PSWorkflowUtility.Invoke-AsWorkflow)

[<span data-ttu-id="ef054-191">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="ef054-191">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

<span data-ttu-id="ef054-192">[PSWorkflow](xref:PSWorkflow) Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ef054-192">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="ef054-193">工作流程指南</span><span class="sxs-lookup"><span data-stu-id="ef054-193">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="ef054-194">撰寫 Windows PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="ef054-194">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
