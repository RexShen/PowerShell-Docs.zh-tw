---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: fdfbb75bf95c8dc248441b6399312ed0592f62de
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202164"
---
# <span data-ttu-id="94fe2-103">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="94fe2-103">Tee-Object</span></span>

## <span data-ttu-id="94fe2-104">概要</span><span class="sxs-lookup"><span data-stu-id="94fe2-104">SYNOPSIS</span></span>
<span data-ttu-id="94fe2-105">將命令輸出儲存至檔案或變數，同時將它透過管線傳送。</span><span class="sxs-lookup"><span data-stu-id="94fe2-105">Saves command output in a file or variable and also sends it down the pipeline.</span></span>

## <span data-ttu-id="94fe2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="94fe2-106">SYNTAX</span></span>

### <span data-ttu-id="94fe2-107">File (預設值)</span><span class="sxs-lookup"><span data-stu-id="94fe2-107">File (Default)</span></span>

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### <span data-ttu-id="94fe2-108">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="94fe2-108">LiteralFile</span></span>

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### <span data-ttu-id="94fe2-109">變數</span><span class="sxs-lookup"><span data-stu-id="94fe2-109">Variable</span></span>

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## <span data-ttu-id="94fe2-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="94fe2-110">DESCRIPTION</span></span>

<span data-ttu-id="94fe2-111">`Tee-Object`指令程式會將輸出重新導向，也就是說，它會以兩個方向傳送命令的輸出 (例如字母 T) 。</span><span class="sxs-lookup"><span data-stu-id="94fe2-111">The `Tee-Object` cmdlet redirects output, that is, it sends the output of a command in two directions (like the letter T).</span></span> <span data-ttu-id="94fe2-112">它會將輸出儲存至檔案或變數，同時將它透過管線傳送。</span><span class="sxs-lookup"><span data-stu-id="94fe2-112">It stores the output in a file or variable and also sends it down the pipeline.</span></span> <span data-ttu-id="94fe2-113">如果 `Tee-Object` 是管線中的最後一個命令，命令輸出就會顯示在提示字元中。</span><span class="sxs-lookup"><span data-stu-id="94fe2-113">If `Tee-Object` is the last command in the pipeline, the command output is displayed at the prompt.</span></span>

## <span data-ttu-id="94fe2-114">範例</span><span class="sxs-lookup"><span data-stu-id="94fe2-114">EXAMPLES</span></span>

### <span data-ttu-id="94fe2-115">範例1：將進程輸出至檔案和主控台</span><span class="sxs-lookup"><span data-stu-id="94fe2-115">Example 1: Output processes to a file and to the console</span></span>

<span data-ttu-id="94fe2-116">此範例會取得在電腦上執行的處理常式清單，並將結果傳送至檔案。</span><span class="sxs-lookup"><span data-stu-id="94fe2-116">This example gets a list of the processes running on the computer and sends the result to a file.</span></span>
<span data-ttu-id="94fe2-117">因為沒有指定第二個路徑，因此處理程序也會顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="94fe2-117">Because a second path is not specified, the processes are also displayed in the console.</span></span>

```powershell
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
83       4     2300       4520    39     0.30    4032 00THotkey
272      6     1400       3944    34     0.06    3088 alg
81       3      804       3284    21     2.45     148 ApntEx
81       4     2008       5808    38     0.75    3684 Apoint
...
```

### <span data-ttu-id="94fe2-118">範例2：將進程輸出到變數和 `Select-Object`</span><span class="sxs-lookup"><span data-stu-id="94fe2-118">Example 2: Output processes to a variable and `Select-Object`</span></span>

<span data-ttu-id="94fe2-119">這個範例會取得在電腦上執行的處理常式清單、將它們儲存到 `$proc` 變數，然後將它們傳送至 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="94fe2-119">This example gets a list of the processes running on the computer, saves them to the `$proc` variable, and pipes them to `Select-Object`.</span></span>

```powershell
Get-Process notepad | Tee-Object -Variable proc | Select-Object processname,handles
```

```Output
ProcessName                              Handles
-----------                              -------
notepad                                  43
notepad                                  37
notepad                                  38
notepad                                  38
```

