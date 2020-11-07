---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: b7aab2ef1e97ae1cc19d42b07145bd7a057f33fc
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347749"
---
# <span data-ttu-id="35703-103">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="35703-103">Unregister-Event</span></span>

## <span data-ttu-id="35703-104">概要</span><span class="sxs-lookup"><span data-stu-id="35703-104">SYNOPSIS</span></span>
<span data-ttu-id="35703-105">取消事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="35703-105">Cancels an event subscription.</span></span>

## <span data-ttu-id="35703-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="35703-106">SYNTAX</span></span>

### <span data-ttu-id="35703-107">BySource (預設值)</span><span class="sxs-lookup"><span data-stu-id="35703-107">BySource (Default)</span></span>

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="35703-108">ById</span><span class="sxs-lookup"><span data-stu-id="35703-108">ById</span></span>

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="35703-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="35703-109">DESCRIPTION</span></span>

<span data-ttu-id="35703-110">此 `Unregister-Event` Cmdlet 會取消使用 `Register-EngineEvent` 、或 Cmdlet 所建立的事件訂閱 `Register-ObjectEvent` `Register-WmiEvent` 。</span><span class="sxs-lookup"><span data-stu-id="35703-110">The `Unregister-Event` cmdlet cancels an event subscription that was created by using the `Register-EngineEvent`, `Register-ObjectEvent`, or `Register-WmiEvent` cmdlet.</span></span>

<span data-ttu-id="35703-111">取消事件訂閱時，會從工作階段刪除事件訂閱者，也不會再將訂閱的事件新增至事件佇列。</span><span class="sxs-lookup"><span data-stu-id="35703-111">When an event subscription is canceled, the event subscriber is deleted from the session and the subscribed events are no longer added to the event queue.</span></span> <span data-ttu-id="35703-112">當您取消使用指令程式所建立之事件的訂閱時 `New-Event` ，也會從會話中刪除新的事件。</span><span class="sxs-lookup"><span data-stu-id="35703-112">When you cancel a subscription to an event created by using the `New-Event` cmdlet, the new event is also deleted from the session.</span></span>

<span data-ttu-id="35703-113">`Unregister-Event` 不會刪除事件佇列中的事件。</span><span class="sxs-lookup"><span data-stu-id="35703-113">`Unregister-Event` does not delete events from the event queue.</span></span> <span data-ttu-id="35703-114">若要刪除事件，請使用 `Remove-Event` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="35703-114">To delete events, use the `Remove-Event` cmdlet.</span></span>

## <span data-ttu-id="35703-115">範例</span><span class="sxs-lookup"><span data-stu-id="35703-115">EXAMPLES</span></span>

### <span data-ttu-id="35703-116">範例 1︰依來源識別碼取消事件訂閱</span><span class="sxs-lookup"><span data-stu-id="35703-116">Example 1: Cancel an event subscription by source identifier</span></span>

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="35703-117">此命令會取消來源識別碼為 ProcessStarted 的事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="35703-117">This command cancels the event subscription that has a source identifier of ProcessStarted.</span></span>

<span data-ttu-id="35703-118">若要尋找事件的來源識別碼，請使用 `Get-Event` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="35703-118">To find the source identifier of an event, use the `Get-Event` cmdlet.</span></span> <span data-ttu-id="35703-119">若要尋找事件訂用帳戶的來源識別碼，請使用 `Get-EventSubscriber` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="35703-119">To find the source identifier of an event subscription, use the `Get-EventSubscriber` cmdlet.</span></span>

### <span data-ttu-id="35703-120">範例 2︰依訂閱識別碼取消事件訂閱</span><span class="sxs-lookup"><span data-stu-id="35703-120">Example 2: Cancel an event subscription by subscription identifier</span></span>

```
PS C:\> Unregister-Event -SubscriptionId 2
```

<span data-ttu-id="35703-121">此命令會取消訂閱識別碼為 2 的事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="35703-121">This command cancels the event subscription that has a subscription identifier of 2.</span></span>

<span data-ttu-id="35703-122">若要尋找事件訂用帳戶的訂用帳戶識別碼，請使用 `Get-EventSubscriber` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="35703-122">To find the subscription identifier of an event subscription, use the `Get-EventSubscriber` cmdlet.</span></span>

### <span data-ttu-id="35703-123">範例 3︰取消所有事件訂閱</span><span class="sxs-lookup"><span data-stu-id="35703-123">Example 3: Cancel all event subscriptions</span></span>

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

<span data-ttu-id="35703-124">此命令會取消工作階段中的所有事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="35703-124">This command cancels all event subscriptions in the session.</span></span>

<span data-ttu-id="35703-125">此命令會使用 `Get-EventSubscriber` Cmdlet 來取得會話中的所有事件訂閱者物件，包括使用事件註冊 Cmdlet 的 **SupportEvent** 參數隱藏的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="35703-125">The command uses the `Get-EventSubscriber` cmdlet to get all event subscriber objects in the session, including the subscribers that are hidden by using the **SupportEvent** parameter of the event registration cmdlets.</span></span>

