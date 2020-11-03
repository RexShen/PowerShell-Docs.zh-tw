---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: 50a7dba8c4e9cb1cfabd42f39e9fdfb43f22f9b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202088"
---
# <span data-ttu-id="ccdf5-103">New-Item</span><span class="sxs-lookup"><span data-stu-id="ccdf5-103">New-Item</span></span>

## <span data-ttu-id="ccdf5-104">概要</span><span class="sxs-lookup"><span data-stu-id="ccdf5-104">SYNOPSIS</span></span>
<span data-ttu-id="ccdf5-105">建立新的項目。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-105">Creates a new item.</span></span>

## <span data-ttu-id="ccdf5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ccdf5-106">SYNTAX</span></span>

### <span data-ttu-id="ccdf5-107">pathSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="ccdf5-107">pathSet (Default)</span></span>

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ccdf5-108">nameSet</span><span class="sxs-lookup"><span data-stu-id="ccdf5-108">nameSet</span></span>

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ccdf5-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ccdf5-109">DESCRIPTION</span></span>

<span data-ttu-id="ccdf5-110">此 `New-Item` Cmdlet 會建立新的專案，並設定其值。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-110">The `New-Item` cmdlet creates a new item and sets its value.</span></span> <span data-ttu-id="ccdf5-111">可以建立的專案類型取決於專案的位置。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-111">The types of items that can be created depend on the location of the item.</span></span> <span data-ttu-id="ccdf5-112">例如，在檔案系統中， `New-Item` 建立檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-112">For example, in the file system, `New-Item` creates files and folders.</span></span> <span data-ttu-id="ccdf5-113">在登錄中， `New-Item` 建立登錄機碼和專案。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-113">In the registry, `New-Item` creates registry keys and entries.</span></span>

<span data-ttu-id="ccdf5-114">`New-Item` 也可以設定它所建立之專案的值。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-114">`New-Item` can also set the value of the items that it creates.</span></span> <span data-ttu-id="ccdf5-115">例如，在建立新檔案時， `New-Item` 可以將初始內容新增至檔案。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-115">For example, when it creates a new file, `New-Item` can add initial content to the file.</span></span>

## <span data-ttu-id="ccdf5-116">範例</span><span class="sxs-lookup"><span data-stu-id="ccdf5-116">EXAMPLES</span></span>

### <span data-ttu-id="ccdf5-117">範例1：在目前的目錄中建立檔案</span><span class="sxs-lookup"><span data-stu-id="ccdf5-117">Example 1: Create a file in the current directory</span></span>

<span data-ttu-id="ccdf5-118">此命令會在目前的目錄中建立名為 "testfile1.txt" 的文字檔。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-118">This command creates a text file that is named "testfile1.txt" in the current directory.</span></span> <span data-ttu-id="ccdf5-119">點 ( '. ' **Path** 參數值中的 ) 表示目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-119">The dot ('.') in the value of the **Path** parameter indicates the current directory.</span></span> <span data-ttu-id="ccdf5-120">在 **Value** 參數後面加上引號的文字會加入檔案中作為內容。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-120">The quoted text that follows the **Value** parameter is added to the file as content.</span></span>

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### <span data-ttu-id="ccdf5-121">範例2：建立目錄</span><span class="sxs-lookup"><span data-stu-id="ccdf5-121">Example 2: Create a directory</span></span>

<span data-ttu-id="ccdf5-122">此命令會在磁片磁碟機中建立名為「日誌」的目錄 `C:` 。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-122">This command creates a directory named "Logfiles" in the `C:` drive.</span></span> <span data-ttu-id="ccdf5-123">**ItemType** 參數會指定新專案為目錄，而不是檔案或其他檔案系統物件。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-123">The **ItemType** parameter specifies that the new item is a directory, not a file or other file system object.</span></span>

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### <span data-ttu-id="ccdf5-124">範例3：建立設定檔</span><span class="sxs-lookup"><span data-stu-id="ccdf5-124">Example 3: Create a profile</span></span>

<span data-ttu-id="ccdf5-125">此命令會在變數所指定的路徑中建立 PowerShell 設定檔 `$profile` 。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-125">This command creates a PowerShell profile in the path that is specified by the `$profile` variable.</span></span>

