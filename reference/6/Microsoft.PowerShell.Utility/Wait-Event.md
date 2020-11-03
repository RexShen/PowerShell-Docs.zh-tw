---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: 8384cf6a4922bf408f4ac569f651c1a3b584d8af
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204292"
---
# <span data-ttu-id="3fa05-103">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="3fa05-103">Wait-Event</span></span>

## <span data-ttu-id="3fa05-104">概要</span><span class="sxs-lookup"><span data-stu-id="3fa05-104">SYNOPSIS</span></span>
<span data-ttu-id="3fa05-105">等候引發特定事件後再繼續執行。</span><span class="sxs-lookup"><span data-stu-id="3fa05-105">Waits until a particular event is raised before continuing to run.</span></span>

## <span data-ttu-id="3fa05-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3fa05-106">SYNTAX</span></span>

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="3fa05-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3fa05-107">DESCRIPTION</span></span>

<span data-ttu-id="3fa05-108">`Wait-Event`Cmdlet 會暫停腳本或函式的執行，直到引發特定事件為止。</span><span class="sxs-lookup"><span data-stu-id="3fa05-108">The `Wait-Event` cmdlet suspends execution of a script or function until a particular event is raised.</span></span> <span data-ttu-id="3fa05-109">當偵測到事件時，就會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="3fa05-109">Execution resumes when the event is detected.</span></span> <span data-ttu-id="3fa05-110">若要取消等待，請按下<kbd>CTRL</kbd> + <kbd>C</kbd>。</span><span class="sxs-lookup"><span data-stu-id="3fa05-110">To cancel the wait, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="3fa05-111">這個功能為事件輪詢提供一個替代方案。</span><span class="sxs-lookup"><span data-stu-id="3fa05-111">This feature provides an alternative to polling for an event.</span></span> <span data-ttu-id="3fa05-112">它也可讓您以兩種不同的方式來判斷事件的回應：</span><span class="sxs-lookup"><span data-stu-id="3fa05-112">It also allows you to determine the response to an event in two different ways:</span></span>

- <span data-ttu-id="3fa05-113">使用事件訂閱的 **Action** 參數</span><span class="sxs-lookup"><span data-stu-id="3fa05-113">using the **Action** parameter of the event subscription</span></span>
- <span data-ttu-id="3fa05-114">等候事件返回，然後以動作回應</span><span class="sxs-lookup"><span data-stu-id="3fa05-114">waiting for an event to return and then respond with an action</span></span>

## <span data-ttu-id="3fa05-115">範例</span><span class="sxs-lookup"><span data-stu-id="3fa05-115">EXAMPLES</span></span>

### <span data-ttu-id="3fa05-116">範例1：等候下一個事件</span><span class="sxs-lookup"><span data-stu-id="3fa05-116">Example 1: Wait for the next event</span></span>

<span data-ttu-id="3fa05-117">此範例會等待下一個引發的事件。</span><span class="sxs-lookup"><span data-stu-id="3fa05-117">This example waits for the next event that is raised.</span></span>

```powershell
Wait-Event
```

### <span data-ttu-id="3fa05-118">範例2：等候具有指定來源識別碼的事件</span><span class="sxs-lookup"><span data-stu-id="3fa05-118">Example 2: Wait for an event with a specified source identifier</span></span>

<span data-ttu-id="3fa05-119">此範例會等待下一個引發且來源識別碼為 ProcessStarted 的事件。</span><span class="sxs-lookup"><span data-stu-id="3fa05-119">This example waits for the next event that is raised and that has a source identifier of ProcessStarted.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="3fa05-120">範例3：等候計時器經過的事件</span><span class="sxs-lookup"><span data-stu-id="3fa05-120">Example 3: Wait for a timer elapsed event</span></span>

<span data-ttu-id="3fa05-121">這個範例會使用指令程式 `Wait-Event` 來等候設定為2000毫秒之計時器上的計時器事件。</span><span class="sxs-lookup"><span data-stu-id="3fa05-121">This example uses the `Wait-Event` cmdlet to wait for a timer event on a timer that is set for 2000 milliseconds.</span></span>

```powershell
$Timer = New-Object Timers.Timer
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Elapsed'
}
Register-ObjectEvent @objectEventArgs
$Timer.Interval = 2000
$Timer.Autoreset = $False
$Timer.Enabled = $True
Wait-Event Timer.Elapsed
```

```Output
ComputerName     :
RunspaceId       : bb560b14-ff43-48d4-b801-5adc31bbc6fb
EventIdentifier  : 1
Sender           : System.Timers.Timer
SourceEventArgs  : System.Timers.ElapsedEventArgs
SourceArgs       : {System.Timers.Timer, System.Timers.ElapsedEventArgs}
SourceIdentifier : Timer.Elapsed
TimeGenerated    : 4/23/2020 2:30:37 PM
MessageData      :
```

