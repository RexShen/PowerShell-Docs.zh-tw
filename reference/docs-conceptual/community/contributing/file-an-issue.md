---
title: 如何提出 PowerShell-Docs 問題
description: 此文章說明提供 PowerShell 文件相關意見反應的方式。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: fa2c74d55cdcd779646c50d58f7705f7a4c33542
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060293"
---
# <a name="how-to-file-a-powershell-docs-issue"></a><span data-ttu-id="446d3-103">如何提出 PowerShell-Docs 問題</span><span class="sxs-lookup"><span data-stu-id="446d3-103">How to file a PowerShell-Docs issue</span></span>

<span data-ttu-id="446d3-104">有兩種方式可以建立問題：</span><span class="sxs-lookup"><span data-stu-id="446d3-104">There are two ways to create an issue:</span></span>

1. <span data-ttu-id="446d3-105">使用頁面底部的意見反應控制項。</span><span class="sxs-lookup"><span data-stu-id="446d3-105">Use the feedback controls at the bottom of the page.</span></span>
1. <span data-ttu-id="446d3-106">直接在 GitHub 中提出問題</span><span class="sxs-lookup"><span data-stu-id="446d3-106">File an issue in GitHub directly</span></span>

## <a name="using-the-feedback-controls"></a><span data-ttu-id="446d3-107">使用意見反應控制項</span><span class="sxs-lookup"><span data-stu-id="446d3-107">Using the feedback controls</span></span>

<span data-ttu-id="446d3-108">如需意見反應控制項的完整說明，請參閱宣佈此[功能][feedback]的 Docs 小組部落格。</span><span class="sxs-lookup"><span data-stu-id="446d3-108">For a full description of the feedback controls, see the Docs Team blog announcing this [feature][feedback].</span></span>

<span data-ttu-id="446d3-109">在 `docs.microsoft.com` 上大部分頁面的底部，您將會看到兩個意見反應按鈕。</span><span class="sxs-lookup"><span data-stu-id="446d3-109">At the bottom of most pages on `docs.microsoft.com`, you'll see two feedback buttons.</span></span> <span data-ttu-id="446d3-110">一個是產品意見反應的連結，另一個則是文件意見反應的連結。</span><span class="sxs-lookup"><span data-stu-id="446d3-110">One is a link for product feedback and one is for documentation feedback.</span></span> <span data-ttu-id="446d3-111">提供文件意見反應需要 GitHub 帳戶。</span><span class="sxs-lookup"><span data-stu-id="446d3-111">The documentation feedback requires a GitHub account.</span></span> <span data-ttu-id="446d3-112">按一下該按鈕會在 GitHub 中驗證您，然後呈現簡單的表單供您輸入意見反應。</span><span class="sxs-lookup"><span data-stu-id="446d3-112">Clicking the button authenticates you in GitHub, then presents a simple form to enter your feedback.</span></span> <span data-ttu-id="446d3-113">當您提交表單時，意見反應控制項會建立新的 GitHub 問題，並將其連結到目前的文章。</span><span class="sxs-lookup"><span data-stu-id="446d3-113">When you submit the form, the feedback control creates a new GitHub issue and links it to the current article.</span></span>

> [!NOTE]
> <span data-ttu-id="446d3-114">這並不是支援管道。</span><span class="sxs-lookup"><span data-stu-id="446d3-114">This is not a support channel.</span></span> <span data-ttu-id="446d3-115">這是用來詢問文件的相關釐清問題，或回報錯誤及遺漏的方法。</span><span class="sxs-lookup"><span data-stu-id="446d3-115">This is a way to ask clarifying questions about documentation or report errors and omissions.</span></span> <span data-ttu-id="446d3-116">如果您需要技術支援，請參閱[社群資源](../community-support.md)。</span><span class="sxs-lookup"><span data-stu-id="446d3-116">If you need technical support, see [Community resources](../community-support.md).</span></span>

## <a name="filing-issues-on-github"></a><span data-ttu-id="446d3-117">在 GitHub 上提出問題</span><span class="sxs-lookup"><span data-stu-id="446d3-117">Filing issues on GitHub</span></span>

<span data-ttu-id="446d3-118">若要直接提出 GitHub 問題，您可以在 [PowerShell-Docs][docs-issues] 存放庫中按一下 [[New issue]][new-issue] \(新增問題\) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="446d3-118">To file a GitHub issue directly, you can click on the [New issue][new-issue] button in the [PowerShell-Docs][docs-issues] repository.</span></span> <span data-ttu-id="446d3-119">針對您想要建立的問題類型，按一下 [Get started]  \(開始使用\) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="446d3-119">Click the **Get started** button for the type of issue you want to create.</span></span> <span data-ttu-id="446d3-120">新的 GitHub 問題會使用範本預先填入。</span><span class="sxs-lookup"><span data-stu-id="446d3-120">The new GitHub issue is prepopulated with a template.</span></span> <span data-ttu-id="446d3-121">範本會協助您提供處理您所回報問題所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="446d3-121">The template helps you provide the information needed to address the problem you're reporting.</span></span>

<span data-ttu-id="446d3-122">在您提出新問題之前，請先閱讀現有的問題，以確認是否已經有人回報您的問題。</span><span class="sxs-lookup"><span data-stu-id="446d3-122">Before you file a new issue, read through existing issues to see if your problem has already been reported.</span></span> <span data-ttu-id="446d3-123">這可協助避免重複，且您的問題可能已經獲得解答。</span><span class="sxs-lookup"><span data-stu-id="446d3-123">This helps avoid duplication and your issue may have been answered already.</span></span> <span data-ttu-id="446d3-124">如果您找到現有問題，您可以加入留言、相關的問題，或是解答。</span><span class="sxs-lookup"><span data-stu-id="446d3-124">If you find an existing issue, you can add your comments, related questions, or answers.</span></span>

## <a name="next-steps"></a><span data-ttu-id="446d3-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="446d3-125">Next steps</span></span>

<span data-ttu-id="446d3-126">請參閱[開始撰寫](get-started-writing.md)。</span><span class="sxs-lookup"><span data-stu-id="446d3-126">See [Get started writing](get-started-writing.md).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="446d3-127">其他資源</span><span class="sxs-lookup"><span data-stu-id="446d3-127">Additional resources</span></span>

[<span data-ttu-id="446d3-128">我們管理問題的方式</span><span class="sxs-lookup"><span data-stu-id="446d3-128">How we manage issues</span></span>](managing-issues.md)

<!-- reference links -->
[feedback]: /teamblog/a-new-feedback-system-is-coming-to-docs
[new-issue]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/new/choose
[docs-issues]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues
