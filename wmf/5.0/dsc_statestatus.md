---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 0e8d0cb1e4afa7bc791d45bfb0b981654cb09ed5
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892564"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="e9099-102">統一且一致的狀態和狀態表示法</span><span class="sxs-lookup"><span data-stu-id="e9099-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="e9099-103">已在此版本中為自動化組建 LCM 狀態與 DSC 狀態增加了一系列的增強功能。</span><span class="sxs-lookup"><span data-stu-id="e9099-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="e9099-104">這些包括整合且一致的狀態和狀態表示法、由 `Get-DscConfigurationStatus` Cmdlet 傳回之狀態物件的可管理 datetime 屬性，以及由 `Get-DscLocalConfigurationManager` Cmdlet 傳回之增強的 LCM 狀態詳細資料屬性。</span><span class="sxs-lookup"><span data-stu-id="e9099-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="e9099-105">LCM 狀態和 DSC 作業狀態的表示法根據下列規則進行重新瀏覽和整合︰</span><span class="sxs-lookup"><span data-stu-id="e9099-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="e9099-106">Notprocessed 資源不會影響 LCM 狀態與 DSC 狀態。</span><span class="sxs-lookup"><span data-stu-id="e9099-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="e9099-107">一旦遇到要求重新開機的資源，LCM 就會停止處理更多資源。</span><span class="sxs-lookup"><span data-stu-id="e9099-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="e9099-108">要求重新開機的資源不處於所需的狀態，直到重新開機真正發生。</span><span class="sxs-lookup"><span data-stu-id="e9099-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="e9099-109">在發生失敗的資源之後，只要其他資源不是依存於失敗的資源，LCM 就會持續處理更多資源。</span><span class="sxs-lookup"><span data-stu-id="e9099-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="e9099-110">`Get-DscConfigurationStatus` Cmdlet 所傳回的整體狀態是所有資源狀態的超集。</span><span class="sxs-lookup"><span data-stu-id="e9099-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="e9099-111">PendingReboot 狀態為 PendingConfiguration 狀態的超集。</span><span class="sxs-lookup"><span data-stu-id="e9099-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

   <span data-ttu-id="e9099-112">下表說明一些典型狀況下的結果狀態和與狀態相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="e9099-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

   | <span data-ttu-id="e9099-113">案例</span><span class="sxs-lookup"><span data-stu-id="e9099-113">Scenario</span></span>                    | <span data-ttu-id="e9099-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="e9099-114">LCMState</span></span>       | <span data-ttu-id="e9099-115">狀態</span><span class="sxs-lookup"><span data-stu-id="e9099-115">Status</span></span> | <span data-ttu-id="e9099-116">要求重新開機</span><span class="sxs-lookup"><span data-stu-id="e9099-116">Reboot Requested</span></span>  | <span data-ttu-id="e9099-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="e9099-117">ResourcesInDesiredState</span></span>  | <span data-ttu-id="e9099-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="e9099-118">ResourcesNotInDesiredState</span></span> |
   |---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
   | <span data-ttu-id="e9099-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="e9099-119">S**^**</span></span>                          | <span data-ttu-id="e9099-120">閒置</span><span class="sxs-lookup"><span data-stu-id="e9099-120">Idle</span></span>                 | <span data-ttu-id="e9099-121">Success</span><span class="sxs-lookup"><span data-stu-id="e9099-121">Success</span></span>    | <span data-ttu-id="e9099-122">$false</span><span class="sxs-lookup"><span data-stu-id="e9099-122">$false</span></span>        | <span data-ttu-id="e9099-123">S</span><span class="sxs-lookup"><span data-stu-id="e9099-123">S</span></span>                            | <span data-ttu-id="e9099-124">$null</span><span class="sxs-lookup"><span data-stu-id="e9099-124">$null</span></span>                          |
   | <span data-ttu-id="e9099-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="e9099-125">F**^**</span></span>                          | <span data-ttu-id="e9099-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="e9099-126">PendingConfiguration</span></span> | <span data-ttu-id="e9099-127">失敗</span><span class="sxs-lookup"><span data-stu-id="e9099-127">Failure</span></span>    | <span data-ttu-id="e9099-128">$false</span><span class="sxs-lookup"><span data-stu-id="e9099-128">$false</span></span>        | <span data-ttu-id="e9099-129">$null</span><span class="sxs-lookup"><span data-stu-id="e9099-129">$null</span></span>                        | <span data-ttu-id="e9099-130">F</span><span class="sxs-lookup"><span data-stu-id="e9099-130">F</span></span>                              |
   | <span data-ttu-id="e9099-131">S,F</span><span class="sxs-lookup"><span data-stu-id="e9099-131">S,F</span></span>                             | <span data-ttu-id="e9099-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="e9099-132">PendingConfiguration</span></span> | <span data-ttu-id="e9099-133">失敗</span><span class="sxs-lookup"><span data-stu-id="e9099-133">Failure</span></span>    | <span data-ttu-id="e9099-134">$false</span><span class="sxs-lookup"><span data-stu-id="e9099-134">$false</span></span>        | <span data-ttu-id="e9099-135">S</span><span class="sxs-lookup"><span data-stu-id="e9099-135">S</span></span>                            | <span data-ttu-id="e9099-136">F</span><span class="sxs-lookup"><span data-stu-id="e9099-136">F</span></span>                              |
   | <span data-ttu-id="e9099-137">F,S</span><span class="sxs-lookup"><span data-stu-id="e9099-137">F,S</span></span>                             | <span data-ttu-id="e9099-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="e9099-138">PendingConfiguration</span></span> | <span data-ttu-id="e9099-139">失敗</span><span class="sxs-lookup"><span data-stu-id="e9099-139">Failure</span></span>    | <span data-ttu-id="e9099-140">$false</span><span class="sxs-lookup"><span data-stu-id="e9099-140">$false</span></span>        | <span data-ttu-id="e9099-141">S</span><span class="sxs-lookup"><span data-stu-id="e9099-141">S</span></span>                            | <span data-ttu-id="e9099-142">F</span><span class="sxs-lookup"><span data-stu-id="e9099-142">F</span></span>                              |
   | <span data-ttu-id="e9099-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="e9099-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="e9099-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="e9099-144">PendingConfiguration</span></span> | <span data-ttu-id="e9099-145">失敗</span><span class="sxs-lookup"><span data-stu-id="e9099-145">Failure</span></span>    | <span data-ttu-id="e9099-146">$false</span><span class="sxs-lookup"><span data-stu-id="e9099-146">$false</span></span>        | <span data-ttu-id="e9099-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="e9099-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="e9099-148">F</span><span class="sxs-lookup"><span data-stu-id="e9099-148">F</span></span>                              |
   | <span data-ttu-id="e9099-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="e9099-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="e9099-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="e9099-150">PendingConfiguration</span></span> | <span data-ttu-id="e9099-151">失敗</span><span class="sxs-lookup"><span data-stu-id="e9099-151">Failure</span></span>    | <span data-ttu-id="e9099-152">$false</span><span class="sxs-lookup"><span data-stu-id="e9099-152">$false</span></span>        | <span data-ttu-id="e9099-153">S</span><span class="sxs-lookup"><span data-stu-id="e9099-153">S</span></span>                            | <span data-ttu-id="e9099-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="e9099-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
   | <span data-ttu-id="e9099-155">S, r</span><span class="sxs-lookup"><span data-stu-id="e9099-155">S, r</span></span>                            | <span data-ttu-id="e9099-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="e9099-156">PendingReboot</span></span>        | <span data-ttu-id="e9099-157">Success</span><span class="sxs-lookup"><span data-stu-id="e9099-157">Success</span></span>    | <span data-ttu-id="e9099-158">$true</span><span class="sxs-lookup"><span data-stu-id="e9099-158">$true</span></span>         | <span data-ttu-id="e9099-159">S</span><span class="sxs-lookup"><span data-stu-id="e9099-159">S</span></span>                            | <span data-ttu-id="e9099-160">r</span><span class="sxs-lookup"><span data-stu-id="e9099-160">r</span></span>                              |
   | <span data-ttu-id="e9099-161">F, r</span><span class="sxs-lookup"><span data-stu-id="e9099-161">F, r</span></span>                            | <span data-ttu-id="e9099-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="e9099-162">PendingReboot</span></span>        | <span data-ttu-id="e9099-163">失敗</span><span class="sxs-lookup"><span data-stu-id="e9099-163">Failure</span></span>    | <span data-ttu-id="e9099-164">$true</span><span class="sxs-lookup"><span data-stu-id="e9099-164">$true</span></span>         | <span data-ttu-id="e9099-165">$null</span><span class="sxs-lookup"><span data-stu-id="e9099-165">$null</span></span>                        | <span data-ttu-id="e9099-166">F, r</span><span class="sxs-lookup"><span data-stu-id="e9099-166">F, r</span></span>                           |
   | <span data-ttu-id="e9099-167">r, S</span><span class="sxs-lookup"><span data-stu-id="e9099-167">r, S</span></span>                            | <span data-ttu-id="e9099-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="e9099-168">PendingReboot</span></span>        | <span data-ttu-id="e9099-169">Success</span><span class="sxs-lookup"><span data-stu-id="e9099-169">Success</span></span>    | <span data-ttu-id="e9099-170">$true</span><span class="sxs-lookup"><span data-stu-id="e9099-170">$true</span></span>         | <span data-ttu-id="e9099-171">$null</span><span class="sxs-lookup"><span data-stu-id="e9099-171">$null</span></span>                        | <span data-ttu-id="e9099-172">r</span><span class="sxs-lookup"><span data-stu-id="e9099-172">r</span></span>                              |
   | <span data-ttu-id="e9099-173">r, F</span><span class="sxs-lookup"><span data-stu-id="e9099-173">r, F</span></span>                            | <span data-ttu-id="e9099-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="e9099-174">PendingReboot</span></span>        | <span data-ttu-id="e9099-175">Success</span><span class="sxs-lookup"><span data-stu-id="e9099-175">Success</span></span>    | <span data-ttu-id="e9099-176">$true</span><span class="sxs-lookup"><span data-stu-id="e9099-176">$true</span></span>         | <span data-ttu-id="e9099-177">$null</span><span class="sxs-lookup"><span data-stu-id="e9099-177">$null</span></span>                        | <span data-ttu-id="e9099-178">r</span><span class="sxs-lookup"><span data-stu-id="e9099-178">r</span></span>                              |

   <span data-ttu-id="e9099-179">^
   S<sub>i</sub>：成功套用的一系列資源；F<sub>i</sub>︰未成功套用的一系列資源；r：需要重新開機的資源\*</span><span class="sxs-lookup"><span data-stu-id="e9099-179">^
   S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

   ```powershell
   $LCMState = (Get-DscLocalConfigurationManager).LCMState
   $Status = (Get-DscConfigurationStatus).Status

   $RebootRequested = (Get-DscConfigurationStatus).RebootRequested

   $ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

   $ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
   ```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="e9099-180">Get-DscConfigurationStatus Cmdlet 中的增強功能</span><span class="sxs-lookup"><span data-stu-id="e9099-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="e9099-181">已在此版本中對 `Get-DscConfigurationStatus` Cmdlet 提供一些增強功能。</span><span class="sxs-lookup"><span data-stu-id="e9099-181">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="e9099-182">先前由 Cmdlet 傳回的物件 StartDate 屬性為字串類型。</span><span class="sxs-lookup"><span data-stu-id="e9099-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="e9099-183">現在，它是 Datetime 類型，可根據 Datetime 物件內建內容讓複雜的選取和篩選更為容易。</span><span class="sxs-lookup"><span data-stu-id="e9099-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

