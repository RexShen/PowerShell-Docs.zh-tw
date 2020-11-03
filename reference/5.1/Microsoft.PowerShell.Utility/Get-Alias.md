---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: cf936b63063b3381c4aac54e246ec921b61c3b22
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203299"
---
# <span data-ttu-id="ae4e5-103">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="ae4e5-103">Get-Alias</span></span>

## <span data-ttu-id="ae4e5-104">概要</span><span class="sxs-lookup"><span data-stu-id="ae4e5-104">SYNOPSIS</span></span>

<span data-ttu-id="ae4e5-105">取得目前工作階段的別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-105">Gets the aliases for the current session.</span></span>

## <span data-ttu-id="ae4e5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ae4e5-106">SYNTAX</span></span>

### <span data-ttu-id="ae4e5-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="ae4e5-107">Default (Default)</span></span>

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="ae4e5-108">定義</span><span class="sxs-lookup"><span data-stu-id="ae4e5-108">Definition</span></span>

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="ae4e5-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ae4e5-109">DESCRIPTION</span></span>

<span data-ttu-id="ae4e5-110">**取得別名** Cmdlet 會取得目前會話中的別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-110">The **Get-Alias** cmdlet gets the aliases in the current session.</span></span>
<span data-ttu-id="ae4e5-111">這包括內建的別名、您已設定或匯入的別名，以及您已新增至 PowerShell 設定檔的別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-111">This includes built-in aliases, aliases that you have set or imported, and aliases that you have added to your PowerShell profile.</span></span>

<span data-ttu-id="ae4e5-112">根據預設， **Get 別名** 會使用別名並傳回命令名稱。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-112">By default, **Get-Alias** takes an alias and returns the command name.</span></span>
<span data-ttu-id="ae4e5-113">當您使用 *定義* 參數時， **Get 別名** 會接受命令名稱並傳回它的別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-113">When you use the *Definition* parameter, **Get-Alias** takes a command name and returns its aliases.</span></span>

<span data-ttu-id="ae4e5-114">從 Windows PowerShell 3.0 開始， **Get 別名** 會以格式顯示非連字號的別名名稱， `<alias> -> <definition>` 讓您更容易找到所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-114">Beginning in Windows PowerShell 3.0, **Get-Alias** displays non-hyphenated alias names in an `<alias> -> <definition>` format to make it even easier to find the information that you need.</span></span>

## <span data-ttu-id="ae4e5-115">範例</span><span class="sxs-lookup"><span data-stu-id="ae4e5-115">EXAMPLES</span></span>

### <span data-ttu-id="ae4e5-116">範例1：取得目前會話中的所有別名</span><span class="sxs-lookup"><span data-stu-id="ae4e5-116">Example 1: Get all aliases in the current session</span></span>

```
PS C:\> Get-Alias

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
Alias           clhy -> Clear-History
...
```

<span data-ttu-id="ae4e5-117">此命令取得目前工作階段中的所有別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-117">This command gets all aliases in the current session.</span></span>

<span data-ttu-id="ae4e5-118">輸出 `<alias> -> <definition>` 會顯示 Windows PowerShell 3.0 中引進的格式。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-118">The output shows the `<alias> -> <definition>` format that was introduced in Windows PowerShell 3.0.</span></span>
<span data-ttu-id="ae4e5-119">此格式只用於不含連字號的別名，因為含連字號的別名通常是 Cmdlet 和函式的慣用名稱，而非暱稱。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-119">This format is used only for aliases that do not include hyphens, because aliases with hyphens are typically preferred names for cmdlets and functions, rather than nicknames.</span></span>

### <span data-ttu-id="ae4e5-120">範例2：依名稱取得別名</span><span class="sxs-lookup"><span data-stu-id="ae4e5-120">Example 2: Get aliases by name</span></span>

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

<span data-ttu-id="ae4e5-121">此命令會取得以 gp 或 sp 開頭的所有別名，但以 ps 結尾的別名除外。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-121">This command gets all aliases that begin with gp or sp, except for aliases that end with ps.</span></span>

### <span data-ttu-id="ae4e5-122">範例3：取得 Cmdlet 的別名</span><span class="sxs-lookup"><span data-stu-id="ae4e5-122">Example 3: Get aliases for a cmdlet</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

