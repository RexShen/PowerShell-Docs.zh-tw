---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: d89d80b296d8800d65c5acfae37434e9b3f3bce9
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201808"
---
# <span data-ttu-id="45139-103">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="45139-103">Export-FormatData</span></span>

## <span data-ttu-id="45139-104">概要</span><span class="sxs-lookup"><span data-stu-id="45139-104">SYNOPSIS</span></span>
<span data-ttu-id="45139-105">在格式化檔案中儲存來自目前工作階段的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="45139-105">Saves formatting data from the current session in a formatting file.</span></span>

## <span data-ttu-id="45139-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="45139-106">SYNTAX</span></span>

### <span data-ttu-id="45139-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="45139-107">ByPath (Default)</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### <span data-ttu-id="45139-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="45139-108">ByLiteralPath</span></span>

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## <span data-ttu-id="45139-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="45139-109">DESCRIPTION</span></span>

<span data-ttu-id="45139-110">此 `Export-FormatData` Cmdlet 會從目前會話中的格式化物件，建立 PowerShell 格式設定檔案 ( # B0 xml) 。</span><span class="sxs-lookup"><span data-stu-id="45139-110">The `Export-FormatData` cmdlet creates PowerShell formatting files (format.ps1xml) from the formatting objects in the current session.</span></span> <span data-ttu-id="45139-111">它會採用傳回的 **ExtendedTypeDefinition** 物件， `Get-FormatData` 並將它們儲存在 XML 格式的檔案中。</span><span class="sxs-lookup"><span data-stu-id="45139-111">It takes the **ExtendedTypeDefinition** objects that `Get-FormatData` returns and saves them in a file in XML format.</span></span>

<span data-ttu-id="45139-112">PowerShell 會使用格式化檔案中的資料 ( # B0 xml) 來產生會話中 Microsoft .NET Framework 物件的預設顯示。</span><span class="sxs-lookup"><span data-stu-id="45139-112">PowerShell uses the data in formatting files (format.ps1xml) to generate the default display of Microsoft .NET Framework objects in the session.</span></span> <span data-ttu-id="45139-113">您可以檢視及編輯格式化檔案，然後使用 Update-FormatData Cmdlet 將格式化資料新增至工作階段。</span><span class="sxs-lookup"><span data-stu-id="45139-113">You can view and edit the formatting files and use the Update-FormatData cmdlet to add the formatting data to a session.</span></span>

<span data-ttu-id="45139-114">如需有關在 PowerShell 中格式化檔案的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="45139-114">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="45139-115">範例</span><span class="sxs-lookup"><span data-stu-id="45139-115">EXAMPLES</span></span>

### <span data-ttu-id="45139-116">範例1：匯出會話格式資料</span><span class="sxs-lookup"><span data-stu-id="45139-116">Example 1: Export session format data</span></span>

```powershell
Get-FormatData -TypeName "*" -PowerShellVersion 5.1 | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="45139-117">此命令會將工作階段中的所有格式資料匯出到 AllFormat.ps1xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="45139-117">This command exports all of the format data in the session to the AllFormat.ps1xml file.</span></span>

<span data-ttu-id="45139-118">此命令會使用 `Get-FormatData` Cmdlet 來取得會話中的格式資料。</span><span class="sxs-lookup"><span data-stu-id="45139-118">The command uses the `Get-FormatData` cmdlet to get the format data in the session.</span></span> <span data-ttu-id="45139-119">`*` **TypeName** 參數的所有) 值 (會指示 Cmdlet 取得會話中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="45139-119">A value of `*` (all) for the **TypeName** parameter directs the cmdlet to get all of the data in the session.</span></span>

<span data-ttu-id="45139-120">此命令會使用管線運算子 (`|`) 將格式資料從 `Get-FormatData` 命令傳送至 `Export-FormatData` Cmdlet，以將格式資料匯出至 AllFormat.ps1 的檔案。</span><span class="sxs-lookup"><span data-stu-id="45139-120">The command uses a pipeline operator (`|`) to send the format data from the `Get-FormatData` command to the `Export-FormatData` cmdlet, which exports the format data to the AllFormat.ps1 file.</span></span>

<span data-ttu-id="45139-121">此 `Export-FormatData` 命令會使用 **IncludeScriptBlock** 參數，將腳本區塊包含在檔案中的格式資料。</span><span class="sxs-lookup"><span data-stu-id="45139-121">The `Export-FormatData` command uses the **IncludeScriptBlock** parameter to include script blocks in the format data in the file.</span></span>

### <span data-ttu-id="45139-122">範例2：匯出類型的格式資料</span><span class="sxs-lookup"><span data-stu-id="45139-122">Example 2: Export format data for a type</span></span>

```powershell
$F = Get-FormatData -TypeName "helpinfoshort" -PowerShellVersion 5.1
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

<span data-ttu-id="45139-123">這些命令會將 **HelpInfoShort** 類型的格式資料匯出到 Help.format.ps1的 xml 檔。</span><span class="sxs-lookup"><span data-stu-id="45139-123">These commands export the format data for the **HelpInfoShort** type to the Help.format.ps1xml file.</span></span>

<span data-ttu-id="45139-124">第一個命令會使用 `Get-FormatData` Cmdlet 來取得 **HelpInfoShort** 類型的格式資料，並將它儲存在 `$F` 變數中。</span><span class="sxs-lookup"><span data-stu-id="45139-124">The first command uses the `Get-FormatData` cmdlet to get the format data for the **HelpInfoShort** type, and it saves it in the `$F` variable.</span></span>

<span data-ttu-id="45139-125">第二個命令會使用 Cmdlet 的 **InputObject** 參數 `Export-FormatData` 來輸入變數中儲存的格式資料 `$F` 。</span><span class="sxs-lookup"><span data-stu-id="45139-125">The second command uses the **InputObject** parameter of the `Export-FormatData` cmdlet to enter the format data saved in the `$F` variable.</span></span> <span data-ttu-id="45139-126">它也會使用 **IncludeScriptBlock** 參數將腳本區塊包含在輸出中。</span><span class="sxs-lookup"><span data-stu-id="45139-126">It also uses the **IncludeScriptBlock** parameter to include script blocks in the output.</span></span>

### <span data-ttu-id="45139-127">範例3：不使用腳本區塊匯出格式資料</span><span class="sxs-lookup"><span data-stu-id="45139-127">Example 3: Export format data without a script block</span></span>

```powershell
Get-FormatData -TypeName "System.Diagnostics.Process" -PowerShellVersion 5.1 | Export-FormatData -Path process.format.ps1xml
Update-FormatData -PrependPath ".\process.format.ps1xml"
Get-Process p*
```

```Output
Handles  NPM(K)  PM(K)  WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------  -----  ----- -----   ------    -- -----------
323                                       5600 powershell
336                                       3900 powershell_ise
138                                       4076 PresentationFontCache
```

<span data-ttu-id="45139-128">此範例顯示從命令省略 **IncludeScriptBlock** 參數的效果 `Export-FormatData` 。</span><span class="sxs-lookup"><span data-stu-id="45139-128">This example shows the effect of omitting the **IncludeScriptBlock** parameter from an `Export-FormatData` command.</span></span>

<span data-ttu-id="45139-129">第一個命令會使用 `Get-FormatData` Cmdlet 來取得 Get-Process Cmdlet **所傳回** 之 system.string 物件的格式資料。</span><span class="sxs-lookup"><span data-stu-id="45139-129">The first command uses the `Get-FormatData` cmdlet to get the format data for the **System.Diagnostics.Process** object that the Get-Process cmdlet returns.</span></span> <span data-ttu-id="45139-130">此命令會使用管線運算子 (`|`) 將格式化資料傳送至 `Export-FormatData` Cmdlet，此 Cmdlet 會將資料匯出至目前目錄中 Process.format.ps1的 xml 檔。</span><span class="sxs-lookup"><span data-stu-id="45139-130">The command uses a pipeline operator (`|`) to send the formatting data to the `Export-FormatData` cmdlet, which exports it to the Process.format.ps1xml file in the current directory.</span></span>

<span data-ttu-id="45139-131">在此情況下，此 `Export-FormatData` 命令不會使用 **IncludeScriptBlock** 參數。</span><span class="sxs-lookup"><span data-stu-id="45139-131">In this case, the `Export-FormatData` command does not use the **IncludeScriptBlock** parameter.</span></span>

<span data-ttu-id="45139-132">第二個命令會使用 `Update-FormatData` Cmdlet 將 Process.format.ps1xml 檔案新增至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="45139-132">The second command uses the `Update-FormatData` cmdlet to add the Process.format.ps1xml file to the current session.</span></span> <span data-ttu-id="45139-133">此命令會使用 **PrependPath** 參數，以確保在處理常式物件的標準格式化資料之前，可以找到 Process.format.ps1xml 檔案中處理常式物件的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="45139-133">The command uses the **PrependPath** parameter to ensure that the formatting data for process objects in the Process.format.ps1xml file is found before the standard formatting data for process objects.</span></span>

<span data-ttu-id="45139-134">第三個命令會顯示此變更的效果。</span><span class="sxs-lookup"><span data-stu-id="45139-134">The third command shows the effects of this change.</span></span> <span data-ttu-id="45139-135">此命令會使用 `Get-Process` Cmdlet 來取得名稱以 P 開頭的處理常式。輸出顯示顯示中遺失使用腳本區塊計算的屬性值。</span><span class="sxs-lookup"><span data-stu-id="45139-135">The command uses the `Get-Process` cmdlet to get processes that have names that begin with P. The output shows that property values that are calculated by using script blocks are missing from the display.</span></span>

## <span data-ttu-id="45139-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="45139-136">PARAMETERS</span></span>

### <span data-ttu-id="45139-137">-Force</span><span class="sxs-lookup"><span data-stu-id="45139-137">-Force</span></span>

<span data-ttu-id="45139-138">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="45139-138">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="45139-139">-IncludeScriptBlock</span><span class="sxs-lookup"><span data-stu-id="45139-139">-IncludeScriptBlock</span></span>

<span data-ttu-id="45139-140">指出是否匯出格式資料中的腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="45139-140">Indicates whether script blocks in the format data are exported.</span></span>

<span data-ttu-id="45139-141">因為指令碼區塊包含程式碼，可能被用於惡意用途，所以預設不會將它們匯出。</span><span class="sxs-lookup"><span data-stu-id="45139-141">Because script blocks contain code and can be used maliciously, they are not exported by default.</span></span>

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

### <span data-ttu-id="45139-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="45139-142">-InputObject</span></span>

<span data-ttu-id="45139-143">指定要匯出的格式資料物件。</span><span class="sxs-lookup"><span data-stu-id="45139-143">Specifies the format data objects to be exported.</span></span> <span data-ttu-id="45139-144">輸入包含物件的變數，或輸入可取得物件的命令，例如 `Get-FormatData` 命令。</span><span class="sxs-lookup"><span data-stu-id="45139-144">Enter a variable that contains the objects or a command that gets the objects, such as a `Get-FormatData` command.</span></span> <span data-ttu-id="45139-145">您也可以透過管線將物件傳送 `Get-FormatData` 至 `Export-FormatData` 。</span><span class="sxs-lookup"><span data-stu-id="45139-145">You can also pipe the objects from `Get-FormatData` to `Export-FormatData`.</span></span>

```yaml
Type: System.Management.Automation.ExtendedTypeDefinition[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="45139-146">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="45139-146">-LiteralPath</span></span>

<span data-ttu-id="45139-147">指定輸出檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="45139-147">Specifies a location for the output file.</span></span> <span data-ttu-id="45139-148">與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="45139-148">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="45139-149">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="45139-149">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="45139-150">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="45139-150">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="45139-151">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="45139-151">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45139-152">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="45139-152">-NoClobber</span></span>

<span data-ttu-id="45139-153">指出此 Cmdlet 不會覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="45139-153">Indicates that the cmdlet does not overwrite existing files.</span></span> <span data-ttu-id="45139-154">依預設， `Export-FormatData` 會覆寫檔案而不發出警告，除非檔案具有唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="45139-154">By default, `Export-FormatData` overwrites files without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="45139-155">若要指示 `Export-FormatData` 覆寫唯讀檔案，請使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="45139-155">To direct `Export-FormatData` to overwrite read-only files, use the **Force** parameter.</span></span>

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

### <span data-ttu-id="45139-156">-Path</span><span class="sxs-lookup"><span data-stu-id="45139-156">-Path</span></span>

<span data-ttu-id="45139-157">指定輸出檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="45139-157">Specifies a location for the output file.</span></span>
<span data-ttu-id="45139-158">輸入路徑 (選擇性) 與副檔名為 format.ps1xml 的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="45139-158">Enter a path (optional) and file name with a format.ps1xml file name extension.</span></span>
<span data-ttu-id="45139-159">如果您省略路徑，會 `Export-FormatData` 在目前的目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="45139-159">If you omit the path, `Export-FormatData` creates the file in the current directory.</span></span>

<span data-ttu-id="45139-160">如果您使用 .ps1xml 以外的副檔名，此 `Update-FormatData` Cmdlet 將無法辨識該檔案。</span><span class="sxs-lookup"><span data-stu-id="45139-160">If you use a file name extension other than .ps1xml, the `Update-FormatData` cmdlet will not recognize the file.</span></span>

<span data-ttu-id="45139-161">如果您指定現有的檔案，則 `Export-FormatData` 會覆寫檔案而不發出警告，除非檔案具有唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="45139-161">If you specify an existing file, `Export-FormatData` overwrites the file without warning, unless the file has the read-only attribute.</span></span> <span data-ttu-id="45139-162">若要覆寫唯讀檔案，請使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="45139-162">To overwrite a read-only file, use the **Force** parameter.</span></span> <span data-ttu-id="45139-163">若要防止覆寫檔案，請使用 **NoClobber** 參數。</span><span class="sxs-lookup"><span data-stu-id="45139-163">To prevent files from being overwritten, use the **NoClobber** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: FilePath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="45139-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="45139-164">CommonParameters</span></span>

<span data-ttu-id="45139-165">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="45139-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="45139-166">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="45139-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="45139-167">輸入</span><span class="sxs-lookup"><span data-stu-id="45139-167">INPUTS</span></span>

### <span data-ttu-id="45139-168">System.Management.Automation.ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="45139-168">System.Management.Automation.ExtendedTypeDefinition</span></span>

<span data-ttu-id="45139-169">您可以透過管線將 **ExtendedTypeDefinition** 物件傳送 `Get-FormatData` 至 `Export-FormatData` 。</span><span class="sxs-lookup"><span data-stu-id="45139-169">You can pipe **ExtendedTypeDefinition** objects from `Get-FormatData` to `Export-FormatData`.</span></span>

## <span data-ttu-id="45139-170">輸出</span><span class="sxs-lookup"><span data-stu-id="45139-170">OUTPUTS</span></span>

### <span data-ttu-id="45139-171">無</span><span class="sxs-lookup"><span data-stu-id="45139-171">None</span></span>

<span data-ttu-id="45139-172">`Export-FormatData` 不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="45139-172">`Export-FormatData` does not return any objects.</span></span>
<span data-ttu-id="45139-173">它會產生一個檔案，並將檔案儲存在指定路徑。</span><span class="sxs-lookup"><span data-stu-id="45139-173">It generates a file and saves it in the specified path.</span></span>

## <span data-ttu-id="45139-174">注意</span><span class="sxs-lookup"><span data-stu-id="45139-174">NOTES</span></span>

- <span data-ttu-id="45139-175">若要使用任何格式化檔案 (包括匯出的格式化檔案)，工作階段的執行原則必須允許執行指令碼和設定檔。</span><span class="sxs-lookup"><span data-stu-id="45139-175">To use any formatting file, including an exported formatting file, the execution policy for the session must allow scripts and configuration files to run.</span></span> <span data-ttu-id="45139-176">如需詳細資訊，請參閱 [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="45139-176">For more information, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="45139-177">相關連結</span><span class="sxs-lookup"><span data-stu-id="45139-177">RELATED LINKS</span></span>

[<span data-ttu-id="45139-178">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="45139-178">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="45139-179">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="45139-179">Update-FormatData</span></span>](Update-FormatData.md)
