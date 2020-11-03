---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: ce91313d1b581e3d666c131caaa1cf7ecad0c04f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201563"
---
# <span data-ttu-id="ff3b1-103">Get-Service</span><span class="sxs-lookup"><span data-stu-id="ff3b1-103">Get-Service</span></span>

## <span data-ttu-id="ff3b1-104">概要</span><span class="sxs-lookup"><span data-stu-id="ff3b1-104">SYNOPSIS</span></span>
<span data-ttu-id="ff3b1-105">取得電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-105">Gets the services on the computer.</span></span>

## <span data-ttu-id="ff3b1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ff3b1-106">SYNTAX</span></span>

### <span data-ttu-id="ff3b1-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="ff3b1-107">Default (Default)</span></span>

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="ff3b1-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ff3b1-108">DisplayName</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="ff3b1-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="ff3b1-109">InputObject</span></span>

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## <span data-ttu-id="ff3b1-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ff3b1-110">DESCRIPTION</span></span>

<span data-ttu-id="ff3b1-111">`Get-Service`Cmdlet 會取得代表電腦上之服務的物件，包括執行中和已停止的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-111">The `Get-Service` cmdlet gets objects that represent the services on a computer, including running and stopped services.</span></span> <span data-ttu-id="ff3b1-112">依預設，當 `Get-Service` 執行時沒有參數時，會傳回所有本機電腦的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-112">By default, when `Get-Service` is run without parameters, all the local computer's services are returned.</span></span>

<span data-ttu-id="ff3b1-113">您可以藉由指定服務的服務名稱或顯示名稱，或使用管線將服務物件傳送至此 Cmdlet，來指示此 Cmdlet 只取得特定的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-113">You can direct this cmdlet to get only particular services by specifying the service name or the display name of the services, or you can pipe service objects to this cmdlet.</span></span>

## <span data-ttu-id="ff3b1-114">範例</span><span class="sxs-lookup"><span data-stu-id="ff3b1-114">EXAMPLES</span></span>

### <span data-ttu-id="ff3b1-115">範例1：取得電腦上的所有服務</span><span class="sxs-lookup"><span data-stu-id="ff3b1-115">Example 1: Get all services on the computer</span></span>

<span data-ttu-id="ff3b1-116">此範例會取得電腦上的所有服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-116">This example gets all of the services on the computer.</span></span> <span data-ttu-id="ff3b1-117">它的行為就像您輸入 `Get-Service *` 的一樣。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-117">It behaves as though you typed `Get-Service *`.</span></span> <span data-ttu-id="ff3b1-118">預設顯示會展示狀態、服務名稱及每個服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-118">The default display shows the status, service name, and display name of each service.</span></span>

```powershell
Get-Service
```

### <span data-ttu-id="ff3b1-119">範例2：取得以搜尋字串開頭的服務</span><span class="sxs-lookup"><span data-stu-id="ff3b1-119">Example 2: Get services that begin with a search string</span></span>

<span data-ttu-id="ff3b1-120">此範例會使用以 WMI 為開頭 (Windows Management Instrumentation) 的服務名稱，來抓取服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-120">This example retrieves services with service names that begin with WMI (Windows Management Instrumentation).</span></span>

```powershell
Get-Service "wmi*"
```

### <span data-ttu-id="ff3b1-121">範例3：顯示包含搜尋字串的服務</span><span class="sxs-lookup"><span data-stu-id="ff3b1-121">Example 3: Display services that include a search string</span></span>

<span data-ttu-id="ff3b1-122">此範例會顯示顯示名稱包含「網路」文字的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-122">This example displays services with a display name that includes the word network.</span></span> <span data-ttu-id="ff3b1-123">搜尋顯示名稱，即使服務名稱不包含 Net （例如 xmlprov (）網路布建服務，也會尋找網路相關的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-123">Searching the display name finds network-related services even when the service name doesn't include Net, such as xmlprov, the Network Provisioning Service.</span></span>

```powershell
Get-Service -Displayname "*network*"
```

### <span data-ttu-id="ff3b1-124">範例4：取得以搜尋字串和排除開頭的服務</span><span class="sxs-lookup"><span data-stu-id="ff3b1-124">Example 4: Get services that begin with a search string and an exclusion</span></span>

