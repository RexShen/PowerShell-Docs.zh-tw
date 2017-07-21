---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell Web 存取的授權規則與安全性功能"
ms.openlocfilehash: 706830f618173879185f5b84570fdc7782434d59
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a><span data-ttu-id="072ac-103">Windows PowerShell Web 存取的授權規則與安全性功能</span><span class="sxs-lookup"><span data-stu-id="072ac-103">Authorization Rules and Security Features of Windows PowerShell Web Access</span></span>

<span data-ttu-id="072ac-104">更新日期︰2013 年 6 月 24 日</span><span class="sxs-lookup"><span data-stu-id="072ac-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="072ac-105">適用目標︰Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="072ac-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="072ac-106">Windows Server® 2012 R2 和 Windows Server® 2012 中的 Windows PowerShell® Web 存取具有受限制的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="072ac-106">Windows PowerShell® Web Access in Windows Server® 2012 R2 and Windows Server® 2012 has a restrictive security model.</span></span> <span data-ttu-id="072ac-107">您必須明確授與使用者存取權，他們才能登入 Windows PowerShell Web 存取閘道並使用網頁型 Windows PowerShell 主控台。</span><span class="sxs-lookup"><span data-stu-id="072ac-107">Users must explicitly be granted access before they can sign in to the Windows PowerShell Web Access gateway and use the web-based Windows PowerShell console.</span></span>

