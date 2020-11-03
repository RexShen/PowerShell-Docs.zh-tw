---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 82db14f6819a003f4f51a35844a9fcce7a146f03
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205172"
---
# <span data-ttu-id="62cdd-103">Disable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="62cdd-103">Disable-PSRemoting</span></span>

## <span data-ttu-id="62cdd-104">概要</span><span class="sxs-lookup"><span data-stu-id="62cdd-104">SYNOPSIS</span></span>
<span data-ttu-id="62cdd-105">防止 PowerShell 端點接收遠端連線。</span><span class="sxs-lookup"><span data-stu-id="62cdd-105">Prevents PowerShell endpoints from receiving remote connections.</span></span>

## <span data-ttu-id="62cdd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="62cdd-106">SYNTAX</span></span>

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="62cdd-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="62cdd-107">DESCRIPTION</span></span>

<span data-ttu-id="62cdd-108">此 `Disable-PSRemoting` Cmdlet 會封鎖對本機電腦上所有 PowerShell 版本6和更高交談端點設定的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="62cdd-108">The `Disable-PSRemoting` cmdlet blocks remote access to all PowerShell version 6 and greater session endpoint configurations on the local computer.</span></span> <span data-ttu-id="62cdd-109">它不會影響 Windows PowerShell 端點設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-109">It does not affect Windows PowerShell endpoint configurations.</span></span> <span data-ttu-id="62cdd-110">若要停用 Windows PowerShell 交談端點設定，請 `Disable-PSRemoting` 從 Windows PowerShell 會話內執行命令。</span><span class="sxs-lookup"><span data-stu-id="62cdd-110">To disable Windows PowerShell session endpoint configurations, run `Disable-PSRemoting` command from within a Windows PowerShell session.</span></span>

<span data-ttu-id="62cdd-111">若要重新啟用所有 PowerShell 第6版和更高交談端點設定的遠端存取，請使用 `Enable-PSRemoting` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="62cdd-111">To re-enable remote access to all PowerShell version 6 and greater session endpoint configurations, use the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="62cdd-112">若要重新啟用對所有 Windows PowerShell 交談端點設定的遠端存取，請 `Enable-PSRemoting` 從 Windows PowerShell 會話內部執行。</span><span class="sxs-lookup"><span data-stu-id="62cdd-112">To re-enable remote access to all Windows PowerShell session endpoint configurations, run `Enable-PSRemoting` from within a Windows PowerShell session.</span></span>

> [!NOTE]
> <span data-ttu-id="62cdd-113">如果您想要停用本機 Windows 電腦的所有 PowerShell 遠端存取，您必須從 PowerShell 6 版或更高版本的會話，以及從 Windows PowerShell 會話內部執行此命令。</span><span class="sxs-lookup"><span data-stu-id="62cdd-113">If you want to disable all PowerShell remote access to a local Windows machine, you must run this command both from a within PowerShell version 6 or greater session and from within a Windows PowerShell session.</span></span> <span data-ttu-id="62cdd-114">預設會在所有的 Windows 電腦上安裝 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="62cdd-114">Windows PowerShell is installed on all Windows machines by default.</span></span>

