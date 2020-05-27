---
title: 我們管理問題的方式
description: 此文章說明 PowerShell-Docs 小組管理提取要求的方式。
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 018200f1a9384f1ea956c9b27a7605db21f2da9e
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692525"
---
# <a name="how-we-manage-issues"></a><span data-ttu-id="025d1-103">我們管理問題的方式</span><span class="sxs-lookup"><span data-stu-id="025d1-103">How we manage issues</span></span>

<span data-ttu-id="025d1-104">此文章記錄我們管理 PowerShell-Docs 存放庫中問題的方式。</span><span class="sxs-lookup"><span data-stu-id="025d1-104">This article documents how we manage issues in the PowerShell-Docs repo.</span></span> <span data-ttu-id="025d1-105">此文章是設計來輔助 PowerShell-Docs 小組成員的工作之用。</span><span class="sxs-lookup"><span data-stu-id="025d1-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="025d1-106">在此發佈的原因，是為了向我們的公共參與者提供流程上的透明度。</span><span class="sxs-lookup"><span data-stu-id="025d1-106">It is published here to provide process transparency for our public contributors.</span></span>

## <a name="sources-of-issues"></a><span data-ttu-id="025d1-107">問題的來源</span><span class="sxs-lookup"><span data-stu-id="025d1-107">Sources of issues</span></span>

- <span data-ttu-id="025d1-108">社群參與者</span><span class="sxs-lookup"><span data-stu-id="025d1-108">Community contributors</span></span>
- <span data-ttu-id="025d1-109">內部參與者</span><span class="sxs-lookup"><span data-stu-id="025d1-109">Internal contributors</span></span>
- <span data-ttu-id="025d1-110">來自社交媒體通道的留言文字記錄</span><span class="sxs-lookup"><span data-stu-id="025d1-110">Transcriptions of comments from social media channels</span></span>
- <span data-ttu-id="025d1-111">透過 Docs 意見反應表單提供的意見反應</span><span class="sxs-lookup"><span data-stu-id="025d1-111">Feedback via the Docs feedback form</span></span>

## <a name="response-time-targets"></a><span data-ttu-id="025d1-112">回應時間目標</span><span class="sxs-lookup"><span data-stu-id="025d1-112">Response time targets</span></span>

- <span data-ttu-id="025d1-113">分級：5 個工作天</span><span class="sxs-lookup"><span data-stu-id="025d1-113">Triaged - 5 business days</span></span>
- <span data-ttu-id="025d1-114">修正或變更：無特定目標，盡最大努力</span><span class="sxs-lookup"><span data-stu-id="025d1-114">Fix or change - no specific target - best effort only</span></span>

### <a name="labeling--milestones"></a><span data-ttu-id="025d1-115">標記與里程碑</span><span class="sxs-lookup"><span data-stu-id="025d1-115">Labeling & Milestones</span></span>

#### <a name="label-types"></a><span data-ttu-id="025d1-116">標籤類型</span><span class="sxs-lookup"><span data-stu-id="025d1-116">Label Types</span></span>

