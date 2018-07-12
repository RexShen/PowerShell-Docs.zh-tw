---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: a5e55611ac59ff5bfecee59ba2b7d7669d08f840
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893734"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="bf786-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bf786-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="bf786-104">概要</span><span class="sxs-lookup"><span data-stu-id="bf786-104">SYNOPSIS</span></span>

<span data-ttu-id="bf786-105">在 Windows PowerShell® Web 存取授權規則集中新增授權規則。</span><span class="sxs-lookup"><span data-stu-id="bf786-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf786-106">語法</span><span class="sxs-lookup"><span data-stu-id="bf786-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="bf786-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="bf786-107">UserGroupNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="bf786-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="bf786-108">UserGroupNameComputerName</span></span>

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="bf786-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="bf786-109">UserNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="bf786-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="bf786-110">UserNameComputerName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="bf786-111">描述</span><span class="sxs-lookup"><span data-stu-id="bf786-111">DESCRIPTION</span></span>

<span data-ttu-id="bf786-112">**Add-PswaAuthorizationRule** Cmdlet 會在 Windows PowerShell® Web 存取授權規則集中新增授權規則。</span><span class="sxs-lookup"><span data-stu-id="bf786-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="bf786-113">您必須指定此規則的使用者、電腦和 Windows PowerShell 端點。</span><span class="sxs-lookup"><span data-stu-id="bf786-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="bf786-114">您可以依個別使用者帳戶和電腦名稱指定使用者和電腦，或藉由指定群組進行指定。</span><span class="sxs-lookup"><span data-stu-id="bf786-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="bf786-115">對於已加入 Active Directory 網域的電腦，此 Cmdlet 會使用電腦的安全性識別碼 (SID) 來建立規則。</span><span class="sxs-lookup"><span data-stu-id="bf786-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="bf786-116">這可讓您在登入頁面的 [電腦名稱] 欄位中，使用簡短名稱、完整網域名稱 (FQDN) 或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="bf786-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="bf786-117">對於未加入 Active Directory 網域的電腦，此 Cmdlet 會使用系統管理員所提供的電腦名稱來建立規則。</span><span class="sxs-lookup"><span data-stu-id="bf786-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="bf786-118">若要成功連線到這部電腦，終端使用者必須提供與出現在規則中完全相同的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="bf786-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="bf786-119">如果網路上有多部同名的電腦，簡短名稱可能會解析成多部電腦。</span><span class="sxs-lookup"><span data-stu-id="bf786-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="bf786-120">這在建立連線時可能會導致模稜兩可的情況。</span><span class="sxs-lookup"><span data-stu-id="bf786-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="bf786-121">例如，如果有名為 "*Server1*” 之工作群組電腦的規則，並將名為 *server1.contoso.com* 的新電腦加入網路，則使用授權規則進行的驗證會成功，且 Windows PowerShell Web 存取會嘗試連線到名為 “*Server1*” 的電腦。</span><span class="sxs-lookup"><span data-stu-id="bf786-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="bf786-122">不保證會建立與指定工作群組電腦的連線，此嘗試可能是針對名為 "*Server1*" 的工作群組或網域電腦。</span><span class="sxs-lookup"><span data-stu-id="bf786-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="bf786-123">為了減少模稜兩可的情況，建議您盡可能針對目的地電腦使用 FQDN 來建立授權規則。</span><span class="sxs-lookup"><span data-stu-id="bf786-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="bf786-124">授權規則會評估 Windows PowerShell Web 存取使用者的主要登入認證，而不是替代認證 (在登入頁面的 [選用連線設定] 區段中找到的第二組認證)。</span><span class="sxs-lookup"><span data-stu-id="bf786-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="bf786-125">如需相關範例，請參閱範例 6。</span><span class="sxs-lookup"><span data-stu-id="bf786-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="bf786-126">參數</span><span class="sxs-lookup"><span data-stu-id="bf786-126">Parameters</span></span>

### <a name="-computergroupname-string"></a><span data-ttu-id="bf786-127">-ComputerGroupName \<String\></span><span class="sxs-lookup"><span data-stu-id="bf786-127">-ComputerGroupName \<String\></span></span>

