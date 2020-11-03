---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/write-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-EventLog
ms.openlocfilehash: cae34c4cf942d9aa4abb9a2d716ef9854f70de2e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203435"
---
# Write-EventLog

## 概要
將事件寫入事件記錄檔。

## SYNTAX

```
Write-EventLog [-LogName] <String> [-Source] <String> [[-EntryType] <EventLogEntryType>] [-Category <Int16>]
 [-EventId] <Int32> [-Message] <String> [-RawData <Byte[]>] [-ComputerName <String>] [<CommonParameters>]
```

## DESCRIPTION
**寫入 EventLog** Cmdlet 會將事件寫入事件記錄檔。

若要將事件寫入事件記錄檔，事件記錄檔必須存在於電腦上，並且必須為事件記錄檔登錄來源。

包含 **eventlog** 名詞 ( **eventlog** Cmdlet 的指令程式) 只會在傳統事件記錄檔上運作。
在 Windows Vista 和更新版本的 Windows 作業系統中，若要從使用「Windows 事件記錄檔」技術的記錄檔中取得事件，請使用 Get-WinEvent Cmdlet。

## 範例

### 範例 1︰將事件寫入應用程式事件記錄檔

```
PS C:\> Write-EventLog -LogName "Application" -Source "MyApp" -EventID 3001 -EntryType Information -Message "MyApp added a user-requested feature to the display." -Category 1 -RawData 10,20
```

此命令將事件從 MyApp 來源寫入 Application 事件記錄檔。

### 範例 2︰將事件寫入遠端電腦的應用程式事件記錄檔

```
PS C:\> Write-EventLog -ComputerName "Server01" -LogName Application -Source "MyApp" -EventID 3001 -Message "MyApp added a user-requested feature to the display."
```

此命令將事件從 MyApp 來源寫入 Server01 遠端電腦上的 Application 事件記錄檔。

## PARAMETERS

### -Category
指定事件的工作類別。
輸入與事件記錄檔之類別訊息檔案中的字串關聯的整數。

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

### -ComputerName
指定遠端電腦。
預設是本機電腦。

輸入遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。

此參數不必依賴 Windows PowerShell 遠端功能。
即使您的電腦未設定為執行遠端命令，您仍然可以使用 Get-EventLog Cmdlet 的 *ComputerName* 參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EntryType
指定事件的項目類型。
這個參數可接受的值如下︰Error、Warning、Information、SuccessAudit 和 FailureAudit。
預設值為 Information。

如需這些值的描述，請參閱 MSDN library 中的 [EventLogEntryType 列舉](https://go.microsoft.com/fwlink/?LinkId=143599) 。

```yaml
Type: System.Diagnostics.EventLogEntryType
Parameter Sets: (All)
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EventId
指定事件識別碼。
這是必要參數。
適用於 *EventId* 參數的最大值為 65535。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ID, EID

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName
指定要在其中寫入事件之記錄檔的名稱。
輸入記錄檔名稱。
記錄檔名稱是 **Log** 屬性的值，而不是 **LogDisplayName** 的值。
不允許使用萬用字元。
這是必要參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Message
指定事件訊息。
這是必要參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MSG

Required: True
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RawData
指定與事件關聯的二進位資料 (單位為位元組)。

```yaml
Type: System.Byte[]
Parameter Sets: (All)
Aliases: RD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source
指定事件來源，這通常是正在將事件寫入記錄檔之應用程式的名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無
您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.Diagnostics.EventLogEntry
這個 Cmdlet 會傳回代表記錄檔中事件的物件。

## 注意

* 若要使用 **Write-EventLog** ，請使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。

*

## 相關連結

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
