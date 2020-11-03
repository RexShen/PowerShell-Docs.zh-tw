---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: ce5dd31170bc47edaa04ca3c31deab62dc4ec354
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208784"
---
# <span data-ttu-id="4a16c-103">Import-BinaryMiLog</span><span class="sxs-lookup"><span data-stu-id="4a16c-103">Import-BinaryMiLog</span></span>

## <span data-ttu-id="4a16c-104">概要</span><span class="sxs-lookup"><span data-stu-id="4a16c-104">SYNOPSIS</span></span>
<span data-ttu-id="4a16c-105">用來根據匯出檔案的內容重新建立儲存的物件。</span><span class="sxs-lookup"><span data-stu-id="4a16c-105">Used to re-create the saved objects based on the contents of an export file.</span></span>

## <span data-ttu-id="4a16c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4a16c-106">SYNTAX</span></span>

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="4a16c-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4a16c-107">DESCRIPTION</span></span>

<span data-ttu-id="4a16c-108">使用這個指令程式可根據所建立的匯出檔案內容，重新建立儲存的物件 `Export-BinaryMILog` 。</span><span class="sxs-lookup"><span data-stu-id="4a16c-108">Use this cmdlet to re-create saved objects based on the contents of an export file created by `Export-BinaryMILog`.</span></span> <span data-ttu-id="4a16c-109">這個 Cmdlet 類似于 `Import-Clixml` ，但會將 `Export-BinaryMILog` 產生的物件儲存在二進位編碼的檔案中。</span><span class="sxs-lookup"><span data-stu-id="4a16c-109">This cmdlet is similar to `Import-Clixml`, except that `Export-BinaryMILog` stores the resulting object in a binary encoded file.</span></span>

## <span data-ttu-id="4a16c-110">範例</span><span class="sxs-lookup"><span data-stu-id="4a16c-110">EXAMPLES</span></span>

### <span data-ttu-id="4a16c-111">範例 1-將匯出的物件還原至檔案</span><span class="sxs-lookup"><span data-stu-id="4a16c-111">Example 1 - Restore objects exported to a file</span></span>

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## <span data-ttu-id="4a16c-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4a16c-112">PARAMETERS</span></span>

### <span data-ttu-id="4a16c-113">-Path</span><span class="sxs-lookup"><span data-stu-id="4a16c-113">-Path</span></span>

<span data-ttu-id="4a16c-114">指定要在其中儲存物件之二進位表示的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="4a16c-114">Specifies the path of the file in which to store the binary representation of the object.</span></span> <span data-ttu-id="4a16c-115">**Path** 參數支援萬用字元和相對路徑。</span><span class="sxs-lookup"><span data-stu-id="4a16c-115">The **Path** parameter supports wildcards and relative paths.</span></span> <span data-ttu-id="4a16c-116">如果路徑解析為一個以上的檔案，則此 Cmdlet 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4a16c-116">This cmdlet generates an error if the path resolves to more than one file.</span></span>

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

### <span data-ttu-id="4a16c-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4a16c-117">CommonParameters</span></span>
<span data-ttu-id="4a16c-118">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4a16c-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4a16c-119">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4a16c-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4a16c-120">輸入</span><span class="sxs-lookup"><span data-stu-id="4a16c-120">INPUTS</span></span>

### <span data-ttu-id="4a16c-121">無</span><span class="sxs-lookup"><span data-stu-id="4a16c-121">None</span></span>

## <span data-ttu-id="4a16c-122">輸出</span><span class="sxs-lookup"><span data-stu-id="4a16c-122">OUTPUTS</span></span>

### <span data-ttu-id="4a16c-123">System.Object</span><span class="sxs-lookup"><span data-stu-id="4a16c-123">System.Object</span></span>

## <span data-ttu-id="4a16c-124">注意</span><span class="sxs-lookup"><span data-stu-id="4a16c-124">NOTES</span></span>

## <span data-ttu-id="4a16c-125">相關連結</span><span class="sxs-lookup"><span data-stu-id="4a16c-125">RELATED LINKS</span></span>