|<span data-ttu-id="025d1-117">前置詞</span><span class="sxs-lookup"><span data-stu-id="025d1-117">Prefix</span></span>  | <span data-ttu-id="025d1-118">描述</span><span class="sxs-lookup"><span data-stu-id="025d1-118">Description</span></span>                                                         |
|------- | --------------------------------------------------------------------|
|<span data-ttu-id="025d1-119">區域</span><span class="sxs-lookup"><span data-stu-id="025d1-119">Area</span></span>    | <span data-ttu-id="025d1-120">用來指出問題正在討論 PowerShell 或文件的哪一個部分。</span><span class="sxs-lookup"><span data-stu-id="025d1-120">Used to indicate what part of PowerShell or the docs that the issue is discussing.</span></span><br><span data-ttu-id="025d1-121">適合讓功能擁有者找出其功能的問題。</span><span class="sxs-lookup"><span data-stu-id="025d1-121">Useful for feature owners to find issues for their feature.</span></span>|
|<span data-ttu-id="025d1-122">Pri</span><span class="sxs-lookup"><span data-stu-id="025d1-122">Pri</span></span>     | <span data-ttu-id="025d1-123">用來指出問題的優先順序。</span><span class="sxs-lookup"><span data-stu-id="025d1-123">Used to indicate the priority of the issue.</span></span> <span data-ttu-id="025d1-124">值範圍為 0-4。</span><span class="sxs-lookup"><span data-stu-id="025d1-124">Value range 0-4.</span></span>        |
|<span data-ttu-id="025d1-125">問題</span><span class="sxs-lookup"><span data-stu-id="025d1-125">Issue</span></span>   | <span data-ttu-id="025d1-126">用來分類問題的意見反應類型</span><span class="sxs-lookup"><span data-stu-id="025d1-126">Used to classify the type of feedback for issue</span></span>                     |
|<span data-ttu-id="025d1-127">檢閱</span><span class="sxs-lookup"><span data-stu-id="025d1-127">Review</span></span>  | <span data-ttu-id="025d1-128">用於需要由小組進一步審查的問題</span><span class="sxs-lookup"><span data-stu-id="025d1-128">Used for issue that require further review by the team</span></span>              |
|<span data-ttu-id="025d1-129">狀態</span><span class="sxs-lookup"><span data-stu-id="025d1-129">Status</span></span>  | <span data-ttu-id="025d1-130">用來指出工作項目的狀態</span><span class="sxs-lookup"><span data-stu-id="025d1-130">Used to indicate the status of the work item</span></span>                        |
|<span data-ttu-id="025d1-131">等候</span><span class="sxs-lookup"><span data-stu-id="025d1-131">Waiting</span></span> | <span data-ttu-id="025d1-132">用來指出我們正在等候某個項目</span><span class="sxs-lookup"><span data-stu-id="025d1-132">Used to indicate that we are waiting on something</span></span>                   |

#### <a name="milestones"></a><span data-ttu-id="025d1-133">里程碑</span><span class="sxs-lookup"><span data-stu-id="025d1-133">Milestones</span></span>

<span data-ttu-id="025d1-134">問題與 PR 應該要以適當的里程碑進行標記。</span><span class="sxs-lookup"><span data-stu-id="025d1-134">Issues and PRs should be tagged with the appropriate milestone.</span></span> <span data-ttu-id="025d1-135">如果問題的目標不是特定版本，則不會使用任何里程碑。</span><span class="sxs-lookup"><span data-stu-id="025d1-135">If the issue is not targeted for a specific version then no milestone is used.</span></span> <span data-ttu-id="025d1-136">針對尚未合併到 PowerShell 程式碼基底之變更的 Docs PR 問題，應該要指派給 [Future] \(未來\) 里程碑。</span><span class="sxs-lookup"><span data-stu-id="025d1-136">Issues for Docs PRs for changes that have yet to be merged into the PowerShell code base should be assigned to the **Future** milestone.</span></span> <span data-ttu-id="025d1-137">在合併程式碼變更之後，請將里程碑變更為適當的版本。</span><span class="sxs-lookup"><span data-stu-id="025d1-137">After the code change has been merged, change the milestone to the appropriate version.</span></span>

