---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-wmiinstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WmiInstance
ms.openlocfilehash: 03288a2ffbef416937b2c92a7d08a5aed49ffb43
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203492"
---
# Set-WmiInstance

## 概要
建立或更新現有 Windows Management Instrumentation (WMI) 類別的執行個體。

## SYNTAX

### class (預設值)

```
Set-WmiInstance [-Class] <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 物件 (object)

```
Set-WmiInstance -InputObject <ManagementObject> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### path

```
Set-WmiInstance -Path <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 查詢

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### list

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
`Set-WmiInstance`Cmdlet 會建立或更新現有 Windows Management Instrumentation (WMI) 類別的實例。
建立或更新的執行個體會寫入 WMI 存放庫中。

已導入 Windows PowerShell 3.0 的新 CIM Cmdlet 可執行與 WMI Cmdlet 相同的工作。
CIM Cmdlet 符合 WS-Management (WSMan) 標準，以及通用訊息模型 (CIM) standard。
這可讓 Cmdlet 使用相同的技術來管理 Windows 電腦和執行其他作業系統的電腦。
請 `Set-WmiInstance` 考慮使用 [CimInstance](/powershell/module/cimcmdlets/set-ciminstance) 或 [CimInstance](/powershell/module/cimcmdlets/new-ciminstance) Cmdlet，而不是使用。

## 範例

### 範例1：設定 WMI 記錄層級

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2}
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
```

這個命令會將 WMI 記錄層級設定為 2。
此命令會在引數參數中傳遞要設定的屬性，並將值一起視為值組。
此參數接受一個由 @{property = value} 建構所定義的雜湊表。
傳回的類別資訊會反映新的值。

### 範例2：建立環境變數及其值

```
PS C:\> Set-WmiInstance -Class win32_environment -Argument @{Name="testvar";VariableValue="testvalue";UserName="<SYSTEM>"}
__GENUS          : 2
__CLASS          : Win32_Environment
__SUPERCLASS     : CIM_SystemResource
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Environment.Name="testvar",UserName="<SYSTEM>"
__PROPERTY_COUNT : 8
__DERIVATION     : {CIM_SystemResource, CIM_LogicalElement, CIM_ManagedSystemElement}
__SERVER         : SYSTEM01
__NAMESPACE      : root\cimv2
__PATH           : \\SYSTEM01\root\cimv2:Win32_Environment.Name="testvar",UserName="<SYSTEM>"
Caption          : <SYSTEM>\testvar
Description      : <SYSTEM>\testvar
InstallDate      :
Name             : testvar
Status           : OK
SystemVariable   : True
UserName         : <SYSTEM>
VariableValue    : testvalue
```

此命令會建立 testvar 環境變數，其值為 testvalue。
它是藉由建立 **Win32_Environment** WMI 類別的新實例來完成這項工作。
此操作需要適當的認證，而且您可能必須重新開機 Windows PowerShell，才能看到新的環境變數。

