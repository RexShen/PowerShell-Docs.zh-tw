---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: d23cfc2aaa680c247aaab91d8875c64c9d62187e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="archive-cmdlets"></a><span data-ttu-id="278a9-102">封存 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="278a9-102">Archive cmdlets</span></span>

<span data-ttu-id="278a9-103">兩個新的 Cmdlet，**Compress-Archive** 和 **Expand-Archive**，讓您可以壓縮和解壓縮 ZIP 檔案。</span><span class="sxs-lookup"><span data-stu-id="278a9-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="278a9-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="278a9-104">Compress-Archive</span></span>
<span data-ttu-id="278a9-105">**Compress-Archive** Cmdlet 會從指定的檔案中建立新的封存檔案。</span><span class="sxs-lookup"><span data-stu-id="278a9-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="278a9-106">封存檔案可讓多個檔案進行封裝，並可選擇性地壓縮成單一檔案，以方便處理和儲存。</span><span class="sxs-lookup"><span data-stu-id="278a9-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="278a9-107">封存檔案可以用 **-CompressionLevel** 參數中指定的壓縮演算法壓縮。</span><span class="sxs-lookup"><span data-stu-id="278a9-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```PowerShell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="278a9-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="278a9-108">Expand-Archive</span></span>
<span data-ttu-id="278a9-109">**Expand-Archive** Cmdlet 會從指定的封存檔案中解壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="278a9-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="278a9-110">封存檔案可讓多個檔案進行封裝，並可選擇性地壓縮成單一檔案，以方便處理和儲存。</span><span class="sxs-lookup"><span data-stu-id="278a9-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```PowerShell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```

