---
description: 說明如何在 PowerShell 中執行遠端命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: 1974352f57625689907143340c7439ed3d92b431
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208188"
---
# <a name="about-remote"></a><span data-ttu-id="0fe7f-104">關於遠端</span><span class="sxs-lookup"><span data-stu-id="0fe7f-104">About Remote</span></span>

## <a name="short-description"></a><span data-ttu-id="0fe7f-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="0fe7f-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="0fe7f-106">說明如何在 PowerShell 中執行遠端命令。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-106">Describes how to run remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="0fe7f-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="0fe7f-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="0fe7f-108">您可以使用暫存或持續連線，在單一電腦或多部電腦上執行遠端命令。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-108">You can run remote commands on a single computer or on multiple computers by using a temporary or persistent connection.</span></span> <span data-ttu-id="0fe7f-109">您也可以啟動單一遠端電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-109">You can also start an interactive session with a single remote computer.</span></span>

<span data-ttu-id="0fe7f-110">本主題提供一系列的範例，說明如何執行不同類型的遠端命令。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-110">This topic provides a series of examples to show you how to run different types of remote command.</span></span> <span data-ttu-id="0fe7f-111">在您嘗試這些基本命令之後，請閱讀描述這些命令所使用之每個 Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-111">After you try these basic commands, read the Help topics that describe each cmdlet that is used in these commands.</span></span> <span data-ttu-id="0fe7f-112">這些主題會提供詳細資料，並說明如何修改命令以符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-112">The topics provide the details and explain how you can modify the commands to meet your needs.</span></span>

<span data-ttu-id="0fe7f-113">注意：若要使用 PowerShell 遠端處理，必須設定本機和遠端電腦以進行遠端處理。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-113">Note: To use PowerShell remoting, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="0fe7f-114">如需詳細資訊，請參閱[about_Remote_Requirements](about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-114">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

## <a name="how-to-start-an-interactive-session-enter-pssession"></a><span data-ttu-id="0fe7f-115">如何啟動互動式會話 (輸入-PSSESSION) </span><span class="sxs-lookup"><span data-stu-id="0fe7f-115">HOW TO START AN INTERACTIVE SESSION (ENTER-PSSESSION)</span></span>

<span data-ttu-id="0fe7f-116">執行遠端命令最簡單的方式，就是啟動遠端電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-116">The easiest way to run remote commands is to start an interactive session with a remote computer.</span></span>

<span data-ttu-id="0fe7f-117">當會話啟動時，您輸入的命令會在遠端電腦上執行，就像您直接在遠端電腦上輸入一樣。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-117">When the session starts, the commands that you type run on the remote computer, just as though you typed them directly on the remote computer.</span></span> <span data-ttu-id="0fe7f-118">您只能在每個互動式會話中連接到一部電腦。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-118">You can connect to only one computer in each interactive session.</span></span>

<span data-ttu-id="0fe7f-119">若要啟動互動式會話，請使用 Enter-PSSession Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-119">To start an interactive session, use the Enter-PSSession cmdlet.</span></span> <span data-ttu-id="0fe7f-120">下列命令會啟動 Server01 電腦的互動式會話：</span><span class="sxs-lookup"><span data-stu-id="0fe7f-120">The following command starts an interactive session with the Server01 computer:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="0fe7f-121">命令提示字元會變更，以指出您已連線到 Server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-121">The command prompt changes to indicate that you are connected to the Server01 computer.</span></span>

```
Server01\PS>
```

<span data-ttu-id="0fe7f-122">現在，您可以在 Server01 電腦上輸入命令。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-122">Now, you can type commands on the Server01 computer.</span></span>

<span data-ttu-id="0fe7f-123">若要結束互動式工作階段，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0fe7f-123">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="0fe7f-124">如需詳細資訊，請參閱輸入-PSSession。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-124">For more information, see Enter-PSSession.</span></span>

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a><span data-ttu-id="0fe7f-125">如何使用具有 COMPUTERNAME 參數的 CMDLET 來取得遠端資料</span><span class="sxs-lookup"><span data-stu-id="0fe7f-125">HOW TO USE CMDLETS THAT HAVE A COMPUTERNAME PARAMETER TO GET REMOTE DATA</span></span>

