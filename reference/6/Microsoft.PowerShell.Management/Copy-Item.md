---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: 0aeebac75c5a84fd78056954d7178de1dbac1460
ms.sourcegitcommit: 33ac34789e86ffb4e7e69453ae38fc0bd24933dd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "93206163"
---
# <span data-ttu-id="dc308-103">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="dc308-103">Copy-Item</span></span>

## <span data-ttu-id="dc308-104">概要</span><span class="sxs-lookup"><span data-stu-id="dc308-104">SYNOPSIS</span></span>
<span data-ttu-id="dc308-105">將項目從某個位置複製到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="dc308-105">Copies an item from one location to another.</span></span>

## <span data-ttu-id="dc308-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dc308-106">SYNTAX</span></span>

### <span data-ttu-id="dc308-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="dc308-107">Path (Default)</span></span>

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="dc308-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="dc308-108">LiteralPath</span></span>

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

## <span data-ttu-id="dc308-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc308-109">DESCRIPTION</span></span>

<span data-ttu-id="dc308-110">`Copy-Item`Cmdlet 會將專案從某個位置複製到相同命名空間中的另一個位置。</span><span class="sxs-lookup"><span data-stu-id="dc308-110">The `Copy-Item` cmdlet copies an item from one location to another location in the same namespace.</span></span>
<span data-ttu-id="dc308-111">比方說，它可以將檔案複製到資料夾，但它無法將檔案複製到憑證磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="dc308-111">For instance, it can copy a file to a folder, but it can't copy a file to a certificate drive.</span></span>

<span data-ttu-id="dc308-112">此 Cmdlet 不會剪下或刪除複製的專案。</span><span class="sxs-lookup"><span data-stu-id="dc308-112">This cmdlet doesn't cut or delete the items being copied.</span></span> <span data-ttu-id="dc308-113">Cmdlet 可以複製的特定專案需視公開專案的 PowerShell 提供者而定。</span><span class="sxs-lookup"><span data-stu-id="dc308-113">The particular items that the cmdlet can copy depend on the PowerShell provider that exposes the item.</span></span> <span data-ttu-id="dc308-114">例如，它可以在檔案系統磁片磁碟機中複製檔案和目錄，以及在登錄磁片磁碟機中複製登錄機碼和專案。</span><span class="sxs-lookup"><span data-stu-id="dc308-114">For instance, it can copy files and directories in a file system drive and registry keys and entries in the registry drive.</span></span>

