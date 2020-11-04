---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 07f8da5e6101b1d9bb1971b3c77b9747c0080a23
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201527"
---
# <span data-ttu-id="90c1d-103">Get-Item</span><span class="sxs-lookup"><span data-stu-id="90c1d-103">Get-Item</span></span>

## <span data-ttu-id="90c1d-104">概要</span><span class="sxs-lookup"><span data-stu-id="90c1d-104">SYNOPSIS</span></span>
<span data-ttu-id="90c1d-105">取得指定位置的項目。</span><span class="sxs-lookup"><span data-stu-id="90c1d-105">Gets the item at the specified location.</span></span>

## <span data-ttu-id="90c1d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="90c1d-106">SYNTAX</span></span>

### <span data-ttu-id="90c1d-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="90c1d-107">Path (Default)</span></span>

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="90c1d-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="90c1d-108">LiteralPath</span></span>

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="90c1d-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="90c1d-109">DESCRIPTION</span></span>

<span data-ttu-id="90c1d-110">`Get-Item`Cmdlet 會取得指定位置的專案。</span><span class="sxs-lookup"><span data-stu-id="90c1d-110">The `Get-Item` cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="90c1d-111">除非您使用萬用字元 (`*`) 來要求專案的所有內容，否則它不會在位置取得專案的內容。</span><span class="sxs-lookup"><span data-stu-id="90c1d-111">It doesn't get the contents of the item at the location unless you use a wildcard character (`*`) to request all the contents of the item.</span></span>

<span data-ttu-id="90c1d-112">PowerShell 提供者會使用此 Cmdlet 來流覽不同類型的資料存放區。</span><span class="sxs-lookup"><span data-stu-id="90c1d-112">This cmdlet is used by PowerShell providers to navigate through different types of data stores.</span></span>

## <span data-ttu-id="90c1d-113">範例</span><span class="sxs-lookup"><span data-stu-id="90c1d-113">EXAMPLES</span></span>

### <span data-ttu-id="90c1d-114">範例1：取得當前目錄</span><span class="sxs-lookup"><span data-stu-id="90c1d-114">Example 1: Get the current directory</span></span>

<span data-ttu-id="90c1d-115">這個範例會取得當前目錄。</span><span class="sxs-lookup"><span data-stu-id="90c1d-115">This example gets the current directory.</span></span> <span data-ttu-id="90c1d-116">點 ( '. ') 代表目前位置的專案， (不是其內容) 。</span><span class="sxs-lookup"><span data-stu-id="90c1d-116">The dot ('.') represents the item at the current location (not its contents).</span></span>

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### <span data-ttu-id="90c1d-117">範例2：取得目前目錄中的所有專案</span><span class="sxs-lookup"><span data-stu-id="90c1d-117">Example 2: Get all the items in the current directory</span></span>

<span data-ttu-id="90c1d-118">這個範例會取得目前目錄中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="90c1d-118">This example gets all the items in the current directory.</span></span> <span data-ttu-id="90c1d-119">萬用字元 (`*`) 代表目前專案的所有內容。</span><span class="sxs-lookup"><span data-stu-id="90c1d-119">The wildcard character (`*`) represents all the contents of the current item.</span></span>

```powershell
Get-Item *
```

```output
Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006   9:29 AM            Logs
d----         7/26/2006   9:26 AM            Recs
-a---         7/26/2006   9:28 AM         80 date.csv
-a---         7/26/2006  10:01 AM         30 filenoext
-a---         7/26/2006   9:30 AM      11472 process.doc
-a---         7/14/2006  10:47 AM         30 test.txt
```

### <span data-ttu-id="90c1d-120">範例3：取得磁片磁碟機的目前的目錄</span><span class="sxs-lookup"><span data-stu-id="90c1d-120">Example 3: Get the current directory of a drive</span></span>

<span data-ttu-id="90c1d-121">此範例會取得磁片磁碟機的目前的目錄 `C:` 。</span><span class="sxs-lookup"><span data-stu-id="90c1d-121">This example gets the current directory of the `C:` drive.</span></span> <span data-ttu-id="90c1d-122">抓取的物件僅代表目錄，而非其內容。</span><span class="sxs-lookup"><span data-stu-id="90c1d-122">The object that is retrieved represents only the directory, not its contents.</span></span>

