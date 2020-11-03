---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 41a49ccd185cdc1ebf5c6f748833ee3f4218784b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203100"
---
# <span data-ttu-id="3475b-103">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="3475b-103">Update-FormatData</span></span>

## <span data-ttu-id="3475b-104">概要</span><span class="sxs-lookup"><span data-stu-id="3475b-104">SYNOPSIS</span></span>
<span data-ttu-id="3475b-105">更新目前工作階段中的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="3475b-105">Updates the formatting data in the current session.</span></span>

## <span data-ttu-id="3475b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3475b-106">SYNTAX</span></span>

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="3475b-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3475b-107">DESCRIPTION</span></span>

<span data-ttu-id="3475b-108">此 Cmdlet 會將格式化檔案 `Update-FormatData` 中的格式化資料重載至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="3475b-108">The `Update-FormatData` cmdlet reloads the formatting data from formatting files into the current session.</span></span> <span data-ttu-id="3475b-109">此 Cmdlet 可讓您更新格式化資料，而不需要重新開機 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3475b-109">This cmdlet lets you update the formatting data without restarting PowerShell.</span></span>

<span data-ttu-id="3475b-110">如果沒有參數，會 `Update-FormatData` 重載它先前載入的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="3475b-110">Without parameters, `Update-FormatData` reloads the formatting files that it loaded previously.</span></span>
<span data-ttu-id="3475b-111">您可以使用的參數， `Update-FormatData` 將新的格式化檔案新增到會話。</span><span class="sxs-lookup"><span data-stu-id="3475b-111">You can use the parameters of `Update-FormatData` to add new formatting files to the session.</span></span>

