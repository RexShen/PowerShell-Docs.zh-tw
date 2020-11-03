---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ChildItem
ms.openlocfilehash: 14b1c5d0f37301a5312f37a115f0abc1c7b5990e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204460"
---
# <span data-ttu-id="757c4-103">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="757c4-103">Get-ChildItem</span></span>

## <span data-ttu-id="757c4-104">概要</span><span class="sxs-lookup"><span data-stu-id="757c4-104">SYNOPSIS</span></span>

<span data-ttu-id="757c4-105">取得一或多個指定之位置中的項目與子項目。</span><span class="sxs-lookup"><span data-stu-id="757c4-105">Gets the items and child items in one or more specified locations.</span></span>

## <span data-ttu-id="757c4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="757c4-106">SYNTAX</span></span>

### <span data-ttu-id="757c4-107">Items (預設值)</span><span class="sxs-lookup"><span data-stu-id="757c4-107">Items (Default)</span></span>

```
Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>]
 [-Recurse] [-Depth <uint32>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>]
 [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### <span data-ttu-id="757c4-108">LiteralItems</span><span class="sxs-lookup"><span data-stu-id="757c4-108">LiteralItems</span></span>

```
Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>]
 [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force] [-Name]
 [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden]
 [-ReadOnly] [-System] [<CommonParameters>]
```

## <span data-ttu-id="757c4-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="757c4-109">DESCRIPTION</span></span>

<span data-ttu-id="757c4-110">`Get-ChildItem`Cmdlet 會取得一或多個指定位置中的專案。</span><span class="sxs-lookup"><span data-stu-id="757c4-110">The `Get-ChildItem` cmdlet gets the items in one or more specified locations.</span></span> <span data-ttu-id="757c4-111">如果項目是容器，它便會取得容器內的項目，稱為子項目。</span><span class="sxs-lookup"><span data-stu-id="757c4-111">If the item is a container, it gets the items inside the container, known as child items.</span></span> <span data-ttu-id="757c4-112">您可以使用 **遞迴** 參數來取得所有子容器中的專案，並使用 **Depth** 參數來限制要遞迴的層級數目。</span><span class="sxs-lookup"><span data-stu-id="757c4-112">You can use the **Recurse** parameter to get items in all child containers and use the **Depth** parameter to limit the number of levels to recurse.</span></span>

<span data-ttu-id="757c4-113">`Get-ChildItem` 不顯示空的目錄。</span><span class="sxs-lookup"><span data-stu-id="757c4-113">`Get-ChildItem` doesn't display empty directories.</span></span> <span data-ttu-id="757c4-114">當 `Get-ChildItem` 命令包含 **深度** 或 **遞迴** 參數時，輸出中不會包含空的目錄。</span><span class="sxs-lookup"><span data-stu-id="757c4-114">When a `Get-ChildItem` command includes the **Depth** or **Recurse** parameters, empty directories aren't included in the output.</span></span>

<span data-ttu-id="757c4-115">位置是 `Get-ChildItem` 由 PowerShell 提供者所公開。</span><span class="sxs-lookup"><span data-stu-id="757c4-115">Locations are exposed to `Get-ChildItem` by PowerShell providers.</span></span> <span data-ttu-id="757c4-116">位置可以是檔案系統目錄、登錄 hive 或憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="757c4-116">A location can be a file system directory, registry hive, or a certificate store.</span></span> <span data-ttu-id="757c4-117">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="757c4-117">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="757c4-118">範例</span><span class="sxs-lookup"><span data-stu-id="757c4-118">EXAMPLES</span></span>

### <span data-ttu-id="757c4-119">範例1：從檔案系統目錄取得子專案</span><span class="sxs-lookup"><span data-stu-id="757c4-119">Example 1: Get child items from a file system directory</span></span>

<span data-ttu-id="757c4-120">此範例會從檔案系統目錄取得子專案。</span><span class="sxs-lookup"><span data-stu-id="757c4-120">This example gets the child items from a file system directory.</span></span> <span data-ttu-id="757c4-121">檔案名和子目錄名稱隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="757c4-121">The filenames and subdirectory names are displayed.</span></span> <span data-ttu-id="757c4-122">針對空的位置，此命令不會傳回任何輸出，並返回 PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="757c4-122">For empty locations, the command doesn't return any output and returns to the PowerShell prompt.</span></span>

<span data-ttu-id="757c4-123">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定目錄 `C:\Test` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-123">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test`.</span></span>
<span data-ttu-id="757c4-124">`Get-ChildItem` 在 PowerShell 主控台中顯示檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="757c4-124">`Get-ChildItem` displays the files and directories in the PowerShell console.</span></span>

```powershell
Get-ChildItem -Path C:\Test
```

