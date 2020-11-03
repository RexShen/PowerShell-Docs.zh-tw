---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Item
ms.openlocfilehash: 6aac74b9b084996377b97997ab78972cb28b0959
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203979"
---
# <span data-ttu-id="4003a-103">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="4003a-103">Invoke-Item</span></span>

## <span data-ttu-id="4003a-104">概要</span><span class="sxs-lookup"><span data-stu-id="4003a-104">SYNOPSIS</span></span>
<span data-ttu-id="4003a-105">在指定項目上執行預設動作。</span><span class="sxs-lookup"><span data-stu-id="4003a-105">Performs the default action on the specified item.</span></span>

## <span data-ttu-id="4003a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4003a-106">SYNTAX</span></span>

### <span data-ttu-id="4003a-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="4003a-107">Path (Default)</span></span>

```
Invoke-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="4003a-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4003a-108">LiteralPath</span></span>

```
Invoke-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="4003a-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4003a-109">DESCRIPTION</span></span>

<span data-ttu-id="4003a-110">此 `Invoke-Item` Cmdlet 會在指定的專案上執行預設動作。</span><span class="sxs-lookup"><span data-stu-id="4003a-110">The `Invoke-Item` cmdlet performs the default action on the specified item.</span></span>
<span data-ttu-id="4003a-111">例如，它會執行可執行檔或在與文件檔案類型相關聯的應用程式中開啟文件檔案。</span><span class="sxs-lookup"><span data-stu-id="4003a-111">For example, it runs an executable file or opens a document file in the application associated with the document file type.</span></span>
<span data-ttu-id="4003a-112">預設動作取決於專案的類型，而且是由提供資料存取權的 PowerShell 提供者所決定。</span><span class="sxs-lookup"><span data-stu-id="4003a-112">The default action depends on the type of item and is determined by the PowerShell provider that provides access to the data.</span></span>

## <span data-ttu-id="4003a-113">範例</span><span class="sxs-lookup"><span data-stu-id="4003a-113">EXAMPLES</span></span>

### <span data-ttu-id="4003a-114">範例1：開啟檔案</span><span class="sxs-lookup"><span data-stu-id="4003a-114">Example 1: Open a file</span></span>

<span data-ttu-id="4003a-115">此命令會在 Microsoft Office Word 中開啟 "aliasApr04.doc" 檔案。</span><span class="sxs-lookup"><span data-stu-id="4003a-115">This command opens the file "aliasApr04.doc" in Microsoft Office Word.</span></span>
<span data-ttu-id="4003a-116">在此情況下，在 Word 中開啟是 ".doc" 檔案的預設動作。</span><span class="sxs-lookup"><span data-stu-id="4003a-116">In this case, opening in Word is the default action for ".doc" files.</span></span>

```powershell
Invoke-Item "C:\Test\aliasApr04.doc"
```

### <span data-ttu-id="4003a-117">範例2：開啟特定類型的所有檔案</span><span class="sxs-lookup"><span data-stu-id="4003a-117">Example 2: Open all files of a specific type</span></span>

<span data-ttu-id="4003a-118">此命令會開啟 [C:\documents and 和 Settings\lister\my documents Documents] 資料夾中的所有 Microsoft Office Excel 試算表。</span><span class="sxs-lookup"><span data-stu-id="4003a-118">This command opens all of the Microsoft Office Excel spreadsheets in the "C:\Documents and Settings\Lister\My Documents" folder.</span></span>
<span data-ttu-id="4003a-119">每一個試算表都會在一個新的 Excel 執行個體中開啟。</span><span class="sxs-lookup"><span data-stu-id="4003a-119">Each spreadsheet is opened in a new instance of Excel.</span></span>
<span data-ttu-id="4003a-120">在此情況下，在 Excel 中開啟是 ".xls" 檔案的預設動作。</span><span class="sxs-lookup"><span data-stu-id="4003a-120">In this case, opening in Excel is the default action for ".xls" files.</span></span>

```powershell
Invoke-Item "C:\Documents and Settings\Lister\My Documents\*.xls"
```

## <span data-ttu-id="4003a-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4003a-121">PARAMETERS</span></span>

### <span data-ttu-id="4003a-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="4003a-122">-Credential</span></span>

<span data-ttu-id="4003a-123">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="4003a-123">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="4003a-124">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="4003a-124">The default is the current user.</span></span>

<span data-ttu-id="4003a-125">輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="4003a-125">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="4003a-126">若您輸入使用者名稱時，會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="4003a-126">If you type a user name, you are prompted for a password.</span></span>

> [!WARNING]
> <span data-ttu-id="4003a-127">與 Windows PowerShell 一起安裝的任何提供者皆不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="4003a-127">This parameter is not supported by any providers installed with Windows PowerShell.</span></span>

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

