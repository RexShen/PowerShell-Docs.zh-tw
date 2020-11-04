---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 529edca36e63d9a72d2a300ebc8c6c26033db0d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203460"
---
# <span data-ttu-id="26673-103">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="26673-103">Suspend-Service</span></span>

## <span data-ttu-id="26673-104">概要</span><span class="sxs-lookup"><span data-stu-id="26673-104">SYNOPSIS</span></span>
<span data-ttu-id="26673-105">暫停一或多個執行中的服務。</span><span class="sxs-lookup"><span data-stu-id="26673-105">Suspends (pauses) one or more running services.</span></span>

## <span data-ttu-id="26673-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="26673-106">SYNTAX</span></span>

### <span data-ttu-id="26673-107">InputObject (預設值)</span><span class="sxs-lookup"><span data-stu-id="26673-107">InputObject (Default)</span></span>

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="26673-108">預設</span><span class="sxs-lookup"><span data-stu-id="26673-108">Default</span></span>

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="26673-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="26673-109">DisplayName</span></span>

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="26673-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="26673-110">DESCRIPTION</span></span>

<span data-ttu-id="26673-111">**暫止服務指令程式** 會針對每個指定的服務，將暫止訊息傳送至 Windows 服務控制器。</span><span class="sxs-lookup"><span data-stu-id="26673-111">The **Suspend-Service** cmdlet sends a suspend message to the Windows Service Controller for each of the specified services.</span></span>
<span data-ttu-id="26673-112">暫止時，服務仍在執行中，但它的動作會在繼續之前停止，例如使用 Resume-Service Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26673-112">While suspended, the service is still running, but its action is stopped until resumed, such as by usingthe Resume-Service cmdlet.</span></span>
<span data-ttu-id="26673-113">您可以依服務的服務名稱或顯示名稱來指定服務，也可以使用 *InputObject* 參數來傳送代表您要暫停之服務的服務物件。</span><span class="sxs-lookup"><span data-stu-id="26673-113">You can specify the services by their service names or display names, or you can use the *InputObject* parameter to pass a service object that represents the services that you want to suspend.</span></span>

## <span data-ttu-id="26673-114">範例</span><span class="sxs-lookup"><span data-stu-id="26673-114">EXAMPLES</span></span>

### <span data-ttu-id="26673-115">範例1：暫止服務</span><span class="sxs-lookup"><span data-stu-id="26673-115">Example 1: Suspend a service</span></span>

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

<span data-ttu-id="26673-116">此命令會暫停本機電腦上的 Telnet service (Tlntsvr) 服務。</span><span class="sxs-lookup"><span data-stu-id="26673-116">This command suspends the Telnet service (Tlntsvr) service on the local computer.</span></span>

### <span data-ttu-id="26673-117">範例2：顯示擱置服務時所發生的情況</span><span class="sxs-lookup"><span data-stu-id="26673-117">Example 2: Display what would happen if you suspend services</span></span>

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

<span data-ttu-id="26673-118">此命令會指出當您暫停服務名稱開頭為 lanman 的服務時，會發生什麼情況。</span><span class="sxs-lookup"><span data-stu-id="26673-118">This command tells what would happen if you suspended the services that have a service name that starts with lanman.</span></span>
<span data-ttu-id="26673-119">若要暫停服務，請重新執行沒有 *WhatIf* 參數的命令。</span><span class="sxs-lookup"><span data-stu-id="26673-119">To suspend the services, rerun the command without the *WhatIf* parameter.</span></span>

### <span data-ttu-id="26673-120">範例3：取得和暫停服務</span><span class="sxs-lookup"><span data-stu-id="26673-120">Example 3: Get and suspend a service</span></span>

```
PS C:\> Get-Service schedule | Suspend-Service
```

<span data-ttu-id="26673-121">此命令會使用 **get-help** Cmdlet 來取得物件，該物件代表電腦上 (排程) 服務工作排程器。</span><span class="sxs-lookup"><span data-stu-id="26673-121">This command uses the **Get-Service** cmdlet to get an object that represents the Task Scheduler (Schedule) service on the computer.</span></span>
<span data-ttu-id="26673-122">管線運算子 (|) 將結果傳遞至擱置服務的擱置 **服務** ，這會暫停服務。</span><span class="sxs-lookup"><span data-stu-id="26673-122">The pipeline operator (|) passes the result to **Suspend-Service** , which suspends the service.</span></span>

