---
description: 說明如何在 PowerShell 中使用命令參數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: 47965b1b1ecb1bde47dfc45f9169fa355223ed09
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207008"
---
# <a name="about-parameters"></a><span data-ttu-id="96d2a-104">關於參數</span><span class="sxs-lookup"><span data-stu-id="96d2a-104">About Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="96d2a-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="96d2a-105">Short description</span></span>
<span data-ttu-id="96d2a-106">說明如何在 PowerShell 中使用命令參數。</span><span class="sxs-lookup"><span data-stu-id="96d2a-106">Describes how to work with command parameters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="96d2a-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="96d2a-107">Long description</span></span>

<span data-ttu-id="96d2a-108">大部分的 PowerShell 命令（例如 Cmdlet、函式和腳本）都會依賴參數，讓使用者選取選項或提供輸入。</span><span class="sxs-lookup"><span data-stu-id="96d2a-108">Most PowerShell commands, such as cmdlets, functions, and scripts, rely on parameters to allow users to select options or provide input.</span></span> <span data-ttu-id="96d2a-109">參數會遵循命令名稱，且具有下列格式：</span><span class="sxs-lookup"><span data-stu-id="96d2a-109">The parameters follow the command name and have the following form:</span></span>

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

<span data-ttu-id="96d2a-110">參數的名稱前面會加上連字號 (-) ，它會向 PowerShell 表示連字號後面的單字是參數名稱。</span><span class="sxs-lookup"><span data-stu-id="96d2a-110">The name of the parameter is preceded by a hyphen (-), which signals to PowerShell that the word following the hyphen is a parameter name.</span></span> <span data-ttu-id="96d2a-111">參數名稱和值可以用空格或冒號字元分隔。</span><span class="sxs-lookup"><span data-stu-id="96d2a-111">The parameter name and value can be separated by a space or a colon character.</span></span> <span data-ttu-id="96d2a-112">某些參數不需要或接受參數值。</span><span class="sxs-lookup"><span data-stu-id="96d2a-112">Some parameters do not require or accept a parameter value.</span></span> <span data-ttu-id="96d2a-113">其他參數則需要值，但不需要在命令中使用參數名稱。</span><span class="sxs-lookup"><span data-stu-id="96d2a-113">Other parameters require a value, but do not require the parameter name in the command.</span></span>

