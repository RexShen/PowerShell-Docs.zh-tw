---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: 9dd0e04476d9f935d3284c30d1628b31417c14c2
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346287"
---
# <span data-ttu-id="d5661-103">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="d5661-103">Stop-Service</span></span>

## <span data-ttu-id="d5661-104">概要</span><span class="sxs-lookup"><span data-stu-id="d5661-104">SYNOPSIS</span></span>
<span data-ttu-id="d5661-105">停止一或多個執行中的服務。</span><span class="sxs-lookup"><span data-stu-id="d5661-105">Stops one or more running services.</span></span>

## <span data-ttu-id="d5661-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d5661-106">SYNTAX</span></span>

### <span data-ttu-id="d5661-107">InputObject (預設值)</span><span class="sxs-lookup"><span data-stu-id="d5661-107">InputObject (Default)</span></span>

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d5661-108">預設</span><span class="sxs-lookup"><span data-stu-id="d5661-108">Default</span></span>

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d5661-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d5661-109">DisplayName</span></span>

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d5661-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d5661-110">DESCRIPTION</span></span>

<span data-ttu-id="d5661-111">`Stop-Service`Cmdlet 會為每個指定的服務傳送停止訊息給 Windows 服務控制器。</span><span class="sxs-lookup"><span data-stu-id="d5661-111">The `Stop-Service` cmdlet sends a stop message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="d5661-112">您可以依服務的服務名稱或顯示名稱來指定服務，也可以使用 **InputObject** 參數來傳送代表您要停止之服務的服務物件。</span><span class="sxs-lookup"><span data-stu-id="d5661-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the service that you want to stop.</span></span>

## <span data-ttu-id="d5661-113">範例</span><span class="sxs-lookup"><span data-stu-id="d5661-113">EXAMPLES</span></span>

### <span data-ttu-id="d5661-114">範例1：停止本機電腦上的服務</span><span class="sxs-lookup"><span data-stu-id="d5661-114">Example 1: Stop a service on the local computer</span></span>

```
PS C:\> Stop-Service -Name "sysmonlog"
```

<span data-ttu-id="d5661-115">此命令會停止本機電腦上的 Performance Logs and Alerts (SysmonLog) 服務。</span><span class="sxs-lookup"><span data-stu-id="d5661-115">This command stops the Performance Logs and Alerts (SysmonLog) service on the local computer.</span></span>

### <span data-ttu-id="d5661-116">範例2：使用顯示名稱停止服務</span><span class="sxs-lookup"><span data-stu-id="d5661-116">Example 2: Stop a service by using the display name</span></span>

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

<span data-ttu-id="d5661-117">此命令會停止本機電腦上的 Telnet 服務。</span><span class="sxs-lookup"><span data-stu-id="d5661-117">This command stops the Telnet service on the local computer.</span></span> <span data-ttu-id="d5661-118">命令使用 `Get-Service` 來取得代表 Telnet 服務的物件。</span><span class="sxs-lookup"><span data-stu-id="d5661-118">The command uses `Get-Service` to get an object that represents the Telnet service.</span></span> <span data-ttu-id="d5661-119">管線運算子 (`|`) 將物件輸送至 `Stop-Service` ，這會停止服務。</span><span class="sxs-lookup"><span data-stu-id="d5661-119">The pipeline operator (`|`) pipes the object to `Stop-Service`, which stops the service.</span></span>

### <span data-ttu-id="d5661-120">範例3：停止具有相依服務的服務</span><span class="sxs-lookup"><span data-stu-id="d5661-120">Example 3: Stop a service that has dependent services</span></span>

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

<span data-ttu-id="d5661-121">此範例會停止本機電腦上的 IISAdmin 服務。</span><span class="sxs-lookup"><span data-stu-id="d5661-121">This example stops the IISAdmin service on the local computer.</span></span> <span data-ttu-id="d5661-122">因為停止這項服務也會停止相依于 IISAdmin 服務的服務，所以最好是 `Stop-Service` 在列出相依于 IISAdmin 服務之服務的命令前面。</span><span class="sxs-lookup"><span data-stu-id="d5661-122">Because stopping this service also stops the services that depend on the IISAdmin service, it is best to precede `Stop-Service` with a command that lists the services that depend on the IISAdmin service.</span></span>

