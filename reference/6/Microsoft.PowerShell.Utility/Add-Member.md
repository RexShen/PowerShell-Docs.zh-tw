---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: ecf83a4dbf267fe105673e062740876156d18d49
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389771"
---
# Add-Member

## 概要
將自訂屬性和方法新增至 PowerShell 物件的實例。

## SYNTAX

### TypeNameSet (預設) 

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### NotePropertyMultiMemberSet

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### NotePropertySingleMemberSet

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### MemberSet

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## DESCRIPTION

此 `Add-Member` Cmdlet 可讓您將成員 (屬性和方法) 加入至 PowerShell 物件的實例。 例如，您可以加入包含物件描述的 NoteProperty 成員，或是執行腳本來變更物件的 **ScriptMethod** 成員。

若要使用 `Add-Member` ，請使用管線將物件傳送至 `Add-Member` ，或使用 **InputObject** 參數指定物件。

**MemberType** 參數會指出您要加入的成員類型。 **Name** 參數會指派名稱給新的成員，而 **Value** 參數會設定成員的值。

您新增的屬性和方法只會新增到您指定之物件特定的執行個體。 `Add-Member` 不會變更物件類型。 若要建立新的物件類型，請使用 `Add-Type` Cmdlet。

您也可以使用 `Export-Clixml` Cmdlet，將物件的實例（包括其他成員）儲存在檔案中。 然後，您可以使用 `Import-Clixml` Cmdlet，從儲存在匯出檔案中的資訊重新建立物件的實例。

從 Windows PowerShell 3.0 開始， `Add-Member` 有新功能可讓您更輕鬆地將附注屬性新增至物件。
您可以使用 **NotePropertyName** 和 **NotePropertyValue** 參數來定義附註屬性，或使用 **NotePropertyMembers** 參數以採用附註屬性名稱和值的雜湊表。

此外，自 Windows PowerShell 3.0 起，需使用會產生輸出物件之 **PassThru** 參數的頻率較少。 `Add-Member` 現在將新成員直接新增至更多類型的輸入物件。 如需詳細資訊，請參閱 **PassThru** 參數描述。

## 範例

### 範例1：將附注屬性新增至 PSObject

下列範例會將值為 "Done" 的 **狀態** 附注屬性新增至代表檔案的 **FileInfo** 物件 `Test.txt` 。

第一個命令會使用 `Get-ChildItem` Cmdlet 取得代表檔案的 **FileInfo** 物件 `Test.txt` 。 它會將它儲存在 `$a` 變數中。

第二個命令會將附注屬性新增至中的物件 `$a` 。

第三個命令使用點標記法來取得中物件的 **Status** 屬性值 `$a` 。 如輸出所示，值為「完成」。

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### 範例2：將別名屬性新增至 PSObject

下列範例會將 **大小** 別名屬性新增至代表檔案的物件 `Test.txt` 。 新屬性是 **Length** 屬性的別名。

第一個命令會使用 `Get-ChildItem` Cmdlet 來取得 `Test.txt` **FileInfo** 物件。

第二個命令會新增 [ **大小** 別名] 屬性。
第三個命令使用點標記法來取得新的 **大小** 屬性值。

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### 範例3：將 StringUse note 屬性新增至字串

此範例會將 **StringUse** note 屬性新增至字串。
因為 `Add-Member` 無法將類型新增至 **字串** 輸入物件，所以您可以指定 **PassThru** 參數來產生輸出物件。 範例中的最後一個命令會顯示新的屬性。

此範例使用 **NotePropertyMembers** 參數。 **NotePropertyMembers** 參數的值為雜湊表。 索引鍵是附注屬性名稱 **StringUse** ，而值則是附注屬性值 [ **顯示** ]。

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### 範例4：將腳本方法新增至 FileInfo 物件

此範例會將 **SizeInMB** 腳本方法新增至 **FileInfo** 物件，此物件會將檔案大小計算為最接近的 mb。 第二個命令會建立 **ScriptBlock** ，以使用類型的 **round** 靜態方法，將檔案 `[math]` 大小舍入至第二個小數位數。

**Value** 參數也會使用 `$This` 代表目前物件的自動變數。 `$This`變數只有在定義新屬性和方法的腳本區塊中才有效。

最後一個命令會使用點標記法，在變數中的物件上呼叫新的 **SizeInMB** 腳本方法 `$A` 。

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### 範例5：將物件的所有屬性複製到另一個

此函式會將一個物件的所有屬性複製到另一個物件。

`foreach`迴圈會使用 `Get-Member` Cmdlet 來取得 **From** 物件的每個屬性。 迴圈內的命令 `foreach` 會在每個屬性的數列中執行。

此 `Add-Member` 命令會將 **From** 物件的屬性新增至 **To** 物件做為 **NoteProperty** 。 使用 **value** 參數來複製值。 它會使用 **Force** 參數來加入具有相同成員名稱的成員。

```powershell
function Copy-Property ($From, $To)
{
    $properties = Get-Member -InputObject $From -MemberType Property
    foreach ($p in $properties)
    {
        $To | Add-Member -MemberType NoteProperty -Name $p.Name -Value $From.$($p.Name) -Force
    }
}
```

### 範例6：建立自訂物件

這個範例會建立 **資產** 自訂物件。

`New-Object`Cmdlet 會建立 **PSObject** 。 此範例會將 **PSObject** 儲存在 `$Asset` 變數中。

第二個命令使用 `[ordered]` 類型加速器來建立名稱和值的已排序字典。 命令會將結果儲存在 `$D` 變數中。

