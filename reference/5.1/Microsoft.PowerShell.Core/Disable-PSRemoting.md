---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 3a281786f99b2a46d0aeb9785480f02b35b2b433
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202339"
---
# <span data-ttu-id="2213f-103">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="2213f-103">Disable-PSRemoting</span></span>

## <span data-ttu-id="2213f-104">概要</span><span class="sxs-lookup"><span data-stu-id="2213f-104">SYNOPSIS</span></span>
<span data-ttu-id="2213f-105">防止 PowerShell 端點接收遠端連線。</span><span class="sxs-lookup"><span data-stu-id="2213f-105">Prevents PowerShell endpoints from receiving remote connections.</span></span>

## <span data-ttu-id="2213f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2213f-106">SYNTAX</span></span>

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2213f-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2213f-107">DESCRIPTION</span></span>

<span data-ttu-id="2213f-108">此 `Disable-PSRemoting` Cmdlet 會封鎖對本機電腦上所有 Windows PowerShell 交談端點設定的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="2213f-108">The `Disable-PSRemoting` cmdlet blocks remote access to all Windows PowerShell session endpoint configurations on the local computer.</span></span> <span data-ttu-id="2213f-109">這包括 PowerShell 6 或更新版本所建立的任何端點。</span><span class="sxs-lookup"><span data-stu-id="2213f-109">This includes any endpoints created by PowerShell 6 or higher.</span></span>

<span data-ttu-id="2213f-110">若要重新啟用對所有會話設定的遠端存取，請使用 `Enable-PSRemoting` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2213f-110">To re-enable remote access to all session configurations, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="2213f-111">這包括 PowerShell 6 或更新版本所建立的任何端點。</span><span class="sxs-lookup"><span data-stu-id="2213f-111">This includes any endpoints created by PowerShell 6 or higher.</span></span> <span data-ttu-id="2213f-112">若要啟用對所選會話設定的遠端存取，請使用 Cmdlet 的 **AccessMode** 參數 `Set-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="2213f-112">To enable remote access to selected session configurations, use the **AccessMode** parameter of the `Set-PSSessionConfiguration` cmdlet.</span></span>
<span data-ttu-id="2213f-113">您也可以使用 `Enable-PSSessionConfiguration` 和 `Disable-PSSessionConfiguration` Cmdlet 來啟用和停用所有使用者的會話設定。</span><span class="sxs-lookup"><span data-stu-id="2213f-113">You can also use the `Enable-PSSessionConfiguration` and `Disable-PSSessionConfiguration` cmdlets to enable and disable session configurations for all users.</span></span> <span data-ttu-id="2213f-114">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="2213f-114">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2213f-115">即使在 `Disable-PSRemoting` 執行之後，您仍然可以在本機電腦上建立回送連接。</span><span class="sxs-lookup"><span data-stu-id="2213f-115">Even after running `Disable-PSRemoting` you can still make loopback connections on the local machine.</span></span> <span data-ttu-id="2213f-116">回送連線是來自的 PowerShell 遠端會話，並連接到相同的本機電腦。</span><span class="sxs-lookup"><span data-stu-id="2213f-116">A loopback connection is a PowerShell remote session that originates from and connects to the same local machine.</span></span> <span data-ttu-id="2213f-117">外部來源的遠端會話仍會被封鎖。</span><span class="sxs-lookup"><span data-stu-id="2213f-117">Remote sessions from external sources remain blocked.</span></span> <span data-ttu-id="2213f-118">針對回送連接，您必須在 **EnableNetworkAccess** 參數中使用隱含的認證。</span><span class="sxs-lookup"><span data-stu-id="2213f-118">For loopback connections you must use implicit credentials along the **EnableNetworkAccess** parameter.</span></span> <span data-ttu-id="2213f-119">如需回送連接的詳細資訊，請參閱 [新的-PSSession](New-PSSession.md)。</span><span class="sxs-lookup"><span data-stu-id="2213f-119">For more information about loopback connections, see [New-PSSession](New-PSSession.md).</span></span>

