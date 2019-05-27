---
title: PowerShell Core 支援週期
description: 控管 PowerShell Core 支援的原則
ms.date: 08/06/2018
ms.openlocfilehash: b8dd4891ecf245b87c3fe2fa61cd241a12209b57
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854384"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="8cfbd-103">PowerShell Core 支援週期</span><span class="sxs-lookup"><span data-stu-id="8cfbd-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="8cfbd-104">PowerShell Core 是一組可以與 Windows PowerShell 分開出貨、安裝和設定的不同工具和元件。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="8cfbd-105">因此，Windows 7/8.1/10 或 Windows Server 授權合約不包含 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="8cfbd-106">不過，傳統 Microsoft 支援合約支援 PowerShell Core，包含 [Premier][]、[Microsoft 企業授權][enterprise-agreement]和[軟體保證權益][assurance]。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="8cfbd-107">您也可以提出您問題的支援要求，付費獲得 PowerShell Core 的[輔助支援][]。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="8cfbd-108">社群支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-108">Community Support</span></span>

<span data-ttu-id="8cfbd-109">我們也會在您可提出問題、Bug 或功能要求的 GitHub 上提供[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="8cfbd-110">或者，您可以在一般 [Microsoft Community][] 或 Microsoft [PowerShell Tech Community][] 上尋求其他社群成員的協助。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="8cfbd-111">我們不保證社群能夠及時處理或解決您的問題。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="8cfbd-112">如果您有需要立即注意的問題，則應該使用傳統付費支援選項。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="8cfbd-113">PowerShell Core 生命週期</span><span class="sxs-lookup"><span data-stu-id="8cfbd-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="8cfbd-114">PowerShell Core 會採用 [Microsoft 現代化生命週期原則 ][modern]。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="8cfbd-115">此支援生命週期是要保持客戶的最新版本最新資訊。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="8cfbd-116">大約每六個月更新 PowerShell Core 6.x 版分支一次 (例如 6.0、6.1、6.2 等等)</span><span class="sxs-lookup"><span data-stu-id="8cfbd-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8cfbd-117">您必須在每個新次要版本發行之後的六個月內進行更新，才能持續接收支援。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="8cfbd-118">例如，如果 PowerShell Core 6.1 是在 2018 年 7 月1 日發行，就必須在 2019 年 1 月 1 日之前更新至 PowerShell Core 6.1 以繼續獲得支援。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8cfbd-119">您必須在每個新修補程式版本發行之後的 30 天內進行更新，才能繼續接收支援。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="8cfbd-120">例如，如果您是執行 PowerShell Core 6.1，而且 6.1.3 在 2019 年 2 月19 日發行，就必須在 2019 年 3 月 21 日 (也就是發行之後的第 30 天) 之前更新至 PowerShell Core 6.1.3 以繼續獲得支援。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="8cfbd-121">如果需要修補程式，我們會在下一次累計更新中發行。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

<span data-ttu-id="8cfbd-122">現代化生命週期原則也需要 Microsoft 在中斷產品 (即 PowerShell Core) 支援之前的 12 個月通知客戶。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-122">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="8cfbd-123">最後，我們預期 PowerShell Core 會採用 「長期維護」方法。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-123">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="8cfbd-124">透過這個方法，我們僅需要提供服務和安全性更新，就能保持對特定 6.x 分支/版本的支援。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-124">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="8cfbd-125">支援的平台</span><span class="sxs-lookup"><span data-stu-id="8cfbd-125">Supported platforms</span></span>

<span data-ttu-id="8cfbd-126">請參閱下表，了解您使用的 PowerShell Core 版本所正式支援的平台。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-126">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="8cfbd-127">我們的社群也針對部分平台貢獻了套件，但這些套件未受正式支援。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-127">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="8cfbd-128">這些套件在表格中標示為 `Community`。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-128">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="8cfbd-129">列為 `Experimental` 的平台為非正式支援，但可用於實驗和提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-129">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="8cfbd-130">6.1</span><span class="sxs-lookup"><span data-stu-id="8cfbd-130">6.1</span></span>         | <span data-ttu-id="8cfbd-131">6.2</span><span class="sxs-lookup"><span data-stu-id="8cfbd-131">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="8cfbd-132">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="8cfbd-132">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="8cfbd-133">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-133">Supported</span></span>   | <span data-ttu-id="8cfbd-134">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-134">Supported</span></span>   |
| <span data-ttu-id="8cfbd-135">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="8cfbd-135">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="8cfbd-136">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-136">Supported</span></span>   | <span data-ttu-id="8cfbd-137">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-137">Supported</span></span>   |
| <span data-ttu-id="8cfbd-138">[Windows Server 半年通道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="8cfbd-138">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="8cfbd-139">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-139">Supported</span></span>   | <span data-ttu-id="8cfbd-140">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-140">Supported</span></span>   |
| <span data-ttu-id="8cfbd-141">Ubuntu 16.04 與 18.04</span><span class="sxs-lookup"><span data-stu-id="8cfbd-141">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="8cfbd-142">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-142">Supported</span></span>   | <span data-ttu-id="8cfbd-143">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-143">Supported</span></span>   |
| <span data-ttu-id="8cfbd-144">Ubuntu 18.10 (透過 Snap 套件)</span><span class="sxs-lookup"><span data-stu-id="8cfbd-144">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="8cfbd-145">群體</span><span class="sxs-lookup"><span data-stu-id="8cfbd-145">Community</span></span>   | <span data-ttu-id="8cfbd-146">群體</span><span class="sxs-lookup"><span data-stu-id="8cfbd-146">Community</span></span>   |
| <span data-ttu-id="8cfbd-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="8cfbd-147">Debian 9</span></span>                                          | <span data-ttu-id="8cfbd-148">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-148">Supported</span></span>   | <span data-ttu-id="8cfbd-149">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-149">Supported</span></span>   |
| <span data-ttu-id="8cfbd-150">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="8cfbd-150">CentOS 7</span></span>                                          | <span data-ttu-id="8cfbd-151">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-151">Supported</span></span>   | <span data-ttu-id="8cfbd-152">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-152">Supported</span></span>   |
| <span data-ttu-id="8cfbd-153">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="8cfbd-153">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="8cfbd-154">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-154">Supported</span></span>   | <span data-ttu-id="8cfbd-155">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-155">Supported</span></span>   |
| <span data-ttu-id="8cfbd-156">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="8cfbd-156">openSUSE 42.3</span></span>                                     | <span data-ttu-id="8cfbd-157">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-157">Supported</span></span>   | <span data-ttu-id="8cfbd-158">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-158">Supported</span></span>   |
| <span data-ttu-id="8cfbd-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="8cfbd-159">Fedora 28</span></span>                                         | <span data-ttu-id="8cfbd-160">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-160">Supported</span></span>   | <span data-ttu-id="8cfbd-161">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-161">Supported</span></span>   |
| <span data-ttu-id="8cfbd-162">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="8cfbd-162">macOS 10.12+</span></span>                                      | <span data-ttu-id="8cfbd-163">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-163">Supported</span></span>   | <span data-ttu-id="8cfbd-164">支援</span><span class="sxs-lookup"><span data-stu-id="8cfbd-164">Supported</span></span>   |
| <span data-ttu-id="8cfbd-165">Arch</span><span class="sxs-lookup"><span data-stu-id="8cfbd-165">Arch</span></span>                                              | <span data-ttu-id="8cfbd-166">群體</span><span class="sxs-lookup"><span data-stu-id="8cfbd-166">Community</span></span>   | <span data-ttu-id="8cfbd-167">群體</span><span class="sxs-lookup"><span data-stu-id="8cfbd-167">Community</span></span>   |
| <span data-ttu-id="8cfbd-168">Raspbian</span><span class="sxs-lookup"><span data-stu-id="8cfbd-168">Raspbian</span></span>                                          | <span data-ttu-id="8cfbd-169">群體</span><span class="sxs-lookup"><span data-stu-id="8cfbd-169">Community</span></span>   | <span data-ttu-id="8cfbd-170">群體</span><span class="sxs-lookup"><span data-stu-id="8cfbd-170">Community</span></span>   |
| <span data-ttu-id="8cfbd-171">Kali</span><span class="sxs-lookup"><span data-stu-id="8cfbd-171">Kali</span></span>                                              | <span data-ttu-id="8cfbd-172">群體</span><span class="sxs-lookup"><span data-stu-id="8cfbd-172">Community</span></span>   | <span data-ttu-id="8cfbd-173">群體</span><span class="sxs-lookup"><span data-stu-id="8cfbd-173">Community</span></span>   |
| <span data-ttu-id="8cfbd-174">AppImage (作用於多個 Linux 平台)</span><span class="sxs-lookup"><span data-stu-id="8cfbd-174">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="8cfbd-175">群體</span><span class="sxs-lookup"><span data-stu-id="8cfbd-175">Community</span></span>   | <span data-ttu-id="8cfbd-176">群體</span><span class="sxs-lookup"><span data-stu-id="8cfbd-176">Community</span></span>   |
| [<span data-ttu-id="8cfbd-177">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="8cfbd-177">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="8cfbd-178">請參閱備註</span><span class="sxs-lookup"><span data-stu-id="8cfbd-178">See note</span></span>    | <span data-ttu-id="8cfbd-179">請參閱備註</span><span class="sxs-lookup"><span data-stu-id="8cfbd-179">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="8cfbd-180">和您執行套件所在的散發一樣，也支援 Snap 套件。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-180">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="8cfbd-181">PowerShell 版本生命週期結束</span><span class="sxs-lookup"><span data-stu-id="8cfbd-181">PowerShell release end of life</span></span>

<span data-ttu-id="8cfbd-182">下表根據 [PowerShell Core 的生命週期](#lifecycle-of-powershell-core)，列出各種版本的停止支援日期。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-182">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="8cfbd-183">版本</span><span class="sxs-lookup"><span data-stu-id="8cfbd-183">Version</span></span> | <span data-ttu-id="8cfbd-184">生命週期結束</span><span class="sxs-lookup"><span data-stu-id="8cfbd-184">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="8cfbd-185">6.0</span><span class="sxs-lookup"><span data-stu-id="8cfbd-185">6.0</span></span>     | <span data-ttu-id="8cfbd-186">2019 年 2 月 13 日</span><span class="sxs-lookup"><span data-stu-id="8cfbd-186">February 13, 2019</span></span>             |
| <span data-ttu-id="8cfbd-187">6.1</span><span class="sxs-lookup"><span data-stu-id="8cfbd-187">6.1</span></span>     | <span data-ttu-id="8cfbd-188">2019 年 9 月 28 日</span><span class="sxs-lookup"><span data-stu-id="8cfbd-188">September 28, 2019</span></span>            |
| <span data-ttu-id="8cfbd-189">6.2</span><span class="sxs-lookup"><span data-stu-id="8cfbd-189">6.2</span></span>     | <span data-ttu-id="8cfbd-190">7 發行後的 6 個月</span><span class="sxs-lookup"><span data-stu-id="8cfbd-190">6 months after 7 releases</span></span>     |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="8cfbd-191">終止支援的平台</span><span class="sxs-lookup"><span data-stu-id="8cfbd-191">Platforms, which are out of support</span></span>

<span data-ttu-id="8cfbd-192">當平台版本到達平台擁有者所定義的生命週期結束時間時，PowerShell Core 也會停止支援該平台版本。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-192">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="8cfbd-193">先前推出的套件仍然可供需要存取的客戶取得，但將不再提供任何類型的正式支援和更新。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-193">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="8cfbd-194">這表示發行版本擁有者已停止支援以下版本，因此不再支援。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-194">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="8cfbd-195">作業系統</span><span class="sxs-lookup"><span data-stu-id="8cfbd-195">OS</span></span>       | <span data-ttu-id="8cfbd-196">版本</span><span class="sxs-lookup"><span data-stu-id="8cfbd-196">Version</span></span> | <span data-ttu-id="8cfbd-197">生命週期結束</span><span class="sxs-lookup"><span data-stu-id="8cfbd-197">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="8cfbd-198">Fedora</span><span class="sxs-lookup"><span data-stu-id="8cfbd-198">Fedora</span></span>   | <span data-ttu-id="8cfbd-199">24</span><span class="sxs-lookup"><span data-stu-id="8cfbd-199">24</span></span>      | [<span data-ttu-id="8cfbd-200">2017 年 8 月</span><span class="sxs-lookup"><span data-stu-id="8cfbd-200">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="8cfbd-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="8cfbd-201">Fedora</span></span>   | <span data-ttu-id="8cfbd-202">25</span><span class="sxs-lookup"><span data-stu-id="8cfbd-202">25</span></span>      | [<span data-ttu-id="8cfbd-203">2017 年 12 月</span><span class="sxs-lookup"><span data-stu-id="8cfbd-203">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="8cfbd-204">Fedora</span><span class="sxs-lookup"><span data-stu-id="8cfbd-204">Fedora</span></span>   | <span data-ttu-id="8cfbd-205">26</span><span class="sxs-lookup"><span data-stu-id="8cfbd-205">26</span></span>      | [<span data-ttu-id="8cfbd-206">2018 年 5 月</span><span class="sxs-lookup"><span data-stu-id="8cfbd-206">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="8cfbd-207">openSUSE</span><span class="sxs-lookup"><span data-stu-id="8cfbd-207">openSUSE</span></span> | <span data-ttu-id="8cfbd-208">42.1</span><span class="sxs-lookup"><span data-stu-id="8cfbd-208">42.1</span></span>    | [<span data-ttu-id="8cfbd-209">2017 年 5 月</span><span class="sxs-lookup"><span data-stu-id="8cfbd-209">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="8cfbd-210">openSUSE</span><span class="sxs-lookup"><span data-stu-id="8cfbd-210">openSUSE</span></span> | <span data-ttu-id="8cfbd-211">42.2</span><span class="sxs-lookup"><span data-stu-id="8cfbd-211">42.2</span></span>    | [<span data-ttu-id="8cfbd-212">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="8cfbd-212">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="8cfbd-213">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="8cfbd-213">Ubuntu</span></span>   | <span data-ttu-id="8cfbd-214">16.10</span><span class="sxs-lookup"><span data-stu-id="8cfbd-214">16.10</span></span>   | [<span data-ttu-id="8cfbd-215">2017 年 7 月</span><span class="sxs-lookup"><span data-stu-id="8cfbd-215">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="8cfbd-216">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="8cfbd-216">Ubuntu</span></span>   | <span data-ttu-id="8cfbd-217">17.04</span><span class="sxs-lookup"><span data-stu-id="8cfbd-217">17.04</span></span>   | [<span data-ttu-id="8cfbd-218">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="8cfbd-218">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="8cfbd-219">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="8cfbd-219">Ubuntu</span></span>   | <span data-ttu-id="8cfbd-220">17.10</span><span class="sxs-lookup"><span data-stu-id="8cfbd-220">17.10</span></span>   | [<span data-ttu-id="8cfbd-221">2018 年 7 月</span><span class="sxs-lookup"><span data-stu-id="8cfbd-221">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="8cfbd-222">Debian</span><span class="sxs-lookup"><span data-stu-id="8cfbd-222">Debian</span></span>   | <span data-ttu-id="8cfbd-223">8</span><span class="sxs-lookup"><span data-stu-id="8cfbd-223">8</span></span>       | [<span data-ttu-id="8cfbd-224">2018 年 6 月</span><span class="sxs-lookup"><span data-stu-id="8cfbd-224">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="8cfbd-225">Fedora</span><span class="sxs-lookup"><span data-stu-id="8cfbd-225">Fedora</span></span>   | <span data-ttu-id="8cfbd-226">27</span><span class="sxs-lookup"><span data-stu-id="8cfbd-226">27</span></span>      | [<span data-ttu-id="8cfbd-227">2018 年 11 月</span><span class="sxs-lookup"><span data-stu-id="8cfbd-227">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="8cfbd-228">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="8cfbd-228">Ubuntu</span></span>   | <span data-ttu-id="8cfbd-229">14.04</span><span class="sxs-lookup"><span data-stu-id="8cfbd-229">14.04</span></span>   | [<span data-ttu-id="8cfbd-230">2019 年 4 月</span><span class="sxs-lookup"><span data-stu-id="8cfbd-230">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="8cfbd-231">授權附註</span><span class="sxs-lookup"><span data-stu-id="8cfbd-231">Notes on licensing</span></span>

<span data-ttu-id="8cfbd-232">PowerShell Core 是透過 [MIT 授權][]所發行。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-232">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="8cfbd-233">透過此授權，而且沒有付費支援合約，則使用者就只有[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-233">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="8cfbd-234">運用社群支援，Microsoft 不保證會回應或修正。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-234">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="8cfbd-235">Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="8cfbd-235">Windows PowerShell Module</span></span>

<span data-ttu-id="8cfbd-236">除非產品模組明確支援 PowerShell Core，否則 PowerShell Core 支援不會包括那些模組。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-236">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="8cfbd-237">例如，使用隨附為 Windows Server 一部分的 `ActiveDirectory` 模組，就是不支援的案例。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-237">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="8cfbd-238">不過，在某些情況下，未明確支援 PowerShell Core 的模組可能會相容。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-238">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="8cfbd-239">安裝 [`WindowsPSModulePath`][] 模組，即可將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-239">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="8cfbd-240">首先，從 PowerShell 資源庫安裝 `WindowsPSModulePath` 模組：</span><span class="sxs-lookup"><span data-stu-id="8cfbd-240">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="8cfbd-241">安裝此模組之後，請執行 `Add-WindowsPSModulePath` Cmdlet，以將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="8cfbd-241">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="8cfbd-242">實驗性功能</span><span class="sxs-lookup"><span data-stu-id="8cfbd-242">Experimental features</span></span>

<span data-ttu-id="8cfbd-243">[實驗性功能][]僅限於[社群支援](#community-support)。</span><span class="sxs-lookup"><span data-stu-id="8cfbd-243">[Experimental features][] are limited to [community support](#community-support).</span></span>

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[社群支援]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[輔助支援]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT 授權]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[實驗性功能]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
[Experimental features]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
