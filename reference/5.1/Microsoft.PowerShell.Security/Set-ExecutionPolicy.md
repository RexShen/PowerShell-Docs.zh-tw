---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 3/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ExecutionPolicy
ms.openlocfilehash: 313ff4f2d3fc89263cdf4d0ede860ef8e538a2ea
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203388"
---
# <span data-ttu-id="64df7-103">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="64df7-103">Set-ExecutionPolicy</span></span>

## <span data-ttu-id="64df7-104">概要</span><span class="sxs-lookup"><span data-stu-id="64df7-104">SYNOPSIS</span></span>
<span data-ttu-id="64df7-105">設定 Windows 電腦的 PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-105">Sets the PowerShell execution policies for Windows computers.</span></span>

## <span data-ttu-id="64df7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="64df7-106">SYNTAX</span></span>

### <span data-ttu-id="64df7-107">全部</span><span class="sxs-lookup"><span data-stu-id="64df7-107">All</span></span>

```
Set-ExecutionPolicy [-ExecutionPolicy] <ExecutionPolicy> [[-Scope] <ExecutionPolicyScope>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="64df7-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="64df7-108">DESCRIPTION</span></span>

<span data-ttu-id="64df7-109">此 `Set-ExecutionPolicy` Cmdlet 會變更 Windows 電腦的 PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-109">The `Set-ExecutionPolicy` cmdlet changes PowerShell execution policies for Windows computers.</span></span> <span data-ttu-id="64df7-110">如需詳細資訊，請參閱 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="64df7-110">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="64df7-111">執行原則是 PowerShell 安全性策略的一部分。</span><span class="sxs-lookup"><span data-stu-id="64df7-111">An execution policy is part of the PowerShell security strategy.</span></span> <span data-ttu-id="64df7-112">執行原則會決定您是否可以載入設定檔，例如 PowerShell 設定檔或執行腳本。</span><span class="sxs-lookup"><span data-stu-id="64df7-112">Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts.</span></span> <span data-ttu-id="64df7-113">而且，腳本在執行前是否必須經過數位簽署。</span><span class="sxs-lookup"><span data-stu-id="64df7-113">And, whether scripts must be digitally signed before they are run.</span></span>

<span data-ttu-id="64df7-114">`Set-ExecutionPolicy`Cmdlet 的預設範圍是 **LocalMachine** ，會影響使用該電腦的每個人。</span><span class="sxs-lookup"><span data-stu-id="64df7-114">The `Set-ExecutionPolicy` cmdlet's default scope is **LocalMachine** , which affects everyone who uses the computer.</span></span> <span data-ttu-id="64df7-115">若要變更 **LocalMachine** 的執行原則，請使用 [以 **系統管理員身分執行** ] 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="64df7-115">To change the execution policy for **LocalMachine** , start PowerShell with **Run as Administrator** .</span></span>

<span data-ttu-id="64df7-116">若要以優先順序順序顯示每個範圍的執行原則，請使用 `Get-ExecutionPolicy -List` 。</span><span class="sxs-lookup"><span data-stu-id="64df7-116">To display the execution policies for each scope in the order of precedence, use `Get-ExecutionPolicy -List`.</span></span> <span data-ttu-id="64df7-117">若要查看適用于 PowerShell 會話的有效執行原則，請使用 `Get-ExecutionPolicy` 沒有參數的。</span><span class="sxs-lookup"><span data-stu-id="64df7-117">To see the effective execution policy for your PowerShell session use `Get-ExecutionPolicy` with no parameters.</span></span>

## <span data-ttu-id="64df7-118">範例</span><span class="sxs-lookup"><span data-stu-id="64df7-118">EXAMPLES</span></span>

### <span data-ttu-id="64df7-119">範例1：設定執行原則</span><span class="sxs-lookup"><span data-stu-id="64df7-119">Example 1: Set an execution policy</span></span>

<span data-ttu-id="64df7-120">此範例顯示如何設定本機電腦的執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-120">This example shows how to set the execution policy for the local computer.</span></span>

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

<span data-ttu-id="64df7-121">此 `Set-ExecutionPolicy` Cmdlet 會使用 **ExecutionPolicy** 參數來指定 **RemoteSigned** 原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-121">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="64df7-122">**Scope** 參數會指定預設的範圍值： **LocalMachine** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-122">The **Scope** parameter specifies the default scope value, **LocalMachine** .</span></span> <span data-ttu-id="64df7-123">若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。</span><span class="sxs-lookup"><span data-stu-id="64df7-123">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="64df7-124">範例2：設定與群組原則衝突的執行原則</span><span class="sxs-lookup"><span data-stu-id="64df7-124">Example 2: Set an execution policy that conflicts with a Group Policy</span></span>

<span data-ttu-id="64df7-125">此命令會嘗試將 **LocalMachine** 範圍的執行原則設定為 [ **受限制** ]。</span><span class="sxs-lookup"><span data-stu-id="64df7-125">This command attempts to set the **LocalMachine** scope's execution policy to **Restricted** .</span></span>
<span data-ttu-id="64df7-126">**LocalMachine** 的限制較多，但不是有效的原則，因為它與群組原則衝突。</span><span class="sxs-lookup"><span data-stu-id="64df7-126">**LocalMachine** is more restrictive, but isn't the effective policy because it conflicts with a Group Policy.</span></span> <span data-ttu-id="64df7-127">**受限制** 的原則會寫入登錄 hive **HKEY_LOCAL_MACHINE** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-127">The **Restricted** policy is written to the registry hive **HKEY_LOCAL_MACHINE** .</span></span>

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

<span data-ttu-id="64df7-128">此 `Set-ExecutionPolicy` Cmdlet 會使用 **ExecutionPolicy** 參數來指定 **受限制** 的原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-128">The `Set-ExecutionPolicy` cmdlet uses the **ExecutionPolicy** parameter to specify the **Restricted** policy.</span></span> <span data-ttu-id="64df7-129">**Scope** 參數會指定預設的範圍值： **LocalMachine** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-129">The **Scope** parameter specifies the default scope value, **LocalMachine** .</span></span>
<span data-ttu-id="64df7-130">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數搭配 **HKLM** 提供者來指定登錄位置。</span><span class="sxs-lookup"><span data-stu-id="64df7-130">The `Get-ChildItem` cmdlet uses the **Path** parameter with the **HKLM** provider to specify registry location.</span></span>

### <span data-ttu-id="64df7-131">範例3：將執行原則從遠端電腦套用至本機電腦</span><span class="sxs-lookup"><span data-stu-id="64df7-131">Example 3: Apply the execution policy from a remote computer to a local computer</span></span>

<span data-ttu-id="64df7-132">此命令會從遠端電腦取得執行原則物件，並在本機電腦上設定原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-132">This command gets the execution policy object from a remote computer and sets the policy on the local computer.</span></span> <span data-ttu-id="64df7-133">`Get-ExecutionPolicy` 將 **Microsoft.PowerShell.ExecutionPolicy** 物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="64df7-133">`Get-ExecutionPolicy` sends a **Microsoft.PowerShell.ExecutionPolicy** object down the pipeline.</span></span> <span data-ttu-id="64df7-134">`Set-ExecutionPolicy` 接受管線輸入，且不需要 **ExecutionPolicy** 參數。</span><span class="sxs-lookup"><span data-stu-id="64df7-134">`Set-ExecutionPolicy` accepts pipeline input and doesn't require the **ExecutionPolicy** parameter.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -ScriptBlock { Get-ExecutionPolicy } | Set-ExecutionPolicy
```

