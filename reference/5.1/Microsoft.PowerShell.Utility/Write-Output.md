---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: ccc72ac961adbcba542a7b8be55ad49df68a5ef6
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208435"
---
# <span data-ttu-id="8de68-103">Write-Output</span><span class="sxs-lookup"><span data-stu-id="8de68-103">Write-Output</span></span>

## <span data-ttu-id="8de68-104">概要</span><span class="sxs-lookup"><span data-stu-id="8de68-104">SYNOPSIS</span></span>
<span data-ttu-id="8de68-105">將指定的物件傳送給管線中的下一個命令。</span><span class="sxs-lookup"><span data-stu-id="8de68-105">Sends the specified objects to the next command in the pipeline.</span></span> <span data-ttu-id="8de68-106">如果命令是管線中的最後一個命令，物件就會顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="8de68-106">If the command is the last command in the pipeline, the objects are displayed in the console.</span></span>

## <span data-ttu-id="8de68-107">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8de68-107">SYNTAX</span></span>

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="8de68-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8de68-108">DESCRIPTION</span></span>

<span data-ttu-id="8de68-109">`Write-Output`Cmdlet 會將指定的物件沿著管線向下傳送至下一個命令。</span><span class="sxs-lookup"><span data-stu-id="8de68-109">The `Write-Output` cmdlet sends the specified object down the pipeline to the next command.</span></span>
<span data-ttu-id="8de68-110">如果命令是管線中的最後一個命令，物件就會顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="8de68-110">If the command is the last command in the pipeline, the object is displayed in the console.</span></span>

<span data-ttu-id="8de68-111">`Write-Output` 將物件沿著主要管線（也稱為「輸出資料流程」或「成功管線」）向下傳送。</span><span class="sxs-lookup"><span data-stu-id="8de68-111">`Write-Output` sends objects down the primary pipeline, also known as the "output stream" or the "success pipeline."</span></span> <span data-ttu-id="8de68-112">若要將錯誤物件沿著錯誤管線向下傳送，請使用 Write-Error。</span><span class="sxs-lookup"><span data-stu-id="8de68-112">To send error objects down the error pipeline, use Write-Error.</span></span>

<span data-ttu-id="8de68-113">這個 Cmdlet 通常是在指令碼中用來在主控台上顯示字串及其他物件。</span><span class="sxs-lookup"><span data-stu-id="8de68-113">This cmdlet is typically used in scripts to display strings and other objects on the console.</span></span> <span data-ttu-id="8de68-114">的其中一個內建別名， `Write-Output` 類似于 `echo` 使用的其他 shell `echo` ，預設行為是在管線結尾顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="8de68-114">One of the built-in aliases for `Write-Output` is `echo` and similar to other shells that use `echo`, the default behavior is to display the output at the end of a pipeline.</span></span> <span data-ttu-id="8de68-115">在 PowerShell 中，通常不需要在預設顯示輸出的實例中使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8de68-115">In PowerShell, it is generally not necessary to use the cmdlet in instances where the output is displayed by default.</span></span> <span data-ttu-id="8de68-116">例如，`Get-Process | Write-Output` 相當於 `Get-Process`。</span><span class="sxs-lookup"><span data-stu-id="8de68-116">For example, `Get-Process | Write-Output` is equivalent to `Get-Process`.</span></span> <span data-ttu-id="8de68-117">或者， `echo "Home directory: $HOME"` 可以撰寫， `"Home directory: $HOME"`</span><span class="sxs-lookup"><span data-stu-id="8de68-117">Or, `echo "Home directory: $HOME"` can be written, `"Home directory: $HOME"`.</span></span>

<span data-ttu-id="8de68-118">依預設，會 `Write-Output` 透過提供給 Cmdlet 的集合來列舉。</span><span class="sxs-lookup"><span data-stu-id="8de68-118">By default, `Write-Output` enumerates through collections provided to the cmdlet.</span></span> <span data-ttu-id="8de68-119">不過， `Write-Output` 也可以使用 **NoEnumerate** 參數，將集合以單一物件的形式傳遞至管線。</span><span class="sxs-lookup"><span data-stu-id="8de68-119">However, `Write-Output` can also be used to pass collections down the pipeline as a single object with the **NoEnumerate** parameter.</span></span>

## <span data-ttu-id="8de68-120">範例</span><span class="sxs-lookup"><span data-stu-id="8de68-120">EXAMPLES</span></span>

### <span data-ttu-id="8de68-121">範例1：取得物件並將它們寫入主控台</span><span class="sxs-lookup"><span data-stu-id="8de68-121">Example 1: Get objects and write them to the console</span></span>

```powershell
$P = Get-Process
Write-Output $P
```

<span data-ttu-id="8de68-122">第一個命令會取得在電腦上執行的處理常式，並將它們儲存在 `$P` 變數中。</span><span class="sxs-lookup"><span data-stu-id="8de68-122">The first command gets processes running on the computer and stores them in the `$P` variable.</span></span>

<span data-ttu-id="8de68-123">第二個和第三個命令會在主控台中顯示處理常式物件 `$P` 。</span><span class="sxs-lookup"><span data-stu-id="8de68-123">The second and third commands display the process objects in `$P` on the console.</span></span>

### <span data-ttu-id="8de68-124">範例2：將輸出傳遞至另一個 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8de68-124">Example 2: Pass output to another cmdlet</span></span>

```powershell
Write-Output "test output" | Get-Member
```

