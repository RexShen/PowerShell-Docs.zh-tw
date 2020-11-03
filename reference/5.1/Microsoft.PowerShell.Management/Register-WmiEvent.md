---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 07/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/register-wmievent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-WmiEvent
ms.openlocfilehash: be29ce6376dea7686c0c063cc5528fbc7d840a9d
ms.sourcegitcommit: 41b072f0b6046d619b0e7f758982783fb648a3d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "93205811"
---
# <span data-ttu-id="3d2a5-103">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="3d2a5-103">Register-WmiEvent</span></span>

## <span data-ttu-id="3d2a5-104">概要</span><span class="sxs-lookup"><span data-stu-id="3d2a5-104">SYNOPSIS</span></span>
<span data-ttu-id="3d2a5-105">訂閱 Windows Management Instrumentation (WMI) 事件。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-105">Subscribes to a Windows Management Instrumentation (WMI) event.</span></span>

## <span data-ttu-id="3d2a5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3d2a5-106">SYNTAX</span></span>

### <span data-ttu-id="3d2a5-107">class (預設值)</span><span class="sxs-lookup"><span data-stu-id="3d2a5-107">class (Default)</span></span>

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Class] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="3d2a5-108">查詢</span><span class="sxs-lookup"><span data-stu-id="3d2a5-108">query</span></span>

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Query] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="3d2a5-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3d2a5-109">DESCRIPTION</span></span>

<span data-ttu-id="3d2a5-110">`Register-WmiEvent`Cmdlet 會訂閱本機電腦或遠端電腦上的 Windows Management Instrumentation (WMI) 事件。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-110">The `Register-WmiEvent` cmdlet subscribes to Windows Management Instrumentation (WMI) events on the local computer or on a remote computer.</span></span>

<span data-ttu-id="3d2a5-111">當訂閱的 WMI 事件被引發時，即使事件是發生在遠端電腦上，也會將事件新增到您本機工作階段內的事件佇列中。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-111">When the subscribed WMI event is raised, it is added to the event queue in your local session even if the event occurs on a remote computer.</span></span> <span data-ttu-id="3d2a5-112">若要取得事件佇列中的事件，請使用 `Get-Event` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-112">To get events in the event queue, use the `Get-Event` cmdlet.</span></span>

<span data-ttu-id="3d2a5-113">您可以使用的參數 `Register-WmiEvent` 來訂閱遠端電腦上的事件，並指定可協助您在佇列中識別事件的事件屬性值。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-113">You can use the parameters of `Register-WmiEvent` to subscribe to events on remote computers and to specify the property values of the events that can help you identify the event in the queue.</span></span> <span data-ttu-id="3d2a5-114">您也可以使用 **Action** 參數來指定引發訂閱事件時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-114">You can also use the **Action** parameter to specify actions to take when a subscribed event is raised.</span></span>

<span data-ttu-id="3d2a5-115">當您訂閱某個事件時，會將事件訂閱者新增到您的工作階段中。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-115">When you subscribe to an event, an event subscriber is added to your session.</span></span> <span data-ttu-id="3d2a5-116">若要取得會話中的事件訂閱者，請使用 `Get-EventSubscriber` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-116">To get the event subscribers in the session, use the `Get-EventSubscriber` cmdlet.</span></span> <span data-ttu-id="3d2a5-117">若要取消訂用帳戶，請使用 `Unregister-Event` Cmdlet，此 Cmdlet 會從會話刪除事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-117">To cancel the subscription, use the `Unregister-Event` cmdlet, which deletes the event subscriber from the session.</span></span>

<span data-ttu-id="3d2a5-118">新通用訊息模型 (CIM) Cmdlet （引進 Windows PowerShell 3.0）會執行與 WMI Cmdlet 相同的工作。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-118">New Common Information Model (CIM) cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="3d2a5-119">CIM Cmdlet 符合 WS-Management (WSMan) 標準和 CIM 標準，可讓 Cmdlet 使用相同的技術來管理執行 Windows 作業系統的電腦，以及執行其他作業系統的電腦。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-119">The CIM cmdlets comply with WS-Management (WSMan) standards and with the CIM standard, which enables the cmdlets to use the same techniques to manage computers that run the Windows operating system and those that run other operating systems.</span></span> <span data-ttu-id="3d2a5-120">請 `Register-WmiEvent` 考慮使用 [CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) Cmdlet，而不是使用。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-120">Instead of using `Register-WmiEvent`, consider using the [Register-CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) cmdlet.</span></span>

## <span data-ttu-id="3d2a5-121">範例</span><span class="sxs-lookup"><span data-stu-id="3d2a5-121">EXAMPLES</span></span>

