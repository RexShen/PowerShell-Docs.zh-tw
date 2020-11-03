---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: 5a1a53c2b312ef36c80ecfb2a771d2fee2ebea7f
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "93206231"
---
# ForEach-Object

## 概要
針對輸入物件集合中的每個項目執行操作。

## SYNTAX

### ScriptBlockSet (預設) 

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PropertyAndMethodSet

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `ForEach-Object` Cmdlet 會對輸入物件集合中的每個專案執行作業。 輸入物件可以透過管道傳送至 Cmdlet，或使用 **InputObject** 參數來指定。

從 Windows PowerShell 3.0 開始，有兩種不同的方式可建立 `ForEach-Object` 命令。

- **腳本區塊** 。 您可以使用指令碼區塊來指定操作。 在腳本區塊中，使用 `$_` 變數來表示目前的物件。 指令碼區塊是 **Process** 參數的值。 腳本區塊可以包含任何 PowerShell 腳本。

  例如，下列命令會取得電腦上每個處理程序之 **ProcessName** 屬性的值。

  `Get-Process | ForEach-Object {$_.ProcessName}`

  `ForEach-Object` 支援 `begin` 、 `process` 和區塊， `end` 如 [about_functions](about/about_functions.md#piping-objects-to-functions)所述。

  > [!NOTE]
  > 腳本區塊會在呼叫端的範圍中執行。 因此，區塊可以存取該範圍中的變數，而且可以在 Cmdlet 完成之後，建立可保存在該範圍內的新變數。

- **Operation 語句** 。 您也可以撰寫像自然語言更類似的 operation 語句。 您可以使用操作陳述式來指定屬性值或呼叫方法。 操作陳述式是在 Windows PowerShell 3.0 中導入。

  例如，下列命令會一併取得電腦上每個處理程序之 **ProcessName** 屬性的值。

  `Get-Process | ForEach-Object ProcessName`

## 範例

### 範例1：分割陣列中的整數

這個範例會採用三個整數的陣列，並將每一個都除以1024。

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### 範例2：取得目錄中所有檔案的長度

此範例會處理 PowerShell 安裝目錄中的檔案和目錄 `$PSHOME` 。

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

如果物件不是目錄，腳本區塊會取得檔案的名稱、將其 **Length** 屬性的值除以1024，然後將空格 ( "" ) 以將它與下一個專案分開。 此 Cmdlet 會使用 **PSISContainer** 屬性來判斷物件是否為目錄。

### 範例3：在最近的系統事件上操作

此範例會將1000最新的事件從系統事件記錄檔寫入至文字檔。 目前的時間會在處理事件之前和之後顯示。

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

`Get-EventLog` 從系統事件記錄檔取得1000的最新事件，並將它們儲存在 `$Events` 變數中。 `$Events` 接著會透過管道傳送至 `ForEach-Object` Cmdlet。 **Begin** 參數會顯示目前的日期和時間。 接下來， **Process** 參數會使用 `Out-File` Cmdlet 來建立名為 events.txt 的文字檔，並將每個事件的訊息屬性儲存在該檔案中。 最後，會使用 **End** 參數，在所有處理都已完成之後顯示日期和時間。

### 範例4：變更登錄機碼的值

此範例會將金鑰下所有子機碼中的 **RemotePath** 登錄專案值變更 `HKCU:\Network` 為大寫文字。

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

您可以使用這個格式來變更登錄項目值的形式或內容。

**Network** 機碼中的每個子機碼代表在登入時將重新連線的連線網路磁碟機。
**RemotePath** 項目包含連線的磁碟機的 UNC 路徑。 例如，如果您將 E：磁片磁碟機對應到 `\\Server\Share` ，則會有的 **e** 子機碼 `HKCU:\Network` ，而 **e** 子機碼中 **RemotePath** 登錄專案的值為 `\\Server\Share` 。

此命令會使用指令程式 `Get-ItemProperty` 取得 **網路** 金鑰的所有子機碼，並使用 `Set-ItemProperty` Cmdlet 來變更每個機碼中 **RemotePath** 登錄專案的值。
在 `Set-ItemProperty` 命令中，路徑是登錄機碼的 **PSPath** 屬性值。 這是代表登錄機碼的 Microsoft .NET Framework 物件的屬性，而不是登錄專案。 此命令會使用 **RemotePath** 值的 **ToUpper ( # B1** 方法，這是 (REG_SZ) 的字串。

因為 `Set-ItemProperty` 正在變更每個機碼的屬性，所以 `ForEach-Object` 需要 Cmdlet 才能存取屬性。

### 範例5：使用 $Null 自動變數

此範例顯示將 `$Null` 自動變數輸送至 Cmdlet 的效果 `ForEach-Object` 。

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

因為 PowerShell 會將 null 視為明確的預留位置，所以 `ForEach-Object` Cmdlet 會產生的 `$Null` 值，就像是對其他物件進行輸送的物件一樣。

### 範例6：取得屬性值

此範例會使用 Cmdlet 的 **成員名稱** 參數，取得所有已安裝之 PowerShell 模組的 **Path** 屬性值 `ForEach-Object` 。

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

第二個命令同等於第一個命令。 它會使用 `Foreach` Cmdlet 的別名， `ForEach-Object` 並省略 **成員** 名稱參數的名稱，這是選擇性的。

`ForEach-Object`Cmdlet 非常適合用來取得屬性值，因為它會在不變更類型的情況下取得值，不像 **格式** Cmdlet `Select-Object` 或 Cmdlet，後者會變更屬性值類型。

### 範例7：將模組名稱分割成元件名稱

此範例顯示三種將兩個以點分隔的模組名稱分割成其元件名稱的方法。

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

命令呼叫字串的 **Split** 方法。 這三個命令使用不同的語法，但它們是相等的並且可交換使用。

第一個命令使用傳統語法，其中包含腳本區塊和目前物件運算子 `$_` 。 它使用點語法來指定要括住分隔符號引數的方法和括號。

第二個命令使用 **MemberName** 參數來指定 **Split** 方法，並使用 **ArgumentName** 參數來將點 (".") 識別為分隔符號。

第三個命令會使用 Cmdlet 的 **Foreach** 別名， `ForEach-Object` 並省略 **成員** 名稱和 **ArgumentList** 參數（選擇性）的名稱。

### 範例8：使用具有兩個腳本區塊的 ForEach-Object

在此範例中，我們會將兩個腳本區塊 positionally 傳遞給。 所有腳本區塊都會系結至 **Process** 參數。 不過，它們會被視為已傳遞至 **Begin** 和 **Process** 參數。

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### 範例9：使用具有兩個以上腳本區塊的 ForEach-Object

在此範例中，我們會將兩個腳本區塊 positionally 傳遞給。 所有腳本區塊都會系結至 **Process** 參數。 不過，它們會被視為已傳遞至 **Begin** 、 **Process** 和 **End** 參數。

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> 第一個腳本區塊一律對應至 `begin` 區塊、最後一個區塊會對應至 `end` 區塊，而 between 中的區塊都會對應至 `process` 區塊。

### 範例10：為每個管線專案執行多個腳本區塊

如上一個範例所示，使用 **Process** 參數傳遞的多個腳本區塊會對應到 **Begin** 和 **End** 參數。 若要避免這種對應，您必須提供 **Begin** 和 **End** 參數的明確值。

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

## PARAMETERS

### -ArgumentList

指定方法呼叫的引數陣列。 如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Begin

指定在此 Cmdlet 處理任何輸入物件之前執行的腳本區塊。 此腳本區塊只會針對整個管線執行一次。 如需有關區塊的詳細資訊 `begin` ，請參閱 [about_Functions](about/about_functions.md#piping-objects-to-functions)。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -End

指定在此 Cmdlet 處理所有輸入物件之後執行的腳本區塊。 此腳本區塊只會針對整個管線執行一次。 如需有關區塊的詳細資訊 `end` ，請參閱 [about_Functions](about/about_functions.md#piping-objects-to-functions)。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定輸入物件。 `ForEach-Object` 在每個輸入物件上執行腳本區塊或動作陳述式。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

當您搭配使用 **inputobject** 參數與時 `ForEach-Object` ，不會將命令結果傳送至，而是 `ForEach-Object` 會將 **inputobject** 值視為單一物件。 即使值是命令結果的集合（例如），也是如此 `-InputObject (Get-Process)` 。
因為 **InputObject** 無法從物件的陣列或集合傳回個別屬性，所以如果您使用 `ForEach-Object` 在已定義屬性中具有特定值之物件的集合上執行作業，則建議您在 `ForEach-Object` 管線中使用，如本主題中的範例所示。

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

### -成員名稱

指定要取得的屬性或要呼叫的方法。

允許使用萬用字元，但只有在產生的字串解析為唯一值時，才會運作。
例如，如果您執行 `Get-Process | ForEach -MemberName *Name` ，而且有一個以上的成員具有包含字串名稱的名稱，例如 **ProcessName** 和 **name** 屬性，則命令會失敗。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Process

指定在每個輸入物件上執行的操作。 此腳本區塊會針對管線中的每個物件執行。 如需有關區塊的詳細資訊 `process` ，請參閱 [about_Functions](about/about_functions.md#piping-objects-to-functions)。

當您將多個腳本區塊提供給 **Process** 參數時，第一個腳本區塊一律會對應至 `begin` 區塊。 如果只有兩個腳本區塊，則第二個區塊會對應至 `process` 區塊。 如果有三個或多個腳本區塊，則第一個腳本區塊一律會對應至 `begin` 區塊、最後一個區塊會對應至 `end` 區塊，而 between 中的區塊都會對應至 `process` 區塊。

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemainingScripts

指定 **Process** 參數未採用的所有腳本區塊。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
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

### System.Management.Automation.PSObject

您可以使用管線將任何物件傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.PSObject

這個 Cmdlet 會傳回由輸入決定的物件。

## 注意

- 此 `ForEach-Object` Cmdlet 的運作方式與 **foreach** 語句很類似，不同之處在于您無法使用管線將輸入傳送至 **foreach** 語句。 如需 **Foreach** 語句的詳細資訊，請參閱 [about_Foreach](./About/about_Foreach.md)。

- 從 PowerShell 4.0 開始， `Where` `ForEach` 已新增方法以與集合搭配使用。 您可以在這裡閱讀更多有關這些新方法的資訊 [about_arrays](./About/about_Arrays.md)

## 相關連結

[Compare-Object](../Microsoft.PowerShell.Utility/Compare-Object.md)

[Where-Object](Where-Object.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Measure-Object](../Microsoft.PowerShell.Utility/Measure-Object.md)

[New-Object](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Tee-Object](../Microsoft.PowerShell.Utility/Tee-Object.md)
