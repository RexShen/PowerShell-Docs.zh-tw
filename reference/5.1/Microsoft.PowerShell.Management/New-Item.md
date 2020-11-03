---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: b1657d369d44d575ee7bed8b76d36224ea2748f2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203595"
---
# <span data-ttu-id="90ea4-103">New-Item</span><span class="sxs-lookup"><span data-stu-id="90ea4-103">New-Item</span></span>

## <span data-ttu-id="90ea4-104">概要</span><span class="sxs-lookup"><span data-stu-id="90ea4-104">SYNOPSIS</span></span>
<span data-ttu-id="90ea4-105">建立新的項目。</span><span class="sxs-lookup"><span data-stu-id="90ea4-105">Creates a new item.</span></span>

## <span data-ttu-id="90ea4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="90ea4-106">SYNTAX</span></span>

### <span data-ttu-id="90ea4-107">pathSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="90ea4-107">pathSet (Default)</span></span>

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="90ea4-108">nameSet</span><span class="sxs-lookup"><span data-stu-id="90ea4-108">nameSet</span></span>

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="90ea4-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="90ea4-109">DESCRIPTION</span></span>

<span data-ttu-id="90ea4-110">此 `New-Item` Cmdlet 會建立新的專案，並設定其值。</span><span class="sxs-lookup"><span data-stu-id="90ea4-110">The `New-Item` cmdlet creates a new item and sets its value.</span></span> <span data-ttu-id="90ea4-111">可以建立的專案類型取決於專案的位置。</span><span class="sxs-lookup"><span data-stu-id="90ea4-111">The types of items that can be created depend on the location of the item.</span></span> <span data-ttu-id="90ea4-112">例如，在檔案系統中， `New-Item` 建立檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="90ea4-112">For example, in the file system, `New-Item` creates files and folders.</span></span> <span data-ttu-id="90ea4-113">在登錄中， `New-Item` 建立登錄機碼和專案。</span><span class="sxs-lookup"><span data-stu-id="90ea4-113">In the registry, `New-Item` creates registry keys and entries.</span></span>

<span data-ttu-id="90ea4-114">`New-Item` 也可以設定它所建立之專案的值。</span><span class="sxs-lookup"><span data-stu-id="90ea4-114">`New-Item` can also set the value of the items that it creates.</span></span> <span data-ttu-id="90ea4-115">例如，在建立新檔案時， `New-Item` 可以將初始內容新增至檔案。</span><span class="sxs-lookup"><span data-stu-id="90ea4-115">For example, when it creates a new file, `New-Item` can add initial content to the file.</span></span>

## <span data-ttu-id="90ea4-116">範例</span><span class="sxs-lookup"><span data-stu-id="90ea4-116">EXAMPLES</span></span>

### <span data-ttu-id="90ea4-117">範例1：在目前的目錄中建立檔案</span><span class="sxs-lookup"><span data-stu-id="90ea4-117">Example 1: Create a file in the current directory</span></span>

<span data-ttu-id="90ea4-118">此命令會在目前的目錄中建立名為 "testfile1.txt" 的文字檔。</span><span class="sxs-lookup"><span data-stu-id="90ea4-118">This command creates a text file that is named "testfile1.txt" in the current directory.</span></span> <span data-ttu-id="90ea4-119">點 ( '. ' **Path** 參數值中的 ) 表示目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="90ea4-119">The dot ('.') in the value of the **Path** parameter indicates the current directory.</span></span> <span data-ttu-id="90ea4-120">在 **Value** 參數後面加上引號的文字會加入檔案中作為內容。</span><span class="sxs-lookup"><span data-stu-id="90ea4-120">The quoted text that follows the **Value** parameter is added to the file as content.</span></span>

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### <span data-ttu-id="90ea4-121">範例2：建立目錄</span><span class="sxs-lookup"><span data-stu-id="90ea4-121">Example 2: Create a directory</span></span>

<span data-ttu-id="90ea4-122">此命令會在磁片磁碟機中建立名為「日誌」的目錄 `C:` 。</span><span class="sxs-lookup"><span data-stu-id="90ea4-122">This command creates a directory named "Logfiles" in the `C:` drive.</span></span> <span data-ttu-id="90ea4-123">**ItemType** 參數會指定新專案為目錄，而不是檔案或其他檔案系統物件。</span><span class="sxs-lookup"><span data-stu-id="90ea4-123">The **ItemType** parameter specifies that the new item is a directory, not a file or other file system object.</span></span>

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### <span data-ttu-id="90ea4-124">範例3：建立設定檔</span><span class="sxs-lookup"><span data-stu-id="90ea4-124">Example 3: Create a profile</span></span>

