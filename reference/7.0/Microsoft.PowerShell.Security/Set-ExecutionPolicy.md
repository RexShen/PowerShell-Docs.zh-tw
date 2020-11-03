---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: d3724c79f5864295c70d5addd46a8a133862d0ec
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201899"
---
# <span data-ttu-id="8ae38-103">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="8ae38-103">Set-ExecutionPolicy</span></span>

## <span data-ttu-id="8ae38-104">概要</span><span class="sxs-lookup"><span data-stu-id="8ae38-104">SYNOPSIS</span></span>
<span data-ttu-id="8ae38-105">設定 Windows 電腦的 PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-105">Sets the PowerShell execution policies for Windows computers.</span></span>

## <span data-ttu-id="8ae38-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8ae38-106">SYNTAX</span></span>

### <span data-ttu-id="8ae38-107">全部</span><span class="sxs-lookup"><span data-stu-id="8ae38-107">All</span></span>

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8ae38-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8ae38-108">DESCRIPTION</span></span>

<span data-ttu-id="8ae38-109">此 `Set-ExecutionPolicy` Cmdlet 會變更 Windows 電腦的 PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-109">The `Set-ExecutionPolicy` cmdlet changes PowerShell execution policies for Windows computers.</span></span> <span data-ttu-id="8ae38-110">如需詳細資訊，請參閱 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="8ae38-110">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="8ae38-111">從非 Windows 電腦的 PowerShell 6.0 開始，預設的執行原則不 **受限制** 且無法變更。</span><span class="sxs-lookup"><span data-stu-id="8ae38-111">Beginning in PowerShell 6.0 for non-Windows computers, the default execution policy is **Unrestricted** and can't be changed.</span></span> <span data-ttu-id="8ae38-112">您 `Set-ExecutionPolicy` 可以使用此 Cmdlet，但 PowerShell 會顯示不支援的主控台訊息。</span><span class="sxs-lookup"><span data-stu-id="8ae38-112">The `Set-ExecutionPolicy` cmdlet is available, but PowerShell displays a console message that it's not supported.</span></span>

<span data-ttu-id="8ae38-113">執行原則是 PowerShell 安全性策略的一部分。</span><span class="sxs-lookup"><span data-stu-id="8ae38-113">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="8ae38-114">執行原則會決定您是否可以載入設定檔，例如 PowerShell 設定檔或執行腳本。</span><span class="sxs-lookup"><span data-stu-id="8ae38-114">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="8ae38-115">而且，腳本在執行前是否必須經過數位簽署。</span><span class="sxs-lookup"><span data-stu-id="8ae38-115">And, whether scripts must be digitally signed before they are run.</span></span>

<span data-ttu-id="8ae38-116">`Set-ExecutionPolicy`Cmdlet 的預設範圍是 **LocalMachine** ，會影響使用該電腦的每個人。</span><span class="sxs-lookup"><span data-stu-id="8ae38-116">The `Set-ExecutionPolicy` cmdlet's default scope is **LocalMachine** , which affects everyone who uses the computer.</span></span> <span data-ttu-id="8ae38-117">若要變更 **LocalMachine** 的執行原則，請使用 [以 **系統管理員身分執行** ] 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8ae38-117">To change the execution policy for **LocalMachine** , start PowerShell with **Run as Administrator** .</span></span>

<span data-ttu-id="8ae38-118">若要以優先順序順序顯示每個範圍的執行原則，請使用 `Get-ExecutionPolicy -List` 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-118">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="8ae38-119">若要查看適用于 PowerShell 會話的有效執行原則，請使用 `Get-ExecutionPolicy` 沒有參數的。</span><span class="sxs-lookup"><span data-stu-id="8ae38-119">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

## <span data-ttu-id="8ae38-120">範例</span><span class="sxs-lookup"><span data-stu-id="8ae38-120">EXAMPLES</span></span>

