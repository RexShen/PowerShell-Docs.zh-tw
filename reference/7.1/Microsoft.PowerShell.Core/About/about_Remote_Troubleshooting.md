---
description: 說明如何針對 PowerShell 中的遠端作業進行疑難排解。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Troubleshooting
ms.openlocfilehash: f19cb90a8671cbe0885af817b0cd8849adc79338
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2020
ms.locfileid: "93208935"
---
# <a name="about-remote-troubleshooting"></a>關於遠端疑難排解

## <a name="short-description"></a>簡短描述
說明如何針對 PowerShell 中的遠端作業進行疑難排解。

## <a name="long-description"></a>完整描述

本節說明當您使用以 WS-Management 技術為基礎的 PowerShell 遠端功能時，可能會遇到的一些問題，並建議這些問題的解決方案。

使用 PowerShell 遠端處理之前，請參閱 [about_Remote](about_remote.md) 和 [about_Remote_Requirements](about_Remote_Requirements.md) ，以取得設定和基本用途的指引。 此外，每個遠端 Cmdlet 的說明主題（特別是參數描述）都有實用的資訊，其設計目的是要協助您避免問題。

> [!NOTE]
> 若要在 WSMan：磁片磁碟機中查看或變更本機電腦的設定，包括會話設定、受信任的主機、埠或接聽程式的變更，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

## <a name="troubleshooting-permission-and-authentication-issues"></a>針對許可權和驗證問題進行疑難排解

本節討論與使用者和電腦許可權和遠端處理需求相關的遠端處理問題。

### <a name="how-to-run-as-administrator"></a>如何以系統管理員身分執行

```
ERROR: Access is denied. You need to run this cmdlet from an elevated
process.
```

若要在本機電腦上啟動遠端會話，或在 WSMan：磁片磁碟機中查看或變更本機電腦的設定，包括會話設定、受信任的主機、埠或接聽程式的變更，請使用 [以 **系統管理員身分執行** ] 選項開始 Windows PowerShell。

若要使用 [以 **系統管理員身分執行** ] 選項開始 Windows PowerShell：

- 以滑鼠右鍵按一下 Windows PowerShell (或 Windows PowerShell ISE) 圖示，然後按一下 [以 **系統管理員身分執行** ]。

  使用 Windows 7 和 Windows Server 2008 R2 中的 [以 **系統管理員身分執行** ] 選項開始 Windows PowerShell。

- 在 Windows 工作列中，以滑鼠右鍵按一下 Windows PowerShell 圖示，然後按一下 [以 **系統管理員身分執行** ]。

  在 Windows Server 2008 R2 中，預設會將 Windows PowerShell 圖示釘選到工作列。

### <a name="how-to-enable-remoting"></a>如何啟用遠端處理

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to
listen for requests on the correct port and HTTP URL.
```

不需要進行任何設定，就能讓電腦傳送遠端命令。
不過，若要接收遠端命令，電腦上必須啟用 PowerShell 遠端功能。 啟用包括啟動 WinRM 服務、將 WinRM 服務的啟動類型設定為 [自動]、建立 HTTP 和 HTTPS 連接的接聽程式，以及建立預設的會話設定。

預設會在 Windows Server 2012 和更新版本的 Windows Server 上啟用 Windows PowerShell 遠端處理。 在所有其他系統上，執行 `Enable-PSRemoting` Cmdlet 以啟用遠端功能。 `Enable-PSRemoting`如果停用遠端功能，您也可以執行 Cmdlet，在 Windows server 2012 和更新版本的 Windows server 上重新啟用遠端功能。

若要設定電腦接收遠端命令，請使用 `Enable-PSRemoting` Cmdlet。 下列命令會啟用所有必要的遠端設定、啟用會話設定，然後重新開機 WinRM 服務，讓變更生效。

`Enable-PSRemoting`

若要隱藏所有使用者提示，請輸入：

`Enable-PSRemoting -Force`

如需詳細資訊，請參閱 [啟用->enable-psremoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting)。

### <a name="how-to-enable-remoting-in-an-enterprise"></a>如何在企業中啟用遠端功能

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

若要讓單一電腦接收遠端 PowerShell 命令並接受連接，請使用 `Enable-PSRemoting` Cmdlet。

若要啟用企業中多部電腦的遠端功能，您可以使用下列調整的選項。

- 若要設定遠端接聽程式，請啟用 [ **允許自動** 設定接聽程式] 群組原則。

- 若要在多部電腦上將 Windows 遠端管理 (WinRM) 的啟動類型設定為 [自動]，請使用 `Set-Service` Cmdlet。

- 若要啟用防火牆例外，請使用 [ **Windows 防火牆：允許本機埠例外** ] 群組原則。

### <a name="how-to-enable-listeners-by-using-a-group-policy"></a>如何使用群組原則啟用接聽程式

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

若要為網域中的所有電腦設定接聽程式，請在下列群組原則路徑中啟用 [ **允許自動** 設定接聽程式] 原則：

```
Computer Configuration\Administrative Templates\Windows Components
    \Windows Remote Management (WinRM)\WinRM service