<span data-ttu-id="ff3b1-125">此範例只會取得服務名稱開頭為 **win** 的服務，但 WinRM 服務除外。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-125">This example only gets the services with service names that begin with **win** , except for the WinRM service.</span></span>

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### <span data-ttu-id="ff3b1-126">範例5：顯示目前作用中的服務</span><span class="sxs-lookup"><span data-stu-id="ff3b1-126">Example 5: Display services that are currently active</span></span>

<span data-ttu-id="ff3b1-127">此範例只會顯示狀態為 [正在執行] 的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-127">This example displays only the services with a status of Running.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

<span data-ttu-id="ff3b1-128">`Get-Service` 取得電腦上的所有服務，並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-128">`Get-Service` gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="ff3b1-129">`Where-Object`Cmdlet 只會選取 **Status** 屬性等於正在執行的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-129">The `Where-Object` cmdlet, selects only the services with a **Status** property that equals Running.</span></span>

<span data-ttu-id="ff3b1-130">Status 只是服務物件的一個屬性。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-130">Status is only one property of service objects.</span></span> <span data-ttu-id="ff3b1-131">若要查看所有屬性，請輸入 `Get-Service | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-131">To see all of the properties, type `Get-Service | Get-Member`.</span></span>

### <span data-ttu-id="ff3b1-132">範例6：列出電腦上具有相依服務的服務</span><span class="sxs-lookup"><span data-stu-id="ff3b1-132">Example 6: List the services on the computer that have dependent services</span></span>

<span data-ttu-id="ff3b1-133">此範例會取得具有相依服務的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-133">This example gets services that have dependent services.</span></span>

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

<span data-ttu-id="ff3b1-134">`Get-Service`Cmdlet 會取得電腦上的所有服務，並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-134">The `Get-Service` cmdlet gets all the services on the computer and sends the objects down the pipeline.</span></span> <span data-ttu-id="ff3b1-135">`Where-Object`Cmdlet 會選取其 **DependentServices** 屬性不是 null 的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-135">The `Where-Object` cmdlet selects the services whose **DependentServices** property isn't null.</span></span>

<span data-ttu-id="ff3b1-136">結果會向下傳送至 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-136">The results are sent down the pipeline to the `Format-List` cmdlet.</span></span> <span data-ttu-id="ff3b1-137">**Property** 參數會顯示服務的名稱、相依服務的名稱，以及顯示每個服務的相依服務數目的計算屬性。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-137">The **Property** parameter displays the name of the service, the name of the dependent services, and a calculated property that displays the number of dependent services for each service.</span></span>

### <span data-ttu-id="ff3b1-138">範例7：依屬性值排序服務</span><span class="sxs-lookup"><span data-stu-id="ff3b1-138">Example 7: Sort services by property value</span></span>

<span data-ttu-id="ff3b1-139">此範例顯示當您依 [ **狀態** ] 屬性的值以遞增順序排序服務時，已停止的服務會在執行服務之前出現。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-139">This example shows that when you sort services in ascending order by the value of their **Status** property, stopped services appear before running services.</span></span> <span data-ttu-id="ff3b1-140">原因是 **狀態** 的值是列舉，其中已停止的值為1，且執行的值為4。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-140">The reason is because the value of **Status** is an enumeration, in which Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="ff3b1-141">如需詳細資訊，請參閱 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-141">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

<span data-ttu-id="ff3b1-142">若要先列出執行中的服務，請使用 Cmdlet 的 **遞減** 參數 `Sort-Object` 。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-142">To list running services first, use the **Descending** parameter of the `Sort-Object` cmdlet.</span></span>

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

### <span data-ttu-id="ff3b1-143">範例8：取得服務的相依服務</span><span class="sxs-lookup"><span data-stu-id="ff3b1-143">Example 8: Get the dependent services of a service</span></span>

<span data-ttu-id="ff3b1-144">此範例會取得 WinRM 服務所需的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-144">This example gets the services that the WinRM service requires.</span></span> <span data-ttu-id="ff3b1-145">傳回服務之 **ServicesDependedOn** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-145">The value of the service's **ServicesDependedOn** property is returned.</span></span>

