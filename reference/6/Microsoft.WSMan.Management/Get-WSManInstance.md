---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmaninstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManInstance
ms.openlocfilehash: 8eeb050b67d25f428612f42bfec253a78907cce6
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205580"
---
# <span data-ttu-id="0ff6d-103">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="0ff6d-103">Get-WSManInstance</span></span>

## <span data-ttu-id="0ff6d-104">概要</span><span class="sxs-lookup"><span data-stu-id="0ff6d-104">SYNOPSIS</span></span>
<span data-ttu-id="0ff6d-105">顯示由資源 URI 所指定之資源執行個體的管理資訊。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-105">Displays management information for a resource instance specified by a Resource URI.</span></span>

## <span data-ttu-id="0ff6d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0ff6d-106">SYNTAX</span></span>

### <span data-ttu-id="0ff6d-107">GetInstance (預設) </span><span class="sxs-lookup"><span data-stu-id="0ff6d-107">GetInstance (Default)</span></span>

```
Get-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-ConnectionURI <Uri>] [-Dialect <Uri>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet <Hashtable>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="0ff6d-108">列舉</span><span class="sxs-lookup"><span data-stu-id="0ff6d-108">Enumerate</span></span>

```
Get-WSManInstance [-ApplicationName <String>] [-BasePropertiesOnly] [-ComputerName <String>]
 [-ConnectionURI <Uri>] [-Dialect <Uri>] [-Enumerate] [-Filter <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-Associations] [-ResourceURI] <Uri> [-ReturnType <String>] [-SessionOption <SessionOption>]
 [-Shallow] [-UseSSL] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## <span data-ttu-id="0ff6d-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0ff6d-109">DESCRIPTION</span></span>
<span data-ttu-id="0ff6d-110">**Set-wsmaninstance** 指令程式會抓取資源統一資源識別元所指定的管理資源實例， (URI) 。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-110">The **Get-WSManInstance** cmdlet retrieves an instance of a management resource that is specified by a resource Uniform Resource Identifier (URI).</span></span>
<span data-ttu-id="0ff6d-111">抓取的資訊可能是複雜的 XML 資訊集，也就是物件或簡單的值。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-111">The information that is retrieved can be a complex XML information set, which is an object, or a simple value.</span></span>
<span data-ttu-id="0ff6d-112">此 Cmdlet 等同于管理 (WS-MANAGEMENT) **Get** 命令的標準 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-112">This cmdlet is the equivalent to the standard Web Services for Management (WS-Management) **Get** command.</span></span>

<span data-ttu-id="0ff6d-113">此 Cmdlet 使用 WS-Management 連線/傳輸層來抓取資訊。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-113">This cmdlet uses the WS-Management connection/transport layer to retrieve information.</span></span>

## <span data-ttu-id="0ff6d-114">範例</span><span class="sxs-lookup"><span data-stu-id="0ff6d-114">EXAMPLES</span></span>

### <span data-ttu-id="0ff6d-115">範例1：從 WMI 取得所有資訊</span><span class="sxs-lookup"><span data-stu-id="0ff6d-115">Example 1: Get all information from WMI</span></span>

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

<span data-ttu-id="0ff6d-116">此命令會傳回 Windows Management Instrumentation (WMI) 對遠端 server01 電腦上的 **WinRM** 服務公開的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-116">This command returns all of the information that Windows Management Instrumentation (WMI) exposes about the **WinRM** service on the remote server01 computer.</span></span>

### <span data-ttu-id="0ff6d-117">範例2：取得多工緩衝處理器服務的狀態</span><span class="sxs-lookup"><span data-stu-id="0ff6d-117">Example 2: Get the status of the Spooler service</span></span>

```
PS C:\> Get-WSManInstance -ResourceURI wmicimv2/win32_service -SelectorSet @{name="spooler"} -Fragment Status -ComputerName "Server01"
XmlFragment=OK
```

<span data-ttu-id="0ff6d-118">此命令只會傳回遠端 server01 電腦上之多工 **緩衝** 處理器服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-118">This command returns only the status of the **Spooler** service on the remote server01 computer.</span></span>

### <span data-ttu-id="0ff6d-119">範例3：取得所有服務的端點參考</span><span class="sxs-lookup"><span data-stu-id="0ff6d-119">Example 3: Get endpoint references for all services</span></span>

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

