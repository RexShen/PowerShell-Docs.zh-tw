---
external help file: Microsoft.PowerShell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflowUtility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflowutility/invoke-asworkflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-AsWorkflow
ms.openlocfilehash: b96bce9fe4d574fe2b7e9c7c0f1e05ee0508adce
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202964"
---
# <span data-ttu-id="9f184-103">Invoke-AsWorkflow</span><span class="sxs-lookup"><span data-stu-id="9f184-103">Invoke-AsWorkflow</span></span>

## <span data-ttu-id="9f184-104">概要</span><span class="sxs-lookup"><span data-stu-id="9f184-104">SYNOPSIS</span></span>
<span data-ttu-id="9f184-105">以 Windows PowerShell 工作流程形式執行命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="9f184-105">Runs a command or expression as a Windows PowerShell Workflow.</span></span>

## <span data-ttu-id="9f184-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9f184-106">SYNTAX</span></span>

### <span data-ttu-id="9f184-107">Command (預設值)</span><span class="sxs-lookup"><span data-stu-id="9f184-107">Command (Default)</span></span>

```
Invoke-AsWorkflow [-CommandName <String>] [-Parameter <Hashtable>] [-InputObject <Object>] [<CommonParameters>]
```

### <span data-ttu-id="9f184-108">運算式</span><span class="sxs-lookup"><span data-stu-id="9f184-108">Expression</span></span>

```
Invoke-AsWorkflow [-Expression <String>] [-InputObject <Object>] [<CommonParameters>]
```

## <span data-ttu-id="9f184-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9f184-109">DESCRIPTION</span></span>

<span data-ttu-id="9f184-110">`Invoke-AsWorkflow`工作流程會以工作流程中的內嵌腳本形式執行任何命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="9f184-110">The `Invoke-AsWorkflow` workflow runs any command or expression as an inline script in a workflow.</span></span>
<span data-ttu-id="9f184-111">這些工作流程使用標準工作流程語意、具有所有工作流程一般參數，而且具有工作流程的所有優點 (包括可停止、繼續及復原的功能)。</span><span class="sxs-lookup"><span data-stu-id="9f184-111">These workflows use the standard workflow semantics, have all workflow common parameters, and have all benefits of workflows, including the ability to stop, resume, and recover.</span></span>

<span data-ttu-id="9f184-112">工作流程是針對長時間執行的命令 (這些命令通常用來收集重要資料) 所設計，但也可用來執行任何命令。</span><span class="sxs-lookup"><span data-stu-id="9f184-112">Workflows are designed for long-running commands that collect critical data, but can be used to run any command.</span></span>
<span data-ttu-id="9f184-113">如需詳細資訊，請參閱 [about_Workflows](../PSWorkflow/About/about_Workflows.md)。</span><span class="sxs-lookup"><span data-stu-id="9f184-113">For more information, see [about_Workflows](../PSWorkflow/About/about_Workflows.md).</span></span>

