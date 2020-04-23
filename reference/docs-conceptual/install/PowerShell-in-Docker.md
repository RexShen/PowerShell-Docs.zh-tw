---
title: 在 Docker 中使用 PowerShell
description: 如何使用預先安裝在 Docker 映像中的 PowerShell。
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: b16a31a04ca863ab55c7c9718b1a1a973e61ee46
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "80646381"
---
# <a name="using-powershell-in-docker"></a><span data-ttu-id="87d1b-103">在 Docker 中使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="87d1b-103">Using PowerShell in Docker</span></span>

<span data-ttu-id="87d1b-104">我們會以預先安裝 PowerShell 的方式發行 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="87d1b-104">We publish Docker images with PowerShell preinstalled.</span></span> <span data-ttu-id="87d1b-105">此文章會示範如何開始使用 Docker 容器中的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="87d1b-105">This article shows you how to get started using PowerShell in the Docker container.</span></span>

## <a name="finding-available-images"></a><span data-ttu-id="87d1b-106">尋找可用的映像</span><span class="sxs-lookup"><span data-stu-id="87d1b-106">Finding available images</span></span>

<span data-ttu-id="87d1b-107">發行的映像需要 Docker 17.05 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="87d1b-107">The released images require Docker 17.05 or newer.</span></span> <span data-ttu-id="87d1b-108">您也應該要能在沒有 `sudo` 或本機系統管理員權限的情況下執行 Docker。</span><span class="sxs-lookup"><span data-stu-id="87d1b-108">It is also expected that you are able to run Docker without `sudo` or local administrative rights.</span></span> <span data-ttu-id="87d1b-109">請遵循 Docker 的官方[指示][install]以正確安裝 `docker`。</span><span class="sxs-lookup"><span data-stu-id="87d1b-109">Please follow Docker's official [instructions][install] to install `docker` correctly.</span></span>

<span data-ttu-id="87d1b-110">發行容器會衍生自官方發佈映像 (例如 `centos:7`)，然後安裝相依性，最後安裝 PowerShell 套件。</span><span class="sxs-lookup"><span data-stu-id="87d1b-110">The release containers derive from the official distribution image, such as `centos:7`, then install dependencies, and finally install the PowerShell package.</span></span>

<span data-ttu-id="87d1b-111">這些容器會存留在 [hub.docker.com/r/microsoft/powershell][docker-release] 中。</span><span class="sxs-lookup"><span data-stu-id="87d1b-111">These containers live at [hub.docker.com/r/microsoft/powershell][docker-release].</span></span>

<span data-ttu-id="87d1b-112">如需這些 Docker 映像的詳細資訊，請瀏覽 GitHub 上的 [PowerShell-Docker][PowerShell-Docker] 存放庫。</span><span class="sxs-lookup"><span data-stu-id="87d1b-112">For more information about these Docker images, visit the [PowerShell-Docker][PowerShell-Docker] repository on GitHub.</span></span>

## <a name="using-powershell-in-a-container"></a><span data-ttu-id="87d1b-113">在容器中使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="87d1b-113">Using PowerShell in a container</span></span>

<span data-ttu-id="87d1b-114">下列步驟會示範下載映像並啟動互動式 PowerShell 工作階段所需的 Docker 命令。</span><span class="sxs-lookup"><span data-stu-id="87d1b-114">The following steps show the Docker commands required to download the image and start an interactive PowerShell session.</span></span>

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a><span data-ttu-id="87d1b-115">在不再需要映像時加以移除</span><span class="sxs-lookup"><span data-stu-id="87d1b-115">Remove the image when no longer needed</span></span>

<span data-ttu-id="87d1b-116">下列命令用於在不再需要 Docker 映像時將其刪除。</span><span class="sxs-lookup"><span data-stu-id="87d1b-116">The following command is used to delete the Docker image when you no longer need it.</span></span>

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a><span data-ttu-id="87d1b-117">法律和授權</span><span class="sxs-lookup"><span data-stu-id="87d1b-117">Legal and Licensing</span></span>

<span data-ttu-id="87d1b-118">PowerShell 是根據 [MIT 授權][]進行授權。</span><span class="sxs-lookup"><span data-stu-id="87d1b-118">PowerShell is licensed under the [MIT license][].</span></span>

### <a name="windows-docker-file-and-image-licenses"></a><span data-ttu-id="87d1b-119">Windows Docker 檔案與映像授權</span><span class="sxs-lookup"><span data-stu-id="87d1b-119">Windows Docker File and Image Licenses</span></span>

<span data-ttu-id="87d1b-120">一旦要求及使用適用於 Windows 容器的容器 OS 映像，即表示您確認、了解並同意可於 Docker Hub 上取得的補充授權條款：</span><span class="sxs-lookup"><span data-stu-id="87d1b-120">By requesting and using the Container OS Image for Windows containers, you acknowledge, understand, and consent to the Supplemental License Terms available on Docker hub:</span></span>

- <span data-ttu-id="87d1b-121">[Window Server Core][Window Server Core]</span><span class="sxs-lookup"><span data-stu-id="87d1b-121">[Window Server Core][Window Server Core]</span></span>
- <span data-ttu-id="87d1b-122">[Nano Server][Nano Server]</span><span class="sxs-lookup"><span data-stu-id="87d1b-122">[Nano Server][Nano Server]</span></span>

### <a name="telemetry"></a><span data-ttu-id="87d1b-123">遙測</span><span class="sxs-lookup"><span data-stu-id="87d1b-123">Telemetry</span></span>

<span data-ttu-id="87d1b-124">根據預設，PowerShell 會收集不具個人識別資訊的有限遙測，以協助開發未來的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="87d1b-124">By default, PowerShell collects limited telemetry without personally identifiable information to help aid development of future versions of PowerShell.</span></span> <span data-ttu-id="87d1b-125">若要選擇退出傳送遙測，請在從安裝位置啟動 PowerShell 之前建立名為 `POWERSHELL_TELEMETRY_OPTOUT` 的環境變數，並將其設定為 `1` 的值。</span><span class="sxs-lookup"><span data-stu-id="87d1b-125">To opt-out of sending telemetry, create an environment variable called `POWERSHELL_TELEMETRY_OPTOUT` set to a value of `1` before starting PowerShell from the installed location.</span></span> <span data-ttu-id="87d1b-126">我們收集的遙測是以 [Microsoft 隱私權聲明][privacy]為基礎。</span><span class="sxs-lookup"><span data-stu-id="87d1b-126">The telemetry we collect falls under the [Microsoft Privacy Statement][privacy].</span></span>

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[MIT 授權]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
