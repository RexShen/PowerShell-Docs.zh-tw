---
description: 在 PowerShell 中將命令結合成管線
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: 1be86d4ff65dfc36a85eac32814c76175157aa4d
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208628"
---
# <a name="about-pipelines"></a><span data-ttu-id="86e3c-104">關於管線</span><span class="sxs-lookup"><span data-stu-id="86e3c-104">About Pipelines</span></span>

## <a name="short-description"></a><span data-ttu-id="86e3c-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="86e3c-105">Short description</span></span>

<span data-ttu-id="86e3c-106">在 PowerShell 中將命令結合成管線</span><span class="sxs-lookup"><span data-stu-id="86e3c-106">Combining commands into pipelines in the PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="86e3c-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="86e3c-107">Long description</span></span>

<span data-ttu-id="86e3c-108">管線是管線運算子所連接的一連串命令 (`|`)  (ASCII 124) 。</span><span class="sxs-lookup"><span data-stu-id="86e3c-108">A pipeline is a series of commands connected by pipeline operators (`|`) (ASCII 124).</span></span> <span data-ttu-id="86e3c-109">每個管線運算子都會將上述命令的結果傳送至下一個命令。</span><span class="sxs-lookup"><span data-stu-id="86e3c-109">Each pipeline operator sends the results of the preceding command to the next command.</span></span>

<span data-ttu-id="86e3c-110">第一個命令的輸出可以傳送給第二個命令的輸入，以便進行處理。</span><span class="sxs-lookup"><span data-stu-id="86e3c-110">The output of the first command can be sent for processing as input to the second command.</span></span> <span data-ttu-id="86e3c-111">此外，也可以將輸出傳送至另一個命令。</span><span class="sxs-lookup"><span data-stu-id="86e3c-111">And that output can be sent to yet another command.</span></span> <span data-ttu-id="86e3c-112">結果是由一系列簡單命令組成的複雜命令鏈或 _管線_ 。</span><span class="sxs-lookup"><span data-stu-id="86e3c-112">The result is a complex command chain or _pipeline_ that is composed of a series of simple commands.</span></span>

<span data-ttu-id="86e3c-113">例如，套用至物件的</span><span class="sxs-lookup"><span data-stu-id="86e3c-113">For example,</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="86e3c-114">在此範例中，發出的物件 `Command-1` 會傳送至 `Command-2` 。</span><span class="sxs-lookup"><span data-stu-id="86e3c-114">In this example, the objects that `Command-1` emits are sent to `Command-2`.</span></span>
<span data-ttu-id="86e3c-115">`Command-2` 處理物件，並將它們傳送至 `Command-3` 。</span><span class="sxs-lookup"><span data-stu-id="86e3c-115">`Command-2` processes the objects and sends them to `Command-3`.</span></span> <span data-ttu-id="86e3c-116">`Command-3` 處理物件，並將它們傳送至管線。</span><span class="sxs-lookup"><span data-stu-id="86e3c-116">`Command-3` processes the objects and send them down the pipeline.</span></span> <span data-ttu-id="86e3c-117">因為管線中沒有其他命令，所以會在主控台顯示結果。</span><span class="sxs-lookup"><span data-stu-id="86e3c-117">Because there are no more commands in the pipeline, the results are displayed at the console.</span></span>

<span data-ttu-id="86e3c-118">在管線中，命令會依序由左至右處理。</span><span class="sxs-lookup"><span data-stu-id="86e3c-118">In a pipeline, the commands are processed in order from left to right.</span></span> <span data-ttu-id="86e3c-119">處理會以單一作業的方式處理，並在產生輸出時顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="86e3c-119">The processing is handled as a single operation and output is displayed as it's generated.</span></span>

<span data-ttu-id="86e3c-120">以下是一個簡單範例。</span><span class="sxs-lookup"><span data-stu-id="86e3c-120">Here is a simple example.</span></span> <span data-ttu-id="86e3c-121">下列命令會取得「記事本」處理常式，然後將它停止。</span><span class="sxs-lookup"><span data-stu-id="86e3c-121">The following command gets the Notepad process and then stops it.</span></span>

<span data-ttu-id="86e3c-122">例如，套用至物件的</span><span class="sxs-lookup"><span data-stu-id="86e3c-122">For example,</span></span>

```powershell
Get-Process notepad | Stop-Process
```

