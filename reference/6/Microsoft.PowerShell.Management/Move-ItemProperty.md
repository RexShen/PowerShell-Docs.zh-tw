---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-ItemProperty
ms.openlocfilehash: 235991da33ae49f8d1dd9b379432963a8930ebc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202879"
---
# Move-ItemProperty

## 概要
將屬性從某個位置移動到另一個位置。

## SYNTAX

### 路徑 (預設值)

```
Move-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Move-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Destination] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

`Move-ItemProperty`Cmdlet 會將專案的屬性從某個專案移到另一個專案。
例如，它可以將登錄專案從一個登錄機碼移至另一個登錄機碼。
當您移動項目屬性後，就會將它加到新位置，並從其原始位置中刪除。

## 範例

### 範例1：將登錄值和其資料移至另一個金鑰

此命令會將 Version 登錄值和其資料從 "MyApp" 子機碼移至登錄機碼的 NewApp 子機 `HKLM\Software\MyCompany` 碼。

```powershell
Move-ItemProperty "HKLM:\Software\MyCompany\MyApp" -Name "Version" -Destination "HKLM:\Software\MyCompany\NewApp"
```

## PARAMETERS

### -Credential

> [!NOTE]
> 使用 PowerShell 安裝的任何提供者都不支援此參數。
> 若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Destination

指定目的地位置的路徑。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

以字串陣列指定此 Cmdlet 在作業中排除的專案。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt`。 允許使用萬用字元。 只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。

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

### -Filter

指定要限定 **路徑** 參數的篩選準則。 [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。 您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。
篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

強制執行命令而不要求使用者確認。
實作會依提供者而異。
如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Include

以字串陣列指定此 Cmdlet 在作業中納入的項目。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `"*.txt"`。 允許使用萬用字元。 **Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。

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

### -LiteralPath

指定一個或多個位置的路徑。 **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要移動之屬性的名稱。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

傳回代表您正在使用之項目的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

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

### -Path

指定屬性之目前位置的路徑。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
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

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至此 Cmdlet。

## 輸出

### 無或 System.Management.Automation.PSCustomObject

當您使用 **PassThru** 參數時，此 Cmdlet 會產生代表已移動之專案屬性的 **PSCustomObject** 。 否則，此 Cmdlet 不會產生任何輸出。

## 注意

此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
