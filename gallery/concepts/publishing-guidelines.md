---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
description: 發行者的指導方針
title: PowerShell 資源庫發行指導方針與最佳做法
ms.openlocfilehash: 64c3d607b13dce64f70f138fdee849e5baaf85df
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265564"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a><span data-ttu-id="6b72f-104">PowerShell 資源庫發行指導方針與最佳做法</span><span class="sxs-lookup"><span data-stu-id="6b72f-104">PowerShellGallery Publishing Guidelines and Best Practices</span></span>

<span data-ttu-id="6b72f-105">此主題說明一些建議的步驟，Microsoft 小組會使用這些步驟，根據「PowerShell 資源庫」處理資訊清單資料的方式，以大量「PowerShell 資源庫」使用者的意見反應，確保發行至「PowerShell 資源庫」的套件會受到廣泛採用，並為使用者提供相當高的價值。</span><span class="sxs-lookup"><span data-stu-id="6b72f-105">This topic describes recommended steps used by Microsoft teams to ensure the packages published to the PowerShell Gallery will be widely adopted and provide high value to users, based on how the PowerShell Gallery handles manifest data and on feedback from large numbers of PowerShell Gallery users.</span></span>
<span data-ttu-id="6b72f-106">凡是依循這些指導方針發行的套件，將較可能獲得安裝、信任及吸引更多使用者。</span><span class="sxs-lookup"><span data-stu-id="6b72f-106">Packages that are published following these guidelines will be more likely to be installed, trusted, and attract more users.</span></span>

