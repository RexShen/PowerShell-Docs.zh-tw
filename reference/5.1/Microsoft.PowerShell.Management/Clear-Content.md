---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: b318abb06d36be5e28b9dcc3dc62fd4a70ab38fb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204071"
---
# <span data-ttu-id="f17b0-103">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="f17b0-103">Clear-Content</span></span>

## <span data-ttu-id="f17b0-104">概要</span><span class="sxs-lookup"><span data-stu-id="f17b0-104">SYNOPSIS</span></span>
<span data-ttu-id="f17b0-105">刪除項目的內容，但不會刪除項目。</span><span class="sxs-lookup"><span data-stu-id="f17b0-105">Deletes the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="f17b0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f17b0-106">SYNTAX</span></span>

### <span data-ttu-id="f17b0-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="f17b0-107">Path (Default)</span></span>

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String>] [<CommonParameters>]
```

### <span data-ttu-id="f17b0-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f17b0-108">LiteralPath</span></span>

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [-Stream <String>] [<CommonParameters>]
```

## <span data-ttu-id="f17b0-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f17b0-109">DESCRIPTION</span></span>

<span data-ttu-id="f17b0-110">此 `Clear-Content` Cmdlet 會刪除專案的內容，例如刪除檔案中的文字，但不會刪除專案。</span><span class="sxs-lookup"><span data-stu-id="f17b0-110">The `Clear-Content` cmdlet deletes the contents of an item, such as deleting the text from a file, but it does not delete the item.</span></span>
<span data-ttu-id="f17b0-111">因此，項目會存在，但會是空的。</span><span class="sxs-lookup"><span data-stu-id="f17b0-111">As a result, the item exists, but it is empty.</span></span>
<span data-ttu-id="f17b0-112">`Clear-Content`類似于 `Clear-Item` ，但它適用于具有內容的專案，而不是具有值的專案。</span><span class="sxs-lookup"><span data-stu-id="f17b0-112">The `Clear-Content` is similar to `Clear-Item`, but it works on items with contents, instead of items with values.</span></span>

## <span data-ttu-id="f17b0-113">範例</span><span class="sxs-lookup"><span data-stu-id="f17b0-113">EXAMPLES</span></span>

### <span data-ttu-id="f17b0-114">範例1：從目錄中刪除所有內容</span><span class="sxs-lookup"><span data-stu-id="f17b0-114">Example 1: Delete all content from a directory</span></span>

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

<span data-ttu-id="f17b0-115">此命令刪除 SmpUsers 目錄之所有子目錄中的 "init.txt" 檔案的所有內容。</span><span class="sxs-lookup"><span data-stu-id="f17b0-115">This command deletes all of the content from the "init.txt" files in all subdirectories of the SmpUsers directory.</span></span>
<span data-ttu-id="f17b0-116">檔案不會被刪除，但會是空的。</span><span class="sxs-lookup"><span data-stu-id="f17b0-116">The files are not deleted, but they are empty.</span></span>

### <span data-ttu-id="f17b0-117">範例2：使用萬用字元刪除所有檔案的內容</span><span class="sxs-lookup"><span data-stu-id="f17b0-117">Example 2: Delete content of all files with a wildcard</span></span>

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

<span data-ttu-id="f17b0-118">此命令刪除目前目錄中副檔名為 ".log" 之所有檔案的內容，包括具有唯讀屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="f17b0-118">This command deletes the contents of all files in the current directory with the ".log" file name extension, including files with the read-only attribute.</span></span>
<span data-ttu-id="f17b0-119">路徑中的星號 (\*) 代表目前目錄中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="f17b0-119">The asterisk (\*) in the path represents all items in the current directory.</span></span>
<span data-ttu-id="f17b0-120">**Force** 參數可讓命令在唯讀檔案上生效。</span><span class="sxs-lookup"><span data-stu-id="f17b0-120">The **Force** parameter makes the command effective on read-only files.</span></span>
<span data-ttu-id="f17b0-121">使用篩選器，將命令限制為副檔名為 .log 的檔案，而不是 \* 在路徑中指定. log，讓作業更快。</span><span class="sxs-lookup"><span data-stu-id="f17b0-121">Using a filter to restrict the command to files with the .log file name extension instead of specifying \*.log in the path makes the operation faster.</span></span>

