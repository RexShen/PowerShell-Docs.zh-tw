---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: a799326c943b09b5b9c0f9cecfdae3b64e6af409
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201911"
---
# <span data-ttu-id="73247-103">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="73247-103">Resume-Service</span></span>

## <span data-ttu-id="73247-104">概要</span><span class="sxs-lookup"><span data-stu-id="73247-104">SYNOPSIS</span></span>
<span data-ttu-id="73247-105">繼續一或多個擱置 (暫停) 的服務。</span><span class="sxs-lookup"><span data-stu-id="73247-105">Resumes one or more suspended (paused) services.</span></span>

## <span data-ttu-id="73247-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="73247-106">SYNTAX</span></span>

### <span data-ttu-id="73247-107">InputObject (預設值)</span><span class="sxs-lookup"><span data-stu-id="73247-107">InputObject (Default)</span></span>

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="73247-108">預設</span><span class="sxs-lookup"><span data-stu-id="73247-108">Default</span></span>

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="73247-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="73247-109">DisplayName</span></span>

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="73247-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="73247-110">DESCRIPTION</span></span>

<span data-ttu-id="73247-111">**Resume Service 指令程式** 會針對每個指定的服務，將繼續訊息傳送至 Windows 服務控制器。</span><span class="sxs-lookup"><span data-stu-id="73247-111">The **Resume-Service** cmdlet sends a resume message to the Windows Service Controller for each of the specified services.</span></span>
<span data-ttu-id="73247-112">如果服務暫停，則會繼續。</span><span class="sxs-lookup"><span data-stu-id="73247-112">If a service is suspended, it resumes.</span></span>
<span data-ttu-id="73247-113">如果目前正在執行，則會忽略該訊息。</span><span class="sxs-lookup"><span data-stu-id="73247-113">If it is currently running, the message is ignored.</span></span>
<span data-ttu-id="73247-114">您可以依服務的服務名稱或顯示名稱來指定服務，也可以使用 *InputObject* 參數來傳送代表您要繼續之服務的服務物件。</span><span class="sxs-lookup"><span data-stu-id="73247-114">You can specify the services by their service names or display names, or you can use the *InputObject* parameter to pass a service object that represents the services that you want to resume.</span></span>

## <span data-ttu-id="73247-115">範例</span><span class="sxs-lookup"><span data-stu-id="73247-115">EXAMPLES</span></span>

### <span data-ttu-id="73247-116">範例1：在本機電腦上繼續服務</span><span class="sxs-lookup"><span data-stu-id="73247-116">Example 1: Resume a service on the local computer</span></span>

```
PS C:\> Resume-Service "sens"
```

<span data-ttu-id="73247-117">此命令會在本機電腦上繼續執行系統事件通知服務。</span><span class="sxs-lookup"><span data-stu-id="73247-117">This command resumes the System Event Notification service  on the local computer.</span></span>
<span data-ttu-id="73247-118">服務名稱在命令中是以 sens 表示。</span><span class="sxs-lookup"><span data-stu-id="73247-118">The service name is represented in the command by sens.</span></span>
<span data-ttu-id="73247-119">此命令會使用 *Name* 參數來指定服務的服務名稱，但是此命令會省略參數名稱，因為參數名稱是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="73247-119">The command uses the *Name* parameter to specify the service name of the service, but the command omits the parameter name because the parameter name is optional.</span></span>

### <span data-ttu-id="73247-120">範例2：繼續所有已暫停的服務</span><span class="sxs-lookup"><span data-stu-id="73247-120">Example 2: Resume all suspended services</span></span>

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

<span data-ttu-id="73247-121">此命令會繼續電腦上所有已暫停的服務。</span><span class="sxs-lookup"><span data-stu-id="73247-121">This command resumes all of the suspended  services on the computer.</span></span>
<span data-ttu-id="73247-122">Get-Service Cmdlet 命令會取得電腦上的所有服務。</span><span class="sxs-lookup"><span data-stu-id="73247-122">The Get-Service cmdlet command gets all of the services on the computer.</span></span>
<span data-ttu-id="73247-123">管線運算子 (|) 將結果傳遞給 Where-Object Cmdlet，其會選取 [ **狀態** ] 屬性為 [已暫停] 的服務。</span><span class="sxs-lookup"><span data-stu-id="73247-123">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects the services that have a **Status** property of Paused.</span></span>
<span data-ttu-id="73247-124">下一個管線運算子會將結果傳送至 **Resume-Service** ，以繼續暫停的服務。</span><span class="sxs-lookup"><span data-stu-id="73247-124">The next pipeline operator sends the results to **Resume-Service** , which resumes the paused services.</span></span>

<span data-ttu-id="73247-125">在實務上，您會先使用 *WhatIf* 參數來判斷此命令的效果，然後再執行它。</span><span class="sxs-lookup"><span data-stu-id="73247-125">In practice, you would use the *WhatIf* parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="73247-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73247-126">PARAMETERS</span></span>

### <span data-ttu-id="73247-127">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="73247-127">-DisplayName</span></span>

<span data-ttu-id="73247-128">指定要繼續之服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="73247-128">Specifies the display names of the services to be resumed.</span></span>
<span data-ttu-id="73247-129">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="73247-129">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="73247-130">-Exclude</span><span class="sxs-lookup"><span data-stu-id="73247-130">-Exclude</span></span>