<span data-ttu-id="2213f-120">若要執行此 Cmdlet，請使用 [以 **系統管理員身分執行** ] 選項啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2213f-120">To run this cmdlet, start Windows PowerShell with the **Run as administrator** option.</span></span>

## <span data-ttu-id="2213f-121">範例</span><span class="sxs-lookup"><span data-stu-id="2213f-121">EXAMPLES</span></span>

### <span data-ttu-id="2213f-122">範例1：防止所有會話設定的遠端存取</span><span class="sxs-lookup"><span data-stu-id="2213f-122">Example 1: Prevent remote access to all session configurations</span></span>

<span data-ttu-id="2213f-123">此範例會防止遠端存取電腦上的所有 PowerShell 交談端點設定。</span><span class="sxs-lookup"><span data-stu-id="2213f-123">This example prevents remote access to all PowerShell session endpoint configurations on the computer.</span></span>

```powershell
Disable-PSRemoting
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="2213f-124">範例2：防止遠端存取所有會話設定，而不需要確認提示</span><span class="sxs-lookup"><span data-stu-id="2213f-124">Example 2: Prevent remote access to all session configurations without confirmation prompt</span></span>

<span data-ttu-id="2213f-125">此範例會防止遠端存取電腦上的所有 PowerShell 交談端點設定，而不提示。</span><span class="sxs-lookup"><span data-stu-id="2213f-125">This example prevents remote access all PowerShell session endpoint configurations on the computer without prompting.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="2213f-126">範例3：執行此 Cmdlet 的效果</span><span class="sxs-lookup"><span data-stu-id="2213f-126">Example 3: Effects of running this cmdlet</span></span>

<span data-ttu-id="2213f-127">此範例顯示使用 Cmdlet 的效果 `Disable-PSRemoting` 。</span><span class="sxs-lookup"><span data-stu-id="2213f-127">This example shows the effect of using the `Disable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="2213f-128">若要執行此命令順序，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2213f-128">To run this command sequence, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="2213f-129">停用會話設定之後， `New-PSSession` Cmdlet 會嘗試在本機電腦上建立遠端會話 (也稱為「回送」 ) 。</span><span class="sxs-lookup"><span data-stu-id="2213f-129">After disabling the sessions configurations, the `New-PSSession` cmdlet attempts to create a remote session to the local computer (also known as a "loopback").</span></span> <span data-ttu-id="2213f-130">因為本機電腦上已停用遠端存取，所以命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="2213f-130">Because remote access is disabled on the local machine, the command fails.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error
 message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

### <span data-ttu-id="2213f-131">範例4：執行此 Cmdlet 和 Enable-PSRemoting 的效果</span><span class="sxs-lookup"><span data-stu-id="2213f-131">Example 4: Effects of running this cmdlet and Enable-PSRemoting</span></span>

<span data-ttu-id="2213f-132">此範例顯示使用和 Cmdlet 的會話設定效果 `Disable-PSRemoting` `Enable-PSRemoting` 。</span><span class="sxs-lookup"><span data-stu-id="2213f-132">This example shows the effect on the session configurations of using the `Disable-PSRemoting` and `Enable-PSRemoting` cmdlets.</span></span>

<span data-ttu-id="2213f-133">`Disable-PSRemoting` 用來停用對所有 PowerShell 交談端點設定的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="2213f-133">`Disable-PSRemoting` is used to disable remote access to all PowerShell session endpoint configurations.</span></span> <span data-ttu-id="2213f-134">**Force** 參數會抑制所有使用者提示。</span><span class="sxs-lookup"><span data-stu-id="2213f-134">The **Force** parameter suppresses all user prompts.</span></span> <span data-ttu-id="2213f-135">`Get-PSSessionConfiguration`和 `Format-Table` Cmdlet 會顯示電腦上的會話設定。</span><span class="sxs-lookup"><span data-stu-id="2213f-135">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations on the computer.</span></span>

