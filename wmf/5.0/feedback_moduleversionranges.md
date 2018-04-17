---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 89e908969641afd9ad9541dcfedcc8eb6315d07c
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="9c448-102">宣告版本範圍 (1.\* 等等) 的模組支援</span><span class="sxs-lookup"><span data-stu-id="9c448-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="9c448-103">結合 **-MinimumVersion** 之後，**-MaximumVersion** 現在可讓使用者在特定範圍內取得/匯入模組。</span><span class="sxs-lookup"><span data-stu-id="9c448-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="9c448-104">此參數也支援**。**\*.</span><span class="sxs-lookup"><span data-stu-id="9c448-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="9c448-105">下列範例會顯示其運作方式︰</span><span class="sxs-lookup"><span data-stu-id="9c448-105">The following example shows how it works:</span></span>

<span data-ttu-id="9c448-106">現在，您可以結合**-MinimumVersion**和**-MaximumVersion**匯入特定範圍內的模組：</span><span class="sxs-lookup"><span data-stu-id="9c448-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
