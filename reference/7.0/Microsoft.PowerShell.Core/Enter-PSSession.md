---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: f5b8d82b2f2a30c176ab01be42201434842a0454
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "93205760"
---
# <span data-ttu-id="b88d1-103">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="b88d1-103">Enter-PSSession</span></span>

## <span data-ttu-id="b88d1-104">概要</span><span class="sxs-lookup"><span data-stu-id="b88d1-104">SYNOPSIS</span></span>
<span data-ttu-id="b88d1-105">啟動遠端電腦的互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="b88d1-105">Starts an interactive session with a remote computer.</span></span>

## <span data-ttu-id="b88d1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b88d1-106">SYNTAX</span></span>

### <span data-ttu-id="b88d1-107">ComputerName (預設值)</span><span class="sxs-lookup"><span data-stu-id="b88d1-107">ComputerName (Default)</span></span>

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="b88d1-108">SSHHost</span><span class="sxs-lookup"><span data-stu-id="b88d1-108">SSHHost</span></span>

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [<CommonParameters>]
```

### <span data-ttu-id="b88d1-109">工作階段</span><span class="sxs-lookup"><span data-stu-id="b88d1-109">Session</span></span>

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="b88d1-110">Uri</span><span class="sxs-lookup"><span data-stu-id="b88d1-110">Uri</span></span>

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="b88d1-111">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b88d1-111">InstanceId</span></span>

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### <span data-ttu-id="b88d1-112">Id</span><span class="sxs-lookup"><span data-stu-id="b88d1-112">Id</span></span>

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="b88d1-113">名稱</span><span class="sxs-lookup"><span data-stu-id="b88d1-113">Name</span></span>

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### <span data-ttu-id="b88d1-114">VMId</span><span class="sxs-lookup"><span data-stu-id="b88d1-114">VMId</span></span>

```
Enter-PSSession [-VMId] <Guid> [-Credential] <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### <span data-ttu-id="b88d1-115">VMName</span><span class="sxs-lookup"><span data-stu-id="b88d1-115">VMName</span></span>

