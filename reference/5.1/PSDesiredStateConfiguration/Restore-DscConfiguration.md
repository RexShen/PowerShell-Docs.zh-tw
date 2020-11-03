---
external help file: Restore-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/restore-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-DscConfiguration
ms.openlocfilehash: 823032f7665d9ec83faa59c37560510e049efdd2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203935"
---
# <span data-ttu-id="27d33-103">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="27d33-103">Restore-DscConfiguration</span></span>

## <span data-ttu-id="27d33-104">概要</span><span class="sxs-lookup"><span data-stu-id="27d33-104">SYNOPSIS</span></span>
<span data-ttu-id="27d33-105">重新套用先前的節點設定。</span><span class="sxs-lookup"><span data-stu-id="27d33-105">Reapplies the previous configuration for the node.</span></span>

## <span data-ttu-id="27d33-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="27d33-106">SYNTAX</span></span>

```
Restore-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="27d33-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="27d33-107">DESCRIPTION</span></span>
<span data-ttu-id="27d33-108">**Restore-DscConfiguration** Cmdlet 會還原先前的節點設定 (如果先前的設定已存在)。</span><span class="sxs-lookup"><span data-stu-id="27d33-108">The **Restore-DscConfiguration** cmdlet reapplies the previous configuration for the node, if a previous configuration exists.</span></span>
<span data-ttu-id="27d33-109">使用通用訊息模型 (CIM) 工作階段指定電腦。</span><span class="sxs-lookup"><span data-stu-id="27d33-109">Specify computers by using Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="27d33-110">如果您沒有指定目標電腦，此 Cmdlet 會還原本機電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="27d33-110">If you do not specify a target computer, the cmdlet restores the configuration of the local computer.</span></span>
<span data-ttu-id="27d33-111">如果先前沒有針對特定節點的設定，此 Cmdlet 會傳回錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="27d33-111">If there is no previous configuration for a particular node, this cmdlet returns an error message.</span></span>

<span data-ttu-id="27d33-112">此 Cmdlet 不支援 **Confirm** 參數。</span><span class="sxs-lookup"><span data-stu-id="27d33-112">This cmdlet does not support the **Confirm** parameter.</span></span>

## <span data-ttu-id="27d33-113">範例</span><span class="sxs-lookup"><span data-stu-id="27d33-113">EXAMPLES</span></span>

### <span data-ttu-id="27d33-114">範例 1：還原本機電腦的設定</span><span class="sxs-lookup"><span data-stu-id="27d33-114">Example 1: Restore the configuration for the local computer</span></span>

```
PS C:\> Restore-DscConfiguration
```

<span data-ttu-id="27d33-115">此命令會還原本機電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="27d33-115">This command restores the configuration for the local computer.</span></span>

### <span data-ttu-id="27d33-116">範例 2：還原指定電腦的設定</span><span class="sxs-lookup"><span data-stu-id="27d33-116">Example 2: Restore configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Restore-DscConfiguration -CimSession $Session
```

<span data-ttu-id="27d33-117">這個範例會還原 CIM 工作階段所指定之電腦上的設定。</span><span class="sxs-lookup"><span data-stu-id="27d33-117">This example restores configuration on a computer specified by a CIM session.</span></span>
<span data-ttu-id="27d33-118">這個範例會針對名為 Server01 的電腦，建立一個搭配此 Cmdlet 使用的 CIM 工作階段。</span><span class="sxs-lookup"><span data-stu-id="27d33-118">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="27d33-119">或者，建立一個 CIM 工作階段的陣列，以便將該 Cmdlet 套用到多部指定的電腦。</span><span class="sxs-lookup"><span data-stu-id="27d33-119">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="27d33-120">第一個命令會使用 **New-CimSession** Cmdlet 建立 CIM 工作階段，然後再以 $Session 變數儲存 **CimSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="27d33-120">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="27d33-121">此命令會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="27d33-121">The command prompts you for a password.</span></span>
<span data-ttu-id="27d33-122">如需詳細資訊，請鍵入 `Get-Help New-CimSession`。</span><span class="sxs-lookup"><span data-stu-id="27d33-122">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="27d33-123">第二個命令會還原以 $Session 變數儲存的 **CimSession** 物件所識別之電腦的設定，在此案例中為名為 Server01 的電腦。</span><span class="sxs-lookup"><span data-stu-id="27d33-123">The second command restores the configuration for the computers identified by the **CimSession** objects stored in the $Session variable, in this case, the computer named Server01.</span></span>

## <span data-ttu-id="27d33-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="27d33-124">PARAMETERS</span></span>

### <span data-ttu-id="27d33-125">-AsJob</span><span class="sxs-lookup"><span data-stu-id="27d33-125">-AsJob</span></span>
<span data-ttu-id="27d33-126">指出此 Cmdlet 會以背景工作方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="27d33-126">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="27d33-127">-CimSession</span><span class="sxs-lookup"><span data-stu-id="27d33-127">-CimSession</span></span>
<span data-ttu-id="27d33-128">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="27d33-128">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="27d33-129">輸入電腦名稱稱或會話物件，例如 **CimSession** 或 **CimSession** Cmdlet 的輸出。</span><span class="sxs-lookup"><span data-stu-id="27d33-129">Enter a computer name or a session object, such as the output of a **New-CimSession** or **Get-CimSession** cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27d33-130">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="27d33-130">-ThrottleLimit</span></span>
<span data-ttu-id="27d33-131">指定為執行 Cmdlet 可建立的最大並行作業數。</span><span class="sxs-lookup"><span data-stu-id="27d33-131">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="27d33-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="27d33-132">-Confirm</span></span>
<span data-ttu-id="27d33-133">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="27d33-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="27d33-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="27d33-134">-WhatIf</span></span>
<span data-ttu-id="27d33-135">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="27d33-135">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="27d33-136">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="27d33-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="27d33-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="27d33-137">CommonParameters</span></span>
<span data-ttu-id="27d33-138">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="27d33-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="27d33-139">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="27d33-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="27d33-140">輸入</span><span class="sxs-lookup"><span data-stu-id="27d33-140">INPUTS</span></span>

## <span data-ttu-id="27d33-141">輸出</span><span class="sxs-lookup"><span data-stu-id="27d33-141">OUTPUTS</span></span>

## <span data-ttu-id="27d33-142">注意</span><span class="sxs-lookup"><span data-stu-id="27d33-142">NOTES</span></span>

## <span data-ttu-id="27d33-143">相關連結</span><span class="sxs-lookup"><span data-stu-id="27d33-143">RELATED LINKS</span></span>

[<span data-ttu-id="27d33-144">Windows PowerShell Desired State Configuration 概觀</span><span class="sxs-lookup"><span data-stu-id="27d33-144">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="27d33-145">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="27d33-145">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="27d33-146">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="27d33-146">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="27d33-147">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="27d33-147">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="27d33-148">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="27d33-148">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
