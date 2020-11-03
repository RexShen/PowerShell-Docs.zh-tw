---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: f24988833faaf56395b95e08430bbcc9fb6d2746
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201772"
---
# <span data-ttu-id="9d993-103">New-Item</span><span class="sxs-lookup"><span data-stu-id="9d993-103">New-Item</span></span>

## <span data-ttu-id="9d993-104">概要</span><span class="sxs-lookup"><span data-stu-id="9d993-104">SYNOPSIS</span></span>
<span data-ttu-id="9d993-105">建立新的項目。</span><span class="sxs-lookup"><span data-stu-id="9d993-105">Creates a new item.</span></span>

## <span data-ttu-id="9d993-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9d993-106">SYNTAX</span></span>

### <span data-ttu-id="9d993-107">pathSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="9d993-107">pathSet (Default)</span></span>

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9d993-108">nameSet</span><span class="sxs-lookup"><span data-stu-id="9d993-108">nameSet</span></span>

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9d993-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9d993-109">DESCRIPTION</span></span>

<span data-ttu-id="9d993-110">此 `New-Item` Cmdlet 會建立新的專案，並設定其值。</span><span class="sxs-lookup"><span data-stu-id="9d993-110">The `New-Item` cmdlet creates a new item and sets its value.</span></span> <span data-ttu-id="9d993-111">可以建立的專案類型取決於專案的位置。</span><span class="sxs-lookup"><span data-stu-id="9d993-111">The types of items that can be created depend on the location of the item.</span></span> <span data-ttu-id="9d993-112">例如，在檔案系統中， `New-Item` 建立檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="9d993-112">For example, in the file system, `New-Item` creates files and folders.</span></span> <span data-ttu-id="9d993-113">在登錄中， `New-Item` 建立登錄機碼和專案。</span><span class="sxs-lookup"><span data-stu-id="9d993-113">In the registry, `New-Item` creates registry keys and entries.</span></span>

<span data-ttu-id="9d993-114">`New-Item` 也可以設定它所建立之專案的值。</span><span class="sxs-lookup"><span data-stu-id="9d993-114">`New-Item` can also set the value of the items that it creates.</span></span> <span data-ttu-id="9d993-115">例如，在建立新檔案時， `New-Item` 可以將初始內容新增至檔案。</span><span class="sxs-lookup"><span data-stu-id="9d993-115">For example, when it creates a new file, `New-Item` can add initial content to the file.</span></span>

## <span data-ttu-id="9d993-116">範例</span><span class="sxs-lookup"><span data-stu-id="9d993-116">EXAMPLES</span></span>

### <span data-ttu-id="9d993-117">範例1：在目前的目錄中建立檔案</span><span class="sxs-lookup"><span data-stu-id="9d993-117">Example 1: Create a file in the current directory</span></span>

<span data-ttu-id="9d993-118">此命令會在目前的目錄中建立名為 "testfile1.txt" 的文字檔。</span><span class="sxs-lookup"><span data-stu-id="9d993-118">This command creates a text file that is named "testfile1.txt" in the current directory.</span></span> <span data-ttu-id="9d993-119">點 ( '. ' **Path** 參數值中的 ) 表示目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="9d993-119">The dot ('.') in the value of the **Path** parameter indicates the current directory.</span></span> <span data-ttu-id="9d993-120">在 **Value** 參數後面加上引號的文字會加入檔案中作為內容。</span><span class="sxs-lookup"><span data-stu-id="9d993-120">The quoted text that follows the **Value** parameter is added to the file as content.</span></span>

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### <span data-ttu-id="9d993-121">範例2：建立目錄</span><span class="sxs-lookup"><span data-stu-id="9d993-121">Example 2: Create a directory</span></span>

<span data-ttu-id="9d993-122">此命令會在磁片磁碟機中建立名為「日誌」的目錄 `C:` 。</span><span class="sxs-lookup"><span data-stu-id="9d993-122">This command creates a directory named "Logfiles" in the `C:` drive.</span></span> <span data-ttu-id="9d993-123">**ItemType** 參數會指定新專案為目錄，而不是檔案或其他檔案系統物件。</span><span class="sxs-lookup"><span data-stu-id="9d993-123">The **ItemType** parameter specifies that the new item is a directory, not a file or other file system object.</span></span>

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### <span data-ttu-id="9d993-124">範例3：建立設定檔</span><span class="sxs-lookup"><span data-stu-id="9d993-124">Example 3: Create a profile</span></span>

