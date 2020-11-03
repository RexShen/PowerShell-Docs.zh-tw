---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 03/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmaninstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManInstance
ms.openlocfilehash: f072bf946bc3114db0b6503157880cbe0fb6d6c3
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205467"
---
# <span data-ttu-id="948f8-103">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="948f8-103">New-WSManInstance</span></span>

## <span data-ttu-id="948f8-104">概要</span><span class="sxs-lookup"><span data-stu-id="948f8-104">SYNOPSIS</span></span>
<span data-ttu-id="948f8-105">建立管理資源的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="948f8-105">Creates a new instance of a management resource.</span></span>

## <span data-ttu-id="948f8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="948f8-106">SYNTAX</span></span>

### <span data-ttu-id="948f8-107">ComputerName (預設值)</span><span class="sxs-lookup"><span data-stu-id="948f8-107">ComputerName (Default)</span></span>

```
New-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable>
 [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="948f8-108">URI</span><span class="sxs-lookup"><span data-stu-id="948f8-108">URI</span></span>

```
New-WSManInstance [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="948f8-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="948f8-109">DESCRIPTION</span></span>

<span data-ttu-id="948f8-110">此 `New-WSManInstance` Cmdlet 會建立管理資源的新實例。</span><span class="sxs-lookup"><span data-stu-id="948f8-110">The `New-WSManInstance` cmdlet creates a new instance of a management resource.</span></span> <span data-ttu-id="948f8-111">它會使用資源 URI 與已設定的值或輸入檔案來建立管理資源的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="948f8-111">It uses a resource URI and a value set or input file to create the new instance of the management resource.</span></span>

<span data-ttu-id="948f8-112">此 Cmdlet 會使用 WinRM 連線/傳輸層來建立管理資源執行個體。</span><span class="sxs-lookup"><span data-stu-id="948f8-112">This cmdlet uses the WinRM connection/transport layer to create the management resource instance.</span></span>

## <span data-ttu-id="948f8-113">範例</span><span class="sxs-lookup"><span data-stu-id="948f8-113">EXAMPLES</span></span>

### <span data-ttu-id="948f8-114">範例1：建立 HTTPS 接聽程式</span><span class="sxs-lookup"><span data-stu-id="948f8-114">Example 1: Create a HTTPS listener</span></span>

<span data-ttu-id="948f8-115">此命令會在所有 IP 位址上建立 WS-Management HTTPS 接聽程式的執行個體。</span><span class="sxs-lookup"><span data-stu-id="948f8-115">This command creates an instance of a WS-Management HTTPS listener on all IP addresses.</span></span>

```powershell
New-WSManInstance winrm/config/Listener -SelectorSet @{Transport='HTTPS'; Address='*'} -ValueSet @{Hostname="HOST";CertificateThumbprint="XXXXXXXXXX"}
```

## <span data-ttu-id="948f8-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="948f8-116">PARAMETERS</span></span>

### <span data-ttu-id="948f8-117">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="948f8-117">-ApplicationName</span></span>

<span data-ttu-id="948f8-118">指定連線中的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="948f8-118">Specifies the application name in the connection.</span></span> <span data-ttu-id="948f8-119">**ApplicationName** 參數的預設值是 **WSMAN** 。</span><span class="sxs-lookup"><span data-stu-id="948f8-119">The default value of the **ApplicationName** parameter is **WSMAN** .</span></span> <span data-ttu-id="948f8-120">遠端端點的完整識別碼使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="948f8-120">The complete identifier for the remote endpoint is in the following format:</span></span>

`<transport>://<server>:<port>/<ApplicationName>`

<span data-ttu-id="948f8-121">例如：</span><span class="sxs-lookup"><span data-stu-id="948f8-121">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="948f8-122">裝載工作階段的網際網路資訊服務 (IIS)，會使用此端點轉送要求至指定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="948f8-122">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span> <span data-ttu-id="948f8-123">預設的 **WSMAN** 設定適用于大部分的用途。</span><span class="sxs-lookup"><span data-stu-id="948f8-123">This default setting of **WSMAN** is appropriate for most uses.</span></span> <span data-ttu-id="948f8-124">此參數是設計用於下列狀況：多部電腦建立遠端連線至同一部執行 Windows PowerShell 的電腦。</span><span class="sxs-lookup"><span data-stu-id="948f8-124">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span> <span data-ttu-id="948f8-125">在此案例中，IIS 會裝載管理 Web 服務 (WS-Management) 以獲得較佳效率。</span><span class="sxs-lookup"><span data-stu-id="948f8-125">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: Wsman
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="948f8-126">-Authentication</span><span class="sxs-lookup"><span data-stu-id="948f8-126">-Authentication</span></span>

<span data-ttu-id="948f8-127">指定用於伺服器的驗證機制。</span><span class="sxs-lookup"><span data-stu-id="948f8-127">Specifies the authentication mechanism to be used at the server.</span></span> <span data-ttu-id="948f8-128">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="948f8-128">Possible values are:</span></span>

- <span data-ttu-id="948f8-129">Basic： Basic 是以純文字將使用者名稱和密碼傳送至伺服器或 proxy 的配置。</span><span class="sxs-lookup"><span data-stu-id="948f8-129">Basic: Basic is a scheme in which the username and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="948f8-130">預設值：使用 WS-Management 通訊協定所執行的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="948f8-130">Default: Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="948f8-131">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="948f8-131">This is the default.</span></span>
- <span data-ttu-id="948f8-132">Digest：Digest 為查問-回應配置，於查問中使用伺服器指定的資料字串。</span><span class="sxs-lookup"><span data-stu-id="948f8-132">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="948f8-133">Kerberos：用戶端電腦和伺服器使用 Kerberos 憑證相互驗證。</span><span class="sxs-lookup"><span data-stu-id="948f8-133">Kerberos: The client computer and the server mutually authenticate using Kerberos certificates.</span></span>
- <span data-ttu-id="948f8-134">Negotiate：Negotiate 為查問-回應配置，會與伺服器或 Proxy 交涉以決定要用於驗證的配置。</span><span class="sxs-lookup"><span data-stu-id="948f8-134">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="948f8-135">例如，此參數值允許交涉以決定要使用 Kerberos 通訊協定或 NTLM。</span><span class="sxs-lookup"><span data-stu-id="948f8-135">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="948f8-136">CredSSP：使用允許使用者委派認證的「認證安全性支援提供者 (CredSSP)」驗證。</span><span class="sxs-lookup"><span data-stu-id="948f8-136">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="948f8-137">此選項是針對下列命令所設計：命令在遠端電腦上執行，但是收集來自其他遠端電腦上的資料，或是在其他遠端電腦上執行其他命令。</span><span class="sxs-lookup"><span data-stu-id="948f8-137">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

> [!CAUTION]
> <span data-ttu-id="948f8-138">CredSSP 將使用者認證從本機電腦委派給遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="948f8-138">CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span> <span data-ttu-id="948f8-139">此做法會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="948f8-139">This practice increases the security risk of the remote operation.</span></span> <span data-ttu-id="948f8-140">若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="948f8-140">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="948f8-141">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="948f8-141">-CertificateThumbprint</span></span>

<span data-ttu-id="948f8-142">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="948f8-142">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="948f8-143">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="948f8-143">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="948f8-144">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="948f8-144">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="948f8-145">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="948f8-145">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="948f8-146">若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell Cert：磁片磁碟機中的或命令。</span><span class="sxs-lookup"><span data-stu-id="948f8-146">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="948f8-147">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="948f8-147">-ComputerName</span></span>

<span data-ttu-id="948f8-148">指定要執行管理作業的電腦。</span><span class="sxs-lookup"><span data-stu-id="948f8-148">Specifies the computer against which you want to run the management operation.</span></span> <span data-ttu-id="948f8-149">值可以是完整網域名稱、NetBIOS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="948f8-149">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="948f8-150">使用本機電腦名稱稱、使用 localhost，或使用點 (`.`) 來指定本機電腦。</span><span class="sxs-lookup"><span data-stu-id="948f8-150">Use the local computer name, use localhost, or use a dot (`.`) to specify the local computer.</span></span> <span data-ttu-id="948f8-151">預設值是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="948f8-151">The local computer is the default.</span></span> <span data-ttu-id="948f8-152">當遠端電腦與使用者位於不同網域，您必須使用完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="948f8-152">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span> <span data-ttu-id="948f8-153">您可以使用管線將此參數的值傳送至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="948f8-153">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: Localhost
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="948f8-154">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="948f8-154">-ConnectionURI</span></span>

<span data-ttu-id="948f8-155">指定連線端點。</span><span class="sxs-lookup"><span data-stu-id="948f8-155">Specifies the connection endpoint.</span></span>
<span data-ttu-id="948f8-156">此字串的格式為：</span><span class="sxs-lookup"><span data-stu-id="948f8-156">The format of this string is:</span></span>

`<Transport>://<Server>:<Port>/<ApplicationName>`

<span data-ttu-id="948f8-157">下列字串是此參數的正確格式值：</span><span class="sxs-lookup"><span data-stu-id="948f8-157">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="948f8-158">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="948f8-158">The URI must be fully qualified.</span></span>

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="948f8-159">-Credential</span><span class="sxs-lookup"><span data-stu-id="948f8-159">-Credential</span></span>

<span data-ttu-id="948f8-160">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="948f8-160">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="948f8-161">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="948f8-161">The default is the current user.</span></span> <span data-ttu-id="948f8-162">輸入使用者名稱，例如 "User01"、"Domain01\User01" 或 " User@Domain.com "。</span><span class="sxs-lookup"><span data-stu-id="948f8-162">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span> <span data-ttu-id="948f8-163">或者，輸入 PSCredential 物件，例如 Cmdlet 所傳回的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="948f8-163">Or, enter a PSCredential object, such as one returned by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="948f8-164">當您輸入使用者名稱時，會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="948f8-164">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="948f8-165">-FilePath</span><span class="sxs-lookup"><span data-stu-id="948f8-165">-FilePath</span></span>

<span data-ttu-id="948f8-166">指定用來建立管理資源之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="948f8-166">Specifies the path of a file that is used to create a management resource.</span></span> <span data-ttu-id="948f8-167">您可以使用 **ResourceURI** 參數與 **SelectorSet** 參數來指定管理資源。</span><span class="sxs-lookup"><span data-stu-id="948f8-167">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter .</span></span> <span data-ttu-id="948f8-168">例如，下列命令會使用 **File** 參數：</span><span class="sxs-lookup"><span data-stu-id="948f8-168">For example, the following command uses the **File** parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmi/cimv2/Win32_Service -SelectorSet @{Name="spooler"} -File c:\input.xml -Authentication Default`

<span data-ttu-id="948f8-169">此命令會使用來自檔案的輸入，在多工緩衝處理器服務上呼叫 **StopService** 方法。</span><span class="sxs-lookup"><span data-stu-id="948f8-169">This command calls the **StopService** method on the Spooler service using input from a file.</span></span> <span data-ttu-id="948f8-170">檔案 `Input.xml` 包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="948f8-170">The file, `Input.xml`, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="948f8-171">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="948f8-171">-OptionSet</span></span>

<span data-ttu-id="948f8-172">將一組切換參數傳遞給服務，以修改或精簡要求的本質。</span><span class="sxs-lookup"><span data-stu-id="948f8-172">Passes a set of switches to a service to modify or refine the nature of the request.</span></span> <span data-ttu-id="948f8-173">這些切換參數類似於命令列殼層中使用的切換參數，因為都是服務特定的切換參數。</span><span class="sxs-lookup"><span data-stu-id="948f8-173">These are similar to switches used in command-line shells because they are service specific.</span></span> <span data-ttu-id="948f8-174">您可以指定任意數目的選項。</span><span class="sxs-lookup"><span data-stu-id="948f8-174">Any number of options can be specified.</span></span>

<span data-ttu-id="948f8-175">下列範例示範的語法可傳遞 a、b 與 c 參數的值 1、2 與 3：</span><span class="sxs-lookup"><span data-stu-id="948f8-175">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="948f8-176">-Port</span><span class="sxs-lookup"><span data-stu-id="948f8-176">-Port</span></span>

<span data-ttu-id="948f8-177">指定用戶端連線 WinRM 服務時所使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="948f8-177">Specifies the port to use when the client connects to the WinRM service.</span></span> <span data-ttu-id="948f8-178">傳輸為 HTTP 時，預設連接埠為 80。</span><span class="sxs-lookup"><span data-stu-id="948f8-178">When the transport is HTTP, the default port is 80.</span></span> <span data-ttu-id="948f8-179">傳輸為 HTTPS 時，預設連接埠為 443。</span><span class="sxs-lookup"><span data-stu-id="948f8-179">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="948f8-180">當您使用 HTTPS 做為傳輸時， **ComputerName** 參數的值必須符合伺服器的憑證一般名稱 (CN) 。</span><span class="sxs-lookup"><span data-stu-id="948f8-180">When you use HTTPS as the transport, the value of the **ComputerName** parameter must match the server's certificate common name (CN).</span></span> <span data-ttu-id="948f8-181">不過，如果 **SkipCNCheck** 參數指定為 **SessionOption** 參數的一部分，則伺服器憑證一般名稱不必符合伺服器主機名稱。</span><span class="sxs-lookup"><span data-stu-id="948f8-181">However, if the **SkipCNCheck** parameter is specified as part of the **SessionOption** parameter, the certificate common name of the server does not have to match the host name of the server.</span></span> <span data-ttu-id="948f8-182">**SkipCNCheck** 參數只能用於信任的電腦。</span><span class="sxs-lookup"><span data-stu-id="948f8-182">The **SkipCNCheck** parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="948f8-183">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="948f8-183">-ResourceURI</span></span>

<span data-ttu-id="948f8-184">包含資源類別或執行個體的「統一資源識別項 (URI)」。</span><span class="sxs-lookup"><span data-stu-id="948f8-184">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="948f8-185">URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。</span><span class="sxs-lookup"><span data-stu-id="948f8-185">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="948f8-186">URI 是由前置詞與資源路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="948f8-186">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="948f8-187">例如：</span><span class="sxs-lookup"><span data-stu-id="948f8-187">For example:</span></span>

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

### <span data-ttu-id="948f8-188">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="948f8-188">-SelectorSet</span></span>

<span data-ttu-id="948f8-189">指定一組值組，用來選取特定管理資源執行個體。</span><span class="sxs-lookup"><span data-stu-id="948f8-189">Specifies a set of value pairs that are used to select particular management resource instances.</span></span> <span data-ttu-id="948f8-190">當有一個以上的資源實例存在時，就會使用 **SelectorSet** 參數。</span><span class="sxs-lookup"><span data-stu-id="948f8-190">The **SelectorSet** parameter is used when more than one instance of the resource exists.</span></span> <span data-ttu-id="948f8-191">**SelectorSet** 參數的值必須是雜湊表。</span><span class="sxs-lookup"><span data-stu-id="948f8-191">The value of the **SelectorSet** parameter must be a hash table.</span></span>

<span data-ttu-id="948f8-192">下列範例顯示如何輸入此參數的值：</span><span class="sxs-lookup"><span data-stu-id="948f8-192">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="948f8-193">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="948f8-193">-SessionOption</span></span>

<span data-ttu-id="948f8-194">定義 WS-Management 工作階段的一組擴充選項。</span><span class="sxs-lookup"><span data-stu-id="948f8-194">Defines a set of extended options for the WS-Management session.</span></span> <span data-ttu-id="948f8-195">輸入您使用 Cmdlet 建立的 **SessionOption** 物件 `New-WSManSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="948f8-195">Enter a **SessionOption** object that you create using the `New-WSManSessionOption` cmdlet.</span></span> <span data-ttu-id="948f8-196">如需可用選項的詳細資訊，請參閱 `New-WSManSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="948f8-196">For more information about the options that are available, see `New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="948f8-197">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="948f8-197">-UseSSL</span></span>

<span data-ttu-id="948f8-198">指定建立遠端電腦連線時，應使用「安全通訊端層 (SSL)」通訊協定。</span><span class="sxs-lookup"><span data-stu-id="948f8-198">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span> <span data-ttu-id="948f8-199">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="948f8-199">By default, SSL is not used.</span></span>

<span data-ttu-id="948f8-200">WS-Management 會加密透過網路傳輸的所有 Windows PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="948f8-200">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span> <span data-ttu-id="948f8-201">**UseSSL** 參數可讓您指定 HTTPS （而非 HTTP）的額外保護。</span><span class="sxs-lookup"><span data-stu-id="948f8-201">The **UseSSL** parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span> <span data-ttu-id="948f8-202">若用於連線的連接埠上無法使用 SSL，且您指定此參數，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="948f8-202">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="948f8-203">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="948f8-203">-ValueSet</span></span>

<span data-ttu-id="948f8-204">指定有助於修改管理資源的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="948f8-204">Specifies a hash table that helps modify a management resource.</span></span> <span data-ttu-id="948f8-205">您可以使用 **ResourceURI** 參數與 **SelectorSet** 參數來指定管理資源。</span><span class="sxs-lookup"><span data-stu-id="948f8-205">You specify the management resource using the **ResourceURI** parameter and the **SelectorSet** parameter.</span></span> <span data-ttu-id="948f8-206">**ValueSet** 參數的值必須是雜湊表。</span><span class="sxs-lookup"><span data-stu-id="948f8-206">The value of the **ValueSet** parameter must be a hash table.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="948f8-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="948f8-207">CommonParameters</span></span>

<span data-ttu-id="948f8-208">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="948f8-208">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="948f8-209">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="948f8-209">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="948f8-210">輸入</span><span class="sxs-lookup"><span data-stu-id="948f8-210">INPUTS</span></span>

### <span data-ttu-id="948f8-211">無</span><span class="sxs-lookup"><span data-stu-id="948f8-211">None</span></span>

<span data-ttu-id="948f8-212">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="948f8-212">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="948f8-213">輸出</span><span class="sxs-lookup"><span data-stu-id="948f8-213">OUTPUTS</span></span>

### <span data-ttu-id="948f8-214">無</span><span class="sxs-lookup"><span data-stu-id="948f8-214">None</span></span>

<span data-ttu-id="948f8-215">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="948f8-215">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="948f8-216">注意</span><span class="sxs-lookup"><span data-stu-id="948f8-216">NOTES</span></span>

<span data-ttu-id="948f8-217">`Set-WmiInstance`Cmdlet （Windows Management Instrumentation (WMI) Cmdlet）很類似。</span><span class="sxs-lookup"><span data-stu-id="948f8-217">The `Set-WmiInstance` cmdlet, a Windows Management Instrumentation (WMI) cmdlet, is similar.</span></span>
<span data-ttu-id="948f8-218">`Set-WmiInstance` 使用 DCOM 連線/傳輸層來建立或更新 WMI 實例。</span><span class="sxs-lookup"><span data-stu-id="948f8-218">`Set-WmiInstance` uses the DCOM connection/transport layer to create or update WMI instances.</span></span>

## <span data-ttu-id="948f8-219">相關連結</span><span class="sxs-lookup"><span data-stu-id="948f8-219">RELATED LINKS</span></span>

[<span data-ttu-id="948f8-220">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="948f8-220">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="948f8-221">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="948f8-221">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="948f8-222">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="948f8-222">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="948f8-223">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="948f8-223">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="948f8-224">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="948f8-224">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="948f8-225">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="948f8-225">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="948f8-226">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="948f8-226">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="948f8-227">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="948f8-227">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="948f8-228">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="948f8-228">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="948f8-229">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="948f8-229">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="948f8-230">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="948f8-230">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="948f8-231">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="948f8-231">Test-WSMan</span></span>](Test-WSMan.md)