### <span data-ttu-id="f17b0-122">範例3：清除資料流程中的所有資料</span><span class="sxs-lookup"><span data-stu-id="f17b0-122">Example 3: Clear all data from a stream</span></span>

<span data-ttu-id="f17b0-123">此範例示範 Cmdlet 如何 `Clear-Content` 從替代資料流程清除內容，同時讓資料流程保持不變。</span><span class="sxs-lookup"><span data-stu-id="f17b0-123">This example shows how the `Clear-Content` cmdlet clears the content from an alternate data stream while leaving the stream intact.</span></span>

<span data-ttu-id="f17b0-124">第一個命令會使用 `Get-Content` Cmdlet 來取得 Copy-Script.ps1 檔案中的區域識別碼串流，該檔案是從網際網路下載。</span><span class="sxs-lookup"><span data-stu-id="f17b0-124">The first command uses the `Get-Content` cmdlet to get the content of the Zone.Identifier stream in the Copy-Script.ps1 file, which was downloaded from the Internet.</span></span>

<span data-ttu-id="f17b0-125">第二個命令會使用 `Clear-Content` Cmdlet 來清除內容。</span><span class="sxs-lookup"><span data-stu-id="f17b0-125">The second command uses the `Clear-Content` cmdlet to clear the content.</span></span>

<span data-ttu-id="f17b0-126">第三個命令重複第一個命令。</span><span class="sxs-lookup"><span data-stu-id="f17b0-126">The third command repeats the first command.</span></span> <span data-ttu-id="f17b0-127">它會確認內容已清除，但資料流程仍然存在。</span><span class="sxs-lookup"><span data-stu-id="f17b0-127">It verifies that the content is cleared, but the stream remains.</span></span> <span data-ttu-id="f17b0-128">如果資料流程已刪除，則命令會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f17b0-128">If the stream were deleted, the command would generate an error.</span></span>

<span data-ttu-id="f17b0-129">您可以使用像這樣的方法來清除替代資料流程的內容。</span><span class="sxs-lookup"><span data-stu-id="f17b0-129">You can use a method like this one to clear the content of an alternate data stream.</span></span> <span data-ttu-id="f17b0-130">但是，不建議使用這個方法來取代封鎖從網際網路下載之檔案的安全性檢查。</span><span class="sxs-lookup"><span data-stu-id="f17b0-130">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="f17b0-131">如果您確認下載的檔案是安全的，請使用 `Unblock-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f17b0-131">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

```powershell
Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
[ZoneTransfer]
ZoneId=3
```

```powershell
Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output

