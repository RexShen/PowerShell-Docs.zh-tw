---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowexecutionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowExecutionOption
ms.openlocfilehash: db5d19396f555a41ad14552823c57f3b11c79321
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205431"
---
# <span data-ttu-id="56d9a-103">New-PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="56d9a-103">New-PSWorkflowExecutionOption</span></span>

## <span data-ttu-id="56d9a-104">概要</span><span class="sxs-lookup"><span data-stu-id="56d9a-104">SYNOPSIS</span></span>

<span data-ttu-id="56d9a-105">建立包含工作流程工作階段之工作階段設定選項的物件。</span><span class="sxs-lookup"><span data-stu-id="56d9a-105">Creates an object that contains session configuration options for workflow sessions.</span></span>

## <span data-ttu-id="56d9a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="56d9a-106">SYNTAX</span></span>

```
New-PSWorkflowExecutionOption [-PersistencePath <String>] [-MaxPersistenceStoreSizeGB <Int64>]
 [-PersistWithEncryption] [-MaxRunningWorkflows <Int32>] [-AllowedActivity <String[]>]
 [-OutOfProcessActivity <String[]>] [-EnableValidation] [-MaxDisconnectedSessions <Int32>]
 [-MaxConnectedSessions <Int32>] [-MaxSessionsPerWorkflow <Int32>] [-MaxSessionsPerRemoteNode <Int32>]
 [-MaxActivityProcesses <Int32>] [-ActivityProcessIdleTimeoutSec <Int32>]
 [-RemoteNodeSessionIdleTimeoutSec <Int32>] [-SessionThrottleLimit <Int32>]
 [-WorkflowShutdownTimeoutMSec <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="56d9a-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="56d9a-107">DESCRIPTION</span></span>

<span data-ttu-id="56d9a-108">此 `New-PSWorkflowExecutionOption` Cmdlet 會建立一個物件，其中包含工作流程會話設定的 advanced 選項，也就是設計來執行 Windows PowerShell 工作流程工作流程的會話設定。</span><span class="sxs-lookup"><span data-stu-id="56d9a-108">The `New-PSWorkflowExecutionOption` cmdlet creates an object that contains advanced options for workflow session configurations, that is session configurations designed to run Windows PowerShell Workflow workflows.</span></span>

<span data-ttu-id="56d9a-109">您可以使用 **new-psworkflowexecutionoption** 物件，它會 `New-PSWorkflowExecutionOption` 產生做為建立或變更會話設定之 Cmdlet 的 **SessionTypeOption** 參數值，例如 `Register-PSSessionConfiguration` 和 `Set-PSSessionConfiguration` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="56d9a-109">You can use the **PSWorkflowExecutionOption** object that `New-PSWorkflowExecutionOption` generates as the value of the **SessionTypeOption** parameter of cmdlets that create or change a session configuration, such as the `Register-PSSessionConfiguration` and `Set-PSSessionConfiguration` cmdlets.</span></span>

<span data-ttu-id="56d9a-110">Cmdlet 的每個參數都 `New-PSWorkflowExecutionOption` 代表 Cmdlet 所傳回之工作流程會話設定選項物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="56d9a-110">Each parameter of the `New-PSWorkflowExecutionOption` cmdlet represents a property of the workflow session configuration option object that the cmdlet returns.</span></span> <span data-ttu-id="56d9a-111">若省略參數，Cmdlet 會使用屬性的預設值來建立物件。</span><span class="sxs-lookup"><span data-stu-id="56d9a-111">If you omit a parameter, the cmdlet creates the object with a default value for the property.</span></span>

<span data-ttu-id="56d9a-112">此 `New-PSWorkflowExecutionOption` Cmdlet 是 Windows PowerShell 工作流程功能的一部分。</span><span class="sxs-lookup"><span data-stu-id="56d9a-112">The `New-PSWorkflowExecutionOption` cmdlet is part of the Windows PowerShell Workflow feature.</span></span>

<span data-ttu-id="56d9a-113">您也可以新增工作流程一般參數到此命令。</span><span class="sxs-lookup"><span data-stu-id="56d9a-113">You can also add workflow common parameters to this command.</span></span> <span data-ttu-id="56d9a-114">如需工作流程一般參數的詳細資訊，請參閱 [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="56d9a-114">For more information about workflow common parameters, see [about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md).</span></span>

<span data-ttu-id="56d9a-115">此 Cmdlet 是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="56d9a-115">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="56d9a-116">範例</span><span class="sxs-lookup"><span data-stu-id="56d9a-116">EXAMPLES</span></span>

### <span data-ttu-id="56d9a-117">範例1：建立工作流程選項物件</span><span class="sxs-lookup"><span data-stu-id="56d9a-117">Example 1: Create a Workflow Options Object</span></span>

```powershell
New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
```

```Output
SessionThrottleLimit                       : 100
PersistencePath                            : C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell\WF\PS
MaxPersistenceStoreSizeGB                  : 10
PersistWithEncryption                      : False
MaxRunningWorkflows                        : 30
AllowedActivity                            : {PSDefaultActivities}
OutOfProcessActivity                       : {InlineScript}
EnableValidation                           : True
MaxDisconnectedSessions                    : 200
MaxConnectedSessions                       : 100
MaxSessionsPerWorkflow                     : 10
MaxSessionsPerRemoteNode                   : 5
MaxActivityProcesses                       : 5
ActivityProcessIdleTimeoutSec              : 60
RemoteNodeSessionIdleTimeoutSec            : 60
WorkflowShutdownTimeoutMSec                : 500
```

<span data-ttu-id="56d9a-118">此命令會使用 `New-PSWorkflowExecutionOption` Cmdlet 將 **MaxSessionsPerWorkflow** 值增加為10，並將 **MaxDisconnectedSessions** 值減少為200。</span><span class="sxs-lookup"><span data-stu-id="56d9a-118">This command uses the `New-PSWorkflowExecutionOption` cmdlet to increase the **MaxSessionsPerWorkflow** value to 10 and decrease the **MaxDisconnectedSessions** value to 200.</span></span>

<span data-ttu-id="56d9a-119">輸出會顯示 Cmdlet 傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="56d9a-119">The output shows the object that the cmdlet returns.</span></span>

### <span data-ttu-id="56d9a-120">範例2：使用工作流程選項物件</span><span class="sxs-lookup"><span data-stu-id="56d9a-120">Example 2: Using a Workflow Options Object</span></span>

```powershell
# Create a Workflow Options object and save it in a variable
$wo = New-PSWorkflowExecutionOption -MaxSessionsPerWorkflow 10 -MaxDisconnectedSessions 200
# Create the ITWorkflow session configuration
Register-PSSessionConfiguration -Name ITWorkflows -SessionTypeOption $wo -Force
```

```Output
    WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=ITWorkflows}                  ITWorkflows
