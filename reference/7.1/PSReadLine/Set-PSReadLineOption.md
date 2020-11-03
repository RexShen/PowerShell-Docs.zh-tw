---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: 4c1c6712966d78f9af4f0c1ff181bf1869c01eea
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208772"
---
# <span data-ttu-id="24324-103">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="24324-103">Set-PSReadLineOption</span></span>

## <span data-ttu-id="24324-104">概要</span><span class="sxs-lookup"><span data-stu-id="24324-104">Synopsis</span></span>
<span data-ttu-id="24324-105">自訂 **PSReadLine** 中的命令列編輯行為。</span><span class="sxs-lookup"><span data-stu-id="24324-105">Customizes the behavior of command line editing in **PSReadLine** .</span></span>

## <span data-ttu-id="24324-106">語法</span><span class="sxs-lookup"><span data-stu-id="24324-106">Syntax</span></span>

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-Colors <Hashtable>] [-PredictionSource <PredictionSource>]
 [<CommonParameters>]
```

## <span data-ttu-id="24324-107">描述</span><span class="sxs-lookup"><span data-stu-id="24324-107">Description</span></span>

<span data-ttu-id="24324-108">`Set-PSReadLineOption`當您編輯命令行時，此 Cmdlet 會自訂 **PSReadLine** 模組的行為。</span><span class="sxs-lookup"><span data-stu-id="24324-108">The `Set-PSReadLineOption` cmdlet customizes the behavior of the **PSReadLine** module when you're editing the command line.</span></span> <span data-ttu-id="24324-109">若要查看 **PSReadLine** 設定，請使用 `Get-PSReadLineOption` 。</span><span class="sxs-lookup"><span data-stu-id="24324-109">To view the **PSReadLine** settings, use `Get-PSReadLineOption`.</span></span>

## <span data-ttu-id="24324-110">範例</span><span class="sxs-lookup"><span data-stu-id="24324-110">Examples</span></span>

### <span data-ttu-id="24324-111">範例1：設定前景和背景色彩</span><span class="sxs-lookup"><span data-stu-id="24324-111">Example 1: Set foreground and background colors</span></span>

<span data-ttu-id="24324-112">此範例會將 **PSReadLine** 設定為以灰色背景顯示具有綠色前景文字的 **批註** 標記。</span><span class="sxs-lookup"><span data-stu-id="24324-112">This example sets **PSReadLine** to display the **Comment** token with green foreground text on a gray background.</span></span> <span data-ttu-id="24324-113">在範例中使用的 escape 序列中， **32** 代表前景色彩，而 **47** 代表背景色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-113">In the escape sequence used in the example, **32** represents the foreground color and **47** represents the background color.</span></span>

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

<span data-ttu-id="24324-114">您可以選擇只設定前景文字色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-114">You can choose to set only a foreground text color.</span></span> <span data-ttu-id="24324-115">例如， **批註** 標記的淺綠色前景文字色彩： ``"Comment"="`e[92m"`` 。</span><span class="sxs-lookup"><span data-stu-id="24324-115">For example, a bright green foreground text color for the **Comment** token: ``"Comment"="`e[92m"``.</span></span>

### <span data-ttu-id="24324-116">範例2：設定鐘樣式</span><span class="sxs-lookup"><span data-stu-id="24324-116">Example 2: Set bell style</span></span>

<span data-ttu-id="24324-117">在此範例中， **PSReadLine** 會回應需要使用者注意的錯誤或狀況。</span><span class="sxs-lookup"><span data-stu-id="24324-117">In this example, **PSReadLine** will respond to errors or conditions that require user attention.</span></span>
<span data-ttu-id="24324-118">**BellStyle** 會設定為在 1221 Hz 發出60毫秒的嗶聲。</span><span class="sxs-lookup"><span data-stu-id="24324-118">The **BellStyle** is set to emit an audible beep at 1221 Hz for 60 ms.</span></span>

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> <span data-ttu-id="24324-119">這項功能可能不適用於平臺上的所有主機。</span><span class="sxs-lookup"><span data-stu-id="24324-119">This feature may not work in all hosts on platforms.</span></span>

### <span data-ttu-id="24324-120">範例3：設定多個選項</span><span class="sxs-lookup"><span data-stu-id="24324-120">Example 3: Set multiple options</span></span>

<span data-ttu-id="24324-121">`Set-PSReadLineOption` 可以使用雜湊表來設定多個選項。</span><span class="sxs-lookup"><span data-stu-id="24324-121">`Set-PSReadLineOption` can set multiple options with a hash table.</span></span>

```powershell
$PSReadLineOptions = @{
    EditMode = "Emacs"
    HistoryNoDuplicates = $true
    HistorySearchCursorMovesToEnd = $true
    Colors = @{
        "Command" = "#8181f7"
    }
}
Set-PSReadLineOption @PSReadLineOptions
```

<span data-ttu-id="24324-122">`$PSReadLineOptions`雜湊表會設定索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="24324-122">The `$PSReadLineOptions` hash table sets the keys and values.</span></span> <span data-ttu-id="24324-123">`Set-PSReadLineOption` 使用的索引鍵和值 `@PSReadLineOptions` 來更新 **PSReadLine** 選項。</span><span class="sxs-lookup"><span data-stu-id="24324-123">`Set-PSReadLineOption` uses the keys and values with `@PSReadLineOptions` to update the **PSReadLine** options.</span></span>

<span data-ttu-id="24324-124">您可以 `$PSReadLineOptions` 在 PowerShell 命令列上，看到輸入雜湊表名稱的索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="24324-124">You can view the keys and values entering the hash table name, `$PSReadLineOptions` on the PowerShell command line.</span></span>

### <span data-ttu-id="24324-125">範例4：設定多個色彩選項</span><span class="sxs-lookup"><span data-stu-id="24324-125">Example 4: Set multiple color options</span></span>

<span data-ttu-id="24324-126">此範例示範如何在單一命令中設定一個以上的色彩值。</span><span class="sxs-lookup"><span data-stu-id="24324-126">This example shows how to set more than one color value in a single command.</span></span>

```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}
```

### <span data-ttu-id="24324-127">範例5：設定多個類型的色彩值</span><span class="sxs-lookup"><span data-stu-id="24324-127">Example 5: Set color values for multiple types</span></span>

<span data-ttu-id="24324-128">此範例顯示三種不同的方法，說明如何設定 **PSReadLine** 中顯示的權杖色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-128">This example shows three different methods for how to set the color of tokens displayed in **PSReadLine** .</span></span>

```powershell
Set-PSReadLineOption -Colors @{
 # Use a ConsoleColor enum
 "Error" = [ConsoleColor]::DarkRed

 # 24 bit color escape sequence
 "String" = "$([char]0x1b)[38;5;100m"

 # RGB value
 "Command" = "#8181f7"
}
```

### <span data-ttu-id="24324-129">範例6：使用 ViModeChangeHandler 來顯示 Vi 模式變更</span><span class="sxs-lookup"><span data-stu-id="24324-129">Example 6: Use ViModeChangeHandler to display Vi mode changes</span></span>

<span data-ttu-id="24324-130">此範例會發出資料指標變更 VT escape，以回應 **Vi** 模式變更。</span><span class="sxs-lookup"><span data-stu-id="24324-130">This example emits a cursor change VT escape in response to a **Vi** mode change.</span></span>

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "`e[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "`e[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

<span data-ttu-id="24324-131">**OnViModeChange** 函數會設定 **Vi** 模式的資料指標選項： insert 和 command。</span><span class="sxs-lookup"><span data-stu-id="24324-131">The **OnViModeChange** function sets the cursor options for the **Vi** modes: insert and command.</span></span>
<span data-ttu-id="24324-132">**ViModeChangeHandler** 會使用 `Function:` 提供者將 **OnViModeChange** 參考為腳本區塊物件。</span><span class="sxs-lookup"><span data-stu-id="24324-132">**ViModeChangeHandler** uses the `Function:` provider to reference **OnViModeChange** as a script block object.</span></span>

<span data-ttu-id="24324-133">如需詳細資訊，請參閱 [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)。</span><span class="sxs-lookup"><span data-stu-id="24324-133">For more information, see [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span></span>

## <span data-ttu-id="24324-134">參數</span><span class="sxs-lookup"><span data-stu-id="24324-134">Parameters</span></span>

### <span data-ttu-id="24324-135">-AddToHistoryHandler</span><span class="sxs-lookup"><span data-stu-id="24324-135">-AddToHistoryHandler</span></span>

<span data-ttu-id="24324-136">指定 **ScriptBlock** ，以控制要將哪些命令新增至 **PSReadLine** 歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="24324-136">Specifies a **ScriptBlock** that controls which commands get added to **PSReadLine** history.</span></span>

<span data-ttu-id="24324-137">**ScriptBlock** 會接收命令列做為輸入。</span><span class="sxs-lookup"><span data-stu-id="24324-137">The **ScriptBlock** receives the command line as input.</span></span> <span data-ttu-id="24324-138">如果 **ScriptBlock** 傳回 `$True` ，則會將命令列新增至歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="24324-138">If the **ScriptBlock** returns `$True`, the command line is added to the history.</span></span>

```yaml
Type: System.Func`2[System.String,System.Object]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-139">-AnsiEscapeTimeout</span><span class="sxs-lookup"><span data-stu-id="24324-139">-AnsiEscapeTimeout</span></span>

<span data-ttu-id="24324-140">當重新導向輸入時（例如，在或下執行時），這個選項是 Windows 專用的 `tmux` `screen` 。</span><span class="sxs-lookup"><span data-stu-id="24324-140">This option is specific to Windows when input is redirected, for example, when running under `tmux` or `screen`.</span></span>

<span data-ttu-id="24324-141">在 Windows 上重新導向的輸入，會以字元序列（開頭為 escape 字元）來傳送許多金鑰。</span><span class="sxs-lookup"><span data-stu-id="24324-141">With redirected input on Windows, many keys are sent as a sequence of characters starting with the escape character.</span></span> <span data-ttu-id="24324-142">您無法區分後面接著更多字元和有效 escape 序列的單一 escape 字元。</span><span class="sxs-lookup"><span data-stu-id="24324-142">It's impossible to distinguish between a single escape character followed by more characters and a valid escape sequence.</span></span>

<span data-ttu-id="24324-143">假設終端機可以比使用者類型更快傳送字元。</span><span class="sxs-lookup"><span data-stu-id="24324-143">The assumption is that the terminal can send the characters faster than a user types.</span></span> <span data-ttu-id="24324-144">**PSReadLine** 會在結束之前等候這個超時，直到它收到完整的 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="24324-144">**PSReadLine** waits for this timeout before concluding that it has received a complete escape sequence.</span></span>

<span data-ttu-id="24324-145">如果您在輸入時看到隨機或非預期的字元，您可以調整此超時時間。</span><span class="sxs-lookup"><span data-stu-id="24324-145">If you see random or unexpected characters when you type, you can adjust this timeout.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-146">-BellStyle</span><span class="sxs-lookup"><span data-stu-id="24324-146">-BellStyle</span></span>

<span data-ttu-id="24324-147">指定 **PSReadLine** 如何回應各種錯誤和不明確的狀況。</span><span class="sxs-lookup"><span data-stu-id="24324-147">Specifies how **PSReadLine** responds to various error and ambiguous conditions.</span></span>

<span data-ttu-id="24324-148">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="24324-148">The valid values are as follows:</span></span>

- <span data-ttu-id="24324-149">**聲音** ：短暫的嗶聲。</span><span class="sxs-lookup"><span data-stu-id="24324-149">**Audible** : A short beep.</span></span>
- <span data-ttu-id="24324-150">**視覺效果** ：文字短暫閃爍。</span><span class="sxs-lookup"><span data-stu-id="24324-150">**Visual** : Text flashes briefly.</span></span>
- <span data-ttu-id="24324-151">**無** ：無意見反應。</span><span class="sxs-lookup"><span data-stu-id="24324-151">**None** : No feedback.</span></span>

```yaml
Type: Microsoft.PowerShell.BellStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Audible
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-152">-色彩</span><span class="sxs-lookup"><span data-stu-id="24324-152">-Colors</span></span>

<span data-ttu-id="24324-153">**Colors** 參數會指定 **PSReadLine** 所使用的各種色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-153">The **Colors** parameter specifies various colors used by **PSReadLine** .</span></span>

<span data-ttu-id="24324-154">引數是一個雜湊表，其中的索引鍵會指定哪個元素和值來指定色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-154">The argument is a hash table where the keys specify which element and the values specify the color.</span></span>
<span data-ttu-id="24324-155">如需詳細資訊，請參閱 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)。</span><span class="sxs-lookup"><span data-stu-id="24324-155">For more information, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="24324-156">例如，色彩可以是來自 **ConsoleColor** 的值， `[ConsoleColor]::Red` 或有效的 ANSI escape 序列。</span><span class="sxs-lookup"><span data-stu-id="24324-156">Colors can be either a value from **ConsoleColor** , for example `[ConsoleColor]::Red`, or a valid ANSI escape sequence.</span></span> <span data-ttu-id="24324-157">有效的 escape 序列取決於您的終端機。</span><span class="sxs-lookup"><span data-stu-id="24324-157">Valid escape sequences depend on your terminal.</span></span> <span data-ttu-id="24324-158">在 PowerShell 5.0 中，紅色文字的範例 escape 序列是 `$([char]0x1b)[91m` 。</span><span class="sxs-lookup"><span data-stu-id="24324-158">In PowerShell 5.0, an example escape sequence for red text is `$([char]0x1b)[91m`.</span></span> <span data-ttu-id="24324-159">在 PowerShell 6 和更新版本中，相同的 escape 序列是 `` `e[91m`` 。</span><span class="sxs-lookup"><span data-stu-id="24324-159">In PowerShell 6 and above, the same escape sequence is `` `e[91m``.</span></span> <span data-ttu-id="24324-160">您可以指定其他的 escape 序列，包括下列類型：</span><span class="sxs-lookup"><span data-stu-id="24324-160">You can specify other escape sequences including the following types:</span></span>

- <span data-ttu-id="24324-161">256色彩</span><span class="sxs-lookup"><span data-stu-id="24324-161">256 color</span></span>
- <span data-ttu-id="24324-162">24位色彩</span><span class="sxs-lookup"><span data-stu-id="24324-162">24-bit color</span></span>
- <span data-ttu-id="24324-163">前景、背景或兩者</span><span class="sxs-lookup"><span data-stu-id="24324-163">Foreground, background, or both</span></span>
- <span data-ttu-id="24324-164">反向、粗體</span><span class="sxs-lookup"><span data-stu-id="24324-164">Inverse, bold</span></span>

<span data-ttu-id="24324-165">如需 ANSI 色彩代碼的詳細資訊，請參閱維琪百科的 [ansi escape 程式碼](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) 。</span><span class="sxs-lookup"><span data-stu-id="24324-165">For more information about ANSI color codes, see [ANSI escape code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia.</span></span>

<span data-ttu-id="24324-166">有效的索引鍵包括：</span><span class="sxs-lookup"><span data-stu-id="24324-166">The valid keys include:</span></span>

- <span data-ttu-id="24324-167">**ContinuationPrompt** ：接續提示的色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-167">**ContinuationPrompt** : The color of the continuation prompt.</span></span>
- <span data-ttu-id="24324-168">**強調** ：強調色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-168">**Emphasis** : The emphasis color.</span></span> <span data-ttu-id="24324-169">例如，搜尋歷程記錄時的相符文字。</span><span class="sxs-lookup"><span data-stu-id="24324-169">For example, the matching text when searching history.</span></span>
- <span data-ttu-id="24324-170">**錯誤** ：錯誤色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-170">**Error** : The error color.</span></span> <span data-ttu-id="24324-171">例如，在提示字元中。</span><span class="sxs-lookup"><span data-stu-id="24324-171">For example, in the prompt.</span></span>
- <span data-ttu-id="24324-172">**選取範圍** ：反白顯示功能表選取專案或選取文字的色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-172">**Selection** : The color to highlight the menu selection or selected text.</span></span>
- <span data-ttu-id="24324-173">**預設** 值：預設標記色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-173">**Default** : The default token color.</span></span>
- <span data-ttu-id="24324-174">**批註** ：註解標記色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-174">**Comment** : The comment token color.</span></span>
- <span data-ttu-id="24324-175">**關鍵字** ：關鍵字標記色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-175">**Keyword** : The keyword token color.</span></span>
- <span data-ttu-id="24324-176">**字串** ：字串標記色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-176">**String** : The string token color.</span></span>
- <span data-ttu-id="24324-177">**運算子** ：運算子標記色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-177">**Operator** : The operator token color.</span></span>
- <span data-ttu-id="24324-178">**變數** ：變數標記色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-178">**Variable** : The variable token color.</span></span>
- <span data-ttu-id="24324-179">**命令** ：命令標記色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-179">**Command** : The command token color.</span></span>
- <span data-ttu-id="24324-180">**參數** ：參數標記色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-180">**Parameter** : The parameter token color.</span></span>
- <span data-ttu-id="24324-181">**類型** ：類型標記色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-181">**Type** : The type token color.</span></span>
- <span data-ttu-id="24324-182">**數位** ：數位標記色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-182">**Number** : The number token color.</span></span>
- <span data-ttu-id="24324-183">**成員** ：成員名稱標記色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-183">**Member** : The member name token color.</span></span>
- <span data-ttu-id="24324-184">**InlinePrediction** ：預測性建議內嵌視圖的色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-184">**InlinePrediction** : The color for the inline view of the predictive suggestion.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-185">-CommandValidationHandler</span><span class="sxs-lookup"><span data-stu-id="24324-185">-CommandValidationHandler</span></span>

<span data-ttu-id="24324-186">指定從 **ValidateAndAcceptLine** 呼叫的 **ScriptBlock** 。</span><span class="sxs-lookup"><span data-stu-id="24324-186">Specifies a **ScriptBlock** that is called from **ValidateAndAcceptLine** .</span></span> <span data-ttu-id="24324-187">如果擲回例外狀況，驗證就會失敗，並回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="24324-187">If an exception is thrown, validation fails and the error is reported.</span></span>

<span data-ttu-id="24324-188">在擲回例外狀況之前，驗證處理常式可以將游標放在錯誤的位置，以便更輕鬆地進行修正。</span><span class="sxs-lookup"><span data-stu-id="24324-188">Before throwing an exception, the validation handler can place the cursor at the point of the error to make it easier to fix.</span></span> <span data-ttu-id="24324-189">驗證處理常式也可以變更命令列，例如修正常見的打字錯誤。</span><span class="sxs-lookup"><span data-stu-id="24324-189">A validation handler can also change the command line, such as to correct common typographical errors.</span></span>

<span data-ttu-id="24324-190">**ValidateAndAcceptLine** 是用來避免您的歷程記錄無法運作的命令。</span><span class="sxs-lookup"><span data-stu-id="24324-190">**ValidateAndAcceptLine** is used to avoid cluttering your history with commands that can't work.</span></span>

```yaml
Type: System.Action`1[System.Management.Automation.Language.CommandAst]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-191">-CompletionQueryItems</span><span class="sxs-lookup"><span data-stu-id="24324-191">-CompletionQueryItems</span></span>

<span data-ttu-id="24324-192">指定在不提示的情況下顯示的完成專案數目上限。</span><span class="sxs-lookup"><span data-stu-id="24324-192">Specifies the maximum number of completion items that are shown without prompting.</span></span>

<span data-ttu-id="24324-193">如果要顯示的專案數大於此值， **PSReadLine** 會在顯示完成專案之前提示 **[是]/[否]** 。</span><span class="sxs-lookup"><span data-stu-id="24324-193">If the number of items to show is greater than this value, **PSReadLine** prompts **yes/no** before displaying the completion items.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-194">-ContinuationPrompt</span><span class="sxs-lookup"><span data-stu-id="24324-194">-ContinuationPrompt</span></span>

<span data-ttu-id="24324-195">指定輸入多行輸入時，在後續行開頭顯示的字串。</span><span class="sxs-lookup"><span data-stu-id="24324-195">Specifies the string displayed at the beginning of the subsequent lines when multi-line input is entered.</span></span> <span data-ttu-id="24324-196">預設值為 () 的雙重大於正負號 `>>` 。</span><span class="sxs-lookup"><span data-stu-id="24324-196">The default is double greater-than signs (`>>`).</span></span> <span data-ttu-id="24324-197">空字串是有效的。</span><span class="sxs-lookup"><span data-stu-id="24324-197">An empty string is valid.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-198">-DingDuration</span><span class="sxs-lookup"><span data-stu-id="24324-198">-DingDuration</span></span>

<span data-ttu-id="24324-199">指定當 **BellStyle** 設定為可 **聽見** 時，嗶聲的持續時間。</span><span class="sxs-lookup"><span data-stu-id="24324-199">Specifies the duration of the beep when **BellStyle** is set to **Audible** .</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50ms
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-200">-DingTone</span><span class="sxs-lookup"><span data-stu-id="24324-200">-DingTone</span></span>

<span data-ttu-id="24324-201">指定當 **BellStyle** 設定為可 **聽見** 時，嗶聲的音調（以赫茲為單位） (Hz) 。</span><span class="sxs-lookup"><span data-stu-id="24324-201">Specifies the tone in Hertz (Hz) of the beep when **BellStyle** is set to **Audible** .</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1221
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-202">-EditMode</span><span class="sxs-lookup"><span data-stu-id="24324-202">-EditMode</span></span>

<span data-ttu-id="24324-203">指定命令列編輯模式。</span><span class="sxs-lookup"><span data-stu-id="24324-203">Specifies the command line editing mode.</span></span> <span data-ttu-id="24324-204">使用這個參數會重設任何由設定的按鍵系結 `Set-PSReadLineKeyHandler` 。</span><span class="sxs-lookup"><span data-stu-id="24324-204">Using this parameter resets any key bindings set by `Set-PSReadLineKeyHandler`.</span></span>

<span data-ttu-id="24324-205">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="24324-205">The valid values are as follows:</span></span>

- <span data-ttu-id="24324-206">**Windows** ：金鑰系結會模擬 PowerShell、cmd 及 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="24324-206">**Windows** : Key bindings emulate PowerShell, cmd, and Visual Studio.</span></span>
- <span data-ttu-id="24324-207">**Emacs** ： Key bindings 會模擬 Bash 或 Emacs。</span><span class="sxs-lookup"><span data-stu-id="24324-207">**Emacs** : Key bindings emulate Bash or Emacs.</span></span>
- <span data-ttu-id="24324-208">**Vi** ：金鑰系結會模擬 Vi。</span><span class="sxs-lookup"><span data-stu-id="24324-208">**Vi** : Key bindings emulate Vi.</span></span>

<span data-ttu-id="24324-209">使用 `Get-PSReadLineKeyHandler` 以查看目前設定之 **EditMode** 的索引鍵系結。</span><span class="sxs-lookup"><span data-stu-id="24324-209">Use `Get-PSReadLineKeyHandler` to see the key bindings for the currently configured **EditMode** .</span></span>

```yaml
Type: Microsoft.PowerShell.EditMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-210">-ExtraPromptLineCount</span><span class="sxs-lookup"><span data-stu-id="24324-210">-ExtraPromptLineCount</span></span>

<span data-ttu-id="24324-211">指定額外的行數。</span><span class="sxs-lookup"><span data-stu-id="24324-211">Specifies the number of extra lines.</span></span>

<span data-ttu-id="24324-212">如果您的提示橫跨一行以上，請指定此參數的值。</span><span class="sxs-lookup"><span data-stu-id="24324-212">If your prompt spans more than one line, specify a value for this parameter.</span></span> <span data-ttu-id="24324-213">當您想要在顯示某些輸出之後， **PSReadLine** 顯示提示時，可使用額外的行時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="24324-213">Use this option when you want extra lines to be available when **PSReadLine** displays the prompt after showing some output.</span></span> <span data-ttu-id="24324-214">例如， **PSReadLine** 會傳回完成的清單。</span><span class="sxs-lookup"><span data-stu-id="24324-214">For example, **PSReadLine** returns a list of completions.</span></span>

<span data-ttu-id="24324-215">在舊版 **PSReadLine** 中需要此選項，但在使用函式時很有用 `InvokePrompt` 。</span><span class="sxs-lookup"><span data-stu-id="24324-215">This option is needed less than in previous versions of **PSReadLine** , but is useful when the `InvokePrompt` function is used.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-216">-HistoryNoDuplicates</span><span class="sxs-lookup"><span data-stu-id="24324-216">-HistoryNoDuplicates</span></span>

<span data-ttu-id="24324-217">此選項會控制重新叫用行為。</span><span class="sxs-lookup"><span data-stu-id="24324-217">This option controls the recall behavior.</span></span> <span data-ttu-id="24324-218">重複的命令仍會新增至歷程記錄檔案。</span><span class="sxs-lookup"><span data-stu-id="24324-218">Duplicate commands are still added to the history file.</span></span>
<span data-ttu-id="24324-219">當設定此選項時，重新叫用命令時只會顯示最新的調用。</span><span class="sxs-lookup"><span data-stu-id="24324-219">When this option is set, only the most recent invocation appears when recalling commands.</span></span> <span data-ttu-id="24324-220">重複的命令會新增至歷程記錄，以便在召回期間保留順序。</span><span class="sxs-lookup"><span data-stu-id="24324-220">Repeated commands are added to history to preserve ordering during recall.</span></span> <span data-ttu-id="24324-221">不過，在重新叫用或搜尋歷程記錄時，您通常不會想要多次看到命令。</span><span class="sxs-lookup"><span data-stu-id="24324-221">However, you typically don't want to see the command multiple times when recalling or searching the history.</span></span>

<span data-ttu-id="24324-222">根據預設，global **PSConsoleReadLineOptions** 物件的 **HistoryNoDuplicates** 屬性會設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="24324-222">By default, the **HistoryNoDuplicates** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="24324-223">使用這個 **SwitchParameter** 會將屬性值設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="24324-223">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="24324-224">若要變更屬性值，您必須指定 **SwitchParameter** 的值，如下所示： `-HistoryNoDuplicates:$False` 。</span><span class="sxs-lookup"><span data-stu-id="24324-224">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-HistoryNoDuplicates:$False`.</span></span>

<span data-ttu-id="24324-225">您可以使用下列命令，直接設定屬性值：</span><span class="sxs-lookup"><span data-stu-id="24324-225">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistoryNoDuplicates = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-226">-HistorySavePath</span><span class="sxs-lookup"><span data-stu-id="24324-226">-HistorySavePath</span></span>

<span data-ttu-id="24324-227">指定儲存記錄之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="24324-227">Specifies the path to the file where history is saved.</span></span> <span data-ttu-id="24324-228">執行 Windows 或非 Windows 平臺的電腦會將檔案儲存在不同的位置。</span><span class="sxs-lookup"><span data-stu-id="24324-228">Computers running Windows or non-Windows platforms store the file in different locations.</span></span> <span data-ttu-id="24324-229">例如，檔案名會儲存在變數中 `$($host.Name)_history.txt` `ConsoleHost_history.txt` 。</span><span class="sxs-lookup"><span data-stu-id="24324-229">The filename is stored in a variable `$($host.Name)_history.txt`, for example `ConsoleHost_history.txt`.</span></span>

<span data-ttu-id="24324-230">如果您未使用此參數，預設路徑如下所示：</span><span class="sxs-lookup"><span data-stu-id="24324-230">If you don't use this parameter, the default path is as follows:</span></span>

<span data-ttu-id="24324-231">**Windows**</span><span class="sxs-lookup"><span data-stu-id="24324-231">**Windows**</span></span>

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

<span data-ttu-id="24324-232">**非 Windows**</span><span class="sxs-lookup"><span data-stu-id="24324-232">**non-Windows**</span></span>

`$env:XDG_DATA_HOME/powershell/PSReadLine\$($host.Name)_history.txt`

`$env:HOME/.local/share/powershell/PSReadLine\$($host.Name)_history.txt`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A file named $($host.Name)_history.txt in $env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine on Windows and $env:XDG_DATA_HOME/powershell/PSReadLine or $env:HOME/.local/share/powershell/PSReadLine on non-Windows platforms
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-233">-HistorySaveStyle</span><span class="sxs-lookup"><span data-stu-id="24324-233">-HistorySaveStyle</span></span>

<span data-ttu-id="24324-234">指定 **PSReadLine** 儲存歷程記錄的方式。</span><span class="sxs-lookup"><span data-stu-id="24324-234">Specifies how **PSReadLine** saves history.</span></span>

<span data-ttu-id="24324-235">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="24324-235">Valid values are as follows:</span></span>

- <span data-ttu-id="24324-236">**SaveIncrementally** ：在執行每個命令之後儲存歷程記錄，並在多個 PowerShell 實例之間共用。</span><span class="sxs-lookup"><span data-stu-id="24324-236">**SaveIncrementally** : Save history after each command is executed and share across multiple instances of PowerShell.</span></span>
- <span data-ttu-id="24324-237">**SaveAtExit** ： PowerShell 結束時附加記錄檔。</span><span class="sxs-lookup"><span data-stu-id="24324-237">**SaveAtExit** : Append history file when PowerShell exits.</span></span>
- <span data-ttu-id="24324-238">**SaveNothing** ：不使用歷程記錄檔。</span><span class="sxs-lookup"><span data-stu-id="24324-238">**SaveNothing** : Don't use a history file.</span></span>

```yaml
Type: Microsoft.PowerShell.HistorySaveStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SaveIncrementally
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-239">-HistorySearchCaseSensitive</span><span class="sxs-lookup"><span data-stu-id="24324-239">-HistorySearchCaseSensitive</span></span>

<span data-ttu-id="24324-240">指定在 **ReverseSearchHistory** 或 **HistorySearchBackward** 等函式中，記錄搜尋會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="24324-240">Specifies that history searching is case-sensitive in functions like **ReverseSearchHistory** or **HistorySearchBackward** .</span></span>

<span data-ttu-id="24324-241">根據預設，global **PSConsoleReadLineOptions** 物件的 **HistorySearchCaseSensitive** 屬性會設定為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="24324-241">By default, the **HistorySearchCaseSensitive** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="24324-242">使用這個 **SwitchParameter** 會將屬性值設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="24324-242">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="24324-243">若要將屬性值變更回，您必須指定 **SwitchParameter** 的值，如下所示： `-HistorySearchCaseSensitive:$False` 。</span><span class="sxs-lookup"><span data-stu-id="24324-243">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCaseSensitive:$False`.</span></span>

<span data-ttu-id="24324-244">您可以使用下列命令，直接設定屬性值：</span><span class="sxs-lookup"><span data-stu-id="24324-244">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistorySearchCaseSensitive = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-245">-HistorySearchCursorMovesToEnd</span><span class="sxs-lookup"><span data-stu-id="24324-245">-HistorySearchCursorMovesToEnd</span></span>

<span data-ttu-id="24324-246">指出游標移至您使用搜尋從歷程記錄載入的命令結尾。</span><span class="sxs-lookup"><span data-stu-id="24324-246">Indicates that the cursor moves to the end of commands that you load from history by using a search.</span></span>
<span data-ttu-id="24324-247">當這個參數設定為時 `$False` ，游標會維持在您按下向上鍵或向下箭號時的位置。</span><span class="sxs-lookup"><span data-stu-id="24324-247">When this parameter is set to `$False`, the cursor remains at the position it was when you pressed the up or down arrows.</span></span>

<span data-ttu-id="24324-248">根據預設，global **PSConsoleReadLineOptions** 物件的 **HistorySearchCursorMovesToEnd** 屬性會設定為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="24324-248">By default, the **HistorySearchCursorMovesToEnd** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="24324-249">使用這個 **SwitchParameter** 會將屬性值設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="24324-249">Using this **SwitchParameter** set the property value to `True`.</span></span> <span data-ttu-id="24324-250">若要將屬性值變更回，您必須指定 **SwitchParameter** 的值，如下所示： `-HistorySearchCursorMovesToEnd:$False` 。</span><span class="sxs-lookup"><span data-stu-id="24324-250">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCursorMovesToEnd:$False`.</span></span>

<span data-ttu-id="24324-251">您可以使用下列命令，直接設定屬性值：</span><span class="sxs-lookup"><span data-stu-id="24324-251">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistorySearchCursorMovesToEnd = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-252">-MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="24324-252">-MaximumHistoryCount</span></span>

<span data-ttu-id="24324-253">指定要在 **PSReadLine** 歷程記錄中儲存的命令數目上限。</span><span class="sxs-lookup"><span data-stu-id="24324-253">Specifies the maximum number of commands to save in **PSReadLine** history.</span></span>

<span data-ttu-id="24324-254">**PSReadLine** 記錄與 PowerShell 歷程記錄分開。</span><span class="sxs-lookup"><span data-stu-id="24324-254">**PSReadLine** history is separate from PowerShell history.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-255">-MaximumKillRingCount</span><span class="sxs-lookup"><span data-stu-id="24324-255">-MaximumKillRingCount</span></span>

<span data-ttu-id="24324-256">指定儲存在終止環形中的專案數目上限。</span><span class="sxs-lookup"><span data-stu-id="24324-256">Specifies the maximum number of items stored in the kill ring.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-257">-PredictionSource</span><span class="sxs-lookup"><span data-stu-id="24324-257">-PredictionSource</span></span>

<span data-ttu-id="24324-258">指定 PSReadLine 的來源，以取得預測性建議。</span><span class="sxs-lookup"><span data-stu-id="24324-258">Specifies the source for PSReadLine to get predictive suggestions.</span></span>

<span data-ttu-id="24324-259">有效值為：</span><span class="sxs-lookup"><span data-stu-id="24324-259">Valid values are:</span></span>

- <span data-ttu-id="24324-260">**無** ：停用預測性建議功能</span><span class="sxs-lookup"><span data-stu-id="24324-260">**None** : disable the predictive suggestion feature</span></span>
- <span data-ttu-id="24324-261">歷程 **記錄** ：僅從歷程記錄取得預測性建議</span><span class="sxs-lookup"><span data-stu-id="24324-261">**History** : get predictive suggestions from history only</span></span>

```yaml
Type: PredictionSource
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-262">-PromptText</span><span class="sxs-lookup"><span data-stu-id="24324-262">-PromptText</span></span>

<span data-ttu-id="24324-263">發生剖析錯誤時， **PSReadLine** 會將提示的一部分變更為紅色。</span><span class="sxs-lookup"><span data-stu-id="24324-263">When there's a parse error, **PSReadLine** changes a part of the prompt red.</span></span> <span data-ttu-id="24324-264">**PSReadLine** 會分析您的提示函式，以決定如何只變更部分提示的色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-264">**PSReadLine** analyzes your prompt function to determine how to change only the color of part of your prompt.</span></span> <span data-ttu-id="24324-265">這種分析並不是100% 可靠。</span><span class="sxs-lookup"><span data-stu-id="24324-265">This analysis isn't 100% reliable.</span></span>

<span data-ttu-id="24324-266">如果 **PSReadLine** 正在以非預期的方式變更您的提示，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="24324-266">Use this option if **PSReadLine** is changing your prompt in unexpected ways.</span></span> <span data-ttu-id="24324-267">包含任何尾端空白。</span><span class="sxs-lookup"><span data-stu-id="24324-267">Include any trailing whitespace.</span></span>

<span data-ttu-id="24324-268">例如，如果您的提示函式看起來如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="24324-268">For example, if your prompt function looked like the following example:</span></span>

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

<span data-ttu-id="24324-269">然後設定：</span><span class="sxs-lookup"><span data-stu-id="24324-269">Then set:</span></span>

`Set-PSReadLineOption -PromptText "# "`

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-270">-ShowToolTips</span><span class="sxs-lookup"><span data-stu-id="24324-270">-ShowToolTips</span></span>

<span data-ttu-id="24324-271">顯示可能的完成時，工具提示會顯示在完成清單中。</span><span class="sxs-lookup"><span data-stu-id="24324-271">When displaying possible completions, tooltips are shown in the list of completions.</span></span>

<span data-ttu-id="24324-272">這個選項預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="24324-272">This option is enabled by default.</span></span> <span data-ttu-id="24324-273">在舊版 **PSReadLine** 中，預設不會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="24324-273">This option wasn't enabled by default in prior versions of **PSReadLine** .</span></span> <span data-ttu-id="24324-274">若要停用，請將此選項設定為 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="24324-274">To disable, set this option to `$False`.</span></span>

<span data-ttu-id="24324-275">根據預設，global **PSConsoleReadLineOptions** 物件的 **ShowToolTips** 屬性會設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="24324-275">By default, the **ShowToolTips** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="24324-276">使用這個 **SwitchParameter** 會將屬性值設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="24324-276">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="24324-277">若要變更屬性值，您必須指定 **SwitchParameter** 的值，如下所示： `-ShowToolTips:$False` 。</span><span class="sxs-lookup"><span data-stu-id="24324-277">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-ShowToolTips:$False`.</span></span>

<span data-ttu-id="24324-278">您可以使用下列命令，直接設定屬性值：</span><span class="sxs-lookup"><span data-stu-id="24324-278">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).ShowToolTips = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-279">-ViModeChangeHandler</span><span class="sxs-lookup"><span data-stu-id="24324-279">-ViModeChangeHandler</span></span>

<span data-ttu-id="24324-280">當 **ViModeIndicator** 設定為時 `Script` ，每次模式變更時，就會叫用提供的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="24324-280">When the **ViModeIndicator** is set to `Script`, the script block provided will be invoked every time the mode changes.</span></span> <span data-ttu-id="24324-281">腳本區塊會提供一個類型的引數 `ViMode` 。</span><span class="sxs-lookup"><span data-stu-id="24324-281">The script block is provided one argument of type `ViMode`.</span></span>

<span data-ttu-id="24324-282">此參數是在 PowerShell 7 中引進。</span><span class="sxs-lookup"><span data-stu-id="24324-282">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-283">-ViModeIndicator</span><span class="sxs-lookup"><span data-stu-id="24324-283">-ViModeIndicator</span></span>

<span data-ttu-id="24324-284">這個選項會設定目前 **Vi** 模式的視覺指示。</span><span class="sxs-lookup"><span data-stu-id="24324-284">This option sets the visual indication for the current **Vi** mode.</span></span> <span data-ttu-id="24324-285">請插入模式或命令模式。</span><span class="sxs-lookup"><span data-stu-id="24324-285">Either insert mode or command mode.</span></span>

<span data-ttu-id="24324-286">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="24324-286">The valid values are as follows:</span></span>

- <span data-ttu-id="24324-287">**無** ：沒有指示。</span><span class="sxs-lookup"><span data-stu-id="24324-287">**None** : There's no indication.</span></span>
- <span data-ttu-id="24324-288">**提示** ：提示會變更色彩。</span><span class="sxs-lookup"><span data-stu-id="24324-288">**Prompt** : The prompt changes color.</span></span>
- <span data-ttu-id="24324-289">**Cursor** ：資料指標的大小變更。</span><span class="sxs-lookup"><span data-stu-id="24324-289">**Cursor** : The cursor changes size.</span></span>
- <span data-ttu-id="24324-290">**腳本** ：列印使用者指定的文字。</span><span class="sxs-lookup"><span data-stu-id="24324-290">**Script** : User-specified text is printed.</span></span>

```yaml
Type: Microsoft.PowerShell.ViModeStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-291">-WordDelimiters</span><span class="sxs-lookup"><span data-stu-id="24324-291">-WordDelimiters</span></span>

<span data-ttu-id="24324-292">指定分隔函式（例如 **ForwardWord** 或 **KillWord** ）之單字的字元。</span><span class="sxs-lookup"><span data-stu-id="24324-292">Specifies the characters that delimit words for functions like **ForwardWord** or **KillWord** .</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"–—―
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="24324-293">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="24324-293">CommonParameters</span></span>

<span data-ttu-id="24324-294">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="24324-294">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="24324-295">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="24324-295">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="24324-296">輸入</span><span class="sxs-lookup"><span data-stu-id="24324-296">Inputs</span></span>

### <span data-ttu-id="24324-297">None</span><span class="sxs-lookup"><span data-stu-id="24324-297">None</span></span>

<span data-ttu-id="24324-298">您無法透過管線將物件傳送至 `Set-PSReadLineOption.`</span><span class="sxs-lookup"><span data-stu-id="24324-298">You cannot pipe objects to `Set-PSReadLineOption.`</span></span>

## <span data-ttu-id="24324-299">輸出</span><span class="sxs-lookup"><span data-stu-id="24324-299">Outputs</span></span>

### <span data-ttu-id="24324-300">無</span><span class="sxs-lookup"><span data-stu-id="24324-300">None</span></span>

<span data-ttu-id="24324-301">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="24324-301">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="24324-302">備忘稿</span><span class="sxs-lookup"><span data-stu-id="24324-302">Notes</span></span>

## <span data-ttu-id="24324-303">相關連結</span><span class="sxs-lookup"><span data-stu-id="24324-303">Related links</span></span>

[<span data-ttu-id="24324-304">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="24324-304">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

[<span data-ttu-id="24324-305">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="24324-305">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="24324-306">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="24324-306">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="24324-307">移除-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="24324-307">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="24324-308">設定-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="24324-308">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
