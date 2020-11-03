---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compare-Object
ms.openlocfilehash: f7decea60b92dc3613eecc1726855c100a245524
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "93208891"
---
# Compare-Object

## 概要
比較兩個物件集。

## 語法

```
Compare-Object [-ReferenceObject] <PSObject[]> [-DifferenceObject] <PSObject[]>
 [-SyncWindow <Int32>] [-Property <Object[]>] [-ExcludeDifferent] [-IncludeEqual] [-PassThru]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## 描述

此 `Compare-Object` Cmdlet 會比較兩組物件。 其中一組物件是 **參考** ，而另一組物件則是 **差異** 。

`Compare-Object` 檢查是否有比較整個物件的可用方法。 如果找不到合適的方法，它會呼叫 **ToString ( # B1** 方法的輸入物件，並比較字串結果。 您可以提供要用於比較的一或多個屬性。 當提供屬性時，此 Cmdlet 只會比較這些屬性的值。

比較的結果會指出屬性值是否只出現在 **參考** 物件中 () ， `<=` 或只出現在 () 的 **差異** 物件中 `=>` 。 如果使用 **IncludeEqual** 參數， (`==`) 表示值是在這兩個物件中。

如果 **參考** 或 **差異** 物件 () 為 null，則會 `$null` `Compare-Object` 產生終止錯誤。

某些範例會使用展開來減少程式碼範例的行長度。 如需詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。

## 範例

### 範例 1-比較兩個文字檔的內容

此範例會比較兩個文字檔的內容。 此範例會使用下列兩個文字檔，其中每個值都在個別行上。

- `Testfile1.txt` 包含值：狗、squirrel 和鳥。
- `Testfile2.txt` 包含下列值：貓、鳥和 racoon。

輸出只會顯示檔案之間不同的行。 `Testfile1.txt` 這是 () 的 **參考** 物件 `<=` ，而 `Testfile2.txt` () 的 **差異** 物件 `=>` 。 不會顯示同時出現在這兩個檔案中的內容行。

```powershell
Compare-Object -ReferenceObject (Get-Content -Path C:\Test\Testfile1.txt) -DifferenceObject (Get-Content -Path C:\Test\Testfile2.txt)
```

```Output
InputObject SideIndicator
----------- -------------
cat         =>
racoon      =>
dog         <=
squirrel    <=
```

### 範例 2-比較每一行內容並排除差異

此範例使用 **ExcludeDifferent** 參數來比較兩個文字檔中每一行的內容。

從 PowerShell 7.1，使用 **ExcludeDifferent** 參數時，會推斷 **IncludeEqual** ，輸出只會包含兩個檔案中包含的行，如 **SideIndicator** () 所示 `==` 。

```powershell
$objects = @{
  ReferenceObject = (Get-Content -Path C:\Test\Testfile1.txt)
  DifferenceObject = (Get-Content -Path C:\Test\Testfile2.txt)
}
Compare-Object @objects -ExcludeDifferent
```

```Output
InputObject SideIndicator
----------- -------------
bird        ==
```

<a id="ex3" />

### 範例 3-使用 PassThru 參數顯示差異

通常會傳回 `Compare-Object` 具有下列屬性的 **PSCustomObject** 類型：

- 要比較的 **InputObject**
- **SideIndicator** 屬性，顯示輸出所屬的輸入物件

當您使用 **PassThru** 參數時，物件的 **型** 別不會變更，但所傳回物件的實例會有一個名為 **SideIndicator** 的新增 **NoteProperty** 。 **SideIndicator** 會顯示輸出所屬的輸入物件。

下列範例顯示不同的輸出類型。

```powershell
$a = $True
Compare-Object -IncludeEqual $a $a
(Compare-Object -IncludeEqual $a $a) | Get-Member
```

```Output
InputObject SideIndicator
----------- -------------
       True ==

   TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
InputObject   NoteProperty System.Boolean InputObject=True
SideIndicator NoteProperty string SideIndicator===
```

```powershell
Compare-Object -IncludeEqual $a $a -PassThru
(Compare-Object -IncludeEqual $a $a -PassThru) | Get-Member
```

```Output
True

   TypeName: System.Boolean
