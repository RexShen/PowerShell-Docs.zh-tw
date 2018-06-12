---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 資源庫,powershell,cmdlet,psgallery,psget
title: PowerShell 資源庫
ms.openlocfilehash: dc7e8dd7e4d96d8424a62cb3256c3164b63a3684
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482925"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="01b34-103">PowerShell 資源庫</span><span class="sxs-lookup"><span data-stu-id="01b34-103">The PowerShell Gallery</span></span>

<span data-ttu-id="01b34-104">PowerShell 資源庫是 PowerShell 內容的集中存放庫。</span><span class="sxs-lookup"><span data-stu-id="01b34-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="01b34-105">您可以在其中找到包含 PowerShell 命令或預期狀態設定 (DSC) 資源的有用 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="01b34-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="01b34-106">您也可以尋找 PowerShell 指令碼，其中有些可能會包含 PowerShell 工作流程，有些則概述一組工作並提供這些工作的序列。</span><span class="sxs-lookup"><span data-stu-id="01b34-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="01b34-107">這些項目有一部分是由 Microsoft 所撰寫，其他則是由 PowerShell 社群所撰寫。</span><span class="sxs-lookup"><span data-stu-id="01b34-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="01b34-108">PowerShellGet 概觀</span><span class="sxs-lookup"><span data-stu-id="01b34-108">PowerShellGet Overview</span></span>

<span data-ttu-id="01b34-109">PowerShellGet 模組包含來自 [PowerShell 資源庫](https://www.PowerShellGallery.com)及其他私用存放庫，用於探索、安裝、更新及發行 PowerShell 成品 (例如模組、DSC 資源、角色功能與指令碼) 的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="01b34-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="01b34-110">開始使用資源庫</span><span class="sxs-lookup"><span data-stu-id="01b34-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="01b34-111">從資源庫安裝項目需要最新版本的 PowerShellGet 模組。</span><span class="sxs-lookup"><span data-stu-id="01b34-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="01b34-112">請參閱[安裝 PowerShellGet](installing-psget.md) 以取得完整的指示。</span><span class="sxs-lookup"><span data-stu-id="01b34-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="01b34-113">如需如何在資源庫使用 PowerShellGet 命令的詳細資訊，請查看[開始使用](getting-started.md)頁面。</span><span class="sxs-lookup"><span data-stu-id="01b34-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="01b34-114">您也可以執行 *Update-Help -Module PowerShellGet* 以安裝這些命令的本機說明。</span><span class="sxs-lookup"><span data-stu-id="01b34-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="01b34-115">支援的作業系統</span><span class="sxs-lookup"><span data-stu-id="01b34-115">Supported Operating Systems</span></span>

<span data-ttu-id="01b34-116">**PowerShellGet** 模組需要 **Windows PowerShell 3.0 或更新版本**，或是 **PowerShell Core 6.0 或更新版本**。</span><span class="sxs-lookup"><span data-stu-id="01b34-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="01b34-117">下列作業系統都有適用的 **Windows PowerShell** 版本：</span><span class="sxs-lookup"><span data-stu-id="01b34-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="01b34-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="01b34-118">Windows 10</span></span>
- <span data-ttu-id="01b34-119">Windows 8.1 專業版</span><span class="sxs-lookup"><span data-stu-id="01b34-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="01b34-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="01b34-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="01b34-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="01b34-121">Windows 7 SP1</span></span>
- <span data-ttu-id="01b34-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="01b34-122">Windows Server 2016</span></span>
- <span data-ttu-id="01b34-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="01b34-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="01b34-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="01b34-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="01b34-125">**PowerShellGet** 也需要 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="01b34-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="01b34-126">您可以從[這裡](https://msdn.microsoft.com/library/5a4x27ek.aspx)安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="01b34-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="01b34-127">**PowerShell Core** 支援許多作業系統。</span><span class="sxs-lookup"><span data-stu-id="01b34-127">**PowerShell Core** supports many operating systems.</span></span> <span data-ttu-id="01b34-128">如需完整的清單，請參閱[這篇文章](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/)。</span><span class="sxs-lookup"><span data-stu-id="01b34-128">See [this article](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) for a full list.</span></span>

<span data-ttu-id="01b34-129">資源庫中裝載的眾多模組將會支援不同的 OS 並具有額外的需求。</span><span class="sxs-lookup"><span data-stu-id="01b34-129">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="01b34-130">如需詳細資訊，請參考模組的文件。</span><span class="sxs-lookup"><span data-stu-id="01b34-130">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="01b34-131">有任何問題嗎？</span><span class="sxs-lookup"><span data-stu-id="01b34-131">Got a question?</span></span> <span data-ttu-id="01b34-132">想提供任何意見？</span><span class="sxs-lookup"><span data-stu-id="01b34-132">Have feedback?</span></span>

<span data-ttu-id="01b34-133">如需 PowerShell 資源庫與 PowerShellGet 的詳細資料，請前往[開始使用](getting-started.md)頁面。</span><span class="sxs-lookup"><span data-stu-id="01b34-133">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="01b34-134">請使用 [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) 提供意見反應及回報問題。</span><span class="sxs-lookup"><span data-stu-id="01b34-134">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
