---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 438f089c1cd6e647ae5ee858234a3919bdc0328d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204323"
---
# <span data-ttu-id="64d3c-103">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="64d3c-103">Import-Alias</span></span>

## <span data-ttu-id="64d3c-104">概要</span><span class="sxs-lookup"><span data-stu-id="64d3c-104">SYNOPSIS</span></span>
<span data-ttu-id="64d3c-105">匯入來自檔案的別名清單。</span><span class="sxs-lookup"><span data-stu-id="64d3c-105">Imports an alias list from a file.</span></span>

## <span data-ttu-id="64d3c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="64d3c-106">SYNTAX</span></span>

### <span data-ttu-id="64d3c-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="64d3c-107">ByPath (Default)</span></span>

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="64d3c-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="64d3c-108">ByLiteralPath</span></span>

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="64d3c-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="64d3c-109">DESCRIPTION</span></span>

<span data-ttu-id="64d3c-110">Cmdlet 會從檔案匯 `Import-Alias` 入別名清單。</span><span class="sxs-lookup"><span data-stu-id="64d3c-110">The `Import-Alias` cmdlet imports an alias list from a file.</span></span>

<span data-ttu-id="64d3c-111">從 Windows PowerShell 3.0 開始，做為安全性功能， `Import-Alias` 預設不會覆寫現有的別名。</span><span class="sxs-lookup"><span data-stu-id="64d3c-111">Beginning in Windows PowerShell 3.0, as a security feature, `Import-Alias` does not overwrite existing aliases by default.</span></span>
<span data-ttu-id="64d3c-112">若要覆寫現有的別名，請在確定別名檔案的內容安全之後，使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="64d3c-112">To overwrite an existing alias, after assuring that the contents of the alias file is safe, use the **Force** parameter.</span></span>

## <span data-ttu-id="64d3c-113">範例</span><span class="sxs-lookup"><span data-stu-id="64d3c-113">EXAMPLES</span></span>

### <span data-ttu-id="64d3c-114">範例 1︰從檔案匯入別名</span><span class="sxs-lookup"><span data-stu-id="64d3c-114">Example 1: Import aliases from a file</span></span>

```powershell
Import-Alias test.txt
```

<span data-ttu-id="64d3c-115">此命令從名為 test.txt 的檔案匯入別名資訊。</span><span class="sxs-lookup"><span data-stu-id="64d3c-115">This command imports alias information from a file named test.txt.</span></span>

## <span data-ttu-id="64d3c-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="64d3c-116">PARAMETERS</span></span>

### <span data-ttu-id="64d3c-117">-Force</span><span class="sxs-lookup"><span data-stu-id="64d3c-117">-Force</span></span>

<span data-ttu-id="64d3c-118">允許 Cmdlet 匯入已定義或是唯讀的別名。</span><span class="sxs-lookup"><span data-stu-id="64d3c-118">Allows the cmdlet to import an alias that is already defined or is read only.</span></span>
<span data-ttu-id="64d3c-119">您可以使用下列命令來顯示與目前定義的別名相關的資訊：</span><span class="sxs-lookup"><span data-stu-id="64d3c-119">You can use the following command to display information about the currently-defined aliases:</span></span>

`Get-Alias | Select-Object Name, Options`

<span data-ttu-id="64d3c-120">如果相對應的別名是唯讀的，它將會顯示在 **Options** 屬性的值中。</span><span class="sxs-lookup"><span data-stu-id="64d3c-120">If the corresponding alias is read-only, it will be displayed in the value of the **Options** property.</span></span>

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

### <span data-ttu-id="64d3c-121">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="64d3c-121">-LiteralPath</span></span>

<span data-ttu-id="64d3c-122">指定包含匯出之別名資訊的檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="64d3c-122">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="64d3c-123">與 **Path** 參數不同， **LiteralPath** 參數的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="64d3c-123">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="64d3c-124">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="64d3c-124">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="64d3c-125">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="64d3c-125">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="64d3c-126">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="64d3c-126">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="64d3c-127">-PassThru</span><span class="sxs-lookup"><span data-stu-id="64d3c-127">-PassThru</span></span>