<span data-ttu-id="0ff6d-120">此命令會傳回對應到本機電腦上之所有服務的端點參照。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-120">This command returns endpoint references that correspond to all the services on the local computer.</span></span>

### <span data-ttu-id="0ff6d-121">範例4：取得符合指定準則的服務</span><span class="sxs-lookup"><span data-stu-id="0ff6d-121">Example 4: Get services that meet specified criteria</span></span>

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

<span data-ttu-id="0ff6d-122">此命令會列出遠端 Server01 電腦上符合下列條件的所有服務：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-122">This command lists all of the services that meet the following criteria on the remote Server01 computer:</span></span>

- <span data-ttu-id="0ff6d-123">服務的啟動類型為自動。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-123">The startup type of the service is Automatic.</span></span>
- <span data-ttu-id="0ff6d-124">服務已停止。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-124">The service is stopped.</span></span>

### <span data-ttu-id="0ff6d-125">範例5：取得與本機電腦上的條件相符的接聽程式設定</span><span class="sxs-lookup"><span data-stu-id="0ff6d-125">Example 5: Get listener configuration that matches criteria on the local computer</span></span>

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

<span data-ttu-id="0ff6d-126">此命令會列出本機電腦上的 WS-Management 接聽程式設定 (對於符合選取器集合中之條件的接聽程式)。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-126">This command lists the WS-Management listener configuration on the local computer for the listener that matches the criteria in the selector set.</span></span>

### <span data-ttu-id="0ff6d-127">範例6：取得符合遠端電腦上準則的接聽程式設定</span><span class="sxs-lookup"><span data-stu-id="0ff6d-127">Example 6: Get listener configuration that matches criteria on a remote computer</span></span>

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

<span data-ttu-id="0ff6d-128">此命令會列出遠端 server01 電腦上的 WS-Management 接聽程式設定 (對於符合選取器集合中之條件的接聽程式)。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-128">This command lists the WS-Management listener configuration on the remote server01 computer for the listener that matches the criteria in the selector set.</span></span>

### <span data-ttu-id="0ff6d-129">範例7：取得與指定實例相關的相關聯實例</span><span class="sxs-lookup"><span data-stu-id="0ff6d-129">Example 7: Get associated instances related to a specified instance</span></span>

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

<span data-ttu-id="0ff6d-130">此命令會取得與所指定執行個體 (winrm) 相關的關聯的執行個體 (associated instance)。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-130">This command gets the associated instances that are related to the specified instance (winrm).</span></span>

<span data-ttu-id="0ff6d-131">您必須將篩選條件括在引號內，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-131">You must enclose the filter in quotation marks, as shown in the example.</span></span>

### <span data-ttu-id="0ff6d-132">範例8：取得與指定實例相關的關聯實例</span><span class="sxs-lookup"><span data-stu-id="0ff6d-132">Example 8: Get association instances related to a specified instance</span></span>

```
PS C:\> Get-WSManInstance -Enumerate -Dialect Association -Associations -Filter "{Object=win32_service?name=winrm}" -ResourceURI wmicimv2/*
```

<span data-ttu-id="0ff6d-133">此命令會取得與所指定執行個體 (winrm) 相關的關聯執行個體 (association instance)。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-133">This command gets association instances that are related to the specified instance (winrm).</span></span>
<span data-ttu-id="0ff6d-134">因為 *方言* 值為 association 且使用 *association* 參數，所以此命令會傳回關聯實例，而非關聯的實例。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-134">Because the *Dialect* value is association and the *Associations* parameter is used, this command returns association instances, not associated instances.</span></span>

<span data-ttu-id="0ff6d-135">您必須將篩選條件括在引號內，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-135">You must enclose the filter in quotation marks, as shown in the example.</span></span>

## <span data-ttu-id="0ff6d-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0ff6d-136">PARAMETERS</span></span>

### <span data-ttu-id="0ff6d-137">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="0ff6d-137">-ApplicationName</span></span>
<span data-ttu-id="0ff6d-138">指定連線中的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-138">Specifies the application name in the connection.</span></span>
<span data-ttu-id="0ff6d-139">*ApplicationName* 參數的預設值是 WSMAN。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-139">The default value of the *ApplicationName* parameter is WSMAN.</span></span>
<span data-ttu-id="0ff6d-140">遠端端點的完整識別碼使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-140">The complete identifier for the remote endpoint is in the following format:</span></span>

