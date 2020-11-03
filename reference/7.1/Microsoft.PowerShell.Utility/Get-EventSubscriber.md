---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-eventsubscriber?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventSubscriber
ms.openlocfilehash: e1ac039ce49141197c2e14b060118dd4c87f7003
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202832"
---
# <span data-ttu-id="b8d9d-103">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="b8d9d-103">Get-EventSubscriber</span></span>

## <span data-ttu-id="b8d9d-104">概要</span><span class="sxs-lookup"><span data-stu-id="b8d9d-104">SYNOPSIS</span></span>
<span data-ttu-id="b8d9d-105">取得目前工作階段中的事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-105">Gets the event subscribers in the current session.</span></span>

## <span data-ttu-id="b8d9d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b8d9d-106">SYNTAX</span></span>

### <span data-ttu-id="b8d9d-107">BySource (預設值)</span><span class="sxs-lookup"><span data-stu-id="b8d9d-107">BySource (Default)</span></span>

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="b8d9d-108">ById</span><span class="sxs-lookup"><span data-stu-id="b8d9d-108">ById</span></span>

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="b8d9d-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b8d9d-109">DESCRIPTION</span></span>

<span data-ttu-id="b8d9d-110">**EventSubscriber** 指令 Cmdlet 會取得目前會話中的事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-110">The **Get-EventSubscriber** cmdlet gets the event subscribers in the current session.</span></span>

<span data-ttu-id="b8d9d-111">當您使用 Register 事件 Cmdlet 訂閱事件時，會將事件訂閱者新增至您的 PowerShell 會話，而您訂閱的事件會在每次引發時新增至您的事件佇列。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-111">When you subscribe to an event by using a Register event cmdlet, an event subscriber is added to your PowerShell session, and the events to which you subscribed are added to your event queue whenever they are raised.</span></span>
<span data-ttu-id="b8d9d-112">若要取消事件訂閱，請使用 Unregister-Event Cmdlet 刪除事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-112">To cancel an event subscription, delete the event subscriber by using the Unregister-Event cmdlet.</span></span>

## <span data-ttu-id="b8d9d-113">範例</span><span class="sxs-lookup"><span data-stu-id="b8d9d-113">EXAMPLES</span></span>

### <span data-ttu-id="b8d9d-114">範例1：取得計時器事件的事件訂閱者</span><span class="sxs-lookup"><span data-stu-id="b8d9d-114">Example 1: Get the event subscriber for a timer event</span></span>

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
TypeName: System.Timers.Timer
Name     MemberType Definition
----     ---------- ----------
Disposed Event      System.EventHandler Disposed(System.Object, System.EventArgs)
Elapsed  Event      System.Timers.ElapsedEventHandler Elapsed(System.Object, System.Timers.ElapsedEventArgs) PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
SubscriptionId   : 4
SourceObject     : System.Timers.Timer
EventName        : Elapsed
SourceIdentifier : Timer.Elapsed
Action           :
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False
```

<span data-ttu-id="b8d9d-115">此範例使用 **EventSubscriber** 命令取得計時器事件的事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-115">This example uses a **Get-EventSubscriber** command to get the event subscriber for a timer event.</span></span>

<span data-ttu-id="b8d9d-116">第一個命令使用 New-Object Cmdlet 建立一個計時器物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-116">The first command uses the New-Object cmdlet to create an instance of a timer object.</span></span>
<span data-ttu-id="b8d9d-117">它會將新的計時器物件儲存在 $Timer 變數中。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-117">It saves the new timer object in the $Timer variable.</span></span>

<span data-ttu-id="b8d9d-118">第二個命令使用 Get-Member Cmdlet 顯示可供計時器物件使用的事件。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-118">The second command uses the Get-Member cmdlet to display the events that are available for timer objects.</span></span>
<span data-ttu-id="b8d9d-119">此命令會使用 **Get 成員** Cmdlet 的型別參數搭配事件的值。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-119">The command uses the Type parameter of the **Get-Member** cmdlet with a value of Event.</span></span>

<span data-ttu-id="b8d9d-120">第三個命令使用 Register-ObjectEvent Cmdlet 登錄計時器物件的 Elapsed 事件。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-120">The third command uses the Register-ObjectEvent cmdlet to register for the Elapsed event on the timer object.</span></span>

<span data-ttu-id="b8d9d-121">第四個命令使用 **EventSubscriber** 指令程式取得事件訂閱者以取得已經過的事件。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-121">The fourth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber for the Elapsed event.</span></span>

### <span data-ttu-id="b8d9d-122">範例2：在事件訂閱者的 Action 屬性中使用 PSEventJob 中的動態模組</span><span class="sxs-lookup"><span data-stu-id="b8d9d-122">Example 2: Use the dynamic module in PSEventJob in the Action property of the event subscriber</span></span>

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer.Interval = 500
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Random -Action { $Random = Get-Random -Min 0 -Max 100 }

Id  Name           State      HasMoreData  Location  Command
--  ----           -----      -----------  --------  -------
3   Timer.Random   NotStarted False                  $Random = Get-Random ...

PS C:\> $Timer.Enabled = $True
PS C:\> $Subscriber = Get-EventSubscriber -SourceIdentifier Timer.Random
PS C:\> ($Subscriber.action).gettype().fullname
System.Management.Automation.PSEventJob
PS C:\> $Subscriber.action | Format-List -Property *

State         : Running
Module        : __DynamicModule_6b5cbe82-d634-41d1-ae5e-ad7fe8d57fe0
StatusMessage :
HasMoreData   : True
Location      :
Command       : $random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 88944290-133d-4b44-8752-f901bd8012e2
Id            : 1
Name          : Timer.Random
ChildJobs     : {}
...

PS C:\> & $Subscriber.action.module {$Random}
96
PS C:\> & $Subscriber.action.module {$Random}
23
```