<span data-ttu-id="64d3c-128">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="64d3c-128">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="64d3c-129">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="64d3c-129">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="64d3c-130">-Path</span><span class="sxs-lookup"><span data-stu-id="64d3c-130">-Path</span></span>

<span data-ttu-id="64d3c-131">指定包含匯出之別名資訊的檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="64d3c-131">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="64d3c-132">允許使用萬用字元，但它們必須解析為單一名稱。</span><span class="sxs-lookup"><span data-stu-id="64d3c-132">Wildcards are allowed but they must resolve to a single name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="64d3c-133">-Scope</span><span class="sxs-lookup"><span data-stu-id="64d3c-133">-Scope</span></span>

<span data-ttu-id="64d3c-134">指定要匯入別名的範圍。</span><span class="sxs-lookup"><span data-stu-id="64d3c-134">Specifies the scope into which the aliases are imported.</span></span>
<span data-ttu-id="64d3c-135">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="64d3c-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="64d3c-136">全球</span><span class="sxs-lookup"><span data-stu-id="64d3c-136">Global</span></span>
- <span data-ttu-id="64d3c-137">本機</span><span class="sxs-lookup"><span data-stu-id="64d3c-137">Local</span></span>
- <span data-ttu-id="64d3c-138">指令碼</span><span class="sxs-lookup"><span data-stu-id="64d3c-138">Script</span></span>
- <span data-ttu-id="64d3c-139">相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。</span><span class="sxs-lookup"><span data-stu-id="64d3c-139">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="64d3c-140">Local 為預設值。</span><span class="sxs-lookup"><span data-stu-id="64d3c-140">The default is Local.</span></span>
<span data-ttu-id="64d3c-141">如需詳細資訊，請參閱 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="64d3c-141">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="64d3c-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="64d3c-142">-Confirm</span></span>

<span data-ttu-id="64d3c-143">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="64d3c-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="64d3c-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="64d3c-144">-WhatIf</span></span>

<span data-ttu-id="64d3c-145">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="64d3c-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="64d3c-146">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="64d3c-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="64d3c-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="64d3c-147">CommonParameters</span></span>

<span data-ttu-id="64d3c-148">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="64d3c-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="64d3c-149">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="64d3c-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="64d3c-150">輸入</span><span class="sxs-lookup"><span data-stu-id="64d3c-150">INPUTS</span></span>

### <span data-ttu-id="64d3c-151">System.String</span><span class="sxs-lookup"><span data-stu-id="64d3c-151">System.String</span></span>

<span data-ttu-id="64d3c-152">您可以使用管線將包含路徑的字串傳送至 `Import-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="64d3c-152">You can pipe a string that contains a path to `Import-Alias`.</span></span>

## <span data-ttu-id="64d3c-153">輸出</span><span class="sxs-lookup"><span data-stu-id="64d3c-153">OUTPUTS</span></span>

### <span data-ttu-id="64d3c-154">無或 System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="64d3c-154">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="64d3c-155">當您使用 **Passthru** 參數時，會傳回 `Import-Alias` 代表別名的 **system.management.automation.aliasinfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="64d3c-155">When you use the **Passthru** parameter, `Import-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="64d3c-156">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="64d3c-156">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="64d3c-157">注意</span><span class="sxs-lookup"><span data-stu-id="64d3c-157">NOTES</span></span>

## <span data-ttu-id="64d3c-158">相關連結</span><span class="sxs-lookup"><span data-stu-id="64d3c-158">RELATED LINKS</span></span>

[<span data-ttu-id="64d3c-159">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="64d3c-159">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="64d3c-160">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="64d3c-160">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="64d3c-161">New-Alias</span><span class="sxs-lookup"><span data-stu-id="64d3c-161">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="64d3c-162">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="64d3c-162">Set-Alias</span></span>](Set-Alias.md)