```

```powershell
Get-PSSessionConfiguration ITWorkflows | Format-List -Property *
```

```Output
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITWorkflows
MaxConcurrentCommandsPerShell : 1000
allowedactivity               : PSDefaultActivities
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
maxsessionsperworkflow        : 10
lang                          : en-US
sessionconfigurationdata      : <SessionConfigurationData>
                                    <Param Name='PrivateData'>
                                        <PrivateData>
                                            <ParamName='enablevalidation' Value='True'/>
                                            <Param Name='allowedactivity'Value='PSDefaultActivities' />
                                            <Param Name='outofprocessactivity' Value='InlineScript'/>
                                            <Param Name='maxdisconnectedsessions' Value='200' />
                                            <ParamName='maxsessionsperworkflow' Value='10'/>
                                        </PrivateData>
                                    </Param>
                                </SessionConfigurationData>
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 25
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
outofprocessactivity          : InlineScript
SDKVersion                    : 2
Name                          : ITWorkflows
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
enablevalidation              : True
Enabled                       : True
maxdisconnectedsessions       : 200
MaxShellsPerUser              : 25
Permission                    :
```

<span data-ttu-id="56d9a-121">前兩個命令會建立新的會話設定物件，並加以註冊。</span><span class="sxs-lookup"><span data-stu-id="56d9a-121">The first two commands create a new session configuration object and registers it.</span></span>

<span data-ttu-id="56d9a-122">第三個命令會使用 `Get-PSSessionConfiguration` Cmdlet 來取得 ITWorkflows 會話設定，並使用 `Format-List` 來顯示清單中會話設定的所有屬性。輸出會顯示會話設定中的工作流程選項。</span><span class="sxs-lookup"><span data-stu-id="56d9a-122">The third command uses the `Get-PSSessionConfiguration` cmdlet to the get the ITWorkflows session configuration and the `Format-List` to display all properties of the session configuration in a list.The output shows that the workflow options in the session configuration.</span></span> <span data-ttu-id="56d9a-123">特別是，工作階段設定具有值為 10 的 **MaxSessionsPerWorkflow** 屬性，以及值為 200 的 **MaxDisconnectedSessions** 屬性。</span><span class="sxs-lookup"><span data-stu-id="56d9a-123">Specifically, the session configuration has a **MaxSessionsPerWorkflow** property with a value of 10 and a **MaxDisconnectedSessions** property with a value of 200.</span></span>

## <span data-ttu-id="56d9a-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="56d9a-124">PARAMETERS</span></span>

### <span data-ttu-id="56d9a-125">-ActivityProcessIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="56d9a-125">-ActivityProcessIdleTimeoutSec</span></span>

<span data-ttu-id="56d9a-126">指定當處理程序成為閒置之後，每個活動主機處理程序的保留時間。</span><span class="sxs-lookup"><span data-stu-id="56d9a-126">Determines how long each activity host process is maintained after the process becomes idle.</span></span> <span data-ttu-id="56d9a-127">當間隔時間過期時，處理程序就會關閉。</span><span class="sxs-lookup"><span data-stu-id="56d9a-127">When the interval expires, the process closes.</span></span>

<span data-ttu-id="56d9a-128">輸入以秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="56d9a-128">Enter a value in seconds.</span></span> <span data-ttu-id="56d9a-129">預設值為 60。</span><span class="sxs-lookup"><span data-stu-id="56d9a-129">The default value is 60.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-130">-AllowedActivity</span><span class="sxs-lookup"><span data-stu-id="56d9a-130">-AllowedActivity</span></span>

<span data-ttu-id="56d9a-131">指定允許在工作階段中執行的活動。</span><span class="sxs-lookup"><span data-stu-id="56d9a-131">Specifies the activities that are permitted to run in the session.</span></span>

<span data-ttu-id="56d9a-132">輸入符合命名空間的活動名稱，例如 `Microsoft.Powershell.HyperV.Activities.*` 。</span><span class="sxs-lookup"><span data-stu-id="56d9a-132">Enter namespace-qualified activity names, such as `Microsoft.Powershell.HyperV.Activities.*`.</span></span>
<span data-ttu-id="56d9a-133">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="56d9a-133">Wildcard characters are supported.</span></span> <span data-ttu-id="56d9a-134">預設值 **PSDefaultActivities** 包含內建的 Windows Workflow Foundation 活動與代表 Windows PowerShell Core Cmdlet 的活動。</span><span class="sxs-lookup"><span data-stu-id="56d9a-134">The default value, **PSDefaultActivities** , includes the built-in Windows Workflow Foundation activities and the activities that represent the Windows PowerShell Core cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: PSDefaultActivities
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-135">-EnableValidation</span><span class="sxs-lookup"><span data-stu-id="56d9a-135">-EnableValidation</span></span>

<span data-ttu-id="56d9a-136">確認工作階段中的所有工作流程活動都已包含在允許活動清單中。</span><span class="sxs-lookup"><span data-stu-id="56d9a-136">Verifies that all workflow activities in the session are included in the allowed activities list.</span></span>

<span data-ttu-id="56d9a-137">預設值為 true。</span><span class="sxs-lookup"><span data-stu-id="56d9a-137">The default value is True.</span></span> <span data-ttu-id="56d9a-138">若要停用驗證，請使用下列命令格式： `-EnableValidation:$false` 。</span><span class="sxs-lookup"><span data-stu-id="56d9a-138">To disable validation, use the following command format: `-EnableValidation:$false`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-139">-MaxActivityProcesses</span><span class="sxs-lookup"><span data-stu-id="56d9a-139">-MaxActivityProcesses</span></span>

<span data-ttu-id="56d9a-140">指定可在工作階段中建立以支援工作流程活動的處理程序數目上限。</span><span class="sxs-lookup"><span data-stu-id="56d9a-140">Specifies the maximum number of processes that can be created in the session to support workflow activities.</span></span> <span data-ttu-id="56d9a-141">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="56d9a-141">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-142">-MaxConnectedSessions</span><span class="sxs-lookup"><span data-stu-id="56d9a-142">-MaxConnectedSessions</span></span>

<span data-ttu-id="56d9a-143">指定處於操作狀態的遠端工作階段數目上限。</span><span class="sxs-lookup"><span data-stu-id="56d9a-143">Specifies the maximum number of remote sessions that are in an operational state.</span></span> <span data-ttu-id="56d9a-144">此配額會套用到連線到所有遠端節點 (目標電腦) 的工作階段。</span><span class="sxs-lookup"><span data-stu-id="56d9a-144">This quota is applied to sessions connected to all remote nodes (target computers).</span></span> <span data-ttu-id="56d9a-145">預設值是 100。</span><span class="sxs-lookup"><span data-stu-id="56d9a-145">The default value is 100.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-146">-MaxDisconnectedSessions</span><span class="sxs-lookup"><span data-stu-id="56d9a-146">-MaxDisconnectedSessions</span></span>

<span data-ttu-id="56d9a-147">指定處於中斷連線狀態的遠端工作階段數目上限。</span><span class="sxs-lookup"><span data-stu-id="56d9a-147">Specifies the maximum number of remote sessions that are in a disconnected state.</span></span> <span data-ttu-id="56d9a-148">此配額會套用到連線到所有遠端節點 (目標電腦) 的工作階段。</span><span class="sxs-lookup"><span data-stu-id="56d9a-148">This quota is applied to sessions connected to all remote nodes (target computers).</span></span> <span data-ttu-id="56d9a-149">預設值為 1000。</span><span class="sxs-lookup"><span data-stu-id="56d9a-149">The default value is 1000.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1000
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-150">-MaxPersistenceStoreSizeGB</span><span class="sxs-lookup"><span data-stu-id="56d9a-150">-MaxPersistenceStoreSizeGB</span></span>

<span data-ttu-id="56d9a-151">指定配置給在工作階段中執行之工作流程的持續性儲存區大小上限 (單位為 GB)。</span><span class="sxs-lookup"><span data-stu-id="56d9a-151">Specifies the maximum size, in gigabytes, of the persistence store allocated to workflows that run in the session.</span></span> <span data-ttu-id="56d9a-152">超過該大小時，會擴充持續性儲存區以儲存所有持續性資料，但會顯示警告並寫入一個訊息到工作流程事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="56d9a-152">When the size is exceeded, the persistence store is expanded to save all persisted data, but a warning is displayed and a message is written to the workflow event log.</span></span> <span data-ttu-id="56d9a-153">預設值是 10。</span><span class="sxs-lookup"><span data-stu-id="56d9a-153">The default value is 10.</span></span>

<span data-ttu-id="56d9a-154">持續性儲存區包含所有工作流程工作的資料。</span><span class="sxs-lookup"><span data-stu-id="56d9a-154">The persistence store contains data for all workflow jobs.</span></span> <span data-ttu-id="56d9a-155">儲存資料的能力可讓工作繼續執行，而不會遺失狀態。</span><span class="sxs-lookup"><span data-stu-id="56d9a-155">The ability to store data allows the jobs to resume without losing state.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-156">-MaxRunningWorkflows</span><span class="sxs-lookup"><span data-stu-id="56d9a-156">-MaxRunningWorkflows</span></span>

<span data-ttu-id="56d9a-157">指定可以同時在工作階段中執行的工作流程數目上限。</span><span class="sxs-lookup"><span data-stu-id="56d9a-157">Specifies that maximum number of workflows that can run in the session concurrently.</span></span>
<span data-ttu-id="56d9a-158">預設值是 30。</span><span class="sxs-lookup"><span data-stu-id="56d9a-158">The default value is 30.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 30
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-159">-MaxSessionsPerRemoteNode</span><span class="sxs-lookup"><span data-stu-id="56d9a-159">-MaxSessionsPerRemoteNode</span></span>

<span data-ttu-id="56d9a-160">指定可以連線到每個遠端節點 (目標電腦) 的工作階段數目上限。</span><span class="sxs-lookup"><span data-stu-id="56d9a-160">Specifies the maximum number of sessions that can be connected to each remote node (target computer).</span></span> <span data-ttu-id="56d9a-161">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="56d9a-161">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-162">-MaxSessionsPerWorkflow</span><span class="sxs-lookup"><span data-stu-id="56d9a-162">-MaxSessionsPerWorkflow</span></span>

<span data-ttu-id="56d9a-163">指定可以建立以支援每個工作流程的工作階段數目上限。</span><span class="sxs-lookup"><span data-stu-id="56d9a-163">Specifies the maximum number of session that can be created to support each workflow.</span></span> <span data-ttu-id="56d9a-164">預設值為 5。</span><span class="sxs-lookup"><span data-stu-id="56d9a-164">The default value is 5.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-165">-OutOfProcessActivity</span><span class="sxs-lookup"><span data-stu-id="56d9a-165">-OutOfProcessActivity</span></span>

<span data-ttu-id="56d9a-166">決定哪些允許的活動 (由 **AllowedActivities** 參數指定) 可跨處理序執行。</span><span class="sxs-lookup"><span data-stu-id="56d9a-166">Determines which allowed activities (specified by the **AllowedActivities** parameter) run out-of-process.</span></span> <span data-ttu-id="56d9a-167">預設值為 **InlineScript** 。</span><span class="sxs-lookup"><span data-stu-id="56d9a-167">The default value is **InlineScript** .</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineScript
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-168">-PersistencePath</span><span class="sxs-lookup"><span data-stu-id="56d9a-168">-PersistencePath</span></span>

<span data-ttu-id="56d9a-169">指定用來儲存工作流程狀態與資料的磁碟位置。</span><span class="sxs-lookup"><span data-stu-id="56d9a-169">Specifies the location on disk where workflow state and data are stored.</span></span> <span data-ttu-id="56d9a-170">儲存工作流程狀態與資料可讓工作流程暫停並繼續，以及在發生中斷或網路故障時復原。</span><span class="sxs-lookup"><span data-stu-id="56d9a-170">Storing the workflow state and data allows workflows to be suspended and resumed, and to recover from interruptions and network failures.</span></span>

<span data-ttu-id="56d9a-171">預設值是 `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`。</span><span class="sxs-lookup"><span data-stu-id="56d9a-171">The default value is `$env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-172">-PersistWithEncryption</span><span class="sxs-lookup"><span data-stu-id="56d9a-172">-PersistWithEncryption</span></span>

