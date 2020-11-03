---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-executionpolicy?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-executionpolicy
ms.openlocfilehash: a846c3605c4adf469b12bfadaa3f90e585558dea
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204755"
---
# <span data-ttu-id="2fad8-103">Get-executionpolicy</span><span class="sxs-lookup"><span data-stu-id="2fad8-103">Get-ExecutionPolicy</span></span>

## <span data-ttu-id="2fad8-104">概要</span><span class="sxs-lookup"><span data-stu-id="2fad8-104">SYNOPSIS</span></span>
<span data-ttu-id="2fad8-105">取得目前工作階段的執行原則。</span><span class="sxs-lookup"><span data-stu-id="2fad8-105">Gets the execution policies for the current session.</span></span>

## <span data-ttu-id="2fad8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2fad8-106">SYNTAX</span></span>

### <span data-ttu-id="2fad8-107">全部</span><span class="sxs-lookup"><span data-stu-id="2fad8-107">All</span></span>

```
Get-ExecutionPolicy [[-Scope] <ExecutionPolicyScope>] [-List] [<CommonParameters>]
```

## <span data-ttu-id="2fad8-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2fad8-108">DESCRIPTION</span></span>

<span data-ttu-id="2fad8-109">若要以優先順序順序顯示每個範圍的執行原則，請使用 `Get-ExecutionPolicy -List` 。</span><span class="sxs-lookup"><span data-stu-id="2fad8-109">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="2fad8-110">若要查看適用于 PowerShell 會話的有效執行原則，請使用 `Get-ExecutionPolicy` 沒有參數的。</span><span class="sxs-lookup"><span data-stu-id="2fad8-110">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

<span data-ttu-id="2fad8-111">有效的執行原則取決於由設定的執行原則， `Set-ExecutionPolicy` 以及群組原則設定。</span><span class="sxs-lookup"><span data-stu-id="2fad8-111">The effective execution policy is determined by execution policies that are set by `Set-ExecutionPolicy` and Group Policy settings.</span></span>

<span data-ttu-id="2fad8-112">如需詳細資訊，請參閱 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="2fad8-112">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="2fad8-113">範例</span><span class="sxs-lookup"><span data-stu-id="2fad8-113">EXAMPLES</span></span>

### <span data-ttu-id="2fad8-114">範例1：取得所有執行原則</span><span class="sxs-lookup"><span data-stu-id="2fad8-114">Example 1: Get all execution policies</span></span>

<span data-ttu-id="2fad8-115">此命令顯示每個範圍的執行原則（依優先順序排列）。</span><span class="sxs-lookup"><span data-stu-id="2fad8-115">This command displays the execution policies for each scope in the order of precedence.</span></span>

```powershell
Get-ExecutionPolicy -List
```

```Output
Scope          ExecutionPolicy
-----          ---------------
MachinePolicy  Undefined
UserPolicy     Undefined
Process        Undefined
CurrentUser    AllSigned
LocalMachine   Undefined
```

<span data-ttu-id="2fad8-116">此 `Get-ExecutionPolicy` Cmdlet 會使用 **List** 參數來顯示每個範圍的執行原則。</span><span class="sxs-lookup"><span data-stu-id="2fad8-116">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span>

### <span data-ttu-id="2fad8-117">範例2：設定執行原則</span><span class="sxs-lookup"><span data-stu-id="2fad8-117">Example 2: Set an execution policy</span></span>

<span data-ttu-id="2fad8-118">此範例顯示如何設定本機電腦的執行原則。</span><span class="sxs-lookup"><span data-stu-id="2fad8-118">This example shows how to set an execution policy for the local computer.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="2fad8-119">此 `Set-ExecutionPolicy` Cmdlet 會使用 **ExecutionPolicy** 參數來指定 **RemoteSigned** 原則。</span><span class="sxs-lookup"><span data-stu-id="2fad8-119">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="2fad8-120">**Scope** 參數會指定預設的範圍值： **LocalMachine** 。</span><span class="sxs-lookup"><span data-stu-id="2fad8-120">The **Scope** parameter specifies the default scope value, **LocalMachine** .</span></span> <span data-ttu-id="2fad8-121">若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。</span><span class="sxs-lookup"><span data-stu-id="2fad8-121">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="2fad8-122">範例3：取得有效的執行原則</span><span class="sxs-lookup"><span data-stu-id="2fad8-122">Example 3: Get the effective execution policy</span></span>

<span data-ttu-id="2fad8-123">此範例說明如何顯示 PowerShell 會話的有效執行原則。</span><span class="sxs-lookup"><span data-stu-id="2fad8-123">This example shows how to display the effective execution policy for a PowerShell session.</span></span>

