---
description: FileSystem
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: FileSystem 提供者
ms.openlocfilehash: 8407dd11c3c9ead10b081b937fbac3db82735eb3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206760"
---
# <a name="filesystem-provider"></a><span data-ttu-id="385bb-104">FileSystem 提供者</span><span class="sxs-lookup"><span data-stu-id="385bb-104">FileSystem provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="385bb-105">提供者名稱</span><span class="sxs-lookup"><span data-stu-id="385bb-105">Provider name</span></span>
<span data-ttu-id="385bb-106">FileSystem</span><span class="sxs-lookup"><span data-stu-id="385bb-106">FileSystem</span></span>

## <a name="drives"></a><span data-ttu-id="385bb-107">磁碟機</span><span class="sxs-lookup"><span data-stu-id="385bb-107">Drives</span></span>

<span data-ttu-id="385bb-108">`C:`, `D:` ...</span><span class="sxs-lookup"><span data-stu-id="385bb-108">`C:`, `D:` ...</span></span>

## <a name="capabilities"></a><span data-ttu-id="385bb-109">功能</span><span class="sxs-lookup"><span data-stu-id="385bb-109">Capabilities</span></span>

<span data-ttu-id="385bb-110">**篩選** 、 **ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="385bb-110">**Filter** , **ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="385bb-111">簡短描述</span><span class="sxs-lookup"><span data-stu-id="385bb-111">Short description</span></span>

<span data-ttu-id="385bb-112">提供檔案與目錄的存取。</span><span class="sxs-lookup"><span data-stu-id="385bb-112">Provides access to files and directories.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="385bb-113">詳細描述</span><span class="sxs-lookup"><span data-stu-id="385bb-113">Detailed description</span></span>

<span data-ttu-id="385bb-114">PowerShell **FileSystem** 提供者可讓您在 powershell 中取得、新增、變更、清除和刪除檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="385bb-114">The PowerShell **FileSystem** provider lets you get, add, change, clear, and delete files and directories in PowerShell.</span></span>

<span data-ttu-id="385bb-115">**FileSystem** 磁片磁碟機是階層式命名空間，其中包含您電腦上的目錄和檔案。</span><span class="sxs-lookup"><span data-stu-id="385bb-115">The **FileSystem** drives are a hierarchical namespace containing the directories and files on your computer.</span></span> <span data-ttu-id="385bb-116">**FileSystem** 磁片磁碟機可以是邏輯或 phsyical 磁片磁碟機、目錄或對應的網路共用。</span><span class="sxs-lookup"><span data-stu-id="385bb-116">A **FileSystem** drive can be a logical or phsyical drive, directory, or mapped network share.</span></span>

<span data-ttu-id="385bb-117">名為的磁片磁碟機 `TEMP:` 將會對應至使用者的臨時目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="385bb-117">A drive called `TEMP:` will be mapped to the user's temporary directory path.</span></span>

>[!NOTE]
> <span data-ttu-id="385bb-118">TEMP：磁片磁碟機中的內容不會被 PowerShell 自動移除，而是由使用者或作業系統進行管理。</span><span class="sxs-lookup"><span data-stu-id="385bb-118">Contents in the TEMP: drive are not automatically removed by PowerShell and is up to the user or operating system to manage.</span></span>

<span data-ttu-id="385bb-119">**FileSystem** 提供者支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。</span><span class="sxs-lookup"><span data-stu-id="385bb-119">The **FileSystem** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="385bb-120">Get-Location</span><span class="sxs-lookup"><span data-stu-id="385bb-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="385bb-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="385bb-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="385bb-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="385bb-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="385bb-123">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="385bb-123">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="385bb-124">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="385bb-124">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="385bb-125">Move-Item</span><span class="sxs-lookup"><span data-stu-id="385bb-125">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="385bb-126">New-Item</span><span class="sxs-lookup"><span data-stu-id="385bb-126">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="385bb-127">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="385bb-127">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="385bb-128">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="385bb-128">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="385bb-129">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="385bb-129">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="385bb-130">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="385bb-130">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="385bb-131">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="385bb-131">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="385bb-132">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="385bb-132">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="385bb-133">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="385bb-133">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="385bb-134">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="385bb-134">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="385bb-135">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="385bb-135">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)
- [<span data-ttu-id="385bb-136">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="385bb-136">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="385bb-137">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="385bb-137">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="385bb-138">此提供者公開的類型</span><span class="sxs-lookup"><span data-stu-id="385bb-138">Types exposed by this provider</span></span>

<span data-ttu-id="385bb-139">檔案是 [FileInfo](/dotnet/api/system.io.fileinfo) 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="385bb-139">Files are instances of the [System.IO.FileInfo](/dotnet/api/system.io.fileinfo) class.</span></span>  <span data-ttu-id="385bb-140">目錄是 [DirectoryInfo](/dotnet/api/system.io.directoryinfo) 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="385bb-140">Directories are instances of the [System.IO.DirectoryInfo](/dotnet/api/system.io.directoryinfo) class.</span></span>

## <a name="navigating-the-filesystem-drives"></a><span data-ttu-id="385bb-141">流覽檔案系統磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="385bb-141">Navigating the FileSystem drives</span></span>

<span data-ttu-id="385bb-142">**FileSystem** 提供者會將電腦上的任何邏輯磁碟機對應為 PowerShell 磁片磁碟機，以公開其資料存放區。</span><span class="sxs-lookup"><span data-stu-id="385bb-142">The **FileSystem** provider exposes its data stores by mapping any logical drives on the computer as PowerShell drives.</span></span> <span data-ttu-id="385bb-143">若要使用 **檔案系統** 磁片磁碟機，您可以將位置變更為磁片磁碟機，uing 磁片磁碟機名稱後面接著冒號 (`:`) 。</span><span class="sxs-lookup"><span data-stu-id="385bb-143">To work with a **FileSystem** drive you can change your location to a drive uing the drive name followed by a colon (`:`).</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="385bb-144">您也可以使用任何其他 PowerShell 磁片磁碟機的 **FileSystem** 提供者。</span><span class="sxs-lookup"><span data-stu-id="385bb-144">You can also work with the **FileSystem** provider from any other PowerShell drive.</span></span> <span data-ttu-id="385bb-145">若要從另一個位置參考檔案或目錄，請 `C:` 在路徑中使用磁片磁碟機名稱 (， `D:` ) 。</span><span class="sxs-lookup"><span data-stu-id="385bb-145">To reference a file or directory from another location, use the drive name (`C:`, `D:`, ...) in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="385bb-146">PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="385bb-146">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="385bb-147">和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="385bb-147">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="385bb-148">和 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。</span><span class="sxs-lookup"><span data-stu-id="385bb-148">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-files-and-directories"></a><span data-ttu-id="385bb-149">取得檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="385bb-149">Getting files and directories</span></span>

<span data-ttu-id="385bb-150">Cmdlet 會傳回 `Get-ChildItem` 目前位置中的所有檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="385bb-150">The `Get-ChildItem` cmdlet returns all files and directories in the current location.</span></span> <span data-ttu-id="385bb-151">您可以指定不同的路徑來搜尋和使用內建參數，以篩選和控制遞迴深度。</span><span class="sxs-lookup"><span data-stu-id="385bb-151">You can specify a different path to search and use built in parameters to filter and control the recursion depth.</span></span>

```powershell
Get-ChildItem
```

<span data-ttu-id="385bb-152">若要閱讀更多 Cmdlet 用法的詳細資訊，請參閱 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)。</span><span class="sxs-lookup"><span data-stu-id="385bb-152">To read more about cmdlet usage, see [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).</span></span>