<span data-ttu-id="64df7-135">此 `Invoke-Command` Cmdlet 會在本機電腦上執行，並將 **ScriptBlock** 傳送至遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="64df7-135">The `Invoke-Command` cmdlet is executed at the local computer and sends the **ScriptBlock** to the remote computer.</span></span> <span data-ttu-id="64df7-136">**ComputerName** 參數指定遠端電腦 **Server01** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-136">The **ComputerName** parameter specifies the remote computer, **Server01** .</span></span> <span data-ttu-id="64df7-137">**ScriptBlock** 參數會 `Get-ExecutionPolicy` 在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="64df7-137">The **ScriptBlock** parameter runs `Get-ExecutionPolicy` on the remote computer.</span></span> <span data-ttu-id="64df7-138">`Get-ExecutionPolicy`物件會向下傳送至 `Set-ExecutionPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="64df7-138">The `Get-ExecutionPolicy` object is sent down the pipeline to the `Set-ExecutionPolicy`.</span></span>
<span data-ttu-id="64df7-139">`Set-ExecutionPolicy` 將執行原則套用到本機電腦的預設範圍 **LocalMachine** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-139">`Set-ExecutionPolicy` applies the execution policy to the local computer's default scope, **LocalMachine** .</span></span>

### <span data-ttu-id="64df7-140">範例4：設定執行原則的範圍</span><span class="sxs-lookup"><span data-stu-id="64df7-140">Example 4: Set the scope for an execution policy</span></span>

