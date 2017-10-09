---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: f68847ba8292a277e464025c1baa17a5aa2752f5
ms.sourcegitcommit: 4ab9a86e47b6effe8fe22ebeb81e8fadff41d31c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2017
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="ec283-102">PowerShell 5.0 或更新版本的並存版本支援</span><span class="sxs-lookup"><span data-stu-id="ec283-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="ec283-103">在 Windows PowerShell 5.0 或更新版本中執行的 Install-Module、Update-Module 和 Publish-Module Cmdlet 現在都有並存 (SxS) 模組版本支援。</span><span class="sxs-lookup"><span data-stu-id="ec283-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="ec283-104">我們還在 Publish-Module Cmdlet 中加入了 -RequiredVersion 參數來指定要發佈的版本。</span><span class="sxs-lookup"><span data-stu-id="ec283-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="ec283-105">Path 參數現在支援有版本資料夾的模組基底路徑。</span><span class="sxs-lookup"><span data-stu-id="ec283-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="ec283-106">**Install-Module 範例：**</span><span class="sxs-lookup"><span data-stu-id="ec283-106">**Install-Module examples:**</span></span>
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

