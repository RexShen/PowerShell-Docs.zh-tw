---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-typedata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-TypeData
ms.openlocfilehash: e8ac450e6681a6bfb9c0b50c8b9cb593ced3bdf3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201968"
---
# Update-TypeData

## 概要
更新工作階段中的延伸類型資料。

## Syntax

### FileSet (預設) 

```
Update-TypeData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DynamicTypeSet

```
Update-TypeData [-MemberType <PSMemberTypes>] [-MemberName <String>] [-Value <Object>]
 [-SecondValue <Object>] [-TypeConverter <Type>] [-TypeAdapter <Type>]
 [-SerializationMethod <String>] [-TargetTypeForDeserialization <Type>]
 [-SerializationDepth <Int32>] [-DefaultDisplayProperty <String>]
 [-InheritPropertySerializationSet <Nullable`1>] [-StringSerializationSource <String>]
 [-DefaultDisplayPropertySet <String[]>] [-DefaultKeyPropertySet <String[]>]
 [-PropertySerializationSet <String[]>] -TypeName <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### TypeDataSet

```
Update-TypeData [-Force] [-TypeData] <TypeData[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 描述

指令 `Update-TypeData` 程式會藉由將檔案重載 `Types.ps1xml` 到記憶體並新增延伸類型資料，來更新會話中的延伸類型資料。

根據預設，PowerShell 會在需要時載入延伸類型資料。 如果沒有參數，會 `Update-TypeData` 重載 `Types.ps1xml` 已載入會話中的所有檔案，包括您新增的任何類型檔案。 您可以使用的參數 `Update-TypeData` 加入新的類型檔案，以及加入和取代延伸類型資料。

`Update-TypeData`Cmdlet 可以用來預先載入所有類型資料。 當您正在開發類型並且想要基於測試目的載入這些新的類型，這個功能就特別有用。

從 Windows PowerShell 3.0 開始，您可以在 `Update-TypeData` 不使用檔案的情況下，使用來新增及取代會話中的延伸類型資料 `Types.ps1xml` 。 動態方式加入的類型資料 (也就是不具有檔案) 僅新增到目前的工作階段。 若要將類型資料新增到所有會話，請將 `Update-TypeData` 命令新增至您的 PowerShell 設定檔。 如需詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。

此外，從 Windows PowerShell 3.0 開始，您可以使用 `Get-TypeData` Cmdlet 取得目前會話中的延伸類型，以及使用 `Remove-TypeData` Cmdlet 從目前的會話刪除延伸類型。

在屬性中發生的例外狀況，或是將屬性新增至命令時， `Update-TypeData` 不會報告錯誤。 這是為了在進行格式化與輸出期間，抑制在許多常見類型中可能會出現的例外狀況。 如果您要取得 .NET 屬性，可以改為使用方法語法來解決例外狀況的隱藏，如下列範例所示：

`"hello".get_Length()`

請注意，方法語法只能與 .NET 屬性搭配使用。 藉由執行 Cmdlet 所新增的屬性 `Update-TypeData` 無法使用方法語法。

如需 PowerShell 中檔案的詳細資訊 `Types.ps1xml` ，請參閱 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)。

## 範例

### 範例1：更新擴充類型

```powershell
Update-TypeData
```

此命令會從已 `Types.ps1xml` 在會話中使用的檔案更新擴充類型設定。

### 範例2：多次更新類型

此範例顯示如何在相同的會話中多次更新類型檔案中的類型。

第一個命令會從檔案更新擴充類型設定 `Types.ps1xml` ， `TypesA.types.ps1xml` 並先處理和檔案 `TypesB.types.ps1xml` 。

第二個命令會顯示如何 `TypesA.types.ps1xml` 再次更新，例如，如果您在檔案中新增或變更類型，您可能會這麼做。 您可以針對檔案重複上述命令 `TypesA.types.ps1xml` ，或執行 `Update-TypeData` 不含參數的命令，因為 `TypesA.types.ps1xml` 已經在目前會話的類型檔案清單中。

```powershell
Update-TypeData -PrependPath TypesA.types.ps1xml, TypesB.types.ps1xml
Update-TypeData -PrependPath TypesA.types.ps1xml
```

### 範例3：將腳本屬性加入至 DateTime 物件

這個範例會使用將 `Update-TypeData` **季** 腳本屬性新增到目前會話中的 **system.object** 物件，例如 Cmdlet 所傳回的物件。 `Get-Date`

```powershell
Update-TypeData -TypeName "System.DateTime" -MemberType ScriptProperty -MemberName "Quarter" -Value {
  if ($this.Month -in @(1,2,3)) {"Q1"}
  elseif ($this.Month -in @(4,5,6)) {"Q2"}
  elseif ($this.Month -in @(7,8,9)) {"Q3"}
  else {"Q4"}
}
(Get-Date).Quarter
```

```Output
Q1
```

此 `Update-TypeData` 命令會使用 **TypeName** 參數來指定 **the System.DateTime** system.string 類型、 **成員** 名稱參數，以指定新屬性的名稱、使用 **MemberType** 屬性指定 **ScriptProperty** 類型，並使用 **Value** 參數來指定決定年度季的腳本。

**Value** 屬性的值為計算目前年度季別的指令碼。 腳本區塊 `$this` 會使用自動變數來代表物件目前的實例，並使用 In 運算子來判斷月份值是否出現在每個整數陣列中。 如需有關運算子的詳細資訊 `-in` ，請參閱 [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md)。

第二個命令會取得目前日期的新 Quarter 屬性。

### 範例4：依預設，更新清單中顯示的類型

這個範例示範如何設定依預設顯示在清單中的類型屬性，也就是未指定屬性時。 因為類型資料不是在檔案中指定 `Types.ps1xml` ，所以它只會在目前的會話中生效。

```powershell
Update-TypeData -TypeName "System.DateTime" -DefaultDisplayPropertySet "DateTime, DayOfYear, Quarter"
Get-Date | Format-List
```

```Output
Thursday, March 15, 2012 12:00:00 AM
DayOfYear : 75
Quarter   : Q1
```

第一個命令會使用指令 `Update-TypeData` 程式來設定 **System. DateTime** 類型的預設清單屬性。 此命令使用 **TypeName** 參數來指定類型和 **DefaultDisplayPropertySet** 參數來指定預設清單屬性。 選取的屬性包含上一個範例中所加入的新 **季** 腳本屬性。

第二個命令 `Get-Date` 會使用 Cmdlet 取得代表目前日期 **的 system.string** 物件。 此命令會使用管線運算子 (`|`) 將 **DateTime** 物件傳送至 `Format-List` Cmdlet。 由於 `Format-List` 命令未指定要顯示在清單中的屬性，因此 PowerShell 會使用命令所建立的預設值 `Update-TypeData` 。

### 範例5：更新管道物件的類型資料

```powershell
Get-Module | Update-TypeData -MemberType ScriptProperty -MemberName "SupportsUpdatableHelp" -Value {
  if ($this.HelpInfoUri) {$True} else {$False}
}
Get-Module -ListAvailable | Format-Table Name, SupportsUpdatableHelp
```

```Output
Name                             SupportsUpdatableHelp
----                             ---------------------
Microsoft.PowerShell.Diagnostics                  True
Microsoft.PowerShell.Host                         True
Microsoft.PowerShell.Management                   True
Microsoft.PowerShell.Security                     True
Microsoft.PowerShell.Utility                      True
Microsoft.WSMan.Management                        True
PSDiagnostics                                    False
PSScheduledJob                                    True
PSWorkflow                                        True
ServerManager                                     True
TroubleshootingPack                              False
```

這個範例示範當您使用管線將物件傳送至時 `Update-TypeData` ，會 `Update-TypeData` 加入物件類型的延伸類型資料。

這項技術比使用 `Get-Member` Cmdlet 或 `Get-Type` 方法來取得物件類型更快。 但是，如果您使用管線將物件集合傳送到 `Update-TypeData` ，它會更新第一個物件類型的類型資料，然後針對集合中的所有其他物件傳回錯誤，因為該類型上已經定義該成員。

第一個命令會使用 `Get-Module` Cmdlet 來取得 PSScheduledJob 模組。 此命令會使用管線將模組物件傳送至 `Update-TypeData` Cmdlet，此 Cmdlet 會更新 **PSModuleInfo** 類型的類型資料，以及從中衍生的類型，例如 `Get-Module` 當您在命令中使用 **ListAvailable** 參數時所傳回的 ModuleInfoGrouping 類型。

這些 `Update-TypeData` 命令會將 **SupportsUpdatableHelp** 腳本屬性新增至所有匯入的模組。 **Value** `$True` 如果已填入模組的 **HelpInfoUri** 屬性，則 value 參數的值為會傳回的腳本 `$False` 。

第二個命令會使用管線將模組物件傳送 `Get-Module` 至 `Format-Table` Cmdlet，此 Cmdlet 會顯示清單中所有模組的 **Name** 和 **SupportsUpdatableHelp** 屬性。

## 參數

### -AppendPath

指定選用檔案的路徑 `.ps1xml` 。 指定的檔案會依載入內建檔案之後所列出的順序載入。 您也可以使用管線將 **AppendPath** 值傳送至 `Update-TypeData` 。

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -DefaultDisplayProperty

指定 `Format-Wide` 當未指定其他屬性時，Cmdlet 所顯示的型別的屬性。

輸入類型的標準或延伸屬性的名稱。 此參數的值可以是相同命令中新增之類型的名稱。

只有在檔案中沒有針對型別定義任何寬度的視圖時，此值才會生效 `Format.ps1xml` 。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultDisplayPropertySet

指定類型的一或多個屬性。 `Format-List`如果未指定其他屬性，Cmdlet 會顯示這些屬性。

輸入類型的標準或延伸屬性的名稱。 此參數的值可以是相同命令中新增之類型的名稱。

只有在檔案中沒有針對類型定義清單視圖時，此值才會生效 `Format.ps1xml` 。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultKeyPropertySet

指定類型的一或多個屬性。 `Group-Object` `Sort-Object` 當沒有指定其他屬性時，和 Cmdlet 會使用這些屬性。

輸入類型的標準或延伸屬性的名稱。 此參數的值可以是相同命令中新增之類型的名稱。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指出此 Cmdlet 會使用指定的類型資料，即使已經為該類型指定類型資料。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DynamicTypeSet, TypeDataSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InheritPropertySerializationSet

指出是否繼承已序列化的屬性集。 預設值是 `$Null`。 此參數可接受的值為：

- `$True`. 已繼承屬性集。
- `$False`. 未繼承屬性集。
- `$Null`. 未定義繼承。

只有當 **SerializationMethod** 參數的值為時，此參數才有效 `SpecificProperties` 。 當此參數的值為時 `$False` ，需要 **PropertySerializationSet** 參數。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Nullable`1[System.Boolean]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -成員名稱

指定屬性或方法的名稱。

使用此參數與 **TypeName** 、 **MemberType** 、 **Value** 及 **SecondValue** 參數，新增或變更類型的屬性或方法。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MemberType

指定要新增或變更的成員類型。

使用此參數與 **TypeName** 、 **MemberType** 、 **Value** 及 **SecondValue** 參數，新增或變更類型的屬性或方法。 此參數可接受的值為：

- AliasProperty
- CodeMethod
- CodeProperty
- Noteproperty
- ScriptMethod
- ScriptProperty

如需這些值的詳細資訊，請參閱 [ Psmembertypes 列舉](/dotnet/api/system.management.automation.psmembertypes)。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: DynamicTypeSet
Aliases:
Accepted values: NoteProperty, AliasProperty, ScriptProperty, CodeProperty, ScriptMethod, CodeMethod

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrependPath

指定選用檔案的路徑 `.ps1xml` 。 指定的檔案會依載入內建檔案之前所列出的順序載入。

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PropertySerializationSet

指定已序列化的屬性名稱。 當 **SerializationMethod** 參數的值為 **SpecificProperties** 時使用此參數。

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecondValue

指定 **AliasProperty** 、 **ScriptProperty** 、 **CodeProperty** 或 **CodeMethod** 成員的額外值。

使用此參數搭配 **TypeName** 、 **MemberType** 、 **Value** 和 **SecondValue** 參數，以新增或變更類型的屬性或方法。

當 **MemberType** 參數的值為時 `AliasProperty` ， **SecondValue** 參數的值必須是資料類型。 PowerShell 會將 (轉換為，將別名屬性的值) 轉換為指定的類型。 例如，如果您加入一個別名屬性來為字串屬性提供替代名稱，您也可以指定 **system.string 的** **SecondValue** ，將別名字串值轉換為整數。

當 **MemberType** 參數的值為時 `ScriptProperty` ，您可以使用 **SecondValue** 參數來指定其他腳本區塊。 **Value** 參數值中的指令碼區塊會取得變數值。 **SecondValue** 參數值中的指令碼區塊會設定變數值。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SerializationDepth

指定要將多少層的類型物件序列化為字串。 預設值會序列化 `1` 物件和其屬性。 值會序列化 `0` 物件，但不會序列化其屬性。 的值會序列化 `2` 物件、其屬性，以及屬性值中的任何物件。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Int32
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### -SerializationMethod

指定類型的序列化方法。 序列化方法決定哪些類型的屬性會序列化，以及用來序列化它們的技術。 此參數可接受的值為：

- `AllPublicProperties`. 序列化類型的所有公用屬性。 您可以使用 **SerializationDepth** 參數，決定是否序列化子屬性。
- `String`. 將類型序列化為字串。 您可以使用 **StringSerializationSource** ，指定要做為序列化結果的類型屬性。 否則，會使用物件的 **ToString** 方法將類型序列化。
- `SpecificProperties`. 只序列化此類型的指定屬性。 使用 **PropertySerializationSet** 參數，指定已序列化的類型屬性。
  您也可以使用 **InheritPropertySerializationSet** 參數來決定是否要繼承屬性集，與 **SerializationDepth** 參數來決定是否要序列化子屬性。

在 PowerShell 中，序列化方法會儲存在 **PSStandardMembers** 的內建物件中。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StringSerializationSource

指定類型的屬性名稱。 指定屬性的值可做為序列化結果。 只有當 **SerializationMethod** 參數的值是字串時，此參數才有效。

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetTypeForDeserialization

指定此類型物件還原序列化時所轉換成為的類型。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeAdapter

指定類型介面卡的類型，例如 **microsoft.powershell.cim.ciminstanceadapter** 。 類型介面卡可讓 PowerShell 取得類型的成員。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeConverter

指定類型轉換器來轉換不同類型之間的值。 如果定義了類型的類型轉換器，類型轉換器的執行個體將會用於轉換。

輸入衍生自 **System.ComponentModel.TypeConverter** 或 **System.Management.Automation.PSTypeConverter** 類別的 **System.Type** 值。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeData

指定此 Cmdlet 新增至會話的型別資料陣列。 輸入包含 **TypeData** 物件的變數，或輸入可取得 **TypeData** 物件的命令，例如 `Get-TypeData` 命令。 您也可以使用管線將 **TypeData** 物件傳送至 `Update-TypeData` 。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.Runspaces.TypeData[]
Parameter Sets: TypeDataSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -TypeName

指定要延伸的類型名稱。

對於 **System** 命名空間中的類型，請輸入簡短名稱。 否則，需要完整類型名稱。 不支援萬用字元。

您可以用管線將類型名稱傳送至 `Update-TypeData` 。 當您使用管線將物件傳送至時，會取得物件的 `Update-TypeData` `Update-TypeData` 類型名稱以及物件類型的類型資料。

您可以使用此參數搭配 **成員名稱** 、 **MemberType** 、 **值** 和 **SecondValue** 參數，來新增或變更類型的屬性或方法。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Value

指定屬性或方法的值。

如果您加入 `AliasProperty` 、、 `CodeProperty` `ScriptProperty` 或 `CodeMethod` 成員，您可以使用 **SecondValue** 參數來新增其他資訊。

您可以使用此參數搭配 **成員名稱** 、 **MemberType** 、 **值** 和 **SecondValue** 參數，來新增或變更類型的屬性或方法。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### System.String

您可以使用管線將包含 **AppendPath** 、 **TypeName** 或 **TypeData** 參數值的字串傳送至 `Update-TypeData` 。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 備忘稿

## 相關連結

[about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Get-TypeData](Get-TypeData.md)

[Remove-TypeData](Remove-TypeData.md)