<span data-ttu-id="64df7-141">此範例示範如何為指定的範圍（ **CurrentUser** ）設定執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-141">This example shows how to set an execution policy for a specified scope, **CurrentUser** .</span></span> <span data-ttu-id="64df7-142">**CurrentUser** 範圍只會影響設定此領域的使用者。</span><span class="sxs-lookup"><span data-stu-id="64df7-142">The **CurrentUser** scope only affects the user who sets this scope.</span></span>

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

<span data-ttu-id="64df7-143">`Set-ExecutionPolicy` 使用 **ExecutionPolicy** 參數來指定 **AllSigned** 原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-143">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span>
<span data-ttu-id="64df7-144">**Scope** 參數指定 **CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-144">The **Scope** parameter specifies the **CurrentUser** .</span></span> <span data-ttu-id="64df7-145">若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。</span><span class="sxs-lookup"><span data-stu-id="64df7-145">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

<span data-ttu-id="64df7-146">使用者的有效執行原則會變成 **AllSigned** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-146">The effective execution policy for the user becomes **AllSigned** .</span></span>

### <span data-ttu-id="64df7-147">範例5：移除目前使用者的執行原則</span><span class="sxs-lookup"><span data-stu-id="64df7-147">Example 5: Remove the execution policy for the current user</span></span>

<span data-ttu-id="64df7-148">此範例示範如何使用 **未定義** 的執行原則，來移除指定範圍的執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-148">This example shows how use the **Undefined** execution policy to remove an execution policy for a specified scope.</span></span>

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

<span data-ttu-id="64df7-149">`Set-ExecutionPolicy` 使用 **ExecutionPolicy** 參數指定 **未定義** 的原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-149">`Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **Undefined** policy.</span></span>
<span data-ttu-id="64df7-150">**Scope** 參數指定 **CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-150">The **Scope** parameter specifies the **CurrentUser** .</span></span> <span data-ttu-id="64df7-151">若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。</span><span class="sxs-lookup"><span data-stu-id="64df7-151">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="64df7-152">範例6：設定目前 PowerShell 會話的執行原則</span><span class="sxs-lookup"><span data-stu-id="64df7-152">Example 6: Set the execution policy for the current PowerShell session</span></span>

