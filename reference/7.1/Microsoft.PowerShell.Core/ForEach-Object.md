---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: e05c9b5e44d26b1e16c82f734ec60ca4cc73ab4d
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "93206236"
---
# <span data-ttu-id="09f5f-103">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="09f5f-103">ForEach-Object</span></span>

## <span data-ttu-id="09f5f-104">概要</span><span class="sxs-lookup"><span data-stu-id="09f5f-104">Synopsis</span></span>
<span data-ttu-id="09f5f-105">針對輸入物件集合中的每個項目執行操作。</span><span class="sxs-lookup"><span data-stu-id="09f5f-105">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="09f5f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="09f5f-106">Syntax</span></span>

### <span data-ttu-id="09f5f-107">ScriptBlockSet (預設) </span><span class="sxs-lookup"><span data-stu-id="09f5f-107">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="09f5f-108">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="09f5f-108">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="09f5f-109">ParallelParameterSet</span><span class="sxs-lookup"><span data-stu-id="09f5f-109">ParallelParameterSet</span></span>

```
ForEach-Object -Parallel <scriptblock> [-InputObject <PSObject>] [-ThrottleLimit <int>]
[-UseNewRunspace] [-TimeoutSeconds <int>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="09f5f-110">Description</span><span class="sxs-lookup"><span data-stu-id="09f5f-110">Description</span></span>

<span data-ttu-id="09f5f-111">此 `ForEach-Object` Cmdlet 會對輸入物件集合中的每個專案執行作業。</span><span class="sxs-lookup"><span data-stu-id="09f5f-111">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="09f5f-112">輸入物件可以透過管道傳送至 Cmdlet，或使用 **InputObject** 參數來指定。</span><span class="sxs-lookup"><span data-stu-id="09f5f-112">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="09f5f-113">從 Windows PowerShell 3.0 開始，有兩種不同的方式可建立 `ForEach-Object` 命令。</span><span class="sxs-lookup"><span data-stu-id="09f5f-113">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="09f5f-114">**腳本區塊** 。</span><span class="sxs-lookup"><span data-stu-id="09f5f-114">**Script block** .</span></span> <span data-ttu-id="09f5f-115">您可以使用指令碼區塊來指定操作。</span><span class="sxs-lookup"><span data-stu-id="09f5f-115">You can use a script block to specify the operation.</span></span> <span data-ttu-id="09f5f-116">在腳本區塊中，使用 `$_` 變數來表示目前的物件。</span><span class="sxs-lookup"><span data-stu-id="09f5f-116">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="09f5f-117">指令碼區塊是 **Process** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="09f5f-117">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="09f5f-118">腳本區塊可以包含任何 PowerShell 腳本。</span><span class="sxs-lookup"><span data-stu-id="09f5f-118">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="09f5f-119">例如，下列命令會取得電腦上每個處理程序之 **ProcessName** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="09f5f-119">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="09f5f-120">`ForEach-Object` 支援 `begin` 、 `process` 和區塊， `end` 如 [about_functions](about/about_functions.md#piping-objects-to-functions)所述。</span><span class="sxs-lookup"><span data-stu-id="09f5f-120">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="09f5f-121">腳本區塊會在呼叫端的範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="09f5f-121">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="09f5f-122">因此，區塊可以存取該範圍中的變數，而且可以在 Cmdlet 完成之後，建立可保存在該範圍內的新變數。</span><span class="sxs-lookup"><span data-stu-id="09f5f-122">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="09f5f-123">**Operation 語句** 。</span><span class="sxs-lookup"><span data-stu-id="09f5f-123">**Operation statement** .</span></span> <span data-ttu-id="09f5f-124">您也可以撰寫像自然語言更類似的 operation 語句。</span><span class="sxs-lookup"><span data-stu-id="09f5f-124">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="09f5f-125">您可以使用操作陳述式來指定屬性值或呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="09f5f-125">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="09f5f-126">操作陳述式是在 Windows PowerShell 3.0 中導入。</span><span class="sxs-lookup"><span data-stu-id="09f5f-126">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="09f5f-127">例如，下列命令會一併取得電腦上每個處理程序之 **ProcessName** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="09f5f-127">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

- <span data-ttu-id="09f5f-128">**平行執行的腳本區塊** 。</span><span class="sxs-lookup"><span data-stu-id="09f5f-128">**Parallel running script block** .</span></span> <span data-ttu-id="09f5f-129">從 PowerShell 7.0 開始，可以使用第三個參數集來平行執行每個腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-129">Beginning with PowerShell 7.0, a third parameter set is available that runs each script block in parallel.</span></span> <span data-ttu-id="09f5f-130">**ThrottleLimit** 參數會限制一次執行的平行腳本數目。</span><span class="sxs-lookup"><span data-stu-id="09f5f-130">The **ThrottleLimit** parameter limits the number of parallel scripts running at a time.</span></span> <span data-ttu-id="09f5f-131">同樣地，您 `$_` 可以使用變數來表示腳本區塊中目前的輸入物件。</span><span class="sxs-lookup"><span data-stu-id="09f5f-131">As before, use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="09f5f-132">使用 `$using:` 關鍵字將變數參考傳遞給執行中的腳本。</span><span class="sxs-lookup"><span data-stu-id="09f5f-132">Use the `$using:` keyword to pass variable references to the running script.</span></span>

  <span data-ttu-id="09f5f-133">在 PowerShell 7 中，會為每個迴圈反復專案建立新的運行空間，以確保最大的隔離。</span><span class="sxs-lookup"><span data-stu-id="09f5f-133">In PowerShell 7, a new runspace is created for each loop iteration to ensure maximum isolation.</span></span>
  <span data-ttu-id="09f5f-134">如果您所執行的工作與建立新的執行空間相較之下，或有許多反覆運算執行大量的工作，則這可能是很大的效能和資源點擊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-134">This can be a large performance and resource hit if the work you are doing is small compared to creating new runspaces or if there are a lot of iterations performing significant work.</span></span> <span data-ttu-id="09f5f-135">從 PowerShell 7.1 開始，預設會重複使用來自運行空間集區的運行空間。</span><span class="sxs-lookup"><span data-stu-id="09f5f-135">As of PowerShell 7.1, runspaces from a runspace pool are reused by default.</span></span> <span data-ttu-id="09f5f-136">運行時集區大小是由 **ThrottleLimit** 參數指定。</span><span class="sxs-lookup"><span data-stu-id="09f5f-136">The runspace pool size is specified by the **ThrottleLimit** parameter.</span></span> <span data-ttu-id="09f5f-137">預設的運行時集區大小為5。</span><span class="sxs-lookup"><span data-stu-id="09f5f-137">The default runspace pool size is 5.</span></span> <span data-ttu-id="09f5f-138">您仍可使用 **UseNewRunspace** 參數為每個反復專案建立新的運行空間。</span><span class="sxs-lookup"><span data-stu-id="09f5f-138">You can still create a new runspace for each iteration using the **UseNewRunspace** switch.</span></span>

  <span data-ttu-id="09f5f-139">根據預設，parallel scriptblocks 會使用啟動平行工作之呼叫端的目前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="09f5f-139">By default, the parallel scriptblocks use the current working directory of the caller that started the parallel tasks.</span></span>

  <span data-ttu-id="09f5f-140">非終止錯誤會寫入至 Cmdlet 錯誤資料流程，因為它們在平行執行的 scriptblocks 中發生。</span><span class="sxs-lookup"><span data-stu-id="09f5f-140">Non-terminating errors are written to the cmdlet error stream as they occur in parallel running scriptblocks.</span></span> <span data-ttu-id="09f5f-141">因為無法判斷平行 scriptblock 執行順序，錯誤資料流程中錯誤的出現順序是隨機的。</span><span class="sxs-lookup"><span data-stu-id="09f5f-141">Because parallel scriptblock execution order cannot be determined, the order in which errors appear in the error stream is random.</span></span> <span data-ttu-id="09f5f-142">同樣地，寫入其他資料流程的訊息（例如警告、詳細資訊或資訊）會以不定的順序寫入這些資料流程。</span><span class="sxs-lookup"><span data-stu-id="09f5f-142">Likewise, messages written to other data streams, like warning, verbose, or information are written to those data streams in an indeterminate order.</span></span>

  <span data-ttu-id="09f5f-143">終止錯誤（例如例外狀況）會終止其發生之 scriptblocks 的個別平行實例。</span><span class="sxs-lookup"><span data-stu-id="09f5f-143">Terminating errors, such as exceptions, terminate the individual parallel instance of the scriptblocks in which they occur.</span></span> <span data-ttu-id="09f5f-144">其中一個 scriptblocks 的終止錯誤可能不會導致 `Foreach-Object` Cmdlet 終止。</span><span class="sxs-lookup"><span data-stu-id="09f5f-144">A terminating error in one scriptblocks may not cause the termination of the `Foreach-Object` cmdlet.</span></span> <span data-ttu-id="09f5f-145">以平行方式執行的其他 scriptblocks 會繼續執行，除非它們也遇到終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="09f5f-145">The other scriptblocks, running in parallel, continue to run unless they also encounter a terminating error.</span></span> <span data-ttu-id="09f5f-146">終止錯誤會以 **ErrorRecord** 的形式寫入至錯誤資料流程，而 **FullyQualifiedErrorId** 為 `PSTaskException` 。</span><span class="sxs-lookup"><span data-stu-id="09f5f-146">The terminating error is written to the error data stream as an **ErrorRecord** with a **FullyQualifiedErrorId** of `PSTaskException`.</span></span>
  <span data-ttu-id="09f5f-147">使用 PowerShell try/catch 或 catch 區塊，可將終止錯誤轉換為非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="09f5f-147">Terminating errors can be converted to non-terminating errors using PowerShell try/catch or trap blocks.</span></span>

## <span data-ttu-id="09f5f-148">範例</span><span class="sxs-lookup"><span data-stu-id="09f5f-148">Examples</span></span>

### <span data-ttu-id="09f5f-149">範例1：分割陣列中的整數</span><span class="sxs-lookup"><span data-stu-id="09f5f-149">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="09f5f-150">這個範例會採用三個整數的陣列，並將每一個都除以1024。</span><span class="sxs-lookup"><span data-stu-id="09f5f-150">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="09f5f-151">範例2：取得目錄中所有檔案的長度</span><span class="sxs-lookup"><span data-stu-id="09f5f-151">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="09f5f-152">此範例會處理 PowerShell 安裝目錄中的檔案和目錄 `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="09f5f-152">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="09f5f-153">如果物件不是目錄，腳本區塊會取得檔案的名稱、將其 **Length** 屬性的值除以1024，然後將空格 ( "" ) 以將它與下一個專案分開。</span><span class="sxs-lookup"><span data-stu-id="09f5f-153">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="09f5f-154">此 Cmdlet 會使用 **PSISContainer** 屬性來判斷物件是否為目錄。</span><span class="sxs-lookup"><span data-stu-id="09f5f-154">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="09f5f-155">範例3：在最近的系統事件上操作</span><span class="sxs-lookup"><span data-stu-id="09f5f-155">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="09f5f-156">此範例會將1000的最新事件從系統事件記錄檔寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="09f5f-156">This example writes the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="09f5f-157">目前的時間會在處理事件之前和之後顯示。</span><span class="sxs-lookup"><span data-stu-id="09f5f-157">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="09f5f-158">`Get-EventLog` 從系統事件記錄檔取得1000的最新事件，並將它們儲存在 `$Events` 變數中。</span><span class="sxs-lookup"><span data-stu-id="09f5f-158">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="09f5f-159">`$Events` 接著會透過管道傳送至 `ForEach-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="09f5f-159">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="09f5f-160">**Begin** 參數會顯示目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="09f5f-160">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="09f5f-161">接下來， **Process** 參數會使用 `Out-File` Cmdlet 來建立名為 events.txt 的文字檔，並將每個事件的訊息屬性儲存在該檔案中。</span><span class="sxs-lookup"><span data-stu-id="09f5f-161">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="09f5f-162">最後，會使用 **End** 參數，在所有處理都已完成之後顯示日期和時間。</span><span class="sxs-lookup"><span data-stu-id="09f5f-162">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="09f5f-163">範例4：變更登錄機碼的值</span><span class="sxs-lookup"><span data-stu-id="09f5f-163">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="09f5f-164">此範例會將金鑰下所有子機碼中的 **RemotePath** 登錄專案值變更 `HKCU:\Network` 為大寫文字。</span><span class="sxs-lookup"><span data-stu-id="09f5f-164">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="09f5f-165">您可以使用這個格式來變更登錄項目值的形式或內容。</span><span class="sxs-lookup"><span data-stu-id="09f5f-165">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="09f5f-166">**網路** 機碼中的每個子機碼代表在登入時重新連線的對應網路磁碟機機。</span><span class="sxs-lookup"><span data-stu-id="09f5f-166">Each subkey in the **Network** key represents a mapped network drive that reconnects at sign on.</span></span> <span data-ttu-id="09f5f-167">**RemotePath** 項目包含連線的磁碟機的 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="09f5f-167">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="09f5f-168">例如，如果您將 E：磁片磁碟機對應到 `\\Server\Share` ，則會在中建立 **e** 子機碼， `HKCU:\Network` 並將 **RemotePath** 登錄值設定為 `\\Server\Share` 。</span><span class="sxs-lookup"><span data-stu-id="09f5f-168">For example, if you map the E: drive to `\\Server\Share`, an **E** subkey is created in `HKCU:\Network` with the **RemotePath** registry value set to `\\Server\Share`.</span></span>

<span data-ttu-id="09f5f-169">此命令會使用指令程式 `Get-ItemProperty` 取得 **網路** 金鑰的所有子機碼，並使用 `Set-ItemProperty` Cmdlet 來變更每個機碼中 **RemotePath** 登錄專案的值。</span><span class="sxs-lookup"><span data-stu-id="09f5f-169">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="09f5f-170">在 `Set-ItemProperty` 命令中，路徑是登錄機碼的 **PSPath** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="09f5f-170">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="09f5f-171">這是代表登錄機碼的 Microsoft .NET Framework 物件的屬性，而不是登錄專案。</span><span class="sxs-lookup"><span data-stu-id="09f5f-171">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="09f5f-172">此命令會使用 **RemotePath** 值的 **ToUpper ( # B1** 方法，這是 (REG_SZ) 的字串。</span><span class="sxs-lookup"><span data-stu-id="09f5f-172">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="09f5f-173">因為 `Set-ItemProperty` 正在變更每個機碼的屬性，所以 `ForEach-Object` 需要 Cmdlet 才能存取屬性。</span><span class="sxs-lookup"><span data-stu-id="09f5f-173">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="09f5f-174">範例5：使用 $Null 自動變數</span><span class="sxs-lookup"><span data-stu-id="09f5f-174">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="09f5f-175">此範例顯示將 `$Null` 自動變數輸送至 Cmdlet 的效果 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="09f5f-175">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="09f5f-176">因為 PowerShell 會將 null 視為明確的預留位置，所以 `ForEach-Object` Cmdlet 會產生的 `$Null` 值，就像是對其他物件進行輸送的物件一樣。</span><span class="sxs-lookup"><span data-stu-id="09f5f-176">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="09f5f-177">範例6：取得屬性值</span><span class="sxs-lookup"><span data-stu-id="09f5f-177">Example 6: Get property values</span></span>

<span data-ttu-id="09f5f-178">此範例會使用 Cmdlet 的 **成員名稱** 參數，取得所有已安裝之 PowerShell 模組的 **Path** 屬性值 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="09f5f-178">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="09f5f-179">第二個命令同等於第一個命令。</span><span class="sxs-lookup"><span data-stu-id="09f5f-179">The second command is equivalent to the first.</span></span> <span data-ttu-id="09f5f-180">它會使用 `Foreach` Cmdlet 的別名， `ForEach-Object` 並省略 **成員** 名稱參數的名稱，這是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="09f5f-180">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="09f5f-181">`ForEach-Object`Cmdlet 在取得屬性值時很有用，因為它會在不變更類型的情況下取得值，不像 **格式** Cmdlet 或 `Select-Object` Cmdlet，後者會變更屬性值類型。</span><span class="sxs-lookup"><span data-stu-id="09f5f-181">The `ForEach-Object` cmdlet is useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="09f5f-182">範例7：將模組名稱分割成元件名稱</span><span class="sxs-lookup"><span data-stu-id="09f5f-182">Example 7: Split module names into component names</span></span>

<span data-ttu-id="09f5f-183">此範例顯示三種將兩個以點分隔的模組名稱分割成其元件名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="09f5f-183">This example shows three ways to split two dot-separated module names into their component names.</span></span>

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

<span data-ttu-id="09f5f-184">命令呼叫字串的 **Split** 方法。</span><span class="sxs-lookup"><span data-stu-id="09f5f-184">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="09f5f-185">這三個命令使用不同的語法，但它們是相等的並且可交換使用。</span><span class="sxs-lookup"><span data-stu-id="09f5f-185">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="09f5f-186">第一個命令使用傳統語法，其中包含腳本區塊和目前物件運算子 `$_` 。</span><span class="sxs-lookup"><span data-stu-id="09f5f-186">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="09f5f-187">它使用點語法來指定要括住分隔符號引數的方法和括號。</span><span class="sxs-lookup"><span data-stu-id="09f5f-187">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="09f5f-188">第二個命令使用 **MemberName** 參數來指定 **Split** 方法，並使用 **ArgumentName** 參數來將點 (".") 識別為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="09f5f-188">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="09f5f-189">第三個命令會使用 Cmdlet 的 **Foreach** 別名， `ForEach-Object` 並省略 **成員** 名稱和 **ArgumentList** 參數（選擇性）的名稱。</span><span class="sxs-lookup"><span data-stu-id="09f5f-189">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="09f5f-190">範例8：使用具有兩個腳本區塊的 ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="09f5f-190">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="09f5f-191">在此範例中，我們會將兩個腳本區塊 positionally 傳遞給。</span><span class="sxs-lookup"><span data-stu-id="09f5f-191">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="09f5f-192">所有腳本區塊都會系結至 **Process** 參數。</span><span class="sxs-lookup"><span data-stu-id="09f5f-192">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="09f5f-193">不過，它們會被視為已傳遞至 **Begin** 和 **Process** 參數。</span><span class="sxs-lookup"><span data-stu-id="09f5f-193">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="09f5f-194">範例9：使用具有兩個以上腳本區塊的 ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="09f5f-194">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="09f5f-195">在此範例中，我們會將兩個腳本區塊 positionally 傳遞給。</span><span class="sxs-lookup"><span data-stu-id="09f5f-195">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="09f5f-196">所有腳本區塊都會系結至 **Process** 參數。</span><span class="sxs-lookup"><span data-stu-id="09f5f-196">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="09f5f-197">不過，它們會被視為已傳遞至 **Begin** 、 **Process** 和 **End** 參數。</span><span class="sxs-lookup"><span data-stu-id="09f5f-197">However, they are treated as if they had been passed to the **Begin** , **Process** , and **End** parameters.</span></span>

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
> <span data-ttu-id="09f5f-198">第一個腳本區塊一律對應至 `begin` 區塊、最後一個區塊會對應至 `end` 區塊，而 between 中的區塊都會對應至 `process` 區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-198">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="09f5f-199">範例10：為每個管線專案執行多個腳本區塊</span><span class="sxs-lookup"><span data-stu-id="09f5f-199">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="09f5f-200">如上一個範例所示，使用 **Process** 參數傳遞的多個腳本區塊會對應到 **Begin** 和 **End** 參數。</span><span class="sxs-lookup"><span data-stu-id="09f5f-200">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="09f5f-201">若要避免這種對應，您必須提供 **Begin** 和 **End** 參數的明確值。</span><span class="sxs-lookup"><span data-stu-id="09f5f-201">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

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

### <span data-ttu-id="09f5f-202">範例11：平行批次執行慢速腳本</span><span class="sxs-lookup"><span data-stu-id="09f5f-202">Example 11: Run slow script in parallel batches</span></span>

<span data-ttu-id="09f5f-203">此範例會執行簡單的腳本區塊，該區塊會評估字串並睡眠一秒鐘。</span><span class="sxs-lookup"><span data-stu-id="09f5f-203">This example runs a simple script block that evaluates a string and sleeps for one second.</span></span>

```powershell
$Message = "Output:"

