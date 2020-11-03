---
description: 描述如何建立和使用參考型別變數。 您可以使用參考型別變數來允許函數變更傳遞給它的變數值。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/24/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_ref?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Ref
ms.openlocfilehash: 3d1ae1fd53e7b4e845c8df76e1826c45b32c9c72
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207588"
---
# <a name="about-ref"></a><span data-ttu-id="e1d24-105">關於參考</span><span class="sxs-lookup"><span data-stu-id="e1d24-105">About Ref</span></span>

## <a name="short-description"></a><span data-ttu-id="e1d24-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="e1d24-106">Short description</span></span>

<span data-ttu-id="e1d24-107">描述如何建立和使用參考型別變數。</span><span class="sxs-lookup"><span data-stu-id="e1d24-107">Describes how to create and use a reference type variable.</span></span> <span data-ttu-id="e1d24-108">您可以使用參考型別變數來允許函數變更傳遞給它的變數值。</span><span class="sxs-lookup"><span data-stu-id="e1d24-108">You can use reference type variables to permit a function to change the value of a variable that is passed to it.</span></span>

## <a name="long-description"></a><span data-ttu-id="e1d24-109">完整描述</span><span class="sxs-lookup"><span data-stu-id="e1d24-109">Long description</span></span>

<span data-ttu-id="e1d24-110">您可以透過傳 *址方式* 或 *依值* 傳遞變數給函數。</span><span class="sxs-lookup"><span data-stu-id="e1d24-110">You can pass variables to functions *by reference* or *by value* .</span></span>

<span data-ttu-id="e1d24-111">當您以傳 *值方式* 傳遞變數時，會傳遞資料的複本。</span><span class="sxs-lookup"><span data-stu-id="e1d24-111">When you pass a variable *by value* , you are passing a copy of the data.</span></span>

<span data-ttu-id="e1d24-112">在下列範例中，函數會變更傳遞給它的變數值。</span><span class="sxs-lookup"><span data-stu-id="e1d24-112">In the following example, the function changes the value of the variable passed to it.</span></span> <span data-ttu-id="e1d24-113">在 PowerShell 中，整數是實數值型別，因此會以傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="e1d24-113">In PowerShell, integers are value types so they are passed by value.</span></span>
<span data-ttu-id="e1d24-114">因此，的值會在函式的 `$var` 範圍之外保持不變。</span><span class="sxs-lookup"><span data-stu-id="e1d24-114">Therefore, the value of `$var` is unchanged outside the scope of the function.</span></span>

```powershell
Function Test($data)
{
    $data = 3
}

$var = 10
Test -data $var
$var
```

```output
10
```

<span data-ttu-id="e1d24-115">在下列範例中，會將包含的變數 `Hashtable` 傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="e1d24-115">In the following example, a variable containing a `Hashtable` is passed to a function.</span></span> <span data-ttu-id="e1d24-116">`Hashtable` 是物件類型，因此預設會以傳 *址方式* 傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="e1d24-116">`Hashtable` is an object type so by default it is passed to the function *by reference* .</span></span>

<span data-ttu-id="e1d24-117">*以傳址方式* 傳遞變數時，函式可以變更資料，而且在函式執行之後仍會保存變更。</span><span class="sxs-lookup"><span data-stu-id="e1d24-117">When passing a variable *by reference* , the function can change the data and that change persists after the function executes.</span></span>

```powershell
Function Test($data)
{
    $data.Test = "New Text"
}

$var = @{}
Test -data $var
$var
```

```output
Name                           Value
----                           -----
Test                           New Text
```

<span data-ttu-id="e1d24-118">函式會新增新的索引鍵/值組，以在函式的範圍之外保存。</span><span class="sxs-lookup"><span data-stu-id="e1d24-118">The function adds a new key-value pair that persists outside of the function's scope.</span></span>

### <a name="writing-functions-to-accept-reference-parameters"></a><span data-ttu-id="e1d24-119">撰寫函數以接受參考參數</span><span class="sxs-lookup"><span data-stu-id="e1d24-119">Writing functions to accept reference parameters</span></span>

<span data-ttu-id="e1d24-120">無論傳遞的資料類型為何，您都可以撰寫函數的程式碼，以取得參數作為參考。</span><span class="sxs-lookup"><span data-stu-id="e1d24-120">You can code your functions to take a parameter as a reference, regardless of the type of data passed.</span></span> <span data-ttu-id="e1d24-121">這需要您將參數類型指定為 `System.Management.Automation.PSReference` 或 `[ref]` 。</span><span class="sxs-lookup"><span data-stu-id="e1d24-121">This requires that you specify the parameters type as `System.Management.Automation.PSReference`, or `[ref]`.</span></span>

