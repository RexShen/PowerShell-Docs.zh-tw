---
ms.date: 06/12/2017
contributor: Farehar
keywords: gallery,powershell,psgallery,資源庫
title: 必須接受授權
ms.openlocfilehash: 69787cdb12aa47223072551c9b68fc046573f022
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218394"
---
# <a name="require-license-acceptance"></a>必須接受授權

「必須接受授權」的文字會顯示在需要接受授權之模組的項目詳細資料頁面上。 模組的授權可以透過按一下 [檢視 License.txt] 連結來檢視。

![必須接受授權](../../Images/RequireLicenseAcceptance.png)

系統會在透過 PowerShellGet 安裝、儲存或更新模組，或部署至 Azure 自動化時，提示使用者接受授權。

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>部署至 Azure 自動化上的必須接受授權

若部署至 Azure 自動化的模組必須接受授權，入口網站 UI 將會顯示免責聲明：「此模組需要您接受授權。 按一下 [確定] 即表示您接受授權條款。」

![部署至 Azure 自動化必須接受授權](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>更多詳細資料

[必須接受 PowerShellGet 中的授權](../../concepts/module-license-acceptance.md)
[Azure 自動化網站](/azure/automation)