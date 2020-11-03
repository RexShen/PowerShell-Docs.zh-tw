---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmaninstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManInstance
ms.openlocfilehash: 1fd516f248e3f361d16e3643271b240f671d9009
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205476"
---
# Get-WSManInstance

## 概要
顯示由資源 URI 所指定之資源執行個體的管理資訊。

## SYNTAX

### GetInstance (預設) 

```
Get-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-ConnectionURI <Uri>] [-Dialect <Uri>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet <Hashtable>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### 列舉

```
Get-WSManInstance [-ApplicationName <String>] [-BasePropertiesOnly] [-ComputerName <String>]
 [-ConnectionURI <Uri>] [-Dialect <Uri>] [-Enumerate] [-Filter <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-Associations] [-ResourceURI] <Uri> [-ReturnType <String>] [-SessionOption <SessionOption>]
 [-Shallow] [-UseSSL] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## DESCRIPTION
**Set-wsmaninstance** 指令程式會抓取資源統一資源識別元所指定的管理資源實例， (URI) 。
抓取的資訊可能是複雜的 XML 資訊集，也就是物件或簡單的值。
此 Cmdlet 等同于管理 (WS-MANAGEMENT) **Get** 命令的標準 Web 服務。

此 Cmdlet 使用 WS-Management 連線/傳輸層來抓取資訊。

## 範例

### 範例1：從 WMI 取得所有資訊

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="winrm"} -ComputerName "Server01"
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : true
Caption                 : Windows Remote Management (WS-Management)
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Windows Remote Management (WinRM) service implements the WS-Management protocol for remote
management. WS-Management is a standard web services protocol used for remote software and
hardware management. The WinRM service listens on the network for WS-Management requests
and processes them. The WinRM Service needs to be configured with a listener using the
winrm.cmd command line tool or through Group Policy in order for it to listen over the
network. The WinRM service provides access to WMI data and enables event collection. Event
collection and subscription to events require that the service is running. WinRM messages
use HTTP and HTTPS as transports. The WinRM service does not depend on IIS but is
preconfigured to share a port with IIS on the same computer.  The WinRM service reserves the
/wsman URL prefix. To prevent conflicts with IIS, administrators should ensure that any
websites hosted on IIS do not use the /wsman URL prefix.
DesktopInteract         : false
DisplayName             : Windows Remote Management (WS-Management)
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : winrm
PathName                : C:\Windows\System32\svchost.exe -k NetworkService
ProcessId               : 948
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : true
StartMode               : Auto
StartName               : NT AUTHORITY\NetworkService
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
WaitHint                : 0
```

此命令會傳回 Windows Management Instrumentation (WMI) 對遠端 server01 電腦上的 **WinRM** 服務公開的所有資訊。

### 範例2：取得多工緩衝處理器服務的狀態

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="spooler"} -Fragment Status -ComputerName "Server01"
XmlFragment=OK
```

此命令只會傳回遠端 server01 電腦上之多工 **緩衝** 處理器服務的狀態。

### 範例3：取得所有服務的端點參考

```
PS C:\> Get-WSManInstance -Enumerate -ResourceURI wmicimv2/win32_service -ReturnType EPR
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Visual Studio 2008 Remote Debugger
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Allows members of the Administrators group to remotely debug server applications using Visual
Studio 2008. Use the Visual Studio 2008 Remote Debugging Configuration Wizard to enable this
service.
DesktopInteract         : false
DisplayName             : Visual Studio 2008 Remote Debugger
ErrorControl            : Ignore
ExitCode                : 1077
InstallDate             : InstallDate
Name                    : msvsmon90
PathName                : "C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe" /service msvsmon90
ProcessId               : 0
ServiceSpecificExitCode : 0
ServiceType             : Own Process
Started                 : false
StartMode               : Disabled
StartName               : LocalSystem
State                   : Stopped
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : COMPUTER01
TagId                   : 0
WaitHint                : 0
...
```

此命令會傳回對應到本機電腦上之所有服務的端點參照。

### 範例4：取得符合指定準則的服務

```
PS C:\> Get-WSManInstance -Enumerate -ResourceURI wmicimv2/* -Filter "select * from win32_service where StartMode = 'Auto' and State = 'Stopped'" -ComputerName "Server01"
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Windows Media Center Service Launcher
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Starts Windows Media Center Scheduler and Windows Media Center Receiver services
at startup if TV is enabled within Windows Media Center.
DesktopInteract         : false
DisplayName             : Windows Media Center Service Launcher
ErrorControl            : Ignore
ExitCode                : 0
InstallDate             : InstallDate
Name                    : ehstart
PathName                : C:\Windows\system32\svchost.exe -k LocalServiceNoNetwork
ProcessId               : 0
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : false
StartMode               : Auto
StartName               : NT AUTHORITY\LocalService
State                   : Stopped
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : Server01
TagId                   : 0
WaitHint                : 0
...
```

