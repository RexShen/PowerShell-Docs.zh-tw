---
title: PowerShell Core 支援週期
description: 控管 PowerShell Core 支援的原則
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402074"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="9a562-103">PowerShell Core 支援週期</span><span class="sxs-lookup"><span data-stu-id="9a562-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="9a562-104">PowerShell Core 是一組可以與 Windows PowerShell 分開出貨、安裝和設定的不同工具和元件。</span><span class="sxs-lookup"><span data-stu-id="9a562-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="9a562-105">因此，Windows 7/8.1/10 或 Windows Server 授權合約不包含 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="9a562-105">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="9a562-106">不過，傳統 Microsoft 支援合約支援 PowerShell Core，包含 [Premier][]、[Microsoft 企業授權][enterprise-agreement]和[軟體保證權益][assurance]。</span><span class="sxs-lookup"><span data-stu-id="9a562-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="9a562-107">您也可以提出您問題的支援要求，付費獲得 PowerShell Core 的[輔助支援][]。</span><span class="sxs-lookup"><span data-stu-id="9a562-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="9a562-108">我們也會在您可提出問題、Bug 或功能要求的 GitHub 上提供[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="9a562-108">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="9a562-109">或者，您可能會在一般 [Microsoft Community][] 或 Microsoft [PowerShell Tech Community][] 上找到其他社群成員的協助。</span><span class="sxs-lookup"><span data-stu-id="9a562-109">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="9a562-110">我們不保證在該處會及時處理或解決您的問題。</span><span class="sxs-lookup"><span data-stu-id="9a562-110">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="9a562-111">如果您有需要立即注意的問題，則應該使用傳統付費支援選項。</span><span class="sxs-lookup"><span data-stu-id="9a562-111">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="9a562-112">PowerShell Core 生命週期</span><span class="sxs-lookup"><span data-stu-id="9a562-112">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="9a562-113">PowerShell Core 會採用 [Microsoft 現代化生命週期原則 ][modern]。</span><span class="sxs-lookup"><span data-stu-id="9a562-113">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="9a562-114">此支援生命週期是要保持客戶的最新版本最新資訊。</span><span class="sxs-lookup"><span data-stu-id="9a562-114">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="9a562-115">大約每六個月更新 PowerShell Core 6.x 版分支一次 (例如 6.0、6.1、6.2 等等)。</span><span class="sxs-lookup"><span data-stu-id="9a562-115">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a562-116">您必須在每個新次要版本發行之後的六個月內進行更新，才能持續接收支援。</span><span class="sxs-lookup"><span data-stu-id="9a562-116">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="9a562-117">例如，如果 PowerShell Core 6.1 是在 2018 年 7 月1 日發行，則必須在 2019 年 1 月 1 日之前更新至 PowerShell Core 6.1 以維護支援。</span><span class="sxs-lookup"><span data-stu-id="9a562-117">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![PowerShell Core 分支生命週期][lifecycle-chart]

<span data-ttu-id="9a562-119">Modern 生命週期原則也需要 Microsoft 在中斷產品 (即 PowerShell Core) 支援之前的 12 個月通知客戶。</span><span class="sxs-lookup"><span data-stu-id="9a562-119">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="9a562-120">最後，我們預期 PowerShell Core 會採用僅需要服務和安全性更新的「長期服務」方式，保持特定 6.x 的分支/版本支援。</span><span class="sxs-lookup"><span data-stu-id="9a562-120">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="9a562-121">支援的平台</span><span class="sxs-lookup"><span data-stu-id="9a562-121">Supported platforms</span></span>

