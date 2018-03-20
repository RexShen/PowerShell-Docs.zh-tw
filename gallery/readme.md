---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "資源庫,powershell,cmdlet,psgallery,psget"
title: "PowerShell 資源庫"
ms.openlocfilehash: 7389ce8286c515b0bfc25f32634a482b060cb74c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="ba491-103">PowerShell 資源庫</span><span class="sxs-lookup"><span data-stu-id="ba491-103">The PowerShell Gallery</span></span>

<span data-ttu-id="ba491-104">PowerShell 資源庫是 PowerShell 內容的集中存放庫。</span><span class="sxs-lookup"><span data-stu-id="ba491-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="ba491-105">您可以在資源庫中找到新的 PowerShell 命令或預期狀態設定 (DSC) 資源。</span><span class="sxs-lookup"><span data-stu-id="ba491-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="ba491-106">PowerShellGet 概觀</span><span class="sxs-lookup"><span data-stu-id="ba491-106">PowerShellGet Overview</span></span>

<span data-ttu-id="ba491-107">PowerShellGet 模組包含來自 [PowerShell 資源庫](https://www.PowerShellGallery.com)及其他私用存放庫，用於探索、安裝、更新及發行 PowerShell 成品 (例如模組、DSC 資源、角色功能與指令碼) 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ba491-107">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="ba491-108">開始使用資源庫</span><span class="sxs-lookup"><span data-stu-id="ba491-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="ba491-109">要從資源庫安裝項目需要最新版本的 PowerShellGet 模組，其在 Windows 10、Windows Management Framework (WMF) 5.0 或 MSI 安裝程式 (適用於 PowerShell 3 及 4) 均有提供。</span><span class="sxs-lookup"><span data-stu-id="ba491-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="ba491-110">[**取得 Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)、</span><span class="sxs-lookup"><span data-stu-id="ba491-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="ba491-111">[**取得 WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) 或</span><span class="sxs-lookup"><span data-stu-id="ba491-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="ba491-112">**取得 MSI 安裝程式**</span><span class="sxs-lookup"><span data-stu-id="ba491-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="ba491-113">使用最新 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 模組，您可以：</span><span class="sxs-lookup"><span data-stu-id="ba491-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="ba491-114">使用 [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) 與 [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322) 在資源庫中搜尋項目</span><span class="sxs-lookup"><span data-stu-id="ba491-114">Search through items in the Gallery with [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>
-   <span data-ttu-id="ba491-115">使用 [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) 與 [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334) 從資源庫將項目儲存到您的系統</span><span class="sxs-lookup"><span data-stu-id="ba491-115">Save items to your system from the Gallery with [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) and [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span></span>
-   <span data-ttu-id="ba491-116">使用 [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) 與 [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327) 從資源庫安裝項目</span><span class="sxs-lookup"><span data-stu-id="ba491-116">Install items from the Gallery with [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span></span>
-   <span data-ttu-id="ba491-117">使用 [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) 與 [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331) 將項目上傳到資源庫</span><span class="sxs-lookup"><span data-stu-id="ba491-117">Upload items to the Gallery with [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) and [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span></span>
-   <span data-ttu-id="ba491-118">使用 [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668) 新增您自己的自訂存放庫</span><span class="sxs-lookup"><span data-stu-id="ba491-118">Add your own custom repository with [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span></span>

<span data-ttu-id="ba491-119">如需如何在資源庫使用 PowerShellGet 命令的詳細資訊，請查看[開始使用](psgallery/psgallery_gettingstarted.md)頁面。</span><span class="sxs-lookup"><span data-stu-id="ba491-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="ba491-120">您也可以執行 *Update-Help -Module PowerShellGet* 以安裝這些命令的本機說明。</span><span class="sxs-lookup"><span data-stu-id="ba491-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="ba491-121">支援的作業系統</span><span class="sxs-lookup"><span data-stu-id="ba491-121">Supported Operating Systems</span></span>

<span data-ttu-id="ba491-122">**PowerShellGet** 模組需要 **PowerShell 3.0 或更新版本**。</span><span class="sxs-lookup"><span data-stu-id="ba491-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="ba491-123">因此，**PowerShellGet** 需要下列其中一個作業系統：</span><span class="sxs-lookup"><span data-stu-id="ba491-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="ba491-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="ba491-124">Windows 10</span></span>
- <span data-ttu-id="ba491-125">Windows 8.1 專業版</span><span class="sxs-lookup"><span data-stu-id="ba491-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="ba491-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="ba491-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="ba491-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="ba491-127">Windows 7 SP1</span></span>
- <span data-ttu-id="ba491-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="ba491-128">Windows Server 2016</span></span>
- <span data-ttu-id="ba491-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ba491-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="ba491-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="ba491-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="ba491-131">**PowerShellGet** 也需要 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="ba491-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="ba491-132">您可以從[這裡](https://msdn.microsoft.com/library/5a4x27ek.aspx)安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="ba491-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="ba491-133">有任何問題嗎？</span><span class="sxs-lookup"><span data-stu-id="ba491-133">Got a question?</span></span> <span data-ttu-id="ba491-134">想提供任何意見？</span><span class="sxs-lookup"><span data-stu-id="ba491-134">Have feedback?</span></span>

<span data-ttu-id="ba491-135">如需 PowerShell 資源庫與 PowerShellGet 的詳細資料，請前往[開始使用](psgallery/psgallery_gettingstarted.md)頁面。</span><span class="sxs-lookup"><span data-stu-id="ba491-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="ba491-136">請使用 [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) 提供意見反應及回報問題。</span><span class="sxs-lookup"><span data-stu-id="ba491-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>

