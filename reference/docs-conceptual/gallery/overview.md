---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 資源庫,powershell,cmdlet,psgallery,psget
title: PowerShell 資源庫
ms.openlocfilehash: e489d2dd4db087b53eb07d2a8793c8f586c9b210
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500571"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="b25f1-103">PowerShell 資源庫</span><span class="sxs-lookup"><span data-stu-id="b25f1-103">The PowerShell Gallery</span></span>

<span data-ttu-id="b25f1-104">PowerShell 資源庫是 PowerShell 內容的集中存放庫。</span><span class="sxs-lookup"><span data-stu-id="b25f1-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="b25f1-105">您可以在其中找到包含 PowerShell 命令或預期狀態設定 (DSC) 資源的有用 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="b25f1-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="b25f1-106">您也可以尋找 PowerShell 指令碼，其中有些可能會包含 PowerShell 工作流程，有些則概述一組工作並提供這些工作的序列。</span><span class="sxs-lookup"><span data-stu-id="b25f1-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="b25f1-107">這些套件有一部分是由 Microsoft 所撰寫，其他則是由 PowerShell 社群所撰寫。</span><span class="sxs-lookup"><span data-stu-id="b25f1-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="b25f1-108">PowerShellGet 概觀</span><span class="sxs-lookup"><span data-stu-id="b25f1-108">PowerShellGet Overview</span></span>

<span data-ttu-id="b25f1-109">PowerShellGet 模組包含適用於探索、安裝、更新及發行 PowerShell 套件的 Cmdlet，其包含來自 [PowerShell 資源庫](https://www.PowerShellGallery.com) \(英文\) 及其他私用存放庫的成品，例如模組、DSC 資源、角色功能與指令碼。</span><span class="sxs-lookup"><span data-stu-id="b25f1-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="b25f1-110">開始使用資源庫</span><span class="sxs-lookup"><span data-stu-id="b25f1-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="b25f1-111">從資源庫安裝套件需要最新版本的 PowerShellGet 模組。</span><span class="sxs-lookup"><span data-stu-id="b25f1-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span> <span data-ttu-id="b25f1-112">請參閱[安裝 PowerShellGet](installing-psget.md) 以取得完整的指示。</span><span class="sxs-lookup"><span data-stu-id="b25f1-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="b25f1-113">如需如何在資源庫使用 PowerShellGet 命令的詳細資訊，請查看[開始使用](getting-started.md)頁面。</span><span class="sxs-lookup"><span data-stu-id="b25f1-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="b25f1-114">您也可以執行 *Update-Help -Module PowerShellGet* 以安裝這些命令的本機說明。</span><span class="sxs-lookup"><span data-stu-id="b25f1-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="b25f1-115">支援的作業系統</span><span class="sxs-lookup"><span data-stu-id="b25f1-115">Supported Operating Systems</span></span>

<span data-ttu-id="b25f1-116">**PowerShellGet** 模組需要 **PowerShell 3.0 或更新版本**。</span><span class="sxs-lookup"><span data-stu-id="b25f1-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="b25f1-117">**PowerShellGet** 需要 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="b25f1-117">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="b25f1-118">您可以從[這裡](https://msdn.microsoft.com/library/5a4x27ek.aspx)安裝 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="b25f1-118">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="b25f1-119">由於 **PowerShell Core** 的跨平台特性，使它能在 Windows、Linux 和 MacOS 上運作，這也代表 **PowerShellGet** 可在那些系統上使用。</span><span class="sxs-lookup"><span data-stu-id="b25f1-119">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="b25f1-120">如需 **PowerShell Core** 所支援之系統的完整清單，請參閱[安裝 PowerShell](/powershell/scripting/install/installing-powershell)。</span><span class="sxs-lookup"><span data-stu-id="b25f1-120">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/install/installing-powershell).</span></span>

<span data-ttu-id="b25f1-121">資源庫中裝載的眾多模組將會支援不同的 OS 並具有額外的需求。</span><span class="sxs-lookup"><span data-stu-id="b25f1-121">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span>
<span data-ttu-id="b25f1-122">如需詳細資訊，請參考模組的文件。</span><span class="sxs-lookup"><span data-stu-id="b25f1-122">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="b25f1-123">有任何問題嗎？</span><span class="sxs-lookup"><span data-stu-id="b25f1-123">Got a question?</span></span> <span data-ttu-id="b25f1-124">想提供任何意見？</span><span class="sxs-lookup"><span data-stu-id="b25f1-124">Have feedback?</span></span>

<span data-ttu-id="b25f1-125">如需 PowerShell 資源庫與 PowerShellGet 的詳細資料，請前往[開始使用](getting-started.md)頁面。</span><span class="sxs-lookup"><span data-stu-id="b25f1-125">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="b25f1-126">請使用 [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) 提供意見反應及回報問題。</span><span class="sxs-lookup"><span data-stu-id="b25f1-126">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
