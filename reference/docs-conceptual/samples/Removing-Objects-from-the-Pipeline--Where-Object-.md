---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 從管線中移除物件 Where Object
description: Where-Object Cmdlet 可讓您篩選在管線上傳遞的物件。
ms.openlocfilehash: e744dc671303711f1cbe8cc724a97c3327c1da85
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500108"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="715fb-104">從管線中移除物件 (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="715fb-104">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="715fb-105">在 PowerShell 中，您通常會產生並沿著管線傳遞比所需更多的物件。</span><span class="sxs-lookup"><span data-stu-id="715fb-105">In PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="715fb-106">您可以使用 `Format-*` Cmdlet 來指定要顯示的特定物件屬性，但這樣做並無法解決從顯示中移除整個物件的問題。</span><span class="sxs-lookup"><span data-stu-id="715fb-106">You can specify the properties of particular objects to display by using the `Format-*` cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="715fb-107">您可能需要在結束管線之前篩選物件，以便只對初始產生的物件子集執行動作。</span><span class="sxs-lookup"><span data-stu-id="715fb-107">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="715fb-108">PowerShell 包含了 `Where-Object` Cmdlet，可讓您測試管線中的每個物件，並只在符合特定測試條件時才沿著管線傳遞。</span><span class="sxs-lookup"><span data-stu-id="715fb-108">PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="715fb-109">未通過測試的物件會從管線中移除。</span><span class="sxs-lookup"><span data-stu-id="715fb-109">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="715fb-110">您需提供測試條件作為 **FilterScript** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="715fb-110">You supply the test condition as the value of the **FilterScript** parameter.</span></span>

## <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="715fb-111">使用 Where-Object 執行簡單的測試</span><span class="sxs-lookup"><span data-stu-id="715fb-111">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="715fb-112"> (以大括弧 `{}` 括住的一或多個 PowerShell 命令)。</span><span class="sxs-lookup"><span data-stu-id="715fb-112">The value of **FilterScript** is a *script block* - one or more PowerShell commands surrounded by braces (`{}`) - that evaluates to true or false.</span></span> <span data-ttu-id="715fb-113">這些指令碼區塊可以很簡單，但若要建立它們，需要了解另一個 PowerShell 概念：比較運算子。</span><span class="sxs-lookup"><span data-stu-id="715fb-113">These script blocks can be very simple, but creating them requires knowing about another PowerShell concept, comparison operators.</span></span> <span data-ttu-id="715fb-114">比較運算子會比較出現在運算子兩側的項目。</span><span class="sxs-lookup"><span data-stu-id="715fb-114">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="715fb-115">比較運算子是以連字號字元 (`-`) 開頭，後面接著名稱。</span><span class="sxs-lookup"><span data-stu-id="715fb-115">Comparison operators begin with a hyphen character (`-`) and are followed by a name.</span></span> <span data-ttu-id="715fb-116">基本比較運算子適用於幾乎任何類型的物件。</span><span class="sxs-lookup"><span data-stu-id="715fb-116">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="715fb-117">更進階的比較運算子只適用於文字或陣列。</span><span class="sxs-lookup"><span data-stu-id="715fb-117">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="715fb-118">根據預設，搭配文字使用時，PowerShell 比較運算子不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="715fb-118">By default, when working with text, PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="715fb-119">基於剖析考量，不會使用 `<`、`>` 和 `=` 等符號作為比較運算子。</span><span class="sxs-lookup"><span data-stu-id="715fb-119">Due to parsing considerations, symbols such as `<`,`>`, and `=` are not used as comparison operators.</span></span> <span data-ttu-id="715fb-120">相反地，比較運算子是由字母所組成。</span><span class="sxs-lookup"><span data-stu-id="715fb-120">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="715fb-121">下表列出基本比較運算子。</span><span class="sxs-lookup"><span data-stu-id="715fb-121">The basic comparison operators are listed in the following table.</span></span>

