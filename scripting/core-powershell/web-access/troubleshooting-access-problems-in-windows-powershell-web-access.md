---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "為 Windows PowerShell Web 存取中的存取問題進行疑難排解"
ms.openlocfilehash: c10e19b177110ff62d44f28b6a523380b55b79e0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
#  <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="473ba-103">疑難排解 Windows PowerShell Web 存取中的存取問題</span><span class="sxs-lookup"><span data-stu-id="473ba-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="473ba-104">更新日期︰2013 年 6 月 24 日</span><span class="sxs-lookup"><span data-stu-id="473ba-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="473ba-105">適用目標︰Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="473ba-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

<span data-ttu-id="473ba-106">下表識別使用者在嘗試使用 Windows PowerShell Web 存取連線到遠端電腦時可能經歷的一些常見問題，以及解決這些問題的建議。</span><span class="sxs-lookup"><span data-stu-id="473ba-106">The following table identifies some common problems that users might experience when they are attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="473ba-107">問題</span><span class="sxs-lookup"><span data-stu-id="473ba-107">Problem</span></span></p></th>
<th><p><span data-ttu-id="473ba-108">可能的原因及解決方案</span><span class="sxs-lookup"><span data-stu-id="473ba-108">Possible cause and solution</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="473ba-109">登入失敗</span><span class="sxs-lookup"><span data-stu-id="473ba-109">Sign-in failure</span></span></p></td>
<td><p><span data-ttu-id="473ba-110">下列各項為可能發生失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="473ba-110">Failure could occur because of any of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="473ba-111">允許使用者存取電腦的授權規則或遠端電腦上的特定工作階段設定不存在。</span><span class="sxs-lookup"><span data-stu-id="473ba-111">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span> <span data-ttu-id="473ba-112">Windows PowerShell Web 存取安全性受到限制；必須使用授權規則明確授與使用者存取遠端電腦的存取權。</span><span class="sxs-lookup"><span data-stu-id="473ba-112">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span> <span data-ttu-id="473ba-113">如需建立授權規則的詳細資訊，請參閱本指南中的 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell Web 存取的授權規則與安全性功能</a>。</span><span class="sxs-lookup"><span data-stu-id="473ba-113">For more information about creating authorization rules, see <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Authorization Rules and Security Features of Windows PowerShell Web Access</a> in this guide.</span></span></p></li>
<li><p><span data-ttu-id="473ba-114">使用者沒有存取目的地電腦的權限。</span><span class="sxs-lookup"><span data-stu-id="473ba-114">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="473ba-115">這可由存取控制清單 (ACL) 來判斷。</span><span class="sxs-lookup"><span data-stu-id="473ba-115">This is determined by access control lists (ACLs).</span></span> <span data-ttu-id="473ba-116">如需詳細資訊，請參閱<a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">使用網頁型 Windows PowerShell 主控台</a>中的＜登入 Windows PowerShell Web 存取＞，或 <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell 小組部落格</a>。</span><span class="sxs-lookup"><span data-stu-id="473ba-116">For more information, see “Signing in to Windows PowerShell Web Access” in <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Use the Web-based Windows PowerShell Console</a>, or the <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell Team Blog</a>.</span></span></p>
<ul>
<li><p><span data-ttu-id="473ba-117">目的電腦可能沒有啟用 Windows PowerShell 遠端管理。</span><span class="sxs-lookup"><span data-stu-id="473ba-117">Windows PowerShell remote management might not be enabled on the destination computer.</span></span> <span data-ttu-id="473ba-118">確認已在使用者嘗試連線的電腦上啟用這個功能。</span><span class="sxs-lookup"><span data-stu-id="473ba-118">Verify that it is enabled on the computer to which the user is trying to connect.</span></span> <span data-ttu-id="473ba-119">如需詳細資訊，請參閱 Windows PowerShell 說明主題中 <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> 的＜如何設定電腦的遠端功能＞一節。</span><span class="sxs-lookup"><span data-stu-id="473ba-119">For more information, see “How to Configure Your Computer for Remoting” in <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> in the Windows PowerShell About Help Topics.</span></span></p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="473ba-120">當使用者嘗試在 Internet Explorer 視窗登入 Windows PowerShell Web 存取時，會看到 [內部伺服器錯誤]<strong></strong> 頁面或 Internet Explorer 停止回應。</span><span class="sxs-lookup"><span data-stu-id="473ba-120">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an <strong>Internal Server Error</strong> page, or Internet Explorer stops responding.</span></span> <span data-ttu-id="473ba-121">這是只有 Internet Explorer 會發生的問題。</span><span class="sxs-lookup"><span data-stu-id="473ba-121">This issue is specific to Internet Explorer.</span></span></p></td>
<td><p><span data-ttu-id="473ba-122">當使用者使用含有中文字元的網域名稱登入，或閘道伺服器名稱含有一或多個中文字元時，會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="473ba-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span> <span data-ttu-id="473ba-123">若要解決這個問題，使用者應<a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">安裝和執行 Internet Explorer 10</a>，然後執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="473ba-123">To work around this issue, the user should <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">install and run Internet Explorer 10</a>, and then perform the following steps.</span></span></p>
<ol>
<li><p><span data-ttu-id="473ba-124">將 Internet Explorer <strong>[文件模式]</strong> 設定變更成 <strong>[IE10 standards (IE10 標準)]</strong>。</span><span class="sxs-lookup"><span data-stu-id="473ba-124">Change the Internet Explorer <strong>Document Mode</strong> setting to <strong>IE10 standards</strong>.</span></span></p>
<ol>
<li><p><span data-ttu-id="473ba-125">按 <strong>F12</strong> 開啟開發人員工具主控台。</span><span class="sxs-lookup"><span data-stu-id="473ba-125">Press <strong>F12</strong> to open the Developer Tools console.</span></span></p></li>
<li><p><span data-ttu-id="473ba-126">在 Internet Explorer 10 中，按一下 <strong>[瀏覽器模式]</strong>，然後選取 <strong>[Internet Explorer 10]</strong>。</span><span class="sxs-lookup"><span data-stu-id="473ba-126">In Internet Explorer 10, click <strong>Browser Mode</strong>, and then select <strong>Internet Explorer 10</strong>.</span></span></p></li>
<li><p><span data-ttu-id="473ba-127">按一下 <strong>[文件模式]</strong>，然後按一下 <strong>[IE10 standards (IE10 標準)]</strong>。</span><span class="sxs-lookup"><span data-stu-id="473ba-127">Click <strong>Document Mode</strong>, and then click <strong>IE10 standards</strong>.</span></span></p></li>
<li><p><span data-ttu-id="473ba-128">再按一次 <strong>F12</strong> 關閉開發人員工具主控台。</span><span class="sxs-lookup"><span data-stu-id="473ba-128">Press <strong>F12</strong> again to close the Developer Tools console.</span></span></p></li>
</ol></li>
<li><p><span data-ttu-id="473ba-129">停用自動 Proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="473ba-129">Disable automatic proxy configuration.</span></span></p>
<ol>
<li><p><span data-ttu-id="473ba-130">在 Internet Explorer 10 中，按一下 <strong>[工具]</strong>，然後按一下 <strong>[網際網路選項]</strong>。</span><span class="sxs-lookup"><span data-stu-id="473ba-130">In Internet Explorer 10, click <strong>Tools</strong>, and then click <strong>Internet Options</strong>.</span></span></p></li>
<li><p><span data-ttu-id="473ba-131">在 <strong>[網際網路選項]</strong> 對話方塊的 <strong>[連線]</strong> 索引標籤中，按一下 <strong>[區域網路設定]</strong>。</span><span class="sxs-lookup"><span data-stu-id="473ba-131">In the <strong>Internet Options</strong> dialog box, on the <strong>Connections</strong> tab, click <strong>LAN settings</strong>.</span></span></p></li>
<li><p><span data-ttu-id="473ba-132">清除 [自動偵測設定]<strong></strong> 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="473ba-132">Clear the <strong>Automatically detect settings</strong> check box.</span></span> <span data-ttu-id="473ba-133">按一下 [確定]<strong></strong>，然後再按一次 [確定]<strong></strong> 關閉 [網際網路選項]<strong></strong> 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="473ba-133">Click <strong>OK</strong>, and then click <strong>OK</strong> again to close the <strong>Internet Options</strong> dialog box.</span></span></p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="473ba-134">無法連線到遠端工作群組電腦</span><span class="sxs-lookup"><span data-stu-id="473ba-134">Cannot connect to a remote workgroup computer</span></span></p></td>
<td><p><span data-ttu-id="473ba-135">如果目的地電腦是工作群組的成員，請使用下列語法提供您的使用者名稱並登入電腦：&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</span><span class="sxs-lookup"><span data-stu-id="473ba-135">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: &lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="473ba-136">即使已安裝角色，仍找不到網頁伺服器 (IIS) 管理工具</span><span class="sxs-lookup"><span data-stu-id="473ba-136">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span></p></td>
<td><p><span data-ttu-id="473ba-137">如果您使用 <span class="code">Install-WindowsFeature</span> Cmdlet 安裝 Windows PowerShell Web 存取，除非將 <span class="code">IncludeManagementTools</span> 參數新增到 Cmdlet，否則不會安裝管理工具。</span><span class="sxs-lookup"><span data-stu-id="473ba-137">If you installed Windows PowerShell Web Access by using the <span class="code">Install-WindowsFeature</span> cmdlet, management tools are not installed unless the <span class="code">IncludeManagementTools</span> parameter is added to the cmdlet.</span></span> <span data-ttu-id="473ba-138">如需範例，請參閱<a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">安裝及使用 Windows PowerShell Web 存取</a>中的＜使用 Windows PowerShell Cmdlet 安裝 Windows PowerShell Web 存取＞。</span><span class="sxs-lookup"><span data-stu-id="473ba-138">For an example, see “To install Windows PowerShell Web Access by using Windows PowerShell cmdlets” in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Install and Use Windows PowerShell Web Access</a>.</span></span> <span data-ttu-id="473ba-139">在以閘道伺服器為目標的「新增角色及功能精靈」工作階段選取工具，可以新增 IIS 管理員主控台及您需要的其他 IIS 管理工具。</span><span class="sxs-lookup"><span data-stu-id="473ba-139">You can add the IIS Manager console and other IIS management tools that you need by selecting the tools in an Add Roles and Features Wizard session that is targeted at the gateway server.</span></span> <span data-ttu-id="473ba-140">您可以從 [伺服器管理員] 中開啟 [新增角色及功能精靈]。</span><span class="sxs-lookup"><span data-stu-id="473ba-140">The Add Roles and Features Wizard is opened from within Server Manager.</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="473ba-141">無法存取 Windows PowerShell Web 存取網站</span><span class="sxs-lookup"><span data-stu-id="473ba-141">The Windows PowerShell Web Access website is not accessible</span></span></p></td>
<td><p><span data-ttu-id="473ba-142">如果在 Internet Explorer 啟用增強式安全性設定 (IE ESC)，您可以新增 Windows PowerShell Web 存取網站到受信任站台清單中，或者停用 IE ESC。</span><span class="sxs-lookup"><span data-stu-id="473ba-142">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites, or disable IE ESC.</span></span> <span data-ttu-id="473ba-143">您可以在 [伺服器管理員] 中 [本機伺服器]<strong></strong> 頁面上的 [屬性]<strong></strong> 磚中停用 IE ESC。</span><span class="sxs-lookup"><span data-stu-id="473ba-143">You can disable IE ESC in the <strong>Properties</strong> tile on the <strong>Local Server</strong> page in Server Manager.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="473ba-144">當閘道伺服器為目的電腦且同時位於工作群組時嘗試連線，會顯示下列錯誤訊息：<strong>授權失敗。請確認您已獲授權而可連線至目的電腦。</strong></span><span class="sxs-lookup"><span data-stu-id="473ba-144">The following error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup: <strong>An authorization failure occurred. Verify that you are authorized to connect to the destination computer.</strong></span></span></p></td>
<td><p><span data-ttu-id="473ba-145">當閘道伺服器也是目的伺服器且位於工作群組時，請指定使用者名稱、電腦名稱，以及下表顯示的使用者群組名稱。</span><span class="sxs-lookup"><span data-stu-id="473ba-145">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name as shown in the following table.</span></span> <span data-ttu-id="473ba-146">請勿單獨使用點 (.) 來代表電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="473ba-146">Do not use a dot (.) by itself to represent the computer name.</span></span></p>
<div>
<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th><p><span data-ttu-id="473ba-147">案例</span><span class="sxs-lookup"><span data-stu-id="473ba-147">Scenario</span></span></p></th>
<th><p><span data-ttu-id="473ba-148">UserName 參數</span><span class="sxs-lookup"><span data-stu-id="473ba-148">UserName Parameter</span></span></p></th>
<th><p><span data-ttu-id="473ba-149">UserGroup 參數</span><span class="sxs-lookup"><span data-stu-id="473ba-149">UserGroup Parameter</span></span></p></th>
<th><p><span data-ttu-id="473ba-150">ComputerName 參數</span><span class="sxs-lookup"><span data-stu-id="473ba-150">ComputerName Parameter</span></span></p></th>
<th><p><span data-ttu-id="473ba-151">ComputerGroup 參數</span><span class="sxs-lookup"><span data-stu-id="473ba-151">ComputerGroup Parameter</span></span></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="473ba-152">閘道伺服器位於網域</span><span class="sxs-lookup"><span data-stu-id="473ba-152">Gateway server is in a domain</span></span></p></td>
<td><p><span data-ttu-id="473ba-153"><em>Server_name</em>\<em>user_name</em>、Localhost\<em>user_name</em> 或 .\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="473ba-153"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="473ba-154"><em>Server_name</em>\<em>user_group</em>、Localhost\<em>user_group</em> 或 .\<em>user_group</em></span><span class="sxs-lookup"><span data-stu-id="473ba-154"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em>, or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="473ba-155">閘道伺服器的完整名稱，或 Localhost</span><span class="sxs-lookup"><span data-stu-id="473ba-155">Fully qualified name of gateway server, or Localhost</span></span></p></td>
<td><p><span data-ttu-id="473ba-156"><em>Server_name</em>\<em>computer_group</em>、Localhost\<em>computer_group</em> 或 .\<em>computer_group</em></span><span class="sxs-lookup"><span data-stu-id="473ba-156"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em>, or .\<em>computer_group</em></span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="473ba-157">閘道伺服器位於工作群組</span><span class="sxs-lookup"><span data-stu-id="473ba-157">Gateway server is in a workgroup</span></span></p></td>
<td><p><span data-ttu-id="473ba-158"><em>Server_name</em>\<em>user_name</em>、Localhost\<em>user_name</em> 或 .\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="473ba-158"><em>Server_name</em>\<em>user_name</em>, Localhost\<em>user_name</em>, or .\<em>user_name</em></span></span></p></td>
<td><p><span data-ttu-id="473ba-159"><em>Server_name</em>\<em>user_group</em>、Localhost\<em>user_group</em> 或 .\<em>user_group</em></span><span class="sxs-lookup"><span data-stu-id="473ba-159"><em>Server_name</em>\<em>user_group</em>, Localhost\<em>user_group</em> or .\<em>user_group</em></span></span></p></td>
<td><p><span data-ttu-id="473ba-160">伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="473ba-160">Server name</span></span></p></td>
<td><p><span data-ttu-id="473ba-161"><em>Server_name</em>\<em>computer_group</em>、Localhost\<em>computer_group</em> 或 .\<em>computer_group</em></span><span class="sxs-lookup"><span data-stu-id="473ba-161"><em>Server_name</em>\<em>computer_group</em>, Localhost\<em>computer_group</em> or .\<em>computer_group</em></span></span></p></td>
</tr>
</tbody>
</table>
</div>
<p><span data-ttu-id="473ba-162">使用下列其中一種格式的認證以目標電腦身分登入閘道伺服器。</span><span class="sxs-lookup"><span data-stu-id="473ba-162">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span></p>
<ul>
<li><p><span data-ttu-id="473ba-163"><em>Server_name</em>\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="473ba-163"><em>Server_name</em>\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="473ba-164">Localhost\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="473ba-164">Localhost\<em>user_name</em></span></span></p></li>
<li><p><span data-ttu-id="473ba-165">.\<em>user_name</em></span><span class="sxs-lookup"><span data-stu-id="473ba-165">.\<em>user_name</em></span></span></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="473ba-166">授權規則顯示安全性識別碼 (SID)，而不是 <em>user_name</em>/<em>computer_name</em>  語法</span><span class="sxs-lookup"><span data-stu-id="473ba-166">A security identifier (SID) is displayed in an authorization rule instead of the syntax <em>user_name</em>/<em>computer_name</em> </span></span></p></td>
<td><p><span data-ttu-id="473ba-167">可能是規則不再有效，或者 Active Directory 網域服務查詢失敗。</span><span class="sxs-lookup"><span data-stu-id="473ba-167">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span> <span data-ttu-id="473ba-168">當閘道伺服器曾經位於工作群組，但之後加入網域的案例中，授權規則通常會無效。</span><span class="sxs-lookup"><span data-stu-id="473ba-168">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain.</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="473ba-169">在授權規則中將目標電腦指定為含網域的 IPv6 位址時，無法登入該目標電腦。</span><span class="sxs-lookup"><span data-stu-id="473ba-169">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span></p></td>
<td><p><span data-ttu-id="473ba-170">授權規則不支援網域名稱格式的 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="473ba-170">Authorization rules do not support an IPv6 address in form of a domain name.</span></span> <span data-ttu-id="473ba-171">若要使用 IPv6 位址指定目的電腦，請在授權規則使用原始 IPv6 位址 (包含冒號)。</span><span class="sxs-lookup"><span data-stu-id="473ba-171">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span> <span data-ttu-id="473ba-172">在 [Windows PowerShell Web 存取] 登入頁面中，支援以網域及數字 (含冒號) IPv6 位址做為目標電腦名稱，但在授權規則中則不行。</span><span class="sxs-lookup"><span data-stu-id="473ba-172">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span> <span data-ttu-id="473ba-173">如需 IPv6 位址的詳細資訊，請參閱 <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a> (IPv6 的運作方式)。</span><span class="sxs-lookup"><span data-stu-id="473ba-173">For more information about IPv6 addresses, see <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a>.</span></span></p></td>
</tr>
</tbody>
</table><span data-ttu-id="473ba-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另請參閱</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="473ba-174">

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="473ba-175">[Windows PowerShell Web 存取的授權規則與安全性功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[使用網頁型 Windows PowerShell 主控台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span><span class="sxs-lookup"><span data-stu-id="473ba-175">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)</span></span>

<span data-ttu-id="473ba-176"><span>顯示︰</span>繼承受保護的</span><span class="sxs-lookup"><span data-stu-id="473ba-176"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="473ba-177"><span class="stdr-votetitle">此頁面是否有幫助？</span></span><span class="sxs-lookup"><span data-stu-id="473ba-177"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="473ba-178">是 否</span><span class="sxs-lookup"><span data-stu-id="473ba-178">Yes No</span></span>

<span data-ttu-id="473ba-179">其他意見反應？</span><span class="sxs-lookup"><span data-stu-id="473ba-179">Additional feedback?</span></span>

<span data-ttu-id="473ba-180"><span class="stdr-count">剩下 <span class="stdr-charcnt">1500</span> 個字元</span> 提交 略過</span><span class="sxs-lookup"><span data-stu-id="473ba-180"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="473ba-181"><span class="stdr-thankyou">謝謝您！</span></span><span class="sxs-lookup"><span data-stu-id="473ba-181"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="473ba-182"><span class="stdr-appreciate">我們非常感謝您的意見反應。</span></span><span class="sxs-lookup"><span data-stu-id="473ba-182"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="473ba-183">管理您的設定檔</span><span class="sxs-lookup"><span data-stu-id="473ba-183">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="473ba-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"><img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /></span> 網站意見反應</a> 網站意見反應</span><span class="sxs-lookup"><span data-stu-id="473ba-184"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="473ba-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="473ba-185"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="473ba-186">請與我們分享您的體驗...</span><span class="sxs-lookup"><span data-stu-id="473ba-186">Tell us about your experience...</span></span>

<span data-ttu-id="473ba-187">頁面是否快速載入？</span><span class="sxs-lookup"><span data-stu-id="473ba-187">Did the page load quickly?</span></span>

<span data-ttu-id="473ba-188"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="473ba-188"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="473ba-189">您喜歡頁面設計嗎？</span><span class="sxs-lookup"><span data-stu-id="473ba-189">Do you like the page design?</span></span>

<span data-ttu-id="473ba-190"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="473ba-190"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="473ba-191">請告訴我們更多資訊</span><span class="sxs-lookup"><span data-stu-id="473ba-191">Tell us more</span></span>

-   [<span data-ttu-id="473ba-192">電子快訊</span><span class="sxs-lookup"><span data-stu-id="473ba-192">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="473ba-193">與我們連絡</span><span class="sxs-lookup"><span data-stu-id="473ba-193">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="473ba-194">隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="473ba-194">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="473ba-195">使用規定</span><span class="sxs-lookup"><span data-stu-id="473ba-195">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="473ba-196">商標</span><span class="sxs-lookup"><span data-stu-id="473ba-196">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="473ba-197">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="473ba-197">© 2016 Microsoft</span></span>

<span data-ttu-id="473ba-198">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="473ba-198">© 2016 Microsoft</span></span>

<span data-ttu-id="473ba-199">連結至此網站或由此網站參照之第三方指令碼和程式碼，係由擁有此類程式碼之第三方授權予　貴用戶，而非 Microsoft 所授予。</span><span class="sxs-lookup"><span data-stu-id="473ba-199">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="473ba-200">請參閱 ASP.NET Ajax CDN 使用條款 - http://www.asp.net/ajaxlibrary/CDN.ashx。</span><span class="sxs-lookup"><span data-stu-id="473ba-200">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

