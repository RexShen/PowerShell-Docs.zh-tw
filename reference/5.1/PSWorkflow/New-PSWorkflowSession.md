---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowSession
ms.openlocfilehash: 995dd8a6df3ac8ebd7a204d2aefef3fa6aa71e14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202968"
---
# <span data-ttu-id="accb1-103">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="accb1-103">New-PSWorkflowSession</span></span>

## <span data-ttu-id="accb1-104">概要</span><span class="sxs-lookup"><span data-stu-id="accb1-104">SYNOPSIS</span></span>
<span data-ttu-id="accb1-105">建立工作流程工作階段。</span><span class="sxs-lookup"><span data-stu-id="accb1-105">Creates a workflow session.</span></span>

## <span data-ttu-id="accb1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="accb1-106">SYNTAX</span></span>

```
New-PSWorkflowSession [[-ComputerName] <String[]>] [-Credential <Object>] [-Name <String[]>] [-Port <Int32>]
 [-UseSSL] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-EnableNetworkAccess]
 [<CommonParameters>]
```

## <span data-ttu-id="accb1-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="accb1-107">DESCRIPTION</span></span>

<span data-ttu-id="accb1-108">此 `New-PSWorkflowSession` Cmdlet 會建立使用者管理的會話 ( **PSSession** ) ，特別針對執行 Windows PowerShell 工作流程而設計。</span><span class="sxs-lookup"><span data-stu-id="accb1-108">The `New-PSWorkflowSession` cmdlet creates a user-managed session ( **PSSession** ) that is especially designed for running Windows PowerShell workflows.</span></span> <span data-ttu-id="accb1-109">它使用 Microsoft.PowerShell.Workflow 工作階段設定，其中包含指令碼、型別與格式設定檔案，以及工作流程所需的選項。</span><span class="sxs-lookup"><span data-stu-id="accb1-109">It uses the Microsoft.PowerShell.Workflow session configuration, which includes scripts, type and formatting files, and options that are required for workflows.</span></span>

<span data-ttu-id="accb1-110">您可以使用 `New-PSWorkflowSession` 或其別名 `nwsn` 。</span><span class="sxs-lookup"><span data-stu-id="accb1-110">You can use `New-PSWorkflowSession` or its alias, `nwsn`.</span></span>

