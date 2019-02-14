---
title: PowerShell Core 支援週期
description: 控管 PowerShell Core 支援的原則
ms.date: 08/06/2018
ms.openlocfilehash: cb1daf953b11ffba8f39bcc05a8b122350c497eb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679452"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="df013-103">PowerShell Core 支援週期</span><span class="sxs-lookup"><span data-stu-id="df013-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="df013-104">PowerShell Core 是一組可以與 Windows PowerShell 分開出貨、安裝和設定的不同工具和元件。</span><span class="sxs-lookup"><span data-stu-id="df013-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="df013-105">因此，PowerShell Core 不會包含在 Windows 7/8.1/10 或 Windows Server 授權合約。</span><span class="sxs-lookup"><span data-stu-id="df013-105">So, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="df013-106">不過，傳統 Microsoft 支援合約支援 PowerShell Core，包含 [Premier][]、[Microsoft 企業授權][enterprise-agreement]和[軟體保證權益][assurance]。</span><span class="sxs-lookup"><span data-stu-id="df013-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="df013-107">您也可以提出您問題的支援要求，付費獲得 PowerShell Core 的[輔助支援][]。</span><span class="sxs-lookup"><span data-stu-id="df013-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="df013-108">我們也會在您可提出問題、Bug 或功能要求的 GitHub 上提供[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="df013-108">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="df013-109">此外，您可能會發現從社群的其他成員的說明，在一般[Microsoft Community][]或 Microsoft [PowerShell Tech Community][]。</span><span class="sxs-lookup"><span data-stu-id="df013-109">Also, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="df013-110">我們提供了不保證在該處社群會處理或未及時解決您的問題。</span><span class="sxs-lookup"><span data-stu-id="df013-110">We offer no guarantee there that the community will address or resolve your issue in a timely manner.</span></span>
<span data-ttu-id="df013-111">如果您有需要立即注意的問題，則應該使用傳統付費支援選項。</span><span class="sxs-lookup"><span data-stu-id="df013-111">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="df013-112">PowerShell Core 生命週期</span><span class="sxs-lookup"><span data-stu-id="df013-112">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="df013-113">PowerShell Core 會採用 [Microsoft 現代化生命週期原則 ][modern]。</span><span class="sxs-lookup"><span data-stu-id="df013-113">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="df013-114">此支援生命週期是要保持客戶的最新版本最新資訊。</span><span class="sxs-lookup"><span data-stu-id="df013-114">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="df013-115">PowerShell core 6.x 版分支將會更新一次大約每六個月 (範例：6.0、 6.1、 6.2 等等。)</span><span class="sxs-lookup"><span data-stu-id="df013-115">The version 6.x branch of PowerShell Core will be updated approximately once every six months (examples: 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df013-116">您必須在每個新次要版本發行之後的六個月內進行更新，才能持續接收支援。</span><span class="sxs-lookup"><span data-stu-id="df013-116">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="df013-117">比方說，如果 PowerShell Core 6.1 發行於 2018 年 7 月 1，則必須更新至 PowerShell Core 6.1 2019 年 1 月 1 日到維護的支援。</span><span class="sxs-lookup"><span data-stu-id="df013-117">For example, if PowerShell Core 6.1 is released on July 1, 2018, you would be expected to update to PowerShell Core 6.1 by January 1, 2019 to maintain support.</span></span>

![PowerShell Core 分支生命週期][lifecycle-chart]

<span data-ttu-id="df013-119">新式生命週期原則也需要，Microsoft 為客戶提供 12 個月通知之前停用產品 (也就是 PowerShell Core) 的支援。</span><span class="sxs-lookup"><span data-stu-id="df013-119">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (that is, PowerShell Core).</span></span>

<span data-ttu-id="df013-120">最後，我們預期 PowerShell Core 會採用 「 長期服務 」 的方法。</span><span class="sxs-lookup"><span data-stu-id="df013-120">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach.</span></span>
<span data-ttu-id="df013-121">在此服務的方法中，我們需要只服務和安全性更新保持特定 6.x 的分支/版本的支援。</span><span class="sxs-lookup"><span data-stu-id="df013-121">In this servicing approach, we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="df013-122">支援的平台</span><span class="sxs-lookup"><span data-stu-id="df013-122">Supported platforms</span></span>

<span data-ttu-id="df013-123">下表來查看哪些平台版本的 PowerShell Core 會使用已正式支援。</span><span class="sxs-lookup"><span data-stu-id="df013-123">The following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="df013-124">我們的社群也針對部分平台貢獻了套件，但這些套件未受正式支援。</span><span class="sxs-lookup"><span data-stu-id="df013-124">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="df013-125">這些套件在表格中標示為 `Community`。</span><span class="sxs-lookup"><span data-stu-id="df013-125">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="df013-126">列為 `Experimental` 的平台為非正式支援，但可用於實驗和提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="df013-126">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="df013-127">6.0</span><span class="sxs-lookup"><span data-stu-id="df013-127">6.0</span></span>         | <span data-ttu-id="df013-128">6.1</span><span class="sxs-lookup"><span data-stu-id="df013-128">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="df013-129">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="df013-129">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="df013-130">支援</span><span class="sxs-lookup"><span data-stu-id="df013-130">Supported</span></span>   | <span data-ttu-id="df013-131">支援</span><span class="sxs-lookup"><span data-stu-id="df013-131">Supported</span></span>   |
| <span data-ttu-id="df013-132">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="df013-132">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="df013-133">支援</span><span class="sxs-lookup"><span data-stu-id="df013-133">Supported</span></span>   | <span data-ttu-id="df013-134">支援</span><span class="sxs-lookup"><span data-stu-id="df013-134">Supported</span></span>   |
| <span data-ttu-id="df013-135">[Windows Server 半年通道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="df013-135">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="df013-136">支援</span><span class="sxs-lookup"><span data-stu-id="df013-136">Supported</span></span>   | <span data-ttu-id="df013-137">支援</span><span class="sxs-lookup"><span data-stu-id="df013-137">Supported</span></span>   |
| <span data-ttu-id="df013-138">Ubuntu 14.04 和 16.04</span><span class="sxs-lookup"><span data-stu-id="df013-138">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="df013-139">支援</span><span class="sxs-lookup"><span data-stu-id="df013-139">Supported</span></span>   | <span data-ttu-id="df013-140">支援</span><span class="sxs-lookup"><span data-stu-id="df013-140">Supported</span></span>   |
| <span data-ttu-id="df013-141">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="df013-141">Ubuntu 18.04</span></span>                                      |             | <span data-ttu-id="df013-142">支援</span><span class="sxs-lookup"><span data-stu-id="df013-142">Supported</span></span>   |
| <span data-ttu-id="df013-143">Ubuntu 18.10 (透過 Snap 套件)</span><span class="sxs-lookup"><span data-stu-id="df013-143">Ubuntu 18.10 (via Snap Package)</span></span>                   |             | <span data-ttu-id="df013-144">群體</span><span class="sxs-lookup"><span data-stu-id="df013-144">Community</span></span>   |
| <span data-ttu-id="df013-145">Debian 9</span><span class="sxs-lookup"><span data-stu-id="df013-145">Debian 9</span></span>                                          | <span data-ttu-id="df013-146">支援</span><span class="sxs-lookup"><span data-stu-id="df013-146">Supported</span></span>   | <span data-ttu-id="df013-147">支援</span><span class="sxs-lookup"><span data-stu-id="df013-147">Supported</span></span>   |
| <span data-ttu-id="df013-148">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="df013-148">CentOS 7</span></span>                                          | <span data-ttu-id="df013-149">支援</span><span class="sxs-lookup"><span data-stu-id="df013-149">Supported</span></span>   | <span data-ttu-id="df013-150">支援</span><span class="sxs-lookup"><span data-stu-id="df013-150">Supported</span></span>   |
| <span data-ttu-id="df013-151">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="df013-151">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="df013-152">支援</span><span class="sxs-lookup"><span data-stu-id="df013-152">Supported</span></span>   | <span data-ttu-id="df013-153">支援</span><span class="sxs-lookup"><span data-stu-id="df013-153">Supported</span></span>   |
| <span data-ttu-id="df013-154">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="df013-154">openSUSE 42.3</span></span>                                     | <span data-ttu-id="df013-155">支援</span><span class="sxs-lookup"><span data-stu-id="df013-155">Supported</span></span>   | <span data-ttu-id="df013-156">支援</span><span class="sxs-lookup"><span data-stu-id="df013-156">Supported</span></span>   |
| <span data-ttu-id="df013-157">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="df013-157">Fedora 28</span></span>                                         |             | <span data-ttu-id="df013-158">支援</span><span class="sxs-lookup"><span data-stu-id="df013-158">Supported</span></span>   |
| <span data-ttu-id="df013-159">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="df013-159">macOS 10.12+</span></span>                                      | <span data-ttu-id="df013-160">支援</span><span class="sxs-lookup"><span data-stu-id="df013-160">Supported</span></span>   | <span data-ttu-id="df013-161">支援</span><span class="sxs-lookup"><span data-stu-id="df013-161">Supported</span></span>   |
| <span data-ttu-id="df013-162">Arch</span><span class="sxs-lookup"><span data-stu-id="df013-162">Arch</span></span>                                              | <span data-ttu-id="df013-163">群體</span><span class="sxs-lookup"><span data-stu-id="df013-163">Community</span></span>   | <span data-ttu-id="df013-164">群體</span><span class="sxs-lookup"><span data-stu-id="df013-164">Community</span></span>   |
| <span data-ttu-id="df013-165">Raspbian</span><span class="sxs-lookup"><span data-stu-id="df013-165">Raspbian</span></span>                                          | <span data-ttu-id="df013-166">Experimental</span><span class="sxs-lookup"><span data-stu-id="df013-166">Experimental</span></span>| <span data-ttu-id="df013-167">群體</span><span class="sxs-lookup"><span data-stu-id="df013-167">Community</span></span>   |
| <span data-ttu-id="df013-168">Kali</span><span class="sxs-lookup"><span data-stu-id="df013-168">Kali</span></span>                                              | <span data-ttu-id="df013-169">群體</span><span class="sxs-lookup"><span data-stu-id="df013-169">Community</span></span>   | <span data-ttu-id="df013-170">群體</span><span class="sxs-lookup"><span data-stu-id="df013-170">Community</span></span>   |
| <span data-ttu-id="df013-171">AppImage (作用於多個 Linux 平台)</span><span class="sxs-lookup"><span data-stu-id="df013-171">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="df013-172">群體</span><span class="sxs-lookup"><span data-stu-id="df013-172">Community</span></span>   | <span data-ttu-id="df013-173">群體</span><span class="sxs-lookup"><span data-stu-id="df013-173">Community</span></span>   |
| [<span data-ttu-id="df013-174">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="df013-174">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="df013-175">請參閱備註</span><span class="sxs-lookup"><span data-stu-id="df013-175">See note</span></span>    | <span data-ttu-id="df013-176">請參閱備註</span><span class="sxs-lookup"><span data-stu-id="df013-176">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="df013-177">Snap 套件會有一段時間處於實驗階段。</span><span class="sxs-lookup"><span data-stu-id="df013-177">Snap packages will be experimental for a period.</span></span>
> <span data-ttu-id="df013-178">之後，我們相信 Snap 就不會帶來新的支援問題，而支援會跟隨於您執行套件的發佈。</span><span class="sxs-lookup"><span data-stu-id="df013-178">After, we are confident that Snap does not introduce new support issues, the support will follow the distribution you are running the package on.</span></span>

## <a name="powershell-release-end-of-life"></a><span data-ttu-id="df013-179">PowerShell 版本生命週期結束的</span><span class="sxs-lookup"><span data-stu-id="df013-179">PowerShell release end of life</span></span>

<span data-ttu-id="df013-180">根據[生命週期的 PowerShell Core](#lifecycle-of-powershell-core)下, 表列出當不同的版本將不再支援的日期。</span><span class="sxs-lookup"><span data-stu-id="df013-180">Based on [Lifecycle of PowerShell Core](#lifecycle-of-powershell-core), the following table lists the dates when various release will no longer be supported.</span></span>

| <span data-ttu-id="df013-181">版本</span><span class="sxs-lookup"><span data-stu-id="df013-181">Version</span></span> | <span data-ttu-id="df013-182">生命週期結束</span><span class="sxs-lookup"><span data-stu-id="df013-182">End Of Life</span></span>                   |
|---------|-------------------------------|
| <span data-ttu-id="df013-183">6.0</span><span class="sxs-lookup"><span data-stu-id="df013-183">6.0</span></span>     | <span data-ttu-id="df013-184">2019 年 2 月 13日日</span><span class="sxs-lookup"><span data-stu-id="df013-184">February 13, 2019</span></span>             |
| <span data-ttu-id="df013-185">6.1</span><span class="sxs-lookup"><span data-stu-id="df013-185">6.1</span></span>     | <span data-ttu-id="df013-186">6.2 發行後的 6 個月</span><span class="sxs-lookup"><span data-stu-id="df013-186">6 Months after 6.2 releases</span></span>   |

## <a name="platforms-which-are-out-of-support"></a><span data-ttu-id="df013-187">平台，也就是不受支援</span><span class="sxs-lookup"><span data-stu-id="df013-187">Platforms, which are out of support</span></span>

<span data-ttu-id="df013-188">當平台版本達到生命週期結束時，所定義的平台擁有者時，PowerShell Core 也將停止支援該平台版本。</span><span class="sxs-lookup"><span data-stu-id="df013-188">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to support that platform version.</span></span>
<span data-ttu-id="df013-189">先前推出的套件仍然可供需要存取的客戶取得，但將不再提供任何類型的正式支援和更新。</span><span class="sxs-lookup"><span data-stu-id="df013-189">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="df013-190">因此，通訊群組擁有者已結束支援下列版本，而不支援。</span><span class="sxs-lookup"><span data-stu-id="df013-190">So, the distribution owners ended support for the following versions and are not supported.</span></span>

| <span data-ttu-id="df013-191">作業系統</span><span class="sxs-lookup"><span data-stu-id="df013-191">OS</span></span>       | <span data-ttu-id="df013-192">版本</span><span class="sxs-lookup"><span data-stu-id="df013-192">Version</span></span> | <span data-ttu-id="df013-193">生命週期結束</span><span class="sxs-lookup"><span data-stu-id="df013-193">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="df013-194">Fedora</span><span class="sxs-lookup"><span data-stu-id="df013-194">Fedora</span></span>   | <span data-ttu-id="df013-195">24</span><span class="sxs-lookup"><span data-stu-id="df013-195">24</span></span>      | [<span data-ttu-id="df013-196">2017 年 8 月</span><span class="sxs-lookup"><span data-stu-id="df013-196">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="df013-197">Fedora</span><span class="sxs-lookup"><span data-stu-id="df013-197">Fedora</span></span>   | <span data-ttu-id="df013-198">25</span><span class="sxs-lookup"><span data-stu-id="df013-198">25</span></span>      | [<span data-ttu-id="df013-199">2017 年 12 月</span><span class="sxs-lookup"><span data-stu-id="df013-199">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="df013-200">Fedora</span><span class="sxs-lookup"><span data-stu-id="df013-200">Fedora</span></span>   | <span data-ttu-id="df013-201">26</span><span class="sxs-lookup"><span data-stu-id="df013-201">26</span></span>      | [<span data-ttu-id="df013-202">2018 年 5 月</span><span class="sxs-lookup"><span data-stu-id="df013-202">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="df013-203">openSUSE</span><span class="sxs-lookup"><span data-stu-id="df013-203">openSUSE</span></span> | <span data-ttu-id="df013-204">42.1</span><span class="sxs-lookup"><span data-stu-id="df013-204">42.1</span></span>    | [<span data-ttu-id="df013-205">2017 年 5 月</span><span class="sxs-lookup"><span data-stu-id="df013-205">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="df013-206">openSUSE</span><span class="sxs-lookup"><span data-stu-id="df013-206">openSUSE</span></span> | <span data-ttu-id="df013-207">42.2</span><span class="sxs-lookup"><span data-stu-id="df013-207">42.2</span></span>    | [<span data-ttu-id="df013-208">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="df013-208">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="df013-209">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="df013-209">Ubuntu</span></span>   | <span data-ttu-id="df013-210">16.10</span><span class="sxs-lookup"><span data-stu-id="df013-210">16.10</span></span>   | [<span data-ttu-id="df013-211">2017 年 7 月</span><span class="sxs-lookup"><span data-stu-id="df013-211">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="df013-212">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="df013-212">Ubuntu</span></span>   | <span data-ttu-id="df013-213">17.04</span><span class="sxs-lookup"><span data-stu-id="df013-213">17.04</span></span>   | [<span data-ttu-id="df013-214">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="df013-214">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="df013-215">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="df013-215">Ubuntu</span></span>   | <span data-ttu-id="df013-216">17.10</span><span class="sxs-lookup"><span data-stu-id="df013-216">17.10</span></span>   | [<span data-ttu-id="df013-217">2018 年 7 月</span><span class="sxs-lookup"><span data-stu-id="df013-217">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| <span data-ttu-id="df013-218">Debian</span><span class="sxs-lookup"><span data-stu-id="df013-218">Debian</span></span>   | <span data-ttu-id="df013-219">8</span><span class="sxs-lookup"><span data-stu-id="df013-219">8</span></span>       | [<span data-ttu-id="df013-220">2018 年 6 月</span><span class="sxs-lookup"><span data-stu-id="df013-220">June 2018</span></span>](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| <span data-ttu-id="df013-221">Fedora</span><span class="sxs-lookup"><span data-stu-id="df013-221">Fedora</span></span>   | <span data-ttu-id="df013-222">27</span><span class="sxs-lookup"><span data-stu-id="df013-222">27</span></span>      | [<span data-ttu-id="df013-223">2018 年 11 月</span><span class="sxs-lookup"><span data-stu-id="df013-223">November 2018</span></span>](https://fedoramagazine.org/fedora-27-end-of-life/)                          |

## <a name="notes-on-licensing"></a><span data-ttu-id="df013-224">授權附註</span><span class="sxs-lookup"><span data-stu-id="df013-224">Notes on licensing</span></span>

<span data-ttu-id="df013-225">PowerShell Core 是透過 [MIT 授權][]所發行。</span><span class="sxs-lookup"><span data-stu-id="df013-225">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="df013-226">依據本授權，且不含付費的支援合約中，使用者僅限於[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="df013-226">Under this license, and without a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="df013-227">運用社群支援，Microsoft 不保證會回應或修正。</span><span class="sxs-lookup"><span data-stu-id="df013-227">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="df013-228">Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="df013-228">Windows PowerShell Module</span></span>

<span data-ttu-id="df013-229">支援的 PowerShell Core 不包含產品模組，除非這些模組明確支援 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="df013-229">Support for PowerShell Core does not include product modules, unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="df013-230">例如，使用隨附為 Windows Server 一部分的 `ActiveDirectory` 模組，就是不支援的案例。</span><span class="sxs-lookup"><span data-stu-id="df013-230">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="df013-231">不過，在某些情況下，未明確支援 PowerShell Core 的模組可能會相容。</span><span class="sxs-lookup"><span data-stu-id="df013-231">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="df013-232">藉由安裝[ `WindowsPSModulePath` ][]模組，您可以新增 Windows PowerShell`PSModulePath`至 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="df013-232">By installing the [`WindowsPSModulePath`][] module, you can add the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="df013-233">首先，從 PowerShell 資源庫安裝 `WindowsPSModulePath` 模組：</span><span class="sxs-lookup"><span data-stu-id="df013-233">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="df013-234">安裝此模組之後，請執行 `Add-WindowsPSModulePath` Cmdlet，以將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="df013-234">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

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