1..8 | ForEach-Object -Parallel {
    "$using:Message $_"
    Start-Sleep 1
} -ThrottleLimit 4
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
```

<span data-ttu-id="09f5f-204">**ThrottleLimit** 參數值設定為4，因此會以四個批次來處理輸入。</span><span class="sxs-lookup"><span data-stu-id="09f5f-204">The **ThrottleLimit** parameter value is set to 4 so that the input is processed in batches of four.</span></span>
<span data-ttu-id="09f5f-205">`$using:`關鍵字是用來將變數傳遞 `$Message` 至每個平行腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-205">The `$using:` keyword is used to pass the `$Message` variable into each parallel script block.</span></span>

### <span data-ttu-id="09f5f-206">範例12：平行取出記錄專案</span><span class="sxs-lookup"><span data-stu-id="09f5f-206">Example 12: Retrieve log entries in parallel</span></span>

<span data-ttu-id="09f5f-207">此範例會從本機 Windows 電腦上的5個系統記錄檔抓取50000記錄專案。</span><span class="sxs-lookup"><span data-stu-id="09f5f-207">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine.</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count
```

```Output
50000
```

<span data-ttu-id="09f5f-208">**Parallel** 參數會針對每個輸入記錄名稱指定平行執行的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-208">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span> <span data-ttu-id="09f5f-209">**ThrottleLimit** 參數可確保所有五個腳本區塊同時執行。</span><span class="sxs-lookup"><span data-stu-id="09f5f-209">The **ThrottleLimit** parameter ensures that all five script blocks run at the same time.</span></span>

