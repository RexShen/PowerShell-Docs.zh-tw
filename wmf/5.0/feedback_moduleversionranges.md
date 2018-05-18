---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="7fa43-102">宣告版本範圍 (1.\* 等等) 的模組支援</span><span class="sxs-lookup"><span data-stu-id="7fa43-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="7fa43-103">結合 **-MinimumVersion** 之後，**-MaximumVersion** 現在可讓使用者在特定範圍內取得/匯入模組。</span><span class="sxs-lookup"><span data-stu-id="7fa43-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="7fa43-104">參數也支援 **.**\*。</span><span class="sxs-lookup"><span data-stu-id="7fa43-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="7fa43-105">下列範例會顯示其運作方式︰</span><span class="sxs-lookup"><span data-stu-id="7fa43-105">The following example shows how it works:</span></span>

<span data-ttu-id="7fa43-106">現在，您可以結合 **-MinimumVersion** 和 **-MaximumVersion** 來匯入特定範圍內的模組：</span><span class="sxs-lookup"><span data-stu-id="7fa43-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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
