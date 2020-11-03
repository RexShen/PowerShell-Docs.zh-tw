---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: 9060f683372617b3a01365ceb81668c75986f46d
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205640"
---
# <span data-ttu-id="e1987-103">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e1987-103">Set-WSManInstance</span></span>

## <span data-ttu-id="e1987-104">概要</span><span class="sxs-lookup"><span data-stu-id="e1987-104">SYNOPSIS</span></span>
<span data-ttu-id="e1987-105">修改與資源相關的管理資訊。</span><span class="sxs-lookup"><span data-stu-id="e1987-105">Modifies the management information that is related to a resource.</span></span>

## <span data-ttu-id="e1987-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e1987-106">SYNTAX</span></span>

### <span data-ttu-id="e1987-107">ComputerName (預設值)</span><span class="sxs-lookup"><span data-stu-id="e1987-107">ComputerName (Default)</span></span>

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="e1987-108">URI</span><span class="sxs-lookup"><span data-stu-id="e1987-108">URI</span></span>

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="e1987-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e1987-109">DESCRIPTION</span></span>

<span data-ttu-id="e1987-110">Set-WSManInstance Cmdlet 會修改與資源相關的管理資訊。</span><span class="sxs-lookup"><span data-stu-id="e1987-110">The Set-WSManInstance cmdlet modifies the management information that is related to a resource.</span></span>

<span data-ttu-id="e1987-111">此 Cmdlet 使用 WinRM 連線/傳輸層來修改資訊。</span><span class="sxs-lookup"><span data-stu-id="e1987-111">This cmdlet uses the WinRM connection/transport layer to modify the information.</span></span>

## <span data-ttu-id="e1987-112">範例</span><span class="sxs-lookup"><span data-stu-id="e1987-112">EXAMPLES</span></span>

