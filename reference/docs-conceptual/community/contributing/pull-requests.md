---
title: 如何提交提取要求
description: 此文章說明如何將提取要求提交至 PowerShell-Docs 存放庫。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 8b392a36c9469b83cf4f088c1799720a091434b4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782645"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="936fb-103">如何提交提取要求</span><span class="sxs-lookup"><span data-stu-id="936fb-103">How to submit pull requests</span></span>

<span data-ttu-id="936fb-104">若要對內容進行變更，請從您的派生提交提取要求 (PR)。</span><span class="sxs-lookup"><span data-stu-id="936fb-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="936fb-105">所有提取要求都必須先經過審查，才能合併。</span><span class="sxs-lookup"><span data-stu-id="936fb-105">A pull request must be reviewed before it can merged.</span></span> <span data-ttu-id="936fb-106">為獲得最佳結果，請先檢閱[編輯檢查清單](editorial-checklist.md)，再提交您的提取要求。</span><span class="sxs-lookup"><span data-stu-id="936fb-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="target-the-correct-branch"></a><span data-ttu-id="936fb-107">以正確的分支為目標</span><span class="sxs-lookup"><span data-stu-id="936fb-107">Target the correct branch</span></span>

<span data-ttu-id="936fb-108">所有提取要求都應該以 `staging` 分支為目標。</span><span class="sxs-lookup"><span data-stu-id="936fb-108">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="936fb-109">一律不應該將變更提交至 `live` 分支。</span><span class="sxs-lookup"><span data-stu-id="936fb-109">Changes should never be submitted to the `live` branch.</span></span> <span data-ttu-id="936fb-110">在 `staging` 分支中所做的變更會合併到 `live` 中，並覆寫對 `live` 所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="936fb-110">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

<span data-ttu-id="936fb-111">如果您提交的變更僅適用於 PowerShell 的未發行版本，請檢查是否有該版本的發行分支。</span><span class="sxs-lookup"><span data-stu-id="936fb-111">If you are submitting a change that only applies to an unreleased version of PowerShell, check for a release branch for that version.</span></span> <span data-ttu-id="936fb-112">您的 PR 應以該發行分支為目標。</span><span class="sxs-lookup"><span data-stu-id="936fb-112">Your PR should be targeted at the release branch.</span></span> <span data-ttu-id="936fb-113">發行分支具有下列名稱模式：`release-<version>`。</span><span class="sxs-lookup"><span data-stu-id="936fb-113">Release branches have the following name pattern: `release-<version>`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="936fb-114">讓所有人都能更有效地使用提取要求程序</span><span class="sxs-lookup"><span data-stu-id="936fb-114">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="936fb-115">越簡單且明確的 PR，就能越快地檢閱及合併。</span><span class="sxs-lookup"><span data-stu-id="936fb-115">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-branches-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="936fb-116">避免更新大量檔案或包含不相關變更的分支</span><span class="sxs-lookup"><span data-stu-id="936fb-116">Avoid branches that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="936fb-117">避免建立包含不相關變更的 PR。</span><span class="sxs-lookup"><span data-stu-id="936fb-117">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="936fb-118">將現有文章的次要變更與新文章或主要重寫分開。</span><span class="sxs-lookup"><span data-stu-id="936fb-118">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="936fb-119">在個別工作分支中處理這些變更。</span><span class="sxs-lookup"><span data-stu-id="936fb-119">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="936fb-120">大量變更會建立有大量已變更檔案的 PR。</span><span class="sxs-lookup"><span data-stu-id="936fb-120">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="936fb-121">將您的 PR 限制為最多 50 個已變更的檔案。</span><span class="sxs-lookup"><span data-stu-id="936fb-121">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="936fb-122">大型 PR 難以檢閱，而且更容易包含錯誤。</span><span class="sxs-lookup"><span data-stu-id="936fb-122">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="936fb-123">重新命名或刪除檔案</span><span class="sxs-lookup"><span data-stu-id="936fb-123">Renaming or deleting files</span></span>

