---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 7bf349c82133b275f0539db7b78c3583d00da31c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203844"
---
# <span data-ttu-id="4187d-103">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="4187d-103">Compress-Archive</span></span>

## <span data-ttu-id="4187d-104">概要</span><span class="sxs-lookup"><span data-stu-id="4187d-104">SYNOPSIS</span></span>
<span data-ttu-id="4187d-105">從指定的檔案和目錄建立壓縮封存或壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-105">Creates a compressed archive, or zipped file, from specified files and directories.</span></span>

## <span data-ttu-id="4187d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4187d-106">SYNTAX</span></span>

### <span data-ttu-id="4187d-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="4187d-107">Path (Default)</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4187d-108">PathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="4187d-108">PathWithUpdate</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4187d-109">PathWithForce</span><span class="sxs-lookup"><span data-stu-id="4187d-109">PathWithForce</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4187d-110">LiteralPathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="4187d-110">LiteralPathWithUpdate</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4187d-111">LiteralPathWithForce</span><span class="sxs-lookup"><span data-stu-id="4187d-111">LiteralPathWithForce</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4187d-112">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4187d-112">LiteralPath</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4187d-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4187d-113">DESCRIPTION</span></span>

<span data-ttu-id="4187d-114">`Compress-Archive`Cmdlet 會從一或多個指定的檔案或目錄建立壓縮或壓縮的封存檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-114">The `Compress-Archive` cmdlet creates a compressed, or zipped, archive file from one or more specified files or directories.</span></span> <span data-ttu-id="4187d-115">封存會將多個檔案（具有選擇性壓縮）封裝成單一壓縮檔案，以方便散發和儲存。</span><span class="sxs-lookup"><span data-stu-id="4187d-115">An archive packages multiple files, with optional compression, into a single zipped file for easier distribution and storage.</span></span> <span data-ttu-id="4187d-116">您可以使用 **CompressionLevel** 參數所指定的壓縮演算法來壓縮封存檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-116">An archive file can be compressed by using the compression algorithm specified by the **CompressionLevel** parameter.</span></span>

<span data-ttu-id="4187d-117">此 `Compress-Archive` Cmdlet 會使用 Microsoft .NET API [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) 來壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-117">The `Compress-Archive` cmdlet uses the Microsoft .NET API [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) to compress files.</span></span>
<span data-ttu-id="4187d-118">檔案大小上限為 2 GB，因為基礎 API 有限制。</span><span class="sxs-lookup"><span data-stu-id="4187d-118">The maximum file size is 2 GB because there's a limitation of the underlying API.</span></span>

<span data-ttu-id="4187d-119">某些範例會使用展開來減少程式碼範例的行長度。</span><span class="sxs-lookup"><span data-stu-id="4187d-119">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="4187d-120">如需詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。</span><span class="sxs-lookup"><span data-stu-id="4187d-120">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="4187d-121">範例</span><span class="sxs-lookup"><span data-stu-id="4187d-121">EXAMPLES</span></span>

### <span data-ttu-id="4187d-122">範例1：壓縮檔案以建立保存檔案</span><span class="sxs-lookup"><span data-stu-id="4187d-122">Example 1: Compress files to create an archive file</span></span>

<span data-ttu-id="4187d-123">此範例會壓縮來自不同目錄的檔案，並建立封存檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-123">This example compresses files from different directories and creates an archive file.</span></span> <span data-ttu-id="4187d-124">萬用字元可用來取得具有特定副檔名的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-124">A wildcard is used to get all files with a particular file extension.</span></span> <span data-ttu-id="4187d-125">封存檔案中沒有目錄結構，因為 **路徑** 只會指定檔案名。</span><span class="sxs-lookup"><span data-stu-id="4187d-125">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="4187d-126">**Path** 參數接受具有萬用字元的特定檔案名和檔案名 `*.vsd` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-126">The **Path** parameter accepts specific file names and file names with wildcards, `*.vsd`.</span></span> <span data-ttu-id="4187d-127">**路徑** 使用以逗號分隔的清單，從不同的目錄中取得檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-127">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="4187d-128">壓縮等級是 **最快** 的，可縮短處理時間。</span><span class="sxs-lookup"><span data-stu-id="4187d-128">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="4187d-129">**DestinationPath** 參數會指定檔案的位置 `Draft.zip` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-129">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="4187d-130">檔案 `Draft.zip` 包含 `Draftdoc.docx` 和所有副檔名為的檔案 `.vsd` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-130">The `Draft.zip` file contains `Draftdoc.docx` and all the files with a `.vsd` extension.</span></span>

