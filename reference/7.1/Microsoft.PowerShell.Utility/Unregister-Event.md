---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: 748ef22203f59090be6f5491ea76b50d54930a95
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205068"
---
# <span data-ttu-id="140fc-103">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="140fc-103">Unregister-Event</span></span>

## <span data-ttu-id="140fc-104">概要</span><span class="sxs-lookup"><span data-stu-id="140fc-104">SYNOPSIS</span></span>
<span data-ttu-id="140fc-105">取消事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="140fc-105">Cancels an event subscription.</span></span>

## <span data-ttu-id="140fc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="140fc-106">SYNTAX</span></span>

### <span data-ttu-id="140fc-107">BySource (預設值)</span><span class="sxs-lookup"><span data-stu-id="140fc-107">BySource (Default)</span></span>

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="140fc-108">ById</span><span class="sxs-lookup"><span data-stu-id="140fc-108">ById</span></span>

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="140fc-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="140fc-109">DESCRIPTION</span></span>
<span data-ttu-id="140fc-110">**Unregister-Event** Cmdlet 會取消使用 Register-EngineEvent、Register-ObjectEvent 或 Register-WmiEvent Cmdlet 建立的事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="140fc-110">The **Unregister-Event** cmdlet cancels an event subscription that was created by using the Register-EngineEvent, Register-ObjectEvent, or Register-WmiEvent cmdlet.</span></span>

<span data-ttu-id="140fc-111">取消事件訂閱時，會從工作階段刪除事件訂閱者，也不會再將訂閱的事件新增至事件佇列。</span><span class="sxs-lookup"><span data-stu-id="140fc-111">When an event subscription is canceled, the event subscriber is deleted from the session and the subscribed events are no longer added to the event queue.</span></span>
<span data-ttu-id="140fc-112">當您取消訂閱使用 New-Event Cmdlet 建立的事件時，也會從工作階段刪除新的事件。</span><span class="sxs-lookup"><span data-stu-id="140fc-112">When you cancel a subscription to an event created by using the New-Event cmdlet, the new event is also deleted from the session.</span></span>

<span data-ttu-id="140fc-113">**Unregister-Event** 不會從事件佇列刪除事件。</span><span class="sxs-lookup"><span data-stu-id="140fc-113">**Unregister-Event** does not delete events from the event queue.</span></span>
<span data-ttu-id="140fc-114">若要刪除事件，請使用 Remove-Event Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="140fc-114">To delete events, use the Remove-Event cmdlet.</span></span>

## <span data-ttu-id="140fc-115">範例</span><span class="sxs-lookup"><span data-stu-id="140fc-115">EXAMPLES</span></span>

### <span data-ttu-id="140fc-116">範例 1︰依來源識別碼取消事件訂閱</span><span class="sxs-lookup"><span data-stu-id="140fc-116">Example 1: Cancel an event subscription by source identifier</span></span>

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="140fc-117">此命令會取消來源識別碼為 ProcessStarted 的事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="140fc-117">This command cancels the event subscription that has a source identifier of ProcessStarted.</span></span>

<span data-ttu-id="140fc-118">若要尋找事件的來源識別碼，請使用 Get-Event Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="140fc-118">To find the source identifier of an event, use the Get-Event cmdlet.</span></span>
<span data-ttu-id="140fc-119">若要尋找事件訂閱的來源識別碼，請使用 **Get-EventSubscriber** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="140fc-119">To find the source identifier of an event subscription, use the **Get-EventSubscriber** cmdlet.</span></span>

### <span data-ttu-id="140fc-120">範例 2︰依訂閱識別碼取消事件訂閱</span><span class="sxs-lookup"><span data-stu-id="140fc-120">Example 2: Cancel an event subscription by subscription identifier</span></span>

```
PS C:\> Unregister-Event -SubscriptionId 2
```

<span data-ttu-id="140fc-121">此命令會取消訂閱識別碼為 2 的事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="140fc-121">This command cancels the event subscription that has a subscription identifier of 2.</span></span>

<span data-ttu-id="140fc-122">若要尋找事件訂閱的訂閱識別碼，請使用 **Get-EventSubscriber** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="140fc-122">To find the subscription identifier of an event subscription, use the **Get-EventSubscriber** cmdlet.</span></span>

### <span data-ttu-id="140fc-123">範例 3︰取消所有事件訂閱</span><span class="sxs-lookup"><span data-stu-id="140fc-123">Example 3: Cancel all event subscriptions</span></span>

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

<span data-ttu-id="140fc-124">此命令會取消工作階段中的所有事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="140fc-124">This command cancels all event subscriptions in the session.</span></span>

<span data-ttu-id="140fc-125">此命令會使用 **Get-EventSubscriber** Cmdlet 取得工作階段中的所有事件訂閱者物件，包括使用事件註冊 Cmdlet 之 *SupportEvent* 參數隱藏的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="140fc-125">The command uses the **Get-EventSubscriber** cmdlet to get all event subscriber objects in the session, including the subscribers that are hidden by using the *SupportEvent* parameter of the event registration cmdlets.</span></span>

