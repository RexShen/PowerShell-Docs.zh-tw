---
title: PowerShell Core 支援週期
description: 控管 PowerShell Core 支援的原則
ms.date: 08/06/2018
ms.openlocfilehash: 60999ed54ca3be15232ffee3ab0c49cb94873a8f
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986745"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="1abf3-103">PowerShell Core 支援週期</span><span class="sxs-lookup"><span data-stu-id="1abf3-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="1abf3-104">PowerShell Core 是一組可以與 Windows PowerShell 分開出貨、安裝和設定的不同工具和元件。</span><span class="sxs-lookup"><span data-stu-id="1abf3-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span> <span data-ttu-id="1abf3-105">因此，Windows 7/8.1/10 或 Windows Server 授權合約不包含 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="1abf3-105">So, PowerShell Core isn't included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="1abf3-106">不過，PowerShell Core 是由傳統 Microsoft 支援合約支援，包含[頂級][]、[Microsoft Enterprise 合約][enterprise-agreement]與[微軟軟體保證][assurance]。</span><span class="sxs-lookup"><span data-stu-id="1abf3-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="1abf3-107">您也可以提出您問題的支援要求，付費獲得 PowerShell Core 的[輔助支援][]。</span><span class="sxs-lookup"><span data-stu-id="1abf3-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="1abf3-108">社群支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-108">Community Support</span></span>