```Output
   Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     08:29                Logs
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="757c4-125">依預設，會 `Get-ChildItem` 列出 ( **屬性** ) 、 **LastWriteTime** 、檔案大小 ( **長度** ) 和專案 **名稱** 的模式。</span><span class="sxs-lookup"><span data-stu-id="757c4-125">By default `Get-ChildItem` lists the mode ( **Attributes** ), **LastWriteTime** , file size ( **Length** ), and the **Name** of the item.</span></span> <span data-ttu-id="757c4-126">**模式** 屬性中的字母可解讀如下：</span><span class="sxs-lookup"><span data-stu-id="757c4-126">The letters in the **Mode** property can be interpreted as follows:</span></span>

- <span data-ttu-id="757c4-127">`l` (連結) </span><span class="sxs-lookup"><span data-stu-id="757c4-127">`l` (link)</span></span>
- <span data-ttu-id="757c4-128">`d` (directory) </span><span class="sxs-lookup"><span data-stu-id="757c4-128">`d` (directory)</span></span>
- <span data-ttu-id="757c4-129">`a` (封存) </span><span class="sxs-lookup"><span data-stu-id="757c4-129">`a` (archive)</span></span>
- <span data-ttu-id="757c4-130">`r` (唯讀) </span><span class="sxs-lookup"><span data-stu-id="757c4-130">`r` (read-only)</span></span>
- <span data-ttu-id="757c4-131">`h` (隱藏) </span><span class="sxs-lookup"><span data-stu-id="757c4-131">`h` (hidden)</span></span>
- <span data-ttu-id="757c4-132">`s` (系統) 。</span><span class="sxs-lookup"><span data-stu-id="757c4-132">`s` (system).</span></span>

<span data-ttu-id="757c4-133">如需模式旗標的詳細資訊，請參閱 [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression)。</span><span class="sxs-lookup"><span data-stu-id="757c4-133">For more information about the mode flags, see [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression).</span></span>

### <span data-ttu-id="757c4-134">範例2：取得目錄中的子專案名稱</span><span class="sxs-lookup"><span data-stu-id="757c4-134">Example 2: Get child item names in a directory</span></span>

<span data-ttu-id="757c4-135">此範例只會列出目錄中專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="757c4-135">This example lists only the names of items in a directory.</span></span>

<span data-ttu-id="757c4-136">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定目錄 `C:\Test` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-136">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test`.</span></span> <span data-ttu-id="757c4-137">**Name** 參數只會傳回指定路徑中的檔案或目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="757c4-137">The **Name** parameter returns only the file or directory names from the specified path.</span></span>

```powershell
Get-ChildItem -Path C:\Test -Name
```

```Output
Logs
anotherfile.txt
Command.txt
CreateTestFile.ps1
ReadOnlyFile.txt
```

### <span data-ttu-id="757c4-138">範例3：取得目前目錄和子目錄中的子專案</span><span class="sxs-lookup"><span data-stu-id="757c4-138">Example 3: Get child items in the current directory and subdirectories</span></span>

<span data-ttu-id="757c4-139">此範例會顯示位於目前的目錄及其子目錄中的 **.txt 檔案。**</span><span class="sxs-lookup"><span data-stu-id="757c4-139">This example displays **.txt** files that are located in the current directory and its subdirectories.</span></span>

```powershell
Get-ChildItem -Path C:\Test\*.txt -Recurse -Force
```

```Output
    Directory: C:\Test\Logs\Adirectory

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile4.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile4.txt

    Directory: C:\Test\Logs\Backup

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 ATextFile.txt
-a----        2/12/2019     15:50             20 LogFile3.txt

    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="757c4-140">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定 `C:\Test\*.txt` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-140">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify `C:\Test\*.txt`.</span></span> <span data-ttu-id="757c4-141">**路徑** 使用星號 (`*`) 萬用字元來指定副檔名為副檔名的所有檔案 `.txt` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-141">**Path** uses the asterisk (`*`) wildcard to specify all files with the filename extension `.txt`.</span></span> <span data-ttu-id="757c4-142">**遞迴** 參數會搜尋 **路徑** 目錄的子目錄，如 **目錄：** 標題所示。</span><span class="sxs-lookup"><span data-stu-id="757c4-142">The **Recurse** parameter searches the **Path** directory its subdirectories, as shown in the **Directory:** headings.</span></span> <span data-ttu-id="757c4-143">**Force** 參數 `hiddenfile.txt` 會顯示具有 **h** 模式的隱藏檔案。</span><span class="sxs-lookup"><span data-stu-id="757c4-143">The **Force** parameter displays hidden files such as `hiddenfile.txt` that have a mode of **h** .</span></span>

### <span data-ttu-id="757c4-144">範例4：使用 Include 參數取得子專案</span><span class="sxs-lookup"><span data-stu-id="757c4-144">Example 4: Get child items using the Include parameter</span></span>

<span data-ttu-id="757c4-145">在此範例中，會 `Get-ChildItem` 使用 **Include** 參數，從 **Path** 參數所指定的目錄中尋找特定的專案。</span><span class="sxs-lookup"><span data-stu-id="757c4-145">In this example `Get-ChildItem` uses the **Include** parameter to find specific items from the directory specified by the **Path** parameter.</span></span>

```powershell
# When using the -Include parameter, if you don't include an asterisk in the path
# the command returns no output.
Get-ChildItem -Path C:\Test\ -Include *.txt
```

```Output

```

```powershell
Get-ChildItem -Path C:\Test\* -Include *.txt
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

<span data-ttu-id="757c4-146">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定目錄 **C:\Test** 。</span><span class="sxs-lookup"><span data-stu-id="757c4-146">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory **C:\Test** .</span></span> <span data-ttu-id="757c4-147">**Path** 參數包含尾端星號 (`*`) 萬用字元來指定目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="757c4-147">The **Path** parameter includes a trailing asterisk (`*`) wildcard to specify the directory's contents.</span></span>
<span data-ttu-id="757c4-148">**Include** 參數使用星號 (`*`) 萬用字元來指定副檔名為 **.txt** 的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="757c4-148">The **Include** parameter uses an asterisk (`*`) wildcard to specify all files with the file name extension **.txt** .</span></span>

<span data-ttu-id="757c4-149">使用 **Include** 參數時， **Path** 參數需要尾端星號 (`*`) 萬用字元來指定目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="757c4-149">When the **Include** parameter is used, the **Path** parameter needs a trailing asterisk (`*`) wildcard to specify the directory's contents.</span></span> <span data-ttu-id="757c4-150">例如： `-Path C:\Test\*` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-150">For example, `-Path C:\Test\*`.</span></span>

