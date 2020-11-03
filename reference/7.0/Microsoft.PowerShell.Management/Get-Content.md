---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Content
ms.openlocfilehash: 1409522cffc2dde2cc5002049126bcfaa30ce846
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201471"
---
# <span data-ttu-id="c0a54-103">Get-Content</span><span class="sxs-lookup"><span data-stu-id="c0a54-103">Get-Content</span></span>

## <span data-ttu-id="c0a54-104">概要</span><span class="sxs-lookup"><span data-stu-id="c0a54-104">SYNOPSIS</span></span>
<span data-ttu-id="c0a54-105">在指定的位置取得項目的內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-105">Gets the content of the item at the specified location.</span></span>

## <span data-ttu-id="c0a54-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c0a54-106">SYNTAX</span></span>

### <span data-ttu-id="c0a54-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="c0a54-107">Path (Default)</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="c0a54-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c0a54-108">LiteralPath</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="c0a54-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c0a54-109">DESCRIPTION</span></span>

<span data-ttu-id="c0a54-110">`Get-Content`Cmdlet 會在路徑指定的位置取得專案的內容，例如檔案中的文字或函式的內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-110">The `Get-Content` cmdlet gets the content of the item at the location specified by the path, such as the text in a file or the content of a function.</span></span> <span data-ttu-id="c0a54-111">針對檔案，會一次讀取一行內容，並傳回物件的集合，每個物件都代表一個內容行。</span><span class="sxs-lookup"><span data-stu-id="c0a54-111">For files, the content is read one line at a time and returns a collection of objects, each of which represents a line of content.</span></span>

<span data-ttu-id="c0a54-112">從 PowerShell 3.0 開始， `Get-Content` 也可以從專案的開頭或結尾取得指定的行數。</span><span class="sxs-lookup"><span data-stu-id="c0a54-112">Beginning in PowerShell 3.0, `Get-Content` can also get a specified number of lines from the beginning or end of an item.</span></span>

## <span data-ttu-id="c0a54-113">範例</span><span class="sxs-lookup"><span data-stu-id="c0a54-113">EXAMPLES</span></span>

### <span data-ttu-id="c0a54-114">範例 1︰取得文字檔的內容</span><span class="sxs-lookup"><span data-stu-id="c0a54-114">Example 1: Get the content of a text file</span></span>

<span data-ttu-id="c0a54-115">這個範例會取得目前目錄中檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-115">This example gets the content of a file in the current directory.</span></span> <span data-ttu-id="c0a54-116">檔案 `LineNumbers.txt` 包含100行（格式為）， **這是第 X 行** ，在數個範例中使用。</span><span class="sxs-lookup"><span data-stu-id="c0a54-116">The `LineNumbers.txt` file contains 100 lines in the format, **This is Line X** and is used in several examples.</span></span>

```powershell
1..100 | ForEach-Object { Add-Content -Path .\LineNumbers.txt -Value "This is line $_." }
Get-Content -Path .\LineNumbers.txt
```

```Output
This is Line 1
This is Line 2
...
This is line 99.
This is line 100.
```

<span data-ttu-id="c0a54-117">陣列值1-100 會將管線向下傳送至 `ForEach-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0a54-117">The array values 1-100 are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="c0a54-118">`ForEach-Object` 使用腳本區塊與 `Add-Content` Cmdlet 來建立檔案 `LineNumbers.txt` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-118">`ForEach-Object` uses a script block with the `Add-Content` cmdlet to create the `LineNumbers.txt` file.</span></span> <span data-ttu-id="c0a54-119">變數 `$_` 代表陣列值，因為每個物件都會向下傳送管線。</span><span class="sxs-lookup"><span data-stu-id="c0a54-119">The variable `$_` represents the array values as each object is sent down the pipeline.</span></span> <span data-ttu-id="c0a54-120">此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定檔案 `LineNumbers.txt` ，並在 PowerShell 主控台中顯示內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-120">The `Get-Content` cmdlet uses the **Path** parameter to specify the `LineNumbers.txt` file and displays the content in the PowerShell console.</span></span>

### <span data-ttu-id="c0a54-121">範例2：限制傳回的行數 Get-Content</span><span class="sxs-lookup"><span data-stu-id="c0a54-121">Example 2: Limit the number of lines Get-Content returns</span></span>

<span data-ttu-id="c0a54-122">此命令會取得檔案的前五行。</span><span class="sxs-lookup"><span data-stu-id="c0a54-122">This command gets the first five lines of a file.</span></span> <span data-ttu-id="c0a54-123">**TotalCount** 參數是用來取得前五行的內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-123">The **TotalCount** parameter is used to gets the first five lines of content.</span></span> <span data-ttu-id="c0a54-124">此範例會使用 `LineNumbers.txt` 範例1中所建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="c0a54-124">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Content -Path .\LineNumbers.txt -TotalCount 5
```

