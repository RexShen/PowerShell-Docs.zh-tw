---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: 為 Windows PowerShell Web 存取中的存取問題進行疑難排解
ms.openlocfilehash: 66e913504cf0c34f8d9ab18b088fb06173aca24c
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733859"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a><span data-ttu-id="7c113-103">疑難排解 Windows PowerShell Web 存取中的存取問題</span><span class="sxs-lookup"><span data-stu-id="7c113-103">Troubleshooting Access Problems in Windows PowerShell Web Access</span></span>

<span data-ttu-id="7c113-104">更新日期：2013 年 6 月 24 日 (修訂日期：2017 年 8 月 23 日)</span><span class="sxs-lookup"><span data-stu-id="7c113-104">Updated: June 24, 2013 (revised August 23, 2017)</span></span>

<span data-ttu-id="7c113-105">適用於：Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="7c113-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="7c113-106">下列各節識別在嘗試使用 Windows PowerShell Web 存取連線到遠端電腦時的一些常見問題，以及解決這些問題的建議。</span><span class="sxs-lookup"><span data-stu-id="7c113-106">The following sections identify some common problems when attempting to connect to a remote computer by using Windows PowerShell Web Access, and includes suggestions for resolving the problems.</span></span>

## <a name="sign-in-failure"></a><span data-ttu-id="7c113-107">登入失敗</span><span class="sxs-lookup"><span data-stu-id="7c113-107">Sign-in failure</span></span>

<span data-ttu-id="7c113-108">下列各項為可能發生失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="7c113-108">Failure could occur because of any of the following.</span></span>

