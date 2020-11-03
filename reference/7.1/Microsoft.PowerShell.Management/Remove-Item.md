---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Item
ms.openlocfilehash: 3d33f0e3ab859d839b22a49a88860624ae06ddf2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202063"
---
# <span data-ttu-id="adf40-103">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="adf40-103">Remove-Item</span></span>

## <span data-ttu-id="adf40-104">概要</span><span class="sxs-lookup"><span data-stu-id="adf40-104">SYNOPSIS</span></span>
<span data-ttu-id="adf40-105">刪除指定的項目。</span><span class="sxs-lookup"><span data-stu-id="adf40-105">Deletes the specified items.</span></span>

## <span data-ttu-id="adf40-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="adf40-106">SYNTAX</span></span>

### <span data-ttu-id="adf40-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="adf40-107">Path (Default)</span></span>

```
Remove-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="adf40-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="adf40-108">LiteralPath</span></span>

```
Remove-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="adf40-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="adf40-109">DESCRIPTION</span></span>

<span data-ttu-id="adf40-110">此 `Remove-Item` Cmdlet 會刪除一或多個專案。</span><span class="sxs-lookup"><span data-stu-id="adf40-110">The `Remove-Item` cmdlet deletes one or more items.</span></span> <span data-ttu-id="adf40-111">由於有許多提供者支援，因此可以刪除許多不同類型的專案，包括檔案、資料夾、登錄機碼、變數、別名及函式。</span><span class="sxs-lookup"><span data-stu-id="adf40-111">Because it is supported by many providers, it can delete many different types of items, including files, folders, registry keys, variables, aliases, and functions.</span></span>

## <span data-ttu-id="adf40-112">範例</span><span class="sxs-lookup"><span data-stu-id="adf40-112">EXAMPLES</span></span>

### <span data-ttu-id="adf40-113">範例1：刪除具有任何副檔名的檔案</span><span class="sxs-lookup"><span data-stu-id="adf40-113">Example 1: Delete files that have any file name extension</span></span>

<span data-ttu-id="adf40-114">此範例會從資料夾中刪除名稱包含點 () 的所有檔案 `.` `C:\Test` 。</span><span class="sxs-lookup"><span data-stu-id="adf40-114">This example deletes all of the files that have names that include a dot (`.`) from the `C:\Test` folder.</span></span> <span data-ttu-id="adf40-115">因為此命令指定一個點，所以此命令不會刪除沒有副檔名的資料夾或檔案。</span><span class="sxs-lookup"><span data-stu-id="adf40-115">Because the command specifies a dot, the command does not delete folders or files that have no file name extension.</span></span>

```powershell
Remove-Item C:\Test\*.*
```

### <span data-ttu-id="adf40-116">範例2：刪除資料夾中的部分檔檔案</span><span class="sxs-lookup"><span data-stu-id="adf40-116">Example 2: Delete some of the document files in a folder</span></span>

<span data-ttu-id="adf40-117">這個範例會從目前的資料夾中刪除所有副檔名為的檔案， `.doc` 以及不包含的名稱 `*1*` 。</span><span class="sxs-lookup"><span data-stu-id="adf40-117">This example deletes from the current folder all files that have a `.doc` file name extension and a name that does not include `*1*`.</span></span>

```powershell
Remove-Item * -Include *.doc -Exclude *1*
```

<span data-ttu-id="adf40-118">它會使用萬用字元 (`*`) 來指定目前資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="adf40-118">It uses the wildcard character (`*`) to specify the contents of the current folder.</span></span> <span data-ttu-id="adf40-119">它會使用 **Include** 和 **Exclude** 參數來指定要刪除的檔案。</span><span class="sxs-lookup"><span data-stu-id="adf40-119">It uses the **Include** and **Exclude** parameters to specify the files to delete.</span></span>

### <span data-ttu-id="adf40-120">範例3：刪除隱藏的唯讀檔案</span><span class="sxs-lookup"><span data-stu-id="adf40-120">Example 3: Delete hidden, read-only files</span></span>

<span data-ttu-id="adf40-121">此命令會刪除 *隱藏* 和 *唯讀* 的檔案。</span><span class="sxs-lookup"><span data-stu-id="adf40-121">This command deletes a file that is both *hidden* and *read-only* .</span></span>

