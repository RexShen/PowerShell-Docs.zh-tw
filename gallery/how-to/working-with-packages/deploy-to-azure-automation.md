---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 部署至 Azure 自動化
ms.openlocfilehash: dc382b1cf3ceaa787f54c555d01e6bd9ba70e680
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003699"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="e57f0-103">部署至 Azure 自動化</span><span class="sxs-lookup"><span data-stu-id="e57f0-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="e57f0-104">套件詳細資料頁面上的 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕，會將該套件從 PowerShell 資源庫部署至 Azure 自動化。</span><span class="sxs-lookup"><span data-stu-id="e57f0-104">The Deploy to Azure Automation button on the package details page will deploy the package from the PowerShell Gallery to Azure Automation.</span></span>

![Deploy to Azure Automation (部署至 Azure 自動化) 按鈕](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="e57f0-106">按一下時，會將您重新導向至使用 Azure 帳戶認證所登入的 Azure 管理入口網站。</span><span class="sxs-lookup"><span data-stu-id="e57f0-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="e57f0-107">如果套件包含相依性，則也會將所有相依性部署至 Azure 自動化。</span><span class="sxs-lookup"><span data-stu-id="e57f0-107">If the package includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="e57f0-108">如果您的自動化帳戶中已有相同的套件與版本，則再次從 PowerShell 資源庫進行部署將會覆寫自動化帳戶中的套件。</span><span class="sxs-lookup"><span data-stu-id="e57f0-108">If the same package and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the package in your Automation account.</span></span>

<span data-ttu-id="e57f0-109">如果您部署模組，則它會出現在 [Azure 自動化] 的 [模組] 區段中。</span><span class="sxs-lookup"><span data-stu-id="e57f0-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="e57f0-110">如果您部署指令碼，則它會出現在 [Azure 自動化] 的 [Runbook] 區段中。</span><span class="sxs-lookup"><span data-stu-id="e57f0-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="e57f0-111">若要停用 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕，請將 AzureAutomationNotSupported 標記新增至套件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e57f0-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the package metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="e57f0-112">部署至 Azure 自動化上的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="e57f0-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="e57f0-113">若部署至 Azure 自動化的模組必須接受授權，入口網站 UI 將會顯示免責聲明：「此模組需要您接受授權。</span><span class="sxs-lookup"><span data-stu-id="e57f0-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="e57f0-114">按一下 [確定] 即表示您接受授權條款。」</span><span class="sxs-lookup"><span data-stu-id="e57f0-114">By clicking OK, you are accepting license terms.'</span></span>

![部署至 Azure 自動化必須接受授權](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="e57f0-116">更多詳細資料</span><span class="sxs-lookup"><span data-stu-id="e57f0-116">More details</span></span>

- [<span data-ttu-id="e57f0-117">PowerShellGet 中的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="e57f0-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="e57f0-118">PowerShell 資源庫中的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="e57f0-118">Require License Acceptance in PowerShell Gallery</span></span>](packages-that-require-license-acceptance.md)
- [<span data-ttu-id="e57f0-119">Azure 自動化網站</span><span class="sxs-lookup"><span data-stu-id="e57f0-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)