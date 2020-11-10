---
description: 描述 Windows PowerShell 工作流程新增至活動的參數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_activitycommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_ActivityCommonParameters
ms.openlocfilehash: 93fdcdb9c5afe0b73e843baf2474ec7d3f96a6cf
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387799"
---
# <a name="about-activitycommonparameters"></a><span data-ttu-id="89064-104">關於 ActivityCommonParameters</span><span class="sxs-lookup"><span data-stu-id="89064-104">About ActivityCommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="89064-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="89064-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="89064-106">描述 Windows PowerShell 工作流程新增至活動的參數。</span><span class="sxs-lookup"><span data-stu-id="89064-106">Describes the parameters that Windows PowerShell Workflow adds to activities.</span></span>

## <a name="long-description"></a><span data-ttu-id="89064-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="89064-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="89064-108">Windows PowerShell 工作流程會將活動一般參數加入至衍生自 PSActivity 基類的活動。</span><span class="sxs-lookup"><span data-stu-id="89064-108">Windows PowerShell Workflow adds the activity common parameters to activities that are derived from the PSActivity base class.</span></span> <span data-ttu-id="89064-109">此類別包括 InlineScript 活動，以及實作為活動的 Windows PowerShell Cmdlet，例如 Get-Process 和 New-winevent。</span><span class="sxs-lookup"><span data-stu-id="89064-109">This category includes the InlineScript activity and Windows PowerShell cmdlets that are implemented as activities, such as Get-Process and Get-WinEvent.</span></span>

<span data-ttu-id="89064-110">活動一般參數在 Suspend-Workflow 和 Checkpoint-Workflow 活動上無效，並且不會加入至 Windows PowerShell 工作流程在 InlineScript 腳本區塊或類似活動中自動執行的 Cmdlet 或運算式。</span><span class="sxs-lookup"><span data-stu-id="89064-110">The activity common parameters are not valid on the Suspend-Workflow and Checkpoint-Workflow activities and they are not added to cmdlets or expressions that Windows PowerShell Workflow automatically runs in an InlineScript script block or similar activity.</span></span> <span data-ttu-id="89064-111">活動一般參數在 InlineScript 活動中可以使用，但在 InlineScript 指令碼區塊中的命令中無法使用。</span><span class="sxs-lookup"><span data-stu-id="89064-111">The activity common parameters are available on the InlineScript activity, but not on commands in the InlineScript script block.</span></span>

<span data-ttu-id="89064-112">數個活動一般參數也是工作流程一般參數或 Windows PowerShell 一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-112">Several of the activity common parameters are also workflow common parameters or Windows PowerShell common parameters.</span></span> <span data-ttu-id="89064-113">其他活動一般參數對活動是唯一的。</span><span class="sxs-lookup"><span data-stu-id="89064-113">Other activity common parameters are unique to activities.</span></span>

<span data-ttu-id="89064-114">如需工作流程一般參數的詳細資訊，請參閱 about_WorkflowCommonParameters。</span><span class="sxs-lookup"><span data-stu-id="89064-114">For information about the workflow common parameters, see about_WorkflowCommonParameters.</span></span> <span data-ttu-id="89064-115">如需 Windows PowerShell 一般參數的詳細資訊，請參閱 about_CommonParameters。</span><span class="sxs-lookup"><span data-stu-id="89064-115">For information about the Windows PowerShell common parameters, see about_CommonParameters.</span></span>

### <a name="list-of-activity-common-parameters"></a><span data-ttu-id="89064-116">活動一般參數的清單</span><span class="sxs-lookup"><span data-stu-id="89064-116">LIST OF ACTIVITY COMMON PARAMETERS</span></span>

```
AppendOutput                      PSDebug
Debug                             PSDisableSerialization
DisplayName                       PSDisableSerializationPreference
ErrorAction                       PSError
Input                             PSPersist
MergeErrorToOutput                PSPort
PSActionRetryCount                PSProgress
PSActionRetryIntervalSec          PSProgressMessage
PSActionRunningTimeoutSec         PSRemotingBehavior
PSApplicationName                 PSRequiredModules
PSAuthentication                  PSSessionOption
PSCertificateThumbprint           PSUseSSL
PSComputerName                    PSVerbose
PSConfigurationName               PSWarning
PSConnectionRetryCount            Result
PSConnectionRetryIntervalSec      UseDefaultInput
PSConnectionURI                   Verbose
PSCredential                      WarningAction
```

### <a name="parameter-descriptions"></a><span data-ttu-id="89064-117">參數描述</span><span class="sxs-lookup"><span data-stu-id="89064-117">PARAMETER DESCRIPTIONS</span></span>

<span data-ttu-id="89064-118">本章節描述活動一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-118">This section describes the activity common parameters.</span></span>

#### <a name="appendoutput-boolean"></a><span data-ttu-id="89064-119">AppendOutput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="89064-119">AppendOutput \<Boolean\></span></span>

<span data-ttu-id="89064-120">的值會 `$True` 將活動的輸出加入變數的值。</span><span class="sxs-lookup"><span data-stu-id="89064-120">A value of `$True` adds the output of the activity to the value of the variable.</span></span>
<span data-ttu-id="89064-121">的值 `$False` 沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="89064-121">A value of `$False` has no effect.</span></span> <span data-ttu-id="89064-122">根據預設，會將值指派給變數來取代變數值。</span><span class="sxs-lookup"><span data-stu-id="89064-122">By default, assigning a value to a variable replaces the variable value.</span></span>

<span data-ttu-id="89064-123">例如，下列命令會將處理常式物件新增至變數中的服務物件 `$x` 。</span><span class="sxs-lookup"><span data-stu-id="89064-123">For example, the following commands add a process object to the service object in the `$x` variable.</span></span>

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x = Get-Process -AppendOutput $true
}
```

<span data-ttu-id="89064-124">此參數是針對以 XAML 為基礎的工作流程所設計。</span><span class="sxs-lookup"><span data-stu-id="89064-124">This parameter is designed for XAML-based workflows.</span></span> <span data-ttu-id="89064-125">在腳本工作流程中，您也可以使用 + = 指派運算子將輸出新增至變數的值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="89064-125">In script workflows, you can also use the += assignment operator to add output to the value of a variable, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x += Get-Process
}
```

#### <a name="debug-switchparameter"></a><span data-ttu-id="89064-126">調試 \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="89064-126">Debug \<SwitchParameter\></span></span>

<span data-ttu-id="89064-127">顯示命令所執行之作業的程式設計人員層級詳細資料。</span><span class="sxs-lookup"><span data-stu-id="89064-127">Displays programmer-level detail about the operation performed by the command.</span></span>
<span data-ttu-id="89064-128">Debug 參數會覆寫目前命令之 $DebugPreference 變數的值。</span><span class="sxs-lookup"><span data-stu-id="89064-128">The Debug parameter overrides the value of the $DebugPreference variable for the current command.</span></span> <span data-ttu-id="89064-129">只有當命令產生調試訊息時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="89064-129">This parameter works only when the command generates debugging messages.</span></span> <span data-ttu-id="89064-130">此參數也是 Windows PowerShell 一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-130">This parameter is also a Windows PowerShell common parameter.</span></span>

#### <a name="displayname-string"></a><span data-ttu-id="89064-131">DisplayName \<String\></span><span class="sxs-lookup"><span data-stu-id="89064-131">DisplayName \<String\></span></span>

