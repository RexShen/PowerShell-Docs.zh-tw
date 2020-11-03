---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 7406b2cac771ae7a741af92cd362cce834c59a50
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203664"
---
# <span data-ttu-id="f6be2-103">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="f6be2-103">Remove-Alias</span></span>

## <span data-ttu-id="f6be2-104">概要</span><span class="sxs-lookup"><span data-stu-id="f6be2-104">SYNOPSIS</span></span>
<span data-ttu-id="f6be2-105">移除目前會話中的別名。</span><span class="sxs-lookup"><span data-stu-id="f6be2-105">Remove an alias from the current session.</span></span>

## <span data-ttu-id="f6be2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f6be2-106">SYNTAX</span></span>

### <span data-ttu-id="f6be2-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="f6be2-107">Default (Default)</span></span>

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="f6be2-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f6be2-108">DESCRIPTION</span></span>

<span data-ttu-id="f6be2-109">`Remove-Alias`Cmdlet 會從目前的 PowerShell 會話中移除別名。</span><span class="sxs-lookup"><span data-stu-id="f6be2-109">The `Remove-Alias` cmdlet removes an alias from the current PowerShell session.</span></span> <span data-ttu-id="f6be2-110">若要移除 **選項** 屬性設為 **ReadOnly** 的別名，請使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="f6be2-110">To remove an alias with the **Option** property set to **ReadOnly** , use the **Force** parameter.</span></span>

<span data-ttu-id="f6be2-111">`Remove-Alias`Cmdlet 是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="f6be2-111">The `Remove-Alias` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="f6be2-112">範例</span><span class="sxs-lookup"><span data-stu-id="f6be2-112">EXAMPLES</span></span>

### <span data-ttu-id="f6be2-113">範例 1-移除別名</span><span class="sxs-lookup"><span data-stu-id="f6be2-113">Example 1 - Remove an alias</span></span>

