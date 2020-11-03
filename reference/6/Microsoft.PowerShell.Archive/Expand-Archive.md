---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: 3775cea92ee32a54921bd9441de2c3e0f5915d1d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "93205315"
---
# <span data-ttu-id="4adff-103">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="4adff-103">Expand-Archive</span></span>

## <span data-ttu-id="4adff-104">概要</span><span class="sxs-lookup"><span data-stu-id="4adff-104">SYNOPSIS</span></span>
<span data-ttu-id="4adff-105">從指定的封存 (壓縮) 檔案中解壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="4adff-105">Extracts files from a specified archive (zipped) file.</span></span>

## <span data-ttu-id="4adff-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4adff-106">SYNTAX</span></span>

### <span data-ttu-id="4adff-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="4adff-107">Path (Default)</span></span>

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4adff-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4adff-108">LiteralPath</span></span>

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4adff-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4adff-109">DESCRIPTION</span></span>

<span data-ttu-id="4adff-110">Cmdlet 會將 `Expand-Archive` 指定之壓縮封存檔案中的檔案解壓縮到指定的目的地資料夾。</span><span class="sxs-lookup"><span data-stu-id="4adff-110">The `Expand-Archive` cmdlet extracts files from a specified zipped archive file to a specified destination folder.</span></span> <span data-ttu-id="4adff-111">封存檔案可讓多個檔案封裝並選擇性地壓縮成單一壓縮檔案，以方便散發和儲存。</span><span class="sxs-lookup"><span data-stu-id="4adff-111">An archive file allows multiple files to be packaged, and optionally compressed, into a single zipped file for easier distribution and storage.</span></span>

## <span data-ttu-id="4adff-112">範例</span><span class="sxs-lookup"><span data-stu-id="4adff-112">EXAMPLES</span></span>

### <span data-ttu-id="4adff-113">範例1：將封存的內容解壓縮</span><span class="sxs-lookup"><span data-stu-id="4adff-113">Example 1: Extract the contents of an archive</span></span>

<span data-ttu-id="4adff-114">此範例會將現有封存檔案的內容解壓縮到 **DestinationPath** 參數所指定的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4adff-114">This example extracts the contents of an existing archive file into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

<span data-ttu-id="4adff-115">在此範例中，會使用 **LiteralPath** 參數，因為檔案名包含可解釋為萬用字元的字元。</span><span class="sxs-lookup"><span data-stu-id="4adff-115">In this example, the **LiteralPath** parameter is used because the filename contains characters that could be interpreted as wildcards.</span></span>

### <span data-ttu-id="4adff-116">範例2：將封存的內容解壓縮到目前的資料夾中</span><span class="sxs-lookup"><span data-stu-id="4adff-116">Example 2: Extract the contents of an archive in the current folder</span></span>

<span data-ttu-id="4adff-117">此範例會將目前資料夾中現有封存檔案的內容，解壓縮到 **DestinationPath** 參數所指定的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4adff-117">This example extracts the contents of an existing archive file in the current folder into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## <span data-ttu-id="4adff-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4adff-118">PARAMETERS</span></span>

### <span data-ttu-id="4adff-119">-DestinationPath</span><span class="sxs-lookup"><span data-stu-id="4adff-119">-DestinationPath</span></span>

<span data-ttu-id="4adff-120">依預設， `Expand-Archive` 會在目前的位置中建立一個與 ZIP 檔案相同名稱的資料夾。</span><span class="sxs-lookup"><span data-stu-id="4adff-120">By default, `Expand-Archive` creates a folder in the current location that is the same name as the ZIP file.</span></span> <span data-ttu-id="4adff-121">參數可讓您指定不同資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="4adff-121">The parameter allows you to specify the path to a different folder.</span></span> <span data-ttu-id="4adff-122">如果目的檔案夾不存在，則會加以建立。</span><span class="sxs-lookup"><span data-stu-id="4adff-122">The target folder is created if it does not exist.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: A folder in the current location
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4adff-123">-Force</span><span class="sxs-lookup"><span data-stu-id="4adff-123">-Force</span></span>

