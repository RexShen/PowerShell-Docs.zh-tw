---
description: 說明如何將參數加入至 advanced 函數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: 4123d71392f8b32df8d04033d85476cb18b39736
ms.sourcegitcommit: 3b1779890f828130a9d73aebf17ebffae511728f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "93208912"
---
# <a name="about-functions-advanced-parameters"></a><span data-ttu-id="be241-104">關於函數的 Advanced 參數</span><span class="sxs-lookup"><span data-stu-id="be241-104">About Functions Advanced Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="be241-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="be241-105">Short description</span></span>

<span data-ttu-id="be241-106">說明如何將參數加入至 advanced 函數。</span><span class="sxs-lookup"><span data-stu-id="be241-106">Explains how to add parameters to advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="be241-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="be241-107">Long description</span></span>

<span data-ttu-id="be241-108">您可以將參數加入至您所撰寫的 advanced 函數，並使用參數屬性和引數來限制函式使用者以參數提交的參數值。</span><span class="sxs-lookup"><span data-stu-id="be241-108">You can add parameters to the advanced functions that you write, and use parameter attributes and arguments to limit the parameter values that function users submit with the parameter.</span></span>

<span data-ttu-id="be241-109">除了 PowerShell 自動新增至所有 Cmdlet 和 advanced 函數的一般參數之外，您新增至函式的參數也可供使用者使用。</span><span class="sxs-lookup"><span data-stu-id="be241-109">The parameters that you add to your function are available to users in addition to the common parameters that PowerShell adds automatically to all cmdlets and advanced functions.</span></span> <span data-ttu-id="be241-110">如需 PowerShell 一般參數的詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="be241-110">For more information about the PowerShell common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="be241-111">從 PowerShell 3.0 開始，您可以使用展開搭配 `@Args` 來代表命令中的參數。</span><span class="sxs-lookup"><span data-stu-id="be241-111">Beginning in PowerShell 3.0, you can use splatting with `@Args` to represent the parameters in a command.</span></span> <span data-ttu-id="be241-112">展開適用于簡單和先進的函式。</span><span class="sxs-lookup"><span data-stu-id="be241-112">Splatting is valid on simple and advanced functions.</span></span> <span data-ttu-id="be241-113">如需詳細資訊，請參閱 [about_Functions](about_Functions.md) 和 [about_Splatting](about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="be241-113">For more information, see [about_Functions](about_Functions.md) and [about_Splatting](about_Splatting.md).</span></span>

## <a name="type-conversion-of-parameter-values"></a><span data-ttu-id="be241-114">參數值的類型轉換</span><span class="sxs-lookup"><span data-stu-id="be241-114">Type conversion of parameter values</span></span>

<span data-ttu-id="be241-115">當您將字串作為引數提供給預期不同類型的參數時，PowerShell 會以隱含方式將字串轉換為參數目標型別。</span><span class="sxs-lookup"><span data-stu-id="be241-115">When you supply strings as arguments to parameters that expect a different type, PowerShell implicitly converts the strings to the parameter target type.</span></span>
<span data-ttu-id="be241-116">Advanced 函式會執行參數值的文化特性不變剖析。</span><span class="sxs-lookup"><span data-stu-id="be241-116">Advanced functions perform culture-invariant parsing of parameter values.</span></span>

<span data-ttu-id="be241-117">相反地，在編譯的 Cmdlet 的參數系結期間會執行區分文化特性的轉換。</span><span class="sxs-lookup"><span data-stu-id="be241-117">By contrast, a culture-sensitive conversion is performed during parameter binding for compiled cmdlets.</span></span>

<span data-ttu-id="be241-118">在此範例中，我們會建立 Cmdlet，以及使用參數的腳本函式 `[datetime]` 。</span><span class="sxs-lookup"><span data-stu-id="be241-118">In this example, we create a cmdlet and a script function that take a `[datetime]` parameter.</span></span> <span data-ttu-id="be241-119">目前的文化特性已變更為使用德文設定。</span><span class="sxs-lookup"><span data-stu-id="be241-119">The current culture is changed to use German settings.</span></span>
<span data-ttu-id="be241-120">德文格式的日期會傳遞至參數。</span><span class="sxs-lookup"><span data-stu-id="be241-120">A German-formatted date is passed to the parameter.</span></span>

```powershell
# Create a cmdlet that accepts a [datetime] argument.
Add-Type @'
  using System;
  using System.Management.Automation;
  [Cmdlet("Get", "Date_Cmdlet")]
  public class GetFooCmdlet : Cmdlet {

    [Parameter(Position=0)]
    public DateTime Date { get; set; }

    protected override void ProcessRecord() {
      WriteObject(Date);
    }
  }
'@ -PassThru | % Assembly | Import-Module

[cultureinfo]::CurrentCulture = 'de-DE'
$dateStr = '19-06-2018'

Get-Date_Cmdlet $dateStr
```

```Output
Dienstag, 19. Juni 2018 00:00:00
```

<span data-ttu-id="be241-121">如上所示，Cmdlet 會使用區分文化特性的剖析來轉換字串。</span><span class="sxs-lookup"><span data-stu-id="be241-121">As shown above, cmdlets use culture-sensitive parsing to convert the string.</span></span>

```powershell
# Define an equivalent function.
function Get-Date_Func {
  param(
    [DateTime] $Date
  )
  process {
    $Date
  }
}

[cultureinfo]::CurrentCulture = 'de-DE'

# This German-format date string doesn't work with the invariant culture.
# E.g., [datetime] '19-06-2018' breaks.
$dateStr = '19-06-2018'

Get-Date_Func $dateStr
```

<span data-ttu-id="be241-122">Advanced 函數使用文化特性非變異剖析，這會導致下列錯誤。</span><span class="sxs-lookup"><span data-stu-id="be241-122">Advanced functions use culture-invariant parsing, which results in the following error.</span></span>

```Output
Get-Date_Func : Cannot process argument transformation on parameter 'Date'. Cannot convert
 value "19-06-2018" to type "System.DateTime". Error: "String was not recognized as a valid
 DateTime."
At line:13 char:15
+ Get-Date_Func $dateStr
+               ~~~~~~~~
    + CategoryInfo          : InvalidData: (:) [Get-Date_Func], ParameterBindingArgumentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Get-Date_Func
```

## <a name="static-parameters"></a><span data-ttu-id="be241-123">靜態參數</span><span class="sxs-lookup"><span data-stu-id="be241-123">Static parameters</span></span>

<span data-ttu-id="be241-124">靜態參數是函數中永遠可用的參數。</span><span class="sxs-lookup"><span data-stu-id="be241-124">Static parameters are parameters that are always available in the function.</span></span>
<span data-ttu-id="be241-125">PowerShell Cmdlet 和腳本中的大部分參數都是靜態參數。</span><span class="sxs-lookup"><span data-stu-id="be241-125">Most parameters in PowerShell cmdlets and scripts are static parameters.</span></span>

<span data-ttu-id="be241-126">下列範例顯示具有下列特性之 **ComputerName** 參數的宣告：</span><span class="sxs-lookup"><span data-stu-id="be241-126">The following example shows the declaration of a **ComputerName** parameter that has the following characteristics:</span></span>

- <span data-ttu-id="be241-127">這是必要的 (需要) 。</span><span class="sxs-lookup"><span data-stu-id="be241-127">It's mandatory (required).</span></span>
- <span data-ttu-id="be241-128">它會接受來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="be241-128">It takes input from the pipeline.</span></span>
- <span data-ttu-id="be241-129">它接受字串陣列做為輸入。</span><span class="sxs-lookup"><span data-stu-id="be241-129">It takes an array of strings as input.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a><span data-ttu-id="be241-130">參數的屬性</span><span class="sxs-lookup"><span data-stu-id="be241-130">Attributes of parameters</span></span>

<span data-ttu-id="be241-131">本節說明您可以新增至函式參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="be241-131">This section describes the attributes that you can add to function parameters.</span></span>

<span data-ttu-id="be241-132">所有屬性都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="be241-132">All attributes are optional.</span></span> <span data-ttu-id="be241-133">但是，如果您省略 **CmdletBinding** 屬性，然後將它辨識為 advanced 函數，則函式必須包含 **參數** 屬性。</span><span class="sxs-lookup"><span data-stu-id="be241-133">However, if you omit the **CmdletBinding** attribute, then to be recognized as an advanced function, the function must include the **Parameter** attribute.</span></span>

<span data-ttu-id="be241-134">您可以在每個參數宣告中加入一個或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="be241-134">You can add one or multiple attributes in each parameter declaration.</span></span> <span data-ttu-id="be241-135">您可以加入至參數宣告的屬性數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="be241-135">There's no limit to the number of attributes that you can add to a parameter declaration.</span></span>

### <a name="parameter-attribute"></a><span data-ttu-id="be241-136">參數屬性</span><span class="sxs-lookup"><span data-stu-id="be241-136">Parameter attribute</span></span>

<span data-ttu-id="be241-137">**Parameter** 屬性是用來宣告函數參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="be241-137">The **Parameter** attribute is used to declare the attributes of function parameters.</span></span>

<span data-ttu-id="be241-138">**參數** 屬性是選擇性的，如果函式的任何參數都不需要屬性，您就可以省略它。</span><span class="sxs-lookup"><span data-stu-id="be241-138">The **Parameter** attribute is optional, and you can omit it if none of the parameters of your functions need attributes.</span></span> <span data-ttu-id="be241-139">但是，若要被辨識為 advanced 函式，而不是簡單的函式，則函式必須有 **CmdletBinding** 屬性或 **參數** 屬性，或兩者都是。</span><span class="sxs-lookup"><span data-stu-id="be241-139">But, to be recognized as an advanced function, rather than a simple function, a function must have either the **CmdletBinding** attribute or the **Parameter** attribute, or both.</span></span>

<span data-ttu-id="be241-140">**Parameter** 屬性有定義參數特性的引數，例如參數是否為強制性或選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="be241-140">The **Parameter** attribute has arguments that define the characteristics of the parameter, such as whether the parameter is mandatory or optional.</span></span>

<span data-ttu-id="be241-141">使用下列語法來宣告 **參數** 屬性、引數和引數值。</span><span class="sxs-lookup"><span data-stu-id="be241-141">Use the following syntax to declare the **Parameter** attribute, an argument, and an argument value.</span></span> <span data-ttu-id="be241-142">括住引數和其值的括弧必須緊接在無中間空間的 **參數** 。</span><span class="sxs-lookup"><span data-stu-id="be241-142">The parentheses that enclose the argument and its value must follow **Parameter** with no intervening space.</span></span>

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

<span data-ttu-id="be241-143">使用逗號來分隔括弧內的引數。</span><span class="sxs-lookup"><span data-stu-id="be241-143">Use commas to separate arguments within the parentheses.</span></span> <span data-ttu-id="be241-144">使用下列語法來宣告 **參數** 屬性的兩個引數。</span><span class="sxs-lookup"><span data-stu-id="be241-144">Use the following syntax to declare two arguments of the **Parameter** attribute.</span></span>

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

<span data-ttu-id="be241-145">從 **參數** 屬性省略時， **參數** 屬性的布林引數類型預設為 **False** 。</span><span class="sxs-lookup"><span data-stu-id="be241-145">The boolean argument types of the **Parameter** attribute default to **False** when omitted from the **Parameter** attribute.</span></span> <span data-ttu-id="be241-146">將引數值設定為， `$true` 或只依名稱列出引數。</span><span class="sxs-lookup"><span data-stu-id="be241-146">Set the argument value to `$true` or just list the argument by name.</span></span> <span data-ttu-id="be241-147">例如，下列 **參數** 屬性是相等的。</span><span class="sxs-lookup"><span data-stu-id="be241-147">For example, the following **Parameter** attributes are equivalent.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

<span data-ttu-id="be241-148">如果您使用不含引數的 **Parameter** 屬性（attribute）做為使用 **CmdletBinding** 屬性的替代方案，則仍然需要在屬性名稱後面加上括弧。</span><span class="sxs-lookup"><span data-stu-id="be241-148">If you use the **Parameter** attribute without arguments, as an alternative to using the **CmdletBinding** attribute, the parentheses that follow the attribute name are still required.</span></span>

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a><span data-ttu-id="be241-149">強制引數</span><span class="sxs-lookup"><span data-stu-id="be241-149">Mandatory argument</span></span>

<span data-ttu-id="be241-150">`Mandatory`引數表示需要參數。</span><span class="sxs-lookup"><span data-stu-id="be241-150">The `Mandatory` argument indicates that the parameter is required.</span></span> <span data-ttu-id="be241-151">如果未指定這個引數，則參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="be241-151">If this argument isn't specified, the parameter is optional.</span></span>

<span data-ttu-id="be241-152">下列範例會宣告 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="be241-152">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="be241-153">它會使用 `Mandatory` 引數讓參數變成強制參數。</span><span class="sxs-lookup"><span data-stu-id="be241-153">It uses the `Mandatory` argument to make the parameter mandatory.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a><span data-ttu-id="be241-154">Position 引數</span><span class="sxs-lookup"><span data-stu-id="be241-154">Position argument</span></span>

<span data-ttu-id="be241-155">`Position`當命令中使用參數時，引數會決定是否需要參數名稱。</span><span class="sxs-lookup"><span data-stu-id="be241-155">The `Position` argument determines whether the parameter name is required when the parameter is used in a command.</span></span> <span data-ttu-id="be241-156">當參數宣告包含 `Position` 引數時，可以省略參數名稱，而 PowerShell 會依據命令中未具名引數值清單中的位置或順序來識別未命名的參數值。</span><span class="sxs-lookup"><span data-stu-id="be241-156">When a parameter declaration includes the `Position` argument, the parameter name can be omitted and PowerShell identifies the unnamed parameter value by its position, or order, in the list of unnamed parameter values in the command.</span></span>

<span data-ttu-id="be241-157">如果 `Position` 未指定引數，參數名稱或參數名稱別名或縮寫在命令中使用參數時，必須在參數值之前。</span><span class="sxs-lookup"><span data-stu-id="be241-157">If the `Position` argument isn't specified, the parameter name, or a parameter name alias or abbreviation, must precede the parameter value whenever the parameter is used in a command.</span></span>

<span data-ttu-id="be241-158">依預設，所有函數參數都是位置。</span><span class="sxs-lookup"><span data-stu-id="be241-158">By default, all function parameters are positional.</span></span> <span data-ttu-id="be241-159">PowerShell 會依照在函式中宣告參數的順序，將位置編號指派給參數。</span><span class="sxs-lookup"><span data-stu-id="be241-159">PowerShell assigns position numbers to parameters in the order in which the parameters are declared in the function.</span></span> <span data-ttu-id="be241-160">若要停用此功能，請將 `PositionalBinding` **CmdletBinding** 屬性的引數值設定為 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="be241-160">To disable this feature, set the value of the `PositionalBinding` argument of the **CmdletBinding** attribute to `$False`.</span></span> <span data-ttu-id="be241-161">`Position`引數優先于 `PositionalBinding` **CmdletBinding** 屬性的引數值。</span><span class="sxs-lookup"><span data-stu-id="be241-161">The `Position` argument takes precedence over the value of the `PositionalBinding` argument of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="be241-162">如需詳細資訊，請參閱 `PositionalBinding` [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)中的。</span><span class="sxs-lookup"><span data-stu-id="be241-162">For more information, see `PositionalBinding` in [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="be241-163">引數的值 `Position` 會指定為整數。</span><span class="sxs-lookup"><span data-stu-id="be241-163">The value of the `Position` argument is specified as an integer.</span></span> <span data-ttu-id="be241-164">位置值 **0** 代表命令中的第一個位置，位置值 **1** 代表命令中的第二個位置，依此類推。</span><span class="sxs-lookup"><span data-stu-id="be241-164">A position value of **0** represents the first position in the command, a position value of **1** represents the second position in the command, and so on.</span></span>

<span data-ttu-id="be241-165">如果函式沒有位置參數，則 PowerShell 會根據參數的宣告順序，將位置指派給每個參數。</span><span class="sxs-lookup"><span data-stu-id="be241-165">If a function has no positional parameters, PowerShell assigns positions to each parameter based on the order in which the parameters are declared.</span></span>
<span data-ttu-id="be241-166">不過，最佳作法是不要依賴此指派。</span><span class="sxs-lookup"><span data-stu-id="be241-166">However, as a best practice, don't rely on this assignment.</span></span> <span data-ttu-id="be241-167">當您想要將參數設為位置時，請使用 `Position` 引數。</span><span class="sxs-lookup"><span data-stu-id="be241-167">When you want parameters to be positional, use the `Position` argument.</span></span>

<span data-ttu-id="be241-168">下列範例會宣告 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="be241-168">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="be241-169">它會使用 `Position` 值為 **0** 的引數。</span><span class="sxs-lookup"><span data-stu-id="be241-169">It uses the `Position` argument with a value of **0**.</span></span> <span data-ttu-id="be241-170">因此，當 `-ComputerName` 從命令省略時，其值必須是命令中的第一個或唯一未命名的參數值。</span><span class="sxs-lookup"><span data-stu-id="be241-170">As a result, when `-ComputerName` is omitted from command, its value must be the first or only unnamed parameter value in the command.</span></span>

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a><span data-ttu-id="be241-171">ParameterSetName 引數</span><span class="sxs-lookup"><span data-stu-id="be241-171">ParameterSetName argument</span></span>

<span data-ttu-id="be241-172">`ParameterSetName`引數指定參數所屬的參數集。</span><span class="sxs-lookup"><span data-stu-id="be241-172">The `ParameterSetName` argument specifies the parameter set to which a parameter belongs.</span></span> <span data-ttu-id="be241-173">如果未指定任何參數集，則參數屬於函式所定義的所有參數集。</span><span class="sxs-lookup"><span data-stu-id="be241-173">If no parameter set is specified, the parameter belongs to all the parameter sets defined by the function.</span></span> <span data-ttu-id="be241-174">因此，若要成為唯一的，每個參數集都必須至少有一個參數不是任何其他參數集的成員。</span><span class="sxs-lookup"><span data-stu-id="be241-174">Therefore, to be unique, each parameter set must have at least one parameter that isn't a member of any other parameter set.</span></span>

> [!NOTE]
> <span data-ttu-id="be241-175">針對 Cmdlet 或函式，有32個參數集的限制。</span><span class="sxs-lookup"><span data-stu-id="be241-175">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

<span data-ttu-id="be241-176">下列範例會宣告參數集中的 **ComputerName** 參數 `Computer` 、參數集中的使用者 **名稱** 參數 `User` ，以及兩個參數集中的 **摘要** 參數。</span><span class="sxs-lookup"><span data-stu-id="be241-176">The following example declares a **ComputerName** parameter in the `Computer` parameter set, a **UserName** parameter in the `User` parameter set, and a **Summary** parameter in both parameter sets.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false)]
    [Switch]
    $Summary
)
```

<span data-ttu-id="be241-177">在 `ParameterSetName` 每個引數中只能指定一個值，而且 `ParameterSetName` 每個 **參數** 屬性只能指定一個引數。</span><span class="sxs-lookup"><span data-stu-id="be241-177">You can specify only one `ParameterSetName` value in each argument and only one `ParameterSetName` argument in each **Parameter** attribute.</span></span> <span data-ttu-id="be241-178">若要指出參數出現在一個以上的參數集中，請新增其他 **參數** 屬性。</span><span class="sxs-lookup"><span data-stu-id="be241-178">To indicate that a parameter appears in more than one parameter set, add additional **Parameter** attributes.</span></span>

<span data-ttu-id="be241-179">下列範例會明確地將 **Summary** 參數加入 `Computer` 和 `User` 參數集。</span><span class="sxs-lookup"><span data-stu-id="be241-179">The following example explicitly adds the **Summary** parameter to the `Computer` and `User` parameter sets.</span></span> <span data-ttu-id="be241-180">**摘要** 參數在參數集內是選擇性的 `Computer` ，且在參數集中為必要項 `User` 。</span><span class="sxs-lookup"><span data-stu-id="be241-180">The **Summary** parameter is optional in the `Computer` parameter set and mandatory in the `User` parameter set.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false, ParameterSetName="Computer")]
    [Parameter(Mandatory=$true, ParameterSetName="User")]
    [Switch]
    $Summary
)
```

