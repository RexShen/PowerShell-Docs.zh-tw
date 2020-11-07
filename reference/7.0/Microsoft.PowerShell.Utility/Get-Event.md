---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-event?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Event
ms.openlocfilehash: 45d9e45bfbbeba7b9467985dc6abf3a28cd8702b
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342343"
---
# <span data-ttu-id="a547a-103">Get-Event</span><span class="sxs-lookup"><span data-stu-id="a547a-103">Get-Event</span></span>

## <span data-ttu-id="a547a-104">概要</span><span class="sxs-lookup"><span data-stu-id="a547a-104">SYNOPSIS</span></span>
<span data-ttu-id="a547a-105">取得事件佇列中的事件。</span><span class="sxs-lookup"><span data-stu-id="a547a-105">Gets the events in the event queue.</span></span>

## <span data-ttu-id="a547a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a547a-106">SYNTAX</span></span>

### <span data-ttu-id="a547a-107">BySource (預設值)</span><span class="sxs-lookup"><span data-stu-id="a547a-107">BySource (Default)</span></span>

```
Get-Event [[-SourceIdentifier] <String>] [<CommonParameters>]
```

### <span data-ttu-id="a547a-108">ById</span><span class="sxs-lookup"><span data-stu-id="a547a-108">ById</span></span>

```
Get-Event [-EventIdentifier] <Int32> [<CommonParameters>]
```

## <span data-ttu-id="a547a-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a547a-109">DESCRIPTION</span></span>

<span data-ttu-id="a547a-110">Cmdlet 會取得 `Get-Event` 目前會話的 PowerShell 事件佇列中的事件。</span><span class="sxs-lookup"><span data-stu-id="a547a-110">The `Get-Event` cmdlet gets events in the PowerShell event queue for the current session.</span></span> <span data-ttu-id="a547a-111">您可以取得所有事件，或使用 **EventIdentifier** 或 **SourceIdentifier** 參數來指定事件。</span><span class="sxs-lookup"><span data-stu-id="a547a-111">You can get all events or use the **EventIdentifier** or **SourceIdentifier** parameter to specify the events.</span></span>

<span data-ttu-id="a547a-112">發生事件時，它會新增到事件佇列。</span><span class="sxs-lookup"><span data-stu-id="a547a-112">When an event occurs, it is added to the event queue.</span></span> <span data-ttu-id="a547a-113">事件佇列包含您已註冊的事件、使用指令程式所建立的事件 `New-Event` ，以及在 PowerShell 結束時引發的事件。</span><span class="sxs-lookup"><span data-stu-id="a547a-113">The event queue includes events for which you have registered, events created by using the `New-Event` cmdlet, and the event that is raised when PowerShell exits.</span></span> <span data-ttu-id="a547a-114">您可以使用 `Get-Event` 或 `Wait-Event` 來取得事件。</span><span class="sxs-lookup"><span data-stu-id="a547a-114">You can use `Get-Event` or `Wait-Event` to get the events.</span></span>

<span data-ttu-id="a547a-115">這個 Cmdlet 不會從事件檢視器記錄檔取得事件。</span><span class="sxs-lookup"><span data-stu-id="a547a-115">This cmdlet does not get events from the Event Viewer logs.</span></span> <span data-ttu-id="a547a-116">若要取得這些事件，請使用 `Get-WinEvent` 或 `Get-EventLog` 。</span><span class="sxs-lookup"><span data-stu-id="a547a-116">To get those events, use `Get-WinEvent` or `Get-EventLog`.</span></span>

## <span data-ttu-id="a547a-117">範例</span><span class="sxs-lookup"><span data-stu-id="a547a-117">EXAMPLES</span></span>

### <span data-ttu-id="a547a-118">範例 1︰取得所有事件</span><span class="sxs-lookup"><span data-stu-id="a547a-118">Example 1: Get all events</span></span>

```
PS C:\> Get-Event
```

<span data-ttu-id="a547a-119">此命令會取得事件佇列中所有的事件。</span><span class="sxs-lookup"><span data-stu-id="a547a-119">This command gets all events in the event queue.</span></span>

### <span data-ttu-id="a547a-120">範例 2︰依來源識別碼取得事件</span><span class="sxs-lookup"><span data-stu-id="a547a-120">Example 2: Get events by source identifier</span></span>

```
PS C:\> Get-Event -SourceIdentifier "PowerShell.ProcessCreated"
```

