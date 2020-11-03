---
description: 說明如何將 PowerShell 的輸出重新導向至文字檔。
keywords: PowerShell，Cmdlet
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: 7e6dcadc3bcabd4dc0521a158db87ca2bba41af8
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208407"
---
# <a name="about-redirection"></a><span data-ttu-id="7cf2d-104">關於重新導向</span><span class="sxs-lookup"><span data-stu-id="7cf2d-104">About Redirection</span></span>

## <a name="short-description"></a><span data-ttu-id="7cf2d-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="7cf2d-105">Short description</span></span>
<span data-ttu-id="7cf2d-106">說明如何將 PowerShell 的輸出重新導向至文字檔。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-106">Explains how to redirect output from PowerShell to text files.</span></span>

## <a name="long-description"></a><span data-ttu-id="7cf2d-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="7cf2d-107">Long description</span></span>

<span data-ttu-id="7cf2d-108">根據預設，PowerShell 會將輸出傳送至 PowerShell 主機。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-108">By default, PowerShell sends output to the PowerShell host.</span></span> <span data-ttu-id="7cf2d-109">這通常是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-109">Usually this is the console application.</span></span> <span data-ttu-id="7cf2d-110">不過，您可以將輸出導向文字檔，也可以將錯誤輸出重新導向至一般輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-110">However, you can direct the output to a text file, and you can redirect error output to the regular output stream.</span></span>

<span data-ttu-id="7cf2d-111">您可以使用下列方法來重新導向輸出：</span><span class="sxs-lookup"><span data-stu-id="7cf2d-111">You can use the following methods to redirect output:</span></span>

- <span data-ttu-id="7cf2d-112">使用 `Out-File` Cmdlet 將命令輸出傳送至文字檔。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-112">Use the `Out-File` cmdlet, which sends command output to a text file.</span></span>
  <span data-ttu-id="7cf2d-113">一般來說， `Out-File` 當您需要使用它的參數（例如 `Encoding` 、 `Force` 、 `Width` 或參數）時，您會使用 Cmdlet `NoClobber` 。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-113">Typically, you use the `Out-File` cmdlet when you need to use its parameters, such as the `Encoding`, `Force`, `Width`, or `NoClobber` parameters.</span></span>

- <span data-ttu-id="7cf2d-114">使用 `Tee-Object` Cmdlet，此 Cmdlet 會將命令輸出傳送至文字檔，然後將它傳送至管線。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-114">Use the `Tee-Object` cmdlet, which sends command output to a text file and then sends it to the pipeline.</span></span>

- <span data-ttu-id="7cf2d-115">使用 PowerShell 重新導向運算子。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-115">Use the PowerShell redirection operators.</span></span> <span data-ttu-id="7cf2d-116">搭配使用重新導向運算子與檔案目標，在功能上相當於傳送到 `Out-File` 無額外參數的管道。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-116">Using the redirection operator with a file target is functionally equivalent to piping to `Out-File` with no extra parameters.</span></span>

<span data-ttu-id="7cf2d-117">如需資料流程的詳細資訊，請參閱 [about_Output_Streams](about_Output_Streams.md)。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-117">For more information about streams, see [about_Output_Streams](about_Output_Streams.md).</span></span>

### <a name="redirectable-output-streams"></a><span data-ttu-id="7cf2d-118">可重新導向輸出資料流程</span><span class="sxs-lookup"><span data-stu-id="7cf2d-118">Redirectable output streams</span></span>

<span data-ttu-id="7cf2d-119">PowerShell 支援下列輸出資料流程的重新導向。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-119">PowerShell supports redirection of the following output streams.</span></span>

