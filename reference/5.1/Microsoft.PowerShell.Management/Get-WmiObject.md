---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WmiObject
ms.openlocfilehash: ed759ff3d0dd35cd55f9dac5a2d76e36eac4dc6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203983"
---
# Get-WmiObject

## 概要
取得 Windows Management Instrumentation (WMI) 類別的執行個體，或可用類別的相關資訊。

## SYNTAX

### 查詢 (預設) 

```
Get-WmiObject [-Class] <String> [[-Property] <String[]>] [-Filter <String>] [-Amended] [-DirectRead]
 [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### list

```
Get-WmiObject [[-Class] <String>] [-Recurse] [-Amended] [-List] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### WQLQuery

```
Get-WmiObject [-Amended] [-DirectRead] -Query <String> [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### Class - 類別

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### path

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

## DESCRIPTION

從 PowerShell 3.0 開始，此 Cmdlet 已被取代 `Get-CimInstance` 。

`Get-WmiObject`Cmdlet 會取得 wmi 類別的實例或可用 wmi 類別的相關資訊。 若要指定遠端電腦，請使用 **ComputerName** 參數。 若指定 **List** 參數，此 Cmdlet 會取得在指定命名空間內可用的 WMI 類別相關資訊。 若指定 **Query** 參數，此 Cmdlet 會執行 WMI 查詢語言 (WQL) 陳述式。

`Get-WmiObject`Cmdlet 不會使用 Windows PowerShell 遠端執行遠端作業。
您可以使用 Cmdlet 的 **ComputerName** 參數， `Get-WmiObject` 即使您的電腦不符合 Windows PowerShell 遠端處理的需求或未在 Windows PowerShell 中設定遠端功能。

從 Windows PowerShell 3.0 開始，傳回之物件的 **__Server** 屬性會 `Get-WmiObject` 有 **PSComputerName** 的別名。 這樣比較容易在輸出和報告中包含來源電腦名稱。

## 範例

### 範例1：取得本機電腦上的處理常式

這個範例會取得本機電腦上的處理常式。

```powershell
Get-WmiObject -Class Win32_Process
```

### 範例2：取得遠端電腦上的服務

此範例會取得遠端電腦上的服務。 **ComputerName** 參數指定遠端電腦的 IP 位址。 根據預設，目前的使用者帳戶必須是遠端電腦上 **Administrators** 群組的成員。

```powershell
Get-WmiObject -Class Win32_Service -ComputerName 10.1.4.62
```

### 範例3：取得本機電腦的根或預設命名空間中的 WMI 類別

這個範例會取得本機電腦的根或預設命名空間中的 WMI 類別。

```powershell
Get-WmiObject -Namespace "root/default" -List
```

### 範例4：在多部電腦上取得命名服務

這個範例會取得 **ComputerName** 參數值所指定電腦上的 WinRM 服務。

```powershell
Get-WmiObject -Query "select * from win32_service where name='WinRM'" -ComputerName Server01, Server02 |
  Format-List -Property PSComputerName, Name, ExitCode, Name, ProcessID, StartMode, State, Status
```

```Output
PSComputerName : SERVER01
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 844
StartMode      : Auto
State          : Running
Status         : OK

