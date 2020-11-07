---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disconnect-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-PSSession
ms.openlocfilehash: 41f278541d1375697ccb95504b7d7b1d28027786
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344060"
---
# <span data-ttu-id="b200e-103">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="b200e-103">Disconnect-PSSession</span></span>

## <span data-ttu-id="b200e-104">概要</span><span class="sxs-lookup"><span data-stu-id="b200e-104">SYNOPSIS</span></span>
<span data-ttu-id="b200e-105">從工作階段中斷連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-105">Disconnects from a session.</span></span>

## <span data-ttu-id="b200e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b200e-106">SYNTAX</span></span>

### <span data-ttu-id="b200e-107">工作階段 (預設)</span><span class="sxs-lookup"><span data-stu-id="b200e-107">Session (Default)</span></span>

```
Disconnect-PSSession [-Session] <PSSession[]> [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="b200e-108">Name</span><span class="sxs-lookup"><span data-stu-id="b200e-108">Name</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b200e-109">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b200e-109">InstanceId</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b200e-110">Id</span><span class="sxs-lookup"><span data-stu-id="b200e-110">Id</span></span>

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b200e-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b200e-111">DESCRIPTION</span></span>

<span data-ttu-id="b200e-112">`Disconnect-PSSession`Cmdlet 會 `New-PSSession` 從目前的會話中斷 ( "PSSession" ) 的 PowerShell 會話連線，例如使用 Cmdlet 啟動的會話。</span><span class="sxs-lookup"><span data-stu-id="b200e-112">The `Disconnect-PSSession` cmdlet disconnects a PowerShell session ("PSSession"), such as one started by using the `New-PSSession` cmdlet, from the current session.</span></span> <span data-ttu-id="b200e-113">如此一來，PSSession 就處於中斷連線的狀態。</span><span class="sxs-lookup"><span data-stu-id="b200e-113">As a result, the PSSession is in a disconnected state.</span></span> <span data-ttu-id="b200e-114">您可以從目前的工作階段，或從本機電腦或另一部電腦的另一個工作階段，連線到中斷連線的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="b200e-114">You can connect to the disconnected PSSession from the current session or from another session on the local computer or a different computer.</span></span>

<span data-ttu-id="b200e-115">此 `Disconnect-PSSession` Cmdlet 只會中斷連接到目前會話的開啟 pssession。</span><span class="sxs-lookup"><span data-stu-id="b200e-115">The `Disconnect-PSSession` cmdlet disconnects only open PSSessions that are connected to the current session.</span></span> <span data-ttu-id="b200e-116">`Disconnect-PSSession` 無法中斷中斷或關閉的 Pssession，或使用 Cmdlet 啟動的互動式 Pssession， `Enter-PSSession` 而且無法中斷連接到其他會話的 pssession。</span><span class="sxs-lookup"><span data-stu-id="b200e-116">`Disconnect-PSSession` cannot disconnect broken or closed PSSessions, or interactive PSSessions started by using the `Enter-PSSession` cmdlet, and it cannot disconnect PSSessions that are connected to other sessions.</span></span>

<span data-ttu-id="b200e-117">若要重新連線到中斷連線的 PSSession，請使用 `Connect-PSSession` 或 `Receive-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b200e-117">To reconnect to a disconnected PSSession, use the `Connect-PSSession` or `Receive-PSSession` cmdlets.</span></span>

<span data-ttu-id="b200e-118">當 PSSession 已中斷連線時，PSSession 中的命令會繼續執行，直到它們完成為止，除非 PSSession 逾時或 PSSession 中的命令被已滿的輸出緩衝區封鎖。</span><span class="sxs-lookup"><span data-stu-id="b200e-118">When a PSSession is disconnected, the commands in the PSSession continue to run until they complete, unless the PSSession times out or the commands in the PSSession are blocked by a full output buffer.</span></span> <span data-ttu-id="b200e-119">若要變更閒置逾時，請使用 **IdleTimeoutSec** 參數。</span><span class="sxs-lookup"><span data-stu-id="b200e-119">To change the idle timeout, use the **IdleTimeoutSec** parameter.</span></span> <span data-ttu-id="b200e-120">若要變更輸出緩衝處理模式，請使用 **OutputBufferingMode** 參數。您也可以使用 Cmdlet 的 **InDisconnectedSession** 參數，在中斷連線的 `Invoke-Command` 會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="b200e-120">To change the output buffering mode, use the **OutputBufferingMode** parameter You can also use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet to run a command in a disconnected session.</span></span>

