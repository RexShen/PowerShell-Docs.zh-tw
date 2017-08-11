---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "安裝和使用 Windows PowerShell Web 存取"
ms.openlocfilehash: a860f7c22829da46f0458ea729fa0afd1fe4fb6f
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
#  <a name="install-and-use-windows-powershell-web-access"></a><span data-ttu-id="21d40-103">安裝和使用 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="21d40-103">Install and Use Windows PowerShell Web Access</span></span>

<span data-ttu-id="21d40-104">更新日期︰2013 年 11 月 5 日</span><span class="sxs-lookup"><span data-stu-id="21d40-104">Updated: November 5, 2013</span></span>

<span data-ttu-id="21d40-105">適用目標︰Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="21d40-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="21d40-106">Windows PowerShell® Web 存取是在 Windows Server® 2012 中首度引進來做為 Windows PowerShell 閘道，可提供以遠端電腦為目標的網頁型 Windows PowerShell 主控台。</span><span class="sxs-lookup"><span data-stu-id="21d40-106">Windows PowerShell® Web Access, first introduced in Windows Server® 2012, acts as a Windows PowerShell gateway, providing a web-based Windows PowerShell console that is targeted at a remote computer.</span></span> <span data-ttu-id="21d40-107">它可讓 IT 專業人員在網頁瀏覽器中，從 Windows PowerShell 主控台執行 Windows PowerShell 命令和指令碼，而不需要 Windows PowerShell、遠端管理軟體，或者在用戶端裝置上安裝瀏覽器外掛程式。</span><span class="sxs-lookup"><span data-stu-id="21d40-107">It enables IT Pros to run Windows PowerShell commands and scripts from a Windows PowerShell console in a web browser, with no Windows PowerShell, remote management software, or browser plug-in installation necessary on the client device.</span></span> <span data-ttu-id="21d40-108">執行網頁型 Windows PowerShell 主控台只需要正確設定的 Windows PowerShell Web 存取閘道，以及支援 JavaScript® 且接受 Cookie 的用戶端裝置瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="21d40-108">All that is required to run the web-based Windows PowerShell console is a properly-configured Windows PowerShell Web Access gateway, and a client device browser that supports JavaScript® and accepts cookies.</span></span>

<span data-ttu-id="21d40-109">用戶端裝置的範例包含膝上型電腦、非工作用個人電腦、租借電腦、平板電腦、網路工作站、執行非 Windows 作業系統的電腦以及行動電話瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="21d40-109">Examples of client devices include laptops, non-work personal computers, borrowed computers, tablet computers, web kiosks, computers that are not running a Windows-based operating system, and cell phone browsers.</span></span> <span data-ttu-id="21d40-110">IT 專業人員能夠從可以存取網際網路連線的裝置及網頁瀏覽器，執行遠端 Windows 伺服器的重要管理工作。</span><span class="sxs-lookup"><span data-stu-id="21d40-110">IT Pros can perform critical management tasks on remote Windows-based servers from devices that have access to an Internet connection and a web browser.</span></span>

<span data-ttu-id="21d40-111">成功安裝和設定閘道之後，使用者就可以使用網頁瀏覽器來存取 Windows PowerShell 主控台。</span><span class="sxs-lookup"><span data-stu-id="21d40-111">After successful gateway setup and configuration, users can access a Windows PowerShell console by using a web browser.</span></span> <span data-ttu-id="21d40-112">當使用者開啟受保護的 Windows PowerShell Web 存取網站時，就可以在成功驗證之後執行網頁型 Windows PowerShell 主控台。</span><span class="sxs-lookup"><span data-stu-id="21d40-112">When users open the secured Windows PowerShell Web Access website, they can run a web-based Windows PowerShell console after successful authentication.</span></span>

<span data-ttu-id="21d40-113">安裝和設定 Windows PowerShell Web 存取時需要執行三個步驟：</span><span class="sxs-lookup"><span data-stu-id="21d40-113">Windows PowerShell Web Access setup and configuration is a three-step process:</span></span>

1.  <span data-ttu-id="21d40-114">安裝 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="21d40-114">Installing Windows PowerShell Web Access</span></span>

2.  <span data-ttu-id="21d40-115">設定閘道</span><span class="sxs-lookup"><span data-stu-id="21d40-115">Configuring the gateway</span></span>

3.  <span data-ttu-id="21d40-116">設定授權規則，以允許使用者存取網頁型 Windows PowerShell 主控台</span><span class="sxs-lookup"><span data-stu-id="21d40-116">Configuring authorization rules that allow users access to the web-based Windows PowerShell console</span></span>

<span data-ttu-id="21d40-117">安裝和設定 Windows PowerShell Web 存取之前，建議您完整閱讀本指南，其中包含如何安裝、保護和解除安裝 Windows PowerShell Web 存取的相關指示。</span><span class="sxs-lookup"><span data-stu-id="21d40-117">Before you install and configure Windows PowerShell Web Access, we recommend that you read this entire guide, which includes instructions about how to install, secure, and uninstall Windows PowerShell Web Access.</span></span> <span data-ttu-id="21d40-118">[使用網頁型 Windows PowerShell 主控台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)主題說明使用者如何登入網頁型主控台，並涵蓋了網頁型 Windows PowerShell 主控台和 **powershell.exe** 主控台之間的限制及差異。</span><span class="sxs-lookup"><span data-stu-id="21d40-118">The [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) topic describes how users sign in to the web-based console, and covers limitations and differences between the web-based Windows PowerShell console and the **powershell.exe** console.</span></span> <span data-ttu-id="21d40-119">網頁型主控台的使用者應該閱讀[使用網頁型 Windows PowerShell 主控台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)，但不需要閱讀本指南的其他章節。</span><span class="sxs-lookup"><span data-stu-id="21d40-119">End users of the web-based console should read [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), but do not need to read the rest of this guide.</span></span>

<span data-ttu-id="21d40-120">本主題不提供深入的網頁伺服器 (IIS) 操作指導方針；只會說明設定 Windows PowerShell Web 存取閘道所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="21d40-120">This topic does not provide in-depth Web Server (IIS) operations guidance; only those steps required to configure the Windows PowerShell Web Access gateway are described in this topic.</span></span> <span data-ttu-id="21d40-121">如需設定和保護 IIS 網站安全的詳細資訊，請參閱＜另請參閱＞一節中的 IIS 文件資源。</span><span class="sxs-lookup"><span data-stu-id="21d40-121">For more information about configuring and securing websites in IIS, see the IIS documentation resources in the See Also section.</span></span>

<span data-ttu-id="21d40-122">下圖顯示 Windows PowerShell Web 存取的運作方式。</span><span class="sxs-lookup"><span data-stu-id="21d40-122">The following diagram shows how Windows PowerShell Web Access works.</span></span>

<span><img src="https://i-technet.sec.s-msft.com/dynimg/IC564303.jpeg" title="Windows PowerShell Web Access diagram" alt="Windows PowerShell Web Access diagram" id="ee15fa8f-ce13-49e5-933d-514f6d60a2b1" /></span>

<span data-ttu-id="21d40-123">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="21d40-123">In this topic:</span></span>

