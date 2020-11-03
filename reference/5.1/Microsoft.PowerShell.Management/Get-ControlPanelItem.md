---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-controlpanelitem?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ControlPanelItem
ms.openlocfilehash: 51bc04b4de901a611330266b6b0f58471f998432
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204024"
---
# Get-ControlPanelItem

## 概要
取得控制台項目。

## SYNTAX

### RegularName (預設值)

```
Get-ControlPanelItem [[-Name] <String[]>] [-Category <String[]>] [<CommonParameters>]
```

### CanonicalName

```
Get-ControlPanelItem -CanonicalName <String[]> [-Category <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-ControlPanelItem`Cmdlet 會取得本機電腦上的控制台專案。 您可以用它來依據名稱、類別或描述來尋找控制台項目，即使在沒有使用者介面的系統上也可以。

此 Cmdlet 只會取得可在系統上開啟的控制台專案。 在沒有主控台或檔案總管的電腦上，此 Cmdlet 只會取得可在沒有這些元件的情況下開啟的控制台專案。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。 它只適用于 Windows 8 和 Windows Server 2012 和更新版本。

## 範例

### 範例 1：取得所有控制台項目

此命令會取得本機電腦上的所有控制台項目。

```powershell
Get-ControlPanelItem
```

```Output
Name                          CanonicalName                 Category                      Description
----                          -------------                 --------                      -----------
Action Center                 Microsoft.ActionCenter        {System and Security}         Review recent messages and...
Administrative Tools          Microsoft.AdministrativeTools {System and Security}         Configure administrative s...
AutoPlay                      Microsoft.AutoPlay            {Hardware}                    Change default settings fo...
BitLocker Drive Encryption    Microsoft.BitLockerDriveEn... {System and Security}         Protect your computer usin...
Color Management              Microsoft.ColorManagement     {All Control Panel Items}     Change advanced color mana...
Credential Manager            Microsoft.CredentialManager   {User Accounts}               Manage your Windows Creden...
Date and Time                 Microsoft.DateAndTime         {Clock, Language, and Region} Set the date, time, and ti...
...
```

### 範例 2：依名稱取得控制台項目

此範例會取得名稱中有程式或應用程式的控制台專案。

```powershell
Get-ControlPanelItem -Name "*Program*", "*App*"
```

### 範例 3：依類別取得控制台項目

此命令會取得名稱中具有安全性之類別目錄中的所有控制台專案。

```powershell
Get-ControlPanelItem -Category "*Security*"
```

### 範例 4：開啟控制台項目

此範例會開啟本機電腦上的 Windows 防火牆控制台專案。

```powershell
Get-ControlPanelItem -Name "Windows Firewall" | Show-ControlPanelItem
```

`Get-ControlPanelItem`Cmdlet 會取得 [控制台] 專案。 `Show-ControlPanelItem`Cmdlet 會將其開啟。

### 範例 5：取得遠端電腦上的控制台項目

此範例會取得 Server01 遠端電腦上的 BitLocker 磁碟機加密控制台專案。
`Invoke-Command`Cmdlet 會 `Get-ControlPanelItem` 從遠端執行 Cmdlet。

```powershell
Invoke-Command -ComputerName "Server01" {Get-ControlPanelItem -Name "BitLocker*" }
```

### 範例 6：搜尋控制台項目的描述

此範例會搜尋控制台專案的 **Description** 屬性，只取得包含名稱 **裝置** 的專案。

```powershell
Get-ControlPanelItem | Where-Object {$_.Description -like "*Device*"}
```

```Output
Name                    CanonicalName                 Category    Description
----                    -------------                 --------    -----------
AutoPlay                Microsoft.AutoPlay            {Hardware}  Change default settings fo...
Devices and Printers    Microsoft.DevicesAndPrinters  {Hardware}  View and manage devices, p...
Sound                   Microsoft.Sound               {Hardware}  Configure your audio devic...
```

`Get-ControlPanelItem`Cmdlet 會取得所有的控制台專案。 此 `Where-Object` Cmdlet 會依 **Description** 屬性的值篩選項目。

## PARAMETERS

### -CanonicalName

依此 Cmdlet 取得的標準名稱或名稱模式，以字串陣列的形式指定控制台專案。 允許使用萬用字元。 如果您輸入多個名稱，此 Cmdlet 會取得符合任何名稱的控制台專案，如同名稱清單中的專案是以 "or" 運算子分隔。

根據預設，此 Cmdlet 會取得系統中的所有控制台專案。

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

### -Category

以字串陣列指定此 Cmdlet 取得之指定類別中的 [控制台] 專案類別。 輸入類別名稱或名稱模式。 允許使用萬用字元。 如果您輸入多個名稱，此 Cmdlet 會取得符合任何名稱的控制台專案，如同名稱清單中的專案是以 "or" 運算子分隔。 根據預設，此 Cmdlet 會取得系統中的所有控制台專案。

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

### -Name

以字串陣列指定此 Cmdlet 取得之控制台的名稱或名稱模式。
允許使用萬用字元。 您也可以使用管線將名稱或名稱模式傳送至此 Cmdlet。

```yaml
Type: System.String[]
Parameter Sets: RegularName
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將名稱或名稱模式傳送至此 Cmdlet。

## 輸出

### Microsoft.PowerShell.Commands.ControlPanelItem

此 Cmdlet 會取得本機電腦上的控制台專案。

## 注意

## 相關連結

[Show-ControlPanelItem](Show-ControlPanelItem.md)
