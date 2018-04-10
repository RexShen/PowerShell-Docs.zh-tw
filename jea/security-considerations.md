---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,安全性
title: JEA 安全性考量
ms.openlocfilehash: 1b83a73c047b056a4cc094d7e4b0bbf31f75f53a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="jea-security-considerations"></a><span data-ttu-id="bad04-103">JEA 安全性考量</span><span class="sxs-lookup"><span data-stu-id="bad04-103">JEA Security Considerations</span></span>

> <span data-ttu-id="bad04-104">適用對象：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bad04-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="bad04-105">JEA 可協助您減少電腦上的永久系統管理員數目來改善安全性的態勢。</span><span class="sxs-lookup"><span data-stu-id="bad04-105">JEA helps you improve your security posture by reducing the number of permanent administrators on your machines.</span></span>
<span data-ttu-id="bad04-106">它是藉由建立新的進入點，供使用者管理系統 (PowerShell 工作階段設定)，這個進入點預設會嚴密鎖定，以避免誤用。</span><span class="sxs-lookup"><span data-stu-id="bad04-106">It does so by creating a new entry point for users to manage the system (a PowerShell session configuration) which is tightly locked down by default to prevent misuse.</span></span>
<span data-ttu-id="bad04-107">需要部分 (但非無限) 電腦存取權以執行系統管理工作的使用者，可以授與他們對 JEA 端點的存取權。</span><span class="sxs-lookup"><span data-stu-id="bad04-107">Users who need some, but not unlimited, access to the machine to perform administrative tasks can be granted access to the JEA endpoint.</span></span>
<span data-ttu-id="bad04-108">由於 JEA 允許他們執行系統管理命令而不必具有直接的系統管理員存取權，您便可以將這些使用者從高度權限的安全性群組移除 (使其成為標準使用者)。</span><span class="sxs-lookup"><span data-stu-id="bad04-108">Because JEA allows them to run admin commands without directly having admin access, you can then remove those users from highly privileged security groups (make them standard users).</span></span>

<span data-ttu-id="bad04-109">本主題會更詳細地描述 JEA 安全性模型與最佳做法。</span><span class="sxs-lookup"><span data-stu-id="bad04-109">This topic describes the JEA security model and best practices in more detail.</span></span>

## <a name="run-as-account"></a><span data-ttu-id="bad04-110">執行身分帳戶</span><span class="sxs-lookup"><span data-stu-id="bad04-110">Run As account</span></span>

<span data-ttu-id="bad04-111">每個 JEA 端點有指定的「執行身分」帳戶，也就是執行連線使用者動作所用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="bad04-111">Each JEA endpoint has a designated "run as" account, which is the account under which the connecting user's actions are performed.</span></span>
<span data-ttu-id="bad04-112">此帳戶是可在[工作階段設定檔](session-configurations.md)中設定，且您選擇的帳戶與端點的安全性有很大的關係。</span><span class="sxs-lookup"><span data-stu-id="bad04-112">This account is configurable in the [session configuration file](session-configurations.md), and the account you choose has a significant bearing on the security of your endpoint.</span></span>

<span data-ttu-id="bad04-113">**虛擬帳戶**是設定執行身分帳戶的建議方式。</span><span class="sxs-lookup"><span data-stu-id="bad04-113">**Virtual accounts** are the recommended way of configuring the run as account.</span></span>
<span data-ttu-id="bad04-114">虛擬帳戶是一次性、暫時的本機帳戶，針對連線使用者而建立，以便在其 JEA 工作階段期間使用。</span><span class="sxs-lookup"><span data-stu-id="bad04-114">Virtual accounts are one-time, temporary local accounts that are created for the connecting user to use during the duration of their JEA session.</span></span>
<span data-ttu-id="bad04-115">他們的工作階段一終止，虛擬帳戶便會損毀，無法再使用。</span><span class="sxs-lookup"><span data-stu-id="bad04-115">As soon as their session is terminated, the virtual account will be destroyed and cannot be used anymore.</span></span>
<span data-ttu-id="bad04-116">連線使用者不知道虛擬帳戶的認證，且無法使用虛擬帳戶透過其他方式存取系統，例如遠端桌面或未受限制的 PowerShell 端點。</span><span class="sxs-lookup"><span data-stu-id="bad04-116">The connecting user does not know the credentials for the virtual account and cannot use the virtual account to access the system via other means, such as Remote Desktop or an unconstrained PowerShell endpoint.</span></span>

