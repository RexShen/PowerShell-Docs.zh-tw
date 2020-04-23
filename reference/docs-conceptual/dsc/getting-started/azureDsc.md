---
ms.date: 03/15/2018
keywords: dsc,powershell,設定,安裝
title: 使用 Microsoft Azure 的 DSC
ms.openlocfilehash: 6d71b69eea78e775a3e5aaac64bccfa10092b8e6
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870824"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="3d5df-103">使用 Microsoft Azure 的 DSC</span><span class="sxs-lookup"><span data-stu-id="3d5df-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="3d5df-104">Microsoft Azure 透過 [Azure 預期狀態設定延伸模組處理常式](/azure/virtual-machines/extensions/dsc-overview) 及透過 [Azure 自動化 DSC](/azure/automation/automation-dsc-overview) 支援預期狀態設定 (DSC)。</span><span class="sxs-lookup"><span data-stu-id="3d5df-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="3d5df-105">Azure 預期狀態設定延伸模組處理常式</span><span class="sxs-lookup"><span data-stu-id="3d5df-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="3d5df-106">Azure DSC 延伸模組允許 VM 裝載在 Microsoft Azure 上由 DSC 管理。</span><span class="sxs-lookup"><span data-stu-id="3d5df-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span> <span data-ttu-id="3d5df-107">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="3d5df-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="3d5df-108">Azure 預期狀態設定延伸模組處理常式</span><span class="sxs-lookup"><span data-stu-id="3d5df-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="3d5df-109">Azure Resource Manager 範本中的 Windows VMSS 與預期狀態設定</span><span class="sxs-lookup"><span data-stu-id="3d5df-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="3d5df-110">將認證傳遞至 Azure DSC 延伸模組處理常式</span><span class="sxs-lookup"><span data-stu-id="3d5df-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="3d5df-111">Azure Desired State Configuration 延伸模組歷程記錄</span><span class="sxs-lookup"><span data-stu-id="3d5df-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="3d5df-112">Azure 自動化 DSC</span><span class="sxs-lookup"><span data-stu-id="3d5df-112">Azure Automation DSC</span></span>

<span data-ttu-id="3d5df-113">[Azure 自動化服務](https://azure.microsoft.com/services/automation/) 可讓您從 Azure 內部管理 DSC 組態、資源及的受管理的節點。</span><span class="sxs-lookup"><span data-stu-id="3d5df-113">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="3d5df-114">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="3d5df-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="3d5df-115">Azure 自動化 DSC</span><span class="sxs-lookup"><span data-stu-id="3d5df-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="3d5df-116">開始使用 Azure 自動化 DSC</span><span class="sxs-lookup"><span data-stu-id="3d5df-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="3d5df-117">將機器上架交由 Azure 自動化 DSC 管理</span><span class="sxs-lookup"><span data-stu-id="3d5df-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)