```powershell
Remove-Item -Path C:\Test\hidden-RO-file.txt -Force
```

<span data-ttu-id="adf40-122">它會使用 **Path** 參數來指定檔案。</span><span class="sxs-lookup"><span data-stu-id="adf40-122">It uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="adf40-123">它會使用 **Force** 參數來刪除它。</span><span class="sxs-lookup"><span data-stu-id="adf40-123">It uses the **Force** parameter to delete it.</span></span> <span data-ttu-id="adf40-124">若無 **強制** ，則無法刪除 _唯讀_ 或 _隱藏_ 的檔案。</span><span class="sxs-lookup"><span data-stu-id="adf40-124">Without **Force** , you cannot delete _read-only_ or _hidden_ files.</span></span>

### <span data-ttu-id="adf40-125">範例4：以遞迴方式刪除子資料夾中的檔案</span><span class="sxs-lookup"><span data-stu-id="adf40-125">Example 4: Delete files in subfolders recursively</span></span>

<span data-ttu-id="adf40-126">此命令會以遞迴方式刪除目前資料夾和所有子資料夾中的所有 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="adf40-126">This command deletes all of the CSV files in the current folder and all subfolders recursively.</span></span>

<span data-ttu-id="adf40-127">因為中的 **遞迴** 參數 `Remove-Item` 有已知的問題，所以此範例中的命令會使用 `Get-ChildItem` 來取得所需的檔案，然後使用管線運算子將它們傳遞給 `Remove-Item` 。</span><span class="sxs-lookup"><span data-stu-id="adf40-127">Because the **Recurse** parameter in `Remove-Item` has a known issue, the command in this example uses `Get-ChildItem` to get the desired files, and then uses the pipeline operator to pass them to `Remove-Item`.</span></span>

```powershell
Get-ChildItem * -Include *.csv -Recurse | Remove-Item
```

<span data-ttu-id="adf40-128">在 `Get-ChildItem` 命令中， **Path** 的值為 (`*`) ，代表目前資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="adf40-128">In the `Get-ChildItem` command, **Path** has a value of (`*`), which represents the contents of the current folder.</span></span> <span data-ttu-id="adf40-129">它使用 **Include** 來指定 CSV 檔案類型，並使用 **遞迴** 來使抓取遞迴。</span><span class="sxs-lookup"><span data-stu-id="adf40-129">It uses **Include** to specify the CSV file type, and it uses **Recurse** to make the retrieval recursive.</span></span> <span data-ttu-id="adf40-130">如果您嘗試指定檔案類型的路徑（例如 `-Path *.csv` ），則 Cmdlet 會將搜尋的主旨解釋為沒有子專案的檔案，且 **遞迴** 失敗。</span><span class="sxs-lookup"><span data-stu-id="adf40-130">If you try to specify the file type the path, such as `-Path *.csv`, the cmdlet interprets the subject of the search to be a file that has no child items, and **Recurse** fails.</span></span>

### <span data-ttu-id="adf40-131">範例5：以遞迴方式刪除子機碼</span><span class="sxs-lookup"><span data-stu-id="adf40-131">Example 5: Delete subkeys recursively</span></span>

<span data-ttu-id="adf40-132">此命令會刪除 "OldApp" 登錄機碼及其所有子機碼和值。</span><span class="sxs-lookup"><span data-stu-id="adf40-132">This command deletes the "OldApp" registry key and all its subkeys and values.</span></span> <span data-ttu-id="adf40-133">它會使用 `Remove-Item` 來移除索引鍵。</span><span class="sxs-lookup"><span data-stu-id="adf40-133">It uses `Remove-Item` to remove the key.</span></span> <span data-ttu-id="adf40-134">已指定路徑，但會省略選擇性參數名稱 ( **路徑** ) 。</span><span class="sxs-lookup"><span data-stu-id="adf40-134">The path is specified, but the optional parameter name ( **Path** ) is omitted.</span></span>

