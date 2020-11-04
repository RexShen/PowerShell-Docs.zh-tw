---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: d3637825e7570e5fb0f3ff77efbc89e9d93974a3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203600"
---
# <span data-ttu-id="932eb-103">Move-Item</span><span class="sxs-lookup"><span data-stu-id="932eb-103">Move-Item</span></span>

## <span data-ttu-id="932eb-104">概要</span><span class="sxs-lookup"><span data-stu-id="932eb-104">SYNOPSIS</span></span>
<span data-ttu-id="932eb-105">將項目從某個位置移動到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="932eb-105">Moves an item from one location to another.</span></span>

## <span data-ttu-id="932eb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="932eb-106">SYNTAX</span></span>

### <span data-ttu-id="932eb-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="932eb-107">Path (Default)</span></span>

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="932eb-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="932eb-108">LiteralPath</span></span>

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="932eb-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="932eb-109">DESCRIPTION</span></span>

<span data-ttu-id="932eb-110">`Move-Item`Cmdlet 會將專案（包括其屬性、內容及子專案）從一個位置移到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="932eb-110">The `Move-Item` cmdlet moves an item, including its properties, contents, and child items, from one location to another location.</span></span>
<span data-ttu-id="932eb-111">移動的位置需由同一個提供者支援。</span><span class="sxs-lookup"><span data-stu-id="932eb-111">The locations must be supported by the same provider.</span></span>
<span data-ttu-id="932eb-112">例如，它可以將檔案或子目錄從一個目錄移至另一個，或將登錄子機碼從一個機碼移至另一個。</span><span class="sxs-lookup"><span data-stu-id="932eb-112">For example, it can move a file or subdirectory from one directory to another or move a registry subkey from one key to another.</span></span>
<span data-ttu-id="932eb-113">當您移動項目後，就會將它加到新位置，並從其原始位置中刪除。</span><span class="sxs-lookup"><span data-stu-id="932eb-113">When you move an item, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="932eb-114">範例</span><span class="sxs-lookup"><span data-stu-id="932eb-114">EXAMPLES</span></span>

### <span data-ttu-id="932eb-115">範例1：將檔案移至另一個目錄，並將它重新命名</span><span class="sxs-lookup"><span data-stu-id="932eb-115">Example 1: Move a file to another directory and rename it</span></span>

<span data-ttu-id="932eb-116">此命令會將 "Test.txt" 檔案從 `C:` 磁片磁碟機移至 "E:\Temp" 目錄，並將它從 "test.txt" 重新命名為 "tst.txt"。</span><span class="sxs-lookup"><span data-stu-id="932eb-116">This command moves the "Test.txt" file from the `C:` drive to the "E:\Temp" directory and renames it from "test.txt" to "tst.txt".</span></span>

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### <span data-ttu-id="932eb-117">範例2：將目錄和其內容移至另一個目錄</span><span class="sxs-lookup"><span data-stu-id="932eb-117">Example 2: Move a directory and its contents to another directory</span></span>

<span data-ttu-id="932eb-118">此命令會將 "C：\Temp" 目錄和其內容移至 "C:\Logs" 目錄。</span><span class="sxs-lookup"><span data-stu-id="932eb-118">This command moves the "C:\Temp" directory and its contents to the "C:\Logs" directory.</span></span>
<span data-ttu-id="932eb-119">"Temp" 目錄及其所有子目錄和檔案都會出現在 "Logs" 目錄中。</span><span class="sxs-lookup"><span data-stu-id="932eb-119">The "Temp" directory, and all of its subdirectories and files, then appear in the "Logs" directory.</span></span>

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### <span data-ttu-id="932eb-120">範例3：將指定之副檔名的所有檔案從目前目錄移至另一個目錄</span><span class="sxs-lookup"><span data-stu-id="932eb-120">Example 3: Move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="932eb-121">此命令會將目前目錄 (中 ( "\* .txt" ) 的所有文字檔移 ( '. ') # A5 加入 "C:\Logs" 目錄。</span><span class="sxs-lookup"><span data-stu-id="932eb-121">This command moves all of the text files ("\*.txt") in the current directory (represented by a dot ('.')) to the "C:\Logs" directory.</span></span>

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### <span data-ttu-id="932eb-122">範例4：以遞迴方式將指定之副檔名的所有檔案從目前目錄移至另一個目錄</span><span class="sxs-lookup"><span data-stu-id="932eb-122">Example 4: Recursively move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="932eb-123">此命令會以遞迴方式將所有文字檔從目前的目錄和所有子目錄移至 "C:\TextFiles" 目錄。</span><span class="sxs-lookup"><span data-stu-id="932eb-123">This command moves all of the text files from the current directory and all subdirectories, recursively, to the "C:\TextFiles" directory.</span></span>

