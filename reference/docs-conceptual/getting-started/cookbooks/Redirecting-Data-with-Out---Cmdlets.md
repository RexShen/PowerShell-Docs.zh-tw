---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用 Out Cmdlet 重新導向資料
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: 3ca7984e831a995e80cbd8a4d83ae9225c2a4f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="d4762-103">使用 Out-\* Cmdlet 重新導向資料</span><span class="sxs-lookup"><span data-stu-id="d4762-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="d4762-104">Windows PowerShell 提供幾個可讓您直接控制資料輸出的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d4762-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="d4762-105">這些 Cmdlet 有兩個重要特性：</span><span class="sxs-lookup"><span data-stu-id="d4762-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="d4762-106">首先，它們通常會將資料轉換成某種文字格式。</span><span class="sxs-lookup"><span data-stu-id="d4762-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="d4762-107">這樣做是因為它們會將資料輸出至需要文字輸入的系統元件，</span><span class="sxs-lookup"><span data-stu-id="d4762-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="d4762-108">所以必須以文字表示物件。</span><span class="sxs-lookup"><span data-stu-id="d4762-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="d4762-109">因此，文字會格式化為您在 Windows PowerShell 主控台視窗中看到的樣子。</span><span class="sxs-lookup"><span data-stu-id="d4762-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="d4762-110">其次，這些 Cmdlet 使用 Windows PowerShell 動詞 **Out**，因為它們會將資訊從 Windows PowerShell 送出至其他位置。</span><span class="sxs-lookup"><span data-stu-id="d4762-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="d4762-111">**Out-Host** Cmdlet 也不例外︰主機視窗顯示會在 Windows PowerShell 之外。</span><span class="sxs-lookup"><span data-stu-id="d4762-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="d4762-112">這點很重要，因為當資料從 Windows PowerShell 送出時，實際上會遭到移除。</span><span class="sxs-lookup"><span data-stu-id="d4762-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="d4762-113">如果您嘗試建立管線將資料分頁至主機視窗，然後嘗試將其格式化為清單，就會看到這種情況，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="d4762-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="d4762-114">您可能預期命令會以清單格式分頁顯示處理程序資訊。</span><span class="sxs-lookup"><span data-stu-id="d4762-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="d4762-115">相反地，它會顯示預設的表格式清單︰</span><span class="sxs-lookup"><span data-stu-id="d4762-115">Instead, it displays the default tabular list:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="d4762-116">**Out-Host** Cmdlet 會將資料直接傳送至主控台，因此 **Format-List** 命令永遠不會收到需要格式化的項目。</span><span class="sxs-lookup"><span data-stu-id="d4762-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="d4762-117">建構此命令的正確方式是將 **Out-Host** Cmdlet 置於管線結尾，如下所示。</span><span class="sxs-lookup"><span data-stu-id="d4762-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="d4762-118">這會格式化清單中的處理程序資料，再將其分頁顯示。</span><span class="sxs-lookup"><span data-stu-id="d4762-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="d4762-119">這適用於所有 **Out** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d4762-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="d4762-120">**Out** Cmdlet 一律會出現在管線結尾處。</span><span class="sxs-lookup"><span data-stu-id="d4762-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="d4762-121">所有 **Out** Cmdlet 都會使用對主控台視窗有效的格式 (包括行的長度限制)，將輸出轉譯成文字。</span><span class="sxs-lookup"><span data-stu-id="d4762-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="d4762-122">分頁主控台輸出 (Out-Host)</span><span class="sxs-lookup"><span data-stu-id="d4762-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="d4762-123">根據預設，Windows PowerShell 會將資料傳送至主機視窗，這與 Out-Host Cmdlet 的功能完全相同。</span><span class="sxs-lookup"><span data-stu-id="d4762-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="d4762-124">如前所述，Out-Host Cmdlet 主要用於將資料分頁。</span><span class="sxs-lookup"><span data-stu-id="d4762-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="d4762-125">例如，下列命令會使用 Out-Host 將 Get-Command Cmdlet 的輸出分頁︰</span><span class="sxs-lookup"><span data-stu-id="d4762-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="d4762-126">您也可以使用 **more** 函式將資料分頁。</span><span class="sxs-lookup"><span data-stu-id="d4762-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="d4762-127">在 Windows PowerShell 中，**more** 是呼叫 **Out-Host -Paging** 的函式。</span><span class="sxs-lookup"><span data-stu-id="d4762-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="d4762-128">下列命令示範如何使用 **more** 函式將 Get-Command 的輸出分頁︰</span><span class="sxs-lookup"><span data-stu-id="d4762-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="d4762-129">如果您包含一或多個檔案名稱作為 more 函式的引數，該函式會讀取指定的檔案並將其內容分頁至主機︰</span><span class="sxs-lookup"><span data-stu-id="d4762-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="d4762-130">捨棄輸出 (Out-Null)</span><span class="sxs-lookup"><span data-stu-id="d4762-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="d4762-131">**Out-Null** Cmdlet 設計成可立即捨棄任何收到的輸入。</span><span class="sxs-lookup"><span data-stu-id="d4762-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="d4762-132">這在捨棄因執行命令的副作用所得到的不必要資料時會很有用。</span><span class="sxs-lookup"><span data-stu-id="d4762-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="d4762-133">輸入下列命令時，命令不會傳回任何項目︰</span><span class="sxs-lookup"><span data-stu-id="d4762-133">When type the following command, you do not get anything back from the command:</span></span>

