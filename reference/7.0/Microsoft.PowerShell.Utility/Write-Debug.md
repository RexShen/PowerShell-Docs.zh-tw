---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: 3217a3c67c262f8061963fd1302c6782620e270d
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208504"
---
# <span data-ttu-id="88724-103">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="88724-103">Write-Debug</span></span>

## <span data-ttu-id="88724-104">概要</span><span class="sxs-lookup"><span data-stu-id="88724-104">SYNOPSIS</span></span>
<span data-ttu-id="88724-105">將偵錯訊息寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="88724-105">Writes a debug message to the console.</span></span>

## <span data-ttu-id="88724-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="88724-106">SYNTAX</span></span>

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="88724-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="88724-107">DESCRIPTION</span></span>

<span data-ttu-id="88724-108">`Write-Debug`Cmdlet 會從腳本或命令將 debug 訊息寫入至主機。</span><span class="sxs-lookup"><span data-stu-id="88724-108">The `Write-Debug` cmdlet writes debug messages to the host from a script or command.</span></span>

<span data-ttu-id="88724-109">根據預設，偵錯工具訊息不會顯示在主控台中，但是您可以使用 **debug** 參數或變數來顯示它們 `$DebugPreference` 。</span><span class="sxs-lookup"><span data-stu-id="88724-109">By default, debug messages are not displayed in the console, but you can display them by using the **Debug** parameter or the `$DebugPreference` variable.</span></span>

## <span data-ttu-id="88724-110">範例</span><span class="sxs-lookup"><span data-stu-id="88724-110">EXAMPLES</span></span>

### <span data-ttu-id="88724-111">範例1：瞭解 $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="88724-111">Example 1: Understand $DebugPreference</span></span>

<span data-ttu-id="88724-112">此範例會寫入 debug 訊息。</span><span class="sxs-lookup"><span data-stu-id="88724-112">This example writes a debug message.</span></span>

```powershell
Write-Debug "Cannot open file."
```

<span data-ttu-id="88724-113">的預設值 `$DebugPreference` 為 **SilentlyContinue** 。</span><span class="sxs-lookup"><span data-stu-id="88724-113">The default value of `$DebugPreference` is **SilentlyContinue** .</span></span> <span data-ttu-id="88724-114">因此，此訊息不會顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="88724-114">Therefore, the message is not displayed in the console.</span></span>

### <span data-ttu-id="88724-115">範例2：變更 $DebugPreference 的值</span><span class="sxs-lookup"><span data-stu-id="88724-115">Example 2: Change the value of $DebugPreference</span></span>

<span data-ttu-id="88724-116">此範例顯示變更變數值的效果 `$DebugPreference` 。</span><span class="sxs-lookup"><span data-stu-id="88724-116">This example shows the effect of changing the value of the `$DebugPreference` variable.</span></span> <span data-ttu-id="88724-117">首先，我們會顯示的目前值 `$DebugPreference` ，並嘗試寫入偵錯工具訊息。</span><span class="sxs-lookup"><span data-stu-id="88724-117">First, we display the current value of `$DebugPreference` and attempt to write a debug message.</span></span> <span data-ttu-id="88724-118">接著，我們會將的值變更 `$DebugPreference` 為 **Continue** ，讓您能夠顯示 debug 訊息。</span><span class="sxs-lookup"><span data-stu-id="88724-118">Then we change the value of `$DebugPreference` to **Continue** , which allows debug messages to be displayed.</span></span>

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

<span data-ttu-id="88724-119">如需的詳細資訊 `$DebugPreference` ，請參閱 [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables)。</span><span class="sxs-lookup"><span data-stu-id="88724-119">For more information about `$DebugPreference`, see [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).</span></span>

### <span data-ttu-id="88724-120">範例3：使用 Debug 參數覆寫 $DebugPreference</span><span class="sxs-lookup"><span data-stu-id="88724-120">Example 3: Use the Debug parameter to override $DebugPreference</span></span>

