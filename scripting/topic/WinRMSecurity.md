---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: WinRMSecurity
redirect_url: https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity
ms.openlocfilehash: 70d17b2af3207af589fd9e323b8fc9ba3908b220
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="powershell-remoting-security-considerations"></a><span data-ttu-id="d3500-103">PowerShell 遠端安全性考量</span><span class="sxs-lookup"><span data-stu-id="d3500-103">PowerShell Remoting Security Considerations</span></span>

<span data-ttu-id="d3500-104">建議採用 PowerShell 遠端來管理 Windows 系統。</span><span class="sxs-lookup"><span data-stu-id="d3500-104">PowerShell Remoting is the recommended way to manage Windows systems.</span></span> <span data-ttu-id="d3500-105">Windows Server 2012 R2 中預設已啟用 PowerShell 遠端。</span><span class="sxs-lookup"><span data-stu-id="d3500-105">PowerShell Remoting is enabled by default in Windows Server 2012 R2.</span></span> <span data-ttu-id="d3500-106">本文件涵蓋使用 PowerShell 遠端時的安全性考量、建議與最佳做法。</span><span class="sxs-lookup"><span data-stu-id="d3500-106">This document covers security concerns, recommendations, and best practices when using PowerShell Remoting.</span></span>

## <a name="what-is-powershell-remoting"></a><span data-ttu-id="d3500-107">什麼是 PowerShell 遠端？</span><span class="sxs-lookup"><span data-stu-id="d3500-107">What is PowerShell Remoting?</span></span>