<span data-ttu-id="3475b-112">格式化檔案是具有副檔名的 XML 格式文字檔 `format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="3475b-112">Formatting files are text files in XML format with the `format.ps1xml` file name extension.</span></span> <span data-ttu-id="3475b-113">檔案中的格式化資料會定義工作階段中 Microsoft .NET Framework 物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="3475b-113">The formatting data in the files defines the display of Microsoft .NET Framework objects in the session.</span></span>

<span data-ttu-id="3475b-114">當 Windows PowerShell 啟動時，會從 PowerShell 安裝目錄中的格式化檔案載入格式資料， (`$pshome`) 至會話。</span><span class="sxs-lookup"><span data-stu-id="3475b-114">When Windows PowerShell starts, it loads the format data from the formatting files in the PowerShell installation directory (`$pshome`) into the session.</span></span> <span data-ttu-id="3475b-115">您可以使用 `Update-FormatData` 將格式化資料重載目前的會話，而不需要重新開機 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="3475b-115">You can use `Update-FormatData` to reload the formatting data into the current session without restarting PowerShell.</span></span> <span data-ttu-id="3475b-116">當您已新增或變更格式化檔案，但不想中斷工作階段時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="3475b-116">This is useful when you have added or changed a formatting file, but do not want to interrupt the session.</span></span>

<span data-ttu-id="3475b-117">如需有關在 PowerShell 中格式化檔案的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="3475b-117">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="3475b-118">範例</span><span class="sxs-lookup"><span data-stu-id="3475b-118">EXAMPLES</span></span>

### <span data-ttu-id="3475b-119">範例 1︰重新載入先前載入的格式化檔案</span><span class="sxs-lookup"><span data-stu-id="3475b-119">Example 1: Reload previously loaded formatting files</span></span>

```powershell
Update-FormatData
```

<span data-ttu-id="3475b-120">這個命令會重新載入它先前載入的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="3475b-120">This command reloads the formatting files that it loaded previously.</span></span>

### <span data-ttu-id="3475b-121">範例 2︰重新載入格式化檔案以及追蹤和記錄格式化檔案</span><span class="sxs-lookup"><span data-stu-id="3475b-121">Example 2: Reload formatting files and trace and log formatting files</span></span>

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

<span data-ttu-id="3475b-122">這個命令會將格式化檔案重新載入工作階段，包括 Trace.format.ps1xml 和 Log.format.ps1xml 這兩個新檔案。</span><span class="sxs-lookup"><span data-stu-id="3475b-122">This command reloads the formatting files into the session, including two new files, Trace.format.ps1xml and Log.format.ps1xml.</span></span>

<span data-ttu-id="3475b-123">由於此命令使用 **AppendPath** 參數，因此，新檔案中的格式化資料會在來自內建檔案的格式化資料之後載入。</span><span class="sxs-lookup"><span data-stu-id="3475b-123">Because the command uses the **AppendPath** parameter, the formatting data in the new files is loaded after the formatting data from the built-in files.</span></span>

<span data-ttu-id="3475b-124">因為新檔案包含內建檔案中未參考物件的格式化資料，所以會使用 **AppendPath** 參數。</span><span class="sxs-lookup"><span data-stu-id="3475b-124">The **AppendPath** parameter is used because the new files contain formatting data for objects that are not referenced in the built-in files.</span></span>

### <span data-ttu-id="3475b-125">範例 3︰編輯格式化檔案，並重新載入</span><span class="sxs-lookup"><span data-stu-id="3475b-125">Example 3: Edit a formatting file and reload it</span></span>

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

<span data-ttu-id="3475b-126">這個範例示範如何在編輯格式化檔案之後重新載入它。</span><span class="sxs-lookup"><span data-stu-id="3475b-126">This example shows how to reload a formatting file after you have edited it.</span></span>

<span data-ttu-id="3475b-127">第一個命令將 NewFiles.format.ps1xml 檔案新增至工作階段。</span><span class="sxs-lookup"><span data-stu-id="3475b-127">The first command adds the NewFiles.format.ps1xml file to the session.</span></span> <span data-ttu-id="3475b-128">它會使用 **PrependPath** 參數，因為檔案包含內建檔案中所參考物件的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="3475b-128">It uses the **PrependPath** parameter because the file contains formatting data for objects that are referenced in the built-in files.</span></span>

<span data-ttu-id="3475b-129">新增 NewFiles.format.ps1xml 檔案並在這些工作階段中測試該檔案之後，作者編輯了該檔案。</span><span class="sxs-lookup"><span data-stu-id="3475b-129">After adding the NewFiles.format.ps1xml file and testing it in these sessions, the author edits the file.</span></span>

<span data-ttu-id="3475b-130">第二個命令會使用 `Update-FormatData` Cmdlet 來重載格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="3475b-130">The second command uses the `Update-FormatData` cmdlet to reload the formatting files.</span></span> <span data-ttu-id="3475b-131">因為先前已載入 NewFiles.format.ps1xml 檔案，所以 `Update-FormatData` 會自動重載，而不使用參數。</span><span class="sxs-lookup"><span data-stu-id="3475b-131">Because the NewFiles.format.ps1xml file was previously loaded, `Update-FormatData` automatically reloads it without using parameters.</span></span>

## <span data-ttu-id="3475b-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3475b-132">PARAMETERS</span></span>

### <span data-ttu-id="3475b-133">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="3475b-133">-AppendPath</span></span>

<span data-ttu-id="3475b-134">指定此 Cmdlet 要新增至工作階段的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="3475b-134">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="3475b-135">這些檔案會在 PowerShell 載入內建的格式化檔案之後載入。</span><span class="sxs-lookup"><span data-stu-id="3475b-135">The files are loaded after PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="3475b-136">將 .NET 物件格式化時，Windows PowerShell 會使用它針對每個 .NET 類型所找到的第一個格式化定義。</span><span class="sxs-lookup"><span data-stu-id="3475b-136">When formatting .NET objects,Windows PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="3475b-137">如果您使用 **AppendPath** 參數，Windows PowerShell 會在遇到您新增的格式化資料之前，先從內建檔案中搜尋資料。</span><span class="sxs-lookup"><span data-stu-id="3475b-137">If you use the **AppendPath** parameter, Windows PowerShell searches the data from the built-in files before it encounters the formatting data that you are adding.</span></span>

<span data-ttu-id="3475b-138">使用這個參數來新增格式化 .NET 物件的檔案，而內建的格式化檔案未參考該物件。</span><span class="sxs-lookup"><span data-stu-id="3475b-138">Use this parameter to add a file that formats a .NET object that is not referenced in the built-in formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3475b-139">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="3475b-139">-PrependPath</span></span>

<span data-ttu-id="3475b-140">指定此 Cmdlet 要新增至工作階段的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="3475b-140">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="3475b-141">這些檔案會在 PowerShell 載入內建的格式化檔案之前載入。</span><span class="sxs-lookup"><span data-stu-id="3475b-141">The files are loaded before PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="3475b-142">將 .NET 物件格式化時，Windows PowerShell 會使用它針對每個 .NET 類型所找到的第一個格式化定義。</span><span class="sxs-lookup"><span data-stu-id="3475b-142">When formatting .NET objects, Windows PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="3475b-143">如果您使用 **PrependPath** 參數，Windows PowerShell 會在遇到來自內建檔案的格式化資料之前，先從您新增的檔案搜尋資料。</span><span class="sxs-lookup"><span data-stu-id="3475b-143">If you use the **PrependPath** parameter, Windows PowerShell searches the data from the files that you are adding before it encounters the formatting data from the built-in files.</span></span>

<span data-ttu-id="3475b-144">使用這個參數來新增格式化 .NET 物件的檔案，而內建的格式化檔案亦參考該物件。</span><span class="sxs-lookup"><span data-stu-id="3475b-144">Use this parameter to add a file that formats a .NET object that is also referenced in the built-in formatting files.</span></span>

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

### <span data-ttu-id="3475b-145">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3475b-145">-Confirm</span></span>

<span data-ttu-id="3475b-146">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="3475b-146">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3475b-147">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3475b-147">-WhatIf</span></span>

<span data-ttu-id="3475b-148">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="3475b-148">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="3475b-149">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="3475b-149">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3475b-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3475b-150">CommonParameters</span></span>

<span data-ttu-id="3475b-151">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3475b-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3475b-152">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="3475b-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3475b-153">輸入</span><span class="sxs-lookup"><span data-stu-id="3475b-153">INPUTS</span></span>

### <span data-ttu-id="3475b-154">System.String</span><span class="sxs-lookup"><span data-stu-id="3475b-154">System.String</span></span>

<span data-ttu-id="3475b-155">您可以使用管線將包含附加路徑的字串傳送至 `Update-FormatData` 。</span><span class="sxs-lookup"><span data-stu-id="3475b-155">You can pipe a string that contains the append path to `Update-FormatData`.</span></span>

## <span data-ttu-id="3475b-156">輸出</span><span class="sxs-lookup"><span data-stu-id="3475b-156">OUTPUTS</span></span>

### <span data-ttu-id="3475b-157">無</span><span class="sxs-lookup"><span data-stu-id="3475b-157">None</span></span>

<span data-ttu-id="3475b-158">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="3475b-158">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="3475b-159">注意</span><span class="sxs-lookup"><span data-stu-id="3475b-159">NOTES</span></span>

- <span data-ttu-id="3475b-160">`Update-FormatData` 也會在會話中，針對從模組匯入的命令更新格式化資料。</span><span class="sxs-lookup"><span data-stu-id="3475b-160">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="3475b-161">如果模組的格式化檔案變更，您可以執行 `Update-FormatData` 命令來更新匯入命令的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="3475b-161">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="3475b-162">您不需要再次匯入模組。</span><span class="sxs-lookup"><span data-stu-id="3475b-162">You do not need to import the module again.</span></span>

## <span data-ttu-id="3475b-163">相關連結</span><span class="sxs-lookup"><span data-stu-id="3475b-163">RELATED LINKS</span></span>

[<span data-ttu-id="3475b-164">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="3475b-164">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="3475b-165">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="3475b-165">Export-FormatData</span></span>](Export-FormatData.md)
