---
title:  解除安裝 Windows PowerShell Web 存取
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
---

#  解除安裝 Windows PowerShell Web 存取

更新日期︰2013 年 6 月 24 日

適用目標︰Windows Server 2012 R2、Windows Server 2012

依照此主題中的步驟，從執行 Windows Server 2012 R2 或 Windows Server 2012 的閘道伺服器刪除 Windows PowerShell Web 存取網站及應用程式。 在開始之前，請通知網頁型主控台的使用者，您正在移除網站。

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

從閘道伺服器解除安裝 Windows PowerShell Web 存取之前，請執行 <span class="code">Uninstall-PswaWebApplication</span> Cmdlet 來移除網站及 Windows PowerShell Web 存取 Web 應用程式，或者使用 IIS 管理員程序，[藉由 IIS 管理員刪除 Windows PowerShell Web 存取網站及 Web 應用程式](#BKMK_delsite)。

解除安裝 Windows PowerShell Web 存取不會解除安裝 IIS 或自動安裝的任何其他功能，因為 Windows PowerShell Web 存取需要這些功能才能執行。 解除安裝程序會保留與 Windows PowerShell Web 存取相依的功能；您可以視需要個別解除安裝這些功能。

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">建議 (快速) 解除安裝</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

本節中的程序可協助您使用 Windows PowerShell Cmdlet 解除安裝 Windows PowerShell Web 存取 Web 應用程式和 Windows PowerShell Web 存取功能。

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 1：刪除 Web 應用程式</span></a>

------------------------------------------------------------------------

如果您已經指定您自訂的網站名稱，請將 <span class="code">WebsiteName</span> 參數新增至您的命令並指定網站名稱。 如果您已經使用自訂的 Web 應用程式 (不是預設應用程式 **pswa**)，請將 <span class="code">WebApplicationName</span> 參數新增至您的命令，並指定 Web 應用程式的名稱。

#### 使用 Uninstall-PswaWebApplication Cmdlet 刪除網站及 Web 應用程式

1.  執行下列其中一個動作來開啟 Windows PowerShell 工作階段。

    -   在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 [Windows PowerShell]。

    -   在 Windows **[開始]** 畫面上，按一下 **[Windows PowerShell]**。

2.  輸入 **Uninstall-PswaWebApplication**，然後按 **Enter**。

3.  如果您正在使用測試憑證，請新增 <span class="code">DeleteTestCertificate</span> 參數到此 Cmdlet，如以下範例所示。

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "複製到剪貼簿。")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 2：解除安裝 Windows PowerShell Web 存取</span></a>

------------------------------------------------------------------------

#### 使用 Windows PowerShell Cmdlet 解除安裝 Windows PowerShell Web 存取

1.  執行下列其中一個動作，使用提高的使用者權限開啟 Windows PowerShell 工作階段。 如果已經開啟工作階段，請移至下一個步驟。

    -   在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。

    -   在 Windows **[開始]** 畫面上，以滑鼠右鍵按一下 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。

2.  輸入下列命令，然後按 **Enter**，其中 *computer\_name* 代表要移除 Windows PowerShell Web 存取的遠端伺服器。 如果移除時需要，<span class="code">–Restart</span> 參數會自動重新啟動目的地伺服器。

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "複製到剪貼簿。")

        Uninstall-WindowsFeature –Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    若要從離線 VHD 移除角色及功能，您必須新增 <span class="code">-ComputerName</span> 參數及 <span class="code">-VHD</span> 參數。 <span class="code">-ComputerName</span> 參數包含要掛接 VHD 的伺服器名稱，<span class="code">-VHD</span> 參數則包含指定伺服器上 VHD 檔案的路徑。

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "複製到剪貼簿。")

        Uninstall-WindowsFeature –Name WindowsPowerShellWebAccess –VHD <path> -ComputerName <computer_name> -Restart

3.  完成移除後，請確認是否已移除 Windows PowerShell Web 存取，方法是在 [伺服器管理員] 中開啟 [所有伺服器] 頁面，選取移除功能的伺服器，並檢視所選伺服器頁面上的 [角色和功能] 磚。 您也可以針對所選伺服器執行 <span class="code">Get-WindowsFeature</span> Cmdlet (Get-WindowsFeature -ComputerName &lt;*computer\_name*&gt;) 來檢視伺服器上安裝的角色和功能清單。

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">自訂解除安裝</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

