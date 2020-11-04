---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-information?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Information
ms.openlocfilehash: e0f28393c95e2c0703c489d4691edcf883b4cb05
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208436"
---
# <span data-ttu-id="9609e-103">Write-Information</span><span class="sxs-lookup"><span data-stu-id="9609e-103">Write-Information</span></span>

## <span data-ttu-id="9609e-104">概要</span><span class="sxs-lookup"><span data-stu-id="9609e-104">SYNOPSIS</span></span>

<span data-ttu-id="9609e-105">指定 PowerShell 如何處理命令的資訊串流資料。</span><span class="sxs-lookup"><span data-stu-id="9609e-105">Specifies how PowerShell handles information stream data for a command.</span></span>

## <span data-ttu-id="9609e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9609e-106">SYNTAX</span></span>

```
Write-Information [-MessageData] <Object> [[-Tags] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="9609e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9609e-107">DESCRIPTION</span></span>

<span data-ttu-id="9609e-108">`Write-Information`Cmdlet 會指定 PowerShell 如何處理命令的資訊串流資料。</span><span class="sxs-lookup"><span data-stu-id="9609e-108">The `Write-Information` cmdlet specifies how PowerShell handles information stream data for a command.</span></span>

<span data-ttu-id="9609e-109">Windows PowerShell 5.0 引進了新的結構化資訊串流。</span><span class="sxs-lookup"><span data-stu-id="9609e-109">Windows PowerShell 5.0 introduces a new, structured information stream.</span></span> <span data-ttu-id="9609e-110">您可以使用此資料流程在腳本及其呼叫端或主應用程式之間傳輸結構化資料。</span><span class="sxs-lookup"><span data-stu-id="9609e-110">You can use this stream to transmit structured data between a script and its callers or the host application.</span></span>
<span data-ttu-id="9609e-111">`Write-Information` 可讓您將參考用訊息新增至資料流程，並指定 PowerShell 如何處理命令的資訊串流資料。</span><span class="sxs-lookup"><span data-stu-id="9609e-111">`Write-Information` lets you add an informational message to the stream, and specify how PowerShell handles information stream data for a command.</span></span> <span data-ttu-id="9609e-112">資訊串流也適用于 `PowerShell.Streams` 、作業和排程工作。</span><span class="sxs-lookup"><span data-stu-id="9609e-112">Information streams also work for `PowerShell.Streams`, jobs, and scheduled tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="9609e-113">資訊資料流程未遵循在其訊息前面加上 "[Stream Name]：" 的標準慣例。</span><span class="sxs-lookup"><span data-stu-id="9609e-113">The information stream does not follow the standard convention of prefixing its messages with "[Stream Name]:".</span></span> <span data-ttu-id="9609e-114">這是為了簡潔和 visual cleanliness。</span><span class="sxs-lookup"><span data-stu-id="9609e-114">This was intended for brevity and visual cleanliness.</span></span>

<span data-ttu-id="9609e-115">`$InformationPreference`喜好設定變數值會決定您所提供的訊息是否 `Write-Information` 會顯示在腳本作業的預期位置。</span><span class="sxs-lookup"><span data-stu-id="9609e-115">The `$InformationPreference` preference variable value determines whether the message you provide to `Write-Information` is displayed at the expected point in a script's operation.</span></span> <span data-ttu-id="9609e-116">因為這個變數的預設值是 `SilentlyContinue` ，預設不會顯示資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="9609e-116">Because the default value of this variable is `SilentlyContinue`, by default, informational messages are not shown.</span></span> <span data-ttu-id="9609e-117">如果您不想要變更的值 `$InformationPreference` ，可以藉由將一般參數新增至您的命令來覆寫它的值 `InformationAction` 。</span><span class="sxs-lookup"><span data-stu-id="9609e-117">If you don't want to change the value of `$InformationPreference`, you can override its value by adding the `InformationAction` common parameter to your command.</span></span> <span data-ttu-id="9609e-118">如需詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) 和 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="9609e-118">For more information, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md) and [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9609e-119">從 Windows PowerShell 5.0 開始，是的包裝函式，可 `Write-Host` `Write-Information` 讓您用 `Write-Host` 來發出輸出至資訊串流。</span><span class="sxs-lookup"><span data-stu-id="9609e-119">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="9609e-120">這可讓您 **捕捉** 或 **隱藏** 使用撰寫的資料， `Write-Host` 同時保留回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="9609e-120">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span> <span data-ttu-id="9609e-121">如需詳細資訊，請參閱 [寫入主機](Write-Host.md)</span><span class="sxs-lookup"><span data-stu-id="9609e-121">For more information see [Write-Host](Write-Host.md)</span></span>

<span data-ttu-id="9609e-122">`Write-Information` 也是 PowerShell 5.x 中支援的工作流程活動。</span><span class="sxs-lookup"><span data-stu-id="9609e-122">`Write-Information` is also a supported workflow activity in PowerShell 5.x.</span></span>

## <span data-ttu-id="9609e-123">範例</span><span class="sxs-lookup"><span data-stu-id="9609e-123">EXAMPLES</span></span>

### <span data-ttu-id="9609e-124">範例 1：寫入 Get- 結果的資訊</span><span class="sxs-lookup"><span data-stu-id="9609e-124">Example 1: Write information for Get- results</span></span>

<span data-ttu-id="9609e-125">在此範例中，您會在執行命令之後顯示參考用訊息「取得您的功能！」， `Get-WindowsFeature` 以尋找名稱值開頭為 ' p ' 的所有功能。</span><span class="sxs-lookup"><span data-stu-id="9609e-125">In this example, you show an informational message, "Got your features!", after running the `Get-WindowsFeature` command to find all features that have a Name value that starts with 'p'.</span></span>
<span data-ttu-id="9609e-126">因為 `$InformationPreference` 變數仍然設定為預設值，所以 `SilentlyContinue` 您要加入 `InformationAction` 參數來覆寫 `$InformationPreference` 該值，並顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="9609e-126">Because the `$InformationPreference` variable is still set to its default, `SilentlyContinue`, you add the `InformationAction` parameter to override the `$InformationPreference` value, and show the message.</span></span> <span data-ttu-id="9609e-127">此 `InformationAction` 值為 Continue，表示會顯示您的訊息，但腳本或命令會繼續（如果尚未完成）。</span><span class="sxs-lookup"><span data-stu-id="9609e-127">The `InformationAction` value is Continue, which means that your message is shown, but the script or command continues, if it is not yet finished.</span></span>

```powershell
Get-WindowsFeature -Name p*
Write-Information -MessageData "Got your features!" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
Got your features!
```

### <span data-ttu-id="9609e-128">範例 2︰寫入資訊並加以標記</span><span class="sxs-lookup"><span data-stu-id="9609e-128">Example 2: Write information and tag it</span></span>

<span data-ttu-id="9609e-129">在此範例中，您會使用 `Write-Information` 來讓使用者知道，他們在執行目前的命令之後，必須執行另一個命令。</span><span class="sxs-lookup"><span data-stu-id="9609e-129">In this example, you use `Write-Information` to let users know they'll need to run another command after they're done running the current command.</span></span> <span data-ttu-id="9609e-130">此範例會在告知性訊息中新增 Instructions 標記。</span><span class="sxs-lookup"><span data-stu-id="9609e-130">The example adds the tag Instructions to the informational message.</span></span> <span data-ttu-id="9609e-131">執行此命令之後，如果您要針對已標記 Instructions 的訊息搜尋資訊資料流，則此處指定的訊息會位於結果之中。</span><span class="sxs-lookup"><span data-stu-id="9609e-131">After running this command, if you search the information stream for messages tagged Instructions, the message specified here would be among the results.</span></span>

```powershell
$message = "To filter your results for PowerShell, pipe your results to the Where-Object cmdlet."
Get-WindowsFeature -Name p*
Write-Information -MessageData $message -Tags "Instructions" -InformationAction Continue
```

```Output
Display Name                                            Name                       Install State
------------                                            ----                       -------------
[ ] Print and Document Services                         Print-Services                 Available
    [ ] Print Server                                    Print-Server                   Available
    [ ] Distributed Scan Server                         Print-Scan-Server              Available
    [ ] Internet Printing                               Print-Internet                 Available
    [ ] LPD Service                                     Print-LPD-Service              Available