<span data-ttu-id="d3500-108">PowerShell 遠端使用 [Windows 遠端管理 (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426.aspx)，這是[管理的 Web 服務 (WS 管理)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) 通訊協定的 Microsoft 實作，可讓使用者在遠端電腦上執行 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="d3500-108">PowerShell Remoting uses [Windows Remote Management (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426.aspx), which is the Microsoft implementation of the [Web Services for Managment (WS-Managment)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) protocol, to allow users to run PowerShell commands on remote computers.</span></span> <span data-ttu-id="d3500-109">您可以在[執行遠端命令](https://technet.microsoft.com/en-us/library/dd819505.aspx)處找到有關使用 PowerShell 遠端的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d3500-109">You can find more information about using PowerShell Remoting at [Running Remote Commands](https://technet.microsoft.com/en-us/library/dd819505.aspx).</span></span>

<span data-ttu-id="d3500-110">PowerShell 遠端和使用 Cmdlet 的 **ComputerName** 參數在遠端電腦上執行不同，其使用遠端程序呼叫 (RPC) 作為其基礎通訊協定。</span><span class="sxs-lookup"><span data-stu-id="d3500-110">PowerShell Remoting is not the same as using the **ComputerName** parameter of a cmdlet to run it on a remote computer, which uses Remote Procedure Call (RPC) as its underlying protocol.</span></span>

##  <a name="powershell-remoting-default-settings"></a><span data-ttu-id="d3500-111">PowerShell 遠端的預設設定</span><span class="sxs-lookup"><span data-stu-id="d3500-111">PowerShell Remoting default settings</span></span>

<span data-ttu-id="d3500-112">PowerShell 遠端 (和 WinRM) 會接聽以下連接埠︰</span><span class="sxs-lookup"><span data-stu-id="d3500-112">PowerShell Remoting (and WinRM) listen on the following ports:</span></span>

- <span data-ttu-id="d3500-113">HTTP：5985</span><span class="sxs-lookup"><span data-stu-id="d3500-113">HTTP: 5985</span></span>
- <span data-ttu-id="d3500-114">HTTPS： 5986</span><span class="sxs-lookup"><span data-stu-id="d3500-114">HTTPS: 5986</span></span>

<span data-ttu-id="d3500-115">PowerShell 遠端預設僅允許連線系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="d3500-115">By default, PowerShell Remoting only allows connections from members of the Administrators group.</span></span> <span data-ttu-id="d3500-116">工作階段會在使用者的內容下啟動，因此透過 PowerShell 遠端連線時，所有套用至個別使用者和群組的作業系統存取控制，都會繼續套用。</span><span class="sxs-lookup"><span data-stu-id="d3500-116">Sessions are launched under the user's context, so all operating system access controls applied to individual users and groups continue to apply to them while connected over PowerShell Remoting.</span></span>

<span data-ttu-id="d3500-117">在私人網路中，PowerShell 遠端的預設 Windows 防火牆規則，可以接受所有的連線。</span><span class="sxs-lookup"><span data-stu-id="d3500-117">On private networks, the default Windows Firewall rule for PowerShell Remoting accepts all connections.</span></span> <span data-ttu-id="d3500-118">在公用網路中，預設的 Windows 防火牆規則只允許來自相同子網路的 PowerShell 遠端連線。</span><span class="sxs-lookup"><span data-stu-id="d3500-118">On public networks, the default Windows Firewall rule allows PowerShell Remoting connections only from within the same subnet.</span></span> <span data-ttu-id="d3500-119">您必須明確地變更該規則，才可開啟 PowerShell 遠端對公用網路上的所有連線。</span><span class="sxs-lookup"><span data-stu-id="d3500-119">You have to explicitly change that rule to open PowerShell Remoting to all connections on a public network.</span></span>

><span data-ttu-id="d3500-120">**警告︰**公用網路的防火牆規則主要是為了保護電腦免受嘗試進行惡意的外部連線的動作。</span><span class="sxs-lookup"><span data-stu-id="d3500-120">**Warning:** The firewall rule for public networks is meant to protect the computer from potentially malicious external connection attempts.</span></span> <span data-ttu-id="d3500-121">移除此規則時，請務必小心。</span><span class="sxs-lookup"><span data-stu-id="d3500-121">Use caution when removing this rule.</span></span>

## <a name="process-isolation"></a><span data-ttu-id="d3500-122">處理程序隔離</span><span class="sxs-lookup"><span data-stu-id="d3500-122">Process isolation</span></span>

<span data-ttu-id="d3500-123">PowerShell 遠端使用 [Windows 遠端管理 (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426) 進行電腦之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="d3500-123">PowerShell Remoting uses [Windows Remote Management (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426) for communication between computers.</span></span> <span data-ttu-id="d3500-124">WinRM 以網路服務帳戶的服務方式執行，並會繁衍隔離的處理程序作為使用者帳戶，以主控 PowerShell 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d3500-124">WinRM runs as a service under the Network Service account, and spawns isolated processes running as user accounts to host PowerShell instances.</span></span> <span data-ttu-id="d3500-125">PowerShell 的執行個體以一位使用者的身分執行時，無法存取執行為另一位使用者的 PowerShell 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d3500-125">An instance of PowerShell running as one user has no access to a process running an instance of PowerShell as another user.</span></span>

## <a name="event-logs-generated-by-powershell-remoting"></a><span data-ttu-id="d3500-126">PowerShell 遠端所產生的事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="d3500-126">Event logs generated by PowerShell Remoting</span></span>

<span data-ttu-id="d3500-127">FireEye 提供了一份良好的摘要，其中內含 PowerShell 遠端工作階段所產生之事件記錄檔與其他安全性辨識項，而且可以從</span><span class="sxs-lookup"><span data-stu-id="d3500-127">FireEye has provided a good summary of the event logs and other security evidence generated by PowerShell Remoting sessions, available at</span></span>  
<span data-ttu-id="d3500-128">[調查 PowerShell 攻擊](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf)取得。</span><span class="sxs-lookup"><span data-stu-id="d3500-128">[Investigating PowerShell Attacks](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).</span></span>

## <a name="encryption-and-transport-protocols"></a><span data-ttu-id="d3500-129">加密及傳輸通訊協定</span><span class="sxs-lookup"><span data-stu-id="d3500-129">Encryption and transport protocols</span></span>

<span data-ttu-id="d3500-130">最好先從兩個層面考量 PowerShell 遠端連線的安全性：初始驗證，以及進行中的通訊。</span><span class="sxs-lookup"><span data-stu-id="d3500-130">It is helpful to consider the security of a PowerShell Remoting connection from two perspectives: initial authentication, and ongoing communication.</span></span> 

<span data-ttu-id="d3500-131">不論所使用的傳輸通訊協定 (HTTP 或 HTTPS) 為何，PowerShell 遠端一律會在初始驗證之後，以每個工作階段 AES-256 對稱金鑰為單位，來加密所有通訊。</span><span class="sxs-lookup"><span data-stu-id="d3500-131">Regardless of the transport protocol used (HTTP or HTTPS), PowerShell Remoting always encrypts all communication after initial authentication with a per-session AES-256 symmetric key.</span></span>
    
### <a name="initial-authentication"></a><span data-ttu-id="d3500-132">初始驗證</span><span class="sxs-lookup"><span data-stu-id="d3500-132">Initial authentication</span></span>

<span data-ttu-id="d3500-133">驗證會確認用戶端至伺服器的身分識別，在理想的情況下，也會確認伺服器到用戶端的身分識別。</span><span class="sxs-lookup"><span data-stu-id="d3500-133">Authentication confirms the identity of the client to the server - and ideally - the server to the client.</span></span>
    
<span data-ttu-id="d3500-134">當用戶端使用其電腦名稱 (例如︰server01 或 server01.contoso.com) 連線到網域伺服器時，預設的驗證通訊協定是 [Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d3500-134">When a client connects to a domain server using its computer name (i.e.: server01, or server01.contoso.com), the default authentication protocol is [Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747.aspx).</span></span>
<span data-ttu-id="d3500-135">Kerberos 可保證使用者識別與伺服器識別，而不會傳送任何種類可重複使用的認證。</span><span class="sxs-lookup"><span data-stu-id="d3500-135">Kerberos guarantees both the user identity and server identity without sending any sort of reusable credential.</span></span>

<span data-ttu-id="d3500-136">當用戶端使用其 IP 位址連線到網域伺服器時，或連線到工作群組伺服器時，便無法進行 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="d3500-136">When a client connects to a domain server using its IP address, or connects to a workgroup server, Kerberos authentication is not possible.</span></span> <span data-ttu-id="d3500-137">在此情況下，PowerShell 遠端會仰賴 [NTLM 驗證通訊協定](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378749.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d3500-137">In that case, PowerShell Remoting relies on the [NTLM authentication protocol](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378749.aspx).</span></span> <span data-ttu-id="d3500-138">NTLM 驗證通訊協定可保證使用者識別，且不會傳送任何種類可委派的認證。</span><span class="sxs-lookup"><span data-stu-id="d3500-138">The NTLM authentication protocol guarantees the user identity without sending any sort of delegable credential.</span></span> <span data-ttu-id="d3500-139">為了要證明使用者識別，NTLM 通訊協定需要用戶端與伺服器從使用者的密碼來計算工作階段金鑰，而不會交換密碼本身。</span><span class="sxs-lookup"><span data-stu-id="d3500-139">To prove user identity, the NTLM protocol requires that both the client and server compute a session key from the user's password without ever exchanging the password itself.</span></span> <span data-ttu-id="d3500-140">伺服器通常不知道使用者的密碼，因此會和知道使用者密碼的網域控制站互相通訊，並為伺服器計算出工作階段金鑰。</span><span class="sxs-lookup"><span data-stu-id="d3500-140">The server typically does not know the user's password, so it communicates with the domain controller, which does know the user's password and calculates the session key for the server.</span></span> 
      
<span data-ttu-id="d3500-141">但 NTLM 通訊協定並不能保證伺服器識別。</span><span class="sxs-lookup"><span data-stu-id="d3500-141">The NTLM protocol does not, however, guarantee server identity.</span></span> <span data-ttu-id="d3500-142">因為所有通訊協定都使用 NTLM 進行驗證，所以可以存取已加入網域之電腦的電腦帳戶之攻擊者，就能叫用網域控制站計算出 NTLM 工作階段金鑰，然後模擬該伺服器。</span><span class="sxs-lookup"><span data-stu-id="d3500-142">As with all protocols that use NTLM for authentication, an attacker with access to a domain-joined computer's machine account could invoke the domain controller to compute an NTLM session-key and thereby impersonate the server.</span></span>

<span data-ttu-id="d3500-143">預設會停用 NTLM 的驗證，但在目標伺服器上設定 SSL 或進行 WinRM TrustedHosts 的設定時，可能會允許。</span><span class="sxs-lookup"><span data-stu-id="d3500-143">NTLM-based authentication is disabled by default, but may be permitted by either configuring SSL on the target server, or by configuring the WinRM TrustedHosts setting.</span></span>
    
#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a><span data-ttu-id="d3500-144">NTLM 連線期間使用 SSL 憑證來驗證伺服器識別</span><span class="sxs-lookup"><span data-stu-id="d3500-144">Using SSL certificates to validate server identity during NTLM-based connections</span></span>

<span data-ttu-id="d3500-145">由於 NTLM 驗證通訊協定無法確保目標伺服器 (只有它已經知道您的密碼) 的身分識別，所以您可以將目標伺服器設定為使用 SSL 進行 PowerShell 遠端。</span><span class="sxs-lookup"><span data-stu-id="d3500-145">Since the NTLM authentication protocol cannot ensure the identity of the target server (only that it already knows your password), you can configure target servers to use SSL for PowerShell Remoting.</span></span> <span data-ttu-id="d3500-146">將 SSL 憑證指派至目標伺服器 (如果由用戶端也信任的憑證授權中心發出)，可讓 NTLM 驗證能保證使用者識別與伺服器識別。</span><span class="sxs-lookup"><span data-stu-id="d3500-146">Assigning a SSL certificate to the target server (if issued by a Certificate Authority that the client also trusts) enables NTLM-based authentication that guarantees both the user identity and server identity.</span></span>
    
#### <a name="ignoring-ntlm-based-server-identity-errors"></a><span data-ttu-id="d3500-147">忽略 NTLM 伺服器識別錯誤</span><span class="sxs-lookup"><span data-stu-id="d3500-147">Ignoring NTLM-based server identity errors</span></span>
      
<span data-ttu-id="d3500-148">如果將 SSL 憑證部署至伺服器進行 NTLM 連線並不可行，可以隱藏所產生的身分識別錯誤，方法是將該伺服器新增至 WinRM **TrustedHosts** 清單。</span><span class="sxs-lookup"><span data-stu-id="d3500-148">If deploying a SSL certificate to a server for NTLM connections is infeasible, you may suppress the resulting identity errors by adding the server to the WinRM **TrustedHosts** list.</span></span> <span data-ttu-id="d3500-149">請注意，將伺服器名稱新增到 TrustedHosts 清單的動作，不應視為任何形式對主機本身信賴的保證，因為 NTLM 驗證通訊協定無法保證實際上連線到的主機是想要連線的主機。</span><span class="sxs-lookup"><span data-stu-id="d3500-149">Please note that adding a server name to the TrustedHosts list should not be considered as any form of statement of the trustworthiness of the hosts themselves - as the NTLM authentication protocol cannot guarantee that you are in fact connecting to the host you are intending to connect to.</span></span>
<span data-ttu-id="d3500-150">相反地，應考慮讓 TrustedHosts 設定成為想要隱藏錯誤 (因無法驗證伺服器身分識別而產生之錯誤) 的主機清單。</span><span class="sxs-lookup"><span data-stu-id="d3500-150">Instead, you should consider the TrustedHosts setting to be the list of hosts for which you wish to suppress the error generated by being unable to verify the server's identity.</span></span>
    
    
### <a name="ongoing-communication"></a><span data-ttu-id="d3500-151">進行中的通訊</span><span class="sxs-lookup"><span data-stu-id="d3500-151">Ongoing Communication</span></span>

<span data-ttu-id="d3500-152">完成初始驗證之後，[PowerShell 遠端通訊協定](https://msdn.microsoft.com/en-us/library/dd357801.aspx) 會使用每個工作階段的 AES-256 對稱金鑰，加密所有進行中的通訊。</span><span class="sxs-lookup"><span data-stu-id="d3500-152">Once initial authentication is complete, the [PowerShell Remoting Protocol](https://msdn.microsoft.com/en-us/library/dd357801.aspx) encrypts all ongoing communication with a per-session AES-256 symmetric key.</span></span>  


## <a name="making-the-second-hop"></a><span data-ttu-id="d3500-153">進行第二次跳躍</span><span class="sxs-lookup"><span data-stu-id="d3500-153">Making the second hop</span></span>

<span data-ttu-id="d3500-154">PowerShell 遠端預設會使用 (如果提供) Kerberos 或 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="d3500-154">By default, PowerShell Remoting uses Kerberos (if available) or NTLM for authentication.</span></span> <span data-ttu-id="d3500-155">這兩種通訊協定驗證遠端電腦時，皆不需要將認證傳送到電腦。</span><span class="sxs-lookup"><span data-stu-id="d3500-155">Both of these protocols authenticate to the remote machine without sending credentials to it.</span></span>
<span data-ttu-id="d3500-156">這是最安全的驗證方式，但因為遠端電腦並沒有使用者的認證，所以無法代替使用者存取其他電腦與服務。</span><span class="sxs-lookup"><span data-stu-id="d3500-156">This is the most secure way to authenticate, but because the remote machine does not have the user's credentials, it cannot access other computers and services on the user's behalf.</span></span> <span data-ttu-id="d3500-157">這稱為「雙躍點 」問題。</span><span class="sxs-lookup"><span data-stu-id="d3500-157">This is known as the "Double-Hop" problem.</span></span>

<span data-ttu-id="d3500-158">避免這個問題的方法有數種︰</span><span class="sxs-lookup"><span data-stu-id="d3500-158">There are several ways to avoid this problem:</span></span>

### <a name="kerberos-constrained-delegation"></a><span data-ttu-id="d3500-159">Kerberos 限制委派</span><span class="sxs-lookup"><span data-stu-id="d3500-159">Kerberos Constrained Delegation</span></span>

<span data-ttu-id="d3500-160">若是高度受信任的伺服器，可以啟用 [Kerberos 限制委派](https://technet.microsoft.com/en-us/library/cc995228.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d3500-160">For highly trusted servers, you can enable [Kerberos Constrained Delegation](https://technet.microsoft.com/en-us/library/cc995228.aspx).</span></span> <span data-ttu-id="d3500-161">遠端伺服器如此即可對指定的電腦與服務清單，模擬已經過驗證的使用者。</span><span class="sxs-lookup"><span data-stu-id="d3500-161">This allows the remote server to impersonate the authenticated user to a specified list of computers and services.</span></span>

### <a name="trust-between-remote-computers"></a><span data-ttu-id="d3500-162">遠端電腦之間的信任</span><span class="sxs-lookup"><span data-stu-id="d3500-162">Trust between remote computers</span></span>

<span data-ttu-id="d3500-163">如果信任使用者從遠端連線到 *Server1*，取用 *Server2* 的資源，可以明確授與 *Server1* 存取這些資源。</span><span class="sxs-lookup"><span data-stu-id="d3500-163">If you trust users connected remotely to *Server1* to resources on *Server2*, you can explicitly grant *Server1* access to those resources.</span></span>

### <a name="use-explicit-credentials-when-accessing-remote-resources"></a><span data-ttu-id="d3500-164">存取遠端資源時使用明確認證</span><span class="sxs-lookup"><span data-stu-id="d3500-164">Use explicit credentials when accessing remote resources</span></span>

<span data-ttu-id="d3500-165">您可以使用 Cmdlet 的 **Credential** 參數，明確地將認證傳遞至遠端資源。</span><span class="sxs-lookup"><span data-stu-id="d3500-165">You can explicitly pass your credentials to a remote resource by using the **Credential** parameter of a cmdlet.</span></span> <span data-ttu-id="d3500-166">例如：</span><span class="sxs-lookup"><span data-stu-id="d3500-166">For example:</span></span>

```powershell
$myCredential = Get-Credential
New-PSDrive -Name Tools \\Server2\Shared\Tools -Credential $myCredential 
```

### <a name="credssp"></a><span data-ttu-id="d3500-167">CredSSP</span><span class="sxs-lookup"><span data-stu-id="d3500-167">CredSSP</span></span>

<span data-ttu-id="d3500-168">您可以使用[認證安全性支援提供者 (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) 進行驗證 (藉由將 "CredSSP"指定為呼叫 [New-PSSession](https://technet.microsoft.com/en-us/library/hh849717.aspx) Cmdlet 的 `Authentication` 參數值。</span><span class="sxs-lookup"><span data-stu-id="d3500-168">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) for authentication (by specifying "CredSSP" as the value of the `Authentication` parameter of a call to the [New-PSSession](https://technet.microsoft.com/en-us/library/hh849717.aspx) cmdlet.</span></span> <span data-ttu-id="d3500-169">CredSSP 會以純文字將認證傳遞至伺服器，因此加以使用時，可能會讓您暴露在認證遭竊的攻擊風險中。</span><span class="sxs-lookup"><span data-stu-id="d3500-169">CredSSP passes credentials in plain text to the server, so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="d3500-170">如果遠端電腦遭到入侵，攻擊者就能存取使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="d3500-170">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="d3500-171">預設會停用 CredSSP (用戶端與伺服器電腦皆是)。</span><span class="sxs-lookup"><span data-stu-id="d3500-171">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="d3500-172">只有在最受信任的環境中才應啟用 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="d3500-172">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="d3500-173">例如，因為網域控制站為高度受信任，所以網域系統管理員會連線到網域控制站。</span><span class="sxs-lookup"><span data-stu-id="d3500-173">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="d3500-174">如需使用 PowerShell 遠端的 CredSSP 時，安全性考量的詳細資訊，請參閱 [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp) (意外妨害：注意 CredSSP)。</span><span class="sxs-lookup"><span data-stu-id="d3500-174">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="d3500-175">如需認證遭竊攻擊的詳細資訊，請參閱[降低傳遞雜湊 (PtH) 攻擊與竊取其他認證](https://www.microsoft.com/en-us/download/details.aspx?id=36036)。</span><span class="sxs-lookup"><span data-stu-id="d3500-175">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>








