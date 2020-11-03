---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/11/2019
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-PSSession
ms.openlocfilehash: 39501e0992ba10ae3638dd5178f2913001b5cd32
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205392"
---
# <span data-ttu-id="564c1-103">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="564c1-103">Receive-PSSession</span></span>

## <span data-ttu-id="564c1-104">概要</span><span class="sxs-lookup"><span data-stu-id="564c1-104">SYNOPSIS</span></span>

<span data-ttu-id="564c1-105">針對已中斷連線的工作階段取得其命令結果</span><span class="sxs-lookup"><span data-stu-id="564c1-105">Gets results of commands in disconnected sessions</span></span>

## <span data-ttu-id="564c1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="564c1-106">SYNTAX</span></span>

### <span data-ttu-id="564c1-107">工作階段 (預設)</span><span class="sxs-lookup"><span data-stu-id="564c1-107">Session (Default)</span></span>

```
Receive-PSSession [-Session] <PSSession> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="564c1-108">Id</span><span class="sxs-lookup"><span data-stu-id="564c1-108">Id</span></span>

```
Receive-PSSession [-Id] <Int32> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="564c1-109">ComputerSessionName</span><span class="sxs-lookup"><span data-stu-id="564c1-109">ComputerSessionName</span></span>

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="564c1-110">ComputerInstanceId</span><span class="sxs-lookup"><span data-stu-id="564c1-110">ComputerInstanceId</span></span>

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="564c1-111">ConnectionUriSessionName</span><span class="sxs-lookup"><span data-stu-id="564c1-111">ConnectionUriSessionName</span></span>

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="564c1-112">ConnectionUriInstanceId</span><span class="sxs-lookup"><span data-stu-id="564c1-112">ConnectionUriInstanceId</span></span>

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="564c1-113">InstanceId</span><span class="sxs-lookup"><span data-stu-id="564c1-113">InstanceId</span></span>

```
Receive-PSSession [-InstanceId] <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="564c1-114">會話</span><span class="sxs-lookup"><span data-stu-id="564c1-114">SessionName</span></span>

```
Receive-PSSession [-Name] <String> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="564c1-115">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="564c1-115">DESCRIPTION</span></span>

<span data-ttu-id="564c1-116">`Receive-PSSession`Cmdlet 會取得已中斷連線 ( **PSSession** ) 的 PowerShell 會話中執行命令的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-116">The `Receive-PSSession` cmdlet gets the results of commands running in PowerShell sessions ( **PSSession** ) that were disconnected.</span></span> <span data-ttu-id="564c1-117">如果會話目前已連線，則 `Receive-PSSession` 會取得會話中斷連接時正在執行的命令結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-117">If the session is currently connected, `Receive-PSSession` gets the results of commands that were running when the session was disconnected.</span></span> <span data-ttu-id="564c1-118">如果會話仍處於中斷線上狀態，則會 `Receive-PSSession` 連接到會話、繼續所有已暫停的命令，並取得會話中執行之命令的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-118">If the session is still disconnected, `Receive-PSSession` connects to the session, resumes any commands that were suspended, and gets the results of commands running in the session.</span></span>

<span data-ttu-id="564c1-119">此 Cmdlet 是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="564c1-119">This cmdlet was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="564c1-120">除了命令之外，您還可以使用 `Receive-PSSession` `Connect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-120">You can use a `Receive-PSSession` in addition to or instead of a `Connect-PSSession` command.</span></span>
<span data-ttu-id="564c1-121">`Receive-PSSession` 可以連接到在其他會話或其他電腦上啟動的任何已中斷連線或重新連線的會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-121">`Receive-PSSession` can connect to any disconnected or reconnected session that was started in other sessions or on other computers.</span></span>

<span data-ttu-id="564c1-122">`Receive-PSSession`適用于 **PSSessions** 使用 `Disconnect-PSSession` Cmdlet 或 `Invoke-Command` **InDisconnectedSession** 參數刻意中斷連線的 pssession。</span><span class="sxs-lookup"><span data-stu-id="564c1-122">`Receive-PSSession` works on **PSSessions** that were disconnected intentionally using the `Disconnect-PSSession` cmdlet or the `Invoke-Command` **InDisconnectedSession** parameter.</span></span> <span data-ttu-id="564c1-123">或意外中斷連線，因為網路中斷。</span><span class="sxs-lookup"><span data-stu-id="564c1-123">Or disconnected unintentionally by a network interruption.</span></span>

<span data-ttu-id="564c1-124">如果您使用此 `Receive-PSSession` Cmdlet 來連線到沒有任何命令正在執行或已暫止的會話，則會 `Receive-PSSession` 連接到會話，但不會傳回任何輸出或錯誤。</span><span class="sxs-lookup"><span data-stu-id="564c1-124">If you use the `Receive-PSSession` cmdlet to connect to a session in which no commands are running or suspended, `Receive-PSSession` connects to the session, but returns no output or errors.</span></span>

<span data-ttu-id="564c1-125">如需中斷連線工作階段功能的詳細資訊，請參閱 [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="564c1-125">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="564c1-126">某些範例會使用展開來減少行長度，並提高可讀性。</span><span class="sxs-lookup"><span data-stu-id="564c1-126">Some examples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="564c1-127">如需詳細資訊，請參閱 [about_Splatting](./About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="564c1-127">For more information, see [about_Splatting](./About/about_Splatting.md).</span></span>

## <span data-ttu-id="564c1-128">範例</span><span class="sxs-lookup"><span data-stu-id="564c1-128">EXAMPLES</span></span>

### <span data-ttu-id="564c1-129">範例1：連接到 PSSession</span><span class="sxs-lookup"><span data-stu-id="564c1-129">Example 1: Connect to a PSSession</span></span>

<span data-ttu-id="564c1-130">此範例會連線到遠端電腦上的會話，並取得會話中執行之命令的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-130">This example connects to a session on a remote computer and gets the results of commands that are running in a session.</span></span>

```powershell
Receive-PSSession -ComputerName Server01 -Name ITTask
```

<span data-ttu-id="564c1-131">`Receive-PSSession`使用 **ComputerName** 參數指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="564c1-131">The `Receive-PSSession` specifies the remote computer with the **ComputerName** parameter.</span></span> <span data-ttu-id="564c1-132">**Name** 參數會識別 Server01 電腦上的 ITTask 會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-132">The **Name** parameter identifies the ITTask session on the Server01 computer.</span></span> <span data-ttu-id="564c1-133">此範例會取得在 ITTask 會話中執行之命令的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-133">The example gets the results of commands that were running in the ITTask session.</span></span>

<span data-ttu-id="564c1-134">因為命令不使用 **OutTarget** 參數，所以結果會出現在命令列上。</span><span class="sxs-lookup"><span data-stu-id="564c1-134">Because the command doesn't use the **OutTarget** parameter, the results appear on the command line.</span></span>

### <span data-ttu-id="564c1-135">範例2：取得已中斷連線會話上所有命令的結果</span><span class="sxs-lookup"><span data-stu-id="564c1-135">Example 2: Get results of all commands on disconnected sessions</span></span>

<span data-ttu-id="564c1-136">此範例會取得在兩部遠端電腦上所有已中斷連線的會話中執行之所有命令的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-136">This example gets the results of all commands running in all disconnected sessions on two remote computers.</span></span>

<span data-ttu-id="564c1-137">如果有任何會話未中斷連線或未執行命令，則 `Receive-PSSession` 不會連接到會話，也不會傳回任何輸出或錯誤。</span><span class="sxs-lookup"><span data-stu-id="564c1-137">If any session wasn't disconnected or isn't running commands, `Receive-PSSession` doesn't connect to the session and doesn't return any output or errors.</span></span>

```powershell
Get-PSSession -ComputerName Server01, Server02 | Receive-PSSession
```

<span data-ttu-id="564c1-138">`Get-PSSession` 使用 **ComputerName** 參數來指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="564c1-138">`Get-PSSession` uses the **ComputerName** parameter to specify the remote computers.</span></span> <span data-ttu-id="564c1-139">物件會向下傳送到管線 `Receive-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-139">The objects are sent down the pipeline to `Receive-PSSession`.</span></span>

### <span data-ttu-id="564c1-140">範例3：取得會話中執行之腳本的結果</span><span class="sxs-lookup"><span data-stu-id="564c1-140">Example 3: Get the results of a script running in a session</span></span>

