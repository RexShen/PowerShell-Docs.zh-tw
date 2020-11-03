---
description: 說明如何使用展開將參數傳遞至 PowerShell 中的命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: 0cf9702adcc7d19a19d9aaa9673fb42e3af715fa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207907"
---
# <a name="about-splatting"></a><span data-ttu-id="173fb-104">關於展開</span><span class="sxs-lookup"><span data-stu-id="173fb-104">About Splatting</span></span>

## <a name="short-description"></a><span data-ttu-id="173fb-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="173fb-105">Short description</span></span>

<span data-ttu-id="173fb-106">說明如何使用展開將參數傳遞至 PowerShell 中的命令。</span><span class="sxs-lookup"><span data-stu-id="173fb-106">Describes how to use splatting to pass parameters to commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="173fb-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="173fb-107">Long description</span></span>

<span data-ttu-id="173fb-108">展開是將參數值的集合傳遞至命令做為單位的方法。</span><span class="sxs-lookup"><span data-stu-id="173fb-108">Splatting is a method of passing a collection of parameter values to a command as a unit.</span></span> <span data-ttu-id="173fb-109">PowerShell 會將集合中的每個值與命令參數產生關聯。</span><span class="sxs-lookup"><span data-stu-id="173fb-109">PowerShell associates each value in the collection with a command parameter.</span></span> <span data-ttu-id="173fb-110">Splatted 參數值會儲存在名為展開的變數中，這看起來像是標準變數，但以 At 符號 (`@`) ，而不是以貨幣符號 (`$`) 。</span><span class="sxs-lookup"><span data-stu-id="173fb-110">Splatted parameter values are stored in named splatting variables, which look like standard variables, but begin with an At symbol (`@`) instead of a dollar sign (`$`).</span></span> <span data-ttu-id="173fb-111">At 符號會告知 PowerShell 您要傳遞值的集合，而不是單一值。</span><span class="sxs-lookup"><span data-stu-id="173fb-111">The At symbol tells PowerShell that you are passing a collection of values, instead of a single value.</span></span>

<span data-ttu-id="173fb-112">展開可讓您的命令變得更短、更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="173fb-112">Splatting makes your commands shorter and easier to read.</span></span> <span data-ttu-id="173fb-113">您可以在不同的命令呼叫中重複使用展開值，並使用展開將參數值從 `$PSBoundParameters` 自動變數傳遞給其他腳本和函式。</span><span class="sxs-lookup"><span data-stu-id="173fb-113">You can reuse the splatting values in different command calls and use splatting to pass parameter values from the `$PSBoundParameters` automatic variable to other scripts and functions.</span></span>

<span data-ttu-id="173fb-114">從 Windows PowerShell 3.0 開始，您也可以使用展開來代表命令的所有參數。</span><span class="sxs-lookup"><span data-stu-id="173fb-114">Beginning in Windows PowerShell 3.0, you can also use splatting to represent all parameters of a command.</span></span>

## <a name="syntax"></a><span data-ttu-id="173fb-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="173fb-115">Syntax</span></span>

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

<span data-ttu-id="173fb-116">若要提供位置參數的參數值（不需要參數名稱），請使用陣列語法。</span><span class="sxs-lookup"><span data-stu-id="173fb-116">To provide parameter values for positional parameters, in which parameter names are not required, use the array syntax.</span></span> <span data-ttu-id="173fb-117">若要提供參數名稱和值組，請使用雜湊表語法。</span><span class="sxs-lookup"><span data-stu-id="173fb-117">To provide parameter name and value pairs, use the hash table syntax.</span></span> <span data-ttu-id="173fb-118">Splatted 值可出現在參數清單中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="173fb-118">The splatted value can appear anywhere in the parameter list.</span></span>

<span data-ttu-id="173fb-119">展開時，您不需要使用雜湊表或陣列來傳遞所有參數。</span><span class="sxs-lookup"><span data-stu-id="173fb-119">When splatting, you do not need to use a hash table or an array to pass all parameters.</span></span> <span data-ttu-id="173fb-120">您可以使用展開傳遞一些參數，並依位置或依參數名稱傳遞其他參數。</span><span class="sxs-lookup"><span data-stu-id="173fb-120">You may pass some parameters by using splatting and pass others by position or by parameter name.</span></span> <span data-ttu-id="173fb-121">此外，您可以在單一命令中 splat 多個物件，如此就不會針對每個參數傳遞多個值。</span><span class="sxs-lookup"><span data-stu-id="173fb-121">Also, you can splat multiple objects in a single command so you don't pass more than one value for each parameter.</span></span>

