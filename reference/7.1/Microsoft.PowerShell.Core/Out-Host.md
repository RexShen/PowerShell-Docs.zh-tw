---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: 9f53f137ecdd415e0185e380cba6ff817972b82e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205003"
---
# <span data-ttu-id="97ed8-103">Out-Host</span><span class="sxs-lookup"><span data-stu-id="97ed8-103">Out-Host</span></span>

## <span data-ttu-id="97ed8-104">概要</span><span class="sxs-lookup"><span data-stu-id="97ed8-104">SYNOPSIS</span></span>
<span data-ttu-id="97ed8-105">將輸出傳送至命令列。</span><span class="sxs-lookup"><span data-stu-id="97ed8-105">Sends output to the command line.</span></span>

## <span data-ttu-id="97ed8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="97ed8-106">SYNTAX</span></span>

### <span data-ttu-id="97ed8-107">全部</span><span class="sxs-lookup"><span data-stu-id="97ed8-107">All</span></span>

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="97ed8-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="97ed8-108">DESCRIPTION</span></span>

<span data-ttu-id="97ed8-109">`Out-Host`Cmdlet 會將輸出傳送至 PowerShell 主機以供顯示。</span><span class="sxs-lookup"><span data-stu-id="97ed8-109">The `Out-Host` cmdlet sends output to the PowerShell host for display.</span></span> <span data-ttu-id="97ed8-110">主機會在命令列中顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="97ed8-110">The host displays the output at the command line.</span></span> <span data-ttu-id="97ed8-111">因為 `Out-Host` 是預設值，除非您想要使用其參數，否則不需要指定它。</span><span class="sxs-lookup"><span data-stu-id="97ed8-111">Because `Out-Host` is the default, you don't have to specify it unless you want to use its parameters.</span></span>

<span data-ttu-id="97ed8-112">`Out-Host` 會自動附加至每個執行的命令。</span><span class="sxs-lookup"><span data-stu-id="97ed8-112">`Out-Host` is automatically appended to every command that is executed.</span></span> <span data-ttu-id="97ed8-113">它會將管線的輸出傳遞給執行命令的主機。</span><span class="sxs-lookup"><span data-stu-id="97ed8-113">It passes the output of the pipeline to the host executing the command.</span></span> <span data-ttu-id="97ed8-114">`Out-Host` 忽略 ANSI escape 序列。</span><span class="sxs-lookup"><span data-stu-id="97ed8-114">`Out-Host` ignores ANSI escape sequences.</span></span> <span data-ttu-id="97ed8-115">Escape 序列是由主機處理。</span><span class="sxs-lookup"><span data-stu-id="97ed8-115">The escape sequences are handled by the host.</span></span> <span data-ttu-id="97ed8-116">`Out-Host` 將 ANSI escape 序列傳遞給主機，而不嘗試解讀或變更它們。</span><span class="sxs-lookup"><span data-stu-id="97ed8-116">`Out-Host` passes ANSI escape sequences to the host without trying to interpret or change them.</span></span>

## <span data-ttu-id="97ed8-117">範例</span><span class="sxs-lookup"><span data-stu-id="97ed8-117">EXAMPLES</span></span>

### <span data-ttu-id="97ed8-118">範例1：一次顯示一個頁面的輸出</span><span class="sxs-lookup"><span data-stu-id="97ed8-118">Example 1: Display output one page at a time</span></span>

<span data-ttu-id="97ed8-119">此範例會顯示一次一個頁面的系統處理。</span><span class="sxs-lookup"><span data-stu-id="97ed8-119">This example displays the system processes one page at a time.</span></span>

```powershell
Get-Process | Out-Host -Paging
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     30    24.12      36.95      15.86   21004  14 ApplicationFrameHost
     55    24.33      60.48      10.80   12904  14 BCompare
<SPACE> next page; <CR> next line; Q quit
      9     4.71       8.94       0.00   16864  14 explorer
<SPACE> next page; <CR> next line; Q quit
```

<span data-ttu-id="97ed8-120">`Get-Process` 取得系統進程，並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="97ed8-120">`Get-Process` gets the system processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="97ed8-121">`Out-Host` 使用 **分頁** 參數，一次顯示一頁數據。</span><span class="sxs-lookup"><span data-stu-id="97ed8-121">`Out-Host` uses the **Paging** parameter to display one page of data at a time.</span></span>

### <span data-ttu-id="97ed8-122">範例2：使用變數作為輸入</span><span class="sxs-lookup"><span data-stu-id="97ed8-122">Example 2: Use a variable as input</span></span>

