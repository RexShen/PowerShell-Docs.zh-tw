---
ms.date: 05/14/2020
keywords: powershell,cmdlet
title: 在 PowerShell 遠端中進行第二次跳躍
description: 本文說明為 PowerShell 遠端設定第二躍點驗證的各種方法，包含安全性含意與建議。
ms.openlocfilehash: 905b27b4e6c612249c945a741bbe0d2ba9ae28aa
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501366"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="54edb-104">在 PowerShell 遠端中進行第二次跳躍</span><span class="sxs-lookup"><span data-stu-id="54edb-104">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="54edb-105">「第二個躍點問題」是指如下所示的情況︰</span><span class="sxs-lookup"><span data-stu-id="54edb-105">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="54edb-106">您已登入 _ServerA_ 。</span><span class="sxs-lookup"><span data-stu-id="54edb-106">You are logged in to _ServerA_ .</span></span>
2. <span data-ttu-id="54edb-107">從 _ServerA_ ，啟動遠端 PowerShell 工作階段，連線到 _ServerB_ 。</span><span class="sxs-lookup"><span data-stu-id="54edb-107">From _ServerA_ , you start a remote PowerShell session to connect to _ServerB_ .</span></span>
3. <span data-ttu-id="54edb-108">您透過 PowerShell 遠端工作階段在 _ServerB_ 上執行的命令，會嘗試存取 _ServerC_ 上的資源。</span><span class="sxs-lookup"><span data-stu-id="54edb-108">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_ .</span></span>
4. <span data-ttu-id="54edb-109">已拒絕 _ServerC_ 上的資源存取，因為您用來建立 PowerShell 遠端工作階段的認證未從 _ServerB_ 傳遞至 _ServerC_ 。</span><span class="sxs-lookup"><span data-stu-id="54edb-109">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_ .</span></span>

<span data-ttu-id="54edb-110">解決這個問題的方法有數種︰</span><span class="sxs-lookup"><span data-stu-id="54edb-110">There are several ways to address this problem.</span></span> <span data-ttu-id="54edb-111">下表依喜好設定的順序列出方法。</span><span class="sxs-lookup"><span data-stu-id="54edb-111">The following table lists the methods in order of preference.</span></span>

|                      <span data-ttu-id="54edb-112">組態</span><span class="sxs-lookup"><span data-stu-id="54edb-112">Configuration</span></span>                       |                                  <span data-ttu-id="54edb-113">附註</span><span class="sxs-lookup"><span data-stu-id="54edb-113">Note</span></span>                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="54edb-114">CredSSP</span><span class="sxs-lookup"><span data-stu-id="54edb-114">CredSSP</span></span>                                                  | <span data-ttu-id="54edb-115">簡單易用與安全性兼具</span><span class="sxs-lookup"><span data-stu-id="54edb-115">Balances ease of use and security</span></span>                                      |
| <span data-ttu-id="54edb-116">以資源為基礎的 Kerberos 限制委派</span><span class="sxs-lookup"><span data-stu-id="54edb-116">Resource-based Kerberos constrained delegation</span></span>           | <span data-ttu-id="54edb-117">設定更加簡單，安全性更高</span><span class="sxs-lookup"><span data-stu-id="54edb-117">Higher security with simpler configuration</span></span>                             |
| <span data-ttu-id="54edb-118">Kerberos 限制委派</span><span class="sxs-lookup"><span data-stu-id="54edb-118">Kerberos constrained delegation</span></span>                          | <span data-ttu-id="54edb-119">安全性高，但需要網域系統管理員</span><span class="sxs-lookup"><span data-stu-id="54edb-119">High security but requires Domain Administrator</span></span>                         |
| <span data-ttu-id="54edb-120">Kerberos 委派 (未受限)</span><span class="sxs-lookup"><span data-stu-id="54edb-120">Kerberos delegation (unconstrained)</span></span>                      | <span data-ttu-id="54edb-121">不建議使用</span><span class="sxs-lookup"><span data-stu-id="54edb-121">Not recommended</span></span>                                                        |
| <span data-ttu-id="54edb-122">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="54edb-122">Just Enough Administration (JEA)</span></span>                         | <span data-ttu-id="54edb-123">安全性最高，但需要更詳細的設定</span><span class="sxs-lookup"><span data-stu-id="54edb-123">Can provide the best security but requires more detailed configuration</span></span> |
| <span data-ttu-id="54edb-124">使用 RunAs 的 PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="54edb-124">PSSessionConfiguration using RunAs</span></span>                       | <span data-ttu-id="54edb-125">比較容易設定，但需要認證管理</span><span class="sxs-lookup"><span data-stu-id="54edb-125">Simpler to configure but requires credential management</span></span>                |
| <span data-ttu-id="54edb-126">在 `Invoke-Command` 指令碼區塊內傳遞認證</span><span class="sxs-lookup"><span data-stu-id="54edb-126">Pass credentials inside an `Invoke-Command` script block</span></span> | <span data-ttu-id="54edb-127">用法最簡單，但必須提供認證</span><span class="sxs-lookup"><span data-stu-id="54edb-127">Simplest to use but you must provide credentials</span></span>                       |