```

啟用原則，並指定 IPv4 和 IPv6 篩選器。 允許 (`*`) 的萬用字元。

### <a name="how-to-enable-remoting-on-public-networks"></a>如何在公用網路上啟用遠端功能

```
ERROR:  Unable to check the status of the firewall
```

`Enable-PSRemoting`當局域網路是公用的，而且命令中未使用 **SkipNetworkProfileCheck** 參數時，此 Cmdlet 會傳回這個錯誤。

在伺服器版本的 Windows 上， `Enable-PSRemoting` 所有網路位置類型都會成功。 它會建立防火牆規則，以允許遠端存取私用和網域 ( "Home" 和 "Work" ) 網路。 針對公用網路，它會建立防火牆規則，以允許從相同的本機子網進行遠端存取。

在用戶端版本的 Windows 上， `Enable-PSRemoting` 在私用和網域網路上會成功。 依預設，它會在公用網路上失敗，但如果您使用 **SkipNetworkProfileCheck** 參數，則會 `Enable-PSRemoting` 成功，並建立允許來自相同本機子網之流量的防火牆規則。

若要移除公用網路上的本機子網限制，並允許從任何位置進行遠端存取，請執行下列命令：

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

此 `Set-NetFirewallRule` Cmdlet 是由 NetSecurity 模組匯出。

> [!NOTE]
> 在 Windows PowerShell 2.0 中，在執行 Windows server 版本的電腦上， `Enable-PSRemoting` 會建立防火牆規則，允許在私人、網域及公用網路上進行遠端存取。 在執行 Windows 用戶端版本的電腦上， `Enable-PSRemoting` 會建立只允許在私用和網域網路上進行遠端存取的防火牆規則。

### <a name="how-to-enable-a-firewall-exception-by-using-a-group-policy"></a>如何使用群組原則啟用防火牆例外

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

若要在網域中的所有電腦上啟用防火牆例外，請啟用下列群組原則路徑中的 [ **Windows 防火牆：允許本機埠例外** ] 原則：

```
Computer Configuration\Administrative Templates\Network
    \Network Connections\Windows Firewall\Domain Profile
```

這項原則可讓電腦上的 Administrators 群組成員使用 **主控台** 中的 **Windows 防火牆** ，以建立 Windows 遠端管理服務的防火牆例外。

如果原則設定不正確，您可能會收到下列錯誤：

```
The client cannot connect to the destination specified in the request. Verify
that the service on the destination is running and is accepting requests.
```

原則中的設定錯誤會導致 **ListeningOn** 屬性的值為空值。 使用下列命令來檢查值。

```powershell
PS> Get-WSManInstance winrm/config/listener -Enumerate

cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
Source                : GPO
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 5985
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {}
```

### <a name="how-to-set-the-startup-type-of-the-winrm-service"></a>如何設定 WinRM 服務的啟動類型

```
ERROR:  ACCESS IS DENIED
```

PowerShell 遠端處理取決於 Windows 遠端管理 (WinRM) 服務。
服務必須正在執行，才能支援遠端命令。

在伺服器版本的 Windows 上，Windows 遠端管理 (WinRM) 服務的啟動類型為自動。

不過，在用戶端版本的 Windows 上，預設會停用 WinRM 服務。

若要在遠端電腦上設定服務的啟動類型，請使用 `Set-Service` Cmdlet。

若要在多部電腦上執行命令，您可以建立電腦名稱稱的文字檔或 CSV 檔案。

例如，下列命令會取得檔案中的電腦名稱稱清單 `Servers.txt` ，然後將所有電腦上的 WinRM 服務啟動類型設定為 [ **自動** ]。

```powershell
$servers = Get-Content servers.txt
Set-Service WinRM -ComputerName $servers -startuptype Automatic
```

若要查看結果，請使用 `Get-WMIObject` Cmdlet 搭配 **Win32_Service** 物件。 如需詳細資訊，請參閱 [設定服務](xref:Microsoft.PowerShell.Management.Set-Service)。

### <a name="how-to-recreate-the-default-session-configurations"></a>如何重新建立預設會話設定

```
ERROR:  ACCESS IS DENIED
```

若要連接到本機電腦並從遠端執行命令，本機電腦必須包含遠端命令的會話設定。

當您使用時 `Enable-PSRemoting` ，它會在本機電腦上建立預設的會話設定。 遠端使用者只要遠端命令未包含 **ConfigurationName** 參數，就會使用這些會話設定。

如果電腦上的預設設定為取消註冊或刪除，請使用 `Enable-PSRemoting` Cmdlet 重新建立它們。 您可以重複使用此 Cmdlet。 如果已設定功能，則不會產生錯誤。

如果您變更預設會話設定，並想要還原原始的預設會話設定，請使用 `Unregister-PSSessionConfiguration` Cmdlet 來刪除已變更的會話設定，然後使用指令程式 `Enable-PSRemoting` 來還原它們。
`Enable-PSRemoting` 不會變更現有的會話設定。

> [!NOTE]
> `Enable-PSRemoting`還原預設會話設定時，不會為設定建立明確的安全描述項。 相反地，設定會繼承 RootSDDL 的安全描述項（預設為安全）。

若要查看 RootSDDL 安全描述項，請輸入：

```powershell
Get-Item wsman:\localhost\Service\RootSDDL
```

若要變更 RootSDDL，請使用 `Set-Item` WSMan：磁片磁碟機中的 Cmdlet。 若要變更會話設定的安全描述項，請使用 `Set-PSSessionConfiguration` Cmdlet 搭配 **SecurityDescriptorSDDL** 或 **ShowSecurityDescriptorUI** 參數。

如需 WSMan：磁片磁碟機的詳細資訊，請參閱 WSMan 提供者的說明主題 ( "Get-help WSMan" ) 。

### <a name="how-to-provide-administrator-credentials"></a>如何提供系統管理員認證

```
ERROR:  ACCESS IS DENIED
```

若要在遠端電腦上建立 PSSession 或執行命令，則目前的使用者必須是遠端電腦上 Administrators 群組的成員。 即使目前的使用者登入屬於 Administrators 群組成員的帳戶，有時還是需要認證。

如果目前的使用者是遠端電腦上 Administrators 群組的成員，或者可以提供 Administrators 群組成員的認證，請使用的 **Credential** 參數 `New-PSSession` `Enter-PSSession` 或 `Invoke-Command` Cmdlet 從遠端連線。

例如，下列命令會提供系統管理員的認證。

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\Admin01
```

如需 **Credential** 參數的詳細資訊，請參閱 [新的-pssession](xref:Microsoft.PowerShell.Core.New-PSSession)、 [輸入-pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession) 或 [Invoke 命令](xref:Microsoft.PowerShell.Core.Invoke-Command)。

### <a name="how-to-enable-remoting-for-non-administrative-users"></a>如何啟用非系統管理使用者的遠端處理

```
ERROR:  ACCESS IS DENIED
```

若要在遠端電腦上建立 PSSession 或執行命令，使用者必須有許可權可以使用遠端電腦上的會話設定。

依預設，只有電腦上 Administrators 群組的成員才有使用預設會話設定的許可權。 因此，只有 Administrators 群組的成員可以從遠端連線到電腦。

若要允許其他使用者連接到本機電腦，請將本機電腦上預設會話設定的 [執行] 許可權授與使用者。

下列命令會開啟屬性工作表，讓您在本機電腦上變更預設的 Microsoft PowerShell 會話設定的安全描述項。

```powershell
Set-PSSessionConfiguration Microsoft.PowerShell -ShowSecurityDescriptorUI
```

如需詳細資訊，請參閱 [about_Session_Configurations](about_Session_Configurations.md)。