<span data-ttu-id="62cdd-115">若要停用並重新啟用對特定交談端點設定的遠端存取，請使用 `Enable-PSSessionConfiguration` 和 `Disable-PSSessionConfiguration` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="62cdd-115">To disable and re-enable remote access to specific session endpoint configurations, use the `Enable-PSSessionConfiguration` and `Disable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="62cdd-116">若要設定個別端點的特定存取設定，請使用 `Set-PSSessionConfiguration` Cmdlet 搭配 **AccessMode** 參數。</span><span class="sxs-lookup"><span data-stu-id="62cdd-116">To set specific access configurations of individual endpoints, use the `Set-PSSessionConfiguration` cmdlet along with the **AccessMode** parameter.</span></span> <span data-ttu-id="62cdd-117">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="62cdd-117">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="62cdd-118">即使在 `Disable-PSRemoting` 執行之後，您仍然可以在本機電腦上建立回送連接。</span><span class="sxs-lookup"><span data-stu-id="62cdd-118">Even after running `Disable-PSRemoting` you can still make loopback connections on the local machine.</span></span> <span data-ttu-id="62cdd-119">回送連線是來自的 PowerShell 遠端會話，並連接到相同的本機電腦。</span><span class="sxs-lookup"><span data-stu-id="62cdd-119">A loopback connection is a PowerShell remote session that originates from and connects to the same local machine.</span></span> <span data-ttu-id="62cdd-120">外部來源的遠端會話仍會被封鎖。</span><span class="sxs-lookup"><span data-stu-id="62cdd-120">Remote sessions from external sources remain blocked.</span></span> <span data-ttu-id="62cdd-121">針對回送連接，您必須在 **EnableNetworkAccess** 參數中使用隱含的認證。</span><span class="sxs-lookup"><span data-stu-id="62cdd-121">For loopback connections you must use implicit credentials along the **EnableNetworkAccess** parameter.</span></span> <span data-ttu-id="62cdd-122">如需回送連接的詳細資訊，請參閱 [新的-PSSession](New-PSSession.md)。</span><span class="sxs-lookup"><span data-stu-id="62cdd-122">For more information about loopback connections, see [New-PSSession](New-PSSession.md).</span></span>

<span data-ttu-id="62cdd-123">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="62cdd-123">This cmdlet is only available on the Windows platform.</span></span> <span data-ttu-id="62cdd-124">它無法在 Linux 或 macOS 版本的 PowerShell 上使用。</span><span class="sxs-lookup"><span data-stu-id="62cdd-124">It is not available on Linux or macOS versions of PowerShell.</span></span> <span data-ttu-id="62cdd-125">若要執行此 Cmdlet，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="62cdd-125">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

## <span data-ttu-id="62cdd-126">範例</span><span class="sxs-lookup"><span data-stu-id="62cdd-126">EXAMPLES</span></span>

### <span data-ttu-id="62cdd-127">範例1：防止遠端存取所有 PowerShell 會話設定</span><span class="sxs-lookup"><span data-stu-id="62cdd-127">Example 1: Prevent remote access to all PowerShell session configurations</span></span>

<span data-ttu-id="62cdd-128">此範例會防止遠端存取電腦上的所有 PowerShell 交談端點設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-128">This example prevents remote access to all PowerShell session endpoint configurations on the computer.</span></span>

```powershell
Disable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="62cdd-129">範例2：防止遠端存取所有 PowerShell 會話設定，而不需要確認提示</span><span class="sxs-lookup"><span data-stu-id="62cdd-129">Example 2: Prevent remote access to all PowerShell session configurations without confirmation prompt</span></span>

<span data-ttu-id="62cdd-130">此範例會防止遠端存取電腦上的所有 PowerShell 交談端點設定，而不提示。</span><span class="sxs-lookup"><span data-stu-id="62cdd-130">This example prevents remote access all PowerShell session endpoint configurations on the computer without prompting.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### <span data-ttu-id="62cdd-131">範例3：執行此 Cmdlet 的效果</span><span class="sxs-lookup"><span data-stu-id="62cdd-131">Example 3: Effects of running this cmdlet</span></span>

<span data-ttu-id="62cdd-132">此範例顯示使用 Cmdlet 的效果 `Disable-PSRemoting` 。</span><span class="sxs-lookup"><span data-stu-id="62cdd-132">This example shows the effect of using the `Disable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="62cdd-133">若要執行此命令順序，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="62cdd-133">To run this command sequence, start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="62cdd-134">停用會話設定之後， `New-PSSession` Cmdlet 會嘗試在本機電腦上建立遠端會話 (也稱為「回送」 ) 。</span><span class="sxs-lookup"><span data-stu-id="62cdd-134">After disabling the sessions configurations, the `New-PSSession` cmdlet attempts to create a remote session to the local computer (also known as a "loopback").</span></span> <span data-ttu-id="62cdd-135">因為本機電腦上已停用遠端存取，所以命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="62cdd-135">Because remote access is disabled on the local machine, the command fails.</span></span>

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
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

### <span data-ttu-id="62cdd-136">範例4：執行此 Cmdlet 和 Enable-PSRemoting 的效果</span><span class="sxs-lookup"><span data-stu-id="62cdd-136">Example 4: Effects of running this cmdlet and Enable-PSRemoting</span></span>

<span data-ttu-id="62cdd-137">此範例顯示使用和 Cmdlet 的會話設定效果 `Disable-PSRemoting` `Enable-PSRemoting` 。</span><span class="sxs-lookup"><span data-stu-id="62cdd-137">This example shows the effect on the session configurations of using the `Disable-PSRemoting` and `Enable-PSRemoting` cmdlets.</span></span>

<span data-ttu-id="62cdd-138">`Disable-PSRemoting` 用來停用對所有 PowerShell 交談端點設定的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="62cdd-138">`Disable-PSRemoting` is used to disable remote access to all PowerShell session endpoint configurations.</span></span> <span data-ttu-id="62cdd-139">**Force** 參數會抑制所有使用者提示。</span><span class="sxs-lookup"><span data-stu-id="62cdd-139">The **Force** parameter suppresses all user prompts.</span></span> <span data-ttu-id="62cdd-140">`Get-PSSessionConfiguration`和 `Format-Table` Cmdlet 會顯示電腦上的會話設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-140">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations on the computer.</span></span>

<span data-ttu-id="62cdd-141">輸出顯示所有具有網路權杖的遠端使用者都會遭到拒絕存取端點設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-141">The output shows that all remote users with a network token are denied access to the endpoint configurations.</span></span> <span data-ttu-id="62cdd-142">本機電腦上的 Administrators 群組可存取端點設定，只要它們是在本機連線 (也稱為回送) 和使用隱含的認證。</span><span class="sxs-lookup"><span data-stu-id="62cdd-142">Administrators group on the local computer are allowed access to the endpoint configurations as long as they are connecting locally (also known as loopback) and using implicit credentials.</span></span>

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
```