### <span data-ttu-id="3fa05-122">範例4：等候指定的超時時間之後的事件</span><span class="sxs-lookup"><span data-stu-id="3fa05-122">Example 4: Wait for an event after a specified timeout</span></span>

<span data-ttu-id="3fa05-123">此範例會等待下一個引發且來源識別碼為 **ProcessStarted** 的事件最多90秒。</span><span class="sxs-lookup"><span data-stu-id="3fa05-123">This example waits up to 90 seconds for the next event that is raised and that has a source identifier of **ProcessStarted** .</span></span> <span data-ttu-id="3fa05-124">如果指定的時間過期，就會結束等待。</span><span class="sxs-lookup"><span data-stu-id="3fa05-124">If the specified time expires, the wait ends.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## <span data-ttu-id="3fa05-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3fa05-125">PARAMETERS</span></span>

### <span data-ttu-id="3fa05-126">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="3fa05-126">-SourceIdentifier</span></span>

<span data-ttu-id="3fa05-127">指定此 Cmdlet 等候事件的來源識別碼。</span><span class="sxs-lookup"><span data-stu-id="3fa05-127">Specifies the source identifier that this cmdlet waits for events.</span></span>
<span data-ttu-id="3fa05-128">根據預設，會 `Wait-Event` 等待任何事件。</span><span class="sxs-lookup"><span data-stu-id="3fa05-128">By default, `Wait-Event` waits for any event.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3fa05-129">-Timeout</span><span class="sxs-lookup"><span data-stu-id="3fa05-129">-Timeout</span></span>

<span data-ttu-id="3fa05-130">指定等候事件發生的最長時間（以秒為單位） `Wait-Event` 。</span><span class="sxs-lookup"><span data-stu-id="3fa05-130">Specifies the maximum time, in seconds, that `Wait-Event` waits for the event to occur.</span></span> <span data-ttu-id="3fa05-131">預設值 -1 表示會無限期等待。</span><span class="sxs-lookup"><span data-stu-id="3fa05-131">The default, -1, waits indefinitely.</span></span> <span data-ttu-id="3fa05-132">當您提交命令時，便會開始計時 `Wait-Event` 。</span><span class="sxs-lookup"><span data-stu-id="3fa05-132">The timing starts when you submit the `Wait-Event` command.</span></span>

<span data-ttu-id="3fa05-133">如果超過指定的時間，即使未引發事件，也會結束等待並返回命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="3fa05-133">If the specified time is exceeded, the wait ends and the command prompt returns, even if the event has not been raised.</span></span> <span data-ttu-id="3fa05-134">不會顯示任何錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="3fa05-134">No error message is displayed.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: -1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3fa05-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3fa05-135">CommonParameters</span></span>

<span data-ttu-id="3fa05-136">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3fa05-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3fa05-137">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3fa05-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3fa05-138">輸入</span><span class="sxs-lookup"><span data-stu-id="3fa05-138">INPUTS</span></span>

### <span data-ttu-id="3fa05-139">System.String</span><span class="sxs-lookup"><span data-stu-id="3fa05-139">System.String</span></span>

## <span data-ttu-id="3fa05-140">輸出</span><span class="sxs-lookup"><span data-stu-id="3fa05-140">OUTPUTS</span></span>

### <span data-ttu-id="3fa05-141">System.Management.Automation.PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="3fa05-141">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="3fa05-142">注意</span><span class="sxs-lookup"><span data-stu-id="3fa05-142">NOTES</span></span>

<span data-ttu-id="3fa05-143">事件、事件訂閱與事件佇列僅存在目前工作階段中。</span><span class="sxs-lookup"><span data-stu-id="3fa05-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="3fa05-144">若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="3fa05-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="3fa05-145">相關連結</span><span class="sxs-lookup"><span data-stu-id="3fa05-145">RELATED LINKS</span></span>

[<span data-ttu-id="3fa05-146">Get-Event</span><span class="sxs-lookup"><span data-stu-id="3fa05-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="3fa05-147">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="3fa05-147">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="3fa05-148">New-Event</span><span class="sxs-lookup"><span data-stu-id="3fa05-148">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="3fa05-149">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="3fa05-149">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="3fa05-150">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="3fa05-150">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="3fa05-151">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="3fa05-151">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="3fa05-152">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="3fa05-152">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="3fa05-153">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="3fa05-153">Wait-Event</span></span>](Wait-Event.md)