| <span data-ttu-id="7cf2d-120">流#</span><span class="sxs-lookup"><span data-stu-id="7cf2d-120">Stream #</span></span> |      <span data-ttu-id="7cf2d-121">Description</span><span class="sxs-lookup"><span data-stu-id="7cf2d-121">Description</span></span>       | <span data-ttu-id="7cf2d-122">引進于</span><span class="sxs-lookup"><span data-stu-id="7cf2d-122">Introduced in</span></span>  |    <span data-ttu-id="7cf2d-123">Write Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7cf2d-123">Write Cmdlet</span></span>     |
| -------- | ---------------------- | -------------- | ------------------- |
| <span data-ttu-id="7cf2d-124">1</span><span class="sxs-lookup"><span data-stu-id="7cf2d-124">1</span></span>        | <span data-ttu-id="7cf2d-125">**成功** 流</span><span class="sxs-lookup"><span data-stu-id="7cf2d-125">**Success** Stream</span></span>     | <span data-ttu-id="7cf2d-126">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="7cf2d-126">PowerShell 2.0</span></span> | `Write-Output`      |
| <span data-ttu-id="7cf2d-127">2</span><span class="sxs-lookup"><span data-stu-id="7cf2d-127">2</span></span>        | <span data-ttu-id="7cf2d-128">**錯誤** 流</span><span class="sxs-lookup"><span data-stu-id="7cf2d-128">**Error** Stream</span></span>       | <span data-ttu-id="7cf2d-129">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="7cf2d-129">PowerShell 2.0</span></span> | `Write-Error`       |
| <span data-ttu-id="7cf2d-130">3</span><span class="sxs-lookup"><span data-stu-id="7cf2d-130">3</span></span>        | <span data-ttu-id="7cf2d-131">**警告** 流</span><span class="sxs-lookup"><span data-stu-id="7cf2d-131">**Warning** Stream</span></span>     | <span data-ttu-id="7cf2d-132">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="7cf2d-132">PowerShell 3.0</span></span> | `Write-Warning`     |
| <span data-ttu-id="7cf2d-133">4</span><span class="sxs-lookup"><span data-stu-id="7cf2d-133">4</span></span>        | <span data-ttu-id="7cf2d-134">**詳細** 資訊流</span><span class="sxs-lookup"><span data-stu-id="7cf2d-134">**Verbose** Stream</span></span>     | <span data-ttu-id="7cf2d-135">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="7cf2d-135">PowerShell 3.0</span></span> | `Write-Verbose`     |
| <span data-ttu-id="7cf2d-136">5</span><span class="sxs-lookup"><span data-stu-id="7cf2d-136">5</span></span>        | <span data-ttu-id="7cf2d-137">**Debug** 流</span><span class="sxs-lookup"><span data-stu-id="7cf2d-137">**Debug** Stream</span></span>       | <span data-ttu-id="7cf2d-138">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="7cf2d-138">PowerShell 3.0</span></span> | `Write-Debug`       |
| <span data-ttu-id="7cf2d-139">6</span><span class="sxs-lookup"><span data-stu-id="7cf2d-139">6</span></span>        | <span data-ttu-id="7cf2d-140">**資訊** 流</span><span class="sxs-lookup"><span data-stu-id="7cf2d-140">**Information** Stream</span></span> | <span data-ttu-id="7cf2d-141">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7cf2d-141">PowerShell 5.0</span></span> | `Write-Information` |
| *        | <span data-ttu-id="7cf2d-142">所有資料流程</span><span class="sxs-lookup"><span data-stu-id="7cf2d-142">All Streams</span></span>            | <span data-ttu-id="7cf2d-143">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="7cf2d-143">PowerShell 3.0</span></span> |                     |

> [!NOTE]
> <span data-ttu-id="7cf2d-144">PowerShell 中也有 **進度** 串流，但不支援重新導向。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-144">There is also a **Progress** stream in PowerShell, but it does not support redirection.</span></span>

### <a name="powershell-redirection-operators"></a><span data-ttu-id="7cf2d-145">PowerShell 重新導向操作員</span><span class="sxs-lookup"><span data-stu-id="7cf2d-145">PowerShell redirection operators</span></span>

<span data-ttu-id="7cf2d-146">PowerShell 重新導向運算子如下所示，其中 `n` 代表資料流程號碼。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-146">The PowerShell redirection operators are as follows, where `n` represents the stream number.</span></span> <span data-ttu-id="7cf2d-147">如果未指定任何資料流程，則 **成功** 的資料流程 ( `1` ) 為預設值。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-147">The **Success** stream ( `1` ) is the default if no stream is specified.</span></span>

| <span data-ttu-id="7cf2d-148">運算子</span><span class="sxs-lookup"><span data-stu-id="7cf2d-148">Operator</span></span> |                         <span data-ttu-id="7cf2d-149">描述</span><span class="sxs-lookup"><span data-stu-id="7cf2d-149">Description</span></span>                         | <span data-ttu-id="7cf2d-150">Syntax</span><span class="sxs-lookup"><span data-stu-id="7cf2d-150">Syntax</span></span> |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | <span data-ttu-id="7cf2d-151">將指定的資料流程傳送至檔案。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-151">Send specified stream to a file.</span></span>                            | `n>`   |
| `>>`     | <span data-ttu-id="7cf2d-152">將指定的資料流程 **附加** 至檔案。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-152">**Append** specified stream to a file.</span></span>                      | `n>>`  |
| `>&1`    | <span data-ttu-id="7cf2d-153">將指定的資料流程重新 _導向_ 至 **成功** 資料流程。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-153">_Redirects_ the specified stream to the **Success** stream.</span></span> | `n>&1` |