<span data-ttu-id="90ea4-125">此命令會在變數所指定的路徑中建立 PowerShell 設定檔 `$profile` 。</span><span class="sxs-lookup"><span data-stu-id="90ea4-125">This command creates a PowerShell profile in the path that is specified by the `$profile` variable.</span></span>

<span data-ttu-id="90ea4-126">您可以使用設定檔來自訂 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="90ea4-126">You can use profiles to customize PowerShell.</span></span> <span data-ttu-id="90ea4-127">`$profile` 是自動 (內建的) 變數，可儲存 "CurrentUser/CurrentHost" 設定檔的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="90ea4-127">`$profile` is an automatic (built-in) variable that stores the path and file name of the "CurrentUser/CurrentHost" profile.</span></span> <span data-ttu-id="90ea4-128">根據預設，設定檔並不存在，即使 PowerShell 會儲存它的路徑和檔案名也一樣。</span><span class="sxs-lookup"><span data-stu-id="90ea4-128">By default, the profile does not exist, even though PowerShell stores a path and file name for it.</span></span>

<span data-ttu-id="90ea4-129">在這個命令中， `$profile` 變數代表檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="90ea4-129">In this command, the `$profile` variable represents the path of the file.</span></span> <span data-ttu-id="90ea4-130">**ItemType** 參數會指定命令建立檔案。</span><span class="sxs-lookup"><span data-stu-id="90ea4-130">**ItemType** parameter specifies that the command creates a file.</span></span> <span data-ttu-id="90ea4-131">**Force** 參數可讓您在設定檔路徑中建立檔案，即使路徑中的目錄不存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="90ea4-131">The **Force** parameter lets you create a file in the profile path, even when the directories in the path do not exist.</span></span>

<span data-ttu-id="90ea4-132">建立設定檔之後，您可以在設定檔中輸入別名、函式和腳本來自訂您的 shell。</span><span class="sxs-lookup"><span data-stu-id="90ea4-132">After you create a profile, you can enter aliases, functions, and scripts in the profile to customize your shell.</span></span>