```powershell
Get-Item C:\
```

### <span data-ttu-id="90c1d-123">範例4：取得指定磁片磁碟機中的專案</span><span class="sxs-lookup"><span data-stu-id="90c1d-123">Example 4: Get items in the specified drive</span></span>

<span data-ttu-id="90c1d-124">此範例會取得磁片磁碟機中的專案 `C:` 。</span><span class="sxs-lookup"><span data-stu-id="90c1d-124">This example gets the items in the `C:` drive.</span></span> <span data-ttu-id="90c1d-125">萬用字元 (`*`) 代表容器中的所有專案，而不只是容器。</span><span class="sxs-lookup"><span data-stu-id="90c1d-125">The wildcard character (`*`) represents all the items in the container, not just the container.</span></span>

```powershell
Get-Item C:\*
```

<span data-ttu-id="90c1d-126">在 PowerShell 中，使用單一星號 (`*`) 來取得內容，而不是傳統 `*.*` 。</span><span class="sxs-lookup"><span data-stu-id="90c1d-126">In PowerShell, use a single asterisk (`*`) to get contents, instead of the traditional `*.*`.</span></span> <span data-ttu-id="90c1d-127">格式會以文字形式來解讀，因此 `*.*` 不會在沒有點的情況下抓取目錄或檔案名。</span><span class="sxs-lookup"><span data-stu-id="90c1d-127">The format is interpreted literally, so `*.*` wouldn't retrieve directories or filenames without a dot.</span></span>

### <span data-ttu-id="90c1d-128">範例5：取得指定之目錄中的屬性</span><span class="sxs-lookup"><span data-stu-id="90c1d-128">Example 5: Get a property in the specified directory</span></span>

