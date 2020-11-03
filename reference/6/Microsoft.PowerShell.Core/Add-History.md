---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-history?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-History
ms.openlocfilehash: 5dfb6c4024daa0efdf25ee2453427e34552bdb4a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204347"
---
# <span data-ttu-id="f5ed8-103">Add-History</span><span class="sxs-lookup"><span data-stu-id="f5ed8-103">Add-History</span></span>

## <span data-ttu-id="f5ed8-104">概要</span><span class="sxs-lookup"><span data-stu-id="f5ed8-104">SYNOPSIS</span></span>
<span data-ttu-id="f5ed8-105">將項目附加至工作階段歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-105">Appends entries to the session history.</span></span>

## <span data-ttu-id="f5ed8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f5ed8-106">SYNTAX</span></span>

```
Add-History [[-InputObject] <PSObject[]>] [-Passthru] [<CommonParameters>]
```

## <span data-ttu-id="f5ed8-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f5ed8-107">DESCRIPTION</span></span>

<span data-ttu-id="f5ed8-108">`Add-History`Cmdlet 會將專案新增至會話歷程記錄的結尾，也就是在目前會話期間輸入的命令清單。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-108">The `Add-History` cmdlet adds entries to the end of the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="f5ed8-109">工作階段歷程記錄是工作階段期間輸入的命令清單。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-109">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="f5ed8-110">工作階段歷程記錄代表命令的執行順序、狀態及開始和結束時間。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-110">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="f5ed8-111">當您輸入每個命令時，PowerShell 會將它新增至歷程記錄，以便您可以重複使用。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-111">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="f5ed8-112">如需會話歷程記錄的詳細資訊，請參閱 [about_History](About/about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-112">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="f5ed8-113">會話歷程記錄是與 **PSReadLine** 模組所維護的歷程記錄分開管理。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-113">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="f5ed8-114">這兩個歷程記錄都可以在載入 **PSReadLine** 的會話中使用。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-114">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="f5ed8-115">此 Cmdlet 僅適用于會話歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-115">This cmdlet only works with the session history.</span></span> <span data-ttu-id="f5ed8-116">如需詳細資訊，請參閱 [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-116">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

<span data-ttu-id="f5ed8-117">您可以使用 `Get-History` 指令程式取得命令，並將它們傳遞給 `Add-History` ，也可以將命令匯出至 CSV 或 XML 檔案，然後匯入命令，並將匯入的檔案傳遞至 `Add-History` 。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-117">You can use the `Get-History` cmdlet to get the commands and pass them to `Add-History`, or you can export the commands to a CSV or XML file, then import the commands, and pass the imported file to `Add-History`.</span></span> <span data-ttu-id="f5ed8-118">您可以使用此 Cmdlet 將特定的命令新增至歷程記錄，或建立包含來自多個工作階段之命令的單一歷程記錄檔案。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-118">You can use this cmdlet to add specific commands to the history or to create a single history file that includes commands from more than one session.</span></span>

## <span data-ttu-id="f5ed8-119">範例</span><span class="sxs-lookup"><span data-stu-id="f5ed8-119">EXAMPLES</span></span>

### <span data-ttu-id="f5ed8-120">範例1：將命令新增至不同會話的歷程記錄</span><span class="sxs-lookup"><span data-stu-id="f5ed8-120">Example 1: Add commands to the history of a different session</span></span>

<span data-ttu-id="f5ed8-121">此範例會將在一個 PowerShell 會話中輸入的命令新增至不同 PowerShell 會話的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-121">This example add the commands typed in one PowerShell session to the history of a different PowerShell session.</span></span>

```powershell
Get-History | Export-Csv c:\testing\history.csv -IncludeTypeInformation
Import-Csv c:\testing\history.csv | Add-History
```

<span data-ttu-id="f5ed8-122">第一個命令會取得代表歷程記錄中之命令的物件，並將其匯出至檔案 `History.csv` 。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-122">The first command gets objects representing the commands in the history and exports them to the `History.csv` file.</span></span>

<span data-ttu-id="f5ed8-123">第二個命令是在不同工作階段的命令列中輸入。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-123">The second command is typed at the command line of a different session.</span></span> <span data-ttu-id="f5ed8-124">它會使用 `Import-Csv` Cmdlet 匯入檔案中的物件 `History.csv` 。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-124">It uses the `Import-Csv` cmdlet to import the objects in the `History.csv` file.</span></span> <span data-ttu-id="f5ed8-125">管線運算子 (`|`) 會將物件傳遞至 `Add-History` Cmdlet，此 Cmdlet 會將代表檔案中命令的物件新增 `History.csv` 至目前的會話歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-125">The pipeline operator (`|`) passes the objects to the `Add-History` cmdlet, which adds the objects representing the commands in the `History.csv` file to the current session history.</span></span>

### <span data-ttu-id="f5ed8-126">範例2：匯入和執行命令</span><span class="sxs-lookup"><span data-stu-id="f5ed8-126">Example 2: Import and run commands</span></span>

<span data-ttu-id="f5ed8-127">此範例會從檔案匯入命令 `History.xml` ，將它們新增至目前的會話歷程記錄，然後執行合併歷程記錄中的命令。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-127">This example imports commands from the `History.xml` file, adds them to the current session history, and then runs the commands in the combined history.</span></span>

```powershell
Import-Clixml c:\temp\history.xml | Add-History -PassThru | ForEach-Object -Process {Invoke-History}
```

<span data-ttu-id="f5ed8-128">第一個命令會使用 `Import-Clixml` Cmdlet 匯入已匯出至檔案的命令歷程記錄 `History.xml` 。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-128">The first command uses the `Import-Clixml` cmdlet to import a command history that was exported to the `History.xml` file.</span></span> <span data-ttu-id="f5ed8-129">管線運算子會將命令傳遞至 `Add-History` Cmdlet，此 Cmdlet 會將命令新增至目前的會話歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-129">The pipeline operator passes the commands to the `Add-History` cmdlet, which adds the commands to the current session history.</span></span> <span data-ttu-id="f5ed8-130">**PassThru** 參數會將代表新增之命令的物件傳遞至管線。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-130">The **PassThru** parameter passes the objects representing the added commands down the pipeline.</span></span>

<span data-ttu-id="f5ed8-131">然後，此命令會使用 `ForEach-Object` Cmdlet 將 `Invoke-History` 命令套用至合併歷程記錄中的每個命令。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-131">The command then uses the `ForEach-Object` cmdlet to apply the `Invoke-History` command to each of the commands in the combined history.</span></span> <span data-ttu-id="f5ed8-132">此 `Invoke-History` 命令會格式化為腳本區塊，並以大括弧 (`{}`) 括住，如 Cmdlet 的 **Process** 參數所要求 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-132">The `Invoke-History` command is formatted as a script block, enclosed in braces (`{}`), as required by the **Process** parameter of the `ForEach-Object` cmdlet.</span></span>

### <span data-ttu-id="f5ed8-133">範例3：將歷程記錄中的命令新增至歷程記錄的結尾</span><span class="sxs-lookup"><span data-stu-id="f5ed8-133">Example 3: Add commands in the history to the end of the history</span></span>

<span data-ttu-id="f5ed8-134">此範例會將歷程記錄中的前五個命令新增至歷程記錄清單的結尾。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-134">This example adds the first five commands in the history to the end of the history list.</span></span>

```powershell
Get-History -Id 5 -Count 5 | Add-History
```

<span data-ttu-id="f5ed8-135">此 `Get-History` Cmdlet 會取得五個命令，並以命令5結尾。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-135">The `Get-History` cmdlet gets the five commands ending in command 5.</span></span> <span data-ttu-id="f5ed8-136">管線運算子會將它們傳遞給 `Add-History` Cmdlet，以將它們附加至目前的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-136">The pipeline operator passes them to the `Add-History` cmdlet, which appends them to the current history.</span></span> <span data-ttu-id="f5ed8-137">此 `Add-History` 命令不包含任何參數，但 PowerShell 會將透過管線傳遞的物件與的 **InputObject** 參數產生關聯 `Add-History` 。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-137">The `Add-History` command does not include any parameters, but PowerShell associates the objects passed through the pipeline with the **InputObject** parameter of `Add-History`.</span></span>

### <span data-ttu-id="f5ed8-138">範例4：將 .csv 檔案中的命令新增至目前的歷程記錄</span><span class="sxs-lookup"><span data-stu-id="f5ed8-138">Example 4: Add commands in a .csv file to the current history</span></span>

<span data-ttu-id="f5ed8-139">此範例會將檔案中的命令新增 `History.csv` 至目前的會話歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-139">This example add the commands in the `History.csv` file to the current session history.</span></span>

```powershell
$a = Import-Csv c:\testing\history.csv
Add-History -InputObject $a -PassThru
```

<span data-ttu-id="f5ed8-140">Cmdlet 會匯 `Import-Csv` 入檔案中的命令 `History.csv` ，並將其內容儲存在變數中 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-140">The `Import-Csv` cmdlet imports the commands in the `History.csv` file and store its contents in the variable `$a`.</span></span>

<span data-ttu-id="f5ed8-141">第二個命令會使用 `Add-History` Cmdlet，將中的命令新增 `History.csv` 至目前的會話歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-141">The second command uses the `Add-History` cmdlet to add the commands from `History.csv` to the current session history.</span></span> <span data-ttu-id="f5ed8-142">它會使用 **InputObject** 參數來指定 `$a` 變數和 **PassThru** 參數，以產生要在命令列中顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-142">It uses the **InputObject** parameter to specify the `$a` variable and the **PassThru** parameter to generate an object to display at the command line.</span></span> <span data-ttu-id="f5ed8-143">如果沒有 **PassThru** 參數，此 `Add-History` Cmdlet 就不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-143">Without the **PassThru** parameter, the `Add-History` cmdlet does not generate any output.</span></span>

### <span data-ttu-id="f5ed8-144">範例5：將 .xml 檔案中的命令新增至目前的歷程記錄</span><span class="sxs-lookup"><span data-stu-id="f5ed8-144">Example 5: Add commands in an .xml file to the current history</span></span>

<span data-ttu-id="f5ed8-145">此範例會將檔案中的命令新增 `history.xml` 至目前的會話歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-145">This example adds the commands in the `history.xml` file to the current session history.</span></span>

```powershell
Add-History -InputObject (Import-Clixml c:\temp\history.xml)
```

<span data-ttu-id="f5ed8-146">**InputObject** 參數會將命令的結果以括弧傳遞給 `Add-History` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-146">The **InputObject** parameter passes the results of the command in parentheses to the `Add-History` cmdlet.</span></span> <span data-ttu-id="f5ed8-147">括弧中的命令會先執行，然後將檔案匯入 `history.xml` PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-147">The command in parentheses, which is executed first, imports the `history.xml` file into PowerShell.</span></span> <span data-ttu-id="f5ed8-148">`Add-History`Cmdlet 接著會將檔案中的命令新增至會話歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-148">The `Add-History` cmdlet then adds the commands in the file to the session history.</span></span>

## <span data-ttu-id="f5ed8-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f5ed8-149">PARAMETERS</span></span>

### <span data-ttu-id="f5ed8-150">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f5ed8-150">-InputObject</span></span>

<span data-ttu-id="f5ed8-151">指定要新增至歷程記錄的專案陣列，做為會話歷程記錄的 **HistoryInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-151">Specifies an array of entries to add to the history as **HistoryInfo** object to the session history.</span></span>
<span data-ttu-id="f5ed8-152">您可以使用此參數將 **HistoryInfo** 物件（例如、或 Cmdlet 所傳回的物件）提交 `Get-History` `Import-Clixml` `Import-Csv` 至 `Add-History` 。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-152">You can use this parameter to submit a **HistoryInfo** object, such as the ones that are returned by the `Get-History`, `Import-Clixml`, or `Import-Csv` cmdlets, to `Add-History`.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f5ed8-153">-Passthru</span><span class="sxs-lookup"><span data-stu-id="f5ed8-153">-Passthru</span></span>

<span data-ttu-id="f5ed8-154">指出此 Cmdlet 會傳回每個歷程記錄專案的 **HistoryInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-154">Indicates that this cmdlet returns a **HistoryInfo** object for each history entry.</span></span> <span data-ttu-id="f5ed8-155">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-155">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f5ed8-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f5ed8-156">CommonParameters</span></span>

<span data-ttu-id="f5ed8-157">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f5ed8-158">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f5ed8-159">輸入</span><span class="sxs-lookup"><span data-stu-id="f5ed8-159">INPUTS</span></span>

### <span data-ttu-id="f5ed8-160">Microsoft.PowerShell.Commands.HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="f5ed8-160">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="f5ed8-161">您可以使用管線將 **HistoryInfo** 物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-161">You can pipe a **HistoryInfo** object to this cmdlet.</span></span>

## <span data-ttu-id="f5ed8-162">輸出</span><span class="sxs-lookup"><span data-stu-id="f5ed8-162">OUTPUTS</span></span>

### <span data-ttu-id="f5ed8-163">無或 Microsoft.PowerShell.Commands.HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="f5ed8-163">None or Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="f5ed8-164">如果您指定 **PassThru** 參數，此 Cmdlet 會傳回 **HistoryInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-164">This cmdlet returns a **HistoryInfo** object if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="f5ed8-165">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-165">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f5ed8-166">注意</span><span class="sxs-lookup"><span data-stu-id="f5ed8-166">NOTES</span></span>

<span data-ttu-id="f5ed8-167">會話歷程記錄是會話期間輸入的命令及其識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-167">The session history is a list of the commands entered during the session together with the ID.</span></span> <span data-ttu-id="f5ed8-168">工作階段歷程記錄代表命令的執行順序、狀態及開始和結束時間。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-168">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="f5ed8-169">當您輸入每個命令時，PowerShell 會將它新增至歷程記錄，以便您可以重複使用。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-169">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="f5ed8-170">如需會話歷程記錄的詳細資訊，請參閱 [about_History](About/about_History.md)。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-170">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="f5ed8-171">如果要指定要新增至歷程記錄的命令，請使用 **InputObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-171">To specify the commands to add to the history, use the **InputObject** parameter.</span></span> <span data-ttu-id="f5ed8-172">此 `Add-History` 命令只會接受 **HistoryInfo** 物件，例如 Cmdlet 針對每個命令所傳回的物件 `Get-History` 。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-172">The `Add-History` command accepts only **HistoryInfo** objects, such as those returned for each command by the `Get-History` cmdlet.</span></span> <span data-ttu-id="f5ed8-173">您無法傳送路徑和檔案名稱或命令清單給它。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-173">You cannot pass it a path and file name or a list of commands.</span></span>

<span data-ttu-id="f5ed8-174">您可以使用 **InputObject** 參數將 **HistoryInfo** 物件的檔案傳遞至 `Add-History` 。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-174">You can use the **InputObject** parameter to pass a file of **HistoryInfo** objects to `Add-History`.</span></span> <span data-ttu-id="f5ed8-175">若要這樣做，請 `Get-History` 使用或 Cmdlet 將命令的結果匯出至檔案 `Export-Csv` ， `Export-Clixml` 然後使用或 Cmdlet 匯入檔案 `Import-Csv` `Import-Clixml` 。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-175">To do so, export the results of a `Get-History` command to a file by using the `Export-Csv` or `Export-Clixml` cmdlet and then import the file by using the `Import-Csv` or `Import-Clixml` cmdlets.</span></span> <span data-ttu-id="f5ed8-176">然後，您可以 **HistoryInfo** `Add-History` 透過管線或變數，將匯入的 HistoryInfo 物件的檔案傳遞至。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-176">You can then pass the file of imported **HistoryInfo** objects to `Add-History` through a pipeline or in a variable.</span></span> <span data-ttu-id="f5ed8-177">如需詳細資訊，請參閱範例。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-177">For more information, see the examples.</span></span>

<span data-ttu-id="f5ed8-178">您傳遞給 Cmdlet 的 **HistoryInfo** 物件檔案 `Add-History` 必須包含類型資訊、資料行標題，以及 **HistoryInfo** 物件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-178">The file of **HistoryInfo** objects that you pass to the `Add-History` cmdlet must include the type information, column headings, and all of the properties of the **HistoryInfo** objects.</span></span> <span data-ttu-id="f5ed8-179">如果您想要將物件傳遞回 `Add-History` ，請不要使用 Cmdlet 的 **NoTypeInformation** 參數，也不 `Export-Csv` 會刪除檔案中的類型資訊、欄標題或任何欄位。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-179">If you intend to pass the objects back to `Add-History`, do not use the **NoTypeInformation** parameter of the `Export-Csv` cmdlet and do not delete the type information, column headings, or any fields in the file.</span></span>

<span data-ttu-id="f5ed8-180">若要修改會話歷程記錄，請將會話匯出至 CSV 或 XML 檔案、修改檔案、匯入檔案，然後使用 `Add-History` 將它附加至目前的會話歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="f5ed8-180">To modify the session history, export the session to a CSV or XML file, modify the file, import the file, and use `Add-History` to append it to the current session history.</span></span>

## <span data-ttu-id="f5ed8-181">相關連結</span><span class="sxs-lookup"><span data-stu-id="f5ed8-181">RELATED LINKS</span></span>

[<span data-ttu-id="f5ed8-182">Clear-History</span><span class="sxs-lookup"><span data-stu-id="f5ed8-182">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="f5ed8-183">Get-History</span><span class="sxs-lookup"><span data-stu-id="f5ed8-183">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="f5ed8-184">Invoke-History</span><span class="sxs-lookup"><span data-stu-id="f5ed8-184">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="f5ed8-185">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="f5ed8-185">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="f5ed8-186">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="f5ed8-186">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="f5ed8-187">設定-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="f5ed8-187">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)