<span data-ttu-id="be241-181">如需參數集的詳細資訊，請參閱 [關於參數集](about_parameter_sets.md)。</span><span class="sxs-lookup"><span data-stu-id="be241-181">For more information about parameter sets, see [About Parameter Sets](about_parameter_sets.md).</span></span>

#### <a name="valuefrompipeline-argument"></a><span data-ttu-id="be241-182">ValueFromPipeline 引數</span><span class="sxs-lookup"><span data-stu-id="be241-182">ValueFromPipeline argument</span></span>

<span data-ttu-id="be241-183">`ValueFromPipeline`引數指出參數接受來自管線物件的輸入。</span><span class="sxs-lookup"><span data-stu-id="be241-183">The `ValueFromPipeline` argument indicates that the parameter accepts input from a pipeline object.</span></span> <span data-ttu-id="be241-184">如果函式接受整個物件，而不只是物件的屬性，請指定此引數。</span><span class="sxs-lookup"><span data-stu-id="be241-184">Specify this argument if the function accepts the entire object, not just a property of the object.</span></span>

<span data-ttu-id="be241-185">下列範例會宣告必要的 **ComputerName** 參數，並接受從管線傳遞至函式的物件。</span><span class="sxs-lookup"><span data-stu-id="be241-185">The following example declares a **ComputerName** parameter that's mandatory and accepts an object that's passed to the function from the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a><span data-ttu-id="be241-186">ValueFromPipelineByPropertyName 引數</span><span class="sxs-lookup"><span data-stu-id="be241-186">ValueFromPipelineByPropertyName argument</span></span>