<span data-ttu-id="9f184-114">您也可以新增工作流程一般參數到此命令。</span><span class="sxs-lookup"><span data-stu-id="9f184-114">You can also add workflow common parameters to this command.</span></span>
<span data-ttu-id="9f184-115">如需工作流程一般參數的詳細資訊，請參閱 [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="9f184-115">For more information about workflow common parameters, see [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)</span></span>

<span data-ttu-id="9f184-116">此工作流程是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9f184-116">This workflow is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="9f184-117">範例</span><span class="sxs-lookup"><span data-stu-id="9f184-117">EXAMPLES</span></span>

### <span data-ttu-id="9f184-118">範例 1：以工作流程形式執行 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9f184-118">Example 1: Run a cmdlet as a workflow</span></span>

```powershell
Invoke-AsWorkflow -PSComputerName (Get-Content Servers.txt) -CommandName Get-ExecutionPolicy
```

```output
PSComputerName                     PSSourceJobInstanceId                   Value
--------------                     ---------------------                   -----
Server01                           77b1cdf8-8226-4662-9067-cd2fa5c3b711    AllSigned
Server02                           a33542d7-3cdd-4339-ab99-0e7cd8e59462    Unrestricted
Server03                           279bac28-066a-4646-9497-8fcdcfe9757e    AllSigned
localhost                          0d858009-2cc4-47a4-a2e0-da17dc2883d0    RemoteSigned
```

<span data-ttu-id="9f184-119">此命令會 `Get-ExecutionPolicy` 在數百部電腦上以工作流程形式執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9f184-119">This command runs the `Get-ExecutionPolicy` cmdlet as a workflow on hundreds of computers.</span></span>

<span data-ttu-id="9f184-120">此命令會使用 **CommandName** 參數來指定要在工作流程中執行的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9f184-120">The command uses the **CommandName** parameter to specify the cmdlet that runs in the workflow.</span></span>
<span data-ttu-id="9f184-121">它會使用 **PSComputerName** 工作流程一般參數來指定要在其上執行命令的電腦。</span><span class="sxs-lookup"><span data-stu-id="9f184-121">It uses the **PSComputerName** workflow common parameter to specify the computers on which the command runs.</span></span>
<span data-ttu-id="9f184-122">**PSComputerName** 參數的值是一個 `Get-Content` 命令，可從 Servers.txt 檔案中取得電腦名稱稱清單。</span><span class="sxs-lookup"><span data-stu-id="9f184-122">The value of the **PSComputerName** parameter is a `Get-Content` command that gets a list of computer names from the Servers.txt file.</span></span>
<span data-ttu-id="9f184-123">參數值會以括弧括住，以在 `Get-Command` 使用值之前直接 Windows PowerShell 執行命令。</span><span class="sxs-lookup"><span data-stu-id="9f184-123">The parameter value is enclosed in parentheses to direct Windows PowerShell to run the `Get-Command` command before using the value.</span></span>

<span data-ttu-id="9f184-124">類似所有遠端命令，若命令在本機電腦上執行 (若 PSComputerName 參數的值包含本機電腦)，您必須使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9f184-124">As with all remote commands, if the command runs on the local computer, (if the value of the PSComputerName parameter includes the local computer), you must start Windows PowerShell with the "Run as administrator" option.</span></span>

### <span data-ttu-id="9f184-125">範例 2：執行具有參數的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9f184-125">Example 2: Run a cmdlet with parameters</span></span>

```powershell
$s = Import-Csv .\Servers.csv -Header ServerName, ServerID
Invoke-AsWorkflow -CommandName Get-ExecutionPolicy -Parameter @{Scope="Process"} -PSComputerName {$s.ServerName} -PSConnectionRetryCount 5
```

<span data-ttu-id="9f184-126">第一個命令會使用 `Import-Csv` Cmdlet 從 Servers.csv 檔案中的內容建立物件。</span><span class="sxs-lookup"><span data-stu-id="9f184-126">The first command uses the `Import-Csv` cmdlet to create an object from the content in the Servers.csv file.</span></span> <span data-ttu-id="9f184-127">此命令會使用 `Header` 參數來建立資料 `ServerName` 行的屬性，該資料行包含目的電腦的名稱，也稱為「遠端節點」。</span><span class="sxs-lookup"><span data-stu-id="9f184-127">The command uses the `Header` parameter to create a `ServerName` property for the column that contains the names of the target computers, also known as "remote nodes."</span></span> <span data-ttu-id="9f184-128">命令會將結果儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="9f184-128">The command saves the result in the `$s` variable.</span></span>

<span data-ttu-id="9f184-129">第二個命令會使用 `Invoke-AsWorkflow` 工作流程在 `Get-ExecutionPolicy` Servers.csv 檔案中的電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="9f184-129">The second command uses the `Invoke-AsWorkflow` workflow to run a `Get-ExecutionPolicy` command on the computers in the Servers.csv file.</span></span> <span data-ttu-id="9f184-130">命令使用的 **CommandName** 參數 `Invoke-AsWorkflow`  來指定要在工作流程中執行的命令。</span><span class="sxs-lookup"><span data-stu-id="9f184-130">The command uses the **CommandName** parameter of `Invoke-AsWorkflow`  to specify the command to run in the workflow.</span></span> <span data-ttu-id="9f184-131">它會使用的 `Parameter` 參數 `Invoke-AsWorkflow` ，以 `Scope` 進程的值指定 `Get-ExecutionPolicy` Cmdlet 的參數。 **Process** 此命令也會使用 `PSConnectionRetryCount` 工作流程一般參數，將每個電腦的命令限制為五次，並使用 `PSComputerName` 工作流程一般參數來指定遠端節點的名稱， (目的電腦) 。</span><span class="sxs-lookup"><span data-stu-id="9f184-131">It uses the `Parameter` parameter of `Invoke-AsWorkflow` to specify the `Scope` parameter of the `Get-ExecutionPolicy` cmdlet with a value of **Process** .The command also uses the `PSConnectionRetryCount` workflow common parameter to limit the command to five attempts on each computer and the `PSComputerName` workflow common parameter to specify the names of the remote nodes (target computers).</span></span> <span data-ttu-id="9f184-132">參數的值 `PSComputerName` 是可取得 `ServerName` 變數中每個物件之屬性的運算式 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="9f184-132">The value of the `PSComputerName` parameter is an expression that gets the `ServerName` property of every object in the `$s` variable.</span></span>

<span data-ttu-id="9f184-133">這些命令會以 `Get-ExecutionPolicy` 工作流程的形式在數百部電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="9f184-133">These commands run a `Get-ExecutionPolicy` command as a workflow on hundreds of computers.</span></span>
<span data-ttu-id="9f184-134">此命令會使用 `Scope` Cmdlet 的參數搭配 `Get-ExecutionPolicy` **Process** 值，以取得目前會話中的執行原則。</span><span class="sxs-lookup"><span data-stu-id="9f184-134">The command uses the `Scope` parameter of the `Get-ExecutionPolicy` cmdlet with a value of **Process** to get the execution policy in the current session.</span></span>

### <span data-ttu-id="9f184-135">範例 3：以工作流程形式執行運算式</span><span class="sxs-lookup"><span data-stu-id="9f184-135">Example 3: Run an expression as a workflow</span></span>

```powershell
Invoke-AsWorkflow -Expression "ipconfig /all" -PSComputerName (Get-Content DomainControllers.txt) -AsJob -JobName IPConfig
```

```output
Id     Name          PSJobTypeName   State         HasMoreData   Location                Command
--     ----          -------------   -----         -----------   --------                -------
2      IpConfig      PSWorkflowJob   Completed     True          Server01, Server01...   Invoke-AsWorkflow
```

<span data-ttu-id="9f184-136">此命令會使用 `Invoke-AsWorkflow` 工作流程來執行 Ipconfig 命令，做為 DomainControllers.txt 檔中所列電腦上的工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="9f184-136">This command uses the `Invoke-AsWorkflow` workflow to run an Ipconfig command as a workflow job on the computers listed in the DomainControllers.txt file.</span></span>

<span data-ttu-id="9f184-137">此命令會使用 `Expression` 參數來指定要執行的運算式。</span><span class="sxs-lookup"><span data-stu-id="9f184-137">The command uses the `Expression` parameter to specify the expression to run.</span></span>
<span data-ttu-id="9f184-138">它會使用 `PSComputerName` 工作流程一般參數來指定遠端節點 (目的電腦) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f184-138">It uses the `PSComputerName` workflow common parameter to specify the names of the remote nodes (target computers).</span></span>

<span data-ttu-id="9f184-139">此命令也會使用 `AsJob` 和 `JobName` 工作流程一般參數，以 "Ipconfig" 工作名稱在每部電腦上以背景工作的形式執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="9f184-139">The command also uses the `AsJob` and `JobName` workflow common parameters to run the workflow as a background job on each computer with the "Ipconfig" job name.</span></span>

<span data-ttu-id="9f184-140">此命令會傳回 `ContainerParentJob` (`System.Management.Automation.ContainerParentJob`) 的物件，其中包含每一部電腦上的工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="9f184-140">The command returns a `ContainerParentJob` object (`System.Management.Automation.ContainerParentJob`) that contains the workflow jobs on each computer.</span></span>

## <span data-ttu-id="9f184-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9f184-141">PARAMETERS</span></span>

### <span data-ttu-id="9f184-142">-CommandName</span><span class="sxs-lookup"><span data-stu-id="9f184-142">-CommandName</span></span>

<span data-ttu-id="9f184-143">以工作流程形式執行指定的 Cmdlet 或進階函式。</span><span class="sxs-lookup"><span data-stu-id="9f184-143">Runs the specified cmdlet or advanced function as a workflow.</span></span>
<span data-ttu-id="9f184-144">輸入 Cmdlet 或函數名稱，例如 `Update-Help` 、 `Set-ExecutionPolicy` 或 `Set-NetFirewallRule` 。</span><span class="sxs-lookup"><span data-stu-id="9f184-144">Enter the cmdlet or function name, such as `Update-Help`, `Set-ExecutionPolicy`, or `Set-NetFirewallRule`.</span></span>

```yaml
Type: System.String
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f184-145">-Expression</span><span class="sxs-lookup"><span data-stu-id="9f184-145">-Expression</span></span>

<span data-ttu-id="9f184-146">指定此 Cmdlet 做為工作流程執行的運算式。</span><span class="sxs-lookup"><span data-stu-id="9f184-146">Specifies the  expression that this cmdlet runs as a workflow.</span></span>
<span data-ttu-id="9f184-147">以字串形式輸入運算式，例如 `"ipconfig /all"` 。</span><span class="sxs-lookup"><span data-stu-id="9f184-147">Enter the expression as a string, such as `"ipconfig /all"`.</span></span>
<span data-ttu-id="9f184-148">若運算式包含空格或特殊字元，請將運算式括在引號中。</span><span class="sxs-lookup"><span data-stu-id="9f184-148">If the expression includes spaces or special characters, enclose the expression in quotation marks.</span></span>

```yaml
Type: System.String
Parameter Sets: Expression
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f184-149">-Parameter</span><span class="sxs-lookup"><span data-stu-id="9f184-149">-Parameter</span></span>

<span data-ttu-id="9f184-150">指定參數中所指定之命令的參數和參數值 `CommandName` 。</span><span class="sxs-lookup"><span data-stu-id="9f184-150">Specifies the parameters and parameter values of the command that is specified in the `CommandName` parameter.</span></span>
<span data-ttu-id="9f184-151">輸入雜湊表，其中每個索引鍵都是參數名稱，而其值為參數值，例如 `@{ExecutionPolicy="AllSigned"}` 。</span><span class="sxs-lookup"><span data-stu-id="9f184-151">Enter a hash table in which each key is a parameter name and its value is the parameter value, such as `@{ExecutionPolicy="AllSigned"}`.</span></span>

<span data-ttu-id="9f184-152">如需雜湊表的相關資訊，請參閱 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。</span><span class="sxs-lookup"><span data-stu-id="9f184-152">For information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Command
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f184-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9f184-153">-InputObject</span></span>

<span data-ttu-id="9f184-154">用來允許管線輸入。</span><span class="sxs-lookup"><span data-stu-id="9f184-154">Used to allows pipeline input.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9f184-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9f184-155">CommonParameters</span></span>

<span data-ttu-id="9f184-156">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9f184-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9f184-157">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="9f184-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

### <span data-ttu-id="9f184-158">WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="9f184-158">WorkflowCommonParameters</span></span>

<span data-ttu-id="9f184-159">此 Cmdlet 也支援工作流程特定的一般參數。</span><span class="sxs-lookup"><span data-stu-id="9f184-159">This cmdlet also supports workflow specific common parameters.</span></span>
<span data-ttu-id="9f184-160">如需詳細資訊，請參閱 [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="9f184-160">For information, see [about_WorkflowCommonParameters](../PSWorkflow/About/about_WorkflowCommonParameters.md).</span></span>

## <span data-ttu-id="9f184-161">輸入</span><span class="sxs-lookup"><span data-stu-id="9f184-161">INPUTS</span></span>

### <span data-ttu-id="9f184-162">System.Object</span><span class="sxs-lookup"><span data-stu-id="9f184-162">System.Object</span></span>

<span data-ttu-id="9f184-163">您可以透過管線將任何物件傳送至 `InputObject` 參數。</span><span class="sxs-lookup"><span data-stu-id="9f184-163">You can pipe any object to the `InputObject` parameter.</span></span>

## <span data-ttu-id="9f184-164">輸出</span><span class="sxs-lookup"><span data-stu-id="9f184-164">OUTPUTS</span></span>

### <span data-ttu-id="9f184-165">無</span><span class="sxs-lookup"><span data-stu-id="9f184-165">None</span></span>

<span data-ttu-id="9f184-166">此命令不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="9f184-166">This command does not generate any output.</span></span>
<span data-ttu-id="9f184-167">不過，它會執行工作流程，工作流程可能會產生輸出。</span><span class="sxs-lookup"><span data-stu-id="9f184-167">However, it runs the workflow, which might generate output.</span></span>

## <span data-ttu-id="9f184-168">注意</span><span class="sxs-lookup"><span data-stu-id="9f184-168">NOTES</span></span>

## <span data-ttu-id="9f184-169">相關連結</span><span class="sxs-lookup"><span data-stu-id="9f184-169">RELATED LINKS</span></span>

[<span data-ttu-id="9f184-170">New-PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="9f184-170">New-PSWorkflowExecutionOption</span></span>](../PSWorkflow/New-PSWorkflowExecutionOption.md)

[<span data-ttu-id="9f184-171">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="9f184-171">New-PSWorkflowSession</span></span>](../PSWorkflow/New-PSWorkflowSession.md)

[<span data-ttu-id="9f184-172">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="9f184-172">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="9f184-173">about_Workflow_Common_Parameters</span><span class="sxs-lookup"><span data-stu-id="9f184-173">about_Workflow_Common_Parameters</span></span>](../PSWorkflow/About/about_WorkflowCommonParameters.md)