```
PS> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       AllSigned
 LocalMachine    RemoteSigned

PS> Get-ExecutionPolicy

AllSigned
```

<span data-ttu-id="2fad8-124">此 `Get-ExecutionPolicy` Cmdlet 會使用 **List** 參數來顯示每個範圍的執行原則。</span><span class="sxs-lookup"><span data-stu-id="2fad8-124">The `Get-ExecutionPolicy` cmdlet uses the **List** parameter to display each scope's execution policy.</span></span> <span data-ttu-id="2fad8-125">此 `Get-ExecutionPolicy` Cmdlet 會在沒有參數的情況下執行，以顯示有效的執行原則 **AllSigned** 。</span><span class="sxs-lookup"><span data-stu-id="2fad8-125">The `Get-ExecutionPolicy` cmdlet is run without a parameter to display the effective execution policy, **AllSigned** .</span></span>

### <span data-ttu-id="2fad8-126">範例4：解除封鎖腳本以在不變更執行原則的情況下執行</span><span class="sxs-lookup"><span data-stu-id="2fad8-126">Example 4: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="2fad8-127">此範例顯示 **RemoteSigned** 執行原則如何防止您執行未簽署的腳本。</span><span class="sxs-lookup"><span data-stu-id="2fad8-127">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="2fad8-128">最佳做法是先閱讀腳本的程式碼，並確認它是安全的，然後 **再** 使用 `Unblock-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2fad8-128">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="2fad8-129">此 `Unblock-File` Cmdlet 會解除封鎖腳本，使其可執行，但不會變更執行原則。</span><span class="sxs-lookup"><span data-stu-id="2fad8-129">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

```
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

.\Start-ActivityTracker.ps1 : File .\Start-ActivityTracker.ps1 cannot be loaded.
The file .\Start-ActivityTracker.ps1 is not digitally signed.
The script will not execute on the system.
For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], PSSecurityException
+ FullyQualifiedErrorId : UnauthorizedAccess

PS> Unblock-File -Path .\Start-ActivityTracker.ps1

PS> Get-ExecutionPolicy

RemoteSigned

PS> .\Start-ActivityTracker.ps1

Task 1:
```

<span data-ttu-id="2fad8-130">`Set-ExecutionPolicy`使用 **ExecutionPolicy** 參數來指定 **RemoteSigned** 原則。</span><span class="sxs-lookup"><span data-stu-id="2fad8-130">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="2fad8-131">設定預設範圍 **LocalMachine** 的原則。</span><span class="sxs-lookup"><span data-stu-id="2fad8-131">The policy is set for the default scope, **LocalMachine** .</span></span>

<span data-ttu-id="2fad8-132">此 `Get-ExecutionPolicy` Cmdlet 會顯示 **RemoteSigned** 是目前 PowerShell 會話的有效執行原則。</span><span class="sxs-lookup"><span data-stu-id="2fad8-132">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="2fad8-133">**Start-ActivityTracker.ps1** 的腳本會從目前的目錄執行。</span><span class="sxs-lookup"><span data-stu-id="2fad8-133">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="2fad8-134">因為腳本未經過數位簽署，所以 **RemoteSigned** 會封鎖腳本。</span><span class="sxs-lookup"><span data-stu-id="2fad8-134">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="2fad8-135">在此範例中，腳本的程式碼已被審核並驗證為可安全執行。</span><span class="sxs-lookup"><span data-stu-id="2fad8-135">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="2fad8-136">此 `Unblock-File` Cmdlet 會使用 **Path** 參數將腳本解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="2fad8-136">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="2fad8-137">若要確認 `Unblock-File` 未變更執行原則，請 `Get-ExecutionPolicy` 顯示有效的執行原則 **RemoteSigned** 。</span><span class="sxs-lookup"><span data-stu-id="2fad8-137">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned** .</span></span>

<span data-ttu-id="2fad8-138">腳本 **Start-ActivityTracker.ps1** 會從目前的目錄執行。</span><span class="sxs-lookup"><span data-stu-id="2fad8-138">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="2fad8-139">腳本開始執行的原因是 Cmdlet 已解除封鎖 `Unblock-File` 。</span><span class="sxs-lookup"><span data-stu-id="2fad8-139">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="2fad8-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2fad8-140">PARAMETERS</span></span>

### <span data-ttu-id="2fad8-141">-List</span><span class="sxs-lookup"><span data-stu-id="2fad8-141">-List</span></span>

