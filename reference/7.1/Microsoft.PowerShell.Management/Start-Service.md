---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Service
ms.openlocfilehash: 71b9ac57b2ab27e26f3a7454662f231b6e1dd764
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204371"
---
# <span data-ttu-id="c54fb-103">Start-Service</span><span class="sxs-lookup"><span data-stu-id="c54fb-103">Start-Service</span></span>

## <span data-ttu-id="c54fb-104">概要</span><span class="sxs-lookup"><span data-stu-id="c54fb-104">SYNOPSIS</span></span>
<span data-ttu-id="c54fb-105">啟動一或多個已停止的服務。</span><span class="sxs-lookup"><span data-stu-id="c54fb-105">Starts one or more stopped services.</span></span>

## <span data-ttu-id="c54fb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c54fb-106">SYNTAX</span></span>

### <span data-ttu-id="c54fb-107">InputObject (預設值)</span><span class="sxs-lookup"><span data-stu-id="c54fb-107">InputObject (Default)</span></span>

```
Start-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c54fb-108">預設</span><span class="sxs-lookup"><span data-stu-id="c54fb-108">Default</span></span>

```
Start-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="c54fb-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c54fb-109">DisplayName</span></span>

```
Start-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c54fb-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c54fb-110">DESCRIPTION</span></span>

<span data-ttu-id="c54fb-111">指令 `Start-Service` 程式會將啟動訊息傳送給每個指定服務的 Windows 服務控制器。</span><span class="sxs-lookup"><span data-stu-id="c54fb-111">The `Start-Service` cmdlet sends a start message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="c54fb-112">如果服務正在執行，系統會忽略該訊息，且沒有錯誤。</span><span class="sxs-lookup"><span data-stu-id="c54fb-112">If a service is already running, the message is ignored without error.</span></span> <span data-ttu-id="c54fb-113">您可以依服務的服務名稱或顯示名稱來指定服務，或是使用 **InputObject** 參數來提供代表您要啟動之服務的服務物件。</span><span class="sxs-lookup"><span data-stu-id="c54fb-113">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to supply a service object that represents the services that you want to start.</span></span>

## <span data-ttu-id="c54fb-114">範例</span><span class="sxs-lookup"><span data-stu-id="c54fb-114">EXAMPLES</span></span>

### <span data-ttu-id="c54fb-115">範例 1︰使用名稱啟動服務</span><span class="sxs-lookup"><span data-stu-id="c54fb-115">Example 1: Start a service by using its name</span></span>

<span data-ttu-id="c54fb-116">此範例會啟動本機電腦上的 EventLog 服務。</span><span class="sxs-lookup"><span data-stu-id="c54fb-116">This example starts the EventLog service on the local computer.</span></span> <span data-ttu-id="c54fb-117">**Name** 參數會依服務的服務名稱來識別服務。</span><span class="sxs-lookup"><span data-stu-id="c54fb-117">The **Name** parameter identifies the service by its service name.</span></span>

```powershell
Start-Service -Name "eventlog"
```

### <span data-ttu-id="c54fb-118">範例 2︰顯示資訊，但不啟動服務</span><span class="sxs-lookup"><span data-stu-id="c54fb-118">Example 2: Display information without starting a service</span></span>

<span data-ttu-id="c54fb-119">此範例顯示當您啟動的服務具有包含 "remote" 的顯示名稱時，會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="c54fb-119">This example shows what would occur if you started the services that have a display name that includes "remote".</span></span>

```powershell
Start-Service -DisplayName *remote* -WhatIf
```

<span data-ttu-id="c54fb-120">**DisplayName** 參數會依據服務的顯示名稱（而非其服務名稱）來識別服務。</span><span class="sxs-lookup"><span data-stu-id="c54fb-120">The **DisplayName** parameter identifies the services by their display name instead of their service name.</span></span> <span data-ttu-id="c54fb-121">**WhatIf** 參數會讓 Cmdlet 顯示當您執行命令時所發生的情況，但不會進行變更。</span><span class="sxs-lookup"><span data-stu-id="c54fb-121">The **WhatIf** parameter causes the cmdlet to display what would happen when you run the command but does not make changes.</span></span>

### <span data-ttu-id="c54fb-122">範例 3︰啟動服務，並在文字檔中記錄動作</span><span class="sxs-lookup"><span data-stu-id="c54fb-122">Example 3: Start a service and record the action in a text file</span></span>

<span data-ttu-id="c54fb-123">此範例會啟動電腦上的 Windows Management Instrumentation (WMI) 服務，並將動作的記錄新增至 services.txt 檔。</span><span class="sxs-lookup"><span data-stu-id="c54fb-123">This example starts the Windows Management Instrumentation (WMI) service on the computer and adds a record of the action to the services.txt file.</span></span>

```powershell
$s = Get-Service wmi
Start-Service -InputObject $s -PassThru | Format-List >> services.txt
```

<span data-ttu-id="c54fb-124">首先我們 `Get-Service` 會使用來取得代表 WMI 服務的物件，並將它儲存在 `$s` 變數中。</span><span class="sxs-lookup"><span data-stu-id="c54fb-124">First we use `Get-Service` to get an object that represent the WMI service and store it in the `$s` variable.</span></span> <span data-ttu-id="c54fb-125">接下來，我們會啟動服務。</span><span class="sxs-lookup"><span data-stu-id="c54fb-125">Next, we start the service.</span></span> <span data-ttu-id="c54fb-126">如果沒有 **PassThru** 參數，則不 `Start-Service` 會建立任何輸出。</span><span class="sxs-lookup"><span data-stu-id="c54fb-126">Without the **PassThru** parameter, `Start-Service` does not create any output.</span></span> <span data-ttu-id="c54fb-127">管線運算子 (|) 將物件輸出傳遞 `Start-Service` 給 `Format-List` Cmdlet，以將物件格式化為其屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="c54fb-127">The pipeline operator (|) passes the object output by `Start-Service` to the `Format-List` cmdlet to format the object as a list of its properties.</span></span> <span data-ttu-id="c54fb-128">附加重新導向運算子 () 會將 \> \> 輸出重新導向至 services.txt 的檔案。</span><span class="sxs-lookup"><span data-stu-id="c54fb-128">The append redirection operator (\>\>) redirects the output to the services.txt file.</span></span> <span data-ttu-id="c54fb-129">輸出會新增至現有檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="c54fb-129">The output is added to the end of the existing file.</span></span>

### <span data-ttu-id="c54fb-130">範例 4︰啟動停用的服務</span><span class="sxs-lookup"><span data-stu-id="c54fb-130">Example 4: Start a disabled service</span></span>

<span data-ttu-id="c54fb-131">此範例示範如何在服務的啟動類型為 **停用** 時啟動服務。</span><span class="sxs-lookup"><span data-stu-id="c54fb-131">This example shows how to start a service when the start type of the service is **Disabled** .</span></span>

```
PS> Start-Service tlntsvr
Start-Service : Service 'Telnet (TlntSvr)' cannot be started due to the following error: Cannot start service TlntSvr on computer '.'.
At line:1 char:14
+ Start-Service  <<<< tlntsvr

