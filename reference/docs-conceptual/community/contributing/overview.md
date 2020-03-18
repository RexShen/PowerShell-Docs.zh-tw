---
title: 對 PowerShell 文件做出貢獻
description: 此文章是如何以 PowerShell 文件參與者身分開始貢獻的概觀。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 5db78ae2805cb26aa79aa698cfb8b5d8ba8911dc
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402625"
---
# <a name="contributing-to-powershell-documentation"></a><span data-ttu-id="078eb-103">對 PowerShell 文件做出貢獻</span><span class="sxs-lookup"><span data-stu-id="078eb-103">Contributing to PowerShell documentation</span></span>

<span data-ttu-id="078eb-104">感謝您支援 PowerShell！</span><span class="sxs-lookup"><span data-stu-id="078eb-104">Thank you for your support of PowerShell!</span></span>

<span data-ttu-id="078eb-105">《參與者指南》是一系列文章，說明我們在 Microsoft 建立文件時所用的工具與程式。</span><span class="sxs-lookup"><span data-stu-id="078eb-105">The Contributor's Guide is a collection of articles that explain the tools and processes we use to create documentation at Microsoft.</span></span> <span data-ttu-id="078eb-106">某些指南涵蓋了所有發行至 [docs.microsoft.com][docs] 之文件集的通用資訊。</span><span class="sxs-lookup"><span data-stu-id="078eb-106">Some of these guides cover information that is common to any documentation set published to [docs.microsoft.com][docs].</span></span> <span data-ttu-id="078eb-107">某些指南是關於我們如何撰寫 PowerShell 文件的專屬內容。</span><span class="sxs-lookup"><span data-stu-id="078eb-107">Some of the guides are specific to how we write documentation for PowerShell.</span></span>

