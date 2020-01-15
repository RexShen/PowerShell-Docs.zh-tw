---
ms.date: 03/15/2018
keywords: dsc,powershell,設定,安裝
title: 使用 Microsoft Azure 的 DSC
ms.openlocfilehash: 6d71b69eea78e775a3e5aaac64bccfa10092b8e6
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870824"
---
# <a name="using-dsc-on-microsoft-azure"></a>使用 Microsoft Azure 的 DSC

Microsoft Azure 透過 [Azure 預期狀態設定延伸模組處理常式](/azure/virtual-machines/extensions/dsc-overview) 及透過 [Azure 自動化 DSC](/azure/automation/automation-dsc-overview) 支援預期狀態設定 (DSC)。

## <a name="azure-desired-state-configuration-extension-handler"></a>Azure 預期狀態設定延伸模組處理常式

Azure DSC 延伸模組允許 VM 裝載在 Microsoft Azure 上由 DSC 管理。 如需詳細資訊，請參閱下列主題：

- [Azure 預期狀態設定延伸模組處理常式](/azure/virtual-machines/extensions/dsc-overview)
- [Azure Resource Manager 範本中的 Windows VMSS 與預期狀態設定](/azure/virtual-machines/extensions/dsc-template)
- [將認證傳遞至 Azure DSC 延伸模組處理常式](/azure/virtual-machines/extensions/dsc-credentials)
- [Azure Desired State Configuration 延伸模組歷程記錄](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>Azure 自動化 DSC

[Azure 自動化服務](https://azure.microsoft.com/services/automation/) 可讓您從 Azure 內部管理 DSC 組態、資源及的受管理的節點。 如需詳細資訊，請參閱下列主題：

- [Azure 自動化 DSC](/azure/automation/automation-dsc-overview)
- [開始使用 Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started)
- [將機器上架交由 Azure 自動化 DSC 管理](/azure/automation/automation-dsc-onboarding)