### <span data-ttu-id="3d2a5-122">範例1：訂閱類別所產生的事件</span><span class="sxs-lookup"><span data-stu-id="3d2a5-122">Example 1: Subscribe to events generated by a class</span></span>

<span data-ttu-id="3d2a5-123">此命令會訂閱 **Win32_ProcessStartTrace** 類別所產生的事件。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-123">This command subscribes to the events generated by the **Win32_ProcessStartTrace** class.</span></span> <span data-ttu-id="3d2a5-124">此類別會在每次處理程序啟動時引發事件。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-124">This class raises an event whenever a process starts.</span></span>

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="3d2a5-125">範例2：訂閱進程的建立事件</span><span class="sxs-lookup"><span data-stu-id="3d2a5-125">Example 2: Subscribe to creation events for a process</span></span>

<span data-ttu-id="3d2a5-126">此命令使用查詢來訂閱 Win32_process 執行個體建立事件。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-126">This command uses a query to subscribe to Win32_process instance creation events.</span></span>

```powershell
$wmiParameters = @{
  Query = "select * from __instancecreationevent within 5 where targetinstance isa 'win32_process'"
  SourceIdentifier = "WMIProcess"
  MessageData = "Test 01"
  TimeOut = 500
}
Register-WmiEvent @wmiParameters
```

### <span data-ttu-id="3d2a5-127">範例3：使用動作來回應事件</span><span class="sxs-lookup"><span data-stu-id="3d2a5-127">Example 3: Use an action to respond to an event</span></span>

<span data-ttu-id="3d2a5-128">此範例示範如何使用動作來回應事件。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-128">This example shows how to use an action to respond to an event.</span></span> <span data-ttu-id="3d2a5-129">在此情況下，當處理常式啟動時， `Start-Process` 會將目前會話中的任何命令寫入至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-129">In this case, when a process starts, any `Start-Process` commands in the current session are written to an XML file.</span></span>

