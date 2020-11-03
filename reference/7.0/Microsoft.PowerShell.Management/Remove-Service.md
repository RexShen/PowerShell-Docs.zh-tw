---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: 13ef4d483ad91b38c175f850da9cd4d1da771935
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201163"
---
# <span data-ttu-id="98ee9-103">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="98ee9-103">Remove-Service</span></span>

## <span data-ttu-id="98ee9-104">概要</span><span class="sxs-lookup"><span data-stu-id="98ee9-104">SYNOPSIS</span></span>
<span data-ttu-id="98ee9-105">移除 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="98ee9-105">Removes a Windows service.</span></span>

## <span data-ttu-id="98ee9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="98ee9-106">SYNTAX</span></span>

### <span data-ttu-id="98ee9-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="98ee9-107">Name (Default)</span></span>

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="98ee9-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="98ee9-108">InputObject</span></span>

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="98ee9-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="98ee9-109">DESCRIPTION</span></span>

<span data-ttu-id="98ee9-110">此 `Remove-Service` Cmdlet 會移除登錄和服務資料庫中的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="98ee9-110">The `Remove-Service` cmdlet removes a Windows service in the registry and in the service database.</span></span>

<span data-ttu-id="98ee9-111">`Remove-Service`Cmdlet 是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="98ee9-111">The `Remove-Service` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="98ee9-112">範例</span><span class="sxs-lookup"><span data-stu-id="98ee9-112">EXAMPLES</span></span>

### <span data-ttu-id="98ee9-113">範例1：移除服務</span><span class="sxs-lookup"><span data-stu-id="98ee9-113">Example 1: Remove a service</span></span>

<span data-ttu-id="98ee9-114">這會移除名為 TestService 的服務。</span><span class="sxs-lookup"><span data-stu-id="98ee9-114">This removes a service named TestService.</span></span>

```powershell
Remove-Service -Name "TestService"
```

### <span data-ttu-id="98ee9-115">範例2：使用顯示名稱移除服務</span><span class="sxs-lookup"><span data-stu-id="98ee9-115">Example 2: Remove a service using the display name</span></span>

<span data-ttu-id="98ee9-116">此範例會移除名為 TestService 的服務。</span><span class="sxs-lookup"><span data-stu-id="98ee9-116">This example removes a service named TestService.</span></span> <span data-ttu-id="98ee9-117">此命令 `Get-Service` 會使用來取得物件，該物件代表使用顯示名稱的 TestService 服務。</span><span class="sxs-lookup"><span data-stu-id="98ee9-117">The command uses `Get-Service` to get an object that represents the TestService service using the display name.</span></span> <span data-ttu-id="98ee9-118">管線運算子 (`|`) 將物件輸送至 `Remove-Service` ，以移除服務。</span><span class="sxs-lookup"><span data-stu-id="98ee9-118">The pipeline operator (`|`) pipes the object to `Remove-Service`, which removes the service.</span></span>

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## <span data-ttu-id="98ee9-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="98ee9-119">PARAMETERS</span></span>

### <span data-ttu-id="98ee9-120">-InputObject</span><span class="sxs-lookup"><span data-stu-id="98ee9-120">-InputObject</span></span>

<span data-ttu-id="98ee9-121">指定代表要移除之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="98ee9-121">Specifies **ServiceController** objects that represent the services to remove.</span></span> <span data-ttu-id="98ee9-122">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="98ee9-122">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="98ee9-123">-Name</span><span class="sxs-lookup"><span data-stu-id="98ee9-123">-Name</span></span>

<span data-ttu-id="98ee9-124">指定要移除之服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="98ee9-124">Specifies the service names of the services to remove.</span></span> <span data-ttu-id="98ee9-125">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="98ee9-125">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="98ee9-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="98ee9-126">-Confirm</span></span>

<span data-ttu-id="98ee9-127">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="98ee9-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="98ee9-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="98ee9-128">-WhatIf</span></span>

<span data-ttu-id="98ee9-129">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="98ee9-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="98ee9-130">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="98ee9-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="98ee9-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="98ee9-131">CommonParameters</span></span>

<span data-ttu-id="98ee9-132">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="98ee9-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="98ee9-133">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="98ee9-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="98ee9-134">輸入</span><span class="sxs-lookup"><span data-stu-id="98ee9-134">INPUTS</span></span>

### <span data-ttu-id="98ee9-135">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="98ee9-135">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="98ee9-136">您可以使用管線將服務物件或包含服務名稱的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="98ee9-136">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="98ee9-137">輸出</span><span class="sxs-lookup"><span data-stu-id="98ee9-137">OUTPUTS</span></span>

### <span data-ttu-id="98ee9-138">無</span><span class="sxs-lookup"><span data-stu-id="98ee9-138">None</span></span>

<span data-ttu-id="98ee9-139">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="98ee9-139">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="98ee9-140">注意</span><span class="sxs-lookup"><span data-stu-id="98ee9-140">NOTES</span></span>

<span data-ttu-id="98ee9-141">若要執行此 Cmdlet，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="98ee9-141">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="98ee9-142">相關連結</span><span class="sxs-lookup"><span data-stu-id="98ee9-142">RELATED LINKS</span></span>

[<span data-ttu-id="98ee9-143">Get-Service</span><span class="sxs-lookup"><span data-stu-id="98ee9-143">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="98ee9-144">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="98ee9-144">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="98ee9-145">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="98ee9-145">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="98ee9-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="98ee9-146">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="98ee9-147">Start-Service</span><span class="sxs-lookup"><span data-stu-id="98ee9-147">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="98ee9-148">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="98ee9-148">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="98ee9-149">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="98ee9-149">Suspend-Service</span></span>](Suspend-Service.md)