### <span data-ttu-id="4187d-131">範例2：使用 LiteralPath 壓縮檔案</span><span class="sxs-lookup"><span data-stu-id="4187d-131">Example 2: Compress files using a LiteralPath</span></span>

<span data-ttu-id="4187d-132">此範例會壓縮特定的命名檔案，並建立新的封存檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-132">This example compresses specific named files and creates a new archive file.</span></span> <span data-ttu-id="4187d-133">封存檔案中沒有目錄結構，因為 **路徑** 只會指定檔案名。</span><span class="sxs-lookup"><span data-stu-id="4187d-133">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="4187d-134">因為 **LiteralPath** 參數不接受萬用字元，所以會使用絕對路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="4187d-134">Absolute path and file names are used because the **LiteralPath** parameter doesn't accept wildcards.</span></span> <span data-ttu-id="4187d-135">**路徑** 使用以逗號分隔的清單，從不同的目錄中取得檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-135">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="4187d-136">壓縮等級是 **最快** 的，可縮短處理時間。</span><span class="sxs-lookup"><span data-stu-id="4187d-136">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="4187d-137">**DestinationPath** 參數會指定檔案的位置 `Draft.zip` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-137">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="4187d-138">檔案 `Draft.zip` 僅包含 `Draftdoc.docx` 和 `diagram2.vsd` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-138">The `Draft.zip` file only contains `Draftdoc.docx` and `diagram2.vsd`.</span></span>

### <span data-ttu-id="4187d-139">範例3：壓縮包含根目錄的目錄</span><span class="sxs-lookup"><span data-stu-id="4187d-139">Example 3: Compress a directory that includes the root directory</span></span>

<span data-ttu-id="4187d-140">此範例會壓縮目錄並建立封存檔案，其中 **包含** 根目錄及其所有檔案和子目錄。</span><span class="sxs-lookup"><span data-stu-id="4187d-140">This example compresses a directory and creates an archive file that **includes** the root directory, and all its files and subdirectories.</span></span> <span data-ttu-id="4187d-141">封存檔案具有目錄結構，因為 **路徑** 指定了根目錄。</span><span class="sxs-lookup"><span data-stu-id="4187d-141">The archive file has a directory structure because the **Path** specifies a root directory.</span></span>

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="4187d-142">`Compress-Archive` 使用 **Path** 參數來指定根目錄 `C:\Reference` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-142">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference`.</span></span> <span data-ttu-id="4187d-143">**DestinationPath** 參數會指定保存檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="4187d-143">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="4187d-144">封存 `Draft.zip` 包含 `Reference` 根目錄及其所有檔案和子目錄。</span><span class="sxs-lookup"><span data-stu-id="4187d-144">The `Draft.zip` archive includes the `Reference` root directory, and all its files and subdirectories.</span></span>

### <span data-ttu-id="4187d-145">範例4：壓縮排除根目錄的目錄</span><span class="sxs-lookup"><span data-stu-id="4187d-145">Example 4: Compress a directory that excludes the root directory</span></span>

<span data-ttu-id="4187d-146">此範例會壓縮目錄並建立保存 **根目錄的封存** 盤案，因為 **路徑** 使用星號 (`*`) 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4187d-146">This example compresses a directory and creates an archive file that **excludes** the root directory because the **Path** uses an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="4187d-147">封存包含目錄結構，其中包含根目錄的檔案和子目錄。</span><span class="sxs-lookup"><span data-stu-id="4187d-147">The archive contains a directory structure that contains the root directory's files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="4187d-148">`Compress-Archive` 使用 **Path** 參數指定根目錄， `C:\Reference` 並以星號 (`*`) 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4187d-148">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="4187d-149">**DestinationPath** 參數會指定保存檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="4187d-149">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="4187d-150">封存 `Draft.zip` 包含根目錄的檔案和子目錄。</span><span class="sxs-lookup"><span data-stu-id="4187d-150">The `Draft.zip` archive contains the root directory's files and subdirectories.</span></span> <span data-ttu-id="4187d-151">`Reference`從封存中排除根目錄。</span><span class="sxs-lookup"><span data-stu-id="4187d-151">The `Reference` root directory is excluded from the archive.</span></span>