<span data-ttu-id="b8d9d-123">這個範例示範如何在事件訂閱者的 Action 屬性中，使用 **PSEventJob** 物件中的動態模組。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-123">This example shows how to use the dynamic module in the **PSEventJob** object in the Action property of the event subscriber.</span></span>

<span data-ttu-id="b8d9d-124">第一個命令使用 New-Object Cmdlet 來建立計時器物件。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-124">The first command uses the New-Object cmdlet to create a timer object.</span></span>
<span data-ttu-id="b8d9d-125">第二個命令將計時器的間隔設定為 500 (毫秒)。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-125">The second command sets the interval of the timer to 500 (milliseconds).</span></span>

<span data-ttu-id="b8d9d-126">第三個命令使用 Register-ObjectEvent Cmdlet 來登錄計時器物件的 Elapsed 事件。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-126">The third command uses the Register-ObjectEvent cmdlet to register the Elapsed event of the timer object.</span></span>
<span data-ttu-id="b8d9d-127">此命令包含一個處理事件的動作。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-127">The command includes an action that handles the event.</span></span>
<span data-ttu-id="b8d9d-128">每當計時器的間隔經過之後，就會引發事件，而動作中的命令也會執行。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-128">Whenever the timer interval elapses, an event is raised and the commands in the action run.</span></span>
<span data-ttu-id="b8d9d-129">在此情況下，Get-Random Cmdlet 會產生0到100之間的亂數字，並將它儲存在 $Random 變數中。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-129">In this case, the Get-Random cmdlet generates a random number between 0 and 100 and saves it in the $Random variable.</span></span>
<span data-ttu-id="b8d9d-130">事件的來源識別碼是 Timer.Random。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-130">The source identifier of the event is Timer.Random.</span></span>

<span data-ttu-id="b8d9d-131">當您在 **ObjectEvent** 命令中使用 *Action* 參數時，此命令會傳回代表該動作的 **PSEventJob** 物件。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-131">When you use an *Action* parameter in a **Register-ObjectEvent** command, the command returns a **PSEventJob** object that represents the action.</span></span>

<span data-ttu-id="b8d9d-132">第四個命令啟用計時器。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-132">The fourth command enables the timer.</span></span>

<span data-ttu-id="b8d9d-133">第五個命令使用 **EventSubscriber 指令程式** 取得 Timer 的事件訂閱者。隨機事件。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-133">The fifth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber of the Timer.Random event.</span></span>
<span data-ttu-id="b8d9d-134">它會將事件訂閱者物件儲存在 $Subscriber 變數中。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-134">It saves the event subscriber object in the $Subscriber variable.</span></span>

<span data-ttu-id="b8d9d-135">第六個命令顯示事件訂閱者物件的 Action 屬性包含 **PSEventJob** 物件。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-135">The sixth command shows that the Action property of the event subscriber object contains a **PSEventJob** object.</span></span>
<span data-ttu-id="b8d9d-136">事實上，它包含的 **PSEventJob** 物件與 **ObjectEvent** 命令傳回的相同。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-136">In fact, it contains the same **PSEventJob** object that the **Register-ObjectEvent** command returned.</span></span>

<span data-ttu-id="b8d9d-137">第七個命令使用 Format-List Cmdlet，在清單的 Action 屬性中顯示 **PSEventJob** 物件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-137">The seventh command uses the Format-List cmdlet to display all of the properties of the **PSEventJob** object in the Action property in a list.</span></span>
<span data-ttu-id="b8d9d-138">結果顯示 **PSEventJob** 物件有一個 Module 屬性，其中包含可執行動作的動態腳本模組。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-138">The result reveals that the **PSEventJob** object has a Module property that contains a dynamic script module that implements the action.</span></span>

