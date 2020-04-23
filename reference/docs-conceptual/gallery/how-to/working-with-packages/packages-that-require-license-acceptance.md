---
ms.date: 06/12/2017
contributor: Farehar
keywords: gallery,powershell,psgallery,資源庫
title: 必須接受授權
ms.openlocfilehash: 4b293ea693062cf9717fa4ca913c3eb9abaf7014
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278635"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="ae443-103">必須接受授權</span><span class="sxs-lookup"><span data-stu-id="ae443-103">Require license acceptance</span></span>

<span data-ttu-id="ae443-104">「必須接受授權」的文字會顯示在需要接受授權之模組的項目詳細資料頁面上。</span><span class="sxs-lookup"><span data-stu-id="ae443-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="ae443-105">模組的授權可以透過按一下 [檢視 License.txt] 連結來檢視。</span><span class="sxs-lookup"><span data-stu-id="ae443-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![必須接受授權](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

<span data-ttu-id="ae443-107">系統會在透過 PowerShellGet 安裝、儲存或更新模組，或部署至 Azure 自動化時，提示使用者接受授權。</span><span class="sxs-lookup"><span data-stu-id="ae443-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="ae443-108">部署至 Azure 自動化上的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="ae443-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="ae443-109">若部署至 Azure 自動化的模組必須接受授權，入口網站 UI 將會顯示免責聲明：「此模組需要您接受授權。</span><span class="sxs-lookup"><span data-stu-id="ae443-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="ae443-110">按一下 [確定] 即表示您接受授權條款。」</span><span class="sxs-lookup"><span data-stu-id="ae443-110">By clicking OK, you are accepting license terms.'</span></span>

![部署至 Azure 自動化必須接受授權](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="ae443-112">其他詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ae443-112">More details</span></span>

<span data-ttu-id="ae443-113">[必須接受 PowerShellGet 中的授權](../../concepts/module-license-acceptance.md)
[Azure 自動化網站](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="ae443-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
