---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 0c007f1becd7364806cfd47e18cf05995b81e0f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203988"
---
# Get-Service

## 概要
取得本機電腦或遠端電腦上的服務。

## SYNTAX

### Default (預設值)

```
Get-Service [[-Name] <String[]>] [-ComputerName <String[]>] [-DependentServices] [-RequiredServices]
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### DisplayName

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] -DisplayName <String[]>
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### InputObject

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## DESCRIPTION

**Get-help** Cmdlet 會取得代表本機電腦或遠端電腦上之服務的物件，包括執行中和已停止的服務。

您可以藉由指定服務的服務名稱或顯示名稱，或使用管線將服務物件傳送至此 Cmdlet，來指示此 Cmdlet 只取得特定的服務。

## 範例

### 範例1：取得電腦上的所有服務

```powershell
Get-Service
```

此命令會取得電腦上的所有服務。
它的行為就像您輸入 `Get-Service *` 的一樣。
預設顯示會展示狀態、服務名稱及每個服務的顯示名稱。

### 範例2：取得以搜尋字串開頭的服務

```powershell
Get-Service "wmi*"
```

此命令會取得服務名稱開頭為 WMI 的服務， (Windows Management Instrumentation) 的縮寫。

### 範例3：顯示包含搜尋字串的服務

```powershell
Get-Service -Displayname "*network*"
```

此命令會顯示顯示名稱包含「網路」文字的服務。
搜尋顯示名稱會尋找網路相關的服務，即使服務名稱並不包含 "Net"，例如 xmlprov (網路佈建服務)。

### 範例4：取得以搜尋字串和排除開頭的服務

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

這些命令只會取得服務名稱開頭為 win 的服務，但 WinRM 服務除外。

### 範例5：顯示目前作用中的服務

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

此命令只會顯示目前使用中的服務。
它會使用 **get-help** Cmdlet 取得電腦上的所有服務。
管線運算子 (|) 將結果傳遞給 Where-Object Cmdlet，此 Cmdlet 只會選取 Status 屬性等於「正在執行」的服務。

Status 只是服務物件的一個屬性。
若要查看所有屬性，請輸入 `Get-Service | Get-Member` 。

### 範例6：取得遠端電腦上的服務

```powershell
Get-Service -ComputerName "Server02"
```

此命令會取得 Server02 遠端電腦上的服務。

因為「 **取得服務** 」的 *ComputerName* 參數不會使用 Windows PowerShell 遠端處理，所以即使電腦未設定 Windows PowerShell 的遠端功能，您還是可以使用這個參數。

### 範例7：列出本機電腦上具有相依服務的服務

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

第一個命令使用 **get-help** Cmdlet 取得電腦上的服務。
管線運算子 (|) 會將服務傳送至 **Where 物件** Cmdlet，此 Cmdlet 會選取 **DependentServices** 屬性不是 null 的服務。

另一個管線運算子會將結果傳送給 Format-List Cmdlet。
此命令會使用其 *Property* 參數來顯示服務的名稱、相依服務的名稱，以及顯示每個服務所擁有之相依服務數目的計算屬性。

### 範例8：依屬性值排序服務

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

此命令顯示當您依 [ **狀態** ] 屬性的值以遞增順序排序服務時，已停止的服務會在執行服務之前出現。
發生這種情況是因為 Status 的值是列舉，其中已停止的值為1，而且執行的值為4。

若要先列出執行中的服務，請使用 Sort-Object Cmdlet 的 *遞減* 參數。

### 範例9：取得多部電腦上的服務

```powershell
Get-Service -Name "WinRM" -ComputerName "localhost", "Server01", "Server02" |
 Format-Table -Property MachineName, Status, Name, DisplayName -auto