## <a name="copying-files-and-directories"></a><span data-ttu-id="385bb-153">複製檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="385bb-153">Copying files and directories</span></span>

<span data-ttu-id="385bb-154">`Copy-Item`Cmdlet 會將檔案和目錄複寫到您指定的位置。</span><span class="sxs-lookup"><span data-stu-id="385bb-154">The `Copy-Item` cmdlet copies files and directories to a location you specify.</span></span>
<span data-ttu-id="385bb-155">參數可用於篩選和遞迴，類似于 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="385bb-155">Parameters are available to filter and recurse, similar to `Get-ChildItem`.</span></span>

<span data-ttu-id="385bb-156">下列命令會將路徑 "C：\temp" 的所有檔案和目錄複寫 \" 到 "C:\Windows\Temp" 資料夾。</span><span class="sxs-lookup"><span data-stu-id="385bb-156">The following command copies all of the files and directories under the path "C:\temp\" to the folder "C:\Windows\Temp".</span></span>

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

<span data-ttu-id="385bb-157">`Copy-Item` 覆寫目的地目錄中的檔案，而不提示確認。</span><span class="sxs-lookup"><span data-stu-id="385bb-157">`Copy-Item` overwrites files in the destination directory without prompting for confirmation.</span></span>

<span data-ttu-id="385bb-158">此命令會將檔案 `a.txt` 從 `C:\a` 目錄複寫到 `C:\a\bb` 目錄。</span><span class="sxs-lookup"><span data-stu-id="385bb-158">This command copies the `a.txt` file from the `C:\a` directory to the `C:\a\bb` directory.</span></span>

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

<span data-ttu-id="385bb-159">將目錄中的所有目錄和檔案複製 `C:\a` 到 `C:\c` 目錄。</span><span class="sxs-lookup"><span data-stu-id="385bb-159">Copies all the directories and files in the `C:\a` directory to the `C:\c` directory.</span></span> <span data-ttu-id="385bb-160">如果要複製的任一個目錄已經存在於目的地目錄中，除非您指定 Force 參數，否則此命令將會失敗。</span><span class="sxs-lookup"><span data-stu-id="385bb-160">If any of the directories to copy already exist in the destination directory, the command will fail unless you specify the Force parameter.</span></span>

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

<span data-ttu-id="385bb-161">如需詳細資訊，請參閱 [複製專案](xref:Microsoft.PowerShell.Management.Copy-Item)。</span><span class="sxs-lookup"><span data-stu-id="385bb-161">For more information, see [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item).</span></span>

## <a name="moving-files-and-directories"></a><span data-ttu-id="385bb-162">移動檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="385bb-162">Moving files and directories</span></span>

<span data-ttu-id="385bb-163">此命令會將 `c.txt` 目錄中的檔案移 `C:\a` 至 `C:\a\aa` 目錄：</span><span class="sxs-lookup"><span data-stu-id="385bb-163">This command moves the `c.txt` file in the `C:\a` directory to the `C:\a\aa` directory:</span></span>

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

<span data-ttu-id="385bb-164">此命令將不會自動覆寫具有相同名稱的現有檔案。</span><span class="sxs-lookup"><span data-stu-id="385bb-164">The command will not automatically overwrite an existing file that has the same name.</span></span> <span data-ttu-id="385bb-165">若要強制此 Cmdlet 覆寫現有的檔案，請指定 Force 參數。</span><span class="sxs-lookup"><span data-stu-id="385bb-165">To force the cmdlet to overwrite an existing file, specify the Force parameter.</span></span>

<span data-ttu-id="385bb-166">當目錄為目前位置時，您無法移動該目錄。</span><span class="sxs-lookup"><span data-stu-id="385bb-166">You cannot move a directory when that directory is the current location.</span></span> <span data-ttu-id="385bb-167">當您使用 `Move-Item` 來移動目前位置的目錄時，您會看到此錯誤。</span><span class="sxs-lookup"><span data-stu-id="385bb-167">When you use `Move-Item` to move the directory at the current location, you see this error.</span></span>

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a><span data-ttu-id="385bb-168">管理檔案內容</span><span class="sxs-lookup"><span data-stu-id="385bb-168">Managing file content</span></span>

### <a name="get-the-content-of-a-file"></a><span data-ttu-id="385bb-169">取得檔案的內容</span><span class="sxs-lookup"><span data-stu-id="385bb-169">Get the content of a file</span></span>

<span data-ttu-id="385bb-170">此命令會取得 "Test.txt" 檔案的內容，並在主控台中顯示它們。</span><span class="sxs-lookup"><span data-stu-id="385bb-170">This command gets the contents of the "Test.txt" file and displays them in the console.</span></span>

```powershell
Get-Content -Path Test.txt
```