<span data-ttu-id="89064-132">指定活動的好記名稱。</span><span class="sxs-lookup"><span data-stu-id="89064-132">Specifies a friendly name for the activity.</span></span> <span data-ttu-id="89064-133">當工作流程執行時，以及在工作流程工作的進度屬性值中，DisplayName 值會出現在進度列中。</span><span class="sxs-lookup"><span data-stu-id="89064-133">The DisplayName value appears in the progress bar while the workflow runs and in the value of the Progress property of the workflow job.</span></span> <span data-ttu-id="89064-134">當命令中也包含 PSProgressMessage 參數時，進度列內容會顯示為 \<DisplayName\> ： \<PSProgressMessage\> format。</span><span class="sxs-lookup"><span data-stu-id="89064-134">When the PSProgressMessage parameter is also included in the command, the progress bar content appears in \<DisplayName\>:\<PSProgressMessage\> format.</span></span>

#### <a name="erroraction-actionpreference"></a><span data-ttu-id="89064-135">ErrorAction \<ActionPreference\></span><span class="sxs-lookup"><span data-stu-id="89064-135">ErrorAction \<ActionPreference\></span></span>

<span data-ttu-id="89064-136">決定活動如何回應來自命令的非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="89064-136">Determines how the activity responds to a non-terminating error from the command.</span></span> <span data-ttu-id="89064-137">它不會影響終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="89064-137">It has no effect on termination errors.</span></span> <span data-ttu-id="89064-138">此參數只適用于命令產生非終止錯誤，例如來自 Write-Error Cmdlet 的錯誤。</span><span class="sxs-lookup"><span data-stu-id="89064-138">This parameter works only when the command generates a non-terminating error, such as those from the Write-Error cmdlet.</span></span> <span data-ttu-id="89064-139">ErrorAction 參數會覆寫目前命令之 $ErrorActionPreference 變數的值。</span><span class="sxs-lookup"><span data-stu-id="89064-139">The ErrorAction parameter overrides the value of the $ErrorActionPreference variable for the current command.</span></span> <span data-ttu-id="89064-140">此參數也是 Windows PowerShell 一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-140">This parameter is also a Windows PowerShell common parameter.</span></span>

<span data-ttu-id="89064-141">有效值：</span><span class="sxs-lookup"><span data-stu-id="89064-141">Valid values:</span></span>

- <span data-ttu-id="89064-142">繼續。</span><span class="sxs-lookup"><span data-stu-id="89064-142">Continue.</span></span> <span data-ttu-id="89064-143">顯示錯誤訊息，並繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="89064-143">Displays the error message and continues executing the command.</span></span> <span data-ttu-id="89064-144">[繼續] 是預設值。</span><span class="sxs-lookup"><span data-stu-id="89064-144">"Continue" is the default value.</span></span>

- <span data-ttu-id="89064-145">忽略。</span><span class="sxs-lookup"><span data-stu-id="89064-145">Ignore.</span></span> <span data-ttu-id="89064-146">隱藏錯誤訊息，並繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="89064-146">Suppresses the error message and continues executing the command.</span></span>
  <span data-ttu-id="89064-147">不同于 SilentlyContinue，Ignore 不會將錯誤訊息加入 $Error 的自動變數中。</span><span class="sxs-lookup"><span data-stu-id="89064-147">Unlike SilentlyContinue, Ignore does not add the error message to the $Error automatic variable.</span></span> <span data-ttu-id="89064-148">忽略值是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="89064-148">The Ignore value is introduced in Windows PowerShell 3.0.</span></span>

- <span data-ttu-id="89064-149">詢問。</span><span class="sxs-lookup"><span data-stu-id="89064-149">Inquire.</span></span> <span data-ttu-id="89064-150">顯示錯誤訊息，並在繼續執行之前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="89064-150">Displays the error message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="89064-151">此值很少使用。</span><span class="sxs-lookup"><span data-stu-id="89064-151">This value is rarely used.</span></span>

- <span data-ttu-id="89064-152">擱置：</span><span class="sxs-lookup"><span data-stu-id="89064-152">Suspend.</span></span> <span data-ttu-id="89064-153">自動暫停工作流程工作，以允許進一步調查。</span><span class="sxs-lookup"><span data-stu-id="89064-153">Automatically suspends a workflow job to allow for further investigation.</span></span> <span data-ttu-id="89064-154">經過調查之後，即可繼續工作流程。</span><span class="sxs-lookup"><span data-stu-id="89064-154">After investigation, the workflow can be resumed.</span></span>

- <span data-ttu-id="89064-155">SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="89064-155">SilentlyContinue.</span></span> <span data-ttu-id="89064-156">隱藏錯誤訊息，並繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="89064-156">Suppresses the error message and continues executing the command.</span></span>

- <span data-ttu-id="89064-157">停止。</span><span class="sxs-lookup"><span data-stu-id="89064-157">Stop.</span></span> <span data-ttu-id="89064-158">顯示錯誤訊息，並停止執行命令。</span><span class="sxs-lookup"><span data-stu-id="89064-158">Displays the error message and stops executing the command.</span></span>

#### <a name="input-object"></a><span data-ttu-id="89064-159">輸入 \<Object[]\></span><span class="sxs-lookup"><span data-stu-id="89064-159">Input \<Object[]\></span></span>

<span data-ttu-id="89064-160">將物件集合提交給活動。</span><span class="sxs-lookup"><span data-stu-id="89064-160">Submits a collection of objects to an activity.</span></span> <span data-ttu-id="89064-161">這是使用管線，一次將物件傳給一個活動的替代方案。</span><span class="sxs-lookup"><span data-stu-id="89064-161">This is an alternative to piping objects to the activity one at a time.</span></span>

#### <a name="mergeerrortooutput-boolean"></a><span data-ttu-id="89064-162">MergeErrorToOutput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="89064-162">MergeErrorToOutput \<Boolean\></span></span>

<span data-ttu-id="89064-163">的值會 `$True` 將錯誤加入至輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="89064-163">A value of `$True` adds errors to the output stream.</span></span> <span data-ttu-id="89064-164">的值 `$False` 沒有作用。</span><span class="sxs-lookup"><span data-stu-id="89064-164">A value of `$False` has not effect.</span></span> <span data-ttu-id="89064-165">使用此參數搭配 Parallel 和 `ForEach -Parallel` 關鍵字，從單一集合的多個平行命令收集錯誤和輸出。</span><span class="sxs-lookup"><span data-stu-id="89064-165">Use this parameter with the Parallel and `ForEach -Parallel` keywords to collect errors and output from multiple parallel commands in a single collection.</span></span>

#### <a name="psactionretrycount-int32"></a><span data-ttu-id="89064-166">PSActionRetryCount \<Int32\></span><span class="sxs-lookup"><span data-stu-id="89064-166">PSActionRetryCount \<Int32\></span></span>

<span data-ttu-id="89064-167">若第一次嘗試失敗，則重複試著執行活動。</span><span class="sxs-lookup"><span data-stu-id="89064-167">Tries repeatedly to run the activity if the first attempt fails.</span></span> <span data-ttu-id="89064-168">預設值 0 不會重試。</span><span class="sxs-lookup"><span data-stu-id="89064-168">The default value, 0, does not retry.</span></span>

#### <a name="psactionretryintervalsec-int32"></a><span data-ttu-id="89064-169">PSActionRetryIntervalSec \<Int32\></span><span class="sxs-lookup"><span data-stu-id="89064-169">PSActionRetryIntervalSec \<Int32\></span></span>

<span data-ttu-id="89064-170">判斷動作的重試間隔，以秒為單位。</span><span class="sxs-lookup"><span data-stu-id="89064-170">Determines the interval between action retries in seconds.</span></span> <span data-ttu-id="89064-171">預設值為 0，立即重試動作。</span><span class="sxs-lookup"><span data-stu-id="89064-171">The default value, 0, retries the action immediately.</span></span> <span data-ttu-id="89064-172">只有當命令中也使用 PSActionRetryCount 參數時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="89064-172">This parameter is valid only when the PSActionRetryCount parameter is also used in the command.</span></span>