<span data-ttu-id="64df7-153">**進程** 範圍只會影響目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="64df7-153">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="64df7-154">執行原則會儲存在環境變數中 `$env:PSExecutionPolicyPreference` ，並在會話關閉時刪除。</span><span class="sxs-lookup"><span data-stu-id="64df7-154">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference` and is deleted when the session is closed.</span></span>

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

<span data-ttu-id="64df7-155">`Set-ExecutionPolicy`使用 **ExecutionPolicy** 參數來指定 **AllSigned** 原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-155">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **AllSigned** policy.</span></span> <span data-ttu-id="64df7-156">**Scope** 參數會指定值 **處理** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-156">The **Scope** parameter specifies the value **Process** .</span></span> <span data-ttu-id="64df7-157">若要查看執行原則設定，請使用 `Get-ExecutionPolicy` Cmdlet 搭配 **List** 參數。</span><span class="sxs-lookup"><span data-stu-id="64df7-157">To view the execution policy settings, use the `Get-ExecutionPolicy` cmdlet with the **List** parameter.</span></span>

### <span data-ttu-id="64df7-158">範例7：解除封鎖腳本以在不變更執行原則的情況下執行</span><span class="sxs-lookup"><span data-stu-id="64df7-158">Example 7: Unblock a script to run it without changing the execution policy</span></span>

<span data-ttu-id="64df7-159">此範例顯示 **RemoteSigned** 執行原則如何防止您執行未簽署的腳本。</span><span class="sxs-lookup"><span data-stu-id="64df7-159">This example shows how the **RemoteSigned** execution policy prevents you from running unsigned scripts.</span></span>

<span data-ttu-id="64df7-160">最佳做法是先閱讀腳本的程式碼，並確認它是安全的，然後 **再** 使用 `Unblock-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64df7-160">A best practice is to read the script's code and verify it's safe **before** using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="64df7-161">此 `Unblock-File` Cmdlet 會解除封鎖腳本，使其可執行，但不會變更執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-161">The `Unblock-File` cmdlet unblocks scripts so they can run, but doesn't change the execution policy.</span></span>

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

<span data-ttu-id="64df7-162">`Set-ExecutionPolicy`使用 **ExecutionPolicy** 參數來指定 **RemoteSigned** 原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-162">The `Set-ExecutionPolicy` uses the **ExecutionPolicy** parameter to specify the **RemoteSigned** policy.</span></span> <span data-ttu-id="64df7-163">設定預設範圍 **LocalMachine** 的原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-163">The policy is set for the default scope, **LocalMachine** .</span></span>

<span data-ttu-id="64df7-164">此 `Get-ExecutionPolicy` Cmdlet 會顯示 **RemoteSigned** 是目前 PowerShell 會話的有效執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-164">The `Get-ExecutionPolicy` cmdlet shows that **RemoteSigned** is the effective execution policy for the current PowerShell session.</span></span>

<span data-ttu-id="64df7-165">**Start-ActivityTracker.ps1** 的腳本會從目前的目錄執行。</span><span class="sxs-lookup"><span data-stu-id="64df7-165">The **Start-ActivityTracker.ps1** script is executed from the current directory.</span></span> <span data-ttu-id="64df7-166">因為腳本未經過數位簽署，所以 **RemoteSigned** 會封鎖腳本。</span><span class="sxs-lookup"><span data-stu-id="64df7-166">The script is blocked by **RemoteSigned** because the script isn't digitally signed.</span></span>

<span data-ttu-id="64df7-167">在此範例中，腳本的程式碼已被審核並驗證為可安全執行。</span><span class="sxs-lookup"><span data-stu-id="64df7-167">For this example, the script's code was reviewed and verified as safe to run.</span></span> <span data-ttu-id="64df7-168">此 `Unblock-File` Cmdlet 會使用 **Path** 參數將腳本解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="64df7-168">The `Unblock-File` cmdlet uses the **Path** parameter to unblock the script.</span></span>

<span data-ttu-id="64df7-169">若要確認 `Unblock-File` 未變更執行原則，請 `Get-ExecutionPolicy` 顯示有效的執行原則 **RemoteSigned** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-169">To verify that `Unblock-File` didn't change the execution policy, `Get-ExecutionPolicy` displays the effective execution policy, **RemoteSigned** .</span></span>

<span data-ttu-id="64df7-170">腳本 **Start-ActivityTracker.ps1** 會從目前的目錄執行。</span><span class="sxs-lookup"><span data-stu-id="64df7-170">The script, **Start-ActivityTracker.ps1** is executed from the current directory.</span></span> <span data-ttu-id="64df7-171">腳本開始執行的原因是 Cmdlet 已解除封鎖 `Unblock-File` 。</span><span class="sxs-lookup"><span data-stu-id="64df7-171">The script begins to run because it was unblocked by the `Unblock-File` cmdlet.</span></span>

## <span data-ttu-id="64df7-172">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="64df7-172">PARAMETERS</span></span>

