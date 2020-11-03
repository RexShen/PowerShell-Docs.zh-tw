---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: 5d4fafe4dbb92f40e31b0af963256fdce50b5a8b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203784"
---
# <span data-ttu-id="2bd4e-103">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="2bd4e-103">Invoke-Item</span></span>

## <span data-ttu-id="2bd4e-104">概要</span><span class="sxs-lookup"><span data-stu-id="2bd4e-104">SYNOPSIS</span></span>
<span data-ttu-id="2bd4e-105">在指定項目上執行預設動作。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-105">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="2bd4e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2bd4e-106">SYNTAX</span></span>

### <span data-ttu-id="2bd4e-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="2bd4e-107">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2bd4e-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2bd4e-108">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2bd4e-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2bd4e-109">DESCRIPTION</span></span>

<span data-ttu-id="2bd4e-110">此 `Invoke-Item` Cmdlet 會在指定的專案上執行預設動作。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-110">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="2bd4e-111">例如，它會執行可執行檔或在與文件檔案類型相關聯的應用程式中開啟文件檔案。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-111">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="2bd4e-112">預設動作取決於專案的類型，而且是由提供資料存取權的 PowerShell 提供者所決定。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-112">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="2bd4e-113">範例</span><span class="sxs-lookup"><span data-stu-id="2bd4e-113">EXAMPLES</span></span>

### <span data-ttu-id="2bd4e-114">範例1：開啟檔案</span><span class="sxs-lookup"><span data-stu-id="2bd4e-114">Example 1: Open a file</span></span>

<span data-ttu-id="2bd4e-115">此命令會在 Microsoft Office Word 中開啟 "aliasApr04.doc" 檔案。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-115">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="2bd4e-116">在此情況下，在 Word 中開啟是 ".doc" 檔案的預設動作。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-116">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="2bd4e-117">範例2：開啟特定類型的所有檔案</span><span class="sxs-lookup"><span data-stu-id="2bd4e-117">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="2bd4e-118">此命令會開啟資料夾中的所有 Microsoft Office Excel 試算表 `C:\Documents and
Settings\Lister\My Documents` 。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-118">This command opens all of the Microsoft Office Excel spreadsheets in the `C:\Documents and
Settings\Lister\My Documents` folder.</span></span> <span data-ttu-id="2bd4e-119">每一個試算表都會在一個新的 Excel 執行個體中開啟。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-119">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="2bd4e-120">在此情況下，在 Excel 中開啟是檔案的預設動作 `.xls` 。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-120">In this case, opening in Excel is the default action for `.xls` files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="2bd4e-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2bd4e-121">PARAMETERS</span></span>

### <span data-ttu-id="2bd4e-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="2bd4e-122">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="2bd4e-123">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-123">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="2bd4e-124">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-124">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2bd4e-125">-Exclude</span><span class="sxs-lookup"><span data-stu-id="2bd4e-125">-Exclude</span></span>

<span data-ttu-id="2bd4e-126">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-126">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="2bd4e-127">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-127">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2bd4e-128">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-128">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="2bd4e-129">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-129">Wildcard characters are permitted.</span></span> <span data-ttu-id="2bd4e-130">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-130">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2bd4e-131">-Filter</span><span class="sxs-lookup"><span data-stu-id="2bd4e-131">-Filter</span></span>

<span data-ttu-id="2bd4e-132">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-132">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="2bd4e-133">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-133">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="2bd4e-134">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-134">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="2bd4e-135">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-135">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2bd4e-136">-Include</span><span class="sxs-lookup"><span data-stu-id="2bd4e-136">-Include</span></span>

<span data-ttu-id="2bd4e-137">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-137">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="2bd4e-138">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2bd4e-139">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-139">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="2bd4e-140">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="2bd4e-141">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-141">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2bd4e-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2bd4e-142">-LiteralPath</span></span>

<span data-ttu-id="2bd4e-143">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="2bd4e-144">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="2bd4e-145">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="2bd4e-146">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2bd4e-147">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="2bd4e-148">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2bd4e-149">-Path</span><span class="sxs-lookup"><span data-stu-id="2bd4e-149">-Path</span></span>

<span data-ttu-id="2bd4e-150">指定選取項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-150">Specifies the path to the selected item.</span></span>
<span data-ttu-id="2bd4e-151">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-151">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="2bd4e-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2bd4e-152">-Confirm</span></span>

<span data-ttu-id="2bd4e-153">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2bd4e-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2bd4e-154">-WhatIf</span></span>

<span data-ttu-id="2bd4e-155">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2bd4e-156">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2bd4e-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2bd4e-157">CommonParameters</span></span>

<span data-ttu-id="2bd4e-158">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-158">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="2bd4e-159">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-159">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2bd4e-160">輸入</span><span class="sxs-lookup"><span data-stu-id="2bd4e-160">INPUTS</span></span>

### <span data-ttu-id="2bd4e-161">System.String</span><span class="sxs-lookup"><span data-stu-id="2bd4e-161">System.String</span></span>

<span data-ttu-id="2bd4e-162">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-162">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="2bd4e-163">輸出</span><span class="sxs-lookup"><span data-stu-id="2bd4e-163">OUTPUTS</span></span>

### <span data-ttu-id="2bd4e-164">無</span><span class="sxs-lookup"><span data-stu-id="2bd4e-164">None</span></span>

<span data-ttu-id="2bd4e-165">命令不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-165">The command does not generate any output.</span></span>
<span data-ttu-id="2bd4e-166">但它叫用的項目可能會產生輸出。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-166">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="2bd4e-167">注意</span><span class="sxs-lookup"><span data-stu-id="2bd4e-167">NOTES</span></span>

<span data-ttu-id="2bd4e-168">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-168">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="2bd4e-169">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-169">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="2bd4e-170">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="2bd4e-170">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="2bd4e-171">相關連結</span><span class="sxs-lookup"><span data-stu-id="2bd4e-171">RELATED LINKS</span></span>

[<span data-ttu-id="2bd4e-172">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="2bd4e-172">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="2bd4e-173">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="2bd4e-173">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="2bd4e-174">Get-Item</span><span class="sxs-lookup"><span data-stu-id="2bd4e-174">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="2bd4e-175">Move-Item</span><span class="sxs-lookup"><span data-stu-id="2bd4e-175">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="2bd4e-176">New-Item</span><span class="sxs-lookup"><span data-stu-id="2bd4e-176">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="2bd4e-177">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="2bd4e-177">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="2bd4e-178">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="2bd4e-178">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="2bd4e-179">Set-Item</span><span class="sxs-lookup"><span data-stu-id="2bd4e-179">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="2bd4e-180">about_Providers</span><span class="sxs-lookup"><span data-stu-id="2bd4e-180">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