- <span data-ttu-id="757c4-151">如果將 **遞迴** 參數加入至命令，則 Path 參數中的尾端星號 (`*`) **Path** 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="757c4-151">If the **Recurse** parameter is added to the command, the trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="757c4-152">**遞迴** 參數會從 **路徑** 目錄及其子目錄中取得專案。</span><span class="sxs-lookup"><span data-stu-id="757c4-152">The **Recurse** parameter gets items from the **Path** directory and its subdirectories.</span></span> <span data-ttu-id="757c4-153">例如， `-Path C:\Test\ -Recurse -Include *.txt`</span><span class="sxs-lookup"><span data-stu-id="757c4-153">For example, `-Path C:\Test\ -Recurse -Include *.txt`</span></span>
- <span data-ttu-id="757c4-154">如果尾端的星號 (`*`) 不包含在 **Path** 參數中，則此命令不會傳回任何輸出，並返回 PowerShell 提示字元。</span><span class="sxs-lookup"><span data-stu-id="757c4-154">If a trailing asterisk (`*`) isn't included in the **Path** parameter, the command doesn't return any output and returns to the PowerShell prompt.</span></span> <span data-ttu-id="757c4-155">例如： `-Path C:\Test\` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-155">For example, `-Path C:\Test\`.</span></span>

### <span data-ttu-id="757c4-156">範例5：使用 Exclude 參數取得子專案</span><span class="sxs-lookup"><span data-stu-id="757c4-156">Example 5: Get child items using the Exclude parameter</span></span>

<span data-ttu-id="757c4-157">範例的輸出會顯示目錄 **C:\Test\Logs** 的內容。</span><span class="sxs-lookup"><span data-stu-id="757c4-157">The example's output shows the contents of the directory **C:\Test\Logs** .</span></span> <span data-ttu-id="757c4-158">輸出是其他使用 **Exclude** 和 **遞迴** 參數之命令的參考。</span><span class="sxs-lookup"><span data-stu-id="757c4-158">The output is a reference for the other commands that use the **Exclude** and **Recurse** parameters.</span></span>

```powershell
Get-ChildItem -Path C:\Test\Logs
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Adirectory
d-----        2/15/2019     08:28                AnEmptyDirectory
d-----        2/15/2019     13:21                Backup
-a----        2/12/2019     16:16             20 Afile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

```powershell
Get-ChildItem -Path C:\Test\Logs\* -Exclude A*
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Backup
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

<span data-ttu-id="757c4-159">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定目錄 `C:\Test\Logs` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-159">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory `C:\Test\Logs`.</span></span>
<span data-ttu-id="757c4-160">**Exclude** 參數會使用星號 (`*`) 萬用字元來指定以或開頭的任何檔案或目錄 **A** ，並 **a** 從輸出中排除。</span><span class="sxs-lookup"><span data-stu-id="757c4-160">The **Exclude** parameter uses the asterisk (`*`) wildcard to specify any files or directories that begin with **A** or **a** are excluded from the output.</span></span>

<span data-ttu-id="757c4-161">使用 **Exclude** 參數時， `*` **Path** 參數中 () 的尾端星號是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="757c4-161">When the **Exclude** parameter is used, a trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="757c4-162">例如，`-Path C:\Test\Logs` 或 `-Path C:\Test\Logs\*`。</span><span class="sxs-lookup"><span data-stu-id="757c4-162">For example, `-Path C:\Test\Logs` or `-Path C:\Test\Logs\*`.</span></span>

- <span data-ttu-id="757c4-163">如果尾端星號 (`*`) 不包含在 **path** 參數中，就會顯示 **path** 參數的內容。</span><span class="sxs-lookup"><span data-stu-id="757c4-163">If a trailing asterisk (`*`) isn't included in the **Path** parameter, the contents of the **Path** parameter are displayed.</span></span> <span data-ttu-id="757c4-164">例外狀況是符合 **排除** 參數值的檔案名或子目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="757c4-164">The exceptions are filenames or subdirectory names that match the **Exclude** parameter's value.</span></span>
- <span data-ttu-id="757c4-165">如果 `*` **path** 參數中包含尾端的星號 () ，命令就會 recurses 至 **path** 參數的子目錄。</span><span class="sxs-lookup"><span data-stu-id="757c4-165">If a trailing asterisk (`*`) is included in the **Path** parameter, the command recurses into the **Path** parameter's subdirectories.</span></span> <span data-ttu-id="757c4-166">例外狀況是符合 **排除** 參數值的檔案名或子目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="757c4-166">The exceptions are filenames or subdirectory names that match the **Exclude** parameter's value.</span></span>
- <span data-ttu-id="757c4-167">如果將 **遞迴** 參數加入至命令，則無論 **Path** 參數是否包含尾端星號 () ，遞迴輸出都會相同 `*` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-167">If the **Recurse** parameter is added to the command, the recursion output is the same whether or not the **Path** parameter includes a trailing asterisk (`*`).</span></span>

### <span data-ttu-id="757c4-168">範例6：從登錄 hive 取得登錄機碼</span><span class="sxs-lookup"><span data-stu-id="757c4-168">Example 6: Get the registry keys from a registry hive</span></span>

<span data-ttu-id="757c4-169">這個範例會從取得所有的登錄機碼 `HKEY_LOCAL_MACHINE\HARDWARE` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-169">This example gets all the registry keys from `HKEY_LOCAL_MACHINE\HARDWARE`.</span></span>

<span data-ttu-id="757c4-170">`Get-ChildItem` 使用 **Path** 參數指定登錄機碼 `HKLM:\HARDWARE` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-170">`Get-ChildItem` uses the **Path** parameter to specify the registry key `HKLM:\HARDWARE`.</span></span> <span data-ttu-id="757c4-171">Hive 的路徑和最上層的登錄機碼會顯示在 PowerShell 主控台中。</span><span class="sxs-lookup"><span data-stu-id="757c4-171">The hive's path and top level of registry keys are displayed in the PowerShell console.</span></span>

<span data-ttu-id="757c4-172">如需詳細資訊，請參閱 [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)。</span><span class="sxs-lookup"><span data-stu-id="757c4-172">For more information, see [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md).</span></span>

```powershell
Get-ChildItem -Path HKLM:\HARDWARE
```

```Output
    Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name             Property
