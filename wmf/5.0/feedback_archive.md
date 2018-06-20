---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218088"
---
# <a name="archive-cmdlets"></a><span data-ttu-id="ddd72-102">封存 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ddd72-102">Archive cmdlets</span></span>

<span data-ttu-id="ddd72-103">兩個新的 Cmdlet，**Compress-Archive** 和 **Expand-Archive**，讓您可以壓縮和解壓縮 ZIP 檔案。</span><span class="sxs-lookup"><span data-stu-id="ddd72-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="ddd72-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="ddd72-104">Compress-Archive</span></span>
<span data-ttu-id="ddd72-105">**Compress-Archive** Cmdlet 會從指定的檔案中建立新的封存檔案。</span><span class="sxs-lookup"><span data-stu-id="ddd72-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="ddd72-106">封存檔案可讓多個檔案進行封裝，並可選擇性地壓縮成單一檔案，以方便處理和儲存。</span><span class="sxs-lookup"><span data-stu-id="ddd72-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="ddd72-107">封存檔案可以用 **-CompressionLevel** 參數中指定的壓縮演算法壓縮。</span><span class="sxs-lookup"><span data-stu-id="ddd72-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="ddd72-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="ddd72-108">Expand-Archive</span></span>
<span data-ttu-id="ddd72-109">**Expand-Archive** Cmdlet 會從指定的封存檔案中解壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="ddd72-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="ddd72-110">封存檔案可讓多個檔案進行封裝，並可選擇性地壓縮成單一檔案，以方便處理和儲存。</span><span class="sxs-lookup"><span data-stu-id="ddd72-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
