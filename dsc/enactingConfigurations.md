---
ms.date: 10/16/2017
keywords: dsc,powershell,設定,安裝
title: 施行設定
ms.openlocfilehash: 3d938d14a4da645bbea7ba30ab41e0af72c4b94e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188463"
---
# <a name="enacting-configurations"></a><span data-ttu-id="c1600-103">施行設定</span><span class="sxs-lookup"><span data-stu-id="c1600-103">Enacting configurations</span></span>

><span data-ttu-id="c1600-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c1600-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c1600-105">PowerShell 預期狀態設定 (DSC) 設定有兩種施行方式：Push 模式和 Pull 模式。</span><span class="sxs-lookup"><span data-stu-id="c1600-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="c1600-106">Push 模式</span><span class="sxs-lookup"><span data-stu-id="c1600-106">Push mode</span></span>

<span data-ttu-id="c1600-107">![Push 模式](images/pushModel.png "Push 模式的運作方式")</span><span class="sxs-lookup"><span data-stu-id="c1600-107">![Push mode](images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="c1600-108">Push 模式指的是使用者呼叫 [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) Cmdlet，將設定積極套用至目標節點。</span><span class="sxs-lookup"><span data-stu-id="c1600-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span></span>

<span data-ttu-id="c1600-109">建立及編譯設定後，您可以呼叫 [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) Cmdlet，設定 MOF 所在路徑之 Cmdlet 的 -Path 參數，以 Push 模式施行設定。</span><span class="sxs-lookup"><span data-stu-id="c1600-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="c1600-110">例如，如果設定 MOF 位於 `C:\DSC\Configurations\localhost.mof`，您可以使用下列命令將其套用到本機電腦：`Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="c1600-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="c1600-111">__注意__：DSC 預設將設定當做背景工作執行。</span><span class="sxs-lookup"><span data-stu-id="c1600-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="c1600-112">若要以互動方式執行設定，請呼叫 [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) 配以 __-Wait__ 參數。</span><span class="sxs-lookup"><span data-stu-id="c1600-112">To run the configuration interactively, call the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="c1600-113">Pull 模式</span><span class="sxs-lookup"><span data-stu-id="c1600-113">Pull mode</span></span>

<span data-ttu-id="c1600-114">![Pull 模式](images/pullModel.png "Pull 模式的運作方式")</span><span class="sxs-lookup"><span data-stu-id="c1600-114">![Pull Mode](images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="c1600-115">在 Pull 模式中，提取用戶端會設定成從遠端提取服務取得其所需的狀態設定。</span><span class="sxs-lookup"><span data-stu-id="c1600-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="c1600-116">同樣地，提取服務已設為 DSC 服務主機，並已佈建提取用戶端所需要的設定和資源。</span><span class="sxs-lookup"><span data-stu-id="c1600-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="c1600-117">每個提取用戶端都有排定的事件，會針對節點的設定執行定期的合規性檢查。</span><span class="sxs-lookup"><span data-stu-id="c1600-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="c1600-118">事件初次觸發時，提取用戶端上的本機設定管理員 (LCM) 會向提取服務提出要求，以取得於 LCM 中指定的設定。</span><span class="sxs-lookup"><span data-stu-id="c1600-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="c1600-119">如果提取服務上有該設定，且它通過初始驗證檢查，設定就會被下載至提取用戶端，而 LCM 將會在那裡執行它。</span><span class="sxs-lookup"><span data-stu-id="c1600-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="c1600-120">LCM 會依照 LCM 的 **ConfigurationModeFrequencyMins** 屬性所指定的固定間隔，檢查用戶端是否符合設定。</span><span class="sxs-lookup"><span data-stu-id="c1600-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="c1600-121">LCM 會依照 LCM 的 **RefreshModeFrequency** 屬性所指定的固定間隔，檢查提取服務上的更新設定。</span><span class="sxs-lookup"><span data-stu-id="c1600-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="c1600-122">如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="c1600-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

<span data-ttu-id="c1600-123">託管提取服務的建議解決方案為 DSC 雲端服務：[Azure 自動化](https://azure.microsoft.com/services/automation/)。</span><span class="sxs-lookup"><span data-stu-id="c1600-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="c1600-124">此託管解決方案能提供圖形化管理、報告，以及集中化的系統管理。</span><span class="sxs-lookup"><span data-stu-id="c1600-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="c1600-125">如需在 Windows Server 上設定提取服務的詳細資訊，請參閱[設定 DSC Web 提取伺服器](pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="c1600-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="c1600-126">不過，請了解此實作僅具備有限的功能，且需要您自行完成部分的整合。</span><span class="sxs-lookup"><span data-stu-id="c1600-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="c1600-127">下列主題會說明提取服務和用戶端：</span><span class="sxs-lookup"><span data-stu-id="c1600-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="c1600-128">Azure 自動化 DSC 概觀</span><span class="sxs-lookup"><span data-stu-id="c1600-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="c1600-129">設定 SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="c1600-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="c1600-130">設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="c1600-130">Configuring a pull client</span></span>](pullClientConfigID.md)