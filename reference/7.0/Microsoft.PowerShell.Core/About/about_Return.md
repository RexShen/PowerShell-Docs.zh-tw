---
description: 結束目前的範圍，這可以是函式、指令碼或指令碼區塊。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: d1cfdf66cbcbc1bb93d6eaef238e9e5d39b56187
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208156"
---
# <a name="about-return"></a><span data-ttu-id="66484-104">關於 Return</span><span class="sxs-lookup"><span data-stu-id="66484-104">About Return</span></span>

## <a name="short-description"></a><span data-ttu-id="66484-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="66484-105">Short description</span></span>

<span data-ttu-id="66484-106">結束目前的範圍，這可以是函式、指令碼或指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="66484-106">Exits the current scope, which can be a function, script, or script block.</span></span>

## <a name="long-description"></a><span data-ttu-id="66484-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="66484-107">Long description</span></span>

<span data-ttu-id="66484-108">關鍵字會結束函式 `return` 、腳本或腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="66484-108">The `return` keyword exits a function, script, or script block.</span></span> <span data-ttu-id="66484-109">您可以使用它來結束特定點的範圍、傳回值，或指出已到達範圍的結尾。</span><span class="sxs-lookup"><span data-stu-id="66484-109">It can be used to exit a scope at a specific point, to return a value, or to indicate that the end of the scope has been reached.</span></span>

<span data-ttu-id="66484-110">熟悉 C 或 C 等語言的使用者， \# 可能會想要使用 `return` 關鍵字來讓範圍保持明確的邏輯。</span><span class="sxs-lookup"><span data-stu-id="66484-110">Users who are familiar with languages like C or C\# might want to use the `return` keyword to make the logic of leaving a scope explicit.</span></span>

<span data-ttu-id="66484-111">在 PowerShell 中，每個語句的結果都會以輸出的形式傳回，即使沒有包含 Return 關鍵字的語句也是一樣。</span><span class="sxs-lookup"><span data-stu-id="66484-111">In PowerShell, the results of each statement are returned as output, even without a statement that contains the Return keyword.</span></span> <span data-ttu-id="66484-112">C 或 C 之類的語言 \# 只會傳回關鍵字所指定的值或值 `return` 。</span><span class="sxs-lookup"><span data-stu-id="66484-112">Languages like C or C\# return only the value or values that are specified by the `return` keyword.</span></span>

> [!NOTE]
> <span data-ttu-id="66484-113">從 PowerShell 5.0 開始，PowerShell 使用正式語法來新增定義類別的語言。</span><span class="sxs-lookup"><span data-stu-id="66484-113">Beginning in PowerShell 5.0, PowerShell added language for defining classes, by using formal syntax.</span></span>  <span data-ttu-id="66484-114">在 PowerShell 類別的內容中，不會有任何來自方法的輸出，除了您使用語句指定的內容之外 `return` 。</span><span class="sxs-lookup"><span data-stu-id="66484-114">In the context of a PowerShell class, nothing is output from a method except what you specify using a `return` statement.</span></span> <span data-ttu-id="66484-115">您可以在 [about_Classes](about_Classes.md)中深入瞭解 PowerShell 類別。</span><span class="sxs-lookup"><span data-stu-id="66484-115">You can read more about PowerShell classes in [about_Classes](about_Classes.md).</span></span>

### <a name="syntax"></a><span data-ttu-id="66484-116">Syntax</span><span class="sxs-lookup"><span data-stu-id="66484-116">Syntax</span></span>

<span data-ttu-id="66484-117">關鍵字的語法如下所示 `return` ：</span><span class="sxs-lookup"><span data-stu-id="66484-117">The syntax for the `return` keyword is as follows:</span></span>

```
return [<expression>]
```

<span data-ttu-id="66484-118">`return`關鍵字可以單獨出現，也可以其後接著值或運算式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="66484-118">The `return` keyword can appear alone, or it can be followed by a value or expression, as follows:</span></span>

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a><span data-ttu-id="66484-119">範例</span><span class="sxs-lookup"><span data-stu-id="66484-119">Examples</span></span>

