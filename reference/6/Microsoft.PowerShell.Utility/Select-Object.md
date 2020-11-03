---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 11aedd0f5249153e01382132c9eeb95f0717cda3
ms.sourcegitcommit: f9ae48d026d65833b9c8ca881058dda0bbd067b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "93206331"
---
# Select-Object

## 概要
選取物件或物件屬性。

## SYNTAX

### DefaultParameter (預設) 

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### SkipLastParameter

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### IndexParameter

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

### SkipIndexParameter

```
Select-Object [-InputObject <PSObject>] [-Unique] [-SkipIndex <Int32[]>] [<CommonParameters>]
```

## DESCRIPTION

`Select-Object`Cmdlet 會選取物件或物件集合的指定屬性。 它也可以選取唯一物件、指定數目的物件，或位於陣列中指定位置的物件。

若要從集合選取物件，請使用 **First** 、 **Last** 、 **Unique** 、 **Skip** 及 **Index** 參數。 若要選取物件屬性，請使用 **Property** 參數。 當您選取 [屬性] 時，會傳回 `Select-Object` 只具有指定屬性的新物件。

從 Windows PowerShell 3.0 開始， `Select-Object` 包含優化功能，可防止命令建立及處理未使用的物件。

當您 `Select-Object` 在命令管線中包含具有 **First** 或 **Index** 參數的命令時，PowerShell 會在所選物件數目產生時立即停止產生物件的命令，即使在管線的命令之前出現產生物件的命令 `Select-Object` 。 若要關閉此最佳化行為，請使用 **Wait** 參數。

## 範例

### 範例1：依屬性選取物件

這個範例會建立物件，而這些物件的 **名稱** 、 **識別碼** 及工作集 ( **WS** ) 處理常式物件的屬性。

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### 範例2：依屬性選取物件並設定結果格式

此範例會取得電腦上處理常式所使用之模組的相關資訊。 它會使用 `Get-Process` Cmdlet 來取得電腦上的處理常式。

它會使用 `Select-Object` Cmdlet 來輸出實例的陣列， `[System.Diagnostics.ProcessModule]` 如每個實例輸出的 **模組** 屬性中所包含 `System.Diagnostics.Process` `Get-Process` 。

Cmdlet 的 **Property** 參數會 `Select-Object` 選取處理常式名稱。 這會將 `ProcessName` **NoteProperty** 加入至每個 `[System.Diagnostics.ProcessModule]` 實例，並在其中填入目前進程的 **ProcessName** 屬性值。

最後， `Format-List` Cmdlet 會用來顯示清單中每個處理常式的名稱和模組。

```powershell
Get-Process Explorer | Select-Object -Property ProcessName -ExpandProperty Modules | Format-List
```

```Output
ProcessName       : explorer
ModuleName        : explorer.exe
FileName          : C:\WINDOWS\explorer.exe
BaseAddress       : 140697278152704
ModuleMemorySize  : 3919872
EntryPointAddress : 140697278841168
FileVersionInfo   : File:             C:\WINDOWS\explorer.exe
                    InternalName:     explorer
                    OriginalFilename: EXPLORER.EXE.MUI
                    FileVersion:      10.0.17134.1 (WinBuild.160101.0800)
                    FileDescription:  Windows Explorer
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.17134.1
...
```

### 範例3：使用最多記憶體選取進程

這個範例會取得使用最多記憶體的五個處理常式。 `Get-Process`Cmdlet 會取得電腦上的處理常式。 指令程式會 `Sort-Object` 根據記憶體 (工作集) 使用方式來排序處理常式，而此 `Select-Object` Cmdlet 只會選取產生之物件陣列的最後五個成員。

包含 Cmdlet 的命令中不需要 **Wait** 參數， `Sort-Object` 因為會 `Sort-Object` 處理所有物件，然後傳回集合。 `Select-Object`優化只適用于在處理時個別傳回物件的命令。

```powershell
Get-Process | Sort-Object -Property WS | Select-Object -Last 5
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VS(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
2866     320       33432      45764   203   222.41   1292 svchost
577      17        23676      50516   265    50.58   4388 WINWORD
826      11        75448      76712   188    19.77   3780 Ps
1367     14        73152      88736   216    61.69    676 Ps
1612     44        66080      92780   380   900.59   6132 INFOPATH
```

### 範例4：選取陣列中的唯一字元

這個範例使用的 **unique** 參數 `Select-Object` ，從字元陣列取得唯一字元。

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### 範例5：在事件記錄檔中選取最新和最舊的事件

此範例會取得 Windows PowerShell 事件記錄檔中的第一個 (最新) 和最後 (最舊的) 事件。

`Get-EventLog` 取得 Windows PowerShell 記錄檔中的所有事件，並將它們儲存在 `$a` 變數中。
然後， `$a` 會透過管道傳送至 `Select-Object` Cmdlet。 此 `Select-Object` 命令會使用 **Index** 參數，從變數中的事件陣列選取事件 `$a` 。 第一個事件的索引為 0。 最後一個事件的索引是減1的專案數目 `$a` 。

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### 範例6：選取第一個物件以外的所有物件

