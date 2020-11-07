---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 35d5d75cad2855753504549262abd2e14af200c0
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344485"
---
# <span data-ttu-id="f2d2e-103">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="f2d2e-103">Remove-Event</span></span>

## <span data-ttu-id="f2d2e-104">概要</span><span class="sxs-lookup"><span data-stu-id="f2d2e-104">SYNOPSIS</span></span>
<span data-ttu-id="f2d2e-105">從事件佇列中刪除事件。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-105">Deletes events from the event queue.</span></span>

## <span data-ttu-id="f2d2e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f2d2e-106">SYNTAX</span></span>

### <span data-ttu-id="f2d2e-107">BySource (預設值)</span><span class="sxs-lookup"><span data-stu-id="f2d2e-107">BySource (Default)</span></span>

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f2d2e-108">ByIdentifier</span><span class="sxs-lookup"><span data-stu-id="f2d2e-108">ByIdentifier</span></span>

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f2d2e-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f2d2e-109">DESCRIPTION</span></span>

<span data-ttu-id="f2d2e-110">此 `Remove-Event` Cmdlet 會從目前會話中的事件佇列刪除事件。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-110">The `Remove-Event` cmdlet deletes events from the event queue in the current session.</span></span>

<span data-ttu-id="f2d2e-111">這個 Cmdlet 只會刪除目前在佇列中的事件。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-111">This cmdlet deletes only the events currently in the queue.</span></span> <span data-ttu-id="f2d2e-112">若要取消事件註冊或取消訂閱，請使用 `Unregister-Event` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-112">To cancel event registrations or unsubscribe, use the `Unregister-Event` cmdlet.</span></span>

## <span data-ttu-id="f2d2e-113">範例</span><span class="sxs-lookup"><span data-stu-id="f2d2e-113">EXAMPLES</span></span>

### <span data-ttu-id="f2d2e-114">範例 1︰依來源識別碼移除事件</span><span class="sxs-lookup"><span data-stu-id="f2d2e-114">Example 1: Remove an event by source identifier</span></span>

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="f2d2e-115">這個命令會從事件佇列中刪除來源識別碼為 Process Started 的事件。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-115">This command deletes events with a source identifier of Process Started from the event queue.</span></span>

### <span data-ttu-id="f2d2e-116">範例 2︰依事件識別碼移除事件</span><span class="sxs-lookup"><span data-stu-id="f2d2e-116">Example 2: Remove an event by event identifier</span></span>

```
PS C:\> Remove-Event -EventIdentifier 30
```

<span data-ttu-id="f2d2e-117">這個命令會從事件佇列中刪除事件識別碼為 30 的事件。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-117">This command deletes the event with an event ID of 30 from the event queue.</span></span>

### <span data-ttu-id="f2d2e-118">範例 3：移除所有事件</span><span class="sxs-lookup"><span data-stu-id="f2d2e-118">Example 3: Remove all events</span></span>

```
PS C:\> Get-Event | Remove-Event
```

<span data-ttu-id="f2d2e-119">這個命令會從事件佇列中刪除所有事件。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-119">This command deletes all events from the event queue.</span></span>

## <span data-ttu-id="f2d2e-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f2d2e-120">PARAMETERS</span></span>

### <span data-ttu-id="f2d2e-121">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="f2d2e-121">-EventIdentifier</span></span>

<span data-ttu-id="f2d2e-122">指定 Cmdlet 要刪除之事件的事件識別碼。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-122">Specifies the event identifier for which the cmdlet deletes.</span></span> <span data-ttu-id="f2d2e-123">每個命令中都需要 **EventIdentifier** 或 **SourceIdentifier** 參數。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-123">An **EventIdentifier** or **SourceIdentifier** parameter is required in every command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ByIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f2d2e-124">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="f2d2e-124">-SourceIdentifier</span></span>

<span data-ttu-id="f2d2e-125">指定此 Cmdlet 從中刪除事件之來源的來源識別碼。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-125">Specifies the source identifier for which this cmdlet deletes events from.</span></span> <span data-ttu-id="f2d2e-126">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-126">Wildcards are not permitted.</span></span> <span data-ttu-id="f2d2e-127">每個命令中都需要 **EventIdentifier** 或 **SourceIdentifier** 參數。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-127">An **EventIdentifier** or **SourceIdentifier** parameter is required in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d2e-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f2d2e-128">-Confirm</span></span>

<span data-ttu-id="f2d2e-129">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-129">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d2e-130">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f2d2e-130">-WhatIf</span></span>

<span data-ttu-id="f2d2e-131">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-131">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f2d2e-132">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-132">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d2e-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2d2e-133">CommonParameters</span></span>

<span data-ttu-id="f2d2e-134">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2d2e-135">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2d2e-136">輸入</span><span class="sxs-lookup"><span data-stu-id="f2d2e-136">INPUTS</span></span>

### <span data-ttu-id="f2d2e-137">System.Management.Automation.PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="f2d2e-137">System.Management.Automation.PSEventArgs</span></span>

<span data-ttu-id="f2d2e-138">您可以透過管線將事件傳送 `Get-Event` 至 `Remove-Event` 。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-138">You can pipe events from `Get-Event` to `Remove-Event`.</span></span>

## <span data-ttu-id="f2d2e-139">輸出</span><span class="sxs-lookup"><span data-stu-id="f2d2e-139">OUTPUTS</span></span>

### <span data-ttu-id="f2d2e-140">None</span><span class="sxs-lookup"><span data-stu-id="f2d2e-140">None</span></span>

<span data-ttu-id="f2d2e-141">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-141">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f2d2e-142">注意</span><span class="sxs-lookup"><span data-stu-id="f2d2e-142">NOTES</span></span>

<span data-ttu-id="f2d2e-143">事件、事件訂閱與事件佇列僅存在目前工作階段中。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="f2d2e-144">若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="f2d2e-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="f2d2e-145">相關連結</span><span class="sxs-lookup"><span data-stu-id="f2d2e-145">RELATED LINKS</span></span>

[<span data-ttu-id="f2d2e-146">Get-Event</span><span class="sxs-lookup"><span data-stu-id="f2d2e-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="f2d2e-147">New-Event</span><span class="sxs-lookup"><span data-stu-id="f2d2e-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="f2d2e-148">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="f2d2e-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="f2d2e-149">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="f2d2e-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="f2d2e-150">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="f2d2e-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="f2d2e-151">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="f2d2e-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="f2d2e-152">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="f2d2e-152">Wait-Event</span></span>](Wait-Event.md)