<span data-ttu-id="86e3c-123">第一個命令會使用 `Get-Process` Cmdlet 來取得代表記事本進程的物件。</span><span class="sxs-lookup"><span data-stu-id="86e3c-123">The first command uses the `Get-Process` cmdlet to get an object representing the Notepad process.</span></span> <span data-ttu-id="86e3c-124">它使用管線運算子 (`|`) 將處理常式物件傳送至 `Stop-Process` Cmdlet，此 Cmdlet 會停止「記事本」處理常式。</span><span class="sxs-lookup"><span data-stu-id="86e3c-124">It uses a pipeline operator (`|`) to send the process object to the `Stop-Process` cmdlet, which stops the Notepad process.</span></span> <span data-ttu-id="86e3c-125">請注意，此 `Stop-Process` 命令沒有 **Name** 或 **ID** 參數來指定處理常式，因為指定的進程是透過管線提交。</span><span class="sxs-lookup"><span data-stu-id="86e3c-125">Notice that the `Stop-Process` command doesn't have a **Name** or **ID** parameter to specify the process, because the specified process is submitted through the pipeline.</span></span>

<span data-ttu-id="86e3c-126">此管線範例會取得目前目錄中的文字檔、只選取超過10000個位元組的檔案、依長度排序，以及顯示資料表中每個檔案的名稱和長度。</span><span class="sxs-lookup"><span data-stu-id="86e3c-126">This pipeline example gets the text files in the current directory, selects only the files that are more than 10,000 bytes long, sorts them by length, and displays the name and length of each file in a table.</span></span>

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

<span data-ttu-id="86e3c-127">此管線是由指定順序的四個命令所組成。</span><span class="sxs-lookup"><span data-stu-id="86e3c-127">This pipeline consists of four commands in the specified order.</span></span> <span data-ttu-id="86e3c-128">下圖顯示每個命令的輸出，因為它會傳遞至管線中的下一個命令。</span><span class="sxs-lookup"><span data-stu-id="86e3c-128">The following illustration shows the output from each command as it's passed to the next command in the pipeline.</span></span>

```
Get-ChildItem -Path *.txt
| (FileInfo objects for *.txt)
V
Where-Object {$_.length -gt 10000}
| (FileInfo objects for *.txt)
| (      Length > 10000      )
V
Sort-Object -Property Length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
V
Format-Table -Property name, length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
| (   Formatted in a table   )
V

Name                       Length
----                       ------
tmp1.txt                    82920
tmp2.txt                   114000
tmp3.txt                   114000
```

## <a name="using-pipelines"></a><span data-ttu-id="86e3c-129">使用管線</span><span class="sxs-lookup"><span data-stu-id="86e3c-129">Using pipelines</span></span>

<span data-ttu-id="86e3c-130">大部分的 PowerShell Cmdlet 都是設計來支援管線。</span><span class="sxs-lookup"><span data-stu-id="86e3c-130">Most PowerShell cmdlets are designed to support pipelines.</span></span> <span data-ttu-id="86e3c-131">在大多數情況下，您可以使用 _管線_ 將 **Get** Cmdlet 的結果傳送至相同名詞的另一個 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86e3c-131">In most cases, you can _pipe_ the results of a **Get** cmdlet to another cmdlet of the same noun.</span></span>
<span data-ttu-id="86e3c-132">例如，您可以透過管道將 Cmdlet 的輸出傳送 `Get-Service` 至 `Start-Service` 或 `Stop-Service` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86e3c-132">For example, you can pipe the output of the `Get-Service` cmdlet to the `Start-Service` or `Stop-Service` cmdlets.</span></span>

<span data-ttu-id="86e3c-133">此範例管線會啟動電腦上的 WMI 服務：</span><span class="sxs-lookup"><span data-stu-id="86e3c-133">This example pipeline starts the WMI service on the computer:</span></span>

```powershell
Get-Service wmi | Start-Service
```

<span data-ttu-id="86e3c-134">針對另一個範例，您可以透過管道將 `Get-Item` PowerShell 登錄提供者中或的輸出傳送 `Get-ChildItem` 至 `New-ItemProperty` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86e3c-134">For another example, you can pipe the output of `Get-Item` or `Get-ChildItem` within the PowerShell registry provider to the `New-ItemProperty` cmdlet.</span></span> <span data-ttu-id="86e3c-135">此範例會將新的登錄專案 **NoOfEmployees** （值為 **8124** ）新增至 **MyCompany** 登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="86e3c-135">This example adds a new registry entry, **NoOfEmployees** , with a value of **8124** , to the **MyCompany** registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