<span data-ttu-id="b8d9d-139">其餘的命令會使用呼叫運算子 ( # A0) 來叫用模組中的命令，並顯示 $Random 變數的值。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-139">The remaining commands use the call operator (&) to invoke the command in the module and display the value of the $Random variable.</span></span>
<span data-ttu-id="b8d9d-140">您可以使用呼叫運算子來叫用模組中的任何命令，包括未匯出的命令。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-140">You can use the call operator to invoke any command in a module, including commands that are not exported.</span></span>
<span data-ttu-id="b8d9d-141">在此情況下，這些命令會顯示 Elapsed 事件發生時所產生的隨機數字。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-141">In this case, the commands show the random number that is being generated when the Elapsed event occurs.</span></span>

<span data-ttu-id="b8d9d-142">如需模組的詳細資訊，請參閱 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-142">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

## <span data-ttu-id="b8d9d-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b8d9d-143">PARAMETERS</span></span>

### <span data-ttu-id="b8d9d-144">-Force</span><span class="sxs-lookup"><span data-stu-id="b8d9d-144">-Force</span></span>

<span data-ttu-id="b8d9d-145">指出此 Cmdlet 會取得所有事件訂閱者，包括使用 *SupportEvent* 參數 ObjectEvent、register >register-wmievent 和 register >register-engineevent 來隱藏事件的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-145">Indicates that this cmdlet gets all event subscribers, including subscribers for events that are hidden by using the *SupportEvent* parameter of Register-ObjectEvent, Register-WmiEvent, and Register-EngineEvent.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8d9d-146">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="b8d9d-146">-SourceIdentifier</span></span>

<span data-ttu-id="b8d9d-147">指定只取得事件訂閱者的 **SourceIdentifier** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-147">Specifies the **SourceIdentifier** property value that gets only the event subscribers.</span></span>
<span data-ttu-id="b8d9d-148">根據預設， **EventSubscriber** 會取得會話中的所有事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-148">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>
<span data-ttu-id="b8d9d-149">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-149">Wildcards are not permitted.</span></span>
<span data-ttu-id="b8d9d-150">此參數區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-150">This parameter is case-sensitive.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b8d9d-151">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="b8d9d-151">-SubscriptionId</span></span>

<span data-ttu-id="b8d9d-152">指定此 Cmdlet 取得的訂用帳戶識別碼。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-152">Specifies the subscription identifier that this cmdlet gets.</span></span>
<span data-ttu-id="b8d9d-153">根據預設， **EventSubscriber** 會取得會話中的所有事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-153">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases: Id

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b8d9d-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8d9d-154">CommonParameters</span></span>

<span data-ttu-id="b8d9d-155">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b8d9d-156">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b8d9d-157">輸入</span><span class="sxs-lookup"><span data-stu-id="b8d9d-157">INPUTS</span></span>

### <span data-ttu-id="b8d9d-158">無</span><span class="sxs-lookup"><span data-stu-id="b8d9d-158">None</span></span>

<span data-ttu-id="b8d9d-159">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-159">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b8d9d-160">輸出</span><span class="sxs-lookup"><span data-stu-id="b8d9d-160">OUTPUTS</span></span>

### <span data-ttu-id="b8d9d-161">System.Management.Automation.PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="b8d9d-161">System.Management.Automation.PSEventSubscriber</span></span>

<span data-ttu-id="b8d9d-162">**EventSubscriber** 會傳回代表每個事件訂閱者的物件。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-162">**Get-EventSubscriber** returns an object that represents each event subscriber.</span></span>

## <span data-ttu-id="b8d9d-163">注意</span><span class="sxs-lookup"><span data-stu-id="b8d9d-163">NOTES</span></span>

* <span data-ttu-id="b8d9d-164">New-Event Cmdlet 建立自訂事件，不會產生訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-164">The New-Event cmdlet, which creates a custom event, does not generate a subscriber.</span></span> <span data-ttu-id="b8d9d-165">因此， **EventSubscriber 指令程式** 將找不到這些事件的訂閱者物件。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-165">Therefore, the **Get-EventSubscriber** cmdlet will not find a subscriber object for these events.</span></span> <span data-ttu-id="b8d9d-166">但是，如果您使用 Register-EngineEvent Cmdlet 來訂閱自訂事件 (為了轉寄事件或指定動作) ， **EventSubscriber** 會尋找 **>register-engineevent** 產生的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-166">However, if you use the Register-EngineEvent cmdlet to subscribe to a custom event (in order to forward the event or to specify an action), **Get-EventSubscriber** will find the subscriber that **Register-EngineEvent** generates.</span></span>

  <span data-ttu-id="b8d9d-167">事件、事件訂閱與事件佇列僅存在目前工作階段中。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-167">Events, event subscriptions, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="b8d9d-168">若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="b8d9d-168">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

*

## <span data-ttu-id="b8d9d-169">相關連結</span><span class="sxs-lookup"><span data-stu-id="b8d9d-169">RELATED LINKS</span></span>

[<span data-ttu-id="b8d9d-170">Get-Event</span><span class="sxs-lookup"><span data-stu-id="b8d9d-170">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="b8d9d-171">New-Event</span><span class="sxs-lookup"><span data-stu-id="b8d9d-171">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="b8d9d-172">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="b8d9d-172">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="b8d9d-173">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="b8d9d-173">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="b8d9d-174">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="b8d9d-174">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="b8d9d-175">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="b8d9d-175">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="b8d9d-176">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="b8d9d-176">Wait-Event</span></span>](Wait-Event.md)

