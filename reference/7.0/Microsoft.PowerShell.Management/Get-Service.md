---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: ce91313d1b581e3d666c131caaa1cf7ecad0c04f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201563"
---
# Get-Service

## 概要
取得電腦上的服務。

## SYNTAX

### Default (預設值)

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### DisplayName

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### InputObject

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-Service`Cmdlet 會取得代表電腦上之服務的物件，包括執行中和已停止的服務。 依預設，當 `Get-Service` 執行時沒有參數時，會傳回所有本機電腦的服務。

您可以藉由指定服務的服務名稱或顯示名稱，或使用管線將服務物件傳送至此 Cmdlet，來指示此 Cmdlet 只取得特定的服務。

## 範例

### 範例1：取得電腦上的所有服務

此範例會取得電腦上的所有服務。 它的行為就像您輸入 `Get-Service *` 的一樣。 預設顯示會展示狀態、服務名稱及每個服務的顯示名稱。

```powershell
Get-Service
```

### 範例2：取得以搜尋字串開頭的服務

此範例會使用以 WMI 為開頭 (Windows Management Instrumentation) 的服務名稱，來抓取服務。

```powershell
Get-Service "wmi*"
```

### 範例3：顯示包含搜尋字串的服務

此範例會顯示顯示名稱包含「網路」文字的服務。 搜尋顯示名稱，即使服務名稱不包含 Net （例如 xmlprov (）網路布建服務，也會尋找網路相關的服務。

```powershell
Get-Service -Displayname "*network*"
```

### 範例4：取得以搜尋字串和排除開頭的服務

此範例只會取得服務名稱開頭為 **win** 的服務，但 WinRM 服務除外。

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### 範例5：顯示目前作用中的服務

此範例只會顯示狀態為 [正在執行] 的服務。

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

`Get-Service` 取得電腦上的所有服務，並將物件沿著管線向下傳送。 `Where-Object`Cmdlet 只會選取 **Status** 屬性等於正在執行的服務。

Status 只是服務物件的一個屬性。 若要查看所有屬性，請輸入 `Get-Service | Get-Member` 。

### 範例6：列出電腦上具有相依服務的服務

此範例會取得具有相依服務的服務。

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

`Get-Service`Cmdlet 會取得電腦上的所有服務，並將物件沿著管線向下傳送。 `Where-Object`Cmdlet 會選取其 **DependentServices** 屬性不是 null 的服務。

結果會向下傳送至 `Format-List` Cmdlet。 **Property** 參數會顯示服務的名稱、相依服務的名稱，以及顯示每個服務的相依服務數目的計算屬性。

### 範例7：依屬性值排序服務

此範例顯示當您依 [ **狀態** ] 屬性的值以遞增順序排序服務時，已停止的服務會在執行服務之前出現。 原因是 **狀態** 的值是列舉，其中已停止的值為1，且執行的值為4。 如需詳細資訊，請參閱 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。

若要先列出執行中的服務，請使用 Cmdlet 的 **遞減** 參數 `Sort-Object` 。

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

### 範例8：取得服務的相依服務

此範例會取得 WinRM 服務所需的服務。 傳回服務之 **ServicesDependedOn** 屬性的值。

```powershell
Get-Service "WinRM" -RequiredServices
```

### 範例9：透過管線運算子取得服務

這個範例會取得本機電腦上的 WinRM 服務。 服務名稱字串（以引號括住）會沿著管線向下傳送至 `Get-Service` 。

```powershell
"WinRM" | Get-Service
```

## PARAMETERS

### -DependentServices

指出此 Cmdlet 只會取得相依于指定服務的服務。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

以字串陣列指定要抓取之服務的顯示名稱。 允許使用萬用字元。

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
此參數的值會限定 **Name** 參數。 輸入名稱元素或模式，例如 `s*` 。 允許使用萬用字元。

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

以字串陣列指定此 Cmdlet 在作業中包含的服務或服務。 此參數的值會限定 **Name** 參數。 輸入名稱元素或模式，例如 `s*` 。 允許使用萬用字元。

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

指定代表要抓取之服務的 **ServiceController** 物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。 您可以使用管線將服務物件傳送至此 Cmdlet。

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

指定要抓取之服務的服務名稱。 允許使用萬用字元。

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

指出此 Cmdlet 只會取得此服務所需的服務。 此參數會取得服務之 **ServicesDependedOn** 屬性的值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: False
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

從 PowerShell 6.0 開始，會將下列屬性新增至 **ServiceController** 物件： **UserName** 、 **Description** 、 **DelayedAutoStart** 、 **BinaryPathName** 和 **StartupType** 。

您也可以 `Get-Service` 使用內建的別名來參考 `gsv` 。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

只有當目前的使用者具有查看服務的許可權時，此 Cmdlet 才會顯示服務。 如果此 Cmdlet 未顯示服務，您可能沒有查看服務的許可權。

若要尋找您系統上每個服務的服務名稱和顯示名稱，請輸入 `Get-Service` 。 服務名稱會出現在 [名稱] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。

當您依 **Status** 屬性的值以遞增順序排序時，已停止的服務會在執行服務之前出現。 服務的 **status** 屬性是一個列舉值，而狀態名稱則代表整數值。 排序次序是以整數值為基礎，而不是名稱。 因為已停止的值為1，且執行的值為4，所以已停止。 如需詳細資訊，請參閱 [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus)。

## 相關連結

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