> [!NOTE]
> <span data-ttu-id="7cf2d-154">與某些 Unix shell 不同的是，您只能將其他資料流程重新導向至 **成功** 串流。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-154">Unlike some Unix shells, you can only redirect other streams to the **Success** stream.</span></span>

## <a name="examples"></a><span data-ttu-id="7cf2d-155">範例</span><span class="sxs-lookup"><span data-stu-id="7cf2d-155">Examples</span></span>

### <a name="example-1-redirect-errors-and-output-to-a-file"></a><span data-ttu-id="7cf2d-156">範例1：將錯誤和輸出重新導向至檔案</span><span class="sxs-lookup"><span data-stu-id="7cf2d-156">Example 1: Redirect errors and output to a file</span></span>

<span data-ttu-id="7cf2d-157">此範例 `dir` 會在一個將成功的專案上執行，另一個則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-157">This example runs `dir` on one item that will succeed, and one that will error.</span></span>

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

<span data-ttu-id="7cf2d-158">它會使用 `2>&1` 將 **錯誤** 資料流程重新導向至 **成功** 資料流程，並將 `>` 結果 **成功** 資料流程傳送至名為 `dir.log`</span><span class="sxs-lookup"><span data-stu-id="7cf2d-158">It uses `2>&1` to redirect the **Error** stream to the **Success** stream, and `>` to send the resultant **Success** stream to a file called `dir.log`</span></span>

### <a name="example-2-send-all-success-stream-data-to-a-file"></a><span data-ttu-id="7cf2d-159">範例2：將所有成功的資料流程資料傳送至檔案</span><span class="sxs-lookup"><span data-stu-id="7cf2d-159">Example 2: Send all Success stream data to a file</span></span>

<span data-ttu-id="7cf2d-160">此範例會將所有 **成功** 的資料流程資料傳送至名為的檔案 `script.log` 。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-160">This example sends all **Success** stream data to a file called `script.log`.</span></span>

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a><span data-ttu-id="7cf2d-161">範例3：將成功、警告和錯誤資料流程傳送至檔案</span><span class="sxs-lookup"><span data-stu-id="7cf2d-161">Example 3: Send Success, Warning, and Error streams to a file</span></span>