<span data-ttu-id="96d2a-114">參數的類型和這些參數的需求會有所不同。</span><span class="sxs-lookup"><span data-stu-id="96d2a-114">The type of parameters and the requirements for those parameters vary.</span></span> <span data-ttu-id="96d2a-115">若要尋找命令參數的相關資訊，請使用 `Get-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="96d2a-115">To find information about the parameters of a command, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="96d2a-116">例如，若要尋找有關 Cmdlet 參數的資訊 `Get-ChildItem` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="96d2a-116">For example, to find information about the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="96d2a-117">若要尋找腳本參數的相關資訊，請使用指令檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="96d2a-117">To find information about the parameters of a script, use the full path to the script file.</span></span> <span data-ttu-id="96d2a-118">例如：</span><span class="sxs-lookup"><span data-stu-id="96d2a-118">For example:</span></span>

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

<span data-ttu-id="96d2a-119">Cmdlet 會傳回 `Get-Help` 與命令相關的各種詳細資料，包括描述、命令語法、參數的相關資訊，以及示範如何在命令中使用參數的範例。</span><span class="sxs-lookup"><span data-stu-id="96d2a-119">The `Get-Help` cmdlet returns various details about the command, including a description, the command syntax, information about the parameters, and examples showing how to use the parameters in a command.</span></span>

<span data-ttu-id="96d2a-120">您也可以使用 Cmdlet 的參數參數 `Get-Help` 來尋找特定參數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="96d2a-120">You can also use the Parameter parameter of the `Get-Help` cmdlet to find information about a particular parameter.</span></span> <span data-ttu-id="96d2a-121">或者，您可以使用 **參數** 參數搭配萬用字元 ( `*` ) 值來尋找命令之所有參數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="96d2a-121">Or, you can use the **Parameter** parameter with the wildcard character ( `*` ) value to find information about all parameters of the command.</span></span> <span data-ttu-id="96d2a-122">例如，下列命令會取得 Cmdlet 之所有參數的相關資訊 `Get-Member` ：</span><span class="sxs-lookup"><span data-stu-id="96d2a-122">For example, the following command gets information about all parameters of the `Get-Member` cmdlet:</span></span>

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a><span data-ttu-id="96d2a-123">預設參數值</span><span class="sxs-lookup"><span data-stu-id="96d2a-123">Default parameter values</span></span>

<span data-ttu-id="96d2a-124">選擇性參數有預設值，也就是當命令中未指定參數時，所使用或假設的值。</span><span class="sxs-lookup"><span data-stu-id="96d2a-124">Optional parameters have a default value, which is the value that is used or assumed when the parameter is not specified in the command.</span></span>

<span data-ttu-id="96d2a-125">例如，許多 Cmdlet 的 **ComputerName** 參數預設值是本機電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="96d2a-125">For example, the default value of the **ComputerName** parameter of many cmdlets is the name of the local computer.</span></span> <span data-ttu-id="96d2a-126">如此一來，除非指定 **ComputerName** 參數，否則命令會使用本機電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="96d2a-126">As a result, the local computer name is used in the command unless the **ComputerName** parameter is specified.</span></span>

<span data-ttu-id="96d2a-127">若要尋找預設參數值，請參閱 Cmdlet 的說明主題。</span><span class="sxs-lookup"><span data-stu-id="96d2a-127">To find the default parameter value, see help topic for the cmdlet.</span></span> <span data-ttu-id="96d2a-128">參數描述應該包含預設值。</span><span class="sxs-lookup"><span data-stu-id="96d2a-128">The parameter description should include the default value.</span></span>

<span data-ttu-id="96d2a-129">您也可以為 Cmdlet 或 advanced 函數的任何參數設定自訂的預設值。</span><span class="sxs-lookup"><span data-stu-id="96d2a-129">You can also set a custom default value for any parameter of a cmdlet or advanced function.</span></span> <span data-ttu-id="96d2a-130">如需設定自訂預設值的詳細資訊，請參閱 [about_Parameters_Default_Values](about_Parameters_Default_Values.md)。</span><span class="sxs-lookup"><span data-stu-id="96d2a-130">For information about setting custom default values, see [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span></span>

### <a name="parameter-attribute-table"></a><span data-ttu-id="96d2a-131">參數屬性工作表</span><span class="sxs-lookup"><span data-stu-id="96d2a-131">Parameter attribute table</span></span>

<span data-ttu-id="96d2a-132">當您使用指令程式的 **完整** 、 **參數** 或 **線上** 參數時 `Get-Help` ，會 `Get-Help` 顯示參數屬性工作表，其中包含參數的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="96d2a-132">When you use the **Full** , **Parameter** , or **Online** parameters of the `Get-Help` cmdlet, `Get-Help` displays a parameter attribute table with detailed information about the parameter.</span></span>

<span data-ttu-id="96d2a-133">此資訊包含使用參數所需知道的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="96d2a-133">This information includes the details you need to know to use the parameter.</span></span>
<span data-ttu-id="96d2a-134">例如，Cmdlet 的說明主題 `Get-ChildItem` 包含其 Path 參數的下列詳細資料：</span><span class="sxs-lookup"><span data-stu-id="96d2a-134">For example, the help topic for the `Get-ChildItem` cmdlet includes the following details about its Path parameter:</span></span>

```
-path <string[]>
    Specifies a path of one or more locations. Wildcard characters are
    permitted. The default location is the current directory (.).