<span data-ttu-id="4adff-124">強制執行命令而不要求使用者確認。</span><span class="sxs-lookup"><span data-stu-id="4adff-124">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="4adff-125">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4adff-125">-LiteralPath</span></span>

<span data-ttu-id="4adff-126">指定封存檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4adff-126">Specifies the path to an archive file.</span></span> <span data-ttu-id="4adff-127">與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="4adff-127">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="4adff-128">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4adff-128">Wildcard characters are not supported.</span></span> <span data-ttu-id="4adff-129">如果路徑包含 escape 字元，請用單引號括住每個 escape 字元，以指示 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="4adff-129">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4adff-130">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4adff-130">-PassThru</span></span>

<span data-ttu-id="4adff-131">讓 Cmdlet 輸出從封存中展開的檔案清單。</span><span class="sxs-lookup"><span data-stu-id="4adff-131">Causes the cmdlet to output a list of the files expanded from the archive.</span></span>

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

### <span data-ttu-id="4adff-132">-Path</span><span class="sxs-lookup"><span data-stu-id="4adff-132">-Path</span></span>

<span data-ttu-id="4adff-133">指定封存檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4adff-133">Specifies the path to the archive file.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4adff-134">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4adff-134">-Confirm</span></span>

<span data-ttu-id="4adff-135">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="4adff-135">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4adff-136">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4adff-136">-WhatIf</span></span>

<span data-ttu-id="4adff-137">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="4adff-137">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4adff-138">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="4adff-138">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4adff-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4adff-139">CommonParameters</span></span>
<span data-ttu-id="4adff-140">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4adff-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4adff-141">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4adff-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4adff-142">輸入</span><span class="sxs-lookup"><span data-stu-id="4adff-142">INPUTS</span></span>

### <span data-ttu-id="4adff-143">System.String</span><span class="sxs-lookup"><span data-stu-id="4adff-143">System.String</span></span>

<span data-ttu-id="4adff-144">您可以使用管線將包含路徑的字串傳送至現有的保存檔案。</span><span class="sxs-lookup"><span data-stu-id="4adff-144">You can pipe a string that contains a path to an existing archive file.</span></span>

## <span data-ttu-id="4adff-145">輸出</span><span class="sxs-lookup"><span data-stu-id="4adff-145">OUTPUTS</span></span>

### <span data-ttu-id="4adff-146">FileSystemInfo</span><span class="sxs-lookup"><span data-stu-id="4adff-146">System.IO.FileSystemInfo</span></span>

<span data-ttu-id="4adff-147">`-PassThru`使用參數時，此 Cmdlet 會輸出從封存擴充的檔案清單。</span><span class="sxs-lookup"><span data-stu-id="4adff-147">When the `-PassThru` parameter is used, the cmdlet outputs a list of files that were expanded from the archive.</span></span>

## <span data-ttu-id="4adff-148">注意</span><span class="sxs-lookup"><span data-stu-id="4adff-148">NOTES</span></span>

<span data-ttu-id="4adff-149">[ZIP 檔案規格](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)不會指定編碼包含非 ASCII 字元之檔案名的標準方式。</span><span class="sxs-lookup"><span data-stu-id="4adff-149">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="4adff-150">此 `Compress-Archive` Cmdlet 會使用 utf-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="4adff-150">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="4adff-151">其他 ZIP 封存工具可能會使用不同的編碼配置。</span><span class="sxs-lookup"><span data-stu-id="4adff-151">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="4adff-152">使用 UTF-8 編碼方式解壓縮未儲存的檔案時，會使用在封存 `Expand-Archive` 中找到的原始值。</span><span class="sxs-lookup"><span data-stu-id="4adff-152">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="4adff-153">這可能會產生與儲存在封存中的來原始檔案名不同的檔案名。</span><span class="sxs-lookup"><span data-stu-id="4adff-153">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="4adff-154">相關連結</span><span class="sxs-lookup"><span data-stu-id="4adff-154">RELATED LINKS</span></span>

[<span data-ttu-id="4adff-155">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="4adff-155">Compress-Archive</span></span>](compress-archive.md)