## <a name="credssp"></a><span data-ttu-id="54edb-128">CredSSP</span><span class="sxs-lookup"><span data-stu-id="54edb-128">CredSSP</span></span>

<span data-ttu-id="54edb-129">您可以使用[認證安全性支援提供者 (CredSSP)][credssp] 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="54edb-129">You can use the [Credential Security Support Provider (CredSSP)][credssp] for authentication.</span></span>
<span data-ttu-id="54edb-130">CredSSP 會在遠端伺服器上快取認證 ( _ServerB_ )，因此在使用時，可能會讓您暴露在認證遭竊的攻擊風險中。</span><span class="sxs-lookup"><span data-stu-id="54edb-130">CredSSP caches credentials on the remote server ( _ServerB_ ), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="54edb-131">如果遠端電腦遭到入侵，攻擊者就能存取使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="54edb-131">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="54edb-132">預設會停用 CredSSP (用戶端與伺服器電腦皆是)。</span><span class="sxs-lookup"><span data-stu-id="54edb-132">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="54edb-133">只有在最受信任的環境中才應啟用 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="54edb-133">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="54edb-134">例如，因為網域控制站為高度受信任，所以網域系統管理員會連線到網域控制站。</span><span class="sxs-lookup"><span data-stu-id="54edb-134">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="54edb-135">如需使用 PowerShell 遠端的 CredSSP 時，安全性考量的詳細資訊，請參閱[意外妨害：注意 CredSSP][beware] \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="54edb-135">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP][beware].</span></span>

<span data-ttu-id="54edb-136">如需認證遭竊攻擊的詳細資訊，請參閱[降低傳遞雜湊 (PtH) 攻擊與竊取其他認證][pth]。</span><span class="sxs-lookup"><span data-stu-id="54edb-136">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft][pth].</span></span>

<span data-ttu-id="54edb-137">如需有關如何啟用及使用 CredSSP 來進行 PowerShell 遠端處理的範例，請參閱 [使用 CredSSP 來啟用 PowerShell "Second-Hop" 功能][credssp-psblog] \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="54edb-137">For an example of how to enable and use CredSSP for PowerShell remoting, see [Enable PowerShell "Second-Hop" Functionality with CredSSP][credssp-psblog].</span></span>

<span data-ttu-id="54edb-138">**優點**</span><span class="sxs-lookup"><span data-stu-id="54edb-138">**Pros**</span></span>

- <span data-ttu-id="54edb-139">這適用於 Windows Server 2008 或更新版本的所有伺服器。</span><span class="sxs-lookup"><span data-stu-id="54edb-139">It works for all servers with Windows Server 2008 or later.</span></span>

<span data-ttu-id="54edb-140">**缺點**</span><span class="sxs-lookup"><span data-stu-id="54edb-140">**Cons**</span></span>

- <span data-ttu-id="54edb-141">有安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="54edb-141">Has security vulnerabilities.</span></span>
- <span data-ttu-id="54edb-142">需要同時設定用戶端和伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="54edb-142">Requires configuration of both client and server roles.</span></span>
- <span data-ttu-id="54edb-143">無法搭配受保護的使用者群組一起使用。</span><span class="sxs-lookup"><span data-stu-id="54edb-143">Does not work with the Protected Users group.</span></span> <span data-ttu-id="54edb-144">如需詳細資訊，請參閱[受保護的使用者安全性群組][protected-users] (英文)。</span><span class="sxs-lookup"><span data-stu-id="54edb-144">For more information, see [Protected Users Security Group][protected-users].</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="54edb-145">Kerberos 限制委派</span><span class="sxs-lookup"><span data-stu-id="54edb-145">Kerberos constrained delegation</span></span>

