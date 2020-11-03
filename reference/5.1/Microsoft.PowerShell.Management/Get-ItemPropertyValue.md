---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itempropertyvalue?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemPropertyValue
ms.openlocfilehash: 2dbbbfeac3810f79b976b6a68ab3089e91707fb3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203995"
---
# Get-ItemPropertyValue

## 概要
取得指定項目的一或多個屬性的值。

## SYNTAX

### 路徑 (預設值)

```
Get-ItemPropertyValue [[-Path] <String[]>] [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Get-ItemPropertyValue -LiteralPath <String[]> [-Name] <String[]> [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## DESCRIPTION

`Get-ItemPropertyValue`當您使用 *Name* 參數時，會取得您所指定之屬性的目前值（位於您以 *path* 或 *LiteralPath* 參數指定的路徑中）。

## 範例

### 範例 1︰取得 ProductID 屬性的值

此命令會取得 Windows 登錄提供者中 "\SOFTWARE\Microsoft\Windows NT\CurrentVersion" 物件的 **ProductID** 屬性值。

```powershell
Get-ItemPropertyValue 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion' -Name ProductID
```

```output
94253-50000-11141-AA785
```

### 範例 2︰取得檔案或資料夾的上次寫入時間

此命令會取得 **LastWriteTime** 屬性的值，或上次變更檔案或資料夾的時間，從 "C:\Users\Test\Documents\ModuleToAssembly" 資料夾，在 FileSystem 提供者中工作。

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime
```

```output
Wednesday, September 3, 2014 2:53:22 PM
```

### 範例 3︰取得檔案或資料夾的多個屬性值

此命令會取得資料夾的 **LastWriteTime** 、 **CreationTime** 和 **Root** 屬性的值。
屬性值會以您指定屬性名稱的順序傳回。

```powershell
Get-ItemPropertyValue -Path C:\Users\Test\Documents\ModuleToAssembly -Name LastWriteTime,CreationTime,Root
```

```output
Wednesday, September 3, 2014 2:53:22 PM
Wednesday, September 3, 2014 2:53:10 PM

Name              : C:\
Parent            :
Exists            : True
Root              : C:\
FullName          : C:\
Extension         :
CreationTime      : 9/1/2014 4:59:45 AM
CreationTimeUtc   : 9/1/2014 11:59:45 AM
LastAccessTime    : 9/27/2014 5:22:02 PM
LastAccessTimeUtc : 9/28/2014 12:22:02 AM
LastWriteTime     : 9/27/2014 5:22:02 PM
LastWriteTimeUtc  : 9/28/2014 12:22:02 AM
Attributes        : Hidden, System, Directory
BaseName          : C:\
Target            :
LinkType          :
Mode              : d--hs-
```

## PARAMETERS

### -Credential

指定具有執行此動作權限的使用者帳戶。
預設為目前使用者。

輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。
若您輸入使用者名稱時，會提示您輸入密碼。

> [!WARNING]
> 與 Windows PowerShell 一起安裝的任何提供者皆不支援此參數。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

以字串陣列指定此 Cmdlet 在作業中排除的項目。
此參數的值會限定 **Path** 參數。
輸入路徑元素或模式，例如 "*.txt"。
允許使用萬用字元。

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

以提供者的格式或語言指定篩選。
此參數的值會限定 **Path** 參數。

篩選的語法 (包括是否使用萬用字元) 取決於提供者。
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

### -Include

以字串陣列指定此 Cmdlet 在作業中納入的項目。
此參數的值會限定 **Path** 參數。
輸入路徑元素或模式，例如 "*.txt"。
允許使用萬用字元。

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

指定屬性之目前位置的路徑。
與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。
沒有字元會被視為萬用字元。
如果路徑包含逸出字元，請將它括在單引號中。
單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要抓取之一或多個屬性的名稱。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定一或多個項目的路徑。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseTransaction

將命令加入使用中交易。
只有交易為處理中狀態時，此參數才有效。
如需詳細資訊，請參閱 about_Transactions。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

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

### System.Boolean、System.String、System.DateTime

此 Cmdlet 對於取得的每個項目屬性值會傳回一個物件。
物件類型取決於所抓取的屬性值。
例如，在檔案系統磁碟機中，此 Cmdlet 可能會傳回檔案或資料夾。

## 注意

此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出您的會話中可用的提供者，請執行 `Get-PSProvider` Cmdlet。 如需詳細資訊，請參閱 about_Providers。

## 相關連結

[Get-ItemProperty](Get-ItemProperty.md)

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)

[Get-PSProvider](Get-PSProvider.md)
