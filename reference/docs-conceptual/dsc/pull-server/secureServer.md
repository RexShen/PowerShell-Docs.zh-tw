---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 提取伺服器最佳做法
ms.openlocfilehash: b2469984086a827b6b2a0fe84d1f326fc214ec28
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500689"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="b8f58-103">提取伺服器最佳做法</span><span class="sxs-lookup"><span data-stu-id="b8f58-103">Pull server best practices</span></span>

<span data-ttu-id="b8f58-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b8f58-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b8f58-105">提取伺服器 (Windows 功能「DSC 服務」  ) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。</span><span class="sxs-lookup"><span data-stu-id="b8f58-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="b8f58-106">建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。</span><span class="sxs-lookup"><span data-stu-id="b8f58-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="b8f58-107">摘要：本文件旨在包含程序和擴充性來協助準備解決方案的工程師。</span><span class="sxs-lookup"><span data-stu-id="b8f58-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="b8f58-108">詳細資訊應該提供客戶找到的最佳做法，經產品小組驗證後確認所提供的建議可穩定應對未來問題。</span><span class="sxs-lookup"><span data-stu-id="b8f58-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

|           |                      <span data-ttu-id="b8f58-109">文件資訊</span><span class="sxs-lookup"><span data-stu-id="b8f58-109">Doc Info</span></span>                      |
| :-------- | :------------------------------------------------- |
| <span data-ttu-id="b8f58-110">作者</span><span class="sxs-lookup"><span data-stu-id="b8f58-110">Author</span></span>    | <span data-ttu-id="b8f58-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="b8f58-111">Michael Greene</span></span>                                     |
| <span data-ttu-id="b8f58-112">檢閱者</span><span class="sxs-lookup"><span data-stu-id="b8f58-112">Reviewers</span></span> | <span data-ttu-id="b8f58-113">Ben Gelens、Ravikanth Chaganti、Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="b8f58-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span> |
| <span data-ttu-id="b8f58-114">已發行</span><span class="sxs-lookup"><span data-stu-id="b8f58-114">Published</span></span> | <span data-ttu-id="b8f58-115">2015 年 4 月</span><span class="sxs-lookup"><span data-stu-id="b8f58-115">April, 2015</span></span>                                        |

## <a name="abstract"></a><span data-ttu-id="b8f58-116">摘要</span><span class="sxs-lookup"><span data-stu-id="b8f58-116">Abstract</span></span>

<span data-ttu-id="b8f58-117">本文件旨在為規劃 Windows PowerShell 期望狀態設定提取伺服器實作的任何人提供官方指引。</span><span class="sxs-lookup"><span data-stu-id="b8f58-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="b8f58-118">提取伺服器是一項簡單的服務，部署只需要幾分鐘。</span><span class="sxs-lookup"><span data-stu-id="b8f58-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="b8f58-119">雖然這份文件會提供可用於部署的技術指引，但本文件的價值如同最佳做法和部署前考慮事項的參考。</span><span class="sxs-lookup"><span data-stu-id="b8f58-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span> <span data-ttu-id="b8f58-120">讀者對 DSC 以及描述 DSC 部署內含元件的詞彙應有基本的了解。</span><span class="sxs-lookup"><span data-stu-id="b8f58-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="b8f58-121">如需詳細資訊，請參閱 [Windows PowerShell Desired State Configuration 概觀](/powershell/scripting/dsc/overview/overview)主題。</span><span class="sxs-lookup"><span data-stu-id="b8f58-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/overview) topic.</span></span> <span data-ttu-id="b8f58-122">因為 DSC 預期依雲端節奏發展，所以包含提取伺服器的基礎技術也預期會發展並推出新功能。</span><span class="sxs-lookup"><span data-stu-id="b8f58-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="b8f58-123">本文件附錄中的版本表提供有關舊版的參考，以及鼓勵展望未來設計的解決方案參考。</span><span class="sxs-lookup"><span data-stu-id="b8f58-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="b8f58-124">本文件分為兩大部分︰</span><span class="sxs-lookup"><span data-stu-id="b8f58-124">The two major sections of this document:</span></span>

- <span data-ttu-id="b8f58-125">設定規劃</span><span class="sxs-lookup"><span data-stu-id="b8f58-125">Configuration Planning</span></span>
- <span data-ttu-id="b8f58-126">安裝指南</span><span class="sxs-lookup"><span data-stu-id="b8f58-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="b8f58-127">Windows Management Framework 版本</span><span class="sxs-lookup"><span data-stu-id="b8f58-127">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="b8f58-128">本文件中的資訊適用於 Windows Management Framework 5.0。</span><span class="sxs-lookup"><span data-stu-id="b8f58-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="b8f58-129">雖然部署及操作提取伺服器不需要 WMF 5.0，但 5.0 版是本文的焦點。</span><span class="sxs-lookup"><span data-stu-id="b8f58-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="b8f58-130">Windows PowerShell Desired State Configuration (Windows PowerShell 期望狀態設定)</span><span class="sxs-lookup"><span data-stu-id="b8f58-130">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="b8f58-131">預期狀態設定 (DSC) 是一個管理平台，使用名為管理物件格式 (MOF) 的業界語法描述通用訊息模型 (CIM)，來部署和管理設定資料。</span><span class="sxs-lookup"><span data-stu-id="b8f58-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="b8f58-132">開放式管理基礎結構 (OMI) 這個開放原始碼專案，可跨 Linux 等平台與網路硬體作業系統進一步開發這些標準。</span><span class="sxs-lookup"><span data-stu-id="b8f58-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="b8f58-133">如需詳細資訊，請參閱[連結至 MOF 規格的 DMTF 頁面](https://www.dmtf.org/standards/cim)以及 [OMI 文件和來源](https://collaboration.opengroup.org/omi/documents.php)。</span><span class="sxs-lookup"><span data-stu-id="b8f58-133">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="b8f58-134">Windows PowerShell 提供一組預期狀態設定的語言延伸模組，您可用來建立與管理宣告式設定。</span><span class="sxs-lookup"><span data-stu-id="b8f58-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="b8f58-135">提取伺服器角色</span><span class="sxs-lookup"><span data-stu-id="b8f58-135">Pull server role</span></span>