### <a name="how-to-enable-remoting-for-administrators-in-other-domains"></a>如何為其他網域中的系統管理員啟用遠端處理

```
ERROR:  ACCESS IS DENIED
```

當另一個網域中的使用者是本機電腦上 Administrators 群組的成員時，該使用者就無法使用系統管理員許可權從遠端連線到本機電腦。 根據預設，來自其他網域的遠端連線只會以標準使用者權限權杖執行。

不過，您可以使用 **LocalAccountTokenFilterPolicy** 登錄專案來變更預設行為，並允許身為 Administrators 群組成員的遠端使用者以系統管理員許可權執行。

> [!CAUTION]
> **LocalAccountTokenFilterPolicy** 專案會針對所有受影響電腦的所有使用者，停用 (UAC) 遠端限制的使用者帳戶控制。 變更原則之前，請先仔細考慮這項設定的含意。

若要變更原則，請使用下列命令將 **LocalAccountTokenFilterPolicy** 登錄專案的值設定為1。

```powershell
New-ItemProperty -Name LocalAccountTokenFilterPolicy `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System `
  -PropertyType DWord -Value 1
```

### <a name="how-to-use-an-ip-address-in-a-remote-command"></a>如何在遠端命令中使用 ip 位址

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

的 **ComputerName** 參數 `New-PSSession` `Enter-PSSession` 和 `Invoke-Command` Cmdlet 會接受 IP 位址做為有效的值。 不過，因為 Kerberos 驗證不支援 IP 位址，所以每當您指定 IP 位址時，預設都會使用 NTLM 驗證。

使用 NTLM 驗證時，需要下列程式進行遠端處理。

1. 設定電腦的 HTTPS 傳輸，或將遠端電腦的 IP 位址新增至本機電腦上的 TrustedHosts 清單。

1. 在所有遠端命令中使用 **Credential** 參數。

   即使您要提交目前使用者的認證，也需要此項。

### <a name="how-to-connect-remotely-from-a-workgroup-based-computer"></a>如何從工作組型電腦遠端連線

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

當本機電腦不在網域中時，需要下列程式進行遠端處理。

1. 設定電腦的 HTTPS 傳輸，或將遠端電腦的名稱新增至本機電腦上的 TrustedHosts 清單。

1. 確認工作組型電腦上已設定密碼。 如果未設定密碼或密碼值是空的，您就無法執行遠端命令。

   若要設定使用者帳戶的密碼，請使用主控台中的使用者帳戶。

1. 在所有遠端命令中使用 **Credential** 參數。

   即使您要提交目前使用者的認證，也需要此項。

### <a name="how-to-add-a-computer-to-the-trusted-hosts-list"></a>如何將電腦新增到信任的主機清單

TrustedHosts 專案可以包含以逗號分隔的電腦名稱稱、IP 位址和完整功能變數名稱清單。 允許使用萬用字元。

若要查看或變更信任的主機清單，請使用 WSMan：磁片磁碟機。 TrustedHost 專案位於 `WSMan:\localhost\Client` 節點中。

只有電腦上 Administrators 群組的成員有權變更電腦上受信任的主機清單。

注意：您為 TrustedHosts 專案設定的值會影響電腦的所有使用者。

若要查看信任的主機清單，請使用下列命令：

```powershell
Get-Item wsman:\localhost\Client\TrustedHosts
```

您也可以使用 `Set-Location` Cmdlet (alias = cd) ，以從 WSMan：磁片磁碟機流覽至該位置。 例如：

```powershell
cd WSMan:\localhost\Client; dir
```

若要將所有電腦新增到信任的主機清單，請使用下列命令，其值為 * (ComputerName 中的所有) 

```powershell
Set-Item wsman:localhost\client\trustedhosts -Value *
```

您也可以使用萬用字元 () 將 `*` 特定網域中的所有電腦新增到信任的主機清單。 例如，下列命令會將 Fabrikam 網域中的所有電腦新增到信任的主機清單中。

```powershell
Set-Item wsman:localhost\client\trustedhosts *.fabrikam.com
```