```Output
This is Line 1
This is Line 2
This is Line 3
This is Line 4
This is Line 5
```

### <span data-ttu-id="c0a54-125">範例3：從文字檔取得特定的內容行</span><span class="sxs-lookup"><span data-stu-id="c0a54-125">Example 3: Get a specific line of content from a text file</span></span>

<span data-ttu-id="c0a54-126">此命令會從檔案取得特定數目的行，然後只顯示該內容的最後一行。</span><span class="sxs-lookup"><span data-stu-id="c0a54-126">This command gets a specific number of lines from a file and then displays only the last line of that content.</span></span> <span data-ttu-id="c0a54-127">**TotalCount** 參數會取得前25行的內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-127">The **TotalCount** parameter gets the first 25 lines of content.</span></span> <span data-ttu-id="c0a54-128">此範例會使用 `LineNumbers.txt` 範例1中所建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="c0a54-128">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

<span data-ttu-id="c0a54-129">此 `Get-Content` 命令會以括弧括住，讓命令完成後再繼續下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="c0a54-129">The `Get-Content` command is wrapped in parentheses so that the command completes before going to the next step.</span></span> <span data-ttu-id="c0a54-130">`Get-Content`傳回線條的陣列，這可讓您在括弧之後加入索引標記法，以抓取特定行號。</span><span class="sxs-lookup"><span data-stu-id="c0a54-130">`Get-Content`returns an array of lines, this allows you to add the index notation after the parenthesis to retrieve a specific line number.</span></span> <span data-ttu-id="c0a54-131">在此情況下， `[-1]` 索引會在傳回的陣列中指定25個抓取行的最後一個索引。</span><span class="sxs-lookup"><span data-stu-id="c0a54-131">In this case, the `[-1]` index specifies the last index in the returned array of 25 retrieved lines.</span></span>

### <span data-ttu-id="c0a54-132">範例4：取得文字檔的最後一行</span><span class="sxs-lookup"><span data-stu-id="c0a54-132">Example 4: Get the last line of a text file</span></span>

<span data-ttu-id="c0a54-133">此命令會從檔案取得第一行和最後一行的內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-133">This command gets the first line and last line of content from a file.</span></span> <span data-ttu-id="c0a54-134">此範例會使用 `LineNumbers.txt` 範例1中所建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="c0a54-134">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

<span data-ttu-id="c0a54-135">此範例會使用 `Get-Item` Cmdlet 來示範您可以使用管線將檔案傳送至 `Get-Content` 參數。</span><span class="sxs-lookup"><span data-stu-id="c0a54-135">This example uses the `Get-Item` cmdlet to demonstrate that you can pipe files into the `Get-Content` parameter.</span></span> <span data-ttu-id="c0a54-136">**Tail** 參數會取得檔案的最後一行。</span><span class="sxs-lookup"><span data-stu-id="c0a54-136">The **Tail** parameter gets the last line of the file.</span></span> <span data-ttu-id="c0a54-137">這個方法比取出所有行並使用 `[-1]` 索引標記法更快。</span><span class="sxs-lookup"><span data-stu-id="c0a54-137">This method is faster than retrieving all of the lines and using the `[-1]` index notation.</span></span>

### <span data-ttu-id="c0a54-138">範例5：取得替代資料流程的內容</span><span class="sxs-lookup"><span data-stu-id="c0a54-138">Example 5: Get the content of an alternate data stream</span></span>