## <a name="splatting-with-hash-tables"></a><span data-ttu-id="173fb-122">具有雜湊表的展開</span><span class="sxs-lookup"><span data-stu-id="173fb-122">Splatting with hash tables</span></span>

<span data-ttu-id="173fb-123">使用雜湊表來 splat 參數名稱和值組。</span><span class="sxs-lookup"><span data-stu-id="173fb-123">Use a hash table to splat parameter name and value pairs.</span></span> <span data-ttu-id="173fb-124">您可以將此格式用於所有參數類型，包括位置和切換參數。</span><span class="sxs-lookup"><span data-stu-id="173fb-124">You can use this format for all parameter types, including positional and switch parameters.</span></span>
<span data-ttu-id="173fb-125">位置參數必須以名稱指派。</span><span class="sxs-lookup"><span data-stu-id="173fb-125">Positional parameters must be assigned by name.</span></span>

<span data-ttu-id="173fb-126">下列範例會比較兩個 `Copy-Item` 命令，以將 Test.txt 檔案複製到相同目錄中的 Test2.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="173fb-126">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="173fb-127">第一個範例會使用包含參數名稱的傳統格式。</span><span class="sxs-lookup"><span data-stu-id="173fb-127">The first example uses the traditional format in which parameter names are included.</span></span>

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

<span data-ttu-id="173fb-128">第二個範例會使用雜湊表展開。</span><span class="sxs-lookup"><span data-stu-id="173fb-128">The second example uses hash table splatting.</span></span> <span data-ttu-id="173fb-129">第一個命令會建立參數名稱和參數值組的雜湊表，並將它儲存在 `$HashArguments` 變數中。</span><span class="sxs-lookup"><span data-stu-id="173fb-129">The first command creates a hash table of parameter-name and parameter-value pairs and stores it in the `$HashArguments` variable.</span></span> <span data-ttu-id="173fb-130">第二個命令會 `$HashArguments` 在命令中使用展開的變數。</span><span class="sxs-lookup"><span data-stu-id="173fb-130">The second command uses the `$HashArguments` variable in a command with splatting.</span></span> <span data-ttu-id="173fb-131">At 符號 (`@HashArguments`) 會取代命令中的貨幣符號 (`$HashArguments`) 。</span><span class="sxs-lookup"><span data-stu-id="173fb-131">The At symbol (`@HashArguments`) replaces the dollar sign (`$HashArguments`) in the command.</span></span>

<span data-ttu-id="173fb-132">若要提供 **WhatIf** 切換參數的值，請使用 `$True` 或 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="173fb-132">To provide a value for the **WhatIf** switch parameter, use `$True` or `$False`.</span></span>

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> <span data-ttu-id="173fb-133">在第一個命令中，At 符號 (`@`) 表示雜湊表，而不是 splatted 值。</span><span class="sxs-lookup"><span data-stu-id="173fb-133">In the first command, the At symbol (`@`) indicates a hash table, not a splatted value.</span></span> <span data-ttu-id="173fb-134">PowerShell 中的雜湊表語法如下： `@{<name>=<value>; <name>=<value>; ...}`</span><span class="sxs-lookup"><span data-stu-id="173fb-134">The syntax for hash tables in PowerShell is: `@{<name>=<value>; <name>=<value>; ...}`</span></span>

## <a name="splatting-with-arrays"></a><span data-ttu-id="173fb-135">具有陣列的展開</span><span class="sxs-lookup"><span data-stu-id="173fb-135">Splatting with arrays</span></span>

<span data-ttu-id="173fb-136">使用陣列來 splat 位置參數的值，而不需要參數名稱。</span><span class="sxs-lookup"><span data-stu-id="173fb-136">Use an array to splat values for positional parameters, which do not require parameter names.</span></span> <span data-ttu-id="173fb-137">這些值必須是陣列中的位置編號順序。</span><span class="sxs-lookup"><span data-stu-id="173fb-137">The values must be in position-number order in the array.</span></span>

<span data-ttu-id="173fb-138">下列範例會比較兩個 `Copy-Item` 命令，以將 Test.txt 檔案複製到相同目錄中的 Test2.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="173fb-138">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="173fb-139">第一個範例會使用傳統格式，其中省略參數名稱。</span><span class="sxs-lookup"><span data-stu-id="173fb-139">The first example uses the traditional format in which parameter names are omitted.</span></span> <span data-ttu-id="173fb-140">參數值會以位置順序出現在命令中。</span><span class="sxs-lookup"><span data-stu-id="173fb-140">The parameter values appear in position order in the command.</span></span>

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

