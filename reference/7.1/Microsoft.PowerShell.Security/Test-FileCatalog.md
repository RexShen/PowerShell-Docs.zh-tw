---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: 4ea34f547e296567fc0ad728d9279392615836d3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346389"
---
# <span data-ttu-id="43036-103">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="43036-103">Test-FileCatalog</span></span>

## <span data-ttu-id="43036-104">概要</span><span class="sxs-lookup"><span data-stu-id="43036-104">SYNOPSIS</span></span>
<span data-ttu-id="43036-105">`Test-FileCatalog` 驗證目錄檔案中包含的雜湊 ( .cat) 是否符合實際檔案的雜湊，以便驗證其真實性。</span><span class="sxs-lookup"><span data-stu-id="43036-105">`Test-FileCatalog` validates whether the hashes contained in a catalog file (.cat) matches the hashes of the actual files in order to validate their authenticity.</span></span>

<span data-ttu-id="43036-106">只有在 Windows 上才支援此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43036-106">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="43036-107">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="43036-107">SYNTAX</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="43036-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="43036-108">DESCRIPTION</span></span>

<span data-ttu-id="43036-109">`Test-FileCatalog` 藉由比較類別目錄檔案 ( 的檔案雜湊來驗證檔案的真實性，並將實際檔案的雜湊與磁片上的實際檔案雜湊) 。</span><span class="sxs-lookup"><span data-stu-id="43036-109">`Test-FileCatalog` validates the authenticity of files by comparing the file hashes of a catalog file (.cat) with the hashes of actual files on disk.</span></span> <span data-ttu-id="43036-110">如果偵測到任何不符的狀況，則會以 >validationfailed 的形式傳回狀態。</span><span class="sxs-lookup"><span data-stu-id="43036-110">If it detects any mismatches, it returns the status as ValidationFailed.</span></span> <span data-ttu-id="43036-111">使用者可以使用 -Detailed 參數來擷取此資訊的完整內容。</span><span class="sxs-lookup"><span data-stu-id="43036-111">Users can retrieve all this information by using the -Detailed parameter.</span></span> <span data-ttu-id="43036-112">它也會在 [簽章] 屬性中顯示目錄的簽章狀態，這相當於 `Get-AuthenticodeSignature` 在類別目錄檔案上呼叫 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43036-112">It also displays signing status of catalog in Signature property which is equivalent to calling `Get-AuthenticodeSignature` cmdlet on the catalog file.</span></span> <span data-ttu-id="43036-113">使用者也可以使用 -FilesToSkip 參數，在驗證期間略過任何檔案。</span><span class="sxs-lookup"><span data-stu-id="43036-113">Users can also skip any file during validation by using the -FilesToSkip parameter.</span></span>

<span data-ttu-id="43036-114">只有在 Windows 上才支援此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43036-114">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="43036-115">範例</span><span class="sxs-lookup"><span data-stu-id="43036-115">EXAMPLES</span></span>

### <span data-ttu-id="43036-116">範例1：建立和驗證檔案類別目錄</span><span class="sxs-lookup"><span data-stu-id="43036-116">Example 1: Create and validate a file catalog</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### <span data-ttu-id="43036-117">範例2：使用詳細輸出驗證檔案類別目錄</span><span class="sxs-lookup"><span data-stu-id="43036-117">Example 2: Validate a file catalog with detailed output</span></span>

```powershell
Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Status        : Valid
HashAlgorithm : SHA256
CatalogItems  : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
PathItems     : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
Signature     : System.Management.Automation.Signature
```

## <span data-ttu-id="43036-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43036-118">PARAMETERS</span></span>

### <span data-ttu-id="43036-119">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="43036-119">-CatalogFilePath</span></span>

<span data-ttu-id="43036-120">類別目錄檔案的路徑 ( .cat) ，其中包含要用於驗證的雜湊。</span><span class="sxs-lookup"><span data-stu-id="43036-120">A path to a catalog file (.cat) that contains the hashes to be used for validation.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="43036-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="43036-121">-Confirm</span></span>