<span data-ttu-id="0ff6d-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="0ff6d-141">\<transport\>://\<server\>:\<port\>/\<ApplicationName\></span></span>

<span data-ttu-id="0ff6d-142">例如：`http://server01:8080/WSMAN`</span><span class="sxs-lookup"><span data-stu-id="0ff6d-142">For example: `http://server01:8080/WSMAN`</span></span>

<span data-ttu-id="0ff6d-143">裝載工作階段的網際網路資訊服務 (IIS)，會使用此端點轉送要求至指定的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-143">Internet Information Services (IIS), which hosts the session, forwards requests with this endpoint to the specified application.</span></span>
<span data-ttu-id="0ff6d-144">此預設設定 WSMAN 適用於大部分用途。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-144">This default setting of WSMAN is appropriate for most uses.</span></span>
<span data-ttu-id="0ff6d-145">如果有許多電腦與執行 PowerShell 的一部電腦建立遠端連線，則會使用此參數。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-145">This parameter is designed to be used if many computers establish remote connections to one computer that is running PowerShell.</span></span>
<span data-ttu-id="0ff6d-146">在此情況下，IIS 會裝載 WS-Management 以提高效率。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-146">In this case, IIS hosts WS-Management for efficiency.</span></span>

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

### <span data-ttu-id="0ff6d-147">-關聯</span><span class="sxs-lookup"><span data-stu-id="0ff6d-147">-Associations</span></span>
<span data-ttu-id="0ff6d-148">指出此 Cmdlet 會取得關聯實例，而非關聯的實例。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-148">Indicates that this cmdlet gets association instances, not associated instances.</span></span>
<span data-ttu-id="0ff6d-149">只有當 *方言* 參數具有 [關聯] 的值時，您才能使用此參數。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-149">You can use this parameter only when the *Dialect* parameter has a value of Association.</span></span>

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

### <span data-ttu-id="0ff6d-150">-Authentication</span><span class="sxs-lookup"><span data-stu-id="0ff6d-150">-Authentication</span></span>
<span data-ttu-id="0ff6d-151">指定用於伺服器的驗證機制。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-151">Specifies the authentication mechanism to be used at the server.</span></span>
<span data-ttu-id="0ff6d-152">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-152">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0ff6d-153">基本。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-153">Basic.</span></span>
<span data-ttu-id="0ff6d-154">Basic 配置使用純文字方式將使用者名稱與密碼傳送至伺服器或 Proxy。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-154">Basic is a scheme in which the user name and password are sent in clear text to the server or proxy.</span></span>
- <span data-ttu-id="0ff6d-155">預設值：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-155">Default.</span></span>
<span data-ttu-id="0ff6d-156">使用 WS-Management 通訊協定實作的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-156">Use the authentication method implemented by the WS-Management protocol.</span></span>
<span data-ttu-id="0ff6d-157">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-157">This is the default.</span></span>
- <span data-ttu-id="0ff6d-158">摘要。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-158">Digest.</span></span>
<span data-ttu-id="0ff6d-159">Digest 為查問-回應配置，於查問中使用伺服器指定的資料字串。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-159">Digest is a challenge-response scheme that uses a server-specified data string for the challenge.</span></span>
- <span data-ttu-id="0ff6d-160">Kerberos。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-160">Kerberos.</span></span>
<span data-ttu-id="0ff6d-161">用戶端電腦和伺服器使用 Kerberos 憑證相互驗證。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-161">The client computer and the server mutually authenticate by using Kerberos certificates.</span></span>
- <span data-ttu-id="0ff6d-162">Negotiate。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-162">Negotiate.</span></span>
<span data-ttu-id="0ff6d-163">Negotiate 為查問-回應配置，會與伺服器或 Proxy 交涉以決定要用於驗證的配置。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-163">Negotiate is a challenge-response scheme that negotiates with the server or proxy to determine the scheme to use for authentication.</span></span>
<span data-ttu-id="0ff6d-164">例如，此參數值允許交涉，以決定要使用 Kerberos 通訊協定或 NTLM。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-164">For example, this parameter value allows for negotiation to determine whether the Kerberos protocol or NTLM is used.</span></span>
- <span data-ttu-id="0ff6d-165">CredSSP。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-165">CredSSP.</span></span>
<span data-ttu-id="0ff6d-166">使用認證安全性支援提供者 (CredSSP) 驗證，讓使用者能夠委派認證。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-166">Use Credential Security Support Provider (CredSSP) authentication, which lets the user delegate credentials.</span></span>
<span data-ttu-id="0ff6d-167">此選項是針對下列命令所設計：命令在遠端電腦上執行，但是收集來自其他遠端電腦上的資料，或是在其他遠端電腦上執行其他命令。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-167">This option is designed for commands that run on one remote computer but collect data from or run additional commands on other remote computers.</span></span>

