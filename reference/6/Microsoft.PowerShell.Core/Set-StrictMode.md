---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: d28ff57c864847658072c9b7a1979b2b513c04b3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204871"
---
# <span data-ttu-id="c46a3-103">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="c46a3-103">Set-StrictMode</span></span>

## <span data-ttu-id="c46a3-104">概要</span><span class="sxs-lookup"><span data-stu-id="c46a3-104">SYNOPSIS</span></span>
<span data-ttu-id="c46a3-105">在運算式、指令碼和指令碼區塊中建立並強制執行編碼規則。</span><span class="sxs-lookup"><span data-stu-id="c46a3-105">Establishes and enforces coding rules in expressions, scripts, and script blocks.</span></span>

## <span data-ttu-id="c46a3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c46a3-106">SYNTAX</span></span>

### <span data-ttu-id="c46a3-107">Version (預設值)</span><span class="sxs-lookup"><span data-stu-id="c46a3-107">Version (Default)</span></span>

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### <span data-ttu-id="c46a3-108">關閉</span><span class="sxs-lookup"><span data-stu-id="c46a3-108">Off</span></span>

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## <span data-ttu-id="c46a3-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c46a3-109">DESCRIPTION</span></span>

<span data-ttu-id="c46a3-110">`Set-StrictMode`Cmdlet 會為目前的範圍和所有子範圍設定 strict 模式，並將其開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="c46a3-110">The `Set-StrictMode` cmdlet configures strict mode for the current scope and all child scopes, and turns it on and off.</span></span> <span data-ttu-id="c46a3-111">當 strict 模式開啟時，如果運算式、腳本或腳本區塊的內容違反基本最佳作法編碼規則，則 PowerShell 會產生終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="c46a3-111">When strict mode is on, PowerShell generates a terminating error when the content of an expression, script, or script block violates basic best-practice coding rules.</span></span>

<span data-ttu-id="c46a3-112">使用 **Version** 參數來決定要強制執行哪些編碼規則。</span><span class="sxs-lookup"><span data-stu-id="c46a3-112">Use the **Version** parameter to determine which coding rules are enforced.</span></span>

<span data-ttu-id="c46a3-113">`Set-PSDebug -Strict` Cmdlet 會開啟全域範圍的 strict 模式。</span><span class="sxs-lookup"><span data-stu-id="c46a3-113">`Set-PSDebug -Strict` cmdlet turns on strict mode for the global scope.</span></span> <span data-ttu-id="c46a3-114">`Set-StrictMode` 只會影響目前的範圍及其子範圍。</span><span class="sxs-lookup"><span data-stu-id="c46a3-114">`Set-StrictMode` affects only the current scope and its child scopes.</span></span> <span data-ttu-id="c46a3-115">因此，您可以在腳本或函式中使用它來覆寫繼承自全域範圍的設定。</span><span class="sxs-lookup"><span data-stu-id="c46a3-115">Therefore, you can use it in a script or function to override the setting inherited from the global scope.</span></span>

<span data-ttu-id="c46a3-116">當 `Set-StrictMode` 關閉時，PowerShell 會有下列行為：</span><span class="sxs-lookup"><span data-stu-id="c46a3-116">When `Set-StrictMode` is off, PowerShell has the following behaviors:</span></span>

- <span data-ttu-id="c46a3-117">未初始化的變數會假設值為 0 (零) 或 `$Null` （視類型而定）</span><span class="sxs-lookup"><span data-stu-id="c46a3-117">Uninitialized variables are assumed to have a value of 0 (zero) or `$Null`, depending on type</span></span>
- <span data-ttu-id="c46a3-118">參考不存在的屬性會傳回 `$Null`</span><span class="sxs-lookup"><span data-stu-id="c46a3-118">References to non-existent properties return `$Null`</span></span>
- <span data-ttu-id="c46a3-119">不當函數語法的結果會隨著錯誤狀況而有所不同</span><span class="sxs-lookup"><span data-stu-id="c46a3-119">Results of improper function syntax vary with the error conditions</span></span>
- <span data-ttu-id="c46a3-120">嘗試在陣列中使用不正確索引來取得值 `$Null`</span><span class="sxs-lookup"><span data-stu-id="c46a3-120">Attempting to retrieve a value using an invalid index in an array returns `$Null`</span></span>

