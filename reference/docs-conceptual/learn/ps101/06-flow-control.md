---
title: 流量控制
description: PowerShell 提供方法來建立迴圈、進行決策，並以邏輯方式控制指令碼中的程式碼流程。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4f0d7b7f5f3c12bb9475af5aed42b2d32cfbc14d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437989"
---
# <a name="chapter-6---flow-control"></a><span data-ttu-id="d092f-103">第 6 章 - 流程控制</span><span class="sxs-lookup"><span data-stu-id="d092f-103">Chapter 6 - Flow control</span></span>

## <a name="scripting"></a><span data-ttu-id="d092f-104">指令碼</span><span class="sxs-lookup"><span data-stu-id="d092f-104">Scripting</span></span>

<span data-ttu-id="d092f-105">從撰寫 PowerShell 單行程式碼轉換到撰寫指令碼時，聽起來很複雜，實際上卻不然。</span><span class="sxs-lookup"><span data-stu-id="d092f-105">When you move from writing PowerShell one-liners to writing scripts, it sounds a lot more complicated than it really is.</span></span> <span data-ttu-id="d092f-106">指令碼只是您會在 PowerShell 主控台中以互動方式執行的相同或類似命令，不同的是，系統會將其儲存為 `.PS1` 檔案。</span><span class="sxs-lookup"><span data-stu-id="d092f-106">A script is nothing more than the same or similar commands that you would run interactively in the PowerShell console, except they're saved as a `.PS1` file.</span></span> <span data-ttu-id="d092f-107">有一些指令碼建構可供您使用，例如 `foreach` 迴圈，而不是 `ForEach-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d092f-107">There are some scripting constructs that you may use such as a `foreach` loop instead of the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="d092f-108">對於初學者來說，當您認為 `foreach` 同時是指令碼建構和 `ForEach-Object` Cmdlet 的別名時，這些差異可能會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="d092f-108">To beginners, the differences can be confusing especially when you consider that `foreach` is both a scripting construct and an alias for the `ForEach-Object` cmdlet.</span></span>

## <a name="looping"></a><span data-ttu-id="d092f-109">迴圈</span><span class="sxs-lookup"><span data-stu-id="d092f-109">Looping</span></span>

<span data-ttu-id="d092f-110">PowerShell 的其中一個絕佳功能就是，一旦您了解如何對某個項目執行一些動作，就幾乎可以針對數百個項目執行相同動作。</span><span class="sxs-lookup"><span data-stu-id="d092f-110">One of the great things about PowerShell is, once you figure out how to do something for one item, it's almost as easy to do the same task for hundreds of items.</span></span> <span data-ttu-id="d092f-111">只要使用 PowerShell 中許多不同類型的迴圈中的其中一個，就能對項目重複執行。</span><span class="sxs-lookup"><span data-stu-id="d092f-111">Simply loop through the items using one of the many different types of loops in PowerShell.</span></span>

### <a name="foreach-object"></a><span data-ttu-id="d092f-112">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="d092f-112">ForEach-Object</span></span>

<span data-ttu-id="d092f-113">`ForEach-Object` 是用來逐一查看管線中項目 (例如使用 PowerShell 單行程式碼) 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d092f-113">`ForEach-Object` is a cmdlet for iterating through items in a pipeline such as with PowerShell one-liners.</span></span> <span data-ttu-id="d092f-114">`ForEach-Object` 會透過管線串流物件。</span><span class="sxs-lookup"><span data-stu-id="d092f-114">`ForEach-Object` streams the objects through the pipeline.</span></span>

