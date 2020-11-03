---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Module
ms.openlocfilehash: d0c0388142092034b06a2185dadcaed2f19d9865
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204515"
---
# New-Module

## 概要
建立只存在記憶體中的新動態模組。

## SYNTAX

### ScriptBlock (預設值)

```
New-Module [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>] [-ReturnResult]
 [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### Name

```
New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>]
 [-ReturnResult] [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## DESCRIPTION

`New-Module`Cmdlet 會從腳本區塊建立動態模組。 動態模組的成員 (例如函式與變數) 可立即在工作階段中使用，而且在您關閉工作階段之前保持可用。

類似靜態模組，預設會匯出動態模組中的 Cmdlet 與函式，而不會匯出變數與別名。 不過，您可以使用 Export-ModuleMember Cmdlet 和的參數來覆 `New-Module` 寫預設值。

您也可以使用的 **AsCustomObject** 參數 `New-Module` ，將動態模組傳回做為自訂物件。 模組的成員 (例如函式) 會以自訂物件的指令碼方法實作，而不會匯入到工作階段。

動態模組只存在於記憶體中，而不是在磁片上。 類似所有模組，動態模組的成員會在全域範圍的子系私人模組範圍中執行。 Get-Module 無法取得動態模組，但是 Get-Command 可以取得匯出的成員。

若要讓動態模組可供使用 `Get-Module` ，請使用管線將 `New-Module` 命令傳送至 import-module，或使用管線將傳回的模組物件傳送至 `New-Module` `Import-Module` 。 此動作會將動態模組新增至 `Get-Module` 清單中，但不會將模組儲存到磁片或使其成為持續性。

## 範例

### 範例1：建立動態模組

此範例會使用名為的函式建立新的動態模組 `Hello` 。 此命令傳回代表新動態模組的模組物件。

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

### 範例2：使用動態模組和 Get-Module 和 Get-Command

此範例示範 Cmdlet 不會傳回動態模組 `Get-Module` 。 Cmdlet 會傳回它們所匯出的成員 `Get-Command` 。

```powershell
new-module -scriptblock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Module

Get-Command Hello
```

```Output
CommandType     Name   Definition
-----------     ----   ----------
Function        Hello  "Hello!"
```

### 範例3：將變數匯出到目前的會話

此範例會使用 `Export-ModuleMember` Cmdlet 將變數匯出到目前的會話。
如果沒有 `Export-ModuleMember` 命令，則只會匯出函數。

```powershell
New-Module -ScriptBlock {$SayHelloHelp="Type 'SayHello', a space, and a name."; function SayHello ($name) { "Hello, $name" }; Export-ModuleMember -function SayHello -Variable SayHelloHelp}
$SayHelloHelp
```

```Output
Type 'SayHello', a space, and a name.
```

```powershell
SayHello Jeffrey
```

```Output
Hello, Jeffrey
```

輸出顯示變數與函式皆匯出到工作階段。

### 範例4：將動態模組提供給 Get-Module

這個範例示範您可以使用管線將動態模組傳送至，藉以建立動態模組 `Get-Module` `Import-Module` 。

`New-Module` 建立輸送至 Cmdlet 的模組物件 `Import-Module` 。 的 **name** 參數會將 `New-Module` 易記名稱指派給模組。 因為 `Import-Module` 預設不會傳回任何物件，所以此命令沒有任何輸出。 `Get-Module`**GreetingModule** 已匯入至目前的會話。

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}} -name GreetingModule | Import-Module
Get-Module
```

```Output
Name              : GreetingModule
Path              : d54dfdac-4531-4db2-9dec-0b4b9c57a1e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Command hello
```

```Output
CommandType     Name                                                               Definition
-----------     ----                                                               ----------
Function        Hello                                                              "Hello!"
```

此 `Get-Command` Cmdlet 會顯示 `Hello` 動態模組所匯出的函式。

### 範例5：產生具有匯出函數的自訂物件

這個範例會示範如何使用的 **AsCustomObject** 參數 `New-Module` 來產生自訂物件，該物件具有代表匯出函數的腳本方法。

此 `New-Module` Cmdlet 會建立包含兩個函式和的動態模組 `Hello` `Goodbye` 。 **AsCustomObject** 參數會建立自訂物件，而不是預設產生的 **PSModuleInfo** 物件 `New-Module` 。 這個自訂物件會儲存在 `$m` 變數中。
`$m`變數似乎沒有指派的值。

```powershell
$m = New-Module -ScriptBlock {
  function Hello ($name) {"Hello, $name"}
  function Goodbye ($name) {"Goodbye, $name"}
} -AsCustomObject
$m
$m | Get-Member
```

```Output
TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Goodbye     ScriptMethod System.Object Goodbye();
Hello       ScriptMethod System.Object Hello();
```

```powershell
$m.goodbye("Jane")
```

```Output
Goodbye, Jane
```

```powershell
$m.hello("Manoj")
```

```Output
Hello, Manoj
```

輸送 `$m` 至 `Get-Member` Cmdlet 會顯示自訂物件的屬性和方法。 輸出顯示物件具有表示和函數的腳本方法 `Hello` `Goodbye` 。
最後，我們會呼叫這些腳本方法，並顯示結果。

### 範例6：取得腳本區塊的結果

此範例使用 **ReturnResult** 參數來要求執行腳本區塊的結果，而不是要求模組物件。 新模組中的腳本區塊會定義函式 `SayHello` ，然後呼叫函數。

```powershell
New-Module -ScriptBlock {function SayHello {"Hello, World!"}; SayHello} -ReturnResult
```

```Output
Hello, World!
```

## PARAMETERS

### -ArgumentList

指定引數陣列，這些引數是傳遞至腳本區塊的參數值。 如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsCustomObject

指出此 Cmdlet 會傳回代表動態模組的自訂物件。 模組成員會以自訂物件的指令碼方法實作，但是不會匯入到工作階段中。 您可以將自訂物件儲存在變數中，並使用點標記法來叫用成員。

如果模組有多個同名的成員，例如函式和變數（兩者都是），則只能從自訂物件存取一個具有每個名稱的成員。

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

### -Cmdlet

指定 Cmdlet 的陣列，此 Cmdlet 會從模組匯出到目前的會話。
輸入以逗號分隔的 Cmdlet 清單。 允許使用萬用字元。 根據預設，會匯出模組中所有的 Cmdlet。

您不能定義指令碼區塊中的 Cmdlet，但是動態模組可以包含　Cmdlet (若動態模組從二進位模組匯入 Cmdlet)。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Function

指定此 Cmdlet 從模組匯出到目前會話的函式陣列。
輸入以逗號分隔的函式清單。 允許使用萬用字元。 根據預設，會匯出模組中定義的所有函式。

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

指定新模組的名稱。 您也可以使用管線將模組名稱傳送至 New-Module。

預設值是以開頭的自動產生名稱， `__DynamicModule_` 後面接著指定動態模組路徑的 GUID。

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ReturnResult

指出此 Cmdlet 會執行腳本區塊並傳回腳本區塊的結果，而不是傳回模組物件。

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

### -ScriptBlock

指定動態模組的內容。 以大括弧括住內容 (`{}`) 來建立腳本區塊。 這是必要參數。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將模組名稱傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.PSModuleInfo、System.Management.Automation.PSCustomObject 或 None

依預設，此 Cmdlet 會產生 **PSModuleInfo** 物件。 如果您使用 **AsCustomObject** 參數，它會產生 **PSCustomObject** 物件。 如果您使用 **ReturnResult** 參數，它會傳回評估動態模組中腳本區塊的結果。

## 注意

您也可以 `New-Module` 使用其別名來參考 `nmo` 。 如需詳細資訊，請參閱 [about_Aliases](About/about_Aliases.md)。

## 相關連結

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[Import-Module](Import-Module.md)

[Remove-Module](Remove-Module.md)