本節中的程序可協助您使用伺服器管理員中的「移除角色及功能精靈」和 IIS 管理員主控台，解除安裝 Windows PowerShell Web 存取 Web 應用程式和 Windows PowerShell Web 存取功能。

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 1：刪除 Web 應用程式</span></a>

------------------------------------------------------------------------

#### 使用 IIS 管理員刪除 Windows PowerShell Web 存取網站及 Web 應用程式

1.  執行下列其中一項動作以開啟 IIS 管理員主控台。 如果已經開啟，請移至下一個步驟。

    -   在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。 在 [伺服器管理員] 的 **[工具]** 功能表上，按一下 **[Internet Information Services (IIS) 管理員]**。

    -   在 Windows [開始] 畫面中，輸入 **Internet Information Services (IIS) 管理員**名稱的任何部分。 當捷徑出現在 [應用程式] 結果時，按一下該捷徑。

2.  在 [IIS 管理員] 樹狀目錄窗格中，選取正在執行 Windows PowerShell Web 存取 Web 應用程式的網站。

3.  在 **[動作]** 窗格的 **[管理網站]** 下，按一下 **[停止]**。

4.  在樹狀目錄窗格中，以滑鼠右鍵按一下正在執行 Windows PowerShell Web 存取 Web 應用程式之網站中的 Web 應用程式，然後按一下 **[移除]**。

5.  在樹狀目錄窗格中，選取 [應用程式集區]，選取 Windows PowerShell Web 存取應用程式集區資料夾，按一下 [動作] 窗格中的 [停止]，然後按一下內容窗格中的 [移除]。

6.  關閉 [IIS 管理員]。

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>解除安裝期間不會刪除憑證。 如果您建立自我簽署憑證，或使用測試憑證並想要將它移除，請在 IIS 管理員中刪除憑證。</p></td>
    </tr>
    </tbody>
    </table>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步驟 2：解除安裝 Windows PowerShell Web 存取</span></a>

------------------------------------------------------------------------

#### 使用移除角色及功能精靈解除安裝 Windows PowerShell Web 存取

1.  如果已經開啟伺服器管理員，請移至下一個步驟。 如果尚未開啟伺服器管理員，請執行下列其中一項動作來將它開啟。

    -   在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。

    -   在 Windows **[開始]** 畫面上，按一下 **[伺服器管理員]**。

2.  在 **[管理]** 功能表上，按一下 **[移除角色及功能]**。

3.  在 [選取目的地伺服器] 頁面上，選取您想要從中移除功能的伺服器或離線 VHD。 若要選取離線 VHD，請先選取要掛接 VHD 的伺服器，然後選取 VHD 檔案。 選取目的地伺服器之後，按一下 **[下一步]**。

4.  再按一下 [下一步]，跳至 [移除功能] 頁面。

5.  取消選取 **[Windows PowerShell Web 存取]** 核取方塊，然後按一下 **[下一步]**。

6.  在 **[確認移除選項]** 頁面上，按一下 **[移除]**。

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另請參閱</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[安裝和使用 Windows PowerShell Web 存取](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS 管理員 7.0 說明](https://technet.microsoft.com/library/cc732664.aspx)

<span>顯示︰</span> 繼承受保護的

<span class="stdr-votetitle">此頁面是否有幫助？</span>
是 否

其他意見反應？

<span class="stdr-count"><span class="stdr-charcnt">剩下 1500</span> 個字元</span> 提交略過此步驟

<span class="stdr-thankyou">謝謝您！</span> <span class="stdr-appreciate">我們非常感謝您的意見反應。</span>

[管理您的設定檔](https://social.technet.microsoft.com/profile)

|

<a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> 站台意見反應</a> 站台意見反應

<a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a>

請與我們分享您的體驗...

頁面是否快速載入？

<span> 是<span> </span></span> <span> 否<span> </span></span>

您喜歡頁面設計嗎？

<span> 是<span> </span></span> <span> 否<span> </span></span>

請告訴我們更多資訊

-   [Flash Newsletter](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [與我們連絡](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [隱私權聲明](https://privacy.microsoft.com/privacystatement)
-   |
-   [使用條款](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [商標](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

© 2016 Microsoft

© 2016 Microsoft

連結至此網站或由此網站參照之第三方指令碼和程式碼，係由擁有此類程式碼之第三方授權予　貴用戶，而非 Microsoft 所授予。 請參閱 ASP.NET Ajax CDN 使用條款 – http://www.asp.net/ajaxlibrary/CDN.ashx。
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />



<!--HONumber=May16_HO2-->