```powershell
Get-Service "WinRM" -RequiredServices
```

### <span data-ttu-id="ff3b1-146">範例9：透過管線運算子取得服務</span><span class="sxs-lookup"><span data-stu-id="ff3b1-146">Example 9: Get a service through the pipeline operator</span></span>

<span data-ttu-id="ff3b1-147">這個範例會取得本機電腦上的 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-147">This example gets the WinRM service on the local computer.</span></span> <span data-ttu-id="ff3b1-148">服務名稱字串（以引號括住）會沿著管線向下傳送至 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-148">The service name string, enclosed in quotation marks, is sent down the pipeline to `Get-Service`.</span></span>

```powershell
"WinRM" | Get-Service
```

## <span data-ttu-id="ff3b1-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ff3b1-149">PARAMETERS</span></span>

### <span data-ttu-id="ff3b1-150">-DependentServices</span><span class="sxs-lookup"><span data-stu-id="ff3b1-150">-DependentServices</span></span>

<span data-ttu-id="ff3b1-151">指出此 Cmdlet 只會取得相依于指定服務的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-151">Indicates that this cmdlet gets only the services that depend upon the specified service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ff3b1-152">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="ff3b1-152">-DisplayName</span></span>

<span data-ttu-id="ff3b1-153">以字串陣列指定要抓取之服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-153">Specifies, as a string array, the display names of services to be retrieved.</span></span> <span data-ttu-id="ff3b1-154">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-154">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="ff3b1-155">-Exclude</span><span class="sxs-lookup"><span data-stu-id="ff3b1-155">-Exclude</span></span>

<span data-ttu-id="ff3b1-156">以字串陣列指定此 Cmdlet 從作業中排除的服務或服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-156">Specifies, as a string array, a service or services that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="ff3b1-157">此參數的值會限定 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-157">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="ff3b1-158">輸入名稱元素或模式，例如 `s*` 。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-158">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="ff3b1-159">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-159">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="ff3b1-160">-Include</span><span class="sxs-lookup"><span data-stu-id="ff3b1-160">-Include</span></span>

<span data-ttu-id="ff3b1-161">以字串陣列指定此 Cmdlet 在作業中包含的服務或服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-161">Specifies, as a string array, a service or services that this cmdlet includes in the operation.</span></span> <span data-ttu-id="ff3b1-162">此參數的值會限定 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-162">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="ff3b1-163">輸入名稱元素或模式，例如 `s*` 。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-163">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="ff3b1-164">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-164">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="ff3b1-165">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ff3b1-165">-InputObject</span></span>

<span data-ttu-id="ff3b1-166">指定代表要抓取之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-166">Specifies **ServiceController** objects representing the services to be retrieved.</span></span> <span data-ttu-id="ff3b1-167">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-167">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="ff3b1-168">您可以使用管線將服務物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-168">You can pipe a service object to this cmdlet.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ff3b1-169">-Name</span><span class="sxs-lookup"><span data-stu-id="ff3b1-169">-Name</span></span>

<span data-ttu-id="ff3b1-170">指定要抓取之服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-170">Specifies the service names of services to be retrieved.</span></span> <span data-ttu-id="ff3b1-171">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-171">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ff3b1-172">-RequiredServices</span><span class="sxs-lookup"><span data-stu-id="ff3b1-172">-RequiredServices</span></span>

<span data-ttu-id="ff3b1-173">指出此 Cmdlet 只會取得此服務所需的服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-173">Indicates that this cmdlet gets only the services that this service requires.</span></span> <span data-ttu-id="ff3b1-174">此參數會取得服務之 **ServicesDependedOn** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-174">This parameter gets the value of the **ServicesDependedOn** property of the service.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ff3b1-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ff3b1-175">CommonParameters</span></span>

<span data-ttu-id="ff3b1-176">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ff3b1-177">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ff3b1-178">輸入</span><span class="sxs-lookup"><span data-stu-id="ff3b1-178">INPUTS</span></span>

