---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: 0cf40af09354314a28af216642d09a5c1fa7479d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202547"
---
# <span data-ttu-id="08485-103">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="08485-103">Test-WSMan</span></span>

## <span data-ttu-id="08485-104">概要</span><span class="sxs-lookup"><span data-stu-id="08485-104">SYNOPSIS</span></span>
<span data-ttu-id="08485-105">測試 WinRM 服務是否已在本機或遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="08485-105">Tests whether the WinRM service is running on a local or remote computer.</span></span>

## <span data-ttu-id="08485-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="08485-106">SYNTAX</span></span>

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="08485-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="08485-107">DESCRIPTION</span></span>

<span data-ttu-id="08485-108">**Test-WSMan** Cmdlet 會提交身分識別要求，以判斷 WinRM 服務是否正在本機或遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="08485-108">The **Test-WSMan** cmdlet submits an identification request that determines whether the WinRM service is running on a local or remote computer.</span></span>
<span data-ttu-id="08485-109">若測試的電腦正在執行該服務，則此 Cmdlet 會顯示已測試之服務的 WS-Management 身分識別結構描述、通訊協定版本、產品廠商與產品版本。</span><span class="sxs-lookup"><span data-stu-id="08485-109">If the tested computer is running the service, the cmdlet displays the WS-Management identity schema, the protocol version, the product vendor, and the product version of the tested service.</span></span>

## <span data-ttu-id="08485-110">範例</span><span class="sxs-lookup"><span data-stu-id="08485-110">EXAMPLES</span></span>

### <span data-ttu-id="08485-111">範例 1︰判斷 WinRM 服務的狀態</span><span class="sxs-lookup"><span data-stu-id="08485-111">Example 1: Determine the status of the WinRM service</span></span>

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="08485-112">此命令會判斷 WinRM 服務是否已在本機電腦或遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="08485-112">This command determines whether the WinRM service is running on the local computer or on a remote computer.</span></span>

### <span data-ttu-id="08485-113">範例 2︰判斷遠端電腦上 WinRM 服務的狀態</span><span class="sxs-lookup"><span data-stu-id="08485-113">Example 2: Determine the status of the WinRM service on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="08485-114">此命令會判斷 WinRM 服務是否正在 server01 電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="08485-114">This command determines whether the WinRM service is running on the server01 computer.</span></span>

### <span data-ttu-id="08485-115">範例 3︰判斷 WinRM 服務的狀態和作業系統版本</span><span class="sxs-lookup"><span data-stu-id="08485-115">Example 3: Determine the status of the WinRM service and the operating system version</span></span>

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

<span data-ttu-id="08485-116">此命令會使用驗證參數，來測試 WS-Management (WinRM) 服務是否正在本機電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="08485-116">This command tests to see whether the WS-Management (WinRM) service is running on the local computer by using the authentication parameter.</span></span>

<span data-ttu-id="08485-117">使用驗證參數可讓 **Test-WSMan** 傳回作業系統版本。</span><span class="sxs-lookup"><span data-stu-id="08485-117">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

### <span data-ttu-id="08485-118">範例 4︰判斷遠端電腦上的 WinRM 服務狀態和作業系統版本</span><span class="sxs-lookup"><span data-stu-id="08485-118">Example 4: Determine the status of the WinRM service and the operating system version on a remote computer</span></span>

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

<span data-ttu-id="08485-119">此命令會使用驗證參數，來查看 WS-Management (WinRM) 服務是否正在名為 server01 的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="08485-119">This command tests to see whether the WS-Management (WinRM) service is running on the computer named server01 using the authentication parameter.</span></span>

<span data-ttu-id="08485-120">使用驗證參數可讓 **Test-WSMan** 傳回作業系統版本。</span><span class="sxs-lookup"><span data-stu-id="08485-120">Using the authentication parameter enables **Test-WSMan** to return the operating system version.</span></span>

## <span data-ttu-id="08485-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="08485-121">PARAMETERS</span></span>

### <span data-ttu-id="08485-122">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="08485-122">-ApplicationName</span></span>