### <span data-ttu-id="64df7-173">-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="64df7-173">-ExecutionPolicy</span></span>

<span data-ttu-id="64df7-174">指定執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-174">Specifies the execution policy.</span></span> <span data-ttu-id="64df7-175">如果沒有任何群組原則，且每個範圍的執行原則都設定為 **未定義** ，則 [ **受限制** ] 會成為所有使用者的有效原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-175">If there are no Group Policies and each scope's execution policy is set to **Undefined** , then **Restricted** becomes the effective policy for all users.</span></span>

<span data-ttu-id="64df7-176">可接受的執行原則值如下：</span><span class="sxs-lookup"><span data-stu-id="64df7-176">The acceptable execution policy values are as follows:</span></span>

- <span data-ttu-id="64df7-177">**AllSigned** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-177">**AllSigned** .</span></span> <span data-ttu-id="64df7-178">要求所有腳本和設定檔都必須由信任的發行者簽署，包括在本機電腦上撰寫的腳本。</span><span class="sxs-lookup"><span data-stu-id="64df7-178">Requires that all scripts and configuration files are signed by a trusted publisher, including scripts written on the local computer.</span></span>
- <span data-ttu-id="64df7-179">**略過** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-179">**Bypass** .</span></span> <span data-ttu-id="64df7-180">不會封鎖任何項目，且不會顯示警告或提示。</span><span class="sxs-lookup"><span data-stu-id="64df7-180">Nothing is blocked and there are no warnings or prompts.</span></span>
- <span data-ttu-id="64df7-181">**Default** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-181">**Default** .</span></span> <span data-ttu-id="64df7-182">設定預設執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-182">Sets the default execution policy.</span></span> <span data-ttu-id="64df7-183">**受限於** windows 用戶端或 Windows server **RemoteSigned** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-183">**Restricted** for Windows clients or **RemoteSigned** for Windows servers.</span></span>
- <span data-ttu-id="64df7-184">**RemoteSigned** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-184">**RemoteSigned** .</span></span> <span data-ttu-id="64df7-185">要求從網際網路下載的所有腳本和設定檔都必須由信任的發行者簽署。</span><span class="sxs-lookup"><span data-stu-id="64df7-185">Requires that all scripts and configuration files downloaded from the Internet are signed by a trusted publisher.</span></span> <span data-ttu-id="64df7-186">Windows server 電腦的預設執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-186">The default execution policy for Windows server computers.</span></span>
- <span data-ttu-id="64df7-187">**受限制** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-187">**Restricted** .</span></span> <span data-ttu-id="64df7-188">不會載入設定檔或執行腳本。</span><span class="sxs-lookup"><span data-stu-id="64df7-188">Doesn't load configuration files or run scripts.</span></span> <span data-ttu-id="64df7-189">預設的執行原則 Windows 用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="64df7-189">The default execution policy Windows client computers.</span></span>
- <span data-ttu-id="64df7-190">**未定義** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-190">**Undefined** .</span></span> <span data-ttu-id="64df7-191">未設定範圍的執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-191">No execution policy is set for the scope.</span></span> <span data-ttu-id="64df7-192">從未由群組原則設定的範圍移除指派的執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-192">Removes an assigned execution policy from a scope that is not set by a Group Policy.</span></span> <span data-ttu-id="64df7-193">如果未 **定義** 所有範圍中的執行原則，則會 **限制** 有效的執行原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-193">If the execution policy in all scopes is **Undefined** , the effective execution policy is **Restricted** .</span></span>
- <span data-ttu-id="64df7-194">不 **受限制** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-194">**Unrestricted** .</span></span> <span data-ttu-id="64df7-195">載入所有設定檔並執行所有指令碼。</span><span class="sxs-lookup"><span data-stu-id="64df7-195">Loads all configuration files and runs all scripts.</span></span> <span data-ttu-id="64df7-196">如果您執行從網際網路下載且未經簽署的指令碼，在執行前會提示您需要執行權限。</span><span class="sxs-lookup"><span data-stu-id="64df7-196">If you run an unsigned script that was downloaded from the Internet, you are prompted for permission before it runs.</span></span>

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