#### <a name="psactionrunningtimeoutsec-int32"></a><span data-ttu-id="89064-173">PSActionRunningTimeoutSec \<Int32\></span><span class="sxs-lookup"><span data-stu-id="89064-173">PSActionRunningTimeoutSec \<Int32\></span></span>

<span data-ttu-id="89064-174">決定每部目標電腦上活動的執行時間。</span><span class="sxs-lookup"><span data-stu-id="89064-174">Determines how long the activity can run on each target computer.</span></span> <span data-ttu-id="89064-175">如果活動未在超時時間過期之前完成，Windows PowerShell 工作流程會產生終止錯誤，並停止處理受影響之目的電腦上的工作流程。</span><span class="sxs-lookup"><span data-stu-id="89064-175">If the activity does not complete before the timeout expires, Windows PowerShell Workflow generates a terminating error and stops processing the workflow on the affected target computer.</span></span>

#### <a name="psallowredirection-boolean"></a><span data-ttu-id="89064-176">PSAllowRedirection \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="89064-176">PSAllowRedirection \<Boolean\></span></span>

<span data-ttu-id="89064-177">值為 $True 允許將連接重新導向至目的電腦。</span><span class="sxs-lookup"><span data-stu-id="89064-177">A value of $True allows redirection of the connection to the target computers.</span></span>
<span data-ttu-id="89064-178">$False 的值沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="89064-178">A value of $False has no effect.</span></span> <span data-ttu-id="89064-179">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-179">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="89064-180">當您使用 PSConnectionURI 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。</span><span class="sxs-lookup"><span data-stu-id="89064-180">When you use the PSConnectionURI parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="89064-181">根據預設，Windows PowerShell 不會重新導向連線，但是您可以使用 PSAllowRedirection 參數搭配 $True 值，以允許將連接重新導向至目的電腦。</span><span class="sxs-lookup"><span data-stu-id="89064-181">By default, Windows PowerShell does not redirect connections, but you can use the PSAllowRedirection parameter with a value of $True to allow redirection of the connection to the target computer.</span></span>

<span data-ttu-id="89064-182">您也可以藉由設定喜好設定變數的 MaximumConnectionRedirectionCount 屬性 `$PSSessionOption` ，或建立會話之 Cmdlet 的 SSessionOption 參數值的 MaximumConnectionRedirectionCount 屬性，來限制連接重新導向的次數。</span><span class="sxs-lookup"><span data-stu-id="89064-182">You can also limit the number of times that the connection is redirected by setting the MaximumConnectionRedirectionCount property of the `$PSSessionOption` preference variable, or the MaximumConnectionRedirectionCount property of the value of the SSessionOption parameter of cmdlets that create a session.</span></span> <span data-ttu-id="89064-183">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="89064-183">The default value is 5.</span></span>

#### <a name="psapplicationname-string"></a><span data-ttu-id="89064-184">PSApplicationName \<String\></span><span class="sxs-lookup"><span data-stu-id="89064-184">PSApplicationName \<String\></span></span>

<span data-ttu-id="89064-185">指定連接 URI 用來連接目的電腦的應用程式名稱區段。</span><span class="sxs-lookup"><span data-stu-id="89064-185">Specifies the application name segment of the connection URI that is used to connect to the target computers.</span></span> <span data-ttu-id="89064-186">當您沒有在命令中使用 ConnectionURI 參數時，請使用這個參數來指定應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="89064-186">Use this parameter to specify the application name when you are not using the ConnectionURI parameter in the command.</span></span> <span data-ttu-id="89064-187">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-187">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="89064-188">預設值是 `$PSSessionApplicationName` 目的電腦上的喜好設定變數值。</span><span class="sxs-lookup"><span data-stu-id="89064-188">The default value is the value of the `$PSSessionApplicationName` preference variable on the target computer.</span></span> <span data-ttu-id="89064-189">若未定義此喜好設定變數，則預設值是 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="89064-189">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="89064-190">這個值適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="89064-190">This value is appropriate for most uses.</span></span> <span data-ttu-id="89064-191">如需詳細資訊，請參閱 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="89064-191">For more information, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="89064-192">WinRM 服務會使用應用程式名稱來選取要用來為連線要求提供服務的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="89064-192">The WinRM service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="89064-193">此參數的值應該符合遠端電腦上接聽程式之 URLPrefix 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="89064-193">The value of this parameter should match the value of the URLPrefix property of a listener on the remote computer.</span></span>

#### <a name="psauthentication-authenticationmechanism"></a><span data-ttu-id="89064-194">PSAuthentication \<AuthenticationMechanism\></span><span class="sxs-lookup"><span data-stu-id="89064-194">PSAuthentication \<AuthenticationMechanism\></span></span>

<span data-ttu-id="89064-195">指定在連接到目的電腦時，用來驗證使用者認證的機制。</span><span class="sxs-lookup"><span data-stu-id="89064-195">Specifies the mechanism that is used to authenticate the user's credentials when connecting to the target computers.</span></span> <span data-ttu-id="89064-196">有效值為 Default、Basic、Credssp、Digest、Kerberos、Negotiate 與 NegotiateWithImplicitCredential。</span><span class="sxs-lookup"><span data-stu-id="89064-196">Valid values are Default, Basic, Credssp, Digest, Kerberos, Negotiate, and NegotiateWithImplicitCredential.</span></span> <span data-ttu-id="89064-197">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="89064-197">The default value is Default.</span></span> <span data-ttu-id="89064-198">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-198">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="89064-199">如需此參數值的詳細資訊，請參閱 PowerShell SDK 中 **AuthenticationMechanism** 列舉的說明。</span><span class="sxs-lookup"><span data-stu-id="89064-199">For information about the values of this parameter, see the description of the **System.Management.Automation.Runspaces.AuthenticationMechanism** enumeration in the PowerShell SDK.</span></span>

> [!WARNING]
> <span data-ttu-id="89064-200">使用者認證會傳遞至要驗證之遠端電腦的「認證安全性服務提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。</span><span class="sxs-lookup"><span data-stu-id="89064-200">Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="89064-201">此機制會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="89064-201">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="89064-202">若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="89064-202">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

#### <a name="pscertificatethumbprint-string"></a><span data-ttu-id="89064-203">PSCertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="89064-203">PSCertificateThumbprint \<String\></span></span>

<span data-ttu-id="89064-204">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="89064-204">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="89064-205">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="89064-205">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="89064-206">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-206">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="89064-207">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="89064-207">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="89064-208">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="89064-208">They can only be mapped to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="89064-209">若要取得憑證，請使用 Windows PowerShell Cert：磁片磁碟機中的 [get-Item](xref:Microsoft.PowerShell.Management.Get-Item) 或 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="89064-209">To get a certificate, use the [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) or [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) cmdlets in the Windows PowerShell Cert: drive.</span></span>

#### <a name="pscomputername-string"></a><span data-ttu-id="89064-210">PSComputerName \<String[]\></span><span class="sxs-lookup"><span data-stu-id="89064-210">PSComputerName \<String[]\></span></span>