<span data-ttu-id="1abf3-109">我們也會在您可提出問題、Bug 或功能要求的 GitHub 上提供[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="1abf3-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="1abf3-110">或者，您可以在一般 [Microsoft Community][] 或 Microsoft [PowerShell Tech Community][] 上尋求其他社群成員的協助。</span><span class="sxs-lookup"><span data-stu-id="1abf3-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span> <span data-ttu-id="1abf3-111">我們不保證社群能夠及時處理或解決您的問題。</span><span class="sxs-lookup"><span data-stu-id="1abf3-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span> <span data-ttu-id="1abf3-112">如果您有需要立即注意的問題，則應該使用傳統付費支援選項。</span><span class="sxs-lookup"><span data-stu-id="1abf3-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="1abf3-113">PowerShell Core 生命週期</span><span class="sxs-lookup"><span data-stu-id="1abf3-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="1abf3-114">PowerShell Core 會採用 [Microsoft 現代化生命週期原則][modern]。</span><span class="sxs-lookup"><span data-stu-id="1abf3-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span> <span data-ttu-id="1abf3-115">此支援生命週期是要保持客戶的最新版本最新資訊。</span><span class="sxs-lookup"><span data-stu-id="1abf3-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="1abf3-116">大約每六個月更新 PowerShell Core 6.x 版分支一次 (例如 6.0、6.1、6.2 等等)</span><span class="sxs-lookup"><span data-stu-id="1abf3-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1abf3-117">您必須在每個新次要版本發行之後的六個月內進行更新，才能持續接收支援。</span><span class="sxs-lookup"><span data-stu-id="1abf3-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="1abf3-118">例如，如果 PowerShell Core 6.1 是在 2018 年 7 月1 日發行，就必須在 2019 年 1 月 1 日之前更新至 PowerShell Core 6.1 以繼續獲得支援。</span><span class="sxs-lookup"><span data-stu-id="1abf3-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1abf3-119">您必須在每個新修補程式版本發行之後的 30 天內進行更新，才能繼續接收支援。</span><span class="sxs-lookup"><span data-stu-id="1abf3-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="1abf3-120">例如，如果您是執行 PowerShell Core 6.1，而且 6.1.3 在 2019 年 2 月19 日發行，您就必須在 2019 年 3 月 21 日 (也就是發行之後的第 30 天) 之前更新至 PowerShell Core 6.1.3 以繼續獲得支援。</span><span class="sxs-lookup"><span data-stu-id="1abf3-120">For example, If you're running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span> <span data-ttu-id="1abf3-121">如果需要修補程式，我們會在下一次累計更新中發行。</span><span class="sxs-lookup"><span data-stu-id="1abf3-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

<span data-ttu-id="1abf3-122">現代化生命週期原則也需要 Microsoft 在中斷產品 (即 PowerShell Core) 支援之前的 12 個月通知客戶。</span><span class="sxs-lookup"><span data-stu-id="1abf3-122">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="1abf3-123">最後，我們預期 PowerShell Core 會採用長期維護方法。</span><span class="sxs-lookup"><span data-stu-id="1abf3-123">Eventually, we expect PowerShell Core will adopt the long-term servicing approach.</span></span> <span data-ttu-id="1abf3-124">透過這個方法，我們僅需要提供服務和安全性更新，就能保持對特定 6.x 分支/版本的支援。</span><span class="sxs-lookup"><span data-stu-id="1abf3-124">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="1abf3-125">支援的平台</span><span class="sxs-lookup"><span data-stu-id="1abf3-125">Supported platforms</span></span>

<span data-ttu-id="1abf3-126">若要確認您使用的平台與 PowerShell Core 版本是受支援的，請參閱下表。</span><span class="sxs-lookup"><span data-stu-id="1abf3-126">To confirm if your platform and version of PowerShell Core are officially supported, see the following table.</span></span>

<span data-ttu-id="1abf3-127">我們的社群也針對部分平台貢獻了套件，但這些套件未受正式支援。</span><span class="sxs-lookup"><span data-stu-id="1abf3-127">Our community has also contributed packages for some platforms, but they aren't officially supported.</span></span> <span data-ttu-id="1abf3-128">這些套件在表格中標示為 `Community`。</span><span class="sxs-lookup"><span data-stu-id="1abf3-128">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="1abf3-129">列為 `Experimental` 的平台為非正式支援，但可用於實驗和提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="1abf3-129">Platforms listed as `Experimental` aren't officially supported, but are available for experimentation and feedback.</span></span>

| <span data-ttu-id="1abf3-130">平台</span><span class="sxs-lookup"><span data-stu-id="1abf3-130">Platform</span></span>                                          | <span data-ttu-id="1abf3-131">6.1</span><span class="sxs-lookup"><span data-stu-id="1abf3-131">6.1</span></span>         | <span data-ttu-id="1abf3-132">6.2</span><span class="sxs-lookup"><span data-stu-id="1abf3-132">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="1abf3-133">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="1abf3-133">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="1abf3-134">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-134">Supported</span></span>   | <span data-ttu-id="1abf3-135">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-135">Supported</span></span>   |
| <span data-ttu-id="1abf3-136">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="1abf3-136">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="1abf3-137">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-137">Supported</span></span>   | <span data-ttu-id="1abf3-138">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-138">Supported</span></span>   |
| <span data-ttu-id="1abf3-139">[Windows Server 半年通道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="1abf3-139">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="1abf3-140">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-140">Supported</span></span>   | <span data-ttu-id="1abf3-141">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-141">Supported</span></span>   |
| <span data-ttu-id="1abf3-142">Ubuntu 16.04 與 18.04</span><span class="sxs-lookup"><span data-stu-id="1abf3-142">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="1abf3-143">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-143">Supported</span></span>   | <span data-ttu-id="1abf3-144">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-144">Supported</span></span>   |
| <span data-ttu-id="1abf3-145">Ubuntu 18.10 (透過 Snap 套件)</span><span class="sxs-lookup"><span data-stu-id="1abf3-145">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="1abf3-146">群體</span><span class="sxs-lookup"><span data-stu-id="1abf3-146">Community</span></span>   | <span data-ttu-id="1abf3-147">群體</span><span class="sxs-lookup"><span data-stu-id="1abf3-147">Community</span></span>   |
| <span data-ttu-id="1abf3-148">Ubuntu 19.04 (透過 Snap 套件)</span><span class="sxs-lookup"><span data-stu-id="1abf3-148">Ubuntu 19.04 (via Snap Package)</span></span>                   | <span data-ttu-id="1abf3-149">群體</span><span class="sxs-lookup"><span data-stu-id="1abf3-149">Community</span></span>   | <span data-ttu-id="1abf3-150">群體</span><span class="sxs-lookup"><span data-stu-id="1abf3-150">Community</span></span>   |
| <span data-ttu-id="1abf3-151">Debian 9</span><span class="sxs-lookup"><span data-stu-id="1abf3-151">Debian 9</span></span>                                          | <span data-ttu-id="1abf3-152">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-152">Supported</span></span>   | <span data-ttu-id="1abf3-153">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-153">Supported</span></span>   |
| <span data-ttu-id="1abf3-154">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1abf3-154">CentOS 7</span></span>                                          | <span data-ttu-id="1abf3-155">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-155">Supported</span></span>   | <span data-ttu-id="1abf3-156">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-156">Supported</span></span>   |
| <span data-ttu-id="1abf3-157">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="1abf3-157">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="1abf3-158">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-158">Supported</span></span>   | <span data-ttu-id="1abf3-159">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-159">Supported</span></span>   |
| <span data-ttu-id="1abf3-160">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="1abf3-160">openSUSE 42.3</span></span>                                     | <span data-ttu-id="1abf3-161">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-161">Supported</span></span>   | <span data-ttu-id="1abf3-162">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-162">Supported</span></span>   |
| <span data-ttu-id="1abf3-163">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="1abf3-163">Fedora 28</span></span>                                         | <span data-ttu-id="1abf3-164">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-164">Supported</span></span>   | <span data-ttu-id="1abf3-165">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-165">Supported</span></span>   |
| <span data-ttu-id="1abf3-166">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="1abf3-166">macOS 10.12+</span></span>                                      | <span data-ttu-id="1abf3-167">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-167">Supported</span></span>   | <span data-ttu-id="1abf3-168">支援</span><span class="sxs-lookup"><span data-stu-id="1abf3-168">Supported</span></span>   |
| <span data-ttu-id="1abf3-169">Arch</span><span class="sxs-lookup"><span data-stu-id="1abf3-169">Arch</span></span>                                              | <span data-ttu-id="1abf3-170">群體</span><span class="sxs-lookup"><span data-stu-id="1abf3-170">Community</span></span>   | <span data-ttu-id="1abf3-171">群體</span><span class="sxs-lookup"><span data-stu-id="1abf3-171">Community</span></span>   |
| <span data-ttu-id="1abf3-172">Raspbian</span><span class="sxs-lookup"><span data-stu-id="1abf3-172">Raspbian</span></span>                                          | <span data-ttu-id="1abf3-173">群體</span><span class="sxs-lookup"><span data-stu-id="1abf3-173">Community</span></span>   | <span data-ttu-id="1abf3-174">群體</span><span class="sxs-lookup"><span data-stu-id="1abf3-174">Community</span></span>   |
| <span data-ttu-id="1abf3-175">Kali</span><span class="sxs-lookup"><span data-stu-id="1abf3-175">Kali</span></span>                                              | <span data-ttu-id="1abf3-176">群體</span><span class="sxs-lookup"><span data-stu-id="1abf3-176">Community</span></span>   | <span data-ttu-id="1abf3-177">群體</span><span class="sxs-lookup"><span data-stu-id="1abf3-177">Community</span></span>   |
| <span data-ttu-id="1abf3-178">AppImage (作用於多個 Linux 平台)</span><span class="sxs-lookup"><span data-stu-id="1abf3-178">AppImage (works on multiple Linux platforms)</span></span>      | <span data-ttu-id="1abf3-179">群體</span><span class="sxs-lookup"><span data-stu-id="1abf3-179">Community</span></span>   | <span data-ttu-id="1abf3-180">群體</span><span class="sxs-lookup"><span data-stu-id="1abf3-180">Community</span></span>   |
| [<span data-ttu-id="1abf3-181">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="1abf3-181">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="1abf3-182">請參閱備註</span><span class="sxs-lookup"><span data-stu-id="1abf3-182">See note</span></span>    | <span data-ttu-id="1abf3-183">請參閱備註</span><span class="sxs-lookup"><span data-stu-id="1abf3-183">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="1abf3-184">和您執行套件所在的發行版本一樣，也支援 Snap 套件。</span><span class="sxs-lookup"><span data-stu-id="1abf3-184">Snap packages are supported the same as the distribution you're running the package on.</span></span>

## <a name="powershell-releases-end-of-life"></a><span data-ttu-id="1abf3-185">PowerShell 版本生命週期結束</span><span class="sxs-lookup"><span data-stu-id="1abf3-185">PowerShell releases end-of-life</span></span>

<span data-ttu-id="1abf3-186">下表根據 [PowerShell Core 的生命週期](#lifecycle-of-powershell-core)，列出各種版本的停止支援日期。</span><span class="sxs-lookup"><span data-stu-id="1abf3-186">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various releases will no longer be supported.</span></span>

| <span data-ttu-id="1abf3-187">版本</span><span class="sxs-lookup"><span data-stu-id="1abf3-187">Version</span></span> | <span data-ttu-id="1abf3-188">生命週期結束</span><span class="sxs-lookup"><span data-stu-id="1abf3-188">End-of-life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="1abf3-189">6.0</span><span class="sxs-lookup"><span data-stu-id="1abf3-189">6.0</span></span>     | <span data-ttu-id="1abf3-190">2019 年 2 月 13 日</span><span class="sxs-lookup"><span data-stu-id="1abf3-190">February 13, 2019</span></span>             |
| <span data-ttu-id="1abf3-191">6.1</span><span class="sxs-lookup"><span data-stu-id="1abf3-191">6.1</span></span>     | <span data-ttu-id="1abf3-192">2019 年 9 月 28 日</span><span class="sxs-lookup"><span data-stu-id="1abf3-192">September 28, 2019</span></span>            |
| <span data-ttu-id="1abf3-193">6.2</span><span class="sxs-lookup"><span data-stu-id="1abf3-193">6.2</span></span>     | <span data-ttu-id="1abf3-194">7 發行後的 6 個月</span><span class="sxs-lookup"><span data-stu-id="1abf3-194">6 months after 7 releases</span></span>     |

## <a name="unsupported-platforms"></a><span data-ttu-id="1abf3-195">不支援的平台</span><span class="sxs-lookup"><span data-stu-id="1abf3-195">Unsupported platforms</span></span>

<span data-ttu-id="1abf3-196">當平台版本到達平台擁有者所定義的生命週期結束時間時，PowerShell Core 也會停止支援該平台版本。</span><span class="sxs-lookup"><span data-stu-id="1abf3-196">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span> <span data-ttu-id="1abf3-197">先前推出的套件仍然可供需要存取的客戶取得，但將不再提供任何類型的正式支援和更新。</span><span class="sxs-lookup"><span data-stu-id="1abf3-197">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="1abf3-198">這表示發行版本擁有者已停止支援下列版本，因此不再支援。</span><span class="sxs-lookup"><span data-stu-id="1abf3-198">So, the distribution owners ended support for the following versions and aren't supported.</span></span>

| <span data-ttu-id="1abf3-199">平台</span><span class="sxs-lookup"><span data-stu-id="1abf3-199">Platform</span></span> | <span data-ttu-id="1abf3-200">版本</span><span class="sxs-lookup"><span data-stu-id="1abf3-200">Version</span></span> | <span data-ttu-id="1abf3-201">生命週期結束</span><span class="sxs-lookup"><span data-stu-id="1abf3-201">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="1abf3-202">Fedora</span><span class="sxs-lookup"><span data-stu-id="1abf3-202">Fedora</span></span>   | <span data-ttu-id="1abf3-203">24</span><span class="sxs-lookup"><span data-stu-id="1abf3-203">24</span></span>      | [<span data-ttu-id="1abf3-204">2017 年 8 月</span><span class="sxs-lookup"><span data-stu-id="1abf3-204">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="1abf3-205">Fedora</span><span class="sxs-lookup"><span data-stu-id="1abf3-205">Fedora</span></span>   | <span data-ttu-id="1abf3-206">25</span><span class="sxs-lookup"><span data-stu-id="1abf3-206">25</span></span>      | [<span data-ttu-id="1abf3-207">2017 年 12 月</span><span class="sxs-lookup"><span data-stu-id="1abf3-207">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="1abf3-208">Fedora</span><span class="sxs-lookup"><span data-stu-id="1abf3-208">Fedora</span></span>   | <span data-ttu-id="1abf3-209">26</span><span class="sxs-lookup"><span data-stu-id="1abf3-209">26</span></span>      | [<span data-ttu-id="1abf3-210">2018 年 5 月</span><span class="sxs-lookup"><span data-stu-id="1abf3-210">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="1abf3-211">openSUSE</span><span class="sxs-lookup"><span data-stu-id="1abf3-211">openSUSE</span></span> | <span data-ttu-id="1abf3-212">42.1</span><span class="sxs-lookup"><span data-stu-id="1abf3-212">42.1</span></span>    | [<span data-ttu-id="1abf3-213">2017 年 5 月</span><span class="sxs-lookup"><span data-stu-id="1abf3-213">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="1abf3-214">openSUSE</span><span class="sxs-lookup"><span data-stu-id="1abf3-214">openSUSE</span></span> | <span data-ttu-id="1abf3-215">42.2</span><span class="sxs-lookup"><span data-stu-id="1abf3-215">42.2</span></span>    | [<span data-ttu-id="1abf3-216">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="1abf3-216">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="1abf3-217">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="1abf3-217">Ubuntu</span></span>   | <span data-ttu-id="1abf3-218">16.10</span><span class="sxs-lookup"><span data-stu-id="1abf3-218">16.10</span></span>   | [<span data-ttu-id="1abf3-219">2017 年 7 月</span><span class="sxs-lookup"><span data-stu-id="1abf3-219">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="1abf3-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="1abf3-220">Ubuntu</span></span>   | <span data-ttu-id="1abf3-221">17.04</span><span class="sxs-lookup"><span data-stu-id="1abf3-221">17.04</span></span>   | [<span data-ttu-id="1abf3-222">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="1abf3-222">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="1abf3-223">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="1abf3-223">Ubuntu</span></span>   | <span data-ttu-id="1abf3-224">17.10</span><span class="sxs-lookup"><span data-stu-id="1abf3-224">17.10</span></span>   | [<span data-ttu-id="1abf3-225">2018 年 7 月</span><span class="sxs-lookup"><span data-stu-id="1abf3-225">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="1abf3-226">Debian</span><span class="sxs-lookup"><span data-stu-id="1abf3-226">Debian</span></span>   | <span data-ttu-id="1abf3-227">8</span><span class="sxs-lookup"><span data-stu-id="1abf3-227">8</span></span>       | [<span data-ttu-id="1abf3-228">2018 年 6 月</span><span class="sxs-lookup"><span data-stu-id="1abf3-228">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="1abf3-229">Fedora</span><span class="sxs-lookup"><span data-stu-id="1abf3-229">Fedora</span></span>   | <span data-ttu-id="1abf3-230">27</span><span class="sxs-lookup"><span data-stu-id="1abf3-230">27</span></span>      | [<span data-ttu-id="1abf3-231">2018 年 11 月</span><span class="sxs-lookup"><span data-stu-id="1abf3-231">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="1abf3-232">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="1abf3-232">Ubuntu</span></span>   | <span data-ttu-id="1abf3-233">14.04</span><span class="sxs-lookup"><span data-stu-id="1abf3-233">14.04</span></span>   | [<span data-ttu-id="1abf3-234">2019 年 4 月</span><span class="sxs-lookup"><span data-stu-id="1abf3-234">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="1abf3-235">授權附註</span><span class="sxs-lookup"><span data-stu-id="1abf3-235">Notes on licensing</span></span>

<span data-ttu-id="1abf3-236">PowerShell Core 是透過 [MIT 授權][]所發行。</span><span class="sxs-lookup"><span data-stu-id="1abf3-236">PowerShell Core is released under the [MIT license][].</span></span> <span data-ttu-id="1abf3-237">透過此授權，而且沒有付費支援合約，則使用者就只有[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="1abf3-237">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span> <span data-ttu-id="1abf3-238">運用社群支援，Microsoft 不保證會回應或修正。</span><span class="sxs-lookup"><span data-stu-id="1abf3-238">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="1abf3-239">Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="1abf3-239">Windows PowerShell Module</span></span>

<span data-ttu-id="1abf3-240">除非產品模組明確支援 PowerShell Core，否則 PowerShell Core 支援不包含那些模組。</span><span class="sxs-lookup"><span data-stu-id="1abf3-240">Support for PowerShell Core doesn't include product modules, unless those modules explicitly support PowerShell Core.</span></span> <span data-ttu-id="1abf3-241">例如，使用隨附為 Windows Server 一部分的 `ActiveDirectory` 模組，就是不支援的案例。</span><span class="sxs-lookup"><span data-stu-id="1abf3-241">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="1abf3-242">不過，在某些情況下，未明確支援 PowerShell Core 的模組可能會相容。</span><span class="sxs-lookup"><span data-stu-id="1abf3-242">However, modules that don't explicitly support PowerShell Core may be compatible in some cases.</span></span> <span data-ttu-id="1abf3-243">安裝 [`WindowsPSModulePath`][] 模組，即可將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="1abf3-243">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="1abf3-244">首先，從 PowerShell 資源庫安裝 `WindowsPSModulePath` 模組：</span><span class="sxs-lookup"><span data-stu-id="1abf3-244">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="1abf3-245">安裝此模組之後，請執行 `Add-WindowsPSModulePath` Cmdlet，以將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="1abf3-245">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="1abf3-246">實驗性功能</span><span class="sxs-lookup"><span data-stu-id="1abf3-246">Experimental features</span></span>

<span data-ttu-id="1abf3-247">[實驗性功能][]僅限於[社群支援](#community-support)。</span><span class="sxs-lookup"><span data-stu-id="1abf3-247">[Experimental features][] are limited to [community support](#community-support).</span></span>

[頂級]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
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