### <span data-ttu-id="09f5f-210">範例13：以工作方式平行執行</span><span class="sxs-lookup"><span data-stu-id="09f5f-210">Example 13: Run in parallel as a job</span></span>

<span data-ttu-id="09f5f-211">此範例會平行執行簡單的腳本區塊，一次建立兩個背景工作。</span><span class="sxs-lookup"><span data-stu-id="09f5f-211">This example runs a simple script block in parallel, creating two background jobs at a time.</span></span>

```powershell
$job = 1..10 | ForEach-Object -Parallel {
    "Output: $_"
    Start-Sleep 1
} -ThrottleLimit 2 -AsJob

$job | Receive-Job -Wait
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
Output: 9
Output: 10
```

<span data-ttu-id="09f5f-212">`$job`變數會接收工作物件，該物件會收集輸出資料並監視正在執行的狀態。</span><span class="sxs-lookup"><span data-stu-id="09f5f-212">the `$job` variable receives the job object that collects output data and monitors running state.</span></span>
<span data-ttu-id="09f5f-213">工作物件會以 `Receive-Job` **等候** 切換參數輸送至。</span><span class="sxs-lookup"><span data-stu-id="09f5f-213">The job object is piped to `Receive-Job` with the **Wait** switch parameter.</span></span> <span data-ttu-id="09f5f-214">這會串流輸出到主控台，就像是在 `ForEach-Object -Parallel` 沒有 **AsJob** 的情況下執行一樣。</span><span class="sxs-lookup"><span data-stu-id="09f5f-214">And this streams output to the console, just as if `ForEach-Object -Parallel` was run without **AsJob** .</span></span>

