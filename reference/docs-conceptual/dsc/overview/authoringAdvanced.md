---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 了解 DSC 在 CI/CD 管線中的角色
description: 此文章描述可用於在 CI/CD 管線中結合設定與資源的方法類型。
ms.openlocfilehash: 8d06b86724eb25e657687e6518c01bb29d984264
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647033"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a><span data-ttu-id="90c43-104">了解 DSC 在 CI/CD 管線中的角色</span><span class="sxs-lookup"><span data-stu-id="90c43-104">Understanding DSC's role in a CI/CD pipeline</span></span>

<span data-ttu-id="90c43-105">本文描述可用於結合設定和資源的方法類型。</span><span class="sxs-lookup"><span data-stu-id="90c43-105">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="90c43-106">每個案例的目標都相同，那就是在想要使用多項設定來達到伺服器部署結束狀態時降低其複雜度。</span><span class="sxs-lookup"><span data-stu-id="90c43-106">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span> <span data-ttu-id="90c43-107">其中一個例子是多個小組參與伺服器部署的結果；例如，應用程式擁有者維護應用程式狀態，而核心小組將變更發行至安全性基準。</span><span class="sxs-lookup"><span data-stu-id="90c43-107">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span> <span data-ttu-id="90c43-108">以下詳細說明每種方法的細微差異，包括優點和風險。</span><span class="sxs-lookup"><span data-stu-id="90c43-108">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![CI/CD 管線的處理流程](media/authoringAdvanced/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="90c43-110">共同撰寫技術類型</span><span class="sxs-lookup"><span data-stu-id="90c43-110">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="90c43-111">本機設定管理員內建兩個解決方案，可實現此概念：</span><span class="sxs-lookup"><span data-stu-id="90c43-111">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

|        <span data-ttu-id="90c43-112">概念</span><span class="sxs-lookup"><span data-stu-id="90c43-112">Concept</span></span>         |                    <span data-ttu-id="90c43-113">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="90c43-113">Detailed Information</span></span>                     |
| ---------------------- | ----------------------------------------------------------- |
| <span data-ttu-id="90c43-114">部分設定</span><span class="sxs-lookup"><span data-stu-id="90c43-114">Partial Configurations</span></span> | [<span data-ttu-id="90c43-115">文件集</span><span class="sxs-lookup"><span data-stu-id="90c43-115">Documentation</span></span>](../pull-server/partialConfigs.md)           |
| <span data-ttu-id="90c43-116">複合資源</span><span class="sxs-lookup"><span data-stu-id="90c43-116">Composite Resources</span></span>    | [<span data-ttu-id="90c43-117">文件集</span><span class="sxs-lookup"><span data-stu-id="90c43-117">Documentation</span></span>](../resources/authoringResourceComposite.md) |

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="90c43-118">了解每種方法的影響</span><span class="sxs-lookup"><span data-stu-id="90c43-118">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="90c43-119">任一解決方案都可用來管理伺服器部署的結果。</span><span class="sxs-lookup"><span data-stu-id="90c43-119">Either of these solutions can be used to manage the outcome of a server deployment.</span></span> <span data-ttu-id="90c43-120">不過，使用每種方法的影響會有明顯差異。</span><span class="sxs-lookup"><span data-stu-id="90c43-120">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="90c43-121">部分設定</span><span class="sxs-lookup"><span data-stu-id="90c43-121">Partial Configurations</span></span>

<span data-ttu-id="90c43-122">使用部分設定時，本機設定管理員會設定為獨立管理多項設定。</span><span class="sxs-lookup"><span data-stu-id="90c43-122">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span> <span data-ttu-id="90c43-123">這些設定會獨立編譯，再指派給節點。</span><span class="sxs-lookup"><span data-stu-id="90c43-123">Configurations are compiled independently and then assigned to the node.</span></span> <span data-ttu-id="90c43-124">這需要使用每項設定的名稱事先設定 LCM。</span><span class="sxs-lookup"><span data-stu-id="90c43-124">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![部分組態圖](media/authoringAdvanced/PartialConfiguration.jpg)

<span data-ttu-id="90c43-126">部分設定提供兩個 (含) 以上的小組對伺服器設定的完整控制權，通常沒有通訊或共同作業優點。</span><span class="sxs-lookup"><span data-stu-id="90c43-126">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="90c43-127">客戶反應這可能會導致資源衝突、意外覆寫，最終失去資產的真正設定控制權。</span><span class="sxs-lookup"><span data-stu-id="90c43-127">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="90c43-128">此外，客戶也反應使用此模型時，每個控制小組設定變更不太可能透過發行管線完全測試，而導致在生產環境中有非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="90c43-128">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="90c43-129">**請務必使用單一管線來評估發行至伺服器的所有變更。**</span><span class="sxs-lookup"><span data-stu-id="90c43-129">**It is critical that a single pipeline be used to evaluate all changes released to servers.**</span></span>

<span data-ttu-id="90c43-130">在下圖中，小組 B 將其部分設定發行至小組 A。小組 A 接著對已同時套用兩項設定的伺服器執行其測試。</span><span class="sxs-lookup"><span data-stu-id="90c43-130">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span> <span data-ttu-id="90c43-131">在此模型中，只有一個授權單位有權在生產環境中進行變更。</span><span class="sxs-lookup"><span data-stu-id="90c43-131">In this model, only one authority has permission to make changes in production.</span></span>

![部分單一管線圖](media/authoringAdvanced/PartialSinglePipeline.jpg)

<span data-ttu-id="90c43-133">當小組 B 需要變更時，他們應該對小組 A 的原始檔控制環境提交提取要求。</span><span class="sxs-lookup"><span data-stu-id="90c43-133">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span> <span data-ttu-id="90c43-134">小組 A 會接著使用測試自動化檢閱變更，並在確認變更不會在伺服器所裝載的應用程式或服務中造成錯誤時將它發行至生產環境。</span><span class="sxs-lookup"><span data-stu-id="90c43-134">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="90c43-135">複合資源</span><span class="sxs-lookup"><span data-stu-id="90c43-135">Composite Resources</span></span>

<span data-ttu-id="90c43-136">複合資源只是封裝成資源的 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="90c43-136">A composite resource is simply a DSC Configuration packaged as a resource.</span></span> <span data-ttu-id="90c43-137">設定 LCM 接受複合資源沒有特殊需求。</span><span class="sxs-lookup"><span data-stu-id="90c43-137">There are no special requirements for configuring LCM to accept composite resources.</span></span> <span data-ttu-id="90c43-138">這些資源會在新設定中使用，而且每次編譯都會產生一個 MOF 檔案。</span><span class="sxs-lookup"><span data-stu-id="90c43-138">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![複合資源圖](media/authoringAdvanced/CompositeResource.jpg)

<span data-ttu-id="90c43-140">複合資源有兩個常見的案例。</span><span class="sxs-lookup"><span data-stu-id="90c43-140">There are two common scenarios for composite resources.</span></span> <span data-ttu-id="90c43-141">第一個是降低複雜度及提取獨特概念。</span><span class="sxs-lookup"><span data-stu-id="90c43-141">The first is to reduce complexity and abstract unique concepts.</span></span> <span data-ttu-id="90c43-142">第二個是允許封裝基準，讓應用程式小組在所有測試皆成功之後，透過其發行管線安全地部署到生產環境。</span><span class="sxs-lookup"><span data-stu-id="90c43-142">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = "Present"
    Path = "c:\inetpub\file1.zip"
    Source = "http://uri/file1.zip"
  }
  Service A
  {
    Ensure = "Present"
    Name = "ServiceA"
    Status = "Running"
  }
  SecurityBaseline Settings
  {
    Ensure = "Present"
    Datacenter = "NorthAmerica"
  }
}
```

<span data-ttu-id="90c43-143">複合資源使用管線來促進撰寫和共同作業，並同時讓運作更臻成熟。</span><span class="sxs-lookup"><span data-stu-id="90c43-143">Composite resources promote both composition and collaboration using a pipeline while building operational maturity.</span></span>

<span data-ttu-id="90c43-144">您可能已在使用複合資源而不自知。</span><span class="sxs-lookup"><span data-stu-id="90c43-144">You might be already using composite resources without realizing it.</span></span> <span data-ttu-id="90c43-145">**ServiceSet** 即為一例。</span><span class="sxs-lookup"><span data-stu-id="90c43-145">An example is **ServiceSet**.</span></span>
<span data-ttu-id="90c43-146">此資源可管理多個 Windows 服務的狀態，而不需要個別列出。</span><span class="sxs-lookup"><span data-stu-id="90c43-146">This resource manages the state of multiple Windows Services without listing them individually.</span></span> <span data-ttu-id="90c43-147">Name 屬性接受字串陣列提供每項服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="90c43-147">The Name property accepts an array of strings to provide the name of each service.</span></span> <span data-ttu-id="90c43-148">編譯設定之後，針對傳遞至 ServiceSet 的每個名稱，MOF 會包含其唯一的 [服務] 區段。</span><span class="sxs-lookup"><span data-stu-id="90c43-148">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="90c43-149">組織可能會有應安裝在每一部伺服器上的「代理程式」或「中介軟體」。</span><span class="sxs-lookup"><span data-stu-id="90c43-149">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span> <span data-ttu-id="90c43-150">複合資源是管理任何這類工具和公用程式相依性、安裝程式和設定的最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="90c43-150">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="90c43-151">跨多部伺服器解決方案的負責人和小組可撰寫含有其需求的設定。</span><span class="sxs-lookup"><span data-stu-id="90c43-151">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span> <span data-ttu-id="90c43-152">接下來，使用複合資源文件中提供的指示，將設定封裝成複合資源。</span><span class="sxs-lookup"><span data-stu-id="90c43-152">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span> <span data-ttu-id="90c43-153">最後，新的複合資源應發佈至檔案共用或 NuGet 摘要等位置，以供應用程式小組在其設定中取用。</span><span class="sxs-lookup"><span data-stu-id="90c43-153">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="90c43-154">每次小組發行新版本，都會將其複合資源模組資訊清單中的版本號碼遞增。</span><span class="sxs-lookup"><span data-stu-id="90c43-154">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span> <span data-ttu-id="90c43-155">應用程式小組會將為管理應用程式相依性所撰寫的複合資源包含在設定中。</span><span class="sxs-lookup"><span data-stu-id="90c43-155">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span> <span data-ttu-id="90c43-156">當營運/安全性小組發行其資源的新版本時，他們會通知應用程式小組有這項新變更。</span><span class="sxs-lookup"><span data-stu-id="90c43-156">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="90c43-157">如果只變更基準，應用程式小組可能會觸發發行至生產環境。</span><span class="sxs-lookup"><span data-stu-id="90c43-157">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="90c43-158">不過，這讓他們有機會在發生服務中斷風險之前評估這對應用程式的影響。</span><span class="sxs-lookup"><span data-stu-id="90c43-158">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

> [!NOTE]
> <span data-ttu-id="90c43-159">關於使用複合資源的意見反應包括了對於進行變更需要編譯和發行新 MOF 的批評。</span><span class="sxs-lookup"><span data-stu-id="90c43-159">Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span> <span data-ttu-id="90c43-160">這是原廠設定。</span><span class="sxs-lookup"><span data-stu-id="90c43-160">This is by design.</span></span> <span data-ttu-id="90c43-161">每個新設定版本都應該包含每個資源特定版本的靜態參考，而且應該經過測試驗證，再到達生產伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="90c43-161">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span> <span data-ttu-id="90c43-162">測試和發行原始檔控制中變更的程序會建立安全的環境，以少量但頻繁的批次來發行變更。</span><span class="sxs-lookup"><span data-stu-id="90c43-162">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="90c43-163">如需使用發行管線管理核心基礎結構的詳細資訊，請參閱技術白皮書：[發行管線模型](../further-reading/whitepapers.md)。</span><span class="sxs-lookup"><span data-stu-id="90c43-163">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