<span data-ttu-id="97ed8-123">這個範例會使用儲存在變數中的物件做為的輸入 `Out-Host` 。</span><span class="sxs-lookup"><span data-stu-id="97ed8-123">This example uses objects stored in a variable as the input for `Out-Host`.</span></span>

```powershell
$io = Get-History
Out-Host -InputObject $io
```

<span data-ttu-id="97ed8-124">`Get-History` 取得 PowerShell 會話的歷程記錄，並將物件儲存在 `$io` 變數中。</span><span class="sxs-lookup"><span data-stu-id="97ed8-124">`Get-History` gets the PowerShell session's history, and stores the objects in the `$io` variable.</span></span>
<span data-ttu-id="97ed8-125">`Out-Host` 使用 **InputObject** 參數來指定 `$io` 變數並顯示歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="97ed8-125">`Out-Host` uses the **InputObject** parameter to specify the `$io` variable and displays the history.</span></span>

## <span data-ttu-id="97ed8-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="97ed8-126">PARAMETERS</span></span>

### <span data-ttu-id="97ed8-127">-InputObject</span><span class="sxs-lookup"><span data-stu-id="97ed8-127">-InputObject</span></span>

<span data-ttu-id="97ed8-128">指定寫入主控台的物件。</span><span class="sxs-lookup"><span data-stu-id="97ed8-128">Specifies the objects that are written to the console.</span></span> <span data-ttu-id="97ed8-129">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="97ed8-129">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="97ed8-130">-Paging</span><span class="sxs-lookup"><span data-stu-id="97ed8-130">-Paging</span></span>

<span data-ttu-id="97ed8-131">指出 `Out-Host` 一次會顯示一頁的輸出，並等待使用者輸入再顯示其餘的頁面。</span><span class="sxs-lookup"><span data-stu-id="97ed8-131">Indicates that `Out-Host` displays one page of output at a time, and waits for user input before the remaining pages are displayed.</span></span> <span data-ttu-id="97ed8-132">依預設，所有輸出都會顯示在單一頁面上。</span><span class="sxs-lookup"><span data-stu-id="97ed8-132">By default, all the output is displayed on a single page.</span></span> <span data-ttu-id="97ed8-133">頁面大小取決於主機特性。</span><span class="sxs-lookup"><span data-stu-id="97ed8-133">The page size is determined by the characteristics of the host.</span></span>

<span data-ttu-id="97ed8-134">按 <kbd>空格鍵</kbd> 以顯示下一頁的輸出，或按 <kbd>Enter</kbd> 鍵來查看下一行輸出。</span><span class="sxs-lookup"><span data-stu-id="97ed8-134">Press the <kbd>Space</kbd> bar to display the next page of output or the <kbd>Enter</kbd> key to view the next line of output.</span></span> <span data-ttu-id="97ed8-135">按 <kbd>Q</kbd> 鍵結束。</span><span class="sxs-lookup"><span data-stu-id="97ed8-135">Press <kbd>Q</kbd> to quit.</span></span>

<span data-ttu-id="97ed8-136">**分頁** 類似于 **更多** 命令。</span><span class="sxs-lookup"><span data-stu-id="97ed8-136">**Paging** is similar to the **more** command.</span></span>

> [!NOTE]
> <span data-ttu-id="97ed8-137">PowerShell ISE 主機不支援 **分頁** 參數。</span><span class="sxs-lookup"><span data-stu-id="97ed8-137">The **Paging** parameter isn't supported by the PowerShell ISE host.</span></span>

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

### <span data-ttu-id="97ed8-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="97ed8-138">CommonParameters</span></span>

<span data-ttu-id="97ed8-139">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="97ed8-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="97ed8-140">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="97ed8-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="97ed8-141">輸入</span><span class="sxs-lookup"><span data-stu-id="97ed8-141">INPUTS</span></span>

### <span data-ttu-id="97ed8-142">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="97ed8-142">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="97ed8-143">您可以將物件沿著管線向下傳送至 `Out-Host` 。</span><span class="sxs-lookup"><span data-stu-id="97ed8-143">You can send objects down the pipeline to `Out-Host`.</span></span>

## <span data-ttu-id="97ed8-144">輸出</span><span class="sxs-lookup"><span data-stu-id="97ed8-144">OUTPUTS</span></span>

### <span data-ttu-id="97ed8-145">無</span><span class="sxs-lookup"><span data-stu-id="97ed8-145">None</span></span>

<span data-ttu-id="97ed8-146">`Out-Host` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="97ed8-146">`Out-Host` doesn't generate any output.</span></span> <span data-ttu-id="97ed8-147">它會將物件傳送至主控制項以供顯示。</span><span class="sxs-lookup"><span data-stu-id="97ed8-147">It sends objects to the host for display.</span></span>