<span data-ttu-id="0fe7f-126">有數個 Cmdlet 具有 ComputerName 參數，可讓您從遠端電腦取得物件。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-126">Several cmdlets have a ComputerName parameter that lets you get objects from remote computers.</span></span>

<span data-ttu-id="0fe7f-127">因為這些 Cmdlet 不會使用 WS-MANAGEMENT 型 PowerShell 遠端處理，所以您可以在任何執行 PowerShell 的電腦上使用這些 Cmdlet 的 ComputerName 參數。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-127">Because these cmdlets do not use WS-Management-based PowerShell remoting, you can use the ComputerName parameter of these cmdlets on any computer that is running PowerShell.</span></span> <span data-ttu-id="0fe7f-128">電腦不需要針對 PowerShell 遠端進行設定，且電腦不需要符合遠端處理的系統需求。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-128">The computers do not have to be configured for PowerShell remoting, and the computers do not have to meet the system requirements for remoting.</span></span>

<span data-ttu-id="0fe7f-129">下列 Cmdlet 具有 ComputerName 參數：</span><span class="sxs-lookup"><span data-stu-id="0fe7f-129">The following cmdlets have a ComputerName parameter:</span></span>

```
Clear-EventLog    Limit-EventLog
Get-Counter       New-EventLog
Get-EventLog      Remove-EventLog
Get-HotFix        Restart-Computer
Get-Process       Show-EventLog
Get-Service       Stop-Computer
Get-WinEvent      Test-Connection
Get-WmiObject     Write-EventLog
```

<span data-ttu-id="0fe7f-130">例如，下列命令會取得 Server01 遠端電腦上的服務：</span><span class="sxs-lookup"><span data-stu-id="0fe7f-130">For example, the following command gets the services on the Server01 remote computer:</span></span>

```powershell
Get-Service -ComputerName Server01
```

<span data-ttu-id="0fe7f-131">一般而言，支援遠端處理而不需要特殊設定的 Cmdlet 具有 **ComputerName** 參數，且沒有 **Session** 參數。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-131">Typically, cmdlets that support remoting without special configuration have a **ComputerName** parameter and do not have a **Session** parameter.</span></span> <span data-ttu-id="0fe7f-132">若要在您的工作階段中尋找這些 Cmdlet，請輸入：</span><span class="sxs-lookup"><span data-stu-id="0fe7f-132">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a><span data-ttu-id="0fe7f-133">如何執行遠端命令</span><span class="sxs-lookup"><span data-stu-id="0fe7f-133">HOW TO RUN A REMOTE COMMAND</span></span>

<span data-ttu-id="0fe7f-134">若要在遠端電腦上執行其他命令，請使用 Invoke-Command Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-134">To run other commands on remote computers, use the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="0fe7f-135">若要執行單一命令或一些不相關的命令，請使用 Invoke-Command 的 ComputerName 參數來指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-135">To run a single command or a few unrelated commands, use the ComputerName parameter of Invoke-Command to specify the remote computers.</span></span> <span data-ttu-id="0fe7f-136">使用 ScriptBlock 參數來指定命令。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-136">Use the ScriptBlock parameter to specify the command.</span></span>

<span data-ttu-id="0fe7f-137">例如，下列命令會在 Server01 電腦上執行 Get-Culture 命令。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-137">For example, the following command runs a Get-Culture command on the Server01 computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="0fe7f-138">ComputerName 參數是針對您在一或多部電腦上執行單一命令或數個不相關命令的情況所設計。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-138">The ComputerName parameter is designed for situation in which you run a single command or several unrelated commands on one or many computers.</span></span> <span data-ttu-id="0fe7f-139">若要建立連到遠端電腦的持續連線，請使用 Session 參數。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-139">To establish a persistent connection to a remote computer, use the Session parameter.</span></span>

## <a name="how-to-create-a-persistent-connection-pssession"></a><span data-ttu-id="0fe7f-140">如何建立 (PSSESSION) 的持續連線</span><span class="sxs-lookup"><span data-stu-id="0fe7f-140">HOW TO CREATE A PERSISTENT CONNECTION (PSSESSION)</span></span>

