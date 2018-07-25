# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="c0826-101">PowerShell Core 支援週期</span><span class="sxs-lookup"><span data-stu-id="c0826-101">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="c0826-102">PowerShell Core 是一組可以與 Windows PowerShell 分開出貨、安裝和設定的不同工具和元件。</span><span class="sxs-lookup"><span data-stu-id="c0826-102">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="c0826-103">因此，Windows 7/8.1/10 或 Windows Server 授權合約不包含 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="c0826-103">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="c0826-104">不過，傳統 Microsoft 支援合約支援 PowerShell Core，包含 [Premier][]、[Microsoft 企業授權][enterprise-agreement]和[軟體保證權益][assurance]。</span><span class="sxs-lookup"><span data-stu-id="c0826-104">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="c0826-105">您也可以提出您問題的支援要求，付費獲得 PowerShell Core 的[輔助支援][]。</span><span class="sxs-lookup"><span data-stu-id="c0826-105">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="c0826-106">我們也會在您可提出問題、Bug 或功能要求的 GitHub 上提供[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="c0826-106">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="c0826-107">或者，您可能會在一般 [Microsoft Community][] 或 Microsoft [PowerShell Tech Community][] 上找到其他社群成員的協助。</span><span class="sxs-lookup"><span data-stu-id="c0826-107">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="c0826-108">我們不保證在該處會及時處理或解決您的問題。</span><span class="sxs-lookup"><span data-stu-id="c0826-108">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="c0826-109">如果您有需要立即注意的問題，則應該使用傳統付費支援選項。</span><span class="sxs-lookup"><span data-stu-id="c0826-109">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="c0826-110">PowerShell Core 生命週期</span><span class="sxs-lookup"><span data-stu-id="c0826-110">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="c0826-111">PowerShell Core 會採用 [Microsoft 現代化生命週期原則 ][modern]。</span><span class="sxs-lookup"><span data-stu-id="c0826-111">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="c0826-112">此支援生命週期是要保持客戶的最新版本最新資訊。</span><span class="sxs-lookup"><span data-stu-id="c0826-112">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="c0826-113">大約每六個月更新 PowerShell Core 6.x 版分支一次 (例如 6.0、6.1、6.2 等等)。</span><span class="sxs-lookup"><span data-stu-id="c0826-113">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0826-114">您必須在每個新次要版本發行之後的六個月內進行更新，才能持續接收支援。</span><span class="sxs-lookup"><span data-stu-id="c0826-114">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="c0826-115">例如，如果 PowerShell Core 6.1 是在 2018 年 7 月1 日發行，則必須在 2019 年 1 月 1 日之前更新至 PowerShell Core 6.1 以維護支援。</span><span class="sxs-lookup"><span data-stu-id="c0826-115">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![PowerShell Core 分支生命週期][lifecycle-chart]

<span data-ttu-id="c0826-117">Modern 生命週期原則也需要 Microsoft 在中斷產品 (即 PowerShell Core) 支援之前的 12 個月通知客戶。</span><span class="sxs-lookup"><span data-stu-id="c0826-117">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="c0826-118">最後，我們預期 PowerShell Core 會採用僅需要服務和安全性更新的「長期服務」方式，保持特定 6.x 的分支/版本支援。</span><span class="sxs-lookup"><span data-stu-id="c0826-118">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="c0826-119">支援的平台</span><span class="sxs-lookup"><span data-stu-id="c0826-119">Supported platforms</span></span>