----             --------
ACPI
DESCRIPTION
DEVICEMAP
RESOURCEMAP
UEFI
```

```powershell
Get-ChildItem -Path HKLM:\HARDWARE -Exclude D*
```

```Output
   Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name                           Property
----                           --------
ACPI
RESOURCEMAP
```

<span data-ttu-id="757c4-173">第一個命令顯示登錄機碼的內容 `HKLM:\HARDWARE` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-173">The first command shows the contents of the `HKLM:\HARDWARE` registry key.</span></span> <span data-ttu-id="757c4-174">**Exclude** 參數會告訴您不要傳回以開頭的任何子機碼 `Get-ChildItem` `D*` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-174">The **Exclude** parameter tells `Get-ChildItem` not to return any subkeys that start with `D*`.</span></span> <span data-ttu-id="757c4-175">目前， **Exclude** 參數只適用于子機碼，而不是專案屬性。</span><span class="sxs-lookup"><span data-stu-id="757c4-175">Currently, the **Exclude** parameter only works on subkeys, not item properties.</span></span>

### <span data-ttu-id="757c4-176">範例7：取得具有程式碼簽署授權單位的所有憑證</span><span class="sxs-lookup"><span data-stu-id="757c4-176">Example 7: Get all certificates with code-signing authority</span></span>

<span data-ttu-id="757c4-177">此範例會取得 PowerShell **Cert：** 磁片磁碟機中具有程式碼簽署授權單位的每個憑證。</span><span class="sxs-lookup"><span data-stu-id="757c4-177">This example gets each certificate in the PowerShell **Cert:** drive that has code-signing authority.</span></span>

<span data-ttu-id="757c4-178">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定 **Cert：** provider。</span><span class="sxs-lookup"><span data-stu-id="757c4-178">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the **Cert:** provider.</span></span> <span data-ttu-id="757c4-179">**遞迴** 參數會搜尋 **路徑** 及其子目錄所指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="757c4-179">The **Recurse** parameter searches the directory specified by **Path** and its subdirectories.</span></span> <span data-ttu-id="757c4-180">**CodeSigningCert** 參數只會取得具有程式碼簽署授權單位的憑證。</span><span class="sxs-lookup"><span data-stu-id="757c4-180">The **CodeSigningCert** parameter gets only certificates that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path Cert:\* -Recurse -CodeSigningCert
```

<span data-ttu-id="757c4-181">如需有關憑證提供者和 Cert：磁片磁碟機的詳細資訊，請參閱 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)。</span><span class="sxs-lookup"><span data-stu-id="757c4-181">For more information about the Certificate provider and the Cert: drive, see [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).</span></span>

### <span data-ttu-id="757c4-182">範例8：使用 Depth 參數取得專案</span><span class="sxs-lookup"><span data-stu-id="757c4-182">Example 8: Get items using the Depth parameter</span></span>

<span data-ttu-id="757c4-183">此範例會顯示目錄及其子目錄中的專案。</span><span class="sxs-lookup"><span data-stu-id="757c4-183">This example displays the items in a directory and its subdirectories.</span></span> <span data-ttu-id="757c4-184">**Depth** 參數會決定要包含在遞迴中的子目錄層級數目。</span><span class="sxs-lookup"><span data-stu-id="757c4-184">The **Depth** parameter determines the number of subdirectory levels to include in the recursion.</span></span> <span data-ttu-id="757c4-185">空白目錄會從輸出中排除。</span><span class="sxs-lookup"><span data-stu-id="757c4-185">Empty directories are excluded from the output.</span></span>

```powershell
Get-ChildItem -Path C:\Parent -Depth 2
```

```Output
    Directory: C:\Parent

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level1
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level2
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1\SubDir_Level2

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:22                SubDir_Level3
-a----        2/13/2019     08:55             26 file.txt
```

<span data-ttu-id="757c4-186">此 `Get-ChildItem` Cmdlet 會使用 **Path** 參數來指定 **C:\Parent** 。</span><span class="sxs-lookup"><span data-stu-id="757c4-186">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify **C:\Parent** .</span></span> <span data-ttu-id="757c4-187">**Depth** 參數會指定兩個層級的遞迴。</span><span class="sxs-lookup"><span data-stu-id="757c4-187">The **Depth** parameter specifies two levels of recursion.</span></span> <span data-ttu-id="757c4-188">`Get-ChildItem` 顯示 **Path** 參數所指定之目錄的內容，以及兩個子目錄層級。</span><span class="sxs-lookup"><span data-stu-id="757c4-188">`Get-ChildItem` displays the contents of the directory specified by the **Path** parameter and the two levels of subdirectories.</span></span>

### <span data-ttu-id="757c4-189">範例9：取得永久連結資訊</span><span class="sxs-lookup"><span data-stu-id="757c4-189">Example 9: Getting hard link information</span></span>

<span data-ttu-id="757c4-190">在 PowerShell 6.2 中，已新增替代的視圖來取得永久連結資訊。</span><span class="sxs-lookup"><span data-stu-id="757c4-190">In PowerShell 6.2, an alternate view was added to get hard link information.</span></span>

```powershell
Get-ChildItem -Path C:\PathContainingHardLink | Format-Table -View childrenWithHardLink
```

## <span data-ttu-id="757c4-191">參數</span><span class="sxs-lookup"><span data-stu-id="757c4-191">Parameters</span></span>

### <span data-ttu-id="757c4-192">-Attributes</span><span class="sxs-lookup"><span data-stu-id="757c4-192">-Attributes</span></span>

