---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/remove-wsmaninstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WSManInstance
ms.openlocfilehash: 0e605d35b485740a7fbe7408427aa191983cc436
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205460"
---
# <span data-ttu-id="f007f-103">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f007f-103">Remove-WSManInstance</span></span>

## <span data-ttu-id="f007f-104">概要</span><span class="sxs-lookup"><span data-stu-id="f007f-104">SYNOPSIS</span></span>
<span data-ttu-id="f007f-105">刪除管理資源執行個體。</span><span class="sxs-lookup"><span data-stu-id="f007f-105">Deletes a management resource instance.</span></span>

## <span data-ttu-id="f007f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f007f-106">SYNTAX</span></span>

### <span data-ttu-id="f007f-107">ComputerName (預設值)</span><span class="sxs-lookup"><span data-stu-id="f007f-107">ComputerName (Default)</span></span>

```
Remove-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-UseSSL]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="f007f-108">URI</span><span class="sxs-lookup"><span data-stu-id="f007f-108">URI</span></span>

```
Remove-WSManInstance [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="f007f-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f007f-109">DESCRIPTION</span></span>

<span data-ttu-id="f007f-110">**Set-wsmaninstance** 指令程式會刪除在 *ResourceURI* 和 *SelectorSet* 參數中指定的管理資源實例。</span><span class="sxs-lookup"><span data-stu-id="f007f-110">The **Remove-WSManInstance** cmdlet deletes an instance of a management resource that is specified in the *ResourceURI* and *SelectorSet* parameters.</span></span>

<span data-ttu-id="f007f-111">此 Cmdlet 會使用 WinRM 連線/傳輸層來刪除管理資源執行個體。</span><span class="sxs-lookup"><span data-stu-id="f007f-111">This cmdlet uses the WinRM connection/transport layer to delete the management resource instance.</span></span>

## <span data-ttu-id="f007f-112">範例</span><span class="sxs-lookup"><span data-stu-id="f007f-112">EXAMPLES</span></span>

### <span data-ttu-id="f007f-113">範例1：刪除接聽程式</span><span class="sxs-lookup"><span data-stu-id="f007f-113">Example 1: Delete a listener</span></span>

```
PS C:\> Remove-WSManInstance -ResourceUri winrm/config/Listener -SelectorSet Address=test.fabrikam.com;Transport=http
```

<span data-ttu-id="f007f-114">此命令會刪除電腦上 WS-Management 的 HTTP 接聽程式。</span><span class="sxs-lookup"><span data-stu-id="f007f-114">This command deletes the WS-Management HTTP listener on a computer.</span></span>

## <span data-ttu-id="f007f-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f007f-115">PARAMETERS</span></span>

### <span data-ttu-id="f007f-116">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="f007f-116">-ApplicationName</span></span>

<span data-ttu-id="f007f-117">指定連線中的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="f007f-117">Specifies the application name in the connection.</span></span>
<span data-ttu-id="f007f-118">*ApplicationName* 參數的預設值是 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="f007f-118">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="f007f-119">遠端端點的完整識別碼使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="f007f-119">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="f007f-120">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="f007f-120">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="f007f-121">例如：`http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="f007f-121">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="f007f-122">裝載工作階段的網際網路資訊服務 (IIS)，會使用此端點轉送要求至指定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f007f-122">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="f007f-123">此預設設定 WSMAN 適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="f007f-123">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="f007f-124">如果有許多電腦與執行 PowerShell 的一部電腦建立遠端連線，則會使用此參數。</span><span class="sxs-lookup"><span data-stu-id="f007f-124">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="f007f-125">在此案例中，IIS 會裝載管理 Web 服務 (WS-Management) 以獲得較佳效率。</span><span class="sxs-lookup"><span data-stu-id="f007f-125">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f007f-126">-Authentication</span><span class="sxs-lookup"><span data-stu-id="f007f-126">-Authentication</span></span>

<span data-ttu-id="f007f-127">指定用於伺服器的驗證機制。</span><span class="sxs-lookup"><span data-stu-id="f007f-127">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="f007f-128">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="f007f-128">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f007f-129">基本。</span><span class="sxs-lookup"><span data-stu-id="f007f-129">Basic.</span></span>
<span data-ttu-id="f007f-130">Basic 配置使用純文字方式將使用者名稱與密碼傳送至伺服器或 Proxy。</span><span class="sxs-lookup"><span data-stu-id="f007f-130">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="f007f-131">預設值：</span><span class="sxs-lookup"><span data-stu-id="f007f-131">Default.</span></span>
<span data-ttu-id="f007f-132">使用 WS-Management 通訊協定實作的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="f007f-132">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="f007f-133">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="f007f-133">This is the default.</span></span>
- <span data-ttu-id="f007f-134">摘要。</span><span class="sxs-lookup"><span data-stu-id="f007f-134">Digest.</span></span>
<span data-ttu-id="f007f-135">Digest 為查問-回應配置，於查問中使用伺服器指定的資料字串。</span><span class="sxs-lookup"><span data-stu-id="f007f-135">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="f007f-136">Kerberos。</span><span class="sxs-lookup"><span data-stu-id="f007f-136">Kerberos.</span></span>
<span data-ttu-id="f007f-137">用戶端電腦和伺服器使用 Kerberos 憑證相互驗證。</span><span class="sxs-lookup"><span data-stu-id="f007f-137">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="f007f-138">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="f007f-138">Negotiate.</span></span>
<span data-ttu-id="f007f-139">Negotiate 為查問-回應配置，會與伺服器或 Proxy 交涉以決定要用於驗證的配置。</span><span class="sxs-lookup"><span data-stu-id="f007f-139">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="f007f-140">例如，此參數值允許交涉，以決定要使用 Kerberos 通訊協定或 NTLM。</span><span class="sxs-lookup"><span data-stu-id="f007f-140">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="f007f-141">CredSSP。</span><span class="sxs-lookup"><span data-stu-id="f007f-141">CredSSP.</span></span>
<span data-ttu-id="f007f-142">使用認證安全性支援提供者 (CredSSP) 驗證，讓使用者能夠委派認證。</span><span class="sxs-lookup"><span data-stu-id="f007f-142">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="f007f-143">此選項是針對下列命令所設計：命令在遠端電腦上執行，但是收集來自其他遠端電腦上的資料，或是在其他遠端電腦上執行其他命令。</span><span class="sxs-lookup"><span data-stu-id="f007f-143">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="f007f-144">注意：CredSSP 會將使用者認證從本機電腦委派給遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="f007f-144">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="f007f-145">此做法會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="f007f-145">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="f007f-146">若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="f007f-146">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="f007f-147">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="f007f-147">-CertificateThumbprint</span></span>

<span data-ttu-id="f007f-148">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="f007f-148">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="f007f-149">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="f007f-149">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="f007f-150">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="f007f-150">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="f007f-151">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="f007f-151">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="f007f-152">若要取得憑證指紋，請使用 PowerShell Cert：磁片磁碟機中的 Get-Item 或 Get-ChildItem 命令。</span><span class="sxs-lookup"><span data-stu-id="f007f-152">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="f007f-153">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f007f-153">-ComputerName</span></span>

<span data-ttu-id="f007f-154">指定要執行管理作業的電腦。</span><span class="sxs-lookup"><span data-stu-id="f007f-154">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="f007f-155">值可以是完整網域名稱、NetBIOS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="f007f-155">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="f007f-156">使用本機電腦名稱、使用 localhost，或使用句點 (.) 來指定本機電腦。</span><span class="sxs-lookup"><span data-stu-id="f007f-156">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="f007f-157">預設值是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="f007f-157">The local computer is the default.</span></span>
<span data-ttu-id="f007f-158">當遠端電腦與使用者位於不同網域，您必須使用完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="f007f-158">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="f007f-159">您可以使用管線將此參數的值傳送至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f007f-159">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f007f-160">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="f007f-160">-ConnectionURI</span></span>

<span data-ttu-id="f007f-161">指定連線端點。</span><span class="sxs-lookup"><span data-stu-id="f007f-161">Specifies the connection endpoint.</span></span>
<span data-ttu-id="f007f-162">這個字串的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="f007f-162">The format of this string is as follows:</span></span>

<span data-ttu-id="f007f-163">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="f007f-163">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="f007f-164">下列字串是此參數的正確格式值：</span><span class="sxs-lookup"><span data-stu-id="f007f-164">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="f007f-165">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="f007f-165">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f007f-166">-Credential</span><span class="sxs-lookup"><span data-stu-id="f007f-166">-Credential</span></span>

<span data-ttu-id="f007f-167">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="f007f-167">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="f007f-168">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="f007f-168">The default is the current user.</span></span>
<span data-ttu-id="f007f-169">輸入使用者名稱，例如 User01、Domain01\User01 或 User@Domain.com 。</span><span class="sxs-lookup"><span data-stu-id="f007f-169">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="f007f-170">或者，輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="f007f-170">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="f007f-171">當您輸入使用者名稱時，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="f007f-171">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="f007f-172">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="f007f-172">-OptionSet</span></span>

<span data-ttu-id="f007f-173">對服務指定一組切換參數，以修改或精簡要求的本質。</span><span class="sxs-lookup"><span data-stu-id="f007f-173">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="f007f-174">這些切換參數類似於命令列殼層中使用的切換參數，因為都是服務特定的切換參數。</span><span class="sxs-lookup"><span data-stu-id="f007f-174">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="f007f-175">您可以指定任意數目的選項。</span><span class="sxs-lookup"><span data-stu-id="f007f-175">Any number of options can be specified.</span></span>

<span data-ttu-id="f007f-176">下列範例示範的語法可傳遞 a、b 與 c 參數的值 1、2 與 3：</span><span class="sxs-lookup"><span data-stu-id="f007f-176">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f007f-177">-Port</span><span class="sxs-lookup"><span data-stu-id="f007f-177">-Port</span></span>

<span data-ttu-id="f007f-178">指定用戶端連線 WinRM 服務時所使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="f007f-178">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="f007f-179">傳輸為 HTTP 時，預設連接埠為 80。</span><span class="sxs-lookup"><span data-stu-id="f007f-179">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="f007f-180">傳輸為 HTTPS 時，預設連接埠為 443。</span><span class="sxs-lookup"><span data-stu-id="f007f-180">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="f007f-181">當您使用 HTTPS 做為傳輸時， *ComputerName* 參數的值必須符合伺服器的憑證一般名稱 (CN) 。</span><span class="sxs-lookup"><span data-stu-id="f007f-181">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="f007f-182">不過，如果 *SkipCNCheck* 參數指定為 *SessionOption* 參數的一部分，則伺服器憑證一般名稱不必符合伺服器主機名稱。</span><span class="sxs-lookup"><span data-stu-id="f007f-182">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="f007f-183">*SkipCNCheck* 參數只能用於信任的電腦。</span><span class="sxs-lookup"><span data-stu-id="f007f-183">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="f007f-184">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="f007f-184">-ResourceURI</span></span>

<span data-ttu-id="f007f-185">指定資源類別或實例的 URI。</span><span class="sxs-lookup"><span data-stu-id="f007f-185">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="f007f-186">URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。</span><span class="sxs-lookup"><span data-stu-id="f007f-186">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="f007f-187">URI 是由前置詞與資源路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="f007f-187">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="f007f-188">例如：</span><span class="sxs-lookup"><span data-stu-id="f007f-188">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f007f-189">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="f007f-189">-SelectorSet</span></span>

<span data-ttu-id="f007f-190">指定一組值組，用來選取特定管理資源執行個體。</span><span class="sxs-lookup"><span data-stu-id="f007f-190">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="f007f-191">當有一個以上的資源實例存在時，就會使用 *SelectorSet* 參數。</span><span class="sxs-lookup"><span data-stu-id="f007f-191">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="f007f-192">*SelectorSet* 的值必須是雜湊表。</span><span class="sxs-lookup"><span data-stu-id="f007f-192">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="f007f-193">下列範例顯示如何輸入此參數的值：</span><span class="sxs-lookup"><span data-stu-id="f007f-193">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f007f-194">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="f007f-194">-SessionOption</span></span>

<span data-ttu-id="f007f-195">指定 WS-Management 工作階段的擴充選項。</span><span class="sxs-lookup"><span data-stu-id="f007f-195">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="f007f-196">輸入您使用 New-WSManSessionOption Cmdlet 建立的 **SessionOption** 物件。</span><span class="sxs-lookup"><span data-stu-id="f007f-196">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="f007f-197">如需可用選項的詳細資訊，請輸入 `Get-Help New-WSManSessionOption`。</span><span class="sxs-lookup"><span data-stu-id="f007f-197">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: so

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f007f-198">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="f007f-198">-UseSSL</span></span>

<span data-ttu-id="f007f-199">指定使用安全通訊端層 (SSL) 通訊協定來建立遠端電腦連線。</span><span class="sxs-lookup"><span data-stu-id="f007f-199">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="f007f-200">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="f007f-200">By default, SSL is not used.</span></span>

<span data-ttu-id="f007f-201">WS-Management 會加密透過網路傳輸的所有 PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="f007f-201">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="f007f-202">*UseSSL* 參數可讓您指定 HTTPS （而非 HTTP）的額外保護。</span><span class="sxs-lookup"><span data-stu-id="f007f-202">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="f007f-203">若用於連線的連接埠上無法使用 SSL，且您指定此參數，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="f007f-203">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases: ssl

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f007f-204">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f007f-204">CommonParameters</span></span>

<span data-ttu-id="f007f-205">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f007f-205">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f007f-206">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f007f-206">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f007f-207">輸入</span><span class="sxs-lookup"><span data-stu-id="f007f-207">INPUTS</span></span>

### <span data-ttu-id="f007f-208">無</span><span class="sxs-lookup"><span data-stu-id="f007f-208">None</span></span>

<span data-ttu-id="f007f-209">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="f007f-209">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="f007f-210">輸出</span><span class="sxs-lookup"><span data-stu-id="f007f-210">OUTPUTS</span></span>

### <span data-ttu-id="f007f-211">無</span><span class="sxs-lookup"><span data-stu-id="f007f-211">None</span></span>

<span data-ttu-id="f007f-212">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f007f-212">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f007f-213">注意</span><span class="sxs-lookup"><span data-stu-id="f007f-213">NOTES</span></span>

* <span data-ttu-id="f007f-214">Remove-WmiObject Cmdlet (它是 Windows Management Instrumentation (WMI) Cmdlet) 是類似的。</span><span class="sxs-lookup"><span data-stu-id="f007f-214">The Remove-WmiObject cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span> <span data-ttu-id="f007f-215">**>get-wmiobject** 會使用 DCOM 連線/傳輸層來建立或更新 WMI 實例。</span><span class="sxs-lookup"><span data-stu-id="f007f-215">**Remove-WmiObject** uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

*

## <span data-ttu-id="f007f-216">相關連結</span><span class="sxs-lookup"><span data-stu-id="f007f-216">RELATED LINKS</span></span>

[<span data-ttu-id="f007f-217">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="f007f-217">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="f007f-218">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="f007f-218">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="f007f-219">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="f007f-219">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="f007f-220">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="f007f-220">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="f007f-221">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="f007f-221">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="f007f-222">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f007f-222">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="f007f-223">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="f007f-223">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="f007f-224">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f007f-224">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="f007f-225">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="f007f-225">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="f007f-226">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="f007f-226">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="f007f-227">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="f007f-227">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="f007f-228">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="f007f-228">Test-WSMan</span></span>](Test-WSMan.md)
