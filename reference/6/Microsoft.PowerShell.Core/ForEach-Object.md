---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 5a1a53c2b312ef36c80ecfb2a771d2fee2ebea7f
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "93206231"
---
# <span data-ttu-id="9be79-103">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="9be79-103">ForEach-Object</span></span>

## <span data-ttu-id="9be79-104">概要</span><span class="sxs-lookup"><span data-stu-id="9be79-104">SYNOPSIS</span></span>
<span data-ttu-id="9be79-105">針對輸入物件集合中的每個項目執行操作。</span><span class="sxs-lookup"><span data-stu-id="9be79-105">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="9be79-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9be79-106">SYNTAX</span></span>

### <span data-ttu-id="9be79-107">ScriptBlockSet (預設) </span><span class="sxs-lookup"><span data-stu-id="9be79-107">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9be79-108">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="9be79-108">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9be79-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9be79-109">DESCRIPTION</span></span>

<span data-ttu-id="9be79-110">此 `ForEach-Object` Cmdlet 會對輸入物件集合中的每個專案執行作業。</span><span class="sxs-lookup"><span data-stu-id="9be79-110">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="9be79-111">輸入物件可以透過管道傳送至 Cmdlet，或使用 **InputObject** 參數來指定。</span><span class="sxs-lookup"><span data-stu-id="9be79-111">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="9be79-112">從 Windows PowerShell 3.0 開始，有兩種不同的方式可建立 `ForEach-Object` 命令。</span><span class="sxs-lookup"><span data-stu-id="9be79-112">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="9be79-113">**腳本區塊** 。</span><span class="sxs-lookup"><span data-stu-id="9be79-113">**Script block** .</span></span> <span data-ttu-id="9be79-114">您可以使用指令碼區塊來指定操作。</span><span class="sxs-lookup"><span data-stu-id="9be79-114">You can use a script block to specify the operation.</span></span> <span data-ttu-id="9be79-115">在腳本區塊中，使用 `$_` 變數來表示目前的物件。</span><span class="sxs-lookup"><span data-stu-id="9be79-115">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="9be79-116">指令碼區塊是 **Process** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="9be79-116">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="9be79-117">腳本區塊可以包含任何 PowerShell 腳本。</span><span class="sxs-lookup"><span data-stu-id="9be79-117">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="9be79-118">例如，下列命令會取得電腦上每個處理程序之 **ProcessName** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9be79-118">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="9be79-119">`ForEach-Object` 支援 `begin` 、 `process` 和區塊， `end` 如 [about_functions](about/about_functions.md#piping-objects-to-functions)所述。</span><span class="sxs-lookup"><span data-stu-id="9be79-119">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="9be79-120">腳本區塊會在呼叫端的範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="9be79-120">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="9be79-121">因此，區塊可以存取該範圍中的變數，而且可以在 Cmdlet 完成之後，建立可保存在該範圍內的新變數。</span><span class="sxs-lookup"><span data-stu-id="9be79-121">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="9be79-122">**Operation 語句** 。</span><span class="sxs-lookup"><span data-stu-id="9be79-122">**Operation statement** .</span></span> <span data-ttu-id="9be79-123">您也可以撰寫像自然語言更類似的 operation 語句。</span><span class="sxs-lookup"><span data-stu-id="9be79-123">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="9be79-124">您可以使用操作陳述式來指定屬性值或呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="9be79-124">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="9be79-125">操作陳述式是在 Windows PowerShell 3.0 中導入。</span><span class="sxs-lookup"><span data-stu-id="9be79-125">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="9be79-126">例如，下列命令會一併取得電腦上每個處理程序之 **ProcessName** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9be79-126">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

## <span data-ttu-id="9be79-127">範例</span><span class="sxs-lookup"><span data-stu-id="9be79-127">EXAMPLES</span></span>

