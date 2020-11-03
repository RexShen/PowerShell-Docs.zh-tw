---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/export-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-BinaryMiLog
ms.openlocfilehash: cf03ad884121c6cf8cf65cdb791cbdc4e587c3b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202515"
---
# <span data-ttu-id="59fcf-103">Export-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="59fcf-103">Export-BinaryMiLog</span></span>

## <span data-ttu-id="59fcf-104">概要</span><span class="sxs-lookup"><span data-stu-id="59fcf-104">SYNOPSIS</span></span>
<span data-ttu-id="59fcf-105">建立物件或物件的二進位編碼標記法，並將它儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="59fcf-105">Creates a binary encoded representation of an object or objects and stores it in a file.</span></span>

## <span data-ttu-id="59fcf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="59fcf-106">SYNTAX</span></span>

```
Export-BinaryMiLog [-InputObject <CimInstance>] [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="59fcf-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="59fcf-107">DESCRIPTION</span></span>

<span data-ttu-id="59fcf-108">`Export-BinaryMILog`Cmdlet 會建立物件或物件的二進位標記法，並將它儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="59fcf-108">The `Export-BinaryMILog` cmdlet creates a binary-based representation of an object or objects and stores it in a file.</span></span> <span data-ttu-id="59fcf-109">然後，您可以使用 `Import-BinaryMiLog` Cmdlet，根據該檔案的內容重新建立儲存的物件。</span><span class="sxs-lookup"><span data-stu-id="59fcf-109">You can then use the `Import-BinaryMiLog` cmdlet to re-create the saved object based on the contents of that file.</span></span>

<span data-ttu-id="59fcf-110">這個 Cmdlet 類似于 `Import-Clixml` ，但會將 `Export-BinaryMILog` 產生的物件儲存在二進位編碼的檔案中。</span><span class="sxs-lookup"><span data-stu-id="59fcf-110">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="59fcf-111">範例</span><span class="sxs-lookup"><span data-stu-id="59fcf-111">EXAMPLES</span></span>

### <span data-ttu-id="59fcf-112">範例 1-建立 CimInstances 的二進位標記法</span><span class="sxs-lookup"><span data-stu-id="59fcf-112">Example 1 - Create a binary representation of CimInstances</span></span>

```powershell
Get-CimInstance Win32_Process | Export-BinaryMiLog -Path "Processes.bmil"
```

<span data-ttu-id="59fcf-113">此命令會將 **CimInstances** 匯出至 Path 參數所指定的二進位 MI 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="59fcf-113">This command exports **CimInstances** to a binary MI log file specified by the Path parameter.</span></span> <span data-ttu-id="59fcf-114">請參閱 Import-BinaryMiLog 的範例，以瞭解如何藉由匯入這個檔案來重新建立 **CimInstances** 。</span><span class="sxs-lookup"><span data-stu-id="59fcf-114">See the example for Import-BinaryMiLog to see how to recreate the **CimInstances** by importing this file.</span></span>

## <span data-ttu-id="59fcf-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="59fcf-115">PARAMETERS</span></span>

### <span data-ttu-id="59fcf-116">-InputObject</span><span class="sxs-lookup"><span data-stu-id="59fcf-116">-InputObject</span></span>

<span data-ttu-id="59fcf-117">指定此 Cmdlet 的輸入。</span><span class="sxs-lookup"><span data-stu-id="59fcf-117">Specifies the input to this cmdlet.</span></span> <span data-ttu-id="59fcf-118">您可以使用這個參數，或者您可以透過管線將輸入傳送到此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="59fcf-118">You can use this parameter, or you can pipe the input to this cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="59fcf-119">-Path</span><span class="sxs-lookup"><span data-stu-id="59fcf-119">-Path</span></span>

<span data-ttu-id="59fcf-120">指定要在其中儲存物件之二進位表示的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="59fcf-120">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="59fcf-121">**Path** 參數支援萬用字元和相對路徑。</span><span class="sxs-lookup"><span data-stu-id="59fcf-121">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="59fcf-122">如果路徑解析為一個以上的檔案，則此 Cmdlet 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="59fcf-122">This cmdlet generates an error if the path resolves to more than one file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="59fcf-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="59fcf-123">CommonParameters</span></span>

<span data-ttu-id="59fcf-124">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="59fcf-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="59fcf-125">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="59fcf-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="59fcf-126">輸入</span><span class="sxs-lookup"><span data-stu-id="59fcf-126">INPUTS</span></span>

### <span data-ttu-id="59fcf-127">Microsoft.Management.Infrastructure.CimInstance</span><span class="sxs-lookup"><span data-stu-id="59fcf-127">Microsoft.Management.Infrastructure.CimInstance</span></span>

## <span data-ttu-id="59fcf-128">輸出</span><span class="sxs-lookup"><span data-stu-id="59fcf-128">OUTPUTS</span></span>

### <span data-ttu-id="59fcf-129">System.Object</span><span class="sxs-lookup"><span data-stu-id="59fcf-129">System.Object</span></span>

## <span data-ttu-id="59fcf-130">注意</span><span class="sxs-lookup"><span data-stu-id="59fcf-130">NOTES</span></span>

## <span data-ttu-id="59fcf-131">相關連結</span><span class="sxs-lookup"><span data-stu-id="59fcf-131">RELATED LINKS</span></span>

[<span data-ttu-id="59fcf-132">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="59fcf-132">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="59fcf-133">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="59fcf-133">Import-BinaryMiLog</span></span>](import-binarymilog.md)

[<span data-ttu-id="59fcf-134">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="59fcf-134">Import-Clixml</span></span>](../microsoft.powershell.utility/import-clixml.md)