```powershell
$action = { Get-History | where { $_.commandline -like "*start-process*" } | export-cliXml "commandHistory.clixml" }
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

```Output
Id    Name            State      HasMoreData   Location  Command
--    ----            -----      -----------   --------  -------
1     ProcessStarted  NotStarted False                   get-history | where {...
```

<span data-ttu-id="3d2a5-130">當您使用 **Action** 參數時，會傳回 `Register-WmiEvent` 代表事件動作的背景工作。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-130">When you use the **Action** parameter, `Register-WmiEvent` returns a background job that represents the event action.</span></span> <span data-ttu-id="3d2a5-131">您可以使用 **Job** Cmdlet （例如 `Get-Job` 和 `Receive-Job` ）來管理事件工作。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-131">You can use the **Job** cmdlets, such as `Get-Job` and `Receive-Job`, to manage the event job.</span></span>

<span data-ttu-id="3d2a5-132">如需詳細資訊，請參閱 about_Jobs。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-132">For more information, see about_Jobs.</span></span>

### <span data-ttu-id="3d2a5-133">範例4：在遠端電腦上註冊事件</span><span class="sxs-lookup"><span data-stu-id="3d2a5-133">Example 4: Register for events on a remote computer</span></span>

<span data-ttu-id="3d2a5-134">此範例會登錄以取得 Server01 遠端電腦上的事件。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-134">This example registers for events on the Server01 remote computer.</span></span>

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "Start" -Computername Server01
Get-Event -SourceIdentifier "Start"
```

<span data-ttu-id="3d2a5-135">WMI 會將事件傳回本機電腦，並將它們儲存在目前工作階段內的事件佇列中。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-135">WMI returns the events to the local computer and stores them in the event queue in the current session.</span></span> <span data-ttu-id="3d2a5-136">若要抓取事件，請執行本機 `Get-Event` 命令。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-136">To retrieve the events, run a local `Get-Event` command.</span></span>

## <span data-ttu-id="3d2a5-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3d2a5-137">PARAMETERS</span></span>

### <span data-ttu-id="3d2a5-138">-Action</span><span class="sxs-lookup"><span data-stu-id="3d2a5-138">-Action</span></span>

<span data-ttu-id="3d2a5-139">指定處理事件的命令。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-139">Specifies commands that handle the events.</span></span> <span data-ttu-id="3d2a5-140">**Action** 參數中的命令會在引發事件時執行，而不會將事件傳送到事件佇列。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-140">The commands in the **Action** parameter run when an event is raised instead of sending the event to the event queue.</span></span> <span data-ttu-id="3d2a5-141">以大括弧括住命令 (`{}`) 來建立腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-141">Enclose the commands in braces (`{}`) to create a script block.</span></span>

<span data-ttu-id="3d2a5-142">**Action** 的值可以包括 `$Event` 、 `$EventSubscriber` 、 `$Sender` 、 `$EventArgs` 和 `$Args` 自動變數，這些變數會將事件的相關資訊提供給 **Action** 腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-142">The value of **Action** can include the `$Event`, `$EventSubscriber`, `$Sender`, `$EventArgs`, and `$Args` automatic variables, which provide information about the event to the **Action** script block.</span></span> <span data-ttu-id="3d2a5-143">如需詳細資訊，請參閱 about_Automatic_Variables。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-143">For more information, see about_Automatic_Variables.</span></span>

<span data-ttu-id="3d2a5-144">當您指定動作時，會傳回 `Register-WmiEvent` 代表該動作的事件工作物件。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-144">When you specify an action, `Register-WmiEvent` returns an event job object that represents that action.</span></span> <span data-ttu-id="3d2a5-145">您可以使用包含 **作業** 名詞 ( **工作 Cmdlet)** 來管理事件工作的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-145">You can use the cmdlets that contain the **Job** noun (the **Job** cmdlets) to manage the event job.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2a5-146">-Class</span><span class="sxs-lookup"><span data-stu-id="3d2a5-146">-Class</span></span>

<span data-ttu-id="3d2a5-147">指定您要訂閱的事件。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-147">Specifies the event to which you are subscribing.</span></span> <span data-ttu-id="3d2a5-148">請輸入產生事件的 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-148">Enter the WMI class that generates the events.</span></span> <span data-ttu-id="3d2a5-149">每個命令中都需要 **類別** 或 **查詢** 參數。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-149">A **Class** or **Query** parameter is required in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2a5-150">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3d2a5-150">-ComputerName</span></span>

<span data-ttu-id="3d2a5-151">指定命令執行所在的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-151">Specifies the name of the computer on which the command runs.</span></span> <span data-ttu-id="3d2a5-152">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-152">The default is the local computer.</span></span>

<span data-ttu-id="3d2a5-153">輸入電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-153">Type the NetBIOS name, an IP address, or a fully qualified domain name of the computer.</span></span> <span data-ttu-id="3d2a5-154">若要指定本機電腦，請輸入電腦名稱稱、點 (`.`) 或 localhost。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-154">To specify the local computer, type the computer name, a dot (`.`), or localhost.</span></span>

<span data-ttu-id="3d2a5-155">此參數不必依賴 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-155">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="3d2a5-156">即使您的電腦未設定為執行遠端命令，您仍然可以使用 **ComputerName** 參數。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-156">You can use the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2a5-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="3d2a5-157">-Credential</span></span>

<span data-ttu-id="3d2a5-158">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-158">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="3d2a5-159">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-159">The default is the current user.</span></span>

<span data-ttu-id="3d2a5-160">輸入使用者名稱（例如 User01 或 Domain01\User01），或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-160">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="3d2a5-161">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-161">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2a5-162">-Forward</span><span class="sxs-lookup"><span data-stu-id="3d2a5-162">-Forward</span></span>

<span data-ttu-id="3d2a5-163">指出此 Cmdlet 會將此訂閱的事件傳送到本機電腦上的會話。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-163">Indicates that this cmdlet sends events for this subscription to the session on the local computer.</span></span>
<span data-ttu-id="3d2a5-164">當您要訂閱遠端電腦上或遠端工作階段中的事件時，請使用此參數。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-164">Use this parameter when you are registering for events on a remote computer or in a remote session.</span></span>

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

### <span data-ttu-id="3d2a5-165">-MaxTriggerCount</span><span class="sxs-lookup"><span data-stu-id="3d2a5-165">-MaxTriggerCount</span></span>

<span data-ttu-id="3d2a5-166">指定最大觸發程式計數。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-166">Specifies the maximum trigger count.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2a5-167">-MessageData</span><span class="sxs-lookup"><span data-stu-id="3d2a5-167">-MessageData</span></span>

<span data-ttu-id="3d2a5-168">指定要與這個事件訂閱建立關聯的任何其他資料。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-168">Specifies any additional data to be associated with this event subscription.</span></span> <span data-ttu-id="3d2a5-169">此參數的值會出現在與此訂用帳戶相關聯之所有事件的 **MessageData** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-169">The value of this parameter appears in the **MessageData** property of all events associated with this subscription.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2a5-170">-Namespace</span><span class="sxs-lookup"><span data-stu-id="3d2a5-170">-Namespace</span></span>

<span data-ttu-id="3d2a5-171">指定 WMI 類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-171">Specifies the namespace of the WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2a5-172">-Query</span><span class="sxs-lookup"><span data-stu-id="3d2a5-172">-Query</span></span>

<span data-ttu-id="3d2a5-173">指定 WMI 查詢語言 (WQL) 的查詢，以識別 WMI 事件類別，例如： `select * from __InstanceDeletionEvent` 。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-173">Specifies a query in WMI Query Language (WQL) that identifies the WMI event class, such as: `select * from __InstanceDeletionEvent`.</span></span>

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2a5-174">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="3d2a5-174">-SourceIdentifier</span></span>

<span data-ttu-id="3d2a5-175">指定您為訂閱選取的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-175">Specifies a name that you select for the subscription.</span></span> <span data-ttu-id="3d2a5-176">您所選取的名稱在目前的工作階段中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-176">The name that you select must be unique in the current session.</span></span> <span data-ttu-id="3d2a5-177">預設值是 Windows PowerShell 所指派的 GUID。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-177">The default value is the GUID that Windows PowerShell assigns.</span></span>

<span data-ttu-id="3d2a5-178">這個參數的值會出現在訂閱者物件以及與此訂閱相關聯之所有事件物件的 **SourceIdentifier** 屬性值中。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-178">The value of this parameter appears in the value of the **SourceIdentifier** property of the subscriber object and of all event objects associated with this subscription.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2a5-179">-SupportEvent</span><span class="sxs-lookup"><span data-stu-id="3d2a5-179">-SupportEvent</span></span>

<span data-ttu-id="3d2a5-180">指出此 Cmdlet 會隱藏事件訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-180">Indicates that this cmdlet hides the event subscription.</span></span> <span data-ttu-id="3d2a5-181">當目前的訂閱是更複雜事件註冊機制的一部分，而且不應該被獨立探索時，請使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-181">Use this parameter when the current subscription is part of a more complex event registration mechanism and it should not be discovered independently.</span></span>

<span data-ttu-id="3d2a5-182">若要查看或取消使用 **SupportEvent** 參數建立的訂閱，請指定和 Cmdlet 的 **Force** 參數 `Get-EventSubscriber` `Unregister-Event` 。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-182">To view or cancel a subscription that was created by using the **SupportEvent** parameter, specify the **Force** parameter of the `Get-EventSubscriber` and `Unregister-Event` cmdlets.</span></span>

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

### <span data-ttu-id="3d2a5-183">-Timeout</span><span class="sxs-lookup"><span data-stu-id="3d2a5-183">-Timeout</span></span>

<span data-ttu-id="3d2a5-184">指定 Windows PowerShell 等候此命令完成的時間長度。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-184">Specifies how long Windows PowerShell waits for this command to finish.</span></span>

<span data-ttu-id="3d2a5-185">預設值為 0 (零) 表示沒有逾時，這會使 Windows PowerShell 無限期等待。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-185">The default value, 0 (zero), means that there is no time-out, and it causes Windows PowerShell to wait indefinitely.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: TimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2a5-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d2a5-186">CommonParameters</span></span>

<span data-ttu-id="3d2a5-187">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d2a5-188">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3d2a5-189">輸入</span><span class="sxs-lookup"><span data-stu-id="3d2a5-189">INPUTS</span></span>

### <span data-ttu-id="3d2a5-190">無</span><span class="sxs-lookup"><span data-stu-id="3d2a5-190">None</span></span>

<span data-ttu-id="3d2a5-191">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-191">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="3d2a5-192">輸出</span><span class="sxs-lookup"><span data-stu-id="3d2a5-192">OUTPUTS</span></span>

### <span data-ttu-id="3d2a5-193">無</span><span class="sxs-lookup"><span data-stu-id="3d2a5-193">None</span></span>

<span data-ttu-id="3d2a5-194">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-194">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3d2a5-195">注意</span><span class="sxs-lookup"><span data-stu-id="3d2a5-195">NOTES</span></span>

<span data-ttu-id="3d2a5-196">若要在 Windows Vista 或更新版本的 Windows 作業系統中使用此 Cmdlet，請使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-196">To use this cmdlet in Windows Vista or a later version of the Windows operating system, start Windows PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="3d2a5-197">事件、事件訂閱與事件佇列僅存在目前工作階段中。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-197">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="3d2a5-198">若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="3d2a5-198">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="3d2a5-199">相關連結</span><span class="sxs-lookup"><span data-stu-id="3d2a5-199">RELATED LINKS</span></span>
