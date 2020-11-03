---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: b5dfd3e55ceadf4141e977f0fb879ba5d05538f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202047"
---
# <span data-ttu-id="86635-103">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="86635-103">Rename-Item</span></span>

## <span data-ttu-id="86635-104">概要</span><span class="sxs-lookup"><span data-stu-id="86635-104">SYNOPSIS</span></span>
<span data-ttu-id="86635-105">重新命名 PowerShell 提供者命名空間中的專案。</span><span class="sxs-lookup"><span data-stu-id="86635-105">Renames an item in a PowerShell provider namespace.</span></span>

## <span data-ttu-id="86635-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="86635-106">SYNTAX</span></span>

### <span data-ttu-id="86635-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="86635-107">ByPath (Default)</span></span>

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="86635-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="86635-108">ByLiteralPath</span></span>

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="86635-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="86635-109">DESCRIPTION</span></span>

<span data-ttu-id="86635-110">`Rename-Item`Cmdlet 會變更指定專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="86635-110">The `Rename-Item` cmdlet changes the name of a specified item.</span></span> <span data-ttu-id="86635-111">這個 Cmdlet 不會影響重新命名之項目的內容。</span><span class="sxs-lookup"><span data-stu-id="86635-111">This cmdlet does not affect the content of the item being renamed.</span></span>

<span data-ttu-id="86635-112">您無法使用 `Rename-Item` 移動專案，例如，藉由指定路徑和新名稱。</span><span class="sxs-lookup"><span data-stu-id="86635-112">You can't use `Rename-Item` to move an item, such as by specifying a path together with the new name.</span></span> <span data-ttu-id="86635-113">若要移動和重新命名專案，請使用 `Move-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86635-113">To move and rename an item, use the `Move-Item` cmdlet.</span></span>

## <span data-ttu-id="86635-114">範例</span><span class="sxs-lookup"><span data-stu-id="86635-114">EXAMPLES</span></span>

### <span data-ttu-id="86635-115">範例1：重新命名檔案</span><span class="sxs-lookup"><span data-stu-id="86635-115">Example 1: Rename a file</span></span>

<span data-ttu-id="86635-116">此命令會將檔案重新命名 `daily_file.txt` 為 `monday_file.txt` 。</span><span class="sxs-lookup"><span data-stu-id="86635-116">This command renames the file `daily_file.txt` to `monday_file.txt`.</span></span>

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### <span data-ttu-id="86635-117">範例2：重新命名和移動專案</span><span class="sxs-lookup"><span data-stu-id="86635-117">Example 2: Rename and move an item</span></span>

<span data-ttu-id="86635-118">您無法使用 `Rename-Item` 來重新命名和移動專案。</span><span class="sxs-lookup"><span data-stu-id="86635-118">You can't use `Rename-Item` to both rename and move an item.</span></span> <span data-ttu-id="86635-119">具體而言，您無法提供 **NewName** 參數值的路徑，除非路徑與 **path** 參數中指定的路徑相同。</span><span class="sxs-lookup"><span data-stu-id="86635-119">Specifically, you can't supply a path for the value of the **NewName** parameter, unless the path is identical to the path specified in the **Path** parameter.</span></span> <span data-ttu-id="86635-120">否則只允許新名稱。</span><span class="sxs-lookup"><span data-stu-id="86635-120">Otherwise, only a new name is permitted.</span></span>

<span data-ttu-id="86635-121">這個範例會嘗試將目前目錄中的檔案重新命名 `project.txt` 為 `old-project.txt` 目錄中的 `D:\Archive` 。</span><span class="sxs-lookup"><span data-stu-id="86635-121">This example attempts to rename the `project.txt` file in the current directory to `old-project.txt` in the `D:\Archive` directory.</span></span> <span data-ttu-id="86635-122">結果是顯示在輸出中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="86635-122">The result is the error shown in the output.</span></span>

```powershell
Rename-Item -Path "project.txt" -NewName "d:\archive\old-project.txt"
```

```Output
Rename-Item : can't rename because the target specified represents a path or device name.
At line:1 char:12
+ Rename-Item <<<<  -path project.txt -NewName d:\archive\old-project.txt
+ CategoryInfo          : InvalidArgument: (:) [Rename-Item], PS>  Move-Item -Path "project.txt" -De
stination "d:\archive\old-project.txt"
```

### <span data-ttu-id="86635-123">範例3：重新命名登錄機碼</span><span class="sxs-lookup"><span data-stu-id="86635-123">Example 3: Rename a registry key</span></span>