<span data-ttu-id="54edb-146">您可以使用舊版的限制委派 (不以資源為基礎) 來進行第二次跳躍。</span><span class="sxs-lookup"><span data-stu-id="54edb-146">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="54edb-147">請以 [使用任何驗證通訊協定] 選項設定 Kerberos 限制委派，以允許進行通訊協定轉換。</span><span class="sxs-lookup"><span data-stu-id="54edb-147">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

<span data-ttu-id="54edb-148">**優點**</span><span class="sxs-lookup"><span data-stu-id="54edb-148">**Pros**</span></span>

- <span data-ttu-id="54edb-149">不需要任何特殊的程式碼</span><span class="sxs-lookup"><span data-stu-id="54edb-149">Requires no special coding</span></span>
- <span data-ttu-id="54edb-150">不會儲存認證。</span><span class="sxs-lookup"><span data-stu-id="54edb-150">Credentials are not stored.</span></span>

<span data-ttu-id="54edb-151">**缺點**</span><span class="sxs-lookup"><span data-stu-id="54edb-151">**Cons**</span></span>

- <span data-ttu-id="54edb-152">不支援 WinRM 的第二個躍點。</span><span class="sxs-lookup"><span data-stu-id="54edb-152">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="54edb-153">需要網域系統管理員的權限才能設定。</span><span class="sxs-lookup"><span data-stu-id="54edb-153">Requires Domain Administrator access to configure.</span></span>
- <span data-ttu-id="54edb-154">必須在遠端伺服器 ( _ServerB_ ) 的 Active Directory 物件上設定。</span><span class="sxs-lookup"><span data-stu-id="54edb-154">Must be configured on the Active Directory object of the remote server ( _ServerB_ ).</span></span>
- <span data-ttu-id="54edb-155">僅限一個網域。</span><span class="sxs-lookup"><span data-stu-id="54edb-155">Limited to one domain.</span></span> <span data-ttu-id="54edb-156">無法跨網域或樹系。</span><span class="sxs-lookup"><span data-stu-id="54edb-156">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="54edb-157">需要更新物件和服務主體名稱 (SPN) 的權限。</span><span class="sxs-lookup"><span data-stu-id="54edb-157">Requires rights to update objects and Service Principal Names (SPNs).</span></span>
- <span data-ttu-id="54edb-158">_ServerB_ 不需要使用者操作，就能直接代表使用者，將 Kerberos 票證擷取至 _ServerC_ 。</span><span class="sxs-lookup"><span data-stu-id="54edb-158">_ServerB_ can acquire a Kerberos ticket to _ServerC_ on behalf of the user without user intervention.</span></span>

> [!NOTE]
> <span data-ttu-id="54edb-159">無法委派已設定 [這是機密帳戶，無法委派] 屬性的 Active Directory 帳戶。</span><span class="sxs-lookup"><span data-stu-id="54edb-159">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="54edb-160">如需詳細資訊，請參閱[安全性焦點：分析特殊權限帳戶的「這是機密帳戶，無法委派」][blog] \(英文\) 和 [Kerberos 驗證工具和設定][ktools] \(英文\)</span><span class="sxs-lookup"><span data-stu-id="54edb-160">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="54edb-161">以資源為基礎的 Kerberos 限制委派</span><span class="sxs-lookup"><span data-stu-id="54edb-161">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="54edb-162">使用以資源為基礎的 Kerberos 限制委派 (在 Windows Server 2012 中引入) 時，您會設定資源所在伺服器物件上的認證委派。</span><span class="sxs-lookup"><span data-stu-id="54edb-162">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span> <span data-ttu-id="54edb-163">在上述第二個躍點情節中，您設定了 _ServerC_ ，以指定其接受之委派認證的來源。</span><span class="sxs-lookup"><span data-stu-id="54edb-163">In the second hop scenario described above, you configure _ServerC_ to specify from where it accepts delegated credentials.</span></span>