<span data-ttu-id="2213f-136">輸出顯示所有具有網路權杖的遠端使用者都會遭到拒絕存取端點設定。</span><span class="sxs-lookup"><span data-stu-id="2213f-136">The output shows that all remote users with a network token are denied access to the endpoint configurations.</span></span> <span data-ttu-id="2213f-137">本機電腦上的 Administrators 群組可存取端點設定，只要它們是在本機連線 (也稱為回送) 和使用隱含的認證。</span><span class="sxs-lookup"><span data-stu-id="2213f-137">Administrators group on the local computer are allowed access to the endpoint configurations as long as they are connecting locally (also known as loopback) and using implicit credentials.</span></span>

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow BUILTIN\Administrators AccessAllowed
microsoft.powershell32        BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   BUILTIN\Administrators AccessAllowed
```

<span data-ttu-id="2213f-138">此 `Enable-PSRemoting` Cmdlet 會重新啟用對電腦上所有 PowerShell 交談端點設定的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="2213f-138">The `Enable-PSRemoting` cmdlet re-enables remote access to all PowerShell session endpoint configurations on the computer.</span></span> <span data-ttu-id="2213f-139">**Force** 參數會抑制所有使用者提示，並在不提示的情況下重新開機 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="2213f-139">The **Force** parameter suppresses all user prompts and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="2213f-140">新的輸出顯示已從所有會話設定中移除 **AccessDenied** 安全描述項。</span><span class="sxs-lookup"><span data-stu-id="2213f-140">The new output shows that the **AccessDenied** security descriptors have been removed from all session configurations.</span></span>

### <span data-ttu-id="2213f-141">範例5：已停用交談端點設定的回送連接</span><span class="sxs-lookup"><span data-stu-id="2213f-141">Example 5: Loopback connections with disabled session endpoint configurations</span></span>

<span data-ttu-id="2213f-142">此範例示範如何停用端點設定，並示範如何對已停用的端點進行成功的回送連接。</span><span class="sxs-lookup"><span data-stu-id="2213f-142">This example demonstrates how endpoint configurations are disabled, and shows how to make a successful loopback connection to a disabled endpoint.</span></span> <span data-ttu-id="2213f-143">`Disable-PSRemoting` 停用所有 PowerShell 交談端點設定。</span><span class="sxs-lookup"><span data-stu-id="2213f-143">`Disable-PSRemoting` disables all PowerShell session endpoint configurations.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message : Access is
denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [New-PSSession], PSRemotin
   gTransportException
    + FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed

```

