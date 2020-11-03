---
description: 本主題說明所有 Windows PowerShell 工作流程命令都有效的參數。 由於 Windows PowerShell 引擎會將它們新增至工作流程，因此您可以在任何工作流程上使用這些參數，而且這些參數會在您撰寫的工作流程上自動啟用。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflowcommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WorkflowCommonParameters
ms.openlocfilehash: 386200475c1dab9735921edd60abbde20ee354c4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207215"
---
# <a name="about-workflowcommonparameters"></a><span data-ttu-id="c1fb3-105">關於 WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="c1fb3-105">About WorkflowCommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="c1fb3-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="c1fb3-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="c1fb3-107">本主題說明所有 Windows PowerShell 工作流程命令都有效的參數。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-107">This topic describes the parameters that are valid on all Windows PowerShell workflow commands.</span></span> <span data-ttu-id="c1fb3-108">由於 Windows PowerShell 引擎會將它們新增至工作流程，因此您可以在任何工作流程上使用這些參數，而且這些參數會在您撰寫的工作流程上自動啟用。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-108">Because the Windows PowerShell engine adds them to workflows, you can use these parameters on any workflow and they are automatically enabled on the workflows that you author.</span></span>

## <a name="long-description"></a><span data-ttu-id="c1fb3-109">詳細描述</span><span class="sxs-lookup"><span data-stu-id="c1fb3-109">LONG DESCRIPTION</span></span>

<span data-ttu-id="c1fb3-110">Windows PowerShell 工作流程一般參數是一組 Cmdlet 參數，可搭配所有 Windows PowerShell 工作流程和活動使用。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-110">Windows PowerShell Workflow common parameters are a set of cmdlet parameters that you can use with all Windows PowerShell workflows and activities.</span></span> <span data-ttu-id="c1fb3-111">它們是由 Windows PowerShell 工作流程引擎新增，而不是由工作流程作者加入，而且會自動提供給工作流程和活動使用。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-111">They are added by the Windows PowerShell Workflow engine, not by the workflow author, and they are automatically available on workflows and activities.</span></span> <span data-ttu-id="c1fb3-112">不過，嵌套三層級深度的工作流程不支援任何一般參數，包括工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-112">However, workflows that are nested three levels deep do not support any common parameters, including workflow common parameters.</span></span>

<span data-ttu-id="c1fb3-113">所有工作流程參數都是選擇性的，且命名 (不是位置) 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-113">All workflow parameters are optional and named (not positional).</span></span> <span data-ttu-id="c1fb3-114">它們不會從管線取得輸入。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-114">They do not take input from the pipeline.</span></span>

<span data-ttu-id="c1fb3-115">大部分的工作流程一般參數都有 PS 前置詞，例如 `PSComputerName` 和 `PSCredential` 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-115">Most of the workflow common parameters have a PS prefix, such as `PSComputerName` and `PSCredential`.</span></span> <span data-ttu-id="c1fb3-116">以 PS 為首碼的參數會設定目的電腦的連接和執行環境，也稱為「遠端節點」。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-116">The PS-prefixed parameters configure the connection and the execution environment for the target computers, also known as "remote nodes."</span></span>

<span data-ttu-id="c1fb3-117">許多工作流程一般參數（例如 `PSAllowRedirection` 和 `AsJob` ）都有類似于 Windows PowerShell 遠端處理和背景工作中使用之參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-117">Many of the workflow common parameters, such as `PSAllowRedirection` and `AsJob`, have names that are similar to parameters used in Windows PowerShell remoting and background jobs.</span></span> <span data-ttu-id="c1fb3-118">這些參數的運作方式與類似命名的遠端和作業參數相同，因此您可以使用在遠端處理和作業中所開發的知識來管理工作流程。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-118">These parameters work in the same way as the similarly-named remoting and job parameters, so you can use the knowledge that you developed in remoting and jobs to manage workflows.</span></span>

<span data-ttu-id="c1fb3-119">工作流程會在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-119">Workflows are introduced in Windows PowerShell 3.0.</span></span>

### <a name="parameter-descriptions"></a><span data-ttu-id="c1fb3-120">參數描述</span><span class="sxs-lookup"><span data-stu-id="c1fb3-120">PARAMETER DESCRIPTIONS</span></span>

<span data-ttu-id="c1fb3-121">本節說明工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-121">This section describes the workflow common parameters.</span></span>