<span data-ttu-id="86635-124">此範例會將登錄機碼從 **廣告** 重新命名為「 **行銷** 」。</span><span class="sxs-lookup"><span data-stu-id="86635-124">This example renames a registry key from **Advertising** to **Marketing** .</span></span> <span data-ttu-id="86635-125">當命令完成時，會重新命名機碼，但機碼中的登錄項目則維持不變。</span><span class="sxs-lookup"><span data-stu-id="86635-125">When the command is complete, the key is renamed, but the registry entries in the key are unchanged.</span></span>

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### <span data-ttu-id="86635-126">範例4：重新命名多個檔案</span><span class="sxs-lookup"><span data-stu-id="86635-126">Example 4: Rename multiple files</span></span>

<span data-ttu-id="86635-127">此範例會將目前目錄中的所有檔案重新命名 `*.txt` 為 `*.log` 。</span><span class="sxs-lookup"><span data-stu-id="86635-127">This example renames all the `*.txt` files in the current directory to `*.log`.</span></span>

```powershell
Get-ChildItem *.txt
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.TXT
-a----        10/3/2019   7:46 AM           2918 Monday.Txt
-a----        10/3/2019   7:47 AM           2918 Wednesday.txt
```

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.Name -replace '.txt','.log' }
Get-ChildItem *.log
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.log
-a----        10/3/2019   7:46 AM           2918 Monday.log
-a----        10/3/2019   7:47 AM           2918 Wednesday.log
```

<span data-ttu-id="86635-128">指令 `Get-ChildItem` 程式會取得目前資料夾中具有副檔名的所有檔案， `.txt` 然後使用管線將它們傳送至 `Rename-Item` 。</span><span class="sxs-lookup"><span data-stu-id="86635-128">The `Get-ChildItem` cmdlet gets all the files in the current folder that have a `.txt` file extension then pipes them to `Rename-Item`.</span></span> <span data-ttu-id="86635-129">**NewName** 的值是腳本區塊，會在將該值提交給 **NewName** 參數之前執行。</span><span class="sxs-lookup"><span data-stu-id="86635-129">The value of **NewName** is a script block that runs before the value is submitted to the **NewName** parameter.</span></span>

<span data-ttu-id="86635-130">在腳本區塊中， `$_` 自動變數代表透過管線傳遞至命令的每個檔案物件。</span><span class="sxs-lookup"><span data-stu-id="86635-130">In the script block, the `$_` automatic variable represents each file object as it comes to the command through the pipeline.</span></span> <span data-ttu-id="86635-131">腳本區塊會使用 `-replace` 運算子，將每個檔案的副檔名取代為 `.log` 。</span><span class="sxs-lookup"><span data-stu-id="86635-131">The script block uses the `-replace` operator to replace the file extension of each file with `.log`.</span></span> <span data-ttu-id="86635-132">請注意，使用 `-replace` 運算子的比對不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="86635-132">Notice that matching using the `-replace` operator is not case sensitive.</span></span>

## <span data-ttu-id="86635-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="86635-133">PARAMETERS</span></span>

### <span data-ttu-id="86635-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="86635-134">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="86635-135">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="86635-135">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="86635-136">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="86635-136">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="86635-137">-Force</span><span class="sxs-lookup"><span data-stu-id="86635-137">-Force</span></span>

<span data-ttu-id="86635-138">強制 Cmdlet 重新命名無法以其他方式變更的專案，例如隱藏或唯讀的檔案，或是唯讀的別名或變數。</span><span class="sxs-lookup"><span data-stu-id="86635-138">Forces the cmdlet to rename items that can't otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="86635-139">此 Cmdlet 無法變更常數別名或變數。</span><span class="sxs-lookup"><span data-stu-id="86635-139">The cmdlet can't change constant aliases or variables.</span></span>
<span data-ttu-id="86635-140">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="86635-140">Implementation varies from provider to provider.</span></span> <span data-ttu-id="86635-141">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="86635-141">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="86635-142">即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="86635-142">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="86635-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="86635-143">-LiteralPath</span></span>

<span data-ttu-id="86635-144">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="86635-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="86635-145">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="86635-145">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="86635-146">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="86635-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="86635-147">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="86635-147">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="86635-148">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="86635-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="86635-149">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="86635-149">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="86635-150">-NewName</span><span class="sxs-lookup"><span data-stu-id="86635-150">-NewName</span></span>

<span data-ttu-id="86635-151">指定項目的新名稱。</span><span class="sxs-lookup"><span data-stu-id="86635-151">Specifies the new name of the item.</span></span> <span data-ttu-id="86635-152">只能輸入名稱，而非路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="86635-152">Enter only a name, not a path and name.</span></span> <span data-ttu-id="86635-153">如果您輸入的路徑與 **path** 參數中指定的路徑不同，則會 `Rename-Item` 產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="86635-153">If you enter a path that differs from the path that is specified in the **Path** parameter, `Rename-Item` generates an error.</span></span>
<span data-ttu-id="86635-154">若要重新命名和移動專案，請使用 `Move-Item` 。</span><span class="sxs-lookup"><span data-stu-id="86635-154">To rename and move an item, use `Move-Item`.</span></span>

<span data-ttu-id="86635-155">您不能在 **NewName** 參數的值中使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="86635-155">You can't use wildcard characters in the value of the **NewName** parameter.</span></span> <span data-ttu-id="86635-156">若要指定多個檔案的名稱，請在正則運算式中使用 **Replace** 運算子。</span><span class="sxs-lookup"><span data-stu-id="86635-156">To specify a name for multiple files, use the **Replace** operator in a regular expression.</span></span> <span data-ttu-id="86635-157">如需 Replace 運算子的詳細資訊，請參閱 [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="86635-157">For more information about the Replace operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="86635-158">-PassThru</span><span class="sxs-lookup"><span data-stu-id="86635-158">-PassThru</span></span>

<span data-ttu-id="86635-159">傳回物件，該物件表示管線的專案。</span><span class="sxs-lookup"><span data-stu-id="86635-159">Returns an object that represents the item to the pipeline.</span></span> <span data-ttu-id="86635-160">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="86635-160">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="86635-161">-Path</span><span class="sxs-lookup"><span data-stu-id="86635-161">-Path</span></span>

<span data-ttu-id="86635-162">指定要重新命名之項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="86635-162">Specifies the path of the item to rename.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="86635-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="86635-163">-Confirm</span></span>

<span data-ttu-id="86635-164">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="86635-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="86635-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="86635-165">-WhatIf</span></span>

<span data-ttu-id="86635-166">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="86635-166">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="86635-167">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="86635-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="86635-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="86635-168">CommonParameters</span></span>

<span data-ttu-id="86635-169">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="86635-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="86635-170">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="86635-170">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="86635-171">輸入</span><span class="sxs-lookup"><span data-stu-id="86635-171">INPUTS</span></span>

### <span data-ttu-id="86635-172">System.String</span><span class="sxs-lookup"><span data-stu-id="86635-172">System.String</span></span>

<span data-ttu-id="86635-173">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="86635-173">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="86635-174">輸出</span><span class="sxs-lookup"><span data-stu-id="86635-174">OUTPUTS</span></span>

### <span data-ttu-id="86635-175">None 或代表重新命名之專案的物件。</span><span class="sxs-lookup"><span data-stu-id="86635-175">None or an object that represents the renamed item.</span></span>

<span data-ttu-id="86635-176">如果您指定 **PassThru** 參數，此 Cmdlet 會產生代表重新命名之專案的物件。</span><span class="sxs-lookup"><span data-stu-id="86635-176">This cmdlet generates an object that represents the renamed item, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="86635-177">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="86635-177">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="86635-178">注意</span><span class="sxs-lookup"><span data-stu-id="86635-178">NOTES</span></span>

<span data-ttu-id="86635-179">`Rename-Item` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="86635-179">`Rename-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="86635-180">若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="86635-180">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="86635-181">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="86635-181">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="86635-182">相關連結</span><span class="sxs-lookup"><span data-stu-id="86635-182">RELATED LINKS</span></span>

[<span data-ttu-id="86635-183">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="86635-183">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="86635-184">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="86635-184">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="86635-185">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="86635-185">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="86635-186">Get-Item</span><span class="sxs-lookup"><span data-stu-id="86635-186">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="86635-187">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="86635-187">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="86635-188">Move-Item</span><span class="sxs-lookup"><span data-stu-id="86635-188">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="86635-189">New-Item</span><span class="sxs-lookup"><span data-stu-id="86635-189">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="86635-190">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="86635-190">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="86635-191">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="86635-191">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="86635-192">Set-Item</span><span class="sxs-lookup"><span data-stu-id="86635-192">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="86635-193">about_Providers</span><span class="sxs-lookup"><span data-stu-id="86635-193">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

