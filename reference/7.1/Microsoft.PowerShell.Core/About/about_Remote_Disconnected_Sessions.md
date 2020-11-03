---
description: 說明如何中斷連線並重新連線至 PowerShell 會話 (PSSession) 。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: 68903485ce92a692453bfba4aa5097dd062437f9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207739"
---
# <a name="about-remote-disconnected-sessions"></a><span data-ttu-id="8e9f3-104">關於遠端中斷連線的會話</span><span class="sxs-lookup"><span data-stu-id="8e9f3-104">About Remote Disconnected Sessions</span></span>

## <a name="short-description"></a><span data-ttu-id="8e9f3-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="8e9f3-105">Short description</span></span>

<span data-ttu-id="8e9f3-106">說明如何中斷連線並重新連線至 PowerShell 會話 (PSSession) 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-106">Explains how to disconnect and reconnect to a PowerShell Session (PSSession).</span></span>

## <a name="long-description"></a><span data-ttu-id="8e9f3-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="8e9f3-107">Long description</span></span>

<span data-ttu-id="8e9f3-108">從 PowerShell 3.0 開始，您可以從 PSSession 中斷連線，然後重新連接到同一部電腦或不同電腦上的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-108">Beginning in PowerShell 3.0, you can disconnect from a PSSession and reconnect to the PSSession on the same computer or a different computer.</span></span> <span data-ttu-id="8e9f3-109">會話狀態會保持不變，而 PSSession 中的命令會在會話中斷連接時繼續執行。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-109">The session state is maintained and commands in the PSSession continue to run while the session is disconnected.</span></span>

<span data-ttu-id="8e9f3-110">只有當遠端電腦執行 PowerShell 3.0 或更新版本時，才能使用 [已中斷連線的會話] 功能。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-110">The Disconnected Sessions feature is only available when the remote computer is running PowerShell 3.0 or a later version.</span></span>

<span data-ttu-id="8e9f3-111">[已中斷連線的會話] 功能可讓您關閉建立 PSSession 的會話，甚至關閉 PowerShell 並關閉電腦，而不會中斷 PSSession 中執行的命令。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-111">The Disconnected Sessions feature allows you to close the session in which a PSSession was created, and even close PowerShell, and shut down the computer, without disrupting commands running in the PSSession.</span></span> <span data-ttu-id="8e9f3-112">已中斷連線的會話適用于執行需要花費很長時間才能完成的命令，並提供 IT 專業人員所需的時間和裝置彈性。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-112">Disconnected sessions are useful for running commands that take an extended time to complete, and provides the time and device flexibility that IT professionals require.</span></span>

<span data-ttu-id="8e9f3-113">您無法從使用 Cmdlet 啟動的互動式會話中斷連線 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-113">You can't disconnect from an interactive session that is started by using the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="8e9f3-114">您可以使用已中斷連線的會話來管理因電腦或網路中斷而意外中斷連線的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-114">You can use disconnected sessions to manage PSSessions that were disconnected unintentionally as the result of a computer or network outage.</span></span>

<span data-ttu-id="8e9f3-115">在實際使用中，已中斷連線的會話功能可讓您開始解決問題、將注意力轉換成較高優先順序的問題，然後繼續在解決方案上工作，甚至是在不同的電腦上的其他位置。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-115">In real-world use, the Disconnected Sessions feature allows you to begin solving a problem, turn your attention to a higher priority issue, and then resume work on the solution, even on a different computer in a different location.</span></span>

## <a name="disconnected-session-cmdlets"></a><span data-ttu-id="8e9f3-116">已中斷連線的會話 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8e9f3-116">Disconnected session cmdlets</span></span>

<span data-ttu-id="8e9f3-117">下列 Cmdlet 支援已中斷連線的會話功能：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-117">The following cmdlets support the Disconnected Sessions feature:</span></span>

- <span data-ttu-id="8e9f3-118">`Connect-PSSession`：連接到中斷連線的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-118">`Connect-PSSession`: Connects to a disconnected PSSession.</span></span>
- <span data-ttu-id="8e9f3-119">`Disconnect-PSSession`：中斷 PSSession 的連接。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-119">`Disconnect-PSSession`: Disconnects a PSSession.</span></span>
- <span data-ttu-id="8e9f3-120">`Get-PSSession`：取得本機電腦或遠端電腦上的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-120">`Get-PSSession`: Gets PSSessions on the local computer or on remote computers.</span></span>
- <span data-ttu-id="8e9f3-121">`Receive-PSSession`：取得在已中斷連線的會話中執行的命令結果。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-121">`Receive-PSSession`: Gets the results of commands that ran in disconnected sessions.</span></span>
- <span data-ttu-id="8e9f3-122">`Invoke-Command`： **InDisconnectedSession** 參數會建立 PSSession 並立即中斷連接。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-122">`Invoke-Command`: **InDisconnectedSession** parameter creates a PSSession and disconnects immediately.</span></span>

## <a name="how-the-disconnected-sessions-feature-works"></a><span data-ttu-id="8e9f3-123">中斷連線的會話功能如何運作</span><span class="sxs-lookup"><span data-stu-id="8e9f3-123">How the Disconnected Sessions feature works</span></span>

<span data-ttu-id="8e9f3-124">從 PowerShell 3.0 開始，Pssession 與建立它們的會話無關。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-124">Beginning in PowerShell 3.0, PSSessions are independent of the sessions in which they're created.</span></span> <span data-ttu-id="8e9f3-125">作用中的 Pssession 會在連線的遠端電腦或 **伺服器端** 上維持，即使建立 PSSession 的會話已關閉，且原始電腦已關閉或中斷與網路的連線。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-125">Active PSSessions are maintained on the remote computer or **server-side** of the connection, even if the session in which the PSSession was created is closed and the originating computer is shut down or disconnected from the network.</span></span>