### <span data-ttu-id="9be79-128">範例1：分割陣列中的整數</span><span class="sxs-lookup"><span data-stu-id="9be79-128">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="9be79-129">這個範例會採用三個整數的陣列，並將每一個都除以1024。</span><span class="sxs-lookup"><span data-stu-id="9be79-129">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="9be79-130">範例2：取得目錄中所有檔案的長度</span><span class="sxs-lookup"><span data-stu-id="9be79-130">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="9be79-131">此範例會處理 PowerShell 安裝目錄中的檔案和目錄 `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="9be79-131">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="9be79-132">如果物件不是目錄，腳本區塊會取得檔案的名稱、將其 **Length** 屬性的值除以1024，然後將空格 ( "" ) 以將它與下一個專案分開。</span><span class="sxs-lookup"><span data-stu-id="9be79-132">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="9be79-133">此 Cmdlet 會使用 **PSISContainer** 屬性來判斷物件是否為目錄。</span><span class="sxs-lookup"><span data-stu-id="9be79-133">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="9be79-134">範例3：在最近的系統事件上操作</span><span class="sxs-lookup"><span data-stu-id="9be79-134">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="9be79-135">此範例會將1000最新的事件從系統事件記錄檔寫入至文字檔。</span><span class="sxs-lookup"><span data-stu-id="9be79-135">This example write the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="9be79-136">目前的時間會在處理事件之前和之後顯示。</span><span class="sxs-lookup"><span data-stu-id="9be79-136">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="9be79-137">`Get-EventLog` 從系統事件記錄檔取得1000的最新事件，並將它們儲存在 `$Events` 變數中。</span><span class="sxs-lookup"><span data-stu-id="9be79-137">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="9be79-138">`$Events` 接著會透過管道傳送至 `ForEach-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9be79-138">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="9be79-139">**Begin** 參數會顯示目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="9be79-139">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="9be79-140">接下來， **Process** 參數會使用 `Out-File` Cmdlet 來建立名為 events.txt 的文字檔，並將每個事件的訊息屬性儲存在該檔案中。</span><span class="sxs-lookup"><span data-stu-id="9be79-140">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="9be79-141">最後，會使用 **End** 參數，在所有處理都已完成之後顯示日期和時間。</span><span class="sxs-lookup"><span data-stu-id="9be79-141">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="9be79-142">範例4：變更登錄機碼的值</span><span class="sxs-lookup"><span data-stu-id="9be79-142">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="9be79-143">此範例會將金鑰下所有子機碼中的 **RemotePath** 登錄專案值變更 `HKCU:\Network` 為大寫文字。</span><span class="sxs-lookup"><span data-stu-id="9be79-143">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="9be79-144">您可以使用這個格式來變更登錄項目值的形式或內容。</span><span class="sxs-lookup"><span data-stu-id="9be79-144">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="9be79-145">**Network** 機碼中的每個子機碼代表在登入時將重新連線的連線網路磁碟機。</span><span class="sxs-lookup"><span data-stu-id="9be79-145">Each subkey in the **Network** key represents a mapped network drive that will reconnect at logon.</span></span>
<span data-ttu-id="9be79-146">**RemotePath** 項目包含連線的磁碟機的 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="9be79-146">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="9be79-147">例如，如果您將 E：磁片磁碟機對應到 `\\Server\Share` ，則會有的 **e** 子機碼 `HKCU:\Network` ，而 **e** 子機碼中 **RemotePath** 登錄專案的值為 `\\Server\Share` 。</span><span class="sxs-lookup"><span data-stu-id="9be79-147">For example, if you map the E: drive to `\\Server\Share`, there will be an **E** subkey of `HKCU:\Network` and the value of the **RemotePath** registry entry in the **E** subkey is `\\Server\Share`.</span></span>