<span data-ttu-id="be241-187">`ValueFromPipelineByPropertyName`引數表示參數會接受來自管線物件之屬性的輸入。</span><span class="sxs-lookup"><span data-stu-id="be241-187">The `ValueFromPipelineByPropertyName` argument indicates that the parameter accepts input from a property of a pipeline object.</span></span> <span data-ttu-id="be241-188">物件屬性必須與參數具有相同的名稱或別名。</span><span class="sxs-lookup"><span data-stu-id="be241-188">The object property must have the same name or alias as the parameter.</span></span>

<span data-ttu-id="be241-189">例如，如果函式具有 **computername** 參數，且管道物件具有 **computername** 屬性，則 **computername** 屬性的值會指派給函數的 **computername** 參數。</span><span class="sxs-lookup"><span data-stu-id="be241-189">For example, if the function has a **ComputerName** parameter, and the piped object has a **ComputerName** property, the value of the **ComputerName** property is assigned to the function's **ComputerName** parameter.</span></span>

<span data-ttu-id="be241-190">下列範例會宣告必要的 **ComputerName** 參數，並接受透過管線傳遞至函式的物件 **computername** 屬性的輸入。</span><span class="sxs-lookup"><span data-stu-id="be241-190">The following example declares a **ComputerName** parameter that's mandatory and accepts input from the object's **ComputerName** property that's passed to the function through the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> <span data-ttu-id="be241-191">接受管線輸入 (`by Value`) 或 (`by PropertyName`) 可在參數上使用 _延遲_ 系結腳本區塊的型別參數。</span><span class="sxs-lookup"><span data-stu-id="be241-191">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of _delay-bind_ script blocks on the parameter.</span></span>
>
> <span data-ttu-id="be241-192">_延遲_ 系結腳本區塊會在 **ParameterBinding** 期間自動執行。</span><span class="sxs-lookup"><span data-stu-id="be241-192">The _delay-bind_ script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="be241-193">結果會系結至參數。</span><span class="sxs-lookup"><span data-stu-id="be241-193">The result is bound to the parameter.</span></span> <span data-ttu-id="be241-194">延遲系結對於定義為類型或的參數無法運作 `ScriptBlock` `System.Object` 。</span><span class="sxs-lookup"><span data-stu-id="be241-194">Delay binding does not work for parameters defined as type `ScriptBlock` or `System.Object`.</span></span> <span data-ttu-id="be241-195">腳本區塊會在未叫用的 _情況下_ 傳遞。</span><span class="sxs-lookup"><span data-stu-id="be241-195">The script block is passed through _without_ being invoked.</span></span>
>
> <span data-ttu-id="be241-196">您可以在這裡閱讀 _延遲_ 系結腳本區塊 [about_Script_Blocks md](about_Script_Blocks.md)。</span><span class="sxs-lookup"><span data-stu-id="be241-196">You can read about _delay-bind_ script blocks here [about_Script_Blocks.md](about_Script_Blocks.md).</span></span>

#### <a name="valuefromremainingarguments-argument"></a><span data-ttu-id="be241-197">ValueFromRemainingArguments 引數</span><span class="sxs-lookup"><span data-stu-id="be241-197">ValueFromRemainingArguments argument</span></span>