<span data-ttu-id="adf40-135">**遞迴** 參數會以遞迴方式刪除 "OldApp" 索引鍵的所有內容。</span><span class="sxs-lookup"><span data-stu-id="adf40-135">The **Recurse** parameter deletes all of the contents of the "OldApp" key recursively.</span></span> <span data-ttu-id="adf40-136">如果機碼包含子機碼，而您省略了 **遞迴** 參數，系統會提示您確認是否要刪除機碼的內容。</span><span class="sxs-lookup"><span data-stu-id="adf40-136">If the key contains subkeys and you omit the **Recurse** parameter, you are prompted to confirm that you want to delete the contents of the key.</span></span>

```powershell
Remove-Item HKLM:\Software\MyCompany\OldApp -Recurse
```

### <span data-ttu-id="adf40-137">範例6：刪除具有特殊字元的檔案</span><span class="sxs-lookup"><span data-stu-id="adf40-137">Example 6: Deleting files with special characters</span></span>

<span data-ttu-id="adf40-138">下列範例示範如何刪除包含特殊字元的檔案，例如方括弧或括弧。</span><span class="sxs-lookup"><span data-stu-id="adf40-138">The following example shows how to delete files that contain special characters like brackets or parentheses.</span></span>

```powershell
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*'
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*' | ForEach-Object { Remove-Item -LiteralPath $_.Name }
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
```

### <span data-ttu-id="adf40-139">範例7：移除替代資料流程</span><span class="sxs-lookup"><span data-stu-id="adf40-139">Example 7: Remove an alternate data stream</span></span>

<span data-ttu-id="adf40-140">此範例示範如何使用 Cmdlet 的 **資料流程** 動態參數 `Remove-Item` 來刪除替代資料流程。</span><span class="sxs-lookup"><span data-stu-id="adf40-140">This example shows how to use the **Stream** dynamic parameter of the `Remove-Item` cmdlet to delete an alternate data stream.</span></span> <span data-ttu-id="adf40-141">Stream 參數是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="adf40-141">The stream parameter is introduced in Windows PowerShell 3.0.</span></span>

```powershell
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
   FileName: \\C:\Test\Copy-Script.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

```

```powershell
Remove-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
Get-Item : Could not open alternate data stream 'Zone.Identifier' of file 'C:\Test\Copy-Script.ps1'.
At line:1 char:1
+ Get-Item 'C:\Test\Copy-Script.ps1' -Stream Zone.Identifier
+ [!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()]~~
    + CategoryInfo          : ObjectNotFound: (C:\Test\Copy-Script.ps1:String) [Get-Item], FileNotFoundE
   xception
    + FullyQualifiedErrorId : AlternateDataStreamNotFound,Microsoft.PowerShell.Commands.GetItemCommand

```