### <span data-ttu-id="4187d-152">範例5：只壓縮根目錄中的檔案</span><span class="sxs-lookup"><span data-stu-id="4187d-152">Example 5: Compress only the files in a root directory</span></span>

<span data-ttu-id="4187d-153">此範例只會壓縮根目錄中的檔案，並建立封存檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-153">This example compresses only the files in a root directory and creates an archive file.</span></span> <span data-ttu-id="4187d-154">封存中沒有目錄結構，因為只會壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-154">There's no directory structure in the archive because only files are compressed.</span></span>

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="4187d-155">`Compress-Archive` 使用 **Path** 參數指定根目錄， `C:\Reference` 並以 **星形點星號** (`*.*`) 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4187d-155">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with a **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="4187d-156">**DestinationPath** 參數會指定保存檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="4187d-156">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="4187d-157">封存 `Draft.zip` 只 `Reference` 會包含根目錄的檔案，而且會排除根目錄。</span><span class="sxs-lookup"><span data-stu-id="4187d-157">The `Draft.zip` archive only contains the `Reference` root directory's files and the root directory is excluded.</span></span>

### <span data-ttu-id="4187d-158">範例6：使用管線來保存檔案</span><span class="sxs-lookup"><span data-stu-id="4187d-158">Example 6: Use the pipeline to archive files</span></span>

<span data-ttu-id="4187d-159">此範例會將檔案傳送至管線，以建立封存。</span><span class="sxs-lookup"><span data-stu-id="4187d-159">This example sends files down the pipeline to create an archive.</span></span> <span data-ttu-id="4187d-160">封存檔案中沒有目錄結構，因為 **路徑** 只會指定檔案名。</span><span class="sxs-lookup"><span data-stu-id="4187d-160">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

<span data-ttu-id="4187d-161">`Get-ChildItem` 使用 **Path** 參數來指定不同目錄中的兩個檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-161">`Get-ChildItem` uses the **Path** parameter to specify two files from different directories.</span></span> <span data-ttu-id="4187d-162">每個檔案都是由 **FileInfo** 物件表示，並且會向下傳送到管線 `Compress-Archive` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-162">Each file is represented by a **FileInfo** object and is sent down the pipeline to `Compress-Archive`.</span></span>
<span data-ttu-id="4187d-163">這兩個指定的檔案會封存在中 `PipelineFiles.zip` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-163">The two specified files are archived in `PipelineFiles.zip`.</span></span>

### <span data-ttu-id="4187d-164">範例7：使用管線來保存目錄</span><span class="sxs-lookup"><span data-stu-id="4187d-164">Example 7: Use the pipeline to archive a directory</span></span>

<span data-ttu-id="4187d-165">此範例會將目錄向下傳送至管線以建立封存。</span><span class="sxs-lookup"><span data-stu-id="4187d-165">This example sends a directory down the pipeline to create an archive.</span></span> <span data-ttu-id="4187d-166">檔案會以 **FileInfo** 物件和目錄的形式傳送到 **DirectoryInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="4187d-166">Files are sent as **FileInfo** objects and directories as **DirectoryInfo** objects.</span></span> <span data-ttu-id="4187d-167">封存的目錄結構不包含根目錄，但其檔案和子目錄會包含在封存中。</span><span class="sxs-lookup"><span data-stu-id="4187d-167">The archive's directory structure doesn't include the root directory, but its files and subdirectories are included in the archive.</span></span>

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

<span data-ttu-id="4187d-168">`Get-ChildItem` 使用 **Path** 參數來指定 `C:\LogFiles` 根目錄。</span><span class="sxs-lookup"><span data-stu-id="4187d-168">`Get-ChildItem` uses the **Path** parameter to specify the `C:\LogFiles` root directory.</span></span> <span data-ttu-id="4187d-169">每個 **FileInfo** 和 **DirectoryInfo** 物件都會沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="4187d-169">Each **FileInfo** and **DirectoryInfo** object is sent down the pipeline.</span></span>

<span data-ttu-id="4187d-170">`Compress-Archive` 將每個物件新增至封存 `PipelineDir.zip` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-170">`Compress-Archive` adds each object to the `PipelineDir.zip` archive.</span></span> <span data-ttu-id="4187d-171">未指定 **Path** 參數，因為管線物件已接收到參數位置0。</span><span class="sxs-lookup"><span data-stu-id="4187d-171">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