## <span data-ttu-id="c46a3-121">範例</span><span class="sxs-lookup"><span data-stu-id="c46a3-121">EXAMPLES</span></span>

### <span data-ttu-id="c46a3-122">範例 1︰開啟 strict 模式為 1.0 版</span><span class="sxs-lookup"><span data-stu-id="c46a3-122">Example 1: Turn on strict mode as version 1.0</span></span>

```powershell
# Strict mode is off by default.
$a -gt 5
```

```Output
False
```

```powershell
Set-StrictMode -Version 1.0
$a -gt 5
```

```Output
The variable $a cannot be retrieved because it has not been set yet.

At line:1 char:3
+ $a <<<<  -gt 5
+ CategoryInfo          : InvalidOperation: (a:Token) [], RuntimeException
+ FullyQualifiedErrorId : VariableIsUndefined
```

<span data-ttu-id="c46a3-123">當 strict 模式設定為1.0 版時，嘗試參考未初始化的變數將會失敗。</span><span class="sxs-lookup"><span data-stu-id="c46a3-123">With strict mode set to version 1.0, attempts to reference variables that are not initialized fail.</span></span>

### <span data-ttu-id="c46a3-124">範例 2︰開啟 strict 模式為 2.0 版</span><span class="sxs-lookup"><span data-stu-id="c46a3-124">Example 2: Turn on strict mode as version 2.0</span></span>

```powershell
# Strict mode is off by default.
function add ($a, $b) {
    '$a = ' + $a
    '$b = ' + $b
    '$a+$b = ' + ($a + $b)
}
add 3 4
```

```Output
$a = 3
$b = 4
$a+$b = 7
```

```powershell
add(3,4)
```

```Output
$a = 3 4
$b =
$a+$b = 3 4
```

```powershell
Set-StrictMode -Version 2.0
add(3,4)
```

```Output
The function or command was called like a method. Parameters should be separated by spaces,
as described in 'Get-Help about_Parameter.'
At line:1 char:4
+ add <<<< (3,4)
+ CategoryInfo          : InvalidOperation: (:) [], RuntimeException
+ FullyQualifiedErrorId : StrictModeFunctionCallWithParens
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$string.Month -eq $null
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$string.Month -eq $null
```

```Output
Property 'Month' cannot be found on this object; make sure it exists.
At line:1 char:9
+ $string. <<<< month
+ CategoryInfo          : InvalidOperation: (.:OperatorToken) [], RuntimeException
+ FullyQualifiedErrorId : PropertyNotFoundStrict
```

<span data-ttu-id="c46a3-125">此命令會開啟 strict 模式，並將它設定為 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="c46a3-125">This command turns strict mode on and sets it to version 2.0.</span></span> <span data-ttu-id="c46a3-126">因此，如果您針對函式呼叫使用方法語法（使用括弧和逗號）或參考未初始化的變數或不存在的屬性，則 PowerShell 會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="c46a3-126">As a result, PowerShell returns an error if you use method syntax, which uses parentheses and commas, for a function call or reference uninitialized variables or non-existent properties.</span></span>

<span data-ttu-id="c46a3-127">範例輸出顯示 2.0 版之 strict 模式的作用。</span><span class="sxs-lookup"><span data-stu-id="c46a3-127">The sample output shows the effect of version 2.0 strict mode.</span></span>

<span data-ttu-id="c46a3-128">如果不是 2.0 版的 strict 模式，"(3,4)" 值會解譯為不新增任何項目的單一陣列物件。</span><span class="sxs-lookup"><span data-stu-id="c46a3-128">Without version 2.0 strict mode, the "(3,4)" value is interpreted as a single array object to which nothing is added.</span></span> <span data-ttu-id="c46a3-129">如果使用 2.0 版的 strict 模式，則會正確解譯為提交兩個值的錯誤語法。</span><span class="sxs-lookup"><span data-stu-id="c46a3-129">By using version 2.0 strict mode, it is correctly interpreted as faulty syntax for submitting two values.</span></span>

<span data-ttu-id="c46a3-130">如果沒有2.0 版，則只會傳回字串中不存在之 **Month** 屬性的參考 `$Null` 。</span><span class="sxs-lookup"><span data-stu-id="c46a3-130">Without version 2.0, the reference to the non-existent **Month** property of a string returns only `$Null`.</span></span> <span data-ttu-id="c46a3-131">如果使用 2.0 版，則會正確解譯為參考錯誤。</span><span class="sxs-lookup"><span data-stu-id="c46a3-131">By using version 2.0, it is interpreted correctly as a reference error.</span></span>