<span data-ttu-id="56d9a-173">表示工作流程會將持續性存放區中的資料加密。</span><span class="sxs-lookup"><span data-stu-id="56d9a-173">Indicates that the workflow encrypts the data in the persistence store.</span></span> <span data-ttu-id="56d9a-174">將持續性資料儲存在網路共用時，請考慮使用此功能。</span><span class="sxs-lookup"><span data-stu-id="56d9a-174">Consider using this feature when storing persistence data in a network share.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: $env:LocalAppData\Microsoft\Windows\PowerShell\WF\PS
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-175">-RemoteNodeSessionIdleTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="56d9a-175">-RemoteNodeSessionIdleTimeoutSec</span></span>

<span data-ttu-id="56d9a-176">指定當連線到遠端節點 (目標電腦) 的工作階段成為閒置時，應該保留該工作階段多久。</span><span class="sxs-lookup"><span data-stu-id="56d9a-176">Specifies how long a session that is connected to a remote node (target computer) is maintained if it is idle.</span></span>

<span data-ttu-id="56d9a-177">輸入以秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="56d9a-177">Enter a value in seconds.</span></span> <span data-ttu-id="56d9a-178">預設值為 60。</span><span class="sxs-lookup"><span data-stu-id="56d9a-178">The default value is 60.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-179">-SessionThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="56d9a-179">-SessionThrottleLimit</span></span>