<span data-ttu-id="ccdf5-126">您可以使用設定檔來自訂 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-126">You can use profiles to customize PowerShell.</span></span> <span data-ttu-id="ccdf5-127">`$profile` 是自動 (內建的) 變數，可儲存 "CurrentUser/CurrentHost" 設定檔的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-127">`$profile` is an automatic (built-in) variable that stores the path and file name of the "CurrentUser/CurrentHost" profile.</span></span> <span data-ttu-id="ccdf5-128">根據預設，設定檔並不存在，即使 PowerShell 會儲存它的路徑和檔案名也一樣。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-128">By default, the profile does not exist, even though PowerShell stores a path and file name for it.</span></span>

<span data-ttu-id="ccdf5-129">在這個命令中， `$profile` 變數代表檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-129">In this command, the `$profile` variable represents the path of the file.</span></span> <span data-ttu-id="ccdf5-130">**ItemType** 參數會指定命令建立檔案。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-130">**ItemType** parameter specifies that the command creates a file.</span></span> <span data-ttu-id="ccdf5-131">**Force** 參數可讓您在設定檔路徑中建立檔案，即使路徑中的目錄不存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-131">The **Force** parameter lets you create a file in the profile path, even when the directories in the path do not exist.</span></span>

<span data-ttu-id="ccdf5-132">建立設定檔之後，您可以在設定檔中輸入別名、函式和腳本來自訂您的 shell。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-132">After you create a profile, you can enter aliases, functions, and scripts in the profile to customize your shell.</span></span>

<span data-ttu-id="ccdf5-133">如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) 和 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-133">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) and [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

### <span data-ttu-id="ccdf5-134">範例4：在不同的目錄中建立目錄</span><span class="sxs-lookup"><span data-stu-id="ccdf5-134">Example 4: Create a directory in a different directory</span></span>

<span data-ttu-id="ccdf5-135">此範例會在 "C:\PS-Test" 目錄中建立新的腳本目錄。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-135">This example creates a new Scripts directory in the "C:\PS-Test" directory.</span></span>

<span data-ttu-id="ccdf5-136">新目錄專案的名稱 "script" 會包含在 **Path** 參數的值中，而不是在 **name** 的值中指定。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-136">The name of the new directory item, "Scripts", is included in the value of **Path** parameter, instead of being specified in the value of **Name** .</span></span> <span data-ttu-id="ccdf5-137">如語法所指示，任何一個命令格式都是有效的。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-137">As indicated by the syntax, either command form is valid.</span></span>

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### <span data-ttu-id="ccdf5-138">範例5：建立多個檔案</span><span class="sxs-lookup"><span data-stu-id="ccdf5-138">Example 5: Create multiple files</span></span>

<span data-ttu-id="ccdf5-139">此範例會在兩個不同的目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-139">This example creates files in two different directories.</span></span> <span data-ttu-id="ccdf5-140">因為 **Path** 接受多個字串，所以您可以使用它來建立多個專案。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-140">Because **Path** takes multiple strings, you can use it to create multiple items.</span></span>

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### <span data-ttu-id="ccdf5-141">範例6：使用萬用字元在多個目錄中建立檔案</span><span class="sxs-lookup"><span data-stu-id="ccdf5-141">Example 6: Use wildcards to create files in multiple directories</span></span>

<span data-ttu-id="ccdf5-142">此 `New-Item` Cmdlet 支援 **Path** 參數中的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-142">The `New-Item` cmdlet supports wildcards in the **Path** parameter.</span></span> <span data-ttu-id="ccdf5-143">下列命令會 `temp.txt` 在 **Path** 參數中以萬用字元指定的所有目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-143">The following command creates a `temp.txt` file in all of the directories specified by the wildcards in the **Path** parameter.</span></span>

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

<span data-ttu-id="ccdf5-144">此 `Get-ChildItem` Cmdlet 會在目錄底下顯示三個目錄 `C:\Temp` 。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-144">The `Get-ChildItem` cmdlet shows three directories under the `C:\Temp` directory.</span></span> <span data-ttu-id="ccdf5-145">使用萬用字元時， `New-Item` Cmdlet 會 `temp.txt` 在目前的目錄下的所有目錄中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-145">Using wildcards the `New-Item` cmdlet creates a `temp.txt` file in all of the directories under the current directory.</span></span> <span data-ttu-id="ccdf5-146">此 `New-Item` Cmdlet 會輸出您建立的專案（以管線傳送至）， `Select-Object` 以確認新建立之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-146">The `New-Item` cmdlet outputs the items you created, which is piped to `Select-Object` to verify the paths of the newly created files.</span></span>