<span data-ttu-id="c0a54-139">此範例描述如何使用 **Stream** 參數，取得儲存在 Windows NTFS 磁片區上之檔案的替代資料流程內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-139">This example describes how to use the **Stream** parameter to get the content of an alternate data stream for files stored on a Windows NTFS volume.</span></span> <span data-ttu-id="c0a54-140">在此範例中，此 `Set-Content` Cmdlet 是用來在名為的檔案中建立範例內容 `Stream.txt` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-140">In this example, the `Set-Content` cmdlet is used to create sample content in a file named `Stream.txt`.</span></span>

```powershell
Set-Content -Path .\Stream.txt -Value 'This is the content of the Stream.txt file'
# Specify a wildcard to the Stream parameter to display all streams of the recently created file.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44
```

```powershell
# Retrieve the content of the primary, or $DATA stream.
Get-Content -Path .\Stream.txt -Stream $DATA
```

```Output
This is the content of the Stream.txt file
```

```powershell
# Use the Stream parameter of Add-Content to create a new Stream containing sample content.
Add-Content -Path .\Stream.txt -Stream NewStream -Value 'Added a stream named NewStream to Stream.txt'
# Use Get-Item to verify the stream was created.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt:NewStream
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt:NewStream
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : NewStream
Length        : 46
```

```powershell
# Retrieve the content of your newly created Stream.
Get-Content -Path .\Stream.txt -Stream NewStream
```

```Output
Added a stream named NewStream to Stream.txt
```

<span data-ttu-id="c0a54-141">**Stream** 參數是 [FileSystem 提供者](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring)的動態參數。</span><span class="sxs-lookup"><span data-stu-id="c0a54-141">The **Stream** parameter is a dynamic parameter of the [FileSystem provider](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).</span></span>
<span data-ttu-id="c0a54-142">依預設 `Get-Content` ，只會從主要或資料流程抓取資料 `$DATA` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-142">By default `Get-Content` only retrieves data from the primary, or `$DATA` stream.</span></span> <span data-ttu-id="c0a54-143">**資料流程** 可以用來儲存隱藏的資料，例如屬性、安全性設定或其他資料。</span><span class="sxs-lookup"><span data-stu-id="c0a54-143">**Streams** can be used to store hidden data such as attributes, security settings, or other data.</span></span>

### <span data-ttu-id="c0a54-144">範例6：取得原始內容</span><span class="sxs-lookup"><span data-stu-id="c0a54-144">Example 6: Get raw content</span></span>

<span data-ttu-id="c0a54-145">此範例中的命令會將檔案的內容以一個字串的形式取得，而不是以字串陣列的形式取得。</span><span class="sxs-lookup"><span data-stu-id="c0a54-145">The commands in this example get the contents of a file as one string, instead of an array of strings.</span></span> <span data-ttu-id="c0a54-146">依預設，如果沒有 **Raw** 動態參數，則會以以分行符號分隔的字串陣列形式傳回內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-146">By default, without the **Raw** dynamic parameter, content is returned as an array of newline-delimited strings.</span></span> <span data-ttu-id="c0a54-147">此範例會使用 `LineNumbers.txt` 範例中所建立的檔案</span><span class="sxs-lookup"><span data-stu-id="c0a54-147">This example uses the `LineNumbers.txt` file that was created in Example</span></span>
1.

```powershell
$raw = Get-Content -Path .\LineNumbers.txt -Raw
$lines = Get-Content -Path .\LineNumbers.txt
Write-Host "Raw contains $($raw.Count) lines."
Write-Host "Lines contains $($lines.Count) lines."
```

```Output
Raw contains 1 lines.
Lines contains 100 lines.
```

### <span data-ttu-id="c0a54-148">範例7：搭配 Get-Content 使用篩選</span><span class="sxs-lookup"><span data-stu-id="c0a54-148">Example 7: Use Filters with Get-Content</span></span>

<span data-ttu-id="c0a54-149">您可以為 Cmdlet 指定篩選 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-149">You can specify a filter to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="c0a54-150">使用篩選準則來限定 **路徑** 參數時，您必須包含尾端星號 (`*`) 來指出路徑的內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-150">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="c0a54-151">下列命令會取得目錄中所有檔案的內容 `*.log` `C:\Temp` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-151">The following command gets the content of all `*.log` files in the `C:\Temp` directory.</span></span>

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### <span data-ttu-id="c0a54-152">範例8：以位元組陣列形式取得檔案內容</span><span class="sxs-lookup"><span data-stu-id="c0a54-152">Example 8: Get file contents as a byte array</span></span>