<span data-ttu-id="a547a-121">此命令會取得 SourceIdentifier 屬性值是 PowerShell.ProcessCreated 的事件。</span><span class="sxs-lookup"><span data-stu-id="a547a-121">This command gets events in which the value of the SourceIdentifier property is PowerShell.ProcessCreated.</span></span>

### <span data-ttu-id="a547a-122">範例 3︰根據事件產生時間取得事件</span><span class="sxs-lookup"><span data-stu-id="a547a-122">Example 3: Get an event based on the time it was generated</span></span>

```
PS C:\> $Events = Get-Event
PS C:\> $Events[0] | Format-List -Property *
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b805917d1b7b
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:09:32 PM
MessageData      : PS C:\> Get-Event | Where {$_.TimeGenerated -ge "11/13/2008 12:15:00 PM"}
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b8059325d1a0
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:15:00 PM
MessageData      :
```

<span data-ttu-id="a547a-123">這個範例示範如何使用 SourceIdentifier 以外的屬性來取得事件。</span><span class="sxs-lookup"><span data-stu-id="a547a-123">This example shows how to get events by using properties other than SourceIdentifier.</span></span>

<span data-ttu-id="a547a-124">第一個命令會取得事件佇列中的所有事件，並將它們儲存在 `$Events` 變數中。</span><span class="sxs-lookup"><span data-stu-id="a547a-124">The first command gets all events in the event queue and saves them in the `$Events` variable.</span></span>

<span data-ttu-id="a547a-125">第二個命令會使用陣列標記法，取得變數中陣列中的第一個 (0 索引) 事件 `$Events` 。</span><span class="sxs-lookup"><span data-stu-id="a547a-125">The second command uses array notation to get the first (0-index) event in the array in the `$Events` variable.</span></span> <span data-ttu-id="a547a-126">此命令會使用管線運算子 (`|`) 將事件傳送至 `Format-List` 命令，此命令會在清單中顯示事件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="a547a-126">The command uses a pipeline operator (`|`) to send the event to the `Format-List` command, which displays all properties of the event in a list.</span></span> <span data-ttu-id="a547a-127">這可讓您檢視事件物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="a547a-127">This allows you to examine the properties of the event object.</span></span>

<span data-ttu-id="a547a-128">第三個命令會顯示如何使用指令 `Where-Object` 程式，以根據產生的時間取得事件。</span><span class="sxs-lookup"><span data-stu-id="a547a-128">The third command shows how to use the `Where-Object` cmdlet to get an event based on the time that it was generated.</span></span>

### <span data-ttu-id="a547a-129">範例 4︰依識別碼取得事件</span><span class="sxs-lookup"><span data-stu-id="a547a-129">Example 4: Get an event by its identifier</span></span>

```
PS C:\> Get-Event -EventIdentifier 2
```

<span data-ttu-id="a547a-130">此命令取得事件識別碼為 2 的事件。</span><span class="sxs-lookup"><span data-stu-id="a547a-130">This command gets the event with an event identifier of 2.</span></span>

## <span data-ttu-id="a547a-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a547a-131">PARAMETERS</span></span>

### <span data-ttu-id="a547a-132">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="a547a-132">-EventIdentifier</span></span>

<span data-ttu-id="a547a-133">指定此 Cmdlet 用以取得事件的事件識別碼。</span><span class="sxs-lookup"><span data-stu-id="a547a-133">Specifies the event identifiers for which this cmdlet gets events.</span></span>

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

### <span data-ttu-id="a547a-134">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="a547a-134">-SourceIdentifier</span></span>

<span data-ttu-id="a547a-135">指定此 Cmdlet 用以取得事件的來源識別碼。</span><span class="sxs-lookup"><span data-stu-id="a547a-135">Specifies source identifiers for which this cmdlet gets events.</span></span> <span data-ttu-id="a547a-136">預設為事件佇列中的所有事件。</span><span class="sxs-lookup"><span data-stu-id="a547a-136">The default is all events in the event queue.</span></span> <span data-ttu-id="a547a-137">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a547a-137">Wildcards are not permitted.</span></span>

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

### <span data-ttu-id="a547a-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a547a-138">CommonParameters</span></span>

<span data-ttu-id="a547a-139">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a547a-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a547a-140">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a547a-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a547a-141">輸入</span><span class="sxs-lookup"><span data-stu-id="a547a-141">INPUTS</span></span>

### <span data-ttu-id="a547a-142">None</span><span class="sxs-lookup"><span data-stu-id="a547a-142">None</span></span>