### <span data-ttu-id="8ae38-121">範例1：設定執行原則</span><span class="sxs-lookup"><span data-stu-id="8ae38-121">Example 1: Set an execution policy</span></span>

<span data-ttu-id="8ae38-122">此範例顯示如何設定本機電腦的執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-122">This example shows how to set the execution policy for the local computer.</span></span>

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
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="8ae38-123">此 `Set-ExecutionPolicy` Cmdlet 會使用 **ExecutionPolicy** 參數來指定 **RemoteSigned** 原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-123">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="8ae38-124">**Scope** 參數會指定預設的範圍值： **LocalMachine** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-124">The **Scope** parameter specifies the default scope value, **LocalMachine** .</span></span> <span data-ttu-id="8ae38-125">若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。</span><span class="sxs-lookup"><span data-stu-id="8ae38-125">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="8ae38-126">範例2：設定與群組原則衝突的執行原則</span><span class="sxs-lookup"><span data-stu-id="8ae38-126">Example 2: Set an execution policy that conflicts with a Group Policy</span></span>

<span data-ttu-id="8ae38-127">此命令會嘗試將 **LocalMachine** 範圍的執行原則設定為 [ **受限制** ]。</span><span class="sxs-lookup"><span data-stu-id="8ae38-127">This command attempts to set the **LocalMachine** scope's execution policy to **Restricted** .</span></span>
<span data-ttu-id="8ae38-128">**LocalMachine** 的限制較多，但不是有效的原則，因為它與群組原則衝突。</span><span class="sxs-lookup"><span data-stu-id="8ae38-128">**LocalMachine** is more restrictive, but isn't the effective policy because it conflicts with a Group Policy.</span></span> <span data-ttu-id="8ae38-129">**受限制** 的原則會寫入登錄 hive **HKEY_LOCAL_MACHINE** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-129">The **Restricted** policy is written to the registry hive **HKEY_LOCAL_MACHINE** .</span></span>

```
PS> Set-ExecutionPolicy -ExecutionPolicy Restricted -Scope LocalMachine

Set-ExecutionPolicy : PowerShell updated your local preference successfully, but the setting is
overridden by the Group Policy applied to your system. Due to the override, your shell will retain
its current effective execution policy of "AllSigned". Contact your Group Policy administrator for
more information. At line:1 char:20 + Set-ExecutionPolicy <<<< restricted

PS> Get-ChildItem -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds

Name                    Property
----                    --------
Microsoft.PowerShell    Path            : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
                        ExecutionPolicy : Restricted
ScriptedDiagnostics     ExecutionPolicy : Unrestricted
```

<span data-ttu-id="8ae38-130">此 `Set-ExecutionPolicy` Cmdlet 會使用 **ExecutionPolicy** 參數來指定 **受限制** 的原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-130">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **Restricted** policy.</span></span> <span data-ttu-id="8ae38-131">**Scope** 參數會指定預設的範圍值： **LocalMachine** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-131">The **Scope** parameter specifies the default scope value, **LocalMachine** .</span></span>
<span data-ttu-id="8ae38-132">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數搭配 **HKLM** 提供者來指定登錄位置。</span><span class="sxs-lookup"><span data-stu-id="8ae38-132">The `Get-ChildItem` cmdlet uses the **Path** parameter with the **HKLM** provider to specify registry location.</span></span>

### <span data-ttu-id="8ae38-133">範例3：將執行原則從遠端電腦套用至本機電腦</span><span class="sxs-lookup"><span data-stu-id="8ae38-133">Example 3: Apply the execution policy from a remote computer to a local computer</span></span>