<span data-ttu-id="932eb-124">此命令會使用 `Get-ChildItem` Cmdlet 來取得目前目錄中的所有子專案， (由點 \[ . \]) 及其子目錄（副檔名為 " *.txt"）。它會使用 **遞迴** 參數來使抓取遞迴，並使用 Include 參數將抓取限制為 "* .txt" 檔案。</span><span class="sxs-lookup"><span data-stu-id="932eb-124">The command uses the `Get-ChildItem` cmdlet to get all of the child items in the current directory (represented by the dot \[.\]) and its subdirectories that have a " *.txt" file name extension. It uses the **Recurse** parameter to make the retrieval recursive and the Include parameter to limit the retrieval to "* .txt" files.</span></span>

<span data-ttu-id="932eb-125">管線運算子 (`|`) 將此命令的結果傳送至 `Move-Item` ，這會將文字檔移至 "TextFiles" 目錄。</span><span class="sxs-lookup"><span data-stu-id="932eb-125">The pipeline operator (`|`) sends the results of this command to `Move-Item`, which moves the text files to the "TextFiles" directory.</span></span>

<span data-ttu-id="932eb-126">如果要移至 "C:\Textfiles" 的檔案具有相同的名稱，則會 `Move-Item` 顯示錯誤並繼續進行，但是只會將每個名稱的一個檔案移至 "C:\Textfiles"。</span><span class="sxs-lookup"><span data-stu-id="932eb-126">If files that are to be moved to "C:\Textfiles" have the same name, `Move-Item` displays an error and continues, but it moves only one file with each name to "C:\Textfiles".</span></span>
<span data-ttu-id="932eb-127">其他檔案仍會留在原始的目錄中。</span><span class="sxs-lookup"><span data-stu-id="932eb-127">The other files remain in their original directories.</span></span>

<span data-ttu-id="932eb-128">如果 "Textfiles" 目錄 (或目的地路徑) 的任何其他元素不存在，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="932eb-128">If the "Textfiles" directory (or any other element of the destination path) does not exist, the command fails.</span></span>
<span data-ttu-id="932eb-129">即使您使用 **Force** 參數，也不會為您建立遺漏的目錄。</span><span class="sxs-lookup"><span data-stu-id="932eb-129">The missing directory is not created for you, even if you use the **Force** parameter.</span></span>
<span data-ttu-id="932eb-130">`Move-Item` 將第一個專案移至稱為 "Textfiles" 的檔案，然後顯示說明該檔案已存在的錯誤。</span><span class="sxs-lookup"><span data-stu-id="932eb-130">`Move-Item` moves the first item to a file called "Textfiles" and then displays an error explaining that the file already exists.</span></span>

<span data-ttu-id="932eb-131">此外，根據預設，不 `Get-ChildItem` 會移動隱藏的檔案。</span><span class="sxs-lookup"><span data-stu-id="932eb-131">Also, by default, `Get-ChildItem` does not move hidden files.</span></span>
<span data-ttu-id="932eb-132">若要移動隱藏的檔案，請使用 **Force** 參數搭配 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="932eb-132">To move hidden files, use the **Force** parameter with `Get-ChildItem`.</span></span>

