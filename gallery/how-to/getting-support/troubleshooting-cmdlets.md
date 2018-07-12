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
# <a name="troubleshooting-cmdlets"></a>疑難排解 Cmdlet

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>如何解決「警告：無法下載套件『您的封裝名稱』」問題

當 `Install-Module` 或 `Update-Module` 有時在某些電腦上失敗時即會回報此問題。
根據我們的調查，這和網路連線有關。
我們近期更新了 NuGet 套件，使其能夠確實下載封裝。
您可以遵循下方指示安裝 NuGet 提供者的最新組建，然後安裝或更新您的模組。
以下使用 'Azure' 模組為例。

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```