<span data-ttu-id="dc308-115">這個 Cmdlet 可以在同一個命令中複製及重新命名專案。</span><span class="sxs-lookup"><span data-stu-id="dc308-115">This cmdlet can copy and rename items in the same command.</span></span> <span data-ttu-id="dc308-116">若要重新命名專案，請在 **Destination** 參數的值中輸入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="dc308-116">To rename an item, enter the new name in the value of the **Destination** parameter.</span></span> <span data-ttu-id="dc308-117">若要重新命名專案但不復制它，請使用 `Rename-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dc308-117">To rename an item and not copy it, use the `Rename-Item` cmdlet.</span></span>

## <span data-ttu-id="dc308-118">範例</span><span class="sxs-lookup"><span data-stu-id="dc308-118">EXAMPLES</span></span>

### <span data-ttu-id="dc308-119">範例1：將檔案複製到指定的目錄</span><span class="sxs-lookup"><span data-stu-id="dc308-119">Example 1: Copy a file to the specified directory</span></span>

<span data-ttu-id="dc308-120">此範例會將檔案複製 `mar1604.log.txt` 到 `C:\Presentation` 目錄。</span><span class="sxs-lookup"><span data-stu-id="dc308-120">This example copies the `mar1604.log.txt` file to the `C:\Presentation` directory.</span></span> <span data-ttu-id="dc308-121">不會刪除原始檔案。</span><span class="sxs-lookup"><span data-stu-id="dc308-121">The original file isn't deleted.</span></span>

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### <span data-ttu-id="dc308-122">範例2：將目錄內容複寫到現有的目錄</span><span class="sxs-lookup"><span data-stu-id="dc308-122">Example 2: Copy directory contents to an existing directory</span></span>

<span data-ttu-id="dc308-123">此範例會將目錄的內容複寫 `C:\Logfiles` 到現有的 `C:\Drawings` 目錄。</span><span class="sxs-lookup"><span data-stu-id="dc308-123">This example copies the contents of the `C:\Logfiles` directory into the existing `C:\Drawings` directory.</span></span> <span data-ttu-id="dc308-124">`Logfiles`不會複製目錄。</span><span class="sxs-lookup"><span data-stu-id="dc308-124">The `Logfiles` directory isn't copied.</span></span>

<span data-ttu-id="dc308-125">如果 `Logfiles` 目錄包含子目錄中的檔案，則會複製這些子目錄的檔案樹狀結構不變。</span><span class="sxs-lookup"><span data-stu-id="dc308-125">If the `Logfiles` directory contains files in subdirectories, those subdirectories are copied with their file trees intact.</span></span> <span data-ttu-id="dc308-126">依預設， **Container** 參數會設定為 **True** ，以保留目錄結構。</span><span class="sxs-lookup"><span data-stu-id="dc308-126">By default, the **Container** parameter is set to **True** , which preserves the directory structure.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> <span data-ttu-id="dc308-127">如果您需要 `Logfiles` 在複本中包含目錄，請 `\*` 從 **路徑** 中移除。</span><span class="sxs-lookup"><span data-stu-id="dc308-127">If you need to include the `Logfiles` directory in the copy, remove the `\*` from the **Path** .</span></span>
> <span data-ttu-id="dc308-128">例如：</span><span class="sxs-lookup"><span data-stu-id="dc308-128">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### <span data-ttu-id="dc308-129">範例3：將目錄和內容複寫到新的目錄</span><span class="sxs-lookup"><span data-stu-id="dc308-129">Example 3: Copy directory and contents to a new directory</span></span>

<span data-ttu-id="dc308-130">此範例會複製 `C:\Logfiles` 來原始目錄的內容，並建立新的目的地目錄。</span><span class="sxs-lookup"><span data-stu-id="dc308-130">This example copies the contents of the `C:\Logfiles` source directory and creates a new destination directory.</span></span> <span data-ttu-id="dc308-131">新的目的地目錄 `\Logs` 是在中建立 `C:\Drawings` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-131">The new destination directory, `\Logs` is created in `C:\Drawings`.</span></span>

<span data-ttu-id="dc308-132">若要包含來原始目錄的名稱，請複製到現有的目的地目錄，如 **範例 2** 所示。</span><span class="sxs-lookup"><span data-stu-id="dc308-132">To include the source directory's name, copy to an existing destination directory as shown in **Example 2** .</span></span> <span data-ttu-id="dc308-133">或者，將新的目的地目錄命名為與來原始目錄相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="dc308-133">Or, name the new destination directory with the same as the source directory.</span></span>

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> <span data-ttu-id="dc308-134">如果 **路徑** 包含 `\*` ，所有目錄的檔案內容（包括子目錄樹狀目錄）都會複製到新的目的地目錄。</span><span class="sxs-lookup"><span data-stu-id="dc308-134">If the **Path** includes `\*`, all the directory's file contents, including the subdirectory trees, are copied to the new destination directory.</span></span> <span data-ttu-id="dc308-135">例如：</span><span class="sxs-lookup"><span data-stu-id="dc308-135">For example:</span></span>
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### <span data-ttu-id="dc308-136">範例4：將檔案複製到指定的目錄，並將檔案重新命名</span><span class="sxs-lookup"><span data-stu-id="dc308-136">Example 4: Copy a file to the specified directory and rename the file</span></span>

<span data-ttu-id="dc308-137">此範例會使用 `Copy-Item` Cmdlet 將 `Get-Widget.ps1` 腳本從 `\\Server01\Share` 目錄複寫到 `\\Server12\ScriptArchive` 目錄。</span><span class="sxs-lookup"><span data-stu-id="dc308-137">This example uses the `Copy-Item` cmdlet to copy the `Get-Widget.ps1` script from the `\\Server01\Share` directory to the `\\Server12\ScriptArchive` directory.</span></span> <span data-ttu-id="dc308-138">在複製作業過程中，命令會將專案名稱從變更 `Get-Widget.ps1` 為 `Get-Widget.ps1.txt` ，因此可以附加至電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="dc308-138">As part of the copy operation, the command changes the item name from `Get-Widget.ps1` to `Get-Widget.ps1.txt`, so it can be attached to email messages.</span></span>

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### <span data-ttu-id="dc308-139">範例5：將檔案複製到遠端電腦</span><span class="sxs-lookup"><span data-stu-id="dc308-139">Example 5: Copy a file to a remote computer</span></span>

<span data-ttu-id="dc308-140">使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-140">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="dc308-141">`Copy-Item`Cmdlet 會 `test.log` `D:\Folder001` `C:\Folder001_Copy` 使用儲存在變數中的會話資訊，從資料夾將資料夾複製到遠端電腦上的資料夾 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-141">The `Copy-Item` cmdlet copies `test.log` from the `D:\Folder001` folder to the `C:\Folder001_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="dc308-142">不會刪除原始檔案。</span><span class="sxs-lookup"><span data-stu-id="dc308-142">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### <span data-ttu-id="dc308-143">範例6：將資料夾複製到遠端電腦</span><span class="sxs-lookup"><span data-stu-id="dc308-143">Example 6: Copy a folder to a remote computer</span></span>