<span data-ttu-id="9d993-125">此命令會在變數所指定的路徑中建立 PowerShell 設定檔 `$profile` 。</span><span class="sxs-lookup"><span data-stu-id="9d993-125">This command creates a PowerShell profile in the path that is specified by the `$profile` variable.</span></span>

<span data-ttu-id="9d993-126">您可以使用設定檔來自訂 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9d993-126">You can use profiles to customize PowerShell.</span></span> <span data-ttu-id="9d993-127">`$profile` 是自動 (內建的) 變數，可儲存 "CurrentUser/CurrentHost" 設定檔的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="9d993-127">`$profile` is an automatic (built-in) variable that stores the path and file name of the "CurrentUser/CurrentHost" profile.</span></span> <span data-ttu-id="9d993-128">根據預設，設定檔並不存在，即使 PowerShell 會儲存它的路徑和檔案名也一樣。</span><span class="sxs-lookup"><span data-stu-id="9d993-128">By default, the profile does not exist, even though PowerShell stores a path and file name for it.</span></span>

<span data-ttu-id="9d993-129">在這個命令中， `$profile` 變數代表檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="9d993-129">In this command, the `$profile` variable represents the path of the file.</span></span> <span data-ttu-id="9d993-130">**ItemType** 參數會指定命令建立檔案。</span><span class="sxs-lookup"><span data-stu-id="9d993-130">**ItemType** parameter specifies that the command creates a file.</span></span> <span data-ttu-id="9d993-131">**Force** 參數可讓您在設定檔路徑中建立檔案，即使路徑中的目錄不存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="9d993-131">The **Force** parameter lets you create a file in the profile path, even when the directories in the path do not exist.</span></span>

<span data-ttu-id="9d993-132">建立設定檔之後，您可以在設定檔中輸入別名、函式和腳本來自訂您的 shell。</span><span class="sxs-lookup"><span data-stu-id="9d993-132">After you create a profile, you can enter aliases, functions, and scripts in the profile to customize your shell.</span></span>

