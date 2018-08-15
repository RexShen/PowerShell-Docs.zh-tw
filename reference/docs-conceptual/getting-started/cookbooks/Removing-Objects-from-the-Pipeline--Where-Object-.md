---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 從管線中移除物件 Where Object
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: c060b93a3823be26ad6c7757acc633bb4fc2fcfa
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587137"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="fd84d-103">從管線中移除物件 (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="fd84d-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="fd84d-104">在 Windows PowerShell 中，您通常會產生並沿著管線傳遞比所需更多的物件。</span><span class="sxs-lookup"><span data-stu-id="fd84d-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="fd84d-105">您可以使用 **Format** Cmdlet 指定要顯示的特定物件屬性，但這樣做並無法解決從顯示中移除整個物件的問題。</span><span class="sxs-lookup"><span data-stu-id="fd84d-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="fd84d-106">您可能需要在結束管線之前篩選物件，以便只對初始產生的物件子集執行動作。</span><span class="sxs-lookup"><span data-stu-id="fd84d-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="fd84d-107">Windows PowerShell 包含了 `Where-Object` Cmdlet，可讓您測試管線中的每個物件，並只在符合特定測試條件時才沿著管線傳遞。</span><span class="sxs-lookup"><span data-stu-id="fd84d-107">Windows PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="fd84d-108">未通過測試的物件會從管線中移除。</span><span class="sxs-lookup"><span data-stu-id="fd84d-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="fd84d-109">您會將測試條件提供為 `Where-Object` **FilterScript** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="fd84d-109">You supply the test condition as the value of the `Where-Object` **FilterScript** parameter.</span></span>

