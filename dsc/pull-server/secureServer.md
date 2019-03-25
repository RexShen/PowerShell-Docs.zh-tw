---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 提取伺服器最佳做法
ms.openlocfilehash: fe483a487f85f2e4edb0928fccfe98746ae11231
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "58057700"
---
# <a name="pull-server-best-practices"></a>提取伺服器最佳做法

適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

> [!IMPORTANT]
> 提取伺服器 (Windows 功能「DSC 服務」) 是支援的 Windows Server 元件，但未計劃提供新特性或功能。 建議開始將受控用戶端轉換為 [Azure 自動化 DSC](/azure/automation/automation-dsc-getting-started) (包括 Windows Server 上提取伺服器以外的功能)，或[此處](pullserver.md#community-solutions-for-pull-service)列出的其中一個社群解決方案。

摘要：本文件旨在包含程序和擴充性來協助準備解決方案的工程師。 詳細資訊應該提供客戶找到的最佳做法，經產品小組驗證後確認所提供的建議可穩定應對未來問題。

| |文件資訊|
|:---|:---|
作者 | Michael Greene
審閱者 | Ben Gelens、Ravikanth Chaganti、Aleksandar Nikolic
已發行 | 2015 年 4 月

## <a name="abstract"></a>摘要

本文件旨在為規劃 Windows PowerShell 期望狀態設定提取伺服器實作的任何人提供官方指引。 提取伺服器是一項簡單的服務，部署只需要幾分鐘。 雖然這份文件會提供可用於部署的技術指引，但本文件的價值如同最佳做法和部署前考慮事項的參考。
讀者對 DSC 以及描述 DSC 部署內含元件的詞彙應有基本的了解。 如需詳細資訊，請參閱 [Windows PowerShell 預期狀態設定概觀](/powershell/dsc/overview)主題。
因為 DSC 預期依雲端節奏發展，所以包含提取伺服器的基礎技術也預期會發展並推出新功能。 本文件附錄中的版本表提供有關舊版的參考，以及鼓勵展望未來設計的解決方案參考。

本文件分為兩大部分︰

- 設定規劃
- 安裝指南

### <a name="versions-of-the-windows-management-framework"></a>Windows Management Framework 版本

本文件中的資訊適用於 Windows Management Framework 5.0。 雖然部署及操作提取伺服器不需要 WMF 5.0，但 5.0 版是本文的焦點。

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell Desired State Configuration (Windows PowerShell 期望狀態設定)

預期狀態設定 (DSC) 是一個管理平台，使用名為管理物件格式 (MOF) 的業界語法描述通用訊息模型 (CIM)，來部署和管理設定資料。 開放式管理基礎結構 (OMI) 這個開放原始碼專案，可跨 Linux 等平台與網路硬體作業系統進一步開發這些標準。 如需詳細資訊，請參閱[連結至 MOF 規格的 DMTF 頁面](https://www.dmtf.org/standards/cim)以及 [OMI 文件和來源](https://collaboration.opengroup.org/omi/documents.php)。

Windows PowerShell 提供一組預期狀態設定的語言延伸模組，您可用來建立與管理宣告式設定。

### <a name="pull-server-role"></a>提取伺服器角色

提取伺服器提供集中式服務以儲存將來可存取的目標節點設定。

提取伺服器角色可以部署為 Web 伺服器執行個體或 SMB 檔案共用。 Web 伺服器功能包括 OData 介面，並可選擇是否包含目標節點功能，回報套用設定後確認成功或失敗。 這項功能在有大量目標節點的環境中很有用。
將目標節點 (也稱為用戶端) 設定指向提取伺服器後，就會下載並套用最新的設定資料和任何必要的指令碼。 單次部署或重複的作業都會出現這種情況，這也會讓提取伺服器成為管理大規模變更的重要資產。 如需詳細資訊，請參閱 [Windows PowerShell Desired State Configuration 提取伺服器](/powershell/dsc/pullServer)及

[推送和提取設定模式](/powershell/dsc/pullServer)。

## <a name="configuration-planning"></a>設定規劃

任何企業軟體部署都有可預先收集的資訊，以利規劃正確的架構，並準備好完成部署所需的步驟。 下列各節提供有關如何準備以及可能需要事先進行的組織性連線資訊。

### <a name="software-requirements"></a>軟體需求

提取伺服器部署需要 Windows Server 的 DSC 服務功能。 這項功能在 Windows Server 2012 中推出，且已透過 Windows Management Framework (WMF) 陸續發行的版本進行更新。

### <a name="software-downloads"></a>軟體下載

除了從 Windows Update 安裝最新的內容，部署 DSC 提取伺服器的最佳做法中也包含了兩個下載項目：最新版本的 Windows Management Framework，以及自動化提取伺服器佈建的 DSC 模組。

### <a name="wmf"></a>WMF

Windows Server 2012 R2 包含名為 DSC 服務的功能。 DSC 服務功能提供提取伺服器功能，包括支援 OData 端點的二進位檔。
WMF 包含在 Windows Server 中，並隨不定期發行的 Windows Server 更新。 [新版 WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) 可包含 DSC 服務功能的更新。 基於這個理由，最好下載最新版的 WMF，並檢閱版本資訊來判斷版本是否包含 DSC 服務功能的更新。 您也應該檢閱指出更新或案例的設計狀態列為穩定或實驗性的版本資訊一節。
為保持彈性靈活的發行週期，個別功能可以宣告穩定，這表示 WMF 發行預覽版本時，功能已就緒可用於生產環境。
WMF 版本過去更新的其他功能 (詳細資訊請參閱 WMF 版本資訊)︰

- Windows PowerShell Windows PowerShell 整合式指令碼
- 環境 (ISE) Windows PowerShell Web 服務 (Management OData
- IIS延伸模組) Windows PowerShell 預期狀態設定 (DSC)
- Windows 遠端管理 (WinRM) Windows Management Instrumentation (WMI)

### <a name="dsc-resource"></a>DSC 資源

佈建使用 DSC 設定指令碼的服務，可以簡化提取伺服器部署。 本文件包含可用來部署生產就緒伺服器節點的設定指令碼。 若要使用設定指令碼，需要不包含在 Windows Server 中的 DSC 模組。 所需模組名稱是 **xPSDesiredStateConfiguration**，其中包含 DSC 資源 **xDscWebService**。 您可以在[這裡](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d)下載 xPSDesiredStateConfiguration 模組。

使用 **PowerShellGet** 模組的 `Install-Module` Cmdlet。

```powershell
Install-Module xPSDesiredStateConfiguration
```

**PowerShellGet** 模組會將模組下載至︰

`C:\Program Files\Windows PowerShell\Modules`

規劃工作|
---|
您可以存取 Windows Server 2012 R2 的安裝檔案嗎？|
部署環境可否存取網際網路，從線上組件庫下載 WMF 和模組？|
安裝作業系統之後，您要如何安裝最新的安全性更新？|
環境可否存取網際網路以取得更新，或有本機 Windows Server Update Services (WSUS) 伺服器？|
您可以存取透過離線導入包含更新的 Windows Server 安裝檔案嗎？|

### <a name="hardware-requirements"></a>硬體需求

實體和虛擬伺服器都支援提取伺服器部署。 提取伺服器的大小需求與 Windows Server 2012 R2 的需求一致。

CPU：1.4 GHz 64 位元處理器記憶體：512 MB 的磁碟空間：32 GB 網路：Gigabit 乙太網路介面卡

規劃工作|
---|
您要部署在實體硬體或虛擬平台？|
目標環境要求新伺服器的程序為何？|
伺服器變成可用的平均迴轉時間為何？|
您會要求何種大小的伺服器？|

### <a name="accounts"></a>帳戶

部署提取伺服器執行個體沒有任何服務帳戶需求。
不過有些時候網站會以本機使用者帳戶的內容執行。
例如，如果需要存取網站內容的儲存體共用，但 Windows Server 或裝載儲存體共用的裝置未加入網域。

### <a name="dns-records"></a>DNS 記錄

設定用戶端使用提取伺服器環境時需要使用伺服器名稱。
測試環境通常會使用伺服器主機名稱，但若無法使用 DNS 名稱解析，則使用伺服器的 IP 位址。
在生產環境或用來表示生產部署的實驗室環境中，最佳做法是建立 DNS CNAME 記錄。

DNS CNAME 可讓您建立指向主機 (A) 記錄的別名。
其他名稱記錄的目的，是如果以後需要變更時能夠增加彈性。
CNAME 可以協助隔離用戶端設定，以便伺服器環境的變更，例如取代提取伺服器或新增其他提取伺服器，不需要與用戶端設定相對應的變更。

在選擇 DNS 記錄名稱時，請牢記解決方案架構。
如果使用負載平衡，則用來保護 HTTPS 流量的憑證就需要與 DNS 記錄共用相同的名稱。

案例 |最佳做法
:---|:---
測試環境 |可能的話，請重新產生規劃的生產環境。 伺服器主機名稱適用於簡單的設定。 若無 DNS 可用，主機名稱可使用 IP 位址。|
單一節點部署 |建立指向伺服器主機名稱的 DNS CNAME 記錄。|

如需詳細資訊，請參閱[在 Windows Server 中設定 DNS 循環配置資源](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10))。

規劃工作|
---|
您知道若要建立與變更 DNS 記錄要連絡誰嗎？|
DNS 記錄要求的平均迴轉時間為何？|
您需要要求伺服器的靜態主機名稱 (A) 記錄嗎？|
您要以 CNAME 的名義要求什麼？|
如有需要，您要使用何種負載平衡解決方案？ (詳細資訊請參閱＜負載平衡＞一節)|

### <a name="public-key-infrastructure"></a>公開金鑰基礎結構

現今大部分的組織都需要網路流量，特別是包含伺服器設定方式等機密資料的流量，必須在傳送時驗證及/或加密。
雖然您可以部署使用 HTTP 的提取伺服器來方便用戶端以純文字提出要求，但最好的做法卻是保護使用 HTTPS 的流量。 您可以在 DSC 資源 **xPSDesiredStateConfiguration** 中使用一組參數，設定服務使用 HTTPS。

保護提取伺服器 HTTPS 流量的憑證需求，和保護任何其他 HTTPS 網站的沒有不同。 Windows Server 憑證服務的 **Web 伺服器**範本符合所需功能。

規劃工作|
---|
如果憑證要求未自動化，您要連絡誰要求憑證？|
要求的平均迴轉時間為何？|
如何傳送憑證檔案給您？|
如何傳送憑證私密金鑰給您？|
預設到期時間多長？|
提取伺服器環境已就緒可用於憑證名稱的 DNS 名稱了嗎？|

### <a name="choosing-an-architecture"></a>選擇架構

您可以使用裝載於 IIS 的 Web 服務或 SMB 檔案共用來部署提取伺服器。 在大部分情況下，Web 服務選項會提供較大的彈性。 HTTPS 流量周遊網路界限很常見，但 SMB 流量通常會在網路間被篩選或封鎖。 Web 服務也提供包含相容伺服器或 Web 報告管理員的選項 (本文件會在未來版本中處理這兩個主題)，提供一個機制供用戶端向伺服器回報狀態，以集中處理。
SMB 讓原則規定不該使用 Web 伺服器的環境，以及不要求 Web 伺服器角色的其他環境需求，有選擇的機會。
無論哪一種情況，請記得評估簽署與加密流量的需求。 HTTPS、SMB 簽署和 IPSEC 原則都是值得考慮的選項。

#### <a name="load-balancing"></a>負載平衡

與 Web 服務互動的用戶端提出以單一回應傳回資訊的要求。 不需要任何循序要求，因此負載平衡平台沒必要確保隨時在單一伺服器上維護工作階段。

規劃工作|
---|
跨伺服器的負載平衡流量會使用哪些解決方案？|
如果使用硬體負載平衡器，誰會接受將新的設定新增至裝置的要求？|
設定新負載平衡 Web 服務要求的平均迴轉時間為何？|
要求需要哪些資訊？|
是您必須要求額外的 IP，還是負責負載平衡的小組處理此事？|
您是否有需要的 DNS 記錄，負責設定負載平衡解決方案的小組會需要它嗎？|
負載平衡解決方案需要的 PKI，是由裝置處理，還是只要沒有工作階段需求，它就可以平衡 HTTPS 流量的負載？|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>提取伺服器上的預備設定和模組

您需要思考提取伺服器要裝載哪些 DSC 模組和設定，這是設定規劃的一部分。 為達成設定規劃的目的，對如何準備內容並將其部署到提取伺服器，一定要有基本的了解。

未來會擴展本節的內容，並收錄到 DSC 提取伺服器的操作指南中。  本指南會討論管理模組和設定日常程序的自動化進程。

#### <a name="dsc-modules"></a>DSC 模組

要求設定的用戶端會需要必要的 DSC 模組。 提取伺服器有一項功能是將 DSC 模組自動隨選散佈給用戶端。 如果您是第一次部署提取伺服器，可能是基於實驗室或證明概念的需要，您可能會相依於從 PowerShell 組件庫等公用存放庫或 DSC 模組的 PowerShell.org GitHub 存放庫取得的 DSC 模組。

請務必記住，即使是受信任的線上來源，例如 PowerShell 組件庫，從公開存放庫下載的任何模組，都應該由具有 PowerShell 經驗和環境知識的人員檢閱，而在該環境中模組的使用早於生產前。 完成此工作的同時，也是檢查模組中是否有可移除的任何其他裝載的好時機，例如文件和範例指令碼。 透過網路將模組從伺服器下載到用戶端時，這會降低每個用戶端之第一個要求的網路頻寬。

每個模組都必須以特定格式封裝為包含模組裝載之 ModuleName_Version.zip 的 ZIP 檔案。 將檔案複製到伺服器之後，就必須建立總和檢查碼檔案。 當用戶端連接到伺服器時，會使用總和檢查碼確認 DSC 模組的內容自發行以來是否變更。

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

規劃工作|
---|
您是否要規劃案例是驗證關鍵的測試或實驗室環境呢？|
是否有可公開取得的模組，包含涵蓋所需一切的資源，還是您需要自行撰寫資源？|
您的環境能否存取網際網路以擷取公用模組？|
誰會負責檢閱 DSC 模組？|
如果您要規劃生產環境，您會使用什麼當作本機存放庫來儲存 DSC 模組？|
中心小組接不接受應用程式小組的 DSC 模組？ 程序為何？|
您會從自己的來源存放庫自動化封裝、複製及建立伺服器的生產就緒 DSC 模組總和檢查碼嗎？|
您的小組也會負責管理自動化平台嗎？|

#### <a name="dsc-configurations"></a>DSC 設定

提取伺服器的目的是提供集中式機制，將 DSC 設定散發到用戶端節點。 設定在伺服器上儲存為 MOF 文件。
每份文件都會以唯一的 **GUID** 命名。 當用戶端設定成要與提取伺服器連線時，也會收到其應要求的設定 **GUID**。 這個依 **GUID** 參考設定的系統能保證全域唯一性，而且十分靈活，讓設定能夠以細微到節點的程度套用，也能以角色設定形式套用，以橫跨多個應該具有相同設定的伺服器。

#### <a name="guids"></a>GUID

當您在考量整個提取伺服器部署時，設定 **GUID** 的規劃值得多加留意。 處理 **GUID** 的方式並沒有明確要求，而且每個環境的程序很可能各不相同。 程序從簡單到複雜︰集中儲存的 CSV 檔案、簡易 SQL 資料表、CMDB 或需要整合其他工具或軟體方案的複雜解決方案。 有兩種一般方法︰

- **依伺服器指派 GUID**：提供確保個別控制每部伺服器設定的量值。 這會提供更新前後一定程度的準確性，在只有幾部伺服器的環境中運作良好。
- **依伺服器角色指派 GUID**：執行相同函式的所有伺服器 (例如網頁伺服器) 都使用相同的 GUID 參考所需的設定資料。  請注意，如果有許多伺服器共用相同的 GUID，設定變更時，它們全部都會同時更新。

  GUID 應該視為機密資訊，因為它可用來進行惡意攻擊，取得您環境如何部署與設定伺服器的情報。 如需詳細資訊，請參閱 [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/) (在 PowerShell Desired State Configuration 提取模式中安全地配置 GUID)。

規劃工作|
---|
誰會負責將就緒的設定複製到提取伺服器資料夾？|
如果是應用程式小組撰寫設定，設定的交付程序為何？|
您會利用存放庫，跨小組儲存撰寫中的設定嗎？|
您會自動化將設定複製到伺服器，並於就緒時建立總和檢查碼的程序嗎？|
您會如何將 GUID 對應至伺服器或角色？這份資料會儲存在何處？|
您要使用什麼樣的程序來設定用戶端電腦？它會如何與您建立及儲存設定 GUID 的程序整合？|

## <a name="installation-guide"></a>安裝指南

*本文件中提供的指令碼都是穩定的範例。請務必先仔細閱讀指令碼，再於生產環境中執行它們。*

### <a name="prerequisites"></a>必要條件

請使用下列命令確認伺服器上的 PowerShell 版本。

```powershell
$PSVersionTable.PSVersion
```

可能的話，請升級至最新版的 Windows Management Framework。
然後，使用下列命令下載 `xPsDesiredStateConfiguration` 模組。

```powershell
Install-Module xPSDesiredStateConfiguration
```

命令會要求您核准後才下載模組。

### <a name="installation-and-configuration-scripts"></a>安裝與設定指令碼

部署 DSC 提取伺服器的最佳方法是使用 DSC 設定指令碼。 本文件顯示的指令碼，包括只設定 DSC Web 服務的基本設定，以及設定 Windows Server 端對端 (包括 DSC Web 服務) 的進階設定。

注意：目前 `xPSDesiredStateConfiguration` DSC 模組需要伺服器使用 EN-US 地區設定。

### <a name="basic-configuration-for-windows-server-2012"></a>Windows Server 2012 基本設定

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Windows Server 2012 R2 進階設定

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a>確認提取伺服器功能

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>設定用戶端

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a>其他參考資料、程式碼片段和範例

本範例示範如何以手動方式啟動用戶端連線 (需要 WMF5) 以進行測試。

```powershell
Update-DscConfiguration –Wait -Verbose
```

[Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) Cmdlet 用於將 CNAME 記錄類型新增至 DNS 區域。

[Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) (建立總和檢查碼並將 DSC MOF 發行至 SMB 提取伺服器) 的 PowerShell 函式會自動產生所需的總和檢查碼，然後將 MOF 設定和總和檢查碼檔案複製到 SMB 提取伺服器。

## <a name="appendix---understanding-odata-service-data-file-types"></a>附錄：了解 ODATA 服務的資料檔案類型

儲存資料檔案是為了建立含 OData Web 服務的提取伺服器在部署期間的資訊。 檔案類型視作業系統而定，如下所述。

- **Windows Server 2012** 檔案類型一律為 .mdb
- **Windows Server 2012 R2** 除非設定中指定 .mdb，否則檔案類型預設為 .edb

在安裝提取伺服器的[進階範例指令碼](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts)中，您也會找到如何自動控制 web.config 檔案設定，防止因檔案類型而發生任何錯誤的範例。