<span data-ttu-id="8e9f3-126">在 PowerShell 2.0 中，從遠端電腦中斷與原始會話或建立它的會話的連線時，會刪除該 PSSession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-126">In PowerShell 2.0, the PSSession is deleted from the remote computer when it's disconnected from the originating session or the session in which it was created ends.</span></span>

<span data-ttu-id="8e9f3-127">當您中斷連線 PSSession 時，PSSession 會保持作用中狀態，並在遠端電腦上進行維護。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-127">When you disconnect a PSSession, the PSSession remains active and is maintained on the remote computer.</span></span> <span data-ttu-id="8e9f3-128">會話狀態 **會從 [執行中]** 變更為 [已 **中斷** 連線]。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-128">The session state changes from **Running** to **Disconnected** .</span></span> <span data-ttu-id="8e9f3-129">您可以從目前的會話或相同電腦上的不同會話，或從不同的電腦重新連接到中斷連線的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-129">You can reconnect to a disconnected PSSession from the current session or from a different session on the same computer, or from a different computer.</span></span> <span data-ttu-id="8e9f3-130">維護會話的遠端電腦必須正在執行，且必須連接到網路。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-130">The remote computer that maintains the session must be running and be connected to the network.</span></span>

<span data-ttu-id="8e9f3-131">中斷連線的 PSSession 中的命令會在遠端電腦上繼續執行，直到命令完成或輸出緩衝區填滿為止。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-131">Commands in a disconnected PSSession continue to run uninterrupted on the remote computer until the command completes or the output buffer fills.</span></span> <span data-ttu-id="8e9f3-132">若要防止完整輸出緩衝區暫停命令，請使用 **OutputBufferingMode** `Disconnect-PSSession` 、 `New-PSSessionOption` 或 Cmdlet 的 OutputBufferingMode 參數 `New-PSTransportOption` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-132">To prevent a full output buffer from suspending a command, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="8e9f3-133">中斷連線的會話會維持在遠端電腦上的中斷線上狀態。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-133">Disconnected sessions are maintained in the disconnected state on the remote computer.</span></span> <span data-ttu-id="8e9f3-134">您可以使用這些方法來重新連接，直到您刪除 PSSession 為止（例如使用 `Remove-PSSession` Cmdlet），或直到 PSSession 的閒置超時時間過期為止。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-134">They're available for you to reconnect, until you delete the PSSession, such as by using the `Remove-PSSession` cmdlet, or until the idle timeout of the PSSession expires.</span></span> <span data-ttu-id="8e9f3-135">您可以使用、或 Cmdlet 的 **IdleTimeoutSec** 或 **IdleTimeout** 參數，來調整 PSSession 的閒置時間 `Disconnect-PSSession` `New-PSSessionOption` `New-PSTransportOption` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-135">You can adjust the idle timeout of a PSSession by using the **IdleTimeoutSec** or **IdleTimeout** parameters of the `Disconnect-PSSession`, `New-PSSessionOption`, or `New-PSTransportOption` cmdlets.</span></span>

<span data-ttu-id="8e9f3-136">另一位使用者可以連接到您建立的 Pssession，但只有在可以提供用來建立會話的認證時，或是使用會話設定的 `RunAs` 認證。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-136">Another user can connect to PSSessions that you created, but only if they can provide the credentials that were used to create the session, or use the `RunAs` credentials of the session configuration.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="8e9f3-137">如何取得 Pssession</span><span class="sxs-lookup"><span data-stu-id="8e9f3-137">How to get PSSessions</span></span>

<span data-ttu-id="8e9f3-138">從 PowerShell 3.0 開始，此 `Get-PSSession` Cmdlet 會在本機電腦和遠端電腦上取得 pssession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-138">Beginning in PowerShell 3.0, the `Get-PSSession` cmdlet gets PSSessions on the local computer and remote computers.</span></span> <span data-ttu-id="8e9f3-139">它也可以取得在目前會話中建立的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-139">It can also get PSSessions that were created in the current session.</span></span>

<span data-ttu-id="8e9f3-140">若要在本機電腦或遠端電腦上取得 Pssession，請使用 **ComputerName** 或 **ConnectionUri** 參數。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-140">To get PSSessions on the local computer or remote computers, use the **ComputerName** or **ConnectionUri** parameters.</span></span> <span data-ttu-id="8e9f3-141">如果沒有參數，則會 `Get-PSSession` 取得在本機會話中建立的 PSSession （不論它們終止的位置為何）。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-141">Without parameters, `Get-PSSession` gets PSSession that were created in the local session, regardless of where they terminate.</span></span>

<span data-ttu-id="8e9f3-142">取得 Pssession 時，請記得在維護的電腦（也就是遠端或 **伺服器端** 電腦）上尋找它們。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-142">When getting PSSessions, remember to look for them on the computer on which they're maintained, that is, the remote or **server-side** computer.</span></span>

<span data-ttu-id="8e9f3-143">例如，如果您建立 Server01 電腦的 PSSession，請從 Server01 電腦取得該會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-143">For example, if you create a PSSession to the Server01 computer, get the session from the Server01 computer.</span></span> <span data-ttu-id="8e9f3-144">如果您從另一部電腦建立 PSSession 至本機電腦，請從本機電腦取得會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-144">If you create a PSSession from another computer to the local computer, get the session from the local computer.</span></span>

<span data-ttu-id="8e9f3-145">下列命令順序顯示如何 `Get-PSSession` 運作。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-145">The following command sequence shows how `Get-PSSession` works.</span></span>

