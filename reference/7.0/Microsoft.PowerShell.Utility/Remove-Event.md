---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 2730e413a79b2af5355cd2ece7c1e8a6d219d708
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201432"
---
# <span data-ttu-id="f3c29-103">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="f3c29-103">Remove-Event</span></span>

## <span data-ttu-id="f3c29-104">概要</span><span class="sxs-lookup"><span data-stu-id="f3c29-104">SYNOPSIS</span></span>
<span data-ttu-id="f3c29-105">從事件佇列中刪除事件。</span><span class="sxs-lookup"><span data-stu-id="f3c29-105">Deletes events from the event queue.</span></span>

## <span data-ttu-id="f3c29-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f3c29-106">SYNTAX</span></span>

### <span data-ttu-id="f3c29-107">BySource (預設值)</span><span class="sxs-lookup"><span data-stu-id="f3c29-107">BySource (Default)</span></span>

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f3c29-108">ByIdentifier</span><span class="sxs-lookup"><span data-stu-id="f3c29-108">ByIdentifier</span></span>

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f3c29-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f3c29-109">DESCRIPTION</span></span>
<span data-ttu-id="f3c29-110">**Remove 事件** Cmdlet 會從目前會話中的事件佇列刪除事件。</span><span class="sxs-lookup"><span data-stu-id="f3c29-110">The **Remove-Event** cmdlet deletes events from the event queue in the current session.</span></span>

<span data-ttu-id="f3c29-111">這個 Cmdlet 只會刪除目前在佇列中的事件。</span><span class="sxs-lookup"><span data-stu-id="f3c29-111">This cmdlet deletes only the events currently in the queue.</span></span>
<span data-ttu-id="f3c29-112">若要取消事件登錄或取消訂閱，請使用 Unregister-Event Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f3c29-112">To cancel event registrations or unsubscribe, use the Unregister-Event cmdlet.</span></span>

## <span data-ttu-id="f3c29-113">範例</span><span class="sxs-lookup"><span data-stu-id="f3c29-113">EXAMPLES</span></span>

### <span data-ttu-id="f3c29-114">範例 1︰依來源識別碼移除事件</span><span class="sxs-lookup"><span data-stu-id="f3c29-114">Example 1: Remove an event by source identifier</span></span>

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="f3c29-115">這個命令會從事件佇列中刪除來源識別碼為 Process Started 的事件。</span><span class="sxs-lookup"><span data-stu-id="f3c29-115">This command deletes events with a source identifier of Process Started from the event queue.</span></span>

### <span data-ttu-id="f3c29-116">範例 2︰依事件識別碼移除事件</span><span class="sxs-lookup"><span data-stu-id="f3c29-116">Example 2: Remove an event by event identifier</span></span>

```
PS C:\> Remove-Event -EventIdentifier 30
```

<span data-ttu-id="f3c29-117">這個命令會從事件佇列中刪除事件識別碼為 30 的事件。</span><span class="sxs-lookup"><span data-stu-id="f3c29-117">This command deletes the event with an event ID of 30 from the event queue.</span></span>

### <span data-ttu-id="f3c29-118">範例 3：移除所有事件</span><span class="sxs-lookup"><span data-stu-id="f3c29-118">Example 3: Remove all events</span></span>

```
PS C:\> Get-Event | Remove-Event
```

<span data-ttu-id="f3c29-119">這個命令會從事件佇列中刪除所有事件。</span><span class="sxs-lookup"><span data-stu-id="f3c29-119">This command deletes all events from the event queue.</span></span>

## <span data-ttu-id="f3c29-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f3c29-120">PARAMETERS</span></span>

### <span data-ttu-id="f3c29-121">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="f3c29-121">-EventIdentifier</span></span>
<span data-ttu-id="f3c29-122">指定 Cmdlet 要刪除之事件的事件識別碼。</span><span class="sxs-lookup"><span data-stu-id="f3c29-122">Specifies the event identifier for which the cmdlet deletes.</span></span>
<span data-ttu-id="f3c29-123">每個命令中都需要 *EventIdentifier* 或 *SourceIdentifier* 參數。</span><span class="sxs-lookup"><span data-stu-id="f3c29-123">An *EventIdentifier* or *SourceIdentifier* parameter is required in every command.</span></span>

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

### <span data-ttu-id="f3c29-124">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="f3c29-124">-SourceIdentifier</span></span>
<span data-ttu-id="f3c29-125">指定此 Cmdlet 從中刪除事件之來源的來源識別碼。</span><span class="sxs-lookup"><span data-stu-id="f3c29-125">Specifies the source identifier for which this cmdlet deletes events from.</span></span>
<span data-ttu-id="f3c29-126">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f3c29-126">Wildcards are not permitted.</span></span>
<span data-ttu-id="f3c29-127">每個命令中都需要 *EventIdentifier* 或 *SourceIdentifier* 參數。</span><span class="sxs-lookup"><span data-stu-id="f3c29-127">An *EventIdentifier* or *SourceIdentifier* parameter is required in every command.</span></span>

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

### <span data-ttu-id="f3c29-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f3c29-128">-Confirm</span></span>
<span data-ttu-id="f3c29-129">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f3c29-129">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f3c29-130">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f3c29-130">-WhatIf</span></span>
<span data-ttu-id="f3c29-131">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f3c29-131">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f3c29-132">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f3c29-132">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f3c29-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f3c29-133">CommonParameters</span></span>
<span data-ttu-id="f3c29-134">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f3c29-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f3c29-135">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f3c29-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f3c29-136">輸入</span><span class="sxs-lookup"><span data-stu-id="f3c29-136">INPUTS</span></span>

### <span data-ttu-id="f3c29-137">System.Management.Automation.PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="f3c29-137">System.Management.Automation.PSEventArgs</span></span>
<span data-ttu-id="f3c29-138">您可以透過管線將事件從 Get-Event 傳送至 **移除事件** 。</span><span class="sxs-lookup"><span data-stu-id="f3c29-138">You can pipe events from Get-Event to **Remove-Event** .</span></span>

## <span data-ttu-id="f3c29-139">輸出</span><span class="sxs-lookup"><span data-stu-id="f3c29-139">OUTPUTS</span></span>

### <span data-ttu-id="f3c29-140">無</span><span class="sxs-lookup"><span data-stu-id="f3c29-140">None</span></span>
<span data-ttu-id="f3c29-141">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f3c29-141">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f3c29-142">注意</span><span class="sxs-lookup"><span data-stu-id="f3c29-142">NOTES</span></span>

* <span data-ttu-id="f3c29-143">事件、事件訂閱與事件佇列僅存在目前工作階段中。</span><span class="sxs-lookup"><span data-stu-id="f3c29-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="f3c29-144">若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="f3c29-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

*

## <span data-ttu-id="f3c29-145">相關連結</span><span class="sxs-lookup"><span data-stu-id="f3c29-145">RELATED LINKS</span></span>

[<span data-ttu-id="f3c29-146">Get-Event</span><span class="sxs-lookup"><span data-stu-id="f3c29-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="f3c29-147">New-Event</span><span class="sxs-lookup"><span data-stu-id="f3c29-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="f3c29-148">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="f3c29-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="f3c29-149">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="f3c29-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="f3c29-150">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="f3c29-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="f3c29-151">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="f3c29-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="f3c29-152">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="f3c29-152">Wait-Event</span></span>](Wait-Event.md)