<span data-ttu-id="94fe2-120">`Select-Object`Cmdlet 會選取 **ProcessName** 並 **處理** 屬性。</span><span class="sxs-lookup"><span data-stu-id="94fe2-120">The `Select-Object` cmdlet selects the **ProcessName** and **Handles** properties.</span></span> <span data-ttu-id="94fe2-121">請注意， `$proc` 變數包含所傳回的預設資訊 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="94fe2-121">Note that the `$proc` variable includes the default information returned by `Get-Process`.</span></span>

### <span data-ttu-id="94fe2-122">範例3：將系統檔案輸出到兩個記錄檔</span><span class="sxs-lookup"><span data-stu-id="94fe2-122">Example 3: Output system files to two log files</span></span>

<span data-ttu-id="94fe2-123">此範例會將系統檔案清單儲存在兩個記錄檔中，也就是累計檔案和目前的檔案。</span><span class="sxs-lookup"><span data-stu-id="94fe2-123">This example saves a list of system files in a two log files, a cumulative file and a current file.</span></span>

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

<span data-ttu-id="94fe2-124">此命令會使用 `Get-ChildItem` Cmdlet 對 D：磁片磁碟機上的系統檔案進行遞迴搜尋。</span><span class="sxs-lookup"><span data-stu-id="94fe2-124">The command uses the `Get-ChildItem` cmdlet to do a recursive search for system files on the D: drive.</span></span> <span data-ttu-id="94fe2-125">管線運算子 (|) 會將清單傳送至，這會將清單附加至 AllSystemFiles.txt 檔案，然後將清單 `Tee-Object` 向下傳遞至 `Out-File` Cmdlet，以將清單儲存在 NewSystemFiles.txt 檔案中。</span><span class="sxs-lookup"><span data-stu-id="94fe2-125">A pipeline operator (|) sends the list to `Tee-Object`, which appends the list to the AllSystemFiles.txt file and passes the list down the pipeline to the `Out-File` cmdlet, which saves the list in the NewSystemFiles.txt file.</span></span>

## <span data-ttu-id="94fe2-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="94fe2-126">PARAMETERS</span></span>

### <span data-ttu-id="94fe2-127">-Append</span><span class="sxs-lookup"><span data-stu-id="94fe2-127">-Append</span></span>

<span data-ttu-id="94fe2-128">指出 Cmdlet 會將輸出附加至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="94fe2-128">Indicates that the cmdlet appends the output to the specified file.</span></span> <span data-ttu-id="94fe2-129">如果沒有這個參數，新內容會取代檔案中的任何現有內容而不會發出警告。</span><span class="sxs-lookup"><span data-stu-id="94fe2-129">Without this parameter, the new content replaces any existing content in the file without warning.</span></span>

<span data-ttu-id="94fe2-130">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="94fe2-130">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94fe2-131">-FilePath</span><span class="sxs-lookup"><span data-stu-id="94fe2-131">-FilePath</span></span>

<span data-ttu-id="94fe2-132">指定此 Cmdlet 將物件儲存到萬用字元的檔案，但必須解析為單一檔案。</span><span class="sxs-lookup"><span data-stu-id="94fe2-132">Specifies a file that this cmdlet saves the object to Wildcard characters are permitted, but must resolve to a single file.</span></span>