<span data-ttu-id="b8f58-136">提取伺服器提供集中式服務以儲存將來可存取的目標節點設定。</span><span class="sxs-lookup"><span data-stu-id="b8f58-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="b8f58-137">提取伺服器角色可以部署為 Web 伺服器執行個體或 SMB 檔案共用。</span><span class="sxs-lookup"><span data-stu-id="b8f58-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="b8f58-138">Web 伺服器功能包括 OData 介面，並可選擇是否包含目標節點功能，回報套用設定後確認成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="b8f58-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="b8f58-139">這項功能在有大量目標節點的環境中很有用。</span><span class="sxs-lookup"><span data-stu-id="b8f58-139">This functionality is useful in environments where there are a large number of target nodes.</span></span> <span data-ttu-id="b8f58-140">將目標節點 (也稱為用戶端) 設定指向提取伺服器後，就會下載並套用最新的設定資料和任何必要的指令碼。</span><span class="sxs-lookup"><span data-stu-id="b8f58-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="b8f58-141">單次部署或重複的作業都會出現這種情況，這也會讓提取伺服器成為管理大規模變更的重要資產。</span><span class="sxs-lookup"><span data-stu-id="b8f58-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="b8f58-142">如需詳細資訊，請參閱 [Windows PowerShell 預期狀態設定提取伺服器](pullserver.md)和[發送及提取設定模式](pullserver.md)。</span><span class="sxs-lookup"><span data-stu-id="b8f58-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](pullserver.md) and [Push and Pull Configuration Modes](pullserver.md).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="b8f58-143">設定規劃</span><span class="sxs-lookup"><span data-stu-id="b8f58-143">Configuration planning</span></span>

<span data-ttu-id="b8f58-144">任何企業軟體部署都有可預先收集的資訊，以利規劃正確的架構，並準備好完成部署所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="b8f58-144">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="b8f58-145">下列各節提供有關如何準備以及可能需要事先進行的組織性連線資訊。</span><span class="sxs-lookup"><span data-stu-id="b8f58-145">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="b8f58-146">軟體需求</span><span class="sxs-lookup"><span data-stu-id="b8f58-146">Software requirements</span></span>

<span data-ttu-id="b8f58-147">提取伺服器部署需要 Windows Server 的 DSC 服務功能。</span><span class="sxs-lookup"><span data-stu-id="b8f58-147">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="b8f58-148">這項功能在 Windows Server 2012 中推出，且已透過 Windows Management Framework (WMF) 陸續發行的版本進行更新。</span><span class="sxs-lookup"><span data-stu-id="b8f58-148">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="b8f58-149">軟體下載</span><span class="sxs-lookup"><span data-stu-id="b8f58-149">Software downloads</span></span>

<span data-ttu-id="b8f58-150">除了從 Windows Update 安裝最新的內容，部署 DSC 提取伺服器的最佳做法中也包含了兩個下載項目：最新版本的 Windows Management Framework，以及自動化提取伺服器佈建的 DSC 模組。</span><span class="sxs-lookup"><span data-stu-id="b8f58-150">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="b8f58-151">WMF</span><span class="sxs-lookup"><span data-stu-id="b8f58-151">WMF</span></span>

<span data-ttu-id="b8f58-152">Windows Server 2012 R2 包含名為 DSC 服務的功能。</span><span class="sxs-lookup"><span data-stu-id="b8f58-152">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="b8f58-153">DSC 服務功能提供提取伺服器功能，包括支援 OData 端點的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="b8f58-153">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span> <span data-ttu-id="b8f58-154">WMF 包含在 Windows Server 中，並隨不定期發行的 Windows Server 更新。</span><span class="sxs-lookup"><span data-stu-id="b8f58-154">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span>
<span data-ttu-id="b8f58-155">[新版 WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) 可包含 DSC 服務功能的更新。</span><span class="sxs-lookup"><span data-stu-id="b8f58-155">[New versions of WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) can include updates to the DSC Service feature.</span></span> <span data-ttu-id="b8f58-156">基於這個理由，最好下載最新版的 WMF，並檢閱版本資訊來判斷版本是否包含 DSC 服務功能的更新。</span><span class="sxs-lookup"><span data-stu-id="b8f58-156">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="b8f58-157">您也應該檢閱指出更新或案例的設計狀態列為穩定或實驗性的版本資訊一節。</span><span class="sxs-lookup"><span data-stu-id="b8f58-157">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span> <span data-ttu-id="b8f58-158">為保持彈性靈活的發行週期，個別功能可以宣告穩定，這表示 WMF 發行預覽版本時，功能已就緒可用於生產環境。</span><span class="sxs-lookup"><span data-stu-id="b8f58-158">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span> <span data-ttu-id="b8f58-159">WMF 版本過去更新的其他功能 (詳細資訊請參閱 WMF 版本資訊)︰</span><span class="sxs-lookup"><span data-stu-id="b8f58-159">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="b8f58-160">Windows PowerShell Windows PowerShell 整合式指令碼</span><span class="sxs-lookup"><span data-stu-id="b8f58-160">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="b8f58-161">環境 (ISE) Windows PowerShell Web 服務 (Management OData</span><span class="sxs-lookup"><span data-stu-id="b8f58-161">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="b8f58-162">IIS延伸模組) Windows PowerShell 預期狀態設定 (DSC)</span><span class="sxs-lookup"><span data-stu-id="b8f58-162">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="b8f58-163">Windows 遠端管理 (WinRM) Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="b8f58-163">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="b8f58-164">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="b8f58-164">DSC resource</span></span>