<span data-ttu-id="86e3c-136">許多公用程式 Cmdlet （例如、、 `Get-Member` 、 `Where-Object` `Sort-Object` 和） `Group-Object` `Measure-Object` 在管線中幾乎都是使用。</span><span class="sxs-lookup"><span data-stu-id="86e3c-136">Many of the utility cmdlets, such as `Get-Member`, `Where-Object`, `Sort-Object`, `Group-Object`, and `Measure-Object` are used almost exclusively in pipelines.</span></span> <span data-ttu-id="86e3c-137">您可以透過管線將任何物件類型傳送至這些 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86e3c-137">You can pipe any object type to these cmdlets.</span></span> <span data-ttu-id="86e3c-138">這個範例會示範如何依照每個進程中的開啟控制碼數目來排序電腦上的所有處理常式。</span><span class="sxs-lookup"><span data-stu-id="86e3c-138">This example shows how to sort all the processes on the computer by the number of open handles in each process.</span></span>

```powershell
Get-Process | Sort-Object -Property handles
```

<span data-ttu-id="86e3c-139">您可以透過管線將物件傳送至格式化、匯出和輸出 Cmdlet，例如 `Format-List` 、 `Format-Table` 、 `Export-Clixml` 、 `Export-CSV` 和 `Out-File` 。</span><span class="sxs-lookup"><span data-stu-id="86e3c-139">You can pipe objects to the formatting, export, and output cmdlets, such as `Format-List`, `Format-Table`, `Export-Clixml`, `Export-CSV`, and `Out-File`.</span></span>

<span data-ttu-id="86e3c-140">此範例示範如何使用指令 `Format-List` 程式來顯示處理常式物件的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="86e3c-140">This example shows how to use the `Format-List` cmdlet to display a list of properties for a process object.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="86e3c-141">在練習中，您會發現將簡單的命令結合成管線可節省時間和輸入，並讓您的腳本更有效率。</span><span class="sxs-lookup"><span data-stu-id="86e3c-141">With a bit of practice, you'll find that combining simple commands into pipelines saves time and typing, and makes your scripting more efficient.</span></span>

## <a name="how-pipelines-work"></a><span data-ttu-id="86e3c-142">管線的運作方式</span><span class="sxs-lookup"><span data-stu-id="86e3c-142">How pipelines work</span></span>

<span data-ttu-id="86e3c-143">本節說明輸入物件如何系結至 Cmdlet 參數，以及在管線執行期間處理。</span><span class="sxs-lookup"><span data-stu-id="86e3c-143">This section explains how input objects are bound to cmdlet parameters and processed during pipeline execution.</span></span>

### <a name="accepts-pipeline-input"></a><span data-ttu-id="86e3c-144">接受管線輸入</span><span class="sxs-lookup"><span data-stu-id="86e3c-144">Accepts pipeline input</span></span>

<span data-ttu-id="86e3c-145">為了支援管線，接收的 Cmdlet 必須有接受管線輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="86e3c-145">To support pipelining, the receiving cmdlet must have a parameter that accepts pipeline input.</span></span> <span data-ttu-id="86e3c-146">使用 `Get-Help` 命令搭配 **Full** 或 **參數** 選項，以判斷 Cmdlet 接受管線輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="86e3c-146">Use the `Get-Help` command with the **Full** or **Parameter** options to determine which parameters of a cmdlet accept pipeline input.</span></span>

<span data-ttu-id="86e3c-147">例如，若要判斷 Cmdlet 的哪些參數 `Start-Service` 接受管線輸入，請輸入：</span><span class="sxs-lookup"><span data-stu-id="86e3c-147">For example, to determine which of the parameters of the `Start-Service` cmdlet accepts pipeline input, type:</span></span>

```powershell
Get-Help Start-Service -Full
```

<span data-ttu-id="86e3c-148">或</span><span class="sxs-lookup"><span data-stu-id="86e3c-148">or</span></span>

```powershell
Get-Help Start-Service -Parameter *
```

<span data-ttu-id="86e3c-149">指令程式的 `Start-Service` 說明只會顯示 **InputObject** 和 **Name** 參數接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="86e3c-149">The help for the `Start-Service` cmdlet shows that only the **InputObject** and **Name** parameters accept pipeline input.</span></span>

```Output
-InputObject <ServiceController[]>
Specifies ServiceController objects representing the services to be started.
Enter a variable that contains the objects, or type a command or expression
that gets the objects.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByValue)
Accept wildcard characters?  false

-Name <String[]>
Specifies the service names for the service to be started.

The parameter name is optional. You can use Name or its alias, ServiceName,
or you can omit the parameter name.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByPropertyName, ByValue)
Accept wildcard characters?  false
```

<span data-ttu-id="86e3c-150">當您透過管線將物件傳送至時 `Start-Service` ，PowerShell 會嘗試將物件與 **InputObject** 和 **Name** 參數產生關聯。</span><span class="sxs-lookup"><span data-stu-id="86e3c-150">When you send objects through the pipeline to `Start-Service`, PowerShell attempts to associate the objects with the **InputObject** and **Name** parameters.</span></span>