<span data-ttu-id="0ff6d-168">注意：CredSSP 會將使用者認證從本機電腦委派給遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-168">Caution: CredSSP delegates the user credentials from the local computer to a remote computer.</span></span>
<span data-ttu-id="0ff6d-169">此做法會使得遠端作業的安全性風險變高。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-169">This practice increases the security risk of the remote operation.</span></span>
<span data-ttu-id="0ff6d-170">若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-170">If the remote computer is compromised, when credentials are passed to it, the credentials can be used to control the network session.</span></span>

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

### <span data-ttu-id="0ff6d-171">-BasePropertiesOnly</span><span class="sxs-lookup"><span data-stu-id="0ff6d-171">-BasePropertiesOnly</span></span>
<span data-ttu-id="0ff6d-172">指出此 Cmdlet 只會列舉屬於由 *ResourceURI* 參數所指定之基類一部分的屬性。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-172">Indicates that this cmdlet enumerates only the properties that are part of the base class that is specified by the *ResourceURI* parameter.</span></span>
<span data-ttu-id="0ff6d-173">如果指定了 *淺層* 參數，這個參數就沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-173">This parameter has no effect if the *Shallow* parameter is specified.</span></span>

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

### <span data-ttu-id="0ff6d-174">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="0ff6d-174">-CertificateThumbprint</span></span>
<span data-ttu-id="0ff6d-175">對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-175">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span>
<span data-ttu-id="0ff6d-176">請輸入憑證的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-176">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="0ff6d-177">憑證將用於用戶端憑證式驗證。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-177">Certificates are used in client certificate-based authentication.</span></span>
<span data-ttu-id="0ff6d-178">這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-178">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="0ff6d-179">若要取得憑證指紋，請使用 PowerShell Cert：磁片磁碟機中的 Get-Item 或 Get-ChildItem 命令。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-179">To get a certificate thumbprint, use the Get-Item or Get-ChildItem command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="0ff6d-180">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="0ff6d-180">-ComputerName</span></span>
<span data-ttu-id="0ff6d-181">指定要執行管理作業的電腦。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-181">Specifies the computer against which to run the management operation.</span></span>
<span data-ttu-id="0ff6d-182">值可以是完整網域名稱、NetBIOS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-182">The value can be a fully qualified domain name, a NetBIOS name, or an IP address.</span></span>
<span data-ttu-id="0ff6d-183">使用本機電腦名稱、使用 localhost，或使用句點 (.) 來指定本機電腦。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-183">Use the local computer name, use localhost, or use a dot (.) to specify the local computer.</span></span>
<span data-ttu-id="0ff6d-184">預設值是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-184">The local computer is the default.</span></span>
<span data-ttu-id="0ff6d-185">當遠端電腦與使用者位於不同網域，您必須使用完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-185">When the remote computer is in a different domain from the user, you must use a fully qualified domain name must be used.</span></span>
<span data-ttu-id="0ff6d-186">您可以使用管線將此參數的值傳送至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-186">You can pipe a value for this parameter to the cmdlet.</span></span>

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

### <span data-ttu-id="0ff6d-187">-ConnectionURI</span><span class="sxs-lookup"><span data-stu-id="0ff6d-187">-ConnectionURI</span></span>
<span data-ttu-id="0ff6d-188">指定連線端點。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-188">Specifies the connection endpoint.</span></span>
<span data-ttu-id="0ff6d-189">這個字串的格式如下所示：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-189">The format of this string is as follows:</span></span>