<span data-ttu-id="62cdd-143">此 `Enable-PSRemoting` Cmdlet 會重新啟用對電腦上所有 PowerShell 交談端點設定的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="62cdd-143">The `Enable-PSRemoting` cmdlet re-enables remote access to all PowerShell session endpoint configurations on the computer.</span></span> <span data-ttu-id="62cdd-144">**Force** 參數會抑制所有使用者提示，並在不提示的情況下重新開機 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="62cdd-144">The **Force** parameter suppresses all user prompts and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="62cdd-145">新的輸出顯示已從所有會話設定中移除 **AccessDenied** 安全描述項。</span><span class="sxs-lookup"><span data-stu-id="62cdd-145">The new output shows that the **AccessDenied** security descriptors have been removed from all session configurations.</span></span>

### <span data-ttu-id="62cdd-146">範例5：已停用交談端點設定的回送連接</span><span class="sxs-lookup"><span data-stu-id="62cdd-146">Example 5: Loopback connections with disabled session endpoint configurations</span></span>

<span data-ttu-id="62cdd-147">此範例示範如何停用端點設定，並示範如何對已停用的端點進行成功的回送連接。</span><span class="sxs-lookup"><span data-stu-id="62cdd-147">This example demonstrates how endpoint configurations are disabled, and shows how to make a successful loopback connection to a disabled endpoint.</span></span> <span data-ttu-id="62cdd-148">`Disable-PSRemoting` 停用所有 PowerShell 交談端點設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-148">`Disable-PSRemoting` disables all PowerShell session endpoint configurations.</span></span>

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -Credential (Get-Credential)
```

```Output
PowerShell credential request
Enter your credentials.
User: UserName
Password for user UserName: ************

