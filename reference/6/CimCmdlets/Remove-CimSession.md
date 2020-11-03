---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: 4c7de7a8ad3ae2a9e69cf4a00f9b9140a4294f4e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203852"
---
# <span data-ttu-id="fbd66-103">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="fbd66-103">Remove-CimSession</span></span>

## <span data-ttu-id="fbd66-104">概要</span><span class="sxs-lookup"><span data-stu-id="fbd66-104">SYNOPSIS</span></span>
<span data-ttu-id="fbd66-105">移除一或多個 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="fbd66-105">Removes one or more CIM sessions.</span></span>

## <span data-ttu-id="fbd66-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fbd66-106">SYNTAX</span></span>

### <span data-ttu-id="fbd66-107">CimSessionSet (預設) </span><span class="sxs-lookup"><span data-stu-id="fbd66-107">CimSessionSet (Default)</span></span>

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fbd66-108">ComputerNameSet</span><span class="sxs-lookup"><span data-stu-id="fbd66-108">ComputerNameSet</span></span>

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fbd66-109">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="fbd66-109">SessionIdSet</span></span>

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fbd66-110">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="fbd66-110">InstanceIdSet</span></span>

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fbd66-111">NameSet</span><span class="sxs-lookup"><span data-stu-id="fbd66-111">NameSet</span></span>

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fbd66-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fbd66-112">DESCRIPTION</span></span>

<span data-ttu-id="fbd66-113">此 `Remove-CimSession` Cmdlet 會從本機 PowerShell 會話中移除一個或多個 CIM 會話物件。</span><span class="sxs-lookup"><span data-stu-id="fbd66-113">The `Remove-CimSession` cmdlet removes one or more CIM session objects from the local PowerShell session.</span></span>

## <span data-ttu-id="fbd66-114">範例</span><span class="sxs-lookup"><span data-stu-id="fbd66-114">EXAMPLES</span></span>

### <span data-ttu-id="fbd66-115">範例1：移除所有 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="fbd66-115">Example 1: Remove all the CIM sessions</span></span>

<span data-ttu-id="fbd66-116">此範例會使用 [CimSession 指令程式](Get-CimSession.md) 來抓取本機電腦上所有可用的 CIM 會話，然後使用來移除它們 `Remove-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="fbd66-116">This example retrieves all the available CIM sessions on the local computer using the [Get-CimSession](Get-CimSession.md) cmdlet, and then removes them using the `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

### <span data-ttu-id="fbd66-117">範例2：移除特定的 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="fbd66-117">Example 2: Remove a specific CIM session</span></span>

<span data-ttu-id="fbd66-118">此範例會移除 **識別碼** 值為5的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="fbd66-118">This example removes the CIM session that has an **Id** value of 5.</span></span>

```powershell
Remove-CimSession -Id 5
```

### <span data-ttu-id="fbd66-119">範例3：使用 WhatIf 參數顯示要移除的 CIM 會話清單</span><span class="sxs-lookup"><span data-stu-id="fbd66-119">Example 3: Show the list of CIM sessions to remove by using the WhatIf parameter</span></span>

<span data-ttu-id="fbd66-120">此範例會使用一般參數 **WhatIf** 來指定不應完成移除，但只會輸出完成時所發生的情況。</span><span class="sxs-lookup"><span data-stu-id="fbd66-120">This example uses the common parameter **WhatIf** to specify that the removal should not be done, but only output what would happen if it were done.</span></span>

```powershell
Remove-CimSession -Name a* -WhatIf
```

## <span data-ttu-id="fbd66-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fbd66-121">PARAMETERS</span></span>

### <span data-ttu-id="fbd66-122">-CimSession</span><span class="sxs-lookup"><span data-stu-id="fbd66-122">-CimSession</span></span>

<span data-ttu-id="fbd66-123">指定要關閉之 CIM 會話的會話物件。</span><span class="sxs-lookup"><span data-stu-id="fbd66-123">Specifies the session objects of the CIM sessions to close.</span></span>