<span data-ttu-id="c0826-120">請參閱下表，以了解您使用的 PowerShell Core 版本所正式支援的平台。</span><span class="sxs-lookup"><span data-stu-id="c0826-120">Please see the following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="c0826-121">我們的社群也針對部分平台貢獻了套件，但這些套件未受正式支援。</span><span class="sxs-lookup"><span data-stu-id="c0826-121">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="c0826-122">這些套件在表格中標示為 `Community`。</span><span class="sxs-lookup"><span data-stu-id="c0826-122">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="c0826-123">列為 `Experimental` 的平台為非正式支援，但可用於實驗和提供意見反應。</span><span class="sxs-lookup"><span data-stu-id="c0826-123">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="c0826-124">6.0</span><span class="sxs-lookup"><span data-stu-id="c0826-124">6.0</span></span>         | <span data-ttu-id="c0826-125">6.1</span><span class="sxs-lookup"><span data-stu-id="c0826-125">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="c0826-126">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="c0826-126">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="c0826-127">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-127">Supported</span></span>   | <span data-ttu-id="c0826-128">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-128">Supported</span></span>   |
| <span data-ttu-id="c0826-129">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="c0826-129">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="c0826-130">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-130">Supported</span></span>   | <span data-ttu-id="c0826-131">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-131">Supported</span></span>   |
| <span data-ttu-id="c0826-132">[Windows Server 半年通道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="c0826-132">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="c0826-133">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-133">Supported</span></span>   | <span data-ttu-id="c0826-134">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-134">Supported</span></span>   |
| <span data-ttu-id="c0826-135">Ubuntu 14.04 和 16.04</span><span class="sxs-lookup"><span data-stu-id="c0826-135">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="c0826-136">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-136">Supported</span></span>   | <span data-ttu-id="c0826-137">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-137">Supported</span></span>   |
| <span data-ttu-id="c0826-138">Ubuntu 17.10 和 18.04</span><span class="sxs-lookup"><span data-stu-id="c0826-138">Ubuntu 17.10, and 18.04</span></span>                           |             | <span data-ttu-id="c0826-139">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-139">Supported</span></span>   |
| <span data-ttu-id="c0826-140">Debian 8.7+ 和 9</span><span class="sxs-lookup"><span data-stu-id="c0826-140">Debian 8.7+, and 9</span></span>                                | <span data-ttu-id="c0826-141">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-141">Supported</span></span>   | <span data-ttu-id="c0826-142">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-142">Supported</span></span>   |
| <span data-ttu-id="c0826-143">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c0826-143">CentOS 7</span></span>                                          | <span data-ttu-id="c0826-144">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-144">Supported</span></span>   | <span data-ttu-id="c0826-145">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-145">Supported</span></span>   |
| <span data-ttu-id="c0826-146">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="c0826-146">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="c0826-147">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-147">Supported</span></span>   | <span data-ttu-id="c0826-148">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-148">Supported</span></span>   |
| <span data-ttu-id="c0826-149">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c0826-149">OpenSUSE 42.2</span></span>                                     | <span data-ttu-id="c0826-150">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-150">Supported</span></span>   | <span data-ttu-id="c0826-151">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-151">Supported</span></span>   |
| <span data-ttu-id="c0826-152">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="c0826-152">Fedora 27</span></span>                                         | <span data-ttu-id="c0826-153">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-153">Supported</span></span>   | <span data-ttu-id="c0826-154">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-154">Supported</span></span>   |
| <span data-ttu-id="c0826-155">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="c0826-155">Fedora 28</span></span>                                         |             | <span data-ttu-id="c0826-156">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-156">Supported</span></span>   |
| <span data-ttu-id="c0826-157">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="c0826-157">macOS 10.12+</span></span>                                      | <span data-ttu-id="c0826-158">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-158">Supported</span></span>   | <span data-ttu-id="c0826-159">支援</span><span class="sxs-lookup"><span data-stu-id="c0826-159">Supported</span></span>   |
| <span data-ttu-id="c0826-160">Arch</span><span class="sxs-lookup"><span data-stu-id="c0826-160">Arch</span></span>                                              | <span data-ttu-id="c0826-161">群體</span><span class="sxs-lookup"><span data-stu-id="c0826-161">Community</span></span>   | <span data-ttu-id="c0826-162">群體</span><span class="sxs-lookup"><span data-stu-id="c0826-162">Community</span></span>   |
| <span data-ttu-id="c0826-163">Raspbian</span><span class="sxs-lookup"><span data-stu-id="c0826-163">Raspbian</span></span>                                          | <span data-ttu-id="c0826-164">Experimental</span><span class="sxs-lookup"><span data-stu-id="c0826-164">Experimental</span></span>| <span data-ttu-id="c0826-165">群體</span><span class="sxs-lookup"><span data-stu-id="c0826-165">Community</span></span>   |
| <span data-ttu-id="c0826-166">Kali</span><span class="sxs-lookup"><span data-stu-id="c0826-166">Kali</span></span>                                              | <span data-ttu-id="c0826-167">群體</span><span class="sxs-lookup"><span data-stu-id="c0826-167">Community</span></span>   | <span data-ttu-id="c0826-168">群體</span><span class="sxs-lookup"><span data-stu-id="c0826-168">Community</span></span>   |
| <span data-ttu-id="c0826-169">AppImage (作用於多個 Linux 平台)</span><span class="sxs-lookup"><span data-stu-id="c0826-169">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="c0826-170">群體</span><span class="sxs-lookup"><span data-stu-id="c0826-170">Community</span></span>   | <span data-ttu-id="c0826-171">群體</span><span class="sxs-lookup"><span data-stu-id="c0826-171">Community</span></span>   |

## <a name="platform-which-are-out-of-support"></a><span data-ttu-id="c0826-172">支援終止的平台</span><span class="sxs-lookup"><span data-stu-id="c0826-172">Platform which are out of support</span></span>

<span data-ttu-id="c0826-173">當平台版本到達平台擁有者所定義的生命週期結束時，PowerShell Core 也會停止對該平台版本提供支援。</span><span class="sxs-lookup"><span data-stu-id="c0826-173">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to provide support for that platform version.</span></span> <span data-ttu-id="c0826-174">先前推出的套件仍然可供需要存取的客戶取得，但將不再提供任何類型的正式支援和更新。</span><span class="sxs-lookup"><span data-stu-id="c0826-174">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="c0826-175">因此，以下版本的支援已經由發行版本擁有者終止，且不受支援。</span><span class="sxs-lookup"><span data-stu-id="c0826-175">Therefore, support for the following versions was ended by the distribution owners and are not supported.</span></span>

| <span data-ttu-id="c0826-176">作業系統</span><span class="sxs-lookup"><span data-stu-id="c0826-176">OS</span></span>       | <span data-ttu-id="c0826-177">版本</span><span class="sxs-lookup"><span data-stu-id="c0826-177">Version</span></span> | <span data-ttu-id="c0826-178">生命週期結束</span><span class="sxs-lookup"><span data-stu-id="c0826-178">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="c0826-179">Fedora</span><span class="sxs-lookup"><span data-stu-id="c0826-179">Fedora</span></span>   | <span data-ttu-id="c0826-180">26</span><span class="sxs-lookup"><span data-stu-id="c0826-180">26</span></span>      | [<span data-ttu-id="c0826-181">2018 年 5 月</span><span class="sxs-lookup"><span data-stu-id="c0826-181">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="c0826-182">Fedora</span><span class="sxs-lookup"><span data-stu-id="c0826-182">Fedora</span></span>   | <span data-ttu-id="c0826-183">25</span><span class="sxs-lookup"><span data-stu-id="c0826-183">25</span></span>      | [<span data-ttu-id="c0826-184">2017 年 12 月</span><span class="sxs-lookup"><span data-stu-id="c0826-184">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="c0826-185">Fedora</span><span class="sxs-lookup"><span data-stu-id="c0826-185">Fedora</span></span>   | <span data-ttu-id="c0826-186">24</span><span class="sxs-lookup"><span data-stu-id="c0826-186">24</span></span>      | [<span data-ttu-id="c0826-187">2017 年 8 月</span><span class="sxs-lookup"><span data-stu-id="c0826-187">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="c0826-188">openSUSE</span><span class="sxs-lookup"><span data-stu-id="c0826-188">openSUSE</span></span> | <span data-ttu-id="c0826-189">42.2</span><span class="sxs-lookup"><span data-stu-id="c0826-189">42.2</span></span>    | [<span data-ttu-id="c0826-190">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="c0826-190">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="c0826-191">openSUSE</span><span class="sxs-lookup"><span data-stu-id="c0826-191">openSUSE</span></span> | <span data-ttu-id="c0826-192">42.1</span><span class="sxs-lookup"><span data-stu-id="c0826-192">42.1</span></span>    | [<span data-ttu-id="c0826-193">2017 年 5 月</span><span class="sxs-lookup"><span data-stu-id="c0826-193">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="c0826-194">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c0826-194">Ubuntu</span></span>   | <span data-ttu-id="c0826-195">17.04</span><span class="sxs-lookup"><span data-stu-id="c0826-195">17.04</span></span>   | [<span data-ttu-id="c0826-196">2018 年 1 月</span><span class="sxs-lookup"><span data-stu-id="c0826-196">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="c0826-197">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c0826-197">Ubuntu</span></span>   | <span data-ttu-id="c0826-198">16.10</span><span class="sxs-lookup"><span data-stu-id="c0826-198">16.10</span></span>   | [<span data-ttu-id="c0826-199">2017 年 7 月</span><span class="sxs-lookup"><span data-stu-id="c0826-199">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |

## <a name="notes-on-licensing"></a><span data-ttu-id="c0826-200">授權附註</span><span class="sxs-lookup"><span data-stu-id="c0826-200">Notes on licensing</span></span>

<span data-ttu-id="c0826-201">PowerShell Core 是透過 [MIT 授權][]所發行。</span><span class="sxs-lookup"><span data-stu-id="c0826-201">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="c0826-202">透過此授權，而且沒有付費支援合約，則使用者就只有[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="c0826-202">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="c0826-203">運用社群支援，Microsoft 不保證會回應或修正。</span><span class="sxs-lookup"><span data-stu-id="c0826-203">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="c0826-204">Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="c0826-204">Windows PowerShell Module</span></span>

<span data-ttu-id="c0826-205">除非其他產品模組明確支援 PowerShell Core，否則 PowerShell Core 支援不會延伸到這些模組。</span><span class="sxs-lookup"><span data-stu-id="c0826-205">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="c0826-206">例如，使用隨附為 Windows Server 一部分的 `ActiveDirectory` 模組，就是不支援的案例。</span><span class="sxs-lookup"><span data-stu-id="c0826-206">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="c0826-207">不過，在某些情況下，未明確支援 PowerShell Core 的模組可能會相容。</span><span class="sxs-lookup"><span data-stu-id="c0826-207">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="c0826-208">安裝 [`WindowsPSModulePath`][] 模組，即可將 Windows PowerShell `PSModulePath` 附加至 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="c0826-208">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="c0826-209">首先，從 PowerShell 資源庫安裝 `WindowsPSModulePath` 模組：</span><span class="sxs-lookup"><span data-stu-id="c0826-209">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="c0826-210">安裝此模組之後，請執行 `Add-WindowsPSModulePath` Cmdlet，以將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="c0826-210">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

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