<span data-ttu-id="8ae38-134">此命令會從遠端電腦取得執行原則物件，並在本機電腦上設定原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-134">This command gets the execution policy object from a remote computer and sets the policy on the local computer.</span></span> <span data-ttu-id="8ae38-135">`Get-ExecutionPolicy` 將 **Microsoft.PowerShell.ExecutionPolicy** 物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="8ae38-135">`Get-ExecutionPolicy` sends a **Microsoft.PowerShell.ExecutionPolicy** object down the pipeline.</span></span> <span data-ttu-id="8ae38-136">`Set-ExecutionPolicy` 接受管線輸入，且不需要 **ExecutionPolicy** 參數。</span><span class="sxs-lookup"><span data-stu-id="8ae38-136">`Set-ExecutionPolicy` accepts pipeline input and doesn't require the **ExecutionPolicy** parameter.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

<span data-ttu-id="8ae38-137">此 `Invoke-Command` Cmdlet 會在本機電腦上執行，並將 **ScriptBlock** 傳送至遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="8ae38-137">The `Invoke-Command` cmdlet is executed at the local computer and sends the **ScriptBlock** to the remote computer.</span></span> <span data-ttu-id="8ae38-138">**ComputerName** 參數指定遠端電腦 **Server01** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-138">The **ComputerName** parameter specifies the remote computer, **Server01** .</span></span> <span data-ttu-id="8ae38-139">**ScriptBlock** 參數會 `Get-ExecutionPolicy` 在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="8ae38-139">The **ScriptBlock** parameter runs `Get-ExecutionPolicy` on the remote computer.</span></span> <span data-ttu-id="8ae38-140">`Get-ExecutionPolicy`物件會向下傳送至 `Set-ExecutionPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-140">The `Get-ExecutionPolicy` object is sent down the pipeline to the `Set-ExecutionPolicy`.</span></span>
<span data-ttu-id="8ae38-141">`Set-ExecutionPolicy` 將執行原則套用到本機電腦的預設範圍 **LocalMachine** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-141">`Set-ExecutionPolicy` applies the execution policy to the local computer's default scope, **LocalMachine** .</span></span>

### <span data-ttu-id="8ae38-142">範例4：設定執行原則的範圍</span><span class="sxs-lookup"><span data-stu-id="8ae38-142">Example 4: Set the scope for an execution policy</span></span>

<span data-ttu-id="8ae38-143">此範例示範如何為指定的範圍（ **CurrentUser** ）設定執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-143">This example shows how to set an execution policy for a specified scope, **CurrentUser** .</span></span> <span data-ttu-id="8ae38-144">**CurrentUser** 範圍只會影響設定此領域的使用者。</span><span class="sxs-lookup"><span data-stu-id="8ae38-144">The **CurrentUser** scope only affects the user who sets this scope.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope CurrentUser
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

<span data-ttu-id="8ae38-145">`Set-ExecutionPolicy` 使用 **ExecutionPolicy** 參數來指定 **AllSigned** 原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-145">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span>
<span data-ttu-id="8ae38-146">**Scope** 參數指定 **CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-146">The **Scope** parameter specifies the **CurrentUser** .</span></span> <span data-ttu-id="8ae38-147">若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。</span><span class="sxs-lookup"><span data-stu-id="8ae38-147">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

<span data-ttu-id="8ae38-148">使用者的有效執行原則會變成 **AllSigned** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-148">The effective execution policy for the user becomes **AllSigned** .</span></span>

### <span data-ttu-id="8ae38-149">範例5：移除目前使用者的執行原則</span><span class="sxs-lookup"><span data-stu-id="8ae38-149">Example 5: Remove the execution policy for the current user</span></span>