### <span data-ttu-id="64df7-197">-Force</span><span class="sxs-lookup"><span data-stu-id="64df7-197">-Force</span></span>

<span data-ttu-id="64df7-198">隱藏所有確認提示。</span><span class="sxs-lookup"><span data-stu-id="64df7-198">Suppresses all the confirmation prompts.</span></span> <span data-ttu-id="64df7-199">請小心使用此參數來避免非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="64df7-199">Use caution with this parameter to avoid unexpected results.</span></span>

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

### <span data-ttu-id="64df7-200">-Scope</span><span class="sxs-lookup"><span data-stu-id="64df7-200">-Scope</span></span>

<span data-ttu-id="64df7-201">指定受執行原則影響的範圍。</span><span class="sxs-lookup"><span data-stu-id="64df7-201">Specifies the scope that is affected by an execution policy.</span></span> <span data-ttu-id="64df7-202">預設範圍是 **LocalMachine** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-202">The default scope is **LocalMachine** .</span></span>

<span data-ttu-id="64df7-203">有效的執行原則取決於優先順序順序，如下所示：</span><span class="sxs-lookup"><span data-stu-id="64df7-203">The effective execution policy is determined by the order of precedence as follows:</span></span>

- <span data-ttu-id="64df7-204">**MachinePolicy** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-204">**MachinePolicy** .</span></span> <span data-ttu-id="64df7-205">由電腦的所有使用者的群組原則設定。</span><span class="sxs-lookup"><span data-stu-id="64df7-205">Set by a Group Policy for all users of the computer.</span></span>
- <span data-ttu-id="64df7-206">**>userpolicy** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-206">**UserPolicy** .</span></span> <span data-ttu-id="64df7-207">由電腦目前使用者的群組原則設定。</span><span class="sxs-lookup"><span data-stu-id="64df7-207">Set by a Group Policy for the current user of the computer.</span></span>
- <span data-ttu-id="64df7-208">**處理** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-208">**Process** .</span></span> <span data-ttu-id="64df7-209">只會影響目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="64df7-209">Affects only the current PowerShell session.</span></span>
- <span data-ttu-id="64df7-210">**CurrentUser** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-210">**CurrentUser** .</span></span> <span data-ttu-id="64df7-211">只會影響目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="64df7-211">Affects only the current user.</span></span>
- <span data-ttu-id="64df7-212">**LocalMachine** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-212">**LocalMachine** .</span></span> <span data-ttu-id="64df7-213">預設範圍會影響電腦的所有使用者。</span><span class="sxs-lookup"><span data-stu-id="64df7-213">Default scope that affects all users of the computer.</span></span>

<span data-ttu-id="64df7-214">**進程** 範圍只會影響目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="64df7-214">The **Process** scope only affects the current PowerShell session.</span></span> <span data-ttu-id="64df7-215">執行原則會儲存在環境變數中，而不是儲存在登錄中 `$env:PSExecutionPolicyPreference` 。</span><span class="sxs-lookup"><span data-stu-id="64df7-215">The execution policy is saved in the environment variable `$env:PSExecutionPolicyPreference`, rather than the registry.</span></span> <span data-ttu-id="64df7-216">當 PowerShell 會話關閉時，會刪除變數和值。</span><span class="sxs-lookup"><span data-stu-id="64df7-216">When the PowerShell session is closed, the variable and value are deleted.</span></span>

<span data-ttu-id="64df7-217">**CurrentUser** 範圍的執行原則會寫入登錄 hive **HKEY_LOCAL_USER** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-217">Execution policies for the **CurrentUser** scope are written to the registry hive **HKEY_LOCAL_USER** .</span></span>

<span data-ttu-id="64df7-218">**LocalMachine** 範圍的執行原則會寫入登錄 hive **HKEY_LOCAL_MACHINE** 。</span><span class="sxs-lookup"><span data-stu-id="64df7-218">Execution policies for the **LocalMachine** scope are written to the registry hive **HKEY_LOCAL_MACHINE** .</span></span>

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