#### <a name="-asjob-switchparameter"></a><span data-ttu-id="c1fb3-122">-AsJob \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-122">-AsJob \<SwitchParameter\></span></span>

<span data-ttu-id="c1fb3-123">以工作流程工作的形式執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-123">Runs the workflow as a workflow job.</span></span> <span data-ttu-id="c1fb3-124">Workflow 命令會立即傳回代表父作業的物件。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-124">The workflow command immediately returns an object that represents a parent job.</span></span> <span data-ttu-id="c1fb3-125">父工作包含在每部目的電腦上執行的子工作。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-125">The parent job contains the child jobs that are running on each of the target computers.</span></span> <span data-ttu-id="c1fb3-126">若要管理工作，請使用各項 Job Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-126">To manage the job, use the Job cmdlets.</span></span> <span data-ttu-id="c1fb3-127">若要取得工作結果，請使用 [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job)。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-127">To get the job results, use [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job).</span></span>

#### <a name="-jobname-string"></a><span data-ttu-id="c1fb3-128">-JobName \<String\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-128">-JobName \<String\></span></span>

<span data-ttu-id="c1fb3-129">指定工作流程工作的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-129">Specifies a friendly name for the workflow job.</span></span> <span data-ttu-id="c1fb3-130">工作預設會命名為 "Job\<n\>"，其中 \<n\> 是序號。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-130">By default, jobs are named "Job\<n\>", where \<n\> is an ordinal number.</span></span>

<span data-ttu-id="c1fb3-131">如果您在工作流程命令中使用 JobName 參數，則工作流程會以工作的形式執行，而且即使您未在命令中包含參數，工作流程命令也會傳回工作物件 `AsJob` 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-131">If you use the JobName parameter in a workflow command, the workflow is run as a job and the workflow command returns a job object, even if you do not include the `AsJob` parameter in the command.</span></span>

<span data-ttu-id="c1fb3-132">如需 Windows PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-132">For more information about Windows PowerShell background jobs, see [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

#### <a name="-psallowredirection-switchparameter"></a><span data-ttu-id="c1fb3-133">-PSAllowRedirection \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-133">-PSAllowRedirection \<SwitchParameter\></span></span>

<span data-ttu-id="c1fb3-134">允許將連接重新導向至目的電腦。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-134">Allows redirection of the connection to the target computers.</span></span>

<span data-ttu-id="c1fb3-135">當您使用 `PSConnectionURI` 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-135">When you use the `PSConnectionURI` parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="c1fb3-136">根據預設，Windows PowerShell 不會重新導向連線，但是您可以使用 `PSAllowRedirection` 參數來允許將連接重新導向至目的電腦。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-136">By default, Windows PowerShell does not redirect connections, but you can use the `PSAllowRedirection` parameter to allow redirection of the connection to the target computer.</span></span>

<span data-ttu-id="c1fb3-137">您也可以藉由設定 `MaximumConnectionRedirectionCount` 喜好設定變數的屬性 `$PSSessionOption` ，或的值的屬性，限制連接重新導向的次數 `MaximumConnectionRedirectionCount` `PSSessionOption parameter` 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-137">You can also limit the number of times that the connection is redirected by setting the `MaximumConnectionRedirectionCount` property of the `$PSSessionOption` preference variable, or the `MaximumConnectionRedirectionCount` property of the value of the `PSSessionOption parameter`.</span></span> <span data-ttu-id="c1fb3-138">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-138">The default value is 5.</span></span> <span data-ttu-id="c1fb3-139">如需詳細資訊，請參閱 `PSSessionOption` 參數和 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)的說明。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-139">For more information, see the description of the `PSSessionOption` parameter and [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

#### <a name="-psapplicationname-string"></a><span data-ttu-id="c1fb3-140">-PSApplicationName \<String\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-140">-PSApplicationName \<String\></span></span>

<span data-ttu-id="c1fb3-141">指定連接 URI 用來連接目的電腦的應用程式名稱區段。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-141">Specifies the application name segment of the connection URI that is used to connect to the target computers.</span></span> <span data-ttu-id="c1fb3-142">當您未在命令中使用參數時，請使用這個參數來指定應用程式名稱 `ConnectionURI` 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-142">Use this parameter to specify the application name when you are not using the `ConnectionURI` parameter in the command.</span></span>

