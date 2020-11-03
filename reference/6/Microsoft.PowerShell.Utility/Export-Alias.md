---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Alias
ms.openlocfilehash: 5a732573a24da5de2a00bfd29abb3711218c64e3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204664"
---
# <span data-ttu-id="efb93-103">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="efb93-103">Export-Alias</span></span>

## <span data-ttu-id="efb93-104">概要</span><span class="sxs-lookup"><span data-stu-id="efb93-104">SYNOPSIS</span></span>
<span data-ttu-id="efb93-105">將目前已定義別名的相關資訊匯出至檔案。</span><span class="sxs-lookup"><span data-stu-id="efb93-105">Exports information about currently defined aliases to a file.</span></span>

## <span data-ttu-id="efb93-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="efb93-106">SYNTAX</span></span>

### <span data-ttu-id="efb93-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="efb93-107">ByPath (Default)</span></span>

```
Export-Alias [-Path] <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append] [-Force]
 [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="efb93-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="efb93-108">ByLiteralPath</span></span>

```
Export-Alias -LiteralPath <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append]
 [-Force] [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="efb93-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="efb93-109">DESCRIPTION</span></span>

<span data-ttu-id="efb93-110">Cmdlet 會將 `Export-Alias` 目前會話中的別名匯出至檔案。</span><span class="sxs-lookup"><span data-stu-id="efb93-110">The `Export-Alias` cmdlet exports the aliases in the current session to a file.</span></span>
<span data-ttu-id="efb93-111">如果輸出檔案不存在，此 Cmdlet 會建立它。</span><span class="sxs-lookup"><span data-stu-id="efb93-111">If the output file does not exist, the cmdlet will create it.</span></span>

<span data-ttu-id="efb93-112">`Export-Alias` 可以匯出特定範圍或所有範圍中的別名，它可以產生 CSV 格式的資料，或是您可以新增至會話或 PowerShell 設定檔的一連串 Set-Alias 命令。</span><span class="sxs-lookup"><span data-stu-id="efb93-112">`Export-Alias` can export the aliases in a particular scope or all scopes, it can generate the data in CSV format or as a series of Set-Alias commands that you can add to a session or to a PowerShell profile.</span></span>

## <span data-ttu-id="efb93-113">範例</span><span class="sxs-lookup"><span data-stu-id="efb93-113">EXAMPLES</span></span>

### <span data-ttu-id="efb93-114">範例1：匯出別名</span><span class="sxs-lookup"><span data-stu-id="efb93-114">Example 1: Export an alias</span></span>

```powershell
Export-Alias -Path "alias.csv"
```

<span data-ttu-id="efb93-115">此命令將目前的別名資訊匯出至目前目錄中名為 Alias.csv 的檔案。</span><span class="sxs-lookup"><span data-stu-id="efb93-115">This command exports current alias information to a file named Alias.csv in the current directory.</span></span>

### <span data-ttu-id="efb93-116">範例2：匯出別名，除非匯出檔案已存在</span><span class="sxs-lookup"><span data-stu-id="efb93-116">Example 2: Export an alias unless the export file already exists</span></span>

```powershell
Export-Alias -Path "alias.csv" -NoClobber
```

<span data-ttu-id="efb93-117">此命令將目前工作階段中的別名匯出至 Alias.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="efb93-117">This command exports the aliases in the current session to an Alias.csv file.</span></span>

<span data-ttu-id="efb93-118">因為指定了 **NoClobber** 參數，所以如果目前的目錄中已經有 Alias.csv 檔案，命令將會失敗。</span><span class="sxs-lookup"><span data-stu-id="efb93-118">Because the **NoClobber** parameter is specified, the command will fail if an Alias.csv file already exists in the current directory.</span></span>

### <span data-ttu-id="efb93-119">範例3：將別名附加至檔案</span><span class="sxs-lookup"><span data-stu-id="efb93-119">Example 3: Append aliases to a file</span></span>

```powershell
Export-Alias -Path "alias.csv" -Append -Description "Appended Aliases" -Force
```

<span data-ttu-id="efb93-120">此命令將目前工作階段中的別名附加至 Alias.csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="efb93-120">This command appends the aliases in the current session to the Alias.csv file.</span></span>

<span data-ttu-id="efb93-121">此命令會使用 **description** 參數將描述加入檔案頂端的批註。</span><span class="sxs-lookup"><span data-stu-id="efb93-121">The command uses the **Description** parameter to add a description to the comments at the top of the file.</span></span>

<span data-ttu-id="efb93-122">此命令也會使用 **Force** 參數來覆寫任何現有的 Alias.csv 檔案，即使這些檔案具有唯讀屬性也一樣。</span><span class="sxs-lookup"><span data-stu-id="efb93-122">The command also uses the **Force** parameter to overwrite any existing Alias.csv files, even if they have the read-only attribute.</span></span>

### <span data-ttu-id="efb93-123">範例4：將別名匯出為腳本</span><span class="sxs-lookup"><span data-stu-id="efb93-123">Example 4: Export aliases as a script</span></span>

```powershell
Export-Alias -Path "alias.ps1" -As Script
Add-Content -Path $Profile -Value (Get-Content alias.ps1)
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -FilePath .\alias.ps1
```

<span data-ttu-id="efb93-124">此範例顯示如何使用產生的腳本檔案格式 `Export-Alias` 。</span><span class="sxs-lookup"><span data-stu-id="efb93-124">This example shows how to use the script file format that `Export-Alias` generates.</span></span>

<span data-ttu-id="efb93-125">第一個命令將工作階段中的別名匯出至 Alias.ps1 檔案。</span><span class="sxs-lookup"><span data-stu-id="efb93-125">The first command exports the aliases in the session to the Alias.ps1 file.</span></span>
<span data-ttu-id="efb93-126">它使用 **As** 參數搭配 Script 值來產生檔案，其中包含每個別名的 Set-Alias 命令。</span><span class="sxs-lookup"><span data-stu-id="efb93-126">It uses the **As** parameter with a value of Script to generate a file that contains a Set-Alias command for each alias.</span></span>

<span data-ttu-id="efb93-127">第二個命令將 Alias.ps1 檔案中的別名加入 CurrentUser-CurrentHost 設定檔。</span><span class="sxs-lookup"><span data-stu-id="efb93-127">The second command adds the aliases in the Alias.ps1 file to the CurrentUser-CurrentHost profile.</span></span>
<span data-ttu-id="efb93-128">設定檔的路徑會儲存在變數中 `$Profile` 。</span><span class="sxs-lookup"><span data-stu-id="efb93-128">The path to the profile is saved in the `$Profile` variable.</span></span>
<span data-ttu-id="efb93-129">此命令會使用 `Get-Content` Cmdlet 來取得 Alias.ps1 檔案中的別名，並使用 `Add-Content` Cmdlet 將它們新增至設定檔。</span><span class="sxs-lookup"><span data-stu-id="efb93-129">The command uses the `Get-Content` cmdlet to get the aliases from the Alias.ps1 file and the `Add-Content` cmdlet to add them to the profile.</span></span>
<span data-ttu-id="efb93-130">如需詳細資訊，請參閱 about_Profiles。</span><span class="sxs-lookup"><span data-stu-id="efb93-130">For more information, see about_Profiles.</span></span>

<span data-ttu-id="efb93-131">第三個和第四個命令會將 Alias.ps1 檔案中的別名新增至 Server01 電腦上的遠端會話。</span><span class="sxs-lookup"><span data-stu-id="efb93-131">The third and fourth commands add the aliases in the Alias.ps1 file to a remote session on the Server01 computer.</span></span>
<span data-ttu-id="efb93-132">第三個命令會使用 `New-PSSession` Cmdlet 來建立會話。</span><span class="sxs-lookup"><span data-stu-id="efb93-132">The third command uses the `New-PSSession` cmdlet to create the session.</span></span>
<span data-ttu-id="efb93-133">第四個命令會使用 Cmdlet 的 **FilePath** 參數 `Invoke-Command` 在新的會話中執行 Alias.ps1 檔案。</span><span class="sxs-lookup"><span data-stu-id="efb93-133">The fourth command uses the **FilePath** parameter of the `Invoke-Command` cmdlet to run the Alias.ps1 file in the new session.</span></span>

## <span data-ttu-id="efb93-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="efb93-134">PARAMETERS</span></span>

### <span data-ttu-id="efb93-135">-Append</span><span class="sxs-lookup"><span data-stu-id="efb93-135">-Append</span></span>

<span data-ttu-id="efb93-136">指出此 Cmdlet 會將輸出附加至指定的檔案，而不是覆寫該檔案現有的內容。</span><span class="sxs-lookup"><span data-stu-id="efb93-136">Indicates that this cmdlet appends the output to the specified file, rather than overwriting the existing contents of that file.</span></span>

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

### <span data-ttu-id="efb93-137">-As</span><span class="sxs-lookup"><span data-stu-id="efb93-137">-As</span></span>

<span data-ttu-id="efb93-138">指定輸出格式。</span><span class="sxs-lookup"><span data-stu-id="efb93-138">Specifies the output format.</span></span>
<span data-ttu-id="efb93-139">預設值為 CSV。</span><span class="sxs-lookup"><span data-stu-id="efb93-139">CSV is the default.</span></span>
<span data-ttu-id="efb93-140">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="efb93-140">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="efb93-141">CSV。</span><span class="sxs-lookup"><span data-stu-id="efb93-141">CSV.</span></span>
<span data-ttu-id="efb93-142">以逗號分隔的值 (CSV) 格式。</span><span class="sxs-lookup"><span data-stu-id="efb93-142">Comma-separated value (CSV) format.</span></span>
- <span data-ttu-id="efb93-143">指令碼：</span><span class="sxs-lookup"><span data-stu-id="efb93-143">Script.</span></span>
<span data-ttu-id="efb93-144">`Set-Alias`針對每個匯出的別名建立命令。</span><span class="sxs-lookup"><span data-stu-id="efb93-144">Creates a `Set-Alias` command for each exported alias.</span></span>
<span data-ttu-id="efb93-145">如果您以 .ps1 副檔名命名輸出檔案，可以指令碼的方式執行它將別名加入任何工作階段。</span><span class="sxs-lookup"><span data-stu-id="efb93-145">If you name the output file with a .ps1 file name extension, you can run it as a script to add the aliases to any session.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ExportAliasFormat
Parameter Sets: (All)
Aliases:
Accepted values: Csv, Script

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efb93-146">-Description</span><span class="sxs-lookup"><span data-stu-id="efb93-146">-Description</span></span>

<span data-ttu-id="efb93-147">指定匯出檔案的描述。</span><span class="sxs-lookup"><span data-stu-id="efb93-147">Specifies the description of the exported file.</span></span>
<span data-ttu-id="efb93-148">描述會顯示在檔案頂端做為註解，後面接標頭資訊。</span><span class="sxs-lookup"><span data-stu-id="efb93-148">The description appears as a comment at the top of the file, following the header information.</span></span>

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

### <span data-ttu-id="efb93-149">-Force</span><span class="sxs-lookup"><span data-stu-id="efb93-149">-Force</span></span>

<span data-ttu-id="efb93-150">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="efb93-150">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="efb93-151">覆寫輸出檔案，即使檔案設定了唯讀屬性亦同。</span><span class="sxs-lookup"><span data-stu-id="efb93-151">Overwrites the output file, even if the read-only attribute is set on the file.</span></span>

<span data-ttu-id="efb93-152">預設 `Export-Alias` 會覆寫檔案而不發出警告，除非已設定唯讀或隱藏屬性，或在命令中使用 **NoClobber** 參數。</span><span class="sxs-lookup"><span data-stu-id="efb93-152">By default, `Export-Alias` overwrites files without warning, unless the read-only or hidden attribute is set or the **NoClobber** parameter is used in the command.</span></span>
<span data-ttu-id="efb93-153">當命令中同時使用 **NoClobber** 參數時，它會優先于 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="efb93-153">The **NoClobber** parameter takes precedence over the **Force** parameter when both are used in a command.</span></span>

<span data-ttu-id="efb93-154">**Force** 參數不能強制 `Export-Alias` 以 hidden 屬性覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="efb93-154">The **Force** parameter cannot force `Export-Alias` to overwrite files with the hidden attribute.</span></span>

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

### <span data-ttu-id="efb93-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="efb93-155">-LiteralPath</span></span>

<span data-ttu-id="efb93-156">指定輸出檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="efb93-156">Specifies the path to the output file.</span></span>
<span data-ttu-id="efb93-157">與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="efb93-157">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="efb93-158">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="efb93-158">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="efb93-159">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="efb93-159">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="efb93-160">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="efb93-160">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="efb93-161">-Name</span><span class="sxs-lookup"><span data-stu-id="efb93-161">-Name</span></span>

<span data-ttu-id="efb93-162">將名稱指定為要匯出之別名的陣列。</span><span class="sxs-lookup"><span data-stu-id="efb93-162">Specifies the names as an array of the aliases to export.</span></span>
<span data-ttu-id="efb93-163">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="efb93-163">Wildcards are permitted.</span></span>

<span data-ttu-id="efb93-164">根據預設，會 `Export-Alias` 匯出會話或範圍中的所有別名。</span><span class="sxs-lookup"><span data-stu-id="efb93-164">By default, `Export-Alias` exports all aliases in the session or scope.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="efb93-165">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="efb93-165">-NoClobber</span></span>

<span data-ttu-id="efb93-166">指出此 Cmdlet 會防止 `Export-Alias` 覆寫任何檔案，即使在命令中使用 **Force** 參數也是如此。</span><span class="sxs-lookup"><span data-stu-id="efb93-166">Indicates that this cmdlet prevents `Export-Alias` from overwriting any files, even if the **Force** parameter is used in the command.</span></span>

<span data-ttu-id="efb93-167">如果省略 **NoClobber** 參數， `Export-Alias` 將會覆寫現有的檔案而不發出警告，除非已在檔案上設定唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="efb93-167">If the **NoClobber** parameter is omitted, `Export-Alias` will overwrite an existing file without warning, unless the read-only attribute is set on the file.</span></span>
<span data-ttu-id="efb93-168">*NoClobber* 優先于 **Force** 參數，它允許 `Export-Alias` 以唯讀屬性覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="efb93-168">*NoClobber* takes precedence over the **Force** parameter, which permits `Export-Alias` to overwrite a file with the read-only attribute.</span></span>

<span data-ttu-id="efb93-169">*NoClobber* 不會防止 **Append** 參數將內容加入現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="efb93-169">*NoClobber* does not prevent the **Append** parameter from adding content to an existing file.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efb93-170">-PassThru</span><span class="sxs-lookup"><span data-stu-id="efb93-170">-PassThru</span></span>

<span data-ttu-id="efb93-171">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="efb93-171">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="efb93-172">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="efb93-172">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="efb93-173">-Path</span><span class="sxs-lookup"><span data-stu-id="efb93-173">-Path</span></span>

<span data-ttu-id="efb93-174">指定輸出檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="efb93-174">Specifies the path to the output file.</span></span>
<span data-ttu-id="efb93-175">允許使用萬用字元，但是產生的路徑值必須解析成單一檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="efb93-175">Wildcards are permitted, but the resulting path value must resolve to a single file name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="efb93-176">-Scope</span><span class="sxs-lookup"><span data-stu-id="efb93-176">-Scope</span></span>

<span data-ttu-id="efb93-177">指定要匯出別名的範圍。</span><span class="sxs-lookup"><span data-stu-id="efb93-177">Specifies the scope from which the aliases should be exported.</span></span>
<span data-ttu-id="efb93-178">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="efb93-178">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="efb93-179">全球</span><span class="sxs-lookup"><span data-stu-id="efb93-179">Global</span></span>
- <span data-ttu-id="efb93-180">本機</span><span class="sxs-lookup"><span data-stu-id="efb93-180">Local</span></span>
- <span data-ttu-id="efb93-181">指令碼</span><span class="sxs-lookup"><span data-stu-id="efb93-181">Script</span></span>
- <span data-ttu-id="efb93-182">相對於目前範圍的數位 (0 至範圍數目，0為目前範圍，1為其父系) </span><span class="sxs-lookup"><span data-stu-id="efb93-182">A number relative to the current scope (0 through the number of scopes where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="efb93-183">預設值為 Local。</span><span class="sxs-lookup"><span data-stu-id="efb93-183">The default value is Local.</span></span>
<span data-ttu-id="efb93-184">如需詳細資訊，請參閱 about_Scopes。</span><span class="sxs-lookup"><span data-stu-id="efb93-184">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="efb93-185">-Confirm</span><span class="sxs-lookup"><span data-stu-id="efb93-185">-Confirm</span></span>

<span data-ttu-id="efb93-186">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="efb93-186">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="efb93-187">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="efb93-187">-WhatIf</span></span>

<span data-ttu-id="efb93-188">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="efb93-188">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="efb93-189">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="efb93-189">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="efb93-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="efb93-190">CommonParameters</span></span>

<span data-ttu-id="efb93-191">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="efb93-191">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="efb93-192">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="efb93-192">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="efb93-193">輸入</span><span class="sxs-lookup"><span data-stu-id="efb93-193">INPUTS</span></span>

### <span data-ttu-id="efb93-194">無。</span><span class="sxs-lookup"><span data-stu-id="efb93-194">None.</span></span>

<span data-ttu-id="efb93-195">您無法使用管線將物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="efb93-195">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="efb93-196">輸出</span><span class="sxs-lookup"><span data-stu-id="efb93-196">OUTPUTS</span></span>

### <span data-ttu-id="efb93-197">無或 System.Management.Automation.AliasInfo</span><span class="sxs-lookup"><span data-stu-id="efb93-197">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="efb93-198">當您使用 **Passthru** 參數時，會傳回 `Export-Alias` 代表別名的 **system.management.automation.aliasinfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="efb93-198">When you use the **Passthru** parameter, `Export-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="efb93-199">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="efb93-199">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="efb93-200">注意</span><span class="sxs-lookup"><span data-stu-id="efb93-200">NOTES</span></span>

* <span data-ttu-id="efb93-201">您只能匯出別名 (Export-Aliases) 至檔案。</span><span class="sxs-lookup"><span data-stu-id="efb93-201">You can only Export-Aliases to a file.</span></span>

## <span data-ttu-id="efb93-202">相關連結</span><span class="sxs-lookup"><span data-stu-id="efb93-202">RELATED LINKS</span></span>

[<span data-ttu-id="efb93-203">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="efb93-203">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="efb93-204">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="efb93-204">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="efb93-205">New-Alias</span><span class="sxs-lookup"><span data-stu-id="efb93-205">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="efb93-206">Set-Alias</span><span class="sxs-lookup"><span data-stu-id="efb93-206">Set-Alias</span></span>](Set-Alias.md)