| <span data-ttu-id="715fb-122">比較運算子</span><span class="sxs-lookup"><span data-stu-id="715fb-122">Comparison Operator</span></span> |                  <span data-ttu-id="715fb-123">意義</span><span class="sxs-lookup"><span data-stu-id="715fb-123">Meaning</span></span>                   |    <span data-ttu-id="715fb-124">範例 (傳回 true)</span><span class="sxs-lookup"><span data-stu-id="715fb-124">Example (returns true)</span></span>    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| <span data-ttu-id="715fb-125">-eq</span><span class="sxs-lookup"><span data-stu-id="715fb-125">-eq</span></span>                 | <span data-ttu-id="715fb-126">等於</span><span class="sxs-lookup"><span data-stu-id="715fb-126">is equal to</span></span>                                | <span data-ttu-id="715fb-127">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="715fb-127">1 -eq 1</span></span>                      |
| <span data-ttu-id="715fb-128">-ne</span><span class="sxs-lookup"><span data-stu-id="715fb-128">-ne</span></span>                 | <span data-ttu-id="715fb-129">不等於</span><span class="sxs-lookup"><span data-stu-id="715fb-129">Is not equal to</span></span>                            | <span data-ttu-id="715fb-130">1 -ne 2</span><span class="sxs-lookup"><span data-stu-id="715fb-130">1 -ne 2</span></span>                      |
| <span data-ttu-id="715fb-131">-lt</span><span class="sxs-lookup"><span data-stu-id="715fb-131">-lt</span></span>                 | <span data-ttu-id="715fb-132">小於</span><span class="sxs-lookup"><span data-stu-id="715fb-132">Is less than</span></span>                               | <span data-ttu-id="715fb-133">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="715fb-133">1 -lt 2</span></span>                      |
| <span data-ttu-id="715fb-134">-le</span><span class="sxs-lookup"><span data-stu-id="715fb-134">-le</span></span>                 | <span data-ttu-id="715fb-135">小於或等於</span><span class="sxs-lookup"><span data-stu-id="715fb-135">Is less than or equal to</span></span>                   | <span data-ttu-id="715fb-136">1 -le 2</span><span class="sxs-lookup"><span data-stu-id="715fb-136">1 -le 2</span></span>                      |
| <span data-ttu-id="715fb-137">-gt</span><span class="sxs-lookup"><span data-stu-id="715fb-137">-gt</span></span>                 | <span data-ttu-id="715fb-138">大於</span><span class="sxs-lookup"><span data-stu-id="715fb-138">Is greater than</span></span>                            | <span data-ttu-id="715fb-139">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="715fb-139">2 -gt 1</span></span>                      |
| <span data-ttu-id="715fb-140">-ge</span><span class="sxs-lookup"><span data-stu-id="715fb-140">-ge</span></span>                 | <span data-ttu-id="715fb-141">大於或等於</span><span class="sxs-lookup"><span data-stu-id="715fb-141">Is greater than or equal to</span></span>                | <span data-ttu-id="715fb-142">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="715fb-142">2 -ge 1</span></span>                      |
| <span data-ttu-id="715fb-143">-like</span><span class="sxs-lookup"><span data-stu-id="715fb-143">-like</span></span>               | <span data-ttu-id="715fb-144">像是 (文字的萬用字元比較)</span><span class="sxs-lookup"><span data-stu-id="715fb-144">Is like (wildcard comparison for text)</span></span>     | <span data-ttu-id="715fb-145">"file.doc" -like "f\*.do?"</span><span class="sxs-lookup"><span data-stu-id="715fb-145">"file.doc" -like "f\*.do?"</span></span>    |
| <span data-ttu-id="715fb-146">-notlike</span><span class="sxs-lookup"><span data-stu-id="715fb-146">-notlike</span></span>            | <span data-ttu-id="715fb-147">不像是 (文字的萬用字元比較)</span><span class="sxs-lookup"><span data-stu-id="715fb-147">Is not like (wildcard comparison for text)</span></span> | <span data-ttu-id="715fb-148">"file.doc" -notlike "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="715fb-148">"file.doc" -notlike "p\*.doc"</span></span> |
| <span data-ttu-id="715fb-149">-contains</span><span class="sxs-lookup"><span data-stu-id="715fb-149">-contains</span></span>           | <span data-ttu-id="715fb-150">包含</span><span class="sxs-lookup"><span data-stu-id="715fb-150">Contains</span></span>                                   | <span data-ttu-id="715fb-151">1,2,3 -contains 1</span><span class="sxs-lookup"><span data-stu-id="715fb-151">1,2,3 -contains 1</span></span>            |
| <span data-ttu-id="715fb-152">-notcontains</span><span class="sxs-lookup"><span data-stu-id="715fb-152">-notcontains</span></span>        | <span data-ttu-id="715fb-153">不包含</span><span class="sxs-lookup"><span data-stu-id="715fb-153">Does not contain</span></span>                           | <span data-ttu-id="715fb-154">1,2,3 -notcontains 4</span><span class="sxs-lookup"><span data-stu-id="715fb-154">1,2,3 -notcontains 4</span></span>         |