<span data-ttu-id="c1fb3-143">預設值是 `$PSSessionApplicationName` 本機電腦上喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-143">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="c1fb3-144">若未定義此喜好設定變數，則預設值是 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-144">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="c1fb3-145">這個值適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-145">This value is appropriate for most uses.</span></span> <span data-ttu-id="c1fb3-146">如需詳細資訊，請參閱 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-146">For more information, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="c1fb3-147">WinRM 服務會使用應用程式名稱來選取要用來為連線要求提供服務的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-147">The WinRM service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="c1fb3-148">此參數的值應該符合 `URLPrefix` 遠端電腦上接聽程式的屬性值。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-148">The value of this parameter should match the value of the `URLPrefix` property of a listener on the remote computer.</span></span>

#### <a name="-psauthentication-authenticationmechanism"></a><span data-ttu-id="c1fb3-149">-PSAuthentication \<AuthenticationMechanism\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-149">-PSAuthentication \<AuthenticationMechanism\></span></span>

<span data-ttu-id="c1fb3-150">指定在連接到目的電腦時，用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-150">Specifies the mechanism that is used to authenticate the user's credentials when connecting to the target computers.</span></span>

<span data-ttu-id="c1fb3-151">有效值為：</span><span class="sxs-lookup"><span data-stu-id="c1fb3-151">Valid values are:</span></span>

- <span data-ttu-id="c1fb3-152">**預設值**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-152">**Default**</span></span>
- <span data-ttu-id="c1fb3-153">**基本**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-153">**Basic**</span></span>
- <span data-ttu-id="c1fb3-154">**Credssp**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-154">**Credssp**</span></span>
- <span data-ttu-id="c1fb3-155">**Digest**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-155">**Digest**</span></span>
- <span data-ttu-id="c1fb3-156">**Kerberos**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-156">**Kerberos**</span></span>
- <span data-ttu-id="c1fb3-157">**洽談**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-157">**Negotiate**</span></span>
- <span data-ttu-id="c1fb3-158">**NegotiateWithImplicitCredential**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-158">**NegotiateWithImplicitCredential**</span></span>

<span data-ttu-id="c1fb3-159">預設值為 **Default** 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-159">The default value is **Default** .</span></span>

<span data-ttu-id="c1fb3-160">如需此參數值的詳細資訊，請參閱 `System.Management.Automation.Runspaces.AuthenticationMechanism` MSDN 中的列舉描述。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-160">For information about the values of this parameter, see the description of the `System.Management.Automation.Runspaces.AuthenticationMechanism` enumeration in MSDN.</span></span>

> [!WARNING]
> <span data-ttu-id="c1fb3-161">使用者認證會傳遞至要驗證之遠端電腦的「認證安全性服務提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-161">Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="c1fb3-162">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-162">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="c1fb3-163">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-163">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

#### <a name="-psauthenticationlevel-authenticationlevel"></a><span data-ttu-id="c1fb3-164">-PSAuthenticationLevel \<AuthenticationLevel\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-164">-PSAuthenticationLevel \<AuthenticationLevel\></span></span>

<span data-ttu-id="c1fb3-165">指定與目的電腦之連接的驗證層級。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-165">Specifies the authentication level for the connections to the target computers.</span></span>
<span data-ttu-id="c1fb3-166">預設值為 **Default** 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-166">The default value is **Default** .</span></span>

<span data-ttu-id="c1fb3-167">有效值為：</span><span class="sxs-lookup"><span data-stu-id="c1fb3-167">Valid values are:</span></span>

|<span data-ttu-id="c1fb3-168">Name</span><span class="sxs-lookup"><span data-stu-id="c1fb3-168">Name</span></span> |<span data-ttu-id="c1fb3-169">描述</span><span class="sxs-lookup"><span data-stu-id="c1fb3-169">Description</span></span> |
|---------|---------|
|<span data-ttu-id="c1fb3-170">**未變更**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-170">**Unchanged**</span></span> | <span data-ttu-id="c1fb3-171">驗證等級與前一個命令相同。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-171">The authentication level is the same as the previous command.</span></span> |
|<span data-ttu-id="c1fb3-172">**預設值**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-172">**Default**</span></span> | <span data-ttu-id="c1fb3-173">Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-173">Windows Authentication.</span></span> |
|<span data-ttu-id="c1fb3-174">**無**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-174">**None**</span></span> | <span data-ttu-id="c1fb3-175">沒有 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-175">No COM authentication.</span></span>   |
|<span data-ttu-id="c1fb3-176">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-176">**Connect**</span></span> | <span data-ttu-id="c1fb3-177">連接層級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-177">Connect-level COM authentication.</span></span>|
|<span data-ttu-id="c1fb3-178">**呼叫**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-178">**Call**</span></span> | <span data-ttu-id="c1fb3-179">呼叫層級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-179">Call-level COM authentication.</span></span>   |
|<span data-ttu-id="c1fb3-180">**包**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-180">**Packet**</span></span> | <span data-ttu-id="c1fb3-181">封包層級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-181">Packet-level COM authentication.</span></span>|
|<span data-ttu-id="c1fb3-182">**PacketIntegrity**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-182">**PacketIntegrity**</span></span> | <span data-ttu-id="c1fb3-183">封包完整性層級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-183">Packet Integrity-level COM authentication.</span></span>  |
|<span data-ttu-id="c1fb3-184">**PacketPrivacy**</span><span class="sxs-lookup"><span data-stu-id="c1fb3-184">**PacketPrivacy**</span></span> | <span data-ttu-id="c1fb3-185">封包隱私權層級 COM 驗證。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-185">Packet Privacy-level COM authentication.</span></span> |

