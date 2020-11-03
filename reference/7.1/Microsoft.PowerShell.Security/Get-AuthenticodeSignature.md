---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: fa3ea8f965ea8089defa5fde7b88b18f00cd83bc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205048"
---
# <span data-ttu-id="7e5cb-103">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="7e5cb-103">Get-AuthenticodeSignature</span></span>

## <span data-ttu-id="7e5cb-104">概要</span><span class="sxs-lookup"><span data-stu-id="7e5cb-104">SYNOPSIS</span></span>
<span data-ttu-id="7e5cb-105">取得檔案的 Authenticode 簽章的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-105">Gets information about the Authenticode signature for a file.</span></span>

## <span data-ttu-id="7e5cb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7e5cb-106">SYNTAX</span></span>

### <span data-ttu-id="7e5cb-107">ByPath (預設值)</span><span class="sxs-lookup"><span data-stu-id="7e5cb-107">ByPath (Default)</span></span>

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="7e5cb-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="7e5cb-108">ByLiteralPath</span></span>

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### <span data-ttu-id="7e5cb-109">ByContent</span><span class="sxs-lookup"><span data-stu-id="7e5cb-109">ByContent</span></span>

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## <span data-ttu-id="7e5cb-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7e5cb-110">DESCRIPTION</span></span>

<span data-ttu-id="7e5cb-111">`Get-AuthenticodeSignature`Cmdlet 會取得檔案或檔案內容的 Authenticode 簽章相關資訊做為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-111">The `Get-AuthenticodeSignature` cmdlet gets information about the Authenticode signature for a file or file content as a byte array.</span></span> <span data-ttu-id="7e5cb-112">如果檔案未簽署，會抓取資訊但欄位是空白的。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-112">If the file is not signed, the information is retrieved, but the fields are blank.</span></span>

## <span data-ttu-id="7e5cb-113">範例</span><span class="sxs-lookup"><span data-stu-id="7e5cb-113">EXAMPLES</span></span>

### <span data-ttu-id="7e5cb-114">範例1：取得檔案的 Authenticode 簽章</span><span class="sxs-lookup"><span data-stu-id="7e5cb-114">Example 1: Get the Authenticode signature for a file</span></span>

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

<span data-ttu-id="7e5cb-115">此命令會取得 NewScript.ps1 檔案中 Authenticode 簽章的相關詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-115">This command gets information about the Authenticode signature in the NewScript.ps1 file.</span></span> <span data-ttu-id="7e5cb-116">它會使用 **FilePath** 參數來指定檔案。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-116">It uses the **FilePath** parameter to specify the file.</span></span>

### <span data-ttu-id="7e5cb-117">範例2：取得多個檔案的 Authenticode 簽章</span><span class="sxs-lookup"><span data-stu-id="7e5cb-117">Example 2: Get the Authenticode signature for multiple files</span></span>

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

<span data-ttu-id="7e5cb-118">此命令會取得命令列中列出之四個檔案的 Authenticode 簽章的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-118">This command gets information about the Authenticode signature for the four files listed at the command line.</span></span> <span data-ttu-id="7e5cb-119">在此範例中，會省略 **FilePath** 參數的名稱（這是選擇性的）。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-119">In this example, the name of the **FilePath** parameter, which is optional, is omitted.</span></span>

### <span data-ttu-id="7e5cb-120">範例3：只針對多個檔案取得有效的 Authenticode 簽章</span><span class="sxs-lookup"><span data-stu-id="7e5cb-120">Example 3: Get only valid Authenticode signatures for multiple files</span></span>

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

<span data-ttu-id="7e5cb-121">此命令 `$PSHOME` 會列出目錄中具有有效 Authenticode 簽章的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-121">This command lists all of the files in the `$PSHOME` directory that have a valid Authenticode signature.</span></span> <span data-ttu-id="7e5cb-122">`$PSHOME`自動變數包含 PowerShell 安裝目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-122">The `$PSHOME` automatic variable contains the path to the PowerShell installation directory.</span></span>