### 範例3：設定數部遠端電腦的 WMI 記錄層級

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2} -Computername "system01", "system02", "system03"
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
...
```

這個命令會將 WMI 記錄層級設定為 2。
此命令會在引數參數中傳遞要設定的屬性，並將值一起視為值組。
此參數接受一個由 @{property = value} 建構所定義的雜湊表。
傳回的類別資訊會反映新的值。

## PARAMETERS

### -Arguments
指定要變更之屬性的名稱和該屬性的新值。
名稱和值必須是成對的名稱和值。
名稱/值組會以雜湊表的形式在命令列上傳遞。
例如：

`@{Setting1=1; Setting2=5; Setting3="test"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: class, object, path
Aliases: Args, Property

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob
表示這個 cmdket 會以背景工作的形式執行。
使用此參數執行需要很長時間才能完成的命令。

當您指定 *AsJob* 參數時，此命令會傳回代表背景工作的物件，然後顯示命令提示字元。
工作完成後，您可以繼續在工作階段中工作。
如果遠端電腦使用 **set-wmiinstance** ，則會在本機電腦上建立工作，而來自遠端電腦的結果則會自動傳回到本機電腦。
若要管理工作，請使用包含 **作業** 名詞 ( **工作 Cmdlet) 的 Cmdlet。**
若要取得工作結果，請使用 Receive-Job Cmdlet。

若要將這個參數與遠端電腦搭配使用，必須設定本機和遠端電腦以進行遠端處理。
此外，您必須使用 Windows Vista 和更新版本的 Windows 作業系統中的 [以系統管理員身分執行] 選項來啟動 Windows PowerShell。
如需詳細資訊，請參閱 about_Remote_Requirements。

如需有關 Windows PowerShell 背景工作的詳細資訊，請參閱 about_Jobs 和 about_Remote_Jobs。

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
指定必須搭配 WMI 連接使用的驗證層級。
此參數可接受的值為：

- -1：未變更。
- 0：預設值。
- 1：無。
未執行任何驗證。
- 2：連接。
只有當用戶端與應用程式建立關聯性時，才會執行驗證。
- 3：呼叫。
只有當應用程式收到要求時，才會在每次呼叫開始時執行驗證。
- 4：封包。
會在從用戶端接收的所有資料上執行驗證。
- 5： PacketIntegrity。
在用戶端與應用程式之間傳輸的所有資料都會經過驗證和驗證。
- 6： PacketPrivacy。
系統會使用其他驗證層級的屬性，並加密所有資料。

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authority
指定用來驗證 WMI 連線的授權單位。
您可以指定標準 NTLM 或 Kerberos 驗證。
若要使用 NTLM，請將授權單位設定為 "ntlmdomain:\<DomainName\>"，其中 \<DomainName\> 識別有效的 NTLM 網域名稱。
若要使用 Kerberos，請指定 kerberos： \<DomainName\> \\ \<ServerName\> 。
當您連線到本機電腦時，不能包含授權單位設定。

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Class
指定 WMI 類別的名稱。

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName
指定此 Cmdlet 執行所在的電腦名稱稱。
預設是本機電腦。

請輸入一部或多部電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。
若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。

此參數不必依賴 Windows PowerShell 遠端功能。
即使您的電腦未設定為執行遠端命令，您仍然可以使用 *ComputerName* 參數。

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
指定具有執行此動作權限的使用者帳戶。
預設為目前使用者。

輸入使用者名稱，例如 User01 或 Domain01\User01，或輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 產生的物件。
如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。

隨 Windows PowerShell 安裝的任何提供者都不支援此參數。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges
指出此 Cmdlet 會在進行 WMI 呼叫之前，先啟用目前使用者的擁有權限。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
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

- 0：預設值。
讀取預設模擬層級的本機登錄，通常設定為3：模擬。
- 1： Anonymous。
隱藏呼叫端的認證。
- 2：識別。
允許物件查詢呼叫端的認證。
- 3：模擬。
允許物件使用呼叫端的認證。
- 4：委派。
允許物件許可其他物件使用呼叫端的認證。

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
指定要做為輸入使用的 **system.management.managementobject** 物件。
使用這個參數時，會忽略所有其他參數（ *引數* 參數除外）。

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Locale
指定 WMI 物件的慣用地區設定。
*地區* 設定參數是以慣用順序，以 MS_ 格式的陣列指定 \<LCID\> 。

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace
指定當與 *類別* 參數搭配使用時，參考的 wmi 類別所在的 wmi 存放庫命名空間。

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
指定您想要建立或更新之實例的 WMI 物件路徑。

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PutType
指出是否要建立或更新 WMI 實例。
此參數可接受的值為：

- UpdateOnly.
更新現有的 WMI 執行個體。
- 以.
建立新的 WMI 執行個體。
- UpdateOrCreate.
如果 WMI 執行個體存在，就更新該執行個體，如果執行個體不存在，則建立新執行個體。

```yaml
Type: System.Management.PutType
Parameter Sets: (All)
Aliases:
Accepted values: None, UpdateOnly, CreateOnly, UpdateOrCreate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
指定為執行此命令可建立的最大同時連線數。
此參數會與 *AsJob* 參數一起使用。
節流限制僅適用於目前命令，不適用於工作階段或電腦。

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

### -Confirm
在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無
此 Cmdlet 不接受輸入。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Get-WmiObject](Get-WmiObject.md)

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Remove-WmiObject](Remove-WmiObject.md)
