---
description: 包含有關在 PowerShell 中執行遠端命令的問題和解答。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_faq?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_FAQ
ms.openlocfilehash: db3b7b554096c0cee6f13365dd8b2fbacb498282
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207735"
---
# <a name="about-remote-faq"></a><span data-ttu-id="0d769-104">關於遠端常見問題集</span><span class="sxs-lookup"><span data-stu-id="0d769-104">About Remote FAQ</span></span>

## <a name="short-description"></a><span data-ttu-id="0d769-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="0d769-105">Short description</span></span>
<span data-ttu-id="0d769-106">包含有關在 PowerShell 中執行遠端命令的問題和解答。</span><span class="sxs-lookup"><span data-stu-id="0d769-106">Contains questions and answers about running remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="0d769-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="0d769-107">Long description</span></span>

<span data-ttu-id="0d769-108">當您從遠端工作時，您會在一部電腦上的 PowerShell 中輸入命令 (稱為「本機電腦」 ) ，但是命令會在另一部電腦上執行， (稱為「遠端電腦」 ) 。</span><span class="sxs-lookup"><span data-stu-id="0d769-108">When you work remotely, you type commands in PowerShell on one computer (known as the "local computer"), but the commands run on another computer (known as the "remote computer").</span></span> <span data-ttu-id="0d769-109">從遠端工作的體驗應該就像直接在遠端電腦上工作一樣。</span><span class="sxs-lookup"><span data-stu-id="0d769-109">The experience of working remotely should be as much like working directly at the remote computer as possible.</span></span>