### <span data-ttu-id="c46a3-132">範例3：開啟 strict 模式為3.0 版</span><span class="sxs-lookup"><span data-stu-id="c46a3-132">Example 3: Turn on strict mode as version 3.0</span></span>

<span data-ttu-id="c46a3-133">如果 strict 模式設定為 **Off** ，則無效或超出界限索引結果會傳回 null 值。</span><span class="sxs-lookup"><span data-stu-id="c46a3-133">With strict mode set to **Off** , invalid or out of bounds indexes result return null values.</span></span>

```powershell
# Strict mode is off by default.
$a = @(1)
$a[2] -eq $null
$a['abc'] -eq $null
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$a[2] -eq $null
$a['abc'] -eq $null
```

```Output
Index was outside the bounds of the array.
At line:1 char:1
+ $a[2] -eq $null
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
    + FullyQualifiedErrorId : System.IndexOutOfRangeException

Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
At line:1 char:1
+ $a['abc'] -eq $null
+ ~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvalidCastFromStringToInteger
```

<span data-ttu-id="c46a3-134">如果 strict 模式設定為第3版或更高版本，則無效或超出範圍索引會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="c46a3-134">With strict mode set to version 3 or higher, invalid or out of bounds indexes result in errors.</span></span>

## <span data-ttu-id="c46a3-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c46a3-135">PARAMETERS</span></span>

### <span data-ttu-id="c46a3-136">-Off</span><span class="sxs-lookup"><span data-stu-id="c46a3-136">-Off</span></span>

<span data-ttu-id="c46a3-137">指出此 Cmdlet 會針對目前的範圍和所有子範圍關閉 strict 模式。</span><span class="sxs-lookup"><span data-stu-id="c46a3-137">Indicates that this cmdlet turns strict mode off for the current scope and all child scopes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Off
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c46a3-138">-Version</span><span class="sxs-lookup"><span data-stu-id="c46a3-138">-Version</span></span>

<span data-ttu-id="c46a3-139">指定在 strict 模式中導致錯誤的條件。</span><span class="sxs-lookup"><span data-stu-id="c46a3-139">Specifies the conditions that cause an error in strict mode.</span></span> <span data-ttu-id="c46a3-140">此參數會接受任何有效的 PowerShell 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="c46a3-140">This parameter accepts any valid PowerShell version number.</span></span> <span data-ttu-id="c46a3-141">任何大於3的數位都會視為 **最新** 的。</span><span class="sxs-lookup"><span data-stu-id="c46a3-141">Any number higher than 3 is treated as **Latest** .</span></span>

<span data-ttu-id="c46a3-142">此參數的有效值為：</span><span class="sxs-lookup"><span data-stu-id="c46a3-142">The effective values for this parameter are:</span></span>

- <span data-ttu-id="c46a3-143">1.0</span><span class="sxs-lookup"><span data-stu-id="c46a3-143">1.0</span></span>
  - <span data-ttu-id="c46a3-144">禁止參考未初始化的變數，但字串中未初始化的變數除外。</span><span class="sxs-lookup"><span data-stu-id="c46a3-144">Prohibits references to uninitialized variables, except for uninitialized variables in strings.</span></span>
- <span data-ttu-id="c46a3-145">2.0</span><span class="sxs-lookup"><span data-stu-id="c46a3-145">2.0</span></span>
  - <span data-ttu-id="c46a3-146">禁止參考未初始化的變數。</span><span class="sxs-lookup"><span data-stu-id="c46a3-146">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="c46a3-147">這包括字串中未初始化的變數。</span><span class="sxs-lookup"><span data-stu-id="c46a3-147">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="c46a3-148">禁止參考不存在的物件屬性。</span><span class="sxs-lookup"><span data-stu-id="c46a3-148">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="c46a3-149">禁止使用呼叫方法語法的函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="c46a3-149">Prohibits function calls that use the syntax for calling methods.</span></span>