```powershell
New-PSSession -ComputerName localhost -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

<span data-ttu-id="2213f-144">第一次使用 `New-PSSession` 嘗試建立本機電腦的遠端會話。</span><span class="sxs-lookup"><span data-stu-id="2213f-144">The first use of `New-PSSession` attempts to create a remote session to the local machine.</span></span> <span data-ttu-id="2213f-145">這種類型的連線會通過網路堆疊，且不是回送。</span><span class="sxs-lookup"><span data-stu-id="2213f-145">This type of connection goes through the network stack and is not a loopback.</span></span> <span data-ttu-id="2213f-146">因此，對已停用端點的連線嘗試會失敗，並出現「 **拒絕存取** 」錯誤。</span><span class="sxs-lookup"><span data-stu-id="2213f-146">Consequently, the connection attempt to the disabled endpoint fails with an **Access is denied** error.</span></span>

<span data-ttu-id="2213f-147">第二次使用時， `New-PSSession` 也會嘗試建立本機電腦的遠端會話。</span><span class="sxs-lookup"><span data-stu-id="2213f-147">The second use of `New-PSSession` also attempts to create a remote session to the local machine.</span></span>
<span data-ttu-id="2213f-148">在此情況下，它會成功，因為它是略過網路堆疊的回送連接。</span><span class="sxs-lookup"><span data-stu-id="2213f-148">In this case, it succeeds because it is a loopback connection that bypasses the network stack.</span></span>

<span data-ttu-id="2213f-149">當符合下列條件時，就會建立回送連接：</span><span class="sxs-lookup"><span data-stu-id="2213f-149">A loopback connection is created when the following conditions are met:</span></span>

- <span data-ttu-id="2213f-150">要連接的電腦名稱稱是 ' localhost '。</span><span class="sxs-lookup"><span data-stu-id="2213f-150">The computer name to connect to is 'localhost'.</span></span>
- <span data-ttu-id="2213f-151">未傳入任何認證。</span><span class="sxs-lookup"><span data-stu-id="2213f-151">No credentials are passed in.</span></span> <span data-ttu-id="2213f-152">目前登入的使用者 (隱含認證) 用於連接。</span><span class="sxs-lookup"><span data-stu-id="2213f-152">Current logged in user (implicit credentials) is used for the connection.</span></span>
- <span data-ttu-id="2213f-153">使用 **EnableNetworkAccess** 切換參數。</span><span class="sxs-lookup"><span data-stu-id="2213f-153">The **EnableNetworkAccess** switch parameter is used.</span></span>

<span data-ttu-id="2213f-154">如需回送連接的詳細資訊，請參閱 [新的-PSSession](New-PSSession.md) 檔。</span><span class="sxs-lookup"><span data-stu-id="2213f-154">For more information on loopback connections, see [New-PSSession](New-PSSession.md) document.</span></span>

### <span data-ttu-id="2213f-155">範例6：防止遠端存取具有自訂安全描述項的會話設定</span><span class="sxs-lookup"><span data-stu-id="2213f-155">Example 6: Prevent remote access to session configurations that have custom security descriptors</span></span>

<span data-ttu-id="2213f-156">此範例示範此 `Disable-PSRemoting` Cmdlet 會停用所有會話設定的遠端存取，這些設定包括具有自訂安全描述項的會話設定。</span><span class="sxs-lookup"><span data-stu-id="2213f-156">This example demonstrates that the `Disable-PSRemoting` cmdlet disables remote access to all session configurations that include session configurations with custom security descriptors.</span></span>

<span data-ttu-id="2213f-157">`Register-PSSessionConfiguration` 建立 **測試** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="2213f-157">`Register-PSSessionConfiguration` creates the **Test** session configuration.</span></span> <span data-ttu-id="2213f-158">**FilePath** 參數指定可自訂會話的會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="2213f-158">The **FilePath** parameter specifies a session configuration file that customizes the session.</span></span> <span data-ttu-id="2213f-159">**ShowSecurityDescriptorUI** 參數會顯示對話方塊，該對話方塊會設定會話設定的許可權。</span><span class="sxs-lookup"><span data-stu-id="2213f-159">The **ShowSecurityDescriptorUI** parameter displays a dialog box that sets permissions for the session configuration.</span></span> <span data-ttu-id="2213f-160">在 [許可權] 對話方塊中，我們會為指定的使用者建立自訂的完整存取權限。</span><span class="sxs-lookup"><span data-stu-id="2213f-160">In the Permissions dialog box, we create custom full-access permissions for the indicated user.</span></span>

<span data-ttu-id="2213f-161">`Get-PSSessionConfiguration`和 `Format-Table` Cmdlet 會顯示會話設定和其屬性。</span><span class="sxs-lookup"><span data-stu-id="2213f-161">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations and their properties.</span></span> <span data-ttu-id="2213f-162">輸出顯示 **測試** 會話設定允許指定使用者的互動式訪問和特殊許可權。</span><span class="sxs-lookup"><span data-stu-id="2213f-162">The output shows that the **Test** session configuration allows interactive access and special permissions for the indicated user.</span></span>

<span data-ttu-id="2213f-163">`Disable-PSRemoting` 停用對所有會話設定的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="2213f-163">`Disable-PSRemoting` disables remote access to all session configurations.</span></span>

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
DOMAIN01\User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\NETWORK AccessDenied, NTAUTHORITY\INTERACTIVE AccessAllowed,
BUILTIN\Administrators AccessAllowed, DOMAIN01\User01 AccessAllowed


[Server01] Connecting to remote server failed with the following error message : Access is denied. For more information, see the about_Rem
ote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

<span data-ttu-id="2213f-164">現在 `Get-PSSessionConfiguration` 和 `Format-Table` Cmdlet 會顯示所有網路使用者的 **AccessDenied** 安全描述項都已新增至所有會話設定，包括 **測試** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="2213f-164">Now the `Get-PSSessionConfiguration` and `Format-Table` cmdlets shows that an **AccessDenied** security descriptor for all network users is added to all session configurations, including the **Test** session configuration.</span></span> <span data-ttu-id="2213f-165">雖然其他安全描述項並未變更，但 "network_deny_all" 安全描述項的優先順序較高。</span><span class="sxs-lookup"><span data-stu-id="2213f-165">Although the other security descriptors are not changed, the "network_deny_all" security descriptor takes precedence.</span></span> <span data-ttu-id="2213f-166">這會由嘗試用 `New-PSSession` 來連接到 **測試** 會話設定來說明。</span><span class="sxs-lookup"><span data-stu-id="2213f-166">This is illustrated by the attempt to use `New-PSSession` to connect to the **Test** session configuration.</span></span>

### <span data-ttu-id="2213f-167">範例7：重新啟用對所選會話設定的遠端存取</span><span class="sxs-lookup"><span data-stu-id="2213f-167">Example 7: Re-enable remote access to selected session configurations</span></span>

<span data-ttu-id="2213f-168">此範例顯示如何只對選取的工作階段設定重新啟用遠端存取。</span><span class="sxs-lookup"><span data-stu-id="2213f-168">This example shows how to re-enable remote access only to selected session configurations.</span></span> <span data-ttu-id="2213f-169">停用所有會話設定之後，我們會重新啟用特定的會話。</span><span class="sxs-lookup"><span data-stu-id="2213f-169">After disabling all session configurations, we re-enable a specific session.</span></span>

<span data-ttu-id="2213f-170">此 `Set-PSSessionConfiguration` Cmdlet 是用來變更 **microsoft。ServerManager** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="2213f-170">The `Set-PSSessionConfiguration` cmdlet is used to change the **microsoft.ServerManager** session configuration.</span></span> <span data-ttu-id="2213f-171">**AccessMode** 參數的值為 [ **遠端** 重新啟用對設定的遠端存取]。</span><span class="sxs-lookup"><span data-stu-id="2213f-171">The **AccessMode** parameter with a value of **Remote** re-enables remote access to the configuration.</span></span>

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name Microsoft.ServerManager -AccessMode Remote -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
```

