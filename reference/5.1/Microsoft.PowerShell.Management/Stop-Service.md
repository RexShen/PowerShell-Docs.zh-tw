---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: 6bffe41f1efd42c686d06f59cf86b374b596d80d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203463"
---
# <span data-ttu-id="382eb-103">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="382eb-103">Stop-Service</span></span>

## <span data-ttu-id="382eb-104">概要</span><span class="sxs-lookup"><span data-stu-id="382eb-104">SYNOPSIS</span></span>
<span data-ttu-id="382eb-105">停止一或多個執行中的服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-105">Stops one or more running services.</span></span>

## <span data-ttu-id="382eb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="382eb-106">SYNTAX</span></span>

### <span data-ttu-id="382eb-107">InputObject (預設值)</span><span class="sxs-lookup"><span data-stu-id="382eb-107">InputObject (Default)</span></span>

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="382eb-108">預設</span><span class="sxs-lookup"><span data-stu-id="382eb-108">Default</span></span>

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="382eb-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="382eb-109">DisplayName</span></span>

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="382eb-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="382eb-110">DESCRIPTION</span></span>

<span data-ttu-id="382eb-111">**停止服務指令程式** 會針對每個指定的服務，將停止訊息傳送至 Windows 服務控制器。</span><span class="sxs-lookup"><span data-stu-id="382eb-111">The **Stop-Service** cmdlet sends a stop message to the Windows Service Controller for each of the specified services.</span></span>
<span data-ttu-id="382eb-112">您可以依服務的服務名稱或顯示名稱來指定服務，也可以使用 **InputObject** 參數來傳送代表您要停止之服務的服務物件。</span><span class="sxs-lookup"><span data-stu-id="382eb-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the service that you want to stop.</span></span>

## <span data-ttu-id="382eb-113">範例</span><span class="sxs-lookup"><span data-stu-id="382eb-113">EXAMPLES</span></span>

### <span data-ttu-id="382eb-114">範例1：停止本機電腦上的服務</span><span class="sxs-lookup"><span data-stu-id="382eb-114">Example 1: Stop a service on the local computer</span></span>

```
PS C:\> Stop-Service -Name "sysmonlog"
```

<span data-ttu-id="382eb-115">此命令會停止本機電腦上的 Performance Logs and Alerts (SysmonLog) 服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-115">This command stops the Performance Logs and Alerts (SysmonLog) service on the local computer.</span></span>

### <span data-ttu-id="382eb-116">範例2：使用顯示名稱停止服務</span><span class="sxs-lookup"><span data-stu-id="382eb-116">Example 2: Stop a service by using the display name</span></span>

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

<span data-ttu-id="382eb-117">此命令會停止本機電腦上的 Telnet 服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-117">This command stops the Telnet service on the local computer.</span></span>
<span data-ttu-id="382eb-118">此命令會使用 **get-service** 取得代表 Telnet 服務的物件。</span><span class="sxs-lookup"><span data-stu-id="382eb-118">The command uses **Get-Service** to get an object that represents the Telnet service.</span></span>
<span data-ttu-id="382eb-119">管線運算子 (|) 將物件傳送到 **停止服務** 的管道，這會停止服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-119">The pipeline operator (|) pipes the object to **Stop-Service** , which stops the service.</span></span>

### <span data-ttu-id="382eb-120">範例3：停止具有相依服務的服務</span><span class="sxs-lookup"><span data-stu-id="382eb-120">Example 3: Stop a service that has dependent services</span></span>

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

<span data-ttu-id="382eb-121">此範例會停止本機電腦上的 IISAdmin 服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-121">This example stops the IISAdmin service on the local computer.</span></span>
<span data-ttu-id="382eb-122">因為停止這項服務也會停止相依于 IISAdmin 服務的服務，所以最好是在 **停止服務** 之前使用一個命令，該命令會列出相依于 IISAdmin 服務的服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-122">Because stopping this service also stops the services that depend on the IISAdmin service, it is best to precede **Stop-Service** with a command that lists the services that depend on the IISAdmin service.</span></span>