<span data-ttu-id="7cf2d-162">這個範例會示範如何結合重新導向運算子，以達成所需的結果。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-162">This example shows how you can combine redirection operators to achieve a desired result.</span></span>

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > P:\Temp\redirection.log
```

- <span data-ttu-id="7cf2d-163">`3>&1` 將 **警告** 資料流程重新導向至 **成功** 資料流程。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-163">`3>&1` redirects the **Warning** stream to the **Success** stream.</span></span>
- <span data-ttu-id="7cf2d-164">`2>&1` 將 **錯誤** 資料流程重新導向至 **成功** 串流， (現在也包含所有 **警告** 資料流程資料) </span><span class="sxs-lookup"><span data-stu-id="7cf2d-164">`2>&1` redirects the **Error** stream to the **Success** stream (which also now includes all **Warning** stream data)</span></span>
- <span data-ttu-id="7cf2d-165">`>` 重新導向 **成功** 資料流程 (現在包含 **警告** 和 **錯誤** 資料流程) 至名為的檔案 `C:\temp\redirection.log`) </span><span class="sxs-lookup"><span data-stu-id="7cf2d-165">`>` redirects the **Success** stream (which now contains both **Warning** and **Error** streams) to a file called `C:\temp\redirection.log`)</span></span>

### <a name="example-4-redirect-all-streams-to-a-file"></a><span data-ttu-id="7cf2d-166">範例4：將所有資料流程重新導向至檔案</span><span class="sxs-lookup"><span data-stu-id="7cf2d-166">Example 4: Redirect all streams to a file</span></span>

<span data-ttu-id="7cf2d-167">此範例會將呼叫之腳本的所有資料流程輸出傳送 `script.ps1` 給稱為 `script.log`</span><span class="sxs-lookup"><span data-stu-id="7cf2d-167">This example sends all streams output from a script called `script.ps1` to a file called `script.log`</span></span>

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a><span data-ttu-id="7cf2d-168">範例5：隱藏所有 Write-Host 和資訊串流資料</span><span class="sxs-lookup"><span data-stu-id="7cf2d-168">Example 5: Suppress all Write-Host and Information stream data</span></span>

<span data-ttu-id="7cf2d-169">此範例會隱藏所有資訊串流資料。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-169">This example suppresses all information stream data.</span></span> <span data-ttu-id="7cf2d-170">若要閱讀 **資訊** 串流 Cmdlet 的詳細資訊，請參閱 [寫入主機](xref:Microsoft.PowerShell.Utility.Write-Host) 和 [寫入資訊](xref:Microsoft.PowerShell.Utility.Write-Information)</span><span class="sxs-lookup"><span data-stu-id="7cf2d-170">To read more about **Information** stream cmdlets, see [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) and [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)</span></span>

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a><span data-ttu-id="7cf2d-171">範例6：顯示動作喜好設定的效果</span><span class="sxs-lookup"><span data-stu-id="7cf2d-171">Example 6: Show the effect of Action Preferences</span></span>

<span data-ttu-id="7cf2d-172">動作喜好設定變數和參數可以變更寫入特定資料流程的內容。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-172">Action Preference variables and parameters can change what gets written to a particular stream.</span></span> <span data-ttu-id="7cf2d-173">此範例中的腳本會顯示的值 `$ErrorActionPreference` 會如何影響寫入至 **錯誤** 資料流程的內容。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-173">The script in this example shows how the value of `$ErrorActionPreference` affects what gets written to the **Error** stream.</span></span>

```powershell
$ErrorActionPreference = 'Continue'
$ErrorActionPreference > log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'SilentlyContinue'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Stop'
$ErrorActionPreference >> log.txt
Try {
    get-item /not-here 2>&1 >> log.txt
}
catch {
    "`tError caught!" >> log.txt
}
$ErrorActionPreference = 'Ignore'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Inquire'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Continue'
```

<span data-ttu-id="7cf2d-174">當我們執行此腳本時，當設定為時，會出現提示 `$ErrorActionPreference` `Inquire` 。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-174">When we run this script we get prompted when `$ErrorActionPreference` is set to `Inquire`.</span></span>

```powershell
PS C:\temp> .\test.ps1

Confirm
Cannot find path 'C:\not-here' because it does not exist.
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): H
Get-Item: C:\temp\test.ps1:23
Line |
  23 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The running command stopped because the user selected the Stop option.
```

<span data-ttu-id="7cf2d-175">當我們檢查記錄檔時，會看到下列內容：</span><span class="sxs-lookup"><span data-stu-id="7cf2d-175">When we examine the log file we see the following:</span></span>

```
PS C:\temp> Get-Content .\log.txt
Continue

Get-Item: C:\temp\test.ps1:3
Line |
   3 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | Cannot find path 'C:\not-here' because it does not exist.

SilentlyContinue
Stop
    Error caught!