```yaml
Type: System.String
Parameter Sets: File
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="94fe2-133">-InputObject</span><span class="sxs-lookup"><span data-stu-id="94fe2-133">-InputObject</span></span>

<span data-ttu-id="94fe2-134">指定要儲存和顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="94fe2-134">Specifies the object to be saved and displayed.</span></span> <span data-ttu-id="94fe2-135">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="94fe2-135">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="94fe2-136">您也可以使用管線將物件傳送至 `Tee-Object` 。</span><span class="sxs-lookup"><span data-stu-id="94fe2-136">You can also pipe an object to `Tee-Object`.</span></span>

<span data-ttu-id="94fe2-137">當您搭配使用 **inputobject** 參數與時， `Tee-Object` 不會將命令結果傳送至，而是 `Tee-Object` 會將 **inputobject** 值視為單一物件（即使值是集合）。</span><span class="sxs-lookup"><span data-stu-id="94fe2-137">When you use the **InputObject** parameter with `Tee-Object`, instead of piping command results to `Tee-Object`, the **InputObject** value is treated as a single object even if the value is a collection.</span></span>

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

### <span data-ttu-id="94fe2-138">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="94fe2-138">-LiteralPath</span></span>

<span data-ttu-id="94fe2-139">指定此 Cmdlet 將物件儲存到其中的檔案。</span><span class="sxs-lookup"><span data-stu-id="94fe2-139">Specifies a file that this cmdlet saves the object to.</span></span> <span data-ttu-id="94fe2-140">**LiteralPath** 參數值與 **FilePath** 不同，會完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="94fe2-140">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="94fe2-141">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="94fe2-141">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="94fe2-142">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="94fe2-142">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="94fe2-143">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="94fe2-143">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94fe2-144">-Variable</span><span class="sxs-lookup"><span data-stu-id="94fe2-144">-Variable</span></span>

<span data-ttu-id="94fe2-145">指定 Cmdlet 用來儲存物件的變數。</span><span class="sxs-lookup"><span data-stu-id="94fe2-145">Specifies a variable that the cmdlet saves the object to.</span></span> <span data-ttu-id="94fe2-146">輸入不含上述貨幣正負號 () 的變數名稱 `$` 。</span><span class="sxs-lookup"><span data-stu-id="94fe2-146">Enter a variable name without the preceding dollar sign (`$`).</span></span>

```yaml
Type: System.String
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="94fe2-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="94fe2-147">CommonParameters</span></span>

<span data-ttu-id="94fe2-148">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="94fe2-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="94fe2-149">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="94fe2-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="94fe2-150">輸入</span><span class="sxs-lookup"><span data-stu-id="94fe2-150">INPUTS</span></span>

### <span data-ttu-id="94fe2-151">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="94fe2-151">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="94fe2-152">您可以透過管線將物件傳送至 `Tee-Object` 。</span><span class="sxs-lookup"><span data-stu-id="94fe2-152">You can pipe objects to `Tee-Object`.</span></span>

## <span data-ttu-id="94fe2-153">輸出</span><span class="sxs-lookup"><span data-stu-id="94fe2-153">OUTPUTS</span></span>

### <span data-ttu-id="94fe2-154">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="94fe2-154">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="94fe2-155">`Tee-Object` 傳回它重新導向的物件。</span><span class="sxs-lookup"><span data-stu-id="94fe2-155">`Tee-Object` returns the object that it redirects.</span></span>

## <span data-ttu-id="94fe2-156">注意</span><span class="sxs-lookup"><span data-stu-id="94fe2-156">NOTES</span></span>

<span data-ttu-id="94fe2-157">您也可以使用 `Out-File` Cmdlet 或重新導向運算子，這兩個都會將輸出儲存在檔案中，但不會將輸出傳送至管線。</span><span class="sxs-lookup"><span data-stu-id="94fe2-157">You can also use the `Out-File` cmdlet or the redirection operator, both of which save the output in a file but do not send it down the pipeline.</span></span>

<span data-ttu-id="94fe2-158">從 PowerShell 6 開始，在 `Tee-Object` 寫入檔案時，會使用不使用 BOM 的 utf-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="94fe2-158">Beginning in PowerShell 6, `Tee-Object` uses BOM-less UTF-8 encoding when it writes to files.</span></span> <span data-ttu-id="94fe2-159">如果您需要不同的編碼方式，請使用 `Out-File` Cmdlet 搭配 **編碼** 參數。</span><span class="sxs-lookup"><span data-stu-id="94fe2-159">If you need a different encoding, use the `Out-File` cmdlet with the **Encoding** parameter.</span></span>

## <span data-ttu-id="94fe2-160">相關連結</span><span class="sxs-lookup"><span data-stu-id="94fe2-160">RELATED LINKS</span></span>

[<span data-ttu-id="94fe2-161">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="94fe2-161">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="94fe2-162">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="94fe2-162">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="94fe2-163">Group-Object</span><span class="sxs-lookup"><span data-stu-id="94fe2-163">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="94fe2-164">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="94fe2-164">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="94fe2-165">New-Object</span><span class="sxs-lookup"><span data-stu-id="94fe2-165">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="94fe2-166">Select-Object</span><span class="sxs-lookup"><span data-stu-id="94fe2-166">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="94fe2-167">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="94fe2-167">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="94fe2-168">Where-Object</span><span class="sxs-lookup"><span data-stu-id="94fe2-168">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="94fe2-169">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="94fe2-169">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