<span data-ttu-id="bad04-117">根據預設，虛擬帳戶屬於電腦上的本機系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="bad04-117">By default, virtual accounts belong to the local administrators group on the machine.</span></span>
<span data-ttu-id="bad04-118">這可讓他們有完整權限可管理系統上的任何資源，但沒有權限來管理網路上的資源。</span><span class="sxs-lookup"><span data-stu-id="bad04-118">This gives them full rights to manage anything on the system, but no rights to manage resources on the network.</span></span>
<span data-ttu-id="bad04-119">向其他電腦進行驗證時，使用者內容將是本機電腦帳戶，而不是虛擬帳戶。</span><span class="sxs-lookup"><span data-stu-id="bad04-119">When authenticating with other machines, the user context will be that of the local computer account, not the virtual account.</span></span>

<span data-ttu-id="bad04-120">網域控制站是特殊案例，因為其中沒有本機系統管理員群組的概念。</span><span class="sxs-lookup"><span data-stu-id="bad04-120">Domain controllers are a special case since there is no concept of a local administrators group.</span></span>
<span data-ttu-id="bad04-121">反過來說，虛擬帳戶將會屬於 Domain Admins，並且可以管理網域控制站上的目錄服務。</span><span class="sxs-lookup"><span data-stu-id="bad04-121">Instead, virtual accounts belong to Domain Admins instead and can manage the directory services on the domain controller.</span></span>
<span data-ttu-id="bad04-122">網域識別仍限制無法在已具現化 JEA 工作階段的網域控制站上使用，且任何的網路存取將會改為顯示成來自網域控制站電腦物件。</span><span class="sxs-lookup"><span data-stu-id="bad04-122">The domain identity is still restricted to use on the domain controller where the JEA session was instantiated, and any network access will appear to come from the domain controller computer object instead.</span></span>

<span data-ttu-id="bad04-123">在這兩種情況下，您可以明確地定義虛擬帳戶應該屬於哪些安全性群組。</span><span class="sxs-lookup"><span data-stu-id="bad04-123">In both cases, you can also explicitly define which security groups the virtual account should belong to.</span></span>
<span data-ttu-id="bad04-124">當您執行的工作也可以不需本機/網域系統管理員權限而執行時，會是比較好的做法。</span><span class="sxs-lookup"><span data-stu-id="bad04-124">This is a good practice when the task you are performing can be done without local/domain admin privileges.</span></span>
<span data-ttu-id="bad04-125">如果您已經為系統管理員定義安全性群組，可以直接將虛擬帳戶成員資格授與該群組，為它提供所需的權限。</span><span class="sxs-lookup"><span data-stu-id="bad04-125">If you already have a security group defined for your admins, you can simply grant the virtual account membership to that group to give it the permissions it needs.</span></span>
<span data-ttu-id="bad04-126">虛擬帳戶群組成員資格僅限於工作站和成員伺服器上的本機安全性群組，但在網域控制站上，他們只能是網域安全性群組的成員。</span><span class="sxs-lookup"><span data-stu-id="bad04-126">Virtual account group membership is limited to local security groups on workstation and member servers, but on a domain controller they can only be members of domain security groups.</span></span>
<span data-ttu-id="bad04-127">一旦您指定虛擬帳戶所屬的一或多個安全性群組，它將不再屬於預設群組 (本機系統管理員或網域系統管理員)。</span><span class="sxs-lookup"><span data-stu-id="bad04-127">Once you specify one or more security groups for the virtual account to belong to, it will no longer belong to the default groups (local admin or domain admin).</span></span>

<span data-ttu-id="bad04-128">下表摘要列出針對虛擬帳戶的可能設定選項和產生的權限</span><span class="sxs-lookup"><span data-stu-id="bad04-128">The table below summarizes the possible configuration options and resulting permissions for virtual accounts</span></span>