<span data-ttu-id="90ea4-133">如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) 和 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="90ea4-133">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) and [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

> [!NOTE]
> <span data-ttu-id="90ea4-134">當您使用這個方法建立檔案時，產生的檔案會編碼為 UTF-8，而不會有位元組順序標記 (BOM) 。</span><span class="sxs-lookup"><span data-stu-id="90ea4-134">When you create a file using this method, the resulting file is encoded as UTF-8 without a byte-order-mark (BOM).</span></span>

### <span data-ttu-id="90ea4-135">範例4：在不同的目錄中建立目錄</span><span class="sxs-lookup"><span data-stu-id="90ea4-135">Example 4: Create a directory in a different directory</span></span>

<span data-ttu-id="90ea4-136">此範例會在 "C:\PS-Test" 目錄中建立新的腳本目錄。</span><span class="sxs-lookup"><span data-stu-id="90ea4-136">This example creates a new Scripts directory in the "C:\PS-Test" directory.</span></span>

<span data-ttu-id="90ea4-137">新目錄專案的名稱 "script" 會包含在 **Path** 參數的值中，而不是在 **name** 的值中指定。</span><span class="sxs-lookup"><span data-stu-id="90ea4-137">The name of the new directory item, "Scripts", is included in the value of **Path** parameter, instead of being specified in the value of **Name** .</span></span> <span data-ttu-id="90ea4-138">如語法所指示，任何一個命令格式都是有效的。</span><span class="sxs-lookup"><span data-stu-id="90ea4-138">As indicated by the syntax, either command form is valid.</span></span>

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### <span data-ttu-id="90ea4-139">範例5：建立多個檔案</span><span class="sxs-lookup"><span data-stu-id="90ea4-139">Example 5: Create multiple files</span></span>

<span data-ttu-id="90ea4-140">此範例會在兩個不同的目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="90ea4-140">This example creates files in two different directories.</span></span> <span data-ttu-id="90ea4-141">因為 **Path** 接受多個字串，所以您可以使用它來建立多個專案。</span><span class="sxs-lookup"><span data-stu-id="90ea4-141">Because **Path** takes multiple strings, you can use it to create multiple items.</span></span>

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### <span data-ttu-id="90ea4-142">範例6：使用-Force 參數嘗試重新建立資料夾</span><span class="sxs-lookup"><span data-stu-id="90ea4-142">Example 6: Use the -Force parameter to attempt to recreate folders</span></span>

<span data-ttu-id="90ea4-143">這個範例會建立一個資料夾，其中包含內的檔案。</span><span class="sxs-lookup"><span data-stu-id="90ea4-143">This example creates a folder with a file inside.</span></span> <span data-ttu-id="90ea4-144">然後，嘗試使用建立相同的資料夾 `-Force` 。</span><span class="sxs-lookup"><span data-stu-id="90ea4-144">Then, attempts to create the same folder using `-Force`.</span></span> <span data-ttu-id="90ea4-145">它不會覆寫資料夾，只會傳回現有的資料夾物件，並建立不完整的檔案。</span><span class="sxs-lookup"><span data-stu-id="90ea4-145">It will not overwrite the folder but simply return the existing folder object with the file created intact.</span></span>

```powershell
PS> New-Item -Path .\TestFolder -ItemType Directory
PS> New-Item -Path .\TestFolder\TestFile.txt -ItemType File

PS> New-Item -Path .\TestFolder -ItemType Directory -Force

    Directory: C:\
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         5/1/2020   8:03 AM                TestFolder

PS> Get-ChildItem .\TestFolder\

    Directory: C:\TestFolder
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:03 AM              0 TestFile.txt
```

### <span data-ttu-id="90ea4-146">範例7：使用-Force 參數來覆寫現有的檔案</span><span class="sxs-lookup"><span data-stu-id="90ea4-146">Example 7: Use the -Force parameter to overwrite existing files</span></span>

<span data-ttu-id="90ea4-147">這個範例會建立具有值的檔案，然後使用重新建立檔案 `-Force` 。</span><span class="sxs-lookup"><span data-stu-id="90ea4-147">This example creates a file with a value and then recreates the file using `-Force`.</span></span> <span data-ttu-id="90ea4-148">這會覆寫現有的檔案，而其內容將會遺失，因為 length 屬性可以看到它。</span><span class="sxs-lookup"><span data-stu-id="90ea4-148">This overwrites The existing file and it will lose it's content as you can see by the length property</span></span>

```powershell
PS> New-Item ./TestFile.txt -ItemType File -Value 'This is just a test file'

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM             24 TestFile.txt

New-Item ./TestFile.txt -ItemType File -Force

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM              0 TestFile.txt
```

> [!NOTE]
> <span data-ttu-id="90ea4-149">搭配使用 `New-Item` 參數與 `-Force` 參數來建立登錄機碼時，命令的行為會與覆寫檔案時相同。</span><span class="sxs-lookup"><span data-stu-id="90ea4-149">When using `New-Item` with the `-Force` switch to create registry keys, the command will behave the same as when overwriting a file.</span></span> <span data-ttu-id="90ea4-150">如果登錄機碼已經存在，則會以空白的登錄機碼覆寫機碼和所有屬性和值。</span><span class="sxs-lookup"><span data-stu-id="90ea4-150">If the registry key already exists, the key and all properties and values will be overwritten with an empty registry key.</span></span>

## <span data-ttu-id="90ea4-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="90ea4-151">PARAMETERS</span></span>

### <span data-ttu-id="90ea4-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="90ea4-152">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="90ea4-153">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="90ea4-153">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="90ea4-154">若要在執行這個 Cmdlet 時模擬另一位使用者或提升您的認證，請使用 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="90ea4-154">To impersonate another user or elevate your credentials when running this cmdlet, use `Invoke-Command`.</span></span>

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

### <span data-ttu-id="90ea4-155">-Force</span><span class="sxs-lookup"><span data-stu-id="90ea4-155">-Force</span></span>

<span data-ttu-id="90ea4-156">強制這個 Cmdlet 建立寫入現有唯讀專案的專案。</span><span class="sxs-lookup"><span data-stu-id="90ea4-156">Forces this cmdlet to create an item that writes over an existing read-only item.</span></span> <span data-ttu-id="90ea4-157">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="90ea4-157">Implementation varies from provider to provider.</span></span> <span data-ttu-id="90ea4-158">即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="90ea4-158">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="90ea4-159">-ItemType</span><span class="sxs-lookup"><span data-stu-id="90ea4-159">-ItemType</span></span>

<span data-ttu-id="90ea4-160">指定新項目的提供者指定類型。</span><span class="sxs-lookup"><span data-stu-id="90ea4-160">Specifies the provider-specified type of the new item.</span></span> <span data-ttu-id="90ea4-161">此參數的可用值取決於您目前使用的提供者。</span><span class="sxs-lookup"><span data-stu-id="90ea4-161">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="90ea4-162">如果您的位置位於 `FileSystem` 磁片磁碟機中，則允許下列值：</span><span class="sxs-lookup"><span data-stu-id="90ea4-162">If your location is in a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="90ea4-163">檔案</span><span class="sxs-lookup"><span data-stu-id="90ea4-163">File</span></span>
- <span data-ttu-id="90ea4-164">目錄</span><span class="sxs-lookup"><span data-stu-id="90ea4-164">Directory</span></span>
- <span data-ttu-id="90ea4-165">>symboliclink</span><span class="sxs-lookup"><span data-stu-id="90ea4-165">SymbolicLink</span></span>
- <span data-ttu-id="90ea4-166">接合</span><span class="sxs-lookup"><span data-stu-id="90ea4-166">Junction</span></span>
- <span data-ttu-id="90ea4-167">硬</span><span class="sxs-lookup"><span data-stu-id="90ea4-167">HardLink</span></span>

<span data-ttu-id="90ea4-168">當您使用這個方法建立檔案時，產生的檔案會編碼為 UTF-8，而不會有位元組順序標記 (BOM) 。</span><span class="sxs-lookup"><span data-stu-id="90ea4-168">When you create a file using this method, the resulting file is encoded as UTF-8 without a byte-order-mark (BOM).</span></span>

<span data-ttu-id="90ea4-169">在 `Certificate` 磁片磁碟機中，這些是您可以指定的值：</span><span class="sxs-lookup"><span data-stu-id="90ea4-169">In a `Certificate` drive, these are the values you can specify:</span></span>

- <span data-ttu-id="90ea4-170">憑證提供者</span><span class="sxs-lookup"><span data-stu-id="90ea4-170">Certificate Provider</span></span>
- <span data-ttu-id="90ea4-171">憑證</span><span class="sxs-lookup"><span data-stu-id="90ea4-171">Certificate</span></span>
- <span data-ttu-id="90ea4-172">市集</span><span class="sxs-lookup"><span data-stu-id="90ea4-172">Store</span></span>
- <span data-ttu-id="90ea4-173">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="90ea4-173">StoreLocation</span></span>

<span data-ttu-id="90ea4-174">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="90ea4-174">For more information see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="90ea4-175">-Name</span><span class="sxs-lookup"><span data-stu-id="90ea4-175">-Name</span></span>

<span data-ttu-id="90ea4-176">指定新項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="90ea4-176">Specifies the name of the new item.</span></span> <span data-ttu-id="90ea4-177">您可以在 [ **名稱** ] 或 [ **路徑** ] 參數值中指定新專案的名稱，也可以在 [ **名稱** ] 或 [ **路徑** ] 值中指定新專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="90ea4-177">You can specify the name of the new item in the **Name** or **Path** parameter value, and you can specify the path of the new item in **Name** or **Path** value.</span></span> <span data-ttu-id="90ea4-178">使用 **Name** 參數傳遞的專案名稱會與 **Path** 參數的值相對應。</span><span class="sxs-lookup"><span data-stu-id="90ea4-178">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: nameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="90ea4-179">-Path</span><span class="sxs-lookup"><span data-stu-id="90ea4-179">-Path</span></span>

<span data-ttu-id="90ea4-180">指定新專案的位置路徑。</span><span class="sxs-lookup"><span data-stu-id="90ea4-180">Specifies the path of the location of the new item.</span></span> <span data-ttu-id="90ea4-181">當省略 **路徑** 時，預設值為目前的位置。</span><span class="sxs-lookup"><span data-stu-id="90ea4-181">The default is the current location when **Path** is omitted.</span></span> <span data-ttu-id="90ea4-182">您可以在 [ **名稱** ] 中指定新專案的名稱，或將它包含在 **Path** 中。</span><span class="sxs-lookup"><span data-stu-id="90ea4-182">You can specify the name of the new item in **Name** , or include it in **Path** .</span></span> <span data-ttu-id="90ea4-183">使用 **Name** 參數傳遞的專案名稱會與 **Path** 參數的值相對應。</span><span class="sxs-lookup"><span data-stu-id="90ea4-183">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

<span data-ttu-id="90ea4-184">針對此 Cmdlet， **Path** 參數的運作方式就像其他 Cmdlet 的 **LiteralPath** 參數。</span><span class="sxs-lookup"><span data-stu-id="90ea4-184">For this cmdlet, the **Path** parameter works like the **LiteralPath** parameter of other cmdlets.</span></span>
<span data-ttu-id="90ea4-185">萬用字元不會被解讀。</span><span class="sxs-lookup"><span data-stu-id="90ea4-185">Wildcard characters are not interpreted.</span></span> <span data-ttu-id="90ea4-186">所有字元都會傳遞至位置的提供者。</span><span class="sxs-lookup"><span data-stu-id="90ea4-186">All characters are passed to the location's provider.</span></span> <span data-ttu-id="90ea4-187">提供者可能不支援所有字元。</span><span class="sxs-lookup"><span data-stu-id="90ea4-187">The provider may not support all characters.</span></span> <span data-ttu-id="90ea4-188">例如，您無法建立包含星號 (`*`) 字元的檔案名。</span><span class="sxs-lookup"><span data-stu-id="90ea4-188">For example, you cannot create a filename that contains an asterisk (`*`) character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: pathSet, nameSet
Aliases:

Required: True (pathSet), False (nameSet)
Position: 0
Default value: Current location
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="90ea4-189">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="90ea4-189">-UseTransaction</span></span>

<span data-ttu-id="90ea4-190">將命令加入使用中交易。</span><span class="sxs-lookup"><span data-stu-id="90ea4-190">Includes the command in the active transaction.</span></span> <span data-ttu-id="90ea4-191">只有交易為處理中狀態時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="90ea4-191">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="90ea4-192">如需詳細資訊，請參閱 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="90ea4-192">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="90ea4-193">-Value</span><span class="sxs-lookup"><span data-stu-id="90ea4-193">-Value</span></span>

<span data-ttu-id="90ea4-194">指定新項目的值。</span><span class="sxs-lookup"><span data-stu-id="90ea4-194">Specifies the value of the new item.</span></span> <span data-ttu-id="90ea4-195">您也可以使用管線將值傳送至 `New-Item` 。</span><span class="sxs-lookup"><span data-stu-id="90ea4-195">You can also pipe a value to `New-Item`.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Target

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="90ea4-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="90ea4-196">-Confirm</span></span>

<span data-ttu-id="90ea4-197">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="90ea4-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="90ea4-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="90ea4-198">-WhatIf</span></span>

<span data-ttu-id="90ea4-199">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="90ea4-199">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="90ea4-200">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="90ea4-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="90ea4-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="90ea4-201">CommonParameters</span></span>

<span data-ttu-id="90ea4-202">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="90ea4-202">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="90ea4-203">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="90ea4-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="90ea4-204">輸入</span><span class="sxs-lookup"><span data-stu-id="90ea4-204">INPUTS</span></span>

### <span data-ttu-id="90ea4-205">System.Object</span><span class="sxs-lookup"><span data-stu-id="90ea4-205">System.Object</span></span>

<span data-ttu-id="90ea4-206">您可以使用管線將新專案的值傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90ea4-206">You can pipe a value for the new item to this cmdlet.</span></span>

## <span data-ttu-id="90ea4-207">輸出</span><span class="sxs-lookup"><span data-stu-id="90ea4-207">OUTPUTS</span></span>

### <span data-ttu-id="90ea4-208">System.Object</span><span class="sxs-lookup"><span data-stu-id="90ea4-208">System.Object</span></span>

<span data-ttu-id="90ea4-209">這個 Cmdlet 會傳回它所建立的專案。</span><span class="sxs-lookup"><span data-stu-id="90ea4-209">This cmdlet returns the item that it creates.</span></span>

## <span data-ttu-id="90ea4-210">注意</span><span class="sxs-lookup"><span data-stu-id="90ea4-210">NOTES</span></span>

<span data-ttu-id="90ea4-211">`New-Item` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="90ea4-211">`New-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="90ea4-212">若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="90ea4-212">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="90ea4-213">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="90ea4-213">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="90ea4-214">相關連結</span><span class="sxs-lookup"><span data-stu-id="90ea4-214">RELATED LINKS</span></span>

[<span data-ttu-id="90ea4-215">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="90ea4-215">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="90ea4-216">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="90ea4-216">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="90ea4-217">Get-Item</span><span class="sxs-lookup"><span data-stu-id="90ea4-217">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="90ea4-218">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="90ea4-218">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="90ea4-219">Move-Item</span><span class="sxs-lookup"><span data-stu-id="90ea4-219">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="90ea4-220">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="90ea4-220">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="90ea4-221">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="90ea4-221">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="90ea4-222">Set-Item</span><span class="sxs-lookup"><span data-stu-id="90ea4-222">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="90ea4-223">about_Providers</span><span class="sxs-lookup"><span data-stu-id="90ea4-223">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
