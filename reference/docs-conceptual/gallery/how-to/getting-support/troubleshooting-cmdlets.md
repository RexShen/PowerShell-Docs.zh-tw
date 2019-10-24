---
ms.date: 06/12/2017
contributor: manikb
keywords: 資源庫,powershell,cmdlet,psget
title: 疑難排解 Cmdlet
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352119"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="b6fea-103">疑難排解 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6fea-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="b6fea-104">如何解決「警告：無法下載套件 '您的套件名稱'」問題</span><span class="sxs-lookup"><span data-stu-id="b6fea-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="b6fea-105">當 `Install-Module` 或 `Update-Module` 有時在某些電腦上失敗時即會回報此問題。</span><span class="sxs-lookup"><span data-stu-id="b6fea-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="b6fea-106">根據我們的調查，這和網路連線有關。</span><span class="sxs-lookup"><span data-stu-id="b6fea-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="b6fea-107">我們近期更新了 NuGet 套件，使其能夠確實下載封裝。</span><span class="sxs-lookup"><span data-stu-id="b6fea-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="b6fea-108">您可以遵循下方指示安裝 NuGet 提供者的最新組建，然後安裝或更新您的模組。</span><span class="sxs-lookup"><span data-stu-id="b6fea-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="b6fea-109">以下使用 'Azure' 模組為例。</span><span class="sxs-lookup"><span data-stu-id="b6fea-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a><span data-ttu-id="b6fea-110">必要網路端點</span><span class="sxs-lookup"><span data-stu-id="b6fea-110">Required network endpoints</span></span>

<span data-ttu-id="b6fea-111">Install 與 Update Cmdlet 需要網際網路存取權才能連線到由 PowerShell 資源庫使用的網路端點。</span><span class="sxs-lookup"><span data-stu-id="b6fea-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="b6fea-112">確定您的網路存取原則可讓您連線到下列端點。</span><span class="sxs-lookup"><span data-stu-id="b6fea-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="b6fea-113">oneget.org</span><span class="sxs-lookup"><span data-stu-id="b6fea-113">oneget.org</span></span>
- <span data-ttu-id="b6fea-114">go.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="b6fea-114">go.microsoft.com</span></span>
- <span data-ttu-id="b6fea-115">az818661.vo.msecnd.net</span><span class="sxs-lookup"><span data-stu-id="b6fea-115">az818661.vo.msecnd.net</span></span>
- <span data-ttu-id="b6fea-116">[www.powershellgallery.com](www.powershellgallery.com)</span><span class="sxs-lookup"><span data-stu-id="b6fea-116">www.powershellgallery.com</span></span>
- <span data-ttu-id="b6fea-117">devopsgallerystorage.blob.core.windows.net</span><span class="sxs-lookup"><span data-stu-id="b6fea-117">devopsgallerystorage.blob.core.windows.net</span></span>
