---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: 00ef887dc79e35a6dff299a37bfafa57aebc77db
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203199"
---
# <span data-ttu-id="563d4-103">New-Alias</span><span class="sxs-lookup"><span data-stu-id="563d4-103">New-Alias</span></span>

## <span data-ttu-id="563d4-104">概要</span><span class="sxs-lookup"><span data-stu-id="563d4-104">SYNOPSIS</span></span>
<span data-ttu-id="563d4-105">建立新的別名。</span><span class="sxs-lookup"><span data-stu-id="563d4-105">Creates a new alias.</span></span>

## <span data-ttu-id="563d4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="563d4-106">SYNTAX</span></span>

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="563d4-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="563d4-107">DESCRIPTION</span></span>
<span data-ttu-id="563d4-108">**New-Alias** Cmdlet 會在目前的 Windows PowerShell 工作階段中建立新的別名。</span><span class="sxs-lookup"><span data-stu-id="563d4-108">The **New-Alias** cmdlet creates a new alias in the current Windows PowerShell session.</span></span>
<span data-ttu-id="563d4-109">在您結束工作階段或是關閉 Windows PowerShell 之後，不會儲存使用 **New-Alias** 建立的別名。</span><span class="sxs-lookup"><span data-stu-id="563d4-109">Aliases created by using **New-Alias** are not saved after you exit the session or close Windows PowerShell.</span></span>
<span data-ttu-id="563d4-110">您可以使用 Export-Alias Cmdlet 將別名資訊儲存到檔案。</span><span class="sxs-lookup"><span data-stu-id="563d4-110">You can use the Export-Alias cmdlet to save your alias information to a file.</span></span>
<span data-ttu-id="563d4-111">您之後可以使用 **Import-Alias** 來抓取儲存的別名資訊。</span><span class="sxs-lookup"><span data-stu-id="563d4-111">You can later use **Import-Alias** to retrieve that saved alias information.</span></span>

## <span data-ttu-id="563d4-112">範例</span><span class="sxs-lookup"><span data-stu-id="563d4-112">EXAMPLES</span></span>

### <span data-ttu-id="563d4-113">範例 1︰建立 Cmdlet 的別名</span><span class="sxs-lookup"><span data-stu-id="563d4-113">Example 1: Create an alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

<span data-ttu-id="563d4-114">此命令會建立名為 List 的別名，以代表 Get-ChildItem Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="563d4-114">This command creates an alias named List to represent the Get-ChildItem cmdlet.</span></span>

### <span data-ttu-id="563d4-115">範例 2︰建立 Cmdlet 的唯讀別名</span><span class="sxs-lookup"><span data-stu-id="563d4-115">Example 2: Create a read-only alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

<span data-ttu-id="563d4-116">此命令會建立名為 W 的別名，以代表 Get-WmiObject Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="563d4-116">This command creates an alias named W to represent the Get-WmiObject cmdlet.</span></span>
<span data-ttu-id="563d4-117">它會為別名建立描述 quick wmi alias，並使其變成唯讀。</span><span class="sxs-lookup"><span data-stu-id="563d4-117">It creates a description, quick wmi alias, for the alias and makes it read-only.</span></span>
<span data-ttu-id="563d4-118">命令的最後一行使用 Get-Alias 取得新的別名，並使用管線將它傳送至 Format-List 以顯示其所有的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="563d4-118">The last line of the command uses Get-Alias to get the new alias and pipes it to Format-List to display all of the information about it.</span></span>

## <span data-ttu-id="563d4-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="563d4-119">PARAMETERS</span></span>