### <span data-ttu-id="09f5f-215">範例14：使用安全線程變數參考</span><span class="sxs-lookup"><span data-stu-id="09f5f-215">Example 14: Using thread safe variable references</span></span>

<span data-ttu-id="09f5f-216">這個範例會平行叫用腳本區塊，以收集唯一的命名進程物件。</span><span class="sxs-lookup"><span data-stu-id="09f5f-216">This example invokes script blocks in parallel to collect uniquely named Process objects.</span></span>

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
Get-Process | ForEach-Object -Parallel {
    $dict = $using:threadSafeDictionary
    $dict.TryAdd($_.ProcessName, $_)
}

$threadSafeDictionary["pwsh"]
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     82    82.87     130.85      15.55    2808   2 pwsh
```

<span data-ttu-id="09f5f-217">**ConcurrentDictionary** 物件的單一實例會傳遞至每個腳本區塊，以收集物件。</span><span class="sxs-lookup"><span data-stu-id="09f5f-217">A single instance of a **ConcurrentDictionary** object is passed to each script block to collect the objects.</span></span> <span data-ttu-id="09f5f-218">由於 **ConcurrentDictionary** 是安全線程，因此每個平行腳本都可以安全地修改它。</span><span class="sxs-lookup"><span data-stu-id="09f5f-218">Since the **ConcurrentDictionary** is thread safe, it is safe to be modified by each parallel script.</span></span> <span data-ttu-id="09f5f-219">不安全線程的物件（例如， **system.object** ）在這裡不是安全的使用方式。</span><span class="sxs-lookup"><span data-stu-id="09f5f-219">A non-thread-safe object, such as **System.Collections.Generic.Dictionary** , would not be safe to use here.</span></span>

> [!NOTE]
> <span data-ttu-id="09f5f-220">此範例是使用 **平行** 參數的效率極低。</span><span class="sxs-lookup"><span data-stu-id="09f5f-220">This example is a very inefficient use of **Parallel** parameter.</span></span> <span data-ttu-id="09f5f-221">腳本只會將輸入物件加入至並行的字典物件。</span><span class="sxs-lookup"><span data-stu-id="09f5f-221">The script simply adds the input object to a concurrent dictionary object.</span></span> <span data-ttu-id="09f5f-222">這很簡單，不值得在個別執行緒中叫用每個腳本的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="09f5f-222">It is trivial and not worth the overhead of invoking each script in a separate thread.</span></span> <span data-ttu-id="09f5f-223">`ForEach-Object`在沒有 **平行** 切換的情況下執行通常更有效率且更快速。</span><span class="sxs-lookup"><span data-stu-id="09f5f-223">Running `ForEach-Object` normally without the **Parallel** switch is much more efficient and faster.</span></span> <span data-ttu-id="09f5f-224">此範例僅供示範如何使用安全線程變數。</span><span class="sxs-lookup"><span data-stu-id="09f5f-224">This example is only intended to demonstrate how to use thread safe variables.</span></span>

### <span data-ttu-id="09f5f-225">範例15：使用平行執行寫入錯誤</span><span class="sxs-lookup"><span data-stu-id="09f5f-225">Example 15: Writing errors with parallel execution</span></span>

<span data-ttu-id="09f5f-226">此範例會以平行方式寫入錯誤資料流程，其中寫入的錯誤順序是隨機的。</span><span class="sxs-lookup"><span data-stu-id="09f5f-226">This example writes to the error stream in parallel, where the order of written errors is random.</span></span>

```powershell
1..3 | ForEach-Object -Parallel {
    Write-Error "Error: $_"
}
```

```Output
Write-Error: Error: 1
Write-Error: Error: 3
Write-Error: Error: 2
```

### <span data-ttu-id="09f5f-227">範例16：平行執行時終止錯誤</span><span class="sxs-lookup"><span data-stu-id="09f5f-227">Example 16: Terminating errors in parallel execution</span></span>

<span data-ttu-id="09f5f-228">此範例示範一個平行執行的 scriptblock 中的終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="09f5f-228">This example demonstrates a terminating error in one parallel running scriptblock.</span></span>

```powershell
1..5 | ForEach-Object -Parallel {
    if ($_ -eq 3)
    {
        throw "Terminating Error: $_"
    }

    Write-Output "Output: $_"
}
```

```Output
Exception: Terminating Error: 3
Output: 1
Output: 4
Output: 2
Output: 5
```

<span data-ttu-id="09f5f-229">`Output: 3` 永遠不會寫入，因為該反覆運算的平行 scriptblock 已經結束。</span><span class="sxs-lookup"><span data-stu-id="09f5f-229">`Output: 3` is never written because the parallel scriptblock for that iteration was terminated.</span></span>

## <span data-ttu-id="09f5f-230">參數</span><span class="sxs-lookup"><span data-stu-id="09f5f-230">Parameters</span></span>

### <span data-ttu-id="09f5f-231">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="09f5f-231">-ArgumentList</span></span>

<span data-ttu-id="09f5f-232">指定方法呼叫的引數陣列。</span><span class="sxs-lookup"><span data-stu-id="09f5f-232">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="09f5f-233">如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="09f5f-233">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="09f5f-234">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="09f5f-234">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="09f5f-235">-Begin</span><span class="sxs-lookup"><span data-stu-id="09f5f-235">-Begin</span></span>

<span data-ttu-id="09f5f-236">指定在此 Cmdlet 處理任何輸入物件之前執行的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-236">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="09f5f-237">此腳本區塊只會針對整個管線執行一次。</span><span class="sxs-lookup"><span data-stu-id="09f5f-237">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="09f5f-238">如需有關區塊的詳細資訊 `begin` ，請參閱 [about_Functions](about/about_functions.md#piping-objects-to-functions)。</span><span class="sxs-lookup"><span data-stu-id="09f5f-238">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

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

### <span data-ttu-id="09f5f-239">-End</span><span class="sxs-lookup"><span data-stu-id="09f5f-239">-End</span></span>

<span data-ttu-id="09f5f-240">指定在此 Cmdlet 處理所有輸入物件之後執行的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-240">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="09f5f-241">此腳本區塊只會針對整個管線執行一次。</span><span class="sxs-lookup"><span data-stu-id="09f5f-241">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="09f5f-242">如需有關區塊的詳細資訊 `end` ，請參閱 [about_Functions](about/about_functions.md#piping-objects-to-functions)。</span><span class="sxs-lookup"><span data-stu-id="09f5f-242">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

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

### <span data-ttu-id="09f5f-243">-InputObject</span><span class="sxs-lookup"><span data-stu-id="09f5f-243">-InputObject</span></span>

<span data-ttu-id="09f5f-244">指定輸入物件。</span><span class="sxs-lookup"><span data-stu-id="09f5f-244">Specifies the input objects.</span></span> <span data-ttu-id="09f5f-245">`ForEach-Object` 在每個輸入物件上執行腳本區塊或動作陳述式。</span><span class="sxs-lookup"><span data-stu-id="09f5f-245">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="09f5f-246">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="09f5f-246">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="09f5f-247">當您搭配使用 **inputobject** 參數與時 `ForEach-Object` ，不會將命令結果傳送至，而是 `ForEach-Object` 會將 **inputobject** 值視為單一物件。</span><span class="sxs-lookup"><span data-stu-id="09f5f-247">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="09f5f-248">即使值是命令結果的集合（例如），也是如此 `-InputObject (Get-Process)` 。</span><span class="sxs-lookup"><span data-stu-id="09f5f-248">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="09f5f-249">因為 **InputObject** 無法從物件的陣列或集合傳回個別屬性，所以如果您使用 `ForEach-Object` 在已定義屬性中具有特定值之物件的集合上執行作業，則建議您在 `ForEach-Object` 管線中使用，如本主題中的範例所示。</span><span class="sxs-lookup"><span data-stu-id="09f5f-249">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

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

### <span data-ttu-id="09f5f-250">-成員名稱</span><span class="sxs-lookup"><span data-stu-id="09f5f-250">-MemberName</span></span>

<span data-ttu-id="09f5f-251">指定要取得的屬性或要呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="09f5f-251">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="09f5f-252">允許使用萬用字元，但只有在產生的字串解析為唯一值時，才會運作。</span><span class="sxs-lookup"><span data-stu-id="09f5f-252">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="09f5f-253">例如，如果您執行 `Get-Process | ForEach -MemberName *Name` ，萬用字元模式會比對一個以上的成員，導致命令失敗。</span><span class="sxs-lookup"><span data-stu-id="09f5f-253">For example, if you run `Get-Process | ForEach -MemberName *Name`, the wildcard pattern matches more than one member causing the command to fail.</span></span>

<span data-ttu-id="09f5f-254">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="09f5f-254">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="09f5f-255">-Process</span><span class="sxs-lookup"><span data-stu-id="09f5f-255">-Process</span></span>

<span data-ttu-id="09f5f-256">指定在每個輸入物件上執行的操作。</span><span class="sxs-lookup"><span data-stu-id="09f5f-256">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="09f5f-257">此腳本區塊會針對管線中的每個物件執行。</span><span class="sxs-lookup"><span data-stu-id="09f5f-257">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="09f5f-258">如需有關區塊的詳細資訊 `process` ，請參閱 [about_Functions](about/about_functions.md#piping-objects-to-functions)。</span><span class="sxs-lookup"><span data-stu-id="09f5f-258">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="09f5f-259">當您將多個腳本區塊提供給 **Process** 參數時，第一個腳本區塊一律會對應至 `begin` 區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-259">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="09f5f-260">如果只有兩個腳本區塊，則第二個區塊會對應至 `process` 區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-260">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="09f5f-261">如果有三個或多個腳本區塊，則第一個腳本區塊一律會對應至 `begin` 區塊、最後一個區塊會對應至 `end` 區塊，而 between 中的區塊都會對應至 `process` 區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-261">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

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

### <span data-ttu-id="09f5f-262">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="09f5f-262">-RemainingScripts</span></span>

<span data-ttu-id="09f5f-263">指定 **Process** 參數未採用的所有腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-263">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="09f5f-264">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="09f5f-264">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="09f5f-265">-Parallel</span><span class="sxs-lookup"><span data-stu-id="09f5f-265">-Parallel</span></span>

<span data-ttu-id="09f5f-266">指定要用於平行處理輸入物件的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-266">Specifies the script block to be used for parallel processing of input objects.</span></span> <span data-ttu-id="09f5f-267">輸入描述操作的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-267">Enter a script block that describes the operation.</span></span>

<span data-ttu-id="09f5f-268">此參數是在 PowerShell 7.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="09f5f-268">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ParallelParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09f5f-269">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="09f5f-269">-ThrottleLimit</span></span>

<span data-ttu-id="09f5f-270">指定平行的腳本區塊數目。</span><span class="sxs-lookup"><span data-stu-id="09f5f-270">Specifies the number of script blocks that in parallel.</span></span> <span data-ttu-id="09f5f-271">除非執行中的腳本區塊計數低於 **ThrottleLimit** ，否則會封鎖輸入物件。</span><span class="sxs-lookup"><span data-stu-id="09f5f-271">Input objects are blocked until the running script block count falls below the **ThrottleLimit** .</span></span> <span data-ttu-id="09f5f-272">預設值是 `5`。</span><span class="sxs-lookup"><span data-stu-id="09f5f-272">The default value is `5`.</span></span>

<span data-ttu-id="09f5f-273">此參數是在 PowerShell 7.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="09f5f-273">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09f5f-274">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="09f5f-274">-TimeoutSeconds</span></span>

<span data-ttu-id="09f5f-275">指定等候所有輸入平行處理的秒數。</span><span class="sxs-lookup"><span data-stu-id="09f5f-275">Specifies the number of seconds to wait for all input to be processed in parallel.</span></span> <span data-ttu-id="09f5f-276">在指定的超時時間之後，就會停止所有執行中的腳本。</span><span class="sxs-lookup"><span data-stu-id="09f5f-276">After the specified timeout time, all running scripts are stopped.</span></span> <span data-ttu-id="09f5f-277">以及要處理的其餘輸入物件都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="09f5f-277">And any remaining input objects to be processed are ignored.</span></span> <span data-ttu-id="09f5f-278">預設值為 `0` 停用 timeout，而且 `ForEach-Object -Parallel` 可以無限期執行。</span><span class="sxs-lookup"><span data-stu-id="09f5f-278">Default value of `0` disables the timeout, and `ForEach-Object -Parallel` can run indefinitely.</span></span> <span data-ttu-id="09f5f-279">在命令列輸入<kbd>Ctrl</kbd> + <kbd>C</kbd>會停止執行 `ForEach-Object -Parallel` 中的命令。</span><span class="sxs-lookup"><span data-stu-id="09f5f-279">Typing <kbd>Ctrl</kbd>+<kbd>C</kbd> at the command line stops a running `ForEach-Object -Parallel` command.</span></span> <span data-ttu-id="09f5f-280">這個參數不能與 **AsJob** 參數一起使用。</span><span class="sxs-lookup"><span data-stu-id="09f5f-280">This parameter cannot be used along with the **AsJob** parameter.</span></span>

<span data-ttu-id="09f5f-281">此參數是在 PowerShell 7.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="09f5f-281">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09f5f-282">-UseNewRunspace</span><span class="sxs-lookup"><span data-stu-id="09f5f-282">-UseNewRunspace</span></span>

<span data-ttu-id="09f5f-283">使平行調用為每個迴圈反復專案建立新的執行時間，而不是從執行時間集區重複使用執行時間。</span><span class="sxs-lookup"><span data-stu-id="09f5f-283">Causes the parallel invocation to create a new runspace for every loop iteration instead of reusing runspaces from the runspace pool.</span></span>

<span data-ttu-id="09f5f-284">此參數是在 PowerShell 7.1 中引進</span><span class="sxs-lookup"><span data-stu-id="09f5f-284">This parameter was introduced in PowerShell 7.1</span></span>

```yml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09f5f-285">-AsJob</span><span class="sxs-lookup"><span data-stu-id="09f5f-285">-AsJob</span></span>

