---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/new-filecatalog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-FileCatalog
ms.openlocfilehash: 139ebf10cd0097d55eac521cd81016f8f168d2bd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203396"
---
# <span data-ttu-id="05ba4-103">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="05ba4-103">New-FileCatalog</span></span>

## <span data-ttu-id="05ba4-104">概要</span><span class="sxs-lookup"><span data-stu-id="05ba4-104">SYNOPSIS</span></span>

<span data-ttu-id="05ba4-105">`New-FileCatalog` 建立檔案雜湊的類別目錄檔案，可用來驗證檔案的真實性。</span><span class="sxs-lookup"><span data-stu-id="05ba4-105">`New-FileCatalog` creates a catalog file of file hashes that can be used to validate the authenticity of a file.</span></span>

## <span data-ttu-id="05ba4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="05ba4-106">SYNTAX</span></span>

```
New-FileCatalog [-CatalogVersion <Int32>] [-CatalogFilePath] <String> [[-Path] <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="05ba4-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="05ba4-107">DESCRIPTION</span></span>

<span data-ttu-id="05ba4-108">`New-FileCatalog` 為一組資料夾和檔案建立 [Windows 類別目錄](/windows-hardware/drivers/install/catalog-files) 檔案。</span><span class="sxs-lookup"><span data-stu-id="05ba4-108">`New-FileCatalog` creates a [Windows catalog file](/windows-hardware/drivers/install/catalog-files) for a set of folders and files.</span></span>
<span data-ttu-id="05ba4-109">此類別目錄檔案包含所提供路徑中所有檔案的雜湊。</span><span class="sxs-lookup"><span data-stu-id="05ba4-109">This catalog file contains hashes for all files in the provided paths.</span></span>
<span data-ttu-id="05ba4-110">然後，使用者可以使用其檔案來散發類別目錄，讓使用者可以在目錄建立時間之後，驗證是否已對資料夾進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="05ba4-110">Users can then distribute the catalog with their files so that users can validate whether any changes have been made to the folders since catalog creation time.</span></span>

<span data-ttu-id="05ba4-111">支援類別目錄第 1 版和第 2 版。</span><span class="sxs-lookup"><span data-stu-id="05ba4-111">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="05ba4-112">第1版使用 (已淘汰的) SHA1 雜湊演算法來建立檔案雜湊，第2版使用 SHA256。</span><span class="sxs-lookup"><span data-stu-id="05ba4-112">Version 1 uses the (deprecated) SHA1 hashing algorithm to create file hashes, and version 2 uses SHA256.</span></span>
<span data-ttu-id="05ba4-113">Windows Server 2008 R2 或 Windows 7 不支援第 2 版的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="05ba4-113">Catalog version 2 is not supported on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="05ba4-114">Windows 8、Windows Server 2012 和更新版本的作業系統，應該使用類別目錄第 2 版。</span><span class="sxs-lookup"><span data-stu-id="05ba4-114">You should use catalog version 2 on Windows 8, Windows Server 2012, and later operating systems.</span></span>

## <span data-ttu-id="05ba4-115">範例</span><span class="sxs-lookup"><span data-stu-id="05ba4-115">EXAMPLES</span></span>

### <span data-ttu-id="05ba4-116">範例1：建立的檔案類別目錄 `Microsoft.PowerShell.Utility`</span><span class="sxs-lookup"><span data-stu-id="05ba4-116">Example 1: Create a file catalog for `Microsoft.PowerShell.Utility`</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         11/2/2018 11:58 AM            950 Microsoft.PowerShell.Utility.cat
```

## <span data-ttu-id="05ba4-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="05ba4-117">PARAMETERS</span></span>

### <span data-ttu-id="05ba4-118">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="05ba4-118">-CatalogFilePath</span></span>

<span data-ttu-id="05ba4-119">應放置目錄檔案 ( .cat) 的檔案或資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="05ba4-119">A path to a file or folder where the catalog file (.cat) should be placed.</span></span>
<span data-ttu-id="05ba4-120">如果指定了資料夾路徑，則會使用預設的檔案名 `catalog.cat` 。</span><span class="sxs-lookup"><span data-stu-id="05ba4-120">If a folder path is specified, the default filename `catalog.cat` will be used.</span></span>

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

### <span data-ttu-id="05ba4-121">-CatalogVersion</span><span class="sxs-lookup"><span data-stu-id="05ba4-121">-CatalogVersion</span></span>

<span data-ttu-id="05ba4-122">接受 `1.0` 或 `2.0` 指定類別目錄版本的可能值。</span><span class="sxs-lookup"><span data-stu-id="05ba4-122">Accepts `1.0` or `2.0` as possible values for specifying the catalog version.</span></span>
<span data-ttu-id="05ba4-123">`1.0` 應該盡可能避免使用，因為它使用不安全的 SHA-1 雜湊演算法，而使用256安全的 sha-1 雜湊演算法時， `2.0` `1.0` 是 Windows 7 和伺服器2008R2 上唯一支援的演算法。</span><span class="sxs-lookup"><span data-stu-id="05ba4-123">`1.0` should be used avoided whenever possible, as it uses the insecure SHA-1 hash algorithm, while `2.0` uses the secure SHA-256 algorithm However, `1.0` is the only supported algorithm on Windows 7 and Server 2008R2.</span></span>

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

### <span data-ttu-id="05ba4-124">-Path</span><span class="sxs-lookup"><span data-stu-id="05ba4-124">-Path</span></span>

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

### <span data-ttu-id="05ba4-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="05ba4-125">-Confirm</span></span>

<span data-ttu-id="05ba4-126">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="05ba4-126">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="05ba4-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="05ba4-127">-WhatIf</span></span>

<span data-ttu-id="05ba4-128">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="05ba4-128">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="05ba4-129">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="05ba4-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="05ba4-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="05ba4-130">CommonParameters</span></span>
<span data-ttu-id="05ba4-131">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="05ba4-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="05ba4-132">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="05ba4-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="05ba4-133">輸入</span><span class="sxs-lookup"><span data-stu-id="05ba4-133">INPUTS</span></span>

### <span data-ttu-id="05ba4-134">System.String</span><span class="sxs-lookup"><span data-stu-id="05ba4-134">System.String</span></span>

<span data-ttu-id="05ba4-135">管線會使用做為目錄檔案名的字串。</span><span class="sxs-lookup"><span data-stu-id="05ba4-135">The pipeline takes a string that is used as the catalog filename.</span></span>

## <span data-ttu-id="05ba4-136">輸出</span><span class="sxs-lookup"><span data-stu-id="05ba4-136">OUTPUTS</span></span>

### <span data-ttu-id="05ba4-137">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="05ba4-137">System.IO.FileInfo</span></span>

## <span data-ttu-id="05ba4-138">注意</span><span class="sxs-lookup"><span data-stu-id="05ba4-138">NOTES</span></span>

## <span data-ttu-id="05ba4-139">相關連結</span><span class="sxs-lookup"><span data-stu-id="05ba4-139">RELATED LINKS</span></span>

[<span data-ttu-id="05ba4-140">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="05ba4-140">Test-FileCatalog</span></span>](Test-FileCatalog.md)

[<span data-ttu-id="05ba4-141">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="05ba4-141">PowerShellGet</span></span>](/powerShell/module/powershellget)
