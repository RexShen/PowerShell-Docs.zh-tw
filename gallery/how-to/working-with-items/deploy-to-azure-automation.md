---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 部署至 Azure 自動化
ms.openlocfilehash: ced67809387a85e089259edf6b091d68e58ba6a7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="9628a-103">部署至 Azure 自動化</span><span class="sxs-lookup"><span data-stu-id="9628a-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="9628a-104">項目詳細資料頁面上的 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕會將項目從 PowerShell Gallery 部署至 Azure 自動化。</span><span class="sxs-lookup"><span data-stu-id="9628a-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Deploy to Azure Automation (部署至 Azure 自動化) 按鈕](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="9628a-106">按一下時，會將您重新導向至使用 Azure 帳戶認證所登入的 Azure 管理入口網站。</span><span class="sxs-lookup"><span data-stu-id="9628a-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="9628a-107">如果項目包含相依性，則也會將所有相依性部署至 Azure 自動化。</span><span class="sxs-lookup"><span data-stu-id="9628a-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="9628a-108">如果您的自動化帳戶中已有相同的項目與版本，則再次從 PowerShell 資源庫進行部署，將會覆寫您自動化帳戶中的項目。</span><span class="sxs-lookup"><span data-stu-id="9628a-108">If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="9628a-109">如果您部署模組，則它會出現在 [Azure 自動化] 的 [模組] 區段中。</span><span class="sxs-lookup"><span data-stu-id="9628a-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="9628a-110">如果您部署指令碼，則它會出現在 [Azure 自動化] 的 [Runbook] 區段中。</span><span class="sxs-lookup"><span data-stu-id="9628a-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="9628a-111">將 AzureAutomationNotSupported 標記新增至項目中繼資料，即可停用 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9628a-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="9628a-112">部署至 Azure 自動化上的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="9628a-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="9628a-113">若部署至 Azure 自動化的模組必須接受授權，入口網站 UI 將會顯示免責聲明：「此模組需要您接受授權。</span><span class="sxs-lookup"><span data-stu-id="9628a-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="9628a-114">按一下 [確定] 即表示您接受授權條款。」</span><span class="sxs-lookup"><span data-stu-id="9628a-114">By clicking OK, you are accepting license terms.'</span></span>

![部署至 Azure 自動化必須接受授權](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="9628a-116">更多詳細資料</span><span class="sxs-lookup"><span data-stu-id="9628a-116">More details</span></span>

- [<span data-ttu-id="9628a-117">PowerShellGet 中的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="9628a-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="9628a-118">PowerShell 資源庫中的必須接受授權</span><span class="sxs-lookup"><span data-stu-id="9628a-118">Require License Acceptance in PowerShell Gallery</span></span>](items-that-require-license-acceptance.md)
- [<span data-ttu-id="9628a-119">Azure 自動化網站</span><span class="sxs-lookup"><span data-stu-id="9628a-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