<span data-ttu-id="9a562-122">請參閱下表，以了解您使用的 PowerShell Core 版本所正式支援的平台。</span><span class="sxs-lookup"><span data-stu-id="9a562-122">Please see the following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="9a562-123">我們的社群也針對部分平台貢獻了套件，但這些套件未受正式支援。</span><span class="sxs-lookup"><span data-stu-id="9a562-123">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="9a562-124">這些套件在表格中標示為 `Community`。</span><span class="sxs-lookup"><span data-stu-id="9a562-124">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="9a562-125">列為 `Experimental` 的平台為非正式支援，但可用於實驗和提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="9a562-125">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="9a562-126">6.0</span><span class="sxs-lookup"><span data-stu-id="9a562-126">6.0</span></span>         | <span data-ttu-id="9a562-127">6.1</span><span class="sxs-lookup"><span data-stu-id="9a562-127">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="9a562-128">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="9a562-128">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="9a562-129">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-129">Supported</span></span>   | <span data-ttu-id="9a562-130">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-130">Supported</span></span>   |
| <span data-ttu-id="9a562-131">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="9a562-131">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="9a562-132">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-132">Supported</span></span>   | <span data-ttu-id="9a562-133">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-133">Supported</span></span>   |
| <span data-ttu-id="9a562-134">[Windows Server 半年通道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="9a562-134">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="9a562-135">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-135">Supported</span></span>   | <span data-ttu-id="9a562-136">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-136">Supported</span></span>   |
| <span data-ttu-id="9a562-137">Ubuntu 14.04 和 16.04</span><span class="sxs-lookup"><span data-stu-id="9a562-137">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="9a562-138">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-138">Supported</span></span>   | <span data-ttu-id="9a562-139">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-139">Supported</span></span>   |
| <span data-ttu-id="9a562-140">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9a562-140">Ubuntu 18.04</span></span>                                      |             | <span data-ttu-id="9a562-141">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-141">Supported</span></span>   |
| <span data-ttu-id="9a562-142">Ubuntu 18.10 (透過 Snap 套件)</span><span class="sxs-lookup"><span data-stu-id="9a562-142">Ubuntu 18.10 (via Snap Package)</span></span>                   |             | <span data-ttu-id="9a562-143">群體</span><span class="sxs-lookup"><span data-stu-id="9a562-143">Community</span></span>   |
| <span data-ttu-id="9a562-144">Debian 8.7+ 和 9</span><span class="sxs-lookup"><span data-stu-id="9a562-144">Debian 8.7+, and 9</span></span>                                | <span data-ttu-id="9a562-145">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-145">Supported</span></span>   | <span data-ttu-id="9a562-146">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-146">Supported</span></span>   |
| <span data-ttu-id="9a562-147">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9a562-147">CentOS 7</span></span>                                          | <span data-ttu-id="9a562-148">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-148">Supported</span></span>   | <span data-ttu-id="9a562-149">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-149">Supported</span></span>   |
| <span data-ttu-id="9a562-150">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="9a562-150">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="9a562-151">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-151">Supported</span></span>   | <span data-ttu-id="9a562-152">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-152">Supported</span></span>   |
| <span data-ttu-id="9a562-153">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="9a562-153">OpenSUSE 42.3</span></span>                                     | <span data-ttu-id="9a562-154">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-154">Supported</span></span>   | <span data-ttu-id="9a562-155">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-155">Supported</span></span>   |
| <span data-ttu-id="9a562-156">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="9a562-156">Fedora 27</span></span>                                         | <span data-ttu-id="9a562-157">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-157">Supported</span></span>   | <span data-ttu-id="9a562-158">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-158">Supported</span></span>   |
| <span data-ttu-id="9a562-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="9a562-159">Fedora 28</span></span>                                         |             | <span data-ttu-id="9a562-160">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-160">Supported</span></span>   |
| <span data-ttu-id="9a562-161">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="9a562-161">macOS 10.12+</span></span>                                      | <span data-ttu-id="9a562-162">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-162">Supported</span></span>   | <span data-ttu-id="9a562-163">支援</span><span class="sxs-lookup"><span data-stu-id="9a562-163">Supported</span></span>   |
| <span data-ttu-id="9a562-164">Arch</span><span class="sxs-lookup"><span data-stu-id="9a562-164">Arch</span></span>                                              | <span data-ttu-id="9a562-165">群體</span><span class="sxs-lookup"><span data-stu-id="9a562-165">Community</span></span>   | <span data-ttu-id="9a562-166">群體</span><span class="sxs-lookup"><span data-stu-id="9a562-166">Community</span></span>   |
| <span data-ttu-id="9a562-167">Raspbian</span><span class="sxs-lookup"><span data-stu-id="9a562-167">Raspbian</span></span>                                          | <span data-ttu-id="9a562-168">Experimental</span><span class="sxs-lookup"><span data-stu-id="9a562-168">Experimental</span></span>| <span data-ttu-id="9a562-169">群體</span><span class="sxs-lookup"><span data-stu-id="9a562-169">Community</span></span>   |
| <span data-ttu-id="9a562-170">Kali</span><span class="sxs-lookup"><span data-stu-id="9a562-170">Kali</span></span>                                              | <span data-ttu-id="9a562-171">群體</span><span class="sxs-lookup"><span data-stu-id="9a562-171">Community</span></span>   | <span data-ttu-id="9a562-172">群體</span><span class="sxs-lookup"><span data-stu-id="9a562-172">Community</span></span>   |
| <span data-ttu-id="9a562-173">AppImage (作用於多個 Linux 平台)</span><span class="sxs-lookup"><span data-stu-id="9a562-173">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="9a562-174">群體</span><span class="sxs-lookup"><span data-stu-id="9a562-174">Community</span></span>   | <span data-ttu-id="9a562-175">群體</span><span class="sxs-lookup"><span data-stu-id="9a562-175">Community</span></span>   |
| [<span data-ttu-id="9a562-176">Snap 套件</span><span class="sxs-lookup"><span data-stu-id="9a562-176">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="9a562-177">請參閱備註</span><span class="sxs-lookup"><span data-stu-id="9a562-177">See note</span></span>    | <span data-ttu-id="9a562-178">請參閱備註</span><span class="sxs-lookup"><span data-stu-id="9a562-178">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="9a562-179">Snap 套件會有一段時間處於實驗階段。</span><span class="sxs-lookup"><span data-stu-id="9a562-179">Snap packages will be experimental for a period.</span></span>  <span data-ttu-id="9a562-180">之後，我們相信 Snap 就不會帶來新的支援問題，而支援會跟隨於您執行套件的發佈。</span><span class="sxs-lookup"><span data-stu-id="9a562-180">After, we are confident that Snap does not introduce new support issues, the support will follow the distribution you are running the package on.</span></span>

## <a name="platform-which-are-out-of-support"></a><span data-ttu-id="9a562-181">支援終止的平台</span><span class="sxs-lookup"><span data-stu-id="9a562-181">Platform which are out of support</span></span>

<span data-ttu-id="9a562-182">當平台版本到達平台擁有者所定義的生命週期結束時，PowerShell Core 也會停止對該平台版本提供支援。</span><span class="sxs-lookup"><span data-stu-id="9a562-182">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to provide support for that platform version.</span></span> <span data-ttu-id="9a562-183">先前推出的套件仍然可供需要存取的客戶取得，但將不再提供任何類型的正式支援和更新。</span><span class="sxs-lookup"><span data-stu-id="9a562-183">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="9a562-184">因此，以下版本的支援已經由發行版本擁有者終止，且不受支援。</span><span class="sxs-lookup"><span data-stu-id="9a562-184">Therefore, support for the following versions was ended by the distribution owners and are not supported.</span></span>

| <span data-ttu-id="9a562-185">作業系統</span><span class="sxs-lookup"><span data-stu-id="9a562-185">OS</span></span>       | <span data-ttu-id="9a562-186">版本</span><span class="sxs-lookup"><span data-stu-id="9a562-186">Version</span></span> | <span data-ttu-id="9a562-187">生命週期結束</span><span class="sxs-lookup"><span data-stu-id="9a562-187">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="9a562-188">Fedora</span><span class="sxs-lookup"><span data-stu-id="9a562-188">Fedora</span></span>   | <span data-ttu-id="9a562-189">24</span><span class="sxs-lookup"><span data-stu-id="9a562-189">24</span></span>      | [<span data-ttu-id="9a562-190">2017 年 8 月</span><span class="sxs-lookup"><span data-stu-id="9a562-190">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="9a562-191">Fedora</span><span class="sxs-lookup"><span data-stu-id="9a562-191">Fedora</span></span>   | <span data-ttu-id="9a562-192">25</span><span class="sxs-lookup"><span data-stu-id="9a562-192">25</span></span>      | [<span data-ttu-id="9a562-193">2017 年 12 月</span><span class="sxs-lookup"><span data-stu-id="9a562-193">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="9a562-194">Fedora</span><span class="sxs-lookup"><span data-stu-id="9a562-194">Fedora</span></span>   | <span data-ttu-id="9a562-195">26</span><span class="sxs-lookup"><span data-stu-id="9a562-195">26</span></span>      | [<span data-ttu-id="9a562-196">2018 年 5 月</span><span class="sxs-lookup"><span data-stu-id="9a562-196">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="9a562-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="9a562-197">openSUSE</span></span> | <span data-ttu-id="9a562-198">42.1</span><span class="sxs-lookup"><span data-stu-id="9a562-198">42.1</span></span>    | [<span data-ttu-id="9a562-199">2017 年 5 月</span><span class="sxs-lookup"><span data-stu-id="9a562-199">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="9a562-200">openSUSE</span><span class="sxs-lookup"><span data-stu-id="9a562-200">openSUSE</span></span> | <span data-ttu-id="9a562-201">42.2</span><span class="sxs-lookup"><span data-stu-id="9a562-201">42.2</span></span>    | [<span data-ttu-id="9a562-202">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="9a562-202">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="9a562-203">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9a562-203">Ubuntu</span></span>   | <span data-ttu-id="9a562-204">16.10</span><span class="sxs-lookup"><span data-stu-id="9a562-204">16.10</span></span>   | [<span data-ttu-id="9a562-205">2017 年 7 月</span><span class="sxs-lookup"><span data-stu-id="9a562-205">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="9a562-206">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9a562-206">Ubuntu</span></span>   | <span data-ttu-id="9a562-207">17.04</span><span class="sxs-lookup"><span data-stu-id="9a562-207">17.04</span></span>   | [<span data-ttu-id="9a562-208">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="9a562-208">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="9a562-209">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9a562-209">Ubuntu</span></span>   | <span data-ttu-id="9a562-210">17.10</span><span class="sxs-lookup"><span data-stu-id="9a562-210">17.10</span></span>   | [<span data-ttu-id="9a562-211">2018 年 7 月</span><span class="sxs-lookup"><span data-stu-id="9a562-211">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a><span data-ttu-id="9a562-212">授權附註</span><span class="sxs-lookup"><span data-stu-id="9a562-212">Notes on licensing</span></span>

<span data-ttu-id="9a562-213">PowerShell Core 是透過 [MIT 授權][]所發行。</span><span class="sxs-lookup"><span data-stu-id="9a562-213">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="9a562-214">透過此授權，而且沒有付費支援合約，則使用者就只有[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="9a562-214">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="9a562-215">運用社群支援，Microsoft 不保證會回應或修正。</span><span class="sxs-lookup"><span data-stu-id="9a562-215">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="9a562-216">Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="9a562-216">Windows PowerShell Module</span></span>

<span data-ttu-id="9a562-217">除非其他產品模組明確支援 PowerShell Core，否則 PowerShell Core 支援不會延伸到這些模組。</span><span class="sxs-lookup"><span data-stu-id="9a562-217">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="9a562-218">例如，使用隨附為 Windows Server 一部分的 `ActiveDirectory` 模組，就是不支援的案例。</span><span class="sxs-lookup"><span data-stu-id="9a562-218">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="9a562-219">不過，在某些情況下，未明確支援 PowerShell Core 的模組可能會相容。</span><span class="sxs-lookup"><span data-stu-id="9a562-219">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="9a562-220">安裝 [`WindowsPSModulePath`][] 模組，即可將 Windows PowerShell `PSModulePath` 附加至 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="9a562-220">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="9a562-221">首先，從 PowerShell 資源庫安裝 `WindowsPSModulePath` 模組：</span><span class="sxs-lookup"><span data-stu-id="9a562-221">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="9a562-222">安裝此模組之後，請執行 `Add-WindowsPSModulePath` Cmdlet，以將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="9a562-222">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

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