### <a name="methods-of-accepting-pipeline-input"></a><span data-ttu-id="86e3c-151">接受管線輸入的方法</span><span class="sxs-lookup"><span data-stu-id="86e3c-151">Methods of accepting pipeline input</span></span>

<span data-ttu-id="86e3c-152">Cmdlet 參數可以透過下列兩種不同方式接受管線輸入：</span><span class="sxs-lookup"><span data-stu-id="86e3c-152">Cmdlets parameters can accept pipeline input in one of two different ways:</span></span>

- <span data-ttu-id="86e3c-153">**ByValue** ：參數會接受符合預期 .net 類型或可轉換為該類型的值。</span><span class="sxs-lookup"><span data-stu-id="86e3c-153">**ByValue** : The parameter accepts values that match the expected .NET type or that can be converted to that type.</span></span>

  <span data-ttu-id="86e3c-154">例如，的 **Name** 參數會 `Start-Service` 接受以傳值方式輸入的管線。</span><span class="sxs-lookup"><span data-stu-id="86e3c-154">For example, the **Name** parameter of `Start-Service` accepts pipeline input by value.</span></span> <span data-ttu-id="86e3c-155">它可以接受可轉換成字串的字串物件或物件。</span><span class="sxs-lookup"><span data-stu-id="86e3c-155">It can accept string objects or objects that can be converted to strings.</span></span>

- <span data-ttu-id="86e3c-156">**ByPropertyName** ：參數只有在輸入物件具有與參數同名的屬性時，才會接受輸入。</span><span class="sxs-lookup"><span data-stu-id="86e3c-156">**ByPropertyName** : The parameter accepts input only when the input object has a property of the same name as the parameter.</span></span>

  <span data-ttu-id="86e3c-157">例如，的 Name 參數 `Start-Service` 可以接受具有 **Name** 屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="86e3c-157">For example, the Name parameter of `Start-Service` can accept objects that have a **Name** property.</span></span> <span data-ttu-id="86e3c-158">若要列出物件的屬性，請使用管線將它傳送至 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="86e3c-158">To list the properties of an object, pipe it to `Get-Member`.</span></span>

<span data-ttu-id="86e3c-159">某些參數可以接受值或屬性名稱的物件，讓您更輕鬆地從管線取得輸入。</span><span class="sxs-lookup"><span data-stu-id="86e3c-159">Some parameters can accept objects by both value or property name, making it easier to take input from the pipeline.</span></span>

### <a name="parameter-binding"></a><span data-ttu-id="86e3c-160">參數繫結</span><span class="sxs-lookup"><span data-stu-id="86e3c-160">Parameter binding</span></span>

<span data-ttu-id="86e3c-161">當您使用管線將物件從一個命令傳送到另一個命令時，PowerShell 會嘗試將管道物件與接收 Cmdlet 的參數產生關聯。</span><span class="sxs-lookup"><span data-stu-id="86e3c-161">When you pipe objects from one command to another command, PowerShell attempts to associate the piped objects with a parameter of the receiving cmdlet.</span></span>

<span data-ttu-id="86e3c-162">PowerShell 的參數系結元件會根據下列準則，將輸入物件與 Cmdlet 參數產生關聯：</span><span class="sxs-lookup"><span data-stu-id="86e3c-162">PowerShell's parameter binding component associates the input objects with cmdlet parameters according to the following criteria:</span></span>

- <span data-ttu-id="86e3c-163">參數必須接受來自管線的輸入。</span><span class="sxs-lookup"><span data-stu-id="86e3c-163">The parameter must accept input from a pipeline.</span></span>
- <span data-ttu-id="86e3c-164">參數必須接受所傳送物件的型別，或是可以轉換成預期型別的型別。</span><span class="sxs-lookup"><span data-stu-id="86e3c-164">The parameter must accept the type of object being sent or a type that can be converted to the expected type.</span></span>
- <span data-ttu-id="86e3c-165">命令中未使用參數。</span><span class="sxs-lookup"><span data-stu-id="86e3c-165">The parameter wasn't used in the command.</span></span>

<span data-ttu-id="86e3c-166">例如， `Start-Service` Cmdlet 有許多參數，但只有兩個， **名稱** 和 **InputObject** 接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="86e3c-166">For example, the `Start-Service` cmdlet has many parameters, but only two of them, **Name** and **InputObject** accept pipeline input.</span></span> <span data-ttu-id="86e3c-167">**Name** 參數接受字串，而 **InputObject** 參數則接受服務物件。</span><span class="sxs-lookup"><span data-stu-id="86e3c-167">The **Name** parameter takes strings and the **InputObject** parameter takes service objects.</span></span> <span data-ttu-id="86e3c-168">因此，您可以使用可轉換成字串或服務物件的屬性，將字串、服務物件和物件輸送。</span><span class="sxs-lookup"><span data-stu-id="86e3c-168">Therefore, you can pipe strings, service objects, and objects with properties that can be converted to string or service objects.</span></span>