<span data-ttu-id="564c1-141">此範例會使用 `Receive-PSSession` Cmdlet 來取得在遠端電腦的會話中執行之腳本的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-141">This example uses the `Receive-PSSession` cmdlet to get the results of a script that was running in a remote computer's session.</span></span>

```powershell
$parms = @{
  ComputerName = "Server01"
  Name = "ITTask"
  OutTarget = "Job"
  JobName = "ITTaskJob01"
  Credential = "Domain01\Admin01"
}
Receive-PSSession @parms
```

```Output
Id     Name            State         HasMoreData     Location
--     ----            -----         -----------     --------
16     ITTaskJob01     Running       True            Server01
```

<span data-ttu-id="564c1-142">命令使用 **ComputerName** 與 **Name** 參數，識別已中斷連線的工作階段。</span><span class="sxs-lookup"><span data-stu-id="564c1-142">The command uses the **ComputerName** and **Name** parameters to identify the disconnected session.</span></span>
<span data-ttu-id="564c1-143">它會使用 **OutTarget** 參數搭配作業的值，以指示 `Receive-PSSession` 將結果作為作業傳回。</span><span class="sxs-lookup"><span data-stu-id="564c1-143">It uses the **OutTarget** parameter with a value of Job to direct `Receive-PSSession` to return the results as a job.</span></span> <span data-ttu-id="564c1-144">**JobName** 參數會在重新連接的會話中指定作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="564c1-144">The **JobName** parameter specifies a name for the job in the reconnected session.</span></span>
<span data-ttu-id="564c1-145">**Credential** 參數會 `Receive-PSSession` 使用網域系統管理員的許可權來執行命令。</span><span class="sxs-lookup"><span data-stu-id="564c1-145">The **Credential** parameter runs the `Receive-PSSession` command using the permissions of a domain administrator.</span></span>

<span data-ttu-id="564c1-146">輸出會顯示 `Receive-PSSession` 在目前的會話中，以作業形式傳回結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-146">The output shows that `Receive-PSSession` returned the results as a job in the current session.</span></span> <span data-ttu-id="564c1-147">若要取得工作結果，請使用 `Receive-Job` 命令</span><span class="sxs-lookup"><span data-stu-id="564c1-147">To get the job results, use a `Receive-Job` command</span></span>

### <span data-ttu-id="564c1-148">範例4：在網路中斷之後取得結果</span><span class="sxs-lookup"><span data-stu-id="564c1-148">Example 4: Get results after a network outage</span></span>

<span data-ttu-id="564c1-149">此範例會在 `Receive-PSSession` 網路中斷中斷會話連線之後，使用 Cmdlet 來取得工作的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-149">This example uses the `Receive-PSSession` cmdlet to get the results of a job after a network outage disrupts a session connection.</span></span> <span data-ttu-id="564c1-150">PowerShell 會在接下來的四分鐘內，每秒自動嘗試重新連線會話一次，而且只有在四分鐘間隔中的所有嘗試都失敗時，才會放棄投入時間。</span><span class="sxs-lookup"><span data-stu-id="564c1-150">PowerShell automatically attempts to reconnect the session once per second for the next four minutes and abandons the effort only if all attempts in the four-minute interval fail.</span></span>

```
PS> $s = New-PSSession -ComputerName Server01 -Name AD -ConfigurationName ADEndpoint
PS> $s

Id  Name   ComputerName    State        ConfigurationName     Availability
--  ----   ------------    -----        -----------------     ------------
8   AD      Server01       Opened       ADEndpoint               Available


PS> Invoke-Command -Session $s -FilePath \\Server12\Scripts\SharedScripts\New-ADResolve.ps1

Running "New-ADResolve.ps1"

# Network outage
# Restart local computer
# Network access is not re-established within 4 minutes


PS> Get-PSSession -ComputerName Server01

Id  Name   ComputerName    State          ConfigurationName      Availability
--  ----   ------------    -----          -----------------      ------------
1  Backup  Server01        Disconnected   Microsoft.PowerShell           None
8  AD      Server01        Disconnected   ADEndpoint                     None


PS> Receive-PSSession -ComputerName Server01 -Name AD -OutTarget Job -JobName AD

Job Id   Name      State         HasMoreData     Location
--       ----      -----         -----------     --------
16       ADJob     Running       True            Server01


PS> Get-PSSession -ComputerName Server01

Id  Name    ComputerName    State         ConfigurationName     Availability
--  ----    ------------    -----         -----------------     ------------
1  Backup   Server01        Disconnected  Microsoft.PowerShell          Busy
8  AD       Server01        Opened        ADEndpoint               Available
```

<span data-ttu-id="564c1-151">此 `New-PSSession` Cmdlet 會在 Server01 電腦上建立會話，並將會話儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="564c1-151">The `New-PSSession` cmdlet creates a session on the Server01 computer and saves the session in the `$s` variable.</span></span> <span data-ttu-id="564c1-152">此 `$s` 變數會顯示狀態為開啟 **狀態** ，且 **可用性** 可以使用。</span><span class="sxs-lookup"><span data-stu-id="564c1-152">The `$s` variable displays that the **State** is Opened and the **Availability** is Available.</span></span> <span data-ttu-id="564c1-153">這些值表示您已連接到會話，而且可以在會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="564c1-153">These values indicate that you're connected to the session and can run commands in the session.</span></span>

<span data-ttu-id="564c1-154">此 `Invoke-Command` Cmdlet 會在變數中的會話中執行腳本 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-154">The `Invoke-Command` cmdlet runs a script in the session in the `$s` variable.</span></span> <span data-ttu-id="564c1-155">指令碼開始執行並傳回資料，但是網路中斷而中斷了工作階段。</span><span class="sxs-lookup"><span data-stu-id="564c1-155">The script begins to run and return data, but a network outage occurs that interrupts the session.</span></span> <span data-ttu-id="564c1-156">使用者必須結束工作階段並重新啟動本機電腦。</span><span class="sxs-lookup"><span data-stu-id="564c1-156">The user has to exit the session and restart the local computer.</span></span>

<span data-ttu-id="564c1-157">當電腦重新開機時，使用者會啟動 PowerShell 並執行 `Get-PSSession` 命令，以取得 Server01 電腦上的會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-157">When the computer restarts, the user starts PowerShell and runs a `Get-PSSession` command to get sessions on the Server01 computer.</span></span> <span data-ttu-id="564c1-158">輸出顯示 Server01 電腦上仍有 **AD** 會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-158">The output shows that the **AD** session still exists on the Server01 computer.</span></span> <span data-ttu-id="564c1-159">此 **狀態** 表示 **AD** 會話已中斷連線。</span><span class="sxs-lookup"><span data-stu-id="564c1-159">The **State** indicates that the **AD** session is disconnected.</span></span> <span data-ttu-id="564c1-160">[無] 的 [ **可用性** ] 值表示會話未連接到任何用戶端會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-160">The **Availability** value of None, indicates that the session isn't connected to any client sessions.</span></span>

<span data-ttu-id="564c1-161">此 `Receive-PSSession` Cmdlet 會重新連接至 **AD** 會話，並取得會話中執行之腳本的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-161">The `Receive-PSSession` cmdlet reconnects to the **AD** session and gets the results of the script that ran in the session.</span></span> <span data-ttu-id="564c1-162">此命令會使用 **OutTarget** 參數，在名為 **adjob 之** 的作業中要求結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-162">The command uses the **OutTarget** parameter to request the results in a job named **ADJob** .</span></span> <span data-ttu-id="564c1-163">此命令會傳回工作物件，且輸出會指出腳本仍在執行中。</span><span class="sxs-lookup"><span data-stu-id="564c1-163">The command returns a job object and the output indicates that the script is still running.</span></span>

<span data-ttu-id="564c1-164">`Get-PSSession`Cmdlet 可用來檢查工作狀態。</span><span class="sxs-lookup"><span data-stu-id="564c1-164">The `Get-PSSession` cmdlet is used to check the job state.</span></span> <span data-ttu-id="564c1-165">輸出會確認 Cmdlet 重新連線 `Receive-PSSession` 至 **AD** 會話，該會話現在已開啟且可供命令使用。</span><span class="sxs-lookup"><span data-stu-id="564c1-165">The output confirms that the `Receive-PSSession` cmdlet reconnected to the **AD** session, which is now open and available for commands.</span></span> <span data-ttu-id="564c1-166">而且，腳本會繼續執行，並取得腳本結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-166">And, the script resumed execution and is getting the script results.</span></span>