<span data-ttu-id="b200e-121">如需中斷連線工作階段功能的詳細資訊，請參閱 [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="b200e-121">For more information about the Disconnected Sessions feature, see [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).</span></span>

<span data-ttu-id="b200e-122">此 Cmdlet 是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="b200e-122">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="b200e-123">範例</span><span class="sxs-lookup"><span data-stu-id="b200e-123">EXAMPLES</span></span>

### <span data-ttu-id="b200e-124">範例 1-依名稱中斷會話的連線</span><span class="sxs-lookup"><span data-stu-id="b200e-124">Example 1 - Disconnect a session by name</span></span>

<span data-ttu-id="b200e-125">此命令中斷 Server01 電腦上 UpdateSession PSSession 與目前工作階段的連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-125">This command disconnects the UpdateSession PSSession on the Server01 computer from the current session.</span></span> <span data-ttu-id="b200e-126">命令使用 **Name** 參數來識別 PSSession。</span><span class="sxs-lookup"><span data-stu-id="b200e-126">The command uses the **Name** parameter to identify the PSSession.</span></span>

```
PS> Disconnect-PSSession -Name UpdateSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  UpdateSession   Server01        Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="b200e-127">輸出顯示中斷連線的嘗試成功。</span><span class="sxs-lookup"><span data-stu-id="b200e-127">The output shows that the attempt to disconnect was successful.</span></span> <span data-ttu-id="b200e-128">工作階段狀態是 Disconnected 且可用性是 None，表示工作階段並非忙碌中，且可以重新連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-128">The session state is Disconnected and the Availability is None, which indicates that the session is not busy and can be reconnected.</span></span>

### <span data-ttu-id="b200e-129">範例 2-中斷會話與特定電腦的連線</span><span class="sxs-lookup"><span data-stu-id="b200e-129">Example 2 - Disconnect a session from a specific computer</span></span>

<span data-ttu-id="b200e-130">此命令中斷 Server12 電腦上 ITTask PSSession 與目前工作階段的連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-130">This command disconnects the ITTask PSSession on the Server12 computer from the current session.</span></span>
<span data-ttu-id="b200e-131">ITTask 工作階段是在目前的工作階段中建立，並連線 Server12 電腦。</span><span class="sxs-lookup"><span data-stu-id="b200e-131">The ITTask session was created in the current session and connects to the Server12 computer.</span></span> <span data-ttu-id="b200e-132">此命令會使用 `Get-PSSession` Cmdlet 來取得會話，並使用 `Disconnect-PSSession` Cmdlet 將它中斷連接。</span><span class="sxs-lookup"><span data-stu-id="b200e-132">The command uses the `Get-PSSession` cmdlet to get the session and the `Disconnect-PSSession` cmdlet to disconnect it.</span></span>

```
PS> Get-PSSession -ComputerName Server12 -Name ITTask |
  Disconnect-PSSession -OutputBufferingMode Drop -IdleTimeoutSec 86400
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  ITTask          Server12        Disconnected  ITTasks               None
```

<span data-ttu-id="b200e-133">此 `Disconnect-PSSession` 命令會使用 **OutputBufferingMode** 參數，將輸出模式設定為 **Drop** 。</span><span class="sxs-lookup"><span data-stu-id="b200e-133">The `Disconnect-PSSession` command uses the **OutputBufferingMode** parameter to set the output mode to **Drop**.</span></span> <span data-ttu-id="b200e-134">此設定確保即使工作階段輸出緩衝區已滿，工作階段中執行的指令碼仍可繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b200e-134">This setting ensures that the script that is running in the session can continue to run even if the session output buffer is full.</span></span> <span data-ttu-id="b200e-135">因為指令碼會將其輸出寫入檔案共用上的報表，所以其他輸出即使遺失也不會受影響。</span><span class="sxs-lookup"><span data-stu-id="b200e-135">Because the script writes its output to a report on a file share, other output can be lost without consequence.</span></span>

<span data-ttu-id="b200e-136">此命令也使用 **IdleTimeoutSec** 參數將工作階段的閒置逾時延長為 24 小時。</span><span class="sxs-lookup"><span data-stu-id="b200e-136">The command also uses the **IdleTimeoutSec** parameter to extend the idle timeout of the session to 24 hours.</span></span> <span data-ttu-id="b200e-137">此設定可以讓此系統管理員或其他系統管理員有時間重新連線到工作階段，確認指令碼有執行和進行疑難排解 (如果需要)。</span><span class="sxs-lookup"><span data-stu-id="b200e-137">This setting allows time for this administrator or other administrators to reconnect to the session to verify that the script ran and troubleshoot if needed.</span></span>

### <span data-ttu-id="b200e-138">範例 3-在多部電腦上使用多個 Pssession</span><span class="sxs-lookup"><span data-stu-id="b200e-138">Example 3 - Using multiple PSSessions on multiple computers</span></span>

<span data-ttu-id="b200e-139">這一系列的命令會示範如何 `Disconnect-PSSession` 在企業案例中使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b200e-139">This series of commands shows how the `Disconnect-PSSession` cmdlet might be used in an enterprise scenario.</span></span> <span data-ttu-id="b200e-140">在本例中，新的技術人員在遠端電腦的工作階段中啟動一個指令碼，執行時產生了問題。</span><span class="sxs-lookup"><span data-stu-id="b200e-140">In this case, a new technician starts a script in a session on a remote computer and runs into a problem.</span></span> <span data-ttu-id="b200e-141">技術人員中斷工作階段的連線，讓較有經驗的管理員可以連線到工作階段並解決問題。</span><span class="sxs-lookup"><span data-stu-id="b200e-141">The technician disconnects from the session so that a more experienced manager can connect to the session and resolve the problem.</span></span>

```
PS> $s = New-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
PS> Invoke-Command $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Get-PSSession -Name ITTask -ComputerName Srv1 | Disconnect-PSSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1 ITTask           Srv1            Disconnected  Microsoft.PowerShell          None

PS> Get-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None
 2 ITTask          Srv2            Opened        Microsoft.PowerShell     Available
 3 ITTask          Srv30           Opened        Microsoft.PowerShell     Available

PS> Get-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None

PS> $s = Connect-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
PS> Invoke-Command -Session $s {dir $home\Scripts\PatchStatusOutput.ps1}
PS> Invoke-Command -Session $s {mkdir $home\Scripts\PatchStatusOutput}
PS> Invoke-Command -Session $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Disconnect-PSSession -Session $s
```

<span data-ttu-id="b200e-142">技術人員先在許多遠端電腦上建立工作階段，並且在每個工作階段中執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="b200e-142">The technician begins by creating sessions on several remote computers and running a script in each session.</span></span> <span data-ttu-id="b200e-143">第一個命令會使用 `New-PSSession` Cmdlet，在三部遠端電腦上建立 ITTask 會話。</span><span class="sxs-lookup"><span data-stu-id="b200e-143">The first command uses the `New-PSSession` cmdlet to create the ITTask session on three remote computers.</span></span> <span data-ttu-id="b200e-144">命令會將工作階段儲存於 $s 變數中。</span><span class="sxs-lookup"><span data-stu-id="b200e-144">The command saves the sessions in the $s variable.</span></span> <span data-ttu-id="b200e-145">第二個命令會使用 Cmdlet 的 **FilePath** 參數 `Invoke-Command` ，在 $s 變數的會話中執行腳本。</span><span class="sxs-lookup"><span data-stu-id="b200e-145">The second command uses the **FilePath** parameter of the `Invoke-Command` cmdlet to run a script in the sessions in the $s variable.</span></span>

<span data-ttu-id="b200e-146">在 Srv1 電腦上執行的指令碼產生未預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b200e-146">The script running on the Srv1 computer generates unexpected errors.</span></span> <span data-ttu-id="b200e-147">技術人員連絡他的管理員並要求協助。</span><span class="sxs-lookup"><span data-stu-id="b200e-147">The technician contacts his manager and asks for assistance.</span></span> <span data-ttu-id="b200e-148">管理員會指示技術人員中斷會話的連線，讓他可以進行調查。第二個命令 `Get-PSSession` 會使用 Cmdlet 取得 Srv1 電腦上的 ITTask 會話，並使用 `Disconnect-PSSession` Cmdlet 將它中斷連接。</span><span class="sxs-lookup"><span data-stu-id="b200e-148">The manager directs the technician to disconnect from the session so he can investigate.The second command uses the `Get-PSSession` cmdlet to get the ITTask session on the Srv1 computer and the `Disconnect-PSSession` cmdlet to disconnect it.</span></span> <span data-ttu-id="b200e-149">此命令不會影響其他電腦上的 ITTask 會話。</span><span class="sxs-lookup"><span data-stu-id="b200e-149">This command does not affect the ITTask sessions on the other computers.</span></span>

<span data-ttu-id="b200e-150">第三個命令會使用 `Get-PSSession` Cmdlet 來取得 ITTask 會話。</span><span class="sxs-lookup"><span data-stu-id="b200e-150">The third command uses the `Get-PSSession` cmdlet to get the ITTask sessions.</span></span> <span data-ttu-id="b200e-151">輸出顯示 Srv2 和 Srv30 電腦上的 ITTask 工作階段並未受到中斷連線命令的影響。</span><span class="sxs-lookup"><span data-stu-id="b200e-151">The output shows that the ITTask sessions on the Srv2 and Srv30 computers were not affected by the command to disconnect.</span></span>

<span data-ttu-id="b200e-152">管理員登入家用電腦、連線到他的公司網路、啟動 PowerShell，然後使用 `Get-PSSession` Cmdlet 取得 Srv1 電腦上的 ITTask 會話。</span><span class="sxs-lookup"><span data-stu-id="b200e-152">The manager logs on to his home computer, connects to his corporate network, starts PowerShell, and uses the `Get-PSSession` cmdlet to get the ITTask session on the Srv1 computer.</span></span> <span data-ttu-id="b200e-153">他使用技術人員的認證存取工作階段。</span><span class="sxs-lookup"><span data-stu-id="b200e-153">He uses the credentials of the technician to access the session.</span></span>

<span data-ttu-id="b200e-154">接下來，管理員會使用此 `Connect-PSSession` Cmdlet 來連線到 Srv1 電腦上的 ITTask 會話。</span><span class="sxs-lookup"><span data-stu-id="b200e-154">Next, the manager uses the `Connect-PSSession` cmdlet to connect to the ITTask session on the Srv1 computer.</span></span> <span data-ttu-id="b200e-155">命令會將工作階段儲存於 $s 變數中。</span><span class="sxs-lookup"><span data-stu-id="b200e-155">The command saves the session in the $s variable.</span></span>

<span data-ttu-id="b200e-156">管理員會使用 `Invoke-Command` Cmdlet，在變數中的會話中執行一些診斷命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="b200e-156">The manager uses the `Invoke-Command` cmdlet to run some diagnostic commands in the session in the `$s` variable.</span></span> <span data-ttu-id="b200e-157">他找出指令碼失敗的原因是因為它找不到必要的目錄。</span><span class="sxs-lookup"><span data-stu-id="b200e-157">He recognizes that the script failed because it did not find a required directory.</span></span>
<span data-ttu-id="b200e-158">管理員會使用函式 `MkDir` 來建立目錄，然後重新開機 `Get-PatchStatus.ps1` 腳本並中斷會話的連線。管理員將他的結果回報給技術人員，建議他重新連接到會話以完成工作，並要求他將命令新增至 `Get-PatchStatus.ps1` 腳本，以建立必要的目錄（如果不存在的話）。</span><span class="sxs-lookup"><span data-stu-id="b200e-158">The manager uses the `MkDir` function to create the directory, and then he restarts the `Get-PatchStatus.ps1` script and disconnects from the session.The manager reports his findings to the technician, suggests that he reconnect to the session to complete the tasks, and asks him to add a command to the `Get-PatchStatus.ps1` script that creates the required directory if it does not exist.</span></span>

### <span data-ttu-id="b200e-159">範例 4-變更 PSSession 的超時值</span><span class="sxs-lookup"><span data-stu-id="b200e-159">Example 4 - Change the timeout value for a PSSession</span></span>

<span data-ttu-id="b200e-160">此範例示範如何更正工作階段的 **IdleTimeout** 屬性值讓它可以中斷連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-160">This example shows how to correct the value of the **IdleTimeout** property of a session so that it can be disconnected.</span></span>

<span data-ttu-id="b200e-161">工作階段的閒置逾時屬性對中斷連線的工作階段非常重要，因為它會決定中斷連線的工作階段在被刪除之前會維持多久的時間。</span><span class="sxs-lookup"><span data-stu-id="b200e-161">The idle timeout property of a session is critical to disconnected sessions, because it determines how long a disconnected session is maintained before it is deleted.</span></span> <span data-ttu-id="b200e-162">您可以在建立工作階段以及中斷工作階段的連線時，設定閒置逾時選項。</span><span class="sxs-lookup"><span data-stu-id="b200e-162">You can set the idle timeout option when you create a session and when you disconnect it.</span></span> <span data-ttu-id="b200e-163">會話閒置時間的預設值是在 `$PSSessionOption` 本機電腦上的喜好設定變數，以及遠端電腦上的會話設定中設定。</span><span class="sxs-lookup"><span data-stu-id="b200e-163">The default values for the idle timeout of a session are set in the `$PSSessionOption` preference variable on the local computer and in the session configuration on the remote computer.</span></span> <span data-ttu-id="b200e-164">為工作階段設定的值優先於工作階段設定中的值，但是工作階段值不能超過工作階段設定中所設定的配額，例如 **MaxIdleTimeoutMs** 值。</span><span class="sxs-lookup"><span data-stu-id="b200e-164">Values set for the session take precedence over values set in the session configuration, but session values cannot exceed quotas set in the session configuration, such as the **MaxIdleTimeoutMs** value.</span></span>

```
PS> $Timeout = New-PSSessionOption -IdleTimeout 172800000
PS> $s = New-PSSession -Computer Server01 -Name ITTask -SessionOption $Timeout
PS> Disconnect-PSSession -Session $s
Disconnect-PSSession : The session ITTask cannot be disconnected because the specified
idle timeout value 172800(seconds) is either greater than the server maximum allowed
43200 (seconds) or less that the minimum allowed60(seconds).  Choose an idle time out
value that is within the allowed range and try again.

PS> Invoke-Command -ComputerName Server01 {Get-PSSessionConfiguration Microsoft.PowerShell} |
 Format-List -Property *

Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/microsoft.powershell
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
SecurityDescriptorSddl        : O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GXGW;;;WD)
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 2147483647
Uri                           : http://schemas.microsoft.com/powershell/microsoft.powershell
SDKVersion                    : 2
Name                          : microsoft.powershell
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
ParentResourceUri             : http://schemas.microsoft.com/powershell/microsoft.powershell
Enabled                       : true
MaxShells                     : 25
MaxShellsPerUser              : 25
Permission                    : BUILTIN\Administrators AccessAllowed
PSComputerName                : localhost
RunspaceId                    : aea84310-6dbf-4c21-90ac-13980039925a
PSShowComputerName            : True


