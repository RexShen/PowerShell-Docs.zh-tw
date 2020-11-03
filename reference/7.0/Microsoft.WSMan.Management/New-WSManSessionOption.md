---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: 2fa100a0388b91a060e1778d703f73e2c85957a8
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201555"
---
# <span data-ttu-id="b7533-103">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="b7533-103">New-WSManSessionOption</span></span>

## <span data-ttu-id="b7533-104">概要</span><span class="sxs-lookup"><span data-stu-id="b7533-104">SYNOPSIS</span></span>
<span data-ttu-id="b7533-105">建立會話選項雜湊表，作為 WS-Management Cmdlet 的輸入參數使用。</span><span class="sxs-lookup"><span data-stu-id="b7533-105">Creates session option hash table to use as input parameters for WS-Management cmdlets.</span></span>

## <span data-ttu-id="b7533-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b7533-106">SYNTAX</span></span>

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## <span data-ttu-id="b7533-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b7533-107">DESCRIPTION</span></span>
<span data-ttu-id="b7533-108">**New-wsmansessionoption** 指令 Cmdlet 會建立可傳遞到 wsman Cmdlet 的 wsman 會話選項雜湊表：</span><span class="sxs-lookup"><span data-stu-id="b7533-108">The **New-WSManSessionOption** cmdlet creates a WSMan Session option hash table which can be passed to WSMan cmdlets:</span></span>

- <span data-ttu-id="b7533-109">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b7533-109">Get-WSManInstance</span></span>
- <span data-ttu-id="b7533-110">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b7533-110">Set-WSManInstance</span></span>
- <span data-ttu-id="b7533-111">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="b7533-111">Invoke-WSManAction</span></span>
- <span data-ttu-id="b7533-112">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b7533-112">Connect-WSMan</span></span>

## <span data-ttu-id="b7533-113">範例</span><span class="sxs-lookup"><span data-stu-id="b7533-113">EXAMPLES</span></span>

### <span data-ttu-id="b7533-114">範例1：建立使用連接選項的連接</span><span class="sxs-lookup"><span data-stu-id="b7533-114">Example 1: Create a connection that uses connection options</span></span>

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

<span data-ttu-id="b7533-115">此範例會使用 **new-wsmansessionoption** 定義的連接選項，建立與遠端 server01 電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="b7533-115">This example creates a connection to the remote server01 computer by using the connection options that are defined by **New-WSManSessionOption** .</span></span>

<span data-ttu-id="b7533-116">第一個命令會使用 **New-WSManSessionOption** 將一組連線設定選項儲存到 $a 變數中。</span><span class="sxs-lookup"><span data-stu-id="b7533-116">The first command uses **New-WSManSessionOption** to store a set of connection setting options in the $a variable.</span></span>
<span data-ttu-id="b7533-117">在此案例中，工作階段選項會設定 30 秒 (30,000 毫秒) 的連線逾時。</span><span class="sxs-lookup"><span data-stu-id="b7533-117">In this case, the session options set a connection time out of 30 seconds (30,000 milliseconds).</span></span>

<span data-ttu-id="b7533-118">第二個命令會使用 *SessionOption* 參數，將儲存在 $a 變數中的認證傳遞至 **連接-WSMan** 。</span><span class="sxs-lookup"><span data-stu-id="b7533-118">The second command uses the *SessionOption* parameter to pass the credentials that are stored in the $a variable to **Connect-WSMan** .</span></span>
<span data-ttu-id="b7533-119">然後， **連接-WSMan** 使用指定的會話選項連線到遠端 server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="b7533-119">Then, **Connect-WSMan** connects to the remote server01 computer by using the specified session options.</span></span>

