---
description: 說明如何在 PowerShell 中建立和使用函式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: 944cb3fc77406cfbf288655d2740bad6ddcceee4
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387629"
---
# <a name="about-functions"></a><span data-ttu-id="b929c-104">關於函式</span><span class="sxs-lookup"><span data-stu-id="b929c-104">About Functions</span></span>

## <a name="short-description"></a><span data-ttu-id="b929c-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="b929c-105">Short description</span></span>

<span data-ttu-id="b929c-106">說明如何在 PowerShell 中建立和使用函式。</span><span class="sxs-lookup"><span data-stu-id="b929c-106">Describes how to create and use functions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="b929c-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="b929c-107">Long description</span></span>

<span data-ttu-id="b929c-108">函式是具有您指派之名稱的 PowerShell 語句清單。</span><span class="sxs-lookup"><span data-stu-id="b929c-108">A function is a list of PowerShell statements that has a name that you assign.</span></span> <span data-ttu-id="b929c-109">當您執行函式時，您會輸入函數名稱。</span><span class="sxs-lookup"><span data-stu-id="b929c-109">When you run a function, you type the function name.</span></span> <span data-ttu-id="b929c-110">清單中的語句會以您在命令提示字元中輸入的方式執行。</span><span class="sxs-lookup"><span data-stu-id="b929c-110">The statements in the list run as if you had typed them at the command prompt.</span></span>

<span data-ttu-id="b929c-111">函數可以簡單如下：</span><span class="sxs-lookup"><span data-stu-id="b929c-111">Functions can be as simple as:</span></span>

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

<span data-ttu-id="b929c-112">函數也可以像 Cmdlet 或應用程式一樣複雜。</span><span class="sxs-lookup"><span data-stu-id="b929c-112">A function can also be as complex as a cmdlet or an application program.</span></span>

<span data-ttu-id="b929c-113">如同 Cmdlet，函數可以有參數。</span><span class="sxs-lookup"><span data-stu-id="b929c-113">Like cmdlets, functions can have parameters.</span></span> <span data-ttu-id="b929c-114">這些參數可以是命名、位置、切換或動態參數。</span><span class="sxs-lookup"><span data-stu-id="b929c-114">The parameters can be named, positional, switch, or dynamic parameters.</span></span> <span data-ttu-id="b929c-115">您可以從命令列或從管線讀取函數參數。</span><span class="sxs-lookup"><span data-stu-id="b929c-115">Function parameters can be read from the command line or from the pipeline.</span></span>

<span data-ttu-id="b929c-116">函數可以傳回可顯示、指派給變數或傳遞給其他函式或 Cmdlet 的值。</span><span class="sxs-lookup"><span data-stu-id="b929c-116">Functions can return values that can be displayed, assigned to variables, or passed to other functions or cmdlets.</span></span> <span data-ttu-id="b929c-117">您也可以使用關鍵字來指定傳回值 `return` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-117">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="b929c-118">`return`關鍵字不會影響或隱藏從函數傳回的其他輸出。</span><span class="sxs-lookup"><span data-stu-id="b929c-118">The `return` keyword does not affect or suppress other output returned from your function.</span></span> <span data-ttu-id="b929c-119">不過， `return` 關鍵字會結束該行的函式。</span><span class="sxs-lookup"><span data-stu-id="b929c-119">However, the `return` keyword exits the function at that line.</span></span> <span data-ttu-id="b929c-120">如需詳細資訊，請參閱 [about_Return](about_Return.md)。</span><span class="sxs-lookup"><span data-stu-id="b929c-120">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="b929c-121">函數的語句清單可以包含不同類型的語句清單，以及關鍵字 `Begin` 、 `Process` 和 `End` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-121">The function's statement list can contain different types of statement lists with the keywords `Begin`, `Process`, and `End`.</span></span> <span data-ttu-id="b929c-122">這些語句清單會以不同的方式處理來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="b929c-122">These statement lists handle input from the pipeline differently.</span></span>

<span data-ttu-id="b929c-123">篩選是一種特殊的函式，使用 `Filter` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b929c-123">A filter is a special kind of function that uses the `Filter` keyword.</span></span>

