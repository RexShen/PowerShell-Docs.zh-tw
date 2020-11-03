---
description: 自訂 PowerShell 行為的變數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Preference_Variables
ms.openlocfilehash: 25677cf687349bf805b66a116d3b2f09d27037bd
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207608"
---
# <a name="about-preference-variables"></a><span data-ttu-id="4cee4-104">關於喜好設定變數</span><span class="sxs-lookup"><span data-stu-id="4cee4-104">About Preference Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="4cee4-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="4cee4-105">Short description</span></span>

<span data-ttu-id="4cee4-106">自訂 PowerShell 行為的變數。</span><span class="sxs-lookup"><span data-stu-id="4cee4-106">Variables that customize the behavior of PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4cee4-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="4cee4-107">Long description</span></span>

<span data-ttu-id="4cee4-108">PowerShell 包含一組可讓您自訂其行為的變數。</span><span class="sxs-lookup"><span data-stu-id="4cee4-108">PowerShell includes a set of variables that enable you to customize its behavior.</span></span> <span data-ttu-id="4cee4-109">這些喜好設定變數的運作方式就像 GUI 系統中的選項。</span><span class="sxs-lookup"><span data-stu-id="4cee4-109">These preference variables work like the options in GUI-based systems.</span></span>

<span data-ttu-id="4cee4-110">喜好設定變數會影響 PowerShell 操作環境和環境中執行的所有命令。</span><span class="sxs-lookup"><span data-stu-id="4cee4-110">The preference variables affect the PowerShell operating environment and all commands run in the environment.</span></span> <span data-ttu-id="4cee4-111">在許多情況下，Cmdlet 都有參數，可讓您用來覆寫特定命令的喜好設定行為。</span><span class="sxs-lookup"><span data-stu-id="4cee4-111">In many cases, the cmdlets have parameters that you can use to override the preference behavior for a specific command.</span></span>

<span data-ttu-id="4cee4-112">下表列出喜好設定變數及其預設值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-112">The following table lists the preference variables and their default values.</span></span>

