---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 473571aa73d9b9331545b80cb5949e7a83c26eff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203179"
---
# <span data-ttu-id="cc32c-103">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="cc32c-103">Out-GridView</span></span>

## <span data-ttu-id="cc32c-104">概要</span><span class="sxs-lookup"><span data-stu-id="cc32c-104">SYNOPSIS</span></span>
<span data-ttu-id="cc32c-105">將輸出傳送到另一個視窗中的互動式表格。</span><span class="sxs-lookup"><span data-stu-id="cc32c-105">Sends output to an interactive table in a separate window.</span></span>

## <span data-ttu-id="cc32c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cc32c-106">SYNTAX</span></span>

### <span data-ttu-id="cc32c-107">PassThru (預設值)</span><span class="sxs-lookup"><span data-stu-id="cc32c-107">PassThru (Default)</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="cc32c-108">等候</span><span class="sxs-lookup"><span data-stu-id="cc32c-108">Wait</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### <span data-ttu-id="cc32c-109">OutputMode</span><span class="sxs-lookup"><span data-stu-id="cc32c-109">OutputMode</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## <span data-ttu-id="cc32c-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cc32c-110">DESCRIPTION</span></span>

<span data-ttu-id="cc32c-111">`Out-GridView`Cmdlet 會將命令的輸出傳送至格線視圖視窗，其中的輸出會顯示在互動式資料表中。</span><span class="sxs-lookup"><span data-stu-id="cc32c-111">The `Out-GridView` cmdlet sends the output from a command to a grid view window where the output is displayed in an interactive table.</span></span>

<span data-ttu-id="cc32c-112">由於此 Cmdlet 需要使用者介面，因此無法在 Windows Server Core 或 Windows Nano Server 上運作。</span><span class="sxs-lookup"><span data-stu-id="cc32c-112">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span>

<span data-ttu-id="cc32c-113">您可以使用下列表格功能來檢查您的資料：</span><span class="sxs-lookup"><span data-stu-id="cc32c-113">You can use the following features of the table to examine your data:</span></span>

- <span data-ttu-id="cc32c-114">隱藏、顯示及重新排列資料行</span><span class="sxs-lookup"><span data-stu-id="cc32c-114">Hide, Show, and Reorder Columns</span></span>
- <span data-ttu-id="cc32c-115">排序資料列</span><span class="sxs-lookup"><span data-stu-id="cc32c-115">Sort rows</span></span>
- <span data-ttu-id="cc32c-116">快速篩選器</span><span class="sxs-lookup"><span data-stu-id="cc32c-116">Quick Filter</span></span>
- <span data-ttu-id="cc32c-117">新增準則篩選</span><span class="sxs-lookup"><span data-stu-id="cc32c-117">Add Criteria Filter</span></span>
- <span data-ttu-id="cc32c-118">複製和貼上</span><span class="sxs-lookup"><span data-stu-id="cc32c-118">Copy and paste</span></span>

