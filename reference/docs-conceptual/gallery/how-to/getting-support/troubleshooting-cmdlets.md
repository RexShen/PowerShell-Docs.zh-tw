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
