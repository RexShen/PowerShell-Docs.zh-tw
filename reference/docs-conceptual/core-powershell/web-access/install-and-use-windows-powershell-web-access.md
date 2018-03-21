---
ms.date: 2017-08-23
keywords: powershell,cmdlet
title: "安裝和使用 Windows PowerShell Web 存取"
ms.openlocfilehash: 2ad7a701dbb464088d6ed47d49a8dc3fb9b911f8
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="install-and-use-windows-powershell-web-access"></a>安裝和使用 Windows PowerShell Web 存取

更新日期︰2013 年 11 月 5 日 (編輯日期：2017 年 8 月 23 日)

適用目標︰Windows Server 2012 R2、Windows Server 2012

## <a name="introduction"></a>簡介

Windows PowerShell Web 存取於 Windows Server 2012 中首度引進，作為 Windows PowerShell 閘道，提供一個以遠端電腦為目標的網頁型 Windows PowerShell 主控台。 它可讓 IT 專業人員在網頁瀏覽器中，從 Windows PowerShell 主控台執行 Windows PowerShell 命令和指令碼，而不需要 Windows PowerShell、遠端管理軟體，或者在用戶端裝置上安裝瀏覽器外掛程式。 執行網頁型 Windows PowerShell 主控台只要有正確設定的 Windows PowerShell Web 存取閘道，以及支援 JavaScript 並接受 Cookie 的用戶端裝置瀏覽器即可。

用戶端裝置的範例包含膝上型電腦、非工作用個人電腦、租借電腦、平板電腦、網路工作站、執行非 Windows 作業系統的電腦以及行動電話瀏覽器。 IT 專業人員能夠從可以存取網際網路連線的裝置及網頁瀏覽器，執行遠端 Windows 伺服器的重要管理工作。

成功安裝和設定閘道之後，使用者就可以使用網頁瀏覽器來存取 Windows PowerShell 主控台。 當使用者開啟受保護的 Windows PowerShell Web 存取網站時，就可以在成功驗證之後執行網頁型 Windows PowerShell 主控台。

安裝和設定 Windows PowerShell Web 存取時需要執行三個步驟：