<span data-ttu-id="b7533-120">**連接-wsman** 通常用於 wsman 提供者的內容中，以連接到遠端電腦，在此案例中為 server01 電腦。</span><span class="sxs-lookup"><span data-stu-id="b7533-120">**Connect-WSMan** is generally used in the context of the WSMan provider to connect to a remote computer, in this case the server01 computer.</span></span>
<span data-ttu-id="b7533-121">不過，您可以使用該 Cmdlet 來建立與遠端電腦的連線，再變更為 WSMan 提供者。</span><span class="sxs-lookup"><span data-stu-id="b7533-121">However, you can use the cmdlet to establish connections to remote computers before you change to the WSMan provider.</span></span>
<span data-ttu-id="b7533-122">那些連線會出現在 **ComputerName** 清單中。</span><span class="sxs-lookup"><span data-stu-id="b7533-122">Those connections appear in the **ComputerName** list.</span></span>

## <span data-ttu-id="b7533-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b7533-123">PARAMETERS</span></span>

### <span data-ttu-id="b7533-124">-NoEncryption</span><span class="sxs-lookup"><span data-stu-id="b7533-124">-NoEncryption</span></span>
<span data-ttu-id="b7533-125">表示連接不會針對透過 HTTP 的遠端作業使用加密。</span><span class="sxs-lookup"><span data-stu-id="b7533-125">Indicates that the connection does not use encryption for remote operations over HTTP.</span></span>

<span data-ttu-id="b7533-126">依預設，不會啟用未加密的流量。</span><span class="sxs-lookup"><span data-stu-id="b7533-126">By default, unencrypted traffic is not enabled.</span></span>
<span data-ttu-id="b7533-127">它必須在本機設定中啟用。</span><span class="sxs-lookup"><span data-stu-id="b7533-127">It must be enabled in the local configuration.</span></span>

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

### <span data-ttu-id="b7533-128">-OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="b7533-128">-OperationTimeout</span></span>
<span data-ttu-id="b7533-129">指定 WS-Management 操作的超時時間（以毫秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="b7533-129">Specifies the time-out, in milliseconds, for the WS-Management operation.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7533-130">-ProxyAccessType</span><span class="sxs-lookup"><span data-stu-id="b7533-130">-ProxyAccessType</span></span>
<span data-ttu-id="b7533-131">指定尋找 Proxy 伺服器的機制。</span><span class="sxs-lookup"><span data-stu-id="b7533-131">Specifies the mechanism by which the proxy server is located.</span></span>
<span data-ttu-id="b7533-132">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="b7533-132">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b7533-133">ProxyIEConfig.</span><span class="sxs-lookup"><span data-stu-id="b7533-133">ProxyIEConfig.</span></span>
<span data-ttu-id="b7533-134">針對目前使用者使用 Internet Explorer proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="b7533-134">Use the Internet Explorer proxy configuration for the current user.</span></span>
- <span data-ttu-id="b7533-135">ProxyWinHttpConfig.</span><span class="sxs-lookup"><span data-stu-id="b7533-135">ProxyWinHttpConfig.</span></span>
<span data-ttu-id="b7533-136">WSMan 用戶端使用 ProxyCfg.exe 公用程式，使用針對 WinHTTP 設定的 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="b7533-136">The WSMan client uses the proxy settings configured for WinHTTP, using the ProxyCfg.exe utility.</span></span>
- <span data-ttu-id="b7533-137">ProxyAutoDetect.</span><span class="sxs-lookup"><span data-stu-id="b7533-137">ProxyAutoDetect.</span></span>
<span data-ttu-id="b7533-138">強制自動偵測 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="b7533-138">Force auto-detection of a proxy server.</span></span>
- <span data-ttu-id="b7533-139">ProxyNoProxyServer.</span><span class="sxs-lookup"><span data-stu-id="b7533-139">ProxyNoProxyServer.</span></span>
<span data-ttu-id="b7533-140">不使用 Proxy 伺服器：</span><span class="sxs-lookup"><span data-stu-id="b7533-140">Do not use a proxy server.</span></span>
<span data-ttu-id="b7533-141">在本機解析所有主機名稱。</span><span class="sxs-lookup"><span data-stu-id="b7533-141">Resolve all host names locally.</span></span>

