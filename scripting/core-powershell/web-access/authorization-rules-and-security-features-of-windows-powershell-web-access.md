# Windows PowerShell Web 存取的授權規則與安全性功能

更新日期︰2013 年 6 月 24 日

適用目標︰Windows Server 2012 R2、Windows Server 2012

Windows Server® 2012 R2 和 Windows Server® 2012 中的 Windows PowerShell® Web 存取具有受限制的安全性模型。 您必須明確授與使用者存取權，他們才能登入 Windows PowerShell Web 存取閘道並使用網頁型 Windows PowerShell 主控台。

-   [設定授權規則及站台安全性](#BKMK_auth)

-   [工作階段管理](#BKMK_sesmgmt)


安裝 Windows PowerShell Web 存取並設定閘道之後，使用者就可以在瀏覽器中開啟登入頁面，但是必須等到 Windows PowerShell Web 存取系統管理員明確授與使用者存取權之後，才能登入。 您可以使用下表所述的 Windows PowerShell Cmdlet，來管理 Windows PowerShell Web 存取存取控制。 沒有適用於新增或管理授權規則的 GUI。 如需 Windows PowerShell Web 存取 Cmdlet 的詳細資訊，請參閱 Cmdlet 參考主題 [Windows PowerShell Web 存取 Cmdlet](https://technet.microsoft.com/library/hh918342.aspx).

系統管理員可以為 Windows PowerShell Web 存取定義 0-*n* 個驗證規則。 預設的安全性是用來限制動作而不是允許動作；零驗證規則表示沒有任何使用者有權存取任何內容。

Windows Server 2012 R2 中的 Add-PswaAuthorizationRule 和 Test-PswaAuthorizationRule 包含可讓您從遠端電腦或從作用中的 Windows PowerShell Web 存取工作階段，新增和測試 Windows PowerShell Web 存取授權規則的 Credential 參數。 如同其他具有 Credential 參數的 Windows PowerShell Cmdlet，您可以將 PSCredential 物件指定為此參數的值。 若要建立 PSCredential 物件且包含您要傳遞至遠端電腦的認證，請執行 [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx) Cmdlet。

Windows PowerShell Web 存取驗證規則是白名單規則。 每個規則都是使用者、目標電腦及指定目標電腦上特定 Windows PowerShell [工作階段設定](https://technet.microsoft.com/library/dd819508.aspx) (也稱為端點或 Runspace) 間允許連線的定義。

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 安全性注意事項 </span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>只要一個規則為真，使用者就可以進行存取。 如果已為使用者授與某部電腦的存取權 (無論是完整語言存取或只能存取 Windows PowerShell 遠端管理 Cmdlet)，使用者都可以從網頁型主控台登入 (或跳躍) 至已與第一部目標電腦連線的其他電腦。 設定 Windows PowerShell Web 存取最安全的方法就是只允許使用者存取受限制的工作階段設定 (也稱為端點或 Runspace)，讓他們能夠完成通常需要遠端執行的特定工作。</p></td>
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
<th><p>名稱</p></th>
<th><p>描述</p></th>
<th><p>參數</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/library/jj592890.aspx">Add-PswaAuthorizationRule</a></p></td>
<td><p>在 Windows PowerShell Web 存取授權規則集中新增授權規則。</p></td>
<td><ul>
<li><p>ComputerGroupName</p></li>
<li><p>ComputerName</p></li>
<li><p>ConfigurationName</p></li>
<li><p>RuleName</p></li>
<li><p>UserGroupName</p></li>
<li><p>UserName</p></li>
<li><p>認證 (Windows Server 2012 R2 和更新版本)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/library/jj592893.aspx">Remove-PswaAuthorizationRule</a></p></td>
<td><p>從 Windows PowerShell Web 存取中移除指定的授權規則。</p></td>
<td><ul>
<li><p>Id</p></li>
<li><p>RuleName</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/library/jj592891.aspx">Get-PswaAuthorizationRule</a></p></td>
<td><p>傳回一組 Windows PowerShell Web 存取授權規則。 如果未使用任何參數，Cmdlet 會傳回所有規則。</p></td>
<td><ul>
<li><p>Id</p></li>
<li><p>RuleName</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/library/jj592892.aspx">Test-PswaAuthorizationRule</a></p></td>
<td><p>評估授權規則以判斷特定使用者、電腦或工作階段設定存取要求是否已經過授權。 根據預設，如果沒有加入參數，Cmdlet 會評估所有的授權規則。 系統管理員可以新增參數，指定授權規則或規則子集來進行測試。</p></td>
<td><ul>
<li><p>ComputerName</p></li>
<li><p>ConfigurationName</p></li>
<li><p>RuleName</p></li>
<li><p>UserName</p></li>
<li><p>認證 (Windows Server 2012 R2 和更新版本)</p></li>
</ul></td>
</tr>
</tbody>
</table>

上述 Cmdlet 可建立一組存取規則，用來為 Windows PowerShell Web 存取閘道上的使用者授與權限。 這些規則與目的地電腦上的存取控制清單 (ACL) 不同，且可以為 Web 存取提供額外的安全性。 下節將有更詳細的安全性說明。

如果使用者無法通過上述任何安全性階層，他們會在瀏覽器視窗收到一般「拒絕存取」訊息。 雖然閘道伺服器會記錄安全性細節，但是不會對一般使用者顯示他們通過多少安全性階層，或在哪一個階層發生登入或驗證失敗。

如需設定授權規則的詳細資訊，請參閱本主題中的[設定授權規則](#BKMK_configrules)。

<a href="" id="BKMK_sec"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">安全性</span></a>

------------------------------------------------------------------------

Windows PowerShell Web 存取安全性模型在網頁型主控台的一般使用者與目標電腦之間有四個階層。 Windows PowerShell Web 存取系統管理員可以在 IIS 管理員主控台中，透過其他設定來增加安全性階層。 如需在 IIS 管理員主控台中保護網站安全的詳細資訊，請參閱[設定網頁伺服器安全性 (IIS 7)](https://technet.microsoft.com/library/cc731278(v=ws.10).aspx)。 如需 IIS 最佳做法及防止拒絕服務攻擊的詳細資訊，請參閱[防止 DoS/拒絕服務攻擊的最佳做法](https://technet.microsoft.com/library/cc750213.aspx)。 系統管理員也可以購買並安裝其他零售的驗證軟體。

下表說明一般使用者與目標電腦之間的四個安全性階層。

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>順序</p></th>
<th><p>階層</p></th>
<th><p>描述</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>網頁伺服器 (IIS) 安全性功能，例如用戶端憑證驗證</p></td>
<td><p>Windows PowerShell Web 存取使用者一律必須提供使用者名稱及密碼，才能在閘道上驗證他們的帳戶。 不過，Windows PowerShell Web 存取系統管理員也可以開啟或關閉選擇性的用戶端憑證驗證 (請參閱<a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">安裝和使用 Windows PowerShell Web 存取</a>中的＜使用 IIS 管理員在現有的網站中設定閘道＞的步驟 10)。 選擇性用戶端憑證功能要求一般使用者除了使用者名稱及密碼之外還需具備有效的用戶端憑證，而這也是網頁伺服器 (IIS) 設定的一部份。 啟用用戶端憑證層時，Windows PowerShell Web 存取登入頁面會提示使用者提供有效的憑證，才能評估他們的登入認證。 用戶端憑證驗證會自動檢查用戶端憑證。</p>
<p>如果找不到有效的憑證，Windows PowerShell Web 存取會通知使用者，讓使用者可以提供憑證。 如果找到有效的用戶端憑證，Windows PowerShell Web 存取會為使用者開啟登入頁面，讓他們提供使用者名稱及密碼。</p>
<p>這是網頁伺服器 (IIS) 提供額外安全性設定的範例。 如需其他 IIS 安全性功能的詳細資訊，請參閱<a href="https://technet.microsoft.com/library/cc731278(ws.10).aspx">設定網頁伺服器安全性 (IIS 7)</a>.</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Windows PowerShell Web 存取表單型閘道驗證</p></td>
<td><p>Windows PowerShell Web 存取登入頁面會要求一組認證 (使用者名稱及密碼)，並提供選項，讓使用者為目標電腦提供不同的認證。 如果使用者沒有提供替代認證，就會使用連線閘道的主要使用者名稱及密碼來連線目標電腦。</p>
<p>所需的認證會在 Windows PowerShell Web 存取閘道上進行驗證。 這些認證必須是本機 Windows PowerShell Web 存取閘道伺服器上或 Active Directory® 中的有效使用者帳戶。</p>
<p>當使用者通過閘道上的驗證之後，Windows PowerShell Web 存取會檢查授權規則，以確定使用者是否有權存取要求的目標電腦。 成功授權之後，使用者的認證就會傳送到目標電腦。</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>Windows PowerShell Web 存取授權規則</p></td>
<td><p>當使用者通過閘道上的驗證之後，Windows PowerShell Web 存取會檢查授權規則，以確定使用者是否有權存取要求的目標電腦。 成功授權之後，使用者的認證就會傳送到目標電腦。</p>
<p>只有在使用者通過閘道驗證之後，目標電腦驗證使用者之前，才會評估這些規則。</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>目標驗證及授權規則</p></td>
<td><p>Windows PowerShell Web 存取的最終安全性階層是目標電腦本身的安全性設定。 使用者必須在目標電腦上及 Windows PowerShell Web 存取授權規則中設定適當的存取權，才能執行 Windows PowerShell 網頁型主控台，透過 Windows PowerShell Web 存取來影響目標電腦。</p>
<p>這個階層提供的安全性機制，與使用者嘗試在 Windows PowerShell 內執行 <strong>Enter-PSSession</strong> 或 <strong>New-PSSession</strong> Cmdlet，以建立目標電腦的遠端 Windows PowerShell 工作階段時所用的評估連線嘗試安全性機制相同。</p>
<p>根據預設，Windows PowerShell Web 存取在閘道及目標電腦上都會使用主要的使用者名稱和密碼進行驗證。 網頁型登入頁面會在標題為<strong>選用連線設定</strong>的區段中提供選項，讓使用者可視需要為目標電腦提供不同的認證。 如果使用者沒有提供替代認證，就會使用連線閘道的主要使用者名稱及密碼來連線目標電腦。</p>
<p>授權規則可用來允許使用者存取特定工作階段設定。 您可以為 Windows PowerShell Web 存取建立受限制的 Runspace 或工作階段設定，並允許特定使用者在登入 Windows PowerShell Web 存取時只能連線到特定的工作階段設定。 您可以使用存取控制清單 (ACL) 來判斷哪些使用者有權存取特定端點，然後使用本節描述的授權規則進一步限制特定使用者組的端點存取權。 如需受限制的 Runspace 詳細資訊，請參閱 MSDN 上的<a href="https://msdn.microsoft.com/library/windows/desktop/ee706589.aspx">受限制的 Runspace</a>。</p></td>
</tr>
</tbody>
</table>

<a href="" id="BKMK_configrules"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">設定授權規則</span></a>

------------------------------------------------------------------------

系統管理員很可能想要針對 Windows PowerShell Web 存取使用者，將已在其環境中定義的同一個授權規則套用到 Windows PowerShell 遠端管理。 本節的第一個程序描述如何新增授與一位使用者存取權、登入以管理一部電腦，以及單一工作階段設定內的安全性規則。 第二個程序描述如何移除不再需要的授權規則。

如果您打算使用自訂工作階段設定來允許特定使用者只能在 Windows PowerShell Web 存取中受限制的 Runspace 內工作，請先建立您的自訂工作階段設定，然後再新增參考這些設定的授權規則。 您不能使用 Windows PowerShell Web 存取 Cmdlet 來建立自訂的工作階段設定。 如需建立自訂工作階段設定的詳細資訊，請參閱 MSDN 上的 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx)。

Windows PowerShell Web 存取 Cmdlet 支援一個萬用字元，也就是星號 ( * )。 不支援在字串中使用萬用字元；每一個屬性 (使用者、電腦或工作階段設定) 使用單一星號。

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
<td><p>如需更多您可以使用授權規則來授與使用者存取權及協助保護 Windows PowerShell Web 存取環境的方法，請參閱本主題中的<a href="#BKMK_others">其他授權規則案例</a>。</p></td>
</tr>
</tbody>
</table>

#### 新增限制性授權規則

1.  執行下列其中一個動作，使用提高的使用者權限開啟 Windows PowerShell 工作階段。

    -   在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 [Windows PowerShell]，然後按一下 [以系統管理員身分執行].

    -   在 Windows [開始] 畫面上，以滑鼠右鍵按一下 [Windows PowerShell]，然後按一下 [以系統管理員身分執行].

2.  <span class="label">使用工作階段設定來限制使用者存取的選擇性步驟：</span>確定您要在規則中使用的工作階段設定已經存在。 如果尚未建立這些設定，請使用 MSDN 上 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) 中建立工作階段設定的指示。

3.  輸入下列程式碼，然後按 **Enter**.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_1079478f-cd51-4d35-8022-4b532a9d57a4'); "複製到剪貼簿。")

        Add-PswaAuthorizationRule –UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    這個授權規則允許特定使用者存取網路上他們通常有權存取的一部電腦，以及該使用者在一般編寫指令碼及 Cmdlet 範圍內的特定工作階段設定存取權。 在下列範例中，<span class="code">Contoso</span> 網域中名為 <span class="code">JSmith</span> 的使用者會被授與管理電腦 <span class="code">Contoso_214</span> 的存取權，並使用名為 <span class="code">NewAdminsOnly 的工作階段設定</span>.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4e760377-e401-4ef4-988f-7a0aec1b2a90'); "複製到剪貼簿。")

        Add-PswaAuthorizationRule –UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  確認已執行 **Get-PswaAuthorizationRule** Cmdlet 或 **Test-PswaAuthorizationRule -UserName &lt;domain\user | computer\user&gt; -ComputerName** &lt;computer_name&gt; 來建立規則。 例如，**Test-PswaAuthorizationRule –UserName Contoso\JSmith –ComputerName Contoso_214**.

#### 移除授權規則

1.  如果尚未開啟 Windows PowerShell 工作階段，請參閱本節中[新增非限制性授權規則](#BKMK_arar)的步驟 1。

2.  輸入下列資訊，然後按下 **Enter**，其中 *rule ID* 代表您想要移除之規則的唯一識別碼。

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0daef66d-0ecf-47fb-a8a0-d4dbceb8409d'); "複製到剪貼簿。")

        Remove-PswaAuthorizationRule -ID <rule ID>

    或者，如果您不知道識別碼，但是知道您想要移除之規則的好記名稱，您可以取得規則的名稱，並將它傳送到 <span class="code">Remove-PswaAuthorizationRule</span> Cmdlet 來移除規則，如下列範例所示：Get-PswaAuthorizationRule -RuleName &lt;*rule name*&gt; | Remove-PswaAuthorizationRule。

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
    <td><p>系統不會提示您確認是否要刪除指定的授權規則；當您按下 <strong>Enter</strong> 時就會刪除該規則。 執行 <strong>Remove-PswaAuthorizationRule</strong> Cmdlet 之前，請先確定您要移除該授權規則。</p></td>
    </tr>
    </tbody>
    </table>

<a href="" id="BKMK_others"></a>
####

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">其他授權規則案例</span></a>

------------------------------------------------------------------------

每一個 Windows PowerShell 工作階段都會使用一個工作階段設定；如果未針對工作階段指定這類設定，Windows PowerShell 就會使用預設的內建 Windows PowerShell 工作階段設定 (稱為 Microsoft.PowerShell)。 預設的工作階段設定包含電腦可用的所有 Cmdlet。 系統管理員可以使用受限制的 Runspace (一般使用者可以執行之有限範圍內的 Cmdlet 及工作) 來定義工作階段設定，以便限制所有電腦的存取權。 如果已為使用者授與某部電腦的存取權 (無論完整的語言存取權或只能存取 Windows PowerShell 遠端管理 Cmdlet)，該使用者就能連線到已與第一部電腦連線的其他電腦。 定義受限制的 Runspace 可防止使用者從他們允許的 Windows PowerShell Runspace 存取其他電腦，而且還可以提升 Windows PowerShell Web 存取環境的安全性。 工作階段設定可以散佈 (使用群組原則) 到系統管理員想要透過 Windows PowerShell Web 存取來存取的所有電腦。 如需工作階段設定的詳細資訊，請參閱 [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)。 下面是這個案例的一些範例。

-   系統管理員會建立一個含有受限制 Runspace 的端點，稱為 **PswaEndpoint**。 然後，系統管理員會建立一個規則 ***,*,PswaEndpoint**，並將該端點散佈到其他電腦。 這個規則允許所有使用者存取具有端點 **PswaEndpoint** 的所有電腦。 如果這是規則集中定義的唯一授權規則，就無法存取不具該端點的電腦。

-   系統管理員建立了含有受限制 Runspace 的端點 **PswaEndpoint**，並想要限制特定使用者的存取權。 系統管理員建立了一個名為 **Level1Support** 的使用者群組，並定義下列規則：**Level1Support,*,PswaEndpoint**。 這個規則可讓 **Level1Support** 群組中的所有使用者有權存取具有 **PswaEndpoint** 設定的所有電腦。 同樣也可以限制特定電腦組的存取權。

-   有些系統管理員會提供比其他使用者更多的存取權給特定使用者。 例如，系統管理員建立兩個使用者群組 **Admins** 和 **BasicSupport**。 系統管理員還會建立含有受限制 Runspace 的端點 **PswaEndpoint**，並定義下列兩個規則：**Admins,*,\*** 和 **BasicSupport,*,PswaEndpoint**。 第一個規則可讓 **Admin** 群組中的所有使用者存取所有電腦，而第二個規則只能讓 **BasicSupport** 群組中的所有使用者存取具有 **PswaEndpoint** 的電腦.

-   某系統管理員已經設定私人測試環境，且想要讓所有已獲授權的網路使用者在網路上存取他們通常可以存取的所有電腦，以及存取他們通常可以存取的所有工作階段設定。 因為這是私人測試環境，所以系統管理員建立的授權規則並不安全。 系統管理員會執行 <span class="code">Add-PswaAuthorizationRule * * *</span> Cmdlet，其中使用萬用字元 **\*** 來代表所有使用者、所有電腦及所有設定。 此規則相當於下列內容︰<span class="code">Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *</span>.

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 安全性注意事項 </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>如需安全的環境，不建議使用這個規則，並略過 Windows PowerShell Web 存取所提供的授權規則安全性階層。</p></td>
    </tr>
    </tbody>
    </table>

-   系統管理員必須讓使用者在包含工作群組和網域的環境中連線到目標電腦，在這種環境中，工作群組電腦偶爾會用來連線到網域的目標電腦，而網域中的電腦偶爾也會用來連線工作群組中的目標電腦。 系統管理員在工作群組中有閘道伺服器 *PswaServer*；網域中則有目標電腦 *srv1.contoso.com*。 使用者 *Chris* 是工作群組閘道伺服器和目標電腦上的授權本機使用者。 他在工作群組伺服器的使用者名稱為 *chrisLocal*；而他在目標電腦的使用者名稱為 *contoso\chris*。 如果要授與 Chris 存取 srv1.contoso.com 的權限，系統管理員要新增下列規則。

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_8d183d3d-1c19-44b8-9297-530b0efc7c79'); "複製到剪貼簿。")

        Add-PswaAuthorizationRule –userName PswaServer\chrisLocal –computerName srv1.contoso.com –configurationName Microsoft.PowerShell

    之前的規則範例會在閘道伺服器驗證 Chris，然後授與他存取 *srv1* 的權限。 在登入頁面上，Chris 必須在 [選用連線設定] 區域 (*contoso\chris*) 中提供第二組認證。 閘道伺服器會使用這組額外的認證，在目標電腦 *srv1.contoso.com* 上驗證他.

    在先前的案例中，Windows PowerShell Web 存取必須先成功完成下列各項且至少獲得一個授權規則的允許，才能順利建立與目標電腦的連線。

    1.  利用 *server_name*\\*user_name* 格式將使用者名稱新增到授權規則，以便在工作群組閘道伺服器上進行驗證

    2.  使用登入頁面上 [選用連線設定] 區域中提供的替代認證，在目標電腦上進行驗證

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
    <td><p>如果閘道與目標電腦位於不同的工作群組或網域，則必須建立兩個工作群組電腦、兩個網域或工作群組及網域間的信任關係。 這個關係無法使用 Windows PowerShell Web 存取授權規則 Cmdlet 進行設定。 授權規則無法定義電腦間的信任關係，只能授權讓使用者連線到特定目標電腦和工作階段設定。 如需如何設定不同網域間信任關係的詳細資訊，請參閱<a href="https://technet.microsoft.com/library/cc794775.aspx">建立網域及樹系信任</a>。 如需如何將工作群組電腦新增至信任主機清單的詳細資訊，請參閱<a href="https://technet.microsoft.com/library/dd759202.aspx">使用伺服器管理員進行遠端管理</a>.</p></td>
    </tr>
    </tbody>
    </table>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">對多個站台使用一組授權規則</span></a>

------------------------------------------------------------------------

授權規則儲存在 XML 檔案中。 根據預設，XML 檔案的路徑名稱為 %windir%\Web\PowershellWebAccess\data\AuthorizationRules.xml。

授權規則 XML 檔案的路徑儲存在 **powwa.config** 檔案中，它的位置在 %windir%\Web\PowershellWebAccess\data。 系統管理員可彈性變更 **powwa.config** 中預設路徑的參照，以符合喜好設定或需求。 如有需要，系統管理員可以變更這個檔案的位置，讓多個 Windows PowerShell Web 存取閘道使用相同的授權規則。

<a href="" id="BKMK_sesmgmt"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">工作階段管理</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

根據預設，Windows PowerShell Web 存取會將使用者限制為一次三個工作階段。 您可以在 IIS 管理員中編輯 Web 應用程式的 **web.config** 檔案，以支援每位使用者不同的工作階段數目。 **web.config** 檔案的路徑為 $Env:Windir\Web\PowerShellWebAccess\wwwroot\Web.config。

根據預設，只要編輯任何設定，網頁伺服器 (IIS) 就會重新啟動應用程式集區。 例如，如果變更 **web.config** 檔案，就會重新啟動應用程式集區。 因為 Windows PowerShell Web 存取會使用記憶體中的工作階段狀態，所以登入 Windows PowerShell Web 存取工作階段的使用者會在應用程式集區重新啟動後遺失他們的工作階段。

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">設定登入頁面的預設參數</span></a>

------------------------------------------------------------------------

如果您的 Windows PowerShell Web 存取閘道正在 Windows Server 2012 R2 上執行，您就可以針對 Windows PowerShell Web 存取登入頁面上顯示的設定來設定預設值。 您可以在上一段中說明的 **web.config** 檔案中設定值。 登入頁面設定的預設值位於 web.config 檔案的 **appSettings** 區段中；以下是 **appSettings** 區段的範例。 其中許多設定的有效值，都與 Windows PowerShell 中的 [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) Cmdlet 的對應參數相同。 例如，<span class="code">defaultApplicationName</span> 索引鍵 (如下列程式碼區塊所示) 即為目標電腦上的 **$PSSessionApplicationName** 喜好設定變數值。

[Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_6ccfd0a1-485a-4ac5-9636-89ebab501bef'); "複製到剪貼簿。")

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

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">逾時和非計劃的連線中斷</span></a>

------------------------------------------------------------------------

Windows PowerShell Web 存取工作階段逾時。 在 Windows Server 2012 上執行的 Windows PowerShell Web 存取中，當工作階段停止活動超過 15 分鐘後，登入使用者就會看到逾時訊息。 如果使用者沒有在逾時訊息顯示後五分鐘內回應，該工作階段就會結束，使用者也會登出。 您可以在 IIS 管理員的網站設定中，變更工作階段的逾時期間。

在 Windows Server 2012 R2 上執行的 Windows PowerShell Web 存取中，根據預設，工作階段會在停止活動超過 20 分鐘後逾時。 如果使用者因為網路錯誤或其他非計劃性關機或失敗 (而不是因為他們自行關閉工作階段) 而從網頁型主控台中斷工作階段的連線，Windows PowerShell Web 存取工作階段就會繼續執行且連線到目標電腦，直到用戶端的逾時期間結束為止。 工作階段會在預設的 20 分鐘或閘道系統管理員所指定的逾時期間之後中斷連線，視何者較短而定。

如果閘道伺服器正在執行 Windows Server 2012 R2，Windows PowerShell Web 存取就能讓使用者在稍後重新連線到已儲存的工作階段，但如果工作階段是因為網路錯誤、非計劃性關機或其他失敗而中斷連線，則在閘道系統管理員指定的逾時期間結束之前，使用者將無法檢視或重新連線到已儲存的工作階段。

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另請參閱</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[安裝和使用 Windows PowerShell Web 存取](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
[Windows PowerShell Web 存取 Cmdlet](https://technet.microsoft.com/library/hh918342.aspx)

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


