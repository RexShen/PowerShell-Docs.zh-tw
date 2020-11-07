---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: dbe084b553587ba09a2ce4b76b0c662915c59808
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347341"
---
# <span data-ttu-id="3b0b6-103">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="3b0b6-103">Remove-Service</span></span>

## <span data-ttu-id="3b0b6-104">概要</span><span class="sxs-lookup"><span data-stu-id="3b0b6-104">SYNOPSIS</span></span>
<span data-ttu-id="3b0b6-105">移除 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-105">Removes a Windows service.</span></span>

## <span data-ttu-id="3b0b6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3b0b6-106">SYNTAX</span></span>

### <span data-ttu-id="3b0b6-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="3b0b6-107">Name (Default)</span></span>

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3b0b6-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="3b0b6-108">InputObject</span></span>

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3b0b6-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3b0b6-109">DESCRIPTION</span></span>

<span data-ttu-id="3b0b6-110">此 `Remove-Service` Cmdlet 會移除登錄和服務資料庫中的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-110">The `Remove-Service` cmdlet removes a Windows service in the registry and in the service database.</span></span>

<span data-ttu-id="3b0b6-111">`Remove-Service`Cmdlet 是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-111">The `Remove-Service` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="3b0b6-112">範例</span><span class="sxs-lookup"><span data-stu-id="3b0b6-112">EXAMPLES</span></span>

### <span data-ttu-id="3b0b6-113">範例1：移除服務</span><span class="sxs-lookup"><span data-stu-id="3b0b6-113">Example 1: Remove a service</span></span>

<span data-ttu-id="3b0b6-114">這會移除名為 TestService 的服務。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-114">This removes a service named TestService.</span></span>

```powershell
Remove-Service -Name "TestService"
```

### <span data-ttu-id="3b0b6-115">範例2：使用顯示名稱移除服務</span><span class="sxs-lookup"><span data-stu-id="3b0b6-115">Example 2: Remove a service using the display name</span></span>

<span data-ttu-id="3b0b6-116">此範例會移除名為 TestService 的服務。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-116">This example removes a service named TestService.</span></span> <span data-ttu-id="3b0b6-117">此命令 `Get-Service` 會使用來取得物件，該物件代表使用顯示名稱的 TestService 服務。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-117">The command uses `Get-Service` to get an object that represents the TestService service using the display name.</span></span> <span data-ttu-id="3b0b6-118">管線運算子 (`|`) 將物件輸送至 `Remove-Service` ，以移除服務。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-118">The pipeline operator (`|`) pipes the object to `Remove-Service`, which removes the service.</span></span>

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## <span data-ttu-id="3b0b6-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3b0b6-119">PARAMETERS</span></span>

### <span data-ttu-id="3b0b6-120">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3b0b6-120">-InputObject</span></span>

<span data-ttu-id="3b0b6-121">指定代表要移除之服務的 **ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-121">Specifies **ServiceController** objects that represent the services to remove.</span></span> <span data-ttu-id="3b0b6-122">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-122">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="3b0b6-123">-Name</span><span class="sxs-lookup"><span data-stu-id="3b0b6-123">-Name</span></span>

<span data-ttu-id="3b0b6-124">指定要移除之服務的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-124">Specifies the service names of the services to remove.</span></span> <span data-ttu-id="3b0b6-125">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-125">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="3b0b6-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3b0b6-126">-Confirm</span></span>

<span data-ttu-id="3b0b6-127">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3b0b6-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3b0b6-128">-WhatIf</span></span>

<span data-ttu-id="3b0b6-129">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="3b0b6-130">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3b0b6-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3b0b6-131">CommonParameters</span></span>

<span data-ttu-id="3b0b6-132">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3b0b6-133">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3b0b6-134">輸入</span><span class="sxs-lookup"><span data-stu-id="3b0b6-134">INPUTS</span></span>

### <span data-ttu-id="3b0b6-135">System.ServiceProcess.ServiceController、System.String</span><span class="sxs-lookup"><span data-stu-id="3b0b6-135">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="3b0b6-136">您可以使用管線將服務物件或包含服務名稱的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-136">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="3b0b6-137">輸出</span><span class="sxs-lookup"><span data-stu-id="3b0b6-137">OUTPUTS</span></span>

### <span data-ttu-id="3b0b6-138">None</span><span class="sxs-lookup"><span data-stu-id="3b0b6-138">None</span></span>

<span data-ttu-id="3b0b6-139">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-139">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="3b0b6-140">注意</span><span class="sxs-lookup"><span data-stu-id="3b0b6-140">NOTES</span></span>

<span data-ttu-id="3b0b6-141">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-141">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="3b0b6-142">若要執行此 Cmdlet，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3b0b6-142">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="3b0b6-143">相關連結</span><span class="sxs-lookup"><span data-stu-id="3b0b6-143">RELATED LINKS</span></span>

[<span data-ttu-id="3b0b6-144">Get-Service</span><span class="sxs-lookup"><span data-stu-id="3b0b6-144">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="3b0b6-145">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="3b0b6-145">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="3b0b6-146">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="3b0b6-146">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="3b0b6-147">Set-Service</span><span class="sxs-lookup"><span data-stu-id="3b0b6-147">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="3b0b6-148">Start-Service</span><span class="sxs-lookup"><span data-stu-id="3b0b6-148">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="3b0b6-149">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="3b0b6-149">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="3b0b6-150">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="3b0b6-150">Suspend-Service</span></span>](Suspend-Service.md)
