---
ms.date: 06/12/2017
contributor: manikb
keywords: 資源庫,powershell,cmdlet,psget
title: 疑難排解 Cmdlet
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328299"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="c7bc0-103">疑難排解 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c7bc0-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="c7bc0-104">如何解決「警告：無法下載套件 '您的套件名稱'」問題</span><span class="sxs-lookup"><span data-stu-id="c7bc0-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="c7bc0-105">當 `Install-Module` 或 `Update-Module` 有時在某些電腦上失敗時即會回報此問題。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="c7bc0-106">根據我們的調查，這和網路連線有關。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="c7bc0-107">我們近期更新了 NuGet 套件，使其能夠確實下載封裝。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="c7bc0-108">您可以遵循下方指示安裝 NuGet 提供者的最新組建，然後安裝或更新您的模組。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="c7bc0-109">以下使用 'Azure' 模組為例。</span><span class="sxs-lookup"><span data-stu-id="c7bc0-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