|    <span data-ttu-id="025d1-138">里程碑</span><span class="sxs-lookup"><span data-stu-id="025d1-138">Milestone</span></span>     |                    <span data-ttu-id="025d1-139">描述</span><span class="sxs-lookup"><span data-stu-id="025d1-139">Description</span></span>                     |
| ---------------- | -------------------------------------------------- |
| <span data-ttu-id="025d1-140">6.x</span><span class="sxs-lookup"><span data-stu-id="025d1-140">6.x</span></span>              | <span data-ttu-id="025d1-141">與 PowerShell 6.0 至 6.2.x 相關的工作項目</span><span class="sxs-lookup"><span data-stu-id="025d1-141">Work items related to PowerShell 6.0 through 6.2.x</span></span> |
| <span data-ttu-id="025d1-142">7.0.0</span><span class="sxs-lookup"><span data-stu-id="025d1-142">7.0.0</span></span>            | <span data-ttu-id="025d1-143">與 PowerShell 7.0 相關的工作項目</span><span class="sxs-lookup"><span data-stu-id="025d1-143">Work items related to PowerShell 7.0</span></span>               |
| <span data-ttu-id="025d1-144">7.1.0</span><span class="sxs-lookup"><span data-stu-id="025d1-144">7.1.0</span></span>            | <span data-ttu-id="025d1-145">與 PowerShell 7.1 相關的工作項目</span><span class="sxs-lookup"><span data-stu-id="025d1-145">Work items related to PowerShell 7.1</span></span>               |
| <span data-ttu-id="025d1-146">未來</span><span class="sxs-lookup"><span data-stu-id="025d1-146">Future</span></span>           | <span data-ttu-id="025d1-147">與未來的 PowerShell 版本相關的工作項目</span><span class="sxs-lookup"><span data-stu-id="025d1-147">Work items a future version of PowerShell</span></span>          |
| <span data-ttu-id="025d1-148">PSReadline-vNext</span><span class="sxs-lookup"><span data-stu-id="025d1-148">PSReadline-vNext</span></span> | <span data-ttu-id="025d1-149">與未來的 PSReadline 版本相關的工作項目</span><span class="sxs-lookup"><span data-stu-id="025d1-149">Work items a future version of PSReadline</span></span>          |

## <a name="triage-process"></a><span data-ttu-id="025d1-150">分級程序</span><span class="sxs-lookup"><span data-stu-id="025d1-150">Triage process</span></span>

<span data-ttu-id="025d1-151">PowerShell Docs 小組每週會開會一次，以討論在上次會議之後新增的任何問題。</span><span class="sxs-lookup"><span data-stu-id="025d1-151">The PowerShell docs team meets once per week to discuss any issues added since last meeting.</span></span> <span data-ttu-id="025d1-152">當已指派標籤，或是已指派擁有者時，便會將問題視為已分級。</span><span class="sxs-lookup"><span data-stu-id="025d1-152">An issue is considered to have been triaged when labels have been assigned or an owner has been assigned.</span></span> <span data-ttu-id="025d1-153">我們鼓勵 PowerShell Docs 小組成員每日審查問題，並在新問題抵達時便對其進行分級。</span><span class="sxs-lookup"><span data-stu-id="025d1-153">PowerShell docs team members are encouraged to review the issues daily and triage new issues as they arrive.</span></span> <span data-ttu-id="025d1-154">如此一來，便可以視需要將每週的分級會議用來深入討論新問題。</span><span class="sxs-lookup"><span data-stu-id="025d1-154">The weekly triage meeting can then be used to discuss the new issues in more detail, as needed.</span></span>

### <a name="misplaced-product-feedback"></a><span data-ttu-id="025d1-155">錯置的產品意見反應</span><span class="sxs-lookup"><span data-stu-id="025d1-155">Misplaced product feedback</span></span>