<span data-ttu-id="bad04-129">電腦類型</span><span class="sxs-lookup"><span data-stu-id="bad04-129">Computer type</span></span>                | <span data-ttu-id="bad04-130">虛擬帳戶群組設定</span><span class="sxs-lookup"><span data-stu-id="bad04-130">Virtual account group configuration</span></span> | <span data-ttu-id="bad04-131">本機使用者內容</span><span class="sxs-lookup"><span data-stu-id="bad04-131">Local user context</span></span>                                      | <span data-ttu-id="bad04-132">網路使用者內容</span><span class="sxs-lookup"><span data-stu-id="bad04-132">Network user context</span></span>
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
<span data-ttu-id="bad04-133">網域控制站</span><span class="sxs-lookup"><span data-stu-id="bad04-133">Domain controller</span></span>            | <span data-ttu-id="bad04-134">Default</span><span class="sxs-lookup"><span data-stu-id="bad04-134">Default</span></span>                             | <span data-ttu-id="bad04-135">網域使用者，'*DOMAIN*\Domain Admins' 的成員</span><span class="sxs-lookup"><span data-stu-id="bad04-135">Domain user, member of '*DOMAIN*\Domain Admins'</span></span>         | <span data-ttu-id="bad04-136">電腦帳戶</span><span class="sxs-lookup"><span data-stu-id="bad04-136">Computer account</span></span>
<span data-ttu-id="bad04-137">網域控制站</span><span class="sxs-lookup"><span data-stu-id="bad04-137">Domain controller</span></span>            | <span data-ttu-id="bad04-138">網域群組 A 和 B</span><span class="sxs-lookup"><span data-stu-id="bad04-138">Domain groups A and B</span></span>               | <span data-ttu-id="bad04-139">網域使用者，'*DOMAIN*\A', '*DOMAIN*\B' 的成員</span><span class="sxs-lookup"><span data-stu-id="bad04-139">Domain user, member of '*DOMAIN*\A', '*DOMAIN*\B'</span></span>       | <span data-ttu-id="bad04-140">電腦帳戶</span><span class="sxs-lookup"><span data-stu-id="bad04-140">Computer account</span></span>
<span data-ttu-id="bad04-141">成員伺服器或工作站</span><span class="sxs-lookup"><span data-stu-id="bad04-141">Member server or workstation</span></span> | <span data-ttu-id="bad04-142">Default</span><span class="sxs-lookup"><span data-stu-id="bad04-142">Default</span></span>                             | <span data-ttu-id="bad04-143">本機使用者，'*BUILTIN*\Administrators' 的成員</span><span class="sxs-lookup"><span data-stu-id="bad04-143">Local user, member of '*BUILTIN*\Administrators'</span></span>        | <span data-ttu-id="bad04-144">電腦帳戶</span><span class="sxs-lookup"><span data-stu-id="bad04-144">Computer account</span></span>
<span data-ttu-id="bad04-145">成員伺服器或工作站</span><span class="sxs-lookup"><span data-stu-id="bad04-145">Member server or workstation</span></span> | <span data-ttu-id="bad04-146">本機群組 C 和 D</span><span class="sxs-lookup"><span data-stu-id="bad04-146">Local groups C and D</span></span>                | <span data-ttu-id="bad04-147">本機使用者，'*COMPUTER*\C' 和 '*COMPUTER*\D' 的成員</span><span class="sxs-lookup"><span data-stu-id="bad04-147">Local user, member of '*COMPUTER*\C' and '*COMPUTER*\D'</span></span> | <span data-ttu-id="bad04-148">電腦帳戶</span><span class="sxs-lookup"><span data-stu-id="bad04-148">Computer account</span></span>

<span data-ttu-id="bad04-149">當您查看安全性稽核事件與應用程式事件記錄檔時，您會看到每個 JEA 使用者工作階段都有唯一的虛擬帳戶。</span><span class="sxs-lookup"><span data-stu-id="bad04-149">When you look at security audit events and application event logs, you will see that each JEA user session has a unique virtual account.</span></span>
<span data-ttu-id="bad04-150">這可協助您從 JEA 端點中的使用者動作回溯到執行命令的原始使用者。</span><span class="sxs-lookup"><span data-stu-id="bad04-150">This helps you track user actions in a JEA endpoint back to the original user who ran the command.</span></span>
<span data-ttu-id="bad04-151">虛擬帳戶名稱採用下列格式："WinRM Virtual Users\\WinRM\_VA\_帳戶號碼\_網域\_SAM 帳戶名稱" 例如，如果網域 "Contoso" 中的使用者 "Alice" 重新啟動 JEA 端點中的服務，則與任何服務控制管理員事件相關聯的使用者名稱會是 "WinRM Virtual Users\\WinRM\_VA\_1\_contoso\_alice"。</span><span class="sxs-lookup"><span data-stu-id="bad04-151">Virtual account names follow the format "WinRM Virtual Users\\WinRM\_VA\_*ACCOUNTNUMBER*\_*DOMAIN*\_*sAMAccountName*" For example, if user "Alice" in domain "Contoso" restarts a service in a JEA endpoint, the username associated with any service control manager events would be "WinRM Virtual Users\\WinRM\_VA\_1\_contoso\_alice".</span></span>


