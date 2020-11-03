---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-wmimethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WmiMethod
ms.openlocfilehash: e9743488e86429e5cc3252162e51268a7978b79d
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "93205283"
---
# Invoke-WmiMethod

## 概要
呼叫 WMI 方法。

## SYNTAX

### class (預設值)

```
Invoke-WmiMethod [-Class] <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 物件 (object)

```
Invoke-WmiMethod -InputObject <ManagementObject> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### path

```
Invoke-WmiMethod -Path <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 查詢

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### list

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Invoke-WmiMethod`Cmdlet 會呼叫 WMI) 物件 (Windows Management Instrumentation 的方法。

在 Windows PowerShell 3.0 中引進的新通用訊息模型 (CIM) Cmdlet，會執行與 WMI Cmdlet 相同的工作。 CIM Cmdlet 符合 WS-Management (WSMan) 標準和 CIM 標準，可讓 Cmdlet 使用相同的技術來管理 Windows 電腦和執行其他作業系統的電腦。 請 `Invoke-WmiMethod` 考慮使用 [Invoke invoke-cimmethod](../cimcmdlets/invoke-cimmethod.md)，而不是使用。

## 範例

### 範例1：列出 WMI 物件的必要順序

```powershell
([wmiclass]'Win32_Volume').GetMethodParameters('Format')
```

```Output
__GENUS           : 2
__CLASS           : __PARAMETERS
__SUPERCLASS      :
__DYNASTY         : __PARAMETERS
__RELPATH         :
__PROPERTY_COUNT  : 6
__DERIVATION      : {}
__SERVER          :
__NAMESPACE       :
__PATH            :
ClusterSize       : 0
EnableCompression : False
FileSystem        : NTFS
Label             :
QuickFormat       : False
Version           : 0
PSComputerName    :
```

此命令列出必要的物件順序。 在 PowerShell 3.0 中叫用 WMI 不同於替代方法，且需要以特定順序輸入物件值。

### 範例2：啟動應用程式的實例

```powershell
([Wmiclass]'Win32_Process').GetMethodParameters('Create')
```

```Output
__GENUS                   : 2
__CLASS                   : __PARAMETERS
__SUPERCLASS              :
__DYNASTY                 : __PARAMETERS
__RELPATH                 :
__PROPERTY_COUNT          : 3
__DERIVATION              : {}
__SERVER                  :
__NAMESPACE               :
__PATH                    :
CommandLine               :
CurrentDirectory          :
ProcessStartupInformation :
PSComputerName            :
```

```powershell
Invoke-WmiMethod -Path win32_process -Name create -ArgumentList notepad.exe
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 2
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ProcessId        : 11312
ReturnValue      : 0
PSComputerName   :
```

此命令會藉由呼叫 Win32_Process 類別的方法，啟動「記事本」的實例 `Create` 。 **Win32_Process**

**ReturnValue** 屬性會填入0，而 **ProcessId** 屬性則會填入整數 (下一個處理序識別碼) （如果命令已完成）。

### 範例3：重新命名檔案

```powershell
Invoke-WmiMethod -Path "CIM_DataFile.Name='C:\scripts\test.txt'" -Name Rename -ArgumentList "C:\scripts\test_bu.txt"
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ReturnValue      : 0
```

此命令會重新命名檔案。 它會使用 **Path** 參數來參考 **CIM_DataFile** 類別的實例。 然後，它會將 Rename 方法套用至該特定執行個體。

如果命令完成， **ReturnValue** 屬性會填入0。

### 範例4：使用傳遞值陣列 `-ArgumentList`

使用後面接著值的物件陣列的範例 `$binSD` `$null` 。

```powershell
$acl = get-acl test.txt
$binSD = $acl.GetSecurityDescriptorBinaryForm()
Invoke-WmiMethod -class Win32_SecurityDescriptorHelper -Name BinarySDToSDDL -ArgumentList $binSD, $null
```

## PARAMETERS

### -ArgumentList

指定要傳送至呼叫之方法的參數。 這個參數的值必須是物件的陣列，且必須以所呼叫方法所需的順序出現。 `Invoke-CimCommand`Cmdlet 沒有這些限制。

若要判斷列出這些物件的順序，請 `GetMethodParameters()` 在 WMI 類別上執行方法，如本主題結尾附近的範例1所示。

> [!IMPORTANT]
> 如果第一個值是包含多個元素的陣列，則需要第二個值 $null。 否則命令會產生錯誤，例如「無法將型別 'System.Byte' 的物件轉換為型別 'System.Array'」。 請參閱上述的範例4。

```yaml
Type: System.Object[]
Parameter Sets: class, object, path
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

指出此 Cmdlet 會以背景工作方式執行命令。 使用此參數執行需要很長時間才能完成的命令。

使用 **AsJob** 參數時，此命令會傳回代表背景工作的物件，然後顯示命令提示字元。 工作完成後，您可以繼續在工作階段中工作。 如果 `Invoke-WmiMethod` 用於遠端電腦，則會在本機電腦上建立工作，而來自遠端電腦的結果則會自動傳回到本機電腦。 若要管理工作，請使用包含 Job 名詞的 Cmdlet (各種 Job Cmdlet)。 若要取得工作結果，請使用 Receive-Job Cmdlet。

若要將這個參數與遠端電腦搭配使用，則本機電腦和遠端電腦必須針對遠端執行功能做設定。 此外，您必須使用 Windows Vista 和更新版本的 Windows 中的 [以系統管理員身分執行] 選項來啟動 Windows PowerShell。 如需詳細資訊，請參閱 about_Remote_Requirements。

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

指定要與 WMI 連線搭配使用的驗證等級。 此參數可接受的值為：

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

指定用來驗證 WMI 連線的授權單位。 您可以指定標準 Windows NT LAN Manager (NTLM) 或 Kerberos 驗證。 若要使用 NTLM，請將授權單位設定為 "ntlmdomain:\<DomainName\>"，其中 \<DomainName\> 識別有效的 NTLM 網域名稱。 若要使用 Kerberos，請指定 kerberos:\<DomainName\ServerName\>。 當您連線到本機電腦時，不能包含授權單位設定。

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

指定包含要呼叫之靜態方法的 WMI 類別。

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

以字串陣列指定此 Cmdlet 在其上執行命令的電腦。 預設是本機電腦。

請輸入一部或多部電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。 若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。

此參數不必依賴 Windows PowerShell 遠端功能。 即使您的電腦未設定為執行遠端命令，您仍然可以使用 **ComputerName** 參數。

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

指定具有執行此動作權限的使用者帳戶。 預設為目前使用者。 輸入使用者名稱，例如 `User01` 、 `Domain01\User01` 或 `User@Contoso.com` 。 或者，輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 所傳回的物件。 當您輸入使用者名稱時，會提示您輸入密碼。

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

指出此 Cmdlet 會在命令進行 WMI 呼叫之前，先啟用目前使用者的擁有權限。

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

指定要使用的模擬等級。 此參數可接受的值為：

- 0：Default (讀取本機登錄以找出預設模擬等級，通常是設定為 "3：Impersonate"。)
- 1：Anonymous (隱藏呼叫端的認證。)
- 2：Identify (允許物件查詢呼叫端的認證。)
- 3：Impersonate (允許物件使用呼叫端的認證。)
- 4：Delegate (允許物件許可其他物件使用呼叫端的認證。)

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

指定要做為輸入使用的 **system.management.managementobject** 物件。 使用這個參數時，會忽略 **旗** 標和 **引數** 參數以外的所有其他參數。

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

指定 WMI 物件的慣用地區設定。 以慣用順序將 **地區** 設定參數的值指定為格式的陣列 `MS_<LCID>` 。

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

### -Name

指定要叫用之方法的名稱。 這是必要參數，不能是 null 或空白。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace

與 **Class** 參數搭配使用時，此參數會指定參考的 wmi 類別或物件所在的 wmi 存放庫命名空間。

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

指定 WMI 類別的 WMI 物件路徑，或指定 WMI 類別之執行個體的 WMI 物件路徑。 您指定的類別或實例必須包含 **Name** 參數中指定的方法。

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

### -ThrottleLimit

針對可同時執行的 WMI 作業數目指定節流值。
此參數會與 **AsJob** 參數一起使用。 節流限制僅適用於目前命令，不適用於工作階段或電腦。

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

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

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

此 Cmdlet 不接受任何輸入。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Get-WSManInstance](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[Invoke-WSManAction](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[New-WSManInstance](../Microsoft.WsMan.Management/New-WSManInstance.md)

[Remove-WSManInstance](../Microsoft.WsMan.Management/Remove-WSManInstance.md)

[Get-WmiObject](Get-WmiObject.md)

[Remove-WmiObject](Remove-WmiObject.md)

[Set-WmiInstance](Set-WmiInstance.md)