PS> Get-CimInstance win32_service | Where-Object Name -eq "tlntsvr"
ExitCode  : 0
Name      : TlntSvr
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS> Set-Service tlntsvr -StartupType manual
PS> Start-Service tlntsvr
```

<span data-ttu-id="c54fb-132">第一次嘗試啟動 Telnet 服務 (tlntsvr) 失敗。</span><span class="sxs-lookup"><span data-stu-id="c54fb-132">The first attempt to start the Telnet service (tlntsvr) fails.</span></span> <span data-ttu-id="c54fb-133">此 `Get-CimInstance` 命令會顯示 Tlntsvr 服務的 **StartMode** 屬性已 **停用** 。</span><span class="sxs-lookup"><span data-stu-id="c54fb-133">The `Get-CimInstance` command shows that the **StartMode** property of the Tlntsvr service is **Disabled** .</span></span> <span data-ttu-id="c54fb-134">Cmdlet 會將 `Set-Service` 啟動類型變更為 **手動** 。</span><span class="sxs-lookup"><span data-stu-id="c54fb-134">The `Set-Service` cmdlet changes the start type to **Manual** .</span></span> <span data-ttu-id="c54fb-135">現在，我們可以重新提交 `Start-Service` 命令。</span><span class="sxs-lookup"><span data-stu-id="c54fb-135">Now, we can resubmit the `Start-Service` command.</span></span> <span data-ttu-id="c54fb-136">這次命令會執行成功。</span><span class="sxs-lookup"><span data-stu-id="c54fb-136">This time, the command succeeds.</span></span> <span data-ttu-id="c54fb-137">若要確認命令是否成功，請執行 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="c54fb-137">To verify that the command succeeded, run `Get-Service`.</span></span>

## <span data-ttu-id="c54fb-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c54fb-138">PARAMETERS</span></span>

### <span data-ttu-id="c54fb-139">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="c54fb-139">-DisplayName</span></span>

<span data-ttu-id="c54fb-140">指定要啟動之服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="c54fb-140">Specifies the display names of the services to start.</span></span> <span data-ttu-id="c54fb-141">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c54fb-141">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c54fb-142">-Exclude</span><span class="sxs-lookup"><span data-stu-id="c54fb-142">-Exclude</span></span>

<span data-ttu-id="c54fb-143">指定此 Cmdlet 省略的服務。</span><span class="sxs-lookup"><span data-stu-id="c54fb-143">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="c54fb-144">此參數的值會限定 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="c54fb-144">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="c54fb-145">輸入名稱元素或模式，例如 `s*` 。</span><span class="sxs-lookup"><span data-stu-id="c54fb-145">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="c54fb-146">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c54fb-146">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c54fb-147">-Include</span><span class="sxs-lookup"><span data-stu-id="c54fb-147">-Include</span></span>

<span data-ttu-id="c54fb-148">指定此 Cmdlet 啟動的服務。</span><span class="sxs-lookup"><span data-stu-id="c54fb-148">Specifies services that this cmdlet starts.</span></span> <span data-ttu-id="c54fb-149">此參數的值會限定 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="c54fb-149">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="c54fb-150">輸入名稱元素或模式，例如 `s*` 。</span><span class="sxs-lookup"><span data-stu-id="c54fb-150">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="c54fb-151">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c54fb-151">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c54fb-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c54fb-152">-InputObject</span></span>

<span data-ttu-id="c54fb-153">指定代表要啟動之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="c54fb-153">Specifies **ServiceController** objects representing the services to be started.</span></span> <span data-ttu-id="c54fb-154">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="c54fb-154">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c54fb-155">-Name</span><span class="sxs-lookup"><span data-stu-id="c54fb-155">-Name</span></span>

<span data-ttu-id="c54fb-156">指定要啟動之服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="c54fb-156">Specifies the service names for the service to be started.</span></span>

<span data-ttu-id="c54fb-157">參數名稱為選擇性。</span><span class="sxs-lookup"><span data-stu-id="c54fb-157">The parameter name is optional.</span></span> <span data-ttu-id="c54fb-158">您可以使用 **名稱** 或其別名、 **ServiceName** ，也可以省略參數名稱。</span><span class="sxs-lookup"><span data-stu-id="c54fb-158">You can use **Name** or its alias, **ServiceName** , or you can omit the parameter name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c54fb-159">-PassThru</span><span class="sxs-lookup"><span data-stu-id="c54fb-159">-PassThru</span></span>

<span data-ttu-id="c54fb-160">傳回代表服務的物件。</span><span class="sxs-lookup"><span data-stu-id="c54fb-160">Returns an object that represents the service.</span></span> <span data-ttu-id="c54fb-161">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="c54fb-161">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="c54fb-162">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c54fb-162">-Confirm</span></span>

<span data-ttu-id="c54fb-163">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="c54fb-163">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c54fb-164">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c54fb-164">-WhatIf</span></span>

<span data-ttu-id="c54fb-165">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="c54fb-165">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c54fb-166">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="c54fb-166">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c54fb-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c54fb-167">CommonParameters</span></span>

<span data-ttu-id="c54fb-168">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c54fb-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c54fb-169">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c54fb-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c54fb-170">輸入</span><span class="sxs-lookup"><span data-stu-id="c54fb-170">INPUTS</span></span>

### <span data-ttu-id="c54fb-171">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="c54fb-171">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="c54fb-172">您可以使用管線將代表服務的物件，或是包含服務名稱的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c54fb-172">You can pipe objects that represent the services or strings that contain the service names to this cmdlet.</span></span>

## <span data-ttu-id="c54fb-173">輸出</span><span class="sxs-lookup"><span data-stu-id="c54fb-173">OUTPUTS</span></span>

### <span data-ttu-id="c54fb-174">無、System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="c54fb-174">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="c54fb-175">如果您指定 **PassThru** ，此 Cmdlet 會產生代表該服務的 **System.ServiceProcess.ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="c54fb-175">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify **PassThru** .</span></span> <span data-ttu-id="c54fb-176">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="c54fb-176">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c54fb-177">注意</span><span class="sxs-lookup"><span data-stu-id="c54fb-177">NOTES</span></span>

* <span data-ttu-id="c54fb-178">您也可以 `Start-Service` 使用內建的別名來參考 `sasv` 。</span><span class="sxs-lookup"><span data-stu-id="c54fb-178">You can also refer to `Start-Service` by its built-in alias, `sasv`.</span></span> <span data-ttu-id="c54fb-179">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="c54fb-179">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
* <span data-ttu-id="c54fb-180">`Start-Service` 只有在目前的使用者有權進行此作業時，才能控制服務。</span><span class="sxs-lookup"><span data-stu-id="c54fb-180">`Start-Service` can control services only if the current user has permission to do this.</span></span> <span data-ttu-id="c54fb-181">若命令無法正確運作，您可能沒有必要的權限。</span><span class="sxs-lookup"><span data-stu-id="c54fb-181">If a command does not work correctly, you might not have the required permissions.</span></span>
* <span data-ttu-id="c54fb-182">若要尋找系統上服務的服務名稱和顯示名稱，請輸入 `Get-Service`。</span><span class="sxs-lookup"><span data-stu-id="c54fb-182">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="c54fb-183">服務名稱會出現在 [ **名稱** ] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="c54fb-183">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>
* <span data-ttu-id="c54fb-184">您只能啟動啟動類型為 [手動]、[自動] 或 [自動] (延遲開始) 的服務。</span><span class="sxs-lookup"><span data-stu-id="c54fb-184">You can start only the services that have a start type of Manual, Automatic, or Automatic (Delayed Start).</span></span> <span data-ttu-id="c54fb-185">您無法啟動啟動類型是 Disabled 的服務。</span><span class="sxs-lookup"><span data-stu-id="c54fb-185">You cannot start the services that have a start type of Disabled.</span></span> <span data-ttu-id="c54fb-186">如果 `Start-Service` 命令因訊息而失敗 `Cannot start service \<service-name\> on computer` ，請使用 `Get-CimInstance` 來尋找服務的啟動類型，如果您需要的話，請使用 `Set-Service` Cmdlet 來變更服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="c54fb-186">If a `Start-Service` command fails with the message `Cannot start service \<service-name\> on computer`, use `Get-CimInstance` to find the start type of the service and, if you have to, use the `Set-Service` cmdlet to change the start type of the service.</span></span>
* <span data-ttu-id="c54fb-187">某些服務，例如效能記錄及警示 (SysmonLog)，在沒有執行任何工作時會自動停止。</span><span class="sxs-lookup"><span data-stu-id="c54fb-187">Some services, such as Performance Logs and Alerts (SysmonLog) stop automatically if they have no work to do.</span></span> <span data-ttu-id="c54fb-188">當 PowerShell 啟動幾乎立即停止的服務時，它會顯示下列訊息： `Service \<display-name\> start failed.`</span><span class="sxs-lookup"><span data-stu-id="c54fb-188">When PowerShell starts a service that stops itself almost immediately, it displays the following message: `Service \<display-name\> start failed.`</span></span>

## <span data-ttu-id="c54fb-189">相關連結</span><span class="sxs-lookup"><span data-stu-id="c54fb-189">RELATED LINKS</span></span>

[<span data-ttu-id="c54fb-190">Get-Service</span><span class="sxs-lookup"><span data-stu-id="c54fb-190">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="c54fb-191">New-Service</span><span class="sxs-lookup"><span data-stu-id="c54fb-191">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="c54fb-192">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="c54fb-192">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="c54fb-193">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="c54fb-193">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="c54fb-194">Set-Service</span><span class="sxs-lookup"><span data-stu-id="c54fb-194">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="c54fb-195">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="c54fb-195">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="c54fb-196">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="c54fb-196">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="c54fb-197">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="c54fb-197">Remove-Service</span></span>](Remove-Service.md)