### <span data-ttu-id="564c1-167">範例5：重新連線至已中斷連線的會話</span><span class="sxs-lookup"><span data-stu-id="564c1-167">Example 5: Reconnect to disconnected sessions</span></span>

<span data-ttu-id="564c1-168">此範例會使用指令 `Receive-PSSession` 程式來重新連線到刻意中斷連線的會話，並取得會話中執行之工作的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-168">This example uses the `Receive-PSSession` cmdlet to reconnect to sessions that were intentionally disconnected and get the results of jobs that were running in the sessions.</span></span>

```
PS> $parms = @{
      InDisconnectedSession = $True
      ComputerName = "Server01", "Server02", "Server30"
      FilePath = "\\Server12\Scripts\SharedScripts\Get-BugStatus.ps1"
      Name = "BugStatus"
      SessionOption = @{IdleTimeout = 86400000}
      ConfigurationName = "ITTasks"
    }
PS> Invoke-Command @parms
PS> Exit


PS> $s = Get-PSSession -ComputerName Server01, Server02, Server30 -Name BugStatus
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Disconnected  ITTasks                       None
8  ITTask  Server02        Disconnected  ITTasks                       None
2  ITTask  Server30        Disconnected  ITTasks                       None


PS> $Results = Receive-PSSession -Session $s
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Opened        ITTasks                  Available
8  ITTask  Server02        Opened        ITTasks                  Available
2  ITTask  Server30        Opened        ITTasks                  Available


PS> $Results

Bug Report - Domain 01
----------------------
ComputerName          BugCount          LastUpdated
--------------        ---------         ------------
Server01              121               Friday, December 30, 2011 5:03:34 PM
```

<span data-ttu-id="564c1-169">此 `Invoke-Command` Cmdlet 會在三部遠端電腦上執行腳本。</span><span class="sxs-lookup"><span data-stu-id="564c1-169">The `Invoke-Command` cmdlet runs a script on three remote computers.</span></span> <span data-ttu-id="564c1-170">因為腳本會收集並匯總來自多個資料庫的資料，所以通常會將腳本花在很長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="564c1-170">Because the script gathers and summarizes data from multiple databases, it often takes the script an extended time to finish.</span></span> <span data-ttu-id="564c1-171">此命令會使用 **InDisconnectedSession** 參數來啟動腳本，然後立即中斷會話的連線。</span><span class="sxs-lookup"><span data-stu-id="564c1-171">The command uses the **InDisconnectedSession** parameter that starts the scripts and then immediately disconnects the sessions.</span></span> <span data-ttu-id="564c1-172">**SessionOption** 參數會擴充已中斷連線會話的 **IdleTimeout** 值。</span><span class="sxs-lookup"><span data-stu-id="564c1-172">The **SessionOption** parameter extends the **IdleTimeout** value of the disconnected session.</span></span> <span data-ttu-id="564c1-173">中斷連線的會話在中斷連接時，會被視為閒置。</span><span class="sxs-lookup"><span data-stu-id="564c1-173">Disconnected sessions are considered idle from the moment they're disconnected.</span></span> <span data-ttu-id="564c1-174">請務必將閒置超時時間設定為足夠的時間，讓命令可以完成，而且您可以重新連線到會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-174">It's important to set the idle time-out for long enough so that the commands can complete and you can reconnect to the session.</span></span> <span data-ttu-id="564c1-175">只有當您建立 **PSSession** 時才可以設定 **IdleTimeout** ，而且只有在中斷與其的連接時才會變更。</span><span class="sxs-lookup"><span data-stu-id="564c1-175">You can set the **IdleTimeout** only when you create the **PSSession** and change it only when you disconnect from it.</span></span> <span data-ttu-id="564c1-176">當您連接至 **PSSession** 或接收其結果時，無法變更 **IdleTimeout** 值。</span><span class="sxs-lookup"><span data-stu-id="564c1-176">You can't change the **IdleTimeout** value when you connect to a **PSSession** or receiving its results.</span></span> <span data-ttu-id="564c1-177">執行命令之後，使用者會結束 PowerShell 並關閉電腦。</span><span class="sxs-lookup"><span data-stu-id="564c1-177">After running the command, the user exits PowerShell and closes the computer.</span></span>

<span data-ttu-id="564c1-178">下一天，使用者會繼續 Windows、啟動 PowerShell，並使用 `Get-PSSession` 來取得腳本執行所在的會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-178">The next day, the user resumes Windows, starts PowerShell, and uses `Get-PSSession` to get the sessions in which the scripts were running.</span></span> <span data-ttu-id="564c1-179">此命令會依電腦名稱稱、會話名稱和會話設定的名稱來識別會話，並將會話儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="564c1-179">The command identifies the sessions by the computer name, session name, and the name of the session configuration and saves the sessions in the `$s` variable.</span></span> <span data-ttu-id="564c1-180">`$s`系統會顯示變數的值，並顯示會話已中斷連線，但不在忙碌中。</span><span class="sxs-lookup"><span data-stu-id="564c1-180">The value of the `$s` variable is displayed and shows that the sessions are disconnected, but aren't busy.</span></span>

<span data-ttu-id="564c1-181">`Receive-PSSession`Cmdlet 會連接到變數中的會話 `$s` 並取得其結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-181">The `Receive-PSSession` cmdlet connects to the sessions in the `$s` variable and gets their results.</span></span>
<span data-ttu-id="564c1-182">命令會將結果儲存在 `$Results` 變數中。</span><span class="sxs-lookup"><span data-stu-id="564c1-182">The command saves the results in the `$Results` variable.</span></span> <span data-ttu-id="564c1-183">`$s`變數隨即顯示，並顯示會話已連線且可供命令使用。</span><span class="sxs-lookup"><span data-stu-id="564c1-183">The `$s` variable is displayed and shows that the sessions are connected and available for commands.</span></span>

<span data-ttu-id="564c1-184">變數中的腳本結果 `$Results` 會顯示在 PowerShell 主控台中。</span><span class="sxs-lookup"><span data-stu-id="564c1-184">The script results in the `$Results` variable are displayed in the PowerShell console.</span></span> <span data-ttu-id="564c1-185">如果有任何結果非預期，使用者可以在會話中執行命令來調查根本原因。</span><span class="sxs-lookup"><span data-stu-id="564c1-185">If any of the results are unexpected, the user can run commands in the sessions to investigate the root cause.</span></span>

### <span data-ttu-id="564c1-186">範例6：在已中斷連線的會話中執行工作</span><span class="sxs-lookup"><span data-stu-id="564c1-186">Example 6: Running a job in a disconnected session</span></span>

<span data-ttu-id="564c1-187">此範例顯示在已中斷連線的會話中執行的工作會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="564c1-187">This example shows what happens to a job that's running in a disconnected session.</span></span>

```
PS> $s = New-PSSession -ComputerName Server01 -Name Test
PS> $j = Invoke-Command -Session $s { 1..1500 | Foreach-Object {"Return $_"; sleep 30}} -AsJob
PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Running       True            Server01


PS> $s | Disconnect-PSSession

Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server01        Disconnected  Microsoft.PowerShell          None


PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Disconnected  True            Server01


PS> Receive-Job $j -Keep

Return 1
Return 2


PS> $s2 = Connect-PSSession -ComputerName Server01 -Name Test
PS> $j2 = Receive-PSSession -ComputerName Server01 -Name Test
PS> Receive-Job $j

Return 3
Return 4
```

<span data-ttu-id="564c1-188">此 `New-PSSession` Cmdlet 會在 Server01 電腦上建立測試會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-188">The `New-PSSession` cmdlet creates the Test session on the Server01 computer.</span></span> <span data-ttu-id="564c1-189">命令會將工作階段儲存於 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="564c1-189">The command saves the session in the `$s` variable.</span></span>

