#  疑難排解 Windows PowerShell Web 存取中的存取問題

更新日期︰2013 年 6 月 24 日

適用目標︰Windows Server 2012 R2、Windows Server 2012

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

下表識別使用者在嘗試使用 Windows PowerShell Web 存取連線到遠端電腦時可能經歷的一些常見問題，以及解決這些問題的建議。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>問題</p></th>
<th><p>可能的原因及解決方案</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>登入失敗</p></td>
<td><p>下列各項為可能發生失敗的原因。</p>
<ul>
<li><p>允許使用者存取電腦的授權規則或遠端電腦上的特定工作階段設定不存在。 Windows PowerShell Web 存取安全性受到限制；必須使用授權規則明確授與使用者存取遠端電腦的存取權。 如需建立授權規則的詳細資訊，請參閱本指南中的 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell Web 存取的授權規則與安全性功能</a>。</p></li>
<li><p>使用者沒有存取目的地電腦的權限。 這可由存取控制清單 (ACL) 來判斷。 如需詳細資訊，請參閱<a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">使用網頁型 Windows PowerShell 主控台</a>中的＜登入 Windows PowerShell Web 存取＞，或 <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell 小組部落格</a>.</p>
<ul>
<li><p>目的電腦可能沒有啟用 Windows PowerShell 遠端管理。 確認已在使用者嘗試連線的電腦上啟用這個功能。 如需詳細資訊，請參閱 Windows PowerShell 說明主題中 <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> 的＜如何設定電腦的遠端功能＞一節。</p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p>當使用者嘗試在 Internet Explorer 視窗登入 Windows PowerShell Web 存取時，會看到 [內部伺服器錯誤]<strong></strong> 頁面或 Internet Explorer 停止回應。 這是只有 Internet Explorer 會發生的問題。</p></td>
<td><p>當使用者使用含有中文字元的網域名稱登入，或閘道伺服器名稱含有一或多個中文字元時，會發生這個問題。 若要解決這個問題，使用者應<a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">安裝和執行 Internet Explorer 10</a>，然後執行下列步驟。</p>
<ol>
<li><p>將 Internet Explorer [文件模式]<strong></strong> 設定變更成 [IE10 標準]<strong></strong>.</p>
<ol>
<li><p>按 <strong>F12</strong> 開啟開發人員工具主控台。</p></li>
<li><p>在 Internet Explorer 10 中，按一下 [瀏覽器模式]<strong></strong>，然後選取 [Internet Explorer 10]<strong></strong>.</p></li>
<li><p>按一下 [文件模式]<strong></strong>，然後按一下 [IE10 標準]<strong></strong>.</p></li>
<li><p>再按一次 <strong>F12</strong> 關閉開發人員工具主控台。</p></li>
</ol></li>
<li><p>停用自動 Proxy 設定。</p>
<ol>
<li><p>在 Internet Explorer 10 中，按一下 [工具]<strong></strong>，然後按一下 [網際網路選項]<strong></strong>.</p></li>
<li><p>在 [網際網路選項]<strong></strong> 對話方塊的 [連線]<strong></strong> 索引標籤，按一下 [區域網路設定]<strong></strong>.</p></li>
<li><p>清除 [自動偵測設定]<strong></strong> 核取方塊。 按一下 [確定]<strong></strong>，然後再按一次 [確定]<strong></strong> 關閉 [網際網路選項]<strong></strong> 對話方塊。</p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>無法連線到遠端工作群組電腦</p></td>
<td><p>如果目的電腦是工作群組的成員，請使用下列語法提供您的使用者名稱並登入電腦：&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>即使已安裝角色，仍找不到網頁伺服器 (IIS) 管理工具</p></td>
<td><p>如果您使用 <span class="code">Install-WindowsFeature</span> Cmdlet 安裝 Windows PowerShell Web 存取，除非將 <span class="code">IncludeManagementTools</span> 參數新增到 Cmdlet，否則不會安裝管理工具。 如需範例，請參閱<a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">安裝及使用 Windows PowerShell Web 存取</a>中的＜使用 Windows PowerShell Cmdlet 安裝 Windows PowerShell Web 存取＞。 在以閘道伺服器為目標的「新增角色及功能精靈」工作階段選取工具，可以新增 IIS 管理員主控台及您需要的其他 IIS 管理工具。 您可以從 [伺服器管理員] 中開啟 [新增角色及功能精靈]。</p></td>
</tr>
<tr class="odd">
<td><p>無法存取 Windows PowerShell Web 存取網站</p></td>
<td><p>如果在 Internet Explorer 啟用增強式安全性設定 (IE ESC)，您可以新增 Windows PowerShell Web 存取網站到受信任站台清單中，或者停用 IE ESC。 您可以在 [伺服器管理員] 中 [本機伺服器]<strong></strong> 頁面上的 [屬性]<strong></strong> 磚中停用 IE ESC。</p></td>
</tr>
<tr class="even">
<td><p>當閘道伺服器為目的電腦且同時位於工作群組時嘗試連線，會顯示下列錯誤訊息：<strong>授權失敗。 請確認您已獲授權可連線至目的電腦。</strong></p></td>
<td><p>當閘道伺服器也是目的伺服器且位於工作群組時，請指定使用者名稱、電腦名稱，以及下表顯示的使用者群組名稱。 請勿單獨使用點 (.) 來代表電腦名稱。</p>
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
<th><p>案例</p></th>
<th><p>UserName 參數</p></th>
<th><p>UserGroup 參數</p></th>
<th><p>ComputerName 參數</p></th>
<th><p>ComputerGroup 參數</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>閘道伺服器位於網域</p></td>
<td><p><em>Server_name</em>\<em>user_name</em>、Localhost\<em>user_name</em> 或 .\<em>user_name</em></p></td>
<td><p><em>Server_name</em>\<em>user_group</em>、Localhost\<em>user_group</em> 或 .\<em>user_group</em></p></td>
<td><p>閘道伺服器的完整名稱，或 Localhost</p></td>
<td><p><em>Server_name</em>\<em>computer_group</em>、Localhost\<em>computer_group</em> 或 .\<em>computer_group</em></p></td>
</tr>
<tr class="even">
<td><p>閘道伺服器位於工作群組</p></td>
<td><p><em>Server_name</em>\<em>user_name</em>、Localhost\<em>user_name</em> 或 .\<em>user_name</em></p></td>
<td><p><em>Server_name</em>\<em>user_group</em>、Localhost\<em>user_group</em> 或 .\<em>user_group</em></p></td>
<td><p>伺服器名稱</p></td>
<td><p><em>Server_name</em>\<em>computer_group</em>、Localhost\<em>computer_group</em> 或 .\<em>computer_group</em></p></td>
</tr>
</tbody>
</table>
</div>
<p>使用下列其中一種格式的認證以目標電腦身分登入閘道伺服器。</p>
<ul>
<li><p><em>Server_name</em>\<em>user_name</em></p></li>
<li><p>Localhost\<em>user_name</em></p></li>
<li><p>.\<em>使用者名稱</em></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>授權規則顯示安全性識別碼 (SID)，而不是 <em>user_name</em>/<em>computer_name 語法</em> </p></td>
<td><p>可能是規則不再有效，或者 Active Directory 網域服務查詢失敗。 當閘道伺服器曾經位於工作群組，但之後加入網域的案例中，授權規則通常會無效。</p></td>
</tr>
<tr class="even">
<td><p>在授權規則中將目標電腦指定為含網域的 IPv6 位址時，無法登入該目標電腦。</p></td>
<td><p>授權規則不支援網域名稱格式的 IPv6 位址。 若要使用 IPv6 位址指定目的電腦，請在授權規則使用原始 IPv6 位址 (包含冒號)。 在 [Windows PowerShell Web 存取] 登入頁面中，支援以網域及數字 (含冒號) IPv6 位址做為目標電腦名稱，但在授權規則中則不行。 如需 IPv6 位址的詳細資訊，請參閱 <a href="https://technet.microsoft.com/library/cc781672.aspx">IPv6 的運作方式</a>.</p></td>
</tr>
</tbody>
</table>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另請參閱</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Windows PowerShell Web 存取的授權規則與安全性功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[使用網頁型 Windows PowerShell 主控台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about\_Remote\_Requirements](https://technet.microsoft.com/library/dd315349.aspx)

<span>顯示︰</span> 繼承受保護的

<span class="stdr-votetitle">此頁面是否有幫助？</span>
是
否

其他意見反應？

<span class="stdr-count"><span class="stdr-charcnt">剩餘 1500</span> 個字元</span>
提交
請跳過此項

<span class="stdr-thankyou">感謝您！</span> <span class="stdr-appreciate">我們非常感謝您的意見反應。</span>

[管理您的設定檔](https://social.technet.microsoft.com/profile)

|

<a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> 網站意見反應</a>
網站意見反應

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