<span data-ttu-id="b8f58-165">佈建使用 DSC 設定指令碼的服務，可以簡化提取伺服器部署。</span><span class="sxs-lookup"><span data-stu-id="b8f58-165">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="b8f58-166">本文件包含可用來部署生產就緒伺服器節點的設定指令碼。</span><span class="sxs-lookup"><span data-stu-id="b8f58-166">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="b8f58-167">若要使用設定指令碼，需要不包含在 Windows Server 中的 DSC 模組。</span><span class="sxs-lookup"><span data-stu-id="b8f58-167">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="b8f58-168">所需模組名稱是 **xPSDesiredStateConfiguration**，其中包含 DSC 資源 **xDscWebService**。</span><span class="sxs-lookup"><span data-stu-id="b8f58-168">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="b8f58-169">您可以在[這裡](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d)下載 xPSDesiredStateConfiguration 模組。</span><span class="sxs-lookup"><span data-stu-id="b8f58-169">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="b8f58-170">使用 **PowerShellGet** 模組的 `Install-Module` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b8f58-170">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="b8f58-171">**PowerShellGet** 模組會將模組下載至︰</span><span class="sxs-lookup"><span data-stu-id="b8f58-171">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="b8f58-172">規劃工作</span><span class="sxs-lookup"><span data-stu-id="b8f58-172">Planning task</span></span>
- <span data-ttu-id="b8f58-173">您可以存取 Windows Server 2012 R2 的安裝檔案嗎？</span><span class="sxs-lookup"><span data-stu-id="b8f58-173">Do you have access to the installation files for Windows Server 2012 R2?</span></span>
- <span data-ttu-id="b8f58-174">部署環境可否存取網際網路，從線上組件庫下載 WMF 和模組？</span><span class="sxs-lookup"><span data-stu-id="b8f58-174">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>
- <span data-ttu-id="b8f58-175">安裝作業系統之後，您要如何安裝最新的安全性更新？</span><span class="sxs-lookup"><span data-stu-id="b8f58-175">How will you install the latest security updates after installing the operating system?</span></span>
- <span data-ttu-id="b8f58-176">環境可否存取網際網路以取得更新，或有本機 Windows Server Update Services (WSUS) 伺服器？</span><span class="sxs-lookup"><span data-stu-id="b8f58-176">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>
- <span data-ttu-id="b8f58-177">您可以存取透過離線導入包含更新的 Windows Server 安裝檔案嗎？</span><span class="sxs-lookup"><span data-stu-id="b8f58-177">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>

### <a name="hardware-requirements"></a><span data-ttu-id="b8f58-178">硬體需求</span><span class="sxs-lookup"><span data-stu-id="b8f58-178">Hardware requirements</span></span>

<span data-ttu-id="b8f58-179">實體和虛擬伺服器都支援提取伺服器部署。</span><span class="sxs-lookup"><span data-stu-id="b8f58-179">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="b8f58-180">提取伺服器的大小需求與 Windows Server 2012 R2 的需求一致。</span><span class="sxs-lookup"><span data-stu-id="b8f58-180">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

- <span data-ttu-id="b8f58-181">CPU：1.4 GHz 64 位元處理器</span><span class="sxs-lookup"><span data-stu-id="b8f58-181">CPU: 1.4 GHz 64-bit processor</span></span>
- <span data-ttu-id="b8f58-182">記憶體：512 MB</span><span class="sxs-lookup"><span data-stu-id="b8f58-182">Memory: 512 MB</span></span>
- <span data-ttu-id="b8f58-183">磁碟空間：32 GB</span><span class="sxs-lookup"><span data-stu-id="b8f58-183">Disk Space: 32 GB</span></span>
- <span data-ttu-id="b8f58-184">網路：Gigabit 乙太網路介面卡</span><span class="sxs-lookup"><span data-stu-id="b8f58-184">Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="b8f58-185">規劃工作</span><span class="sxs-lookup"><span data-stu-id="b8f58-185">Planning task</span></span>
- <span data-ttu-id="b8f58-186">您要部署在實體硬體或虛擬平台？</span><span class="sxs-lookup"><span data-stu-id="b8f58-186">Will you deploy on physical hardware or on a virtualization platform?</span></span>
- <span data-ttu-id="b8f58-187">目標環境要求新伺服器的程序為何？</span><span class="sxs-lookup"><span data-stu-id="b8f58-187">What is the process to request a new server for your target environment?</span></span>
- <span data-ttu-id="b8f58-188">伺服器變成可用的平均迴轉時間為何？</span><span class="sxs-lookup"><span data-stu-id="b8f58-188">What is the average turnaround time for a server to become available?</span></span>
- <span data-ttu-id="b8f58-189">您會要求何種大小的伺服器？</span><span class="sxs-lookup"><span data-stu-id="b8f58-189">What size server will you request?</span></span>