<span data-ttu-id="89064-211">指定活動執行所在的目的電腦。</span><span class="sxs-lookup"><span data-stu-id="89064-211">Specifies the target computers on which the activity run.</span></span> <span data-ttu-id="89064-212">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="89064-212">The default is the local computer.</span></span> <span data-ttu-id="89064-213">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-213">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="89064-214">請輸入 NETBIOS 名稱、IP 位址或是一部或多部電腦的完整網域名稱 (以逗號分隔的清單方式)。</span><span class="sxs-lookup"><span data-stu-id="89064-214">Type the NETBIOS name, IP address, or fully-qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="89064-215">若要指定本機電腦，請輸入電腦名稱、"localhost" 或句點 (.)。</span><span class="sxs-lookup"><span data-stu-id="89064-215">To specify the local computer, type the computer name, "localhost", or a dot (.).</span></span>

<span data-ttu-id="89064-216">若要在 PSComputerName 參數的值中包含本機電腦，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="89064-216">To include the local computer in the value of the PSComputerName parameter, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="89064-217">如果從命令省略此參數，或它的值為 $null 或空字串，則工作流程目標是本機電腦，而且不會使用 Windows PowerShell 遠端執行命令。</span><span class="sxs-lookup"><span data-stu-id="89064-217">If this parameter is omitted from the command, or it value is $null or an empty string, the workflow target is the local computer and Windows PowerShell remoting is not used to run the command.</span></span>

<span data-ttu-id="89064-218">若要在 ComputerName 參數的值中使用 IP 位址，命令必須包含 PSCredential 參數。</span><span class="sxs-lookup"><span data-stu-id="89064-218">To use an IP address in the value of the ComputerName parameter, the command must include the PSCredential parameter.</span></span> <span data-ttu-id="89064-219">此外，必須將電腦設定為使用 HTTPS 傳輸，或必須在本機電腦的 WinRM TrustedHosts 清單中包含遠端電腦的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="89064-219">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="89064-220">如需將電腦名稱稱新增到 TrustedHosts 清單的指示，請參閱 [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)中的「如何將電腦新增到信任的主機清單」。</span><span class="sxs-lookup"><span data-stu-id="89064-220">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span></span>

#### <a name="psconfigurationname-string"></a><span data-ttu-id="89064-221">PSConfigurationName \<String\></span><span class="sxs-lookup"><span data-stu-id="89064-221">PSConfigurationName \<String\></span></span>