<span data-ttu-id="90c1d-129">這個範例會取得目錄的 **LastAccessTime** 屬性 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="90c1d-129">This example gets the **LastAccessTime** property of the `C:\Windows` directory.</span></span> <span data-ttu-id="90c1d-130">**LastAccessTime** 只是檔案系統目錄的一個屬性。</span><span class="sxs-lookup"><span data-stu-id="90c1d-130">**LastAccessTime** is just one property of file system directories.</span></span> <span data-ttu-id="90c1d-131">若要查看目錄的所有屬性，請輸入 `(Get-Item <directory-name>) | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="90c1d-131">To see all the properties of a directory, type `(Get-Item <directory-name>) | Get-Member`.</span></span>

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### <span data-ttu-id="90c1d-132">範例6：顯示登錄機碼的內容</span><span class="sxs-lookup"><span data-stu-id="90c1d-132">Example 6: Show the contents of a registry key</span></span>

<span data-ttu-id="90c1d-133">此範例會顯示 **Microsoft PowerShell** 登錄機碼的內容。</span><span class="sxs-lookup"><span data-stu-id="90c1d-133">This example shows the contents of the **Microsoft.PowerShell** registry key.</span></span> <span data-ttu-id="90c1d-134">您可以使用這個指令程式搭配 PowerShell 登錄提供者來取得登錄機碼和子機碼，但您必須使用指令程式 `Get-ItemProperty` 來取得登錄值和資料。</span><span class="sxs-lookup"><span data-stu-id="90c1d-134">You can use this cmdlet with the PowerShell Registry provider to get registry keys and subkeys, but you must use the `Get-ItemProperty` cmdlet to get the registry values and data.</span></span>

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### <span data-ttu-id="90c1d-135">範例7：取得具有排除專案的目錄中的專案</span><span class="sxs-lookup"><span data-stu-id="90c1d-135">Example 7: Get items in a directory that have an exclusion</span></span>

<span data-ttu-id="90c1d-136">這個範例會取得 Windows 目錄中名稱包含點 () 的專案 `.` ，但開頭不是 `w*` 。此範例僅適用于路徑包含萬用字元 (`*`) 來指定專案內容時。</span><span class="sxs-lookup"><span data-stu-id="90c1d-136">This example gets items in the Windows directory with names that include a dot (`.`), but don't begin with `w*`.This example works only when the path includes a wildcard character (`*`) to specify the contents of the item.</span></span>

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### <span data-ttu-id="90c1d-137">範例8：取得硬連結資訊</span><span class="sxs-lookup"><span data-stu-id="90c1d-137">Example 8: Getting hardlink information</span></span>

<span data-ttu-id="90c1d-138">在 PowerShell 6.2 中，已新增替代視圖來取得硬連結的資訊。</span><span class="sxs-lookup"><span data-stu-id="90c1d-138">In PowerShell 6.2, an alternate view was added to get hardlink information.</span></span> <span data-ttu-id="90c1d-139">若要取得硬連結的資訊，請將輸出輸送至 `Format-Table -View childrenWithHardlink`</span><span class="sxs-lookup"><span data-stu-id="90c1d-139">To get the hardlink information, pipe the output to `Format-Table -View childrenWithHardlink`</span></span>

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### <span data-ttu-id="90c1d-140">範例9：實驗性功能 PSUnixFileStat 的輸出</span><span class="sxs-lookup"><span data-stu-id="90c1d-140">Example 9: Output for experimental feature PSUnixFileStat</span></span>

<span data-ttu-id="90c1d-141">在 Unix 系統上的 PowerShell 7 中，實驗性功能 **PSUnixFileStat** 提供類似 Unix 的輸出：</span><span class="sxs-lookup"><span data-stu-id="90c1d-141">In PowerShell 7 on Unix systems, the experimental feature **PSUnixFileStat** provides Unix-like output:</span></span>

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

<span data-ttu-id="90c1d-142">現在屬於輸出的新屬性為：</span><span class="sxs-lookup"><span data-stu-id="90c1d-142">The new properties that are now part of the output are:</span></span>

- <span data-ttu-id="90c1d-143">**UnixMode** 是 Unix 系統上所代表的檔案許可權</span><span class="sxs-lookup"><span data-stu-id="90c1d-143">**UnixMode** is the file permissions as represented on a Unix system</span></span>
- <span data-ttu-id="90c1d-144">**使用者** 是檔案擁有者</span><span class="sxs-lookup"><span data-stu-id="90c1d-144">**User** is the file owner</span></span>
- <span data-ttu-id="90c1d-145">**群組** 是群組擁有者</span><span class="sxs-lookup"><span data-stu-id="90c1d-145">**Group** is the group owner</span></span>
- <span data-ttu-id="90c1d-146">**大小** 是 Unix 系統上表示的檔案或目錄大小</span><span class="sxs-lookup"><span data-stu-id="90c1d-146">**Size** is the size of the file or directory as represented on a Unix system</span></span>

## <span data-ttu-id="90c1d-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="90c1d-147">PARAMETERS</span></span>

### <span data-ttu-id="90c1d-148">-Stream</span><span class="sxs-lookup"><span data-stu-id="90c1d-148">-Stream</span></span>

<span data-ttu-id="90c1d-149">從檔案中取得指定的替代 NTFS 檔案資料流。</span><span class="sxs-lookup"><span data-stu-id="90c1d-149">Gets the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="90c1d-150">輸入資料流名稱。</span><span class="sxs-lookup"><span data-stu-id="90c1d-150">Enter the stream name.</span></span> <span data-ttu-id="90c1d-151">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="90c1d-151">Wildcards are supported.</span></span> <span data-ttu-id="90c1d-152">若要取得所有資料流程，請使用星號 (`*`) 。</span><span class="sxs-lookup"><span data-stu-id="90c1d-152">To get all streams, use an asterisk (`*`).</span></span> <span data-ttu-id="90c1d-153">此參數在資料夾中無效。</span><span class="sxs-lookup"><span data-stu-id="90c1d-153">This parameter isn't valid on folders.</span></span>

<span data-ttu-id="90c1d-154">**Stream** 是動態參數， **FileSystem** 提供者會將它新增至 `Get-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90c1d-154">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Item` cmdlet.</span></span>
<span data-ttu-id="90c1d-155">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="90c1d-155">This parameter works only in file system drives.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No alternate file streams
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="90c1d-156">-Credential</span><span class="sxs-lookup"><span data-stu-id="90c1d-156">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="90c1d-157">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="90c1d-157">This parameter isn't supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="90c1d-158">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="90c1d-158">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="90c1d-159">-Exclude</span><span class="sxs-lookup"><span data-stu-id="90c1d-159">-Exclude</span></span>