此命令會列出遠端 Server01 電腦上符合下列條件的所有服務：

- 服務的啟動類型為自動。
- 服務已停止。

### 範例5：取得與本機電腦上的條件相符的接聽程式設定

```
PS C:\> Get-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{Address="*";Transport="http"}
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 80
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {100.0.0.1, 123.123.123.123, ::1, 2001:4898:0:fff:0:5efe:123.123.123.123...}
```

此命令會列出本機電腦上的 WS-Management 接聽程式設定 (對於符合選取器集合中之條件的接聽程式)。

### 範例6：取得符合遠端電腦上準則的接聽程式設定

```
PS C:\> Get-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{Address="*";Transport="http"} -ComputerName "Server01"
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 80
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {100.0.0.1, 123.123.123.124, ::1, 2001:4898:0:fff:0:5efe:123.123.123.124...}
```

此命令會列出遠端 server01 電腦上的 WS-Management 接聽程式設定 (對於符合選取器集合中之條件的接聽程式)。

### 範例7：取得與指定實例相關的相關聯實例

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
xsi                       : http://www.w3.org/2001/XMLSchema-instance
p                         : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_ComputerSystem
cim                       : http://schemas.dmtf.org/wbem/wscim/1/common
type                      : p:Win32_ComputerSystem_Type
lang                      : en-US
AdminPasswordStatus       : 1
AutomaticManagedPagefile  : true
AutomaticResetBootOption  : true
AutomaticResetCapability  : true
BootOptionOnLimit         : BootOptionOnLimit
BootOptionOnWatchDog      : BootOptionOnWatchDog
BootROMSupported          : true
BootupState               : Normal boot
Caption                   : SERVER01
ChassisBootupState        : 3
CreationClassName         : Win32_ComputerSystem
CurrentTimeZone           : -480
DaylightInEffect          : false
Description               : AT/AT COMPATIBLE
DNSHostName               : server01
Domain                    : site01.corp.fabrikam.com
DomainRole                : 1
EnableDaylightSavingsTime : true
FrontPanelResetStatus     : 2
InfraredSupported         : false
InstallDate               : InstallDate
KeyboardPasswordStatus    : 2
LastLoadInfo              : LastLoadInfo
Manufacturer              : Dell Inc.
Model                     : OptiPlex 745
Name                      : SERVER01
NameFormat                : NameFormat
NetworkServerModeEnabled  : true
NumberOfLogicalProcessors : 2
NumberOfProcessors        : 1
OEMStringArray            : www.dell.com
PartOfDomain              : true
PauseAfterReset           : -1
PCSystemType              : 5
PowerManagementSupported  : PowerManagementSupported
PowerOnPasswordStatus     : 1
PowerState                : 0
PowerSupplyState          : 3
PrimaryOwnerContact       : PrimaryOwnerContact
PrimaryOwnerName          : testuser01
ResetCapability           : 1
ResetCount                : -1
ResetLimit                : -1
Roles                     : {LM_Workstation, LM_Server, SQLServer, NT}
Status                    : OK
SystemStartupDelay        : SystemStartupDelay
SystemStartupSetting      : SystemStartupSetting
SystemType                : X86-based PC
ThermalState              : 3
TotalPhysicalMemory       : 3217760256
UserName                  : FABRIKAM\testuser01
WakeUpType                : 6
Workgroup                 : Workgroup
xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_Service_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : false
Caption                 : Remote Procedure Call (RPC)
CheckPoint              : 0
CreationClassName       : Win32_Service
Description             : Serves as the endpoint mapper and COM Service Control Manager. If this service is stopped
or disabled, programs using COM or Remote Procedure Call (RPC) services will not function
properly.
DesktopInteract         : false
DisplayName             : Remote Procedure Call (RPC)
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : RpcSs
PathName                : C:\Windows\system32\svchost.exe -k rpcss
ProcessId               : 1100
ServiceSpecificExitCode : 0
ServiceType             : Share Process
Started                 : true
StartMode               : Auto
StartName               : NT AUTHORITY\NetworkService
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
WaitHint                : 0