<span data-ttu-id="e1d24-122">使用參考時，您必須使用 `Value` 型別的屬性 `System.Management.Automation.PSReference` 來存取您的資料。</span><span class="sxs-lookup"><span data-stu-id="e1d24-122">When using references, you must use the `Value` property of the `System.Management.Automation.PSReference` type to access your data.</span></span>

```powershell
Function Test([ref]$data)
{
    $data.Value = 3
}
```

<span data-ttu-id="e1d24-123">若要將變數傳遞給需要參考的參數，您必須輸入將變數轉換為參考。</span><span class="sxs-lookup"><span data-stu-id="e1d24-123">To pass a variable to a parameter that expects a reference, you must type cast your variable as a reference.</span></span>

> [!NOTE]
> <span data-ttu-id="e1d24-124">括弧和括弧都是必要的。</span><span class="sxs-lookup"><span data-stu-id="e1d24-124">The brackets and parenthesis are BOTH required.</span></span>

```powershell
$var = 10
Test -data ([ref]$var)
$var
```

```output
3
```

### <a name="passing-references-to-net-methods"></a><span data-ttu-id="e1d24-125">傳遞 .NET 方法的參考</span><span class="sxs-lookup"><span data-stu-id="e1d24-125">Passing references to .NET methods</span></span>

<span data-ttu-id="e1d24-126">某些 .NET 方法可能會要求您傳遞變數作為參考。</span><span class="sxs-lookup"><span data-stu-id="e1d24-126">Some .NET methods may require you to pass a variable as a reference.</span></span> <span data-ttu-id="e1d24-127">當方法的定義在 `in` 參數上使用關鍵字、或時， `out` `ref` 它需要參考。</span><span class="sxs-lookup"><span data-stu-id="e1d24-127">When the method's definition uses the keywords `in`, `out`, or `ref` on a parameter, it expects a reference.</span></span>

```powershell
[int] | Get-Member -Static -Name TryParse
```

```output
Name     MemberType Definition
----     ---------- ----------
TryParse Method     static bool TryParse(string s, [ref] int result)
```

<span data-ttu-id="e1d24-128">`TryParse`方法會嘗試將字串剖析為整數。</span><span class="sxs-lookup"><span data-stu-id="e1d24-128">The `TryParse` method attempts to parse a string as an integer.</span></span> <span data-ttu-id="e1d24-129">如果方法成功，它會傳回 `$true` ，而且結果會儲存在您以傳 **址方式** 傳遞的變數中。</span><span class="sxs-lookup"><span data-stu-id="e1d24-129">If the method succeeds, it returns `$true`, and the result is stored in the variable you passed **by reference** .</span></span>

```
PS> $number = 0
PS> [int]::TryParse("15", ([ref]$number))
True
PS> $number
15
```

### <a name="references-and-scopes"></a><span data-ttu-id="e1d24-130">參考和範圍</span><span class="sxs-lookup"><span data-stu-id="e1d24-130">References and scopes</span></span>

<span data-ttu-id="e1d24-131">參考允許父範圍中的變數值在子範圍內變更。</span><span class="sxs-lookup"><span data-stu-id="e1d24-131">References allow the value of a variable in the parent scope to be changed within a child scope.</span></span>

```powershell
# Create a value type variable.
$i = 0
# Create a reference type variable.
$iRef = [ref]0
# Invoke a scriptblock to attempt to change both values.
&{$i++;$iRef.Value++}
# Output the results.
"`$i = $i;`$iRef = $($iRef.Value)"
```

```output
$i = 0;$iRef = 1
```

<span data-ttu-id="e1d24-132">只有參考型別的變數已變更。</span><span class="sxs-lookup"><span data-stu-id="e1d24-132">Only the reference type's variable was changed.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1d24-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1d24-133">See also</span></span>

[<span data-ttu-id="e1d24-134">about_Variables</span><span class="sxs-lookup"><span data-stu-id="e1d24-134">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="e1d24-135">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="e1d24-135">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="e1d24-136">about_Functions</span><span class="sxs-lookup"><span data-stu-id="e1d24-136">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="e1d24-137">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="e1d24-137">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="e1d24-138">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="e1d24-138">about_Scopes</span></span>](about_scopes.md)