<span data-ttu-id="be241-198">`ValueFromRemainingArguments`引數表示參數會接受命令中所有未指派給函式之其他參數的參數值。</span><span class="sxs-lookup"><span data-stu-id="be241-198">The `ValueFromRemainingArguments` argument indicates that the parameter accepts all the parameter's values in the command that aren't assigned to other parameters of the function.</span></span>

<span data-ttu-id="be241-199">使用具有 **ValueFromRemainingArguments** 之集合的已知問題，會將傳入的集合視為單一元素。</span><span class="sxs-lookup"><span data-stu-id="be241-199">There's a known issue for using collections with **ValueFromRemainingArguments** where the passed-in collection is treated as a single element.</span></span>

<span data-ttu-id="be241-200">下列範例示範此已知問題。</span><span class="sxs-lookup"><span data-stu-id="be241-200">The following example demonstrates this known issue.</span></span> <span data-ttu-id="be241-201">**其餘** 參數 **應包含\*\*\*\*索引 0** 和 **索引 1** 的 **兩個** 參數。</span><span class="sxs-lookup"><span data-stu-id="be241-201">The **Remaining** parameter should contain **one** at **index 0** and **two** at **index 1**.</span></span>
<span data-ttu-id="be241-202">相反地，這兩個元素會合並為單一實體。</span><span class="sxs-lookup"><span data-stu-id="be241-202">Instead, both elements are combined into a single entity.</span></span>

```powershell
function Test-Remainder
{
     param(
         [string]
         [Parameter(Mandatory = $true, Position=0)]
         $Value,
         [string[]]
         [Parameter(Position=1, ValueFromRemainingArguments)]
         $Remaining)
     "Found $($Remaining.Count) elements"
     for ($i = 0; $i -lt $Remaining.Count; $i++)
     {
        "${i}: $($Remaining[$i])"
     }
}
Test-Remainder first one,two
```

```Output
Found 1 elements
0: one two
```

> [!NOTE]
> <span data-ttu-id="be241-203">此問題已在 PowerShell 6.2 中解決。</span><span class="sxs-lookup"><span data-stu-id="be241-203">This issue is resolved in PowerShell 6.2.</span></span>

#### <a name="helpmessage-argument"></a><span data-ttu-id="be241-204">HelpMessage 引數</span><span class="sxs-lookup"><span data-stu-id="be241-204">HelpMessage argument</span></span>

<span data-ttu-id="be241-205">`HelpMessage`引數指定包含參數或其值之簡短描述的字串。</span><span class="sxs-lookup"><span data-stu-id="be241-205">The `HelpMessage` argument specifies a string that contains a brief description of the parameter or its value.</span></span> <span data-ttu-id="be241-206">當命令缺少強制參數值時，PowerShell 會在出現的提示中顯示此訊息。</span><span class="sxs-lookup"><span data-stu-id="be241-206">PowerShell displays this message in the prompt that appears when a mandatory parameter value is missing from a command.</span></span> <span data-ttu-id="be241-207">這個引數對選擇性參數沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="be241-207">This argument has no effect on optional parameters.</span></span>

<span data-ttu-id="be241-208">下列範例會宣告必要的 **ComputerName** 參數，以及說明預期參數值的說明訊息。</span><span class="sxs-lookup"><span data-stu-id="be241-208">The following example declares a mandatory **ComputerName** parameter and a help message that explains the expected parameter value.</span></span>

<span data-ttu-id="be241-209">如果函式沒有其他以 [批註為基礎的說明](./about_comment_based_help.md) 語法 (例如， `.SYNOPSIS`) 則這則訊息也會顯示在 `Get-Help` 輸出中。</span><span class="sxs-lookup"><span data-stu-id="be241-209">If there is no other [comment-based help](./about_comment_based_help.md) syntax for the function (for example, `.SYNOPSIS`) then this message also shows up in `Get-Help` output.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a><span data-ttu-id="be241-210">Alias 屬性</span><span class="sxs-lookup"><span data-stu-id="be241-210">Alias attribute</span></span>

<span data-ttu-id="be241-211">**Alias** 屬性會建立參數的替代名稱。</span><span class="sxs-lookup"><span data-stu-id="be241-211">The **Alias** attribute establishes an alternate name for the parameter.</span></span>
<span data-ttu-id="be241-212">您可以指派給參數的別名數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="be241-212">There's no limit to the number of aliases that you can assign to a parameter.</span></span>

<span data-ttu-id="be241-213">下列範例顯示將 **CN** 和 **MachineName** 別名新增至必要 **ComputerName** 參數的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="be241-213">The following example shows a parameter declaration that adds the **CN** and **MachineName** aliases to the mandatory **ComputerName** parameter.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a><span data-ttu-id="be241-214">SupportsWildcards 屬性</span><span class="sxs-lookup"><span data-stu-id="be241-214">SupportsWildcards attribute</span></span>

<span data-ttu-id="be241-215">**SupportsWildcards** 屬性是用來指出參數接受萬用字元值。</span><span class="sxs-lookup"><span data-stu-id="be241-215">The **SupportsWildcards** attribute is used to indicate that the parameter accepts wildcard values.</span></span> <span data-ttu-id="be241-216">下列範例顯示支援萬用字元值的強制 **路徑** 參數的參數宣告。</span><span class="sxs-lookup"><span data-stu-id="be241-216">The following example shows a parameter declaration for a mandatory **Path** parameter that supports wildcard values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

<span data-ttu-id="be241-217">使用這個屬性不會自動啟用萬用字元支援。</span><span class="sxs-lookup"><span data-stu-id="be241-217">Using this attribute does not automatically enable wildcard support.</span></span> <span data-ttu-id="be241-218">Cmdlet 開發人員必須執行程式碼來處理萬用字元輸入。</span><span class="sxs-lookup"><span data-stu-id="be241-218">The cmdlet developer must implement the code to handle the wildcard input.</span></span> <span data-ttu-id="be241-219">支援的萬用字元會根據基礎 API 或 PowerShell 提供者而有所不同。</span><span class="sxs-lookup"><span data-stu-id="be241-219">The wildcards supported can vary according to the underlying API or PowerShell provider.</span></span> <span data-ttu-id="be241-220">如需詳細資訊，請參閱 [about_Wildcards](about_Wildcards.md)。</span><span class="sxs-lookup"><span data-stu-id="be241-220">For more information, see [about_Wildcards](about_Wildcards.md).</span></span>

### <a name="parameter-and-variable-validation-attributes"></a><span data-ttu-id="be241-221">參數和變數驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-221">Parameter and variable validation attributes</span></span>

<span data-ttu-id="be241-222">驗證屬性可指示 PowerShell 測試使用者在呼叫 advanced 函式時所提交的參數值。</span><span class="sxs-lookup"><span data-stu-id="be241-222">Validation attributes direct PowerShell to test the parameter values that users submit when they call the advanced function.</span></span> <span data-ttu-id="be241-223">如果參數值未通過測試，則會產生錯誤，而且不會呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="be241-223">If the parameter values fail the test, an error is generated and the function isn't called.</span></span> <span data-ttu-id="be241-224">參數驗證只會套用至提供的輸入，而且不會驗證任何其他值，例如預設值。</span><span class="sxs-lookup"><span data-stu-id="be241-224">Parameter validation is only applied to the input provided and any other values like default values are not validated.</span></span>

<span data-ttu-id="be241-225">您也可以使用驗證屬性來限制使用者可為變數指定的值。</span><span class="sxs-lookup"><span data-stu-id="be241-225">You can also use the validation attributes to restrict the values that users can specify for variables.</span></span> <span data-ttu-id="be241-226">當您搭配使用類型轉換器與驗證屬性時，必須在屬性之前定義類型轉換器。</span><span class="sxs-lookup"><span data-stu-id="be241-226">When you use a type converter along with a validation attribute, the type converter has to be defined before the attribute.</span></span>

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a><span data-ttu-id="be241-227">AllowNull 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-227">AllowNull validation attribute</span></span>