<span data-ttu-id="f6be2-114">此範例會移除名為 `del` 的別名，表示 `Remove-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f6be2-114">This example removes an alias named `del` that represents the `Remove-Item` cmdlet.</span></span>

```powershell
Remove-Alias -Name del
```

### <span data-ttu-id="f6be2-115">範例 2-移除所有的非常數別名</span><span class="sxs-lookup"><span data-stu-id="f6be2-115">Example 2 - Remove all non-Constant aliases</span></span>

<span data-ttu-id="f6be2-116">此範例會移除目前 PowerShell 會話中的所有別名，但 **選項** 屬性設為 **常數** 的別名除外。</span><span class="sxs-lookup"><span data-stu-id="f6be2-116">This example removes all aliases from the current PowerShell session, except for aliases with the **Options** property set to **Constant** .</span></span> <span data-ttu-id="f6be2-117">執行命令之後，別名可在其他 PowerShell 會話或新的 PowerShell 會話中使用。</span><span class="sxs-lookup"><span data-stu-id="f6be2-117">After the command is run, the aliases are available in other PowerShell sessions or new PowerShell sessions.</span></span>

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

<span data-ttu-id="f6be2-118">`Get-Alias` 取得 PowerShell 會話中的所有別名，並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="f6be2-118">`Get-Alias` gets all the aliases in the PowerShell session and sends the objects down the pipeline.</span></span>
<span data-ttu-id="f6be2-119">`Where-Object` 使用腳本區塊，而自動變數 (`$_`) 和 **Options** 屬性代表目前的管線物件。</span><span class="sxs-lookup"><span data-stu-id="f6be2-119">`Where-Object` uses a script block, and the automatic variable (`$_`) and **Options** property represent the current pipeline object.</span></span> <span data-ttu-id="f6be2-120">參數 **NE** (不等於) ，會選取沒有設定為 **常數** 之 **選項** 值的物件。</span><span class="sxs-lookup"><span data-stu-id="f6be2-120">The parameter **NE** (not equal), selects objects that don't have an **Options** value set to **Constant** .</span></span> <span data-ttu-id="f6be2-121">`Remove-Alias` 使用 **Force** 參數從 PowerShell 會話移除別名，包括唯讀別名。</span><span class="sxs-lookup"><span data-stu-id="f6be2-121">`Remove-Alias` uses the **Force** parameter to remove aliases, including read-only aliases, from the PowerShell session.</span></span>

## <span data-ttu-id="f6be2-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f6be2-122">PARAMETERS</span></span>

### <span data-ttu-id="f6be2-123">-Force</span><span class="sxs-lookup"><span data-stu-id="f6be2-123">-Force</span></span>

<span data-ttu-id="f6be2-124">指出此 Cmdlet 會移除別名，包括 **選項** 屬性設為 **ReadOnly** 的別名。</span><span class="sxs-lookup"><span data-stu-id="f6be2-124">Indicates that the cmdlet removes an alias, including aliases with the **Option** property set to **ReadOnly** .</span></span> <span data-ttu-id="f6be2-125">**Force** 參數無法移除 **選項** 屬性設為 **常數** 的別名。</span><span class="sxs-lookup"><span data-stu-id="f6be2-125">The **Force** parameter can't remove an alias with an **Option** property set to **Constant** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6be2-126">-Name</span><span class="sxs-lookup"><span data-stu-id="f6be2-126">-Name</span></span>

<span data-ttu-id="f6be2-127">指定要移除之別名的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6be2-127">Specifies the name of the alias to remove.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f6be2-128">-Scope</span><span class="sxs-lookup"><span data-stu-id="f6be2-128">-Scope</span></span>

<span data-ttu-id="f6be2-129">只會影響指定範圍內的別名。</span><span class="sxs-lookup"><span data-stu-id="f6be2-129">Affects only the aliases in the specified scope.</span></span> <span data-ttu-id="f6be2-130">預設範圍為 [ **本機** ]。</span><span class="sxs-lookup"><span data-stu-id="f6be2-130">The default scope is **Local** .</span></span> <span data-ttu-id="f6be2-131">如需詳細資訊，請參閱 [about_Scopes](../microsoft.powershell.core/about/about_scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="f6be2-131">For more information, see [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).</span></span>

<span data-ttu-id="f6be2-132">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="f6be2-132">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f6be2-133">全球</span><span class="sxs-lookup"><span data-stu-id="f6be2-133">Global</span></span>
- <span data-ttu-id="f6be2-134">本機</span><span class="sxs-lookup"><span data-stu-id="f6be2-134">Local</span></span>
- <span data-ttu-id="f6be2-135">指令碼</span><span class="sxs-lookup"><span data-stu-id="f6be2-135">Script</span></span>
- <span data-ttu-id="f6be2-136">相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。</span><span class="sxs-lookup"><span data-stu-id="f6be2-136">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f6be2-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f6be2-137">CommonParameters</span></span>

<span data-ttu-id="f6be2-138">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f6be2-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f6be2-139">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f6be2-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f6be2-140">輸入</span><span class="sxs-lookup"><span data-stu-id="f6be2-140">INPUTS</span></span>

### <span data-ttu-id="f6be2-141">System.String[]</span><span class="sxs-lookup"><span data-stu-id="f6be2-141">System.String[]</span></span>

<span data-ttu-id="f6be2-142">您可以使用管線將別名物件傳送至 **移除別名** 。</span><span class="sxs-lookup"><span data-stu-id="f6be2-142">You can pipe an alias object to **Remove-Alias** .</span></span>

## <span data-ttu-id="f6be2-143">輸出</span><span class="sxs-lookup"><span data-stu-id="f6be2-143">OUTPUTS</span></span>

### <span data-ttu-id="f6be2-144">無</span><span class="sxs-lookup"><span data-stu-id="f6be2-144">None</span></span>

<span data-ttu-id="f6be2-145">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f6be2-145">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="f6be2-146">注意</span><span class="sxs-lookup"><span data-stu-id="f6be2-146">NOTES</span></span>

<span data-ttu-id="f6be2-147">變更只會影響目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="f6be2-147">Changes only affect the current scope.</span></span> <span data-ttu-id="f6be2-148">若要從所有會話中移除別名，請將 **移除別名** 命令新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="f6be2-148">To remove an alias from all sessions, add a **Remove-Alias** command to your PowerShell profile.</span></span>

<span data-ttu-id="f6be2-149">如需詳細資訊，請參閱 [about_Aliases](../microsoft.powershell.core/about/about_aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="f6be2-149">For more information, see [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).</span></span>

## <span data-ttu-id="f6be2-150">相關連結</span><span class="sxs-lookup"><span data-stu-id="f6be2-150">RELATED LINKS</span></span>

[<span data-ttu-id="f6be2-151">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="f6be2-151">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="f6be2-152">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="f6be2-152">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="f6be2-153">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="f6be2-153">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="f6be2-154">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="f6be2-154">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="f6be2-155">New-Alias</span><span class="sxs-lookup"><span data-stu-id="f6be2-155">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="f6be2-156">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="f6be2-156">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="f6be2-157">Where-Object</span><span class="sxs-lookup"><span data-stu-id="f6be2-157">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