<span data-ttu-id="e9099-184">以下為傳回所有 DSC 作業記錄的範例，此作業記錄發生在每週和今天相同的日子。</span><span class="sxs-lookup"><span data-stu-id="e9099-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="e9099-185">不變更節點設定的作業記錄 (也就是唯讀作業)。</span><span class="sxs-lookup"><span data-stu-id="e9099-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="e9099-186">因此，`Test-DscConfiguration`、`Get-DscConfiguration` 作業無法在從 `Get-DscConfigurationStatus` Cmdlet 傳回的物件中攙雜使用。</span><span class="sxs-lookup"><span data-stu-id="e9099-186">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span>
<span data-ttu-id="e9099-187">中繼設定的設定作業記錄會加入至 `Get-DscConfigurationStatus` Cmdlet 傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="e9099-187">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="e9099-188">以下是從 `Get-DscConfigurationStatus` –All Cmdlet 傳回的結果範例。</span><span class="sxs-lookup"><span data-stu-id="e9099-188">Following is an example of result returned from `Get-DscConfigurationStatus` –All cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="e9099-189">Get-DscLocalConfigurationManager Cmdlet 中的增強功能</span><span class="sxs-lookup"><span data-stu-id="e9099-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="e9099-190">LCMStateDetail 的新欄位會加入至從 `Get-DscLocalConfigurationManager` Cmdlet 傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="e9099-190">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="e9099-191">LCMState「忙碌」時，就會將此欄位填滿。</span><span class="sxs-lookup"><span data-stu-id="e9099-191">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="e9099-192">它可以由下列 Cmdlet 擷取：</span><span class="sxs-lookup"><span data-stu-id="e9099-192">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="e9099-193">以下是連續監控設定的範例輸出，它需要遠端節點上的兩次重新開機。</span><span class="sxs-lookup"><span data-stu-id="e9099-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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