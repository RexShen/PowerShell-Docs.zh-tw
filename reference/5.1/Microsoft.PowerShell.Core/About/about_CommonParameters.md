---
description: 描述可以搭配任何 Cmdlet 使用的參數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: 441154d60440024ebea9d5047430f6e9209d8f04
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208080"
---
# <a name="about-commonparameters"></a><span data-ttu-id="3cdaa-104">關於 CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3cdaa-104">About CommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="3cdaa-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="3cdaa-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="3cdaa-106">描述可以搭配任何 Cmdlet 使用的參數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-106">Describes the parameters that can be used with any cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="3cdaa-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="3cdaa-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="3cdaa-108">一般參數是一組您可以搭配任何 Cmdlet 使用的 Cmdlet 參數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-108">The common parameters are a set of cmdlet parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="3cdaa-109">它們是由 PowerShell 所執行，不是由 Cmdlet 開發人員所執行，而且會自動提供給任何 Cmdlet 使用。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-109">They're implemented by PowerShell, not by the cmdlet developer, and they're automatically available to any cmdlet.</span></span>

<span data-ttu-id="3cdaa-110">您可以搭配任何 Cmdlet 使用一般參數，但它們可能不會影響所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-110">You can use the common parameters with any cmdlet, but they might not have an effect on all cmdlets.</span></span> <span data-ttu-id="3cdaa-111">例如，如果 Cmdlet 不會產生任何詳細資訊輸出，使用 **verbose** 一般參數沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-111">For example, if a cmdlet doesn't generate any verbose output, using the **Verbose** common parameter has no effect.</span></span>

<span data-ttu-id="3cdaa-112">一般參數也適用于使用 **CmdletBinding** 屬性或 **參數** 屬性的 advanced 函數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-112">The common parameters are also available on advanced functions that use the **CmdletBinding** attribute or the **Parameter** attribute.</span></span>

<span data-ttu-id="3cdaa-113">數個常見參數會覆寫您使用 PowerShell 喜好設定變數設定的系統預設值或喜好設定。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-113">Several common parameters override system defaults or preferences that you set by using the PowerShell preference variables.</span></span> <span data-ttu-id="3cdaa-114">和喜好設定變數不同的是，一般參數只會影響使用它們的命令。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-114">Unlike the preference variables, the common parameters affect only the commands in which they're used.</span></span>