<span data-ttu-id="385bb-171">您可以使用管線將檔案的內容傳送至其他 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="385bb-171">You can pipe the contents of the file to another cmdlet.</span></span> <span data-ttu-id="385bb-172">例如，下列命令會讀取檔案的內容 `Test.txt` ，然後以輸入形式提供給 [ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="385bb-172">For example, the following command reads the contents of the `Test.txt` file and then supplies them as input to the [ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet:</span></span>

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

<span data-ttu-id="385bb-173">您也可以將檔案的提供者路徑加上貨幣符號 () ，以取出檔案的內容 `$` 。</span><span class="sxs-lookup"><span data-stu-id="385bb-173">You can also retrieve the content of a file by prefixing its provider path with the dollar sign (`$`).</span></span> <span data-ttu-id="385bb-174">因為變數命名限制，路徑必須以大括弧括住。</span><span class="sxs-lookup"><span data-stu-id="385bb-174">The path must be enclosed in curly braces due to variable naming restrictions.</span></span> <span data-ttu-id="385bb-175">如需詳細資訊，請參閱 [about_Variables](about_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="385bb-175">For more information, see [about_Variables](about_Variables.md).</span></span>

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a><span data-ttu-id="385bb-176">將內容新增至檔案</span><span class="sxs-lookup"><span data-stu-id="385bb-176">Add content to a file</span></span>

<span data-ttu-id="385bb-177">此命令會將 "test content" 字串附加至檔案 `Test.txt` ：</span><span class="sxs-lookup"><span data-stu-id="385bb-177">This command appends the "test content" string to the `Test.txt` file:</span></span>

```powershell
Add-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="385bb-178">不會刪除檔案中的現有內容 `Test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="385bb-178">The existing content in the `Test.txt` file is not deleted.</span></span>

### <a name="replace-the-content-of-a-file"></a><span data-ttu-id="385bb-179">取代檔案的內容</span><span class="sxs-lookup"><span data-stu-id="385bb-179">Replace the content of a file</span></span>

<span data-ttu-id="385bb-180">此命令會以「測試內容」字串取代檔案的內容 `Test.txt` ：</span><span class="sxs-lookup"><span data-stu-id="385bb-180">This command replaces the contents of the `Test.txt` file with the "test content" string:</span></span>

```powershell
Set-Content -Path test.txt -Value "test content"
```

<span data-ttu-id="385bb-181">它會覆寫的內容 `Test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="385bb-181">It overwrites the contents of `Test.txt`.</span></span> <span data-ttu-id="385bb-182">您可以使用 [新專案](xref:Microsoft.PowerShell.Management.New-Item)Cmdlet 的 **Value** 參數，在建立內容時將內容新增至檔案。</span><span class="sxs-lookup"><span data-stu-id="385bb-182">You can use the **Value** parameter of the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to add content to a file when you create it.</span></span>

### <a name="loop-through-the-contents-of-a-file"></a><span data-ttu-id="385bb-183">逐一查看檔案的內容</span><span class="sxs-lookup"><span data-stu-id="385bb-183">Loop through the contents of a file</span></span>

<span data-ttu-id="385bb-184">根據預設，此 `Get-Content` Cmdlet 會使用行結尾字元做為分隔符號，因此它會以字串集合的形式取得檔案，其中每一行都是檔案中的一個字串。</span><span class="sxs-lookup"><span data-stu-id="385bb-184">By default, the `Get-Content` cmdlet uses the end-of-line character as its delimiter, so it gets a file as a collection of strings, with each line as one string in the file.</span></span>

<span data-ttu-id="385bb-185">您可以使用 `-Delimiter` 參數來指定替代分隔符號。</span><span class="sxs-lookup"><span data-stu-id="385bb-185">You can use the `-Delimiter` parameter to specify an alternate delimiter.</span></span> <span data-ttu-id="385bb-186">如果您將它設定為代表某區段結尾或下一區段開頭的字元，就可以將檔案分割為邏輯部分。</span><span class="sxs-lookup"><span data-stu-id="385bb-186">If you set it to the characters that denote the end of a section or the beginning of the next section, you can split the file into logical parts.</span></span>

<span data-ttu-id="385bb-187">第一個命令會取得檔案 `Employees.txt` 並將它分割成區段，而每個區段的結尾都是「員工記錄結尾」，並且會將它儲存在 `$e` 變數中。</span><span class="sxs-lookup"><span data-stu-id="385bb-187">The first command gets the `Employees.txt` file and splits it into sections, each of which ends with the words "End of Employee Record" and it saves it in the `$e` variable.</span></span>

<span data-ttu-id="385bb-188">第二個命令會使用陣列標記法，取得集合中的第一個專案 `$e` 。</span><span class="sxs-lookup"><span data-stu-id="385bb-188">The second command uses array notation to get the first item in the collection in `$e`.</span></span> <span data-ttu-id="385bb-189">因為 PowerShell 陣列是以零為基礎，所以它會使用索引0。</span><span class="sxs-lookup"><span data-stu-id="385bb-189">It uses an index of 0, because PowerShell arrays are zero-based.</span></span>

<span data-ttu-id="385bb-190">如需有關 Cmdlet 的詳細資訊 `Get-Content` ，請參閱 [取得內容](xref:Microsoft.PowerShell.Management.Get-Content)的說明主題。</span><span class="sxs-lookup"><span data-stu-id="385bb-190">For more information about `Get-Content` cmdlet, see the help topic for the [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content).</span></span>

<span data-ttu-id="385bb-191">如需陣列的詳細資訊，請參閱 [about_Arrays](../About/about_Arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="385bb-191">For more information about arrays, see [about_Arrays](../About/about_Arrays.md).</span></span>

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a><span data-ttu-id="385bb-192">管理安全描述項</span><span class="sxs-lookup"><span data-stu-id="385bb-192">Managing security descriptors</span></span>

### <a name="view-the-acl-for-a-file"></a><span data-ttu-id="385bb-193">查看檔案的 ACL</span><span class="sxs-lookup"><span data-stu-id="385bb-193">View the ACL for a file</span></span>

<span data-ttu-id="385bb-194">此命令會傳回 [AccessControl. system.security.accesscontrol.filesecurity](/dotnet/api/system.security.accesscontrol.filesecurity) 物件：</span><span class="sxs-lookup"><span data-stu-id="385bb-194">This command returns a [System.Security.AccessControl.FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) object:</span></span>

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

<span data-ttu-id="385bb-195">如需此物件的詳細資訊，請將命令輸送至 [取得成員](xref:Microsoft.PowerShell.Utility.Get-Member) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="385bb-195">For more information about this object, pipe the command to the [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member) cmdlet.</span></span> <span data-ttu-id="385bb-196">或者，請參閱 MSDN (Microsoft 開發人員網路) 程式庫中的「[System.security.accesscontrol.filesecurity](/dotnet/api/system.security.accesscontrol.filesecurity) 類別」。</span><span class="sxs-lookup"><span data-stu-id="385bb-196">Or, see "[FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) Class" in the MSDN (Microsoft Developer Network) library.</span></span>

### <a name="modify-the-acl-for-a-file"></a><span data-ttu-id="385bb-197">修改檔案的 ACL</span><span class="sxs-lookup"><span data-stu-id="385bb-197">Modify the ACL for a file</span></span>

### <a name="create-and-set-an-acl-for-a-file"></a><span data-ttu-id="385bb-198">建立並設定檔案的 ACL</span><span class="sxs-lookup"><span data-stu-id="385bb-198">Create and set an ACL for a file</span></span>

## <a name="creating-files-and-directories"></a><span data-ttu-id="385bb-199">建立檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="385bb-199">Creating files and directories</span></span>

### <a name="create-a-directory"></a><span data-ttu-id="385bb-200">建立目錄</span><span class="sxs-lookup"><span data-stu-id="385bb-200">Create a directory</span></span>

<span data-ttu-id="385bb-201">此命令會 `logfiles` 在磁片磁碟機上建立目錄 `C` ：</span><span class="sxs-lookup"><span data-stu-id="385bb-201">This command creates the `logfiles` directory on the `C` drive:</span></span>

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

<span data-ttu-id="385bb-202">PowerShell 也包含 `mkdir` (別名 `md`) 的函式，該函 [式使用新專案](xref:Microsoft.PowerShell.Management.New-Item) Cmdlet 來建立新目錄。</span><span class="sxs-lookup"><span data-stu-id="385bb-202">PowerShell also includes a `mkdir` function (alias `md`) that uses the [New-Item](xref:Microsoft.PowerShell.Management.New-Item) cmdlet to create a new directory.</span></span>

### <a name="create-a-file"></a><span data-ttu-id="385bb-203">建立檔案</span><span class="sxs-lookup"><span data-stu-id="385bb-203">Create a file</span></span>

<span data-ttu-id="385bb-204">此命令會 `log2.txt` 在目錄中建立檔案 `C:\logfiles` ，然後將 "test log" 字串新增至檔案：</span><span class="sxs-lookup"><span data-stu-id="385bb-204">This command creates the `log2.txt` file in the `C:\logfiles` directory and then adds the "test log" string to the file:</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a><span data-ttu-id="385bb-205">建立具有內容的檔案</span><span class="sxs-lookup"><span data-stu-id="385bb-205">Create a file with content</span></span>

<span data-ttu-id="385bb-206">在目錄中建立名為的檔案 `log2.txt` `C:\logfiles` ，並將字串 "test log" 新增至檔案。</span><span class="sxs-lookup"><span data-stu-id="385bb-206">Creates a file called `log2.txt` in the `C:\logfiles` directory and adds the string "test log" to the file.</span></span>

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a><span data-ttu-id="385bb-207">重新命名檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="385bb-207">Renaming files and directories</span></span>

### <a name="rename-a-file"></a><span data-ttu-id="385bb-208">重新命名檔案</span><span class="sxs-lookup"><span data-stu-id="385bb-208">Rename a file</span></span>

<span data-ttu-id="385bb-209">此命令會將目錄中的檔案重新命名 `a.txt` `C:\a` 為 `b.txt` ：</span><span class="sxs-lookup"><span data-stu-id="385bb-209">This command renames the `a.txt` file in the `C:\a` directory to `b.txt`:</span></span>

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a><span data-ttu-id="385bb-210">重新命名目錄</span><span class="sxs-lookup"><span data-stu-id="385bb-210">Rename a directory</span></span>

<span data-ttu-id="385bb-211">此命令會將 `C:\a\cc` 目錄重新命名為 `C:\a\dd` ：</span><span class="sxs-lookup"><span data-stu-id="385bb-211">This command renames the `C:\a\cc` directory to `C:\a\dd`:</span></span>

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a><span data-ttu-id="385bb-212">刪除檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="385bb-212">Deleting files and directories</span></span>

### <a name="delete-a-file"></a><span data-ttu-id="385bb-213">刪除檔案</span><span class="sxs-lookup"><span data-stu-id="385bb-213">Delete a file</span></span>

<span data-ttu-id="385bb-214">此命令會刪除 `Test.txt` 目前目錄中的檔案：</span><span class="sxs-lookup"><span data-stu-id="385bb-214">This command deletes the `Test.txt` file in the current directory:</span></span>

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a><span data-ttu-id="385bb-215">使用萬用字元刪除檔案</span><span class="sxs-lookup"><span data-stu-id="385bb-215">Delete files using wildcards</span></span>

<span data-ttu-id="385bb-216">此命令會刪除目前目錄中副檔名為的所有檔案 `.xml` ：</span><span class="sxs-lookup"><span data-stu-id="385bb-216">This command deletes all the files in the current directory that have the `.xml` file name extension:</span></span>

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a><span data-ttu-id="385bb-217">藉由叫用相關聯的檔案來啟動程式</span><span class="sxs-lookup"><span data-stu-id="385bb-217">Starting a program by invoking an associated file</span></span>

### <a name="invoke-a-file"></a><span data-ttu-id="385bb-218">叫用檔案</span><span class="sxs-lookup"><span data-stu-id="385bb-218">Invoke a file</span></span>

<span data-ttu-id="385bb-219">第一個命令會使用 [get-help](xref:Microsoft.PowerShell.Management.Get-Service) Cmdlet 來取得本機服務的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="385bb-219">The first command uses the [Get-Service](xref:Microsoft.PowerShell.Management.Get-Service) cmdlet to get information about local services.</span></span>

<span data-ttu-id="385bb-220">它會將資訊傳送至 [匯出 Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) Cmdlet，然後將該資訊儲存在檔案中 `Services.csv` 。</span><span class="sxs-lookup"><span data-stu-id="385bb-220">It pipes the information to the [Export-Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdlet and then stores that information in the `Services.csv` file.</span></span>

<span data-ttu-id="385bb-221">第二個命令會使用 [Invoke 專案](xref:Microsoft.PowerShell.Management.Invoke-Item) ， `services.csv` 在與擴充功能相關聯的程式中開啟檔案 `.csv` ：</span><span class="sxs-lookup"><span data-stu-id="385bb-221">The second command uses [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item) to open the `services.csv` file in the program associated with the `.csv` extension:</span></span>

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a><span data-ttu-id="385bb-222">取得具有指定屬性的檔案和資料夾</span><span class="sxs-lookup"><span data-stu-id="385bb-222">Getting files and folders with specified attributes</span></span>

### <a name="get-system-files"></a><span data-ttu-id="385bb-223">取得系統檔案</span><span class="sxs-lookup"><span data-stu-id="385bb-223">Get System files</span></span>

<span data-ttu-id="385bb-224">此命令會取得目前目錄及其子目錄中的系統檔案。</span><span class="sxs-lookup"><span data-stu-id="385bb-224">This command gets system files in the current directory and its subdirectories.</span></span>

<span data-ttu-id="385bb-225">它會使用 `-File` 參數，只取得 (非目錄) 的檔案，以及 `-System` 只取得具有 "system" 屬性之專案的參數。</span><span class="sxs-lookup"><span data-stu-id="385bb-225">It uses the `-File` parameter to get only files (not directories) and the `-System` parameter to get only items with the "system" attribute.</span></span>

<span data-ttu-id="385bb-226">它會使用 `-Recurse` 參數來取得目前目錄和所有子目錄中的專案。</span><span class="sxs-lookup"><span data-stu-id="385bb-226">It uses the `-Recurse` parameter to get the items in the current directory and all subdirectories.</span></span>

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a><span data-ttu-id="385bb-227">取得隱藏的檔案</span><span class="sxs-lookup"><span data-stu-id="385bb-227">Get Hidden files</span></span>

<span data-ttu-id="385bb-228">此命令會取得目前目錄中的所有檔案 (包括隱藏的檔案)。</span><span class="sxs-lookup"><span data-stu-id="385bb-228">This command gets all files, including hidden files, in the current directory.</span></span>

<span data-ttu-id="385bb-229">它會使用具有兩個值的 **屬性** 參數，這些值會 `!Directory+Hidden` 取得隱藏的檔案，以及 `!Directory` 取得所有其他檔案。</span><span class="sxs-lookup"><span data-stu-id="385bb-229">It uses the **Attributes** parameter with two values, `!Directory+Hidden`, which gets hidden files, and `!Directory`, which gets all other files.</span></span>

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

<span data-ttu-id="385bb-230">`dir -att !d,!d+h` 相當於這個命令。</span><span class="sxs-lookup"><span data-stu-id="385bb-230">`dir -att !d,!d+h` is the equivalent of this command.</span></span>

### <a name="get-compressed-and-encrypted-files"></a><span data-ttu-id="385bb-231">取得壓縮和加密的檔案</span><span class="sxs-lookup"><span data-stu-id="385bb-231">Get Compressed and Encrypted files</span></span>

<span data-ttu-id="385bb-232">此命令會取得目前目錄中已壓縮或加密的檔案。</span><span class="sxs-lookup"><span data-stu-id="385bb-232">This command gets files in the current directory that are either compressed or encrypted.</span></span>

<span data-ttu-id="385bb-233">它會使用 `-Attributes` 具有兩個值的參數： `Compressed` 和 `Encrypted` 。</span><span class="sxs-lookup"><span data-stu-id="385bb-233">It uses the `-Attributes` parameter with two values, `Compressed` and `Encrypted`.</span></span> <span data-ttu-id="385bb-234">這些值會以逗號分隔， `,` 表示 "OR" 運算子。</span><span class="sxs-lookup"><span data-stu-id="385bb-234">The values are separated by a comma `,` which represents the "OR" operator.</span></span>

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a><span data-ttu-id="385bb-235">動態參數</span><span class="sxs-lookup"><span data-stu-id="385bb-235">Dynamic parameters</span></span>

<span data-ttu-id="385bb-236">動態參數是 PowerShell 提供者新增的 Cmdlet 參數，而且只有在提供者啟用的磁片磁碟機中使用 Cmdlet 時才能使用。</span><span class="sxs-lookup"><span data-stu-id="385bb-236">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a><span data-ttu-id="385bb-237">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span><span class="sxs-lookup"><span data-stu-id="385bb-237">Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\></span></span>

<span data-ttu-id="385bb-238">指定檔案的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="385bb-238">Specifies the file encoding.</span></span> <span data-ttu-id="385bb-239">預設值為 ASCII。</span><span class="sxs-lookup"><span data-stu-id="385bb-239">The default is ASCII.</span></span>

- <span data-ttu-id="385bb-240">**Ascii** ：使用 ascii (7 位) 字元集的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="385bb-240">**ASCII** :  Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="385bb-241">**BigEndianUnicode** ：使用位元組由大到小的位元組順序，以 Utf-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="385bb-241">**BigEndianUnicode** :  Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="385bb-242">**字串** ：使用字串的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="385bb-242">**String** :  Uses the encoding type for a string.</span></span>
- <span data-ttu-id="385bb-243">**Unicode** ：使用位元組由大到小的位元組順序，以 Utf-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="385bb-243">**Unicode** :  Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="385bb-244">**UTF7** ：以 Utf-7 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="385bb-244">**UTF7** :   Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="385bb-245">**UTF8** ：以 Utf-8 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="385bb-245">**UTF8** :  Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="385bb-246">**UTF8BOM** ：使用 (BOM) 的位元組順序標記來編碼 utf-8 格式</span><span class="sxs-lookup"><span data-stu-id="385bb-246">**UTF8BOM** : Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="385bb-247">**UF8NOBOM** ：以不含位元組順序標記的 Utf-8 格式來編碼 (BOM) </span><span class="sxs-lookup"><span data-stu-id="385bb-247">**UF8NOBOM** : Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="385bb-248">**UTF32** ：以 UTF-32 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="385bb-248">**UTF32** :  Encodes in UTF-32 format.</span></span>
- <span data-ttu-id="385bb-249">**預設** ：在預設安裝的字碼頁中進行編碼。</span><span class="sxs-lookup"><span data-stu-id="385bb-249">**Default** : Encodes in the default installed code page.</span></span>
- <span data-ttu-id="385bb-250">**OEM** ：對 MS-DOS 和主控台程式使用預設編碼。</span><span class="sxs-lookup"><span data-stu-id="385bb-250">**OEM** : Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="385bb-251">**未知** ：編碼類型未知或無效。</span><span class="sxs-lookup"><span data-stu-id="385bb-251">**Unknown** :  The encoding type is unknown or invalid.</span></span> <span data-ttu-id="385bb-252">資料可視為二進位檔。</span><span class="sxs-lookup"><span data-stu-id="385bb-252">The data can be treated as binary.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-253">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-253">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-254">Add-Content</span><span class="sxs-lookup"><span data-stu-id="385bb-254">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="385bb-255">Get-Content</span><span class="sxs-lookup"><span data-stu-id="385bb-255">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="385bb-256">Set-Content</span><span class="sxs-lookup"><span data-stu-id="385bb-256">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a><span data-ttu-id="385bb-257">Delimiter \<System.String\></span><span class="sxs-lookup"><span data-stu-id="385bb-257">Delimiter \<System.String\></span></span>

<span data-ttu-id="385bb-258">指定分隔符號，讓 [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) 在讀取時可用來將檔案分割成物件。</span><span class="sxs-lookup"><span data-stu-id="385bb-258">Specifies the delimiter that [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) uses to divide the file into objects while it reads.</span></span>

<span data-ttu-id="385bb-259">預設值為 `\n` ，行尾字元。</span><span class="sxs-lookup"><span data-stu-id="385bb-259">The default is `\n`, the end-of-line character.</span></span>

<span data-ttu-id="385bb-260">讀取文字檔時， [Get 內容](xref:Microsoft.PowerShell.Management.Get-Content) 會傳回字串物件的集合，其中每個物件的結尾都是分隔符號。</span><span class="sxs-lookup"><span data-stu-id="385bb-260">When reading a text file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns a collection of string objects, each of which ends with the delimiter character.</span></span>

<span data-ttu-id="385bb-261">輸入不存在於檔案中的分隔符號， [Get 內容](xref:Microsoft.PowerShell.Management.Get-Content) 會以單一、未分隔的物件形式傳回整個檔案。</span><span class="sxs-lookup"><span data-stu-id="385bb-261">Entering a delimiter that does not exist in the file, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) returns the entire file as a single, un-delimited object.</span></span>

<span data-ttu-id="385bb-262">您可以使用這個參數，藉由指定檔案分隔符號 (例如 "End of Example") 做為分隔符號，將大型檔案分割成較小的檔案。</span><span class="sxs-lookup"><span data-stu-id="385bb-262">You can use this parameter to split a large file into smaller files by specifying a file separator, such as "End of Example", as the delimiter.</span></span> <span data-ttu-id="385bb-263">分隔符號會保留 (不會被捨棄)，並成為每個檔案區段中的最後一個項目。</span><span class="sxs-lookup"><span data-stu-id="385bb-263">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

> [!NOTE]
> <span data-ttu-id="385bb-264">目前，當參數的值 `-Delimiter` 為空字串時， [Get 內容](xref:Microsoft.PowerShell.Management.Get-Content) 不會傳回任何內容。</span><span class="sxs-lookup"><span data-stu-id="385bb-264">Currently, when the value of the `-Delimiter` parameter is an empty string, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) does not return anything.</span></span>
> <span data-ttu-id="385bb-265">這是已知的問題。</span><span class="sxs-lookup"><span data-stu-id="385bb-265">This is a known issue.</span></span> <span data-ttu-id="385bb-266">若要強制 [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) 以單一、未分隔的物件形式傳回整個檔案，請輸入檔案中不存在的值。</span><span class="sxs-lookup"><span data-stu-id="385bb-266">To force [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) to return the entire file as a single, undelimited string, enter a value that does not exist in the file.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-267">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-267">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-268">Get-Content</span><span class="sxs-lookup"><span data-stu-id="385bb-268">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a><span data-ttu-id="385bb-269">Wait \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="385bb-269">Wait \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="385bb-270">等候要附加至檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="385bb-270">Waits for content to be appended to the file.</span></span> <span data-ttu-id="385bb-271">如果內容已附加，就會傳回附加的內容。</span><span class="sxs-lookup"><span data-stu-id="385bb-271">If content is appended, it returns the appended content.</span></span> <span data-ttu-id="385bb-272">如果內容已變更，則會傳回整個檔案。</span><span class="sxs-lookup"><span data-stu-id="385bb-272">If the content has changed, it returns the entire file.</span></span>

<span data-ttu-id="385bb-273">等候時，[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) 每秒會檢查檔案一次，直到您中斷它為止，例如，按下 CTRL+C。</span><span class="sxs-lookup"><span data-stu-id="385bb-273">When waiting, [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) checks the file once each second until you interrupt it, such as by pressing CTRL+C.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-274">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-274">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-275">Get-Content</span><span class="sxs-lookup"><span data-stu-id="385bb-275">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a><span data-ttu-id="385bb-276">Attributes \<FlagsExpression\></span><span class="sxs-lookup"><span data-stu-id="385bb-276">Attributes \<FlagsExpression\></span></span>

<span data-ttu-id="385bb-277">取得具有指定屬性的檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="385bb-277">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="385bb-278">此參數支援所有屬性，可讓您指定複雜的屬性組合。</span><span class="sxs-lookup"><span data-stu-id="385bb-278">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="385bb-279">`-Attributes`參數是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="385bb-279">The `-Attributes` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="385bb-280">`-Attributes`參數支援下列屬性：</span><span class="sxs-lookup"><span data-stu-id="385bb-280">The `-Attributes` parameter supports the following attributes:</span></span>

- <span data-ttu-id="385bb-281">**封存**</span><span class="sxs-lookup"><span data-stu-id="385bb-281">**Archive**</span></span>
- <span data-ttu-id="385bb-282">**Compressed**</span><span class="sxs-lookup"><span data-stu-id="385bb-282">**Compressed**</span></span>
- <span data-ttu-id="385bb-283">**裝置**</span><span class="sxs-lookup"><span data-stu-id="385bb-283">**Device**</span></span>
- <span data-ttu-id="385bb-284">**目錄**</span><span class="sxs-lookup"><span data-stu-id="385bb-284">**Directory**</span></span>
- <span data-ttu-id="385bb-285">**已加密**</span><span class="sxs-lookup"><span data-stu-id="385bb-285">**Encrypted**</span></span>
- <span data-ttu-id="385bb-286">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="385bb-286">**Hidden**</span></span>
- <span data-ttu-id="385bb-287">**Normal**</span><span class="sxs-lookup"><span data-stu-id="385bb-287">**Normal**</span></span>
- <span data-ttu-id="385bb-288">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="385bb-288">**NotContentIndexed**</span></span>
- <span data-ttu-id="385bb-289">**離線**</span><span class="sxs-lookup"><span data-stu-id="385bb-289">**Offline**</span></span>
- <span data-ttu-id="385bb-290">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="385bb-290">**ReadOnly**</span></span>
- <span data-ttu-id="385bb-291">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="385bb-291">**ReparsePoint**</span></span>
- <span data-ttu-id="385bb-292">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="385bb-292">**SparseFile**</span></span>
- <span data-ttu-id="385bb-293">**系統**</span><span class="sxs-lookup"><span data-stu-id="385bb-293">**System**</span></span>
- <span data-ttu-id="385bb-294">**暫存**</span><span class="sxs-lookup"><span data-stu-id="385bb-294">**Temporary**</span></span>

<span data-ttu-id="385bb-295">如需這些屬性的說明，請參閱 [FileAttributes](/dotnet/api/system.io.fileattributes) 列舉。</span><span class="sxs-lookup"><span data-stu-id="385bb-295">For a description of these attributes, see the [FileAttributes](/dotnet/api/system.io.fileattributes) enumeration.</span></span>

<span data-ttu-id="385bb-296">使用下列運算子來結合屬性。</span><span class="sxs-lookup"><span data-stu-id="385bb-296">Use the following operators to combine attributes.</span></span>

- <span data-ttu-id="385bb-297">`!` -NOT</span><span class="sxs-lookup"><span data-stu-id="385bb-297">`!` - NOT</span></span>
- <span data-ttu-id="385bb-298">`+` -和</span><span class="sxs-lookup"><span data-stu-id="385bb-298">`+` - AND</span></span>
- <span data-ttu-id="385bb-299">`,` -或</span><span class="sxs-lookup"><span data-stu-id="385bb-299">`,` - OR</span></span>

<span data-ttu-id="385bb-300">運算子和其屬性之間不允許有任何空格。</span><span class="sxs-lookup"><span data-stu-id="385bb-300">No spaces are permitted between an operator and its attribute.</span></span> <span data-ttu-id="385bb-301">不過，逗號之前可以有空格。</span><span class="sxs-lookup"><span data-stu-id="385bb-301">However, spaces are permitted before commas.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-302">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-302">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-303">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="385bb-303">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a><span data-ttu-id="385bb-304">Directory \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="385bb-304">Directory \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="385bb-305">取得目錄 (資料夾)。</span><span class="sxs-lookup"><span data-stu-id="385bb-305">Gets directories (folders).</span></span>

<span data-ttu-id="385bb-306">`-Directory`參數是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="385bb-306">The `-Directory` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="385bb-307">若只要取得目錄，請使用 `-Directory` 參數並省略 `-File` 參數。</span><span class="sxs-lookup"><span data-stu-id="385bb-307">To get only directories, use the `-Directory` parameter and omit the `-File` parameter.</span></span> <span data-ttu-id="385bb-308">若要排除目錄，請使用 `-File` 參數並省略 `-Directory` 參數，或使用 `-Attributes` 參數。</span><span class="sxs-lookup"><span data-stu-id="385bb-308">To exclude directories, use the `-File` parameter and omit the `-Directory` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-309">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-309">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-310">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="385bb-310">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a><span data-ttu-id="385bb-311">File \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="385bb-311">File \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="385bb-312">取得檔案。</span><span class="sxs-lookup"><span data-stu-id="385bb-312">Gets files.</span></span>

<span data-ttu-id="385bb-313">`-File`參數是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="385bb-313">The `-File` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="385bb-314">若只要取得檔案，請使用 `-File` 參數並省略 `-Directory` 參數。</span><span class="sxs-lookup"><span data-stu-id="385bb-314">To get only files, use the `-File` parameter and omit the `-Directory` parameter.</span></span> <span data-ttu-id="385bb-315">若要排除檔案，請使用 `-Directory` 參數並省略 `-File` 參數，或使用 `-Attributes` 參數。</span><span class="sxs-lookup"><span data-stu-id="385bb-315">To exclude files, use the `-Directory` parameter and omit the `-File` parameter, or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-316">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-316">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-317">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="385bb-317">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a><span data-ttu-id="385bb-318">Hidden \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="385bb-318">Hidden \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="385bb-319">只取得隱藏的檔案和目錄 (資料夾)。</span><span class="sxs-lookup"><span data-stu-id="385bb-319">Gets only hidden files and directories (folders).</span></span> <span data-ttu-id="385bb-320">根據預設， [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 只會取得非隱藏的專案。</span><span class="sxs-lookup"><span data-stu-id="385bb-320">By default, [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) gets only non-hidden items.</span></span>

<span data-ttu-id="385bb-321">`-Hidden`參數是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="385bb-321">The `-Hidden` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="385bb-322">若只要取得隱藏的專案，請使用 `-Hidden` 參數、其 `h` 或 `ah` 別名，或參數的 **隱藏** 值 `-Attributes` 。</span><span class="sxs-lookup"><span data-stu-id="385bb-322">To get only hidden items, use the `-Hidden` parameter, its `h` or `ah` aliases, or the **Hidden** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="385bb-323">若要排除隱藏的專案，請省略 `-Hidden` 參數或使用 `-Attributes` 參數。</span><span class="sxs-lookup"><span data-stu-id="385bb-323">To exclude hidden items, omit the `-Hidden` parameter or use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-324">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-324">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-325">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="385bb-325">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a><span data-ttu-id="385bb-326">ReadOnly \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="385bb-326">ReadOnly \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="385bb-327">只取得唯讀的檔案和目錄 (資料夾)。</span><span class="sxs-lookup"><span data-stu-id="385bb-327">Gets only read-only files and directories (folders).</span></span>

<span data-ttu-id="385bb-328">`-ReadOnly`參數是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="385bb-328">The `-ReadOnly` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="385bb-329">若只要取得唯讀專案，請使用參數 `-ReadOnly` 、其 `ar` 別名或參數的 **ReadOnly** 值 `-Attributes` 。</span><span class="sxs-lookup"><span data-stu-id="385bb-329">To get only read-only items, use the `-ReadOnly` parameter, its `ar` alias, or the **ReadOnly** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="385bb-330">若要排除唯讀專案，請使用 `-Attributes` 參數。</span><span class="sxs-lookup"><span data-stu-id="385bb-330">To exclude read-only items, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-331">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-331">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-332">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="385bb-332">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a><span data-ttu-id="385bb-333">System \<System.Management.Automation.SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="385bb-333">System \<System.Management.Automation.SwitchParameter\></span></span>

<span data-ttu-id="385bb-334">只取得系統檔案和目錄 (資料夾)。</span><span class="sxs-lookup"><span data-stu-id="385bb-334">Gets only system files and directories (folders).</span></span>

<span data-ttu-id="385bb-335">`-System`參數是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="385bb-335">The `-System` parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="385bb-336">若只要取得系統檔案和資料夾，請使用參數 `-System` 、其 `as` 別名或參數的 **系統** 值 `-Attributes` 。</span><span class="sxs-lookup"><span data-stu-id="385bb-336">To get only system files and folders, use the `-System` parameter, its `as` alias, or the **System** value of the `-Attributes` parameter.</span></span> <span data-ttu-id="385bb-337">若要排除系統檔案和資料夾，請使用 `-Attributes` 參數。</span><span class="sxs-lookup"><span data-stu-id="385bb-337">To exclude system files and folders, use the `-Attributes` parameter.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-338">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-338">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-339">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="385bb-339">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a><span data-ttu-id="385bb-340">NewerThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="385bb-340">NewerThan \<System.DateTime\></span></span>

<span data-ttu-id="385bb-341">`$True`當檔案的 `LastWriteTime` 值大於指定的日期時傳回。</span><span class="sxs-lookup"><span data-stu-id="385bb-341">Returns `$True` when the `LastWriteTime` value of a file is greater than the specified date.</span></span> <span data-ttu-id="385bb-342">否則，它會傳回 `$False`。</span><span class="sxs-lookup"><span data-stu-id="385bb-342">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="385bb-343">輸入 [datetime](/dotnet/api/system.datetime) 物件（例如， [取得日期](xref:Microsoft.PowerShell.Utility.Get-Date) Cmdlet 所傳回的物件），或輸入可轉換為 [DateTime](/dotnet/api/system.datetime) 物件的字串，例如 `"August 10, 2011 2:00 PM"` 。</span><span class="sxs-lookup"><span data-stu-id="385bb-343">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-344">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-344">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-345">Test-Path</span><span class="sxs-lookup"><span data-stu-id="385bb-345">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a><span data-ttu-id="385bb-346">OlderThan \<System.DateTime\></span><span class="sxs-lookup"><span data-stu-id="385bb-346">OlderThan \<System.DateTime\></span></span>

<span data-ttu-id="385bb-347">`$True`當檔案的 `LastWriteTime` 值小於指定的日期時傳回。</span><span class="sxs-lookup"><span data-stu-id="385bb-347">Returns `$True` when the `LastWriteTime` value of a file is less than the specified date.</span></span> <span data-ttu-id="385bb-348">否則，它會傳回 `$False`。</span><span class="sxs-lookup"><span data-stu-id="385bb-348">Otherwise, it returns `$False`.</span></span>

<span data-ttu-id="385bb-349">輸入 [datetime](/dotnet/api/system.datetime) 物件（例如， [取得日期](xref:Microsoft.PowerShell.Utility.Get-Date) Cmdlet 所傳回的物件），或輸入可轉換為 [DateTime](/dotnet/api/system.datetime) 物件的字串，例如 `"August 10, 2011 2:00 PM"` 。</span><span class="sxs-lookup"><span data-stu-id="385bb-349">Enter a [DateTime](/dotnet/api/system.datetime) object, such as one that the [Get-Date](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet returns, or a string that can be converted to a [DateTime](/dotnet/api/system.datetime) object, such as `"August 10, 2011 2:00 PM"`.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-350">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-350">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-351">Test-Path</span><span class="sxs-lookup"><span data-stu-id="385bb-351">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a><span data-ttu-id="385bb-352">Stream \<System.String\></span><span class="sxs-lookup"><span data-stu-id="385bb-352">Stream \<System.String\></span></span>

<span data-ttu-id="385bb-353">管理替代資料流。</span><span class="sxs-lookup"><span data-stu-id="385bb-353">Manages alternate data streams.</span></span> <span data-ttu-id="385bb-354">輸入資料流名稱。</span><span class="sxs-lookup"><span data-stu-id="385bb-354">Enter the stream name.</span></span> <span data-ttu-id="385bb-355">只有在檔案系統磁片磁碟機中的 [Get 專案](xref:Microsoft.PowerShell.Management.Get-Item) 和 [移除專案](xref:Microsoft.PowerShell.Management.Remove-Item) 命令中，才允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="385bb-355">Wildcards are permitted only in [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) for and [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item) commands in a file system drive.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-356">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-356">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-357">Add-Content</span><span class="sxs-lookup"><span data-stu-id="385bb-357">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="385bb-358">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="385bb-358">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="385bb-359">Get-Item</span><span class="sxs-lookup"><span data-stu-id="385bb-359">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="385bb-360">Get-Content</span><span class="sxs-lookup"><span data-stu-id="385bb-360">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="385bb-361">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="385bb-361">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="385bb-362">Set-Content</span><span class="sxs-lookup"><span data-stu-id="385bb-362">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a><span data-ttu-id="385bb-363">Raw \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="385bb-363">Raw \<SwitchParameter\></span></span>

<span data-ttu-id="385bb-364">忽略新行字元。</span><span class="sxs-lookup"><span data-stu-id="385bb-364">Ignores newline characters.</span></span> <span data-ttu-id="385bb-365">以單一項目形式傳回內容。</span><span class="sxs-lookup"><span data-stu-id="385bb-365">Returns contents as a single item.</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-366">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-366">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-367">Get-Content</span><span class="sxs-lookup"><span data-stu-id="385bb-367">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a><span data-ttu-id="385bb-368">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="385bb-368">ItemType \<String\></span></span>

<span data-ttu-id="385bb-369">此參數可讓您指定要建立的專案 tye `New-Item`</span><span class="sxs-lookup"><span data-stu-id="385bb-369">This parameter allows you to specify the tye of item to create with `New-Item`</span></span>

<span data-ttu-id="385bb-370">此參數的可用值取決於您目前使用的提供者。</span><span class="sxs-lookup"><span data-stu-id="385bb-370">The available values of this parameter depend on the current provider you are using.</span></span>

<span data-ttu-id="385bb-371">在 `FileSystem` 磁片磁碟機中，允許下列值：</span><span class="sxs-lookup"><span data-stu-id="385bb-371">In a `FileSystem` drive, the following values are allowed:</span></span>

- <span data-ttu-id="385bb-372">檔案</span><span class="sxs-lookup"><span data-stu-id="385bb-372">File</span></span>
- <span data-ttu-id="385bb-373">目錄</span><span class="sxs-lookup"><span data-stu-id="385bb-373">Directory</span></span>
- <span data-ttu-id="385bb-374">>symboliclink</span><span class="sxs-lookup"><span data-stu-id="385bb-374">SymbolicLink</span></span>
- <span data-ttu-id="385bb-375">接合</span><span class="sxs-lookup"><span data-stu-id="385bb-375">Junction</span></span>
- <span data-ttu-id="385bb-376">硬</span><span class="sxs-lookup"><span data-stu-id="385bb-376">HardLink</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="385bb-377">支援的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="385bb-377">Cmdlets supported</span></span>

- [<span data-ttu-id="385bb-378">New-Item</span><span class="sxs-lookup"><span data-stu-id="385bb-378">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="385bb-379">使用管線</span><span class="sxs-lookup"><span data-stu-id="385bb-379">Using the pipeline</span></span>

<span data-ttu-id="385bb-380">提供者 Cmdlet 接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="385bb-380">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="385bb-381">您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。</span><span class="sxs-lookup"><span data-stu-id="385bb-381">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="385bb-382">若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。</span><span class="sxs-lookup"><span data-stu-id="385bb-382">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="385bb-383">取得說明</span><span class="sxs-lookup"><span data-stu-id="385bb-383">Getting help</span></span>

<span data-ttu-id="385bb-384">從 Windows PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁碟機中的行為方式。</span><span class="sxs-lookup"><span data-stu-id="385bb-384">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="385bb-385">若要取得針對檔案系統磁片磁碟機自訂的說明主題，請在檔案系統磁片磁碟機中執行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 的參數來指定檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="385bb-385">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a><span data-ttu-id="385bb-386">另請參閱</span><span class="sxs-lookup"><span data-stu-id="385bb-386">See also</span></span>

[<span data-ttu-id="385bb-387">about_Providers</span><span class="sxs-lookup"><span data-stu-id="385bb-387">about_Providers</span></span>](../About/about_Providers.md)