<span data-ttu-id="bf786-128">指定 Active Directory 網域服務 (AD DS) 或本機群組中，此規則授與存取權的電腦群組名稱。</span><span class="sxs-lookup"><span data-stu-id="bf786-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="bf786-129">別名</span><span class="sxs-lookup"><span data-stu-id="bf786-129">Aliases</span></span>                              | <span data-ttu-id="bf786-130">無</span><span class="sxs-lookup"><span data-stu-id="bf786-130">none</span></span>                                 |
| <span data-ttu-id="bf786-131">必要？</span><span class="sxs-lookup"><span data-stu-id="bf786-131">Required?</span></span>                            | <span data-ttu-id="bf786-132">true</span><span class="sxs-lookup"><span data-stu-id="bf786-132">true</span></span>                                 |
| <span data-ttu-id="bf786-133">位置？</span><span class="sxs-lookup"><span data-stu-id="bf786-133">Position?</span></span>                            | <span data-ttu-id="bf786-134">具名</span><span class="sxs-lookup"><span data-stu-id="bf786-134">named</span></span>                                |
| <span data-ttu-id="bf786-135">預設值</span><span class="sxs-lookup"><span data-stu-id="bf786-135">Default Value</span></span>                        | <span data-ttu-id="bf786-136">無</span><span class="sxs-lookup"><span data-stu-id="bf786-136">none</span></span>                                 |
| <span data-ttu-id="bf786-137">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="bf786-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf786-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="bf786-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="bf786-139">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="bf786-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf786-140">false</span><span class="sxs-lookup"><span data-stu-id="bf786-140">false</span></span>                                |

### <a name="-computername-string"></a><span data-ttu-id="bf786-141">-ComputerName \<String\></span><span class="sxs-lookup"><span data-stu-id="bf786-141">-ComputerName \<String\></span></span>

<span data-ttu-id="bf786-142">指定此規則授與存取權的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="bf786-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="bf786-143">別名</span><span class="sxs-lookup"><span data-stu-id="bf786-143">Aliases</span></span>                              | <span data-ttu-id="bf786-144">無</span><span class="sxs-lookup"><span data-stu-id="bf786-144">none</span></span>                                 |
| <span data-ttu-id="bf786-145">必要？</span><span class="sxs-lookup"><span data-stu-id="bf786-145">Required?</span></span>                            | <span data-ttu-id="bf786-146">true</span><span class="sxs-lookup"><span data-stu-id="bf786-146">true</span></span>                                 |
| <span data-ttu-id="bf786-147">位置？</span><span class="sxs-lookup"><span data-stu-id="bf786-147">Position?</span></span>                            | <span data-ttu-id="bf786-148">具名</span><span class="sxs-lookup"><span data-stu-id="bf786-148">named</span></span>                                |
| <span data-ttu-id="bf786-149">預設值</span><span class="sxs-lookup"><span data-stu-id="bf786-149">Default Value</span></span>                        | <span data-ttu-id="bf786-150">無</span><span class="sxs-lookup"><span data-stu-id="bf786-150">none</span></span>                                 |
| <span data-ttu-id="bf786-151">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="bf786-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf786-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="bf786-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="bf786-153">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="bf786-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf786-154">false</span><span class="sxs-lookup"><span data-stu-id="bf786-154">false</span></span>                                |

### <a name="-configurationname-string"></a><span data-ttu-id="bf786-155">-ConfigurationName \<String\></span><span class="sxs-lookup"><span data-stu-id="bf786-155">-ConfigurationName \<String\></span></span>

<span data-ttu-id="bf786-156">指定此規則授與存取權的 Windows PowerShell 工作階段設定名稱，也稱為 Runspace。</span><span class="sxs-lookup"><span data-stu-id="bf786-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="bf786-157">別名</span><span class="sxs-lookup"><span data-stu-id="bf786-157">Aliases</span></span>                              | <span data-ttu-id="bf786-158">無</span><span class="sxs-lookup"><span data-stu-id="bf786-158">none</span></span>                                 |
| <span data-ttu-id="bf786-159">必要？</span><span class="sxs-lookup"><span data-stu-id="bf786-159">Required?</span></span>                            | <span data-ttu-id="bf786-160">true</span><span class="sxs-lookup"><span data-stu-id="bf786-160">true</span></span>                                 |
| <span data-ttu-id="bf786-161">位置？</span><span class="sxs-lookup"><span data-stu-id="bf786-161">Position?</span></span>                            | <span data-ttu-id="bf786-162">具名</span><span class="sxs-lookup"><span data-stu-id="bf786-162">named</span></span>                                |
| <span data-ttu-id="bf786-163">預設值</span><span class="sxs-lookup"><span data-stu-id="bf786-163">Default Value</span></span>                        | <span data-ttu-id="bf786-164">無</span><span class="sxs-lookup"><span data-stu-id="bf786-164">none</span></span>                                 |
| <span data-ttu-id="bf786-165">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="bf786-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf786-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="bf786-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="bf786-167">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="bf786-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf786-168">false</span><span class="sxs-lookup"><span data-stu-id="bf786-168">false</span></span>                                |