<span data-ttu-id="c0a54-153">這個範例示範如何以單一物件的形式取得檔案的內容 `[byte[]]` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-153">This example demonstrates how to get the contents of a file as a `[byte[]]` as a single object.</span></span>

```powershell
$byteArray = Get-Content -Path C:\temp\test.txt -AsByteStream -Raw
Get-Member -InputObject $bytearray
```

```Output
TypeName: System.Byte[]

Name           MemberType            Definition
----           ----------            ----------
Count          AliasProperty         Count = Length
Add            Method                int IList.Add(System.Object value)
```

<span data-ttu-id="c0a54-154">第一個命令會使用 **AsByteStream** 參數來取得檔案的位元組資料流程。</span><span class="sxs-lookup"><span data-stu-id="c0a54-154">The first command uses the **AsByteStream** parameter to get the stream of bytes from the file.</span></span>
<span data-ttu-id="c0a54-155">**Raw** 參數可確保傳回的位元組是 `[System.Byte[]]` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-155">The **Raw** parameter ensures that the bytes are returned as a `[System.Byte[]]`.</span></span> <span data-ttu-id="c0a54-156">如果未經處理 **的參數不** 存在，則傳回值為位元組資料流程，而 PowerShell 會將其視為 `[System.Object[]]` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-156">If the **Raw** parameter was absent, the return value is a stream of bytes, which is interpreted by PowerShell as `[System.Object[]]`.</span></span>

## <span data-ttu-id="c0a54-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c0a54-157">PARAMETERS</span></span>

### <span data-ttu-id="c0a54-158">-Path</span><span class="sxs-lookup"><span data-stu-id="c0a54-158">-Path</span></span>

<span data-ttu-id="c0a54-159">指定取得內容之專案的路徑 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-159">Specifies the path to an item where `Get-Content` gets the content.</span></span> <span data-ttu-id="c0a54-160">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c0a54-160">Wildcard characters are permitted.</span></span> <span data-ttu-id="c0a54-161">路徑需為項目的路徑，而非容器的路徑。</span><span class="sxs-lookup"><span data-stu-id="c0a54-161">The paths must be paths to items, not to containers.</span></span> <span data-ttu-id="c0a54-162">例如，您必須指定一或多個檔案的路徑，而非目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="c0a54-162">For example, you must specify a path to one or more files, not a path to a directory.</span></span>

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

### <span data-ttu-id="c0a54-163">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c0a54-163">-LiteralPath</span></span>

<span data-ttu-id="c0a54-164">指定一個或多個位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="c0a54-164">Specifies a path to one or more locations.</span></span> <span data-ttu-id="c0a54-165">**LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="c0a54-165">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="c0a54-166">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c0a54-166">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c0a54-167">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="c0a54-167">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c0a54-168">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="c0a54-168">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="c0a54-169">如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="c0a54-169">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="c0a54-170">-ReadCount</span><span class="sxs-lookup"><span data-stu-id="c0a54-170">-ReadCount</span></span>

<span data-ttu-id="c0a54-171">指定管線一次傳送多少行的內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-171">Specifies how many lines of content are sent through the pipeline at a time.</span></span> <span data-ttu-id="c0a54-172">預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="c0a54-172">The default value is 1.</span></span>
<span data-ttu-id="c0a54-173">值為 0 (零) 會一次傳送所有內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-173">A value of 0 (zero) sends all of the content at one time.</span></span>

<span data-ttu-id="c0a54-174">這個參數不會變更顯示的內容，但它會影響顯示內容所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="c0a54-174">This parameter does not change the content displayed, but it does affect the time it takes to display the content.</span></span> <span data-ttu-id="c0a54-175">隨著 **ReadCount** 的值增加，傳回第一行所花費的時間也會增加，但是作業的總時間減少。</span><span class="sxs-lookup"><span data-stu-id="c0a54-175">As the value of **ReadCount** increases, the time it takes to return the first line increases, but the total time for the operation decreases.</span></span> <span data-ttu-id="c0a54-176">這可能會造成大型專案的可察覺差異。</span><span class="sxs-lookup"><span data-stu-id="c0a54-176">This can make a perceptible difference in large items.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c0a54-177">-TotalCount</span><span class="sxs-lookup"><span data-stu-id="c0a54-177">-TotalCount</span></span>