Required?                    false
Position?                    0
Default value                Current directory
Accept pipeline input?       true (ByValue, ByPropertyName)
Accept wildcard characters?  true
```

<span data-ttu-id="96d2a-135">參數資訊包括參數語法、參數的描述，以及參數屬性。</span><span class="sxs-lookup"><span data-stu-id="96d2a-135">The parameter information includes the parameter syntax, a description of the parameter, and the parameter attributes.</span></span> <span data-ttu-id="96d2a-136">下列各節說明參數屬性。</span><span class="sxs-lookup"><span data-stu-id="96d2a-136">The following sections describe the parameter attributes.</span></span>

#### <a name="parameter-required"></a><span data-ttu-id="96d2a-137">需要參數</span><span class="sxs-lookup"><span data-stu-id="96d2a-137">Parameter Required</span></span>

<span data-ttu-id="96d2a-138">這項設定會指出參數是否為強制性，也就是使用此 Cmdlet 的所有命令都必須包含此參數。</span><span class="sxs-lookup"><span data-stu-id="96d2a-138">This setting indicates whether the parameter is mandatory, that is, whether all commands that use this cmdlet must include this parameter.</span></span> <span data-ttu-id="96d2a-139">當此值為 **True** ，且命令缺少參數時，PowerShell 會提示您輸入參數的值。</span><span class="sxs-lookup"><span data-stu-id="96d2a-139">When the value is **True** and the parameter is missing from the command, PowerShell prompts you for a value for the parameter.</span></span>

#### <a name="parameter-position"></a><span data-ttu-id="96d2a-140">參數位置</span><span class="sxs-lookup"><span data-stu-id="96d2a-140">Parameter Position</span></span>

<span data-ttu-id="96d2a-141">如果設定為 `Position` 正整數，則不需要參數名稱。</span><span class="sxs-lookup"><span data-stu-id="96d2a-141">If the `Position` setting is set to a positive integer, the parameter name is not required.</span></span> <span data-ttu-id="96d2a-142">這種類型的參數稱為位置參數，而數位則表示參數必須與其他位置參數相對應的出現位置。</span><span class="sxs-lookup"><span data-stu-id="96d2a-142">This type of parameter is referred to as a positional parameter, and the number indicates the position in which the parameter must appear in relation to other positional parameters.</span></span> <span data-ttu-id="96d2a-143">具名引數可以列在 Cmdlet 名稱後面的任何位置。</span><span class="sxs-lookup"><span data-stu-id="96d2a-143">A named parameter can be listed in any position after the cmdlet name.</span></span> <span data-ttu-id="96d2a-144">如果您包含位置參數的參數名稱，參數可以列在 Cmdlet 名稱後面的任何位置。</span><span class="sxs-lookup"><span data-stu-id="96d2a-144">If you include the parameter name for a positional parameter, the parameter can be listed in any position after the cmdlet name.</span></span>

<span data-ttu-id="96d2a-145">例如， `Get-ChildItem` Cmdlet 具有 Path 和 Exclude 參數。</span><span class="sxs-lookup"><span data-stu-id="96d2a-145">For example, the `Get-ChildItem` cmdlet has Path and Exclude parameters.</span></span> <span data-ttu-id="96d2a-146">`Position`**路徑** 的設定為 **0** ，表示它是位置參數。</span><span class="sxs-lookup"><span data-stu-id="96d2a-146">The `Position` setting for **Path** is **0** , which means that it is a positional parameter.</span></span> <span data-ttu-id="96d2a-147">[ `Position` **排除** ] 的設定 **名** 為。</span><span class="sxs-lookup"><span data-stu-id="96d2a-147">The `Position` setting for **Exclude** is **named** .</span></span>

<span data-ttu-id="96d2a-148">這表示 **路徑** 不需要參數名稱，但其參數值必須是命令中的第一個或唯一未命名的參數值。</span><span class="sxs-lookup"><span data-stu-id="96d2a-148">This means that **Path** does not require the parameter name, but its parameter value must be the first or only unnamed parameter value in the command.</span></span>
<span data-ttu-id="96d2a-149">不過，因為 Exclude 參數是一個具名引數，所以您可以將它放在命令中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="96d2a-149">However, because the Exclude parameter is a named parameter, you can place it in any position in the command.</span></span>

<span data-ttu-id="96d2a-150">由於 `Position` 這兩個參數的設定，您可以使用下列任何一個命令：</span><span class="sxs-lookup"><span data-stu-id="96d2a-150">As a result of the `Position` settings for these two parameters, you can use any of the following commands:</span></span>

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

<span data-ttu-id="96d2a-151">如果您要包含不包含參數名稱的另一個位置參數，該參數必須依照設定所指定的順序來放置 `Position` 。</span><span class="sxs-lookup"><span data-stu-id="96d2a-151">If you were to include another positional parameter without including the parameter name, that parameter must be placed in the order specified by the `Position` setting.</span></span>

#### <a name="parameter-type"></a><span data-ttu-id="96d2a-152">參數類型</span><span class="sxs-lookup"><span data-stu-id="96d2a-152">Parameter Type</span></span>

<span data-ttu-id="96d2a-153">這項設定會指定 Microsoft .NET Framework 類型的參數值。</span><span class="sxs-lookup"><span data-stu-id="96d2a-153">This setting specifies the Microsoft .NET Framework type of the parameter value.</span></span> <span data-ttu-id="96d2a-154">例如，如果類型是 **Int32** ，則參數值必須是整數。</span><span class="sxs-lookup"><span data-stu-id="96d2a-154">For example, if the type is **Int32** , the parameter value must be an integer.</span></span> <span data-ttu-id="96d2a-155">如果類型是字串，參數值必須是字元字串。</span><span class="sxs-lookup"><span data-stu-id="96d2a-155">If the type is string, the parameter value must be a character string.</span></span> <span data-ttu-id="96d2a-156">如果字串包含空格，則值必須以引號括住，或空格前面必須加上 escape 字元 ( ' ) 。</span><span class="sxs-lookup"><span data-stu-id="96d2a-156">If the string contains spaces, the value must be enclosed in quotation marks, or the spaces must be preceded by the escape character ( \` ).</span></span>

#### <a name="default-value"></a><span data-ttu-id="96d2a-157">預設值</span><span class="sxs-lookup"><span data-stu-id="96d2a-157">Default Value</span></span>

<span data-ttu-id="96d2a-158">如果未提供其他值，此設定會指定參數將假設的值。</span><span class="sxs-lookup"><span data-stu-id="96d2a-158">This setting specifies the value that the parameter will assume if no other value is provided.</span></span> <span data-ttu-id="96d2a-159">例如，Path 參數的預設值通常是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="96d2a-159">For example, the default value of the Path parameter is often the current directory.</span></span> <span data-ttu-id="96d2a-160">必要參數永遠沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="96d2a-160">Required parameters never have a default value.</span></span>
<span data-ttu-id="96d2a-161">針對許多選擇性參數，沒有預設值，因為參數未使用時，不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="96d2a-161">For many optional parameters, there is no default because the parameter has no effect if it is not used.</span></span>

#### <a name="accepts-multiple-values"></a><span data-ttu-id="96d2a-162">接受多個值</span><span class="sxs-lookup"><span data-stu-id="96d2a-162">Accepts Multiple Values</span></span>

<span data-ttu-id="96d2a-163">這項設定會指出參數是否接受多個參數值。</span><span class="sxs-lookup"><span data-stu-id="96d2a-163">This setting indicates whether a parameter accepts multiple parameter values.</span></span>
<span data-ttu-id="96d2a-164">當參數接受多個值時，您可以在命令中輸入以逗號分隔的清單做為參數的值，或將逗號分隔清單儲存 (變數中的陣列) ，然後將變數指定為參數值。</span><span class="sxs-lookup"><span data-stu-id="96d2a-164">When a parameter accepts multiple values, you can type a comma-separated list as the value of the parameter in the command, or save a comma-separated list (an array) in a variable, and then specify the variable as the parameter value.</span></span>

<span data-ttu-id="96d2a-165">例如，Cmdlet 的 ServiceName 參數 `Get-Service` 接受多個值。</span><span class="sxs-lookup"><span data-stu-id="96d2a-165">For example, the ServiceName parameter of the `Get-Service` cmdlet accepts multiple values.</span></span> <span data-ttu-id="96d2a-166">下列命令都有效：</span><span class="sxs-lookup"><span data-stu-id="96d2a-166">The following commands are both valid:</span></span>

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a><span data-ttu-id="96d2a-167">接受管線輸入</span><span class="sxs-lookup"><span data-stu-id="96d2a-167">Accepts Pipeline Input</span></span>

<span data-ttu-id="96d2a-168">此設定會指出您是否可以使用管線運算子 ( `|` ) 將值傳送至參數。</span><span class="sxs-lookup"><span data-stu-id="96d2a-168">This setting indicates whether you can use the pipeline operator ( `|` ) to send a value to the parameter.</span></span>

```
Value                    Description
-----                    -----------
False                    Indicates that you cannot pipe a value to the
                         parameter.

