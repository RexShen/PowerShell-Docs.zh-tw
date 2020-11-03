---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/group-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Group-Object
ms.openlocfilehash: f430dd1f9d9f820dda88ba5ad40023650204604d
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205984"
---
# Group-Object

## 概要
將包含指定屬性之相同值的物件分組。

## SYNTAX

### 雜湊表

```
Group-Object [-NoElement] [-AsHashTable] [-AsString] [-InputObject <PSObject>]
 [[-Property] <Object[]>] [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## DESCRIPTION

此 `Group-Object` Cmdlet 會根據指定屬性的值，在群組中顯示物件。
`Group-Object` 傳回資料表，其中每個屬性值都有一個資料列，以及顯示具有該值之專案數目的資料行。

如果您指定一個以上的屬性，請 `Group-Object` 先依第一個屬性的值將它們分組，然後在每個屬性群組內，依下一個屬性的值分組。

## 範例

### 範例1：依副檔名群組檔案

此範例會以遞迴方式取得中的檔案 `$PSHOME` ，並依副檔名將它們分組。 輸出會傳送至 `Sort-Object` Cmdlet，以針對指定的延伸模組找到的計數檔案進行排序。 空白 **名稱** 代表目錄。

此範例使用 **NoElement** 參數來省略群組的成員。

```powershell
$files = Get-ChildItem -Path $PSHOME -Recurse
$files | Group-Object -Property extension -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  365 .xml
  231 .cdxml
  197
  169 .ps1xml
  142 .txt
  114 .psd1
   63 .psm1
   49 .xsd
   36 .dll
   15 .mfl
   15 .mof
...
```

### 範例2：依機率和 evens 分組整數

此範例顯示如何使用腳本區塊做為 **Property** 參數的值。 此命令會顯示從1到20的整數，並依機率和甚至來分組。

```powershell
1..20 | Group-Object -Property {$_ % 2}
```

```Output
Count Name                      Group
----- ----                      -----
   10 0                         {2, 4, 6, 8...}
   10 1                         {1, 3, 5, 7...}