```powreshell
Get-Command | Out-Null
```

<span data-ttu-id="d4762-134">**Out-Null** Cmdlet 不會捨棄錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="d4762-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="d4762-135">例如，如果您輸入下列命令，會顯示訊息通知您 Windows PowerShell 無法辨識 'Is-NotACommand'：</span><span class="sxs-lookup"><span data-stu-id="d4762-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="d4762-136">列印資料 (Out-Printer)</span><span class="sxs-lookup"><span data-stu-id="d4762-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="d4762-137">您可以使用 **Out-Printer** Cmdlet 列印資料。</span><span class="sxs-lookup"><span data-stu-id="d4762-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="d4762-138">如果您未提供印表機名稱，**Out-Printer** Cmdlet 會使用預設印表機。</span><span class="sxs-lookup"><span data-stu-id="d4762-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="d4762-139">您可以使用任何 Windows 印表機，方法是指定其顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="d4762-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="d4762-140">您不需要任何印表機連接埠對應，或甚至是真正的實體印表機。</span><span class="sxs-lookup"><span data-stu-id="d4762-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="d4762-141">例如，如果您已安裝 Microsoft Office Document Imaging 工具，您可以輸入下列命令將資料傳送至影像檔︰</span><span class="sxs-lookup"><span data-stu-id="d4762-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="d4762-142">儲存資料 (Out-File)</span><span class="sxs-lookup"><span data-stu-id="d4762-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="d4762-143">您可以使用 **Out-File** Cmdlet 將輸出傳送至檔案，而不是主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="d4762-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="d4762-144">下列命令列會將處理程序清單傳送至檔案 **C:\\temp\\processlist.txt**：</span><span class="sxs-lookup"><span data-stu-id="d4762-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="d4762-145">如果您習慣於傳統輸出重新導向，使用 **Out-File** Cmdlet 的結果可能不如您的預期。</span><span class="sxs-lookup"><span data-stu-id="d4762-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="d4762-146">若要了解其行為，您必須知道 **Out-File** Cmdlet 操作所在的內容。</span><span class="sxs-lookup"><span data-stu-id="d4762-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="d4762-147">**Out-File** Cmdlet 預設會建立 Unicode 檔案。</span><span class="sxs-lookup"><span data-stu-id="d4762-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="d4762-148">從長遠看來，這是最佳的預設值，但這表示預期 ASCII 檔案的工具將無法以預設輸出格式正常運作。</span><span class="sxs-lookup"><span data-stu-id="d4762-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="d4762-149">您可以使用 **Encoding** 參數，將預設輸出格式變更為 ASCII︰</span><span class="sxs-lookup"><span data-stu-id="d4762-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="d4762-150">**Out-File** 會格式化檔案內容，使其看起來像是主控台輸出。</span><span class="sxs-lookup"><span data-stu-id="d4762-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="d4762-151">這會導致輸出和在大部分情況下的主控台視窗中一樣被截斷。</span><span class="sxs-lookup"><span data-stu-id="d4762-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="d4762-152">例如，如果您執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d4762-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="d4762-153">輸出看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="d4762-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="d4762-154">若要取得不會強制行換行以符合螢幕寬度的輸出，您可以使用**Width** 參數指定行的寬度。</span><span class="sxs-lookup"><span data-stu-id="d4762-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="d4762-155">因為 **Width** 是 32 位元整數參數，所有可以有最大值 2147483647。</span><span class="sxs-lookup"><span data-stu-id="d4762-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="d4762-156">請輸入下列命令將行的寬度設定為此最大值︰</span><span class="sxs-lookup"><span data-stu-id="d4762-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="d4762-157">當您想要以輸出主控台上的顯示格式來儲存輸出時，**Out-File** Cmdlet 會很有用。</span><span class="sxs-lookup"><span data-stu-id="d4762-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="d4762-158">如需更細微地控制輸出格式，您需要更進階的工具。</span><span class="sxs-lookup"><span data-stu-id="d4762-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="d4762-159">我們將在下一章探討這些工具，以及有關物件操作的一些詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d4762-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>