<span data-ttu-id="90c1d-160">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="90c1d-160">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="90c1d-161">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="90c1d-161">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="90c1d-162">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="90c1d-162">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="90c1d-163">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="90c1d-163">Wildcard characters are permitted.</span></span> <span data-ttu-id="90c1d-164">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="90c1d-164">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="90c1d-165">-Filter</span><span class="sxs-lookup"><span data-stu-id="90c1d-165">-Filter</span></span>

<span data-ttu-id="90c1d-166">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="90c1d-166">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="90c1d-167">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="90c1d-167">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="90c1d-168">篩選比其他參數更有效率。</span><span class="sxs-lookup"><span data-stu-id="90c1d-168">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="90c1d-169">此提供者會在取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="90c1d-169">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="90c1d-170">篩選字串會傳遞至 .NET API 以列舉檔案。</span><span class="sxs-lookup"><span data-stu-id="90c1d-170">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="90c1d-171">API 僅支援 `*` 和 `?` 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="90c1d-171">The API only supports `*` and `?` wildcards.</span></span>

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

### <span data-ttu-id="90c1d-172">-Force</span><span class="sxs-lookup"><span data-stu-id="90c1d-172">-Force</span></span>

<span data-ttu-id="90c1d-173">指出此 Cmdlet 會取得無法以其他方式存取的專案，例如隱藏的專案。</span><span class="sxs-lookup"><span data-stu-id="90c1d-173">Indicates that this cmdlet gets items that can't otherwise be accessed, such as hidden items.</span></span>
<span data-ttu-id="90c1d-174">實作會依提供者而異。</span><span class="sxs-lookup"><span data-stu-id="90c1d-174">Implementation varies from provider to provider.</span></span> <span data-ttu-id="90c1d-175">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="90c1d-175">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="90c1d-176">即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="90c1d-176">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="90c1d-177">-Include</span><span class="sxs-lookup"><span data-stu-id="90c1d-177">-Include</span></span>

<span data-ttu-id="90c1d-178">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="90c1d-178">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="90c1d-179">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="90c1d-179">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="90c1d-180">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="90c1d-180">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="90c1d-181">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="90c1d-181">Wildcard characters are permitted.</span></span> <span data-ttu-id="90c1d-182">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="90c1d-182">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="90c1d-183">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="90c1d-183">-LiteralPath</span></span>

<span data-ttu-id="90c1d-184">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="90c1d-184">Specifies a path to one or more locations.</span></span> <span data-ttu-id="90c1d-185">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="90c1d-185">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="90c1d-186">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="90c1d-186">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="90c1d-187">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="90c1d-187">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="90c1d-188">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="90c1d-188">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="90c1d-189">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="90c1d-189">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="90c1d-190">-Path</span><span class="sxs-lookup"><span data-stu-id="90c1d-190">-Path</span></span>

<span data-ttu-id="90c1d-191">指定項目的路徑。</span><span class="sxs-lookup"><span data-stu-id="90c1d-191">Specifies the path to an item.</span></span> <span data-ttu-id="90c1d-192">此 Cmdlet 會取得指定位置的專案。</span><span class="sxs-lookup"><span data-stu-id="90c1d-192">This cmdlet gets the item at the specified location.</span></span> <span data-ttu-id="90c1d-193">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="90c1d-193">Wildcard characters are permitted.</span></span> <span data-ttu-id="90c1d-194">這個參數是必要參數，但參數名稱 **路徑** 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="90c1d-194">This parameter is required, but the parameter name **Path** is optional.</span></span>

