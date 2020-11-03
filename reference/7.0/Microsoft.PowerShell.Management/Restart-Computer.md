---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: ce9e19140cb0bb8fd9172fa7ca7929fb696f9c65
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205503"
---
# Restart-Computer

## 概要
重新開機本機電腦和遠端電腦上的作業系統。

## SYNTAX

### DefaultSet (預設值)

```
Restart-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential]<PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Restart-Computer`Cmdlet 會重新開機本機電腦和遠端電腦上的作業系統。

您可以使用的參數 `Restart-Computer` 來執行重新開機作業、指定驗證等級和替代認證、限制同時執行的作業，以及強制立即重新開機。

從 Windows PowerShell 3.0 開始，您可以先等候重新開機完成，再執行下一個命令。 指定等候超時和查詢間隔，並等候特定服務可在重新開機的電腦上使用。 這項功能可讓您在腳本和函式中使用非常實用 `Restart-Computer` 。

## 範例

### 範例1：重新開機本機電腦

`Restart-Computer` 重新開機本機電腦。

```powershell
Restart-Computer
```

### 範例2：重新開機多部電腦

`Restart-Computer` 可以重新開機遠端和本機電腦。 **ComputerName** 參數接受電腦名稱稱的陣列。

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### 範例3：從文字檔取得電腦名稱稱

`Restart-Computer` 從文字檔取得電腦名稱稱的清單，並重新啟動電腦。 未指定 **ComputerName** 參數。 但因為它是第一個位置參數，所以它會接受從管線傳送的文字檔中的電腦名稱稱。

```powershell
Get-Content -Path C:\Domain01.txt | Restart-Computer
```

`Get-Content` 使用 **Path** 參數從文字檔中取得電腦名稱稱的清單， **Domain01.txt** 。 電腦名稱稱會沿著管線向下傳送。 `Restart-Computer` 重新開機每部電腦。

### 範例4：強制重新開機文字檔中列出的電腦

此範例會強制立即重新開機檔案中列出的電腦 `Domain01.txt` 。 文字檔中的電腦名稱稱會儲存在變數中。 **Force** 參數會強制立即重新開機。

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force
```

`Get-Content` 使用 **Path** 參數從文字檔中取得電腦名稱稱的清單， **Domain01.txt** 。 電腦名稱稱會儲存在變數中 `$Names` 。 `Get-Credential` 提示您輸入使用者名稱和密碼，並將值儲存在變數中 `$Creds` 。 `Restart-Computer` 使用 **ComputerName** 和 **Credential** 參數及其變數。 **Force** 參數會導致立即重新開機每一部電腦。

### 範例6：重新開機遠端電腦並等候 PowerShell

`Restart-Computer` 重新開機遠端電腦，然後等候最多5分鐘的時間 (300 秒) ，讓 PowerShell 在重新開機的電腦上變成可用，然後再繼續進行。

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

`Restart-Computer` 使用 **ComputerName** 參數來指定 **Server01** 。 **Wait** 參數會等候重新開機完成。 的 **會指定 PowerShell** 可以在遠端電腦上執行命令。 Timeout 參數指定五分鐘的等候 **時間** 。 **Delay** 參數會每隔兩秒查詢一次遠端電腦，以判斷是否已重新開機。

### 範例7：使用 WsmanAuthentication 重新開機電腦

`Restart-Computer` 使用 **WsmanAuthentication** 機制重新開機遠端電腦。
Kerberos 驗證會決定目前使用者是否具有重新開機遠端電腦的許可權。 如需詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

```powershell
Restart-Computer -ComputerName Server01 -WsmanAuthentication Kerberos
```

`Restart-Computer` 使用 **ComputerName** 參數來指定遠端電腦 **Server01** 。
**WsmanAuthentication** 參數會將驗證方法指定為 **Kerberos** 。

## PARAMETERS

### -ComputerName

指定一個電腦名稱稱或以逗號分隔的電腦名稱稱陣列。 `Restart-Computer` 接受管線或變數中的 **ComputerName** 物件。

輸入遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。 若要指定本機電腦，請輸入電腦名稱稱、點 `.` 或 localhost。

此參數不依賴 PowerShell 遠端功能。 即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。

如果未指定 **ComputerName** 參數，則會 `Restart-Computer` 重新開機本機電腦。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作之許可權的使用者帳戶。 預設為目前使用者。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Delay

指定查詢的頻率（以秒為單位）。 PowerShell 會查詢 **For** 參數指定的服務，以判斷在重新開機電腦之後，服務是否可用。

這個參數只適用于 **Wait** 和 **For** 參數。

此參數是在 Windows PowerShell 3.0 引進。

如果未指定 **Delay** 參數，會 `Restart-Computer` 使用五秒的延遲。

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -For

指定 PowerShell 的行為，因為它會等候指定的服務或功能在電腦重新開機後變成可用。 這個參數只對 **Wait** 參數有效。

此參數可接受的值為：

- **預設值** ：等候 PowerShell 重新開機。
- **Powershell** ：可以在電腦上的 powershell 遠端會話中執行命令。
- **WMI** ：接收對電腦 Win32_ComputerSystem 查詢的回覆。
- **WinRM** ：可以使用 WS-Management 來建立連到電腦的遠端工作階段。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: (All)
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

強制立即重新開機電腦。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Timeout

指定等待的持續時間 (單位為秒)。 當超時時間過後， `Restart-Computer` 即使電腦未重新開機，也會回到命令提示字元。

**Timeout** 參數只對 **Wait** 參數有效。 **Timeout** 會覆寫 **等待** 參數的無限等待期間。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait

`Restart-Computer` 抑制 PowerShell 提示字元並封鎖管線，直到電腦重新開機為止。 您可以在腳本中使用這個參數來重新開機電腦，然後在重新開機完成時繼續處理。

**Wait** 參數會無限期地等候電腦重新開機。 您可以使用 **Timeout** 來調整計時 **，以及使用和****延遲** 參數來等待特定服務在重新開機的電腦上變成可用。

當您重新開機本機電腦時， **Wait** 參數無效。 如果 **ComputerName** 參數的值包含遠端電腦和本機電腦的名稱，則會產生在 `Restart-Computer` 本機電腦上 **等候** 的非終止錯誤，但是會等待遠端電腦重新開機。

此參數是在 Windows PowerShell 3.0 引進。

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

### -WsmanAuthentication

指定用來驗證使用者認證的機制。 此參數是在 Windows PowerShell 3.0 引進。

此參數可接受的值為： **Basic** 、 **CredSSP** 、 **Default** 、 **Digest** 、 **Kerberos** 和 **Negotiate** 。

如需詳細資訊，請參閱 [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!WARNING]
> 認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。 此機制會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在執行之前提示您確認 `Restart-Computer` 。

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

顯示執行時所發生的情況 `Restart-Computer` 。 `Restart-Computer`Cmdlet 不會執行。

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

### System.String

`Restart-Computer` 接受來自管線或變數的電腦名稱稱。

## 輸出

### 無

`Restart-Computer` 不會產生任何輸出。

## 注意

- `Restart-Computer` 只適用于執行 Windows 的電腦，而且需要 WinRM 和 WMI 來關閉系統，包括本機系統。
- `Restart-Computer`使用 Windows Management Instrumentation (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem)類別的[Win32Shutdown 方法](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem)。 此方法需要針對用來重新開機電腦的使用者帳戶啟用 **SeShutdownPrivilege** 許可權。

## 相關連結

[關於 Windows 遠端管理](/windows/desktop/WinRM/about-windows-remote-management)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[WS-Management 通訊協定](/windows/desktop/WinRM/ws-management-protocol)