<span data-ttu-id="43036-122">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="43036-122">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="43036-123">-Detailed</span><span class="sxs-lookup"><span data-stu-id="43036-123">-Detailed</span></span>

<span data-ttu-id="43036-124">傳回更詳細的資訊， `CatalogInformation` 其中包含所測試的檔案、其預期/實際的雜湊，以及類別目錄檔案的 Authenticode 簽章（如果已簽署的話）。</span><span class="sxs-lookup"><span data-stu-id="43036-124">Returns more information a more detailed `CatalogInformation` object that contains the files tested, their expected/actual hashes, and an Authenticode signature of the catalog file if it's signed.</span></span>

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

### <span data-ttu-id="43036-125">->-filestoskip</span><span class="sxs-lookup"><span data-stu-id="43036-125">-FilesToSkip</span></span>

<span data-ttu-id="43036-126">不應在驗證過程中測試的路徑陣列。</span><span class="sxs-lookup"><span data-stu-id="43036-126">An array of paths that should not be tested as part of the validation.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43036-127">-Path</span><span class="sxs-lookup"><span data-stu-id="43036-127">-Path</span></span>

<span data-ttu-id="43036-128">應針對類別目錄檔案進行驗證的資料夾或檔案陣列。</span><span class="sxs-lookup"><span data-stu-id="43036-128">A folder or array of files that should be validated against the catalog file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="43036-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="43036-129">-WhatIf</span></span>

<span data-ttu-id="43036-130">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="43036-130">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="43036-131">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="43036-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="43036-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43036-132">CommonParameters</span></span>

<span data-ttu-id="43036-133">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="43036-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43036-134">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="43036-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="43036-135">輸入</span><span class="sxs-lookup"><span data-stu-id="43036-135">INPUTS</span></span>

### <span data-ttu-id="43036-136">DirectoryInfo []、System.string []</span><span class="sxs-lookup"><span data-stu-id="43036-136">System.IO.DirectoryInfo[], System.String[]</span></span>

<span data-ttu-id="43036-137">管線接受字串或物件的陣列 `DirectoryInfo` ，這些字串或物件代表需要驗證之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="43036-137">The pipeline accepts an array of strings or `DirectoryInfo` objects that represent paths to the files that need to be validated.</span></span>

## <span data-ttu-id="43036-138">輸出</span><span class="sxs-lookup"><span data-stu-id="43036-138">OUTPUTS</span></span>

### <span data-ttu-id="43036-139">CatalogValidationStatus。</span><span class="sxs-lookup"><span data-stu-id="43036-139">System.Management.Automation.CatalogValidationStatus</span></span>

<span data-ttu-id="43036-140">預設傳回型別，其中包含或的 `Valid` 值 `ValidationFailed` 。</span><span class="sxs-lookup"><span data-stu-id="43036-140">The default return type containing a value of either `Valid` or `ValidationFailed`.</span></span>

### <span data-ttu-id="43036-141">CatalogInformation。</span><span class="sxs-lookup"><span data-stu-id="43036-141">System.Management.Automation.CatalogInformation</span></span>

<span data-ttu-id="43036-142">當使用時，會傳回更詳細的物件 `-Detailed` ，可用於分析可能或可能尚未通過驗證的特定檔案、預期的雜湊與找到的雜湊，以及用於目錄中的演算法。</span><span class="sxs-lookup"><span data-stu-id="43036-142">A more detailed object returned when using `-Detailed` which can be used to analyze specific files that may or may not have passed validation, which hashes were expected vs. found, and the algorithm used in the catalog.</span></span>

## <span data-ttu-id="43036-143">注意</span><span class="sxs-lookup"><span data-stu-id="43036-143">NOTES</span></span>

<span data-ttu-id="43036-144">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="43036-144">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="43036-145">相關連結</span><span class="sxs-lookup"><span data-stu-id="43036-145">RELATED LINKS</span></span>

[<span data-ttu-id="43036-146">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="43036-146">New-FileCatalog</span></span>](New-FileCatalog.md)

[<span data-ttu-id="43036-147">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="43036-147">PowerShellGet</span></span>](/powershell/module/PowerShellGet)