### <span data-ttu-id="4187d-172">範例8：遞迴會如何影響封存</span><span class="sxs-lookup"><span data-stu-id="4187d-172">Example 8: How recursion can affect archives</span></span>

<span data-ttu-id="4187d-173">此範例顯示遞迴如何在封存中複製檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-173">This example shows how recursion can duplicate files in your archive.</span></span> <span data-ttu-id="4187d-174">例如，如果您使用 `Get-ChildItem` With **遞迴** 參數。</span><span class="sxs-lookup"><span data-stu-id="4187d-174">For example, if you use `Get-ChildItem` with the **Recurse** parameter.</span></span> <span data-ttu-id="4187d-175">作為遞迴進程，每個 **FileInfo** 和 **DirectoryInfo** 物件都會向下傳送到該管線，並新增至封存。</span><span class="sxs-lookup"><span data-stu-id="4187d-175">As recursion processes, each **FileInfo** and **DirectoryInfo** object is sent down the pipeline and added to the archive.</span></span>

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

<span data-ttu-id="4187d-176">`C:\TestLog`目錄不包含任何檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-176">The `C:\TestLog` directory doesn't contain any files.</span></span> <span data-ttu-id="4187d-177">它包含名為 `testsub` 且包含檔案的子目錄 `testlog.txt` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-177">It does contain a subdirectory named `testsub` that contains the `testlog.txt` file.</span></span>

<span data-ttu-id="4187d-178">`Get-ChildItem` 使用 **Path** 參數來指定根目錄 `C:\TestLog` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-178">`Get-ChildItem` uses the **Path** parameter to specify the root directory, `C:\TestLog`.</span></span> <span data-ttu-id="4187d-179">**遞迴** 參數會處理檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="4187d-179">The **Recurse** parameter processes the files and directories.</span></span> <span data-ttu-id="4187d-180">建立 **DirectoryInfo** 物件 `testsub` ，以及 **FileInfo** 物件 `testlog.txt` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-180">A **DirectoryInfo** object is created for `testsub` and a **FileInfo** object `testlog.txt`.</span></span>

<span data-ttu-id="4187d-181">每個物件都會向下傳送到管線 `Compress-Archive` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-181">Each object is sent down the pipeline to `Compress-Archive`.</span></span> <span data-ttu-id="4187d-182">**DestinationPath** 指定保存檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="4187d-182">The **DestinationPath** specifies the location for the archive file.</span></span> <span data-ttu-id="4187d-183">未指定 **Path** 參數，因為管線物件已接收到參數位置0。</span><span class="sxs-lookup"><span data-stu-id="4187d-183">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

<span data-ttu-id="4187d-184">下列摘要描述 `PipelineRecurse.zip` 包含重複檔案的封存內容：</span><span class="sxs-lookup"><span data-stu-id="4187d-184">The following summary describes the `PipelineRecurse.zip` archive's contents that contains a duplicate file:</span></span>

- <span data-ttu-id="4187d-185">**DirectoryInfo** 物件會建立 `testsub` 目錄，並包含 `testlog.txt` 可反映原始目錄結構的檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-185">The **DirectoryInfo** object creates the `testsub` directory and contains the `testlog.txt` file, which reflects the original directory structure.</span></span>
- <span data-ttu-id="4187d-186">**FileInfo** 物件會 `testlog.txt` 在保存庫的根目錄中建立重複的。</span><span class="sxs-lookup"><span data-stu-id="4187d-186">The **FileInfo** object creates a duplicate `testlog.txt` in the archive's root.</span></span> <span data-ttu-id="4187d-187">由於遞迴將檔案物件傳送至，所以會建立重複的檔案 `Compress-Archive` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-187">The duplicate file is created because recursion sent a file object to `Compress-Archive`.</span></span> <span data-ttu-id="4187d-188">這是預期的行為，因為管線中傳送的每個物件都會新增至封存。</span><span class="sxs-lookup"><span data-stu-id="4187d-188">This behavior is expected because each object sent down the pipeline is added to the archive.</span></span>

### <span data-ttu-id="4187d-189">範例9：更新現有的封存檔案</span><span class="sxs-lookup"><span data-stu-id="4187d-189">Example 9: Update an existing archive file</span></span>

