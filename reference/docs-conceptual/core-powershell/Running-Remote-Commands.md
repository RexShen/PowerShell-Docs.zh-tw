---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 執行遠端命令
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: d21d1def1e25895f65b3578bf2892d56f14cc150
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482874"
---
# <a name="running-remote-commands"></a><span data-ttu-id="4fc3e-103">執行遠端命令</span><span class="sxs-lookup"><span data-stu-id="4fc3e-103">Running Remote Commands</span></span>

<span data-ttu-id="4fc3e-104">您可以使用單一 Windows PowerShell 命令，在一或數百部電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="4fc3e-105">Windows PowerShell 透過使用各種技術 (包括 WMI、RPC 與 WS) 支援遠端運算。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-in-powershell-core"></a><span data-ttu-id="4fc3e-106">PowerShell Core 中的遠端</span><span class="sxs-lookup"><span data-stu-id="4fc3e-106">Remoting in PowerShell Core</span></span>

<span data-ttu-id="4fc3e-107">PowerShell Core 是 Windows、macOS 和 Linux 上的較新 PowerShell 版本，支援 WMI、WS-Management 和 SSH 遠端 </span><span class="sxs-lookup"><span data-stu-id="4fc3e-107">PowerShell Core, the newer edition of PowerShell on Windows, macOS, and Linux, supports WMI, WS-Management, and SSH remoting.</span></span>
<span data-ttu-id="4fc3e-108">(不再支援 RPC)。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-108">(RPC is no longer supported.)</span></span>

<span data-ttu-id="4fc3e-109">如需進行這項設定的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="4fc3e-109">For more information on setting this up, see:</span></span>