<span data-ttu-id="d092f-115">雖然 `Get-Command` 的 **Module** 參數會接受多個字串值，但只會透過屬性名稱的管線輸入或透過參數輸入接受它們。</span><span class="sxs-lookup"><span data-stu-id="d092f-115">Although the **Module** parameter of `Get-Command` accepts multiple values that are strings, it only accepts them via pipeline input by property name or via parameter input.</span></span> <span data-ttu-id="d092f-116">在下列案例中，如果我想要以 by value 值方式將兩個字串以管線傳送至 `Get-Command`，以便與 **Module** 參數搭配使用，我就必須使用 `ForEach-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d092f-116">In the following scenario, if I want to pipe two strings by value to `Get-Command` for use with the **Module** parameter, I would need to use the `ForEach-Object` cmdlet.</span></span>

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

<span data-ttu-id="d092f-117">在上述範例中，`$_` 是目前的物件。</span><span class="sxs-lookup"><span data-stu-id="d092f-117">In the previous example, `$_` is the current object.</span></span> <span data-ttu-id="d092f-118">從 PowerShell 3.0 版開始，您可以使用 `$PSItem`，而不是 `$_`。</span><span class="sxs-lookup"><span data-stu-id="d092f-118">Beginning with PowerShell version 3.0, `$PSItem` can be used instead of `$_`.</span></span> <span data-ttu-id="d092f-119">但我發現，大部分經驗豐富的 PowerShell 使用者仍然偏好使用 `$_`，因為它具回溯相容且要輸入的字較少。</span><span class="sxs-lookup"><span data-stu-id="d092f-119">But I find that most experienced PowerShell users still prefer using `$_` since it's backward compatible and less to type.</span></span>

<span data-ttu-id="d092f-120">使用 `foreach` 關鍵字時，您必須先將所有項目儲存在記憶體中，然後再逐一查看，如果您不知道要處理多少個項目，則這可能會很棘手。</span><span class="sxs-lookup"><span data-stu-id="d092f-120">When using the `foreach` keyword, you must store all of the items in memory before iterating through them, which could be difficult if you don't know how many items you're working with.</span></span>

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="d092f-121">許多時候，`foreach` 或 `ForEach-Object` 之類的迴圈都是必要的。</span><span class="sxs-lookup"><span data-stu-id="d092f-121">Many times a loop such as `foreach` or `ForEach-Object` is necessary.</span></span> <span data-ttu-id="d092f-122">否則，您會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="d092f-122">Otherwise you'll receive an error message.</span></span>

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

<span data-ttu-id="d092f-123">其他時候，您可以取得相同的結果，同時將迴圈完全消除。</span><span class="sxs-lookup"><span data-stu-id="d092f-123">Other times, you can get the same results while eliminating the loop altogether.</span></span> <span data-ttu-id="d092f-124">請參閱 Cmdlet 說明以了解您的選項。</span><span class="sxs-lookup"><span data-stu-id="d092f-124">Consult the cmdlet help to understand your options.</span></span>

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="d092f-125">如您在先前的範例中所見，`Get-ADComputer` 的 **Identity** 參數只會在透過參數輸入提供時接受單一值，但在透過管線輸入提供輸入時，則會允許多個項目。</span><span class="sxs-lookup"><span data-stu-id="d092f-125">As you can see in the previous examples, the **Identity** parameter for `Get-ADComputer` only accepts a single value when provided via parameter input, but it allows for multiple items when the input is provided via pipeline input.</span></span>

### <a name="for"></a><span data-ttu-id="d092f-126">For</span><span class="sxs-lookup"><span data-stu-id="d092f-126">For</span></span>

<span data-ttu-id="d092f-127">當指定的條件為 true 時，`for` 迴圈會逐一查看。</span><span class="sxs-lookup"><span data-stu-id="d092f-127">A `for` loop iterates while a specified condition is true.</span></span> <span data-ttu-id="d092f-128">`for` 迴圈不是我經常使用的項目，但它有其用途。</span><span class="sxs-lookup"><span data-stu-id="d092f-128">The `for` loop is not something that I use often, but it does have its uses.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

<span data-ttu-id="d092f-129">在上述範例中，迴圈會逐一查看四次，從數字一開始，且只要計數器變數 `$i` 小於 5，就會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="d092f-129">In the previous example, the loop will iterate four times by starting off with the number one and continue as long as the counter variable `$i` is less than 5.</span></span> <span data-ttu-id="d092f-130">它總計會睡眠 10 秒。</span><span class="sxs-lookup"><span data-stu-id="d092f-130">It will sleep for a total of 10 seconds.</span></span>

### <a name="do"></a><span data-ttu-id="d092f-131">要做的事</span><span class="sxs-lookup"><span data-stu-id="d092f-131">Do</span></span>

<span data-ttu-id="d092f-132">PowerShell 中有兩個不同的 `do` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="d092f-132">There are two different `do` loops in PowerShell.</span></span> <span data-ttu-id="d092f-133">`Do Until` 會在指定的條件為 false 時執行。</span><span class="sxs-lookup"><span data-stu-id="d092f-133">`Do Until` runs while the specified condition is false.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

<span data-ttu-id="d092f-134">先前的範例是數字遊戲，會繼續進行，直到您猜測的值等於 `Get-Random` Cmdlet 產生的相同數字。</span><span class="sxs-lookup"><span data-stu-id="d092f-134">The previous example is a numbers game that continues until the value you guess equals the same number that the `Get-Random` cmdlet generated.</span></span>

<span data-ttu-id="d092f-135">`Do While` 就正好相反。</span><span class="sxs-lookup"><span data-stu-id="d092f-135">`Do While` is just the opposite.</span></span> <span data-ttu-id="d092f-136">只要指定的條件評估為 true，它就會執行。</span><span class="sxs-lookup"><span data-stu-id="d092f-136">It runs as long as the specified condition evaluates to true.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

<span data-ttu-id="d092f-137">藉由將測試條件反轉為不等於，使用 `Do While` 迴圈即可達成相同的結果。</span><span class="sxs-lookup"><span data-stu-id="d092f-137">The same results are achieved with a `Do While` loop by reversing the test condition to not equals.</span></span>

<span data-ttu-id="d092f-138">`Do` 迴圈一律會至少執行一次，因為會在迴圈結尾評估條件。</span><span class="sxs-lookup"><span data-stu-id="d092f-138">`Do` loops always run at least once because the condition is evaluated at the end of the loop.</span></span>

### <a name="while"></a><span data-ttu-id="d092f-139">While</span><span class="sxs-lookup"><span data-stu-id="d092f-139">While</span></span>

<span data-ttu-id="d092f-140">與 `Do While` 迴圈類似，只要指定的條件為 true，`While` 迴圈就會執行。</span><span class="sxs-lookup"><span data-stu-id="d092f-140">Similar to the `Do While` loop, a `While` loop runs as long as the specified condition is true.</span></span> <span data-ttu-id="d092f-141">但差異在於，`While` 迴圈會在執行任何程式碼之前，在迴圈頂端評估條件。</span><span class="sxs-lookup"><span data-stu-id="d092f-141">The difference however, is that a `While` loop evaluates the condition at the top of the loop before any code is run.</span></span> <span data-ttu-id="d092f-142">因此，如果條件評估為 false，則不會執行。</span><span class="sxs-lookup"><span data-stu-id="d092f-142">So it doesn't run if the condition evaluates to false.</span></span>

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

<span data-ttu-id="d092f-143">上一個範例會計算在美國的感恩節是在哪一天。</span><span class="sxs-lookup"><span data-stu-id="d092f-143">The previous example calculates what day Thanksgiving Day is on in the United States.</span></span> <span data-ttu-id="d092f-144">它一律是在 11 月的第四個星期四。</span><span class="sxs-lookup"><span data-stu-id="d092f-144">It's always on the fourth Thursday of November.</span></span> <span data-ttu-id="d092f-145">如此一來，迴圈就會從 11 月 22 日開始，並在星期幾不等於星期四時加一天。</span><span class="sxs-lookup"><span data-stu-id="d092f-145">So the loop starts with the 22nd day of November and adds a day while the day of the week isn't equal to Thursday.</span></span> <span data-ttu-id="d092f-146">如果 22 日為星期四，則完全不會執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="d092f-146">If the 22nd is a Thursday, the loop doesn't run at all.</span></span>

## <a name="break-continue-and-return"></a><span data-ttu-id="d092f-147">Break、Continue 和 Return</span><span class="sxs-lookup"><span data-stu-id="d092f-147">Break, Continue, and Return</span></span>

<span data-ttu-id="d092f-148">`Break` 的設計目的是要中斷迴圈。</span><span class="sxs-lookup"><span data-stu-id="d092f-148">`Break` is designed to break out of a loop.</span></span> <span data-ttu-id="d092f-149">它通常也會與 `switch` 陳述式搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d092f-149">It's also commonly used with the `switch` statement.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

<span data-ttu-id="d092f-150">上一個範例中所示的 `break` 陳述式會導致迴圈在第一次反覆項目時結束。</span><span class="sxs-lookup"><span data-stu-id="d092f-150">The `break` statement shown in the previous example causes the loop to exit on the first iteration.</span></span>

<span data-ttu-id="d092f-151">Continue 的設計則是要跳到迴圈的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="d092f-151">Continue is designed to skip to the next iteration of a loop.</span></span>

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

<span data-ttu-id="d092f-152">上一個範例會輸出數字 1、2、4 和 5。</span><span class="sxs-lookup"><span data-stu-id="d092f-152">The previous example will output the numbers 1, 2, 4, and 5.</span></span> <span data-ttu-id="d092f-153">它會略過數字 3，並繼續進行迴圈的下一個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="d092f-153">It skips number 3 and continues with the next iteration of the loop.</span></span> <span data-ttu-id="d092f-154">類似於 `break`，`continue` 會中斷迴圈，但目前的反覆項目除外。</span><span class="sxs-lookup"><span data-stu-id="d092f-154">Similar to `break`, `continue` breaks out of the loop except only for the current iteration.</span></span> <span data-ttu-id="d092f-155">執行會繼續進行下一個反覆項目，而不是中斷迴圈並停止。</span><span class="sxs-lookup"><span data-stu-id="d092f-155">Execution continues with the next iteration instead of breaking out of the loop and stopping.</span></span>

<span data-ttu-id="d092f-156">Return 的設計目的是要結束現有的範圍。</span><span class="sxs-lookup"><span data-stu-id="d092f-156">Return is designed to exit out of the existing scope.</span></span>

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

<span data-ttu-id="d092f-157">請注意，在上述範例中，Return 會輸出第一個結果，然後從迴圈結束。</span><span class="sxs-lookup"><span data-stu-id="d092f-157">Notice that in the previous example, return outputs the first result and then exists out of the loop.</span></span> <span data-ttu-id="d092f-158">如需更完整結果陳述式的說明，請參閱我的其中一個部落格文章：[「PowerShell Return 關鍵字」][]。</span><span class="sxs-lookup"><span data-stu-id="d092f-158">A more thorough explanation of the result statement can be found in one of my blog articles: ["The PowerShell return keyword"][].</span></span>

## <a name="summary"></a><span data-ttu-id="d092f-159">摘要</span><span class="sxs-lookup"><span data-stu-id="d092f-159">Summary</span></span>

<span data-ttu-id="d092f-160">在本章中，您已了解 PowerShell 中存在的不同類型迴圈。</span><span class="sxs-lookup"><span data-stu-id="d092f-160">In this chapter, you've learned about the different types of loops that exist in PowerShell.</span></span>

## <a name="review"></a><span data-ttu-id="d092f-161">檢閱</span><span class="sxs-lookup"><span data-stu-id="d092f-161">Review</span></span>

1. <span data-ttu-id="d092f-162">`ForEach-Object` Cmdlet 與 foreach 指令碼建構中有何差異？</span><span class="sxs-lookup"><span data-stu-id="d092f-162">What is the difference in the `ForEach-Object` cmdlet and the foreach scripting construct?</span></span>
1. <span data-ttu-id="d092f-163">使用 While 迴圈而不是 Do While 或 Do Until 迴圈的主要優點為何？</span><span class="sxs-lookup"><span data-stu-id="d092f-163">What is the primary advantage of using a While loop instead of a Do While or Do Until loop.</span></span>
1. <span data-ttu-id="d092f-164">Break 和 Continue 陳述式有何不同？</span><span class="sxs-lookup"><span data-stu-id="d092f-164">How do the break and continue statements differ?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="d092f-165">建議閱讀資料</span><span class="sxs-lookup"><span data-stu-id="d092f-165">Recommended Reading</span></span>

- <span data-ttu-id="d092f-166">[ForEach-Object][]</span><span class="sxs-lookup"><span data-stu-id="d092f-166">[ForEach-Object][]</span></span>
- <span data-ttu-id="d092f-167">[about_ForEach][]</span><span class="sxs-lookup"><span data-stu-id="d092f-167">[about_ForEach][]</span></span>
- <span data-ttu-id="d092f-168">[about_For][]</span><span class="sxs-lookup"><span data-stu-id="d092f-168">[about_For][]</span></span>
- <span data-ttu-id="d092f-169">[about_Do][]</span><span class="sxs-lookup"><span data-stu-id="d092f-169">[about_Do][]</span></span>
- <span data-ttu-id="d092f-170">[about_While][]</span><span class="sxs-lookup"><span data-stu-id="d092f-170">[about_While][]</span></span>
- <span data-ttu-id="d092f-171">[about_Break][]</span><span class="sxs-lookup"><span data-stu-id="d092f-171">[about_Break][]</span></span>
- <span data-ttu-id="d092f-172">[about_Continue][]</span><span class="sxs-lookup"><span data-stu-id="d092f-172">[about_Continue][]</span></span>
- <span data-ttu-id="d092f-173">[about_Return][]</span><span class="sxs-lookup"><span data-stu-id="d092f-173">[about_Return][]</span></span>

<!-- link references -->
[ForEach-Object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
[「PowerShell Return 關鍵字」]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
["The PowerShell return keyword"]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