<span data-ttu-id="dc308-144">使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-144">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="dc308-145">此 `Copy-Item` Cmdlet 會 `D:\Folder002` `C:\Folder002_Copy` 使用儲存在變數中的會話資訊，將資料夾複製到遠端電腦上的目錄 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-145">The `Copy-Item` cmdlet copies the `D:\Folder002` folder to the `C:\Folder002_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="dc308-146">任何子資料夾或檔案都不會在不使用 **遞迴** 參數的情況下複製。</span><span class="sxs-lookup"><span data-stu-id="dc308-146">Any subfolders or files are not copied without using the **Recurse** switch.</span></span>
<span data-ttu-id="dc308-147">`Folder002_Copy`如果資料夾還不存在，此作業會建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="dc308-147">The operation creates the `Folder002_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### <span data-ttu-id="dc308-148">範例7：以遞迴方式將資料夾的整個內容複寫到遠端電腦</span><span class="sxs-lookup"><span data-stu-id="dc308-148">Example 7: Recursively copy the entire contents of a folder to a remote computer</span></span>

<span data-ttu-id="dc308-149">使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-149">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="dc308-150">此 `Copy-Item` Cmdlet 會 `D:\Folder003` `C:\Folder003_Copy` 使用儲存在變數中的會話資訊，將資料夾中的整個內容複寫到遠端電腦上的目錄 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-150">The `Copy-Item` cmdlet copies the entire contents from the `D:\Folder003` folder to the `C:\Folder003_Copy` directory on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="dc308-151">這些子資料夾的檔案樹狀結構會原封不動地複製。</span><span class="sxs-lookup"><span data-stu-id="dc308-151">The subfolders are copied with their file trees intact.</span></span> <span data-ttu-id="dc308-152">`Folder003_Copy`如果資料夾還不存在，此作業會建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="dc308-152">The operation creates the `Folder003_Copy` folder if it doesn't already exist.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### <span data-ttu-id="dc308-153">範例8：將檔案複製到遠端電腦，然後重新命名檔案</span><span class="sxs-lookup"><span data-stu-id="dc308-153">Example 8: Copy a file to a remote computer and then rename the file</span></span>

<span data-ttu-id="dc308-154">使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-154">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="dc308-155">`Copy-Item`Cmdlet 會 `scriptingexample.ps1` `D:\Folder004` `C:\Folder004_Copy` 使用儲存在變數中的會話資訊，從資料夾將資料夾複製到遠端電腦上的資料夾 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-155">The `Copy-Item` cmdlet copies `scriptingexample.ps1` from the `D:\Folder004` folder to the `C:\Folder004_Copy` folder on the remote computer using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="dc308-156">在複製作業過程中，命令會將專案名稱從變更 `scriptingexample.ps1` 為 `scriptingexample_copy.ps1` ，因此可以附加至電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="dc308-156">As part of the copy operation, the command changes the item name from `scriptingexample.ps1` to `scriptingexample_copy.ps1`, so it can be attached to email messages.</span></span> <span data-ttu-id="dc308-157">不會刪除原始檔案。</span><span class="sxs-lookup"><span data-stu-id="dc308-157">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### <span data-ttu-id="dc308-158">範例9：將遠端檔案複製到本機電腦</span><span class="sxs-lookup"><span data-stu-id="dc308-158">Example 9: Copy a remote file to the local computer</span></span>