PS> $s.Runspace.ConnectionInfo
ConnectionUri                     : http://Server01/wsman
ComputerName                      : Server01
Scheme                            : http
Port                              : 80
AppName                           : /wsman
Credential                        :
ShellUri                          : http://schemas.microsoft.com/powershell/Microsoft.PowerShell
AuthenticationMechanism           : Default
CertificateThumbprint             :
MaximumConnectionRedirectionCount : 5
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
UseCompression                    : True
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
NoEncryption                      : False
UseUTF16                          : False
OutputBufferingMode               : Drop
IncludePortInSPN                  : False
Culture                           : en-US
UICulture                         : en-US
OpenTimeout                       : 180000
CancelTimeout                     : 60000
OperationTimeout                  : 180000
IdleTimeout                       : 172800000

PS> Disconnect-PSSession $s -IdleTimeoutSec 43200
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Disconnected  Microsoft.PowerShell          None

PS> $s.Runspace.ConnectionInfo.IdleTimeout
43200000
```

<span data-ttu-id="b200e-165">第一個命令會使用 `New-PSSessionOption` Cmdlet 來建立會話選項物件。</span><span class="sxs-lookup"><span data-stu-id="b200e-165">The first command uses the `New-PSSessionOption` cmdlet to create a session option object.</span></span> <span data-ttu-id="b200e-166">它使用 **IdleTimeout** 參數設定 48 小時 (172800000 毫秒) 的閒置逾時。</span><span class="sxs-lookup"><span data-stu-id="b200e-166">It uses the **IdleTimeout** parameter to set an idle timeout of 48 hours (172800000 milliseconds).</span></span> <span data-ttu-id="b200e-167">命令會將工作階段選項物件儲存在 $Timeout 變數中。</span><span class="sxs-lookup"><span data-stu-id="b200e-167">The command saves the session option object in the $Timeout variable.</span></span>

<span data-ttu-id="b200e-168">第二個命令會使用 `New-PSSession` Cmdlet 在 Server01 電腦上建立 ITTask 會話。</span><span class="sxs-lookup"><span data-stu-id="b200e-168">The second command uses the `New-PSSession` cmdlet to create the ITTask session on the Server01 computer.</span></span> <span data-ttu-id="b200e-169">命令會將工作階段儲存在 $s 變數中。</span><span class="sxs-lookup"><span data-stu-id="b200e-169">The command save the session in the $s variable.</span></span> <span data-ttu-id="b200e-170">**SessionOption** 參數的值是在 $Timeout 變數中的 48 小時閒置逾時。</span><span class="sxs-lookup"><span data-stu-id="b200e-170">The value of the **SessionOption** parameter is the 48-hour idle timeout in the $Timeout variable.</span></span>

<span data-ttu-id="b200e-171">第三個命令中斷 $s 變數中 ITTask 工作階段的連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-171">The third command disconnects the ITTask session in the $s variable.</span></span> <span data-ttu-id="b200e-172">此命令會失敗，因為工作階段的閒置逾時值超過工作階段設定中的 **MaxIdleTimeoutMs** 配額。</span><span class="sxs-lookup"><span data-stu-id="b200e-172">The command fails because the idle timeout value of the session exceeds the **MaxIdleTimeoutMs** quota in the session configuration.</span></span> <span data-ttu-id="b200e-173">因為工作階段要在中斷連線之後，才會使用到閒置逾時，所以工作階段在使用中時，可能不會偵測到此違規。</span><span class="sxs-lookup"><span data-stu-id="b200e-173">Because the idle timeout is not used until the session is disconnected, this violation can go undetected while the session is in use.</span></span>

<span data-ttu-id="b200e-174">第四個命令會使用 `Invoke-Command` `Get-PSSessionConfiguration` 指令程式在 Server01 電腦上執行 Microsoft PowerShell 會話設定的命令。</span><span class="sxs-lookup"><span data-stu-id="b200e-174">The fourth command uses the `Invoke-Command` cmdlet to run a `Get-PSSessionConfiguration` command for the Microsoft.PowerShell session configuration on the Server01 computer.</span></span> <span data-ttu-id="b200e-175">此命令會使用 `Format-List` Cmdlet，在清單中顯示會話設定的所有屬性。輸出顯示 **MaxIdleTimeoutMS** 屬性（可為使用會話設定的會話建立最大容許的 **IdleTimeout** 值）是43200000毫秒 (12 小時) 。</span><span class="sxs-lookup"><span data-stu-id="b200e-175">The command uses the `Format-List` cmdlet to display all properties of the session configuration in a list.The output shows that the **MaxIdleTimeoutMS** property, which establishes the maximum permitted **IdleTimeout** value for sessions that use the session configuration, is 43200000 milliseconds (12 hours).</span></span>

<span data-ttu-id="b200e-176">第五個命令取得 $s 變數中工作階段的工作階段選項值。</span><span class="sxs-lookup"><span data-stu-id="b200e-176">The fifth command gets the session option values of the session in the $s variable.</span></span> <span data-ttu-id="b200e-177">許多會話選項的值是會話之 [ **運行** 時] 屬性的 [ **ConnectionInfo** ] 屬性的屬性。輸出顯示會話的 **IdleTimeout** 屬性值為172800000毫秒 (48 小時) ，這違反會話設定中12小時的 **MaxIdleTimeoutMs** 配額。若要解決此衝突，您可以使用 **ConfigurationName** 參數來選取不同的會話設定，或使用 **IdleTimeout** 參數來減少會話的閒置時間。</span><span class="sxs-lookup"><span data-stu-id="b200e-177">The values of many session options are properties of the **ConnectionInfo** property of the **Runspace** property of the session.The output shows that the value of the **IdleTimeout** property of the session is 172800000 milliseconds (48 hours), which violates the **MaxIdleTimeoutMs** quota of 12 hours in the session configuration.To resolve this conflict, you can use the **ConfigurationName** parameter to select a different session configuration or use the **IdleTimeout** parameter to reduce the idle timeout of the session.</span></span>

<span data-ttu-id="b200e-178">第六個命令中斷工作階段的連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-178">The sixth command disconnects the session.</span></span> <span data-ttu-id="b200e-179">它使用 **IdleTimeoutSec** 參數設定最大 12 小時的閒置逾時。</span><span class="sxs-lookup"><span data-stu-id="b200e-179">It uses the **IdleTimeoutSec** parameter to set the idle timeout to the 12-hour maximum.</span></span>

<span data-ttu-id="b200e-180">第七個命令取得中斷連線工作階段的 **IdleTimeout** 屬性值，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="b200e-180">The seventh command gets the value of the **IdleTimeout** property of the disconnected session, which is measured in milliseconds.</span></span> <span data-ttu-id="b200e-181">輸出確認命令成功。</span><span class="sxs-lookup"><span data-stu-id="b200e-181">The output confirms that the command was successful.</span></span>

## <span data-ttu-id="b200e-182">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b200e-182">PARAMETERS</span></span>

### <span data-ttu-id="b200e-183">-Id</span><span class="sxs-lookup"><span data-stu-id="b200e-183">-Id</span></span>

<span data-ttu-id="b200e-184">中斷具指定工作階段識別碼的工作階段連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-184">Disconnects from sessions with the specified session ID.</span></span> <span data-ttu-id="b200e-185">輸入一或多個識別碼 (以逗號分隔)，或使用範圍運算子 (..) 來指定某個範圍的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b200e-185">Type one or more IDs (separated by commas), or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="b200e-186">若要取得會話的識別碼，請使用 `Get-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b200e-186">To get the ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="b200e-187">執行個體識別碼儲存在工作階段的 **ID** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="b200e-187">The instance ID is stored in the **ID** property of the session.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b200e-188">-IdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="b200e-188">-IdleTimeoutSec</span></span>