<span data-ttu-id="90c1d-195">使用點 (`.`) 來指定目前的位置。</span><span class="sxs-lookup"><span data-stu-id="90c1d-195">Use a dot (`.`) to specify the current location.</span></span> <span data-ttu-id="90c1d-196">使用 (`*`) 萬用字元來指定目前位置中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="90c1d-196">Use the wildcard character (`*`) to specify all the items in the current location.</span></span>

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

### <span data-ttu-id="90c1d-197">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="90c1d-197">CommonParameters</span></span>

<span data-ttu-id="90c1d-198">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="90c1d-198">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="90c1d-199">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="90c1d-199">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="90c1d-200">輸入</span><span class="sxs-lookup"><span data-stu-id="90c1d-200">INPUTS</span></span>

### <span data-ttu-id="90c1d-201">System.String</span><span class="sxs-lookup"><span data-stu-id="90c1d-201">System.String</span></span>

<span data-ttu-id="90c1d-202">您可以使用管線將包含路徑的字串傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90c1d-202">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="90c1d-203">輸出</span><span class="sxs-lookup"><span data-stu-id="90c1d-203">OUTPUTS</span></span>

### <span data-ttu-id="90c1d-204">System.Object</span><span class="sxs-lookup"><span data-stu-id="90c1d-204">System.Object</span></span>

<span data-ttu-id="90c1d-205">這個 Cmdlet 會傳回它所取得的物件。</span><span class="sxs-lookup"><span data-stu-id="90c1d-205">This cmdlet returns the objects that it gets.</span></span> <span data-ttu-id="90c1d-206">類型是由路徑中的物件類型決定。</span><span class="sxs-lookup"><span data-stu-id="90c1d-206">The type is determined by the type of objects in the path.</span></span>

## <span data-ttu-id="90c1d-207">注意</span><span class="sxs-lookup"><span data-stu-id="90c1d-207">NOTES</span></span>

<span data-ttu-id="90c1d-208">此 Cmdlet 不會有 **遞迴** 參數，因為它只會取得專案，而不是其內容。</span><span class="sxs-lookup"><span data-stu-id="90c1d-208">This cmdlet does not have a **Recurse** parameter, because it gets only an item, not its contents.</span></span>
<span data-ttu-id="90c1d-209">若要以遞迴方式取得專案的內容，請使用 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="90c1d-209">To get the contents of an item recursively, use `Get-ChildItem`.</span></span>

<span data-ttu-id="90c1d-210">若要流覽登錄，請使用此 Cmdlet 來取得登錄機碼和， `Get-ItemProperty` 以取得登錄值和資料。</span><span class="sxs-lookup"><span data-stu-id="90c1d-210">To navigate through the registry, use this cmdlet to get registry keys and the `Get-ItemProperty` to get registry values and data.</span></span> <span data-ttu-id="90c1d-211">登錄值可視為是登錄機碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="90c1d-211">The registry values are considered to be properties of the registry key.</span></span>
  
<span data-ttu-id="90c1d-212">此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="90c1d-212">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="90c1d-213">若要列出工作階段中可用的提供者，請輸入 `Get-PsProvider`。</span><span class="sxs-lookup"><span data-stu-id="90c1d-213">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="90c1d-214">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="90c1d-214">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="90c1d-215">相關連結</span><span class="sxs-lookup"><span data-stu-id="90c1d-215">RELATED LINKS</span></span>

[<span data-ttu-id="90c1d-216">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="90c1d-216">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="90c1d-217">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="90c1d-217">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="90c1d-218">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="90c1d-218">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="90c1d-219">Move-Item</span><span class="sxs-lookup"><span data-stu-id="90c1d-219">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="90c1d-220">New-Item</span><span class="sxs-lookup"><span data-stu-id="90c1d-220">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="90c1d-221">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="90c1d-221">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="90c1d-222">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="90c1d-222">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="90c1d-223">Set-Item</span><span class="sxs-lookup"><span data-stu-id="90c1d-223">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="90c1d-224">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="90c1d-224">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="90c1d-225">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="90c1d-225">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="90c1d-226">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="90c1d-226">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="90c1d-227">about_Providers</span><span class="sxs-lookup"><span data-stu-id="90c1d-227">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)