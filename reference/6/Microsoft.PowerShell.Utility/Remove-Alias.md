---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 08ef751e0573f896c5f63737b00b55ab77ae73e3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204319"
---
# <span data-ttu-id="a9f29-103">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="a9f29-103">Remove-Alias</span></span>

## <span data-ttu-id="a9f29-104">概要</span><span class="sxs-lookup"><span data-stu-id="a9f29-104">SYNOPSIS</span></span>
<span data-ttu-id="a9f29-105">移除目前會話中的別名。</span><span class="sxs-lookup"><span data-stu-id="a9f29-105">Remove an alias from the current session.</span></span>

## <span data-ttu-id="a9f29-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a9f29-106">SYNTAX</span></span>

### <span data-ttu-id="a9f29-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="a9f29-107">Default (Default)</span></span>

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="a9f29-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a9f29-108">DESCRIPTION</span></span>

<span data-ttu-id="a9f29-109">`Remove-Alias`Cmdlet 會從目前的 PowerShell 會話中移除別名。</span><span class="sxs-lookup"><span data-stu-id="a9f29-109">The `Remove-Alias` cmdlet removes an alias from the current PowerShell session.</span></span> <span data-ttu-id="a9f29-110">若要移除 **選項** 屬性設為 **ReadOnly** 的別名，請使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="a9f29-110">To remove an alias with the **Option** property set to **ReadOnly** , use the **Force** parameter.</span></span>

<span data-ttu-id="a9f29-111">`Remove-Alias`Cmdlet 是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="a9f29-111">The `Remove-Alias` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="a9f29-112">範例</span><span class="sxs-lookup"><span data-stu-id="a9f29-112">EXAMPLES</span></span>

### <span data-ttu-id="a9f29-113">範例 1-移除別名</span><span class="sxs-lookup"><span data-stu-id="a9f29-113">Example 1 - Remove an alias</span></span>