xsi                     : http://www.w3.org/2001/XMLSchema-instance
p                       : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_SystemDriver
cim                     : http://schemas.dmtf.org/wbem/wscim/1/common
type                    : p:Win32_SystemDriver_Type
lang                    : en-US
AcceptPause             : false
AcceptStop              : true
Caption                 : HTTP
CreationClassName       : Win32_SystemDriver
Description             : HTTP
DesktopInteract         : false
DisplayName             : HTTP
ErrorControl            : Normal
ExitCode                : 0
InstallDate             : InstallDate
Name                    : HTTP
PathName                : C:\Windows\system32\drivers\HTTP.sys
ServiceSpecificExitCode : 0
ServiceType             : Kernel Driver
Started                 : true
StartMode               : Manual
StartName               :
State                   : Running
Status                  : OK
SystemCreationClassName : Win32_ComputerSystem
SystemName              : SERVER01
TagId                   : 0
```

此命令會取得與所指定執行個體 (winrm) 相關的關聯的執行個體 (associated instance)。

您必須將篩選條件括在引號內，如範例所示。

### 範例8：取得與指定實例相關的關聯實例

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Associations -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
```

此命令會取得與所指定執行個體 (winrm) 相關的關聯執行個體 (association instance)。
因為 *方言* 值為 association 且使用 *association* 參數，所以此命令會傳回關聯實例，而非關聯的實例。

您必須將篩選條件括在引號內，如範例所示。

## PARAMETERS

### -ApplicationName
指定連線中的應用程式名稱。
*ApplicationName* 參數的預設值是 WSMAN。
遠端端點的完整識別碼使用下列格式：

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

例如：`http://server01:8080/WSMAN`

裝載工作階段的網際網路資訊服務 (IIS)，會使用此端點轉送要求至指定的應用程式。
此預設設定 WSMAN 適用於大部分用途。
如果有許多電腦與執行 PowerShell 的一部電腦建立遠端連線，則會使用此參數。
在此情況下，IIS 會裝載 WS-Management 以提高效率。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -關聯
指出此 Cmdlet 會取得關聯實例，而非關聯的實例。
只有當 *方言* 參數具有 [關聯] 的值時，您才能使用此參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication
指定用於伺服器的驗證機制。
此參數可接受的值為：

- 基本。
Basic 配置使用純文字方式將使用者名稱與密碼傳送至伺服器或 Proxy。
- 預設值：
使用 WS-Management 通訊協定實作的驗證方法。
這是預設值。
- 摘要。
Digest 為查問-回應配置，於查問中使用伺服器指定的資料字串。
- Kerberos。
用戶端電腦和伺服器使用 Kerberos 憑證相互驗證。
- Negotiate。
Negotiate 為查問-回應配置，會與伺服器或 Proxy 交涉以決定要用於驗證的配置。
例如，此參數值允許交涉，以決定要使用 Kerberos 通訊協定或 NTLM。
- CredSSP。
使用認證安全性支援提供者 (CredSSP) 驗證，讓使用者能夠委派認證。
此選項是針對下列命令所設計：命令在遠端電腦上執行，但是收集來自其他遠端電腦上的資料，或是在其他遠端電腦上執行其他命令。

注意：CredSSP 會將使用者認證從本機電腦委派給遠端電腦。
此做法會使得遠端作業的安全性風險變高。
若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -BasePropertiesOnly
指出此 Cmdlet 只會列舉屬於由 *ResourceURI* 參數所指定之基類一部分的屬性。
如果指定了 *淺層* 參數，這個參數就沒有任何作用。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases: UBPO, Base

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint
對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。
請輸入憑證的憑證指紋。

憑證將用於用戶端憑證式驗證。
這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。

若要取得憑證指紋，請使用 PowerShell Cert：磁片磁碟機中的 Get-Item 或 Get-ChildItem 命令。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName
指定要執行管理作業的電腦。
值可以是完整網域名稱、NetBIOS 名稱或 IP 位址。
使用本機電腦名稱、使用 localhost，或使用句點 (.) 來指定本機電腦。
預設值是本機電腦。
當遠端電腦與使用者位於不同網域，您必須使用完整網域名稱。
您可以使用管線將此參數的值傳送至 Cmdlet。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI
指定連線端點。
這個字串的格式如下所示：

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

下列字串是此參數的正確格式值：

`http://Server01:8080/WSMAN`

