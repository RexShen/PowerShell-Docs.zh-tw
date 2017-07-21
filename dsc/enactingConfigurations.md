---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "施行設定"
ms.openlocfilehash: db82788650186eb82f67b30b24cd45b719bbe314
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="enacting-configurations"></a><span data-ttu-id="5e845-103">施行設定</span><span class="sxs-lookup"><span data-stu-id="5e845-103">Enacting configurations</span></span>

><span data-ttu-id="5e845-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5e845-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5e845-105">PowerShell 預期狀態設定 (DSC) 設定有兩種施行方式：Push 模式和 Pull 模式。</span><span class="sxs-lookup"><span data-stu-id="5e845-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="5e845-106">Push 模式</span><span class="sxs-lookup"><span data-stu-id="5e845-106">Push mode</span></span>

<span data-ttu-id="5e845-107">![Push 模式](images/Push.png "Push 模式的運作方式")</span><span class="sxs-lookup"><span data-stu-id="5e845-107">![Push mode](images/Push.png "How push mode works")</span></span>

<span data-ttu-id="5e845-108">Push 模式指的是使用者呼叫 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet，將設定積極套用至目標節點。</span><span class="sxs-lookup"><span data-stu-id="5e845-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span>

<span data-ttu-id="5e845-109">建立及編譯設定後，您可以呼叫 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet，設定 MOF 所在路徑之 Cmdlet 的 -Path 參數，以 Push 模式施行設定。</span><span class="sxs-lookup"><span data-stu-id="5e845-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span> <span data-ttu-id="5e845-110">例如，如果設定 MOF 位於 `C:\DSC\Configurations\localhost.mof`，您可以使用下列命令將其套用到本機電腦：`Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="5e845-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="5e845-111">__注意__：DSC 預設將設定當做背景工作執行。</span><span class="sxs-lookup"><span data-stu-id="5e845-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="5e845-112">若要以互動方式執行設定，請呼叫 [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) 配以 __-Wait__ 參數。</span><span class="sxs-lookup"><span data-stu-id="5e845-112">To run the configuration interactively, call the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) with the __-Wait__ parameter.</span></span>


## <a name="pull-mode"></a><span data-ttu-id="5e845-113">Pull 模式</span><span class="sxs-lookup"><span data-stu-id="5e845-113">Pull mode</span></span>

<span data-ttu-id="5e845-114">![Pull 模式](images/Pull.png "Pull 模式的運作方式")</span><span class="sxs-lookup"><span data-stu-id="5e845-114">![Pull Mode](images/Pull.png "How pull mode works")</span></span>

<span data-ttu-id="5e845-115">在 Pull 模式中，提取用戶端會設定成從遠端的提取伺服器取得其所需的狀態設定。</span><span class="sxs-lookup"><span data-stu-id="5e845-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull server.</span></span> <span data-ttu-id="5e845-116">同樣地，提取伺服器已設為 DSC 服務主機，佈建了提取用戶端所需要的設定和資源。</span><span class="sxs-lookup"><span data-stu-id="5e845-116">Likewise, the pull server has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span> <span data-ttu-id="5e845-117">每個提取用戶端都有排定的工作，對節點設定執行定期的相容性檢查。</span><span class="sxs-lookup"><span data-stu-id="5e845-117">Each one of the pull clients has a scheduled task that performs a periodic compliance check on the configuration of the node.</span></span> <span data-ttu-id="5e845-118">當第一次觸發事件時，提取用戶端上的本機設定管理員 (LCM) 會向提取伺服器提出要求，以取得 LCM 中指定的設定。</span><span class="sxs-lookup"><span data-stu-id="5e845-118">When the event is triggered the first time, it the Local Configuration Manager (LCM) on the pull client makes a request to the pull server to get the configuration specified in the LCM.</span></span> <span data-ttu-id="5e845-119">如果提取伺服器上有這個設定，而且它通過了初始驗證檢查，設定就會傳輸到提取用戶端，LCM 會在這裡執行它。</span><span class="sxs-lookup"><span data-stu-id="5e845-119">If that configuration exists on the pull server, and it passes initial validation checks, the configuration is transmitted to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="5e845-120">LCM 會依照 LCM 的 **ConfigurationModeFrequencyMins** 屬性所指定的固定間隔，檢查用戶端是否符合設定。</span><span class="sxs-lookup"><span data-stu-id="5e845-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="5e845-121">LCM 會依照 LCM 的 **RefreshModeFrequency** 屬性所指定的固定間隔，檢查提取伺服器上的更新設定。</span><span class="sxs-lookup"><span data-stu-id="5e845-121">The LCM checks for updated configurations on the pull server at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span> <span data-ttu-id="5e845-122">如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](metaConfig.md)。</span><span class="sxs-lookup"><span data-stu-id="5e845-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

<span data-ttu-id="5e845-123">如需設定 DSC 提取伺服器的詳細資訊，請參閱[設定 DSC Web 提取伺服器](pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="5e845-123">For more information on setting up a DSC Pull Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>

<span data-ttu-id="5e845-124">如果想要利用線上服務裝載提取伺服器功能，請參閱 [Azure 自動化 DSC](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/) 服務。</span><span class="sxs-lookup"><span data-stu-id="5e845-124">If you would prefer to take advantage of an online service to host Pull Server functionality, see the [Azure Automation DSC](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-overview/) service.</span></span>

<span data-ttu-id="5e845-125">下列主題說明如何設定提取伺服器和用戶端：</span><span class="sxs-lookup"><span data-stu-id="5e845-125">The following topics explain how to set up pull servers and clients:</span></span>

- [<span data-ttu-id="5e845-126">設定 Web 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="5e845-126">Setting up a web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="5e845-127">設定 SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="5e845-127">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="5e845-128">設定提取用戶端</span><span class="sxs-lookup"><span data-stu-id="5e845-128">Configuring a pull client</span></span>](pullClientConfigID.md)