<span data-ttu-id="a547a-143">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a547a-143">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a547a-144">輸出</span><span class="sxs-lookup"><span data-stu-id="a547a-144">OUTPUTS</span></span>

### <span data-ttu-id="a547a-145">System.Management.Automation.PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="a547a-145">System.Management.Automation.PSEventArgs</span></span>

<span data-ttu-id="a547a-146">`Get-Event` 傳回每個事件的 **PSEventArgs** 物件。</span><span class="sxs-lookup"><span data-stu-id="a547a-146">`Get-Event` returns a **PSEventArgs** object for each event.</span></span> <span data-ttu-id="a547a-147">如果要查看此物件的描述，請輸入 `Get-Help Get-Event -Full`，並參閱說明主題的＜附註＞一節。</span><span class="sxs-lookup"><span data-stu-id="a547a-147">To see a description of this object, type `Get-Help Get-Event -Full` and see the Notes section of the help topic.</span></span>

## <span data-ttu-id="a547a-148">注意</span><span class="sxs-lookup"><span data-stu-id="a547a-148">NOTES</span></span>

<span data-ttu-id="a547a-149">Linux 或 macOS 平臺上沒有可用的事件來源。</span><span class="sxs-lookup"><span data-stu-id="a547a-149">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="a547a-150">事件、事件訂閱與事件佇列僅存在目前工作階段中。</span><span class="sxs-lookup"><span data-stu-id="a547a-150">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="a547a-151">若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="a547a-151">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

<span data-ttu-id="a547a-152">Cmdlet 會傳回 `Get-Event` **PSEventArgs** 物件， ( **PSEventArgs** ) 具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a547a-152">The `Get-Event` cmdlet returns a **PSEventArgs** object ( **System.Management.Automation.PSEventArgs** ) with the following properties:</span></span>

- <span data-ttu-id="a547a-153">ComputerName。</span><span class="sxs-lookup"><span data-stu-id="a547a-153">ComputerName.</span></span> <span data-ttu-id="a547a-154">發生事件之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="a547a-154">The name of the computer on which the event occurred.</span></span> <span data-ttu-id="a547a-155">從遠端電腦轉送事件時，才會填入這個屬性值。</span><span class="sxs-lookup"><span data-stu-id="a547a-155">This property value is populated only when the event is forwarded from a remote computer.</span></span>

- <span data-ttu-id="a547a-156">RunspaceId。</span><span class="sxs-lookup"><span data-stu-id="a547a-156">RunspaceId.</span></span> <span data-ttu-id="a547a-157">可唯一識別發生事件之工作階段的 GUID。</span><span class="sxs-lookup"><span data-stu-id="a547a-157">A GUID that uniquely identifies the session in which the event occurred.</span></span> <span data-ttu-id="a547a-158">從遠端電腦轉送事件時，才會填入這個屬性值。</span><span class="sxs-lookup"><span data-stu-id="a547a-158">This property value is populated only when the event is forwarded from a remote computer.</span></span>

- <span data-ttu-id="a547a-159">EventIdentifier。</span><span class="sxs-lookup"><span data-stu-id="a547a-159">EventIdentifier.</span></span> <span data-ttu-id="a547a-160">可唯一識別目前工作階段中之事件通知的整數 (Int32)。</span><span class="sxs-lookup"><span data-stu-id="a547a-160">An integer (Int32) that uniquely identifies the event notification in the current session.</span></span>

- <span data-ttu-id="a547a-161">Sender。</span><span class="sxs-lookup"><span data-stu-id="a547a-161">Sender.</span></span> <span data-ttu-id="a547a-162">產生事件的物件。</span><span class="sxs-lookup"><span data-stu-id="a547a-162">The object that generated the event.</span></span> <span data-ttu-id="a547a-163">在 **Action** 參數的值中， `$Sender` 自動變數包含傳送者物件。</span><span class="sxs-lookup"><span data-stu-id="a547a-163">In the value of the **Action** parameter, the `$Sender` automatic variable contains the sender object.</span></span>