<span data-ttu-id="173fb-141">第二個範例使用陣列展開。</span><span class="sxs-lookup"><span data-stu-id="173fb-141">The second example uses array splatting.</span></span> <span data-ttu-id="173fb-142">第一個命令會建立參數值的陣列，並將其儲存在 `$ArrayArguments` 變數中。</span><span class="sxs-lookup"><span data-stu-id="173fb-142">The first command creates an array of the parameter values and stores it in the `$ArrayArguments` variable.</span></span> <span data-ttu-id="173fb-143">值是在陣列中的位置順序。</span><span class="sxs-lookup"><span data-stu-id="173fb-143">The values are in position order in the array.</span></span> <span data-ttu-id="173fb-144">第二個命令使用 `$ArrayArguments` 展開中命令的變數。</span><span class="sxs-lookup"><span data-stu-id="173fb-144">The second command uses the `$ArrayArguments` variable in a command in splatting.</span></span> <span data-ttu-id="173fb-145">At 符號 (`@ArrayArguments`) 會取代命令中的貨幣符號 (`$ArrayArguments`) 。</span><span class="sxs-lookup"><span data-stu-id="173fb-145">The At symbol (`@ArrayArguments`) replaces the dollar sign (`$ArrayArguments`) in the command.</span></span>

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a><span data-ttu-id="173fb-146">使用 ArgumentList 參數</span><span class="sxs-lookup"><span data-stu-id="173fb-146">Using the ArgumentList parameter</span></span>

<span data-ttu-id="173fb-147">有數個 Cmdlet 具有 **ArgumentList** 參數，可用來將參數值傳遞給 Cmdlet 所執行的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="173fb-147">Several cmdlets have an **ArgumentList** parameter that is used to pass parameter values to a script block that is executed by the cmdlet.</span></span> <span data-ttu-id="173fb-148">**ArgumentList** 參數會取得傳遞至腳本區塊的值陣列。</span><span class="sxs-lookup"><span data-stu-id="173fb-148">The **ArgumentList** parameter takes an array of values that is passed to the script block.</span></span> <span data-ttu-id="173fb-149">PowerShell 實際上使用陣列展開將值系結至腳本區塊的參數。</span><span class="sxs-lookup"><span data-stu-id="173fb-149">PowerShell is effectively using array splatting to bind the values to the parameters of the script block.</span></span> <span data-ttu-id="173fb-150">使用 **ArgumentList** 時，如果您需要將陣列當作系結至單一參數的單一物件傳遞，則必須將陣列包裝為另一個陣列的唯一元素。</span><span class="sxs-lookup"><span data-stu-id="173fb-150">When using **ArgumentList** , if you need to pass an array as a single object bound to a single parameter, you must wrap the array as the only element of another array.</span></span>