#### <a name="-pscertificatethumbprint-string"></a><span data-ttu-id="c1fb3-186">-PSCertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-186">-PSCertificateThumbprint \<String\></span></span>

<span data-ttu-id="c1fb3-187">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-187">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="c1fb3-188">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-188">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="c1fb3-189">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-189">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="c1fb3-190">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-190">They can only be mapped to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="c1fb3-191">若要取得憑證，請使用 [Get 專案](xref:Microsoft.PowerShell.Management.Get-Item) 或 [get-childitem] (。/../Microsoft.PowerShell.Management/Get-Childitem.md Windows PowerShell Cert：磁片磁碟機中的) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-191">To get a certificate, use the [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) or [Get-ChildItem] (../../Microsoft.PowerShell.Management/Get-Childitem.md) cmdlets in the Windows PowerShell Cert: drive.</span></span>

#### <a name="-pscomputername-string"></a><span data-ttu-id="c1fb3-192">-PSComputerName \<String[]\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-192">-PSComputerName \<String[]\></span></span>

<span data-ttu-id="c1fb3-193">指定屬於工作流程目標節點的電腦清單。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-193">Specifies the list of computers that are the target nodes of the workflow.</span></span>
<span data-ttu-id="c1fb3-194">工作流程中的命令或活動會在使用此參數指定的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-194">Commands or activities in a workflow are run on the computers that are specified by using this parameter.</span></span> <span data-ttu-id="c1fb3-195">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-195">The default is the local computer.</span></span>

<span data-ttu-id="c1fb3-196">請輸入 NETBIOS 名稱、IP 位址或是一部或多部電腦的完整網域名稱 (以逗號分隔的清單方式)。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-196">Type the NETBIOS name, IP address, or fully-qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="c1fb3-197">若要指定本機電腦，請輸入電腦名稱、"localhost" 或句點 (.)。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-197">To specify the local computer, type the computer name, "localhost", or a dot (.).</span></span>

<span data-ttu-id="c1fb3-198">若要在參數值中包含本機電腦 `PSComputerName` ，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-198">To include the local computer in the value of the `PSComputerName` parameter, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="c1fb3-199">如果從命令省略此參數，或它的值為 `$null` 或空字串，則工作流程目標是本機電腦，而且不會使用 Windows PowerShell 遠端處理來執行命令。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-199">If this parameter is omitted from the command, or it value is `$null` or an empty string, the workflow target is the local computer and Windows PowerShell remoting is not used to run the command.</span></span>

<span data-ttu-id="c1fb3-200">若要在參數的值中使用 IP 位址 `ComputerName` ，命令必須包含 `PSCredential` 參數。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-200">To use an IP address in the value of the `ComputerName` parameter, the command must include the `PSCredential` parameter.</span></span> <span data-ttu-id="c1fb3-201">此外，必須將電腦設定為使用 HTTPS 傳輸，或必須在本機電腦的 WinRM TrustedHosts 清單中包含遠端電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-201">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="c1fb3-202">如需將電腦名稱稱新增到 TrustedHosts 清單的指示，請參閱 [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)中的「 *如何將電腦新增到信任的主機清單* 」。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-202">For instructions for adding a computer name to the TrustedHosts list, see *"How to Add a Computer to the Trusted Host List"* in [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span></span>

#### <a name="-psconfigurationname-string"></a><span data-ttu-id="c1fb3-203">-PSConfigurationName \<String\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-203">-PSConfigurationName \<String\></span></span>

