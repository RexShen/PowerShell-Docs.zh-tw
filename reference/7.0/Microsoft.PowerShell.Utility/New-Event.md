---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: e842aca53947b4dc9e606f2f6b17532c7c9e0cb4
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346644"
---
# <span data-ttu-id="34bce-103">New-Event</span><span class="sxs-lookup"><span data-stu-id="34bce-103">New-Event</span></span>

## <span data-ttu-id="34bce-104">概要</span><span class="sxs-lookup"><span data-stu-id="34bce-104">SYNOPSIS</span></span>
<span data-ttu-id="34bce-105">建立新的事件。</span><span class="sxs-lookup"><span data-stu-id="34bce-105">Creates a new event.</span></span>

## <span data-ttu-id="34bce-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="34bce-106">SYNTAX</span></span>

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="34bce-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="34bce-107">DESCRIPTION</span></span>

<span data-ttu-id="34bce-108">`New-Event`Cmdlet 會建立新的自訂事件。</span><span class="sxs-lookup"><span data-stu-id="34bce-108">The `New-Event` cmdlet creates a new custom event.</span></span>

<span data-ttu-id="34bce-109">您可以使用自訂事件來通知使用者關於程式的狀態變更，以及您的程式可偵測到的任何變更，包括硬體或系統狀況、應用程式狀態、磁碟狀態、網路狀態或背景工作完成。</span><span class="sxs-lookup"><span data-stu-id="34bce-109">You can use custom events to notify users about state changes in your program and any change that your program can detect, including hardware or system conditions, application status, disk status, network status, or the completion of a background job.</span></span>

<span data-ttu-id="34bce-110">自訂事件每次引發時會自動新增至您工作階段的事件佇列，不需要訂閱它們。</span><span class="sxs-lookup"><span data-stu-id="34bce-110">Custom events are automatically added to the event queue in your session whenever they are raised; you do not need to subscribe to them.</span></span> <span data-ttu-id="34bce-111">但是，如果您想要將事件轉送到本機會話，或指定回應事件的動作，請使用 `Register-EngineEvent` Cmdlet 來訂閱自訂事件。</span><span class="sxs-lookup"><span data-stu-id="34bce-111">However, if you want to forward an event to the local session or specify an action to respond to the event, use the `Register-EngineEvent` cmdlet to subscribe to the custom event.</span></span>

<span data-ttu-id="34bce-112">當您訂閱自訂事件時，會將事件訂閱者新增到您的工作階段中。</span><span class="sxs-lookup"><span data-stu-id="34bce-112">When you subscribe to a custom event, the event subscriber is added to your session.</span></span> <span data-ttu-id="34bce-113">如果您使用 Cmdlet 取消事件訂閱 `Unregister-Event` ，則會從會話刪除事件訂閱者和自訂事件。</span><span class="sxs-lookup"><span data-stu-id="34bce-113">If you cancel the event subscription by using the `Unregister-Event` cmdlet, the event subscriber and custom event are deleted from the session.</span></span> <span data-ttu-id="34bce-114">如果您沒有訂閱自訂事件，必須變更程式條件或關閉 PowerShell 會話，才能刪除事件。</span><span class="sxs-lookup"><span data-stu-id="34bce-114">If you do not subscribe to the custom event, to delete the event, you must change the program conditions or close the PowerShell session.</span></span>

## <span data-ttu-id="34bce-115">範例</span><span class="sxs-lookup"><span data-stu-id="34bce-115">EXAMPLES</span></span>

### <span data-ttu-id="34bce-116">範例1：在事件佇列中建立新事件</span><span class="sxs-lookup"><span data-stu-id="34bce-116">Example 1: Create a new event in the event queue</span></span>

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

<span data-ttu-id="34bce-117">此命令會在 PowerShell 事件佇列中建立新的事件。</span><span class="sxs-lookup"><span data-stu-id="34bce-117">This command creates a new event in the PowerShell event queue.</span></span> <span data-ttu-id="34bce-118">它會使用 **Windows Timer** 物件來傳送事件。</span><span class="sxs-lookup"><span data-stu-id="34bce-118">It uses a **Windows.Timer** object to send the event.</span></span>

### <span data-ttu-id="34bce-119">範例2：引發事件以回應另一個事件</span><span class="sxs-lookup"><span data-stu-id="34bce-119">Example 2: Raise an event in response to another event</span></span>

```
PS C:\> function Enable-ProcessCreationEvent
{
   $Query = New-Object System.Management.WqlEventQuery "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1), "TargetInstance isa 'Win32_Process'"
   $ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
   $Identifier = "WMI.ProcessCreated"
   Register-ObjectEvent $ProcessWatcher "EventArrived" -SupportEvent $Identifier -Action
   {
      [void] (New-Event -SourceID "PowerShell.ProcessCreated" -Sender $Args[0] -EventArguments $Args[1].SourceEventArgs.NewEvent.TargetInstance)
   }
}
```