Name          MemberType   Definition
----          ----------   ----------
CompareTo     Method       int CompareTo(System.Object obj), int CompareTo(bool value), int IComparable.CompareTo(Syst
Equals        Method       bool Equals(System.Object obj), bool Equals(bool obj), bool IEquatable[bool].Equals(bool ot
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
GetTypeCode   Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean     Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte        Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar        Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime    Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal     Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble      Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16       Method       short IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32       Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64       Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte       Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle      Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString      Method       string ToString(), string ToString(System.IFormatProvider provider), string IConvertible.To
ToType        Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16      Method       ushort IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32      Method       uint IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64      Method       ulong IConvertible.ToUInt64(System.IFormatProvider provider)
TryFormat     Method       bool TryFormat(System.Span[char] destination, [ref] int charsWritten)
SideIndicator NoteProperty string SideIndicator===
```

使用 **PassThru** 時， **系統** 會傳回 (system.string) 的原始物件類型。 請注意，[system.string **] 物件的** 預設格式所顯示的輸出未顯示 [ **SideIndicator** ] 屬性。 不過 **，傳回的** system.string 物件具有加入的 **NoteProperty** 。

### 範例 4-使用屬性比較兩個簡單的物件

在此範例中，我們會比較兩個具有相同長度的不同字串。

```powershell
Compare-Object -ReferenceObject 'abc' -DifferenceObject 'xyz' -Property Length -IncludeEqual
```

```Output
Length SideIndicator
------ -------------
     3 ==
```

### 範例 5-使用屬性比較複雜物件

此範例顯示比較複雜物件時的行為。 在此範例中，我們會針對不同的 PowerShell 實例儲存兩個不同的處理常式物件。 這兩個變數都包含具有相同名稱的處理常式物件。 當比較物件但未指定 **Property** 參數時，此 Cmdlet 會將物件視為相等。 請注意， **InputObject** 的值與 **ToString ( # B1** 方法的結果相同。 由於 **system.object** 沒有 **IComparable** 介面，因此 Cmdlet 會將物件轉換成字串，然後比較結果。

```powershell
PS> Get-Process pwsh

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    101   123.32     139.10      35.81   11168   1 pwsh
     89   107.55      66.97      11.44   17600   1 pwsh

PS> $a = Get-Process -Id 11168
PS> $b = Get-Process -Id 17600
PS> $a.ToString()
System.Diagnostics.Process (pwsh)
PS> $b.ToString()
System.Diagnostics.Process (pwsh)
PS> Compare-Object $a $b -IncludeEqual

InputObject                       SideIndicator
-----------                       -------------
System.Diagnostics.Process (pwsh) ==

PS> Compare-Object $a $b -Property ProcessName, Id, CPU

ProcessName    Id       CPU SideIndicator
-----------    --       --- -------------
pwsh        17600   11.4375 =>
pwsh        11168 36.203125 <=
```

當您指定要比較的屬性時，此 Cmdlet 會顯示差異。

### 範例 6-比較執行 IComparable 的複雜物件

如果物件實作為 **IComparable** ，此 Cmdlet 會搜尋比較物件的方式。如果物件是不同的類型，則會將 **差異** 物件轉換成 **ReferenceObject** 的類型，然後再進行比較。

在此範例中，我們會比較字串與 **TimeSpan** 物件。 在第一種情況下，字串會轉換成 **TimeSpan** ，因此物件相等。

```powershell
Compare-Object ([TimeSpan]"0:0:1") "0:0:1" -IncludeEqual
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    ==
```

```powershell
Compare-Object "0:0:1" ([TimeSpan]"0:0:1")
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    =>
0:0:1       <=
```

在第二個案例中， **TimeSpan** 會轉換成字串，因此物件是不同的。

## 參數

### -CaseSensitive

指出比較應區分大小寫。

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

指定要用於比較的文化特性。

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

### -DifferenceObject

指定與 **參考** 物件比較的物件。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ExcludeDifferent

指出這個 Cmdlet 只會顯示相同物件的比較特性。 捨棄物件之間的差異。

使用 **ExcludeDifferent** 搭配 **IncludeEqual** ，只顯示 **參考** 和 **差異** 物件之間相符的行。

如果指定了 **ExcludeDifferent** 但沒有 **IncludeEqual** ，就不會有輸出。

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

### -IncludeEqual

**IncludeEqual** 會顯示 **參考** 和 **差異** 物件之間的相符專案。

根據預設，輸出也會包含 **參考** 和 **差異** 物件之間的差異。

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

### -PassThru

當您使用 **PassThru** 參數時，會 `Compare-Object` 省略比較物件周圍的 **PSCustomObject** 包裝函式，並傳回不同的物件（不變）。

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

指定要比較之 **參考** 和 **差異** 物件的屬性陣列。

**Property** 參數的值可以是新的計算屬性。 計算的屬性可以是腳本區塊或雜湊表。 有效的索引鍵/值組為：

- 運算式 `<string>` 或 `<script block>`

如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferenceObject

指定用來做為比較參考的物件陣列。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SyncWindow

指定 `Compare-Object` 在物件集合中尋找相符項時檢查的相鄰物件數目。 `Compare-Object` 當在集合中找不到相同位置的物件時，檢查連續的物件。 預設值是 `[Int32]::MaxValue` ，這表示會 `Compare-Object` 檢查整個物件集合。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: [Int32]::MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以將物件沿著管線向下傳送至 **DifferenceObject** 參數。

## 輸出

### 無

如果 **參考** 物件和 **差異** 物件相同，除非您使用 **IncludeEqual** 參數，否則不會有輸出。

### System.Management.Automation.PSCustomObject

如果物件不同，請將不同的 `Compare-Object` 物件包裝在 `PSCustomObject` 具有 **SideIndicator** 屬性的包裝函式中，以參考差異。

當您使用 **PassThru** 參數時，物件的 **型** 別不會變更，但所傳回物件的實例會有一個名為 **SideIndicator** 的新增 **NoteProperty** 。 **SideIndicator** 會顯示輸出所屬的輸入物件。

## 備忘稿

使用 **PassThru** 參數時，主控台中顯示的輸出可能不會包含 **SideIndicator** 屬性。 的物件類型輸出的預設格式視圖 `Compare-Object` 不包含 **SideIndicator** 屬性。 如需詳細資訊，請參閱本文中的 [範例 3](#ex3) 。

## 相關連結

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)
