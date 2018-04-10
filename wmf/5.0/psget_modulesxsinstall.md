---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: f9a121c320ffb780503dbe0c278f698a6fa40289
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="172c1-102">PowerShell 5.0 或更新版本的並存版本支援</span><span class="sxs-lookup"><span data-stu-id="172c1-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="172c1-103">在 Windows PowerShell 5.0 或更新版本中執行的 Install-Module、Update-Module 和 Publish-Module Cmdlet 現在都有並存 (SxS) 模組版本支援。</span><span class="sxs-lookup"><span data-stu-id="172c1-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="172c1-104">我們還在 Publish-Module Cmdlet 中加入了 -RequiredVersion 參數來指定要發佈的版本。</span><span class="sxs-lookup"><span data-stu-id="172c1-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="172c1-105">Path 參數現在支援有版本資料夾的模組基底路徑。</span><span class="sxs-lookup"><span data-stu-id="172c1-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="172c1-106">**Install-Module 範例：**</span><span class="sxs-lookup"><span data-stu-id="172c1-106">**Install-Module examples:**</span></span>
```powershell
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Get-InstalledModule -Name PSScriptAnalyzer -AllVersions

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```