<span data-ttu-id="0fe7f-141">當您使用 Invoke-Command Cmdlet 的 ComputerName 參數時，Windows PowerShell 只會針對命令建立連接。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-141">When you use the ComputerName parameter of the Invoke-Command cmdlet, Windows PowerShell establishes a connection just for the command.</span></span> <span data-ttu-id="0fe7f-142">然後，在命令完成時，就會關閉連線。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-142">Then, it closes the connection when the command is complete.</span></span> <span data-ttu-id="0fe7f-143">命令中所定義的任何變數或函數都會遺失。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-143">Any variables or functions that are defined in the command are lost.</span></span>

<span data-ttu-id="0fe7f-144">若要建立連到遠端電腦的持續連線，請使用 New-PSSession Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-144">To create a persistent connection to a remote computer, use the New-PSSession cmdlet.</span></span> <span data-ttu-id="0fe7f-145">例如，下列命令會在 Server01 和 Server02 電腦上建立 Pssession，然後將 Pssession 儲存在 $s 變數中。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-145">For example, the following command creates PSSessions on the Server01 and Server02 computers and then saves the PSSessions in the $s variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="0fe7f-146">如何在 PSSESSION 中執行命令</span><span class="sxs-lookup"><span data-stu-id="0fe7f-146">HOW TO RUN COMMANDS IN A PSSESSION</span></span>

<span data-ttu-id="0fe7f-147">您可以使用 PSSession 來執行一系列共用資料的遠端命令，例如函數、別名和變數的值。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-147">With a PSSession, you can run a series of remote commands that share data, like functions, aliases, and the values of variables.</span></span> <span data-ttu-id="0fe7f-148">若要在 PSSession 中執行命令，請使用 Invoke-Command Cmdlet 的 Session 參數。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-148">To run commands in a PSSession, use the Session parameter of the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="0fe7f-149">例如，下列命令會使用 Invoke-Command Cmdlet，在 Server01 和 Server02 電腦上的 Pssession 中執行 Get-Process 命令。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-149">For example, the following command uses the Invoke-Command cmdlet to run a Get-Process command in the PSSessions on the Server01 and Server02 computers.</span></span>
<span data-ttu-id="0fe7f-150">命令會將 $p 變數中的處理常式儲存在每個 PSSession 中。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-150">The command saves the processes in a $p variable in each PSSession.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

<span data-ttu-id="0fe7f-151">因為 PSSession 使用持續性連接，所以您可以在使用 $p 變數的相同 PSSession 中執行另一個命令。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-151">Because the PSSession uses a persistent connection, you can run another command in the same PSSession that uses the $p variable.</span></span> <span data-ttu-id="0fe7f-152">下列命令會計算 $p 中儲存的進程數目。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-152">The following command counts the number of processes saved in $p.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a><span data-ttu-id="0fe7f-153">如何在多部電腦上執行遠端命令</span><span class="sxs-lookup"><span data-stu-id="0fe7f-153">HOW TO RUN A REMOTE COMMAND ON MULTIPLE COMPUTERS</span></span>

<span data-ttu-id="0fe7f-154">若要在多部電腦上執行遠端命令，請在 [Invoke 命令的 ComputerName] 參數值中輸入所有電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-154">To run a remote command on multiple computers, type all of the computer names in the value of the ComputerName parameter of Invoke-Command.</span></span> <span data-ttu-id="0fe7f-155">以逗號分隔名稱。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-155">Separate the names with commas.</span></span>

<span data-ttu-id="0fe7f-156">例如，下列命令會在三部電腦上執行 Get-Culture 命令：</span><span class="sxs-lookup"><span data-stu-id="0fe7f-156">For example, the following command runs a Get-Culture command on three computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="0fe7f-157">您也可以在多個 Pssession 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-157">You can also run a command in multiple PSSessions.</span></span> <span data-ttu-id="0fe7f-158">下列命令會在 Server01、Server02 和 Server03 電腦上建立 Pssession，然後在每個 Pssession 中執行 Get-Culture 命令。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-158">The following commands create PSSessions on the Server01, Server02, and Server03 computers and then run a Get-Culture command in each of the PSSessions.</span></span>

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="0fe7f-159">若要包含電腦的 [本機電腦] 清單，請輸入本機電腦的名稱、輸入點 ( ) 或輸入 "localhost"。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-159">To include the local computer list of computers, type the name of the local computer, type a dot (.), or type  "localhost".</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a><span data-ttu-id="0fe7f-160">如何在遠端電腦上執行腳本</span><span class="sxs-lookup"><span data-stu-id="0fe7f-160">HOW TO RUN A SCRIPT ON REMOTE COMPUTERS</span></span>