<span data-ttu-id="8de68-125">此命令會將 "test output" 字串傳送至 `Get-Member` Cmdlet，以顯示 system.string 類別的成員 **System.String** ，示範此字串是沿著管線傳遞。</span><span class="sxs-lookup"><span data-stu-id="8de68-125">This command pipes the "test output" string to the `Get-Member` cmdlet, which displays the members of the **System.String** class, demonstrating that the string was passed along the pipeline.</span></span>

### <span data-ttu-id="8de68-126">範例3：在輸出中隱藏列舉</span><span class="sxs-lookup"><span data-stu-id="8de68-126">Example 3: Suppress enumeration in output</span></span>

```powershell
Write-Output 1,2,3 | Measure-Object
```

```Output
Count    : 3
...
```

```powershell
Write-Output 1,2,3 -NoEnumerate | Measure-Object
```

```Output
Count    : 1
...
```

<span data-ttu-id="8de68-127">此命令會新增 **NoEnumerate** 參數，以透過管線將集合或陣列視為單一物件。</span><span class="sxs-lookup"><span data-stu-id="8de68-127">This command adds the **NoEnumerate** parameter to treat a collection or array as a single object through the pipeline.</span></span>

## <span data-ttu-id="8de68-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8de68-128">PARAMETERS</span></span>

### <span data-ttu-id="8de68-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="8de68-129">-InputObject</span></span>

<span data-ttu-id="8de68-130">指定要沿著管線向下傳送的物件。</span><span class="sxs-lookup"><span data-stu-id="8de68-130">Specifies the objects to send down the pipeline.</span></span> <span data-ttu-id="8de68-131">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="8de68-131">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8de68-132">-NoEnumerate</span><span class="sxs-lookup"><span data-stu-id="8de68-132">-NoEnumerate</span></span>

<span data-ttu-id="8de68-133">根據預設，此 `Write-Output` Cmdlet 一律會列舉其輸出。</span><span class="sxs-lookup"><span data-stu-id="8de68-133">By default, the `Write-Output` cmdlet always enumerates its output.</span></span> <span data-ttu-id="8de68-134">**NoEnumerate** 參數會隱藏預設行為，並防止 `Write-Output` 列舉輸出。</span><span class="sxs-lookup"><span data-stu-id="8de68-134">The **NoEnumerate** parameter suppresses the default behavior, and prevents `Write-Output` from enumerating output.</span></span> <span data-ttu-id="8de68-135">如果命令是以括弧括住， **NoEnumerate** 參數就沒有任何作用，因為括弧會強制列舉。</span><span class="sxs-lookup"><span data-stu-id="8de68-135">The **NoEnumerate** parameter has no effect if the command is wrapped in parentheses, because the parentheses force enumeration.</span></span> <span data-ttu-id="8de68-136">例如， `(Write-Output 1,2,3)` 仍會列舉陣列。</span><span class="sxs-lookup"><span data-stu-id="8de68-136">For example, `(Write-Output 1,2,3)` still enumerates the array.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8de68-137">此參數在 PowerShell 6.2 和更新版本中已修正的 Windows PowerShell 中有問題。</span><span class="sxs-lookup"><span data-stu-id="8de68-137">There is an issue with this switch in Windows PowerShell that is fixed in PowerShell 6.2 and above.</span></span> <span data-ttu-id="8de68-138">使用 **NoEnumerate** 並明確使用 **InputObject** 參數時，命令仍然會列舉。</span><span class="sxs-lookup"><span data-stu-id="8de68-138">When using **NoEnumerate** and explicitly using the **InputObject** parameter, the command still enumerates.</span></span> <span data-ttu-id="8de68-139">若要解決這個問題，請傳遞 **InputObject** 引數 (s) positionally。</span><span class="sxs-lookup"><span data-stu-id="8de68-139">To work around this, pass the **InputObject** argument(s) positionally.</span></span>

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

### <span data-ttu-id="8de68-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8de68-140">CommonParameters</span></span>

<span data-ttu-id="8de68-141">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8de68-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8de68-142">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8de68-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8de68-143">輸入</span><span class="sxs-lookup"><span data-stu-id="8de68-143">INPUTS</span></span>

### <span data-ttu-id="8de68-144">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="8de68-144">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8de68-145">您可以透過管線將物件傳送至 `Write-Output` 。</span><span class="sxs-lookup"><span data-stu-id="8de68-145">You can pipe objects to `Write-Output`.</span></span>

## <span data-ttu-id="8de68-146">輸出</span><span class="sxs-lookup"><span data-stu-id="8de68-146">OUTPUTS</span></span>

### <span data-ttu-id="8de68-147">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="8de68-147">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8de68-148">`Write-Output` 傳回提交為輸入的物件。</span><span class="sxs-lookup"><span data-stu-id="8de68-148">`Write-Output` returns the objects that are submitted as input.</span></span>

## <span data-ttu-id="8de68-149">注意</span><span class="sxs-lookup"><span data-stu-id="8de68-149">NOTES</span></span>

## <span data-ttu-id="8de68-150">相關連結</span><span class="sxs-lookup"><span data-stu-id="8de68-150">RELATED LINKS</span></span>

[<span data-ttu-id="8de68-151">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="8de68-151">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="8de68-152">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="8de68-152">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="8de68-153">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="8de68-153">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="8de68-154">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="8de68-154">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="8de68-155">Write-Error</span><span class="sxs-lookup"><span data-stu-id="8de68-155">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="8de68-156">Write-Host</span><span class="sxs-lookup"><span data-stu-id="8de68-156">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="8de68-157">Write-Information</span><span class="sxs-lookup"><span data-stu-id="8de68-157">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="8de68-158">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="8de68-158">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="8de68-159">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="8de68-159">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="8de68-160">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="8de68-160">Write-Warning</span></span>](Write-Warning.md)
