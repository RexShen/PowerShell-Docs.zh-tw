---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: Windows PowerShell 預期狀態設定概觀
description: DSC 是 PowerShell 中的管理平台，可讓您以程式碼形式的設定來管理 IT 和開發基礎結構。
ms.openlocfilehash: 4170603ea2733edb662a7ae32653676496cf7b5c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650915"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="d6e07-104">Windows PowerShell 預期狀態設定概觀</span><span class="sxs-lookup"><span data-stu-id="d6e07-104">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="d6e07-105">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d6e07-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d6e07-106">DSC 是 PowerShell 中的管理平台，可讓您以程式碼形式的設定來管理 IT 和開發基礎結構。</span><span class="sxs-lookup"><span data-stu-id="d6e07-106">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="d6e07-107">如需使用 DSC 的商務優點概觀，請參閱[適合決策者的預期狀態設定概觀](decisionMaker.md)。</span><span class="sxs-lookup"><span data-stu-id="d6e07-107">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="d6e07-108">如需使用 DSC 的工程優點概觀，請參閱[適合工程師的預期狀態設定概觀](DscForEngineers.md)。</span><span class="sxs-lookup"><span data-stu-id="d6e07-108">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="d6e07-109">若要快速開始使用 DSC，請參閱 [DSC 快速入門](../quickstarts/website-quickstart.md)。</span><span class="sxs-lookup"><span data-stu-id="d6e07-109">To start using DSC quickly, see [DSC quick start](../quickstarts/website-quickstart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="d6e07-110">重要概念</span><span class="sxs-lookup"><span data-stu-id="d6e07-110">Key Concepts</span></span>

<span data-ttu-id="d6e07-111">DSC 是用於設定、部署和管理系統的宣告式平台。</span><span class="sxs-lookup"><span data-stu-id="d6e07-111">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="d6e07-112">它包含三個主要元件：</span><span class="sxs-lookup"><span data-stu-id="d6e07-112">It consists of three primary components:</span></span>

- <span data-ttu-id="d6e07-113">[設定](../configurations/configurations.md) 是宣告式 PowerShell 指令碼，會定義和設定資源的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6e07-113">[Configurations](../configurations/configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span> <span data-ttu-id="d6e07-114">在執行設定時，DSC (及設定所呼叫的資源) 將只會「實現目標狀態」，確保系統存在於設定所配置的狀態。</span><span class="sxs-lookup"><span data-stu-id="d6e07-114">Upon running the configuration, DSC (and the resources being called by the configuration) will simply "make it so", ensuring that the system exists in the state laid out by the configuration.</span></span> <span data-ttu-id="d6e07-115">DSC 設定也是等冪：本機設定管理員 (LCM) 仍可確定電腦依據設定中宣告的任何狀態所設定。</span><span class="sxs-lookup"><span data-stu-id="d6e07-115">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="d6e07-116">[資源](../resources/resources.md)是 DSC「實現目標狀態」的方式。</span><span class="sxs-lookup"><span data-stu-id="d6e07-116">[Resources](../resources/resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="d6e07-117">它們包含的程式碼可使設定的目標進入並保持在指定狀態。</span><span class="sxs-lookup"><span data-stu-id="d6e07-117">They contain the code that put and keep the target of a configuration in the specified state.</span></span> <span data-ttu-id="d6e07-118">資源位於 PowerShell 模組，且可以被撰寫以針對檔案或 Windows 處理序等一般項目建立模型，或是針對 IIS 伺服器或 Azure 中執行的 VM 等特定項目建立模型。</span><span class="sxs-lookup"><span data-stu-id="d6e07-118">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="d6e07-119">[本機設定管理員 (LCM)](../managing-nodes/metaConfig.md) 是 DSC 用於協助資源和設定之間互動的引擎。</span><span class="sxs-lookup"><span data-stu-id="d6e07-119">The [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span> <span data-ttu-id="d6e07-120">LCM 使用資源所實作的控制流程，定期輪詢系統，以確保能維持設定所定義的狀態。</span><span class="sxs-lookup"><span data-stu-id="d6e07-120">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span> <span data-ttu-id="d6e07-121">如果系統未符合狀態，LCM 會呼叫資源內的程式碼，以根據設定來「實現目標狀態」。</span><span class="sxs-lookup"><span data-stu-id="d6e07-121">If the system is out of state, the LCM makes calls to the code in resources to "make it so" according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6e07-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6e07-122">See Also</span></span>

- [<span data-ttu-id="d6e07-123">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="d6e07-123">DSC Configurations</span></span>](../configurations/configurations.md)
- [<span data-ttu-id="d6e07-124">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="d6e07-124">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="d6e07-125">設定本機設定管理員</span><span class="sxs-lookup"><span data-stu-id="d6e07-125">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