這個範例會在 Servers.txt 檔案中列出的每一部電腦上建立新的 PSSession，除了第一部電腦之外。

`Select-Object` 選取電腦名稱稱清單中的所有電腦，但不選取第一部電腦。 產生的電腦清單會設定為 Cmdlet 的 **ComputerName** 參數值 `New-PSSession` 。

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### 範例7：重新命名檔案，然後選取多個以進行審核

此範例會將 "-ro" 尾碼新增至具有唯讀屬性之文字檔的基底名稱，然後顯示前五個檔案，讓使用者可以看到效果的範例。

`Get-ChildItem` 使用 **ReadOnly** 動態參數來取得唯讀檔案。 產生的檔案會以管道傳送至 `Rename-Item` Cmdlet，以重新命名檔案。 它使用的 **Passthru** 參數將重新 `Rename-Item` 命名的檔案傳送至 `Select-Object` Cmdlet，此 Cmdlet 會選取前5個來顯示。

的 **Wait** 參數 `Select-Object` 會防止 PowerShell 在 `Get-ChildItem` 取得前五個唯讀文字檔之後停止 Cmdlet。 在沒有此參數的情況下，只會重新命名前五個唯讀檔案。

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### 範例8：示範-ExpandProperty 參數的複雜

此範例示範 **ExpandProperty** 參數的複雜。

請注意，產生的輸出是實例的陣列 `[System.Int32]` 。 實例符合 **輸出視圖** 的標準格式化規則。 這適用于任何 *展開* 的屬性。 如果輸出的物件具有特定的標準格式，則可能不會顯示展開的屬性。

```powershell
# Create a custom object to use for the Select-Object example.
$object = [pscustomobject]@{Name="CustomObject";Expand=@(1,2,3,4,5)}
# Use the ExpandProperty parameter to Expand the property.
$object | Select-Object -ExpandProperty Expand -Property Name
```

```Output
1
2
3
4
5
```

```powershell
# The output did not contain the Name property, but it was added successfully.
# Use Get-Member to confirm the Name property was added and populated.
$object | Select-Object -ExpandProperty Expand -Property Name | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType   Definition
----        ----------   ----------
CompareTo   Method       int CompareTo(System.Object value), int CompareTo(int value), int IComparable.CompareTo(System.Object obj)...
Equals      Method       bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int].Equals(int other)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
GetTypeCode Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar      Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime  Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal   Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble    Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16     Method       int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32     Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64     Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte     Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle    Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString    Method       string ToString(), string ToString(string format), string ToString(System.IFormatProvider provider)...
ToType      Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16    Method       uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32    Method       uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64    Method       uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
Name        NoteProperty string Name=CustomObject
```

### 範例9：在物件上建立自訂屬性

下列範例示範如何使用將 `Select-Object` 自訂屬性加入至任何物件。
當您指定不存在的屬性名稱時，會 `Select-Object` 將該屬性建立為每個傳遞之物件上的 **NoteProperty** 。

```powershell
$customObject = 1 | Select-Object -Property MyCustomProperty
$customObject.MyCustomProperty = "New Custom Property"
$customObject
```

```Output
MyCustomProperty
----------------
New Custom Property
```

### 範例10：為每個 InputObject 建立計算屬性

這個範例示範 `Select-Object` 如何使用，將計算屬性加入至您的輸入。 將 **ScriptBlock** 傳遞給 **Property** 參數會導致 `Select-Object` 在每個傳遞的物件上評估運算式，並將結果新增至輸出。 在 **ScriptBlock** 內，您可以使用 `$_` 變數來參考管線中的目前物件。

依預設， `Select-Object` 會使用 **ScriptBlock** 字串做為屬性的名稱。 使用 **雜湊表** ，您可以將 **ScriptBlock** 的輸出標記為新增至每個物件的自訂屬性。 您可以將多個計算屬性加入至傳遞給的每個物件 `Select-Object` 。

```powershell
# Create a calculated property called $_.StartTime.DayOfWeek
Get-Process | Select-Object -Property ProcessName,{$_.StartTime.DayOfWeek}
```

```Output
ProcessName  $_.StartTime.DayOfWeek
----         ----------------------
alg                       Wednesday
ati2evxx                  Wednesday
ati2evxx                   Thursday
...
```

```powershell
# Add a custom property to calculate the size in KiloBytes of each FileInfo object you pass in.
# Use the pipeline variable to divide each file's length by 1 KiloBytes
$size = @{label="Size(KB)";expression={$_.length/1KB}}
# Create an additional calculated property with the number of Days since the file was last accessed.
# You can also shorten the key names to be 'l', and 'e', or use Name instead of Label.
$days = @{l="Days";e={((Get-Date) - $_.LastAccessTime).Days}}
# You can also shorten the name of your label key to 'l' and your expression key to 'e'.
Get-ChildItem $PSHOME -File | Select-Object Name, $size, $days
```