<span data-ttu-id="66484-120">下列範例 `return` 會在符合條件時，使用關鍵字來結束特定點的函式。</span><span class="sxs-lookup"><span data-stu-id="66484-120">The following example uses the `return` keyword to exit a function at a specific point if a conditional is met.</span></span> <span data-ttu-id="66484-121">奇數數位不會相乘，因為 return 語句會在語句執行之前結束。</span><span class="sxs-lookup"><span data-stu-id="66484-121">Odd numbers are not multiplied because the return statement exits before that statement can execute.</span></span>

```powershell
function MultiplyEven
{
    param($number)

    if ($number % 2) { return "$number is not even" }
    $number * 2
}

1..10 | ForEach-Object {MultiplyEven -Number $_}
```

```output
1 is not even
4
3 is not even
8
5 is not even
12
7 is not even
16
9 is not even
20
```

<span data-ttu-id="66484-122">在 PowerShell 中，即使未使用關鍵字，也可以傳回值 `return` 。</span><span class="sxs-lookup"><span data-stu-id="66484-122">In PowerShell, values can be returned even if the `return` keyword is not used.</span></span>
<span data-ttu-id="66484-123">會傳回每個語句的結果。</span><span class="sxs-lookup"><span data-stu-id="66484-123">The results of each statement are returned.</span></span> <span data-ttu-id="66484-124">例如，下列語句會傳回變數的值 `$a` ：</span><span class="sxs-lookup"><span data-stu-id="66484-124">For example, the following statements return the value of the `$a` variable:</span></span>

```powershell
$a
return
```

<span data-ttu-id="66484-125">下列語句也會傳回的值 `$a` ：</span><span class="sxs-lookup"><span data-stu-id="66484-125">The following statement also returns the value of `$a`:</span></span>

```powershell
return $a
```

<span data-ttu-id="66484-126">下列範例包含一個語句，其目的是要讓使用者知道函式正在執行計算：</span><span class="sxs-lookup"><span data-stu-id="66484-126">The following example includes a statement intended to let the user know that the function is performing a calculation:</span></span>

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

<span data-ttu-id="66484-127">「請稍候。</span><span class="sxs-lookup"><span data-stu-id="66484-127">The "Please wait.</span></span> <span data-ttu-id="66484-128">正在處理計算 ...」不顯示字串。</span><span class="sxs-lookup"><span data-stu-id="66484-128">Working on calculation..." string is not displayed.</span></span> <span data-ttu-id="66484-129">相反地，它會指派給 `$a` 變數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="66484-129">Instead, it is assigned to the `$a` variable, as in the following example:</span></span>

```
PS> $a
Please wait. Working on calculation...
87
```

<span data-ttu-id="66484-130">參考字串和計算結果都是由函式傳回並指派給 `$a` 變數。</span><span class="sxs-lookup"><span data-stu-id="66484-130">Both the informational string and the result of the calculation are returned by the function and assigned to the `$a` variable.</span></span>

<span data-ttu-id="66484-131">如果您想要在函式內顯示訊息，從 PowerShell 5.0 開始，您可以使用此 `Information` 資料流程。</span><span class="sxs-lookup"><span data-stu-id="66484-131">If you would like to display a message within your function, beginning in PowerShell 5.0, you can use the `Information` stream.</span></span> <span data-ttu-id="66484-132">下列程式碼會使用 `Write-Information` Cmdlet 搭配 `InformationAction` **Continue** 來修正上述範例。</span><span class="sxs-lookup"><span data-stu-id="66484-132">The code below corrects the above example using the `Write-Information` cmdlet with a `InformationAction` of **Continue** .</span></span>

```powershell
function calculation {
    param ($value)

    Write-Information "Please wait. Working on calculation..." -InformationAction Continue
    $value += 73
    return $value
}

$a = calculation 14
```

```output
Please wait. Working on calculation...
C:\PS> $a
87
```

### <a name="return-values-and-the-pipeline"></a><span data-ttu-id="66484-133">傳回值和管線</span><span class="sxs-lookup"><span data-stu-id="66484-133">Return values and the Pipeline</span></span>