<span data-ttu-id="89064-222">指定用來在目的電腦上建立會話的會話設定。</span><span class="sxs-lookup"><span data-stu-id="89064-222">Specifies the session configurations that are used to create sessions on the target computers.</span></span> <span data-ttu-id="89064-223">請在目的電腦上輸入會話設定的名稱， (不在執行工作流程的電腦上。</span><span class="sxs-lookup"><span data-stu-id="89064-223">Enter the name of a session configuration on the target computers (not on the computer that is running the workflow.</span></span> <span data-ttu-id="89064-224">預設值為 [Microsoft. PowerShell]。</span><span class="sxs-lookup"><span data-stu-id="89064-224">The default is Microsoft.PowerShell.</span></span> <span data-ttu-id="89064-225">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-225">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionretrycount-uint"></a><span data-ttu-id="89064-226">PSConnectionRetryCount \<UInt\></span><span class="sxs-lookup"><span data-stu-id="89064-226">PSConnectionRetryCount \<UInt\></span></span>

<span data-ttu-id="89064-227">指定第一次連線嘗試失敗時，嘗試連接至每部目的電腦的次數上限。</span><span class="sxs-lookup"><span data-stu-id="89064-227">Specifies the maximum number of attempts to connect to each target computer if the first connection attempt fails.</span></span> <span data-ttu-id="89064-228">輸入介於1和 4294967295 (UInt) 之間的數位。</span><span class="sxs-lookup"><span data-stu-id="89064-228">Enter a number between 1 and 4,294,967,295 (UInt.MaxValue).</span></span> <span data-ttu-id="89064-229">預設值為零 (0) 表示無重試嘗試。</span><span class="sxs-lookup"><span data-stu-id="89064-229">The default value, zero (0), represents no retry attempts.</span></span>
<span data-ttu-id="89064-230">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-230">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionretryintervalsec-uint"></a><span data-ttu-id="89064-231">PSConnectionRetryIntervalSec \<UInt\></span><span class="sxs-lookup"><span data-stu-id="89064-231">PSConnectionRetryIntervalSec \<UInt\></span></span>

<span data-ttu-id="89064-232">指定連接重試嘗試之間的延遲（以秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="89064-232">Specifies the delay between connection retry attempts in seconds.</span></span> <span data-ttu-id="89064-233">預設值為零 (0)。</span><span class="sxs-lookup"><span data-stu-id="89064-233">The default value is zero (0).</span></span> <span data-ttu-id="89064-234">只有當 PSConnectionRetryCount 的值至少為1時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="89064-234">This parameter is valid only when the value of PSConnectionRetryCount is at least 1.</span></span> <span data-ttu-id="89064-235">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-235">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionuri-systemuri"></a><span data-ttu-id="89064-236">PSConnectionURI \<System.Uri\></span><span class="sxs-lookup"><span data-stu-id="89064-236">PSConnectionURI \<System.Uri\></span></span>

<span data-ttu-id="89064-237">指定 (URI) 的統一資源識別項，以定義目的電腦上活動的連接端點。</span><span class="sxs-lookup"><span data-stu-id="89064-237">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint for the activity on the target computer.</span></span> <span data-ttu-id="89064-238">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="89064-238">The URI must be fully qualified.</span></span> <span data-ttu-id="89064-239">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-239">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="89064-240">這個字串的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="89064-240">The format of this string is as follows:</span></span>

```
<Transport>://<ComputerName>:<Port>/<ApplicationName>
```

<span data-ttu-id="89064-241">預設值是 `http://localhost:5985/WSMAN`。</span><span class="sxs-lookup"><span data-stu-id="89064-241">The default value is `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="89064-242">如果您未指定 PSConnectionURI，您可以使用 PSUseSSL、PSComputerName、PSPort 和 PSApplicationName 參數來指定 PSConnectionURI 值。</span><span class="sxs-lookup"><span data-stu-id="89064-242">If you do not specify a PSConnectionURI, you can use the PSUseSSL, PSComputerName, PSPort, and PSApplicationName parameters to specify the PSConnectionURI values.</span></span>

<span data-ttu-id="89064-243">URI 的 Transport 區段有效值為 HTTP 與 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="89064-243">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="89064-244">若指定含傳輸區段的連線 URI，但未指定連接埠，將會以標準連接埠 80 (適用於 HTTP) 和 443 (適用於 HTTPS) 建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="89064-244">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="89064-245">若要使用預設連接埠於 Windows PowerShell 遠端功能，請為 HTTP 指定連接埠 5985，或是為 HTTPS 指定連接埠 5986。</span><span class="sxs-lookup"><span data-stu-id="89064-245">To use the default ports for Windows PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

#### <a name="pscredential-pscredential"></a><span data-ttu-id="89064-246">PSCredential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="89064-246">PSCredential \<PSCredential\></span></span>

<span data-ttu-id="89064-247">指定具有在目的電腦上執行活動之許可權的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="89064-247">Specifies a user account that has permission to run the activity on the target computer.</span></span> <span data-ttu-id="89064-248">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="89064-248">The default is the current user.</span></span> <span data-ttu-id="89064-249">只有當命令中包含 PSComputerName 參數時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="89064-249">This parameter is valid only when the PSComputerName parameter is included in the command.</span></span> <span data-ttu-id="89064-250">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-250">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="89064-251">輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入包含 PSCredential 物件的變數，例如 Get-Credential Cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="89064-251">Type a user name, such as "User01" or "Domain01\User01", or enter a variable that contains a PSCredential object, such as one that the Get-Credential cmdlet returns.</span></span> <span data-ttu-id="89064-252">若您只輸入使用者名稱，將會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="89064-252">If you enter only a user name, you will be prompted for a password.</span></span>

#### <a name="psdebug-psdatacollectiondebugrecord"></a><span data-ttu-id="89064-253">Set-psdebug \<PSDataCollection[DebugRecord]\></span><span class="sxs-lookup"><span data-stu-id="89064-253">PSDebug \<PSDataCollection[DebugRecord]\></span></span>

<span data-ttu-id="89064-254">將偵錯工具訊息從活動加入至指定的 debug 記錄集合，而不是將偵錯工具訊息寫入主控台，或工作流程作業的 Debug 屬性值。</span><span class="sxs-lookup"><span data-stu-id="89064-254">Adds debug messages from the activity to the specified debug record collection, instead of writing the debug messages to the console or to the value of the Debug property of the workflow job.</span></span> <span data-ttu-id="89064-255">您可以將多個活動的偵錯訊息，新增至相同的偵錯記錄集合物件。</span><span class="sxs-lookup"><span data-stu-id="89064-255">You can add debug messages from multiple activities to the same debug record collection object.</span></span>

<span data-ttu-id="89064-256">若要使用此活動一般參數，請使用 New-Object Cmdlet 來建立 DebugRecord 類型的 C o n 物件，並將物件儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="89064-256">To use this activity common parameter, use the New-Object cmdlet to create a PSDataCollection object with a type of DebugRecord and save the object in a variable.</span></span> <span data-ttu-id="89064-257">然後，將變數做為一或多個活動的 Set-psdebug 參數值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="89064-257">Then, use the variable as the value of the PSDebug parameter of one or more activities, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
    $debugCollection = New-Object -Type `
    System.Management.Automation.PSDataCollection[System.Management.Automation.DebugRecord]
    InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    if ($debugCollection -like "Missing") { ...}
}
```

#### <a name="psdisableserialization-boolean"></a><span data-ttu-id="89064-258">PSDisableSerialization \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="89064-258">PSDisableSerialization \<Boolean\></span></span>

<span data-ttu-id="89064-259">指示活動將「即時」(未序列化) 物件傳回至工作流程。</span><span class="sxs-lookup"><span data-stu-id="89064-259">Directs the activity to return "live" (not serialized) objects to the workflow.</span></span>
<span data-ttu-id="89064-260">產生的物件具有方法與屬性，但它們無法在取得檢查點時儲存。</span><span class="sxs-lookup"><span data-stu-id="89064-260">The resulting objects have methods, as well as properties, but they cannot be saved when a checkpoint is taken.</span></span>

#### <a name="psdisableserializationpreference-boolean"></a><span data-ttu-id="89064-261">PSDisableSerializationPreference \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="89064-261">PSDisableSerializationPreference \<Boolean\></span></span>

<span data-ttu-id="89064-262">將 PSDisableSerialization 參數的對等項套用至整個工作流程，而不只是活動。</span><span class="sxs-lookup"><span data-stu-id="89064-262">Applies the equivalent of the PSDisableSerialization parameter to the entire workflow, not just the activity.</span></span> <span data-ttu-id="89064-263">通常不建議加入這個參數，因為無法繼續或保存未序列化其物件的工作流程。</span><span class="sxs-lookup"><span data-stu-id="89064-263">Adding this parameter is generally not recommended, because a workflow that doesn't serialize its objects cannot be resumed or persisted.</span></span>

<span data-ttu-id="89064-264">有效值：</span><span class="sxs-lookup"><span data-stu-id="89064-264">Valid values:</span></span>

- <span data-ttu-id="89064-265"> (預設) 如果省略，而且您尚未將 PSDisableSerialization 參數加入至活動，則會序列化物件。</span><span class="sxs-lookup"><span data-stu-id="89064-265">(Default) If omitted, and you have also not added the PSDisableSerialization parameter to an activity, objects are serialized.</span></span>

- <span data-ttu-id="89064-266">`$True`.</span><span class="sxs-lookup"><span data-stu-id="89064-266">`$True`.</span></span> <span data-ttu-id="89064-267">指示工作流程中的所有活動傳回「即時」(未序列化) 物件。</span><span class="sxs-lookup"><span data-stu-id="89064-267">Directs all activities within a workflow to return "live" (not serialized) objects.</span></span> <span data-ttu-id="89064-268">產生的物件具有方法與屬性，但它們無法在取得檢查點時儲存。</span><span class="sxs-lookup"><span data-stu-id="89064-268">The resulting objects have methods, as well as properties, but they cannot be saved when a checkpoint is taken.</span></span>
- <span data-ttu-id="89064-269">`$False`.</span><span class="sxs-lookup"><span data-stu-id="89064-269">`$False`.</span></span> <span data-ttu-id="89064-270">工作流程物件會序列化。</span><span class="sxs-lookup"><span data-stu-id="89064-270">Workflow objects are serialized.</span></span>

#### <a name="pserror-psdatacollectionerrorrecord"></a><span data-ttu-id="89064-271">PSError \<PSDataCollection[ErrorRecord]\></span><span class="sxs-lookup"><span data-stu-id="89064-271">PSError \<PSDataCollection[ErrorRecord]\></span></span>

<span data-ttu-id="89064-272">將錯誤訊息從活動加入至指定的錯誤記錄集合，而不是將錯誤訊息寫入主控台，或工作流程工作的錯誤屬性值。</span><span class="sxs-lookup"><span data-stu-id="89064-272">Adds error messages from the activity to the specified error record collection, instead of writing the error messages to the console or to the value of the Error property of the workflow job.</span></span> <span data-ttu-id="89064-273">您可以將多個活動的錯誤訊息，新增至相同的錯誤記錄集合物件。</span><span class="sxs-lookup"><span data-stu-id="89064-273">You can add error messages from multiple activities to the same error record collection object.</span></span>

<span data-ttu-id="89064-274">若要使用此活動一般參數，請使用 `New-Object` Cmdlet 來建立 c o n 物件，其類型為 ErrorRecord，並將物件儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="89064-274">To use this activity common parameter, use the `New-Object` cmdlet to create a PSDataCollection object with a type of ErrorRecord and save the object in a variable.</span></span> <span data-ttu-id="89064-275">然後，將變數做為一或多個活動的 PSError 參數值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="89064-275">Then, use the variable as the value of the PSError parameter of one or more activities, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
   $typeName = "System.Management.Automation.PSDataCollection"
   $typeName += '[System.Management.Automation.ErrorRecord]'
   $ec = New-Object $typeName
   InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSError $ec
   InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSError $ec
   if ($ec.Count -gt 2)
   {
      # Do Some Work.
   }
}
```

#### <a name="pspersist-boolean"></a><span data-ttu-id="89064-276">PSPersist \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="89064-276">PSPersist \<Boolean\></span></span>

<span data-ttu-id="89064-277">接受活動之後的檢查點。</span><span class="sxs-lookup"><span data-stu-id="89064-277">Takes a checkpoint after the activity.</span></span> <span data-ttu-id="89064-278">除了在工作流程中指定的檢查點之外，此檢查點也是。</span><span class="sxs-lookup"><span data-stu-id="89064-278">This checkpoint is in addition to any checkpoints that are specified in the workflow.</span></span> <span data-ttu-id="89064-279">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-279">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="89064-280">「檢查點」或「持續點」是工作流程狀態的快照，以及工作流程執行時所捕捉到的資料，並儲存到磁片上的持續性存放區。</span><span class="sxs-lookup"><span data-stu-id="89064-280">A "checkpoint" or "persistence point" is a snapshot of the workflow state and data that is captured while the workflow runs and is saved to a persistence store on disk.</span></span> <span data-ttu-id="89064-281">Windows PowerShell 工作流程使用儲存的資料，從上一個持續點繼續暫停或中斷的工作流程，而不是重新開機工作流程。</span><span class="sxs-lookup"><span data-stu-id="89064-281">Windows PowerShell Workflow uses the saved data to resume a suspended or interrupted workflow from the last persistence point, rather than to restart the workflow.</span></span>

<span data-ttu-id="89064-282">有效值：</span><span class="sxs-lookup"><span data-stu-id="89064-282">Valid values:</span></span>

- <span data-ttu-id="89064-283"> (預設) 如果您省略此參數，則不會新增任何檢查點。</span><span class="sxs-lookup"><span data-stu-id="89064-283">(Default) If you omit this parameter, no checkpoints are added.</span></span> <span data-ttu-id="89064-284">檢查點會根據工作流程的設定取得。</span><span class="sxs-lookup"><span data-stu-id="89064-284">Checkpoints are taken based on the settings for the workflow.</span></span>

- <span data-ttu-id="89064-285">`$True`.</span><span class="sxs-lookup"><span data-stu-id="89064-285">`$True`.</span></span> <span data-ttu-id="89064-286">在活動完成後採取檢查點。</span><span class="sxs-lookup"><span data-stu-id="89064-286">Takes a checkpoint after the activity completes.</span></span>
  <span data-ttu-id="89064-287">除了在工作流程中指定的檢查點之外，此檢查點也是。</span><span class="sxs-lookup"><span data-stu-id="89064-287">This checkpoint is in addition to any checkpoints that are specified in the workflow.</span></span>

- <span data-ttu-id="89064-288">`$False`.</span><span class="sxs-lookup"><span data-stu-id="89064-288">`$False`.</span></span> <span data-ttu-id="89064-289">未新增任何檢查點。</span><span class="sxs-lookup"><span data-stu-id="89064-289">No checkpoints are added.</span></span> <span data-ttu-id="89064-290">只有在工作流程中指定時，才會採取檢查點。</span><span class="sxs-lookup"><span data-stu-id="89064-290">Checkpoints are taken only when specified in the workflow.</span></span>

#### <a name="psport-int32"></a><span data-ttu-id="89064-291">PSPort \<Int32\></span><span class="sxs-lookup"><span data-stu-id="89064-291">PSPort \<Int32\></span></span>

<span data-ttu-id="89064-292">指定目的電腦上的網路埠。</span><span class="sxs-lookup"><span data-stu-id="89064-292">Specifies the network port on the target computers.</span></span> <span data-ttu-id="89064-293">預設連接埠是 5985 (用於 HTTP 的 WinRM 連接埠) 和 5986 (用於 HTTPS 的 WinRM 連接埠)。</span><span class="sxs-lookup"><span data-stu-id="89064-293">The default ports are 5985 (the WinRM port for HTTP) and 5986 (the WinRM port for HTTPS).</span></span> <span data-ttu-id="89064-294">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-294">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="89064-295">除非您必須這樣做，否則請勿使用 PSPort 參數。</span><span class="sxs-lookup"><span data-stu-id="89064-295">Do not use the PSPort parameter unless you must.</span></span> <span data-ttu-id="89064-296">命令中設定的埠會套用到命令執行所在的所有電腦或會話。</span><span class="sxs-lookup"><span data-stu-id="89064-296">The port set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="89064-297">替代的連接埠設定可能使得命令無法在全部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="89064-297">An alternate port setting might prevent the command from running on all computers.</span></span> <span data-ttu-id="89064-298">使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。</span><span class="sxs-lookup"><span data-stu-id="89064-298">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span>

#### <a name="psprogress-psdatacollectionprogressrecord"></a><span data-ttu-id="89064-299">PSProgress \<PSDataCollection[ProgressRecord]\></span><span class="sxs-lookup"><span data-stu-id="89064-299">PSProgress \<PSDataCollection[ProgressRecord]\></span></span>

<span data-ttu-id="89064-300">將進度訊息從活動加入至指定的進度記錄集合，而不是將進度訊息寫入主控台，或工作流程作業的進度屬性值。</span><span class="sxs-lookup"><span data-stu-id="89064-300">Adds progress messages from the activity to the specified progress record collection, instead of writing the progress messages to the console or to the value of the Progress property of the workflow job.</span></span> <span data-ttu-id="89064-301">您可以將多個活動的進度訊息，新增至相同的進度記錄集合物件。</span><span class="sxs-lookup"><span data-stu-id="89064-301">You can add progress messages from multiple activities to the same progress record collection object.</span></span>

#### <a name="psprogressmessage-string"></a><span data-ttu-id="89064-302">PSProgressMessage \<String\></span><span class="sxs-lookup"><span data-stu-id="89064-302">PSProgressMessage \<String\></span></span>

<span data-ttu-id="89064-303">指定活動的易記描述。</span><span class="sxs-lookup"><span data-stu-id="89064-303">Specifies a friendly description of the activity.</span></span> <span data-ttu-id="89064-304">當工作流程執行時，PSProgressMessage 值會出現在進度列中。</span><span class="sxs-lookup"><span data-stu-id="89064-304">The PSProgressMessage value appears in the progress bar while the workflow runs.</span></span> <span data-ttu-id="89064-305">當命令中也包含 DisplayName 時，進度列內容會顯示為 \<DisplayName\> ： \<PSProgressMessage\> format。</span><span class="sxs-lookup"><span data-stu-id="89064-305">When the DisplayName is also included in the command, the progress bar content appears in \<DisplayName\>:\<PSProgressMessage\> format.</span></span>

<span data-ttu-id="89064-306">這個參數特別適合用來識別 ForEach 平行腳本區塊中的活動。</span><span class="sxs-lookup"><span data-stu-id="89064-306">This parameter is particularly useful for identifying activities in a ForEach -Parallel script block.</span></span> <span data-ttu-id="89064-307">若缺欠此訊息，會以相同的名稱識別所有平行分支中的活動。</span><span class="sxs-lookup"><span data-stu-id="89064-307">Without this message, activities in all parallel branches are identified by the same name.</span></span>

#### <a name="psremotingbehavior-remotingbehavior"></a><span data-ttu-id="89064-308">PSRemotingBehavior \<RemotingBehavior\></span><span class="sxs-lookup"><span data-stu-id="89064-308">PSRemotingBehavior \<RemotingBehavior\></span></span>

<span data-ttu-id="89064-309">指定在目標電腦上執行活動時要如何管理遠端處理。</span><span class="sxs-lookup"><span data-stu-id="89064-309">Specifies how remoting is managed when the activity is run on target computers.</span></span>
<span data-ttu-id="89064-310">PowerShell 是預設值。</span><span class="sxs-lookup"><span data-stu-id="89064-310">PowerShell is the default.</span></span>

<span data-ttu-id="89064-311">有效值為：</span><span class="sxs-lookup"><span data-stu-id="89064-311">Valid values are:</span></span>

- <span data-ttu-id="89064-312">無：活動不會在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="89064-312">None: The activity is not run on remote computers.</span></span>

- <span data-ttu-id="89064-313">PowerShell： Windows PowerShell 遠端處理是用來在目的電腦上執行活動。</span><span class="sxs-lookup"><span data-stu-id="89064-313">PowerShell: Windows PowerShell remoting is used to run the activity on target computers.</span></span>

- <span data-ttu-id="89064-314">Custom：活動支援它自己的遠端處理類型。</span><span class="sxs-lookup"><span data-stu-id="89064-314">Custom: The activity supports its own type of remoting.</span></span> <span data-ttu-id="89064-315">當實作為活動的 Cmdlet 將 RemotingCapability 屬性的值設定為 SupportedByCommand，且命令包含 ComputerName 參數時，這個值就有效。</span><span class="sxs-lookup"><span data-stu-id="89064-315">This value is valid when the cmdlet that is being implemented as an activity sets the value of the RemotingCapability attribute to SupportedByCommand and the command includes the ComputerName parameter.</span></span>

#### <a name="psrequiredmodules-string"></a><span data-ttu-id="89064-316">PSRequiredModules \<String[]\></span><span class="sxs-lookup"><span data-stu-id="89064-316">PSRequiredModules \<String[]\></span></span>

<span data-ttu-id="89064-317">執行命令前匯入指定的模組。</span><span class="sxs-lookup"><span data-stu-id="89064-317">Imports the specified modules before running the command.</span></span> <span data-ttu-id="89064-318">輸入模組名稱。</span><span class="sxs-lookup"><span data-stu-id="89064-318">Enter the module names.</span></span> <span data-ttu-id="89064-319">這些模組必須安裝在目的電腦上。</span><span class="sxs-lookup"><span data-stu-id="89064-319">The modules must be installed on the target computer.</span></span>

<span data-ttu-id="89064-320">在模組中第一次使用任何命令時，會自動匯入 PSModulePath 環境變數所指定的路徑中所安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="89064-320">Modules that are installed in a path specified in the PSModulePath environment variable are automatically imported on first use of any command in the module.</span></span>
<span data-ttu-id="89064-321">使用這個參數來匯入不在 PSModulePath 位置中的模組。</span><span class="sxs-lookup"><span data-stu-id="89064-321">Use this parameter to import modules that are not in a PSModulePath location.</span></span>

<span data-ttu-id="89064-322">因為工作流程中的每個活動是在其自己的工作階段中執行，所以 Import-Module 命令只會將模組匯入到執行它的工作階段中。</span><span class="sxs-lookup"><span data-stu-id="89064-322">Because each activity in a workflow runs in its own session, an Import-Module command imports a module only into the session in which it runs.</span></span> <span data-ttu-id="89064-323">它不會將模組匯入到執行其他活動的工作階段。</span><span class="sxs-lookup"><span data-stu-id="89064-323">It does not import the module into sessions in which other activities run.</span></span>

#### <a name="pssessionoption-pssessionoption"></a><span data-ttu-id="89064-324">PSSessionOption \<PSSessionOption\></span><span class="sxs-lookup"><span data-stu-id="89064-324">PSSessionOption \<PSSessionOption\></span></span>

<span data-ttu-id="89064-325">將會話的 advanced 選項設定為目的電腦。</span><span class="sxs-lookup"><span data-stu-id="89064-325">Sets advanced options for the sessions to the target computers.</span></span> <span data-ttu-id="89064-326">輸入 PSSessionOption 物件，例如您使用 New-PSSessionOption Cmdlet 建立的物件。</span><span class="sxs-lookup"><span data-stu-id="89064-326">Enter a PSSessionOption object, such as one that you create by using the New-PSSessionOption cmdlet.</span></span> <span data-ttu-id="89064-327">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-327">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="89064-328">會話選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。</span><span class="sxs-lookup"><span data-stu-id="89064-328">The default values for the session options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="89064-329">否則，會話會使用會話設定中指定的值。</span><span class="sxs-lookup"><span data-stu-id="89064-329">Otherwise, the session uses the values specified in the session configuration.</span></span>

<span data-ttu-id="89064-330">如需會話選項的描述（包括預設值），請參閱 New-PSSessionOption Cmdlet [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)的說明主題。</span><span class="sxs-lookup"><span data-stu-id="89064-330">For a description of the session options, including the default values, see the help topic for the New-PSSessionOption cmdlet [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="89064-331">如需 $PSSessionOption 喜好設定變數的詳細資訊，請參閱 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="89064-331">For more information about the $PSSessionOption preference variable, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

#### <a name="psusessl-boolean"></a><span data-ttu-id="89064-332">PSUseSSL \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="89064-332">PSUseSSL \<Boolean\></span></span>

<span data-ttu-id="89064-333">$True 的值會使用安全通訊端層 (SSL) 通訊協定來建立與目的電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="89064-333">A value of $True uses the Secure Sockets Layer (SSL) protocol to establish a connection to the target computer.</span></span> <span data-ttu-id="89064-334">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="89064-334">By default, SSL is not used.</span></span> <span data-ttu-id="89064-335">$False 的值沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="89064-335">A value of $False has no effect.</span></span> <span data-ttu-id="89064-336">此活動一般參數也是工作流程一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-336">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="89064-337">WS-Management 會加密透過網路傳輸的所有 Windows PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="89064-337">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="89064-338">UseSSL 是額外的保護，可透過 HTTPS (而非 HTTP) 傳送資料。</span><span class="sxs-lookup"><span data-stu-id="89064-338">UseSSL is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span> <span data-ttu-id="89064-339">若您使用此參數，但是命令所用的連接埠上無法使用 SSL，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="89064-339">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

#### <a name="psverbose-psdatacollectionverboserecord"></a><span data-ttu-id="89064-340">PSVerbose \<PSDataCollection[VerboseRecord]\></span><span class="sxs-lookup"><span data-stu-id="89064-340">PSVerbose \<PSDataCollection[VerboseRecord]\></span></span>

<span data-ttu-id="89064-341">將詳細資訊訊息從活動加入至指定的詳細資訊記錄集合，而不是將詳細資訊訊息寫入主控台，或工作流程工作的詳細資訊屬性值。</span><span class="sxs-lookup"><span data-stu-id="89064-341">Adds verbose messages from the activity to the specified verbose record collection, instead of writing the verbose messages to the console or to the value of the Verbose property of the workflow job.</span></span> <span data-ttu-id="89064-342">您可以將多個活動的詳細資訊訊息，新增至相同的詳細資訊記錄集合物件。</span><span class="sxs-lookup"><span data-stu-id="89064-342">You can add verbose messages from multiple activities to the same verbose record collection object.</span></span>

#### <a name="pswarning-psdatacollectionwarningrecord"></a><span data-ttu-id="89064-343">PSWarning \<PSDataCollection[WarningRecord]\></span><span class="sxs-lookup"><span data-stu-id="89064-343">PSWarning \<PSDataCollection[WarningRecord]\></span></span>

<span data-ttu-id="89064-344">將警告訊息從活動加入至指定的警告記錄集合，而不是將警告訊息寫入主控台，或工作流程工作的 Warning 屬性值。</span><span class="sxs-lookup"><span data-stu-id="89064-344">Adds warning messages from the activity to the specified warning record collection, instead of writing the warning messages to the console or to the value of the Warning property of the workflow job.</span></span> <span data-ttu-id="89064-345">您可以將多個活動的警告訊息，新增至相同的警告記錄集合物件。</span><span class="sxs-lookup"><span data-stu-id="89064-345">You can add warning messages from multiple activities to the same warning record collection object.</span></span>

#### <a name="result"></a><span data-ttu-id="89064-346">結果</span><span class="sxs-lookup"><span data-stu-id="89064-346">Result</span></span>

<span data-ttu-id="89064-347">這個參數只在 XAML 工作流程中有效。</span><span class="sxs-lookup"><span data-stu-id="89064-347">This parameter is valid only in XAML workflows.</span></span>

#### <a name="usedefaultinput-boolean"></a><span data-ttu-id="89064-348">UseDefaultInput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="89064-348">UseDefaultInput \<Boolean\></span></span>

<span data-ttu-id="89064-349">接受所有的工作流程輸入做為活動的輸入值。</span><span class="sxs-lookup"><span data-stu-id="89064-349">Accepts all workflow input as input to the activity by value.</span></span>

<span data-ttu-id="89064-350">例如，下列範例工作流程中的 Get-Process 活動會使用 UseDefaultInput 活動一般參數來取得傳遞至工作流程的輸入。</span><span class="sxs-lookup"><span data-stu-id="89064-350">For example, the Get-Process activity in the following sample workflow uses the UseDefaultInput activity common parameter to get input that is passed to the workflow.</span></span> <span data-ttu-id="89064-351">使用輸入執行工作流程時，該輸入由活動使用。</span><span class="sxs-lookup"><span data-stu-id="89064-351">When you run the workflow with input, that input is used by the activity.</span></span>

```powershell
workflow Test-Workflow
{
    Get-Service -UseDefaultInput $True
}

PS C:> Test-Workflow -InputObject WinRm
```

```output
Status   Name        DisplayName                            PSComputerName
------   ----        -----------                            --------------
Running  winrm       Windows Remote Management (WS-Manag... localhost
```

#### <a name="verbose-switchparameter"></a><span data-ttu-id="89064-352">詳細 \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="89064-352">Verbose \<SwitchParameter\></span></span>

<span data-ttu-id="89064-353">顯示命令所執行之作業的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="89064-353">Displays detailed information about the operation performed by the command.</span></span>
<span data-ttu-id="89064-354">這項資訊與追蹤或交易記錄檔中的資訊類似。</span><span class="sxs-lookup"><span data-stu-id="89064-354">This information resembles the information in a trace or in a transaction log.</span></span>
<span data-ttu-id="89064-355">Verbose 參數會覆寫目前命令之 $VerbosePreference 變數的值。</span><span class="sxs-lookup"><span data-stu-id="89064-355">The Verbose parameter overrides the value of the $VerbosePreference variable for the current command.</span></span> <span data-ttu-id="89064-356">此參數只適用于命令產生詳細訊息時。</span><span class="sxs-lookup"><span data-stu-id="89064-356">This parameter works only when the command generates a verbose message.</span></span> <span data-ttu-id="89064-357">此參數也是 Windows PowerShell 一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-357">This parameter is also a Windows PowerShell common parameter.</span></span>

#### <a name="warningaction-actionpreference"></a><span data-ttu-id="89064-358">WarningAction \<ActionPreference\></span><span class="sxs-lookup"><span data-stu-id="89064-358">WarningAction \<ActionPreference\></span></span>

<span data-ttu-id="89064-359">決定活動回應警告的方式。</span><span class="sxs-lookup"><span data-stu-id="89064-359">Determines how the activity responds to a warning.</span></span> <span data-ttu-id="89064-360">[繼續] 是預設值。</span><span class="sxs-lookup"><span data-stu-id="89064-360">"Continue" is the default value.</span></span> <span data-ttu-id="89064-361">WarningAction 參數會覆寫目前命令之 $WarningPreference 變數的值。</span><span class="sxs-lookup"><span data-stu-id="89064-361">The WarningAction parameter overrides the value of the $WarningPreference variable for the current command.</span></span> <span data-ttu-id="89064-362">只有當命令產生警告訊息時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="89064-362">This parameter works only when the command generates a warning message.</span></span> <span data-ttu-id="89064-363">此參數也是 Windows PowerShell 一般參數。</span><span class="sxs-lookup"><span data-stu-id="89064-363">This parameter is also a Windows PowerShell common parameter.</span></span>

<span data-ttu-id="89064-364">有效值：</span><span class="sxs-lookup"><span data-stu-id="89064-364">Valid Values:</span></span>

- <span data-ttu-id="89064-365">SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="89064-365">SilentlyContinue.</span></span> <span data-ttu-id="89064-366">隱藏警告訊息，並繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="89064-366">Suppresses the warning message and continues executing the command.</span></span>

- <span data-ttu-id="89064-367">繼續。</span><span class="sxs-lookup"><span data-stu-id="89064-367">Continue.</span></span> <span data-ttu-id="89064-368">顯示警告訊息，並繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="89064-368">Displays the warning message and continues executing the command.</span></span>
  <span data-ttu-id="89064-369">[繼續] 是預設值。</span><span class="sxs-lookup"><span data-stu-id="89064-369">"Continue" is the default value.</span></span>

- <span data-ttu-id="89064-370">詢問。</span><span class="sxs-lookup"><span data-stu-id="89064-370">Inquire.</span></span> <span data-ttu-id="89064-371">顯示警告訊息，並在繼續執行之前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="89064-371">Displays the warning message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="89064-372">此值很少使用。</span><span class="sxs-lookup"><span data-stu-id="89064-372">This value is rarely used.</span></span>

- <span data-ttu-id="89064-373">停止。</span><span class="sxs-lookup"><span data-stu-id="89064-373">Stop.</span></span> <span data-ttu-id="89064-374">顯示警告訊息，並停止執行命令。</span><span class="sxs-lookup"><span data-stu-id="89064-374">Displays the warning message and stops executing the command.</span></span>

> [!NOTE]
> <span data-ttu-id="89064-375">當命令中使用參數來執行腳本或函式時，WarningAction 參數不會覆寫 $WarningAction 喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="89064-375">The WarningAction parameter does not override the value of the $WarningAction preference variable when the parameter is used in a command to run a script or function.</span></span>

### <a name="examples"></a><span data-ttu-id="89064-376">範例</span><span class="sxs-lookup"><span data-stu-id="89064-376">EXAMPLES</span></span>

<span data-ttu-id="89064-377">活動一般參數非常有用。</span><span class="sxs-lookup"><span data-stu-id="89064-377">The activity common parameters are extremely useful.</span></span> <span data-ttu-id="89064-378">例如，您可以使用 PSComputerName 參數，只在目的電腦的子集上執行特定的活動。</span><span class="sxs-lookup"><span data-stu-id="89064-378">For example, you can use the PSComputerName parameter to run particular activities on only a subset of the target computers.</span></span>

<span data-ttu-id="89064-379">或者，您可以使用 PSConnectionRetryCount 和 PSConnectionRetryIntervalSec 參數來調整特定活動的重試值。</span><span class="sxs-lookup"><span data-stu-id="89064-379">Or, you might use the PSConnectionRetryCount and PSConnectionRetryIntervalSec parameters to adjust the retry values for particular activities.</span></span>

<span data-ttu-id="89064-380">下列範例示範如何使用 PSComputerName 活動一般參數，只在特定網域的電腦上執行 Get-EventLog 活動。</span><span class="sxs-lookup"><span data-stu-id="89064-380">The following example shows how to use the PSComputerName activity common parameters to run a Get-EventLog activity only on computers it a particular domain.</span></span>

```powershell
Workflow Test-Workflow
{
    $UserDomain = Get-Content -Path '.\UserComputers.txt'
    $Log = (Get-EventLog -LogName "Windows PowerShell" `
      -PSComputerName $UserDomain)

    if ($Log)
    {
        # Do Work Here.
    }
}
```

<!--
# KEYWORDS
[about_Activity_Common_Parameters](about_Activity_Common_Parameters.md)
[about_Activity_Parameters](about_Activity_Parameters.md)
[about_ActivityParameters]()about_ActivityParameters.md) -->

## <a name="see-also"></a><span data-ttu-id="89064-381">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89064-381">SEE ALSO</span></span>

<span data-ttu-id="89064-382">[about_Workflows](about_workflows.md) 
[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="89064-382">[about_Workflows](about_workflows.md)
[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)</span></span>
