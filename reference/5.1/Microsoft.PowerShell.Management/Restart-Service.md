---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Service
ms.openlocfilehash: b5af4f55166993e54048dd76bb8345550718c170
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203527"
---
# <span data-ttu-id="82f89-103">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="82f89-103">Restart-Service</span></span>

## <span data-ttu-id="82f89-104">概要</span><span class="sxs-lookup"><span data-stu-id="82f89-104">SYNOPSIS</span></span>
<span data-ttu-id="82f89-105">停止然後啟動一或多個服務。</span><span class="sxs-lookup"><span data-stu-id="82f89-105">Stops and then starts one or more services.</span></span>

## <span data-ttu-id="82f89-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="82f89-106">SYNTAX</span></span>

### <span data-ttu-id="82f89-107">InputObject (預設值)</span><span class="sxs-lookup"><span data-stu-id="82f89-107">InputObject (Default)</span></span>

```
Restart-Service [-Force] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="82f89-108">預設</span><span class="sxs-lookup"><span data-stu-id="82f89-108">Default</span></span>

```
Restart-Service [-Force] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="82f89-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="82f89-109">DisplayName</span></span>

```
Restart-Service [-Force] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="82f89-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="82f89-110">DESCRIPTION</span></span>

<span data-ttu-id="82f89-111">**Restart-Service** Cmdlet 可針對指定的服務向 Windows 服務控制器傳送停止訊息，然後再傳送啟動訊息。</span><span class="sxs-lookup"><span data-stu-id="82f89-111">The **Restart-Service** cmdlet sends a stop message and then a start message to the Windows Service Controller for a specified service.</span></span>
<span data-ttu-id="82f89-112">如果服務已停止，它會啟動而不會以錯誤訊息通知您。</span><span class="sxs-lookup"><span data-stu-id="82f89-112">If a service was already stopped, it is started without notifying you of an error.</span></span>
<span data-ttu-id="82f89-113">您可以依服務的服務名稱或顯示名稱來指定服務，或是使用 *InputObject* 參數來傳送代表每個要重新啟動之服務的物件。</span><span class="sxs-lookup"><span data-stu-id="82f89-113">You can specify the services by their service names or display names, or you can use the *InputObject* parameter to pass an object that represents each service that you want to restart.</span></span>

## <span data-ttu-id="82f89-114">範例</span><span class="sxs-lookup"><span data-stu-id="82f89-114">EXAMPLES</span></span>

### <span data-ttu-id="82f89-115">範例 1：重新啟動本機電腦上的服務</span><span class="sxs-lookup"><span data-stu-id="82f89-115">Example 1: Restart a service on the local computer</span></span>

```powershell
PS C:\> Restart-Service -Name winmgmt
```

<span data-ttu-id="82f89-116">此命令會重新啟動本機電腦上的 Windows Management Instrumentation 服務 (WinMgmt)。</span><span class="sxs-lookup"><span data-stu-id="82f89-116">This command restarts the Windows Management Instrumentation service (WinMgmt) on the local computer.</span></span>

### <span data-ttu-id="82f89-117">範例 2：排除服務</span><span class="sxs-lookup"><span data-stu-id="82f89-117">Example 2: Exclude a service</span></span>

```powershell
PS C:\> Restart-Service -DisplayName "net*" -Exclude "net logon"
```

<span data-ttu-id="82f89-118">此命令會重新啟動除了 Net Logon 服務之外，所有顯示名稱開頭為 Net 的服務。</span><span class="sxs-lookup"><span data-stu-id="82f89-118">This command restarts the services that have a display name that starts with Net, except for the Net Logon service.</span></span>

### <span data-ttu-id="82f89-119">範例 3：啟動所有已停止的網路服務</span><span class="sxs-lookup"><span data-stu-id="82f89-119">Example 3: Start all stopped network services</span></span>

```powershell
PS C:\> Get-Service -Name "net*" | Where-Object {$_.Status -eq "Stopped"} | Restart-Service
```

<span data-ttu-id="82f89-120">此命令啟動電腦上所有已停止的網路服務。</span><span class="sxs-lookup"><span data-stu-id="82f89-120">This command starts all of the stopped network services on the computer.</span></span>

<span data-ttu-id="82f89-121">此命令會使用 Get-Service Cmdlet 取得代表服務名稱開頭為 net 之服務的物件。</span><span class="sxs-lookup"><span data-stu-id="82f89-121">This command uses the Get-Service cmdlet to get objects that represent the services whose service name starts with net.</span></span>
<span data-ttu-id="82f89-122">管線運算子 (|) 會將服務物件傳送至 Where-Object Cmdlet，它只會選取狀態為 stopped 的服務。</span><span class="sxs-lookup"><span data-stu-id="82f89-122">The pipeline operator (|) sends the services object to the Where-Object cmdlet, which selects only the services that have a status of stopped.</span></span>
<span data-ttu-id="82f89-123">另一個管線運算子會將選取的服務傳送至 **Restart-Service** 。</span><span class="sxs-lookup"><span data-stu-id="82f89-123">Another pipeline operator sends the selected services to **Restart-Service** .</span></span>

<span data-ttu-id="82f89-124">在實務上，您會先使用 *WhatIf* 參數來判斷此命令的效果，然後再執行它。</span><span class="sxs-lookup"><span data-stu-id="82f89-124">In practice, you would use the *WhatIf* parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="82f89-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="82f89-125">PARAMETERS</span></span>

### <span data-ttu-id="82f89-126">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="82f89-126">-DisplayName</span></span>

<span data-ttu-id="82f89-127">指定要重新啟動之服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="82f89-127">Specifies the display names of services to restarted.</span></span>
<span data-ttu-id="82f89-128">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="82f89-128">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="82f89-129">-Exclude</span><span class="sxs-lookup"><span data-stu-id="82f89-129">-Exclude</span></span>

<span data-ttu-id="82f89-130">指定此 Cmdlet 省略的服務。</span><span class="sxs-lookup"><span data-stu-id="82f89-130">Specifies services that this cmdlet omits.</span></span>
<span data-ttu-id="82f89-131">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="82f89-131">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="82f89-132">輸入名稱元素或模式，例如 s\*。</span><span class="sxs-lookup"><span data-stu-id="82f89-132">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="82f89-133">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="82f89-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="82f89-134">-Force</span><span class="sxs-lookup"><span data-stu-id="82f89-134">-Force</span></span>

<span data-ttu-id="82f89-135">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="82f89-135">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="82f89-136">-Include</span><span class="sxs-lookup"><span data-stu-id="82f89-136">-Include</span></span>

<span data-ttu-id="82f89-137">指定此 Cmdlet 重新開機的服務。</span><span class="sxs-lookup"><span data-stu-id="82f89-137">Specifies services that this cmdlet restarts.</span></span>
<span data-ttu-id="82f89-138">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="82f89-138">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="82f89-139">輸入名稱元素或模式，例如 s\*。</span><span class="sxs-lookup"><span data-stu-id="82f89-139">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="82f89-140">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="82f89-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="82f89-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="82f89-141">-InputObject</span></span>

<span data-ttu-id="82f89-142">指定代表要重新開機之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="82f89-142">Specifies **ServiceController** objects that represent the services to restart.</span></span>
<span data-ttu-id="82f89-143">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="82f89-143">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="82f89-144">-Name</span><span class="sxs-lookup"><span data-stu-id="82f89-144">-Name</span></span>

<span data-ttu-id="82f89-145">指定要重新啟動之服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="82f89-145">Specifies the service names of the services to restart.</span></span>

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

### <span data-ttu-id="82f89-146">-PassThru</span><span class="sxs-lookup"><span data-stu-id="82f89-146">-PassThru</span></span>

<span data-ttu-id="82f89-147">傳回代表服務的物件。</span><span class="sxs-lookup"><span data-stu-id="82f89-147">Returns an object that represents the service.</span></span>
<span data-ttu-id="82f89-148">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="82f89-148">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="82f89-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="82f89-149">-Confirm</span></span>

<span data-ttu-id="82f89-150">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="82f89-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="82f89-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="82f89-151">-WhatIf</span></span>

<span data-ttu-id="82f89-152">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="82f89-152">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="82f89-153">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="82f89-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="82f89-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82f89-154">CommonParameters</span></span>

<span data-ttu-id="82f89-155">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="82f89-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82f89-156">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="82f89-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82f89-157">輸入</span><span class="sxs-lookup"><span data-stu-id="82f89-157">INPUTS</span></span>

### <span data-ttu-id="82f89-158">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="82f89-158">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="82f89-159">您可以使用管線將服務物件或包含服務名稱的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="82f89-159">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="82f89-160">輸出</span><span class="sxs-lookup"><span data-stu-id="82f89-160">OUTPUTS</span></span>

### <span data-ttu-id="82f89-161">無、System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="82f89-161">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="82f89-162">如果您指定 *PassThru* 參數，此 Cmdlet 會產生代表重新啟動之服務的 **System.ServiceProcess.ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="82f89-162">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the restarted service, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="82f89-163">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="82f89-163">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="82f89-164">注意</span><span class="sxs-lookup"><span data-stu-id="82f89-164">NOTES</span></span>

* <span data-ttu-id="82f89-165">只有當目前的使用者具有控制服務的權限時， **Restart-Service** 才能控制服務。</span><span class="sxs-lookup"><span data-stu-id="82f89-165">**Restart-Service** can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="82f89-166">若命令無法正確運作，您可能沒有必要的權限。</span><span class="sxs-lookup"><span data-stu-id="82f89-166">If a command does not work correctly, you might not have the required permissions.</span></span>
* <span data-ttu-id="82f89-167">若要尋找系統上服務的服務名稱和顯示名稱，請輸入 **Get service** 。</span><span class="sxs-lookup"><span data-stu-id="82f89-167">To find the service names and display names of the services on your system, type **Get-Service** ".</span></span> <span data-ttu-id="82f89-168">服務名稱會出現在 [ **名稱** ] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="82f89-168">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="82f89-169">相關連結</span><span class="sxs-lookup"><span data-stu-id="82f89-169">RELATED LINKS</span></span>

[<span data-ttu-id="82f89-170">Get-Service</span><span class="sxs-lookup"><span data-stu-id="82f89-170">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="82f89-171">New-Service</span><span class="sxs-lookup"><span data-stu-id="82f89-171">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="82f89-172">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="82f89-172">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="82f89-173">Set-Service</span><span class="sxs-lookup"><span data-stu-id="82f89-173">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="82f89-174">Start-Service</span><span class="sxs-lookup"><span data-stu-id="82f89-174">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="82f89-175">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="82f89-175">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="82f89-176">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="82f89-176">Suspend-Service</span></span>](Suspend-Service.md)