<span data-ttu-id="35703-126">它使用管線運算子 (`|`) 將訂閱者物件傳送至 `Unregister-Event` ，這會將它們從會話中刪除。</span><span class="sxs-lookup"><span data-stu-id="35703-126">It uses a pipeline operator (`|`) to send the subscriber objects to `Unregister-Event`, which deletes them from the session.</span></span> <span data-ttu-id="35703-127">若要完成此工作，在上也需要 **Force** 參數 `Unregister-Event` 。</span><span class="sxs-lookup"><span data-stu-id="35703-127">To complete the task, the **Force** parameter is also required on `Unregister-Event`.</span></span>

## <span data-ttu-id="35703-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="35703-128">PARAMETERS</span></span>

### <span data-ttu-id="35703-129">-Force</span><span class="sxs-lookup"><span data-stu-id="35703-129">-Force</span></span>

<span data-ttu-id="35703-130">取消所有事件訂閱，包括使用、和之 **SupportEvent** 參數隱藏的訂閱 `Register-ObjectEvent` `Register-WmiEvent` `Register-EngineEvent` 。</span><span class="sxs-lookup"><span data-stu-id="35703-130">Cancels all event subscriptions, including subscriptions that were hidden by using the **SupportEvent** parameter of `Register-ObjectEvent`, `Register-WmiEvent`, and `Register-EngineEvent`.</span></span>

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

### <span data-ttu-id="35703-131">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="35703-131">-SourceIdentifier</span></span>

<span data-ttu-id="35703-132">指定此 Cmdlet 取消事件訂閱的來源識別碼。</span><span class="sxs-lookup"><span data-stu-id="35703-132">Specifies a source identifier that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="35703-133">每個命令中必須包含 **SourceIdentifier** 或 **SubscriptionId** 參數。</span><span class="sxs-lookup"><span data-stu-id="35703-133">A **SourceIdentifier** or **SubscriptionId** parameter must be included in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35703-134">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="35703-134">-SubscriptionId</span></span>

<span data-ttu-id="35703-135">指定此 Cmdlet 取消事件訂閱的來源識別碼 ID。</span><span class="sxs-lookup"><span data-stu-id="35703-135">Specifies a source identifier ID that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="35703-136">每個命令中必須包含 **SourceIdentifier** 或 **SubscriptionId** 參數。</span><span class="sxs-lookup"><span data-stu-id="35703-136">A **SourceIdentifier** or **SubscriptionId** parameter must be included in every command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="35703-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="35703-137">-Confirm</span></span>

<span data-ttu-id="35703-138">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="35703-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="35703-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="35703-139">-WhatIf</span></span>

<span data-ttu-id="35703-140">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="35703-140">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="35703-141">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="35703-141">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="35703-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="35703-142">CommonParameters</span></span>

<span data-ttu-id="35703-143">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="35703-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="35703-144">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="35703-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="35703-145">輸入</span><span class="sxs-lookup"><span data-stu-id="35703-145">INPUTS</span></span>

### <span data-ttu-id="35703-146">System.Management.Automation.PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="35703-146">System.Management.Automation.PSEventSubscriber</span></span>

<span data-ttu-id="35703-147">您可以透過管道將輸出傳送 `Get-EventSubscriber` 至 `Unregister-Event` 。</span><span class="sxs-lookup"><span data-stu-id="35703-147">You can pipe the output from `Get-EventSubscriber` to `Unregister-Event`.</span></span>

## <span data-ttu-id="35703-148">輸出</span><span class="sxs-lookup"><span data-stu-id="35703-148">OUTPUTS</span></span>

### <span data-ttu-id="35703-149">None</span><span class="sxs-lookup"><span data-stu-id="35703-149">None</span></span>

<span data-ttu-id="35703-150">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="35703-150">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="35703-151">注意</span><span class="sxs-lookup"><span data-stu-id="35703-151">NOTES</span></span>

<span data-ttu-id="35703-152">Linux 或 macOS 平臺上沒有可用的事件來源。</span><span class="sxs-lookup"><span data-stu-id="35703-152">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="35703-153">事件、事件訂閱與事件佇列僅存在目前工作階段中。</span><span class="sxs-lookup"><span data-stu-id="35703-153">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="35703-154">若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="35703-154">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

<span data-ttu-id="35703-155">`Unregister-Event``New-Event`除非您已使用 Cmdlet 訂閱事件，否則無法刪除使用指令程式所建立的事件 `Register-EngineEvent` 。</span><span class="sxs-lookup"><span data-stu-id="35703-155">`Unregister-Event` cannot delete events created by using the `New-Event` cmdlet unless you have subscribed to the event by using the `Register-EngineEvent` cmdlet.</span></span> <span data-ttu-id="35703-156">若要從工作階段刪除自訂事件，您必須以程式設計方式將它移除，或關閉工作階段。</span><span class="sxs-lookup"><span data-stu-id="35703-156">To delete a custom event from the session, you must remove it programmatically or close the session.</span></span>

## <span data-ttu-id="35703-157">相關連結</span><span class="sxs-lookup"><span data-stu-id="35703-157">RELATED LINKS</span></span>

[<span data-ttu-id="35703-158">Get-Event</span><span class="sxs-lookup"><span data-stu-id="35703-158">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="35703-159">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="35703-159">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="35703-160">New-Event</span><span class="sxs-lookup"><span data-stu-id="35703-160">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="35703-161">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="35703-161">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="35703-162">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="35703-162">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="35703-163">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="35703-163">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="35703-164">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="35703-164">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="35703-165">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="35703-165">Wait-Event</span></span>](Wait-Event.md)