<span data-ttu-id="54edb-164">**優點**</span><span class="sxs-lookup"><span data-stu-id="54edb-164">**Pros**</span></span>

- <span data-ttu-id="54edb-165">不會儲存認證。</span><span class="sxs-lookup"><span data-stu-id="54edb-165">Credentials are not stored.</span></span>
- <span data-ttu-id="54edb-166">使用 PowerShell Cmdlet 設定。</span><span class="sxs-lookup"><span data-stu-id="54edb-166">Configured using PowerShell cmdlets.</span></span> <span data-ttu-id="54edb-167">無須任何特殊程式碼。</span><span class="sxs-lookup"><span data-stu-id="54edb-167">No special coding required.</span></span>
- <span data-ttu-id="54edb-168">無須網域系統管理員的權限就能設定。</span><span class="sxs-lookup"><span data-stu-id="54edb-168">Does not require Domain Administrator access to configure.</span></span>
- <span data-ttu-id="54edb-169">可跨網域與樹系工作。</span><span class="sxs-lookup"><span data-stu-id="54edb-169">Works across domains and forests.</span></span>

<span data-ttu-id="54edb-170">**缺點**</span><span class="sxs-lookup"><span data-stu-id="54edb-170">**Cons**</span></span>

- <span data-ttu-id="54edb-171">需要 Windows Server 2012 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="54edb-171">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="54edb-172">不支援 WinRM 的第二個躍點。</span><span class="sxs-lookup"><span data-stu-id="54edb-172">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="54edb-173">需要更新物件和服務主體名稱 (SPN) 的權限。</span><span class="sxs-lookup"><span data-stu-id="54edb-173">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

> [!NOTE]
> <span data-ttu-id="54edb-174">無法委派已設定 [這是機密帳戶，無法委派] 屬性的 Active Directory 帳戶。</span><span class="sxs-lookup"><span data-stu-id="54edb-174">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="54edb-175">如需詳細資訊，請參閱[安全性焦點：分析特殊權限帳戶的「這是機密帳戶，無法委派」][blog] \(英文\) 和 [Kerberos 驗證工具和設定][ktools] \(英文\)</span><span class="sxs-lookup"><span data-stu-id="54edb-175">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts][blog] and [Kerberos Authentication Tools and Settings][ktools].</span></span>

### <a name="example"></a><span data-ttu-id="54edb-176">範例</span><span class="sxs-lookup"><span data-stu-id="54edb-176">Example</span></span>

<span data-ttu-id="54edb-177">下列 PowerShell 範例昦 _ServerC_ 上，設定以資源型的限制式委派，以允許來自 _ServerB_ 的委派認證，現在讓我們一起來看看。</span><span class="sxs-lookup"><span data-stu-id="54edb-177">Let's look at a PowerShell example that configures resource-based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_ .</span></span> <span data-ttu-id="54edb-178">這個範例會假設所有伺服器都執行 Windows Server 2012 或更新版本，而且任何伺服器所屬的每個網域都有至少一個 Windows Server 2012 網域控制站。</span><span class="sxs-lookup"><span data-stu-id="54edb-178">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="54edb-179">您必須先新增 `RSAT-AD-PowerShell` 功能以安裝 Active Directory PowerShell 模組，然後將該模組匯入到您的工作階段，之後才能設定限制委派︰</span><span class="sxs-lookup"><span data-stu-id="54edb-179">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
Add-WindowsFeature RSAT-AD-PowerShell
Import-Module ActiveDirectory
Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="54edb-180">數個可用的 Cmdlet 現在有 **PrincipalsAllowedToDelegateToAccount** 參數︰</span><span class="sxs-lookup"><span data-stu-id="54edb-180">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```Output
CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="54edb-181">**PrincipalsAllowedToDelegateToAccount** 參數會設定 Active Directory 物件屬性 **msDS-AllowedToActOnBehalfOfOtherIdentity** ，此屬性包含存取控制清單 (ACL)，指定哪些帳戶有權委派認證給相關聯的帳戶 (在本例中是 _ServerA_ 的電腦帳戶)。</span><span class="sxs-lookup"><span data-stu-id="54edb-181">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity** , which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _ServerA_ ).</span></span>

<span data-ttu-id="54edb-182">現在，讓我們設定將用來代表伺服器的變數︰</span><span class="sxs-lookup"><span data-stu-id="54edb-182">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="54edb-183">WinRM (以及 PowerShell 遠端) 預設會以電腦帳戶的身分執行。</span><span class="sxs-lookup"><span data-stu-id="54edb-183">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="54edb-184">您可以檢視 `winrm` 服務的 **StartName** 屬性來看到這點︰</span><span class="sxs-lookup"><span data-stu-id="54edb-184">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
Get-CimInstance Win32_Service -Filter 'Name="winrm"' | Select-Object StartName
```