<span data-ttu-id="4187d-190">此範例會更新目錄中的現有封存檔案 `Draft.Zip` `C:\Archives` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-190">This example updates an existing archive file, `Draft.Zip`, in the `C:\Archives` directory.</span></span> <span data-ttu-id="4187d-191">在此範例中，現有的封存檔案包含根目錄及其檔案和子目錄。</span><span class="sxs-lookup"><span data-stu-id="4187d-191">In this example, the existing archive file contains the root directory, and its files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

<span data-ttu-id="4187d-192">此命令會更新 `Draft.Zip` `C:\Reference` 目錄及其子目錄中現有檔案的較新版本。</span><span class="sxs-lookup"><span data-stu-id="4187d-192">The command updates `Draft.Zip` with newer versions of existing files in the `C:\Reference` directory and its subdirectories.</span></span> <span data-ttu-id="4187d-193">此外，已新增至 `C:\Reference` 或其子目錄的新檔案會包含在更新的封存中 `Draft.Zip` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-193">And, new files that were added to `C:\Reference` or its subdirectories are included in the updated `Draft.Zip` archive.</span></span>

## <span data-ttu-id="4187d-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4187d-194">PARAMETERS</span></span>

### <span data-ttu-id="4187d-195">-CompressionLevel</span><span class="sxs-lookup"><span data-stu-id="4187d-195">-CompressionLevel</span></span>

<span data-ttu-id="4187d-196">指定當您在建立封存檔案時要套用多少壓縮。</span><span class="sxs-lookup"><span data-stu-id="4187d-196">Specifies how much compression to apply when you're creating the archive file.</span></span> <span data-ttu-id="4187d-197">更快的壓縮需要較少的時間來建立檔案，但可能會產生較大的檔案大小。</span><span class="sxs-lookup"><span data-stu-id="4187d-197">Faster compression requires less time to create the file, but can result in larger file sizes.</span></span>

<span data-ttu-id="4187d-198">如果未指定此參數，此命令會使用預設值 [ **最佳** ]。</span><span class="sxs-lookup"><span data-stu-id="4187d-198">If this parameter isn't specified, the command uses the default value, **Optimal** .</span></span>

<span data-ttu-id="4187d-199">以下是此參數可接受的值：</span><span class="sxs-lookup"><span data-stu-id="4187d-199">The following are the acceptable values for this parameter:</span></span>

- <span data-ttu-id="4187d-200">**最快速** 。</span><span class="sxs-lookup"><span data-stu-id="4187d-200">**Fastest** .</span></span> <span data-ttu-id="4187d-201">使用可用的最快壓縮方法來減少處理時間。</span><span class="sxs-lookup"><span data-stu-id="4187d-201">Use the fastest compression method available to reduce processing time.</span></span> <span data-ttu-id="4187d-202">更快的壓縮可能會產生較大的檔案大小。</span><span class="sxs-lookup"><span data-stu-id="4187d-202">Faster compression can result in larger file sizes.</span></span>
- <span data-ttu-id="4187d-203">**NoCompression** 。</span><span class="sxs-lookup"><span data-stu-id="4187d-203">**NoCompression** .</span></span> <span data-ttu-id="4187d-204">不會壓縮原始檔案案。</span><span class="sxs-lookup"><span data-stu-id="4187d-204">Doesn't compress the source files.</span></span>
- <span data-ttu-id="4187d-205">**最佳** ：</span><span class="sxs-lookup"><span data-stu-id="4187d-205">**Optimal** .</span></span> <span data-ttu-id="4187d-206">處理時間取決於檔案大小。</span><span class="sxs-lookup"><span data-stu-id="4187d-206">Processing time is dependent on file size.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Optimal, NoCompression, Fastest

Required: False
Position: Named
Default value: Optimal
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4187d-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4187d-207">-Confirm</span></span>

<span data-ttu-id="4187d-208">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="4187d-208">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4187d-209">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="4187d-209">-DestinationPath</span></span>

<span data-ttu-id="4187d-210">此為必要參數，並指定封存輸出檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4187d-210">This parameter is required and specifies the path to the archive output file.</span></span> <span data-ttu-id="4187d-211">**DestinationPath** 應該包含 zip 壓縮檔案的名稱，以及壓縮檔案的絕對或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="4187d-211">The **DestinationPath** should include the name of the zipped file, and either the absolute or relative path to the zipped file.</span></span>

