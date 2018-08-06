---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: bed1186c10082bbdac7249503bf623678f13fccd
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267934"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="91200-102">統一且一致的狀態和狀態表示法</span><span class="sxs-lookup"><span data-stu-id="91200-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="91200-103">已在此版本中為自動化組建 LCM 狀態與 DSC 狀態增加了一系列的增強功能。</span><span class="sxs-lookup"><span data-stu-id="91200-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="91200-104">這些包括整合且一致的狀態和狀態表示法、由 `Get-DscConfigurationStatus` Cmdlet 傳回之狀態物件的可管理 datetime 屬性，以及由 `Get-DscLocalConfigurationManager` Cmdlet 傳回之增強的 LCM 狀態詳細資料屬性。</span><span class="sxs-lookup"><span data-stu-id="91200-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="91200-105">LCM 狀態和 DSC 作業狀態的表示法根據下列規則進行重新瀏覽和整合︰</span><span class="sxs-lookup"><span data-stu-id="91200-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="91200-106">Notprocessed 資源不會影響 LCM 狀態與 DSC 狀態。</span><span class="sxs-lookup"><span data-stu-id="91200-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="91200-107">一旦遇到要求重新開機的資源，LCM 就會停止處理更多資源。</span><span class="sxs-lookup"><span data-stu-id="91200-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="91200-108">要求重新開機的資源不處於所需的狀態，直到重新開機真正發生。</span><span class="sxs-lookup"><span data-stu-id="91200-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="91200-109">在發生失敗的資源之後，只要其他資源不是依存於失敗的資源，LCM 就會持續處理更多資源。</span><span class="sxs-lookup"><span data-stu-id="91200-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="91200-110">`Get-DscConfigurationStatus` Cmdlet 所傳回的整體狀態是所有資源狀態的超集。</span><span class="sxs-lookup"><span data-stu-id="91200-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="91200-111">PendingReboot 狀態為 PendingConfiguration 狀態的超集。</span><span class="sxs-lookup"><span data-stu-id="91200-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="91200-112">下表說明一些典型狀況下的結果狀態和與狀態相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="91200-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="91200-113">案例</span><span class="sxs-lookup"><span data-stu-id="91200-113">Scenario</span></span>                        | <span data-ttu-id="91200-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="91200-114">LCMState</span></span>             | <span data-ttu-id="91200-115">狀態</span><span class="sxs-lookup"><span data-stu-id="91200-115">Status</span></span>     | <span data-ttu-id="91200-116">要求重新開機</span><span class="sxs-lookup"><span data-stu-id="91200-116">Reboot Requested</span></span> | <span data-ttu-id="91200-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="91200-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="91200-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="91200-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="91200-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="91200-119">S**^**</span></span>                          | <span data-ttu-id="91200-120">閒置</span><span class="sxs-lookup"><span data-stu-id="91200-120">Idle</span></span>                 | <span data-ttu-id="91200-121">Success</span><span class="sxs-lookup"><span data-stu-id="91200-121">Success</span></span>    | <span data-ttu-id="91200-122">$false</span><span class="sxs-lookup"><span data-stu-id="91200-122">$false</span></span>        | <span data-ttu-id="91200-123">S</span><span class="sxs-lookup"><span data-stu-id="91200-123">S</span></span>                            | <span data-ttu-id="91200-124">$null</span><span class="sxs-lookup"><span data-stu-id="91200-124">$null</span></span>                          |
| <span data-ttu-id="91200-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="91200-125">F**^**</span></span>                          | <span data-ttu-id="91200-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="91200-126">PendingConfiguration</span></span> | <span data-ttu-id="91200-127">失敗</span><span class="sxs-lookup"><span data-stu-id="91200-127">Failure</span></span>    | <span data-ttu-id="91200-128">$false</span><span class="sxs-lookup"><span data-stu-id="91200-128">$false</span></span>        | <span data-ttu-id="91200-129">$null</span><span class="sxs-lookup"><span data-stu-id="91200-129">$null</span></span>                        | <span data-ttu-id="91200-130">F</span><span class="sxs-lookup"><span data-stu-id="91200-130">F</span></span>                              |
| <span data-ttu-id="91200-131">S,F</span><span class="sxs-lookup"><span data-stu-id="91200-131">S,F</span></span>                             | <span data-ttu-id="91200-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="91200-132">PendingConfiguration</span></span> | <span data-ttu-id="91200-133">失敗</span><span class="sxs-lookup"><span data-stu-id="91200-133">Failure</span></span>    | <span data-ttu-id="91200-134">$false</span><span class="sxs-lookup"><span data-stu-id="91200-134">$false</span></span>        | <span data-ttu-id="91200-135">S</span><span class="sxs-lookup"><span data-stu-id="91200-135">S</span></span>                            | <span data-ttu-id="91200-136">F</span><span class="sxs-lookup"><span data-stu-id="91200-136">F</span></span>                              |
| <span data-ttu-id="91200-137">F,S</span><span class="sxs-lookup"><span data-stu-id="91200-137">F,S</span></span>                             | <span data-ttu-id="91200-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="91200-138">PendingConfiguration</span></span> | <span data-ttu-id="91200-139">失敗</span><span class="sxs-lookup"><span data-stu-id="91200-139">Failure</span></span>    | <span data-ttu-id="91200-140">$false</span><span class="sxs-lookup"><span data-stu-id="91200-140">$false</span></span>        | <span data-ttu-id="91200-141">S</span><span class="sxs-lookup"><span data-stu-id="91200-141">S</span></span>                            | <span data-ttu-id="91200-142">F</span><span class="sxs-lookup"><span data-stu-id="91200-142">F</span></span>                              |
| <span data-ttu-id="91200-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="91200-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="91200-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="91200-144">PendingConfiguration</span></span> | <span data-ttu-id="91200-145">失敗</span><span class="sxs-lookup"><span data-stu-id="91200-145">Failure</span></span>    | <span data-ttu-id="91200-146">$false</span><span class="sxs-lookup"><span data-stu-id="91200-146">$false</span></span>        | <span data-ttu-id="91200-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="91200-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="91200-148">F</span><span class="sxs-lookup"><span data-stu-id="91200-148">F</span></span>                              |
| <span data-ttu-id="91200-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="91200-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="91200-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="91200-150">PendingConfiguration</span></span> | <span data-ttu-id="91200-151">失敗</span><span class="sxs-lookup"><span data-stu-id="91200-151">Failure</span></span>    | <span data-ttu-id="91200-152">$false</span><span class="sxs-lookup"><span data-stu-id="91200-152">$false</span></span>        | <span data-ttu-id="91200-153">S</span><span class="sxs-lookup"><span data-stu-id="91200-153">S</span></span>                            | <span data-ttu-id="91200-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="91200-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="91200-155">S, r</span><span class="sxs-lookup"><span data-stu-id="91200-155">S, r</span></span>                            | <span data-ttu-id="91200-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="91200-156">PendingReboot</span></span>        | <span data-ttu-id="91200-157">Success</span><span class="sxs-lookup"><span data-stu-id="91200-157">Success</span></span>    | <span data-ttu-id="91200-158">$true</span><span class="sxs-lookup"><span data-stu-id="91200-158">$true</span></span>         | <span data-ttu-id="91200-159">S</span><span class="sxs-lookup"><span data-stu-id="91200-159">S</span></span>                            | <span data-ttu-id="91200-160">r</span><span class="sxs-lookup"><span data-stu-id="91200-160">r</span></span>                              |
| <span data-ttu-id="91200-161">F, r</span><span class="sxs-lookup"><span data-stu-id="91200-161">F, r</span></span>                            | <span data-ttu-id="91200-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="91200-162">PendingReboot</span></span>        | <span data-ttu-id="91200-163">失敗</span><span class="sxs-lookup"><span data-stu-id="91200-163">Failure</span></span>    | <span data-ttu-id="91200-164">$true</span><span class="sxs-lookup"><span data-stu-id="91200-164">$true</span></span>         | <span data-ttu-id="91200-165">$null</span><span class="sxs-lookup"><span data-stu-id="91200-165">$null</span></span>                        | <span data-ttu-id="91200-166">F, r</span><span class="sxs-lookup"><span data-stu-id="91200-166">F, r</span></span>                           |
| <span data-ttu-id="91200-167">r, S</span><span class="sxs-lookup"><span data-stu-id="91200-167">r, S</span></span>                            | <span data-ttu-id="91200-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="91200-168">PendingReboot</span></span>        | <span data-ttu-id="91200-169">Success</span><span class="sxs-lookup"><span data-stu-id="91200-169">Success</span></span>    | <span data-ttu-id="91200-170">$true</span><span class="sxs-lookup"><span data-stu-id="91200-170">$true</span></span>         | <span data-ttu-id="91200-171">$null</span><span class="sxs-lookup"><span data-stu-id="91200-171">$null</span></span>                        | <span data-ttu-id="91200-172">r</span><span class="sxs-lookup"><span data-stu-id="91200-172">r</span></span>                              |
| <span data-ttu-id="91200-173">r, F</span><span class="sxs-lookup"><span data-stu-id="91200-173">r, F</span></span>                            | <span data-ttu-id="91200-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="91200-174">PendingReboot</span></span>        | <span data-ttu-id="91200-175">Success</span><span class="sxs-lookup"><span data-stu-id="91200-175">Success</span></span>    | <span data-ttu-id="91200-176">$true</span><span class="sxs-lookup"><span data-stu-id="91200-176">$true</span></span>         | <span data-ttu-id="91200-177">$null</span><span class="sxs-lookup"><span data-stu-id="91200-177">$null</span></span>                        | <span data-ttu-id="91200-178">r</span><span class="sxs-lookup"><span data-stu-id="91200-178">r</span></span>                              |