<span data-ttu-id="564c1-190">此 `Invoke-Command` Cmdlet 會在變數中的會話中執行命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-190">The `Invoke-Command` cmdlet runs a command in the session in the `$s` variable.</span></span> <span data-ttu-id="564c1-191">此命令會使用 **AsJob** 參數將命令當作工作執行，並在目前的會話中建立工作物件。</span><span class="sxs-lookup"><span data-stu-id="564c1-191">The command uses the **AsJob** parameter to run the command as a job and creates the job object in the current session.</span></span>
<span data-ttu-id="564c1-192">此命令會傳回儲存在變數中的工作物件 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-192">The command returns a job object that's saved in the `$j` variable.</span></span> <span data-ttu-id="564c1-193">`$j`變數會顯示工作物件。</span><span class="sxs-lookup"><span data-stu-id="564c1-193">The `$j` variable displays the job object.</span></span>

<span data-ttu-id="564c1-194">變數中的會話物件 `$s` 會沿著管線向下傳送 `Disconnect-PSSession` ，且會話會中斷連線。</span><span class="sxs-lookup"><span data-stu-id="564c1-194">The session object in the `$s` variable is sent down the pipeline to `Disconnect-PSSession` and the session is disconnected.</span></span>

<span data-ttu-id="564c1-195">`$j`變數隨即顯示，並顯示中斷連接工作物件到變數中的效果 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-195">The `$j` variable is displayed and shows the effect of disconnecting the job object in the `$j` variable.</span></span> <span data-ttu-id="564c1-196">工作狀態現在為「已中斷連線」。</span><span class="sxs-lookup"><span data-stu-id="564c1-196">The job state is now Disconnected.</span></span>

<span data-ttu-id="564c1-197">`Receive-Job`會在變數中的作業上執行 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-197">The `Receive-Job` is run on the job in the `$j` variable.</span></span> <span data-ttu-id="564c1-198">輸出顯示作業在會話與工作中斷連接之前，開始傳回輸出。</span><span class="sxs-lookup"><span data-stu-id="564c1-198">The output shows that the job began to return output before the session and the job were disconnected.</span></span>

<span data-ttu-id="564c1-199">此 `Connect-PSSession` Cmdlet 會在相同的用戶端會話中執行。</span><span class="sxs-lookup"><span data-stu-id="564c1-199">The `Connect-PSSession` cmdlet is run in the same client session.</span></span> <span data-ttu-id="564c1-200">此命令會重新連接至 Server01 電腦上的測試會話，並將會話儲存在 `$s2` 變數中。</span><span class="sxs-lookup"><span data-stu-id="564c1-200">The command reconnects to the Test session on the Server01 computer and saves the session in the `$s2` variable.</span></span>

<span data-ttu-id="564c1-201">`Receive-PSSession`Cmdlet 會取得會話中執行之工作的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-201">The `Receive-PSSession` cmdlet gets the results of the job that was running in the session.</span></span> <span data-ttu-id="564c1-202">因為此命令是在相同的會話中執行，所以 `Receive-PSSession` 預設會以作業形式傳回結果，並重複使用相同的工作物件。</span><span class="sxs-lookup"><span data-stu-id="564c1-202">Because the command is run in the same session, `Receive-PSSession` returns the results as a job by default and reuses the same job object.</span></span> <span data-ttu-id="564c1-203">此命令會將工作儲存在 `$j2` 變數中。</span><span class="sxs-lookup"><span data-stu-id="564c1-203">The command saves the job in the `$j2` variable.</span></span> <span data-ttu-id="564c1-204">`Receive-Job`Cmdlet 會取得變數中工作的結果 `$j` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-204">The `Receive-Job` cmdlet gets the results of the job in the `$j` variable.</span></span>

## <span data-ttu-id="564c1-205">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="564c1-205">PARAMETERS</span></span>

### <span data-ttu-id="564c1-206">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="564c1-206">-AllowRedirection</span></span>

<span data-ttu-id="564c1-207">指出此 Cmdlet 允許將此連線重新導向至替代的統一資源識別項 (URI) 。</span><span class="sxs-lookup"><span data-stu-id="564c1-207">Indicates that this cmdlet allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="564c1-208">使用 **ConnectionURI** 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。</span><span class="sxs-lookup"><span data-stu-id="564c1-208">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="564c1-209">根據預設，PowerShell 不會重新導向連線，但是您可以使用這個參數讓它重新導向連接。</span><span class="sxs-lookup"><span data-stu-id="564c1-209">By default, PowerShell doesn't redirect connections, but you can use this parameter to enable it to redirect the connection.</span></span>

<span data-ttu-id="564c1-210">您也可以變更 **MaximumConnectionRedirectionCount** 工作階段選項值，限制連線重新導向的次數。</span><span class="sxs-lookup"><span data-stu-id="564c1-210">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="564c1-211">使用 Cmdlet 的 **MaximumRedirection** 參數， `New-PSSessionOption` 或設定喜好設定變數的 **MaximumConnectionRedirectionCount** 屬性 `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-211">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="564c1-212">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="564c1-212">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-213">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="564c1-213">-ApplicationName</span></span>

<span data-ttu-id="564c1-214">指定應用程式。</span><span class="sxs-lookup"><span data-stu-id="564c1-214">Specifies an application.</span></span> <span data-ttu-id="564c1-215">此 Cmdlet 只會連接到使用指定應用程式的會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-215">This cmdlet connects only to sessions that use the specified application.</span></span>

<span data-ttu-id="564c1-216">輸入連線 URI 的應用程式名稱區段。</span><span class="sxs-lookup"><span data-stu-id="564c1-216">Enter the application name segment of the connection URI.</span></span> <span data-ttu-id="564c1-217">例如，在下列連接 URI 中，WSMan 是應用程式名稱： `http://localhost:5985/WSMAN` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-217">For example, in the following connection URI, WSMan is the application name: `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="564c1-218">工作階段的應用程式名稱儲存在工作階段的 **Runspace.ConnectionInfo.AppName** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="564c1-218">The application name of a session is stored in the **Runspace.ConnectionInfo.AppName** property of the session.</span></span>

<span data-ttu-id="564c1-219">參數的值可用來選取和篩選會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-219">The parameter's value is used to select and filter sessions.</span></span> <span data-ttu-id="564c1-220">它不會變更會話使用的應用程式。</span><span class="sxs-lookup"><span data-stu-id="564c1-220">It doesn't change the application that the session uses.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-221">-Authentication</span><span class="sxs-lookup"><span data-stu-id="564c1-221">-Authentication</span></span>

<span data-ttu-id="564c1-222">指定在命令中用來驗證使用者認證的機制，以重新連線到中斷連線的會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-222">Specifies the mechanism that's used to authenticate the user credentials in the command to reconnect to a disconnected session.</span></span> <span data-ttu-id="564c1-223">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="564c1-223">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="564c1-224">預設</span><span class="sxs-lookup"><span data-stu-id="564c1-224">Default</span></span>
- <span data-ttu-id="564c1-225">基本</span><span class="sxs-lookup"><span data-stu-id="564c1-225">Basic</span></span>
- <span data-ttu-id="564c1-226">Credssp</span><span class="sxs-lookup"><span data-stu-id="564c1-226">Credssp</span></span>
- <span data-ttu-id="564c1-227">Digest</span><span class="sxs-lookup"><span data-stu-id="564c1-227">Digest</span></span>
- <span data-ttu-id="564c1-228">Kerberos</span><span class="sxs-lookup"><span data-stu-id="564c1-228">Kerberos</span></span>
- <span data-ttu-id="564c1-229">交涉</span><span class="sxs-lookup"><span data-stu-id="564c1-229">Negotiate</span></span>
- <span data-ttu-id="564c1-230">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="564c1-230">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="564c1-231">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="564c1-231">The default value is Default.</span></span>

<span data-ttu-id="564c1-232">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="564c1-232">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="564c1-233">認證安全性支援提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="564c1-233">Credential Security Support Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="564c1-234">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="564c1-234">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="564c1-235">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="564c1-235">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-236">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="564c1-236">-CertificateThumbprint</span></span>

<span data-ttu-id="564c1-237">指定具有連線至已中斷連線工作階段權限之使用者帳戶的數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="564c1-237">Specifies the digital public key certificate (X509) of a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="564c1-238">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="564c1-238">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="564c1-239">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="564c1-239">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="564c1-240">憑證只能對應至本機使用者帳戶，而且無法使用網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="564c1-240">Certificates can be mapped only to local user accounts, and don't work with domain accounts.</span></span>

