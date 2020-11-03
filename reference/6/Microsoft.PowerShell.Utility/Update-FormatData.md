---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 8e04de16aebc467360c7f9b02de6681ddc3e7ca3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204568"
---
# <span data-ttu-id="727be-103">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="727be-103">Update-FormatData</span></span>

## <span data-ttu-id="727be-104">概要</span><span class="sxs-lookup"><span data-stu-id="727be-104">SYNOPSIS</span></span>
<span data-ttu-id="727be-105">更新目前工作階段中的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="727be-105">Updates the formatting data in the current session.</span></span>

## <span data-ttu-id="727be-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="727be-106">SYNTAX</span></span>

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="727be-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="727be-107">DESCRIPTION</span></span>

<span data-ttu-id="727be-108">此 Cmdlet 會將格式化檔案 `Update-FormatData` 中的格式化資料重載至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="727be-108">The `Update-FormatData` cmdlet reloads the formatting data from formatting files into the current session.</span></span> <span data-ttu-id="727be-109">此 Cmdlet 可讓您更新格式化資料，而不需要重新開機 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="727be-109">This cmdlet lets you update the formatting data without restarting PowerShell.</span></span>

<span data-ttu-id="727be-110">如果沒有參數，會 `Update-FormatData` 重載它先前載入的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="727be-110">Without parameters, `Update-FormatData` reloads the formatting files that it loaded previously.</span></span>
<span data-ttu-id="727be-111">您可以使用的參數， `Update-FormatData` 將新的格式化檔案新增到會話。</span><span class="sxs-lookup"><span data-stu-id="727be-111">You can use the parameters of `Update-FormatData` to add new formatting files to the session.</span></span>