<span data-ttu-id="66484-134">當您從腳本區塊或函式傳回集合時，PowerShell 會自動展開成員，並透過管線一次傳遞一個。</span><span class="sxs-lookup"><span data-stu-id="66484-134">When you return a collection from your script block or function, PowerShell automatically unrolls the members and passes them one at a time through the pipeline.</span></span> <span data-ttu-id="66484-135">這是因為 PowerShell 的一次性處理。</span><span class="sxs-lookup"><span data-stu-id="66484-135">This is due to PowerShell's one-at-a-time processing.</span></span> <span data-ttu-id="66484-136">如需詳細資訊，請參閱 [about_pipelines](about_pipelines.md)。</span><span class="sxs-lookup"><span data-stu-id="66484-136">For more information, see [about_pipelines](about_pipelines.md).</span></span>

<span data-ttu-id="66484-137">下列會傳回數位陣列的範例函式說明這個概念。</span><span class="sxs-lookup"><span data-stu-id="66484-137">This concept is illustrated by the following sample function that returns an array of numbers.</span></span> <span data-ttu-id="66484-138">函式的輸出會以管道傳送至 `Measure-Object` Cmdlet，以計算管線中的物件數目。</span><span class="sxs-lookup"><span data-stu-id="66484-138">The output from the function is piped to the `Measure-Object` cmdlet which counts the number of objects in the pipeline.</span></span>

```powershell
function Test-Return
{
    $array = 1,2,3
    return $array
}
Test-Return | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

<span data-ttu-id="66484-139">若要強制腳本區塊或函數將集合以單一物件的形式傳回至管線，請使用下列兩種方法之一：</span><span class="sxs-lookup"><span data-stu-id="66484-139">To force a script block or function to return collection as a single object to the pipeline, use one of the following two methods:</span></span>

- <span data-ttu-id="66484-140">一元陣列運算式</span><span class="sxs-lookup"><span data-stu-id="66484-140">Unary array expression</span></span>

  <span data-ttu-id="66484-141">利用一元運算式，您可以將管線的傳回值以單一物件的形式傳送，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="66484-141">Utilizing a unary expression you can send your return value down the pipeline as a single object as illustrated by the following example.</span></span>

  ```powershell
  function Test-Return
  {
      $array = 1,2,3
      return (, $array)
  }
  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

- <span data-ttu-id="66484-142">`Write-Output` with **NoEnumerate** 參數。</span><span class="sxs-lookup"><span data-stu-id="66484-142">`Write-Output` with **NoEnumerate** parameter.</span></span>

  <span data-ttu-id="66484-143">您也可以使用 `Write-Output` Cmdlet 搭配 **NoEnumerate** 參數。</span><span class="sxs-lookup"><span data-stu-id="66484-143">You can also use the `Write-Output` cmdlet with the **NoEnumerate** parameter.</span></span> <span data-ttu-id="66484-144">下列範例會使用 `Measure-Object` Cmdlet 來計算從範例函式依關鍵字傳送至管線的物件 `return` 。</span><span class="sxs-lookup"><span data-stu-id="66484-144">The example below uses the `Measure-Object` cmdlet to count the objects sent to the pipeline from the sample function by the `return` keyword.</span></span>

  ```powershell
  function Test-Return
  {
      $array = 1, 2, 3
      return Write-Output -NoEnumerate $array
  }

  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

## <a name="see-also"></a><span data-ttu-id="66484-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66484-145">See also</span></span>

[<span data-ttu-id="66484-146">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="66484-146">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="66484-147">about_Functions</span><span class="sxs-lookup"><span data-stu-id="66484-147">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="66484-148">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="66484-148">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="66484-149">about_Classes</span><span class="sxs-lookup"><span data-stu-id="66484-149">about_Classes</span></span>](about_Classes.md)

[<span data-ttu-id="66484-150">Write-Information</span><span class="sxs-lookup"><span data-stu-id="66484-150">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)

[<span data-ttu-id="66484-151">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="66484-151">about_Script_Blocks</span></span>](about_Script_Blocks.md)