<span data-ttu-id="936fb-124">如果您要重新命名或刪除檔案，必須有與該 PR 相關聯的問題。</span><span class="sxs-lookup"><span data-stu-id="936fb-124">If you are renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="936fb-125">該問題必須討論重新命名或刪除檔案的需求。</span><span class="sxs-lookup"><span data-stu-id="936fb-125">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="936fb-126">避免混合增加內容或檔案重新命名及刪除的變更。</span><span class="sxs-lookup"><span data-stu-id="936fb-126">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="936fb-127">已重新命名或刪除的任何檔案，都必須新增至主要重新導向檔案。</span><span class="sxs-lookup"><span data-stu-id="936fb-127">Any file that is renamed or deleted must be added to the master redirection file.</span></span> <span data-ttu-id="936fb-128">可能的話，您也應該更新連結至已重新命名或已刪除內容的任何檔案。</span><span class="sxs-lookup"><span data-stu-id="936fb-128">When possible, you should also update any files that link to the renamed or deleted content.</span></span> <span data-ttu-id="936fb-129">這包含任何目錄檔案。</span><span class="sxs-lookup"><span data-stu-id="936fb-129">This includes any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="936fb-130">Docs PR 驗證服務</span><span class="sxs-lookup"><span data-stu-id="936fb-130">Docs PR validation service</span></span>

<span data-ttu-id="936fb-131">Docs PR 驗證服務是 GitHub 應用程式，可對 PR 中的檔案執行驗證規則。</span><span class="sxs-lookup"><span data-stu-id="936fb-131">The Docs PR validation service is a GitHub app that runs validation rules on the files in a PR.</span></span> <span data-ttu-id="936fb-132">您必須修正驗證服務所報告的任何錯誤或警告 (請參閱例外狀況)。</span><span class="sxs-lookup"><span data-stu-id="936fb-132">You must fix any errors or warnings (see exceptions) reported by the validation service.</span></span>

<span data-ttu-id="936fb-133">可以忽略下列警告：</span><span class="sxs-lookup"><span data-stu-id="936fb-133">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="936fb-134">您將看見下列行為：</span><span class="sxs-lookup"><span data-stu-id="936fb-134">You'll see the following behavior:</span></span>

1. <span data-ttu-id="936fb-135">您提交 PR。</span><span class="sxs-lookup"><span data-stu-id="936fb-135">You submit a PR.</span></span>
1. <span data-ttu-id="936fb-136">在指出 PR 狀態的 GitHub 註解中，您會看到存放庫已啟用「檢查」狀態。</span><span class="sxs-lookup"><span data-stu-id="936fb-136">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repository.</span></span> <span data-ttu-id="936fb-137">請注意，在此範例中，已啟用兩個檢查，「認可驗證」與 "OpenPublishing.Build"：</span><span class="sxs-lookup"><span data-stu-id="936fb-137">Note that in this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![驗證狀態 - 部分檢查失敗](media/pull-requests/validation-failed.png)

   <span data-ttu-id="936fb-139">即使認可驗證失敗，建置也可以通過。</span><span class="sxs-lookup"><span data-stu-id="936fb-139">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="936fb-140">如需詳細資訊，請按一下 [Details]  \(詳細資料\)。</span><span class="sxs-lookup"><span data-stu-id="936fb-140">Click **Details** for more information.</span></span>
1. <span data-ttu-id="936fb-141">在 [Details] \(詳細資料\) 頁面上，您會看到所有失敗的驗證檢查，以及如何修正問題的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="936fb-141">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="936fb-142">驗證成功時，系統會將下列留言新增至 PR：</span><span class="sxs-lookup"><span data-stu-id="936fb-142">When validation succeeds, the following comment is added to the PR:</span></span>

   ![驗證狀態：成功](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="936fb-144">如果您是外部 (不是 Microsoft 員工) 參與者，則無法存取詳細的建置報告或預覽連結。</span><span class="sxs-lookup"><span data-stu-id="936fb-144">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="936fb-145">當 PR 是由 PowerShell-Docs 小組的成員審查時，該人員可能會要求您進行變更或修正由驗證報告標示的問題。</span><span class="sxs-lookup"><span data-stu-id="936fb-145">When the PR is reviewed by a member of the PowerShell-Docs team, you may be asked to make changes or fix problems flagged by the validation report.</span></span> <span data-ttu-id="936fb-146">PowerShell-Docs 小組可以協助您了解如何修正及避免未來提交的這些問題。</span><span class="sxs-lookup"><span data-stu-id="936fb-146">The PowerShell-Docs team can help you understand how to fix and avoid these problems for future submissions.</span></span>

## <a name="next-steps"></a><span data-ttu-id="936fb-147">後續步驟</span><span class="sxs-lookup"><span data-stu-id="936fb-147">Next steps</span></span>

[<span data-ttu-id="936fb-148">PowerShell-Docs 樣式指南</span><span class="sxs-lookup"><span data-stu-id="936fb-148">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="936fb-149">其他資源</span><span class="sxs-lookup"><span data-stu-id="936fb-149">Additional resources</span></span>

[<span data-ttu-id="936fb-150">我們管理提取要求的方式</span><span class="sxs-lookup"><span data-stu-id="936fb-150">How we manage pull requests</span></span>](managing-pull-requests.md)