<span data-ttu-id="c0a54-178">指定從檔案或其他項目的開頭算起的行數。</span><span class="sxs-lookup"><span data-stu-id="c0a54-178">Specifies the number of lines from the beginning of a file or other item.</span></span> <span data-ttu-id="c0a54-179">預設值為 -1 (所有行)。</span><span class="sxs-lookup"><span data-stu-id="c0a54-179">The default is -1 (all lines).</span></span>

<span data-ttu-id="c0a54-180">您可以使用 **TotalCount** 參數名稱或其別名 **First** 或 **Head** 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-180">You can use the **TotalCount** parameter name or its aliases, **First** or **Head** .</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: First, Head

Required: False
Position: Named
Default value: -1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c0a54-181">-Tail</span><span class="sxs-lookup"><span data-stu-id="c0a54-181">-Tail</span></span>

<span data-ttu-id="c0a54-182">指定從檔案或其他項目的結尾算起的行數。</span><span class="sxs-lookup"><span data-stu-id="c0a54-182">Specifies the number of lines from the end of a file or other item.</span></span> <span data-ttu-id="c0a54-183">您可以使用 **Tail** 參數名稱或其別名 **Last** 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-183">You can use the **Tail** parameter name or its alias, **Last** .</span></span> <span data-ttu-id="c0a54-184">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c0a54-184">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Last

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c0a54-185">-Filter</span><span class="sxs-lookup"><span data-stu-id="c0a54-185">-Filter</span></span>