若要將特定電腦的名稱新增至信任主機清單，請使用下列命令格式：

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <ComputerName>
```

其中每個值都 `<ComputerName>` 必須具有下列格式：

```
<Computer>.<Domain>.<Company>.<top-level-domain>
```

例如：

```powershell
$server = 'Server01.Domain01.Fabrikam.com'
Set-Item wsman:\localhost\Client\TrustedHosts -Value $server
```

若要將電腦名稱稱新增至現有的受信任主機清單，請先將目前的值儲存在變數中，然後將值設定為包含目前值和新值的逗號分隔清單。

例如，若要將 Server01 電腦新增至現有的受信任主機清單，請使用下列命令

```powershell
$curValue = (Get-Item wsman:\localhost\Client\TrustedHosts).value

Set-Item wsman:\localhost\Client\TrustedHosts -Value `
  "$curValue, Server01.Domain01.Fabrikam.com"
```

若要將特定電腦的 IP 位址新增至信任主機清單，請使用下列命令格式：

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <IP Address>
```

例如：

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value 172.16.0.0
```

若要將電腦新增至遠端電腦的 TrustedHosts 清單，請使用 `Connect-WSMan` Cmdlet 將遠端電腦的節點新增到本機電腦上的 WSMan：磁片磁碟機。 然後使用 `Set-Item` 命令來新增電腦。

如需有關 Cmdlet 的詳細資訊 `Connect-WSMan` ，請參閱 [連接-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)。

## <a name="troubleshooting-computer-configuration-issues"></a>針對電腦設定問題進行疑難排解

本節討論與電腦、網域或企業特定設定相關的遠端處理問題。

### <a name="how-to-configure-remoting-on-alternate-ports"></a>如何設定替代埠上的遠端處理

```
ERROR: The connection to the specified remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

PowerShell 遠端預設會針對 HTTP 傳輸使用埠80。 每當使用者未在遠端命令中指定 **ConnectionURI** 或 **埠** 參數時，就會使用預設通訊埠。

若要變更 PowerShell 使用的預設通訊埠，請使用 `Set-Item` WSMan：磁片磁碟機中的 Cmdlet 來變更接聽程式分節點中的埠值。

例如，下列命令會將預設埠變更為8080。

```powershell
Set-Item wsman:\localhost\listener\listener*\port -Value 8080
```

### <a name="how-to-configure-remoting-with-a-proxy-server"></a>如何設定 proxy 伺服器的遠端處理

```
ERROR: The client cannot connect to the destination specified in the request.
Verify that the service on the destination is running and is accepting
requests.
```

因為 PowerShell 遠端使用 HTTP 通訊協定，所以會受到 HTTP proxy 設定的影響。 在具有 proxy 伺服器的企業中，使用者無法直接存取 PowerShell 遠端電腦。

若要解決此問題，請在遠端命令中使用 proxy 設定選項。 可用的設定如下：

- System.management.automation.remoting.proxyaccesstype
- ProxyAuthentication
- ProxyCredential

若要為特定命令設定這些選項，請使用下列程式：

1. 使用 Cmdlet 的 **system.management.automation.remoting.proxyaccesstype** 、 **ProxyAuthentication** 和 **ProxyCredential** 參數， `New-PSSessionOption` 建立具有您企業之 proxy 設定的會話選項物件。 將選項物件儲存為變數。

1. 使用包含 option 物件的變數做為 **SessionOption** `New-PSSession` 、 `Enter-PSSession` 或命令的 SessionOption 參數值 `Invoke-Command` 。

例如，下列命令會建立具有 proxy 會話選項的會話選項物件，然後使用該物件來建立遠端會話。

```powershell
$SessionOption = New-PSSessionOption -ProxyAccessType IEConfig `
-ProxyAuthentication Negotiate -ProxyCredential Domain01\User01

New-PSSession -ConnectionURI https://www.fabrikam.com
```

如需有關 Cmdlet 的詳細資訊 `New-PSSessionOption` ，請參閱 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。

若要為目前會話中的所有遠端命令設定這些選項，請使用在 `New-PSSessionOption` 喜好設定變數值中建立的選項物件 `$PSSessionOption` 。 如需詳細資訊，請參閱 [about_Preference_Variables](about_Preference_Variables.md)。

若要為所有遠端命令設定本機電腦上所有 PowerShell 會話的這些選項，請將 `$PSSessionOption` 喜好設定變數新增至您的 PowerShell 設定檔。 如需 PowerShell 設定檔的詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。

### <a name="how-to-detect-a-32-bit-session-on-a-64-bit-computer"></a>如何在64位電腦上偵測32位的會話

