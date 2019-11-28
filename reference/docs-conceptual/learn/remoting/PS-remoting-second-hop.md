---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 在 PowerShell 遠端中進行第二次跳躍
ms.openlocfilehash: 567d75009f7d53e9e95e5480b275ec3991cfb9f5
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417622"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="f3d53-103">在 PowerShell 遠端中進行第二次跳躍</span><span class="sxs-lookup"><span data-stu-id="f3d53-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="f3d53-104">「第二個躍點問題」是指如下所示的情況︰</span><span class="sxs-lookup"><span data-stu-id="f3d53-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="f3d53-105">您已登入 _ServerA_。</span><span class="sxs-lookup"><span data-stu-id="f3d53-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="f3d53-106">從 _ServerA_，啟動遠端 PowerShell 工作階段，連線到 _ServerB_。</span><span class="sxs-lookup"><span data-stu-id="f3d53-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="f3d53-107">您透過 PowerShell 遠端工作階段在 _ServerB_ 上執行的命令，會嘗試存取 _ServerC_ 上的資源。</span><span class="sxs-lookup"><span data-stu-id="f3d53-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="f3d53-108">已拒絕 _ServerC_ 上的資源存取，因為您用來建立 PowerShell 遠端工作階段的認證未從 _ServerB_ 傳遞至 _ServerC_。</span><span class="sxs-lookup"><span data-stu-id="f3d53-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="f3d53-109">解決這個問題的方法有數種︰</span><span class="sxs-lookup"><span data-stu-id="f3d53-109">There are several ways to address this problem.</span></span> <span data-ttu-id="f3d53-110">在本主題中，我們將探討幾個最受歡迎的第二個躍點問題解決方案。</span><span class="sxs-lookup"><span data-stu-id="f3d53-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="f3d53-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="f3d53-111">CredSSP</span></span>