<span data-ttu-id="173fb-151">下列範例中的腳本區塊會採用一個字串陣列的單一參數。</span><span class="sxs-lookup"><span data-stu-id="173fb-151">The following example has a script block that takes a single parameter that is an array of strings.</span></span>

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```

<span data-ttu-id="173fb-152">在此範例中，只有中的第一個專案 `$array` 會傳遞至腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="173fb-152">In this example, only the first item in `$array` is passed to the script block.</span></span>
```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList (,$array)
```

<span data-ttu-id="173fb-153">在此範例中， `$array` 會包裝在陣列中，以便將整個陣列以單一物件的形式傳遞至腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="173fb-153">In this example, `$array` is wrapped in an array so that the entire array is passed to the script block as a single object.</span></span>

```Output
Hello World!
```

## <a name="examples"></a><span data-ttu-id="173fb-154">範例</span><span class="sxs-lookup"><span data-stu-id="173fb-154">Examples</span></span>

<span data-ttu-id="173fb-155">此範例顯示如何在不同的命令中重複使用 splatted 值。</span><span class="sxs-lookup"><span data-stu-id="173fb-155">This example shows how to reuse splatted values in different commands.</span></span> <span data-ttu-id="173fb-156">此範例中的命令會使用 `Write-Host` Cmdlet 將訊息寫入至主機程式主控台。</span><span class="sxs-lookup"><span data-stu-id="173fb-156">The commands in this example use the `Write-Host` cmdlet to write messages to the host program console.</span></span> <span data-ttu-id="173fb-157">它會使用展開來指定前景和背景色彩。</span><span class="sxs-lookup"><span data-stu-id="173fb-157">It uses splatting to specify the foreground and background colors.</span></span>

<span data-ttu-id="173fb-158">若要變更所有命令的色彩，請只變更變數的值 `$Colors` 。</span><span class="sxs-lookup"><span data-stu-id="173fb-158">To change the colors of all commands, just change the value of the `$Colors` variable.</span></span>

<span data-ttu-id="173fb-159">第一個命令會建立參數名稱和值的雜湊表，並將雜湊表儲存在 `$Colors` 變數中。</span><span class="sxs-lookup"><span data-stu-id="173fb-159">The first command creates a hash table of parameter names and values and stores the hash table in the `$Colors` variable.</span></span>

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

<span data-ttu-id="173fb-160">第二個和第三個命令會 `$Colors` 在命令中使用展開的變數 `Write-Host` 。</span><span class="sxs-lookup"><span data-stu-id="173fb-160">The second and third commands use the `$Colors` variable for splatting in a `Write-Host` command.</span></span> <span data-ttu-id="173fb-161">若要使用 `$Colors variable` ，請以 () 的 At 符號取代貨幣符號 (`$Colors`) `@Colors` 。</span><span class="sxs-lookup"><span data-stu-id="173fb-161">To use the `$Colors variable`, replace the dollar sign (`$Colors`) with an At symbol (`@Colors`).</span></span>

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

<span data-ttu-id="173fb-162">此範例示範如何使用展開和自動變數，將其參數轉送至其他命令 `$PSBoundParameters` 。</span><span class="sxs-lookup"><span data-stu-id="173fb-162">This example shows how to forward their parameters to other commands by using splatting and the `$PSBoundParameters` automatic variable.</span></span>

<span data-ttu-id="173fb-163">`$PSBoundParameters`自動變數是字典物件， (的) ，其中包含執行腳本或函式時所使用的所有參數名稱和值。</span><span class="sxs-lookup"><span data-stu-id="173fb-163">The `$PSBoundParameters` automatic variable is a dictionary object (System.Collections.Generic.Dictionary) that contains all the parameter names and values that are used when a script or function is run.</span></span>

<span data-ttu-id="173fb-164">在下列範例中，我們會使用 `$PSBoundParameters` 變數，將傳遞給腳本或函式的參數值轉送 `Test2` 至函式 `Test1` 。</span><span class="sxs-lookup"><span data-stu-id="173fb-164">In the following example, we use the `$PSBoundParameters` variable to forward the parameters values passed to a script or function from `Test2` function to the `Test1` function.</span></span> <span data-ttu-id="173fb-165">這兩個函式呼叫都是 `Test1` `Test2` 使用展開。</span><span class="sxs-lookup"><span data-stu-id="173fb-165">Both calls to the `Test1` function from `Test2` use splatting.</span></span>

```powershell
function Test1
{
    param($a, $b, $c)

    $a
    $b
    $c
}

function Test2
{
    param($a, $b, $c)

    #Call the Test1 function with $a, $b, and $c.
    Test1 @PsBoundParameters

    #Call the Test1 function with $b and $c, but not with $a
    $LimitedParameters = $PSBoundParameters
    $LimitedParameters.Remove("a") | Out-Null
    Test1 @LimitedParameters
}
```

```Output
Test2 -a 1 -b 2 -c 3
1
2
3
2
3
```

## <a name="splatting-command-parameters"></a><span data-ttu-id="173fb-166">展開命令參數</span><span class="sxs-lookup"><span data-stu-id="173fb-166">Splatting command parameters</span></span>

<span data-ttu-id="173fb-167">您可以使用展開來代表命令的參數。</span><span class="sxs-lookup"><span data-stu-id="173fb-167">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="173fb-168">當您建立 proxy 函式時（也就是呼叫另一個命令的函式），這項技術會很有用。</span><span class="sxs-lookup"><span data-stu-id="173fb-168">This technique is useful when you are creating a proxy function, that is, a function that calls another command.</span></span> <span data-ttu-id="173fb-169">這項功能是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="173fb-169">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="173fb-170">若要 splat 命令的參數，請使用 `@Args` 來代表命令參數。</span><span class="sxs-lookup"><span data-stu-id="173fb-170">To splat the parameters of a command, use `@Args` to represent the command parameters.</span></span> <span data-ttu-id="173fb-171">這項技術比列舉命令參數更為簡單，即使呼叫的命令的參數變更，也不需要修訂。</span><span class="sxs-lookup"><span data-stu-id="173fb-171">This technique is easier than enumerating command parameters and it works without revision even if the parameters of the called command change.</span></span>

<span data-ttu-id="173fb-172">這項功能會使用 `$Args` 自動變數，其中包含所有未指派的參數值。</span><span class="sxs-lookup"><span data-stu-id="173fb-172">The feature uses the `$Args` automatic variable, which contains all unassigned parameter values.</span></span>

<span data-ttu-id="173fb-173">例如，下列函式會呼叫 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="173fb-173">For example, the following function calls the `Get-Process` cmdlet.</span></span> <span data-ttu-id="173fb-174">在此函數中， `@Args` 表示 Cmdlet 的所有參數 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="173fb-174">In this function, `@Args` represents all the parameters of the `Get-Process` cmdlet.</span></span>

```powershell
function Get-MyProcess { Get-Process @Args }
```

<span data-ttu-id="173fb-175">當您使用 `Get-MyProcess` 函數時，所有未指派的參數和參數值都會傳遞至 `@Args` ，如下列命令所示。</span><span class="sxs-lookup"><span data-stu-id="173fb-175">When you use the `Get-MyProcess` function, all unassigned parameters and parameter values are passed to `@Args`, as shown in the following commands.</span></span>

```powershell
Get-MyProcess -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    463      46   225484     237196   719    15.86   3228 powershell
```

```powershell
Get-MyProcess -Name PowerShell_Ise -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.2.9200.16384   6.2.9200.1638... C:\Windows\system32\WindowsPowerShell\...
```

<span data-ttu-id="173fb-176">您可以 `@Args` 在已明確宣告參數的函式中使用。</span><span class="sxs-lookup"><span data-stu-id="173fb-176">You can use `@Args` in a function that has explicitly declared parameters.</span></span> <span data-ttu-id="173fb-177">您可以在函式中使用一次以上，但您輸入的所有參數都會傳遞至的所有實例 `@Args` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="173fb-177">You can use it more than once in a function, but all parameters that you enter are passed to all instances of `@Args`, as shown in the following example.</span></span>

```powershell
function Get-MyCommand
{
    Param ([switch]$P, [switch]$C)
    if ($P) { Get-Process @Args }
    if ($C) { Get-Command @Args }
}

