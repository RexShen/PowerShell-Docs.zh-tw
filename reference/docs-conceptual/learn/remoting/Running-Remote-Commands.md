---
ms.date: 08/21/2020
keywords: powershell,cmdlet
title: 執行遠端命令
description: 說明使用 PowerShell 在遠端系統上執行命令的方法。
ms.openlocfilehash: e9e07fec96cbd93d3bf06be2a1f98ec7aa7d8f19
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501349"
---
# <a name="running-remote-commands"></a><span data-ttu-id="5be1c-104">執行遠端命令</span><span class="sxs-lookup"><span data-stu-id="5be1c-104">Running Remote Commands</span></span>

<span data-ttu-id="5be1c-105">您可以使用單一 PowerShell 命令，在一部或數百部電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="5be1c-105">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="5be1c-106">Windows PowerShell 透過使用各種技術 (包括 WMI、RPC 與 WS) 支援遠端運算。</span><span class="sxs-lookup"><span data-stu-id="5be1c-106">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="5be1c-107">PowerShell Core 支援 WMI、WS-Management 與 SSH 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="5be1c-107">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="5be1c-108">在 PowerShell 6 中，不再支援 RPC。</span><span class="sxs-lookup"><span data-stu-id="5be1c-108">In PowerShell 6, RPC is no longer supported.</span></span> <span data-ttu-id="5be1c-109">在 PowerShell 7 及以上版本中，只有 Windows 支援 RPC。</span><span class="sxs-lookup"><span data-stu-id="5be1c-109">In PowerShell 7 and above, RPC is supported only in Windows.</span></span>