### <span data-ttu-id="ccdf5-147">範例7：建立檔案或資料夾的符號連結</span><span class="sxs-lookup"><span data-stu-id="ccdf5-147">Example 7: Create a symbolic link to a file or folder</span></span>

<span data-ttu-id="ccdf5-148">這個範例會在目前的資料夾中建立 Notice.txt 檔案的符號連結。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-148">This example creates a symbolic link to the Notice.txt file in the current folder.</span></span>

```powershell
$link = New-Item -ItemType SymbolicLink -Path .\link -Target .\Notice.txt
$link | Select-Object LinkType, Target
```

```Output
LinkType     Target
--------     ------
SymbolicLink {.\Notice.txt}
```

<span data-ttu-id="ccdf5-149">在此範例中， **Target** 是 **Value** 參數的別名。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-149">In this example, **Target** is an alias for the **Value** parameter.</span></span> <span data-ttu-id="ccdf5-150">符號連結的目標可以是相對路徑。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-150">The target of the symbolic link can be a relative path.</span></span> <span data-ttu-id="ccdf5-151">在 PowerShell 6.2 之前，目標必須是完整路徑。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-151">Prior to PowerShell v6.2, the target must be a fully-qualified path.</span></span>

<span data-ttu-id="ccdf5-152">從 PowerShell 7.1 開始，您現在可以使用相對路徑建立 **>symboliclink** 至 Windows 上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-152">Beginning in PowerShell 7.1, you can now create to a **SymbolicLink** to a folder on Windows using a relative path.</span></span>

### <span data-ttu-id="ccdf5-153">範例8：使用-Force 參數嘗試重新建立資料夾</span><span class="sxs-lookup"><span data-stu-id="ccdf5-153">Example 8: Use the -Force parameter to attempt to recreate folders</span></span>

<span data-ttu-id="ccdf5-154">這個範例會建立一個資料夾，其中包含內的檔案。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-154">This example creates a folder with a file inside.</span></span> <span data-ttu-id="ccdf5-155">然後，嘗試使用建立相同的資料夾 `-Force` 。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-155">Then, attempts to create the same folder using `-Force`.</span></span> <span data-ttu-id="ccdf5-156">它不會覆寫資料夾，只會傳回現有的資料夾物件，並建立不完整的檔案。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-156">It will not overwrite the folder but simply return the existing folder object with the file created intact.</span></span>

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

### <span data-ttu-id="ccdf5-157">範例9：使用-Force 參數來覆寫現有的檔案</span><span class="sxs-lookup"><span data-stu-id="ccdf5-157">Example 9: Use the -Force parameter to overwrite existing files</span></span>

<span data-ttu-id="ccdf5-158">這個範例會建立具有值的檔案，然後使用重新建立檔案 `-Force` 。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-158">This example creates a file with a value and then recreates the file using `-Force`.</span></span> <span data-ttu-id="ccdf5-159">這會覆寫現有的檔案，而其內容將會遺失，因為 length 屬性可以看到它。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-159">This overwrites The existing file and it will lose it's content as you can see by the length property</span></span>

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
> <span data-ttu-id="ccdf5-160">搭配使用 `New-Item` 參數與 `-Force` 參數來建立登錄機碼時，命令的行為會與覆寫檔案時相同。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-160">When using `New-Item` with the `-Force` switch to create registry keys, the command will behave the same as when overwriting a file.</span></span> <span data-ttu-id="ccdf5-161">如果登錄機碼已經存在，則會以空白的登錄機碼覆寫機碼和所有屬性和值。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-161">If the registry key already exists, the key and all properties and values will be overwritten with an empty registry key.</span></span>

## <span data-ttu-id="ccdf5-162">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ccdf5-162">PARAMETERS</span></span>

### <span data-ttu-id="ccdf5-163">-Credential</span><span class="sxs-lookup"><span data-stu-id="ccdf5-163">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="ccdf5-164">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-164">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="ccdf5-165">若要在執行這個 Cmdlet 時模擬另一位使用者或提升您的認證，請使用 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-165">To impersonate another user or elevate your credentials when running this cmdlet, use `Invoke-Command`.</span></span>

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

### <span data-ttu-id="ccdf5-166">-Force</span><span class="sxs-lookup"><span data-stu-id="ccdf5-166">-Force</span></span>