<span data-ttu-id="3cdaa-115">如需詳細資訊，請參閱 [about_Preference_Variables](./about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-115">For more information, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

<span data-ttu-id="3cdaa-116">下列清單顯示一般參數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-116">The following list displays the common parameters.</span></span> <span data-ttu-id="3cdaa-117">其別名會列在括弧中。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-117">Their aliases are listed in parentheses.</span></span>

- <span data-ttu-id="3cdaa-118">**Debug** (db)</span><span class="sxs-lookup"><span data-stu-id="3cdaa-118">**Debug** (db)</span></span>
- <span data-ttu-id="3cdaa-119">**ErrorAction** (ea) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-119">**ErrorAction** (ea)</span></span>
- <span data-ttu-id="3cdaa-120">**ErrorVariable** (ev) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-120">**ErrorVariable** (ev)</span></span>
- <span data-ttu-id="3cdaa-121">**InformationAction** (infa) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-121">**InformationAction** (infa)</span></span>
- <span data-ttu-id="3cdaa-122">**可使用 informationvariable** (iv) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-122">**InformationVariable** (iv)</span></span>
- <span data-ttu-id="3cdaa-123">**OutVariable** (ov) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-123">**OutVariable** (ov)</span></span>
- <span data-ttu-id="3cdaa-124">**OutBuffer** (ob) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-124">**OutBuffer** (ob)</span></span>
- <span data-ttu-id="3cdaa-125">**PipelineVariable** (pv) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-125">**PipelineVariable** (pv)</span></span>
- <span data-ttu-id="3cdaa-126">**Verbose** (vb) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-126">**Verbose** (vb)</span></span>
- <span data-ttu-id="3cdaa-127">**WarningAction** (wa) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-127">**WarningAction** (wa)</span></span>
- <span data-ttu-id="3cdaa-128">**WarningVariable** (wv) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-128">**WarningVariable** (wv)</span></span>

<span data-ttu-id="3cdaa-129">**動作** 參數是 **ActionPreference** 類型值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-129">The **Action** parameters are **ActionPreference** type values.</span></span>
<span data-ttu-id="3cdaa-130">**ActionPreference** 是具有下列值的列舉：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-130">**ActionPreference** is an enumeration with the following values:</span></span>

| <span data-ttu-id="3cdaa-131">Name</span><span class="sxs-lookup"><span data-stu-id="3cdaa-131">Name</span></span>             | <span data-ttu-id="3cdaa-132">值</span><span class="sxs-lookup"><span data-stu-id="3cdaa-132">Value</span></span> |
|------------------|-------|
| <span data-ttu-id="3cdaa-133">暫止</span><span class="sxs-lookup"><span data-stu-id="3cdaa-133">Suspend</span></span>          | <span data-ttu-id="3cdaa-134">5</span><span class="sxs-lookup"><span data-stu-id="3cdaa-134">5</span></span>     |
| <span data-ttu-id="3cdaa-135">略過</span><span class="sxs-lookup"><span data-stu-id="3cdaa-135">Ignore</span></span>           | <span data-ttu-id="3cdaa-136">4</span><span class="sxs-lookup"><span data-stu-id="3cdaa-136">4</span></span>     |
| <span data-ttu-id="3cdaa-137">詢問</span><span class="sxs-lookup"><span data-stu-id="3cdaa-137">Inquire</span></span>          | <span data-ttu-id="3cdaa-138">3</span><span class="sxs-lookup"><span data-stu-id="3cdaa-138">3</span></span>     |
| <span data-ttu-id="3cdaa-139">繼續</span><span class="sxs-lookup"><span data-stu-id="3cdaa-139">Continue</span></span>         | <span data-ttu-id="3cdaa-140">2</span><span class="sxs-lookup"><span data-stu-id="3cdaa-140">2</span></span>     |
| <span data-ttu-id="3cdaa-141">停止</span><span class="sxs-lookup"><span data-stu-id="3cdaa-141">Stop</span></span>             | <span data-ttu-id="3cdaa-142">1</span><span class="sxs-lookup"><span data-stu-id="3cdaa-142">1</span></span>     |
| <span data-ttu-id="3cdaa-143">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="3cdaa-143">SilentlyContinue</span></span> | <span data-ttu-id="3cdaa-144">0</span><span class="sxs-lookup"><span data-stu-id="3cdaa-144">0</span></span>     |

<span data-ttu-id="3cdaa-145">您可以使用名稱或值搭配參數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-145">You may use the name or the value with the parameter.</span></span>

<span data-ttu-id="3cdaa-146">除了一般參數之外，許多 Cmdlet 也提供風險降低參數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-146">In addition to the common parameters, many cmdlets offer risk mitigation parameters.</span></span> <span data-ttu-id="3cdaa-147">牽涉到系統或使用者資料風險的 Cmdlet 通常會提供這些參數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-147">Cmdlets that involve risk to the system or to user data usually offer these parameters.</span></span>

<span data-ttu-id="3cdaa-148">風險降低的參數包括：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-148">The risk mitigation parameters are:</span></span>

- <span data-ttu-id="3cdaa-149">**WhatIf** (wi-fi) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-149">**WhatIf** (wi)</span></span>
- <span data-ttu-id="3cdaa-150">**確認** (cf) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-150">**Confirm** (cf)</span></span>

### <a name="common-parameter-descriptions"></a><span data-ttu-id="3cdaa-151">一般參數描述</span><span class="sxs-lookup"><span data-stu-id="3cdaa-151">COMMON PARAMETER DESCRIPTIONS</span></span>

#### <a name="debug"></a><span data-ttu-id="3cdaa-152">偵錯</span><span class="sxs-lookup"><span data-stu-id="3cdaa-152">Debug</span></span>

<span data-ttu-id="3cdaa-153">顯示命令所執行之作業的程式設計人員層級詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-153">Displays programmer-level detail about the operation done by the command.</span></span> <span data-ttu-id="3cdaa-154">只有當命令產生調試訊息時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-154">This parameter works only when the command generates a debugging message.</span></span> <span data-ttu-id="3cdaa-155">例如，當命令包含 Cmdlet 時，此參數會運作 `Write-Debug` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-155">For example, this parameter works when a command contains the `Write-Debug` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="3cdaa-156">根據預設，不會顯示偵錯工具訊息，因為變數的值 `$DebugPreference` 是 **SilentlyContinue** 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-156">By default, debugging messages aren't displayed because the value of the `$DebugPreference` variable is **SilentlyContinue** .</span></span>

<span data-ttu-id="3cdaa-157">在互動模式中， **Debug** 參數會覆寫 `$DebugPreference` 目前命令的變數值，並將的值設定 `$DebugPreference` 為 **Inquire** 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-157">In interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Inquire** .</span></span>

<span data-ttu-id="3cdaa-158">在非互動模式中， **Debug** 參數會覆寫 `$DebugPreference` 目前命令的變數值，將的值設定 `$DebugPreference` 為 **Continue** 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-158">In non-interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Continue** .</span></span>

<span data-ttu-id="3cdaa-159">`-Debug:$true` 的效果與相同 `-Debug` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-159">`-Debug:$true` has the same effect as `-Debug`.</span></span> <span data-ttu-id="3cdaa-160">`-Debug:$false`當 `$DebugPreference` 不是 **SilentlyContinue** （這是預設值）時，使用來抑制偵錯工具訊息的顯示。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-160">Use `-Debug:$false` to suppress the display of debugging messages when `$DebugPreference` isn't **SilentlyContinue** , which is the default.</span></span>

#### <a name="erroraction"></a><span data-ttu-id="3cdaa-161">ErrorAction</span><span class="sxs-lookup"><span data-stu-id="3cdaa-161">ErrorAction</span></span>

<span data-ttu-id="3cdaa-162">決定 Cmdlet 如何回應來自命令的非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-162">Determines how the cmdlet responds to a non-terminating error from the command.</span></span>
<span data-ttu-id="3cdaa-163">此參數只適用于命令產生非終止錯誤，例如來自 Cmdlet 的錯誤 `Write-Error` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-163">This parameter works only when the command generates a non-terminating error, such as those from the `Write-Error` cmdlet.</span></span>

```yaml
Type: ActionPreference
Aliases: ea
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="3cdaa-164">**ErrorAction** 參數會覆寫 `$ErrorActionPreference` 目前命令的變數值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-164">The **ErrorAction** parameter overrides the value of the `$ErrorActionPreference` variable for the current command.</span></span> <span data-ttu-id="3cdaa-165">因為變數的預設值 `$ErrorActionPreference` 為 **Continue** ，所以會顯示錯誤訊息並繼續執行，除非您使用 **ErrorAction** 參數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-165">Because the default value of the `$ErrorActionPreference` variable is **Continue** , error messages are displayed and execution continues unless you use the **ErrorAction** parameter.</span></span>

<span data-ttu-id="3cdaa-166">**ErrorAction** 參數不會影響終止錯誤 (例如遺漏資料、不正確參數或許可權不足) 導致命令無法順利完成。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-166">The **ErrorAction** parameter has no effect on terminating errors (such as missing data, parameters that aren't valid, or insufficient permissions) that prevent a command from completing successfully.</span></span>

<span data-ttu-id="3cdaa-167">`-ErrorAction:Continue` 顯示錯誤訊息，並繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-167">`-ErrorAction:Continue` display the error message and continues executing the command.</span></span> <span data-ttu-id="3cdaa-168">`Continue` 是預設值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-168">`Continue` is the default.</span></span>

<span data-ttu-id="3cdaa-169">`-ErrorAction:Ignore` 隱藏錯誤訊息，並繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-169">`-ErrorAction:Ignore` suppresses the error message and continues executing the command.</span></span> <span data-ttu-id="3cdaa-170">不同于 **SilentlyContinue** ， **Ignore** 不會將錯誤訊息加入至 `$Error` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-170">Unlike **SilentlyContinue** , **Ignore** doesn't add the error message to the `$Error` automatic variable.</span></span> <span data-ttu-id="3cdaa-171">**忽略** 值是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-171">The **Ignore** value is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="3cdaa-172">`-ErrorAction:Inquire` 顯示錯誤訊息，並在繼續執行之前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-172">`-ErrorAction:Inquire` displays the error message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="3cdaa-173">此值很少使用。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-173">This value is rarely used.</span></span>

<span data-ttu-id="3cdaa-174">`-ErrorAction:SilentlyContinue` 隱藏錯誤訊息，並繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-174">`-ErrorAction:SilentlyContinue` suppresses the error message and continues executing the command.</span></span>

<span data-ttu-id="3cdaa-175">`-ErrorAction:Stop` 顯示錯誤訊息，並停止執行命令。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-175">`-ErrorAction:Stop` displays the error message and stops executing the command.</span></span>

<span data-ttu-id="3cdaa-176">`-ErrorAction:Suspend` 僅適用于 PowerShell 6 和以上版本中不支援的工作流程。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-176">`-ErrorAction:Suspend` is only available for workflows which aren't supported in PowerShell 6 and beyond.</span></span>

> [!NOTE]
> <span data-ttu-id="3cdaa-177">**ErrorAction** 參數會覆寫，但在 `$ErrorAction` 命令中使用參數來執行腳本或函式時，不會取代喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-177">The **ErrorAction** parameter overrides, but does not replace the value of the `$ErrorAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="errorvariable"></a><span data-ttu-id="3cdaa-178">ErrorVariable</span><span class="sxs-lookup"><span data-stu-id="3cdaa-178">ErrorVariable</span></span>

<span data-ttu-id="3cdaa-179">**ErrorVariable** 會將命令相關的錯誤訊息儲存在指定的變數和 `$Error` 自動變數中。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-179">**ErrorVariable** stores error messages about the command in the specified variable and in the `$Error` automatic variable.</span></span> <span data-ttu-id="3cdaa-180">如需詳細資訊，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="3cdaa-180">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md)</span></span>

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="3cdaa-181">根據預設，新的錯誤訊息會覆寫已儲存在變數中的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-181">By default, new error messages overwrite error messages that are already stored in the variable.</span></span> <span data-ttu-id="3cdaa-182">若要將錯誤訊息附加至變數內容，請在 `+` 變數名稱之前輸入加號 () 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-182">To append the error message to the variable content, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="3cdaa-183">例如，下列命令 `$a` 會建立變數，然後在其中儲存任何錯誤：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-183">For example, the following command creates the `$a` variable and then stores any errors in it:</span></span>

```powershell
Get-Process -Id 6 -ErrorVariable a
```

<span data-ttu-id="3cdaa-184">下列命令會將任何錯誤訊息新增至 `$a` 變數：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-184">The following command adds any error messages to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

<span data-ttu-id="3cdaa-185">下列命令會顯示的內容 `$a` ：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-185">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="3cdaa-186">您可以使用這個參數來建立只包含來自特定命令之錯誤訊息的變數，而不會影響 `$Error` 自動變數的行為。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-186">You can use this parameter to create a variable that contains only error messages from specific commands and does not affect the behavior of the `$Error` automatic variable.</span></span> <span data-ttu-id="3cdaa-187">`$Error`自動變數包含會話中所有命令的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-187">The `$Error` automatic variable contains error messages from all the commands in the session.</span></span> <span data-ttu-id="3cdaa-188">您可以使用陣列標記法（例如 `$a[0]` 或） `$error[1,2]` 來參考儲存在變數中的特定錯誤。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-188">You can use array notation, such as `$a[0]` or `$error[1,2]` to refer to specific errors stored in the variables.</span></span>

> [!NOTE]
> <span data-ttu-id="3cdaa-189">自訂錯誤變數包含命令所產生的所有錯誤，包括呼叫嵌套函數或腳本的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-189">The custom error variable contains all errors generated by the command, including errors from calls to nested functions or scripts.</span></span>

#### <a name="informationaction"></a><span data-ttu-id="3cdaa-190">InformationAction</span><span class="sxs-lookup"><span data-stu-id="3cdaa-190">InformationAction</span></span>

<span data-ttu-id="3cdaa-191">在 PowerShell 5.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-191">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="3cdaa-192">在使用它的命令或腳本內， **InformationAction** 一般參數會覆寫 `$InformationPreference` 喜好設定變數的值，此值預設會設定為 **SilentlyContinue** 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-192">Within the command or script in which it's used, the **InformationAction** common parameter overrides the value of the `$InformationPreference` preference variable, which by default is set to **SilentlyContinue** .</span></span> <span data-ttu-id="3cdaa-193">當您 `Write-Information` 在腳本中使用 **InformationAction** 時， `Write-Information` 會根據 **InformationAction** 參數的值顯示值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-193">When you use `Write-Information` in a script with **InformationAction** , `Write-Information` values are shown depending on the value of the **InformationAction** parameter.</span></span> <span data-ttu-id="3cdaa-194">如需的詳細資訊 `$InformationPreference` ，請參閱 [about_Preference_Variables](./about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-194">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

```yaml
Type: ActionPreference
Aliases: ia
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="3cdaa-195">`-InformationAction:Stop` 在命令出現時停止命令或腳本 `Write-Information` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-195">`-InformationAction:Stop` stops a command or script at an occurrence of the `Write-Information` command.</span></span>

<span data-ttu-id="3cdaa-196">`-InformationAction:Ignore` 抑制參考用訊息，並繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-196">`-InformationAction:Ignore` suppresses the informational message and continues running the command.</span></span> <span data-ttu-id="3cdaa-197">不同于 **SilentlyContinue** ，請 **略** 過完全忘記密碼的告知性訊息;它不會將參考用訊息新增至資訊串流。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-197">Unlike **SilentlyContinue** , **Ignore** completely forgets the informational message; it doesn't add the informational message to the information stream.</span></span>

<span data-ttu-id="3cdaa-198">`-InformationAction:Inquire` 顯示您在命令中指定的參考用訊息 `Write-Information` ，然後詢問您是否要繼續。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-198">`-InformationAction:Inquire` displays the informational message that you specify in a `Write-Information` command, then asks whether you want to continue.</span></span>

<span data-ttu-id="3cdaa-199">`-InformationAction:Continue` 顯示資訊訊息，並繼續執行。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-199">`-InformationAction:Continue` displays the informational message, and continues running.</span></span>

<span data-ttu-id="3cdaa-200">`-InformationAction:Suspend` PowerShell Core 不受支援，因為它僅適用于工作流程。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-200">`-InformationAction:Suspend` isn't supported on PowerShell Core as it is only available for workflows.</span></span>

<span data-ttu-id="3cdaa-201">`-InformationAction:SilentlyContinue` 沒有任何作用，因為參考用訊息不 (預設) 顯示，腳本會繼續執行而不會中斷。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-201">`-InformationAction:SilentlyContinue` no effect as the informational message aren't (Default) displayed, and the script continues without interruption.</span></span>

> [!NOTE]
> <span data-ttu-id="3cdaa-202">**InformationAction** 參數會覆寫，但在 `$InformationAction` 命令中使用參數來執行腳本或函式時，不會取代喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-202">The **InformationAction** parameter overrides, but does not replace the value of the `$InformationAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="informationvariable"></a><span data-ttu-id="3cdaa-203">可使用 informationvariable</span><span class="sxs-lookup"><span data-stu-id="3cdaa-203">InformationVariable</span></span>

<span data-ttu-id="3cdaa-204">在 PowerShell 5.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-204">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="3cdaa-205">在使用它的命令或腳本內， **可使用 informationvariable** 一般參數會將字串儲存在變數中，而您可以藉由新增命令來指定該字串 `Write-Information` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-205">Within the command or script in which it's used, the **InformationVariable** common parameter stores in a variable a string that you specify by adding the `Write-Information` command.</span></span> <span data-ttu-id="3cdaa-206">`Write-Information` 系統會根據 **InformationAction** 一般參數的值來顯示值;如果您未加入 **InformationAction** 一般參數，則 `Write-Information` 會根據喜好設定變數的值來顯示字串 `$InformationPreference` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-206">`Write-Information` values are shown depending on the value of the **InformationAction** common parameter; if you don't add the **InformationAction** common parameter, `Write-Information` strings are shown depending on the value of the `$InformationPreference` preference variable.</span></span> <span data-ttu-id="3cdaa-207">如需的詳細資訊 `$InformationPreference` ，請參閱 [about_Preference_Variables](./about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-207">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3cdaa-208">資訊變數包含命令所產生的所有資訊訊息，包括呼叫嵌套函數或腳本的資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-208">The information variable contains all information messages generated by the command, including information messages from calls to nested functions or scripts.</span></span>

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a><span data-ttu-id="3cdaa-209">OutBuffer</span><span class="sxs-lookup"><span data-stu-id="3cdaa-209">OutBuffer</span></span>

<span data-ttu-id="3cdaa-210">決定在透過管線傳送任何物件之前，要在緩衝區中累積的物件數目。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-210">Determines the number of objects to accumulate in a buffer before any objects are sent through the pipeline.</span></span> <span data-ttu-id="3cdaa-211">如果您省略此參數，則會在產生物件時傳送物件。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-211">If you omit this parameter, objects are sent as they're generated.</span></span>

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="3cdaa-212">此資源管理參數是針對 advanced 使用者所設計。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-212">This resource management parameter is designed for advanced users.</span></span> <span data-ttu-id="3cdaa-213">當您使用此參數時，PowerShell 會以批次方式將資料傳送至下一個 Cmdlet `OutBuffer + 1` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-213">When you use this parameter, PowerShell sends data to the next cmdlet in batches of `OutBuffer + 1`.</span></span>

<span data-ttu-id="3cdaa-214">下列範例替代項 `ForEach-Object` 會顯示使用此 Cmdlet 的進程區塊 `Write-Host` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-214">The following example alternates displays between to `ForEach-Object` process blocks that use the `Write-Host` cmdlet.</span></span> <span data-ttu-id="3cdaa-215">顯示會以2或的批次方式來替代 `OutBuffer + 1` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-215">The display alternates in batches of 2 or `OutBuffer + 1`.</span></span>

```powershell
1..4 | ForEach-Object {
        Write-Host "$($_): First"; $_
      } -OutBuffer 1 | ForEach-Object {
                        Write-Host "$($_): Second" }
```

```Output
1: First
2: First
1: Second
2: Second
3: First
4: First
3: Second
4: Second
```

#### <a name="outvariable"></a><span data-ttu-id="3cdaa-216">OutVariable</span><span class="sxs-lookup"><span data-stu-id="3cdaa-216">OutVariable</span></span>

<span data-ttu-id="3cdaa-217">除了透過管線傳送輸出外，還會將命令中的輸出物件儲存在指定的變數中。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-217">Stores output objects from the command in the specified variable in addition to sending the output along the pipeline.</span></span>

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="3cdaa-218">若要將輸出新增至變數，而不是取代任何可能已儲存在該處的輸出，請在 `+` 變數名稱之前輸入加號 () 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-218">To add the output to the variable, instead of replacing any output that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="3cdaa-219">例如，下列命令 `$out` 會建立變數，並將處理常式物件儲存在其中：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-219">For example, the following command creates the `$out` variable and stores the process object in it:</span></span>

```powershell
Get-Process PowerShell -OutVariable out
```

<span data-ttu-id="3cdaa-220">下列命令會將處理常式物件新增至 `$out` 變數：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-220">The following command adds the process object to the `$out` variable:</span></span>

```powershell
Get-Process iexplore -OutVariable +out
```

<span data-ttu-id="3cdaa-221">下列命令會顯示變數的內容 `$out` ：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-221">The following command displays the contents of the `$out` variable:</span></span>

```powershell
$out
```

> [!NOTE]
> <span data-ttu-id="3cdaa-222">**OutVariable** 參數所建立的變數是 `[System.Collections.ArrayList]` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-222">The variable created by the **OutVariable** parameter is a `[System.Collections.ArrayList]`.</span></span>

#### <a name="pipelinevariable"></a><span data-ttu-id="3cdaa-223">PipelineVariable</span><span class="sxs-lookup"><span data-stu-id="3cdaa-223">PipelineVariable</span></span>

<span data-ttu-id="3cdaa-224">當任何命名命令流經管線時， **PipelineVariable** 會將目前的管線元素值儲存為變數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-224">**PipelineVariable** stores the value of the current pipeline element as a variable, for any named command as it flows through the pipeline.</span></span>

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="3cdaa-225">有效的值是字串，與任何變數名稱的值相同。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-225">Valid values are strings, the same as for any variable names.</span></span>

<span data-ttu-id="3cdaa-226">以下是 **PipelineVariable** 運作方式的範例。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-226">The following is an example of how **PipelineVariable** works.</span></span> <span data-ttu-id="3cdaa-227">在此範例中， **PipelineVariable** 參數會加入至 `Foreach-Object` 命令，以將命令的結果儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-227">In this example, the **PipelineVariable** parameter is added to a `Foreach-Object` command to store the results of the command in variables.</span></span> <span data-ttu-id="3cdaa-228">從1到10的數位範圍會輸送到第一個 `Foreach-Object` 命令，其結果會儲存在名為 **Left** 的變數中。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-228">A range of numbers, 1 to 10, are piped into the first `Foreach-Object` command, the results of which are stored in a variable named **Left** .</span></span>

<span data-ttu-id="3cdaa-229">第一個命令的結果 `Foreach-Object` 會輸送到第二個 `Foreach-Object` 命令，以篩選第一個命令所傳回的物件 `Foreach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-229">The results of the first `Foreach-Object` command are piped into a second `Foreach-Object` command, which filters the objects returned by the first `Foreach-Object` command.</span></span> <span data-ttu-id="3cdaa-230">第二個命令的結果會儲存在名為 **Right** 的變數中。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-230">The results of the second command are stored in a variable named **Right** .</span></span>

<span data-ttu-id="3cdaa-231">第三 `Foreach-Object` 個命令 `Foreach-Object` 會使用乘法運算子來處理前兩個輸送命令的結果（由 **左** 和 **右** 變數所表示）。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-231">In the third `Foreach-Object` command, the results of the first two `Foreach-Object` piped commands, represented by the variables **Left** and **Right** , are processed by using a multiplication operator.</span></span> <span data-ttu-id="3cdaa-232">此命令會指示在 **左右** 變數中儲存的物件要相乘 **，並指定** 結果應顯示為「左範圍成員 \* 右範圍成員 = 產品」。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-232">The command instructs objects stored in the **Left** and **Right** variables to be multiplied, and specifies that the results should be displayed as "Left range member \* Right range member = product".</span></span>

```powershell
1..10 | Foreach-Object -PipelineVariable Left -Process { $_ } |
  Foreach-Object -PV Right -Process { 1..10 } |
  Foreach-Object -Process { "$Left * $Right = " + ($Left*$Right) }
```

```output
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
1 * 4 = 4
1 * 5 = 5
...
```

#### <a name="verbose"></a><span data-ttu-id="3cdaa-233">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="3cdaa-233">Verbose</span></span>

<span data-ttu-id="3cdaa-234">顯示命令所執行之操作的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-234">Displays detailed information about the operation done by the command.</span></span> <span data-ttu-id="3cdaa-235">這項資訊與追蹤或交易記錄檔中的資訊類似。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-235">This information resembles the information in a trace or in a transaction log.</span></span> <span data-ttu-id="3cdaa-236">此參數只適用于命令產生詳細訊息時。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-236">This parameter works only when the command generates a verbose message.</span></span> <span data-ttu-id="3cdaa-237">例如，當命令包含 Cmdlet 時，此參數會運作 `Write-Verbose` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-237">For example, this parameter works when a command contains the `Write-Verbose` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="3cdaa-238">**Verbose** 參數會覆寫 `$VerbosePreference` 目前命令的變數值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-238">The **Verbose** parameter overrides the value of the `$VerbosePreference` variable for the current command.</span></span> <span data-ttu-id="3cdaa-239">因為變數的預設值 `$VerbosePreference` 是 **SilentlyContinue** ，所以預設不會顯示詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-239">Because the default value of the `$VerbosePreference` variable is **SilentlyContinue** , verbose messages aren't displayed by default.</span></span>

<span data-ttu-id="3cdaa-240">`-Verbose:$true` 的效果與 `-Verbose`</span><span class="sxs-lookup"><span data-stu-id="3cdaa-240">`-Verbose:$true` has the same effect as `-Verbose`</span></span>

<span data-ttu-id="3cdaa-241">`-Verbose:$false` 抑制詳細資訊訊息的顯示。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-241">`-Verbose:$false` suppresses the display of verbose messages.</span></span> <span data-ttu-id="3cdaa-242">當 `$VerbosePreference` (預設) 不會 **SilentlyContinue** 的值時，請使用此參數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-242">Use this parameter when the value of `$VerbosePreference` isn't **SilentlyContinue** (the default).</span></span>

#### <a name="warningaction"></a><span data-ttu-id="3cdaa-243">WarningAction</span><span class="sxs-lookup"><span data-stu-id="3cdaa-243">WarningAction</span></span>

<span data-ttu-id="3cdaa-244">決定 Cmdlet 如何回應命令的警告。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-244">Determines how the cmdlet responds to a warning from the command.</span></span> <span data-ttu-id="3cdaa-245">[ **繼續** ] 是預設值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-245">**Continue** is the default value.</span></span> <span data-ttu-id="3cdaa-246">只有當命令產生警告訊息時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-246">This parameter works only when the command generates a warning message.</span></span> <span data-ttu-id="3cdaa-247">例如，當命令包含 Cmdlet 時，此參數會運作 `Write-Warning` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-247">For example, this parameter works when a command contains the `Write-Warning` cmdlet.</span></span>

```yaml
Type: ActionPreference
Aliases: wa
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="3cdaa-248">**WarningAction** 參數會覆寫 `$WarningPreference` 目前命令的變數值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-248">The **WarningAction** parameter overrides the value of the `$WarningPreference` variable for the current command.</span></span> <span data-ttu-id="3cdaa-249">因為變數的預設值 `$WarningPreference` 為 **Continue** ，所以會顯示警告並繼續執行，除非您使用 **WarningAction** 參數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-249">Because the default value of the `$WarningPreference` variable is **Continue** , warnings are displayed and execution continues unless you use the **WarningAction** parameter.</span></span>

<span data-ttu-id="3cdaa-250">`-WarningAction:Continue` 顯示警告訊息，並繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-250">`-WarningAction:Continue` displays the warning messages and continues executing the command.</span></span> <span data-ttu-id="3cdaa-251">`Continue` 是預設值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-251">`Continue` is the default.</span></span>

<span data-ttu-id="3cdaa-252">`-WarningAction:Inquire` 顯示警告訊息，並在繼續執行之前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-252">`-WarningAction:Inquire` displays the warning message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="3cdaa-253">此值很少使用。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-253">This value is rarely used.</span></span>

<span data-ttu-id="3cdaa-254">`-WarningAction:SilentlyContinue` 隱藏警告訊息，並繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-254">`-WarningAction:SilentlyContinue` suppresses the warning message and continues executing the command.</span></span>

<span data-ttu-id="3cdaa-255">`-WarningAction:Stop` 顯示警告訊息，並停止執行命令。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-255">`-WarningAction:Stop` displays the warning message and stops executing the command.</span></span>

> [!NOTE]
> <span data-ttu-id="3cdaa-256">**WarningAction** 參數會覆寫，但在 `$WarningAction` 命令中使用參數來執行腳本或函式時，不會取代喜好設定變數的值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-256">The **WarningAction** parameter overrides, but does not replace the value of the `$WarningAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="warningvariable"></a><span data-ttu-id="3cdaa-257">WarningVariable</span><span class="sxs-lookup"><span data-stu-id="3cdaa-257">WarningVariable</span></span>

<span data-ttu-id="3cdaa-258">將命令相關警告儲存在指定的變數中。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-258">Stores warnings about the command in the specified variable.</span></span>

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="3cdaa-259">所有產生的警告都會儲存在變數中，即使這些警告不會顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-259">All generated warnings are saved in the variable even if the warnings aren't displayed to the user.</span></span>

<span data-ttu-id="3cdaa-260">若要將警告附加至變數內容，而不是取代任何可能已儲存在該處的警告，請在 `+` 變數名稱之前輸入加號 () 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-260">To append the warnings to the variable content, instead of replacing any warnings that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="3cdaa-261">例如，下列命令 `$a` 會建立變數，並在其中儲存任何警告：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-261">For example, the following command creates the `$a` variable and then stores any warnings in it:</span></span>

```powershell
Get-Process -Id 6 -WarningVariable a
```

<span data-ttu-id="3cdaa-262">下列命令會將任何警告新增至 `$a` 變數：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-262">The following command adds any warnings to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -WarningVariable +a
```

<span data-ttu-id="3cdaa-263">下列命令會顯示的內容 `$a` ：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-263">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="3cdaa-264">您可以使用這個參數來建立只包含特定命令之警告的變數。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-264">You can use this parameter to create a variable that contains only warnings from specific commands.</span></span> <span data-ttu-id="3cdaa-265">您可以使用陣列標記法（例如 `$a[0]` 或） `$warning[1,2]` 來參考儲存在變數中的特定警告。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-265">You can use array notation, such as `$a[0]` or `$warning[1,2]` to refer to specific warnings stored in the variable.</span></span>

> [!NOTE]
> <span data-ttu-id="3cdaa-266">警告變數包含命令所產生的所有警告，包括呼叫嵌套函數或腳本的警告。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-266">The warning variable contains all warnings generated by the command, including warnings from calls to nested functions or scripts.</span></span>
### <a name="risk-management-parameter-descriptions"></a><span data-ttu-id="3cdaa-267">風險管理參數描述</span><span class="sxs-lookup"><span data-stu-id="3cdaa-267">Risk Management Parameter Descriptions</span></span>

#### <a name="whatif"></a><span data-ttu-id="3cdaa-268">WhatIf</span><span class="sxs-lookup"><span data-stu-id="3cdaa-268">WhatIf</span></span>

<span data-ttu-id="3cdaa-269">顯示描述命令效果的訊息，而不是執行命令。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-269">Displays a message that describes the effect of the command, instead of executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="3cdaa-270">**WhatIf** 參數會覆寫 `$WhatIfPreference` 目前命令的變數值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-270">The **WhatIf** parameter overrides the value of the `$WhatIfPreference` variable for the current command.</span></span> <span data-ttu-id="3cdaa-271">因為變數的預設值 `$WhatIfPreference` 為 0 (停用) ，所以不會在沒有 **whatif** 參數的情況下執行 **whatif** 行為。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-271">Because the default value of the `$WhatIfPreference` variable is 0 (disabled), **WhatIf** behavior isn't done without the **WhatIf** parameter.</span></span> <span data-ttu-id="3cdaa-272">如需詳細資訊，請參閱 [about_Preference_Variables](about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="3cdaa-272">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="3cdaa-273">`-WhatIf:$true` 的效果與相同 `-WhatIf` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-273">`-WhatIf:$true` has the same effect as `-WhatIf`.</span></span>

<span data-ttu-id="3cdaa-274">`-WhatIf:$false` 隱藏變數的值為1時，所產生的自動 WhatIf 行為 `$WhatIfPreference` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-274">`-WhatIf:$false` suppresses the automatic WhatIf behavior that results when the value of the `$WhatIfPreference` variable is 1.</span></span>

<span data-ttu-id="3cdaa-275">例如，下列命令會 `-WhatIf` 在命令中使用參數 `Remove-Item` ：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-275">For example, the following command uses the `-WhatIf` parameter in a `Remove-Item` command:</span></span>

```powershell
Remove-Item Date.csv -WhatIf
```

<span data-ttu-id="3cdaa-276">PowerShell 不會移除該專案，而是會列出其所進行的作業，以及會受影響的專案。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-276">Instead of removing the item, PowerShell lists the operations it would do and the items that would be affected.</span></span> <span data-ttu-id="3cdaa-277">此命令會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-277">This command produces the following output:</span></span>

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a><span data-ttu-id="3cdaa-278">確認</span><span class="sxs-lookup"><span data-stu-id="3cdaa-278">Confirm</span></span>

<span data-ttu-id="3cdaa-279">在執行命令之前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-279">Prompts you for confirmation before executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="3cdaa-280">**Confirm** 參數會覆寫 `$ConfirmPreference` 目前命令的變數值。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-280">The **Confirm** parameter overrides the value of the `$ConfirmPreference` variable for the current command.</span></span> <span data-ttu-id="3cdaa-281">預設值為 true。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-281">The default value is true.</span></span> <span data-ttu-id="3cdaa-282">如需詳細資訊，請參閱 [about_Preference_Variables](about_Preference_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="3cdaa-282">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="3cdaa-283">`-Confirm:$true` 的效果與相同 `-Confirm` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-283">`-Confirm:$true` has the same effect as `-Confirm`.</span></span>

<span data-ttu-id="3cdaa-284">`-Confirm:$false` 抑制自動確認，這會在的值 `$ConfirmPreference` 小於或等於 Cmdlet 的預估風險時發生。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-284">`-Confirm:$false` suppresses automatic confirmation, which occurs when the value of `$ConfirmPreference` is less than or equal to the estimated risk of the cmdlet.</span></span>

<span data-ttu-id="3cdaa-285">例如，下列命令會搭配命令使用 **Confirm** 參數 `Remove-Item` 。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-285">For example, the following command uses the **Confirm** parameter with a `Remove-Item` command.</span></span> <span data-ttu-id="3cdaa-286">在移除專案之前，PowerShell 會列出其所進行的作業，以及會受影響的專案，並要求核准。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-286">Before removing the item, PowerShell lists the operations it would do and the items that would be affected, and asks for approval.</span></span>

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

<span data-ttu-id="3cdaa-287">確認回應選項如下所示：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-287">The Confirm response options are as follows:</span></span>

|<span data-ttu-id="3cdaa-288">回應</span><span class="sxs-lookup"><span data-stu-id="3cdaa-288">Response</span></span>       |<span data-ttu-id="3cdaa-289">結果</span><span class="sxs-lookup"><span data-stu-id="3cdaa-289">Result</span></span>                                                     |
|---------------|-----------------------------------------------------------|
|<span data-ttu-id="3cdaa-290">是 (Y) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-290">Yes (Y)</span></span>        |<span data-ttu-id="3cdaa-291">執行動作。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-291">Perform the action.</span></span>                                        |
|<span data-ttu-id="3cdaa-292">是所有 () </span><span class="sxs-lookup"><span data-stu-id="3cdaa-292">Yes to All (A)</span></span> |<span data-ttu-id="3cdaa-293">執行所有動作並隱藏後續的確認查詢</span><span class="sxs-lookup"><span data-stu-id="3cdaa-293">Perform all actions and suppress subsequent Confirm queries</span></span>|
|               |<span data-ttu-id="3cdaa-294">適用于此命令。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-294">for this command.</span></span>                                          |
|<span data-ttu-id="3cdaa-295">無 (N) ：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-295">No (N):</span></span>        |<span data-ttu-id="3cdaa-296">請勿執行此動作。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-296">Do not perform the action.</span></span>                                 |
|<span data-ttu-id="3cdaa-297">所有 (L) ：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-297">No to All (L):</span></span> |<span data-ttu-id="3cdaa-298">請勿執行任何動作，並隱藏後續的確認</span><span class="sxs-lookup"><span data-stu-id="3cdaa-298">Do not perform any actions and suppress subsequent Confirm</span></span> |
|               |<span data-ttu-id="3cdaa-299">此命令的查詢。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-299">queries for this command.</span></span>                                  |
|<span data-ttu-id="3cdaa-300">暫止 (S) ：</span><span class="sxs-lookup"><span data-stu-id="3cdaa-300">Suspend (S):</span></span>   |<span data-ttu-id="3cdaa-301">暫停命令並建立暫時會話。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-301">Pause the command and create a temporary session.</span></span>          |
|<span data-ttu-id="3cdaa-302">協助 (？ ) </span><span class="sxs-lookup"><span data-stu-id="3cdaa-302">Help (?)</span></span>       |<span data-ttu-id="3cdaa-303">顯示這些選項的說明。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-303">Display help for these options.</span></span>                            |

<span data-ttu-id="3cdaa-304">**暫** 止選項會將命令放在保留位置，並建立暫時的嵌套會話，讓您可以在準備好選擇 **確認** 選項之前工作。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-304">The **Suspend** option places the command on hold and creates a temporary nested session in which you can work until you're ready to choose a **Confirm** option.</span></span> <span data-ttu-id="3cdaa-305">嵌套會話的命令提示字元有兩個額外的游標 ( # A2) ，表示它是原始父命令的子系操作。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-305">The command prompt for the nested session has two extra carets (>>) to indicate that it's a child operation of the original parent command.</span></span> <span data-ttu-id="3cdaa-306">您可以在嵌套的會話中執行命令和腳本。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-306">You can run commands and scripts in the nested session.</span></span> <span data-ttu-id="3cdaa-307">若要結束嵌套會話並返回原始命令的 Confirm 選項，請輸入 "exit"。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-307">To end the nested session and return to the Confirm options for the original command, type "exit".</span></span>

<span data-ttu-id="3cdaa-308">在下列範例中，當使用者檢查命令參數的說明時，會使用 **暫停** 選項 (S) 來暫時中止命令。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-308">In the following example, the **Suspend** option (S) is used to halt a command temporarily while the user checks the help for a command parameter.</span></span> <span data-ttu-id="3cdaa-309">取得所需的資訊之後，使用者會輸入 "exit" 來結束嵌套提示字元，然後選取 [是] (y) 回應至 [確認] 查詢。</span><span class="sxs-lookup"><span data-stu-id="3cdaa-309">After obtaining the needed information, the user types "exit" to end the nested prompt and then selects the Yes (y) response to the Confirm query.</span></span>

```
PS C:\ps-test> New-Item -ItemType File -Name Test.txt -Confirm

Confirm
Are you sure you want to perform this action?

Performing operation "Create File" on Target "Destination:
C:\ps-test\test.txt".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default
is "Y"): s

PS C:\ps-test> Get-Help New-Item -Parameter ItemType

-ItemType <string>
Specifies the provider-specified type of the new item.

Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByPropertyName)
Accept wildcard characters?  false

PS C:\ps-test> exit

Confirm
Are you sure you want to perform this action?
Performing operation "Create File" on Target "Destination: C:\ps-test\test
.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (defau
lt is "Y"): y

Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         8/27/2010   2:41 PM          0 test.txt
```

## <a name="keywords"></a><span data-ttu-id="3cdaa-310">關鍵 字</span><span class="sxs-lookup"><span data-stu-id="3cdaa-310">KEYWORDS</span></span>

<span data-ttu-id="3cdaa-311">about_Common_Parameters</span><span class="sxs-lookup"><span data-stu-id="3cdaa-311">about_Common_Parameters</span></span>

## <a name="see-also"></a><span data-ttu-id="3cdaa-312">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cdaa-312">SEE ALSO</span></span>

[<span data-ttu-id="3cdaa-313">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="3cdaa-313">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="3cdaa-314">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="3cdaa-314">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)

[<span data-ttu-id="3cdaa-315">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="3cdaa-315">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)

[<span data-ttu-id="3cdaa-316">Write-Error</span><span class="sxs-lookup"><span data-stu-id="3cdaa-316">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)

[<span data-ttu-id="3cdaa-317">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="3cdaa-317">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