New-PSSession: [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

<span data-ttu-id="62cdd-149">第一次使用 `New-PSSession` 嘗試建立本機電腦的遠端會話。</span><span class="sxs-lookup"><span data-stu-id="62cdd-149">The first use of `New-PSSession` attempts to create a remote session to the local machine.</span></span> <span data-ttu-id="62cdd-150">**ConfigurationName** 參數是用來指定停用的 PowerShell 端點。</span><span class="sxs-lookup"><span data-stu-id="62cdd-150">The **ConfigurationName** parameter is used to specify a disabled PowerShell endpoint.</span></span> <span data-ttu-id="62cdd-151">認證會透過 **Credential** 參數明確地傳遞至命令。</span><span class="sxs-lookup"><span data-stu-id="62cdd-151">Credentials are explicitly passed to the command through the **Credential** parameter.</span></span> <span data-ttu-id="62cdd-152">這種類型的連線會通過網路堆疊，且不是回送。</span><span class="sxs-lookup"><span data-stu-id="62cdd-152">This type of connection goes through the network stack and is not a loopback.</span></span> <span data-ttu-id="62cdd-153">因此，對已停用端點的連線嘗試會失敗，並出現「 **拒絕存取** 」錯誤。</span><span class="sxs-lookup"><span data-stu-id="62cdd-153">Consequently, the connection attempt to the disabled endpoint fails with an **Access is denied** error.</span></span>

<span data-ttu-id="62cdd-154">第二次使用時， `New-PSSession` 也會嘗試建立本機電腦的遠端會話。</span><span class="sxs-lookup"><span data-stu-id="62cdd-154">The second use of `New-PSSession` also attempts to create a remote session to the local machine.</span></span>
<span data-ttu-id="62cdd-155">在此情況下，它會成功，因為它是略過網路堆疊的回送連接。</span><span class="sxs-lookup"><span data-stu-id="62cdd-155">In this case, it succeeds because it is a loopback connection that bypasses the network stack.</span></span>

<span data-ttu-id="62cdd-156">當符合下列條件時，就會建立回送連接：</span><span class="sxs-lookup"><span data-stu-id="62cdd-156">A loopback connection is created when the following conditions are met:</span></span>

- <span data-ttu-id="62cdd-157">要連接的電腦名稱稱是 ' localhost '。</span><span class="sxs-lookup"><span data-stu-id="62cdd-157">The computer name to connect to is 'localhost'.</span></span>
- <span data-ttu-id="62cdd-158">未傳入任何認證。</span><span class="sxs-lookup"><span data-stu-id="62cdd-158">No credentials are passed in.</span></span> <span data-ttu-id="62cdd-159">目前登入的使用者 (隱含認證) 用於連接。</span><span class="sxs-lookup"><span data-stu-id="62cdd-159">Current logged in user (implicit credentials) is used for the connection.</span></span>
- <span data-ttu-id="62cdd-160">使用 **EnableNetworkAccess** 切換參數。</span><span class="sxs-lookup"><span data-stu-id="62cdd-160">The **EnableNetworkAccess** switch parameter is used.</span></span>

<span data-ttu-id="62cdd-161">如需回送連接的詳細資訊，請參閱 [新的-PSSession](New-PSSession.md) 檔。</span><span class="sxs-lookup"><span data-stu-id="62cdd-161">For more information on loopback connections, see [New-PSSession](New-PSSession.md) document.</span></span>

### <span data-ttu-id="62cdd-162">範例6：停用所有 PowerShell 遠端端點設定</span><span class="sxs-lookup"><span data-stu-id="62cdd-162">Example 6: Disabling all PowerShell remoting endpoint configurations</span></span>

<span data-ttu-id="62cdd-163">此範例示範如何 `Disable-PSRemoting` 執行命令不會影響 Windows PowerShell 端點設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-163">This example demonstrates how running the `Disable-PSRemoting` command does not affect Windows PowerShell endpoint configurations.</span></span> <span data-ttu-id="62cdd-164">`Get-PSSessionConfiguration` 在 Windows PowerShell 中執行會顯示所有端點設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-164">`Get-PSSessionConfiguration` run within Windows PowerShell shows all endpoint configurations.</span></span> <span data-ttu-id="62cdd-165">我們看到 Windows PowerShell 端點設定未停用。</span><span class="sxs-lookup"><span data-stu-id="62cdd-165">We see that the Windows PowerShell endpoint configurations are not disabled.</span></span>

```powershell
Disable-PSRemoting -Force
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

```powershell
powershell.exe -command 'Disable-PSRemoting -Force'
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting or
Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the
Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management
                Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

<span data-ttu-id="62cdd-166">若要停用這些端點設定， `Disable-PSRemoting` 必須在 Windows PowerShell 會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="62cdd-166">To disable these endpoint configurations, the `Disable-PSRemoting` command must be run from within a Windows PowerShell session.</span></span> <span data-ttu-id="62cdd-167">現在， `Get-PSSessionConfiguration` 從 Windows PowerShell 中執行，顯示所有端點設定都已停用。</span><span class="sxs-lookup"><span data-stu-id="62cdd-167">Now, `Get-PSSessionConfiguration` run from within Windows PowerShell shows that all endpoint configurations are disabled.</span></span>

### <span data-ttu-id="62cdd-168">範例7：防止遠端存取具有自訂安全描述項的會話設定</span><span class="sxs-lookup"><span data-stu-id="62cdd-168">Example 7: Prevent remote access to session configurations that have custom security descriptors</span></span>

<span data-ttu-id="62cdd-169">此範例示範此 `Disable-PSRemoting` Cmdlet 會停用所有會話設定的遠端存取，這些設定包括具有自訂安全描述項的會話設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-169">This example demonstrates that the `Disable-PSRemoting` cmdlet disables remote access to all session configurations that include session configurations with custom security descriptors.</span></span>

<span data-ttu-id="62cdd-170">`Register-PSSessionConfiguration` 建立 **測試** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-170">`Register-PSSessionConfiguration` creates the **Test** session configuration.</span></span> <span data-ttu-id="62cdd-171">**FilePath** 參數指定可自訂會話的會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="62cdd-171">The **FilePath** parameter specifies a session configuration file that customizes the session.</span></span> <span data-ttu-id="62cdd-172">**ShowSecurityDescriptorUI** 參數會顯示對話方塊，該對話方塊會設定會話設定的許可權。</span><span class="sxs-lookup"><span data-stu-id="62cdd-172">The **ShowSecurityDescriptorUI** parameter displays a dialog box that sets permissions for the session configuration.</span></span> <span data-ttu-id="62cdd-173">在 [許可權] 對話方塊中，我們會為指定的使用者建立自訂的完整存取權限。</span><span class="sxs-lookup"><span data-stu-id="62cdd-173">In the Permissions dialog box, we create custom full-access permissions for the indicated user.</span></span>

<span data-ttu-id="62cdd-174">`Get-PSSessionConfiguration`和 `Format-Table` Cmdlet 會顯示會話設定和其屬性。</span><span class="sxs-lookup"><span data-stu-id="62cdd-174">The `Get-PSSessionConfiguration` and `Format-Table` cmdlets display the session configurations and their properties.</span></span> <span data-ttu-id="62cdd-175">輸出顯示 **測試** 會話設定允許指定使用者的互動式訪問和特殊許可權。</span><span class="sxs-lookup"><span data-stu-id="62cdd-175">The output shows that the **Test** session configuration allows interactive access and special permissions for the indicated user.</span></span>

<span data-ttu-id="62cdd-176">`Disable-PSRemoting` 停用對所有會話設定的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="62cdd-176">`Disable-PSRemoting` disables remote access to all session configurations.</span></span>

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, User01 AccessAllowed

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName Test
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

<span data-ttu-id="62cdd-177">現在 `Get-PSSessionConfiguration` 和 `Format-Table` Cmdlet 會顯示所有網路使用者的 **AccessDenied** 安全描述項都已新增至所有會話設定，包括 **測試** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-177">Now the `Get-PSSessionConfiguration` and `Format-Table` cmdlets shows that an **AccessDenied** security descriptor for all network users is added to all session configurations, including the **Test** session configuration.</span></span> <span data-ttu-id="62cdd-178">雖然其他安全描述項並未變更，但 "network_deny_all" 安全描述項的優先順序較高。</span><span class="sxs-lookup"><span data-stu-id="62cdd-178">Although the other security descriptors are not changed, the "network_deny_all" security descriptor takes precedence.</span></span> <span data-ttu-id="62cdd-179">這會由嘗試用 `New-PSSession` 來連接到 **測試** 會話設定來說明。</span><span class="sxs-lookup"><span data-stu-id="62cdd-179">This is illustrated by the attempt to use `New-PSSession` to connect to the **Test** session configuration.</span></span>

### <span data-ttu-id="62cdd-180">範例8：重新啟用對所選會話設定的遠端存取</span><span class="sxs-lookup"><span data-stu-id="62cdd-180">Example 8: Re-enable remote access to selected session configurations</span></span>

<span data-ttu-id="62cdd-181">此範例顯示如何只對選取的工作階段設定重新啟用遠端存取。</span><span class="sxs-lookup"><span data-stu-id="62cdd-181">This example shows how to re-enable remote access only to selected session configurations.</span></span> <span data-ttu-id="62cdd-182">停用所有會話設定之後，我們會重新啟用特定的會話。</span><span class="sxs-lookup"><span data-stu-id="62cdd-182">After disabling all session configurations, we re-enable a specific session.</span></span>

<span data-ttu-id="62cdd-183">此 `Set-PSSessionConfiguration` Cmdlet 可用來變更 **PowerShell. 6** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-183">The `Set-PSSessionConfiguration` cmdlet is used to change the **PowerShell.6** session configuration.</span></span> <span data-ttu-id="62cdd-184">**AccessMode** 參數的值為 [ **遠端** 重新啟用對設定的遠端存取]。</span><span class="sxs-lookup"><span data-stu-id="62cdd-184">The **AccessMode** parameter with a value of **Remote** re-enables remote access to the configuration.</span></span>

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name PowerShell.6 -AccessMode Remote -Force
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

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\ ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
```

## <span data-ttu-id="62cdd-185">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="62cdd-185">PARAMETERS</span></span>

### <span data-ttu-id="62cdd-186">-Confirm</span><span class="sxs-lookup"><span data-stu-id="62cdd-186">-Confirm</span></span>

<span data-ttu-id="62cdd-187">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="62cdd-187">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="62cdd-188">-Force</span><span class="sxs-lookup"><span data-stu-id="62cdd-188">-Force</span></span>

<span data-ttu-id="62cdd-189">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="62cdd-189">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="62cdd-190">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="62cdd-190">-WhatIf</span></span>

<span data-ttu-id="62cdd-191">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="62cdd-191">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="62cdd-192">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="62cdd-192">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="62cdd-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="62cdd-193">CommonParameters</span></span>

<span data-ttu-id="62cdd-194">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="62cdd-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="62cdd-195">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="62cdd-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="62cdd-196">輸入</span><span class="sxs-lookup"><span data-stu-id="62cdd-196">INPUTS</span></span>

### <span data-ttu-id="62cdd-197">無</span><span class="sxs-lookup"><span data-stu-id="62cdd-197">None</span></span>

<span data-ttu-id="62cdd-198">您無法透過管線將任何物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="62cdd-198">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="62cdd-199">輸出</span><span class="sxs-lookup"><span data-stu-id="62cdd-199">OUTPUTS</span></span>

### <span data-ttu-id="62cdd-200">無</span><span class="sxs-lookup"><span data-stu-id="62cdd-200">None</span></span>

<span data-ttu-id="62cdd-201">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="62cdd-201">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="62cdd-202">注意</span><span class="sxs-lookup"><span data-stu-id="62cdd-202">NOTES</span></span>

- <span data-ttu-id="62cdd-203">停用會話設定不會復原或 Cmdlet 所做的所有變更 `Enable-PSRemoting` `Enable-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="62cdd-203">Disabling the session configurations does not undo all the changes that were made by the `Enable-PSRemoting` or `Enable-PSSessionConfiguration` cmdlets.</span></span> <span data-ttu-id="62cdd-204">您可能必須手動復原下列變更。</span><span class="sxs-lookup"><span data-stu-id="62cdd-204">You might have to undo the following changes manually.</span></span>

  1. <span data-ttu-id="62cdd-205">停止及停用 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="62cdd-205">Stop and disable the WinRM service.</span></span>
  2. <span data-ttu-id="62cdd-206">刪除接受任何 IP 位址上之要求的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="62cdd-206">Delete the listener that accepts requests on any IP address.</span></span>
  3. <span data-ttu-id="62cdd-207">停用 WS-Management 通訊的防火牆例外。</span><span class="sxs-lookup"><span data-stu-id="62cdd-207">Disable the firewall exceptions for WS-Management communications.</span></span>
  4. <span data-ttu-id="62cdd-208">將 LocalAccountTokenFilterPolicy 的值還原為 0，以限制對電腦上之 Administrators 群組成員的遠端存取。</span><span class="sxs-lookup"><span data-stu-id="62cdd-208">Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the Administrators group on the computer.</span></span>

- <span data-ttu-id="62cdd-209">交談端點設定是定義會話環境的一組設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-209">A session endpoint configuration is a group of settings that define the environment for a session.</span></span>
  <span data-ttu-id="62cdd-210">連接到電腦的每個會話都必須使用在電腦上註冊的其中一個交談端點設定。</span><span class="sxs-lookup"><span data-stu-id="62cdd-210">Every session that connects to the computer must use one of the session endpoint configurations that are registered on the computer.</span></span> <span data-ttu-id="62cdd-211">藉由拒絕對所有交談端點設定的遠端存取，您可以有效防止遠端使用者建立連線到電腦的會話。</span><span class="sxs-lookup"><span data-stu-id="62cdd-211">By denying remote access to all session endpoint configurations, you effectively prevent remote users from establishing sessions that connect to the computer.</span></span>

## <span data-ttu-id="62cdd-212">相關連結</span><span class="sxs-lookup"><span data-stu-id="62cdd-212">RELATED LINKS</span></span>

[<span data-ttu-id="62cdd-213">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="62cdd-213">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="62cdd-214">Enable-PSRemoting</span><span class="sxs-lookup"><span data-stu-id="62cdd-214">Enable-PSRemoting</span></span>](Enable-PSRemoting.md)

[<span data-ttu-id="62cdd-215">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="62cdd-215">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="62cdd-216">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="62cdd-216">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="62cdd-217">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="62cdd-217">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="62cdd-218">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="62cdd-218">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="62cdd-219">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="62cdd-219">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="62cdd-220">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="62cdd-220">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