### <span data-ttu-id="26673-123">範例4：暫停所有可暫停的服務</span><span class="sxs-lookup"><span data-stu-id="26673-123">Example 4: Suspend all services that can be suspended</span></span>

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

<span data-ttu-id="26673-124">此命令會暫停電腦上所有可暫停的服務。</span><span class="sxs-lookup"><span data-stu-id="26673-124">This command suspends all of the services on the computer that can be suspended.</span></span>
<span data-ttu-id="26673-125">它會使用 **get-help** 來取得代表電腦上之服務的物件。</span><span class="sxs-lookup"><span data-stu-id="26673-125">It uses **Get-Service** to get objects that represent the services on the computer.</span></span>
<span data-ttu-id="26673-126">管線運算子會將結果傳遞至 Where-Object Cmdlet，此 Cmdlet 只會選取具有 **CanPauseAndContinue** 屬性 $True 值的服務。</span><span class="sxs-lookup"><span data-stu-id="26673-126">The pipeline operator passes the results to the Where-Object cmdlet, which selects only the services that have a value of $True for the **CanPauseAndContinue** property.</span></span>
<span data-ttu-id="26673-127">另一個管線運算子會將結果傳遞至 **暫止的服務** 。</span><span class="sxs-lookup"><span data-stu-id="26673-127">Another pipeline operator passes the results to **Suspend-Service** .</span></span>
<span data-ttu-id="26673-128">*Confirm* 參數會在暫停每個服務之前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="26673-128">The *Confirm* parameter prompts you for confirmation before suspending each of the services.</span></span>

## <span data-ttu-id="26673-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="26673-129">PARAMETERS</span></span>

### <span data-ttu-id="26673-130">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="26673-130">-DisplayName</span></span>

<span data-ttu-id="26673-131">指定要暫停之服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="26673-131">Specifies the display names of the services to be suspended.</span></span>
<span data-ttu-id="26673-132">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="26673-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="26673-133">-Exclude</span><span class="sxs-lookup"><span data-stu-id="26673-133">-Exclude</span></span>

<span data-ttu-id="26673-134">指定要從指定服務中省略的服務。</span><span class="sxs-lookup"><span data-stu-id="26673-134">Specifies services to omit from the specified services.</span></span>
<span data-ttu-id="26673-135">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="26673-135">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="26673-136">輸入名稱元素或模式，例如 "s\*"。</span><span class="sxs-lookup"><span data-stu-id="26673-136">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="26673-137">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="26673-137">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="26673-138">-Include</span><span class="sxs-lookup"><span data-stu-id="26673-138">-Include</span></span>

<span data-ttu-id="26673-139">指定要暫停的服務。</span><span class="sxs-lookup"><span data-stu-id="26673-139">Specifies services to suspend.</span></span>
<span data-ttu-id="26673-140">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="26673-140">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="26673-141">輸入名稱元素或模式，例如 "s\*"。</span><span class="sxs-lookup"><span data-stu-id="26673-141">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="26673-142">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="26673-142">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="26673-143">-InputObject</span><span class="sxs-lookup"><span data-stu-id="26673-143">-InputObject</span></span>

<span data-ttu-id="26673-144">指定代表要暫停之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="26673-144">Specifies **ServiceController** objects that represent the services to suspend.</span></span>
<span data-ttu-id="26673-145">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="26673-145">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="26673-146">-Name</span><span class="sxs-lookup"><span data-stu-id="26673-146">-Name</span></span>

<span data-ttu-id="26673-147">指定要暫停之服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="26673-147">Specifies the service names of the services to suspend.</span></span>
<span data-ttu-id="26673-148">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="26673-148">Wildcard characters are permitted.</span></span>

<span data-ttu-id="26673-149">參數名稱為選擇性。</span><span class="sxs-lookup"><span data-stu-id="26673-149">The parameter name is optional.</span></span>
<span data-ttu-id="26673-150">您可以使用 *名稱* 或其別名、 *ServiceName* ，也可以省略參數名稱。</span><span class="sxs-lookup"><span data-stu-id="26673-150">You can use *Name* or its alias, *ServiceName* , or you can omit the parameter name.</span></span>

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