<span data-ttu-id="c1fb3-204">指定用來在目的電腦上設定會話的會話設定。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-204">Specifies the session configurations that are used to configure sessions on the target computers.</span></span> <span data-ttu-id="c1fb3-205">請在目的電腦上輸入會話設定， (不是工作流程伺服器電腦) 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-205">Enter a session configuration on the target computers (not the workflow server computer).</span></span> <span data-ttu-id="c1fb3-206">預設為 `Microsoft.PowerShell.Workflow`。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-206">The default is `Microsoft.PowerShell.Workflow`.</span></span>

#### <a name="-psconnectionretrycount-uint"></a><span data-ttu-id="c1fb3-207">-PSConnectionRetryCount \<UInt\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-207">-PSConnectionRetryCount \<UInt\></span></span>

<span data-ttu-id="c1fb3-208">指定第一次連線嘗試失敗時，嘗試連接至每部目的電腦的次數上限。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-208">Specifies the maximum number of attempts to connect to each target computer if the first connection attempt fails.</span></span> <span data-ttu-id="c1fb3-209">輸入介於1和 4294967295 (UInt) 之間的數位。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-209">Enter a number between 1 and 4,294,967,295 (UInt.MaxValue).</span></span> <span data-ttu-id="c1fb3-210">預設值為零 (0) 表示無重試嘗試。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-210">The default value, zero (0), represents no retry attempts.</span></span>

#### <a name="-psconnectionretryintervalsec-uint"></a><span data-ttu-id="c1fb3-211">-PSConnectionRetryIntervalSec \<UInt\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-211">-PSConnectionRetryIntervalSec \<UInt\></span></span>

<span data-ttu-id="c1fb3-212">指定連接重試嘗試之間的延遲（以秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-212">Specifies the delay between connection retry attempts in seconds.</span></span> <span data-ttu-id="c1fb3-213">預設值為零 (0)。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-213">The default value is zero (0).</span></span> <span data-ttu-id="c1fb3-214">只有當 PSConnectionRetryCount 的值至少為1時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-214">This parameter is valid only when the value of PSConnectionRetryCount is at least 1.</span></span>

#### <a name="-psconnectionuri-systemuri"></a><span data-ttu-id="c1fb3-215">-PSConnectionURI \<System.Uri\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-215">-PSConnectionURI \<System.Uri\></span></span>

<span data-ttu-id="c1fb3-216">指定 (URI) 的統一資源識別項，以定義目的電腦上工作流程的連接端點。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-216">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint for the workflow on the target computer.</span></span> <span data-ttu-id="c1fb3-217">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-217">The URI must be fully qualified.</span></span>

<span data-ttu-id="c1fb3-218">這個字串的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="c1fb3-218">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="c1fb3-219">預設值是 `http://localhost:5985/WSMAN`。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-219">The default value is `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="c1fb3-220">如果您未指定 `PSConnectionURI` ，則可以使用 `PSUseSSL` 、 `PSComputerName` 、 `PSPort` 和 `PSApplicationName` 參數來指定 `PSConnectionURI` 值。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-220">If you do not specify a `PSConnectionURI`, you can use the `PSUseSSL`, `PSComputerName`, `PSPort`, and `PSApplicationName` parameters to specify the `PSConnectionURI` values.</span></span>

<span data-ttu-id="c1fb3-221">URI 的傳輸區段有效值為 **HTTP** 和 **HTTPS** 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-221">Valid values for the Transport segment of the URI are **HTTP** and **HTTPS** .</span></span>
<span data-ttu-id="c1fb3-222">若指定含傳輸區段的連線 URI，但未指定連接埠，將會以標準連接埠 80 (適用於 HTTP) 和 443 (適用於 HTTPS) 建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-222">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="c1fb3-223">若要使用預設連接埠於 Windows PowerShell 遠端功能，請為 HTTP 指定連接埠 5985，或是為 HTTPS 指定連接埠 5986。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-223">To use the default ports for Windows PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

#### <a name="-pscredential-pscredential"></a><span data-ttu-id="c1fb3-224">-PSCredential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-224">-PSCredential \<PSCredential\></span></span>

<span data-ttu-id="c1fb3-225">指定具有在目的電腦上執行工作流程之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-225">Specifies a user account that has permission to run a workflow on the target computer.</span></span> <span data-ttu-id="c1fb3-226">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-226">The default is the current user.</span></span> <span data-ttu-id="c1fb3-227">只有當命令中包含 PSComputerName 參數時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-227">This parameter is valid only when the PSComputerName parameter is included in the command.</span></span>

