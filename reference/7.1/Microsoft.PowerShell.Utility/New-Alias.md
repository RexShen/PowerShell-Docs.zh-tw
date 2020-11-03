---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: b004cae919c32078d7c2d79174637a0fa4130ab1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204995"
---
# <span data-ttu-id="757bc-103">New-Alias</span><span class="sxs-lookup"><span data-stu-id="757bc-103">New-Alias</span></span>

## <span data-ttu-id="757bc-104">概要</span><span class="sxs-lookup"><span data-stu-id="757bc-104">SYNOPSIS</span></span>
<span data-ttu-id="757bc-105">建立新的別名。</span><span class="sxs-lookup"><span data-stu-id="757bc-105">Creates a new alias.</span></span>

## <span data-ttu-id="757bc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="757bc-106">SYNTAX</span></span>

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="757bc-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="757bc-107">DESCRIPTION</span></span>

<span data-ttu-id="757bc-108">**新別名** Cmdlet 會在目前的 PowerShell 會話中建立新的別名。</span><span class="sxs-lookup"><span data-stu-id="757bc-108">The **New-Alias** cmdlet creates a new alias in the current PowerShell session.</span></span>
<span data-ttu-id="757bc-109">在您結束會話或關閉 PowerShell 之後，不會儲存使用 **新別名** 所建立的別名。</span><span class="sxs-lookup"><span data-stu-id="757bc-109">Aliases created by using **New-Alias** are not saved after you exit the session or close PowerShell.</span></span>
<span data-ttu-id="757bc-110">您可以使用 Export-Alias Cmdlet 將別名資訊儲存到檔案。</span><span class="sxs-lookup"><span data-stu-id="757bc-110">You can use the Export-Alias cmdlet to save your alias information to a file.</span></span>
<span data-ttu-id="757bc-111">您之後可以使用 **Import-Alias** 來抓取儲存的別名資訊。</span><span class="sxs-lookup"><span data-stu-id="757bc-111">You can later use **Import-Alias** to retrieve that saved alias information.</span></span>

## <span data-ttu-id="757bc-112">範例</span><span class="sxs-lookup"><span data-stu-id="757bc-112">EXAMPLES</span></span>

### <span data-ttu-id="757bc-113">範例 1︰建立 Cmdlet 的別名</span><span class="sxs-lookup"><span data-stu-id="757bc-113">Example 1: Create an alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

<span data-ttu-id="757bc-114">此命令會建立名為 List 的別名，以代表 Get-ChildItem Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="757bc-114">This command creates an alias named List to represent the Get-ChildItem cmdlet.</span></span>

### <span data-ttu-id="757bc-115">範例 2︰建立 Cmdlet 的唯讀別名</span><span class="sxs-lookup"><span data-stu-id="757bc-115">Example 2: Create a read-only alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

<span data-ttu-id="757bc-116">此命令會建立名為 W 的別名，以代表 Get-WmiObject Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="757bc-116">This command creates an alias named W to represent the Get-WmiObject cmdlet.</span></span>
<span data-ttu-id="757bc-117">它會為別名建立描述 quick wmi alias，並使其變成唯讀。</span><span class="sxs-lookup"><span data-stu-id="757bc-117">It creates a description, quick wmi alias, for the alias and makes it read-only.</span></span>
<span data-ttu-id="757bc-118">命令的最後一行使用 Get-Alias 取得新的別名，並使用管線將它傳送至 Format-List 以顯示其所有的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="757bc-118">The last line of the command uses Get-Alias to get the new alias and pipes it to Format-List to display all of the information about it.</span></span>

## <span data-ttu-id="757bc-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="757bc-119">PARAMETERS</span></span>

### <span data-ttu-id="757bc-120">-Description</span><span class="sxs-lookup"><span data-stu-id="757bc-120">-Description</span></span>

<span data-ttu-id="757bc-121">指定別名的描述。</span><span class="sxs-lookup"><span data-stu-id="757bc-121">Specifies a description of the alias.</span></span>
<span data-ttu-id="757bc-122">您可以輸入任何字串。</span><span class="sxs-lookup"><span data-stu-id="757bc-122">You can type any string.</span></span>
<span data-ttu-id="757bc-123">如果描述包含空格，請將它括在引號中。</span><span class="sxs-lookup"><span data-stu-id="757bc-123">If the description includes spaces, enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="757bc-124">-Force</span><span class="sxs-lookup"><span data-stu-id="757bc-124">-Force</span></span>

<span data-ttu-id="757bc-125">指出如果所命名的別名已經存在，此 Cmdlet 的運作方式就和 Set-Alias 一樣。</span><span class="sxs-lookup"><span data-stu-id="757bc-125">Indicates that the cmdlet acts like Set-Alias if the alias named already exists.</span></span>

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

### <span data-ttu-id="757bc-126">-Name</span><span class="sxs-lookup"><span data-stu-id="757bc-126">-Name</span></span>

<span data-ttu-id="757bc-127">指定新的別名。</span><span class="sxs-lookup"><span data-stu-id="757bc-127">Specifies the new alias.</span></span>
<span data-ttu-id="757bc-128">您可以在別名中使用任何英數字元，但是第一個字元不能是數字。</span><span class="sxs-lookup"><span data-stu-id="757bc-128">You can use any alphanumeric characters in an alias, but the first character cannot be a number.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="757bc-129">-Option</span><span class="sxs-lookup"><span data-stu-id="757bc-129">-Option</span></span>

<span data-ttu-id="757bc-130">指定別名的 **Options** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="757bc-130">Specifies the value of the **Options** property of the alias.</span></span>
<span data-ttu-id="757bc-131">有效值為：</span><span class="sxs-lookup"><span data-stu-id="757bc-131">Valid values are:</span></span>

