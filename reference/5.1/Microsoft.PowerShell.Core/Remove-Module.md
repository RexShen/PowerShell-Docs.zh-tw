---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: a1052c357f19fd8f06eb39a14f8e8eded0c881a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202680"
---
# <span data-ttu-id="95b8a-103">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="95b8a-103">Remove-Module</span></span>

## <span data-ttu-id="95b8a-104">概要</span><span class="sxs-lookup"><span data-stu-id="95b8a-104">SYNOPSIS</span></span>
<span data-ttu-id="95b8a-105">移除目前工作階段的模組。</span><span class="sxs-lookup"><span data-stu-id="95b8a-105">Removes modules from the current session.</span></span>

## <span data-ttu-id="95b8a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="95b8a-106">SYNTAX</span></span>

### <span data-ttu-id="95b8a-107">NAME</span><span class="sxs-lookup"><span data-stu-id="95b8a-107">name</span></span>

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="95b8a-108">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="95b8a-108">FullyQualifiedName</span></span>

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="95b8a-109">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="95b8a-109">ModuleInfo</span></span>

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="95b8a-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="95b8a-110">DESCRIPTION</span></span>

<span data-ttu-id="95b8a-111">**Remove-Module** Cmdlet 會從目前的工作階段移除模組的成員，例如 Cmdlet 和函式。</span><span class="sxs-lookup"><span data-stu-id="95b8a-111">The **Remove-Module** cmdlet removes the members of a module, such as cmdlets and functions, from the current session.</span></span>

<span data-ttu-id="95b8a-112">如果模組包含組件 (.dll)，則會移除組件所實作的所有成員，但不會將組件解除載入。</span><span class="sxs-lookup"><span data-stu-id="95b8a-112">If the module includes an assembly (.dll), all members that are implemented by the assembly are removed, but the assembly is not unloaded.</span></span>

<span data-ttu-id="95b8a-113">此 Cmdlet 不會將模組解除安裝，或將它從電腦中刪除。</span><span class="sxs-lookup"><span data-stu-id="95b8a-113">This cmdlet does not uninstall the module or delete it from the computer.</span></span>
<span data-ttu-id="95b8a-114">它只會影響目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="95b8a-114">It affects only the current PowerShell session.</span></span>

## <span data-ttu-id="95b8a-115">範例</span><span class="sxs-lookup"><span data-stu-id="95b8a-115">EXAMPLES</span></span>

### <span data-ttu-id="95b8a-116">範例 1：移除模組</span><span class="sxs-lookup"><span data-stu-id="95b8a-116">Example 1: Remove a module</span></span>

```powershell
Remove-Module -Name "BitsTransfer"
```

<span data-ttu-id="95b8a-117">此命令從目前的工作階段移除 BitsTransfer 模組。</span><span class="sxs-lookup"><span data-stu-id="95b8a-117">This command removes the BitsTransfer module from the current session.</span></span>

### <span data-ttu-id="95b8a-118">範例 2：移除所有模組</span><span class="sxs-lookup"><span data-stu-id="95b8a-118">Example 2: Remove all modules</span></span>

```powershell
Get-Module | Remove-Module
```

<span data-ttu-id="95b8a-119">此命令從目前的工作階段移除所有模組。</span><span class="sxs-lookup"><span data-stu-id="95b8a-119">This command removes all modules from the current session.</span></span>

### <span data-ttu-id="95b8a-120">範例 3︰使用管線移除模組</span><span class="sxs-lookup"><span data-stu-id="95b8a-120">Example 3: Remove modules by using the pipeline</span></span>

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

<span data-ttu-id="95b8a-121">此命令從目前的工作階段移除 BitsTransfer 和 PSDiagnostics 模組。</span><span class="sxs-lookup"><span data-stu-id="95b8a-121">This command removes the BitsTransfer and PSDiagnostics modules from the current session.</span></span>

<span data-ttu-id="95b8a-122">命令使用管線運算子 (|) 將模組名稱傳送至 **Remove-Module** 。</span><span class="sxs-lookup"><span data-stu-id="95b8a-122">The command uses a pipeline operator (|) to send the module names to **Remove-Module** .</span></span>
<span data-ttu-id="95b8a-123">它使用 *Verbose* 一般參數，取得所移除之成員的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="95b8a-123">It uses the *Verbose* common parameter to get detailed information about the members that are removed.</span></span>

<span data-ttu-id="95b8a-124">*Verbose* 訊息會顯示已移除的項目。</span><span class="sxs-lookup"><span data-stu-id="95b8a-124">The *Verbose* messages show the items that are removed.</span></span>
<span data-ttu-id="95b8a-125">這些訊息會有所不同，因為 BitsTransfer 模組包含一個實作其 Cmdlet 的組件，以及一個含有自己的組件的巢狀模組。</span><span class="sxs-lookup"><span data-stu-id="95b8a-125">The messages differ because the BitsTransfer module includes an assembly that implements its cmdlets and a nested module with its own assembly.</span></span>
<span data-ttu-id="95b8a-126">PSDiagnostics 模組則包含可匯出函式的模組指令檔 (.psm1)。</span><span class="sxs-lookup"><span data-stu-id="95b8a-126">The PSDiagnostics module includes a module script file (.psm1) that exports functions.</span></span>