<span data-ttu-id="8ae38-150">此範例示範如何使用 **未定義** 的執行原則，來移除指定範圍的執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-150">This example shows how use the **Undefined** execution policy to remove an execution policy for a specified scope.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
Get-ExecutionPolicy -List
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine    RemoteSigned
```

<span data-ttu-id="8ae38-151">`Set-ExecutionPolicy` 使用 **ExecutionPolicy** 參數指定 **未定義** 的原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-151">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **Undefined** policy.</span></span>
<span data-ttu-id="8ae38-152">**Scope** 參數指定 **CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-152">The **Scope** parameter specifies the **CurrentUser** .</span></span> <span data-ttu-id="8ae38-153">若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。</span><span class="sxs-lookup"><span data-stu-id="8ae38-153">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="8ae38-154">範例6：設定目前 PowerShell 會話的執行原則</span><span class="sxs-lookup"><span data-stu-id="8ae38-154">Example 6: Set the execution policy for the current PowerShell session</span></span>

<span data-ttu-id="8ae38-155">**進程** 範圍只會影響目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="8ae38-155">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="8ae38-156">執行原則會儲存在環境變數中 `$env:PSExecutionPolicyPreference` ，並在會話關閉時刪除。</span><span class="sxs-lookup"><span data-stu-id="8ae38-156">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference` and is deleted when the session is closed.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy AllSigned -Scope Process
```

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       AllSigned
  CurrentUser    RemoteSigned
 LocalMachine    RemoteSigned
```

