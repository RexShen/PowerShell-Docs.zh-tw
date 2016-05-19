#  使用網頁型 Windows PowerShell 主控台

更新日期︰2013 年 6 月 24 日

適用目標︰Windows Server 2012 R2、Windows Server 2012

Windows PowerShell® Web 存取可讓 Windows PowerShell® 使用者登入 Secure Sockets Layer (SSL) 保護的網站，以使用 Windows PowerShell 工作階段、Cmdlet 和指令碼來管理遠端電腦。 因為 Windows PowerShell 主控台在網頁瀏覽器中執行，所以可以從各種用戶端裝置開啟，包括行動電話、平板電腦、公用電腦亭、膝上型電腦或共用或借用的電腦。 網頁型 Windows PowerShell 主控台用於使用者在登入處理程序中指定的遠端電腦。 本主題說明如何登入並開始使用 Windows PowerShell Web 存取網頁型主控台。

本主題不會說明如何使用 Windows PowerShell，或執行 Cmdlet 或指令碼。 如需如何使用 Windows PowerShell 及指令碼資源的詳細資訊，請參閱本主題結尾的另請參閱區段。

本主題內容：

-   [支援的瀏覽器及用戶端裝置](#BKMK_browser)

-   [登入 Windows PowerShell Web 存取](#BKMK_sign)

-   [登出及逾時](#BKMK_timeout)

-   [網頁型 Windows PowerShell 主控台的差異](#BKMK_web)

<a href="" id="BKMK_browser"></a>
------------------------------------------------------------------------

Windows PowerShell Web 存取支援下列網際網路瀏覽器。 雖然並未正式支援行動瀏覽器，但很多行動瀏覽器應該都可以執行網頁型 Windows PowerShell 主控台。 其他接受 Cookie、執行 JavaScript 以及執行 HTTPS 網站的瀏覽器預期也可以運作，但尚未經過正式測試。

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">支援的桌上型電腦瀏覽器</span></a>

------------------------------------------------------------------------

-   適用於 Microsoft Windows® 8.0、9.0、10.0 以及 11.0 的 Windows® Internet Explorer®

-   Mozilla Firefox® 10.0.2

-   適用於 Windows 的 Google Chrome™ 17.0.963.56m

-   適用於 Windows 的 Apple Safari® 5.1.2

-   適用於 Mac OS® 的 Apple Safari 5.1.2

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">通過基本測試的行動裝置或瀏覽器</span></a>

------------------------------------------------------------------------

-   Windows Phone 7 和 7.5

-   Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)

-   適用於 iPhone 作業系統 5.0.1 的 Apple Safari

-   適用於 iPad 2 作業系統 5.0.1 的 Apple Safari

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">瀏覽器需求</span></a>

------------------------------------------------------------------------

若要使用 Windows PowerShell Web 存取網頁型主控台，瀏覽器必須執行下列作業。

-   允許來自 Windows PowerShell Web 存取閘道網站的 Cookie。

-   可以開啟和讀取 HTTPS 頁面。

-   開啟和執行使用 JavaScript 的網站。

<a href="" id="BKMK_sign"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">登入 Windows PowerShell Web 存取</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

您的 Windows PowerShell Web 存取系統管理員應該提供您組織的 Windows PowerShell Web 存取閘道網站位址的 URL。 根據預設，這個網址是 https://&lt;server\_name&gt;/pswa。 在您登入 Windows PowerShell Web 存取之前，請確定您有想要管理之遠端電腦的名稱或 IP 位址。 您必須是遠端電腦上的已授權使用者，而且電腦必須設定為允許遠端管理。 如需如何設定電腦以允許遠端管理的詳細資訊，請參閱[在 Windows PowerShell 中啟用和使用遠端命令](https://technet.microsoft.com/magazine/ff700227.aspx)。 設定電腦以允許遠端管理最簡單的方法，就是在電腦上使用提升的使用者權限 ([以系統管理員身分執行]) 開啟的 Windows PowerShell 工作階段中執行 **Enable-PSRemoting -force** Cmdlet。).

### 登入 Windows PowerShell Web 存取

1.  在網際網路瀏覽器視窗或索引標籤中開啟 Windows PowerShell Web 存取網站。

2.  在 Windows PowerShell Web 存取登入頁面，提供您的網路使用者名稱、密碼以及您想要管理 (而且是已授權使用者) 的電腦名稱。 如果 Windows PowerShell Web 存取系統管理員指示您使用自訂網站或 Proxy 伺服器的 URI，而不是電腦名稱，請在 [連線類型] 欄位中選取 [連線 URI]，然後提供 URI。

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
    <td><ul>
    <li><p>如果目的地電腦在工作群組中，請使用下列語法提供您的使用者名稱並登入電腦：&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;.</p></li>
    <li><p>如果目的地電腦是閘道伺服器，您可以在 [電腦名稱]<strong></strong> 欄位中指定 <strong>localhost</strong>。</p></li>
    <li><p>如果目的地電腦是閘道伺服器，而且閘道伺服器位於工作群組中，您可以使用 [電腦名稱]<strong></strong> 欄位中的 <strong>localhost</strong>，但不要使用 [使用者名稱]<strong></strong> 欄位中的 localhost\&lt;<em>user_name</em>&gt;。 您必須使用 &lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;.</p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

3.  [選用連線設定] 區段與您想要管理的遠端電腦授權需求有關。 如需等同於選用連線設定之參數的詳細資訊，請參閱 [Enter-PSSession Cmdlet 說明](https://technet.microsoft.com/library/dd315384.aspx).

    一般而言，您用來通過 Windows PowerShell Web 存取閘道的認證與您想要管理之電腦所識別的認證相同。 不過，如果您想要使用不同的認證來管理您在步驟 2 指定的遠端電腦，請展開 [選用連線設定] 區段，然後提供替代的認證。 否則，請前往步驟 6。

4.  如果 Windows PowerShell Web 存取系統管理員已經針對 Windows PowerShell Web 存取使用者建立自訂工作階段設定，請在 [組態名稱] 欄位中輸入工作階段設定的名稱。 如需工作階段設定的詳細資訊，請參閱 Microsoft 網站上的 [about\_Session\_Configurations](https://technet.microsoft.com/library/dd819508.aspx)。

5.  請保留 [驗證類型] 設為 [預設]，除非 Windows PowerShell Web 存取系統管理員指示您不要保留。

6.  按一下 [登入].

<a href="" id="BKMK_timeout"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">登出及逾時</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

下列其中一項會將您登出網頁型 Windows PowerShell 工作階段。

-   按一下主控台右下角的 [登出]。 (僅限 Windows Server 2012)

-   按一下主控台右下角的 [儲存] 或 [結束] (僅限 Windows Server 2012 R2)。 按一下 [儲存] 儲存並關閉您的 Windows PowerShell Web 存取工作階段；您稍後可以重新連線至工作階段。 當您重新登入 Windows PowerShell Web 存取時，Windows PowerShell Web 存取會顯示一份已儲存工作階段的清單；您可以選取並重新連線至已儲存的工作階段，或者啟動新的工作階段。 允許使用者開啟的工作階段數目上限 (包括已儲存和使用中)，由閘道管理員所設定。

    按一下 [結束] 會將您登出 Windows PowerShell Web 存取工作階段而不加以儲存。

-   在相同的瀏覽器工作階段或相同瀏覽器工作階段的新索引標籤中，嘗試登入以管理不同的遠端電腦。 (這在閘道伺服器執行 Windows Server 2012 R2 時並不適用；Windows Server 2012 R2 上執行的 Windows PowerShell Web 存取不允許在相同的瀏覽器工作階段中有多個使用者工作階段。)如需如何在相同電腦上使用多個使用中工作階段的詳細資訊，請參閱本主題[網頁型主控台的限制](#BKMK_limits)一節中的＜同時連線多部目標電腦＞。

-   工作階段 20 分鐘沒有活動。 閘道系統管理員可以自訂沒有活動的逾時期間；如需詳細資訊，請參閱[工作階段管理](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt).

    -   如果您因為網路錯誤或其他非計劃中的關機或失敗 (而不是因為您自己關閉了工作階段) 從 Web 型主控台中斷工作階段的連線，Windows PowerShell Web 存取工作階段將繼續執行且連線到目標電腦，直到用戶端的逾時期間結束為止。 根據預設，此逾時期限是 20 分鐘，由閘道管理員所設定。 工作階段會在預設的 20 分鐘或閘道系統管理員所指定的逾時期間之後中斷連線，視何者較短而定。

        如果閘道伺服器執行 Windows Server 2012 R2，Windows PowerShell Web 存取可讓使用者在稍後重新連線到工作階段，但您將無法檢視或重新連線到已儲存的工作階段，直到閘道系統管理員所指定的逾時期間結束為止。

-   關閉瀏覽器視窗或索引標籤。

-   關閉正在執行瀏覽器的用戶端裝置，或者中斷網路連線。

-   在 Web 主控台執行 [結束] 命令。 如果您連線的工作階段設定支援 [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) 模式，或在受限制的 Runspace 中，則這個命令無效。

如果您想要重新登入，請再次開啟 Windows PowerShell Web 存取網頁，然後遵循本主題[登入 Windows PowerShell Web 存取](#BKMK_signin)的步驟來登入。

<a href="" id="BKMK_web"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">網頁型 Windows PowerShell 主控台的差異</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

登入 Windows PowerShell Web 存取後，會在您的瀏覽器視窗或索引標籤中開啟網頁型 Windows PowerShell 主控台。 因為這個主控台是連線到您在登入處理程序中指定的遠端電腦，所以只能在主控台使用可在遠端電腦上使用的 Windows PowerShell Cmdlet 或指令碼。 本節將說明 Windows PowerShell Web 存取主控台的其他限制，以及 Windows PowerShell Web 存取主控台和已安裝之 **PowerShell.exe** 主控台之間的差異。

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">與 PowerShell.exe 的功能差異</span></a>

------------------------------------------------------------------------

大部分的 Windows PowerShell 主機功能可在 Windows PowerShell Web 存取網頁型主控台中提供使用，但有一些功能未提供使用。

-   <span class="label">巢狀進度顯示。</span>  Windows PowerShell Web 存取為報告進度 Cmdlet 顯示進度 GUI，但只會顯示最上層的進度資訊。

-   <span class="label">輸入色彩修改。</span>  輸入色彩 (前景及背景) 無法變更。 輸出、警告、詳細資訊以及錯誤訊息的樣式，都可以藉由執行指令碼來變更。

-   <span class="label">PSHostRawUserInterface。</span>  Windows PowerShell Web 存取是透過 Windows PowerShell 遠端管理來實作，並使用遠端 runspace。 Windows PowerShell Web 存取不會實作這個介面中的某些方法；例如，寫入 Windows 主控台的任何命令。 類似 **PowerTab** 的命令不適用於 Windows PowerShell Web 存取。

-   <span class="label">功能鍵。</span>  Windows PowerShell Web 存取不支援某些功能鍵，因為在許多情況下命令是由瀏覽器保留。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>不支援的功能鍵</p></th>
<th><p>動作</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ctrl+C</p></td>
<td><p>在 Windows PowerShell Web 存取中，<strong>Ctrl+C</strong> 是由瀏覽器用來複製內容。 主控台提供 [取消]<strong></strong> 按鈕，使用者也可以使用 <strong>Ctrl+Q</strong> 來取消命令。</p></td>
</tr>
<tr class="even">
<td><p>Alt-space, e, l</p></td>
<td><p>捲動螢幕緩衝區</p></td>
</tr>
<tr class="odd">
<td><p>Alt+空格鍵, e, f</p></td>
<td><p>搜尋螢幕緩衝區中的文字</p></td>
</tr>
<tr class="even">
<td><p>Alt+空格鍵, e, k</p></td>
<td><p>選取要從螢幕緩衝區複製的文字</p></td>
</tr>
<tr class="odd">
<td><p>Alt+空格鍵, e, p</p></td>
<td><p>將剪貼簿內容貼到 Windows PowerShell 主控台</p></td>
</tr>
<tr class="even">
<td><p>Alt+空格鍵, c</p></td>
<td><p>關閉 Windows PowerShell 主控台</p></td>
</tr>
<tr class="odd">
<td><p>Ctrl+Break</p></td>
<td><p>強制關閉 Windows PowerShell 視窗</p></td>
</tr>
<tr class="even">
<td><p>Ctrl+Home</p></td>
<td><p>從目前命令列前面開始刪除</p></td>
</tr>
<tr class="odd">
<td><p>Ctrl+End</p></td>
<td><p>刪除到命令列的結尾</p></td>
</tr>
<tr class="even">
<td><p>F1</p></td>
<td><p>在命令列上將游標向右移動一個字元</p></td>
</tr>
<tr class="odd">
<td><p>F2</p></td>
<td><p>藉由複製上個命令所輸入的字元來建立新的命令</p></td>
</tr>
<tr class="even">
<td><p>F3</p></td>
<td><p>使用上個命令列的內容來完成命令列</p></td>
</tr>
<tr class="odd">
<td><p>F4</p></td>
<td><p>從游標位置刪除字元</p></td>
</tr>
<tr class="even">
<td><p>F5</p></td>
<td><p>向前查看您的命令歷程記錄。 若要存取 Windows PowerShell Web 存取命令歷程記錄中的命令，按一下網頁型主控台中的[記錄]<strong></strong> 捲動按鈕。</p></td>
</tr>
<tr class="odd">
<td><p>F7</p></td>
<td><p>以互動方式從命令歷程記錄選取命令</p></td>
</tr>
<tr class="even">
<td><p>F8</p></td>
<td><p>查看歷程記錄，顯示符合目前文字的命令</p></td>
</tr>
<tr class="odd">
<td><p>F9</p></td>
<td><p>執行歷程記錄中特定編號的命令</p></td>
</tr>
<tr class="even">
<td><p>Page Up</p></td>
<td><p>執行歷程記錄中的第一個命令</p></td>
</tr>
<tr class="odd">
<td><p>Page Down</p></td>
<td><p>執行歷程記錄中的最後一個命令</p></td>
</tr>
<tr class="even">
<td><p>Alt+F7</p></td>
<td><p>清除命令歷程記錄清單</p></td>
</tr>
</tbody>
</table>

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">網頁型主控台的限制</span></a>

------------------------------------------------------------------------

-   <span class="label">雙躍點。</span>   如果您嘗試使用 Windows PowerShell Web 存取建立新工作階段或在新工作階段工作，可能會遭遇雙躍點 (或從第一個連線再連線到第二部電腦) 限制。 Windows PowerShell Web 存取使用遠端 runspace，且目前 **PowerShell.exe** 不支援從遠端 runspace 建立另一台電腦的遠端連線。 如果您嘗試使用 **Enter-PSSession** Cmdlet 從現有的連線再連線到第二部遠端電腦，您可能會收到各種錯誤，例如「無法取得網路資源」。

    若要避免雙躍點錯誤，系統管理員應該在組織的網路環境中設定 CredSSP 驗證。 如需設定 CredSSP 驗證的詳細資訊，請參閱 Microsoft 網站上的 [適用於第二躍點遠端的 CredSSP](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx)。 當您想要管理第二部遠端電腦時也可以提供明確的認證；隱含的認證通常不允許第二躍點。

-   Windows PowerShell Web 存取會使用且具有與遠端 Windows PowerShell 工作階段相同的限制。 直接呼叫 Windows 主控台 API 的命令 (例如用於主控台型編輯器或文字型功能表程式的命令) 無法運作，因為這些命令無法讀寫標準輸入、輸出以及錯誤管道。 因此，會啟動可執行檔 (例如 **notepad.exe**) 或顯示 GUI (例如 <span class="code">OpenGridView</span> 或 <span class="code">ogv</span>) 的命令無法運作。 您的體驗會受到這個行為影響；對您而言，Windows PowerShell Web 存取似乎不會回應您的命令。

-   TAB 鍵自動完成無法在具有受限制 Runspace 或處於 **NoLanguage** 模式的工作階段運作。 雖然系統管理員可以設定工作階段來支援 TAB 鍵自動完成，但基於安全理由並不鼓勵這樣做，因為它會對未獲授權的使用者暴露下列資訊。

    -   內部檔案系統路徑

    -   內部電腦的共用資料夾

    -   Runspace 中的變數

    -   載入的類型或 .NET Framework 命名空間

    -   環境變數

-   登入 **NoLanguage** 工作階段設定或 Windows PowerShell Web Access 中限制的 runspace 的使用者無法執行 [結束] 命令來結束工作階段。 若要登出，使用者應該按一下主控台頁面上的 [登出]。

-   <span class="label">同時連線到多部目標電腦。</span>   如果閘道伺服器執行 Windows Server 2012，則 Windows PowerShell Web 存取只會允許每個瀏覽器工作階段連線到一部遠端電腦；它不允許使用者登入一次，然後使用個別的瀏覽器索引標籤連線到多部遠端電腦。 當您開啟新索引標籤或新瀏覽器視窗時，Windows PowerShell Web 存取會提示您中斷目前工作階段的連線，然後啟動新的工作階段，如此您就可以連線到新的 (或相同的) 遠端電腦。 不過，如果需要針對不同的遠端電腦使用兩個或多個獨立的工作階段，Internet Explorer 中的功能可以讓您建立新工作階段。 若要在 Internet Explorer 中啟動新的瀏覽器工作階段，請按下 **ALT**，開啟 [檔案] 功能表，然後選取 [新增工作階段]。 然後，在新的工作階段中，開啟 Windows PowerShell Web 存取網站，並登入以存取另一部遠端電腦。

    當 Windows PowerShell Web 存取閘道在 Windows Server 2012 R2 上執行時，使用者可以在不同的瀏覽器索引標籤中開啟多個遠端電腦連線。 如果您想要使用網頁型 Windows PowerShell 主控台開啟多個遠端電腦連線，請檢查您的 Windows PowerShell Web 存取閘道管理員，以查看閘道伺服器是否支援此功能。

-   <span class="label">持續性 Windows PowerShell 工作階段 (重新連線)。</span>   Windows PowerShell Web 存取閘道逾時之後，會關閉閘道和目標電腦之間的遠端連線。 這會停止目前正在處理的所有 Cmdlet 或指令碼。 當您執行長時間執行的工作時，建議您使用 Windows PowerShell **-Job** 基礎結構，您就可以啟動工作、中斷電腦連線、稍後重新連線，然後讓工作持續進行。 使用 **-Job** Cmdlet 的另一個優點是您可以透過使用 Windows PowerShell Web 存取啟動它們、登出，然後稍後再透過執行 Windows PowerShell Web 存取或另一部主機 (例如 Windows PowerShell® 整合式指令碼環境 (ISE)) 重新連線。

-   <span class="label">調整主控台大小。</span>   您可以使用下列三種方式調整 **PowerShell.exe** 主控台視窗大小。

    -   使用滑鼠拖曳並調整主控台視窗大小

    -   使用主控台內容 GUI 變更高度及寬度內容

    -   使用 Cmdlet 變更主控台視窗的高度及寬度

        Windows PowerShell Web 存取的主控台視窗可以使用 Cmdlet 來設定，如下所示。 在下列範例中，使用者將 Windows PowerShell Web 存取主控台的寬度變更為 **20**.

        [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_778d5e55-9195-4bd7-b313-d1fbca7876e4'); "複製到剪貼簿。")

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        您可以類似的方式變更主控台的高度。

        您可以在 [Windows PowerShell 小組部落格](http://blogs.msdn.com/b/powershell/)中找到自訂主控台檢視的其他範例。.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另請參閱</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Windows PowerShell Cmdlet 參考資料](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[Microsoft TechNet 上的 Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet 指令碼中心存放庫](http://gallery.technet.microsoft.com/scriptcenter)
[指令碼中心 - Hi，Scripting Guy！部落格](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell 小組部落格](http://blogs.msdn.com/b/powershell/)

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