### <span data-ttu-id="95b8a-127">範例 4︰使用 ModuleInfo 移除模組</span><span class="sxs-lookup"><span data-stu-id="95b8a-127">Example 4: Remove a module by using ModuleInfo</span></span>

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

<span data-ttu-id="95b8a-128">此命令會使用 *ModuleInfo* 參數移除 BitsTransfer 模組。</span><span class="sxs-lookup"><span data-stu-id="95b8a-128">This command uses the *ModuleInfo* parameter to remove the BitsTransfer module.</span></span>

## <span data-ttu-id="95b8a-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="95b8a-129">PARAMETERS</span></span>

### <span data-ttu-id="95b8a-130">-Force</span><span class="sxs-lookup"><span data-stu-id="95b8a-130">-Force</span></span>

<span data-ttu-id="95b8a-131">指出此 Cmdlet 會移除唯讀模組。</span><span class="sxs-lookup"><span data-stu-id="95b8a-131">Indicates that this cmdlet removes read-only modules.</span></span>
<span data-ttu-id="95b8a-132">**Remove-Module** 預設只會移除讀寫模組。</span><span class="sxs-lookup"><span data-stu-id="95b8a-132">By default, **Remove-Module** removes only read-write modules.</span></span>

<span data-ttu-id="95b8a-133">**ReadOnly** 和 **ReadWrite** 值是儲存在模組的 **AccessMode** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="95b8a-133">The **ReadOnly** and **ReadWrite** values are stored in **AccessMode** property of a module.</span></span>

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

### <span data-ttu-id="95b8a-134">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="95b8a-134">-FullyQualifiedName</span></span>

<span data-ttu-id="95b8a-135">指定要移除之模組的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="95b8a-135">Specifies the fully qualified names of modules to remove.</span></span>

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

### <span data-ttu-id="95b8a-136">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="95b8a-136">-ModuleInfo</span></span>

<span data-ttu-id="95b8a-137">指定要移除的模組物件。</span><span class="sxs-lookup"><span data-stu-id="95b8a-137">Specifies the module objects to remove.</span></span>
<span data-ttu-id="95b8a-138">輸入包含模組物件 ( **PSModuleInfo** ) 的變數，或輸入可取得模組物件的命令，例如 Get-Module 命令。</span><span class="sxs-lookup"><span data-stu-id="95b8a-138">Enter a variable that contains a module object ( **PSModuleInfo** ) or a command that gets a module object, such as a Get-Module command.</span></span>
<span data-ttu-id="95b8a-139">您也可以使用管線將模組物件傳送至 **Remove-Module** 。</span><span class="sxs-lookup"><span data-stu-id="95b8a-139">You can also pipe module objects to **Remove-Module** .</span></span>

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

### <span data-ttu-id="95b8a-140">-Name</span><span class="sxs-lookup"><span data-stu-id="95b8a-140">-Name</span></span>

<span data-ttu-id="95b8a-141">指定要移除之模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="95b8a-141">Specifies the names of modules to remove.</span></span>
<span data-ttu-id="95b8a-142">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="95b8a-142">Wildcard characters are permitted.</span></span>
<span data-ttu-id="95b8a-143">您也可以使用管線將名稱字串傳送至 **Remove-Module** 。</span><span class="sxs-lookup"><span data-stu-id="95b8a-143">You can also pipe name strings to **Remove-Module** .</span></span>

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

### <span data-ttu-id="95b8a-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="95b8a-144">-Confirm</span></span>

<span data-ttu-id="95b8a-145">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="95b8a-145">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="95b8a-146">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="95b8a-146">-WhatIf</span></span>

<span data-ttu-id="95b8a-147">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="95b8a-147">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="95b8a-148">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="95b8a-148">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="95b8a-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="95b8a-149">CommonParameters</span></span>

<span data-ttu-id="95b8a-150">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="95b8a-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="95b8a-151">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="95b8a-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="95b8a-152">輸入</span><span class="sxs-lookup"><span data-stu-id="95b8a-152">INPUTS</span></span>

### <span data-ttu-id="95b8a-153">System.String、System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="95b8a-153">System.String, System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="95b8a-154">您可以使用管線將模組名稱和模組物件傳送至 **Remove-Module** 。</span><span class="sxs-lookup"><span data-stu-id="95b8a-154">You can pipe module names and module objects to **Remove-Module** .</span></span>

## <span data-ttu-id="95b8a-155">輸出</span><span class="sxs-lookup"><span data-stu-id="95b8a-155">OUTPUTS</span></span>

### <span data-ttu-id="95b8a-156">無</span><span class="sxs-lookup"><span data-stu-id="95b8a-156">None</span></span>

<span data-ttu-id="95b8a-157">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="95b8a-157">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="95b8a-158">注意</span><span class="sxs-lookup"><span data-stu-id="95b8a-158">NOTES</span></span>

## <span data-ttu-id="95b8a-159">相關連結</span><span class="sxs-lookup"><span data-stu-id="95b8a-159">RELATED LINKS</span></span>

[<span data-ttu-id="95b8a-160">Get-Module</span><span class="sxs-lookup"><span data-stu-id="95b8a-160">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="95b8a-161">Import-Module</span><span class="sxs-lookup"><span data-stu-id="95b8a-161">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="95b8a-162">about_Modules</span><span class="sxs-lookup"><span data-stu-id="95b8a-162">about_Modules</span></span>](About/about_Modules.md)