<span data-ttu-id="56d9a-180">指定要建立多少操作以支援在工作階段中啟動的所有工作流程。</span><span class="sxs-lookup"><span data-stu-id="56d9a-180">Specifies how many operations are created to support all workflows started in the session.</span></span> <span data-ttu-id="56d9a-181">預設值是 100。</span><span class="sxs-lookup"><span data-stu-id="56d9a-181">The default value is 100.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-182">-WorkflowShutdownTimeoutMSec</span><span class="sxs-lookup"><span data-stu-id="56d9a-182">-WorkflowShutdownTimeoutMSec</span></span>

<span data-ttu-id="56d9a-183">指定強制暫停工作階段中的所有工作流程之後，應該保留該工作階段多久。</span><span class="sxs-lookup"><span data-stu-id="56d9a-183">Specifies how long the session is maintained after all workflows in the session are forcibly suspended.</span></span> <span data-ttu-id="56d9a-184">逾時期間經過之後，Windows PowerShell 會關閉該工作階段 (即使並非所有工作流程都已暫停)。</span><span class="sxs-lookup"><span data-stu-id="56d9a-184">When the timeout expires, Windows PowerShell closes the session, even if all workflows are not yet suspended.</span></span>

<span data-ttu-id="56d9a-185">輸入以毫秒為單位的值。</span><span class="sxs-lookup"><span data-stu-id="56d9a-185">Enter a value in milliseconds.</span></span>
<span data-ttu-id="56d9a-186">預設值為 500。</span><span class="sxs-lookup"><span data-stu-id="56d9a-186">The default value is 500.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 500
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56d9a-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="56d9a-187">CommonParameters</span></span>

