---
ms.date: 06/12/2017
title: 必須接受授權
description: 如何在項目詳細資料頁面上檢視套件授權
ms.openlocfilehash: 0d8a9ed671f7993726bc3fa41d11159b366e5a28
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662311"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="d32b3-103">必須接受授權</span><span class="sxs-lookup"><span data-stu-id="d32b3-103">Require license acceptance</span></span>

<span data-ttu-id="d32b3-104">「必須接受授權」的文字會顯示在需要接受授權之模組的項目詳細資料頁面上。</span><span class="sxs-lookup"><span data-stu-id="d32b3-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="d32b3-105">模組的授權可以透過按一下 [檢視 License.txt] 連結來檢視。</span><span class="sxs-lookup"><span data-stu-id="d32b3-105">License for module can be viewed by clicking on **View License.txt** link.</span></span>

![必須接受授權](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

<span data-ttu-id="d32b3-107">系統會在透過 PowerShellGet 安裝、儲存或更新模組，或部署至 Azure 自動化時，提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="d32b3-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="d32b3-108">部署至 Azure 自動化上的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="d32b3-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="d32b3-109">若部署至 Azure 自動化的模組必須接受授權，入口網站 UI 將會顯示免責聲明：「此模組需要您接受授權。</span><span class="sxs-lookup"><span data-stu-id="d32b3-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="d32b3-110">按一下 [確定] 即表示您接受授權條款。」</span><span class="sxs-lookup"><span data-stu-id="d32b3-110">By clicking OK, you are accepting license terms.'</span></span>

![部署至 Azure 自動化必須接受授權](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="d32b3-112">其他詳細資訊</span><span class="sxs-lookup"><span data-stu-id="d32b3-112">More details</span></span>

<span data-ttu-id="d32b3-113">[必須接受 PowerShellGet 中的授權](../../concepts/module-license-acceptance.md)
[Azure 自動化網站](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="d32b3-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