<span data-ttu-id="dc308-159">使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-159">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="dc308-160">`Copy-Item`Cmdlet 會 `test.log` `C:\MyRemoteData\` `D:\MyLocalData` 使用儲存在變數中的會話資訊，從遠端複製到本機資料夾 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-160">The `Copy-Item` cmdlet copies `test.log` from the remote `C:\MyRemoteData\` to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="dc308-161">不會刪除原始檔案。</span><span class="sxs-lookup"><span data-stu-id="dc308-161">The original file isn't deleted.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="dc308-162">範例10：將遠端資料夾的整個內容複寫到本機電腦</span><span class="sxs-lookup"><span data-stu-id="dc308-162">Example 10: Copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="dc308-163">使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-163">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="dc308-164">此 `Copy-Item` Cmdlet 會 `C:\MyRemoteData\scripts` `D:\MyLocalData` 使用儲存在變數中的會話資訊，將遠端資料夾中的整個內容複寫到本機資料夾 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-164">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="dc308-165">如果 scripts 資料夾包含子資料夾中的檔案，則會複製這些子資料夾的檔案樹狀結構不變。</span><span class="sxs-lookup"><span data-stu-id="dc308-165">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### <span data-ttu-id="dc308-166">範例11：以遞迴方式將遠端資料夾的整個內容複寫到本機電腦</span><span class="sxs-lookup"><span data-stu-id="dc308-166">Example 11: Recursively copy the entire contents of a remote folder to the local computer</span></span>

<span data-ttu-id="dc308-167">使用的認證，建立名為 **Server01** 的遠端電腦的會話 `Contoso\User01` ，並將結果儲存在名為的變數中 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-167">A session is created to the remote computer named **Server01** with the credential of `Contoso\User01` and stores the results in the variable named `$Session`.</span></span>

<span data-ttu-id="dc308-168">此 `Copy-Item` Cmdlet 會 `C:\MyRemoteData\scripts` `D:\MyLocalData\scripts` 使用儲存在變數中的會話資訊，將遠端資料夾中的整個內容複寫到本機資料夾 `$Session` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-168">The `Copy-Item` cmdlet copies the entire contents from the remote `C:\MyRemoteData\scripts` folder to the local `D:\MyLocalData\scripts` folder using the session information stored in the `$Session` variable.</span></span> <span data-ttu-id="dc308-169">因為使用了 **遞迴** 參數，所以作業會建立腳本資料夾（如果尚未存在）。</span><span class="sxs-lookup"><span data-stu-id="dc308-169">Because the **Recurse** parameter is used, the operation creates the scripts folder if it doesn't already exist.</span></span> <span data-ttu-id="dc308-170">如果 scripts 資料夾包含子資料夾中的檔案，則會複製這些子資料夾的檔案樹狀結構不變。</span><span class="sxs-lookup"><span data-stu-id="dc308-170">If the scripts folder contains files in subfolders, those subfolders are copied with their file trees intact.</span></span>

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### <span data-ttu-id="dc308-171">範例12：以遞迴方式將檔案從資料夾樹狀結構複製到目前的資料夾</span><span class="sxs-lookup"><span data-stu-id="dc308-171">Example 12: Recursively copy files from a folder tree into the current folder</span></span>

<span data-ttu-id="dc308-172">此範例示範如何將多層的資料夾結構中的檔案複製到單一的一般資料夾中。</span><span class="sxs-lookup"><span data-stu-id="dc308-172">This example shows how to copy files from a multilevel folder structure into a single flat folder.</span></span>
<span data-ttu-id="dc308-173">前三個命令會顯示現有的資料夾結構，以及兩個檔案的內容，這兩個都是名稱 `file3.txt` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-173">The first three commands show the existing folder structure and the contents of two files, both names `file3.txt`.</span></span>

```powershell
PS C:\temp\test> (Get-ChildItem C:\temp\tree -Recurse).FullName
C:\temp\tree\subfolder
C:\temp\tree\file1.txt
C:\temp\tree\file2.txt
C:\temp\tree\file3.txt
C:\temp\tree\subfolder\file3.txt
C:\temp\tree\subfolder\file4.txt
C:\temp\tree\subfolder\file5.txt

PS C:\temp\test> Get-Content C:\temp\tree\file3.txt
This is file3.txt in the root folder

PS C:\temp\test> Get-Content C:\temp\tree\subfolder\file3.txt
This is file3.txt in the subfolder

PS C:\temp\test> Copy-Item -Path C:\temp\tree -Filter *.txt -Recurse -Container:$false
PS C:\temp\test> (Get-ChildItem . -Recurse).FullName
C:\temp\test\subfolder
C:\temp\test\file1.txt
C:\temp\test\file2.txt
C:\temp\test\file3.txt
C:\temp\test\file4.txt
C:\temp\test\file5.txt

