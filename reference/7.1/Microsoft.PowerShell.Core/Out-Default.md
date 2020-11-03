---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: c1293b93079fed439c42d6ba41747cbe6a0c33fe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205004"
---
# Out-Default

## 概要
將輸出傳送到預設的格式器和預設的輸出 Cmdlet。

## SYNTAX

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

PowerShell 會自動加入 `Out-Default` 至每個管線的結尾。 `Out-Default` 決定如何格式化和輸出物件資料流程。 如果物件資料流程是字串資料流程，請 `Out-Default` 直接將這些物件傳送至，以 `Out-Host` 呼叫主機提供的適當 api。 如果物件資料流程不包含字串，會 `Out-Default` 檢查物件以判斷要執行的動作。
首先，它會查看物件類型，並判斷是否有此物件類型的已註冊 _view_ 。

PowerShell 會 (Cmdlet 定義 XML 架構和機制， `Update-FormatData`) 可讓任何人註冊物件類型的視圖。 您可以針對任何物件類型指定 **寬型** 、 **清單** 、 **表格** 或 **自訂** 的視圖。 這些視圖會指定要顯示的屬性，以及應如何顯示這些屬性。 如果已註冊某個視圖，它會定義要使用的格式器。 因此，如果已註冊的視圖是 **資料表** 視圖，則會將 `Out-Default` 物件串流至 `Format-Table | Out-Host` 。 `Format-Table` 將物件轉換成格式記錄的資料流程， (由 view 定義) 中的資料所驅動，然後將 `Out-Host` 格式化記錄轉換為主機介面上的呼叫。

## 範例

### 範例 1

雖然這個 Cmdlet 不會直接由使用者執行，但它可以是。

```powershell
Get-Process | Select-Object -First 5 | Out-Default
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     12     2.56       5.20       0.00    7376   0 aesm_service
     48    34.32      18.10      26.64    9320  13 AlertusDesktopAlert
     24    13.97      12.74       0.77   12656  13 ApplicationFrameHost
      8     1.79       4.41       0.00    8180   0 AppVShNotify
      9     1.99       5.07       0.19   19320  13 AppVShNotify
```

## PARAMETERS

### -InputObject

接受 Cmdlet 的輸入。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -文字記錄

判斷是否應將輸出傳送至 PowerShell 的轉譯服務。

```yaml
Type: System.Management.Automation.SwitchParameter
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

## 輸出

## 注意

## 相關連結

[Format-Custom](../Microsoft.PowerShell.Utility/Format-Custom.md)

[Format-List](../Microsoft.PowerShell.Utility/Format-List.md)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Format-Wide](../Microsoft.PowerShell.Utility/Format-Wide.md)

[about_Format.ps1xml](About/about_Format.ps1xml.md)

[PowerShell 格式化和輸出的實際運作方式](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)