<span data-ttu-id="7e5cb-123">此命令會使用 `Get-ChildItem` Cmdlet 來取得目錄中的檔案 `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-123">The command uses the `Get-ChildItem` cmdlet to get the files in the `$PSHOME` directory.</span></span> <span data-ttu-id="7e5cb-124">它會使用的模式 *。*</span><span class="sxs-lookup"><span data-stu-id="7e5cb-124">It uses a pattern of *.*</span></span> <span data-ttu-id="7e5cb-125">若要排除目錄 (，雖然它也會排除檔案名) 中沒有句點的檔案。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-125">to exclude directories (although it also excludes files without a dot in the filename).</span></span>

<span data-ttu-id="7e5cb-126">此命令會使用管線運算子 (`|`) 將檔案傳送 `$PSHOME` 至 `ForEach-Object` Cmdlet，其中 `Get-AuthenticodeSignature` 會針對每個檔案呼叫。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-126">The command uses a pipeline operator (`|`) to send the files in `$PSHOME` to the `ForEach-Object` cmdlet, where `Get-AuthenticodeSignature` is called for each file.</span></span>

<span data-ttu-id="7e5cb-127">命令的結果 `Get-AuthenticodeSignature` 會傳送至 `Where-Object` 只選取狀態為有效之簽章物件的命令。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-127">The results of the `Get-AuthenticodeSignature` command are sent to a `Where-Object` command that selects only the signature objects with a status of Valid.</span></span>

### <span data-ttu-id="7e5cb-128">範例4：取得指定為位元組陣列的檔案內容的 Authenticode 簽章</span><span class="sxs-lookup"><span data-stu-id="7e5cb-128">Example 4: Get the Authenticode signature for a file content specified as byte array</span></span>

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

<span data-ttu-id="7e5cb-129">此命令會取得檔案內容之 Authenticode 簽章的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-129">This command gets information about the Authenticode signature for the content of a file.</span></span> <span data-ttu-id="7e5cb-130">在此範例中，會指定副檔名以及檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-130">In this example, the file extension is specified along with the content of the file.</span></span>

## <span data-ttu-id="7e5cb-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7e5cb-131">PARAMETERS</span></span>

### <span data-ttu-id="7e5cb-132">-Content</span><span class="sxs-lookup"><span data-stu-id="7e5cb-132">-Content</span></span>

<span data-ttu-id="7e5cb-133">檔案的內容，作為要抓取 Authenticode 簽章的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-133">Contents of a file as a byte array for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="7e5cb-134">此參數必須搭配 **SourcePathOrExtension** 參數使用。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-134">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="7e5cb-135">檔案內容的格式必須是 Unicode (UTF-16LE) 格式。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-135">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7e5cb-136">-FilePath</span><span class="sxs-lookup"><span data-stu-id="7e5cb-136">-FilePath</span></span>

<span data-ttu-id="7e5cb-137">指定要檢查之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-137">Specifies the path to the file to examine.</span></span> <span data-ttu-id="7e5cb-138">允許使用萬用字元，但它們必須指向單一檔案。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-138">Wildcards are permitted, but they must lead to a single file.</span></span> <span data-ttu-id="7e5cb-139">當您指定此參數的值時，不需要在命令列輸入 **FilePath** 。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-139">It is not necessary to type **FilePath** at the command line when you specify a value for this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="7e5cb-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7e5cb-140">-LiteralPath</span></span>

<span data-ttu-id="7e5cb-141">指定要檢查之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-141">Specifies the path to the file being examined.</span></span> <span data-ttu-id="7e5cb-142">**LiteralPath** 參數值與 **FilePath** 不同，會完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-142">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="7e5cb-143">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="7e5cb-144">如果路徑包含 escape 字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-144">If the path includes an escape character, enclose it in single quotation marks.</span></span> <span data-ttu-id="7e5cb-145">單引號可告知 PowerShell 不要將任何字元解釋為 escape 字元。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-145">Single quotation marks tell PowerShell not to interpret any characters as escape characters.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7e5cb-146">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="7e5cb-146">-SourcePathOrExtension</span></span>

<span data-ttu-id="7e5cb-147">要抓取 Authenticode 簽章之內容的檔案或檔案類型路徑。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-147">Path to the file or file type of the content for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="7e5cb-148">此參數會搭配將檔案內容當做位元組陣列傳遞的 **內容** 使用。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-148">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7e5cb-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e5cb-149">CommonParameters</span></span>

<span data-ttu-id="7e5cb-150">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7e5cb-151">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-151">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7e5cb-152">輸入</span><span class="sxs-lookup"><span data-stu-id="7e5cb-152">INPUTS</span></span>

### <span data-ttu-id="7e5cb-153">System.String</span><span class="sxs-lookup"><span data-stu-id="7e5cb-153">System.String</span></span>

<span data-ttu-id="7e5cb-154">您可以使用管線將包含檔案路徑的字串傳送至 `Get-AuthenticodeSignature` 。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-154">You can pipe a string that contains a file path to `Get-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="7e5cb-155">輸出</span><span class="sxs-lookup"><span data-stu-id="7e5cb-155">OUTPUTS</span></span>

### <span data-ttu-id="7e5cb-156">System.Management.Automation.Signature</span><span class="sxs-lookup"><span data-stu-id="7e5cb-156">System.Management.Automation.Signature</span></span>

<span data-ttu-id="7e5cb-157">`Get-AuthenticodeSignature` 傳回其取得之每個簽章的簽章物件。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-157">`Get-AuthenticodeSignature` returns a signature object for each signature that it gets.</span></span>

## <span data-ttu-id="7e5cb-158">注意</span><span class="sxs-lookup"><span data-stu-id="7e5cb-158">NOTES</span></span>

<span data-ttu-id="7e5cb-159">如需 PowerShell 中 Authenticode 簽章的相關資訊，請參閱 [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)。</span><span class="sxs-lookup"><span data-stu-id="7e5cb-159">For information about Authenticode signatures in PowerShell, see [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).</span></span>

## <span data-ttu-id="7e5cb-160">相關連結</span><span class="sxs-lookup"><span data-stu-id="7e5cb-160">RELATED LINKS</span></span>

[<span data-ttu-id="7e5cb-161">Get-executionpolicy</span><span class="sxs-lookup"><span data-stu-id="7e5cb-161">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="7e5cb-162">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="7e5cb-162">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="7e5cb-163">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="7e5cb-163">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="7e5cb-164">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="7e5cb-164">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="7e5cb-165">about_Signing</span><span class="sxs-lookup"><span data-stu-id="7e5cb-165">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)