```

```Output
MachineName    Status  Name  DisplayName
------------   ------  ----  -----------
localhost      Running WinRM Windows Remote Management (WS-Management)
Server01       Running WinRM Windows Remote Management (WS-Management)
Server02       Running WinRM Windows Remote Management (WS-Management)
```

此命令會使用 **get-help** Cmdlet 在兩部遠端電腦上執行 Get-Service Winrm 命令，並在本機電腦上執行 ( "localhost" ) 。

此命令會在遠端電腦上執行，並將結果傳回本機電腦。
管線運算子 (|) 將結果傳送至 **格式資料表** Cmdlet，此 Cmdlet 會將服務格式化為資料表。
**Format 資料表** 命令使用 *Property* 參數來指定顯示在資料表中的屬性，包括 **MachineName** 屬性。

### 範例10：取得服務的相依服務

```powershell
Get-Service "WinRM" -RequiredServices
```

此命令會取得 WinRM 服務所需的服務。

此命令會傳回服務之 **ServicesDependedOn** 屬性的值。

### 範例11：透過管線運算子取得服務

```powershell
"WinRM" | Get-Service
```

此命令會取得本機電腦上的 WinRM 服務。
此範例示範您可以使用管線將服務名稱字串 (以引號括住) 至 **取得服務** 。

## PARAMETERS

### -ComputerName

取得在指定電腦上執行的服務。
預設是本機電腦。

輸入遠端電腦 (FQDN) 的 NetBIOS 名稱、IP 位址或完整功能變數名稱。
若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。

此參數不必依賴 Windows PowerShell 遠端功能。
即使您的電腦未設定為執行遠端命令，您也可以使用 **Get-Service** 的 *ComputerName* 參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DependentServices

指出此 Cmdlet 只會取得相依于指定服務的服務。

根據預設，此 Cmdlet 會取得所有服務。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

以字串陣列指定要抓取之服務的顯示名稱。
允許使用萬用字元。
根據預設，此 Cmdlet 會取得電腦上的所有服務。

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Exclude

以字串陣列指定此 Cmdlet 從作業中排除的服務或服務。
此參數的值會限定 *Name* 參數。
輸入名稱元素或模式，例如 "s*"。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

以字串陣列指定此 Cmdlet 在作業中包含的服務或服務。
此參數的值會限定 *Name* 參數。
輸入名稱元素或模式，例如 "s*"。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

指定代表要抓取之服務的 **ServiceController** 物件。
輸入包含物件的變數，或輸入可取得物件的命令或運算式。
您也可以使用管線將服務物件傳送至此 Cmdlet。

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要抓取之服務的服務名稱。
允許使用萬用字元。
根據預設，此 Cmdlet 會取得電腦上的所有服務。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -RequiredServices

指出此 Cmdlet 只會取得此服務所需的服務。

此參數會取得服務之 **ServicesDependedOn** 屬性的值。
根據預設，此 Cmdlet 會取得所有服務。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.ServiceProcess.ServiceController、System.String

您可以使用管線將服務物件或服務名稱傳送至此 Cmdlet。

## 輸出

### System.ServiceProcess.ServiceController

此 Cmdlet 會傳回代表電腦上服務的物件。

## 注意

您也可以使用內建的別名 "gsv" 來參考 **Get Service** 。 如需詳細資訊，請參閱 about_Aliases。

只有當目前的使用者具有查看服務的許可權時，此 Cmdlet 才會顯示服務。
如果此 Cmdlet 未顯示服務，您可能沒有查看服務的許可權。

若要尋找您系統上每個服務的服務名稱和顯示名稱，請輸入 `Get-Service` 。
服務名稱會出現在 Name 欄位中，而顯示名稱會出現在 DisplayName 欄位中。

當您依狀態值以遞增順序進行排序時，"Stopped" 服務會顯示在 "Running" 服務之前。
服務的 Status 屬性是一個列舉值，其中狀態的名稱會呈現為整數值。
排序是根據整數值，而不是根據名稱。
"Running" 會出現在 "Stopped" 之前，因為 "Stopped" 的值為 "1"，而 "Running" 的值為 "4"。

## 相關連結

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