### <a name="accounts"></a><span data-ttu-id="b8f58-190">帳戶</span><span class="sxs-lookup"><span data-stu-id="b8f58-190">Accounts</span></span>

<span data-ttu-id="b8f58-191">部署提取伺服器執行個體沒有任何服務帳戶需求。</span><span class="sxs-lookup"><span data-stu-id="b8f58-191">There are no service account requirements to deploy a pull server instance.</span></span> <span data-ttu-id="b8f58-192">不過有些時候網站會以本機使用者帳戶的內容執行。</span><span class="sxs-lookup"><span data-stu-id="b8f58-192">However, there are scenarios where the website could run in the context of a local user account.</span></span> <span data-ttu-id="b8f58-193">例如，如果需要存取網站內容的儲存體共用，但 Windows Server 或裝載儲存體共用的裝置未加入網域。</span><span class="sxs-lookup"><span data-stu-id="b8f58-193">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="b8f58-194">DNS 記錄</span><span class="sxs-lookup"><span data-stu-id="b8f58-194">DNS records</span></span>

<span data-ttu-id="b8f58-195">設定用戶端使用提取伺服器環境時需要使用伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="b8f58-195">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="b8f58-196">測試環境通常會使用伺服器主機名稱，但若無法使用 DNS 名稱解析，則使用伺服器的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="b8f58-196">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span> <span data-ttu-id="b8f58-197">在生產環境或用來表示生產部署的實驗室環境中，最佳做法是建立 DNS CNAME 記錄。</span><span class="sxs-lookup"><span data-stu-id="b8f58-197">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="b8f58-198">DNS CNAME 可讓您建立指向主機 (A) 記錄的別名。</span><span class="sxs-lookup"><span data-stu-id="b8f58-198">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span> <span data-ttu-id="b8f58-199">其他名稱記錄的目的，是如果以後需要變更時能夠增加彈性。</span><span class="sxs-lookup"><span data-stu-id="b8f58-199">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span> <span data-ttu-id="b8f58-200">CNAME 可以協助隔離用戶端設定，以便伺服器環境的變更，例如取代提取伺服器或新增其他提取伺服器，不需要與用戶端設定相對應的變更。</span><span class="sxs-lookup"><span data-stu-id="b8f58-200">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="b8f58-201">在選擇 DNS 記錄名稱時，請牢記解決方案架構。</span><span class="sxs-lookup"><span data-stu-id="b8f58-201">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="b8f58-202">如果使用負載平衡，則用來保護 HTTPS 流量的憑證就需要與 DNS 記錄共用相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8f58-202">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

       <span data-ttu-id="b8f58-203">狀況</span><span class="sxs-lookup"><span data-stu-id="b8f58-203">Scenario</span></span>        |                                                                                         <span data-ttu-id="b8f58-204">最佳做法</span><span class="sxs-lookup"><span data-stu-id="b8f58-204">Best Practice</span></span>
:--------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="b8f58-205">測試環境</span><span class="sxs-lookup"><span data-stu-id="b8f58-205">Test Environment</span></span>       | <span data-ttu-id="b8f58-206">可能的話，請重新產生規劃的生產環境。</span><span class="sxs-lookup"><span data-stu-id="b8f58-206">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="b8f58-207">伺服器主機名稱適用於簡單的設定。</span><span class="sxs-lookup"><span data-stu-id="b8f58-207">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="b8f58-208">若無 DNS 可用，主機名稱可使用 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="b8f58-208">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>
<span data-ttu-id="b8f58-209">單一節點部署</span><span class="sxs-lookup"><span data-stu-id="b8f58-209">Single Node Deployment</span></span> | <span data-ttu-id="b8f58-210">建立指向伺服器主機名稱的 DNS CNAME 記錄。</span><span class="sxs-lookup"><span data-stu-id="b8f58-210">Create a DNS CNAME record that points to the server hostname.</span></span>