<span data-ttu-id="56d9a-188">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="56d9a-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="56d9a-189">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="56d9a-189">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="56d9a-190">輸入</span><span class="sxs-lookup"><span data-stu-id="56d9a-190">INPUTS</span></span>

### <span data-ttu-id="56d9a-191">無</span><span class="sxs-lookup"><span data-stu-id="56d9a-191">None</span></span>

<span data-ttu-id="56d9a-192">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="56d9a-192">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="56d9a-193">輸出</span><span class="sxs-lookup"><span data-stu-id="56d9a-193">OUTPUTS</span></span>

### <span data-ttu-id="56d9a-194">New-psworkflowexecutionoption。</span><span class="sxs-lookup"><span data-stu-id="56d9a-194">Microsoft.PowerShell.Commands.PSWorkflowExecutionOption</span></span>

## <span data-ttu-id="56d9a-195">注意</span><span class="sxs-lookup"><span data-stu-id="56d9a-195">NOTES</span></span>

<span data-ttu-id="56d9a-196">超過此選項所設定的最大值時，用來在工作階段中建立另一個執行個體的命令會失敗，除非在參數描述中另有設定。</span><span class="sxs-lookup"><span data-stu-id="56d9a-196">When the maximum value set by an option is exceeded, the command to create another instance in the session fails, unless noted in the parameter description.</span></span> <span data-ttu-id="56d9a-197">例如，若 **MaxConnectedSessions** 的值是 100。</span><span class="sxs-lookup"><span data-stu-id="56d9a-197">For example, if the value of **MaxConnectedSessions** is 100.</span></span> <span data-ttu-id="56d9a-198">用來建立 101st 工作階段以連線到遠端節點 (目標電腦) 的命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="56d9a-198">The command to create the 101st session to a remote node (target computer) fails.</span></span>