- <span data-ttu-id="a547a-164">SourceEventArgs。</span><span class="sxs-lookup"><span data-stu-id="a547a-164">SourceEventArgs.</span></span> <span data-ttu-id="a547a-165">衍生自 EventArgs 的第一個參數 (如果存在的話)。</span><span class="sxs-lookup"><span data-stu-id="a547a-165">The first parameter that derives from EventArgs, if it exists.</span></span> <span data-ttu-id="a547a-166">例如，在計時器經過的事件中，簽章的表單物件為 **timers.elapsedeventargs** e， **SourceEventArgs** 屬性會包含 **timers.elapsedeventargs** 。</span><span class="sxs-lookup"><span data-stu-id="a547a-166">For example, in a timer elapsed event in which the signature has the form Object sender, **Timers.ElapsedEventArgs** e, the **SourceEventArgs** property would contain the **Timers.ElapsedEventArgs**.</span></span> <span data-ttu-id="a547a-167">在 **Action** 參數的值中， `$EventArgs` 自動變數包含此值。</span><span class="sxs-lookup"><span data-stu-id="a547a-167">In the value of the **Action** parameter, the `$EventArgs` automatic variable contains this value.</span></span>

- <span data-ttu-id="a547a-168">SourceArgs。</span><span class="sxs-lookup"><span data-stu-id="a547a-168">SourceArgs.</span></span> <span data-ttu-id="a547a-169">原始事件簽章的所有參數。</span><span class="sxs-lookup"><span data-stu-id="a547a-169">All parameters of the original event signature.</span></span> <span data-ttu-id="a547a-170">若為標準事件簽章，表示傳送者 `$Args[0]` ，並 `$Args[1]` 代表 **SourceEventArgs** 。</span><span class="sxs-lookup"><span data-stu-id="a547a-170">For a standard event signature, `$Args[0]` represents the sender, and `$Args[1]` represents the **SourceEventArgs**.</span></span> <span data-ttu-id="a547a-171">在 **Action** 參數的值中， `$Args` 自動變數包含此值。</span><span class="sxs-lookup"><span data-stu-id="a547a-171">In the value of the **Action** parameter, the `$Args` automatic variable contains this value.</span></span>

- <span data-ttu-id="a547a-172">SourceIdentifier。</span><span class="sxs-lookup"><span data-stu-id="a547a-172">SourceIdentifier.</span></span> <span data-ttu-id="a547a-173">識別事件訂閱的字串。</span><span class="sxs-lookup"><span data-stu-id="a547a-173">A string that identifies the event subscription.</span></span> <span data-ttu-id="a547a-174">在 **Action** 參數的值中，自動變數的 **SourceIdentifier** 屬性會 `$Event` 包含此值。</span><span class="sxs-lookup"><span data-stu-id="a547a-174">In the value of the **Action** parameter, the **SourceIdentifier** property of the `$Event` automatic variable contains this value.</span></span>

- <span data-ttu-id="a547a-175">TimeGenerated。</span><span class="sxs-lookup"><span data-stu-id="a547a-175">TimeGenerated.</span></span> <span data-ttu-id="a547a-176">代表產生該事件時間的 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="a547a-176">A **DateTime** object that represents the time at which the event was generated.</span></span>
  <span data-ttu-id="a547a-177">在 **Action** 參數的值中，自動變數的 **TimeGenerated** 屬性會 `$Event` 包含此值。</span><span class="sxs-lookup"><span data-stu-id="a547a-177">In the value of the **Action** parameter, the **TimeGenerated** property of the `$Event` automatic variable contains this value.</span></span>

- <span data-ttu-id="a547a-178">MessageData.</span><span class="sxs-lookup"><span data-stu-id="a547a-178">MessageData.</span></span> <span data-ttu-id="a547a-179">與事件訂閱相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="a547a-179">Data associated with the event subscription.</span></span> <span data-ttu-id="a547a-180">使用者註冊事件時，會指定此資料。</span><span class="sxs-lookup"><span data-stu-id="a547a-180">Users specify this data when they register an event.</span></span> <span data-ttu-id="a547a-181">在 **Action** 參數的值中，自動變數的 **MessageData** 屬性會 `$Event` 包含此值。</span><span class="sxs-lookup"><span data-stu-id="a547a-181">In the value of the **Action** parameter, the **MessageData** property of the `$Event` automatic variable contains this value.</span></span>

## <span data-ttu-id="a547a-182">相關連結</span><span class="sxs-lookup"><span data-stu-id="a547a-182">RELATED LINKS</span></span>

[<span data-ttu-id="a547a-183">New-Event</span><span class="sxs-lookup"><span data-stu-id="a547a-183">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="a547a-184">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="a547a-184">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="a547a-185">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="a547a-185">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="a547a-186">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="a547a-186">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="a547a-187">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="a547a-187">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="a547a-188">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="a547a-188">Wait-Event</span></span>](Wait-Event.md)
