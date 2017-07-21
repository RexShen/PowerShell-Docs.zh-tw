---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用網頁型 Windows PowerShell 主控台"
ms.openlocfilehash: 48ed1646c00f909c4e950f197f51a30205060ef0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
#  <a name="use-the-web-based-windows-powershell-console"></a><span data-ttu-id="69ec3-103">使用網頁型 Windows PowerShell 主控台</span><span class="sxs-lookup"><span data-stu-id="69ec3-103">Use the Web-based Windows PowerShell Console</span></span>

<span data-ttu-id="69ec3-104">更新日期︰2013 年 6 月 24 日</span><span class="sxs-lookup"><span data-stu-id="69ec3-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="69ec3-105">適用目標︰Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="69ec3-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="69ec3-106">Windows PowerShell® Web 存取可讓 Windows PowerShell® 使用者登入 Secure Sockets Layer (SSL) 保護的網站，以使用 Windows PowerShell 工作階段、Cmdlet 和指令碼來管理遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="69ec3-106">Windows PowerShell® Web Access lets Windows PowerShell® users sign in to a Secure Sockets Layer (SSL)-secured website to use Windows PowerShell sessions, cmdlets, and scripts to manage a remote computer.</span></span> <span data-ttu-id="69ec3-107">因為 Windows PowerShell 主控台在網頁瀏覽器中執行，所以可以從各種用戶端裝置開啟，包括行動電話、平板電腦、公用電腦亭、膝上型電腦或共用或借用的電腦。</span><span class="sxs-lookup"><span data-stu-id="69ec3-107">Because the Windows PowerShell console runs in a web browser, it can be opened from a variety of client devices, including cell phones, tablet computers, public computing kiosks, laptop computers, or shared or borrowed computers.</span></span> <span data-ttu-id="69ec3-108">網頁型 Windows PowerShell 主控台用於使用者在登入處理程序中指定的遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="69ec3-108">The web-based Windows PowerShell console is targeted at a remote computer that is specified by users as part of the sign-in process.</span></span> <span data-ttu-id="69ec3-109">本主題說明如何登入並開始使用 Windows PowerShell Web 存取網頁型主控台。</span><span class="sxs-lookup"><span data-stu-id="69ec3-109">This topic describes how to sign in to and start using the Windows PowerShell Web Access web-based console.</span></span>

<span data-ttu-id="69ec3-110">本主題不會說明如何使用 Windows PowerShell，或執行 Cmdlet 或指令碼。</span><span class="sxs-lookup"><span data-stu-id="69ec3-110">This topic does not describe how to use Windows PowerShell or run cmdlets or scripts.</span></span> <span data-ttu-id="69ec3-111">如需如何使用 Windows PowerShell 及指令碼資源的詳細資訊，請參閱本主題結尾的另請參閱區段。</span><span class="sxs-lookup"><span data-stu-id="69ec3-111">For information about how to use Windows PowerShell, and scripting resources, see the See Also section at the end of this topic.</span></span>

<span data-ttu-id="69ec3-112">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="69ec3-112">In this topic:</span></span>