<span data-ttu-id="a9f29-114">此範例會移除名為 `del` 的別名，表示 `Remove-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a9f29-114">This example removes an alias named `del` that represents the `Remove-Item` cmdlet.</span></span>

```powershell
Remove-Alias -Name del
```

### <span data-ttu-id="a9f29-115">範例 2-移除所有的非常數別名</span><span class="sxs-lookup"><span data-stu-id="a9f29-115">Example 2 - Remove all non-Constant aliases</span></span>

<span data-ttu-id="a9f29-116">此範例會移除目前 PowerShell 會話中的所有別名，但 **選項** 屬性設為 **常數** 的別名除外。</span><span class="sxs-lookup"><span data-stu-id="a9f29-116">This example removes all aliases from the current PowerShell session, except for aliases with the **Options** property set to **Constant** .</span></span> <span data-ttu-id="a9f29-117">執行命令之後，別名可在其他 PowerShell 會話或新的 PowerShell 會話中使用。</span><span class="sxs-lookup"><span data-stu-id="a9f29-117">After the command is run, the aliases are available in other PowerShell sessions or new PowerShell sessions.</span></span>

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

<span data-ttu-id="a9f29-118">`Get-Alias` 取得 PowerShell 會話中的所有別名，並將物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="a9f29-118">`Get-Alias` gets all the aliases in the PowerShell session and sends the objects down the pipeline.</span></span>
<span data-ttu-id="a9f29-119">`Where-Object` 使用腳本區塊，而自動變數 (`$_`) 和 **Options** 屬性代表目前的管線物件。</span><span class="sxs-lookup"><span data-stu-id="a9f29-119">`Where-Object` uses a script block, and the automatic variable (`$_`) and **Options** property represent the current pipeline object.</span></span> <span data-ttu-id="a9f29-120">參數 **NE** (不等於) ，會選取沒有設定為 **常數** 之 **選項** 值的物件。</span><span class="sxs-lookup"><span data-stu-id="a9f29-120">The parameter **NE** (not equal), selects objects that don't have an **Options** value set to **Constant** .</span></span> <span data-ttu-id="a9f29-121">`Remove-Alias` 使用 **Force** 參數從 PowerShell 會話移除別名，包括唯讀別名。</span><span class="sxs-lookup"><span data-stu-id="a9f29-121">`Remove-Alias` uses the **Force** parameter to remove aliases, including read-only aliases, from the PowerShell session.</span></span>

## <span data-ttu-id="a9f29-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a9f29-122">PARAMETERS</span></span>

### <span data-ttu-id="a9f29-123">-Force</span><span class="sxs-lookup"><span data-stu-id="a9f29-123">-Force</span></span>

<span data-ttu-id="a9f29-124">指出此 Cmdlet 會移除別名，包括 **選項** 屬性設為 **ReadOnly** 的別名。</span><span class="sxs-lookup"><span data-stu-id="a9f29-124">Indicates that the cmdlet removes an alias, including aliases with the **Option** property set to **ReadOnly** .</span></span> <span data-ttu-id="a9f29-125">**Force** 參數無法移除 **選項** 屬性設為 **常數** 的別名。</span><span class="sxs-lookup"><span data-stu-id="a9f29-125">The **Force** parameter can't remove an alias with an **Option** property set to **Constant** .</span></span>

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

### <span data-ttu-id="a9f29-126">-Name</span><span class="sxs-lookup"><span data-stu-id="a9f29-126">-Name</span></span>

<span data-ttu-id="a9f29-127">指定要移除之別名的名稱。</span><span class="sxs-lookup"><span data-stu-id="a9f29-127">Specifies the name of the alias to remove.</span></span>

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

### <span data-ttu-id="a9f29-128">-Scope</span><span class="sxs-lookup"><span data-stu-id="a9f29-128">-Scope</span></span>

<span data-ttu-id="a9f29-129">只會影響指定範圍內的別名。</span><span class="sxs-lookup"><span data-stu-id="a9f29-129">Affects only the aliases in the specified scope.</span></span> <span data-ttu-id="a9f29-130">預設範圍為 [ **本機** ]。</span><span class="sxs-lookup"><span data-stu-id="a9f29-130">The default scope is **Local** .</span></span> <span data-ttu-id="a9f29-131">如需詳細資訊，請參閱 [about_Scopes](../microsoft.powershell.core/about/about_scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="a9f29-131">For more information, see [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).</span></span>

<span data-ttu-id="a9f29-132">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="a9f29-132">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a9f29-133">全球</span><span class="sxs-lookup"><span data-stu-id="a9f29-133">Global</span></span>
- <span data-ttu-id="a9f29-134">本機</span><span class="sxs-lookup"><span data-stu-id="a9f29-134">Local</span></span>
- <span data-ttu-id="a9f29-135">指令碼</span><span class="sxs-lookup"><span data-stu-id="a9f29-135">Script</span></span>
- <span data-ttu-id="a9f29-136">相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。</span><span class="sxs-lookup"><span data-stu-id="a9f29-136">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

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

### <span data-ttu-id="a9f29-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a9f29-137">CommonParameters</span></span>

<span data-ttu-id="a9f29-138">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a9f29-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a9f29-139">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a9f29-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a9f29-140">輸入</span><span class="sxs-lookup"><span data-stu-id="a9f29-140">INPUTS</span></span>

### <span data-ttu-id="a9f29-141">System.String[]</span><span class="sxs-lookup"><span data-stu-id="a9f29-141">System.String[]</span></span>

<span data-ttu-id="a9f29-142">您可以使用管線將別名物件傳送至 **移除別名** 。</span><span class="sxs-lookup"><span data-stu-id="a9f29-142">You can pipe an alias object to **Remove-Alias** .</span></span>

## <span data-ttu-id="a9f29-143">輸出</span><span class="sxs-lookup"><span data-stu-id="a9f29-143">OUTPUTS</span></span>

### <span data-ttu-id="a9f29-144">無</span><span class="sxs-lookup"><span data-stu-id="a9f29-144">None</span></span>

<span data-ttu-id="a9f29-145">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a9f29-145">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="a9f29-146">注意</span><span class="sxs-lookup"><span data-stu-id="a9f29-146">NOTES</span></span>

<span data-ttu-id="a9f29-147">變更只會影響目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="a9f29-147">Changes only affect the current scope.</span></span> <span data-ttu-id="a9f29-148">若要從所有會話中移除別名，請將 **移除別名** 命令新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="a9f29-148">To remove an alias from all sessions, add a **Remove-Alias** command to your PowerShell profile.</span></span>

<span data-ttu-id="a9f29-149">如需詳細資訊，請參閱 [about_Aliases](../microsoft.powershell.core/about/about_aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="a9f29-149">For more information, see [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).</span></span>

## <span data-ttu-id="a9f29-150">相關連結</span><span class="sxs-lookup"><span data-stu-id="a9f29-150">RELATED LINKS</span></span>

[<span data-ttu-id="a9f29-151">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="a9f29-151">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="a9f29-152">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="a9f29-152">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="a9f29-153">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="a9f29-153">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="a9f29-154">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="a9f29-154">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="a9f29-155">New-Alias</span><span class="sxs-lookup"><span data-stu-id="a9f29-155">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="a9f29-156">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="a9f29-156">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="a9f29-157">Where-Object</span><span class="sxs-lookup"><span data-stu-id="a9f29-157">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