<span data-ttu-id="ae4e5-123">此命令取得 Get-ChildItem Cmdlet 的別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-123">This command gets the aliases for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="ae4e5-124">依預設，當您知道別名時， **取得別名** Cmdlet 會取得專案名稱。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-124">By default, the **Get-Alias** cmdlet gets the item name when you know the alias.</span></span>
<span data-ttu-id="ae4e5-125">當您知道專案名稱時， *定義* 參數會取得別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-125">The *Definition* parameter gets the alias when you know the item name.</span></span>

### <span data-ttu-id="ae4e5-126">範例4：依屬性取得別名</span><span class="sxs-lookup"><span data-stu-id="ae4e5-126">Example 4: Get aliases by property</span></span>

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

<span data-ttu-id="ae4e5-127">此命令會取得 Options 屬性值為 ReadOnly 的所有別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-127">This command gets all aliases in which the value of the Options property is ReadOnly.</span></span>
<span data-ttu-id="ae4e5-128">此命令可讓您快速找出 PowerShell 內建的別名，因為它們具有 ReadOnly 選項。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-128">This command provides a quick way to find the aliases that are built into PowerShell, because they have the ReadOnly option.</span></span>

<span data-ttu-id="ae4e5-129">選項只是 System.management.automation.aliasinfo 物件的一個屬性，可 **取得別名** 。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-129">Options is just one property of the AliasInfo objects that **Get-Alias** gets.</span></span>
<span data-ttu-id="ae4e5-130">若要尋找 System.management.automation.aliasinfo 物件的所有屬性和方法，請輸入 `Get-Alias | get-member` 。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-130">To find all properties and methods of AliasInfo objects, type `Get-Alias | get-member`.</span></span>

### <span data-ttu-id="ae4e5-131">範例5：依名稱取得別名並依開頭字母篩選</span><span class="sxs-lookup"><span data-stu-id="ae4e5-131">Example 5: Get aliases by name and filter by beginning letter</span></span>

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

<span data-ttu-id="ae4e5-132">此範例取得名稱結尾為 "-PSSession" 且開頭不是 "e" 之命令的別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-132">This example gets aliases for commands that have names that end in "-PSSession", except for those that begin with "e".</span></span>

<span data-ttu-id="ae4e5-133">命令使用 *Scope* 參數將命令套用至全域範圍。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-133">The command uses the *Scope* parameter to apply the command in the global scope.</span></span>
<span data-ttu-id="ae4e5-134">當您想要取得工作階段中的別名時，這在指令碼中相當有用。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-134">This is useful in scripts when you want to get the aliases in the session.</span></span>

## <span data-ttu-id="ae4e5-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ae4e5-135">PARAMETERS</span></span>

### <span data-ttu-id="ae4e5-136">-Definition</span><span class="sxs-lookup"><span data-stu-id="ae4e5-136">-Definition</span></span>

<span data-ttu-id="ae4e5-137">取得指定項目的別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-137">Gets the aliases for the specified item.</span></span>
<span data-ttu-id="ae4e5-138">請輸入 Cmdlet、函式、指令碼、檔案或可執行檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-138">Enter the name of a cmdlet, function, script, file, or executable file.</span></span>

<span data-ttu-id="ae4e5-139">此參數稱為 *定義* ，因為它會在別名物件的定義屬性中搜尋專案名稱。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-139">This parameter is called *Definition* , because it searches for the item name in the Definition property of the alias object.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Definition
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="ae4e5-140">-Exclude</span><span class="sxs-lookup"><span data-stu-id="ae4e5-140">-Exclude</span></span>

<span data-ttu-id="ae4e5-141">省略指定的項目。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-141">Omits the specified items.</span></span>
<span data-ttu-id="ae4e5-142">此參數的值會限定 Name 和 Definition 參數。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-142">The value of this parameter qualifies the Name and Definition parameters.</span></span>
<span data-ttu-id="ae4e5-143">輸入名稱、定義或模式，例如 "s\*"。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-143">Enter a name, a definition, or a pattern, such as "s\*".</span></span>
<span data-ttu-id="ae4e5-144">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-144">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="ae4e5-145">-Name</span><span class="sxs-lookup"><span data-stu-id="ae4e5-145">-Name</span></span>