```Output
StartName
---------
NT AUTHORITY\NetworkService
```

<span data-ttu-id="54edb-185">為了讓 _ServerC_ 允許來自 _ServerB_ 之 PowerShell 遠端工作階段的委派，我們必須在 _ServerC_ 上，將 **PrincipalsAllowedToDelegateToAccount** 參數設為 _ServerB_ 的電腦物件：</span><span class="sxs-lookup"><span data-stu-id="54edb-185">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_ , we must set the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_ :</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="54edb-186">Kerberos [金鑰發佈中心 (KDC)](/windows/win32/secauthn/key-distribution-center) 會快取拒絕存取的存取嘗試 (負快取) 達 15 分鐘。</span><span class="sxs-lookup"><span data-stu-id="54edb-186">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied-access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="54edb-187">如果 _ServerB_ 先前曾嘗試存取 _ServerC_ ，您必須叫用下列命令清除 _ServerB_ 上的快取︰</span><span class="sxs-lookup"><span data-stu-id="54edb-187">If _ServerB_ has previously attempted to access _ServerC_ , you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="54edb-188">您也可以重新啟動電腦，或等待至少 15 分鐘的時間以清除快取。</span><span class="sxs-lookup"><span data-stu-id="54edb-188">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="54edb-189">清除快取之後，便可以成功執行程式碼，從 _ServerA_ 經過 _ServerB_ 再到 _ServerC_ ：</span><span class="sxs-lookup"><span data-stu-id="54edb-189">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_ :</span></span>

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

<span data-ttu-id="54edb-190">在此範例中，`$using` 變數用來使 _ServerB_ 可看見 `$ServerC` 變數。</span><span class="sxs-lookup"><span data-stu-id="54edb-190">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_ .</span></span>
<span data-ttu-id="54edb-191">如需 `$using` 變數的詳細資訊，請參閱 [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables)。</span><span class="sxs-lookup"><span data-stu-id="54edb-191">For more information about the `$using` variable, see [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables).</span></span>

<span data-ttu-id="54edb-192">若要允許多部伺服器委派認證給 _ServerC_ ，請將 _ServerC_ 上 **PrincipalsAllowedToDelegateToAccount** 參數的值設為陣列︰</span><span class="sxs-lookup"><span data-stu-id="54edb-192">To allow multiple servers to delegate credentials to _ServerC_ , set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

<span data-ttu-id="54edb-193">如果您想要進行跨網域的第二次跳躍，請新增 _ServerB_ 所屬網域的網域控制站完整網域名稱 (FQDN)︰</span><span class="sxs-lookup"><span data-stu-id="54edb-193">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="54edb-194">若要移除委派認證給 ServerC 的能力，請將 _ServerC_ 上 **PrincipalsAllowedToDelegateToAccount** 參數的值設為 `$null`︰</span><span class="sxs-lookup"><span data-stu-id="54edb-194">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="54edb-195">以資源為基礎的 Kerberos 限制委派相關資訊</span><span class="sxs-lookup"><span data-stu-id="54edb-195">Information on resource-based Kerberos constrained delegation</span></span>

