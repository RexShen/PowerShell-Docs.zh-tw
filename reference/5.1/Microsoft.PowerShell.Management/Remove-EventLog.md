---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-EventLog
ms.openlocfilehash: 4cf29146727c9a54715459a2d56e47a27c5bacc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203564"
---
# Remove-EventLog

## 概要
刪除事件記錄檔或取消註冊事件來源。

## SYNTAX

### Default (預設值)

```
Remove-EventLog [[-ComputerName] <String[]>] [-LogName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 來源

```
Remove-EventLog [[-ComputerName] <String[]>] [-Source <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Remove-EventLog** Cmdlet 會從本機或遠端電腦中刪除事件記錄檔，並取消註冊記錄檔的所有事件來源。
您也可以使用這個 Cmdlet 來取消註冊事件來源，而不刪除任何事件記錄檔。

包含 **eventlog** 名詞（ **eventlog** Cmdlet）的 Cmdlet 只適用于傳統的事件記錄檔。
在 Windows Vista 和更新版本的 Windows 作業系統中，若要從使用「Windows 事件記錄檔」技術的記錄檔中取得事件，請使用 Get-WinEvent。

注意：這個 Cmdlet 可以刪除作業系統事件記錄檔，這樣可能導致應用程式失敗和非預期的系統行為。

## 範例

### 範例 1︰從本機電腦中移除事件記錄檔

```
PS C:\> Remove-EventLog -LogName "MyLog"
```

此命令會從本機電腦刪除 MyLog 事件記錄檔，並取消註冊其事件來源。

### 範例 2︰從幾部電腦中移除事件記錄檔

```
PS C:\> Remove-EventLog -LogName "MyLog", "TestLog" -ComputerName "Server01", "Server02", "localhost"
```

此命令會從本機電腦與 Server01 和 Server02 遠端電腦中刪除 MyLog 和 TestLog 事件記錄檔。
此命令也會取消註冊這些記錄檔的事件來源。

### 範例 3︰刪除事件來源

```
PS C:\> Remove-EventLog -Source "MyApp"
```

此命令會從本機電腦上的記錄檔刪除 MyApp 事件來源。
當命令完成時，MyApp 程式無法寫入任何事件記錄檔。

### 範例 4︰移除事件記錄檔，然後確認動作

```
The first command lists the event logs on the local computer.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
15,168      7 OverwriteAsNeeded          12 ZapLog

The second command deletes the ZapLog event log.
PS C:\> Remove-EventLog -LogName "ZapLog"

The third command lists the event logs again. The ZapLog event log no longer appears in the list.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
```

這些命令會顯示如何列出電腦上的事件記錄檔，並確認已成功 **移除 EventLog** 命令。

### 範例 5︰移除事件來源，然後確認動作

```
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'" | foreach {$_.sources}
MyApp
TestApp
PS C:\> Remove-Eventlog -Source "MyApp"
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'"} | foreach {$_.sources}
TestApp
```

這些命令使用 Get-WmiObject Cmdlet，列出本機電腦上的事件來源。
您可以使用這些命令來確認命令成功與否或刪除事件來源。

第一個命令會取得本機電腦上 TestLog 事件記錄檔的事件來源。
MyApp 是其中一個來源。

第二個命令會使用 **Remove-EventLog** 的 *Source* 參數來刪除 MyApp 事件來源。

第三個命令與第一個命令相同。
它會顯示已刪除 MyApp 事件來源 。

## PARAMETERS

### -ComputerName
指定遠端電腦。
預設是本機電腦。

輸入遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。
若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。

此參數不必依賴 Windows PowerShell 遠端功能。
您可以使用 **Remove-EventLog** 的 *ComputerName* 參數，即使您的電腦未設定為執行遠端命令也一樣。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName
指定事件記錄檔。
輸入一或多個事件記錄檔的記錄檔名稱，並使用逗號區隔。
記錄檔名稱是 **Log** 屬性的值，而非 *LogDisplayName* ，不允許使用萬用字元。
這是必要參數。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source
指定此 Cmdlet 取消註冊的事件來源。
輸入來源名稱 (不是可執行檔名稱)，並使用逗號區隔。

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: SRC

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
您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### 無
此 Cmdlet 不會傳回任何輸出。

## 注意

* 若要在 Windows Vista 和更新版本的 Windows 作業系統上使用 **Remove-EventLog** ，請使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。

  如果您移除事件記錄檔，然後重新建立記錄檔，您將無法註冊相同的事件來源。
使用事件來源將項目寫入原始記錄檔的應用程式，將無法寫入新的記錄檔。

* 當您取消註冊特定記錄檔的事件來源時，事件來源可能無法在其他事件記錄檔中寫入項目。

## 相關連結

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
