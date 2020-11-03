---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-warning?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Warning
ms.openlocfilehash: 7e74e53bd056a452917d2f2380b817fc6925f0fe
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208467"
---
# <span data-ttu-id="4f11d-103">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="4f11d-103">Write-Warning</span></span>

## <span data-ttu-id="4f11d-104">概要</span><span class="sxs-lookup"><span data-stu-id="4f11d-104">SYNOPSIS</span></span>
<span data-ttu-id="4f11d-105">寫入警告訊息。</span><span class="sxs-lookup"><span data-stu-id="4f11d-105">Writes a warning message.</span></span>

## <span data-ttu-id="4f11d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4f11d-106">SYNTAX</span></span>

```
Write-Warning [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="4f11d-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4f11d-107">DESCRIPTION</span></span>

<span data-ttu-id="4f11d-108">Cmdlet 會將 `Write-Warning` 警告訊息寫入至 PowerShell 主機。</span><span class="sxs-lookup"><span data-stu-id="4f11d-108">The `Write-Warning` cmdlet writes a warning message to the PowerShell host.</span></span> <span data-ttu-id="4f11d-109">警告的回應取決於使用者的 `$WarningPreference` 變數值和 **WarningAction** 一般參數的使用方式。</span><span class="sxs-lookup"><span data-stu-id="4f11d-109">The response to the warning depends on the value of the user's `$WarningPreference` variable and the use of the **WarningAction** common parameter.</span></span>

## <span data-ttu-id="4f11d-110">範例</span><span class="sxs-lookup"><span data-stu-id="4f11d-110">EXAMPLES</span></span>

### <span data-ttu-id="4f11d-111">範例 1︰寫入警告訊息</span><span class="sxs-lookup"><span data-stu-id="4f11d-111">Example 1: Write a warning message</span></span>

<span data-ttu-id="4f11d-112">這個命令會顯示訊息 "WARNING: This is only a test warning."</span><span class="sxs-lookup"><span data-stu-id="4f11d-112">This command displays the message "WARNING: This is only a test warning."</span></span>

```powershell
Write-Warning "This is only a test warning."
```

### <span data-ttu-id="4f11d-113">範例 2︰將字串傳遞給 Write-Warning</span><span class="sxs-lookup"><span data-stu-id="4f11d-113">Example 2: Pass a string to Write-Warning</span></span>

<span data-ttu-id="4f11d-114">此命令顯示您可以使用管線運算子 () 將 `|` 字串傳送至 `Write-Warning` 。</span><span class="sxs-lookup"><span data-stu-id="4f11d-114">This command shows that you can use a pipeline operator (`|`) to send a string to `Write-Warning`.</span></span>
<span data-ttu-id="4f11d-115">您可以將字串儲存在變數中（如這個命令所示），或直接使用管線將字串傳送至 `Write-Warning` 。</span><span class="sxs-lookup"><span data-stu-id="4f11d-115">You can save the string in a variable, as shown in this command, or pipe the string directly to `Write-Warning`.</span></span>

```powershell
$w = "This is only a test warning."
$w | Write-Warning
```

### <span data-ttu-id="4f11d-116">範例 3︰設定 $WarningPreference 變數和寫入警告</span><span class="sxs-lookup"><span data-stu-id="4f11d-116">Example 3: Set the $WarningPreference variable and write a warning</span></span>

<span data-ttu-id="4f11d-117">此範例顯示命令的變數值效果 `$WarningPreference` `Write-Warning` 。</span><span class="sxs-lookup"><span data-stu-id="4f11d-117">This example shows the effect of the value of the `$WarningPreference` variable on a `Write-Warning` command.</span></span>

```powershell
PS> $WarningPreference
Continue
PS> Write-Warning "This is only a test warning."
This is only a test warning.
PS> $WarningPreference = "SilentlyContinue"
PS> Write-Warning "This is only a test warning."
PS> $WarningPreference = "Stop"
PS> Write-Warning "This is only a test warning."
WARNING: This is only a test message.
Write-Warning : Command execution stopped because the shell variable "WarningPreference" is set to Stop.
At line:1 char:14
     + Write-Warning <<<<  "This is only a test message."