```
ERROR: The term "<tool-Name>" is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

如果遠端電腦執行的是64位版本的 Windows，而遠端命令使用32位會話設定（例如 Microsoft.powershell32），則 Windows 遠端管理 (WinRM) 會載入 WOW64 進程，而 Windows 會自動將目錄的所有參考重新導向 `$env:Windir\System32` 至 `$env:Windir\SysWOW64` 目錄。

如此一來，如果您嘗試使用 System32 目錄中的工具，而這些工具在 SysWow64 目錄中沒有對應專案（例如），則在 `Defrag.exe` 目錄中找不到工具。

若要尋找會話中使用的處理器架構，請使用 **PROCESSOR_ARCHITECTURE** 環境變數的值。 下列命令會在變數中尋找會話的處理器架構 `$s` 。

```powershell
$s = New-PSSession -ComputerName Server01 -ConfigurationName CustomShell
Invoke-Command -Session $s {$env:PROCESSOR_ARCHITECTURE}
```

```Output
x86
```

如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](about_Session_Configurations.md)。

## <a name="troubleshooting-policy-and-preference-issues"></a>針對原則和喜好設定問題進行疑難排解

本節討論與本機電腦和遠端電腦上設定的原則和喜好設定相關的遠端處理問題。

### <a name="how-to-change-the-execution-policy-for-import-pssession-and-import-module"></a>如何變更 Import-PSSession 和 Import-Module 的執行原則

```
ERROR: Import-Module: File <filename> cannot be loaded because the
execution of scripts is disabled on this system.
```

`Import-PSSession`和 `Export-PSSession` Cmdlet 會建立包含未簽署腳本檔案和格式化檔案的模組。

若要使用或來匯入這些 Cmdlet 所建立的模組， `Import-PSSession` 則 `Import-Module` 無法限制或 AllSigned 目前會話中的執行原則。 如需 PowerShell 執行原則的詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。

若要匯入模組而不變更登錄中設定之本機電腦的執行原則，請使用的 **範圍** 參數，為 `Set-ExecutionPolicy` 單一進程設定較不嚴格的執行原則。

例如，下列命令會啟動具有執行原則的進程 `RemoteSigned` 。 執行原則變更只會影響目前的進程，而不會變更 PowerShell **ExecutionPolicy** 登錄設定。

```powershell
Set-ExecutionPolicy -Scope process -ExecutionPolicy RemoteSigned
```

您也可以使用的 **ExecutionPolicy** 參數 `PowerShell.exe` ，以較不嚴格的執行原則來啟動單一會話。

```powershell
PowerShell.exe -ExecutionPolicy RemoteSigned
```

如需執行原則的詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。 如需詳細資訊，請鍵入 `PowerShell.exe -?`。

### <a name="how-to-set-and-change-quotas"></a>如何設定和變更配額

```
ERROR: The total data received from the remote client exceeded allowed
maximum.
```

您可以使用配額來防止本機電腦和遠端電腦過度使用資源，而不會發生意外和惡意。

基本設定中提供下列配額。

- WSMan 提供者 (WSMan： ) 提供數個配額設定，例如節點中的 **MaxEnvelopeSizeKB** 和 **MaxProviderRequests** 設定， `WSMan:<ComputerName>` 以及節點中的 **MaxConcurrentOperations** 、 **MaxConcurrentOperationsPerUser** 和 **MaxConnections** 設定 `WSMan:<ComputerName>\Service` 。

- 您可以使用 Cmdlet 的 **MaximumReceivedDataSizePerCommand** 和 **MaximumReceivedObjectSize** 參數和喜好設定變數來保護本機電腦 `New-PSSessionOption` `$PSSessionOption` 。

- 您可以藉由新增會話設定的限制（例如，使用 Cmdlet 的 **MaximumReceivedDataSizePerCommandMB** 和 **MaximumReceivedObjectSizeMB** 參數）來保護遠端電腦 `Register-PSSessionConfiguration` 。

當配額與命令衝突時，PowerShell 會產生錯誤。

若要解決此錯誤，請將遠端命令變更為符合配額。 或者，判斷配額的來源，然後增加配額以允許命令完成。

例如，下列命令會將遠端電腦上的 Microsoft PowerShell 會話設定中的物件大小配額增加為 10 MB (預設值) 為 11 MB。

```powershell
Set-PSSessionConfiguration -Name microsoft.PowerShell `
  -MaximumReceivedObjectSizeMB 11 -Force
```