<span data-ttu-id="c1fb3-228">輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入包含物件的變數 `PSCredential` ，例如 Cmdlet 所傳回的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-228">Type a user name, such as "User01" or "Domain01\User01", or enter a variable that contains a `PSCredential` object, such as one that the `Get-Credential` cmdlet returns.</span></span> <span data-ttu-id="c1fb3-229">若您只輸入使用者名稱，將會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-229">If you enter only a user name, you will be prompted for a password.</span></span>

#### <a name="-pselapsedtimeoutsec-uint32"></a><span data-ttu-id="c1fb3-230">-PSElapsedTimeoutSec \<UInt32\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-230">-PSElapsedTimeoutSec \<UInt32\></span></span>

<span data-ttu-id="c1fb3-231">決定在系統中維護工作流程和所有相關資源的時間長度。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-231">Determines how long the workflow and all related resources are maintained in the system.</span></span> <span data-ttu-id="c1fb3-232">當超時時間過期時，即使工作流程仍在處理中，也會將其刪除。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-232">When the timeout expires, the workflow is deleted, even if it is still processing.</span></span> <span data-ttu-id="c1fb3-233">請輸入介於10到4294967295之間的值。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-233">Enter a value between 10 and 4,294,967,295.</span></span> <span data-ttu-id="c1fb3-234">預設值 0 (零) 表示沒有經過的超時時間。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-234">The default value, 0 (zero), means that there is no elapsed timeout.</span></span>

#### <a name="-psparametercollection-hashtable"></a><span data-ttu-id="c1fb3-235">-PSParameterCollection \<Hashtable[]\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-235">-PSParameterCollection \<Hashtable[]\></span></span>

<span data-ttu-id="c1fb3-236">針對不同的目的電腦指定不同的工作流程一般參數值。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-236">Specifies different workflow common parameter values for different target computers.</span></span>

<span data-ttu-id="c1fb3-237">輸入以逗號分隔的雜湊表清單，其中每一部目的電腦各有一個雜湊表。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-237">Enter a comma-separated list of hash tables with one hash table for each target computer.</span></span> <span data-ttu-id="c1fb3-238">在每個雜湊表中，第一個索引鍵是， `PSComputerName` 而它的值是目的電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-238">In each hash table, the first key is `PSComputerName` and its value is the name of the target computer.</span></span> <span data-ttu-id="c1fb3-239">電腦名稱稱中允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-239">Wildcard characters are permitted in the computer name.</span></span> <span data-ttu-id="c1fb3-240">針對雜湊表中其餘的索引鍵，索引鍵是參數名稱，而值是參數值。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-240">For the remaining keys in the hash table, the key is the parameter name and the value is the parameter value.</span></span>

<span data-ttu-id="c1fb3-241">例如：</span><span class="sxs-lookup"><span data-stu-id="c1fb3-241">For example:</span></span>

```powershell
-PSParameterCollection @{PSComputerName="*"; PSElapsedTimeoutSec=20},
@{PSComputerName="Server02"},
@{PSComputerName="Server03"},
@{PSComputerName="Server01"; PSElapsedTimeoutSec=10}
```

<span data-ttu-id="c1fb3-242">在上述範例中，所有的連接都會有20秒的預設 PSElapsedTimeoutSec，但是 Server01 會指定自己的10秒超時，來覆寫預設值。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-242">In the above example, all connections will have a default PSElapsedTimeoutSec of 20 seconds, except for Server01 which overrides the default value by specifying its own timeout of 10 seconds.</span></span>

#### <a name="-pspersist-boolean"></a><span data-ttu-id="c1fb3-243">-PSPersist \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-243">-PSPersist \<Boolean\></span></span>

<span data-ttu-id="c1fb3-244">除了工作流程中指定的檢查點之外，還會將檢查點加入至工作流程。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-244">Adds checkpoints to the workflow, in addition to any checkpoints that are specified in the workflow.</span></span>

<span data-ttu-id="c1fb3-245">此參數無法隱藏工作流程中的檢查點，例如使用 `PSPersist` 活動一般參數、 `Checkpoint-Workflow` 活動或變數所指定的檢查點 `$PSPersistPreference` 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-245">This parameter cannot suppress the checkpoints in a workflow, such as those specified by using the `PSPersist` activity common parameter, the `Checkpoint-Workflow` activity, or the `$PSPersistPreference` variable.</span></span>