<span data-ttu-id="86e3c-169">PowerShell 盡可能有效率地管理參數系結。</span><span class="sxs-lookup"><span data-stu-id="86e3c-169">PowerShell manages parameter binding as efficiently as possible.</span></span> <span data-ttu-id="86e3c-170">您無法建議或強制 PowerShell 系結至特定的參數。</span><span class="sxs-lookup"><span data-stu-id="86e3c-170">You can't suggest or force the PowerShell to bind to a specific parameter.</span></span> <span data-ttu-id="86e3c-171">如果 PowerShell 無法系結輸送的物件，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="86e3c-171">The command fails if PowerShell can't bind the piped objects.</span></span>

<span data-ttu-id="86e3c-172">如需針對系結錯誤進行疑難排解的詳細資訊，請參閱本文稍後的 [調查管線錯誤](#investigating-pipeline-errors) 。</span><span class="sxs-lookup"><span data-stu-id="86e3c-172">For more information about troubleshooting binding errors, see [Investigating Pipeline Errors](#investigating-pipeline-errors) later in this article.</span></span>

### <a name="one-at-a-time-processing"></a><span data-ttu-id="86e3c-173">一次性的處理</span><span class="sxs-lookup"><span data-stu-id="86e3c-173">One-at-a-time processing</span></span>

<span data-ttu-id="86e3c-174">將物件傳送至命令很像是使用命令的參數來提交物件。</span><span class="sxs-lookup"><span data-stu-id="86e3c-174">Piping objects to a command is much like using a parameter of the command to submit the objects.</span></span> <span data-ttu-id="86e3c-175">讓我們看看管線範例。</span><span class="sxs-lookup"><span data-stu-id="86e3c-175">Let's look at a pipeline example.</span></span> <span data-ttu-id="86e3c-176">在此範例中，我們會使用管線來顯示服務物件的表格。</span><span class="sxs-lookup"><span data-stu-id="86e3c-176">In this example, we use a pipeline to display a table of service objects.</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="86e3c-177">功能上，這就像是使用的 **InputObject** 參數 `Format-Table` 來提交物件集合。</span><span class="sxs-lookup"><span data-stu-id="86e3c-177">Functionally, this is like using the **InputObject** parameter of `Format-Table` to submit the object collection.</span></span>

<span data-ttu-id="86e3c-178">例如，我們可以將服務集合儲存至使用 **InputObject** 參數傳遞的變數。</span><span class="sxs-lookup"><span data-stu-id="86e3c-178">For example, we can save the collection of services to a variable that is passed using the **InputObject** parameter.</span></span>

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

<span data-ttu-id="86e3c-179">也可以將命令內嵌在 **InputObject** 參數中。</span><span class="sxs-lookup"><span data-stu-id="86e3c-179">Or we can embed the command in the **InputObject** parameter.</span></span>

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

<span data-ttu-id="86e3c-180">不過，有一個重要的差異。</span><span class="sxs-lookup"><span data-stu-id="86e3c-180">However, there's an important difference.</span></span> <span data-ttu-id="86e3c-181">當您使用管線將多個物件傳送至命令時，PowerShell 會一次將物件傳送至命令。</span><span class="sxs-lookup"><span data-stu-id="86e3c-181">When you pipe multiple objects to a command, PowerShell sends the objects to the command one at a time.</span></span> <span data-ttu-id="86e3c-182">當您使用命令參數時，物件會以單一陣列物件的形式傳送。</span><span class="sxs-lookup"><span data-stu-id="86e3c-182">When you use a command parameter, the objects are sent as a single array object.</span></span> <span data-ttu-id="86e3c-183">這項微小差異有顯著的後果。</span><span class="sxs-lookup"><span data-stu-id="86e3c-183">This minor difference has significant consequences.</span></span>

<span data-ttu-id="86e3c-184">執行管線時，PowerShell 會自動列舉任何實作為介面的類型， `IEnumerable` 並一次透過管線傳送成員。</span><span class="sxs-lookup"><span data-stu-id="86e3c-184">When executing a pipeline, PowerShell automatically enumerates any type that implements the `IEnumerable` interface and sends the members through the pipeline one at a time.</span></span> <span data-ttu-id="86e3c-185">例外狀況是 `[hashtable]` ，需要呼叫 `GetEnumerator()` 方法。</span><span class="sxs-lookup"><span data-stu-id="86e3c-185">The exception is `[hashtable]`, which requires a call to the `GetEnumerator()` method.</span></span>

<span data-ttu-id="86e3c-186">在下列範例中，會使用管線將陣列和 hashtable 輸送至 `Measure-Object` Cmdlet，以計算從管線接收的物件數目。</span><span class="sxs-lookup"><span data-stu-id="86e3c-186">In the following examples, an array and a hashtable are piped to the `Measure-Object` cmdlet to count the number of objects received from the pipeline.</span></span> <span data-ttu-id="86e3c-187">陣列有多個成員，而雜湊表具有多個索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="86e3c-187">The array has multiple members, and the hashtable has multiple key-value pairs.</span></span> <span data-ttu-id="86e3c-188">一次只列舉一個陣列。</span><span class="sxs-lookup"><span data-stu-id="86e3c-188">Only the array is enumerated one at a time.</span></span>

```powershell
@(1,2,3) | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

```powershell
@{"One"=1;"Two"=2} | Measure-Object
```

```Output
Count    : 1
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

<span data-ttu-id="86e3c-189">同樣地，如果您使用管線將多個處理常式物件從 `Get-Process` Cmdlet 傳送至 `Get-Member` Cmdlet，則 PowerShell 會將每個處理常式物件一次傳送至 `Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="86e3c-189">Similarly, if you pipe multiple process objects from the `Get-Process` cmdlet to the `Get-Member` cmdlet, PowerShell sends each process object, one at a time, to `Get-Member`.</span></span> <span data-ttu-id="86e3c-190">`Get-Member` 顯示處理常式物件的 .NET 類別 (類型) ，以及其屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="86e3c-190">`Get-Member` displays the .NET class (type) of the process objects, and their properties and methods.</span></span>

```powershell
Get-Process | Get-Member
```

```Output
TypeName: System.Diagnostics.Process

Name      MemberType     Definition
----      ----------     ----------
Handles   AliasProperty  Handles = Handlecount
Name      AliasProperty  Name = ProcessName
NPM       AliasProperty  NPM = NonpagedSystemMemorySize
...
```

> [!NOTE]
> <span data-ttu-id="86e3c-191">`Get-Member` 排除重複專案，因此如果物件全都屬於相同類型，則只會顯示一個物件類型。</span><span class="sxs-lookup"><span data-stu-id="86e3c-191">`Get-Member` eliminates duplicates, so if the objects are all of the same type, it only displays one object type.</span></span>

<span data-ttu-id="86e3c-192">但是，如果您使用的 **InputObject** 參數 `Get-Member` ，則會 `Get-Member` 接收 system.string 的陣列，將物件 **處理** 為單一單位。</span><span class="sxs-lookup"><span data-stu-id="86e3c-192">However, if you use the **InputObject** parameter of `Get-Member`, then `Get-Member` receives an array of **System.Diagnostics.Process** objects as a single unit.</span></span> <span data-ttu-id="86e3c-193">它會顯示物件陣列的屬性。</span><span class="sxs-lookup"><span data-stu-id="86e3c-193">It displays the properties of an array of objects.</span></span> <span data-ttu-id="86e3c-194"> (記下陣列符號 (`[]`) 在 **system.object** 類型名稱之後。 ) </span><span class="sxs-lookup"><span data-stu-id="86e3c-194">(Note the array symbol (`[]`) after the **System.Object** type name.)</span></span>

<span data-ttu-id="86e3c-195">例如，套用至物件的</span><span class="sxs-lookup"><span data-stu-id="86e3c-195">For example,</span></span>

```powershell
Get-Member -InputObject (Get-Process)
```

```Output
TypeName: System.Object[]

Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
Address            Method        System.Object& Address(Int32 )
Clone              Method        System.Object Clone()
...
```

<span data-ttu-id="86e3c-196">這可能不是您想要的結果。</span><span class="sxs-lookup"><span data-stu-id="86e3c-196">This result might not be what you intended.</span></span> <span data-ttu-id="86e3c-197">但是在您瞭解之後，就可以使用它。</span><span class="sxs-lookup"><span data-stu-id="86e3c-197">But after you understand it, you can use it.</span></span> <span data-ttu-id="86e3c-198">例如，所有陣列物件都有 **Count** 屬性。</span><span class="sxs-lookup"><span data-stu-id="86e3c-198">For example, all array objects have a **Count** property.</span></span> <span data-ttu-id="86e3c-199">您可以使用它來計算電腦上執行的處理常式數目。</span><span class="sxs-lookup"><span data-stu-id="86e3c-199">You can use that to count the number of processes running on the computer.</span></span>

<span data-ttu-id="86e3c-200">例如，套用至物件的</span><span class="sxs-lookup"><span data-stu-id="86e3c-200">For example,</span></span>

```powershell
(Get-Process).count
```

<span data-ttu-id="86e3c-201">請務必記住，管線上傳送的物件會一次傳遞一個。</span><span class="sxs-lookup"><span data-stu-id="86e3c-201">It's important to remember that objects sent down the pipeline are delivered one at a time.</span></span>

## <a name="investigating-pipeline-errors"></a><span data-ttu-id="86e3c-202">調查管線錯誤</span><span class="sxs-lookup"><span data-stu-id="86e3c-202">Investigating pipeline errors</span></span>

<span data-ttu-id="86e3c-203">當 PowerShell 無法使輸送的物件與接收 Cmdlet 的參數產生關聯時，命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="86e3c-203">When PowerShell can't associate the piped objects with a parameter of the receiving cmdlet, the command fails.</span></span>

<span data-ttu-id="86e3c-204">在下列範例中，我們會嘗試將登錄專案從一個登錄機碼移至另一個登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="86e3c-204">In the following example, we try to move a registry entry from one registry key to another.</span></span> <span data-ttu-id="86e3c-205">此 `Get-Item` Cmdlet 會取得目的地路徑，然後以管線傳送至 `Move-ItemProperty` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86e3c-205">The `Get-Item` cmdlet gets the destination path, which is then piped to the `Move-ItemProperty` cmdlet.</span></span> <span data-ttu-id="86e3c-206">此 `Move-ItemProperty` 命令會指定要移動的登錄專案目前的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="86e3c-206">The `Move-ItemProperty` command specifies the current path and name of the registry entry to be moved.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

<span data-ttu-id="86e3c-207">此命令會失敗，且 PowerShell 會顯示下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="86e3c-207">The command fails and PowerShell displays the following error message:</span></span>

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

<span data-ttu-id="86e3c-208">若要調查，請使用 `Trace-Command` Cmdlet 來追蹤 PowerShell 的參數系結元件。</span><span class="sxs-lookup"><span data-stu-id="86e3c-208">To investigate, use the `Trace-Command` cmdlet to trace the parameter binding component of PowerShell.</span></span> <span data-ttu-id="86e3c-209">下列範例會在管線執行時追蹤參數系結。</span><span class="sxs-lookup"><span data-stu-id="86e3c-209">The following example traces parameter binding while the pipeline is executing.</span></span> <span data-ttu-id="86e3c-210">**PSHost** 參數會在主控台中顯示追蹤結果，而 **FilePath** 參數會將追蹤結果傳送至檔案， `debug.txt` 以供稍後參考。</span><span class="sxs-lookup"><span data-stu-id="86e3c-210">The **PSHost** parameter displays the trace results in the console and the **FilePath** parameter send the trace results to the `debug.txt` file for later reference.</span></span>

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

<span data-ttu-id="86e3c-211">追蹤的結果很長，但它們會顯示系結至 Cmdlet 的值， `Get-Item` 然後再將命名值系結至 `Move-ItemProperty` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86e3c-211">The results of the trace are lengthy, but they show the values being bound to the `Get-Item` cmdlet and then the named values being bound to the `Move-ItemProperty` cmdlet.</span></span>

```Output
...
BIND NAMED cmd line args [`Move-ItemProperty`]
BIND arg [HKLM:\Software\MyCompany\design] to parameter [Path]
...
BIND arg [product] to parameter [Name]
...
BIND POSITIONAL cmd line args [`Move-ItemProperty`]
...
```

<span data-ttu-id="86e3c-212">最後，它會顯示嘗試將路徑系結至失敗的 **目的地** 參數 `Move-ItemProperty` 。</span><span class="sxs-lookup"><span data-stu-id="86e3c-212">Finally, it shows that the attempt to bind the path to the **Destination** parameter of `Move-ItemProperty` failed.</span></span>

```Output
...
BIND PIPELINE object to parameters: [`Move-ItemProperty`]
PIPELINE object TYPE = [Microsoft.Win32.RegistryKey]
RESTORING pipeline parameter's original values
Parameter [Destination] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
Parameter [Credential] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
...
```

<span data-ttu-id="86e3c-213">使用 `Get-Help` Cmdlet 來查看 **目的地** 參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="86e3c-213">Use the `Get-Help` cmdlet to view the attributes of the **Destination** parameter.</span></span>

```Output
Get-Help Move-ItemProperty -Parameter Destination

-Destination <String>
    Specifies the path to the destination location.

    Required?                    true
    Position?                    1
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  false
```

<span data-ttu-id="86e3c-214">結果會顯示 **目的地** 只接受「依屬性名稱」的管線輸入。</span><span class="sxs-lookup"><span data-stu-id="86e3c-214">The results show that **Destination** takes pipeline input only "by property name".</span></span> <span data-ttu-id="86e3c-215">因此，輸送的物件必須有一個名為 **Destination** 的屬性。</span><span class="sxs-lookup"><span data-stu-id="86e3c-215">Therefore, the piped object must have a property named **Destination** .</span></span>

<span data-ttu-id="86e3c-216">使用 `Get-Member` 以查看來自的物件屬性 `Get-Item` 。</span><span class="sxs-lookup"><span data-stu-id="86e3c-216">Use `Get-Member` to see the properties of the object coming from `Get-Item`.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

<span data-ttu-id="86e3c-217">輸出顯示此專案為不具有 **目的地** 屬性的 **Microsoft. RegistryKey** 物件。</span><span class="sxs-lookup"><span data-stu-id="86e3c-217">The output shows that the item is a **Microsoft.Win32.RegistryKey** object that doesn't have a **Destination** property.</span></span> <span data-ttu-id="86e3c-218">這會說明命令失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="86e3c-218">That explains why the command failed.</span></span>

<span data-ttu-id="86e3c-219">**Path** 參數會依名稱或傳值方式接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="86e3c-219">The **Path** parameter accepts pipeline input by name or by value.</span></span>

```Output
Get-Help Move-ItemProperty -Parameter Path

-Path <String[]>
    Specifies the path to the current location of the property. Wildcard
    characters are permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  true
```

<span data-ttu-id="86e3c-220">若要修正此命令，我們必須在 Cmdlet 中指定目的地， `Move-ItemProperty` 並使用 `Get-Item` 來取得我們想要移動之專案的 **路徑** 。</span><span class="sxs-lookup"><span data-stu-id="86e3c-220">To fix the command, we must specify the destination in the `Move-ItemProperty` cmdlet and use `Get-Item` to get the **Path** of the item we want to move.</span></span>

<span data-ttu-id="86e3c-221">例如，套用至物件的</span><span class="sxs-lookup"><span data-stu-id="86e3c-221">For example,</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a><span data-ttu-id="86e3c-222">內建行接續符號</span><span class="sxs-lookup"><span data-stu-id="86e3c-222">Intrinsic line continuation</span></span>

<span data-ttu-id="86e3c-223">如先前所討論，管線是由管線運算子連接的一連串命令 (`|`) ，通常是以單一行寫入。</span><span class="sxs-lookup"><span data-stu-id="86e3c-223">As already discussed, a pipeline is a series of commands connected by pipeline operators (`|`), usually written on a single line.</span></span> <span data-ttu-id="86e3c-224">不過，為了方便閱讀，PowerShell 可讓您將管線分割成多行。</span><span class="sxs-lookup"><span data-stu-id="86e3c-224">However, for readability, PowerShell allows you to split the pipeline across multiple lines.</span></span>
<span data-ttu-id="86e3c-225">當管道運算子是該行上的最後一個 token 時，PowerShell 剖析器會將下一行加入至目前的命令，以繼續管線的結構。</span><span class="sxs-lookup"><span data-stu-id="86e3c-225">When a pipe operator is the last token on the line, the PowerShell parser joins the next line to current command to continue the construction of the pipeline.</span></span>

<span data-ttu-id="86e3c-226">例如，下列單行管線：</span><span class="sxs-lookup"><span data-stu-id="86e3c-226">For example, the following single-line pipeline:</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="86e3c-227">可以撰寫為：</span><span class="sxs-lookup"><span data-stu-id="86e3c-227">can be written as:</span></span>

```powershell
Command-1 |
  Command-2 |
    Command-3
```

<span data-ttu-id="86e3c-228">後續幾行的前置空格並不重要。</span><span class="sxs-lookup"><span data-stu-id="86e3c-228">The leading spaces on the subsequent lines are not significant.</span></span> <span data-ttu-id="86e3c-229">縮排可增強可讀性。</span><span class="sxs-lookup"><span data-stu-id="86e3c-229">The indentation enhances readability.</span></span>

## <a name="see-also"></a><span data-ttu-id="86e3c-230">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86e3c-230">See Also</span></span>

[<span data-ttu-id="86e3c-231">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="86e3c-231">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="86e3c-232">about_Objects</span><span class="sxs-lookup"><span data-stu-id="86e3c-232">about_Objects</span></span>](about_objects.md)

[<span data-ttu-id="86e3c-233">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="86e3c-233">about_Parameters</span></span>](about_parameters.md)

[<span data-ttu-id="86e3c-234">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="86e3c-234">about_Command_Syntax</span></span>](about_command_syntax.md)

[<span data-ttu-id="86e3c-235">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="86e3c-235">about_ForEach</span></span>](about_foreach.md)