<span data-ttu-id="8e9f3-146">第一個命令會建立 Server01 電腦的會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-146">The first command creates a session to the Server01 computer.</span></span> <span data-ttu-id="8e9f3-147">會話位於 Server01 電腦上。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-147">The session resides on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="8e9f3-148">若要取得會話，請使用值為 Server01 的 **ComputerName** 參數 `Get-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-148">To get the session, use the **ComputerName** parameter of `Get-PSSession` with a value of Server01.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

<span data-ttu-id="8e9f3-149">如果 **ComputerName** 參數的值 `Get-PSSession` 是 localhost，會 `Get-PSSession` 取得在上終止的 pssession，並且在本機電腦上進行維護。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-149">If the value of the **ComputerName** parameter of `Get-PSSession` is localhost, `Get-PSSession` gets PSSessions that terminate at and are maintained on the local computer.</span></span> <span data-ttu-id="8e9f3-150">即使是在本機電腦上啟動，也不會在 Server01 電腦上取得 Pssession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-150">It doesn't get PSSessions on the Server01 computer, even if they were started on the local computer.</span></span>

```powershell
Get-PSSession -ComputerName localhost
```

<span data-ttu-id="8e9f3-151">若要取得在目前會話中建立的會話，請使用 `Get-PSSession` 不含參數的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-151">To get sessions that were created in the current session, use the `Get-PSSession` cmdlet without parameters.</span></span> <span data-ttu-id="8e9f3-152">在此範例中， `Get-PSSession` 會取得在目前會話中建立並連接到 Server01 電腦的 PSSession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-152">In this example, `Get-PSSession` gets the PSSession that was created in the current session and connects to the Server01 computer.</span></span>

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a><span data-ttu-id="8e9f3-153">如何中斷會話的連線</span><span class="sxs-lookup"><span data-stu-id="8e9f3-153">How to disconnect sessions</span></span>

<span data-ttu-id="8e9f3-154">若要中斷連接 PSSession，請使用 `Disconnect-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-154">To disconnect a PSSession, use the `Disconnect-PSSession` cmdlet.</span></span> <span data-ttu-id="8e9f3-155">若要識別 PSSession，請使用 **Session** 參數，或從 `New-PSSession` 或 Cmdlet 到的管線 `Get-PSSession` `Disconnect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-155">To identify the PSSession, use the **Session** parameter, or pipeline a PSSession from the `New-PSSession` or `Get-PSSession` cmdlets to `Disconnect-PSSession`.</span></span>

<span data-ttu-id="8e9f3-156">下列命令會中斷連接 PSSession 與 Server01 電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-156">The following command disconnects the PSSession to the Server01 computer.</span></span>
<span data-ttu-id="8e9f3-157">請注意， **State** 屬性的值已 **中斷** 連線，而且 **可用性** 為 **None** 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-157">Notice that the value of the **State** property is **Disconnected** and the **Availability** is **None** .</span></span>

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="8e9f3-158">若要建立已中斷連線的會話，請使用 Cmdlet 的 **InDisconnectedSession** 參數 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-158">To create a disconnected session, use the **InDisconnectedSession** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="8e9f3-159">它會建立會話、啟動命令，然後立即中斷連線，然後命令才會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-159">It creates a session, starts the command, and disconnects immediately, before the command can return any output.</span></span>

<span data-ttu-id="8e9f3-160">下列命令會 `Get-WinEvent` 在 Server02 遠端電腦上的已中斷連線會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-160">The following command runs a `Get-WinEvent` command in a disconnected session on the Server02 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a><span data-ttu-id="8e9f3-161">如何連接到已中斷連線的會話</span><span class="sxs-lookup"><span data-stu-id="8e9f3-161">How to connect to disconnected sessions</span></span>

<span data-ttu-id="8e9f3-162">您可以從建立 PSSession 的會話，或從本機電腦或其他電腦上的其他會話，連接到任何可用的中斷連線 PSSession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-162">You can connect to any available disconnected PSSession from the session in which you created the PSSession or from other sessions on the local computer or other computers.</span></span>

<span data-ttu-id="8e9f3-163">您可以建立 PSSession、在 PSSession 中執行命令、中斷連接 PSSession、關閉 PowerShell，然後關閉電腦。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-163">You can create a PSSession, run commands in the PSSession, disconnect from the PSSession, close PowerShell, and shut down the computer.</span></span> <span data-ttu-id="8e9f3-164">數小時之後，您可以開啟不同的電腦、取得 PSSession、連接到該電腦，並取得在 PSSession 中斷連接時在 PSSession 中執行的命令結果。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-164">Hours later, you can open a different computer, get the PSSession, connect to it, and get the results of commands that ran in the PSSession while it was disconnected.</span></span> <span data-ttu-id="8e9f3-165">然後，您可以在會話中執行更多命令。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-165">Then you can run more commands in the session.</span></span>

<span data-ttu-id="8e9f3-166">若要連接中斷連線的 PSSession，請使用 `Connect-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-166">To connect a disconnected PSSession, use the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="8e9f3-167">您可以使用 **ComputerName** 或 **ConnectionUri** 參數來識別 pssession，或從管線到的 `Get-PSSession` 管線 `Connect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-167">Use the **ComputerName** or **ConnectionUri** parameters to identify the PSSession, or pipeline a PSSession from `Get-PSSession` to `Connect-PSSession`.</span></span>

<span data-ttu-id="8e9f3-168">下列命令會取得 Server02 電腦上的會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-168">The following command gets the sessions on the Server02 computer.</span></span> <span data-ttu-id="8e9f3-169">輸出包含兩個已中斷連線的會話，兩者皆可使用。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-169">The output includes two disconnected sessions, both of which are available.</span></span>

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

<span data-ttu-id="8e9f3-170">下列命令會連接到 Session2。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-170">The following command connects to Session2.</span></span> <span data-ttu-id="8e9f3-171">PSSession 現在已開放且可供使用。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-171">The PSSession is now open and available.</span></span>

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a><span data-ttu-id="8e9f3-172">如何取得結果</span><span class="sxs-lookup"><span data-stu-id="8e9f3-172">How to get the results</span></span>

