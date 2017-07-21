---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "解除安裝 Windows PowerShell Web 存取"
ms.openlocfilehash: 7231d5eadceda8e3b28d9a81c2b5dcbe43680ff2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
#  <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="a590d-103">解除安裝 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="a590d-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="a590d-104">更新日期︰2013 年 6 月 24 日</span><span class="sxs-lookup"><span data-stu-id="a590d-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="a590d-105">適用目標︰Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a590d-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="a590d-106">依照此主題中的步驟，從執行 Windows Server 2012 R2 或 Windows Server 2012 的閘道伺服器刪除 Windows PowerShell Web 存取網站及應用程式。</span><span class="sxs-lookup"><span data-stu-id="a590d-106">Follow steps in this topic to delete the Windows PowerShell Web Access website and application from the gateway server that is running either Windows Server 2012 R2 or Windows Server 2012.</span></span> <span data-ttu-id="a590d-107">在開始之前，請通知網頁型主控台的使用者，您正在移除網站。</span><span class="sxs-lookup"><span data-stu-id="a590d-107">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

<span data-ttu-id="a590d-108">從閘道伺服器解除安裝 Windows PowerShell Web 存取之前，請執行 <span class="code">Uninstall-PswaWebApplication</span> Cmdlet 來移除網站及 Windows PowerShell Web 存取 Web 應用程式，或者使用 IIS 管理員程序，[藉由 IIS 管理員刪除 Windows PowerShell Web 存取網站及 Web 應用程式](#BKMK_delsite)。</span><span class="sxs-lookup"><span data-stu-id="a590d-108">Before you uninstall Windows PowerShell Web Access from the gateway server, either run the <span class="code">Uninstall-PswaWebApplication</span> cmdlet to remove the website and Windows PowerShell Web Access web applications, or use the IIS Manager procedure, [To delete the Windows PowerShell Web Access website and web applications by using IIS Manager](#BKMK_delsite).</span></span>

<span data-ttu-id="a590d-109">解除安裝 Windows PowerShell Web 存取不會解除安裝 IIS 或自動安裝的任何其他功能，因為 Windows PowerShell Web 存取需要這些功能才能執行。</span><span class="sxs-lookup"><span data-stu-id="a590d-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="a590d-110">解除安裝程序會保留與 Windows PowerShell Web 存取相依的功能；您可以視需要個別解除安裝這些功能。</span><span class="sxs-lookup"><span data-stu-id="a590d-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

<span data-ttu-id="a590d-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">建議 (快速) 解除安裝</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="a590d-111"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Recommended (quick) uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="a590d-112">本節中的程序可協助您使用 Windows PowerShell Cmdlet 解除安裝 Windows PowerShell Web 存取 Web 應用程式和 Windows PowerShell Web 存取功能。</span><span class="sxs-lookup"><span data-stu-id="a590d-112">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using Windows PowerShell cmdlets.</span></span>

###

<span data-ttu-id="a590d-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 1：刪除 Web 應用程式</span></a></span><span class="sxs-lookup"><span data-stu-id="a590d-113"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="a590d-114">如果您已經指定您自訂的網站名稱，請將 <span class="code">WebsiteName</span> 參數新增至您的命令並指定網站名稱。</span><span class="sxs-lookup"><span data-stu-id="a590d-114">If you have specified your own, custom website name, add the <span class="code">WebsiteName</span> parameter to your command, and specify the website name.</span></span> <span data-ttu-id="a590d-115">如果您已經使用自訂的 Web 應用程式 (不是預設應用程式 **pswa**)，請將 <span class="code">WebApplicationName</span> 參數新增至您的命令，並指定 Web 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="a590d-115">If you have used a custom web application (not the default application, **pswa**, add the <span class="code">WebApplicationName</span> parameter to your command, and specify the name of the web application.</span></span>

#### <a name="to-delete-the-website-and-web-applications-by-using-the-uninstall-pswawebapplication-cmdlet"></a><span data-ttu-id="a590d-116">使用 Uninstall-PswaWebApplication Cmdlet 刪除網站及 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="a590d-116">To delete the website and web applications by using the Uninstall-PswaWebApplication cmdlet</span></span>

1.  <span data-ttu-id="a590d-117">執行下列其中一個動作來開啟 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="a590d-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="a590d-118">在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 [Windows PowerShell]。</span><span class="sxs-lookup"><span data-stu-id="a590d-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="a590d-119">在 Windows **[開始]** 畫面上，按一下 **[Windows PowerShell]**。</span><span class="sxs-lookup"><span data-stu-id="a590d-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2.  <span data-ttu-id="a590d-120">輸入 **Uninstall-PswaWebApplication**，然後按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="a590d-120">Type **Uninstall-PswaWebApplication**, and then press **Enter**.</span></span>

3.  <span data-ttu-id="a590d-121">如果您正在使用測試憑證，請新增 <span class="code">DeleteTestCertificate</span> 參數到此 Cmdlet，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="a590d-121">If you are using a test certificate, add the <span class="code">DeleteTestCertificate</span> parameter to the cmdlet, as shown in the following example.</span></span>

    [<span data-ttu-id="a590d-122">Copy</span><span class="sxs-lookup"><span data-stu-id="a590d-122">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "複製到剪貼簿。")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<span data-ttu-id="a590d-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 2：解除安裝 Windows PowerShell Web 存取</span></a></span><span class="sxs-lookup"><span data-stu-id="a590d-123"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a><span data-ttu-id="a590d-124">使用 Windows PowerShell Cmdlet 解除安裝 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="a590d-124">To uninstall Windows PowerShell Web Access by using Windows PowerShell cmdlets</span></span>

1.  <span data-ttu-id="a590d-125">執行下列其中一個動作，使用提高的使用者權限開啟 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="a590d-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="a590d-126">如果已經開啟工作階段，請移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="a590d-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="a590d-127">在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="a590d-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="a590d-128">在 Windows **[開始]** 畫面上，以滑鼠右鍵按一下 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="a590d-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

2.  <span data-ttu-id="a590d-129">輸入下列命令，然後按 **Enter**，其中 *computer_name* 代表要移除 Windows PowerShell Web 存取的遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="a590d-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="a590d-130">如果移除時需要，<span class="code">-Restart</span> 參數會自動重新啟動目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="a590d-130">The <span class="code">-Restart</span> parameter automatically restarts destination servers if required by the removal.</span></span>

    [<span data-ttu-id="a590d-131">Copy</span><span class="sxs-lookup"><span data-stu-id="a590d-131">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "複製到剪貼簿。")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="a590d-132">若要從離線 VHD 移除角色及功能，您必須新增 <span class="code">-ComputerName</span> 參數及 <span class="code">-VHD</span> 參數。</span><span class="sxs-lookup"><span data-stu-id="a590d-132">To remove roles and features from an offline VHD, you must add both the <span class="code">-ComputerName</span> parameter and the <span class="code">-VHD</span> parameter.</span></span> <span data-ttu-id="a590d-133"><span class="code">-ComputerName</span> 參數包含要掛接 VHD 的伺服器名稱，<span class="code">-VHD</span> 參數則包含指定伺服器上 VHD 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a590d-133">The <span class="code">-ComputerName</span> parameter contains the name of the server on which to mount the VHD, and the <span class="code">-VHD</span> parameter contains the path to the VHD file on the specified server.</span></span>

    [<span data-ttu-id="a590d-134">Copy</span><span class="sxs-lookup"><span data-stu-id="a590d-134">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "複製到剪貼簿。")

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

3.  <span data-ttu-id="a590d-135">完成移除後，請確認是否已移除 Windows PowerShell Web 存取，方法是在 [伺服器管理員] 中開啟 [所有伺服器] 頁面，選取移除功能的伺服器，並檢視所選伺服器頁面上的 [角色和功能] 磚。</span><span class="sxs-lookup"><span data-stu-id="a590d-135">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span> <span data-ttu-id="a590d-136">您也可以針對所選伺服器執行 <span class="code">Get-WindowsFeature</span> Cmdlet (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) 來檢視伺服器上安裝的角色和功能清單。</span><span class="sxs-lookup"><span data-stu-id="a590d-136">You can also run the <span class="code">Get-WindowsFeature</span> cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

<span data-ttu-id="a590d-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">自訂解除安裝</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="a590d-137"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Custom uninstallation</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="a590d-138">本節中的程序可協助您使用伺服器管理員中的「移除角色及功能精靈」和 IIS 管理員主控台，解除安裝 Windows PowerShell Web 存取 Web 應用程式和 Windows PowerShell Web 存取功能。</span><span class="sxs-lookup"><span data-stu-id="a590d-138">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

###

<span data-ttu-id="a590d-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 1：刪除 Web 應用程式</span></a></span><span class="sxs-lookup"><span data-stu-id="a590d-139"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 1: Delete the web application</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-delete-the-windows-powershell-web-access-website-and-web-applications-by-using-iis-manager"></a><span data-ttu-id="a590d-140">使用 IIS 管理員刪除 Windows PowerShell Web 存取網站及 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="a590d-140">To delete the Windows PowerShell Web Access website and web applications by using IIS Manager</span></span>

1.  <span data-ttu-id="a590d-141">執行下列其中一項動作以開啟 IIS 管理員主控台。</span><span class="sxs-lookup"><span data-stu-id="a590d-141">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="a590d-142">如果已經開啟，請移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="a590d-142">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="a590d-143">在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。</span><span class="sxs-lookup"><span data-stu-id="a590d-143">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="a590d-144">在 [伺服器管理員] 的 **[工具]** 功能表上，按一下 **[Internet Information Services (IIS) 管理員]**。</span><span class="sxs-lookup"><span data-stu-id="a590d-144">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="a590d-145">在 Windows [開始] 畫面中，輸入 **Internet Information Services (IIS) 管理員**名稱的任何部分。</span><span class="sxs-lookup"><span data-stu-id="a590d-145">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="a590d-146">當捷徑出現在 [應用程式] 結果時，按一下該捷徑。</span><span class="sxs-lookup"><span data-stu-id="a590d-146">Click the shortcut when it is displayed in the **Apps** results.</span></span>

2.  <span data-ttu-id="a590d-147">在 [IIS 管理員] 樹狀目錄窗格中，選取正在執行 Windows PowerShell Web 存取 Web 應用程式的網站。</span><span class="sxs-lookup"><span data-stu-id="a590d-147">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

3.  <span data-ttu-id="a590d-148">在 **[動作]** 窗格的 **[管理網站]** 下，按一下 **[停止]**。</span><span class="sxs-lookup"><span data-stu-id="a590d-148">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

4.  <span data-ttu-id="a590d-149">在樹狀目錄窗格中，以滑鼠右鍵按一下正在執行 Windows PowerShell Web 存取 Web 應用程式之網站中的 Web 應用程式，然後按一下 **[移除]**。</span><span class="sxs-lookup"><span data-stu-id="a590d-149">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

5.  <span data-ttu-id="a590d-150">在樹狀目錄窗格中，選取 [應用程式集區]，選取 Windows PowerShell Web 存取應用程式集區資料夾，按一下 [動作] 窗格中的 [停止]，然後按一下內容窗格中的 [移除]。</span><span class="sxs-lookup"><span data-stu-id="a590d-150">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

6.  <span data-ttu-id="a590d-151">關閉 [IIS 管理員]。</span><span class="sxs-lookup"><span data-stu-id="a590d-151">Close IIS Manager.</span></span>

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span data-ttu-id="a590d-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></span><span class="sxs-lookup"><span data-stu-id="a590d-152"><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Note </span></span></span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span data-ttu-id="a590d-153">解除安裝期間不會刪除憑證。</span><span class="sxs-lookup"><span data-stu-id="a590d-153">The certificate is not deleted during uninstallation.</span></span> <span data-ttu-id="a590d-154">如果您建立自我簽署憑證，或使用測試憑證並想要將它移除，請在 IIS 管理員中刪除憑證。</span><span class="sxs-lookup"><span data-stu-id="a590d-154">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span></p></td>
    </tr>
    </tbody>
    </table>

###

<span data-ttu-id="a590d-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 2：解除安裝 Windows PowerShell Web 存取</span></a></span><span class="sxs-lookup"><span data-stu-id="a590d-155"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Step 2: Uninstall Windows PowerShell Web Access</span></a></span></span>

------------------------------------------------------------------------

#### <a name="to-uninstall-windows-powershell-web-access-by-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="a590d-156">使用移除角色及功能精靈解除安裝 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="a590d-156">To uninstall Windows PowerShell Web Access by using the Remove Roles and Features Wizard</span></span>

1.  <span data-ttu-id="a590d-157">如果已經開啟伺服器管理員，請移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="a590d-157">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="a590d-158">如果尚未開啟伺服器管理員，請執行下列其中一項動作來將它開啟。</span><span class="sxs-lookup"><span data-stu-id="a590d-158">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="a590d-159">在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。</span><span class="sxs-lookup"><span data-stu-id="a590d-159">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="a590d-160">在 Windows **[開始]** 畫面上，按一下 **[伺服器管理員]**。</span><span class="sxs-lookup"><span data-stu-id="a590d-160">On the Windows **Start** screen, click **Server Manager**.</span></span>

2.  <span data-ttu-id="a590d-161">在 **[管理]** 功能表上，按一下 **[移除角色及功能]**。</span><span class="sxs-lookup"><span data-stu-id="a590d-161">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

3.  <span data-ttu-id="a590d-162">在 [選取目的地伺服器] 頁面上，選取您想要從中移除功能的伺服器或離線 VHD。</span><span class="sxs-lookup"><span data-stu-id="a590d-162">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="a590d-163">若要選取離線 VHD，請先選取要掛接 VHD 的伺服器，然後選取 VHD 檔案。</span><span class="sxs-lookup"><span data-stu-id="a590d-163">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="a590d-164">選取目的地伺服器之後，按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="a590d-164">After you have selected the destination server, click **Next**.</span></span>

4.  <span data-ttu-id="a590d-165">再按一下 [下一步]，跳至 [移除功能] 頁面。</span><span class="sxs-lookup"><span data-stu-id="a590d-165">Click **Next** again to skip to the **Remove features** page.</span></span>

5.  <span data-ttu-id="a590d-166">取消選取 **[Windows PowerShell Web 存取]** 核取方塊，然後按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="a590d-166">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

6.  <span data-ttu-id="a590d-167">在 **[確認移除選項]** 頁面上，按一下 **[移除]**。</span><span class="sxs-lookup"><span data-stu-id="a590d-167">On the **Confirm removal selections** page, click **Remove**.</span></span>

<span data-ttu-id="a590d-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另請參閱</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span><span class="sxs-lookup"><span data-stu-id="a590d-168"><a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">See Also</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a></span></span>

------------------------------------------------------------------------

<span data-ttu-id="a590d-169">[安裝和使用 Windows PowerShell Web 存取](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS 管理員 7.0 說明](https://technet.microsoft.com/library/cc732664.aspx)</span><span class="sxs-lookup"><span data-stu-id="a590d-169">[Install and Use Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS Manager 7.0 Help](https://technet.microsoft.com/library/cc732664.aspx)</span></span>

<span data-ttu-id="a590d-170"><span>顯示︰</span>繼承受保護的</span><span class="sxs-lookup"><span data-stu-id="a590d-170"><span>Show:</span> Inherited Protected</span></span>

<span data-ttu-id="a590d-171"><span class="stdr-votetitle">此頁面是否有幫助？</span></span><span class="sxs-lookup"><span data-stu-id="a590d-171"><span class="stdr-votetitle">Was this page helpful?</span></span></span>
<span data-ttu-id="a590d-172">是 否</span><span class="sxs-lookup"><span data-stu-id="a590d-172">Yes No</span></span>

<span data-ttu-id="a590d-173">其他意見反應？</span><span class="sxs-lookup"><span data-stu-id="a590d-173">Additional feedback?</span></span>

<span data-ttu-id="a590d-174"><span class="stdr-count">剩下 <span class="stdr-charcnt">1500</span> 個字元</span> 提交 略過</span><span class="sxs-lookup"><span data-stu-id="a590d-174"><span class="stdr-count"><span class="stdr-charcnt">1500</span> characters remaining</span> Submit Skip this</span></span>

<span data-ttu-id="a590d-175"><span class="stdr-thankyou">謝謝您！</span></span><span class="sxs-lookup"><span data-stu-id="a590d-175"><span class="stdr-thankyou">Thank you!</span></span></span> <span data-ttu-id="a590d-176"><span class="stdr-appreciate">我們非常感謝您的意見反應。</span></span><span class="sxs-lookup"><span data-stu-id="a590d-176"><span class="stdr-appreciate">We appreciate your feedback.</span></span></span>

[<span data-ttu-id="a590d-177">管理您的設定檔</span><span class="sxs-lookup"><span data-stu-id="a590d-177">Manage Your Profile</span></span>](https://social.technet.microsoft.com/profile)

|

<span data-ttu-id="a590d-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"><img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /></span> 網站意見反應</a> 網站意見反應</span><span class="sxs-lookup"><span data-stu-id="a590d-178"><a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Site Feedback</a> Site Feedback</span></span>

<span data-ttu-id="a590d-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span><span class="sxs-lookup"><span data-stu-id="a590d-179"><a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a></span></span>

<span data-ttu-id="a590d-180">請與我們分享您的體驗...</span><span class="sxs-lookup"><span data-stu-id="a590d-180">Tell us about your experience...</span></span>

<span data-ttu-id="a590d-181">頁面是否快速載入？</span><span class="sxs-lookup"><span data-stu-id="a590d-181">Did the page load quickly?</span></span>

<span data-ttu-id="a590d-182"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="a590d-182"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="a590d-183">您喜歡頁面設計嗎？</span><span class="sxs-lookup"><span data-stu-id="a590d-183">Do you like the page design?</span></span>

<span data-ttu-id="a590d-184"><span> 是<span> </span></span> <span> 否<span> </span></span></span><span class="sxs-lookup"><span data-stu-id="a590d-184"><span> Yes<span> </span></span> <span> No<span> </span></span></span></span>

<span data-ttu-id="a590d-185">請告訴我們更多資訊</span><span class="sxs-lookup"><span data-stu-id="a590d-185">Tell us more</span></span>

-   [<span data-ttu-id="a590d-186">電子快訊</span><span class="sxs-lookup"><span data-stu-id="a590d-186">Flash Newsletter</span></span>](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [<span data-ttu-id="a590d-187">與我們連絡</span><span class="sxs-lookup"><span data-stu-id="a590d-187">Contact Us</span></span>](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [<span data-ttu-id="a590d-188">隱私權聲明</span><span class="sxs-lookup"><span data-stu-id="a590d-188">Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
-   |
-   [<span data-ttu-id="a590d-189">使用規定</span><span class="sxs-lookup"><span data-stu-id="a590d-189">Terms of Use</span></span>](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [<span data-ttu-id="a590d-190">商標</span><span class="sxs-lookup"><span data-stu-id="a590d-190">Trademarks</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

<span data-ttu-id="a590d-191">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="a590d-191">© 2016 Microsoft</span></span>

<span data-ttu-id="a590d-192">© 2016 Microsoft</span><span class="sxs-lookup"><span data-stu-id="a590d-192">© 2016 Microsoft</span></span>

<span data-ttu-id="a590d-193">連結至此網站或由此網站參照之第三方指令碼和程式碼，係由擁有此類程式碼之第三方授權予　貴用戶，而非 Microsoft 所授予。</span><span class="sxs-lookup"><span data-stu-id="a590d-193">Third party scripts and code linked to or referenced from this website are licensed to you by the parties that own such code, not by Microsoft.</span></span> <span data-ttu-id="a590d-194">請參閱 ASP.NET Ajax CDN 使用條款 - http://www.asp.net/ajaxlibrary/CDN.ashx。</span><span class="sxs-lookup"><span data-stu-id="a590d-194">See ASP.NET Ajax CDN Terms of Use - http://www.asp.net/ajaxlibrary/CDN.ashx.</span></span>
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

