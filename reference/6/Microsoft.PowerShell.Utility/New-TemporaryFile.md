---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-temporaryfile?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TemporaryFile
ms.openlocfilehash: 566a8bf22815e55457da430a02af391bb308b50c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204571"
---
# <span data-ttu-id="bdf85-103">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="bdf85-103">New-TemporaryFile</span></span>

## <span data-ttu-id="bdf85-104">概要</span><span class="sxs-lookup"><span data-stu-id="bdf85-104">SYNOPSIS</span></span>
<span data-ttu-id="bdf85-105">建立暫存檔。</span><span class="sxs-lookup"><span data-stu-id="bdf85-105">Creates a temporary file.</span></span>

## <span data-ttu-id="bdf85-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bdf85-106">SYNTAX</span></span>

```
New-TemporaryFile [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bdf85-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bdf85-107">DESCRIPTION</span></span>

<span data-ttu-id="bdf85-108">此 Cmdlet 會建立可在腳本中使用的暫存檔案。</span><span class="sxs-lookup"><span data-stu-id="bdf85-108">This cmdlet creates temporary files that you can use in scripts.</span></span>

<span data-ttu-id="bdf85-109">此 `New-TemporaryFile` Cmdlet 會建立副檔名為的空白檔案 `.tmp` 。</span><span class="sxs-lookup"><span data-stu-id="bdf85-109">The `New-TemporaryFile` cmdlet creates an empty file that has the `.tmp` file name extension.</span></span>
<span data-ttu-id="bdf85-110">此 Cmdlet 會為檔案命名 `tmp<NNNN>.tmp` ，其中 `<NNNN>` 是隨機的十六進位數位。</span><span class="sxs-lookup"><span data-stu-id="bdf85-110">This cmdlet names the file `tmp<NNNN>.tmp`, where `<NNNN>` is a random hexadecimal number.</span></span>
<span data-ttu-id="bdf85-111">Cmdlet 會在您的 **暫存** 資料夾中建立檔案。</span><span class="sxs-lookup"><span data-stu-id="bdf85-111">The cmdlet creates the file in your **TEMP** folder.</span></span>

<span data-ttu-id="bdf85-112">此 Cmdlet 會使用 [GetTempPath ( # B1](/dotnet/api/system.io.path.gettemppath) 方法來尋找您的 **暫存** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="bdf85-112">This cmdlet uses the [Path.GetTempPath()](/dotnet/api/system.io.path.gettemppath) method to find your **TEMP** folder.</span></span> <span data-ttu-id="bdf85-113">這個方法會以下列順序檢查環境變數是否存在，並使用第一個找到的路徑：</span><span class="sxs-lookup"><span data-stu-id="bdf85-113">This method checks for the existence of environment variables in the following order and uses the first path found:</span></span>

- <span data-ttu-id="bdf85-114">在 Windows 平臺上：</span><span class="sxs-lookup"><span data-stu-id="bdf85-114">On Windows platforms:</span></span>

  1. <span data-ttu-id="bdf85-115">TMP 環境變數所指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="bdf85-115">The path specified by the TMP environment variable.</span></span>
  1. <span data-ttu-id="bdf85-116">TEMP 環境變數所指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="bdf85-116">The path specified by the TEMP environment variable.</span></span>
  1. <span data-ttu-id="bdf85-117">USERPROFILE 環境變數所指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="bdf85-117">The path specified by the USERPROFILE environment variable.</span></span>
  1. <span data-ttu-id="bdf85-118">Windows 目錄。</span><span class="sxs-lookup"><span data-stu-id="bdf85-118">The Windows directory.</span></span>

- <span data-ttu-id="bdf85-119">在非 Windows 平臺上：使用 TMPDIR 環境變數所指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="bdf85-119">On non-Windows platforms: Uses the path specified by the TMPDIR environment variable.</span></span>

## <span data-ttu-id="bdf85-120">範例</span><span class="sxs-lookup"><span data-stu-id="bdf85-120">EXAMPLES</span></span>

### <span data-ttu-id="bdf85-121">範例1：建立暫存檔案</span><span class="sxs-lookup"><span data-stu-id="bdf85-121">Example 1: Create a temporary file</span></span>

```powershell
$TempFile = New-TemporaryFile
```

<span data-ttu-id="bdf85-122">此命令會 `.tmp` 在暫存資料夾中產生檔案，然後將檔案的參考儲存在 `$TempFile` 變數中。</span><span class="sxs-lookup"><span data-stu-id="bdf85-122">This command generates a `.tmp` file in your temporary folder, and then stores a reference to the file in the `$TempFile` variable.</span></span> <span data-ttu-id="bdf85-123">您稍後可以在腳本中使用此檔案。</span><span class="sxs-lookup"><span data-stu-id="bdf85-123">You can use this file later in your script.</span></span>

## <span data-ttu-id="bdf85-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bdf85-124">PARAMETERS</span></span>

### <span data-ttu-id="bdf85-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bdf85-125">-Confirm</span></span>

<span data-ttu-id="bdf85-126">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="bdf85-126">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bdf85-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bdf85-127">-WhatIf</span></span>

<span data-ttu-id="bdf85-128">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="bdf85-128">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="bdf85-129">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="bdf85-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bdf85-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bdf85-130">CommonParameters</span></span>

<span data-ttu-id="bdf85-131">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bdf85-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bdf85-132">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="bdf85-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="bdf85-133">輸入</span><span class="sxs-lookup"><span data-stu-id="bdf85-133">INPUTS</span></span>

## <span data-ttu-id="bdf85-134">輸出</span><span class="sxs-lookup"><span data-stu-id="bdf85-134">OUTPUTS</span></span>

### <span data-ttu-id="bdf85-135">System.IO.FileInfo</span><span class="sxs-lookup"><span data-stu-id="bdf85-135">System.IO.FileInfo</span></span>

<span data-ttu-id="bdf85-136">此 Cmdlet 會傳回代表暫存檔案的 **FileInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="bdf85-136">This cmdlet returns a **FileInfo** object that represents the temporary file.</span></span>

## <span data-ttu-id="bdf85-137">注意</span><span class="sxs-lookup"><span data-stu-id="bdf85-137">NOTES</span></span>

## <span data-ttu-id="bdf85-138">相關連結</span><span class="sxs-lookup"><span data-stu-id="bdf85-138">RELATED LINKS</span></span>