<span data-ttu-id="be241-228">**AllowNull** 屬性可讓必要參數的值為 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="be241-228">The **AllowNull** attribute allows the value of a mandatory parameter to be `$null`.</span></span> <span data-ttu-id="be241-229">下列範例會宣告一個可以有 **null** 值的 hashtable **get-computerinfo** 參數。</span><span class="sxs-lookup"><span data-stu-id="be241-229">The following example declares a hashtable **ComputerInfo** parameter that can have a **null** value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> <span data-ttu-id="be241-230">如果類型轉換器設定為 string， **AllowNull** 屬性就無法運作，因為字串型別不接受 null 值。</span><span class="sxs-lookup"><span data-stu-id="be241-230">The **AllowNull** attribute doesn't work if the type converter is set to string as the string type will not accept a null value.</span></span> <span data-ttu-id="be241-231">您可以在此案例中使用 **AllowEmptyString** 屬性。</span><span class="sxs-lookup"><span data-stu-id="be241-231">You can use the **AllowEmptyString** attribute for this scenario.</span></span>

### <a name="allowemptystring-validation-attribute"></a><span data-ttu-id="be241-232">AllowEmptyString 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-232">AllowEmptyString validation attribute</span></span>

<span data-ttu-id="be241-233">**AllowEmptyString** 屬性可讓必要參數的值為空字串 (`""`) 。</span><span class="sxs-lookup"><span data-stu-id="be241-233">The **AllowEmptyString** attribute allows the value of a mandatory parameter to be an empty string (`""`).</span></span> <span data-ttu-id="be241-234">下列範例會宣告可具有空字串值的 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="be241-234">The following example declares a **ComputerName** parameter that can have an empty string value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a><span data-ttu-id="be241-235">AllowEmptyCollection 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-235">AllowEmptyCollection validation attribute</span></span>

<span data-ttu-id="be241-236">**AllowEmptyCollection** 屬性可讓必要參數的值為空集合 `@()` 。</span><span class="sxs-lookup"><span data-stu-id="be241-236">The **AllowEmptyCollection** attribute allows the value of a mandatory parameter to be an empty collection `@()`.</span></span> <span data-ttu-id="be241-237">下列範例宣告的 **ComputerName** 參數可以有空的集合值。</span><span class="sxs-lookup"><span data-stu-id="be241-237">The following example declares a **ComputerName** parameter that can have an empty collection value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a><span data-ttu-id="be241-238">ValidateCount 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-238">ValidateCount validation attribute</span></span>

<span data-ttu-id="be241-239">**ValidateCount** 屬性會指定參數所接受的參數值的最小和最大數目。</span><span class="sxs-lookup"><span data-stu-id="be241-239">The **ValidateCount** attribute specifies the minimum and maximum number of parameter values that a parameter accepts.</span></span> <span data-ttu-id="be241-240">如果命令中呼叫函數的參數值數目超出該範圍，則 PowerShell 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="be241-240">PowerShell generates an error if the number of parameter values in the command that calls the function is outside that range.</span></span>

<span data-ttu-id="be241-241">下列參數宣告會建立 **ComputerName** 參數，該參數會採用一到五個參數值。</span><span class="sxs-lookup"><span data-stu-id="be241-241">The following parameter declaration creates a **ComputerName** parameter that takes one to five parameter values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a><span data-ttu-id="be241-242">ValidateLength 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-242">ValidateLength validation attribute</span></span>

<span data-ttu-id="be241-243">**ValidateLength** 屬性會指定參數或變數值中的最小和最大字元數。</span><span class="sxs-lookup"><span data-stu-id="be241-243">The **ValidateLength** attribute specifies the minimum and maximum number of characters in a parameter or variable value.</span></span> <span data-ttu-id="be241-244">如果為參數或變數指定的值長度超出範圍，則 PowerShell 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="be241-244">PowerShell generates an error if the length of a value specified for a parameter or a variable is outside of the range.</span></span>

<span data-ttu-id="be241-245">在下列範例中，每個電腦名稱稱都必須有一到十個字元。</span><span class="sxs-lookup"><span data-stu-id="be241-245">In the following example, each computer name must have one to ten characters.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="be241-246">在下列範例中，變數的值 `$number` 必須是長度最少一個字元，最多10個字元。</span><span class="sxs-lookup"><span data-stu-id="be241-246">In the following example, the value of the variable `$number` must be a minimum of one character in length, and a maximum of ten characters.</span></span>

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> <span data-ttu-id="be241-247">在此範例中，的值 `01` 會以單引號括住。</span><span class="sxs-lookup"><span data-stu-id="be241-247">In this example, the value of `01` is wrapped in single quotes.</span></span> <span data-ttu-id="be241-248">**ValidateLength** 屬性不會接受數位，而不會以引號括住。</span><span class="sxs-lookup"><span data-stu-id="be241-248">The **ValidateLength** attribute won't accept a number without being wrapped in quotes.</span></span>

### <a name="validatepattern-validation-attribute"></a><span data-ttu-id="be241-249">ValidatePattern 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-249">ValidatePattern validation attribute</span></span>

<span data-ttu-id="be241-250">**ValidatePattern** 屬性會指定與參數或變數值比較的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="be241-250">The **ValidatePattern** attribute specifies a regular expression that's compared to the parameter or variable value.</span></span> <span data-ttu-id="be241-251">如果值不符合正則運算式模式，則 PowerShell 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="be241-251">PowerShell generates an error if the value doesn't match the regular expression pattern.</span></span>

<span data-ttu-id="be241-252">在下列範例中，參數值必須包含四位數的數位，而且每個數位都必須是0到9的數位。</span><span class="sxs-lookup"><span data-stu-id="be241-252">In the following example, the parameter value must contain a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="be241-253">在下列範例中，變數的值 `$number` 必須正好是四位數的數位，而且每個數位都必須是0到9的數位。</span><span class="sxs-lookup"><span data-stu-id="be241-253">In the following example, the value of the variable `$number` must be exactly a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a><span data-ttu-id="be241-254">ValidateRange 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-254">ValidateRange validation attribute</span></span>

<span data-ttu-id="be241-255">**ValidateRange** 屬性會指定每個參數或變數值的數值範圍。</span><span class="sxs-lookup"><span data-stu-id="be241-255">The **ValidateRange** attribute specifies a numeric range for each parameter or variable value.</span></span> <span data-ttu-id="be241-256">如果任何值超出該範圍，PowerShell 就會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="be241-256">PowerShell generates an error if any value is outside that range.</span></span> <span data-ttu-id="be241-257">在下列範例中， **嘗試** 參數的值必須介於0到10之間。</span><span class="sxs-lookup"><span data-stu-id="be241-257">In the following example, the value of the **Attempts** parameter must be between zero and ten.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

<span data-ttu-id="be241-258">在下列範例中，變數的值 `$number` 必須介於0到10之間。</span><span class="sxs-lookup"><span data-stu-id="be241-258">In the following example, the value of the variable `$number` must be between zero and ten.</span></span>

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

### <a name="validatescript-validation-attribute"></a><span data-ttu-id="be241-259">ValidateScript 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-259">ValidateScript validation attribute</span></span>

<span data-ttu-id="be241-260">**ValidateScript** 屬性會指定用來驗證參數或變數值的腳本。</span><span class="sxs-lookup"><span data-stu-id="be241-260">The **ValidateScript** attribute specifies a script that is used to validate a parameter or variable value.</span></span> <span data-ttu-id="be241-261">PowerShell 會使用管線將值傳送至腳本，如果腳本傳回或腳本擲回例外狀況，則會產生錯誤 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="be241-261">PowerShell pipes the value to the script, and generates an error if the script returns `$false` or if the script throws an exception.</span></span>

<span data-ttu-id="be241-262">當您使用 **ValidateScript** 屬性時，所驗證的值會對應至 `$_` 變數。</span><span class="sxs-lookup"><span data-stu-id="be241-262">When you use the **ValidateScript** attribute, the value that's being validated is mapped to the `$_` variable.</span></span> <span data-ttu-id="be241-263">您可以使用 `$_` 變數來參考腳本中的值。</span><span class="sxs-lookup"><span data-stu-id="be241-263">You can use the `$_` variable to refer to the value in the script.</span></span>

<span data-ttu-id="be241-264">在下列範例中， **EventDate** 參數的值必須大於或等於目前的日期。</span><span class="sxs-lookup"><span data-stu-id="be241-264">In the following example, the value of the **EventDate** parameter must be greater than or equal to the current date.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

<span data-ttu-id="be241-265">在下列範例中，變數的值 `$date` 必須大於或等於目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="be241-265">In the following example, the value of the variable `$date` must be greater than or equal to the current date and time.</span></span>

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> <span data-ttu-id="be241-266">如果您使用 **ValidateScript** ，則無法將 `$null` 值傳遞給參數。</span><span class="sxs-lookup"><span data-stu-id="be241-266">If you use **ValidateScript** , you cannot pass a `$null` value to the parameter.</span></span> <span data-ttu-id="be241-267">當您傳遞 null 值時 **ValidateScript** 無法驗證引數。</span><span class="sxs-lookup"><span data-stu-id="be241-267">When you pass a null value **ValidateScript** can't validate the argument.</span></span>