True (by Value)          Indicates that you can pipe any value to the
                         parameter, just so the value has the .NET
                         Framework type specified for the parameter or the
                         value can be converted to the specified .NET
                         Framework type.
```

<span data-ttu-id="96d2a-169">當參數為 "True (by Value) " 時，PowerShell 會嘗試將任何輸送的值與該參數產生關聯，然後再嘗試其他方法來解讀命令。</span><span class="sxs-lookup"><span data-stu-id="96d2a-169">When a parameter is "True (by Value)", PowerShell tries to associate any piped values with that parameter before it tries other methods to interpret the command.</span></span>

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

<span data-ttu-id="96d2a-170">例如，只有當值具有名為 **name** 的屬性時，您才可以使用管線將值傳送至 **name** 參數。</span><span class="sxs-lookup"><span data-stu-id="96d2a-170">For example, you can pipe a value to a **Name** parameter only when the value has a property called **Name** .</span></span>

> [!NOTE]
> <span data-ttu-id="96d2a-171">接受管線輸入 (`by Value`) 或 (`by PropertyName`) 可在參數上使用 **延遲** 系結腳本區塊的型別參數。</span><span class="sxs-lookup"><span data-stu-id="96d2a-171">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
>
> <span data-ttu-id="96d2a-172">**延遲** 系結腳本區塊會在 **ParameterBinding** 期間自動執行。</span><span class="sxs-lookup"><span data-stu-id="96d2a-172">The **delay-bind** script block is run automatically during **ParameterBinding** .</span></span> <span data-ttu-id="96d2a-173">結果會系結至參數。</span><span class="sxs-lookup"><span data-stu-id="96d2a-173">The result is bound to the parameter.</span></span> <span data-ttu-id="96d2a-174">延遲系結 **不適用於** 定義為類型 `ScriptBlock` 或的參數 `System.Object` ，而是在未叫用的 **情況** 下傳遞腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="96d2a-174">Delay binding does **not** work for parameters defined as type `ScriptBlock` or `System.Object`, the script block is passed through **without** being invoked.</span></span>
>
> <span data-ttu-id="96d2a-175">您可以在這裡閱讀 **延遲** 系結腳本區塊 [about_Script_Blocks md](about_Script_Blocks.md)</span><span class="sxs-lookup"><span data-stu-id="96d2a-175">You can read about **delay-bind** script blocks here [about_Script_Blocks.md](about_Script_Blocks.md)</span></span>

#### <a name="accepts-wildcard-characters"></a><span data-ttu-id="96d2a-176">接受萬用字元</span><span class="sxs-lookup"><span data-stu-id="96d2a-176">Accepts Wildcard Characters</span></span>

<span data-ttu-id="96d2a-177">這項設定會指出參數的值是否可以包含萬用字元，以便讓參數值符合目標容器中的一個以上現有專案。</span><span class="sxs-lookup"><span data-stu-id="96d2a-177">This setting indicates whether the parameter's value can contain wildcard characters so that the parameter value can be matched to more than one existing item in the target container.</span></span>

#### <a name="common-parameters"></a><span data-ttu-id="96d2a-178">一般參數</span><span class="sxs-lookup"><span data-stu-id="96d2a-178">Common Parameters</span></span>

<span data-ttu-id="96d2a-179">一般參數是您可以搭配任何 Cmdlet 使用的參數。</span><span class="sxs-lookup"><span data-stu-id="96d2a-179">Common parameters are parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="96d2a-180">如需一般參數的詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="96d2a-180">For more information about common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="96d2a-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96d2a-181">See also</span></span>

[<span data-ttu-id="96d2a-182">about_Command_syntax</span><span class="sxs-lookup"><span data-stu-id="96d2a-182">about_Command_syntax</span></span>](about_Command_syntax.md)

[<span data-ttu-id="96d2a-183">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="96d2a-183">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="96d2a-184">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="96d2a-184">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="96d2a-185">about_Parameters_Default_Values</span><span class="sxs-lookup"><span data-stu-id="96d2a-185">about_Parameters_Default_Values</span></span>](about_Parameters_Default_Values.md)

[<span data-ttu-id="96d2a-186">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="96d2a-186">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="96d2a-187">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="96d2a-187">about_Wildcards</span></span>](about_Wildcards.md)
