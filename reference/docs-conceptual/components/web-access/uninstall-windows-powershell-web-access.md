---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: 解除安裝 Windows PowerShell Web 存取
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058128"
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="801ac-103">解除安裝 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="801ac-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="801ac-104">更新日期：2013 年 6 月 24 日</span><span class="sxs-lookup"><span data-stu-id="801ac-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="801ac-105">適用於：Windows Server 2012 R2、Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="801ac-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="801ac-106">本主題中的步驟會將 Windows PowerShell Web 存取網站及對應的應用程式，從安裝所在的閘道伺服器移除。</span><span class="sxs-lookup"><span data-stu-id="801ac-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="801ac-107">通知使用者</span><span class="sxs-lookup"><span data-stu-id="801ac-107">Notify users</span></span>

<span data-ttu-id="801ac-108">在開始之前，請通知網頁型主控台的使用者，您正在移除網站。</span><span class="sxs-lookup"><span data-stu-id="801ac-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="801ac-109">解除安裝 Windows PowerShell Web 存取不會解除安裝 IIS 或自動安裝的任何其他功能，因為 Windows PowerShell Web 存取需要這些功能才能執行。</span><span class="sxs-lookup"><span data-stu-id="801ac-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span>
<span data-ttu-id="801ac-110">解除安裝程序會保留與 Windows PowerShell Web 存取相依的功能；您可以視需要個別解除安裝這些功能。</span><span class="sxs-lookup"><span data-stu-id="801ac-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="801ac-111">建議 (快速) 解除安裝</span><span class="sxs-lookup"><span data-stu-id="801ac-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="801ac-112">本節中的程序可協助您解除安裝：</span><span class="sxs-lookup"><span data-stu-id="801ac-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="801ac-113">Windows PowerShell Web 存取 Web 應用程式，以及</span><span class="sxs-lookup"><span data-stu-id="801ac-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="801ac-114">Windows PowerShell Web 存取功能</span><span class="sxs-lookup"><span data-stu-id="801ac-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="801ac-115">其藉由使用 Windows PowerShell Cmdlet 來完成。</span><span class="sxs-lookup"><span data-stu-id="801ac-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="801ac-116">步驟 1：使用 Cmdlet 刪除 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="801ac-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="801ac-117">執行下列其中一個動作來開啟 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="801ac-117">Do one of the following to open a Windows PowerShell session.</span></span>

    -   <span data-ttu-id="801ac-118">在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 [Windows PowerShell]。</span><span class="sxs-lookup"><span data-stu-id="801ac-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>

    -   <span data-ttu-id="801ac-119">在 Windows **[開始]** 畫面上，按一下 **[Windows PowerShell]**。</span><span class="sxs-lookup"><span data-stu-id="801ac-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="801ac-120">輸入 `Uninstall-PswaWebApplication`，然後按 **Enter** 鍵。</span><span class="sxs-lookup"><span data-stu-id="801ac-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>
   1. <span data-ttu-id="801ac-121">如果您已經指定您自訂的網站名稱，請將 `-WebsiteName` 參數新增至您的命令並指定網站名稱。</span><span class="sxs-lookup"><span data-stu-id="801ac-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. <span data-ttu-id="801ac-122">如果您已經使用自訂的 Web 應用程式 (不是預設應用程式 **pswa**)，請將 `-WebApplicationName` 參數新增至您的命令，並指定 Web 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="801ac-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. <span data-ttu-id="801ac-123">如果您使用測試憑證，請新增 `DeleteTestCertificate` 參數到此 Cmdlet，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="801ac-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="801ac-124">步驟 2：使用 Cmdlet 解除安裝 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="801ac-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="801ac-125">執行下列其中一個動作，使用提高的使用者權限開啟 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="801ac-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="801ac-126">如果已經開啟工作階段，請移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="801ac-126">If a session is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="801ac-127">在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="801ac-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>

    -   <span data-ttu-id="801ac-128">在 Windows **[開始]** 畫面上，以滑鼠右鍵按一下 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。</span><span class="sxs-lookup"><span data-stu-id="801ac-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="801ac-129">輸入下列命令，然後按 **Enter**，其中 *computer_name* 代表要移除 Windows PowerShell Web 存取的遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="801ac-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="801ac-130">如果移除時需要， `-Restart` 參數會自動重新啟動目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="801ac-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    <span data-ttu-id="801ac-131">若要從離線 VHD 移除角色及功能，您必須新增 `-ComputerName` 參數及 `-VHD` 參數。</span><span class="sxs-lookup"><span data-stu-id="801ac-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="801ac-132">`-ComputerName` 參數包含要掛接 VHD 的伺服器名稱， `-VHD` 參數則包含指定伺服器上的 VHD 檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="801ac-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. <span data-ttu-id="801ac-133">完成移除後，請確認是否已移除 Windows PowerShell Web 存取，方法是在 [伺服器管理員] 中開啟 [所有伺服器] 頁面，選取移除功能的伺服器，並檢視所選伺服器頁面上的 [角色和功能] 磚。</span><span class="sxs-lookup"><span data-stu-id="801ac-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="801ac-134">您也可以針對所選伺服器執行 `Get-WindowsFeature` Cmdlet (Get-WindowsFeature -ComputerName &lt;電腦名稱&gt;)，檢視伺服器上安裝的角色和功能清單。</span><span class="sxs-lookup"><span data-stu-id="801ac-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="801ac-135">自訂解除安裝</span><span class="sxs-lookup"><span data-stu-id="801ac-135">Custom uninstallation</span></span>

