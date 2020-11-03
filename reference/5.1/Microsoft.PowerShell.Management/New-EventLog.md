---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-EventLog
ms.openlocfilehash: 61fafc0670a24fd6ca057e4cf0c7179d90446b07
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203596"
---
# New-EventLog

## 概要
在本機或遠端電腦上建立新的事件記錄檔和新的事件來源。

## SYNTAX

```
New-EventLog [-LogName] <string> [-Source] <string[]> [[-ComputerName] <string[]>]
  [-CategoryResourceFile <string>] [-MessageResourceFile <string>] [-ParameterResourceFile <string>]
  [<CommonParameters>]
```

## DESCRIPTION

這個 Cmdlet 會在本機或遠端電腦上建立新的傳統事件記錄檔。 它也可以登錄要寫入新記錄檔或現有記錄檔的事件來源。

包含事件記錄檔名詞 (事件記錄檔 Cmdlet) 的 Cmdlet 只適用於傳統的事件記錄檔。
若要在 Windows Vista 和更新版本的 Windows 中，從使用 Windows 事件記錄檔技術的記錄檔中取得事件，請使用 `Get-WinEvent` 。

## 範例

### 範例 1-建立新的事件記錄檔

這個命令在本機電腦上建立 TestLog 事件記錄檔，並為其登錄新來源。

```powershell
New-EventLog -source TestApp -LogName TestLog -MessageResourceFile C:\Test\TestApp.dll
```

### 範例 2-將新的事件來源新增至現有的記錄檔

這個命令將新的事件來源 (NewTestApp) 新增到 Server01 遠端電腦上的應用程式記錄檔。

```powershell
$file = "C:\Program Files\TestApps\NewTestApp.dll"
New-EventLog -ComputerName Server01 -Source NewTestApp -LogName Application -MessageResourceFile $file -CategoryResourceFile $file
```

這個命令要求 NewTestApp.dll 檔案必須位於 Server01 電腦上。

## PARAMETERS

### -CategoryResourceFile

指定包含來源事件類別字串的檔案路徑。 這個檔案也稱為「類別訊息檔案」。

這個檔案必須存在於建立事件記錄檔的電腦上。 這個參數不會建立或移動檔案。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

在指定的電腦上建立新的事件記錄檔。 預設是本機電腦。

遠端電腦的 NetBIOS 名稱、IP 位址或完整功能變數名稱。
若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 "localhost"。

此參數不依賴 PowerShell 遠端功能。 **ComputerName** `Get-EventLog` 即使您的電腦未設定為執行遠端命令，您也可以使用 ComputerName 參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 3
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

指定事件記錄檔的名稱。

如果記錄檔不存在，就會 `New-EventLog` 建立記錄檔，並針對新事件記錄檔的 **Log** 和 **LogDisplayName** 屬性使用此值。 如果記錄檔存在， `New-EventLog` 則為事件記錄檔登錄新的來源。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageResourceFile

指定包含來源事件訊息格式字串的檔案路徑。
這個檔案也稱為「事件訊息檔案」。

這個檔案必須存在於建立事件記錄檔的電腦上。
這個參數不會建立或移動檔案。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ParameterResourceFile

指定檔案的路徑，該檔案中包含事件說明中用來替換參數的字串。 這個檔案也稱為「參數訊息檔案」。

這個檔案必須存在於建立事件記錄檔的電腦上。
這個參數不會建立或移動檔案。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

指定事件記錄檔來源的名稱，例如，寫入事件記錄檔的應用程式。 這是必要參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 2
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

## 注意

若要使用 `New-EventLog` Windows Vista 和更新版本的 windows，請使用 [以系統管理員身分執行] 選項開啟 PowerShell。

若要在 Windows Vista、Windows XP Professional 或 Windows Server 2003 中建立事件來源，您必須是電腦上的 Administrators 群組成員。

當您建立新的事件記錄檔和新的事件來源時，系統會登錄新記錄檔的新來源，但直到將第一個項目寫入記錄檔時，才會建立該記錄檔。

作業系統會將事件記錄檔儲存為檔案。

當您建立新的事件記錄檔時，相關聯的檔案會儲存在 `$env:SystemRoot\System32\Config` 指定電腦上的目錄中。

檔案名為 **Log** 屬性的前八個字元，檔案名副檔名為 .evt。

## 相關連結

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Show-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
