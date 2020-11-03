---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: 1eeeb912ab32ec5334959daba1e352f20fec15b1
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208687"
---
# <span data-ttu-id="c87a9-103">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="c87a9-103">Invoke-WSManAction</span></span>

## <span data-ttu-id="c87a9-104">概要</span><span class="sxs-lookup"><span data-stu-id="c87a9-104">SYNOPSIS</span></span>
<span data-ttu-id="c87a9-105">在由資源 URI 與選取器所指定的物件上叫用動作。</span><span class="sxs-lookup"><span data-stu-id="c87a9-105">Invokes an action on the object that is specified by the Resource URI and by the selectors.</span></span>

## <span data-ttu-id="c87a9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c87a9-106">SYNTAX</span></span>

### <span data-ttu-id="c87a9-107">URI (預設) </span><span class="sxs-lookup"><span data-stu-id="c87a9-107">URI (Default)</span></span>

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="c87a9-108">ComputerName</span><span class="sxs-lookup"><span data-stu-id="c87a9-108">ComputerName</span></span>

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="c87a9-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c87a9-109">DESCRIPTION</span></span>

<span data-ttu-id="c87a9-110">Invoke-WSManAction 會在由 RESOURCE_URI 所指定 (其中，參數是以機碼/值組的形式指定) 的物件上執行動作。</span><span class="sxs-lookup"><span data-stu-id="c87a9-110">The Invoke-WSManAction runs an action on the object that is specified by RESOURCE_URI, where parameters are specified by key value pairs.</span></span>

<span data-ttu-id="c87a9-111">此 Cmdlet 會使用 WSMan 連線/傳輸層來執行動作。</span><span class="sxs-lookup"><span data-stu-id="c87a9-111">This cmdlet uses the WSMan connection/transport layer to run the action.</span></span>

## <span data-ttu-id="c87a9-112">範例</span><span class="sxs-lookup"><span data-stu-id="c87a9-112">EXAMPLES</span></span>

### <span data-ttu-id="c87a9-113">範例 1</span><span class="sxs-lookup"><span data-stu-id="c87a9-113">Example 1</span></span>

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="c87a9-114">此命令會呼叫對應至多工緩衝處理器服務之 Win32_Service WMI 類別執行個體的 StartService 方法。</span><span class="sxs-lookup"><span data-stu-id="c87a9-114">This command calls the StartService method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>

<span data-ttu-id="c87a9-115">傳回值指出動作是否成功。</span><span class="sxs-lookup"><span data-stu-id="c87a9-115">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="c87a9-116">在此案例中，0 的傳回值表示成功。</span><span class="sxs-lookup"><span data-stu-id="c87a9-116">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="c87a9-117">5 的傳回值表示服務已啟動。</span><span class="sxs-lookup"><span data-stu-id="c87a9-117">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="c87a9-118">範例 2</span><span class="sxs-lookup"><span data-stu-id="c87a9-118">Example 2</span></span>