<span data-ttu-id="c1fb3-246">「檢查點」或「持續點」是工作流程執行時所捕捉的工作流程狀態和資料的快照集，而且會儲存到磁片或 SQL 資料庫中的持續性存放區。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-246">A "checkpoint" or "persistence point" is a snapshot of the workflow state and data that is captured while the workflow runs and is saved to a persistence store on disk or in a SQL database.</span></span> <span data-ttu-id="c1fb3-247">Windows PowerShell 工作流程使用儲存的資料，從上一個持續點繼續暫停或中斷的工作流程，而不是重新開機工作流程。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-247">Windows PowerShell Workflow uses the saved data to resume a suspended or interrupted workflow from the last persistence point, rather than to restart the workflow.</span></span>

<span data-ttu-id="c1fb3-248">有效值：</span><span class="sxs-lookup"><span data-stu-id="c1fb3-248">Valid values:</span></span>

- <span data-ttu-id="c1fb3-249"> ( *預設* ) 如果您省略此參數，則除了工作流程中指定的任何檢查點之外，還會將檢查點加入至工作流程的開頭和結尾。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-249">( *Default* ) If you omit this parameter, a checkpoint is added to the beginning and end of the workflow, in addition to any checkpoints that are specified in the workflow.</span></span>

- <span data-ttu-id="c1fb3-250">`$True`.</span><span class="sxs-lookup"><span data-stu-id="c1fb3-250">`$True`.</span></span> <span data-ttu-id="c1fb3-251">將檢查點加入至工作流程的開頭和結尾，以及在每個活動之後的檢查點，以及工作流程中指定的任何檢查點。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-251">Adds a checkpoint to the beginning and end of the workflow and a checkpoint after each activity, in addition to any checkpoints that are specified in the workflow.</span></span>

- <span data-ttu-id="c1fb3-252">`$False`.</span><span class="sxs-lookup"><span data-stu-id="c1fb3-252">`$False`.</span></span> <span data-ttu-id="c1fb3-253">未新增任何檢查點。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-253">No checkpoints are added.</span></span> <span data-ttu-id="c1fb3-254">只有在工作流程中指定時，才會採取檢查點。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-254">Checkpoints are taken only when specified in the workflow.</span></span>

#### <a name="-psport-int32"></a><span data-ttu-id="c1fb3-255">-PSPort \<Int32\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-255">-PSPort \<Int32\></span></span>

<span data-ttu-id="c1fb3-256">指定目的電腦上的網路埠。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-256">Specifies the network port on the target computers.</span></span> <span data-ttu-id="c1fb3-257">預設連接埠是 5985 (用於 HTTP 的 WinRM 連接埠) 和 5986 (用於 HTTPS 的 WinRM 連接埠)。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-257">The default ports are 5985 (the WinRM port for HTTP) and 5986 (the WinRM port for HTTPS).</span></span>

<span data-ttu-id="c1fb3-258">除非您必須這樣做，否則請勿使用 PSPort 參數。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-258">Do not use the PSPort parameter unless you must.</span></span> <span data-ttu-id="c1fb3-259">命令中設定的埠會套用到命令執行所在的所有電腦或會話。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-259">The port set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="c1fb3-260">替代的連接埠設定可能使得命令無法在全部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-260">An alternate port setting might prevent the command from running on all computers.</span></span> <span data-ttu-id="c1fb3-261">使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-261">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span>

#### <a name="-psprivatemetadata-hashtable"></a><span data-ttu-id="c1fb3-262">-PSPrivateMetadata \<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-262">-PSPrivateMetadata \<Hashtable\></span></span>

<span data-ttu-id="c1fb3-263">提供自訂的資訊給工作流程工作。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-263">Provides customized information to workflow jobs.</span></span> <span data-ttu-id="c1fb3-264">輸入雜湊表。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-264">Enter a hash table.</span></span> <span data-ttu-id="c1fb3-265">每個工作流程都會自訂索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-265">The keys and values are customized for each workflow.</span></span> <span data-ttu-id="c1fb3-266">如需工作流程私用中繼資料的詳細資訊，請參閱工作流程的說明主題。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-266">For information about the private metadata of a workflow, see the help topic for the workflow.</span></span>