<span data-ttu-id="0ff6d-190">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span><span class="sxs-lookup"><span data-stu-id="0ff6d-190">\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\></span></span>

<span data-ttu-id="0ff6d-191">下列字串是此參數的正確格式值：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-191">The following string is a correctly formatted value for this parameter:</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="0ff6d-192">此 URI 必須是完整的 URI。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-192">The URI must be fully qualified.</span></span>

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

### <span data-ttu-id="0ff6d-193">-Credential</span><span class="sxs-lookup"><span data-stu-id="0ff6d-193">-Credential</span></span>
<span data-ttu-id="0ff6d-194">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-194">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="0ff6d-195">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-195">The default is the current user.</span></span>
<span data-ttu-id="0ff6d-196">輸入使用者名稱，例如 User01、Domain01\User01 或 User@Domain.com 。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-196">Type a user name, such as User01, Domain01\User01, or User@Domain.com.</span></span>
<span data-ttu-id="0ff6d-197">或者，輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-197">Or, enter a **PSCredential** object, such as one returned by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="0ff6d-198">當您輸入使用者名稱時，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-198">When you type a user name, this cmdlet prompts you for a password.</span></span>

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

### <span data-ttu-id="0ff6d-199">-Dialect</span><span class="sxs-lookup"><span data-stu-id="0ff6d-199">-Dialect</span></span>
<span data-ttu-id="0ff6d-200">指定要在篩選述詞中使用的方言。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-200">Specifies the dialect to use in the filter predicate.</span></span>
<span data-ttu-id="0ff6d-201">這可以是遠端服務支援的任何方言。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-201">This can be any dialect that is supported by the remote service.</span></span>
<span data-ttu-id="0ff6d-202">下列別名可用於方言 URI：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-202">The following aliases can be used for the dialect URI:</span></span>

