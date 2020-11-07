---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/new-filecatalog?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-FileCatalog
ms.openlocfilehash: 23e74ae3e49d291b0ff6410c7d075a308b3d27e8
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343635"
---
# <span data-ttu-id="9defc-103">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="9defc-103">New-FileCatalog</span></span>

## <span data-ttu-id="9defc-104">概要</span><span class="sxs-lookup"><span data-stu-id="9defc-104">SYNOPSIS</span></span>
<span data-ttu-id="9defc-105">`New-FileCatalog` 建立檔案雜湊的類別目錄檔案，可用來驗證檔案的真實性。</span><span class="sxs-lookup"><span data-stu-id="9defc-105">`New-FileCatalog` creates a catalog file of file hashes that can be used to validate the authenticity of a file.</span></span>

## <span data-ttu-id="9defc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9defc-106">SYNTAX</span></span>

```
New-FileCatalog [-CatalogVersion <Int32>] [-CatalogFilePath] <String> [[-Path] <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="9defc-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9defc-107">DESCRIPTION</span></span>

<span data-ttu-id="9defc-108">`New-FileCatalog` 為一組資料夾和檔案建立 [Windows 類別目錄](/windows-hardware/drivers/install/catalog-files) 檔案。</span><span class="sxs-lookup"><span data-stu-id="9defc-108">`New-FileCatalog` creates a [Windows catalog file](/windows-hardware/drivers/install/catalog-files) for a set of folders and files.</span></span> <span data-ttu-id="9defc-109">此類別目錄檔案包含所提供路徑中所有檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="9defc-109">This catalog file contains hashes for all files in the provided paths.</span></span> <span data-ttu-id="9defc-110">然後，使用者可以使用其檔案來散發類別目錄，讓使用者可以在目錄建立時間之後，驗證是否已對資料夾進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="9defc-110">Users can then distribute the catalog with their files so that users can validate whether any changes have been made to the folders since catalog creation time.</span></span>

<span data-ttu-id="9defc-111">支援類別目錄第 1 版和第 2 版。</span><span class="sxs-lookup"><span data-stu-id="9defc-111">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="9defc-112">第1版使用 (已淘汰的) SHA1 雜湊演算法來建立檔案雜湊，第2版使用 SHA256。</span><span class="sxs-lookup"><span data-stu-id="9defc-112">Version 1 uses the (deprecated) SHA1 hashing algorithm to create file hashes, and version 2 uses SHA256.</span></span> <span data-ttu-id="9defc-113">Windows Server 2008 R2 或 Windows 7 不支援第 2 版的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="9defc-113">Catalog version 2 is not supported on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="9defc-114">Windows 8、Windows Server 2012 和更新版本的作業系統，應該使用類別目錄第 2 版。</span><span class="sxs-lookup"><span data-stu-id="9defc-114">You should use catalog version 2 on Windows 8, Windows Server 2012, and later operating systems.</span></span>

## <span data-ttu-id="9defc-115">範例</span><span class="sxs-lookup"><span data-stu-id="9defc-115">EXAMPLES</span></span>

### <span data-ttu-id="9defc-116">範例1：建立的檔案類別目錄 `Microsoft.PowerShell.Utility`</span><span class="sxs-lookup"><span data-stu-id="9defc-116">Example 1: Create a file catalog for `Microsoft.PowerShell.Utility`</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         11/2/2018 11:58 AM            950 Microsoft.PowerShell.Utility.cat
```

## <span data-ttu-id="9defc-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9defc-117">PARAMETERS</span></span>

### <span data-ttu-id="9defc-118">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="9defc-118">-CatalogFilePath</span></span>

<span data-ttu-id="9defc-119">應放置目錄檔案 ( .cat) 的檔案或資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="9defc-119">A path to a file or folder where the catalog file (.cat) should be placed.</span></span> <span data-ttu-id="9defc-120">如果指定了資料夾路徑，則會使用預設的檔案名 `catalog.cat` 。</span><span class="sxs-lookup"><span data-stu-id="9defc-120">If a folder path is specified, the default filename `catalog.cat` will be used.</span></span>

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

### <span data-ttu-id="9defc-121">-CatalogVersion</span><span class="sxs-lookup"><span data-stu-id="9defc-121">-CatalogVersion</span></span>

<span data-ttu-id="9defc-122">接受 `1.0` 或 `2.0` 指定類別目錄版本的可能值。</span><span class="sxs-lookup"><span data-stu-id="9defc-122">Accepts `1.0` or `2.0` as possible values for specifying the catalog version.</span></span> <span data-ttu-id="9defc-123">`1.0` 應該盡可能避免使用，因為它使用不安全的 SHA-1 雜湊演算法，而使用256安全的 sha-1 雜湊演算法時， `2.0` `1.0` 是 Windows 7 和伺服器2008R2 上唯一支援的演算法。</span><span class="sxs-lookup"><span data-stu-id="9defc-123">`1.0` should be used avoided whenever possible, as it uses the insecure SHA-1 hash algorithm, while `2.0` uses the secure SHA-256 algorithm However, `1.0` is the only supported algorithm on Windows 7 and Server 2008R2.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9defc-124">-Path</span><span class="sxs-lookup"><span data-stu-id="9defc-124">-Path</span></span>

<span data-ttu-id="9defc-125">接受目錄檔案中應包含的檔案或資料夾路徑或路徑陣列。</span><span class="sxs-lookup"><span data-stu-id="9defc-125">Accepts a path or array of paths to files or folders that should be included in the catalog file.</span></span> <span data-ttu-id="9defc-126">如果指定資料夾，也會包含資料夾中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="9defc-126">If a folder is specified, all the files in the folder will be included as well.</span></span>

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

### <span data-ttu-id="9defc-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9defc-127">-Confirm</span></span>

<span data-ttu-id="9defc-128">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="9defc-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9defc-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9defc-129">-WhatIf</span></span>

<span data-ttu-id="9defc-130">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="9defc-130">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9defc-131">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="9defc-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9defc-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9defc-132">CommonParameters</span></span>

<span data-ttu-id="9defc-133">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9defc-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9defc-134">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9defc-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9defc-135">輸入</span><span class="sxs-lookup"><span data-stu-id="9defc-135">INPUTS</span></span>

### <span data-ttu-id="9defc-136">System.String</span><span class="sxs-lookup"><span data-stu-id="9defc-136">System.String</span></span>

<span data-ttu-id="9defc-137">管線會使用做為目錄檔案名的字串。</span><span class="sxs-lookup"><span data-stu-id="9defc-137">The pipeline takes a string that is used as the catalog filename.</span></span>

## <span data-ttu-id="9defc-138">輸出</span><span class="sxs-lookup"><span data-stu-id="9defc-138">OUTPUTS</span></span>

### <span data-ttu-id="9defc-139">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="9defc-139">System.IO.FileInfo</span></span>

## <span data-ttu-id="9defc-140">注意</span><span class="sxs-lookup"><span data-stu-id="9defc-140">NOTES</span></span>

<span data-ttu-id="9defc-141">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="9defc-141">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="9defc-142">相關連結</span><span class="sxs-lookup"><span data-stu-id="9defc-142">RELATED LINKS</span></span>

[<span data-ttu-id="9defc-143">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="9defc-143">Test-FileCatalog</span></span>](Test-FileCatalog.md)

[<span data-ttu-id="9defc-144">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="9defc-144">PowerShellGet</span></span>](/powerShell/module/powershellget)
