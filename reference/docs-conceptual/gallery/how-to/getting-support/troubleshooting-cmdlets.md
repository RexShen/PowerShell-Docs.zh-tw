---
ms.date: 06/12/2017
title: 疑難排解 Cmdlet
description: 此文章提供使用 PowerShell 資源庫來對錯誤進行疑難排解的資訊與步驟
ms.openlocfilehash: db9e58c185c6f3bca26ff3639af85fa2dba48909
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661064"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="91740-103">疑難排解 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="91740-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="91740-104">如何解決「警告：無法下載套件 '您的套件名稱'」問題</span><span class="sxs-lookup"><span data-stu-id="91740-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="91740-105">當 `Install-Module` 或 `Update-Module` 有時在某些電腦上失敗時即會回報此問題。</span><span class="sxs-lookup"><span data-stu-id="91740-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="91740-106">根據我們的調查，這和網路連線有關。</span><span class="sxs-lookup"><span data-stu-id="91740-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="91740-107">我們近期更新了 NuGet 套件，使其能夠確實下載封裝。</span><span class="sxs-lookup"><span data-stu-id="91740-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="91740-108">您可以遵循下方指示安裝 NuGet 提供者的最新組建，然後安裝或更新您的模組。</span><span class="sxs-lookup"><span data-stu-id="91740-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="91740-109">以下使用 'Azure' 模組為例。</span><span class="sxs-lookup"><span data-stu-id="91740-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a><span data-ttu-id="91740-110">必要網路端點</span><span class="sxs-lookup"><span data-stu-id="91740-110">Required network endpoints</span></span>

<span data-ttu-id="91740-111">Install 與 Update Cmdlet 需要網際網路存取權才能連線到由 PowerShell 資源庫使用的網路端點。</span><span class="sxs-lookup"><span data-stu-id="91740-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="91740-112">確定您的網路存取原則可讓您連線到下列端點。</span><span class="sxs-lookup"><span data-stu-id="91740-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="91740-113">oneget.org</span><span class="sxs-lookup"><span data-stu-id="91740-113">oneget.org</span></span>
- <span data-ttu-id="91740-114">go.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="91740-114">go.microsoft.com</span></span>
- <span data-ttu-id="91740-115">az818661.vo.msecnd.net</span><span class="sxs-lookup"><span data-stu-id="91740-115">az818661.vo.msecnd.net</span></span>
- <span data-ttu-id="91740-116">www.powershellgallery.com</span><span class="sxs-lookup"><span data-stu-id="91740-116">www.powershellgallery.com</span></span>
- <span data-ttu-id="91740-117">devopsgallerystorage.blob.core.windows.net</span><span class="sxs-lookup"><span data-stu-id="91740-117">devopsgallerystorage.blob.core.windows.net</span></span>
