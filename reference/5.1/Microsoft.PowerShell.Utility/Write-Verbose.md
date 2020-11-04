---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: e16e002ab9e803900712542c329723f6a44a880f
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208432"
---
# <span data-ttu-id="7e061-103">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="7e061-103">Write-Verbose</span></span>

## <span data-ttu-id="7e061-104">概要</span><span class="sxs-lookup"><span data-stu-id="7e061-104">SYNOPSIS</span></span>
<span data-ttu-id="7e061-105">將文字寫入詳細資訊訊息串流。</span><span class="sxs-lookup"><span data-stu-id="7e061-105">Writes text to the verbose message stream.</span></span>

## <span data-ttu-id="7e061-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7e061-106">SYNTAX</span></span>

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="7e061-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7e061-107">DESCRIPTION</span></span>

<span data-ttu-id="7e061-108">Cmdlet 會將 `Write-Verbose` 文字寫入 PowerShell 中的詳細資訊訊息串流。</span><span class="sxs-lookup"><span data-stu-id="7e061-108">The `Write-Verbose` cmdlet writes text to the verbose message stream in PowerShell.</span></span> <span data-ttu-id="7e061-109">一般而言，詳細資訊訊息串流是用來提供更深入的命令處理相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7e061-109">Typically, the verbose message stream is used to deliver more in depth information about command processing.</span></span>

<span data-ttu-id="7e061-110">根據預設，不會顯示詳細資訊訊息串流，但您可以變更變數的值 `$VerbosePreference` 或在任何命令中使用 **verbose** 一般參數來顯示它。</span><span class="sxs-lookup"><span data-stu-id="7e061-110">By default, the verbose message stream is not displayed, but you can display it by changing the value of the `$VerbosePreference` variable or using the **Verbose** common parameter in any command.</span></span>

## <span data-ttu-id="7e061-111">範例</span><span class="sxs-lookup"><span data-stu-id="7e061-111">EXAMPLES</span></span>

### <span data-ttu-id="7e061-112">範例1：寫入狀態訊息</span><span class="sxs-lookup"><span data-stu-id="7e061-112">Example 1: Write a status message</span></span>

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

<span data-ttu-id="7e061-113">這些命令會使用 `Write-Verbose` Cmdlet 來顯示狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="7e061-113">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="7e061-114">根據預設，不會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="7e061-114">By default, the message is not displayed.</span></span>

<span data-ttu-id="7e061-115">第二個命令會使用 **verbose** 一般參數，其會顯示任何詳細資訊訊息，不論變數的值為何 `$VerbosePreference` 。</span><span class="sxs-lookup"><span data-stu-id="7e061-115">The second command uses the **Verbose** common parameter, which displays any verbose messages, regardless of the value of the `$VerbosePreference` variable.</span></span>

### <span data-ttu-id="7e061-116">範例2：設定 $VerbosePreference 並寫入狀態訊息</span><span class="sxs-lookup"><span data-stu-id="7e061-116">Example 2: Set $VerbosePreference and write a status message</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

<span data-ttu-id="7e061-117">這些命令會使用 `Write-Verbose` Cmdlet 來顯示狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="7e061-117">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="7e061-118">根據預設，不會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="7e061-118">By default, the message is not displayed.</span></span>

<span data-ttu-id="7e061-119">第一個命令會將 Continue 的值指派給 `$VerbosePreference` 喜好設定變數。</span><span class="sxs-lookup"><span data-stu-id="7e061-119">The first command assigns a value of Continue to the `$VerbosePreference` preference variable.</span></span> <span data-ttu-id="7e061-120">預設值會 `SilentlyContinue` 抑制詳細資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="7e061-120">The default value, `SilentlyContinue`, suppresses verbose messages.</span></span> <span data-ttu-id="7e061-121">第二個命令寫入詳細資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="7e061-121">The second command writes a verbose message.</span></span>

## <span data-ttu-id="7e061-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7e061-122">PARAMETERS</span></span>

### <span data-ttu-id="7e061-123">-Message</span><span class="sxs-lookup"><span data-stu-id="7e061-123">-Message</span></span>

<span data-ttu-id="7e061-124">指定要顯示的訊息。</span><span class="sxs-lookup"><span data-stu-id="7e061-124">Specifies the message to display.</span></span> <span data-ttu-id="7e061-125">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="7e061-125">This parameter is required.</span></span> <span data-ttu-id="7e061-126">您也可以使用管線將訊息字串傳送至 `Write-Verbose` 。</span><span class="sxs-lookup"><span data-stu-id="7e061-126">You can also pipe a message string to `Write-Verbose`.</span></span>

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

### <span data-ttu-id="7e061-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e061-127">CommonParameters</span></span>

<span data-ttu-id="7e061-128">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7e061-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7e061-129">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="7e061-129">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7e061-130">輸入</span><span class="sxs-lookup"><span data-stu-id="7e061-130">INPUTS</span></span>

### <span data-ttu-id="7e061-131">System.String</span><span class="sxs-lookup"><span data-stu-id="7e061-131">System.String</span></span>

<span data-ttu-id="7e061-132">您可以使用管線將包含訊息的字串傳送至 `Write-Verbose` 。</span><span class="sxs-lookup"><span data-stu-id="7e061-132">You can pipe a string that contains the message to `Write-Verbose`.</span></span>

## <span data-ttu-id="7e061-133">輸出</span><span class="sxs-lookup"><span data-stu-id="7e061-133">OUTPUTS</span></span>

### <span data-ttu-id="7e061-134">無</span><span class="sxs-lookup"><span data-stu-id="7e061-134">None</span></span>

<span data-ttu-id="7e061-135">`Write-Verbose` 只寫入詳細資訊訊息串流。</span><span class="sxs-lookup"><span data-stu-id="7e061-135">`Write-Verbose` writes only to the verbose message stream.</span></span>

## <span data-ttu-id="7e061-136">注意</span><span class="sxs-lookup"><span data-stu-id="7e061-136">NOTES</span></span>

- <span data-ttu-id="7e061-137">只有在此命令使用 **Verbose** 一般參數時，才會傳回詳細資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="7e061-137">Verbose messages are returned only when the command uses the **Verbose** common parameter.</span></span> <span data-ttu-id="7e061-138">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7e061-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>
- <span data-ttu-id="7e061-139">在 Windows PowerShell 背景工作和遠端命令中， `$VerbosePreference` 工作會話和遠端會話中的變數會決定預設是否顯示詳細資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="7e061-139">In Windows PowerShell background jobs and remote commands, the `$VerbosePreference` variable in the job session and remote session determine whether the verbose message is displayed by default.</span></span>
  <span data-ttu-id="7e061-140">如需變數的詳細資訊 `$VerbosePreference` ，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="7e061-140">For more information about the `$VerbosePreference` variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="7e061-141">相關連結</span><span class="sxs-lookup"><span data-stu-id="7e061-141">RELATED LINKS</span></span>

[<span data-ttu-id="7e061-142">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="7e061-142">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="7e061-143">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="7e061-143">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="7e061-144">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="7e061-144">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="7e061-145">Write-Error</span><span class="sxs-lookup"><span data-stu-id="7e061-145">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="7e061-146">Write-Host</span><span class="sxs-lookup"><span data-stu-id="7e061-146">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="7e061-147">Write-Information</span><span class="sxs-lookup"><span data-stu-id="7e061-147">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="7e061-148">Write-Output</span><span class="sxs-lookup"><span data-stu-id="7e061-148">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="7e061-149">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="7e061-149">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="7e061-150">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="7e061-150">Write-Warning</span></span>](Write-Warning.md)