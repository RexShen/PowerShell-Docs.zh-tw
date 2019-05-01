---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 適合決策者的預期狀態設定概觀
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079586"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a><span data-ttu-id="2bfa7-103">適合決策者的預期狀態設定概觀</span><span class="sxs-lookup"><span data-stu-id="2bfa7-103">Desired State Configuration Overview for Decision Makers</span></span>

<span data-ttu-id="2bfa7-104">本文件說明使用 Windows PowerShell Desired State Configuration (DSC) 的商務優勢。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-104">This document describes the business benefits of using Windows PowerShell Desired State Configuration (DSC).</span></span> <span data-ttu-id="2bfa7-105">這不是技術指南。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-105">It is not a technical guide.</span></span>

## <a name="what-is-desired-state-configuration"></a><span data-ttu-id="2bfa7-106">什麼是預期狀態設定？</span><span class="sxs-lookup"><span data-stu-id="2bfa7-106">What Is Desired State Configuration?</span></span>

<span data-ttu-id="2bfa7-107">PowerShell Desired State Configuration 是 Windows 內建的開放式標準設定管理平台。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-107">PowerShell Desired State Configuration is a configuration management platform built into Windows that is based on open standards.</span></span> <span data-ttu-id="2bfa7-108">DSC 的彈性足以因應部署生命週期 (開發、測試、生產階段前，生產環境) 各階段穩定且一致的運作，向外延展時亦然。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-108">DSC is flexible enough to function reliably and consistently in each stage of the deployment lifecycle (development, test, pre-production, production), as well as during scale-out.</span></span>