<span data-ttu-id="b8f58-211">如需詳細資訊，請參閱[在 Windows Server 中設定 DNS 循環配置資源](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="b8f58-211">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="b8f58-212">規劃工作</span><span class="sxs-lookup"><span data-stu-id="b8f58-212">Planning task</span></span>
- <span data-ttu-id="b8f58-213">您知道若要建立與變更 DNS 記錄要連絡誰嗎？</span><span class="sxs-lookup"><span data-stu-id="b8f58-213">Do you know who to contact to have DNS records created and changed?</span></span>
- <span data-ttu-id="b8f58-214">DNS 記錄要求的平均迴轉時間為何？</span><span class="sxs-lookup"><span data-stu-id="b8f58-214">What is the average turnaround for a request for a DNS record?</span></span>
- <span data-ttu-id="b8f58-215">您需要要求伺服器的靜態主機名稱 (A) 記錄嗎？</span><span class="sxs-lookup"><span data-stu-id="b8f58-215">Do you need to request static Hostname (A) records for servers?</span></span>
- <span data-ttu-id="b8f58-216">您要以 CNAME 的名義要求什麼？</span><span class="sxs-lookup"><span data-stu-id="b8f58-216">What will you request as a CNAME?</span></span>
- <span data-ttu-id="b8f58-217">如有需要，您要使用何種負載平衡解決方案？</span><span class="sxs-lookup"><span data-stu-id="b8f58-217">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="b8f58-218">(詳細資訊請參閱＜負載平衡＞一節)</span><span class="sxs-lookup"><span data-stu-id="b8f58-218">(see section titled Load Balancing for details)</span></span>

### <a name="public-key-infrastructure"></a><span data-ttu-id="b8f58-219">公開金鑰基礎結構</span><span class="sxs-lookup"><span data-stu-id="b8f58-219">Public Key Infrastructure</span></span>

<span data-ttu-id="b8f58-220">現今大部分的組織都需要網路流量，特別是包含伺服器設定方式等機密資料的流量，必須在傳送時驗證及/或加密。</span><span class="sxs-lookup"><span data-stu-id="b8f58-220">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="b8f58-221">雖然您可以部署使用 HTTP 的提取伺服器來方便用戶端以純文字提出要求，但最好的做法卻是保護使用 HTTPS 的流量。</span><span class="sxs-lookup"><span data-stu-id="b8f58-221">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="b8f58-222">您可以在 DSC 資源 **xPSDesiredStateConfiguration** 中使用一組參數，設定服務使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="b8f58-222">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="b8f58-223">保護提取伺服器 HTTPS 流量的憑證需求，和保護任何其他 HTTPS 網站的沒有不同。</span><span class="sxs-lookup"><span data-stu-id="b8f58-223">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="b8f58-224">Windows Server 憑證服務的 **Web 伺服器**範本符合所需功能。</span><span class="sxs-lookup"><span data-stu-id="b8f58-224">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="b8f58-225">規劃工作</span><span class="sxs-lookup"><span data-stu-id="b8f58-225">Planning task</span></span>
- <span data-ttu-id="b8f58-226">如果憑證要求未自動化，您要連絡誰要求憑證？</span><span class="sxs-lookup"><span data-stu-id="b8f58-226">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>
- <span data-ttu-id="b8f58-227">要求的平均迴轉時間為何？</span><span class="sxs-lookup"><span data-stu-id="b8f58-227">What is the average turnaround for the request?</span></span>
- <span data-ttu-id="b8f58-228">如何傳送憑證檔案給您？</span><span class="sxs-lookup"><span data-stu-id="b8f58-228">How will the certificate file be transferred to you?</span></span>
- <span data-ttu-id="b8f58-229">如何傳送憑證私密金鑰給您？</span><span class="sxs-lookup"><span data-stu-id="b8f58-229">How will the certificate private key be transferred to you?</span></span>
- <span data-ttu-id="b8f58-230">預設到期時間多長？</span><span class="sxs-lookup"><span data-stu-id="b8f58-230">How long is the default expiration time?</span></span>
- <span data-ttu-id="b8f58-231">提取伺服器環境已就緒可用於憑證名稱的 DNS 名稱了嗎？</span><span class="sxs-lookup"><span data-stu-id="b8f58-231">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>

### <a name="choosing-an-architecture"></a><span data-ttu-id="b8f58-232">選擇架構</span><span class="sxs-lookup"><span data-stu-id="b8f58-232">Choosing an architecture</span></span>

<span data-ttu-id="b8f58-233">您可以使用裝載於 IIS 的 Web 服務或 SMB 檔案共用來部署提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="b8f58-233">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="b8f58-234">在大部分情況下，Web 服務選項會提供較大的彈性。</span><span class="sxs-lookup"><span data-stu-id="b8f58-234">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="b8f58-235">HTTPS 流量周遊網路界限很常見，但 SMB 流量通常會在網路間被篩選或封鎖。</span><span class="sxs-lookup"><span data-stu-id="b8f58-235">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="b8f58-236">Web 服務也提供包含相容伺服器或 Web 報告管理員的選項 (本文件會在未來版本中處理這兩個主題)，提供一個機制供用戶端向伺服器回報狀態，以集中處理。</span><span class="sxs-lookup"><span data-stu-id="b8f58-236">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span> <span data-ttu-id="b8f58-237">SMB 讓原則規定不該使用 Web 伺服器的環境，以及不要求 Web 伺服器角色的其他環境需求，有選擇的機會。</span><span class="sxs-lookup"><span data-stu-id="b8f58-237">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span> <span data-ttu-id="b8f58-238">無論哪一種情況，請記得評估簽署與加密流量的需求。</span><span class="sxs-lookup"><span data-stu-id="b8f58-238">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="b8f58-239">HTTPS、SMB 簽署和 IPSEC 原則都是值得考慮的選項。</span><span class="sxs-lookup"><span data-stu-id="b8f58-239">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="b8f58-240">負載平衡</span><span class="sxs-lookup"><span data-stu-id="b8f58-240">Load balancing</span></span>

<span data-ttu-id="b8f58-241">與 Web 服務互動的用戶端提出以單一回應傳回資訊的要求。</span><span class="sxs-lookup"><span data-stu-id="b8f58-241">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="b8f58-242">不需要任何循序要求，因此負載平衡平台沒必要確保隨時在單一伺服器上維護工作階段。</span><span class="sxs-lookup"><span data-stu-id="b8f58-242">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="b8f58-243">規劃工作</span><span class="sxs-lookup"><span data-stu-id="b8f58-243">Planning task</span></span>
- <span data-ttu-id="b8f58-244">跨伺服器的負載平衡流量會使用哪些解決方案？</span><span class="sxs-lookup"><span data-stu-id="b8f58-244">What solution will be used for load balancing traffic across servers?</span></span>
- <span data-ttu-id="b8f58-245">如果使用硬體負載平衡器，誰會接受將新的設定新增至裝置的要求？</span><span class="sxs-lookup"><span data-stu-id="b8f58-245">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>
- <span data-ttu-id="b8f58-246">設定新負載平衡 Web 服務要求的平均迴轉時間為何？</span><span class="sxs-lookup"><span data-stu-id="b8f58-246">What is the average turnaround for a request to configure a new load balanced web service?</span></span>
- <span data-ttu-id="b8f58-247">要求需要哪些資訊？</span><span class="sxs-lookup"><span data-stu-id="b8f58-247">What information will be required for the request?</span></span>
- <span data-ttu-id="b8f58-248">是您必須要求額外的 IP，還是負責負載平衡的小組處理此事？</span><span class="sxs-lookup"><span data-stu-id="b8f58-248">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>
- <span data-ttu-id="b8f58-249">您是否有需要的 DNS 記錄，負責設定負載平衡解決方案的小組會需要它嗎？</span><span class="sxs-lookup"><span data-stu-id="b8f58-249">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>
- <span data-ttu-id="b8f58-250">負載平衡解決方案需要的 PKI，是由裝置處理，還是只要沒有工作階段需求，它就可以平衡 HTTPS 流量的負載？</span><span class="sxs-lookup"><span data-stu-id="b8f58-250">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="b8f58-251">提取伺服器上的預備設定和模組</span><span class="sxs-lookup"><span data-stu-id="b8f58-251">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="b8f58-252">您需要思考提取伺服器要裝載哪些 DSC 模組和設定，這是設定規劃的一部分。</span><span class="sxs-lookup"><span data-stu-id="b8f58-252">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="b8f58-253">為達成設定規劃的目的，對如何準備內容並將其部署到提取伺服器，一定要有基本的了解。</span><span class="sxs-lookup"><span data-stu-id="b8f58-253">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="b8f58-254">未來會擴展本節的內容，並收錄到 DSC 提取伺服器的操作指南中。</span><span class="sxs-lookup"><span data-stu-id="b8f58-254">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span> <span data-ttu-id="b8f58-255">本指南會討論管理模組和設定日常程序的自動化進程。</span><span class="sxs-lookup"><span data-stu-id="b8f58-255">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="b8f58-256">DSC 模組</span><span class="sxs-lookup"><span data-stu-id="b8f58-256">DSC modules</span></span>

<span data-ttu-id="b8f58-257">要求設定的用戶端會需要必要的 DSC 模組。</span><span class="sxs-lookup"><span data-stu-id="b8f58-257">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="b8f58-258">提取伺服器有一項功能是將 DSC 模組自動隨選散佈給用戶端。</span><span class="sxs-lookup"><span data-stu-id="b8f58-258">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="b8f58-259">如果您是第一次部署提取伺服器，可能是基於實驗室或證明概念的需要，您可能會相依於從 PowerShell 組件庫等公用存放庫或 DSC 模組的 PowerShell.org GitHub 存放庫取得的 DSC 模組。</span><span class="sxs-lookup"><span data-stu-id="b8f58-259">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="b8f58-260">請務必記住，即使是受信任的線上來源，例如 PowerShell 組件庫，從公開存放庫下載的任何模組，都應該由具有 PowerShell 經驗和環境知識的人員檢閱，而在該環境中模組的使用早於生產前。</span><span class="sxs-lookup"><span data-stu-id="b8f58-260">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="b8f58-261">完成此工作的同時，也是檢查模組中是否有可移除的任何其他裝載的好時機，例如文件和範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="b8f58-261">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="b8f58-262">透過網路將模組從伺服器下載到用戶端時，這會降低每個用戶端之第一個要求的網路頻寬。</span><span class="sxs-lookup"><span data-stu-id="b8f58-262">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="b8f58-263">每個模組都必須以特定格式封裝為包含模組裝載之 ModuleName_Version.zip 的 ZIP 檔案。</span><span class="sxs-lookup"><span data-stu-id="b8f58-263">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="b8f58-264">將檔案複製到伺服器之後，就必須建立總和檢查碼檔案。</span><span class="sxs-lookup"><span data-stu-id="b8f58-264">After the file is copied to the server a checksum file must be created.</span></span>
<span data-ttu-id="b8f58-265">當用戶端連接到伺服器時，會使用總和檢查碼確認 DSC 模組的內容自發行以來是否變更。</span><span class="sxs-lookup"><span data-stu-id="b8f58-265">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="b8f58-266">規劃工作</span><span class="sxs-lookup"><span data-stu-id="b8f58-266">Planning task</span></span>
- <span data-ttu-id="b8f58-267">您是否要規劃案例是驗證關鍵的測試或實驗室環境呢？</span><span class="sxs-lookup"><span data-stu-id="b8f58-267">If you are planning a test or lab environment which scenarios are key to validate?</span></span>
- <span data-ttu-id="b8f58-268">是否有可公開取得的模組，包含涵蓋所需一切的資源，還是您需要自行撰寫資源？</span><span class="sxs-lookup"><span data-stu-id="b8f58-268">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>
- <span data-ttu-id="b8f58-269">您的環境能否存取網際網路以擷取公用模組？</span><span class="sxs-lookup"><span data-stu-id="b8f58-269">Will your environment have Internet access to retrieve public modules?</span></span>
- <span data-ttu-id="b8f58-270">誰會負責檢閱 DSC 模組？</span><span class="sxs-lookup"><span data-stu-id="b8f58-270">Who will be responsible for reviewing DSC modules?</span></span>
- <span data-ttu-id="b8f58-271">如果您要規劃生產環境，您會使用什麼當作本機存放庫來儲存 DSC 模組？</span><span class="sxs-lookup"><span data-stu-id="b8f58-271">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>
- <span data-ttu-id="b8f58-272">中心小組接不接受應用程式小組的 DSC 模組？</span><span class="sxs-lookup"><span data-stu-id="b8f58-272">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="b8f58-273">程序為何？</span><span class="sxs-lookup"><span data-stu-id="b8f58-273">What will the process be?</span></span>
- <span data-ttu-id="b8f58-274">您會從自己的來源存放庫自動化封裝、複製及建立伺服器的生產就緒 DSC 模組總和檢查碼嗎？</span><span class="sxs-lookup"><span data-stu-id="b8f58-274">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>
- <span data-ttu-id="b8f58-275">您的小組也會負責管理自動化平台嗎？</span><span class="sxs-lookup"><span data-stu-id="b8f58-275">Will your team be responsible for managing the automation platform as well?</span></span>

#### <a name="dsc-configurations"></a><span data-ttu-id="b8f58-276">DSC 組態</span><span class="sxs-lookup"><span data-stu-id="b8f58-276">DSC configurations</span></span>

<span data-ttu-id="b8f58-277">提取伺服器的目的是提供集中式機制，將 DSC 設定散發到用戶端節點。</span><span class="sxs-lookup"><span data-stu-id="b8f58-277">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="b8f58-278">設定在伺服器上儲存為 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="b8f58-278">The configurations are stored on the server as MOF documents.</span></span> <span data-ttu-id="b8f58-279">每份文件都會以唯一的 **GUID** 命名。</span><span class="sxs-lookup"><span data-stu-id="b8f58-279">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="b8f58-280">當用戶端設定成要與提取伺服器連線時，也會收到其應要求的設定 **GUID**。</span><span class="sxs-lookup"><span data-stu-id="b8f58-280">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="b8f58-281">這個依 **GUID** 參考設定的系統能保證全域唯一性，而且十分靈活，讓設定能夠以細微到節點的程度套用，也能以角色設定形式套用，以橫跨多個應該具有相同設定的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b8f58-281">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="b8f58-282">GUID</span><span class="sxs-lookup"><span data-stu-id="b8f58-282">Guids</span></span>

<span data-ttu-id="b8f58-283">當您在考量整個提取伺服器部署時，設定 **GUID** 的規劃值得多加留意。</span><span class="sxs-lookup"><span data-stu-id="b8f58-283">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="b8f58-284">處理 **GUID** 的方式並沒有明確要求，而且每個環境的程序很可能各不相同。</span><span class="sxs-lookup"><span data-stu-id="b8f58-284">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="b8f58-285">程序從簡單到複雜︰集中儲存的 CSV 檔案、簡易 SQL 資料表、CMDB 或需要整合其他工具或軟體方案的複雜解決方案。</span><span class="sxs-lookup"><span data-stu-id="b8f58-285">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="b8f58-286">有兩種一般方法︰</span><span class="sxs-lookup"><span data-stu-id="b8f58-286">There are two general approaches:</span></span>

- <span data-ttu-id="b8f58-287">**依伺服器指派 GUID**：提供確保個別控制每部伺服器設定的量值。</span><span class="sxs-lookup"><span data-stu-id="b8f58-287">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="b8f58-288">這會提供更新前後一定程度的準確性，在只有幾部伺服器的環境中運作良好。</span><span class="sxs-lookup"><span data-stu-id="b8f58-288">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="b8f58-289">**依伺服器角色指派 GUID**：執行相同函式的所有伺服器 (例如網頁伺服器) 都使用相同的 GUID 參考所需的設定資料。</span><span class="sxs-lookup"><span data-stu-id="b8f58-289">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span> <span data-ttu-id="b8f58-290">請注意，如果有許多伺服器共用相同的 GUID，設定變更時，它們全部都會同時更新。</span><span class="sxs-lookup"><span data-stu-id="b8f58-290">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="b8f58-291">GUID 應該視為機密資訊，因為它可用來進行惡意攻擊，取得您環境如何部署與設定伺服器的情報。</span><span class="sxs-lookup"><span data-stu-id="b8f58-291">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="b8f58-292">如需詳細資訊，請參閱 [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/) (在 PowerShell Desired State Configuration 提取模式中安全地配置 GUID)。</span><span class="sxs-lookup"><span data-stu-id="b8f58-292">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="b8f58-293">規劃工作</span><span class="sxs-lookup"><span data-stu-id="b8f58-293">Planning task</span></span>
- <span data-ttu-id="b8f58-294">誰會負責將就緒的設定複製到提取伺服器資料夾？</span><span class="sxs-lookup"><span data-stu-id="b8f58-294">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>
- <span data-ttu-id="b8f58-295">如果是應用程式小組撰寫設定，設定的交付程序為何？</span><span class="sxs-lookup"><span data-stu-id="b8f58-295">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>
- <span data-ttu-id="b8f58-296">您會利用存放庫，跨小組儲存撰寫中的設定嗎？</span><span class="sxs-lookup"><span data-stu-id="b8f58-296">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>
- <span data-ttu-id="b8f58-297">您會自動化將設定複製到伺服器，並於就緒時建立總和檢查碼的程序嗎？</span><span class="sxs-lookup"><span data-stu-id="b8f58-297">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>
- <span data-ttu-id="b8f58-298">您會如何將 GUID 對應至伺服器或角色？這份資料會儲存在何處？</span><span class="sxs-lookup"><span data-stu-id="b8f58-298">How will you map Guids to servers or roles, and where will this be stored?</span></span>
- <span data-ttu-id="b8f58-299">您要使用什麼樣的程序來設定用戶端電腦？它會如何與您建立及儲存設定 GUID 的程序整合？</span><span class="sxs-lookup"><span data-stu-id="b8f58-299">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>

## <a name="installation-guide"></a><span data-ttu-id="b8f58-300">安裝指南</span><span class="sxs-lookup"><span data-stu-id="b8f58-300">Installation Guide</span></span>

<span data-ttu-id="b8f58-301">*本文件中提供的指令碼都是穩定的範例。請務必先仔細閱讀指令碼，再於生產環境中執行它們。*</span><span class="sxs-lookup"><span data-stu-id="b8f58-301">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b8f58-302">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b8f58-302">Prerequisites</span></span>

<span data-ttu-id="b8f58-303">請使用下列命令確認伺服器上的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="b8f58-303">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="b8f58-304">可能的話，請升級至最新版的 Windows Management Framework。</span><span class="sxs-lookup"><span data-stu-id="b8f58-304">If possible, upgrade to the latest version of Windows Management Framework.</span></span> <span data-ttu-id="b8f58-305">然後，使用下列命令下載 `xPsDesiredStateConfiguration` 模組。</span><span class="sxs-lookup"><span data-stu-id="b8f58-305">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="b8f58-306">命令會要求您核准後才下載模組。</span><span class="sxs-lookup"><span data-stu-id="b8f58-306">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="b8f58-307">安裝與設定指令碼</span><span class="sxs-lookup"><span data-stu-id="b8f58-307">Installation and configuration scripts</span></span>

<span data-ttu-id="b8f58-308">部署 DSC 提取伺服器的最佳方法是使用 DSC 設定指令碼。</span><span class="sxs-lookup"><span data-stu-id="b8f58-308">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="b8f58-309">本文件顯示的指令碼，包括只設定 DSC Web 服務的基本設定，以及設定 Windows Server 端對端 (包括 DSC Web 服務) 的進階設定。</span><span class="sxs-lookup"><span data-stu-id="b8f58-309">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="b8f58-310">注意:目前 `xPSDesiredStateConfiguration` DSC 模組需要伺服器使用 EN-US 地區設定。</span><span class="sxs-lookup"><span data-stu-id="b8f58-310">Note:  Currently the `xPSDesiredStateConfiguration` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="b8f58-311">Windows Server 2012 基本設定</span><span class="sxs-lookup"><span data-stu-id="b8f58-311">Basic configuration for Windows Server 2012</span></span>

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="b8f58-312">Windows Server 2012 R2 進階設定</span><span class="sxs-lookup"><span data-stu-id="b8f58-312">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments
# on Windows Server 2012 R2. Many of the features demonstrated are optional and
# provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority,
        # complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider
        # modifying the default port, possibly leveraging port 443 in environments where that is
        # enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="b8f58-313">確認提取伺服器功能</span><span class="sxs-lookup"><span data-stu-id="b8f58-313">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the
# default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="b8f58-314">設定用戶端</span><span class="sxs-lookup"><span data-stu-id="b8f58-314">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="b8f58-315">其他參考資料、程式碼片段和範例</span><span class="sxs-lookup"><span data-stu-id="b8f58-315">Additional references, snippets, and examples</span></span>

<span data-ttu-id="b8f58-316">本範例示範如何以手動方式啟動用戶端連線 (需要 WMF5) 以進行測試。</span><span class="sxs-lookup"><span data-stu-id="b8f58-316">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="b8f58-317">[Add-DnsServerResourceRecordName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname) Cmdlet 用於將 CNAME 記錄類型新增至 DNS 區域。</span><span class="sxs-lookup"><span data-stu-id="b8f58-317">The [Add-DnsServerResourceRecordName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="b8f58-318">[Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) (建立總和檢查碼並將 DSC MOF 發行至 SMB 提取伺服器) 的 PowerShell 函式會自動產生所需的總和檢查碼，然後將 MOF 設定和總和檢查碼檔案複製到 SMB 提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="b8f58-318">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="b8f58-319">附錄：了解 ODATA 服務的資料檔案類型</span><span class="sxs-lookup"><span data-stu-id="b8f58-319">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="b8f58-320">儲存資料檔案是為了建立含 OData Web 服務的提取伺服器在部署期間的資訊。</span><span class="sxs-lookup"><span data-stu-id="b8f58-320">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="b8f58-321">檔案類型視作業系統而定，如下所述。</span><span class="sxs-lookup"><span data-stu-id="b8f58-321">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="b8f58-322">**Windows Server 2012** 檔案類型一律為 .mdb</span><span class="sxs-lookup"><span data-stu-id="b8f58-322">**Windows Server 2012** The file type will always be   .mdb</span></span>
- <span data-ttu-id="b8f58-323">**Windows Server 2012 R2** 除非設定中指定 .mdb，否則檔案類型預設為 .edb</span><span class="sxs-lookup"><span data-stu-id="b8f58-323">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="b8f58-324">在安裝提取伺服器的[進階範例指令碼](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts)中，您也會找到如何自動控制 web.config 檔案設定，防止因檔案類型而發生任何錯誤的範例。</span><span class="sxs-lookup"><span data-stu-id="b8f58-324">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