<span data-ttu-id="adf40-142">**Stream** 參數會 `Get-Item` 取得檔案的 **區域。識別碼** 資料流程 `Copy-Script.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="adf40-142">The **Stream** parameter `Get-Item` gets the **Zone.Identifier** stream of the `Copy-Script.ps1` file.</span></span> <span data-ttu-id="adf40-143">`Remove-Item` 使用 **資料流程** 參數來移除 **區域。** 檔案的識別碼資料流程。</span><span class="sxs-lookup"><span data-stu-id="adf40-143">`Remove-Item` uses the **Stream** parameter to remove the **Zone.Identifier** stream of the file.</span></span> <span data-ttu-id="adf40-144">最後，此 `Get-Item` Cmdlet 會顯示已刪除的 **區域識別碼** 串流。</span><span class="sxs-lookup"><span data-stu-id="adf40-144">Finally, the `Get-Item` cmdlet shows that the **Zone.Identifier** stream was deleted.</span></span>

## <span data-ttu-id="adf40-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="adf40-145">PARAMETERS</span></span>

### <span data-ttu-id="adf40-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="adf40-146">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="adf40-147">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="adf40-147">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="adf40-148">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="adf40-148">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="adf40-149">-Exclude</span><span class="sxs-lookup"><span data-stu-id="adf40-149">-Exclude</span></span>

<span data-ttu-id="adf40-150">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="adf40-150">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="adf40-151">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="adf40-151">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="adf40-152">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="adf40-152">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="adf40-153">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="adf40-153">Wildcard characters are permitted.</span></span> <span data-ttu-id="adf40-154">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="adf40-154">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="adf40-155">-Filter</span><span class="sxs-lookup"><span data-stu-id="adf40-155">-Filter</span></span>

<span data-ttu-id="adf40-156">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="adf40-156">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="adf40-157">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="adf40-157">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="adf40-158">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="adf40-158">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="adf40-159">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="adf40-159">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="adf40-160">-Force</span><span class="sxs-lookup"><span data-stu-id="adf40-160">-Force</span></span>

<span data-ttu-id="adf40-161">強制 Cmdlet 移除無法以其他方式變更的專案，例如隱藏或唯讀的檔案，或是唯讀的別名或變數。</span><span class="sxs-lookup"><span data-stu-id="adf40-161">Forces the cmdlet to remove items that cannot otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="adf40-162">Cmdlet 無法移除常數別名或變數。</span><span class="sxs-lookup"><span data-stu-id="adf40-162">The cmdlet cannot remove constant aliases or variables.</span></span>
<span data-ttu-id="adf40-163">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="adf40-163">Implementation varies from provider to provider.</span></span> <span data-ttu-id="adf40-164">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="adf40-164">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="adf40-165">即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="adf40-165">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="adf40-166">-Include</span><span class="sxs-lookup"><span data-stu-id="adf40-166">-Include</span></span>

<span data-ttu-id="adf40-167">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="adf40-167">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="adf40-168">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="adf40-168">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="adf40-169">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="adf40-169">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="adf40-170">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="adf40-170">Wildcard characters are permitted.</span></span> <span data-ttu-id="adf40-171">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="adf40-171">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="adf40-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="adf40-172">-LiteralPath</span></span>

<span data-ttu-id="adf40-173">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="adf40-173">Specifies a path to one or more locations.</span></span> <span data-ttu-id="adf40-174">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="adf40-174">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="adf40-175">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="adf40-175">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="adf40-176">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="adf40-176">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="adf40-177">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="adf40-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="adf40-178">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="adf40-178">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="adf40-179">-Path</span><span class="sxs-lookup"><span data-stu-id="adf40-179">-Path</span></span>

<span data-ttu-id="adf40-180">指定要移除之專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="adf40-180">Specifies a path of the items being removed.</span></span>
<span data-ttu-id="adf40-181">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="adf40-181">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="adf40-182">-Recurse</span><span class="sxs-lookup"><span data-stu-id="adf40-182">-Recurse</span></span>

<span data-ttu-id="adf40-183">指出此 Cmdlet 會刪除指定位置和位置的所有子專案中的專案。</span><span class="sxs-lookup"><span data-stu-id="adf40-183">Indicates that this cmdlet deletes the items in the specified locations and in all child items of the locations.</span></span>

<span data-ttu-id="adf40-184">當搭配 **Include** 參數使用時， **遞迴** 參數可能不會刪除所有子資料夾或所有子專案。</span><span class="sxs-lookup"><span data-stu-id="adf40-184">When it is used with the **Include** parameter, the **Recurse** parameter might not delete all subfolders or all child items.</span></span> <span data-ttu-id="adf40-185">這是已知的問題。</span><span class="sxs-lookup"><span data-stu-id="adf40-185">This is a known issue.</span></span> <span data-ttu-id="adf40-186">若要解決此問題，請嘗試將命令的結果傳送 `Get-ChildItem -Recurse` 至 `Remove-Item` ，如本主題的「範例4」所述。</span><span class="sxs-lookup"><span data-stu-id="adf40-186">As a workaround, try piping results of the `Get-ChildItem -Recurse` command to `Remove-Item`, as described in "Example 4" in this topic.</span></span>

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

### <span data-ttu-id="adf40-187">-Stream</span><span class="sxs-lookup"><span data-stu-id="adf40-187">-Stream</span></span>

<span data-ttu-id="adf40-188">**資料流程** 參數是動態參數，FileSystem 提供者會將其加入至 `Remove-Item` 。</span><span class="sxs-lookup"><span data-stu-id="adf40-188">The **Stream** parameter is a dynamic parameter that the FileSystem provider adds to `Remove-Item`.</span></span>
<span data-ttu-id="adf40-189">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="adf40-189">This parameter works only in file system drives.</span></span>

<span data-ttu-id="adf40-190">您可以使用 `Remove-Item` 刪除替代資料流程。</span><span class="sxs-lookup"><span data-stu-id="adf40-190">You can use `Remove-Item` to delete an alternative data stream.</span></span> <span data-ttu-id="adf40-191">但是，不建議使用這個方法來取代封鎖從網際網路下載之檔案的安全性檢查。</span><span class="sxs-lookup"><span data-stu-id="adf40-191">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="adf40-192">如果您確認下載的檔案是安全的，請使用 `Unblock-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="adf40-192">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="adf40-193">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="adf40-193">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="adf40-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="adf40-194">-Confirm</span></span>