<span data-ttu-id="d5661-123">第一個命令會列出與 IISAdmin 相依的服務。</span><span class="sxs-lookup"><span data-stu-id="d5661-123">The first command lists the services that depend on IISAdmin.</span></span> <span data-ttu-id="d5661-124">它會使用 `Get-Service` 來取得代表 IISAdmin 服務的物件。</span><span class="sxs-lookup"><span data-stu-id="d5661-124">It uses `Get-Service` to get an object that represents the IISAdmin service.</span></span> <span data-ttu-id="d5661-125">管線運算子 (`|`) 將結果傳遞給 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d5661-125">The pipeline operator (`|`) passes the result to the `Format-List` cmdlet.</span></span> <span data-ttu-id="d5661-126">命令使用的 **Property** 參數 `Format-List` ，只列出服務的 **Name** 和 **DependentServices** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d5661-126">The command uses the **Property** parameter of `Format-List` to list only the **Name** and **DependentServices** properties of the service.</span></span>

<span data-ttu-id="d5661-127">第二個命令會停止 IISAdmin 服務。</span><span class="sxs-lookup"><span data-stu-id="d5661-127">The second command stops the IISAdmin service.</span></span> <span data-ttu-id="d5661-128">需要 **Force** 參數才能停止具有相依服務的服務。</span><span class="sxs-lookup"><span data-stu-id="d5661-128">The **Force** parameter is required to stop a service that has dependent services.</span></span> <span data-ttu-id="d5661-129">此命令會使用 **Confirm** 參數，在停止每個服務之前要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="d5661-129">The command uses the **Confirm** parameter to request confirmation from the user before it stops each service.</span></span>

## <span data-ttu-id="d5661-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d5661-130">PARAMETERS</span></span>

### <span data-ttu-id="d5661-131">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="d5661-131">-DisplayName</span></span>

<span data-ttu-id="d5661-132">指定要停止之服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="d5661-132">Specifies the display names of the services to stop.</span></span>
<span data-ttu-id="d5661-133">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d5661-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d5661-134">-Exclude</span><span class="sxs-lookup"><span data-stu-id="d5661-134">-Exclude</span></span>

<span data-ttu-id="d5661-135">指定此 Cmdlet 省略的服務。</span><span class="sxs-lookup"><span data-stu-id="d5661-135">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="d5661-136">此參數的值會限定 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="d5661-136">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="d5661-137">輸入名稱元素或模式，例如 s\*。</span><span class="sxs-lookup"><span data-stu-id="d5661-137">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="d5661-138">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d5661-138">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d5661-139">-Force</span><span class="sxs-lookup"><span data-stu-id="d5661-139">-Force</span></span>

<span data-ttu-id="d5661-140">強制 Cmdlet 停止服務，即使該服務具有相依的服務。</span><span class="sxs-lookup"><span data-stu-id="d5661-140">Forces the cmdlet to stop a service even if that service has dependent services.</span></span>

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

### <span data-ttu-id="d5661-141">-Include</span><span class="sxs-lookup"><span data-stu-id="d5661-141">-Include</span></span>

<span data-ttu-id="d5661-142">指定此 Cmdlet 停止的服務。</span><span class="sxs-lookup"><span data-stu-id="d5661-142">Specifies services that this cmdlet stops.</span></span> <span data-ttu-id="d5661-143">此參數的值會限定 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="d5661-143">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="d5661-144">輸入名稱元素或模式，例如 s\*。</span><span class="sxs-lookup"><span data-stu-id="d5661-144">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="d5661-145">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d5661-145">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="d5661-146">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d5661-146">-InputObject</span></span>

<span data-ttu-id="d5661-147">指定代表要停止之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="d5661-147">Specifies **ServiceController** objects that represent the services to stop.</span></span> <span data-ttu-id="d5661-148">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="d5661-148">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="d5661-149">-Name</span><span class="sxs-lookup"><span data-stu-id="d5661-149">-Name</span></span>