<span data-ttu-id="b7533-142">預設值為 ProxyIEConfig。</span><span class="sxs-lookup"><span data-stu-id="b7533-142">The default value is ProxyIEConfig.</span></span>

```yaml
Type: Microsoft.WSMan.Management.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: ProxyIEConfig, ProxyWinHttpConfig, ProxyAutoDetect, ProxyNoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7533-143">-ProxyAuthentication</span><span class="sxs-lookup"><span data-stu-id="b7533-143">-ProxyAuthentication</span></span>
<span data-ttu-id="b7533-144">指定要在 Proxy 使用的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="b7533-144">Specifies the authentication method to use at the proxy.</span></span>
<span data-ttu-id="b7533-145">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="b7533-145">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b7533-146">基本。</span><span class="sxs-lookup"><span data-stu-id="b7533-146">Basic.</span></span>
<span data-ttu-id="b7533-147">Basic 配置使用純文字方式將使用者名稱與密碼傳送至伺服器或 Proxy。</span><span class="sxs-lookup"><span data-stu-id="b7533-147">Basic is a scheme in which the user name and password are sent in clear-text to the server or proxy.</span></span>
- <span data-ttu-id="b7533-148">摘要。</span><span class="sxs-lookup"><span data-stu-id="b7533-148">Digest.</span></span>
<span data-ttu-id="b7533-149">Digest 為查問-回應配置，於查問中使用伺服器指定的資料字串。</span><span class="sxs-lookup"><span data-stu-id="b7533-149">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="b7533-150">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="b7533-150">Negotiate.</span></span>
<span data-ttu-id="b7533-151">Negotiate 為查問-回應配置，會與伺服器或 Proxy 交涉以決定要用於驗證的配置。</span><span class="sxs-lookup"><span data-stu-id="b7533-151">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine which scheme to use for authentication.</span></span>
<span data-ttu-id="b7533-152">範例包括 Kerberos 通訊協定與 NTLM。</span><span class="sxs-lookup"><span data-stu-id="b7533-152">Examples are the Kerberos protocol and NTLM.</span></span>

<span data-ttu-id="b7533-153">預設值為 Negotiate。</span><span class="sxs-lookup"><span data-stu-id="b7533-153">The default value is Negotiate.</span></span>

```yaml
Type: Microsoft.WSMan.Management.ProxyAuthentication
Parameter Sets: (All)
Aliases:
Accepted values: Negotiate, Basic, Digest

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7533-154">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="b7533-154">-ProxyCredential</span></span>
<span data-ttu-id="b7533-155">指定有權透過中繼 Web proxy 取得存取權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="b7533-155">Specifies a user account that has permission to gain access through an intermediate Web proxy.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7533-156">-SkipCACheck</span><span class="sxs-lookup"><span data-stu-id="b7533-156">-SkipCACheck</span></span>
<span data-ttu-id="b7533-157">指定當它透過 HTTPS 連線時，用戶端並不會驗證伺服器憑證是否由信任的憑證授權單位單位 (CA) 簽署。</span><span class="sxs-lookup"><span data-stu-id="b7533-157">Specifies that, when it connects over HTTPS, the client does not validate that the server certificate is signed by a trusted certification authority (CA).</span></span>
<span data-ttu-id="b7533-158">只有當遠端電腦受其他方法信任時才使用此選項，例如，如果遠端電腦屬於實體安全且隔離的網路，或在 WS-Management 設定中將遠端電腦列為受信任的主機。</span><span class="sxs-lookup"><span data-stu-id="b7533-158">Use this option only when the remote computer is trusted by another method, for example, if the remote computer is part of a network that is physically secure and isolated or the remote computer is listed as a trusted host in the WS-Management configuration.</span></span>

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