<span data-ttu-id="56d9a-199">工作階段設定物件的屬性取決於工作階段設定所設定的選項，以及這些選項的值。</span><span class="sxs-lookup"><span data-stu-id="56d9a-199">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="56d9a-200">此外，使用工作階段設定檔的工作階段設定會有額外的屬性。</span><span class="sxs-lookup"><span data-stu-id="56d9a-200">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="56d9a-201">特別是，包含 **PSWorkflowExecutionOptions** 物件的工作階段設定屬性視工作流程選項值而異。</span><span class="sxs-lookup"><span data-stu-id="56d9a-201">In particular, the properties of session configurations that include a **PSWorkflowExecutionOptions** object vary based on the workflow option values.</span></span> <span data-ttu-id="56d9a-202">例如，若工作階段設定包含會為 **SessionThrottleLimit** 屬性設定非預設值的 **PSWorkflowExecutionOptions** 物件，則該工作階段設定具有 **SessionThrottleLimit** 屬性。</span><span class="sxs-lookup"><span data-stu-id="56d9a-202">For example, if the session configuration includes a **PSWorkflowExecutionOptions** object that sets a non-default value for the **SessionThrottleLimit** property, the session configuration has a **SessionThrottleLimit** property.</span></span> <span data-ttu-id="56d9a-203">否則，則沒有。</span><span class="sxs-lookup"><span data-stu-id="56d9a-203">Otherwise, it does not.</span></span>

## <span data-ttu-id="56d9a-204">相關連結</span><span class="sxs-lookup"><span data-stu-id="56d9a-204">RELATED LINKS</span></span>

[<span data-ttu-id="56d9a-205">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="56d9a-205">New-PSWorkflowSession</span></span>](New-PSWorkflowSession.md)

[<span data-ttu-id="56d9a-206">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="56d9a-206">about_Workflows</span></span>](../PSWorkflow/About/about_Workflows.md)

[<span data-ttu-id="56d9a-207">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="56d9a-207">about_WorkflowCommonParameters</span></span>](About/about_WorkflowCommonParameters.md)