### <span data-ttu-id="64df7-219">-Confirm</span><span class="sxs-lookup"><span data-stu-id="64df7-219">-Confirm</span></span>

<span data-ttu-id="64df7-220">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="64df7-220">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="64df7-221">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="64df7-221">-WhatIf</span></span>

<span data-ttu-id="64df7-222">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="64df7-222">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="64df7-223">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="64df7-223">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="64df7-224">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="64df7-224">CommonParameters</span></span>

<span data-ttu-id="64df7-225">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="64df7-225">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="64df7-226">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="64df7-226">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="64df7-227">輸入</span><span class="sxs-lookup"><span data-stu-id="64df7-227">INPUTS</span></span>

### <span data-ttu-id="64df7-228">Microsoft.PowerShell.ExecutionPolicy、System.String</span><span class="sxs-lookup"><span data-stu-id="64df7-228">Microsoft.PowerShell.ExecutionPolicy, System.String</span></span>

<span data-ttu-id="64df7-229">您可以使用管線將執行原則物件或包含執行原則名稱的字串傳送至 `Set-ExecutionPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="64df7-229">You can pipe an execution policy object or a string that contains the name of an execution policy to `Set-ExecutionPolicy`.</span></span>

## <span data-ttu-id="64df7-230">輸出</span><span class="sxs-lookup"><span data-stu-id="64df7-230">OUTPUTS</span></span>

### <span data-ttu-id="64df7-231">無</span><span class="sxs-lookup"><span data-stu-id="64df7-231">None</span></span>

<span data-ttu-id="64df7-232">`Set-ExecutionPolicy` 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="64df7-232">`Set-ExecutionPolicy` doesn't return any output.</span></span>

## <span data-ttu-id="64df7-233">注意</span><span class="sxs-lookup"><span data-stu-id="64df7-233">NOTES</span></span>

<span data-ttu-id="64df7-234">`Set-ExecutionPolicy` 不會變更 **MachinePolicy** 和 **>userpolicy** 範圍，因為它們是由群組原則設定。</span><span class="sxs-lookup"><span data-stu-id="64df7-234">`Set-ExecutionPolicy` doesn't change the **MachinePolicy** and **UserPolicy** scopes because they are set by Group Policies.</span></span>

<span data-ttu-id="64df7-235">`Set-ExecutionPolicy` 即使使用者喜好設定比原則更嚴格，也不會覆寫群組原則。</span><span class="sxs-lookup"><span data-stu-id="64df7-235">`Set-ExecutionPolicy` doesn't override a Group Policy, even if the user preference is more restrictive than the policy.</span></span>

<span data-ttu-id="64df7-236">如果電腦或使用者的群組原則 **開啟腳本執行** ，則會儲存使用者喜好設定，但它並不會有效。</span><span class="sxs-lookup"><span data-stu-id="64df7-236">If the Group Policy **Turn on Script Execution** is enabled for the computer or user, the user preference is saved, but it is not effective.</span></span> <span data-ttu-id="64df7-237">PowerShell 會顯示說明衝突的訊息。</span><span class="sxs-lookup"><span data-stu-id="64df7-237">PowerShell displays a message that explains the conflict.</span></span>

## <span data-ttu-id="64df7-238">相關連結</span><span class="sxs-lookup"><span data-stu-id="64df7-238">RELATED LINKS</span></span>

[<span data-ttu-id="64df7-239">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="64df7-239">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="64df7-240">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="64df7-240">about_Group_Policy_Settings</span></span>](../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md)

[<span data-ttu-id="64df7-241">about_Providers</span><span class="sxs-lookup"><span data-stu-id="64df7-241">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="64df7-242">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="64df7-242">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="64df7-243">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="64df7-243">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="64df7-244">Get-executionpolicy</span><span class="sxs-lookup"><span data-stu-id="64df7-244">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="64df7-245">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="64df7-245">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="64df7-246">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="64df7-246">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="64df7-247">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="64df7-247">Unblock-File</span></span>](../Microsoft.PowerShell.Utility/Unblock-File.md)