<span data-ttu-id="adf40-195">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="adf40-195">Prompts you for confirmation before running the cmdlet.</span></span> <span data-ttu-id="adf40-196">如需詳細資訊，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="adf40-196">For more information, see the following articles:</span></span>

- [<span data-ttu-id="adf40-197">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="adf40-197">about_Preference_Variables</span></span>](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)
- [<span data-ttu-id="adf40-198">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="adf40-198">about_Functions_CmdletBindingAttribute</span></span>](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

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

### <span data-ttu-id="adf40-199">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="adf40-199">-WhatIf</span></span>

<span data-ttu-id="adf40-200">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="adf40-200">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="adf40-201">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="adf40-201">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="adf40-202">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="adf40-202">CommonParameters</span></span>

<span data-ttu-id="adf40-203">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="adf40-203">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="adf40-204">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="adf40-204">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="adf40-205">輸入</span><span class="sxs-lookup"><span data-stu-id="adf40-205">INPUTS</span></span>

### <span data-ttu-id="adf40-206">System.String</span><span class="sxs-lookup"><span data-stu-id="adf40-206">System.String</span></span>

<span data-ttu-id="adf40-207">您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="adf40-207">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="adf40-208">輸出</span><span class="sxs-lookup"><span data-stu-id="adf40-208">OUTPUTS</span></span>

### <span data-ttu-id="adf40-209">無</span><span class="sxs-lookup"><span data-stu-id="adf40-209">None</span></span>

<span data-ttu-id="adf40-210">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="adf40-210">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="adf40-211">注意</span><span class="sxs-lookup"><span data-stu-id="adf40-211">NOTES</span></span>

<span data-ttu-id="adf40-212">此 `Remove-Item` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="adf40-212">The `Remove-Item` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="adf40-213">若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="adf40-213">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="adf40-214">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="adf40-214">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="adf40-215">當您嘗試在不使用 **遞迴** 參數的情況下刪除包含專案的資料夾時，此 Cmdlet 會提示您確認。</span><span class="sxs-lookup"><span data-stu-id="adf40-215">When you try to delete a folder that contains items without using the **Recurse** parameter, the cmdlet prompts for confirmation.</span></span> <span data-ttu-id="adf40-216">使用 `-Confirm:$false` 不會抑制提示。</span><span class="sxs-lookup"><span data-stu-id="adf40-216">Using `-Confirm:$false` does not suppress the prompt.</span></span> <span data-ttu-id="adf40-217">這是原廠設定。</span><span class="sxs-lookup"><span data-stu-id="adf40-217">This is by design.</span></span>

## <span data-ttu-id="adf40-218">相關連結</span><span class="sxs-lookup"><span data-stu-id="adf40-218">RELATED LINKS</span></span>

[<span data-ttu-id="adf40-219">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="adf40-219">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="adf40-220">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="adf40-220">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="adf40-221">Get-Item</span><span class="sxs-lookup"><span data-stu-id="adf40-221">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="adf40-222">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="adf40-222">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="adf40-223">Move-Item</span><span class="sxs-lookup"><span data-stu-id="adf40-223">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="adf40-224">New-Item</span><span class="sxs-lookup"><span data-stu-id="adf40-224">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="adf40-225">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="adf40-225">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="adf40-226">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="adf40-226">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="adf40-227">Set-Item</span><span class="sxs-lookup"><span data-stu-id="adf40-227">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="adf40-228">about_Providers</span><span class="sxs-lookup"><span data-stu-id="adf40-228">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="adf40-229">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="adf40-229">about_Preference_Variables</span></span>](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)

[<span data-ttu-id="adf40-230">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="adf40-230">about_Functions_CmdletBindingAttribute</span></span>](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