<span data-ttu-id="ae4e5-146">指定此 Cmdlet 取得的別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-146">Specifies the aliases that this cmdlet gets.</span></span>
<span data-ttu-id="ae4e5-147">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-147">Wildcards are permitted.</span></span>
<span data-ttu-id="ae4e5-148">依預設，會抓取 `Get-Alias` 為目前會話定義的所有別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-148">By default, `Get-Alias` retrieves all aliases defined for the current session.</span></span>
<span data-ttu-id="ae4e5-149">參數名稱 **名稱** 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-149">The parameter name **Name** is optional.</span></span>
<span data-ttu-id="ae4e5-150">您也可以透過管線將別名名稱傳送至 `Get-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-150">You can also pipe alias names to `Get-Alias`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: All aliases
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ae4e5-151">-Scope</span><span class="sxs-lookup"><span data-stu-id="ae4e5-151">-Scope</span></span>

<span data-ttu-id="ae4e5-152">指定此 Cmdlet 取得別名的範圍。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-152">Specifies the scope for which this cmdlet gets aliases.</span></span>
<span data-ttu-id="ae4e5-153">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="ae4e5-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ae4e5-154">全球</span><span class="sxs-lookup"><span data-stu-id="ae4e5-154">Global</span></span>
- <span data-ttu-id="ae4e5-155">本機</span><span class="sxs-lookup"><span data-stu-id="ae4e5-155">Local</span></span>
- <span data-ttu-id="ae4e5-156">指令碼</span><span class="sxs-lookup"><span data-stu-id="ae4e5-156">Script</span></span>
- <span data-ttu-id="ae4e5-157">相對於目前範圍的數字 (0 至範圍數目，0 為目前範圍，1 為其父系)。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-157">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="ae4e5-158">Local 為預設值。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-158">Local is the default.</span></span>
<span data-ttu-id="ae4e5-159">如需詳細資訊，請參閱 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-159">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="ae4e5-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ae4e5-160">CommonParameters</span></span>

<span data-ttu-id="ae4e5-161">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ae4e5-162">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ae4e5-163">輸入</span><span class="sxs-lookup"><span data-stu-id="ae4e5-163">INPUTS</span></span>

### <span data-ttu-id="ae4e5-164">System.String</span><span class="sxs-lookup"><span data-stu-id="ae4e5-164">System.String</span></span>

<span data-ttu-id="ae4e5-165">您可以透過管線將別名名稱傳送至 **取得別名** 。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-165">You can pipe alias names to **Get-Alias** .</span></span>

## <span data-ttu-id="ae4e5-166">輸出</span><span class="sxs-lookup"><span data-stu-id="ae4e5-166">OUTPUTS</span></span>

### <span data-ttu-id="ae4e5-167">System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="ae4e5-167">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="ae4e5-168">**取得別名** 會傳回代表每個別名的物件。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-168">**Get-Alias** returns an object that represents each alias.</span></span>
<span data-ttu-id="ae4e5-169">**取得別名** 會針對每個別名傳回相同的物件，但 PowerShell 會使用以箭號為基礎的格式來顯示非連字號別名的名稱。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-169">**Get-Alias** returns the same object for every alias, but PowerShell uses an arrow-based format to display the names of non-hyphenated aliases.</span></span>

## <span data-ttu-id="ae4e5-170">注意</span><span class="sxs-lookup"><span data-stu-id="ae4e5-170">NOTES</span></span>

- <span data-ttu-id="ae4e5-171">若要建立新的別名，請使用 Set-Alias 或 New-Alias。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-171">To create a new alias, use Set-Alias or New-Alias.</span></span> <span data-ttu-id="ae4e5-172">若要刪除別名，請使用 Remove-Item。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-172">To delete an alias, use Remove-Item.</span></span>
- <span data-ttu-id="ae4e5-173">箭號型別名名稱格式不會用於含連字號的別名。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-173">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="ae4e5-174">這些可能是 Cmdlet 和函式的慣用替代名稱，而不是典型的縮寫或暱稱。</span><span class="sxs-lookup"><span data-stu-id="ae4e5-174">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames.</span></span>

## <span data-ttu-id="ae4e5-175">相關連結</span><span class="sxs-lookup"><span data-stu-id="ae4e5-175">RELATED LINKS</span></span>

[<span data-ttu-id="ae4e5-176">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="ae4e5-176">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="ae4e5-177">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="ae4e5-177">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="ae4e5-178">New-Alias</span><span class="sxs-lookup"><span data-stu-id="ae4e5-178">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="ae4e5-179">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="ae4e5-179">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="ae4e5-180">別名提供者</span><span class="sxs-lookup"><span data-stu-id="ae4e5-180">Alias Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[<span data-ttu-id="ae4e5-181">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="ae4e5-181">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)