<span data-ttu-id="715fb-155">`Where-Object` 指令碼區塊使用特殊變數 `$_` 來參照管線中目前的物件。</span><span class="sxs-lookup"><span data-stu-id="715fb-155">`Where-Object` script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="715fb-156">以下示範其運作方式。</span><span class="sxs-lookup"><span data-stu-id="715fb-156">Here is an example of how it works.</span></span> <span data-ttu-id="715fb-157">如果您有一份數字清單，而且只想要傳回小於 3 的數字，您可以輸入下列命令以使用 `Where-Object` 來篩選數字︰</span><span class="sxs-lookup"><span data-stu-id="715fb-157">If you have a list of numbers, and only want to return the ones that are less than 3, you can use `Where-Object` to filter the numbers by typing:</span></span>

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a><span data-ttu-id="715fb-158">根據物件屬性篩選</span><span class="sxs-lookup"><span data-stu-id="715fb-158">Filtering Based on Object Properties</span></span>

<span data-ttu-id="715fb-159">因為 `$_` 參照了目前的管線物件，所以我們可以針對測試來存取其屬性。</span><span class="sxs-lookup"><span data-stu-id="715fb-159">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="715fb-160">舉例來說，我們可以檢視 WMI 中的 **Win32_SystemDriver** 類別。</span><span class="sxs-lookup"><span data-stu-id="715fb-160">As an example, we can look at the **Win32_SystemDriver** class in WMI.</span></span> <span data-ttu-id="715fb-161">一部系統上可能會有數百個系統驅動程式，但您可能只對某一組系統驅動程式感興趣，例如目前執行中的驅動程式。</span><span class="sxs-lookup"><span data-stu-id="715fb-161">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="715fb-162">針對 **Win32_SystemDriver** 類別，相關屬性為 **State** 。</span><span class="sxs-lookup"><span data-stu-id="715fb-162">For the **Win32_SystemDriver** class the relevant property is **State** .</span></span> <span data-ttu-id="715fb-163">您可以輸入下列命令來篩選系統驅動程式，只選取執行中的驅動程式︰</span><span class="sxs-lookup"><span data-stu-id="715fb-163">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

<span data-ttu-id="715fb-164">這仍會產生一長串清單。</span><span class="sxs-lookup"><span data-stu-id="715fb-164">This still produces a long list.</span></span> <span data-ttu-id="715fb-165">您可以一併測試 **StartMode** 值，以篩選成只選取設定為自動啟動的驅動程式：</span><span class="sxs-lookup"><span data-stu-id="715fb-165">You may want to filter to only select the drivers set to start automatically by testing the **StartMode** value as well:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Auto"}
```

```Output
DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
...
```

<span data-ttu-id="715fb-166">因為我們知道驅動程式正在執行，所以這會提供許多不再需要的資訊。</span><span class="sxs-lookup"><span data-stu-id="715fb-166">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span>
<span data-ttu-id="715fb-167">事實上，我們此時可能只需要名稱和顯示名稱資訊。</span><span class="sxs-lookup"><span data-stu-id="715fb-167">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="715fb-168">下列命令只會包含這兩個屬性，以產生更簡單的輸出︰</span><span class="sxs-lookup"><span data-stu-id="715fb-168">The following command includes only those two properties, resulting in much simpler output:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Manual"} |
      Format-Table -Property Name,DisplayName
```

