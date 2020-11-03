---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-EventLog
ms.openlocfilehash: 695a13d4fbbf60caadeed994c1aa9c36432be917
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204068"
---
# Clear-EventLog

## 概要
清除本機或遠端電腦上指定之事件記錄檔中的所有專案。

## SYNTAX

```
Clear-EventLog [-LogName] <String[]> [[-ComputerName] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Clear-EventLog`Cmdlet 會刪除本機電腦或遠端電腦上指定之事件記錄檔中的所有專案。
若要使用 `Clear-EventLog` ，您必須是受影響電腦上 Administrators 群組的成員。

包含 **eventlog** 名詞 (eventlog Cmdlet 的指令程式) 只會在傳統事件記錄檔上運作。
若要在 Windows Vista 和更新版本的 Windows 中，從使用 Windows 事件記錄檔技術的記錄檔中取得事件，請使用 Get-WinEvent Cmdlet。

## 範例

### 範例1：清除本機電腦上的特定事件記錄檔類型

```powershell
Clear-EventLog "Windows PowerShell"
```

此命令會清除本機電腦上 Windows PowerShell 事件記錄檔中的專案。

### 範例2：清除本機和遠端電腦上的特定多個記錄類型

```powershell
Clear-EventLog -LogName ODiag, OSession -ComputerName localhost, Server02
```

此命令會清除 Microsoft Office 診斷 (ODiag) 中的所有專案，以及 Microsoft Office 會話 (OSession) 本機電腦和 Server02 遠端電腦上的記錄。

### 範例3：清除指定電腦上的所有記錄，然後顯示事件記錄檔清單

```powershell
Clear-EventLog -LogName application, system -confirm
```

此命令會在刪除指定的事件記錄檔中的項目之前提示您確認。

### 範例4：清除指定電腦上的所有記錄，然後顯示事件記錄檔清單

```powershell
function clear-all-event-logs ($computerName="localhost")
{
   $logs = Get-EventLog -ComputerName $computername -List | ForEach-Object {$_.Log}
   $logs | ForEach-Object {Clear-EventLog -ComputerName $computername -LogName $_ }
   Get-EventLog -ComputerName $computername -list
}

clear-all-event-logs -ComputerName Server01
```

```Output
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded           0 Application
15,168      0 OverwriteAsNeeded           0 DFS Replication
512         7 OverwriteOlder              0 DxStudio
20,480      0 OverwriteAsNeeded           0 Hardware Events
512         7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
16,384      0 OverwriteAsNeeded           0 Microsoft Office Diagnostics
16,384      0 OverwriteAsNeeded           0 Microsoft Office Sessions
30,016      0 OverwriteAsNeeded           1 Security
15,168      0 OverwriteAsNeeded           2 System
15,360      0 OverwriteAsNeeded           0 Windows PowerShell
```

此函式會清除指定電腦上的所有事件記錄檔，然後顯示操作結果的事件記錄檔清單。

請注意，在清除記錄檔之後有一些項目加入「系統」和「安全性」記錄檔，而加入的時間是在顯示記錄檔之前。

## PARAMETERS

### -ComputerName

指定遠端電腦。
預設是本機電腦。

輸入遠端電腦的 NetBIOS 名稱、網際網路通訊協定 (IP) 位址或完整網域名稱。
若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 "localhost"。

此參數不必依賴 Windows PowerShell 遠端功能。
**ComputerName** `Get-EventLog` 即使您的電腦未設定為執行遠端命令，您也可以使用 ComputerName 參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LogName

指定事件記錄檔。
輸入一或多個事件記錄檔的記錄檔名稱 (Log 屬性的值，而不是 LogDisplayName)，並使用逗號區隔。
不允許使用萬用字元。
這是必要參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### 無

您無法透過管道傳送物件至 `Clear-EventLog` 。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

- 若要使用 `Clear-EventLog` Windows Vista 和更新版本的 windows，請使用 [以系統管理員身分執行] 選項開始 Windows PowerShell。

## 相關連結

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
