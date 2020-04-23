---
title: 我們管理提取要求的方式
description: 此文章說明 PowerShell-Docs 小組管理提取要求的方式。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b9b37816dfdf38e4d8b7c2d66799164d0e97d257
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "79060383"
---
# <a name="managing-pull-requests"></a><span data-ttu-id="b26b4-103">管理提取要求</span><span class="sxs-lookup"><span data-stu-id="b26b4-103">Managing pull requests</span></span>

<span data-ttu-id="b26b4-104">此文章記錄我們管理 PowerShell-Docs 存放庫中提取要求的方式。</span><span class="sxs-lookup"><span data-stu-id="b26b4-104">This article documents how we manage pull requests in the PowerShell-Docs repo.</span></span> <span data-ttu-id="b26b4-105">此文章是設計來輔助 PowerShell-Docs 小組成員的工作之用。</span><span class="sxs-lookup"><span data-stu-id="b26b4-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="b26b4-106">在此發佈的原因，是為了向我們的公共參與者提供流程上的透明度。</span><span class="sxs-lookup"><span data-stu-id="b26b4-106">It is published here to provide process transparency for our public contributors.</span></span>

## <a name="best-practices"></a><span data-ttu-id="b26b4-107">最佳作法</span><span class="sxs-lookup"><span data-stu-id="b26b4-107">Best practices</span></span>

- <span data-ttu-id="b26b4-108">提交 PR 的人員不應該在沒有進行同儕審查的情況下合併該 PR。</span><span class="sxs-lookup"><span data-stu-id="b26b4-108">The person submitting the PR should not merge the PR without a peer review.</span></span>
- <span data-ttu-id="b26b4-109">在提交 PR 時指派同儕審查者。</span><span class="sxs-lookup"><span data-stu-id="b26b4-109">Assign the peer reviewer when the PR is submitted.</span></span> <span data-ttu-id="b26b4-110">早期指派能讓審查者透過編輯備註儘早回應。</span><span class="sxs-lookup"><span data-stu-id="b26b4-110">Early assignment allows the reviewer to respond sooner with editorial remarks.</span></span>
- <span data-ttu-id="b26b4-111">使用留言來描述變更的本質，或是所要求的審查類型。</span><span class="sxs-lookup"><span data-stu-id="b26b4-111">Use comments to describe the nature of the change or the type of review being requested.</span></span> <span data-ttu-id="b26b4-112">請務必對審查者進行 @mention。</span><span class="sxs-lookup"><span data-stu-id="b26b4-112">Be sure to @mention the reviewer.</span></span> <span data-ttu-id="b26b4-113">例如，如果變更為微幅性質，且您不需要完整的技術審查，請在留言中說明此情況。</span><span class="sxs-lookup"><span data-stu-id="b26b4-113">For example, if the change is minor and you don't need a full technical review, explain this in a comment.</span></span>

## <a name="pr-process-steps"></a><span data-ttu-id="b26b4-114">PR 程序步驟</span><span class="sxs-lookup"><span data-stu-id="b26b4-114">PR Process steps</span></span>