- <span data-ttu-id="757bc-132">無：別名沒有 (預設值的條件約束) </span><span class="sxs-lookup"><span data-stu-id="757bc-132">None: The alias has no constraints (default value)</span></span>
- <span data-ttu-id="757bc-133">ReadOnly：可以刪除別名，但除非使用 **Force** 參數，否則無法變更</span><span class="sxs-lookup"><span data-stu-id="757bc-133">ReadOnly: The alias can be deleted but cannot be changed except by using the **Force** parameter</span></span>
- <span data-ttu-id="757bc-134">常數：無法刪除或變更別名</span><span class="sxs-lookup"><span data-stu-id="757bc-134">Constant: The alias cannot be deleted or changed</span></span>
- <span data-ttu-id="757bc-135">私用：別名只能在目前的範圍中使用</span><span class="sxs-lookup"><span data-stu-id="757bc-135">Private: The alias is available only in the current scope</span></span>
- <span data-ttu-id="757bc-136">AllScope：別名會複製到所建立的任何新範圍</span><span class="sxs-lookup"><span data-stu-id="757bc-136">AllScope: The alias is copied to any new scopes that are created</span></span>
- <span data-ttu-id="757bc-137">未指定：未指定選項</span><span class="sxs-lookup"><span data-stu-id="757bc-137">Unspecified: The option is not specified</span></span>

<span data-ttu-id="757bc-138">若要查看會話中所有別名的 **Options** 屬性，請輸入 `Get-Alias | Format-Table -Property Name, Options -AutoSize` 。</span><span class="sxs-lookup"><span data-stu-id="757bc-138">To see the **Options** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -AutoSize`.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="757bc-139">-PassThru</span><span class="sxs-lookup"><span data-stu-id="757bc-139">-PassThru</span></span>

<span data-ttu-id="757bc-140">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="757bc-140">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="757bc-141">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="757bc-141">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="757bc-142">-Scope</span><span class="sxs-lookup"><span data-stu-id="757bc-142">-Scope</span></span>

<span data-ttu-id="757bc-143">指定新別名的範圍。</span><span class="sxs-lookup"><span data-stu-id="757bc-143">Specifies the scope of the new alias.</span></span>
<span data-ttu-id="757bc-144">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="757bc-144">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="757bc-145">全球</span><span class="sxs-lookup"><span data-stu-id="757bc-145">Global</span></span>
- <span data-ttu-id="757bc-146">本機</span><span class="sxs-lookup"><span data-stu-id="757bc-146">Local</span></span>
- <span data-ttu-id="757bc-147">指令碼</span><span class="sxs-lookup"><span data-stu-id="757bc-147">Script</span></span>
- <span data-ttu-id="757bc-148">相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。</span><span class="sxs-lookup"><span data-stu-id="757bc-148">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="757bc-149">Local 為預設值。</span><span class="sxs-lookup"><span data-stu-id="757bc-149">Local is the default.</span></span>
<span data-ttu-id="757bc-150">如需詳細資訊，請參閱 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="757bc-150">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="757bc-151">-Value</span><span class="sxs-lookup"><span data-stu-id="757bc-151">-Value</span></span>

<span data-ttu-id="757bc-152">指定 Cmdlet 名稱或已有別名的命令元素。</span><span class="sxs-lookup"><span data-stu-id="757bc-152">Specifies the name of the cmdlet or command element that is being aliased.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="757bc-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="757bc-153">-Confirm</span></span>

<span data-ttu-id="757bc-154">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="757bc-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="757bc-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="757bc-155">-WhatIf</span></span>

<span data-ttu-id="757bc-156">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="757bc-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="757bc-157">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="757bc-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="757bc-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="757bc-158">CommonParameters</span></span>

<span data-ttu-id="757bc-159">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="757bc-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="757bc-160">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="757bc-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="757bc-161">輸入</span><span class="sxs-lookup"><span data-stu-id="757bc-161">INPUTS</span></span>

### <span data-ttu-id="757bc-162">無</span><span class="sxs-lookup"><span data-stu-id="757bc-162">None</span></span>

<span data-ttu-id="757bc-163">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="757bc-163">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="757bc-164">輸出</span><span class="sxs-lookup"><span data-stu-id="757bc-164">OUTPUTS</span></span>

### <span data-ttu-id="757bc-165">無或 System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="757bc-165">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="757bc-166">使用 *Passthru* 參數時， **New-Alias** 會產生代表新別名的 **System.Management.Automation.AliasInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="757bc-166">When you use the *Passthru* parameter, **New-Alias** generates a **System.Management.Automation.AliasInfo** object representing the new alias.</span></span>
<span data-ttu-id="757bc-167">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="757bc-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="757bc-168">注意</span><span class="sxs-lookup"><span data-stu-id="757bc-168">NOTES</span></span>

* <span data-ttu-id="757bc-169">若要建立新的別名，請使用 `Set-Alias` 或 `New-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="757bc-169">To create a new alias, use `Set-Alias` or `New-Alias`.</span></span> <span data-ttu-id="757bc-170">若要變更別名，請使用 `Set-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="757bc-170">To change an alias, use `Set-Alias`.</span></span> <span data-ttu-id="757bc-171">若要刪除別名，請使用 `Remove-Item` 。</span><span class="sxs-lookup"><span data-stu-id="757bc-171">To delete an alias, use `Remove-Item`.</span></span>

## <span data-ttu-id="757bc-172">相關連結</span><span class="sxs-lookup"><span data-stu-id="757bc-172">RELATED LINKS</span></span>

[<span data-ttu-id="757bc-173">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="757bc-173">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="757bc-174">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="757bc-174">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="757bc-175">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="757bc-175">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="757bc-176">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="757bc-176">Set-Alias</span></span>](Set-Alias.md)

