---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSnapin
ms.openlocfilehash: e74aff3e52c61f41a54664efbab9c0f195b0d409
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202676"
---
# <span data-ttu-id="e90cf-103">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="e90cf-103">Remove-PSSnapin</span></span>

## <span data-ttu-id="e90cf-104">概要</span><span class="sxs-lookup"><span data-stu-id="e90cf-104">SYNOPSIS</span></span>
<span data-ttu-id="e90cf-105">從目前的工作階段中移除 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="e90cf-105">Removes Windows PowerShell snap-ins from the current session.</span></span>

## <span data-ttu-id="e90cf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e90cf-106">SYNTAX</span></span>

```
Remove-PSSnapin [-Name] <String[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e90cf-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e90cf-107">DESCRIPTION</span></span>
<span data-ttu-id="e90cf-108">**PSSnapin** 指令 Cmdlet 會從目前的會話中移除 Windows PowerShell 的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="e90cf-108">The **Remove-PSSnapin** cmdlet removes a Windows PowerShell snap-in from the current session.</span></span>
<span data-ttu-id="e90cf-109">您可以使用它來移除您已新增的嵌入式管理單元，Windows PowerShell 無法使用這個 Cmdlet 來移除隨 Windows PowerShell 安裝的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="e90cf-109">You can use it to remove snap-ins that you have added to Windows PowerShell You cannot use this cmdlet to remove the snap-ins that are installed with Windows PowerShell.</span></span>

<span data-ttu-id="e90cf-110">從目前的會話移除嵌入式管理單元之後，仍會載入嵌入式管理單元，但該嵌入式管理單元中的 Cmdlet 和提供者將無法再于會話中使用。</span><span class="sxs-lookup"><span data-stu-id="e90cf-110">After you remove a snap-in from the current session, the snap-in is still loaded, but the cmdlets and providers in the snap-in are no longer available in the session.</span></span>

## <span data-ttu-id="e90cf-111">範例</span><span class="sxs-lookup"><span data-stu-id="e90cf-111">EXAMPLES</span></span>

### <span data-ttu-id="e90cf-112">範例1：移除嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="e90cf-112">Example 1: Remove a snap-in</span></span>

```
PS C:\> remove-pssnapin -Name Microsoft.Exchange
```

<span data-ttu-id="e90cf-113">此命令會從目前的會話移除 **Microsoft. Exchange** 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="e90cf-113">This command removes the **Microsoft.Exchange** snap-in from the current session.</span></span>
<span data-ttu-id="e90cf-114">當命令完成時，嵌入式管理單元支援的 Cmdlet 和提供者於工作階段中將無法使用。</span><span class="sxs-lookup"><span data-stu-id="e90cf-114">When the command is complete, the cmdlets and providers that the snap-in supported are not available in the session.</span></span>

### <span data-ttu-id="e90cf-115">範例2：使用名稱搭配管線來移除嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="e90cf-115">Example 2: Remove snap-ins by using names with the pipeline</span></span>

```
PS C:\> Get-PSSnapIn smp* | Remove-PSSnapIn
```

<span data-ttu-id="e90cf-116">此命令會從目前會話移除名稱開頭為 smp 的 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="e90cf-116">This command removes the Windows PowerShell snap-ins that have names that start with smp from the current session.</span></span>

<span data-ttu-id="e90cf-117">此命令會使用 **PSSnapin** Cmdlet 取得代表嵌入式管理單元的物件。管線運算子 (|) 將結果傳送至 **PSSnapin** Cmdlet，這會將它們從會話中移除。</span><span class="sxs-lookup"><span data-stu-id="e90cf-117">The command uses the **Get-PSSnapin** cmdlet to get objects that represent the snap-ins. The pipeline operator (|) sends the results to the **Remove-PSSnapin** cmdlet, which removes them from the session.</span></span>
<span data-ttu-id="e90cf-118">這個嵌入式管理單元支援的提供者與 Cmdlet 於工作階段中將無法使用。</span><span class="sxs-lookup"><span data-stu-id="e90cf-118">The providers and cmdlets that this snap-in supports are no longer available in the session.</span></span>

<span data-ttu-id="e90cf-119">當您使用管線將物件傳送至 **PSSnapin** 時，物件的名稱會與 *name* 參數相關聯，它會接受管線中具有 **name** 屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="e90cf-119">When you pipe objects to **Remove-PSSnapin** , the names of the objects are associated with the *Name* parameter, which accepts objects from the pipeline that have a **Name** property.</span></span>

### <span data-ttu-id="e90cf-120">範例3：使用名稱移除嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="e90cf-120">Example 3: Remove snap-ins by using names</span></span>

```
PS C:\> Remove-PSSnapin -Name *event*
```

<span data-ttu-id="e90cf-121">此命令會移除所有名稱包含事件的 Windows PowerShell 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="e90cf-121">This command removes all Windows PowerShell snap-ins that have names that include event.</span></span>

## <span data-ttu-id="e90cf-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e90cf-122">PARAMETERS</span></span>

### <span data-ttu-id="e90cf-123">-Name</span><span class="sxs-lookup"><span data-stu-id="e90cf-123">-Name</span></span>
<span data-ttu-id="e90cf-124">指定要從目前工作階段中移除的 Windows PowerShell 嵌入式管理單元名稱。</span><span class="sxs-lookup"><span data-stu-id="e90cf-124">Specifies the names of Windows PowerShell snap-ins to remove from the current session.</span></span>
<span data-ttu-id="e90cf-125">允許使用萬用字元 (\*)。</span><span class="sxs-lookup"><span data-stu-id="e90cf-125">Wildcard characters (\*) are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e90cf-126">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e90cf-126">-PassThru</span></span>
<span data-ttu-id="e90cf-127">傳回代表嵌入式管理單元的物件。</span><span class="sxs-lookup"><span data-stu-id="e90cf-127">Returns an object that represents the snap-in.</span></span>
<span data-ttu-id="e90cf-128">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="e90cf-128">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e90cf-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e90cf-129">-Confirm</span></span>
<span data-ttu-id="e90cf-130">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="e90cf-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e90cf-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e90cf-131">-WhatIf</span></span>
<span data-ttu-id="e90cf-132">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="e90cf-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e90cf-133">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="e90cf-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e90cf-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e90cf-134">CommonParameters</span></span>
<span data-ttu-id="e90cf-135">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e90cf-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e90cf-136">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="e90cf-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e90cf-137">輸入</span><span class="sxs-lookup"><span data-stu-id="e90cf-137">INPUTS</span></span>

### <span data-ttu-id="e90cf-138">System.Management.Automation.PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="e90cf-138">System.Management.Automation.PSSnapInInfo</span></span>
<span data-ttu-id="e90cf-139">您可以使用管線將嵌入式管理單元物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e90cf-139">You can pipe a snap-in object to this cmdlet.</span></span>

## <span data-ttu-id="e90cf-140">輸出</span><span class="sxs-lookup"><span data-stu-id="e90cf-140">OUTPUTS</span></span>

### <span data-ttu-id="e90cf-141">None、PSSnapInInfo、Automation。</span><span class="sxs-lookup"><span data-stu-id="e90cf-141">None, System.Management.Automation.PSSnapInInfo</span></span>
<span data-ttu-id="e90cf-142">如果您指定 *PassThru* 參數，此 Cmdlet 會產生代表嵌入式管理單元的 **PSSnapInInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="e90cf-142">This cmdlet generates a **System.Management.Automation.PSSnapInInfo** object that represents the snap-in, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="e90cf-143">根據預設， **PSSnapin** 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="e90cf-143">By default, **Remove-PSSnapin** does not generate any output.</span></span>

## <span data-ttu-id="e90cf-144">注意</span><span class="sxs-lookup"><span data-stu-id="e90cf-144">NOTES</span></span>

* <span data-ttu-id="e90cf-145">**PSSnapin** 從會話移除嵌入式管理單元之前，不會檢查 Windows PowerShell 的版本。</span><span class="sxs-lookup"><span data-stu-id="e90cf-145">**Remove-PSSnapin** does not check the version of Windows PowerShell before removing a snap-in from the session.</span></span> <span data-ttu-id="e90cf-146">如果嵌入式管理單元不可移除，則會出現警告，且命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="e90cf-146">If a snap-in cannot be removed, a warning appears and the command fails.</span></span>
* <span data-ttu-id="e90cf-147">**PSSnapin** 只會影響目前的會話。</span><span class="sxs-lookup"><span data-stu-id="e90cf-147">**Remove-PSSnapin** affects only the current session.</span></span> <span data-ttu-id="e90cf-148">如果已將 Add-PSSnapin 命令新增到 Windows PowerShell 設定檔，您應該刪除命令以從未來工作階段移除嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="e90cf-148">If you have added an Add-PSSnapin command to your Windows PowerShell profile, you should delete the command to remove the snap-in from future sessions.</span></span> <span data-ttu-id="e90cf-149">如需指示，請輸入 `Get-Help about_Profiles` 。</span><span class="sxs-lookup"><span data-stu-id="e90cf-149">For instructions, type `Get-Help about_Profiles`.</span></span>

## <span data-ttu-id="e90cf-150">相關連結</span><span class="sxs-lookup"><span data-stu-id="e90cf-150">RELATED LINKS</span></span>

[<span data-ttu-id="e90cf-151">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="e90cf-151">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="e90cf-152">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="e90cf-152">Get-PSSnapin</span></span>](Get-PSSnapin.md)
