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
# <a name="troubleshooting-cmdlets"></a>疑難排解 Cmdlet

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>如何解決「警告：無法下載套件 '您的套件名稱'」問題

當 `Install-Module` 或 `Update-Module` 有時在某些電腦上失敗時即會回報此問題。 根據我們的調查，這和網路連線有關。 我們近期更新了 NuGet 套件，使其能夠確實下載封裝。 您可以遵循下方指示安裝 NuGet 提供者的最新組建，然後安裝或更新您的模組。 以下使用 'Azure' 模組為例。

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a>必要網路端點

Install 與 Update Cmdlet 需要網際網路存取權才能連線到由 PowerShell 資源庫使用的網路端點。 確定您的網路存取原則可讓您連線到下列端點。

- oneget.org
- go.microsoft.com
- az818661.vo.msecnd.net
- www.powershellgallery.com
- devopsgallerystorage.blob.core.windows.net