PSComputerName : SERVER02
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 932
StartMode      : Auto
State          : Running
Status         : OK
```

管線運算子 (|) 將輸出傳送至 `Format-List` Cmdlet，此 Cmdlet 會將 **PSComputerName** 屬性新增至預設輸出。 **PSComputerName** 是傳回之物件的 **__Server** 屬性的別名 `Get-WmiObject` 。 此別名是在 PowerShell 3.0 中引進。

### 範例5：停止遠端電腦上的服務

此範例會停止遠端電腦上的 WinRM 服務。 `Get-WmiObject` 取得 Server01 上 WinRM 服務物件的實例。 然後，它會在該物件上叫用 **Win32_Service** WMI 類別的 **StopService** 方法。

```powershell
(Get-WmiObject -Class Win32_Service -Filter "name='WinRM'" -ComputerName Server01).StopService()
```

這相當於使用 `Stop-Service` Cmdlet。

### 範例6：取得本機電腦上的 BIOS

此範例會從本機電腦取得 BIOS 資訊。 Cmdlet 的 **Property** 參數 `Format-List` 是用來顯示清單中傳回之物件的所有屬性。 依預設，只 `Types.ps1xml` 會顯示設定檔中定義的屬性子集。

```powershell
Get-WmiObject -Class Win32_Bios | Format-List -Property *
```

```Output
Status                : OK
Name                  : Phoenix ROM BIOS PLUS Version 1.10 A05
Caption               : Phoenix ROM BIOS PLUS Version 1.10 A05
SMBIOSPresent         : True
__GENUS               : 2
__CLASS               : Win32_BIOS
__SUPERCLASS          : CIM_BIOSElement
__DYNASTY             : CIM_ManagedSystemElement
__RELPATH             : Win32_BIOS.Name="Phoenix ROM BIOS PLUS Version 1.10
__PROPERTY_COUNT      : 27
__DERIVATION          : {CIM_BIOSElement, CIM_SoftwareElement, CIM_LogicalElement,
__SERVER              : Server01
__NAMESPACE           : root\cimv2
__PATH                : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
BiosCharacteristics   : {7, 9, 10, 11...}
BIOSVersion           : {DELL   - 15, Phoenix ROM BIOS PLUS Version 1.10 A05}
BuildNumber           :
CodeSet               :
CurrentLanguage       : en|US|iso8859-1
Description           : Phoenix ROM BIOS PLUS Version 1.10 A05
IdentificationCode    :
InstallableLanguages  : 1
InstallDate           :
LanguageEdition       :
ListOfLanguages       : {en|US|iso8859-1}
Manufacturer          : Dell Inc.
OtherTargetOS         :
PrimaryBIOS           : True
ReleaseDate           : 20101103000000.000000+000
SerialNumber          : 8VDM9P1
SMBIOSBIOSVersion     : A05
SMBIOSMajorVersion    : 2
SMBIOSMinorVersion    : 6
SoftwareElementID     : Phoenix ROM BIOS PLUS Version 1.10 A05
SoftwareElementState  : 3
TargetOperatingSystem : 0
Version               : DELL   - 15
Scope                 : System.Management.ManagementScope
Path                  : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
Options               : System.Management.ObjectGetOptions
ClassPath             : \\JUNE-PC\root\cimv2:Win32_BIOS
Properties            : {BiosCharacteristics, BIOSVersion, BuildNumber, Caption...}
SystemProperties      : {__GENUS, __CLASS, __SUPERCLASS, __DYNASTY...}
Qualifiers            : {dynamic, Locale, provider, UUID}
Site                  :
Container             :
```

### 範例7：取得遠端電腦上的服務

此範例會使用 Cmdlet 的 **Credential** 參數 `Get-WmiObject` 來取得遠端電腦上的服務。 **Credential** 參數的值是使用者帳戶的名稱。 使用者會被提示輸入密碼。

```powershell
Get-WmiObject Win32_Service -Credential FABRIKAM\administrator -ComputerName Fabrikam
```

> [!NOTE]
> 以本機電腦為目標時，無法使用認證。

## PARAMETERS

### -已修改

取得或設定一個值，該值會指示從 WMI 傳回的物件是否該包含修改過的資訊。 一般而言，修改的資訊是可當地語系化的資訊，例如附加至 WMI 物件的物件和屬性描述。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

以背景工作方式執行命令。 使用此參數執行需要很長時間才能完成的命令。

使用 **AsJob** 參數時，此命令會傳回代表背景工作的物件，然後顯示命令提示字元。 工作完成後，您可以繼續在工作階段中工作。 如果 `Get-WmiObject` 在遠端電腦上使用，則會在本機電腦上建立工作，而來自遠端電腦的結果則會自動傳回到本機電腦。 若要管理工作，請使用包含 Job Cmdlet 的 Cmdlet。 若要取得工作結果，請使用 `Receive-Job` Cmdlet。

> [!NOTE]
> 若要將這個參數與遠端電腦搭配使用，則本機電腦和遠端電腦必須針對遠端執行功能做設定。 此外，您必須使用 Windows Vista 和更新版之 Windows 中的 [以系統管理員身分執行] 選項來啟動 Windows PowerShell。 如需詳細資訊，請參閱[about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md)。

如需 Windows PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) 和 [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication

指定要與 WMI 連線搭配使用的驗證等級。
有效值為：

- -1：Unchanged
- 0：Default
- 1：None (不執行驗證。)
- 2：Connect (只有當用戶端與應用程式建立關係時，才執行驗證。)
- 3：Call (只有在每次呼叫的開始並當應用程式接收要求時，才執行驗證。)
- 4：Packet (在從用戶端接收的所有資料上執行驗證。)
- 5： PacketIntegrity (在用戶端和應用程式之間傳送的所有資料都會經過驗證和驗證。 ) 
- 6：PacketPrivacy (使用其他驗證等級的屬性，並加密所有資料。)

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authority

指定用來驗證 WMI 連線的授權單位。 您可以指定標準 NTLM 或 Kerberos 驗證。 若要使用 NTLM，請將授權單位設定為 `ntlmdomain:<DomainName>` ，其中會 `<DomainName>` 識別有效的 NTLM 功能變數名稱。 若要使用 Kerberos，請指定 `kerberos:<DomainName>\<ServerName>` 。 當您連線到本機電腦時，不能包含授權單位設定。

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

### -Class

指定 WMI 類別的名稱。 使用此參數時，Cmdlet 會抓取 WMI 類別的執行個體。

```yaml
Type: System.String
Parameter Sets: query, list
Aliases: ClassName

Required: True (query), False (list)
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定管理操作的目標電腦。 輸入 (FQDN) 、NetBIOS 名稱或 IP 位址的完整功能變數名稱。 當遠端電腦與本機電腦位於不同網域，則必須使用完整網域名稱。

預設是本機電腦。 若要指定本機電腦 (例如在一份電腦名稱清單中)，請使用 "localhost"、本機電腦名稱或句點 (.)。

此參數不必依賴使用 WS-Management 的 Windows PowerShell 遠端功能。 **ComputerName** `Get-WmiObject` 即使您的電腦未設定為執行遠端命令 WS-Management，您也可以使用 ComputerName 參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。 預設為目前使用者。 輸入使用者名稱，例如 "User01"、"Domain01\User01" 或 User@Contoso.com 。 或者，輸入 **PSCredential** 物件，例如 Cmdlet 所傳回的物件 `Get-Credential` 。 當您輸入使用者名稱時，會提示您輸入密碼。 以本機電腦為目標時，無法使用認證。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DirectRead

指定是否不論其基底類別或衍生類別，都針對指定類別要求直接存取 WMI 提供者。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: query, WQLQuery
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges

在命令進行 WMI 呼叫之前，先啟用目前使用者的所有權限。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

指定 **Where** 子句做為篩選。 使用 WMI 查詢語言 (WQL) 的語法。

> [!IMPORTANT]
> 不要在參數值中包含 **Where** 關鍵字。 例如，下列命令只會傳回具有 'c:' **DeviceID** 的邏輯磁碟，以及具有名稱 'WinRM' 且沒有使用 **Where** 關鍵字的服務。

`Get-WmiObject Win32_LogicalDisk -filter "DeviceID = 'c:' "`

`Get-WmiObject win32_service -filter "name='WinRM'"`

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Impersonation

指定要使用的模擬等級。

此參數可接受的值為：

- 0：預設值。 讀取本機登錄以取得預設的模擬層級。 預設值通常會設定為 [模擬 **]。**
- 1： Anonymous。 隱藏呼叫端的認證。
- 2：識別。 允許物件查詢呼叫端的認證。
- 3：模擬。 允許物件使用呼叫端的認證。
- 4：委派。 允許物件許可其他物件使用呼叫端的認證。

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -List

取得 WMI 存放庫命名空間 (由 **Namespace** 參數指定) 中 WMI 類別的名稱。

如果您指定 **List** 參數，而不是 **命名空間** 參數，則 `Get-WmiObject` 預設會使用 **Root\Cimv2** 命名空間。 此 Cmdlet 不會使用登錄機碼中的 **預設命名空間** 登錄專案 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` 來決定預設的命名空間。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Locale

指定 WMI 物件的慣用地區設定。
輸入 MS_\<LCID\> 格式的值。

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

### -Namespace

搭配 **Class** 參數使用時， **Namespace** 參數會指定 WMI 存放庫命名空間 (指定的 WMI 類別所在)。 搭配 **List** 參數使用時，它會指定收集 WMI 類別資訊的命名空間。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Property

指定此 Cmdlet 從中取得資訊的 WMI 類別屬性。 輸入屬性名稱。

```yaml
Type: System.String[]
Parameter Sets: query
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query

執行指定的 WMI 查詢語言 (WQL) 陳述式。 這個參數不支援事件查詢。

```yaml
Type: System.String
Parameter Sets: WQLQuery
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Recurse

在目前的命名空間及所有其他命名空間，搜尋 **Class** 參數所指定的類別名稱。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定 WMI 作業能同時執行的數目上限。 只有當命令中使用 **AsJob** 參數時，此參數才有效。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法透過管道傳送輸入 `Get-WmiObject` 。

## 輸出

### PSObject 或 System.management.automation.remotingjob。

使用 **AsJob** 參數時，此 Cmdlet 會傳回工作物件。 否則，傳回的物件 `Get-WmiObject` 取決於 **類別** 參數的值。

## 注意

若要在遠端電腦存取 WMI 資訊，執行 Cmdlet 的帳戶必須是遠端電腦上本機 Administrators 群組的成員。 或者，可以變更遠端存放庫的 WMI 命名空間上的預設存取控制，來授與其他帳戶存取權限。

預設只會顯示 WMI 類別的某些屬性。 每個 WMI 類別會顯示的屬性集指定於 Types.ps1xml 設定檔中。 若要取得 WMI 物件的所有屬性，請使用 `Get-Member` 或 `Format-List` Cmdlet。

## 相關連結

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Remove-WmiObject](Remove-WmiObject.md)

[Set-WmiInstance](Set-WmiInstance.md)

[Get-WSManInstance](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[Invoke-WSManAction](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[New-WSManInstance](../Microsoft.WsMan.Management/New-WSManInstance.md)

[Remove-WSManInstance](../Microsoft.WsMan.Management/Remove-WSManInstance.md)