### <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="fd84d-110">使用 Where-Object 執行簡單的測試</span><span class="sxs-lookup"><span data-stu-id="fd84d-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="fd84d-111">**FilterScript** 的值是評估為 true 或 false 的指令碼區塊 (以大括弧 {} 括住的一或多個 Windows PowerShell 命令)。</span><span class="sxs-lookup"><span data-stu-id="fd84d-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="fd84d-112">這些指令碼區塊可以很簡單，但建立時需要了解另一個 Windows PowerShell 概念：比較運算子。</span><span class="sxs-lookup"><span data-stu-id="fd84d-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="fd84d-113">比較運算子會比較出現在運算子兩側的項目。</span><span class="sxs-lookup"><span data-stu-id="fd84d-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="fd84d-114">比較運算子是以 '-' 字元開頭，後面接著名稱。</span><span class="sxs-lookup"><span data-stu-id="fd84d-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="fd84d-115">基本比較運算子適用於幾乎任何類型的物件。</span><span class="sxs-lookup"><span data-stu-id="fd84d-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="fd84d-116">更進階的比較運算子只適用於文字或陣列。</span><span class="sxs-lookup"><span data-stu-id="fd84d-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="fd84d-117">根據預設，搭配文字使用時，Windows PowerShell 比較運算子不會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="fd84d-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="fd84d-118">基於剖析考量，不會使用 <、> 和 = 等符號作為比較運算子。</span><span class="sxs-lookup"><span data-stu-id="fd84d-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="fd84d-119">相反地，比較運算子是由字母所組成。</span><span class="sxs-lookup"><span data-stu-id="fd84d-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="fd84d-120">下表列出基本比較運算子。</span><span class="sxs-lookup"><span data-stu-id="fd84d-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="fd84d-121">比較運算子</span><span class="sxs-lookup"><span data-stu-id="fd84d-121">Comparison Operator</span></span>|<span data-ttu-id="fd84d-122">意義</span><span class="sxs-lookup"><span data-stu-id="fd84d-122">Meaning</span></span>|<span data-ttu-id="fd84d-123">範例 (傳回 true)</span><span class="sxs-lookup"><span data-stu-id="fd84d-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="fd84d-124">-eq</span><span class="sxs-lookup"><span data-stu-id="fd84d-124">-eq</span></span>|<span data-ttu-id="fd84d-125">等於</span><span class="sxs-lookup"><span data-stu-id="fd84d-125">is equal to</span></span>|<span data-ttu-id="fd84d-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="fd84d-126">1 -eq 1</span></span>|
|<span data-ttu-id="fd84d-127">-ne</span><span class="sxs-lookup"><span data-stu-id="fd84d-127">-ne</span></span>|<span data-ttu-id="fd84d-128">不等於</span><span class="sxs-lookup"><span data-stu-id="fd84d-128">Is not equal to</span></span>|<span data-ttu-id="fd84d-129">1 -ne 2</span><span class="sxs-lookup"><span data-stu-id="fd84d-129">1 -ne 2</span></span>|
|<span data-ttu-id="fd84d-130">-lt</span><span class="sxs-lookup"><span data-stu-id="fd84d-130">-lt</span></span>|<span data-ttu-id="fd84d-131">小於</span><span class="sxs-lookup"><span data-stu-id="fd84d-131">Is less than</span></span>|<span data-ttu-id="fd84d-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="fd84d-132">1 -lt 2</span></span>|
|<span data-ttu-id="fd84d-133">-le</span><span class="sxs-lookup"><span data-stu-id="fd84d-133">-le</span></span>|<span data-ttu-id="fd84d-134">小於或等於</span><span class="sxs-lookup"><span data-stu-id="fd84d-134">Is less than or equal to</span></span>|<span data-ttu-id="fd84d-135">1 -le 2</span><span class="sxs-lookup"><span data-stu-id="fd84d-135">1 -le 2</span></span>|
|<span data-ttu-id="fd84d-136">-gt</span><span class="sxs-lookup"><span data-stu-id="fd84d-136">-gt</span></span>|<span data-ttu-id="fd84d-137">大於</span><span class="sxs-lookup"><span data-stu-id="fd84d-137">Is greater than</span></span>|<span data-ttu-id="fd84d-138">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="fd84d-138">2 -gt 1</span></span>|
|<span data-ttu-id="fd84d-139">-ge</span><span class="sxs-lookup"><span data-stu-id="fd84d-139">-ge</span></span>|<span data-ttu-id="fd84d-140">大於或等於</span><span class="sxs-lookup"><span data-stu-id="fd84d-140">Is greater than or equal to</span></span>|<span data-ttu-id="fd84d-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="fd84d-141">2 -ge 1</span></span>|
|<span data-ttu-id="fd84d-142">-like</span><span class="sxs-lookup"><span data-stu-id="fd84d-142">-like</span></span>|<span data-ttu-id="fd84d-143">像是 (文字的萬用字元比較)</span><span class="sxs-lookup"><span data-stu-id="fd84d-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="fd84d-144">"file.doc" -like "f\*.do?"</span><span class="sxs-lookup"><span data-stu-id="fd84d-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="fd84d-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="fd84d-145">-notlike</span></span>|<span data-ttu-id="fd84d-146">不像是 (文字的萬用字元比較)</span><span class="sxs-lookup"><span data-stu-id="fd84d-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="fd84d-147">"file.doc" -notlike "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="fd84d-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="fd84d-148">-contains</span><span class="sxs-lookup"><span data-stu-id="fd84d-148">-contains</span></span>|<span data-ttu-id="fd84d-149">包含</span><span class="sxs-lookup"><span data-stu-id="fd84d-149">Contains</span></span>|<span data-ttu-id="fd84d-150">1,2,3 -contains 1</span><span class="sxs-lookup"><span data-stu-id="fd84d-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="fd84d-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="fd84d-151">-notcontains</span></span>|<span data-ttu-id="fd84d-152">不包含</span><span class="sxs-lookup"><span data-stu-id="fd84d-152">Does not contain</span></span>|<span data-ttu-id="fd84d-153">1,2,3 -notcontains 4</span><span class="sxs-lookup"><span data-stu-id="fd84d-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="fd84d-154">Where-Object 指令碼區塊使用特殊變數 `$_` 來參照管線中的目前物件。</span><span class="sxs-lookup"><span data-stu-id="fd84d-154">Where-Object script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="fd84d-155">以下示範其運作方式。</span><span class="sxs-lookup"><span data-stu-id="fd84d-155">Here is an example of how it works.</span></span> <span data-ttu-id="fd84d-156">如果您有一份數值清單，並且只想要傳回小於 3 的數值，您可以輸入下列命令使用 Where-Object 來篩選數值︰</span><span class="sxs-lookup"><span data-stu-id="fd84d-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a><span data-ttu-id="fd84d-157">根據物件屬性篩選</span><span class="sxs-lookup"><span data-stu-id="fd84d-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="fd84d-158">因為 `$_` 參照了目前的管線物件，所以我們可以針對測試來存取其屬性。</span><span class="sxs-lookup"><span data-stu-id="fd84d-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="fd84d-159">例如，我們可以檢視 WMI 中的 Win32_SystemDriver 類別。</span><span class="sxs-lookup"><span data-stu-id="fd84d-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="fd84d-160">一部系統上可能會有數百個系統驅動程式，但您可能只對某一組系統驅動程式感興趣，例如目前執行中的驅動程式。</span><span class="sxs-lookup"><span data-stu-id="fd84d-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="fd84d-161">如果您使用 Get-Member 檢視 Win32_SystemDriver 成員 (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType 屬性**)，您會看到相關屬性為 State，而且當驅動程式正在執行時，其值為 "Running"。</span><span class="sxs-lookup"><span data-stu-id="fd84d-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="fd84d-162">您可以輸入下列命令來篩選系統驅動程式，只選取執行中的驅動程式︰</span><span class="sxs-lookup"><span data-stu-id="fd84d-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