<span data-ttu-id="bad04-152">**群組受管理的服務帳戶 (gMSA)** 適用於成員伺服器需要在 JEA 工作階段中存取網路資源時。</span><span class="sxs-lookup"><span data-stu-id="bad04-152">**Group managed service accounts (gMSAs)** are useful when a member server needs to have access to network resources in the JEA session.</span></span>
<span data-ttu-id="bad04-153">範例使用案例是用來控制不同電腦上所裝載之 REST API 存取的 JEA 端點。</span><span class="sxs-lookup"><span data-stu-id="bad04-153">An example use case for this is a JEA endpoint that is used to control access to a REST API hosted on a different machine.</span></span>
<span data-ttu-id="bad04-154">很容易即可撰寫函式，在 REST API 上進行所需的引動過程，但為了向 API 進行驗證，您需要網路身分識別。</span><span class="sxs-lookup"><span data-stu-id="bad04-154">It is easy to write functions to make the desired invocations on the REST API, but in order to authenticate with the API you need a network identity.</span></span>
<span data-ttu-id="bad04-155">使用群組受管理的服務帳戶可促成「第二個躍點」，同時仍可控制哪些電腦可以使用帳戶。</span><span class="sxs-lookup"><span data-stu-id="bad04-155">Using a group managed service account makes the "second hop" possible while still having control over which computers can use the account.</span></span>
<span data-ttu-id="bad04-156">gMSA 的有效權限由 gMSA 帳戶所屬安全性群組 (本機或網域) 定義。</span><span class="sxs-lookup"><span data-stu-id="bad04-156">The effective permissions of the gMSA are defined by the security groups (local or domain) to which the gMSA account belongs.</span></span>

<span data-ttu-id="bad04-157">JEA 端點設定為使用 gMSA 帳戶之後，所有 JEA 使用者的動作會顯示為來自相同的群組受管理的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="bad04-157">When a JEA endpoint is configured to use a gMSA account, the actions of all JEA users will appear to come from the same group managed service account.</span></span>
<span data-ttu-id="bad04-158">從動作回溯到特定使用者的唯一方法，是在 PowerShell 工作階段文字記錄中識別執行的命令集合。</span><span class="sxs-lookup"><span data-stu-id="bad04-158">The only way you can trace actions back to a specific user is to identify the set of commands run in a PowerShell session transcript.</span></span>

