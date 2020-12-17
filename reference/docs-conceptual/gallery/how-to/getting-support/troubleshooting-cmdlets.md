---
ms.date: 12/01/2020
title: 疑難排解 Cmdlet
description: 此文章提供使用 PowerShell 資源庫來對錯誤進行疑難排解的資訊與步驟
ms.openlocfilehash: 980da8ea7b8a09513f33a9939d512c437b755d8d
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913313"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="f3c6c-103">疑難排解 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f3c6c-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="f3c6c-104">如何解決「警告：無法下載套件 '您的套件名稱'」問題</span><span class="sxs-lookup"><span data-stu-id="f3c6c-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="f3c6c-105">當 `Install-Module` 或 `Update-Module` 有時在某些電腦上失敗時即會回報此問題。</span><span class="sxs-lookup"><span data-stu-id="f3c6c-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="f3c6c-106">根據我們的調查，這和網路連線有關。</span><span class="sxs-lookup"><span data-stu-id="f3c6c-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="f3c6c-107">我們近期更新了 NuGet 套件，使其能夠確實下載封裝。</span><span class="sxs-lookup"><span data-stu-id="f3c6c-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="f3c6c-108">您可以遵循下方指示安裝 NuGet 提供者的最新組建，然後安裝或更新您的模組。</span><span class="sxs-lookup"><span data-stu-id="f3c6c-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="f3c6c-109">以下使用 'Azure' 模組為例。</span><span class="sxs-lookup"><span data-stu-id="f3c6c-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

## <a name="required-network-endpoints"></a><span data-ttu-id="f3c6c-110">必要網路端點</span><span class="sxs-lookup"><span data-stu-id="f3c6c-110">Required network endpoints</span></span>

<span data-ttu-id="f3c6c-111">Install 與 Update Cmdlet 需要網際網路存取權才能連線到由 PowerShell 資源庫使用的網路端點。</span><span class="sxs-lookup"><span data-stu-id="f3c6c-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="f3c6c-112">確定您的網路存取原則可讓您連線到下列端點。</span><span class="sxs-lookup"><span data-stu-id="f3c6c-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="f3c6c-113">`psg-prod-eastus.azureedge.net` - CDN 主機名稱</span><span class="sxs-lookup"><span data-stu-id="f3c6c-113">`psg-prod-eastus.azureedge.net` - CDN hostname</span></span>
- <span data-ttu-id="f3c6c-114">`az818661.vo.msecnd.net` - CDN 主機名稱</span><span class="sxs-lookup"><span data-stu-id="f3c6c-114">`az818661.vo.msecnd.net` - CDN hostname</span></span>
- <span data-ttu-id="f3c6c-115">`devopsgallerystorage.blob.core.windows.net` - 儲存體帳戶主機名稱</span><span class="sxs-lookup"><span data-stu-id="f3c6c-115">`devopsgallerystorage.blob.core.windows.net` - storage account hostname</span></span>
- <span data-ttu-id="f3c6c-116">`*.powershellgallery.com` - 網站</span><span class="sxs-lookup"><span data-stu-id="f3c6c-116">`*.powershellgallery.com` - website</span></span>
- <span data-ttu-id="f3c6c-117">`go.microsoft.com` - 重新導向服務</span><span class="sxs-lookup"><span data-stu-id="f3c6c-117">`go.microsoft.com` - redirection service</span></span>

> [!NOTE]
> <span data-ttu-id="f3c6c-118">當 PowerShell 資源庫服務發生中斷時，與 PowerShell 資源庫互動的 Cmdlet 可能會因未預期的錯誤而失敗。</span><span class="sxs-lookup"><span data-stu-id="f3c6c-118">Cmdlets that interact with the PowerShell Gallery can fail with unexpected errors when there is an outage of the PowerShell Gallery services.</span></span> <span data-ttu-id="f3c6c-119">若要查看 PowerShell 資源庫目前的狀態，請參閱 GitHub 上的 [PowerShell 資源庫狀態](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) \(英文\) 頁面。</span><span class="sxs-lookup"><span data-stu-id="f3c6c-119">To see the current status of the PowerShell Gallery, see the [PowerShell Gallery Status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) page on GitHub.</span></span>
