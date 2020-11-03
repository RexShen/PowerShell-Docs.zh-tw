---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-ControlPanelItem
ms.openlocfilehash: 368e385d51437f9ac93b700c929b185dce30a644
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203488"
---
# Show-ControlPanelItem

## 概要
開啟控制台項目。

## SYNTAX

### RegularName (預設值)

```
Show-ControlPanelItem [-Name] <String[]> [<CommonParameters>]
```

### CanonicalName

```
Show-ControlPanelItem -CanonicalName <String[]> [<CommonParameters>]
```

### ControlPanelItem

```
Show-ControlPanelItem [[-InputObject] <ControlPanelItem[]>] [<CommonParameters>]
```

## DESCRIPTION

`Show-ControlPanelItem`Cmdlet 會開啟本機電腦上的控制台專案。 您可以使用它來依名稱、類別或描述來開啟控制台專案，即使在沒有使用者介面的系統上也一樣。 您可以透過管線將控制台專案從 `Get-ControlPanelItem` Cmdlet 傳送至 `Show-ControlPanelItem` 。

`Show-ControlPanelItem` 只會搜尋可在系統上開啟的控制台專案。 在沒有 **主控台** 或 **檔案總管** 的電腦上， `Show-ControlPanelItem` 只會搜尋可在沒有這些元件的情況下開啟的控制台專案。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進，並可在 Windows 8、Windows Server 2012 和更新版本上運作。

## 範例

### 範例1：顯示控制台專案

此範例會啟動 [ **自動播放** ] 控制台專案。

```powershell
Show-ControlPanelItem -Name "AutoPlay"
```

### 範例2：使用管線將控制台專案輸送至此 Cmdlet

此範例會在本機電腦上開啟 **Windows Defender 防火牆** 控制台專案。
Windows 防火牆控制台專案的名稱已在 Windows 版本中變更。 這個範例會使用萬用字元模式來尋找 [控制台] 專案。

```powershell
Get-ControlPanelItem -Name "*Firewall" | Show-ControlPanelItem
```

`Get-ControlPanelItem` 取得 [控制台] 專案，而 `Show-ControlPanelItem` Cmdlet 會開啟該專案。

### 範例 3：使用檔案名稱來開啟控制台項目

此範例會使用應用程式名稱來開啟 [ **程式和功能** ] 控制台專案。

```powershell
appwiz.cpl
```

這個方法是使用命令的替代方法 `Show-ControlPanelItem` 。

> [!NOTE]
> 在 PowerShell 中，您可以省略控制台檔案的 cpl 副檔名，因為它包含在環境變數的值中 `$env:PathExt` 。

## PARAMETERS

### -CanonicalName

使用指定的正式名稱或名稱模式來指定 [控制台] 專案。 允許使用萬用字元。 如果您輸入多個名稱，此 Cmdlet 會開啟符合任何名稱的 [控制台] 專案，如同 [名稱] 清單中的專案是以 **OR** 運算子分隔。

```yaml
Type: System.String[]
Parameter Sets: CanonicalName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

藉由提交 [控制台專案] 物件，指定要開啟的控制台專案。 輸入包含控制台專案物件的變數，或輸入可取得控制台專案物件的命令或運算式，例如 `Get-ControlPanelItem` 。

```yaml
Type: Microsoft.PowerShell.Commands.ControlPanelItem[]
Parameter Sets: ControlPanelItem
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定控制台專案的名稱。 允許使用萬用字元。 如果您輸入多個名稱，此 Cmdlet 會開啟符合任何名稱的 [控制台] 專案，如同 [名稱] 清單中的專案是以 **OR** 運算子分隔。

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.string、傳送至 get-controlpanelitem、。

您可以使用管線將名稱或控制台專案物件傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 注意

## 相關連結

[Get-ControlPanelItem](Get-ControlPanelItem.md)