<span data-ttu-id="fbd66-124">輸入包含 CIM 會話的變數，或輸入可建立或取得 CIM 會話的命令，例如 [`New-CimSession`](New-CimSession.md) 或 [`Get-CimSession`](Get-CimSession.md) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fbd66-124">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the [`New-CimSession`](New-CimSession.md) or [`Get-CimSession`](Get-CimSession.md) cmdlets.</span></span>
<span data-ttu-id="fbd66-125">如需詳細資訊，請參閱 [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="fbd66-125">For more information, see [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fbd66-126">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="fbd66-126">-ComputerName</span></span>

<span data-ttu-id="fbd66-127">指定電腦名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="fbd66-127">Specifies an array of names of computers.</span></span> <span data-ttu-id="fbd66-128">移除連接到指定電腦的會話。</span><span class="sxs-lookup"><span data-stu-id="fbd66-128">Removes the sessions that connect to the specified computers.</span></span> <span data-ttu-id="fbd66-129">您可以指定完整功能變數名稱 (FQDN) 或 NetBIOS 名稱。</span><span class="sxs-lookup"><span data-stu-id="fbd66-129">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="fbd66-130">-Id</span><span class="sxs-lookup"><span data-stu-id="fbd66-130">-Id</span></span>

<span data-ttu-id="fbd66-131">指定要移除之 CIM 會話的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fbd66-131">Specifies the ID of the CIM session to remove.</span></span> <span data-ttu-id="fbd66-132">指定一或多個以逗號分隔的識別碼，或使用範圍運算子 (`..`) 來指定識別碼的範圍。</span><span class="sxs-lookup"><span data-stu-id="fbd66-132">Specify one or more IDs separated by commas, or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="fbd66-133">**識別碼** 是一個整數，可唯一識別目前 PowerShell 會話中的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="fbd66-133">An **Id** is an integer that uniquely identifies the CIM session in the current PowerShell session.</span></span>

<span data-ttu-id="fbd66-134">如需範圍運算子的詳細資訊，請參閱 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="fbd66-134">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fbd66-135">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="fbd66-135">-InstanceId</span></span>

<span data-ttu-id="fbd66-136">指定要移除之 CIM 會話的實例識別碼。</span><span class="sxs-lookup"><span data-stu-id="fbd66-136">Specifies the instance ID of the CIM session to remove.</span></span> <span data-ttu-id="fbd66-137">**InstanceId** 是唯一識別 CIM 會話 (GUID) 的全域唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="fbd66-137">**InstanceId** is a Globally Unique Identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="fbd66-138">**InstanceId** 是唯一的，即使您有多個會話在 PowerShell 中執行也是一樣。</span><span class="sxs-lookup"><span data-stu-id="fbd66-138">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="fbd66-139">**Instanceid** 儲存在代表 CIM 會話之物件的 **instanceid** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="fbd66-139">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fbd66-140">-Name</span><span class="sxs-lookup"><span data-stu-id="fbd66-140">-Name</span></span>

<span data-ttu-id="fbd66-141">指定要移除之 CIM 會話的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="fbd66-141">Specifies the friendly name of the CIM session to remove.</span></span> <span data-ttu-id="fbd66-142">您可以使用萬用字元搭配此參數。</span><span class="sxs-lookup"><span data-stu-id="fbd66-142">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="fbd66-143">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fbd66-143">-Confirm</span></span>

<span data-ttu-id="fbd66-144">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="fbd66-144">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="fbd66-145">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fbd66-145">-WhatIf</span></span>

<span data-ttu-id="fbd66-146">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="fbd66-146">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="fbd66-147">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="fbd66-147">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="fbd66-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fbd66-148">CommonParameters</span></span>

<span data-ttu-id="fbd66-149">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="fbd66-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fbd66-150">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="fbd66-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fbd66-151">輸入</span><span class="sxs-lookup"><span data-stu-id="fbd66-151">INPUTS</span></span>

### <span data-ttu-id="fbd66-152">無</span><span class="sxs-lookup"><span data-stu-id="fbd66-152">None</span></span>

<span data-ttu-id="fbd66-153">此 Cmdlet 不接受任何輸入物件。</span><span class="sxs-lookup"><span data-stu-id="fbd66-153">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="fbd66-154">輸出</span><span class="sxs-lookup"><span data-stu-id="fbd66-154">OUTPUTS</span></span>

### <span data-ttu-id="fbd66-155">System.Object</span><span class="sxs-lookup"><span data-stu-id="fbd66-155">System.Object</span></span>

<span data-ttu-id="fbd66-156">此 Cmdlet 會傳回包含 CIM 會話資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="fbd66-156">This cmdlet returns an object that contains CIM session information.</span></span>

## <span data-ttu-id="fbd66-157">注意</span><span class="sxs-lookup"><span data-stu-id="fbd66-157">NOTES</span></span>

## <span data-ttu-id="fbd66-158">相關連結</span><span class="sxs-lookup"><span data-stu-id="fbd66-158">RELATED LINKS</span></span>

[<span data-ttu-id="fbd66-159">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="fbd66-159">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="fbd66-160">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="fbd66-160">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="fbd66-161">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="fbd66-161">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)
