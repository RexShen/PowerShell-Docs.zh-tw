---
ms.date: 06/12/2017
title: 具備相容 PowerShell 版本的指令碼
description: 此文章說明 PowerShellGet Cmdlet 如何支援 Desktop 與 Core 版本的 PowerShell 指令碼。
ms.openlocfilehash: c9d8af24be8138283027263c62140b3fd04d6b24
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656048"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="5c398-103">具備相容 PowerShell 版本的指令碼</span><span class="sxs-lookup"><span data-stu-id="5c398-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="5c398-104">從 5.1 版開始，PowerShell 提供代表各種功能集及平台相容性的不同版本。</span><span class="sxs-lookup"><span data-stu-id="5c398-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="5c398-105">**Desktop Edition︰** 建置在 .NET Framework 上，與在完整使用量的 Windows 版本 (如 Server Core 和 Windows Desktop) 上執行之 PowerShell 版本的指令碼和模組相容。</span><span class="sxs-lookup"><span data-stu-id="5c398-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>

- <span data-ttu-id="5c398-106">**Core Edition︰** 建置在 .NET Core 上，與在降低使用量的 Windows 版本 (如 Nano Server 和 Windows IoT) 上執行之 PowerShell 版本的指令碼和模組相容。</span><span class="sxs-lookup"><span data-stu-id="5c398-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="5c398-107">$PSVersionTable PSEdition 屬性會顯示正在執行的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="5c398-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="5c398-108">指令碼作者可在 `#requires` 陳述式上使用 PSEdition 參數，只允許指令碼在相容的 PowerShell 版本上執行。</span><span class="sxs-lookup"><span data-stu-id="5c398-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a `#requires` statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="5c398-109">PowerShell Gallery 使用者可以尋找特定 PowerShell 版本上所支援的指令碼清單。</span><span class="sxs-lookup"><span data-stu-id="5c398-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="5c398-110">沒有 PSEdition_Desktop 與 PSEdition_Core 標記的指令碼會被視為可在 PowerShell Desktop 版本上正常運作。</span><span class="sxs-lookup"><span data-stu-id="5c398-110">Scripts without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop edition.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="5c398-111">其他詳細資訊</span><span class="sxs-lookup"><span data-stu-id="5c398-111">More details</span></span>

- [<span data-ttu-id="5c398-112">PSEditions 的模組</span><span class="sxs-lookup"><span data-stu-id="5c398-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="5c398-113">PowerShellGallery 的 PSEditions 支援</span><span class="sxs-lookup"><span data-stu-id="5c398-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)