<span data-ttu-id="c1fb3-267">Windows PowerShell 工作流程引擎不會處理這個參數。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-267">This parameter is not processed by the Windows PowerShell Workflow engine.</span></span>
<span data-ttu-id="c1fb3-268">相反地，引擎會直接將雜湊表傳遞給工作流程。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-268">Instead, the engine passes the hash table directly to the workflow.</span></span>

#### <a name="-psrunningtimeoutsec-uint32"></a><span data-ttu-id="c1fb3-269">-PSRunningTimeoutSec \<UInt32\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-269">-PSRunningTimeoutSec \<UInt32\></span></span>

<span data-ttu-id="c1fb3-270">指定工作流程的執行時間（以秒為單位），不包括工作流程暫止的任何時間。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-270">Specifies the running time of the workflow in seconds, excluding any time that the workflow is suspended.</span></span> <span data-ttu-id="c1fb3-271">如果工作流程執行在時間過期時未完成，Windows PowerShell 工作流程引擎會強制停止工作流程的執行。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-271">If workflow execution is not complete when the time expires, the Windows PowerShell Workflow engine forcibly stops the execution of the workflow.</span></span>

#### <a name="-pssessionoption-pssessionoption"></a><span data-ttu-id="c1fb3-272">-PSSessionOption \<PSSessionOption\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-272">-PSSessionOption \<PSSessionOption\></span></span>

<span data-ttu-id="c1fb3-273">將會話的 advanced 選項設定為目的電腦。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-273">Sets advanced options for the sessions to the target computers.</span></span> <span data-ttu-id="c1fb3-274">輸入 `PSSessionOption` 您使用 Cmdlet 建立的物件，例如您所建立的物件 `New-PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-274">Enter a `PSSessionOption` object, such as one that you create by using the `New-PSSessionOption` cmdlet.</span></span>

<span data-ttu-id="c1fb3-275">會話選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-275">The default values for the session options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="c1fb3-276">否則，會話會使用會話設定中指定的值。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-276">Otherwise, the session uses the values specified in the session configuration.</span></span>

<span data-ttu-id="c1fb3-277">如需會話選項的描述（包括預設值），請參閱 Cmdlet ( 的說明主題 `New-PSSessionOption` 。/../Microsoft.PowerShell.Core/New-PSSessionOption.md) 。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-277">For a description of the session options, including the default values, see the help topic for the `New-PSSessionOption` cmdlet (../../Microsoft.PowerShell.Core/New-PSSessionOption.md).</span></span> <span data-ttu-id="c1fb3-278">如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-278">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

#### <a name="-psusessl-switchparameter"></a><span data-ttu-id="c1fb3-279">-PSUseSSL \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="c1fb3-279">-PSUseSSL \<SwitchParameter\></span></span>

<span data-ttu-id="c1fb3-280">使用安全通訊端層 (SSL) 通訊協定來建立與目的電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-280">Uses the Secure Sockets Layer (SSL) protocol to establish a connection to the target computer.</span></span> <span data-ttu-id="c1fb3-281">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-281">By default, SSL is not used.</span></span>

<span data-ttu-id="c1fb3-282">WS-Management 會加密透過網路傳輸的所有 Windows PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-282">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="c1fb3-283">UseSSL 是額外的保護，可透過 HTTPS (而非 HTTP) 傳送資料。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-283">UseSSL is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span> <span data-ttu-id="c1fb3-284">若您使用此參數，但是命令所用的連接埠上無法使用 SSL，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="c1fb3-284">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1fb3-285">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1fb3-285">SEE ALSO</span></span>

- [<span data-ttu-id="c1fb3-286">about_ActivityCommonParameters</span><span class="sxs-lookup"><span data-stu-id="c1fb3-286">about_ActivityCommonParameters</span></span>](about_ActivityCommonParameters.md)
- [<span data-ttu-id="c1fb3-287">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="c1fb3-287">about_Workflows</span></span>](about_Workflows.md)
- [<span data-ttu-id="c1fb3-288">Invoke-AsWorkflow</span><span class="sxs-lookup"><span data-stu-id="c1fb3-288">Invoke-AsWorkflow</span></span>](xref:PSWorkflowUtility.Invoke-AsWorkflow)
- [<span data-ttu-id="c1fb3-289">New-PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="c1fb3-289">New-PSWorkflowExecutionOption</span></span>](xref:PSWorkflow.New-PSWorkflowExecutionOption)
- [<span data-ttu-id="c1fb3-290">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="c1fb3-290">New-PSWorkflowSession</span></span>](xref:PSWorkflow.New-PSWorkflowSession)
