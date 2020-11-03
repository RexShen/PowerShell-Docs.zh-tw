---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/limit-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Limit-EventLog
ms.openlocfilehash: 3ec3214103dc6151e148f7482b0be8b821871e3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203619"
---
# Limit-EventLog

## 概要
設定限制事件記錄檔大小和其項目存留期的事件記錄檔屬性。

## SYNTAX

```
Limit-EventLog [-LogName] <String[]> [-ComputerName <String[]>] [-RetentionDays <Int32>]
 [-OverflowAction <OverflowAction>] [-MaximumSize <Int64>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Limit-EventLog** Cmdlet 會設定傳統事件記錄檔的大小上限、每個事件必須保留多久，以及當記錄檔到達大小上限時，會發生什麼事。
您可以使用它來限制本機電腦或遠端電腦上的事件記錄檔。

包含 EventLog 名詞 (EventLog Cmdlet) 的 Cmdlet 只能用於傳統事件記錄檔。
在 Windows Vista 和更新版本的 Windows 中，若要從使用「Windows 事件記錄檔」技術的記錄檔中取得事件，請使用 Get-WinEvent。

## 範例

### 範例1：增加事件記錄檔的大小

```
PS C:\> Limit-EventLog -LogName "Windows PowerShell" -MaximumSize 20KB
```

此命令將本機電腦上 Windows PowerShell 事件記錄檔的大小上限增加到 20480 位元組 (20 KB)。

### 範例2：保留指定期間的事件記錄檔

```
PS C:\> Limit-EventLog -LogName Security -ComputerName "Server01", "Server02" -RetentionDays 7
```

此命令會確保將 Server01 和 Server02 電腦上 Security 事件記錄檔中的事件至少保留 7 天。

### 範例3：變更所有事件記錄檔的溢位動作

```
PS C:\> $Logs = Get-EventLog -List | ForEach {$_.log}
PS C:\> Limit-EventLog -OverflowAction OverwriteOlder -LogName $Logs
PS C:\> Get-EventLog -List

Max(K) Retain OverflowAction     Entries  Log
------ ------ --------------     -------  ---
15,168      0 OverwriteOlder       3,412  Application
512         0 OverwriteOlder           0  DFS Replication
512         0 OverwriteOlder          17  DxStudio
10,240      7 OverwriteOlder           0  HardwareEvents
512         0 OverwriteOlder           0  Internet Explorer
512         0 OverwriteOlder           0  Key Management Service
16,384      0 OverwriteOlder           4  ODiag
16,384      0 OverwriteOlder         389  OSession Security
15,168      0 OverwriteOlder      19,360  System
15,360      0 OverwriteOlder      15,828  Windows PowerShell
```

此範例會將本機電腦上所有事件記錄檔的溢位動作變更為 OverwriteOlder。

第一個命令取得本機電腦上所有記錄檔的記錄檔名稱。
第二個命令設定溢位動作。
第三個命令顯示結果。

## PARAMETERS

### -ComputerName
指定遠端電腦。
預設是本機電腦。

輸入 NetBIOS 名稱、網際網路通訊協定 (IP) 位址，或遠端電腦 (FQDN) 的完整功能變數名稱。
若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。

此參數不必依賴 Windows PowerShell 遠端功能。
即使您的電腦未設定為執行遠端命令，您也可以使用 **Limit-EventLog** 的 *ComputerName* 參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumSize
指定事件記錄檔的大小上限 (單位為位元組)。
輸入介於 64 KB 到 4 GB 之間的值。
此值必須可被 64 KB (65536) 整除。

此參數會指定代表傳統事件記錄檔之 system.string **物件的** **MaximumKilobytes** 屬性值。

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OverflowAction
指定當事件記錄檔達到大小上限時要採取的動作。

此參數可接受的值為：

- DoNotOverwrite：保留現有的項目並捨棄新的項目。
- OverwriteAsNeeded：每個新項目皆覆寫最舊的項目。
- OverwriteOlder：新的事件會覆寫早于 **MinimumRetentionDays** 屬性所指定之值的事件。 如果沒有早于 **MinimumRetentionDays** 屬性值所指定的事件，則會捨棄新的事件。

此參數會指定代表傳統事件記錄檔之 system.string **物件的** **OverflowAction** 屬性值。

```yaml
Type: System.Diagnostics.OverflowAction
Parameter Sets: (All)
Aliases: OFA
Accepted values: OverwriteOlder, OverwriteAsNeeded, DoNotOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RetentionDays
指定事件必須保留在事件記錄檔中的天數下限。

此參數會指定代表傳統事件記錄檔之 system.string **物件的** **MinimumRetentionDays** 屬性值。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: MRD

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
此 Cmdlet 不會產生任何輸出。

## 注意

* 若要在 Windows Vista 和更新版本的 Windows 上使用此 Cmdlet，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。

  此 Cmdlet 會變更代表傳統事件記錄檔之 **system.string 物件的屬性。**
若要查看事件記錄檔屬性的目前設定，請輸入 `Get-EventLog -List` 。

*

## 相關連結

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