```
Enter-PSSession [-VMName] <String> [-Credential] <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="b88d1-116">ContainerId</span><span class="sxs-lookup"><span data-stu-id="b88d1-116">ContainerId</span></span>

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## <span data-ttu-id="b88d1-117">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b88d1-117">DESCRIPTION</span></span>

<span data-ttu-id="b88d1-118">`Enter-PSSession`Cmdlet 會啟動單一遠端電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-118">The `Enter-PSSession` cmdlet starts an interactive session with a single remote computer.</span></span>
<span data-ttu-id="b88d1-119">在會話期間，您輸入的命令會在遠端電腦上執行，就像您直接在遠端電腦上輸入一樣。</span><span class="sxs-lookup"><span data-stu-id="b88d1-119">During the session, the commands that you type run on the remote computer, just as if you were typing directly on the remote computer.</span></span> <span data-ttu-id="b88d1-120">您一次只能有一個互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="b88d1-120">You can have only one interactive session at a time.</span></span>

<span data-ttu-id="b88d1-121">通常，您會使用 **ComputerName** 參數來指定遠端電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="b88d1-121">Typically, you use the **ComputerName** parameter to specify the name of the remote computer.</span></span>
<span data-ttu-id="b88d1-122">不過，您也可以使用針對互動式會話使用 Cmdlet 所建立的會話 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-122">However, you can also use a session that you create by using the `New-PSSession` cmdlet for the interactive session.</span></span> <span data-ttu-id="b88d1-123">不過，您無法使用 `Disconnect-PSSession` 、 `Connect-PSSession` 或 `Receive-PSSession` Cmdlet 來中斷與互動式會話的連線或重新連接。</span><span class="sxs-lookup"><span data-stu-id="b88d1-123">However, you cannot use the `Disconnect-PSSession`, `Connect-PSSession`, or `Receive-PSSession` cmdlets to disconnect from or re-connect to an interactive session.</span></span>

<span data-ttu-id="b88d1-124">從 PowerShell 6.0 開始，如果本機電腦上有 SSH 可供使用，且遠端電腦已設定 PowerShell SSH 端點，您就可以使用安全殼層 (SSH) 來建立與遠端電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="b88d1-124">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="b88d1-125">以 SSH 為基礎的 PowerShell 遠端會話的優點是，它可以跨多個平臺運作， (Windows、Linux、macOS) 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-125">The benefit an SSH based PowerShell remote session is that it works across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="b88d1-126">針對以 SSH 為基礎的遠端處理，您可以使用 **HostName** 參數設定來指定遠端電腦和相關的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="b88d1-126">For SSH based remoting you use the **HostName** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="b88d1-127">如需有關如何設定 PowerShell SSH 遠端的詳細資訊，請參閱透過 [SSH 的 Powershell 遠端](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)功能。</span><span class="sxs-lookup"><span data-stu-id="b88d1-127">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="b88d1-128">若要結束互動式會話並中斷與遠端電腦的連線，請使用 `Exit-PSSession` Cmdlet 或輸入 `exit` 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-128">To end the interactive session and disconnect from the remote computer, use the `Exit-PSSession` cmdlet, or type `exit`.</span></span>

## <span data-ttu-id="b88d1-129">範例</span><span class="sxs-lookup"><span data-stu-id="b88d1-129">EXAMPLES</span></span>

### <span data-ttu-id="b88d1-130">範例1：啟動互動式會話</span><span class="sxs-lookup"><span data-stu-id="b88d1-130">Example 1: Start an interactive session</span></span>

```
PS> Enter-PSSession
[localhost]: PS>
```

<span data-ttu-id="b88d1-131">此命令會在本機電腦上啟動互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="b88d1-131">This command starts an interactive session on the local computer.</span></span> <span data-ttu-id="b88d1-132">命令提示字元的變更，指出您現在在不同的工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="b88d1-132">The command prompt changes to indicate that you are now running commands in a different session.</span></span>

<span data-ttu-id="b88d1-133">您輸入的命令會在新的工作階段中執行，而結果會以文字傳回預設的工作階段。</span><span class="sxs-lookup"><span data-stu-id="b88d1-133">The commands that you enter run in the new session, and the results are returned to the default session as text.</span></span>

### <span data-ttu-id="b88d1-134">範例2：使用互動式會話</span><span class="sxs-lookup"><span data-stu-id="b88d1-134">Example 2: Work with an interactive session</span></span>

<span data-ttu-id="b88d1-135">第一個命令會使用指令 `Enter-PSSession` 程式來啟動 Server01 遠端電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-135">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with Server01, a remote computer.</span></span> <span data-ttu-id="b88d1-136">當工作階段啟動時，命令提示字元會變成包含電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="b88d1-136">When the session starts, the command prompt changes to include the computer name.</span></span>

<span data-ttu-id="b88d1-137">第二個命令取得 PowerShell 處理程序，並將輸出重新導向到 Process.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="b88d1-137">The second command gets the PowerShell process and redirects the output to the Process.txt file.</span></span> <span data-ttu-id="b88d1-138">命令會提交給遠端電腦，且此檔案會儲存在遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="b88d1-138">The command is submitted to the remote computer, and the file is saved on the remote computer.</span></span>

<span data-ttu-id="b88d1-139">第三個命令使用 **Exit** 關鍵字結束互動式會話，並關閉連接。</span><span class="sxs-lookup"><span data-stu-id="b88d1-139">The third command uses the **Exit** keyword to end the interactive session and close the connection.</span></span>
<span data-ttu-id="b88d1-140">第四個命令確認 Process.txt 檔案位於遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="b88d1-140">The fourth command confirms that the Process.txt file is on the remote computer.</span></span> <span data-ttu-id="b88d1-141">`Get-ChildItem`本機電腦上的 ( "dir" ) 命令找不到該檔案。</span><span class="sxs-lookup"><span data-stu-id="b88d1-141">A `Get-ChildItem` ("dir") command on the local computer cannot find the file.</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

<span data-ttu-id="b88d1-142">此命令會顯示如何在遠端電腦中使用互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="b88d1-142">This command shows how to work in an interactive session with a remote computer.</span></span>

### <span data-ttu-id="b88d1-143">範例3：使用 Session 參數</span><span class="sxs-lookup"><span data-stu-id="b88d1-143">Example 3: Use the Session parameter</span></span>

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

<span data-ttu-id="b88d1-144">這些命令使用的 **Session** 參數 `Enter-PSSession` ，在現有的 PowerShell 會話中執行互動式會話， ( **PSSession** ) 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-144">These commands use the **Session** parameter of `Enter-PSSession` to run the interactive session in an existing PowerShell session ( **PSSession** ).</span></span>

### <span data-ttu-id="b88d1-145">範例4：啟動互動式會話，並指定埠和認證參數</span><span class="sxs-lookup"><span data-stu-id="b88d1-145">Example 4: Start an interactive session and specify the Port and Credential parameters</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

<span data-ttu-id="b88d1-146">此命令會啟動 Server01 電腦的互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="b88d1-146">This command starts an interactive session with the Server01 computer.</span></span> <span data-ttu-id="b88d1-147">它會使用 **port** 參數來指定埠，並使用 **Credential** 參數來指定具有連線到遠端電腦之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="b88d1-147">It uses the **Port** parameter to specify the port and the **Credential** parameter to specify the account of a user who has permission to connect to the remote computer.</span></span>

### <span data-ttu-id="b88d1-148">範例5：停止互動式會話</span><span class="sxs-lookup"><span data-stu-id="b88d1-148">Example 5: Stop an interactive session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

<span data-ttu-id="b88d1-149">此範例顯示如何啟動和停止互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="b88d1-149">This example shows how to start and stop an interactive session.</span></span> <span data-ttu-id="b88d1-150">第一個命令會使用 `Enter-PSSession` Cmdlet 來啟動 Server01 電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-150">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

<span data-ttu-id="b88d1-151">第二個命令會使用 `Exit-PSSession` Cmdlet 來結束會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-151">The second command uses the `Exit-PSSession` cmdlet to end the session.</span></span> <span data-ttu-id="b88d1-152">您也可以使用 **Exit** 關鍵字結束互動式會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-152">You can also use the **Exit** keyword to end the interactive session.</span></span> <span data-ttu-id="b88d1-153">`Exit-PSSession` 和 **Exit** 有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="b88d1-153">`Exit-PSSession` and **Exit** have the same effect.</span></span>

### <span data-ttu-id="b88d1-154">範例6：使用 SSH 啟動互動式會話</span><span class="sxs-lookup"><span data-stu-id="b88d1-154">Example 6: Start an interactive session using SSH</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="b88d1-155">此範例說明如何使用安全殼層 (SSH) 來啟動互動式會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-155">This example shows how to start an interactive session using Secure Shell (SSH).</span></span> <span data-ttu-id="b88d1-156">如果在遠端電腦上設定 SSH 以提示輸入密碼，您將會收到密碼提示。</span><span class="sxs-lookup"><span data-stu-id="b88d1-156">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span>
<span data-ttu-id="b88d1-157">否則，您必須使用以 SSH 金鑰為基礎的使用者驗證。</span><span class="sxs-lookup"><span data-stu-id="b88d1-157">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="b88d1-158">範例7：使用 SSH 啟動互動式會話，並指定埠和使用者驗證金鑰</span><span class="sxs-lookup"><span data-stu-id="b88d1-158">Example 7: Start an interactive session using SSH and specify the Port and user authentication key</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="b88d1-159">此範例說明如何使用 SSH 啟動互動式會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-159">This example shows how to start an interactive session using SSH.</span></span> <span data-ttu-id="b88d1-160">它會使用 **port** 參數來指定要使用的埠，並使用 **KeyFilePath** 參數來指定用來在遠端電腦上驗證使用者的 RSA 金鑰。</span><span class="sxs-lookup"><span data-stu-id="b88d1-160">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to authenticate the user on the remote computer.</span></span>

## <span data-ttu-id="b88d1-161">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b88d1-161">PARAMETERS</span></span>

### <span data-ttu-id="b88d1-162">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="b88d1-162">-AllowRedirection</span></span>

<span data-ttu-id="b88d1-163">允許重新導向此連線至替代「統一資源識別項 (URI)」。</span><span class="sxs-lookup"><span data-stu-id="b88d1-163">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="b88d1-164">依預設，不允許重新導向。</span><span class="sxs-lookup"><span data-stu-id="b88d1-164">By default, redirection is not allowed.</span></span>

<span data-ttu-id="b88d1-165">使用 **ConnectionURI** 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。</span><span class="sxs-lookup"><span data-stu-id="b88d1-165">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="b88d1-166">根據預設，PowerShell 不會重新導向連線，但是您可以使用此參數允許它重新導向連接。</span><span class="sxs-lookup"><span data-stu-id="b88d1-166">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="b88d1-167">您也可以變更 **MaximumConnectionRedirectionCount** 工作階段選項值，限制連線重新導向的次數。</span><span class="sxs-lookup"><span data-stu-id="b88d1-167">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="b88d1-168">使用 Cmdlet 的 **MaximumRedirection** 參數， `New-PSSessionOption` 或設定喜好設定變數的 **MaximumConnectionRedirectionCount** 屬性 `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-168">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="b88d1-169">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="b88d1-169">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-170">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="b88d1-170">-ApplicationName</span></span>

