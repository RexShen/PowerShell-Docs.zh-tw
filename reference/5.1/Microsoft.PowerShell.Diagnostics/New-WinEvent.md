---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 202d1792769dcdcda7a156621bfc50c89a1a92ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202260"
---
# New-WinEvent

## 概要

為指定的事件提供者建立新的 Windows 事件。

## SYNTAX

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## DESCRIPTION

**New-WinEvent** Cmdlet 會為事件提供者建立 Windows 事件追蹤 (ETW) 事件。
您可以使用這個 Cmdlet，從 Windows PowerShell 將事件新增到 ETW 通道。

## 範例

### 範例 1

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

這個命令會使用 **New-WinEvent** Cmdlet，針對 Microsoft-Windows-PowerShell 提供者建立事件 45090。

## PARAMETERS

### -Id

指定透過工具資訊清單登錄的事件識別碼。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Payload

指定事件的訊息。 將事件寫入事件記錄檔時，承載會儲存於事件物件的 **Message** 屬性中。

當指定的承載不符合事件定義中的承載時，Windows PowerShell 會產生警告，但命令仍會成功。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

指定將事件寫入事件記錄檔的事件提供者，例如 "Microsoft-Windows-PowerShell"。 ETW 事件提供者是將事件寫入 ETW 工作階段的邏輯實體。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version

指定事件的版本號碼。 輸入事件編號。 Windows PowerShell 會將此數字轉換成所需的 Byte 類型。

這個參數可讓您在定義相同事件的不同版本時指定事件。

```yaml
Type: System.Byte
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

此 Cmdlet 不接受來自管線的輸入。

## 輸出

### 無

此 Cmdlet 會產生輸出。

## 注意

* 當提供者將事件寫入事件記錄檔之後，您可以使用 Get-WinEvent Cmdlet 從事件記錄檔取得事件。

## 相關連結

[Get-WinEvent](Get-WinEvent.md)
