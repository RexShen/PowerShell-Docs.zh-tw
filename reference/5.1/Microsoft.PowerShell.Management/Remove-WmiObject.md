---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WmiObject
ms.openlocfilehash: 287eb02e7de2f4182e0ecfd7f6b6a7cafb66969e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203559"
---
# Remove-WmiObject

## 概要
刪除現有 Windows Management Instrumentation (WMI) 類別的執行個體。

## SYNTAX

### class (預設值)

```
Remove-WmiObject [-Class] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 物件 (object)

```
Remove-WmiObject -InputObject <ManagementObject> [-AsJob] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### path

```
Remove-WmiObject -Path <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### 查詢

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### list

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
**>get-wmiobject** 指令程式會刪除現有 WINDOWS MANAGEMENT INSTRUMENTATION (WMI) 類別的實例。

## 範例

### 範例1：關閉 Win32 進程的所有實例

```
PS C:\> notepad
PS C:\> $np = Get-WmiObject -Query "select * from win32_process where name='notepad.exe'"
PS C:\> $np | Remove-WmiObject
```

這個範例會關閉 Notepad.exe 的所有實例。

第一個命令會啟動一個「記事本」執行個體。

第二個命令會使用 Get-WmiObject Cmdlet 來取出對應至 Notepad.exe 的 Win32_Process 實例，然後將它們儲存在 $np 變數中。

第三個命令會將 $np 變數中的物件傳遞至 **>get-wmiobject** ，以刪除 Notepad.exe 的所有實例。

### 範例2：刪除資料夾

```
PS C:\> $a = Get-WMIObject -Query "Select * From Win32_Directory Where Name ='C:\\Test'"
PS C:\> $a | Remove-WMIObject
```

此命令會刪除 C:\Test 資料夾。

第一個命令會使用 **>get-wmiobject** 來查詢 C:\Test 資料夾，然後將物件儲存在 $a 變數中。

第二個命令會以管線將 $a 變數傳送至 **>get-wmiobject** ，以刪除資料夾。

## PARAMETERS

### -AsJob
指出此 Cmdlet 會以背景工作的形式執行。
使用此參數執行需要很長時間才能完成的命令。

已導入 Windows PowerShell 3.0 的新 CIM Cmdlet 可執行與 WMI Cmdlet 相同的工作。
CIM Cmdlet 符合 WS-Management (WSMan) 標準以及通用訊息模型 (CIM) 標準，可讓 Cmdlet 使用相同的技術來管理執行 Windows 作業系統的電腦，以及執行其他作業系統的電腦。
請考慮使用 CimInstance 指令程式，而不是使用 **>get-wmiobject** https://go.microsoft.com/fwlink/?LinkId=227964 。

使用 *AsJob* 參數時，此命令會傳回代表背景工作的物件，然後顯示命令提示字元。
工作完成後，您可以繼續在工作階段中工作。
如果對遠端電腦使用 **Remove-WmiObject** ，就會在本機電腦上建立工作，而來自遠端電腦的結果則會自動傳回到本機電腦。
若要管理工作，請使用包含 **作業** 名詞 ( **工作 Cmdlet) 的 Cmdlet。**
若要取得工作結果，請使用 Receive-Job Cmdlet。

若要將此參數用於遠端電腦，必須設定本機和遠端電腦以進行遠端處理。
使用 [以系統管理員身分執行] 選項開始 Windows PowerShell。
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
指定用於 WMI 連線的驗證層級。
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
指定此 Cmdlet 刪除之 WMI 類別的名稱。

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
使用這個參數時，將會忽略所有其他參數。

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
*地區* 設定參數是以慣用順序指定為 MS_ 格式的陣列 \<LCID\> 。

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
指定 WMI 類別的 WMI 物件路徑，或指定要刪除之 WMI 類別執行個體的 WMI 物件路徑。

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

### System.Management.ManagementObject
您可以使用管線將管理物件傳送至此 Cmdlet。

## 輸出

### None、System.management.automation.remotingjob、Automation。
如果您指定 *AsJob* 參數，此 Cmdlet 會傳回工作物件。
否則，它不會產生任何輸出。

## 注意

## 相關連結

[Get-WmiObject](Get-WmiObject.md)

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Set-WmiInstance](Set-WmiInstance.md)