<span data-ttu-id="f3d53-112">您可以使用[認證安全性支援提供者 (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="f3d53-112">You can use the [Credential Security Support Provider (CredSSP)](/windows/win32/secauthn/credential-security-support-provider) for authentication.</span></span> <span data-ttu-id="f3d53-113">CredSSP 會在遠端伺服器上快取認證 (_ServerB_)，因此在使用時，可能會讓您暴露在認證遭竊的攻擊風險中。</span><span class="sxs-lookup"><span data-stu-id="f3d53-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="f3d53-114">如果遠端電腦遭到入侵，攻擊者就能存取使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="f3d53-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="f3d53-115">預設會停用 CredSSP (用戶端與伺服器電腦皆是)。</span><span class="sxs-lookup"><span data-stu-id="f3d53-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="f3d53-116">只有在最受信任的環境中才應啟用 CredSSP。</span><span class="sxs-lookup"><span data-stu-id="f3d53-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="f3d53-117">例如，因為網域控制站為高度受信任，所以網域系統管理員會連線到網域控制站。</span><span class="sxs-lookup"><span data-stu-id="f3d53-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="f3d53-118">如需使用 PowerShell 遠端的 CredSSP 時，安全性考量的詳細資訊，請參閱[意外妨害：注意 CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="f3d53-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="f3d53-119">如需認證遭竊攻擊的詳細資訊，請參閱[降低傳遞雜湊 (PtH) 攻擊與竊取其他認證](https://www.microsoft.com/en-us/download/details.aspx?id=36036)。</span><span class="sxs-lookup"><span data-stu-id="f3d53-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="f3d53-120">如需如何啟用及使用 CredSSP 進行 PowerShell 遠端功能的範例，請參閱 [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/) (使用 CredSSP 來解決第二個躍點問題)。</span><span class="sxs-lookup"><span data-stu-id="f3d53-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="f3d53-121">優點</span><span class="sxs-lookup"><span data-stu-id="f3d53-121">Pros</span></span>

- <span data-ttu-id="f3d53-122">這適用於 Windows Server 2008 或更新版本的所有伺服器。</span><span class="sxs-lookup"><span data-stu-id="f3d53-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="f3d53-123">缺點</span><span class="sxs-lookup"><span data-stu-id="f3d53-123">Cons</span></span>

- <span data-ttu-id="f3d53-124">有安全性弱點。</span><span class="sxs-lookup"><span data-stu-id="f3d53-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="f3d53-125">需要同時設定用戶端和伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="f3d53-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="f3d53-126">Kerberos 委派 (未受限)</span><span class="sxs-lookup"><span data-stu-id="f3d53-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="f3d53-127">您也可以使用 Kerberos 未受限制的委派進行第二次跳躍。</span><span class="sxs-lookup"><span data-stu-id="f3d53-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="f3d53-128">不過，這個方法無法控制委派認證的使用位置。</span><span class="sxs-lookup"><span data-stu-id="f3d53-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="f3d53-129">**注意：** 無法委派已設定 [這是機密帳戶，無法委派]  屬性的 Active Directory 帳戶。</span><span class="sxs-lookup"><span data-stu-id="f3d53-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="f3d53-130">如需詳細資訊，請參閱[安全性焦點：分析特殊權限帳戶的「這是機密帳戶，無法委派」](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) \(英文\) 和 [Kerberos 驗證工具和設定](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="f3d53-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="f3d53-131">優點</span><span class="sxs-lookup"><span data-stu-id="f3d53-131">Pros</span></span>

- <span data-ttu-id="f3d53-132">不需要任何特殊的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f3d53-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="f3d53-133">缺點</span><span class="sxs-lookup"><span data-stu-id="f3d53-133">Cons</span></span>

- <span data-ttu-id="f3d53-134">不支援 WinRM 的第二個躍點。</span><span class="sxs-lookup"><span data-stu-id="f3d53-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="f3d53-135">無法控制認證的使用位置，造成安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="f3d53-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="f3d53-136">Kerberos 限制委派</span><span class="sxs-lookup"><span data-stu-id="f3d53-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="f3d53-137">您可以使用舊版的限制委派 (不以資源為基礎) 來進行第二次跳躍。</span><span class="sxs-lookup"><span data-stu-id="f3d53-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="f3d53-138">請以 [使用任何驗證通訊協定] 選項設定 Kerberos 限制委派，以允許進行通訊協定轉換。</span><span class="sxs-lookup"><span data-stu-id="f3d53-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="f3d53-139">無法委派已設定 [這是機密帳戶，無法委派]  屬性的 Active Directory 帳戶。</span><span class="sxs-lookup"><span data-stu-id="f3d53-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="f3d53-140">如需詳細資訊，請參閱[安全性焦點：分析特殊權限帳戶的「這是機密帳戶，無法委派」](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) \(英文\) 和 [Kerberos 驗證工具和設定](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="f3d53-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="f3d53-141">優點</span><span class="sxs-lookup"><span data-stu-id="f3d53-141">Pros</span></span>

- <span data-ttu-id="f3d53-142">不需要任何特殊的程式碼</span><span class="sxs-lookup"><span data-stu-id="f3d53-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="f3d53-143">缺點</span><span class="sxs-lookup"><span data-stu-id="f3d53-143">Cons</span></span>

- <span data-ttu-id="f3d53-144">不支援 WinRM 的第二個躍點。</span><span class="sxs-lookup"><span data-stu-id="f3d53-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="f3d53-145">必須在遠端伺服器 (_ServerB_) 的 Active Directory 物件上設定。</span><span class="sxs-lookup"><span data-stu-id="f3d53-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="f3d53-146">僅限一個網域。</span><span class="sxs-lookup"><span data-stu-id="f3d53-146">Limited to one domain.</span></span> <span data-ttu-id="f3d53-147">無法跨網域或樹系。</span><span class="sxs-lookup"><span data-stu-id="f3d53-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="f3d53-148">需要更新物件和服務主體名稱 (SPN) 的權限。</span><span class="sxs-lookup"><span data-stu-id="f3d53-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="f3d53-149">以資源為基礎的 Kerberos 限制委派</span><span class="sxs-lookup"><span data-stu-id="f3d53-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="f3d53-150">使用以資源為基礎的 Kerberos 限制委派 (在 Windows Server 2012 中引入) 時，您會設定資源所在伺服器物件上的認證委派。</span><span class="sxs-lookup"><span data-stu-id="f3d53-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="f3d53-151">在上述的第二個躍點案例中，您會設定 _ServerC_ 以指定它接受委派認證的來源。</span><span class="sxs-lookup"><span data-stu-id="f3d53-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="f3d53-152">**注意：** 無法委派已設定 [這是機密帳戶，無法委派]  屬性的 Active Directory 帳戶。</span><span class="sxs-lookup"><span data-stu-id="f3d53-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="f3d53-153">如需詳細資訊，請參閱[安全性焦點：分析特殊權限帳戶的「這是機密帳戶，無法委派」](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) \(英文\) 和 [Kerberos 驗證工具和設定](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="f3d53-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="f3d53-154">優點</span><span class="sxs-lookup"><span data-stu-id="f3d53-154">Pros</span></span>

- <span data-ttu-id="f3d53-155">不會儲存認證。</span><span class="sxs-lookup"><span data-stu-id="f3d53-155">Credentials are not stored.</span></span>
- <span data-ttu-id="f3d53-156">使用 PowerShell Cmdlet 進行設定相當容易 -- 不需要特殊的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f3d53-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="f3d53-157">不需要任何特殊網域存取。</span><span class="sxs-lookup"><span data-stu-id="f3d53-157">No special domain access is required.</span></span>
- <span data-ttu-id="f3d53-158">可跨網域與樹系工作。</span><span class="sxs-lookup"><span data-stu-id="f3d53-158">Works across domains and forests.</span></span>
- <span data-ttu-id="f3d53-159">PowerShell 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f3d53-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="f3d53-160">缺點</span><span class="sxs-lookup"><span data-stu-id="f3d53-160">Cons</span></span>

- <span data-ttu-id="f3d53-161">需要 Windows Server 2012 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="f3d53-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="f3d53-162">不支援 WinRM 的第二個躍點。</span><span class="sxs-lookup"><span data-stu-id="f3d53-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="f3d53-163">需要更新物件和服務主體名稱 (SPN) 的權限。</span><span class="sxs-lookup"><span data-stu-id="f3d53-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="f3d53-164">範例</span><span class="sxs-lookup"><span data-stu-id="f3d53-164">Example</span></span>

<span data-ttu-id="f3d53-165">讓我們看看在 _ServerC_ 上設定以資源為基礎之限制委派的 PowerShell 範例，以允許來自 _ServerB_ 的委派認證。</span><span class="sxs-lookup"><span data-stu-id="f3d53-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="f3d53-166">這個範例會假設所有伺服器都執行 Windows Server 2012 或更新版本，而且任何伺服器所屬的每個網域都有至少一個 Windows Server 2012 網域控制站。</span><span class="sxs-lookup"><span data-stu-id="f3d53-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="f3d53-167">您必須先新增 `RSAT-AD-PowerShell` 功能以安裝 Active Directory PowerShell 模組，然後將該模組匯入到您的工作階段，之後才能設定限制委派︰</span><span class="sxs-lookup"><span data-stu-id="f3d53-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="f3d53-168">數個可用的 Cmdlet 現在有 **PrincipalsAllowedToDelegateToAccount** 參數︰</span><span class="sxs-lookup"><span data-stu-id="f3d53-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="f3d53-169">**PrincipalsAllowedToDelegateToAccount** 參數會設定 Active Directory 物件屬性 **msDS-AllowedToActOnBehalfOfOtherIdentity**，其中包含存取控制清單 (ACL)，指定哪些帳戶有權可委派認證給相關聯的帳戶 (在本例中，它會是 _Server_ 的電腦帳戶)。</span><span class="sxs-lookup"><span data-stu-id="f3d53-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="f3d53-170">現在，讓我們設定將用來代表伺服器的變數︰</span><span class="sxs-lookup"><span data-stu-id="f3d53-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="f3d53-171">WinRM (以及 PowerShell 遠端) 預設會以電腦帳戶的身分執行。</span><span class="sxs-lookup"><span data-stu-id="f3d53-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="f3d53-172">您可以檢視 `winrm` 服務的 **StartName** 屬性來看到這點︰</span><span class="sxs-lookup"><span data-stu-id="f3d53-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="f3d53-173">為了讓 _ServerC_ 從 _ServerB_ 上的 PowerShell 遠端工作階段允許委派，我們會藉由將 _ServerC_ 上的 **PrincipalsAllowedToDelegateToAccount** 參數設為 _ServerB_ 的電腦物件來授與存取權：</span><span class="sxs-lookup"><span data-stu-id="f3d53-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="f3d53-174">Kerberos [金鑰發行中心 (KDC)](/windows/win32/secauthn/key-distribution-center) 會快取遭拒的存取嘗試達 15 分鐘 (負快取)。</span><span class="sxs-lookup"><span data-stu-id="f3d53-174">The Kerberos [Key Distribution Center (KDC)](/windows/win32/secauthn/key-distribution-center) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="f3d53-175">如果 _ServerB_ 先前曾嘗試存取 _ServerC_，您必須叫用下列命令清除 _ServerB_ 上的快取︰</span><span class="sxs-lookup"><span data-stu-id="f3d53-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="f3d53-176">您也可以重新啟動電腦，或等待至少 15 分鐘的時間以清除快取。</span><span class="sxs-lookup"><span data-stu-id="f3d53-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="f3d53-177">清除快取之後，便可以成功執行程式碼，從 _ServerA_ 經過 _ServerB_ 再到 _ServerC_：</span><span class="sxs-lookup"><span data-stu-id="f3d53-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="f3d53-178">在此範例中，`$using` 變數用來使 _ServerB_ 可看見 `$ServerC` 變數。</span><span class="sxs-lookup"><span data-stu-id="f3d53-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="f3d53-179">如需 `$using` 變數的詳細資訊，請參閱 [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f3d53-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="f3d53-180">若要允許多部伺服器委派認證給 _ServerC_，請將 _ServerC_ 上 **PrincipalsAllowedToDelegateToAccount** 參數的值設為陣列︰</span><span class="sxs-lookup"><span data-stu-id="f3d53-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="f3d53-181">如果您想要進行跨網域的第二次跳躍，請新增 _ServerB_ 所屬網域的網域控制站完整網域名稱 (FQDN)︰</span><span class="sxs-lookup"><span data-stu-id="f3d53-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="f3d53-182">若要移除委派認證給 ServerC 的能力，請將 _ServerC_ 上 **PrincipalsAllowedToDelegateToAccount** 參數的值設為 `$null`︰</span><span class="sxs-lookup"><span data-stu-id="f3d53-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="f3d53-183">以資源為基礎的 Kerberos 限制委派相關資訊</span><span class="sxs-lookup"><span data-stu-id="f3d53-183">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="f3d53-184">Kerberos 驗證的新功能</span><span class="sxs-lookup"><span data-stu-id="f3d53-184">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- <span data-ttu-id="f3d53-185">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1) (Windows Server 2012 如何緩解 Kerberos 限制委派的痛苦，第 1 部分)</span><span class="sxs-lookup"><span data-stu-id="f3d53-185">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)</span></span>
- <span data-ttu-id="f3d53-186">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2) (Windows Server 2012 如何緩解 Kerberos 限制委派的痛苦，第 2 部分)</span><span class="sxs-lookup"><span data-stu-id="f3d53-186">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)</span></span>
- [<span data-ttu-id="f3d53-187">了解使用整合式 Windows 驗證之 Azure Active Directory 應用程式 Proxy 部署的 Kerberos 限制委派</span><span class="sxs-lookup"><span data-stu-id="f3d53-187">Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication</span></span>](https://aka.ms/kcdpaper)
- <span data-ttu-id="f3d53-188">[[MS-ADA2]：Active Directory 結構描述屬性 M2.210 屬性 msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="f3d53-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](/openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405)</span></span>
- <span data-ttu-id="f3d53-189">[[MS-SFU]：Kerberos 通訊協定延伸模組：Service for User 與限制委派通訊協定 1.3.2 S4U2Proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="f3d53-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](/openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a)</span></span>
- <span data-ttu-id="f3d53-190">[Resource Based Kerberos Constrained Delegation](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/) (以資源為基礎的 Kerberos 限制委派)</span><span class="sxs-lookup"><span data-stu-id="f3d53-190">[Resource Based Kerberos Constrained Delegation](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)</span></span>
- <span data-ttu-id="f3d53-191">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/) (使用 PrincipalsAllowedToDelegateToAccount 進行遠端系統管理，而不需要限制委派)</span><span class="sxs-lookup"><span data-stu-id="f3d53-191">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="f3d53-192">使用 RunAs 的 PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f3d53-192">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="f3d53-193">您可以在 _ServerB_ 上建立工作階段設定，並設定其 **RunAsCredential** 參數。</span><span class="sxs-lookup"><span data-stu-id="f3d53-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="f3d53-194">如需使用 PSSessionConfiguration 和 RunAs 來解決第二個躍點問題的資訊，請參閱 [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/) (PowerShell 遠端進行多重躍點的另一個解決方案)。</span><span class="sxs-lookup"><span data-stu-id="f3d53-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="f3d53-195">優點</span><span class="sxs-lookup"><span data-stu-id="f3d53-195">Pros</span></span>

- <span data-ttu-id="f3d53-196">適用於 WMF 3.0 或更新版本的任何伺服器。</span><span class="sxs-lookup"><span data-stu-id="f3d53-196">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="f3d53-197">缺點</span><span class="sxs-lookup"><span data-stu-id="f3d53-197">Cons</span></span>

- <span data-ttu-id="f3d53-198">需要在每個中繼伺服器 (_ServerB_) 設定 **PSSessionConfiguration** 和 **RunAs**。</span><span class="sxs-lookup"><span data-stu-id="f3d53-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="f3d53-199">使用網域 **RunAs** 帳戶時需要密碼維護</span><span class="sxs-lookup"><span data-stu-id="f3d53-199">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="f3d53-200">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="f3d53-200">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="f3d53-201">JEA 可讓您限制系統管理員可以在 PowerShell 工作階段期間執行哪些命令。</span><span class="sxs-lookup"><span data-stu-id="f3d53-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="f3d53-202">它可以用來解決第二個躍點問題。</span><span class="sxs-lookup"><span data-stu-id="f3d53-202">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="f3d53-203">如需 JEA 的資訊，請參閱 [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview)。</span><span class="sxs-lookup"><span data-stu-id="f3d53-203">For information about JEA, see [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="f3d53-204">優點</span><span class="sxs-lookup"><span data-stu-id="f3d53-204">Pros</span></span>

- <span data-ttu-id="f3d53-205">使用虛擬帳戶時不需要密碼維護。</span><span class="sxs-lookup"><span data-stu-id="f3d53-205">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="f3d53-206">缺點</span><span class="sxs-lookup"><span data-stu-id="f3d53-206">Cons</span></span>

- <span data-ttu-id="f3d53-207">需要 WMF 5.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="f3d53-207">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="f3d53-208">需要在每個中繼伺服器 (_ServerB_) 上設定。</span><span class="sxs-lookup"><span data-stu-id="f3d53-208">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="f3d53-209">在 Invoke-Command 指令碼區塊內傳遞認證</span><span class="sxs-lookup"><span data-stu-id="f3d53-209">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="f3d53-210">您可以在呼叫 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) Cmdlet 的 **ScriptBlock** 參數內傳遞認證。</span><span class="sxs-lookup"><span data-stu-id="f3d53-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="f3d53-211">優點</span><span class="sxs-lookup"><span data-stu-id="f3d53-211">Pros</span></span>

- <span data-ttu-id="f3d53-212">不需要特殊的伺服器設定。</span><span class="sxs-lookup"><span data-stu-id="f3d53-212">Does not require special server configuration.</span></span>
- <span data-ttu-id="f3d53-213">適用於執行 WMF 2.0 或更新版本的任何伺服器。</span><span class="sxs-lookup"><span data-stu-id="f3d53-213">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="f3d53-214">缺點</span><span class="sxs-lookup"><span data-stu-id="f3d53-214">Cons</span></span>

- <span data-ttu-id="f3d53-215">需要使用不便的程式碼技巧。</span><span class="sxs-lookup"><span data-stu-id="f3d53-215">Requires an awkward code technique.</span></span>
- <span data-ttu-id="f3d53-216">如果執行 WMF 2.0，需要不同的語法以便傳遞引數至遠端工作階段。</span><span class="sxs-lookup"><span data-stu-id="f3d53-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="f3d53-217">範例</span><span class="sxs-lookup"><span data-stu-id="f3d53-217">Example</span></span>

<span data-ttu-id="f3d53-218">下列範例示範如何在 **Invoke-Command** 指令碼區塊中傳遞認證︰</span><span class="sxs-lookup"><span data-stu-id="f3d53-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="f3d53-219">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3d53-219">See also</span></span>

[<span data-ttu-id="f3d53-220">PowerShell 遠端安全性考量</span><span class="sxs-lookup"><span data-stu-id="f3d53-220">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