1. <span data-ttu-id="b26b4-115">作者：建立 PR</span><span class="sxs-lookup"><span data-stu-id="b26b4-115">Writer: Create PR</span></span>
   - <span data-ttu-id="b26b4-116">連結由 PR 所解決的任何問題</span><span class="sxs-lookup"><span data-stu-id="b26b4-116">Link any issues resolved by the PR</span></span>
   - <span data-ttu-id="b26b4-117">使用 GitHub 的[自動關閉](https://help.github.com/en/articles/closing-issues-using-keywords) \(英文\) 功能來關閉問題</span><span class="sxs-lookup"><span data-stu-id="b26b4-117">Use GitHub's [autoclose](https://help.github.com/en/articles/closing-issues-using-keywords) feature to close the issue</span></span>
1. <span data-ttu-id="b26b4-118">作者：指派同儕審查者</span><span class="sxs-lookup"><span data-stu-id="b26b4-118">Writer: Assign peer reviewer</span></span>
1. <span data-ttu-id="b26b4-119">審查者：校對及留言 (視需要)</span><span class="sxs-lookup"><span data-stu-id="b26b4-119">Reviewer: proofreads and comments (as necessary)</span></span>
1. <span data-ttu-id="b26b4-120">作者：納入審查意見反應</span><span class="sxs-lookup"><span data-stu-id="b26b4-120">Writer: Incorporate review feedback</span></span>
1. <span data-ttu-id="b26b4-121">Both (兩者)：審查預覽呈現</span><span class="sxs-lookup"><span data-stu-id="b26b4-121">Both: Review preview rendering</span></span>
1. <span data-ttu-id="b26b4-122">Both (兩者)：審查驗證報告，修正警告與錯誤</span><span class="sxs-lookup"><span data-stu-id="b26b4-122">Both: Review validation report - fix warnings and errors</span></span>
1. <span data-ttu-id="b26b4-123">作者：加入結案留言 (包括 Acrolinx 資訊)</span><span class="sxs-lookup"><span data-stu-id="b26b4-123">Writer: Add sign-off comment (include Acrolinx info)</span></span>
1. <span data-ttu-id="b26b4-124">審查者：將審查標示為「已核准」</span><span class="sxs-lookup"><span data-stu-id="b26b4-124">Reviewer: Mark review "Approved"</span></span>
1. <span data-ttu-id="b26b4-125">存放庫管理員：合併 PR (請參閱下文以取得準則)</span><span class="sxs-lookup"><span data-stu-id="b26b4-125">Repo Admin: Merge PR (see below for criteria)</span></span>

## <a name="content-reviewer-checklist"></a><span data-ttu-id="b26b4-126">內容審查者檢查清單</span><span class="sxs-lookup"><span data-stu-id="b26b4-126">Content Reviewer Checklist</span></span>

<span data-ttu-id="b26b4-127">請參閱[編輯檢查清單](editorial-checklist.md)以取得更完整的清單。</span><span class="sxs-lookup"><span data-stu-id="b26b4-127">See the [editorial checklist](editorial-checklist.md) for a more comprehensive list.</span></span>

- <span data-ttu-id="b26b4-128">針對文法、樣式、簡潔、技術準確度進行校對</span><span class="sxs-lookup"><span data-stu-id="b26b4-128">Proofread for grammar, style, concision, technical accuracy</span></span>
- <span data-ttu-id="b26b4-129">確保範例仍適用於目標版本</span><span class="sxs-lookup"><span data-stu-id="b26b4-129">Ensure examples still apply for the target version</span></span>
- <span data-ttu-id="b26b4-130">檢查預覽呈現</span><span class="sxs-lookup"><span data-stu-id="b26b4-130">Check Preview rendering</span></span>
- <span data-ttu-id="b26b4-131">檢查中繼資料：ms.date、移除 ms.assetid、確定必要欄位</span><span class="sxs-lookup"><span data-stu-id="b26b4-131">Check metadata - ms.date, remove ms.assetid, ensure required fields</span></span>
- <span data-ttu-id="b26b4-132">驗證 Markdown 正確性</span><span class="sxs-lookup"><span data-stu-id="b26b4-132">Validate markdown correctness</span></span>
  - <span data-ttu-id="b26b4-133">參閱樣式指南以取得格式特定內容</span><span class="sxs-lookup"><span data-stu-id="b26b4-133">See style guide for formatting specific content</span></span>
- <span data-ttu-id="b26b4-134">依下列項目重新組織範例：</span><span class="sxs-lookup"><span data-stu-id="b26b4-134">Reorganize examples as follows:</span></span>
  - <span data-ttu-id="b26b4-135">簡介文句</span><span class="sxs-lookup"><span data-stu-id="b26b4-135">Intro sentence(s)</span></span>
  - <span data-ttu-id="b26b4-136">程式碼與輸出</span><span class="sxs-lookup"><span data-stu-id="b26b4-136">Code and output</span></span>
  - <span data-ttu-id="b26b4-137">程式碼的詳細說明 (視需要)</span><span class="sxs-lookup"><span data-stu-id="b26b4-137">Detailed explanation of code (as necessary)</span></span>
- <span data-ttu-id="b26b4-138">檢查超連結的正確性</span><span class="sxs-lookup"><span data-stu-id="b26b4-138">Check hyperlinks for accuracy</span></span>
  - <span data-ttu-id="b26b4-139">取代或移除 TechNet/MSDN 連結</span><span class="sxs-lookup"><span data-stu-id="b26b4-139">Replace or remove TechNet/MSDN links</span></span>
  - <span data-ttu-id="b26b4-140">確定連到目標的重新導向數目為最低</span><span class="sxs-lookup"><span data-stu-id="b26b4-140">Ensure minimum number of redirects to target</span></span>
  - <span data-ttu-id="b26b4-141">確定 HTTPS</span><span class="sxs-lookup"><span data-stu-id="b26b4-141">Ensure HTTPS</span></span>
  - <span data-ttu-id="b26b4-142">修正連結類型</span><span class="sxs-lookup"><span data-stu-id="b26b4-142">Correct link type</span></span>
    - <span data-ttu-id="b26b4-143">針對本機檔案使用檔案連結</span><span class="sxs-lookup"><span data-stu-id="b26b4-143">File links for local files</span></span>
    - <span data-ttu-id="b26b4-144">針對位於 DocSet 外部的檔案使用 URL 連結</span><span class="sxs-lookup"><span data-stu-id="b26b4-144">URL links for files outside of the docset</span></span>
  - <span data-ttu-id="b26b4-145">從 URL 移除地區設定</span><span class="sxs-lookup"><span data-stu-id="b26b4-145">Remove locales from URLs</span></span>
  - <span data-ttu-id="b26b4-146">簡化指向 `docs.microsoft.com` 的 URL</span><span class="sxs-lookup"><span data-stu-id="b26b4-146">Simplify URLs pointing to `docs.microsoft.com`</span></span>

## <a name="branch-merge-process"></a><span data-ttu-id="b26b4-147">分支合併程序</span><span class="sxs-lookup"><span data-stu-id="b26b4-147">Branch Merge Process</span></span>

<span data-ttu-id="b26b4-148">暫存分支是唯一應該合併到作用中分支的分支。</span><span class="sxs-lookup"><span data-stu-id="b26b4-148">The staging branch is the only branch that should ever be merged into live.</span></span> <span data-ttu-id="b26b4-149">應該要壓縮從短期 (Working) 分支進行的合併。</span><span class="sxs-lookup"><span data-stu-id="b26b4-149">Merges from short-lived (working) branches should be squashed.</span></span>

| <span data-ttu-id="b26b4-150">合併來源/目標 </span><span class="sxs-lookup"><span data-stu-id="b26b4-150">*Merge from/to*</span></span>  | <span data-ttu-id="b26b4-151">*release-branch*</span><span class="sxs-lookup"><span data-stu-id="b26b4-151">*release-branch*</span></span> | <span data-ttu-id="b26b4-152">*staging*</span><span class="sxs-lookup"><span data-stu-id="b26b4-152">*staging*</span></span>        | <span data-ttu-id="b26b4-153">*live*</span><span class="sxs-lookup"><span data-stu-id="b26b4-153">*live*</span></span>      |
| ---------------- |:----------------:|:----------------:|:-----------:|
| <span data-ttu-id="b26b4-154">*working-branch*</span><span class="sxs-lookup"><span data-stu-id="b26b4-154">*working-branch*</span></span> | <span data-ttu-id="b26b4-155">壓縮並合併</span><span class="sxs-lookup"><span data-stu-id="b26b4-155">squash and merge</span></span> | <span data-ttu-id="b26b4-156">壓縮並合併</span><span class="sxs-lookup"><span data-stu-id="b26b4-156">squash and merge</span></span> | <span data-ttu-id="b26b4-157">不允許</span><span class="sxs-lookup"><span data-stu-id="b26b4-157">Not allowed</span></span> |
| <span data-ttu-id="b26b4-158">*release-branch*</span><span class="sxs-lookup"><span data-stu-id="b26b4-158">*release-branch*</span></span> | &mdash;          | <span data-ttu-id="b26b4-159">merge</span><span class="sxs-lookup"><span data-stu-id="b26b4-159">merge</span></span>            | <span data-ttu-id="b26b4-160">不允許</span><span class="sxs-lookup"><span data-stu-id="b26b4-160">Not allowed</span></span> |
| <span data-ttu-id="b26b4-161">*staging*</span><span class="sxs-lookup"><span data-stu-id="b26b4-161">*staging*</span></span>        | <span data-ttu-id="b26b4-162">重訂基底</span><span class="sxs-lookup"><span data-stu-id="b26b4-162">rebase</span></span>           | &mdash;          | <span data-ttu-id="b26b4-163">merge</span><span class="sxs-lookup"><span data-stu-id="b26b4-163">merge</span></span>       |

### <a name="pr-merger-checklist"></a><span data-ttu-id="b26b4-164">PR 合併檢查清單</span><span class="sxs-lookup"><span data-stu-id="b26b4-164">PR Merger checklist</span></span>

- <span data-ttu-id="b26b4-165">內容審查完成</span><span class="sxs-lookup"><span data-stu-id="b26b4-165">Content review complete</span></span>
- <span data-ttu-id="b26b4-166">針對變更的正確目標分支</span><span class="sxs-lookup"><span data-stu-id="b26b4-166">Correct target branch for the change</span></span>
- <span data-ttu-id="b26b4-167">沒有合併衝突</span><span class="sxs-lookup"><span data-stu-id="b26b4-167">No merge conflicts</span></span>
- <span data-ttu-id="b26b4-168">通過所有驗證及建置步驟</span><span class="sxs-lookup"><span data-stu-id="b26b4-168">All validation and build step pass</span></span>
  - <span data-ttu-id="b26b4-169">應該修正警告與建議 (請參閱[注意](#notes)以取得例外)</span><span class="sxs-lookup"><span data-stu-id="b26b4-169">Warnings and suggestions should be fixed (see [Notes](#notes) for exceptions)</span></span>
  - <span data-ttu-id="b26b4-170">沒有任何中斷的連結</span><span class="sxs-lookup"><span data-stu-id="b26b4-170">No broken links</span></span>
- <span data-ttu-id="b26b4-171">根據表格進行合併</span><span class="sxs-lookup"><span data-stu-id="b26b4-171">Merge according to table</span></span>

### <a name="notes"></a><span data-ttu-id="b26b4-172">注意</span><span class="sxs-lookup"><span data-stu-id="b26b4-172">Notes</span></span>

<span data-ttu-id="b26b4-173">可以忽略下列警告：</span><span class="sxs-lookup"><span data-stu-id="b26b4-173">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="b26b4-174">合併 PR 時，會變更目標分支的「標頭」。</span><span class="sxs-lookup"><span data-stu-id="b26b4-174">When a PR is merged, the HEAD of the target branch is changed.</span></span> <span data-ttu-id="b26b4-175">任何以先前的「標頭」為基礎的未結 PR 現在都已過時。</span><span class="sxs-lookup"><span data-stu-id="b26b4-175">Any open PRs that were based on the previous HEAD are now outdated.</span></span> <span data-ttu-id="b26b4-176">可以使用系統管理員權限來覆寫 GitHub 中的合併警告，來合併過時的 PR。</span><span class="sxs-lookup"><span data-stu-id="b26b4-176">The outdated PR can be merged using Admin rights to override the merge warnings in GitHub.</span></span> <span data-ttu-id="b26b4-177">如果先前的已合併 PR 未觸及相同的檔案，這是個安全的做法。</span><span class="sxs-lookup"><span data-stu-id="b26b4-177">This is safe to do if the previously merged PR(s) have not touched the same files.</span></span> <span data-ttu-id="b26b4-178">不過，按一下 [Update Branch]  \(更新分支\) 按鈕是最安全的做法。</span><span class="sxs-lookup"><span data-stu-id="b26b4-178">However, clicking the **Update Branch** button is the safest option.</span></span> <span data-ttu-id="b26b4-179">您可能會有需要修正的未解決衝突。</span><span class="sxs-lookup"><span data-stu-id="b26b4-179">You may have unresolved conflicts that need to be fixed.</span></span>

## <a name="publishing-to-live"></a><span data-ttu-id="b26b4-180">發佈到即時網站</span><span class="sxs-lookup"><span data-stu-id="b26b4-180">Publishing to Live</span></span>

<span data-ttu-id="b26b4-181">在 `staging` 分支中累積的變更，需要定期發佈到即時網站。</span><span class="sxs-lookup"><span data-stu-id="b26b4-181">Periodically, the changes accumulated in the `staging` branch need to be published to the live website.</span></span> <span data-ttu-id="b26b4-182">這需要將 `staging` 分支合併到 `live` 分支。</span><span class="sxs-lookup"><span data-stu-id="b26b4-182">This require merging the `staging` branch into the `live` branch.</span></span>

- <span data-ttu-id="b26b4-183">`staging` 分支至少應該要每週合併到 `live` 一次。</span><span class="sxs-lookup"><span data-stu-id="b26b4-183">The `staging` branch should be merged to `live` at least once per week.</span></span>
- <span data-ttu-id="b26b4-184">在做出任何重大變更之後，`staging` 分支應該要合併到 `live`。</span><span class="sxs-lookup"><span data-stu-id="b26b4-184">The `staging` branch should be merged to `live` after any significant change.</span></span>
  - <span data-ttu-id="b26b4-185">對 50 個或更多的檔案進行變更</span><span class="sxs-lookup"><span data-stu-id="b26b4-185">Changes to 50 or more files</span></span>
  - <span data-ttu-id="b26b4-186">在合併發行分支之後</span><span class="sxs-lookup"><span data-stu-id="b26b4-186">After merging a release branch</span></span>
  - <span data-ttu-id="b26b4-187">對存放庫或 DocSet 設定 (docfx.json、OPS 設定、建置指令碼等) 進行變更</span><span class="sxs-lookup"><span data-stu-id="b26b4-187">Changes to repo or docset configurations (docfx.json, OPS configs, build scripts, etc.)</span></span>
  - <span data-ttu-id="b26b4-188">對重新導向檔案進行變更</span><span class="sxs-lookup"><span data-stu-id="b26b4-188">Changes to the redirection file</span></span>
  - <span data-ttu-id="b26b4-189">對目錄進行變更</span><span class="sxs-lookup"><span data-stu-id="b26b4-189">Changes to the TOC</span></span>
  - <span data-ttu-id="b26b4-190">在合併「專案」分支 (內容重新整理、大量更新等) 之後</span><span class="sxs-lookup"><span data-stu-id="b26b4-190">After merging a "project" branch (content reorg, bulk update, etc.)</span></span>