<span data-ttu-id="932eb-133">注意：在 Windows PowerShell 2.0 中，使用 Cmdlet 的 **遞迴** 參數時 `Get-ChildItem` ， **Path** 參數的值必須是容器。</span><span class="sxs-lookup"><span data-stu-id="932eb-133">Note: In Windows PowerShell 2.0, when using the **Recurse** parameter of the `Get-ChildItem` cmdlet, the value of the **Path** parameter must be a container.</span></span>
<span data-ttu-id="932eb-134">請使用 **Include** 參數來指定 .txt 副檔名篩選 (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`)。</span><span class="sxs-lookup"><span data-stu-id="932eb-134">Use the **Include** parameter to specify the .txt file name extension filter (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).</span></span>

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

### <span data-ttu-id="932eb-135">範例5：將登錄機碼和值移至另一個金鑰</span><span class="sxs-lookup"><span data-stu-id="932eb-135">Example 5: Move registry keys and values to another key</span></span>

<span data-ttu-id="932eb-136">此命令會將 "HKLM\Software" 中 "MyCompany" 登錄機碼內的登錄機碼和值移至 "Mynewcompany 機" 機碼。</span><span class="sxs-lookup"><span data-stu-id="932eb-136">This command moves the registry keys and values within the "MyCompany" registry key in "HKLM\Software" to the "MyNewCompany" key.</span></span>
<span data-ttu-id="932eb-137">萬用字元 ( ' \* ' ) 表示應移動 "MyCompany" 索引鍵的內容，而不是金鑰本身。</span><span class="sxs-lookup"><span data-stu-id="932eb-137">The wildcard character ('\*') indicates that the contents of the "MyCompany" key should be moved, not the key itself.</span></span>
<span data-ttu-id="932eb-138">在這個命令中，會省略選擇性的 **路徑** 和 **目的地** 參數名稱。</span><span class="sxs-lookup"><span data-stu-id="932eb-138">In this command, the optional **Path** and **Destination** parameter names are omitted.</span></span>

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### <span data-ttu-id="932eb-139">範例6：將目錄和其內容移至指定目錄的子目錄</span><span class="sxs-lookup"><span data-stu-id="932eb-139">Example 6: Move a directory and its contents to a subdirectory of the specified directory</span></span>

<span data-ttu-id="932eb-140">此命令會將 "Logs \[ 9 月 \` 6 日 \] " 目錄 (及其內容) 移至 "logs \[ 2006 \] " 目錄。</span><span class="sxs-lookup"><span data-stu-id="932eb-140">This command moves the "Logs\[Sept\`06\]" directory (and its contents) into the "Logs\[2006\]" directory.</span></span>

<span data-ttu-id="932eb-141">使用 **LiteralPath** 參數而非 **Path** ，因為原始目錄名稱包含左括弧和右括弧字元 ( " \[ " 和 " \] " ) 。</span><span class="sxs-lookup"><span data-stu-id="932eb-141">The **LiteralPath** parameter is used instead of **Path** , because the original directory name includes left bracket and right bracket characters ("\[" and "\]").</span></span>
<span data-ttu-id="932eb-142">路徑也會括在單引號 (' ') 中，因此不會誤譯倒單引號 (\`)。</span><span class="sxs-lookup"><span data-stu-id="932eb-142">The path is also enclosed in single quotation marks (' '), so that the backtick symbol (\`) is not misinterpreted.</span></span>

<span data-ttu-id="932eb-143">**Destination** 參數不需要常值路徑，因為目的地變數也必須括在單引號中，因為它包含可能會誤解的括弧。</span><span class="sxs-lookup"><span data-stu-id="932eb-143">The **Destination** parameter does not require a literal path, because the Destination variable also must be enclosed in single quotation marks, because it includes brackets that can be misinterpreted.</span></span>

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

## <span data-ttu-id="932eb-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="932eb-144">PARAMETERS</span></span>

### <span data-ttu-id="932eb-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="932eb-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="932eb-146">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="932eb-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="932eb-147">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="932eb-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="932eb-148">-Destination</span><span class="sxs-lookup"><span data-stu-id="932eb-148">-Destination</span></span>

<span data-ttu-id="932eb-149">指定要移動之項目所在位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="932eb-149">Specifies the path to the location where the items are being moved.</span></span>
<span data-ttu-id="932eb-150">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="932eb-150">The default is the current directory.</span></span>
<span data-ttu-id="932eb-151">允許使用萬用字元，但是結果必須指定單一位置。</span><span class="sxs-lookup"><span data-stu-id="932eb-151">Wildcards are permitted, but the result must specify a single location.</span></span>

<span data-ttu-id="932eb-152">若要重新命名正在移動的專案，請在 **Destination** 參數的值中指定新名稱。</span><span class="sxs-lookup"><span data-stu-id="932eb-152">To rename the item being moved, specify a new name in the value of the **Destination** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="932eb-153">-Exclude</span><span class="sxs-lookup"><span data-stu-id="932eb-153">-Exclude</span></span>

<span data-ttu-id="932eb-154">以字串陣列指定此 Cmdlet 在作業中排除的項目。</span><span class="sxs-lookup"><span data-stu-id="932eb-154">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="932eb-155">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="932eb-155">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="932eb-156">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="932eb-156">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="932eb-157">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="932eb-157">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="932eb-158">-Filter</span><span class="sxs-lookup"><span data-stu-id="932eb-158">-Filter</span></span>

<span data-ttu-id="932eb-159">以提供者的格式或語言指定篩選。</span><span class="sxs-lookup"><span data-stu-id="932eb-159">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="932eb-160">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="932eb-160">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="932eb-161">篩選的語法 (包括是否使用萬用字元) 取決於提供者。</span><span class="sxs-lookup"><span data-stu-id="932eb-161">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="932eb-162">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="932eb-162">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="932eb-163">-Force</span><span class="sxs-lookup"><span data-stu-id="932eb-163">-Force</span></span>

<span data-ttu-id="932eb-164">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="932eb-164">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="932eb-165">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="932eb-165">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="932eb-166">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="932eb-166">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="932eb-167">-Include</span><span class="sxs-lookup"><span data-stu-id="932eb-167">-Include</span></span>

<span data-ttu-id="932eb-168">以字串陣列指定此 Cmdlet 在作業中移動的專案或專案。</span><span class="sxs-lookup"><span data-stu-id="932eb-168">Specifies, as a string array, an item or items that this cmdlet moves in the operation.</span></span>
<span data-ttu-id="932eb-169">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="932eb-169">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="932eb-170">輸入路徑元素或模式，例如 "\*.txt"。</span><span class="sxs-lookup"><span data-stu-id="932eb-170">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="932eb-171">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="932eb-171">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="932eb-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="932eb-172">-LiteralPath</span></span>

<span data-ttu-id="932eb-173">指定項目之目前位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="932eb-173">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="932eb-174">與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="932eb-174">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="932eb-175">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="932eb-175">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="932eb-176">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="932eb-176">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="932eb-177">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="932eb-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="932eb-178">-PassThru</span><span class="sxs-lookup"><span data-stu-id="932eb-178">-PassThru</span></span>

<span data-ttu-id="932eb-179">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="932eb-179">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="932eb-180">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="932eb-180">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="932eb-181">-Path</span><span class="sxs-lookup"><span data-stu-id="932eb-181">-Path</span></span>

<span data-ttu-id="932eb-182">指定項目之目前位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="932eb-182">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="932eb-183">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="932eb-183">The default is the current directory.</span></span>
<span data-ttu-id="932eb-184">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="932eb-184">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="932eb-185">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="932eb-185">-UseTransaction</span></span>

<span data-ttu-id="932eb-186">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="932eb-186">Includes the command in the active transaction.</span></span>
<span data-ttu-id="932eb-187">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="932eb-187">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="932eb-188">如需詳細資訊，請參閱 about_Transactions。</span><span class="sxs-lookup"><span data-stu-id="932eb-188">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="932eb-189">-Confirm</span><span class="sxs-lookup"><span data-stu-id="932eb-189">-Confirm</span></span>

<span data-ttu-id="932eb-190">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="932eb-190">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="932eb-191">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="932eb-191">-WhatIf</span></span>

<span data-ttu-id="932eb-192">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="932eb-192">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="932eb-193">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="932eb-193">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="932eb-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="932eb-194">CommonParameters</span></span>

<span data-ttu-id="932eb-195">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="932eb-195">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="932eb-196">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="932eb-196">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="932eb-197">輸入</span><span class="sxs-lookup"><span data-stu-id="932eb-197">INPUTS</span></span>

### <span data-ttu-id="932eb-198">System.String</span><span class="sxs-lookup"><span data-stu-id="932eb-198">System.String</span></span>

<span data-ttu-id="932eb-199">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="932eb-199">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="932eb-200">輸出</span><span class="sxs-lookup"><span data-stu-id="932eb-200">OUTPUTS</span></span>

### <span data-ttu-id="932eb-201">無或表示已移動項目的物件。</span><span class="sxs-lookup"><span data-stu-id="932eb-201">None or an object representing the moved item.</span></span>

<span data-ttu-id="932eb-202">當您使用 *PassThru* 參數時，此 Cmdlet 會產生代表已移動之專案的物件。</span><span class="sxs-lookup"><span data-stu-id="932eb-202">When you use the *PassThru* parameter, this cmdlet generates an object representing the moved item.</span></span>
<span data-ttu-id="932eb-203">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="932eb-203">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="932eb-204">注意</span><span class="sxs-lookup"><span data-stu-id="932eb-204">NOTES</span></span>

<span data-ttu-id="932eb-205">此 Cmdlet 會在相同提供者所支援的磁片磁碟機之間移動檔案，但它只會在同一個磁片磁碟機內移動目錄。</span><span class="sxs-lookup"><span data-stu-id="932eb-205">This cmdlet will move files between drives that are supported by the same provider, but it will move directories only within the same drive.</span></span>

<span data-ttu-id="932eb-206">由於 `Move-Item` 命令會移動專案的屬性、內容及子專案，因此所有移動預設都是遞迴的。</span><span class="sxs-lookup"><span data-stu-id="932eb-206">Because a `Move-Item` command moves the properties, contents, and child items of an item, all moves are recursive by default.</span></span>

<span data-ttu-id="932eb-207">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="932eb-207">This cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="932eb-208">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="932eb-208">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="932eb-209">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="932eb-209">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="932eb-210">相關連結</span><span class="sxs-lookup"><span data-stu-id="932eb-210">RELATED LINKS</span></span>

[<span data-ttu-id="932eb-211">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="932eb-211">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="932eb-212">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="932eb-212">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="932eb-213">Get-Item</span><span class="sxs-lookup"><span data-stu-id="932eb-213">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="932eb-214">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="932eb-214">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="932eb-215">New-Item</span><span class="sxs-lookup"><span data-stu-id="932eb-215">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="932eb-216">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="932eb-216">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="932eb-217">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="932eb-217">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="932eb-218">Set-Item</span><span class="sxs-lookup"><span data-stu-id="932eb-218">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="932eb-219">about_Providers</span><span class="sxs-lookup"><span data-stu-id="932eb-219">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)