<span data-ttu-id="b200e-189">變更中斷連線 PSSession 的閒置逾時值。</span><span class="sxs-lookup"><span data-stu-id="b200e-189">Changes the idle timeout value of the disconnected PSSession.</span></span> <span data-ttu-id="b200e-190">輸入以秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="b200e-190">Enter a value in seconds.</span></span> <span data-ttu-id="b200e-191">最小值為 60 (1 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="b200e-191">The minimum value is 60 (1 minute).</span></span>

<span data-ttu-id="b200e-192">閒置逾時決定中斷連線的 PSSession 在遠端電腦上維持的時間長度。</span><span class="sxs-lookup"><span data-stu-id="b200e-192">The idle timeout determines how long the disconnected PSSession is maintained on the remote computer.</span></span> <span data-ttu-id="b200e-193">當逾時過期時，就會刪除 PSSession。</span><span class="sxs-lookup"><span data-stu-id="b200e-193">When the timeout expires, the PSSession is deleted.</span></span>

<span data-ttu-id="b200e-194">中斷連線的 PSSession 一旦中斷連線，便被視為閒置，即使命令仍然在中斷連線的工作階段中執行也是如此。</span><span class="sxs-lookup"><span data-stu-id="b200e-194">Disconnected PSSessions are considered to be idle from the moment that they are disconnected, even if commands are running in the disconnected session.</span></span>

<span data-ttu-id="b200e-195">工作階段的閒置逾時預設值由工作階段設定的 **IdleTimeoutMs** 屬性所設定。</span><span class="sxs-lookup"><span data-stu-id="b200e-195">The default value for the idle timeout of a session is set by the value of the **IdleTimeoutMs** property of the session configuration.</span></span> <span data-ttu-id="b200e-196">預設值為 7200000 毫秒 (2 小時)。</span><span class="sxs-lookup"><span data-stu-id="b200e-196">The default value is 7200000 milliseconds (2 hours).</span></span>

<span data-ttu-id="b200e-197">此參數的值會優先於 $PSSessionOption 喜好設定變數的 **IdleTimeout** 屬性，以及工作階段設定中的預設閒置逾時值。</span><span class="sxs-lookup"><span data-stu-id="b200e-197">The value of this parameter takes precedence over the value of the **IdleTimeout** property of the $PSSessionOption preference variable and the default idle timeout value in the session configuration.</span></span> <span data-ttu-id="b200e-198">不過，這個值不能超過工作階段設定的 **MaxIdleTimeoutMs** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="b200e-198">However, this value cannot exceed the value of the **MaxIdleTimeoutMs** property of the session configuration.</span></span> <span data-ttu-id="b200e-199">**MaxIdleTimeoutMs** 的預設值為 12 小時 (43200000 毫秒)。</span><span class="sxs-lookup"><span data-stu-id="b200e-199">The default value of **MaxIdleTimeoutMs** is 12 hours (43200000 milliseconds).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b200e-200">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="b200e-200">-InstanceId</span></span>

<span data-ttu-id="b200e-201">中斷具指定執行個體識別碼的工作階段連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-201">Disconnects from sessions with the specified instance IDs.</span></span>

<span data-ttu-id="b200e-202">執行個體識別碼是 GUID，可唯一識別本機或遠端電腦上的某個階段作業。</span><span class="sxs-lookup"><span data-stu-id="b200e-202">The instance ID is a GUID that uniquely identifies a session on a local or remote computer.</span></span> <span data-ttu-id="b200e-203">執行個體識別碼是唯一的，甚至可跨多部電腦上的多個工作階段。</span><span class="sxs-lookup"><span data-stu-id="b200e-203">The instance ID is unique, even across multiple sessions on multiple computers.</span></span>

<span data-ttu-id="b200e-204">若要取得會話的實例識別碼，請使用 `Get-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b200e-204">To get the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="b200e-205">實例識別碼儲存在會話的 **InstanceID** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="b200e-205">The instance ID is stored in the **InstanceID** property of the session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b200e-206">-Name</span><span class="sxs-lookup"><span data-stu-id="b200e-206">-Name</span></span>

<span data-ttu-id="b200e-207">中斷具指定易記名稱的工作階段連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-207">Disconnects from sessions with the specified friendly names.</span></span> <span data-ttu-id="b200e-208">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b200e-208">Wildcards are permitted.</span></span>

<span data-ttu-id="b200e-209">若要取得會話的易記名稱，請使用 `Get-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b200e-209">To get the friendly name of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="b200e-210">好記名稱儲存在工作階段的 **Name** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="b200e-210">The friendly name is stored in the **Name** property of the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="b200e-211">-Session</span><span class="sxs-lookup"><span data-stu-id="b200e-211">-Session</span></span>

<span data-ttu-id="b200e-212">中斷指定 PSSessions 的連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-212">Disconnects from the specified PSSessions.</span></span> <span data-ttu-id="b200e-213">輸入 PSSession 物件，例如 Cmdlet 所傳回的物件 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="b200e-213">Enter PSSession objects, such as those that the `New-PSSession` cmdlet returns.</span></span> <span data-ttu-id="b200e-214">您也可以使用管線將 PSSession 物件傳送至 `Disconnect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="b200e-214">You can also pipe a PSSession object to `Disconnect-PSSession`.</span></span>

<span data-ttu-id="b200e-215">此 `Get-PSSession` Cmdlet 可以取得在遠端電腦上終止的所有 pssession，包括已中斷連線的 pssession，以及連線至其他電腦上其他會話的 pssession。</span><span class="sxs-lookup"><span data-stu-id="b200e-215">The `Get-PSSession` cmdlet can get all PSSessions that terminate at a remote computer, including PSSessions that are disconnected and PSSessions that are connected to other sessions on other computers.</span></span> <span data-ttu-id="b200e-216">`Disconnect-PSSession` 只中斷連接到目前會話的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="b200e-216">`Disconnect-PSSession` disconnects only PSSession that are connected to the current session.</span></span> <span data-ttu-id="b200e-217">如果您以管線將其他 Pssession 傳送至 `Disconnect-PSSession` ，則 `Disconnect-PSSession` 命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="b200e-217">If you pipe other PSSessions to `Disconnect-PSSession`, the `Disconnect-PSSession` command fails.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b200e-218">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b200e-218">-ThrottleLimit</span></span>

<span data-ttu-id="b200e-219">設定命令的節流限制 `Disconnect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="b200e-219">Sets the throttle limit for the `Disconnect-PSSession` command.</span></span>

<span data-ttu-id="b200e-220">節流限制是可建立以執行此命令的最大同時連線數。</span><span class="sxs-lookup"><span data-stu-id="b200e-220">The throttle limit is the maximum number of concurrent connections that can be established to run this command.</span></span> <span data-ttu-id="b200e-221">若省略此參數，或輸入值為 0，則會使用預設值 32。</span><span class="sxs-lookup"><span data-stu-id="b200e-221">If you omit this parameter or enter a value of 0, the default value, 32, is used.</span></span>

<span data-ttu-id="b200e-222">節流限制僅適用於目前命令，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="b200e-222">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b200e-223">-OutputBufferingMode</span><span class="sxs-lookup"><span data-stu-id="b200e-223">-OutputBufferingMode</span></span>

<span data-ttu-id="b200e-224">決定當輸出緩衝區已滿時，如何管理中斷連線工作階段中的命令輸出。</span><span class="sxs-lookup"><span data-stu-id="b200e-224">Determines how command output is managed in the disconnected session when the output buffer is full.</span></span> <span data-ttu-id="b200e-225">預設值為 **Block** 。</span><span class="sxs-lookup"><span data-stu-id="b200e-225">The default value is **Block**.</span></span>

<span data-ttu-id="b200e-226">如果中斷連線工作階段中的命令傳回輸出，且輸出緩衝區填滿，此參數的值可有效決定此命令是否要在工作階段中斷連線的情況下繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b200e-226">If the command in the disconnected session is returning output and the output buffer fills, the value of this parameter effectively determines whether the command continues to run while the session is disconnected.</span></span> <span data-ttu-id="b200e-227">**Block** 值會暫停命令，直到工作階段重新連線為止。</span><span class="sxs-lookup"><span data-stu-id="b200e-227">A value of **Block** suspends the command until the session is reconnected.</span></span> <span data-ttu-id="b200e-228">**Drop** 值允許命令完成，但可能會遺失資料。</span><span class="sxs-lookup"><span data-stu-id="b200e-228">A value of **Drop** allows the command to complete, although data might be lost.</span></span> <span data-ttu-id="b200e-229">使用 **Drop** 值時，請將命令輸出重新導向至磁碟上的檔案。</span><span class="sxs-lookup"><span data-stu-id="b200e-229">When using the **Drop** value, redirect the command output to a file on disk.</span></span>

<span data-ttu-id="b200e-230">有效值為：</span><span class="sxs-lookup"><span data-stu-id="b200e-230">Valid values are:</span></span>

- <span data-ttu-id="b200e-231">**Block** ：當輸出緩衝區已滿時，會暫停執行直到清除緩衝區為止。</span><span class="sxs-lookup"><span data-stu-id="b200e-231">**Block** : When the output buffer is full, execution is suspended until the buffer is clear.</span></span>
- <span data-ttu-id="b200e-232">**Drop** ：當輸出緩衝區已滿時，會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b200e-232">**Drop** : When the output buffer is full, execution continues.</span></span> <span data-ttu-id="b200e-233">儲存新的輸出時，會捨棄最舊的輸出。</span><span class="sxs-lookup"><span data-stu-id="b200e-233">As new output is saved, the oldest output is discarded.</span></span>
- <span data-ttu-id="b200e-234">**None** ：未指定輸出緩衝模式。</span><span class="sxs-lookup"><span data-stu-id="b200e-234">**None** : No output buffering mode is specified.</span></span> <span data-ttu-id="b200e-235">對於中斷連線的工作階段，則使用工作階段設定的 **OutputBufferingMode** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="b200e-235">The value of the **OutputBufferingMode** property of the session configuration is used for the disconnected session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Block
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b200e-236">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b200e-236">-Confirm</span></span>

<span data-ttu-id="b200e-237">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="b200e-237">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b200e-238">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b200e-238">-WhatIf</span></span>

<span data-ttu-id="b200e-239">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="b200e-239">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b200e-240">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="b200e-240">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b200e-241">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b200e-241">CommonParameters</span></span>

<span data-ttu-id="b200e-242">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b200e-242">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b200e-243">如需詳細資訊，請參閱 [about_CommonParameters](./About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b200e-243">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b200e-244">輸入</span><span class="sxs-lookup"><span data-stu-id="b200e-244">INPUTS</span></span>

### <span data-ttu-id="b200e-245">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="b200e-245">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="b200e-246">您可以使用管線將會話傳送至 `Disconnect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="b200e-246">You can pipe a session to `Disconnect-PSSession`.</span></span>

## <span data-ttu-id="b200e-247">輸出</span><span class="sxs-lookup"><span data-stu-id="b200e-247">OUTPUTS</span></span>

### <span data-ttu-id="b200e-248">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="b200e-248">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="b200e-249">`Disconnect-PSSession` 傳回代表其中斷連接之會話的物件。</span><span class="sxs-lookup"><span data-stu-id="b200e-249">`Disconnect-PSSession` returns an object that represents the session that it disconnected.</span></span>

## <span data-ttu-id="b200e-250">注意</span><span class="sxs-lookup"><span data-stu-id="b200e-250">NOTES</span></span>

<span data-ttu-id="b200e-251">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="b200e-251">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="b200e-252">`Disconnect-PSSession`只有當本機和遠端電腦執行 PowerShell 3.0 或更新版本時，此 Cmdlet 才會運作。</span><span class="sxs-lookup"><span data-stu-id="b200e-252">The `Disconnect-PSSession` cmdlet works only when the local and remote computers are running PowerShell 3.0 or later.</span></span>
- <span data-ttu-id="b200e-253">如果您在已 `Disconnect-PSSession` 中斷連線的會話上使用此 Cmdlet，此命令對會話沒有任何作用，且不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b200e-253">If you use the `Disconnect-PSSession` cmdlet on a disconnected session, the command has no effect on the session and it does not generate errors.</span></span>
- <span data-ttu-id="b200e-254">具有互動式安全性權杖 (使用 **EnableNetworkAccess** 參數所建立) 且已中斷連線的回送工作階段只能從當初建立該工作階段的電腦重新連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-254">Disconnected loopback sessions with interactive security tokens (those created with the **EnableNetworkAccess** parameter) can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="b200e-255">此限制可防止電腦遭受惡意存取。</span><span class="sxs-lookup"><span data-stu-id="b200e-255">This restriction protects the computer from malicious access.</span></span>
- <span data-ttu-id="b200e-256">當您中斷連線 PSSession 時，工作階段狀態為 **Disconnected** 且可用性為 **None** 。</span><span class="sxs-lookup"><span data-stu-id="b200e-256">When you disconnect a PSSession, the session state is **Disconnected** and the availability is **None**.</span></span>

  <span data-ttu-id="b200e-257">**State** 屬性的值是相對於目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="b200e-257">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="b200e-258">因此，值為 **Disconnected** 表示 PSSession 並未連線目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="b200e-258">Therefore, a value of **Disconnected** means that the PSSession is not connected to the current session.</span></span> <span data-ttu-id="b200e-259">不過，它並不表示 PSSession 中斷所有工作階段的連線。</span><span class="sxs-lookup"><span data-stu-id="b200e-259">However, it does not mean that the PSSession is disconnected from all sessions.</span></span> <span data-ttu-id="b200e-260">它可能連線不同的工作階段。</span><span class="sxs-lookup"><span data-stu-id="b200e-260">It might be connected to a different session.</span></span> <span data-ttu-id="b200e-261">若要判斷是否可以連線或重新連線工作階段，請使用 **Availability** 屬性。</span><span class="sxs-lookup"><span data-stu-id="b200e-261">To determine whether you can connect or reconnect to the session, use the **Availability** property.</span></span>

  <span data-ttu-id="b200e-262">**Availability** 值為 **None** 表示您可以連線工作階段。</span><span class="sxs-lookup"><span data-stu-id="b200e-262">An **Availability** value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="b200e-263">值為 **Busy** 表示您無法連線 PSSession，因為它已連線另一個工作階段。</span><span class="sxs-lookup"><span data-stu-id="b200e-263">A value of **Busy** indicates that you cannot connect to the PSSession because it is connected to another session.</span></span>

  <span data-ttu-id="b200e-264">如需會話的 **State** 屬性值的詳細資訊，請參閱 [ runspacestate 列舉](/dotnet/api/system.management.automation.runspaces.runspacestate)。</span><span class="sxs-lookup"><span data-stu-id="b200e-264">For more information about the values of the **State** property of sessions, see [RunspaceState Enumeration](/dotnet/api/system.management.automation.runspaces.runspacestate).</span></span>

  <span data-ttu-id="b200e-265">如需會話的 **Availability** 屬性值的詳細資訊，請參閱 [RunspaceAvailability 列舉](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。</span><span class="sxs-lookup"><span data-stu-id="b200e-265">For more information about the values of the **Availability** property of sessions, see [RunspaceAvailability Enumeration](/dotnet/api/system.management.automation.runspaces.runspaceavailability).</span></span>

## <span data-ttu-id="b200e-266">相關連結</span><span class="sxs-lookup"><span data-stu-id="b200e-266">RELATED LINKS</span></span>

[<span data-ttu-id="b200e-267">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="b200e-267">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="b200e-268">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="b200e-268">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="b200e-269">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="b200e-269">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="b200e-270">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="b200e-270">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="b200e-271">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b200e-271">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="b200e-272">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="b200e-272">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="b200e-273">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="b200e-273">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="b200e-274">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="b200e-274">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="b200e-275">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="b200e-275">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="b200e-276">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="b200e-276">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="b200e-277">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="b200e-277">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="b200e-278">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="b200e-278">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="b200e-279">about_Remote</span><span class="sxs-lookup"><span data-stu-id="b200e-279">about_Remote</span></span>](About/about_Remote.md)

[<span data-ttu-id="b200e-280">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="b200e-280">about_Remote_Disconnected_Sessions</span></span>](About/about_Remote_Disconnected_Sessions.md)