<span data-ttu-id="08485-123">指定連線中的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="08485-123">Specifies the application name in the connection.</span></span>
<span data-ttu-id="08485-124">*ApplicationName* 參數的預設值是 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="08485-124">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="08485-125">遠端端點的完整識別碼使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="08485-125">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="08485-126">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="08485-126">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="08485-127">例如：`http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="08485-127">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="08485-128">裝載工作階段的網際網路資訊服務 (IIS)，會使用此端點轉送要求至指定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="08485-128">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="08485-129">此預設設定 WSMAN 適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="08485-129">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="08485-130">如果有許多電腦與執行 PowerShell 的一部電腦建立遠端連線，則會使用此參數。</span><span class="sxs-lookup"><span data-stu-id="08485-130">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="08485-131">在此案例中，IIS 會裝載管理 Web 服務 (WS-Management) 以獲得較佳效率。</span><span class="sxs-lookup"><span data-stu-id="08485-131">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="08485-132">-Authentication</span><span class="sxs-lookup"><span data-stu-id="08485-132">-Authentication</span></span>

<span data-ttu-id="08485-133">指定用於伺服器的驗證機制。</span><span class="sxs-lookup"><span data-stu-id="08485-133">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="08485-134">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="08485-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="08485-135">基本。</span><span class="sxs-lookup"><span data-stu-id="08485-135">Basic.</span></span>
<span data-ttu-id="08485-136">Basic 配置使用純文字方式將使用者名稱與密碼傳送至伺服器或 Proxy。</span><span class="sxs-lookup"><span data-stu-id="08485-136">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="08485-137">預設值：</span><span class="sxs-lookup"><span data-stu-id="08485-137">Default.</span></span>
<span data-ttu-id="08485-138">使用 WS-Management 通訊協定實作的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="08485-138">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="08485-139">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="08485-139">This is the default.</span></span>
- <span data-ttu-id="08485-140">摘要。</span><span class="sxs-lookup"><span data-stu-id="08485-140">Digest.</span></span>
<span data-ttu-id="08485-141">Digest 為查問-回應配置，於查問中使用伺服器指定的資料字串。</span><span class="sxs-lookup"><span data-stu-id="08485-141">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="08485-142">Kerberos。</span><span class="sxs-lookup"><span data-stu-id="08485-142">Kerberos.</span></span>
<span data-ttu-id="08485-143">用戶端電腦和伺服器使用 Kerberos 憑證相互驗證。</span><span class="sxs-lookup"><span data-stu-id="08485-143">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="08485-144">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="08485-144">Negotiate.</span></span>
<span data-ttu-id="08485-145">Negotiate 為查問-回應配置，會與伺服器或 Proxy 交涉以決定要用於驗證的配置。</span><span class="sxs-lookup"><span data-stu-id="08485-145">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="08485-146">例如，此參數值允許交涉，以決定要使用 Kerberos 通訊協定或 NTLM。</span><span class="sxs-lookup"><span data-stu-id="08485-146">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="08485-147">CredSSP。</span><span class="sxs-lookup"><span data-stu-id="08485-147">CredSSP.</span></span>
<span data-ttu-id="08485-148">使用認證安全性支援提供者 (CredSSP) 驗證，讓使用者能夠委派認證。</span><span class="sxs-lookup"><span data-stu-id="08485-148">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="08485-149">此選項是針對下列命令所設計：命令在遠端電腦上執行，但是收集來自其他遠端電腦上的資料，或是在其他遠端電腦上執行其他命令。</span><span class="sxs-lookup"><span data-stu-id="08485-149">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="08485-150">注意：CredSSP 會將使用者認證從本機電腦委派給遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="08485-150">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="08485-151">此做法會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="08485-151">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="08485-152">若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="08485-152">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

<span data-ttu-id="08485-153">重要：若未指定 *Authentication* 參數，就會以匿名方式將 **Test-WSMan** 要求傳送到遠端電腦，而不使用驗證。</span><span class="sxs-lookup"><span data-stu-id="08485-153">Important: If you do not specify the *Authentication* parameter,, the **Test-WSMan** request is sent to the remote computer anonymously, without using authentication.</span></span>
<span data-ttu-id="08485-154">若以匿名方式提出要求，它就不會傳回任何作業系統版本特定的資訊。</span><span class="sxs-lookup"><span data-stu-id="08485-154">If the request is made anonymously, it returns no information that is specific to the operating-system version.</span></span>
<span data-ttu-id="08485-155">相反地，此 Cmdlet 會為作業系統版本與 Service Pack 等級顯示 Null 值 (OS：0.0.0 SP：0.0)。</span><span class="sxs-lookup"><span data-stu-id="08485-155">Instead, this cmdlet displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="08485-156">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="08485-156">-CertificateThumbprint</span></span>

<span data-ttu-id="08485-157">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="08485-157">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="08485-158">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="08485-158">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="08485-159">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="08485-159">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="08485-160">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="08485-160">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="08485-161">若要取得憑證指紋，請使用 PowerShell Cert：磁片磁碟機中的 Get-Item 或 Get-ChildItem 命令。</span><span class="sxs-lookup"><span data-stu-id="08485-161">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="08485-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="08485-162">-ComputerName</span></span>

<span data-ttu-id="08485-163">指定要執行管理作業的電腦。</span><span class="sxs-lookup"><span data-stu-id="08485-163">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="08485-164">值可以是完整網域名稱、NetBIOS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="08485-164">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="08485-165">使用本機電腦名稱、使用 localhost，或使用句點 (.) 來指定本機電腦。</span><span class="sxs-lookup"><span data-stu-id="08485-165">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="08485-166">預設值是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="08485-166">The local computer is the default.</span></span>
<span data-ttu-id="08485-167">當遠端電腦與使用者位於不同網域，您必須使用完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="08485-167">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="08485-168">您可以使用管線將此參數的值傳送至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="08485-168">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="08485-169">-Credential</span><span class="sxs-lookup"><span data-stu-id="08485-169">-Credential</span></span>

<span data-ttu-id="08485-170">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="08485-170">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="08485-171">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="08485-171">The default is the current user.</span></span>
<span data-ttu-id="08485-172">輸入使用者名稱，例如 User01、Domain01\User01 或 User@Domain.com 。</span><span class="sxs-lookup"><span data-stu-id="08485-172">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="08485-173">或者，輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="08485-173">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="08485-174">當您輸入使用者名稱時，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="08485-174">When you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="08485-175">-Port</span><span class="sxs-lookup"><span data-stu-id="08485-175">-Port</span></span>

<span data-ttu-id="08485-176">指定用戶端連線 WinRM 服務時所使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="08485-176">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="08485-177">傳輸為 HTTP 時，預設連接埠為 80。</span><span class="sxs-lookup"><span data-stu-id="08485-177">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="08485-178">傳輸為 HTTPS 時，預設連接埠為 443。</span><span class="sxs-lookup"><span data-stu-id="08485-178">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="08485-179">當您使用 HTTPS 做為傳輸時， *ComputerName* 參數的值必須符合伺服器的憑證一般名稱 (CN) 。</span><span class="sxs-lookup"><span data-stu-id="08485-179">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>

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

### <span data-ttu-id="08485-180">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="08485-180">-UseSSL</span></span>

<span data-ttu-id="08485-181">指定使用安全通訊端層 (SSL) 通訊協定來建立遠端電腦連線。</span><span class="sxs-lookup"><span data-stu-id="08485-181">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="08485-182">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="08485-182">By default, SSL is not used.</span></span>

<span data-ttu-id="08485-183">WS-Management 會加密透過網路傳輸的所有 PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="08485-183">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="08485-184">*UseSSL* 參數可讓您指定 HTTPS （而非 HTTP）的額外保護。</span><span class="sxs-lookup"><span data-stu-id="08485-184">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="08485-185">若用於連線的連接埠上無法使用 SSL，且您指定此參數，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="08485-185">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="08485-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="08485-186">CommonParameters</span></span>

<span data-ttu-id="08485-187">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="08485-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="08485-188">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="08485-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="08485-189">輸入</span><span class="sxs-lookup"><span data-stu-id="08485-189">INPUTS</span></span>

### <span data-ttu-id="08485-190">無</span><span class="sxs-lookup"><span data-stu-id="08485-190">None</span></span>

<span data-ttu-id="08485-191">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="08485-191">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="08485-192">輸出</span><span class="sxs-lookup"><span data-stu-id="08485-192">OUTPUTS</span></span>

### <span data-ttu-id="08485-193">無</span><span class="sxs-lookup"><span data-stu-id="08485-193">None</span></span>

<span data-ttu-id="08485-194">這個 Cmdlet 不會產生任何輸出物件。</span><span class="sxs-lookup"><span data-stu-id="08485-194">This cmdlet does not generate any output object.</span></span>

## <span data-ttu-id="08485-195">注意</span><span class="sxs-lookup"><span data-stu-id="08485-195">NOTES</span></span>

* <span data-ttu-id="08485-196">根據預設， **Test-WSMan** Cmdlet 會以不使用驗證的方式查詢 WinRM 服務，而且它不會傳回任何作業系統版本特定的資訊。</span><span class="sxs-lookup"><span data-stu-id="08485-196">By default, the **Test-WSMan** cmdlet queries the WinRM service without using authentication, and it returns no information that is specific to the operating-system version.</span></span> <span data-ttu-id="08485-197">相反地，它會為作業系統版本與 Service Pack 等級顯示 Null 值 (OS：0.0.0 SP：0.0)。</span><span class="sxs-lookup"><span data-stu-id="08485-197">Instead, it displays null values for the operating system version and service pack level (OS: 0.0.0 SP: 0.0).</span></span>

*

## <span data-ttu-id="08485-198">相關連結</span><span class="sxs-lookup"><span data-stu-id="08485-198">RELATED LINKS</span></span>

[<span data-ttu-id="08485-199">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="08485-199">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="08485-200">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="08485-200">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="08485-201">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="08485-201">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="08485-202">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="08485-202">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="08485-203">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="08485-203">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="08485-204">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="08485-204">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="08485-205">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="08485-205">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="08485-206">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="08485-206">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="08485-207">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="08485-207">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="08485-208">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="08485-208">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="08485-209">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="08485-209">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="08485-210">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="08485-210">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)