### <span data-ttu-id="4003a-128">-Exclude</span><span class="sxs-lookup"><span data-stu-id="4003a-128">-Exclude</span></span>

<span data-ttu-id="4003a-129">以字串陣列指定此 Cmdlet 在作業中排除的項目。</span><span class="sxs-lookup"><span data-stu-id="4003a-129">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="4003a-130">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="4003a-130">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="4003a-131">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="4003a-131">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="4003a-132">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4003a-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="4003a-133">-Filter</span><span class="sxs-lookup"><span data-stu-id="4003a-133">-Filter</span></span>

<span data-ttu-id="4003a-134">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="4003a-134">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="4003a-135">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="4003a-135">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="4003a-136">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="4003a-136">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="4003a-137">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="4003a-137">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="4003a-138">-Include</span><span class="sxs-lookup"><span data-stu-id="4003a-138">-Include</span></span>

<span data-ttu-id="4003a-139">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="4003a-139">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="4003a-140">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="4003a-140">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="4003a-141">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="4003a-141">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="4003a-142">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4003a-142">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4003a-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4003a-143">-LiteralPath</span></span>

<span data-ttu-id="4003a-144">指定項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="4003a-144">Specifies a path to the item.</span></span>
<span data-ttu-id="4003a-145">與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="4003a-145">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="4003a-146">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4003a-146">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="4003a-147">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="4003a-147">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="4003a-148">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="4003a-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4003a-149">-Path</span><span class="sxs-lookup"><span data-stu-id="4003a-149">-Path</span></span>

<span data-ttu-id="4003a-150">指定選取項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="4003a-150">Specifies the path to the selected item.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4003a-151">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="4003a-151">-UseTransaction</span></span>

<span data-ttu-id="4003a-152">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="4003a-152">Includes the command in the active transaction.</span></span>
<span data-ttu-id="4003a-153">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="4003a-153">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="4003a-154">如需詳細資訊，請參閱 about_transactions。</span><span class="sxs-lookup"><span data-stu-id="4003a-154">For more information, see about_transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4003a-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4003a-155">-Confirm</span></span>
<span data-ttu-id="4003a-156">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="4003a-156">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4003a-157">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4003a-157">-WhatIf</span></span>

<span data-ttu-id="4003a-158">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="4003a-158">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4003a-159">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="4003a-159">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4003a-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4003a-160">CommonParameters</span></span>

<span data-ttu-id="4003a-161">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="4003a-161">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="4003a-162">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="4003a-162">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4003a-163">輸入</span><span class="sxs-lookup"><span data-stu-id="4003a-163">INPUTS</span></span>

### <span data-ttu-id="4003a-164">System.String</span><span class="sxs-lookup"><span data-stu-id="4003a-164">System.String</span></span>

<span data-ttu-id="4003a-165">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4003a-165">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="4003a-166">輸出</span><span class="sxs-lookup"><span data-stu-id="4003a-166">OUTPUTS</span></span>

### <span data-ttu-id="4003a-167">無</span><span class="sxs-lookup"><span data-stu-id="4003a-167">None</span></span>

<span data-ttu-id="4003a-168">命令不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="4003a-168">The command does not generate any output.</span></span>
<span data-ttu-id="4003a-169">但它叫用的項目可能會產生輸出。</span><span class="sxs-lookup"><span data-stu-id="4003a-169">However, output might be generated by the item that it invokes.</span></span>

## <span data-ttu-id="4003a-170">注意</span><span class="sxs-lookup"><span data-stu-id="4003a-170">NOTES</span></span>

<span data-ttu-id="4003a-171">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="4003a-171">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="4003a-172">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="4003a-172">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="4003a-173">如需詳細資訊，請參閱 about_Providers。</span><span class="sxs-lookup"><span data-stu-id="4003a-173">For more information, see about_Providers.</span></span>

## <span data-ttu-id="4003a-174">相關連結</span><span class="sxs-lookup"><span data-stu-id="4003a-174">RELATED LINKS</span></span>

[<span data-ttu-id="4003a-175">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="4003a-175">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="4003a-176">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="4003a-176">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="4003a-177">Get-Item</span><span class="sxs-lookup"><span data-stu-id="4003a-177">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="4003a-178">Move-Item</span><span class="sxs-lookup"><span data-stu-id="4003a-178">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="4003a-179">New-Item</span><span class="sxs-lookup"><span data-stu-id="4003a-179">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="4003a-180">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="4003a-180">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="4003a-181">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="4003a-181">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="4003a-182">Set-Item</span><span class="sxs-lookup"><span data-stu-id="4003a-182">Set-Item</span></span>](Set-Item.md)
