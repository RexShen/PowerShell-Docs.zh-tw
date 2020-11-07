---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: aadb0d53ad180ba1e88d31e5d008c6090ae0c9b3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345216"
---
# New-Service

## 概要
建立新的 Windows 服務。

## SYNTAX

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartupType>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `New-Service` Cmdlet 會在登錄和服務資料庫中建立 Windows 服務的新專案。 新的服務需要在服務期間執行的可執行檔。

此 Cmdlet 的參數可讓您設定服務的顯示名稱、描述、啟動類型與相依性。

## 範例

### 範例1：建立服務

```powershell
New-Service -Name "TestService" -BinaryPathName "C:\WINDOWS\System32\svchost.exe -k netsvcs"
```

此命令會建立名為 TestService 的服務。

### 範例2：建立包含描述、啟動類型和顯示名稱的服務

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = "C:\WINDOWS\System32\svchost.exe -k netsvcs"
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

此命令會建立名為 TestService 的服務。 它使用的參數 `New-Service` 來指定新服務的描述、啟動類型和顯示名稱。

### 範例3：查看新的服務

```powershell
Get-CimInstance -ClassName Win32_Service -Filter "Name='testservice'"
```

```Output
ExitCode  : 0
Name      : testservice
ProcessId : 0
StartMode : Auto
State     : Stopped
Status    : OK
```

此命令會使用 `Get-CimInstance` 來取得新服務的 **Win32_Service** 物件。 此物件包含啟動模式和服務描述。

## PARAMETERS

### -BinaryPathName

指定服務的可執行檔路徑。 這是必要參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

將服務所使用的帳戶指定為 [服務登入帳戶](/windows/desktop/ad/about-service-logon-accounts)。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。 如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

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

### -DependsOn

指定新服務所依存之其他服務的名稱。 若要輸入多個服務名稱，請使用逗號來分隔名稱。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

指定服務的描述。

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

### -DisplayName

指定服務的顯示名稱。

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

### -Name

指定服務的名稱。 這是必要參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StartupType

設定服務的啟動類型。 此參數可接受的值為：

- **自動** -服務會在系統啟動時啟動或由作業系統啟動。
  如果自動啟動的服務依賴手動啟動的服務，以手動方式啟動的服務也會在系統啟動時自動啟動。
- **AutomaticDelayedStart** -在系統開機之後不久就會開始。
- **停用** -服務已停用，且無法由使用者或應用程式啟動。
- **InvalidValue** -不支援此值。 使用此值會導致錯誤。
- **手動** -此服務只會由使用者以手動方式啟動，使用服務控制管理員或由應用程式啟動。

 預設值為 [ **自動** ]。

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases:
Accepted values: Automatic, Manual, Disabled, AutomaticDelayedStart, InvalidValue

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

### None

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.ServiceProcess.ServiceController

此 Cmdlet 會傳回代表新服務的物件。

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

若要執行此 Cmdlet，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

## 相關連結

[Get-Service](Get-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