[ ] Peer Name Resolution Protocol                       PNRP                           Available
[X] Windows PowerShell                                  PowerShellRoot                 Installed
    [X] Windows PowerShell 5.0                          PowerShell                     Installed
    [ ] Windows PowerShell 2.0 Engine                   PowerShell-V2                    Removed
    [X] Windows PowerShell ISE                          PowerShell-ISE                 Installed
To filter your results for PowerShell, pipe your results to the Where-Object cmdlet.
```

### <span data-ttu-id="9609e-132">範例 3︰將資訊寫入檔案</span><span class="sxs-lookup"><span data-stu-id="9609e-132">Example 3: Write information to a file</span></span>

```powershell
function Test-Info
{
    Get-Process P*
    Write-Information "Here you go"
}
Test-Info 6> Info.txt
```

## <span data-ttu-id="9609e-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9609e-133">PARAMETERS</span></span>

### <span data-ttu-id="9609e-134">-MessageData</span><span class="sxs-lookup"><span data-stu-id="9609e-134">-MessageData</span></span>

<span data-ttu-id="9609e-135">指定您想要在使用者執行指令碼或命令時顯示的告知性訊息。</span><span class="sxs-lookup"><span data-stu-id="9609e-135">Specifies an informational message that you want to display to users as they run a script or command.</span></span> <span data-ttu-id="9609e-136">為了獲得最佳結果，請以引號括住告知性訊息。</span><span class="sxs-lookup"><span data-stu-id="9609e-136">For best results, enclose the informational message in quotation marks.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9609e-137">-Tags</span><span class="sxs-lookup"><span data-stu-id="9609e-137">-Tags</span></span>

<span data-ttu-id="9609e-138">指定簡單字串，您可以用來排序和篩選您已新增至資訊資料流程的訊息 `Write-Information` 。</span><span class="sxs-lookup"><span data-stu-id="9609e-138">Specifies a simple string that you can use to sort and filter messages that you have added to the information stream with `Write-Information`.</span></span> <span data-ttu-id="9609e-139">這個參數的運作方式類似于中的 **Tags** 參數 `New-ModuleManifest` 。</span><span class="sxs-lookup"><span data-stu-id="9609e-139">This parameter works similarly to the **Tags** parameter in `New-ModuleManifest`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9609e-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9609e-140">CommonParameters</span></span>

<span data-ttu-id="9609e-141">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9609e-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9609e-142">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9609e-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9609e-143">輸入</span><span class="sxs-lookup"><span data-stu-id="9609e-143">INPUTS</span></span>

### <span data-ttu-id="9609e-144">無</span><span class="sxs-lookup"><span data-stu-id="9609e-144">None</span></span>

<span data-ttu-id="9609e-145">`Write-Information` 不接受輸送的輸入。</span><span class="sxs-lookup"><span data-stu-id="9609e-145">`Write-Information` does not accept piped input.</span></span>

## <span data-ttu-id="9609e-146">輸出</span><span class="sxs-lookup"><span data-stu-id="9609e-146">OUTPUTS</span></span>

### <span data-ttu-id="9609e-147">System.Management.Automation.InformationRecord</span><span class="sxs-lookup"><span data-stu-id="9609e-147">System.Management.Automation.InformationRecord</span></span>

## <span data-ttu-id="9609e-148">注意</span><span class="sxs-lookup"><span data-stu-id="9609e-148">NOTES</span></span>

## <span data-ttu-id="9609e-149">相關連結</span><span class="sxs-lookup"><span data-stu-id="9609e-149">RELATED LINKS</span></span>

[<span data-ttu-id="9609e-150">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="9609e-150">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="9609e-151">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="9609e-151">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="9609e-152">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9609e-152">about_CommonParameters</span></span>](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)

[<span data-ttu-id="9609e-153">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="9609e-153">about_Preference_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)

[<span data-ttu-id="9609e-154">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="9609e-154">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="9609e-155">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="9609e-155">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="9609e-156">Write-Host</span><span class="sxs-lookup"><span data-stu-id="9609e-156">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="9609e-157">Write-Information</span><span class="sxs-lookup"><span data-stu-id="9609e-157">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="9609e-158">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="9609e-158">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="9609e-159">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="9609e-159">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="9609e-160">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="9609e-160">Write-Warning</span></span>](Write-Warning.md)

[<span data-ttu-id="9609e-161">Write-Output</span><span class="sxs-lookup"><span data-stu-id="9609e-161">Write-Output</span></span>](Write-Output.md)