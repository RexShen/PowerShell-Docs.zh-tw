---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: b8577db1d44f0e7bd4571a080133fecaa282770b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201483"
---
# <span data-ttu-id="7eb3d-103">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="7eb3d-103">Remove-Module</span></span>

## <span data-ttu-id="7eb3d-104">概要</span><span class="sxs-lookup"><span data-stu-id="7eb3d-104">SYNOPSIS</span></span>
<span data-ttu-id="7eb3d-105">移除目前工作階段的模組。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-105">Removes modules from the current session.</span></span>

## <span data-ttu-id="7eb3d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7eb3d-106">SYNTAX</span></span>

### <span data-ttu-id="7eb3d-107">NAME</span><span class="sxs-lookup"><span data-stu-id="7eb3d-107">name</span></span>

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7eb3d-108">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="7eb3d-108">FullyQualifiedName</span></span>

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7eb3d-109">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="7eb3d-109">ModuleInfo</span></span>

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7eb3d-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7eb3d-110">DESCRIPTION</span></span>

<span data-ttu-id="7eb3d-111">**Remove-Module** Cmdlet 會從目前的工作階段移除模組的成員，例如 Cmdlet 和函式。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-111">The **Remove-Module** cmdlet removes the members of a module, such as cmdlets and functions, from the current session.</span></span>

<span data-ttu-id="7eb3d-112">如果模組包含組件 (.dll)，則會移除組件所實作的所有成員，但不會將組件解除載入。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-112">If the module includes an assembly (.dll), all members that are implemented by the assembly are removed, but the assembly is not unloaded.</span></span>

<span data-ttu-id="7eb3d-113">此 Cmdlet 不會將模組解除安裝，或將它從電腦中刪除。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-113">This cmdlet does not uninstall the module or delete it from the computer.</span></span>
<span data-ttu-id="7eb3d-114">它只會影響目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-114">It affects only the current PowerShell session.</span></span>

## <span data-ttu-id="7eb3d-115">範例</span><span class="sxs-lookup"><span data-stu-id="7eb3d-115">EXAMPLES</span></span>

### <span data-ttu-id="7eb3d-116">範例 1：移除模組</span><span class="sxs-lookup"><span data-stu-id="7eb3d-116">Example 1: Remove a module</span></span>

```powershell
Remove-Module -Name "BitsTransfer"
```

<span data-ttu-id="7eb3d-117">此命令從目前的工作階段移除 BitsTransfer 模組。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-117">This command removes the BitsTransfer module from the current session.</span></span>

### <span data-ttu-id="7eb3d-118">範例 2：移除所有模組</span><span class="sxs-lookup"><span data-stu-id="7eb3d-118">Example 2: Remove all modules</span></span>

```powershell
Get-Module | Remove-Module
```

<span data-ttu-id="7eb3d-119">此命令從目前的工作階段移除所有模組。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-119">This command removes all modules from the current session.</span></span>

### <span data-ttu-id="7eb3d-120">範例 3︰使用管線移除模組</span><span class="sxs-lookup"><span data-stu-id="7eb3d-120">Example 3: Remove modules by using the pipeline</span></span>

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

<span data-ttu-id="7eb3d-121">此命令從目前的工作階段移除 BitsTransfer 和 PSDiagnostics 模組。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-121">This command removes the BitsTransfer and PSDiagnostics modules from the current session.</span></span>

<span data-ttu-id="7eb3d-122">命令使用管線運算子 (|) 將模組名稱傳送至 **Remove-Module** 。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-122">The command uses a pipeline operator (|) to send the module names to **Remove-Module** .</span></span>
<span data-ttu-id="7eb3d-123">它使用 *Verbose* 一般參數，取得所移除之成員的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-123">It uses the *Verbose* common parameter to get detailed information about the members that are removed.</span></span>

<span data-ttu-id="7eb3d-124">*Verbose* 訊息會顯示已移除的項目。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-124">The *Verbose* messages show the items that are removed.</span></span>
<span data-ttu-id="7eb3d-125">這些訊息會有所不同，因為 BitsTransfer 模組包含一個實作其 Cmdlet 的組件，以及一個含有自己的組件的巢狀模組。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-125">The messages differ because the BitsTransfer module includes an assembly that implements its cmdlets and a nested module with its own assembly.</span></span>
<span data-ttu-id="7eb3d-126">PSDiagnostics 模組則包含可匯出函式的模組指令檔 (.psm1)。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-126">The PSDiagnostics module includes a module script file (.psm1) that exports functions.</span></span>

### <span data-ttu-id="7eb3d-127">範例 4︰使用 ModuleInfo 移除模組</span><span class="sxs-lookup"><span data-stu-id="7eb3d-127">Example 4: Remove a module by using ModuleInfo</span></span>

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

<span data-ttu-id="7eb3d-128">此命令會使用 *ModuleInfo* 參數移除 BitsTransfer 模組。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-128">This command uses the *ModuleInfo* parameter to remove the BitsTransfer module.</span></span>

## <span data-ttu-id="7eb3d-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7eb3d-129">PARAMETERS</span></span>

### <span data-ttu-id="7eb3d-130">-Force</span><span class="sxs-lookup"><span data-stu-id="7eb3d-130">-Force</span></span>

<span data-ttu-id="7eb3d-131">指出此 Cmdlet 會移除唯讀模組。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-131">Indicates that this cmdlet removes read-only modules.</span></span>
<span data-ttu-id="7eb3d-132">**Remove-Module** 預設只會移除讀寫模組。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-132">By default, **Remove-Module** removes only read-write modules.</span></span>

