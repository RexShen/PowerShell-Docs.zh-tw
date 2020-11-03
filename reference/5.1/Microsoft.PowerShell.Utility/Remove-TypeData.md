---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 5ba104eb3183916891d9fbf560dac2ecc4a9f6b6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203155"
---
# Remove-TypeData

## 概要
從目前的工作階段刪除延伸類型。

## Syntax

### RemoveTypeDataSet (預設值)

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RemoveTypeSet

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RemoveFileSet

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Remove-TypeData`Cmdlet 會從目前的會話刪除延伸類型資料。 此 Cmdlet 只會影響目前的工作階段和在目前工作階段中建立的工作階段。

您可以藉由在命令和檔案中定義來將屬性和方法新增至 PowerShell 中的物件 `Update-TypeData` `Types.ps1xml` 。 `Remove-TypeData` 從目前的會話刪除這些擴充屬性和方法。 `Remove-TypeData` 不會刪除檔案，也不會 `Types.ps1xml` 刪除檔案中的任何延伸類型定義 `Types.ps1xml` 。 如需檔案的詳細資訊 `Types.ps1xml` ，請參閱 [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md)。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例 1︰移除指定類型的類型資料

此範例會從會話中刪除 system.string **類型的所有類型資料** ，包括檔案所新增的類型資料， `Types.ps1xml` 以及使用指令程式新增至會話的動態類型資料 `Update-TypeData` 。

```powershell
Remove-TypeData -TypeName System.Array
```

### 範例 2︰從工作階段移除延伸的資料類型

此範例顯示從會話移除延伸類型資料的效果。 第一個會 `Get-TypeData` 取得 system.string 類型的延伸 **System.DateTime** 類型資料。 輸出顯示已將 **DateTime** 屬性新增至 PowerShell 中 **的所有 system.string 物件。** Cmdlet 會傳回 `Get-Date` **system.object** 物件。 此命令會使用點標記法來取得傳回之 **system.string 物件的** **datetime** 屬性值 `Get-Date` 。

```powershell
Get-TypeData System.DateTime
(Get-Date).DateTime
Get-TypeData System.DateTime | Remove-TypeData
(Get-Date).DateTime
```

```Output
TypeName        Members
--------        -------
System.DateTime {[DateTime, System.Management.Automation.Runspaces.ScriptPropertyData]}

Friday, January 20, 2012 9:01:00 PM
```

下一個指令程式 `Get-TypeData` 可取得 system.string 類型的所有延伸 **System.DateTime** 類型資料，以及 Cmdlet 用來 `Remove-TypeData` 刪除延伸類型資料的管道。 最後一個 `Get-Date` Cmdlet 會顯示刪除 system.string 類型之延伸類型資料的效果 **System.DateTime** 。 因為 system.string **屬性不再** 存在，所以取得其值的命令不會傳回任何內容。

### 範例 3︰移除模組的延伸類型

此範例會移除模組物件的所有延伸類型資料。 當您使用管線將物件傳送至時 `Remove-TypeData` ，會 `Remove-TypeData` 取得物件類型的名稱，並移除該類型所有物件的所有類型資料。

```powershell
Get-Module | Remove-TypeData
```

### 範例 4︰移除指定模組的延伸類型

此範例會使用 Cmdlet 的 **Path** 參數 `Remove-TypeData` ，移除 `Types.ps1xml` **PSScheduledJob** 和 **PSWorkflow** 模組所新增之檔案中定義的延伸類型。 此命令不會影響使用 Cmdlet 新增的動態類型資料 `Update-TypeData` 。 只有在模組已經匯入目前的工作階段時，命令才會成功。

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

如需模組的詳細資訊，請參閱 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。

### 範例 5：從遠端工作階段移除延伸類型

此範例會從遠端會話移除延伸類型。 此命令會使用 `Invoke-Command` Cmdlet 來移除變數中會話內所有 CIM 類型的延伸類型資料 `$S` 。

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## 參數

### -Path

指定此 Cmdlet 要從工作階段刪除延伸類型資料之檔案的陣列。 這是必要參數。

輸入一或多個檔案的路徑和檔案名 `Types.ps1xml` 。 不支援萬用字元。 若省略路徑，則預設位置為目前目錄。

```yaml
Type: System.String[]
Parameter Sets: RemoveFileSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeData

指定此 Cmdlet 要從工作階段中刪除的類型資料。 這是必要參數。 輸入包含 **TypeData** 物件的變數， ( **TypeData** ) ，或輸入可取得 **TypeData** 物件的命令，例如 `Get-TypeData` 命令。 您也可以透過管線將 **TypeData** 物件傳送至 `Remove-TypeData` 。

```yaml
Type: System.Management.Automation.Runspaces.TypeData
Parameter Sets: RemoveTypeDataSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -TypeName

指定此 Cmdlet 要刪除所有延伸類型資料的類型。 對於系統命名空間中的類型，請輸入簡短名稱。 否則，需要完整類型名稱。 不支援萬用字元。

您可以用管線將類型名稱傳送至 `Remove-TypeData` 。 當您使用管線將物件傳送至時 `Remove-TypeData` ，會 `Remove-TypeData` 取得物件的類型名稱，並移除物件類型的所有類型資料。

```yaml
Type: System.String
Parameter Sets: RemoveTypeSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

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

### System.Management.Automation.Runspaces.TypeData

您可以透過管線將 **TypeData** 物件（例如 Cmdlet 所傳回的物件）傳送 `Get-TypeData` 至 `Remove-TypeData` 。

### System.String

您可以透過管道將類型名稱傳送至 `Remove-TypeData` 。 當您使用管線將物件傳送至時 `Remove-TypeData` ，會 `Remove-TypeData` 取得物件的類型名稱，並移除物件類型的所有類型資料。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 備忘稿

`Remove-TypeData` 只能移除目前會話中的延伸類型資料。 它無法移除已在電腦上但尚未新增至目前工作階段的延伸類型資料，例如尚未匯入目前工作階段之模組中定義的延伸類型。

## 相關連結

[Get-TypeData](Get-TypeData.md)

[Update-TypeData](Update-TypeData.md)
