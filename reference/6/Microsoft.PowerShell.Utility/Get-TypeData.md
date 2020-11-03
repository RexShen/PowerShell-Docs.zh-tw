---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: 33df0697420249c8a35c792ca71f80c96efaafb7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204603"
---
# Get-TypeData

## 概要
取得目前工作階段中的延伸類型資料。

## 語法

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## 描述

`Get-TypeData`Cmdlet 會取得目前會話中的延伸類型資料。 這包括依檔案新增到會話的類型資料 `Types.ps1xml` ，以及使用 Cmdlet 的參數新增的動態類型資料 `Update-TypeData` 。

您可以使用傳回的延伸類型資料 `Get-TypeData` 來檢查會話中的類型資料，並將其傳送至 `Update-TypeData` 和 `Remove-TypeData` Cmdlet。

延伸類型資料會將屬性和方法新增至 PowerShell 中的物件。 您可以比照使用物件類型中定義之屬性和方法的方式，來使用新增的屬性和方法。 不過，在撰寫腳本時，請注意，新增的屬性和方法可能不會出現在每個 PowerShell 會話中。

如需檔案的詳細資訊 `Types.ps1xml` ，請參閱 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)。 如需 Cmdlet 新增之動態類型資料的詳細資訊 `Update-TypeData` ，請參閱 `Update-TypeData` 。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：取得所有延伸類型資料

這個範例會取得目前會話中的所有延伸類型資料。

 ```powershell
Get-TypeData
```

### 範例2：依名稱取得類型

這個範例會取得目前會話中名稱包含事件的所有類型。

 ```powershell
"*Eventing*" | Get-TypeData
```

```Output
TypeName                                                  Members
--------                                                  -------
System.Diagnostics.Eventing.Reader.EventLogConfiguration  {}System.Diagnostics.Eventing.Reader.EventLogRecord
                                                          {}System.Diagnostics.Eventing.Reader.ProviderMetadata
                                                          {[ProviderName, System.Management.Automation.Runspaces.AliasProper...
```

### 範例3：取得用來建立屬性值的腳本區塊

這個範例會取得腳本區塊，以建立 **EventLogEntry** 物件之 **EventID** 屬性的值。

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### 範例4：取得定義指定物件之屬性的腳本區塊

這個範例會取得腳本區塊，以定義 PowerShell 中 system.string **物件的** **datetime** 屬性。

 ```powershell
(Get-TypeData -TypeName System.DateTime).Members["DateTime"].GetScriptBlock
if ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq  "Date") {
    "{0}" -f $this.ToLongDateString()
}
elseif ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq "Time") {
    "{0}" -f  $this.ToLongTimeString()
}
else {
    "{0} {1}" -f $this.ToLongDateString(), $this.ToLongTimeString()
}
```

此命令會使用 `Get-TypeData` Cmdlet 來取得 **DataTime** 類型的延伸類型資料。 此命令取得 **TypeData** 物件的 **Members** 屬性。

**Members** 屬性包含由延伸類型資料所定義之屬性和方法的雜湊表。 Members 雜湊表中的每個索引鍵都是一個屬性或方法的名稱，而每個值則是該屬性或方法值的定義。

此命令會取得 **成員** 及其 **GetScriptBlock** 屬性值中的 **日期時間** 索引鍵。

輸出會顯示腳本區塊，此區塊會在 PowerShell 中 **建立每個** system.string 物件的 **datetime** 屬性值。

## 參數

### -TypeName

只針對具有指定名稱的類型，將類型資料指定為數組。 依預設，會 `Get-TypeData` 取得會話中的所有類型。

請輸入類型名稱或名稱模式。 即使是 System 命名空間中的類型，還是需要具有萬用字元的完整名稱或名稱模式。 支援萬用字元，且參數名稱 **TypeName** 是選擇性的。 您也可以透過管道將類型名稱傳送至 `Get-TypeData` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以用管線將類型名稱傳送至 `Get-TypeData` 。

## 輸出

### System.Management.Automation.Runspaces.TypeData

## 備忘稿

`Get-TypeData` 只取得目前會話中的延伸類型資料。 它不會取得已在電腦上但尚未新增至目前工作階段的延伸類型資料，例如尚未匯入目前工作階段之模組中定義的延伸類型。

## 相關連結

[about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Remove-TypeData](Remove-TypeData.md)

[Update-TypeData](Update-TypeData.md)