<span data-ttu-id="564c1-241">若要取得憑證指紋，請 `Get-Item` `Get-ChildItem` 在 PowerShell 磁片磁碟機中使用或命令 `Cert:` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-241">To get a certificate thumbprint, use a `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-242">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="564c1-242">-ComputerName</span></span>

<span data-ttu-id="564c1-243">指定儲存已中斷連線工作階段的電腦。</span><span class="sxs-lookup"><span data-stu-id="564c1-243">Specifies the computer on which the disconnected session is stored.</span></span> <span data-ttu-id="564c1-244">會話會儲存在伺服器端的電腦上，或連接的接收端。</span><span class="sxs-lookup"><span data-stu-id="564c1-244">Sessions are stored on the computer that's at the server-side, or receiving end of a connection.</span></span> <span data-ttu-id="564c1-245">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="564c1-245">The default is the local computer.</span></span>

<span data-ttu-id="564c1-246">輸入一部電腦 (FQDN) 的 NetBIOS 名稱、IP 位址或完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="564c1-246">Type the NetBIOS name, an IP address, or a fully qualified domain name (FQDN) of one computer.</span></span>
<span data-ttu-id="564c1-247">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="564c1-247">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="564c1-248">若要指定本機電腦，請輸入電腦名稱稱、點 (`.`) 、 `$env:COMPUTERNAME` 或 localhost。</span><span class="sxs-lookup"><span data-stu-id="564c1-248">To specify the local computer, type the computer name, a dot (`.`), `$env:COMPUTERNAME`, or localhost.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-249">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="564c1-249">-ConfigurationName</span></span>

<span data-ttu-id="564c1-250">指定會話設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="564c1-250">Specifies the name of a session configuration.</span></span> <span data-ttu-id="564c1-251">此 Cmdlet 只會連接到使用指定會話設定的會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-251">This cmdlet connects only to sessions that use the specified session configuration.</span></span>

<span data-ttu-id="564c1-252">輸入工作階段設定的設定名稱或完整資源 URI。</span><span class="sxs-lookup"><span data-stu-id="564c1-252">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="564c1-253">若您僅指定設定名稱，則會在前面加上下列架構 URI：</span><span class="sxs-lookup"><span data-stu-id="564c1-253">If you specify only the configuration name, the following schema URI is prepended:</span></span>

<span data-ttu-id="564c1-254">`http://schemas.microsoft.com/powershell`.</span><span class="sxs-lookup"><span data-stu-id="564c1-254">`http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="564c1-255">工作階段的設定名稱儲存在工作階段的 **ConfigurationName** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="564c1-255">The configuration name of a session is stored in the **ConfigurationName** property of the session.</span></span>

<span data-ttu-id="564c1-256">參數的值可用來選取和篩選會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-256">The parameter's value is used to select and filter sessions.</span></span> <span data-ttu-id="564c1-257">它不會變更會話使用的會話設定。</span><span class="sxs-lookup"><span data-stu-id="564c1-257">It doesn't change the session configuration that the session uses.</span></span>

<span data-ttu-id="564c1-258">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](./About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="564c1-258">For more information about session configurations, see [about_Session_Configurations](./About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-259">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="564c1-259">-ConnectionUri</span></span>

<span data-ttu-id="564c1-260">指定 URI，定義用來重新連線至已中斷連線會話的連接端點。</span><span class="sxs-lookup"><span data-stu-id="564c1-260">Specifies a URI that defines the connection endpoint that is used to reconnect to the disconnected session.</span></span>

<span data-ttu-id="564c1-261">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="564c1-261">The URI must be fully qualified.</span></span> <span data-ttu-id="564c1-262">字串的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="564c1-262">The string's format is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="564c1-263">預設值如下：</span><span class="sxs-lookup"><span data-stu-id="564c1-263">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="564c1-264">如果您未指定連接 URI，您可以使用 **UseSSL** 、 **ComputerName** 、 **Port** 及 **ApplicationName** 參數來指定連接 uri 值。</span><span class="sxs-lookup"><span data-stu-id="564c1-264">If you don't specify a connection URI, you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the connection URI values.</span></span>

<span data-ttu-id="564c1-265">URI 的 **Transport** 區段有效值為 HTTP 與 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="564c1-265">Valid values for the **Transport** segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="564c1-266">如果您指定具有傳輸區段的連線 URI，但未指定埠，則會使用標準埠：80（適用于 HTTP）和443（適用于 HTTPS）來建立會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-266">If you specify a connection URI with a Transport segment, but don't specify a port, the session is created with standard ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="564c1-267">若要使用 PowerShell 遠端的預設埠，請指定 HTTP 的埠5985或 HTTPS 的5986。</span><span class="sxs-lookup"><span data-stu-id="564c1-267">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="564c1-268">如果目的地電腦將連線重新導向至不同的 URI，除非您在命令中使用 **AllowRedirection** 參數，否則 PowerShell 會禁止重新導向。</span><span class="sxs-lookup"><span data-stu-id="564c1-268">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-269">-Credential</span><span class="sxs-lookup"><span data-stu-id="564c1-269">-Credential</span></span>

<span data-ttu-id="564c1-270">指定具有連線至已中斷連線工作階段權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="564c1-270">Specifies a user account that has permission to connect to the disconnected session.</span></span> <span data-ttu-id="564c1-271">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="564c1-271">The default is the current user.</span></span>

<span data-ttu-id="564c1-272">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-272">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="564c1-273">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="564c1-273">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="564c1-274">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="564c1-274">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="564c1-275">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="564c1-275">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-276">-Id</span><span class="sxs-lookup"><span data-stu-id="564c1-276">-Id</span></span>

<span data-ttu-id="564c1-277">指定已中斷連線會話的識別碼。</span><span class="sxs-lookup"><span data-stu-id="564c1-277">Specifies the ID of a disconnected session.</span></span> <span data-ttu-id="564c1-278">只有當已中斷連線的會話先前連接到目前的會話時， **識別碼** 參數才有效。</span><span class="sxs-lookup"><span data-stu-id="564c1-278">The **Id** parameter works only when the disconnected session was previously connected to the current session.</span></span>

<span data-ttu-id="564c1-279">當會話儲存在本機電腦上，但未連接到目前的會話時，此參數有效，但不有效。</span><span class="sxs-lookup"><span data-stu-id="564c1-279">This parameter is valid, but not effective, when the session is stored on the local computer, but wasn't connected to the current session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-280">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="564c1-280">-InstanceId</span></span>

<span data-ttu-id="564c1-281">指定已中斷連線工作階段的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="564c1-281">Specifies the instance ID of the disconnected session.</span></span> <span data-ttu-id="564c1-282">實例識別碼是 GUID，可唯一識別本機或遠端電腦上的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="564c1-282">The instance ID is a GUID that uniquely identifies a **PSSession** on a local or remote computer.</span></span> <span data-ttu-id="564c1-283">實例識別碼儲存在 **PSSession** 的 **InstanceID** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="564c1-283">The instance ID is stored in the **InstanceID** property of the **PSSession** .</span></span>

```yaml
Type: System.Guid
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-284">-JobName</span><span class="sxs-lookup"><span data-stu-id="564c1-284">-JobName</span></span>