- <span data-ttu-id="025d1-156">為客戶輸入留言以指出其為產品意見反應，並提供適當意見反應管道的連結。</span><span class="sxs-lookup"><span data-stu-id="025d1-156">Enter a comment for the customer indicating it is product feedback and provide a link to the appropriate feedback channel.</span></span>
- <span data-ttu-id="025d1-157">選擇性：將問題複製到適當的產品意見反應位置、新增已複製項目的連結，然後關閉該問題。</span><span class="sxs-lookup"><span data-stu-id="025d1-157">Optional: Copy the issue to the appropriate product feedback location, add a link to the copied item, and close the issue.</span></span> <span data-ttu-id="025d1-158">請勿將問題複製到 UserVoice。</span><span class="sxs-lookup"><span data-stu-id="025d1-158">DO NOT copy issues to UserVoice.</span></span>

  | <span data-ttu-id="025d1-159">DocSet</span><span class="sxs-lookup"><span data-stu-id="025d1-159">DocSet</span></span>    | <span data-ttu-id="025d1-160">產品意見反應 URL</span><span class="sxs-lookup"><span data-stu-id="025d1-160">Product Feedback URL</span></span>                                           |
  | --------- | -------------------------------------------------------------- |
  | <span data-ttu-id="025d1-161">developer</span><span class="sxs-lookup"><span data-stu-id="025d1-161">developer</span></span> | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | <span data-ttu-id="025d1-162">dsc</span><span class="sxs-lookup"><span data-stu-id="025d1-162">dsc</span></span>       | `https://windowsserver.uservoice.com/forums/301869-powershell` |
  | <span data-ttu-id="025d1-163">gallery</span><span class="sxs-lookup"><span data-stu-id="025d1-163">gallery</span></span>   | `https://github.com/powershell/powershellgallery/issues/new`   |
  | <span data-ttu-id="025d1-164">jea</span><span class="sxs-lookup"><span data-stu-id="025d1-164">jea</span></span>       | `https://github.com/powershell/jea/issues/new`                 |
  | <span data-ttu-id="025d1-165">reference</span><span class="sxs-lookup"><span data-stu-id="025d1-165">reference</span></span> | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | <span data-ttu-id="025d1-166">wmf</span><span class="sxs-lookup"><span data-stu-id="025d1-166">wmf</span></span>       | `https://windowsserver.uservoice.com/forums/301869-powershell` |

### <a name="support-requests"></a><span data-ttu-id="025d1-167">支援要求</span><span class="sxs-lookup"><span data-stu-id="025d1-167">Support requests</span></span>

- <span data-ttu-id="025d1-168">如果支援問題很簡單，請有禮貌地加以回答，然後關閉該問題。</span><span class="sxs-lookup"><span data-stu-id="025d1-168">If the support question is simple, answer it politely and close the issue.</span></span>
- <span data-ttu-id="025d1-169">如果問題比較複雜，或是提交者回覆更多問題，請將其重新導向到論壇和支援管道。</span><span class="sxs-lookup"><span data-stu-id="025d1-169">If the question is more complicated, or the submitter replies with more questions, redirect them to forums and support channels.</span></span> <span data-ttu-id="025d1-170">重新導向到論壇的建議文字：</span><span class="sxs-lookup"><span data-stu-id="025d1-170">Suggested text for redirecting to forums:</span></span>

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a><span data-ttu-id="025d1-171">管理辦法違規</span><span class="sxs-lookup"><span data-stu-id="025d1-171">Code of conduct violations</span></span>

- <span data-ttu-id="025d1-172">若有需要，請編輯問題以移除任何冒犯的內容。</span><span class="sxs-lookup"><span data-stu-id="025d1-172">Edit the issue to remove any offensive content, if necessary.</span></span>
- <span data-ttu-id="025d1-173">輸入留言以指出該問題為垃圾訊息、關閉該問題，然後加以鎖定以防止進一步的留言。</span><span class="sxs-lookup"><span data-stu-id="025d1-173">Enter a comment indicating the issue is spam, close the issue, and then lock it to prevent further comments.</span></span>
- <span data-ttu-id="025d1-174">發生此情況的每一個案例都應該在每週的分級會議中討論，以判斷是否需要執行進一步動作 (向 GitHub 或 Microsoft 法務部門回報)。</span><span class="sxs-lookup"><span data-stu-id="025d1-174">Each occurrence of this should be discussed in the weekly triage to determine the need for further action (report to GitHub or Microsoft Legal).</span></span>