<span data-ttu-id="801ac-136">本節中的程序可協助您使用伺服器管理員中的「移除角色及功能精靈」和 IIS 管理員主控台，解除安裝 Windows PowerShell Web 存取 Web 應用程式和 Windows PowerShell Web 存取功能。</span><span class="sxs-lookup"><span data-stu-id="801ac-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="801ac-137">步驟 1：使用 IIS 管理員刪除 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="801ac-137">Step 1: Delete the web application using IIS Manager</span></span>


1. <span data-ttu-id="801ac-138">執行下列其中一個動作以開啟 IIS 管理員主控台。</span><span class="sxs-lookup"><span data-stu-id="801ac-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="801ac-139">如果已經開啟，請移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="801ac-139">If it is already open, go on to the next step.</span></span>

    -   <span data-ttu-id="801ac-140">在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。</span><span class="sxs-lookup"><span data-stu-id="801ac-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="801ac-141">在 [伺服器管理員] 的 **[工具]** 功能表上，按一下 **[Internet Information Services (IIS) 管理員]**。</span><span class="sxs-lookup"><span data-stu-id="801ac-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

    -   <span data-ttu-id="801ac-142">在 Windows [開始] 畫面中，輸入 **Internet Information Services (IIS) 管理員**名稱的任何部分。</span><span class="sxs-lookup"><span data-stu-id="801ac-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="801ac-143">當捷徑出現在 [應用程式] 結果時，按一下該捷徑。</span><span class="sxs-lookup"><span data-stu-id="801ac-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="801ac-144">在 [IIS 管理員] 樹狀目錄窗格中，選取正在執行 Windows PowerShell Web 存取 Web 應用程式的網站。</span><span class="sxs-lookup"><span data-stu-id="801ac-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="801ac-145">在 **[動作]** 窗格的 **[管理網站]** 下，按一下 **[停止]**。</span><span class="sxs-lookup"><span data-stu-id="801ac-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="801ac-146">在樹狀目錄窗格中，以滑鼠右鍵按一下正在執行 Windows PowerShell Web 存取 Web 應用程式之網站中的 Web 應用程式，然後按一下 **[移除]**。</span><span class="sxs-lookup"><span data-stu-id="801ac-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="801ac-147">在樹狀目錄窗格中，選取 [應用程式集區]，選取 Windows PowerShell Web 存取應用程式集區資料夾，按一下 [動作] 窗格中的 [停止]，然後按一下內容窗格中的 [移除]。</span><span class="sxs-lookup"><span data-stu-id="801ac-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="801ac-148">關閉 [IIS 管理員]。</span><span class="sxs-lookup"><span data-stu-id="801ac-148">Close IIS Manager.</span></span>

> <span data-ttu-id="801ac-149">![警告注意](images/SecurityNote.jpeg)**注意**：</span><span class="sxs-lookup"><span data-stu-id="801ac-149">![Warning note](images/SecurityNote.jpeg)**Note**:</span></span>
>
> <span data-ttu-id="801ac-150">解除安裝期間不會刪除憑證。</span><span class="sxs-lookup"><span data-stu-id="801ac-150">The certificate is not deleted during uninstallation.</span></span>
>
> <span data-ttu-id="801ac-151">如果您建立自我簽署憑證，或使用測試憑證並想要將它移除，請在 IIS 管理員中刪除憑證。</span><span class="sxs-lookup"><span data-stu-id="801ac-151">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="801ac-152">步驟 2：使用移除角色及功能精靈解除安裝 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="801ac-152">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="801ac-153">如果已經開啟伺服器管理員，請移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="801ac-153">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="801ac-154">如果尚未開啟伺服器管理員，請執行下列其中一個動作來將它開啟。</span><span class="sxs-lookup"><span data-stu-id="801ac-154">If Server Manager is not already open, open it by doing one of the following.</span></span>

    -   <span data-ttu-id="801ac-155">在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。</span><span class="sxs-lookup"><span data-stu-id="801ac-155">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>

    -   <span data-ttu-id="801ac-156">在 Windows **[開始]** 畫面上，按一下 **[伺服器管理員]**。</span><span class="sxs-lookup"><span data-stu-id="801ac-156">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="801ac-157">在 **[管理]** 功能表上，按一下 **[移除角色及功能]**。</span><span class="sxs-lookup"><span data-stu-id="801ac-157">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="801ac-158">在 [選取目的地伺服器] 頁面上，選取您想要從中移除功能的伺服器或離線 VHD。</span><span class="sxs-lookup"><span data-stu-id="801ac-158">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="801ac-159">若要選取離線 VHD，請先選取要掛接 VHD 的伺服器，然後選取 VHD 檔案。</span><span class="sxs-lookup"><span data-stu-id="801ac-159">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="801ac-160">選取目的地伺服器之後，按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="801ac-160">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="801ac-161">再按一下 [下一步]，跳至 [移除功能] 頁面。</span><span class="sxs-lookup"><span data-stu-id="801ac-161">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="801ac-162">取消選取 **[Windows PowerShell Web 存取]** 核取方塊，然後按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="801ac-162">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="801ac-163">在 **[確認移除選項]** 頁面上，按一下 **[移除]**。</span><span class="sxs-lookup"><span data-stu-id="801ac-163">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="801ac-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="801ac-164">See Also</span></span>

- [<span data-ttu-id="801ac-165">安裝和使用 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="801ac-165">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="801ac-166">IIS 管理員 7.0 說明</span><span class="sxs-lookup"><span data-stu-id="801ac-166">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)