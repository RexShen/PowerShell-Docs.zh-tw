---
title: PowerShell Core 支援週期
description: 控管 PowerShell Core 支援的原則
ms.date: 08/06/2018
ms.openlocfilehash: 178e5c43520f9a392ca219b9f785eb18b1ec5436
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086949"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="c8d69-103">PowerShell Core 支援週期</span><span class="sxs-lookup"><span data-stu-id="c8d69-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="c8d69-104">PowerShell Core 是一組可以與 Windows PowerShell 分開出貨、安裝和設定的不同工具和元件。</span><span class="sxs-lookup"><span data-stu-id="c8d69-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="c8d69-105">因此，Windows 7/8.1/10 或 Windows Server 授權合約不包含 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="c8d69-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="c8d69-106">不過，傳統 Microsoft 支援合約支援 PowerShell Core，包含 [Premier][]、[Microsoft 企業授權][enterprise-agreement]和[軟體保證權益][assurance]。</span><span class="sxs-lookup"><span data-stu-id="c8d69-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="c8d69-107">您也可以提出您問題的支援要求，付費獲得 PowerShell Core 的[輔助支援][]。</span><span class="sxs-lookup"><span data-stu-id="c8d69-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

## <a name="community-support"></a><span data-ttu-id="c8d69-108">社群支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-108">Community Support</span></span>