## <span data-ttu-id="2213f-172">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2213f-172">PARAMETERS</span></span>

### <span data-ttu-id="2213f-173">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2213f-173">-Confirm</span></span>

<span data-ttu-id="2213f-174">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="2213f-174">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2213f-175">-Force</span><span class="sxs-lookup"><span data-stu-id="2213f-175">-Force</span></span>
<span data-ttu-id="2213f-176">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="2213f-176">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="2213f-177">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2213f-177">-WhatIf</span></span>

<span data-ttu-id="2213f-178">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="2213f-178">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2213f-179">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="2213f-179">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2213f-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2213f-180">CommonParameters</span></span>

<span data-ttu-id="2213f-181">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2213f-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2213f-182">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2213f-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2213f-183">輸入</span><span class="sxs-lookup"><span data-stu-id="2213f-183">INPUTS</span></span>

### <span data-ttu-id="2213f-184">無</span><span class="sxs-lookup"><span data-stu-id="2213f-184">None</span></span>

<span data-ttu-id="2213f-185">您無法透過管線將任何物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2213f-185">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="2213f-186">輸出</span><span class="sxs-lookup"><span data-stu-id="2213f-186">OUTPUTS</span></span>

### <span data-ttu-id="2213f-187">無</span><span class="sxs-lookup"><span data-stu-id="2213f-187">None</span></span>

<span data-ttu-id="2213f-188">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="2213f-188">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2213f-189">注意</span><span class="sxs-lookup"><span data-stu-id="2213f-189">NOTES</span></span>