<span data-ttu-id="078eb-108">您可以在我們的集中式[參與者指南][contribute]中找到一般文章。</span><span class="sxs-lookup"><span data-stu-id="078eb-108">The common articles are available in our centralized [Contributor's Guide][contribute].</span></span> <span data-ttu-id="078eb-109">這裡提供 PowerShell 專屬指南。</span><span class="sxs-lookup"><span data-stu-id="078eb-109">The PowerShell-specific guides are available here.</span></span>

## <a name="ways-to-contribute"></a><span data-ttu-id="078eb-110">參與方法</span><span class="sxs-lookup"><span data-stu-id="078eb-110">Ways to contribute</span></span>

<span data-ttu-id="078eb-111">做出貢獻的方式有兩種：</span><span class="sxs-lookup"><span data-stu-id="078eb-111">There are two ways to contribute.</span></span> <span data-ttu-id="078eb-112">這兩個貢獻對我們而言很重要。</span><span class="sxs-lookup"><span data-stu-id="078eb-112">Both contributions are valuable to us.</span></span>

- <span data-ttu-id="078eb-113">[提出問題][file-an-issue]，以協助我們找出文件中的問題與缺口。</span><span class="sxs-lookup"><span data-stu-id="078eb-113">[Filing issues][file-an-issue] helps us identify problems and gaps in our documentation.</span></span> <span data-ttu-id="078eb-114">有時候問題不好解決，需要進行更多調查及研究。</span><span class="sxs-lookup"><span data-stu-id="078eb-114">Sometimes the issues are difficult to resolve, requiring more investigation and research.</span></span> <span data-ttu-id="078eb-115">問題程序可讓我們對問題進行交談，並開發出滿意的解決方式。</span><span class="sxs-lookup"><span data-stu-id="078eb-115">The issue process allows us to have a conversation about the problem and develop a satisfactory resolution.</span></span>

- <span data-ttu-id="078eb-116">提交新內容或現有文章的變更是更複雜的程序。</span><span class="sxs-lookup"><span data-stu-id="078eb-116">Submitting new content or changes to existing articles is a more involved process.</span></span> <span data-ttu-id="078eb-117">下列資訊概述用於將內容提交至文件的工具、程序與標準。</span><span class="sxs-lookup"><span data-stu-id="078eb-117">The following information outlines the tools, processes, and standards for submitting content to the documentation.</span></span>

## <a name="prepare-to-make-a-contribution"></a><span data-ttu-id="078eb-118">準備做出貢獻</span><span class="sxs-lookup"><span data-stu-id="078eb-118">Prepare to make a contribution</span></span>

<span data-ttu-id="078eb-119">參與文件內容需要 GitHub 帳戶。</span><span class="sxs-lookup"><span data-stu-id="078eb-119">Contributing to the documentation requires a GitHub account.</span></span> <span data-ttu-id="078eb-120">使用下列檢查清單來取得工具，並了解我們用來做出貢獻的程序。</span><span class="sxs-lookup"><span data-stu-id="078eb-120">Use the following checklist to get the tools and understand the processes we use for making contributions.</span></span>

1. [<span data-ttu-id="078eb-121">註冊 GitHub</span><span class="sxs-lookup"><span data-stu-id="078eb-121">Sign up for GitHub</span></span>](/contribute/get-started-setup-github)
1. [<span data-ttu-id="078eb-122">安裝 Git 與 Markdown 工具</span><span class="sxs-lookup"><span data-stu-id="078eb-122">Install Git and Markdown tools</span></span>](/contribute/get-started-setup-tools)
1. [<span data-ttu-id="078eb-123">安裝文件編寫套件</span><span class="sxs-lookup"><span data-stu-id="078eb-123">Install the Docs Authoring Pack</span></span>](/contribute/how-to-write-docs-auth-pack)
1. <span data-ttu-id="078eb-124">[安裝 Posh-Git][posh-git] - 非必要，僅為建議</span><span class="sxs-lookup"><span data-stu-id="078eb-124">[Install Posh-Git][posh-git] - not required but recommended</span></span>
1. [<span data-ttu-id="078eb-125">設定本機 Git 存放庫</span><span class="sxs-lookup"><span data-stu-id="078eb-125">Set up a local Git repository</span></span>](/contribute/get-started-setup-local)
1. [<span data-ttu-id="078eb-126">檢閱 Git 與 GitHub 基本概念</span><span class="sxs-lookup"><span data-stu-id="078eb-126">Review Git and GitHub fundamentals</span></span>](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a><span data-ttu-id="078eb-127">開始撰寫文件</span><span class="sxs-lookup"><span data-stu-id="078eb-127">Get started writing docs</span></span>

<span data-ttu-id="078eb-128">有兩種方式可以參與文件的變更：</span><span class="sxs-lookup"><span data-stu-id="078eb-128">There are two ways to contribute changes to the documentation:</span></span>

1. [<span data-ttu-id="078eb-129">對現有文件進行快速編輯</span><span class="sxs-lookup"><span data-stu-id="078eb-129">Quick edits to existing docs</span></span>](/contribute/#quick-edits-to-existing-documents)
   - <span data-ttu-id="078eb-130">微幅修正、修正錯字或微幅新增</span><span class="sxs-lookup"><span data-stu-id="078eb-130">Minor corrections, fixing typos, or small additions</span></span>
1. [<span data-ttu-id="078eb-131">文件的完整 GitHub 工作流程</span><span class="sxs-lookup"><span data-stu-id="078eb-131">Full GitHub workflow for docs</span></span>](/contribute/how-to-write-workflows-major)
   - <span data-ttu-id="078eb-132">大幅變更、多個版本、新增或變更影像，或參與新文章編寫</span><span class="sxs-lookup"><span data-stu-id="078eb-132">large changes, multiple versions, adding or changing images, or contributing new articles</span></span>

<span data-ttu-id="078eb-133">此外，請參閱集中式《參與者指南》中的[編寫基本知識](/contribute/style-quick-start)一節。</span><span class="sxs-lookup"><span data-stu-id="078eb-133">Also, read the [Writing essentials](/contribute/style-quick-start) section of the centralized Contributor's Guide.</span></span> <span data-ttu-id="078eb-134">另一個絕佳的資源是 [Microsoft 寫作風格指南][style-guide]。</span><span class="sxs-lookup"><span data-stu-id="078eb-134">Another excellent resource is the [Microsoft Writing Style Guide][style-guide].</span></span> <span data-ttu-id="078eb-135">《Microsoft 寫作風格指南》的目標是協助編輯者、技術作者、開發人員、行銷人員以及 IT 中的其他人撰寫更好的內容。</span><span class="sxs-lookup"><span data-stu-id="078eb-135">The goal of the Microsoft Writing Style Guide is to help editors, technical writers, developers, marketers, and anyone else in IT write better content.</span></span>

<span data-ttu-id="078eb-136">您對此公用存放庫中之文件與程式碼範例所做的微幅修正或釐清，將受到 docs.microsoft.com [ 使用規定][terms-of-use]的約束。</span><span class="sxs-lookup"><span data-stu-id="078eb-136">Minor corrections or clarifications to documentation and code examples in public repositories are covered by the docs.microsoft.com [Terms of Use][terms-of-use].</span></span>

<span data-ttu-id="078eb-137">當您要進行大幅變更時，請使用完整的 GitHub 工作流程。</span><span class="sxs-lookup"><span data-stu-id="078eb-137">Use the full GitHub workflow when you're making significant changes.</span></span> <span data-ttu-id="078eb-138">如果您不是 Microsoft 的員工，大幅變更會在提取要求中產生註解，要求您提交線上[貢獻授權合約 (CLA)][cla]。</span><span class="sxs-lookup"><span data-stu-id="078eb-138">If you're not an employee of Microsoft, significant changes generate a comment in the pull request that asks you to submit an online [Contribution Licensing Agreement (CLA)][cla].</span></span> <span data-ttu-id="078eb-139">您必須先完成線上表單，我們才會審核或接受您的提取要求。</span><span class="sxs-lookup"><span data-stu-id="078eb-139">We need you to complete the online form before we can review or accept your pull request.</span></span>

## <a name="code-of-conduct"></a><span data-ttu-id="078eb-140">管理辦法</span><span class="sxs-lookup"><span data-stu-id="078eb-140">Code of conduct</span></span>

<span data-ttu-id="078eb-141">所有發佈到 docs.microsoft.com 的存放庫都採用 [Microsoft 開放原始碼管理辦法](https://opensource.microsoft.com/codeofconduct/) \(英文\) 或 [.NET Foundation 管理辦法](https://dotnetfoundation.org/code-of-conduct) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="078eb-141">All repositories that publish to docs.microsoft.com have adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) or the [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct).</span></span> <span data-ttu-id="078eb-142">如需詳細資訊，請參閱[管理辦法常見問題集](https://opensource.microsoft.com/codeofconduct/faq/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="078eb-142">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="078eb-143">後續步驟</span><span class="sxs-lookup"><span data-stu-id="078eb-143">Next steps</span></span>

<span data-ttu-id="078eb-144">下列文章涵蓋 PowerShell 文件的專屬資訊。</span><span class="sxs-lookup"><span data-stu-id="078eb-144">The following articles cover information specific to PowerShell documentation.</span></span> <span data-ttu-id="078eb-145">當與集中式《參與者指南》中的指導方針重疊時，我們會說明那些規則與 PowerShell 內容有何差異。</span><span class="sxs-lookup"><span data-stu-id="078eb-145">Where there's overlap with the guidance in the centralized Contributor's Guide, we call out how those rules differ for the PowerShell content.</span></span>

<span data-ttu-id="078eb-146">請檢閱下列文件：</span><span class="sxs-lookup"><span data-stu-id="078eb-146">Review the following documents:</span></span>

- [<span data-ttu-id="078eb-147">如何提出問題</span><span class="sxs-lookup"><span data-stu-id="078eb-147">How to file an issue</span></span>](file-an-issue.md)
- [<span data-ttu-id="078eb-148">開始編寫文件</span><span class="sxs-lookup"><span data-stu-id="078eb-148">Get started writing docs</span></span>](get-started-writing.md)
- [<span data-ttu-id="078eb-149">提交提取要求</span><span class="sxs-lookup"><span data-stu-id="078eb-149">Submitting a pull request</span></span>](pull-requests.md)
- [<span data-ttu-id="078eb-150">PowerShell-Docs 樣式指南</span><span class="sxs-lookup"><span data-stu-id="078eb-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)
- [<span data-ttu-id="078eb-151">編輯 Cmdlet 參考</span><span class="sxs-lookup"><span data-stu-id="078eb-151">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<span data-ttu-id="078eb-152">其他資源</span><span class="sxs-lookup"><span data-stu-id="078eb-152">Additional resources</span></span>

- [<span data-ttu-id="078eb-153">編輯檢查清單</span><span class="sxs-lookup"><span data-stu-id="078eb-153">Editorial checklist</span></span>](editorial-checklist.md)
- [<span data-ttu-id="078eb-154">我們管理問題的方式</span><span class="sxs-lookup"><span data-stu-id="078eb-154">How we manage issues</span></span>](managing-issues.md)
- [<span data-ttu-id="078eb-155">我們管理提取要求的方式</span><span class="sxs-lookup"><span data-stu-id="078eb-155">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: https://docs.microsoft.com/powershell
[style-guide]: https://docs.microsoft.com/style-guide/welcome/
[terms-of-use]: https://docs.microsoft.com/legal/termsofuse