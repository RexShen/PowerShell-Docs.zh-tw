# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="58603-101">PowerShell Core 支援週期</span><span class="sxs-lookup"><span data-stu-id="58603-101">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="58603-102">PowerShell Core 是一組可以與 Windows PowerShell 分開出貨、安裝和設定的不同工具和元件。</span><span class="sxs-lookup"><span data-stu-id="58603-102">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="58603-103">因此，Windows 7/8.1/10 或 Windows Server 授權合約不包含 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="58603-103">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="58603-104">不過，傳統 Microsoft 支援合約支援 PowerShell Core，包含 [Premier][]、[Microsoft 企業授權][enterprise-agreement]和[軟體保證權益][assurance]。</span><span class="sxs-lookup"><span data-stu-id="58603-104">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="58603-105">您也可以提出您問題的支援要求，付費獲得 PowerShell Core 的[輔助支援][]。</span><span class="sxs-lookup"><span data-stu-id="58603-105">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="58603-106">我們也會在您可提出問題、Bug 或功能要求的 GitHub 上提供[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="58603-106">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="58603-107">或者，您可能會在一般 [Microsoft Community][] 或 Microsoft [PowerShell Tech Community][] 上找到其他社群成員的協助。</span><span class="sxs-lookup"><span data-stu-id="58603-107">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="58603-108">我們不保證在該處會及時處理或解決您的問題。</span><span class="sxs-lookup"><span data-stu-id="58603-108">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="58603-109">如果您有需要立即注意的問題，則應該使用傳統付費支援選項。</span><span class="sxs-lookup"><span data-stu-id="58603-109">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="58603-110">PowerShell Core 生命週期</span><span class="sxs-lookup"><span data-stu-id="58603-110">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="58603-111">PowerShell Core 會採用 [Microsoft 現代化生命週期原則 ][modern]。</span><span class="sxs-lookup"><span data-stu-id="58603-111">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="58603-112">此支援生命週期是要保持客戶的最新版本最新資訊。</span><span class="sxs-lookup"><span data-stu-id="58603-112">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="58603-113">大約每六個月更新 PowerShell Core 6.x 版分支一次 (例如 6.0、6.1、6.2 等等)。</span><span class="sxs-lookup"><span data-stu-id="58603-113">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="58603-114">您必須在每個新次要版本發行之後的六個月內進行更新，才能持續接收支援。</span><span class="sxs-lookup"><span data-stu-id="58603-114">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="58603-115">例如，如果 PowerShell Core 6.1 是在 2018 年 7 月1 日發行，則必須在 2019 年 1 月 1 日之前更新至 PowerShell Core 6.1 以維護支援。</span><span class="sxs-lookup"><span data-stu-id="58603-115">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![PowerShell Core 分支生命週期][lifecycle-chart]

<span data-ttu-id="58603-117">Modern 生命週期原則也需要 Microsoft 在中斷產品 (即 PowerShell Core) 支援之前的 12 個月通知客戶。</span><span class="sxs-lookup"><span data-stu-id="58603-117">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="58603-118">最後，我們預期 PowerShell Core 會採用僅需要服務和安全性更新的「長期服務」方式，保持特定 6.x 的分支/版本支援。</span><span class="sxs-lookup"><span data-stu-id="58603-118">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="58603-119">支援的平台</span><span class="sxs-lookup"><span data-stu-id="58603-119">Supported platforms</span></span>

<span data-ttu-id="58603-120">下列平台正式支援 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="58603-120">PowerShell Core is officially supported on the following platforms:</span></span>

* <span data-ttu-id="58603-121">Windows 7、8.1 和 10</span><span class="sxs-lookup"><span data-stu-id="58603-121">Windows 7, 8.1, and 10</span></span>
* <span data-ttu-id="58603-122">Windows Server 2008 R2、2012 R2、2016</span><span class="sxs-lookup"><span data-stu-id="58603-122">Windows Server 2008 R2, 2012 R2, 2016</span></span>
* <span data-ttu-id="58603-123">[Windows Server 半年通道][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="58603-123">[Windows Server Semi-Annual Channel][semi-annual]</span></span>
* <span data-ttu-id="58603-124">Ubuntu 14.04、16.04 和 17.04</span><span class="sxs-lookup"><span data-stu-id="58603-124">Ubuntu 14.04, 16.04, and 17.04</span></span>
* <span data-ttu-id="58603-125">Debian 8.7+ 和 9</span><span class="sxs-lookup"><span data-stu-id="58603-125">Debian 8.7+, and 9</span></span>
* <span data-ttu-id="58603-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="58603-126">CentOS 7</span></span>
* <span data-ttu-id="58603-127">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="58603-127">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="58603-128">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="58603-128">OpenSUSE 42.2</span></span>
* <span data-ttu-id="58603-129">Fedora 25、26</span><span class="sxs-lookup"><span data-stu-id="58603-129">Fedora 25, 26</span></span>
* <span data-ttu-id="58603-130">macOS 10.12+</span><span class="sxs-lookup"><span data-stu-id="58603-130">macOS 10.12+</span></span>

<span data-ttu-id="58603-131">我們的社群也提供下列平台的套件，但未正式進行支援：</span><span class="sxs-lookup"><span data-stu-id="58603-131">Our community has also contributed packages for the following platforms, but they are not officially suppported:</span></span>

* <span data-ttu-id="58603-132">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="58603-132">Arch Linux</span></span>
* <span data-ttu-id="58603-133">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="58603-133">Kali Linux</span></span>
* <span data-ttu-id="58603-134">AppImage (作用於多個 Linux 平台)</span><span class="sxs-lookup"><span data-stu-id="58603-134">AppImage (works on multiple Linux platforms)</span></span>

## <a name="notes-on-licensing"></a><span data-ttu-id="58603-135">授權附註</span><span class="sxs-lookup"><span data-stu-id="58603-135">Notes on licensing</span></span>

<span data-ttu-id="58603-136">PowerShell Core 是透過 [MIT 授權][]所發行。</span><span class="sxs-lookup"><span data-stu-id="58603-136">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="58603-137">透過此授權，而且沒有付費支援合約，則使用者就只有[社群支援][]。</span><span class="sxs-lookup"><span data-stu-id="58603-137">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="58603-138">運用社群支援，Microsoft 不保證會回應或修正。</span><span class="sxs-lookup"><span data-stu-id="58603-138">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="58603-139">Windows PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="58603-139">Windows PowerShell Module</span></span>

<span data-ttu-id="58603-140">除非其他產品模組明確支援 PowerShell Core，否則 PowerShell Core 支援不會延伸到這些模組。</span><span class="sxs-lookup"><span data-stu-id="58603-140">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="58603-141">例如，使用隨附為 Windows Server 一部分的 `ActiveDirectory` 模組，就是不支援的案例。</span><span class="sxs-lookup"><span data-stu-id="58603-141">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="58603-142">不過，在某些情況下，未明確支援 PowerShell Core 的模組可能會相容。</span><span class="sxs-lookup"><span data-stu-id="58603-142">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="58603-143">安裝 [`WindowsPSModulePath`][] 模組，即可將 Windows PowerShell `PSModulePath` 附加至 PowerShell Core `PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="58603-143">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="58603-144">首先，從 PowerShell 資源庫安裝 `WindowsPSModulePath` 模組：</span><span class="sxs-lookup"><span data-stu-id="58603-144">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="58603-145">安裝此模組之後，請執行 `Add-WindowsPSModulePath` Cmdlet，以將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core：</span><span class="sxs-lookup"><span data-stu-id="58603-145">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

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