### <span data-ttu-id="b7533-159">-SkipCNCheck</span><span class="sxs-lookup"><span data-stu-id="b7533-159">-SkipCNCheck</span></span>
<span data-ttu-id="b7533-160">指定伺服器的憑證一般名稱 (CN) 不需要與伺服器的主機名稱相符。</span><span class="sxs-lookup"><span data-stu-id="b7533-160">Specifies that the certificate common name (CN) of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="b7533-161">此選項只用於使用 HTTPS 的遠端操作。</span><span class="sxs-lookup"><span data-stu-id="b7533-161">This is used only in remote operations using HTTPS.</span></span>
<span data-ttu-id="b7533-162">此選項只應該用於信任的電腦。</span><span class="sxs-lookup"><span data-stu-id="b7533-162">This option should only be used for trusted computers.</span></span>

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

### <span data-ttu-id="b7533-163">-SkipRevocationCheck</span><span class="sxs-lookup"><span data-stu-id="b7533-163">-SkipRevocationCheck</span></span>
<span data-ttu-id="b7533-164">表示連接不會驗證伺服器憑證的撤銷狀態。</span><span class="sxs-lookup"><span data-stu-id="b7533-164">Indicates that the connection does not validate the revocation status on the server certificate.</span></span>

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

### <span data-ttu-id="b7533-165">-SPNPort</span><span class="sxs-lookup"><span data-stu-id="b7533-165">-SPNPort</span></span>
<span data-ttu-id="b7533-166">指定要附加至遠端伺服器 (SPN) 之連接服務主體名稱的埠號碼。</span><span class="sxs-lookup"><span data-stu-id="b7533-166">Specifies a port number to append to the connection Service Principal Name (SPN) of the remote server.</span></span>
<span data-ttu-id="b7533-167">當驗證機制是 Kerberos 或 Negotiate 時，會使用 SPN。</span><span class="sxs-lookup"><span data-stu-id="b7533-167">An SPN is used when the authentication mechanism is Kerberos or Negotiate.</span></span>

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

### <span data-ttu-id="b7533-168">-UseUTF16</span><span class="sxs-lookup"><span data-stu-id="b7533-168">-UseUTF16</span></span>
<span data-ttu-id="b7533-169">表示連接會以 UTF16 格式（而不是 UTF8 格式）編碼要求。</span><span class="sxs-lookup"><span data-stu-id="b7533-169">Indicates that the connection encodes the request in UTF16 format instead of UTF8 format.</span></span>
<span data-ttu-id="b7533-170">預設值為 UTF8 編碼。</span><span class="sxs-lookup"><span data-stu-id="b7533-170">The default is UTF8 encoding.</span></span>

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

### <span data-ttu-id="b7533-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7533-171">CommonParameters</span></span>
<span data-ttu-id="b7533-172">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b7533-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7533-173">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b7533-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b7533-174">輸入</span><span class="sxs-lookup"><span data-stu-id="b7533-174">INPUTS</span></span>

## <span data-ttu-id="b7533-175">輸出</span><span class="sxs-lookup"><span data-stu-id="b7533-175">OUTPUTS</span></span>

### <span data-ttu-id="b7533-176">SessionOption</span><span class="sxs-lookup"><span data-stu-id="b7533-176">SessionOption</span></span>

## <span data-ttu-id="b7533-177">注意</span><span class="sxs-lookup"><span data-stu-id="b7533-177">NOTES</span></span>

## <span data-ttu-id="b7533-178">相關連結</span><span class="sxs-lookup"><span data-stu-id="b7533-178">RELATED LINKS</span></span>

[<span data-ttu-id="b7533-179">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b7533-179">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="b7533-180">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b7533-180">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="b7533-181">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="b7533-181">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="b7533-182">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b7533-182">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="b7533-183">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="b7533-183">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="b7533-184">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b7533-184">Get-WSManInstance</span></span>](Get-WSManInstance.md)

[<span data-ttu-id="b7533-185">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="b7533-185">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="b7533-186">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b7533-186">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="b7533-187">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b7533-187">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="b7533-188">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b7533-188">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="b7533-189">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="b7533-189">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="b7533-190">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="b7533-190">Test-WSMan</span></span>](Test-WSMan.md)