<span data-ttu-id="c8d69-109">我們也會在您可提出問題、Bug 或功能要求的 GitHub 上提供[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="c8d69-109">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="c8d69-110">或者，您可以在一般 [Microsoft Community][] 或 Microsoft [PowerShell Tech Community][] 上尋求其他社群成員的協助。</span><span class="sxs-lookup"><span data-stu-id="c8d69-110">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="c8d69-111">我們不保證社群能夠及時處理或解決您的問題。</span><span class="sxs-lookup"><span data-stu-id="c8d69-111">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="c8d69-112">如果您有需要立即注意的問題，則應該使用傳統付費支援選項。</span><span class="sxs-lookup"><span data-stu-id="c8d69-112">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="c8d69-113">PowerShell Core 生命週期</span><span class="sxs-lookup"><span data-stu-id="c8d69-113">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="c8d69-114">PowerShell Core 會採用 [Microsoft 現代化生命週期原則 ][modern]。</span><span class="sxs-lookup"><span data-stu-id="c8d69-114">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="c8d69-115">此支援生命週期是要保持客戶的最新版本最新資訊。</span><span class="sxs-lookup"><span data-stu-id="c8d69-115">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="c8d69-116">大約每六個月更新 PowerShell Core 6.x 版分支一次 (例如 6.0、6.1、6.2 等等)</span><span class="sxs-lookup"><span data-stu-id="c8d69-116">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8d69-117">您必須在每個新次要版本發行之後的六個月內進行更新，才能持續接收支援。</span><span class="sxs-lookup"><span data-stu-id="c8d69-117">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="c8d69-118">例如，如果 PowerShell Core 6.1 是在 2018 年 7 月1 日發行，就必須在 2019 年 1 月 1 日之前更新至 PowerShell Core 6.1 以繼續獲得支援。</span><span class="sxs-lookup"><span data-stu-id="c8d69-118">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8d69-119">您必須在每個新修補程式版本發行之後的 30 天內進行更新，才能繼續接收支援。</span><span class="sxs-lookup"><span data-stu-id="c8d69-119">You must update within 30 days after each new patch version release to continue receiving support.</span></span>

<span data-ttu-id="c8d69-120">例如，如果您是執行 PowerShell Core 6.1，而且 6.1.3 在 2019 年 2 月19 日發行，就必須在 2019 年 3 月 21 日 (也就是發行之後的第 30 天) 之前更新至 PowerShell Core 6.1.3 以繼續獲得支援。</span><span class="sxs-lookup"><span data-stu-id="c8d69-120">For example, If you are running PowerShell Core 6.1 and 6.1.3 was released on February 19, 2019, you would be expected to update to PowerShell Core 6.1.3 by March 21, 2019, which is 30 days after the release to maintain support.</span></span>
<span data-ttu-id="c8d69-121">如果需要修補程式，我們會在下一次累計更新中發行。</span><span class="sxs-lookup"><span data-stu-id="c8d69-121">If any fixes are found to be required, the fixes will be released in our next cumulative update.</span></span>

![PowerShell Core 分支生命週期][lifecycle-chart]

<span data-ttu-id="c8d69-123">現代化生命週期原則也需要 Microsoft 在中斷產品 (即 PowerShell Core) 支援之前的 12 個月通知客戶。</span><span class="sxs-lookup"><span data-stu-id="c8d69-123">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="c8d69-124">最後，我們預期 PowerShell Core 會採用 「長期維護」方法。</span><span class="sxs-lookup"><span data-stu-id="c8d69-124">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="c8d69-125">透過這個方法，我們僅需要提供服務和安全性更新，就能保持對特定 6.x 分支/版本的支援。</span><span class="sxs-lookup"><span data-stu-id="c8d69-125">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="c8d69-126">支援的平台</span><span class="sxs-lookup"><span data-stu-id="c8d69-126">Supported platforms</span></span>

<span data-ttu-id="c8d69-127">請參閱下表，了解您使用的 PowerShell Core 版本所正式支援的平台。</span><span class="sxs-lookup"><span data-stu-id="c8d69-127">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="c8d69-128">我們的社群也針對部分平台貢獻了套件，但這些套件未受正式支援。</span><span class="sxs-lookup"><span data-stu-id="c8d69-128">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="c8d69-129">這些套件在表格中標示為 `Community`。</span><span class="sxs-lookup"><span data-stu-id="c8d69-129">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="c8d69-130">列為 `Experimental` 的平台為非正式支援，但可用於實驗和提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="c8d69-130">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="c8d69-131">6.1</span><span class="sxs-lookup"><span data-stu-id="c8d69-131">6.1</span></span>         | <span data-ttu-id="c8d69-132">6.2</span><span class="sxs-lookup"><span data-stu-id="c8d69-132">6.2</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="c8d69-133">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="c8d69-133">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="c8d69-134">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-134">Supported</span></span>   | <span data-ttu-id="c8d69-135">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-135">Supported</span></span>   |
| <span data-ttu-id="c8d69-136">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="c8d69-136">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="c8d69-137">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-137">Supported</span></span>   | <span data-ttu-id="c8d69-138">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-138">Supported</span></span>   |
| <span data-ttu-id="c8d69-139">[Windows Server 半年通道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="c8d69-139">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="c8d69-140">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-140">Supported</span></span>   | <span data-ttu-id="c8d69-141">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-141">Supported</span></span>   |
| <span data-ttu-id="c8d69-142">Ubuntu 16.04 與 18.04</span><span class="sxs-lookup"><span data-stu-id="c8d69-142">Ubuntu 16.04 and 18.04</span></span>                            | <span data-ttu-id="c8d69-143">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-143">Supported</span></span>   | <span data-ttu-id="c8d69-144">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-144">Supported</span></span>   |
| <span data-ttu-id="c8d69-145">Ubuntu 18.10 (透過 Snap 套件)</span><span class="sxs-lookup"><span data-stu-id="c8d69-145">Ubuntu 18.10 (via Snap Package)</span></span>                   | <span data-ttu-id="c8d69-146">群體</span><span class="sxs-lookup"><span data-stu-id="c8d69-146">Community</span></span>   | <span data-ttu-id="c8d69-147">群體</span><span class="sxs-lookup"><span data-stu-id="c8d69-147">Community</span></span>   |
| <span data-ttu-id="c8d69-148">Debian 9</span><span class="sxs-lookup"><span data-stu-id="c8d69-148">Debian 9</span></span>                                          | <span data-ttu-id="c8d69-149">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-149">Supported</span></span>   | <span data-ttu-id="c8d69-150">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-150">Supported</span></span>   |
| <span data-ttu-id="c8d69-151">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c8d69-151">CentOS 7</span></span>                                          | <span data-ttu-id="c8d69-152">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-152">Supported</span></span>   | <span data-ttu-id="c8d69-153">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-153">Supported</span></span>   |
| <span data-ttu-id="c8d69-154">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="c8d69-154">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="c8d69-155">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-155">Supported</span></span>   | <span data-ttu-id="c8d69-156">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-156">Supported</span></span>   |
| <span data-ttu-id="c8d69-157">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="c8d69-157">openSUSE 42.3</span></span>                                     | <span data-ttu-id="c8d69-158">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-158">Supported</span></span>   | <span data-ttu-id="c8d69-159">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-159">Supported</span></span>   |
| <span data-ttu-id="c8d69-160">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c8d69-160">Fedora 28</span></span>                                         | <span data-ttu-id="c8d69-161">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-161">Supported</span></span>   | <span data-ttu-id="c8d69-162">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-162">Supported</span></span>   |
| <span data-ttu-id="c8d69-163">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="c8d69-163">macOS 10.12+</span></span>                                      | <span data-ttu-id="c8d69-164">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-164">Supported</span></span>   | <span data-ttu-id="c8d69-165">支援</span><span class="sxs-lookup"><span data-stu-id="c8d69-165">Supported</span></span>   |
| <span data-ttu-id="c8d69-166">Arch</span><span class="sxs-lookup"><span data-stu-id="c8d69-166">Arch</span></span>                                              | <span data-ttu-id="c8d69-167">群體</span><span class="sxs-lookup"><span data-stu-id="c8d69-167">Community</span></span>   | <span data-ttu-id="c8d69-168">群體</span><span class="sxs-lookup"><span data-stu-id="c8d69-168">Community</span></span>   |
| <span data-ttu-id="c8d69-169">Raspbian</span><span class="sxs-lookup"><span data-stu-id="c8d69-169">Raspbian</span></span>                                          | <span data-ttu-id="c8d69-170">群體</span><span class="sxs-lookup"><span data-stu-id="c8d69-170">Community</span></span>   | <span data-ttu-id="c8d69-171">群體</span><span class="sxs-lookup"><span data-stu-id="c8d69-171">Community</span></span>   |
| <span data-ttu-id="c8d69-172">Kali</span><span class="sxs-lookup"><span data-stu-id="c8d69-172">Kali</span></span>                                              | <span data-ttu-id="c8d69-173">群體</span><span class="sxs-lookup"><span data-stu-id="c8d69-173">Community</span></span>   | <span data-ttu-id="c8d69-174">群體</span><span class="sxs-lookup"><span data-stu-id="c8d69-174">Community</span></span>   |
| <span data-ttu-id="c8d69-175">AppImage (作用於多個 Linux 平台)</span><span class="sxs-lookup"><span data-stu-id="c8d69-175">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="c8d69-176">群體</span><span class="sxs-lookup"><span data-stu-id="c8d69-176">Community</span></span>   | <span data-ttu-id="c8d69-177">群體</span><span class="sxs-lookup"><span data-stu-id="c8d69-177">Community</span></span>   |
| [<span data-ttu-id="c8d69-178">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="c8d69-178">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="c8d69-179">請參閱備註</span><span class="sxs-lookup"><span data-stu-id="c8d69-179">See note</span></span>    | <span data-ttu-id="c8d69-180">請參閱備註</span><span class="sxs-lookup"><span data-stu-id="c8d69-180">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="c8d69-181">和您執行套件所在的散發一樣，也支援 Snap 套件。</span><span class="sxs-lookup"><span data-stu-id="c8d69-181">Snap packages are supported the same as the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="c8d69-182">PowerShell 版本生命週期結束</span><span class="sxs-lookup"><span data-stu-id="c8d69-182">PowerShell release end of life</span></span>

<span data-ttu-id="c8d69-183">下表根據 [PowerShell Core 的生命週期](#lifecycle-of-powershell-core)，列出各種版本的停止支援日期。</span><span class="sxs-lookup"><span data-stu-id="c8d69-183">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="c8d69-184">版本</span><span class="sxs-lookup"><span data-stu-id="c8d69-184">Version</span></span> | <span data-ttu-id="c8d69-185">生命週期結束</span><span class="sxs-lookup"><span data-stu-id="c8d69-185">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="c8d69-186">6.0</span><span class="sxs-lookup"><span data-stu-id="c8d69-186">6.0</span></span>     | <span data-ttu-id="c8d69-187">2019 年 2 月 13 日</span><span class="sxs-lookup"><span data-stu-id="c8d69-187">February 13, 2019</span></span>             |
| <span data-ttu-id="c8d69-188">6.1</span><span class="sxs-lookup"><span data-stu-id="c8d69-188">6.1</span></span>     | <span data-ttu-id="c8d69-189">2019 年 9 月 28 日</span><span class="sxs-lookup"><span data-stu-id="c8d69-189">September 28, 2019</span></span>            |
| <span data-ttu-id="c8d69-190">6.2</span><span class="sxs-lookup"><span data-stu-id="c8d69-190">6.2</span></span>     | <span data-ttu-id="c8d69-191">6.3 發行後的 6 個月</span><span class="sxs-lookup"><span data-stu-id="c8d69-191">6 months after 6.3 releases</span></span>   |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="c8d69-192">終止支援的平台</span><span class="sxs-lookup"><span data-stu-id="c8d69-192">Platforms, which are out of support</span></span>

<span data-ttu-id="c8d69-193">當平台版本到達平台擁有者所定義的生命週期結束時間時，PowerShell Core 也會停止支援該平台版本。</span><span class="sxs-lookup"><span data-stu-id="c8d69-193">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="c8d69-194">先前推出的套件仍然可供需要存取的客戶取得，但將不再提供任何類型的正式支援和更新。</span><span class="sxs-lookup"><span data-stu-id="c8d69-194">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="c8d69-195">這表示發行版本擁有者已停止支援以下版本，因此不再支援。</span><span class="sxs-lookup"><span data-stu-id="c8d69-195">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="c8d69-196">作業系統</span><span class="sxs-lookup"><span data-stu-id="c8d69-196">OS</span></span>       | <span data-ttu-id="c8d69-197">版本</span><span class="sxs-lookup"><span data-stu-id="c8d69-197">Version</span></span> | <span data-ttu-id="c8d69-198">生命週期結束</span><span class="sxs-lookup"><span data-stu-id="c8d69-198">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="c8d69-199">Fedora</span><span class="sxs-lookup"><span data-stu-id="c8d69-199">Fedora</span></span>   | <span data-ttu-id="c8d69-200">24</span><span class="sxs-lookup"><span data-stu-id="c8d69-200">24</span></span>      | [<span data-ttu-id="c8d69-201">2017 年 8 月</span><span class="sxs-lookup"><span data-stu-id="c8d69-201">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="c8d69-202">Fedora</span><span class="sxs-lookup"><span data-stu-id="c8d69-202">Fedora</span></span>   | <span data-ttu-id="c8d69-203">25</span><span class="sxs-lookup"><span data-stu-id="c8d69-203">25</span></span>      | [<span data-ttu-id="c8d69-204">2017 年 12 月</span><span class="sxs-lookup"><span data-stu-id="c8d69-204">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="c8d69-205">Fedora</span><span class="sxs-lookup"><span data-stu-id="c8d69-205">Fedora</span></span>   | <span data-ttu-id="c8d69-206">26</span><span class="sxs-lookup"><span data-stu-id="c8d69-206">26</span></span>      | [<span data-ttu-id="c8d69-207">2018 年 5 月</span><span class="sxs-lookup"><span data-stu-id="c8d69-207">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="c8d69-208">openSUSE</span><span class="sxs-lookup"><span data-stu-id="c8d69-208">openSUSE</span></span> | <span data-ttu-id="c8d69-209">42.1</span><span class="sxs-lookup"><span data-stu-id="c8d69-209">42.1</span></span>    | [<span data-ttu-id="c8d69-210">2017 年 5 月</span><span class="sxs-lookup"><span data-stu-id="c8d69-210">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="c8d69-211">openSUSE</span><span class="sxs-lookup"><span data-stu-id="c8d69-211">openSUSE</span></span> | <span data-ttu-id="c8d69-212">42.2</span><span class="sxs-lookup"><span data-stu-id="c8d69-212">42.2</span></span>    | [<span data-ttu-id="c8d69-213">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="c8d69-213">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="c8d69-214">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c8d69-214">Ubuntu</span></span>   | <span data-ttu-id="c8d69-215">16.10</span><span class="sxs-lookup"><span data-stu-id="c8d69-215">16.10</span></span>   | [<span data-ttu-id="c8d69-216">2017 年 7 月</span><span class="sxs-lookup"><span data-stu-id="c8d69-216">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="c8d69-217">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c8d69-217">Ubuntu</span></span>   | <span data-ttu-id="c8d69-218">17.04</span><span class="sxs-lookup"><span data-stu-id="c8d69-218">17.04</span></span>   | [<span data-ttu-id="c8d69-219">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="c8d69-219">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="c8d69-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c8d69-220">Ubuntu</span></span>   | <span data-ttu-id="c8d69-221">17.10</span><span class="sxs-lookup"><span data-stu-id="c8d69-221">17.10</span></span>   | [<span data-ttu-id="c8d69-222">2018 年 7 月</span><span class="sxs-lookup"><span data-stu-id="c8d69-222">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="c8d69-223">Debian</span><span class="sxs-lookup"><span data-stu-id="c8d69-223">Debian</span></span>   | <span data-ttu-id="c8d69-224">8</span><span class="sxs-lookup"><span data-stu-id="c8d69-224">8</span></span>       | [<span data-ttu-id="c8d69-225">2018 年 6 月</span><span class="sxs-lookup"><span data-stu-id="c8d69-225">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="c8d69-226">Fedora</span><span class="sxs-lookup"><span data-stu-id="c8d69-226">Fedora</span></span>   | <span data-ttu-id="c8d69-227">27</span><span class="sxs-lookup"><span data-stu-id="c8d69-227">27</span></span>      | [<span data-ttu-id="c8d69-228">2018 年 11 月</span><span class="sxs-lookup"><span data-stu-id="c8d69-228">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| <span data-ttu-id="c8d69-229">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c8d69-229">Ubuntu</span></span>   | <span data-ttu-id="c8d69-230">14.04</span><span class="sxs-lookup"><span data-stu-id="c8d69-230">14.04</span></span>   | [<span data-ttu-id="c8d69-231">2019 年 4 月</span><span class="sxs-lookup"><span data-stu-id="c8d69-231">April 2019</span></span>](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a><span data-ttu-id="c8d69-232">授權附註</span><span class="sxs-lookup"><span data-stu-id="c8d69-232">Notes on licensing</span></span>

<span data-ttu-id="c8d69-233">PowerShell Core 是透過 [MIT 授權][]所發行。</span><span class="sxs-lookup"><span data-stu-id="c8d69-233">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="c8d69-234">透過此授權，而且沒有付費支援合約，則使用者就只有[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="c8d69-234">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="c8d69-235">運用社群支援，Microsoft 不保證會回應或修正。</span><span class="sxs-lookup"><span data-stu-id="c8d69-235">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="c8d69-236">Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="c8d69-236">Windows PowerShell Module</span></span>

<span data-ttu-id="c8d69-237">除非產品模組明確支援 PowerShell Core，否則 PowerShell Core 支援不會包括那些模組。</span><span class="sxs-lookup"><span data-stu-id="c8d69-237">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="c8d69-238">例如，使用隨附為 Windows Server 一部分的 `ActiveDirectory` 模組，就是不支援的案例。</span><span class="sxs-lookup"><span data-stu-id="c8d69-238">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="c8d69-239">不過，在某些情況下，未明確支援 PowerShell Core 的模組可能會相容。</span><span class="sxs-lookup"><span data-stu-id="c8d69-239">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="c8d69-240">安裝 [`WindowsPSModulePath`][] 模組，即可將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="c8d69-240">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="c8d69-241">首先，從 PowerShell 資源庫安裝 `WindowsPSModulePath` 模組：</span><span class="sxs-lookup"><span data-stu-id="c8d69-241">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="c8d69-242">安裝此模組之後，請執行 `Add-WindowsPSModulePath` Cmdlet，以將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="c8d69-242">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a><span data-ttu-id="c8d69-243">實驗性功能</span><span class="sxs-lookup"><span data-stu-id="c8d69-243">Experimental features</span></span>

<span data-ttu-id="c8d69-244">[實驗性功能][]僅限於[社群支援](#community-support)。</span><span class="sxs-lookup"><span data-stu-id="c8d69-244">[Experimental features][] are limited to [community support](#community-support).</span></span>

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