<span data-ttu-id="b88d1-171">指定連線 URI 的應用程式名稱區段。</span><span class="sxs-lookup"><span data-stu-id="b88d1-171">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="b88d1-172">當您沒有在命令中使用 **ConnectionURI** 參數時，請使用這個參數來指定應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="b88d1-172">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="b88d1-173">預設值是 `$PSSessionApplicationName` 本機電腦上喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="b88d1-173">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="b88d1-174">若未定義此喜好設定變數，則預設值是 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="b88d1-174">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="b88d1-175">這個值適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="b88d1-175">This value is appropriate for most uses.</span></span> <span data-ttu-id="b88d1-176">如需詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b88d1-176">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="b88d1-177">**WinRM** 服務會使用應用程式名稱來選取接聽程式，以服務連線要求。</span><span class="sxs-lookup"><span data-stu-id="b88d1-177">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="b88d1-178">此參數的值應該符合遠端電腦上接聽程式之 **URLPrefix** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b88d1-178">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-179">-Authentication</span><span class="sxs-lookup"><span data-stu-id="b88d1-179">-Authentication</span></span>

<span data-ttu-id="b88d1-180">指定用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="b88d1-180">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="b88d1-181">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="b88d1-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b88d1-182">預設</span><span class="sxs-lookup"><span data-stu-id="b88d1-182">Default</span></span>
- <span data-ttu-id="b88d1-183">基本</span><span class="sxs-lookup"><span data-stu-id="b88d1-183">Basic</span></span>
- <span data-ttu-id="b88d1-184">Credssp</span><span class="sxs-lookup"><span data-stu-id="b88d1-184">Credssp</span></span>
- <span data-ttu-id="b88d1-185">Digest</span><span class="sxs-lookup"><span data-stu-id="b88d1-185">Digest</span></span>
- <span data-ttu-id="b88d1-186">Kerberos</span><span class="sxs-lookup"><span data-stu-id="b88d1-186">Kerberos</span></span>
- <span data-ttu-id="b88d1-187">交涉</span><span class="sxs-lookup"><span data-stu-id="b88d1-187">Negotiate</span></span>
- <span data-ttu-id="b88d1-188">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="b88d1-188">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="b88d1-189">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="b88d1-189">The default value is Default.</span></span>