```Output
Name                        Size(KB)        Days
----                        --------        ----
Certificate.format.ps1xml   12.5244140625   223
Diagnostics.Format.ps1xml   4.955078125     223
DotNetTypes.format.ps1xml   134.9833984375  223
```

## PARAMETERS

### -ExcludeProperty

指定此 Cmdlet 從作業中排除的屬性。 允許使用萬用字元。

從 PowerShell 6 開始，不再需要包含 **Property** 參數， **ExcludeProperty** 才能運作。

```yaml
Type: System.String[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ExpandProperty

請指定要選取的屬性，並指示應嘗試延伸該屬性。

- 如果指定的屬性是陣列，則陣列的每個值都會包含在輸出中。
- 如果指定的屬性是物件，則會針對每個 **InputObject** 展開物件屬性

無論是哪一種情況，輸出物件的 **類型** 都將符合展開屬性的 **類型** 。

如果指定了 **Property** 參數， `Select-Object` 將會嘗試將每個選取的屬性新增為每個輸出物件的 **NoteProperty** 。

> [!WARNING]
> 如果您收到錯誤：因為屬性已存在，所以無法處理 Select： Property `<PropertyName>` ，請考慮下列事項。
> 請注意，使用時 `-ExpandProperty` ， `Select-Object` 不能取代現有的屬性。
> 這表示：
>
> - 如果展開的物件具有相同名稱的屬性，就會發生錯誤。
> - 如果 *選取* 的物件具有與 *展開* 物件屬性相同名稱的屬性，就會發生錯誤。

```yaml
Type: System.String
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -First

指定要從輸入物件陣列開始位置選取的物件數。

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Index

依據物件的索引值從陣列選取物件。 在使用逗號區隔的清單中輸入索引。 陣列中的索引是以 0 開始，其中 0 代表第一個值，(n-1) 則代表最後一個值。

```yaml
Type: System.Int32[]
Parameter Sets: IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要透過管線傳送給 Cmdlet 的物件。 此參數可讓您將物件輸送至 `Select-Object` 。

當您將物件傳遞給 **inputobject** 參數時（而不是使用管線）， `Select-Object` 會將 **InputObject** 視為單一物件（即使值是集合）。 建議您在將集合傳遞至時，使用管線 `Select-Object` 。

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

### -Last

指定要從輸入物件陣列結束位置選取的物件數。

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Property

指定要選取的屬性。 這些屬性會以 **NoteProperty** 成員的形式新增至輸出物件。 允許使用萬用字元。

**Property** 參數的值可以是新的計算屬性。 若要建立計算的屬性，請使用雜湊表。

有效索引鍵為：

- 名稱 (或標籤) - `<string>`
- 運算式 `<string>` 或 `<script block>`

如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Skip

略過 (不選取) 指定的項目數。 根據預設， **Skip** 參數會從物件陣列或清單的開頭開始計算，但是如果命令使用 **最後一個** 參數，就會從清單或陣列的結尾算起。

與從 0 位置開始計算的 **Index** 參數不同， **Skip** 參數會從 1 開始。

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipLast

略過 (不會從清單或陣列的結尾選取) 指定數目的專案。 的運作方式與使用 **Skip** 搭配 **Last** 參數的方式相同。

不同于從0開始計算的 **Index** 參數， **SkipLast** 參數會從1開始。

```yaml
Type: System.Int32
Parameter Sets: SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Unique

指定當輸入物件的子集具有完全相同的屬性與值，將只會選取子集的一個成員。

此參數區分大小寫。 因此，只有字元大小寫不同的字串會被視為唯一的字串。

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

### -Wait

指出此 Cmdlet 會關閉優化。 PowerShell 會以命令在命令管線中出現的循序執行命令，並讓它們產生所有物件。 根據預設，如果您 `Select-Object` 在命令管線中包含具有 **First** 或 **Index** 參數的命令，則 PowerShell 會在產生選取的物件數目時，停止產生物件的命令。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultParameter, IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipIndex

```yaml
Type: System.Int32[]
Parameter Sets: SkipIndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管線將任何物件傳送至 `Select-Object` 。

## 輸出

### System.Management.Automation.PSObject

## 注意

- 您也可以 `Select-Object` 使用它的內建別名來參考 Cmdlet `select` 。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

- 的優化功能 `Select-Object` 僅適用于在處理管線時將物件寫入至管線的命令。 它對緩衝已處理之物件的命令沒有效果，並且會將它們以集合的方式寫入。 立即寫入物件是 Cmdlet 設計最佳做法。 如需詳細資訊，請參閱以 [強烈建議的開發指導方針](/powershell/scripting/developer/windows-powershell)，將 _單一記錄寫入管線_ 。

## 相關連結

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Group-Object](Group-Object.md)

[Sort-Object](Sort-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