此 URI 必須是完整的 URI。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
指定具有執行此動作權限的使用者帳戶。
預設為目前使用者。
輸入使用者名稱，例如 User01、Domain01\User01 或 User@Domain.com 。
或者，輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 所傳回的物件。
當您輸入使用者名稱時，此 Cmdlet 會提示您輸入密碼。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Dialect
指定要在篩選述詞中使用的方言。
這可以是遠端服務支援的任何方言。
下列別名可用於方言 URI：

- WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`
- 選擇 `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`
- 協會 `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -列舉
指出此 Cmdlet 會傳回管理資源的所有實例。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter
指定列舉的篩選運算式。
如果您指定此參數，您也必須指定 *方言* 。

此參數的有效值取決於 *方言* 中指定的方言。
例如，如果 *方言* 為 WQL，則 *Filter* 參數必須包含字串，且該字串必須包含有效的 WQL 查詢，例如下列查詢：

`"Select * from Win32_Service where State != Running"`

如果 *方言* 是關聯的，則 *篩選準則* 必須包含字串，且該字串必須包含有效的篩選，例如下列篩選：

`-filter:Object=EPR\[;AssociationClassName=AssocClassName\]\[;ResultClassName=ClassName\]\[;Role=RefPropertyName\]\[;ResultRole=RefPropertyName\]}`

```yaml
Type: System.String
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fragment
指定要針對所指定操作在執行個體中更新或抓取的區段。
例如，若要取得多工緩衝處理器服務的狀態，請指定下列各項：

`-Fragment Status`

```yaml
Type: System.String
Parameter Sets: GetInstance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OptionSet
對服務指定一組切換參數，以修改或精簡要求的本質。
這些切換參數類似於命令列殼層中使用的切換參數，因為都是服務特定的切換參數。
您可以指定任意數目的選項。

下列範例示範的語法可傳遞 a、b 與 c 參數的值 1、2 與 3：

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: OS

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Port
指定用戶端連線 WinRM 服務時所使用的連接埠。
傳輸為 HTTP 時，預設連接埠為 80。
傳輸為 HTTPS 時，預設連接埠為 443。

當您使用 HTTPS 做為傳輸時， *ComputerName* 參數的值必須符合伺服器的憑證一般名稱 (CN) 。
不過，如果 *SkipCNCheck* 參數指定為 *SessionOption* 參數的一部分，則伺服器憑證一般名稱不必符合伺服器主機名稱。
*SkipCNCheck* 參數只能用於信任的電腦。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceURI
指定資源類別或實例的 URI。
URI 會識別電腦上特定類型的資源，例如磁片或處理常式。

URI 是由前置詞與資源路徑所組成。
例如：

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: RURI

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ReturnType
指定要傳回的資料類型。
此參數可接受的值為：

- Object
- EPR
- ObjectAndEPR

預設值為 Object。

如果您指定 Object 或未指定此參數，這個 Cmdlet 只會傳回物件。
如果您指定 (EPR 的端點參考) 這個 Cmdlet 只會傳回物件的端點參考。
端點參照包含資源 URI 與執行個體之選取器的相關資訊。
如果您指定 ObjectAndEPR，此 Cmdlet 會傳回物件及其相關聯的端點參考。

```yaml
Type: System.String
Parameter Sets: Enumerate
Aliases: RT
Accepted values: object, epr, objectandepr

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SelectorSet
指定一組值組，用來選取特定管理資源執行個體。
當有一個以上的資源實例存在時，就會使用 *SelectorSet* 參數。
*SelectorSet* 參數的值必須是雜湊表。

下列範例顯示如何輸入此參數的值：

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: GetInstance
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption
指定 WS-Management 工作階段的擴充選項。
輸入您使用 New-WSManSessionOption Cmdlet 建立的 **SessionOption** 物件。
如需可用選項的詳細資訊，請輸入 `Get-Help New-WSManSessionOption`。

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: SO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -淺層
指出此 Cmdlet 只會傳回資源 URI 中所指定之基類的實例。
如果您未指定這個參數，此 Cmdlet 會傳回 URI 中所指定之基類的實例，以及其所有衍生類別的實例。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Enumerate
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL
指定使用安全通訊端層 (SSL) 通訊協定來建立遠端電腦連線。
預設不會使用 SSL。

WS-Management 會加密透過網路傳輸的所有 PowerShell 內容。
*UseSSL* 參數可讓您指定 HTTPS （而非 HTTP）的額外保護。
若用於連線的連接埠上無法使用 SSL，且您指定此參數，則命令會失敗。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SSL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無
此命令不接受任何輸入。

## 輸出

### System.Xml.XmlElement
此 Cmdlet 會產生 **XMLElement** 物件。

## 注意

## 相關連結

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
