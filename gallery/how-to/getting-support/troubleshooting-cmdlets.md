---
ms.date: 06/12/2017
contributor: manikb
keywords: 資源庫,powershell,cmdlet,psget
title: 疑難排解 Cmdlet
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892469"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="aeb4a-103">疑難排解 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="aeb4a-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="aeb4a-104">如何解決「警告：無法下載套件『您的封裝名稱』」問題</span><span class="sxs-lookup"><span data-stu-id="aeb4a-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="aeb4a-105">當 `Install-Module` 或 `Update-Module` 有時在某些電腦上失敗時即會回報此問題。</span><span class="sxs-lookup"><span data-stu-id="aeb4a-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="aeb4a-106">根據我們的調查，這和網路連線有關。</span><span class="sxs-lookup"><span data-stu-id="aeb4a-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="aeb4a-107">我們近期更新了 NuGet 套件，使其能夠確實下載封裝。</span><span class="sxs-lookup"><span data-stu-id="aeb4a-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="aeb4a-108">您可以遵循下方指示安裝 NuGet 提供者的最新組建，然後安裝或更新您的模組。</span><span class="sxs-lookup"><span data-stu-id="aeb4a-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="aeb4a-109">以下使用 'Azure' 模組為例。</span><span class="sxs-lookup"><span data-stu-id="aeb4a-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```