<span data-ttu-id="382eb-123">第一個命令會列出與 IISAdmin 相依的服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-123">The first command lists the services that depend on IISAdmin.</span></span>
<span data-ttu-id="382eb-124">它會使用 **取得服務** 來取得代表 IISAdmin 服務的物件。</span><span class="sxs-lookup"><span data-stu-id="382eb-124">It uses **Get-Service** to get an object that represents the IISAdmin service.</span></span>
<span data-ttu-id="382eb-125">管線運算子 (|) 會將結果傳送至 Format-List Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="382eb-125">The pipeline operator (|) passes the result to the Format-List cmdlet.</span></span>
<span data-ttu-id="382eb-126">此命令會使用 **格式清單** 的 *Property* 參數，只列出服務的 **Name** 和 **DependentServices** 屬性。</span><span class="sxs-lookup"><span data-stu-id="382eb-126">The command uses the *Property* parameter of **Format-List** to list only the **Name** and **DependentServices** properties of the service.</span></span>

<span data-ttu-id="382eb-127">第二個命令會停止 IISAdmin 服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-127">The second command stops the IISAdmin service.</span></span>
<span data-ttu-id="382eb-128">需要 *Force* 參數才能停止具有相依服務的服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-128">The *Force* parameter is required to stop a service that has dependent services.</span></span>
<span data-ttu-id="382eb-129">此命令會使用 *Confirm* 參數，在停止每個服務之前要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="382eb-129">The command uses the *Confirm* parameter to request confirmation from the user before it stops each service.</span></span>

## <span data-ttu-id="382eb-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="382eb-130">PARAMETERS</span></span>

### <span data-ttu-id="382eb-131">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="382eb-131">-DisplayName</span></span>

<span data-ttu-id="382eb-132">指定要停止之服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="382eb-132">Specifies the display names of the services to stop.</span></span>
<span data-ttu-id="382eb-133">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="382eb-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="382eb-134">-Exclude</span><span class="sxs-lookup"><span data-stu-id="382eb-134">-Exclude</span></span>

<span data-ttu-id="382eb-135">指定此 Cmdlet 省略的服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-135">Specifies services that this cmdlet omits.</span></span>
<span data-ttu-id="382eb-136">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="382eb-136">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="382eb-137">輸入名稱元素或模式，例如 s\*。</span><span class="sxs-lookup"><span data-stu-id="382eb-137">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="382eb-138">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="382eb-138">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="382eb-139">-Force</span><span class="sxs-lookup"><span data-stu-id="382eb-139">-Force</span></span>

<span data-ttu-id="382eb-140">強制 Cmdlet 停止服務，即使該服務具有相依的服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-140">Forces the cmdlet to stop a service even if that service has dependent services.</span></span>

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

### <span data-ttu-id="382eb-141">-Include</span><span class="sxs-lookup"><span data-stu-id="382eb-141">-Include</span></span>

<span data-ttu-id="382eb-142">指定此 Cmdlet 停止的服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-142">Specifies services that this cmdlet stops.</span></span>
<span data-ttu-id="382eb-143">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="382eb-143">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="382eb-144">輸入名稱元素或模式，例如 s\*。</span><span class="sxs-lookup"><span data-stu-id="382eb-144">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="382eb-145">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="382eb-145">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="382eb-146">-InputObject</span><span class="sxs-lookup"><span data-stu-id="382eb-146">-InputObject</span></span>

<span data-ttu-id="382eb-147">指定代表要停止之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="382eb-147">Specifies **ServiceController** objects that represent the services to stop.</span></span>
<span data-ttu-id="382eb-148">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="382eb-148">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="382eb-149">-Name</span><span class="sxs-lookup"><span data-stu-id="382eb-149">-Name</span></span>

<span data-ttu-id="382eb-150">指定要停止之服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="382eb-150">Specifies the service names of the services to stop.</span></span>
<span data-ttu-id="382eb-151">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="382eb-151">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="382eb-152">-NoWait</span><span class="sxs-lookup"><span data-stu-id="382eb-152">-NoWait</span></span>