<span data-ttu-id="4187d-212">如果 **DestinationPath** 中的檔案名沒有 `.zip` 副檔名，此 Cmdlet 會加入副檔名 `.zip` 。</span><span class="sxs-lookup"><span data-stu-id="4187d-212">If the file name in **DestinationPath** doesn't have a `.zip` file name extension, the cmdlet adds the `.zip` file name extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4187d-213">-Force</span><span class="sxs-lookup"><span data-stu-id="4187d-213">-Force</span></span>

<span data-ttu-id="4187d-214">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="4187d-214">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithForce, LiteralPathWithForce
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4187d-215">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4187d-215">-LiteralPath</span></span>

<span data-ttu-id="4187d-216">指定您想要新增至封存壓縮檔案的檔案路徑或路徑。</span><span class="sxs-lookup"><span data-stu-id="4187d-216">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="4187d-217">與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="4187d-217">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="4187d-218">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4187d-218">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="4187d-219">如果路徑包含 escape 字元，請用單引號括住每個 escape 字元，以指示 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="4187d-219">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>
<span data-ttu-id="4187d-220">若要指定多個路徑，並將檔案包含在輸出壓縮檔案中的多個位置，請使用逗號來分隔路徑。</span><span class="sxs-lookup"><span data-stu-id="4187d-220">To specify multiple paths, and include files in multiple locations in your output zipped file, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathWithUpdate, LiteralPathWithForce, LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4187d-221">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4187d-221">-PassThru</span></span>

<span data-ttu-id="4187d-222">導致 Cmdlet 輸出檔案物件，代表已建立的封存檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-222">Causes the cmdlet to output a file object representing the archive file created.</span></span>

<span data-ttu-id="4187d-223">此參數是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="4187d-223">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="4187d-224">-Path</span><span class="sxs-lookup"><span data-stu-id="4187d-224">-Path</span></span>

<span data-ttu-id="4187d-225">指定您想要新增至封存壓縮檔案的檔案路徑或路徑。</span><span class="sxs-lookup"><span data-stu-id="4187d-225">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="4187d-226">若要指定多個路徑，並將檔案包含在多個位置，請使用逗號來分隔路徑。</span><span class="sxs-lookup"><span data-stu-id="4187d-226">To specify multiple paths, and include files in multiple locations, use commas to separate the paths.</span></span>

<span data-ttu-id="4187d-227">此參數接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4187d-227">This parameter accepts wildcard characters.</span></span> <span data-ttu-id="4187d-228">萬用字元可讓您將目錄中的所有檔案新增至您的封存檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-228">Wildcard characters allow you to add all files in a directory to your archive file.</span></span>

<span data-ttu-id="4187d-229">使用萬用字元搭配根目錄會影響封存的內容：</span><span class="sxs-lookup"><span data-stu-id="4187d-229">Using wildcards with a root directory affects the archive's contents:</span></span>

- <span data-ttu-id="4187d-230">若要建立 **包含** 根目錄及其所有檔案和子目錄的封存，請在 **路徑** 中指定不含萬用字元的根目錄。</span><span class="sxs-lookup"><span data-stu-id="4187d-230">To create an archive that **includes** the root directory, and all its files and subdirectories, specify the root directory in the **Path** without wildcards.</span></span> <span data-ttu-id="4187d-231">例如：`-Path C:\Reference`</span><span class="sxs-lookup"><span data-stu-id="4187d-231">For example: `-Path C:\Reference`</span></span>
- <span data-ttu-id="4187d-232">若要建立封存以 **排除** 根目錄，但 zips 其所有檔案和子目錄，請使用星號 (`*`) 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4187d-232">To create an archive that **excludes** the root directory, but zips all its files and subdirectories, use the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="4187d-233">例如：`-Path C:\Reference\*`</span><span class="sxs-lookup"><span data-stu-id="4187d-233">For example: `-Path C:\Reference\*`</span></span>
- <span data-ttu-id="4187d-234">若要建立只 zips 根目錄中檔案的封存，請使用 **星號--星號** (`*.*`) 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4187d-234">To create an archive that only zips the files in the root directory, use the **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="4187d-235">根目錄的子目錄不包含在封存中。</span><span class="sxs-lookup"><span data-stu-id="4187d-235">Subdirectories of the root aren't included in the archive.</span></span> <span data-ttu-id="4187d-236">例如：`-Path C:\Reference\*.*`</span><span class="sxs-lookup"><span data-stu-id="4187d-236">For example: `-Path C:\Reference\*.*`</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path, PathWithUpdate, PathWithForce
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="4187d-237">-更新</span><span class="sxs-lookup"><span data-stu-id="4187d-237">-Update</span></span>