```powershell
Invoke-WSManAction -Action stopservice -ResourceURI wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:input.xml -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="c87a9-119">此命令會使用來自檔案的輸入，在多工緩衝處理器服務上呼叫 StopService 方法。</span><span class="sxs-lookup"><span data-stu-id="c87a9-119">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="c87a9-120">該檔案 (Input.xml) 包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="c87a9-120">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

<span data-ttu-id="c87a9-121">傳回值指出動作是否成功。</span><span class="sxs-lookup"><span data-stu-id="c87a9-121">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="c87a9-122">在此案例中，0 的傳回值表示成功。</span><span class="sxs-lookup"><span data-stu-id="c87a9-122">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="c87a9-123">5 的傳回值表示服務已啟動。</span><span class="sxs-lookup"><span data-stu-id="c87a9-123">A return value of 5 indicates that the service is already started.</span></span>

### <span data-ttu-id="c87a9-124">範例 3</span><span class="sxs-lookup"><span data-stu-id="c87a9-124">Example 3</span></span>

```powershell
Invoke-WSManAction -Action create -ResourceURI wmicimv2/win32_process -ValueSet @{commandline="notepad.exe";currentdirectory="C:\"}
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Process
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ProcessId   : 6356
ReturnValue : 0
```

<span data-ttu-id="c87a9-125">此命令會呼叫 Win32_Process 類別的 Create 方法。</span><span class="sxs-lookup"><span data-stu-id="c87a9-125">This command calls the Create method of the Win32_Process class.</span></span>
<span data-ttu-id="c87a9-126">它會將方法傳遞給兩個參數值，Notepad.exe 和 "C： \" 。</span><span class="sxs-lookup"><span data-stu-id="c87a9-126">It passes the method two parameter values, Notepad.exe and "C:\".</span></span>
<span data-ttu-id="c87a9-127">如此一來，就會建立新的程式來執行「記事本」，而新進程的目前的目錄會設定為 "C： \" 。</span><span class="sxs-lookup"><span data-stu-id="c87a9-127">As a result, a new process is created to run Notepad, and the current directory of the new process is set to "C:\".</span></span>

### <span data-ttu-id="c87a9-128">範例 4</span><span class="sxs-lookup"><span data-stu-id="c87a9-128">Example 4</span></span>

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -ComputerName server01 -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

<span data-ttu-id="c87a9-129">此命令會呼叫對應至多工緩衝處理器服務之 Win32_Service WMI 類別執行個體的 StartService 方法。</span><span class="sxs-lookup"><span data-stu-id="c87a9-129">This command calls the StartService method of the Win32_Service WMI class instance that corresponds to the Spooler service.</span></span>
<span data-ttu-id="c87a9-130">因為已指定 ComputerName 參數，該命令會針對遠端 server01 電腦執行。</span><span class="sxs-lookup"><span data-stu-id="c87a9-130">Because the ComputerName parameter is specified, the command runs against the remote server01 computer.</span></span>

<span data-ttu-id="c87a9-131">傳回值指出動作是否成功。</span><span class="sxs-lookup"><span data-stu-id="c87a9-131">The return value indicates whether the action was successful.</span></span>
<span data-ttu-id="c87a9-132">在此案例中，0 的傳回值表示成功。</span><span class="sxs-lookup"><span data-stu-id="c87a9-132">In this case, a return value of 0 indicates success.</span></span>
<span data-ttu-id="c87a9-133">5 的傳回值表示服務已啟動。</span><span class="sxs-lookup"><span data-stu-id="c87a9-133">A return value of 5 indicates that the service is already started.</span></span>

## <span data-ttu-id="c87a9-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c87a9-134">PARAMETERS</span></span>

### <span data-ttu-id="c87a9-135">-Action</span><span class="sxs-lookup"><span data-stu-id="c87a9-135">-Action</span></span>

<span data-ttu-id="c87a9-136">指定要在由 ResourceURI 與選取器所指定之管理物件上執行的方法。</span><span class="sxs-lookup"><span data-stu-id="c87a9-136">Specifies the method to run on the management object specified by the ResourceURI and selectors.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c87a9-137">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="c87a9-137">-ApplicationName</span></span>

<span data-ttu-id="c87a9-138">指定連線中的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="c87a9-138">Specifies the application name in the connection.</span></span>
<span data-ttu-id="c87a9-139">ApplicationName 參數的預設值是 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="c87a9-139">The default value of the ApplicationName parameter is WSMAN.</span></span>
<span data-ttu-id="c87a9-140">遠端端點的完整識別碼使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="c87a9-140">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="c87a9-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="c87a9-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="c87a9-142">例如：</span><span class="sxs-lookup"><span data-stu-id="c87a9-142">For example:</span></span>

`http://server01:8080/WSMAN`

<span data-ttu-id="c87a9-143">裝載工作階段的網際網路資訊服務 (IIS)，會使用此端點轉送要求至指定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c87a9-143">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="c87a9-144">此預設設定 "WSMAN" 適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="c87a9-144">This default setting of "WSMAN" is appropriate for most uses.</span></span>
<span data-ttu-id="c87a9-145">此參數是設計用於下列狀況：多部電腦建立遠端連線至同一部執行 Windows PowerShell 的電腦。</span><span class="sxs-lookup"><span data-stu-id="c87a9-145">This parameter is designed to be used when numerous computers establish remote connections to one computer running Windows PowerShell.</span></span>
<span data-ttu-id="c87a9-146">在此案例中，IIS 會裝載管理 Web 服務 (WS-Management) 以獲得較佳效率。</span><span class="sxs-lookup"><span data-stu-id="c87a9-146">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="c87a9-147">-Authentication</span><span class="sxs-lookup"><span data-stu-id="c87a9-147">-Authentication</span></span>

<span data-ttu-id="c87a9-148">指定用於伺服器的驗證機制。</span><span class="sxs-lookup"><span data-stu-id="c87a9-148">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="c87a9-149">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="c87a9-149">Possible values are:</span></span>

- <span data-ttu-id="c87a9-150">Basic：Basic 配置使用純文字方式將使用者名稱與密碼傳送至伺服器或 Proxy。</span><span class="sxs-lookup"><span data-stu-id="c87a9-150">Basic: Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="c87a9-151">Default：使用 WS-Management 通訊協定實作的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="c87a9-151">Default : Use the authentication method implemented by the WS-Management protocol.</span></span> <span data-ttu-id="c87a9-152">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="c87a9-152">This is the default.</span></span>
- <span data-ttu-id="c87a9-153">Digest：Digest 為查問-回應配置，於查問中使用伺服器指定的資料字串。</span><span class="sxs-lookup"><span data-stu-id="c87a9-153">Digest: Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="c87a9-154">Kerberos：用戶端電腦和伺服器使用 Kerberos 憑證相互驗證。</span><span class="sxs-lookup"><span data-stu-id="c87a9-154">Kerberos: The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="c87a9-155">Negotiate：Negotiate 為查問-回應配置，會與伺服器或 Proxy 交涉以決定要用於驗證的配置。</span><span class="sxs-lookup"><span data-stu-id="c87a9-155">Negotiate: Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span> <span data-ttu-id="c87a9-156">例如，此參數值允許交涉以決定要使用 Kerberos 通訊協定或 NTLM。</span><span class="sxs-lookup"><span data-stu-id="c87a9-156">For example, this parameter value allows negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="c87a9-157">CredSSP：使用允許使用者委派認證的「認證安全性支援提供者 (CredSSP)」驗證。</span><span class="sxs-lookup"><span data-stu-id="c87a9-157">CredSSP: Use Credential Security Support Provider (CredSSP) authentication, which allows the user to delegate credentials.</span></span> <span data-ttu-id="c87a9-158">此選項是針對下列命令所設計：命令在遠端電腦上執行，但是收集來自其他遠端電腦上的資料，或是在其他遠端電腦上執行其他命令。</span><span class="sxs-lookup"><span data-stu-id="c87a9-158">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="c87a9-159">注意：CredSSP 會將使用者認證從本機電腦委派給遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="c87a9-159">Caution: CredSSP delegates the user's credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="c87a9-160">此做法會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="c87a9-160">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="c87a9-161">若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="c87a9-161">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="c87a9-162">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="c87a9-162">-CertificateThumbprint</span></span>

<span data-ttu-id="c87a9-163">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="c87a9-163">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="c87a9-164">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="c87a9-164">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="c87a9-165">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="c87a9-165">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="c87a9-166">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="c87a9-166">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="c87a9-167">若要取得憑證指紋，請在 Windows PowerShell Cert: 磁碟機中使用 Get-Item 或 Get-ChildItem 命令。</span><span class="sxs-lookup"><span data-stu-id="c87a9-167">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the Windows PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="c87a9-168">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="c87a9-168">-ComputerName</span></span>

<span data-ttu-id="c87a9-169">指定要執行管理作業的電腦。</span><span class="sxs-lookup"><span data-stu-id="c87a9-169">Specifies the computer against which you want to run the management operation.</span></span>
<span data-ttu-id="c87a9-170">值可以是完整網域名稱、NetBIOS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="c87a9-170">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="c87a9-171">使用本機電腦名稱、使用 localhost，或使用句點 (.) 來指定本機電腦。</span><span class="sxs-lookup"><span data-stu-id="c87a9-171">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="c87a9-172">預設值是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="c87a9-172">The local computer is the default.</span></span>
<span data-ttu-id="c87a9-173">當遠端電腦與使用者位於不同網域，您必須使用完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="c87a9-173">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="c87a9-174">您可以使用管線將此參數的值傳送至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c87a9-174">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="c87a9-175">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="c87a9-175">-ConnectionURI</span></span>

<span data-ttu-id="c87a9-176">指定連線端點。</span><span class="sxs-lookup"><span data-stu-id="c87a9-176">Specifies the connection endpoint.</span></span>
<span data-ttu-id="c87a9-177">此字串的格式為：</span><span class="sxs-lookup"><span data-stu-id="c87a9-177">The format of this string is:</span></span>

<span data-ttu-id="c87a9-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="c87a9-178">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="c87a9-179">下列字串是此參數的正確格式值：</span><span class="sxs-lookup"><span data-stu-id="c87a9-179">The following string is a properly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="c87a9-180">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="c87a9-180">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="c87a9-181">-Credential</span><span class="sxs-lookup"><span data-stu-id="c87a9-181">-Credential</span></span>

<span data-ttu-id="c87a9-182">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="c87a9-182">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="c87a9-183">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="c87a9-183">The default is the current user.</span></span>
<span data-ttu-id="c87a9-184">輸入使用者名稱，例如 "User01"、"Domain01\User01" 或 User@Domain.com 。</span><span class="sxs-lookup"><span data-stu-id="c87a9-184">Type a user name, such as "User01", "Domain01\User01", or User@Domain.com.</span></span>
<span data-ttu-id="c87a9-185">或者，輸入 PSCredential 物件，例如 Get-Credential Cmdlet 傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="c87a9-185">Or, enter a PSCredential object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="c87a9-186">當您輸入使用者名稱時，會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="c87a9-186">When you type a user name, you will be prompted for a password.</span></span>

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

### <span data-ttu-id="c87a9-187">-FilePath</span><span class="sxs-lookup"><span data-stu-id="c87a9-187">-FilePath</span></span>

<span data-ttu-id="c87a9-188">指定用來更新管理資源之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="c87a9-188">Specifies the path of a file that is used to update a management resource.</span></span>
<span data-ttu-id="c87a9-189">您可以使用 ResourceURI 參數與 SelectorSet 參數來指定管理資源。</span><span class="sxs-lookup"><span data-stu-id="c87a9-189">You specify the management resource by using the ResourceURI parameter and the SelectorSet parameter.</span></span>
<span data-ttu-id="c87a9-190">例如，下列命令使用 FilePath 參數：</span><span class="sxs-lookup"><span data-stu-id="c87a9-190">For example, the following command uses the FilePath parameter:</span></span>

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

<span data-ttu-id="c87a9-191">此命令會使用來自檔案的輸入，在多工緩衝處理器服務上呼叫 StopService 方法。</span><span class="sxs-lookup"><span data-stu-id="c87a9-191">This command calls the StopService method on the Spooler service by using input from a file.</span></span>
<span data-ttu-id="c87a9-192">該檔案 (Input.xml) 包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="c87a9-192">The file, Input.xml, contains the following content:</span></span>

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

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

### <span data-ttu-id="c87a9-193">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="c87a9-193">-OptionSet</span></span>

<span data-ttu-id="c87a9-194">將一組參數傳遞至服務，以修改或精簡要求的本質。</span><span class="sxs-lookup"><span data-stu-id="c87a9-194">Passes a set of switches  to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="c87a9-195">這些切換參數類似於命令列殼層中使用的切換參數，因為都是服務特定的切換參數。</span><span class="sxs-lookup"><span data-stu-id="c87a9-195">These are similar to switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="c87a9-196">您可以指定任意數目的選項。</span><span class="sxs-lookup"><span data-stu-id="c87a9-196">Any number of options  can be specified.</span></span>

<span data-ttu-id="c87a9-197">下列範例示範的語法可傳遞 a、b 與 c 參數的值 1、2 與 3：</span><span class="sxs-lookup"><span data-stu-id="c87a9-197">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c87a9-198">-Port</span><span class="sxs-lookup"><span data-stu-id="c87a9-198">-Port</span></span>

<span data-ttu-id="c87a9-199">指定用戶端連線 WinRM 服務時所使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="c87a9-199">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="c87a9-200">傳輸為 HTTP 時，預設連接埠為 80。</span><span class="sxs-lookup"><span data-stu-id="c87a9-200">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="c87a9-201">傳輸為 HTTPS 時，預設連接埠為 443。</span><span class="sxs-lookup"><span data-stu-id="c87a9-201">When the transport is HTTPS, the default port is 443.</span></span>
<span data-ttu-id="c87a9-202">使用 HTTPS 做為傳輸時，ComputerName 參數的值必須符合伺服器憑證一般名稱 (CN)。</span><span class="sxs-lookup"><span data-stu-id="c87a9-202">When you use HTTPS as the transport, the value of the ComputerName parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="c87a9-203">不過，如果 SkipCNCheck 參數指定為 SessionOption 參數的一部分，則伺服器憑證一般名稱不必符合伺服器主機名稱。</span><span class="sxs-lookup"><span data-stu-id="c87a9-203">However, if the SkipCNCheck parameter is specified as part of the SessionOption parameter, then the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="c87a9-204">SkipCNCheck 參數只能用於信任的電腦。</span><span class="sxs-lookup"><span data-stu-id="c87a9-204">The SkipCNCheck parameter should be used only for trusted machines.</span></span>

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

### <span data-ttu-id="c87a9-205">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="c87a9-205">-ResourceURI</span></span>

<span data-ttu-id="c87a9-206">包含資源類別或執行個體的「統一資源識別項 (URI)」。</span><span class="sxs-lookup"><span data-stu-id="c87a9-206">Contains the Uniform Resource Identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="c87a9-207">URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。</span><span class="sxs-lookup"><span data-stu-id="c87a9-207">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="c87a9-208">URI 是由前置詞與資源路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="c87a9-208">A URI consists of a prefix and a path to a resource.</span></span>
<span data-ttu-id="c87a9-209">例如：</span><span class="sxs-lookup"><span data-stu-id="c87a9-209">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c87a9-210">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="c87a9-210">-SelectorSet</span></span>

<span data-ttu-id="c87a9-211">指定一組值組，用來選取特定管理資源執行個體。</span><span class="sxs-lookup"><span data-stu-id="c87a9-211">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="c87a9-212">當有一個以上的資源實例存在時，就會使用 *SelectorSet* 。</span><span class="sxs-lookup"><span data-stu-id="c87a9-212">*SelectorSet* is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="c87a9-213">*SelectorSet* 的值必須是雜湊表。</span><span class="sxs-lookup"><span data-stu-id="c87a9-213">The value of *SelectorSet* must be a hash table.</span></span>

<span data-ttu-id="c87a9-214">下列範例顯示如何輸入此參數的值：</span><span class="sxs-lookup"><span data-stu-id="c87a9-214">The following example shows how to enter a value for this parameter:</span></span>

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c87a9-215">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="c87a9-215">-SessionOption</span></span>

<span data-ttu-id="c87a9-216">定義 WS-Management 工作階段的一組擴充選項。</span><span class="sxs-lookup"><span data-stu-id="c87a9-216">Defines a set of extended options for the WS-Management session.</span></span>
<span data-ttu-id="c87a9-217">輸入使用 New-WSManSessionOption Cmdlet 所建立的 SessionOption 物件。</span><span class="sxs-lookup"><span data-stu-id="c87a9-217">Enter a SessionOption object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="c87a9-218">如需可用選項的詳細資訊，請參閱 New-WSManSessionOption。</span><span class="sxs-lookup"><span data-stu-id="c87a9-218">For more information about the options that are available, see New-WSManSessionOption.</span></span>

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

### <span data-ttu-id="c87a9-219">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="c87a9-219">-UseSSL</span></span>

<span data-ttu-id="c87a9-220">指定使用安全通訊端層 (SSL) 通訊協定來建立遠端電腦連線。</span><span class="sxs-lookup"><span data-stu-id="c87a9-220">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="c87a9-221">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="c87a9-221">By default, SSL is not used.</span></span>

<span data-ttu-id="c87a9-222">WS-Management 會加密透過網路傳輸的所有 PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="c87a9-222">WS-Management encrypts all the PowerShell content  that is transmitted over the network.</span></span>
<span data-ttu-id="c87a9-223">UseSSL 參數可讓您指定 HTTPS 額外保護，以取代 HTTP。</span><span class="sxs-lookup"><span data-stu-id="c87a9-223">The UseSSL parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="c87a9-224">若用於連線的連接埠上無法使用 SSL，且您指定此參數，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="c87a9-224">If SSL is not available on the port that is used for the connection and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="c87a9-225">-ValueSet</span><span class="sxs-lookup"><span data-stu-id="c87a9-225">-ValueSet</span></span>

<span data-ttu-id="c87a9-226">指定有助於修改管理資源的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="c87a9-226">Specifies a hash table that helps modify a management resource.</span></span>
<span data-ttu-id="c87a9-227">您可以使用 ResourceURI 和 SelectorSet 參數來指定管理資源。</span><span class="sxs-lookup"><span data-stu-id="c87a9-227">You specify the management resource using the ResourceURI and SelectorSet parameters.</span></span>
<span data-ttu-id="c87a9-228">ValueSet 參數的值必須為雜湊表。</span><span class="sxs-lookup"><span data-stu-id="c87a9-228">The value of the ValueSet parameter must be a hash table.</span></span>

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

### <span data-ttu-id="c87a9-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c87a9-229">CommonParameters</span></span>

<span data-ttu-id="c87a9-230">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c87a9-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c87a9-231">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c87a9-231">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c87a9-232">輸入</span><span class="sxs-lookup"><span data-stu-id="c87a9-232">INPUTS</span></span>

### <span data-ttu-id="c87a9-233">無</span><span class="sxs-lookup"><span data-stu-id="c87a9-233">None</span></span>

<span data-ttu-id="c87a9-234">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="c87a9-234">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="c87a9-235">輸出</span><span class="sxs-lookup"><span data-stu-id="c87a9-235">OUTPUTS</span></span>

### <span data-ttu-id="c87a9-236">無</span><span class="sxs-lookup"><span data-stu-id="c87a9-236">None</span></span>

<span data-ttu-id="c87a9-237">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="c87a9-237">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c87a9-238">注意</span><span class="sxs-lookup"><span data-stu-id="c87a9-238">NOTES</span></span>

## <span data-ttu-id="c87a9-239">相關連結</span><span class="sxs-lookup"><span data-stu-id="c87a9-239">RELATED LINKS</span></span>

[<span data-ttu-id="c87a9-240">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="c87a9-240">Invoke-WmiMethod</span></span>](../Microsoft.PowerShell.Management/Invoke-WmiMethod.md)

[<span data-ttu-id="c87a9-241">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="c87a9-241">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="c87a9-242">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="c87a9-242">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="c87a9-243">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="c87a9-243">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="c87a9-244">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="c87a9-244">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="c87a9-245">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="c87a9-245">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="c87a9-246">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="c87a9-246">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="c87a9-247">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="c87a9-247">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="c87a9-248">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="c87a9-248">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="c87a9-249">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="c87a9-249">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="c87a9-250">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="c87a9-250">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="c87a9-251">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="c87a9-251">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="c87a9-252">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="c87a9-252">Test-WSMan</span></span>](Test-WSMan.md)