<span data-ttu-id="8e9f3-173">若要取得在中斷連線的 PSSession 中執行之命令的結果，請使用 `Receive-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-173">To get the results of commands that ran in a disconnected PSSession, use the `Receive-PSSession` cmdlet.</span></span>

<span data-ttu-id="8e9f3-174">您可以使用 `Receive-PSSession` 而不是使用 `Connect-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-174">You can use `Receive-PSSession` rather than using the `Connect-PSSession` cmdlet.</span></span> <span data-ttu-id="8e9f3-175">如果會話已重新連接，則 `Receive-PSSession` 會取得會話中斷連線時執行的命令結果。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-175">If the session is already reconnected, `Receive-PSSession` gets the results of commands that ran when the session was disconnected.</span></span> <span data-ttu-id="8e9f3-176">如果 PSSession 仍中斷連接，則會 `Receive-PSSession` 連接到它，然後取得在中斷連接時執行的命令結果。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-176">If the PSSession is still disconnected, `Receive-PSSession` connects to it and then gets the results of commands that ran while it was disconnected.</span></span>

<span data-ttu-id="8e9f3-177">`Receive-PSSession` 可以在作業 (中，以非同步方式傳回結果) 或以同步方式) 主機程式 (。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-177">`Receive-PSSession` can return the results in a job (asynchronously) or to the host program (synchronously).</span></span> <span data-ttu-id="8e9f3-178">使用 **OutTarget** 參數來選取 **作業** 或 **主機** 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-178">Use the **OutTarget** parameter to select **Job** or **Host** .</span></span> <span data-ttu-id="8e9f3-179">預設值為 **Host** 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-179">The default value is **Host** .</span></span> <span data-ttu-id="8e9f3-180">但是，如果所接收的命令是在目前會話中做為 **工作** 啟動，則預設會以 **作業** 形式傳回。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-180">However, if the command that's being received was started in the current session as a **Job** , it's returned as a **Job** by default.</span></span>

<span data-ttu-id="8e9f3-181">下列命令會使用指令 `Receive-PSSession` 程式來連線到 Server02 電腦上的 PSSession，並取得 `Get-WinEvent` 在 Session3 會話中執行之命令的結果。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-181">The following command uses the `Receive-PSSession` cmdlet to connect to the PSSession on the Server02 computer and get the results of the `Get-WinEvent` command that ran in the Session3 session.</span></span> <span data-ttu-id="8e9f3-182">此命令會使用 **OutTarget** 參數來取得 **作業** 中的結果。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-182">The command uses the **OutTarget** parameter to get the results in a **Job** .</span></span>

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

<span data-ttu-id="8e9f3-183">若要取得作業的結果，請使用 `Receive-Job` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-183">To get the job's results, use the `Receive-Job` cmdlet.</span></span>

```powershell
Get-Job | Receive-Job -Keep
```

```Output
ProviderName: PowerShell

TimeCreated             Id LevelDisplayName Message     PSComputerName
-----------             -- ---------------- -------     --------------
5/14/2012 7:26:04 PM   400 Information      Engine stat Server02
5/14/2012 7:26:03 PM   600 Information      Provider "W Server02
5/14/2012 7:26:03 PM   600 Information      Provider "C Server02
5/14/2012 7:26:03 PM   600 Information      Provider "V Server02
```

## <a name="state-and-availability-properties"></a><span data-ttu-id="8e9f3-184">狀態和可用性屬性</span><span class="sxs-lookup"><span data-stu-id="8e9f3-184">State and Availability properties</span></span>

<span data-ttu-id="8e9f3-185">中斷連線之 PSSession 的 **狀態** 和 **可用性** 屬性會告訴您會話是否可供您重新連接。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-185">The **State** and **Availability** properties of a disconnected PSSession tell you whether the session is available for you to reconnect to it.</span></span>

<span data-ttu-id="8e9f3-186">當 PSSession 連接到目前的會話時，它的狀態會 **開啟** ，而且 **可以使用** 它的可用性。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-186">When a PSSession is connected to the current session, its state is **Opened** and its availability is **Available** .</span></span> <span data-ttu-id="8e9f3-187">當您中斷與 PSSession 的連接時，PSSession 狀態會 **中斷** 連線，而且其可用性為 **None** 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-187">When you disconnect from the PSSession, the PSSession state is **Disconnected** and its availability is **None** .</span></span>

<span data-ttu-id="8e9f3-188">**State** 屬性的值是相對於目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-188">The value of the **State** property is relative to the current session.</span></span> <span data-ttu-id="8e9f3-189">值為「已 **中斷** 連線」表示 PSSession 未連接到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-189">A value of **Disconnected** means that the PSSession isn't connected to the current session.</span></span> <span data-ttu-id="8e9f3-190">但是，這並不表示 PSSession 與所有會話中斷連接。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-190">But, it doesn't mean that the PSSession is disconnected from all sessions.</span></span> <span data-ttu-id="8e9f3-191">它可能連線不同的工作階段。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-191">It might be connected to a different session.</span></span>

<span data-ttu-id="8e9f3-192">若要判斷您是否可以連接或重新連線到 PSSession，請使用 **Availability** 屬性。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-192">To determine whether you can connect or reconnect to the PSSession, use the **Availability** property.</span></span> <span data-ttu-id="8e9f3-193">[ **無** ] 值表示您可以連線至會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-193">A value of **None** indicates that you can connect to the session.</span></span> <span data-ttu-id="8e9f3-194">「 **忙碌** 」值表示您無法連接到 PSSession，因為它已連接到另一個會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-194">A value of **Busy** indicates that you can't connect to the PSSession because it's connected to another session.</span></span>

<span data-ttu-id="8e9f3-195">下列範例會在同一部電腦上的兩個 PowerShell 會話中執行。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-195">The following example is run in two PowerShell sessions on the same computer.</span></span>
<span data-ttu-id="8e9f3-196">請注意，當 PSSession 中斷連接並重新連線時，每個會話中 **狀態** 和 **可用性** 屬性的變更值。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-196">Note the changing values of the **State** and **Availability** properties in each session as the PSSession is disconnected and reconnected.</span></span>

```powershell
# Session 1
New-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30 -Name Test | Disconnect-PSSession
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Connect-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
3 Test    Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```Output
# Idle Timeout
```

<span data-ttu-id="8e9f3-197">中斷連線的會話會一直保留在遠端電腦上，直到您將它們刪除為止，例如使用 `Remove-PSSession` Cmdlet 或它們超時。PSSession 的 **IdleTimeout** 屬性會決定已中斷連線的會話在被刪除之前的維護時間。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-197">Disconnected sessions are maintained on the remote computer until you delete them, such as by using the `Remove-PSSession` cmdlet, or they time out. The **IdleTimeout** property of a PSSession determines how long a disconnected session is maintained before it's deleted.</span></span>

<span data-ttu-id="8e9f3-198">當 **心跳執行緒** 沒有收到回應時，pssession 就會閒置。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-198">PSSessions are idle when the **heartbeat thread** receives no response.</span></span>
<span data-ttu-id="8e9f3-199">中斷會話的連線可讓它閒置並啟動 **IdleTimeout** 時鐘，即使命令仍在已中斷連線的會話中執行也是如此。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-199">Disconnecting a session makes it idle and starts the **IdleTimeout** clock, even if commands are still running in the disconnected session.</span></span> <span data-ttu-id="8e9f3-200">PowerShell 會將已中斷連線的會話視為作用中，但為閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-200">PowerShell considers disconnected sessions to be active, but idle.</span></span>

<span data-ttu-id="8e9f3-201">建立和中斷會話的連線時，請確認 PSSession 中的閒置超時時間夠長，足以維持會話的需求，但前提是它在遠端電腦上耗用不必要的資源。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-201">When creating and disconnecting sessions, verify that the idle timeout in the PSSession is long enough to maintain the session for your needs, but not so long that it consumes unnecessary resources on the remote computer.</span></span>

<span data-ttu-id="8e9f3-202">會話設定的 **IdleTimeoutMs** 屬性會決定使用會話設定之會話的預設閒置超時時間。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-202">The **IdleTimeoutMs** property of the session configuration determines the default idle timeout of sessions that use the session configuration.</span></span> <span data-ttu-id="8e9f3-203">您可以覆寫預設值，但您使用的值不能超過會話設定的 **MaxIdleTimeoutMs** 屬性。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-203">You can override the default value, but the value that you use can't exceed the **MaxIdleTimeoutMs** property of the session configuration.</span></span>

<span data-ttu-id="8e9f3-204">若要尋找會話設定的 **IdleTimeoutMs** 和 **MaxIdleTimeoutMs** 值的值，請使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-204">To find the value of the **IdleTimeoutMs** and **MaxIdleTimeoutMs** values of a session configuration, use the following command format.</span></span>

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

<span data-ttu-id="8e9f3-205">您可以覆寫會話設定中的預設值，並在建立 PSSession 以及中斷連接時，設定 PSSession 的閒置時間。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-205">You can override the default value in the session configuration and set the idle timeout of a PSSession when you create a PSSession and when you disconnect.</span></span>

<span data-ttu-id="8e9f3-206">如果您是遠端電腦上 Administrators 群組的成員，您可以建立並變更會話設定的 **IdleTimeoutMs** 和 **MaxIdleTimeoutMs** 屬性。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-206">If you're a member of the Administrators group on the remote computer, you can create and change the **IdleTimeoutMs** and **MaxIdleTimeoutMs** properties of session configurations.</span></span>

## <a name="idle-timeout-values"></a><span data-ttu-id="8e9f3-207">閒置超時值</span><span class="sxs-lookup"><span data-stu-id="8e9f3-207">Idle timeout values</span></span>

<span data-ttu-id="8e9f3-208">會話設定和會話選項的閒置超時值是以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-208">The idle timeout value of session configurations and session options is in milliseconds.</span></span> <span data-ttu-id="8e9f3-209">會話和會話設定選項的閒置超時值（以秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-209">The idle timeout value of sessions and session configuration options is in seconds.</span></span>

<span data-ttu-id="8e9f3-210">您可以在建立 PSSession (`New-PSSession` 、 `Invoke-Command`) 和 () 中斷連接時，設定 pssession 的閒置時間 `Disconnect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-210">You can set the idle timeout of a PSSession when you create the PSSession (`New-PSSession`, `Invoke-Command`) and when you disconnect from it (`Disconnect-PSSession`).</span></span> <span data-ttu-id="8e9f3-211">但是，當您連接到 **IdleTimeout** PSSession (`Connect-PSSession`) 或)  (取得結果時，無法變更 IdleTimeout 值 `Receive-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-211">However, you can't change the **IdleTimeout** value when you connect to the PSSession (`Connect-PSSession`) or get results (`Receive-PSSession`).</span></span>

<span data-ttu-id="8e9f3-212">`Connect-PSSession`和 `Receive-PSSession` Cmdlet 具有 **SessionOption** 參數，該參數會採用 **SessionOption** 物件，例如 Cmdlet 所傳回的物件 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-212">The `Connect-PSSession` and `Receive-PSSession` cmdlets have a **SessionOption** parameter that takes a **SessionOption** object, such as one returned by the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="8e9f3-213">**SessionOption** 物件中的 **idletimeout** 值和喜好設定變數中的 **idletimeout** 值 `$PSSessionOption` 不會變更或命令中 PSSession 的 **idletimeout** 值 `Connect-PSSession` `Receive-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-213">The **IdleTimeout** value in **SessionOption** object and the **IdleTimeout** value in the `$PSSessionOption` preference variable don't change the value of the **IdleTimeout** of the PSSession in a `Connect-PSSession` or `Receive-PSSession` command.</span></span>

<span data-ttu-id="8e9f3-214">若要建立具有特定閒置超時值的 PSSession，請建立 `$PSSessionOption` 喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-214">To create a PSSession with a particular idle timeout value, create a `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="8e9f3-215">將 [ **IdleTimeout** ] 屬性的值設定為所需的值， (以毫秒為單位) 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-215">Set the value of the **IdleTimeout** property to the desired value (in milliseconds).</span></span>

<span data-ttu-id="8e9f3-216">當您建立 Pssession 時，變數中的值 `$PSSessionOption` 會優先于會話設定中的值。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-216">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="8e9f3-217">例如，下列命令會將閒置的時間設定為48小時：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-217">For example, the following command sets an idle timeout of 48 hours:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

<span data-ttu-id="8e9f3-218">若要建立具有特定閒置超時值的 PSSession，請使用 Cmdlet 的 **IdleTimeoutMSec** 參數 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-218">To create a PSSession with a particular idle timeout value, use the **IdleTimeoutMSec** parameter of the `New-PSSessionOption` cmdlet.</span></span> <span data-ttu-id="8e9f3-219">然後，在或 Cmdlet 的 **SessionOption** 參數值中使用 session 選項 `New-PSSession` `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-219">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="8e9f3-220">建立會話時所設定的值會優先于 `$PSSessionOption` 喜好設定變數和會話設定中所設定的值。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-220">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="8e9f3-221">例如：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-221">For example:</span></span>

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

<span data-ttu-id="8e9f3-222">若要在中斷連接時變更 PSSession 的閒置時間，請使用 Cmdlet 的 **IdleTimeoutSec** 參數 `Disconnect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-222">To change the idle timeout of a PSSession when disconnecting, use the **IdleTimeoutSec** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="8e9f3-223">例如：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-223">For example:</span></span>

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

<span data-ttu-id="8e9f3-224">若要建立具有特定閒置 timeout 和最大閒置超時時間的會話設定，請使用 Cmdlet 的 **IdleTimeoutSec** 和 **MaxIdleTimeoutSec** 參數 `New-PSTransportOption` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-224">To create a session configuration with a particular idle timeout and maximum idle timeout, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="8e9f3-225">然後，在的 **TransportOption** 參數值中使用 transport 選項 `Register-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-225">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="8e9f3-226">例如：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-226">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="8e9f3-227">若要變更會話設定的預設閒置 timeout 和最大閒置時間，請使用 Cmdlet 的 **IdleTimeoutSec** 和 **MaxIdleTimeoutSec** 參數 `New-PSTransportOption` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-227">To change the default idle timeout and maximum idle timeout of a session configuration, use the **IdleTimeoutSec** and **MaxIdleTimeoutSec** parameters of the `New-PSTransportOption` cmdlet.</span></span> <span data-ttu-id="8e9f3-228">然後，在的 **TransportOption** 參數值中使用 transport 選項 `Set-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-228">Then, use the transport option in the value of the **TransportOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="8e9f3-229">例如：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-229">For example:</span></span>

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a><span data-ttu-id="8e9f3-230">輸出緩衝模式</span><span class="sxs-lookup"><span data-stu-id="8e9f3-230">Output buffering mode</span></span>

<span data-ttu-id="8e9f3-231">PSSession 的輸出緩衝處理模式會決定當 PSSession 的輸出緩衝區已滿時，如何管理命令輸出。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-231">The output buffering mode of a PSSession determines how command output is managed when the output buffer of the PSSession is full.</span></span>

<span data-ttu-id="8e9f3-232">在中斷連線的會話中，輸出緩衝處理模式會在會話中斷連線時，有效地判斷命令是否繼續執行。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-232">In a disconnected session, the output buffering mode effectively determines whether the command continues to run while the session is disconnected.</span></span>

<span data-ttu-id="8e9f3-233">有效的值如下：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-233">The valid values as follows:</span></span>

- <span data-ttu-id="8e9f3-234">**封鎖** 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-234">**Block** .</span></span> <span data-ttu-id="8e9f3-235">當輸出緩衝區已滿時，會暫停執行直到清除緩衝區為止。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-235">When the output buffer is full, execution is suspended until the buffer is clear.</span></span> <span data-ttu-id="8e9f3-236">預設值。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-236">The default value.</span></span>
- <span data-ttu-id="8e9f3-237">**卸除** ：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-237">**Drop** .</span></span> <span data-ttu-id="8e9f3-238">當輸出緩衝區已滿時，會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-238">When the output buffer is full, execution continues.</span></span> <span data-ttu-id="8e9f3-239">當產生新的輸出時，會捨棄最舊的輸出。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-239">As new output is generated, the oldest output is discarded.</span></span>

<span data-ttu-id="8e9f3-240">**區塊** 會保留資料，但可能會中斷命令。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-240">**Block** preserves data, but might interrupt the command.</span></span> <span data-ttu-id="8e9f3-241">**Drop** 值允許命令完成，但可能會遺失資料。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-241">A value of **Drop** allows the command to complete, although data might be lost.</span></span> <span data-ttu-id="8e9f3-242">使用 **Drop** 值時，請將命令輸出重新導向至磁碟上的檔案。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-242">When using the **Drop** value, redirect the command output to a file on disk.</span></span> <span data-ttu-id="8e9f3-243">此值建議用於已中斷連線的會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-243">This value is recommended for disconnected sessions.</span></span>

<span data-ttu-id="8e9f3-244">會話設定的 **OutputBufferingMode** 屬性會決定使用會話設定之會話的預設輸出緩衝處理模式。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-244">The **OutputBufferingMode** property of the session configuration determines the default output buffering mode of sessions that use the session configuration.</span></span>

<span data-ttu-id="8e9f3-245">若要尋找會話設定的 **OutputBufferingMode** 值，您可以使用下列其中一種命令格式：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-245">To find a session configuration's value of the **OutputBufferingMode** , you can use either of the following command formats:</span></span>

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

<span data-ttu-id="8e9f3-246">您可以覆寫會話設定中的預設值，並在您建立 PSSession、中斷連線和重新連線時，設定 PSSession 的輸出緩衝模式。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-246">You can override the default value in the session configuration and set the output buffering mode of a PSSession when you create a PSSession, when you disconnect, and when you reconnect.</span></span>

<span data-ttu-id="8e9f3-247">如果您是遠端電腦上 Administrators 群組的成員，您可以建立及變更會話設定的輸出緩衝處理模式。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-247">If you're a member of the Administrators group on the remote computer, you can create and change the output buffering mode of session configurations.</span></span>

<span data-ttu-id="8e9f3-248">若要使用 **drop** 的輸出緩衝處理模式來建立 PSSession，請建立一個 `$PSSessionOption` 喜好設定變數，其中 **OutputBufferingMode** 屬性的值為 **drop** 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-248">To create a PSSession with an output buffering mode of **Drop** , create a `$PSSessionOption` preference variable in which the value of the **OutputBufferingMode** property is **Drop** .</span></span>

<span data-ttu-id="8e9f3-249">當您建立 Pssession 時，變數中的值 `$PSSessionOption` 會優先于會話設定中的值。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-249">When you create PSSessions, the values in `$PSSessionOption` variable take precedence over the values in the session configuration.</span></span>

<span data-ttu-id="8e9f3-250">例如：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-250">For example:</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

<span data-ttu-id="8e9f3-251">若要使用 **drop** 的輸出緩衝處理模式來建立 PSSession，請使用指令程式的 **OutputBufferingMode** 參數 `New-PSSessionOption` 來建立具有 **drop** 值的會話選項。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-251">To create a PSSession with an output buffering mode of **Drop** , use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop** .</span></span> <span data-ttu-id="8e9f3-252">然後，在或 Cmdlet 的 **SessionOption** 參數值中使用 session 選項 `New-PSSession` `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-252">Then, use the session option in the value of the **SessionOption** parameter of the `New-PSSession` or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="8e9f3-253">建立會話時所設定的值會優先于 `$PSSessionOption` 喜好設定變數和會話設定中所設定的值。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-253">The values set when creating the session take precedence over the values set in the `$PSSessionOption` preference variable and the session configuration.</span></span>

<span data-ttu-id="8e9f3-254">例如：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-254">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

<span data-ttu-id="8e9f3-255">若要在中斷連接時變更 PSSession 的輸出緩衝處理模式，請使用 Cmdlet 的 **OutputBufferingMode** 參數 `Disconnect-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-255">To change the output buffering mode of a PSSession when disconnecting, use the **OutputBufferingMode** parameter of the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="8e9f3-256">例如：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-256">For example:</span></span>

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

<span data-ttu-id="8e9f3-257">若要在重新連接時變更 PSSession 的輸出緩衝處理模式，請使用指令程式的 **OutputBufferingMode** 參數 `New-PSSessionOption` 來建立具有 **Drop** 值的會話選項。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-257">To change the output buffering mode of a PSSession when reconnecting, use the **OutputBufferingMode** parameter of the `New-PSSessionOption` cmdlet to create a session option with a value of **Drop** .</span></span> <span data-ttu-id="8e9f3-258">然後，在或的 **SessionOption** 參數值中使用 session 選項 `Connect-PSSession` `Receive-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-258">Then, use the session option in the value of the **SessionOption** parameter of `Connect-PSSession` or `Receive-PSSession`.</span></span>

<span data-ttu-id="8e9f3-259">例如：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-259">For example:</span></span>

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

<span data-ttu-id="8e9f3-260">若要建立具有預設輸出緩衝處理模式的會話設定 **，請** 使用指令程式的 **OutputBufferingMode** 參數 `New-PSTransportOption` 來建立具有 **drop** 值的傳輸選項物件。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-260">To create a session configuration with a default output buffering mode of **Drop** , use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option object with a value of **Drop** .</span></span> <span data-ttu-id="8e9f3-261">然後，在的 **TransportOption** 參數值中使用 transport 選項 `Register-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-261">Then, use the transport option in the value of the **TransportOption** parameter of `Register-PSSessionConfiguration`.</span></span>

<span data-ttu-id="8e9f3-262">例如：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-262">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

<span data-ttu-id="8e9f3-263">若要變更會話設定的預設輸出緩衝處理模式，請使用 Cmdlet 的 **OutputBufferingMode** 參數 `New-PSTransportOption` 來建立具有 **Drop** 值的傳輸選項。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-263">To change the default output buffering mode of a session configuration, use the **OutputBufferingMode** parameter of the `New-PSTransportOption` cmdlet to create a transport option with a value of **Drop** .</span></span> <span data-ttu-id="8e9f3-264">然後，在的 **SessionOption** 參數值中使用 Transport 選項 `Set-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-264">Then, use the Transport option in the value of the **SessionOption** parameter of `Set-PSSessionConfiguration`.</span></span>

<span data-ttu-id="8e9f3-265">例如：</span><span class="sxs-lookup"><span data-stu-id="8e9f3-265">For example:</span></span>

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a><span data-ttu-id="8e9f3-266">中斷回送會話</span><span class="sxs-lookup"><span data-stu-id="8e9f3-266">Disconnecting loopback sessions</span></span>

<span data-ttu-id="8e9f3-267">回送會話（或本機會話）是在同一部電腦上產生和終止的 Pssession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-267">Loopback sessions, or local sessions, are PSSessions that originate and terminate on the same computer.</span></span> <span data-ttu-id="8e9f3-268">如同其他 Pssession，作用中的回送會話會在本機電腦)  (連接的遠端電腦上維護，因此您可以中斷連線，並重新連線到回送會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-268">Like other PSSessions, active loopback sessions are maintained on the computer on the remote end of the connection (the local computer), so you can disconnect from and reconnect to loopback sessions.</span></span>

<span data-ttu-id="8e9f3-269">根據預設，系統會使用網路安全性權杖來建立回送會話，而不允許在會話中執行命令來存取其他電腦。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-269">By default, loopback sessions are created with a network security token that doesn't permit commands run in the session to access other computers.</span></span> <span data-ttu-id="8e9f3-270">您可以從本機電腦或遠端電腦上的任何會話，重新連接具有網路安全性權杖的回送會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-270">You can reconnect to loopback sessions that have a network security token from any session on the local computer or a remote computer.</span></span>

<span data-ttu-id="8e9f3-271">但是，如果您使用、 **EnableNetworkAccess** 或 Cmdlet 的 EnableNetworkAccess `New-PSSession` 參數 `Enter-PSSession` `Invoke-Command` ，則會使用互動式安全性權杖來建立回送會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-271">However, if you use the **EnableNetworkAccess** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlet, the loopback session is created with an interactive security token.</span></span> <span data-ttu-id="8e9f3-272">互動式權杖可讓您在回送會話中執行的命令，從其他電腦取得資料。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-272">The interactive token enables commands that run in the loopback session to get data from other computers.</span></span>

<span data-ttu-id="8e9f3-273">您可以中斷與互動式權杖的回送會話，然後從相同的會話或相同電腦上的不同會話重新連線至這些會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-273">You can disconnect loopback sessions with interactive tokens and then reconnect to them from the same session or a different session on the same computer.</span></span>
<span data-ttu-id="8e9f3-274">不過，若要防止惡意存取，您只能從其建立所在的電腦，使用互動式權杖重新連接回送會話。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-274">However, to prevent malicious access, you can reconnect to loopback sessions with interactive tokens only from the computer on which they were created.</span></span>

## <a name="waiting-for-jobs-in-disconnected-sessions"></a><span data-ttu-id="8e9f3-275">正在等待已中斷連線的會話中的工作</span><span class="sxs-lookup"><span data-stu-id="8e9f3-275">Waiting for jobs in disconnected sessions</span></span>

<span data-ttu-id="8e9f3-276">此 `Wait-Job` Cmdlet 會等到作業完成，然後再回到命令提示字元或下一個命令。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-276">The `Wait-Job` cmdlet waits until a job completes and then returns to the command prompt or the next command.</span></span> <span data-ttu-id="8e9f3-277">根據預設， `Wait-Job` 如果正在執行工作的會話已中斷連線，則會傳回。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-277">By default, `Wait-Job` returns if the session in which a job is running is disconnected.</span></span> <span data-ttu-id="8e9f3-278">若要指示 `Wait-Job` Cmdlet 在會話重新連線之前等候，請在 [已 **開啟** ] 狀態下，使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-278">To direct the `Wait-Job` cmdlet to wait until the session is reconnected, in the **Opened** state, use the **Force** parameter.</span></span> <span data-ttu-id="8e9f3-279">如需詳細資訊，請參閱 [等候工作](xref:Microsoft.PowerShell.Core.Wait-Job)。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-279">For more information, see [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job).</span></span>

## <a name="robust-sessions-and-unintentional-disconnection"></a><span data-ttu-id="8e9f3-280">健全的會話和不慎中斷連接</span><span class="sxs-lookup"><span data-stu-id="8e9f3-280">Robust sessions and unintentional disconnection</span></span>

<span data-ttu-id="8e9f3-281">PSSession 可能因為電腦失敗或網路中斷而意外中斷連線。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-281">A PSSession might be unintentionally disconnected because of a computer failure or network outage.</span></span> <span data-ttu-id="8e9f3-282">PowerShell 會嘗試復原 PSSession，但其成功與否取決於原因的嚴重性和持續時間。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-282">PowerShell attempts to recover the PSSession, but its success depends upon the severity and duration of the cause.</span></span>

<span data-ttu-id="8e9f3-283">不慎中斷連線的 PSSession 狀態可能已 **中斷** 或關閉，但也可能 **已\*\*\*\*中斷** 連線。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-283">The state of an unintentionally disconnected PSSession might be **Broken** or **Closed** , but it might also be **Disconnected** .</span></span> <span data-ttu-id="8e9f3-284">如果 **狀態** 的值已 **中斷連接** ，您可以使用相同的技術來管理 PSSession，就像是在會話已刻意中斷連線的情況下一樣。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-284">If the value of **State** is **Disconnected** , you can use the same techniques to manage the PSSession as you would if the session were disconnected intentionally.</span></span> <span data-ttu-id="8e9f3-285">例如，您可以使用 `Connect-PSSession` 指令程式重新連線到會話，並使用 `Receive-PSSession` 指令程式取得會話中斷連線時執行的命令結果。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-285">For example, you can use the `Connect-PSSession` cmdlet to reconnect to the session and the `Receive-PSSession` cmdlet to get results of commands that ran while the session was disconnected.</span></span>

<span data-ttu-id="8e9f3-286">如果您關閉 (exit) 在 PSSession 中執行命令時，會在其中建立 PSSession 的會話，則 PowerShell 會在遠端電腦上維持 **中斷連接** 狀態的 pssession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-286">If you close (exit) the session in which a PSSession was created while commands are running in the PSSession, PowerShell maintains the PSSession in the **Disconnected** state on the remote computer.</span></span> <span data-ttu-id="8e9f3-287">如果您關閉 (exit) 已建立 PSSession 的會話，但 PSSession 中沒有執行任何命令，則 PowerShell 不會嘗試維護 PSSession。</span><span class="sxs-lookup"><span data-stu-id="8e9f3-287">If you close (exit) the session in which a PSSession was created, but no commands are running in the PSSession, PowerShell doesn't attempt to maintain the PSSession.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e9f3-288">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e9f3-288">See also</span></span>

[<span data-ttu-id="8e9f3-289">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="8e9f3-289">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="8e9f3-290">about_Remote</span><span class="sxs-lookup"><span data-stu-id="8e9f3-290">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="8e9f3-291">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="8e9f3-291">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="8e9f3-292">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="8e9f3-292">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="8e9f3-293">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="8e9f3-293">about_Session_Configurations</span></span>](about_Session_Configurations.md)

[<span data-ttu-id="8e9f3-294">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="8e9f3-294">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="8e9f3-295">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="8e9f3-295">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="8e9f3-296">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="8e9f3-296">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="8e9f3-297">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="8e9f3-297">Receive-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[<span data-ttu-id="8e9f3-298">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="8e9f3-298">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

