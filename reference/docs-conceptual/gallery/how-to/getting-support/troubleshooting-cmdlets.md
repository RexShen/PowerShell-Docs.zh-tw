---
ms.date: 06/12/2017
contributor: manikb
keywords: 資源庫,powershell,cmdlet,psget
title: 疑難排解 Cmdlet
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "72352119"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="581e3-103">疑難排解 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="581e3-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="581e3-104">如何解決「警告：無法下載套件 '您的套件名稱'」問題</span><span class="sxs-lookup"><span data-stu-id="581e3-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="581e3-105">當 `Install-Module` 或 `Update-Module` 有時在某些電腦上失敗時即會回報此問題。</span><span class="sxs-lookup"><span data-stu-id="581e3-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="581e3-106">根據我們的調查，這和網路連線有關。</span><span class="sxs-lookup"><span data-stu-id="581e3-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="581e3-107">我們近期更新了 NuGet 套件，使其能夠確實下載封裝。</span><span class="sxs-lookup"><span data-stu-id="581e3-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="581e3-108">您可以遵循下方指示安裝 NuGet 提供者的最新組建，然後安裝或更新您的模組。</span><span class="sxs-lookup"><span data-stu-id="581e3-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="581e3-109">以下使用 'Azure' 模組為例。</span><span class="sxs-lookup"><span data-stu-id="581e3-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a><span data-ttu-id="581e3-110">必要網路端點</span><span class="sxs-lookup"><span data-stu-id="581e3-110">Required network endpoints</span></span>

<span data-ttu-id="581e3-111">Install 與 Update Cmdlet 需要網際網路存取權才能連線到由 PowerShell 資源庫使用的網路端點。</span><span class="sxs-lookup"><span data-stu-id="581e3-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="581e3-112">確定您的網路存取原則可讓您連線到下列端點。</span><span class="sxs-lookup"><span data-stu-id="581e3-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="581e3-113">oneget.org</span><span class="sxs-lookup"><span data-stu-id="581e3-113">oneget.org</span></span>
- <span data-ttu-id="581e3-114">go.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="581e3-114">go.microsoft.com</span></span>
- <span data-ttu-id="581e3-115">az818661.vo.msecnd.net</span><span class="sxs-lookup"><span data-stu-id="581e3-115">az818661.vo.msecnd.net</span></span>
- <span data-ttu-id="581e3-116">www.powershellgallery.com</span><span class="sxs-lookup"><span data-stu-id="581e3-116">www.powershellgallery.com</span></span>
- <span data-ttu-id="581e3-117">devopsgallerystorage.blob.core.windows.net</span><span class="sxs-lookup"><span data-stu-id="581e3-117">devopsgallerystorage.blob.core.windows.net</span></span>