### <span data-ttu-id="563d4-120">-Description</span><span class="sxs-lookup"><span data-stu-id="563d4-120">-Description</span></span>
<span data-ttu-id="563d4-121">指定別名的描述。</span><span class="sxs-lookup"><span data-stu-id="563d4-121">Specifies a description of the alias.</span></span>
<span data-ttu-id="563d4-122">您可以輸入任何字串。</span><span class="sxs-lookup"><span data-stu-id="563d4-122">You can type any string.</span></span>
<span data-ttu-id="563d4-123">如果描述包含空格，請將它括在引號中。</span><span class="sxs-lookup"><span data-stu-id="563d4-123">If the description includes spaces, enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="563d4-124">-Force</span><span class="sxs-lookup"><span data-stu-id="563d4-124">-Force</span></span>
<span data-ttu-id="563d4-125">指出如果所命名的別名已經存在，此 Cmdlet 的運作方式就和 Set-Alias 一樣。</span><span class="sxs-lookup"><span data-stu-id="563d4-125">Indicates that the cmdlet acts like Set-Alias if the alias named already exists.</span></span>

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

### <span data-ttu-id="563d4-126">-Name</span><span class="sxs-lookup"><span data-stu-id="563d4-126">-Name</span></span>
<span data-ttu-id="563d4-127">指定新的別名。</span><span class="sxs-lookup"><span data-stu-id="563d4-127">Specifies the new alias.</span></span>
<span data-ttu-id="563d4-128">您可以在別名中使用任何英數字元，但是第一個字元不能是數字。</span><span class="sxs-lookup"><span data-stu-id="563d4-128">You can use any alphanumeric characters in an alias, but the first character cannot be a number.</span></span>

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

### <span data-ttu-id="563d4-129">-Option</span><span class="sxs-lookup"><span data-stu-id="563d4-129">-Option</span></span>
<span data-ttu-id="563d4-130">指定別名的 **Options** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="563d4-130">Specifies the value of the **Options** property of the alias.</span></span>
<span data-ttu-id="563d4-131">有效值為：</span><span class="sxs-lookup"><span data-stu-id="563d4-131">Valid values are:</span></span>

- <span data-ttu-id="563d4-132">無：別名沒有 (預設值的條件約束) </span><span class="sxs-lookup"><span data-stu-id="563d4-132">None: The alias has no constraints (default value)</span></span>
- <span data-ttu-id="563d4-133">ReadOnly：可以刪除別名，但除非使用 **Force** 參數，否則無法變更</span><span class="sxs-lookup"><span data-stu-id="563d4-133">ReadOnly: The alias can be deleted but cannot be changed except by using the **Force** parameter</span></span>
- <span data-ttu-id="563d4-134">常數：無法刪除或變更別名</span><span class="sxs-lookup"><span data-stu-id="563d4-134">Constant: The alias cannot be deleted or changed</span></span>
- <span data-ttu-id="563d4-135">私用：別名只能在目前的範圍中使用</span><span class="sxs-lookup"><span data-stu-id="563d4-135">Private: The alias is available only in the current scope</span></span>
- <span data-ttu-id="563d4-136">AllScope：別名會複製到所建立的任何新範圍</span><span class="sxs-lookup"><span data-stu-id="563d4-136">AllScope: The alias is copied to any new scopes that are created</span></span>
- <span data-ttu-id="563d4-137">未指定：未指定選項</span><span class="sxs-lookup"><span data-stu-id="563d4-137">Unspecified: The option is not specified</span></span>