<span data-ttu-id="140fc-126">它會使用管線運算子 (|) 將訂閱者物件傳送給 **Unregister-Event** ，這會將它們從工作階段中刪除。</span><span class="sxs-lookup"><span data-stu-id="140fc-126">It uses a pipeline operator (|) to send the subscriber objects to **Unregister-Event** , which deletes them from the session.</span></span>
<span data-ttu-id="140fc-127">若要完成工作， **Unregister-Event** 中也需有 *Force* 參數。</span><span class="sxs-lookup"><span data-stu-id="140fc-127">To complete the task, the *Force* parameter is also required on **Unregister-Event** .</span></span>

## <span data-ttu-id="140fc-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="140fc-128">PARAMETERS</span></span>

### <span data-ttu-id="140fc-129">-Force</span><span class="sxs-lookup"><span data-stu-id="140fc-129">-Force</span></span>
<span data-ttu-id="140fc-130">取消所有事件訂閱，包括使用 **Register-ObjectEvent** 、 **Register-WmiEvent** 及 **Register-EngineEvent** 的 *SupportEvent* 參數隱藏的訂閱。</span><span class="sxs-lookup"><span data-stu-id="140fc-130">Cancels all event subscriptions, including subscriptions that were hidden by using the *SupportEvent* parameter of **Register-ObjectEvent** , **Register-WmiEvent** , and **Register-EngineEvent** .</span></span>

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

### <span data-ttu-id="140fc-131">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="140fc-131">-SourceIdentifier</span></span>
<span data-ttu-id="140fc-132">指定此 Cmdlet 取消事件訂閱的來源識別碼。</span><span class="sxs-lookup"><span data-stu-id="140fc-132">Specifies a source identifier that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="140fc-133">每個命令中必須包含 *SourceIdentifier* 或 *SubscriptionId* 參數。</span><span class="sxs-lookup"><span data-stu-id="140fc-133">A *SourceIdentifier* or *SubscriptionId* parameter must be included in every command.</span></span>

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

### <span data-ttu-id="140fc-134">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="140fc-134">-SubscriptionId</span></span>
<span data-ttu-id="140fc-135">指定此 Cmdlet 取消事件訂閱的來源識別碼 ID。</span><span class="sxs-lookup"><span data-stu-id="140fc-135">Specifies a source identifier ID that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="140fc-136">每個命令中必須包含 *SourceIdentifier* 或 *SubscriptionId* 參數。</span><span class="sxs-lookup"><span data-stu-id="140fc-136">A *SourceIdentifier* or *SubscriptionId* parameter must be included in every command.</span></span>

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

### <span data-ttu-id="140fc-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="140fc-137">-Confirm</span></span>
<span data-ttu-id="140fc-138">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="140fc-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="140fc-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="140fc-139">-WhatIf</span></span>
<span data-ttu-id="140fc-140">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="140fc-140">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="140fc-141">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="140fc-141">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="140fc-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="140fc-142">CommonParameters</span></span>
<span data-ttu-id="140fc-143">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="140fc-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="140fc-144">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="140fc-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="140fc-145">輸入</span><span class="sxs-lookup"><span data-stu-id="140fc-145">INPUTS</span></span>

### <span data-ttu-id="140fc-146">System.Management.Automation.PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="140fc-146">System.Management.Automation.PSEventSubscriber</span></span>
<span data-ttu-id="140fc-147">您可以使用管線將輸出從 Get-EventSubscriber 傳送至 **Unregister-Event** 。</span><span class="sxs-lookup"><span data-stu-id="140fc-147">You can pipe the output from Get-EventSubscriber to **Unregister-Event** .</span></span>

## <span data-ttu-id="140fc-148">輸出</span><span class="sxs-lookup"><span data-stu-id="140fc-148">OUTPUTS</span></span>

### <span data-ttu-id="140fc-149">無</span><span class="sxs-lookup"><span data-stu-id="140fc-149">None</span></span>
<span data-ttu-id="140fc-150">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="140fc-150">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="140fc-151">注意</span><span class="sxs-lookup"><span data-stu-id="140fc-151">NOTES</span></span>

* <span data-ttu-id="140fc-152">事件、事件訂閱與事件佇列僅存在目前工作階段中。</span><span class="sxs-lookup"><span data-stu-id="140fc-152">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="140fc-153">若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="140fc-153">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

  <span data-ttu-id="140fc-154">**Unregister-Event** 無法刪除使用 New-Event Cmdlet 建立的事件，除非您已經使用 **Register-EngineEvent** Cmdlet 訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="140fc-154">**Unregister-Event** cannot delete events created by using the New-Event cmdlet unless you have subscribed to the event by using the **Register-EngineEvent** cmdlet.</span></span>
<span data-ttu-id="140fc-155">若要從工作階段刪除自訂事件，您必須以程式設計方式將它移除，或關閉工作階段。</span><span class="sxs-lookup"><span data-stu-id="140fc-155">To delete a custom event from the session, you must remove it programmatically or close the session.</span></span>

*

## <span data-ttu-id="140fc-156">相關連結</span><span class="sxs-lookup"><span data-stu-id="140fc-156">RELATED LINKS</span></span>

[<span data-ttu-id="140fc-157">Get-Event</span><span class="sxs-lookup"><span data-stu-id="140fc-157">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="140fc-158">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="140fc-158">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="140fc-159">New-Event</span><span class="sxs-lookup"><span data-stu-id="140fc-159">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="140fc-160">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="140fc-160">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="140fc-161">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="140fc-161">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="140fc-162">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="140fc-162">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="140fc-163">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="140fc-163">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="140fc-164">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="140fc-164">Wait-Event</span></span>](Wait-Event.md)