PS C:\temp\test> Get-Content .\file3.txt
This is file3.txt in the subfolder
```

<span data-ttu-id="dc308-174">`Copy-Item`Cmdlet 的 **容器** 參數設定為 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-174">The `Copy-Item` cmdlet has the **Container** parameter set to `$false`.</span></span> <span data-ttu-id="dc308-175">這會導致複製源資料夾的內容，但不會保留資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="dc308-175">This causes the contents of the source folder to be copied but does not preserve the folder structure.</span></span> <span data-ttu-id="dc308-176">請注意，在目的資料夾中會覆寫具有相同名稱的檔案。</span><span class="sxs-lookup"><span data-stu-id="dc308-176">Notice that files with the same name are overwritten in the destination folder.</span></span>

## <span data-ttu-id="dc308-177">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dc308-177">PARAMETERS</span></span>

### <span data-ttu-id="dc308-178">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dc308-178">-Confirm</span></span>

<span data-ttu-id="dc308-179">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="dc308-179">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="dc308-180">-Container</span><span class="sxs-lookup"><span data-stu-id="dc308-180">-Container</span></span>

<span data-ttu-id="dc308-181">指出此 Cmdlet 會在複製作業期間保留容器物件。</span><span class="sxs-lookup"><span data-stu-id="dc308-181">Indicates that this cmdlet preserves container objects during the copy operation.</span></span> <span data-ttu-id="dc308-182">依預設， **Container** 參數會設定為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="dc308-182">By default, the **Container** parameter is set to **True** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc308-183">-Credential</span><span class="sxs-lookup"><span data-stu-id="dc308-183">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="dc308-184">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="dc308-184">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="dc308-185">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="dc308-185">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="dc308-186">-Destination</span><span class="sxs-lookup"><span data-stu-id="dc308-186">-Destination</span></span>

<span data-ttu-id="dc308-187">指定新位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="dc308-187">Specifies the path to the new location.</span></span> <span data-ttu-id="dc308-188">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="dc308-188">The default is the current directory.</span></span>

<span data-ttu-id="dc308-189">若要重新命名複製的專案，請在 **Destination** 參數的值中指定新名稱。</span><span class="sxs-lookup"><span data-stu-id="dc308-189">To rename the item being copied, specify a new name in the value of the **Destination** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dc308-190">-Exclude</span><span class="sxs-lookup"><span data-stu-id="dc308-190">-Exclude</span></span>

<span data-ttu-id="dc308-191">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="dc308-191">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="dc308-192">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="dc308-192">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="dc308-193">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="dc308-193">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="dc308-194">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="dc308-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="dc308-195">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-195">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="dc308-196">-Filter</span><span class="sxs-lookup"><span data-stu-id="dc308-196">-Filter</span></span>

<span data-ttu-id="dc308-197">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="dc308-197">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="dc308-198">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="dc308-198">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="dc308-199">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="dc308-199">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="dc308-200">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="dc308-200">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span>

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

### <span data-ttu-id="dc308-201">-Force</span><span class="sxs-lookup"><span data-stu-id="dc308-201">-Force</span></span>

<span data-ttu-id="dc308-202">指出此 Cmdlet 會複製無法以其他方式變更的專案，例如複製唯讀檔案或別名。</span><span class="sxs-lookup"><span data-stu-id="dc308-202">Indicates that this cmdlet copies items that can't otherwise be changed, such as copying over a read-only file or alias.</span></span>

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

### <span data-ttu-id="dc308-203">-FromSession</span><span class="sxs-lookup"><span data-stu-id="dc308-203">-FromSession</span></span>

<span data-ttu-id="dc308-204">指定要從中複製遠端檔案的 **PSSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="dc308-204">Specifies the **PSSession** object from which a remote file is being copied.</span></span> <span data-ttu-id="dc308-205">當您使用這個參數時， **Path** 和 **LiteralPath** 參數會參考遠端電腦上的本機路徑。</span><span class="sxs-lookup"><span data-stu-id="dc308-205">When you use this parameter, the **Path** and **LiteralPath** parameters refer to the local path on the remote machine.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc308-206">-Include</span><span class="sxs-lookup"><span data-stu-id="dc308-206">-Include</span></span>

<span data-ttu-id="dc308-207">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="dc308-207">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="dc308-208">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="dc308-208">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="dc308-209">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="dc308-209">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="dc308-210">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="dc308-210">Wildcard characters are permitted.</span></span> <span data-ttu-id="dc308-211">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-211">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="dc308-212">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="dc308-212">-LiteralPath</span></span>

<span data-ttu-id="dc308-213">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="dc308-213">Specifies a path to one or more locations.</span></span> <span data-ttu-id="dc308-214">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="dc308-214">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="dc308-215">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="dc308-215">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="dc308-216">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="dc308-216">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="dc308-217">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="dc308-217">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="dc308-218">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="dc308-218">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="dc308-219">-PassThru</span><span class="sxs-lookup"><span data-stu-id="dc308-219">-PassThru</span></span>

<span data-ttu-id="dc308-220">傳回代表您正在使用之專案的物件。</span><span class="sxs-lookup"><span data-stu-id="dc308-220">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="dc308-221">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="dc308-221">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="dc308-222">-Path</span><span class="sxs-lookup"><span data-stu-id="dc308-222">-Path</span></span>

<span data-ttu-id="dc308-223">以字串陣列指定要複製之專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="dc308-223">Specifies, as a string array, the path to the items to copy.</span></span> <span data-ttu-id="dc308-224">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="dc308-224">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="dc308-225">-Recurse</span><span class="sxs-lookup"><span data-stu-id="dc308-225">-Recurse</span></span>

<span data-ttu-id="dc308-226">指出此 Cmdlet 會執行遞迴複製。</span><span class="sxs-lookup"><span data-stu-id="dc308-226">Indicates that this cmdlet does a recursive copy.</span></span>

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

### <span data-ttu-id="dc308-227">-ToSession</span><span class="sxs-lookup"><span data-stu-id="dc308-227">-ToSession</span></span>

<span data-ttu-id="dc308-228">指定要將遠端檔案複製到其中的 **PSSession** 物件。</span><span class="sxs-lookup"><span data-stu-id="dc308-228">Specifies the **PSSession** object to which a remote file is being copied.</span></span> <span data-ttu-id="dc308-229">當您使用此參數時， **目的地** 參數會參考遠端電腦上的本機路徑。</span><span class="sxs-lookup"><span data-stu-id="dc308-229">When you use this parameter, the **Destination** parameter refers to the local path on the remote machine.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc308-230">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dc308-230">-WhatIf</span></span>

<span data-ttu-id="dc308-231">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="dc308-231">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="dc308-232">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dc308-232">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="dc308-233">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dc308-233">CommonParameters</span></span>

<span data-ttu-id="dc308-234">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="dc308-234">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="dc308-235">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="dc308-235">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dc308-236">輸入</span><span class="sxs-lookup"><span data-stu-id="dc308-236">INPUTS</span></span>

### <span data-ttu-id="dc308-237">System.String</span><span class="sxs-lookup"><span data-stu-id="dc308-237">System.String</span></span>

<span data-ttu-id="dc308-238">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="dc308-238">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="dc308-239">輸出</span><span class="sxs-lookup"><span data-stu-id="dc308-239">OUTPUTS</span></span>

### <span data-ttu-id="dc308-240">無或代表複製專案的物件</span><span class="sxs-lookup"><span data-stu-id="dc308-240">None or an object representing the copied item</span></span>

<span data-ttu-id="dc308-241">當您使用 **PassThru** 參數時，此 Cmdlet 會傳回代表所複製專案的物件。</span><span class="sxs-lookup"><span data-stu-id="dc308-241">When you use the **PassThru** parameter, this cmdlet returns an object that represents the copied item.</span></span> <span data-ttu-id="dc308-242">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="dc308-242">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="dc308-243">注意</span><span class="sxs-lookup"><span data-stu-id="dc308-243">NOTES</span></span>

<span data-ttu-id="dc308-244">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="dc308-244">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="dc308-245">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="dc308-245">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="dc308-246">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="dc308-246">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="dc308-247">相關連結</span><span class="sxs-lookup"><span data-stu-id="dc308-247">RELATED LINKS</span></span>

[<span data-ttu-id="dc308-248">about_Providers</span><span class="sxs-lookup"><span data-stu-id="dc308-248">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="dc308-249">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="dc308-249">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="dc308-250">Get-Item</span><span class="sxs-lookup"><span data-stu-id="dc308-250">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="dc308-251">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="dc308-251">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="dc308-252">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="dc308-252">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="dc308-253">Move-Item</span><span class="sxs-lookup"><span data-stu-id="dc308-253">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="dc308-254">New-Item</span><span class="sxs-lookup"><span data-stu-id="dc308-254">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="dc308-255">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="dc308-255">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="dc308-256">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="dc308-256">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="dc308-257">Set-Item</span><span class="sxs-lookup"><span data-stu-id="dc308-257">Set-Item</span></span>](Set-Item.md)