<span data-ttu-id="7eb3d-133">**ReadOnly** 和 **ReadWrite** 值是儲存在模組的 **AccessMode** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-133">The **ReadOnly** and **ReadWrite** values are stored in **AccessMode** property of a module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7eb3d-134">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="7eb3d-134">-FullyQualifiedName</span></span>

<span data-ttu-id="7eb3d-135">指定要移除之模組的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-135">Specifies the fully qualified names of modules to remove.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7eb3d-136">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="7eb3d-136">-ModuleInfo</span></span>

<span data-ttu-id="7eb3d-137">指定要移除的模組物件。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-137">Specifies the module objects to remove.</span></span>
<span data-ttu-id="7eb3d-138">輸入包含模組物件 ( **PSModuleInfo** ) 的變數，或輸入可取得模組物件的命令，例如 Get-Module 命令。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-138">Enter a variable that contains a module object ( **PSModuleInfo** ) or a command that gets a module object, such as a Get-Module command.</span></span>
<span data-ttu-id="7eb3d-139">您也可以使用管線將模組物件傳送至 **Remove-Module** 。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-139">You can also pipe module objects to **Remove-Module** .</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7eb3d-140">-Name</span><span class="sxs-lookup"><span data-stu-id="7eb3d-140">-Name</span></span>

<span data-ttu-id="7eb3d-141">指定要移除之模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-141">Specifies the names of modules to remove.</span></span>
<span data-ttu-id="7eb3d-142">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-142">Wildcard characters are permitted.</span></span>
<span data-ttu-id="7eb3d-143">您也可以使用管線將名稱字串傳送至 **Remove-Module** 。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-143">You can also pipe name strings to **Remove-Module** .</span></span>

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="7eb3d-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7eb3d-144">-Confirm</span></span>

<span data-ttu-id="7eb3d-145">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-145">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7eb3d-146">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7eb3d-146">-WhatIf</span></span>

<span data-ttu-id="7eb3d-147">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-147">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7eb3d-148">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-148">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7eb3d-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7eb3d-149">CommonParameters</span></span>

<span data-ttu-id="7eb3d-150">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7eb3d-151">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7eb3d-152">輸入</span><span class="sxs-lookup"><span data-stu-id="7eb3d-152">INPUTS</span></span>

### <span data-ttu-id="7eb3d-153">System.String、System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="7eb3d-153">System.String, System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="7eb3d-154">您可以使用管線將模組名稱和模組物件傳送至 **Remove-Module** 。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-154">You can pipe module names and module objects to **Remove-Module** .</span></span>

## <span data-ttu-id="7eb3d-155">輸出</span><span class="sxs-lookup"><span data-stu-id="7eb3d-155">OUTPUTS</span></span>

### <span data-ttu-id="7eb3d-156">無</span><span class="sxs-lookup"><span data-stu-id="7eb3d-156">None</span></span>

<span data-ttu-id="7eb3d-157">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-157">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7eb3d-158">注意</span><span class="sxs-lookup"><span data-stu-id="7eb3d-158">NOTES</span></span>

<span data-ttu-id="7eb3d-159">移除模組時，模組上會執行的事件。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-159">When removing a module, there is an event on the module that will execute.</span></span>
<span data-ttu-id="7eb3d-160">此事件可讓模組回應移除並執行一些清除，例如釋出資源。</span><span class="sxs-lookup"><span data-stu-id="7eb3d-160">This event allows a module to react to being removed and perform some cleanup such as freeing up resources.</span></span> <span data-ttu-id="7eb3d-161">範例：</span><span class="sxs-lookup"><span data-stu-id="7eb3d-161">Example:</span></span>

<span data-ttu-id="7eb3d-162">$OnRemoveScript = {</span><span class="sxs-lookup"><span data-stu-id="7eb3d-162">$OnRemoveScript = {</span></span>

  <span data-ttu-id="7eb3d-163">\# 執行清除</span><span class="sxs-lookup"><span data-stu-id="7eb3d-163">\# perform cleanup</span></span>

  <span data-ttu-id="7eb3d-164">$cachedSessions |Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="7eb3d-164">$cachedSessions | Remove-PSSession</span></span>

<span data-ttu-id="7eb3d-165">}</span><span class="sxs-lookup"><span data-stu-id="7eb3d-165">}</span></span>

<span data-ttu-id="7eb3d-166">$ExecutionCoNtext. SessionState. OnRemove + = $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="7eb3d-166">$ExecutionContext.SessionState.Module.OnRemove += $OnRemoveScript</span></span>

<span data-ttu-id="7eb3d-167">為了達到絕對一致性，回應 PowerShell 進程的關閉可能也很有用：</span><span class="sxs-lookup"><span data-stu-id="7eb3d-167">For full consistency, it might be also useful to react to the closing of the PowerShell process:</span></span>

<span data-ttu-id="7eb3d-168">Register-EngineEvent-SourceIdentifier ( [PsEngineEvent]：：結束) -動作 $OnRemoveScript</span><span class="sxs-lookup"><span data-stu-id="7eb3d-168">Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Action $OnRemoveScript</span></span>

## <span data-ttu-id="7eb3d-169">相關連結</span><span class="sxs-lookup"><span data-stu-id="7eb3d-169">RELATED LINKS</span></span>

[<span data-ttu-id="7eb3d-170">Get-Module</span><span class="sxs-lookup"><span data-stu-id="7eb3d-170">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="7eb3d-171">Import-Module</span><span class="sxs-lookup"><span data-stu-id="7eb3d-171">Import-Module</span></span>](Import-Module.md)