<span data-ttu-id="0fe7f-161">若要在遠端電腦上執行本機腳本，請使用 Invoke 命令的 FilePath 參數。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-161">To run a local script on remote computers, use the FilePath parameter of Invoke-Command.</span></span>

<span data-ttu-id="0fe7f-162">例如，下列命令會在 S1 和 S2 電腦上執行 Sample.ps1 腳本：</span><span class="sxs-lookup"><span data-stu-id="0fe7f-162">For example, the following command runs the Sample.ps1 script on the S1 and S2 computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

<span data-ttu-id="0fe7f-163">腳本的結果會傳回到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-163">The results of the script are returned to the local computer.</span></span> <span data-ttu-id="0fe7f-164">您不需要複製任何檔案。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-164">You do not need to copy any files.</span></span>

## <a name="how-to-stop-a-remote-command"></a><span data-ttu-id="0fe7f-165">如何停止遠端命令</span><span class="sxs-lookup"><span data-stu-id="0fe7f-165">HOW TO STOP A REMOTE COMMAND</span></span>

<span data-ttu-id="0fe7f-166">若要中斷命令，請按 CTRL + C。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-166">To interrupt a command, press CTRL+C.</span></span> <span data-ttu-id="0fe7f-167">中斷要求會傳遞至遠端電腦，以終止遠端命令。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-167">The interrupt request is passed to the remote computer where it terminates the remote command.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="0fe7f-168">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="0fe7f-168">FOR MORE INFORMATION</span></span>

- <span data-ttu-id="0fe7f-169">如需遠端處理系統需求的詳細資訊，請參閱 [about_Remote_Requirements](about_Remote_Requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-169">For information about the system requirements for remoting, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

- <span data-ttu-id="0fe7f-170">如需如何格式化遠端輸出的說明，請參閱 [about_Remote_Output](about_Remote_Output.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-170">For help in formatting remote output, see [about_Remote_Output](about_Remote_Output.md).</span></span>

- <span data-ttu-id="0fe7f-171">如需遠端處理運作方式、如何管理遠端資料、特殊設定、安全性問題和其他常見問題的詳細資訊，請參閱 [about_Remote_FAQ](about_Remote_FAQ.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-171">For information about how remoting works, how to manage remote data, special configurations, security issues, and other frequently asked questions, see [about_Remote_FAQ](about_Remote_FAQ.md).</span></span>

- <span data-ttu-id="0fe7f-172">如需解決遠端處理錯誤的說明，請參閱 about_Remote_Troubleshooting。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-172">For help in resolving remoting errors, see about_Remote_Troubleshooting.</span></span>

- <span data-ttu-id="0fe7f-173">如需 Pssession 和持續連接的詳細資訊，請參閱 [about_PSSessions](about_PSSessions.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-173">For information about PSSessions and persistent connections, see [about_PSSessions](about_PSSessions.md).</span></span>

- <span data-ttu-id="0fe7f-174">如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe7f-174">For information about PowerShell background jobs, see [about_Jobs](about_Jobs.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="0fe7f-175">關鍵 字</span><span class="sxs-lookup"><span data-stu-id="0fe7f-175">KEYWORDS</span></span>

<span data-ttu-id="0fe7f-176">about_Remoting</span><span class="sxs-lookup"><span data-stu-id="0fe7f-176">about_Remoting</span></span>

## <a name="see-also"></a><span data-ttu-id="0fe7f-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fe7f-177">SEE ALSO</span></span>

[<span data-ttu-id="0fe7f-178">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="0fe7f-178">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="0fe7f-179">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="0fe7f-179">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="0fe7f-180">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="0fe7f-180">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="0fe7f-181">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="0fe7f-181">about_Remote_FAQ</span></span>](about_Remote_FAQ.md)

[<span data-ttu-id="0fe7f-182">about_Remote_TroubleShooting</span><span class="sxs-lookup"><span data-stu-id="0fe7f-182">about_Remote_TroubleShooting</span></span>](about_Remote_TroubleShooting.md)

[<span data-ttu-id="0fe7f-183">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="0fe7f-183">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="0fe7f-184">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="0fe7f-184">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="0fe7f-185">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="0fe7f-185">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="0fe7f-186">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="0fe7f-186">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
