---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 40d9da7d2e7e3233608b893b026c2b89c7155ab1
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "93205755"
---
# <span data-ttu-id="9e213-103">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="9e213-103">Enter-PSSession</span></span>

## <span data-ttu-id="9e213-104">概要</span><span class="sxs-lookup"><span data-stu-id="9e213-104">SYNOPSIS</span></span>
<span data-ttu-id="9e213-105">啟動遠端電腦的互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="9e213-105">Starts an interactive session with a remote computer.</span></span>

## <span data-ttu-id="9e213-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9e213-106">SYNTAX</span></span>

### <span data-ttu-id="9e213-107">ComputerName (預設值)</span><span class="sxs-lookup"><span data-stu-id="9e213-107">ComputerName (Default)</span></span>

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [-Credential <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="9e213-108">工作階段</span><span class="sxs-lookup"><span data-stu-id="9e213-108">Session</span></span>

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="9e213-109">Uri</span><span class="sxs-lookup"><span data-stu-id="9e213-109">Uri</span></span>

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [-Credential <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="9e213-110">InstanceId</span><span class="sxs-lookup"><span data-stu-id="9e213-110">InstanceId</span></span>

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### <span data-ttu-id="9e213-111">Id</span><span class="sxs-lookup"><span data-stu-id="9e213-111">Id</span></span>

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="9e213-112">名稱</span><span class="sxs-lookup"><span data-stu-id="9e213-112">Name</span></span>

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### <span data-ttu-id="9e213-113">VMId</span><span class="sxs-lookup"><span data-stu-id="9e213-113">VMId</span></span>

```
Enter-PSSession [-VMId] <Guid> -Credential <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### <span data-ttu-id="9e213-114">VMName</span><span class="sxs-lookup"><span data-stu-id="9e213-114">VMName</span></span>

```
Enter-PSSession [-VMName] <String> -Credential <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="9e213-115">ContainerId</span><span class="sxs-lookup"><span data-stu-id="9e213-115">ContainerId</span></span>

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## <span data-ttu-id="9e213-116">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9e213-116">DESCRIPTION</span></span>

<span data-ttu-id="9e213-117">`Enter-PSSession`Cmdlet 會啟動單一遠端電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-117">The `Enter-PSSession` cmdlet starts an interactive session with a single remote computer.</span></span> <span data-ttu-id="9e213-118">在會話期間，您輸入的命令會在遠端電腦上執行，就像您直接在遠端電腦上輸入一樣。</span><span class="sxs-lookup"><span data-stu-id="9e213-118">During the session, the commands that you type run on the remote computer, just as if you were typing directly on the remote computer.</span></span> <span data-ttu-id="9e213-119">您一次只能有一個互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="9e213-119">You can have only one interactive session at a time.</span></span>

<span data-ttu-id="9e213-120">通常，您會使用 **ComputerName** 參數來指定遠端電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e213-120">Typically, you use the **ComputerName** parameter to specify the name of the remote computer.</span></span>
<span data-ttu-id="9e213-121">不過，您也可以使用針對互動式會話使用 Cmdlet 所建立的會話 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="9e213-121">However, you can also use a session that you create by using the `New-PSSession` cmdlet for the interactive session.</span></span> <span data-ttu-id="9e213-122">不過，您無法使用 `Disconnect-PSSession` 、 `Connect-PSSession` 或 `Receive-PSSession` Cmdlet 來中斷與互動式會話的連線或重新連接。</span><span class="sxs-lookup"><span data-stu-id="9e213-122">However, you cannot use the `Disconnect-PSSession`, `Connect-PSSession`, or `Receive-PSSession` cmdlets to disconnect from or re-connect to an interactive session.</span></span>

<span data-ttu-id="9e213-123">若要結束互動式會話並中斷與遠端電腦的連線，請使用 `Exit-PSSession` Cmdlet 或輸入 `exit` 。</span><span class="sxs-lookup"><span data-stu-id="9e213-123">To end the interactive session and disconnect from the remote computer, use the `Exit-PSSession` cmdlet, or type `exit`.</span></span>

## <span data-ttu-id="9e213-124">範例</span><span class="sxs-lookup"><span data-stu-id="9e213-124">EXAMPLES</span></span>

### <span data-ttu-id="9e213-125">範例1：啟動互動式會話</span><span class="sxs-lookup"><span data-stu-id="9e213-125">Example 1: Start an interactive session</span></span>

```
PS C:\> Enter-PSSession
[localhost]: PS C:\>
```

<span data-ttu-id="9e213-126">此命令會在本機電腦上啟動互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="9e213-126">This command starts an interactive session on the local computer.</span></span> <span data-ttu-id="9e213-127">命令提示字元的變更，指出您現在在不同的工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="9e213-127">The command prompt changes to indicate that you are now running commands in a different session.</span></span>

<span data-ttu-id="9e213-128">您輸入的命令會在新的工作階段中執行，而結果會以文字傳回預設的工作階段。</span><span class="sxs-lookup"><span data-stu-id="9e213-128">The commands that you enter run in the new session, and the results are returned to the default session as text.</span></span>

### <span data-ttu-id="9e213-129">範例2：使用互動式會話</span><span class="sxs-lookup"><span data-stu-id="9e213-129">Example 2: Work with an interactive session</span></span>

<span data-ttu-id="9e213-130">第一個命令會使用指令 `Enter-PSSession` 程式來啟動 Server01 遠端電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-130">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with Server01, a remote computer.</span></span> <span data-ttu-id="9e213-131">當工作階段啟動時，命令提示字元會變成包含電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="9e213-131">When the session starts, the command prompt changes to include the computer name.</span></span>
<span data-ttu-id="9e213-132">第二個命令會取得 Windows PowerShell 的進程，並將輸出重新導向至 Process.txt 的檔案。</span><span class="sxs-lookup"><span data-stu-id="9e213-132">The second command gets the Windows PowerShell process and redirects the output to the Process.txt file.</span></span> <span data-ttu-id="9e213-133">命令會提交給遠端電腦，且此檔案會儲存在遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="9e213-133">The command is submitted to the remote computer, and the file is saved on the remote computer.</span></span>
<span data-ttu-id="9e213-134">第三個命令使用 **Exit** 關鍵字結束互動式會話，並關閉連接。</span><span class="sxs-lookup"><span data-stu-id="9e213-134">The third command uses the **Exit** keyword to end the interactive session and close the connection.</span></span>
<span data-ttu-id="9e213-135">第四個命令確認 Process.txt 檔案位於遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="9e213-135">The fourth command confirms that the Process.txt file is on the remote computer.</span></span> <span data-ttu-id="9e213-136">`Get-ChildItem`本機電腦上的 ( "dir" ) 命令找不到該檔案。</span><span class="sxs-lookup"><span data-stu-id="9e213-136">A `Get-ChildItem` ("dir") command on the local computer cannot find the file.</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS C:\>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

<span data-ttu-id="9e213-137">此命令會顯示如何在遠端電腦中使用互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="9e213-137">This command shows how to work in an interactive session with a remote computer.</span></span>

### <span data-ttu-id="9e213-138">範例3：使用 Session 參數</span><span class="sxs-lookup"><span data-stu-id="9e213-138">Example 3: Use the Session parameter</span></span>

```powershell
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
[Server01]: PS C:\>
```

<span data-ttu-id="9e213-139">這些命令使用的 **Session** 參數 `Enter-PSSession` ，在現有的 Windows PowerShell 會話中執行互動式會話 ( **PSSession** ) 。</span><span class="sxs-lookup"><span data-stu-id="9e213-139">These commands use the **Session** parameter of `Enter-PSSession` to run the interactive session in an existing Windows PowerShell session ( **PSSession** ).</span></span>

### <span data-ttu-id="9e213-140">範例4：啟動互動式會話，並指定埠和認證參數</span><span class="sxs-lookup"><span data-stu-id="9e213-140">Example 4: Start an interactive session and specify the Port and Credential parameters</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS C:\>
```

<span data-ttu-id="9e213-141">此命令會啟動 Server01 電腦的互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="9e213-141">This command starts an interactive session with the Server01 computer.</span></span> <span data-ttu-id="9e213-142">它會使用 **port** 參數來指定埠，並使用 **Credential** 參數來指定具有連線到遠端電腦之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9e213-142">It uses the **Port** parameter to specify the port and the **Credential** parameter to specify the account of a user who has permission to connect to the remote computer.</span></span>

### <span data-ttu-id="9e213-143">範例5：停止互動式會話</span><span class="sxs-lookup"><span data-stu-id="9e213-143">Example 5: Stop an interactive session</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS C:\> Exit-PSSession
PS C:\>
```

<span data-ttu-id="9e213-144">此範例顯示如何啟動和停止互動式工作階段。</span><span class="sxs-lookup"><span data-stu-id="9e213-144">This example shows how to start and stop an interactive session.</span></span> <span data-ttu-id="9e213-145">第一個命令會使用 `Enter-PSSession` Cmdlet 來啟動 Server01 電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-145">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

<span data-ttu-id="9e213-146">第二個命令會使用 `Exit-PSSession` Cmdlet 來結束會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-146">The second command uses the `Exit-PSSession` cmdlet to end the session.</span></span> <span data-ttu-id="9e213-147">您也可以使用 **Exit** 關鍵字結束互動式會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-147">You can also use the **Exit** keyword to end the interactive session.</span></span> <span data-ttu-id="9e213-148">`Exit-PSSession` 和 **Exit** 有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="9e213-148">`Exit-PSSession` and **Exit** have the same effect.</span></span>

## <span data-ttu-id="9e213-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9e213-149">PARAMETERS</span></span>

### <span data-ttu-id="9e213-150">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="9e213-150">-AllowRedirection</span></span>

<span data-ttu-id="9e213-151">允許重新導向此連線至替代「統一資源識別項 (URI)」。</span><span class="sxs-lookup"><span data-stu-id="9e213-151">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="9e213-152">依預設，不允許重新導向。</span><span class="sxs-lookup"><span data-stu-id="9e213-152">By default, redirection is not allowed.</span></span>

<span data-ttu-id="9e213-153">使用 **ConnectionURI** 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。</span><span class="sxs-lookup"><span data-stu-id="9e213-153">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="9e213-154">根據預設，Windows PowerShell 不會重新導向連線，但是您可以使用此參數允許它重新導向連線。</span><span class="sxs-lookup"><span data-stu-id="9e213-154">By default, Windows PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="9e213-155">您也可以變更 **MaximumConnectionRedirectionCount** 工作階段選項值，限制連線重新導向的次數。</span><span class="sxs-lookup"><span data-stu-id="9e213-155">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="9e213-156">使用 Cmdlet 的 **MaximumRedirection** 參數， `New-PSSessionOption` 或設定喜好設定變數的 **MaximumConnectionRedirectionCount** 屬性 `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="9e213-156">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="9e213-157">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="9e213-157">The default value is 5.</span></span>

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

### <span data-ttu-id="9e213-158">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="9e213-158">-ApplicationName</span></span>

<span data-ttu-id="9e213-159">指定連線 URI 的應用程式名稱區段。</span><span class="sxs-lookup"><span data-stu-id="9e213-159">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="9e213-160">當您沒有在命令中使用 **ConnectionURI** 參數時，請使用這個參數來指定應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="9e213-160">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="9e213-161">預設值是 `$PSSessionApplicationName` 本機電腦上喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="9e213-161">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="9e213-162">若未定義此喜好設定變數，則預設值是 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="9e213-162">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="9e213-163">這個值適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="9e213-163">This value is appropriate for most uses.</span></span> <span data-ttu-id="9e213-164">如需詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="9e213-164">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="9e213-165">**WinRM** 服務會使用應用程式名稱來選取接聽程式，以服務連線要求。</span><span class="sxs-lookup"><span data-stu-id="9e213-165">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="9e213-166">此參數的值應該符合遠端電腦上接聽程式之 **URLPrefix** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9e213-166">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="9e213-167">-Authentication</span><span class="sxs-lookup"><span data-stu-id="9e213-167">-Authentication</span></span>

<span data-ttu-id="9e213-168">指定用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="9e213-168">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="9e213-169">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="9e213-169">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9e213-170">預設</span><span class="sxs-lookup"><span data-stu-id="9e213-170">Default</span></span>
- <span data-ttu-id="9e213-171">基本</span><span class="sxs-lookup"><span data-stu-id="9e213-171">Basic</span></span>
- <span data-ttu-id="9e213-172">Credssp</span><span class="sxs-lookup"><span data-stu-id="9e213-172">Credssp</span></span>
- <span data-ttu-id="9e213-173">Digest</span><span class="sxs-lookup"><span data-stu-id="9e213-173">Digest</span></span>
- <span data-ttu-id="9e213-174">Kerberos</span><span class="sxs-lookup"><span data-stu-id="9e213-174">Kerberos</span></span>
- <span data-ttu-id="9e213-175">交涉</span><span class="sxs-lookup"><span data-stu-id="9e213-175">Negotiate</span></span>
- <span data-ttu-id="9e213-176">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="9e213-176">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="9e213-177">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="9e213-177">The default value is Default.</span></span>

<span data-ttu-id="9e213-178">CredSSP 驗證僅適用于 Windows Vista、Windows Server 2008 和更新版本的 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="9e213-178">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="9e213-179">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="9e213-179">For more information about the values of this parameter, see [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="9e213-180">注意：使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="9e213-180">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="9e213-181">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="9e213-181">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="9e213-182">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="9e213-182">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="9e213-183">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="9e213-183">-CertificateThumbprint</span></span>

<span data-ttu-id="9e213-184">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="9e213-184">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="9e213-185">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="9e213-185">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="9e213-186">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="9e213-186">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="9e213-187">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="9e213-187">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="9e213-188">若要取得憑證，請使用 `Get-Item` `Get-ChildItem` Windows PowerShell Cert：磁片磁碟機中的或命令。</span><span class="sxs-lookup"><span data-stu-id="9e213-188">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the Windows PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="9e213-189">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="9e213-189">-ComputerName</span></span>

<span data-ttu-id="9e213-190">指定電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="9e213-190">Specifies a computer name.</span></span> <span data-ttu-id="9e213-191">此 Cmdlet 會啟動與指定遠端電腦的互動式會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-191">This cmdlet starts an interactive session with the specified remote computer.</span></span> <span data-ttu-id="9e213-192">僅輸入電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="9e213-192">Enter only one computer name.</span></span> <span data-ttu-id="9e213-193">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="9e213-193">The default is the local computer.</span></span>

<span data-ttu-id="9e213-194">輸入電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="9e213-194">Type the NetBIOS name, the IP address, or the fully qualified domain name of the computer.</span></span> <span data-ttu-id="9e213-195">您也可以使用管線將電腦名稱稱傳送至 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="9e213-195">You can also pipe a computer name to `Enter-PSSession`.</span></span>

<span data-ttu-id="9e213-196">若要在 **ComputerName** 參數的值中使用 IP 位址，命令必須包含 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="9e213-196">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="9e213-197">此外，必須將電腦設定為使用 HTTPS 傳輸，或必須在本機電腦的 WinRM TrustedHosts 清單中包含遠端電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="9e213-197">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="9e213-198">如需將電腦名稱稱新增到 TrustedHosts 清單的指示，請參閱 [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md)中的「如何將電腦新增到信任的主機清單」。</span><span class="sxs-lookup"><span data-stu-id="9e213-198">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="9e213-199">注意：在 Windows Vista 和更新版本的 Windows 作業系統中，若要在 **ComputerName** 參數的值中包含本機電腦，您必須使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9e213-199">Note: In Windows Vista and later versions of the Windows operating system, to include the local computer in the value of the **ComputerName** parameter, you must start Windows PowerShell with the Run as administrator option.</span></span>

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

### <span data-ttu-id="9e213-200">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="9e213-200">-ConfigurationName</span></span>

<span data-ttu-id="9e213-201">指定用於互動式工作階段的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="9e213-201">Specifies the session configuration that is used for the interactive session.</span></span>

<span data-ttu-id="9e213-202">輸入工作階段設定的設定名稱或完整資源 URI。</span><span class="sxs-lookup"><span data-stu-id="9e213-202">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="9e213-203">如果您只指定設定名稱，則會在前面加上下列架構 URI： `http://schemas.microsoft.com/powershell` 。</span><span class="sxs-lookup"><span data-stu-id="9e213-203">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="9e213-204">工作階段的工作階段設定是位於遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="9e213-204">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="9e213-205">如果遠端電腦上沒有指定的工作階段設定，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="9e213-205">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="9e213-206">預設值是 `$PSSessionConfigurationName` 本機電腦上喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="9e213-206">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="9e213-207">若未設定此喜好設定變數，則預設為 Microsoft.PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9e213-207">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="9e213-208">如需詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="9e213-208">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

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

### <span data-ttu-id="9e213-209">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="9e213-209">-ConnectionUri</span></span>

<span data-ttu-id="9e213-210">指定定義會話之連接端點的 URI。</span><span class="sxs-lookup"><span data-stu-id="9e213-210">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="9e213-211">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="9e213-211">The URI must be fully qualified.</span></span> <span data-ttu-id="9e213-212">這個字串的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="9e213-212">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="9e213-213">預設值如下：</span><span class="sxs-lookup"><span data-stu-id="9e213-213">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="9e213-214">如果您未指定 **ConnectionURI** ，可以使用 **UseSSL** 、 **ComputerName** 、 **Port** 及 **ApplicationName** 參數來指定 **ConnectionURI** 值。</span><span class="sxs-lookup"><span data-stu-id="9e213-214">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="9e213-215">URI 的 Transport 區段有效值為 HTTP 與 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="9e213-215">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="9e213-216">如果您指定具有傳輸區段的連線 URI，但未指定埠，則會使用標準埠：80（適用于 HTTP）和443（適用于 HTTPS）來建立會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-216">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created by using standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="9e213-217">若要使用預設連接埠於 Windows PowerShell 遠端功能，請為 HTTP 指定連接埠 5985，或是為 HTTPS 指定連接埠 5986。</span><span class="sxs-lookup"><span data-stu-id="9e213-217">To use the default ports for Windows PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="9e213-218">若目的地電腦將連線重新導向至不同 URI，除非您在命令中使用 **AllowRedirection** 參數，否則 Windows PowerShell 會禁止重新導向。</span><span class="sxs-lookup"><span data-stu-id="9e213-218">If the destination computer redirects the connection to a different URI, Windows PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

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

### <span data-ttu-id="9e213-219">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="9e213-219">-ContainerId</span></span>

<span data-ttu-id="9e213-220">指定容器的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9e213-220">Specifies the ID of a container.</span></span>

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

### <span data-ttu-id="9e213-221">-Credential</span><span class="sxs-lookup"><span data-stu-id="9e213-221">-Credential</span></span>

<span data-ttu-id="9e213-222">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9e213-222">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="9e213-223">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="9e213-223">The default is the current user.</span></span>

<span data-ttu-id="9e213-224">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="9e213-224">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="9e213-225">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="9e213-225">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="9e213-226">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="9e213-226">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="9e213-227">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="9e213-227">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="9e213-228">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="9e213-228">-EnableNetworkAccess</span></span>

<span data-ttu-id="9e213-229">指出此 Cmdlet 會將互動式安全性權杖新增至回送會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-229">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="9e213-230">互動式權杖可讓您在會從其他電腦取得資料的回送工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="9e213-230">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="9e213-231">例如，您可以在會將 XML 檔案從遠端電腦複製到本機電腦的工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="9e213-231">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="9e213-232">回送會話是在同一部電腦上產生和結束的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="9e213-232">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="9e213-233">若要建立回送會話，請省略 **ComputerName** 參數，或將其值設為。</span><span class="sxs-lookup"><span data-stu-id="9e213-233">To create a loopback session, omit the **ComputerName** parameter or set its value to .</span></span> <span data-ttu-id="9e213-234"> (點) 、localhost 或本機電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e213-234">(dot), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="9e213-235">根據預設，系統會使用網路權杖建立回送會話，這可能不會提供足夠的許可權來驗證遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="9e213-235">By default, loopback sessions are created by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="9e213-236">**EnableNetworkAccess** 參數只在回送工作階段中有效。</span><span class="sxs-lookup"><span data-stu-id="9e213-236">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="9e213-237">如果您在遠端電腦上建立會話時使用 **EnableNetworkAccess** ，則命令會成功，但是會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="9e213-237">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="9e213-238">您也可以允許回送工作階段中的遠端存取，方式是使用 **CredSSP** 參數的 **Authentication** 值，這樣會把工作階段認證委派給其他電腦。</span><span class="sxs-lookup"><span data-stu-id="9e213-238">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="9e213-239">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9e213-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="9e213-240">-Id</span><span class="sxs-lookup"><span data-stu-id="9e213-240">-Id</span></span>

<span data-ttu-id="9e213-241">指定現有工作階段的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9e213-241">Specifies the ID of an existing session.</span></span> <span data-ttu-id="9e213-242">`Enter-PSSession` 針對互動式會話使用指定的會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-242">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="9e213-243">若要尋找會話的識別碼，請使用 `Get-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9e213-243">To find the ID of a session, use the `Get-PSSession` cmdlet.</span></span>

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

### <span data-ttu-id="9e213-244">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="9e213-244">-InstanceId</span></span>

<span data-ttu-id="9e213-245">指定現有工作階段的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="9e213-245">Specifies the instance ID of an existing session.</span></span> <span data-ttu-id="9e213-246">`Enter-PSSession` 針對互動式會話使用指定的會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-246">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="9e213-247">執行個體識別碼是 GUID。</span><span class="sxs-lookup"><span data-stu-id="9e213-247">The instance ID is a GUID.</span></span> <span data-ttu-id="9e213-248">若要尋找會話的實例識別碼，請使用 `Get-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9e213-248">To find the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="9e213-249">您也可以使用 **Session** 、 **Name** 或 **ID** 參數來指定現有的會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-249">You can also use the **Session** , **Name** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="9e213-250">或者，您可以使用 **ComputerName** 參數來啟動暫時會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-250">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

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

### <span data-ttu-id="9e213-251">-Name</span><span class="sxs-lookup"><span data-stu-id="9e213-251">-Name</span></span>

<span data-ttu-id="9e213-252">指定現有工作階段的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="9e213-252">Specifies the friendly name of an existing session.</span></span> <span data-ttu-id="9e213-253">`Enter-PSSession` 針對互動式會話使用指定的會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-253">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="9e213-254">如果您指定的名稱符合多個工作階段，此命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="9e213-254">If the name that you specify matches more than one session, the command fails.</span></span> <span data-ttu-id="9e213-255">您也可以使用 **Session** 、 **InstanceID** 或 **ID** 參數來指定現有的會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-255">You can also use the **Session** , **InstanceID** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="9e213-256">或者，您可以使用 **ComputerName** 參數來啟動暫時會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-256">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

<span data-ttu-id="9e213-257">若要建立會話的易記名稱，請使用 Cmdlet 的 **name** 參數 `New-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="9e213-257">To establish a friendly name for a session, use the **Name** parameter of the `New-PSSession` cmdlet.</span></span>

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

### <span data-ttu-id="9e213-258">-Port</span><span class="sxs-lookup"><span data-stu-id="9e213-258">-Port</span></span>

<span data-ttu-id="9e213-259">指定遠端電腦上用於此命令的網路埠。</span><span class="sxs-lookup"><span data-stu-id="9e213-259">Specifies the network port on the remote computer that is used for this command.</span></span> <span data-ttu-id="9e213-260">若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="9e213-260">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="9e213-261">預設的埠是5985，也就是 HTTP 的 WinRM 埠和5986，也就是 HTTPS 的 WinRM 埠。</span><span class="sxs-lookup"><span data-stu-id="9e213-261">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="9e213-262">使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。</span><span class="sxs-lookup"><span data-stu-id="9e213-262">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="9e213-263">使用下列命令來設定接聽程式：</span><span class="sxs-lookup"><span data-stu-id="9e213-263">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="9e213-264">除非必要，否則請勿使用 **Port** 參數。</span><span class="sxs-lookup"><span data-stu-id="9e213-264">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="9e213-265">命令中的連接埠設定會套用到所有電腦或命令執行所在工作階段。</span><span class="sxs-lookup"><span data-stu-id="9e213-265">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="9e213-266">替代的連接埠設定可能使得命令無法在全部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="9e213-266">An alternate port setting might prevent the command from running on all computers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9e213-267">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="9e213-267">-RunAsAdministrator</span></span>

<span data-ttu-id="9e213-268">指出 **PSSession** 以系統管理員身分執行。</span><span class="sxs-lookup"><span data-stu-id="9e213-268">Indicates that the **PSSession** runs as administrator.</span></span>

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

### <span data-ttu-id="9e213-269">-Session</span><span class="sxs-lookup"><span data-stu-id="9e213-269">-Session</span></span>

<span data-ttu-id="9e213-270">指定用於互動式會話的 Windows PowerShell 會話 ( **PSSession** ) 。</span><span class="sxs-lookup"><span data-stu-id="9e213-270">Specifies a Windows PowerShell session ( **PSSession** ) to use for the interactive session.</span></span> <span data-ttu-id="9e213-271">這個參數接受工作階段物件。</span><span class="sxs-lookup"><span data-stu-id="9e213-271">This parameter takes a session object.</span></span> <span data-ttu-id="9e213-272">您也可以使用 **Name** 、 **InstanceID** 或 **ID** 參數來指定 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="9e213-272">You can also use the **Name** , **InstanceID** , or **ID** parameters to specify a **PSSession** .</span></span>

<span data-ttu-id="9e213-273">輸入包含會話物件的變數，或輸入可建立或取得會話物件的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。</span><span class="sxs-lookup"><span data-stu-id="9e213-273">Enter a variable that contains a session object or a command that creates or gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="9e213-274">您也可以使用管線將會話物件傳送至 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="9e213-274">You can also pipe a session object to `Enter-PSSession`.</span></span> <span data-ttu-id="9e213-275">您只能使用此參數提交一個 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="9e213-275">You can submit only one **PSSession** by using this parameter.</span></span> <span data-ttu-id="9e213-276">如果您輸入的變數包含一個以上的 **PSSession** ，命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="9e213-276">If you enter a variable that contains more than one **PSSession** , the command fails.</span></span>

<span data-ttu-id="9e213-277">當您使用 `Exit-PSSession` 或 **EXIT** 關鍵字時，互動式會話會結束，但您建立的 **PSSession** 會保持開啟且可供使用。</span><span class="sxs-lookup"><span data-stu-id="9e213-277">When you use `Exit-PSSession` or the **EXIT** keyword, the interactive session ends, but the **PSSession** that you created remains open and available for use.</span></span>

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

### <span data-ttu-id="9e213-278">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="9e213-278">-SessionOption</span></span>

<span data-ttu-id="9e213-279">設定工作階段的進階選項。</span><span class="sxs-lookup"><span data-stu-id="9e213-279">Sets advanced options for the session.</span></span> <span data-ttu-id="9e213-280">輸入 **SessionOption** 物件（例如您使用 Cmdlet 建立的物件 `New-PSSessionOption` ），或輸入雜湊表，其中索引鍵為會話選項名稱，而值為會話選項值。</span><span class="sxs-lookup"><span data-stu-id="9e213-280">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="9e213-281">選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。</span><span class="sxs-lookup"><span data-stu-id="9e213-281">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="9e213-282">否則，將以工作階段設定中設定的選項建立預設值。</span><span class="sxs-lookup"><span data-stu-id="9e213-282">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="9e213-283">會話選項值的優先順序高於 `$PSSessionOption` 喜好設定變數和會話設定中設定之會話的預設值。</span><span class="sxs-lookup"><span data-stu-id="9e213-283">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="9e213-284">不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。</span><span class="sxs-lookup"><span data-stu-id="9e213-284">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="9e213-285">如需會話選項的描述（包括預設值），請參閱 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="9e213-285">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="9e213-286">如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="9e213-286">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="9e213-287">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="9e213-287">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="9e213-288">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="9e213-288">-UseSSL</span></span>

<span data-ttu-id="9e213-289">指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來建立與遠端電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="9e213-289">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="9e213-290">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="9e213-290">By default, SSL is not used.</span></span>

<span data-ttu-id="9e213-291">WS-Management 會加密透過網路傳輸的所有 Windows PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="9e213-291">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="9e213-292">**UseSSL** 參數是額外的保護，可跨 HTTPS 連接（而非 HTTP 連線）傳送資料。</span><span class="sxs-lookup"><span data-stu-id="9e213-292">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="9e213-293">如果您使用此參數，但是命令所用的埠上無法使用 SSL，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="9e213-293">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="9e213-294">-VMId</span><span class="sxs-lookup"><span data-stu-id="9e213-294">-VMId</span></span>

<span data-ttu-id="9e213-295">指定虛擬機器的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9e213-295">Specifies the ID of a virtual machine.</span></span>

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

### <span data-ttu-id="9e213-296">-VMName</span><span class="sxs-lookup"><span data-stu-id="9e213-296">-VMName</span></span>

<span data-ttu-id="9e213-297">指定虛擬機器的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e213-297">Specifies the name of a virtual machine.</span></span>

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

### <span data-ttu-id="9e213-298">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9e213-298">CommonParameters</span></span>

<span data-ttu-id="9e213-299">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9e213-299">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9e213-300">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9e213-300">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9e213-301">輸入</span><span class="sxs-lookup"><span data-stu-id="9e213-301">INPUTS</span></span>

### <span data-ttu-id="9e213-302">System.string，System.object。 PSSession。</span><span class="sxs-lookup"><span data-stu-id="9e213-302">System.String, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="9e213-303">您可以使用管線將電腦名稱稱（字串）或會話物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9e213-303">You can pipe a computer name, as a string, or a session object to this cmdlet.</span></span>

## <span data-ttu-id="9e213-304">輸出</span><span class="sxs-lookup"><span data-stu-id="9e213-304">OUTPUTS</span></span>

### <span data-ttu-id="9e213-305">無</span><span class="sxs-lookup"><span data-stu-id="9e213-305">None</span></span>

<span data-ttu-id="9e213-306">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="9e213-306">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="9e213-307">注意</span><span class="sxs-lookup"><span data-stu-id="9e213-307">NOTES</span></span>

<span data-ttu-id="9e213-308">若要連線遠端電腦，您必須是遠端電腦上 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="9e213-308">To connect to a remote computer, you must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="9e213-309">若要在本機電腦上啟動互動式會話，您必須使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9e213-309">To start an interactive session on the local computer, you must start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="9e213-310">當您使用時 `Enter-PSSession` ，遠端電腦上的使用者設定檔會用於互動式會話。</span><span class="sxs-lookup"><span data-stu-id="9e213-310">When you use `Enter-PSSession`, your user profile on the remote computer is used for the interactive session.</span></span> <span data-ttu-id="9e213-311">遠端使用者設定檔中的命令，包括用來新增 PowerShell 模組的命令，以及變更命令提示字元的命令，會在顯示遠端提示字元之前執行。</span><span class="sxs-lookup"><span data-stu-id="9e213-311">The commands in the remote user profile, including commands to add PowerShell modules and to change the command prompt, run before the remote prompt is displayed.</span></span>

<span data-ttu-id="9e213-312">`Enter-PSSession` 針對互動式會話使用本機電腦上的 UI 文化特性設定。</span><span class="sxs-lookup"><span data-stu-id="9e213-312">`Enter-PSSession` uses the UI culture setting on the local computer for the interactive session.</span></span> <span data-ttu-id="9e213-313">若要尋找本機 UI 文化特性，請使用 `$UICulture` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="9e213-313">To find the local UI culture, use the `$UICulture` automatic variable.</span></span>

<span data-ttu-id="9e213-314">`Enter-PSSession` 需要 `Get-Command` 、 `Out-Default` 和 `Exit-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9e213-314">`Enter-PSSession` requires the `Get-Command`, `Out-Default`, and `Exit-PSSession` cmdlets.</span></span> <span data-ttu-id="9e213-315">如果遠端電腦上的會話設定中未包含這些 Cmdlet，則 `Enter-PSSession` 命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="9e213-315">If these cmdlets are not included in the session configuration on the remote computer, the `Enter-PSSession` commands fails.</span></span>

<span data-ttu-id="9e213-316">不同于 `Invoke-Command` ，這會在命令傳送到遠端電腦之前剖析並解讀命令， `Enter-PSSession` 而不需要解釋，就會將命令直接傳送至遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="9e213-316">Unlike `Invoke-Command`, which parses and interprets the commands before it sends them to the remote computer, `Enter-PSSession` sends the commands directly to the remote computer without interpretation.</span></span>

<span data-ttu-id="9e213-317">如果您想要輸入的會話正忙於處理命令，則 PowerShell 回應命令之前可能會有延遲 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="9e213-317">If the session you want to enter is busy processing a command, there might be a delay before PowerShell responds to the `Enter-PSSession` command.</span></span> <span data-ttu-id="9e213-318">您會在會話可用時立即連線。</span><span class="sxs-lookup"><span data-stu-id="9e213-318">You are connected as soon as the session is available.</span></span> <span data-ttu-id="9e213-319">若要取消 `Enter-PSSession` 命令，請按下<kbd>CTRL</kbd> + <kbd>C</kbd>。</span><span class="sxs-lookup"><span data-stu-id="9e213-319">To cancel the `Enter-PSSession` command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

## <span data-ttu-id="9e213-320">相關連結</span><span class="sxs-lookup"><span data-stu-id="9e213-320">RELATED LINKS</span></span>

[<span data-ttu-id="9e213-321">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="9e213-321">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="9e213-322">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="9e213-322">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="9e213-323">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="9e213-323">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="9e213-324">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="9e213-324">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="9e213-325">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="9e213-325">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="9e213-326">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="9e213-326">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="9e213-327">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="9e213-327">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="9e213-328">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="9e213-328">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="9e213-329">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="9e213-329">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="9e213-330">about_Remote</span><span class="sxs-lookup"><span data-stu-id="9e213-330">about_Remote</span></span>](About/about_Remote.md)