-   [<span data-ttu-id="072ac-108">設定授權規則及站台安全性</span><span class="sxs-lookup"><span data-stu-id="072ac-108">Configuring authorization rules and site security</span></span>](#BKMK_auth)

-   [<span data-ttu-id="072ac-109">工作階段管理</span><span class="sxs-lookup"><span data-stu-id="072ac-109">Session management</span></span>](#BKMK_sesmgmt)


<span data-ttu-id="072ac-110">安裝 Windows PowerShell Web 存取並設定閘道之後，使用者就可以在瀏覽器中開啟登入頁面，但是必須等到 Windows PowerShell Web 存取系統管理員明確授與使用者存取權之後，才能登入。</span><span class="sxs-lookup"><span data-stu-id="072ac-110">After Windows PowerShell Web Access is installed and the gateway is configured, users can open the sign-in page in a browser, but they cannot sign in until the Windows PowerShell Web Access administrator grants users access explicitly.</span></span> <span data-ttu-id="072ac-111">您可以使用下表所述的 Windows PowerShell Cmdlet，來管理 Windows PowerShell Web 存取存取控制。</span><span class="sxs-lookup"><span data-stu-id="072ac-111">Windows PowerShell Web Access access control is managed by using the set of Windows PowerShell cmdlets described in the following table.</span></span> <span data-ttu-id="072ac-112">沒有適用於新增或管理授權規則的 GUI。</span><span class="sxs-lookup"><span data-stu-id="072ac-112">There is no comparable GUI for adding or managing authorization rules.</span></span> <span data-ttu-id="072ac-113">如需 Windows PowerShell Web 存取 Cmdlet 的詳細資訊，請參閱 Cmdlet 參考主題：[Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx) (Windows PowerShell Web 存取 Cmdlet)。</span><span class="sxs-lookup"><span data-stu-id="072ac-113">For more detailed information about Windows PowerShell Web Access cmdlets, see the cmdlet reference topics, [Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).</span></span>

<span data-ttu-id="072ac-114">系統管理員可以為「Windows PowerShell Web 存取」定義 0-*n* 個驗證規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-114">Administrators can define 0-*n* authentication rules for Windows PowerShell Web Access.</span></span> <span data-ttu-id="072ac-115">預設的安全性是用來限制動作而不是允許動作；零驗證規則表示沒有任何使用者有權存取任何內容。</span><span class="sxs-lookup"><span data-stu-id="072ac-115">The default security is restrictive rather than permissive; zero authentication rules means no users have access to anything.</span></span>

<span data-ttu-id="072ac-116">Windows Server 2012 R2 中的 Add-PswaAuthorizationRule 和 Test-PswaAuthorizationRule 包含可讓您從遠端電腦或從作用中的 Windows PowerShell Web 存取工作階段，新增和測試 Windows PowerShell Web 存取授權規則的 Credential 參數。</span><span class="sxs-lookup"><span data-stu-id="072ac-116">Add-PswaAuthorizationRule and Test-PswaAuthorizationRule in Windows Server 2012 R2 include a Credential parameter that allows you to add and test Windows PowerShell Web Access authorization rules from a remote computer, or from within an active Windows PowerShell Web Access session.</span></span> <span data-ttu-id="072ac-117">如同其他具有 Credential 參數的 Windows PowerShell Cmdlet，您可以將 PSCredential 物件指定為此參數的值。</span><span class="sxs-lookup"><span data-stu-id="072ac-117">As with other Windows PowerShell cmdlets that have a Credential parameter, you can specify a PSCredential object as the value of the parameter.</span></span> <span data-ttu-id="072ac-118">若要建立 PSCredential 物件且包含您要傳遞至遠端電腦的認證，請執行 [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="072ac-118">To create a PSCredential object that contains credentials you want to pass to a remote computer, run the [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx) cmdlet.</span></span>

<span data-ttu-id="072ac-119">Windows PowerShell Web 存取驗證規則是允許清單規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-119">Windows PowerShell Web Access authentication rules are whitelist rules.</span></span> <span data-ttu-id="072ac-120">每個規則都是使用者、目標電腦及指定目標電腦上特定 Windows PowerShell [工作階段設定](https://technet.microsoft.com/library/dd819508.aspx) (也稱為端點或 Runspace) 間允許連線的定義。</span><span class="sxs-lookup"><span data-stu-id="072ac-120">Each rule is a definition of an allowed connection between users, target computers, and particular Windows PowerShell [session configurations](https://technet.microsoft.com/library/dd819508.aspx) (also referred to as endpoints or runspaces) on specified target computers.</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="072ac-121"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 安全性注意事項 </span></span><span class="sxs-lookup"><span data-stu-id="072ac-121"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="072ac-122">只要一個規則為真，使用者就可以進行存取。</span><span class="sxs-lookup"><span data-stu-id="072ac-122">A user needs only one rule to be true to get access.</span></span> <span data-ttu-id="072ac-123">如果已為使用者授與某部電腦的存取權 (無論是完整語言存取或只能存取 Windows PowerShell 遠端管理 Cmdlet)，使用者都可以從網頁型主控台登入 (或跳躍) 至已與第一部目標電腦連線的其他電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-123">If a user is given access to one computer with either full language access or access only to Windows PowerShell remote management cmdlets, from the web-based console, the user can log on (or hop) to other computers that are connected to the first target computer.</span></span> <span data-ttu-id="072ac-124">設定 Windows PowerShell Web 存取最安全的方法就是只允許使用者存取受限制的工作階段設定 (也稱為端點或 Runspace)，讓他們能夠完成通常需要遠端執行的特定工作。</span><span class="sxs-lookup"><span data-stu-id="072ac-124">The most secure way to configure Windows PowerShell Web Access is to allow users access only to constrained session configurations (also called endpoints or runspaces) that allow them to accomplish specific tasks that they normally need to perform remotely.</span></span></p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="072ac-125">名稱</span><span class="sxs-lookup"><span data-stu-id="072ac-125">Name</span></span></p></th>
<th><p><span data-ttu-id="072ac-126">描述</span><span class="sxs-lookup"><span data-stu-id="072ac-126">Description</span></span></p></th>
<th><p><span data-ttu-id="072ac-127">參數</span><span class="sxs-lookup"><span data-stu-id="072ac-127">Parameters</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="072ac-128"><a href="https://technet.microsoft.com/library/jj592890.aspx">Add-PswaAuthorizationRule</a></span><span class="sxs-lookup"><span data-stu-id="072ac-128"><a href="https://technet.microsoft.com/library/jj592890.aspx">Add-PswaAuthorizationRule</a></span></span></p></td>
<td><p><span data-ttu-id="072ac-129">在 Windows PowerShell Web 存取授權規則集中新增授權規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-129">Adds a new authorization rule to the Windows PowerShell Web Access authorization rule set.</span></span></p></td>
<td><ul>
<li><p><span data-ttu-id="072ac-130">ComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="072ac-130">ComputerGroupName</span></span></p></li>
<li><p><span data-ttu-id="072ac-131">ComputerName</span><span class="sxs-lookup"><span data-stu-id="072ac-131">ComputerName</span></span></p></li>
<li><p><span data-ttu-id="072ac-132">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="072ac-132">ConfigurationName</span></span></p></li>
<li><p><span data-ttu-id="072ac-133">RuleName</span><span class="sxs-lookup"><span data-stu-id="072ac-133">RuleName</span></span></p></li>
<li><p><span data-ttu-id="072ac-134">UserGroupName</span><span class="sxs-lookup"><span data-stu-id="072ac-134">UserGroupName</span></span></p></li>
<li><p><span data-ttu-id="072ac-135">UserName</span><span class="sxs-lookup"><span data-stu-id="072ac-135">UserName</span></span></p></li>
<li><p><span data-ttu-id="072ac-136">認證 (Windows Server 2012 R2 和更新版本)</span><span class="sxs-lookup"><span data-stu-id="072ac-136">Credential (Windows Server 2012 R2 and later)</span></span></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="072ac-137"><a href="https://technet.microsoft.com/library/jj592893.aspx">Remove-PswaAuthorizationRule</a></span><span class="sxs-lookup"><span data-stu-id="072ac-137"><a href="https://technet.microsoft.com/library/jj592893.aspx">Remove-PswaAuthorizationRule</a></span></span></p></td>
<td><p><span data-ttu-id="072ac-138">從 Windows PowerShell Web 存取中移除指定的授權規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-138">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span></p></td>
<td><ul>
<li><p><span data-ttu-id="072ac-139">Id</span><span class="sxs-lookup"><span data-stu-id="072ac-139">Id</span></span></p></li>
<li><p><span data-ttu-id="072ac-140">RuleName</span><span class="sxs-lookup"><span data-stu-id="072ac-140">RuleName</span></span></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="072ac-141"><a href="https://technet.microsoft.com/library/jj592891.aspx">Get-PswaAuthorizationRule</a></span><span class="sxs-lookup"><span data-stu-id="072ac-141"><a href="https://technet.microsoft.com/library/jj592891.aspx">Get-PswaAuthorizationRule</a></span></span></p></td>
<td><p><span data-ttu-id="072ac-142">傳回一組 Windows PowerShell Web 存取授權規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-142">Returns a set of Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="072ac-143">如果未使用任何參數，Cmdlet 會傳回所有規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-143">When it is used without parameters, the cmdlet returns all rules.</span></span></p></td>
<td><ul>
<li><p><span data-ttu-id="072ac-144">Id</span><span class="sxs-lookup"><span data-stu-id="072ac-144">Id</span></span></p></li>
<li><p><span data-ttu-id="072ac-145">RuleName</span><span class="sxs-lookup"><span data-stu-id="072ac-145">RuleName</span></span></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="072ac-146"><a href="https://technet.microsoft.com/library/jj592892.aspx">Test-PswaAuthorizationRule</a></span><span class="sxs-lookup"><span data-stu-id="072ac-146"><a href="https://technet.microsoft.com/library/jj592892.aspx">Test-PswaAuthorizationRule</a></span></span></p></td>
<td><p><span data-ttu-id="072ac-147">評估授權規則以判斷特定使用者、電腦或工作階段設定存取要求是否已經過授權。</span><span class="sxs-lookup"><span data-stu-id="072ac-147">Evaluates authorization rules to determine if a specific user, computer, or session configuration access request is authorized.</span></span> <span data-ttu-id="072ac-148">根據預設，如果沒有加入參數，Cmdlet 會評估所有的授權規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-148">By default, if no parameters are added, the cmdlet evaluates all authorization rules.</span></span> <span data-ttu-id="072ac-149">系統管理員可以新增參數，指定授權規則或規則子集來進行測試。</span><span class="sxs-lookup"><span data-stu-id="072ac-149">By adding parameters, administrators can specify an authorization rule or a subset of rules to test.</span></span></p></td>
<td><ul>
<li><p><span data-ttu-id="072ac-150">ComputerName</span><span class="sxs-lookup"><span data-stu-id="072ac-150">ComputerName</span></span></p></li>
<li><p><span data-ttu-id="072ac-151">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="072ac-151">ConfigurationName</span></span></p></li>
<li><p><span data-ttu-id="072ac-152">RuleName</span><span class="sxs-lookup"><span data-stu-id="072ac-152">RuleName</span></span></p></li>
<li><p><span data-ttu-id="072ac-153">UserName</span><span class="sxs-lookup"><span data-stu-id="072ac-153">UserName</span></span></p></li>
<li><p><span data-ttu-id="072ac-154">認證 (Windows Server 2012 R2 和更新版本)</span><span class="sxs-lookup"><span data-stu-id="072ac-154">Credential (Windows Server 2012 R2 and later)</span></span></p></li>
</ul></td>
</tr>
</tbody>
</table>

<span data-ttu-id="072ac-155">上述 Cmdlet 可建立一組存取規則，用來為 Windows PowerShell Web 存取閘道上的使用者授與權限。</span><span class="sxs-lookup"><span data-stu-id="072ac-155">The preceding cmdlets create a set of access rules which are used to authorize a user on the Windows PowerShell Web Access gateway.</span></span> <span data-ttu-id="072ac-156">這些規則與目的地電腦上的存取控制清單 (ACL) 不同，且可以為 Web 存取提供額外的安全性。</span><span class="sxs-lookup"><span data-stu-id="072ac-156">The rules are different from the access control lists (ACLs) on the destination computer, and provide an additional layer of security for web access.</span></span> <span data-ttu-id="072ac-157">下節將有更詳細的安全性說明。</span><span class="sxs-lookup"><span data-stu-id="072ac-157">More details about security are described in the following section.</span></span>

<span data-ttu-id="072ac-158">如果使用者無法通過上述任何安全性階層，他們會在瀏覽器視窗收到一般「拒絕存取」訊息。</span><span class="sxs-lookup"><span data-stu-id="072ac-158">If users cannot pass any of the preceding security layers, they receive a generic “access denied” message in their browser windows.</span></span> <span data-ttu-id="072ac-159">雖然閘道伺服器會記錄安全性細節，但是不會對一般使用者顯示他們通過多少安全性階層，或在哪一個階層發生登入或驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="072ac-159">Although security details are logged on the gateway server, end users are not shown information about how many security layers they passed, or at which layer the sign-in or authentication failure occurred.</span></span>

<span data-ttu-id="072ac-160">如需設定授權規則的詳細資訊，請參閱本主題中的[設定授權規則](#BKMK_configrules)。</span><span class="sxs-lookup"><span data-stu-id="072ac-160">For more information about configuring authorization rules, see [Configuring authorization rules](#BKMK_configrules) in this topic.</span></span>

<a href="" id="BKMK_sec"></a>
###

<span data-ttu-id="072ac-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">安全性</span></a></span><span class="sxs-lookup"><span data-stu-id="072ac-161"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Security</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="072ac-162">Windows PowerShell Web 存取安全性模型在網頁型主控台的一般使用者與目標電腦之間有四個階層。</span><span class="sxs-lookup"><span data-stu-id="072ac-162">The Windows PowerShell Web Access security model has four layers between an end user of the web-based console, and a target computer.</span></span> <span data-ttu-id="072ac-163">Windows PowerShell Web 存取系統管理員可以在 IIS 管理員主控台中，透過其他設定來增加安全性階層。</span><span class="sxs-lookup"><span data-stu-id="072ac-163">Windows PowerShell Web Access administrators can add security layers through additional configuration in the IIS Manager console.</span></span> <span data-ttu-id="072ac-164">如需在 IIS 管理員主控台中保護網站安全的詳細資訊，請參閱[設定網頁伺服器安全性 (IIS 7)](https://technet.microsoft.com/library/cc731278(v=ws.10).aspx)。</span><span class="sxs-lookup"><span data-stu-id="072ac-164">For more information about securing websites in the IIS Manager console, see [Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278(v=ws.10).aspx).</span></span> <span data-ttu-id="072ac-165">如需 IIS 最佳做法及防止拒絕服務攻擊的詳細資訊，請參閱[防止 DoS/拒絕服務攻擊的最佳做法](https://technet.microsoft.com/library/cc750213.aspx)。</span><span class="sxs-lookup"><span data-stu-id="072ac-165">For more information about IIS best practices and preventing denial-of-service attacks, see [Best Practices for Preventing DoS/Denial of Service Attacks](https://technet.microsoft.com/library/cc750213.aspx).</span></span> <span data-ttu-id="072ac-166">系統管理員也可以購買並安裝其他零售的驗證軟體。</span><span class="sxs-lookup"><span data-stu-id="072ac-166">An administrator can also buy and install additional, retail authentication software.</span></span>

<span data-ttu-id="072ac-167">下表說明一般使用者與目標電腦之間的四個安全性階層。</span><span class="sxs-lookup"><span data-stu-id="072ac-167">The following table describes the four layers of security between end users and target computers.</span></span>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="072ac-168">順序</span><span class="sxs-lookup"><span data-stu-id="072ac-168">Order</span></span></p></th>
<th><p><span data-ttu-id="072ac-169">階層</span><span class="sxs-lookup"><span data-stu-id="072ac-169">Layer</span></span></p></th>
<th><p><span data-ttu-id="072ac-170">描述</span><span class="sxs-lookup"><span data-stu-id="072ac-170">Description</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="072ac-171">1</span><span class="sxs-lookup"><span data-stu-id="072ac-171">1</span></span></p></td>
<td><p><span data-ttu-id="072ac-172">網頁伺服器 (IIS) 安全性功能，例如用戶端憑證驗證</span><span class="sxs-lookup"><span data-stu-id="072ac-172">Web Server (IIS) security features, such as client certificate authentication</span></span></p></td>
<td><p><span data-ttu-id="072ac-173">Windows PowerShell Web 存取使用者一律必須提供使用者名稱及密碼，才能在閘道上驗證他們的帳戶。</span><span class="sxs-lookup"><span data-stu-id="072ac-173">Windows PowerShell Web Access users must always provide a user name and password to authenticate their accounts on the gateway.</span></span> <span data-ttu-id="072ac-174">不過，Windows PowerShell Web 存取系統管理員也可以開啟或關閉選擇性的用戶端憑證驗證 (請參閱<a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">安裝和使用 Windows PowerShell Web 存取</a>中的＜使用 IIS 管理員在現有的網站中設定閘道＞的步驟 10)。</span><span class="sxs-lookup"><span data-stu-id="072ac-174">However, Windows PowerShell Web Access administrators can also turn optional client certificate authentication on or off (see step 10 of “To use IIS Manager to configure the gateway in an existing website” in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a>).</span></span> <span data-ttu-id="072ac-175">選擇性用戶端憑證功能要求一般使用者除了使用者名稱及密碼之外還需具備有效的用戶端憑證，而這也是網頁伺服器 (IIS) 設定的一部份。</span><span class="sxs-lookup"><span data-stu-id="072ac-175">The optional client certificate feature requires end users to have a valid client certificate, in addition to their user names and passwords, and is part of Web Server (IIS) configuration.</span></span> <span data-ttu-id="072ac-176">啟用用戶端憑證層時，Windows PowerShell Web 存取登入頁面會提示使用者提供有效的憑證，才能評估他們的登入認證。</span><span class="sxs-lookup"><span data-stu-id="072ac-176">When the client certificate layer is enabled, the Windows PowerShell Web Access sign-in page prompts users to provide valid certificates before their sign-in credentials are evaluated.</span></span> <span data-ttu-id="072ac-177">用戶端憑證驗證會自動檢查用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="072ac-177">Client certificate authentication automatically checks for the client certificate.</span></span></p>
<p><span data-ttu-id="072ac-178">如果找不到有效的憑證，Windows PowerShell Web 存取會通知使用者，讓使用者可以提供憑證。</span><span class="sxs-lookup"><span data-stu-id="072ac-178">If a valid certificate is not found, Windows PowerShell Web Access informs users, so they can provide the certificate.</span></span> <span data-ttu-id="072ac-179">如果找到有效的用戶端憑證，Windows PowerShell Web 存取會為使用者開啟登入頁面，讓他們提供使用者名稱及密碼。</span><span class="sxs-lookup"><span data-stu-id="072ac-179">If a valid client certificate is found, Windows PowerShell Web Access opens the sign-in page for users to provide their user names and passwords.</span></span></p>
<p><span data-ttu-id="072ac-180">這是網頁伺服器 (IIS) 提供額外安全性設定的範例。</span><span class="sxs-lookup"><span data-stu-id="072ac-180">This is one example of additional security settings that are offered by Web Server (IIS).</span></span> <span data-ttu-id="072ac-181">如需其他 IIS 安全性功能的詳細資訊，請參閱<a href="https://technet.microsoft.com/library/cc731278(ws.10).aspx">設定網頁伺服器安全性 (IIS 7)</a>。</span><span class="sxs-lookup"><span data-stu-id="072ac-181">For more information about other IIS security features, see <a href="https://technet.microsoft.com/library/cc731278(ws.10).aspx">Configure Web Server Security (IIS 7)</a>.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="072ac-182">2</span><span class="sxs-lookup"><span data-stu-id="072ac-182">2</span></span></p></td>
<td><p><span data-ttu-id="072ac-183">Windows PowerShell Web 存取表單型閘道驗證</span><span class="sxs-lookup"><span data-stu-id="072ac-183">Windows PowerShell Web Access forms-based gateway authentication</span></span></p></td>
<td><p><span data-ttu-id="072ac-184">Windows PowerShell Web 存取登入頁面會要求一組認證 (使用者名稱及密碼)，並提供選項，讓使用者為目標電腦提供不同的認證。</span><span class="sxs-lookup"><span data-stu-id="072ac-184">The Windows PowerShell Web Access sign-in page requires a set of credentials (user name and password) and offers users the option of providing different credentials for the target computer.</span></span> <span data-ttu-id="072ac-185">如果使用者沒有提供替代認證，就會使用連線閘道的主要使用者名稱及密碼來連線目標電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-185">If the user does not provide alternate credentials, the primary user name and password that are used to connect to the gateway are also used to connect to the target computer.</span></span></p>
<p><span data-ttu-id="072ac-186">所需的認證會在 Windows PowerShell Web 存取閘道上進行驗證。</span><span class="sxs-lookup"><span data-stu-id="072ac-186">The required credentials are authenticated on the Windows PowerShell Web Access gateway.</span></span> <span data-ttu-id="072ac-187">這些認證必須是本機 Windows PowerShell Web 存取閘道伺服器上或 Active Directory® 中的有效使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="072ac-187">These credentials must be valid user accounts on either the local Windows PowerShell Web Access gateway server, or in Active Directory®.</span></span></p>
<p><span data-ttu-id="072ac-188">當使用者通過閘道上的驗證之後，Windows PowerShell Web 存取會檢查授權規則，以確定使用者是否有權存取要求的目標電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-188">After a user is authenticated at the gateway, Windows PowerShell Web Access checks authorization rules to verify if the user has access to the requested target computer.</span></span> <span data-ttu-id="072ac-189">成功授權之後，使用者的認證就會傳送到目標電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-189">After successful authorization, the user’s credentials are passed along to the target computer.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="072ac-190">3</span><span class="sxs-lookup"><span data-stu-id="072ac-190">3</span></span></p></td>
<td><p><span data-ttu-id="072ac-191">Windows PowerShell Web 存取授權規則</span><span class="sxs-lookup"><span data-stu-id="072ac-191">Windows PowerShell Web Access authorization rules</span></span></p></td>
<td><p><span data-ttu-id="072ac-192">當使用者通過閘道上的驗證之後，Windows PowerShell Web 存取會檢查授權規則，以確定使用者是否有權存取要求的目標電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-192">After a user is authenticated at the gateway, Windows PowerShell Web Access checks authorization rules to verify if the user has access to the requested target computer.</span></span> <span data-ttu-id="072ac-193">成功授權之後，使用者的認證就會傳送到目標電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-193">After successful authorization, the user’s credentials are passed along to the target computer.</span></span></p>
<p><span data-ttu-id="072ac-194">只有在使用者通過閘道驗證之後，目標電腦驗證使用者之前，才會評估這些規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-194">These rules are evaluated only after a user has been authenticated by the gateway, and before a user can be authenticated on a target computer.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="072ac-195">4</span><span class="sxs-lookup"><span data-stu-id="072ac-195">4</span></span></p></td>
<td><p><span data-ttu-id="072ac-196">目標驗證及授權規則</span><span class="sxs-lookup"><span data-stu-id="072ac-196">Target authentication and authorization rules</span></span></p></td>
<td><p><span data-ttu-id="072ac-197">Windows PowerShell Web 存取的最終安全性階層是目標電腦本身的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="072ac-197">The final layer of security for Windows PowerShell Web Access is the target computer’s own security configuration.</span></span> <span data-ttu-id="072ac-198">使用者必須在目標電腦上及 Windows PowerShell Web 存取授權規則中設定適當的存取權，才能執行 Windows PowerShell 網頁型主控台，透過 Windows PowerShell Web 存取來影響目標電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-198">Users must have the appropriate access rights configured on the target computer, and also in the Windows PowerShell Web Access authorization rules, to run a Windows PowerShell web-based console that affects a target computer through Windows PowerShell Web Access.</span></span></p>
<p><span data-ttu-id="072ac-199">這個階層提供的安全性機制，與使用者嘗試在 Windows PowerShell 內執行 <strong>Enter-PSSession</strong> 或 <strong>New-PSSession</strong> Cmdlet，以建立目標電腦的遠端 Windows PowerShell 工作階段時所用的評估連線嘗試安全性機制相同。</span><span class="sxs-lookup"><span data-stu-id="072ac-199">This layer offers the same security mechanisms that would evaluate connection attempts if users tried to create a remote Windows PowerShell session to a target computer from within Windows PowerShell by running the <strong>Enter-PSSession</strong> or <strong>New-PSSession</strong> cmdlets.</span></span></p>
<p><span data-ttu-id="072ac-200">根據預設，Windows PowerShell Web 存取在閘道及目標電腦上都會使用主要的使用者名稱和密碼進行驗證。</span><span class="sxs-lookup"><span data-stu-id="072ac-200">By default, Windows PowerShell Web Access uses the primary user name and password for authentication on both the gateway and the target computer.</span></span> <span data-ttu-id="072ac-201">網頁型登入頁面會在標題為<strong>選用連線設定</strong>的區段中提供選項，讓使用者可視需要為目標電腦提供不同的認證。</span><span class="sxs-lookup"><span data-stu-id="072ac-201">The web-based sign-in page, in a section titled <strong>Optional connection settings</strong>, offers users the option of providing different credentials for the target computer, if they are required.</span></span> <span data-ttu-id="072ac-202">如果使用者沒有提供替代認證，就會使用連線閘道的主要使用者名稱及密碼來連線目標電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-202">If the user does not provide alternate credentials, the primary user name and password that are used to connect to the gateway are also used to connect to the target computer.</span></span></p>
<p><span data-ttu-id="072ac-203">授權規則可用來允許使用者存取特定工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="072ac-203">Authorization rules can be used to allow users access to a particular session configuration.</span></span> <span data-ttu-id="072ac-204">您可以為 Windows PowerShell Web 存取建立受限制的 Runspace 或工作階段設定，並允許特定使用者在登入 Windows PowerShell Web 存取時只能連線到特定的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="072ac-204">You can create restricted runspaces or session configurations for Windows PowerShell Web Access, and allow specific users to connect only to specific session configurations when they sign in to Windows PowerShell Web Access.</span></span> <span data-ttu-id="072ac-205">您可以使用存取控制清單 (ACL) 來判斷哪些使用者有權存取特定端點，然後使用本節描述的授權規則進一步限制特定使用者組的端點存取權。</span><span class="sxs-lookup"><span data-stu-id="072ac-205">You can use access control lists (ACLs) to determine which users have access to specific endpoints, and further restrict access to the endpoint for a specific set of users by using authorization rules described in this section.</span></span> <span data-ttu-id="072ac-206">如需受限制的 Runspace 詳細資訊，請參閱 MSDN 上的<a href="https://msdn.microsoft.com/library/windows/desktop/ee706589.aspx">受限制的 Runspace</a>。</span><span class="sxs-lookup"><span data-stu-id="072ac-206">For more information about restricted runspaces, see <a href="https://msdn.microsoft.com/library/windows/desktop/ee706589.aspx">Constrained Runspaces</a> on MSDN.</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="072ac-207">

<a href="" id="BKMK_configrules"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">設定授權規則</span></a></span><span class="sxs-lookup"><span data-stu-id="072ac-207">

<a href="" id="BKMK_configrules"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configuring authorization rules</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="072ac-208">系統管理員很可能想要針對 Windows PowerShell Web 存取使用者，將已在其環境中定義的同一個授權規則套用到 Windows PowerShell 遠端管理。</span><span class="sxs-lookup"><span data-stu-id="072ac-208">Administrators likely want the same authorization rule for Windows PowerShell Web Access users that is already defined in their environment for Windows PowerShell remote management.</span></span> <span data-ttu-id="072ac-209">本節的第一個程序描述如何新增授與一位使用者存取權、登入以管理一部電腦，以及單一工作階段設定內的安全性規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-209">The first procedure in this section describes how to add a secure authorization rule that grants access to one user, signing in to manage one computer, and within a single session configuration.</span></span> <span data-ttu-id="072ac-210">第二個程序描述如何移除不再需要的授權規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-210">The second procedure describes how to remove an authorization rule that is no longer needed.</span></span>

<span data-ttu-id="072ac-211">如果您打算使用自訂工作階段設定來允許特定使用者只能在 Windows PowerShell Web 存取中受限制的 Runspace 內工作，請先建立您的自訂工作階段設定，然後再新增參考這些設定的授權規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-211">If you plan to use custom session configurations to allow specific users to work only within restricted runspaces in Windows PowerShell Web Access, create your custom session configurations before you add authorization rules that refer to them.</span></span> <span data-ttu-id="072ac-212">您不能使用 Windows PowerShell Web 存取 Cmdlet 來建立自訂的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="072ac-212">You cannot use the Windows PowerShell Web Access cmdlets to create custom session configurations.</span></span> <span data-ttu-id="072ac-213">如需建立自訂工作階段設定的詳細資訊，請參閱 MSDN 上的 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx)。</span><span class="sxs-lookup"><span data-stu-id="072ac-213">For more information about creating custom session configurations, see [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

<span data-ttu-id="072ac-214">Windows PowerShell Web 存取 Cmdlet 支援一個萬用字元，也就是星號 ( \* )。</span><span class="sxs-lookup"><span data-stu-id="072ac-214">Windows PowerShell Web Access cmdlets support one wildcard character, an asterisk ( \* ).</span></span> <span data-ttu-id="072ac-215">不支援在字串中使用萬用字元；每一個屬性 (使用者、電腦或工作階段設定) 使用單一星號。</span><span class="sxs-lookup"><span data-stu-id="072ac-215">Wildcard characters within strings are not supported; use a single asterisk per property (users, computers, or session configurations).</span></span>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="072ac-216"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></span><span class="sxs-lookup"><span data-stu-id="072ac-216"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="072ac-217">如需更多您可以使用授權規則來授與使用者存取權及協助保護 Windows PowerShell Web 存取環境的方法，請參閱本主題中的<a href="#BKMK_others">其他授權規則案例</a>。</span><span class="sxs-lookup"><span data-stu-id="072ac-217">For more ways you can use authorization rules to grant access to users and help secure the Windows PowerShell Web Access environment, see <a href="#BKMK_others">Other authorization rule scenario examples</a> in this topic.</span></span></p></td>
</tr>
</tbody>
</table>

#### <a name="to-add-a-restrictive-authorization-rule"></a><span data-ttu-id="072ac-218">新增限制性授權規則</span><span class="sxs-lookup"><span data-stu-id="072ac-218">To add a restrictive authorization rule</span></span>

1.  <span data-ttu-id="072ac-219">執行下列其中一個動作，使用提高的使用者權限開啟 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="072ac-219">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span>

    -   <span data-ttu-id="072ac-220">在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="072ac-220">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="072ac-221">在 Windows **[開始]** 畫面上，以滑鼠右鍵按一下 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="072ac-221">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="072ac-222"><span class="label">使用工作階段設定來限制使用者存取的選擇性步驟：</span>確認您要在規則中使用的工作階段設定已經存在。</span><span class="sxs-lookup"><span data-stu-id="072ac-222"><span class="label">Optional step for restricting user access by using session configurations:</span> Verify that session configurations that you want to use in your rules already exist.</span></span> <span data-ttu-id="072ac-223">如果尚未建立這些設定，請使用 MSDN 上 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) 中建立工作階段設定的指示。</span><span class="sxs-lookup"><span data-stu-id="072ac-223">If they have not yet been created, use instructions for creating session configurations in [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) on MSDN.</span></span>

3.  <span data-ttu-id="072ac-224">輸入下列程式碼，然後按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="072ac-224">Type the following, and then press **Enter**.</span></span>

    [<span data-ttu-id="072ac-225">Copy</span><span class="sxs-lookup"><span data-stu-id="072ac-225">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_1079478f-cd51-4d35-8022-4b532a9d57a4'); "複製到剪貼簿。")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    <span data-ttu-id="072ac-226">這個授權規則允許特定使用者存取網路上他們通常有權存取的一部電腦，以及該使用者在一般編寫指令碼及 Cmdlet 範圍內的特定工作階段設定存取權。</span><span class="sxs-lookup"><span data-stu-id="072ac-226">This authorization rule allows a specific user access to one computer on the network to which they typically have access, with access to a specific session configuration that is scoped to the user’s typical scripting and cmdlet needs.</span></span> <span data-ttu-id="072ac-227">在下列範例中，<span class="code">Contoso</span> 網域中名為 <span class="code">JSmith</span> 的使用者會被授與管理電腦 <span class="code">Contoso_214</span> 的存取權，並使用名為 <span class="code">NewAdminsOnly</span> 的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="072ac-227">In the following example, a user named <span class="code">JSmith</span> in the <span class="code">Contoso</span> domain is granted access to manage the computer <span class="code">Contoso_214</span>, and use a session configuration named <span class="code">NewAdminsOnly</span>.</span></span>

    [<span data-ttu-id="072ac-228">Copy</span><span class="sxs-lookup"><span data-stu-id="072ac-228">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4e760377-e401-4ef4-988f-7a0aec1b2a90'); "複製到剪貼簿。")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  <span data-ttu-id="072ac-229">執行 **Get-PswaAuthorizationRule** Cmdlet 或 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;，確認已建立規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-229">Verify that the rule has been created by running either the **Get-PswaAuthorizationRule** cmdlet, or **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt;.</span></span> <span data-ttu-id="072ac-230">例如，**Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**。</span><span class="sxs-lookup"><span data-stu-id="072ac-230">For example, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.</span></span>

#### <a name="to-remove-an-authorization-rule"></a><span data-ttu-id="072ac-231">移除授權規則</span><span class="sxs-lookup"><span data-stu-id="072ac-231">To remove an authorization rule</span></span>

1.  <span data-ttu-id="072ac-232">如果尚未開啟 Windows PowerShell 工作階段，請參閱本節中[新增非限制性授權規則](#BKMK_arar)的步驟 1。</span><span class="sxs-lookup"><span data-stu-id="072ac-232">If a Windows PowerShell session is not already open, see step 1 of [To add a restrictive authorization rule](#BKMK_arar) in this section.</span></span>

2.  <span data-ttu-id="072ac-233">輸入下列資訊，然後按下 **Enter**，其中 *rule ID* 代表您想要移除之規則的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="072ac-233">Type the following, and then press **Enter**, where *rule ID* represents the unique ID number of the rule that you want to remove.</span></span>

    [<span data-ttu-id="072ac-234">Copy</span><span class="sxs-lookup"><span data-stu-id="072ac-234">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0daef66d-0ecf-47fb-a8a0-d4dbceb8409d'); "複製到剪貼簿。")

        Remove-PswaAuthorizationRule -ID <rule ID>

    <span data-ttu-id="072ac-235">或者，如果您不知道識別碼，但是知道您想要移除之規則的好記名稱，您可以取得規則的名稱，並將它傳送到 <span class="code">Remove-PswaAuthorizationRule</span> Cmdlet 來移除規則，如下列範例所示：Get-PswaAuthorizationRule -RuleName &lt;*rule name*&gt; | Remove-PswaAuthorizationRule。</span><span class="sxs-lookup"><span data-stu-id="072ac-235">Alternatively, if you do not know the ID number, but know the friendly name of the rule you want to remove, you can get the name of the rule, and pipe it to the <span class="code">Remove-PswaAuthorizationRule</span> cmdlet to remove the rule, as shown in the following example: Get-PswaAuthorizationRule -RuleName &lt;*rule name*&gt; | Remove-PswaAuthorizationRule.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="072ac-236"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></span><span class="sxs-lookup"><span data-stu-id="072ac-236"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="072ac-237">系統不會提示您確認是否要刪除指定的授權規則；當您按下 <strong>Enter</strong> 時就會刪除該規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-237">You are not prompted to confirm whether you want to delete the specified authorization rule; the rule is deleted when you press <strong>Enter</strong>.</span></span> <span data-ttu-id="072ac-238">執行 <strong>Remove-PswaAuthorizationRule</strong> Cmdlet 之前，請先確定您要移除該授權規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-238">Be sure that you want to remove the authorization rule before running the <strong>Remove-PswaAuthorizationRule</strong> cmdlet.</span></span></p></td>
    </tr>
    </tbody>
    </table><span data-ttu-id="072ac-239">

<a href="" id="BKMK_others"></a>
####

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">其他授權規則案例範例</span></a></span><span class="sxs-lookup"><span data-stu-id="072ac-239">

<a href="" id="BKMK_others"></a>
####

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Other authorization rule scenario examples</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="072ac-240">每一個 Windows PowerShell 工作階段都會使用一個工作階段設定；如果未針對工作階段指定這類設定，Windows PowerShell 就會使用預設的內建 Windows PowerShell 工作階段設定 (稱為 Microsoft.PowerShell)。</span><span class="sxs-lookup"><span data-stu-id="072ac-240">Every Windows PowerShell session uses a session configuration; if one is not specified for a session, Windows PowerShell uses the default, built-in Windows PowerShell session configuration, called Microsoft.PowerShell.</span></span> <span data-ttu-id="072ac-241">預設的工作階段設定包含電腦可用的所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="072ac-241">The default session configuration includes all cmdlets that are available on a computer.</span></span> <span data-ttu-id="072ac-242">系統管理員可以使用受限制的 Runspace (一般使用者可以執行之有限範圍內的 Cmdlet 及工作) 來定義工作階段設定，以便限制所有電腦的存取權。</span><span class="sxs-lookup"><span data-stu-id="072ac-242">Administrators can restrict access to all computers by defining a session configuration with a restricted runspace (a limited range of cmdlets and tasks that their end users could perform).</span></span> <span data-ttu-id="072ac-243">如果已為使用者授與某部電腦的存取權 (無論完整的語言存取權或只能存取 Windows PowerShell 遠端管理 Cmdlet)，該使用者就能連線到已與第一部電腦連線的其他電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-243">A user who is granted access to one computer with either full language access or only the Windows PowerShell remote management cmdlets can connect to other computers that are connected to the first computer.</span></span> <span data-ttu-id="072ac-244">定義受限制的 Runspace 可防止使用者從他們允許的 Windows PowerShell Runspace 存取其他電腦，而且還可以提升 Windows PowerShell Web 存取環境的安全性。</span><span class="sxs-lookup"><span data-stu-id="072ac-244">Defining a restricted runspace can prevent users from accessing other computers from their allowed Windows PowerShell runspace, and improves the security of your Windows PowerShell Web Access environment.</span></span> <span data-ttu-id="072ac-245">工作階段設定可以散佈 (使用群組原則) 到系統管理員想要透過 Windows PowerShell Web 存取來存取的所有電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-245">The session configuration can be distributed (by using Group Policy) to all computers that administrators want to make accessible through Windows PowerShell Web Access.</span></span> <span data-ttu-id="072ac-246">如需工作階段設定的詳細資訊，請參閱 [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)。</span><span class="sxs-lookup"><span data-stu-id="072ac-246">For more information about session configurations, see [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx).</span></span> <span data-ttu-id="072ac-247">下面是這個案例的一些範例。</span><span class="sxs-lookup"><span data-stu-id="072ac-247">The following are some examples of this scenario.</span></span>

-   <span data-ttu-id="072ac-248">系統管理員會建立一個含有受限制 Runspace 的端點，稱為 **PswaEndpoint**。</span><span class="sxs-lookup"><span data-stu-id="072ac-248">An administrator creates an endpoint, called **PswaEndpoint**, with a restricted runspace.</span></span> <span data-ttu-id="072ac-249">然後，系統管理員會建立 **\*,\*,PswaEndpoint** 規則，並將該端點散佈到其他電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-249">Then, the administrator creates a rule, **\*,\*,PswaEndpoint**, and distributes the endpoint to other computers.</span></span> <span data-ttu-id="072ac-250">這個規則允許所有使用者存取具有端點 **PswaEndpoint** 的所有電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-250">The rule allows all users to access all computers with the endpoint **PswaEndpoint**.</span></span> <span data-ttu-id="072ac-251">如果這是規則集中定義的唯一授權規則，就無法存取不具該端點的電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-251">If this is the only authorization rule defined in the rule set, computers without that endpoint would not be accessible.</span></span>

-   <span data-ttu-id="072ac-252">系統管理員建立了含有受限制 Runspace 的端點 **PswaEndpoint**，並想要限制特定使用者的存取權。</span><span class="sxs-lookup"><span data-stu-id="072ac-252">The administrator created an endpoint with a restricted runspace called **PswaEndpoint**,and wants to restrict access to specific users.</span></span> <span data-ttu-id="072ac-253">系統管理員建立了一個名為 **Level1Support** 的使用者群組，並定義下列規則：**Level1Support,\*,PswaEndpoint**。</span><span class="sxs-lookup"><span data-stu-id="072ac-253">The administrator creates a group of users called **Level1Support**, and defines the following rule: **Level1Support,\*,PswaEndpoint**.</span></span> <span data-ttu-id="072ac-254">這個規則可讓 **Level1Support** 群組中的所有使用者有權存取具有 **PswaEndpoint** 設定的所有電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-254">The rule grants any users in the group **Level1Support** access to all computers with the **PswaEndpoint** configuration.</span></span> <span data-ttu-id="072ac-255">同樣也可以限制特定電腦組的存取權。</span><span class="sxs-lookup"><span data-stu-id="072ac-255">Similarly, access can be restricted to a specific set of computers.</span></span>

-   <span data-ttu-id="072ac-256">有些系統管理員會提供比其他使用者更多的存取權給特定使用者。</span><span class="sxs-lookup"><span data-stu-id="072ac-256">Some administrators provide certain users more access than others.</span></span> <span data-ttu-id="072ac-257">例如，系統管理員建立兩個使用者群組 **Admins** 和 **BasicSupport**。</span><span class="sxs-lookup"><span data-stu-id="072ac-257">For example, an administrator creates two user groups, **Admins** and **BasicSupport**.</span></span> <span data-ttu-id="072ac-258">系統管理員還會建立含有受限制 Runspace 的端點 **PswaEndpoint**，並定義下列兩個規則：**Admins,\*,\*** 和 **BasicSupport,\*,PswaEndpoint**。</span><span class="sxs-lookup"><span data-stu-id="072ac-258">The administrator also creates an endpoint with a restricted runspace called **PswaEndpoint**, and defines the following two rules: **Admins,\*,\*** and **BasicSupport,\*,PswaEndpoint**.</span></span> <span data-ttu-id="072ac-259">第一個規則可讓 **Admin** 群組中的所有使用者存取所有電腦，而第二個規則只能讓 **BasicSupport** 群組中的所有使用者存取具有 **PswaEndpoint** 的電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-259">The first rule provides all users in the **Admin** group access to all computers, and the second rule provides all users in the **BasicSupport** group access only to those computers with **PswaEndpoint**.</span></span>

-   <span data-ttu-id="072ac-260">某系統管理員已經設定私人測試環境，且想要讓所有已獲授權的網路使用者在網路上存取他們通常可以存取的所有電腦，以及存取他們通常可以存取的所有工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="072ac-260">An administrator has set up a private test environment, and wants to allow all authorized network users access to all computers on the network to which they typically have access, with access to all session configurations to which they typically have access.</span></span> <span data-ttu-id="072ac-261">因為這是私人測試環境，所以系統管理員建立的授權規則並不安全。</span><span class="sxs-lookup"><span data-stu-id="072ac-261">Because this is a private test environment, the administrator creates an authorization rule that is not secure.</span></span> <span data-ttu-id="072ac-262">系統管理員會執行 <span class="code">Add-PswaAuthorizationRule\* \* \*</span> Cmdlet，其中使用萬用字元 **\*** 來代表所有使用者、所有電腦及所有設定。</span><span class="sxs-lookup"><span data-stu-id="072ac-262">The administrator runs the cmdlet <span class="code">Add-PswaAuthorizationRule \* \* \*</span>, which uses the wildcard character **\*** to represent all users, all computers, and all configurations.</span></span> <span data-ttu-id="072ac-263">此規則相當於下列內容︰<span class="code">Add-PswaAuthorizationRule -UserName \* -ComputerName \* -ConfigurationName \*</span>。</span><span class="sxs-lookup"><span data-stu-id="072ac-263">This rule is the equivalent of the following: <span class="code">Add-PswaAuthorizationRule -UserName \* -ComputerName \* -ConfigurationName \*</span>.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="072ac-264"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 安全性注意事項 </span></span><span class="sxs-lookup"><span data-stu-id="072ac-264"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Security Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="072ac-265">如需安全的環境，不建議使用這個規則，並略過 Windows PowerShell Web 存取所提供的授權規則安全性階層。</span><span class="sxs-lookup"><span data-stu-id="072ac-265">This rule is not recommended in a secure environment, and bypasses the authorization rule layer of security provided by Windows PowerShell Web Access.</span></span></p></td>
    </tr>
    </tbody>
    </table>

-   <span data-ttu-id="072ac-266">系統管理員必須讓使用者在包含工作群組和網域的環境中連線到目標電腦，在這種環境中，工作群組電腦偶爾會用來連線到網域的目標電腦，而網域中的電腦偶爾也會用來連線工作群組中的目標電腦。</span><span class="sxs-lookup"><span data-stu-id="072ac-266">An administrator must allow users to connect to target computers in an environment that includes both workgroups and domains, where workgroup computers are occasionally used to connect to target computers in domains, and computers in domains are occasionally used to connect to target computers in workgroups.</span></span> <span data-ttu-id="072ac-267">系統管理員在工作群組中有閘道伺服器 *PswaServer*；網域中則有目標電腦 *srv1.contoso.com*。</span><span class="sxs-lookup"><span data-stu-id="072ac-267">The administrator has a gateway server, *PswaServer*, in a workgroup; and target computer *srv1.contoso.com* is in a domain.</span></span> <span data-ttu-id="072ac-268">使用者 *Chris* 是工作群組閘道伺服器和目標電腦上的授權本機使用者。</span><span class="sxs-lookup"><span data-stu-id="072ac-268">User *Chris* is an authorized local user on both the workgroup gateway server and the target computer.</span></span> <span data-ttu-id="072ac-269">他在工作群組伺服器的使用者名稱為 *chrisLocal*，而他在目標電腦的使用者名稱為 *contoso\\chris*。</span><span class="sxs-lookup"><span data-stu-id="072ac-269">His user name on the workgroup server is *chrisLocal*; and his user name on the target computer is *contoso\\chris*.</span></span> <span data-ttu-id="072ac-270">如果要授與 Chris 存取 srv1.contoso.com 的權限，系統管理員要新增下列規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-270">To authorize access to srv1.contoso.com for Chris, the administrator adds the following rule.</span></span>

    [<span data-ttu-id="072ac-271">Copy</span><span class="sxs-lookup"><span data-stu-id="072ac-271">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_8d183d3d-1c19-44b8-9297-530b0efc7c79'); "複製到剪貼簿。")

        Add-PswaAuthorizationRule -userName PswaServer\chrisLocal -computerName srv1.contoso.com -configurationName Microsoft.PowerShell

    <span data-ttu-id="072ac-272">之前的規則範例會在閘道伺服器驗證 Chris，然後授與他存取 *srv1* 的權限。</span><span class="sxs-lookup"><span data-stu-id="072ac-272">The preceding rule example authenticates Chris on the gateway server, and then authorizes his access to *srv1*.</span></span> <span data-ttu-id="072ac-273">在登入頁面上，Chris 必須在 **[選用連線設定]** 區域 (*contoso\\chris*) 中提供第二組認證。</span><span class="sxs-lookup"><span data-stu-id="072ac-273">On the sign-in page, Chris must provide a second set of credentials in the **Optional connection settings** area (*contoso\\chris*).</span></span> <span data-ttu-id="072ac-274">閘道伺服器會使用這組額外的認證，在目標電腦 *srv1.contoso.com* 上驗證他。</span><span class="sxs-lookup"><span data-stu-id="072ac-274">The gateway server uses the additional set of credentials to authenticate him on the target computer, *srv1.contoso.com*.</span></span>

    <span data-ttu-id="072ac-275">在先前的案例中，Windows PowerShell Web 存取必須先成功完成下列各項且至少獲得一個授權規則的允許，才能順利建立與目標電腦的連線。</span><span class="sxs-lookup"><span data-stu-id="072ac-275">In the preceding scenario, Windows PowerShell Web Access establishes a successful connection to the target computer only after the following have been successful, and allowed by at least one authorization rule.</span></span>

    1.  <span data-ttu-id="072ac-276">利用 *server_name*\\*user_name* 格式將使用者名稱新增到授權規則，以便在工作群組閘道伺服器上進行驗證</span><span class="sxs-lookup"><span data-stu-id="072ac-276">Authentication on the workgroup gateway server by adding a user name in the format *server_name*\\*user_name* to the authorization rule</span></span>

    2.  <span data-ttu-id="072ac-277">使用登入頁面上 [選用連線設定] 區域中提供的替代認證，在目標電腦上進行驗證</span><span class="sxs-lookup"><span data-stu-id="072ac-277">Authentication on the target computer by using alternate credentials provided on the sign-in page, in the **Optional connection settings** area</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="072ac-278"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></span><span class="sxs-lookup"><span data-stu-id="072ac-278"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="072ac-279">如果閘道與目標電腦位於不同的工作群組或網域，則必須建立兩個工作群組電腦、兩個網域或工作群組及網域間的信任關係。</span><span class="sxs-lookup"><span data-stu-id="072ac-279">If gateway and target computers are in different workgroups or domains, a trust relationship must be established between the two workgroup computers, the two domains, or between the workgroup and the domain.</span></span> <span data-ttu-id="072ac-280">這個關係無法使用 Windows PowerShell Web 存取授權規則 Cmdlet 進行設定。</span><span class="sxs-lookup"><span data-stu-id="072ac-280">This relationship cannot be configured by using Windows PowerShell Web Access authorization rule cmdlets.</span></span> <span data-ttu-id="072ac-281">授權規則無法定義電腦間的信任關係，只能授權讓使用者連線到特定目標電腦和工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="072ac-281">Authorization rules do not define a trust relationship between computers; they can only authorize users to connect to specific target computers and session configurations.</span></span> <span data-ttu-id="072ac-282">如需如何設定不同網域間信任關係的詳細資訊，請參閱<a href="https://technet.microsoft.com/library/cc794775.aspx">建立網域及樹系信任</a>。</span><span class="sxs-lookup"><span data-stu-id="072ac-282">For more information about how to configure a trust relationship between different domains, see <a href="https://technet.microsoft.com/library/cc794775.aspx">Creating Domain and Forest Trusts</a>.</span></span> <span data-ttu-id="072ac-283">如需如何將工作群組電腦加入信任主機清單的詳細資訊，請參閱<a href="https://technet.microsoft.com/library/dd759202.aspx">使用伺服器管理員進行遠端管理</a>。</span><span class="sxs-lookup"><span data-stu-id="072ac-283">For more information about how to add workgroup computers to a trusted hosts list, see <a href="https://technet.microsoft.com/library/dd759202.aspx">Remote Management with Server Manager</a>.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="072ac-284"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">對多個站台使用一組授權規則</span></a></span><span class="sxs-lookup"><span data-stu-id="072ac-284"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Using a single set of authorization rules for multiple sites</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="072ac-285">授權規則儲存在 XML 檔案中。</span><span class="sxs-lookup"><span data-stu-id="072ac-285">Authorization rules are stored in an XML file.</span></span> <span data-ttu-id="072ac-286">根據預設，XML 檔案的路徑名稱為 %windir%\\Web\\PowershellWebAccess\\data\\AuthorizationRules.xml。</span><span class="sxs-lookup"><span data-stu-id="072ac-286">By default, the path name of the XML file is %windir%\\Web\\PowershellWebAccess\\data\\AuthorizationRules.xml.</span></span>

<span data-ttu-id="072ac-287">授權規則 XML 檔案的路徑儲存在 **powwa.config** 檔案中，它的位置在 %windir%\\Web\\PowershellWebAccess\\data。</span><span class="sxs-lookup"><span data-stu-id="072ac-287">The path to the authorization rules XML file is stored in the **powwa.config** file, which is found in %windir%\\Web\\PowershellWebAccess\\data.</span></span> <span data-ttu-id="072ac-288">系統管理員可彈性變更 **powwa.config** 中預設路徑的參照，以符合喜好設定或需求。</span><span class="sxs-lookup"><span data-stu-id="072ac-288">The administrator has the flexibility to change the reference to the default path in **powwa.config** to suit preferences or requirements.</span></span> <span data-ttu-id="072ac-289">如有需要，系統管理員可以變更這個檔案的位置，讓多個 Windows PowerShell Web 存取閘道使用相同的授權規則。</span><span class="sxs-lookup"><span data-stu-id="072ac-289">Allowing the administrator to change the location of the file lets multiple Windows PowerShell Web Access gateways use the same authorization rules, if such a configuration is desired.</span></span>

<a href="" id="BKMK_sesmgmt"></a>

<span data-ttu-id="072ac-290"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">工作階段管理</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="072ac-290"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Session management</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="072ac-291">根據預設，Windows PowerShell Web 存取會將使用者限制為一次三個工作階段。</span><span class="sxs-lookup"><span data-stu-id="072ac-291">By default, Windows PowerShell Web Access limits a user to three sessions at one time.</span></span> <span data-ttu-id="072ac-292">您可以在 IIS 管理員中編輯 Web 應用程式的 **web.config** 檔案，以支援每位使用者不同的工作階段數目。</span><span class="sxs-lookup"><span data-stu-id="072ac-292">You can edit the web application’s **web.config** file in IIS Manager to support a different number of sessions per user.</span></span> <span data-ttu-id="072ac-293">**web.config** 檔案的路徑為 $Env:Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web.config。</span><span class="sxs-lookup"><span data-stu-id="072ac-293">The path to the **web.config** file is $Env:Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web.config.</span></span>

<span data-ttu-id="072ac-294">根據預設，只要編輯任何設定，網頁伺服器 (IIS) 就會重新啟動應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="072ac-294">By default, Web Server (IIS) is configured to restart the application pool if any settings are edited.</span></span> <span data-ttu-id="072ac-295">例如，如果變更 **web.config** 檔案，就會重新啟動應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="072ac-295">For example, the application pool is restarted if changes are made to the **web.config** file.</span></span> <span data-ttu-id="072ac-296">因為 Windows PowerShell Web 存取會使用記憶體中的工作階段狀態，所以登入 Windows PowerShell Web 存取工作階段的使用者會在應用程式集區重新啟動後遺失他們的工作階段。</span><span class="sxs-lookup"><span data-stu-id="072ac-296">Because Windows PowerShell Web Access uses in-memory session states, users signed in to Windows PowerShell Web Access sessions lose their sessions when the application pool is restarted.</span></span>

###

<span data-ttu-id="072ac-297"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">設定登入頁面的預設參數</span></a></span><span class="sxs-lookup"><span data-stu-id="072ac-297"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Setting default parameters on the sign-in page</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="072ac-298">如果您的 Windows PowerShell Web 存取閘道正在 Windows Server 2012 R2 上執行，您就可以針對 Windows PowerShell Web 存取登入頁面上顯示的設定來設定預設值。</span><span class="sxs-lookup"><span data-stu-id="072ac-298">If your Windows PowerShell Web Access gateway is running on Windows Server 2012 R2, you can configure default values for the settings that are displayed on the Windows PowerShell Web Access sign-in page.</span></span> <span data-ttu-id="072ac-299">您可以在上一段中說明的 **web.config** 檔案中設定值。</span><span class="sxs-lookup"><span data-stu-id="072ac-299">You can configure values in the **web.config** file that is described in the preceding paragraph.</span></span> <span data-ttu-id="072ac-300">登入頁面設定的預設值位於 web.config 檔案的 **appSettings** 區段中；以下是 **appSettings** 區段的範例。</span><span class="sxs-lookup"><span data-stu-id="072ac-300">Default values for the sign-in page settings are found in the **appSettings** section of the web.config file; the following is an example of the **appSettings** section.</span></span> <span data-ttu-id="072ac-301">其中許多設定的有效值，都與 Windows PowerShell 中的 [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) Cmdlet 的對應參數相同。</span><span class="sxs-lookup"><span data-stu-id="072ac-301">Valid values for many of these settings are the same as those for the corresponding parameters of the [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) cmdlet in Windows PowerShell.</span></span> <span data-ttu-id="072ac-302">例如，<span class="code">defaultApplicationName</span> 索引鍵 (如下列程式碼區塊所示) 即為目標電腦上的 **$PSSessionApplicationName** 喜好設定變數值。</span><span class="sxs-lookup"><span data-stu-id="072ac-302">For example, the <span class="code">defaultApplicationName</span> key, as shown in the following code block, is the value of the **$PSSessionApplicationName** preference variable on the target computer.</span></span>

[<span data-ttu-id="072ac-303">Copy</span><span class="sxs-lookup"><span data-stu-id="072ac-303">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_6ccfd0a1-485a-4ac5-9636-89ebab501bef'); "複製到剪貼簿。")

    <appSettings>
            <add key="maxSessionsAllowedPerUser" value="3"/>
            <add key="defaultPortNumber" value="5985"/>
            <add key="defaultSSLPortNumber" value="5986"/>
            <add key="defaultApplicationName" value="WSMAN"/>
            <add key="defaultUseSslSelection" value="0"/>
            <add key="defaultAuthenticationType" value="0"/>
            <add key="defaultAllowRedirection" value="0"/>
            <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
    </appSettings>

###

<span data-ttu-id="072ac-304"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">逾時和非計劃的連線中斷</span></a></span><span class="sxs-lookup"><span data-stu-id="072ac-304"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Time-outs and unplanned disconnections</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="072ac-305">Windows PowerShell Web 存取工作階段逾時。</span><span class="sxs-lookup"><span data-stu-id="072ac-305">Windows PowerShell Web Access sessions time out.</span></span> <span data-ttu-id="072ac-306">在 Windows Server 2012 上執行的 Windows PowerShell Web 存取中，當工作階段停止活動超過 15 分鐘後，登入使用者就會看到逾時訊息。</span><span class="sxs-lookup"><span data-stu-id="072ac-306">In Windows PowerShell Web Access running on Windows Server 2012, A time-out message is displayed to signed-in users after 15 minutes of session inactivity.</span></span> <span data-ttu-id="072ac-307">如果使用者沒有在逾時訊息顯示後五分鐘內回應，該工作階段就會結束，使用者也會登出。</span><span class="sxs-lookup"><span data-stu-id="072ac-307">If the user does not respond within five minutes after the time-out message is displayed, the session is ended, and the user is signed out.</span></span> <span data-ttu-id="072ac-308">您可以在 IIS 管理員的網站設定中，變更工作階段的逾時期間。</span><span class="sxs-lookup"><span data-stu-id="072ac-308">You can change time-out periods for sessions in the website settings in IIS Manager.</span></span>

<span data-ttu-id="072ac-309">在 Windows Server 2012 R2 上執行的 Windows PowerShell Web 存取中，根據預設，工作階段會在停止活動超過 20 分鐘後逾時。</span><span class="sxs-lookup"><span data-stu-id="072ac-309">In Windows PowerShell Web Access running on Windows Server 2012 R2, sessions time out, by default, after 20 minutes of inactivity.</span></span> <span data-ttu-id="072ac-310">如果使用者因為網路錯誤或其他非計劃性關機或失敗 (而不是因為他們自行關閉工作階段) 而從網頁型主控台中斷工作階段的連線，Windows PowerShell Web 存取工作階段就會繼續執行且連線到目標電腦，直到用戶端的逾時期間結束為止。</span><span class="sxs-lookup"><span data-stu-id="072ac-310">If users are disconnected from sessions in the web-based console because of network errors or other unplanned shutdowns or failures, and not because they have closed the sessions themselves, the Windows PowerShell Web Access sessions continue to run, connected to target computers, until the time-out period on the client side lapses.</span></span> <span data-ttu-id="072ac-311">工作階段會在預設的 20 分鐘或閘道系統管理員所指定的逾時期間之後中斷連線，視何者較短而定。</span><span class="sxs-lookup"><span data-stu-id="072ac-311">The session is disconnected after either the default 20 minutes, or after the time-out period specified by the gateway administrator, whichever is shorter.</span></span>

<span data-ttu-id="072ac-312">如果閘道伺服器正在執行 Windows Server 2012 R2，Windows PowerShell Web 存取就能讓使用者在稍後重新連線到已儲存的工作階段，但如果工作階段是因為網路錯誤、非計劃性關機或其他失敗而中斷連線，則在閘道系統管理員指定的逾時期間結束之前，使用者將無法檢視或重新連線到已儲存的工作階段。</span><span class="sxs-lookup"><span data-stu-id="072ac-312">If the gateway server is running Windows Server 2012 R2, Windows PowerShell Web Access lets users reconnect to saved sessions at a later time, but when network errors, unplanned shutdowns, or other failures disconnect sessions, users cannot see or reconnect to saved sessions until after the time-out period specified by the gateway administrator has lapsed.</span></span>

<span data-ttu-id="072ac-313"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另請參閱</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="072ac-313"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="072ac-314">[安裝和使用 Windows PowerShell Web 存取](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
[Windows PowerShell Web 存取 Cmdlets](https://technet.microsoft.com/library/hh918342.aspx)</span><span class="sxs-lookup"><span data-stu-id="072ac-314">[Install and Use Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
[Windows PowerShell Web Access Cmdlets](https://technet.microsoft.com/library/hh918342.aspx)</span></span>

<span data-ttu-id="072ac-315"><span>顯示︰</span>繼承受保護的</span><span class="sxs-lookup"><span data-stu-id="072ac-315"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="072ac-316"><span class="stdr-votetitle">此頁面是否有幫助？</span></span><span class="sxs-lookup"><span data-stu-id="072ac-316"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="072ac-317">是 否</span><span class="sxs-lookup"><span data-stu-id="072ac-317">Yes No</span></span>

<span data-ttu-id="072ac-318">其他意見反應？</span><span class="sxs-lookup"><span data-stu-id="072ac-318">Additional feedback?</span></span>

<span data-ttu-id="072ac-319"><span class="stdr-count">剩下 <span class="stdr-charcnt">1500</span> 個字元</span> 提交 略過</span><span class="sxs-lookup"><span data-stu-id="072ac-319"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="072ac-320"><span class="stdr-thankyou">謝謝您！</span></span><span class="sxs-lookup"><span data-stu-id="072ac-320"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="072ac-321"><span class="stdr-appreciate">我們非常感謝您的意見反應。</span></span><span class="sxs-lookup"><span data-stu-id="072ac-321"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="072ac-322">管理您的設定檔</span><span class="sxs-lookup"><span data-stu-id="072ac-322">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="072ac-323"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"><img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /></span> 網站意見反應</a> 網站意見反應</span><span class="sxs-lookup"><span data-stu-id="072ac-323"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="072ac-324"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="072ac-324"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="072ac-325">請與我們分享您的體驗...</span><span class="sxs-lookup"><span data-stu-id="072ac-325">Tell us about your experience...</span></span>

<span data-ttu-id="072ac-326">頁面是否快速載入？</span><span class="sxs-lookup"><span data-stu-id="072ac-326">Did the page load quickly?</span></span>

<span data-ttu-id="072ac-327"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="072ac-327"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="072ac-328">您喜歡頁面設計嗎？</span><span class="sxs-lookup"><span data-stu-id="072ac-328">Do you like the page design?</span></span>

<span data-ttu-id="072ac-329"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="072ac-329"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="072ac-330">請告訴我們更多資訊</span><span class="sxs-lookup"><span data-stu-id="072ac-330">Tell us more</span></span>

-   [<span data-ttu-id="072ac-331">電子快訊</span><span class="sxs-lookup"><span data-stu-id="072ac-331">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="072ac-332">與我們連絡</span><span class="sxs-lookup"><span data-stu-id="072ac-332">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="072ac-333">隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="072ac-333">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="072ac-334">使用規定</span><span class="sxs-lookup"><span data-stu-id="072ac-334">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="072ac-335">商標</span><span class="sxs-lookup"><span data-stu-id="072ac-335">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="072ac-336">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="072ac-336">© 2016 Microsoft</span></span>

<span data-ttu-id="072ac-337">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="072ac-337">© 2016 Microsoft</span></span>

<span data-ttu-id="072ac-338">連結至此網站或由此網站參照之第三方指令碼和程式碼，係由擁有此類程式碼之第三方授權予　貴用戶，而非 Microsoft 所授予。</span><span class="sxs-lookup"><span data-stu-id="072ac-338">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="072ac-339">請參閱 ASP.NET Ajax CDN 使用條款 - http://www.asp.net/ajaxlibrary/CDN.ashx。</span><span class="sxs-lookup"><span data-stu-id="072ac-339">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