- <span data-ttu-id="7c113-109">允許使用者存取電腦的授權規則或遠端電腦上的特定工作階段設定不存在。</span><span class="sxs-lookup"><span data-stu-id="7c113-109">An authorization rule that allows the user access to the computer, or a specific session configuration on the remote computer, does not exist.</span></span>

  <span data-ttu-id="7c113-110">Windows PowerShell Web 存取安全性受到限制；必須使用授權規則明確授與使用者存取遠端電腦的存取權。</span><span class="sxs-lookup"><span data-stu-id="7c113-110">Windows PowerShell Web Access security is restrictive; users must be granted explicit access to remote computers by using authorization rules.</span></span>

  <span data-ttu-id="7c113-111">如需建立授權規則的詳細資訊，請參閱 [Windows PowerShell Web 存取的授權規則與安全性功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。</span><span class="sxs-lookup"><span data-stu-id="7c113-111">For more information about creating authorization rules, see [Authorization Rules and Security Features of Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).</span></span>

- <span data-ttu-id="7c113-112">使用者沒有存取目的地電腦的權限。</span><span class="sxs-lookup"><span data-stu-id="7c113-112">The user does not have authorized access to the destination computer.</span></span> <span data-ttu-id="7c113-113">這可由存取控制清單 (ACL) 來判斷。</span><span class="sxs-lookup"><span data-stu-id="7c113-113">This is determined by access control lists (ACLs).</span></span>

  <span data-ttu-id="7c113-114">如需詳細資訊，請參閱[登入 Windows PowerShell Web 存取](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access)或 Windows PowerShell 小組部落格。</span><span class="sxs-lookup"><span data-stu-id="7c113-114">For more information, see [Signing in to Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), or the Windows PowerShell Team Blog.</span></span>

- <span data-ttu-id="7c113-115">目的電腦可能沒有啟用 Windows PowerShell 遠端管理。</span><span class="sxs-lookup"><span data-stu-id="7c113-115">Windows PowerShell remote management might not be enabled on the destination computer.</span></span>

  <span data-ttu-id="7c113-116">確認已在使用者嘗試連線的電腦上啟用遠端管理。</span><span class="sxs-lookup"><span data-stu-id="7c113-116">Verify remote management is enabled on the computer to which the user is trying to connect.</span></span>

  <span data-ttu-id="7c113-117">如需詳細資訊，請參閱 [How to Configure Your Computer for Remoting](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting) (如何設定電腦的遠端功能)。</span><span class="sxs-lookup"><span data-stu-id="7c113-117">For more information, see [How to Configure Your Computer for Remoting](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).</span></span>

## <a name="internal-server-error"></a><span data-ttu-id="7c113-118">內部伺服器錯誤</span><span class="sxs-lookup"><span data-stu-id="7c113-118">Internal Server Error</span></span>

<span data-ttu-id="7c113-119">當使用者嘗試在 Internet Explorer 視窗登入 Windows PowerShell Web 存取時，會看到 [內部伺服器錯誤]  頁面或 *Internet Explorer* 停止回應。</span><span class="sxs-lookup"><span data-stu-id="7c113-119">When users try to sign in to Windows PowerShell Web Access in an Internet Explorer window, they are shown an **Internal Server Error** page, or *Internet Explorer* stops responding.</span></span>

<span data-ttu-id="7c113-120">這是只有 Internet Explorer 會發生的問題。</span><span class="sxs-lookup"><span data-stu-id="7c113-120">This issue is specific to Internet Explorer.</span></span>

### <a name="possible-cause"></a><span data-ttu-id="7c113-121">可能的原因</span><span class="sxs-lookup"><span data-stu-id="7c113-121">Possible cause</span></span>

<span data-ttu-id="7c113-122">當使用者使用含有中文字元的網域名稱登入，或閘道伺服器名稱含有一或多個中文字元時，會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="7c113-122">This can occur for users who have signed in with a domain name that contains Chinese characters, or if one or more Chinese characters are part of the gateway server name.</span></span>

#### <a name="workaround"></a><span data-ttu-id="7c113-123">因應措施</span><span class="sxs-lookup"><span data-stu-id="7c113-123">Workaround</span></span>

1. [<span data-ttu-id="7c113-124">安裝和執行 Internet Explorer 10</span><span class="sxs-lookup"><span data-stu-id="7c113-124">Install and run Internet Explorer 10</span></span>](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. <span data-ttu-id="7c113-125">將 Internet Explorer [文件模式]  設定變更為 [IE10]  標準。</span><span class="sxs-lookup"><span data-stu-id="7c113-125">Change Internet Explorer **Document Mode** setting to *IE10* standards.</span></span>
   1. <span data-ttu-id="7c113-126">按 **F12** 開啟開發人員工具主控台</span><span class="sxs-lookup"><span data-stu-id="7c113-126">Press **F12** to open the Developer Tools console</span></span>
   1. <span data-ttu-id="7c113-127">在 Internet Explorer 10 中，按一下 **[瀏覽器模式]** ，然後選取 *[Internet Explorer 10]* 。</span><span class="sxs-lookup"><span data-stu-id="7c113-127">In Internet Explorer 10, click **Browser Mode**, and then select *Internet Explorer 10*.</span></span>
   1. <span data-ttu-id="7c113-128">按一下 [文件模式]  ，然後按一下 [IE10]  標準。</span><span class="sxs-lookup"><span data-stu-id="7c113-128">Click **Document Mode**, and then click *IE10* standards.</span></span>
   1. <span data-ttu-id="7c113-129">再按一次 **F12** 關閉開發人員工具主控台。</span><span class="sxs-lookup"><span data-stu-id="7c113-129">Press **F12** again to close the Developer Tools console.</span></span>
1. <span data-ttu-id="7c113-130">停用 Internet Explorer 10 中的自動 Proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="7c113-130">Disable automatic proxy configuration in Internet Explorer 10.</span></span>
   1. <span data-ttu-id="7c113-131">按一下 [工具]  ，然後按一下 [網際網路選項]  。</span><span class="sxs-lookup"><span data-stu-id="7c113-131">Click **Tools**, and then click **Internet Options**.</span></span>
   1. <span data-ttu-id="7c113-132">在 **[網際網路選項]** 對話方塊的 **[連線]** 索引標籤中，按一下 **[區域網路設定]** 。</span><span class="sxs-lookup"><span data-stu-id="7c113-132">In the **Internet Options** dialog box, on the **Connections** tab, click **LAN settings**.</span></span>
   1. <span data-ttu-id="7c113-133">清除 [自動偵測設定]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7c113-133">Clear the **Automatically detect settings** check box.</span></span> <span data-ttu-id="7c113-134">按一下 [確定]  ，然後再按一次 [確定]  關閉 [網際網路選項]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7c113-134">Click **OK**, and then click **OK** again to close the *Internet Options* dialog box.</span></span>

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a><span data-ttu-id="7c113-135">無法連線到遠端工作群組電腦</span><span class="sxs-lookup"><span data-stu-id="7c113-135">Cannot connect to a remote workgroup computer</span></span>

<span data-ttu-id="7c113-136">如果目的地電腦是工作群組的成員，請使用下列語法提供您的使用者名稱並登入電腦：`<workgroup_name>\<user_name>`</span><span class="sxs-lookup"><span data-stu-id="7c113-136">If the destination computer is a member of a workgroup, use the following syntax to provide your user name and sign in to the computer: `<workgroup_name>\<user_name>`</span></span>

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a><span data-ttu-id="7c113-137">即使已安裝角色，仍找不到網頁伺服器 (IIS) 管理工具</span><span class="sxs-lookup"><span data-stu-id="7c113-137">Cannot find Web Server (IIS) management tools, even though the role was installed</span></span>

<span data-ttu-id="7c113-138">如果您使用 `Install-WindowsFeature` Cmdlet 安裝 Windows PowerShell Web 存取，除非將 `-IncludeManagementTools` 參數新增至 Cmdlet，否則不會安裝管理工具。</span><span class="sxs-lookup"><span data-stu-id="7c113-138">If you installed Windows PowerShell Web Access by using the `Install-WindowsFeature` cmdlet, management tools are not installed unless the `-IncludeManagementTools` parameter is added to the cmdlet.</span></span>

<span data-ttu-id="7c113-139">如需範例，請參閱[使用 Windows PowerShell Cmdlet 安裝 Windows PowerShell Web 存取](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets)。</span><span class="sxs-lookup"><span data-stu-id="7c113-139">For an example, see [To install Windows PowerShell Web Access by using Windows PowerShell cmdlets](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).</span></span>

<span data-ttu-id="7c113-140">在以閘道伺服器為目標的 [新增角色及功能精靈]  工作階段選取工具，可以新增 IIS 管理員主控台及您需要的其他 IIS 管理工具。</span><span class="sxs-lookup"><span data-stu-id="7c113-140">You can add the IIS Manager console, and other IIS management tools that you need, by selecting the tools in an **Add Roles and Features Wizard** session that is targeted at the gateway server.</span></span>
<span data-ttu-id="7c113-141">您可以從 [伺服器管理員] 中開啟 [新增角色及功能精靈]。</span><span class="sxs-lookup"><span data-stu-id="7c113-141">The Add Roles and Features Wizard is opened from within Server Manager.</span></span>

## <a name="windows-powershell-web-access-website-is-not-accessible"></a><span data-ttu-id="7c113-142">無法存取 Windows PowerShell Web 存取網站</span><span class="sxs-lookup"><span data-stu-id="7c113-142">Windows PowerShell Web Access website is not accessible</span></span>

<span data-ttu-id="7c113-143">如果在 Internet Explorer 啟用增強式安全性設定 (IE ESC)，您可以將 Windows PowerShell Web 存取網站新增至信任的網站清單。</span><span class="sxs-lookup"><span data-stu-id="7c113-143">If Enhanced Security Configuration is enabled in Internet Explorer (IE ESC), you can add the Windows PowerShell Web Access website to the list of trusted sites.</span></span>

<span data-ttu-id="7c113-144">較不建議的方法是停用 IE ESC，因為這會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="7c113-144">A less recommended approach, due to security risks, is to disable IE ESC.</span></span>
<span data-ttu-id="7c113-145">您可以在 [伺服器管理員] 中 [本機伺服器] 頁面上的 [屬性] 磚中停用 IE ESC。</span><span class="sxs-lookup"><span data-stu-id="7c113-145">You can disable IE ESC in the Properties tile on the Local Server page in Server Manager.</span></span>

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a><span data-ttu-id="7c113-146">授權失敗。</span><span class="sxs-lookup"><span data-stu-id="7c113-146">An authorization failure occurred.</span></span> <span data-ttu-id="7c113-147">請確認您已獲授權可連線至目的電腦。</span><span class="sxs-lookup"><span data-stu-id="7c113-147">Verify that you are authorized to connect to the destination computer.</span></span>

<span data-ttu-id="7c113-148">當閘道伺服器為目的地電腦且同時位於工作群組時嘗試連線，會顯示上述錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="7c113-148">The above error message is displayed while trying to connect when the gateway server is the destination computer, and is also in a workgroup.</span></span>

<span data-ttu-id="7c113-149">當閘道伺服器也是目的地伺服器且位於工作群組時，請指定使用者名稱、電腦名稱和使用者群組名稱。</span><span class="sxs-lookup"><span data-stu-id="7c113-149">When the gateway server is also the destination server, and it is in a workgroup, specify the user name, computer name, and user group name.</span></span>
<span data-ttu-id="7c113-150">請勿單獨使用點 (.) 來代表電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="7c113-150">Do not use a dot (.) by itself to represent the computer name.</span></span>

### <a name="scenarios-and-proper-values"></a><span data-ttu-id="7c113-151">案例和適當的值</span><span class="sxs-lookup"><span data-stu-id="7c113-151">Scenarios and proper values</span></span>

#### <a name="all-cases"></a><span data-ttu-id="7c113-152">所有情況</span><span class="sxs-lookup"><span data-stu-id="7c113-152">All cases</span></span>

<span data-ttu-id="7c113-153">參數</span><span class="sxs-lookup"><span data-stu-id="7c113-153">Parameter</span></span> | <span data-ttu-id="7c113-154">值</span><span class="sxs-lookup"><span data-stu-id="7c113-154">Value</span></span>
-- | --
<span data-ttu-id="7c113-155">UserName</span><span class="sxs-lookup"><span data-stu-id="7c113-155">UserName</span></span> | <span data-ttu-id="7c113-156">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="7c113-156">Server\_name\\user\_name</span></span><br/><span data-ttu-id="7c113-157">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="7c113-157">Localhost\\user\_name</span></span><br/><span data-ttu-id="7c113-158">.\\user\_name</span><span class="sxs-lookup"><span data-stu-id="7c113-158">.\\user\_name</span></span>
<span data-ttu-id="7c113-159">UserGroup</span><span class="sxs-lookup"><span data-stu-id="7c113-159">UserGroup</span></span> | <span data-ttu-id="7c113-160">Server\_name\\user\_group</span><span class="sxs-lookup"><span data-stu-id="7c113-160">Server\_name\\user\_group</span></span><br/><span data-ttu-id="7c113-161">Localhost\\user\_group</span><span class="sxs-lookup"><span data-stu-id="7c113-161">Localhost\\user\_group</span></span><br/><span data-ttu-id="7c113-162">.\\user\_group</span><span class="sxs-lookup"><span data-stu-id="7c113-162">.\\user\_group</span></span>
<span data-ttu-id="7c113-163">ComputerGroup</span><span class="sxs-lookup"><span data-stu-id="7c113-163">ComputerGroup</span></span> | <span data-ttu-id="7c113-164">Server\_name\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="7c113-164">Server\_name\\computer\_group</span></span><br/><span data-ttu-id="7c113-165">Localhost\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="7c113-165">Localhost\\computer\_group</span></span><br/><span data-ttu-id="7c113-166">.\\computer\_group</span><span class="sxs-lookup"><span data-stu-id="7c113-166">.\\computer\_group</span></span>

#### <a name="gateway-server-is-in-a-domain"></a><span data-ttu-id="7c113-167">閘道伺服器位於網域</span><span class="sxs-lookup"><span data-stu-id="7c113-167">Gateway server is in a domain</span></span>

<span data-ttu-id="7c113-168">參數</span><span class="sxs-lookup"><span data-stu-id="7c113-168">Parameter</span></span> | <span data-ttu-id="7c113-169">值</span><span class="sxs-lookup"><span data-stu-id="7c113-169">Value</span></span>
-- | --
<span data-ttu-id="7c113-170">ComputerName</span><span class="sxs-lookup"><span data-stu-id="7c113-170">ComputerName</span></span> | <span data-ttu-id="7c113-171">閘道伺服器的完整名稱，或 Localhost</span><span class="sxs-lookup"><span data-stu-id="7c113-171">Fully qualified name of gateway server, or Localhost</span></span>

#### <a name="gateway-server-is-in-a-workgroup"></a><span data-ttu-id="7c113-172">閘道伺服器位於工作群組</span><span class="sxs-lookup"><span data-stu-id="7c113-172">Gateway server is in a workgroup</span></span>

<span data-ttu-id="7c113-173">參數</span><span class="sxs-lookup"><span data-stu-id="7c113-173">Parameter</span></span> | <span data-ttu-id="7c113-174">值</span><span class="sxs-lookup"><span data-stu-id="7c113-174">Value</span></span>
-- | --
<span data-ttu-id="7c113-175">ComputerName</span><span class="sxs-lookup"><span data-stu-id="7c113-175">ComputerName</span></span> | <span data-ttu-id="7c113-176">伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="7c113-176">Server name</span></span>

### <a name="gateway-credentials"></a><span data-ttu-id="7c113-177">閘道認證</span><span class="sxs-lookup"><span data-stu-id="7c113-177">Gateway credentials</span></span>

<span data-ttu-id="7c113-178">使用下列其中一種格式的認證以目標電腦身分登入閘道伺服器。</span><span class="sxs-lookup"><span data-stu-id="7c113-178">Sign in to a gateway server as target computer by using credentials formatted as one of the following.</span></span>

- <span data-ttu-id="7c113-179">Server\_name\\user\_name</span><span class="sxs-lookup"><span data-stu-id="7c113-179">Server\_name\\user\_name</span></span>
- <span data-ttu-id="7c113-180">Localhost\\user\_name</span><span class="sxs-lookup"><span data-stu-id="7c113-180">Localhost\\user\_name</span></span>
- <span data-ttu-id="7c113-181">.\\user\_name</span><span class="sxs-lookup"><span data-stu-id="7c113-181">.\\user\_name</span></span>

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a><span data-ttu-id="7c113-182">授權規則顯示安全性識別碼 (SID)</span><span class="sxs-lookup"><span data-stu-id="7c113-182">A security identifier (SID) is displayed in an authorization rule</span></span>

<span data-ttu-id="7c113-183">授權規則顯示安全性識別碼 (SID)，而不是 user\_name/computer\_name 語法。</span><span class="sxs-lookup"><span data-stu-id="7c113-183">A security identifier (SID) is displayed in an authorization rule instead of the syntax user\_name/computer\_name.</span></span>

<span data-ttu-id="7c113-184">可能是規則不再有效，或者 Active Directory 網域服務查詢失敗。</span><span class="sxs-lookup"><span data-stu-id="7c113-184">Either the rule is no longer valid, or the Active Directory Domain Services query failed.</span></span>
<span data-ttu-id="7c113-185">如果閘道伺服器曾經位於工作群組，但之後加入網域，則授權規則通常無效</span><span class="sxs-lookup"><span data-stu-id="7c113-185">An authorization rule is usually not valid in scenarios where the gateway server was at one time in a workgroup, but was later joined to a domain</span></span>

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a><span data-ttu-id="7c113-186">因為 IPv6 位址包含一個網域，所以無法使用規則登入</span><span class="sxs-lookup"><span data-stu-id="7c113-186">Cannot sign in with rule as an IPv6 address with a domain</span></span>

<span data-ttu-id="7c113-187">在授權規則中將目標電腦指定為含網域的 IPv6 位址時，無法登入該目標電腦。</span><span class="sxs-lookup"><span data-stu-id="7c113-187">Cannot sign in to a target computer that has been specified in authorization rules as an IPv6 address with a domain.</span></span>

<span data-ttu-id="7c113-188">授權規則不支援網域名稱格式的 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="7c113-188">Authorization rules do not support an IPv6 address in form of a domain name.</span></span>

<span data-ttu-id="7c113-189">若要使用 IPv6 位址指定目的電腦，請在授權規則使用原始 IPv6 位址 (包含冒號)。</span><span class="sxs-lookup"><span data-stu-id="7c113-189">To specify a destination computer by using an IPv6 address, use the original IPv6 address (that contains colons) in the authorization rule.</span></span>
<span data-ttu-id="7c113-190">在 [Windows PowerShell Web 存取] 登入頁面中，支援以網域及數字 (含冒號) IPv6 位址做為目標電腦名稱，但在授權規則中則不行。</span><span class="sxs-lookup"><span data-stu-id="7c113-190">Both domain and numerical (with colons) IPv6 addresses are supported as the target computer name on the Windows PowerShell Web Access sign-in page, but not in authorization rules.</span></span>

<span data-ttu-id="7c113-191">如需 IPv6 位址的詳細資訊，請參閱 [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx) (IPv6 的運作方式)。</span><span class="sxs-lookup"><span data-stu-id="7c113-191">For more information about IPv6 addresses, see [How IPv6 Works](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="7c113-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c113-192">See Also</span></span>

- <span data-ttu-id="7c113-193">[Windows PowerShell Web 存取的授權規則與安全性功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="7c113-193">[Authorization Rules and Security Features of Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)</span></span>
- <span data-ttu-id="7c113-194">[使用網頁型 Windows PowerShell 主控台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="7c113-194">[Use the Web-based Windows PowerShell Console](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)</span></span>
- [<span data-ttu-id="7c113-195">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="7c113-195">about_Remote_Requirements</span></span>](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