<span data-ttu-id="757c4-193">取得具有指定屬性的檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="757c4-193">Gets files and folders with the specified attributes.</span></span> <span data-ttu-id="757c4-194">此參數支援所有屬性，可讓您指定複雜的屬性組合。</span><span class="sxs-lookup"><span data-stu-id="757c4-194">This parameter supports all attributes and lets you specify complex combinations of attributes.</span></span>

<span data-ttu-id="757c4-195">例如，若要取得已加密或壓縮的非系統檔案 (非目錄)，請輸入：</span><span class="sxs-lookup"><span data-stu-id="757c4-195">For example, to get non-system files (not directories) that are encrypted or compressed, type:</span></span>

`Get-ChildItem -Attributes !Directory+!System+Encrypted, !Directory+!System+Compressed`

<span data-ttu-id="757c4-196">若要尋找具有常用屬性的檔案和資料夾，請使用 **attributes** 參數。</span><span class="sxs-lookup"><span data-stu-id="757c4-196">To find files and folders with commonly used attributes, use the **Attributes** parameter.</span></span> <span data-ttu-id="757c4-197">或參數 **目錄** 、 **File** 、 **Hidden** 、 **ReadOnly** 和 **System** 。</span><span class="sxs-lookup"><span data-stu-id="757c4-197">Or, the parameters **Directory** , **File** , **Hidden** , **ReadOnly** , and **System** .</span></span>

<span data-ttu-id="757c4-198">**Attributes** 參數支援下列屬性：</span><span class="sxs-lookup"><span data-stu-id="757c4-198">The **Attributes** parameter supports the following properties:</span></span>

- <span data-ttu-id="757c4-199">**封存**</span><span class="sxs-lookup"><span data-stu-id="757c4-199">**Archive**</span></span>
- <span data-ttu-id="757c4-200">**Compressed**</span><span class="sxs-lookup"><span data-stu-id="757c4-200">**Compressed**</span></span>
- <span data-ttu-id="757c4-201">**裝置**</span><span class="sxs-lookup"><span data-stu-id="757c4-201">**Device**</span></span>
- <span data-ttu-id="757c4-202">**目錄**</span><span class="sxs-lookup"><span data-stu-id="757c4-202">**Directory**</span></span>
- <span data-ttu-id="757c4-203">**已加密**</span><span class="sxs-lookup"><span data-stu-id="757c4-203">**Encrypted**</span></span>
- <span data-ttu-id="757c4-204">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="757c4-204">**Hidden**</span></span>
- <span data-ttu-id="757c4-205">**IntegrityStream**</span><span class="sxs-lookup"><span data-stu-id="757c4-205">**IntegrityStream**</span></span>
- <span data-ttu-id="757c4-206">**Normal**</span><span class="sxs-lookup"><span data-stu-id="757c4-206">**Normal**</span></span>
- <span data-ttu-id="757c4-207">**NoScrubData**</span><span class="sxs-lookup"><span data-stu-id="757c4-207">**NoScrubData**</span></span>
- <span data-ttu-id="757c4-208">**NotContentIndexed**</span><span class="sxs-lookup"><span data-stu-id="757c4-208">**NotContentIndexed**</span></span>
- <span data-ttu-id="757c4-209">**離線**</span><span class="sxs-lookup"><span data-stu-id="757c4-209">**Offline**</span></span>
- <span data-ttu-id="757c4-210">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="757c4-210">**ReadOnly**</span></span>
- <span data-ttu-id="757c4-211">**ReparsePoint**</span><span class="sxs-lookup"><span data-stu-id="757c4-211">**ReparsePoint**</span></span>
- <span data-ttu-id="757c4-212">**SparseFile**</span><span class="sxs-lookup"><span data-stu-id="757c4-212">**SparseFile**</span></span>
- <span data-ttu-id="757c4-213">**系統**</span><span class="sxs-lookup"><span data-stu-id="757c4-213">**System**</span></span>
- <span data-ttu-id="757c4-214">**暫存**</span><span class="sxs-lookup"><span data-stu-id="757c4-214">**Temporary**</span></span>

<span data-ttu-id="757c4-215">如需這些屬性的說明，請參閱 [FileAttributes 列舉](/dotnet/api/system.io.fileattributes)。</span><span class="sxs-lookup"><span data-stu-id="757c4-215">For a description of these attributes, see the [FileAttributes Enumeration](/dotnet/api/system.io.fileattributes).</span></span>

<span data-ttu-id="757c4-216">若要結合屬性，請使用下列運算子：</span><span class="sxs-lookup"><span data-stu-id="757c4-216">To combine attributes, use the following operators:</span></span>

- <span data-ttu-id="757c4-217">`!` (不) </span><span class="sxs-lookup"><span data-stu-id="757c4-217">`!` (NOT)</span></span>
- <span data-ttu-id="757c4-218">`+` (和) </span><span class="sxs-lookup"><span data-stu-id="757c4-218">`+` (AND)</span></span>
- <span data-ttu-id="757c4-219">`,` (或) </span><span class="sxs-lookup"><span data-stu-id="757c4-219">`,` (OR)</span></span>

<span data-ttu-id="757c4-220">請勿在運算子和其屬性之間使用空格。</span><span class="sxs-lookup"><span data-stu-id="757c4-220">Don't use spaces between an operator and its attribute.</span></span> <span data-ttu-id="757c4-221">逗號之後會接受空格。</span><span class="sxs-lookup"><span data-stu-id="757c4-221">Spaces are accepted after commas.</span></span>

<span data-ttu-id="757c4-222">針對通用屬性，請使用下列縮寫：</span><span class="sxs-lookup"><span data-stu-id="757c4-222">For common attributes, use the following abbreviations:</span></span>