<span data-ttu-id="09f5f-286">使平行調用以 PowerShell 作業的形式執行。</span><span class="sxs-lookup"><span data-stu-id="09f5f-286">Causes the parallel invocation to run as a PowerShell job.</span></span> <span data-ttu-id="09f5f-287">傳回單一工作物件，而不是執行中腳本區塊的輸出。</span><span class="sxs-lookup"><span data-stu-id="09f5f-287">A single job object is returned instead of output from the running script blocks.</span></span> <span data-ttu-id="09f5f-288">工作物件包含每個執行之平行腳本區塊的子工作。</span><span class="sxs-lookup"><span data-stu-id="09f5f-288">The job object contains child jobs for each parallel script block that runs.</span></span> <span data-ttu-id="09f5f-289">所有 PowerShell 工作 Cmdlet 都可以使用此工作物件來監視執行狀態並取得資料。</span><span class="sxs-lookup"><span data-stu-id="09f5f-289">The job object can be used by all PowerShell job cmdlets, to monitor running state and retrieve data.</span></span>

<span data-ttu-id="09f5f-290">此參數是在 PowerShell 7.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="09f5f-290">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09f5f-291">-Confirm</span><span class="sxs-lookup"><span data-stu-id="09f5f-291">-Confirm</span></span>

<span data-ttu-id="09f5f-292">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="09f5f-292">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09f5f-293">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="09f5f-293">-WhatIf</span></span>