### <a name="validateset-attribute"></a><span data-ttu-id="be241-268">ValidateSet 屬性</span><span class="sxs-lookup"><span data-stu-id="be241-268">ValidateSet attribute</span></span>

<span data-ttu-id="be241-269">**ValidateSet** 屬性會為參數或變數指定一組有效值，並啟用 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="be241-269">The **ValidateSet** attribute specifies a set of valid values for a parameter or variable and enables tab completion.</span></span> <span data-ttu-id="be241-270">如果參數或變數值不符合集合中的值，PowerShell 就會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="be241-270">PowerShell generates an error if a parameter or variable value doesn't match a value in the set.</span></span> <span data-ttu-id="be241-271">在下列範例中， **Detail** 參數的值只能是 Low、Average 或 High。</span><span class="sxs-lookup"><span data-stu-id="be241-271">In the following example, the value of the **Detail** parameter can only be Low, Average, or High.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

<span data-ttu-id="be241-272">在下列範例中，變數的值 `$flavor` 必須是巧克力、草莓或香草。</span><span class="sxs-lookup"><span data-stu-id="be241-272">In the following example, the value of the variable `$flavor` must be either Chocolate, Strawberry, or Vanilla.</span></span>

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

<span data-ttu-id="be241-273">只要在腳本內指派該變數，就會發生驗證。</span><span class="sxs-lookup"><span data-stu-id="be241-273">The validation occurs whenever that variable is assigned even within the script.</span></span> <span data-ttu-id="be241-274">例如，下列程式會在執行時間產生錯誤：</span><span class="sxs-lookup"><span data-stu-id="be241-274">For example, the following results in an error at runtime:</span></span>

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

### <a name="validatenotnull-validation-attribute"></a><span data-ttu-id="be241-275">ValidateNotNull 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-275">ValidateNotNull validation attribute</span></span>

<span data-ttu-id="be241-276">**ValidateNotNull** 屬性指定參數值不能是 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="be241-276">The **ValidateNotNull** attribute specifies that the parameter value can't be `$null`.</span></span> <span data-ttu-id="be241-277">如果參數值為，PowerShell 會產生錯誤 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="be241-277">PowerShell generates an error if the parameter value is `$null`.</span></span>

<span data-ttu-id="be241-278">**ValidateNotNull** 屬性是設計用來在參數為選擇性且類型未定義或具有無法以隱含方式轉換 null 值（例如 **物件** ）的類型轉換器時使用。</span><span class="sxs-lookup"><span data-stu-id="be241-278">The **ValidateNotNull** attribute is designed to be used when the parameter is optional and the type is undefined or has a type converter that can't implicitly convert a null value like **object**.</span></span> <span data-ttu-id="be241-279">如果您指定的型別會隱含地轉換 null 值（例如 **字串** ），即使使用 **ValidateNotNull** 屬性，也會將 null 值轉換為空字串。</span><span class="sxs-lookup"><span data-stu-id="be241-279">If you specify a type that that will implicitly convert a null value such as a **string** , the null value is converted to an empty string even when using the **ValidateNotNull** attribute.</span></span> <span data-ttu-id="be241-280">針對此案例，請使用 **ValidateNotNullOrEmpty**</span><span class="sxs-lookup"><span data-stu-id="be241-280">For this scenario use the **ValidateNotNullOrEmpty**</span></span>

<span data-ttu-id="be241-281">在下列範例中， **ID** 參數的值不能是 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="be241-281">In the following example, the value of the **ID** parameter can't be `$null`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a><span data-ttu-id="be241-282">ValidateNotNullOrEmpty 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-282">ValidateNotNullOrEmpty validation attribute</span></span>

<span data-ttu-id="be241-283">**ValidateNotNullOrEmpty** 屬性指定參數值不能是 `$null` ，也不能是 () 的空字串 `""` 。</span><span class="sxs-lookup"><span data-stu-id="be241-283">The **ValidateNotNullOrEmpty** attribute specifies that the parameter value can't be `$null` and can't be an empty string (`""`).</span></span> <span data-ttu-id="be241-284">如果在函式呼叫中使用參數，但其值為 `$null` 、空字串 (`""`) 或空陣列，則 PowerShell 會產生錯誤 `@()` 。</span><span class="sxs-lookup"><span data-stu-id="be241-284">PowerShell generates an error if the parameter is used in a function call, but its value is `$null`, an empty string (`""`), or an empty array `@()`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a><span data-ttu-id="be241-285">ValidateDrive 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-285">ValidateDrive validation attribute</span></span>

<span data-ttu-id="be241-286">**ValidateDrive** 屬性指定參數值必須代表路徑，而這只是指允許的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="be241-286">The **ValidateDrive** attribute specifies that the parameter value must represent the path, that's referring to allowed drives only.</span></span> <span data-ttu-id="be241-287">如果參數值參考了允許的磁片磁碟機，則 PowerShell 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="be241-287">PowerShell generates an error if the parameter value refers to drives other than the allowed.</span></span> <span data-ttu-id="be241-288">除了磁片磁碟機本身以外，不會驗證路徑是否存在。</span><span class="sxs-lookup"><span data-stu-id="be241-288">Existence of the path, except for the drive itself, isn't verified.</span></span>

<span data-ttu-id="be241-289">如果您使用相對路徑，則目前磁片磁碟機必須位於允許的磁片磁碟機清單中。</span><span class="sxs-lookup"><span data-stu-id="be241-289">If you use relative path, the current drive must be in the allowed drive list.</span></span>

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a><span data-ttu-id="be241-290">ValidateUserDrive 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-290">ValidateUserDrive validation attribute</span></span>

<span data-ttu-id="be241-291">**ValidateUserDrive** 屬性指定參數值必須代表參考 `User` 磁片磁碟機的路徑。</span><span class="sxs-lookup"><span data-stu-id="be241-291">The **ValidateUserDrive** attribute specifies that the parameter value must represent the path, that is referring to `User` drive.</span></span> <span data-ttu-id="be241-292">如果路徑參考不同的磁片磁碟機，PowerShell 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="be241-292">PowerShell generates an error if the path refers to a different drive.</span></span> <span data-ttu-id="be241-293">驗證屬性只會測試路徑的磁片磁碟機部分是否存在。</span><span class="sxs-lookup"><span data-stu-id="be241-293">The validation attribute only tests for the existence of the drive portion of the path.</span></span>

<span data-ttu-id="be241-294">如果您使用相對路徑，則目前磁片磁碟機必須是 `User` 。</span><span class="sxs-lookup"><span data-stu-id="be241-294">If you use relative path, the current drive must be `User`.</span></span>