### <span data-ttu-id="e1987-113">範例1：停用本機電腦上的接聽程式</span><span class="sxs-lookup"><span data-stu-id="e1987-113">Example 1: Disable a listener on the local computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.171, ::1, 2001:4898:0:fff:0:5efe:172.30.168.171...}
```

<span data-ttu-id="e1987-114">此命令會停用本機電腦上的 https 接聽程式。</span><span class="sxs-lookup"><span data-stu-id="e1987-114">This command disables the https listener on the local computer.</span></span>

<span data-ttu-id="e1987-115">重要：符合指定的屬性時， *ValueSet* 參數會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e1987-115">Important: The *ValueSet* parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="e1987-116">例如，在這個命令中，</span><span class="sxs-lookup"><span data-stu-id="e1987-116">For example, in this command,</span></span>

<span data-ttu-id="e1987-117">這會失敗： `-ValueSet @{enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="e1987-117">This fails: `-ValueSet @{enabled="False"}`</span></span>

<span data-ttu-id="e1987-118">這會成功： `-ValueSet @{Enabled="False"}`</span><span class="sxs-lookup"><span data-stu-id="e1987-118">This succeeds: `-ValueSet @{Enabled="False"}`</span></span>

### <span data-ttu-id="e1987-119">範例2：在本機電腦上設定信封大小上限</span><span class="sxs-lookup"><span data-stu-id="e1987-119">Example 2: Set the maximum envelope size on the local computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config -ValueSet @{MaxEnvelopeSizekb = "200"}
```

```Output
cfg                 : http://schemas.microsoft.com/wbem/wsman/1/config
lang                : en-US
MaxEnvelopeSizekb   : 200
MaxTimeoutms        : 60000
MaxBatchItems       : 32000
MaxProviderRequests : 4294967295
Client              : Client
Service             : Service
Winrs               : Winrs
```

<span data-ttu-id="e1987-120">此命令會將本機電腦上的 MaxEnvelopeSizekb 值設定為 200。</span><span class="sxs-lookup"><span data-stu-id="e1987-120">This command sets the MaxEnvelopeSizekb value to 200 on the local computer.</span></span>

<span data-ttu-id="e1987-121">重要：比對指定的屬性時，ValueSet 參數會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e1987-121">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="e1987-122">例如，使用上述命令。</span><span class="sxs-lookup"><span data-stu-id="e1987-122">For example, using the above command.</span></span>

<span data-ttu-id="e1987-123">這會失敗：-ValueSet @ {MaxEnvelopeSizeKB = "200"}</span><span class="sxs-lookup"><span data-stu-id="e1987-123">This fails:     -ValueSet @{MaxEnvelopeSizeKB ="200"}</span></span>

<span data-ttu-id="e1987-124">這會成功：-ValueSet @ {MaxEnvelopeSizekb = "200"}</span><span class="sxs-lookup"><span data-stu-id="e1987-124">This succeeds:  -ValueSet @{MaxEnvelopeSizekb ="200"}</span></span>

### <span data-ttu-id="e1987-125">範例3：停用遠端電腦上的接聽程式</span><span class="sxs-lookup"><span data-stu-id="e1987-125">Example 3: Disable a listener on a remote computer</span></span>

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -ComputerName SERVER02 -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.172, ::1, 2001:4898:0:fff:0:5efe:172.30.168.172...}
```

<span data-ttu-id="e1987-126">此命令會停用遠端電腦 SERVER02 上的 https 接聽程式。</span><span class="sxs-lookup"><span data-stu-id="e1987-126">This command disables the https listener on the remote computer SERVER02.</span></span>

<span data-ttu-id="e1987-127">重要：比對指定的屬性時，ValueSet 參數會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e1987-127">Important: The ValueSet parameter is case-sensitive when matching the properties specified.</span></span>

<span data-ttu-id="e1987-128">例如，使用上述命令。</span><span class="sxs-lookup"><span data-stu-id="e1987-128">For example, using the above command.</span></span>

<span data-ttu-id="e1987-129">這會失敗：-ValueSet @ {enabled = "False"}</span><span class="sxs-lookup"><span data-stu-id="e1987-129">This fails:     -ValueSet @{enabled="False"}</span></span>

<span data-ttu-id="e1987-130">這會成功：-ValueSet @ {Enabled = "False"}</span><span class="sxs-lookup"><span data-stu-id="e1987-130">This succeeds:  -ValueSet @{Enabled="False"}</span></span>

## <span data-ttu-id="e1987-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1987-131">PARAMETERS</span></span>

### <span data-ttu-id="e1987-132">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="e1987-132">-ApplicationName</span></span>

<span data-ttu-id="e1987-133">指定連線中的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="e1987-133">Specifies the application name in the connection.</span></span>
<span data-ttu-id="e1987-134">ApplicationName 參數的預設值是 "WSMAN"。</span><span class="sxs-lookup"><span data-stu-id="e1987-134">The default value of the ApplicationName parameter is "WSMAN".</span></span>
<span data-ttu-id="e1987-135">遠端端點的完整識別碼使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="e1987-135">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="e1987-136">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="e1987-136">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="e1987-137">例如：</span><span class="sxs-lookup"><span data-stu-id="e1987-137">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="e1987-138">裝載工作階段的網際網路資訊服務 (IIS)，會使用此端點轉送要求至指定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1987-138">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="e1987-139">此預設設定 "WSMAN" 適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="e1987-139">This default setting of "WSMAN" is appropriate for most uses.</span></span>
<span data-ttu-id="e1987-140">此參數是設計用於下列狀況：多部電腦建立遠端連線至同一部執行 Windows PowerShell 的電腦。</span><span class="sxs-lookup"><span data-stu-id="e1987-140">This parameter is designed to be used when numerous computers establish remote connections to one computer that is running Windows PowerShell.</span></span>
<span data-ttu-id="e1987-141">在此案例中，IIS 會裝載管理 Web 服務 (WS-Management) 以獲得較佳效率。</span><span class="sxs-lookup"><span data-stu-id="e1987-141">In this case, IIS hosts Web Services for Management (WS-Management ) for efficiency.</span></span>

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

### <span data-ttu-id="e1987-142">-Authentication</span><span class="sxs-lookup"><span data-stu-id="e1987-142">-Authentication</span></span>

<span data-ttu-id="e1987-143">指定用於伺服器的驗證機制。</span><span class="sxs-lookup"><span data-stu-id="e1987-143">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="e1987-144">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="e1987-144">Possible values are:</span></span>

- <span data-ttu-id="e1987-145">Basic：Basic 配置使用純文字方式將使用者名稱與密碼傳送至伺服器或 Proxy。</span><span class="sxs-lookup"><span data-stu-id="e1987-145">Basic: Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="e1987-146">Default：使用 WS-Management 通訊協定實作的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="e1987-146">Default : Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="e1987-147">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="e1987-147">This is the default.</span></span>
- <span data-ttu-id="e1987-148">Digest：Digest 為查問-回應配置，於查問中使用伺服器指定的資料字串。</span><span class="sxs-lookup"><span data-stu-id="e1987-148">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="e1987-149">Kerberos：用戶端電腦和伺服器使用 Kerberos 憑證相互驗證。</span><span class="sxs-lookup"><span data-stu-id="e1987-149">Kerberos: The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="e1987-150">Negotiate：Negotiate 為查問-回應配置，會與伺服器或 Proxy 交涉以決定要用於驗證的配置。</span><span class="sxs-lookup"><span data-stu-id="e1987-150">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="e1987-151">例如，此參數值允許交涉以決定要使用 Kerberos 通訊協定或 NTLM。</span><span class="sxs-lookup"><span data-stu-id="e1987-151">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="e1987-152">CredSSP：使用允許使用者委派認證的「認證安全性支援提供者 (CredSSP)」驗證。</span><span class="sxs-lookup"><span data-stu-id="e1987-152">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="e1987-153">此選項是針對下列命令所設計：命令在遠端電腦上執行，但是收集來自其他遠端電腦上的資料，或是在其他遠端電腦上執行其他命令。</span><span class="sxs-lookup"><span data-stu-id="e1987-153">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="e1987-154">注意：CredSSP 會將使用者認證從本機電腦委派給遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="e1987-154">Caution: CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="e1987-155">此做法會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="e1987-155">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="e1987-156">若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="e1987-156">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1987-157">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="e1987-157">-CertificateThumbprint</span></span>

<span data-ttu-id="e1987-158">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="e1987-158">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="e1987-159">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="e1987-159">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="e1987-160">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="e1987-160">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="e1987-161">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="e1987-161">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="e1987-162">若要取得憑證指紋，請使用 PowerShell Cert：磁片磁碟機中的 Get-Item 或 Get-ChildItem 命令。</span><span class="sxs-lookup"><span data-stu-id="e1987-162">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="e1987-163">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="e1987-163">-ComputerName</span></span>

<span data-ttu-id="e1987-164">指定要執行管理作業的電腦。</span><span class="sxs-lookup"><span data-stu-id="e1987-164">Specifies the computer against which you want to run the management operation.</span></span>
<span data-ttu-id="e1987-165">值可以是完整網域名稱、NetBIOS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="e1987-165">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="e1987-166">使用本機電腦名稱、使用 localhost，或使用句點 (.) 來指定本機電腦。</span><span class="sxs-lookup"><span data-stu-id="e1987-166">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="e1987-167">預設值是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="e1987-167">The local computer is the default.</span></span>
<span data-ttu-id="e1987-168">當遠端電腦與使用者位於不同網域，您必須使用完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="e1987-168">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="e1987-169">您可以使用管線將此參數的值傳送至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e1987-169">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="e1987-170">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="e1987-170">-ConnectionURI</span></span>

<span data-ttu-id="e1987-171">指定連線端點。</span><span class="sxs-lookup"><span data-stu-id="e1987-171">Specifies the connection endpoint.</span></span>
<span data-ttu-id="e1987-172">此字串的格式為：</span><span class="sxs-lookup"><span data-stu-id="e1987-172">The format of this string is:</span></span>

<span data-ttu-id="e1987-173">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="e1987-173">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="e1987-174">下列字串是此參數的正確格式值：</span><span class="sxs-lookup"><span data-stu-id="e1987-174">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="e1987-175">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="e1987-175">The URI must be fully qualified .</span></span>

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

### <span data-ttu-id="e1987-176">-Credential</span><span class="sxs-lookup"><span data-stu-id="e1987-176">-Credential</span></span>

<span data-ttu-id="e1987-177">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="e1987-177">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="e1987-178">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="e1987-178">The default is the current user.</span></span>
<span data-ttu-id="e1987-179">輸入使用者名稱，例如 "User01"、"Domain01\User01" 或 " User@Domain.com "。</span><span class="sxs-lookup"><span data-stu-id="e1987-179">Type a user name, such as "User01", "Domain01\User01", or "User@Domain.com".</span></span>
<span data-ttu-id="e1987-180">或者，輸入 PSCredential 物件，例如 Get-Credential Cmdlet 傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="e1987-180">Or, enter a PSCredential object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="e1987-181">當您輸入使用者名稱時，會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="e1987-181">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="e1987-182">-Dialect</span><span class="sxs-lookup"><span data-stu-id="e1987-182">-Dialect</span></span>

<span data-ttu-id="e1987-183">指定要在篩選述詞中使用的方言。</span><span class="sxs-lookup"><span data-stu-id="e1987-183">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="e1987-184">這可以是遠端服務支援的任何方言。</span><span class="sxs-lookup"><span data-stu-id="e1987-184">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="e1987-185">下列別名可用於方言 URI：</span><span class="sxs-lookup"><span data-stu-id="e1987-185">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="e1987-186">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="e1987-186">WQL: `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="e1987-187">選擇： `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="e1987-187">Selector: `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="e1987-188">協會： `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="e1987-188">Association: `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: http://schemas.microsoft.com/wbem/wsman/1/WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1987-189">-FilePath</span><span class="sxs-lookup"><span data-stu-id="e1987-189">-FilePath</span></span>

<span data-ttu-id="e1987-190">指定用來更新管理資源之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e1987-190">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="e1987-191">您可以使用 ResourceURI 參數與 SelectorSet 參數來指定管理資源。</span><span class="sxs-lookup"><span data-stu-id="e1987-191">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter .</span></span>
<span data-ttu-id="e1987-192">例如，下列命令使用 FilePath 參數：</span><span class="sxs-lookup"><span data-stu-id="e1987-192">For example, the following command uses the FilePath parameter:</span></span>

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

<span data-ttu-id="e1987-193">此命令會使用來自檔案的輸入，在多工緩衝處理器服務上呼叫 StopService 方法。</span><span class="sxs-lookup"><span data-stu-id="e1987-193">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="e1987-194">該檔案 (Input.xml) 包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="e1987-194">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1987-195">-Fragment</span><span class="sxs-lookup"><span data-stu-id="e1987-195">-Fragment</span></span>

<span data-ttu-id="e1987-196">指定要針對所指定操作在執行個體中更新或抓取的區段。</span><span class="sxs-lookup"><span data-stu-id="e1987-196">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="e1987-197">例如，若要取得多工緩衝處理器服務的狀態，請指定 "-Fragment Status"。</span><span class="sxs-lookup"><span data-stu-id="e1987-197">For example, to get the status of a spooler service, specify "-Fragment Status".</span></span>

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

### <span data-ttu-id="e1987-198">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="e1987-198">-OptionSet</span></span>

<span data-ttu-id="e1987-199">將一組切換參數傳遞給服務，以修改或精簡要求的本質。</span><span class="sxs-lookup"><span data-stu-id="e1987-199">Passes a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="e1987-200">這些切換參數類似於命令列殼層中使用的切換參數，因為都是服務特定的切換參數。</span><span class="sxs-lookup"><span data-stu-id="e1987-200">These are similar to switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="e1987-201">您可以指定任意數目的選項。</span><span class="sxs-lookup"><span data-stu-id="e1987-201">Any number of options can be specified.</span></span>

<span data-ttu-id="e1987-202">下列範例示範的語法可傳遞 a、b 與 c 參數的值 1、2 與 3：</span><span class="sxs-lookup"><span data-stu-id="e1987-202">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

<span data-ttu-id="e1987-203">-OptionSet @{a=1;b=2;c=3}</span><span class="sxs-lookup"><span data-stu-id="e1987-203">-OptionSet @{a=1;b=2;c=3}</span></span>

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

### <span data-ttu-id="e1987-204">-Port</span><span class="sxs-lookup"><span data-stu-id="e1987-204">-Port</span></span>

<span data-ttu-id="e1987-205">指定用戶端連線 WinRM 服務時所使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="e1987-205">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="e1987-206">傳輸為 HTTP 時，預設連接埠為 80。</span><span class="sxs-lookup"><span data-stu-id="e1987-206">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="e1987-207">傳輸為 HTTPS 時，預設連接埠為 443。</span><span class="sxs-lookup"><span data-stu-id="e1987-207">When the transport is HTTPS, the default port is 443.</span></span>
<span data-ttu-id="e1987-208">使用 HTTPS 做為傳輸時，ComputerName 參數的值必須符合伺服器憑證一般名稱 (CN)。</span><span class="sxs-lookup"><span data-stu-id="e1987-208">When you use HTTPS as the transport, the value of the ComputerName parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="e1987-209">不過，如果 SkipCNCheck 參數指定為 SessionOption 參數的一部分，則伺服器憑證一般名稱不必符合伺服器主機名稱。</span><span class="sxs-lookup"><span data-stu-id="e1987-209">However, if the SkipCNCheck parameter is specified as part of the SessionOption parameter, then the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="e1987-210">SkipCNCheck 參數只能用於信任的電腦。</span><span class="sxs-lookup"><span data-stu-id="e1987-210">The SkipCNCheck parameter should be used only for trusted machines.</span></span>

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

### <span data-ttu-id="e1987-211">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="e1987-211">-ResourceURI</span></span>

<span data-ttu-id="e1987-212">包含資源類別或執行個體的「統一資源識別項 (URI)」。</span><span class="sxs-lookup"><span data-stu-id="e1987-212">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="e1987-213">URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。</span><span class="sxs-lookup"><span data-stu-id="e1987-213">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="e1987-214">URI 是由前置詞與資源路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="e1987-214">A URI consists of a prefix and a path to a resource.</span></span>
<span data-ttu-id="e1987-215">例如：</span><span class="sxs-lookup"><span data-stu-id="e1987-215">For example:</span></span>

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

### <span data-ttu-id="e1987-216">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="e1987-216">-SelectorSet</span></span>

<span data-ttu-id="e1987-217">指定一組值組，用來選取特定管理資源執行個體。</span><span class="sxs-lookup"><span data-stu-id="e1987-217">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="e1987-218">若存在超過一個以上的資源執行個體，請使用 SelectorSet 參數。</span><span class="sxs-lookup"><span data-stu-id="e1987-218">The SelectorSet parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="e1987-219">SelectorSet 參數的值必須為雜湊表。</span><span class="sxs-lookup"><span data-stu-id="e1987-219">The value of the SelectorSet parameter must be a hash table.</span></span>
<span data-ttu-id="e1987-220">下列範例顯示如何輸入此參數的值：</span><span class="sxs-lookup"><span data-stu-id="e1987-220">The following example shows how to enter a value for this parameter:</span></span>

<span data-ttu-id="e1987-221">-SelectorSet @{Name="WinRM";ID="yyy"}</span><span class="sxs-lookup"><span data-stu-id="e1987-221">-SelectorSet @{Name="WinRM";ID="yyy"}</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e1987-222">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="e1987-222">-SessionOption</span></span>

<span data-ttu-id="e1987-223">定義 WS-Management 工作階段的一組擴充選項。</span><span class="sxs-lookup"><span data-stu-id="e1987-223">Defines a set of extended options for the WS-Management session.</span></span>
<span data-ttu-id="e1987-224">輸入使用 New-WSManSessionOption Cmdlet 所建立的 SessionOption 物件。</span><span class="sxs-lookup"><span data-stu-id="e1987-224">Enter a SessionOption object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="e1987-225">如需可用選項的詳細資訊，請參閱 New-WSManSessionOption。</span><span class="sxs-lookup"><span data-stu-id="e1987-225">For more information about the options that are available, see New-WSManSessionOption.</span></span>

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

### <span data-ttu-id="e1987-226">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="e1987-226">-UseSSL</span></span>

<span data-ttu-id="e1987-227">指定建立遠端電腦連線時，應使用「安全通訊端層 (SSL)」通訊協定。</span><span class="sxs-lookup"><span data-stu-id="e1987-227">Specifies that the Secure Sockets Layer (SSL) protocol should be used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="e1987-228">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="e1987-228">By default, SSL is not used.</span></span>

<span data-ttu-id="e1987-229">WS-Management 會加密透過網路傳輸的所有 Windows PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="e1987-229">WS-Management encrypts all the Windows PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="e1987-230">UseSSL 參數可讓您指定 HTTPS 額外保護，以取代 HTTP。</span><span class="sxs-lookup"><span data-stu-id="e1987-230">The UseSSL parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="e1987-231">若用於連線的連接埠上無法使用 SSL，且您指定此參數，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="e1987-231">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="e1987-232">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="e1987-232">-ValueSet</span></span>

<span data-ttu-id="e1987-233">指定有助於修改管理資源的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="e1987-233">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="e1987-234">您可以使用 ResourceURI 參數與 SelectorSet 參數來指定管理資源。</span><span class="sxs-lookup"><span data-stu-id="e1987-234">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter.</span></span>
<span data-ttu-id="e1987-235">ValueSet 參數的值必須為雜湊表。</span><span class="sxs-lookup"><span data-stu-id="e1987-235">The value of the ValueSet parameter must be a hash table.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e1987-236">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1987-236">CommonParameters</span></span>

<span data-ttu-id="e1987-237">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e1987-237">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1987-238">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="e1987-238">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="e1987-239">輸入</span><span class="sxs-lookup"><span data-stu-id="e1987-239">INPUTS</span></span>

### <span data-ttu-id="e1987-240">無</span><span class="sxs-lookup"><span data-stu-id="e1987-240">None</span></span>

<span data-ttu-id="e1987-241">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="e1987-241">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="e1987-242">輸出</span><span class="sxs-lookup"><span data-stu-id="e1987-242">OUTPUTS</span></span>

### <span data-ttu-id="e1987-243">無</span><span class="sxs-lookup"><span data-stu-id="e1987-243">None</span></span>

<span data-ttu-id="e1987-244">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="e1987-244">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e1987-245">注意</span><span class="sxs-lookup"><span data-stu-id="e1987-245">NOTES</span></span>

## <span data-ttu-id="e1987-246">相關連結</span><span class="sxs-lookup"><span data-stu-id="e1987-246">RELATED LINKS</span></span>

[<span data-ttu-id="e1987-247">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="e1987-247">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="e1987-248">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e1987-248">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="e1987-249">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="e1987-249">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="e1987-250">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e1987-250">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="e1987-251">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="e1987-251">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="e1987-252">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e1987-252">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="e1987-253">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="e1987-253">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="e1987-254">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e1987-254">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="e1987-255">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="e1987-255">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="e1987-256">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="e1987-256">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="e1987-257">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="e1987-257">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="e1987-258">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="e1987-258">Test-WSMan</span></span>](Test-WSMan.md)

