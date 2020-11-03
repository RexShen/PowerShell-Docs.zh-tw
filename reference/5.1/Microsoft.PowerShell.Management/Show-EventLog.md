---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-EventLog
ms.openlocfilehash: e8dbcf1aa4280c0481714a8a9fb24f2e5ef79ffe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203491"
---
# Show-EventLog

## 概要
在 [事件檢視器] 中顯示本機或遠端電腦的事件記錄檔。

## SYNTAX

```
Show-EventLog [[-ComputerName] <String>] [<CommonParameters>]
```

## DESCRIPTION
**Show-EventLog** Cmdlet 會在本機電腦上開啟事件檢視器，並在本機電腦或遠端電腦上顯示所有傳統事件記錄檔。

在 Windows Vista 或更新版本的 Windows 作業系統中，若要開啟 [事件檢視器]，則目前的使用者必須是本機電腦上 Administrators 群組的成員。

包含 **eventlog** 名詞 ( **eventlog** Cmdlet 的指令程式) 只會在傳統事件記錄檔上運作。
在 Windows Vista 和更新版本的 Windows 作業系統中，若要從使用「Windows 事件記錄檔」技術的記錄檔中取得事件，請使用 Get-WinEvent Cmdlet。

## 範例

### 範例 1︰顯示本機電腦的事件記錄檔

```
PS C:\> Show-EventLog
```

此命令會開啟 [事件檢視器]，並顯示本機電腦上的傳統事件記錄檔。

### 範例 2︰顯示遠端電腦的事件記錄檔

```
PS C:\> Show-EventLog -ComputerName "Server01"
```

此命令會開啟 [事件檢視器]，並顯示 Server01 電腦上的傳統事件記錄檔。

## PARAMETERS

### -ComputerName
指定遠端電腦。
**Show-EventLog** 會顯示本機電腦上事件檢視器中指定電腦的事件記錄檔。
預設是本機電腦。

輸入遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。

此參數不必依賴 Windows PowerShell 遠端功能。
即使您的電腦未設定為執行遠端命令，您仍然可以使用 *ComputerName* 參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 0
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

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

* [事件檢視器] 一開啟，Windows PowerShell 命令提示字元就會傳回。 您可以在 [事件檢視器] 開啟時於目前的工作階段中工作。

  因為此 Cmdlet 需要使用者介面，它無法在 Windows Server 的 Server Core 安裝上使用。

*

## 相關連結

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[New-EventLog](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Write-EventLog](Write-EventLog.md)