<span data-ttu-id="9be79-148">此命令會使用指令程式 `Get-ItemProperty` 取得 **網路** 金鑰的所有子機碼，並使用 `Set-ItemProperty` Cmdlet 來變更每個機碼中 **RemotePath** 登錄專案的值。</span><span class="sxs-lookup"><span data-stu-id="9be79-148">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="9be79-149">在 `Set-ItemProperty` 命令中，路徑是登錄機碼的 **PSPath** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="9be79-149">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="9be79-150">這是代表登錄機碼的 Microsoft .NET Framework 物件的屬性，而不是登錄專案。</span><span class="sxs-lookup"><span data-stu-id="9be79-150">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="9be79-151">此命令會使用 **RemotePath** 值的 **ToUpper ( # B1** 方法，這是 (REG_SZ) 的字串。</span><span class="sxs-lookup"><span data-stu-id="9be79-151">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="9be79-152">因為 `Set-ItemProperty` 正在變更每個機碼的屬性，所以 `ForEach-Object` 需要 Cmdlet 才能存取屬性。</span><span class="sxs-lookup"><span data-stu-id="9be79-152">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="9be79-153">範例5：使用 $Null 自動變數</span><span class="sxs-lookup"><span data-stu-id="9be79-153">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="9be79-154">此範例顯示將 `$Null` 自動變數輸送至 Cmdlet 的效果 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="9be79-154">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="9be79-155">因為 PowerShell 會將 null 視為明確的預留位置，所以 `ForEach-Object` Cmdlet 會產生的 `$Null` 值，就像是對其他物件進行輸送的物件一樣。</span><span class="sxs-lookup"><span data-stu-id="9be79-155">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="9be79-156">範例6：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="9be79-156">Example 6: Get property values</span></span>

<span data-ttu-id="9be79-157">此範例會使用 Cmdlet 的 **成員名稱** 參數，取得所有已安裝之 PowerShell 模組的 **Path** 屬性值 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="9be79-157">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="9be79-158">第二個命令同等於第一個命令。</span><span class="sxs-lookup"><span data-stu-id="9be79-158">The second command is equivalent to the first.</span></span> <span data-ttu-id="9be79-159">它會使用 `Foreach` Cmdlet 的別名， `ForEach-Object` 並省略 **成員** 名稱參數的名稱，這是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="9be79-159">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="9be79-160">`ForEach-Object`Cmdlet 非常適合用來取得屬性值，因為它會在不變更類型的情況下取得值，不像 **格式** Cmdlet `Select-Object` 或 Cmdlet，後者會變更屬性值類型。</span><span class="sxs-lookup"><span data-stu-id="9be79-160">The `ForEach-Object` cmdlet is very useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="9be79-161">範例7：將模組名稱分割成元件名稱</span><span class="sxs-lookup"><span data-stu-id="9be79-161">Example 7: Split module names into component names</span></span>

<span data-ttu-id="9be79-162">此範例顯示三種將兩個以點分隔的模組名稱分割成其元件名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="9be79-162">This examples shows three ways to split two dot-separated module names into their component names.</span></span>

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

<span data-ttu-id="9be79-163">命令呼叫字串的 **Split** 方法。</span><span class="sxs-lookup"><span data-stu-id="9be79-163">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="9be79-164">這三個命令使用不同的語法，但它們是相等的並且可交換使用。</span><span class="sxs-lookup"><span data-stu-id="9be79-164">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="9be79-165">第一個命令使用傳統語法，其中包含腳本區塊和目前物件運算子 `$_` 。</span><span class="sxs-lookup"><span data-stu-id="9be79-165">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="9be79-166">它使用點語法來指定要括住分隔符號引數的方法和括號。</span><span class="sxs-lookup"><span data-stu-id="9be79-166">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="9be79-167">第二個命令使用 **MemberName** 參數來指定 **Split** 方法，並使用 **ArgumentName** 參數來將點 (".") 識別為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="9be79-167">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="9be79-168">第三個命令會使用 Cmdlet 的 **Foreach** 別名， `ForEach-Object` 並省略 **成員** 名稱和 **ArgumentList** 參數（選擇性）的名稱。</span><span class="sxs-lookup"><span data-stu-id="9be79-168">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="9be79-169">範例8：使用具有兩個腳本區塊的 ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="9be79-169">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="9be79-170">在此範例中，我們會將兩個腳本區塊 positionally 傳遞給。</span><span class="sxs-lookup"><span data-stu-id="9be79-170">In this example we pass two script blocks positionally.</span></span> <span data-ttu-id="9be79-171">所有腳本區塊都會系結至 **Process** 參數。</span><span class="sxs-lookup"><span data-stu-id="9be79-171">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="9be79-172">不過，它們會被視為已傳遞至 **Begin** 和 **Process** 參數。</span><span class="sxs-lookup"><span data-stu-id="9be79-172">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="9be79-173">範例9：使用具有兩個以上腳本區塊的 ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="9be79-173">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="9be79-174">在此範例中，我們會將兩個腳本區塊 positionally 傳遞給。</span><span class="sxs-lookup"><span data-stu-id="9be79-174">In this example we pass two script blocks positionally.</span></span> <span data-ttu-id="9be79-175">所有腳本區塊都會系結至 **Process** 參數。</span><span class="sxs-lookup"><span data-stu-id="9be79-175">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="9be79-176">不過，它們會被視為已傳遞至 **Begin** 、 **Process** 和 **End** 參數。</span><span class="sxs-lookup"><span data-stu-id="9be79-176">However, they are treated as if they had been passed to the **Begin** , **Process** , and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> <span data-ttu-id="9be79-177">第一個腳本區塊一律對應至 `begin` 區塊、最後一個區塊會對應至 `end` 區塊，而 between 中的區塊都會對應至 `process` 區塊。</span><span class="sxs-lookup"><span data-stu-id="9be79-177">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="9be79-178">範例10：為每個管線專案執行多個腳本區塊</span><span class="sxs-lookup"><span data-stu-id="9be79-178">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="9be79-179">如上一個範例所示，使用 **Process** 參數傳遞的多個腳本區塊會對應到 **Begin** 和 **End** 參數。</span><span class="sxs-lookup"><span data-stu-id="9be79-179">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="9be79-180">若要避免這種對應，您必須提供 **Begin** 和 **End** 參數的明確值。</span><span class="sxs-lookup"><span data-stu-id="9be79-180">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

## <span data-ttu-id="9be79-181">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9be79-181">PARAMETERS</span></span>

### <span data-ttu-id="9be79-182">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="9be79-182">-ArgumentList</span></span>

<span data-ttu-id="9be79-183">指定方法呼叫的引數陣列。</span><span class="sxs-lookup"><span data-stu-id="9be79-183">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="9be79-184">如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="9be79-184">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="9be79-185">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9be79-185">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be79-186">-Begin</span><span class="sxs-lookup"><span data-stu-id="9be79-186">-Begin</span></span>

<span data-ttu-id="9be79-187">指定在此 Cmdlet 處理任何輸入物件之前執行的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="9be79-187">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="9be79-188">此腳本區塊只會針對整個管線執行一次。</span><span class="sxs-lookup"><span data-stu-id="9be79-188">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="9be79-189">如需有關區塊的詳細資訊 `begin` ，請參閱 [about_Functions](about/about_functions.md#piping-objects-to-functions)。</span><span class="sxs-lookup"><span data-stu-id="9be79-189">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be79-190">-End</span><span class="sxs-lookup"><span data-stu-id="9be79-190">-End</span></span>

<span data-ttu-id="9be79-191">指定在此 Cmdlet 處理所有輸入物件之後執行的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="9be79-191">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="9be79-192">此腳本區塊只會針對整個管線執行一次。</span><span class="sxs-lookup"><span data-stu-id="9be79-192">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="9be79-193">如需有關區塊的詳細資訊 `end` ，請參閱 [about_Functions](about/about_functions.md#piping-objects-to-functions)。</span><span class="sxs-lookup"><span data-stu-id="9be79-193">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be79-194">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9be79-194">-InputObject</span></span>

<span data-ttu-id="9be79-195">指定輸入物件。</span><span class="sxs-lookup"><span data-stu-id="9be79-195">Specifies the input objects.</span></span> <span data-ttu-id="9be79-196">`ForEach-Object` 在每個輸入物件上執行腳本區塊或動作陳述式。</span><span class="sxs-lookup"><span data-stu-id="9be79-196">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="9be79-197">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="9be79-197">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="9be79-198">當您搭配使用 **inputobject** 參數與時 `ForEach-Object` ，不會將命令結果傳送至，而是 `ForEach-Object` 會將 **inputobject** 值視為單一物件。</span><span class="sxs-lookup"><span data-stu-id="9be79-198">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="9be79-199">即使值是命令結果的集合（例如），也是如此 `-InputObject (Get-Process)` 。</span><span class="sxs-lookup"><span data-stu-id="9be79-199">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="9be79-200">因為 **InputObject** 無法從物件的陣列或集合傳回個別屬性，所以如果您使用 `ForEach-Object` 在已定義屬性中具有特定值之物件的集合上執行作業，則建議您在 `ForEach-Object` 管線中使用，如本主題中的範例所示。</span><span class="sxs-lookup"><span data-stu-id="9be79-200">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9be79-201">-成員名稱</span><span class="sxs-lookup"><span data-stu-id="9be79-201">-MemberName</span></span>

<span data-ttu-id="9be79-202">指定要取得的屬性或要呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="9be79-202">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="9be79-203">允許使用萬用字元，但只有在產生的字串解析為唯一值時，才會運作。</span><span class="sxs-lookup"><span data-stu-id="9be79-203">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="9be79-204">例如，如果您執行 `Get-Process | ForEach -MemberName *Name` ，而且有一個以上的成員具有包含字串名稱的名稱，例如 **ProcessName** 和 **name** 屬性，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="9be79-204">If, for example, you run `Get-Process | ForEach -MemberName *Name`, and more than one member exists with a name that contains the string Name, such as the **ProcessName** and **Name** properties, the command fails.</span></span>

<span data-ttu-id="9be79-205">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9be79-205">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9be79-206">-Process</span><span class="sxs-lookup"><span data-stu-id="9be79-206">-Process</span></span>

<span data-ttu-id="9be79-207">指定在每個輸入物件上執行的操作。</span><span class="sxs-lookup"><span data-stu-id="9be79-207">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="9be79-208">此腳本區塊會針對管線中的每個物件執行。</span><span class="sxs-lookup"><span data-stu-id="9be79-208">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="9be79-209">如需有關區塊的詳細資訊 `process` ，請參閱 [about_Functions](about/about_functions.md#piping-objects-to-functions)。</span><span class="sxs-lookup"><span data-stu-id="9be79-209">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="9be79-210">當您將多個腳本區塊提供給 **Process** 參數時，第一個腳本區塊一律會對應至 `begin` 區塊。</span><span class="sxs-lookup"><span data-stu-id="9be79-210">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="9be79-211">如果只有兩個腳本區塊，則第二個區塊會對應至 `process` 區塊。</span><span class="sxs-lookup"><span data-stu-id="9be79-211">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="9be79-212">如果有三個或多個腳本區塊，則第一個腳本區塊一律會對應至 `begin` 區塊、最後一個區塊會對應至 `end` 區塊，而 between 中的區塊都會對應至 `process` 區塊。</span><span class="sxs-lookup"><span data-stu-id="9be79-212">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be79-213">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="9be79-213">-RemainingScripts</span></span>

<span data-ttu-id="9be79-214">指定 **Process** 參數未採用的所有腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="9be79-214">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="9be79-215">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9be79-215">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be79-216">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9be79-216">-Confirm</span></span>

<span data-ttu-id="9be79-217">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="9be79-217">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be79-218">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9be79-218">-WhatIf</span></span>

<span data-ttu-id="9be79-219">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="9be79-219">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9be79-220">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="9be79-220">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9be79-221">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9be79-221">CommonParameters</span></span>

<span data-ttu-id="9be79-222">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9be79-222">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9be79-223">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9be79-223">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9be79-224">輸入</span><span class="sxs-lookup"><span data-stu-id="9be79-224">INPUTS</span></span>

### <span data-ttu-id="9be79-225">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="9be79-225">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9be79-226">您可以使用管線將任何物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9be79-226">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="9be79-227">輸出</span><span class="sxs-lookup"><span data-stu-id="9be79-227">OUTPUTS</span></span>

### <span data-ttu-id="9be79-228">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="9be79-228">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9be79-229">這個 Cmdlet 會傳回由輸入決定的物件。</span><span class="sxs-lookup"><span data-stu-id="9be79-229">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="9be79-230">注意</span><span class="sxs-lookup"><span data-stu-id="9be79-230">NOTES</span></span>

- <span data-ttu-id="9be79-231">此 `ForEach-Object` Cmdlet 的運作方式與 **foreach** 語句很類似，不同之處在于您無法使用管線將輸入傳送至 **foreach** 語句。</span><span class="sxs-lookup"><span data-stu-id="9be79-231">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="9be79-232">如需 **Foreach** 語句的詳細資訊，請參閱 [about_Foreach](./About/about_Foreach.md)。</span><span class="sxs-lookup"><span data-stu-id="9be79-232">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="9be79-233">從 PowerShell 4.0 開始， `Where` `ForEach` 已新增方法以與集合搭配使用。</span><span class="sxs-lookup"><span data-stu-id="9be79-233">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="9be79-234">您可以在這裡閱讀更多有關這些新方法的資訊 [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="9be79-234">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="9be79-235">相關連結</span><span class="sxs-lookup"><span data-stu-id="9be79-235">RELATED LINKS</span></span>

[<span data-ttu-id="9be79-236">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="9be79-236">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="9be79-237">Where-Object</span><span class="sxs-lookup"><span data-stu-id="9be79-237">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="9be79-238">Group-Object</span><span class="sxs-lookup"><span data-stu-id="9be79-238">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="9be79-239">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="9be79-239">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="9be79-240">New-Object</span><span class="sxs-lookup"><span data-stu-id="9be79-240">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="9be79-241">Select-Object</span><span class="sxs-lookup"><span data-stu-id="9be79-241">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="9be79-242">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="9be79-242">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="9be79-243">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="9be79-243">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