- <span data-ttu-id="757c4-223">`D` (Directory) </span><span class="sxs-lookup"><span data-stu-id="757c4-223">`D` (Directory)</span></span>
- <span data-ttu-id="757c4-224">`H` (隱藏) </span><span class="sxs-lookup"><span data-stu-id="757c4-224">`H` (Hidden)</span></span>
- <span data-ttu-id="757c4-225">`R` (唯讀) </span><span class="sxs-lookup"><span data-stu-id="757c4-225">`R` (Read-only)</span></span>
- <span data-ttu-id="757c4-226">`S` (系統) </span><span class="sxs-lookup"><span data-stu-id="757c4-226">`S` (System)</span></span>

```yaml
Type: System.Management.Automation.FlagsExpression`1[System.IO.FileAttributes]
Parameter Sets: (All)
Aliases:
Accepted values: Archive, Compressed, Device, Directory, Encrypted, Hidden, IntegrityStream, Normal, NoScrubData, NotContentIndexed, Offline, ReadOnly, ReparsePoint, SparseFile, System, Temporary

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="757c4-227">-Depth</span><span class="sxs-lookup"><span data-stu-id="757c4-227">-Depth</span></span>

<span data-ttu-id="757c4-228">此參數是在 PowerShell 5.0 中新增的，可讓您控制遞迴的深度。</span><span class="sxs-lookup"><span data-stu-id="757c4-228">This parameter was added in PowerShell 5.0 and enables you to control the depth of recursion.</span></span> <span data-ttu-id="757c4-229">依預設，會 `Get-ChildItem` 顯示上層目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="757c4-229">By default, `Get-ChildItem` displays the contents of the parent directory.</span></span> <span data-ttu-id="757c4-230">**Depth** 參數會決定包含在遞迴中的子目錄層級數目，並顯示內容。</span><span class="sxs-lookup"><span data-stu-id="757c4-230">The **Depth** parameter determines the number of subdirectory levels that are included in the recursion and displays the contents.</span></span>

<span data-ttu-id="757c4-231">例如， `Depth 2` 包含 **Path** 參數的目錄、第一個子目錄層級和第二層子目錄。</span><span class="sxs-lookup"><span data-stu-id="757c4-231">For example, `Depth 2` includes the **Path** parameter's directory, first level of subdirectories, and second level of subdirectories.</span></span> <span data-ttu-id="757c4-232">依預設，目錄名稱和檔案名會包含在輸出中。</span><span class="sxs-lookup"><span data-stu-id="757c4-232">By default directory names and filenames are included in the output.</span></span>

> [!NOTE]
> <span data-ttu-id="757c4-233">從 PowerShell 或 **cmd.exe** 的 Windows 電腦上，您可以使用 **tree.com** 命令來顯示目錄結構的圖形化視圖。</span><span class="sxs-lookup"><span data-stu-id="757c4-233">On a Windows computer from PowerShell or **cmd.exe** , you can display a graphical view of a directory structure with the **tree.com** command.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="757c4-234">-Directory</span><span class="sxs-lookup"><span data-stu-id="757c4-234">-Directory</span></span>

<span data-ttu-id="757c4-235">若要取得目錄清單，請使用 **directory** 參數或 **Attributes** 參數搭配 **directory** 屬性。</span><span class="sxs-lookup"><span data-stu-id="757c4-235">To get a list of directories, use the **Directory** parameter or the **Attributes** parameter with the **Directory** property.</span></span> <span data-ttu-id="757c4-236">您可以使用 **遞迴** 參數搭配 **目錄** 。</span><span class="sxs-lookup"><span data-stu-id="757c4-236">You can use the **Recurse** parameter with **Directory** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ad, d

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="757c4-237">-Exclude</span><span class="sxs-lookup"><span data-stu-id="757c4-237">-Exclude</span></span>

<span data-ttu-id="757c4-238">以字串陣列指定此 Cmdlet 從作業中排除的屬性或屬性。</span><span class="sxs-lookup"><span data-stu-id="757c4-238">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="757c4-239">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="757c4-239">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="757c4-240">輸入路徑元素或模式，例如 `*.txt` 或 `A*` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-240">Enter a path element or pattern, such as `*.txt` or `A*`.</span></span> <span data-ttu-id="757c4-241">(接受萬用字元)。</span><span class="sxs-lookup"><span data-stu-id="757c4-241">Wildcard characters are accepted.</span></span>

<span data-ttu-id="757c4-242">`*` **Path** 參數中 () 的尾端星號是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="757c4-242">A trailing asterisk (`*`) in the **Path** parameter is optional.</span></span> <span data-ttu-id="757c4-243">例如，`-Path C:\Test\Logs` 或 `-Path C:\Test\Logs\*`。</span><span class="sxs-lookup"><span data-stu-id="757c4-243">For example, `-Path C:\Test\Logs` or `-Path C:\Test\Logs\*`.</span></span> <span data-ttu-id="757c4-244">如果包含尾端星號 (`*`) ，則命令會 recurses 至 **Path** 參數的子目錄。</span><span class="sxs-lookup"><span data-stu-id="757c4-244">If a trailing asterisk (`*`) is included, the command recurses into the **Path** parameter's subdirectories.</span></span> <span data-ttu-id="757c4-245">如果沒有星號 (`*`) ，則會顯示 **Path** 參數的內容。</span><span class="sxs-lookup"><span data-stu-id="757c4-245">Without the asterisk (`*`), the contents of the **Path** parameter are displayed.</span></span> <span data-ttu-id="757c4-246">範例5和 Notes 區段中包含更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="757c4-246">More details are included in Example 5 and the Notes section.</span></span>

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

### <span data-ttu-id="757c4-247">-File</span><span class="sxs-lookup"><span data-stu-id="757c4-247">-File</span></span>

<span data-ttu-id="757c4-248">若要取得檔案的清單，請使用 **File** 參數。</span><span class="sxs-lookup"><span data-stu-id="757c4-248">To get a list of files, use the **File** parameter.</span></span> <span data-ttu-id="757c4-249">您可以使用 **遞迴** 參數搭配 **File** 。</span><span class="sxs-lookup"><span data-stu-id="757c4-249">You can use the **Recurse** parameter with **File** .</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: af

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="757c4-250">-Filter</span><span class="sxs-lookup"><span data-stu-id="757c4-250">-Filter</span></span>