```

<span data-ttu-id="4f11d-118">第一個命令會顯示變數的預設值 `$WarningPreference` ，也就是 `Continue` 。</span><span class="sxs-lookup"><span data-stu-id="4f11d-118">The first command displays the default value of the `$WarningPreference` variable, which is `Continue`.</span></span> <span data-ttu-id="4f11d-119">因此，當您撰寫警告時，便會顯示該警告訊息，然後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="4f11d-119">As a result, when you write a warning, the warning message is displayed and execution continues.</span></span>

<span data-ttu-id="4f11d-120">當您變更變數的值時 `$WarningPreference` ，命令的效果會 `Write-Warning` 再次變更。</span><span class="sxs-lookup"><span data-stu-id="4f11d-120">When you change the value of the `$WarningPreference` variable, the effect of the `Write-Warning` command changes again.</span></span> <span data-ttu-id="4f11d-121">的值會 `SilentlyContinue` 抑制警告。</span><span class="sxs-lookup"><span data-stu-id="4f11d-121">A value of `SilentlyContinue` suppresses the warning.</span></span> <span data-ttu-id="4f11d-122">的值會 `Stop` 顯示警告，然後停止執行命令。</span><span class="sxs-lookup"><span data-stu-id="4f11d-122">A value of `Stop` displays the warning and then stops execution of the command.</span></span>

<span data-ttu-id="4f11d-123">如需變數的詳細資訊 `$WarningPreference` ，請參閱 [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="4f11d-123">For more information about the `$WarningPreference` variable, see [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="4f11d-124">範例 4︰設定 WarningAction 參數和寫入警告</span><span class="sxs-lookup"><span data-stu-id="4f11d-124">Example 4: Set the WarningAction parameter and write a warning</span></span>

<span data-ttu-id="4f11d-125">此範例顯示命令的 **WarningAction** 一般參數效果 `Write-Warning` 。</span><span class="sxs-lookup"><span data-stu-id="4f11d-125">This example shows the effect of the **WarningAction** common parameter on a `Write-Warning` command.</span></span> <span data-ttu-id="4f11d-126">您可以使用 **WarningAction** 一般參數搭配任何 Cmdlet，來判斷 PowerShell 如何回應從該命令產生的警告。</span><span class="sxs-lookup"><span data-stu-id="4f11d-126">You can use the **WarningAction** common parameter with any cmdlet to determine how PowerShell responds to warnings resulting from that command.</span></span> <span data-ttu-id="4f11d-127">**WarningAction** 一般參數會覆寫該 `$WarningPreference` 特定命令的唯一值。</span><span class="sxs-lookup"><span data-stu-id="4f11d-127">The **WarningAction** common parameter overrides the value of the `$WarningPreference` only for that particular command.</span></span>

```powershell
PS> Write-Warning "This is only a test warning." -WarningAction Inquire
WARNING: This is only a test warning.
Confirm
Continue with this operation?
 [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="4f11d-128">此命令會使用 `Write-Warning` Cmdlet 來顯示警告。</span><span class="sxs-lookup"><span data-stu-id="4f11d-128">This command uses the `Write-Warning` cmdlet to display a warning.</span></span> <span data-ttu-id="4f11d-129">當 **WarningAction** 一般參數的值為 "Inquire" 時，會指示系統在命令顯示警告時提示使用者。</span><span class="sxs-lookup"><span data-stu-id="4f11d-129">The **WarningAction** common parameter with a value of Inquire directs the system to prompt the user when the command displays a warning.</span></span>

<span data-ttu-id="4f11d-130">如需 **WarningAction** 一般參數的詳細資訊，請參閱 [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="4f11d-130">For more information about the **WarningAction** common parameter, see [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4f11d-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4f11d-131">PARAMETERS</span></span>

### <span data-ttu-id="4f11d-132">-Message</span><span class="sxs-lookup"><span data-stu-id="4f11d-132">-Message</span></span>
<span data-ttu-id="4f11d-133">指定警告訊息。</span><span class="sxs-lookup"><span data-stu-id="4f11d-133">Specifies the warning message.</span></span>

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

### <span data-ttu-id="4f11d-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4f11d-134">CommonParameters</span></span>

<span data-ttu-id="4f11d-135">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4f11d-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4f11d-136">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4f11d-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4f11d-137">輸入</span><span class="sxs-lookup"><span data-stu-id="4f11d-137">INPUTS</span></span>

### <span data-ttu-id="4f11d-138">System.String</span><span class="sxs-lookup"><span data-stu-id="4f11d-138">System.String</span></span>

<span data-ttu-id="4f11d-139">您可以使用管線將包含警告的字串傳送至 `Write-Warning` 。</span><span class="sxs-lookup"><span data-stu-id="4f11d-139">You can pipe a string that contains the warning to `Write-Warning`.</span></span>

## <span data-ttu-id="4f11d-140">輸出</span><span class="sxs-lookup"><span data-stu-id="4f11d-140">OUTPUTS</span></span>

### <span data-ttu-id="4f11d-141">無</span><span class="sxs-lookup"><span data-stu-id="4f11d-141">None</span></span>

<span data-ttu-id="4f11d-142">`Write-Warning` 只寫入警告串流。</span><span class="sxs-lookup"><span data-stu-id="4f11d-142">`Write-Warning` writes only to the warning stream.</span></span> <span data-ttu-id="4f11d-143">它不會產生任何其他輸出。</span><span class="sxs-lookup"><span data-stu-id="4f11d-143">It does not generate any other output.</span></span>

## <span data-ttu-id="4f11d-144">注意</span><span class="sxs-lookup"><span data-stu-id="4f11d-144">NOTES</span></span>

<span data-ttu-id="4f11d-145">變數的預設值 `$WarningPreference` 是 `Continue` ，它會顯示警告，然後繼續執行命令。</span><span class="sxs-lookup"><span data-stu-id="4f11d-145">The default value for the `$WarningPreference` variable is `Continue`, which displays the warning and then continues executing the command.</span></span> <span data-ttu-id="4f11d-146">若要判斷喜好設定變數（例如）的有效值 `$WarningPreference` ，請將它設定為隨機字元的字串，例如 "abc"。</span><span class="sxs-lookup"><span data-stu-id="4f11d-146">To determine valid values for a preference variable such as `$WarningPreference`, set it to a string of random characters, such as "abc".</span></span> <span data-ttu-id="4f11d-147">產生的錯誤訊息會列出有效的值。</span><span class="sxs-lookup"><span data-stu-id="4f11d-147">The resulting error message lists the valid values.</span></span>

## <span data-ttu-id="4f11d-148">相關連結</span><span class="sxs-lookup"><span data-stu-id="4f11d-148">RELATED LINKS</span></span>

[<span data-ttu-id="4f11d-149">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="4f11d-149">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="4f11d-150">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="4f11d-150">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="4f11d-151">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="4f11d-151">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="4f11d-152">Write-Error</span><span class="sxs-lookup"><span data-stu-id="4f11d-152">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="4f11d-153">Write-Host</span><span class="sxs-lookup"><span data-stu-id="4f11d-153">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="4f11d-154">Write-Information</span><span class="sxs-lookup"><span data-stu-id="4f11d-154">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="4f11d-155">Write-Output</span><span class="sxs-lookup"><span data-stu-id="4f11d-155">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="4f11d-156">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="4f11d-156">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="4f11d-157">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="4f11d-157">Write-Verbose</span></span>](Write-Verbose.md)