<span data-ttu-id="563d4-138">若要查看會話中所有別名的 **Options** 屬性，請輸入 `Get-Alias | Format-Table -Property Name, Options -AutoSize` 。</span><span class="sxs-lookup"><span data-stu-id="563d4-138">To see the **Options** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -AutoSize`.</span></span>

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

### <span data-ttu-id="563d4-139">-PassThru</span><span class="sxs-lookup"><span data-stu-id="563d4-139">-PassThru</span></span>
<span data-ttu-id="563d4-140">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="563d4-140">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="563d4-141">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="563d4-141">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="563d4-142">-Scope</span><span class="sxs-lookup"><span data-stu-id="563d4-142">-Scope</span></span>
<span data-ttu-id="563d4-143">指定新別名的範圍。</span><span class="sxs-lookup"><span data-stu-id="563d4-143">Specifies the scope of the new alias.</span></span>
<span data-ttu-id="563d4-144">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="563d4-144">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="563d4-145">全球</span><span class="sxs-lookup"><span data-stu-id="563d4-145">Global</span></span>
- <span data-ttu-id="563d4-146">本機</span><span class="sxs-lookup"><span data-stu-id="563d4-146">Local</span></span>
- <span data-ttu-id="563d4-147">指令碼</span><span class="sxs-lookup"><span data-stu-id="563d4-147">Script</span></span>
- <span data-ttu-id="563d4-148">相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。</span><span class="sxs-lookup"><span data-stu-id="563d4-148">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="563d4-149">Local 為預設值。</span><span class="sxs-lookup"><span data-stu-id="563d4-149">Local is the default.</span></span>
<span data-ttu-id="563d4-150">如需詳細資訊，請參閱 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="563d4-150">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="563d4-151">-Value</span><span class="sxs-lookup"><span data-stu-id="563d4-151">-Value</span></span>
<span data-ttu-id="563d4-152">指定 Cmdlet 名稱或已有別名的命令元素。</span><span class="sxs-lookup"><span data-stu-id="563d4-152">Specifies the name of the cmdlet or command element that is being aliased.</span></span>

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

### <span data-ttu-id="563d4-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="563d4-153">-Confirm</span></span>
<span data-ttu-id="563d4-154">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="563d4-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="563d4-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="563d4-155">-WhatIf</span></span>
<span data-ttu-id="563d4-156">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="563d4-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="563d4-157">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="563d4-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="563d4-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="563d4-158">CommonParameters</span></span>
<span data-ttu-id="563d4-159">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="563d4-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="563d4-160">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="563d4-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="563d4-161">輸入</span><span class="sxs-lookup"><span data-stu-id="563d4-161">INPUTS</span></span>

### <span data-ttu-id="563d4-162">無</span><span class="sxs-lookup"><span data-stu-id="563d4-162">None</span></span>
<span data-ttu-id="563d4-163">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="563d4-163">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="563d4-164">輸出</span><span class="sxs-lookup"><span data-stu-id="563d4-164">OUTPUTS</span></span>

### <span data-ttu-id="563d4-165">無或 System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="563d4-165">None or System.Management.Automation.AliasInfo</span></span>
<span data-ttu-id="563d4-166">使用 *Passthru* 參數時， **New-Alias** 會產生代表新別名的 **System.Management.Automation.AliasInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="563d4-166">When you use the *Passthru* parameter, **New-Alias** generates a **System.Management.Automation.AliasInfo** object representing the new alias.</span></span>
<span data-ttu-id="563d4-167">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="563d4-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="563d4-168">注意</span><span class="sxs-lookup"><span data-stu-id="563d4-168">NOTES</span></span>

* <span data-ttu-id="563d4-169">若要建立新的別名，請使用 Set-Alias 或 New-Alias。</span><span class="sxs-lookup"><span data-stu-id="563d4-169">To create a new alias, use Set-Alias or New-Alias.</span></span> <span data-ttu-id="563d4-170">若要變更別名，請使用 **Set-Alias** 。</span><span class="sxs-lookup"><span data-stu-id="563d4-170">To change an alias, use **Set-Alias** .</span></span> <span data-ttu-id="563d4-171">若要刪除別名，請使用 Remove-Item。</span><span class="sxs-lookup"><span data-stu-id="563d4-171">To delete an alias, use Remove-Item.</span></span>

*

## <span data-ttu-id="563d4-172">相關連結</span><span class="sxs-lookup"><span data-stu-id="563d4-172">RELATED LINKS</span></span>

[<span data-ttu-id="563d4-173">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="563d4-173">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="563d4-174">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="563d4-174">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="563d4-175">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="563d4-175">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="563d4-176">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="563d4-176">Set-Alias</span></span>](Set-Alias.md)