<span data-ttu-id="4187d-238">將封存中較舊的檔案版本取代為具有相同名稱的較新檔案版本，以更新指定的封存。</span><span class="sxs-lookup"><span data-stu-id="4187d-238">Updates the specified archive by replacing older file versions in the archive with newer file versions that have the same names.</span></span> <span data-ttu-id="4187d-239">您也可以新增此參數，以將檔案新增至現有的封存。</span><span class="sxs-lookup"><span data-stu-id="4187d-239">You can also add this parameter to add files to an existing archive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithUpdate, LiteralPathWithUpdate
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4187d-240">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4187d-240">-WhatIf</span></span>

<span data-ttu-id="4187d-241">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="4187d-241">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4187d-242">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4187d-242">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="4187d-243">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4187d-243">CommonParameters</span></span>

<span data-ttu-id="4187d-244">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4187d-244">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4187d-245">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4187d-245">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4187d-246">輸入</span><span class="sxs-lookup"><span data-stu-id="4187d-246">INPUTS</span></span>

### <span data-ttu-id="4187d-247">System.String</span><span class="sxs-lookup"><span data-stu-id="4187d-247">System.String</span></span>

<span data-ttu-id="4187d-248">您可以使用管線將包含路徑的字串傳送至一或多個檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-248">You can pipe a string that contains a path to one or more files.</span></span>

## <span data-ttu-id="4187d-249">輸出</span><span class="sxs-lookup"><span data-stu-id="4187d-249">OUTPUTS</span></span>

### <span data-ttu-id="4187d-250">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="4187d-250">System.IO.FileInfo</span></span>

<span data-ttu-id="4187d-251">當您使用 **PassThru** 參數時，此 Cmdlet 只會傳回 **FileInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="4187d-251">The cmdlet only returns a **FileInfo** object when you use the **PassThru** parameter.</span></span>

## <span data-ttu-id="4187d-252">注意</span><span class="sxs-lookup"><span data-stu-id="4187d-252">NOTES</span></span>

<span data-ttu-id="4187d-253">使用遞迴並將物件沿著管線向下傳送，可以在您的封存中複製檔案。</span><span class="sxs-lookup"><span data-stu-id="4187d-253">Using recursion and sending objects down the pipeline can duplicate files in your archive.</span></span> <span data-ttu-id="4187d-254">例如，如果您使用 `Get-ChildItem` With **遞迴** 參數，則每個向下傳送管線的 **FileInfo** 和 **DirectoryInfo** 物件都會新增至封存。</span><span class="sxs-lookup"><span data-stu-id="4187d-254">For example, if you use `Get-ChildItem` with the **Recurse** parameter, each **FileInfo** and **DirectoryInfo** object that's sent down the pipeline is added to the archive.</span></span>

<span data-ttu-id="4187d-255">[ZIP 檔案規格](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)不會指定編碼包含非 ASCII 字元之檔案名的標準方式。</span><span class="sxs-lookup"><span data-stu-id="4187d-255">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="4187d-256">此 `Compress-Archive` Cmdlet 會使用 utf-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="4187d-256">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="4187d-257">其他 ZIP 封存工具可能會使用不同的編碼配置。</span><span class="sxs-lookup"><span data-stu-id="4187d-257">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="4187d-258">使用 UTF-8 編碼方式解壓縮未儲存的檔案時，會使用在封存 `Expand-Archive` 中找到的原始值。</span><span class="sxs-lookup"><span data-stu-id="4187d-258">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="4187d-259">這可能會產生與儲存在封存中的來原始檔案名不同的檔案名。</span><span class="sxs-lookup"><span data-stu-id="4187d-259">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="4187d-260">相關連結</span><span class="sxs-lookup"><span data-stu-id="4187d-260">RELATED LINKS</span></span>

[<span data-ttu-id="4187d-261">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="4187d-261">Expand-Archive</span></span>](Expand-Archive.md)

[<span data-ttu-id="4187d-262">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4187d-262">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)