<span data-ttu-id="fd84d-163">這仍會產生一長串清單。</span><span class="sxs-lookup"><span data-stu-id="fd84d-163">This still produces a long list.</span></span> <span data-ttu-id="fd84d-164">您可能還想要進行篩選，只選取要藉由測試 StartMode 值自動啟動的驅動程式︰</span><span class="sxs-lookup"><span data-stu-id="fd84d-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

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
```

<span data-ttu-id="fd84d-165">因為我們知道驅動程式正在執行，所以這會提供許多不再需要的資訊。</span><span class="sxs-lookup"><span data-stu-id="fd84d-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="fd84d-166">事實上，我們此時可能只需要名稱和顯示名稱資訊。</span><span class="sxs-lookup"><span data-stu-id="fd84d-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="fd84d-167">下列命令只會包含這兩個屬性，以產生更簡單的輸出︰</span><span class="sxs-lookup"><span data-stu-id="fd84d-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

<span data-ttu-id="fd84d-168">上述命令中有兩個 Where-Object 項目，但可使用 -and 邏輯運算子以單一 Where-Object 項目來表示，就像這樣︰</span><span class="sxs-lookup"><span data-stu-id="fd84d-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="fd84d-169">下表列出標準邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="fd84d-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="fd84d-170">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="fd84d-170">Logical Operator</span></span>|<span data-ttu-id="fd84d-171">意義</span><span class="sxs-lookup"><span data-stu-id="fd84d-171">Meaning</span></span>|<span data-ttu-id="fd84d-172">範例 (傳回 true)</span><span class="sxs-lookup"><span data-stu-id="fd84d-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="fd84d-173">-and</span><span class="sxs-lookup"><span data-stu-id="fd84d-173">-and</span></span>|<span data-ttu-id="fd84d-174">邏輯 and；若兩側為 true 即為 true</span><span class="sxs-lookup"><span data-stu-id="fd84d-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="fd84d-175">(1 -eq 1) -and (2 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="fd84d-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="fd84d-176">-or</span><span class="sxs-lookup"><span data-stu-id="fd84d-176">-or</span></span>|<span data-ttu-id="fd84d-177">邏輯 or；若任一側為 true 即為 true</span><span class="sxs-lookup"><span data-stu-id="fd84d-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="fd84d-178">(1 -eq 1) -or (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="fd84d-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="fd84d-179">-not</span><span class="sxs-lookup"><span data-stu-id="fd84d-179">-not</span></span>|<span data-ttu-id="fd84d-180">邏輯 not；將 true 與 false 反轉</span><span class="sxs-lookup"><span data-stu-id="fd84d-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="fd84d-181">-not (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="fd84d-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="fd84d-182">邏輯 not；將 true 與 false 反轉</span><span class="sxs-lookup"><span data-stu-id="fd84d-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="fd84d-183">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="fd84d-183">\!(1 -eq 2)</span></span>|
