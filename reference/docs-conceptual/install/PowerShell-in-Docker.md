---
title: 在 Docker 中使用 PowerShell
description: 如何使用預先安裝在 Docker 映像中的 PowerShell。
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: b16a31a04ca863ab55c7c9718b1a1a973e61ee46
ms.sourcegitcommit: f55da6dea4b58a2cd13c7be7c24c07341f177b71
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80646381"
---
# <a name="using-powershell-in-docker"></a>在 Docker 中使用 PowerShell

我們會以預先安裝 PowerShell 的方式發行 Docker 映像。 此文章會示範如何開始使用 Docker 容器中的 PowerShell。

## <a name="finding-available-images"></a>尋找可用的映像

發行的映像需要 Docker 17.05 或更新版本。 您也應該要能在沒有 `sudo` 或本機系統管理員權限的情況下執行 Docker。 請遵循 Docker 的官方[指示][install]以正確安裝 `docker`。

發行容器會衍生自官方發佈映像 (例如 `centos:7`)，然後安裝相依性，最後安裝 PowerShell 套件。

這些容器會存留在 [hub.docker.com/r/microsoft/powershell][docker-release] 中。

如需這些 Docker 映像的詳細資訊，請瀏覽 GitHub 上的 [PowerShell-Docker][PowerShell-Docker] 存放庫。

## <a name="using-powershell-in-a-container"></a>在容器中使用 PowerShell

下列步驟會示範下載映像並啟動互動式 PowerShell 工作階段所需的 Docker 命令。

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a>在不再需要映像時加以移除

下列命令用於在不再需要 Docker 映像時將其刪除。

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a>法律和授權

PowerShell 是根據 [MIT 授權][]進行授權。

### <a name="windows-docker-file-and-image-licenses"></a>Windows Docker 檔案與映像授權

一旦要求及使用適用於 Windows 容器的容器 OS 映像，即表示您確認、了解並同意可於 Docker Hub 上取得的補充授權條款：

- [Window Server Core][Window Server Core]
- [Nano Server][Nano Server]

### <a name="telemetry"></a>遙測

根據預設，PowerShell 會收集不具個人識別資訊的有限遙測，以協助開發未來的 PowerShell 版本。 若要選擇退出傳送遙測，請在從安裝位置啟動 PowerShell 之前建立名為 `POWERSHELL_TELEMETRY_OPTOUT` 的環境變數，並將其設定為 `1` 的值。 我們收集的遙測是以 [Microsoft 隱私權聲明][privacy]為基礎。

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[MIT 授權]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