<span data-ttu-id="d5661-150">指定要停止之服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="d5661-150">Specifies the service names of the services to stop.</span></span> <span data-ttu-id="d5661-151">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d5661-151">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="d5661-152">-NoWait</span><span class="sxs-lookup"><span data-stu-id="d5661-152">-NoWait</span></span>

<span data-ttu-id="d5661-153">指出此 Cmdlet 使用 no wait 選項。</span><span class="sxs-lookup"><span data-stu-id="d5661-153">Indicates that this cmdlet uses the no wait option.</span></span>

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

### <span data-ttu-id="d5661-154">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d5661-154">-PassThru</span></span>

<span data-ttu-id="d5661-155">傳回代表服務的物件。</span><span class="sxs-lookup"><span data-stu-id="d5661-155">Returns an object that represents the service.</span></span> <span data-ttu-id="d5661-156">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="d5661-156">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="d5661-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d5661-157">-Confirm</span></span>

<span data-ttu-id="d5661-158">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="d5661-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d5661-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d5661-159">-WhatIf</span></span>

<span data-ttu-id="d5661-160">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="d5661-160">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d5661-161">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="d5661-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d5661-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d5661-162">CommonParameters</span></span>

<span data-ttu-id="d5661-163">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d5661-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d5661-164">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d5661-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d5661-165">輸入</span><span class="sxs-lookup"><span data-stu-id="d5661-165">INPUTS</span></span>

### <span data-ttu-id="d5661-166">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="d5661-166">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="d5661-167">您可以使用管線將服務物件或包含服務名稱的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d5661-167">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="d5661-168">輸出</span><span class="sxs-lookup"><span data-stu-id="d5661-168">OUTPUTS</span></span>

### <span data-ttu-id="d5661-169">無、System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="d5661-169">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="d5661-170">如果您使用 **PassThru** 參數，此 Cmdlet 會產生代表服務的 **system.serviceprocess.dll ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="d5661-170">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you use the **PassThru** parameter.</span></span> <span data-ttu-id="d5661-171">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="d5661-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d5661-172">注意</span><span class="sxs-lookup"><span data-stu-id="d5661-172">NOTES</span></span>

<span data-ttu-id="d5661-173">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="d5661-173">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="d5661-174">您也可以 `Stop-Service` 使用內建的別名 **spsv** 來參考。</span><span class="sxs-lookup"><span data-stu-id="d5661-174">You can also refer to `Stop-Service` by its built-in alias, **spsv**.</span></span> <span data-ttu-id="d5661-175">如需詳細資訊，請參閱 about_Aliases。</span><span class="sxs-lookup"><span data-stu-id="d5661-175">For more information, see about_Aliases.</span></span>

<span data-ttu-id="d5661-176">`Stop-Service` 只有當目前的使用者有權進行此作業時，才能控制服務。</span><span class="sxs-lookup"><span data-stu-id="d5661-176">`Stop-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="d5661-177">若命令無法正確運作，您可能沒有必要的權限。</span><span class="sxs-lookup"><span data-stu-id="d5661-177">If a command does not work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="d5661-178">若要尋找系統上服務的服務名稱和顯示名稱，請輸入 `Get-Service`。</span><span class="sxs-lookup"><span data-stu-id="d5661-178">To find the service names and display names of the services on your system, type `Get-Service`.</span></span> <span data-ttu-id="d5661-179">服務名稱會出現在 [ **名稱** ] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="d5661-179">The service names appear in the **Name** column and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="d5661-180">相關連結</span><span class="sxs-lookup"><span data-stu-id="d5661-180">RELATED LINKS</span></span>

[<span data-ttu-id="d5661-181">Get-Service</span><span class="sxs-lookup"><span data-stu-id="d5661-181">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="d5661-182">New-Service</span><span class="sxs-lookup"><span data-stu-id="d5661-182">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="d5661-183">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="d5661-183">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="d5661-184">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="d5661-184">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="d5661-185">Set-Service</span><span class="sxs-lookup"><span data-stu-id="d5661-185">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="d5661-186">Start-Service</span><span class="sxs-lookup"><span data-stu-id="d5661-186">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="d5661-187">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="d5661-187">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="d5661-188">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="d5661-188">Remove-Service</span></span>](Remove-Service.md)