```

### 範例3：依 >entrytype 分組事件記錄檔事件

此範例會在系統事件記錄檔中顯示1000最新的專案，並依 **>entrytype** 分組。

在輸出中， **Count** 資料行代表每個群組中的專案數。 [ **名稱** ] 資料行代表定義群組的 **事件** 類型值。 **群組** 資料行代表每個群組中的物件。

```powershell
Get-WinEvent -LogName System -MaxEvents 1000 | Group-Object -Property LevelDisplayName
```

```Output
Count Name          Group
----- ----          -----
  153 Error         {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  722 Information   {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
  125 Warning       {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics...}
```

### 範例4：依優先權類別分組進程

此範例示範 **NoElement** 參數的效果。 這些命令會依優先順序類別將電腦上的處理程序分組。

第一個命令會使用 `Get-Process` Cmdlet 取得電腦上的處理常式，並將物件沿著管線向下傳送。 `Group-Object`依進程的 **PriorityClass** 屬性值將物件分組。

第二個範例會使用 **NoElement** 參數來消除輸出中群組的成員。 結果是只有 **Count** 和 **Name** 屬性值的資料表。

結果顯示在下列範例輸出中。

```powershell
Get-Process | Group-Object -Property PriorityClass
```

```Output
Count Name         Group
----- ----         -----
   55 Normal       {System.Diagnostics.Process (AdtAgent), System.Diagnosti...
    1              {System.Diagnostics.Process (Idle)}
    3 High         {System.Diagnostics.Process (Newproc), System.Diagnostic...
    2 BelowNormal  {System.Diagnostics.Process (winperf),
```

```powershell
Get-Process | Group-Object -Property PriorityClass -NoElement
```

```Output
Count Name
----- ----
   55 Normal
    1
    3 High
    2 BelowNormal
```

### 範例5：依名稱分組進程

下列範例會使用 `Group-Object` 來群組在本機電腦上執行的多個處理常式實例。 `Where-Object` 顯示具有一個以上實例的進程。

```powershell
Get-Process | Group-Object -Property Name -NoElement | Where-Object {$_.Count -gt 1}
```

```Output
Count Name
----- ----
2     csrss
5     svchost
2     winlogon
2     wmiprvse
```

### 範例6：雜湊表中的群組物件

這個範例會使用 **AsHashTable** 和 **AsString** 參數，以索引鍵/值組的集合傳回雜湊表中的群組。

在產生的雜湊表中，每個屬性值為索引鍵，而群組元素為值。
因為每個索引鍵是雜湊表物件的屬性，您可以使用點標記法來顯示值。

第一個命令會取得 `Get` `Set` 會話中的和 Cmdlet、依動詞將這些指令程式分組、以雜湊表傳回群組，然後將雜湊表儲存在 `$A` 變數中。

第二個命令會顯示中的雜湊表 `$A` 。 有兩個索引鍵/值組，一個用於 `Get` Cmdlet，另一個用於 `Set` Cmdlet。

第三個命令使用點標記法， `$A.Get` 在中顯示 **Get** 索引鍵的值 `$A` 。 這些值為 **CmdletInfo** 物件。 **AsString** 參數不會將群組中的物件轉換成字串。

```powershell
$A = Get-Command Get-*, Set-* -CommandType cmdlet | Group-Object -Property Verb -AsHashTable -AsString
$A
```

```Output
Name     Value
----     -----
Get      {Get-Acl, Get-Alias, Get-AppLockerFileInformation, Get-AppLockerPolicy...}
Set      {Set-Acl, Set-Alias, Set-AppBackgroundTaskResourcePolicy, Set-AppLockerPolicy...}
```

```powershell
$A.Get
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Cmdlet          Get-Acl                            6.1.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-Alias                          6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-AuthenticodeSignature          6.1.0.0    Microsoft.PowerShell.Security
Cmdlet          Get-ChildItem                      6.1.0.0    Microsoft.PowerShell.Management
...
```

## PARAMETERS

### -AsHashTable

指出此 Cmdlet 會以雜湊表傳回群組。 雜湊表的索引鍵為屬性值，會以其為依據進行物件分組。 雜湊表的值是具有該屬性值的物件。

**AsHashTable** 參數本身會傳回每一個雜湊表，其中每個索引鍵都是群組物件的實例。 搭配 **AsString** 參數使用時，雜湊表中的索引鍵為字串。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: AHT

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsString

指出此 Cmdlet 會將雜湊表索引鍵轉換成字串。 依預設，雜湊表索引鍵是群組物件的執行個體。 只有搭配 **AsHashTable** 參數使用時，此參數才有效。

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

### -CaseSensitive

指出此 Cmdlet 會讓群組區分大小寫。 如果沒有這個參數，群組中物件的屬性值可能大小寫會有不同。

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

### -Culture

指定比較字串時要使用的文化特性。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要分組的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

當您使用 **InputObject** 參數將物件集合提交至時，會 `Group-Object` `Group-Object` 收到一個代表集合的物件。 如此一來，它會建立該物件做為其成員的單一群組。

若要將集合中的物件分組，請使用管線將物件傳送至 `Group-Object` 。

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

### -NoElement

指出此 Cmdlet 會從結果中省略群組的成員。

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

### -Property

指定要分組的屬性。 物件會依據指定屬性的值進行分組。

**Property** 參數的值可以是新的計算屬性。 計算的屬性可以是腳本區塊或雜湊表。 有效的索引鍵/值組為：

- 運算式 `<string>` 或 `<script block>`

如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管線將任何物件傳送至 `Group-Object` 。

## 輸出

### Microsoft.PowerShell.Commands.GroupInfo 或 System.Collections.Hashtable

當您使用 **AsHashTable** 參數時，會傳回 `Group-Object` **Hashtable** 物件。
否則，它會傳回 **GroupInfo** 物件。

## 注意

您可以使用格式化 Cmdlet （例如和）的 **GroupBy** 參數 `Format-Table` `Format-List` 來群組物件。 與不同的是，它會建立每個屬性值各有 `Group-Object` 一個資料列的單一資料表，而 **GroupBy** 參數會為每個屬性值建立一個資料表，其中每個具有屬性值的專案都會有一個資料列。

`Group-Object` 不需要分組的物件為相同的 Microsoft .NET Core 類型。 將不同 .NET Core 類型的物件分組時，會 `Group-Object` 使用下列規則：

- 相同的屬性名稱和類型。

  如果物件具有具有指定名稱的屬性，且屬性值有相同的 .NET Core 類型，則會使用相同類型之物件所使用的相同規則將屬性值分組。

- 相同的屬性名稱，不同的類型。

  如果物件具有具有指定名稱的屬性，但是屬性值在不同的物件中有不同的 .NET Core 型別，則 `Group-Object` 會使用第一次出現之屬性的 .Net core 型別做為該屬性群組的 .Net core 型別。 當物件具有含不同類型的屬性時，屬性值會轉換為該群組的類型。 如果類型轉換失敗，則物件不會包含在群組中。

- 遺漏屬性。

  沒有指定屬性的物件無法群組。 未分組的物件會顯示在名為的群組中的最後一個 **GroupInfo** 物件輸出中 `AutomationNull.Value` 。

## 相關連結

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