<span data-ttu-id="34bce-120">這個範例函式會使用 `New-Event` Cmdlet 來引發事件以回應另一個事件。</span><span class="sxs-lookup"><span data-stu-id="34bce-120">This sample function uses the `New-Event` cmdlet to raise an event in response to another event.</span></span> <span data-ttu-id="34bce-121">此命令會使用 `Register-ObjectEvent` Cmdlet 來訂閱在新的進程建立時所引發的 Windows Management Instrumentation (WMI) 事件。</span><span class="sxs-lookup"><span data-stu-id="34bce-121">The command uses the `Register-ObjectEvent` cmdlet to subscribe to the Windows Management Instrumentation (WMI) event that is raised when a new process is created.</span></span> <span data-ttu-id="34bce-122">此命令會使用 Cmdlet 的 **Action** 參數來呼叫 `New-Event` Cmdlet，以建立新的事件。</span><span class="sxs-lookup"><span data-stu-id="34bce-122">The command uses the **Action** parameter of the cmdlet to call the `New-Event` cmdlet, which creates the new event.</span></span>

<span data-ttu-id="34bce-123">由於引發的事件會 `New-Event` 自動新增至 PowerShell 事件佇列，因此不需要註冊該事件。</span><span class="sxs-lookup"><span data-stu-id="34bce-123">Because the events that `New-Event` raises are automatically added to the PowerShell event queue, you do not need to register for that event.</span></span>

## <span data-ttu-id="34bce-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="34bce-124">PARAMETERS</span></span>

### <span data-ttu-id="34bce-125">-EventArguments</span><span class="sxs-lookup"><span data-stu-id="34bce-125">-EventArguments</span></span>

<span data-ttu-id="34bce-126">指定包含事件選項的物件。</span><span class="sxs-lookup"><span data-stu-id="34bce-126">Specifies an object that contains options for the event.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34bce-127">-MessageData</span><span class="sxs-lookup"><span data-stu-id="34bce-127">-MessageData</span></span>

<span data-ttu-id="34bce-128">指定與事件關聯的其他資料。</span><span class="sxs-lookup"><span data-stu-id="34bce-128">Specifies additional data associated with the event.</span></span> <span data-ttu-id="34bce-129">此參數的值會顯示在事件物件的 **MessageData** 屬性。</span><span class="sxs-lookup"><span data-stu-id="34bce-129">The value of this parameter appears in the **MessageData** property of the event object.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34bce-130">-寄件者</span><span class="sxs-lookup"><span data-stu-id="34bce-130">-Sender</span></span>

<span data-ttu-id="34bce-131">指定引發事件的物件。</span><span class="sxs-lookup"><span data-stu-id="34bce-131">Specifies the object that raises the event.</span></span> <span data-ttu-id="34bce-132">預設值為 PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="34bce-132">The default is the PowerShell engine.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34bce-133">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="34bce-133">-SourceIdentifier</span></span>

<span data-ttu-id="34bce-134">指定新事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="34bce-134">Specifies a name for the new event.</span></span> <span data-ttu-id="34bce-135">此為必要參數，它在工作階段中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="34bce-135">This parameter is required, and it must be unique in the session.</span></span>

<span data-ttu-id="34bce-136">此參數的值會出現在事件的 **SourceIdentifier** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="34bce-136">The value of this parameter appears in the **SourceIdentifier** property of the events.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="34bce-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="34bce-137">CommonParameters</span></span>

<span data-ttu-id="34bce-138">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="34bce-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="34bce-139">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="34bce-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="34bce-140">輸入</span><span class="sxs-lookup"><span data-stu-id="34bce-140">INPUTS</span></span>

### <span data-ttu-id="34bce-141">None</span><span class="sxs-lookup"><span data-stu-id="34bce-141">None</span></span>

<span data-ttu-id="34bce-142">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="34bce-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="34bce-143">輸出</span><span class="sxs-lookup"><span data-stu-id="34bce-143">OUTPUTS</span></span>

### <span data-ttu-id="34bce-144">System.Management.Automation.PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="34bce-144">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="34bce-145">注意</span><span class="sxs-lookup"><span data-stu-id="34bce-145">NOTES</span></span>

<span data-ttu-id="34bce-146">Linux 或 macOS 平臺上沒有可用的事件來源。</span><span class="sxs-lookup"><span data-stu-id="34bce-146">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="34bce-147">新的自訂事件、事件訂閱與事件佇列只會存在目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="34bce-147">The new custom event, the event subscription, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="34bce-148">若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="34bce-148">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="34bce-149">相關連結</span><span class="sxs-lookup"><span data-stu-id="34bce-149">RELATED LINKS</span></span>

[<span data-ttu-id="34bce-150">Get-Event</span><span class="sxs-lookup"><span data-stu-id="34bce-150">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="34bce-151">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="34bce-151">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="34bce-152">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="34bce-152">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="34bce-153">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="34bce-153">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="34bce-154">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="34bce-154">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="34bce-155">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="34bce-155">Wait-Event</span></span>](Wait-Event.md)