<span data-ttu-id="bad04-159">**傳遞認證**適合下列情況使用：您未指定執行身分帳戶，但想要讓 PowerShell 使用連線使用者的認證在遠端伺服器上執行命令。</span><span class="sxs-lookup"><span data-stu-id="bad04-159">**Pass-thru credentials** are used when you do not specify a run as account and want PowerShell to use the connecting user's credential to run commands on the remote server.</span></span>
<span data-ttu-id="bad04-160">「不」建議針對 JEA 使用此設定，因為您需要授與連線使用者對特殊權限管理群組的直接存取權。</span><span class="sxs-lookup"><span data-stu-id="bad04-160">This configuration is *not* recommended for JEA as it would require you to grant the connecting user direct access to privileged management groups.</span></span>
<span data-ttu-id="bad04-161">如果連線使用者已經有系統管理員權限，他們可以完全避免使用 JEA 並透過其他未受限制的方式來管理系統。</span><span class="sxs-lookup"><span data-stu-id="bad04-161">If the connecting user already has admin privileges, they can avoid JEA altogether and manage the system via other, unconstrained means.</span></span>
<span data-ttu-id="bad04-162">請參閱下節，了解 [JEA 無法防止系統管理員](#jea-does-not-protect-against-admins)的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bad04-162">See the section below on how [JEA does not protect against admins](#jea-does-not-protect-against-admins) for more information.</span></span>

<span data-ttu-id="bad04-163">**標準執行身分帳戶**可讓您指定整個 PowerShell 工作階段將執行的任何使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="bad04-163">**Standard run as accounts** allow you to specify any user account under which the entire PowerShell session will run.</span></span>
<span data-ttu-id="bad04-164">這是一項重要的差異，因為已設定為使用固定執行身分帳戶 (使用 `-RunAsCredential` 參數) 的工作階段設定不會察覺 JEA。</span><span class="sxs-lookup"><span data-stu-id="bad04-164">This is an important distinction, because a session configuration set to use a fixed run as account (with the `-RunAsCredential` parameter) is not JEA-aware.</span></span>
<span data-ttu-id="bad04-165">這表示角色定義不再如預期般運作，且獲得授權存取端點的每個使用者都會被指派相同的角色。</span><span class="sxs-lookup"><span data-stu-id="bad04-165">That means that role definitions no longer function as expected, and every user authorized to access the endpoint will be assigned the same role.</span></span>

<span data-ttu-id="bad04-166">您不應該在 JEA 端點上使用 RunAsCredential，因為難以從動作回溯到特定的使用者，並且也缺乏將使用者對應至角色的支援。</span><span class="sxs-lookup"><span data-stu-id="bad04-166">You should not use a RunAsCredential on a JEA endpoint because of the difficulty in tracing actions back to specific users and the lack of support for mapping users to roles.</span></span>

## <a name="winrm-endpoint-acl"></a><span data-ttu-id="bad04-167">WinRM 端點 ACL</span><span class="sxs-lookup"><span data-stu-id="bad04-167">WinRM Endpoint ACL</span></span>

<span data-ttu-id="bad04-168">如同一般的 PowerShell 遠端端點，每個 JEA 端點在 WinRM 設定中都有個別的存取控制清單 (ACL) 設定，控制誰可以向 JEA 端點進行驗證。</span><span class="sxs-lookup"><span data-stu-id="bad04-168">As with regular PowerShell remoting endpoints, each JEA endpoint has a separate access control list (ACL) set in the WinRM configuration that controls who can authenticate with the JEA endpoint.</span></span>
<span data-ttu-id="bad04-169">如果設定不當，受信任的使用者可能無法存取 JEA 端點，和/或不受信任的使用者可能取得存取權。</span><span class="sxs-lookup"><span data-stu-id="bad04-169">If improperly configured, trusted users may not be able to access the JEA endpoint and/or untrusted users may gain access.</span></span>
<span data-ttu-id="bad04-170">不過，WinRM ACL 不會影響將使用者對應至 JEA 角色。</span><span class="sxs-lookup"><span data-stu-id="bad04-170">The WinRM ACL does not, however, affect the mapping of users to JEA roles.</span></span>
<span data-ttu-id="bad04-171">那是由系統上登錄的工作階段設定檔中的 *RoleDefinitions* 欄位所控制。</span><span class="sxs-lookup"><span data-stu-id="bad04-171">That is controlled by the *RoleDefinitions* field in the session configuration file that was registered on the system.</span></span>

<span data-ttu-id="bad04-172">根據預設，當您使用工作階段設定檔和一或多個角色功能登錄 JEA 端點時，WinRM ACL 會設定為允許所有對應至端點的一或多個角色存取權。</span><span class="sxs-lookup"><span data-stu-id="bad04-172">By default, when you register a JEA endpoint using a session configuration file and one or more role capabilities, the WinRM ACL will be configured to allow all users mapping to one or more roles access to the endpoint.</span></span>
<span data-ttu-id="bad04-173">例如，使用下列命令設定的 JEA 工作階段，會授與完整存取權給 *CONTOSO\JEA\_Lev1* 和 *CONTOSO\JEA\_Lev2*。</span><span class="sxs-lookup"><span data-stu-id="bad04-173">For example, a JEA session configured using the following commands will grant full access to *CONTOSO\JEA\_Lev1* and *CONTOSO\JEA\_Lev2*.</span></span>

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

<span data-ttu-id="bad04-174">您可以使用 [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) Cmdlet 稽核使用者權限。</span><span class="sxs-lookup"><span data-stu-id="bad04-174">You can audit user permissions with the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

<span data-ttu-id="bad04-175">若要變更哪些使用者可以存取，請執行 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` 以取得互動式提示或執行 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` 來更新權限。</span><span class="sxs-lookup"><span data-stu-id="bad04-175">To change which users have access, run either `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` for an interactive prompt or `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` to update the permissions.</span></span>
<span data-ttu-id="bad04-176">使用者需要至少有「叫用」權利才能存取 JEA 端點。</span><span class="sxs-lookup"><span data-stu-id="bad04-176">Users need at least *Invoke* rights to access the JEA endpoint.</span></span>

<span data-ttu-id="bad04-177">如果其他使用者也獲得授與 JEA 端點的存取權，但不屬於工作階段設定檔中定義的任何角色，他們可以啟動 JEA 工作階段，但只有預設 Cmdlet 的存取權。</span><span class="sxs-lookup"><span data-stu-id="bad04-177">If additional users are granted access to the JEA endpoint but do not fall into any of the roles defined in the session configuration file, they will be able to start a JEA session but only have access to the default cmdlets.</span></span>
<span data-ttu-id="bad04-178">您可以藉由執行 `Get-PSSessionCapability` 稽核 JEA 端點中的使用者權限。</span><span class="sxs-lookup"><span data-stu-id="bad04-178">You can audit user permissions in a JEA endpoint by running `Get-PSSessionCapability`.</span></span>
<span data-ttu-id="bad04-179">請參閱 [JEA 上的稽核和報告](audit-and-report.md)一文，以取得有關稽核使用者可在 JEA 端點存取之命令的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bad04-179">Check out the [Auditing and Reporting on JEA](audit-and-report.md) article for more information about auditing which commands a user has access to in a JEA endpoint.</span></span>

## <a name="least-privilege-roles"></a><span data-ttu-id="bad04-180">最低權限角色</span><span class="sxs-lookup"><span data-stu-id="bad04-180">Least privilege roles</span></span>

<span data-ttu-id="bad04-181">在設計 JEA 角色時，請務必記得在幕後執行的虛擬或群組受管理的服務帳戶，通常具有無限制的存取權可管理本機電腦。</span><span class="sxs-lookup"><span data-stu-id="bad04-181">When designing JEA roles, it is important to remember that the virtual or group managed service account running behind the scenes often has unrestricted access to manage the local machine.</span></span>
<span data-ttu-id="bad04-182">透過限制可使用特殊權限的內容執行的應用程式與命令，JEA 角色功能可協助限制該帳戶的用途。</span><span class="sxs-lookup"><span data-stu-id="bad04-182">JEA role capabilities help restrict what that account can be used for by limiting the commands and applications that can be run using that privileged context.</span></span>
<span data-ttu-id="bad04-183">設計不當的角色可能會允許執行危險命令，可能允許使用者突破 JEA 界限或取得機密資訊的存取權。</span><span class="sxs-lookup"><span data-stu-id="bad04-183">Improperly designed roles can allow dangerous commands to run that may allow a user to break out of the JEA boundaries or obtain access to sensitive information.</span></span>

<span data-ttu-id="bad04-184">例如，請考慮下列角色功能項目：</span><span class="sxs-lookup"><span data-stu-id="bad04-184">For example, consider the following role capability entry:</span></span>

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

<span data-ttu-id="bad04-185">此角色功能可讓使用者執行任何 PowerShell Cmdlet，並使用來自 Microsoft.PowerShell.Management 模組的名詞 "Process"。</span><span class="sxs-lookup"><span data-stu-id="bad04-185">This role capability allows users to run any PowerShell cmdlet with the noun "Process" from the Microsoft.PowerShell.Management module.</span></span>
<span data-ttu-id="bad04-186">使用者可能需要存取像是 `Get-Process` 的 Cmdlet，以了解什麼應用程式在系統上執行，並存取 `Stop-Process` 以終止任何停止回應的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bad04-186">Users may need to access cmdlets like `Get-Process` to understand what applications are running on the system and `Stop-Process` to kill any hung applications.</span></span>
<span data-ttu-id="bad04-187">不過，此項目也允許 `Start-Process`，這可以用來以完整的系統管理員權限啟動任意程式。</span><span class="sxs-lookup"><span data-stu-id="bad04-187">However, this entry also allows `Start-Process`, which can be used to start up an arbitrary program with full administrator permissions.</span></span>
<span data-ttu-id="bad04-188">程式不需要在本機系統上安裝，因此敵人可以在提供連線使用者本機系統管理員權限的檔案共用上啟動程式、執行惡意程式碼等等。</span><span class="sxs-lookup"><span data-stu-id="bad04-188">The program doesn't need to be installed locally on the system, so an adversary could simply start a program on a file share that gives the connecting user local admin privileges, runs malware, and more.'</span></span>

<span data-ttu-id="bad04-189">這項相同角色功能的更安全版本應該如下︰</span><span class="sxs-lookup"><span data-stu-id="bad04-189">A more secure version of this same role capability would look like:</span></span>

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

<span data-ttu-id="bad04-190">請避免在角色功能使用萬用字元，並且務必要定期[稽核有效的使用者權限](audit-and-report.md#check-effective-rights-for-a-specific-user)，以了解使用者可以存取哪些命令。</span><span class="sxs-lookup"><span data-stu-id="bad04-190">Avoid using wildcards in role capabilities, and be sure to [audit effective user permissions](audit-and-report.md#check-effective-rights-for-a-specific-user) regularly to understand which commands a user has access to.</span></span>

## <a name="jea-does-not-protect-against-admins"></a><span data-ttu-id="bad04-191">JEA 無法防止系統管理員</span><span class="sxs-lookup"><span data-stu-id="bad04-191">JEA does not protect against admins</span></span>

<span data-ttu-id="bad04-192">JEA 的核心原則之一是它可讓非系統管理員執行「一些」管理工作。</span><span class="sxs-lookup"><span data-stu-id="bad04-192">One of the core principles of JEA is that it allows non-admins to perform *some* admin tasks.</span></span>
<span data-ttu-id="bad04-193">JEA 無法防止已經有系統管理員權限的使用者。</span><span class="sxs-lookup"><span data-stu-id="bad04-193">JEA does not protect against those who already have administrator privileges.</span></span>
<span data-ttu-id="bad04-194">屬於「網域系統管理員」、「本機系統管理員」或環境中其他高權限群組的使用者，仍然可以透過其他方式登入電腦，以避開 JEA 的保護。</span><span class="sxs-lookup"><span data-stu-id="bad04-194">Users who belong "domain admins," "local admins," or other highly privileged groups in your environment will still be able to get around JEA's protections by signing into the machine via another means.</span></span>
<span data-ttu-id="bad04-195">例如，他們可以使用 RDP 登入、使用遠端 MMC 主控台或連接至未受限制的 PowerShell 端點。</span><span class="sxs-lookup"><span data-stu-id="bad04-195">They could, for example, sign in with RDP, use remote MMC consoles, or connect to unconstrained PowerShell endpoints.</span></span>
<span data-ttu-id="bad04-196">系統上的本機系統管理員也可以修改 JEA 設定，允許其他使用者管理系統，或變更角色功能以擴充使用者可以在其 JEA 工作階段中執行的動作範圍。</span><span class="sxs-lookup"><span data-stu-id="bad04-196">Local admins on the system can also modify JEA configurations to allow additional users to manage the system or change a role capability to extend the scope of what a user can do in their JEA session.</span></span>
<span data-ttu-id="bad04-197">因此務必要評估您的 JEA 使用者延伸權限，看看他們是否有其他方法可取得系統的特殊權限存取。</span><span class="sxs-lookup"><span data-stu-id="bad04-197">It is therefore important to evaluate your JEA users' extended permissions to see if there are other ways they could gain privileged access to the system.</span></span>

<span data-ttu-id="bad04-198">常見的做法是使用 JEA 進行一般日常維護，並且擁有「即時 」(Just-in-Time) 的特殊權限存取管理解決方案，可讓使用者在緊急情況下暫時成為本機系統管理員。</span><span class="sxs-lookup"><span data-stu-id="bad04-198">A common practice is to use JEA for regular day-to-day maintenance and have a "just in time" privileged access management solution allow users to temporarily become local admins in emergency situations.</span></span>
<span data-ttu-id="bad04-199">這有助於確保使用者在系統上不是永久的系統管理員，但如果 (並且唯有) 他們完成的工作流程會記錄他們對那些權限的使用，便可以取得那些權限。</span><span class="sxs-lookup"><span data-stu-id="bad04-199">This helps ensure users are not permanent admins on the system, but can get those rights if, and only when, they complete a workflow that documents their use of those permissions.</span></span>