<span data-ttu-id="6b72f-107">以下是一些指導方針，說明哪些是良好「PowerShell 資源庫」套件的構成要素、哪些選擇性「資訊清單」設定最重要、如何利用初始檢閱者和 [Powershell 指令碼分析程式](https://aka.ms/psscriptanalyzer)的意見反應來改善您的程式碼，以及如何為模組、文件、測試和範例設定版本來指定如何使用您已共用的項目。</span><span class="sxs-lookup"><span data-stu-id="6b72f-107">Included below are guidelines for what makes a good PowerShell Gallery package, what optional Manifest settings are most important, improving your code with feedback from initial reviewers and [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer), versioning your module, documentation, tests & examples for how to use what you have shared.</span></span>
<span data-ttu-id="6b72f-108">本文件大部分皆依循發行[高品質 DSC 資源模組](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md) \(英文\) 的指導方針。</span><span class="sxs-lookup"><span data-stu-id="6b72f-108">Much of this documentation follows the guidelines for publishing [High Quality DSC Resource Modules](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).</span></span>

<span data-ttu-id="6b72f-109">如需了解將套件發行至「PowerShell 資源」的技巧，請參閱[建立和發行套件](/powershell/gallery/how-to/publishing-packages/publishing-a-package)。</span><span class="sxs-lookup"><span data-stu-id="6b72f-109">For the mechanics of publishing a package to the PowerShell Gallery, see [Creating and Publishing a Package](/powershell/gallery/how-to/publishing-packages/publishing-a-package).</span></span>

<span data-ttu-id="6b72f-110">歡迎您提供有關這些指導方針的意見反應。</span><span class="sxs-lookup"><span data-stu-id="6b72f-110">Feedback on these guidelines is welcomed.</span></span> <span data-ttu-id="6b72f-111">如果您確實有意見反應，請在我們的 [Github 文件儲存機制](https://github.com/powershell/powershell-docs/issues) \(英文\) 中提出問題。</span><span class="sxs-lookup"><span data-stu-id="6b72f-111">If you do have feedback, please open issues in our [Github documentation repository](https://github.com/powershell/powershell-docs/issues).</span></span>

## <a name="best-practices-for-publishing-packages"></a><span data-ttu-id="6b72f-112">發行套件的最佳做法</span><span class="sxs-lookup"><span data-stu-id="6b72f-112">Best practices for publishing packages</span></span>

<span data-ttu-id="6b72f-113">下列最佳做法是「PowerShell 資源庫」項目使用者表示重要的最佳做法，列出順序是依照提名優先順序。</span><span class="sxs-lookup"><span data-stu-id="6b72f-113">The following best practices are what the users of PowerShell Gallery items say is important, and are listed in nominal priority order.</span></span>
<span data-ttu-id="6b72f-114">遵循這些準則的套件更有可能被其他人下載和採用。</span><span class="sxs-lookup"><span data-stu-id="6b72f-114">Packages that follow these guidelines are far more likely to be downloaded and adopted by others.</span></span>

- <span data-ttu-id="6b72f-115">使用 PSScriptAnalyzer</span><span class="sxs-lookup"><span data-stu-id="6b72f-115">Use PSScriptAnalyzer</span></span>
- <span data-ttu-id="6b72f-116">包含文件和範例</span><span class="sxs-lookup"><span data-stu-id="6b72f-116">Include documentation and examples</span></span>
- <span data-ttu-id="6b72f-117">針對意見反應做出回應</span><span class="sxs-lookup"><span data-stu-id="6b72f-117">Be responsive to feedback</span></span>
- <span data-ttu-id="6b72f-118">提供模組而不是指令碼</span><span class="sxs-lookup"><span data-stu-id="6b72f-118">Provide modules rather than scripts</span></span>
- <span data-ttu-id="6b72f-119">提供專案網站的連結</span><span class="sxs-lookup"><span data-stu-id="6b72f-119">Provide links to a project site</span></span>
- <span data-ttu-id="6b72f-120">標記使用相容的 PSEdition(s) 及平台套件</span><span class="sxs-lookup"><span data-stu-id="6b72f-120">Tag your package with the compatible PSEdition(s) and platforms</span></span> 
- <span data-ttu-id="6b72f-121">在模組中隨附測試</span><span class="sxs-lookup"><span data-stu-id="6b72f-121">Include tests with your modules</span></span>
- <span data-ttu-id="6b72f-122">包含和/或連結至授權條款</span><span class="sxs-lookup"><span data-stu-id="6b72f-122">Include and/or link to license terms</span></span>
- <span data-ttu-id="6b72f-123">簽署您的程式碼</span><span class="sxs-lookup"><span data-stu-id="6b72f-123">Sign your code</span></span>
- <span data-ttu-id="6b72f-124">依循 [SemVer](http://semver.org/) 指導方針來進行版本設定</span><span class="sxs-lookup"><span data-stu-id="6b72f-124">Follow [SemVer](http://semver.org/) guidelines for versioning</span></span>
- <span data-ttu-id="6b72f-125">使用「常用的 PowerShell 資源庫」標記中記載的常用標記</span><span class="sxs-lookup"><span data-stu-id="6b72f-125">Use common tags, as documented in Common PowerShell Gallery tags</span></span>
- <span data-ttu-id="6b72f-126">使用本機存放庫來測試發行</span><span class="sxs-lookup"><span data-stu-id="6b72f-126">Test publishing using a local repository</span></span>
- <span data-ttu-id="6b72f-127">使用 PowerShellGet 發佈</span><span class="sxs-lookup"><span data-stu-id="6b72f-127">Use PowerShellGet to publish</span></span>

<span data-ttu-id="6b72f-128">下面各節將簡要說明這上述每一個做法。</span><span class="sxs-lookup"><span data-stu-id="6b72f-128">Each of these is covered briefly in the sections below.</span></span>

## <a name="use-psscriptanalyzer"></a><span data-ttu-id="6b72f-129">使用 PSScriptAnalyzer</span><span class="sxs-lookup"><span data-stu-id="6b72f-129">Use PSScriptAnalyzer</span></span>

<span data-ttu-id="6b72f-130">[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) 是一個可在 PowerShell 程式碼上運作的免費靜態程式碼分析工具。</span><span class="sxs-lookup"><span data-stu-id="6b72f-130">[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) is a free static code analysis tool that works on PowerShell code.</span></span>
<span data-ttu-id="6b72f-131">PSScriptAnalyzer 會識別出 PowerShell 程式碼中最常見的問題，且通常會提供如何修正該問題的建議。</span><span class="sxs-lookup"><span data-stu-id="6b72f-131">PSScriptAnalyzer will identify the most common issues seen in PowerShell code, and often a recommendation for how to fix the issue.</span></span>
<span data-ttu-id="6b72f-132">此工具相當容易使用，並且會將問題分類為「錯誤」(代表嚴重，必須加以解決)、「警告」(代表需要檢閱且應該加以解決)，以及「資訊」(代表值得查看以了解最佳做法)。</span><span class="sxs-lookup"><span data-stu-id="6b72f-132">The tool is easy to use, and categorizes the issues as Errors (severe, must be addressed), Warning (need to be reviewed & should be addressed), and Information (worth checking out for best practices).</span></span>
<span data-ttu-id="6b72f-133">所有發行至「PowerShell 資源庫」的套件都會由 PSScriptAnalyzer 掃描，如有任何錯誤，就會回報給擁有者且必須加以解決。</span><span class="sxs-lookup"><span data-stu-id="6b72f-133">All packages published to the PowerShell Gallery will be scanned using PSScriptAnalyzer, and any errors will be reported back to the owner and must be addressed.</span></span>

<span data-ttu-id="6b72f-134">最佳做法是搭配 `-Recurse` 和 `-Severity` 警告執行 `Invoke-ScriptAnalyzer`。</span><span class="sxs-lookup"><span data-stu-id="6b72f-134">The best practice is to run `Invoke-ScriptAnalyzer` with `-Recurse` and `-Severity` Warning.</span></span>

<span data-ttu-id="6b72f-135">請檢閱結果並確保：</span><span class="sxs-lookup"><span data-stu-id="6b72f-135">Review the results, and ensure that:</span></span>

- <span data-ttu-id="6b72f-136">所有「錯誤」在您的文件中都已獲得更正或處理</span><span class="sxs-lookup"><span data-stu-id="6b72f-136">All Errors are corrected or addressed in your documentation</span></span>
- <span data-ttu-id="6b72f-137">所有「警告」都已獲得檢閱和適當的處理</span><span class="sxs-lookup"><span data-stu-id="6b72f-137">All Warnings are reviewed, and addressed where applicable</span></span>

<span data-ttu-id="6b72f-138">強烈建議從「PowerShell 資源庫」取得套件的使用者執行 PSScriptAnalyzer 並評估所有「錯誤」和「警告」。</span><span class="sxs-lookup"><span data-stu-id="6b72f-138">Users who acquire packages from the PowerShell Gallery are strongly encouraged to run PSScriptAnalyzer and evaluate all Errors and Warnings.</span></span>
<span data-ttu-id="6b72f-139">使用者如果看到 PSScriptAnalyzer 回報某個錯誤，非常可能會連絡套件擁有者。</span><span class="sxs-lookup"><span data-stu-id="6b72f-139">Users are very likely to contact package owners if they see that there is an error reported by PSScriptAnalyzer.</span></span>
<span data-ttu-id="6b72f-140">如果您的套件有充分的理由必須保留標示為錯誤的程式碼，請將該資訊新增到您的文件中，以避免需要多次回答相同的問題。</span><span class="sxs-lookup"><span data-stu-id="6b72f-140">If there is a compelling reason for your package to keep code that is flagged as an error, add that information to your documentation to avoid having to answer the same question many times.</span></span>

## <a name="include-documentation-and-examples"></a><span data-ttu-id="6b72f-141">包含文件和範例</span><span class="sxs-lookup"><span data-stu-id="6b72f-141">Include documentation and examples</span></span>

<span data-ttu-id="6b72f-142">文件和範例是確保使用者能夠利用任何共用程式碼的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="6b72f-142">Documentation and examples are the best way to ensure users can take advantage of any shared code.</span></span>

<span data-ttu-id="6b72f-143">文件是可包含在發行至「PowerShell 資源庫」之套件中的最有用說明資料。</span><span class="sxs-lookup"><span data-stu-id="6b72f-143">Documentation is the most helpful thing to include in packages published to the PowerShell Gallery.</span></span>
<span data-ttu-id="6b72f-144">使用者通常會略過沒有文件的套件，因為可以選擇閱讀程式碼來了解該套件是什麼及如何使用它。</span><span class="sxs-lookup"><span data-stu-id="6b72f-144">Users will generally bypass packages without documentation, as the alternative is to read the code to understand what the package is and how to use it.</span></span>
<span data-ttu-id="6b72f-145">MSDN 中提供數篇有關如何隨 PowerShell 套件提供文件的文章，包括：</span><span class="sxs-lookup"><span data-stu-id="6b72f-145">There are several articles available about how to provide documentation with PowerShell packages, including:</span></span>

- <span data-ttu-id="6b72f-146">如需提供說明的指導方針，請參閱[如何撰寫 Cmdlet 說明](https://go.microsoft.com/fwlink/?LinkID=123415) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="6b72f-146">Guidelines for providing help are in [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415)</span></span>
- <span data-ttu-id="6b72f-147">建立 Cmdlet 說明，這是適用於所有 PowerShell 指令碼、函式或 Cmdlet 的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="6b72f-147">Creating cmdlet help, which is the best approach for any PowerShell script, function, or cmdlet.</span></span>
  <span data-ttu-id="6b72f-148">如需如何建立 Cmdlet 說明的資訊，請從[如何撰寫 Cmdlet 說明](https://go.microsoft.com/fwlink/?LinkID=123415) \(英文\) 開始著手。</span><span class="sxs-lookup"><span data-stu-id="6b72f-148">For information about how to create cmdlet help, start with [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415).</span></span>
  <span data-ttu-id="6b72f-149">若要在指令碼中新增說明，請參閱[關於註解型說明](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="6b72f-149">To add help within a script, see [About Comment Based Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>
- <span data-ttu-id="6b72f-150">許多模組也包含文字格式的文件，例如 MarkDown 檔案。</span><span class="sxs-lookup"><span data-stu-id="6b72f-150">Many modules also include documentation in text format, such as MarkDown files.</span></span>
  <span data-ttu-id="6b72f-151">當 Github 中有大量使用 Markdown 格式的專案網站時，這會特別有用。</span><span class="sxs-lookup"><span data-stu-id="6b72f-151">This can be particularly helpful when there is a project site in Github, where Markdown is a heavily used format.</span></span>
  <span data-ttu-id="6b72f-152">最佳做法是使用[具備 Github 特色的 Markdown](https://help.github.com/categories/writing-on-github/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="6b72f-152">The best practice is to use [Github-flavored Markdown](https://help.github.com/categories/writing-on-github/)</span></span>

<span data-ttu-id="6b72f-153">範例會向使用者說明應該如何使用套件。</span><span class="sxs-lookup"><span data-stu-id="6b72f-153">Examples show users how the package is intended to be used.</span></span>
<span data-ttu-id="6b72f-154">許多開發人員會說他們在看文件之前會先看範例來了解如何使用某些項目。</span><span class="sxs-lookup"><span data-stu-id="6b72f-154">Many developers will say that they look at examples before documentation to understand how to use something.</span></span>
<span data-ttu-id="6b72f-155">最佳類型的範例會說明基本用法，再加上模擬的實際使用案例，而且程式碼會有詳細的註解。</span><span class="sxs-lookup"><span data-stu-id="6b72f-155">The best type of examples show basic use, plus a simulated realistic use case, and the code is well-commented.</span></span>
<span data-ttu-id="6b72f-156">發行至「PowerShell 資源庫」之模組的範例應該位於模組根目錄底下的 [Examples] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6b72f-156">Examples for modules published to the PowerShell Gallery should be in an Examples folder under the module root.</span></span>

<span data-ttu-id="6b72f-157">您可以在 Examples\RegistryResource 資料夾底下的 [PSDscResource 模組](https://www.powershellgallery.com/packages/PSDscResources)中找到理想的範例模式。</span><span class="sxs-lookup"><span data-stu-id="6b72f-157">A good pattern for examples can be found in the [PSDscResource module](https://www.powershellgallery.com/packages/PSDscResources) under the Examples\RegistryResource folder.</span></span>
<span data-ttu-id="6b72f-158">一共有四個範例使用案例，其中每個檔案最上方都有一段簡短的描述，記載了所要示範的內容。</span><span class="sxs-lookup"><span data-stu-id="6b72f-158">There are four sample use cases with a brief description at the top of each file that documents what is being demonstrated.</span></span>

## <a name="respond-to-feedback"></a><span data-ttu-id="6b72f-159">針對意見反應做出回應</span><span class="sxs-lookup"><span data-stu-id="6b72f-159">Respond to feedback</span></span>

<span data-ttu-id="6b72f-160">正確地對意見反應做出回應的套件擁有者在社群中會享有高評價。</span><span class="sxs-lookup"><span data-stu-id="6b72f-160">Package owners who respond properly to feedback are highly valued by the community.</span></span>
<span data-ttu-id="6b72f-161">提供具建設性意見反應的使用者是重要的回應對象，因為他們對套件的興趣大到足以嘗試協助改進該套件。</span><span class="sxs-lookup"><span data-stu-id="6b72f-161">Users who provide constructive feedback are important to respond to, as they are interested enough in the package to try to help improve it.</span></span>

<span data-ttu-id="6b72f-162">「PowerShell 資源庫」中提供兩種意見反應方法：</span><span class="sxs-lookup"><span data-stu-id="6b72f-162">There are two feedback methods available in the PowerShell Gallery:</span></span>

- <span data-ttu-id="6b72f-163">連絡擁有者：這可讓使用者傳送電子郵件給套件擁有者。</span><span class="sxs-lookup"><span data-stu-id="6b72f-163">Contact Owner: This allows a user to send an email to the package owner(s).</span></span> <span data-ttu-id="6b72f-164">如果您是套件擁有者，請務必隨時注意與「PowerShell 資源庫」套件搭配使用的電子郵件地址，並針對提出的問題進行回應。</span><span class="sxs-lookup"><span data-stu-id="6b72f-164">As an package owner, is important to monitor the email address used with the PowerShell Gallery packages, and respond to issues that are raised.</span></span> <span data-ttu-id="6b72f-165">此方法有一個缺點，就是只有使用者和擁有者可以看到溝通內容，因此擁有者可能必須回答相同的問題許多次。</span><span class="sxs-lookup"><span data-stu-id="6b72f-165">The one disadvantage to this method is that only the user and owner will ever see the communication, so the owner may have to answer the same question many times.</span></span>
- <span data-ttu-id="6b72f-166">評論：套件頁面底部有一個 [評論] 欄位。</span><span class="sxs-lookup"><span data-stu-id="6b72f-166">Comments: At the bottom of the package page is a Comment field.</span></span>
  <span data-ttu-id="6b72f-167">此系統的優點是其他使用者可以看到評論和回應，減少了必須回答任何單一問題的次數。</span><span class="sxs-lookup"><span data-stu-id="6b72f-167">The advantage to this system is that other users can see the comments and responses, which reduces the number of times any single question must be answered.</span></span>
  <span data-ttu-id="6b72f-168">如果您是套件擁有者，強烈建議您「關注」針對每個套件提出的評論。</span><span class="sxs-lookup"><span data-stu-id="6b72f-168">As a package owner, it is strongly recommended that you Follow the comments made for each package.</span></span>
<span data-ttu-id="6b72f-169">如需相關做法的詳細資料，請參閱[透過社群媒體或評論來提供意見反應](../how-to/working-with-packages/social-media-feedback.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="6b72f-169">See [Providing Feedback via Social Media or Comments](../how-to/working-with-packages/social-media-feedback.md) for details on how to do that.</span></span>

<span data-ttu-id="6b72f-170">以具建設性的方式回應意見反應的擁有者會受到社群激賞。</span><span class="sxs-lookup"><span data-stu-id="6b72f-170">Owners who respond to feedback constructively are appreciated by the community.</span></span>
<span data-ttu-id="6b72f-171">您可以藉機利用報告來視需要要求更多資訊、提供因應措施，或是指出是否可透過更新來修正問題。</span><span class="sxs-lookup"><span data-stu-id="6b72f-171">Use the opportunity in the report to request more information if needed, provide a workaround, or identify if an update fixes a problem.</span></span>

<span data-ttu-id="6b72f-172">如果從這些溝通管道中的任何一個管道觀察到不當的行為，請使用「PowerShell 資源庫」的 [檢舉不當使用] 功能來連絡「資源庫系統管理員」。</span><span class="sxs-lookup"><span data-stu-id="6b72f-172">If there is inappropriate behavior observed from either of these communication channels, use the Report Abuse feature of the PowerShell Gallery to contact the Gallery Administrators.</span></span>

## <a name="modules-versus-scripts"></a><span data-ttu-id="6b72f-173">模組與指令碼之比較</span><span class="sxs-lookup"><span data-stu-id="6b72f-173">Modules Versus Scripts</span></span>

<span data-ttu-id="6b72f-174">與其他使用者共用指令碼是相當好的做法，並可為其他使用者提供如何解決他們問題的範例。</span><span class="sxs-lookup"><span data-stu-id="6b72f-174">Sharing a script with other users is great, and provides others with examples of how to solve problems they may have.</span></span>
<span data-ttu-id="6b72f-175">問題在於「PowerShell 資源庫」中的指令碼是單一檔案，並無個別的文件、範例及測試。</span><span class="sxs-lookup"><span data-stu-id="6b72f-175">The issue is that scripts in the PowerShell Gallery are single files without separate documentation, examples, and tests.</span></span>

<span data-ttu-id="6b72f-176">「PowerShell 模組」具有資料夾結構，可允許將多個資料夾和檔案包含在套件中。</span><span class="sxs-lookup"><span data-stu-id="6b72f-176">PowerShell Modules have a folder structure that allows multiple folders and files to be included with the package.</span></span>
<span data-ttu-id="6b72f-177">模組結構可將我們列為最佳做法的下列其他套件都納入其中：Cmdlet 說明、文件、範例與測試。</span><span class="sxs-lookup"><span data-stu-id="6b72f-177">The module structure enables including the other packages we list as best practices: cmdlet help, documentation, examples, and tests.</span></span>
<span data-ttu-id="6b72f-178">最大的缺點在於模組內的指令碼必須公開並當作函式使用。</span><span class="sxs-lookup"><span data-stu-id="6b72f-178">The biggest disadvantage is that a script inside a module must be exposed and used as a function.</span></span>
<span data-ttu-id="6b72f-179">如需有關如何建立模組的資訊，請參閱[撰寫 Windows PowerShell 模組](http://go.microsoft.com/fwlink/?LinkId=144916) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="6b72f-179">For information on how to create a module, see [Writing a Windows PowerShell Module](http://go.microsoft.com/fwlink/?LinkId=144916).</span></span>

<span data-ttu-id="6b72f-180">在一些情況下，指令碼可為使用者提供較佳的體驗，特別是搭配 DSC 設定時。</span><span class="sxs-lookup"><span data-stu-id="6b72f-180">There are situations where a script provides a better experience for the user, particularly with DSC configurations.</span></span>
<span data-ttu-id="6b72f-181">DSC 設定的最佳做法是以指令碼的形式發行設定，此指令碼會隨附一個包含文件、範例及測試的模組。</span><span class="sxs-lookup"><span data-stu-id="6b72f-181">The best practice for DSC configurations is to publish the configuration as a script with an accompanying module that contains the docs, examples, and tests.</span></span>
<span data-ttu-id="6b72f-182">此指令碼會使用 RequiredModules = @(模組名稱) 來列出隨附的模組。</span><span class="sxs-lookup"><span data-stu-id="6b72f-182">The script lists the accompanying module using RequiredModules = @(Name of the Module).</span></span>
<span data-ttu-id="6b72f-183">此方法可以與任何指令碼搭配使用。</span><span class="sxs-lookup"><span data-stu-id="6b72f-183">This approach can be used with any script.</span></span>

<span data-ttu-id="6b72f-184">依循其他最佳做法的獨立指令碼可以為其他使用者提供實際的價值。</span><span class="sxs-lookup"><span data-stu-id="6b72f-184">Standalone scripts that follow the other best practices provide real value to other users.</span></span>
<span data-ttu-id="6b72f-185">將指令碼發行至「PowerShell 資源庫」時，強烈建議您提供註解型文件和「專案網站」的連結。</span><span class="sxs-lookup"><span data-stu-id="6b72f-185">Providing comment-based documentation and a link to a Project Site are highly recommended when publishing a script to the PowerShell Gallery.</span></span>

## <a name="provide-a-link-to-a-project-site"></a><span data-ttu-id="6b72f-186">提供專案網站的連結</span><span class="sxs-lookup"><span data-stu-id="6b72f-186">Provide a link to a project site</span></span>

<span data-ttu-id="6b72f-187">「專案網站」是發行者可以與其「PowerShell 資源庫」套件使用者直接互動的地方。</span><span class="sxs-lookup"><span data-stu-id="6b72f-187">A Project Site is where a publisher can interact directly with the users of their PowerShell Gallery packages.</span></span>
<span data-ttu-id="6b72f-188">使用者會偏好使用提供此連結的套件，因為這可讓他們更輕鬆取得套件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6b72f-188">Users prefer packages that provide this, as it allows them to get information about the package more easily.</span></span>
<span data-ttu-id="6b72f-189">「PowerShell 資源庫」中的許多套件都是在 GitHub 中開發的，其他套件則是由具有專用網站空間的組織提供的。</span><span class="sxs-lookup"><span data-stu-id="6b72f-189">Many packages in the PowerShell Gallery are developed in GitHub, others are provided by organizations with a dedicated web presence.</span></span>
<span data-ttu-id="6b72f-190">上述每一個都可以視為專案網站。</span><span class="sxs-lookup"><span data-stu-id="6b72f-190">Each of these can be considered a project site.</span></span>

<span data-ttu-id="6b72f-191">若要新增連結，請依下列方式將 ProjectURI 包含在資訊清單的 PSData 區段中：</span><span class="sxs-lookup"><span data-stu-id="6b72f-191">Adding a link is done by including ProjectURI in the PSData section of the manifest as follows:</span></span>

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

<span data-ttu-id="6b72f-192">當已提供 ProjectURI 時，「PowerShell 資源庫」就會在套件頁面的左邊包含「專案網站」的連結。</span><span class="sxs-lookup"><span data-stu-id="6b72f-192">When a ProjectURI is provided, the PowerShell Gallery will include a link to the Project Site on the left side of the package page.</span></span>

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a><span data-ttu-id="6b72f-193">標記使用相容的 PSEdition(s) 及平台套件</span><span class="sxs-lookup"><span data-stu-id="6b72f-193">Tag your package with the compatible PSEdition(s) and platforms</span></span> 

<span data-ttu-id="6b72f-194">若要將套件也會使用其環境的使用者示範使用下列標籤：</span><span class="sxs-lookup"><span data-stu-id="6b72f-194">Use the following tags to demonstrate to users which packages will work well with their enviroment:</span></span>

- <span data-ttu-id="6b72f-195">使用 Windows PowerShell 相容的 PSEdition_Desktop： 套件</span><span class="sxs-lookup"><span data-stu-id="6b72f-195">PSEdition_Desktop : Packages that are compatible with Windows PowerShell</span></span> 
- <span data-ttu-id="6b72f-196">與 Powershell Core 相容的 PSEdition_Core： 套件</span><span class="sxs-lookup"><span data-stu-id="6b72f-196">PSEdition_Core : Packages that are compatible with Powershell Core</span></span> 
- <span data-ttu-id="6b72f-197">Windows： 套件與 Windows 作業系統相容</span><span class="sxs-lookup"><span data-stu-id="6b72f-197">Windows : Packages that are compatible with the Windows Operating System</span></span>
- <span data-ttu-id="6b72f-198">使用 Linux 作業系統相容的 Linux： 套件</span><span class="sxs-lookup"><span data-stu-id="6b72f-198">Linux : Packages that are compatible with Linux Operating Systems</span></span> 
- <span data-ttu-id="6b72f-199">MacOS： 套件與 Mac 作業系統相容</span><span class="sxs-lookup"><span data-stu-id="6b72f-199">MacOS : Packages that are compatible with the Mac Operating System</span></span>

## <a name="include-tests"></a><span data-ttu-id="6b72f-200">包含測試</span><span class="sxs-lookup"><span data-stu-id="6b72f-200">Include tests</span></span>

<span data-ttu-id="6b72f-201">包含具有開放原始碼的測試對使用者而言相當重要，因為這可以向使用者提供您所驗證項目的相關保證，並提供與您程式碼運作情況相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="6b72f-201">Including tests with open-source code is important to users, as it gives them assurance about what you validate, and provides information on how your code works.</span></span> <span data-ttu-id="6b72f-202">這也可以讓使用者確保當修改您的程式碼以配合其環境時，不致於破壞您的原始功能。</span><span class="sxs-lookup"><span data-stu-id="6b72f-202">It also allows users to ensure they do not break your original functionality if they modify your code to fit their environment.</span></span>

<span data-ttu-id="6b72f-203">強烈建議您撰寫測試來利用 Pester 測試架構，這是專為 PowerShell 設計的測試架構。</span><span class="sxs-lookup"><span data-stu-id="6b72f-203">It is strongly recommended that tests be written to take advantage of the Pester test framework, which has been designed specifically for PowerShell.</span></span>
<span data-ttu-id="6b72f-204">除了可以從 [GitHub](https://github.com/Pester/Pester)、[PowerShell 資源庫](https://www.powershellgallery.com/packages/Pester/)取得 Pester 之外，Windows 10、Windows Server 2016、WMF 5.0 及 WMF 5.1 中也隨附 Pester。</span><span class="sxs-lookup"><span data-stu-id="6b72f-204">Pester is available in [GitHub](https://github.com/Pester/Pester), the [PowerShell Gallery](https://www.powershellgallery.com/packages/Pester/), and ships in Windows 10, Windows Server 2016, WMF 5.0 and WMF 5.1.</span></span>

<span data-ttu-id="6b72f-205">[GitHub 中的 Pester 專案網站](https://github.com/Pester/Pester)包含有關撰寫 Pester 測試的詳細文件，從入門到最佳做法一應俱全。</span><span class="sxs-lookup"><span data-stu-id="6b72f-205">The [Pester project site in GitHub](https://github.com/Pester/Pester) includes good documentation on writing Pester tests, from getting started to best practices.</span></span>

<span data-ttu-id="6b72f-206">[高品質資源模組文件](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md) \(英文\) 中指出了測試目標涵蓋範圍，建議涵蓋 70% 的單元測試程式碼。</span><span class="sxs-lookup"><span data-stu-id="6b72f-206">The targets for test coverage are called out in the [High Quality Resource Module documentation](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), with 70% unit test code coverage recommended.</span></span>

## <a name="include-andor-link-to-license-terms"></a><span data-ttu-id="6b72f-207">包含和/或連結至授權條款</span><span class="sxs-lookup"><span data-stu-id="6b72f-207">Include and/or link to license terms</span></span>

<span data-ttu-id="6b72f-208">所有發行至「PowerShell 資源庫」的套件都必須指定授權條款，或是受到[使用規定](https://www.powershellgallery.com/policies/Terms) \(英文\) 底下「展示 A」中所包含的授權約束。</span><span class="sxs-lookup"><span data-stu-id="6b72f-208">All packages published to the PowerShell Gallery must specify the license terms, or be bound by the license included in the [Terms of Use](https://www.powershellgallery.com/policies/Terms) under "Exhibit A".</span></span>
<span data-ttu-id="6b72f-209">指定不同授權的最佳方法是在 PSData 中使用 LicenseURI 來提供授權的連結。</span><span class="sxs-lookup"><span data-stu-id="6b72f-209">The best approach to specifying a different license is to provide a link to the license using the LicenseURI in PSData.</span></span>
<span data-ttu-id="6b72f-210">您可以在＜建議的資訊清單欄位＞主題中找到相關範例。</span><span class="sxs-lookup"><span data-stu-id="6b72f-210">You can find an example in the Recommended Manifest Fields topic.</span></span>

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a><span data-ttu-id="6b72f-211">簽署您的程式碼</span><span class="sxs-lookup"><span data-stu-id="6b72f-211">Sign your code</span></span>

<span data-ttu-id="6b72f-212">程式碼簽署可以向使用者提供最高層級的保證，不僅可確保套件發行者安全可靠，也可確保他們取得的程式碼複本與發行者發行的完全相同。</span><span class="sxs-lookup"><span data-stu-id="6b72f-212">Code signing provides users with the highest level of assurance for who published the package, and that the copy of the code they acquire is exactly what the publisher released.</span></span>
<span data-ttu-id="6b72f-213">若要廣泛深入了解程式碼簽署，請參閱[程式碼簽署簡介](http://go.microsoft.com/fwlink/?LinkId=106296) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="6b72f-213">To learn more about code signing generally, see [Introduction to Code Signing](http://go.microsoft.com/fwlink/?LinkId=106296).</span></span>
<span data-ttu-id="6b72f-214">PowerShell 透過兩種主要的方法來支援程式碼簽署驗證：</span><span class="sxs-lookup"><span data-stu-id="6b72f-214">PowerShell supports validation of code signing through two primary approaches:</span></span>

- <span data-ttu-id="6b72f-215">簽署指令碼檔</span><span class="sxs-lookup"><span data-stu-id="6b72f-215">Signing script files</span></span>
- <span data-ttu-id="6b72f-216">類別目錄簽署模組</span><span class="sxs-lookup"><span data-stu-id="6b72f-216">Catalog signing a module</span></span>

<span data-ttu-id="6b72f-217">簽署 PowerShell 檔案是一個廣為接受的方法，可確保所要執行的程式碼是由可靠的來源產生的，並且尚未經過修改。</span><span class="sxs-lookup"><span data-stu-id="6b72f-217">Signing PowerShell files is a well-established approach to ensuring that the code being executed was produced by a reliable source, and has not been modified.</span></span>
<span data-ttu-id="6b72f-218">如需有關如何簽署 PowerShell 指令碼檔的詳細資料，請參閱[關於簽署](/powershell/module/microsoft.powershell.core/about/about_signing) \(英文\) 主題。</span><span class="sxs-lookup"><span data-stu-id="6b72f-218">Details on how to sign PowerShell script files is covered in the [About Signing](/powershell/module/microsoft.powershell.core/about/about_signing) topic.</span></span>
<span data-ttu-id="6b72f-219">大致而言，您可以將簽章新增至 PowerShell 在載入指令碼時驗證的任何 .PS1 檔案中。</span><span class="sxs-lookup"><span data-stu-id="6b72f-219">In overview, a signature can be added to any .PS1 file that PowerShell validates when the script is loaded.</span></span>
<span data-ttu-id="6b72f-220">您可以使用[執行原則](/powershell/module/microsoft.powershell.core/about/about_execution_policies) Cmdlet 來限制 PowerShell，以確保所使用的是已簽署的指令碼。</span><span class="sxs-lookup"><span data-stu-id="6b72f-220">PowerShell can be constrained using the [Execution Policy](/powershell/module/microsoft.powershell.core/about/about_execution_policies) cmdlets to ensure use of signed scripts.</span></span>

<span data-ttu-id="6b72f-221">類別目錄簽署模組是 PowerShell 5.1 版中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="6b72f-221">Catalog signing modules is a feature added to PowerShell in version 5.1.</span></span>
<span data-ttu-id="6b72f-222">如需了解如何簽署模組，請參閱[類別目錄 Cmdlet](/powershell/wmf/5.1/catalog-cmdlets) 主題。</span><span class="sxs-lookup"><span data-stu-id="6b72f-222">How to sign a module is covered in the [Catalog Cmdlets](/powershell/wmf/5.1/catalog-cmdlets) topic.</span></span>
<span data-ttu-id="6b72f-223">大致而言，簽署類別目錄的方式是建立類別目錄檔案 (包含模組中每個檔案的雜湊值)，然後簽署該檔案。</span><span class="sxs-lookup"><span data-stu-id="6b72f-223">In overview, catalog signing is done by creating a catalog file, which contains a hash value for every file in the module, and then signing that file.</span></span>
<span data-ttu-id="6b72f-224">PowerShellGet publish-module、install-module、save-module 與 update-module Cmdlet 會檢查簽章以確保檔案有效，然後確認每個套件的雜湊值與類別目錄中的內容相符。</span><span class="sxs-lookup"><span data-stu-id="6b72f-224">The PowerShellGet publish-module, install-module, save-module, and update-module cmdlets will check the signature to ensure it is valid, then confirm that the hash value for each package matches what is in the catalog.</span></span>
<span data-ttu-id="6b72f-225">如果系統上已安裝舊版的模組，install-module 將會確認新版本的簽署授權單位與先前安裝的相符。</span><span class="sxs-lookup"><span data-stu-id="6b72f-225">If a previous version of the module is installed on the system, install-module will confirm that the signing authority for the new version matches what was previously installed.</span></span>
<span data-ttu-id="6b72f-226">類別目錄簽署可以與簽署指令碼檔案搭配運作，但不會取代其功能。</span><span class="sxs-lookup"><span data-stu-id="6b72f-226">Catalog signing works with, but does not replace signing script files.</span></span> <span data-ttu-id="6b72f-227">PowerShell 不會在載入模組時驗證類別目錄簽章。</span><span class="sxs-lookup"><span data-stu-id="6b72f-227">PowerShell does not validate catalog signatures at module load time.</span></span>

## <a name="follow-semver-guidelines-for-versioning"></a><span data-ttu-id="6b72f-228">遵循 SemVer 方針來進行版本設定</span><span class="sxs-lookup"><span data-stu-id="6b72f-228">Follow SemVer guidelines for versioning</span></span>

<span data-ttu-id="6b72f-229">[SemVer](http://semver.org/) 是一個公開慣例，說明如何形成版本結構及變更版本以便輕鬆解譯變更。</span><span class="sxs-lookup"><span data-stu-id="6b72f-229">[SemVer](http://semver.org/) is a public convention that describes how to structure and change a version to allow easy intepretation of changes.</span></span>
<span data-ttu-id="6b72f-230">您套件的版本必須包含在資訊清單資料中。</span><span class="sxs-lookup"><span data-stu-id="6b72f-230">The version for your package must be included in the manifest data.</span></span>

- <span data-ttu-id="6b72f-231">該版本的結構應該是 3 個以句號分隔的數值區塊，例如 0.1.1 或 4.11.192</span><span class="sxs-lookup"><span data-stu-id="6b72f-231">The version should be structured as 3 numeric blocks separated by periods, as in 0.1.1 or 4.11.192</span></span>
- <span data-ttu-id="6b72f-232">開頭為 "0" 的版本表示該套件還不適用於生產環境，並且如果 "0" 是唯一使用的數字，則第一個數字應該只能以 "0" 為開頭</span><span class="sxs-lookup"><span data-stu-id="6b72f-232">Versions starting with "0" indicate that the package is not yet production ready, and the first number should only begin with "0" if that is the only number used</span></span>
- <span data-ttu-id="6b72f-233">第一個數字的變更 (從 1.9.9999 變更為 2.0.0) 代表版本之間的主要且重大變更</span><span class="sxs-lookup"><span data-stu-id="6b72f-233">Changes in the first number (1.9.9999 to 2.0.0) indicate major and breaking changes between the versions</span></span>
- <span data-ttu-id="6b72f-234">第二個數字 (1.1 to 1.2) 的變更代表功能層級變更，例如加入新的 Cmdlet 到某個模組中</span><span class="sxs-lookup"><span data-stu-id="6b72f-234">Changes to the second number (1.1 to 1.2) indicate feature-level changes, such as adding new cmdlets to a module</span></span>
- <span data-ttu-id="6b72f-235">第三個數字的變更代表非重大變更，例如新參數、更新的範例或新測試</span><span class="sxs-lookup"><span data-stu-id="6b72f-235">Changes to the third number indicate non-breaking changes, such as new parameters, updated samples, or new tests</span></span>
- <span data-ttu-id="6b72f-236">列出版本時，PowerShell 會將版本當作字串來排序，因此會將 1.01.0 視為比 1.001.0 還要新</span><span class="sxs-lookup"><span data-stu-id="6b72f-236">When listing versions, PowerShell will sort the versions as strings, so 1.01.0 will be treated as greater than 1.001.0</span></span>

<span data-ttu-id="6b72f-237">PowerShell 的建立時間是在 SemVer 發行前，因此它支援 SemVer 的大多數但非全部元素，具體而言：</span><span class="sxs-lookup"><span data-stu-id="6b72f-237">PowerShell was created before SemVer was published, so it provides support for most but not all elements of SemVer, specifically:</span></span>

- <span data-ttu-id="6b72f-238">它不支援版本號碼中的發行前版本字串。</span><span class="sxs-lookup"><span data-stu-id="6b72f-238">It does not support prerelease strings in version numbers.</span></span> <span data-ttu-id="6b72f-239">當發行者想要在提供 1.0.0 版之後提供某個新主要版本的預覽版本時，該字串會相當有用。</span><span class="sxs-lookup"><span data-stu-id="6b72f-239">This is useful when a publisher wishes to deliver a preview release of a new major version after providing a version 1.0.0.</span></span> <span data-ttu-id="6b72f-240">在未來的「PowerShell 資源庫」和 PowerShellGet Cmdlet 版本中將會支援此功能。</span><span class="sxs-lookup"><span data-stu-id="6b72f-240">This will be supported in a future release of the PowerShell Gallery and PowerShellGet cmdlets.</span></span>
- <span data-ttu-id="6b72f-241">PowerShell 和「PowerShell 資源庫」允許使用含有 1、2 及 4 個區段的版本字串。</span><span class="sxs-lookup"><span data-stu-id="6b72f-241">PowerShell and the PowerShell Gallery allow version strings with 1, 2, and 4 segments.</span></span> <span data-ttu-id="6b72f-242">許多早期的模組並未依循這些指導方針，而來自 Microsoft 的產品版本會包含組建資訊作為第 4 個數字區塊 (例如 5.1.14393.1066)。</span><span class="sxs-lookup"><span data-stu-id="6b72f-242">Many early modules did not follow the guidelines, and product releases from Microsoft include build information as a 4th block of numbers (for example 5.1.14393.1066).</span></span> <span data-ttu-id="6b72f-243">從版本設定的觀點來看，會將這些差異都予以忽略。</span><span class="sxs-lookup"><span data-stu-id="6b72f-243">From a versioning standpoint, these differences are ignored.</span></span>

## <a name="test-using-a-local-repository"></a><span data-ttu-id="6b72f-244">使用本機存放庫來測試</span><span class="sxs-lookup"><span data-stu-id="6b72f-244">Test using a local repository</span></span>

<span data-ttu-id="6b72f-245">PowerShell 資源庫並不適合作為測試發行程序的目標。</span><span class="sxs-lookup"><span data-stu-id="6b72f-245">The PowerShell Gallery is not designed to be a target for testing the publishing process.</span></span>
<span data-ttu-id="6b72f-246">若要測試發行至 PowerShell 資源庫的端點對端點程序，最佳方式為設定並使用您自己的本機存放庫。</span><span class="sxs-lookup"><span data-stu-id="6b72f-246">The best way to test out the end-to-end process of publishing to the PowerShell Gallery is to set up and use your own local repository.</span></span>
<span data-ttu-id="6b72f-247">這可以由以下方法達成：</span><span class="sxs-lookup"><span data-stu-id="6b72f-247">This can be done in a few ways, including:</span></span>

- <span data-ttu-id="6b72f-248">在 Github 中使用 [PS 私人資源庫專案](https://github.com/PowerShell/PSPrivateGallery)來設定本機 PowerShell 資源庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b72f-248">Set up a local PowerShell Gallery instance, using the [PS Private Gallery project](https://github.com/PowerShell/PSPrivateGallery) in Github.</span></span> <span data-ttu-id="6b72f-249">此預覽專案會協助您設定 PowerShell 資源庫執行個體，讓您可以控制及用於測試。</span><span class="sxs-lookup"><span data-stu-id="6b72f-249">This preview project will help you set up an instance of the PowerShell Gallery that you can control, and use for your tests.</span></span>
- <span data-ttu-id="6b72f-250">設定[內部 NuGet 存放庫](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/)。</span><span class="sxs-lookup"><span data-stu-id="6b72f-250">Set up an [internal Nuget repository](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/).</span></span> <span data-ttu-id="6b72f-251">這個方法的設定較為複雜，但是能夠驗證更多需求。值得注意的是，不論您發行時目標是否有相依性，都能使用 API 金鑰進行驗證。</span><span class="sxs-lookup"><span data-stu-id="6b72f-251">This will require more work to set up, but will have the advantage of validating a few more of the requirements, notably validating use of an API key, and whether or not dependencies are present in the target when you publish.</span></span>
- <span data-ttu-id="6b72f-252">將檔案共用設定為測試「存放庫」。</span><span class="sxs-lookup"><span data-stu-id="6b72f-252">Set up a file share as the test “repository”.</span></span> <span data-ttu-id="6b72f-253">這很容易設定，但因為其為檔案共用，所以無法執行上述的驗證。</span><span class="sxs-lookup"><span data-stu-id="6b72f-253">This is easy to set up, but since it is a file share, the validations noted above will not take place.</span></span> <span data-ttu-id="6b72f-254">在此案例中，因為檔案共用不會檢查 (必要的) API 金鑰，所以您可以使用發行到 PowerShell 資源庫的相同金鑰，這可以說是潛在優點。</span><span class="sxs-lookup"><span data-stu-id="6b72f-254">One potential advantage in this case is that the file share does not check the (required) API key, so you can use the same key you would to publish to the PowerShell Gallery.</span></span>

<span data-ttu-id="6b72f-255">透過以上任一種方法，您可以使用 Register-PSRepository 來定義新的「存放庫」，用於 Publish-Module 的 -Repository 屬性。</span><span class="sxs-lookup"><span data-stu-id="6b72f-255">With any of these solutions, use Register-PSRepository to define a new "repository", which you use in the -Repository property for Publish-Module.</span></span>

<span data-ttu-id="6b72f-256">另外為測試發行補充一點：您發行到 PowerShell 資源庫的任何套件都必須在營運團隊的協助下才能刪除，因此他們會確認沒有任何內容相依於您要發行的套件。</span><span class="sxs-lookup"><span data-stu-id="6b72f-256">One additional point about test publishing: any package you publish to the PowerShell Gallery cannot be deleted without help from the operations team, who will confirm that nothing is dependent upon the package you wish to publish.</span></span>
<span data-ttu-id="6b72f-257">基於此原因，我們不支援將 PowerShell 資源庫用作測試目標，且會與任何這樣做的發行者連絡。</span><span class="sxs-lookup"><span data-stu-id="6b72f-257">For that reason, we do not support the PowerShell Gallery as a testing target, and will contact any publisher who does so.</span></span>

## <a name="use-powershellget-to-publish"></a><span data-ttu-id="6b72f-258">使用 PowerShellGet 發佈</span><span class="sxs-lookup"><span data-stu-id="6b72f-258">Use PowerShellGet to publish</span></span>

<span data-ttu-id="6b72f-259">強烈建議發行者搭配 PowerShell 資源庫使用 Publish-Module 和 Publish-Script Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6b72f-259">It is strongly recommended that publishers use the Publish-Module and Publish-Script cmdlets when working with the PowerShell Gallery.</span></span>
<span data-ttu-id="6b72f-260">已建立 PowerShellGet，因此您不需要記住透過發佈至 PowerShell 資源庫進行安裝的重要詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6b72f-260">PowerShellGet has been created to help you avoid remembering important details about installing from and publishing to the PowerShell Gallery.</span></span>
<span data-ttu-id="6b72f-261">有時候，發行者會選擇略過 PowerShellGet 並使用 NuGet 用戶端或 PackageManagement Cmdlet，而不是使用 Publish-Module。</span><span class="sxs-lookup"><span data-stu-id="6b72f-261">On occasion, publishers have chosen to skip PowerShellGet and use the NuGet client, or PackageManagement cmdlets, instead of Publish-Module.</span></span>
<span data-ttu-id="6b72f-262">有幾個容易忽略的詳細資料會導致各種不同的支援要求。</span><span class="sxs-lookup"><span data-stu-id="6b72f-262">There are a number of details that are easily missed, which results in a variety of support requests.</span></span>

<span data-ttu-id="6b72f-263">如有任何原因導致您無法使用 Publish-Module 或 Publish-Script，請讓我們知道。</span><span class="sxs-lookup"><span data-stu-id="6b72f-263">If there is a reason that you cannot use Publish-Module or Publish-Script, please let us know.</span></span>
<span data-ttu-id="6b72f-264">請在 PowerShellGet GitHub 存放庫中提出問題，並提供導致您選擇 NuGet 或 PackageManagement 的詳細原因。</span><span class="sxs-lookup"><span data-stu-id="6b72f-264">File an issue in the PowerShellGet GitHub repo, and provide the details that cause you to choose NuGet or PackageManagement.</span></span>

## <a name="recommended-workflow"></a><span data-ttu-id="6b72f-265">建議的工作流程</span><span class="sxs-lookup"><span data-stu-id="6b72f-265">Recommended workflow</span></span>

<span data-ttu-id="6b72f-266">針對發行至「PowerShell 資源庫」的套件，我們找到的最成功方法是：</span><span class="sxs-lookup"><span data-stu-id="6b72f-266">The most successful approach we have found for packages published to the PowerShell Gallery is this:</span></span>

- <span data-ttu-id="6b72f-267">在開放原始碼的專案網站中進行初始開發。</span><span class="sxs-lookup"><span data-stu-id="6b72f-267">Do initial development in a an open-source project site.</span></span> <span data-ttu-id="6b72f-268">PowerShell 小組使用的是 Github。</span><span class="sxs-lookup"><span data-stu-id="6b72f-268">The PowerShell Team uses Github.</span></span>
- <span data-ttu-id="6b72f-269">利用檢閱者和 [Powershell 指令碼分析程式](https://aka.ms/psscriptanalyzer)的意見反應來讓程式碼變得穩定</span><span class="sxs-lookup"><span data-stu-id="6b72f-269">Use feedback from reviewers and [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer) to get the code to stable state</span></span>
- <span data-ttu-id="6b72f-270">包含文件，讓其他使用者了解如何使用您的作品</span><span class="sxs-lookup"><span data-stu-id="6b72f-270">Include documentation, so others know how to use your work</span></span>
- <span data-ttu-id="6b72f-271">使用本機存放庫測試發行動作。</span><span class="sxs-lookup"><span data-stu-id="6b72f-271">Test out the publishing action using a local repository.</span></span>
- <span data-ttu-id="6b72f-272">將穩定版或 Alpha 版發行至「PowerShell 資源庫」，其中務必包含文件和您專案網站的連結</span><span class="sxs-lookup"><span data-stu-id="6b72f-272">Publish a stable or Alpha release to the PowerShell Gallery, making sure to include the documentation and link to your project site</span></span>
- <span data-ttu-id="6b72f-273">收集意見反應並在您的專案網站中逐一查看程式碼，然後將穩定的更新發行至「PowerShell 資源庫」</span><span class="sxs-lookup"><span data-stu-id="6b72f-273">Gather feedback and iterate on the code in your project site, then publish stable updates to the PowerShell Gallery</span></span>
- <span data-ttu-id="6b72f-274">在您的專案和模組中新增範例和 Pester 測試</span><span class="sxs-lookup"><span data-stu-id="6b72f-274">Add examples and Pester tests in your project and your module</span></span>
- <span data-ttu-id="6b72f-275">決定是否要以程式碼簽署您的套件</span><span class="sxs-lookup"><span data-stu-id="6b72f-275">Decide if you want to code sign your package</span></span>
- <span data-ttu-id="6b72f-276">當您覺得專案已經準備好在生產環境中使用時，將 1.0.0 版本發行至「PowerShell 資源庫」</span><span class="sxs-lookup"><span data-stu-id="6b72f-276">When you feel the project is ready to use in a production environment, publish a 1.0.0 version to the PowerShell Gallery</span></span>
- <span data-ttu-id="6b72f-277">繼續收集意見反應並根據使用者提供的意見逐一查看您的程式碼</span><span class="sxs-lookup"><span data-stu-id="6b72f-277">Continue to gather feedback and iterate on your code based on user input</span></span>