如需此 Cmdlet 的詳細資訊 `New-PSSessionOption` ，請參閱 `New-PSSessionOption` 。

如需 WS-Management 配額的詳細資訊，請參閱 [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)。

### <a name="how-to-resolve-timeout-errors"></a>如何解決逾時錯誤

```
ERROR: The WS-Management service cannot complete the operation within
the time specified in OperationTimeout.
```

您可以使用超時來防止本機電腦和遠端電腦過度使用資源，而不會發生意外和惡意。 在本機和遠端電腦上設定 timeout 時，PowerShell 會使用最短的 timeout 設定。

基本設定中提供下列超時。

- WSMan 提供者 (WSMan： ) 提供數個用戶端和服務端的超時設定，例如節點中的 **MaxTimeoutms** 設定， `WSMan:<ComputerName>` 以及節點中的 **EnumerationTimeoutms** 和 **MaxPacketRetrievalTimeSeconds** 設定 `WSMan:<ComputerName>\Service` 。

- 您可以使用 Cmdlet 的 **CancelTimeout** 、 **IdleTimeout** 、 **OpenTimeout** 和 **OperationTimeout** 參數和喜好設定變數來保護本機電腦 `New-PSSessionOption` `$PSSessionOption` 。

- 您也可以在會話的會話設定中，以程式設計的方式設定 timeout 值，以保護遠端電腦。

當超時值不允許作業完成時，PowerShell 會終止作業並產生錯誤。

若要解決此錯誤，請將命令變更為在逾時間隔內完成，或判斷超時限制的來源，並增加逾時間隔，以允許命令完成。

例如，下列命令會使用指令 `New-PSSessionOption` 程式建立 **OperationTimeout** 值為4分鐘的會話選項物件 (在 MS) 中，然後使用會話選項物件來建立遠端會話。

```powershell
$pso = New-PSSessionoption -OperationTimeout 240000

New-PSSession -ComputerName Server01 -sessionOption $pso
```

如需 WS-Management 超時的詳細資訊，請參閱 WSMan 提供者的說明主題 (類型 `Get-Help WSMan`) 。

如需有關 Cmdlet 的詳細資訊 `New-PSSessionOption` ，請參閱 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。

## <a name="troubleshooting-unresponsive-behavior"></a>針對沒有回應的行為進行疑難排解

本節討論防止命令完成和防止或延遲傳回 PowerShell 提示的遠端處理問題。

### <a name="how-to-interrupt-a-command"></a>如何中斷命令

某些原生的 Windows 程式，例如具有使用者介面的程式、會提示輸入的主控台應用程式，以及使用 Win32 主控台 API 的主控台應用程式，在 PowerShell 遠端主機中無法正常運作。

當您使用這些程式時，可能會看到非預期的行為，例如沒有輸出、部分輸出或未完成的遠端命令。

若要結束沒有回應的程式，請輸入<kbd>CTRL</kbd> + <kbd>C</kbd>。 若要查看任何可能已回報的錯誤，請輸入 `$error` 本機主機和遠端會話。

## <a name="how-to-recover-from-an-operation-failure"></a>如何從操作失敗中復原

```
ERROR: The I/O operation has been aborted because of either a thread exit
or an  application request.
```

當作業結束時，會傳回此錯誤。
一般來說，當 WinRM 服務在其他 WinRM 作業正在進行時停止或重新開機時，就會發生此情況。

若要解決此問題，請確認 WinRM 服務正在執行，然後再次嘗試命令。

1. 使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。
1. 執行下列命令：

   `Start-Service WinRM`

1. 重新執行產生錯誤的命令。

## <a name="linux-and-macos-limitations"></a>Linux 和 macOS 限制

### <a name="authentication"></a>驗證

只有基本驗證適用于 macOS，而且嘗試使用其他驗證配置可能會導致進程損毀。

請參閱 [OMI authentication](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) 指示。

## <a name="see-also"></a>另請參閱

[Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)

[Export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession)

[Import-Module](xref:Microsoft.PowerShell.Core.Import-Module)

[about_Remote](about_Remote.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[about_Remote_Variables](about_Remote_Variables.md)