<span data-ttu-id="2fad8-142">取得工作階段的所有執行原則值，依照優先順序列出。</span><span class="sxs-lookup"><span data-stu-id="2fad8-142">Gets all execution policy values for the session listed in precedence order.</span></span> <span data-ttu-id="2fad8-143">根據預設， `Get-ExecutionPolicy` 只會取得有效的執行原則。</span><span class="sxs-lookup"><span data-stu-id="2fad8-143">By default, `Get-ExecutionPolicy` gets only the effective execution policy.</span></span>

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

### <span data-ttu-id="2fad8-144">-Scope</span><span class="sxs-lookup"><span data-stu-id="2fad8-144">-Scope</span></span>

<span data-ttu-id="2fad8-145">指定受執行原則影響的範圍。</span><span class="sxs-lookup"><span data-stu-id="2fad8-145">Specifies the scope that is affected by an execution policy.</span></span>

<span data-ttu-id="2fad8-146">有效的執行原則取決於優先順序順序，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2fad8-146">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="2fad8-147">**MachinePolicy** 。</span><span class="sxs-lookup"><span data-stu-id="2fad8-147">**MachinePolicy** .</span></span> <span data-ttu-id="2fad8-148">由電腦的所有使用者的群組原則設定。</span><span class="sxs-lookup"><span data-stu-id="2fad8-148">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="2fad8-149">**>userpolicy** 。</span><span class="sxs-lookup"><span data-stu-id="2fad8-149">**UserPolicy** .</span></span> <span data-ttu-id="2fad8-150">由電腦目前使用者的群組原則設定。</span><span class="sxs-lookup"><span data-stu-id="2fad8-150">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="2fad8-151">**處理** 。</span><span class="sxs-lookup"><span data-stu-id="2fad8-151">**Process** .</span></span> <span data-ttu-id="2fad8-152">只會影響目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="2fad8-152">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="2fad8-153">**CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="2fad8-153">**CurrentUser** .</span></span> <span data-ttu-id="2fad8-154">只會影響目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="2fad8-154">Affects only the current user.</span></span>
- <span data-ttu-id="2fad8-155">**LocalMachine** 。</span><span class="sxs-lookup"><span data-stu-id="2fad8-155">**LocalMachine** .</span></span> <span data-ttu-id="2fad8-156">預設範圍會影響電腦的所有使用者。</span><span class="sxs-lookup"><span data-stu-id="2fad8-156">Default scope that affects all users of the computer.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 0
Default value: Effective execution policy
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2fad8-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2fad8-157">CommonParameters</span></span>

<span data-ttu-id="2fad8-158">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2fad8-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2fad8-159">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2fad8-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2fad8-160">輸入</span><span class="sxs-lookup"><span data-stu-id="2fad8-160">INPUTS</span></span>

### <span data-ttu-id="2fad8-161">無</span><span class="sxs-lookup"><span data-stu-id="2fad8-161">None</span></span>

<span data-ttu-id="2fad8-162">`Get-ExecutionPolicy` 不接受來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="2fad8-162">`Get-ExecutionPolicy` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="2fad8-163">輸出</span><span class="sxs-lookup"><span data-stu-id="2fad8-163">OUTPUTS</span></span>

### <span data-ttu-id="2fad8-164">Microsoft.PowerShell.ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="2fad8-164">Microsoft.PowerShell.ExecutionPolicy</span></span>

## <span data-ttu-id="2fad8-165">注意</span><span class="sxs-lookup"><span data-stu-id="2fad8-165">NOTES</span></span>

<span data-ttu-id="2fad8-166">執行原則是 PowerShell 安全性策略的一部分。</span><span class="sxs-lookup"><span data-stu-id="2fad8-166">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="2fad8-167">執行原則會決定您是否可以載入設定檔，例如 PowerShell 設定檔或執行腳本。</span><span class="sxs-lookup"><span data-stu-id="2fad8-167">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="2fad8-168">而且，腳本在執行前是否必須經過數位簽署。</span><span class="sxs-lookup"><span data-stu-id="2fad8-168">And, whether scripts must be digitally signed before they are run.</span></span>

## <span data-ttu-id="2fad8-169">相關連結</span><span class="sxs-lookup"><span data-stu-id="2fad8-169">RELATED LINKS</span></span>

[<span data-ttu-id="2fad8-170">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="2fad8-170">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)

[<span data-ttu-id="2fad8-171">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="2fad8-171">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="2fad8-172">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="2fad8-172">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="2fad8-173">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="2fad8-173">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="2fad8-174">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="2fad8-174">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)