<span data-ttu-id="9d993-133">如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) 和 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="9d993-133">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) and [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

### <span data-ttu-id="9d993-134">範例4：在不同的目錄中建立目錄</span><span class="sxs-lookup"><span data-stu-id="9d993-134">Example 4: Create a directory in a different directory</span></span>

<span data-ttu-id="9d993-135">此範例會在 "C:\PS-Test" 目錄中建立新的腳本目錄。</span><span class="sxs-lookup"><span data-stu-id="9d993-135">This example creates a new Scripts directory in the "C:\PS-Test" directory.</span></span>

<span data-ttu-id="9d993-136">新目錄專案的名稱 "script" 會包含在 **Path** 參數的值中，而不是在 **name** 的值中指定。</span><span class="sxs-lookup"><span data-stu-id="9d993-136">The name of the new directory item, "Scripts", is included in the value of **Path** parameter, instead of being specified in the value of **Name** .</span></span> <span data-ttu-id="9d993-137">如語法所指示，任何一個命令格式都是有效的。</span><span class="sxs-lookup"><span data-stu-id="9d993-137">As indicated by the syntax, either command form is valid.</span></span>

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### <span data-ttu-id="9d993-138">範例5：建立多個檔案</span><span class="sxs-lookup"><span data-stu-id="9d993-138">Example 5: Create multiple files</span></span>

<span data-ttu-id="9d993-139">此範例會在兩個不同的目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="9d993-139">This example creates files in two different directories.</span></span> <span data-ttu-id="9d993-140">因為 **Path** 接受多個字串，所以您可以使用它來建立多個專案。</span><span class="sxs-lookup"><span data-stu-id="9d993-140">Because **Path** takes multiple strings, you can use it to create multiple items.</span></span>

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### <span data-ttu-id="9d993-141">範例6：使用萬用字元在多個目錄中建立檔案</span><span class="sxs-lookup"><span data-stu-id="9d993-141">Example 6: Use wildcards to create files in multiple directories</span></span>

<span data-ttu-id="9d993-142">此 `New-Item` Cmdlet 支援 **Path** 參數中的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9d993-142">The `New-Item` cmdlet supports wildcards in the **Path** parameter.</span></span> <span data-ttu-id="9d993-143">下列命令會 `temp.txt` 在 **Path** 參數中以萬用字元指定的所有目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="9d993-143">The following command creates a `temp.txt` file in all of the directories specified by the wildcards in the **Path** parameter.</span></span>

```powershell
Get-ChildItem -Path C:\Temp\
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d-----        5/15/2019   6:45 AM        1   One
d-----        5/15/2019   6:45 AM        1   Two
d-----        5/15/2019   6:45 AM        1   Three
```

```powershell
New-Item -Path * -Name temp.txt -ItemType File | Select-Object FullName
```

```Output
FullName
--------
C:\Temp\One\temp.txt
C:\Temp\Three\temp.txt
C:\Temp\Two\temp.txt
```

<span data-ttu-id="9d993-144">此 `Get-ChildItem` Cmdlet 會在目錄底下顯示三個目錄 `C:\Temp` 。</span><span class="sxs-lookup"><span data-stu-id="9d993-144">The `Get-ChildItem` cmdlet shows three directories under the `C:\Temp` directory.</span></span> <span data-ttu-id="9d993-145">使用萬用字元時， `New-Item` Cmdlet 會 `temp.txt` 在目前的目錄下的所有目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="9d993-145">Using wildcards the `New-Item` cmdlet creates a `temp.txt` file in all of the directories under the current directory.</span></span> <span data-ttu-id="9d993-146">此 `New-Item` Cmdlet 會輸出您建立的專案（以管線傳送至）， `Select-Object` 以確認新建立之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="9d993-146">The `New-Item` cmdlet outputs the items you created, which is piped to `Select-Object` to verify the paths of the newly created files.</span></span>

### <span data-ttu-id="9d993-147">範例7：建立檔案或資料夾的符號連結</span><span class="sxs-lookup"><span data-stu-id="9d993-147">Example 7: Create a symbolic link to a file or folder</span></span>

<span data-ttu-id="9d993-148">這個範例會在目前的資料夾中建立 Notice.txt 檔案的符號連結。</span><span class="sxs-lookup"><span data-stu-id="9d993-148">This example creates a symbolic link to the Notice.txt file in the current folder.</span></span>

```powershell
$link = New-Item -ItemType SymbolicLink -Path .\link -Target .\Notice.txt
$link | Select-Object LinkType, Target
```

```Output
LinkType     Target
--------     ------
SymbolicLink {.\Notice.txt}
```

<span data-ttu-id="9d993-149">在此範例中， **Target** 是 **Value** 參數的別名。</span><span class="sxs-lookup"><span data-stu-id="9d993-149">In this example, **Target** is an alias for the **Value** parameter.</span></span> <span data-ttu-id="9d993-150">符號連結的目標可以是相對路徑。</span><span class="sxs-lookup"><span data-stu-id="9d993-150">The target of the symbolic link can be a relative path.</span></span> <span data-ttu-id="9d993-151">在 PowerShell 6.2 之前，目標必須是完整路徑。</span><span class="sxs-lookup"><span data-stu-id="9d993-151">Prior to PowerShell v6.2, the target must be a fully-qualified path.</span></span>

> [!CAUTION]
> <span data-ttu-id="9d993-152">如果您要建立 **>symboliclink** 至 Windows 上的資料夾，您必須使用完整路徑。</span><span class="sxs-lookup"><span data-stu-id="9d993-152">If you are creating a **SymbolicLink** to a folder on Windows, you must use a fully-qualified path.</span></span> <span data-ttu-id="9d993-153">如果您使用相對路徑，則會將連結建立為檔案類型連結，而不是目錄類型的連結。</span><span class="sxs-lookup"><span data-stu-id="9d993-153">If you use a relative path, the link is created as a file-type link instead of a directory-type link.</span></span>

### <span data-ttu-id="9d993-154">範例8：使用-Force 參數嘗試重新建立資料夾</span><span class="sxs-lookup"><span data-stu-id="9d993-154">Example 8: Use the -Force parameter to attempt to recreate folders</span></span>

<span data-ttu-id="9d993-155">這個範例會建立一個資料夾，其中包含內的檔案。</span><span class="sxs-lookup"><span data-stu-id="9d993-155">This example creates a folder with a file inside.</span></span> <span data-ttu-id="9d993-156">然後，嘗試使用建立相同的資料夾 `-Force` 。</span><span class="sxs-lookup"><span data-stu-id="9d993-156">Then, attempts to create the same folder using `-Force`.</span></span> <span data-ttu-id="9d993-157">它不會覆寫資料夾，只會傳回現有的資料夾物件，並建立不完整的檔案。</span><span class="sxs-lookup"><span data-stu-id="9d993-157">It will not overwrite the folder but simply return the existing folder object with the file created intact.</span></span>

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

### <span data-ttu-id="9d993-158">範例9：使用-Force 參數來覆寫現有的檔案</span><span class="sxs-lookup"><span data-stu-id="9d993-158">Example 9: Use the -Force parameter to overwrite existing files</span></span>

<span data-ttu-id="9d993-159">這個範例會建立具有值的檔案，然後使用重新建立檔案 `-Force` 。</span><span class="sxs-lookup"><span data-stu-id="9d993-159">This example creates a file with a value and then recreates the file using `-Force`.</span></span> <span data-ttu-id="9d993-160">這會覆寫現有的檔案，而其內容將會遺失，因為 length 屬性可以看到它。</span><span class="sxs-lookup"><span data-stu-id="9d993-160">This overwrites The existing file and it will lose it's content as you can see by the length property</span></span>

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
> <span data-ttu-id="9d993-161">搭配使用 `New-Item` 參數與 `-Force` 參數來建立登錄機碼時，命令的行為會與覆寫檔案時相同。</span><span class="sxs-lookup"><span data-stu-id="9d993-161">When using `New-Item` with the `-Force` switch to create registry keys, the command will behave the same as when overwriting a file.</span></span> <span data-ttu-id="9d993-162">如果登錄機碼已經存在，則會以空白的登錄機碼覆寫機碼和所有屬性和值。</span><span class="sxs-lookup"><span data-stu-id="9d993-162">If the registry key already exists, the key and all properties and values will be overwritten with an empty registry key.</span></span>

## <span data-ttu-id="9d993-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9d993-163">PARAMETERS</span></span>

### <span data-ttu-id="9d993-164">-Credential</span><span class="sxs-lookup"><span data-stu-id="9d993-164">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="9d993-165">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="9d993-165">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="9d993-166">若要在執行這個 Cmdlet 時模擬另一位使用者或提升您的認證，請使用 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="9d993-166">To impersonate another user or elevate your credentials when running this cmdlet, use `Invoke-Command`.</span></span>

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

### <span data-ttu-id="9d993-167">-Force</span><span class="sxs-lookup"><span data-stu-id="9d993-167">-Force</span></span>

<span data-ttu-id="9d993-168">強制這個 Cmdlet 建立寫入現有唯讀專案的專案。</span><span class="sxs-lookup"><span data-stu-id="9d993-168">Forces this cmdlet to create an item that writes over an existing read-only item.</span></span> <span data-ttu-id="9d993-169">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="9d993-169">Implementation varies from provider to provider.</span></span> <span data-ttu-id="9d993-170">即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="9d993-170">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="9d993-171">-ItemType</span><span class="sxs-lookup"><span data-stu-id="9d993-171">-ItemType</span></span>

<span data-ttu-id="9d993-172">指定新項目的提供者指定類型。</span><span class="sxs-lookup"><span data-stu-id="9d993-172">Specifies the provider-specified type of the new item.</span></span> <span data-ttu-id="9d993-173">此參數的可用值取決於您目前使用的提供者。</span><span class="sxs-lookup"><span data-stu-id="9d993-173">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="9d993-174">如果您的位置位於 `FileSystem` 磁片磁碟機中，則允許下列值：</span><span class="sxs-lookup"><span data-stu-id="9d993-174">If your location is in a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="9d993-175">檔案</span><span class="sxs-lookup"><span data-stu-id="9d993-175">File</span></span>
- <span data-ttu-id="9d993-176">目錄</span><span class="sxs-lookup"><span data-stu-id="9d993-176">Directory</span></span>
- <span data-ttu-id="9d993-177">>symboliclink</span><span class="sxs-lookup"><span data-stu-id="9d993-177">SymbolicLink</span></span>
- <span data-ttu-id="9d993-178">接合</span><span class="sxs-lookup"><span data-stu-id="9d993-178">Junction</span></span>
- <span data-ttu-id="9d993-179">硬</span><span class="sxs-lookup"><span data-stu-id="9d993-179">HardLink</span></span>

> [!NOTE]
> <span data-ttu-id="9d993-180">`SymbolicLink`在 Windows 上建立類型需要以系統管理員的許可權提升許可權。</span><span class="sxs-lookup"><span data-stu-id="9d993-180">Creating a `SymbolicLink` type on Windows requires elevation as administrator.</span></span> <span data-ttu-id="9d993-181">不過，已啟用開發人員模式的 Windows 10 (組建14972或) 更新版本，不再需要提高建立符號連結的許可權。</span><span class="sxs-lookup"><span data-stu-id="9d993-181">However, Windows 10 (build 14972 or newer) with Developer Mode enabled no longer requires elevation creating symbolic links.</span></span>

<span data-ttu-id="9d993-182">在 `Certificate` 磁片磁碟機中，這些是您可以指定的值：</span><span class="sxs-lookup"><span data-stu-id="9d993-182">In a `Certificate` drive, these are the values you can specify:</span></span>

- <span data-ttu-id="9d993-183">憑證提供者</span><span class="sxs-lookup"><span data-stu-id="9d993-183">Certificate Provider</span></span>
- <span data-ttu-id="9d993-184">憑證</span><span class="sxs-lookup"><span data-stu-id="9d993-184">Certificate</span></span>
- <span data-ttu-id="9d993-185">市集</span><span class="sxs-lookup"><span data-stu-id="9d993-185">Store</span></span>
- <span data-ttu-id="9d993-186">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="9d993-186">StoreLocation</span></span>

<span data-ttu-id="9d993-187">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="9d993-187">For more information see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="9d993-188">-Name</span><span class="sxs-lookup"><span data-stu-id="9d993-188">-Name</span></span>

<span data-ttu-id="9d993-189">指定新項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="9d993-189">Specifies the name of the new item.</span></span> <span data-ttu-id="9d993-190">您可以在 [ **名稱** ] 或 [ **路徑** ] 參數值中指定新專案的名稱，也可以在 [ **名稱** ] 或 [ **路徑** ] 值中指定新專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="9d993-190">You can specify the name of the new item in the **Name** or **Path** parameter value, and you can specify the path of the new item in **Name** or **Path** value.</span></span> <span data-ttu-id="9d993-191">使用 **Name** 參數傳遞的專案名稱會與 **Path** 參數的值相對應。</span><span class="sxs-lookup"><span data-stu-id="9d993-191">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

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

### <span data-ttu-id="9d993-192">-Path</span><span class="sxs-lookup"><span data-stu-id="9d993-192">-Path</span></span>

<span data-ttu-id="9d993-193">指定新專案的位置路徑。</span><span class="sxs-lookup"><span data-stu-id="9d993-193">Specifies the path of the location of the new item.</span></span> <span data-ttu-id="9d993-194">當省略 **路徑** 時，預設值為目前的位置。</span><span class="sxs-lookup"><span data-stu-id="9d993-194">The default is the current location when **Path** is omitted.</span></span> <span data-ttu-id="9d993-195">您可以在 [ **名稱** ] 中指定新專案的名稱，或將它包含在 **Path** 中。</span><span class="sxs-lookup"><span data-stu-id="9d993-195">You can specify the name of the new item in **Name** , or include it in **Path** .</span></span> <span data-ttu-id="9d993-196">使用 **Name** 參數傳遞的專案名稱會與 **Path** 參數的值相對應。</span><span class="sxs-lookup"><span data-stu-id="9d993-196">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

<span data-ttu-id="9d993-197">針對此 Cmdlet， **Path** 參數的運作方式就像其他 Cmdlet 的 **LiteralPath** 參數。</span><span class="sxs-lookup"><span data-stu-id="9d993-197">For this cmdlet, the **Path** parameter works like the **LiteralPath** parameter of other cmdlets.</span></span>
<span data-ttu-id="9d993-198">萬用字元不會被解讀。</span><span class="sxs-lookup"><span data-stu-id="9d993-198">Wildcard characters are not interpreted.</span></span> <span data-ttu-id="9d993-199">所有字元都會傳遞至位置的提供者。</span><span class="sxs-lookup"><span data-stu-id="9d993-199">All characters are passed to the location's provider.</span></span> <span data-ttu-id="9d993-200">提供者可能不支援所有字元。</span><span class="sxs-lookup"><span data-stu-id="9d993-200">The provider may not support all characters.</span></span> <span data-ttu-id="9d993-201">例如，您無法建立包含星號 (`*`) 字元的檔案名。</span><span class="sxs-lookup"><span data-stu-id="9d993-201">For example, you cannot create a filename that contains an asterisk (`*`) character.</span></span>

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

### <span data-ttu-id="9d993-202">-Value</span><span class="sxs-lookup"><span data-stu-id="9d993-202">-Value</span></span>

<span data-ttu-id="9d993-203">指定新項目的值。</span><span class="sxs-lookup"><span data-stu-id="9d993-203">Specifies the value of the new item.</span></span> <span data-ttu-id="9d993-204">您也可以使用管線將值傳送至 `New-Item` 。</span><span class="sxs-lookup"><span data-stu-id="9d993-204">You can also pipe a value to `New-Item`.</span></span>

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

### <span data-ttu-id="9d993-205">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9d993-205">-Confirm</span></span>

<span data-ttu-id="9d993-206">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="9d993-206">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9d993-207">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9d993-207">-WhatIf</span></span>

<span data-ttu-id="9d993-208">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="9d993-208">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9d993-209">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="9d993-209">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9d993-210">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9d993-210">CommonParameters</span></span>

<span data-ttu-id="9d993-211">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="9d993-211">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="9d993-212">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="9d993-212">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9d993-213">輸入</span><span class="sxs-lookup"><span data-stu-id="9d993-213">INPUTS</span></span>

### <span data-ttu-id="9d993-214">System.Object</span><span class="sxs-lookup"><span data-stu-id="9d993-214">System.Object</span></span>

<span data-ttu-id="9d993-215">您可以使用管線將新專案的值傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9d993-215">You can pipe a value for the new item to this cmdlet.</span></span>

## <span data-ttu-id="9d993-216">輸出</span><span class="sxs-lookup"><span data-stu-id="9d993-216">OUTPUTS</span></span>

### <span data-ttu-id="9d993-217">System.Object</span><span class="sxs-lookup"><span data-stu-id="9d993-217">System.Object</span></span>

<span data-ttu-id="9d993-218">這個 Cmdlet 會傳回它所建立的專案。</span><span class="sxs-lookup"><span data-stu-id="9d993-218">This cmdlet returns the item that it creates.</span></span>

## <span data-ttu-id="9d993-219">注意</span><span class="sxs-lookup"><span data-stu-id="9d993-219">NOTES</span></span>

<span data-ttu-id="9d993-220">`New-Item` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="9d993-220">`New-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="9d993-221">若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="9d993-221">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="9d993-222">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="9d993-222">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="9d993-223">相關連結</span><span class="sxs-lookup"><span data-stu-id="9d993-223">RELATED LINKS</span></span>

[<span data-ttu-id="9d993-224">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="9d993-224">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="9d993-225">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="9d993-225">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="9d993-226">Get-Item</span><span class="sxs-lookup"><span data-stu-id="9d993-226">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="9d993-227">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="9d993-227">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="9d993-228">Move-Item</span><span class="sxs-lookup"><span data-stu-id="9d993-228">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="9d993-229">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="9d993-229">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="9d993-230">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="9d993-230">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="9d993-231">Set-Item</span><span class="sxs-lookup"><span data-stu-id="9d993-231">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="9d993-232">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9d993-232">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