<span data-ttu-id="b88d1-190">CredSSP 驗證僅適用于 Windows Vista、Windows Server 2008 和更新版本的 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="b88d1-190">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="b88d1-191">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="b88d1-191">For more information about the values of this parameter, see [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="b88d1-192">注意：使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="b88d1-192">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="b88d1-193">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="b88d1-193">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="b88d1-194">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="b88d1-194">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-195">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="b88d1-195">-CertificateThumbprint</span></span>

<span data-ttu-id="b88d1-196">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="b88d1-196">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="b88d1-197">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="b88d1-197">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="b88d1-198">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="b88d1-198">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="b88d1-199">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="b88d1-199">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="b88d1-200">若要取得憑證，請使用 `Get-Item` `Get-ChildItem` PowerShell Cert：磁片磁碟機中的或命令。</span><span class="sxs-lookup"><span data-stu-id="b88d1-200">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-201">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b88d1-201">-ComputerName</span></span>

<span data-ttu-id="b88d1-202">指定電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="b88d1-202">Specifies a computer name.</span></span> <span data-ttu-id="b88d1-203">此 Cmdlet 會啟動與指定遠端電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-203">This cmdlet starts an interactive session with the specified remote computer.</span></span> <span data-ttu-id="b88d1-204">僅輸入電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="b88d1-204">Enter only one computer name.</span></span> <span data-ttu-id="b88d1-205">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="b88d1-205">The default is the local computer.</span></span>

<span data-ttu-id="b88d1-206">輸入電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="b88d1-206">Type the NetBIOS name, the IP address, or the fully qualified domain name of the computer.</span></span> <span data-ttu-id="b88d1-207">您也可以使用管線將電腦名稱稱傳送至 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-207">You can also pipe a computer name to `Enter-PSSession`.</span></span>

<span data-ttu-id="b88d1-208">若要在 **ComputerName** 參數的值中使用 IP 位址，命令必須包含 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="b88d1-208">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="b88d1-209">此外，必須將電腦設定為使用 HTTPS 傳輸，或必須在本機電腦的 WinRM TrustedHosts 清單中包含遠端電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="b88d1-209">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="b88d1-210">如需將電腦名稱稱新增到 TrustedHosts 清單的指示，請參閱 [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md)中的「如何將電腦新增到信任的主機清單」。</span><span class="sxs-lookup"><span data-stu-id="b88d1-210">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="b88d1-211">注意：在 Windows Vista 和更新版本的 Windows 作業系統中，若要在 **ComputerName** 參數的值中包含本機電腦，您必須使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b88d1-211">Note: In Windows Vista and later versions of the Windows operating system, to include the local computer in the value of the **ComputerName** parameter, you must start PowerShell with the Run as administrator option.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-212">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="b88d1-212">-ConfigurationName</span></span>

<span data-ttu-id="b88d1-213">指定用於互動式工作階段的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="b88d1-213">Specifies the session configuration that is used for the interactive session.</span></span>

<span data-ttu-id="b88d1-214">輸入工作階段設定的設定名稱或完整資源 URI。</span><span class="sxs-lookup"><span data-stu-id="b88d1-214">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="b88d1-215">如果您只指定設定名稱，則會在前面加上下列架構 URI： `http://schemas.microsoft.com/powershell` 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-215">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="b88d1-216">與 SSH 搭配使用時，會指定要在目標上使用的子系統，如 sshd_config 中所定義。</span><span class="sxs-lookup"><span data-stu-id="b88d1-216">When used with SSH, this specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="b88d1-217">SSH 的預設值是 `powershell` 子系統。</span><span class="sxs-lookup"><span data-stu-id="b88d1-217">The default value for SSH is the `powershell` subsystem.</span></span>

<span data-ttu-id="b88d1-218">工作階段的工作階段設定是位於遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="b88d1-218">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="b88d1-219">如果遠端電腦上沒有指定的工作階段設定，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="b88d1-219">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="b88d1-220">預設值是 `$PSSessionConfigurationName` 本機電腦上喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="b88d1-220">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="b88d1-221">若未設定此喜好設定變數，則預設為 Microsoft.PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b88d1-221">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="b88d1-222">如需詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b88d1-222">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-223">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="b88d1-223">-ConnectionUri</span></span>

<span data-ttu-id="b88d1-224">指定定義會話之連接端點的 URI。</span><span class="sxs-lookup"><span data-stu-id="b88d1-224">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="b88d1-225">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="b88d1-225">The URI must be fully qualified.</span></span> <span data-ttu-id="b88d1-226">這個字串的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="b88d1-226">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="b88d1-227">預設值如下：</span><span class="sxs-lookup"><span data-stu-id="b88d1-227">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="b88d1-228">如果您未指定 **ConnectionURI** ，可以使用 **UseSSL** 、 **ComputerName** 、 **Port** 及 **ApplicationName** 參數來指定 **ConnectionURI** 值。</span><span class="sxs-lookup"><span data-stu-id="b88d1-228">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="b88d1-229">URI 的 Transport 區段有效值為 HTTP 與 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b88d1-229">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="b88d1-230">如果您指定具有傳輸區段的連線 URI，但未指定埠，則會使用標準埠：80（適用于 HTTP）和443（適用于 HTTPS）來建立會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-230">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created by using standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="b88d1-231">若要使用 PowerShell 遠端的預設埠，請指定 HTTP 的埠5985或 HTTPS 的5986。</span><span class="sxs-lookup"><span data-stu-id="b88d1-231">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="b88d1-232">如果目的地電腦將連線重新導向至不同的 URI，除非您在命令中使用 **AllowRedirection** 參數，否則 PowerShell 會禁止重新導向。</span><span class="sxs-lookup"><span data-stu-id="b88d1-232">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri
Parameter Sets: Uri
Aliases: URI, CU

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-233">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="b88d1-233">-ContainerId</span></span>

<span data-ttu-id="b88d1-234">指定容器的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b88d1-234">Specifies the ID of a container.</span></span>

```yaml
Type: System.String
Parameter Sets: ContainerId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-235">-Credential</span><span class="sxs-lookup"><span data-stu-id="b88d1-235">-Credential</span></span>

<span data-ttu-id="b88d1-236">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="b88d1-236">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="b88d1-237">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="b88d1-237">The default is the current user.</span></span>

<span data-ttu-id="b88d1-238">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-238">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="b88d1-239">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="b88d1-239">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="b88d1-240">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="b88d1-240">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="b88d1-241">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="b88d1-241">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: 1
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-242">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="b88d1-242">-EnableNetworkAccess</span></span>

<span data-ttu-id="b88d1-243">指出此 Cmdlet 會將互動式安全性權杖新增至回送會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-243">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="b88d1-244">互動式權杖可讓您在會從其他電腦取得資料的回送工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="b88d1-244">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="b88d1-245">例如，您可以在會將 XML 檔案從遠端電腦複製到本機電腦的工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="b88d1-245">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="b88d1-246">回送會話是在同一部電腦上產生和結束的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-246">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="b88d1-247">若要建立回送會話，請省略 **ComputerName** 參數，或將其值設為。</span><span class="sxs-lookup"><span data-stu-id="b88d1-247">To create a loopback session, omit the **ComputerName** parameter or set its value to .</span></span> <span data-ttu-id="b88d1-248"> (點) 、localhost 或本機電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="b88d1-248">(dot), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="b88d1-249">根據預設，系統會使用網路權杖建立回送會話，這可能不會提供足夠的許可權來驗證遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="b88d1-249">By default, loopback sessions are created by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="b88d1-250">**EnableNetworkAccess** 參數只在回送工作階段中有效。</span><span class="sxs-lookup"><span data-stu-id="b88d1-250">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="b88d1-251">如果您在遠端電腦上建立會話時使用 **EnableNetworkAccess** ，則命令會成功，但是會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="b88d1-251">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="b88d1-252">您也可以允許回送工作階段中的遠端存取，方式是使用 **CredSSP** 參數的 **Authentication** 值，這樣會把工作階段認證委派給其他電腦。</span><span class="sxs-lookup"><span data-stu-id="b88d1-252">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="b88d1-253">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="b88d1-253">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-254">-HostName</span><span class="sxs-lookup"><span data-stu-id="b88d1-254">-HostName</span></span>

<span data-ttu-id="b88d1-255">指定安全殼層 (SSH) 型連接的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="b88d1-255">Specifies a computer name for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="b88d1-256">這類似于 **ComputerName** 參數，不同之處在于遠端電腦的連線是使用 SSH 而非 Windows WinRM 進行。</span><span class="sxs-lookup"><span data-stu-id="b88d1-256">This is similar to the **ComputerName** parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span> <span data-ttu-id="b88d1-257">此參數支援使用格式將使用者名稱和（或）埠指定為主機名參數值的一部分 `user@hostname:port` 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-257">This parameter supports specifying the user name and/or port as part of the host name parameter value using the form `user@hostname:port`.</span></span> <span data-ttu-id="b88d1-258">指定為主機名一部分的使用者名稱和（或）埠，會優先于 `-UserName` 和 `-Port` 參數（如果有指定的話）。</span><span class="sxs-lookup"><span data-stu-id="b88d1-258">The user name and/or port specified as part of the host name takes precedence over the `-UserName` and `-Port` parameters, if specified.</span></span> <span data-ttu-id="b88d1-259">這可讓您將多個電腦名稱稱傳遞給這個參數，其中有些會有特定的使用者名稱和（或）埠，而其他則使用和參數中的使用者名稱和/或埠 `-UserName` `-Port` 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-259">This allows passing multiple computer names to this parameter where some have specific user names and/or ports, while others use the user name and/or port from the `-UserName` and `-Port` parameters.</span></span>

<span data-ttu-id="b88d1-260">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b88d1-260">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-261">-Id</span><span class="sxs-lookup"><span data-stu-id="b88d1-261">-Id</span></span>

<span data-ttu-id="b88d1-262">指定現有工作階段的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b88d1-262">Specifies the ID of an existing session.</span></span> <span data-ttu-id="b88d1-263">`Enter-PSSession` 針對互動式會話使用指定的會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-263">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="b88d1-264">若要尋找會話的識別碼，請使用 `Get-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b88d1-264">To find the ID of a session, use the `Get-PSSession` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-265">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="b88d1-265">-InstanceId</span></span>

<span data-ttu-id="b88d1-266">指定現有工作階段的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="b88d1-266">Specifies the instance ID of an existing session.</span></span> <span data-ttu-id="b88d1-267">`Enter-PSSession` 針對互動式會話使用指定的會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-267">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="b88d1-268">執行個體識別碼是 GUID。</span><span class="sxs-lookup"><span data-stu-id="b88d1-268">The instance ID is a GUID.</span></span> <span data-ttu-id="b88d1-269">若要尋找會話的實例識別碼，請使用 `Get-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b88d1-269">To find the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="b88d1-270">您也可以使用 **Session** 、 **Name** 或 **ID** 參數來指定現有的會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-270">You can also use the **Session** , **Name** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="b88d1-271">或者，您可以使用 **ComputerName** 參數來啟動暫時會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-271">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

```yaml
Type: System.Guid
Parameter Sets: InstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-272">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="b88d1-272">-KeyFilePath</span></span>

<span data-ttu-id="b88d1-273">指定安全殼層 (SSH) 用來驗證遠端電腦上使用者的金鑰檔路徑。</span><span class="sxs-lookup"><span data-stu-id="b88d1-273">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="b88d1-274">SSH 允許透過私用/公開金鑰來執行使用者驗證，作為基本密碼驗證的替代方案。</span><span class="sxs-lookup"><span data-stu-id="b88d1-274">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="b88d1-275">如果遠端電腦設定為進行金鑰驗證，則此參數可以用來提供識別使用者的金鑰。</span><span class="sxs-lookup"><span data-stu-id="b88d1-275">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="b88d1-276">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b88d1-276">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-277">-Name</span><span class="sxs-lookup"><span data-stu-id="b88d1-277">-Name</span></span>

<span data-ttu-id="b88d1-278">指定現有工作階段的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="b88d1-278">Specifies the friendly name of an existing session.</span></span> <span data-ttu-id="b88d1-279">`Enter-PSSession` 針對互動式會話使用指定的會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-279">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="b88d1-280">如果您指定的名稱符合多個工作階段，此命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="b88d1-280">If the name that you specify matches more than one session, the command fails.</span></span> <span data-ttu-id="b88d1-281">您也可以使用 **Session** 、 **InstanceID** 或 **ID** 參數來指定現有的會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-281">You can also use the **Session** , **InstanceID** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="b88d1-282">或者，您可以使用 **ComputerName** 參數來啟動暫時會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-282">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

<span data-ttu-id="b88d1-283">若要建立會話的易記名稱，請使用 Cmdlet 的 **name** 參數 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-283">To establish a friendly name for a session, use the **Name** parameter of the `New-PSSession` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-284">-Port</span><span class="sxs-lookup"><span data-stu-id="b88d1-284">-Port</span></span>

<span data-ttu-id="b88d1-285">指定遠端電腦上用於此命令的網路埠。</span><span class="sxs-lookup"><span data-stu-id="b88d1-285">Specifies the network port on the remote computer that is used for this command.</span></span>

<span data-ttu-id="b88d1-286">在 PowerShell 6.0 中，此參數包含在支援安全殼層 (SSH) 連線的 **HostName** 參數集中。</span><span class="sxs-lookup"><span data-stu-id="b88d1-286">In PowerShell 6.0 this parameter was inlcuded in the **HostName** parameter set which supports Secure Shell (SSH) connections.</span></span>

<span data-ttu-id="b88d1-287">**WinRM (ComputerName 參數集)**</span><span class="sxs-lookup"><span data-stu-id="b88d1-287">**WinRM (ComputerName parameter set)**</span></span>

<span data-ttu-id="b88d1-288">若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="b88d1-288">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="b88d1-289">預設的埠是5985，也就是 HTTP 的 WinRM 埠和5986，也就是 HTTPS 的 WinRM 埠。</span><span class="sxs-lookup"><span data-stu-id="b88d1-289">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="b88d1-290">使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。</span><span class="sxs-lookup"><span data-stu-id="b88d1-290">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="b88d1-291">使用下列命令來設定接聽程式：</span><span class="sxs-lookup"><span data-stu-id="b88d1-291">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="b88d1-292">除非必要，否則請勿使用 **Port** 參數。</span><span class="sxs-lookup"><span data-stu-id="b88d1-292">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="b88d1-293">命令中的連接埠設定會套用到所有電腦或命令執行所在工作階段。</span><span class="sxs-lookup"><span data-stu-id="b88d1-293">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="b88d1-294">替代的連接埠設定可能使得命令無法在全部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="b88d1-294">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="b88d1-295">**SSH (HostName 參數集)**</span><span class="sxs-lookup"><span data-stu-id="b88d1-295">**SSH (HostName parameter set)**</span></span>

<span data-ttu-id="b88d1-296">若要連線到遠端電腦，必須使用 SSH 服務 (SSHD) 設定遠端電腦，而且必須在連線使用的埠上進行接聽。</span><span class="sxs-lookup"><span data-stu-id="b88d1-296">To connect to a remote computer, the remote computer must be configured with the SSH service (SSHD) and must be listening on the port that the connection uses.</span></span> <span data-ttu-id="b88d1-297">SSH 的預設埠為22。</span><span class="sxs-lookup"><span data-stu-id="b88d1-297">The default port for SSH is 22.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-298">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="b88d1-298">-RunAsAdministrator</span></span>

<span data-ttu-id="b88d1-299">指出 **PSSession** 以系統管理員身分執行。</span><span class="sxs-lookup"><span data-stu-id="b88d1-299">Indicates that the **PSSession** runs as administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-300">-Session</span><span class="sxs-lookup"><span data-stu-id="b88d1-300">-Session</span></span>

<span data-ttu-id="b88d1-301">指定要用於互動式會話 ( **PSSession** ) 的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-301">Specifies a PowerShell session ( **PSSession** ) to use for the interactive session.</span></span> <span data-ttu-id="b88d1-302">這個參數接受工作階段物件。</span><span class="sxs-lookup"><span data-stu-id="b88d1-302">This parameter takes a session object.</span></span> <span data-ttu-id="b88d1-303">您也可以使用 **Name** 、 **InstanceID** 或 **ID** 參數來指定 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-303">You can also use the **Name** , **InstanceID** , or **ID** parameters to specify a **PSSession** .</span></span>

<span data-ttu-id="b88d1-304">輸入包含會話物件的變數，或輸入可建立或取得會話物件的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="b88d1-304">Enter a variable that contains a session object or a command that creates or gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="b88d1-305">您也可以使用管線將會話物件傳送至 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-305">You can also pipe a session object to `Enter-PSSession`.</span></span> <span data-ttu-id="b88d1-306">您只能使用此參數提交一個 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-306">You can submit only one **PSSession** by using this parameter.</span></span> <span data-ttu-id="b88d1-307">如果您輸入的變數包含一個以上的 **PSSession** ，命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="b88d1-307">If you enter a variable that contains more than one **PSSession** , the command fails.</span></span>

<span data-ttu-id="b88d1-308">當您使用 `Exit-PSSession` 或 **EXIT** 關鍵字時，互動式會話會結束，但您建立的 **PSSession** 會保持開啟且可供使用。</span><span class="sxs-lookup"><span data-stu-id="b88d1-308">When you use `Exit-PSSession` or the **EXIT** keyword, the interactive session ends, but the **PSSession** that you created remains open and available for use.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-309">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="b88d1-309">-SessionOption</span></span>

<span data-ttu-id="b88d1-310">設定工作階段的進階選項。</span><span class="sxs-lookup"><span data-stu-id="b88d1-310">Sets advanced options for the session.</span></span> <span data-ttu-id="b88d1-311">輸入 **SessionOption** 物件（例如您使用 Cmdlet 建立的物件 `New-PSSessionOption` ），或輸入雜湊表，其中索引鍵為會話選項名稱，而值為會話選項值。</span><span class="sxs-lookup"><span data-stu-id="b88d1-311">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="b88d1-312">選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。</span><span class="sxs-lookup"><span data-stu-id="b88d1-312">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="b88d1-313">否則，將以工作階段設定中設定的選項建立預設值。</span><span class="sxs-lookup"><span data-stu-id="b88d1-313">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="b88d1-314">會話選項值的優先順序高於 `$PSSessionOption` 喜好設定變數和會話設定中設定之會話的預設值。</span><span class="sxs-lookup"><span data-stu-id="b88d1-314">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="b88d1-315">不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。</span><span class="sxs-lookup"><span data-stu-id="b88d1-315">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="b88d1-316">如需會話選項的描述（包括預設值），請參閱 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-316">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="b88d1-317">如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="b88d1-317">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="b88d1-318">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="b88d1-318">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-319">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="b88d1-319">-SSHTransport</span></span>

<span data-ttu-id="b88d1-320">指出使用安全殼層 (SSH) 來建立遠端連線。</span><span class="sxs-lookup"><span data-stu-id="b88d1-320">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="b88d1-321">PowerShell 預設會使用 Windows WinRM 連接到遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="b88d1-321">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="b88d1-322">此參數會強制 PowerShell 使用 HostName 參數集來建立以 SSH 為基礎的遠端連線。</span><span class="sxs-lookup"><span data-stu-id="b88d1-322">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="b88d1-323">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b88d1-323">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-324">-子系統</span><span class="sxs-lookup"><span data-stu-id="b88d1-324">-Subsystem</span></span>

<span data-ttu-id="b88d1-325">指定用於新 **PSSession** 的 SSH 子系統。</span><span class="sxs-lookup"><span data-stu-id="b88d1-325">Specifies the SSH subsystem used for the new **PSSession** .</span></span>

<span data-ttu-id="b88d1-326">這會指定要在目標上使用的子系統，如 sshd_config 中所定義。</span><span class="sxs-lookup"><span data-stu-id="b88d1-326">This specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="b88d1-327">子系統會使用預先定義的參數啟動特定版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b88d1-327">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span> <span data-ttu-id="b88d1-328">如果指定的子系統不存在於遠端電腦上，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="b88d1-328">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="b88d1-329">如果未使用此參數，則預設值為 ' powershell ' 子系統。</span><span class="sxs-lookup"><span data-stu-id="b88d1-329">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-330">-UserName</span><span class="sxs-lookup"><span data-stu-id="b88d1-330">-UserName</span></span>

<span data-ttu-id="b88d1-331">指定用於在遠端電腦上建立會話之帳戶的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="b88d1-331">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="b88d1-332">使用者驗證方法將取決於遠端電腦上如何設定安全殼層 (SSH) 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-332">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="b88d1-333">如果 SSH 設定為基本密碼驗證，則系統會提示您輸入使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="b88d1-333">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="b88d1-334">如果設定 SSH 以進行金鑰型使用者驗證，則可透過 **KeyFilePath** 參數提供金鑰檔案路徑，而且不會出現任何密碼提示。</span><span class="sxs-lookup"><span data-stu-id="b88d1-334">If SSH is configured for key based user authentication then a key file path can be provided via the **KeyFilePath** parameter and no password prompt will occur.</span></span> <span data-ttu-id="b88d1-335">請注意，如果用戶端使用者金鑰檔位於 SSH 已知的位置，則金鑰型驗證不需要 **KeyFilePath** 參數，且使用者驗證會根據使用者名稱自動進行。</span><span class="sxs-lookup"><span data-stu-id="b88d1-335">Note that if the client user key file is located in an SSH known location then the **KeyFilePath** parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="b88d1-336">如需詳細資訊，請參閱關於金鑰型使用者驗證的 SSH 檔。</span><span class="sxs-lookup"><span data-stu-id="b88d1-336">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="b88d1-337">這不是必要的參數。</span><span class="sxs-lookup"><span data-stu-id="b88d1-337">This is not a required parameter.</span></span> <span data-ttu-id="b88d1-338">如果未指定 **UserName** 參數，則會使用目前登入的使用者名稱做為連接。</span><span class="sxs-lookup"><span data-stu-id="b88d1-338">If no **UserName** parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="b88d1-339">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b88d1-339">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-340">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="b88d1-340">-UseSSL</span></span>

<span data-ttu-id="b88d1-341">指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來建立與遠端電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="b88d1-341">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="b88d1-342">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="b88d1-342">By default, SSL is not used.</span></span>

<span data-ttu-id="b88d1-343">WS-Management 加密透過網路傳輸的所有 PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="b88d1-343">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="b88d1-344">**UseSSL** 參數是額外的保護，可跨 HTTPS 連接（而非 HTTP 連線）傳送資料。</span><span class="sxs-lookup"><span data-stu-id="b88d1-344">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="b88d1-345">如果您使用此參數，但是命令所用的埠上無法使用 SSL，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="b88d1-345">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-346">-VMId</span><span class="sxs-lookup"><span data-stu-id="b88d1-346">-VMId</span></span>

<span data-ttu-id="b88d1-347">指定虛擬機器的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b88d1-347">Specifies the ID of a virtual machine.</span></span>

```yaml
Type: System.Guid
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-348">-VMName</span><span class="sxs-lookup"><span data-stu-id="b88d1-348">-VMName</span></span>

<span data-ttu-id="b88d1-349">指定虛擬機器的名稱。</span><span class="sxs-lookup"><span data-stu-id="b88d1-349">Specifies the name of a virtual machine.</span></span>

```yaml
Type: System.String
Parameter Sets: VMName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b88d1-350">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b88d1-350">CommonParameters</span></span>

<span data-ttu-id="b88d1-351">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b88d1-351">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b88d1-352">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b88d1-352">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b88d1-353">輸入</span><span class="sxs-lookup"><span data-stu-id="b88d1-353">INPUTS</span></span>

### <span data-ttu-id="b88d1-354">System.string，System.object。 PSSession。</span><span class="sxs-lookup"><span data-stu-id="b88d1-354">System.String, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="b88d1-355">您可以使用管線將電腦名稱稱（字串）或會話物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b88d1-355">You can pipe a computer name, as a string, or a session object to this cmdlet.</span></span>

## <span data-ttu-id="b88d1-356">輸出</span><span class="sxs-lookup"><span data-stu-id="b88d1-356">OUTPUTS</span></span>

### <span data-ttu-id="b88d1-357">無</span><span class="sxs-lookup"><span data-stu-id="b88d1-357">None</span></span>

<span data-ttu-id="b88d1-358">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="b88d1-358">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="b88d1-359">注意</span><span class="sxs-lookup"><span data-stu-id="b88d1-359">NOTES</span></span>

<span data-ttu-id="b88d1-360">若要連線遠端電腦，您必須是遠端電腦上 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="b88d1-360">To connect to a remote computer, you must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="b88d1-361">若要在本機電腦上啟動互動式會話，您必須使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b88d1-361">To start an interactive session on the local computer, you must start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="b88d1-362">當您使用時 `Enter-PSSession` ，遠端電腦上的使用者設定檔會用於互動式會話。</span><span class="sxs-lookup"><span data-stu-id="b88d1-362">When you use `Enter-PSSession`, your user profile on the remote computer is used for the interactive session.</span></span> <span data-ttu-id="b88d1-363">遠端使用者設定檔中的命令，包括用來新增 PowerShell 模組的命令，以及變更命令提示字元的命令，會在顯示遠端提示字元之前執行。</span><span class="sxs-lookup"><span data-stu-id="b88d1-363">The commands in the remote user profile, including commands to add PowerShell modules and to change the command prompt, run before the remote prompt is displayed.</span></span>

<span data-ttu-id="b88d1-364">`Enter-PSSession` 針對互動式會話使用本機電腦上的 UI 文化特性設定。</span><span class="sxs-lookup"><span data-stu-id="b88d1-364">`Enter-PSSession` uses the UI culture setting on the local computer for the interactive session.</span></span> <span data-ttu-id="b88d1-365">若要尋找本機 UI 文化特性，請使用 `$UICulture` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="b88d1-365">To find the local UI culture, use the `$UICulture` automatic variable.</span></span>

<span data-ttu-id="b88d1-366">`Enter-PSSession` 需要 `Get-Command` 、 `Out-Default` 和 `Exit-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b88d1-366">`Enter-PSSession` requires the `Get-Command`, `Out-Default`, and `Exit-PSSession` cmdlets.</span></span> <span data-ttu-id="b88d1-367">如果遠端電腦上的會話設定中未包含這些 Cmdlet，則 `Enter-PSSession` 命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="b88d1-367">If these cmdlets are not included in the session configuration on the remote computer, the `Enter-PSSession` commands fails.</span></span>

<span data-ttu-id="b88d1-368">不同于 `Invoke-Command` ，這會在命令傳送到遠端電腦之前剖析並解讀命令， `Enter-PSSession` 而不需要解釋，就會將命令直接傳送至遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="b88d1-368">Unlike `Invoke-Command`, which parses and interprets the commands before it sends them to the remote computer, `Enter-PSSession` sends the commands directly to the remote computer without interpretation.</span></span>

<span data-ttu-id="b88d1-369">如果您想要輸入的會話正忙於處理命令，則 PowerShell 回應命令之前可能會有延遲 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="b88d1-369">If the session you want to enter is busy processing a command, there might be a delay before PowerShell responds to the `Enter-PSSession` command.</span></span> <span data-ttu-id="b88d1-370">您會在會話可用時立即連線。</span><span class="sxs-lookup"><span data-stu-id="b88d1-370">You are connected as soon as the session is available.</span></span> <span data-ttu-id="b88d1-371">若要取消 `Enter-PSSession` 命令，請按下<kbd>CTRL</kbd> + <kbd>C</kbd>。</span><span class="sxs-lookup"><span data-stu-id="b88d1-371">To cancel the `Enter-PSSession` command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="b88d1-372">從 PowerShell 6.0 開始包含 **主機名稱** 參數集。</span><span class="sxs-lookup"><span data-stu-id="b88d1-372">The **HostName** parameter set was included starting with PowerShell 6.0.</span></span> <span data-ttu-id="b88d1-373">已新增它，以根據安全殼層 (SSH) 提供 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="b88d1-373">It was added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="b88d1-374">在多個平臺上都支援 SSH 和 PowerShell (Windows、Linux、macOS) 和 PowerShell 遠端處理會在安裝和設定 PowerShell 和 SSH 的平臺上運作。</span><span class="sxs-lookup"><span data-stu-id="b88d1-374">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="b88d1-375">這與先前僅限 Windows 的遠端處理（以 WinRM 為基礎）和大部分的 WinRM 特定功能和限制都不適用。</span><span class="sxs-lookup"><span data-stu-id="b88d1-375">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="b88d1-376">例如，目前不支援 WinRM 型配額、會話選項、自訂端點設定以及中斷連接/重新連線功能。</span><span class="sxs-lookup"><span data-stu-id="b88d1-376">For example, WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="b88d1-377">如需有關如何設定 PowerShell SSH 遠端的詳細資訊，請參閱透過 [SSH 的 Powershell 遠端](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)功能。</span><span class="sxs-lookup"><span data-stu-id="b88d1-377">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="b88d1-378">在 PowerShell 7.1 之前，透過 SSH 進行遠端處理不支援第二躍點遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="b88d1-378">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="b88d1-379">這項功能僅限於使用 WinRM 的工作階段。</span><span class="sxs-lookup"><span data-stu-id="b88d1-379">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="b88d1-380">PowerShell 7.1 可讓 `Enter-PSSession` 與 `Enter-PSHostProcess` 在任何互動式遠端工作階段中作業。</span><span class="sxs-lookup"><span data-stu-id="b88d1-380">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <span data-ttu-id="b88d1-381">相關連結</span><span class="sxs-lookup"><span data-stu-id="b88d1-381">RELATED LINKS</span></span>

[<span data-ttu-id="b88d1-382">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="b88d1-382">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="b88d1-383">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="b88d1-383">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="b88d1-384">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="b88d1-384">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="b88d1-385">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="b88d1-385">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="b88d1-386">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="b88d1-386">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="b88d1-387">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="b88d1-387">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="b88d1-388">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="b88d1-388">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="b88d1-389">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="b88d1-389">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="b88d1-390">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="b88d1-390">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="b88d1-391">about_Remote</span><span class="sxs-lookup"><span data-stu-id="b88d1-391">about_Remote</span></span>](About/about_Remote.md)