* <span data-ttu-id="4fc3e-110">[PowerShell Core 中的 SSH 遠端功能][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="4fc3e-110">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="4fc3e-111">[PowerShell Core 中的 WSMan 遠端功能][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="4fc3e-111">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="4fc3e-112">不需要進行設定的遠端執行功能</span><span class="sxs-lookup"><span data-stu-id="4fc3e-112">Remoting Without Configuration</span></span>

<span data-ttu-id="4fc3e-113">許多 Windows PowerShell Cmdlet 都有 ComputerName 參數，可讓您收集資料，並變更一或多部遠端電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-113">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="4fc3e-114">它們使用各種通訊技術，且許多都能在 Windows PowerShell 支援的所有 Windows 作業系統上運作，而不需要特殊設定。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-114">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="4fc3e-115">這些 Cmdlet 包含：</span><span class="sxs-lookup"><span data-stu-id="4fc3e-115">These cmdlets include:</span></span>

* [<span data-ttu-id="4fc3e-116">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="4fc3e-116">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="4fc3e-117">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="4fc3e-117">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="4fc3e-118">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="4fc3e-118">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="4fc3e-119">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="4fc3e-119">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="4fc3e-120">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="4fc3e-120">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
* [<span data-ttu-id="4fc3e-121">Get-Process</span><span class="sxs-lookup"><span data-stu-id="4fc3e-121">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="4fc3e-122">Get-Service</span><span class="sxs-lookup"><span data-stu-id="4fc3e-122">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="4fc3e-123">Set-Service</span><span class="sxs-lookup"><span data-stu-id="4fc3e-123">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="4fc3e-124">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="4fc3e-124">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="4fc3e-125">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="4fc3e-125">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="4fc3e-126">一般而言，支援遠端處理而不需要特殊設定的 Cmdlet 具有 ComputerName 參數，而沒有 Session 參數。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-126">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="4fc3e-127">若要在您的工作階段中尋找這些 Cmdlet，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4fc3e-127">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="4fc3e-128">Windows PowerShell 遠端執行功能</span><span class="sxs-lookup"><span data-stu-id="4fc3e-128">Windows PowerShell Remoting</span></span>

<span data-ttu-id="4fc3e-129">Windows PowerShell 遠端執行功能使用 WS-Management 通訊協定，可讓您在一或多部遠端電腦上執行任何 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-129">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="4fc3e-130">它可讓您建立持續連線、啟動 1:1 互動式工作階段，以及在多部電腦上執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-130">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="4fc3e-131">若要使用 Windows PowerShell 遠端執行功能，必須針對遠端管理設定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-131">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="4fc3e-132">如需包括指示的詳細資訊，請參閱[關於遠端需求](https://technet.microsoft.com/library/dd315349.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-132">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/library/dd315349.aspx).</span></span>

<span data-ttu-id="4fc3e-133">設定 Windows PowerShell 遠端執行功能之後，許多遠端處理策略就可供您使用。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-133">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="4fc3e-134">這份文件的其餘部分只列出其中幾個。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-134">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="4fc3e-135">如需詳細資訊，請參閱[關於遠端](https://technet.microsoft.com/library/dd347744.aspx)與[關於遠端常見問題集](https://technet.microsoft.com/library/dd347744.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-135">For more information, see [About Remote](https://technet.microsoft.com/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="4fc3e-136">啟動互動式工作階段</span><span class="sxs-lookup"><span data-stu-id="4fc3e-136">Start an Interactive Session</span></span>

<span data-ttu-id="4fc3e-137">若要啟動與單一遠端電腦的互動式工作階段，請使用 [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-137">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="4fc3e-138">例如，若要啟動與 Server01 遠端電腦的互動式工作階段，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4fc3e-138">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="4fc3e-139">命令提示字元將變更為顯示您所連線之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-139">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="4fc3e-140">從那時開始，您在提示字元中輸入的所有命令都會在遠端電腦上執行，而結果會顯示本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-140">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="4fc3e-141">若要結束互動式工作階段，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4fc3e-141">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="4fc3e-142">如需 Enter-PSSession 與 Exit-PSSession Cmdlet 的詳細資訊，請參閱 [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) 與 [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478)。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-142">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="4fc3e-143">執行遠端命令</span><span class="sxs-lookup"><span data-stu-id="4fc3e-143">Run a Remote Command</span></span>

<span data-ttu-id="4fc3e-144">若要在一或多部遠端電腦上執行任何命令，請使用 [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-144">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="4fc3e-145">例如，若要在 Server01 與 Server02 遠端電腦上執行 [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) 命令，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4fc3e-145">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="4fc3e-146">輸出會傳回到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-146">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

<span data-ttu-id="4fc3e-147">如需 Invoke-Command Cmdlet 的詳細資訊，請參閱 [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="4fc3e-148">執行指令碼</span><span class="sxs-lookup"><span data-stu-id="4fc3e-148">Run a Script</span></span>

<span data-ttu-id="4fc3e-149">若要在一或多部遠端電腦上執行指令碼，請使用 Invoke-Command Cmdlet 的 FilePath 參數。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-149">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="4fc3e-150">您的本機電腦上必須有該指令碼或可存取該指令碼。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="4fc3e-151">結果會傳回到您的本機電腦。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="4fc3e-152">例如，下列命令會在 Server01 與 Server02 遠端電腦上執行 DiskCollect.ps1 指令碼。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-152">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="4fc3e-153">如需 Invoke-Command Cmdlet 的詳細資訊，請參閱 [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-153">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="4fc3e-154">建立持續連線</span><span class="sxs-lookup"><span data-stu-id="4fc3e-154">Establish a Persistent Connection</span></span>

<span data-ttu-id="4fc3e-155">若要執行一系列共用資料的相關命令，請在遠端電腦上建立工作階段，然後使用 Invoke-Command Cmdlet 在您建立的工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-155">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="4fc3e-156">若要建立遠端工作階段，請使用 New-PSSession Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-156">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="4fc3e-157">例如，下列命令會在 Server01 電腦上建立遠端工作階段，並在 Server02 電腦上建立另一個遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-157">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="4fc3e-158">它會將該工作階段物件儲存於 $s 變數中。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-158">It saves the session objects in the $s variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="4fc3e-159">現在，工作階段已建立，您可以在其中執行任何命令。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="4fc3e-160">因為工作階段是持續性，您可以在單一命令中收集資料，並將它用於後續的命令。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-160">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="4fc3e-161">例如，下列命令會在 $s 變數的工作階段中執行 Get-HotFix 命令，並將結果儲存在 $h 變數中。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="4fc3e-162">$h 變數會建立在 $s 的各個工作階段中，但不會存在於本機工作階段。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-162">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="4fc3e-163">現在您可以在後續命令中使用 $h 變數中的資料，例如下列範例。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-163">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="4fc3e-164">結果會顯示在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-164">The results are displayed on the local computer.</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="4fc3e-165">進階遠端處理</span><span class="sxs-lookup"><span data-stu-id="4fc3e-165">Advanced Remoting</span></span>

<span data-ttu-id="4fc3e-166">Windows PowerShell 遠端管理在這裡開始。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-166">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="4fc3e-167">使用 Windows PowerShell 安裝的 Cmdlet，您可以同時建立及設定本機與遠端電腦的遠端工作階段、建立自訂與受限制的工作階段、允許使用者從實際隱含執行於遠端工作階段的遠端工作階段匯入命令，以及設定遠端工作階段安全性等。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-167">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="4fc3e-168">為簡化遠端設定，Windows PowerShell 包含 WSMan 提供者。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-168">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="4fc3e-169">提供者建立的 WSMAN: 磁碟機可讓您瀏覽本機電腦與遠端電腦上組態設定的階層。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-169">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="4fc3e-170">如需 WSMan 提供者的詳細資訊，請參閱 [WSMan 提供者](https://technet.microsoft.com/library/dd819476.aspx)與[關於 WS-Management Cmdlet](https://technet.microsoft.com/library/dd819481.aspx)，或在 Windows PowerShell 主控台中，輸入 "Get-Help wsman"。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-170">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="4fc3e-171">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="4fc3e-171">For more information, see:</span></span>

- [<span data-ttu-id="4fc3e-172">關於遠端常見問題集</span><span class="sxs-lookup"><span data-stu-id="4fc3e-172">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="4fc3e-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4fc3e-173">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="4fc3e-174">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="4fc3e-174">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="4fc3e-175">如需遠端處理錯誤的說明，請參閱 [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4fc3e-175">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="4fc3e-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fc3e-176">See Also</span></span>

- [<span data-ttu-id="4fc3e-177">about_Remote</span><span class="sxs-lookup"><span data-stu-id="4fc3e-177">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="4fc3e-178">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="4fc3e-178">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="4fc3e-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="4fc3e-179">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="4fc3e-180">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="4fc3e-180">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="4fc3e-181">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="4fc3e-181">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="4fc3e-182">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="4fc3e-182">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="4fc3e-183">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="4fc3e-183">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="4fc3e-184">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="4fc3e-184">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="4fc3e-185">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="4fc3e-185">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="4fc3e-186">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4fc3e-186">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="4fc3e-187">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="4fc3e-187">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md