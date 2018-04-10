---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 0c450d765531c18c0b73c5c64262e9895f92068a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="archive-cmdlets"></a><span data-ttu-id="8a80f-102">封存 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8a80f-102">Archive cmdlets</span></span>

<span data-ttu-id="8a80f-103">兩個新的 Cmdlet，**Compress-Archive** 和 **Expand-Archive**，讓您可以壓縮和解壓縮 ZIP 檔案。</span><span class="sxs-lookup"><span data-stu-id="8a80f-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="8a80f-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="8a80f-104">Compress-Archive</span></span>
<span data-ttu-id="8a80f-105">**Compress-Archive** Cmdlet 會從指定的檔案中建立新的封存檔案。</span><span class="sxs-lookup"><span data-stu-id="8a80f-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="8a80f-106">封存檔案可讓多個檔案進行封裝，並可選擇性地壓縮成單一檔案，以方便處理和儲存。</span><span class="sxs-lookup"><span data-stu-id="8a80f-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="8a80f-107">封存檔案可以用 **-CompressionLevel** 參數中指定的壓縮演算法壓縮。</span><span class="sxs-lookup"><span data-stu-id="8a80f-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="8a80f-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="8a80f-108">Expand-Archive</span></span>
<span data-ttu-id="8a80f-109">**Expand-Archive** Cmdlet 會從指定的封存檔案中解壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="8a80f-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="8a80f-110">封存檔案可讓多個檔案進行封裝，並可選擇性地壓縮成單一檔案，以方便處理和儲存。</span><span class="sxs-lookup"><span data-stu-id="8a80f-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```