### <span data-ttu-id="26673-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="26673-151">-PassThru</span></span>

<span data-ttu-id="26673-152">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="26673-152">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="26673-153">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="26673-153">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="26673-154">-Confirm</span><span class="sxs-lookup"><span data-stu-id="26673-154">-Confirm</span></span>

<span data-ttu-id="26673-155">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="26673-155">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="26673-156">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="26673-156">-WhatIf</span></span>

<span data-ttu-id="26673-157">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="26673-157">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="26673-158">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="26673-158">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="26673-159">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="26673-159">CommonParameters</span></span>

<span data-ttu-id="26673-160">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="26673-160">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="26673-161">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="26673-161">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="26673-162">輸入</span><span class="sxs-lookup"><span data-stu-id="26673-162">INPUTS</span></span>

### <span data-ttu-id="26673-163">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="26673-163">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="26673-164">您可以使用管線將服務物件或包含服務名稱的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26673-164">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="26673-165">輸出</span><span class="sxs-lookup"><span data-stu-id="26673-165">OUTPUTS</span></span>

### <span data-ttu-id="26673-166">無、System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="26673-166">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="26673-167">如果您指定 *PassThru* 參數，此 Cmdlet 會產生代表服務的 **system.serviceprocess.dll ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="26673-167">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="26673-168">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="26673-168">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="26673-169">注意</span><span class="sxs-lookup"><span data-stu-id="26673-169">NOTES</span></span>

* <span data-ttu-id="26673-170">只有當目前的使用者有權進行此作業時， **暫停服務** 才能控制服務。</span><span class="sxs-lookup"><span data-stu-id="26673-170">**Suspend-Service** can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="26673-171">若命令無法正確運作，您可能沒有必要的權限。</span><span class="sxs-lookup"><span data-stu-id="26673-171">If a command does not work correctly, you might not have the required permissions.</span></span>
* <span data-ttu-id="26673-172">**暫止服務** 只能暫停支援暫止和繼續的服務。</span><span class="sxs-lookup"><span data-stu-id="26673-172">**Suspend-Service** can suspend only services that support being suspended and resumed.</span></span> <span data-ttu-id="26673-173">若要判斷特定服務是否可以暫止，請使用 Get-Service Cmdlet 搭配 **CanPauseAndContinue** 屬性。</span><span class="sxs-lookup"><span data-stu-id="26673-173">To determine whether a particular service can be suspended, use the Get-Service cmdlet together with the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="26673-174">例如： `Get-Service wmi | Format-List Name, CanPauseAndContinue` 。</span><span class="sxs-lookup"><span data-stu-id="26673-174">For example, `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span></span> <span data-ttu-id="26673-175">若要尋找電腦上所有可暫停的服務，請輸入 `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` 。</span><span class="sxs-lookup"><span data-stu-id="26673-175">To find all services on the computer that can be suspended, type `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}`.</span></span>
* <span data-ttu-id="26673-176">若要尋找系統上服務的服務名稱和顯示名稱，請輸入 **Get-service** 。</span><span class="sxs-lookup"><span data-stu-id="26673-176">To find the service names and display names of the services on your system, type **Get-Service** .</span></span> <span data-ttu-id="26673-177">服務名稱會出現在 [ **名稱** ] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="26673-177">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="26673-178">相關連結</span><span class="sxs-lookup"><span data-stu-id="26673-178">RELATED LINKS</span></span>

[<span data-ttu-id="26673-179">Get-Service</span><span class="sxs-lookup"><span data-stu-id="26673-179">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="26673-180">New-Service</span><span class="sxs-lookup"><span data-stu-id="26673-180">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="26673-181">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="26673-181">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="26673-182">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="26673-182">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="26673-183">Set-Service</span><span class="sxs-lookup"><span data-stu-id="26673-183">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="26673-184">Start-Service</span><span class="sxs-lookup"><span data-stu-id="26673-184">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="26673-185">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="26673-185">Stop-Service</span></span>](Stop-Service.md)