<span data-ttu-id="727be-112">格式化檔案是具有副檔名的 XML 格式文字檔 `format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="727be-112">Formatting files are text files in XML format with the `format.ps1xml` file name extension.</span></span> <span data-ttu-id="727be-113">檔案中的格式化資料會定義工作階段中 Microsoft .NET Framework 物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="727be-113">The formatting data in the files defines the display of Microsoft .NET Framework objects in the session.</span></span>

<span data-ttu-id="727be-114">PowerShell 啟動時，會從 PowerShell 原始程式碼載入格式資料。</span><span class="sxs-lookup"><span data-stu-id="727be-114">When PowerShell starts, it loads the format data from the PowerShell source code.</span></span> <span data-ttu-id="727be-115">不過，您可以建立自訂的 format.ps1xml 檔案，以更新目前會話中的格式。</span><span class="sxs-lookup"><span data-stu-id="727be-115">However, you can create custom format.ps1xml files to update formatting in the current session.</span></span> <span data-ttu-id="727be-116">您可以使用 `Update-FormatData` 將格式化資料重載目前的會話，而不需要重新開機 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="727be-116">You can use `Update-FormatData` to reload the formatting data into the current session without restarting PowerShell.</span></span> <span data-ttu-id="727be-117">當您已新增或變更格式化檔案，但不想中斷工作階段時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="727be-117">This is useful when you have added or changed a formatting file, but do not want to interrupt the session.</span></span>

<span data-ttu-id="727be-118">如需有關在 PowerShell 中格式化檔案的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="727be-118">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="727be-119">範例</span><span class="sxs-lookup"><span data-stu-id="727be-119">EXAMPLES</span></span>

### <span data-ttu-id="727be-120">範例 1︰重新載入先前載入的格式化檔案</span><span class="sxs-lookup"><span data-stu-id="727be-120">Example 1: Reload previously loaded formatting files</span></span>

```powershell
Update-FormatData
```

<span data-ttu-id="727be-121">這個命令會重新載入它先前載入的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="727be-121">This command reloads the formatting files that it loaded previously.</span></span>

### <span data-ttu-id="727be-122">範例 2︰重新載入格式化檔案以及追蹤和記錄格式化檔案</span><span class="sxs-lookup"><span data-stu-id="727be-122">Example 2: Reload formatting files and trace and log formatting files</span></span>

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

<span data-ttu-id="727be-123">這個命令會將格式化檔案重新載入工作階段，包括 Trace.format.ps1xml 和 Log.format.ps1xml 這兩個新檔案。</span><span class="sxs-lookup"><span data-stu-id="727be-123">This command reloads the formatting files into the session, including two new files, Trace.format.ps1xml and Log.format.ps1xml.</span></span>

<span data-ttu-id="727be-124">由於此命令使用 **AppendPath** 參數，因此，新檔案中的格式化資料會在來自內建檔案的格式化資料之後載入。</span><span class="sxs-lookup"><span data-stu-id="727be-124">Because the command uses the **AppendPath** parameter, the formatting data in the new files is loaded after the formatting data from the built-in files.</span></span>

<span data-ttu-id="727be-125">因為新檔案包含內建檔案中未參考物件的格式化資料，所以會使用 **AppendPath** 參數。</span><span class="sxs-lookup"><span data-stu-id="727be-125">The **AppendPath** parameter is used because the new files contain formatting data for objects that are not referenced in the built-in files.</span></span>

### <span data-ttu-id="727be-126">範例 3︰編輯格式化檔案，並重新載入</span><span class="sxs-lookup"><span data-stu-id="727be-126">Example 3: Edit a formatting file and reload it</span></span>

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

<span data-ttu-id="727be-127">這個範例示範如何在編輯格式化檔案之後重新載入它。</span><span class="sxs-lookup"><span data-stu-id="727be-127">This example shows how to reload a formatting file after you have edited it.</span></span>

<span data-ttu-id="727be-128">第一個命令將 NewFiles.format.ps1xml 檔案新增至工作階段。</span><span class="sxs-lookup"><span data-stu-id="727be-128">The first command adds the NewFiles.format.ps1xml file to the session.</span></span> <span data-ttu-id="727be-129">它會使用 **PrependPath** 參數，因為檔案包含內建檔案中所參考物件的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="727be-129">It uses the **PrependPath** parameter because the file contains formatting data for objects that are referenced in the built-in files.</span></span>

<span data-ttu-id="727be-130">新增 NewFiles.format.ps1xml 檔案並在這些工作階段中測試該檔案之後，作者編輯了該檔案。</span><span class="sxs-lookup"><span data-stu-id="727be-130">After adding the NewFiles.format.ps1xml file and testing it in these sessions, the author edits the file.</span></span>

<span data-ttu-id="727be-131">第二個命令會使用 `Update-FormatData` Cmdlet 來重載格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="727be-131">The second command uses the `Update-FormatData` cmdlet to reload the formatting files.</span></span> <span data-ttu-id="727be-132">因為先前已載入 NewFiles.format.ps1xml 檔案，所以 `Update-FormatData` 會自動重載，而不使用參數。</span><span class="sxs-lookup"><span data-stu-id="727be-132">Because the NewFiles.format.ps1xml file was previously loaded, `Update-FormatData` automatically reloads it without using parameters.</span></span>

## <span data-ttu-id="727be-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="727be-133">PARAMETERS</span></span>

### <span data-ttu-id="727be-134">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="727be-134">-AppendPath</span></span>

<span data-ttu-id="727be-135">指定此 Cmdlet 要新增至工作階段的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="727be-135">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="727be-136">這些檔案會在 PowerShell 載入內建的格式化檔案之後載入。</span><span class="sxs-lookup"><span data-stu-id="727be-136">The files are loaded after PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="727be-137">將 .NET 物件格式化時，PowerShell 會使用它針對每個 .NET 類型所找到的第一個格式化定義。</span><span class="sxs-lookup"><span data-stu-id="727be-137">When formatting .NET objects, PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="727be-138">如果您使用 **AppendPath** 參數，則 PowerShell 會在遇到您要新增的格式化資料之前，先從內建檔案搜尋資料。</span><span class="sxs-lookup"><span data-stu-id="727be-138">If you use the **AppendPath** parameter, PowerShell searches the data from the built-in files before it encounters the formatting data that you are adding.</span></span>

<span data-ttu-id="727be-139">使用這個參數來新增格式化 .NET 物件的檔案，而內建的格式化檔案未參考該物件。</span><span class="sxs-lookup"><span data-stu-id="727be-139">Use this parameter to add a file that formats a .NET object that is not referenced in the built-in formatting files.</span></span>

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

### <span data-ttu-id="727be-140">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="727be-140">-PrependPath</span></span>

<span data-ttu-id="727be-141">指定此 Cmdlet 要新增至工作階段的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="727be-141">Specifies formatting files that this cmdlet adds to the session.</span></span> <span data-ttu-id="727be-142">這些檔案會在 PowerShell 載入內建的格式化檔案之前載入。</span><span class="sxs-lookup"><span data-stu-id="727be-142">The files are loaded before PowerShell loads the built-in formatting files.</span></span>

<span data-ttu-id="727be-143">將 .NET 物件格式化時，PowerShell 會使用它針對每個 .NET 類型所找到的第一個格式化定義。</span><span class="sxs-lookup"><span data-stu-id="727be-143">When formatting .NET objects, PowerShell uses the first formatting definition that it finds for each .NET type.</span></span> <span data-ttu-id="727be-144">如果您使用 **PrependPath** 參數，則 PowerShell 會在遇到來自內建檔案的格式化資料之前，從您要新增的檔案中搜尋資料。</span><span class="sxs-lookup"><span data-stu-id="727be-144">If you use the **PrependPath** parameter, PowerShell searches the data from the files that you are adding before it encounters the formatting data from the built-in files.</span></span>

<span data-ttu-id="727be-145">使用這個參數來新增格式化 .NET 物件的檔案，而內建的格式化檔案亦參考該物件。</span><span class="sxs-lookup"><span data-stu-id="727be-145">Use this parameter to add a file that formats a .NET object that is also referenced in the built-in formatting files.</span></span>

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

### <span data-ttu-id="727be-146">-Confirm</span><span class="sxs-lookup"><span data-stu-id="727be-146">-Confirm</span></span>

<span data-ttu-id="727be-147">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="727be-147">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="727be-148">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="727be-148">-WhatIf</span></span>

<span data-ttu-id="727be-149">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="727be-149">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="727be-150">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="727be-150">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="727be-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="727be-151">CommonParameters</span></span>

<span data-ttu-id="727be-152">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="727be-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="727be-153">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="727be-153">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="727be-154">輸入</span><span class="sxs-lookup"><span data-stu-id="727be-154">INPUTS</span></span>

### <span data-ttu-id="727be-155">System.String</span><span class="sxs-lookup"><span data-stu-id="727be-155">System.String</span></span>

<span data-ttu-id="727be-156">您可以使用管線將包含附加路徑的字串傳送至 `Update-FormatData` 。</span><span class="sxs-lookup"><span data-stu-id="727be-156">You can pipe a string that contains the append path to `Update-FormatData`.</span></span>

## <span data-ttu-id="727be-157">輸出</span><span class="sxs-lookup"><span data-stu-id="727be-157">OUTPUTS</span></span>

### <span data-ttu-id="727be-158">無</span><span class="sxs-lookup"><span data-stu-id="727be-158">None</span></span>

<span data-ttu-id="727be-159">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="727be-159">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="727be-160">注意</span><span class="sxs-lookup"><span data-stu-id="727be-160">NOTES</span></span>

- <span data-ttu-id="727be-161">`Update-FormatData` 也會在會話中，針對從模組匯入的命令更新格式化資料。</span><span class="sxs-lookup"><span data-stu-id="727be-161">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="727be-162">如果模組的格式化檔案變更，您可以執行 `Update-FormatData` 命令來更新匯入命令的格式化資料。</span><span class="sxs-lookup"><span data-stu-id="727be-162">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="727be-163">您不需要再次匯入模組。</span><span class="sxs-lookup"><span data-stu-id="727be-163">You do not need to import the module again.</span></span>

## <span data-ttu-id="727be-164">相關連結</span><span class="sxs-lookup"><span data-stu-id="727be-164">RELATED LINKS</span></span>

[<span data-ttu-id="727be-165">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="727be-165">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="727be-166">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="727be-166">Export-FormatData</span></span>](Export-FormatData.md)