Ignore
Inquire
```

## <a name="notes"></a><span data-ttu-id="7cf2d-176">備忘稿</span><span class="sxs-lookup"><span data-stu-id="7cf2d-176">Notes</span></span>

<span data-ttu-id="7cf2d-177">未附加資料 (`>` 和 `n>`) 會覆寫指定檔案的目前內容而不會發出警告的重新導向運算子。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-177">The redirection operators that do not append data (`>` and `n>`) overwrite the current contents of the specified file without warning.</span></span>

<span data-ttu-id="7cf2d-178">但是，如果檔案是唯讀、隱藏或系統檔案，則重新導向 **會失敗** 。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-178">However, if the file is a read-only, hidden, or system file, the redirection **fails** .</span></span> <span data-ttu-id="7cf2d-179">附加重新導向運算子 (`>>` 和 `n>>`) 不會寫入至唯讀檔案，但是會將內容附加至系統或隱藏的檔案。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-179">The append redirection operators (`>>` and `n>>`) do not write to a read-only file, but they append content to a system or hidden file.</span></span>

<span data-ttu-id="7cf2d-180">若要強制將內容重新導向至唯讀、隱藏或系統檔案，請使用 `Out-File` Cmdlet 搭配其 `Force` 參數。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-180">To force the redirection of content to a read-only, hidden, or system file, use the `Out-File` cmdlet with its `Force` parameter.</span></span>

<span data-ttu-id="7cf2d-181">當您寫入檔案時，重新導向運算子會使用 `UTF8NoBOM` 編碼。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-181">When you are writing to files, the redirection operators use `UTF8NoBOM` encoding.</span></span> <span data-ttu-id="7cf2d-182">如果檔案具有不同的編碼方式，輸出的格式可能會不正確。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-182">If the file has a different encoding, the output might not be formatted correctly.</span></span> <span data-ttu-id="7cf2d-183">若要寫入具有不同編碼的檔案，請使用 `Out-File` Cmdlet 搭配其 `Encoding` 參數。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-183">To write to files with a different encoding, use the `Out-File` cmdlet with its `Encoding` parameter.</span></span>

### <a name="potential-confusion-with-comparison-operators"></a><span data-ttu-id="7cf2d-184">比較運算子的潛在混淆</span><span class="sxs-lookup"><span data-stu-id="7cf2d-184">Potential confusion with comparison operators</span></span>

<span data-ttu-id="7cf2d-185">`>`運算子不會與[大於](about_Comparison_Operators.md#-gt)比較運算子混淆 (通常表示為 `>` 其他程式設計語言) 。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-185">The `>` operator is not to be confused with the [Greater-than](about_Comparison_Operators.md#-gt) comparison operator (often denoted as `>` in other programming languages).</span></span>

<span data-ttu-id="7cf2d-186">根據所比較的物件而定，使用的輸出 `>` 可能會是正確的 (因為36不大於 42) 。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-186">Depending on the objects being compared, the output using `>` can appear to be correct (because 36 is not greater than 42).</span></span>

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

<span data-ttu-id="7cf2d-187">不過，檢查本機檔案系統可以看到 `42` 已寫入的檔案，以及內容 `36` 。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-187">However, a check of the local filesystem can see that a file called `42` was written, with the contents `36`.</span></span>

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

<span data-ttu-id="7cf2d-188">嘗試使用反向比較 `<` (小於) ，會產生系統錯誤：</span><span class="sxs-lookup"><span data-stu-id="7cf2d-188">Attempting to use the reverse comparison `<` (less than), yields a system error:</span></span>

```powershell
PS> if (36 < 42) { "true" } else { "false" }
At line:1 char:8
+ if (36 < 42) { "true" } else { "false" }
+        ~
The '<' operator is reserved for future use.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : RedirectionNotSupported
```

<span data-ttu-id="7cf2d-189">如果數值比較是必要的作業， `-lt` 則 `-gt` 應該使用。</span><span class="sxs-lookup"><span data-stu-id="7cf2d-189">If numeric comparison is the required operation, `-lt` and `-gt` should be used.</span></span> <span data-ttu-id="7cf2d-190">請參閱： [ `-gt` 比較運算子](about_Comparison_Operators.md#-gt)</span><span class="sxs-lookup"><span data-stu-id="7cf2d-190">See: [`-gt` Comparison Operator](about_Comparison_Operators.md#-gt)</span></span>

## <a name="see-also"></a><span data-ttu-id="7cf2d-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cf2d-191">See also</span></span>

- [<span data-ttu-id="7cf2d-192">Out-File</span><span class="sxs-lookup"><span data-stu-id="7cf2d-192">Out-File</span></span>](xref:Microsoft.PowerShell.Utility.Out-File)
- [<span data-ttu-id="7cf2d-193">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="7cf2d-193">Tee-Object</span></span>](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [<span data-ttu-id="7cf2d-194">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="7cf2d-194">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="7cf2d-195">Write-Error</span><span class="sxs-lookup"><span data-stu-id="7cf2d-195">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)
- [<span data-ttu-id="7cf2d-196">Write-Host</span><span class="sxs-lookup"><span data-stu-id="7cf2d-196">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)
- [<span data-ttu-id="7cf2d-197">Write-Information</span><span class="sxs-lookup"><span data-stu-id="7cf2d-197">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)
- [<span data-ttu-id="7cf2d-198">Write-Output</span><span class="sxs-lookup"><span data-stu-id="7cf2d-198">Write-Output</span></span>](xref:Microsoft.PowerShell.Utility.Write-Output)
- [<span data-ttu-id="7cf2d-199">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="7cf2d-199">Write-Progress</span></span>](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [<span data-ttu-id="7cf2d-200">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="7cf2d-200">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [<span data-ttu-id="7cf2d-201">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="7cf2d-201">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [<span data-ttu-id="7cf2d-202">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="7cf2d-202">about_Output_Streams</span></span>](about_Output_Streams.md)
- [<span data-ttu-id="7cf2d-203">about_Operators</span><span class="sxs-lookup"><span data-stu-id="7cf2d-203">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="7cf2d-204">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="7cf2d-204">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="7cf2d-205">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="7cf2d-205">about_Path_Syntax</span></span>](about_Path_Syntax.md)