<span data-ttu-id="ccdf5-167">強制這個 Cmdlet 建立寫入現有唯讀專案的專案。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-167">Forces this cmdlet to create an item that writes over an existing read-only item.</span></span> <span data-ttu-id="ccdf5-168">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-168">Implementation varies from provider to provider.</span></span> <span data-ttu-id="ccdf5-169">即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-169">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="ccdf5-170">-ItemType</span><span class="sxs-lookup"><span data-stu-id="ccdf5-170">-ItemType</span></span>

<span data-ttu-id="ccdf5-171">指定新項目的提供者指定類型。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-171">Specifies the provider-specified type of the new item.</span></span> <span data-ttu-id="ccdf5-172">此參數的可用值取決於您目前使用的提供者。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-172">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="ccdf5-173">如果您的位置位於 `FileSystem` 磁片磁碟機中，則允許下列值：</span><span class="sxs-lookup"><span data-stu-id="ccdf5-173">If your location is in a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="ccdf5-174">檔案</span><span class="sxs-lookup"><span data-stu-id="ccdf5-174">File</span></span>
- <span data-ttu-id="ccdf5-175">目錄</span><span class="sxs-lookup"><span data-stu-id="ccdf5-175">Directory</span></span>
- <span data-ttu-id="ccdf5-176">>symboliclink</span><span class="sxs-lookup"><span data-stu-id="ccdf5-176">SymbolicLink</span></span>
- <span data-ttu-id="ccdf5-177">接合</span><span class="sxs-lookup"><span data-stu-id="ccdf5-177">Junction</span></span>
- <span data-ttu-id="ccdf5-178">硬</span><span class="sxs-lookup"><span data-stu-id="ccdf5-178">HardLink</span></span>

> [!NOTE]
> <span data-ttu-id="ccdf5-179">`SymbolicLink`在 Windows 上建立類型需要以系統管理員的許可權提升許可權。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-179">Creating a `SymbolicLink` type on Windows requires elevation as administrator.</span></span> <span data-ttu-id="ccdf5-180">不過，已啟用開發人員模式的 Windows 10 (組建14972或) 更新版本，不再需要提高建立符號連結的許可權。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-180">However, Windows 10 (build 14972 or newer) with Developer Mode enabled no longer requires elevation creating symbolic links.</span></span>

<span data-ttu-id="ccdf5-181">在 `Certificate` 磁片磁碟機中，這些是您可以指定的值：</span><span class="sxs-lookup"><span data-stu-id="ccdf5-181">In a `Certificate` drive, these are the values you can specify:</span></span>

- <span data-ttu-id="ccdf5-182">憑證提供者</span><span class="sxs-lookup"><span data-stu-id="ccdf5-182">Certificate Provider</span></span>
- <span data-ttu-id="ccdf5-183">憑證</span><span class="sxs-lookup"><span data-stu-id="ccdf5-183">Certificate</span></span>
- <span data-ttu-id="ccdf5-184">市集</span><span class="sxs-lookup"><span data-stu-id="ccdf5-184">Store</span></span>
- <span data-ttu-id="ccdf5-185">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="ccdf5-185">StoreLocation</span></span>

<span data-ttu-id="ccdf5-186">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-186">For more information see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="ccdf5-187">-Name</span><span class="sxs-lookup"><span data-stu-id="ccdf5-187">-Name</span></span>

<span data-ttu-id="ccdf5-188">指定新項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-188">Specifies the name of the new item.</span></span> <span data-ttu-id="ccdf5-189">您可以在 [ **名稱** ] 或 [ **路徑** ] 參數值中指定新專案的名稱，也可以在 [ **名稱** ] 或 [ **路徑** ] 值中指定新專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-189">You can specify the name of the new item in the **Name** or **Path** parameter value, and you can specify the path of the new item in **Name** or **Path** value.</span></span> <span data-ttu-id="ccdf5-190">使用 **Name** 參數傳遞的專案名稱會與 **Path** 參數的值相對應。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-190">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

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

### <span data-ttu-id="ccdf5-191">-Path</span><span class="sxs-lookup"><span data-stu-id="ccdf5-191">-Path</span></span>

<span data-ttu-id="ccdf5-192">指定新專案的位置路徑。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-192">Specifies the path of the location of the new item.</span></span> <span data-ttu-id="ccdf5-193">當省略 **路徑** 時，預設值為目前的位置。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-193">The default is the current location when **Path** is omitted.</span></span> <span data-ttu-id="ccdf5-194">您可以在 [ **名稱** ] 中指定新專案的名稱，或將它包含在 **Path** 中。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-194">You can specify the name of the new item in **Name** , or include it in **Path** .</span></span> <span data-ttu-id="ccdf5-195">使用 **Name** 參數傳遞的專案名稱會與 **Path** 參數的值相對應。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-195">Items names passed using the **Name** parameter are created relative to the value of the **Path** parameter.</span></span>