<span data-ttu-id="c0a54-186">指定要限定 **路徑** 參數的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="c0a54-186">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="c0a54-187">[FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="c0a54-187">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="c0a54-188">您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。</span><span class="sxs-lookup"><span data-stu-id="c0a54-188">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="c0a54-189">篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。</span><span class="sxs-lookup"><span data-stu-id="c0a54-189">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="c0a54-190">-Include</span><span class="sxs-lookup"><span data-stu-id="c0a54-190">-Include</span></span>

<span data-ttu-id="c0a54-191">以字串陣列指定此 Cmdlet 在作業中納入的項目。</span><span class="sxs-lookup"><span data-stu-id="c0a54-191">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="c0a54-192">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="c0a54-192">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="c0a54-193">輸入路徑元素或模式，例如 `"*.txt"`。</span><span class="sxs-lookup"><span data-stu-id="c0a54-193">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="c0a54-194">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c0a54-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="c0a54-195">**Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-195">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c0a54-196">-Exclude</span><span class="sxs-lookup"><span data-stu-id="c0a54-196">-Exclude</span></span>

<span data-ttu-id="c0a54-197">以字串陣列指定此 Cmdlet 在作業中排除的專案。</span><span class="sxs-lookup"><span data-stu-id="c0a54-197">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span>
<span data-ttu-id="c0a54-198">此參數的值會限定 **Path** 參數。</span><span class="sxs-lookup"><span data-stu-id="c0a54-198">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="c0a54-199">輸入路徑元素或模式，例如 `*.txt`。</span><span class="sxs-lookup"><span data-stu-id="c0a54-199">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="c0a54-200">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c0a54-200">Wildcard characters are permitted.</span></span>

<span data-ttu-id="c0a54-201">只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-201">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="c0a54-202">-Force</span><span class="sxs-lookup"><span data-stu-id="c0a54-202">-Force</span></span>

<span data-ttu-id="c0a54-203">**Force** 會覆寫唯讀屬性或建立目錄來完成檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="c0a54-203">**Force** will override a read-only attribute or create directories to complete a file path.</span></span> <span data-ttu-id="c0a54-204">**Force** 參數不會嘗試變更檔案許可權或覆寫安全性限制。</span><span class="sxs-lookup"><span data-stu-id="c0a54-204">The **Force** parameter does not attempt to change file permissions or override security restrictions.</span></span>

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

### <span data-ttu-id="c0a54-205">-Credential</span><span class="sxs-lookup"><span data-stu-id="c0a54-205">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="c0a54-206">使用 PowerShell 安裝的任何提供者都不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="c0a54-206">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="c0a54-207">若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="c0a54-207">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="c0a54-208">-Delimiter</span><span class="sxs-lookup"><span data-stu-id="c0a54-208">-Delimiter</span></span>

<span data-ttu-id="c0a54-209">指定在 `Get-Content` 讀取時，用來將檔案分割成物件的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="c0a54-209">Specifies the delimiter that `Get-Content` uses to divide the file into objects while it reads.</span></span> <span data-ttu-id="c0a54-210">預設值為 `\n` ，行尾字元。</span><span class="sxs-lookup"><span data-stu-id="c0a54-210">The default is `\n`, the end-of-line character.</span></span> <span data-ttu-id="c0a54-211">讀取文字檔時，會傳回 `Get-Content` 字串物件的集合，每個物件的結尾都是行尾字元。</span><span class="sxs-lookup"><span data-stu-id="c0a54-211">When reading a text file, `Get-Content` returns a collection of string objects, each of which ends with an end-of-line character.</span></span> <span data-ttu-id="c0a54-212">當您輸入不存在於檔案中的分隔符號時，會 `Get-Content` 以單一未分隔物件的形式傳回整個檔案。</span><span class="sxs-lookup"><span data-stu-id="c0a54-212">When you enter a delimiter that does not exist in the file, `Get-Content` returns the entire file as a single, undelimited object.</span></span>

<span data-ttu-id="c0a54-213">您可以使用這個參數，藉由指定檔案分隔符號做為分隔符號，將大型檔案分割成較小的檔案。</span><span class="sxs-lookup"><span data-stu-id="c0a54-213">You can use this parameter to split a large file into smaller files by specifying a file separator, as the delimiter.</span></span> <span data-ttu-id="c0a54-214">分隔符號會保留 (不會被捨棄)，並成為每個檔案區段中的最後一個項目。</span><span class="sxs-lookup"><span data-stu-id="c0a54-214">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

<span data-ttu-id="c0a54-215">**分隔符號** 是動態參數， **FileSystem** 提供者會將它新增至 `Get-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0a54-215">**Delimiter** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="c0a54-216">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="c0a54-216">This parameter works only in file system drives.</span></span>

> [!NOTE]
> <span data-ttu-id="c0a54-217">目前，當 **分隔符號** 參數的值為空字串時，不 `Get-Content` 會傳回任何值。</span><span class="sxs-lookup"><span data-stu-id="c0a54-217">Currently, when the value of the **Delimiter** parameter is an empty string, `Get-Content` does not return anything.</span></span> <span data-ttu-id="c0a54-218">這是已知的問題。</span><span class="sxs-lookup"><span data-stu-id="c0a54-218">This is a known issue.</span></span> <span data-ttu-id="c0a54-219">強制 `Get-Content` 將整個檔案以單一未分隔字串的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="c0a54-219">To force `Get-Content` to return the entire file as a single, undelimited string.</span></span> <span data-ttu-id="c0a54-220">輸入不存在於檔案中的值。</span><span class="sxs-lookup"><span data-stu-id="c0a54-220">Enter a value that does not exist in the file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: End-of-line character
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0a54-221">-Wait</span><span class="sxs-lookup"><span data-stu-id="c0a54-221">-Wait</span></span>

<span data-ttu-id="c0a54-222">在所有現有的行都已輸出之後，將檔案保持開啟。</span><span class="sxs-lookup"><span data-stu-id="c0a54-222">Keeps the file open after all existing lines have been output.</span></span> <span data-ttu-id="c0a54-223">等候時， `Get-Content` 每秒會檢查檔案一次，並輸出新行（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="c0a54-223">While waiting, `Get-Content` checks the file once each second and outputs new lines if present.</span></span> <span data-ttu-id="c0a54-224">您可以按下 **CTRL + C** 來中斷 **等候** 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-224">You can interrupt **Wait** by pressing **CTRL+C** .</span></span> <span data-ttu-id="c0a54-225">如果檔案遭到刪除，則等候也會結束，在這種情況下，會報告非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0a54-225">Waiting also ends if the file gets deleted, in which case a non-terminating error is reported.</span></span>

<span data-ttu-id="c0a54-226">**Wait** 是動態參數，FileSystem 提供者會將它新增至 `Get-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0a54-226">**Wait** is a dynamic parameter that the FileSystem provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="c0a54-227">此參數只適用於檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="c0a54-227">This parameter works only in file system drives.</span></span> <span data-ttu-id="c0a54-228">**Wait** 無法結合 **Raw** 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-228">**Wait** cannot be combined with **Raw** .</span></span>

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

### <span data-ttu-id="c0a54-229">-Raw</span><span class="sxs-lookup"><span data-stu-id="c0a54-229">-Raw</span></span>

<span data-ttu-id="c0a54-230">忽略分行符號，並以一個字串傳回換行字元的整個檔案內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-230">Ignores newline characters and returns the entire contents of a file in one string with the newlines preserved.</span></span> <span data-ttu-id="c0a54-231">依預設，檔案中的分行符號會用來做為分隔符號，以將輸入區隔開至字串陣列。</span><span class="sxs-lookup"><span data-stu-id="c0a54-231">By default, newline characters in a file are used as delimiters to separate the input into an array of strings.</span></span> <span data-ttu-id="c0a54-232">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c0a54-232">This parameter was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="c0a54-233">**Raw** 是動態參數， **FileSystem** 提供者會將此參數新增至 `Get-Content` Cmdlet，此參數只適用于檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="c0a54-233">**Raw** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="c0a54-234">-Encoding</span><span class="sxs-lookup"><span data-stu-id="c0a54-234">-Encoding</span></span>

<span data-ttu-id="c0a54-235">指定目標檔案的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="c0a54-235">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="c0a54-236">預設值是 `utf8NoBOM`。</span><span class="sxs-lookup"><span data-stu-id="c0a54-236">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="c0a54-237">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="c0a54-237">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c0a54-238">`ascii`：使用 ASCII (7 位) 字元集的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c0a54-238">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="c0a54-239">`bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c0a54-239">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="c0a54-240">`oem`：針對 MS-DOS 和主控台程式使用預設編碼。</span><span class="sxs-lookup"><span data-stu-id="c0a54-240">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="c0a54-241">`unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c0a54-241">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="c0a54-242">`utf7`：以 UTF-7 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c0a54-242">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="c0a54-243">`utf8`：以 UTF-8 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c0a54-243">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="c0a54-244">`utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式</span><span class="sxs-lookup"><span data-stu-id="c0a54-244">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c0a54-245">`utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) </span><span class="sxs-lookup"><span data-stu-id="c0a54-245">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="c0a54-246">`utf32`：以 UTF-32 格式編碼。</span><span class="sxs-lookup"><span data-stu-id="c0a54-246">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="c0a54-247">Encoding 是動態參數， **FileSystem** 提供者會將它新增至 `Get-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0a54-247">Encoding is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="c0a54-248">此參數僅適用于檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="c0a54-248">This parameter is available only in file system drives.</span></span>

<span data-ttu-id="c0a54-249">讀取和寫入二進位檔案時，請使用 **AsByteStream** 參數，並針對 **ReadCount** 參數使用0的值。</span><span class="sxs-lookup"><span data-stu-id="c0a54-249">When reading from and writing to binary files, use the **AsByteStream** parameter and a value of 0 for the **ReadCount** parameter.</span></span> <span data-ttu-id="c0a54-250">**ReadCount** 值為0時，會以單一讀取操作讀取整個檔案。</span><span class="sxs-lookup"><span data-stu-id="c0a54-250">A **ReadCount** value of 0 reads the entire file in a single read operation.</span></span> <span data-ttu-id="c0a54-251">預設的 **ReadCount** 值1會在每個讀取操作中讀取一個位元組，並將每個位元組轉換為不同的物件，當您使用 `Set-Content` Cmdlet 將位元組寫入檔案時，除非您使用 **AsByteStream** 參數，否則會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0a54-251">The default **ReadCount** value, 1, reads one byte in each read operation and converts each byte into a separate object, which causes errors when you use the `Set-Content` cmdlet to write the bytes to a file unless you use **AsByteStream** parameter.</span></span>

<span data-ttu-id="c0a54-252">從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-252">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="c0a54-253">如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)。</span><span class="sxs-lookup"><span data-stu-id="c0a54-253">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0a54-254">-Stream</span><span class="sxs-lookup"><span data-stu-id="c0a54-254">-Stream</span></span>

<span data-ttu-id="c0a54-255">從檔案取得指定的替代 NTFS 檔案資料流內容。</span><span class="sxs-lookup"><span data-stu-id="c0a54-255">Gets the contents of the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="c0a54-256">輸入資料流名稱。</span><span class="sxs-lookup"><span data-stu-id="c0a54-256">Enter the stream name.</span></span>
<span data-ttu-id="c0a54-257">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c0a54-257">Wildcards are not supported.</span></span>

<span data-ttu-id="c0a54-258">**Stream** 是動態參數， **FileSystem** 提供者會將它新增至 `Get-Content` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0a54-258">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="c0a54-259">此參數只適用于 Windows 系統上的檔案系統磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="c0a54-259">This parameter works only in file system drives on Windows systems.</span></span> <span data-ttu-id="c0a54-260">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="c0a54-260">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c0a54-261">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="c0a54-261">-AsByteStream</span></span>

<span data-ttu-id="c0a54-262">指定應將內容讀取為位元組資料流程。</span><span class="sxs-lookup"><span data-stu-id="c0a54-262">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="c0a54-263">**AsByteStream** 參數是在 Windows PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="c0a54-263">The **AsByteStream** parameter was introduced in Windows PowerShell 6.0.</span></span>

<span data-ttu-id="c0a54-264">當您使用 **AsByteStream** 參數搭配 **編碼** 參數時，就會發生警告。</span><span class="sxs-lookup"><span data-stu-id="c0a54-264">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="c0a54-265">**AsByteStream** 參數會忽略任何編碼，並以位元組資料流程的形式傳回輸出。</span><span class="sxs-lookup"><span data-stu-id="c0a54-265">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="c0a54-266">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c0a54-266">CommonParameters</span></span>

<span data-ttu-id="c0a54-267">這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-267">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="c0a54-268">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="c0a54-268">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c0a54-269">輸入</span><span class="sxs-lookup"><span data-stu-id="c0a54-269">INPUTS</span></span>

### <span data-ttu-id="c0a54-270">System.Int64、System.String[]、System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="c0a54-270">System.Int64, System.String[], System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="c0a54-271">您可以透過管道將讀取計數、總數、路徑或認證傳送至 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="c0a54-271">You can pipe the read count, total count, paths, or credentials to `Get-Content`.</span></span>

## <span data-ttu-id="c0a54-272">輸出</span><span class="sxs-lookup"><span data-stu-id="c0a54-272">OUTPUTS</span></span>

### <span data-ttu-id="c0a54-273">System.Byte、System.String</span><span class="sxs-lookup"><span data-stu-id="c0a54-273">System.Byte, System.String</span></span>

<span data-ttu-id="c0a54-274">`Get-Content` 傳回字串或位元組。</span><span class="sxs-lookup"><span data-stu-id="c0a54-274">`Get-Content` returns strings or bytes.</span></span> <span data-ttu-id="c0a54-275">輸出類型取決於您指定做為輸入的內容類型。</span><span class="sxs-lookup"><span data-stu-id="c0a54-275">The output type depends upon the type of content that you specify as input.</span></span>

## <span data-ttu-id="c0a54-276">注意</span><span class="sxs-lookup"><span data-stu-id="c0a54-276">NOTES</span></span>

<span data-ttu-id="c0a54-277">此 `Get-Content` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。</span><span class="sxs-lookup"><span data-stu-id="c0a54-277">The `Get-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="c0a54-278">若要取得會話中的提供者，請使用 `Get-PSProvider` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c0a54-278">To get the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="c0a54-279">如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。</span><span class="sxs-lookup"><span data-stu-id="c0a54-279">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="c0a54-280">相關連結</span><span class="sxs-lookup"><span data-stu-id="c0a54-280">RELATED LINKS</span></span>

[<span data-ttu-id="c0a54-281">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="c0a54-281">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="c0a54-282">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c0a54-282">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="c0a54-283">Add-Content</span><span class="sxs-lookup"><span data-stu-id="c0a54-283">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="c0a54-284">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="c0a54-284">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="c0a54-285">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="c0a54-285">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="c0a54-286">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="c0a54-286">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="c0a54-287">Set-Content</span><span class="sxs-lookup"><span data-stu-id="c0a54-287">Set-Content</span></span>](Set-Content.md)
