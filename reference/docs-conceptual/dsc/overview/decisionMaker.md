---
ms.date: 10/11/2019
keywords: dsc,powershell,設定,安裝
title: 適合決策者的預期狀態設定概觀
ms.openlocfilehash: b6d483d105c2d3b9be7215be36397d452338c7f1
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737248"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a><span data-ttu-id="2928c-103">適用於決策者的預期狀態設定概觀</span><span class="sxs-lookup"><span data-stu-id="2928c-103">Desired State Configuration overview for decision makers</span></span>

<span data-ttu-id="2928c-104">此文件說明使用 PowerShell 預期狀態設定 (DSC) 的商業優勢，它不是技術指南。</span><span class="sxs-lookup"><span data-stu-id="2928c-104">This document describes the business benefits of using PowerShell Desired State Configuration (DSC), and isn't a technical guide.</span></span>

## <a name="what-is-dsc"></a><span data-ttu-id="2928c-105">什麼是 DSC？</span><span class="sxs-lookup"><span data-stu-id="2928c-105">What Is DSC?</span></span>

<span data-ttu-id="2928c-106">PowerShell DSC 是 Windows 內建的開放式標準組態管理平台。</span><span class="sxs-lookup"><span data-stu-id="2928c-106">PowerShell DSC is a configuration management platform built into Windows that is based on open standards.</span></span> <span data-ttu-id="2928c-107">DSC 的彈性足以因應部署生命週期 (開發、測試、生產階段前、生產環境) 各階段穩定且一致的運作，相應放大時亦然。</span><span class="sxs-lookup"><span data-stu-id="2928c-107">DSC is flexible enough to function reliably and consistently in each stage of the deployment lifecycle (development, test, pre-production, production), and during scale-out.</span></span>

