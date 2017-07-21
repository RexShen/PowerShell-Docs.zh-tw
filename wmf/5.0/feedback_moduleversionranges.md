---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: b64464eb2b4dd87ebe716e159fb916ac328b3b37
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="c274c-102">宣告版本範圍 (1.* 等等) 的模組支援</span><span class="sxs-lookup"><span data-stu-id="c274c-102">Modules support for declaring version ranges (1.*, etc)</span></span>
<span data-ttu-id="c274c-103">結合 **-MinimumVersion** 之後，**-MaximumVersion** 現在可讓使用者在特定範圍內取得/匯入模組。</span><span class="sxs-lookup"><span data-stu-id="c274c-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="c274c-104">此參數也支援 **.***。</span><span class="sxs-lookup"><span data-stu-id="c274c-104">The parameter also support **.***.</span></span> <span data-ttu-id="c274c-105">下列範例會顯示其運作方式︰</span><span class="sxs-lookup"><span data-stu-id="c274c-105">The following example shows how it works:</span></span>

```PowerShell
Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:

PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