|             <span data-ttu-id="4cee4-113">變數</span><span class="sxs-lookup"><span data-stu-id="4cee4-113">Variable</span></span>             |       <span data-ttu-id="4cee4-114">預設值</span><span class="sxs-lookup"><span data-stu-id="4cee4-114">Default Value</span></span>       |
| -------------------------------- | ------------------------- |
| `$ConfirmPreference`             | <span data-ttu-id="4cee4-115">高</span><span class="sxs-lookup"><span data-stu-id="4cee4-115">High</span></span>                      |
| `$DebugPreference`               | <span data-ttu-id="4cee4-116">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="4cee4-116">SilentlyContinue</span></span>          |
| `$ErrorActionPreference`         | <span data-ttu-id="4cee4-117">Continue</span><span class="sxs-lookup"><span data-stu-id="4cee4-117">Continue</span></span>                  |
| `$ErrorView`                     | <span data-ttu-id="4cee4-118">NormalView</span><span class="sxs-lookup"><span data-stu-id="4cee4-118">NormalView</span></span>                |
| `$FormatEnumerationLimit`        | <span data-ttu-id="4cee4-119">4</span><span class="sxs-lookup"><span data-stu-id="4cee4-119">4</span></span>                         |
| `$InformationPreference`         | <span data-ttu-id="4cee4-120">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="4cee4-120">SilentlyContinue</span></span>          |
| `$LogCommandHealthEvent`         | <span data-ttu-id="4cee4-121">False (未記錄) </span><span class="sxs-lookup"><span data-stu-id="4cee4-121">False (not logged)</span></span>        |
| `$LogCommandLifecycleEvent`      | <span data-ttu-id="4cee4-122">False (未記錄) </span><span class="sxs-lookup"><span data-stu-id="4cee4-122">False (not logged)</span></span>        |
| `$LogEngineHealthEvent`          | <span data-ttu-id="4cee4-123">True (記錄) </span><span class="sxs-lookup"><span data-stu-id="4cee4-123">True (logged)</span></span>             |
| `$LogEngineLifecycleEvent`       | <span data-ttu-id="4cee4-124">True (記錄) </span><span class="sxs-lookup"><span data-stu-id="4cee4-124">True (logged)</span></span>             |
| `$LogProviderLifecycleEvent`     | <span data-ttu-id="4cee4-125">True (記錄) </span><span class="sxs-lookup"><span data-stu-id="4cee4-125">True (logged)</span></span>             |
| `$LogProviderHealthEvent`        | <span data-ttu-id="4cee4-126">True (記錄) </span><span class="sxs-lookup"><span data-stu-id="4cee4-126">True (logged)</span></span>             |
| `$MaximumAliasCount`             | <span data-ttu-id="4cee4-127">4096</span><span class="sxs-lookup"><span data-stu-id="4cee4-127">4096</span></span>                      |
| `$MaximumDriveCount`             | <span data-ttu-id="4cee4-128">4096</span><span class="sxs-lookup"><span data-stu-id="4cee4-128">4096</span></span>                      |
| `$MaximumErrorCount`             | <span data-ttu-id="4cee4-129">256</span><span class="sxs-lookup"><span data-stu-id="4cee4-129">256</span></span>                       |
| `$MaximumFunctionCount`          | <span data-ttu-id="4cee4-130">4096</span><span class="sxs-lookup"><span data-stu-id="4cee4-130">4096</span></span>                      |
| `$MaximumHistoryCount`           | <span data-ttu-id="4cee4-131">4096</span><span class="sxs-lookup"><span data-stu-id="4cee4-131">4096</span></span>                      |
| `$MaximumVariableCount`          | <span data-ttu-id="4cee4-132">4096</span><span class="sxs-lookup"><span data-stu-id="4cee4-132">4096</span></span>                      |
| `$OFS`                           | <span data-ttu-id="4cee4-133"> (空白字元 (`" "`) # A3</span><span class="sxs-lookup"><span data-stu-id="4cee4-133">(Space character (`" "`))</span></span> |
| `$OutputEncoding`                | <span data-ttu-id="4cee4-134">**ASCIIEncoding** 物件</span><span class="sxs-lookup"><span data-stu-id="4cee4-134">**ASCIIEncoding** object</span></span>  |
| `$ProgressPreference`            | <span data-ttu-id="4cee4-135">繼續</span><span class="sxs-lookup"><span data-stu-id="4cee4-135">Continue</span></span>                  |
| `$PSDefaultParameterValues`      | <span data-ttu-id="4cee4-136"> (無-空白雜湊表) </span><span class="sxs-lookup"><span data-stu-id="4cee4-136">(None - empty hash table)</span></span> |
| `$PSEmailServer`                 | <span data-ttu-id="4cee4-137">(無)</span><span class="sxs-lookup"><span data-stu-id="4cee4-137">(None)</span></span>                    |
| `$PSModuleAutoLoadingPreference` | <span data-ttu-id="4cee4-138">全部</span><span class="sxs-lookup"><span data-stu-id="4cee4-138">All</span></span>                       |
| `$PSSessionApplicationName`      | <span data-ttu-id="4cee4-139">wsman</span><span class="sxs-lookup"><span data-stu-id="4cee4-139">wsman</span></span>                     |
| `$PSSessionConfigurationName`    | `http://schemas.microsoft.com/powershell/Microsoft.PowerShell` |
| `$PSSessionOption`               | <span data-ttu-id="4cee4-140">請參閱 [$PSSessionOption](#pssessionoption)</span><span class="sxs-lookup"><span data-stu-id="4cee4-140">See [$PSSessionOption](#pssessionoption)</span></span> |
| `$Transcript`                    | <span data-ttu-id="4cee4-141">(無)</span><span class="sxs-lookup"><span data-stu-id="4cee4-141">(none)</span></span>                    |
| `$VerbosePreference`             | <span data-ttu-id="4cee4-142">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="4cee4-142">SilentlyContinue</span></span>          |
| `$WarningPreference`             | <span data-ttu-id="4cee4-143">Continue</span><span class="sxs-lookup"><span data-stu-id="4cee4-143">Continue</span></span>                  |
| `$WhatIfPreference`              | <span data-ttu-id="4cee4-144">False</span><span class="sxs-lookup"><span data-stu-id="4cee4-144">False</span></span>                     |

<span data-ttu-id="4cee4-145">PowerShell 包含下列儲存使用者喜好設定的環境變數。</span><span class="sxs-lookup"><span data-stu-id="4cee4-145">PowerShell includes the following environment variables that store user preferences.</span></span> <span data-ttu-id="4cee4-146">如需這些環境變數的詳細資訊，請參閱 [about_Environment_Variables](about_Environment_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-146">For more information about these environment variables, see [about_Environment_Variables](about_Environment_Variables.md).</span></span>

- `env:PSExecutionPolicyPreference`
- `$env:PSModulePath`

> [!NOTE]
> <span data-ttu-id="4cee4-147">喜好設定變數的變更只會在腳本和函式中生效（如果這些腳本或函式定義所在的範圍與使用喜好設定的範圍相同）。</span><span class="sxs-lookup"><span data-stu-id="4cee4-147">Changes to preference variable only take effect in scripts and functions if those scripts or functions are defined in the same scope as the scope in which preference was used.</span></span> <span data-ttu-id="4cee4-148">如需詳細資訊，請參閱 [about_Scopes](about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-148">For more information, see [about_Scopes](about_Scopes.md).</span></span>

## <a name="working-with-preference-variables"></a><span data-ttu-id="4cee4-149">使用喜好設定變數</span><span class="sxs-lookup"><span data-stu-id="4cee4-149">Working with preference variables</span></span>

<span data-ttu-id="4cee4-150">本檔說明每個喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="4cee4-150">This document describes each of the preference variables.</span></span>

<span data-ttu-id="4cee4-151">若要顯示特定喜好設定變數的目前值，請輸入變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="4cee4-151">To display the current value of a specific preference variable, type the variable's name.</span></span> <span data-ttu-id="4cee4-152">例如，下列命令會顯示 `$ConfirmPreference` 變數的值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-152">For example, the following command displays the `$ConfirmPreference` variable's value.</span></span>

```powershell
 $ConfirmPreference
```

```Output
High
```

<span data-ttu-id="4cee4-153">若要變更變數的值，請使用指派語句。</span><span class="sxs-lookup"><span data-stu-id="4cee4-153">To change a variable's value, use an assignment statement.</span></span> <span data-ttu-id="4cee4-154">例如，下列語句會將 `$ConfirmPreference` 參數的值變更為 **Medium** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-154">For example, the following statement changes the `$ConfirmPreference` parameter's value to **Medium** .</span></span>

```powershell
$ConfirmPreference = "Medium"
```

<span data-ttu-id="4cee4-155">您所設定的值是目前 PowerShell 會話的特定值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-155">The values that you set are specific to the current PowerShell session.</span></span> <span data-ttu-id="4cee4-156">若要讓變數在所有 PowerShell 會話中都有效，請將它們新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="4cee4-156">To make variables effective in all PowerShell sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="4cee4-157">如需詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-157">For more information, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="working-remotely"></a><span data-ttu-id="4cee4-158">從遠端工作</span><span class="sxs-lookup"><span data-stu-id="4cee4-158">Working remotely</span></span>

<span data-ttu-id="4cee4-159">當您在遠端電腦上執行命令時，遠端命令僅受限於遠端電腦的 PowerShell 用戶端中設定的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-159">When you run commands on a remote computer, the remote commands are only subject to the preferences set in the remote computer's PowerShell client.</span></span> <span data-ttu-id="4cee4-160">例如，當您執行遠端命令時，遠端電腦的變數值會 `$DebugPreference` 決定 PowerShell 如何回應偵錯工具訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-160">For example, when you run a remote command, the value of the remote computer's `$DebugPreference` variable determines how PowerShell responds to debugging messages.</span></span>

<span data-ttu-id="4cee4-161">如需遠端命令的詳細資訊，請參閱 [about_Remote](about_Remote.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-161">For more information about remote commands, see [about_Remote](about_Remote.md).</span></span>

### <a name="confirmpreference"></a><span data-ttu-id="4cee4-162">\$ConfirmPreference</span><span class="sxs-lookup"><span data-stu-id="4cee4-162">\$ConfirmPreference</span></span>

<span data-ttu-id="4cee4-163">判斷 PowerShell 是否會在執行 Cmdlet 或函式之前，自動提示您進行確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-163">Determines whether PowerShell automatically prompts you for confirmation before running a cmdlet or function.</span></span>

<span data-ttu-id="4cee4-164">`$ConfirmPreference`變數的有效值為 [ **高** ]、[ **中** ] 或 [ **低** ]。</span><span class="sxs-lookup"><span data-stu-id="4cee4-164">The `$ConfirmPreference` variable's valid values are **High** , **Medium** , or **Low** .</span></span> <span data-ttu-id="4cee4-165">Cmdlet 和函式會被指派 **高** 、 **中** 或 **低** 的風險。</span><span class="sxs-lookup"><span data-stu-id="4cee4-165">Cmdlets and functions are assigned a risk of **High** , **Medium** , or **Low** .</span></span> <span data-ttu-id="4cee4-166">當變數的值 `$ConfirmPreference` 小於或等於指派給 Cmdlet 或函式的風險時，PowerShell 會在執行 Cmdlet 或函式之前，自動提示您進行確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-166">When the value of the `$ConfirmPreference` variable is less than or equal to the risk assigned to a cmdlet or function, PowerShell automatically prompts you for confirmation before running the cmdlet or function.</span></span>

<span data-ttu-id="4cee4-167">如果變數的值 `$ConfirmPreference` 為 **None** ，則 PowerShell 永遠不會在執行 Cmdlet 或函式之前自動提示您。</span><span class="sxs-lookup"><span data-stu-id="4cee4-167">If the value of the `$ConfirmPreference` variable is **None** , PowerShell never automatically prompts you before running a cmdlet or function.</span></span>

<span data-ttu-id="4cee4-168">若要變更會話中所有 Cmdlet 和函式的確認行為，請變更 `$ConfirmPreference` 變數的值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-168">To change the confirming behavior for all cmdlets and functions in the session, change `$ConfirmPreference` variable's value.</span></span>

<span data-ttu-id="4cee4-169">若要覆寫 `$ConfirmPreference` 單一命令的，請使用 Cmdlet 或函式的 **Confirm** 參數。</span><span class="sxs-lookup"><span data-stu-id="4cee4-169">To override the `$ConfirmPreference` for a single command, use a cmdlet's or function's **Confirm** parameter.</span></span> <span data-ttu-id="4cee4-170">若要要求確認，請使用 `-Confirm` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-170">To request confirmation, use `-Confirm`.</span></span> <span data-ttu-id="4cee4-171">若要隱藏確認，請使用 `-Confirm:$false` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-171">To suppress confirmation, use `-Confirm:$false`.</span></span>

<span data-ttu-id="4cee4-172">有效的值 `$ConfirmPreference` ：</span><span class="sxs-lookup"><span data-stu-id="4cee4-172">Valid values of `$ConfirmPreference`:</span></span>

- <span data-ttu-id="4cee4-173">**無** ： PowerShell 不會自動提示。</span><span class="sxs-lookup"><span data-stu-id="4cee4-173">**None** : PowerShell doesn't prompt automatically.</span></span> <span data-ttu-id="4cee4-174">若要要求確認特定的命令，請使用 Cmdlet 或函式的 **Confirm** 參數。</span><span class="sxs-lookup"><span data-stu-id="4cee4-174">To request confirmation of a particular command, use the **Confirm** parameter of the cmdlet or function.</span></span>
- <span data-ttu-id="4cee4-175">**低** ： PowerShell 在執行具有低、中或高風險的 Cmdlet 或函式之前，會先提示確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-175">**Low** : PowerShell prompts for confirmation before running cmdlets or functions with a low, medium, or high risk.</span></span>
- <span data-ttu-id="4cee4-176">**媒體** ： PowerShell 在執行具有中或高風險的 Cmdlet 或函式之前，會先提示確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-176">**Medium** : PowerShell prompts for confirmation before running cmdlets or functions with a medium, or high risk.</span></span>
- <span data-ttu-id="4cee4-177">**高** ： PowerShell 在執行具有高風險的 Cmdlet 或函式之前，會先提示確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-177">**High** : PowerShell prompts for confirmation before running cmdlets or functions with a high risk.</span></span>

#### <a name="detailed-explanation"></a><span data-ttu-id="4cee4-178">詳細說明</span><span class="sxs-lookup"><span data-stu-id="4cee4-178">Detailed explanation</span></span>

<span data-ttu-id="4cee4-179">PowerShell 會在執行動作之前自動提示您進行確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-179">PowerShell can automatically prompt you for confirmation before doing an action.</span></span> <span data-ttu-id="4cee4-180">例如，當 Cmdlet 或函式大幅影響系統來刪除資料或使用大量系統資源時。</span><span class="sxs-lookup"><span data-stu-id="4cee4-180">For example, when cmdlet or function significantly affects the system to delete data or use a significant amount of system resources.</span></span>

```powershell
Remove-Item -Path C:\file.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\file.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"):
```

<span data-ttu-id="4cee4-181">風險預估是 Cmdlet 或函式的屬性，稱為其 **ConfirmImpact** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-181">The estimate of the risk is an attribute of the cmdlet or function known as its **ConfirmImpact** .</span></span> <span data-ttu-id="4cee4-182">使用者無法變更它。</span><span class="sxs-lookup"><span data-stu-id="4cee4-182">Users can't change it.</span></span>

<span data-ttu-id="4cee4-183">可能會對系統造成風險的 Cmdlet 和函式有一個 **Confirm** 參數，可讓您用來要求或隱藏單一命令的確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-183">Cmdlets and functions that might pose a risk to the system have a **Confirm** parameter that you can use to request or suppress confirmation for a single command.</span></span>

<span data-ttu-id="4cee4-184">因為大部分的 Cmdlet 和函式使用預設的風險值 **ConfirmImpact** ，而預設值為 High **，** 所以 `$ConfirmPreference` 很 **High** 少會發生自動確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-184">Because most cmdlets and functions use the default risk value, **ConfirmImpact** , of **Medium** , and the default value of `$ConfirmPreference` is **High** , automatic confirmation rarely occurs.</span></span> <span data-ttu-id="4cee4-185">不過，您可以藉由將的值變更為 [ `$ConfirmPreference` **中** ] 或 [ **低** ]，來啟用自動確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-185">However, you can activate automatic confirmation by changing the value of `$ConfirmPreference` to **Medium** or **Low** .</span></span>

#### <a name="examples"></a><span data-ttu-id="4cee4-186">範例</span><span class="sxs-lookup"><span data-stu-id="4cee4-186">Examples</span></span>

<span data-ttu-id="4cee4-187">此範例顯示 `$ConfirmPreference` 變數的預設值（ **High** ）效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-187">This example shows the effect of the `$ConfirmPreference` variable's default value, **High** .</span></span> <span data-ttu-id="4cee4-188">最 **高** 值只會確認高風險的 Cmdlet 和函式。</span><span class="sxs-lookup"><span data-stu-id="4cee4-188">The **High** value only confirms high-risk cmdlets and functions.</span></span> <span data-ttu-id="4cee4-189">因為大部分的 Cmdlet 和函式都是中度風險，所以不會自動確認並 `Remove-Item` 刪除該檔案。</span><span class="sxs-lookup"><span data-stu-id="4cee4-189">Since most cmdlets and functions are medium risk, they aren't automatically confirmed and `Remove-Item` deletes the file.</span></span> <span data-ttu-id="4cee4-190">新增 `-Confirm` 至命令會提示使用者進行確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-190">Adding `-Confirm` to the command prompts the user for confirmation.</span></span>

```powershell
$ConfirmPreference
```

```Output
High
```

```powershell
Remove-Item -Path C:\temp1.txt
```

<span data-ttu-id="4cee4-191">用 `-Confirm` 來要求確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-191">Use `-Confirm` to request confirmation.</span></span>

```powershell
Remove-Item -Path C:\temp2.txt -Confirm
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

<span data-ttu-id="4cee4-192">下列範例顯示將值變更 `$ConfirmPreference` 為 **Medium** 的效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-192">The following example shows the effect of changing the value of `$ConfirmPreference` to **Medium** .</span></span> <span data-ttu-id="4cee4-193">因為大部分的 Cmdlet 和函式都是中度風險，所以會自動確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-193">Because most cmdlets and function are medium risk, they're automatically confirmed.</span></span> <span data-ttu-id="4cee4-194">若要隱藏單一命令的確認提示，請使用的 **Confirm** 參數值為 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-194">To suppress the confirmation prompt for a single command, use the **Confirm** parameter with a value of `$false`.</span></span>

```powershell
$ConfirmPreference = "Medium"
Remove-Item -Path C:\temp2.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

```powershell
Remove-Item -Path C:\temp3.txt -Confirm:$false
```

### <a name="debugpreference"></a><span data-ttu-id="4cee4-195">\$DebugPreference</span><span class="sxs-lookup"><span data-stu-id="4cee4-195">\$DebugPreference</span></span>

<span data-ttu-id="4cee4-196">決定 PowerShell 如何回應腳本、Cmdlet 或提供者所產生的訊息，或命令列中的 `Write-Debug` 命令。</span><span class="sxs-lookup"><span data-stu-id="4cee4-196">Determines how PowerShell responds to debugging messages generated by a script, cmdlet or provider, or by a `Write-Debug` command at the command line.</span></span>

<span data-ttu-id="4cee4-197">某些 Cmdlet 會顯示偵錯工具，通常是專為程式設計人員和技術支援專業人員設計的技術訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-197">Some cmdlets display debugging messages, which are typically technical messages designed for programmers and technical support professionals.</span></span> <span data-ttu-id="4cee4-198">根據預設，不會顯示偵錯工具訊息，但是您可以藉由變更的值來顯示偵錯工具訊息 `$DebugPreference` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-198">By default, debugging messages aren't displayed, but you can display debugging messages by changing the value of `$DebugPreference`.</span></span>

<span data-ttu-id="4cee4-199">您可以使用 Cmdlet 的 **Debug** 一般參數來顯示或隱藏特定命令的偵錯工具訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-199">You can use the **Debug** common parameter of a cmdlet to display or hide the debugging messages for a specific command.</span></span> <span data-ttu-id="4cee4-200">如需詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-200">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="4cee4-201">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="4cee4-201">The valid values are as follows:</span></span>

- <span data-ttu-id="4cee4-202">**停止** ：顯示 debug 訊息並停止執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-202">**Stop** : Displays the debug message and stops executing.</span></span> <span data-ttu-id="4cee4-203">將錯誤寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="4cee4-203">Writes an error to the console.</span></span>
- <span data-ttu-id="4cee4-204">**Inquire** ：顯示 debug 訊息，並詢問您是否要繼續。</span><span class="sxs-lookup"><span data-stu-id="4cee4-204">**Inquire** : Displays the debug message and asks you whether you want to continue.</span></span> <span data-ttu-id="4cee4-205">將 **Debug** 一般參數加入至命令，當命令設定為產生偵錯工具訊息時，會將變數的值變更 `$DebugPreference` 為 **Inquire** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-205">Adding the **Debug** common parameter to a command, when the command is configured to generate a debugging message, changes the value of the `$DebugPreference` variable to **Inquire** .</span></span>
- <span data-ttu-id="4cee4-206">**繼續** ：顯示 debug 訊息，並繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-206">**Continue** : Displays the debug message and continues with execution.</span></span>
- <span data-ttu-id="4cee4-207">**SilentlyContinue** ： (預設) 沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="4cee4-207">**SilentlyContinue** : (Default) No effect.</span></span> <span data-ttu-id="4cee4-208">調試訊息不會顯示，而且會繼續執行而不會中斷。</span><span class="sxs-lookup"><span data-stu-id="4cee4-208">The debug message isn't displayed and execution continues without interruption.</span></span>

#### <a name="examples"></a><span data-ttu-id="4cee4-209">範例</span><span class="sxs-lookup"><span data-stu-id="4cee4-209">Examples</span></span>

<span data-ttu-id="4cee4-210">下列範例顯示在 `$DebugPreference` `Write-Debug` 命令列輸入命令時，變更值的效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-210">The following examples show the effect of changing the values of `$DebugPreference` when a `Write-Debug` command is entered at the command line.</span></span>
<span data-ttu-id="4cee4-211">這項變更會影響所有的偵錯工具訊息，包括 Cmdlet 和腳本所產生的訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-211">The change affects all debugging messages, including messages generated by cmdlets and scripts.</span></span> <span data-ttu-id="4cee4-212">這些範例會顯示 **Debug** 參數，該參數會顯示或隱藏與單一命令相關的調試訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-212">The examples show the **Debug** parameter, which displays or hides the debugging messages related to a single command.</span></span>

<span data-ttu-id="4cee4-213">此範例顯示 `$DebugPreference` 變數預設值 **SilentlyContinue** 的效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-213">This example shows the effect of the `$DebugPreference` variable's default value, **SilentlyContinue** .</span></span> <span data-ttu-id="4cee4-214">依預設， `Write-Debug` 不會顯示 Cmdlet 的偵錯工具訊息，而且會繼續處理。</span><span class="sxs-lookup"><span data-stu-id="4cee4-214">By default, the `Write-Debug` cmdlet's debug message isn't displayed and processing continues.</span></span> <span data-ttu-id="4cee4-215">使用 **Debug** 參數時，它會覆寫單一命令的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-215">When the **Debug** parameter is used, it overrides the preference for a single command.</span></span> <span data-ttu-id="4cee4-216">系統會提示使用者進行確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-216">The user is prompted for confirmation.</span></span>

```powershell
$DebugPreference
```

```Output
SilentlyContinue
```

```powershell
Write-Debug -Message "Hello, World"
```

```powershell
Write-Debug -Message "Hello, World" -Debug
```

```Output
DEBUG: Hello, World
Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend
[?] Help (default is "Y"):
```

<span data-ttu-id="4cee4-217">此範例顯示 `$DebugPreference` 使用 **Continue** 值的效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-217">This example shows the effect of `$DebugPreference` with the **Continue** value.</span></span> <span data-ttu-id="4cee4-218">隨即會顯示偵錯工具訊息，並繼續處理命令。</span><span class="sxs-lookup"><span data-stu-id="4cee4-218">The debug message is displayed and the command continues to process.</span></span>

```powershell
$DebugPreference = "Continue"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
```

<span data-ttu-id="4cee4-219">此範例使用 **Debug** 參數搭配的值 `$false` 來抑制單一命令的訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-219">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="4cee4-220">不會顯示調試訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-220">The debug message isn't displayed.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

<span data-ttu-id="4cee4-221">此範例顯示 `$DebugPreference` 設定為 **Stop** 值的效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-221">This example shows the effect of `$DebugPreference` being set to the **Stop** value.</span></span> <span data-ttu-id="4cee4-222">隨即會顯示偵錯工具訊息並停止命令。</span><span class="sxs-lookup"><span data-stu-id="4cee4-222">The debug message is displayed and the command is stopped.</span></span>

```powershell
$DebugPreference = "Stop"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
Write-Debug : The running command stopped because the preference variable
 "DebugPreference" or common parameter is set to Stop: Hello, World
At line:1 char:1
+ Write-Debug -Message "Hello, World"
```

<span data-ttu-id="4cee4-223">此範例使用 **Debug** 參數搭配的值 `$false` 來抑制單一命令的訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-223">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="4cee4-224">不會顯示 debug 訊息，也不會停止處理。</span><span class="sxs-lookup"><span data-stu-id="4cee4-224">The debug message isn't displayed and processing isn't stopped.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

<span data-ttu-id="4cee4-225">此範例顯示 `$DebugPreference` 設定為 **Inquire** 值的效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-225">This example shows the effect of `$DebugPreference` being set to the **Inquire** value.</span></span> <span data-ttu-id="4cee4-226">隨即會顯示偵錯工具訊息，並提示使用者進行確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-226">The debug message is displayed and the user is prompted for confirmation.</span></span>

```powershell
$DebugPreference = "Inquire"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend
[?] Help (default is "Y"):
```

<span data-ttu-id="4cee4-227">此範例使用 **Debug** 參數搭配的值 `$false` 來抑制單一命令的訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-227">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="4cee4-228">調試訊息不會顯示，而且會繼續處理。</span><span class="sxs-lookup"><span data-stu-id="4cee4-228">The debug message isn't displayed and processing continues.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

### <a name="erroractionpreference"></a><span data-ttu-id="4cee4-229">\$ErrorActionPreference</span><span class="sxs-lookup"><span data-stu-id="4cee4-229">\$ErrorActionPreference</span></span>

<span data-ttu-id="4cee4-230">判斷 PowerShell 如何回應非終止錯誤，這是不會停止 Cmdlet 處理的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cee4-230">Determines how PowerShell responds to a non-terminating error, an error that doesn't stop the cmdlet processing.</span></span> <span data-ttu-id="4cee4-231">例如，在命令列或腳本、Cmdlet 或提供者中，例如 Cmdlet 所產生的錯誤 `Write-Error` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-231">For example, at the command line or in a script, cmdlet, or provider, such as the errors generated by the `Write-Error` cmdlet.</span></span>

<span data-ttu-id="4cee4-232">您可以使用 Cmdlet 的 **ErrorAction** 一般參數覆寫特定命令的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-232">You can use a cmdlet's **ErrorAction** common parameter to override the preference for a specific command.</span></span>

<span data-ttu-id="4cee4-233">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="4cee4-233">The valid values are as follows:</span></span>

- <span data-ttu-id="4cee4-234">**繼續** ： (預設) 顯示錯誤訊息，並繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-234">**Continue** : (Default) Displays the error message and continues executing.</span></span>
- <span data-ttu-id="4cee4-235">**Ignore** ：抑制錯誤訊息，並繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="4cee4-235">**Ignore** : Suppresses the error message and continues to execute the command.</span></span> <span data-ttu-id="4cee4-236">**Ignore** 值適用于每個命令使用，不是用來做為儲存的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-236">The **Ignore** value is intended for per-command use, not for use as saved preference.</span></span> <span data-ttu-id="4cee4-237">**Ignore** 對變數而言不是有效的值 `$ErrorActionPreference` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-237">**Ignore** isn't a valid value for the `$ErrorActionPreference` variable.</span></span>
- <span data-ttu-id="4cee4-238">**查詢** ：顯示錯誤訊息，並詢問您是否要繼續。</span><span class="sxs-lookup"><span data-stu-id="4cee4-238">**Inquire** : Displays the error message and asks you whether you want to continue.</span></span>
- <span data-ttu-id="4cee4-239">**SilentlyContinue** ：無效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-239">**SilentlyContinue** : No effect.</span></span> <span data-ttu-id="4cee4-240">不會顯示錯誤訊息，且會繼續執行而不會中斷。</span><span class="sxs-lookup"><span data-stu-id="4cee4-240">The error message isn't displayed and execution continues without interruption.</span></span>
- <span data-ttu-id="4cee4-241">**停止** ：顯示錯誤訊息並停止執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-241">**Stop** : Displays the error message and stops executing.</span></span> <span data-ttu-id="4cee4-242">除了產生的錯誤之外， **Stop** 值也會產生 ActionPreferenceStopException 物件至錯誤資料流程。</span><span class="sxs-lookup"><span data-stu-id="4cee4-242">In addition to the error generated, the **Stop** value generates an ActionPreferenceStopException object to the error stream.</span></span>
  <span data-ttu-id="4cee4-243">資料流</span><span class="sxs-lookup"><span data-stu-id="4cee4-243">stream</span></span>
- <span data-ttu-id="4cee4-244">**暫** 止：自動暫停工作流程工作以允許進一步調查。</span><span class="sxs-lookup"><span data-stu-id="4cee4-244">**Suspend** : Automatically suspends a workflow job to allow for further investigation.</span></span> <span data-ttu-id="4cee4-245">經過調查之後，即可繼續工作流程。</span><span class="sxs-lookup"><span data-stu-id="4cee4-245">After investigation, the workflow can be resumed.</span></span> <span data-ttu-id="4cee4-246">「 **暫停** 」值適用于每個命令使用，不是用來做為儲存的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-246">The **Suspend** value is intended for per-command use, not for use as saved preference.</span></span> <span data-ttu-id="4cee4-247">**暫** 止不是有效的 `$ErrorActionPreference` 變數值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-247">**Suspend** isn't a valid value for the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="4cee4-248">`$ErrorActionPreference` 而 **ErrorAction** 參數不會影響 PowerShell 如何回應停止 Cmdlet 處理的終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cee4-248">`$ErrorActionPreference` and the **ErrorAction** parameter don't affect how PowerShell responds to terminating errors that stop cmdlet processing.</span></span> <span data-ttu-id="4cee4-249">如需 **ErrorAction** 一般參數的詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-249">For more information about the **ErrorAction** common parameter, see [about_CommonParameters](about_CommonParameters.md).</span></span>

#### <a name="examples"></a><span data-ttu-id="4cee4-250">範例</span><span class="sxs-lookup"><span data-stu-id="4cee4-250">Examples</span></span>

<span data-ttu-id="4cee4-251">這些範例顯示變數不同值的效果 `$ErrorActionPreference` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-251">These examples show the effect of the different values of the `$ErrorActionPreference` variable.</span></span> <span data-ttu-id="4cee4-252">**ErrorAction** 參數是用來覆寫 `$ErrorActionPreference` 值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-252">The **ErrorAction** parameter is used to override the `$ErrorActionPreference` value.</span></span>

<span data-ttu-id="4cee4-253">此範例會顯示 `$ErrorActionPreference` 預設值 [ **繼續** ]。</span><span class="sxs-lookup"><span data-stu-id="4cee4-253">This example shows the `$ErrorActionPreference` default value, **Continue** .</span></span> <span data-ttu-id="4cee4-254">產生非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cee4-254">A non-terminating error is generated.</span></span> <span data-ttu-id="4cee4-255">訊息隨即顯示，並且繼續處理。</span><span class="sxs-lookup"><span data-stu-id="4cee4-255">The message is displayed and processing continues.</span></span>

```powershell
# Change the ErrorActionPreference to 'Continue'
$ErrorActionPreference = 'Continue'
# Generate a non-terminating error and continue processing the script.
Write-Error -Message  'Test Error' ; Write-Host 'Hello World'
```

```Output
Write-Error -Message  'Test Error' ; Write-Host 'Hello World' : Test Error
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

Hello World
```

<span data-ttu-id="4cee4-256">此範例顯示 `$ErrorActionPreference` 預設值： **Inquire** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-256">This example shows the `$ErrorActionPreference` default value, **Inquire** .</span></span> <span data-ttu-id="4cee4-257">系統會產生錯誤，並顯示提示動作。</span><span class="sxs-lookup"><span data-stu-id="4cee4-257">An error is generated and a prompt for action is shown.</span></span>

```powershell
# Change the ErrorActionPreference to 'Inquire'
$ErrorActionPreference = 'Inquire'
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
```

```Output
Confirm
Test Error
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="4cee4-258">這個範例會示範 `$ErrorActionPreference` 要 **SilentlyContinue** 的設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-258">This example shows the `$ErrorActionPreference` set to **SilentlyContinue** .</span></span>
<span data-ttu-id="4cee4-259">會隱藏錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-259">The error message is suppressed.</span></span>

```powershell
# Change the ErrorActionPreference to 'SilentlyContinue'
$ErrorActionPreference = 'SilentlyContinue'
# Generate an error message
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
# Error message is suppressed and script continues processing
```

```Output
Hello World
```

<span data-ttu-id="4cee4-260">這個範例會顯示 `$ErrorActionPreference` 要 **停止** 的設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-260">This example shows the `$ErrorActionPreference` set to **Stop** .</span></span> <span data-ttu-id="4cee4-261">它也會顯示為變數產生的額外物件 `$Error` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-261">It also shows the extra object generated to the `$Error` variable.</span></span>

```powershell
# Change the ErrorActionPreference to 'Stop'
$ErrorActionPreference = 'Stop'
# Error message is is generated and script stops processing
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'

# Show the ActionPreferenceStopException and the error generated
$Error[0]
$Error[1]
```

```Output
Write-Error -Message 'Test Error' ; Write-Host 'Hello World' : Test Error
At line:1 char:1
+ Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

The running command stopped because the preference variable "ErrorActionPreference"
or common parameter is set to Stop: Test Error

Write-Error -Message 'Test Error' ; Write-Host 'Hello World' : Test Error
At line:1 char:1
+ Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

### <a name="errorview"></a><span data-ttu-id="4cee4-262">\$ErrorView</span><span class="sxs-lookup"><span data-stu-id="4cee4-262">\$ErrorView</span></span>

<span data-ttu-id="4cee4-263">決定 PowerShell 中錯誤訊息的顯示格式。</span><span class="sxs-lookup"><span data-stu-id="4cee4-263">Determines the display format of error messages in PowerShell.</span></span>

<span data-ttu-id="4cee4-264">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="4cee4-264">The valid values are as follows:</span></span>

- <span data-ttu-id="4cee4-265">**NormalView** ： (預設) 為大部分的使用者設計的詳細觀點。</span><span class="sxs-lookup"><span data-stu-id="4cee4-265">**NormalView** : (Default) A detailed view designed for most users.</span></span> <span data-ttu-id="4cee4-266">包含錯誤的描述，以及包含在錯誤中的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="4cee4-266">Consists of a description of the error and the name of the object involved in the error.</span></span>
- <span data-ttu-id="4cee4-267">**CategoryView** ：專為生產環境所設計的簡潔結構化視圖。</span><span class="sxs-lookup"><span data-stu-id="4cee4-267">**CategoryView** : A succinct, structured view designed for production environments.</span></span> <span data-ttu-id="4cee4-268">其格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="4cee4-268">The format is as follows:</span></span>

  <span data-ttu-id="4cee4-269">{Category}： ( {TargetName}： {TargetType} ) ： [{Activity}]，{Reason}</span><span class="sxs-lookup"><span data-stu-id="4cee4-269">{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}</span></span>

<span data-ttu-id="4cee4-270">如需 **CategoryView** 中欄位的詳細資訊，請參閱 [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) 類別。</span><span class="sxs-lookup"><span data-stu-id="4cee4-270">For more information about the fields in **CategoryView** , see [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) class.</span></span>

#### <a name="examples"></a><span data-ttu-id="4cee4-271">範例</span><span class="sxs-lookup"><span data-stu-id="4cee4-271">Examples</span></span>

<span data-ttu-id="4cee4-272">這個範例示範當的值 `$ErrorView` 是預設的 **NormalView** 時，如何顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cee4-272">This example shows how an error appears when the value of `$ErrorView` is the default, **NormalView** .</span></span> <span data-ttu-id="4cee4-273">`Get-ChildItem` 用來尋找不存在的檔案。</span><span class="sxs-lookup"><span data-stu-id="4cee4-273">`Get-ChildItem` is used to find a non-existent file.</span></span>

```powershell
Get-ChildItem -Path C:\nofile.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\nofile.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path C:\nofile.txt
```

<span data-ttu-id="4cee4-274">這個範例示範當的值 `$ErrorView` 變更為 **CategoryView** 時，會如何顯示相同的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cee4-274">This example shows how the same error appears when the value of `$ErrorView` is changed to **CategoryView** .</span></span>

```powershell
$ErrorView = "CategoryView"
Get-ChildItem -Path C:\nofile.txt
```

```Output
ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem], ItemNotFoundException
```

<span data-ttu-id="4cee4-275">這個範例示範的值 `$ErrorView` 只會影響錯誤顯示。</span><span class="sxs-lookup"><span data-stu-id="4cee4-275">This example demonstrates that the value of `$ErrorView` only affects the error display.</span></span> <span data-ttu-id="4cee4-276">它不會變更儲存在自動變數中之錯誤物件的結構 `$Error` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-276">It doesn't change the structure of the error object that is stored in the `$Error` automatic variable.</span></span> <span data-ttu-id="4cee4-277">如需自動變數的相關資訊 `$Error` ，請參閱 [about_automatic_variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-277">For information about the `$Error` automatic variable, see [about_automatic_variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="4cee4-278">下列命令會使用與錯誤陣列（專案 **0** ）中最新錯誤相關聯的 **ErrorRecord** 物件，並將所有錯誤物件的屬性格式化為清單中的所有錯誤物件。</span><span class="sxs-lookup"><span data-stu-id="4cee4-278">The following command takes the **ErrorRecord** object associated with the most recent error in the error array, **element 0** , and formats all the error object's properties in a list.</span></span>

```powershell
$Error[0] | Format-List -Property * -Force
```

```Output
PSMessageDetails      :
Exception             : System.Management.Automation.ItemNotFoundException:
                          Cannot find path 'C:\nofile.txt' because it does
                          not exist.
                        at System.Management.Automation.SessionStateInternal.
                          GetChildItems(String path, Boolean recurse, UInt32
                          depth, CmdletProviderContext context)
                        at System.Management.Automation.ChildItemCmdlet
                          ProviderIntrinsics.Get(String path, Boolean
                          recurse, UInt32 depth, CmdletProviderContext context)
                        at Microsoft.PowerShell.Commands.GetChildItemCommand.
                          ProcessRecord()
TargetObject          : C:\nofile.txt
CategoryInfo          : ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem],
                          ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,
                          Microsoft.PowerShell.Commands.GetChildItemCommand
ErrorDetails          :
InvocationInfo        : System.Management.Automation.InvocationInfo
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo : {0, 1}
```

### <a name="formatenumerationlimit"></a><span data-ttu-id="4cee4-279">\$FormatEnumerationLimit</span><span class="sxs-lookup"><span data-stu-id="4cee4-279">\$FormatEnumerationLimit</span></span>

<span data-ttu-id="4cee4-280">決定顯示中包含多少列舉專案。</span><span class="sxs-lookup"><span data-stu-id="4cee4-280">Determines how many enumerated items are included in a display.</span></span> <span data-ttu-id="4cee4-281">此變數不會影響基礎物件，只會影響顯示。</span><span class="sxs-lookup"><span data-stu-id="4cee4-281">This variable doesn't affect the underlying objects, only the display.</span></span> <span data-ttu-id="4cee4-282">當的值 `$FormatEnumerationLimit` 少於列舉的專案數目時，PowerShell 會新增省略號 (`...`) 來指出未顯示的專案。</span><span class="sxs-lookup"><span data-stu-id="4cee4-282">When the value of `$FormatEnumerationLimit` is fewer than the number of enumerated items, PowerShell adds an ellipsis (`...`) to indicate items not shown.</span></span>

<span data-ttu-id="4cee4-283">**有效的值** ：整數 (`Int32`) </span><span class="sxs-lookup"><span data-stu-id="4cee4-283">**Valid values** : Integers (`Int32`)</span></span>

<span data-ttu-id="4cee4-284">**預設值** ：4</span><span class="sxs-lookup"><span data-stu-id="4cee4-284">**Default value** : 4</span></span>

#### <a name="examples"></a><span data-ttu-id="4cee4-285">範例</span><span class="sxs-lookup"><span data-stu-id="4cee4-285">Examples</span></span>

<span data-ttu-id="4cee4-286">此範例顯示如何使用 `$FormatEnumerationLimit` 變數來改善列舉專案的顯示。</span><span class="sxs-lookup"><span data-stu-id="4cee4-286">This example shows how to use the `$FormatEnumerationLimit` variable to improve the display of enumerated items.</span></span>

<span data-ttu-id="4cee4-287">此範例中的命令會產生一份資料表，其中列出在電腦上執行的所有服務，其中有兩個群組：一個用來 **執行服務，另一個用於\*\*\*\*已停止** 的服務。</span><span class="sxs-lookup"><span data-stu-id="4cee4-287">The command in this example generates a table that lists all the services running on the computer in two groups: one for **running** services and one for **stopped** services.</span></span> <span data-ttu-id="4cee4-288">它會使用 `Get-Service` 命令來取得所有服務，然後透過管線將結果傳送至 `Group-Object` Cmdlet，此 Cmdlet 會依服務狀態將結果分組。</span><span class="sxs-lookup"><span data-stu-id="4cee4-288">It uses a `Get-Service` command to get all the services, and then sends the results through the pipeline to the `Group-Object` cmdlet, which groups the results by the service status.</span></span>

<span data-ttu-id="4cee4-289">結果是在 [ **名稱** ] 資料行中列出狀態的資料表，以及 [ **群組** ] 資料行中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="4cee4-289">The result is a table that lists the status in the **Name** column, and the processes in the **Group** column.</span></span> <span data-ttu-id="4cee4-290">若要變更資料行標籤，請使用雜湊表，請參閱 [about_Hash_Tables](about_Hash_Tables.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-290">To change the column labels, use a hash table, see [about_Hash_Tables](about_Hash_Tables.md).</span></span> <span data-ttu-id="4cee4-291">如需詳細資訊，請參閱 [格式資料表](xref:Microsoft.PowerShell.Utility.Format-Table)中的範例。</span><span class="sxs-lookup"><span data-stu-id="4cee4-291">For more information, see the examples in [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

<span data-ttu-id="4cee4-292">找出目前的值 `$FormatEnumerationLimit` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-292">Find the current value of `$FormatEnumerationLimit`.</span></span>

```powershell
$FormatEnumerationLimit
```

```Output
4
```

<span data-ttu-id="4cee4-293">列出依 **狀態** 分組的所有服務。</span><span class="sxs-lookup"><span data-stu-id="4cee4-293">List all services grouped by **Status** .</span></span> <span data-ttu-id="4cee4-294">每個狀態的 [ **群組** ] 資料行中最多會列出四項服務，因為的 `$FormatEnumerationLimit` 值為 **4** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-294">There are a maximum of four services listed in the **Group** column for each status because `$FormatEnumerationLimit` has a value of **4** .</span></span>

```powershell
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv...}
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart...}
```

<span data-ttu-id="4cee4-295">若要增加列出的專案數目，請將的值增加 `$FormatEnumerationLimit` 到 **1000** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-295">To increase the number of items listed, increase the value of `$FormatEnumerationLimit` to **1000** .</span></span> <span data-ttu-id="4cee4-296">使用 `Get-Service` 和 `Group-Object` 來顯示服務。</span><span class="sxs-lookup"><span data-stu-id="4cee4-296">Use `Get-Service` and `Group-Object` to display the services.</span></span>

```powershell
$FormatEnumerationLimit = 1000
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec...
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc...
```

<span data-ttu-id="4cee4-297">使用 `Format-Table` **Wrap** 參數來顯示服務清單。</span><span class="sxs-lookup"><span data-stu-id="4cee4-297">Use `Format-Table` with the **Wrap** parameter to display the list of services.</span></span>

```powershell
Get-Service | Group-Object -Property Status | Format-Table -Wrap
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec,
                  Client for NFS, CryptSvc, DcomLaunch, Dhcp, dmserver,
                  Dnscache, ERSvc, Eventlog, EventSystem, FwcAgent, helpsvc,
                  HidServ, IISADMIN, InoRPC, InoRT, InoTask, lanmanserver,
                  lanmanworkstation, LmHosts, MDM, Netlogon, Netman, Nla,
                  NtLmSsp, PlugPlay, PolicyAgent, ProtectedStorage, RasMan,
                  RemoteRegistry, RpcSs, SamSs, Schedule, seclogon, SENS,
                  SharedAccess, ShellHWDetection, SMT PSVC, Spooler,
                  srservice, SSDPSRV, stisvc, TapiSrv, TermService, Themes,
                  TrkWks, UMWdf, W32Time, W3SVC, WebClient, winmgmt, wscsvc,
                  wuauserv, WZCSVC, zzInterix}

41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc,
                  ClipSrv, clr_optimization_v2.0.50727_32, COMSysApp,
                  CronService, dmadmin, FastUserSwitchingCompatibility,
                  HTTPFilter, ImapiService, Mapsvc, Messenger, mnmsrvc,
                  MSDTC, MSIServer, msvsmon80, NetDDE, NetDDEdsdm, NtmsSvc,
                  NVSvc, ose, RasAuto, RDSessMgr, RemoteAccess, RpcLocator,
                  SCardSvr, SwPrv, SysmonLog, TlntSvr, upnphost, UPS, VSS,
                  WmdmPmSN, Wmi, WmiApSrv, xmlprov}
```

### <a name="informationpreference"></a><span data-ttu-id="4cee4-298">\$InformationPreference</span><span class="sxs-lookup"><span data-stu-id="4cee4-298">\$InformationPreference</span></span>

<span data-ttu-id="4cee4-299">`$InformationPreference`變數可讓您設定要顯示給使用者的資訊串流喜好設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-299">The `$InformationPreference` variable lets you set information stream preferences that you want displayed to users.</span></span> <span data-ttu-id="4cee4-300">具體來說，您可以藉由新增 [寫入資訊](xref:Microsoft.PowerShell.Utility.Write-Information) Cmdlet 來新增至命令或腳本的參考訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-300">Specifically, informational messages that you added to commands or scripts by adding the [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information) cmdlet.</span></span> <span data-ttu-id="4cee4-301">如果使用 **InformationAction** 參數，它的值會覆寫變數的值 `$InformationPreference` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-301">If the **InformationAction** parameter is used, its value overrides the value of the `$InformationPreference` variable.</span></span> <span data-ttu-id="4cee4-302">`Write-Information` 已在 PowerShell 5.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="4cee4-302">`Write-Information` was introduced in PowerShell 5.0.</span></span>

<span data-ttu-id="4cee4-303">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="4cee4-303">The valid values are as follows:</span></span>

- <span data-ttu-id="4cee4-304">**停止** ：在命令出現時停止命令或腳本 `Write-Information` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-304">**Stop** : Stops a command or script at an occurrence of the `Write-Information` command.</span></span>
- <span data-ttu-id="4cee4-305">**Inquire** ：顯示您在命令中指定的參考用訊息 `Write-Information` ，然後詢問您是否要繼續。</span><span class="sxs-lookup"><span data-stu-id="4cee4-305">**Inquire** : Displays the informational message that you specify in a `Write-Information` command, then asks whether you want to continue.</span></span>
- <span data-ttu-id="4cee4-306">**繼續** ：顯示資訊訊息，並繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-306">**Continue** : Displays the informational message, and continues running.</span></span>
- <span data-ttu-id="4cee4-307">**暫** 止：執行命令後自動暫停工作流程工作 `Write-Information` ，以允許使用者在繼續之前查看訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-307">**Suspend** : Automatically suspends a workflow job after a `Write-Information` command is carried out, to allow users to see the messages before continuing.</span></span> <span data-ttu-id="4cee4-308">工作流程可依使用者的意願繼續。</span><span class="sxs-lookup"><span data-stu-id="4cee4-308">The workflow can be resumed at the user's discretion.</span></span>
- <span data-ttu-id="4cee4-309">**SilentlyContinue** ： (預設) 沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="4cee4-309">**SilentlyContinue** : (Default) No effect.</span></span> <span data-ttu-id="4cee4-310">不會顯示資訊訊息，腳本會繼續執行而不會中斷。</span><span class="sxs-lookup"><span data-stu-id="4cee4-310">The informational messages aren't displayed, and the script continues without interruption.</span></span>

### <a name="logevent"></a><span data-ttu-id="4cee4-311">\$記錄 \* 事件</span><span class="sxs-lookup"><span data-stu-id="4cee4-311">\$Log\*Event</span></span>

<span data-ttu-id="4cee4-312">**Log \* 事件** 喜好設定變數會決定哪些類型的事件會寫入事件檢視器中的 PowerShell 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4cee4-312">The **Log\*Event** preference variables determine which types of events are written to the PowerShell event log in Event Viewer.</span></span> <span data-ttu-id="4cee4-313">依預設，只會記錄引擎和提供者事件。</span><span class="sxs-lookup"><span data-stu-id="4cee4-313">By default, only engine and provider events are logged.</span></span> <span data-ttu-id="4cee4-314">但是，您可以使用 **log \* 事件** 喜好設定變數來自訂您的記錄檔，例如記錄有關命令的事件。</span><span class="sxs-lookup"><span data-stu-id="4cee4-314">But, you can use the **Log\*Event** preference variables to customize your log, such as logging events about commands.</span></span>

<span data-ttu-id="4cee4-315">**Log \* 事件** 喜好設定變數如下所示：</span><span class="sxs-lookup"><span data-stu-id="4cee4-315">The **Log\*Event** preference variables are as follows:</span></span>

- <span data-ttu-id="4cee4-316">`$LogCommandHealthEvent`：記錄命令初始化和處理中的錯誤和例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4cee4-316">`$LogCommandHealthEvent`: Logs errors and exceptions in command initialization and processing.</span></span> <span data-ttu-id="4cee4-317">預設值為 `$false` (不會) 記錄。</span><span class="sxs-lookup"><span data-stu-id="4cee4-317">The default is `$false` (not logged).</span></span>
- <span data-ttu-id="4cee4-318">`$LogCommandLifecycleEvent`：在命令探索中記錄命令的啟動和停止，以及命令管線和安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4cee4-318">`$LogCommandLifecycleEvent`: Logs the starting and stopping of commands and command pipelines and security exceptions in command discovery.</span></span> <span data-ttu-id="4cee4-319">預設值為 `$false` (不會) 記錄。</span><span class="sxs-lookup"><span data-stu-id="4cee4-319">The default is `$false` (not logged).</span></span>
- <span data-ttu-id="4cee4-320">`$LogEngineHealthEvent`：記錄會話的錯誤和失敗。</span><span class="sxs-lookup"><span data-stu-id="4cee4-320">`$LogEngineHealthEvent`: Logs errors and failures of sessions.</span></span> <span data-ttu-id="4cee4-321">預設值是 `$true` (記錄) 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-321">The default is `$true` (logged).</span></span>
- <span data-ttu-id="4cee4-322">`$LogEngineLifecycleEvent`：記錄會話的開啟和關閉。</span><span class="sxs-lookup"><span data-stu-id="4cee4-322">`$LogEngineLifecycleEvent`: Logs the opening and closing of sessions.</span></span> <span data-ttu-id="4cee4-323">預設值是 `$true` (記錄) 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-323">The default is `$true` (logged).</span></span>
- <span data-ttu-id="4cee4-324">`$LogProviderHealthEvent`：記錄提供者錯誤，例如讀取和寫入錯誤、查閱錯誤和調用錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cee4-324">`$LogProviderHealthEvent`: Logs provider errors, such as read and write errors, lookup errors, and invocation errors.</span></span> <span data-ttu-id="4cee4-325">預設值是 `$true` (記錄) 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-325">The default is `$true` (logged).</span></span>
- <span data-ttu-id="4cee4-326">`$LogProviderLifecycleEvent`：記錄 PowerShell 提供者的新增和移除。</span><span class="sxs-lookup"><span data-stu-id="4cee4-326">`$LogProviderLifecycleEvent`: Logs adding and removing of PowerShell providers.</span></span> <span data-ttu-id="4cee4-327">預設值是 `$true` (記錄) 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-327">The default is `$true` (logged).</span></span> <span data-ttu-id="4cee4-328">如需 PowerShell 提供者的詳細資訊，請參閱 [about_Providers](about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-328">For information about PowerShell providers, see [about_Providers](about_Providers.md).</span></span>

<span data-ttu-id="4cee4-329">若要啟用 **記錄 \* 事件** ，請輸入具有值的變數 `$true` ，例如：</span><span class="sxs-lookup"><span data-stu-id="4cee4-329">To enable a **Log\*Event** , type the variable with a value of `$true`, for example:</span></span>

```powershell
$LogCommandLifeCycleEvent = $true
```

<span data-ttu-id="4cee4-330">若要停用事件種類，請輸入值為的變數 `$false` ，例如：</span><span class="sxs-lookup"><span data-stu-id="4cee4-330">To disable an event type, type the variable with a value of `$false`, for example:</span></span>

```powershell
$LogCommandLifeCycleEvent = $false
```

<span data-ttu-id="4cee4-331">您啟用的事件只會對目前的 PowerShell 主控台有效。</span><span class="sxs-lookup"><span data-stu-id="4cee4-331">The events that you enable are effective only for the current PowerShell console.</span></span> <span data-ttu-id="4cee4-332">若要將設定套用至所有主控台，請將變數設定儲存在您的 PowerShell 設定檔中。</span><span class="sxs-lookup"><span data-stu-id="4cee4-332">To apply the configuration to all consoles, save the variable settings in your PowerShell profile.</span></span> <span data-ttu-id="4cee4-333">如需詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-333">For more information, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="maximumaliascount"></a><span data-ttu-id="4cee4-334">\$MaximumAliasCount</span><span class="sxs-lookup"><span data-stu-id="4cee4-334">\$MaximumAliasCount</span></span>

<span data-ttu-id="4cee4-335">判斷在 PowerShell 會話中允許的別名數目。</span><span class="sxs-lookup"><span data-stu-id="4cee4-335">Determines how many aliases are permitted in a PowerShell session.</span></span> <span data-ttu-id="4cee4-336">預設值為 **4096** ，而且應該足以滿足大部分的用途。</span><span class="sxs-lookup"><span data-stu-id="4cee4-336">The default value is **4096** and that should be enough for most uses.</span></span> <span data-ttu-id="4cee4-337">您可以調整 `$MaximumAliasCount` 以符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="4cee4-337">You can adjust `$MaximumAliasCount` to meet your needs.</span></span>

<span data-ttu-id="4cee4-338">**有效的值** ： 1024-32768 (`Int32`) </span><span class="sxs-lookup"><span data-stu-id="4cee4-338">**Valid values** : 1024 - 32768 (`Int32`)</span></span>

<span data-ttu-id="4cee4-339">**預設值** ：4096</span><span class="sxs-lookup"><span data-stu-id="4cee4-339">**Default** : 4096</span></span>

<span data-ttu-id="4cee4-340">若要計算您系統上的別名，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4cee4-340">To count the aliases on your system, type:</span></span>

```powershell
(Get-Alias).count
```

### <a name="maximumdrivecount"></a><span data-ttu-id="4cee4-341">\$MaximumDriveCount</span><span class="sxs-lookup"><span data-stu-id="4cee4-341">\$MaximumDriveCount</span></span>

<span data-ttu-id="4cee4-342">判斷指定的會話中允許的 PowerShell 磁片磁碟機數目。</span><span class="sxs-lookup"><span data-stu-id="4cee4-342">Determines how many PowerShell drives are permitted in a given session.</span></span> <span data-ttu-id="4cee4-343">例如，PowerShell 提供者所公開的檔案系統磁片磁碟機和資料存放區，會顯示為磁片磁碟機，例如 `Alias:` 和 `HKLM:` 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="4cee4-343">For example, file system drives and data stores that are exposed by PowerShell providers and appear as drives, such as the `Alias:` and `HKLM:` drives.</span></span>

<span data-ttu-id="4cee4-344">**有效的值** ： 1024-32768 (`Int32`) </span><span class="sxs-lookup"><span data-stu-id="4cee4-344">**Valid values** : 1024 - 32768 (`Int32`)</span></span>

<span data-ttu-id="4cee4-345">**預設值** ：4096</span><span class="sxs-lookup"><span data-stu-id="4cee4-345">**Default** : 4096</span></span>

<span data-ttu-id="4cee4-346">若要計算您系統上的別名，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4cee4-346">To count the aliases on your system, type:</span></span>

```powershell
(Get-PSDrive).count
```

### <a name="maximumerrorcount"></a><span data-ttu-id="4cee4-347">\$MaximumErrorCount</span><span class="sxs-lookup"><span data-stu-id="4cee4-347">\$MaximumErrorCount</span></span>

<span data-ttu-id="4cee4-348">決定在會話的錯誤歷程記錄中儲存多少錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cee4-348">Determines how many errors are saved in the error history for the session.</span></span>

<span data-ttu-id="4cee4-349">**有效的值** ： 256-32768 (`Int32`) </span><span class="sxs-lookup"><span data-stu-id="4cee4-349">**Valid values** : 256 - 32768 (`Int32`)</span></span>

<span data-ttu-id="4cee4-350">**預設值** ：256</span><span class="sxs-lookup"><span data-stu-id="4cee4-350">**Default** : 256</span></span>

<span data-ttu-id="4cee4-351">代表每個保留錯誤的物件會儲存在 `$Error` 自動變數中。</span><span class="sxs-lookup"><span data-stu-id="4cee4-351">Objects that represent each retained error are stored in the `$Error` automatic variable.</span></span> <span data-ttu-id="4cee4-352">`$Error` 包含錯誤記錄物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="4cee4-352">`$Error` contains an array of error record objects.</span></span> <span data-ttu-id="4cee4-353">最新的錯誤是陣列中的第一個物件 `$Error[0]` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-353">The most recent error is the first object in the array, `$Error[0]`.</span></span>

<span data-ttu-id="4cee4-354">若要計算您系統上的錯誤，請使用 `$Error` 陣列的 **count** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4cee4-354">To count the errors on your system, use the `$Error` array's **Count** property.</span></span>

```powershell
$Error.count
```

<span data-ttu-id="4cee4-355">若要顯示特定的錯誤，請使用 `[0]` 陣列標記法來查看最近的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cee4-355">To display a specific error, use the `[0]` array notation to see the most recent error.</span></span>

```powershell
$Error[0]
```

<span data-ttu-id="4cee4-356">若要顯示最舊的保留錯誤，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4cee4-356">To display the oldest retained error, type:</span></span>

```powershell
$Error[($Error.Count -1]
```

<span data-ttu-id="4cee4-357">**Force** 參數會覆寫 **ErrorRecord** 物件的特殊格式，並還原為傳統格式。</span><span class="sxs-lookup"><span data-stu-id="4cee4-357">The **Force** parameter overrides the special formatting of **ErrorRecord** objects and reverts to the conventional format.</span></span> <span data-ttu-id="4cee4-358">若要顯示 **ErrorRecord** 物件的屬性，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="4cee4-358">To display the properties of the **ErrorRecord** object, type the following command:</span></span>

```powershell
$Error[0] | Format-List -Property * -Force
```

<span data-ttu-id="4cee4-359">在此範例中，會 `$Error.Count` 顯示錯誤的數目。</span><span class="sxs-lookup"><span data-stu-id="4cee4-359">In this example, `$Error.Count` displays the number of errors.</span></span> <span data-ttu-id="4cee4-360">若要刪除錯誤記錄中的所有錯誤，請使用 `Clear` 錯誤陣列的方法。</span><span class="sxs-lookup"><span data-stu-id="4cee4-360">To delete all errors from the error history, use the `Clear` method of the error array.</span></span>

```powershell
$Error.Count
```

```Output
17
```

```powershell
$Error.Clear()
$Error.Count
```

```Output
0
```

<span data-ttu-id="4cee4-361">若要尋找錯誤陣列的所有屬性和方法，請使用 `Get-Member` Cmdlet 與其 **InputObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="4cee4-361">To find all properties and methods of an error array, use the `Get-Member` cmdlet with its **InputObject** parameter.</span></span> <span data-ttu-id="4cee4-362">當您使用 **InputObject** 參數時，會 `Get-Member` 顯示集合的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="4cee4-362">When you use the **InputObject** parameter, `Get-Member` displays the properties and methods of the collection.</span></span>

```powershell
Get-Member -InputObject $Error
```

<span data-ttu-id="4cee4-363">當您使用管線將物件集合傳送至時 `Get-Member` ，會 `Get-Member` 顯示集合中物件的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="4cee4-363">When you pipe a collection of objects to `Get-Member`, `Get-Member` displays the properties and methods of the objects in the collection.</span></span>

```powershell
$Error | Get-Member
```

### <a name="maximumfunctioncount"></a><span data-ttu-id="4cee4-364">\$MaximumFunctionCount</span><span class="sxs-lookup"><span data-stu-id="4cee4-364">\$MaximumFunctionCount</span></span>

<span data-ttu-id="4cee4-365">判斷指定的會話中允許的函數數目。</span><span class="sxs-lookup"><span data-stu-id="4cee4-365">Determines how many functions are permitted in a given session.</span></span>

<span data-ttu-id="4cee4-366">**有效的值** ： 1024-32768 (`Int32`) </span><span class="sxs-lookup"><span data-stu-id="4cee4-366">**Valid values** : 1024 - 32768 (`Int32`)</span></span>

<span data-ttu-id="4cee4-367">**預設值** ：4096</span><span class="sxs-lookup"><span data-stu-id="4cee4-367">**Default** : 4096</span></span>

<span data-ttu-id="4cee4-368">若要查看會話中的函數，請使用 `Function:` powershell 提供者所公開的 powershell 磁片磁碟機 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-368">To see the functions in your session, use the PowerShell `Function:` drive that is exposed by the PowerShell `Function` provider.</span></span> <span data-ttu-id="4cee4-369">如需提供者的詳細資訊 `Function` ，請 [about_Function_Provider](about_Function_Provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-369">For more information about the `Function` provider, [about_Function_Provider](about_Function_Provider.md).</span></span>

<span data-ttu-id="4cee4-370">若要列出目前會話中的函數，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4cee4-370">To list the functions in the current session, type:</span></span>

```powershell
Get-ChildItem Function:
```

<span data-ttu-id="4cee4-371">若要計算目前會話中的函數，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4cee4-371">To count the functions in the current session, type:</span></span>

```powershell
(Get-ChildItem Function:).Count
```

### <a name="maximumhistorycount"></a><span data-ttu-id="4cee4-372">\$MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="4cee4-372">\$MaximumHistoryCount</span></span>

<span data-ttu-id="4cee4-373">決定目前會話的命令歷程記錄中所儲存的命令數目。</span><span class="sxs-lookup"><span data-stu-id="4cee4-373">Determines how many commands are saved in the command history for the current session.</span></span>

<span data-ttu-id="4cee4-374">**有效的值** ： 1-32768 (`Int32`) </span><span class="sxs-lookup"><span data-stu-id="4cee4-374">**Valid values** : 1 - 32768 (`Int32`)</span></span>

<span data-ttu-id="4cee4-375">**預設值** ：4096</span><span class="sxs-lookup"><span data-stu-id="4cee4-375">**Default** : 4096</span></span>

<span data-ttu-id="4cee4-376">若要判斷命令歷程記錄中目前儲存的命令數目，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4cee4-376">To determine the number of commands current saved in the command history, type:</span></span>

```powershell
(Get-History).Count
```

<span data-ttu-id="4cee4-377">若要查看儲存在會話歷程記錄中的命令，請使用 `Get-History` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4cee4-377">To see the commands saved in your session history, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="4cee4-378">如需詳細資訊，請參閱 [about_History](about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-378">For more information, see [about_History](about_History.md).</span></span>

### <a name="maximumvariablecount"></a><span data-ttu-id="4cee4-379">\$MaximumVariableCount</span><span class="sxs-lookup"><span data-stu-id="4cee4-379">\$MaximumVariableCount</span></span>

<span data-ttu-id="4cee4-380">判斷指定的會話中允許的變數數目，包括自動變數、喜好設定變數，以及您在命令和腳本中建立的變數。</span><span class="sxs-lookup"><span data-stu-id="4cee4-380">Determines how many variables are permitted in a given session, including automatic variables, preference variables, and the variables that you create in commands and scripts.</span></span>

<span data-ttu-id="4cee4-381">**有效的值** ： 1024-32768 (`Int32`) </span><span class="sxs-lookup"><span data-stu-id="4cee4-381">**Valid values** : 1024 - 32768 (`Int32`)</span></span>

<span data-ttu-id="4cee4-382">**預設值** ：4096</span><span class="sxs-lookup"><span data-stu-id="4cee4-382">**Default** : 4096</span></span>

<span data-ttu-id="4cee4-383">若要查看會話中的變數，請使用 `Get-Variable` powershell `Variable:` 磁片磁碟機和 powershell 提供者的 Cmdlet 和功能 `Variable` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-383">To see the variables in your session, use the `Get-Variable` cmdlet and the features of the PowerShell `Variable:` drive and the PowerShell `Variable` provider.</span></span> <span data-ttu-id="4cee4-384">如需詳細資訊，請參閱 [about_Variable_Provider](about_Variable_Provider.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-384">For information, see [about_Variable_Provider](about_Variable_Provider.md).</span></span>

<span data-ttu-id="4cee4-385">若要尋找系統上目前的變數數目，請輸入：</span><span class="sxs-lookup"><span data-stu-id="4cee4-385">To find the current number of variables on the system, type:</span></span>

```powershell
(Get-Variable).Count
```

### <a name="ofs"></a><span data-ttu-id="4cee4-386">\$.OFS</span><span class="sxs-lookup"><span data-stu-id="4cee4-386">\$OFS</span></span>

<span data-ttu-id="4cee4-387">輸出欄位分隔符號 (.OFS) 指定字元來分隔轉換成字串的陣列元素。</span><span class="sxs-lookup"><span data-stu-id="4cee4-387">The Output Field Separator (OFS) specifies the character that separates the elements of an array that is converted to a string.</span></span>

<span data-ttu-id="4cee4-388">**有效的值** ：任何字串。</span><span class="sxs-lookup"><span data-stu-id="4cee4-388">**Valid values** : Any string.</span></span>

<span data-ttu-id="4cee4-389">**預設值** ：空間</span><span class="sxs-lookup"><span data-stu-id="4cee4-389">**Default** : Space</span></span>

<span data-ttu-id="4cee4-390">根據預設，此 `$OFS` 變數不存在，而且輸出檔分隔符號是一個空格，但是您可以加入這個變數，並將它設定為任何字串。</span><span class="sxs-lookup"><span data-stu-id="4cee4-390">By default, the `$OFS` variable doesn't exist and the output file separator is a space, but you can add this variable and set it to any string.</span></span> <span data-ttu-id="4cee4-391">您可以藉 `$OFS` 由輸入來變更會話中的值 `$OFS="<value>"` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-391">You can change the value of `$OFS` in your session, by typing `$OFS="<value>"`.</span></span>

> [!NOTE]
> <span data-ttu-id="4cee4-392">如果您需要在 `" "` 腳本、模組或設定輸出中 () 空間的預設值，請小心在 `$OFS` 程式碼中的其他位置未變更預設值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-392">If you're expecting the default value of a space (`" "`) in your script, module, or configuration output, be careful that the `$OFS` default value hasn't been changed elsewhere in your code.</span></span>

#### <a name="examples"></a><span data-ttu-id="4cee4-393">範例</span><span class="sxs-lookup"><span data-stu-id="4cee4-393">Examples</span></span>

<span data-ttu-id="4cee4-394">這個範例顯示當陣列轉換成字串時，會使用空格來分隔值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-394">This example shows that a space is used to separate the values when an array is converted to a string.</span></span> <span data-ttu-id="4cee4-395">在此情況下，會將整數陣列儲存在變數中，然後將變數轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="4cee4-395">In this case, an array of integers is stored in a variable and then the variable is cast as a string.</span></span>

```powershell
$array = 1,2,3,4
[string]$array
```

```Output
1 2 3 4
```

<span data-ttu-id="4cee4-396">若要變更分隔符號，請將 `$OFS` 值指派給該變數。</span><span class="sxs-lookup"><span data-stu-id="4cee4-396">To change the separator, add the `$OFS` variable by assigning a value to it.</span></span>
<span data-ttu-id="4cee4-397">變數必須命名為 `$OFS` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-397">The variable must be named `$OFS`.</span></span>

```powershell
$OFS = "+"
[string]$array
```

```Output
1+2+3+4
```

<span data-ttu-id="4cee4-398">若要還原預設行為，您可以 () 指派空間給 `" "` 值， `$OFS` 或刪除變數。</span><span class="sxs-lookup"><span data-stu-id="4cee4-398">To restore the default behavior, you can assign a space (`" "`) to the value of `$OFS` or delete the variable.</span></span> <span data-ttu-id="4cee4-399">下列命令會刪除變數，然後確認分隔符號是空格。</span><span class="sxs-lookup"><span data-stu-id="4cee4-399">The following commands delete the variable and then verify that the separator is a space.</span></span>

```powershell
Remove-Variable OFS
[string]$array
```

```Output
1 2 3 4
```

### <a name="outputencoding"></a><span data-ttu-id="4cee4-400">\$OutputEncoding</span><span class="sxs-lookup"><span data-stu-id="4cee4-400">\$OutputEncoding</span></span>

<span data-ttu-id="4cee4-401">決定 PowerShell 在將文字傳送至其他應用程式時所使用的字元編碼方法。</span><span class="sxs-lookup"><span data-stu-id="4cee4-401">Determines the character encoding method that PowerShell uses when it sends text to other applications.</span></span>

<span data-ttu-id="4cee4-402">例如，如果應用程式將 Unicode 字串傳回到 PowerShell，您可能需要將值變更為 **>unicodeencoding** ，才能正確地傳送字元。</span><span class="sxs-lookup"><span data-stu-id="4cee4-402">For example, if an application returns Unicode strings to PowerShell, you might need to change the value to **UnicodeEncoding** to send the characters correctly.</span></span>

<span data-ttu-id="4cee4-403">有效的值如下：衍生自編碼類別的物件，例如 **ASCIIEncoding** 、 **SBCSCodePageEncoding** 、 **UTF7Encoding** 、 **UTF8Encoding** 、 **>utf32encoding** 和 **>unicodeencoding** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-403">The valid values are as follows: Objects derived from an Encoding class, such as **ASCIIEncoding** , **SBCSCodePageEncoding** , **UTF7Encoding** , **UTF8Encoding** , **UTF32Encoding** , and **UnicodeEncoding** .</span></span>

<span data-ttu-id="4cee4-404">**預設值** ： ASCIIEncoding 物件 (ASCIIEncoding) </span><span class="sxs-lookup"><span data-stu-id="4cee4-404">**Default** : ASCIIEncoding object (System.Text.ASCIIEncoding)</span></span>

#### <a name="examples"></a><span data-ttu-id="4cee4-405">範例</span><span class="sxs-lookup"><span data-stu-id="4cee4-405">Examples</span></span>

<span data-ttu-id="4cee4-406">此範例示範如何在已針對使用 Unicode 字元的語言（例如中文）當地語系化的電腦上，讓 Windows **findstr.exe** 命令在 PowerShell 中運作。</span><span class="sxs-lookup"><span data-stu-id="4cee4-406">This example shows how to make the Windows **findstr.exe** command work in PowerShell on a computer that is localized for a language that uses Unicode characters, such as Chinese.</span></span>

<span data-ttu-id="4cee4-407">第一個命令會尋找的值 `$OutputEncoding` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-407">The first command finds the value of `$OutputEncoding`.</span></span> <span data-ttu-id="4cee4-408">因為值是編碼物件，所以只會顯示其 **encoding.encodingname** 屬性。</span><span class="sxs-lookup"><span data-stu-id="4cee4-408">Because the value is an encoding object, display only its **EncodingName** property.</span></span>

```powershell
$OutputEncoding.EncodingName
```

<span data-ttu-id="4cee4-409">在此範例中， **findstr.exe** 命令是用來搜尋檔案中有兩個中文字元 `Test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-409">In this example, a **findstr.exe** command is used to search for two Chinese characters that are present in the `Test.txt` file.</span></span> <span data-ttu-id="4cee4-410">在 Windows 命令提示字元中執行此 **findstr.exe** 命令 ( **cmd.exe** ) ， **findstr.exe** 會尋找文字檔中的字元。</span><span class="sxs-lookup"><span data-stu-id="4cee4-410">When this **findstr.exe** command is run in the Windows Command Prompt ( **cmd.exe** ), **findstr.exe** finds the characters in the text file.</span></span> <span data-ttu-id="4cee4-411">不過，當您在 PowerShell 中執行相同的 **findstr.exe** 命令時，找不到字元，因為 PowerShell 會將它們傳送至 ASCII 文字中的 **findstr.exe** ，而不是 Unicode 文字。</span><span class="sxs-lookup"><span data-stu-id="4cee4-411">However, when you run the same **findstr.exe** command in PowerShell, the characters aren't found because the PowerShell sends them to **findstr.exe** in ASCII text, instead of in Unicode text.</span></span>

```powershell
findstr <Unicode-characters>
```

<span data-ttu-id="4cee4-412">若要在 PowerShell 中執行命令，請將的值設定 `$OutputEncoding` 為主控台的 [ **OutputEncoding** ] 屬性值（以針對 Windows 選取的地區設定為基礎）。</span><span class="sxs-lookup"><span data-stu-id="4cee4-412">To make the command work in PowerShell, set the value of `$OutputEncoding` to the value of the **OutputEncoding** property of the console, that is based on the locale selected for Windows.</span></span> <span data-ttu-id="4cee4-413">由於 **OutputEncoding** 是主控台的靜態屬性，因此請在命令中使用雙冒號 (`::`) 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-413">Because **OutputEncoding** is a static property of the console, use double-colons (`::`) in the command.</span></span>

```powershell
$OutputEncoding = [console]::OutputEncoding
$OutputEncoding.EncodingName
```

```Output
OEM United States
```

<span data-ttu-id="4cee4-414">編碼變更之後， **findstr.exe** 命令會尋找 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="4cee4-414">After the encoding change, the **findstr.exe** command finds the Unicode characters.</span></span>

```powershell
findstr <Unicode-characters>
```

```Output
test.txt:         <Unicode-characters>
```

### <a name="progresspreference"></a><span data-ttu-id="4cee4-415">\$ProgressPreference</span><span class="sxs-lookup"><span data-stu-id="4cee4-415">\$ProgressPreference</span></span>

<span data-ttu-id="4cee4-416">決定 PowerShell 如何回應腳本、Cmdlet 或提供者所產生的進度更新，例如 [寫入進度](xref:Microsoft.PowerShell.Utility.Write-Progress) Cmdlet 所產生的進度列。</span><span class="sxs-lookup"><span data-stu-id="4cee4-416">Determines how PowerShell responds to progress updates generated by a script, cmdlet, or provider, such as the progress bars generated by the [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress) cmdlet.</span></span>
<span data-ttu-id="4cee4-417">此 `Write-Progress` Cmdlet 會建立顯示命令狀態的進度列。</span><span class="sxs-lookup"><span data-stu-id="4cee4-417">The `Write-Progress` cmdlet creates progress bars that show a command's status.</span></span>

<span data-ttu-id="4cee4-418">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="4cee4-418">The valid values are as follows:</span></span>

- <span data-ttu-id="4cee4-419">**停止** ：不顯示進度列。</span><span class="sxs-lookup"><span data-stu-id="4cee4-419">**Stop** : Doesn't display the progress bar.</span></span> <span data-ttu-id="4cee4-420">相反地，它會顯示錯誤訊息並停止執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-420">Instead, it displays an error message and stops executing.</span></span>
- <span data-ttu-id="4cee4-421">**Inquire** ：不顯示進度列。</span><span class="sxs-lookup"><span data-stu-id="4cee4-421">**Inquire** : Doesn't display the progress bar.</span></span> <span data-ttu-id="4cee4-422">提示您提供繼續的許可權。</span><span class="sxs-lookup"><span data-stu-id="4cee4-422">Prompts for permission to continue.</span></span> <span data-ttu-id="4cee4-423">如果您使用 `Y` 或回復 `A` ，則會顯示進度列。</span><span class="sxs-lookup"><span data-stu-id="4cee4-423">If you reply with `Y` or `A`, it displays the progress bar.</span></span>
- <span data-ttu-id="4cee4-424">**繼續** ： (預設) 顯示進度列，並繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-424">**Continue** : (Default) Displays the progress bar and continues with execution.</span></span>
- <span data-ttu-id="4cee4-425">**SilentlyContinue** ：執行命令，但不會顯示進度列。</span><span class="sxs-lookup"><span data-stu-id="4cee4-425">**SilentlyContinue** : Executes the command, but doesn't display the progress bar.</span></span>

### <a name="psemailserver"></a><span data-ttu-id="4cee4-426">\$PSEmailServer</span><span class="sxs-lookup"><span data-stu-id="4cee4-426">\$PSEmailServer</span></span>

<span data-ttu-id="4cee4-427">指定用來傳送電子郵件訊息的預設電子郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="4cee4-427">Specifies the default e-mail server that is used to send email messages.</span></span> <span data-ttu-id="4cee4-428">傳送電子郵件的 Cmdlet 會使用這個喜好設定變數，例如 [傳送 send-mailmessage](xref:Microsoft.PowerShell.Utility.Send-MailMessage) 指令程式。</span><span class="sxs-lookup"><span data-stu-id="4cee4-428">This preference variable is used by cmdlets that send email, such as the [Send-MailMessage](xref:Microsoft.PowerShell.Utility.Send-MailMessage) cmdlet.</span></span>

### <a name="psdefaultparametervalues"></a><span data-ttu-id="4cee4-429">\$PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="4cee4-429">\$PSDefaultParameterValues</span></span>

<span data-ttu-id="4cee4-430">指定 Cmdlet 和 advanced 函式之參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-430">Specifies default values for the parameters of cmdlets and advanced functions.</span></span>
<span data-ttu-id="4cee4-431">的值 `$PSDefaultParameterValues` 是雜湊表，其中索引鍵是由 Cmdlet 名稱和參數名稱所組成，並以冒號分隔 (`:`) 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-431">The value of `$PSDefaultParameterValues` is a hash table where the key consists of the cmdlet name and parameter name separated by a colon (`:`).</span></span> <span data-ttu-id="4cee4-432">值是您指定的自訂預設值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-432">The value is a custom default value that you specify.</span></span>

<span data-ttu-id="4cee4-433">`$PSDefaultParameterValues` 已在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="4cee4-433">`$PSDefaultParameterValues` was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="4cee4-434">如需此喜好設定變數的詳細資訊，請參閱 [about_Parameters_Default_Values](about_Parameters_Default_Values.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-434">For more information about this preference variable, see [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span></span>

### <a name="psmoduleautoloadingpreference"></a><span data-ttu-id="4cee4-435">\$PSModuleAutoloadingPreference</span><span class="sxs-lookup"><span data-stu-id="4cee4-435">\$PSModuleAutoloadingPreference</span></span>

<span data-ttu-id="4cee4-436">啟用和停用自動匯入會話中的模組。</span><span class="sxs-lookup"><span data-stu-id="4cee4-436">Enables and disables automatic importing of modules in the session.</span></span> <span data-ttu-id="4cee4-437">**All** 是預設值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-437">**All** is the default.</span></span> <span data-ttu-id="4cee4-438">不論變數的值為何，您都可以使用 [import-module](xref:Microsoft.PowerShell.Core.Import-Module) 匯入模組。</span><span class="sxs-lookup"><span data-stu-id="4cee4-438">Regardless of the variable's value, you can use [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module) to import a module.</span></span>

<span data-ttu-id="4cee4-439">有效值為：</span><span class="sxs-lookup"><span data-stu-id="4cee4-439">Valid values are:</span></span>

- <span data-ttu-id="4cee4-440">**全部** ：模組會在第一次使用時自動匯入。</span><span class="sxs-lookup"><span data-stu-id="4cee4-440">**All** : Modules are imported automatically on first-use.</span></span> <span data-ttu-id="4cee4-441">若要匯入模組，請取得或使用模組中的任何命令。</span><span class="sxs-lookup"><span data-stu-id="4cee4-441">To import a module, get or use any command in the module.</span></span> <span data-ttu-id="4cee4-442">例如，使用 `Get-Command`。</span><span class="sxs-lookup"><span data-stu-id="4cee4-442">For example, use `Get-Command`.</span></span>
- <span data-ttu-id="4cee4-443">**ModuleQualified** ：只有在使用者使用模組中命令的模組限定名稱時，才會自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="4cee4-443">**ModuleQualified** : Modules are imported automatically only when a user uses the module-qualified name of a command in the module.</span></span> <span data-ttu-id="4cee4-444">例如，如果使用者輸入，則 `MyModule\MyCommand` PowerShell 會匯入 **MyModule** 模組。</span><span class="sxs-lookup"><span data-stu-id="4cee4-444">For example, if the user types `MyModule\MyCommand`, PowerShell imports the **MyModule** module.</span></span>
- <span data-ttu-id="4cee4-445">**無** ：在會話中停用自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="4cee4-445">**None** : Automatic importing of modules is disabled in the session.</span></span> <span data-ttu-id="4cee4-446">若要匯入模組，請使用 `Import-Module` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4cee4-446">To import a module, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="4cee4-447">如需自動匯入模組的詳細資訊，請參閱 [about_Modules](about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-447">For more information about automatic importing of modules, see [about_Modules](about_Modules.md).</span></span>

### <a name="pssessionapplicationname"></a><span data-ttu-id="4cee4-448">\$PSSessionApplicationName</span><span class="sxs-lookup"><span data-stu-id="4cee4-448">\$PSSessionApplicationName</span></span>

<span data-ttu-id="4cee4-449">指定遠端命令的預設應用程式名稱，此命令會使用 Web 服務來管理 (WS-MANAGEMENT) 技術。</span><span class="sxs-lookup"><span data-stu-id="4cee4-449">Specifies the default application name for a remote command that uses Web Services for Management (WS-Management) technology.</span></span> <span data-ttu-id="4cee4-450">如需詳細資訊，請參閱 [關於 Windows 遠端管理](/windows/win32/winrm/about-windows-remote-management)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-450">For more information, see [About Windows Remote Management](/windows/win32/winrm/about-windows-remote-management).</span></span>

<span data-ttu-id="4cee4-451">系統預設的應用程式名稱是 `WSMAN` ，但您可以使用這個喜好設定變數來變更預設值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-451">The system default application name is `WSMAN`, but you can use this preference variable to change the default.</span></span>

<span data-ttu-id="4cee4-452">應用程式名稱是連接 URI 中的最後一個節點。</span><span class="sxs-lookup"><span data-stu-id="4cee4-452">The application name is the last node in a connection URI.</span></span> <span data-ttu-id="4cee4-453">例如，下列範例 URI 中的應用程式名稱為 `WSMAN` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-453">For example, the application name in the following sample URI is `WSMAN`.</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="4cee4-454">當遠端命令未指定連接 URI 或應用程式名稱時，就會使用預設的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="4cee4-454">The default application name is used when the remote command doesn't specify a connection URI or an application name.</span></span>

<span data-ttu-id="4cee4-455">**WinRM** 服務會使用應用程式名稱來選取接聽程式，以服務連線要求。</span><span class="sxs-lookup"><span data-stu-id="4cee4-455">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="4cee4-456">參數的值應該符合遠端電腦上接聽程式之 **URLPrefix** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-456">The parameter's value should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

<span data-ttu-id="4cee4-457">若要覆寫系統預設值和這個變數的值，並為特定會話選取不同的應用程式名稱，請使用 [新的-pssession](xref:Microsoft.PowerShell.Core.New-PSSession)、 [輸入-Pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession)或 [Invoke 命令](xref:Microsoft.PowerShell.Core.Invoke-Command)Cmdlet 的 **ConnectionURI** 或 **ApplicationName** 參數。</span><span class="sxs-lookup"><span data-stu-id="4cee4-457">To override the system default and the value of this variable, and select a different application name for a particular session, use the **ConnectionURI** or **ApplicationName** parameters of the [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession), or [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlets.</span></span>

<span data-ttu-id="4cee4-458">`$PSSessionApplicationName`喜好設定變數是在本機電腦上設定的，但它會指定遠端電腦上的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="4cee4-458">The `$PSSessionApplicationName` preference variable is set on the local computer, but it specifies a listener on the remote computer.</span></span> <span data-ttu-id="4cee4-459">如果您指定的應用程式名稱不存在於遠端電腦上，用來建立會話的命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="4cee4-459">If the application name that you specify doesn't exist on the remote computer, the command to establish the session fails.</span></span>

### <a name="pssessionconfigurationname"></a><span data-ttu-id="4cee4-460">\$PSSessionConfigurationName</span><span class="sxs-lookup"><span data-stu-id="4cee4-460">\$PSSessionConfigurationName</span></span>

<span data-ttu-id="4cee4-461">指定用於在目前會話中建立之 **pssession** 的預設會話設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-461">Specifies the default session configuration that is used for **PSSessions** created in the current session.</span></span>

<span data-ttu-id="4cee4-462">此喜好設定變數是在本機電腦上設定的，但它會指定位於遠端電腦上的會話設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-462">This preference variable is set on the local computer, but it specifies a session configuration that's located on the remote computer.</span></span>

<span data-ttu-id="4cee4-463">變數的值 `$PSSessionConfigurationName` 是完整的資源 URI。</span><span class="sxs-lookup"><span data-stu-id="4cee4-463">The value of the `$PSSessionConfigurationName` variable is a fully qualified resource URI.</span></span>

<span data-ttu-id="4cee4-464">預設值 `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` 表示遠端電腦上的 **Microsoft PowerShell** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-464">The default value `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` indicates the **Microsoft.PowerShell** session configuration on the remote computer.</span></span>

<span data-ttu-id="4cee4-465">如果您只指定設定名稱，則會在前面加上下列架構 URI：</span><span class="sxs-lookup"><span data-stu-id="4cee4-465">If you specify only a configuration name, the following schema URI is prepended:</span></span>

`http://schemas.microsoft.com/PowerShell/`

<span data-ttu-id="4cee4-466">您可以使用 **ConfigurationName** `New-PSSession` 、 `Enter-PSSession` 或 Cmdlet 的 ConfigurationName 參數來覆寫預設值，並為特定會話選取不同的會話設定 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-466">You can override the default and select a different session configuration for a particular session by using the **ConfigurationName** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="4cee4-467">您可以隨時變更此變數的值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-467">You can change the value of this variable at any time.</span></span> <span data-ttu-id="4cee4-468">當您這樣做時，請記住，您選取的會話設定必須存在於遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="4cee4-468">When you do, remember that the session configuration that you select must exist on the remote computer.</span></span> <span data-ttu-id="4cee4-469">如果不是，用來建立使用會話設定之會話的命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="4cee4-469">If it doesn't, the command to create a session that uses the session configuration fails.</span></span>

<span data-ttu-id="4cee4-470">當遠端使用者建立連接到這部電腦的會話時，這個喜好設定變數不會決定要使用的本機會話設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-470">This preference variable doesn't determine which local session configurations are used when remote users create a session that connects to this computer.</span></span>
<span data-ttu-id="4cee4-471">不過，您可以使用本機會話設定的許可權來判斷哪些使用者可能會使用這些設定。</span><span class="sxs-lookup"><span data-stu-id="4cee4-471">However, you can use the permissions for the local session configurations to determine which users may use them.</span></span>

### <a name="pssessionoption"></a><span data-ttu-id="4cee4-472">\$PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="4cee4-472">\$PSSessionOption</span></span>

<span data-ttu-id="4cee4-473">在遠端會話中建立 advanced user 選項的預設值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-473">Establishes the default values for advanced user options in a remote session.</span></span>
<span data-ttu-id="4cee4-474">這些選項喜好設定會覆寫會話選項的系統預設值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-474">These option preferences override the system default values for session options.</span></span>

<span data-ttu-id="4cee4-475">`$PSSessionOption`變數包含 **PSSessionOption** 物件。</span><span class="sxs-lookup"><span data-stu-id="4cee4-475">The `$PSSessionOption` variable contains a **PSSessionOption** object.</span></span> <span data-ttu-id="4cee4-476">如需詳細資訊，請參閱 [PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-476">For more information, see [System.Management.Automation.Remoting.PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption).</span></span>
<span data-ttu-id="4cee4-477">物件的每個屬性都代表一個會話選項。</span><span class="sxs-lookup"><span data-stu-id="4cee4-477">Each property of the object represents a session option.</span></span> <span data-ttu-id="4cee4-478">例如， **NoCompression** 屬性會在會話期間開啟資料壓縮。</span><span class="sxs-lookup"><span data-stu-id="4cee4-478">For example, the **NoCompression** property turns of data compression during the session.</span></span>

<span data-ttu-id="4cee4-479">根據預設， `$PSSessionOption` 變數包含 **PSSessionOption** 物件，其中包含所有選項的預設值，如下所示。</span><span class="sxs-lookup"><span data-stu-id="4cee4-479">By default, the `$PSSessionOption` variable contains a **PSSessionOption** object with the default values for all options, as shown below.</span></span>

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
IncludePortInSPN                  : False
OutputBufferingMode               : None
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : -00:00:00.0010000
```

<span data-ttu-id="4cee4-480">如需這些選項的說明和詳細資訊，請參閱 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-480">For descriptions of these options and more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span> <span data-ttu-id="4cee4-481">如需遠端命令和會話的詳細資訊，請參閱 [about_Remote](about_Remote.md) 和 [about_PSSessions](about_PSSessions.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-481">For more information about remote commands and sessions, see [about_Remote](about_Remote.md) and [about_PSSessions](about_PSSessions.md).</span></span>

<span data-ttu-id="4cee4-482">若要變更喜好設定變數的值 `$PSSessionOption` ，請使用 `New-PSSessionOption` Cmdlet 以您偏好的選項值來建立 **PSSessionOption** 物件。</span><span class="sxs-lookup"><span data-stu-id="4cee4-482">To change the value of the `$PSSessionOption` preference variable, use the `New-PSSessionOption` cmdlet to create a **PSSessionOption** object with the option values you prefer.</span></span> <span data-ttu-id="4cee4-483">將輸出儲存在名為的變數中 `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-483">Save the output in a variable called `$PSSessionOption`.</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -NoCompression
```

<span data-ttu-id="4cee4-484">若要 `$PSSessionOption` 在每個 powershell 會話中使用喜好設定變數，請將 `New-PSSessionOption` 建立變數的命令新增 `$PSSessionOption` 至您的 powershell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="4cee4-484">To use the `$PSSessionOption` preference variable in every PowerShell session, add a `New-PSSessionOption` command that creates the `$PSSessionOption` variable to your PowerShell profile.</span></span> <span data-ttu-id="4cee4-485">如需詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-485">For more information, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="4cee4-486">您可以為特定的遠端會話設定自訂選項。</span><span class="sxs-lookup"><span data-stu-id="4cee4-486">You can set custom options for a particular remote session.</span></span> <span data-ttu-id="4cee4-487">您所設定的選項會優先于系統預設值和喜好設定變數的值 `$PSSessionOption` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-487">The options that you set take precedence over the system defaults and the value of the `$PSSessionOption` preference variable.</span></span>

<span data-ttu-id="4cee4-488">若要設定自訂會話選項，請使用 `New-PSSessionOption` Cmdlet 來建立 **PSSessionOption** 物件。</span><span class="sxs-lookup"><span data-stu-id="4cee4-488">To set custom session options, use the `New-PSSessionOption` cmdlet to create a **PSSessionOption** object.</span></span> <span data-ttu-id="4cee4-489">然後，在建立會話的 Cmdlet 中使用 **PSSessionOption** 物件做為 **SessionOption** 參數的值，例如 `New-PSSession` 、 `Enter-PSSession` 和 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-489">Then, use the **PSSessionOption** object as the value of the **SessionOption** parameter in cmdlets that create a session, such as `New-PSSession`, `Enter-PSSession`, and `Invoke-Command`.</span></span>

### <a name="transcript"></a><span data-ttu-id="4cee4-490">$Transcript</span><span class="sxs-lookup"><span data-stu-id="4cee4-490">$Transcript</span></span>

<span data-ttu-id="4cee4-491">用 `Start-Transcript` 來指定文字記錄檔的名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="4cee4-491">Used by `Start-Transcript` to specify the name and location of the transcript file.</span></span> <span data-ttu-id="4cee4-492">如果您未指定 **path** 參數的值，會 `Start-Transcript` 使用全域變數值中的路徑 `$Transcript` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-492">If you do not specify a value for the **Path** parameter, `Start-Transcript` uses the path in the value of the `$Transcript` global variable.</span></span> <span data-ttu-id="4cee4-493">如果您尚未建立此變數，請將文字記錄以檔案的 `Start-Transcript` 形式儲存在 `$Home\My Documents` 目錄中 `\PowerShell_transcript.<time-stamp>.txt` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-493">If you have not created this variable, `Start-Transcript` stores the transcripts in the `$Home\My Documents` directory as `\PowerShell_transcript.<time-stamp>.txt` files.</span></span>

### <a name="verbosepreference"></a><span data-ttu-id="4cee4-494">\$VerbosePreference</span><span class="sxs-lookup"><span data-stu-id="4cee4-494">\$VerbosePreference</span></span>

<span data-ttu-id="4cee4-495">決定 PowerShell 如何回應腳本、Cmdlet 或提供者所產生的詳細資訊訊息，例如 [寫入詳細](xref:Microsoft.PowerShell.Utility.Write-Verbose) 資訊 Cmdlet 所產生的訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-495">Determines how PowerShell responds to verbose messages generated by a script, cmdlet, or provider, such as the messages generated by the [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose) cmdlet.</span></span>
<span data-ttu-id="4cee4-496">詳細資訊訊息說明執行命令所執行的動作。</span><span class="sxs-lookup"><span data-stu-id="4cee4-496">Verbose messages describe the actions performed to execute a command.</span></span>

<span data-ttu-id="4cee4-497">依預設不會顯示詳細訊息，但您可以藉由變更的值來變更此行為 `$VerbosePreference` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-497">By default, verbose messages aren't displayed, but you can change this behavior by changing the value of `$VerbosePreference`.</span></span>

<span data-ttu-id="4cee4-498">您可以使用 Cmdlet 的 **verbose** 一般參數來顯示或隱藏特定命令的詳細資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-498">You can use the **Verbose** common parameter of a cmdlet to display or hide the verbose messages for a specific command.</span></span> <span data-ttu-id="4cee4-499">如需詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-499">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="4cee4-500">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="4cee4-500">The valid values are as follows:</span></span>

- <span data-ttu-id="4cee4-501">**停止** ：顯示詳細資訊訊息和錯誤訊息，然後停止執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-501">**Stop** : Displays the verbose message and an error message and then stops executing.</span></span>
- <span data-ttu-id="4cee4-502">**Inquire** ：顯示詳細資訊訊息，然後顯示詢問您是否要繼續的提示。</span><span class="sxs-lookup"><span data-stu-id="4cee4-502">**Inquire** : Displays the verbose message and then displays a prompt that asks you whether you want to continue.</span></span>
- <span data-ttu-id="4cee4-503">**繼續** ：顯示詳細資訊訊息，然後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-503">**Continue** : Displays the verbose message and then continues with execution.</span></span>
- <span data-ttu-id="4cee4-504">**SilentlyContinue** ： (預設) 不會顯示詳細資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-504">**SilentlyContinue** : (Default) Doesn't display the verbose message.</span></span> <span data-ttu-id="4cee4-505">繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-505">Continues executing.</span></span>

#### <a name="examples"></a><span data-ttu-id="4cee4-506">範例</span><span class="sxs-lookup"><span data-stu-id="4cee4-506">Examples</span></span>

<span data-ttu-id="4cee4-507">這些範例會顯示不同值的效果 `$VerbosePreference` ，以及 **詳細** 資訊參數以覆寫喜好設定值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-507">These examples show the effect of the different values of `$VerbosePreference` and the **Verbose** parameter to override the preference value.</span></span>

<span data-ttu-id="4cee4-508">此範例顯示 **SilentlyContinue** 值的效果，這是預設值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-508">This example shows the effect of the **SilentlyContinue** value, that is the default.</span></span> <span data-ttu-id="4cee4-509">此命令會使用 **message** 參數，但不會將訊息寫入 PowerShell 主控台。</span><span class="sxs-lookup"><span data-stu-id="4cee4-509">The command uses the **Message** parameter, but doesn't write a message to the PowerShell console.</span></span>

```powershell
Write-Verbose -Message "Verbose message test."
```

<span data-ttu-id="4cee4-510">使用 **Verbose** 參數時，會寫入訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-510">When the **Verbose** parameter is used, the message is written.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose
```

```Output
VERBOSE: Verbose message test.
```

<span data-ttu-id="4cee4-511">此範例顯示 **Continue** 值的效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-511">This example shows the effect of the **Continue** value.</span></span> <span data-ttu-id="4cee4-512">`$VerbosePreference`變數設定為 **Continue** ，並顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-512">The `$VerbosePreference` variable is set to **Continue** and the message is displayed.</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
```

<span data-ttu-id="4cee4-513">這個範例會使用 **Verbose** 參數，其值 `$false` 會覆寫 **Continue** 值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-513">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Continue** value.</span></span> <span data-ttu-id="4cee4-514">不會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-514">The message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

<span data-ttu-id="4cee4-515">此範例顯示 **Stop** 值的效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-515">This example shows the effect of the **Stop** value.</span></span> <span data-ttu-id="4cee4-516">`$VerbosePreference`變數已設定為 [ **停止** ]，並顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-516">The `$VerbosePreference` variable is set to **Stop** and the message is displayed.</span></span> <span data-ttu-id="4cee4-517">此命令已停止。</span><span class="sxs-lookup"><span data-stu-id="4cee4-517">The command is stopped.</span></span>

```powershell
$VerbosePreference = "Stop"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
Write-Verbose : The running command stopped because the preference variable
  "VerbosePreference" or common parameter is set to Stop: Verbose message test.
At line:1 char:1
+ Write-Verbose -Message "Verbose message test."
```

<span data-ttu-id="4cee4-518">這個範例會使用 **Verbose** 參數，其值 `$false` 會覆寫 **停止** 值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-518">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Stop** value.</span></span> <span data-ttu-id="4cee4-519">不會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-519">The message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

<span data-ttu-id="4cee4-520">此範例顯示 **Inquire** 值的效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-520">This example shows the effect of the **Inquire** value.</span></span> <span data-ttu-id="4cee4-521">`$VerbosePreference`變數設定為 **Inquire** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-521">The `$VerbosePreference` variable is set to **Inquire** .</span></span> <span data-ttu-id="4cee4-522">訊息隨即顯示，並提示使用者進行確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-522">The message is displayed and the user is prompted for confirmation.</span></span>

```powershell
$VerbosePreference = "Inquire"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend
[?] Help (default is "Y"):
```

<span data-ttu-id="4cee4-523">這個範例會使用 **Verbose** 參數，其值 `$false` 會覆寫 **查詢** 值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-523">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Inquire** value.</span></span> <span data-ttu-id="4cee4-524">系統不會提示使用者，也不會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-524">The user isn't prompted and the message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

### <a name="warningpreference"></a><span data-ttu-id="4cee4-525">\$WarningPreference</span><span class="sxs-lookup"><span data-stu-id="4cee4-525">\$WarningPreference</span></span>

<span data-ttu-id="4cee4-526">決定 PowerShell 如何回應腳本、Cmdlet 或提供者所產生的警告訊息，例如由 [Write-warning](xref:Microsoft.PowerShell.Utility.Write-Warning) Cmdlet 所產生的訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-526">Determines how PowerShell responds to warning messages generated by a script, cmdlet, or provider, such as the messages generated by the [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning) cmdlet.</span></span>

<span data-ttu-id="4cee4-527">根據預設，會顯示警告訊息並繼續執行，但您可以藉由變更的值來變更此行為 `$WarningPreference` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-527">By default, warning messages are displayed and execution continues, but you can change this behavior by changing the value of `$WarningPreference`.</span></span>

<span data-ttu-id="4cee4-528">您可以使用 Cmdlet 的 **WarningAction** 一般參數，來判斷 PowerShell 如何回應特定命令的警告。</span><span class="sxs-lookup"><span data-stu-id="4cee4-528">You can use the **WarningAction** common parameter of a cmdlet to determine how PowerShell responds to warnings from a particular command.</span></span> <span data-ttu-id="4cee4-529">如需詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee4-529">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="4cee4-530">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="4cee4-530">The valid values are as follows:</span></span>

- <span data-ttu-id="4cee4-531">**停止** ：顯示警告訊息和錯誤訊息，然後停止執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-531">**Stop** : Displays the warning message and an error message and then stops executing.</span></span>
- <span data-ttu-id="4cee4-532">**查詢** ：顯示警告訊息，然後提示您取得繼續的許可權。</span><span class="sxs-lookup"><span data-stu-id="4cee4-532">**Inquire** : Displays the warning message and then prompts for permission to continue.</span></span>
- <span data-ttu-id="4cee4-533">**繼續** ： (預設值) 顯示警告訊息，然後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-533">**Continue** : (Default) Displays the warning message and then continues executing.</span></span>
- <span data-ttu-id="4cee4-534">**SilentlyContinue** ：不顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-534">**SilentlyContinue** : Doesn't display the warning message.</span></span> <span data-ttu-id="4cee4-535">繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4cee4-535">Continues executing.</span></span>

#### <a name="examples"></a><span data-ttu-id="4cee4-536">範例</span><span class="sxs-lookup"><span data-stu-id="4cee4-536">Examples</span></span>

<span data-ttu-id="4cee4-537">這些範例會顯示不同值的效果 `$WarningPreference` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-537">These examples show the effect of the different values of `$WarningPreference`.</span></span>
<span data-ttu-id="4cee4-538">**WarningAction** 參數會覆寫喜好設定值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-538">The **WarningAction** parameter overrides the preference value.</span></span>

<span data-ttu-id="4cee4-539">此範例顯示預設值的效果 [ **Continue** ]。</span><span class="sxs-lookup"><span data-stu-id="4cee4-539">This example shows the effect of the default value, **Continue** .</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
```

<span data-ttu-id="4cee4-540">此範例使用 **WarningAction** 參數搭配值 **SilentlyContinue** 來抑制警告。</span><span class="sxs-lookup"><span data-stu-id="4cee4-540">This example uses the **WarningAction** parameter with the value **SilentlyContinue** to suppress the warning.</span></span> <span data-ttu-id="4cee4-541">不會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-541">The message isn't displayed.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

<span data-ttu-id="4cee4-542">此範例會將 `$WarningPreference` 變數變更為 **SilentlyContinue** 值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-542">This example changes the `$WarningPreference` variable to the **SilentlyContinue** value.</span></span> <span data-ttu-id="4cee4-543">不會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-543">The message isn't displayed.</span></span>

```powershell
$WarningPreference = "SilentlyContinue"
$m = "This action can delete data."
Write-Warning -Message $m
```

<span data-ttu-id="4cee4-544">此範例會在產生警告時使用 **WarningAction** 參數來停止。</span><span class="sxs-lookup"><span data-stu-id="4cee4-544">This example uses the **WarningAction** parameter to stop when a warning is generated.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Stop
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m -WarningAction Stop
```

<span data-ttu-id="4cee4-545">此範例會將 `$WarningPreference` 變數變更為 **查詢** 值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-545">This example changes the `$WarningPreference` variable to the **Inquire** value.</span></span> <span data-ttu-id="4cee4-546">系統會提示使用者進行確認。</span><span class="sxs-lookup"><span data-stu-id="4cee4-546">The user is prompted for confirmation.</span></span>

```powershell
$WarningPreference = "Inquire"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend
[?] Help (default is "Y"):
```

<span data-ttu-id="4cee4-547">此範例使用 **WarningAction** 參數搭配值 **SilentlyContinue** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-547">This example uses the **WarningAction** parameter with the value **SilentlyContinue** .</span></span> <span data-ttu-id="4cee4-548">此命令會繼續執行，且不會顯示任何訊息。</span><span class="sxs-lookup"><span data-stu-id="4cee4-548">The command continues to execute and no message is displayed.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

<span data-ttu-id="4cee4-549">此範例會將 `$WarningPreference` 值變更為 [ **停止** ]。</span><span class="sxs-lookup"><span data-stu-id="4cee4-549">This example changes the `$WarningPreference` value to **Stop** .</span></span>

```powershell
$WarningPreference = "Stop"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m
```

<span data-ttu-id="4cee4-550">此範例會使用 **WarningAction** 搭配 **查詢** 值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-550">This example uses the **WarningAction** with the **Inquire** value.</span></span> <span data-ttu-id="4cee4-551">出現警告時，系統會提示使用者。</span><span class="sxs-lookup"><span data-stu-id="4cee4-551">The user is prompted when a warning occurs.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Inquire
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend
[?] Help (default is "Y"):
```

### <a name="whatifpreference"></a><span data-ttu-id="4cee4-552">\$WhatIfPreference</span><span class="sxs-lookup"><span data-stu-id="4cee4-552">\$WhatIfPreference</span></span>

<span data-ttu-id="4cee4-553">決定是否針對支援的每個命令自動啟用 **WhatIf** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-553">Determines whether **WhatIf** is automatically enabled for every command that supports it.</span></span> <span data-ttu-id="4cee4-554">當 **WhatIf** 啟用時，此 Cmdlet 會報告命令的預期效果，但不會執行命令。</span><span class="sxs-lookup"><span data-stu-id="4cee4-554">When **WhatIf** is enabled, the cmdlet reports the expected effect of the command, but doesn't execute the command.</span></span>

<span data-ttu-id="4cee4-555">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="4cee4-555">The valid values are as follows:</span></span>

- <span data-ttu-id="4cee4-556">**False** ( **0** ，未啟用) ： (預設) **WhatIf** 不會自動啟用。</span><span class="sxs-lookup"><span data-stu-id="4cee4-556">**False** ( **0** , not enabled): (Default) **WhatIf** isn't automatically enabled.</span></span> <span data-ttu-id="4cee4-557">若要手動啟用，請使用 Cmdlet 的 **WhatIf** 參數。</span><span class="sxs-lookup"><span data-stu-id="4cee4-557">To enable it manually, use the cmdlet's **WhatIf** parameter.</span></span>
- <span data-ttu-id="4cee4-558">**True** ( **1** ，enabled) ： **WhatIf** 會在任何支援的命令上自動啟用。</span><span class="sxs-lookup"><span data-stu-id="4cee4-558">**True** ( **1** , enabled): **WhatIf** is automatically enabled on any command that supports it.</span></span> <span data-ttu-id="4cee4-559">使用者可以將 **WhatIf** 參數的值設為 **False** ，以手動方式停用它，例如 `-WhatIf:$false` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-559">Users can use the **WhatIf** parameter with a value of **False** to disable it manually, such as `-WhatIf:$false`.</span></span>

#### <a name="examples"></a><span data-ttu-id="4cee4-560">範例</span><span class="sxs-lookup"><span data-stu-id="4cee4-560">Examples</span></span>

<span data-ttu-id="4cee4-561">這些範例會顯示不同值的效果 `$WhatIfPreference` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-561">These examples show the effect of the different values of `$WhatIfPreference`.</span></span>
<span data-ttu-id="4cee4-562">它們會示範如何使用 **WhatIf** 參數來覆寫特定命令的喜好設定值。</span><span class="sxs-lookup"><span data-stu-id="4cee4-562">They show how to use the **WhatIf** parameter to override the preference value for a specific command.</span></span>

<span data-ttu-id="4cee4-563">此範例顯示 `$WhatIfPreference` 變數設定為預設值 **False** 的效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-563">This example shows the effect of the `$WhatIfPreference` variable set to the default value, **False** .</span></span> <span data-ttu-id="4cee4-564">使用 `Get-ChildItem` 確認檔案是否存在。</span><span class="sxs-lookup"><span data-stu-id="4cee4-564">Use `Get-ChildItem` to verify that the file exists.</span></span>
<span data-ttu-id="4cee4-565">`Remove-Item` 刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="4cee4-565">`Remove-Item` deletes the file.</span></span> <span data-ttu-id="4cee4-566">刪除檔案之後，您可以使用確認刪除 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-566">After the file is deleted, you can verify the deletion with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path .\test.txt
Remove-Item -Path ./test.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           9/13/2019    10:53             10 test.txt
```

```powershell
Get-ChildItem -Path .\test.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -File test.txt
```

<span data-ttu-id="4cee4-567">此範例顯示當的值為 False 時，使用 **WhatIf** 參數的 `$WhatIfPreference` 效果 **False** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-567">This example shows the effect of using the **WhatIf** parameter when the value of `$WhatIfPreference` is **False** .</span></span>

<span data-ttu-id="4cee4-568">請確認檔案存在。</span><span class="sxs-lookup"><span data-stu-id="4cee4-568">Verify that the file exists.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="4cee4-569">使用 **WhatIf** 參數來判斷嘗試刪除檔案的結果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-569">Use the **WhatIf** parameter to determine the result of attempting to delete the file.</span></span>

```powershell
Remove-Item -Path .\test2.txt -WhatIf
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
``````

<span data-ttu-id="4cee4-570">確認未刪除該檔案。</span><span class="sxs-lookup"><span data-stu-id="4cee4-570">Verify that the file wasn't deleted.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="4cee4-571">此範例顯示 `$WhatIfPreference` 變數設定為 **True** 的效果。</span><span class="sxs-lookup"><span data-stu-id="4cee4-571">This example shows the effect of the `$WhatIfPreference` variable set to the value, **True** .</span></span> <span data-ttu-id="4cee4-572">當您使用刪除檔案時， `Remove-Item` 會顯示檔案的路徑，但不會刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="4cee4-572">When you use `Remove-Item` to delete a file, the file's path is displayed, but the file isn't deleted.</span></span>

<span data-ttu-id="4cee4-573">嘗試刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="4cee4-573">Attempt to delete a file.</span></span> <span data-ttu-id="4cee4-574">當執行時，會顯示一則訊息 `Remove-Item` ，但不會刪除該檔案。</span><span class="sxs-lookup"><span data-stu-id="4cee4-574">A message is displayed about what would happen if `Remove-Item` was run, but the file isn't deleted.</span></span>

```powershell
$WhatIfPreference = "True"
Remove-Item -Path .\test2.txt
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
```

<span data-ttu-id="4cee4-575">使用 `Get-ChildItem` 確認未刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="4cee4-575">Use `Get-ChildItem` to verify that the file wasn't deleted.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="4cee4-576">這個範例示範當的值為 True 時，如何刪除 `$WhatIfPreference` 檔案 **True** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-576">This example shows how to delete a file when the value of `$WhatIfPreference` is **True** .</span></span> <span data-ttu-id="4cee4-577">它會使用具有值的 **WhatIf** 參數 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-577">It uses the **WhatIf** parameter with a value of `$false`.</span></span> <span data-ttu-id="4cee4-578">使用 `Get-ChildItem` 確認檔案已刪除。</span><span class="sxs-lookup"><span data-stu-id="4cee4-578">Use `Get-ChildItem` to verify the file was deleted.</span></span>

```powershell
Remove-Item -Path .\test2.txt -WhatIf:$false
Get-ChildItem -Path .\test2.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test2.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path .\test2.txt
```

<span data-ttu-id="4cee4-579">以下是不 `Get-Process` 支援 **whatif** 且 `Stop-Process` 支援 **whatif** 的 Cmdlet 範例。</span><span class="sxs-lookup"><span data-stu-id="4cee4-579">The following are examples of the `Get-Process` cmdlet that doesn't support **WhatIf** and `Stop-Process` that does support **WhatIf** .</span></span> <span data-ttu-id="4cee4-580">`$WhatIfPreference`變數的值為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-580">The `$WhatIfPreference` variable's value is **True** .</span></span>

<span data-ttu-id="4cee4-581">`Get-Process` 不支援 **WhatIf** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-581">`Get-Process` doesn't support **WhatIf** .</span></span> <span data-ttu-id="4cee4-582">當命令執行時，它會顯示 **Winword** 處理常式。</span><span class="sxs-lookup"><span data-stu-id="4cee4-582">When the command is executed, it displays the **Winword** process.</span></span>

```powershell
Get-Process -Name Winword
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    130   119.84     173.38       8.39   15024   4 WINWORD
```

<span data-ttu-id="4cee4-583">`Stop-Process` 支援 **WhatIf** 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-583">`Stop-Process` does support **WhatIf** .</span></span> <span data-ttu-id="4cee4-584">**Winword** 進程不會停止。</span><span class="sxs-lookup"><span data-stu-id="4cee4-584">The **Winword** process isn't stopped.</span></span>

```powershell
Stop-Process -Name Winword
```

```Output
What if: Performing the operation "Stop-Process" on target "WINWORD (15024)".
```

<span data-ttu-id="4cee4-585">您可以使用 Whatif 參數搭配的值來覆寫 `Stop-Process` **whatif** 行為 **WhatIf** `$false` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-585">You can override the `Stop-Process` **WhatIf** behavior by using the **WhatIf** parameter with a value of `$false`.</span></span> <span data-ttu-id="4cee4-586">**Winword** 進程已停止。</span><span class="sxs-lookup"><span data-stu-id="4cee4-586">The **Winword** process is stopped.</span></span>

```powershell
Stop-Process -Name Winword -WhatIf:$false
```

<span data-ttu-id="4cee4-587">若要確認 **Winword** 進程已停止，請使用 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="4cee4-587">To verify that the **Winword** process was stopped, use `Get-Process`.</span></span>

```powershell
Get-Process -Name Winword
```

```Output
Get-Process : Cannot find a process with the name "Winword".
  Verify the process name and call the cmdlet again.
At line:1 char:1
+ Get-Process -Name Winword
```

## <a name="see-also"></a><span data-ttu-id="4cee4-588">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cee4-588">See also</span></span>

[<span data-ttu-id="4cee4-589">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="4cee4-589">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="4cee4-590">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4cee4-590">about_CommonParameters</span></span>](about_CommonParameters.md)

[<span data-ttu-id="4cee4-591">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="4cee4-591">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="4cee4-592">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="4cee4-592">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="4cee4-593">about_Remote</span><span class="sxs-lookup"><span data-stu-id="4cee4-593">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="4cee4-594">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="4cee4-594">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="4cee4-595">about_Variables</span><span class="sxs-lookup"><span data-stu-id="4cee4-595">about_Variables</span></span>](about_Variables.md)