- <span data-ttu-id="54edb-196">[Kerberos 驗證的新功能][whats-new]</span><span class="sxs-lookup"><span data-stu-id="54edb-196">[What's New in Kerberos Authentication][whats-new]</span></span>
- <span data-ttu-id="54edb-197">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1][kcd2012-1] (Windows Server 2012 如何緩解 Kerberos 限制委派的痛苦，第 1 部分)</span><span class="sxs-lookup"><span data-stu-id="54edb-197">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1][kcd2012-1]</span></span>
- <span data-ttu-id="54edb-198">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2][kcd2012-2] (Windows Server 2012 如何緩解 Kerberos 限制委派的痛苦，第 2 部分)</span><span class="sxs-lookup"><span data-stu-id="54edb-198">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2][kcd2012-2]</span></span>
- <span data-ttu-id="54edb-199">[了解使用整合式 Windows 驗證之 Azure Active Directory 應用程式 Proxy 部署的 Kerberos 限制委派][kcdpaper]</span><span class="sxs-lookup"><span data-stu-id="54edb-199">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication][kcdpaper]</span></span>
- <span data-ttu-id="54edb-200">[[MS-ADA2] Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2] ([MS-ADA2] Active Directory 結構描述屬性 M2.210 屬性 msDS-AllowedToActOnBehalfOfOtherIdentity)</span><span class="sxs-lookup"><span data-stu-id="54edb-200">[[MS-ADA2] Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2]</span></span>
- <span data-ttu-id="54edb-201">[[MS-SFU] Kerberos 通訊協定延伸模組：Service for User 與限制委派通訊協定 1.3.2 S4U2Proxy][MS-SFU] \(英文\)</span><span class="sxs-lookup"><span data-stu-id="54edb-201">[[MS-SFU] Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy][MS-SFU]</span></span>
- <span data-ttu-id="54edb-202">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount][remote-admin] (使用 PrincipalsAllowedToDelegateToAccount 進行遠端系統管理，而不需要限制委派)</span><span class="sxs-lookup"><span data-stu-id="54edb-202">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount][remote-admin]</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="54edb-203">Kerberos 委派 (未受限)</span><span class="sxs-lookup"><span data-stu-id="54edb-203">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="54edb-204">您也可以使用 Kerberos 未受限制的委派進行第二次跳躍。</span><span class="sxs-lookup"><span data-stu-id="54edb-204">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="54edb-205">如同所有 Kerberos 案例一樣，認證不予儲存。</span><span class="sxs-lookup"><span data-stu-id="54edb-205">Like all Kerberos scenarios, credentials are not stored.</span></span> <span data-ttu-id="54edb-206">此方法不支援 WinRM 的第二個躍點。</span><span class="sxs-lookup"><span data-stu-id="54edb-206">This method does not support the second hop for WinRM.</span></span>

> [!WARNING]
> <span data-ttu-id="54edb-207">此方法無法控制委派認證的使用位置，</span><span class="sxs-lookup"><span data-stu-id="54edb-207">This method provides no control of where delegated credentials are used.</span></span> <span data-ttu-id="54edb-208">而且安全性低於 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="54edb-208">It is less secure than CredSSP.</span></span> <span data-ttu-id="54edb-209">此方法只適用於測試案例。</span><span class="sxs-lookup"><span data-stu-id="54edb-209">This method should only be used for testing scenarios.</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="54edb-210">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="54edb-210">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="54edb-211">JEA 可讓您限制系統管理員可以在 PowerShell 工作階段期間執行哪些命令。</span><span class="sxs-lookup"><span data-stu-id="54edb-211">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="54edb-212">它可以用來解決第二個躍點問題。</span><span class="sxs-lookup"><span data-stu-id="54edb-212">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="54edb-213">如需 JEA 的資訊，請參閱 [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview)。</span><span class="sxs-lookup"><span data-stu-id="54edb-213">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

<span data-ttu-id="54edb-214">**優點**</span><span class="sxs-lookup"><span data-stu-id="54edb-214">**Pros**</span></span>

- <span data-ttu-id="54edb-215">使用虛擬帳戶時不需要密碼維護。</span><span class="sxs-lookup"><span data-stu-id="54edb-215">No password maintenance when using a virtual account.</span></span>

<span data-ttu-id="54edb-216">**缺點**</span><span class="sxs-lookup"><span data-stu-id="54edb-216">**Cons**</span></span>