第三個命令會使用 Cmdlet 的 **NotePropertyMembers** 參數 `Add-Member` ，將變數中的字典新增 `$D` 至 **PSObject** 。
**TypeName** 屬性會將新的名稱、 **資產** 指派給 **PSObject** 。

最後一個命令會將新 **資產** 物件輸送至 `Get-Member` Cmdlet。 輸出顯示物件具有 **資產** 的類型名稱，以及我們在排序的字典中定義的附注屬性。

```powershell
$Asset = New-Object -TypeName PSObject
$d = [ordered]@{Name="Server30";System="Server Core";PSVersion="4.0"}
$Asset | Add-Member -NotePropertyMembers $d -TypeName Asset
$Asset | Get-Member
```

```Output
   TypeName: Asset

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty System.String Name=Server30
PSVersion   NoteProperty System.String PSVersion=4.0
System      NoteProperty System.String System=Server Core
```

## PARAMETERS

### -Force

指出此 Cmdlet 會加入新成員，即使該物件具有相同名稱的自訂成員。
您無法使用 **Force** 參數來取代型別的標準成員。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要新增成員的物件。
輸入包含物件的變數，或輸入可取得物件的命令或運算式。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MemberType

指定要加入之成員的類型。
這是必要參數。
此參數可接受的值為：

- NoteProperty
- AliasProperty
- ScriptProperty
- CodeProperty
- ScriptMethod
- CodeMethod

如需這些值的詳細資訊，請參閱 PowerShell SDK 中的 [ Psmembertypes 列舉](/dotnet/api/system.management.automation.psmembertypes) 。

並非所有物件都有每個類型的成員。
如果您指定物件沒有的成員類型，PowerShell 會傳回錯誤。

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: MemberSet
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定此 Cmdlet 新增的成員名稱。

```yaml
Type: System.String
Parameter Sets: MemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyMembers

指定內容是附註屬性名稱和值的雜湊表或排序的字典。
輸入其中的索引鍵為附註屬性名稱且值為附註屬性值的雜湊表或字典。

如需 PowerShell 中雜湊表和已排序字典的詳細資訊，請參閱 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Collections.IDictionary
Parameter Sets: NotePropertyMultiMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyName

指定附注屬性名稱。

請使用此參數搭配 **NotePropertyValue** 參數。
這是選擇性參數。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotePropertyValue

指定附注屬性值。

使用此參數搭配 **NotePropertyName** 參數。
這是選擇性參數。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Object
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

傳回代表您正在使用之項目的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

針對大部分的物件， `Add-Member` 將新成員新增至輸入物件。
但是，當輸入物件是字串時， `Add-Member` 無法將成員加入至輸入物件。
對於這些物件，使用 **PassThru** 參數可建立輸出物件。

在 Windows PowerShell 2.0 中， `Add-Member` 僅將成員新增至物件的 **PSObject** 包裝函式，而非物件。
使用 **PassThru** 參數，為具有 **PSObject** 包裝函式的任何物件建立輸出物件。

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

### -SecondValue

指定與 **AliasProperty** 、 **ScriptProperty** 、 **CodeProperty** 或 **CodeMethod** 成員相關的其他選擇性資訊。

如果在加入 **AliasProperty** 時使用，則這個參數必須是資料類型。
將轉換成指定的資料類型會新增至 **AliasProperty** 的值。

例如，如果您加入的 **AliasProperty** 會為字串屬性提供替代名稱，您也可以指定 System.string 的 **SecondValue** 參數 **，以指出** 在使用對應的 **AliasProperty** 存取時，該字串屬性的值應轉換成整數。

新增 **ScriptProperty** 成員時，您可以使用 **SecondValue** 參數來指定額外的 **ScriptBlock** 。 在 **Value** 參數中指定的第一個 **ScriptBlock** 會用來取得變數的值。 在 **SecondValue** 參數中指定的第二個 **ScriptBlock** 會用來設定變數的值。

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Value

指定已新增成員的初始值。
如果您加入 **AliasProperty** 、 **CodeProperty** 、 **ScriptProperty** 或 **CodeMethod** 成員，您可以使用 **SecondValue** 參數來提供選擇性的其他資訊。

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

指定類型的名稱。

當類型是 **System** 命名空間中的類別或具有類型加速器的類型時，您可以輸入類型的簡短名稱。 否則，需要完整類型名稱。
只有當 **InputObject** 為 **PSObject** 時，此參數才有效。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: TypeNameSet, NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: True (TypeNameSet), False (NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管線將任何物件類型傳送至此 Cmdlet。

## 輸出

### None 或 System.object

當您使用 **PassThru** 參數時，此 Cmdlet 會傳回新擴充的物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

您只能將成員新增到 **PSObject** 物件。 若要判斷物件是否為 **PSObject** 物件，請使用 `-is` 運算子。

例如，若要測試儲存在變數中的物件 `$obj` ，請輸入 `$obj -is [PSObject]` 。

**MemberType** 、 **Name** 、 **Value** 和 **SecondValue** 參數的名稱是選擇性的。
如果您省略參數名稱，未命名的參數值必須以下列順序顯示： **MemberType** 、 **Name** 、 **Value** 和 **SecondValue** 。

如果包含參數名稱，參數可以任何順序顯示。

您可以 `$this` 在定義新屬性和方法之值的腳本區塊中使用自動變數。
`$this`變數是指要加入屬性和方法之物件的實例。 如需變數的詳細資訊 `$this` ，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

## 相關連結

[Export-Clixml](Export-Clixml.md)

[Get-Member](Get-Member.md)

[Import-Clixml](Import-Clixml.md)

[New-Object](New-Object.md)

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)
