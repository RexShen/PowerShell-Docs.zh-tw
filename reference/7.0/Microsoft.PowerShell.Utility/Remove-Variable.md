---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: 26d53ab633f5f73495a8d66012ae55dc10c5d629
ms.sourcegitcommit: 84fcc90bd018ab76ac4e964d53e7c9c2b5a7b6c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205735"
---
# <span data-ttu-id="6dcb2-103">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="6dcb2-103">Remove-Variable</span></span>

## <span data-ttu-id="6dcb2-104">概要</span><span class="sxs-lookup"><span data-stu-id="6dcb2-104">SYNOPSIS</span></span>
<span data-ttu-id="6dcb2-105">刪除變數和它的值。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-105">Deletes a variable and its value.</span></span>

## <span data-ttu-id="6dcb2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6dcb2-106">SYNTAX</span></span>

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6dcb2-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6dcb2-107">DESCRIPTION</span></span>

<span data-ttu-id="6dcb2-108">此 `Remove-Variable` Cmdlet 會從其定義所在的範圍中刪除變數和其值，例如目前的會話。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-108">The `Remove-Variable` cmdlet deletes a variable and its value from the scope in which it is defined, such as the current session.</span></span> <span data-ttu-id="6dcb2-109">您無法使用此 Cmdlet 刪除設定為常數或系統所擁有的變數。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-109">You cannot use this cmdlet to delete variables that are set as constants or those that are owned by the system.</span></span>

## <span data-ttu-id="6dcb2-110">範例</span><span class="sxs-lookup"><span data-stu-id="6dcb2-110">EXAMPLES</span></span>

### <span data-ttu-id="6dcb2-111">範例 1︰移除變數</span><span class="sxs-lookup"><span data-stu-id="6dcb2-111">Example 1: Remove a variable</span></span>

```powershell
Remove-Variable Smp
```

<span data-ttu-id="6dcb2-112">此命令會刪除 `$Smp` 變數。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-112">This command deletes the `$Smp` variable.</span></span>

## <span data-ttu-id="6dcb2-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6dcb2-113">PARAMETERS</span></span>

### <span data-ttu-id="6dcb2-114">-Exclude</span><span class="sxs-lookup"><span data-stu-id="6dcb2-114">-Exclude</span></span>

<span data-ttu-id="6dcb2-115">指定此 Cmdlet 從作業省略之項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-115">Specifies an array of items that this cmdlet omits from the operation.</span></span> <span data-ttu-id="6dcb2-116">此參數的值會限定 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-116">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="6dcb2-117">輸入名稱元素或模式，例如 "s\*"。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-117">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="6dcb2-118">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-118">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="6dcb2-119">-Force</span><span class="sxs-lookup"><span data-stu-id="6dcb2-119">-Force</span></span>

<span data-ttu-id="6dcb2-120">指示 Cmdlet 移除變數，即使它是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-120">Indicates that the cmdlet removes a variable even if it is read-only.</span></span> <span data-ttu-id="6dcb2-121">即使使用 **Force** 參數，Cmdlet 也無法移除常數。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-121">Even using the **Force** parameter, the cmdlet cannot remove a constant.</span></span>

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

### <span data-ttu-id="6dcb2-122">-Include</span><span class="sxs-lookup"><span data-stu-id="6dcb2-122">-Include</span></span>

<span data-ttu-id="6dcb2-123">指定此 Cmdlet 在作業中刪除之項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-123">Specifies an array of items that this cmdlet deletes in the operation.</span></span> <span data-ttu-id="6dcb2-124">此參數的值會限定 **Name** 參數。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-124">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="6dcb2-125">輸入名稱元素或模式，例如 s\*。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-125">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="6dcb2-126">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-126">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="6dcb2-127">-Name</span><span class="sxs-lookup"><span data-stu-id="6dcb2-127">-Name</span></span>