1. [安裝 Windows PowerShell Web 存取](#install-windows-powershell-web-access)
1. [設定閘道](#configure-the-gateway)
1. [設定限制性授權規則](#configure-a-restrictive-authorization-rule)

安裝和設定 Windows PowerShell Web 存取之前，建議您完整閱讀本指南，其中包含如何安裝、保護和解除安裝 Windows PowerShell Web 存取的相關指示。
[使用網頁型 Windows PowerShell 主控台](https://technet.microsoft.com/library/hh831417(v=ws.11).aspx)主題說明使用者如何登入網頁型主控台，並涵蓋了網頁型 Windows PowerShell 主控台和 **powershell.exe** 主控台之間的限制及差異。 網頁型主控台的終端使用者應該閱讀[使用網頁型 Windows PowerShell 主控台](use-the-web-based-windows-powershell-console.md)，但不需要閱讀本指南的其他章節。

本主題不提供深入的 IIS 網頁伺服器操作指導方針；只會說明設定 Windows PowerShell Web 存取閘道所需的步驟。 如需設定和保護 IIS 網站安全的詳細資訊，請參閱＜另請參閱＞一節中的 IIS 文件資源。

下圖顯示 Windows PowerShell Web 存取的運作方式。

![Windows PowerShell Web 存取圖](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>執行 Windows PowerShell Web 存取的需求

Windows PowerShell Web 存取需要網頁伺服器 (IIS)、.NET Framework 4.5，以及 Windows PowerShell 3.0 或 Windows PowerShell 4.0，才能在您要執行閘道的伺服器上執行。 您可以使用伺服器管理員中的 [新增角色及功能精靈] 或伺服器管理員的 Windows PowerShell 部署 Cmdlet，在執行 Windows Server 2012 R2 或 Windows Server 2012 的伺服器上安裝 Windows PowerShell Web 存取。 使用伺服器管理員或其部署 Cmdlet 安裝 Windows PowerShell Web 存取時，會在安裝處理程序期間自動新增必要的角色和功能。

Windows PowerShell Web 存取允許遠端使用者，在網頁瀏覽器中使用 Windows PowerShell 來存取組織中的電腦。 雖然 Windows PowerShell Web 存取是一個方便且功能強大的管理工具，但網頁型存取有安全性風險，應該儘可能安全地設定。 建議設定 Windows PowerShell Web 存取閘道的系統管理員使用可用的安全性階層，包含 Windows PowerShell Web 存取隨附之以 Cmdlet為基礎的授權規則，以及網頁伺服器 (IIS) 與協力廠商應用程式中可用的安全性階層。 這份文件含有只建議用於測試環境的不安全範例，以及建議用於安全部署的範例。

## <a name="browser-and-client-device-support"></a>瀏覽器及用戶端裝置支援

Windows PowerShell Web 存取支援下列網際網路瀏覽器。
雖然並未正式支援行動瀏覽器，但很多行動瀏覽器應該都可以執行網頁型 Windows PowerShell 主控台。 其他接受 Cookie、執行 JavaScript 以及執行 HTTPS 網站的瀏覽器預期也可以運作，但尚未經過正式測試。

### <a name="supported-desktop-computer-browsers"></a>支援的桌上型電腦瀏覽器

- 適用於 Microsoft Windows 8.0、9.0、10.0 和 11.0 的 Windows Internet Explorer
- Mozilla Firefox 10.0.2
- 適用於 Windows 的 Google Chrome 17.0.963.56m
- 適用於 Windows 的 Apple Safari 5.1.2
- 適用於 Mac OS 的 Apple Safari 5.1.2

### <a name="minimally-tested-mobile-devices-or-browsers"></a>通過基本測試的行動裝置或瀏覽器

- Windows Phone 7 和 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)
- 適用於 iPhone 作業系統 5.0.1 的 Apple Safari
- 適用於 iPad 2 作業系統 5.0.1 的 Apple Safari

### <a name="browser-requirements"></a>瀏覽器需求

若要使用 Windows PowerShell Web 存取網頁型主控台，瀏覽器必須執行下列作業。

- 允許來自 Windows PowerShell Web 存取閘道網站的 Cookie。
- 可以開啟和讀取 HTTPS 頁面。
- 開啟和執行使用 JavaScript 的網站。

## <a name="recommended-quick-deployment"></a>建議的快速部署

您可以使用 Windows PowerShell 部署 Cmdlet 或從伺服器管理員中開啟的 [新增角色及功能精靈]，在執行 Windows Server 2012 R2 或 Windows Server 2012 的伺服器上安裝 Windows PowerShell Web 存取閘道。 若要快速安裝和設定，請使用 Windows PowerShell Cmdlet，如本節所述。

1. [安裝 Windows PowerShell Web 存取](#install-Windows-powershell-web-access)
1. [設定閘道](#configure-the-gateway)
1. [設定限制性授權規則](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access"></a>安裝 Windows PowerShell Web 存取

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>使用 Windows PowerShell Cmdlet 安裝 Windows PowerShell Web 存取

1. 執行下列其中一個動作，使用提高的使用者權限開啟 Windows PowerShell 工作階段。
    - 在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。
    - 在 Windows **[開始]** 畫面上，以滑鼠右鍵按一下 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。

    >**![注意](images/note.jpeg) 注意**：在 Windows PowerShell 3.0 和 4.0 中，執行屬於模組的 Cmdlet 之前，不需要將伺服器管理員 Cmdlet 模組匯入 Windows PowerShell 工作階段。 當您首次執行屬於模組的 Cmdlet 時，會自動匯入模組。 此外，Windows PowerShell Cmdlet 不會區分大小寫。

1. 輸入下列內容，然後按 **Enter**，其中 *computer_name* 代表要安裝 Windows PowerShell Web 存取的遠端電腦 (如果適用)。 如有需要，`-Restart` 參數會自動重新啟動目的地伺服器。

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   >**![注意](images/note.jpeg) 注意**
   >
   >使用 Windows PowerShell Cmdlet 安裝 Windows PowerShell Web 存取，預設不會新增網頁伺服器 (IIS) 管理工具。 如果您想要在與 Windows PowerShell Web 存取閘道相同的伺服器上安裝管理工具，可將 `-IncludeManagementTools` 參數新增至安裝命令 (如本步驟所提供)。 如果您從遠端電腦管理 Windows PowerShell Web 存取網站，在您要用來管理閘道的電腦上，透過安裝 [Windows 8.1 的遠端伺服器管理工具](http://go.microsoft.com/fwlink/?LinkID=304145)或 [Windows 8 的遠端伺服器管理工具](http://go.microsoft.com/fwlink/p/?LinkID=238560)來安裝 [IIS 管理員] 嵌入式管理單元。
   
   若要在離線 VHD 安裝角色及功能，您必須新增 `-ComputerName` 參數及 `-VHD` 參數。 `-ComputerName` 參數包含要掛接 VHD 的伺服器名稱，`-VHD` 參數則包含指定伺服器上的 VHD 檔案路徑。

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. 完成安裝後，在使用提高的使用者權限開啟的 Windows PowerShell 主控台中，藉由在目的地伺服器上執行 **Get-WindowsFeature** Cmdlet，來確認 Windows PowerShell Web 存取已安裝於目的地伺服器上。 您也可以在 [所有伺服器] 頁面上選取目的地伺服器，然後檢視所選伺服器的 [角色和功能] 磚，藉以確認 Windows PowerShell Web 存取已安裝於伺服器管理員主控台中。 您也可以檢視 Windows PowerShell Web 存取的讀我檔案。

1. 安裝 Windows PowerShell Web 存取之後，系統會提示您檢閱讀我檔案，其中包含適用於閘道的必要且基本的安裝指示。 下一節[設定閘道](#configure-the-gateway)中也會有這些安裝指示。 讀我檔案的路徑是 **C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt**。

### <a name="configure-the-gateway"></a>設定閘道

**Install-PswaWebApplication** Cmdlet 是快速設定 Windows PowerShell Web 存取的方法。 雖然您可以新增 `UseTestCertificate` 參數到 `Install-PswaWebApplication` Cmdlet 來安裝自我簽署的 SSL 憑證進行測試，但這並不安全；若要安全的生產環境，一定要使用由憑證授權單位 (CA) 簽署的有效 SSL 憑證。
系統管理員可以使用 IIS 管理員主控台以選擇的簽署憑證來取代測試憑證。

您可以執行 `Install-PswaWebApplication` Cmdlet 或在 IIS 管理員中執行 GUI 設定步驟，來完成 Windows PowerShell Web 存取 Web 應用程式設定。 根據預設，Cmdlet 會在 [IIS 管理員] 上顯示的 [預設的網站] 容器中，安裝 Web 應用程式 **pswa** (以及應用程式集區 **pswa_pool**)；如有需要，可以指示 Cmdlet 變更 Web 應用程式的預設網站容器。 IIS 管理員提供 Web 應用程式可用的設定選項，例如變更連接埠號碼或安全通訊端層 (SSL) 憑證。

>**![安全性提示](images/securitynote.jpeg) 安全性提示**
> 
>強烈建議系統管理員將閘道設定為使用 CA 簽署的有效憑證。 

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>使用 Install-PswaWebApplication 以測試憑證設定 Windows PowerShell Web 存取閘道

1. 執行下列其中一個動作來開啟 Windows PowerShell 工作階段。

    - 在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 [Windows PowerShell]。

    - 在 Windows **[開始]** 畫面上，按一下 **[Windows PowerShell]**。

2. 輸入下列程式碼，然後按 **Enter**。

    **Install-PswaWebApplication -UseTestCertificate**

  >**![安全性提示](images/securitynote.jpeg) 安全性提示**
  >
  >
            `UseTestCertificate` 參數只能用在私人測試環境中。 若要安全的生產環境，建議使用 CA 簽署的有效憑證。

執行這個 Cmdlet 會在 IIS [預設的網站] 容器中安裝 Windows PowerShell Web 存取 Web 應用程式。 這個 Cmdlet 會建立在預設網站 `https://<server_name>/pswa` 上執行 Windows PowerShell Web 存取所需的基礎結構。 若要在不同網站安裝 Web 應用程式，請新增 `WebSiteName` 參數以提供網站名稱。 若要變更 Web 應用程式的名稱 (預設是 `pswa`)，請新增 `WebApplicationName` 參數。

執行 Cmdlet 可以設定下列設定。 如有需要，可以在 IIS 管理員主控台手動變更這些設定。

- Path：/pswa
- ApplicationPool：pswa_pool
- EnabledProtocols：http
- PhysicalPath：%*windir*%/Web/PowerShellWebAccess/wwwroot

**範例**：`Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

在這個範例中，針對 Windows PowerShell Web 存取產生的網站是 https://\<伺服器名稱\>/myWebApp。

>**![注意](images/note.jpeg) 注意** 
> 
>必須透過新增授權規則，讓使用者獲得網站存取權，才能進行登入。 如需詳細資訊，請參閱[設定限制性授權規則](#configure-a-restrictive-authorization-rule)和 [Windows PowerShell Web 存取的授權規則與安全性功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>使用 Install-PswaWebApplication 和 IIS 管理員以正版憑證設定 Windows PowerShell Web 存取閘道

1. 執行下列其中一個動作來開啟 Windows PowerShell 工作階段。

    - 在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 [Windows PowerShell]。

    - 在 Windows **[開始]** 畫面上，按一下 **[Windows PowerShell]**。

2. 輸入下列程式碼，然後按 **Enter**。

    **Install-PswaWebApplication**

    執行 Cmdlet 可以設定下列閘道設定。
    如有需要，可以在 IIS 管理員主控台手動變更這些設定。
    您也可以指定 `WebsiteName` Cmdlet 的 `WebApplicationName` 及 `Install-PswaWebApplication` 參數值。

    - Path：/pswa

    - ApplicationPool：pswa_pool

    - EnabledProtocols：http

    - PhysicalPath：%*windir*%/Web/PowerShellWebAccess/wwwroot

3. 執行下列其中一項動作以開啟 IIS 管理員主控台。

    - 在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。 在 [伺服器管理員] 的 **[工具]** 功能表上，按一下 **[Internet Information Services (IIS) 管理員]**。

    - 在 Windows **[開始]** 畫面上，按一下 **[伺服器管理員]**。

4. 在 [IIS 管理員] 樹狀目錄窗格中，展開安裝 Windows PowerShell Web 存取的伺服器節點，直到可以看到 [站台] 資料夾為止。 展開 [站台] 資料夾。

5. 選取您已安裝 Windows PowerShell Web 存取 Web 應用程式的網站。 在 **[動作]** 窗格中，按一下 **[繫結]**。

6. 在 **[站台繫結]** 對話方塊中，按一下 **[新增]**。

7. 在 **[新增站台繫結]** 對話方塊的 **[類型]** 欄位中選取 **[https]**。

8. 在 [SSL 憑證] 欄位中，從下拉式功能表中選取您已簽署的憑證。 按一下 **[確定]**。 如需如何取得憑證的詳細資訊，請參閱本主題中的[在 IIS 管理員設定 SSL 憑證](#to-configure-an-ssl-certificate-in-iis-Manager)。

    現在 Windows PowerShell Web 存取 Web 應用程式已設定為使用您已簽署的 SSL 憑證。

    您可以在瀏覽器視窗中開啟 **https://\<伺服器名稱\>/pswa**，來存取 Windows PowerShell Web 存取。

>**![注意](images/note.jpeg) 注意** 
> 
>必須透過新增授權規則，讓使用者獲得網站存取權，才能進行登入。 
>如需詳細資訊，請參閱本主題中的[設定限制性授權規則](#configure-a-restrictive-authorization-rule)，以及 [Windows PowerShell Web 存取的授權規則與安全性功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

### <a name="configure-a-restrictive-authorization-rule"></a>設定限制性授權規則

安裝 Windows PowerShell Web 存取並設定閘道之後，使用者就可以在瀏覽器中開啟登入頁面，但是必須等到 Windows PowerShell Web 存取系統管理員明確授與使用者存取權之後，才能登入。 您可以使用下表所述的 Windows PowerShell Cmdlet，來管理 Windows PowerShell Web 存取存取控制。 沒有適用於新增或管理授權規則的 GUI。 如需 Windows PowerShell Web 存取 Cmdlet 的詳細資訊，請參閱 Cmdlet 參考主題：[Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md) (Windows PowerShell Web 存取 Cmdlet)。

如需 Windows PowerShell Web 存取授權規則和安全性的詳細資訊，請參閱 [Windows PowerShell Web 存取的授權規則與安全性功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

#### <a name="to-add-a-restrictive-authorization-rule"></a>新增限制性授權規則

1. 執行下列其中一個動作，使用提高的使用者權限開啟 Windows PowerShell 工作階段。

    - 在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。

    - 在 Windows **[開始]** 畫面上，以滑鼠右鍵按一下 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。

2. 使用工作階段設定來限制使用者存取的選擇性步驟：確認您要在規則中使用的工作階段設定已經存在。 如果尚未建立這些設定，請使用 [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations) 中建立工作階段設定的指示。

3. 輸入下列程式碼，然後按 **Enter**。

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   這個授權規則允許特定使用者存取網路上他們通常有權存取的一部電腦，以及該使用者在一般編寫指令碼及 Cmdlet 範圍內的特定工作階段設定存取權。
   
   在下列範例中，`JSmith` 網域中的使用者 `Contoso` 被授與管理電腦 `Contoso_214` 的存取權，並使用名為 `NewAdminsOnly` 的工作階段設定。

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. 執行 `Get-PswaAuthorizationRule` Cmdlet 或 `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>` 確認已建立規則

5. 例如，`Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`。

設定授權規則之後，授權使用者就可以開始登入網頁型主控台，並開始使用 Windows PowerShell Web 存取。

## <a name="custom-deployment"></a>自訂部署

您可以使用伺服器管理員中的 [新增角色及功能精靈]，在執行 Windows Server 2012 R2 或 Windows Server 2012 的伺服器上安裝 Windows PowerShell Web 存取閘道。 安裝 Windows PowerShell Web 存取之後，您可以在 IIS 管理員中自訂閘道的設定。

### <a name="install-windows-powershell-web-access"></a>安裝 Windows PowerShell Web 存取

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a>使用新增角色及功能精靈安裝 Windows PowerShell Web 存取

1. 如果已經開啟伺服器管理員，請移至下一個步驟。 如果尚未開啟伺服器管理員，請執行下列其中一項動作來將它開啟。

    - 在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。

    - 在 Windows **[開始]** 畫面上，按一下 **[伺服器管理員]**。

2. 在 **[管理]** 功能表上，按一下 **[新增角色及功能]**。

3. 在 [選取安裝類型] 頁面上，選取 [角色型或功能型安裝]。 按 **[下一步]**。

4. 在 [選取目的地伺服器] 頁面上，從伺服器集區選取伺服器，或選取離線 VHD。 若要選取離線 VHD 做為目的地伺服器，請先選取要掛接 VHD 的伺服器，然後選取 VHD 檔案。 如需如何將伺服器新增到伺服器集區的相關資訊，請參閱伺服器管理員說明。 選取目的地伺服器之後，按一下 **[下一步]**。

5. 在精靈的 **[選取功能]** 頁面上，展開 **[Windows PowerShell]**，然後選取 **[Windows PowerShell Web 存取]**。

6. 請注意，系統會提示您新增必要的功能，例如 .NET Framework 4.5 以及網頁伺服器 (IIS) 的角色服務。 新增必要的功能，然後繼續。

    >**![注意](images/note.jpeg) 注意** 
    >
    >使用 [新增角色及功能精靈] 安裝 Windows PowerShell Web 存取，也會安裝網頁伺服器 (IIS)，包括 [IIS 管理員] 嵌入式管理單元。 如果您使用 [新增角色及功能精靈]，預設會安裝嵌入式管理單元及其他 IIS 管理工具。 如果您依下列程序中所述方式使用 Windows PowerShell Cmdlet 安裝 Windows PowerShell Web 存取，預設不會新增管理工具。

7. 如果 Windows PowerShell Web 存取的功能檔案未儲存於您在步驟 4 選取的目的地伺服器上，可在 [確認安裝選項] 頁面上按一下 [指定替代來源路徑]，然後提供功能檔案的路徑。 否則，按一下 **[安裝]**。

8. 按一下 [安裝] 之後，[安裝進度] 頁面就會顯示安裝進度、結果及訊息，例如警告、失敗或 Windows PowerShell Web 存取所需的後續安裝設定步驟。 安裝 Windows PowerShell Web 存取之後，系統會提示您檢閱讀我檔案，其中包含適用於閘道的必要且基本的安裝指示。 本主題中也包含這些指示。 讀我檔案的路徑是 `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`。

### <a name="configure-the-gateway"></a>設定閘道

本節的指示適用於在網站的子目錄 (不是根目錄) 中安裝 Windows PowerShell Web 存取 Web 應用程式。 這個程序是等同於 `Install-PswaWebApplication` Cmdlet 所執行之動作的 GUI 動作。 本節還包含如何使用 IIS 管理員，將 Windows PowerShell Web 存取閘道設定為根網站的指示。

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>使用 IIS 管理員在現有的網站中設定閘道

1. 執行下列其中一項動作以開啟 IIS 管理員主控台。

    - 在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。 在 [伺服器管理員] 的 **[工具]** 功能表上，按一下 **[Internet Information Services (IIS) 管理員]**。

    - 在 Windows [開始] 畫面中，輸入 **Internet Information Services (IIS) 管理員**名稱的任何部分。 當捷徑出現在 [應用程式] 結果時，按一下該捷徑。

2. 為 Windows PowerShell Web 存取建立新的應用程式集區。 在 [IIS 管理員] 樹狀目錄窗格中展開閘道伺服器的節點，選取 [應用程式集區]，然後在 [動作] 窗格中按一下 [新增應用程式集區]。

3. 新增名為 **pswa_pool** (或提供另一個名稱) 的新應用程式集區。 按一下 **[確定]**。

4. 在 [IIS 管理員] 樹狀目錄窗格中，展開安裝 Windows PowerShell Web 存取的伺服器節點，直到可以看到 [站台] 資料夾為止。 選取 [站台] 資料夾。

5. 以滑鼠右鍵按一下您想要新增 Windows PowerShell Web 存取網站的網站 (例如 **[預設的網站]**)，然後按一下 **[新增應用程式]**。

6. 在 [別名] 欄位中輸入 pswa，或者提供另一個別名。 別名會成為虛擬目錄名稱。 例如，下列 URL 中的 **pswa** 代表在這個步驟中指定的別名：**https://\<伺服器名稱\>/pswa**。

7. 在 [應用程式集區] 欄位中，選取您在步驟 3 建立的應用程式集區。

8. 在 [實體路徑] 欄位中，瀏覽應用程式的位置。 您可以使用預設位置 %windir%/Web/PowerShellWebAccess/wwwroot。 按一下 **[確定]**。

9. 依照本主題的＜在 IIS 管理員中設定 SSL 憑證＞(#to-configure-an-ssl-certificate-in-iis-Manager) 程序中的步驟進行。

10. ![](images/SecurityNote.jpeg) 選擇性的安全性步驟：

    在樹狀目錄窗格中選取網站後，按兩下 [內容] 窗格中的 [SSL 設定]。 選取 [需要 SSL]，然後在 [動作] 窗格中，按一下 [套用]。 您也可以選擇性地在 [SSL 設定] 窗格中，要求連線到 Windows PowerShell Web 存取網站的使用者必須擁有用戶端憑證。 用戶端憑證可協助確認用戶端裝置使用者的身份。 如需要求用戶端憑證如何增加 Windows PowerShell Web 存取安全性的詳細資訊，請參閱本指南中的 [Windows PowerShell Web 存取的授權規則與安全性功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

11. 開啟用戶端裝置的瀏覽器工作階段。 如需支援的瀏覽器及裝置的詳細資訊，請參閱本主題的[瀏覽器及用戶端裝置支援](#browser-and-client-device-support)。

12. 開啟新的 Windows PowerShell Web 存取網站 **https://\<*gateway-server-name*\>/pswa**。

    瀏覽器應該會顯示 Windows PowerShell Web 存取主控台登入頁面。

    >**![注意](images/note.jpeg) 注意** 
    > 
    >必須透過新增授權規則，讓使用者獲得網站存取權，才能進行登入。 
    >如需詳細資訊，請參閱本主題中的[設定限制性授權規則](#configure-a-restrictive-authorization-rule)，以及 [Windows PowerShell Web 存取的授權規則與安全性功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

13. 在使用提高的使用者權限 (以系統管理員身分執行) 開啟的 Windows PowerShell 工作階段中，執行下列指令碼，其中 *application_pool_name* 代表您在步驟 3 建立的應用程式集區名稱，以便授與該應用程式集區授權檔案的存取權。

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    若要檢視授權檔案的現有存取權，請執行下列命令：

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>使用 IIS 管理員以測試憑證將閘道設定為根網站

1. 執行下列其中一項動作以開啟 IIS 管理員主控台。

    - 在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。 在 [伺服器管理員] 的 **[工具]** 功能表上，按一下 **[Internet Information Services (IIS) 管理員]**。

    - 在 Windows [開始] 畫面中，輸入 **Internet Information Services (IIS) 管理員**名稱的任何部分。 當捷徑出現在 [應用程式] 結果時，按一下該捷徑。

2. 在 [IIS 管理員] 樹狀目錄窗格中，展開安裝 Windows PowerShell Web 存取的伺服器節點，直到可以看到 [站台] 資料夾為止。 選取 [站台] 資料夾。

3. 在 **[動作]** 窗格中，按一下 **[Add Website] \(新增網站)**。

4. 輸入網站的名稱，例如 **Windows PowerShell Web Access**。

5. 此時會自動為新網站建立應用程式集區。 若要使用不同的應用程式集區，按一下 [選取]，以選取要與新網站相關聯的應用程式集區。 在 **[選取應用程式集區]** 對話方塊中選取替代的應用程式集區，然後按一下 **[確定]**。

6. 在 [實體路徑] 文字方塊中，瀏覽到 %*windir*%/Web/PowerShellWebAccess/wwwroot。

7. 在 **[繫結]** 區域的 **[類型]** 欄位中，選取 **[https]**。

8. 為其他站台或應用程式尚未使用的網站指派連接埠號碼。 若要尋找開放的連接埠，可以在命令提示字元視窗中執行 **netstat** 命令。 預設連接埠號碼為 443。

    如果另一個網站已經使用 443，或者有其他需要變更連接埠號碼的安全性原因，請變更預設連接埠。 如果在閘道伺服器上執行的另一個網站正在使用您選取的連接埠，當您在 [新增網站] 對話方塊中按一下 [確定] 時，就會顯示警告。 您必須使用未使用的連接埠來執行 Windows PowerShell Web 存取。

9. 或者，如果組織有需要，可以指定對組織及使用者有意義的主機名稱，例如 **www.contoso.com**。按一下 **[確定]**。

10. 如需更安全的生產環境，強烈建議您提供 CA 簽署的有效憑證。 您必須提供 SSL 憑證，因為使用者只能透過 HTTPS 網站連線到 Windows PowerShell Web 存取。 如需如何取得憑證的詳細資訊，請參閱本主題中的[在 IIS 管理員中設定 SSL 憑證](#to-configure-an-ssl-certificate-in-iis-Manager)。

11. 按一下 [確定]，以關閉 [新增網站] 對話方塊。

12. 在使用提高的使用者權限 (以系統管理員身分執行) 開啟的 Windows PowerShell 工作階段中，執行下列指令碼，其中 *application_pool_name* 代表您在步驟 4 建立的應用程式集區名稱，以便授與該應用程式集區授權檔案的存取權。

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    若要檢視授權檔案的現有存取權，請執行下列命令：

        c:\windows\system32\icacls.exe $authorizationFile

13. 在 [IIS 管理員] 樹狀目錄窗格中選取新網站後，在 [動作]  窗格中按一下 [啟動]  以啟動網站。

14. 開啟用戶端裝置的瀏覽器工作階段。 如需支援的瀏覽器及裝置的詳細資訊，請參閱本文件的[瀏覽器及用戶端裝置支援](#browser-and-client-device-support)。

15. 開啟新的 Windows PowerShell Web 存取網站。

    由於根網站會指向 Windows PowerShell Web 存取資料夾，因此，當您開啟 **https://\<*gateway_server_name*\>** 時，瀏覽器應該會顯示 Windows PowerShell Web 存取登入頁面。 您應該不需要在 URL 中新增 **/pswa**。

    >**![注意](images/note.jpeg) 注意** 
    > 
    >必須透過新增授權規則，讓使用者獲得網站存取權，才能進行登入。 
    >如需詳細資訊，請參閱本主題中的[設定限制性授權規則](#configure-a-restrictive-authorization-rule)，以及 [Windows PowerShell Web 存取的授權規則與安全性功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

### <a name="configure-a-restrictive-authorization-rule"></a>設定限制性授權規則

安裝 Windows PowerShell Web 存取並設定閘道之後，使用者就可以在瀏覽器中開啟登入頁面，但是必須等到 Windows PowerShell Web 存取系統管理員明確授與使用者存取權之後，才能登入。 您可以使用下表所述的 Windows PowerShell Cmdlet，來管理 Windows PowerShell Web 存取存取控制。 沒有適用於新增或管理授權規則的 GUI。 如需 Windows PowerShell Web 存取 Cmdlet 的詳細資訊，請參閱 Cmdlet 參考主題：[Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md) (Windows PowerShell Web 存取 Cmdlet)。

如需 Windows PowerShell Web 存取授權規則和安全性的詳細資訊，請參閱 [Windows PowerShell Web 存取的授權規則與安全性功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

#### <a name="to-add-a-restrictive-authorization-rule"></a>新增限制性授權規則

1. 執行下列其中一個動作，使用提高的使用者權限開啟 Windows PowerShell 工作階段。

    - 在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。

    - 在 Windows **[開始]** 畫面上，以滑鼠右鍵按一下 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。

2. ![安全性注意事項](images/SecurityNote.jpeg) 使用工作階段設定限制使用者存取的選擇性步驟：

    確定您要在規則中使用的工作階段設定已經存在。 如果尚未建立這些設定，請使用 [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations) 中建立工作階段設定的指示。

3. 輸入下列程式碼，然後按 **Enter**。

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    這個授權規則允許特定使用者存取網路 (他們通常擁有其存取權) 上的一部電腦，並能夠存取範圍是使用者一般指令碼編寫及 cmdlet 需求的特定工作階段設定。 
    
    在下列範例中，`JSmith` 網域中的使用者 `Contoso` 被授與管理電腦 `Contoso_214` 的存取權，並使用名為 `NewAdminsOnly` 的工作階段設定。

        Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4. 執行 `Get-PswaAuthorizationRule` Cmdlet 或 `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>` 確認已建立規則。 

    例如，`Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`。

設定授權規則之後，授權使用者就可以開始登入網頁型主控台，並開始使用 Windows PowerShell Web 存取。

## <a name="configure-a-genuine-certificate"></a>設定正版憑證

若要安全的生產環境，請一律使用由憑證授權單位 (CA) 簽署的有效 SSL 憑證。 本節中的程序說明如何從 CA 取得有效的 SSL 憑證並加以套用。

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>在 IIS 管理員中設定 SSL 憑證

1. 在 [IIS 管理員] 樹狀目錄窗格中，選取安裝 Windows PowerShell Web 存取的伺服器。

2. 在內容窗格中，按兩下 **[伺服器憑證]**。

3. 在 [動作] 窗格中，執行下列其中一項。 如需在 IIS 中設定伺服器憑證的詳細資訊，請參閱[在 IIS 7 中設定伺服器憑證](https://technet.microsoft.com/library/cc732230.aspx)。

    - 按一下 [匯入]，從網路上的位置匯入現有的有效憑證。

    - 按一下 [建立憑證要求]，向 CA (例如 [VeriSign](http://www.verisign.com/)、[Thawte](https://www.thawte.com/) 或 [GeoTrust](https://www.geotrust.com/)) 要求憑證。 憑證的一般名稱必須符合要求中的主機標頭。

      例如，如果用戶端瀏覽器要求 http://www.contoso.com/，則一般名稱也必須為 http://www.contoso.com/。 這是提供憑證給 Windows PowerShell Web 存取閘道最安全且最建議的選項。

    - 按一下 [建立自我簽署憑證]，建立您可以立即使用的憑證，稍後視需要交由 CA 簽署。 為自我簽署的憑證指定易記名稱，例如 **Windows PowerShell Web 存取**。 這個選項並不安全，建議只用於私人測試環境。

4. 建立或取得憑證之後，在 [IIS 管理員] 樹狀目錄窗格中選取要套用此憑證的網站 (例如 [預設的網站])，然後在 [動作] 窗格中按一下 [繫結]。

5. 如果尚未顯示繫結，請在 [新增站台繫結] 對話方塊中，新增站台的 [https] 繫結。 如果您不是使用自我簽署的憑證，請指定這個程序步驟 3 所指定的主機名稱。 如果您使用的是自我簽署的憑證，就不需要這個步驟。

6. 選取您在這個程序的步驟 3 取得或建立的憑證，然後按一下 **[確定]**。

## <a name="using-the-web-based-windows-powershell-console"></a>使用網頁型 Windows PowerShell 主控台

依本主題所述方式安裝 Windows PowerShell Web 存取並完成閘道設定之後，就可以使用 Windows PowerShell 網頁型主控台。 如需開始使用網頁型主控台的詳細資訊，請參閱[使用網頁型 Windows PowerShell 主控台](use-the-web-based-windows-powershell-console.md)。

## <a name="see-also"></a>另請參閱

- [Internet Information Services (IIS) 7.0 文件](https://technet.microsoft.com/library/cc753433.aspx)
- [IIS 管理員 7.0 說明](https://technet.microsoft.com/library/cc732664.aspx)
- [設定網頁伺服器安全性 (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
- [IPsec 部署資源](https://technet.microsoft.com/network/bb531150)
