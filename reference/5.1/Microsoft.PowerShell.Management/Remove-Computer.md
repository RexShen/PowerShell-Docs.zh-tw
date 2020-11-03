---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Computer
ms.openlocfilehash: 89e43220a8d5ac675ea232db09cf3edec2ca2b97
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203567"
---
# <span data-ttu-id="a810d-103">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="a810d-103">Remove-Computer</span></span>

## <span data-ttu-id="a810d-104">概要</span><span class="sxs-lookup"><span data-stu-id="a810d-104">SYNOPSIS</span></span>
<span data-ttu-id="a810d-105">將本機電腦從其網域中移除。</span><span class="sxs-lookup"><span data-stu-id="a810d-105">Removes the local computer from its domain.</span></span>

## <span data-ttu-id="a810d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a810d-106">SYNTAX</span></span>

### <span data-ttu-id="a810d-107">Local (預設值)</span><span class="sxs-lookup"><span data-stu-id="a810d-107">Local (Default)</span></span>

```
Remove-Computer [[-UnjoinDomainCredential] <PSCredential>] [-Restart] [-Force] [-PassThru]
 [-WorkgroupName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a810d-108">遠端</span><span class="sxs-lookup"><span data-stu-id="a810d-108">Remote</span></span>

```
Remove-Computer -UnjoinDomainCredential <PSCredential> [-LocalCredential <PSCredential>] [-Restart]
 [-ComputerName <String[]>] [-Force] [-PassThru] [-WorkgroupName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="a810d-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a810d-109">DESCRIPTION</span></span>

<span data-ttu-id="a810d-110">Cmdlet 會將 `Remove-Computer` 本機電腦和遠端電腦從其目前網域中移除。</span><span class="sxs-lookup"><span data-stu-id="a810d-110">The `Remove-Computer` cmdlet removes the local computer and remote computers from their current domains.</span></span>

<span data-ttu-id="a810d-111">當您將電腦從網域中移除時， `Remove-Computer` 也會停用該電腦的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="a810d-111">When you remove a computer from a domain, `Remove-Computer` also disables the domain account of the computer.</span></span> <span data-ttu-id="a810d-112">您必須提供明確的認證，將電腦從其網域中退出，即使它們是目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="a810d-112">You must provide explicit credentials to unjoin the computer from its domain, even when they are the credentials of the current user.</span></span> <span data-ttu-id="a810d-113">您必須重新開機電腦，才能讓變更生效。</span><span class="sxs-lookup"><span data-stu-id="a810d-113">You must restart the computer to make the change effective.</span></span> <span data-ttu-id="a810d-114">此外，當您將電腦從網域中移除時，必須將它移到工作群組中。</span><span class="sxs-lookup"><span data-stu-id="a810d-114">Also, when you remove a computer from a domain, you must move it to a workgroup.</span></span> <span data-ttu-id="a810d-115">請使用 **WorkgroupName** 參數來指定工作群組。</span><span class="sxs-lookup"><span data-stu-id="a810d-115">Use the **WorkgroupName** parameter to specify the workgroup.</span></span>

<span data-ttu-id="a810d-116">若要將電腦從工作組移到網域、從一個工作組移到另一個工作組，或是從一個網域移到另一個網域，請使用 `Add-Computer` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a810d-116">To move a computer from a workgroup to a domain, from one workgroup to another, or from one domain to another, use the `Add-Computer` cmdlet.</span></span>

<span data-ttu-id="a810d-117">若要取得此命令的結果，請使用 **Verbose** 和 **PassThru** 參數。</span><span class="sxs-lookup"><span data-stu-id="a810d-117">To get the results of the command, use the **Verbose** and **PassThru** parameters.</span></span> <span data-ttu-id="a810d-118">若要抑制使用者提示，請使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="a810d-118">To suppress the user prompt, use the **Force** parameter.</span></span>

<span data-ttu-id="a810d-119">`Remove-Computer` 從網域移除本機電腦和遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="a810d-119">`Remove-Computer` removes the local computer and remote computers from domains.</span></span> <span data-ttu-id="a810d-120">它包含認證參數，用來指定連線到遠端電腦及從網域退出時所要使用的替代認證； **Restart** 參數，用來重新啟動受影響的電腦；以及 **WorkgroupName** 參數，用來指定電腦要加入的工作群組名稱。</span><span class="sxs-lookup"><span data-stu-id="a810d-120">It includes credential parameters that specify alternate credentials for connecting to remote computers, and unjoining from a domain, a **Restart** parameter for restarting the affected computers, and a **WorkgroupName** parameter for specifying the name of the workgroup to which computers are added.</span></span>

## <span data-ttu-id="a810d-121">範例</span><span class="sxs-lookup"><span data-stu-id="a810d-121">EXAMPLES</span></span>

### <span data-ttu-id="a810d-122">範例1：將本機電腦從其網域中移除</span><span class="sxs-lookup"><span data-stu-id="a810d-122">Example 1: Remove the local computer from its domain</span></span>

<span data-ttu-id="a810d-123">此範例會將本機電腦從其加入的網域中移除。</span><span class="sxs-lookup"><span data-stu-id="a810d-123">This example removes the local computer from the domain to which it is joined.</span></span>

```powershell
Remove-Computer -UnjoinDomaincredential Domain01\Admin01 -PassThru -Verbose -Restart
```

<span data-ttu-id="a810d-124">**UnjoinDomainCredential** 參數提供網域系統管理員的認證。</span><span class="sxs-lookup"><span data-stu-id="a810d-124">The **UnjoinDomainCredential** parameter provides the credentials of a domain administrator.</span></span> <span data-ttu-id="a810d-125">**PassThru** 和 **詳細** 資訊一般參數會顯示命令成功或失敗的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a810d-125">The **PassThru** and the **Verbose** common parameters display information about the success or failure of the command.</span></span> <span data-ttu-id="a810d-126">**Restart** 參數會重新開機電腦以完成移除操作。</span><span class="sxs-lookup"><span data-stu-id="a810d-126">The **Restart** parameter restarts the computer to complete the remove operation.</span></span>

<span data-ttu-id="a810d-127">當未指定工作組名稱時，會將電腦從其網域中移除之後，移至名為的工作組。</span><span class="sxs-lookup"><span data-stu-id="a810d-127">When no workgroup name is specified, the computer is moved to the workgroup named after it is removed from its domain.</span></span>

### <span data-ttu-id="a810d-128">範例2：將數部電腦移至舊版工作組</span><span class="sxs-lookup"><span data-stu-id="a810d-128">Example 2: Move several computers to a legacy workgroup</span></span>

<span data-ttu-id="a810d-129">此範例會從其網域移除檔案中列出的所有電腦 `OldServers.txt` ，並將它們移至 **舊版** 工作組。</span><span class="sxs-lookup"><span data-stu-id="a810d-129">This example removes all the computers listed in the `OldServers.txt` file from their domains and moves them into the **Legacy** workgroup.</span></span>

```powershell
Remove-Computer -ComputerName (Get-Content OldServers.txt) -LocalCredential Domain01\Admin01 -UnJoinDomainCredential Domain01\Admin01 -WorkgroupName "Legacy" -Force -Restart
```

<span data-ttu-id="a810d-130">**LocalCredential** 參數提供具有連線到遠端電腦之許可權的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="a810d-130">The **LocalCredential** parameter provides the credentials of a user who has permission to connect to remote computers.</span></span> <span data-ttu-id="a810d-131">**UnjoinDomainCredential** 參數提供有許可權可從其網域移除電腦的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="a810d-131">The **UnjoinDomainCredential** parameter provides the credentials of a user who has permission to remove the computers from their domains.</span></span> <span data-ttu-id="a810d-132">**Force** 參數會抑制每部電腦的確認提示。</span><span class="sxs-lookup"><span data-stu-id="a810d-132">The **Force** parameter suppresses the confirmation prompts for each computer.</span></span> <span data-ttu-id="a810d-133">**重新開機** 參數會在每一部電腦從其網域中移除後，重新開機電腦。</span><span class="sxs-lookup"><span data-stu-id="a810d-133">The **Restart** parameter restarts each of the computers after it is removed from its domain.</span></span>

### <span data-ttu-id="a810d-134">範例3：在沒有確認的情況下，從工作組移除電腦</span><span class="sxs-lookup"><span data-stu-id="a810d-134">Example 3: Remove computers from a workgroup without confirmation</span></span>

<span data-ttu-id="a810d-135">此範例會將遠端電腦、Server01 和本機電腦從其網域中移除，並將其新增至 **本機** 工作組。</span><span class="sxs-lookup"><span data-stu-id="a810d-135">This example removes the remote computer, Server01, and the local computer from their domains and adds them to the **Local** workgroup.</span></span>

```powershell
Remove-Computer -ComputerName "Server01", "localhost" -UnjoinDomainCredential Domain01\Admin01 -WorkgroupName "Local" -Restart -Force
```

<span data-ttu-id="a810d-136">**Force** 參數會抑制每部電腦的確認提示。</span><span class="sxs-lookup"><span data-stu-id="a810d-136">The **Force** parameter suppresses the confirmation prompt for each computer.</span></span> <span data-ttu-id="a810d-137">**重新開機** 參數會重新開機電腦，讓變更生效。</span><span class="sxs-lookup"><span data-stu-id="a810d-137">The **Restart** parameter restarts the computers to make the change effective.</span></span>

## <span data-ttu-id="a810d-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a810d-138">PARAMETERS</span></span>

### <span data-ttu-id="a810d-139">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="a810d-139">-ComputerName</span></span>

<span data-ttu-id="a810d-140">指定要從其網域中移除的電腦。</span><span class="sxs-lookup"><span data-stu-id="a810d-140">Specifies the computers to be removed from their domains.</span></span> <span data-ttu-id="a810d-141">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="a810d-141">The default is the local computer.</span></span>

<span data-ttu-id="a810d-142">輸入遠端電腦 (FQDN) 的 NetBIOS 名稱、IP 位址或完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="a810d-142">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of the remote computers.</span></span> <span data-ttu-id="a810d-143">若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。</span><span class="sxs-lookup"><span data-stu-id="a810d-143">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="a810d-144">此參數不依賴 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="a810d-144">This parameter does not rely on PowerShell remoting.</span></span> <span data-ttu-id="a810d-145">**ComputerName** `Remove-Computer` 即使您的電腦未設定為執行遠端命令，您也可以使用 ComputerName 參數。</span><span class="sxs-lookup"><span data-stu-id="a810d-145">You can use the **ComputerName** parameter of `Remove-Computer` even if your computer is not configured to run remote commands.</span></span>

<span data-ttu-id="a810d-146">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="a810d-146">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a810d-147">-Force</span><span class="sxs-lookup"><span data-stu-id="a810d-147">-Force</span></span>

<span data-ttu-id="a810d-148">抑制使用者提示。</span><span class="sxs-lookup"><span data-stu-id="a810d-148">Suppresses the user prompt.</span></span> <span data-ttu-id="a810d-149">依預設， `Remove-Computer` 會在移除每部電腦之前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="a810d-149">By default, `Remove-Computer` prompts you for confirmation before removing each computer.</span></span>

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

### <span data-ttu-id="a810d-150">-LocalCredential</span><span class="sxs-lookup"><span data-stu-id="a810d-150">-LocalCredential</span></span>

<span data-ttu-id="a810d-151">指定具有連線到 **ComputerName** 參數所指定電腦之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a810d-151">Specifies a user account that has permission to connect to the computers that the **ComputerName** parameter specifies.</span></span> <span data-ttu-id="a810d-152">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="a810d-152">The default is the current user.</span></span>

<span data-ttu-id="a810d-153">輸入使用者名稱（例如 `User01` 或）， `Domain01\User01` 或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="a810d-153">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a810d-154">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="a810d-154">If you type a user name, the cmdlet prompts you for a password.</span></span> <span data-ttu-id="a810d-155">若要指定具有將電腦從其目前網域中移除之權限的使用者帳戶，請使用 **UnjoinDomainCredential** 參數。</span><span class="sxs-lookup"><span data-stu-id="a810d-155">To specify a user account that has permission to remove the computer from its current domain, use the **UnjoinDomainCredential** parameter.</span></span>

<span data-ttu-id="a810d-156">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="a810d-156">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a810d-157">-PassThru</span><span class="sxs-lookup"><span data-stu-id="a810d-157">-PassThru</span></span>

<span data-ttu-id="a810d-158">傳回命令的結果。</span><span class="sxs-lookup"><span data-stu-id="a810d-158">Returns the results of the command.</span></span> <span data-ttu-id="a810d-159">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a810d-159">Otherwise, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="a810d-160">-Restart</span><span class="sxs-lookup"><span data-stu-id="a810d-160">-Restart</span></span>

<span data-ttu-id="a810d-161">指出此 Cmdlet 會重新開機正在移除的電腦。</span><span class="sxs-lookup"><span data-stu-id="a810d-161">Indicates that this cmdlet restarts the computers that are being removed.</span></span> <span data-ttu-id="a810d-162">通常必須重新啟動才能使變更生效。</span><span class="sxs-lookup"><span data-stu-id="a810d-162">A restart is often required to make the change effective.</span></span>

<span data-ttu-id="a810d-163">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="a810d-163">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a810d-164">-UnjoinDomainCredential</span><span class="sxs-lookup"><span data-stu-id="a810d-164">-UnjoinDomainCredential</span></span>

<span data-ttu-id="a810d-165">指定具有將電腦從其目前網域中移除之權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a810d-165">Specifies a user account that has permission to remove the computers from their current domains.</span></span>
<span data-ttu-id="a810d-166">必須由這個參數提供明確的認證 (即使值是目前使用者的認證)，才能將遠端電腦從網域中移除。</span><span class="sxs-lookup"><span data-stu-id="a810d-166">Explicit credentials, as provided by this parameter, are required to remove remote computers from a domain, even when the value is the credentials of the current user.</span></span>

<span data-ttu-id="a810d-167">輸入使用者名稱（例如 User01 或 Domain01\User01），或輸入 **PSCredential** 物件，例如所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="a810d-167">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by `Get-Credential`.</span></span> <span data-ttu-id="a810d-168">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="a810d-168">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="a810d-169">若要指定具有連線到遠端電腦之權限的使用者帳戶，請使用 **LocalCredential** 參數。</span><span class="sxs-lookup"><span data-stu-id="a810d-169">To specify a user account that has permission to connect to the remote computers, use the **LocalCredential** parameter.</span></span>

<span data-ttu-id="a810d-170">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="a810d-170">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Local, Remote
Aliases: Credential

Required: False (Local), True (Remote)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a810d-171">-WorkgroupName</span><span class="sxs-lookup"><span data-stu-id="a810d-171">-WorkgroupName</span></span>

<span data-ttu-id="a810d-172">指定在將電腦從其網域中移除後，要讓它們加入的工作群組名稱。</span><span class="sxs-lookup"><span data-stu-id="a810d-172">Specifies the name of a workgroup to which the computers are added when they are removed from their domains.</span></span> <span data-ttu-id="a810d-173">預設值為 **WORKGROUP** 。</span><span class="sxs-lookup"><span data-stu-id="a810d-173">The default value is **WORKGROUP** .</span></span> <span data-ttu-id="a810d-174">當您將電腦從網域中移除時，必須將它新增到工作群組中。</span><span class="sxs-lookup"><span data-stu-id="a810d-174">When you remove a computer from a domain, you must add it to a workgroup.</span></span>

<span data-ttu-id="a810d-175">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="a810d-175">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a810d-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a810d-176">-Confirm</span></span>

<span data-ttu-id="a810d-177">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="a810d-177">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a810d-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a810d-178">-WhatIf</span></span>

<span data-ttu-id="a810d-179">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="a810d-179">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a810d-180">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="a810d-180">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a810d-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a810d-181">CommonParameters</span></span>

<span data-ttu-id="a810d-182">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a810d-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a810d-183">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a810d-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a810d-184">輸入</span><span class="sxs-lookup"><span data-stu-id="a810d-184">INPUTS</span></span>

### <span data-ttu-id="a810d-185">System.String</span><span class="sxs-lookup"><span data-stu-id="a810d-185">System.String</span></span>

<span data-ttu-id="a810d-186">您可以透過管線將電腦名稱稱傳送至 thisCmdlet。</span><span class="sxs-lookup"><span data-stu-id="a810d-186">You can pipe computer names to thiscmdlet.</span></span>

## <span data-ttu-id="a810d-187">輸出</span><span class="sxs-lookup"><span data-stu-id="a810d-187">OUTPUTS</span></span>

### <span data-ttu-id="a810d-188">Microsoft.PowerShell.Commands.ComputerChangeInfo</span><span class="sxs-lookup"><span data-stu-id="a810d-188">Microsoft.PowerShell.Commands.ComputerChangeInfo</span></span>

<span data-ttu-id="a810d-189">當您使用 **PassThru** 參數時，會傳回 `Remove-Computer` **ComputerChangeInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="a810d-189">When you use the **PassThru** parameter, `Remove-Computer` returns a **ComputerChangeInfo** object.</span></span>
<span data-ttu-id="a810d-190">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a810d-190">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a810d-191">注意</span><span class="sxs-lookup"><span data-stu-id="a810d-191">NOTES</span></span>

<span data-ttu-id="a810d-192">這個 Cmdlet 不會將電腦從工作群組中移除。</span><span class="sxs-lookup"><span data-stu-id="a810d-192">This cmdlet does not remove computers from workgroups.</span></span>

## <span data-ttu-id="a810d-193">相關連結</span><span class="sxs-lookup"><span data-stu-id="a810d-193">RELATED LINKS</span></span>

[<span data-ttu-id="a810d-194">Add-Computer</span><span class="sxs-lookup"><span data-stu-id="a810d-194">Add-Computer</span></span>](Add-Computer.md)

[<span data-ttu-id="a810d-195">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="a810d-195">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="a810d-196">Remove-Computer</span><span class="sxs-lookup"><span data-stu-id="a810d-196">Remove-Computer</span></span>](Remove-Computer.md)

[<span data-ttu-id="a810d-197">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="a810d-197">Rename-Computer</span></span>](Rename-Computer.md)

[<span data-ttu-id="a810d-198">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="a810d-198">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="a810d-199">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="a810d-199">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="a810d-200">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="a810d-200">Stop-Computer</span></span>](Stop-Computer.md)

[<span data-ttu-id="a810d-201">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="a810d-201">Test-Connection</span></span>](Test-Connection.md)