<span data-ttu-id="2bfa7-109">DSC 的中心概念是[設定](../configurations/configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-109">DSC centers around [configurations](../configurations/configurations.md).</span></span>
<span data-ttu-id="2bfa7-110">設定是容易讀取的文件，描述由特定特性的電腦 (「節點」) 組成的環境。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-110">A configuration is an easy-to-read document that describes an environment made up of computers ("nodes") with specific characteristics.</span></span>
<span data-ttu-id="2bfa7-111">這些特性可以簡單到像是確保已啟用特定的 Windows 功能，也可以複雜到像是部署 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-111">These characteristics can be as simple as ensuring a specific Windows feature is enabled or as complex as deploying SharePoint.</span></span>

<span data-ttu-id="2bfa7-112">DSC 也有內建的監視和報告。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-112">DSC also has monitoring and reporting built in.</span></span>
<span data-ttu-id="2bfa7-113">如果系統不再相容，DSC 會引發警示，採取動作更正系統。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-113">If a system is no longer compliant, DSC can raise an alert and act to correct the system.</span></span>

## <a name="benefits-of-using-desired-state-configuration"></a><span data-ttu-id="2bfa7-114">使用預期狀態設定的優勢</span><span class="sxs-lookup"><span data-stu-id="2bfa7-114">Benefits of Using Desired State Configuration</span></span>

<span data-ttu-id="2bfa7-115">設定應設計為易於讀取、儲存及更新。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-115">Configurations are designed to be easily read, stored, and updated.</span></span>
<span data-ttu-id="2bfa7-116">設定會宣告目標裝置應有的狀態，不需要撰寫如何成就裝置狀態的指示。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-116">Configurations declare the state target devices should be in, instead of writing instructions for how to put them in that state.</span></span>
<span data-ttu-id="2bfa7-117">這可讓您以更經濟的成本透過 DSC 了解、採用、實作和維護設定。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-117">This makes it much less costly to learn, adopt, implement, and maintain configuration through DSC.</span></span>

<span data-ttu-id="2bfa7-118">建立設定即表示，已在單一位置將複雜的部署步驟擷取為「單一事實來源」。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-118">Creating configurations means that complex deployment steps are captured as a "single source of truth" in a single location.</span></span>
<span data-ttu-id="2bfa7-119">這讓特定電腦集合的重複部署更不容易出錯。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-119">This makes repeated deployments of a specific set of machines much less error-prone.</span></span>
<span data-ttu-id="2bfa7-120">也因此可讓部署更快速且更可靠，藉此縮短複雜部署的完成時間。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-120">In turn, making deployments faster and more reliable which enables a quick turnaround on complex deployments.</span></span>

<span data-ttu-id="2bfa7-121">設定也可透過 [PowerShell 資源庫](https://powershellgallery.com)來分享，亦即對於要完成的工作，可能已經有共通案例與最佳做法。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-121">Configurations are also shareable via the [PowerShell Gallery](https://powershellgallery.com) meaning common scenarios and best practices might already exist for the work that needs to be done.</span></span>


## <a name="desired-state-configuration-and-devops"></a><span data-ttu-id="2bfa7-122">預期狀態設定和 DevOps</span><span class="sxs-lookup"><span data-stu-id="2bfa7-122">Desired State Configuration and DevOps</span></span>

<span data-ttu-id="2bfa7-123">DSC 的設計過程納入了 [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) 考量，是人員、流程和工具的組合，可允許快速建置與反覆開發週期，為內部或外部的終端使用者創造價值。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-123">DSC was designed with [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) in mind, a combination of people, processes, and tools that allow for rapid deployment and iteration focused on delivering value to end users whether internal or external.</span></span>
<span data-ttu-id="2bfa7-124">讓單一設定定義環境即表示，開發人員可以將需求編碼成設定、將該設定簽入原始檔控制，而維運小組可以輕鬆部署程式碼，不必進行可能會出錯的手動程序。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-124">Having a single configuration define an environment means that developers can encode their requirements into a configuration, check that configuration into source control, and operation teams can easily deploy code without having to go through error-prone manual processes.</span></span>

<span data-ttu-id="2bfa7-125">設定也[以資料為動力](../configurations/configData.md)，讓維運小組更容易識別及變更環境，而不必開發人員介入。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-125">Configurations are also [data-driven](../configurations/configData.md), which makes it easier for ops to identify and change environments without developer intervention.</span></span>

## <a name="desired-state-configuration-on-premises-and-off-premises"></a><span data-ttu-id="2bfa7-126">內部部署及外部部署的預期狀態設定</span><span class="sxs-lookup"><span data-stu-id="2bfa7-126">Desired State Configuration On-Premises and Off-Premises</span></span>
<span data-ttu-id="2bfa7-127">DSC 可以用來管理內部部署及外部部署的部署。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-127">DSC can be used to manage both on-premise and off-premise deployments.</span></span>
<span data-ttu-id="2bfa7-128">在內部部署解決方案方面，DSC 有[提取伺服器](../pull-server/pullServer.md)可集中管理電腦，並報告其狀態。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-128">For on-premise solutions, DSC has a [pull server](../pull-server/pullServer.md) that can be used to centralize management of machines and report on their status.</span></span>
<span data-ttu-id="2bfa7-129">在雲端解決方案方面，只要能夠使用 Windows 的地方都可以使用 DSC。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-129">For cloud solutions, DSC is usable wherever Windows is usable.</span></span>
<span data-ttu-id="2bfa7-130">建置在預期狀態設定之上的 Azure 也有特定供應項目，例如能集中 DSC 報告的 [Azure 自動化](https://azure.microsoft.com/en-us/documentation/services/automation/)。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-130">There are also specific offerings from Azure built on Desired State Configuration, such as [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), which centralizes reporting of DSC.</span></span>

## <a name="dsc-and-compatibility"></a><span data-ttu-id="2bfa7-131">DSC 和相容性</span><span class="sxs-lookup"><span data-stu-id="2bfa7-131">DSC and Compatibility</span></span>

<span data-ttu-id="2bfa7-132">DSC 雖是在 Windows Server 2012 R2 引進，卻是透過 Windows Management Framework (WMF) 套件供低階的作業系統使用。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-132">Although DSC was introduced in Windows Server 2012 R2, it is available for down-level operating systems via the Windows Management Framework (WMF) package.</span></span>
<span data-ttu-id="2bfa7-133">WMF 詳細資訊請參閱 [PowerShell 首頁](/powershell/)。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-133">More information about the WMF can be found on the [PowerShell homepage](/powershell/).</span></span>

<span data-ttu-id="2bfa7-134">DSC 也可用來管理 Linux。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-134">DSC can also be used to manage Linux.</span></span> <span data-ttu-id="2bfa7-135">如需詳細資訊，請參閱[開始使用 DSC for Linux](../getting-started/lnxGettingStarted.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfa7-135">For more information, see [Getting Started with DSC for Linux](../getting-started/lnxGettingStarted.md).</span></span>