- <span data-ttu-id="54edb-217">需要 WMF 5.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="54edb-217">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="54edb-218">需要在每個中繼伺服器 ( _ServerB_ ) 上設定。</span><span class="sxs-lookup"><span data-stu-id="54edb-218">Requires configuration on every intermediate server ( _ServerB_ ).</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="54edb-219">使用 RunAs 的 PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="54edb-219">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="54edb-220">您可以在 _ServerB_ 上建立工作階段設定，並設定其 **RunAsCredential** 參數。</span><span class="sxs-lookup"><span data-stu-id="54edb-220">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="54edb-221">如需使用 **PSSessionConfiguration** 與 **RunAs** 來解決第二個躍點問題的資訊，請參閱 [另一種解決 PowerShell 遠端多個躍點問題的方法][pssessionconfig]。</span><span class="sxs-lookup"><span data-stu-id="54edb-221">For information about using **PSSessionConfiguration** and **RunAs** to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting][pssessionconfig].</span></span>

<span data-ttu-id="54edb-222">**優點**</span><span class="sxs-lookup"><span data-stu-id="54edb-222">**Pros**</span></span>

- <span data-ttu-id="54edb-223">適用於 WMF 3.0 或更新版本的任何伺服器。</span><span class="sxs-lookup"><span data-stu-id="54edb-223">Works with any server with WMF 3.0 or later.</span></span>

<span data-ttu-id="54edb-224">**缺點**</span><span class="sxs-lookup"><span data-stu-id="54edb-224">**Cons**</span></span>

- <span data-ttu-id="54edb-225">需要在每個中繼伺服器 ( _ServerB_ ) 設定 **PSSessionConfiguration** 和 **RunAs** 。</span><span class="sxs-lookup"><span data-stu-id="54edb-225">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server ( _ServerB_ ).</span></span>
- <span data-ttu-id="54edb-226">使用網域 **RunAs** 帳戶時需要密碼維護</span><span class="sxs-lookup"><span data-stu-id="54edb-226">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="54edb-227">在 Invoke-Command 指令碼區塊內傳遞認證</span><span class="sxs-lookup"><span data-stu-id="54edb-227">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="54edb-228">您可以在呼叫 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) Cmdlet 的 **ScriptBlock** 參數內傳遞認證。</span><span class="sxs-lookup"><span data-stu-id="54edb-228">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

<span data-ttu-id="54edb-229">**優點**</span><span class="sxs-lookup"><span data-stu-id="54edb-229">**Pros**</span></span>

- <span data-ttu-id="54edb-230">不需要特殊的伺服器設定。</span><span class="sxs-lookup"><span data-stu-id="54edb-230">Does not require special server configuration.</span></span>
- <span data-ttu-id="54edb-231">適用於執行 WMF 2.0 或更新版本的任何伺服器。</span><span class="sxs-lookup"><span data-stu-id="54edb-231">Works on any server running WMF 2.0 or later.</span></span>

<span data-ttu-id="54edb-232">**缺點**</span><span class="sxs-lookup"><span data-stu-id="54edb-232">**Cons**</span></span>

- <span data-ttu-id="54edb-233">需要使用不便的程式碼技巧。</span><span class="sxs-lookup"><span data-stu-id="54edb-233">Requires an awkward code technique.</span></span>
- <span data-ttu-id="54edb-234">如果執行 WMF 2.0，需要不同的語法以便傳遞引數至遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="54edb-234">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="54edb-235">範例</span><span class="sxs-lookup"><span data-stu-id="54edb-235">Example</span></span>

<span data-ttu-id="54edb-236">下列範例示範如何在 **Invoke-Command** 指令碼區塊中傳遞認證︰</span><span class="sxs-lookup"><span data-stu-id="54edb-236">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="54edb-237">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54edb-237">See also</span></span>

[<span data-ttu-id="54edb-238">PowerShell 遠端安全性考量</span><span class="sxs-lookup"><span data-stu-id="54edb-238">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)

<!-- link references -->
[blog]: /archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts
[ktools]: /previous-versions/windows/it-pro/windows-server-2003/cc738673(v=ws.10)
[credssp]: /windows/win32/secauthn/credential-security-support-provider
[beware]: https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp
[pth]: https://www.microsoft.com/download/details.aspx?id=36036
[credssp-psblog]: https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/
[whats-new]: /previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11)
[kcd2012-1]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1
[kcd2012-2]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2
[kcdpaper]: https://aka.ms/kcdpaper
[MS-ADA2]: /openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405
[MS-SFU]: /openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a
[remote-admin]: /archive/blogs/taylorb/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount
[pssessionconfig]: /archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting
[protected-users]: /windows-server/security/credentials-protection-and-management/protected-users-security-group