```

## <span data-ttu-id="f17b0-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f17b0-132">PARAMETERS</span></span>

### <span data-ttu-id="f17b0-133">-Credential</span><span class="sxs-lookup"><span data-stu-id="f17b0-133">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="f17b0-134">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="f17b0-134">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="f17b0-135">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 Invoke 命令。</span><span class="sxs-lookup"><span data-stu-id="f17b0-135">To impersonate another user, or elevate your credentials when running this cmdlet, use Invoke-Command.</span></span>

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

### <span data-ttu-id="f17b0-136">-Exclude</span><span class="sxs-lookup"><span data-stu-id="f17b0-136">-Exclude</span></span>

<span data-ttu-id="f17b0-137">以字串陣列指定此 Cmdlet 從內容路徑省略的字串。</span><span class="sxs-lookup"><span data-stu-id="f17b0-137">Specifies, as a string array, strings that this cmdlet omits from the path to the content.</span></span>
<span data-ttu-id="f17b0-138">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="f17b0-138">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="f17b0-139">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="f17b0-139">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="f17b0-140">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f17b0-140">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="f17b0-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="f17b0-141">-Filter</span></span>

<span data-ttu-id="f17b0-142">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="f17b0-142">Specifies a filter in the provider's format or language.</span></span>
<span data-ttu-id="f17b0-143">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="f17b0-143">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="f17b0-144">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="f17b0-144">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span>
<span data-ttu-id="f17b0-145">篩選比其他參數更有效率，因為提供者會在抓取物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="f17b0-145">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="f17b0-146">-Force</span><span class="sxs-lookup"><span data-stu-id="f17b0-146">-Force</span></span>

<span data-ttu-id="f17b0-147">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="f17b0-147">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="f17b0-148">-Include</span><span class="sxs-lookup"><span data-stu-id="f17b0-148">-Include</span></span>

<span data-ttu-id="f17b0-149">以字串陣列指定此 Cmdlet 所清除的內容。</span><span class="sxs-lookup"><span data-stu-id="f17b0-149">Specifies, as a string array, content that this cmdlet clears.</span></span>
<span data-ttu-id="f17b0-150">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="f17b0-150">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="f17b0-151">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="f17b0-151">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="f17b0-152">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f17b0-152">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="f17b0-153">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f17b0-153">-LiteralPath</span></span>

<span data-ttu-id="f17b0-154">指定要從中刪除內容之項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="f17b0-154">Specifies the paths to the items from which content is deleted.</span></span>
<span data-ttu-id="f17b0-155">與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="f17b0-155">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="f17b0-156">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f17b0-156">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="f17b0-157">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="f17b0-157">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="f17b0-158">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="f17b0-158">Single quotation marks tell having PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="f17b0-159">-Path</span><span class="sxs-lookup"><span data-stu-id="f17b0-159">-Path</span></span>

<span data-ttu-id="f17b0-160">指定要從中刪除內容之項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="f17b0-160">Specifies the paths to the items from which content is deleted.</span></span>
<span data-ttu-id="f17b0-161">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f17b0-161">Wildcards are permitted.</span></span>
<span data-ttu-id="f17b0-162">路徑需為項目的路徑，而非容器的路徑。</span><span class="sxs-lookup"><span data-stu-id="f17b0-162">The paths must be paths to items, not to containers.</span></span>
<span data-ttu-id="f17b0-163">例如，您必須指定一或多個檔案的路徑，而非目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="f17b0-163">For example, you must specify a path to one or more files, not a path to a directory.</span></span>
<span data-ttu-id="f17b0-164">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f17b0-164">Wildcards are permitted.</span></span>
<span data-ttu-id="f17b0-165">此為必要參數，但是參數名稱 ("Path") 為選擇性。</span><span class="sxs-lookup"><span data-stu-id="f17b0-165">This parameter is required, but the parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="f17b0-166">-Stream</span><span class="sxs-lookup"><span data-stu-id="f17b0-166">-Stream</span></span>

<span data-ttu-id="f17b0-167">指定內容的替代資料流程。</span><span class="sxs-lookup"><span data-stu-id="f17b0-167">Specifies an alternative data stream for content.</span></span>
<span data-ttu-id="f17b0-168">如果資料流程不存在，此 Cmdlet 會建立該資料流程。</span><span class="sxs-lookup"><span data-stu-id="f17b0-168">If the stream does not exist, this cmdlet creates it.</span></span>
<span data-ttu-id="f17b0-169">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f17b0-169">Wildcard characters are not supported.</span></span>

<span data-ttu-id="f17b0-170">**Stream** 是動態參數，FileSystem 提供者會將其加入至 `Clear-Content` 。</span><span class="sxs-lookup"><span data-stu-id="f17b0-170">**Stream** is a dynamic parameter that the FileSystem provider adds to `Clear-Content`.</span></span>
<span data-ttu-id="f17b0-171">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="f17b0-171">This parameter works only in file system drives.</span></span>

<span data-ttu-id="f17b0-172">您可以使用 `Clear-Content` Cmdlet 來變更區域的內容。識別碼替代資料流程。</span><span class="sxs-lookup"><span data-stu-id="f17b0-172">You can use the `Clear-Content` cmdlet to change the content of the Zone.Identifier alternate data stream.</span></span>
<span data-ttu-id="f17b0-173">不過，我們不建議您這樣做，以排除封鎖從網際網路下載之檔案的安全性檢查。</span><span class="sxs-lookup"><span data-stu-id="f17b0-173">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span>
<span data-ttu-id="f17b0-174">如果您確認下載的檔案是安全的，請使用 `Unblock-File` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f17b0-174">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="f17b0-175">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="f17b0-175">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f17b0-176">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="f17b0-176">-UseTransaction</span></span>

<span data-ttu-id="f17b0-177">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="f17b0-177">Includes the command in the active transaction.</span></span>
<span data-ttu-id="f17b0-178">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="f17b0-178">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="f17b0-179">如需詳細資訊，請參閱 [about_transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="f17b0-179">For more information, see [about_transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="f17b0-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f17b0-180">-Confirm</span></span>

<span data-ttu-id="f17b0-181">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f17b0-181">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f17b0-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f17b0-182">-WhatIf</span></span>

<span data-ttu-id="f17b0-183">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f17b0-183">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f17b0-184">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f17b0-184">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f17b0-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f17b0-185">CommonParameters</span></span>

<span data-ttu-id="f17b0-186">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="f17b0-186">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="f17b0-187">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="f17b0-187">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f17b0-188">輸入</span><span class="sxs-lookup"><span data-stu-id="f17b0-188">INPUTS</span></span>

### <span data-ttu-id="f17b0-189">無</span><span class="sxs-lookup"><span data-stu-id="f17b0-189">None</span></span>

<span data-ttu-id="f17b0-190">您無法透過管道傳送物件至 `Clear-Content` 。</span><span class="sxs-lookup"><span data-stu-id="f17b0-190">You cannot pipe objects to `Clear-Content`.</span></span>

## <span data-ttu-id="f17b0-191">輸出</span><span class="sxs-lookup"><span data-stu-id="f17b0-191">OUTPUTS</span></span>

### <span data-ttu-id="f17b0-192">無</span><span class="sxs-lookup"><span data-stu-id="f17b0-192">None</span></span>

<span data-ttu-id="f17b0-193">此 Cmdlet 不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="f17b0-193">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="f17b0-194">注意</span><span class="sxs-lookup"><span data-stu-id="f17b0-194">NOTES</span></span>

<span data-ttu-id="f17b0-195">您可以搭配 `Clear-Content` PowerShell FileSystem 提供者和其他操作內容的提供者使用。</span><span class="sxs-lookup"><span data-stu-id="f17b0-195">You can use `Clear-Content` with the PowerShell FileSystem provider and with other providers that manipulate content.</span></span>
<span data-ttu-id="f17b0-196">若要清除不被視為內容的專案，例如 PowerShell 憑證或登錄提供者所管理的專案，請使用 `Clear-Item` 。</span><span class="sxs-lookup"><span data-stu-id="f17b0-196">To clear items that are not considered to be content, such as items managed by the PowerShell Certificate or Registry providers, use `Clear-Item`.</span></span>

<span data-ttu-id="f17b0-197">此 `Clear-Content` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="f17b0-197">The `Clear-Content` cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="f17b0-198">若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="f17b0-198">To list the providers available in your session, type `Get-PsProvider`.</span></span>
<span data-ttu-id="f17b0-199">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="f17b0-199">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="f17b0-200">相關連結</span><span class="sxs-lookup"><span data-stu-id="f17b0-200">RELATED LINKS</span></span>

[<span data-ttu-id="f17b0-201">Add-Content</span><span class="sxs-lookup"><span data-stu-id="f17b0-201">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="f17b0-202">Get-Content</span><span class="sxs-lookup"><span data-stu-id="f17b0-202">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="f17b0-203">Get-Item</span><span class="sxs-lookup"><span data-stu-id="f17b0-203">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="f17b0-204">Set-Content</span><span class="sxs-lookup"><span data-stu-id="f17b0-204">Set-Content</span></span>](Set-Content.md)

[<span data-ttu-id="f17b0-205">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f17b0-205">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