<span data-ttu-id="5be1c-110">如需 PowerShell Core 中遠端功能的詳細資訊，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="5be1c-110">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="5be1c-111">[PowerShell Core 中的 SSH 遠端功能][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="5be1c-111">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="5be1c-112">[PowerShell Core 中的 WSMan 遠端功能][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="5be1c-112">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="5be1c-113">不需設定的 Windows PowerShell 遠端功能</span><span class="sxs-lookup"><span data-stu-id="5be1c-113">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="5be1c-114">許多 Windows PowerShell Cmdlet 都有 ComputerName 參數，可讓您收集資料，並變更一或多部遠端電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="5be1c-114">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="5be1c-115">這些 Cmdlet 使用各種不同的通訊協定，在不需任何特殊設定的所有 Windows 作業系統上運作。</span><span class="sxs-lookup"><span data-stu-id="5be1c-115">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="5be1c-116">這些 Cmdlet 包含：</span><span class="sxs-lookup"><span data-stu-id="5be1c-116">These cmdlets include:</span></span>

- [<span data-ttu-id="5be1c-117">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="5be1c-117">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="5be1c-118">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="5be1c-118">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="5be1c-119">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="5be1c-119">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="5be1c-120">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="5be1c-120">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="5be1c-121">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="5be1c-121">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="5be1c-122">Get-Process</span><span class="sxs-lookup"><span data-stu-id="5be1c-122">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="5be1c-123">Get-Service</span><span class="sxs-lookup"><span data-stu-id="5be1c-123">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="5be1c-124">Set-Service</span><span class="sxs-lookup"><span data-stu-id="5be1c-124">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="5be1c-125">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="5be1c-125">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="5be1c-126">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="5be1c-126">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="5be1c-127">一般而言，不需特殊設定即可支援遠端功能的 Cmdlet 具有 ComputerName 參數，而且沒有 Session 參數。</span><span class="sxs-lookup"><span data-stu-id="5be1c-127">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="5be1c-128">若要在您的工作階段中尋找這些 Cmdlet，請輸入：</span><span class="sxs-lookup"><span data-stu-id="5be1c-128">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="5be1c-129">Windows PowerShell 遠端執行功能</span><span class="sxs-lookup"><span data-stu-id="5be1c-129">Windows PowerShell Remoting</span></span>

<span data-ttu-id="5be1c-130">使用 WS-Management 通訊協定，Windows PowerShell 遠端功能可讓您在一或多部遠端電腦上執行任何 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="5be1c-130">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="5be1c-131">您可以建立持續連線、啟動互動式工作階段，以及在遠端電腦上執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="5be1c-131">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="5be1c-132">若要使用 Windows PowerShell 遠端執行功能，必須針對遠端管理設定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="5be1c-132">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="5be1c-133">如需包括指示的詳細資訊，請參閱[關於遠端需求](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)。</span><span class="sxs-lookup"><span data-stu-id="5be1c-133">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="5be1c-134">設定 Windows PowerShell 遠端功能之後，就有許多遠端處理策略可供您使用。</span><span class="sxs-lookup"><span data-stu-id="5be1c-134">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="5be1c-135">本文只列出其中幾個。</span><span class="sxs-lookup"><span data-stu-id="5be1c-135">This article lists just a few of them.</span></span> <span data-ttu-id="5be1c-136">如需詳細資訊，請參閱[關於遠端](/powershell/module/microsoft.powershell.core/about/about_remote)。</span><span class="sxs-lookup"><span data-stu-id="5be1c-136">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="5be1c-137">啟動互動式工作階段</span><span class="sxs-lookup"><span data-stu-id="5be1c-137">Start an Interactive Session</span></span>

<span data-ttu-id="5be1c-138">若要啟動與遠端電腦的互動式工作階段，請使用 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5be1c-138">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span> <span data-ttu-id="5be1c-139">例如，若要啟動與 Server01 遠端電腦的互動式工作階段，請輸入：</span><span class="sxs-lookup"><span data-stu-id="5be1c-139">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="5be1c-140">此命令提示字元會變更以顯示遠端電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="5be1c-140">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="5be1c-141">您在提示字元中輸入的所有命令都會在遠端電腦上執行，而結果均會顯示於本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="5be1c-141">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="5be1c-142">若要結束互動式工作階段，請輸入：</span><span class="sxs-lookup"><span data-stu-id="5be1c-142">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="5be1c-143">如需 Enter-PSSession 與 Exit-PSSession Cmdlet 的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="5be1c-143">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="5be1c-144">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="5be1c-144">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="5be1c-145">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="5be1c-145">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="5be1c-146">執行遠端命令</span><span class="sxs-lookup"><span data-stu-id="5be1c-146">Run a Remote Command</span></span>

<span data-ttu-id="5be1c-147">若要在一或多部遠端電腦上執行命令，請使用 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5be1c-147">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="5be1c-148">例如，若要在 Server01 與 Server02 遠端電腦上執行 [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) 命令，請輸入：</span><span class="sxs-lookup"><span data-stu-id="5be1c-148">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="5be1c-149">輸出會傳回到您的電腦。</span><span class="sxs-lookup"><span data-stu-id="5be1c-149">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="5be1c-150">執行指令碼</span><span class="sxs-lookup"><span data-stu-id="5be1c-150">Run a Script</span></span>

<span data-ttu-id="5be1c-151">若要在一或多部遠端電腦上執行指令碼，請使用 `Invoke-Command` Cmdlet 的 FilePath 參數。</span><span class="sxs-lookup"><span data-stu-id="5be1c-151">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="5be1c-152">您的本機電腦上必須有該指令碼或可存取該指令碼。</span><span class="sxs-lookup"><span data-stu-id="5be1c-152">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="5be1c-153">結果會傳回到您的本機電腦。</span><span class="sxs-lookup"><span data-stu-id="5be1c-153">The results are returned to your local computer.</span></span>

<span data-ttu-id="5be1c-154">例如，下列命令會在遠端電腦 (Server01 與 Server02) 上執行 DiskCollect.ps1 指令碼。</span><span class="sxs-lookup"><span data-stu-id="5be1c-154">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="5be1c-155">建立持續連線</span><span class="sxs-lookup"><span data-stu-id="5be1c-155">Establish a Persistent Connection</span></span>

<span data-ttu-id="5be1c-156">使用 `New-PSSession` Cmdlet，在遠端電腦上建立一個持續性工作階段。</span><span class="sxs-lookup"><span data-stu-id="5be1c-156">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="5be1c-157">下列範例會在 Server01 與 Server02 上建立遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="5be1c-157">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="5be1c-158">工作階段物件會儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="5be1c-158">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="5be1c-159">現在，工作階段已建立，您可以在其中執行任何命令。</span><span class="sxs-lookup"><span data-stu-id="5be1c-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="5be1c-160">此外，由於工作階段是持續性的，因此，您可以從單一命令收集資料，並將它用於其他命令中。</span><span class="sxs-lookup"><span data-stu-id="5be1c-160">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="5be1c-161">例如，下列命令會在 $s 變數的工作階段中執行 Get-HotFix 命令，並將結果儲存在 $h 變數中。</span><span class="sxs-lookup"><span data-stu-id="5be1c-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="5be1c-162">$h 變數是在 $s 的每個工作階段中所建立，但在本機工作階段中不存在。</span><span class="sxs-lookup"><span data-stu-id="5be1c-162">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="5be1c-163">現在，您可以搭配相同工作階段中的其他命令來使用 `$h` 變數中的資料。</span><span class="sxs-lookup"><span data-stu-id="5be1c-163">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="5be1c-164">結果會顯示在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="5be1c-164">The results are displayed on the local computer.</span></span> <span data-ttu-id="5be1c-165">例如：</span><span class="sxs-lookup"><span data-stu-id="5be1c-165">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="5be1c-166">進階遠端處理</span><span class="sxs-lookup"><span data-stu-id="5be1c-166">Advanced Remoting</span></span>

<span data-ttu-id="5be1c-167">Windows PowerShell 遠端管理在這裡開始。</span><span class="sxs-lookup"><span data-stu-id="5be1c-167">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="5be1c-168">使用 Windows PowerShell 安裝的 Cmdlet，您可以同時建立及設定本機與遠端電腦的遠端工作階段、建立自訂與受限制的工作階段、允許使用者從實際隱含執行於遠端工作階段的遠端工作階段匯入命令，以及設定遠端工作階段安全性等。</span><span class="sxs-lookup"><span data-stu-id="5be1c-168">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="5be1c-169">Windows PowerShell 包含 WSMan 提供者。</span><span class="sxs-lookup"><span data-stu-id="5be1c-169">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="5be1c-170">提供者會建立 `WSMAN:` 磁碟機，讓您可以完整瀏覽本機電腦與遠端電腦上組態設定的階層。</span><span class="sxs-lookup"><span data-stu-id="5be1c-170">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="5be1c-171">如需 WSMan 提供者的詳細資訊，請參閱 [WSMan 提供者](https://technet.microsoft.com/library/dd819476.aspx) \(英文\) 與[關於 WS-Management Cmdlet](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets)，或在 Windows PowerShell 主控台中，輸入 `Get-Help wsman`。</span><span class="sxs-lookup"><span data-stu-id="5be1c-171">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="5be1c-172">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="5be1c-172">For more information, see:</span></span>

- [<span data-ttu-id="5be1c-173">關於遠端常見問題集</span><span class="sxs-lookup"><span data-stu-id="5be1c-173">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="5be1c-174">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5be1c-174">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="5be1c-175">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="5be1c-175">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="5be1c-176">如需遠端處理錯誤的說明，請參閱 [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5be1c-176">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="5be1c-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5be1c-177">See Also</span></span>

- [<span data-ttu-id="5be1c-178">about_Remote</span><span class="sxs-lookup"><span data-stu-id="5be1c-178">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="5be1c-179">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="5be1c-179">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="5be1c-180">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="5be1c-180">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="5be1c-181">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="5be1c-181">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="5be1c-182">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="5be1c-182">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="5be1c-183">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="5be1c-183">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="5be1c-184">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="5be1c-184">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="5be1c-185">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="5be1c-185">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="5be1c-186">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="5be1c-186">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="5be1c-187">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5be1c-187">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="5be1c-188">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="5be1c-188">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