<span data-ttu-id="8ae38-157">`Set-ExecutionPolicy`使用 **ExecutionPolicy** 參數來指定 **AllSigned** 原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-157">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span> <span data-ttu-id="8ae38-158">**Scope** 參數會指定值 **處理** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-158">The **Scope** parameter specifies the value **Process** .</span></span> <span data-ttu-id="8ae38-159">若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。</span><span class="sxs-lookup"><span data-stu-id="8ae38-159">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="8ae38-160">範例7：解除封鎖腳本以在不變更執行原則的情況下執行</span><span class="sxs-lookup"><span data-stu-id="8ae38-160">Example 7: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="8ae38-161">此範例顯示 **RemoteSigned** 執行原則如何防止您執行未簽署的腳本。</span><span class="sxs-lookup"><span data-stu-id="8ae38-161">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="8ae38-162">最佳做法是先閱讀腳本的程式碼，並確認它是安全的，然後 **再** 使用 `Unblock-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8ae38-162">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="8ae38-163">此 `Unblock-File` Cmdlet 會解除封鎖腳本，使其可執行，但不會變更執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-163">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

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

<span data-ttu-id="8ae38-164">`Set-ExecutionPolicy`使用 **ExecutionPolicy** 參數來指定 **RemoteSigned** 原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-164">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="8ae38-165">設定預設範圍 **LocalMachine** 的原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-165">The policy is set for the default scope, **LocalMachine** .</span></span>

<span data-ttu-id="8ae38-166">此 `Get-ExecutionPolicy` Cmdlet 會顯示 **RemoteSigned** 是目前 PowerShell 會話的有效執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-166">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="8ae38-167">**Start-ActivityTracker.ps1** 的腳本會從目前的目錄執行。</span><span class="sxs-lookup"><span data-stu-id="8ae38-167">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="8ae38-168">因為腳本未經過數位簽署，所以 **RemoteSigned** 會封鎖腳本。</span><span class="sxs-lookup"><span data-stu-id="8ae38-168">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="8ae38-169">在此範例中，腳本的程式碼已被審核並驗證為可安全執行。</span><span class="sxs-lookup"><span data-stu-id="8ae38-169">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="8ae38-170">此 `Unblock-File` Cmdlet 會使用 **Path** 參數將腳本解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="8ae38-170">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="8ae38-171">若要確認 `Unblock-File` 未變更執行原則，請 `Get-ExecutionPolicy` 顯示有效的執行原則 **RemoteSigned** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-171">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned** .</span></span>

<span data-ttu-id="8ae38-172">腳本 **Start-ActivityTracker.ps1** 會從目前的目錄執行。</span><span class="sxs-lookup"><span data-stu-id="8ae38-172">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="8ae38-173">腳本開始執行的原因是 Cmdlet 已解除封鎖 `Unblock-File` 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-173">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="8ae38-174">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8ae38-174">PARAMETERS</span></span>

### <span data-ttu-id="8ae38-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8ae38-175">-Confirm</span></span>

<span data-ttu-id="8ae38-176">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="8ae38-176">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8ae38-177">-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="8ae38-177">-ExecutionPolicy</span></span>

<span data-ttu-id="8ae38-178">指定執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-178">Specifies the execution policy.</span></span> <span data-ttu-id="8ae38-179">如果沒有任何群組原則，且每個範圍的執行原則都設定為 **未定義** ，則 [ **受限制** ] 會成為所有使用者的有效原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-179">If there are no Group Policies and each scope's execution policy is set to **Undefined** , then **Restricted** becomes the effective policy for all users.</span></span>

<span data-ttu-id="8ae38-180">可接受的執行原則值如下：</span><span class="sxs-lookup"><span data-stu-id="8ae38-180">The acceptable execution policy values are as follows:</span></span>

- <span data-ttu-id="8ae38-181">**AllSigned** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-181">**AllSigned** .</span></span> <span data-ttu-id="8ae38-182">要求所有腳本和設定檔都必須由信任的發行者簽署，包括在本機電腦上撰寫的腳本。</span><span class="sxs-lookup"><span data-stu-id="8ae38-182">Requires that all scripts and configuration files are signed by a trusted publisher, including scripts written on the local computer.</span></span>
- <span data-ttu-id="8ae38-183">**略過** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-183">**Bypass** .</span></span> <span data-ttu-id="8ae38-184">不會封鎖任何項目，且不會顯示警告或提示。</span><span class="sxs-lookup"><span data-stu-id="8ae38-184">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="8ae38-185">**Default** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-185">**Default** .</span></span> <span data-ttu-id="8ae38-186">設定預設執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-186">Sets the default execution policy.</span></span> <span data-ttu-id="8ae38-187">**受限於** windows 用戶端或 Windows server **RemoteSigned** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-187">**Restricted** for Windows clients or **RemoteSigned** for Windows servers.</span></span>
- <span data-ttu-id="8ae38-188">**RemoteSigned** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-188">**RemoteSigned** .</span></span> <span data-ttu-id="8ae38-189">要求從網際網路下載的所有腳本和設定檔都必須由信任的發行者簽署。</span><span class="sxs-lookup"><span data-stu-id="8ae38-189">Requires that all scripts and configuration files downloaded from the Internet are signed by a trusted publisher.</span></span> <span data-ttu-id="8ae38-190">Windows server 電腦的預設執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-190">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="8ae38-191">**受限制** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-191">**Restricted** .</span></span> <span data-ttu-id="8ae38-192">不會載入設定檔或執行腳本。</span><span class="sxs-lookup"><span data-stu-id="8ae38-192">Doesn't load configuration files or run scripts.</span></span> <span data-ttu-id="8ae38-193">預設的執行原則 Windows 用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="8ae38-193">The default execution policy Windows client computers.</span></span>
- <span data-ttu-id="8ae38-194">**未定義** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-194">**Undefined** .</span></span> <span data-ttu-id="8ae38-195">未設定範圍的執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-195">No execution policy is set for the scope.</span></span> <span data-ttu-id="8ae38-196">從未由群組原則設定的範圍移除指派的執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-196">Removes an assigned execution policy from a scope that is not set by a Group Policy.</span></span> <span data-ttu-id="8ae38-197">如果未 **定義** 所有範圍中的執行原則，則會 **限制** 有效的執行原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-197">If the execution policy in all scopes is **Undefined** , the effective execution policy is **Restricted** .</span></span>
- <span data-ttu-id="8ae38-198">不 **受限制** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-198">**Unrestricted** .</span></span> <span data-ttu-id="8ae38-199">從 PowerShell 6.0 開始，這是非 Windows 電腦的預設執行原則，無法變更。</span><span class="sxs-lookup"><span data-stu-id="8ae38-199">Beginning in PowerShell 6.0, this is the default execution policy for non-Windows computers and can't be changed.</span></span> <span data-ttu-id="8ae38-200">載入所有設定檔並執行所有指令碼。</span><span class="sxs-lookup"><span data-stu-id="8ae38-200">Loads all configuration files and runs all scripts.</span></span> <span data-ttu-id="8ae38-201">如果您執行從網際網路下載的未簽署腳本，系統會在執行之前提示您提供許可權。</span><span class="sxs-lookup"><span data-stu-id="8ae38-201">If you run an unsigned script that was downloaded from the internet, you're prompted for permission before it runs.</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: AllSigned, Bypass, Default, RemoteSigned, Restricted, Undefined, Unrestricted

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8ae38-202">-Force</span><span class="sxs-lookup"><span data-stu-id="8ae38-202">-Force</span></span>

<span data-ttu-id="8ae38-203">隱藏所有確認提示。</span><span class="sxs-lookup"><span data-stu-id="8ae38-203">Suppresses all the confirmation prompts.</span></span> <span data-ttu-id="8ae38-204">請小心使用此參數來避免非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="8ae38-204">Use caution with this parameter to avoid unexpected results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ae38-205">-Scope</span><span class="sxs-lookup"><span data-stu-id="8ae38-205">-Scope</span></span>

<span data-ttu-id="8ae38-206">指定受執行原則影響的範圍。</span><span class="sxs-lookup"><span data-stu-id="8ae38-206">Specifies the scope that is affected by an execution policy.</span></span> <span data-ttu-id="8ae38-207">預設範圍是 **LocalMachine** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-207">The default scope is **LocalMachine** .</span></span>

<span data-ttu-id="8ae38-208">有效的執行原則取決於優先順序順序，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8ae38-208">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="8ae38-209">**MachinePolicy** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-209">**MachinePolicy** .</span></span> <span data-ttu-id="8ae38-210">由電腦的所有使用者的群組原則設定。</span><span class="sxs-lookup"><span data-stu-id="8ae38-210">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="8ae38-211">**>userpolicy** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-211">**UserPolicy** .</span></span> <span data-ttu-id="8ae38-212">由電腦目前使用者的群組原則設定。</span><span class="sxs-lookup"><span data-stu-id="8ae38-212">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="8ae38-213">**處理** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-213">**Process** .</span></span> <span data-ttu-id="8ae38-214">只會影響目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="8ae38-214">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="8ae38-215">**CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-215">**CurrentUser** .</span></span> <span data-ttu-id="8ae38-216">只會影響目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="8ae38-216">Affects only the current user.</span></span>
- <span data-ttu-id="8ae38-217">**LocalMachine** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-217">**LocalMachine** .</span></span> <span data-ttu-id="8ae38-218">預設範圍會影響電腦的所有使用者。</span><span class="sxs-lookup"><span data-stu-id="8ae38-218">Default scope that affects all users of the computer.</span></span>

<span data-ttu-id="8ae38-219">**進程** 範圍只會影響目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="8ae38-219">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="8ae38-220">執行原則會儲存在環境變數中，而不是儲存在登錄中 `$env:PSExecutionPolicyPreference` 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-220">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="8ae38-221">當 PowerShell 會話關閉時，會刪除變數和值。</span><span class="sxs-lookup"><span data-stu-id="8ae38-221">When the PowerShell session is closed, the variable and value are deleted.</span></span>

<span data-ttu-id="8ae38-222">**CurrentUser** 範圍的執行原則會寫入登錄 hive **HKEY_LOCAL_USER** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-222">Execution policies for the **CurrentUser** scope are written to the registry hive **HKEY_LOCAL_USER** .</span></span>

<span data-ttu-id="8ae38-223">**LocalMachine** 範圍的執行原則會寫入登錄 hive **HKEY_LOCAL_MACHINE** 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-223">Execution policies for the **LocalMachine** scope are written to the registry hive **HKEY_LOCAL_MACHINE** .</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicyScope
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, LocalMachine, MachinePolicy, Process, UserPolicy

Required: False
Position: 1
Default value: LocalMachine
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="8ae38-224">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8ae38-224">-WhatIf</span></span>

<span data-ttu-id="8ae38-225">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="8ae38-225">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8ae38-226">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="8ae38-226">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8ae38-227">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8ae38-227">CommonParameters</span></span>

<span data-ttu-id="8ae38-228">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8ae38-228">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8ae38-229">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8ae38-229">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8ae38-230">輸入</span><span class="sxs-lookup"><span data-stu-id="8ae38-230">INPUTS</span></span>

### <span data-ttu-id="8ae38-231">Microsoft.PowerShell.ExecutionPolicy、System.String</span><span class="sxs-lookup"><span data-stu-id="8ae38-231">Microsoft.PowerShell.ExecutionPolicy, System.String</span></span>

<span data-ttu-id="8ae38-232">您可以使用管線將執行原則物件或包含執行原則名稱的字串傳送至 `Set-ExecutionPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="8ae38-232">You can pipe an execution policy object or a string that contains the name of an execution policy to `Set-ExecutionPolicy`.</span></span>