- <span data-ttu-id="2213f-190">停用會話設定不會復原或 Cmdlet 所做的所有變更 `Enable-PSRemoting` `Enable-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="2213f-190">Disabling the session configurations does not undo all the changes that were made by the `Enable-PSRemoting` or `Enable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="2213f-191">您可能必須手動復原下列變更。</span><span class="sxs-lookup"><span data-stu-id="2213f-191">You might have to undo the following changes manually.</span></span>

  1. <span data-ttu-id="2213f-192">停止及停用 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="2213f-192">Stop and disable the WinRM service.</span></span>
  2. <span data-ttu-id="2213f-193">刪除接受任何 IP 位址上之要求的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="2213f-193">Delete the listener that accepts requests on any IP address.</span></span>
  3. <span data-ttu-id="2213f-194">停用 WS-Management 通訊的防火牆例外。</span><span class="sxs-lookup"><span data-stu-id="2213f-194">Disable the firewall exceptions for WS-Management communications.</span></span>
  4. <span data-ttu-id="2213f-195">將 LocalAccountTokenFilterPolicy 的值還原為 0，以限制對電腦上之 Administrators 群組成員的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="2213f-195">Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the Administrators group on the computer.</span></span>

  <span data-ttu-id="2213f-196">工作階段設定是定義工作階段環境的一組設定。</span><span class="sxs-lookup"><span data-stu-id="2213f-196">A session configuration is a group of settings that define the environment for a session.</span></span> <span data-ttu-id="2213f-197">連線到電腦的每個工作階段都必須使用在本機電腦上註冊的其中一項工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="2213f-197">Every session that connects to the computer must use one of the session configurations that are registered on the computer.</span></span> <span data-ttu-id="2213f-198">如果拒絕對所有工作階段設定的遠端存取，即可有效防止遠端使用者建立連線到電腦的工作階段。</span><span class="sxs-lookup"><span data-stu-id="2213f-198">By denying remote access to all session configurations, you effectively prevent remote users from establishing sessions that connect to the computer.</span></span>

  <span data-ttu-id="2213f-199">在 Windows PowerShell 2.0 中，會 `Disable-PSRemoting` 將 Deny_All 專案加入至所有會話設定的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="2213f-199">In Windows PowerShell 2.0, `Disable-PSRemoting` adds a Deny_All entry to the security descriptors of all session configurations.</span></span> <span data-ttu-id="2213f-200">此設定可防止所有使用者在本機電腦上建立使用者管理的會話。</span><span class="sxs-lookup"><span data-stu-id="2213f-200">This setting prevents all users from creating user-managed sessions to the local computer.</span></span> <span data-ttu-id="2213f-201">在 Windows PowerShell 3.0 中，會 `Disable-PSRemoting` 將 Network_Deny_All 專案加入至所有會話設定的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="2213f-201">In Windows PowerShell 3.0, `Disable-PSRemoting` adds a Network_Deny_All entry to the security descriptors of all session configurations.</span></span> <span data-ttu-id="2213f-202">這項設定可防止其他電腦上的使用者在本機電腦上建立使用者管理的會話，但允許本機電腦的使用者建立使用者管理的回送會話。</span><span class="sxs-lookup"><span data-stu-id="2213f-202">This setting prevents users on other computers from creating user-managed sessions on the local computer, but allows users of the local computer to create user-managed loopback sessions.</span></span>

  <span data-ttu-id="2213f-203">在 Windows PowerShell 2.0 中， `Disable-PSRemoting` 相當於 `Disable-PSSessionConfiguration -Name *` 。</span><span class="sxs-lookup"><span data-stu-id="2213f-203">In Windows PowerShell 2.0, `Disable-PSRemoting` is the equivalent of `Disable-PSSessionConfiguration -Name *`.</span></span> <span data-ttu-id="2213f-204">在 Windows PowerShell 3.0 和更新版本中， `Disable-PSRemoting` 相當於 `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`</span><span class="sxs-lookup"><span data-stu-id="2213f-204">In Windows PowerShell 3.0 and later releases, `Disable-PSRemoting` is the equivalent of `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`</span></span>

## <span data-ttu-id="2213f-205">相關連結</span><span class="sxs-lookup"><span data-stu-id="2213f-205">RELATED LINKS</span></span>

[<span data-ttu-id="2213f-206">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2213f-206">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="2213f-207">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="2213f-207">Enable-PSRemoting</span></span>](Enable-PSRemoting.md)

[<span data-ttu-id="2213f-208">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2213f-208">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="2213f-209">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="2213f-209">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="2213f-210">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2213f-210">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="2213f-211">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2213f-211">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="2213f-212">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="2213f-212">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="2213f-213">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="2213f-213">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