<span data-ttu-id="accb1-111">您也可以新增工作流程一般參數到此命令。</span><span class="sxs-lookup"><span data-stu-id="accb1-111">You can also add workflow common parameters to this command.</span></span> <span data-ttu-id="accb1-112">如需工作流程一般參數的詳細資訊，請參閱 [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="accb1-112">For more information about workflow common parameters, see [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)</span></span>

<span data-ttu-id="accb1-113">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="accb1-113">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="accb1-114">範例</span><span class="sxs-lookup"><span data-stu-id="accb1-114">EXAMPLES</span></span>

### <span data-ttu-id="accb1-115">範例1：在遠端電腦上建立工作流程會話</span><span class="sxs-lookup"><span data-stu-id="accb1-115">Example 1: Create a workflow session on a remote computer</span></span>

<span data-ttu-id="accb1-116">此範例會在 ServerNode01 遠端電腦上建立 **WorkflowTests** 會話。</span><span class="sxs-lookup"><span data-stu-id="accb1-116">This example creates the **WorkflowTests** session on the ServerNode01 remote computer.</span></span>

```powershell
$params = @{
    ComputerName = "ServerNode01"
    Name = "WorkflowTests"
    SessionOption = (New-PSSessionOption -OutputBufferingMode Drop)
}
New-PSWorkflowSession @params
```

<span data-ttu-id="accb1-117">**SessionOption** 參數的值是一個 `New-PSSessionOption` 命令，此命令會將會話中的輸出緩衝處理模式設定為 **Drop** 。</span><span class="sxs-lookup"><span data-stu-id="accb1-117">The value of the **SessionOption** parameter is a `New-PSSessionOption` command that sets the output buffering mode in the session to **Drop** .</span></span>

### <span data-ttu-id="accb1-118">範例2：在多部遠端電腦上建立工作流程會話</span><span class="sxs-lookup"><span data-stu-id="accb1-118">Example 2: Create workflow sessions on multiple remote computers</span></span>

<span data-ttu-id="accb1-119">此範例會在 ServerNode01 和 Server12 電腦上建立工作流程會話。</span><span class="sxs-lookup"><span data-stu-id="accb1-119">This example creates workflow sessions on the ServerNode01 and Server12 computers.</span></span> <span data-ttu-id="accb1-120">此命令會使用 **Credential** 參數，以網域系統管理員的權限執行。</span><span class="sxs-lookup"><span data-stu-id="accb1-120">The command uses the **Credential** parameter to run with the permissions of the domain administrator.</span></span>

```powershell
"ServerNode01", "Server12" |
    New-PSWorkflowSession -Name WorkflowSession -Credential Domain01\Admin01 -ThrottleLimit 150
```

<span data-ttu-id="accb1-121">此命令會使用 **ThrottleLimit** 參數，將每個命令的節流限制增加到 150。</span><span class="sxs-lookup"><span data-stu-id="accb1-121">The command uses the **ThrottleLimit** parameter to increase the per-command throttle limit to 150.</span></span>
<span data-ttu-id="accb1-122">此值的優先順序高於在 [] 中設定的預設節流限制（100 **）。**</span><span class="sxs-lookup"><span data-stu-id="accb1-122">This value takes precedence over the default throttle limit of 100 that is set in the **Microsoft.PowerShell.Workflow** session configuration.</span></span>

## <span data-ttu-id="accb1-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="accb1-123">PARAMETERS</span></span>

### <span data-ttu-id="accb1-124">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="accb1-124">-ApplicationName</span></span>

<span data-ttu-id="accb1-125">指定連線 URI 的應用程式名稱區段。</span><span class="sxs-lookup"><span data-stu-id="accb1-125">Specifies the application name segment of the connection URI.</span></span>

<span data-ttu-id="accb1-126">預設值是 `$PSSessionApplicationName` 本機電腦上喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="accb1-126">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="accb1-127">若未定義此喜好設定變數，則預設值是 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="accb1-127">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="accb1-128">這個值適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="accb1-128">This value is appropriate for most uses.</span></span> <span data-ttu-id="accb1-129">如需詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="accb1-129">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="accb1-130">WinRM 服務會使用應用程式名稱來選取要用來為連線要求提供服務的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="accb1-130">The WinRM service uses the application name to select a listener to service the connection request.</span></span>
<span data-ttu-id="accb1-131">此參數的值應該符合遠端電腦上接聽程式之 **URLPrefix** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="accb1-131">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="accb1-132">-Authentication</span><span class="sxs-lookup"><span data-stu-id="accb1-132">-Authentication</span></span>

<span data-ttu-id="accb1-133">指定用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="accb1-133">Specifies the mechanism that is used to authenticate the user credentials.</span></span>
<span data-ttu-id="accb1-134">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="accb1-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="accb1-135">預設</span><span class="sxs-lookup"><span data-stu-id="accb1-135">Default</span></span>
- <span data-ttu-id="accb1-136">基本</span><span class="sxs-lookup"><span data-stu-id="accb1-136">Basic</span></span>
- <span data-ttu-id="accb1-137">Credssp</span><span class="sxs-lookup"><span data-stu-id="accb1-137">Credssp</span></span>
- <span data-ttu-id="accb1-138">Digest</span><span class="sxs-lookup"><span data-stu-id="accb1-138">Digest</span></span>
- <span data-ttu-id="accb1-139">Kerberos</span><span class="sxs-lookup"><span data-stu-id="accb1-139">Kerberos</span></span>
- <span data-ttu-id="accb1-140">交涉</span><span class="sxs-lookup"><span data-stu-id="accb1-140">Negotiate</span></span>
- <span data-ttu-id="accb1-141">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="accb1-141">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="accb1-142">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="accb1-142">The default value is Default.</span></span>

<span data-ttu-id="accb1-143">CredSSP 驗證僅適用于 Windows Vista、Windows Server 2008 和更新版本的 Windows 作業系統。</span><span class="sxs-lookup"><span data-stu-id="accb1-143">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="accb1-144">如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。</span><span class="sxs-lookup"><span data-stu-id="accb1-144">For more information about the values of this parameter, see [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="accb1-145">認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="accb1-145">Credential Security Service Provider (CredSSP) authentication, in which the user credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="accb1-146">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="accb1-146">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="accb1-147">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="accb1-147">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="accb1-148">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="accb1-148">-CertificateThumbprint</span></span>

<span data-ttu-id="accb1-149">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="accb1-149">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="accb1-150">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="accb1-150">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="accb1-151">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="accb1-151">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="accb1-152">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="accb1-152">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="accb1-153">若要取得憑證指紋，請使用 `Get-Item` Cmdlet 或 `Get-ChildItem` Windows PowerShell Cert：磁片磁碟機中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="accb1-153">To get a certificate thumbprint, use the `Get-Item` cmdlet or the `Get-ChildItem` cmdlet in the Windows PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="accb1-154">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="accb1-154">-ComputerName</span></span>

<span data-ttu-id="accb1-155">建立 ( **PSSession** ) 至指定電腦的持續連線。</span><span class="sxs-lookup"><span data-stu-id="accb1-155">Creates a persistent connection ( **PSSession** ) to the specified computer.</span></span> <span data-ttu-id="accb1-156">如果您輸入多個電腦名稱稱，Windows PowerShell 會建立多個 **pssession** ，每一部電腦各一個。</span><span class="sxs-lookup"><span data-stu-id="accb1-156">If you enter multiple computer names, Windows PowerShell creates multiple **PSSessions** , one for each computer.</span></span> <span data-ttu-id="accb1-157">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="accb1-157">The default is the local computer.</span></span>

<span data-ttu-id="accb1-158">輸入一或多部遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="accb1-158">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span> <span data-ttu-id="accb1-159">若要指定本機電腦，請輸入電腦名稱、localhost 或句點 (.)。</span><span class="sxs-lookup"><span data-stu-id="accb1-159">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span> <span data-ttu-id="accb1-160">當電腦與使用者位於不同網域，則必須使用完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="accb1-160">When the computer is in a different domain than the user, the fully qualified domain name is required.</span></span> <span data-ttu-id="accb1-161">您也可以使用管線將電腦名稱稱（以引號括住）傳送至 `New-PSWorkflowSession` 。</span><span class="sxs-lookup"><span data-stu-id="accb1-161">You can also pipe a computer name, in quotation marks to `New-PSWorkflowSession`.</span></span>

<span data-ttu-id="accb1-162">若要在 **ComputerName** 參數的值中使用 IP 位址，命令必須包含 **Credential** 參數。</span><span class="sxs-lookup"><span data-stu-id="accb1-162">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="accb1-163">此外，必須將電腦設定為使用 HTTPS 傳輸，或必須在本機電腦的 WinRM TrustedHosts 清單中包含遠端電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="accb1-163">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="accb1-164">如需將電腦名稱稱新增到 TrustedHosts 清單的指示，請參閱 [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)中的「如何將電腦新增到信任的主機清單」。</span><span class="sxs-lookup"><span data-stu-id="accb1-164">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="accb1-165">-Credential</span><span class="sxs-lookup"><span data-stu-id="accb1-165">-Credential</span></span>

<span data-ttu-id="accb1-166">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="accb1-166">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="accb1-167">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="accb1-167">The default is the current user.</span></span> <span data-ttu-id="accb1-168">輸入使用者名稱，例如 User01、Domain01\User01 或 User@Domain.com ，或輸入 **PSCredential** 物件，例如 Cmdlet 所傳回的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="accb1-168">Type a user name, such as User01, Domain01\User01, or User@Domain.com, or enter a **PSCredential** object, such as one returned by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="accb1-169">當您輸入使用者名稱時，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="accb1-169">When you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="accb1-170">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="accb1-170">-EnableNetworkAccess</span></span>

<span data-ttu-id="accb1-171">指出此 Cmdlet 會將互動式安全性權杖新增至回送會話。</span><span class="sxs-lookup"><span data-stu-id="accb1-171">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="accb1-172">互動式權杖可讓您在會從其他電腦取得資料的回送工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="accb1-172">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="accb1-173">例如，您可以在會將 XML 檔案從遠端電腦複製到本機電腦的工作階段中執行命令。</span><span class="sxs-lookup"><span data-stu-id="accb1-173">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="accb1-174">回送會話是在同一部電腦上產生和結束的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="accb1-174">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="accb1-175">若要建立回送會話，請不要指定 **ComputerName** 參數，或將其值設為點、localhost 或本機電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="accb1-175">To create a loopback session, do not specify the **ComputerName** parameter or set its value to dot, localhost, or the name of the local computer.</span></span>

<span data-ttu-id="accb1-176">根據預設，會建立具有網路權杖的回送會話，這可能不會提供足夠的許可權來驗證遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="accb1-176">By default, loopback sessions are created that have a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="accb1-177">**EnableNetworkAccess** 參數只在回送工作階段中有效。</span><span class="sxs-lookup"><span data-stu-id="accb1-177">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="accb1-178">如果您在遠端電腦上建立會話時指定 **EnableNetworkAccess** 參數，則命令會成功，但是會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="accb1-178">If you specify the **EnableNetworkAccess** parameter when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="accb1-179">您也可以允許回送工作階段中的遠端存取，方式是使用 **CredSSP** 參數的 **Authentication** 值，這樣會把工作階段認證委派給其他電腦。</span><span class="sxs-lookup"><span data-stu-id="accb1-179">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="accb1-180">為了保護電腦免于惡意存取，具有互動式權杖的已中斷連線回送會話（使用 **EnableNetworkAccess** 參數所建立的權杖）只能從建立該會話的電腦重新連接。</span><span class="sxs-lookup"><span data-stu-id="accb1-180">To protect the computer from malicious access, disconnected loopback sessions that have interactive tokens, those created by using the **EnableNetworkAccess** parameter, can be reconnected only from the computer on which the session was created.</span></span> <span data-ttu-id="accb1-181">使用 CredSSP 驗證且已中斷連線的工作階段可從其他電腦重新連線。</span><span class="sxs-lookup"><span data-stu-id="accb1-181">Disconnected sessions that use CredSSP authentication can be reconnected from other computers.</span></span> <span data-ttu-id="accb1-182">如需詳細資訊，請參閱 `Disconnect-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="accb1-182">For more information, see the `Disconnect-PSSession` cmdlet.</span></span>

<span data-ttu-id="accb1-183">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="accb1-183">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="accb1-184">-Name</span><span class="sxs-lookup"><span data-stu-id="accb1-184">-Name</span></span>

<span data-ttu-id="accb1-185">指定工作流程工作階段的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="accb1-185">Specifies a friendly name for the workflow session.</span></span> <span data-ttu-id="accb1-186">您可以使用名稱搭配其他 Cmdlet，例如 `Get-PSSession` 和 `Enter-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="accb1-186">You can use the name with other cmdlets, such as `Get-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="accb1-187">該名稱對電腦或目前工作階段而言不需要是唯一的。</span><span class="sxs-lookup"><span data-stu-id="accb1-187">The name is not required to be unique to the computer or the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Session#
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="accb1-188">-Port</span><span class="sxs-lookup"><span data-stu-id="accb1-188">-Port</span></span>

<span data-ttu-id="accb1-189">指定遠端電腦上要供此連線使用的網路連接埠。</span><span class="sxs-lookup"><span data-stu-id="accb1-189">Specifies the network port on the remote computer that is used for this connection.</span></span> <span data-ttu-id="accb1-190">若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="accb1-190">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="accb1-191">預設通訊埠為 5985 (WinRM 埠（適用于 HTTP）) 和 5986 (適用于 HTTPS) 的 WinRM 埠。</span><span class="sxs-lookup"><span data-stu-id="accb1-191">The default ports are 5985 (WinRM port for HTTP) and 5986 (WinRM port for HTTPS).</span></span>

<span data-ttu-id="accb1-192">使用其他埠之前，您必須先將遠端電腦上的 WinRM 接聽程式設定為在該埠上接聽。</span><span class="sxs-lookup"><span data-stu-id="accb1-192">Before using another port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="accb1-193">使用下列命令來設定接聽程式：</span><span class="sxs-lookup"><span data-stu-id="accb1-193">Use the following commands to configure the listener:</span></span>

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="accb1-194">除非必要，否則請勿使用 **Port** 參數。</span><span class="sxs-lookup"><span data-stu-id="accb1-194">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="accb1-195">命令中的連接埠設定會套用到所有電腦或命令執行所在工作階段。</span><span class="sxs-lookup"><span data-stu-id="accb1-195">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="accb1-196">替代的連接埠設定可能使得命令無法在全部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="accb1-196">An alternate port setting might prevent the command from running on all computers.</span></span>

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

### <span data-ttu-id="accb1-197">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="accb1-197">-SessionOption</span></span>

<span data-ttu-id="accb1-198">指定會話的 advanced 選項。</span><span class="sxs-lookup"><span data-stu-id="accb1-198">Specifies advanced options for the session.</span></span> <span data-ttu-id="accb1-199">輸入 **SessionOption** 物件，例如使用 Cmdlet 建立的物件 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="accb1-199">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet.</span></span>

<span data-ttu-id="accb1-200">選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。</span><span class="sxs-lookup"><span data-stu-id="accb1-200">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="accb1-201">否則，將以工作階段設定中設定的選項建立預設值。</span><span class="sxs-lookup"><span data-stu-id="accb1-201">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="accb1-202">會話選項值的優先順序高於 `$PSSessionOption` 喜好設定變數和會話設定中設定之會話的預設值。</span><span class="sxs-lookup"><span data-stu-id="accb1-202">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="accb1-203">不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。</span><span class="sxs-lookup"><span data-stu-id="accb1-203">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span> <span data-ttu-id="accb1-204">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="accb1-204">For more information about session configurations, see [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="accb1-205">如需會話選項的描述（包括預設值），請參閱 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="accb1-205">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="accb1-206">如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="accb1-206">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="accb1-207">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="accb1-207">-ThrottleLimit</span></span>

<span data-ttu-id="accb1-208">指定為執行此命令可建立的最大同時連線數。</span><span class="sxs-lookup"><span data-stu-id="accb1-208">Specifies the maximum number of concurrent connections that can be established to run this command.</span></span>
<span data-ttu-id="accb1-209">如果您省略此參數，或輸入 0 (零) 的值，則會使用 **microsoft.powershellworkflow** 會話設定的預設值100。</span><span class="sxs-lookup"><span data-stu-id="accb1-209">If you omit this parameter or enter a value of 0 (zero), the default value for the **Microsoft.PowerShellWorkflow** session configuration, 100, is used.</span></span>

<span data-ttu-id="accb1-210">節流限制僅適用於目前命令，不適用於工作階段或電腦。</span><span class="sxs-lookup"><span data-stu-id="accb1-210">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="accb1-211">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="accb1-211">-UseSSL</span></span>

<span data-ttu-id="accb1-212">指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來建立與遠端電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="accb1-212">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="accb1-213">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="accb1-213">By default, SSL is not used.</span></span>

<span data-ttu-id="accb1-214">WS-Management 會加密透過網路傳輸的所有 Windows PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="accb1-214">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="accb1-215">**UseSSL** 參數是額外的保護，可跨 HTTPS 連接（而非 HTTP 連線）傳送資料。</span><span class="sxs-lookup"><span data-stu-id="accb1-215">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="accb1-216">如果您指定此參數，但命令所用的埠上沒有 SSL，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="accb1-216">If you specify this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="accb1-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="accb1-217">CommonParameters</span></span>

<span data-ttu-id="accb1-218">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="accb1-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="accb1-219">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="accb1-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="accb1-220">輸入</span><span class="sxs-lookup"><span data-stu-id="accb1-220">INPUTS</span></span>

### <span data-ttu-id="accb1-221">System.servicemodel. PSSession []，System.string。</span><span class="sxs-lookup"><span data-stu-id="accb1-221">System.Management.Automation.Runspaces.PSSession[], System.String</span></span>

<span data-ttu-id="accb1-222">您可以使用管線將會話或電腦名稱稱傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="accb1-222">You can pipe a session or a computer name to this cmdlet.</span></span>

## <span data-ttu-id="accb1-223">輸出</span><span class="sxs-lookup"><span data-stu-id="accb1-223">OUTPUTS</span></span>

### <span data-ttu-id="accb1-224">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="accb1-224">System.Management.Automation.Runspaces.PSSession</span></span>

## <span data-ttu-id="accb1-225">注意</span><span class="sxs-lookup"><span data-stu-id="accb1-225">NOTES</span></span>

<span data-ttu-id="accb1-226">`New-PSWorkflowSession`命令相當於下列命令：</span><span class="sxs-lookup"><span data-stu-id="accb1-226">A `New-PSWorkflowSession` command is equivalent to the following command:</span></span>

`New-PSSession -ConfigurationName Microsoft.PowerShell.Workflow`

## <span data-ttu-id="accb1-227">相關連結</span><span class="sxs-lookup"><span data-stu-id="accb1-227">RELATED LINKS</span></span>

[<span data-ttu-id="accb1-228">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="accb1-228">Disconnect-PSSession</span></span>](../Microsoft.PowerShell.Core/Disconnect-PSSession.md)

[<span data-ttu-id="accb1-229">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="accb1-229">New-PSSession</span></span>](../Microsoft.PowerShell.Core/New-PSSession.md)

[<span data-ttu-id="accb1-230">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="accb1-230">New-PSTransportOption</span></span>](../Microsoft.PowerShell.Core/New-PSTransportOption.md)

[<span data-ttu-id="accb1-231">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="accb1-231">Register-PSSessionConfiguration</span></span>](../Microsoft.PowerShell.Core/Register-PSSessionConfiguration.md)

[<span data-ttu-id="accb1-232">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="accb1-232">about_PSSessions</span></span>](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[<span data-ttu-id="accb1-233">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="accb1-233">about_Session_Configurations</span></span>](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)

[<span data-ttu-id="accb1-234">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="accb1-234">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="accb1-235">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="accb1-235">about_WorkflowCommonParameters</span></span>](About/about_WorkflowCommonParameters.md)
