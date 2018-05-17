---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: 部署至 Azure 自動化
ms.openlocfilehash: 1efdc289228d3a6962302d12ccf44143ce63a806
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="deploy-to-azure-automation"></a>部署至 Azure 自動化

項目詳細資料頁面上的 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕會將項目從 PowerShell Gallery 部署至 Azure 自動化。

![Deploy to Azure Automation (部署至 Azure 自動化) 按鈕](../../Images/DeployToAzureAutomationButton.png)

按一下時，會將您重新導向至使用 Azure 帳戶認證所登入的 Azure 管理入口網站。
如果項目包含相依性，則也會將所有相依性部署至 Azure 自動化。

> [!WARNING]
> 如果您的自動化帳戶中已有相同的項目與版本，則再次從 PowerShell 資源庫進行部署，將會覆寫您自動化帳戶中的項目。

如果您部署模組，則它會出現在 [Azure 自動化] 的 [模組] 區段中。  如果您部署指令碼，則它會出現在 [Azure 自動化] 的 [Runbook] 區段中。

將 AzureAutomationNotSupported 標記新增至項目中繼資料，即可停用 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕。

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>部署至 Azure 自動化上的必須接受授權

若部署至 Azure 自動化的模組必須接受授權，入口網站 UI 將會顯示免責聲明：「此模組需要您接受授權。 按一下 [確定] 即表示您接受授權條款。」

![部署至 Azure 自動化必須接受授權](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>更多詳細資料

- [PowerShellGet 中的必須接受授權](../../concepts/module-license-acceptance.md)
- [PowerShell 資源庫中的必須接受授權](items-that-require-license-acceptance.md)
- [Azure 自動化網站](http://azure.microsoft.com/services/automation/)
