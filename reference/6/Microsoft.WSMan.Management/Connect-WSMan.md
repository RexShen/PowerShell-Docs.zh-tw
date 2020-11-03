---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/connect-wsman?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-WSMan
ms.openlocfilehash: d06ede0e27713b1a309aa2ed265f02881d34124e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204831"
---
# <span data-ttu-id="88641-103">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="88641-103">Connect-WSMan</span></span>

## <span data-ttu-id="88641-104">概要</span><span class="sxs-lookup"><span data-stu-id="88641-104">SYNOPSIS</span></span>
<span data-ttu-id="88641-105">連線到遠端電腦上的 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="88641-105">Connects to the WinRM service on a remote computer.</span></span>

## <span data-ttu-id="88641-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="88641-106">SYNTAX</span></span>

### <span data-ttu-id="88641-107">ComputerName (預設值)</span><span class="sxs-lookup"><span data-stu-id="88641-107">ComputerName (Default)</span></span>

```
Connect-WSMan [-ApplicationName <String>] [[-ComputerName] <String>] [-OptionSet <Hashtable>] [-Port <Int32>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="88641-108">URI</span><span class="sxs-lookup"><span data-stu-id="88641-108">URI</span></span>

```
Connect-WSMan [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-Port <Int32>] [-SessionOption <SessionOption>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="88641-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="88641-109">DESCRIPTION</span></span>
<span data-ttu-id="88641-110">**Connect-WSMan** Cmdlet 會連線到遠端電腦上的 WinRM 服務，並且會建立與遠端電腦的持續連線。</span><span class="sxs-lookup"><span data-stu-id="88641-110">The **Connect-WSMan** cmdlet connects to the WinRM service on a remote computer, and it establishes a persistent connection to the remote computer.</span></span>
<span data-ttu-id="88641-111">您可以在 WSMan 提供者中使用此 Cmdlet 來連線到遠端電腦上的 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="88641-111">You can use this cmdlet in the context of the WSMan provider to connect to the WinRM service on a remote computer.</span></span>
<span data-ttu-id="88641-112">不過，您也可以使用此 Cmdlet 來連線到遠端電腦上的 WinRM 服務，再變更為 WSMan 提供者。</span><span class="sxs-lookup"><span data-stu-id="88641-112">However, you can also use this cmdlet to connect to the WinRM service on a remote computer before you change to the WSMan provider.</span></span>
<span data-ttu-id="88641-113">遠端電腦會出現在 WSMan 提供者的根目錄。</span><span class="sxs-lookup"><span data-stu-id="88641-113">The remote computer appears in the root directory of the WSMan provider.</span></span>

<span data-ttu-id="88641-114">當用戶端與伺服器電腦位於不同的網域或工作群組時，需要明確宣告的認證。</span><span class="sxs-lookup"><span data-stu-id="88641-114">Explicit credentials are required when the client and server computers are in different domains or workgroups.</span></span>

<span data-ttu-id="88641-115">如需如何中斷與遠端電腦上 WinRM 服務之連線的詳細資訊，請參閱 Disconnect-WSMan Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="88641-115">For information about how to disconnect from the WinRM service on a remote computer, see the Disconnect-WSMan cmdlet.</span></span>

## <span data-ttu-id="88641-116">範例</span><span class="sxs-lookup"><span data-stu-id="88641-116">EXAMPLES</span></span>

### <span data-ttu-id="88641-117">範例 1︰連線到遠端電腦</span><span class="sxs-lookup"><span data-stu-id="88641-117">Example 1: Connect to a remote computer</span></span>

```
PS C:\> Connect-WSMan -ComputerName "server01"
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="88641-118">此命令會建立與遠端 server01 電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="88641-118">This command creates a connection to the remote server01 computer.</span></span>

<span data-ttu-id="88641-119">**Connect-WSMan** Cmdlet 通常是在 WSMan 提供者中用來連線到遠端電腦 (在此案例中是 server01 電腦)。</span><span class="sxs-lookup"><span data-stu-id="88641-119">The **Connect-WSMan** cmdlet is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="88641-120">不過，您可以使用該 Cmdlet 來建立與遠端電腦的連線，再變更為 WSMan 提供者。</span><span class="sxs-lookup"><span data-stu-id="88641-120">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="88641-121">那些連線會出現在 **ComputerName** 清單中。</span><span class="sxs-lookup"><span data-stu-id="88641-121">Those connections appear in the **ComputerName** list.</span></span>

### <span data-ttu-id="88641-122">範例 2︰使用 Administrator 認證連線到遠端電腦</span><span class="sxs-lookup"><span data-stu-id="88641-122">Example 2: Connect to a remote computer by using Administrator credentials</span></span>

```
PS C:\> $cred = Get-Credential Administrator
PS C:\> Connect-WSMan -ComputerName "server01" -Credential $cred
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="88641-123">此命令會使用 Administrator 帳戶驗證來建立與遠端系統 server01 的連線。</span><span class="sxs-lookup"><span data-stu-id="88641-123">This command creates a connection to the remote system server01 using the Administrator account credentials.</span></span>

<span data-ttu-id="88641-124">第一個命令會使用 Get-Credential Cmdlet 來取得 Administrator 認證並將其儲存在 $cred 變數中。</span><span class="sxs-lookup"><span data-stu-id="88641-124">The first command uses the Get-Credential cmdlet to get the Administrator credentials and then stores them in the $cred variable.</span></span>
<span data-ttu-id="88641-125">**Get-Credential** 會透過對話方塊或命令列 (視系統登錄設定而定) 提示您輸入使用者名稱的密碼和密碼。</span><span class="sxs-lookup"><span data-stu-id="88641-125">**Get-Credential** prompts you for a password of username and password through a dialog box or at the command line, depending on system registry settings.</span></span>

<span data-ttu-id="88641-126">第二個命令會使用 *Credential* 參數，將 $cred 中儲存的認證傳遞至 **連接-WSMan** 。</span><span class="sxs-lookup"><span data-stu-id="88641-126">The second command uses the *Credential* parameter to pass the credentials stored in $cred to **Connect-WSMan** .</span></span>
<span data-ttu-id="88641-127">**Connect-WSMan** 接著會使用 Administrator 認證來連線到遠端系統 server01。</span><span class="sxs-lookup"><span data-stu-id="88641-127">**Connect-WSMan** then connects to the remote system server01 by using the Administrator credentials.</span></span>

### <span data-ttu-id="88641-128">範例 3︰透過指定的連接埠連線到遠端電腦</span><span class="sxs-lookup"><span data-stu-id="88641-128">Example 3: Connect to a remote computer over a specified port</span></span>

```
PS C:\> Connect-WSMan -ComputerName "server01" -Port 80
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="88641-129">此命令會透過連接埠 80 建立與遠端 server01 電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="88641-129">This command creates a connection to the remote server01 computer over port 80.</span></span>

### <span data-ttu-id="88641-130">範例 4︰使用連線選項連線到遠端電腦</span><span class="sxs-lookup"><span data-stu-id="88641-130">Example 4: Connect to a remote computer by using connection options</span></span>

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

<span data-ttu-id="88641-131">此範例會使用在 **New-WSManSessionOption** 命令中定義的連線選項來建立與遠端 server01 電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="88641-131">This example creates a connection to the remote server01 computer by using the connection options that are defined in the **New-WSManSessionOption** command.</span></span>

<span data-ttu-id="88641-132">第一個命令會使用 **New-WSManSessionOption** 將一組連線設定選項儲存到 $a 變數中。</span><span class="sxs-lookup"><span data-stu-id="88641-132">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="88641-133">在此案例中，工作階段選項會設定 30 秒 (30,000 毫秒) 的連線逾時。</span><span class="sxs-lookup"><span data-stu-id="88641-133">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="88641-134">第二個命令會使用 *SessionOption* 參數，將儲存在 $a 變數中的認證傳遞至 **連接-WSMan** 。</span><span class="sxs-lookup"><span data-stu-id="88641-134">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan** .</span></span>
<span data-ttu-id="88641-135">然後， **連接-WSMan** 使用指定的會話選項連線到遠端 server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="88641-135">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

## <span data-ttu-id="88641-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="88641-136">PARAMETERS</span></span>

### <span data-ttu-id="88641-137">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="88641-137">-ApplicationName</span></span>
<span data-ttu-id="88641-138">指定連線中的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="88641-138">Specifies the application name in the connection.</span></span>
<span data-ttu-id="88641-139">*ApplicationName* 參數的預設值是 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="88641-139">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="88641-140">遠端端點的完整識別碼使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="88641-140">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="88641-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="88641-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="88641-142">例如：`http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="88641-142">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="88641-143">裝載工作階段的網際網路資訊服務 (IIS)，會使用此端點轉送要求至指定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="88641-143">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="88641-144">此預設設定 WSMAN 適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="88641-144">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="88641-145">如果有許多電腦與執行 PowerShell 的一部電腦建立遠端連線，則會使用此參數。</span><span class="sxs-lookup"><span data-stu-id="88641-145">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="88641-146">在此案例中，IIS 會裝載管理 Web 服務 (WS-Management) 以獲得較佳效率。</span><span class="sxs-lookup"><span data-stu-id="88641-146">In this case, IIS hosts Web Services for Management (WS-Management) for efficiency.</span></span>

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

### <span data-ttu-id="88641-147">-Authentication</span><span class="sxs-lookup"><span data-stu-id="88641-147">-Authentication</span></span>
<span data-ttu-id="88641-148">指定用於伺服器的驗證機制。</span><span class="sxs-lookup"><span data-stu-id="88641-148">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="88641-149">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="88641-149">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="88641-150">基本。</span><span class="sxs-lookup"><span data-stu-id="88641-150">Basic.</span></span>
<span data-ttu-id="88641-151">Basic 配置使用純文字方式將使用者名稱與密碼傳送至伺服器或 Proxy。</span><span class="sxs-lookup"><span data-stu-id="88641-151">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="88641-152">預設值：</span><span class="sxs-lookup"><span data-stu-id="88641-152">Default.</span></span>
<span data-ttu-id="88641-153">使用 WS-Management 通訊協定實作的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="88641-153">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="88641-154">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="88641-154">This is the default.</span></span>
- <span data-ttu-id="88641-155">摘要。</span><span class="sxs-lookup"><span data-stu-id="88641-155">Digest.</span></span>
<span data-ttu-id="88641-156">Digest 為查問-回應配置，於查問中使用伺服器指定的資料字串。</span><span class="sxs-lookup"><span data-stu-id="88641-156">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="88641-157">Kerberos。</span><span class="sxs-lookup"><span data-stu-id="88641-157">Kerberos.</span></span>
<span data-ttu-id="88641-158">用戶端電腦和伺服器使用 Kerberos 憑證相互驗證。</span><span class="sxs-lookup"><span data-stu-id="88641-158">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="88641-159">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="88641-159">Negotiate.</span></span>
<span data-ttu-id="88641-160">Negotiate 為查問-回應配置，會與伺服器或 Proxy 交涉以決定要用於驗證的配置。</span><span class="sxs-lookup"><span data-stu-id="88641-160">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="88641-161">例如，此參數值允許交涉，以決定要使用 Kerberos 通訊協定或 NTLM。</span><span class="sxs-lookup"><span data-stu-id="88641-161">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="88641-162">CredSSP。</span><span class="sxs-lookup"><span data-stu-id="88641-162">CredSSP.</span></span>
<span data-ttu-id="88641-163">使用認證安全性支援提供者 (CredSSP) 驗證，讓使用者能夠委派認證。</span><span class="sxs-lookup"><span data-stu-id="88641-163">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="88641-164">此選項是針對下列命令所設計：命令在遠端電腦上執行，但是收集來自其他遠端電腦上的資料，或是在其他遠端電腦上執行其他命令。</span><span class="sxs-lookup"><span data-stu-id="88641-164">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="88641-165">注意：CredSSP 會將使用者認證從本機電腦委派給遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="88641-165">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="88641-166">此做法會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="88641-166">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="88641-167">若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="88641-167">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="88641-168">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="88641-168">-CertificateThumbprint</span></span>
<span data-ttu-id="88641-169">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="88641-169">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="88641-170">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="88641-170">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="88641-171">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="88641-171">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="88641-172">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="88641-172">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="88641-173">若要取得憑證指紋，請使用 PowerShell Cert：磁片磁碟機中的 Get-Item 或 Get-ChildItem 命令。</span><span class="sxs-lookup"><span data-stu-id="88641-173">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="88641-174">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="88641-174">-ComputerName</span></span>
<span data-ttu-id="88641-175">指定要執行管理作業的電腦。</span><span class="sxs-lookup"><span data-stu-id="88641-175">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="88641-176">值可以是完整網域名稱、NetBIOS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="88641-176">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="88641-177">使用本機電腦名稱、使用 localhost，或使用句點 (.) 來指定本機電腦。</span><span class="sxs-lookup"><span data-stu-id="88641-177">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="88641-178">預設值是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="88641-178">The local computer is the default.</span></span>
<span data-ttu-id="88641-179">當遠端電腦與使用者位於不同網域，您必須使用完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="88641-179">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="88641-180">您可以使用管線將此參數的值傳送至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="88641-180">You can pipe a value for this parameter to the cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="88641-181">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="88641-181">-ConnectionURI</span></span>
<span data-ttu-id="88641-182">指定連線端點。</span><span class="sxs-lookup"><span data-stu-id="88641-182">Specifies the connection endpoint.</span></span>
<span data-ttu-id="88641-183">這個字串的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="88641-183">The format of this string is as follows:</span></span>

<span data-ttu-id="88641-184">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="88641-184">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="88641-185">下列字串是此參數的正確格式值：</span><span class="sxs-lookup"><span data-stu-id="88641-185">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="88641-186">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="88641-186">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="88641-187">-Credential</span><span class="sxs-lookup"><span data-stu-id="88641-187">-Credential</span></span>
<span data-ttu-id="88641-188">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="88641-188">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="88641-189">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="88641-189">The default is the current user.</span></span>
<span data-ttu-id="88641-190">輸入使用者名稱，例如 User01、Domain01\User01 或 User@Domain.com 。</span><span class="sxs-lookup"><span data-stu-id="88641-190">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="88641-191">或者，輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="88641-191">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="88641-192">當您輸入使用者名稱時，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="88641-192">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="88641-193">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="88641-193">-OptionSet</span></span>
<span data-ttu-id="88641-194">對服務指定一組切換參數，以修改或精簡要求的本質。</span><span class="sxs-lookup"><span data-stu-id="88641-194">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="88641-195">這些切換參數類似於命令列殼層中使用的切換參數，因為都是服務特定的切換參數。</span><span class="sxs-lookup"><span data-stu-id="88641-195">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="88641-196">您可以指定任意數目的選項。</span><span class="sxs-lookup"><span data-stu-id="88641-196">Any number of options can be specified.</span></span>

<span data-ttu-id="88641-197">下列範例示範的語法可傳遞 a、b 與 c 參數的值 1、2 與 3：</span><span class="sxs-lookup"><span data-stu-id="88641-197">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="88641-198">-Port</span><span class="sxs-lookup"><span data-stu-id="88641-198">-Port</span></span>
<span data-ttu-id="88641-199">指定用戶端連線 WinRM 服務時所使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="88641-199">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="88641-200">傳輸為 HTTP 時，預設連接埠為 80。</span><span class="sxs-lookup"><span data-stu-id="88641-200">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="88641-201">傳輸為 HTTPS 時，預設連接埠為 443。</span><span class="sxs-lookup"><span data-stu-id="88641-201">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="88641-202">當您使用 HTTPS 做為傳輸時， *ComputerName* 參數的值必須符合伺服器的憑證一般名稱 (CN) 。</span><span class="sxs-lookup"><span data-stu-id="88641-202">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="88641-203">不過，如果 *SkipCNCheck* 參數指定為 *SessionOption* 參數的一部分，則伺服器憑證一般名稱不必符合伺服器主機名稱。</span><span class="sxs-lookup"><span data-stu-id="88641-203">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="88641-204">*SkipCNCheck* 參數只能用於信任的電腦。</span><span class="sxs-lookup"><span data-stu-id="88641-204">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="88641-205">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="88641-205">-SessionOption</span></span>
<span data-ttu-id="88641-206">指定 WS-Management 工作階段的擴充選項。</span><span class="sxs-lookup"><span data-stu-id="88641-206">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="88641-207">輸入您使用 New-WSManSessionOption Cmdlet 建立的 **SessionOption** 物件。</span><span class="sxs-lookup"><span data-stu-id="88641-207">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="88641-208">如需可用選項的詳細資訊，請輸入 `Get-Help New-WSManSessionOption`。</span><span class="sxs-lookup"><span data-stu-id="88641-208">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="88641-209">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="88641-209">-UseSSL</span></span>
<span data-ttu-id="88641-210">指定使用安全通訊端層 (SSL) 通訊協定來建立遠端電腦連線。</span><span class="sxs-lookup"><span data-stu-id="88641-210">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="88641-211">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="88641-211">By default, SSL is not used.</span></span>

<span data-ttu-id="88641-212">WS-Management 會加密透過網路傳輸的所有 PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="88641-212">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="88641-213">*UseSSL* 參數可讓您指定 HTTPS （而非 HTTP）的額外保護。</span><span class="sxs-lookup"><span data-stu-id="88641-213">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="88641-214">若用於連線的連接埠上無法使用 SSL，且您指定此參數，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="88641-214">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="88641-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="88641-215">CommonParameters</span></span>
<span data-ttu-id="88641-216">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="88641-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="88641-217">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="88641-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="88641-218">輸入</span><span class="sxs-lookup"><span data-stu-id="88641-218">INPUTS</span></span>

### <span data-ttu-id="88641-219">無</span><span class="sxs-lookup"><span data-stu-id="88641-219">None</span></span>
<span data-ttu-id="88641-220">此 Cmdlet 不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="88641-220">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="88641-221">輸出</span><span class="sxs-lookup"><span data-stu-id="88641-221">OUTPUTS</span></span>

### <span data-ttu-id="88641-222">無</span><span class="sxs-lookup"><span data-stu-id="88641-222">None</span></span>
<span data-ttu-id="88641-223">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="88641-223">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="88641-224">注意</span><span class="sxs-lookup"><span data-stu-id="88641-224">NOTES</span></span>

* <span data-ttu-id="88641-225">您不需要建立 WS-Management 工作階段，就可以在遠端電腦上執行管理命令或查詢遠端電腦上的管理資料。</span><span class="sxs-lookup"><span data-stu-id="88641-225">You can run management commands or query management data on a remote computer without creating a WS-Management session.</span></span> <span data-ttu-id="88641-226">您可以使用 Invoke-WSManAction 的 *ComputerName* 參數和 set-wsmaninstance 來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="88641-226">You can do this by using the *ComputerName* parameters of Invoke-WSManAction and Get-WSManInstance.</span></span> <span data-ttu-id="88641-227">當您使用 *ComputerName* 參數時，PowerShell 會建立用於單一命令的暫時連接。</span><span class="sxs-lookup"><span data-stu-id="88641-227">When you use the *ComputerName* parameter, PowerShell creates a temporary connection that is used for the single command.</span></span> <span data-ttu-id="88641-228">該命令執行之後，此連線即會關閉。</span><span class="sxs-lookup"><span data-stu-id="88641-228">After the command runs, the connection is closed.</span></span>

*

## <span data-ttu-id="88641-229">相關連結</span><span class="sxs-lookup"><span data-stu-id="88641-229">RELATED LINKS</span></span>

[<span data-ttu-id="88641-230">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="88641-230">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="88641-231">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="88641-231">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="88641-232">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="88641-232">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="88641-233">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="88641-233">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="88641-234">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="88641-234">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="88641-235">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="88641-235">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="88641-236">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="88641-236">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="88641-237">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="88641-237">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="88641-238">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="88641-238">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="88641-239">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="88641-239">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="88641-240">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="88641-240">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="88641-241">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="88641-241">Test-WSMan</span></span>](Test-WSMan.md)