-   [<span data-ttu-id="69ec3-113">支援的瀏覽器及用戶端裝置</span><span class="sxs-lookup"><span data-stu-id="69ec3-113">Supported browsers and client devices</span></span>](#BKMK_browser)

-   [<span data-ttu-id="69ec3-114">登入 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="69ec3-114">Signing in to Windows PowerShell Web Access</span></span>](#BKMK_sign)

-   [<span data-ttu-id="69ec3-115">登出及逾時</span><span class="sxs-lookup"><span data-stu-id="69ec3-115">Signing out and timing out</span></span>](#BKMK_timeout)

-   [<span data-ttu-id="69ec3-116">網頁型 Windows PowerShell 主控台的差異</span><span class="sxs-lookup"><span data-stu-id="69ec3-116">Differences in the web-based Windows PowerShell console</span></span>](#BKMK_web)

<a href="" id="BKMK_browser"></a>
------------------------------------------------------------------------

<span data-ttu-id="69ec3-117">Windows PowerShell Web 存取支援下列網際網路瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="69ec3-117">Windows PowerShell Web Access supports the following Internet browsers.</span></span> <span data-ttu-id="69ec3-118">雖然並未正式支援行動瀏覽器，但很多行動瀏覽器應該都可以執行網頁型 Windows PowerShell 主控台。</span><span class="sxs-lookup"><span data-stu-id="69ec3-118">Although mobile browsers are not officially supported, many may be able to run the web-based Windows PowerShell console.</span></span> <span data-ttu-id="69ec3-119">其他接受 Cookie、執行 JavaScript 以及執行 HTTPS 網站的瀏覽器預期也可以運作，但尚未經過正式測試。</span><span class="sxs-lookup"><span data-stu-id="69ec3-119">Other browsers that accept cookies, run JavaScript, and run HTTPS websites are expected to work, but are not officially tested.</span></span>

###

<span data-ttu-id="69ec3-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">支援的桌上型電腦瀏覽器</span></a></span><span class="sxs-lookup"><span data-stu-id="69ec3-120"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Supported desktop computer browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="69ec3-121">適用於 Microsoft Windows® 8.0、9.0、10.0 以及 11.0 的 Windows® Internet Explorer®</span><span class="sxs-lookup"><span data-stu-id="69ec3-121">Windows® Internet Explorer® for Microsoft Windows® 8.0, 9.0, 10.0, and 11.0</span></span>

-   <span data-ttu-id="69ec3-122">Mozilla Firefox® 10.0.2</span><span class="sxs-lookup"><span data-stu-id="69ec3-122">Mozilla Firefox® 10.0.2</span></span>

-   <span data-ttu-id="69ec3-123">適用於 Windows 的 Google Chrome™ 17.0.963.56m</span><span class="sxs-lookup"><span data-stu-id="69ec3-123">Google Chrome™ 17.0.963.56m for Windows</span></span>

-   <span data-ttu-id="69ec3-124">適用於 Windows 的 Apple Safari® 5.1.2</span><span class="sxs-lookup"><span data-stu-id="69ec3-124">Apple Safari® 5.1.2 for Windows</span></span>

-   <span data-ttu-id="69ec3-125">適用於 Mac OS® 的 Apple Safari 5.1.2</span><span class="sxs-lookup"><span data-stu-id="69ec3-125">Apple Safari 5.1.2 for Mac OS®</span></span>

###

<span data-ttu-id="69ec3-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">通過基本測試的行動裝置或瀏覽器</span></a></span><span class="sxs-lookup"><span data-stu-id="69ec3-126"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Minimally-tested mobile devices or browsers</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="69ec3-127">Windows Phone 7 和 7.5</span><span class="sxs-lookup"><span data-stu-id="69ec3-127">Windows Phone 7 and 7.5</span></span>

-   <span data-ttu-id="69ec3-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span><span class="sxs-lookup"><span data-stu-id="69ec3-128">Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)</span></span>

-   <span data-ttu-id="69ec3-129">適用於 iPhone 作業系統 5.0.1 的 Apple Safari</span><span class="sxs-lookup"><span data-stu-id="69ec3-129">Apple Safari for iPhone operating system 5.0.1</span></span>

-   <span data-ttu-id="69ec3-130">適用於 iPad 2 作業系統 5.0.1 的 Apple Safari</span><span class="sxs-lookup"><span data-stu-id="69ec3-130">Apple Safari for iPad 2 operating system 5.0.1</span></span>

###

<span data-ttu-id="69ec3-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">瀏覽器需求</span></a></span><span class="sxs-lookup"><span data-stu-id="69ec3-131"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser requirements</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="69ec3-132">若要使用 Windows PowerShell Web 存取網頁型主控台，瀏覽器必須執行下列作業。</span><span class="sxs-lookup"><span data-stu-id="69ec3-132">To use the Windows PowerShell Web Access web-based console, browsers must do the following.</span></span>

-   <span data-ttu-id="69ec3-133">允許來自 Windows PowerShell Web 存取閘道網站的 Cookie。</span><span class="sxs-lookup"><span data-stu-id="69ec3-133">Allow cookies from the Windows PowerShell Web Access gateway website.</span></span>

-   <span data-ttu-id="69ec3-134">可以開啟和讀取 HTTPS 頁面。</span><span class="sxs-lookup"><span data-stu-id="69ec3-134">Be able to open and read HTTPS pages.</span></span>

-   <span data-ttu-id="69ec3-135">開啟和執行使用 JavaScript 的網站。</span><span class="sxs-lookup"><span data-stu-id="69ec3-135">Open and run websites that use JavaScript.</span></span>

<a href="" id="BKMK_sign"></a>

<span data-ttu-id="69ec3-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">登入 Windows PowerShell Web 存取</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="69ec3-136"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing in to Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="69ec3-137">您的 Windows PowerShell Web 存取系統管理員應該提供您組織的 Windows PowerShell Web 存取閘道網站位址的 URL。</span><span class="sxs-lookup"><span data-stu-id="69ec3-137">Your Windows PowerShell Web Access administrator should provide you with a URL that is the address of your organization’s Windows PowerShell Web Access gateway website.</span></span> <span data-ttu-id="69ec3-138">根據預設，這個網址是 https://&lt;server_name&gt;/pswa。</span><span class="sxs-lookup"><span data-stu-id="69ec3-138">By default, this website address is https://&lt;server_name&gt;/pswa.</span></span> <span data-ttu-id="69ec3-139">在您登入 Windows PowerShell Web 存取之前，請確定您有想要管理之遠端電腦的名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="69ec3-139">Before you sign in to Windows PowerShell Web Access, be sure that you have the name or IP address of the remote computer that you want to manage.</span></span> <span data-ttu-id="69ec3-140">您必須是遠端電腦上的已授權使用者，而且電腦必須設定為允許遠端管理。</span><span class="sxs-lookup"><span data-stu-id="69ec3-140">You must be an authorized user on the remote computer, and it must be configured to allow remote management.</span></span> <span data-ttu-id="69ec3-141">如需如何設定電腦以允許遠端管理的詳細資訊，請參閱[在 Windows PowerShell 中啟用和使用遠端命令](https://technet.microsoft.com/magazine/ff700227.aspx)。</span><span class="sxs-lookup"><span data-stu-id="69ec3-141">For more information about configuring your computer to allow remote management, see [Enable and Use Remote Commands in Windows PowerShell](https://technet.microsoft.com/magazine/ff700227.aspx).</span></span> <span data-ttu-id="69ec3-142">設定電腦以允許遠端管理最簡單的方法，就是在電腦上使用提升的使用者權限 (**[以系統管理員身分執行]**) 開啟的 Windows PowerShell 工作階段中執行 **Enable-PSRemoting -force** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="69ec3-142">The simplest method of configuring your computer to allow remote management is to run the **Enable-PSRemoting -force** cmdlet on the computer, in a Windows PowerShell session that has been opened with elevated user rights (**Run as Administrator**).</span></span>

### <a name="to-sign-in-to-windows-powershell-web-access"></a><span data-ttu-id="69ec3-143">登入 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="69ec3-143">To sign in to Windows PowerShell Web Access</span></span>

1.  <span data-ttu-id="69ec3-144">在網際網路瀏覽器視窗或索引標籤中開啟 Windows PowerShell Web 存取網站。</span><span class="sxs-lookup"><span data-stu-id="69ec3-144">Open the Windows PowerShell Web Access website in an Internet browser window or tab.</span></span>

2.  <span data-ttu-id="69ec3-145">在 Windows PowerShell Web 存取登入頁面，提供您的網路使用者名稱、密碼以及您想要管理 (而且是已授權使用者) 的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="69ec3-145">On the Windows PowerShell Web Access sign-in page, provide your network user name, password, and the name of the computer that you want to manage (and on which you are an authorized user).</span></span> <span data-ttu-id="69ec3-146">如果 Windows PowerShell Web 存取系統管理員指示您使用自訂網站或 Proxy 伺服器的 URI，而不是電腦名稱，請在 [連線類型] 欄位中選取 [連線 URI]，然後提供 URI。</span><span class="sxs-lookup"><span data-stu-id="69ec3-146">If the Windows PowerShell Web Access administrator has instructed you to use a URI to a custom site or proxy server instead of a computer name, select **Connection URI** in the **Connection type** field, and then provide the URI.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="69ec3-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></span><span class="sxs-lookup"><span data-stu-id="69ec3-147"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><ul>
    <li><p><span data-ttu-id="69ec3-148">如果目的地電腦在工作群組中，請使用下列語法提供您的使用者名稱並登入電腦：&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;。</span><span class="sxs-lookup"><span data-stu-id="69ec3-148">If the destination computer is in a workgroup, use the following syntax to provide your user name and sign in to the computer:&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    <li><p><span data-ttu-id="69ec3-149">如果目的地電腦是閘道伺服器，您可以在 [電腦名稱]<strong></strong> 欄位中指定 <strong>localhost</strong>。</span><span class="sxs-lookup"><span data-stu-id="69ec3-149">If the destination computer is the gateway server, you can specify <strong>localhost</strong> in the <strong>Computer name</strong> field.</span></span></p></li>
    <li><p><span data-ttu-id="69ec3-150">如果目的地電腦是閘道伺服器，而且閘道伺服器位於工作群組中，則 [電腦名稱]<strong></strong> 欄位可以使用 <strong>localhost</strong>，但 [使用者名稱]<strong></strong> 欄位不要使用 localhost\&lt;<em>user_name</em>&gt;。</span><span class="sxs-lookup"><span data-stu-id="69ec3-150">If the destination computer is the gateway server, and the gateway server is in a workgroup, you can use <strong>localhost</strong> in the <strong>Computer name</strong> field, but do not use localhost\&lt;<em>user_name</em>&gt; in the <strong>User name</strong> field.</span></span> <span data-ttu-id="69ec3-151">您必須使用 &lt;<em>工作群組名稱</em>&gt;\&lt;<em>user_name</em>&gt;。</span><span class="sxs-lookup"><span data-stu-id="69ec3-151">You must use &lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;.</span></span></p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

3.  <span data-ttu-id="69ec3-152">[選用連線設定] 區段與您想要管理的遠端電腦授權需求有關。</span><span class="sxs-lookup"><span data-stu-id="69ec3-152">The **Optional Connection Settings** section relates to the authorization requirements of the remote computer that you want to manage.</span></span> <span data-ttu-id="69ec3-153">如需等同於選用連線設定之參數的詳細資訊，請參閱 [Enter-PSSession](https://technet.microsoft.com/library/dd315384.aspx)。</span><span class="sxs-lookup"><span data-stu-id="69ec3-153">For more information about the parameters that are equivalent to optional connection settings, see the [Enter-PSSession cmdlet Help](https://technet.microsoft.com/library/dd315384.aspx).</span></span>

    <span data-ttu-id="69ec3-154">一般而言，您用來通過 Windows PowerShell Web 存取閘道的認證與您想要管理之電腦所識別的認證相同。</span><span class="sxs-lookup"><span data-stu-id="69ec3-154">Typically, the credentials you use to pass through the Windows PowerShell Web Access gateway are the same that are recognized by the remote computer that you want to manage.</span></span> <span data-ttu-id="69ec3-155">不過，如果您想要使用不同的認證來管理您在步驟 2 指定的遠端電腦，請展開 [選用連線設定] 區段，然後提供替代的認證。</span><span class="sxs-lookup"><span data-stu-id="69ec3-155">However, if you want to use different credentials to manage the remote computer that you specified in step 2, expand the **Optional Connection Settings** section, and provide the alternate credentials.</span></span> <span data-ttu-id="69ec3-156">否則，請前往步驟 6。</span><span class="sxs-lookup"><span data-stu-id="69ec3-156">Otherwise, skip to step 6.</span></span>

4.  <span data-ttu-id="69ec3-157">如果 Windows PowerShell Web 存取系統管理員已經針對 Windows PowerShell Web 存取使用者建立自訂工作階段設定，請在 [組態名稱] 欄位中輸入工作階段設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="69ec3-157">If the Windows PowerShell Web Access administrator has created a custom session configuration for Windows PowerShell Web Access users, type the name of the session configuration name in the **Configuration name** field.</span></span> <span data-ttu-id="69ec3-158">如需工作階段設定的詳細資訊，請參閱 Microsoft 網站上的 [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)。</span><span class="sxs-lookup"><span data-stu-id="69ec3-158">For more information about session configurations, see [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx) on the Microsoft website.</span></span>

5.  <span data-ttu-id="69ec3-159">請保留 [驗證類型] 設為 [預設]，除非 Windows PowerShell Web 存取系統管理員指示您不要保留。</span><span class="sxs-lookup"><span data-stu-id="69ec3-159">Keep the **Authentication type** set to **Default** unless you have been instructed to do otherwise by the Windows PowerShell Web Access administrator.</span></span>

6.  <span data-ttu-id="69ec3-160">按一下 **[登入]**。</span><span class="sxs-lookup"><span data-stu-id="69ec3-160">Click **Sign in**.</span></span>

<a href="" id="BKMK_timeout"></a>

<span data-ttu-id="69ec3-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">登出及逾時</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="69ec3-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Signing out and timing out</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="69ec3-162">下列其中一項會將您登出網頁型 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="69ec3-162">Any of the following signs you out of a web-based Windows PowerShell session.</span></span>

-   <span data-ttu-id="69ec3-163">按一下主控台右下角的 [登出]。</span><span class="sxs-lookup"><span data-stu-id="69ec3-163">Clicking **Sign out** in the lower right corner of the console.</span></span> <span data-ttu-id="69ec3-164">(僅限 Windows Server 2012)</span><span class="sxs-lookup"><span data-stu-id="69ec3-164">(Windows Server 2012 only)</span></span>

-   <span data-ttu-id="69ec3-165">按一下主控台右下角的 [儲存] 或 [結束]\(僅限 Windows Server 2012 R2)。</span><span class="sxs-lookup"><span data-stu-id="69ec3-165">Clicking **Save** or **Exit** in the lower right corner of the console (Windows Server 2012 R2 only).</span></span> <span data-ttu-id="69ec3-166">按一下 [儲存] 儲存並關閉您的 Windows PowerShell Web 存取工作階段；您稍後可以重新連線至工作階段。</span><span class="sxs-lookup"><span data-stu-id="69ec3-166">Clicking **Save** saves and closes your Windows PowerShell Web Access session; you can reconnect to the session later.</span></span> <span data-ttu-id="69ec3-167">當您重新登入 Windows PowerShell Web 存取時，Windows PowerShell Web 存取會顯示一份已儲存工作階段的清單；您可以選取並重新連線至已儲存的工作階段，或者啟動新的工作階段。</span><span class="sxs-lookup"><span data-stu-id="69ec3-167">When you sign in to Windows PowerShell Web Access again, Windows PowerShell Web Access displays a list of your saved sessions; you can either select and reconnect to a saved session, or start a new session.</span></span> <span data-ttu-id="69ec3-168">允許使用者開啟的工作階段數目上限 (包括已儲存和使用中)，由閘道管理員所設定。</span><span class="sxs-lookup"><span data-stu-id="69ec3-168">The maximum number of open sessions that users are allowed, both saved and active, is configured by the gateway administrator.</span></span>

    <span data-ttu-id="69ec3-169">按一下 [結束] 會將您登出 Windows PowerShell Web 存取工作階段而不加以儲存。</span><span class="sxs-lookup"><span data-stu-id="69ec3-169">Clicking **Exit** signs you out of the Windows PowerShell Web Access session without saving it.</span></span>

-   <span data-ttu-id="69ec3-170">在相同的瀏覽器工作階段或相同瀏覽器工作階段的新索引標籤中，嘗試登入以管理不同的遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="69ec3-170">Attempting to sign in to manage a different remote computer in the same browser session, or in a new tab of the same browser session.</span></span> <span data-ttu-id="69ec3-171">(這在閘道伺服器執行 Windows Server 2012 R2 時並不適用；Windows Server 2012 R2 上執行的 Windows PowerShell Web 存取不允許在相同的瀏覽器工作階段中有多個使用者工作階段。)如需如何在相同電腦上使用多個使用中工作階段的詳細資訊，請參閱本主題[網頁型主控台的限制](#BKMK_limits)一節中的＜同時連線多部目標電腦＞。</span><span class="sxs-lookup"><span data-stu-id="69ec3-171">(This does not apply if the gateway server is running Windows Server 2012 R2; Windows PowerShell Web Access running on Windows Server 2012 R2 does allow multiple user sessions in new tabs in the same browser session.) For more information about how to use more than one active session on the same computer, see “Connecting to multiple target computers simultaneously” in the [Limitations of the web-based console](#BKMK_limits) section of this topic.</span></span>

-   <span data-ttu-id="69ec3-172">工作階段 20 分鐘沒有活動。</span><span class="sxs-lookup"><span data-stu-id="69ec3-172">20 minutes of inactivity in the session.</span></span> <span data-ttu-id="69ec3-173">閘道系統管理員可以自訂沒有活動的逾時期間；如需詳細資訊，請參閱[工作階段管理](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt)。</span><span class="sxs-lookup"><span data-stu-id="69ec3-173">The gateway administrator can customize the inactivity time-out period; for more information, see [Session management](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).</span></span>

    -   <span data-ttu-id="69ec3-174">如果您因為網路錯誤或其他非計劃中的關機或失敗 (而不是因為您自己關閉了工作階段) 從 Web 型主控台中斷工作階段的連線，Windows PowerShell Web 存取工作階段將繼續執行且連線到目標電腦，直到用戶端的逾時期間結束為止。</span><span class="sxs-lookup"><span data-stu-id="69ec3-174">If you are disconnected from a session in the web-based console because of a network error or other unplanned shutdown or failure, and not because you have closed the session yourself, the Windows PowerShell Web Access session continues to run, connected to the target computer, until the time-out period on the client side lapses.</span></span> <span data-ttu-id="69ec3-175">根據預設，此逾時期限是 20 分鐘，由閘道管理員所設定。</span><span class="sxs-lookup"><span data-stu-id="69ec3-175">By default, this time-out period is 20 minutes, and is configured by the gateway administrator.</span></span> <span data-ttu-id="69ec3-176">工作階段會在預設的 20 分鐘或閘道系統管理員所指定的逾時期間之後中斷連線，視何者較短而定。</span><span class="sxs-lookup"><span data-stu-id="69ec3-176">The session is disconnected after either the default 20 minutes, or after the time-out period specified by the gateway administrator, whichever is shorter.</span></span>

        <span data-ttu-id="69ec3-177">如果閘道伺服器執行 Windows Server 2012 R2，Windows PowerShell Web 存取可讓使用者在稍後重新連線到工作階段，但您將無法檢視或重新連線到已儲存的工作階段，直到閘道系統管理員所指定的逾時期間結束為止。</span><span class="sxs-lookup"><span data-stu-id="69ec3-177">If the gateway server is running Windows Server 2012 R2, Windows PowerShell Web Access lets users reconnect to saved sessions at a later time, but you cannot see or reconnect to saved sessions until after the time-out period specified by the gateway administrator has lapsed.</span></span>

-   <span data-ttu-id="69ec3-178">關閉瀏覽器視窗或索引標籤。</span><span class="sxs-lookup"><span data-stu-id="69ec3-178">Closing the browser window or tab.</span></span>

-   <span data-ttu-id="69ec3-179">關閉正在執行瀏覽器的用戶端裝置，或者中斷網路連線。</span><span class="sxs-lookup"><span data-stu-id="69ec3-179">Turning off the client device on which the browser is running, or disconnecting it from the network.</span></span>

-   <span data-ttu-id="69ec3-180">在 Web 主控台執行 [結束] 命令。</span><span class="sxs-lookup"><span data-stu-id="69ec3-180">Running the **Exit** command in the web console.</span></span> <span data-ttu-id="69ec3-181">如果您連線的工作階段設定支援 [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) 模式，或在受限制的 Runspace 中，則這個命令無效。</span><span class="sxs-lookup"><span data-stu-id="69ec3-181">This command does not work if the session configuration to which you are connected to is configured to support [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) mode, or is in a restricted runspace.</span></span>

<span data-ttu-id="69ec3-182">如果您想要重新登入，請再次開啟 Windows PowerShell Web 存取網頁，然後遵循本主題[登入 Windows PowerShell Web 存取](#BKMK_signin)的步驟來登入。</span><span class="sxs-lookup"><span data-stu-id="69ec3-182">If you want to sign in again, open the Windows PowerShell Web Access web page again, and sign in by following the steps in [To sign in to Windows PowerShell Web Access](#BKMK_signin) in this topic.</span></span>

<a href="" id="BKMK_web"></a>

<span data-ttu-id="69ec3-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">網頁型 Windows PowerShell 主控台的差異</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="69ec3-183"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Differences in the web-based Windows PowerShell console</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="69ec3-184">登入 Windows PowerShell Web 存取後，會在您的瀏覽器視窗或索引標籤中開啟網頁型 Windows PowerShell 主控台。</span><span class="sxs-lookup"><span data-stu-id="69ec3-184">After signing in to Windows PowerShell Web Access, a web-based Windows PowerShell console opens in your browser window or tab.</span></span> <span data-ttu-id="69ec3-185">因為這個主控台是連線到您在登入處理程序中指定的遠端電腦，所以只能在主控台使用可在遠端電腦上使用的 Windows PowerShell Cmdlet 或指令碼。</span><span class="sxs-lookup"><span data-stu-id="69ec3-185">Because the console is connected to the remote computer that you specified during the sign-in process, only those Windows PowerShell cmdlets or scripts that are available on the remote computer can be used in the console.</span></span> <span data-ttu-id="69ec3-186">本節將說明 Windows PowerShell Web 存取主控台的其他限制，以及 Windows PowerShell Web 存取主控台和已安裝之 **PowerShell.exe** 主控台之間的差異。</span><span class="sxs-lookup"><span data-stu-id="69ec3-186">This section describes other limitations of Windows PowerShell Web Access consoles, and differences between Windows PowerShell Web Access consoles and the installed **PowerShell.exe** console.</span></span>

###

<span data-ttu-id="69ec3-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">與 PowerShell.exe 的功能差異</span></a></span><span class="sxs-lookup"><span data-stu-id="69ec3-187"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Functional disparity with PowerShell.exe</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="69ec3-188">大部分的 Windows PowerShell 主機功能可在 Windows PowerShell Web 存取網頁型主控台中提供使用，但有一些功能未提供使用。</span><span class="sxs-lookup"><span data-stu-id="69ec3-188">The majority of Windows PowerShell host functionality is available in the Windows PowerShell Web Access web-based console, but there are some features that are not available.</span></span>

-   <span data-ttu-id="69ec3-189"><span class="label">巢狀進度顯示。</span></span><span class="sxs-lookup"><span data-stu-id="69ec3-189"><span class="label">Nested progress displays.</span></span></span>  <span data-ttu-id="69ec3-190">Windows PowerShell Web 存取為報告進度 Cmdlet 顯示進度 GUI，但只會顯示最上層的進度資訊。</span><span class="sxs-lookup"><span data-stu-id="69ec3-190">Windows PowerShell Web Access displays a progress GUI for cmdlets that report progress, but only top-level progress information is displayed.</span></span>

-   <span data-ttu-id="69ec3-191"><span class="label">輸入色彩修改。</span></span><span class="sxs-lookup"><span data-stu-id="69ec3-191"><span class="label">Input color modification.</span></span></span>  <span data-ttu-id="69ec3-192">輸入色彩 (前景及背景) 無法變更。</span><span class="sxs-lookup"><span data-stu-id="69ec3-192">The input color (both foreground and background) cannot be changed.</span></span> <span data-ttu-id="69ec3-193">輸出、警告、詳細資訊以及錯誤訊息的樣式，都可以藉由執行指令碼來變更。</span><span class="sxs-lookup"><span data-stu-id="69ec3-193">The style of output, warning, verbose, and error messages can all be changed by running a script.</span></span>

-   <span data-ttu-id="69ec3-194"><span class="label">PSHostRawUserInterface。</span></span><span class="sxs-lookup"><span data-stu-id="69ec3-194"><span class="label">PSHostRawUserInterface.</span></span></span>  <span data-ttu-id="69ec3-195">Windows PowerShell Web 存取是透過 Windows PowerShell 遠端管理來實作，並使用遠端 runspace。</span><span class="sxs-lookup"><span data-stu-id="69ec3-195">Windows PowerShell Web Access is implemented over Windows PowerShell remote management, and uses a remote runspace.</span></span> <span data-ttu-id="69ec3-196">Windows PowerShell Web 存取不會實作這個介面中的某些方法；例如，寫入 Windows 主控台的任何命令。</span><span class="sxs-lookup"><span data-stu-id="69ec3-196">Windows PowerShell Web Access does not implement some methods in this interface; for example, any command that writes to the Windows console.</span></span> <span data-ttu-id="69ec3-197">類似 **PowerTab** 的命令不適用於 Windows PowerShell Web 存取。</span><span class="sxs-lookup"><span data-stu-id="69ec3-197">Commands such as **PowerTab** do not work in Windows PowerShell Web Access.</span></span>

-   <span data-ttu-id="69ec3-198"><span class="label">功能鍵。</span></span><span class="sxs-lookup"><span data-stu-id="69ec3-198"><span class="label">Function keys.</span></span></span>  <span data-ttu-id="69ec3-199">Windows PowerShell Web 存取不支援某些功能鍵，因為在許多情況下命令是由瀏覽器保留。</span><span class="sxs-lookup"><span data-stu-id="69ec3-199">Windows PowerShell Web Access does not support some function keys, in many cases because the commands are reserved by the browser.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="69ec3-200">不支援的功能鍵</span><span class="sxs-lookup"><span data-stu-id="69ec3-200">Unsupported Function Key</span></span></p></th>
<th><p><span data-ttu-id="69ec3-201">動作</span><span class="sxs-lookup"><span data-stu-id="69ec3-201">Action</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="69ec3-202">Ctrl+C</span><span class="sxs-lookup"><span data-stu-id="69ec3-202">Ctrl+C</span></span></p></td>
<td><p><span data-ttu-id="69ec3-203">在 Windows PowerShell Web 存取中，<strong>Ctrl+C</strong> 是由瀏覽器用來複製內容。</span><span class="sxs-lookup"><span data-stu-id="69ec3-203">In Windows PowerShell Web Access, <strong>Ctrl+C</strong> is used by the browser to copy content.</span></span> <span data-ttu-id="69ec3-204">主控台提供 [取消]<strong></strong> 按鈕，使用者也可以使用 <strong>Ctrl+Q</strong> 來取消命令。</span><span class="sxs-lookup"><span data-stu-id="69ec3-204">The console offers a <strong>Cancel</strong> button, and users can also use <strong>Ctrl+Q</strong> to cancel commands.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69ec3-205">Alt-space, e, l</span><span class="sxs-lookup"><span data-stu-id="69ec3-205">Alt-space, e, l</span></span></p></td>
<td><p><span data-ttu-id="69ec3-206">捲動螢幕緩衝區</span><span class="sxs-lookup"><span data-stu-id="69ec3-206">Scroll through the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69ec3-207">Alt+空格鍵, e, f</span><span class="sxs-lookup"><span data-stu-id="69ec3-207">Alt+Space, e, f</span></span></p></td>
<td><p><span data-ttu-id="69ec3-208">搜尋螢幕緩衝區中的文字</span><span class="sxs-lookup"><span data-stu-id="69ec3-208">Search for text in the screen buffer</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69ec3-209">Alt+空格鍵, e, k</span><span class="sxs-lookup"><span data-stu-id="69ec3-209">Alt+Space, e, k</span></span></p></td>
<td><p><span data-ttu-id="69ec3-210">選取要從螢幕緩衝區複製的文字</span><span class="sxs-lookup"><span data-stu-id="69ec3-210">Select text to be copied from the screen buffer</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69ec3-211">Alt+空格鍵, e, p</span><span class="sxs-lookup"><span data-stu-id="69ec3-211">Alt+Space, e, p</span></span></p></td>
<td><p><span data-ttu-id="69ec3-212">將剪貼簿內容貼到 Windows PowerShell 主控台</span><span class="sxs-lookup"><span data-stu-id="69ec3-212">Paste clipboard contents into the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69ec3-213">Alt+空格鍵, c</span><span class="sxs-lookup"><span data-stu-id="69ec3-213">Alt+Space, c</span></span></p></td>
<td><p><span data-ttu-id="69ec3-214">關閉 Windows PowerShell 主控台</span><span class="sxs-lookup"><span data-stu-id="69ec3-214">Close the Windows PowerShell console</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69ec3-215">Ctrl+Break</span><span class="sxs-lookup"><span data-stu-id="69ec3-215">Ctrl+Break</span></span></p></td>
<td><p><span data-ttu-id="69ec3-216">強制關閉 Windows PowerShell 視窗</span><span class="sxs-lookup"><span data-stu-id="69ec3-216">Force the Windows PowerShell window to close</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69ec3-217">Ctrl+Home</span><span class="sxs-lookup"><span data-stu-id="69ec3-217">Ctrl+Home</span></span></p></td>
<td><p><span data-ttu-id="69ec3-218">從目前命令列前面開始刪除</span><span class="sxs-lookup"><span data-stu-id="69ec3-218">Deletes from the beginning of the current command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69ec3-219">Ctrl+End</span><span class="sxs-lookup"><span data-stu-id="69ec3-219">Ctrl+End</span></span></p></td>
<td><p><span data-ttu-id="69ec3-220">刪除到命令列的結尾</span><span class="sxs-lookup"><span data-stu-id="69ec3-220">Deletes to end of the command line</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69ec3-221">F1</span><span class="sxs-lookup"><span data-stu-id="69ec3-221">F1</span></span></p></td>
<td><p><span data-ttu-id="69ec3-222">在命令列上將游標向右移動一個字元</span><span class="sxs-lookup"><span data-stu-id="69ec3-222">Move cursor one character to the right on your command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69ec3-223">F2</span><span class="sxs-lookup"><span data-stu-id="69ec3-223">F2</span></span></p></td>
<td><p><span data-ttu-id="69ec3-224">藉由複製上個命令所輸入的字元來建立新的命令</span><span class="sxs-lookup"><span data-stu-id="69ec3-224">Creates a new command by copying your last command up to the character that you type</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69ec3-225">F3</span><span class="sxs-lookup"><span data-stu-id="69ec3-225">F3</span></span></p></td>
<td><p><span data-ttu-id="69ec3-226">使用上個命令列的內容來完成命令列</span><span class="sxs-lookup"><span data-stu-id="69ec3-226">Complete the command line with content from your last command line</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69ec3-227">F4</span><span class="sxs-lookup"><span data-stu-id="69ec3-227">F4</span></span></p></td>
<td><p><span data-ttu-id="69ec3-228">從游標位置刪除字元</span><span class="sxs-lookup"><span data-stu-id="69ec3-228">Deletes characters from cursor position</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69ec3-229">F5</span><span class="sxs-lookup"><span data-stu-id="69ec3-229">F5</span></span></p></td>
<td><p><span data-ttu-id="69ec3-230">向前查看您的命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="69ec3-230">Scan backward through your command history.</span></span> <span data-ttu-id="69ec3-231">若要存取 Windows PowerShell Web 存取命令歷程記錄中的命令，按一下網頁型主控台中的[記錄]<strong></strong> 捲動按鈕。</span><span class="sxs-lookup"><span data-stu-id="69ec3-231">To access commands in the command history in Windows PowerShell Web Access, click the <strong>History</strong> scroll buttons in the web-based console.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69ec3-232">F7</span><span class="sxs-lookup"><span data-stu-id="69ec3-232">F7</span></span></p></td>
<td><p><span data-ttu-id="69ec3-233">以互動方式從命令歷程記錄選取命令</span><span class="sxs-lookup"><span data-stu-id="69ec3-233">Interactively select a command from your command history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69ec3-234">F8</span><span class="sxs-lookup"><span data-stu-id="69ec3-234">F8</span></span></p></td>
<td><p><span data-ttu-id="69ec3-235">查看歷程記錄，顯示符合目前文字的命令</span><span class="sxs-lookup"><span data-stu-id="69ec3-235">Scan history displaying commands that match current text</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69ec3-236">F9</span><span class="sxs-lookup"><span data-stu-id="69ec3-236">F9</span></span></p></td>
<td><p><span data-ttu-id="69ec3-237">執行歷程記錄中特定編號的命令</span><span class="sxs-lookup"><span data-stu-id="69ec3-237">Run a specific numbered command from history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69ec3-238">Page Up</span><span class="sxs-lookup"><span data-stu-id="69ec3-238">Page Up</span></span></p></td>
<td><p><span data-ttu-id="69ec3-239">執行歷程記錄中的第一個命令</span><span class="sxs-lookup"><span data-stu-id="69ec3-239">Run the first command in the history</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="69ec3-240">Page Down</span><span class="sxs-lookup"><span data-stu-id="69ec3-240">Page Down</span></span></p></td>
<td><p><span data-ttu-id="69ec3-241">執行歷程記錄中的最後一個命令</span><span class="sxs-lookup"><span data-stu-id="69ec3-241">Run the last command in the history</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="69ec3-242">Alt+F7</span><span class="sxs-lookup"><span data-stu-id="69ec3-242">Alt+F7</span></span></p></td>
<td><p><span data-ttu-id="69ec3-243">清除命令歷程記錄清單</span><span class="sxs-lookup"><span data-stu-id="69ec3-243">Clear the command history list</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="69ec3-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">網頁型主控台的限制</span></a></span><span class="sxs-lookup"><span data-stu-id="69ec3-244">

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Limitations of the web-based console</span></a></span></span>

------------------------------------------------------------------------

-   <span data-ttu-id="69ec3-245"><span class="label">雙躍點。</span></span><span class="sxs-lookup"><span data-stu-id="69ec3-245"><span class="label">Double-hop.</span></span></span>   <span data-ttu-id="69ec3-246">如果您嘗試使用 Windows PowerShell Web 存取建立新工作階段或在新工作階段工作，可能會遭遇雙躍點 (或從第一個連線再連線到第二部電腦) 限制。</span><span class="sxs-lookup"><span data-stu-id="69ec3-246">You can encounter the double-hop (or connecting to a second computer from the first connection) limitation if you try to create or work on a new session by using Windows PowerShell Web Access.</span></span> <span data-ttu-id="69ec3-247">Windows PowerShell Web 存取使用遠端 runspace，且目前 **PowerShell.exe** 不支援從遠端 runspace 建立另一台電腦的遠端連線。</span><span class="sxs-lookup"><span data-stu-id="69ec3-247">Windows PowerShell Web Access uses a remote runspace, and currently, **PowerShell.exe** does not support establishing a remote connection to a second computer from a remote runspace.</span></span> <span data-ttu-id="69ec3-248">如果您嘗試使用 **Enter-PSSession** Cmdlet 從現有的連線再連線到第二部遠端電腦，您可能會收到各種錯誤，例如「無法取得網路資源」。</span><span class="sxs-lookup"><span data-stu-id="69ec3-248">If you attempt to connect to a second remote computer from an existing connection by using the **Enter-PSSession** cmdlet, for example, you can get various errors, such as “Cannot get network resources.”</span></span>

    <span data-ttu-id="69ec3-249">若要避免雙躍點錯誤，系統管理員應該在組織的網路環境中設定 CredSSP 驗證。</span><span class="sxs-lookup"><span data-stu-id="69ec3-249">To avoid double-hop errors, your administrator should configure CredSSP authentication in your organization’s network environment.</span></span> <span data-ttu-id="69ec3-250">如需設定 CredSSP 驗證的詳細資訊，請參閱 Microsoft 網站上的 [適用於第二躍點遠端的 CredSSP](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx)。</span><span class="sxs-lookup"><span data-stu-id="69ec3-250">For more information about configuring CredSSP authentication, see [CredSSP for second-hop remoting](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx) on the Microsoft website.</span></span> <span data-ttu-id="69ec3-251">當您想要管理第二部遠端電腦時也可以提供明確的認證；隱含的認證通常不允許第二躍點。</span><span class="sxs-lookup"><span data-stu-id="69ec3-251">You can also provide explicit credentials when you want to manage a second remote computer; implicit credentials are unlikely to allow the second hop.</span></span>

-   <span data-ttu-id="69ec3-252">Windows PowerShell Web 存取會使用且具有與遠端 Windows PowerShell 工作階段相同的限制。</span><span class="sxs-lookup"><span data-stu-id="69ec3-252">Windows PowerShell Web Access uses and has the same limitations as a remote Windows PowerShell session.</span></span> <span data-ttu-id="69ec3-253">直接呼叫 Windows 主控台 API 的命令 (例如用於主控台型編輯器或文字型功能表程式的命令) 無法運作，因為這些命令無法讀寫標準輸入、輸出以及錯誤管道。</span><span class="sxs-lookup"><span data-stu-id="69ec3-253">Commands that directly call Windows console APIs, such as those for console-based editors or text-based menu programs, do not work because the commands do not read or write to standard input, output, and error pipes.</span></span> <span data-ttu-id="69ec3-254">因此，會啟動可執行檔 (例如 **notepad.exe**) 或顯示 GUI (例如 <span class="code">OpenGridView</span> 或 <span class="code">ogv</span>) 的命令無法運作。</span><span class="sxs-lookup"><span data-stu-id="69ec3-254">Therefore, commands that launch an executable file, such as **notepad.exe**, or display a GUI, such as <span class="code">OpenGridView</span> or <span class="code">ogv</span>, do not work.</span></span> <span data-ttu-id="69ec3-255">您的體驗會受到這個行為影響；對您而言，Windows PowerShell Web 存取似乎不會回應您的命令。</span><span class="sxs-lookup"><span data-stu-id="69ec3-255">Your experience is affected by this behavior; to you, it appears that Windows PowerShell Web Access is not responding to your command.</span></span>

-   <span data-ttu-id="69ec3-256">TAB 鍵自動完成無法在具有受限制 Runspace 或處於 **NoLanguage** 模式的工作階段運作。</span><span class="sxs-lookup"><span data-stu-id="69ec3-256">Tab completion does not work in a session configuration with a restricted runspace or one that is in **NoLanguage** mode.</span></span> <span data-ttu-id="69ec3-257">雖然系統管理員可以設定工作階段來支援 TAB 鍵自動完成，但基於安全理由並不鼓勵這樣做，因為它會對未獲授權的使用者暴露下列資訊。</span><span class="sxs-lookup"><span data-stu-id="69ec3-257">Although administrators can configure a session to support tab completion, it is discouraged for security reasons, because it can expose the following information to unauthorized users.</span></span>

    -   <span data-ttu-id="69ec3-258">內部檔案系統路徑</span><span class="sxs-lookup"><span data-stu-id="69ec3-258">Internal file system paths</span></span>

    -   <span data-ttu-id="69ec3-259">內部電腦的共用資料夾</span><span class="sxs-lookup"><span data-stu-id="69ec3-259">Shared folders on internal computers</span></span>

    -   <span data-ttu-id="69ec3-260">Runspace 中的變數</span><span class="sxs-lookup"><span data-stu-id="69ec3-260">Variables in the runspace</span></span>

    -   <span data-ttu-id="69ec3-261">載入的類型或 .NET Framework 命名空間</span><span class="sxs-lookup"><span data-stu-id="69ec3-261">Loaded types or.NET Framework namespaces</span></span>

    -   <span data-ttu-id="69ec3-262">環境變數</span><span class="sxs-lookup"><span data-stu-id="69ec3-262">Environment variables</span></span>

-   <span data-ttu-id="69ec3-263">登入 **NoLanguage** 工作階段設定或 Windows PowerShell Web Access 中限制的 runspace 的使用者無法執行 [結束] 命令來結束工作階段。</span><span class="sxs-lookup"><span data-stu-id="69ec3-263">Users who are signed in to a **NoLanguage** session configuration or a restricted runspace in Windows PowerShell Web Access cannot run the **Exit** command to end the session.</span></span> <span data-ttu-id="69ec3-264">若要登出，使用者應該按一下主控台頁面上的 [登出]。</span><span class="sxs-lookup"><span data-stu-id="69ec3-264">To sign out, users should click **Sign Out** on the console page.</span></span>

-   <span data-ttu-id="69ec3-265"><span class="label">同時連線到多部目標電腦。</span></span><span class="sxs-lookup"><span data-stu-id="69ec3-265"><span class="label">Connecting to multiple target computers simultaneously.</span></span></span>   <span data-ttu-id="69ec3-266">如果閘道伺服器執行 Windows Server 2012，則 Windows PowerShell Web 存取只會允許每個瀏覽器工作階段連線到一部遠端電腦；它不允許使用者登入一次，然後使用個別的瀏覽器索引標籤連線到多部遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="69ec3-266">If the gateway server is running Windows Server 2012, Windows PowerShell Web Access allows only one remote computer connection per browser session; it does not allow users to sign in once, and connect to multiple remote computers by using separate browser tabs.</span></span> <span data-ttu-id="69ec3-267">當您開啟新索引標籤或新瀏覽器視窗時，Windows PowerShell Web 存取會提示您中斷目前工作階段的連線，然後啟動新的工作階段，如此您就可以連線到新的 (或相同的) 遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="69ec3-267">When you open a new tab or new browser window, Windows PowerShell Web Access prompts you to disconnect your current session and start a new session, so that you can connect to the new (or the same) remote computer.</span></span> <span data-ttu-id="69ec3-268">不過，如果需要針對不同的遠端電腦使用兩個或多個獨立的工作階段，Internet Explorer 中的功能可以讓您建立新工作階段。</span><span class="sxs-lookup"><span data-stu-id="69ec3-268">If two or more separate sessions to different remote computers are desired, however, a feature in Internet Explorer lets you create a new session.</span></span> <span data-ttu-id="69ec3-269">若要在 Internet Explorer 中啟動新的瀏覽器工作階段，請按下 **ALT**，開啟 [檔案] 功能表，然後選取 [新增工作階段]。</span><span class="sxs-lookup"><span data-stu-id="69ec3-269">To start a new browser session in Internet Explorer, press **ALT**, open the **File** menu, and then select **New Session**.</span></span> <span data-ttu-id="69ec3-270">然後，在新的工作階段中，開啟 Windows PowerShell Web 存取網站，並登入以存取另一部遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="69ec3-270">Then, open the Windows PowerShell Web Access website in the new session, and sign in to access another remote computer.</span></span>

    <span data-ttu-id="69ec3-271">當 Windows PowerShell Web 存取閘道在 Windows Server 2012 R2 上執行時，使用者可以在不同的瀏覽器索引標籤中開啟多個遠端電腦連線。</span><span class="sxs-lookup"><span data-stu-id="69ec3-271">When the Windows PowerShell Web Access gateway is running on Windows Server 2012 R2, users can open multiple connections to remote computers in different browser tabs.</span></span> <span data-ttu-id="69ec3-272">如果您想要使用網頁型 Windows PowerShell 主控台開啟多個遠端電腦連線，請檢查您的 Windows PowerShell Web 存取閘道管理員，以查看閘道伺服器是否支援此功能。</span><span class="sxs-lookup"><span data-stu-id="69ec3-272">If you want to open more than one connection to a remote computer by using the web-based Windows PowerShell console, check with your Windows PowerShell Web Access gateway administrator to see if this feature is supported by the gateway server.</span></span>

-   <span data-ttu-id="69ec3-273"><span class="label">持續性 Windows PowerShell 工作階段 (重新連線)。</span></span><span class="sxs-lookup"><span data-stu-id="69ec3-273"><span class="label">Persistent Windows PowerShell sessions (Reconnection).</span></span></span>   <span data-ttu-id="69ec3-274">Windows PowerShell Web 存取閘道逾時之後，會關閉閘道和目標電腦之間的遠端連線。</span><span class="sxs-lookup"><span data-stu-id="69ec3-274">After you time out of the Windows PowerShell Web Access gateway, the remote connection between the gateway and the target computer is closed.</span></span> <span data-ttu-id="69ec3-275">這會停止目前正在處理的所有 Cmdlet 或指令碼。</span><span class="sxs-lookup"><span data-stu-id="69ec3-275">This stops any cmdlets or scripts that are currently in process.</span></span> <span data-ttu-id="69ec3-276">當您執行長時間執行的工作時，建議您使用 Windows PowerShell **-Job** 基礎結構，您就可以啟動工作、中斷電腦連線、稍後重新連線，然後讓工作持續進行。</span><span class="sxs-lookup"><span data-stu-id="69ec3-276">You are encouraged to use the Windows PowerShell **-Job** infrastructure when you are performing long-running tasks, so that you can start jobs, disconnect from the computer, reconnect later, and have jobs persist.</span></span> <span data-ttu-id="69ec3-277">使用 **-Job** Cmdlet 的另一個優點是您可以透過使用 Windows PowerShell Web 存取啟動它們、登出，然後稍後再透過執行 Windows PowerShell Web 存取或另一部主機 (例如 Windows PowerShell® 整合式指令碼環境 (ISE)) 重新連線。</span><span class="sxs-lookup"><span data-stu-id="69ec3-277">Another benefit of using **-Job** cmdlets is that you can start them by using Windows PowerShell Web Access, sign out, and then reconnect later, either by running Windows PowerShell Web Access or another host (such as Windows PowerShell® Integrated Scripting Environment (ISE)).</span></span>

-   <span data-ttu-id="69ec3-278"><span class="label">調整主控台大小。</span></span><span class="sxs-lookup"><span data-stu-id="69ec3-278"><span class="label">Console resizing.</span></span></span>   <span data-ttu-id="69ec3-279">您可以使用下列三種方式調整 **PowerShell.exe** 主控台視窗大小。</span><span class="sxs-lookup"><span data-stu-id="69ec3-279">The **PowerShell.exe** console window can be resized in the following three ways.</span></span>

    -   <span data-ttu-id="69ec3-280">使用滑鼠拖曳並調整主控台視窗大小</span><span class="sxs-lookup"><span data-stu-id="69ec3-280">Drag and adjust the console window size with a mouse</span></span>

    -   <span data-ttu-id="69ec3-281">使用主控台內容 GUI 變更高度及寬度內容</span><span class="sxs-lookup"><span data-stu-id="69ec3-281">Change the height and width properties by using a GUI for console properties</span></span>

    -   <span data-ttu-id="69ec3-282">使用 Cmdlet 變更主控台視窗的高度及寬度</span><span class="sxs-lookup"><span data-stu-id="69ec3-282">Changing the height and width of console windows with a cmdlet</span></span>

        <span data-ttu-id="69ec3-283">Windows PowerShell Web 存取的主控台視窗可以使用 Cmdlet 來設定，如下所示。</span><span class="sxs-lookup"><span data-stu-id="69ec3-283">The console window for Windows PowerShell Web Access can be configured by using the cmdlets as follows.</span></span> <span data-ttu-id="69ec3-284">在下列範例中，使用者將 Windows PowerShell Web 存取主控台的寬度變更為 **20**。</span><span class="sxs-lookup"><span data-stu-id="69ec3-284">In the following example, a user changes the width of Windows PowerShell Web Access console to **20**.</span></span>

        [<span data-ttu-id="69ec3-285">Copy</span><span class="sxs-lookup"><span data-stu-id="69ec3-285">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_778d5e55-9195-4bd7-b313-d1fbca7876e4'); "複製到剪貼簿。")

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        <span data-ttu-id="69ec3-286">您可以類似的方式變更主控台的高度。</span><span class="sxs-lookup"><span data-stu-id="69ec3-286">You can change the height of the console in a similar manner.</span></span>

        <span data-ttu-id="69ec3-287">您可以在 [Windows PowerShell 小組部落格](http://blogs.msdn.com/b/powershell/)中找到自訂主控台檢視的其他範例。</span><span class="sxs-lookup"><span data-stu-id="69ec3-287">Additional examples for customizing the console view are available in the [Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/).</span></span>

<span data-ttu-id="69ec3-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另請參閱</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="69ec3-288"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="69ec3-289">[Windows PowerShell Cmdlet 參考資料](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Microsoft TechNet 上的 Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet 指令碼中心存放庫](http://gallery.technet.microsoft.com/scriptcenter)
[指令碼中心 - Hi，Scripting Guy！部落格](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/) (Windows PowerShell 小組部落格)</span><span class="sxs-lookup"><span data-stu-id="69ec3-289">[Windows PowerShell Cmdlet Reference](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Windows PowerShell on Microsoft TechNet](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet Script Center Repository](http://gallery.technet.microsoft.com/scriptcenter)
[Script Center - Hey, Scripting Guy!](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell Team Blog](http://blogs.msdn.com/b/powershell/)</span></span>

<span data-ttu-id="69ec3-290"><span>顯示︰</span>繼承受保護的</span><span class="sxs-lookup"><span data-stu-id="69ec3-290"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="69ec3-291"><span class="stdr-votetitle">此頁面是否有幫助？</span></span><span class="sxs-lookup"><span data-stu-id="69ec3-291"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="69ec3-292">是 否</span><span class="sxs-lookup"><span data-stu-id="69ec3-292">Yes No</span></span>

<span data-ttu-id="69ec3-293">其他意見反應？</span><span class="sxs-lookup"><span data-stu-id="69ec3-293">Additional feedback?</span></span>

<span data-ttu-id="69ec3-294"><span class="stdr-count">剩下 <span class="stdr-charcnt">1500</span> 個字元</span> 提交 略過</span><span class="sxs-lookup"><span data-stu-id="69ec3-294"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="69ec3-295"><span class="stdr-thankyou">謝謝您！</span></span><span class="sxs-lookup"><span data-stu-id="69ec3-295"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="69ec3-296"><span class="stdr-appreciate">我們非常感謝您的意見反應。</span></span><span class="sxs-lookup"><span data-stu-id="69ec3-296"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="69ec3-297">管理您的設定檔</span><span class="sxs-lookup"><span data-stu-id="69ec3-297">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="69ec3-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"><img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /></span> 網站意見反應</a> 網站意見反應</span><span class="sxs-lookup"><span data-stu-id="69ec3-298"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="69ec3-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="69ec3-299"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="69ec3-300">請與我們分享您的體驗...</span><span class="sxs-lookup"><span data-stu-id="69ec3-300">Tell us about your experience...</span></span>

<span data-ttu-id="69ec3-301">頁面是否快速載入？</span><span class="sxs-lookup"><span data-stu-id="69ec3-301">Did the page load quickly?</span></span>

<span data-ttu-id="69ec3-302"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="69ec3-302"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="69ec3-303">您喜歡頁面設計嗎？</span><span class="sxs-lookup"><span data-stu-id="69ec3-303">Do you like the page design?</span></span>

<span data-ttu-id="69ec3-304"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="69ec3-304"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="69ec3-305">請告訴我們更多資訊</span><span class="sxs-lookup"><span data-stu-id="69ec3-305">Tell us more</span></span>

-   [<span data-ttu-id="69ec3-306">電子快訊</span><span class="sxs-lookup"><span data-stu-id="69ec3-306">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="69ec3-307">與我們連絡</span><span class="sxs-lookup"><span data-stu-id="69ec3-307">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="69ec3-308">隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="69ec3-308">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="69ec3-309">使用規定</span><span class="sxs-lookup"><span data-stu-id="69ec3-309">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="69ec3-310">商標</span><span class="sxs-lookup"><span data-stu-id="69ec3-310">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="69ec3-311">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="69ec3-311">© 2016 Microsoft</span></span>

<span data-ttu-id="69ec3-312">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="69ec3-312">© 2016 Microsoft</span></span>

<span data-ttu-id="69ec3-313">連結至此網站或由此網站參照之第三方指令碼和程式碼，係由擁有此類程式碼之第三方授權予　貴用戶，而非 Microsoft 所授予。</span><span class="sxs-lookup"><span data-stu-id="69ec3-313">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="69ec3-314">請參閱 ASP.NET Ajax CDN 使用條款 - http://www.asp.net/ajaxlibrary/CDN.ashx。</span><span class="sxs-lookup"><span data-stu-id="69ec3-314">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