## <span data-ttu-id="8ae38-233">輸出</span><span class="sxs-lookup"><span data-stu-id="8ae38-233">OUTPUTS</span></span>

### <span data-ttu-id="8ae38-234">無</span><span class="sxs-lookup"><span data-stu-id="8ae38-234">None</span></span>

<span data-ttu-id="8ae38-235">`Set-ExecutionPolicy` 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="8ae38-235">`Set-ExecutionPolicy` doesn't return any output.</span></span>

## <span data-ttu-id="8ae38-236">注意</span><span class="sxs-lookup"><span data-stu-id="8ae38-236">NOTES</span></span>

<span data-ttu-id="8ae38-237">`Set-ExecutionPolicy` 不會變更 **MachinePolicy** 和 **>userpolicy** 範圍，因為它們是由群組原則設定。</span><span class="sxs-lookup"><span data-stu-id="8ae38-237">`Set-ExecutionPolicy` doesn't change the **MachinePolicy** and **UserPolicy** scopes because they are set by Group Policies.</span></span>

<span data-ttu-id="8ae38-238">`Set-ExecutionPolicy` 即使使用者喜好設定比原則更嚴格，也不會覆寫群組原則。</span><span class="sxs-lookup"><span data-stu-id="8ae38-238">`Set-ExecutionPolicy` doesn't override a Group Policy, even if the user preference is more restrictive than the policy.</span></span>