<span data-ttu-id="757c4-251">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="757c4-251">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="757c4-252">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="757c4-252">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports filters.</span></span> <span data-ttu-id="757c4-253">篩選比其他參數更有效率。</span><span class="sxs-lookup"><span data-stu-id="757c4-253">Filters are more efficient than other parameters.</span></span> <span data-ttu-id="757c4-254">此提供者會在取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="757c4-254">The provider applies filter when the cmdlet gets the objects rather than having PowerShell filter the objects after they're retrieved.</span></span> <span data-ttu-id="757c4-255">篩選字串會傳遞至 .NET API 以列舉檔案。</span><span class="sxs-lookup"><span data-stu-id="757c4-255">The filter string is passed to the .NET API to enumerate files.</span></span> <span data-ttu-id="757c4-256">API 僅支援 `*` 和 `?` 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="757c4-256">The API only supports `*` and `?` wildcards.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="757c4-257">-FollowSymlink</span><span class="sxs-lookup"><span data-stu-id="757c4-257">-FollowSymlink</span></span>

<span data-ttu-id="757c4-258">根據預設，此 `Get-ChildItem` Cmdlet 會顯示在遞迴期間找到之目錄的符號連結，但不會將其遞迴。</span><span class="sxs-lookup"><span data-stu-id="757c4-258">By default, the `Get-ChildItem` cmdlet displays symbolic links to directories found during recursion, but doesn't recurse into them.</span></span> <span data-ttu-id="757c4-259">使用 **FollowSymlink** 參數來搜尋以這些符號連結為目標的目錄。</span><span class="sxs-lookup"><span data-stu-id="757c4-259">Use the **FollowSymlink** parameter to search the directories that target those symbolic links.</span></span> <span data-ttu-id="757c4-260">**FollowSymlink** 是動態參數，只有 **FileSystem** 提供者才支援。</span><span class="sxs-lookup"><span data-stu-id="757c4-260">The **FollowSymlink** is a dynamic parameter and is supported only in the **FileSystem** provider.</span></span>

<span data-ttu-id="757c4-261">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="757c4-261">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="757c4-262">-Force</span><span class="sxs-lookup"><span data-stu-id="757c4-262">-Force</span></span>

<span data-ttu-id="757c4-263">允許 Cmdlet 取得使用者無法存取的專案，例如隱藏的檔案或系統檔案。</span><span class="sxs-lookup"><span data-stu-id="757c4-263">Allows the cmdlet to get items that otherwise can't be accessed by the user, such as hidden or system files.</span></span> <span data-ttu-id="757c4-264">**Force** 參數不會覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="757c4-264">The **Force** parameter doesn't override security restrictions.</span></span> <span data-ttu-id="757c4-265">實作因提供者而異。</span><span class="sxs-lookup"><span data-stu-id="757c4-265">Implementation varies among providers.</span></span> <span data-ttu-id="757c4-266">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="757c4-266">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="757c4-267">-Hidden</span><span class="sxs-lookup"><span data-stu-id="757c4-267">-Hidden</span></span>

<span data-ttu-id="757c4-268">若只要取得隱藏的專案，請使用 **hidden** 參數或 **Attributes** 參數搭配 **隱藏** 的屬性。</span><span class="sxs-lookup"><span data-stu-id="757c4-268">To get only hidden items, use the **Hidden** parameter or the **Attributes** parameter with the **Hidden** property.</span></span> <span data-ttu-id="757c4-269">依預設， `Get-ChildItem` 不會顯示隱藏的專案。</span><span class="sxs-lookup"><span data-stu-id="757c4-269">By default, `Get-ChildItem` doesn't display hidden items.</span></span> <span data-ttu-id="757c4-270">使用 **Force** 參數來取得隱藏的專案。</span><span class="sxs-lookup"><span data-stu-id="757c4-270">Use the **Force** parameter to get hidden items.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ah, h

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="757c4-271">-Include</span><span class="sxs-lookup"><span data-stu-id="757c4-271">-Include</span></span>

<span data-ttu-id="757c4-272">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="757c4-272">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="757c4-273">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="757c4-273">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="757c4-274">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="757c4-274">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="757c4-275">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="757c4-275">Wildcard characters are permitted.</span></span> <span data-ttu-id="757c4-276">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-276">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="757c4-277">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="757c4-277">-LiteralPath</span></span>

<span data-ttu-id="757c4-278">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="757c4-278">Specifies a path to one or more locations.</span></span> <span data-ttu-id="757c4-279">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="757c4-279">The value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="757c4-280">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="757c4-280">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="757c4-281">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="757c4-281">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="757c4-282">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="757c4-282">Single quotation marks tell PowerShell to not interpret any characters as escape sequences.</span></span>

<span data-ttu-id="757c4-283">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="757c4-283">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralItems
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="757c4-284">-Name</span><span class="sxs-lookup"><span data-stu-id="757c4-284">-Name</span></span>

<span data-ttu-id="757c4-285">只取得位置中專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="757c4-285">Gets only the names of the items in the location.</span></span> <span data-ttu-id="757c4-286">輸出是可向下傳送管線給其他命令的字串物件。</span><span class="sxs-lookup"><span data-stu-id="757c4-286">The output is a string object that can be sent down the pipeline to other commands.</span></span> <span data-ttu-id="757c4-287">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="757c4-287">Wildcards are permitted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="757c4-288">-Path</span><span class="sxs-lookup"><span data-stu-id="757c4-288">-Path</span></span>

<span data-ttu-id="757c4-289">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="757c4-289">Specifies a path to one or more locations.</span></span> <span data-ttu-id="757c4-290">可使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="757c4-290">Wildcards are accepted.</span></span> <span data-ttu-id="757c4-291">預設位置是 () 的目前的目錄 `.` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-291">The default location is the current directory (`.`).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Items
Aliases:

