---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 91f48fb43d7fb099e34ce5d3b3b632e3cb119d64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="68a96-103">部署至 Azure 自動化</span><span class="sxs-lookup"><span data-stu-id="68a96-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="68a96-104">項目詳細資料頁面上的 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕會將項目從 PowerShell Gallery 部署至 Azure 自動化。</span><span class="sxs-lookup"><span data-stu-id="68a96-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Deploy to Azure Automation (部署至 Azure 自動化) 按鈕](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="68a96-106">按一下時，會將您重新導向至使用 Azure 帳戶認證所登入的 Azure 管理入口網站。</span><span class="sxs-lookup"><span data-stu-id="68a96-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="68a96-107">如果項目包含相依性，則也會將所有相依性部署至 Azure 自動化。</span><span class="sxs-lookup"><span data-stu-id="68a96-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="68a96-108">警告︰如果相同的項目和版本已存在於您的自動化帳戶，則再次從 PowerShell Gallery 部署它將會覆寫自動化帳戶中的項目。</span><span class="sxs-lookup"><span data-stu-id="68a96-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="68a96-109">如果您部署模組，則它會出現在 [Azure 自動化] 的 [模組] 區段中。</span><span class="sxs-lookup"><span data-stu-id="68a96-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="68a96-110">如果您部署指令碼，則它會出現在 [Azure 自動化] 的 [Runbook] 區段中。</span><span class="sxs-lookup"><span data-stu-id="68a96-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="68a96-111">將 AzureAutomationNotSupported 標記新增至項目中繼資料，即可停用 [Deploy to Azure Automation] \(部署至 Azure 自動化) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="68a96-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="68a96-112">若要深入了解 Azure 自動化，請參閱 [Azure 自動化網站](http://azure.microsoft.com/en-us/services/automation/)。</span><span class="sxs-lookup"><span data-stu-id="68a96-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/en-us/services/automation/).</span></span>