### <span data-ttu-id="ff3b1-179">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="ff3b1-179">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="ff3b1-180">您可以使用管線將服務物件或服務名稱傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-180">You can pipe a service object or a service name to this cmdlet.</span></span>

## <span data-ttu-id="ff3b1-181">輸出</span><span class="sxs-lookup"><span data-stu-id="ff3b1-181">OUTPUTS</span></span>

### <span data-ttu-id="ff3b1-182">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="ff3b1-182">System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="ff3b1-183">此 Cmdlet 會傳回代表電腦上服務的物件。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-183">This cmdlet returns objects that represent the services on the computer.</span></span>

## <span data-ttu-id="ff3b1-184">注意</span><span class="sxs-lookup"><span data-stu-id="ff3b1-184">NOTES</span></span>

<span data-ttu-id="ff3b1-185">從 PowerShell 6.0 開始，會將下列屬性新增至 **ServiceController** 物件： **UserName** 、 **Description** 、 **DelayedAutoStart** 、 **BinaryPathName** 和 **StartupType** 。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-185">Beginning in PowerShell 6.0, the following properties are added to the **ServiceController** objects: **UserName** , **Description** , **DelayedAutoStart** , **BinaryPathName** , and **StartupType** .</span></span>

<span data-ttu-id="ff3b1-186">您也可以 `Get-Service` 使用內建的別名來參考 `gsv` 。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-186">You can also refer to `Get-Service` by its built-in alias, `gsv`.</span></span> <span data-ttu-id="ff3b1-187">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-187">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="ff3b1-188">只有當目前的使用者具有查看服務的許可權時，此 Cmdlet 才會顯示服務。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-188">This cmdlet can display services only when the current user has permission to see them.</span></span> <span data-ttu-id="ff3b1-189">如果此 Cmdlet 未顯示服務，您可能沒有查看服務的許可權。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-189">If this cmdlet does not display services, you might not have permission to see them.</span></span>

<span data-ttu-id="ff3b1-190">若要尋找您系統上每個服務的服務名稱和顯示名稱，請輸入 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-190">To find the service name and display name of each service on your system, type `Get-Service`.</span></span> <span data-ttu-id="ff3b1-191">服務名稱會出現在 [名稱] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-191">The service names appear in the Name column, and the display names appear in the **DisplayName** column.</span></span>

<span data-ttu-id="ff3b1-192">當您依 **Status** 屬性的值以遞增順序排序時，已停止的服務會在執行服務之前出現。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-192">When you sort in ascending order by the **Status** property's value, Stopped services appear before Running services.</span></span> <span data-ttu-id="ff3b1-193">服務的 **status** 屬性是一個列舉值，而狀態名稱則代表整數值。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-193">The service's **Status** property is an enumerated value and the status names represent integer values.</span></span> <span data-ttu-id="ff3b1-194">排序次序是以整數值為基礎，而不是名稱。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-194">The sort order is based on the integer value, not the name.</span></span> <span data-ttu-id="ff3b1-195">因為已停止的值為1，且執行的值為4，所以已停止。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-195">Stopped appears before because Running because Stopped has a value of 1, and Running has a value of 4.</span></span> <span data-ttu-id="ff3b1-196">如需詳細資訊，請參閱 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。</span><span class="sxs-lookup"><span data-stu-id="ff3b1-196">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

## <span data-ttu-id="ff3b1-197">相關連結</span><span class="sxs-lookup"><span data-stu-id="ff3b1-197">RELATED LINKS</span></span>

[<span data-ttu-id="ff3b1-198">New-Service</span><span class="sxs-lookup"><span data-stu-id="ff3b1-198">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="ff3b1-199">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="ff3b1-199">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="ff3b1-200">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="ff3b1-200">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="ff3b1-201">Set-Service</span><span class="sxs-lookup"><span data-stu-id="ff3b1-201">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="ff3b1-202">Start-Service</span><span class="sxs-lookup"><span data-stu-id="ff3b1-202">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="ff3b1-203">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="ff3b1-203">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="ff3b1-204">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="ff3b1-204">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="ff3b1-205">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="ff3b1-205">Remove-Service</span></span>](Remove-Service.md)