-   [<span data-ttu-id="21d40-124">執行 Windows PowerShell Web 存取的需求</span><span class="sxs-lookup"><span data-stu-id="21d40-124">Requirements for running Windows PowerShell Web Access</span></span>](#BKMK_reqs)

-   [<span data-ttu-id="21d40-125">瀏覽器及用戶端裝置支援</span><span class="sxs-lookup"><span data-stu-id="21d40-125">Browser and client device support</span></span>](#BKMK_browser)

-   [<span data-ttu-id="21d40-126">建議 (快速) 部署</span><span class="sxs-lookup"><span data-stu-id="21d40-126">Recommended (quick) deployment</span></span>](#BKMK_recm)

-   [<span data-ttu-id="21d40-127">自訂部署</span><span class="sxs-lookup"><span data-stu-id="21d40-127">Custom deployment</span></span>](#BKMK_custom)

-   [<span data-ttu-id="21d40-128">設定正版憑證</span><span class="sxs-lookup"><span data-stu-id="21d40-128">Configure a genuine certificate</span></span>](#BKMK_configcert)

<a href="" id="BKMK_reqs"></a>

<span data-ttu-id="21d40-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">執行 Windows PowerShell Web 存取的需求</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="21d40-129"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requirements for running Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="21d40-130">Windows PowerShell Web 存取需要網頁伺服器 (IIS)、.NET Framework 4.5，以及 Windows PowerShell 3.0 或 Windows PowerShell 4.0，才能在您要執行閘道的伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="21d40-130">Windows PowerShell Web Access requires Web Server (IIS), .NET Framework 4.5, and Windows PowerShell 3.0 or Windows PowerShell 4.0 to be running on the server on which you want to run the gateway.</span></span> <span data-ttu-id="21d40-131">您可以使用伺服器管理員中的 [新增角色及功能精靈] 或伺服器管理員的 Windows PowerShell 部署 Cmdlet，在執行 Windows Server 2012 R2 或 Windows Server 2012 的伺服器上安裝 Windows PowerShell Web 存取。</span><span class="sxs-lookup"><span data-stu-id="21d40-131">You can install Windows PowerShell Web Access on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either the Add Roles and Features Wizard in Server Manager, or Windows PowerShell deployment cmdlets for Server Manager.</span></span> <span data-ttu-id="21d40-132">使用伺服器管理員或其部署 Cmdlet 安裝 Windows PowerShell Web 存取時，會在安裝處理程序期間自動新增必要的角色和功能。</span><span class="sxs-lookup"><span data-stu-id="21d40-132">When you install Windows PowerShell Web Access by using Server Manager or its deployment cmdlets, required roles and features are automatically added as part of the installation process.</span></span>

<span data-ttu-id="21d40-133">Windows PowerShell Web 存取允許遠端使用者，在網頁瀏覽器中使用 Windows PowerShell 來存取組織中的電腦。</span><span class="sxs-lookup"><span data-stu-id="21d40-133">Windows PowerShell Web Access allows remote users to access computers in your organization by using Windows PowerShell in a web browser.</span></span> <span data-ttu-id="21d40-134">雖然 Windows PowerShell Web 存取是一個方便且功能強大的管理工具，但網頁型存取有安全性風險，應該儘可能安全地設定。</span><span class="sxs-lookup"><span data-stu-id="21d40-134">Although Windows PowerShell Web Access is a convenient and powerful management tool, the web-based access poses security risks, and should be configured as securely as possible.</span></span> <span data-ttu-id="21d40-135">建議設定 Windows PowerShell Web 存取閘道的系統管理員使用可用的安全性階層，包含 Windows PowerShell Web 存取隨附之以 Cmdlet為基礎的授權規則，以及網頁伺服器 (IIS) 與協力廠商應用程式中可用的安全性階層。</span><span class="sxs-lookup"><span data-stu-id="21d40-135">We recommend that administrators who configure the Windows PowerShell Web Access gateway use available security layers, both the cmdlet-based authorization rules included with Windows PowerShell Web Access, and security layers that are available in Web Server (IIS) and third-party applications.</span></span> <span data-ttu-id="21d40-136">這份文件含有只建議用於測試環境的不安全範例，以及建議用於安全部署的範例。</span><span class="sxs-lookup"><span data-stu-id="21d40-136">This documentation includes both unsecure examples that are only recommended for test environments, as well as examples that are recommended for secure deployments.</span></span>

<a href="" id="BKMK_browser"></a>

<span data-ttu-id="21d40-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">瀏覽器及用戶端裝置支援</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="21d40-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser and client device support</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="21d40-138">Windows PowerShell Web 存取支援下列網際網路瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="21d40-138">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="21d40-139">雖然並未正式支援行動瀏覽器，但很多行動瀏覽器應該都可以執行網頁型 Windows PowerShell 主控台。</span><span class="sxs-lookup"><span data-stu-id="21d40-139">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="21d40-140">其他接受 Cookie、執行 JavaScript 以及執行 HTTPS 網站的瀏覽器預期也可以運作，但尚未經過正式測試。</span><span class="sxs-lookup"><span data-stu-id="21d40-140">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="21d40-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">支援的桌上型電腦瀏覽器</span></a></span><span class="sxs-lookup"><span data-stu-id="21d40-141"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="21d40-142">適用於 Microsoft Windows® 8.0、9.0、10.0 以及 11.0 的 Windows® Internet Explorer®</span><span class="sxs-lookup"><span data-stu-id="21d40-142">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="21d40-143">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="21d40-143">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="21d40-144">適用於 Windows 的 Google Chrome™ 17.0.963.56m</span><span class="sxs-lookup"><span data-stu-id="21d40-144">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="21d40-145">適用於 Windows 的 Apple Safari® 5.1.2</span><span class="sxs-lookup"><span data-stu-id="21d40-145">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="21d40-146">適用於 Mac OS® 的 Apple Safari 5.1.2</span><span class="sxs-lookup"><span data-stu-id="21d40-146">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="21d40-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">通過基本測試的行動裝置或瀏覽器</span></a></span><span class="sxs-lookup"><span data-stu-id="21d40-147"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="21d40-148">Windows Phone 7 和 7.5</span><span class="sxs-lookup"><span data-stu-id="21d40-148">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="21d40-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="21d40-149">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="21d40-150">適用於 iPhone 作業系統 5.0.1 的 Apple Safari</span><span class="sxs-lookup"><span data-stu-id="21d40-150">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="21d40-151">適用於 iPad 2 作業系統 5.0.1 的 Apple Safari</span><span class="sxs-lookup"><span data-stu-id="21d40-151">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="21d40-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">瀏覽器需求</span></a></span><span class="sxs-lookup"><span data-stu-id="21d40-152"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="21d40-153">若要使用 Windows PowerShell Web 存取網頁型主控台，瀏覽器必須執行下列作業。</span><span class="sxs-lookup"><span data-stu-id="21d40-153">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="21d40-154">允許來自 Windows PowerShell Web 存取閘道網站的 Cookie。</span><span class="sxs-lookup"><span data-stu-id="21d40-154">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="21d40-155">可以開啟和讀取 HTTPS 頁面。</span><span class="sxs-lookup"><span data-stu-id="21d40-155">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="21d40-156">開啟和執行使用 JavaScript 的網站。</span><span class="sxs-lookup"><span data-stu-id="21d40-156">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_recm"></a>

<span data-ttu-id="21d40-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">建議 (快速) 部署</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="21d40-157"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="21d40-158">您可以使用 Windows PowerShell 部署 Cmdlet 或從伺服器管理員中開啟的 [新增角色及功能精靈]，在執行 Windows Server 2012 R2 或 Windows Server 2012 的伺服器上安裝 Windows PowerShell Web 存取閘道。</span><span class="sxs-lookup"><span data-stu-id="21d40-158">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using either Windows PowerShell cmdlets, or by using the Add Roles and Features Wizard that is opened from within Server Manager.</span></span> <span data-ttu-id="21d40-159">若要快速安裝和設定，請使用 Windows PowerShell Cmdlet，如本節所述。</span><span class="sxs-lookup"><span data-stu-id="21d40-159">For quick installation and configuration, use Windows PowerShell cmdlets, as described in this section.</span></span>

-   [<span data-ttu-id="21d40-160">步驟 1：安裝 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="21d40-160">Step 1: Install Windows PowerShell Web Access</span></span>](#BKMK_step1)

-   [<span data-ttu-id="21d40-161">步驟 2：設定閘道</span><span class="sxs-lookup"><span data-stu-id="21d40-161">Step 2: Configure the gateway</span></span>](#BKMK_step2)

-   [<span data-ttu-id="21d40-162">步驟 3：設定限制性授權規則</span><span class="sxs-lookup"><span data-stu-id="21d40-162">Step 3: Configure a restrictive authorization rule</span></span>](#BKMK_step3)

<a href="" id="BKMK_step1"></a>
###

<span data-ttu-id="21d40-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 1：安裝 Windows PowerShell Web 存取</span></a></span><span class="sxs-lookup"><span data-stu-id="21d40-163"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="21d40-164">使用 Windows PowerShell Cmdlet 安裝 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="21d40-164">To install Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="21d40-165">執行下列其中一個動作，使用提高的使用者權限開啟 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="21d40-165">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="21d40-166">在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-166">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="21d40-167">在 Windows **[開始]** 畫面上，以滑鼠右鍵按一下 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-167">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="21d40-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></span><span class="sxs-lookup"><span data-stu-id="21d40-168"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="21d40-169">在 Windows PowerShell 3.0 和 4.0 中，執行屬於模組的 Cmdlet 之前，不需要將伺服器管理員 Cmdlet 模組匯入 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="21d40-169">In Windows PowerShell 3.0 and 4.0, there is no need to import the Server Manager cmdlet module into the Windows PowerShell session before running cmdlets that are part of the module.</span></span> <span data-ttu-id="21d40-170">當您首次執行屬於模組的 Cmdlet 時，會自動匯入模組。</span><span class="sxs-lookup"><span data-stu-id="21d40-170">A module is automatically imported the first time you run a cmdlet that is part of the module.</span></span> <span data-ttu-id="21d40-171">此外，Windows PowerShell Cmdlet 不會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="21d40-171">Also, Windows PowerShell cmdlets are not case-sensitive.</span></span></p></td>
    </tr>
    </tbody>
    </table>

2.  <span data-ttu-id="21d40-172">輸入下列內容，然後按 **Enter**，其中 *computer_name* 代表要安裝 Windows PowerShell Web 存取的遠端電腦 (如果適用)。</span><span class="sxs-lookup"><span data-stu-id="21d40-172">Type the following, and then press **Enter**, where *computer_name* represents a remote computer on which you want to install Windows PowerShell Web Access, if applicable.</span></span> <span data-ttu-id="21d40-173">如有需要，<span class="code">Restart</span> 參數會自動重新啟動目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="21d40-173">The <span class="code">Restart</span> parameter automatically restarts destination servers if required.</span></span>

    [<span data-ttu-id="21d40-174">Copy</span><span class="sxs-lookup"><span data-stu-id="21d40-174">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_374a9c21-4f6e-471e-b957-bb190a594533'); "複製到剪貼簿。")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="21d40-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></span><span class="sxs-lookup"><span data-stu-id="21d40-175"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="21d40-176">使用 Windows PowerShell Cmdlet 安裝 Windows PowerShell Web 存取，預設不會新增網頁伺服器 (IIS) 管理工具。</span><span class="sxs-lookup"><span data-stu-id="21d40-176">Installing Windows PowerShell Web Access by using Windows PowerShell cmdlets does not add Web Server (IIS) management tools by default.</span></span> <span data-ttu-id="21d40-177">如果您想要在與 Windows PowerShell Web 存取閘道相同的伺服器上安裝管理工具，可將 <span class="code">IncludeManagementTools</span> 參數新增到安裝命令 (如本步驟所提供)。</span><span class="sxs-lookup"><span data-stu-id="21d40-177">If you want to install the management tools on the same server as the Windows PowerShell Web Access gateway, add the <span class="code">IncludeManagementTools</span> parameter to the installation command (as provided in this step).</span></span> <span data-ttu-id="21d40-178">如果您從遠端電腦管理 Windows PowerShell Web 存取網站，在您要用來管理閘道的電腦上，透過安裝 <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Windows 8.1 的遠端伺服器管理工具</a>或 <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Windows 8 的遠端伺服器管理工具</a>來安裝 [IIS 管理員] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="21d40-178">If you are managing the Windows PowerShell Web Access website from a remote computer, install the IIS Manager snap-in by installing <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Remote Server Administration Tools for Windows 8.1</a> or <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Remote Server Administration Tools for Windows 8</a> on the computer from which you want to manage the gateway.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="21d40-179">若要在離線 VHD 上安裝角色和功能，您必須新增 <span class="code">ComputerName</span> 參數及 <span class="code">VHD</span> 參數。</span><span class="sxs-lookup"><span data-stu-id="21d40-179">To install roles and features on an offline VHD, you must add both the <span class="code">ComputerName</span> parameter and the <span class="code">VHD</span> parameter.</span></span> <span data-ttu-id="21d40-180"><span class="code">ComputerName</span> 參數包含要掛接 VHD 的伺服器名稱，<span class="code">VHD</span> 參數則包含指定伺服器上的 VHD 檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="21d40-180">The <span class="code">ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="21d40-181">Copy</span><span class="sxs-lookup"><span data-stu-id="21d40-181">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_d841d509-347e-49d0-bf54-8d1f306bece6'); "複製到剪貼簿。")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart

3.  <span data-ttu-id="21d40-182">完成安裝後，在使用提高的使用者權限開啟的 Windows PowerShell 主控台中，藉由在目的地伺服器上執行 **Get-WindowsFeature** Cmdlet，來確認 Windows PowerShell Web 存取已安裝於目的地伺服器上。</span><span class="sxs-lookup"><span data-stu-id="21d40-182">When installation is complete, verify that Windows PowerShell Web Access was installed on destination servers by running the **Get-WindowsFeature** cmdlet on a destination server, in a Windows PowerShell console that has been opened with elevated user rights.</span></span> <span data-ttu-id="21d40-183">您也可以在 [所有伺服器] 頁面上選取目的地伺服器，然後檢視所選伺服器的 [角色和功能] 磚，藉以確認 Windows PowerShell Web 存取已安裝於伺服器管理員主控台中。</span><span class="sxs-lookup"><span data-stu-id="21d40-183">You can also verify that Windows PowerShell Web Access was installed in the Server Manager console, by selecting a destination server on the **All Servers** page, and then viewing the **Roles and Features** tile for the selected server.</span></span> <span data-ttu-id="21d40-184">您也可以檢視 Windows PowerShell Web 存取的讀我檔案。</span><span class="sxs-lookup"><span data-stu-id="21d40-184">You can also view the readme file for Windows PowerShell Web Access.</span></span>

4.  <span data-ttu-id="21d40-185">安裝 Windows PowerShell Web 存取之後，系統會提示您檢閱讀我檔案，其中包含適用於閘道的必要且基本的安裝指示。</span><span class="sxs-lookup"><span data-stu-id="21d40-185">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="21d40-186">[步驟 2：設定閘道](#BKMK_step2)一節中也會有這些安裝指示。</span><span class="sxs-lookup"><span data-stu-id="21d40-186">These setup instructions are also in the following section, [Step 2: Configure the gateway](#BKMK_step2).</span></span> <span data-ttu-id="21d40-187">讀我檔案的路徑是 <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>。</span><span class="sxs-lookup"><span data-stu-id="21d40-187">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

<a href="" id="BKMK_step2"></a>
###

<span data-ttu-id="21d40-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 2：設定閘道</span></a></span><span class="sxs-lookup"><span data-stu-id="21d40-188"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="21d40-189">**Install-PswaWebApplication** Cmdlet 是快速設定 Windows PowerShell Web 存取的方法。</span><span class="sxs-lookup"><span data-stu-id="21d40-189">The **Install-PswaWebApplication** cmdlet is a quick way to get Windows PowerShell Web Access configured.</span></span> <span data-ttu-id="21d40-190">雖然您可以基於測試目的將 <span class="code">UseTestCertificate</span> 參數新增到 <span class="code">Install-PswaWebApplication</span> Cmdlet 來安裝自我簽署的 SSL 憑證，但這並不安全；為了擁有安全的生產環境，一定要使用由憑證授權單位 (CA) 簽署的有效 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="21d40-190">Although you can add the <span class="code">UseTestCertificate</span> parameter to the <span class="code">Install-PswaWebApplication</span> cmdlet to install a self-signed SSL certificate for test purposes, this is not secure; for a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="21d40-191">系統管理員可以使用 IIS 管理員主控台以選擇的簽署憑證來取代測試憑證。</span><span class="sxs-lookup"><span data-stu-id="21d40-191">Administrators can replace the test certificate with a signed certificate of their choice by using the IIS Manager console.</span></span>

<span data-ttu-id="21d40-192">您可以執行 <span class="code">Install-PswaWebApplication</span> Cmdlet 或在 IIS 管理員中執行 GUI 設定步驟，來完成 Windows PowerShell Web 存取 Web 應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="21d40-192">You can complete Windows PowerShell Web Access web application configuration either by running the <span class="code">Install-PswaWebApplication</span> cmdlet or by performing GUI-based configuration steps in IIS Manager.</span></span> <span data-ttu-id="21d40-193">根據預設，Cmdlet 會在 [IIS 管理員] 上顯示的 [預設的網站] 容器中，安裝 Web 應用程式 **pswa** (以及應用程式集區 **pswa_pool**)；如有需要，可以指示 Cmdlet 變更 Web 應用程式的預設網站容器。</span><span class="sxs-lookup"><span data-stu-id="21d40-193">By default, the cmdlet installs the web application, **pswa** (and an application pool for it, **pswa_pool**), in the **Default Web Site** container, as shown in IIS Manager; if desired, you can instruct the cmdlet to change the default site container of the web application.</span></span> <span data-ttu-id="21d40-194">IIS 管理員提供 Web 應用程式可用的設定選項，例如變更連接埠號碼或安全通訊端層 (SSL) 憑證。</span><span class="sxs-lookup"><span data-stu-id="21d40-194">IIS Manager offers configuration options that are available for web applications, such as changing the port number or the Secure Sockets Layer (SSL) certificate.</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="21d40-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 安全性注意事項 </span></span><span class="sxs-lookup"><span data-stu-id="21d40-195"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="21d40-196">強烈建議系統管理員將閘道設定為使用 CA 簽署的有效憑證。</span><span class="sxs-lookup"><span data-stu-id="21d40-196">We strongly recommend that administrators configure the gateway to use a valid certificate that has been signed by a CA.</span></span></p></td>
</tr>
</tbody>
</table>

-   [<span data-ttu-id="21d40-197">使用 Install-PswaWebApplication 以測試憑證設定 Windows PowerShell Web 存取閘道</span><span class="sxs-lookup"><span data-stu-id="21d40-197">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>](#BKMK_testcert)

-   [<span data-ttu-id="21d40-198">使用 Install-PswaWebApplication 和 IIS 管理員以正版憑證設定 Windows PowerShell Web 存取閘道</span><span class="sxs-lookup"><span data-stu-id="21d40-198">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>](#BKMK_gencert)

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a><span data-ttu-id="21d40-199">使用 Install-PswaWebApplication 以測試憑證設定 Windows PowerShell Web 存取閘道</span><span class="sxs-lookup"><span data-stu-id="21d40-199">To configure the Windows PowerShell Web Access gateway with a test certificate by using Install-PswaWebApplication</span></span>

1.  <span data-ttu-id="21d40-200">執行下列其中一個動作來開啟 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="21d40-200">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="21d40-201">在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 [Windows PowerShell]。</span><span class="sxs-lookup"><span data-stu-id="21d40-201">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="21d40-202">在 Windows **[開始]** 畫面上，按一下 **[Windows PowerShell]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-202">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="21d40-203">輸入下列程式碼，然後按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="21d40-203">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="21d40-204">**Install-PswaWebApplication -UseTestCertificate**</span><span class="sxs-lookup"><span data-stu-id="21d40-204">**Install-PswaWebApplication -UseTestCertificate**</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="21d40-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 安全性注意事項 </span></span><span class="sxs-lookup"><span data-stu-id="21d40-205"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="21d40-206"><span class="code">UseTestCertificate</span> 參數只能用於私人測試環境中。</span><span class="sxs-lookup"><span data-stu-id="21d40-206">The <span class="code">UseTestCertificate</span> parameter should only be used in a private test environment.</span></span> <span data-ttu-id="21d40-207">若要安全的生產環境，建議使用 CA 簽署的有效憑證。</span><span class="sxs-lookup"><span data-stu-id="21d40-207">For a secure production environment, we recommend using a valid certificate that has been signed by a CA.</span></span></p></td>
    </tr>
    </tbody>
    </table>

    <span data-ttu-id="21d40-208">執行這個 Cmdlet 會在 IIS [預設的網站] 容器中安裝 Windows PowerShell Web 存取 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="21d40-208">Running the cmdlet installs the Windows PowerShell Web Access web application within the IIS Default Web Site container.</span></span> <span data-ttu-id="21d40-209">這個 Cmdlet 會建立在預設網站 (https://&lt;server_name&gt;/pswa) 上執行 Windows PowerShell Web 存取所需的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="21d40-209">The cmdlet creates the infrastructure required to run Windows PowerShell Web Access on the default website, https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="21d40-210">若要在不同的網站上安裝 Web 應用程式，新增 <span class="code">WebSiteName</span> 參數來提供網站名稱。</span><span class="sxs-lookup"><span data-stu-id="21d40-210">To install the web application in a different website, provide the website name by adding the <span class="code">WebSiteName</span> parameter.</span></span> <span data-ttu-id="21d40-211">若要變更 Web 應用程式的名稱 (預設是 <span class="code">pswa</span>)，新增 <span class="code">WebApplicationName</span> 參數。</span><span class="sxs-lookup"><span data-stu-id="21d40-211">To change the name of the web application (the default is <span class="code">pswa</span>), add the <span class="code">WebApplicationName</span> parameter.</span></span>

    <span data-ttu-id="21d40-212">執行 Cmdlet 可以設定下列設定。</span><span class="sxs-lookup"><span data-stu-id="21d40-212">The following settings are configured by running the cmdlet.</span></span> <span data-ttu-id="21d40-213">如有需要，可以在 IIS 管理員主控台手動變更這些設定。</span><span class="sxs-lookup"><span data-stu-id="21d40-213">You can change these manually in the IIS Manager console, if desired.</span></span>

    -   <span data-ttu-id="21d40-214">Path：/pswa</span><span class="sxs-lookup"><span data-stu-id="21d40-214">Path: /pswa</span></span>

    -   <span data-ttu-id="21d40-215">ApplicationPool：pswa_pool</span><span class="sxs-lookup"><span data-stu-id="21d40-215">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="21d40-216">EnabledProtocols：http</span><span class="sxs-lookup"><span data-stu-id="21d40-216">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="21d40-217">PhysicalPath：%*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="21d40-217">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

    <span data-ttu-id="21d40-218"><span class="label">範例︰</span><span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span><span class="sxs-lookup"><span data-stu-id="21d40-218"><span class="label">Example:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span></span></span>

    <span data-ttu-id="21d40-219">在這個範例中，針對 Windows PowerShell Web 存取產生的網站是 https://&lt; *server_name*&gt;/myWebApp。</span><span class="sxs-lookup"><span data-stu-id="21d40-219">In this example, the resulting website for Windows PowerShell Web Access is https://&lt; *server_name*&gt;/myWebApp.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="21d40-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></span><span class="sxs-lookup"><span data-stu-id="21d40-220"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="21d40-221">必須透過新增授權規則，讓使用者獲得網站存取權，才能進行登入。</span><span class="sxs-lookup"><span data-stu-id="21d40-221">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="21d40-222">如需詳細資訊，請參閱<a href="#BKMK_step3">步驟 3：設定限制性授權規則</a>和 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell Web 存取的授權規則與安全性功能</a>。</span><span class="sxs-lookup"><span data-stu-id="21d40-222">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a><span data-ttu-id="21d40-223">使用 Install-PswaWebApplication 和 IIS 管理員以正版憑證設定 Windows PowerShell Web 存取閘道</span><span class="sxs-lookup"><span data-stu-id="21d40-223">To configure the Windows PowerShell Web Access gateway with a genuine certificate by using Install-PswaWebApplication and IIS Manager</span></span>

1.  <span data-ttu-id="21d40-224">執行下列其中一個動作來開啟 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="21d40-224">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="21d40-225">在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 [Windows PowerShell]。</span><span class="sxs-lookup"><span data-stu-id="21d40-225">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="21d40-226">在 Windows **[開始]** 畫面上，按一下 **[Windows PowerShell]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-226">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="21d40-227">輸入下列程式碼，然後按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="21d40-227">Type the following, and then press **Enter**.</span></span>

    <span data-ttu-id="21d40-228">**Install-PswaWebApplication**</span><span class="sxs-lookup"><span data-stu-id="21d40-228">**Install-PswaWebApplication**</span></span>

    <span data-ttu-id="21d40-229">執行 Cmdlet 可以設定下列閘道設定。</span><span class="sxs-lookup"><span data-stu-id="21d40-229">The following gateway settings are configured by running the cmdlet.</span></span> <span data-ttu-id="21d40-230">如有需要，可以在 IIS 管理員主控台手動變更這些設定。</span><span class="sxs-lookup"><span data-stu-id="21d40-230">You can change these manually in the IIS Manager console, if desired.</span></span> <span data-ttu-id="21d40-231">您也可以針對 <span class="code">Install-PswaWebApplication</span> Cmdlet 的 <span class="code">WebsiteName</span> 和 <span class="code">WebApplicationName</span> 參數指定值。</span><span class="sxs-lookup"><span data-stu-id="21d40-231">You can also specify values for the <span class="code">WebsiteName</span> and <span class="code">WebApplicationName</span> parameters of the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span>

    -   <span data-ttu-id="21d40-232">Path：/pswa</span><span class="sxs-lookup"><span data-stu-id="21d40-232">Path: /pswa</span></span>

    -   <span data-ttu-id="21d40-233">ApplicationPool：pswa_pool</span><span class="sxs-lookup"><span data-stu-id="21d40-233">ApplicationPool: pswa_pool</span></span>

    -   <span data-ttu-id="21d40-234">EnabledProtocols：http</span><span class="sxs-lookup"><span data-stu-id="21d40-234">EnabledProtocols: http</span></span>

    -   <span data-ttu-id="21d40-235">PhysicalPath：%*windir*%/Web/PowerShellWebAccess/wwwroot</span><span class="sxs-lookup"><span data-stu-id="21d40-235">PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot</span></span>

3.  <span data-ttu-id="21d40-236">執行下列其中一項動作以開啟 IIS 管理員主控台。</span><span class="sxs-lookup"><span data-stu-id="21d40-236">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="21d40-237">在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。</span><span class="sxs-lookup"><span data-stu-id="21d40-237">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="21d40-238">在 [伺服器管理員] 的 **[工具]** 功能表上，按一下 **[Internet Information Services (IIS) 管理員]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-238">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="21d40-239">在 Windows **[開始]** 畫面上，按一下 **[伺服器管理員]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-239">On the Windows **Start** screen, click **Server Manager**.</span></span>

4.  <span data-ttu-id="21d40-240">在 [IIS 管理員] 樹狀目錄窗格中，展開安裝 Windows PowerShell Web 存取的伺服器節點，直到可以看到 [站台] 資料夾為止。</span><span class="sxs-lookup"><span data-stu-id="21d40-240">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="21d40-241">展開 [站台] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="21d40-241">Expand the **Sites** folder.</span></span>

5.  <span data-ttu-id="21d40-242">選取您已安裝 Windows PowerShell Web 存取 Web 應用程式的網站。</span><span class="sxs-lookup"><span data-stu-id="21d40-242">Select the website in which you have installed the Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="21d40-243">在 **[動作]** 窗格中，按一下 **[繫結]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-243">In the **Actions** pane, click **Bindings**.</span></span>

6.  <span data-ttu-id="21d40-244">在 **[站台繫結]** 對話方塊中，按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-244">In the **Site Binding** dialog box, click **Add**.</span></span>

7.  <span data-ttu-id="21d40-245">在 **[新增站台繫結]** 對話方塊的 **[類型]** 欄位中選取 **[https]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-245">In the **Add Site Binding** dialog box, in the **Type** field, select **https**.</span></span>

8.  <span data-ttu-id="21d40-246">在 [SSL 憑證] 欄位中，從下拉式功能表中選取您已簽署的憑證。</span><span class="sxs-lookup"><span data-stu-id="21d40-246">In the **SSL certificate** field, select your signed certificate from the drop-down menu.</span></span> <span data-ttu-id="21d40-247">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-247">Click **OK**.</span></span> <span data-ttu-id="21d40-248">如需如何取得憑證的詳細資訊，請參閱本主題中的[在 IIS 管理員設定 SSL 憑證](#BKMK_cert)。</span><span class="sxs-lookup"><span data-stu-id="21d40-248">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

    <span data-ttu-id="21d40-249">現在 Windows PowerShell Web 存取 Web 應用程式已設定為使用您已簽署的 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="21d40-249">The Windows PowerShell Web Access web application is now configured to use your signed SSL certificate.</span></span> <span data-ttu-id="21d40-250">您可以在瀏覽器視窗中開啟 https://&lt;server_name&gt;/pswa，來存取 Windows PowerShell Web 存取。</span><span class="sxs-lookup"><span data-stu-id="21d40-250">You can access Windows PowerShell Web Access by opening https://&lt;server_name&gt;/pswa in a browser window.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="21d40-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></span><span class="sxs-lookup"><span data-stu-id="21d40-251"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="21d40-252">必須透過新增授權規則，讓使用者獲得網站存取權，才能進行登入。</span><span class="sxs-lookup"><span data-stu-id="21d40-252">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span> <span data-ttu-id="21d40-253">如需詳細資訊，請參閱<a href="#BKMK_step3">步驟 3：設定限制性授權規則</a>和 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell Web 存取的授權規則與安全性功能</a>。</span><span class="sxs-lookup"><span data-stu-id="21d40-253">For more information, see <a href="#BKMK_step3">Step 3: Configure a restrictive authorization rule</a> and <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table><span data-ttu-id="21d40-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 3：設定限制性授權規則</span></a></span><span class="sxs-lookup"><span data-stu-id="21d40-254">

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="21d40-255">安裝 Windows PowerShell Web 存取並設定閘道之後，使用者就可以在瀏覽器中開啟登入頁面，但是必須等到 Windows PowerShell Web 存取系統管理員明確授與使用者存取權之後，才能登入。</span><span class="sxs-lookup"><span data-stu-id="21d40-255">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="21d40-256">您可以使用下表所述的 Windows PowerShell Cmdlet，來管理 Windows PowerShell Web 存取存取控制。</span><span class="sxs-lookup"><span data-stu-id="21d40-256">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="21d40-257">沒有適用於新增或管理授權規則的 GUI。</span><span class="sxs-lookup"><span data-stu-id="21d40-257">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="21d40-258">如需 Windows PowerShell Web 存取 Cmdlet 的詳細資訊，請參閱 Cmdlet 參考主題：[Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx) (Windows PowerShell Web 存取 Cmdlet)。</span><span class="sxs-lookup"><span data-stu-id="21d40-258">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="21d40-259">如需 Windows PowerShell Web 存取授權規則和安全性的詳細資訊，請參閱 [Windows PowerShell Web 存取的授權規則與安全性功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)。</span><span class="sxs-lookup"><span data-stu-id="21d40-259">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="21d40-260">新增限制性授權規則</span><span class="sxs-lookup"><span data-stu-id="21d40-260">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="21d40-261">執行下列其中一個動作，使用提高的使用者權限開啟 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="21d40-261">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="21d40-262">在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-262">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="21d40-263">在 Windows **[開始]** 畫面上，以滑鼠右鍵按一下 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-263">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="21d40-264"><span class="label">使用工作階段設定來限制使用者存取的選擇性步驟：</span>確認您要在規則中使用的工作階段設定已經存在。</span><span class="sxs-lookup"><span data-stu-id="21d40-264"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="21d40-265">如果尚未建立這些設定，請使用 MSDN 上 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) 中建立工作階段設定的指示。</span><span class="sxs-lookup"><span data-stu-id="21d40-265">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="21d40-266">輸入下列程式碼，然後按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="21d40-266">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="21d40-267">Copy</span><span class="sxs-lookup"><span data-stu-id="21d40-267">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_f9e7959b-75d0-4d63-8f8e-02334a8dd09d'); "複製到剪貼簿。")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="21d40-268">這個授權規則允許特定使用者存取網路上他們通常有權存取的一部電腦，以及該使用者在一般編寫指令碼及 Cmdlet 範圍內的特定工作階段設定存取權。</span><span class="sxs-lookup"><span data-stu-id="21d40-268">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="21d40-269">在下列範例中，<span class="code">Contoso</span> 網域中名為 <span class="code">JSmith</span> 的使用者會被授與管理電腦 <span class="code">Contoso_214</span> 的存取權，並使用名為 <span class="code">NewAdminsOnly</span> 的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="21d40-269">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="21d40-270">Copy</span><span class="sxs-lookup"><span data-stu-id="21d40-270">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ebd5bc5e-ec5d-4955-a86a-63843e480e37'); "複製到剪貼簿。")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="21d40-271">執行 **Get-PswaAuthorizationRule** Cmdlet 或 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;，確認已建立規則。</span><span class="sxs-lookup"><span data-stu-id="21d40-271">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="21d40-272">例如，**Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**。</span><span class="sxs-lookup"><span data-stu-id="21d40-272">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="21d40-273">設定授權規則之後，授權使用者就可以開始登入網頁型主控台，並開始使用 Windows PowerShell Web 存取。</span><span class="sxs-lookup"><span data-stu-id="21d40-273">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_custom"></a>

<span data-ttu-id="21d40-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">自訂部署</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="21d40-274"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom deployment</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="21d40-275">您可以使用伺服器管理員中的 [新增角色及功能精靈]，在執行 Windows Server 2012 R2 或 Windows Server 2012 的伺服器上安裝 Windows PowerShell Web 存取閘道。</span><span class="sxs-lookup"><span data-stu-id="21d40-275">You can install the Windows PowerShell Web Access gateway on a server that is running Windows Server 2012 R2 or Windows Server 2012 by using the Add Roles and Features Wizard in Server Manager.</span></span> <span data-ttu-id="21d40-276">安裝 Windows PowerShell Web 存取之後，您可以在 IIS 管理員中自訂閘道的設定。</span><span class="sxs-lookup"><span data-stu-id="21d40-276">After Windows PowerShell Web Access is installed, you can customize the configuration of the gateway in IIS Manager.</span></span>

<a href="" id="BKMK_custom1"></a>
###

<span data-ttu-id="21d40-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 1：安裝 Windows PowerShell Web 存取</span></a></span><span class="sxs-lookup"><span data-stu-id="21d40-277"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Install Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a><span data-ttu-id="21d40-278">使用新增角色及功能精靈安裝 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="21d40-278">To install Windows PowerShell Web Access by using the Add Roles and Features Wizard</span></span>

1.  <span data-ttu-id="21d40-279">如果已經開啟伺服器管理員，請移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="21d40-279">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="21d40-280">如果尚未開啟伺服器管理員，請執行下列其中一項動作來將它開啟。</span><span class="sxs-lookup"><span data-stu-id="21d40-280">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="21d40-281">在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。</span><span class="sxs-lookup"><span data-stu-id="21d40-281">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="21d40-282">在 Windows **[開始]** 畫面上，按一下 **[伺服器管理員]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-282">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="21d40-283">在 **[管理]** 功能表上，按一下 **[新增角色及功能]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-283">On the **Manage** menu, click **Add Roles and Features**.</span></span>

3.  <span data-ttu-id="21d40-284">在 [選取安裝類型] 頁面上，選取 [角色型或功能型安裝]。</span><span class="sxs-lookup"><span data-stu-id="21d40-284">On the **Select installation type** page, select **Role-based or feature-based installation**.</span></span> <span data-ttu-id="21d40-285">按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-285">Click **Next**.</span></span>

4.  <span data-ttu-id="21d40-286">在 [選取目的地伺服器] 頁面上，從伺服器集區選取伺服器，或選取離線 VHD。</span><span class="sxs-lookup"><span data-stu-id="21d40-286">On the **Select destination server** page, select a server from the server pool, or select an offline VHD.</span></span> <span data-ttu-id="21d40-287">若要選取離線 VHD 做為目的地伺服器，請先選取要掛接 VHD 的伺服器，然後選取 VHD 檔案。</span><span class="sxs-lookup"><span data-stu-id="21d40-287">To select an offline VHD as your destination server, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="21d40-288">如需如何將伺服器新增到伺服器集區的相關資訊，請參閱伺服器管理員說明。</span><span class="sxs-lookup"><span data-stu-id="21d40-288">For information about how to add servers to your server pool, see the Server Manager Help.</span></span> <span data-ttu-id="21d40-289">選取目的地伺服器之後，按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-289">After you have selected the destination server, click **Next**.</span></span>

5.  <span data-ttu-id="21d40-290">在精靈的 **[選取功能]** 頁面上，展開 **[Windows PowerShell]**，然後選取 **[Windows PowerShell Web 存取]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-290">On the **Select features** page of the wizard, expand **Windows PowerShell**, and then select **Windows PowerShell Web Access**.</span></span>

6.  <span data-ttu-id="21d40-291">請注意，系統會提示您新增必要的功能，例如 .NET Framework 4.5 以及網頁伺服器 (IIS) 的角色服務。</span><span class="sxs-lookup"><span data-stu-id="21d40-291">Note that you are prompted to add required features, such as .NET Framework 4.5, and role services of Web Server (IIS).</span></span> <span data-ttu-id="21d40-292">新增必要的功能，然後繼續。</span><span class="sxs-lookup"><span data-stu-id="21d40-292">Add required features and continue.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="21d40-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></span><span class="sxs-lookup"><span data-stu-id="21d40-293"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="21d40-294">使用 [新增角色及功能精靈] 安裝 Windows PowerShell Web 存取，也會安裝網頁伺服器 (IIS)，包括 [IIS 管理員] 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="21d40-294">Installing Windows PowerShell Web Access by using the Add Roles and Features Wizard also installs Web Server (IIS), including the IIS Manager snap-in.</span></span> <span data-ttu-id="21d40-295">如果您使用 [新增角色及功能精靈]，預設會安裝嵌入式管理單元及其他 IIS 管理工具。</span><span class="sxs-lookup"><span data-stu-id="21d40-295">The snap-in and other IIS management tools are installed by default if you use Add Roles and Features Wizard.</span></span> <span data-ttu-id="21d40-296">如果您依下列程序中所述方式使用 Windows PowerShell Cmdlet 安裝 Windows PowerShell Web 存取，預設不會新增管理工具。</span><span class="sxs-lookup"><span data-stu-id="21d40-296">If you install Windows PowerShell Web Access by using Windows PowerShell cmdlets as described in the following procedure, management tools are not added by default.</span></span></p></td>
    </tr>
    </tbody>
    </table>

7.  <span data-ttu-id="21d40-297">如果 Windows PowerShell Web 存取的功能檔案未儲存於您在步驟 4 選取的目的地伺服器上，可在 [確認安裝選項] 頁面上按一下 [指定替代來源路徑]，然後提供功能檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="21d40-297">On the **Confirm installation selections** page, if the feature files for Windows PowerShell Web Access are not stored on the destination server that you selected in step 4, click **Specify an alternate source path**, and provide the path to the feature files.</span></span> <span data-ttu-id="21d40-298">否則，按一下 **[安裝]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-298">Otherwise, click **Install**.</span></span>

8.  <span data-ttu-id="21d40-299">按一下 [安裝] 之後，[安裝進度] 頁面就會顯示安裝進度、結果及訊息，例如警告、失敗或 Windows PowerShell Web 存取所需的後續安裝設定步驟。</span><span class="sxs-lookup"><span data-stu-id="21d40-299">After you click **Install**, the **Installation progress** page displays installation progress, results, and messages such as warnings, failures, or post-installation configuration steps that are required for Windows PowerShell Web Access.</span></span> <span data-ttu-id="21d40-300">安裝 Windows PowerShell Web 存取之後，系統會提示您檢閱讀我檔案，其中包含適用於閘道的必要且基本的安裝指示。</span><span class="sxs-lookup"><span data-stu-id="21d40-300">After Windows PowerShell Web Access is installed, you are prompted to review the readme file, which contains basic, required setup instructions for the gateway.</span></span> <span data-ttu-id="21d40-301">本主題中也包含這些指示。</span><span class="sxs-lookup"><span data-stu-id="21d40-301">These instructions are also included in this topic.</span></span> <span data-ttu-id="21d40-302">讀我檔案的路徑是 <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>。</span><span class="sxs-lookup"><span data-stu-id="21d40-302">The path to the readme file is <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.</span></span>

###

<span data-ttu-id="21d40-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 2：設定閘道</span></a></span><span class="sxs-lookup"><span data-stu-id="21d40-303"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Configure the gateway</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="21d40-304">本節的指示適用於在網站的子目錄 (不是根目錄) 中安裝 Windows PowerShell Web 存取 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="21d40-304">Instructions in this section are for installing the Windows PowerShell Web Access web application in a subdirectory—and not in the root directory—of your website.</span></span> <span data-ttu-id="21d40-305">這個程序是等同於 <span class="code">Install-PswaWebApplication</span> Cmdlet 所執行之動作的 GUI 動作。</span><span class="sxs-lookup"><span data-stu-id="21d40-305">This procedure is the GUI-based equivalent of the actions performed by the <span class="code">Install-PswaWebApplication</span> cmdlet.</span></span> <span data-ttu-id="21d40-306">本節還包含如何使用 IIS 管理員，將 Windows PowerShell Web 存取閘道設定為根網站的指示。</span><span class="sxs-lookup"><span data-stu-id="21d40-306">This section also includes instructions for how to use IIS Manager to configure the Windows PowerShell Web Access gateway as a root website.</span></span>

-   [<span data-ttu-id="21d40-307">使用 IIS 管理員在現有的網站中設定閘道</span><span class="sxs-lookup"><span data-stu-id="21d40-307">To use IIS Manager to configure the gateway in an existing website</span></span>](#BKMK_configman)

-   [<span data-ttu-id="21d40-308">使用 IIS 管理員以測試憑證將閘道設定為根網站</span><span class="sxs-lookup"><span data-stu-id="21d40-308">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>](#BKMK_configroot)

-   

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a><span data-ttu-id="21d40-309">使用 IIS 管理員在現有的網站中設定閘道</span><span class="sxs-lookup"><span data-stu-id="21d40-309">To use IIS Manager to configure the gateway in an existing website</span></span>

1.  <span data-ttu-id="21d40-310">執行下列其中一項動作以開啟 IIS 管理員主控台。</span><span class="sxs-lookup"><span data-stu-id="21d40-310">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="21d40-311">在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。</span><span class="sxs-lookup"><span data-stu-id="21d40-311">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="21d40-312">在 [伺服器管理員] 的 **[工具]** 功能表上，按一下 **[Internet Information Services (IIS) 管理員]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-312">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="21d40-313">在 Windows [開始] 畫面中，輸入 **Internet Information Services (IIS) 管理員**名稱的任何部分。</span><span class="sxs-lookup"><span data-stu-id="21d40-313">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="21d40-314">當捷徑出現在 [應用程式] 結果時，按一下該捷徑。</span><span class="sxs-lookup"><span data-stu-id="21d40-314">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="21d40-315">為 Windows PowerShell Web 存取建立新的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="21d40-315">Create a new application pool for Windows PowerShell Web Access.</span></span> <span data-ttu-id="21d40-316">在 [IIS 管理員] 樹狀目錄窗格中展開閘道伺服器的節點，選取 [應用程式集區]，然後在 [動作] 窗格中按一下 [新增應用程式集區]。</span><span class="sxs-lookup"><span data-stu-id="21d40-316">Expand the node of the gateway server in the IIS Manager tree pane, select **Application Pools**, and click **Add Application Pool** in the **Actions** pane.</span></span>

3.  <span data-ttu-id="21d40-317">新增名為 **pswa_pool** (或提供另一個名稱) 的新應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="21d40-317">Add a new application pool with the name **pswa_pool**, or provide another name.</span></span> <span data-ttu-id="21d40-318">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-318">Click **OK**.</span></span>

4.  <span data-ttu-id="21d40-319">在 [IIS 管理員] 樹狀目錄窗格中，展開安裝 Windows PowerShell Web 存取的伺服器節點，直到可以看到 [站台] 資料夾為止。</span><span class="sxs-lookup"><span data-stu-id="21d40-319">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="21d40-320">選取 [站台] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="21d40-320">Select the **Sites** folder.</span></span>

5.  <span data-ttu-id="21d40-321">以滑鼠右鍵按一下您想要新增 Windows PowerShell Web 存取網站的網站 (例如 **[預設的網站]**)，然後按一下 **[新增應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-321">Right-click the website (for example, **Default Web Site**) to which you would like to add the Windows PowerShell Web Access website, and then click **Add Application**.</span></span>

6.  <span data-ttu-id="21d40-322">在 [別名] 欄位中輸入 pswa，或者提供另一個別名。</span><span class="sxs-lookup"><span data-stu-id="21d40-322">In the **Alias** field, type pswa, or provide another alias.</span></span> <span data-ttu-id="21d40-323">別名會成為虛擬目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="21d40-323">The alias becomes the virtual directory name.</span></span> <span data-ttu-id="21d40-324">例如，下列 URL 中的 **pswa** 代表在這個步驟中指定的別名：https://&lt;server_name&gt;/pswa。</span><span class="sxs-lookup"><span data-stu-id="21d40-324">For example, **pswa** in the following URL represents the alias specified in this step: https://&lt;server_name&gt;/pswa.</span></span>

7.  <span data-ttu-id="21d40-325">在 [應用程式集區] 欄位中，選取您在步驟 3 建立的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="21d40-325">In the **Application pool** field, select the application pool that you created in step 3.</span></span>

8.  <span data-ttu-id="21d40-326">在 [實體路徑] 欄位中，瀏覽應用程式的位置。</span><span class="sxs-lookup"><span data-stu-id="21d40-326">In the **Physical path** field, browse for the location of the application.</span></span> <span data-ttu-id="21d40-327">您可以使用預設位置 %windir%/Web/PowerShellWebAccess/wwwroot。</span><span class="sxs-lookup"><span data-stu-id="21d40-327">You can use the default location, %windir%/Web/PowerShellWebAccess/wwwroot.</span></span> <span data-ttu-id="21d40-328">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-328">Click **OK**.</span></span>

9.  <span data-ttu-id="21d40-329">請遵照本主題之 [在 IIS 管理員中設定 SSL 憑證](#BKMK_cert) 程序中的步驟執行。</span><span class="sxs-lookup"><span data-stu-id="21d40-329">Follow the steps in the procedure [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic.</span></span>

10. <span data-ttu-id="21d40-330"><span class="label">選擇性安全性步驟：</span>在樹狀目錄窗格中選取網站後，按兩下內容窗格中的 [SSL 設定]。</span><span class="sxs-lookup"><span data-stu-id="21d40-330"><span class="label">Optional security step:</span> With the website selected in the tree pane, double-click **SSL Settings** in the content pane.</span></span> <span data-ttu-id="21d40-331">選取 [需要 SSL]，然後在 [動作] 窗格中，按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="21d40-331">Select **Require SSL**, and then in the **Actions** pane, click **Apply**.</span></span> <span data-ttu-id="21d40-332">您也可以選擇性地在 [SSL 設定] 窗格中，要求連線到 Windows PowerShell Web 存取網站的使用者必須擁有用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="21d40-332">Optionally, in the **SSL Settings** pane, you can require that users connecting to the Windows PowerShell Web Access website have client certificates.</span></span> <span data-ttu-id="21d40-333">用戶端憑證可協助確認用戶端裝置使用者的身份。</span><span class="sxs-lookup"><span data-stu-id="21d40-333">Client certificates help to verify the identity of a client device user.</span></span> <span data-ttu-id="21d40-334">如需要求用戶端憑證如何增加 Windows PowerShell Web 存取安全性的詳細資訊，請參閱本指南中的 [Windows PowerShell Web 存取的授權規則與安全性功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)。</span><span class="sxs-lookup"><span data-stu-id="21d40-334">For more information about how requiring client certificates can increase the security of Windows PowerShell Web Access, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) in this guide.</span></span>

11. <span data-ttu-id="21d40-335">開啟用戶端裝置的瀏覽器工作階段。</span><span class="sxs-lookup"><span data-stu-id="21d40-335">Open a browser session on a client device.</span></span> <span data-ttu-id="21d40-336">如需支援的瀏覽器及裝置的詳細資訊，請參閱本主題的[瀏覽器及用戶端裝置支援](#BKMK_browser)。</span><span class="sxs-lookup"><span data-stu-id="21d40-336">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this topic.</span></span>

12. <span data-ttu-id="21d40-337">開啟新的 Windows PowerShell Web 存取網站 https://&lt; *gateway_server_name*&gt;/pswa。</span><span class="sxs-lookup"><span data-stu-id="21d40-337">Open the new Windows PowerShell Web Access website, https://&lt; *gateway_server_name*&gt;/pswa.</span></span>

    <span data-ttu-id="21d40-338">瀏覽器應該會顯示 Windows PowerShell Web 存取主控台登入頁面。</span><span class="sxs-lookup"><span data-stu-id="21d40-338">The browser should display the Windows PowerShell Web Access console sign-in page.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="21d40-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></span><span class="sxs-lookup"><span data-stu-id="21d40-339"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="21d40-340">必須透過新增授權規則，讓使用者獲得網站存取權，才能進行登入。</span><span class="sxs-lookup"><span data-stu-id="21d40-340">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

13. <span data-ttu-id="21d40-341">在使用提高的使用者權限 (以系統管理員身分執行) 開啟的 Windows PowerShell 工作階段中，執行下列指令碼，其中 *application_pool_name* 代表您在步驟 3 建立的應用程式集區名稱，以便授與該應用程式集區授權檔案的存取權。</span><span class="sxs-lookup"><span data-stu-id="21d40-341">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 3, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="21d40-342">Copy</span><span class="sxs-lookup"><span data-stu-id="21d40-342">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c1a80a93-8fcf-4beb-a025-5f81bfb8bdae'); "複製到剪貼簿。")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="21d40-343">若要檢視授權檔案的現有存取權，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="21d40-343">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="21d40-344">Copy</span><span class="sxs-lookup"><span data-stu-id="21d40-344">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ac2179c2-9548-4a17-8663-267fdd105380'); "複製到剪貼簿。")

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a><span data-ttu-id="21d40-345">使用 IIS 管理員以測試憑證將閘道設定為根網站</span><span class="sxs-lookup"><span data-stu-id="21d40-345">To use IIS Manager to configure the gateway as a root website with a test certificate</span></span>

1.  <span data-ttu-id="21d40-346">執行下列其中一項動作以開啟 IIS 管理員主控台。</span><span class="sxs-lookup"><span data-stu-id="21d40-346">Open the IIS Manager console by doing one of the following.</span></span>

    -   <span data-ttu-id="21d40-347">在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。</span><span class="sxs-lookup"><span data-stu-id="21d40-347">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="21d40-348">在 [伺服器管理員] 的 **[工具]** 功能表上，按一下 **[Internet Information Services (IIS) 管理員]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-348">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="21d40-349">在 Windows [開始] 畫面中，輸入 **Internet Information Services (IIS) 管理員**名稱的任何部分。</span><span class="sxs-lookup"><span data-stu-id="21d40-349">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="21d40-350">當捷徑出現在 [應用程式] 結果時，按一下該捷徑。</span><span class="sxs-lookup"><span data-stu-id="21d40-350">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="21d40-351">在 [IIS 管理員] 樹狀目錄窗格中，展開安裝 Windows PowerShell Web 存取的伺服器節點，直到可以看到 [站台] 資料夾為止。</span><span class="sxs-lookup"><span data-stu-id="21d40-351">In the IIS Manager tree pane, expand the node for the server on which Windows PowerShell Web Access is installed until the **Sites** folder is visible.</span></span> <span data-ttu-id="21d40-352">選取 [站台] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="21d40-352">Select the **Sites** folder.</span></span>

3.  <span data-ttu-id="21d40-353">在 **[動作]** 窗格中，按一下 **[Add Website] \(新增網站)**。</span><span class="sxs-lookup"><span data-stu-id="21d40-353">In the **Actions** pane, click **Add Website**.</span></span>

4.  <span data-ttu-id="21d40-354">輸入網站的名稱，例如 **Windows PowerShell Web Access**。</span><span class="sxs-lookup"><span data-stu-id="21d40-354">Type a name for the website, such as **Windows PowerShell Web Access**.</span></span>

5.  <span data-ttu-id="21d40-355">此時會自動為新網站建立應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="21d40-355">An application pool is automatically created for the new website.</span></span> <span data-ttu-id="21d40-356">若要使用不同的應用程式集區，按一下 [選取]，以選取要與新網站相關聯的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="21d40-356">To use a different application pool, click **Select** to select an application pool to associate with the new website.</span></span> <span data-ttu-id="21d40-357">在 **[選取應用程式集區]** 對話方塊中選取替代的應用程式集區，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-357">Select the alternate application pool in the **Select Application Pool** dialog box, and then click **OK**.</span></span>

6.  <span data-ttu-id="21d40-358">在 [實體路徑] 文字方塊中，瀏覽到 %*windir*%/Web/PowerShellWebAccess/wwwroot。</span><span class="sxs-lookup"><span data-stu-id="21d40-358">In the **Physical path** text box, navigate to %*windir*%/Web/PowerShellWebAccess/wwwroot.</span></span>

7.  <span data-ttu-id="21d40-359">在 **[繫結]** 區域的 **[類型]** 欄位中，選取 **[https]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-359">In the **Type** field of the **Binding** area, select **https**.</span></span>

8.  <span data-ttu-id="21d40-360">為其他站台或應用程式尚未使用的網站指派連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="21d40-360">Assign a port number to the website that is not already in use by another site or application.</span></span> <span data-ttu-id="21d40-361">若要尋找開放的連接埠，可以在命令提示字元視窗中執行 **netstat** 命令。</span><span class="sxs-lookup"><span data-stu-id="21d40-361">To locate open ports, you can run the **netstat** command in a Command Prompt window.</span></span> <span data-ttu-id="21d40-362">預設連接埠號碼為 443。</span><span class="sxs-lookup"><span data-stu-id="21d40-362">The default port number is 443.</span></span>

    <span data-ttu-id="21d40-363">如果另一個網站已經使用 443，或者有其他需要變更連接埠號碼的安全性原因，請變更預設連接埠。</span><span class="sxs-lookup"><span data-stu-id="21d40-363">Change the default port if another website is already using 443, or if you have other security reasons for changing the port number.</span></span> <span data-ttu-id="21d40-364">如果在閘道伺服器上執行的另一個網站正在使用您選取的連接埠，當您在 [新增網站] 對話方塊中按一下 [確定] 時，就會顯示警告。</span><span class="sxs-lookup"><span data-stu-id="21d40-364">If another website that is running on your gateway server is using your selected port, a warning is displayed when you click **OK** in the **Add Website** dialog box.</span></span> <span data-ttu-id="21d40-365">您必須使用未使用的連接埠來執行 Windows PowerShell Web 存取。</span><span class="sxs-lookup"><span data-stu-id="21d40-365">You must use an unused port to run Windows PowerShell Web Access.</span></span>

9.  <span data-ttu-id="21d40-366">或者，如果組織有需要，可以指定對組織及使用者有意義的主機名稱，例如 **www.contoso.com**。</span><span class="sxs-lookup"><span data-stu-id="21d40-366">Optionally, if needed for your organization, specify a host name that makes sense to your organization and users, such as **www.contoso.com**.</span></span> <span data-ttu-id="21d40-367">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-367">Click **OK**.</span></span>

10. <span data-ttu-id="21d40-368">如需更安全的生產環境，強烈建議您提供 CA 簽署的有效憑證。</span><span class="sxs-lookup"><span data-stu-id="21d40-368">For a more secure production environment, we strongly recommend providing a valid certificate that has been signed by a CA.</span></span> <span data-ttu-id="21d40-369">您必須提供 SSL 憑證，因為使用者只能透過 HTTPS 網站連線到 Windows PowerShell Web 存取。</span><span class="sxs-lookup"><span data-stu-id="21d40-369">You must provide an SSL certificate, because users can only connect to Windows PowerShell Web Access through an HTTPS website.</span></span> <span data-ttu-id="21d40-370">如需如何取得憑證的詳細資訊，請參閱本主題中的[在 IIS 管理員設定 SSL 憑證](#BKMK_cert)。</span><span class="sxs-lookup"><span data-stu-id="21d40-370">See [To configure an SSL certificate in IIS Manager](#BKMK_cert) in this topic for more information about how to obtain a certificate.</span></span>

11. <span data-ttu-id="21d40-371">按一下 [確定]，以關閉 [新增網站] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21d40-371">Click **OK** to close the **Add Website** dialog box.</span></span>

12. <span data-ttu-id="21d40-372">在使用提高的使用者權限 (以系統管理員身分執行) 開啟的 Windows PowerShell 工作階段中，執行下列指令碼，其中 *application_pool_name* 代表您在步驟 4 建立的應用程式集區名稱，以便授與該應用程式集區授權檔案的存取權。</span><span class="sxs-lookup"><span data-stu-id="21d40-372">In a Windows PowerShell session that has been opened with elevated user rights (Run as Administrator), run the following script, in which *application_pool_name* represents the name of the application pool that you created in step 4, to give the application pool access rights to the authorization file.</span></span>

    [<span data-ttu-id="21d40-373">Copy</span><span class="sxs-lookup"><span data-stu-id="21d40-373">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_35ae9944-ca44-4af7-9c96-616083b3e3db'); "複製到剪貼簿。")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    <span data-ttu-id="21d40-374">若要檢視授權檔案的現有存取權，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="21d40-374">To view existing access rights on the authorization file, run the following command:</span></span>

    [<span data-ttu-id="21d40-375">Copy</span><span class="sxs-lookup"><span data-stu-id="21d40-375">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0eb6d70a-2807-498b-b088-fa5233ed68d5'); "複製到剪貼簿。")

        c:\windows\system32\icacls.exe $authorizationFile

13. <span data-ttu-id="21d40-376">在 [IIS 管理員] 樹狀目錄窗格中選取新網站後，在 [動作] 窗格中按一下 [啟動] 以啟動網站。</span><span class="sxs-lookup"><span data-stu-id="21d40-376">With the new website selected in the IIS Manager tree pane, click **Start** in the **Actions** pane to start the website.</span></span>

14. <span data-ttu-id="21d40-377">開啟用戶端裝置的瀏覽器工作階段。</span><span class="sxs-lookup"><span data-stu-id="21d40-377">Open a browser session on a client device.</span></span> <span data-ttu-id="21d40-378">如需支援的瀏覽器及裝置的詳細資訊，請參閱本文件的[瀏覽器及用戶端裝置支援](#BKMK_browser)。</span><span class="sxs-lookup"><span data-stu-id="21d40-378">For more information about supported browsers and devices, see [Browser and client device support](#BKMK_browser) in this document.</span></span>

15. <span data-ttu-id="21d40-379">開啟新的 Windows PowerShell Web 存取網站。</span><span class="sxs-lookup"><span data-stu-id="21d40-379">Open the new Windows PowerShell Web Access website.</span></span>

    <span data-ttu-id="21d40-380">由於根網站會指向 Windows PowerShell Web 存取資料夾，因此，當您開啟 https://&lt; *gateway_server_name*&gt; 時，瀏覽器應該會顯示 Windows PowerShell Web 存取登入頁面。</span><span class="sxs-lookup"><span data-stu-id="21d40-380">Because the root website points to the Windows PowerShell Web Access folder, the browser should display the Windows PowerShell Web Access sign-in page when you open https://&lt; *gateway_server_name*&gt;.</span></span> <span data-ttu-id="21d40-381">您應該不需要在 URL 中新增 **/pswa**。</span><span class="sxs-lookup"><span data-stu-id="21d40-381">You should not need to add **/pswa** to the URL.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="21d40-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></span><span class="sxs-lookup"><span data-stu-id="21d40-382"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="21d40-383">必須透過新增授權規則，讓使用者獲得網站存取權，才能進行登入。</span><span class="sxs-lookup"><span data-stu-id="21d40-383">You cannot sign in until users have been granted access to the website by adding authorization rules.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="21d40-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 3：設定限制性授權規則</span></a></span><span class="sxs-lookup"><span data-stu-id="21d40-384"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 3: Configure a restrictive authorization rule</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="21d40-385">安裝 Windows PowerShell Web 存取並設定閘道之後，使用者就可以在瀏覽器中開啟登入頁面，但是必須等到 Windows PowerShell Web 存取系統管理員明確授與使用者存取權之後，才能登入。</span><span class="sxs-lookup"><span data-stu-id="21d40-385">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="21d40-386">您可以使用下表所述的 Windows PowerShell Cmdlet，來管理 Windows PowerShell Web 存取存取控制。</span><span class="sxs-lookup"><span data-stu-id="21d40-386">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="21d40-387">沒有適用於新增或管理授權規則的 GUI。</span><span class="sxs-lookup"><span data-stu-id="21d40-387">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="21d40-388">如需 Windows PowerShell Web 存取 Cmdlet 的詳細資訊，請參閱 Cmdlet 參考主題：[Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx) (Windows PowerShell Web 存取 Cmdlet)。</span><span class="sxs-lookup"><span data-stu-id="21d40-388">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="21d40-389">如需 Windows PowerShell Web 存取授權規則和安全性的詳細資訊，請參閱 [Windows PowerShell Web 存取的授權規則與安全性功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)。</span><span class="sxs-lookup"><span data-stu-id="21d40-389">For more detail about Windows PowerShell Web Access authorization rules and security, see [Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).</span></span>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="21d40-390">新增限制性授權規則</span><span class="sxs-lookup"><span data-stu-id="21d40-390">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="21d40-391">執行下列其中一個動作，使用提高的使用者權限開啟 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="21d40-391">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="21d40-392">在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-392">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="21d40-393">在 Windows **[開始]** 畫面上，以滑鼠右鍵按一下 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-393">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="21d40-394"><span class="label">使用工作階段設定來限制使用者存取的選擇性步驟：</span>確認您要在規則中使用的工作階段設定已經存在。</span><span class="sxs-lookup"><span data-stu-id="21d40-394"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="21d40-395">如果尚未建立這些設定，請使用 MSDN 上 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) 中建立工作階段設定的指示。</span><span class="sxs-lookup"><span data-stu-id="21d40-395">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="21d40-396">輸入下列程式碼，然後按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="21d40-396">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="21d40-397">Copy</span><span class="sxs-lookup"><span data-stu-id="21d40-397">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4df22c91-f56f-4bb5-91e7-99f9b365ed5d'); "複製到剪貼簿。")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="21d40-398">這個授權規則允許特定使用者存取網路上他們通常有權存取的一部電腦，以及該使用者在一般編寫指令碼及 Cmdlet 範圍內的特定工作階段設定存取權。</span><span class="sxs-lookup"><span data-stu-id="21d40-398">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="21d40-399">在下列範例中，<span class="code">Contoso</span> 網域中名為 <span class="code">JSmith</span> 的使用者會被授與管理電腦 <span class="code">Contoso_214</span> 的存取權，並使用名為 <span class="code">NewAdminsOnly</span> 的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="21d40-399">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="21d40-400">Copy</span><span class="sxs-lookup"><span data-stu-id="21d40-400">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_efc3999a-2905-453f-86cd-014b41658ffc'); "複製到剪貼簿。")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="21d40-401">執行 **Get-PswaAuthorizationRule** Cmdlet 或 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;，確認已建立規則。</span><span class="sxs-lookup"><span data-stu-id="21d40-401">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="21d40-402">例如，**Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**。</span><span class="sxs-lookup"><span data-stu-id="21d40-402">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

<span data-ttu-id="21d40-403">設定授權規則之後，授權使用者就可以開始登入網頁型主控台，並開始使用 Windows PowerShell Web 存取。</span><span class="sxs-lookup"><span data-stu-id="21d40-403">After you have configured an authorization rule, you are ready for authorized users to sign in to the web-based console and begin using Windows PowerShell Web Access.</span></span>

<a href="" id="BKMK_configcert"></a>

<span data-ttu-id="21d40-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">設定正版憑證</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="21d40-404"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configure a genuine certificate</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="21d40-405">若要安全的生產環境，請一律使用由憑證授權單位 (CA) 簽署的有效 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="21d40-405">For a secure production environment, always use a valid SSL certificate that has been signed by a certification authority (CA).</span></span> <span data-ttu-id="21d40-406">本節中的程序說明如何從 CA 取得有效的 SSL 憑證並加以套用。</span><span class="sxs-lookup"><span data-stu-id="21d40-406">The procedure in this section describes how to obtain and apply a valid SSL certificate from a CA.</span></span>

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a><span data-ttu-id="21d40-407">在 IIS 管理員中設定 SSL 憑證</span><span class="sxs-lookup"><span data-stu-id="21d40-407">To configure an SSL certificate in IIS Manager</span></span>

1.  <span data-ttu-id="21d40-408">在 [IIS 管理員] 樹狀目錄窗格中，選取安裝 Windows PowerShell Web 存取的伺服器。</span><span class="sxs-lookup"><span data-stu-id="21d40-408">In the IIS Manager tree pane, select the server on which Windows PowerShell Web Access is installed.</span></span>

2.  <span data-ttu-id="21d40-409">在內容窗格中，按兩下 **[伺服器憑證]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-409">In the content pane, double click **Server Certificates**.</span></span>

3.  <span data-ttu-id="21d40-410">在 [動作] 窗格中，執行下列其中一項。</span><span class="sxs-lookup"><span data-stu-id="21d40-410">In the **Actions** pane, do one of the following.</span></span> <span data-ttu-id="21d40-411">如需在 IIS 中設定伺服器憑證的詳細資訊，請參閱[在 IIS 7 中設定伺服器憑證](https://technet.microsoft.com/library/cc732230.aspx)。</span><span class="sxs-lookup"><span data-stu-id="21d40-411">For more information about configuring server certificates in IIS, see [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).</span></span>

    -   <span data-ttu-id="21d40-412">按一下 [匯入]，從網路上的位置匯入現有的有效憑證。</span><span class="sxs-lookup"><span data-stu-id="21d40-412">Click **Import** to import an existing, valid certificate from a location on your network.</span></span>

    -   <span data-ttu-id="21d40-413">按一下 [建立憑證要求]，向 CA (例如 VeriSign™、Thawte 或 GeoTrust®) 要求憑證。</span><span class="sxs-lookup"><span data-stu-id="21d40-413">Click **Create Certificate Request** to request a certificate from a CA such as VeriSign™, Thawte, or GeoTrust®.</span></span> <span data-ttu-id="21d40-414">憑證的一般名稱必須符合要求中的主機標頭。</span><span class="sxs-lookup"><span data-stu-id="21d40-414">The certificate's common name must match the host header in the request.</span></span> <span data-ttu-id="21d40-415">例如，如果用戶端瀏覽器要求 http://www.contoso.com/，則一般名稱也必須為 http://www.contoso.com/。</span><span class="sxs-lookup"><span data-stu-id="21d40-415">For example, if the client browser requests http://www.contoso.com/, then the common name must also be http://www.contoso.com/.</span></span> <span data-ttu-id="21d40-416">這是提供憑證給 Windows PowerShell Web 存取閘道最安全且最建議的選項。</span><span class="sxs-lookup"><span data-stu-id="21d40-416">This is the most secure and recommended option for providing the Windows PowerShell Web Access gateway with a certificate.</span></span>

    -   <span data-ttu-id="21d40-417">按一下 [建立自我簽署憑證]，建立您可以立即使用的憑證，稍後視需要交由 CA 簽署。</span><span class="sxs-lookup"><span data-stu-id="21d40-417">Click **Create a Self-Signed Certificate** to create a certificate that you can use immediately, and have signed later by a CA if desired.</span></span> <span data-ttu-id="21d40-418">為自我簽署的憑證指定易記名稱，例如 **Windows PowerShell Web 存取**。</span><span class="sxs-lookup"><span data-stu-id="21d40-418">Specify a friendly name for the self-signed certificate, such as **Windows PowerShell Web Access**.</span></span> <span data-ttu-id="21d40-419">這個選項並不安全，建議只用於私人測試環境。</span><span class="sxs-lookup"><span data-stu-id="21d40-419">This option is not considered secure, and is recommended only for a private test environment.</span></span>

4.  <span data-ttu-id="21d40-420">建立或取得憑證之後，在 [IIS 管理員] 樹狀目錄窗格中選取要套用此憑證的網站 (例如 [預設的網站])，然後在 [動作] 窗格中按一下 [繫結]。</span><span class="sxs-lookup"><span data-stu-id="21d40-420">After creating or obtaining a certificate, select the website to which the certificate is applied (for example, **Default Web Site**) in the IIS Manager tree pane, and then click **Bindings** in the **Actions** pane.</span></span>

5.  <span data-ttu-id="21d40-421">如果尚未顯示繫結，請在 [新增站台繫結] 對話方塊中，新增站台的 [https] 繫結。</span><span class="sxs-lookup"><span data-stu-id="21d40-421">In the **Add Site Binding** dialog box, add an **https** binding for the site, if one is not already displayed.</span></span> <span data-ttu-id="21d40-422">如果您不是使用自我簽署的憑證，請指定這個程序步驟 3 所指定的主機名稱。</span><span class="sxs-lookup"><span data-stu-id="21d40-422">If you are not using a self-signed certificate, specify the host name from step 3 of this procedure.</span></span> <span data-ttu-id="21d40-423">如果您使用的是自我簽署的憑證，就不需要這個步驟。</span><span class="sxs-lookup"><span data-stu-id="21d40-423">If you are using a self-signed certificate, this step is not required.</span></span>

6.  <span data-ttu-id="21d40-424">選取您在這個程序的步驟 3 取得或建立的憑證，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="21d40-424">Select the certificate that you obtained or created in step 3 of this procedure, and then click **OK**.</span></span>

<a href="" id="BKMK_using"></a>

<span data-ttu-id="21d40-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">使用網頁型 Windows PowerShell 主控台</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="21d40-425"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Using the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="21d40-426">依本主題所述方式安裝 Windows PowerShell Web 存取並完成閘道設定之後，就可以使用 Windows PowerShell 網頁型主控台。</span><span class="sxs-lookup"><span data-stu-id="21d40-426">After Windows PowerShell Web Access is installed and the gateway configuration is finished as described in this topic, the Windows PowerShell web-based console is ready to use.</span></span> <span data-ttu-id="21d40-427">如需開始使用網頁型主控台的詳細資訊，請參閱[使用網頁型 Windows PowerShell 主控台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)。</span><span class="sxs-lookup"><span data-stu-id="21d40-427">For more information about getting started in the web-based console, see [Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).</span></span>

<span data-ttu-id="21d40-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另請參閱</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="21d40-428"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="21d40-429">[Internet Information Services (IIS) 7.0 文件](https://technet.microsoft.com/library/cc753433.aspx)
[IIS 管理員 7.0 說明](https://technet.microsoft.com/library/cc732664.aspx)
[設定網頁伺服器安全性 (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec 部屬資源](https://technet.microsoft.com/network/bb531150)</span><span class="sxs-lookup"><span data-stu-id="21d40-429">[Internet Information Services (IIS) 7.0 Documentation](https://technet.microsoft.com/library/cc753433.aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)
[Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec Deployment Resources](https://technet.microsoft.com/network/bb531150)</span></span>

<span data-ttu-id="21d40-430"><span>顯示︰</span>繼承受保護的</span><span class="sxs-lookup"><span data-stu-id="21d40-430"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="21d40-431"><span class="stdr-votetitle">此頁面是否有幫助？</span></span><span class="sxs-lookup"><span data-stu-id="21d40-431"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="21d40-432">是 否</span><span class="sxs-lookup"><span data-stu-id="21d40-432">Yes No</span></span>

<span data-ttu-id="21d40-433">其他意見反應？</span><span class="sxs-lookup"><span data-stu-id="21d40-433">Additional feedback?</span></span>

<span data-ttu-id="21d40-434"><span class="stdr-count">剩下 <span class="stdr-charcnt">1500</span> 個字元</span> 提交 略過</span><span class="sxs-lookup"><span data-stu-id="21d40-434"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="21d40-435"><span class="stdr-thankyou">謝謝您！</span></span><span class="sxs-lookup"><span data-stu-id="21d40-435"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="21d40-436"><span class="stdr-appreciate">我們非常感謝您的意見反應。</span></span><span class="sxs-lookup"><span data-stu-id="21d40-436"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="21d40-437">管理您的設定檔</span><span class="sxs-lookup"><span data-stu-id="21d40-437">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="21d40-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"><img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /></span> 網站意見反應</a> 網站意見反應</span><span class="sxs-lookup"><span data-stu-id="21d40-438"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="21d40-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="21d40-439"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="21d40-440">請與我們分享您的體驗...</span><span class="sxs-lookup"><span data-stu-id="21d40-440">Tell us about your experience...</span></span>

<span data-ttu-id="21d40-441">頁面是否快速載入？</span><span class="sxs-lookup"><span data-stu-id="21d40-441">Did the page load quickly?</span></span>

<span data-ttu-id="21d40-442"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="21d40-442"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="21d40-443">您喜歡頁面設計嗎？</span><span class="sxs-lookup"><span data-stu-id="21d40-443">Do you like the page design?</span></span>

<span data-ttu-id="21d40-444"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="21d40-444"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="21d40-445">請告訴我們更多資訊</span><span class="sxs-lookup"><span data-stu-id="21d40-445">Tell us more</span></span>

-   [<span data-ttu-id="21d40-446">電子快訊</span><span class="sxs-lookup"><span data-stu-id="21d40-446">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="21d40-447">與我們連絡</span><span class="sxs-lookup"><span data-stu-id="21d40-447">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="21d40-448">隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="21d40-448">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="21d40-449">使用規定</span><span class="sxs-lookup"><span data-stu-id="21d40-449">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="21d40-450">商標</span><span class="sxs-lookup"><span data-stu-id="21d40-450">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="21d40-451">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="21d40-451">© 2016 Microsoft</span></span>

<span data-ttu-id="21d40-452">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="21d40-452">© 2016 Microsoft</span></span>

<span data-ttu-id="21d40-453">連結至此網站或由此網站參照之第三方指令碼和程式碼，係由擁有此類程式碼之第三方授權予　貴用戶，而非 Microsoft 所授予。</span><span class="sxs-lookup"><span data-stu-id="21d40-453">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="21d40-454">請參閱 ASP.NET Ajax CDN 使用條款 - http://www.asp.net/ajaxlibrary/CDN.ashx。</span><span class="sxs-lookup"><span data-stu-id="21d40-454">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