- <span data-ttu-id="c46a3-150">3.0</span><span class="sxs-lookup"><span data-stu-id="c46a3-150">3.0</span></span>
  - <span data-ttu-id="c46a3-151">禁止參考未初始化的變數。</span><span class="sxs-lookup"><span data-stu-id="c46a3-151">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="c46a3-152">這包括字串中未初始化的變數。</span><span class="sxs-lookup"><span data-stu-id="c46a3-152">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="c46a3-153">禁止參考不存在的物件屬性。</span><span class="sxs-lookup"><span data-stu-id="c46a3-153">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="c46a3-154">禁止使用呼叫方法語法的函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="c46a3-154">Prohibits function calls that use the syntax for calling methods.</span></span>
  - <span data-ttu-id="c46a3-155">禁止超出範圍或無法解析的陣列索引。</span><span class="sxs-lookup"><span data-stu-id="c46a3-155">Prohibit out of bounds or unresolvable array indexes.</span></span>
- <span data-ttu-id="c46a3-156">Latest</span><span class="sxs-lookup"><span data-stu-id="c46a3-156">Latest</span></span>
  - <span data-ttu-id="c46a3-157">選取可用的最新版本。</span><span class="sxs-lookup"><span data-stu-id="c46a3-157">Selects the latest version available.</span></span> <span data-ttu-id="c46a3-158">最新的版本是最嚴格的。</span><span class="sxs-lookup"><span data-stu-id="c46a3-158">The latest version is the most strict.</span></span> <span data-ttu-id="c46a3-159">使用此值可確保腳本會使用最嚴格的可用版本（即使將新版本新增至 PowerShell 亦同）。</span><span class="sxs-lookup"><span data-stu-id="c46a3-159">Use this value to make sure that scripts use the strictest available version, even when new versions are added to PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="c46a3-160">使用腳本中的 **最新\*\*\*\*版本** 。</span><span class="sxs-lookup"><span data-stu-id="c46a3-160">Using a **Version** of **Latest** in scripts.</span></span> <span data-ttu-id="c46a3-161">新版本的 PowerShell 可能會變更 **最新** 版本的意義。</span><span class="sxs-lookup"><span data-stu-id="c46a3-161">The meaning of **Latest** can change in new releases of PowerShell.</span></span> <span data-ttu-id="c46a3-162">因此，針對舊版 PowerShell 所撰寫的腳本，在 `Set-StrictMode -Version Latest` 較新版本的 powershell 中執行時，會受限於更嚴格的規則。</span><span class="sxs-lookup"><span data-stu-id="c46a3-162">Therefore, a script written for an older version of PowerShell that uses `Set-StrictMode -Version Latest` is subject to more restrictive rules when run in a newer version of PowerShell.</span></span>

```yaml
Type: System.Version
Parameter Sets: Version
Aliases: v

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c46a3-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c46a3-163">CommonParameters</span></span>

<span data-ttu-id="c46a3-164">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c46a3-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c46a3-165">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c46a3-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c46a3-166">輸入</span><span class="sxs-lookup"><span data-stu-id="c46a3-166">INPUTS</span></span>

### <span data-ttu-id="c46a3-167">無</span><span class="sxs-lookup"><span data-stu-id="c46a3-167">None</span></span>

<span data-ttu-id="c46a3-168">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c46a3-168">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c46a3-169">輸出</span><span class="sxs-lookup"><span data-stu-id="c46a3-169">OUTPUTS</span></span>

### <span data-ttu-id="c46a3-170">無</span><span class="sxs-lookup"><span data-stu-id="c46a3-170">None</span></span>

<span data-ttu-id="c46a3-171">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="c46a3-171">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="c46a3-172">注意</span><span class="sxs-lookup"><span data-stu-id="c46a3-172">NOTES</span></span>

<span data-ttu-id="c46a3-173">`Set-StrictMode` 只有在設定的範圍及其子範圍中才有效。</span><span class="sxs-lookup"><span data-stu-id="c46a3-173">`Set-StrictMode` is effective only in the scope in which it is set and in its child scopes.</span></span> <span data-ttu-id="c46a3-174">如需 PowerShell 中之範圍的詳細資訊，請參閱 [about_Scopes](about/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="c46a3-174">For more information about scopes in PowerShell, see [about_Scopes](about/about_Scopes.md).</span></span>

## <span data-ttu-id="c46a3-175">相關連結</span><span class="sxs-lookup"><span data-stu-id="c46a3-175">RELATED LINKS</span></span>

[<span data-ttu-id="c46a3-176">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="c46a3-176">Set-PSDebug</span></span>](Set-PSDebug.md)