<span data-ttu-id="8ae38-239">如果電腦或使用者的群組原則 **開啟腳本執行** ，則會儲存使用者喜好設定，但它並不會有效。</span><span class="sxs-lookup"><span data-stu-id="8ae38-239">If the Group Policy **Turn on Script Execution** is enabled for the computer or user, the user preference is saved, but it is not effective.</span></span> <span data-ttu-id="8ae38-240">PowerShell 會顯示說明衝突的訊息。</span><span class="sxs-lookup"><span data-stu-id="8ae38-240">PowerShell displays a message that explains the conflict.</span></span>

## <span data-ttu-id="8ae38-241">相關連結</span><span class="sxs-lookup"><span data-stu-id="8ae38-241">RELATED LINKS</span></span>

[<span data-ttu-id="8ae38-242">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="8ae38-242">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="8ae38-243">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="8ae38-243">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="8ae38-244">about_Providers</span><span class="sxs-lookup"><span data-stu-id="8ae38-244">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="8ae38-245">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="8ae38-245">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="8ae38-246">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="8ae38-246">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="8ae38-247">Get-executionpolicy</span><span class="sxs-lookup"><span data-stu-id="8ae38-247">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="8ae38-248">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="8ae38-248">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="8ae38-249">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="8ae38-249">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="8ae38-250">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="8ae38-250">Unblock-File</span></span>](../Microsoft.PowerShell.Utility/Unblock-File.md)
