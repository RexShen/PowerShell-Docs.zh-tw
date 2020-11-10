---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: 8f782a7d1cc4403c3f212ff7973eb2c173be4342
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387578"
---
# <span data-ttu-id="6fcbd-103">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="6fcbd-103">Connect-PSSession</span></span>

## <span data-ttu-id="6fcbd-104">概要</span><span class="sxs-lookup"><span data-stu-id="6fcbd-104">SYNOPSIS</span></span>
<span data-ttu-id="6fcbd-105">重新連線至已中斷連線的工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-105">Reconnects to disconnected sessions.</span></span>

## <span data-ttu-id="6fcbd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6fcbd-106">SYNTAX</span></span>

### <span data-ttu-id="6fcbd-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="6fcbd-107">Name (Default)</span></span>

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
  [<CommonParameters>]
```

### <span data-ttu-id="6fcbd-108">工作階段</span><span class="sxs-lookup"><span data-stu-id="6fcbd-108">Session</span></span>

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
  [<CommonParameters>]
```

### <span data-ttu-id="6fcbd-109">ComputerNameGuid</span><span class="sxs-lookup"><span data-stu-id="6fcbd-109">ComputerNameGuid</span></span>

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
  -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
  [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
  [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6fcbd-110">ComputerName</span><span class="sxs-lookup"><span data-stu-id="6fcbd-110">ComputerName</span></span>

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
  [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
  [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
  [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6fcbd-111">ConnectionUriGuid</span><span class="sxs-lookup"><span data-stu-id="6fcbd-111">ConnectionUriGuid</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
  -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
  [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>]
  [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6fcbd-112">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="6fcbd-112">ConnectionUri</span></span>

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
  [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
  [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>]
  [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6fcbd-113">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6fcbd-113">InstanceId</span></span>

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
  [<CommonParameters>]
```

### <span data-ttu-id="6fcbd-114">Id</span><span class="sxs-lookup"><span data-stu-id="6fcbd-114">Id</span></span>

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6fcbd-115">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6fcbd-115">DESCRIPTION</span></span>

<span data-ttu-id="6fcbd-116">此 `Connect-PSSession` Cmdlet 會重新連接到使用者管理的 PowerShell 會話， ( **pssession** ) 已中斷連線。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-116">The `Connect-PSSession` cmdlet reconnects to user-managed PowerShell sessions ( **PSSessions** ) that were disconnected.</span></span> <span data-ttu-id="6fcbd-117">它適用于刻意中斷連線的會話，例如使用 Cmdlet `Disconnect-PSSession` 或 Cmdlet 的 **InDisconnectedSession** 參數 `Invoke-Command` ，以及不慎中斷連線的會話，例如暫時性網路中斷。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-117">It works on sessions that are disconnected intentionally, such as by using the `Disconnect-PSSession` cmdlet or the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet, and those that were disconnected unintentionally, such as by a temporary network outage.</span></span>

<span data-ttu-id="6fcbd-118">`Connect-PSSession` 可以連接到由相同使用者啟動的任何已中斷連線的會話。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-118">`Connect-PSSession` can connect to any disconnected session that was started by the same user.</span></span> <span data-ttu-id="6fcbd-119">這些包括從其他電腦上的其他會話啟動或中斷連線的電腦。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-119">These include those that were started by or disconnected from other sessions on other computers.</span></span>

<span data-ttu-id="6fcbd-120">但是， `Connect-PSSession` 無法連接到已中斷或已關閉的會話，或使用 Cmdlet 啟動的互動式會話 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-120">However, `Connect-PSSession` cannot connect to broken or closed sessions, or interactive sessions started by using the `Enter-PSSession` cmdlet.</span></span> <span data-ttu-id="6fcbd-121">您也無法連線其他使用者啟動的工作階段，除非您可以提供建立工作階段之使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-121">Also you cannot connect sessions to sessions started by other users, unless you can provide the credentials of the user who created the session.</span></span>

<span data-ttu-id="6fcbd-122">如需中斷連線工作階段功能的詳細資訊，請參閱 [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-122">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="6fcbd-123">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-123">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="6fcbd-124">範例</span><span class="sxs-lookup"><span data-stu-id="6fcbd-124">EXAMPLES</span></span>

### <span data-ttu-id="6fcbd-125">範例1：重新連接到會話</span><span class="sxs-lookup"><span data-stu-id="6fcbd-125">Example 1: Reconnect to a session</span></span>

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

<span data-ttu-id="6fcbd-126">此命令重新連線至 Server01 電腦上的 ITTask 工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-126">This command reconnects to the ITTask session on the Server01 computer.</span></span>

<span data-ttu-id="6fcbd-127">輸出顯示命令成功。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-127">The output shows that the command was successful.</span></span> <span data-ttu-id="6fcbd-128">會話的 **狀態** 是開啟的，而且 **可用性** 可以使用，這表示您可以在會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-128">The **State** of the session is Opened and the **Availability** is Available, which indicates that you can run commands in the session.</span></span>

### <span data-ttu-id="6fcbd-129">範例2：中斷連線和重新連接的效果</span><span class="sxs-lookup"><span data-stu-id="6fcbd-129">Example 2: Effect of disconnecting and reconnecting</span></span>

```
PS C:\> Get-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available


PS C:\> Get-PSSession | Disconnect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Disconnected  Microsoft.PowerShell          None


PS C:\> Get-PSSession | Connect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available
```

<span data-ttu-id="6fcbd-130">此範例顯示中斷連線再重新連線工作階段的作用。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-130">This example shows the effect of disconnecting and then reconnecting to a session.</span></span>

<span data-ttu-id="6fcbd-131">第一個命令會使用 `Get-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-131">The first command uses the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="6fcbd-132">若無 **ComputerName** 參數，命令只會取得目前工作階段中所建立的工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-132">Without the **ComputerName** parameter, the command gets only sessions that were created in the current session.</span></span>

<span data-ttu-id="6fcbd-133">輸出顯示命令取得本機電腦上的 Backups 工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-133">The output shows that the command gets the Backups session on the local computer.</span></span> <span data-ttu-id="6fcbd-134">會話的 **狀態** 會開啟，並提供 **可用性** 。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-134">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="6fcbd-135">第二個命令 `Get-PSSession` 會使用 Cmdlet 來取得在目前會話中建立的 **PSSession** 物件，以及將 `Disconnect-PSSession` 會話中斷連接的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-135">The second command uses the `Get-PSSession` cmdlet to get the **PSSession** objects that were created in the current session and the `Disconnect-PSSession` cmdlet to disconnect the sessions.</span></span> <span data-ttu-id="6fcbd-136">輸出顯示 Backups 工作階段已中斷連線。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-136">The output shows that the Backups session was disconnected.</span></span> <span data-ttu-id="6fcbd-137">會話的 **狀態** 為「已中斷連線」，且 **可用性** 為「無」。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-137">The **State** of the session is Disconnected and the **Availability** is None.</span></span>

<span data-ttu-id="6fcbd-138">第三個命令 `Get-PSSession` 會使用 Cmdlet 來取得在目前會話中建立的 **PSSession** 物件，以及用 `Connect-PSSession` 來重新連接會話的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-138">The third command uses the `Get-PSSession` cmdlet to get the **PSSession** objects that were created in the current session and the `Connect-PSSession` cmdlet to reconnect the sessions.</span></span> <span data-ttu-id="6fcbd-139">輸出顯示 Backups 工作階段已重新連線。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-139">The output shows that the Backups session was reconnected.</span></span> <span data-ttu-id="6fcbd-140">會話的 **狀態** 會開啟，並提供 **可用性** 。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-140">The **State** of the session is Opened and the **Availability** is Available.</span></span>

<span data-ttu-id="6fcbd-141">如果您 `Connect-PSSession` 在未中斷連線的會話上使用此 Cmdlet，此命令不會影響會話，且不會產生任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-141">If you use the `Connect-PSSession` cmdlet on a session that is not disconnected, the command does not affect the session and it does not generate any errors.</span></span>

### <span data-ttu-id="6fcbd-142">範例3：企業案例中的一系列命令</span><span class="sxs-lookup"><span data-stu-id="6fcbd-142">Example 3: Series of commands in an enterprise scenario</span></span>

<span data-ttu-id="6fcbd-143">這一系列的命令會示範如何 `Connect-PSSession` 在企業案例中使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-143">This series of commands shows how the `Connect-PSSession` cmdlet might be used in an enterprise scenario.</span></span> <span data-ttu-id="6fcbd-144">在此案例中，系統管理員在遠端電腦工作階段中啟動長時間執行的工作。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-144">In this case, a system administrator starts a long-running job in a session on a remote computer.</span></span> <span data-ttu-id="6fcbd-145">啟動工作之後，系統管理員從工作階段中斷連線，之後就回家了。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-145">After starting the job, the administrator disconnects from the session and goes home.</span></span>
<span data-ttu-id="6fcbd-146">稍後，系統管理員登入家用電腦，並確認工作已完成，直到完成為止。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-146">Later that evening, the administrator logs on to her home computer and verifies that the job ran until it is completed.</span></span>

<span data-ttu-id="6fcbd-147">系統管理員一開始先在遠端電腦上建立會話，並在會話中執行腳本。第一個命令會使用 `New-PSSession` Cmdlet，在 Server01 遠端電腦上建立 ITTask 會話。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-147">The administrator starts by creating a sessions on a remote computer and running a script in the session.The first command uses the `New-PSSession` cmdlet to create the ITTask session on the Server01 remote computer.</span></span> <span data-ttu-id="6fcbd-148">命令使用 **ConfigurationName** 參數指定 ITTasks 工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-148">The command uses the **ConfigurationName** parameter to specify the ITTasks session configuration.</span></span> <span data-ttu-id="6fcbd-149">此命令會將會話儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-149">The command saves the sessions in the `$s` variable.</span></span>

<span data-ttu-id="6fcbd-150">第二個命令 `Invoke-Command` Cmdlet 可在變數中的會話中啟動背景工作 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-150">The second command `Invoke-Command` cmdlet to start a background job in the session in the `$s` variable.</span></span> <span data-ttu-id="6fcbd-151">它使用 **FilePath** 參數，在背景工作中執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-151">It uses the **FilePath** parameter to run the script in the background job.</span></span>

<span data-ttu-id="6fcbd-152">第三個命令會使用 `Disconnect-PSSession` Cmdlet，從變數中的會話中斷連接 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-152">The third command uses the `Disconnect-PSSession` cmdlet to disconnect from the session in the `$s` variable.</span></span> <span data-ttu-id="6fcbd-153">命令使用值為 **Drop** 的 OutputBufferingMode 參數，避免因為傳遞輸出至工作階段而使得指令碼遭封鎖。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-153">The command uses the **OutputBufferingMode** parameter with a value of Drop to prevent the script from being blocked by having to deliver output to the session.</span></span> <span data-ttu-id="6fcbd-154">它會使用 **IdleTimeoutSec** 參數將會話超時時間延長為15個小時。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-154">It uses the **IdleTimeoutSec** parameter to extend the session time-out to 15 hours.</span></span> <span data-ttu-id="6fcbd-155">當命令完成時，系統管理員會將電腦鎖定並上線。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-155">When the command is completed, the administrator locks her computer and goes home for the evening.</span></span>

<span data-ttu-id="6fcbd-156">之後，系統管理員會啟動家用電腦、登入公司網路，然後啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-156">Later that evening, the administrator starts her home computer, logs on to the corporate network, and starts PowerShell.</span></span> <span data-ttu-id="6fcbd-157">第四個命令會使用 `Get-PSSession` Cmdlet 來取得 Server01 電腦上的會話。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-157">The fourth command uses the `Get-PSSession` cmdlet to get the sessions on the Server01 computer.</span></span> <span data-ttu-id="6fcbd-158">此命令會尋找 ITTask 會話。第五個命令會使用 `Connect-PSSession` Cmdlet 連接到 ITTask 會話。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-158">The command finds the ITTask session.The fifth command uses the `Connect-PSSession` cmdlet to connect to the ITTask session.</span></span> <span data-ttu-id="6fcbd-159">命令會將工作階段儲存於 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-159">The command saves the session in the `$s` variable.</span></span>

<span data-ttu-id="6fcbd-160">第六個命令會使用 `Invoke-Command` Cmdlet 在 `Get-Job` 變數的會話中執行命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-160">The sixth command uses the `Invoke-Command` cmdlet to run a `Get-Job` command in the session in the `$s` variable.</span></span> <span data-ttu-id="6fcbd-161">輸出顯示作業已順利完成。第七個命令會使用 `Invoke-Command` Cmdlet，在 `Receive-Job` 會話中的變數的會話中執行命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-161">The output shows that the job finished successfully.The seventh command uses the `Invoke-Command` cmdlet to run a `Receive-Job` command in the session in the `$s` variable in the session.</span></span> <span data-ttu-id="6fcbd-162">命令會將結果儲存在 `$BackupSpecs` 變數中。第八個命令會使用 `Invoke-Command` Cmdlet 在會話中執行另一個腳本。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-162">The command saves the results in the `$BackupSpecs` variable.The eighth command uses the `Invoke-Command` cmdlet to runs another script in the session.</span></span> <span data-ttu-id="6fcbd-163">此命令會使用 `$BackupSpecs` 會話中的變數值做為腳本的輸入。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-163">The command uses the value of the `$BackupSpecs` variable in the session as input to the script.</span></span>

```
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

<span data-ttu-id="6fcbd-164">第九個命令中斷與變數中會話的連線 `$s` 。系統管理員關閉 PowerShell 並關閉電腦。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-164">The ninth command disconnects from the session in the `$s` variable.The administrator closes PowerShell and closes the computer.</span></span> <span data-ttu-id="6fcbd-165">系統管理員隔天可從工作電腦重新連線工作階段，並檢查指令碼狀態。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-165">She can reconnect to the session on the next day and check the script status from her work computer.</span></span>

## <span data-ttu-id="6fcbd-166">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6fcbd-166">PARAMETERS</span></span>

### <span data-ttu-id="6fcbd-167">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="6fcbd-167">-AllowRedirection</span></span>

<span data-ttu-id="6fcbd-168">指出此 Cmdlet 允許將此連接重新導向至替代 URI。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-168">Indicates that this cmdlet allows redirection of this connection to an alternate URI.</span></span>

<span data-ttu-id="6fcbd-169">使用 **ConnectionURI** 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-169">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="6fcbd-170">根據預設，PowerShell 不會重新導向連線，但是您可以使用此參數允許它重新導向連接。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-170">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="6fcbd-171">您也可以變更 **MaximumConnectionRedirectionCount** 工作階段選項值，限制連線重新導向的次數。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-171">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="6fcbd-172">使用 Cmdlet 的 **MaximumRedirection** 參數， `New-PSSessionOption` 或設定 **$PSSessionOption** 喜好設定變數的 **MaximumConnectionRedirectionCount** 屬性。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-172">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the **$PSSessionOption** preference variable.</span></span> <span data-ttu-id="6fcbd-173">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-173">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-174">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="6fcbd-174">-ApplicationName</span></span>

<span data-ttu-id="6fcbd-175">指定應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-175">Specifies the name of an application.</span></span> <span data-ttu-id="6fcbd-176">此 Cmdlet 只會連接到使用指定應用程式的會話。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-176">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="6fcbd-177">輸入連線 URI 的應用程式名稱區段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-177">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="6fcbd-178">例如，在下列連接 URI 中，應用程式名稱為 WSMan： `http://localhost:5985/WSMAN` 。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-178">For example, in the following connection URI, the application name is WSMan: `http://localhost:5985/WSMAN`.</span></span> <span data-ttu-id="6fcbd-179">工作階段的應用程式名稱儲存在工作階段的 **Runspace.ConnectionInfo.AppName** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-179">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="6fcbd-180">此參數的值可用來選取與篩選工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-180">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="6fcbd-181">它不會變更工作階段使用的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-181">It does not change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-182">-Authentication</span><span class="sxs-lookup"><span data-stu-id="6fcbd-182">-Authentication</span></span>

<span data-ttu-id="6fcbd-183">指定在命令中用來驗證使用者認證的機制，以重新連線到中斷連線的會話。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-183">Specifies the mechanism that is used to authenticate user credentials in the command to reconnect to the disconnected session.</span></span> <span data-ttu-id="6fcbd-184">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="6fcbd-184">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6fcbd-185">預設</span><span class="sxs-lookup"><span data-stu-id="6fcbd-185">Default</span></span>
- <span data-ttu-id="6fcbd-186">基本</span><span class="sxs-lookup"><span data-stu-id="6fcbd-186">Basic</span></span>
- <span data-ttu-id="6fcbd-187">Credssp</span><span class="sxs-lookup"><span data-stu-id="6fcbd-187">Credssp</span></span>
- <span data-ttu-id="6fcbd-188">Digest</span><span class="sxs-lookup"><span data-stu-id="6fcbd-188">Digest</span></span>
- <span data-ttu-id="6fcbd-189">Kerberos</span><span class="sxs-lookup"><span data-stu-id="6fcbd-189">Kerberos</span></span>
- <span data-ttu-id="6fcbd-190">交涉</span><span class="sxs-lookup"><span data-stu-id="6fcbd-190">Negotiate</span></span>
- <span data-ttu-id="6fcbd-191">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="6fcbd-191">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="6fcbd-192">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-192">The default value is Default.</span></span>

<span data-ttu-id="6fcbd-193">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-193">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="6fcbd-194">使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-194">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="6fcbd-195">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-195">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="6fcbd-196">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-196">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-197">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="6fcbd-197">-CertificateThumbprint</span></span>

<span data-ttu-id="6fcbd-198">指定具有連線至已中斷連線工作階段權限之使用者帳戶的數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-198">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="6fcbd-199">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-199">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="6fcbd-200">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-200">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="6fcbd-201">這些帳戶只能對應至本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-201">They can be mapped only to local user accounts.</span></span> <span data-ttu-id="6fcbd-202">它們無法使用網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-202">They do not work with domain accounts.</span></span>

<span data-ttu-id="6fcbd-203">若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell Cert：磁片磁碟機中的或命令。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-203">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-204">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="6fcbd-204">-ComputerName</span></span>

<span data-ttu-id="6fcbd-205">指定儲存中斷連線工作階段的電腦。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-205">Specifies the computers on which the disconnected sessions are stored.</span></span> <span data-ttu-id="6fcbd-206">會話會儲存在位於伺服器端或接收端連接端點的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-206">Sessions are stored on the computer that is at the server-side or receiving end of a connection.</span></span> <span data-ttu-id="6fcbd-207">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-207">The default is the local computer.</span></span>

<span data-ttu-id="6fcbd-208">輸入電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-208">Type the NetBIOS name, an IP address, or a fully qualified domain name of one computer.</span></span> <span data-ttu-id="6fcbd-209">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-209">Wildcard characters are not permitted.</span></span> <span data-ttu-id="6fcbd-210">若要指定本機電腦，請輸入電腦名稱稱、localhost 或點 (。 ) </span><span class="sxs-lookup"><span data-stu-id="6fcbd-210">To specify the local computer, type the computer name, localhost, or a dot (.)</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameGuid, ComputerName
Aliases: Cn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-211">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="6fcbd-211">-ConfigurationName</span></span>

<span data-ttu-id="6fcbd-212">只連線使用指定工作階段設定的工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-212">Connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="6fcbd-213">輸入工作階段設定的設定名稱或完整資源 URI。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-213">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="6fcbd-214">如果您只指定設定名稱，則會在前面加上下列架構 URI： `http://schemas.microsoft.com/powershell` 。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-214">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span> <span data-ttu-id="6fcbd-215">工作階段的設定名稱儲存在工作階段的 **ConfigurationName** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-215">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="6fcbd-216">此參數的值可用來選取與篩選工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-216">The value of this parameter is used to select and filter sessions.</span></span> <span data-ttu-id="6fcbd-217">它不會變更工作階段使用的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-217">It does not change the session configuration that the session uses.</span></span>

<span data-ttu-id="6fcbd-218">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-218">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-219">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="6fcbd-219">-ConnectionUri</span></span>

<span data-ttu-id="6fcbd-220">針對已中斷連線的會話，指定連接端點的 Uri。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-220">Specifies the URIs of the connection endpoints for the disconnected sessions.</span></span>

<span data-ttu-id="6fcbd-221">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-221">The URI must be fully qualified.</span></span> <span data-ttu-id="6fcbd-222">這個字串的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="6fcbd-222">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="6fcbd-223">預設值如下：</span><span class="sxs-lookup"><span data-stu-id="6fcbd-223">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="6fcbd-224">如果您沒有指定連接 URI，您可以使用 **UseSSL** 和 **Port** 參數來指定連接 uri 值。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-224">If you do not specify a connection URI, you can use the **UseSSL** and **Port** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="6fcbd-225">URI 的 **Transport** 區段有效值為 HTTP 與 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-225">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="6fcbd-226">若指定含傳輸區段的連線 URI，但未指定連接埠，將會以標準連接埠 80 (適用於 HTTP) 和 443 (適用於 HTTPS) 建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-226">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="6fcbd-227">若要使用 PowerShell 遠端的預設埠，請指定 HTTP 的埠5985或 HTTPS 的5986。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-227">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="6fcbd-228">如果目的地電腦將連線重新導向至不同的 URI，除非您在命令中使用 **AllowRedirection** 參數，否則 PowerShell 會禁止重新導向。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-228">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-229">-Credential</span><span class="sxs-lookup"><span data-stu-id="6fcbd-229">-Credential</span></span>

<span data-ttu-id="6fcbd-230">指定具有連線至已中斷連線工作階段權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-230">Specifies a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="6fcbd-231">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-231">The default is the current user.</span></span>

<span data-ttu-id="6fcbd-232">輸入使用者名稱，例如 `User01` 或 `Domain01\User01` ，或輸入 `PSCredential` Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-232">Type a user name, such as `User01` or `Domain01\User01`, or enter a `PSCredential` object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="6fcbd-233">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-233">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="6fcbd-234">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-234">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="6fcbd-235">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-235">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-236">-Id</span><span class="sxs-lookup"><span data-stu-id="6fcbd-236">-Id</span></span>

<span data-ttu-id="6fcbd-237">指定已中斷連線工作階段的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-237">Specifies the IDs of the disconnected sessions.</span></span> <span data-ttu-id="6fcbd-238">只有當已中斷連線的會話先前連接到目前的會話時， **識別碼** 參數才有效。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-238">The **Id** parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="6fcbd-239">當工作階段儲存在本機電腦，但是未連線目前工作階段，則此參數有效，但沒有作用。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-239">This parameter is valid, but not effective, when the session is stored on the local computer, but was not connected to the current session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-240">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="6fcbd-240">-InstanceId</span></span>

<span data-ttu-id="6fcbd-241">指定已中斷連線工作階段的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-241">Specifies the instance IDs of the disconnected sessions.</span></span>

<span data-ttu-id="6fcbd-242">實例識別碼是 GUID，可唯一識別本機或遠端電腦上的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-242">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span>

<span data-ttu-id="6fcbd-243">實例識別碼儲存在 **PSSession** 的 **InstanceID** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-243">The instance ID is stored in the **InstanceID** property of the **PSSession**.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: ComputerNameGuid, ConnectionUriGuid, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-244">-Name</span><span class="sxs-lookup"><span data-stu-id="6fcbd-244">-Name</span></span>

<span data-ttu-id="6fcbd-245">指定已中斷連線工作階段的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-245">Specifies the friendly names of the disconnected sessions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri
Aliases:

Required: True (Name), False (ComputerName, ConnectionUri)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-246">-Port</span><span class="sxs-lookup"><span data-stu-id="6fcbd-246">-Port</span></span>

<span data-ttu-id="6fcbd-247">指定遠端電腦上用來重新連線至工作階段的網路連接埠。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-247">Specifies the network port on the remote computer that is used to reconnect to the session.</span></span> <span data-ttu-id="6fcbd-248">若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-248">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="6fcbd-249">預設的埠是5985，也就是 HTTP 的 WinRM 埠和5986，也就是 HTTPS 的 WinRM 埠。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-249">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="6fcbd-250">使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-250">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="6fcbd-251">若要設定接聽程式，請在 PowerShell 提示字元中輸入下列兩個命令：</span><span class="sxs-lookup"><span data-stu-id="6fcbd-251">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="6fcbd-252">除非必要，否則請勿使用 **Port** 參數。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-252">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="6fcbd-253">在命令中設定的連接埠，將套用於執行命令所在的所有電腦或工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-253">The port that is set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="6fcbd-254">替代的連接埠設定可能使得命令無法在全部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-254">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-255">-Session</span><span class="sxs-lookup"><span data-stu-id="6fcbd-255">-Session</span></span>

<span data-ttu-id="6fcbd-256">指定已中斷連線的工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-256">Specifies the disconnected sessions.</span></span> <span data-ttu-id="6fcbd-257">輸入包含 **pssession** 物件的變數，或輸入可建立或取得 **pssession** 物件的命令，例如 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-257">Enter a variable that contains the **PSSession** objects or a command that creates or gets the **PSSession** objects, such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-258">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="6fcbd-258">-SessionOption</span></span>

<span data-ttu-id="6fcbd-259">指定會話的 advanced 選項。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-259">Specifies advanced options for the session.</span></span> <span data-ttu-id="6fcbd-260">輸入 **SessionOption** 物件（例如您使用 Cmdlet 建立的物件 `New-PSSessionOption` ），或輸入雜湊表，其中索引鍵為會話選項名稱，而值為會話選項值。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-260">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="6fcbd-261">選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-261">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="6fcbd-262">否則，將以工作階段設定中設定的選項建立預設值。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-262">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="6fcbd-263">會話選項值的優先順序高於 `$PSSessionOption` 喜好設定變數和會話設定中設定之會話的預設值。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-263">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="6fcbd-264">不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-264">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="6fcbd-265">如需包含預設值之會話選項的描述，請參閱 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-265">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="6fcbd-266">如需 **$PSSessionOption** 喜好設定變數的詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-266">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="6fcbd-267">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-267">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-268">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="6fcbd-268">-ThrottleLimit</span></span>

<span data-ttu-id="6fcbd-269">指定為執行此命令可建立的最大同時連線數。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-269">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="6fcbd-270">若省略此參數，或輸入值為 0，則會使用預設值 32。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-270">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="6fcbd-271">節流限制僅適用於目前命令，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-271">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-272">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="6fcbd-272">-UseSSL</span></span>

<span data-ttu-id="6fcbd-273">指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來連線到中斷連線的會話。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-273">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="6fcbd-274">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-274">By default, SSL is not used.</span></span>

<span data-ttu-id="6fcbd-275">WS-Management 加密透過網路傳輸的所有 PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-275">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="6fcbd-276">**UseSSL** 參數是額外的保護，可跨 HTTPS 連接（而非 HTTP 連線）傳送資料。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-276">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="6fcbd-277">如果您使用此參數，但是命令所用的埠上無法使用 SSL，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-277">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fcbd-278">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6fcbd-278">-Confirm</span></span>

<span data-ttu-id="6fcbd-279">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-279">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6fcbd-280">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6fcbd-280">-WhatIf</span></span>

<span data-ttu-id="6fcbd-281">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-281">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6fcbd-282">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-282">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6fcbd-283">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6fcbd-283">CommonParameters</span></span>

<span data-ttu-id="6fcbd-284">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-284">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6fcbd-285">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-285">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6fcbd-286">輸入</span><span class="sxs-lookup"><span data-stu-id="6fcbd-286">INPUTS</span></span>

### <span data-ttu-id="6fcbd-287">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="6fcbd-287">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="6fcbd-288">您可以使用管線將會話 ( **PSSession** ) 傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-288">You can pipe a session ( **PSSession** ) to this cmdlet.</span></span>

## <span data-ttu-id="6fcbd-289">輸出</span><span class="sxs-lookup"><span data-stu-id="6fcbd-289">OUTPUTS</span></span>

### <span data-ttu-id="6fcbd-290">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="6fcbd-290">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="6fcbd-291">此 Cmdlet 會傳回物件，代表它重新連接的會話。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-291">This cmdlet returns an object that represents the session to which it reconnected.</span></span>

## <span data-ttu-id="6fcbd-292">注意</span><span class="sxs-lookup"><span data-stu-id="6fcbd-292">NOTES</span></span>

- <span data-ttu-id="6fcbd-293">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-293">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="6fcbd-294">`Connect-PSSession` 只重新連接到已中斷連線的會話，也就是具有 [ **狀態** ] 屬性值為 [已中斷連線] 的會話。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-294">`Connect-PSSession` reconnects only to sessions that are disconnected, that is, sessions that have a value of Disconnected for the **State** property.</span></span> <span data-ttu-id="6fcbd-295">只有連接到或結束的會話，才能中斷執行 Windows PowerShell 3.0 或更新版本的電腦。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-295">Only sessions that are connected to, or end at, computers that run Windows PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>

- <span data-ttu-id="6fcbd-296">如果您 `Connect-PSSession` 在未中斷連線的會話上使用，此命令不會影響會話，且不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-296">If you use `Connect-PSSession` on a session that is not disconnected, the command does not affect the session and it does not generate errors.</span></span>

- <span data-ttu-id="6fcbd-297">使用 **EnableNetworkAccess** 參數所建立之互動式權杖的已中斷連線回送會話，只能從建立該會話的電腦重新連接。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-297">Disconnected loopback sessions with interactive tokens, which are created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="6fcbd-298">此限制可防止電腦遭受惡意存取。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-298">This restriction protects the computer from malicious access.</span></span>

- <span data-ttu-id="6fcbd-299">**PSSession** 的 **State** 屬性值是相對於目前的會話。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-299">The value of the **State** property of a **PSSession** is relative to the current session.</span></span>
  <span data-ttu-id="6fcbd-300">因此，[已 **中斷** 連線] 值表示 **PSSession** 未連接到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-300">Therefore, a value of **Disconnected** means that the **PSSession** is not connected to the current session.</span></span> <span data-ttu-id="6fcbd-301">但是，它並不表示 **PSSession** 與所有會話中斷連接。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-301">However, it does not mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="6fcbd-302">它可能連線不同的工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-302">It might be connected to a different session.</span></span> <span data-ttu-id="6fcbd-303">若要判斷是否可以連線或重新連線工作階段，請使用 **Availability** 屬性。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-303">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="6fcbd-304">**Availability** 值為 None 表示您可以連線工作階段。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-304">An **Availability** value of None indicates that you can connect to the session.</span></span> <span data-ttu-id="6fcbd-305">「忙碌」值表示您無法連接到 **PSSession** ，因為它已連接到另一個會話。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-305">A value of Busy indicates that you cannot connect to the **PSSession** because it is connected to another session.</span></span>

  <span data-ttu-id="6fcbd-306">如需會話的 **State** 屬性值的詳細資訊，請參閱 [ runspacestate 列舉](/dotnet/api/system.management.automation.runspaces.runspacestate)。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-306">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

  <span data-ttu-id="6fcbd-307">如需會話的 **Availability** 屬性值的詳細資訊，請參閱 [RunspaceAvailability 列舉](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-307">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

- <span data-ttu-id="6fcbd-308">當您連接到 **pssession** 時，無法變更 **PSSession** 的空閒超時值。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-308">You cannot change the idle time-out value of a **PSSession** when you connect to the **PSSession**.</span></span> <span data-ttu-id="6fcbd-309">的 **SessionOption** 參數 `Connect-PSSession` 會採用具有 **IdleTimeout** 值的 **SessionOption** 物件。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-309">The **SessionOption** parameter of `Connect-PSSession` takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="6fcbd-310">不過， **IdleTimeout** **SessionOption** **IdleTimeout** `$PSSessionOption` 連接至 **PSSession** 時，會忽略 SessionOption 物件的 idletimeout 值和變數的 idletimeout 值。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-310">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the `$PSSessionOption` variable are ignored when connecting to a **PSSession**.</span></span>

  <span data-ttu-id="6fcbd-311">當您建立 **pssession** 時，可以使用 **PSSession** `New-PSSession` 或 `Invoke-Command` Cmdlet，以及從 **pssession** 中斷連接時，設定和變更 pssession 的閒置時間。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-311">You can set and change the idle time-out of a **PSSession** when you create the **PSSession** , by using the `New-PSSession` or `Invoke-Command` cmdlets, and when you disconnect from the **PSSession**.</span></span>

  <span data-ttu-id="6fcbd-312">**PSSession** 的 **IdleTimeout** 屬性對中斷連線的會話而言是不可或缺的，因為它會決定中斷連線的會話在遠端電腦上的維護時間。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-312">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions, because it determines how long a disconnected session is maintained on the remote computer.</span></span> <span data-ttu-id="6fcbd-313">已中斷連線的工作階段一被中斷連線，便被視為閒置，即使命令仍然在已中斷連線的工作階段中執行也是如此。</span><span class="sxs-lookup"><span data-stu-id="6fcbd-313">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

## <span data-ttu-id="6fcbd-314">相關連結</span><span class="sxs-lookup"><span data-stu-id="6fcbd-314">RELATED LINKS</span></span>

[<span data-ttu-id="6fcbd-315">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="6fcbd-315">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="6fcbd-316">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="6fcbd-316">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="6fcbd-317">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="6fcbd-317">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="6fcbd-318">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="6fcbd-318">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="6fcbd-319">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fcbd-319">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="6fcbd-320">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="6fcbd-320">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="6fcbd-321">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="6fcbd-321">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="6fcbd-322">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="6fcbd-322">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="6fcbd-323">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="6fcbd-323">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="6fcbd-324">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6fcbd-324">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="6fcbd-325">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="6fcbd-325">Remove-PSSession</span></span>](Remove-PSSession.md)