<span data-ttu-id="6dcb2-128">指定要移除之變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-128">Specifies the name of the variable to be removed.</span></span> <span data-ttu-id="6dcb2-129">參數名稱 ( **名稱** ) 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-129">The parameter name ( **Name** ) is optional.</span></span>
<span data-ttu-id="6dcb2-130">允許萬用字元</span><span class="sxs-lookup"><span data-stu-id="6dcb2-130">Wildcards are permitted</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="6dcb2-131">-Scope</span><span class="sxs-lookup"><span data-stu-id="6dcb2-131">-Scope</span></span>

<span data-ttu-id="6dcb2-132">只取得指定範圍內的變數。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-132">Gets only the variables in the specified scope.</span></span> <span data-ttu-id="6dcb2-133">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="6dcb2-133">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6dcb2-134">全球</span><span class="sxs-lookup"><span data-stu-id="6dcb2-134">Global</span></span>
- <span data-ttu-id="6dcb2-135">本機</span><span class="sxs-lookup"><span data-stu-id="6dcb2-135">Local</span></span>
- <span data-ttu-id="6dcb2-136">指令碼</span><span class="sxs-lookup"><span data-stu-id="6dcb2-136">Script</span></span>
- <span data-ttu-id="6dcb2-137">相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-137">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="6dcb2-138">Local 為預設值。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-138">Local is the default.</span></span> <span data-ttu-id="6dcb2-139">如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-139">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6dcb2-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6dcb2-140">-Confirm</span></span>

<span data-ttu-id="6dcb2-141">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6dcb2-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6dcb2-142">-WhatIf</span></span>

<span data-ttu-id="6dcb2-143">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6dcb2-144">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6dcb2-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6dcb2-145">CommonParameters</span></span>

<span data-ttu-id="6dcb2-146">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6dcb2-147">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6dcb2-148">輸入</span><span class="sxs-lookup"><span data-stu-id="6dcb2-148">INPUTS</span></span>

### <span data-ttu-id="6dcb2-149">System.Management.Automation.PSVariable</span><span class="sxs-lookup"><span data-stu-id="6dcb2-149">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="6dcb2-150">您可以使用管線將變數物件傳送至 `Remove-Variable` 。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-150">You can pipe a variable object to `Remove-Variable`.</span></span>

## <span data-ttu-id="6dcb2-151">輸出</span><span class="sxs-lookup"><span data-stu-id="6dcb2-151">OUTPUTS</span></span>

### <span data-ttu-id="6dcb2-152">無</span><span class="sxs-lookup"><span data-stu-id="6dcb2-152">None</span></span>

<span data-ttu-id="6dcb2-153">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-153">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="6dcb2-154">注意</span><span class="sxs-lookup"><span data-stu-id="6dcb2-154">NOTES</span></span>

- <span data-ttu-id="6dcb2-155">變更只會影響目前的範圍，例如工作階段。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-155">Changes affect only the current scope, such as a session.</span></span> <span data-ttu-id="6dcb2-156">若要從所有的會話刪除變數，請將 `Remove-Variable` 命令新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-156">To delete a variable from all sessions, add a `Remove-Variable` command to your PowerShell profile.</span></span>

- <span data-ttu-id="6dcb2-157">您也可以 `Remove-Variable` 使用內建的別名來參考 `rv` 。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-157">You can also refer to `Remove-Variable` by its built-in alias, `rv`.</span></span> <span data-ttu-id="6dcb2-158">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="6dcb2-158">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

## <span data-ttu-id="6dcb2-159">相關連結</span><span class="sxs-lookup"><span data-stu-id="6dcb2-159">RELATED LINKS</span></span>

[<span data-ttu-id="6dcb2-160">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="6dcb2-160">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="6dcb2-161">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="6dcb2-161">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="6dcb2-162">New-Variable</span><span class="sxs-lookup"><span data-stu-id="6dcb2-162">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="6dcb2-163">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="6dcb2-163">Set-Variable</span></span>](Set-Variable.md)