- <span data-ttu-id="0ff6d-203">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span><span class="sxs-lookup"><span data-stu-id="0ff6d-203">WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`</span></span>
- <span data-ttu-id="0ff6d-204">選擇 `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span><span class="sxs-lookup"><span data-stu-id="0ff6d-204">Selector `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`</span></span>
- <span data-ttu-id="0ff6d-205">協會 `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span><span class="sxs-lookup"><span data-stu-id="0ff6d-205">Association `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`</span></span>

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

### <span data-ttu-id="0ff6d-206">-列舉</span><span class="sxs-lookup"><span data-stu-id="0ff6d-206">-Enumerate</span></span>
<span data-ttu-id="0ff6d-207">指出此 Cmdlet 會傳回管理資源的所有實例。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-207">Indicates that this cmdlet returns all of the instances of a management resource.</span></span>

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

### <span data-ttu-id="0ff6d-208">-Filter</span><span class="sxs-lookup"><span data-stu-id="0ff6d-208">-Filter</span></span>
<span data-ttu-id="0ff6d-209">指定列舉的篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-209">Specifies the filter expression for the enumeration.</span></span>
<span data-ttu-id="0ff6d-210">如果您指定此參數，您也必須指定 *方言* 。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-210">If you specify this parameter, you must also specify *Dialect* .</span></span>

<span data-ttu-id="0ff6d-211">此參數的有效值取決於 *方言* 中指定的方言。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-211">The valid values of this parameter depend on the dialect that is specified in *Dialect* .</span></span>
<span data-ttu-id="0ff6d-212">例如，如果 *方言* 為 WQL，則 *Filter* 參數必須包含字串，且該字串必須包含有效的 WQL 查詢，例如下列查詢：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-212">For example, if *Dialect* is WQL, the *Filter* parameter must contain a string, and the string must contain a valid WQL query such as the following query:</span></span>

`"Select * from Win32_Service where State != Running"`

<span data-ttu-id="0ff6d-213">如果 *方言* 是關聯的，則 *篩選準則* 必須包含字串，且該字串必須包含有效的篩選，例如下列篩選：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-213">If *Dialect* is Association, *Filter* must contain a string, and the string must contain a valid filter, such as the following filter:</span></span>

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

### <span data-ttu-id="0ff6d-214">-Fragment</span><span class="sxs-lookup"><span data-stu-id="0ff6d-214">-Fragment</span></span>
<span data-ttu-id="0ff6d-215">指定要針對所指定操作在執行個體中更新或抓取的區段。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-215">Specifies a section inside the instance that is to be updated or retrieved for the specified operation.</span></span>
<span data-ttu-id="0ff6d-216">例如，若要取得多工緩衝處理器服務的狀態，請指定下列各項：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-216">For example, to get the status of a spooler service, specify the following:</span></span>

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

### <span data-ttu-id="0ff6d-217">-OptionSet</span><span class="sxs-lookup"><span data-stu-id="0ff6d-217">-OptionSet</span></span>
<span data-ttu-id="0ff6d-218">對服務指定一組切換參數，以修改或精簡要求的本質。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-218">Specifies a set of switches to a service to modify or refine the nature of the request.</span></span>
<span data-ttu-id="0ff6d-219">這些切換參數類似於命令列殼層中使用的切換參數，因為都是服務特定的切換參數。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-219">These resemble switches used in command-line shells because they are service specific.</span></span>
<span data-ttu-id="0ff6d-220">您可以指定任意數目的選項。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-220">Any number of options can be specified.</span></span>

<span data-ttu-id="0ff6d-221">下列範例示範的語法可傳遞 a、b 與 c 參數的值 1、2 與 3：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-221">The following example demonstrates the syntax that passes the values 1, 2, and 3 for the a, b, and c parameters:</span></span>

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

### <span data-ttu-id="0ff6d-222">-Port</span><span class="sxs-lookup"><span data-stu-id="0ff6d-222">-Port</span></span>
<span data-ttu-id="0ff6d-223">指定用戶端連線 WinRM 服務時所使用的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-223">Specifies the port to use when the client connects to the WinRM service.</span></span>
<span data-ttu-id="0ff6d-224">傳輸為 HTTP 時，預設連接埠為 80。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-224">When the transport is HTTP, the default port is 80.</span></span>
<span data-ttu-id="0ff6d-225">傳輸為 HTTPS 時，預設連接埠為 443。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-225">When the transport is HTTPS, the default port is 443.</span></span>

<span data-ttu-id="0ff6d-226">當您使用 HTTPS 做為傳輸時， *ComputerName* 參數的值必須符合伺服器的憑證一般名稱 (CN) 。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-226">When you use HTTPS as the transport, the value of the *ComputerName* parameter must match the server's certificate common name (CN).</span></span>
<span data-ttu-id="0ff6d-227">不過，如果 *SkipCNCheck* 參數指定為 *SessionOption* 參數的一部分，則伺服器憑證一般名稱不必符合伺服器主機名稱。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-227">However, if the *SkipCNCheck* parameter is specified as part of the *SessionOption* parameter, the certificate common name of the server does not have to match the host name of the server.</span></span>
<span data-ttu-id="0ff6d-228">*SkipCNCheck* 參數只能用於信任的電腦。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-228">The *SkipCNCheck* parameter should be used only for trusted computers.</span></span>

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

### <span data-ttu-id="0ff6d-229">-ResourceURI</span><span class="sxs-lookup"><span data-stu-id="0ff6d-229">-ResourceURI</span></span>
<span data-ttu-id="0ff6d-230">指定資源類別或實例的 URI。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-230">Specifies the URI of the resource class or instance.</span></span>
<span data-ttu-id="0ff6d-231">URI 會識別電腦上特定類型的資源，例如磁片或處理常式。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-231">The URI identifies a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="0ff6d-232">URI 是由前置詞與資源路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-232">A URI consists of a prefix and a path of a resource.</span></span>
<span data-ttu-id="0ff6d-233">例如：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-233">For example:</span></span>

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

### <span data-ttu-id="0ff6d-234">-ReturnType</span><span class="sxs-lookup"><span data-stu-id="0ff6d-234">-ReturnType</span></span>
<span data-ttu-id="0ff6d-235">指定要傳回的資料類型。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-235">Specifies the type of data to be returned.</span></span>
<span data-ttu-id="0ff6d-236">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-236">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0ff6d-237">Object</span><span class="sxs-lookup"><span data-stu-id="0ff6d-237">Object</span></span>
- <span data-ttu-id="0ff6d-238">EPR</span><span class="sxs-lookup"><span data-stu-id="0ff6d-238">EPR</span></span>
- <span data-ttu-id="0ff6d-239">ObjectAndEPR</span><span class="sxs-lookup"><span data-stu-id="0ff6d-239">ObjectAndEPR</span></span>

<span data-ttu-id="0ff6d-240">預設值為 Object。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-240">The default value is Object.</span></span>

<span data-ttu-id="0ff6d-241">如果您指定 Object 或未指定此參數，這個 Cmdlet 只會傳回物件。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-241">If you specify Object or do not specify this parameter, this cmdlet returns only objects.</span></span>
<span data-ttu-id="0ff6d-242">如果您指定 (EPR 的端點參考) 這個 Cmdlet 只會傳回物件的端點參考。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-242">If you specify endpoint reference (EPR) this cmdlet returns only the endpoint references of the objects.</span></span>
<span data-ttu-id="0ff6d-243">端點參照包含資源 URI 與執行個體之選取器的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-243">Endpoint references contain information about the resource URI and the selectors for the instance.</span></span>
<span data-ttu-id="0ff6d-244">如果您指定 ObjectAndEPR，此 Cmdlet 會傳回物件及其相關聯的端點參考。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-244">If you specify ObjectAndEPR, this cmdlet returns both the object and its associated endpoint references.</span></span>

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

### <span data-ttu-id="0ff6d-245">-SelectorSet</span><span class="sxs-lookup"><span data-stu-id="0ff6d-245">-SelectorSet</span></span>
<span data-ttu-id="0ff6d-246">指定一組值組，用來選取特定管理資源執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-246">Specifies a set of value pairs that are used to select particular management resource instances.</span></span>
<span data-ttu-id="0ff6d-247">當有一個以上的資源實例存在時，就會使用 *SelectorSet* 參數。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-247">The *SelectorSet* parameter is used when more than one instance of the resource exists.</span></span>
<span data-ttu-id="0ff6d-248">*SelectorSet* 參數的值必須是雜湊表。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-248">The value of the *SelectorSet* parameter must be a hash table.</span></span>

<span data-ttu-id="0ff6d-249">下列範例顯示如何輸入此參數的值：</span><span class="sxs-lookup"><span data-stu-id="0ff6d-249">The following example shows how to enter a value for this parameter:</span></span>

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

### <span data-ttu-id="0ff6d-250">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="0ff6d-250">-SessionOption</span></span>
<span data-ttu-id="0ff6d-251">指定 WS-Management 工作階段的擴充選項。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-251">Specifies extended options for the WS-Management session.</span></span>
<span data-ttu-id="0ff6d-252">輸入您使用 New-WSManSessionOption Cmdlet 建立的 **SessionOption** 物件。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-252">Enter a **SessionOption** object that you create by using the New-WSManSessionOption cmdlet.</span></span>
<span data-ttu-id="0ff6d-253">如需可用選項的詳細資訊，請輸入 `Get-Help New-WSManSessionOption`。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-253">For more information about the options that are available, type `Get-Help New-WSManSessionOption`.</span></span>

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

### <span data-ttu-id="0ff6d-254">-淺層</span><span class="sxs-lookup"><span data-stu-id="0ff6d-254">-Shallow</span></span>
<span data-ttu-id="0ff6d-255">指出此 Cmdlet 只會傳回資源 URI 中所指定之基類的實例。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-255">Indicates that this cmdlet returns only instances of the base class that is specified in the resource URI.</span></span>
<span data-ttu-id="0ff6d-256">如果您未指定這個參數，此 Cmdlet 會傳回 URI 中所指定之基類的實例，以及其所有衍生類別的實例。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-256">If you do not specify this parameter,, this cmdlet returns instances of the base class that is specified in the URI and in all its derived classes.</span></span>

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

### <span data-ttu-id="0ff6d-257">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="0ff6d-257">-UseSSL</span></span>
<span data-ttu-id="0ff6d-258">指定使用安全通訊端層 (SSL) 通訊協定來建立遠端電腦連線。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-258">Specifies that the Secure Sockets Layer (SSL) protocol is used to establish a connection to the remote computer.</span></span>
<span data-ttu-id="0ff6d-259">預設不會使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-259">By default, SSL is not used.</span></span>

<span data-ttu-id="0ff6d-260">WS-Management 會加密透過網路傳輸的所有 PowerShell 內容。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-260">WS-Management encrypts all the PowerShell content that is transmitted over the network.</span></span>
<span data-ttu-id="0ff6d-261">*UseSSL* 參數可讓您指定 HTTPS （而非 HTTP）的額外保護。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-261">The *UseSSL* parameter lets you specify the additional protection of HTTPS instead of HTTP.</span></span>
<span data-ttu-id="0ff6d-262">若用於連線的連接埠上無法使用 SSL，且您指定此參數，則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-262">If SSL is not available on the port that is used for the connection, and you specify this parameter, the command fails.</span></span>

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

### <span data-ttu-id="0ff6d-263">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0ff6d-263">CommonParameters</span></span>
<span data-ttu-id="0ff6d-264">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-264">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0ff6d-265">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-265">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0ff6d-266">輸入</span><span class="sxs-lookup"><span data-stu-id="0ff6d-266">INPUTS</span></span>

### <span data-ttu-id="0ff6d-267">無</span><span class="sxs-lookup"><span data-stu-id="0ff6d-267">None</span></span>
<span data-ttu-id="0ff6d-268">此命令不接受任何輸入。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-268">This command does not accept any input.</span></span>

## <span data-ttu-id="0ff6d-269">輸出</span><span class="sxs-lookup"><span data-stu-id="0ff6d-269">OUTPUTS</span></span>

### <span data-ttu-id="0ff6d-270">System.Xml.XmlElement</span><span class="sxs-lookup"><span data-stu-id="0ff6d-270">System.Xml.XmlElement</span></span>
<span data-ttu-id="0ff6d-271">此 Cmdlet 會產生 **XMLElement** 物件。</span><span class="sxs-lookup"><span data-stu-id="0ff6d-271">This cmdlet generates an **XMLElement** object.</span></span>

## <span data-ttu-id="0ff6d-272">注意</span><span class="sxs-lookup"><span data-stu-id="0ff6d-272">NOTES</span></span>

## <span data-ttu-id="0ff6d-273">相關連結</span><span class="sxs-lookup"><span data-stu-id="0ff6d-273">RELATED LINKS</span></span>

[<span data-ttu-id="0ff6d-274">Connect-WSMan</span><span class="sxs-lookup"><span data-stu-id="0ff6d-274">Connect-WSMan</span></span>](Connect-WSMan.md)

[<span data-ttu-id="0ff6d-275">Disable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="0ff6d-275">Disable-WSManCredSSP</span></span>](Disable-WSManCredSSP.md)

[<span data-ttu-id="0ff6d-276">Disconnect-WSMan</span><span class="sxs-lookup"><span data-stu-id="0ff6d-276">Disconnect-WSMan</span></span>](Disconnect-WSMan.md)

[<span data-ttu-id="0ff6d-277">Enable-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="0ff6d-277">Enable-WSManCredSSP</span></span>](Enable-WSManCredSSP.md)

[<span data-ttu-id="0ff6d-278">Get-WSManCredSSP</span><span class="sxs-lookup"><span data-stu-id="0ff6d-278">Get-WSManCredSSP</span></span>](Get-WSManCredSSP.md)

[<span data-ttu-id="0ff6d-279">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="0ff6d-279">Invoke-WSManAction</span></span>](Invoke-WSManAction.md)

[<span data-ttu-id="0ff6d-280">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="0ff6d-280">New-WSManInstance</span></span>](New-WSManInstance.md)

[<span data-ttu-id="0ff6d-281">New-WSManSessionOption</span><span class="sxs-lookup"><span data-stu-id="0ff6d-281">New-WSManSessionOption</span></span>](New-WSManSessionOption.md)

[<span data-ttu-id="0ff6d-282">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="0ff6d-282">Remove-WSManInstance</span></span>](Remove-WSManInstance.md)

[<span data-ttu-id="0ff6d-283">Set-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="0ff6d-283">Set-WSManInstance</span></span>](Set-WSManInstance.md)

[<span data-ttu-id="0ff6d-284">Set-WSManQuickConfig</span><span class="sxs-lookup"><span data-stu-id="0ff6d-284">Set-WSManQuickConfig</span></span>](Set-WSManQuickConfig.md)

[<span data-ttu-id="0ff6d-285">Test-WSMan</span><span class="sxs-lookup"><span data-stu-id="0ff6d-285">Test-WSMan</span></span>](Test-WSMan.md)