<span data-ttu-id="0d769-110">注意：若要使用 PowerShell 遠端處理，必須設定遠端電腦以進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="0d769-110">Note: To use PowerShell remoting, the remote computer must be configured for remoting.</span></span> <span data-ttu-id="0d769-111">如需詳細資訊，請參閱[about_Remote_Requirements](about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d769-111">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

### <a name="must-both-computers-have-powershell-installed"></a><span data-ttu-id="0d769-112">這兩部電腦都必須安裝 PowerShell 嗎？</span><span class="sxs-lookup"><span data-stu-id="0d769-112">Must both computers have PowerShell installed?</span></span>

<span data-ttu-id="0d769-113">是。</span><span class="sxs-lookup"><span data-stu-id="0d769-113">Yes.</span></span> <span data-ttu-id="0d769-114">若要從遠端工作，本機和遠端電腦必須具有 PowerShell、Microsoft .NET Framework，以及管理 (WS-MANAGEMENT) 通訊協定的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="0d769-114">To work remotely, the local and remote computers must have PowerShell, the Microsoft .NET Framework, and the Web Services for Management (WS-Management) protocol.</span></span> <span data-ttu-id="0d769-115">執行特定命令所需的任何檔案和其他資源都必須位於遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="0d769-115">Any files and other resources that are needed to execute a particular command must be on the remote computer.</span></span>

<span data-ttu-id="0d769-116">執行 Windows PowerShell 3.0 的電腦和執行 Windows PowerShell 2.0 的電腦都可以從遠端連線，並執行遠端命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-116">Computers running Windows PowerShell 3.0 and computers running Windows PowerShell 2.0 can connect to each other remotely and run remote commands.</span></span>
<span data-ttu-id="0d769-117">不過，某些功能（例如從會話中斷連線並重新連接）的功能，只有在兩部電腦都執行 Windows PowerShell 3.0 時才會運作。</span><span class="sxs-lookup"><span data-stu-id="0d769-117">However, some features, such as the ability to disconnect from a session and reconnect to it, work only when both computers are running Windows PowerShell 3.0.</span></span>

<span data-ttu-id="0d769-118">您必須具有連線到遠端電腦的許可權、執行 PowerShell 的許可權，以及存取資料存放區的許可權 (例如) 的檔案和資料夾，以及遠端電腦上的登錄。</span><span class="sxs-lookup"><span data-stu-id="0d769-118">You must have permission to connect to the remote computer, permission to run PowerShell, and permission to access data stores (such as files and folders), and the registry on the remote computer.</span></span>

<span data-ttu-id="0d769-119">如需詳細資訊，請參閱[about_Remote_Requirements](about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d769-119">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

### <a name="how-does-remoting-work"></a><span data-ttu-id="0d769-120">遠端處理的運作方式為何？</span><span class="sxs-lookup"><span data-stu-id="0d769-120">How does remoting work?</span></span>

<span data-ttu-id="0d769-121">當您提交遠端命令時，命令會經由網路傳輸至遠端電腦上的 PowerShell 引擎，並在遠端電腦上的 PowerShell 用戶端中執行。</span><span class="sxs-lookup"><span data-stu-id="0d769-121">When you submit a remote command, the command is transmitted across the network to the PowerShell engine on the remote computer, and it runs in the PowerShell client on the remote computer.</span></span> <span data-ttu-id="0d769-122">命令結果會傳送回本機電腦，並顯示在本機電腦上的 PowerShell 會話中。</span><span class="sxs-lookup"><span data-stu-id="0d769-122">The command results are sent back to the local computer and appear in the PowerShell session on the local computer.</span></span>

<span data-ttu-id="0d769-123">為了傳輸命令並接收輸出，PowerShell 會使用 WS-Management 的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="0d769-123">To transmit the commands and receive the output, PowerShell uses the WS-Management protocol.</span></span> <span data-ttu-id="0d769-124">如需 WS-Management 通訊協定的相關資訊，請參閱 Windows 檔中的 [WS-Management 通訊協定](/windows/win32/winrm/ws-management-protocol) 。</span><span class="sxs-lookup"><span data-stu-id="0d769-124">For information about the WS-Management protocol, see [WS-Management Protocol](/windows/win32/winrm/ws-management-protocol) in the Windows documentation.</span></span>

<span data-ttu-id="0d769-125">從 Windows PowerShell 3.0 開始，遠端會話會儲存在遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="0d769-125">Beginning in Windows PowerShell 3.0, remote sessions are stored on the remote computer.</span></span> <span data-ttu-id="0d769-126">這可讓您從會話中斷連線，然後從不同的會話或不同的電腦重新連接，而不會中斷命令或遺失狀態。</span><span class="sxs-lookup"><span data-stu-id="0d769-126">This enables you to disconnect from the session and reconnect from a different session or a different computer without interrupting the commands or losing state.</span></span>

### <a name="is-powershell-remoting-secure"></a><span data-ttu-id="0d769-127">PowerShell 遠端處理是否安全？</span><span class="sxs-lookup"><span data-stu-id="0d769-127">Is PowerShell remoting secure?</span></span>

<span data-ttu-id="0d769-128">當您連線到遠端電腦時，系統會使用本機電腦上的使用者名稱和密碼認證，或您在命令中提供的認證將您登入遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="0d769-128">When you connect to a remote computer, the system uses the username and password credentials on the local computer or the credentials that you supply in the command to log you in to the remote computer.</span></span> <span data-ttu-id="0d769-129">認證和傳輸的其餘部分都會加密。</span><span class="sxs-lookup"><span data-stu-id="0d769-129">The credentials and the rest of the transmission are encrypted.</span></span>

<span data-ttu-id="0d769-130">若要新增額外的保護，您可以將遠端電腦設定為使用安全通訊端層 (SSL) 而非 HTTP 來接聽 Windows 遠端管理 (WinRM) 要求。</span><span class="sxs-lookup"><span data-stu-id="0d769-130">To add additional protection, you can configure the remote computer to use Secure Sockets Layer (SSL) instead of HTTP to listen for Windows Remote Management (WinRM) requests.</span></span> <span data-ttu-id="0d769-131">然後， **UseSSL** `Invoke-Command` `New-PSSession` `Enter-PSSession` 當建立連接時，使用者可以使用、和 Cmdlet 的 UseSSL 參數。</span><span class="sxs-lookup"><span data-stu-id="0d769-131">Then, users can use the **UseSSL** parameter of the `Invoke-Command`, `New-PSSession`, and `Enter-PSSession` cmdlets when establishing a connection.</span></span> <span data-ttu-id="0d769-132">此選項會使用更安全的 HTTPS 通道，而不是 HTTP。</span><span class="sxs-lookup"><span data-stu-id="0d769-132">This option uses the more secure HTTPS channel instead of HTTP.</span></span>

### <a name="do-all-remote-commands-require-powershell-remoting"></a><span data-ttu-id="0d769-133">所有遠端命令都需要 PowerShell 遠端處理嗎？</span><span class="sxs-lookup"><span data-stu-id="0d769-133">Do all remote commands require PowerShell remoting?</span></span>

<span data-ttu-id="0d769-134">否。</span><span class="sxs-lookup"><span data-stu-id="0d769-134">No.</span></span> <span data-ttu-id="0d769-135">有數個 Cmdlet 具有 **ComputerName** 參數，可讓您從遠端電腦取得物件。</span><span class="sxs-lookup"><span data-stu-id="0d769-135">Several cmdlets have a **ComputerName** parameter that lets you get objects from the remote computer.</span></span>

<span data-ttu-id="0d769-136">這些 Cmdlet 不會使用 PowerShell 遠端處理。</span><span class="sxs-lookup"><span data-stu-id="0d769-136">These cmdlets do not use PowerShell remoting.</span></span> <span data-ttu-id="0d769-137">因此，您可以在任何執行 PowerShell 的電腦上使用它們，即使電腦未設定 PowerShell 遠端功能，或電腦不符合 PowerShell 遠端處理的需求。</span><span class="sxs-lookup"><span data-stu-id="0d769-137">So, you can use them on any computer that is running PowerShell, even if the computer is not configured for PowerShell remoting or if the computer does not meet the requirements for PowerShell remoting.</span></span>

<span data-ttu-id="0d769-138">這些 Cmdlet 包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="0d769-138">These cmdlets include the following:</span></span>

- `Get-Process`
- `Get-Service`
- `Get-WinEvent`
- `Get-EventLog`
- `Test-Connection`

<span data-ttu-id="0d769-139">若要尋找具有 **ComputerName** 參數的所有 Cmdlet，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0d769-139">To find all the cmdlets with a **ComputerName** parameter, type:</span></span>

```powershell
Get-Help * -Parameter ComputerName
# or
Get-Command -ParameterName ComputerName
```

<span data-ttu-id="0d769-140">若要判斷特定 Cmdlet 的 **ComputerName** 參數是否需要 PowerShell 遠端處理，請參閱參數描述。</span><span class="sxs-lookup"><span data-stu-id="0d769-140">To determine whether the **ComputerName** parameter of a particular cmdlet requires PowerShell remoting, see the parameter description.</span></span> <span data-ttu-id="0d769-141">若要顯示參數描述，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0d769-141">To display the parameter description, type:</span></span>

```powershell
Get-Help <cmdlet-name> -Parameter ComputerName
```

<span data-ttu-id="0d769-142">例如：</span><span class="sxs-lookup"><span data-stu-id="0d769-142">For example:</span></span>

```powershell
Get-Help Get-Process -Parameter ComputerName
```

<span data-ttu-id="0d769-143">若為所有其他命令，請使用 `Invoke-Command` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d769-143">For all other commands, use the `Invoke-Command` cmdlet.</span></span>

### <a name="how-do-i-run-a-command-on-a-remote-computer"></a><span data-ttu-id="0d769-144">如何? 在遠端電腦上執行命令？</span><span class="sxs-lookup"><span data-stu-id="0d769-144">How do I run a command on a remote computer?</span></span>

<span data-ttu-id="0d769-145">若要在遠端電腦上執行命令，請使用 `Invoke-Command` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d769-145">To run a command on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="0d769-146">以大括弧括住命令 (`{}`) 將它設為腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="0d769-146">Enclose your command in braces (`{}`) to make it a script block.</span></span> <span data-ttu-id="0d769-147">使用的 **ScriptBlock** 參數 `Invoke-Command` 來指定命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-147">Use the **ScriptBlock** parameter of `Invoke-Command` to specify the command.</span></span>

<span data-ttu-id="0d769-148">您可以使用的 **ComputerName** 參數 `Invoke-Command` 來指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="0d769-148">You can use the **ComputerName** parameter of `Invoke-Command` to specify a remote computer.</span></span> <span data-ttu-id="0d769-149">或者，您可以建立遠端電腦的持續連線 (會話) 然後使用的 **session** 參數 `Invoke-Command` 在會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-149">Or, you can create a persistent connection to a remote computer (a session) and then use the **Session** parameter of `Invoke-Command` to run the command in the session.</span></span>

<span data-ttu-id="0d769-150">例如，下列命令會 `Get-Process` 從遠端執行命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-150">For example, the following commands run a `Get-Process` command remotely.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-Process}

#  - OR -

Invoke-Command -Session $s -ScriptBlock {Get-Process}
```

<span data-ttu-id="0d769-151">若要中斷遠端命令，請輸入<kbd>CTRL</kbd> + <kbd>C</kbd>。</span><span class="sxs-lookup"><span data-stu-id="0d769-151">To interrupt a remote command, type <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="0d769-152">中斷要求會傳遞至遠端電腦，並在該處終止遠端命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-152">The interruption request is passed to the remote computer, where it terminates the remote command.</span></span>

<span data-ttu-id="0d769-153">如需遠端命令的詳細資訊，請參閱 about_Remote 以及支援遠端處理之 Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="0d769-153">For more information about remote commands, see about_Remote and the Help topics for the cmdlets that support remoting.</span></span>

### <a name="can-i-just-telnet-into-a-remote-computer"></a><span data-ttu-id="0d769-154">我可以只是 telnet 進入遠端電腦嗎？</span><span class="sxs-lookup"><span data-stu-id="0d769-154">Can I just telnet into a remote computer?</span></span>

<span data-ttu-id="0d769-155">您可以使用此 `Enter-PSSession` Cmdlet 來啟動遠端電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="0d769-155">You can use the `Enter-PSSession` cmdlet to start an interactive session with a remote computer.</span></span>

<span data-ttu-id="0d769-156">在 PowerShell 提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="0d769-156">At the PowerShell prompt, type:</span></span>

```powershell
Enter-PSSession <ComputerName>
```

<span data-ttu-id="0d769-157">命令提示字元會變更，顯示您已連線到遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="0d769-157">The command prompt changes to show that you are connected to the remote computer.</span></span>

```
<ComputerName>\C:>
```

<span data-ttu-id="0d769-158">現在，您輸入的命令會在遠端電腦上執行，就像您直接在遠端電腦上輸入一樣。</span><span class="sxs-lookup"><span data-stu-id="0d769-158">Now, the commands that you type run on the remote computer just as though you typed them directly on the remote computer.</span></span>

<span data-ttu-id="0d769-159">若要結束互動式工作階段，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0d769-159">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="0d769-160">互動式會話是使用 WS-Management 通訊協定的持續性會話。</span><span class="sxs-lookup"><span data-stu-id="0d769-160">An interactive session is a persistent session that uses the WS-Management protocol.</span></span> <span data-ttu-id="0d769-161">這與使用 Telnet 不同，但提供類似的體驗。</span><span class="sxs-lookup"><span data-stu-id="0d769-161">It is not the same as using Telnet, but it provides a similar experience.</span></span>

<span data-ttu-id="0d769-162">如需詳細資訊，請參閱`Enter-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="0d769-162">For more information, see `Enter-PSSession`.</span></span>

### <a name="can-i-create-a-persistent-connection"></a><span data-ttu-id="0d769-163">我可以建立持續性連接嗎？</span><span class="sxs-lookup"><span data-stu-id="0d769-163">Can I create a persistent connection?</span></span>

<span data-ttu-id="0d769-164">是。</span><span class="sxs-lookup"><span data-stu-id="0d769-164">Yes.</span></span> <span data-ttu-id="0d769-165">您可以指定遠端電腦的名稱、NetBIOS 名稱或其 IP 位址，以執行遠端命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-165">You can run remote commands by specifying the name of the remote computer, its NetBIOS name, or its IP address.</span></span> <span data-ttu-id="0d769-166">或者，您可以指定連接至遠端電腦 (PSSession) 的 PowerShell 會話，以執行遠端命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-166">Or, you can run remote commands by specifying a PowerShell session (PSSession) that is connected to the remote computer.</span></span>

<span data-ttu-id="0d769-167">當您使用或的 **ComputerName** 參數 `Invoke-Command` 時 `Enter-PSSession` ，PowerShell 會建立暫時的連接。</span><span class="sxs-lookup"><span data-stu-id="0d769-167">When you use the **ComputerName** parameter of `Invoke-Command` or `Enter-PSSession`, PowerShell establishes a temporary connection.</span></span> <span data-ttu-id="0d769-168">PowerShell 會使用連接來只執行目前的命令，然後關閉連接。</span><span class="sxs-lookup"><span data-stu-id="0d769-168">PowerShell uses the connection to run only the current command, and then it closes the connection.</span></span> <span data-ttu-id="0d769-169">這是一種非常有效率的方法，可執行單一命令或數個不相關的命令，即使在許多遠端電腦上也一樣。</span><span class="sxs-lookup"><span data-stu-id="0d769-169">This is a very efficient method for running a single command or several unrelated commands, even on many remote computers.</span></span>

<span data-ttu-id="0d769-170">當您使用 `New-PSSession` Cmdlet 建立 pssession 時，PowerShell 會為 pssession 建立持續連線。</span><span class="sxs-lookup"><span data-stu-id="0d769-170">When you use the `New-PSSession` cmdlet to create a PSSession, PowerShell establishes a persistent connection for the PSSession.</span></span> <span data-ttu-id="0d769-171">然後，您可以在 PSSession 中執行多個命令，包括共用資料的命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-171">Then, you can run multiple commands in the PSSession, including commands that share data.</span></span>

<span data-ttu-id="0d769-172">一般來說，您會建立 PSSession 來執行一系列共用資料的相關命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-172">Typically, you create a PSSession to run a series of related commands that share data.</span></span> <span data-ttu-id="0d769-173">否則， **ComputerName** 參數所建立的暫時連接就足以滿足大部分的命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-173">Otherwise, the temporary connection created by the **ComputerName** parameter is sufficient for most commands.</span></span>

<span data-ttu-id="0d769-174">如需會話的詳細資訊，請參閱 about_PSSessions。</span><span class="sxs-lookup"><span data-stu-id="0d769-174">For more information about sessions, see about_PSSessions.</span></span>

### <a name="can-i-run-commands-on-more-than-one-computer-at-a-time"></a><span data-ttu-id="0d769-175">我可以一次在一部以上的電腦上執行命令嗎？</span><span class="sxs-lookup"><span data-stu-id="0d769-175">Can I run commands on more than one computer at a time?</span></span>

<span data-ttu-id="0d769-176">是。</span><span class="sxs-lookup"><span data-stu-id="0d769-176">Yes.</span></span> <span data-ttu-id="0d769-177">Cmdlet 的 **ComputerName** 參數 `Invoke-Command` 接受多個電腦名稱稱，而 **Session** 參數則接受多個 pssession。</span><span class="sxs-lookup"><span data-stu-id="0d769-177">The **ComputerName** parameter of the `Invoke-Command` cmdlet accepts multiple computer names, and the **Session** parameter accepts multiple PSSessions.</span></span>

<span data-ttu-id="0d769-178">當您執行 `Invoke-Command` 命令時，PowerShell 會在所有指定的電腦或所有指定的 pssession 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-178">When you run an `Invoke-Command` command, PowerShell runs the commands on all of the specified computers or in all of the specified PSSessions.</span></span>

<span data-ttu-id="0d769-179">PowerShell 可以管理數以百計的並行遠端連線。</span><span class="sxs-lookup"><span data-stu-id="0d769-179">PowerShell can manage hundreds of concurrent remote connections.</span></span> <span data-ttu-id="0d769-180">不過，您可以傳送的遠端命令數目可能會受限於您的電腦資源及其建立和維護多個網路連線的容量。</span><span class="sxs-lookup"><span data-stu-id="0d769-180">However, the number of remote commands that you can send might be limited by the resources of your computer and its capacity to establish and maintain multiple network connections.</span></span>

<span data-ttu-id="0d769-181">如需詳細資訊，請參閱說明主題中的範例 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="0d769-181">For more information, see the example in the `Invoke-Command` Help topic.</span></span>

### <a name="where-are-my-profiles"></a><span data-ttu-id="0d769-182">我的設定檔在哪裡？</span><span class="sxs-lookup"><span data-stu-id="0d769-182">Where are my profiles?</span></span>

<span data-ttu-id="0d769-183">PowerShell 設定檔不會自動在遠端會話中執行，因此設定檔新增的命令不會出現在會話中。</span><span class="sxs-lookup"><span data-stu-id="0d769-183">PowerShell profiles are not run automatically in remote sessions, so the commands that the profile adds are not present in the session.</span></span> <span data-ttu-id="0d769-184">此外，在 `$profile` 遠端會話中不會填入自動變數。</span><span class="sxs-lookup"><span data-stu-id="0d769-184">In addition, the `$profile` automatic variable is not populated in remote sessions.</span></span>

<span data-ttu-id="0d769-185">若要在會話中執行設定檔，請使用 `Invoke-Command` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0d769-185">To run a profile in a session, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="0d769-186">例如，下列命令會從的會話中的本機電腦執行適用設定檔 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="0d769-186">For example, the following command runs the CurrentUserCurrentHost profile from the local computer in the session in `$s`.</span></span>

```
Invoke-Command -Session $s -FilePath $profile
```

<span data-ttu-id="0d769-187">下列命令會從會話中的遠端電腦執行適用設定檔 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="0d769-187">The following command runs the CurrentUserCurrentHost profile from the remote computer in the session in `$s`.</span></span> <span data-ttu-id="0d769-188">因為 `$profile` 未填入變數，所以命令會使用設定檔的明確路徑。</span><span class="sxs-lookup"><span data-stu-id="0d769-188">Because the `$profile` variable is not populated, the command uses the explicit path to the profile.</span></span>

```powershell
Invoke-Command -Session $s {
  . "$home\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

<span data-ttu-id="0d769-189">執行此命令之後，就可以在中使用設定檔新增至會話的命令 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="0d769-189">After running this command, the commands that the profile adds to the session are available in `$s`.</span></span>

<span data-ttu-id="0d769-190">您也可以在會話設定中使用啟動腳本，以在每個使用會話設定的遠端會話中執行設定檔。</span><span class="sxs-lookup"><span data-stu-id="0d769-190">You can also use a startup script in a session configuration to run a profile in every remote session that uses the session configuration.</span></span>

<span data-ttu-id="0d769-191">如需 PowerShell 設定檔的詳細資訊，請參閱 about_Profiles。</span><span class="sxs-lookup"><span data-stu-id="0d769-191">For more information about PowerShell profiles, see about_Profiles.</span></span>
<span data-ttu-id="0d769-192">如需會話設定的詳細資訊，請參閱 `Register-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="0d769-192">For more information about session configurations, see `Register-PSSessionConfiguration`.</span></span>

### <a name="how-does-throttling-work-on-remote-commands"></a><span data-ttu-id="0d769-193">節流在遠端命令上的運作方式為何？</span><span class="sxs-lookup"><span data-stu-id="0d769-193">How does throttling work on remote commands?</span></span>

<span data-ttu-id="0d769-194">為了協助您管理本機電腦上的資源，PowerShell 包含每個命令的節流功能，可讓您限制針對每個命令所建立的並行遠端連線數目。</span><span class="sxs-lookup"><span data-stu-id="0d769-194">To help you manage the resources on your local computer, PowerShell includes a per-command throttling feature that lets you limit the number of concurrent remote connections that are established for each command.</span></span>

<span data-ttu-id="0d769-195">預設值為32同時連線，但您可以使用 Cmdlet 的 **ThrottleLimit** 參數來設定特定命令的自訂節流限制。</span><span class="sxs-lookup"><span data-stu-id="0d769-195">The default is 32 concurrent connections, but you can use the **ThrottleLimit** parameter of the cmdlets to set a custom throttle limit for particular commands.</span></span>

<span data-ttu-id="0d769-196">當您使用節流功能時，請記住它會套用至每個命令，而不是套用至整個會話或電腦。</span><span class="sxs-lookup"><span data-stu-id="0d769-196">When you use the throttling feature, remember that it is applied to each command, not to the entire session or to the computer.</span></span> <span data-ttu-id="0d769-197">如果您在數個會話或 Pssession 中同時執行命令，並行連接數目就是所有會話中並行連接的總和。</span><span class="sxs-lookup"><span data-stu-id="0d769-197">If you are running commands concurrently in several sessions or PSSessions, the number of concurrent connections is the sum of the concurrent connections in all the sessions.</span></span>

<span data-ttu-id="0d769-198">若要使用 **ThrottleLimit** 參數尋找 Cmdlet，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0d769-198">To find cmdlets with a **ThrottleLimit** parameter, type:</span></span>

```
Get-Help * -Parameter ThrottleLimit
-or-
Get-Command -ParameterName ThrottleLimit
```

### <a name="is-the-output-of-remote-commands-different-from-local-output"></a><span data-ttu-id="0d769-199">遠端命令的輸出與本機輸出有何不同？</span><span class="sxs-lookup"><span data-stu-id="0d769-199">Is the output of remote commands different from local output?</span></span>

<span data-ttu-id="0d769-200">當您在本機使用 PowerShell 時，您會傳送和接收「即時」 .NET Framework 物件;「即時」物件是與實際程式或系統元件相關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="0d769-200">When you use PowerShell locally, you send and receive "live" .NET Framework objects; "live" objects are objects that are associated with actual programs or system components.</span></span> <span data-ttu-id="0d769-201">當您叫用方法或變更即時物件的屬性時，變更會影響實際的程式或元件。</span><span class="sxs-lookup"><span data-stu-id="0d769-201">When you invoke the methods or change the properties of live objects, the changes affect the actual program or component.</span></span> <span data-ttu-id="0d769-202">此外，當程式或元件的屬性變更時，代表它們的物件屬性也會變更。</span><span class="sxs-lookup"><span data-stu-id="0d769-202">And, when the properties of a program or component change, the properties of the object that represent them also change.</span></span>

<span data-ttu-id="0d769-203">不過，因為大部分的即時物件無法透過網路傳輸，所以 PowerShell 會「序列化」遠端命令中傳送的大部分物件，也就是說，它會將每個物件轉換成 XML (條件約束語言（XML [CLiXML]） ) 資料元素以進行傳輸。</span><span class="sxs-lookup"><span data-stu-id="0d769-203">However, because most live objects cannot be transmitted over the network, PowerShell "serializes" most of the objects sent in remote commands, that is, it converts each object into a series of XML (Constraint Language in XML [CLiXML]) data elements for transmission.</span></span>

<span data-ttu-id="0d769-204">當 PowerShell 收到序列化的物件時，它會將 XML 轉換成還原序列化的物件類型。</span><span class="sxs-lookup"><span data-stu-id="0d769-204">When PowerShell receives a serialized object, it converts the XML into a deserialized object type.</span></span> <span data-ttu-id="0d769-205">還原序列化的物件是在上一次程式或元件的屬性正確記錄，但不再是「即時」，也就是它不再與元件直接相關聯。</span><span class="sxs-lookup"><span data-stu-id="0d769-205">The deserialized object is an accurate record of the properties of the program or component at a previous time, but it is no longer "live", that is, it is no longer directly associated with the component.</span></span> <span data-ttu-id="0d769-206">而且會移除這些方法，因為這些方法不再有效。</span><span class="sxs-lookup"><span data-stu-id="0d769-206">And, the methods are removed because they are no longer effective.</span></span>

<span data-ttu-id="0d769-207">一般而言，您可以使用已還原序列化的物件，就像使用即時物件一樣，但是您必須知道其限制。</span><span class="sxs-lookup"><span data-stu-id="0d769-207">Typically, you can use deserialized objects just as you would use live objects, but you must be aware of their limitations.</span></span> <span data-ttu-id="0d769-208">此外，Cmdlet 所傳回的物件 `Invoke-Command` 會有其他屬性，可協助您判斷命令的來源。</span><span class="sxs-lookup"><span data-stu-id="0d769-208">Also, the objects that are returned by the `Invoke-Command` cmdlet have additional properties that help you to determine the origin of the command.</span></span>

<span data-ttu-id="0d769-209">某些物件類型（例如 DirectoryInfo 物件和 Guid）會在收到時轉換回即時物件。</span><span class="sxs-lookup"><span data-stu-id="0d769-209">Some object types, such as DirectoryInfo objects and GUIDs, are converted back into live objects when they are received.</span></span> <span data-ttu-id="0d769-210">這些物件不需要任何特殊處理或格式化。</span><span class="sxs-lookup"><span data-stu-id="0d769-210">These objects do not need any special handling or formatting.</span></span>

<span data-ttu-id="0d769-211">如需有關解讀和格式化遠端輸出的詳細資訊，請參閱 [about_Remote_Output](about_Remote_Output.md)。</span><span class="sxs-lookup"><span data-stu-id="0d769-211">For information about interpreting and formatting remote output, see [about_Remote_Output](about_Remote_Output.md).</span></span>

### <a name="can-i-run-background-jobs-remotely"></a><span data-ttu-id="0d769-212">我可以從遠端執行背景工作嗎？</span><span class="sxs-lookup"><span data-stu-id="0d769-212">Can I run background jobs remotely?</span></span>

<span data-ttu-id="0d769-213">是。</span><span class="sxs-lookup"><span data-stu-id="0d769-213">Yes.</span></span> <span data-ttu-id="0d769-214">PowerShell 背景工作是非同步執行的 PowerShell 命令，而不需要與會話互動。</span><span class="sxs-lookup"><span data-stu-id="0d769-214">A PowerShell background job is a PowerShell command that runs asynchronously without interacting with the session.</span></span> <span data-ttu-id="0d769-215">當您啟動背景工作時，命令提示字元會立即傳回，而且您可以在工作執行時繼續在會話中工作，即使執行時間有一段很長的時間。</span><span class="sxs-lookup"><span data-stu-id="0d769-215">When you start a background job, the command prompt returns immediately, and you can continue to work in the session while the job runs even if it runs for an extended period of time.</span></span>

<span data-ttu-id="0d769-216">即使正在執行其他命令，您也可以啟動背景工作，因為背景工作一律會在暫時會話中以非同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="0d769-216">You can start a background job even while other commands are running because background jobs always run asynchronously in a temporary session.</span></span>

<span data-ttu-id="0d769-217">您可以在本機或遠端電腦上執行背景工作。</span><span class="sxs-lookup"><span data-stu-id="0d769-217">You can run background jobs on a local or remote computer.</span></span> <span data-ttu-id="0d769-218">根據預設，背景工作會在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="0d769-218">By default, a background job runs on the local computer.</span></span> <span data-ttu-id="0d769-219">不過，您可以使用 Cmdlet 的 **AsJob** 參數， `Invoke-Command` 以背景工作的形式執行任何遠端命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-219">However, you can use the **AsJob** parameter of the `Invoke-Command` cmdlet to run any remote command as a background job.</span></span> <span data-ttu-id="0d769-220">而且，您可以使用 `Invoke-Command` `Start-Job` 從遠端執行命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-220">And, you can use `Invoke-Command` to run a `Start-Job` command remotely.</span></span>

<span data-ttu-id="0d769-221">如需 PowerShell 中背景工作的詳細資訊，請參閱 [about_Jobs (about_Jobs md) ] 和 [about_Remote_Jobs (about_Remote_Jobs md) ]。</span><span class="sxs-lookup"><span data-stu-id="0d769-221">For more information about background jobs in PowerShell , see [about_Jobs(about_Jobs.md)] and [about_Remote_Jobs(about_Remote_Jobs.md)].</span></span>

### <a name="can-i-run-windows-programs-on-a-remote-computer"></a><span data-ttu-id="0d769-222">我可以在遠端電腦上執行 windows 程式嗎？</span><span class="sxs-lookup"><span data-stu-id="0d769-222">Can I run windows programs on a remote computer?</span></span>

<span data-ttu-id="0d769-223">您可以使用 PowerShell 遠端命令，在遠端電腦上執行以 Windows 為基礎的程式。</span><span class="sxs-lookup"><span data-stu-id="0d769-223">You can use PowerShell remote commands to run Windows-based programs on remote computers.</span></span> <span data-ttu-id="0d769-224">例如，您可以 `Shutdown.exe` `Ipconfig.exe` 在遠端電腦上執行或。</span><span class="sxs-lookup"><span data-stu-id="0d769-224">For example, you can run `Shutdown.exe` or `Ipconfig.exe` on a remote computer.</span></span>

<span data-ttu-id="0d769-225">不過，您無法使用 PowerShell 命令來開啟遠端電腦上任何程式的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="0d769-225">However, you cannot use PowerShell commands to open the user interface for any program on a remote computer.</span></span>

<span data-ttu-id="0d769-226">當您在遠端電腦上啟動 Windows 程式時，命令不會完成，且 PowerShell 命令提示字元不會傳回，直到程式完成為止，或直到您按下<kbd>CTRL</kbd> + <kbd>C</kbd>以中斷命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-226">When you start a Windows program on a remote computer, the command is not completed, and the PowerShell command prompt does not return, until the program is finished or until you press <kbd>CTRL</kbd>+<kbd>C</kbd> to interrupt the command.</span></span> <span data-ttu-id="0d769-227">例如，如果您在 `Ipconfig.exe` 遠端電腦上執行程式，則在完成之前，命令提示字元不會傳回 `Ipconfig.exe` 。</span><span class="sxs-lookup"><span data-stu-id="0d769-227">For example, if you run the `Ipconfig.exe` program on a remote computer, the command prompt does not return until `Ipconfig.exe` is completed.</span></span>

<span data-ttu-id="0d769-228">如果您使用遠端命令來啟動具有使用者介面的程式，則程式進程會啟動，但不會顯示使用者介面。</span><span class="sxs-lookup"><span data-stu-id="0d769-228">If you use remote commands to start a program that has a user interface, the program process starts, but the user interface does not appear.</span></span> <span data-ttu-id="0d769-229">PowerShell 命令未完成，而且在您停止程式進程或直到您按下<kbd>CTRL</kbd> + <kbd>C</kbd>（會中斷命令並停止進程）之前，命令提示字元都不會傳回。</span><span class="sxs-lookup"><span data-stu-id="0d769-229">The PowerShell command is not completed, and the command prompt does not return until you stop the program process or until you press <kbd>CTRL</kbd>+<kbd>C</kbd>, which interrupts the command and stops the process.</span></span>

<span data-ttu-id="0d769-230">例如，如果您使用 PowerShell 命令 `Notepad` 在遠端電腦上執行，則會在遠端電腦上啟動「記事本」處理常式，但不會顯示「記事本」使用者介面。</span><span class="sxs-lookup"><span data-stu-id="0d769-230">For example, if you use a PowerShell command to run `Notepad` on a remote computer, the Notepad process starts on the remote computer, but the Notepad user interface does not appear.</span></span> <span data-ttu-id="0d769-231">若要中斷命令並還原命令提示字元，請按下<kbd>CTRL</kbd> + <kbd>C</kbd>。</span><span class="sxs-lookup"><span data-stu-id="0d769-231">To interrupt the command and restore the command prompt, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

### <a name="can-i-limit-the-commands-that-users-can-run-remotely-on-my-computer"></a><span data-ttu-id="0d769-232">我可以限制使用者可以在我的電腦上遠端執行的命令嗎？</span><span class="sxs-lookup"><span data-stu-id="0d769-232">Can I limit the commands that users can run remotely on my computer?</span></span>

<span data-ttu-id="0d769-233">是。</span><span class="sxs-lookup"><span data-stu-id="0d769-233">Yes.</span></span> <span data-ttu-id="0d769-234">每個遠端會話都必須使用遠端電腦上的其中一個會話設定。</span><span class="sxs-lookup"><span data-stu-id="0d769-234">Every remote session must use one of the session configurations on the remote computer.</span></span> <span data-ttu-id="0d769-235">您可以管理電腦上的會話設定 (以及這些會話設定的許可權) 來判斷誰可以在您的電腦上遠端執行命令，以及他們可以執行的命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-235">You can manage the session configurations on your computer (and the permissions to those session configurations) to determine who can run commands remotely on your computer and which commands they can run.</span></span>

<span data-ttu-id="0d769-236">會話設定會設定會話的環境。</span><span class="sxs-lookup"><span data-stu-id="0d769-236">A session configuration configures the environment for the session.</span></span> <span data-ttu-id="0d769-237">您可以使用會執行新設定類別的元件，或使用在會話中執行的腳本來定義設定。</span><span class="sxs-lookup"><span data-stu-id="0d769-237">You can define the configuration by using an assembly that implements a new configuration class or by using a script that runs in the session.</span></span> <span data-ttu-id="0d769-238">設定可以判斷會話中可用的命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-238">The configuration can determine the commands that are available in the session.</span></span>
<span data-ttu-id="0d769-239">此外，設定可以包含保護電腦的設定，例如限制會話可在單一物件或命令中從遠端接收的資料量的設定。</span><span class="sxs-lookup"><span data-stu-id="0d769-239">And, the configuration can include settings that protect the computer, such as settings that limit the amount of data that the session can receive remotely in a single object or command.</span></span> <span data-ttu-id="0d769-240">您也可以指定安全描述項，以決定使用設定時所需的許可權。</span><span class="sxs-lookup"><span data-stu-id="0d769-240">You can also specify a security descriptor that determines the permissions that are required to use the configuration.</span></span>

<span data-ttu-id="0d769-241">此 `Enable-PSRemoting` Cmdlet 會在您的電腦上建立預設會話設定： microsoft.powershell32 (64 位作業系統，但僅) 。</span><span class="sxs-lookup"><span data-stu-id="0d769-241">The `Enable-PSRemoting` cmdlet creates the default session configurations on your computer: Microsoft.PowerShell, Microsoft.PowerShell.Workflow, and Microsoft.PowerShell32 (64-bit operating systems only).</span></span> <span data-ttu-id="0d769-242">`Enable-PSRemoting` 將設定的安全描述項設定為只允許您電腦上 Administrators 群組的成員使用它們。</span><span class="sxs-lookup"><span data-stu-id="0d769-242">`Enable-PSRemoting` sets the security descriptor for the configuration to allow only members of the Administrators group on your computer to use them.</span></span>

<span data-ttu-id="0d769-243">您可以使用會話設定 Cmdlet 來編輯預設會話設定、建立新的會話設定，以及變更所有會話設定的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="0d769-243">You can use the session configuration cmdlets to edit the default session configurations, to create new session configurations, and to change the security descriptors of all the session configurations.</span></span>

<span data-ttu-id="0d769-244">從 Windows PowerShell 3.0 開始，此 `New-PSSessionConfigurationFile` Cmdlet 可讓您使用文字檔來建立自訂會話設定。</span><span class="sxs-lookup"><span data-stu-id="0d769-244">Beginning in Windows PowerShell 3.0, the `New-PSSessionConfigurationFile` cmdlet lets you create custom session configurations by using a text file.</span></span> <span data-ttu-id="0d769-245">此檔案包含設定語言模式的選項，以及指定在使用會話設定的會話中可用的 Cmdlet 和模組的選項。</span><span class="sxs-lookup"><span data-stu-id="0d769-245">The file includes options for setting the language mode and for specifying the cmdlets and modules that are available in sessions that use the session configuration.</span></span>

<span data-ttu-id="0d769-246">當使用者使用 `Invoke-Command` 、 `New-PSSession` 或 Cmdlet 時 `Enter-PSSession` ，可以使用 **ConfigurationName** 參數來表示會話所使用的會話設定。</span><span class="sxs-lookup"><span data-stu-id="0d769-246">When users use the `Invoke-Command`, `New-PSSession`, or `Enter-PSSession` cmdlets, they can use the **ConfigurationName** parameter to indicate the session configuration that is used for the session.</span></span> <span data-ttu-id="0d769-247">此外，他們可以變更會話中喜好設定變數的值，藉以變更會話使用的預設設定 `$PSSessionConfigurationName` 。</span><span class="sxs-lookup"><span data-stu-id="0d769-247">And, they can change the default configuration that their sessions use by changing the value of the `$PSSessionConfigurationName` preference variable in the session.</span></span>

<span data-ttu-id="0d769-248">如需會話設定的詳細資訊，請參閱 session configuration Cmdlet 的說明。</span><span class="sxs-lookup"><span data-stu-id="0d769-248">For more information about session configurations, see the Help for the session configuration cmdlets.</span></span> <span data-ttu-id="0d769-249">若要尋找會話設定 Cmdlet，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0d769-249">To find the session configuration cmdlets, type:</span></span>

```powershell
Get-Command *PSSessionConfiguration
```

### <a name="what-are-fan-in-and-fan-out-configurations"></a><span data-ttu-id="0d769-250">什麼是傳入和傳出的設定？</span><span class="sxs-lookup"><span data-stu-id="0d769-250">What are fan in and fan out configurations?</span></span>

<span data-ttu-id="0d769-251">涉及多部電腦最常見的 PowerShell 遠端處理案例是一對多的設定，其中一部本機電腦 (系統管理員的電腦) 在多部遠端電腦上執行 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-251">The most common PowerShell remoting scenario involving multiple computers is the one-to-many configuration, in which one local computer (the administrator's computer) runs PowerShell commands on numerous remote computers.</span></span> <span data-ttu-id="0d769-252">這就是所謂的「展開傳送」案例。</span><span class="sxs-lookup"><span data-stu-id="0d769-252">This is known as the "fan-out" scenario.</span></span>

<span data-ttu-id="0d769-253">不過，在某些企業中，設定是多對一的，其中許多用戶端電腦會連線到執行 PowerShell 的單一遠端電腦，例如檔案伺服器或 kiosk。</span><span class="sxs-lookup"><span data-stu-id="0d769-253">However, in some enterprises, the configuration is many-to-one, where many client computers connect to a single remote computer that is running PowerShell, such as a file server or a kiosk.</span></span> <span data-ttu-id="0d769-254">這就是所謂的「收合傳送」設定。</span><span class="sxs-lookup"><span data-stu-id="0d769-254">This is known as the "fan-in" configuration.</span></span>

<span data-ttu-id="0d769-255">PowerShell 遠端支援展開和收合傳送的設定。</span><span class="sxs-lookup"><span data-stu-id="0d769-255">PowerShell remoting supports both fan-out and fan-in configurations.</span></span>

<span data-ttu-id="0d769-256">針對展開傳送設定，PowerShell 會使用 Web 服務進行管理 (WS-MANAGEMENT) 通訊協定，以及支援 Microsoft WS-MANAGEMENT 的 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="0d769-256">For the fan-out configuration, PowerShell uses the Web Services for Management (WS-Management) protocol and the WinRM service that supports the Microsoft implementation of WS-Management.</span></span> <span data-ttu-id="0d769-257">當本機電腦連線到遠端電腦時，WS-Management 會建立連線，並使用適用于 PowerShell 的外掛程式，在遠端電腦上啟動 PowerShell 主機進程 ( # A0) 。</span><span class="sxs-lookup"><span data-stu-id="0d769-257">When a local computer connects to a remote computer, WS-Management establishes a connection and uses a plug-in for PowerShell to start the PowerShell host process (Wsmprovhost.exe) on the remote computer.</span></span> <span data-ttu-id="0d769-258">使用者可以指定替代埠、替代會話設定，以及其他自訂遠端連線的功能。</span><span class="sxs-lookup"><span data-stu-id="0d769-258">The user can specify an alternate port, an alternate session configuration, and other features to customize the remote connection.</span></span>

<span data-ttu-id="0d769-259">為了支援「收合傳送」設定，PowerShell 會使用網際網路資訊服務 (IIS) 來裝載 WS-MANAGEMENT、載入 PowerShell 外掛程式，以及啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0d769-259">To support the "fan-in" configuration, PowerShell uses internet Information Services (IIS) to host WS-Management, to load the PowerShell plug-in, and to start PowerShell.</span></span> <span data-ttu-id="0d769-260">在此案例中，您不會在個別進程中啟動每個 PowerShell 會話，而是在相同的主機進程中執行所有的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="0d769-260">In this scenario, instead of starting each PowerShell session in a separate process, all PowerShell sessions run in the same host process.</span></span>

<span data-ttu-id="0d769-261">在 Windows XP 或 Windows Server 2003 中，不支援 IIS 裝載和扇入遠端系統管理。</span><span class="sxs-lookup"><span data-stu-id="0d769-261">IIS hosting and fan-in remote management is not supported in Windows XP or in Windows Server 2003.</span></span>

<span data-ttu-id="0d769-262">在 [收合傳送] 設定中，使用者可以指定連接 URI 和 HTTP 端點，包括傳輸、電腦名稱稱、埠和應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="0d769-262">In a fan-in configuration, the user can specify a connection URI and an HTTP endpoint, including the transport, computer name, port, and application name.</span></span>
<span data-ttu-id="0d769-263">IIS 會將具有指定應用程式名稱的所有要求轉送至應用程式。</span><span class="sxs-lookup"><span data-stu-id="0d769-263">IIS forwards all the requests with a specified application name to the application.</span></span> <span data-ttu-id="0d769-264">預設值為 WS-MANAGEMENT，可裝載 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0d769-264">The default is WS-Management, which can host PowerShell.</span></span>

<span data-ttu-id="0d769-265">您也可以指定驗證機制，並禁止或允許從 HTTP 和 HTTPS 端點重新導向。</span><span class="sxs-lookup"><span data-stu-id="0d769-265">You can also specify an authentication mechanism and prohibit or allow redirection from HTTP and HTTPS endpoints.</span></span>

### <a name="can-i-test-remoting-on-a-single-computer-not-in-a-domain"></a><span data-ttu-id="0d769-266">我可以在不在網域中的單一電腦上測試遠端功能嗎？</span><span class="sxs-lookup"><span data-stu-id="0d769-266">Can I test remoting on a single computer not in a domain?</span></span>

<span data-ttu-id="0d769-267">是。</span><span class="sxs-lookup"><span data-stu-id="0d769-267">Yes.</span></span> <span data-ttu-id="0d769-268">即使本機電腦不在網域中，也可以使用 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="0d769-268">PowerShell remoting is available even when the local computer is not in a domain.</span></span> <span data-ttu-id="0d769-269">您可以使用遠端功能連接到會話，並在同一部電腦上建立會話。</span><span class="sxs-lookup"><span data-stu-id="0d769-269">You can use the remoting features to connect to sessions and to create sessions on the same computer.</span></span> <span data-ttu-id="0d769-270">這些功能的運作方式與連接到遠端電腦時相同。</span><span class="sxs-lookup"><span data-stu-id="0d769-270">The features work the same as they do when you connect to a remote computer.</span></span>

<span data-ttu-id="0d769-271">若要在工作組中的電腦上執行遠端命令，請變更電腦上的下列 Windows 設定。</span><span class="sxs-lookup"><span data-stu-id="0d769-271">To run remote commands on a computer in a workgroup, change the following Windows settings on the computer.</span></span>

<span data-ttu-id="0d769-272">注意：這些設定會影響系統上的所有使用者，而且可以讓系統更容易遭受惡意攻擊。</span><span class="sxs-lookup"><span data-stu-id="0d769-272">Caution: These settings affect all users on the system and they can make the system more vulnerable to a malicious attack.</span></span> <span data-ttu-id="0d769-273">進行這些變更時請務必小心。</span><span class="sxs-lookup"><span data-stu-id="0d769-273">Use caution when making these changes.</span></span>

- <span data-ttu-id="0d769-274">Windows Vista、Windows 7、Windows 8：</span><span class="sxs-lookup"><span data-stu-id="0d769-274">Windows Vista, Windows 7, Windows 8:</span></span>

  <span data-ttu-id="0d769-275">建立下列登錄專案，然後將其值設定為1： LocalAccountTokenFilterPolicy in ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`</span><span class="sxs-lookup"><span data-stu-id="0d769-275">Create the following registry entry, and then set its value to 1: LocalAccountTokenFilterPolicy in ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`</span></span>

  <span data-ttu-id="0d769-276">您可以使用下列 PowerShell 命令來新增此專案：</span><span class="sxs-lookup"><span data-stu-id="0d769-276">You can use the following PowerShell command to add this entry:</span></span>

    ```powershell
    $parameters = @{
      Path='HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System'
      Name='LocalAccountTokenFilterPolicy'
      propertyType='DWord'
      Value=1
    }
    New-ItemProperty @parameters
    ```

- <span data-ttu-id="0d769-277">Windows Server 2003、Windows Server 2008、Windows Server 2012、Windows Server 2012 R2：</span><span class="sxs-lookup"><span data-stu-id="0d769-277">Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2:</span></span>

  <span data-ttu-id="0d769-278">因為 [網路存取：共用和本機帳戶的安全性模型] 原則的預設設定為 [傳統]，所以不需要進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="0d769-278">No changes are needed because the default setting of the "Network Access: Sharing and security model for local accounts" policy is "Classic".</span></span> <span data-ttu-id="0d769-279">如果設定變更，請驗證設定。</span><span class="sxs-lookup"><span data-stu-id="0d769-279">Verify the setting in case it has changed.</span></span>

### <a name="can-i-run-remote-commands-on-a-computer-in-another-domain"></a><span data-ttu-id="0d769-280">我可以在另一個網域的電腦上執行遠端命令嗎？</span><span class="sxs-lookup"><span data-stu-id="0d769-280">Can I run remote commands on a computer in another domain?</span></span>

<span data-ttu-id="0d769-281">是。</span><span class="sxs-lookup"><span data-stu-id="0d769-281">Yes.</span></span> <span data-ttu-id="0d769-282">一般而言，命令會在沒有錯誤的情況下執行，不過您可能需要使用、或 Cmdlet 的 **Credential** 參數， `Invoke-Command` `New-PSSession` `Enter-PSSession` 以提供遠端電腦上 Administrators 群組成員的認證。</span><span class="sxs-lookup"><span data-stu-id="0d769-282">Typically, the commands run without error, although you might need to use the **Credential** parameter of the `Invoke-Command`, `New-PSSession`, or `Enter-PSSession` cmdlets to provide the credentials of a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="0d769-283">即使目前的使用者是本機電腦和遠端電腦上的 Administrators 群組成員，有時還是需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="0d769-283">This is sometimes required even when the current user is a member of the Administrators group on the local and remote computers.</span></span>

<span data-ttu-id="0d769-284">但是，如果遠端電腦不是在本機電腦信任的網域中，則遠端電腦可能無法驗證使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="0d769-284">However, if the remote computer is not in a domain that the local computer trusts, the remote computer might not be able to authenticate the user's credentials.</span></span>

<span data-ttu-id="0d769-285">若要啟用驗證，請使用下列命令，將遠端電腦新增至 WinRM 中本機電腦的受信任主機清單。</span><span class="sxs-lookup"><span data-stu-id="0d769-285">To enable authentication, use the following command to add the remote computer to the list of trusted hosts for the local computer in WinRM.</span></span> <span data-ttu-id="0d769-286">在 PowerShell 提示字元中輸入命令。</span><span class="sxs-lookup"><span data-stu-id="0d769-286">Type the command at the PowerShell prompt.</span></span>

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value <Remote-computer-name>
```

<span data-ttu-id="0d769-287">例如，若要將 Server01 電腦新增至本機電腦上的受信任主機清單，請在 PowerShell 提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="0d769-287">For example, to add the Server01 computer to the list of trusted hosts on the local computer, type the following command at the PowerShell prompt:</span></span>

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value Server01
```

### <a name="does-powershell-support-remoting-over-ssh"></a><span data-ttu-id="0d769-288">PowerShell 是否支援透過 SSH 進行遠端處理？</span><span class="sxs-lookup"><span data-stu-id="0d769-288">Does PowerShell support remoting over SSH?</span></span>

<span data-ttu-id="0d769-289">是。</span><span class="sxs-lookup"><span data-stu-id="0d769-289">Yes.</span></span> <span data-ttu-id="0d769-290">如需詳細資訊，請參閱透過 [SSH 的 PowerShell 遠端](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)功能。</span><span class="sxs-lookup"><span data-stu-id="0d769-290">For more information, see [PowerShell remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d769-291">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d769-291">See also</span></span>

[<span data-ttu-id="0d769-292">about_Remote</span><span class="sxs-lookup"><span data-stu-id="0d769-292">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="0d769-293">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="0d769-293">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="0d769-294">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="0d769-294">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="0d769-295">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="0d769-295">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)

[<span data-ttu-id="0d769-296">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="0d769-296">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="0d769-297">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="0d769-297">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="0d769-298">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="0d769-298">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
