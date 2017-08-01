---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: ccb39f44e8d11f1e2a912da0c4f18b700e836c91
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>如何解決「警告：無法下載封裝『您的封裝名稱』」問題？




有人回報 Install-Module 或 Update-Module 有時候在某些機器上會失敗。
根據我們的調查，這和網路連線有關。
我們近期更新了 NuGet 套件，使其能夠確實下載封裝。
您可以遵循下方指示安裝 NuGet 提供者的最新組建，然後安裝或更新您的模組。
以下使用 'Azure' 模組為例。

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