<span data-ttu-id="09f5f-294">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="09f5f-294">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="09f5f-295">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="09f5f-295">The cmdlet is not run.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="09f5f-296">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="09f5f-296">CommonParameters</span></span>

<span data-ttu-id="09f5f-297">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="09f5f-297">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="09f5f-298">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="09f5f-298">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="09f5f-299">輸入</span><span class="sxs-lookup"><span data-stu-id="09f5f-299">Inputs</span></span>

### <span data-ttu-id="09f5f-300">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="09f5f-300">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="09f5f-301">您可以使用管線將任何物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="09f5f-301">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="09f5f-302">輸出</span><span class="sxs-lookup"><span data-stu-id="09f5f-302">Outputs</span></span>

### <span data-ttu-id="09f5f-303">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="09f5f-303">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="09f5f-304">這個 Cmdlet 會傳回由輸入決定的物件。</span><span class="sxs-lookup"><span data-stu-id="09f5f-304">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="09f5f-305">備忘稿</span><span class="sxs-lookup"><span data-stu-id="09f5f-305">Notes</span></span>

- <span data-ttu-id="09f5f-306">此 `ForEach-Object` Cmdlet 的運作方式與 **foreach** 語句很類似，不同之處在于您無法使用管線將輸入傳送至 **foreach** 語句。</span><span class="sxs-lookup"><span data-stu-id="09f5f-306">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="09f5f-307">如需 **Foreach** 語句的詳細資訊，請參閱 [about_Foreach](./About/about_Foreach.md)。</span><span class="sxs-lookup"><span data-stu-id="09f5f-307">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="09f5f-308">從 PowerShell 4.0 開始， `Where` `ForEach` 已新增方法以與集合搭配使用。</span><span class="sxs-lookup"><span data-stu-id="09f5f-308">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="09f5f-309">您可以在這裡閱讀更多有關這些新方法的資訊 [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="09f5f-309">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

- <span data-ttu-id="09f5f-310">`ForEach-Object -Parallel`參數集使用 PowerShell 的內部 API 來執行每個腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-310">The `ForEach-Object -Parallel` parameter set uses PowerShell's internal API to run each script block.</span></span> <span data-ttu-id="09f5f-311">這會比 `ForEach-Object` 以連續處理正常執行的額外負荷更大。</span><span class="sxs-lookup"><span data-stu-id="09f5f-311">This is significantly more overhead than running `ForEach-Object` normally with sequential processing.</span></span> <span data-ttu-id="09f5f-312">使用 **平行** 執行的額外負荷（相較于腳本區塊所執行的工作）是很重要的。</span><span class="sxs-lookup"><span data-stu-id="09f5f-312">It is important to use **Parallel** where the overhead of running in parallel is small compared to work the script block performs.</span></span> <span data-ttu-id="09f5f-313">例如：</span><span class="sxs-lookup"><span data-stu-id="09f5f-313">For example:</span></span>

  - <span data-ttu-id="09f5f-314">多核心機器上的大量計算腳本</span><span class="sxs-lookup"><span data-stu-id="09f5f-314">Compute intensive scripts on multi-core machines</span></span>
  - <span data-ttu-id="09f5f-315">花費時間等待結果或執行檔案作業的腳本</span><span class="sxs-lookup"><span data-stu-id="09f5f-315">Scripts that spend time waiting for results or doing file operations</span></span>

  <span data-ttu-id="09f5f-316">使用 **Parallel** 參數可能會導致腳本執行速度比平常慢很多。</span><span class="sxs-lookup"><span data-stu-id="09f5f-316">Using the **Parallel** parameter can cause scripts to run much slower than normal.</span></span> <span data-ttu-id="09f5f-317">尤其是當平行腳本很簡單時。</span><span class="sxs-lookup"><span data-stu-id="09f5f-317">Especially if the parallel scripts are trivial.</span></span> <span data-ttu-id="09f5f-318">以 **平行** 方式進行實驗，以找出它的好處。</span><span class="sxs-lookup"><span data-stu-id="09f5f-318">Experiment with **Parallel** to discover where it can be beneficial.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="09f5f-319">`ForEach-Object -Parallel`參數集會在個別進程執行緒上平行執行腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="09f5f-319">The `ForEach-Object -Parallel` parameter set runs script blocks in parallel on separate process threads.</span></span> <span data-ttu-id="09f5f-320">`$using:`關鍵字允許從 Cmdlet 調用執行緒將變數參考傳遞至每個執行中的腳本區塊執行緒。</span><span class="sxs-lookup"><span data-stu-id="09f5f-320">The `$using:` keyword allows passing variable references from the cmdlet invocation thread to each running script block thread.</span></span> <span data-ttu-id="09f5f-321">因為腳本區塊會在不同的執行緒中執行，所以必須安全地使用以傳址方式傳遞的物件變數。</span><span class="sxs-lookup"><span data-stu-id="09f5f-321">Since the script blocks run in different threads, the object variables passed by reference must be used safely.</span></span> <span data-ttu-id="09f5f-322">一般而言，從未變更的參考物件讀取是安全的。</span><span class="sxs-lookup"><span data-stu-id="09f5f-322">Generally it is safe to read from referenced objects that don't change.</span></span> <span data-ttu-id="09f5f-323">但是，如果要修改物件狀態，您就必須使用安全線程物件，例如 .Net **system.object。並行** 類型 (查看範例 11) 。</span><span class="sxs-lookup"><span data-stu-id="09f5f-323">But if the object state is being modified then you must used thread safe objects, such as .Net **System.Collection.Concurrent** types (See Example 11).</span></span>

## <span data-ttu-id="09f5f-324">相關連結</span><span class="sxs-lookup"><span data-stu-id="09f5f-324">Related links</span></span>

[<span data-ttu-id="09f5f-325">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="09f5f-325">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="09f5f-326">Where-Object</span><span class="sxs-lookup"><span data-stu-id="09f5f-326">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="09f5f-327">Group-Object</span><span class="sxs-lookup"><span data-stu-id="09f5f-327">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="09f5f-328">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="09f5f-328">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="09f5f-329">New-Object</span><span class="sxs-lookup"><span data-stu-id="09f5f-329">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="09f5f-330">Select-Object</span><span class="sxs-lookup"><span data-stu-id="09f5f-330">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="09f5f-331">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="09f5f-331">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="09f5f-332">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="09f5f-332">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)