- <span data-ttu-id="91200-179">S<sub>i</sub>︰一系列成功套用的資源</span><span class="sxs-lookup"><span data-stu-id="91200-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="91200-180">F<sub>i</sub>︰一系列套用失敗的資源</span><span class="sxs-lookup"><span data-stu-id="91200-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="91200-181">r︰需要重新開機的資源</span><span class="sxs-lookup"><span data-stu-id="91200-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="91200-182">Get-DscConfigurationStatus Cmdlet 中的增強功能</span><span class="sxs-lookup"><span data-stu-id="91200-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="91200-183">已在此版本中對 `Get-DscConfigurationStatus` Cmdlet 提供一些增強功能。</span><span class="sxs-lookup"><span data-stu-id="91200-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="91200-184">先前由 Cmdlet 傳回的物件 StartDate 屬性為字串類型。</span><span class="sxs-lookup"><span data-stu-id="91200-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="91200-185">現在，它是 Datetime 類型，可根據 Datetime 物件內建內容讓複雜的選取和篩選更為容易。</span><span class="sxs-lookup"><span data-stu-id="91200-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

<span data-ttu-id="91200-186">下列範例會傳回所有 DSC 作業記錄，這些記錄會發生在每週和當天相同的日子。</span><span class="sxs-lookup"><span data-stu-id="91200-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="91200-187">不變更節點設定的作業記錄 (也就是唯讀作業)。</span><span class="sxs-lookup"><span data-stu-id="91200-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="91200-188">因此，`Test-DscConfiguration`、`Get-DscConfiguration` 作業無法在從 `Get-DscConfigurationStatus` Cmdlet 傳回的物件中攙雜使用。</span><span class="sxs-lookup"><span data-stu-id="91200-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="91200-189">中繼設定的設定作業記錄會加入至 `Get-DscConfigurationStatus` Cmdlet 傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="91200-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="91200-190">以下是從 `Get-DscConfigurationStatus –All` Cmdlet 傳回的結果範例。</span><span class="sxs-lookup"><span data-stu-id="91200-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="91200-191">Get-DscLocalConfigurationManager Cmdlet 中的增強功能</span><span class="sxs-lookup"><span data-stu-id="91200-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="91200-192">LCMStateDetail 的新欄位會加入至從 `Get-DscLocalConfigurationManager` Cmdlet 傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="91200-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="91200-193">LCMState「忙碌」時，就會將此欄位填滿。</span><span class="sxs-lookup"><span data-stu-id="91200-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="91200-194">它可以由下列 Cmdlet 擷取：</span><span class="sxs-lookup"><span data-stu-id="91200-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="91200-195">以下是連續監控設定的範例輸出，它需要遠端節點上的兩次重新開機。</span><span class="sxs-lookup"><span data-stu-id="91200-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

```output
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```