## <span data-ttu-id="97ed8-148">注意</span><span class="sxs-lookup"><span data-stu-id="97ed8-148">NOTES</span></span>

<span data-ttu-id="97ed8-149">所有 PowerShell 主機都不支援 **分頁** 參數。</span><span class="sxs-lookup"><span data-stu-id="97ed8-149">The **Paging** parameter isn't supported by all PowerShell hosts.</span></span> <span data-ttu-id="97ed8-150">例如，如果您在 PowerShell ISE 中使用 **分頁** 參數，則會顯示下列錯誤： `out-lineoutput : The method or operation is not implemented.`</span><span class="sxs-lookup"><span data-stu-id="97ed8-150">For example, if you use the **Paging** parameter in the PowerShell ISE, the following error is displayed: `out-lineoutput : The method or operation is not implemented.`</span></span>

<span data-ttu-id="97ed8-151">包含 **Out** 動詞的 Cmdlet 不會將 `Out-` 物件格式化。</span><span class="sxs-lookup"><span data-stu-id="97ed8-151">The cmdlets that contain the **Out** verb, `Out-`, don't format objects.</span></span> <span data-ttu-id="97ed8-152">它們會轉譯物件，並將它們傳送至指定的顯示目的地。</span><span class="sxs-lookup"><span data-stu-id="97ed8-152">They render objects and send them to the specified display destination.</span></span> <span data-ttu-id="97ed8-153">如果您將未格式化的物件傳送至 `Out-` Cmdlet，此 Cmdlet 會將它傳送到格式化 Cmdlet，然後才轉譯它。</span><span class="sxs-lookup"><span data-stu-id="97ed8-153">If you send an unformatted object to an `Out-` cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.</span></span>

<span data-ttu-id="97ed8-154">`Out-`Cmdlet 沒有名稱或檔案路徑的參數。</span><span class="sxs-lookup"><span data-stu-id="97ed8-154">The `Out-` cmdlets don't have parameters for names or file paths.</span></span> <span data-ttu-id="97ed8-155">若要將資料傳送至 `Out-` Cmdlet，請使用管線將 PowerShell 命令的輸出傳送至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="97ed8-155">To send data to an `Out-` cmdlet, use the pipeline to send a PowerShell command's output to the cmdlet.</span></span> <span data-ttu-id="97ed8-156">或者，您可以將資料儲存在變數中，然後使用 **InputObject** 參數將資料傳遞給 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="97ed8-156">Or, you can store data in a variable and use the **InputObject** parameter to pass the data to the cmdlet.</span></span>

<span data-ttu-id="97ed8-157">`Out-Host` 傳送資料，但不會產生任何輸出物件。</span><span class="sxs-lookup"><span data-stu-id="97ed8-157">`Out-Host` sends data, but it doesn't produce any output objects.</span></span> <span data-ttu-id="97ed8-158">如果您將的輸出管線 `Out-Host` 至 `Get-Member` Cmdlet，則會 `Get-Member` 報告未指定任何物件。</span><span class="sxs-lookup"><span data-stu-id="97ed8-158">If you pipeline the output of `Out-Host` to the `Get-Member` cmdlet, `Get-Member` reports that no objects have been specified.</span></span>

## <span data-ttu-id="97ed8-159">相關連結</span><span class="sxs-lookup"><span data-stu-id="97ed8-159">RELATED LINKS</span></span>

[<span data-ttu-id="97ed8-160">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="97ed8-160">Clear-Host</span></span>](Clear-Host.md)

[<span data-ttu-id="97ed8-161">Out-Default</span><span class="sxs-lookup"><span data-stu-id="97ed8-161">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="97ed8-162">Out-File</span><span class="sxs-lookup"><span data-stu-id="97ed8-162">Out-File</span></span>](../Microsoft.PowerShell.Utility/Out-File.md)

[<span data-ttu-id="97ed8-163">Out-Null</span><span class="sxs-lookup"><span data-stu-id="97ed8-163">Out-Null</span></span>](Out-Null.md)

[<span data-ttu-id="97ed8-164">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="97ed8-164">Out-Printer</span></span>](../Microsoft.PowerShell.Utility/Out-Printer.md)

[<span data-ttu-id="97ed8-165">Out-String</span><span class="sxs-lookup"><span data-stu-id="97ed8-165">Out-String</span></span>](../Microsoft.PowerShell.Utility/Out-String.md)

[<span data-ttu-id="97ed8-166">Write-Host</span><span class="sxs-lookup"><span data-stu-id="97ed8-166">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)