Get-MyCommand -P -C -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
408      28    75568      83176   620     1.33   1692 powershell

Path               : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Extension          : .exe
Definition         : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Visibility         : Public
OutputType         : {System.String}
Name               : powershell.exe
CommandType        : Application
ModuleName         :
Module             :
RemotingCapability : PowerShell
Parameters         :
ParameterSets      :
HelpUri            :
FileVersionInfo    : File:             C:\Windows\System32\WindowsPowerShell
                     \v1.0\powershell.exe
                     InternalName:     POWERSHELL
                     OriginalFilename: PowerShell.EXE.MUI
                     FileVersion:      10.0.14393.0 (rs1_release.160715-1616
                     FileDescription:  Windows PowerShell
                     Product:          Microsoft Windows Operating System
                     ProductVersion:   10.0.14393.0
                     Debug:            False
                     Patched:          False
                     PreRelease:       False
                     PrivateBuild:     False
                     SpecialBuild:     False
                     Language:         English (United States)
```

## <a name="notes"></a><span data-ttu-id="173fb-178">備忘稿</span><span class="sxs-lookup"><span data-stu-id="173fb-178">Notes</span></span>

<span data-ttu-id="173fb-179">如果您使用 **CmdletBinding** 或 **參數** 屬性將函式變成 advanced 函數，則函式中將 `$args` 無法再使用自動變數。</span><span class="sxs-lookup"><span data-stu-id="173fb-179">If you make a function into an advanced function by using either the **CmdletBinding** or **Parameter** attributes, the `$args` automatic variable is no longer available in the function.</span></span> <span data-ttu-id="173fb-180">Advanced 函數需要明確的參數定義。</span><span class="sxs-lookup"><span data-stu-id="173fb-180">Advanced functions require explicit parameter definition.</span></span>

<span data-ttu-id="173fb-181">PowerShell Desired State Configuration (DSC) 並未設計成使用展開。</span><span class="sxs-lookup"><span data-stu-id="173fb-181">PowerShell Desired State Configuration (DSC) was not designed to use splatting.</span></span>
<span data-ttu-id="173fb-182">您無法使用展開將值傳遞至 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="173fb-182">You cannot use splatting to pass values into a DSC resource.</span></span> <span data-ttu-id="173fb-183">如需詳細資訊，請參閱 Gael Colas 的文章 [虛擬展開 DSC 資源](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)。</span><span class="sxs-lookup"><span data-stu-id="173fb-183">For more information, see Gael Colas' article [Pseudo-Splatting DSC Resources](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/).</span></span>

## <a name="see-also"></a><span data-ttu-id="173fb-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="173fb-184">See also</span></span>

[<span data-ttu-id="173fb-185">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="173fb-185">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="173fb-186">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="173fb-186">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="173fb-187">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="173fb-187">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="173fb-188">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="173fb-188">about_Parameters</span></span>](about_Parameters.md)