<span data-ttu-id="2928c-108">DSC 的中心概念是[設定](../configurations/configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="2928c-108">DSC centers around [configurations](../configurations/configurations.md).</span></span> <span data-ttu-id="2928c-109">設定是 PowerShell 指令碼，描述由特定特性的電腦 (或稱「節點」) 組成的環境。</span><span class="sxs-lookup"><span data-stu-id="2928c-109">A configuration is PowerShell script that describes an environment made up of computers, or nodes, with specific characteristics.</span></span> <span data-ttu-id="2928c-110">這些特性可以簡單到像是確保已啟用特定的 Windows 功能，也可以複雜到像是部署 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="2928c-110">These characteristics can be as simple as ensuring a specific Windows feature is enabled or as complex as deploying SharePoint.</span></span>

<span data-ttu-id="2928c-111">DSC 內建監視和報告功能。</span><span class="sxs-lookup"><span data-stu-id="2928c-111">DSC has monitoring and reporting built-in.</span></span> <span data-ttu-id="2928c-112">如果系統不再相容，DSC 會引發警示，採取動作更正系統。</span><span class="sxs-lookup"><span data-stu-id="2928c-112">If a system is no longer compliant, DSC can raise an alert and act to correct the system.</span></span>

## <a name="benefits-of-using-dsc"></a><span data-ttu-id="2928c-113">使用 DSC 的優點</span><span class="sxs-lookup"><span data-stu-id="2928c-113">Benefits of using DSC</span></span>

<span data-ttu-id="2928c-114">設定的設計可簡化讀取、儲存及更新設定的方式。</span><span class="sxs-lookup"><span data-stu-id="2928c-114">The configuration's design simplifies how they're read, stored, and updated.</span></span> <span data-ttu-id="2928c-115">設定會宣告目標裝置的狀態，不需要撰寫如何讓裝置進入該狀態的指示。</span><span class="sxs-lookup"><span data-stu-id="2928c-115">Configurations declare the state of target devices, rather than writing instructions for how to place devices in that state.</span></span> <span data-ttu-id="2928c-116">這些因素可降低透過 DSC 學習、採用及維護設定的成本。</span><span class="sxs-lookup"><span data-stu-id="2928c-116">These factors reduce the costs to learn, adopt, implement, and maintain configuration through DSC.</span></span>

<span data-ttu-id="2928c-117">建立設定即表示，已在單一位置將複雜的部署步驟擷取為**單一事實來源**。</span><span class="sxs-lookup"><span data-stu-id="2928c-117">Creating configurations means that complex deployment steps are captured as a **single source of truth** in a single location.</span></span> <span data-ttu-id="2928c-118">設定讓特定電腦集合的重複部署更不容易出錯。</span><span class="sxs-lookup"><span data-stu-id="2928c-118">Configurations make repeated deployments of a specific set of machines less error-prone.</span></span> <span data-ttu-id="2928c-119">此外，部署更快速且更可靠，藉此縮短複雜部署的完成時間。</span><span class="sxs-lookup"><span data-stu-id="2928c-119">And, deployments are faster and more reliable, which enables a quick turnaround on complex deployments.</span></span>

<span data-ttu-id="2928c-120">設定也可以透過 [PowerShell 資源庫](https://powershellgallery.com)共用。</span><span class="sxs-lookup"><span data-stu-id="2928c-120">Configurations are shareable via the [PowerShell Gallery](https://powershellgallery.com).</span></span> <span data-ttu-id="2928c-121">您需要完成的工作可能已有常見案例和最佳做法。</span><span class="sxs-lookup"><span data-stu-id="2928c-121">It's possible that common scenarios and best practices might already exist for the work you need to do.</span></span>

## <a name="dsc-and-devops"></a><span data-ttu-id="2928c-122">DSC 與 DevOps</span><span class="sxs-lookup"><span data-stu-id="2928c-122">DSC and DevOps</span></span>

<span data-ttu-id="2928c-123">DSC 在設計時即已考慮到 [DevOps](/archive/blogs/ashleymcglone/devops-for-n00bs-ie-windows-people-like-me) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="2928c-123">DSC was designed with [DevOps](/archive/blogs/ashleymcglone/devops-for-n00bs-ie-windows-people-like-me) in mind.</span></span> <span data-ttu-id="2928c-124">它是人員、程序與工具的組合，可允許快速部署與反覆開發週期，為內部或外部的終端使用者創造價值。</span><span class="sxs-lookup"><span data-stu-id="2928c-124">A combination of people, processes, and tools that allow for rapid deployment and iteration focused on delivering value to end users whether internal or external.</span></span> <span data-ttu-id="2928c-125">定義環境的單一設定表示開發人員可以將其需求編碼到設定中，並將該設定簽入原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="2928c-125">A single configuration that defines an environment means that developers can encode their requirements into a configuration and check that configuration into source control.</span></span> <span data-ttu-id="2928c-126">作業小組接著可以部署程式碼，而不需要執行容易出錯的人工處理。</span><span class="sxs-lookup"><span data-stu-id="2928c-126">Operations teams can then deploy code without going through error-prone manual processes.</span></span>

<span data-ttu-id="2928c-127">設定是[資料驅動](../configurations/configData.md)的。</span><span class="sxs-lookup"><span data-stu-id="2928c-127">Configurations are [data-driven](../configurations/configData.md).</span></span> <span data-ttu-id="2928c-128">已定義的資料可讓作業小組更容易識別及變更環境，而不必開發人員介入。</span><span class="sxs-lookup"><span data-stu-id="2928c-128">The defined data makes it easier for operations to identify and change environments without developer intervention.</span></span>

## <a name="dsc-on-premises-and-off-premises"></a><span data-ttu-id="2928c-129">DSC 內部部署與外部部署</span><span class="sxs-lookup"><span data-stu-id="2928c-129">DSC on-premises and off-premises</span></span>

<span data-ttu-id="2928c-130">DSC 可管理內部部署及外部部署的部署。</span><span class="sxs-lookup"><span data-stu-id="2928c-130">DSC can manage on-premises and off-premises deployments.</span></span> <span data-ttu-id="2928c-131">針對內部部署解決方案，DSC 具有[提取伺服器](../pull-server/pullServer.md)，可用來集中管理電腦並回報其狀態。</span><span class="sxs-lookup"><span data-stu-id="2928c-131">For on-premises solutions, DSC has a [Pull Server](../pull-server/pullServer.md) that's used to centralize management of machines and report on their status.</span></span> <span data-ttu-id="2928c-132">針對外部部署雲端解決方案，DSC 可在 Windows 可用的地方使用。</span><span class="sxs-lookup"><span data-stu-id="2928c-132">For off-premises cloud solutions, DSC is usable any place Windows is usable.</span></span>
<span data-ttu-id="2928c-133">Azure 提供以 DSC 為基礎建置的特定供應項目，例如 [Azure 自動化](https://azure.microsoft.com/en-us/documentation/services/automation/)，這可讓您集中管理 DSC 回報功能。</span><span class="sxs-lookup"><span data-stu-id="2928c-133">There are specific offerings from Azure built on DSC, such as [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), that centralizes DSC reporting.</span></span>

## <a name="dsc-and-compatibility"></a><span data-ttu-id="2928c-134">DSC 和相容性</span><span class="sxs-lookup"><span data-stu-id="2928c-134">DSC and compatibility</span></span>

<span data-ttu-id="2928c-135">DSC 是在 Windows Server 2012 R2 引進，卻是透過 Windows Management Framework (WMF) 供較低的作業系統使用。</span><span class="sxs-lookup"><span data-stu-id="2928c-135">DSC was introduced in Windows Server 2012 R2, but it's available for down-level operating systems via the Windows Management Framework (WMF).</span></span> <span data-ttu-id="2928c-136">如需有關 WMF 的詳細資訊，請參閱 [Windows Management Framework](/powershell/scripting/wmf/overview) 套件。</span><span class="sxs-lookup"><span data-stu-id="2928c-136">For more information about WMF, see [Windows Management Framework](/powershell/scripting/wmf/overview).</span></span>

<span data-ttu-id="2928c-137">DSC 也可以用來管理 Linux。</span><span class="sxs-lookup"><span data-stu-id="2928c-137">DSC can be used to manage Linux.</span></span> <span data-ttu-id="2928c-138">如需詳細資訊，請參閱[開始使用 DSC for Linux](../getting-started/lnxGettingStarted.md)。</span><span class="sxs-lookup"><span data-stu-id="2928c-138">For more information, see [Getting Started with DSC for Linux](../getting-started/lnxGettingStarted.md).</span></span>