Required: False
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="757c4-292">-ReadOnly</span><span class="sxs-lookup"><span data-stu-id="757c4-292">-ReadOnly</span></span>

<span data-ttu-id="757c4-293">若只要取得唯讀專案，請使用 **readonly** 參數或 **Attributes** 參數 **readonly** 屬性。</span><span class="sxs-lookup"><span data-stu-id="757c4-293">To get only read-only items, use the **ReadOnly** parameter or the **Attributes** parameter **ReadOnly** property.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ar

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="757c4-294">-Recurse</span><span class="sxs-lookup"><span data-stu-id="757c4-294">-Recurse</span></span>

<span data-ttu-id="757c4-295">取得指定之位置中的項目及那些位置中的所有子項目。</span><span class="sxs-lookup"><span data-stu-id="757c4-295">Gets the items in the specified locations and in all child items of the locations.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: s

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="757c4-296">-System</span><span class="sxs-lookup"><span data-stu-id="757c4-296">-System</span></span>

<span data-ttu-id="757c4-297">只取得系統檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="757c4-297">Gets only system files and directories.</span></span> <span data-ttu-id="757c4-298">若只要取得系統檔案和資料夾，請使用 **system** 參數或 **Attributes** 參數 **系統** 屬性。</span><span class="sxs-lookup"><span data-stu-id="757c4-298">To get only system files and folders, use the **System** parameter or **Attributes** parameter **System** property.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: as

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="757c4-299">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="757c4-299">CommonParameters</span></span>

<span data-ttu-id="757c4-300">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="757c4-300">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="757c4-301">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="757c4-301">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="757c4-302">輸入</span><span class="sxs-lookup"><span data-stu-id="757c4-302">INPUTS</span></span>

### <span data-ttu-id="757c4-303">System.String</span><span class="sxs-lookup"><span data-stu-id="757c4-303">System.String</span></span>

<span data-ttu-id="757c4-304">您可以使用管線將包含路徑的字串傳送至 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-304">You can pipe a string that contains a path to `Get-ChildItem`.</span></span>

## <span data-ttu-id="757c4-305">輸出</span><span class="sxs-lookup"><span data-stu-id="757c4-305">OUTPUTS</span></span>

### <span data-ttu-id="757c4-306">System.Object</span><span class="sxs-lookup"><span data-stu-id="757c4-306">System.Object</span></span>

<span data-ttu-id="757c4-307">傳回的物件類型 `Get-ChildItem` 取決於提供者磁片磁碟機路徑中的物件。</span><span class="sxs-lookup"><span data-stu-id="757c4-307">The type of object that `Get-ChildItem` returns is determined by the objects in the provider drive path.</span></span>

### <span data-ttu-id="757c4-308">System.String</span><span class="sxs-lookup"><span data-stu-id="757c4-308">System.String</span></span>

<span data-ttu-id="757c4-309">如果您使用 **Name** 參數，則會 `Get-ChildItem` 以字串形式傳回物件名稱。</span><span class="sxs-lookup"><span data-stu-id="757c4-309">If you use the **Name** parameter, `Get-ChildItem` returns the object names as strings.</span></span>

## <span data-ttu-id="757c4-310">注意</span><span class="sxs-lookup"><span data-stu-id="757c4-310">NOTES</span></span>

- <span data-ttu-id="757c4-311">`Get-ChildItem` 可以使用任何內建的別名、、和來執行 `ls` `dir` `gci` 。</span><span class="sxs-lookup"><span data-stu-id="757c4-311">`Get-ChildItem` can be run using any of the built-in aliases, `ls`, `dir`, and `gci`.</span></span> <span data-ttu-id="757c4-312">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="757c4-312">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="757c4-313">`Get-ChildItem` 預設不會取得隱藏的專案。</span><span class="sxs-lookup"><span data-stu-id="757c4-313">`Get-ChildItem` doesn't get hidden items by default.</span></span> <span data-ttu-id="757c4-314">若要取得隱藏的項目，請使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="757c4-314">To get hidden items, use the **Force** parameter.</span></span>
- <span data-ttu-id="757c4-315">此 `Get-ChildItem` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="757c4-315">The `Get-ChildItem` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="757c4-316">若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="757c4-316">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="757c4-317">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="757c4-317">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="757c4-318">相關連結</span><span class="sxs-lookup"><span data-stu-id="757c4-318">RELATED LINKS</span></span>

[<span data-ttu-id="757c4-319">about_Certificate_Provider</span><span class="sxs-lookup"><span data-stu-id="757c4-319">about_Certificate_Provider</span></span>](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)

[<span data-ttu-id="757c4-320">about_Providers</span><span class="sxs-lookup"><span data-stu-id="757c4-320">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="757c4-321">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="757c4-321">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="757c4-322">about_Registry_Provider</span><span class="sxs-lookup"><span data-stu-id="757c4-322">about_Registry_Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)

[<span data-ttu-id="757c4-323">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="757c4-323">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="757c4-324">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="757c4-324">Get-Alias</span></span>](../Microsoft.PowerShell.Utility/Get-Alias.md)

[<span data-ttu-id="757c4-325">Get-Item</span><span class="sxs-lookup"><span data-stu-id="757c4-325">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="757c4-326">Get-Location</span><span class="sxs-lookup"><span data-stu-id="757c4-326">Get-Location</span></span>](Get-Location.md)

[<span data-ttu-id="757c4-327">Get-Process</span><span class="sxs-lookup"><span data-stu-id="757c4-327">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="757c4-328">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="757c4-328">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="757c4-329">Split-Path</span><span class="sxs-lookup"><span data-stu-id="757c4-329">Split-Path</span></span>](Split-Path.md)