<span data-ttu-id="b929c-124">函數也可以像 Cmdlet 一樣運作。</span><span class="sxs-lookup"><span data-stu-id="b929c-124">Functions can also act like cmdlets.</span></span> <span data-ttu-id="b929c-125">您可以建立函式，其運作方式就像 Cmdlet，而不需要使用程式 `C#` 設計。</span><span class="sxs-lookup"><span data-stu-id="b929c-125">You can create a function that works just like a cmdlet without using `C#` programming.</span></span> <span data-ttu-id="b929c-126">如需詳細資訊，請參閱 [about_Functions_Advanced](about_Functions_Advanced.md)。</span><span class="sxs-lookup"><span data-stu-id="b929c-126">For more information, see [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="b929c-127">Syntax</span><span class="sxs-lookup"><span data-stu-id="b929c-127">Syntax</span></span>

<span data-ttu-id="b929c-128">以下是函數的語法：</span><span class="sxs-lookup"><span data-stu-id="b929c-128">The following is the syntax for a function:</span></span>

```
function [<scope:>]<name> [([type]$parameter1[,[type]$parameter2])]
{
  param([type]$parameter1 [,[type]$parameter2])
  dynamicparam {<statement list>}
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="b929c-129">函數包含下列專案：</span><span class="sxs-lookup"><span data-stu-id="b929c-129">A function includes the following items:</span></span>

- <span data-ttu-id="b929c-130">`Function`關鍵字</span><span class="sxs-lookup"><span data-stu-id="b929c-130">A `Function` keyword</span></span>
- <span data-ttu-id="b929c-131">範圍 (選擇性) </span><span class="sxs-lookup"><span data-stu-id="b929c-131">A scope (optional)</span></span>
- <span data-ttu-id="b929c-132">您選取的名稱</span><span class="sxs-lookup"><span data-stu-id="b929c-132">A name that you select</span></span>
- <span data-ttu-id="b929c-133">任何數目的具名引數 (選擇性) </span><span class="sxs-lookup"><span data-stu-id="b929c-133">Any number of named parameters (optional)</span></span>
- <span data-ttu-id="b929c-134">以大括弧括住的一或多個 PowerShell 命令 `{}`</span><span class="sxs-lookup"><span data-stu-id="b929c-134">One or more PowerShell commands enclosed in braces `{}`</span></span>

<span data-ttu-id="b929c-135">如需 `Dynamicparam` 函數中關鍵字和動態參數的詳細資訊，請參閱 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b929c-135">For more information about the `Dynamicparam` keyword and dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="simple-functions"></a><span data-ttu-id="b929c-136">簡單函數</span><span class="sxs-lookup"><span data-stu-id="b929c-136">Simple Functions</span></span>

<span data-ttu-id="b929c-137">函數不需要太複雜，就很有用。</span><span class="sxs-lookup"><span data-stu-id="b929c-137">Functions do not have to be complicated to be useful.</span></span> <span data-ttu-id="b929c-138">最簡單的函式具有下列格式：</span><span class="sxs-lookup"><span data-stu-id="b929c-138">The simplest functions have the following format:</span></span>

```
function <function-name> {statements}
```

<span data-ttu-id="b929c-139">例如，下列函式會使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b929c-139">For example, the following function starts PowerShell with the Run as Administrator option.</span></span>

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

<span data-ttu-id="b929c-140">若要使用函數，請輸入： `Start-PSAdmin`</span><span class="sxs-lookup"><span data-stu-id="b929c-140">To use the function, type: `Start-PSAdmin`</span></span>

<span data-ttu-id="b929c-141">若要將語句加入至函數，請在個別的行上輸入每個語句，或使用分號 `;` 來分隔語句。</span><span class="sxs-lookup"><span data-stu-id="b929c-141">To add statements to the function, type each statement on a separate line, or use a semi-colon `;` to separate the statements.</span></span>

<span data-ttu-id="b929c-142">例如，下列函式 `.jpg` 會在目前使用者的目錄中尋找在開始日期之後變更的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="b929c-142">For example, the following function finds all `.jpg` files in the current user's directories that were changed after the start date.</span></span>

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

<span data-ttu-id="b929c-143">您可以建立有用小型函式的工具箱。</span><span class="sxs-lookup"><span data-stu-id="b929c-143">You can create a toolbox of useful small functions.</span></span> <span data-ttu-id="b929c-144">將這些函式新增至您的 PowerShell 設定檔，如本主題的 [about_Profiles](about_Profiles.md) 和稍後所述。</span><span class="sxs-lookup"><span data-stu-id="b929c-144">Add these functions to your PowerShell profile, as described in [about_Profiles](about_Profiles.md) and later in this topic.</span></span>

## <a name="function-names"></a><span data-ttu-id="b929c-145">函數名稱</span><span class="sxs-lookup"><span data-stu-id="b929c-145">Function Names</span></span>

<span data-ttu-id="b929c-146">您可以將任何名稱指派給函式，但您與其他人共用的函式應遵循針對所有 PowerShell 命令所建立的命名規則。</span><span class="sxs-lookup"><span data-stu-id="b929c-146">You can assign any name to a function, but functions that you share with others should follow the naming rules that have been established for all PowerShell commands.</span></span>

<span data-ttu-id="b929c-147">函式名稱應該包含動詞-名片語，其中動詞會識別函式所執行的動作，而名詞會識別 Cmdlet 執行其動作的專案。</span><span class="sxs-lookup"><span data-stu-id="b929c-147">Functions names should consist of a verb-noun pair in which the verb identifies the action that the function performs and the noun identifies the item on which the cmdlet performs its action.</span></span>

<span data-ttu-id="b929c-148">函式應使用已核准給所有 PowerShell 命令的標準動詞。</span><span class="sxs-lookup"><span data-stu-id="b929c-148">Functions should use the standard verbs that have been approved for all PowerShell commands.</span></span> <span data-ttu-id="b929c-149">這些動詞命令可協助我們讓命令名稱保持簡單、一致且方便使用者瞭解。</span><span class="sxs-lookup"><span data-stu-id="b929c-149">These verbs help us to keep our command names simple, consistent, and easy for users to understand.</span></span>

<span data-ttu-id="b929c-150">如需標準 PowerShell 動詞命令的詳細資訊，請參閱 Microsoft Docs 中的 [已核准動詞](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) 。</span><span class="sxs-lookup"><span data-stu-id="b929c-150">For more information about the standard PowerShell verbs, see [Approved Verbs](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) in the Microsoft Docs.</span></span>

## <a name="functions-with-parameters"></a><span data-ttu-id="b929c-151">具有參數的函式</span><span class="sxs-lookup"><span data-stu-id="b929c-151">Functions with Parameters</span></span>

<span data-ttu-id="b929c-152">您可以搭配使用參數與函數，包括具名引數、位置參數、切換參數和動態參數。</span><span class="sxs-lookup"><span data-stu-id="b929c-152">You can use parameters with functions, including named parameters, positional parameters, switch parameters, and dynamic parameters.</span></span> <span data-ttu-id="b929c-153">如需函數中動態參數的詳細資訊，請參閱 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b929c-153">For more information about dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="named-parameters"></a><span data-ttu-id="b929c-154">具名參數</span><span class="sxs-lookup"><span data-stu-id="b929c-154">Named Parameters</span></span>

<span data-ttu-id="b929c-155">您可以定義任何數目的具名引數。</span><span class="sxs-lookup"><span data-stu-id="b929c-155">You can define any number of named parameters.</span></span> <span data-ttu-id="b929c-156">您可以包含具名引數的預設值，如本主題稍後所述。</span><span class="sxs-lookup"><span data-stu-id="b929c-156">You can include a default value for named parameters, as described later in this topic.</span></span>

<span data-ttu-id="b929c-157">您可以使用關鍵字來定義大括弧內的參數 `Param` ，如下列範例語法所示：</span><span class="sxs-lookup"><span data-stu-id="b929c-157">You can define parameters inside the braces using the `Param` keyword, as shown in the following sample syntax:</span></span>

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

<span data-ttu-id="b929c-158">您也可以在沒有關鍵詞的大括弧之外定義參數 `Param` ，如下列範例語法所示：</span><span class="sxs-lookup"><span data-stu-id="b929c-158">You can also define parameters outside the braces without the `Param` keyword, as shown in the following sample syntax:</span></span>

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

<span data-ttu-id="b929c-159">以下是此替代語法的範例。</span><span class="sxs-lookup"><span data-stu-id="b929c-159">Below is an example of this alternative syntax.</span></span>

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

<span data-ttu-id="b929c-160">雖然第一個方法是慣用的，但這兩種方法並沒有任何差異。</span><span class="sxs-lookup"><span data-stu-id="b929c-160">While the first method is preferred, there is no difference between these two methods.</span></span>

<span data-ttu-id="b929c-161">當您執行函式時，您為參數提供的值會指派給包含參數名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="b929c-161">When you run the function, the value you supply for a parameter is assigned to a variable that contains the parameter name.</span></span> <span data-ttu-id="b929c-162">可以在函數中使用該變數的值。</span><span class="sxs-lookup"><span data-stu-id="b929c-162">The value of that variable can be used in the function.</span></span>

<span data-ttu-id="b929c-163">下列範例是名為的函式 `Get-SmallFiles` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-163">The following example is a function called `Get-SmallFiles`.</span></span> <span data-ttu-id="b929c-164">此函數有 `$Size` 參數。</span><span class="sxs-lookup"><span data-stu-id="b929c-164">This function has a `$Size` parameter.</span></span> <span data-ttu-id="b929c-165">此函式會顯示小於參數值的所有檔案 `$Size` ，並排除目錄：</span><span class="sxs-lookup"><span data-stu-id="b929c-165">The function displays all the files that are smaller than the value of the `$Size` parameter, and it excludes directories:</span></span>

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="b929c-166">在函數中，您可以使用 `$Size` 變數，也就是為參數定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="b929c-166">In the function, you can use the `$Size` variable, which is the name defined for the parameter.</span></span>

<span data-ttu-id="b929c-167">若要使用此函式，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="b929c-167">To use this function, type the following command:</span></span>

```powershell
Get-SmallFiles -Size 50
```

<span data-ttu-id="b929c-168">您也可以輸入沒有參數名稱之具名引數的值。</span><span class="sxs-lookup"><span data-stu-id="b929c-168">You can also enter a value for a named parameter without the parameter name.</span></span>
<span data-ttu-id="b929c-169">例如，下列命令提供的結果與為 **Size** 參數命名的命令相同：</span><span class="sxs-lookup"><span data-stu-id="b929c-169">For example, the following command gives the same result as a command that names the **Size** parameter:</span></span>

```powershell
Get-SmallFiles 50
```

<span data-ttu-id="b929c-170">若要定義參數的預設值，請在參數名稱之後輸入等號和值，如下列範例變化所示 `Get-SmallFiles` ：</span><span class="sxs-lookup"><span data-stu-id="b929c-170">To define a default value for a parameter, type an equal sign and the value after the parameter name, as shown in the following variation of the `Get-SmallFiles` example:</span></span>

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="b929c-171">如果您 `Get-SmallFiles` 不輸入值，函數會將100指派給 `$size` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-171">If you type `Get-SmallFiles` without a value, the function assigns 100 to `$size`.</span></span> <span data-ttu-id="b929c-172">如果您提供值，此函數會使用該值。</span><span class="sxs-lookup"><span data-stu-id="b929c-172">If you provide a value, the function uses that value.</span></span>

<span data-ttu-id="b929c-173">（選擇性）您可以藉由將 **PSDefaultValue** 屬性新增至參數的描述，並指定 **PSDefaultValue** 的 **help** 屬性，提供描述參數預設值的簡短說明字串。</span><span class="sxs-lookup"><span data-stu-id="b929c-173">Optionally, you can provide a brief help string that describes the default value of your parameter, by adding the **PSDefaultValue** attribute to the description of your parameter, and specifying the **Help** property of **PSDefaultValue**.</span></span> <span data-ttu-id="b929c-174">若要提供說明字串來描述函式中 **Size** 參數 (100) 的預設值 `Get-SmallFiles` ，請新增 **PSDefaultValue** 屬性，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b929c-174">To provide a help string that describes the default value (100) of the **Size** parameter in the `Get-SmallFiles` function, add the **PSDefaultValue** attribute as shown in the following example.</span></span>

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

<span data-ttu-id="b929c-175">如需 **PSDefaultValue** 屬性類別的詳細資訊，請參閱 [PSDefaultValue 屬性成員](/dotnet/api/system.management.automation.psdefaultvalueattribute)。</span><span class="sxs-lookup"><span data-stu-id="b929c-175">For more information about the **PSDefaultValue** attribute class, see [PSDefaultValue Attribute Members](/dotnet/api/system.management.automation.psdefaultvalueattribute).</span></span>

### <a name="positional-parameters"></a><span data-ttu-id="b929c-176">位置參數</span><span class="sxs-lookup"><span data-stu-id="b929c-176">Positional Parameters</span></span>

<span data-ttu-id="b929c-177">位置參數是沒有參數名稱的參數。</span><span class="sxs-lookup"><span data-stu-id="b929c-177">A positional parameter is a parameter without a parameter name.</span></span> <span data-ttu-id="b929c-178">PowerShell 使用參數值順序，將每個參數值與函數中的參數產生關聯。</span><span class="sxs-lookup"><span data-stu-id="b929c-178">PowerShell uses the parameter value order to associate each parameter value with a parameter in the function.</span></span>

<span data-ttu-id="b929c-179">當您使用位置參數時，請在函式名稱之後輸入一或多個值。</span><span class="sxs-lookup"><span data-stu-id="b929c-179">When you use positional parameters, type one or more values after the function name.</span></span> <span data-ttu-id="b929c-180">位置參數值會指派給 `$args` 陣列變數。</span><span class="sxs-lookup"><span data-stu-id="b929c-180">Positional parameter values are assigned to the `$args` array variable.</span></span>
<span data-ttu-id="b929c-181">函數名稱後面的值會指派給陣列中的第一個位置 `$args` `$args[0]` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-181">The value that follows the function name is assigned to the first position in the `$args` array, `$args[0]`.</span></span>

<span data-ttu-id="b929c-182">下列 `Get-Extension` 函數會將副檔名新增 `.txt` 至您提供的檔案名：</span><span class="sxs-lookup"><span data-stu-id="b929c-182">The following `Get-Extension` function adds the `.txt` file name extension to a file name that you supply:</span></span>

```powershell
function Get-Extension {
  $name = $args[0] + ".txt"
  $name
}
```

```powershell
Get-Extension myTextFile
```

```Output
myTextFile.txt
```

### <a name="switch-parameters"></a><span data-ttu-id="b929c-183">切換參數</span><span class="sxs-lookup"><span data-stu-id="b929c-183">Switch Parameters</span></span>

<span data-ttu-id="b929c-184">切換參數是不需要值的參數。</span><span class="sxs-lookup"><span data-stu-id="b929c-184">A switch is a parameter that does not require a value.</span></span> <span data-ttu-id="b929c-185">相反地，您必須輸入函式名稱，後面接著 switch 參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="b929c-185">Instead, you type the function name followed by the name of the switch parameter.</span></span>

<span data-ttu-id="b929c-186">若要定義切換參數，請在 `[switch]` 參數名稱前面指定類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b929c-186">To define a switch parameter, specify the type `[switch]` before the parameter name, as shown in the following example:</span></span>

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

<span data-ttu-id="b929c-187">當您在函式 `On` 名稱之後輸入 switch 參數時，函數會顯示 "switch on"。</span><span class="sxs-lookup"><span data-stu-id="b929c-187">When you type the `On` switch parameter after the function name, the function displays "Switch on".</span></span> <span data-ttu-id="b929c-188">如果沒有切換參數，則會顯示 "Switch off"。</span><span class="sxs-lookup"><span data-stu-id="b929c-188">Without the switch parameter, it displays "Switch off".</span></span>

```powershell
Switch-Item -on
```

```Output
Switch on
```

```powershell
Switch-Item
```

```Output
Switch off
```

<span data-ttu-id="b929c-189">您也可以在執行函式時，將 **布林** 值指派給參數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b929c-189">You can also assign a **Boolean** value to a switch when you run the function, as shown in the following example:</span></span>

```powershell
Switch-Item -on:$true
```

```Output
Switch on
```

```powershell
Switch-Item -on:$false
```

```Output
Switch off
```

## <a name="using-splatting-to-represent-command-parameters"></a><span data-ttu-id="b929c-190">使用展開來代表命令參數</span><span class="sxs-lookup"><span data-stu-id="b929c-190">Using Splatting to Represent Command Parameters</span></span>

<span data-ttu-id="b929c-191">您可以使用展開來代表命令的參數。</span><span class="sxs-lookup"><span data-stu-id="b929c-191">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="b929c-192">這項功能是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="b929c-192">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="b929c-193">在呼叫會話命令的函式中使用此技巧。</span><span class="sxs-lookup"><span data-stu-id="b929c-193">Use this technique in functions that call commands in the session.</span></span> <span data-ttu-id="b929c-194">您不需要宣告或列舉命令參數，或在命令參數變更時變更函數。</span><span class="sxs-lookup"><span data-stu-id="b929c-194">You do not need to declare or enumerate the command parameters, or change the function when command parameters change.</span></span>

<span data-ttu-id="b929c-195">下列範例函式會呼叫 `Get-Command` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b929c-195">The following sample function calls the `Get-Command` cmdlet.</span></span> <span data-ttu-id="b929c-196">命令用 `@Args` 來表示的參數 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-196">The command uses `@Args` to represent the parameters of `Get-Command`.</span></span>

```powershell
function Get-MyCommand { Get-Command @Args }
```

<span data-ttu-id="b929c-197">`Get-Command`當您呼叫函數時，可以使用的所有參數 `Get-MyCommand` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-197">You can use all of the parameters of `Get-Command` when you call the `Get-MyCommand` function.</span></span> <span data-ttu-id="b929c-198">參數和參數值會使用傳遞至命令 `@Args` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-198">The parameters and parameter values are passed to the command using `@Args`.</span></span>

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

<span data-ttu-id="b929c-199">此 `@Args` 功能使用 `$Args` 自動參數，這代表未宣告的 Cmdlet 參數和其餘引數的值。</span><span class="sxs-lookup"><span data-stu-id="b929c-199">The `@Args` feature uses the `$Args` automatic parameter, which represents undeclared cmdlet parameters and values from remaining arguments.</span></span>

<span data-ttu-id="b929c-200">如需展開的詳細資訊，請參閱 [about_Splatting](about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="b929c-200">For more information about splatting, see [about_Splatting](about_Splatting.md).</span></span>

## <a name="piping-objects-to-functions"></a><span data-ttu-id="b929c-201">將物件輸送至函式</span><span class="sxs-lookup"><span data-stu-id="b929c-201">Piping Objects to Functions</span></span>

<span data-ttu-id="b929c-202">任何函數都可以從管線取得輸入。</span><span class="sxs-lookup"><span data-stu-id="b929c-202">Any function can take input from the pipeline.</span></span> <span data-ttu-id="b929c-203">您可以使用 `Begin` 、和關鍵字，控制函式處理管線輸入的方式 `Process` `End` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-203">You can control how a function processes input from the pipeline using `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="b929c-204">下列範例語法會顯示三個關鍵字：</span><span class="sxs-lookup"><span data-stu-id="b929c-204">The following sample syntax shows the three keywords:</span></span>

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="b929c-205">`Begin`語句清單只會在函數的開頭執行一次。</span><span class="sxs-lookup"><span data-stu-id="b929c-205">The `Begin` statement list runs one time only, at the beginning of the function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b929c-206">如果您的函式 `Begin` 定義 `Process` 或 `End` 區塊，則您的所有程式碼都必須位於這些區塊內。</span><span class="sxs-lookup"><span data-stu-id="b929c-206">If your function defines a `Begin`, `Process` or `End` block, all of your code must reside inside those blocks.</span></span> <span data-ttu-id="b929c-207">如果 *有定義任何* 區塊，則不會在區塊外辨識任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="b929c-207">No code will be recognized outside the blocks if *any* of the blocks are defined.</span></span>

<span data-ttu-id="b929c-208">`Process`語句清單會針對管線中的每個物件執行一次。</span><span class="sxs-lookup"><span data-stu-id="b929c-208">The `Process` statement list runs one time for each object in the pipeline.</span></span>
<span data-ttu-id="b929c-209">當 `Process` 區塊正在執行時，每個管線物件一次都會指派給 `$_` 自動變數（一個管線物件）。</span><span class="sxs-lookup"><span data-stu-id="b929c-209">While the `Process` block is running, each pipeline object is assigned to the `$_` automatic variable, one pipeline object at a time.</span></span>

<span data-ttu-id="b929c-210">在函數接收管線中的所有物件之後， `End` 語句清單會執行一次。</span><span class="sxs-lookup"><span data-stu-id="b929c-210">After the function receives all the objects in the pipeline, the `End` statement list runs one time.</span></span> <span data-ttu-id="b929c-211">如果未 `Begin` `Process` 使用、或 `End` 關鍵字，則會將所有語句視為 `End` 語句清單。</span><span class="sxs-lookup"><span data-stu-id="b929c-211">If no `Begin`, `Process`, or `End` keywords are used, all the statements are treated like an `End` statement list.</span></span>

<span data-ttu-id="b929c-212">下列函數會使用 `Process` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b929c-212">The following function uses the `Process` keyword.</span></span> <span data-ttu-id="b929c-213">此函數會顯示管線的範例：</span><span class="sxs-lookup"><span data-stu-id="b929c-213">The function displays examples from the pipeline:</span></span>

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

<span data-ttu-id="b929c-214">若要示範此函數，請輸入以逗號分隔的數位清單，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b929c-214">To demonstrate this function, enter an list of numbers separated by commas, as shown in the following example:</span></span>

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

<span data-ttu-id="b929c-215">當您在管線中使用函式時，輸送至函式的物件會指派給 `$input` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="b929c-215">When you use a function in a pipeline, the objects piped to the function are assigned to the `$input` automatic variable.</span></span> <span data-ttu-id="b929c-216">函式會在 `Begin` 任何物件來自管線之前，以關鍵字執行語句。</span><span class="sxs-lookup"><span data-stu-id="b929c-216">The function runs statements with the `Begin` keyword before any objects come from the pipeline.</span></span> <span data-ttu-id="b929c-217">`End`從管線接收所有物件之後，函數會使用關鍵字執行語句。</span><span class="sxs-lookup"><span data-stu-id="b929c-217">The function runs statements with the `End` keyword after all the objects have been received from the pipeline.</span></span>

<span data-ttu-id="b929c-218">下列範例會顯示 `$input` 具有和關鍵字的自動變數 `Begin` `End` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-218">The following example shows the `$input` automatic variable with `Begin` and `End` keywords.</span></span>

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

<span data-ttu-id="b929c-219">如果此函式是使用管線執行，則會顯示下列結果：</span><span class="sxs-lookup"><span data-stu-id="b929c-219">If this function is run by using the pipeline, it displays the following results:</span></span>

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

<span data-ttu-id="b929c-220">當 `Begin` 語句執行時，該函式不會有來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="b929c-220">When the `Begin` statement runs, the function does not have the input from the pipeline.</span></span> <span data-ttu-id="b929c-221">當函式 `End` 具有值之後，就會執行此語句。</span><span class="sxs-lookup"><span data-stu-id="b929c-221">The `End` statement runs after the function has the values.</span></span>

<span data-ttu-id="b929c-222">如果函式有 `Process` 關鍵字，則中的每個物件 `$input` 都會從移除 `$input` 並指派給 `$_` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-222">If the function has a `Process` keyword, each object in `$input` is removed from `$input` and assigned to `$_`.</span></span> <span data-ttu-id="b929c-223">下列範例有 `Process` 語句清單：</span><span class="sxs-lookup"><span data-stu-id="b929c-223">The following example has a `Process` statement list:</span></span>

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

<span data-ttu-id="b929c-224">在此範例中，輸送至函式的每個物件都會傳送至 `Process` 語句清單。</span><span class="sxs-lookup"><span data-stu-id="b929c-224">In this example, each object that is piped to the function is sent to the `Process` statement list.</span></span> <span data-ttu-id="b929c-225">`Process`語句會在每個物件上執行，一次一個物件。</span><span class="sxs-lookup"><span data-stu-id="b929c-225">The `Process` statements run on each object, one object at a time.</span></span> <span data-ttu-id="b929c-226">`$input`當函數到達關鍵字時，自動變數是空的 `End` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-226">The `$input` automatic variable is empty when the function reaches the `End` keyword.</span></span>

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

<span data-ttu-id="b929c-227">如需詳細資訊，請參閱[使用枚舉](about_Automatic_Variables.md#using-enumerators)器</span><span class="sxs-lookup"><span data-stu-id="b929c-227">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators)</span></span>

## <a name="filters"></a><span data-ttu-id="b929c-228">篩選器</span><span class="sxs-lookup"><span data-stu-id="b929c-228">Filters</span></span>

<span data-ttu-id="b929c-229">篩選是在管線中的每個物件上執行的函式類型。</span><span class="sxs-lookup"><span data-stu-id="b929c-229">A filter is a type of function that runs on each object in the pipeline.</span></span> <span data-ttu-id="b929c-230">篩選準則類似于函式及其在區塊中的所有語句 `Process` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-230">A filter resembles a function with all its statements in a `Process` block.</span></span>

<span data-ttu-id="b929c-231">篩選準則的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="b929c-231">The syntax of a filter is as follows:</span></span>

```
filter [<scope:>]<name> {<statement list>}
```

<span data-ttu-id="b929c-232">下列篩選器會從管線中取得記錄專案，然後顯示整個專案或僅顯示專案的訊息部分：</span><span class="sxs-lookup"><span data-stu-id="b929c-232">The following filter takes log entries from the pipeline and then displays either the whole entry or only the message portion of the entry:</span></span>

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a><span data-ttu-id="b929c-233">函數範圍</span><span class="sxs-lookup"><span data-stu-id="b929c-233">Function Scope</span></span>

<span data-ttu-id="b929c-234">函數存在於建立它的範圍中。</span><span class="sxs-lookup"><span data-stu-id="b929c-234">A function exists in the scope in which it was created.</span></span>

<span data-ttu-id="b929c-235">如果函式是腳本的一部分，則函式可用於該腳本內的語句。</span><span class="sxs-lookup"><span data-stu-id="b929c-235">If a function is part of a script, the function is available to statements within that script.</span></span> <span data-ttu-id="b929c-236">根據預設，腳本中的函式無法在命令提示字元中使用。</span><span class="sxs-lookup"><span data-stu-id="b929c-236">By default, a function in a script is not available at the command prompt.</span></span>

<span data-ttu-id="b929c-237">您可以指定函數的範圍。</span><span class="sxs-lookup"><span data-stu-id="b929c-237">You can specify the scope of a function.</span></span> <span data-ttu-id="b929c-238">例如，在下列範例中，函式會新增至全域範圍：</span><span class="sxs-lookup"><span data-stu-id="b929c-238">For example, the function is added to the global scope in the following example:</span></span>

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

<span data-ttu-id="b929c-239">當函式在全域範圍內時，您可以在腳本、函數和命令列中使用函數。</span><span class="sxs-lookup"><span data-stu-id="b929c-239">When a function is in the global scope, you can use the function in scripts, in functions, and at the command line.</span></span>

<span data-ttu-id="b929c-240">函數通常會建立範圍。</span><span class="sxs-lookup"><span data-stu-id="b929c-240">Functions normally create a scope.</span></span> <span data-ttu-id="b929c-241">在函數中建立的專案（例如變數）只存在於函式範圍中。</span><span class="sxs-lookup"><span data-stu-id="b929c-241">The items created in a function, such as variables, exist only in the function scope.</span></span>

<span data-ttu-id="b929c-242">如需 PowerShell 中之範圍的詳細資訊，請參閱 [about_Scopes](about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="b929c-242">For more information about scope in PowerShell, see [about_Scopes](about_Scopes.md).</span></span>

## <a name="finding-and-managing-functions-using-the-function-drive"></a><span data-ttu-id="b929c-243">使用 Function：磁片磁碟機尋找和管理函數</span><span class="sxs-lookup"><span data-stu-id="b929c-243">Finding and Managing Functions Using the Function: Drive</span></span>

<span data-ttu-id="b929c-244">PowerShell 中的所有函式和篩選都會自動儲存在 `Function:` 磁片磁碟機中。</span><span class="sxs-lookup"><span data-stu-id="b929c-244">All the functions and filters in PowerShell are automatically stored in the `Function:` drive.</span></span> <span data-ttu-id="b929c-245">此磁片磁碟機是 **由 PowerShell 函** 式提供者所公開。</span><span class="sxs-lookup"><span data-stu-id="b929c-245">This drive is exposed by the PowerShell **Function** provider.</span></span>

<span data-ttu-id="b929c-246">參考磁片磁碟機時，請在函式 `Function:` 後面 **Function** 輸入冒號，就像參考 `C` 電腦的或 `D` 磁片磁碟機一樣。</span><span class="sxs-lookup"><span data-stu-id="b929c-246">When referring to the `Function:` drive, type a colon after **Function** , just as you would do when referencing the `C` or `D` drive of a computer.</span></span>

<span data-ttu-id="b929c-247">下列命令會顯示目前 PowerShell 會話中的所有函式：</span><span class="sxs-lookup"><span data-stu-id="b929c-247">The following command displays all the functions in the current session of PowerShell:</span></span>

```powershell
Get-ChildItem function:
```

<span data-ttu-id="b929c-248">函數中的命令會以腳本區塊的形式儲存在函式的 definition 屬性中。</span><span class="sxs-lookup"><span data-stu-id="b929c-248">The commands in the function are stored as a script block in the definition property of the function.</span></span> <span data-ttu-id="b929c-249">例如，若要在 PowerShell 隨附的 Help 函式中顯示命令，請輸入：</span><span class="sxs-lookup"><span data-stu-id="b929c-249">For example, to display the commands in the Help function that comes with PowerShell, type:</span></span>

```powershell
(Get-ChildItem function:help).Definition
```

<span data-ttu-id="b929c-250">您也可以使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="b929c-250">You can also use the following syntax.</span></span>

```powershell
$function:help
```

<span data-ttu-id="b929c-251">如需有關磁片磁碟機的詳細資訊 `Function:` ，請參閱 **函數** 提供者的說明主題。</span><span class="sxs-lookup"><span data-stu-id="b929c-251">For more information about the `Function:` drive, see the help topic for the **Function** provider.</span></span> <span data-ttu-id="b929c-252">輸入 `Get-Help Function`。</span><span class="sxs-lookup"><span data-stu-id="b929c-252">Type `Get-Help Function`.</span></span>

## <a name="reusing-functions-in-new-sessions"></a><span data-ttu-id="b929c-253">在新的會話中重複使用函數</span><span class="sxs-lookup"><span data-stu-id="b929c-253">Reusing Functions in New Sessions</span></span>

<span data-ttu-id="b929c-254">當您在 PowerShell 命令提示字元中輸入函式時，該函式會成為目前會話的一部分。</span><span class="sxs-lookup"><span data-stu-id="b929c-254">When you type a function at the PowerShell command prompt, the function becomes part of the current session.</span></span> <span data-ttu-id="b929c-255">它可供使用，直到會話結束為止。</span><span class="sxs-lookup"><span data-stu-id="b929c-255">It is available until the session ends.</span></span>

<span data-ttu-id="b929c-256">若要在所有 PowerShell 會話中使用您的函式，請將函式新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="b929c-256">To use your function in all PowerShell sessions, add the function to your PowerShell profile.</span></span> <span data-ttu-id="b929c-257">如需設定檔的詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="b929c-257">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="b929c-258">您也可以將函數儲存在 PowerShell 腳本檔案中。</span><span class="sxs-lookup"><span data-stu-id="b929c-258">You can also save your function in a PowerShell script file.</span></span> <span data-ttu-id="b929c-259">在文字檔中輸入您的函式，然後使用副檔名儲存檔案 `.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="b929c-259">Type your function in a text file, and then save the file with the `.ps1` file name extension.</span></span>

## <a name="writing-help-for-functions"></a><span data-ttu-id="b929c-260">撰寫函數的說明</span><span class="sxs-lookup"><span data-stu-id="b929c-260">Writing Help for Functions</span></span>

<span data-ttu-id="b929c-261">此 Cmdlet 會取得函式的說明 `Get-Help` ，以及 Cmdlet、提供者和腳本的說明。</span><span class="sxs-lookup"><span data-stu-id="b929c-261">The `Get-Help` cmdlet gets help for functions, as well as for cmdlets, providers, and scripts.</span></span> <span data-ttu-id="b929c-262">若要取得函式的說明，請輸入， `Get-Help` 後面接著函式名稱。</span><span class="sxs-lookup"><span data-stu-id="b929c-262">To get help for a function, type `Get-Help` followed by the function name.</span></span>

<span data-ttu-id="b929c-263">例如，若要取得函數的說明 `Get-MyDisks` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="b929c-263">For example, to get help for the `Get-MyDisks` function, type:</span></span>

```powershell
Get-Help Get-MyDisks
```

<span data-ttu-id="b929c-264">您可以使用下列兩種方法的其中一個來撰寫函數的說明：</span><span class="sxs-lookup"><span data-stu-id="b929c-264">You can write help for a function by using either of the two following methods:</span></span>

- <span data-ttu-id="b929c-265">函數的 Comment-Based 說明</span><span class="sxs-lookup"><span data-stu-id="b929c-265">Comment-Based Help for Functions</span></span>

  <span data-ttu-id="b929c-266">使用批註中的特殊關鍵字來建立說明主題。</span><span class="sxs-lookup"><span data-stu-id="b929c-266">Create a help topic by using special keywords in the comments.</span></span> <span data-ttu-id="b929c-267">若要為函式建立以批註為基礎的說明，必須將批註放在函式主體的開頭或結尾，或在 function 關鍵字前面的行上。</span><span class="sxs-lookup"><span data-stu-id="b929c-267">To create comment-based help for a function, the comments must be placed at the beginning or end of the function body or on the lines preceding the function keyword.</span></span> <span data-ttu-id="b929c-268">如需以批註為基礎的說明的詳細資訊，請參閱 [about_Comment_Based_Help](about_Comment_Based_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="b929c-268">For more information about comment-based help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="b929c-269">函數的 XML-Based 說明</span><span class="sxs-lookup"><span data-stu-id="b929c-269">XML-Based Help for Functions</span></span>

  <span data-ttu-id="b929c-270">建立以 XML 為基礎的說明主題，例如通常為 Cmdlet 建立的類型。</span><span class="sxs-lookup"><span data-stu-id="b929c-270">Create an XML-based help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="b929c-271">如果您要將說明主題當地語系化為多種語言，則需要以 XML 為基礎的說明。</span><span class="sxs-lookup"><span data-stu-id="b929c-271">XML-based help is required if you are localizing help topics into multiple languages.</span></span>

  <span data-ttu-id="b929c-272">若要將函式與以 XML 為基礎的說明主題產生關聯，請使用以 `.ExternalHelp` 批註為基礎的說明關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b929c-272">To associate the function with the XML-based help topic, use the `.ExternalHelp` comment-based help keyword.</span></span> <span data-ttu-id="b929c-273">如果沒有這個關鍵字，則找不到函式 `Get-Help` 說明主題，而且對 `Get-Help` 函數的呼叫只會傳回自動產生的說明。</span><span class="sxs-lookup"><span data-stu-id="b929c-273">Without this keyword, `Get-Help` cannot find the function help topic and calls to `Get-Help` for the function return only auto-generated help.</span></span>

  <span data-ttu-id="b929c-274">如需關鍵字的詳細資訊 `ExternalHelp` ，請參閱 [about_Comment_Based_Help](about_Comment_Based_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="b929c-274">For more information about the `ExternalHelp` keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="b929c-275">如需以 XML 為基礎之說明的詳細資訊，請參閱 [如何撰寫 Cmdlet 說明](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)。</span><span class="sxs-lookup"><span data-stu-id="b929c-275">For more information about XML-based help, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="see-also"></a><span data-ttu-id="b929c-276">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b929c-276">See also</span></span>

[<span data-ttu-id="b929c-277">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="b929c-277">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="b929c-278">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="b929c-278">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="b929c-279">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="b929c-279">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="b929c-280">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="b929c-280">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="b929c-281">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="b929c-281">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="b929c-282">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="b929c-282">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="b929c-283">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="b929c-283">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="b929c-284">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="b929c-284">about_Parameters</span></span>](about_Parameters.md)

[<span data-ttu-id="b929c-285">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="b929c-285">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="b929c-286">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="b929c-286">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="b929c-287">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="b929c-287">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="b929c-288">about_Function_provider</span><span class="sxs-lookup"><span data-stu-id="b929c-288">about_Function_provider</span></span>](about_Function_provider.md)