<span data-ttu-id="88724-121">函式會將 `Test-Debug` 變數的值寫入 `$DebugPreference` 至 PowerShell 主機和偵錯工具資料流程。</span><span class="sxs-lookup"><span data-stu-id="88724-121">The `Test-Debug` function writes the value of the `$DebugPreference` variable to the PowerShell host and to the Debug stream.</span></span> <span data-ttu-id="88724-122">在此範例中，我們使用 **Debug** 參數來覆寫此 `$DebugPreference` 值。</span><span class="sxs-lookup"><span data-stu-id="88724-122">In this example, we use the **Debug** parameter to override the `$DebugPreference` value.</span></span>

```powershell
function Test-Debug {
    [CmdletBinding()]
    param()
    Write-Debug ('$DebugPreference is ' + $DebugPreference)
    Write-Host ('$DebugPreference is ' + $DebugPreference)
}
```

```
PS> Test-Debug
$DebugPreference is SilentlyContinue

PS> Test-Debug -Debug
DEBUG: $DebugPreference is Continue
$DebugPreference is Continue
PS> $DebugPreference
SilentlyContinue
```

<span data-ttu-id="88724-123">請注意， `$DebugPreference` 當您使用 **Debug** 參數時，會變更的值。</span><span class="sxs-lookup"><span data-stu-id="88724-123">Notice that the value of `$DebugPreference` changes when you use the **Debug** parameter.</span></span> <span data-ttu-id="88724-124">這項變更只會影響函數的範圍。</span><span class="sxs-lookup"><span data-stu-id="88724-124">This change only affects the scope of the function.</span></span> <span data-ttu-id="88724-125">此值不會在函式之外受到影響。</span><span class="sxs-lookup"><span data-stu-id="88724-125">The value is not affected outside the function.</span></span>

<span data-ttu-id="88724-126">如需有關 **Debug** 一般參數的詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="88724-126">For more information about the **Debug** common parameter, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="88724-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="88724-127">PARAMETERS</span></span>

### <span data-ttu-id="88724-128">-Message</span><span class="sxs-lookup"><span data-stu-id="88724-128">-Message</span></span>

<span data-ttu-id="88724-129">指定要傳送至主控台的偵錯訊息。</span><span class="sxs-lookup"><span data-stu-id="88724-129">Specifies the debug message to send to the console.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="88724-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="88724-130">CommonParameters</span></span>

<span data-ttu-id="88724-131">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="88724-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="88724-132">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="88724-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="88724-133">輸入</span><span class="sxs-lookup"><span data-stu-id="88724-133">INPUTS</span></span>

### <span data-ttu-id="88724-134">System.String</span><span class="sxs-lookup"><span data-stu-id="88724-134">System.String</span></span>

<span data-ttu-id="88724-135">您可以使用管線將包含 debug 訊息的字串傳送至 `Write-Debug` 。</span><span class="sxs-lookup"><span data-stu-id="88724-135">You can pipe a string that contains a debug message to `Write-Debug`.</span></span>

## <span data-ttu-id="88724-136">輸出</span><span class="sxs-lookup"><span data-stu-id="88724-136">OUTPUTS</span></span>

### <span data-ttu-id="88724-137">無</span><span class="sxs-lookup"><span data-stu-id="88724-137">None</span></span>

<span data-ttu-id="88724-138">`Write-Debug` 只寫入至 debug 資料流程。</span><span class="sxs-lookup"><span data-stu-id="88724-138">`Write-Debug` only writes to the debug stream.</span></span> <span data-ttu-id="88724-139">它不會將任何物件寫入管線。</span><span class="sxs-lookup"><span data-stu-id="88724-139">It does not write any objects to the pipeline.</span></span>

## <span data-ttu-id="88724-140">注意</span><span class="sxs-lookup"><span data-stu-id="88724-140">NOTES</span></span>

## <span data-ttu-id="88724-141">相關連結</span><span class="sxs-lookup"><span data-stu-id="88724-141">RELATED LINKS</span></span>

[<span data-ttu-id="88724-142">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="88724-142">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="88724-143">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="88724-143">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="88724-144">Write-Error</span><span class="sxs-lookup"><span data-stu-id="88724-144">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="88724-145">Write-Host</span><span class="sxs-lookup"><span data-stu-id="88724-145">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="88724-146">Write-Output</span><span class="sxs-lookup"><span data-stu-id="88724-146">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="88724-147">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="88724-147">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="88724-148">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="88724-148">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="88724-149">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="88724-149">Write-Warning</span></span>](Write-Warning.md)