<span data-ttu-id="564c1-285">指定傳回之作業的易記名稱 `Receive-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-285">Specifies a friendly name for the job that `Receive-PSSession` returns.</span></span>

<span data-ttu-id="564c1-286">`Receive-PSSession` 當 **OutTarget** 參數的值為 job，或在已中斷連線會話中執行的工作在目前的會話中啟動時，會傳回工作。</span><span class="sxs-lookup"><span data-stu-id="564c1-286">`Receive-PSSession` returns a job when the value of the **OutTarget** parameter is Job or the job that's running in the disconnected session was started in the current session.</span></span>

<span data-ttu-id="564c1-287">如果在已中斷連線的會話中執行的工作是在目前會話中啟動，則 PowerShell 會重複使用會話中的原始工作物件，並忽略 **JobName** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="564c1-287">If the job that's running in the disconnected session was started in the current session, PowerShell reuses the original job object in the session and ignores the value of the **JobName** parameter.</span></span>

<span data-ttu-id="564c1-288">如果在已中斷連線的會話中執行的工作是在不同的會話中啟動，則 PowerShell 會建立新的工作物件。</span><span class="sxs-lookup"><span data-stu-id="564c1-288">If the job that's running in the disconnected session was started in a different session, PowerShell creates a new job object.</span></span> <span data-ttu-id="564c1-289">它會使用預設名稱，但是您可以使用此參數來變更名稱。</span><span class="sxs-lookup"><span data-stu-id="564c1-289">It uses a default name, but you can use this parameter to change the name.</span></span>

<span data-ttu-id="564c1-290">如果 **OutTarget** 參數的預設值或明確值不是工作，則命令會成功，但是 **JobName** 參數沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="564c1-290">If the default value or explicit value of the **OutTarget** parameter isn't Job, the command succeeds, but the **JobName** parameter has no effect.</span></span>

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

### <span data-ttu-id="564c1-291">-Name</span><span class="sxs-lookup"><span data-stu-id="564c1-291">-Name</span></span>

<span data-ttu-id="564c1-292">指定已中斷連線工作階段的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="564c1-292">Specifies the friendly name of the disconnected session.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ConnectionUriSessionName, SessionName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-293">-OutTarget</span><span class="sxs-lookup"><span data-stu-id="564c1-293">-OutTarget</span></span>

<span data-ttu-id="564c1-294">決定如何傳回工作階段結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-294">Determines how the session results are returned.</span></span> <span data-ttu-id="564c1-295">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="564c1-295">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="564c1-296">**作業** 。</span><span class="sxs-lookup"><span data-stu-id="564c1-296">**Job** .</span></span> <span data-ttu-id="564c1-297">以非同步方式，傳回工作物件中的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-297">Returns the results asynchronously in a job object.</span></span> <span data-ttu-id="564c1-298">您可以使用 **JobName** 參數，指定工作的名稱或新名稱。</span><span class="sxs-lookup"><span data-stu-id="564c1-298">You can use the **JobName** parameter to specify a name or new name for the job.</span></span>
- <span data-ttu-id="564c1-299">**主機** 。</span><span class="sxs-lookup"><span data-stu-id="564c1-299">**Host** .</span></span> <span data-ttu-id="564c1-300">將結果傳回命令列 (同步)。</span><span class="sxs-lookup"><span data-stu-id="564c1-300">Returns the results to the command line (synchronously).</span></span> <span data-ttu-id="564c1-301">若正在繼續命令，或結果包含大量物件，則回應可能會延遲。</span><span class="sxs-lookup"><span data-stu-id="564c1-301">If the command is being resumed or the results consist of a large number of objects, the response might be delayed.</span></span>

<span data-ttu-id="564c1-302">**OutTarget** 參數的預設值為 Host。</span><span class="sxs-lookup"><span data-stu-id="564c1-302">The default value of the **OutTarget** parameter is Host.</span></span> <span data-ttu-id="564c1-303">如果在已中斷連線的會話中接收的命令是在目前會話中啟動，則 **OutTarget** 參數的預設值會是命令啟動的形式。</span><span class="sxs-lookup"><span data-stu-id="564c1-303">If the command that's being received in a disconnected session was started in the current session, the default value of the **OutTarget** parameter is the form in which the command was started.</span></span> <span data-ttu-id="564c1-304">如果命令是以作業的形式啟動，則預設會以工作傳回。</span><span class="sxs-lookup"><span data-stu-id="564c1-304">If the command was started as a job, by default, it's returned as a job.</span></span> <span data-ttu-id="564c1-305">否則，預設會將它傳回至主機程式。</span><span class="sxs-lookup"><span data-stu-id="564c1-305">Otherwise, it's returned to the host program by default.</span></span>

<span data-ttu-id="564c1-306">主機程式在命令列顯示傳回的物件時，通常不會有延遲，但是也可能不同。</span><span class="sxs-lookup"><span data-stu-id="564c1-306">Typically, the host program displays returned objects at the command line without delay, but this behavior can vary.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutTarget
Parameter Sets: (All)
Aliases:
Accepted values: Default, Host, Job

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-307">-Port</span><span class="sxs-lookup"><span data-stu-id="564c1-307">-Port</span></span>

<span data-ttu-id="564c1-308">指定遠端電腦用來重新連線至會話的網路埠。</span><span class="sxs-lookup"><span data-stu-id="564c1-308">Specifies the remote computer's network port that's used to reconnect to the session.</span></span> <span data-ttu-id="564c1-309">若要連接到遠端電腦，它必須在連線使用的埠上接聽。</span><span class="sxs-lookup"><span data-stu-id="564c1-309">To connect to a remote computer, it must be listening on the port that the connection uses.</span></span> <span data-ttu-id="564c1-310">預設的埠是5985，也就是 HTTP 的 WinRM 埠和5986，也就是 HTTPS 的 WinRM 埠。</span><span class="sxs-lookup"><span data-stu-id="564c1-310">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="564c1-311">使用替代埠之前，您必須先將遠端電腦上的 WinRM 接聽程式設定為在該埠上接聽。</span><span class="sxs-lookup"><span data-stu-id="564c1-311">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen on that port.</span></span> <span data-ttu-id="564c1-312">若要設定接聽程式，請在 PowerShell 提示字元中輸入下列兩個命令：</span><span class="sxs-lookup"><span data-stu-id="564c1-312">To configure the listener, type the following two commands at the PowerShell prompt:</span></span>

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

<span data-ttu-id="564c1-313">除非必要，否則請勿使用 **Port** 參數。</span><span class="sxs-lookup"><span data-stu-id="564c1-313">Don't use the **Port** parameter unless it's necessary.</span></span> <span data-ttu-id="564c1-314">命令中設定的埠會套用到命令執行所在的所有電腦或會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-314">The port that's set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="564c1-315">替代的連接埠設定可能使得命令無法在全部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="564c1-315">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-316">-Session</span><span class="sxs-lookup"><span data-stu-id="564c1-316">-Session</span></span>

<span data-ttu-id="564c1-317">指定已中斷連線的工作階段。</span><span class="sxs-lookup"><span data-stu-id="564c1-317">Specifies the disconnected session.</span></span> <span data-ttu-id="564c1-318">輸入包含 **pssession** 的變數，或輸入可建立或取得 **pssession** 的命令，例如 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="564c1-318">Enter a variable that contains the **PSSession** or a command that creates or gets the **PSSession** , such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-319">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="564c1-319">-SessionOption</span></span>

<span data-ttu-id="564c1-320">指定會話的 advanced 選項。</span><span class="sxs-lookup"><span data-stu-id="564c1-320">Specifies advanced options for the session.</span></span> <span data-ttu-id="564c1-321">輸入 **SessionOption** 物件（例如您使用 Cmdlet 建立的物件 `New-PSSessionOption` ），或輸入雜湊表，其中索引鍵為會話選項名稱，而值為會話選項值。</span><span class="sxs-lookup"><span data-stu-id="564c1-321">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="564c1-322">選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。</span><span class="sxs-lookup"><span data-stu-id="564c1-322">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it's set.</span></span> <span data-ttu-id="564c1-323">否則，將以工作階段設定中設定的選項建立預設值。</span><span class="sxs-lookup"><span data-stu-id="564c1-323">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="564c1-324">會話選項值的優先順序高於 `$PSSessionOption` 喜好設定變數和會話設定中設定之會話的預設值。</span><span class="sxs-lookup"><span data-stu-id="564c1-324">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="564c1-325">不過，它們的優先順序不會高於會話設定中所設定的最大值、配額或限制。</span><span class="sxs-lookup"><span data-stu-id="564c1-325">However, they don't take precedence over maximum values, quotas, or limits set in the session configuration.</span></span>

<span data-ttu-id="564c1-326">如需包含預設值之會話選項的描述，請參閱 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-326">For a description of the session options that includes the default values, see `New-PSSessionOption`.</span></span> <span data-ttu-id="564c1-327">如需 **$PSSessionOption** 喜好設定變數的詳細資訊，請參閱 [about_Preference_Variables](./About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="564c1-327">For information about the **$PSSessionOption** preference variable, see [about_Preference_Variables](./About/about_Preference_Variables.md).</span></span> <span data-ttu-id="564c1-328">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](./About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="564c1-328">For more information about session configurations, see [about_Session_Configurations](./About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-329">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="564c1-329">-UseSSL</span></span>

<span data-ttu-id="564c1-330">指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來連線到中斷連線的會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-330">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to connect to the disconnected session.</span></span> <span data-ttu-id="564c1-331">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="564c1-331">By default, SSL isn't used.</span></span>

<span data-ttu-id="564c1-332">WS-Management 加密透過網路傳輸的所有 PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="564c1-332">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="564c1-333">**UseSSL** 為額外的保護，可使用 HTTPS 連線取代 HTTP 連線來傳送資料。</span><span class="sxs-lookup"><span data-stu-id="564c1-333">**UseSSL** is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="564c1-334">如果您使用此參數，而且在用於命令的埠上無法使用 SSL，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="564c1-334">If you use this parameter and SSL isn't available on the port that's used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="564c1-335">-Confirm</span><span class="sxs-lookup"><span data-stu-id="564c1-335">-Confirm</span></span>

<span data-ttu-id="564c1-336">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="564c1-336">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="564c1-337">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="564c1-337">-WhatIf</span></span>

<span data-ttu-id="564c1-338">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="564c1-338">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="564c1-339">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="564c1-339">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="564c1-340">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="564c1-340">CommonParameters</span></span>

<span data-ttu-id="564c1-341">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="564c1-341">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="564c1-342">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="564c1-342">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="564c1-343">輸入</span><span class="sxs-lookup"><span data-stu-id="564c1-343">INPUTS</span></span>

### <span data-ttu-id="564c1-344">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="564c1-344">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="564c1-345">您可以使用管線將會話物件傳送至此 Cmdlet，例如 Cmdlet 所傳回的物件 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-345">You can pipe session objects to this cmdlet, such as objects returned by the `Get-PSSession` cmdlet.</span></span>

### <span data-ttu-id="564c1-346">System.Int32</span><span class="sxs-lookup"><span data-stu-id="564c1-346">System.Int32</span></span>

<span data-ttu-id="564c1-347">您可以透過管線將會話識別碼傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="564c1-347">You can pipe session Ids to this cmdlet.</span></span>

### <span data-ttu-id="564c1-348">System.Guid</span><span class="sxs-lookup"><span data-stu-id="564c1-348">System.Guid</span></span>

<span data-ttu-id="564c1-349">您可以透過管線將會話的實例識別碼傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="564c1-349">You can pipe the instance Ids of sessions this cmdlet.</span></span>

### <span data-ttu-id="564c1-350">System.String</span><span class="sxs-lookup"><span data-stu-id="564c1-350">System.String</span></span>

<span data-ttu-id="564c1-351">您可以透過管線將會話名稱傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="564c1-351">You can pipe session names to this cmdlet.</span></span>

## <span data-ttu-id="564c1-352">輸出</span><span class="sxs-lookup"><span data-stu-id="564c1-352">OUTPUTS</span></span>

### <span data-ttu-id="564c1-353">管理. 作業或 PSObject</span><span class="sxs-lookup"><span data-stu-id="564c1-353">System.Management.Automation.Job or PSObject</span></span>

<span data-ttu-id="564c1-354">此 Cmdlet 會傳回在已中斷連線會話中執行的命令結果（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="564c1-354">This cmdlet returns the results of commands that ran in the disconnected session, if any.</span></span> <span data-ttu-id="564c1-355">如果 **OutTarget** 參數的值或預設值為 job，則會傳回 `Receive-PSSession` 工作物件。</span><span class="sxs-lookup"><span data-stu-id="564c1-355">If the value or default value of the **OutTarget** parameter is Job, `Receive-PSSession` returns a job object.</span></span> <span data-ttu-id="564c1-356">否則，它會傳回代表該命令結果的物件。</span><span class="sxs-lookup"><span data-stu-id="564c1-356">Otherwise, it returns objects that represent that command results.</span></span>

## <span data-ttu-id="564c1-357">注意</span><span class="sxs-lookup"><span data-stu-id="564c1-357">NOTES</span></span>

<span data-ttu-id="564c1-358">`Receive-PSSession` 只從已中斷連線的會話取得結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-358">`Receive-PSSession` gets results only from sessions that were disconnected.</span></span> <span data-ttu-id="564c1-359">只有在執行 PowerShell 3.0 或更新版本的電腦上連線或終止的會話，才能中斷連線並重新連接。</span><span class="sxs-lookup"><span data-stu-id="564c1-359">Only sessions that are connected to, or terminate at, computers that run PowerShell 3.0 or later versions can be disconnected and reconnected.</span></span>

<span data-ttu-id="564c1-360">如果在已中斷連線的會話中執行的命令未產生結果，或是結果已經傳回至另一個會話，則 `Receive-PSSession` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="564c1-360">If the commands that were running in the disconnected session didn't generate results or if the results were already returned to another session, `Receive-PSSession` doesn't generate any output.</span></span>

<span data-ttu-id="564c1-361">會話的輸出緩衝處理模式會決定會話中斷連線時，會話中的命令如何管理輸出。</span><span class="sxs-lookup"><span data-stu-id="564c1-361">A session's output buffering mode determines how commands in the session manage output when the session is disconnected.</span></span> <span data-ttu-id="564c1-362">當會話的 **OutputBufferingMode** 選項值為 Drop 且輸出緩衝區已滿時，命令就會開始刪除輸出。</span><span class="sxs-lookup"><span data-stu-id="564c1-362">When the value of the **OutputBufferingMode** option of the session is Drop and the output buffer is full, the command starts to delete output.</span></span> <span data-ttu-id="564c1-363">`Receive-PSSession` 無法復原此輸出。</span><span class="sxs-lookup"><span data-stu-id="564c1-363">`Receive-PSSession` can't recover this output.</span></span> <span data-ttu-id="564c1-364">如需輸出緩衝處理模式選項的詳細資訊，請參閱 [PSSessionOption](New-PSSessionOption.md) 和 [>new-pstransportoption](New-PSTransportOption.md) Cmdlet 的說明文章。</span><span class="sxs-lookup"><span data-stu-id="564c1-364">For more information about the output buffering mode option, see the help articles for the [New-PSSessionOption](New-PSSessionOption.md) and [New-PSTransportOption](New-PSTransportOption.md) cmdlets.</span></span>

<span data-ttu-id="564c1-365">當您連接到 **pssession** 或接收結果時，無法變更 **PSSession** 的空閒超時值。</span><span class="sxs-lookup"><span data-stu-id="564c1-365">You can't change the idle time-out value of a **PSSession** when you connect to the **PSSession** or receive results.</span></span> <span data-ttu-id="564c1-366">的 **SessionOption** 參數 `Receive-PSSession` 會採用具有 **IdleTimeout** 值的 **SessionOption** 物件。</span><span class="sxs-lookup"><span data-stu-id="564c1-366">The **SessionOption** parameter of `Receive-PSSession` takes a **SessionOption** object that has an **IdleTimeout** value.</span></span> <span data-ttu-id="564c1-367">不過，當 **IdleTimeout** **SessionOption** 它 **IdleTimeout** `$PSSessionOption` 連接到 **PSSession** 或接收結果時，會忽略 SessionOption 物件的 idletimeout 值和變數的 idletimeout 值。</span><span class="sxs-lookup"><span data-stu-id="564c1-367">However, the **IdleTimeout** value of the **SessionOption** object and the **IdleTimeout** value of the `$PSSessionOption` variable are ignored when it connects to a **PSSession** or receiving results.</span></span>

- <span data-ttu-id="564c1-368">當您建立 **pssession** 時，可以使用 **PSSession** `New-PSSession` 或 `Invoke-Command` Cmdlet，以及從 **pssession** 中斷連接時，設定和變更 pssession 的閒置時間。</span><span class="sxs-lookup"><span data-stu-id="564c1-368">You can set and change the idle time-out of a **PSSession** when you create the **PSSession** , by using the `New-PSSession` or `Invoke-Command` cmdlets, and when you disconnect from the **PSSession** .</span></span>
- <span data-ttu-id="564c1-369">**PSSession** 的 **IdleTimeout** 屬性對中斷連線的會話而言是不可或缺的，因為它會決定中斷連線的會話在遠端電腦上的維護時間。</span><span class="sxs-lookup"><span data-stu-id="564c1-369">The **IdleTimeout** property of a **PSSession** is critical to disconnected sessions because it determines how long a disconnected session is maintained on the remote computer.</span></span> <span data-ttu-id="564c1-370">已中斷連線的工作階段一被中斷連線，便被視為閒置，即使命令仍然在已中斷連線的工作階段中執行也是如此。</span><span class="sxs-lookup"><span data-stu-id="564c1-370">Disconnected sessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

<span data-ttu-id="564c1-371">如果您使用指令程式的 **AsJob** 參數在遠端會話中啟動啟動作業 `Invoke-Command` ，則會在目前的會話中建立工作物件，即使工作是在遠端會話中執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="564c1-371">If you start a start a job in a remote session by using the **AsJob** parameter of the `Invoke-Command` cmdlet, the job object is created in the current session, even though the job runs in the remote session.</span></span> <span data-ttu-id="564c1-372">如果您中斷遠端會話的連線，目前會話中的工作物件就會與工作中斷連線。</span><span class="sxs-lookup"><span data-stu-id="564c1-372">If you disconnect the remote session, the job object in the current session is disconnected from the job.</span></span> <span data-ttu-id="564c1-373">工作物件包含傳回的任何結果，但不會從已中斷連線會話中的作業接收新的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-373">The job object contains any results that were returned to it, but doesn't receive new results from the job in the disconnected session.</span></span>

<span data-ttu-id="564c1-374">如果不同的用戶端連接到包含執行中工作的會話，則新連線的會話將無法使用傳遞至原始會話中原始工作物件的結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-374">If a different client connects to the session that contains the running job, the results that were delivered to the original job object in the original session aren't available in the newly connected session.</span></span> <span data-ttu-id="564c1-375">只有未傳遞至原始工作物件的結果，才能在重新連線的工作階段中使用。</span><span class="sxs-lookup"><span data-stu-id="564c1-375">Only results that were not delivered to the original job object are available in the reconnected session.</span></span>

<span data-ttu-id="564c1-376">同樣地，如果您在會話中啟動腳本，然後從會話中斷連線，則在中斷連接之前，腳本傳遞給會話的任何結果都不會提供給連線到該會話的另一個用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="564c1-376">Similarly, if you start a script in a session and then disconnect from the session, any results that the script delivers to the session before disconnecting aren't available to another client that connects to the session.</span></span>

<span data-ttu-id="564c1-377">若要防止您要中斷連線的會話中遺失資料，請使用 Cmdlet 的 **InDisconnectedSession** 參數 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="564c1-377">To prevent data loss in sessions that you intend to disconnect, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="564c1-378">因為此參數會避免將結果傳回目前工作階段，因此重新連線至工作階段時，所有結果都可供使用。</span><span class="sxs-lookup"><span data-stu-id="564c1-378">Because this parameter prevents results from being returned to the current session, all results are available when the session is reconnected.</span></span>

<span data-ttu-id="564c1-379">您也可以使用 `Invoke-Command` Cmdlet `Start-Job` 在遠端會話中執行命令，以避免資料遺失。</span><span class="sxs-lookup"><span data-stu-id="564c1-379">You can also prevent data loss by using the `Invoke-Command` cmdlet to run a `Start-Job` command in the remote session.</span></span> <span data-ttu-id="564c1-380">在此狀況下，工作物件將建立於遠端工作階段中。</span><span class="sxs-lookup"><span data-stu-id="564c1-380">In this case, the job object is created in the remote session.</span></span> <span data-ttu-id="564c1-381">您無法使用 `Receive-PSSession` Cmdlet 來取得工作結果。</span><span class="sxs-lookup"><span data-stu-id="564c1-381">You can't use the `Receive-PSSession` cmdlet to get the job results.</span></span> <span data-ttu-id="564c1-382">相反地，請使用 `Connect-PSSession` Cmdlet 連接到會話，然後使用 `Invoke-Command` Cmdlet `Receive-Job` 在會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="564c1-382">Instead, use the `Connect-PSSession` cmdlet to connect to the session and then use the `Invoke-Command` cmdlet to run a `Receive-Job` command in the session.</span></span>

<span data-ttu-id="564c1-383">當包含執行中工作的會話中斷連線，然後重新連線時，只有在作業已中斷連線並重新連線至相同會話，且重新連線的命令未指定新工作名稱時，才會重複使用原始工作物件。</span><span class="sxs-lookup"><span data-stu-id="564c1-383">When a session that contains a running job is disconnected and then reconnected, the original job object is reused only if the job is disconnected and reconnected to the same session, and the command to reconnect doesn't specify a new job name.</span></span> <span data-ttu-id="564c1-384">如果會話重新連線至不同的用戶端會話，或指定了新的作業名稱，則 PowerShell 會為新會話建立新的工作物件。</span><span class="sxs-lookup"><span data-stu-id="564c1-384">If the session is reconnected to a different client session or a new job name is specified, PowerShell creates a new job object for the new session.</span></span>

<span data-ttu-id="564c1-385">當您中斷連接 **PSSession** 時，會話狀態會中斷連線，而且可用性為 None。</span><span class="sxs-lookup"><span data-stu-id="564c1-385">When you disconnect a **PSSession** , the session state is Disconnected and the availability is None.</span></span>

- <span data-ttu-id="564c1-386">**State** 屬性的值是相對於目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="564c1-386">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="564c1-387">值為「已中斷連線」表示 **PSSession** 未連接到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-387">A value of Disconnected means that the **PSSession** isn't connected to the current session.</span></span> <span data-ttu-id="564c1-388">但是，它並不表示 **PSSession** 與所有會話中斷連接。</span><span class="sxs-lookup"><span data-stu-id="564c1-388">However, it doesn't mean that the **PSSession** is disconnected from all sessions.</span></span> <span data-ttu-id="564c1-389">它可能連線不同的工作階段。</span><span class="sxs-lookup"><span data-stu-id="564c1-389">It might be connected to a different session.</span></span>
  <span data-ttu-id="564c1-390">若要判斷是否可以連線或重新連線工作階段，請使用 **Availability** 屬性。</span><span class="sxs-lookup"><span data-stu-id="564c1-390">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>
- <span data-ttu-id="564c1-391">**Availability** 值為 None 表示您可以連線工作階段。</span><span class="sxs-lookup"><span data-stu-id="564c1-391">An **Availability** value of None indicates that you can connect to the session.</span></span> <span data-ttu-id="564c1-392">「忙碌」值表示您無法連接到 **PSSession** ，因為它已連接到另一個會話。</span><span class="sxs-lookup"><span data-stu-id="564c1-392">A value of Busy indicates that you can't connect to the **PSSession** because it's connected to another session.</span></span>
- <span data-ttu-id="564c1-393">如需會話的 **State** 屬性值的詳細資訊，請參閱 MSDN library 中的 [ runspacestate](/dotnet/api/system.management.automation.runspaces.runspacestate) 。</span><span class="sxs-lookup"><span data-stu-id="564c1-393">For more information about the values of the **State** property of sessions, see [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate) in the MSDN library.</span></span>
- <span data-ttu-id="564c1-394">如需會話的 **Availability** 屬性值的詳細資訊，請參閱 [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。</span><span class="sxs-lookup"><span data-stu-id="564c1-394">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="564c1-395">相關連結</span><span class="sxs-lookup"><span data-stu-id="564c1-395">RELATED LINKS</span></span>

[<span data-ttu-id="564c1-396">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="564c1-396">about_PSSessions</span></span>](./About/about_PSSessions.md)

[<span data-ttu-id="564c1-397">about_Remote</span><span class="sxs-lookup"><span data-stu-id="564c1-397">about_Remote</span></span>](./About/about_Remote.md)

[<span data-ttu-id="564c1-398">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="564c1-398">about_Remote_Disconnected_Sessions</span></span>](./About/about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="564c1-399">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="564c1-399">about_Session_Configurations</span></span>](./About/about_Session_Configurations.md)

[<span data-ttu-id="564c1-400">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="564c1-400">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="564c1-401">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="564c1-401">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="564c1-402">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="564c1-402">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="564c1-403">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="564c1-403">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="564c1-404">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="564c1-404">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="564c1-405">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="564c1-405">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="564c1-406">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="564c1-406">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="564c1-407">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="564c1-407">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="564c1-408">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="564c1-408">Remove-PSSession</span></span>](Remove-PSSession.md)