### <a name="-credential--pscredential"></a><span data-ttu-id="bf786-169">-Credential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="bf786-169">-Credential  \<PSCredential\></span></span>

<span data-ttu-id="bf786-170">指定您要用來變更 Windows PowerShell Web 存取授權規則之使用者帳戶的 **PSCredential** 物件。</span><span class="sxs-lookup"><span data-stu-id="bf786-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="bf786-171">如果您未新增這個參數，此 Cmdlet 就會使用目前登入的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="bf786-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="bf786-172">若要取得從遠端新增授權規則所需的 **PSCredential** 物件，請執行 [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bf786-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="bf786-173">別名</span><span class="sxs-lookup"><span data-stu-id="bf786-173">Aliases</span></span>                              | <span data-ttu-id="bf786-174">無</span><span class="sxs-lookup"><span data-stu-id="bf786-174">none</span></span>                                 |
| <span data-ttu-id="bf786-175">必要？</span><span class="sxs-lookup"><span data-stu-id="bf786-175">Required?</span></span>                            | <span data-ttu-id="bf786-176">false</span><span class="sxs-lookup"><span data-stu-id="bf786-176">false</span></span>                                |
| <span data-ttu-id="bf786-177">位置？</span><span class="sxs-lookup"><span data-stu-id="bf786-177">Position?</span></span>                            | <span data-ttu-id="bf786-178">具名</span><span class="sxs-lookup"><span data-stu-id="bf786-178">named</span></span>                                |
| <span data-ttu-id="bf786-179">預設值</span><span class="sxs-lookup"><span data-stu-id="bf786-179">Default Value</span></span>                        | <span data-ttu-id="bf786-180">無</span><span class="sxs-lookup"><span data-stu-id="bf786-180">none</span></span>                                 |
| <span data-ttu-id="bf786-181">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="bf786-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf786-182">false</span><span class="sxs-lookup"><span data-stu-id="bf786-182">false</span></span>                                |
| <span data-ttu-id="bf786-183">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="bf786-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf786-184">false</span><span class="sxs-lookup"><span data-stu-id="bf786-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="bf786-185">-Force</span><span class="sxs-lookup"><span data-stu-id="bf786-185">-Force</span></span>

<span data-ttu-id="bf786-186">強制執行命令而不要求使用者確認。\\</span><span class="sxs-lookup"><span data-stu-id="bf786-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="bf786-187">此外，當您輸入簡單或簡短電腦名稱時 (例如非網域名稱的名稱或不完整的名稱)，它也會提示確認。</span><span class="sxs-lookup"><span data-stu-id="bf786-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="bf786-188">為了安全起見會要求確認，讓您只有在電腦位於工作群組時，才能使用簡單名稱來新增電腦。</span><span class="sxs-lookup"><span data-stu-id="bf786-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="bf786-189">別名</span><span class="sxs-lookup"><span data-stu-id="bf786-189">Aliases</span></span>                              | <span data-ttu-id="bf786-190">無</span><span class="sxs-lookup"><span data-stu-id="bf786-190">none</span></span>                                 |
| <span data-ttu-id="bf786-191">必要？</span><span class="sxs-lookup"><span data-stu-id="bf786-191">Required?</span></span>                            | <span data-ttu-id="bf786-192">false</span><span class="sxs-lookup"><span data-stu-id="bf786-192">false</span></span>                                |
| <span data-ttu-id="bf786-193">位置？</span><span class="sxs-lookup"><span data-stu-id="bf786-193">Position?</span></span>                            | <span data-ttu-id="bf786-194">具名</span><span class="sxs-lookup"><span data-stu-id="bf786-194">named</span></span>                                |
| <span data-ttu-id="bf786-195">預設值</span><span class="sxs-lookup"><span data-stu-id="bf786-195">Default Value</span></span>                        | <span data-ttu-id="bf786-196">無</span><span class="sxs-lookup"><span data-stu-id="bf786-196">none</span></span>                                 |
| <span data-ttu-id="bf786-197">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="bf786-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf786-198">false</span><span class="sxs-lookup"><span data-stu-id="bf786-198">false</span></span>                                |
| <span data-ttu-id="bf786-199">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="bf786-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf786-200">false</span><span class="sxs-lookup"><span data-stu-id="bf786-200">false</span></span>                                |

### <a name="-rulename-string"></a><span data-ttu-id="bf786-201">-RuleName \<String\></span><span class="sxs-lookup"><span data-stu-id="bf786-201">-RuleName \<String\></span></span>

<span data-ttu-id="bf786-202">指定此規則的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="bf786-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="bf786-203">別名</span><span class="sxs-lookup"><span data-stu-id="bf786-203">Aliases</span></span>                              | <span data-ttu-id="bf786-204">無</span><span class="sxs-lookup"><span data-stu-id="bf786-204">none</span></span>                                 |
| <span data-ttu-id="bf786-205">必要？</span><span class="sxs-lookup"><span data-stu-id="bf786-205">Required?</span></span>                            | <span data-ttu-id="bf786-206">false</span><span class="sxs-lookup"><span data-stu-id="bf786-206">false</span></span>                                |
| <span data-ttu-id="bf786-207">位置？</span><span class="sxs-lookup"><span data-stu-id="bf786-207">Position?</span></span>                            | <span data-ttu-id="bf786-208">具名</span><span class="sxs-lookup"><span data-stu-id="bf786-208">named</span></span>                                |
| <span data-ttu-id="bf786-209">預設值</span><span class="sxs-lookup"><span data-stu-id="bf786-209">Default Value</span></span>                        | <span data-ttu-id="bf786-210">無</span><span class="sxs-lookup"><span data-stu-id="bf786-210">none</span></span>                                 |
| <span data-ttu-id="bf786-211">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="bf786-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf786-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="bf786-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="bf786-213">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="bf786-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf786-214">false</span><span class="sxs-lookup"><span data-stu-id="bf786-214">false</span></span>                                |

### <a name="-usergroupname-string"></a><span data-ttu-id="bf786-215">-UserGroupName \<String\[\]\></span><span class="sxs-lookup"><span data-stu-id="bf786-215">-UserGroupName \<String\[\]\></span></span>

<span data-ttu-id="bf786-216">指定 AD DS 或本機群組中，此規則授與存取權的一或多個使用者群組名稱。</span><span class="sxs-lookup"><span data-stu-id="bf786-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="bf786-217">別名</span><span class="sxs-lookup"><span data-stu-id="bf786-217">Aliases</span></span>                              | <span data-ttu-id="bf786-218">無</span><span class="sxs-lookup"><span data-stu-id="bf786-218">none</span></span>                                 |
| <span data-ttu-id="bf786-219">必要？</span><span class="sxs-lookup"><span data-stu-id="bf786-219">Required?</span></span>                            | <span data-ttu-id="bf786-220">true</span><span class="sxs-lookup"><span data-stu-id="bf786-220">true</span></span>                                 |
| <span data-ttu-id="bf786-221">位置？</span><span class="sxs-lookup"><span data-stu-id="bf786-221">Position?</span></span>                            | <span data-ttu-id="bf786-222">具名</span><span class="sxs-lookup"><span data-stu-id="bf786-222">named</span></span>                                |
| <span data-ttu-id="bf786-223">預設值</span><span class="sxs-lookup"><span data-stu-id="bf786-223">Default Value</span></span>                        | <span data-ttu-id="bf786-224">無</span><span class="sxs-lookup"><span data-stu-id="bf786-224">none</span></span>                                 |
| <span data-ttu-id="bf786-225">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="bf786-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf786-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="bf786-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="bf786-227">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="bf786-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf786-228">false</span><span class="sxs-lookup"><span data-stu-id="bf786-228">false</span></span>                                |

### <a name="-username-string"></a><span data-ttu-id="bf786-229">-UserName \<String\[\]\></span><span class="sxs-lookup"><span data-stu-id="bf786-229">-UserName \<String\[\]\></span></span>

<span data-ttu-id="bf786-230">指定此規則授與存取權的一或多個使用者。</span><span class="sxs-lookup"><span data-stu-id="bf786-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="bf786-231">使用者名稱可以是閘道電腦上的本機使用者帳戶，或是 AD DS 中的使用者。</span><span class="sxs-lookup"><span data-stu-id="bf786-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="bf786-232">格式是 `domain\user` 或 `computer\user`。</span><span class="sxs-lookup"><span data-stu-id="bf786-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="bf786-233">別名</span><span class="sxs-lookup"><span data-stu-id="bf786-233">Aliases</span></span>                              | <span data-ttu-id="bf786-234">無</span><span class="sxs-lookup"><span data-stu-id="bf786-234">none</span></span>                                 |
| <span data-ttu-id="bf786-235">必要？</span><span class="sxs-lookup"><span data-stu-id="bf786-235">Required?</span></span>                            | <span data-ttu-id="bf786-236">true</span><span class="sxs-lookup"><span data-stu-id="bf786-236">true</span></span>                                 |
| <span data-ttu-id="bf786-237">位置？</span><span class="sxs-lookup"><span data-stu-id="bf786-237">Position?</span></span>                            | <span data-ttu-id="bf786-238">1</span><span class="sxs-lookup"><span data-stu-id="bf786-238">1</span></span>                                    |
| <span data-ttu-id="bf786-239">預設值</span><span class="sxs-lookup"><span data-stu-id="bf786-239">Default Value</span></span>                        | <span data-ttu-id="bf786-240">無</span><span class="sxs-lookup"><span data-stu-id="bf786-240">none</span></span>                                 |
| <span data-ttu-id="bf786-241">接受管線輸入？</span><span class="sxs-lookup"><span data-stu-id="bf786-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="bf786-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="bf786-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="bf786-243">接受萬用字元？</span><span class="sxs-lookup"><span data-stu-id="bf786-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="bf786-244">false</span><span class="sxs-lookup"><span data-stu-id="bf786-244">false</span></span>                                |

###  <a name="commonparameters"></a><span data-ttu-id="bf786-245">\<CommonParameters\></span><span class="sxs-lookup"><span data-stu-id="bf786-245">\<CommonParameters\></span></span>

<span data-ttu-id="bf786-246">這個 Cmdlet 支援一般參數：-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer 和 -OutVariable。</span><span class="sxs-lookup"><span data-stu-id="bf786-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="bf786-247">如需詳細資訊，請參閱 [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters)。</span><span class="sxs-lookup"><span data-stu-id="bf786-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="bf786-248">輸入</span><span class="sxs-lookup"><span data-stu-id="bf786-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="bf786-249">String</span><span class="sxs-lookup"><span data-stu-id="bf786-249">String</span></span>

<span data-ttu-id="bf786-250">此 Cmdlet 會接受字串或字串陣列作為輸入。</span><span class="sxs-lookup"><span data-stu-id="bf786-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="bf786-251">String\[\]</span><span class="sxs-lookup"><span data-stu-id="bf786-251">String\[\]</span></span>

<span data-ttu-id="bf786-252">此 Cmdlet 會接受字串或字串陣列作為輸入。</span><span class="sxs-lookup"><span data-stu-id="bf786-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="bf786-253">輸出</span><span class="sxs-lookup"><span data-stu-id="bf786-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="bf786-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="bf786-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="bf786-255">此 Cmdlet 會傳回授權規則物件。</span><span class="sxs-lookup"><span data-stu-id="bf786-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="bf786-256">範例</span><span class="sxs-lookup"><span data-stu-id="bf786-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="bf786-257">範例 1</span><span class="sxs-lookup"><span data-stu-id="bf786-257">EXAMPLE 1</span></span>

<span data-ttu-id="bf786-258">此範例會授權 *SMAdmins* 群組中的使用者，存取 *srv2* 上的工作階段設定 *PSWAEndpoint* 或受限制的 Runspace。\\</span><span class="sxs-lookup"><span data-stu-id="bf786-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="bf786-259">**注意**：電腦名稱必須是完整網域名稱 (FQDN)。</span><span class="sxs-lookup"><span data-stu-id="bf786-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="bf786-260">系統管理員會定義受限制的工作階段設定或 Runspace，也就是終端使用者可以執行之一組有限的 Cmdlet 和工作。</span><span class="sxs-lookup"><span data-stu-id="bf786-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="bf786-261">定義受限制的 Runspace 可防止使用者存取不在允許的 Windows PowerShell® Runspace 中的其他電腦，因此提供更安全的連線。</span><span class="sxs-lookup"><span data-stu-id="bf786-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="bf786-262">如需工作階段設定的詳細資訊，請參閱 [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) 或[安裝和使用 Windows PowerShell Web 存取](../install-and-use-windows-powershell-web-access.md)。</span><span class="sxs-lookup"><span data-stu-id="bf786-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="bf786-263">範例 2</span><span class="sxs-lookup"><span data-stu-id="bf786-263">EXAMPLE 2</span></span>

<span data-ttu-id="bf786-264">此範例會授權名為 `contoso\user1`、`contoso\user2` 和 `contoso\user3` 之使用者群組中的使用者，存取 *srv2* 上的預設 Windows PowerShell 工作階段設定 `Microsoft.PowerShell`。</span><span class="sxs-lookup"><span data-stu-id="bf786-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named `contoso\user1`, `contoso\user2`, and `contoso\user3`.</span></span> <span data-ttu-id="bf786-265">此 Cmdlet 會建立三個規則 (一人一個)。</span><span class="sxs-lookup"><span data-stu-id="bf786-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="bf786-266">範例 3</span><span class="sxs-lookup"><span data-stu-id="bf786-266">EXAMPLE 3</span></span>

<span data-ttu-id="bf786-267">此範例示範如何透過管線輸入使用者名稱值。</span><span class="sxs-lookup"><span data-stu-id="bf786-267">This example illustrates how to input user name values via the pipeline.</span></span>

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="bf786-268">範例 4</span><span class="sxs-lookup"><span data-stu-id="bf786-268">EXAMPLE 4</span></span>

<span data-ttu-id="bf786-269">此範例示範所有參數如何依屬性名稱採用來自管線的值。</span><span class="sxs-lookup"><span data-stu-id="bf786-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="bf786-270">範例 5</span><span class="sxs-lookup"><span data-stu-id="bf786-270">EXAMPLE 5</span></span>

<span data-ttu-id="bf786-271">此範例會新增規則，允許名為 `PswaServer\ChrisLocal` 的本機使用者存取名為 **srv1.contoso.com** 的伺服器。</span><span class="sxs-lookup"><span data-stu-id="bf786-271">This example adds a rule to allow the local user named `PswaServer\ChrisLocal` access to the server named **srv1.contoso.com**.</span></span>

<span data-ttu-id="bf786-272">此範例描述閘道位於工作群組且目的地電腦位於網域的案例。</span><span class="sxs-lookup"><span data-stu-id="bf786-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="bf786-273">授權規則適用於閘道上的本機使用者。</span><span class="sxs-lookup"><span data-stu-id="bf786-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="bf786-274">在 Windows PowerShell Web 存取登入頁面上，若要成功驗證，使用者必須提供 [選用連線設定] 區域中的第二組認證。</span><span class="sxs-lookup"><span data-stu-id="bf786-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="bf786-275">閘道伺服器會使用這組額外的認證，在目的地電腦 (名為 *srv1.contoso.com* 的伺服器) 上驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="bf786-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````powershell
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="bf786-276">範例 6</span><span class="sxs-lookup"><span data-stu-id="bf786-276">EXAMPLE 6</span></span>

<span data-ttu-id="bf786-277">此範例允許所有使用者存取所有電腦上的所有端點。</span><span class="sxs-lookup"><span data-stu-id="bf786-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="bf786-278">這基本上就是關閉授權規則。\\</span><span class="sxs-lookup"><span data-stu-id="bf786-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="bf786-279">**注意**：不建議在有安全性顧慮的部署中使用萬用字元 `*`，只有在測試環境或不需要嚴格安全性的部署中才應考慮使用。</span><span class="sxs-lookup"><span data-stu-id="bf786-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="bf786-280">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf786-280">See Also</span></span>

<span data-ttu-id="bf786-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="bf786-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>

<span data-ttu-id="bf786-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="bf786-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>

<span data-ttu-id="bf786-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="bf786-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>

<span data-ttu-id="bf786-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="bf786-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>

[<span data-ttu-id="bf786-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="bf786-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[<span data-ttu-id="bf786-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="bf786-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[<span data-ttu-id="bf786-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="bf786-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)