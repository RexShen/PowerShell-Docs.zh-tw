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
# <a name="troubleshooting-cmdlets"></a>疑難排解 Cmdlet

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>如何解決「警告：無法下載套件 '您的套件名稱'」問題

當 `Install-Module` 或 `Update-Module` 有時在某些電腦上失敗時即會回報此問題。 根據我們的調查，這和網路連線有關。 我們近期更新了 NuGet 套件，使其能夠確實下載封裝。 您可以遵循下方指示安裝 NuGet 提供者的最新組建，然後安裝或更新您的模組。 以下使用 'Azure' 模組為例。

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

## <a name="required-network-endpoints"></a>必要網路端點

Install 與 Update Cmdlet 需要網際網路存取權才能連線到由 PowerShell 資源庫使用的網路端點。 確定您的網路存取原則可讓您連線到下列端點。

- `psg-prod-eastus.azureedge.net` - CDN 主機名稱
- `az818661.vo.msecnd.net` - CDN 主機名稱
- `devopsgallerystorage.blob.core.windows.net` - 儲存體帳戶主機名稱
- `*.powershellgallery.com` - 網站
- `go.microsoft.com` - 重新導向服務

> [!NOTE]
> 當 PowerShell 資源庫服務發生中斷時，與 PowerShell 資源庫互動的 Cmdlet 可能會因未預期的錯誤而失敗。 若要查看 PowerShell 資源庫目前的狀態，請參閱 GitHub 上的 [PowerShell 資源庫狀態](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) \(英文\) 頁面。