<span data-ttu-id="73247-131">指定此 Cmdlet 省略的服務。</span><span class="sxs-lookup"><span data-stu-id="73247-131">Specifies services that this cmdlet omits.</span></span>
<span data-ttu-id="73247-132">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="73247-132">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="73247-133">輸入名稱元素或模式，例如 s\*。</span><span class="sxs-lookup"><span data-stu-id="73247-133">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="73247-134">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="73247-134">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="73247-135">-Include</span><span class="sxs-lookup"><span data-stu-id="73247-135">-Include</span></span>

<span data-ttu-id="73247-136">指定要繼續的服務。</span><span class="sxs-lookup"><span data-stu-id="73247-136">Specifies services to resume.</span></span>
<span data-ttu-id="73247-137">此參數的值會限定 *Name* 參數。</span><span class="sxs-lookup"><span data-stu-id="73247-137">The value of this parameter qualifies *Name* parameter.</span></span>
<span data-ttu-id="73247-138">輸入名稱元素或模式，例如 s\*。</span><span class="sxs-lookup"><span data-stu-id="73247-138">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="73247-139">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="73247-139">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="73247-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="73247-140">-InputObject</span></span>

<span data-ttu-id="73247-141">指定代表要繼續之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="73247-141">Specifies **ServiceController** objects that represent the services to resumed.</span></span>
<span data-ttu-id="73247-142">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="73247-142">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="73247-143">-Name</span><span class="sxs-lookup"><span data-stu-id="73247-143">-Name</span></span>

<span data-ttu-id="73247-144">指定要繼續之服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="73247-144">Specifies the service names of the services to be resumed.</span></span>

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

### <span data-ttu-id="73247-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="73247-145">-PassThru</span></span>

<span data-ttu-id="73247-146">傳回代表服務的物件。</span><span class="sxs-lookup"><span data-stu-id="73247-146">Returns an object that represents the service.</span></span>
<span data-ttu-id="73247-147">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="73247-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="73247-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="73247-148">-Confirm</span></span>

<span data-ttu-id="73247-149">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="73247-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="73247-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="73247-150">-WhatIf</span></span>

<span data-ttu-id="73247-151">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="73247-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="73247-152">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="73247-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="73247-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73247-153">CommonParameters</span></span>

<span data-ttu-id="73247-154">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="73247-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73247-155">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="73247-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="73247-156">輸入</span><span class="sxs-lookup"><span data-stu-id="73247-156">INPUTS</span></span>

### <span data-ttu-id="73247-157">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="73247-157">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="73247-158">您可以使用管線將服務物件或包含服務名稱的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="73247-158">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="73247-159">輸出</span><span class="sxs-lookup"><span data-stu-id="73247-159">OUTPUTS</span></span>

### <span data-ttu-id="73247-160">無、System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="73247-160">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="73247-161">如果您指定 *PassThru* 參數，此 Cmdlet 會產生代表已繼續服務的 **system.serviceprocess.dll ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="73247-161">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the resumed service, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="73247-162">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="73247-162">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="73247-163">注意</span><span class="sxs-lookup"><span data-stu-id="73247-163">NOTES</span></span>

* <span data-ttu-id="73247-164">已暫停之服務的狀態已暫停。</span><span class="sxs-lookup"><span data-stu-id="73247-164">The status of services that have been suspended is Paused.</span></span> <span data-ttu-id="73247-165">當服務繼續執行時，其狀態會是 [正在執行]。</span><span class="sxs-lookup"><span data-stu-id="73247-165">When services are resumed, their status is Running.</span></span>
* <span data-ttu-id="73247-166">**Resume-服務** 只有在目前的使用者有權執行此動作時，才能控制服務。</span><span class="sxs-lookup"><span data-stu-id="73247-166">**Resume-Service** can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="73247-167">若命令無法正確運作，您可能沒有必要的權限。</span><span class="sxs-lookup"><span data-stu-id="73247-167">If a command does not work correctly, you might not have the required permissions.</span></span>
* <span data-ttu-id="73247-168">若要尋找系統上服務的服務名稱和顯示名稱，請輸入 `Get-Service`。</span><span class="sxs-lookup"><span data-stu-id="73247-168">To find the service names and display names of the services on your system, type `Get-Service`.</span></span> <span data-ttu-id="73247-169">服務名稱會出現在 [ **名稱** ] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="73247-169">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="73247-170">相關連結</span><span class="sxs-lookup"><span data-stu-id="73247-170">RELATED LINKS</span></span>

[<span data-ttu-id="73247-171">Get-Service</span><span class="sxs-lookup"><span data-stu-id="73247-171">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="73247-172">New-Service</span><span class="sxs-lookup"><span data-stu-id="73247-172">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="73247-173">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="73247-173">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="73247-174">Set-Service</span><span class="sxs-lookup"><span data-stu-id="73247-174">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="73247-175">Start-Service</span><span class="sxs-lookup"><span data-stu-id="73247-175">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="73247-176">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="73247-176">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="73247-177">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="73247-177">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="73247-178">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="73247-178">Remove-Service</span></span>](Remove-Service.md)