<span data-ttu-id="ccdf5-196">針對此 Cmdlet， **Path** 參數的運作方式就像其他 Cmdlet 的 **LiteralPath** 參數。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-196">For this cmdlet, the **Path** parameter works like the **LiteralPath** parameter of other cmdlets.</span></span>
<span data-ttu-id="ccdf5-197">萬用字元不會被解讀。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-197">Wildcard characters are not interpreted.</span></span> <span data-ttu-id="ccdf5-198">所有字元都會傳遞至位置的提供者。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-198">All characters are passed to the location's provider.</span></span> <span data-ttu-id="ccdf5-199">提供者可能不支援所有字元。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-199">The provider may not support all characters.</span></span> <span data-ttu-id="ccdf5-200">例如，您無法建立包含星號 (`*`) 字元的檔案名。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-200">For example, you cannot create a filename that contains an asterisk (`*`) character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: pathSet
Aliases:

Required: True (pathSet), False (nameSet)
Position: 0
Default value: Current location
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ccdf5-201">-Value</span><span class="sxs-lookup"><span data-stu-id="ccdf5-201">-Value</span></span>

<span data-ttu-id="ccdf5-202">指定新項目的值。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-202">Specifies the value of the new item.</span></span> <span data-ttu-id="ccdf5-203">您也可以使用管線將值傳送至 `New-Item` 。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-203">You can also pipe a value to `New-Item`.</span></span>

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

### <span data-ttu-id="ccdf5-204">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ccdf5-204">-Confirm</span></span>

<span data-ttu-id="ccdf5-205">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-205">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ccdf5-206">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ccdf5-206">-WhatIf</span></span>

<span data-ttu-id="ccdf5-207">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-207">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ccdf5-208">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-208">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ccdf5-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ccdf5-209">CommonParameters</span></span>

<span data-ttu-id="ccdf5-210">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-210">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="ccdf5-211">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-211">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ccdf5-212">輸入</span><span class="sxs-lookup"><span data-stu-id="ccdf5-212">INPUTS</span></span>

### <span data-ttu-id="ccdf5-213">System.Object</span><span class="sxs-lookup"><span data-stu-id="ccdf5-213">System.Object</span></span>

<span data-ttu-id="ccdf5-214">您可以使用管線將新專案的值傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-214">You can pipe a value for the new item to this cmdlet.</span></span>

## <span data-ttu-id="ccdf5-215">輸出</span><span class="sxs-lookup"><span data-stu-id="ccdf5-215">OUTPUTS</span></span>

### <span data-ttu-id="ccdf5-216">System.Object</span><span class="sxs-lookup"><span data-stu-id="ccdf5-216">System.Object</span></span>

<span data-ttu-id="ccdf5-217">這個 Cmdlet 會傳回它所建立的專案。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-217">This cmdlet returns the item that it creates.</span></span>

## <span data-ttu-id="ccdf5-218">注意</span><span class="sxs-lookup"><span data-stu-id="ccdf5-218">NOTES</span></span>

<span data-ttu-id="ccdf5-219">`New-Item` 的設計目的是要與任何提供者公開的資料搭配使用。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-219">`New-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="ccdf5-220">若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-220">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="ccdf5-221">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="ccdf5-221">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="ccdf5-222">相關連結</span><span class="sxs-lookup"><span data-stu-id="ccdf5-222">RELATED LINKS</span></span>

[<span data-ttu-id="ccdf5-223">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="ccdf5-223">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="ccdf5-224">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="ccdf5-224">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="ccdf5-225">Get-Item</span><span class="sxs-lookup"><span data-stu-id="ccdf5-225">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="ccdf5-226">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="ccdf5-226">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="ccdf5-227">Move-Item</span><span class="sxs-lookup"><span data-stu-id="ccdf5-227">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="ccdf5-228">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="ccdf5-228">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="ccdf5-229">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="ccdf5-229">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="ccdf5-230">Set-Item</span><span class="sxs-lookup"><span data-stu-id="ccdf5-230">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="ccdf5-231">about_Providers</span><span class="sxs-lookup"><span data-stu-id="ccdf5-231">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