```powershell
function Test-UserDrivePath{
    [OutputType([bool])]
    Param(
      [Parameter(Mandatory=, Position=0)][ValidateUserDrive()][String]$Path
      )
    $True
}

Test-UserDrivePath -Path C:\
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. The path
argument drive C does not belong to the set of approved drives: User.
Supply a path argument with an approved drive.
```

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. Cannot
find drive. A drive with the name 'User' does not exist.
```

<span data-ttu-id="be241-295">您可以 `User` 在 (JEA) 會話設定的足夠管理中定義磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="be241-295">You can define `User` drive in Just Enough Administration (JEA) session configurations.</span></span> <span data-ttu-id="be241-296">在此範例中，我們會建立使用者：磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="be241-296">For this example, we create the User: drive.</span></span>

```powershell
New-PSDrive -Name 'User' -PSProvider FileSystem -Root $env:HOMEPATH
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
User               75.76         24.24 FileSystem    C:\Users\ExampleUser

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
True
```

### <a name="validatetrusteddata-validation-attribute"></a><span data-ttu-id="be241-297">ValidateTrustedData 驗證屬性</span><span class="sxs-lookup"><span data-stu-id="be241-297">ValidateTrustedData validation attribute</span></span>

<span data-ttu-id="be241-298">此屬性已新增至 PowerShell 6.1.1。</span><span class="sxs-lookup"><span data-stu-id="be241-298">This attribute was added in PowerShell 6.1.1.</span></span>

<span data-ttu-id="be241-299">目前，此屬性是由 PowerShell 本身在內部使用，並非供外部使用。</span><span class="sxs-lookup"><span data-stu-id="be241-299">At this time, the attribute is used internally by PowerShell itself and is not intended for external usage.</span></span>

## <a name="dynamic-parameters"></a><span data-ttu-id="be241-300">動態參數</span><span class="sxs-lookup"><span data-stu-id="be241-300">Dynamic parameters</span></span>

<span data-ttu-id="be241-301">動態參數是 Cmdlet、函式或腳本的參數，只有在特定條件下才能使用。</span><span class="sxs-lookup"><span data-stu-id="be241-301">Dynamic parameters are parameters of a cmdlet, function, or script that are available only under certain conditions.</span></span>

<span data-ttu-id="be241-302">例如，只有在提供者磁片磁碟機或提供者磁片磁碟機的特定路徑中使用 Cmdlet 時，有數個提供者 Cmdlet 具有可用的參數。</span><span class="sxs-lookup"><span data-stu-id="be241-302">For example, several provider cmdlets have parameters that are available only when the cmdlet is used in the provider drive, or in a particular path of the provider drive.</span></span> <span data-ttu-id="be241-303">例如，只有在 **Encoding** `Add-Content` `Get-Content` `Set-Content` 檔案系統磁片磁碟機中使用時，才可以在、和 Cmdlet 上使用 Encoding 參數。</span><span class="sxs-lookup"><span data-stu-id="be241-303">For example, the **Encoding** parameter is available on the `Add-Content`, `Get-Content`, and `Set-Content` cmdlets only when it's used in a file system drive.</span></span>

<span data-ttu-id="be241-304">您也可以建立只在函數命令中使用另一個參數時，或當另一個參數具有特定值時才會出現的參數。</span><span class="sxs-lookup"><span data-stu-id="be241-304">You can also create a parameter that appears only when another parameter is used in the function command or when another parameter has a certain value.</span></span>

<span data-ttu-id="be241-305">動態參數可能很有用，但只在必要時才使用，因為使用者可能很難探索。</span><span class="sxs-lookup"><span data-stu-id="be241-305">Dynamic parameters can be useful, but use them only when necessary, because they can be difficult for users to discover.</span></span> <span data-ttu-id="be241-306">若要尋找動態參數，使用者必須在提供者路徑中，使用 Cmdlet 的 **ArgumentList** 參數 `Get-Command` ，或使用的 **path** 參數 `Get-Help` 。</span><span class="sxs-lookup"><span data-stu-id="be241-306">To find a dynamic parameter, the user must be in the provider path, use the **ArgumentList** parameter of the `Get-Command` cmdlet, or use the **Path** parameter of `Get-Help`.</span></span>

<span data-ttu-id="be241-307">若要建立函數或腳本的動態參數，請使用 `DynamicParam` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="be241-307">To create a dynamic parameter for a function or script, use the `DynamicParam` keyword.</span></span>

<span data-ttu-id="be241-308">語法如下：</span><span class="sxs-lookup"><span data-stu-id="be241-308">The syntax is as follows:</span></span>

`DynamicParam {<statement-list>}`

<span data-ttu-id="be241-309">在語句清單中，使用 `If` 語句來指定函數中可用參數的條件。</span><span class="sxs-lookup"><span data-stu-id="be241-309">In the statement list, use an `If` statement to specify the conditions under which the parameter is available in the function.</span></span>

<span data-ttu-id="be241-310">使用 `New-Object` Cmdlet 來建立 **RuntimeDefinedParameter** 物件，以代表參數並指定其名稱。</span><span class="sxs-lookup"><span data-stu-id="be241-310">Use the `New-Object` cmdlet to create a **System.Management.Automation.RuntimeDefinedParameter** object to represent the parameter and specify its name.</span></span>

<span data-ttu-id="be241-311">您可以使用 `New-Object` 命令來建立 **ParameterAttribute** 物件，以代表參數的屬性，例如 **強制** 、 **位置** 或 **ValueFromPipeline** 或其參數集。</span><span class="sxs-lookup"><span data-stu-id="be241-311">You can use a `New-Object` command to create a **System.Management.Automation.ParameterAttribute** object to represent attributes of the parameter, such as **Mandatory** , **Position** , or **ValueFromPipeline** or its parameter set.</span></span>

<span data-ttu-id="be241-312">下列範例顯示範例函式，其中包含名為 **Name** 和 **Path** 的標準參數，以及一個名為 **DP1** 的選擇性動態參數。</span><span class="sxs-lookup"><span data-stu-id="be241-312">The following example shows a sample function with standard parameters named **Name** and **Path** , and an optional dynamic parameter named **DP1**.</span></span> <span data-ttu-id="be241-313">**DP1** 參數位於 `PSet1` 參數集中，且具有類型 `Int32` 。</span><span class="sxs-lookup"><span data-stu-id="be241-313">The **DP1** parameter is in the `PSet1` parameter set and has a type of `Int32`.</span></span>
<span data-ttu-id="be241-314">**DP1** `Get-Sample` 只有當 **Path** 參數的值以開頭 `HKLM:` ，表示在登錄磁片磁碟機中使用時，DP1 參數才可在函式中使用 `HKEY_LOCAL_MACHINE` 。</span><span class="sxs-lookup"><span data-stu-id="be241-314">The **DP1** parameter is available in the `Get-Sample` function only when the value of the **Path** parameter starts with `HKLM:`, indicating that it's being used in the `HKEY_LOCAL_MACHINE` registry drive.</span></span>

```powershell
function Get-Sample {
  [CmdletBinding()]
  Param([String]$Name, [String]$Path)

  DynamicParam
  {
    if ($Path.StartsWith("HKLM:"))
    {
      $attributes = New-Object -Type `
        System.Management.Automation.ParameterAttribute
      $attributes.ParameterSetName = "PSet1"
      $attributes.Mandatory = $false
      $attributeCollection = New-Object `
        -Type System.Collections.ObjectModel.Collection[System.Attribute]
      $attributeCollection.Add($attributes)

      $dynParam1 = New-Object -Type `
        System.Management.Automation.RuntimeDefinedParameter("DP1", [Int32],
          $attributeCollection)

      $paramDictionary = New-Object `
        -Type System.Management.Automation.RuntimeDefinedParameterDictionary
      $paramDictionary.Add("DP1", $dynParam1)
      return $paramDictionary
    }
  }
}
```

<span data-ttu-id="be241-315">如需詳細資訊，請參閱 [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter)。</span><span class="sxs-lookup"><span data-stu-id="be241-315">For more information, see [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter).</span></span>

## <a name="switch-parameters"></a><span data-ttu-id="be241-316">切換參數</span><span class="sxs-lookup"><span data-stu-id="be241-316">Switch parameters</span></span>

<span data-ttu-id="be241-317">Switch 參數是沒有參數值的參數。</span><span class="sxs-lookup"><span data-stu-id="be241-317">Switch parameters are parameters with no parameter value.</span></span> <span data-ttu-id="be241-318">它們只有在使用時才有效，而且只有一個效果。</span><span class="sxs-lookup"><span data-stu-id="be241-318">They're effective only when they're used and have only one effect.</span></span>

<span data-ttu-id="be241-319">例如， **powershell.exe** 的 **NoProfile** 參數是切換參數。</span><span class="sxs-lookup"><span data-stu-id="be241-319">For example, the **NoProfile** parameter of **powershell.exe** is a switch parameter.</span></span>

<span data-ttu-id="be241-320">若要在函數中建立切換參數，請 `Switch` 在參數定義中指定類型。</span><span class="sxs-lookup"><span data-stu-id="be241-320">To create a switch parameter in a function, specify the `Switch` type in the parameter definition.</span></span>

<span data-ttu-id="be241-321">例如：</span><span class="sxs-lookup"><span data-stu-id="be241-321">For example:</span></span>

```powershell
Param([Switch]<ParameterName>)
```

<span data-ttu-id="be241-322">或者，您可以使用另一種方法：</span><span class="sxs-lookup"><span data-stu-id="be241-322">Or, you can use an another method:</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

<span data-ttu-id="be241-323">切換參數很容易使用，而且偏好使用布林值參數，而這些參數的語法比較困難。</span><span class="sxs-lookup"><span data-stu-id="be241-323">Switch parameters are easy to use and are preferred over Boolean parameters, which have a more difficult syntax.</span></span>

<span data-ttu-id="be241-324">例如，若要使用切換參數，使用者可以在命令中輸入參數。</span><span class="sxs-lookup"><span data-stu-id="be241-324">For example, to use a switch parameter, the user types the parameter in the command.</span></span>

`-IncludeAll`

<span data-ttu-id="be241-325">若要使用布林值參數，使用者可以輸入參數和布林值。</span><span class="sxs-lookup"><span data-stu-id="be241-325">To use a Boolean parameter, the user types the parameter and a Boolean value.</span></span>

`-IncludeAll:$true`

<span data-ttu-id="be241-326">建立切換參數時，請謹慎選擇參數名稱。</span><span class="sxs-lookup"><span data-stu-id="be241-326">When creating switch parameters, choose the parameter name carefully.</span></span> <span data-ttu-id="be241-327">請確定參數名稱會將參數的效果傳達給使用者。</span><span class="sxs-lookup"><span data-stu-id="be241-327">Be sure that the parameter name communicates the effect of the parameter to the user.</span></span>
<span data-ttu-id="be241-328">避免不明確的詞彙（例如，可能代表需要值的 **篩選** 或 **最大** 值）。</span><span class="sxs-lookup"><span data-stu-id="be241-328">Avoid ambiguous terms, such as **Filter** or **Maximum** that might imply a value is required.</span></span>

## <a name="argumentcompleter-attribute"></a><span data-ttu-id="be241-329">ArgumentCompleter 屬性</span><span class="sxs-lookup"><span data-stu-id="be241-329">ArgumentCompleter attribute</span></span>

<span data-ttu-id="be241-330">**ArgumentCompleter** 屬性可讓您將 tab 鍵自動完成值新增至特定參數。</span><span class="sxs-lookup"><span data-stu-id="be241-330">The **ArgumentCompleter** attribute allows you to add tab completion values to a specific parameter.</span></span> <span data-ttu-id="be241-331">必須針對需要 tab 鍵自動完成的每個參數定義 **ArgumentCompleter** 屬性。</span><span class="sxs-lookup"><span data-stu-id="be241-331">An **ArgumentCompleter** attribute must be defined for each parameter that needs tab completion.</span></span> <span data-ttu-id="be241-332">類似于 **get-dynamicparameters** ，當使用者按下 <kbd>Tab 鍵</kbd> 之後，可在執行時間計算可用的值。</span><span class="sxs-lookup"><span data-stu-id="be241-332">Similar to **DynamicParameters** , the available values are calculated at runtime when the user presses <kbd>Tab</kbd> after the parameter name.</span></span>

<span data-ttu-id="be241-333">若要加入 **ArgumentCompleter** 屬性，您需要定義判斷值的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="be241-333">To add an **ArgumentCompleter** attribute, you need to define a script block that determines the values.</span></span> <span data-ttu-id="be241-334">腳本區塊必須以下列指定的順序來採用下列參數。</span><span class="sxs-lookup"><span data-stu-id="be241-334">The script block must take the following parameters in the order specified below.</span></span> <span data-ttu-id="be241-335">參數的名稱並不重要，因為 positionally 會提供值。</span><span class="sxs-lookup"><span data-stu-id="be241-335">The parameter's names don't matter as the values are provided positionally.</span></span>

<span data-ttu-id="be241-336">語法如下：</span><span class="sxs-lookup"><span data-stu-id="be241-336">The syntax is as follows:</span></span>

```powershell
Param(
    [Parameter(Mandatory)]
    [ArgumentCompleter({
        param ( $commandName,
                $parameterName,
                $wordToComplete,
                $commandAst,
                $fakeBoundParameters )
        # Perform calculation of tab completed values here.
    })]
)
```

### <a name="argumentcompleter-script-block"></a><span data-ttu-id="be241-337">ArgumentCompleter 腳本區塊</span><span class="sxs-lookup"><span data-stu-id="be241-337">ArgumentCompleter script block</span></span>

<span data-ttu-id="be241-338">腳本區塊參數會設定為下列值：</span><span class="sxs-lookup"><span data-stu-id="be241-338">The script block parameters are set to the following values:</span></span>

- <span data-ttu-id="be241-339">`$commandName` (位置 0) -此參數會設定為腳本區塊提供 tab 鍵自動完成之命令的名稱。</span><span class="sxs-lookup"><span data-stu-id="be241-339">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="be241-340">`$parameterName` (位置 1) -此參數會設定為其值需要 tab 鍵自動完成的參數。</span><span class="sxs-lookup"><span data-stu-id="be241-340">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="be241-341">`$wordToComplete` (位置 2) -此參數會設定為使用者在按下 <kbd>Tab 鍵</kbd>之前所提供的值。您的腳本區塊應該使用此值來判斷 tab 鍵自動完成值。</span><span class="sxs-lookup"><span data-stu-id="be241-341">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="be241-342">`$commandAst` (位置 3) -這個參數會設定為目前輸入行 (AST) 的抽象語法樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="be241-342">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="be241-343">如需詳細資訊，請參閱 [Ast 類別](/dotnet/api/system.management.automation.language.ast)。</span><span class="sxs-lookup"><span data-stu-id="be241-343">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="be241-344">`$fakeBoundParameters` (位置 4) - `$PSBoundParameters` 在使用者按下索引標籤之前，此參數會設定為包含 Cmdlet 之<kbd>Tab</kbd>的雜湊表。如需詳細資訊，請參閱[about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="be241-344">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="be241-345">**ArgumentCompleter** 腳本區塊必須使用管線來展開值，例如 `ForEach-Object` 、 `Where-Object` 或其他適合的方法。</span><span class="sxs-lookup"><span data-stu-id="be241-345">The **ArgumentCompleter** script block must unroll the values using the pipeline, such as `ForEach-Object`, `Where-Object`, or another suitable method.</span></span>
<span data-ttu-id="be241-346">傳回值陣列會導致 PowerShell 將整個陣列視為 **一個** tab 鍵自動完成值。</span><span class="sxs-lookup"><span data-stu-id="be241-346">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="be241-347">下列範例會將 tab 鍵自動完成新增至 **Value** 參數。</span><span class="sxs-lookup"><span data-stu-id="be241-347">The following example adds tab completion to the **Value** parameter.</span></span> <span data-ttu-id="be241-348">如果只指定 **值** 參數，則會顯示 **值** 的所有可能值或引數。</span><span class="sxs-lookup"><span data-stu-id="be241-348">If only the **Value** parameter is specified, all possible values, or arguments, for **Value** are displayed.</span></span> <span data-ttu-id="be241-349">當指定 **型** 別參數時， **Value** 參數只會顯示該類型的可能值。</span><span class="sxs-lookup"><span data-stu-id="be241-349">When the **Type** parameter is specified, the **Value** parameter only displays the possible values for that type.</span></span>

<span data-ttu-id="be241-350">此外， `-like` 運算子可確保如果使用者輸入下列命令並使用 <kbd>Tab 鍵</kbd> 自動完成，則只會傳回 **Apple** 。</span><span class="sxs-lookup"><span data-stu-id="be241-350">In addition, the `-like` operator ensures that if the user types the following command and uses <kbd>Tab</kbd> completion, only **Apple** is returned.</span></span>

`Test-ArgumentCompleter -Type Fruits -Value A`

```powershell
function Test-ArgumentCompleter {
[CmdletBinding()]
 param (
        [Parameter(Mandatory=$true)]
        [ValidateSet('Fruits', 'Vegetables')]
        $Type,
        [Parameter(Mandatory=$true)]
        [ArgumentCompleter( {
            param ( $commandName,
                    $parameterName,
                    $wordToComplete,
                    $commandAst,
                    $fakeBoundParameters )

            $possibleValues = @{
                Fruits = @('Apple', 'Orange', 'Banana')
                Vegetables = @('Tomato', 'Squash', 'Corn')
            }
            if ($fakeBoundParameters.ContainsKey('Type'))
            {
                $possibleValues[$fakeBoundParameters.Type] | Where-Object {
                    $_ -like "$wordToComplete*"
                }
            }
            else
            {
                $possibleValues.Values | ForEach-Object {$_}
            }
        } )]
        $Value
      )
}
```

## <a name="see-also"></a><span data-ttu-id="be241-351">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be241-351">See also</span></span>

[<span data-ttu-id="be241-352">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="be241-352">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="be241-353">about_Functions</span><span class="sxs-lookup"><span data-stu-id="be241-353">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="be241-354">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="be241-354">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="be241-355">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="be241-355">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="be241-356">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="be241-356">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="be241-357">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="be241-357">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