<span data-ttu-id="cc32c-119">如需完整指示，請參閱本文的「 [附注](#notes) 」一節。</span><span class="sxs-lookup"><span data-stu-id="cc32c-119">For full instructions, see the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="cc32c-120">範例</span><span class="sxs-lookup"><span data-stu-id="cc32c-120">EXAMPLES</span></span>

### <span data-ttu-id="cc32c-121">範例1：將進程輸出至方格視圖</span><span class="sxs-lookup"><span data-stu-id="cc32c-121">Example 1: Output processes to a grid view</span></span>

<span data-ttu-id="cc32c-122">這個範例會取得在本機電腦上執行的處理常式，並將它們傳送至方格視圖視窗。</span><span class="sxs-lookup"><span data-stu-id="cc32c-122">This example gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
Get-Process | Out-GridView
```

### <span data-ttu-id="cc32c-123">範例2：使用變數將進程輸出至方格視圖</span><span class="sxs-lookup"><span data-stu-id="cc32c-123">Example 2: Use a variable to output processes to a grid view</span></span>

<span data-ttu-id="cc32c-124">此範例也會取得在本機電腦上執行的處理常式，並將它們傳送至方格視圖視窗。</span><span class="sxs-lookup"><span data-stu-id="cc32c-124">This example also gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
$P = Get-Process
$P | Out-GridView
```

<span data-ttu-id="cc32c-125">Cmdlet 的輸出 `Get-Process` 會儲存在 `$P` 變數中。</span><span class="sxs-lookup"><span data-stu-id="cc32c-125">The output of the `Get-Process` cmdlet is saved in the `$P` variable.</span></span> <span data-ttu-id="cc32c-126">然後， `$P` 會輸送至 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-126">Then, `$P` is piped to `Out-GridView`.</span></span>

### <span data-ttu-id="cc32c-127">範例3：在格線視圖中顯示選取的屬性</span><span class="sxs-lookup"><span data-stu-id="cc32c-127">Example 3: Display a selected properties in a grid view</span></span>

<span data-ttu-id="cc32c-128">此範例會在格線視圖中顯示正在執行之進程的已選取屬性。</span><span class="sxs-lookup"><span data-stu-id="cc32c-128">This example displays selected properties of the running processes in a grid view.</span></span>

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

<span data-ttu-id="cc32c-129">的輸出 `Get-Process` 會以管道傳送至， `Select-Object` 以選取 [ \*\*\*\*\*\*名稱\*\*]、[工作集] 和 [ **PeakWorkingSet** ] 屬性。</span><span class="sxs-lookup"><span data-stu-id="cc32c-129">The output of `Get-Process` is piped to `Select-Object` to select the **Name**, **WorkingSet**, and **PeakWorkingSet** properties.</span></span> <span data-ttu-id="cc32c-130">另一個管線運算子會將篩選的物件傳送至 `Sort-Object` Cmdlet，以依工作集屬性的值以 **WorkingSet** 遞減順序排序它們。</span><span class="sxs-lookup"><span data-stu-id="cc32c-130">Another pipeline operator sends the filtered objects to the `Sort-Object` cmdlet to sort them in descending order by the value of the **WorkingSet** property.</span></span>
<span data-ttu-id="cc32c-131">然後，排序的結果會輸送至 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-131">Then, the sorted results are piped to `Out-GridView`.</span></span> <span data-ttu-id="cc32c-132">您現在已經可以使用資料格檢視的功能來搜尋、排序及篩選資料。</span><span class="sxs-lookup"><span data-stu-id="cc32c-132">You can now use the features of the grid view to search, sort, and filter the data.</span></span>

### <span data-ttu-id="cc32c-133">範例4：將輸出儲存至變數，然後輸出方格視圖</span><span class="sxs-lookup"><span data-stu-id="cc32c-133">Example 4: Save output to a variable, and then output a grid view</span></span>

<span data-ttu-id="cc32c-134">此範例會將 Cmdlet 輸出儲存在變數中，然後將它傳送至 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-134">This example saves cmdlet output in a variable then sends it to `Out-GridView`.</span></span>

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

<span data-ttu-id="cc32c-135">`Get-ChildItem` 使用自動變數，取得 PowerShell 安裝目錄及其子目錄中的所有檔案 `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-135">`Get-ChildItem` gets all the files in the PowerShell installation directory and its subdirectories using the the `$PSHOME` automatic variable.</span></span> <span data-ttu-id="cc32c-136">命令中的括號會確立操作的順序。</span><span class="sxs-lookup"><span data-stu-id="cc32c-136">The parentheses in the command establish the order of operations.</span></span> <span data-ttu-id="cc32c-137">因此，命令的輸出 `Get-ChildItem` 會先儲存在變數中， `$A` 然後再傳送至 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-137">As a result, the output from the `Get-ChildItem` command is saved in the `$A` variable before it is sent to `Out-GridView`.</span></span>

### <span data-ttu-id="cc32c-138">範例5：將指定電腦的輸出流程輸出至方格視圖</span><span class="sxs-lookup"><span data-stu-id="cc32c-138">Example 5: Output processes for a specified computer to a grid view</span></span>

<span data-ttu-id="cc32c-139">此範例會在格線視圖視窗中顯示在 Server01 電腦上執行的處理常式。</span><span class="sxs-lookup"><span data-stu-id="cc32c-139">This example displays the processes that are running on the Server01 computer in a grid view window.</span></span>

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

<span data-ttu-id="cc32c-140">範例會使用 `ogv` ，這是 Cmdlet 的別名 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-140">The examle uses `ogv`, which is the alias for the `Out-GridView` cmdlet.</span></span> <span data-ttu-id="cc32c-141">**Title** 參數指定視窗標題。</span><span class="sxs-lookup"><span data-stu-id="cc32c-141">The **Title** parameter specifies the window title.</span></span>

### <span data-ttu-id="cc32c-142">範例6：將遠端電腦的資料輸出至方格視圖</span><span class="sxs-lookup"><span data-stu-id="cc32c-142">Example 6: Output data from remote computers to a grid view</span></span>

<span data-ttu-id="cc32c-143">此範例示範如何將從遠端電腦收集的資料傳送至 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-143">This example shows how to send data collected from remote computers to `Out-GridView`.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

<span data-ttu-id="cc32c-144">`Invoke-Command` 會 `Get-Culture` 在三部遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="cc32c-144">`Invoke-Command` runs `Get-Culture` on three remote computers.</span></span> <span data-ttu-id="cc32c-145">產生的資料會以管道傳送至 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-145">The resulting data is piped to `Out-GridView`.</span></span> <span data-ttu-id="cc32c-146">請注意，在遠端電腦上執行的腳本區塊不包含 `Out-GridView` 命令。</span><span class="sxs-lookup"><span data-stu-id="cc32c-146">Notice that the script block that runs on the remote computer does not include the `Out-GridView` command.</span></span> <span data-ttu-id="cc32c-147">如果有包含，當此命令嘗試在每一部遠端電腦上開啟資料格檢視視窗時，將會失敗。</span><span class="sxs-lookup"><span data-stu-id="cc32c-147">If it did, the command would fail when it tried to open a grid view window on each of the remote computers.</span></span>

### <span data-ttu-id="cc32c-148">範例7：傳遞多個專案至 `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="cc32c-148">Example 7: Pass multiple items through `Out-GridView`</span></span>

<span data-ttu-id="cc32c-149">此範例可讓您從視窗中選取多個進程 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-149">This example lets you select multiple processes from the `Out-GridView` window.</span></span> <span data-ttu-id="cc32c-150">您選取的進程會傳遞至 `Export-Csv` 命令，並寫入至檔案 `ProcessLog.csv` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-150">The processes that you select are passed to the `Export-Csv` command and written to the `ProcessLog.csv` file.</span></span>

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

<span data-ttu-id="cc32c-151">的 **PassThru** 參數 `Out-GridView` 可讓您在管線中傳送多個專案。</span><span class="sxs-lookup"><span data-stu-id="cc32c-151">The **PassThru** parameter of `Out-GridView` lets you send multiple items down the pipeline.</span></span> <span data-ttu-id="cc32c-152">**PassThru** 參數等同於使用 **OutputMode** 參數的 **Multiple** 值。</span><span class="sxs-lookup"><span data-stu-id="cc32c-152">The **PassThru** parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

### <span data-ttu-id="cc32c-153">範例8：建立 Windows 快捷方式 `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="cc32c-153">Example 8: Create a Windows shortcut to `Out-GridView`</span></span>

<span data-ttu-id="cc32c-154">這個範例會示範如何使用的 **Wait** 參數 `Out-GridView` 來建立視窗的 Windows 快捷方式 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-154">This example shows how to use the **Wait** parameter of `Out-GridView` to create a Windows shortcut to the `Out-GridView` window.</span></span>

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

<span data-ttu-id="cc32c-155">此命令列可以在 Windows 快捷方式中使用。</span><span class="sxs-lookup"><span data-stu-id="cc32c-155">This command line can be used in a Windows shortcut.</span></span> <span data-ttu-id="cc32c-156">如果沒有 **Wait** 參數，PowerShell 會在視窗開啟時立即 `Out-GridView` 結束，這會 `Out-GridView` 立即關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="cc32c-156">Without the **Wait** parameter, PowerShell would exit as soon as the `Out-GridView` window opened, which would close the `Out-GridView` window almost immediately.</span></span>

## <span data-ttu-id="cc32c-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cc32c-157">PARAMETERS</span></span>

### <span data-ttu-id="cc32c-158">-InputObject</span><span class="sxs-lookup"><span data-stu-id="cc32c-158">-InputObject</span></span>

<span data-ttu-id="cc32c-159">指定 Cmdlet 接受做為輸入的物件 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-159">Specifies object that the cmdlet accepts as input for `Out-GridView`.</span></span>

<span data-ttu-id="cc32c-160">當您使用 **InputObject** 參數將物件的集合傳送至時 `Out-GridView` ， `Out-GridView` 會將該集合視為一個集合物件，並且會顯示一個代表集合的資料列。</span><span class="sxs-lookup"><span data-stu-id="cc32c-160">When you use the **InputObject** parameter to send a collection of objects to `Out-GridView`, `Out-GridView` treats the collection as one collection object, and it displays one row that represents the collection.</span></span> <span data-ttu-id="cc32c-161">若要顯示集合中的每個物件，請使用管線運算子 (|傳送物件的) `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-161">To display the each object in the collection, use a pipeline operator (|) to send objects to `Out-GridView`.</span></span>

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

### <span data-ttu-id="cc32c-162">-OutputMode</span><span class="sxs-lookup"><span data-stu-id="cc32c-162">-OutputMode</span></span>

<span data-ttu-id="cc32c-163">指定互動式視窗向下傳送管線的專案，做為其他命令的輸入。</span><span class="sxs-lookup"><span data-stu-id="cc32c-163">Specifies the items that the interactive window sends down the pipeline as input to other commands.</span></span>
<span data-ttu-id="cc32c-164">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="cc32c-164">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="cc32c-165">若要從互動式視窗將項目沿著管線向下傳送，請按一下項目來進行選取，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="cc32c-165">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span>

<span data-ttu-id="cc32c-166">這個參數的值會決定您可以沿著管線向下傳送的項目數。</span><span class="sxs-lookup"><span data-stu-id="cc32c-166">The values of this parameter determine how many items you can send down the pipeline.</span></span>

- <span data-ttu-id="cc32c-167">無。</span><span class="sxs-lookup"><span data-stu-id="cc32c-167">None.</span></span>  <span data-ttu-id="cc32c-168">沒有項目。</span><span class="sxs-lookup"><span data-stu-id="cc32c-168">No items.</span></span> <span data-ttu-id="cc32c-169">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="cc32c-169">This is the default value.</span></span>
- <span data-ttu-id="cc32c-170">單一。</span><span class="sxs-lookup"><span data-stu-id="cc32c-170">Single.</span></span> <span data-ttu-id="cc32c-171">零個項目或一個項目。</span><span class="sxs-lookup"><span data-stu-id="cc32c-171">Zero items or one item.</span></span> <span data-ttu-id="cc32c-172">如果下一個命令只能接受一個輸入物件，請使用這個值。</span><span class="sxs-lookup"><span data-stu-id="cc32c-172">Use this value when the next command can take only one input object.</span></span>
- <span data-ttu-id="cc32c-173">多個。</span><span class="sxs-lookup"><span data-stu-id="cc32c-173">Multiple.</span></span> <span data-ttu-id="cc32c-174">零個、一個或許多個項目。</span><span class="sxs-lookup"><span data-stu-id="cc32c-174">Zero, one, or many items.</span></span> <span data-ttu-id="cc32c-175">如果下一個命令可以接受多個輸入物件，請使用這個值。</span><span class="sxs-lookup"><span data-stu-id="cc32c-175">Use this value when the next command can take multiple input objects.</span></span> <span data-ttu-id="cc32c-176">這個值相當於 **Passthru** 參數。</span><span class="sxs-lookup"><span data-stu-id="cc32c-176">This value is equivalent to the **Passthru** parameter.</span></span>

<span data-ttu-id="cc32c-177">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="cc32c-177">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutputModeOption
Parameter Sets: OutputMode
Aliases:
Accepted values: None, Single, Multiple

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc32c-178">-PassThru</span><span class="sxs-lookup"><span data-stu-id="cc32c-178">-PassThru</span></span>

<span data-ttu-id="cc32c-179">指出此 Cmdlet 會將專案從互動式視窗沿著管線向下傳送，以做為其他命令的輸入。</span><span class="sxs-lookup"><span data-stu-id="cc32c-179">Indicates that the cmdlet sends items from the interactive window down the pipeline as input to other commands.</span></span> <span data-ttu-id="cc32c-180">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="cc32c-180">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="cc32c-181">這個參數等同於使用 **OutputMode** 參數的 **Multiple** 值。</span><span class="sxs-lookup"><span data-stu-id="cc32c-181">This parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

<span data-ttu-id="cc32c-182">若要從互動式視窗將項目沿著管線向下傳送，請按一下項目來進行選取，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="cc32c-182">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span> <span data-ttu-id="cc32c-183">支援按住 Shift 鍵並按一下滑鼠左鍵及按住 Ctrl 鍵並按一下滑鼠左鍵來進行選取。</span><span class="sxs-lookup"><span data-stu-id="cc32c-183">Shift-click and Ctrl-click are supported.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PassThru
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc32c-184">-Title</span><span class="sxs-lookup"><span data-stu-id="cc32c-184">-Title</span></span>

<span data-ttu-id="cc32c-185">指定出現在視窗標題列中的文字 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-185">Specifies the text that appears in the title bar of the `Out-GridView` window.</span></span> <span data-ttu-id="cc32c-186">依預設，標題列會顯示叫用的命令 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-186">By default, the title bar displays the command that invokes `Out-GridView`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc32c-187">-Wait</span><span class="sxs-lookup"><span data-stu-id="cc32c-187">-Wait</span></span>

<span data-ttu-id="cc32c-188">指出此 Cmdlet 會抑制命令提示字元，並防止 Windows PowerShell 關閉，直到 `Out-GridView` 視窗關閉為止。</span><span class="sxs-lookup"><span data-stu-id="cc32c-188">Indicates that the cmdlet suppresses the command prompt and prevents Windows PowerShell from closing until the `Out-GridView` window is closed.</span></span> <span data-ttu-id="cc32c-189">依預設，當視窗開啟時，會傳回命令提示字元 `Out-GridView` 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-189">By default, the command prompt returns when the `Out-GridView` window opens.</span></span>

<span data-ttu-id="cc32c-190">這項功能可讓您 `Out-GridView` 在 Windows 快捷方式中使用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cc32c-190">This feature lets you use the `Out-GridView` cmdlets in Windows shortcuts.</span></span> <span data-ttu-id="cc32c-191">當 `Out-GridView` 在沒有 **Wait** 參數的快捷方式中使用時， `Out-GridView` 視窗只會在 PowerShell 關閉之前短暫顯示。</span><span class="sxs-lookup"><span data-stu-id="cc32c-191">When `Out-GridView` is used in a shortcut without the **Wait** parameter, the `Out-GridView` window appears only momentarily before PowerShell closes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Wait
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc32c-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cc32c-192">CommonParameters</span></span>

<span data-ttu-id="cc32c-193">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cc32c-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cc32c-194">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cc32c-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cc32c-195">輸入</span><span class="sxs-lookup"><span data-stu-id="cc32c-195">INPUTS</span></span>

### <span data-ttu-id="cc32c-196">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="cc32c-196">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="cc32c-197">您可以將任何物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cc32c-197">You can send any object to this cmdlet.</span></span>

## <span data-ttu-id="cc32c-198">輸出</span><span class="sxs-lookup"><span data-stu-id="cc32c-198">OUTPUTS</span></span>

### <span data-ttu-id="cc32c-199">無</span><span class="sxs-lookup"><span data-stu-id="cc32c-199">None</span></span>

<span data-ttu-id="cc32c-200">通常 `Out-GridView` 不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="cc32c-200">Normally, `Out-GridView` does not return any objects.</span></span> <span data-ttu-id="cc32c-201">使用 **PassThru** 參數時，代表選取資料列的物件會傳回至管線。</span><span class="sxs-lookup"><span data-stu-id="cc32c-201">When using the **PassThru** parameter, the objects representing the selected rows are returned to the pipeline.</span></span>

## <span data-ttu-id="cc32c-202">注意</span><span class="sxs-lookup"><span data-stu-id="cc32c-202">NOTES</span></span>

<span data-ttu-id="cc32c-203">您無法使用遠端命令在另一部電腦上開啟資料格檢視視窗。</span><span class="sxs-lookup"><span data-stu-id="cc32c-203">You cannot use a remote command to open a grid view window on another computer.</span></span>

<span data-ttu-id="cc32c-204">您傳送給的命令輸出 `Out-GridView` 無法使用 Cmdlet 來格式化 `Format` ，例如 `Format-Table` 或 `Format-Wide` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cc32c-204">The command output that you send to `Out-GridView` cannot be formatted using the `Format` cmdlets, such as `Format-Table` or `Format-Wide` cmdlets.</span></span> <span data-ttu-id="cc32c-205">若要選取屬性，請使用 `Select-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cc32c-205">To select properties, use the `Select-Object` cmdlet.</span></span>

<span data-ttu-id="cc32c-206">來自遠端命令的已還原序列化輸出在資料格檢視中可能無法正確格式化。</span><span class="sxs-lookup"><span data-stu-id="cc32c-206">Deserialized output from remote commands might not be formatted correctly in the grid view window.</span></span>

<span data-ttu-id="cc32c-207">**的鍵盤快速鍵**`Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="cc32c-207">**Keyboard Shortcuts for** `Out-GridView`</span></span>

|              <span data-ttu-id="cc32c-208">使用此按鍵：</span><span class="sxs-lookup"><span data-stu-id="cc32c-208">Use this key:</span></span>              |                                   <span data-ttu-id="cc32c-209">可執行此動作：</span><span class="sxs-lookup"><span data-stu-id="cc32c-209">To perform this action:</span></span>                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <span data-ttu-id="cc32c-210"><kbd>索引標籤</kbd></span><span class="sxs-lookup"><span data-stu-id="cc32c-210"><kbd>Tab</kbd></span></span>                          | <span data-ttu-id="cc32c-211">將游標從 [ **篩選** ] 方塊移到 [ **新增條件** ] 功能表，再移回資料表。</span><span class="sxs-lookup"><span data-stu-id="cc32c-211">Moves the cursor from the **Filter** box to the **Add criteria** menu to the table and back.</span></span> |
| <span data-ttu-id="cc32c-212"><kbd>UpArrow</kbd></span><span class="sxs-lookup"><span data-stu-id="cc32c-212"><kbd>UpArrow</kbd></span></span>                      | <span data-ttu-id="cc32c-213">上移一列。</span><span class="sxs-lookup"><span data-stu-id="cc32c-213">Move up one row.</span></span> <span data-ttu-id="cc32c-214">從資料的第一個資料列移至資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="cc32c-214">Moves to column headers from first row of data.</span></span>                             |
| <span data-ttu-id="cc32c-215"><kbd>Download-downarrow-circled</kbd></span><span class="sxs-lookup"><span data-stu-id="cc32c-215"><kbd>DownArrow</kbd></span></span>                    | <span data-ttu-id="cc32c-216">向下移動一個資料列。</span><span class="sxs-lookup"><span data-stu-id="cc32c-216">Move down one row.</span></span>                                                                           |
| <span data-ttu-id="cc32c-217"><kbd>LeftArrow</kbd></span><span class="sxs-lookup"><span data-stu-id="cc32c-217"><kbd>LeftArrow</kbd></span></span>                    | <span data-ttu-id="cc32c-218">在資料行標頭資料列中，向左移動一欄。</span><span class="sxs-lookup"><span data-stu-id="cc32c-218">In column header row, move left one column.</span></span>                                                  |
| <span data-ttu-id="cc32c-219"><kbd>向右鍵</kbd></span><span class="sxs-lookup"><span data-stu-id="cc32c-219"><kbd>RightArrow</kbd></span></span>                   | <span data-ttu-id="cc32c-220">在資料行標頭資料列中，向右移動一欄。</span><span class="sxs-lookup"><span data-stu-id="cc32c-220">In column header row, move right one column.</span></span>                                                 |
| <span data-ttu-id="cc32c-221"><kbd>CoNtextMenuKey</kbd></span><span class="sxs-lookup"><span data-stu-id="cc32c-221"><kbd>ContextMenuKey</kbd></span></span>               | <span data-ttu-id="cc32c-222">在 [資料行標頭資料列] 中，顯示 [選取欄位] 選項。</span><span class="sxs-lookup"><span data-stu-id="cc32c-222">In column header row, displays the Select Columns option.</span></span>                                    |
| <span data-ttu-id="cc32c-223"><kbd>Enter</kbd> 或 <kbd>空格鍵</kbd></span><span class="sxs-lookup"><span data-stu-id="cc32c-223"><kbd>Enter</kbd> or <kbd>Spacebar</kbd></span></span> | <span data-ttu-id="cc32c-224">在資料行標頭資料列中，將資料行資料排序 (切換 a-z、Z-A) 。</span><span class="sxs-lookup"><span data-stu-id="cc32c-224">In column header row, sort column data (toggle A-Z, Z-A).</span></span>                                    |

<span data-ttu-id="cc32c-225">**如何使用格線視圖視窗功能**</span><span class="sxs-lookup"><span data-stu-id="cc32c-225">**How to Use the Grid View Window Features**</span></span>

<span data-ttu-id="cc32c-226">**隱藏或顯示欄位：**</span><span class="sxs-lookup"><span data-stu-id="cc32c-226">**To hide or show a column:**</span></span>

1. <span data-ttu-id="cc32c-227">以滑鼠右鍵按一下任何欄標題，然後按一下 [ **選取資料行**]。</span><span class="sxs-lookup"><span data-stu-id="cc32c-227">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="cc32c-228">在 [ **選取資料行** ] 對話方塊中，使用方向鍵將選取之資料行之間的資料行移至 [可用的資料行] 方塊。</span><span class="sxs-lookup"><span data-stu-id="cc32c-228">In the **Select Columns** dialog box, use the arrow keys to move the columns between the Selected columns to the Available columns boxes.</span></span> <span data-ttu-id="cc32c-229">格線視圖視窗中只會顯示 [ **選取資料行** ] 方塊中的資料行。</span><span class="sxs-lookup"><span data-stu-id="cc32c-229">Only columns in the **Select Columns** box appear in the grid view window.</span></span>

<span data-ttu-id="cc32c-230">**重新排列欄位：**</span><span class="sxs-lookup"><span data-stu-id="cc32c-230">**To reorder columns:**</span></span>

<span data-ttu-id="cc32c-231">您可以將資料行拖放到所需的位置。</span><span class="sxs-lookup"><span data-stu-id="cc32c-231">You can drag and drop columns into the desired location.</span></span> <span data-ttu-id="cc32c-232">或者，使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="cc32c-232">Or use the following steps:</span></span>

1. <span data-ttu-id="cc32c-233">以滑鼠右鍵按一下任何欄標題，然後按一下 [ **選取資料行**]。</span><span class="sxs-lookup"><span data-stu-id="cc32c-233">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="cc32c-234">在 [ **選取資料行** ] 對話方塊中，使用 [ **上移** ] 和 **[下移] 按鈕來** 重新排列資料行。</span><span class="sxs-lookup"><span data-stu-id="cc32c-234">In the **Select Columns** dialog box, use the **Move up** and **Move down** buttons to reorder the columns.</span></span> <span data-ttu-id="cc32c-235">清單頂端的欄位在資料格檢視視窗中會顯示在清單底部欄位的左邊。</span><span class="sxs-lookup"><span data-stu-id="cc32c-235">Columns at the top of the list appear to the left of columns at the bottom of the list in the grid view window.</span></span>

<span data-ttu-id="cc32c-236">**如何排序表格資料**</span><span class="sxs-lookup"><span data-stu-id="cc32c-236">**How to Sort Table Data**</span></span>

- <span data-ttu-id="cc32c-237">若要排序資料，請按一下欄標題。</span><span class="sxs-lookup"><span data-stu-id="cc32c-237">To sort the data, click a column header.</span></span>
- <span data-ttu-id="cc32c-238">若要變更排序順序，請再按一下欄標題。</span><span class="sxs-lookup"><span data-stu-id="cc32c-238">To change the sort order, click the column header again.</span></span> <span data-ttu-id="cc32c-239">每次按一下相同的標題，排序順序就會在遞增順序與遞減順序之間切換。</span><span class="sxs-lookup"><span data-stu-id="cc32c-239">Each time you click the same header, the sort order toggles between ascending to descending order.</span></span> <span data-ttu-id="cc32c-240">欄標題中的三角形表示目前的順序。</span><span class="sxs-lookup"><span data-stu-id="cc32c-240">The current order is indicated by a triangle in the column header.</span></span>

<span data-ttu-id="cc32c-241">**如何選取表格資料**</span><span class="sxs-lookup"><span data-stu-id="cc32c-241">**How to Select Table Data**</span></span>

- <span data-ttu-id="cc32c-242">若要選取資料列，請選取資料列，或使用向上或向下箭號來流覽至資料列。</span><span class="sxs-lookup"><span data-stu-id="cc32c-242">To select a row, select the row or use the up or down arrow to navigate to the row.</span></span>
- <span data-ttu-id="cc32c-243">若要選取除了標頭資料列) 以外的所有資料列 (，請按下<kbd>CTRL</kbd> + <kbd>鍵</kbd>。</span><span class="sxs-lookup"><span data-stu-id="cc32c-243">To select all rows (except for the header row), press <kbd>CTRL</kbd>+<kbd>A</kbd>.</span></span>
- <span data-ttu-id="cc32c-244">若要選取連續的資料列，請按住 <kbd>SHIFT</kbd> 鍵，同時按一下資料列或使用方向鍵。</span><span class="sxs-lookup"><span data-stu-id="cc32c-244">To select consecutive rows, press and hold the <kbd>SHIFT</kbd> key while clicking the rows or using the arrow keys.</span></span>
- <span data-ttu-id="cc32c-245">若要選取不連續的資料列，請按 <kbd>CTRL</kbd> 鍵，然後按一下將資料列加入至選取專案。</span><span class="sxs-lookup"><span data-stu-id="cc32c-245">To select nonconsecutive rows, press the <kbd>CTRL</kbd> key and click to add a row to the selection.</span></span>
- <span data-ttu-id="cc32c-246">您無法選取欄位，也無法選取整個欄標題列。</span><span class="sxs-lookup"><span data-stu-id="cc32c-246">You cannot select columns, and you cannot select the entire column header row.</span></span>

<span data-ttu-id="cc32c-247">**如何複製列**</span><span class="sxs-lookup"><span data-stu-id="cc32c-247">**How to Copy Rows**</span></span>

- <span data-ttu-id="cc32c-248">若要從表格複製一列或多列，請選取那些列，然後按 CTRL+C。</span><span class="sxs-lookup"><span data-stu-id="cc32c-248">To copy one or more rows from the table, select the rows and then press CTRL+C.</span></span>

  <span data-ttu-id="cc32c-249">您可以將資料貼到任何文字或試算表程式中。</span><span class="sxs-lookup"><span data-stu-id="cc32c-249">You can paste the data into any text or spreadsheet program.</span></span> <span data-ttu-id="cc32c-250">您無法複製欄位或或列的部分，也無法複製欄標題列。</span><span class="sxs-lookup"><span data-stu-id="cc32c-250">You cannot copy columns or parts of rows and you cannot copy the column header row.</span></span>

<span data-ttu-id="cc32c-251">**如何在資料表中搜尋 (快速篩選)**</span><span class="sxs-lookup"><span data-stu-id="cc32c-251">**How to Search in the Table (Quick Filter)**</span></span>

<span data-ttu-id="cc32c-252">您可以使用 [篩選] 方塊來搜尋資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="cc32c-252">Use the Filter box to search for data in the table.</span></span> <span data-ttu-id="cc32c-253">在方塊中輸入時，只有包含輸入之文字的項目才會顯示在表格中。</span><span class="sxs-lookup"><span data-stu-id="cc32c-253">When you type in the box, only items that include the typed text appear in the table.</span></span>

- <span data-ttu-id="cc32c-254">搜尋文字。</span><span class="sxs-lookup"><span data-stu-id="cc32c-254">Search for text.</span></span> <span data-ttu-id="cc32c-255">若要搜尋表格中的文字，請在 [篩選] 方塊中輸入要尋找的文字。</span><span class="sxs-lookup"><span data-stu-id="cc32c-255">To search for text in the table, in the Filter box, type the text to find.</span></span>
- <span data-ttu-id="cc32c-256">搜尋多個字。</span><span class="sxs-lookup"><span data-stu-id="cc32c-256">Search for multiple words.</span></span> <span data-ttu-id="cc32c-257">若要搜尋表格中的多個字，請輸入文字並以空格分隔。</span><span class="sxs-lookup"><span data-stu-id="cc32c-257">To search for multiple words in the table, type the words separated by spaces.</span></span> <span data-ttu-id="cc32c-258">`Out-GridView` 顯示包含所有文字 (邏輯 AND) 的資料列。</span><span class="sxs-lookup"><span data-stu-id="cc32c-258">`Out-GridView` displays rows that include all the words (logical AND).</span></span>
- <span data-ttu-id="cc32c-259">搜尋片語。</span><span class="sxs-lookup"><span data-stu-id="cc32c-259">Search for literal phrases.</span></span> <span data-ttu-id="cc32c-260">若要搜尋包含空格或特殊字元的片語，請以引號括住該片語。</span><span class="sxs-lookup"><span data-stu-id="cc32c-260">To search for phrases that include spaces or special characters, enclose the phrase in quotation marks.</span></span> <span data-ttu-id="cc32c-261">`Out-GridView` 顯示包含片語完全相符的資料列。</span><span class="sxs-lookup"><span data-stu-id="cc32c-261">`Out-GridView` displays rows that include an exact match for the phrase.</span></span>
- <span data-ttu-id="cc32c-262">在欄位中搜尋。</span><span class="sxs-lookup"><span data-stu-id="cc32c-262">Search in columns.</span></span> <span data-ttu-id="cc32c-263">若要在一個或多個欄位中搜尋文字，請使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="cc32c-263">To search for text in one or more columns, use the following format:</span></span>

  `<column>:<text> [<column>:<text>] ...`

  <span data-ttu-id="cc32c-264">例如，若要在 **DisplayName** 欄位中尋找 "Net"，請在 [ **篩選** ] 方塊中輸入：</span><span class="sxs-lookup"><span data-stu-id="cc32c-264">For example, to find "Net" in the **DisplayName** column, in the **Filter** box, type:</span></span>

  `displayname:net`

  <span data-ttu-id="cc32c-265">若要在 [ **DisplayName** ] 和 [ **名稱** ] 資料行中尋找 "Net" 的資料列，請在 [ **篩選** ] 方塊中輸入：</span><span class="sxs-lookup"><span data-stu-id="cc32c-265">To find rows with "Net" in the **DisplayName** and **Name** columns, in the **Filter** box, type:</span></span>

  `displayname:net name:net`

- <span data-ttu-id="cc32c-266">關閉搜尋。</span><span class="sxs-lookup"><span data-stu-id="cc32c-266">Turn off search.</span></span> <span data-ttu-id="cc32c-267">若要再次顯示整份資料表，請按一下 [ **篩選** ] 方塊右上角的 [紅色 X] 按鈕，或從 [ **篩選** ] 方塊中刪除文字。</span><span class="sxs-lookup"><span data-stu-id="cc32c-267">To display the entire table again, click the red X button in the top right corner of the **Filter** box or delete the text from the **Filter** box.</span></span>

<span data-ttu-id="cc32c-268">**使用條件來篩選表格**</span><span class="sxs-lookup"><span data-stu-id="cc32c-268">**Use Criteria to Filter the Table**</span></span>

<span data-ttu-id="cc32c-269">您可以使用規則或準則來判斷哪些專案要顯示在資料表中。</span><span class="sxs-lookup"><span data-stu-id="cc32c-269">You can use rules or criteria to determine which items are displayed in the table.</span></span> <span data-ttu-id="cc32c-270">只有當專案滿足您所建立的所有條件時，才會出現這些專案。</span><span class="sxs-lookup"><span data-stu-id="cc32c-270">Items appear only when they satisfy all the criteria that you establish.</span></span> <span data-ttu-id="cc32c-271">可用的條件取決於資料格檢視視窗中所顯示之物件的屬性，以及這些屬性的 .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="cc32c-271">The available criteria are determined by the properties of the objects displayed in the grid view window and the .NET Framework types of those properties.</span></span>

<span data-ttu-id="cc32c-272">每個條件都具有下列格式：</span><span class="sxs-lookup"><span data-stu-id="cc32c-272">Each criterion has the following format:</span></span>

`<column> <operator> <value>`

<span data-ttu-id="cc32c-273">不同屬性的準則是由 **和** 連接。</span><span class="sxs-lookup"><span data-stu-id="cc32c-273">Criteria for different properties are connected by **AND**.</span></span> <span data-ttu-id="cc32c-274">相同屬性的準則是由 **或** 連接。</span><span class="sxs-lookup"><span data-stu-id="cc32c-274">Criteria for the same property are connected by **OR**.</span></span> <span data-ttu-id="cc32c-275">您無法變更邏輯連接子。</span><span class="sxs-lookup"><span data-stu-id="cc32c-275">You cannot change the logical connectors.</span></span>

<span data-ttu-id="cc32c-276">條件只會影響顯示。</span><span class="sxs-lookup"><span data-stu-id="cc32c-276">The criteria only affects the display.</span></span> <span data-ttu-id="cc32c-277">它不會將項目從表格中刪除。</span><span class="sxs-lookup"><span data-stu-id="cc32c-277">It does not delete items from the table.</span></span>

<span data-ttu-id="cc32c-278">**如何新增條件**</span><span class="sxs-lookup"><span data-stu-id="cc32c-278">**How to Add Criteria**</span></span>

1. <span data-ttu-id="cc32c-279">若要顯示 [ **新增條件** ] 功能表按鈕，請按一下視窗右上角的展開箭號。</span><span class="sxs-lookup"><span data-stu-id="cc32c-279">To display the **Add criteria** menu button, in the upper right corner of the window, click the Expand arrow.</span></span>
2. <span data-ttu-id="cc32c-280">按一下 [ **新增條件** ] 功能表按鈕。</span><span class="sxs-lookup"><span data-stu-id="cc32c-280">Click the **Add Criteria** menu button.</span></span>
3. <span data-ttu-id="cc32c-281">按一下來選取欄位 (屬性)。</span><span class="sxs-lookup"><span data-stu-id="cc32c-281">Click to select columns (properties).</span></span> <span data-ttu-id="cc32c-282">您可以選取一個或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="cc32c-282">You can select one or many properties.</span></span>
4. <span data-ttu-id="cc32c-283">當您完成選取 [屬性] 時，按一下 [ **加入** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cc32c-283">When you are finished selecting properties, click the **Add** button.</span></span>
5. <span data-ttu-id="cc32c-284">若要取消新增，請按一下 [ **取消**]。</span><span class="sxs-lookup"><span data-stu-id="cc32c-284">To cancel the additions, click **Cancel**.</span></span>
6. <span data-ttu-id="cc32c-285">若要新增更多條件，請再按一下 [ **新增條件** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cc32c-285">To add more criteria, click the **Add Criteria** button again.</span></span>

<span data-ttu-id="cc32c-286">**如何編輯條件**</span><span class="sxs-lookup"><span data-stu-id="cc32c-286">**How to Edit a Criterion**</span></span>

- <span data-ttu-id="cc32c-287">若要變更運算子，請按一下藍色運算子值，然後從下拉式清單中選取不同的運算子。</span><span class="sxs-lookup"><span data-stu-id="cc32c-287">To change an operator, click the blue operator value, and then select a different operator from the drop-down list.</span></span>
- <span data-ttu-id="cc32c-288">若要輸入或變更某個值，請在值方塊中輸入值。</span><span class="sxs-lookup"><span data-stu-id="cc32c-288">To enter or change a value, type a value in the value box.</span></span> <span data-ttu-id="cc32c-289">如果輸入的值無效，就會顯示圓形的 X 圖示。</span><span class="sxs-lookup"><span data-stu-id="cc32c-289">If you enter a value that is not valid, a circular X icon appears.</span></span> <span data-ttu-id="cc32c-290">若要將它移除，請變更該值。</span><span class="sxs-lookup"><span data-stu-id="cc32c-290">To remove it, change the value.</span></span>
- <span data-ttu-id="cc32c-291">若要建立 **或** 語句，請新增具有相同屬性的條件。</span><span class="sxs-lookup"><span data-stu-id="cc32c-291">To create an **OR** statement, add a criteria with the same property.</span></span>

<span data-ttu-id="cc32c-292">**如何刪除條件**</span><span class="sxs-lookup"><span data-stu-id="cc32c-292">**How to Delete Criteria**</span></span>

- <span data-ttu-id="cc32c-293">若要刪除選取的條件，請按一下每個條件旁邊的紅色 X。</span><span class="sxs-lookup"><span data-stu-id="cc32c-293">To delete selected criteria, click the red X beside each criterion.</span></span>
- <span data-ttu-id="cc32c-294">若要刪除所有條件，請按一下 [ **全部清除** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="cc32c-294">To delete all criteria, click the **Clear All** button.</span></span>

## <span data-ttu-id="cc32c-295">相關連結</span><span class="sxs-lookup"><span data-stu-id="cc32c-295">RELATED LINKS</span></span>

[<span data-ttu-id="cc32c-296">Out-File</span><span class="sxs-lookup"><span data-stu-id="cc32c-296">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="cc32c-297">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="cc32c-297">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="cc32c-298">Out-String</span><span class="sxs-lookup"><span data-stu-id="cc32c-298">Out-String</span></span>](Out-String.md)