<span data-ttu-id="382eb-153">指出此 Cmdlet 使用 no wait 選項。</span><span class="sxs-lookup"><span data-stu-id="382eb-153">Indicates that this cmdlet uses the no wait option.</span></span>

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

### <span data-ttu-id="382eb-154">-PassThru</span><span class="sxs-lookup"><span data-stu-id="382eb-154">-PassThru</span></span>

<span data-ttu-id="382eb-155">傳回代表服務的物件。</span><span class="sxs-lookup"><span data-stu-id="382eb-155">Returns an object that represents the service.</span></span>
<span data-ttu-id="382eb-156">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="382eb-156">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="382eb-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="382eb-157">-Confirm</span></span>

<span data-ttu-id="382eb-158">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="382eb-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="382eb-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="382eb-159">-WhatIf</span></span>

<span data-ttu-id="382eb-160">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="382eb-160">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="382eb-161">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="382eb-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="382eb-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="382eb-162">CommonParameters</span></span>

<span data-ttu-id="382eb-163">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="382eb-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="382eb-164">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="382eb-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="382eb-165">輸入</span><span class="sxs-lookup"><span data-stu-id="382eb-165">INPUTS</span></span>

### <span data-ttu-id="382eb-166">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="382eb-166">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="382eb-167">您可以使用管線將服務物件或包含服務名稱的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="382eb-167">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="382eb-168">輸出</span><span class="sxs-lookup"><span data-stu-id="382eb-168">OUTPUTS</span></span>

### <span data-ttu-id="382eb-169">無、System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="382eb-169">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="382eb-170">如果您使用 *PassThru* 參數，此 Cmdlet 會產生代表服務的 **system.serviceprocess.dll ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="382eb-170">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you use the *PassThru* parameter.</span></span>
<span data-ttu-id="382eb-171">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="382eb-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="382eb-172">注意</span><span class="sxs-lookup"><span data-stu-id="382eb-172">NOTES</span></span>

* <span data-ttu-id="382eb-173">您也可以使用內建的別名 **spsv** 來參考 **停止服務** 。</span><span class="sxs-lookup"><span data-stu-id="382eb-173">You can also refer to **Stop-Service** by its built-in alias, **spsv** .</span></span> <span data-ttu-id="382eb-174">如需詳細資訊，請參閱 about_Aliases。</span><span class="sxs-lookup"><span data-stu-id="382eb-174">For more information, see about_Aliases.</span></span>

  <span data-ttu-id="382eb-175">只有當目前的使用者有權進行此作業時， **停止服務** 才能控制服務。</span><span class="sxs-lookup"><span data-stu-id="382eb-175">**Stop-Service** can control services only when the current user has permission to do this.</span></span>
<span data-ttu-id="382eb-176">若命令無法正確運作，您可能沒有必要的權限。</span><span class="sxs-lookup"><span data-stu-id="382eb-176">If a command does not work correctly, you might not have the required permissions.</span></span>

  <span data-ttu-id="382eb-177">若要尋找系統上服務的服務名稱和顯示名稱，請輸入 `Get-Service`。</span><span class="sxs-lookup"><span data-stu-id="382eb-177">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
<span data-ttu-id="382eb-178">服務名稱會出現在 [ **名稱** ] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="382eb-178">The service names appear in the **Name** column and the display names appear in the **DisplayName** column.</span></span>

*

## <span data-ttu-id="382eb-179">相關連結</span><span class="sxs-lookup"><span data-stu-id="382eb-179">RELATED LINKS</span></span>

[<span data-ttu-id="382eb-180">Get-Service</span><span class="sxs-lookup"><span data-stu-id="382eb-180">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="382eb-181">New-Service</span><span class="sxs-lookup"><span data-stu-id="382eb-181">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="382eb-182">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="382eb-182">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="382eb-183">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="382eb-183">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="382eb-184">Set-Service</span><span class="sxs-lookup"><span data-stu-id="382eb-184">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="382eb-185">Start-Service</span><span class="sxs-lookup"><span data-stu-id="382eb-185">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="382eb-186">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="382eb-186">Suspend-Service</span></span>](Suspend-Service.md)