```Output
Name              DisplayName
----              -----------
AsyncMac               RAS Asynchronous Media Driver
bindflt                Windows Bind Filter Driver
bowser                 Browser
CompositeBus           Composite Bus Enumerator Driver
condrv                 Console Driver
HdAudAddService        Microsoft 1.1 UAA Function Driver for High Definition Audio Service
HDAudBus               Microsoft UAA Bus Driver for High Definition Audio
HidUsb                 Microsoft HID Class Driver
HTTP                   HTTP Service
igfx                   igfx
IntcDAud               Intel(R) Display Audio
intelppm               Intel Processor Driver
...
```

<span data-ttu-id="715fb-169">上述命令中有兩個 `Where-Object` 元素，但可使用 `-and` 邏輯運算子以單一 `Where-Object` 元素來表示它們，就像這樣︰</span><span class="sxs-lookup"><span data-stu-id="715fb-169">There are two `Where-Object` elements in the above command, but they can be expressed in a single `Where-Object` element by using the `-and` logical operator, like this:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

<span data-ttu-id="715fb-170">下表列出標準邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="715fb-170">The standard logical operators are listed in the following table.</span></span>

| <span data-ttu-id="715fb-171">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="715fb-171">Logical Operator</span></span> |                 <span data-ttu-id="715fb-172">意義</span><span class="sxs-lookup"><span data-stu-id="715fb-172">Meaning</span></span>                  |  <span data-ttu-id="715fb-173">範例 (傳回 true)</span><span class="sxs-lookup"><span data-stu-id="715fb-173">Example (returns true)</span></span>  |
| ---------------- | ---------------------------------------- | ------------------------ |
| <span data-ttu-id="715fb-174">-and</span><span class="sxs-lookup"><span data-stu-id="715fb-174">-and</span></span>             | <span data-ttu-id="715fb-175">邏輯 and；若兩側為 true 即為 true</span><span class="sxs-lookup"><span data-stu-id="715fb-175">Logical and; true if both sides are true</span></span> | <span data-ttu-id="715fb-176">(1 -eq 1) -and (2 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="715fb-176">(1 -eq 1) -and (2 -eq 2)</span></span> |
| <span data-ttu-id="715fb-177">-or</span><span class="sxs-lookup"><span data-stu-id="715fb-177">-or</span></span>              | <span data-ttu-id="715fb-178">邏輯 or；若任一側為 true 即為 true</span><span class="sxs-lookup"><span data-stu-id="715fb-178">Logical or; true if either side is true</span></span>  | <span data-ttu-id="715fb-179">(1 -eq 1) -or (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="715fb-179">(1 -eq 1) -or (1 -eq 2)</span></span>  |
| <span data-ttu-id="715fb-180">-not</span><span class="sxs-lookup"><span data-stu-id="715fb-180">-not</span></span>             | <span data-ttu-id="715fb-181">邏輯 not；將 true 與 false 反轉</span><span class="sxs-lookup"><span data-stu-id="715fb-181">Logical not; reverses true and false</span></span>     | <span data-ttu-id="715fb-182">-not (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="715fb-182">-not (1 -eq 2)</span></span>           |
| \!               | <span data-ttu-id="715fb-183">邏輯 not；將 true 與 false 反轉</span><span class="sxs-lookup"><span data-stu-id="715fb-183">Logical not; reverses true and false</span></span>     | <span data-ttu-id="715fb-184">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="715fb-184">\!(1 -eq 2)</span></span>              |
