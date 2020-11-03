---
description: 在 PowerShell 中將命令結合成管線
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: ca933e7e130959ef725d760d859ca43b99bdfc76
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207299"
---
# <a name="about-pipelines"></a>關於管線

## <a name="short-description"></a>簡短描述

在 PowerShell 中將命令結合成管線

## <a name="long-description"></a>完整描述

管線是管線運算子所連接的一連串命令 (`|`)  (ASCII 124) 。 每個管線運算子都會將上述命令的結果傳送至下一個命令。

第一個命令的輸出可以傳送給第二個命令的輸入，以便進行處理。 此外，也可以將輸出傳送至另一個命令。 結果是由一系列簡單命令組成的複雜命令鏈或 _管線_ 。

例如，套用至物件的

```powershell
Command-1 | Command-2 | Command-3
```

在此範例中，發出的物件 `Command-1` 會傳送至 `Command-2` 。
`Command-2` 處理物件，並將它們傳送至 `Command-3` 。 `Command-3` 處理物件，並將它們傳送至管線。 因為管線中沒有其他命令，所以會在主控台顯示結果。

在管線中，命令會依序由左至右處理。 處理會以單一作業的方式處理，並在產生輸出時顯示輸出。

以下是一個簡單範例。 下列命令會取得「記事本」處理常式，然後將它停止。

例如，套用至物件的

```powershell
Get-Process notepad | Stop-Process
```

第一個命令會使用 `Get-Process` Cmdlet 來取得代表記事本進程的物件。 它使用管線運算子 (`|`) 將處理常式物件傳送至 `Stop-Process` Cmdlet，此 Cmdlet 會停止「記事本」處理常式。 請注意，此 `Stop-Process` 命令沒有 **Name** 或 **ID** 參數來指定處理常式，因為指定的進程是透過管線提交。

此管線範例會取得目前目錄中的文字檔、只選取超過10000個位元組的檔案、依長度排序，以及顯示資料表中每個檔案的名稱和長度。

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

此管線是由指定順序的四個命令所組成。 下圖顯示每個命令的輸出，因為它會傳遞至管線中的下一個命令。

```
Get-ChildItem -Path *.txt
| (FileInfo objects for *.txt)
V
Where-Object {$_.length -gt 10000}
| (FileInfo objects for *.txt)
| (      Length > 10000      )
V
Sort-Object -Property Length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
V
Format-Table -Property name, length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
| (   Formatted in a table   )
V

Name                       Length
----                       ------
tmp1.txt                    82920
tmp2.txt                   114000
tmp3.txt                   114000
```

## <a name="using-pipelines"></a>使用管線

大部分的 PowerShell Cmdlet 都是設計來支援管線。 在大多數情況下，您可以使用 _管線_ 將 **Get** Cmdlet 的結果傳送至相同名詞的另一個 Cmdlet。
例如，您可以透過管道將 Cmdlet 的輸出傳送 `Get-Service` 至 `Start-Service` 或 `Stop-Service` Cmdlet。

此範例管線會啟動電腦上的 WMI 服務：

```powershell
Get-Service wmi | Start-Service
```

針對另一個範例，您可以透過管道將 `Get-Item` PowerShell 登錄提供者中或的輸出傳送 `Get-ChildItem` 至 `New-ItemProperty` Cmdlet。 此範例會將新的登錄專案 **NoOfEmployees** （值為 **8124** ）新增至 **MyCompany** 登錄機碼。

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

許多公用程式 Cmdlet （例如、、 `Get-Member` 、 `Where-Object` `Sort-Object` 和） `Group-Object` `Measure-Object` 在管線中幾乎都是使用。 您可以透過管線將任何物件類型傳送至這些 Cmdlet。 這個範例會示範如何依照每個進程中的開啟控制碼數目來排序電腦上的所有處理常式。

```powershell
Get-Process | Sort-Object -Property handles
```

您可以透過管線將物件傳送至格式化、匯出和輸出 Cmdlet，例如 `Format-List` 、 `Format-Table` 、 `Export-Clixml` 、 `Export-CSV` 和 `Out-File` 。

此範例示範如何使用指令 `Format-List` 程式來顯示處理常式物件的屬性清單。

```powershell
Get-Process winlogon | Format-List -Property *
```

在練習中，您會發現將簡單的命令結合成管線可節省時間和輸入，並讓您的腳本更有效率。

## <a name="how-pipelines-work"></a>管線的運作方式

本節說明輸入物件如何系結至 Cmdlet 參數，以及在管線執行期間處理。

### <a name="accepts-pipeline-input"></a>接受管線輸入

為了支援管線，接收的 Cmdlet 必須有接受管線輸入的參數。 使用 `Get-Help` 命令搭配 **Full** 或 **參數** 選項，以判斷 Cmdlet 接受管線輸入的參數。

例如，若要判斷 Cmdlet 的哪些參數 `Start-Service` 接受管線輸入，請輸入：

```powershell
Get-Help Start-Service -Full
```

或

```powershell
Get-Help Start-Service -Parameter *
```

指令程式的 `Start-Service` 說明只會顯示 **InputObject** 和 **Name** 參數接受管線輸入。

```Output
-InputObject <ServiceController[]>
Specifies ServiceController objects representing the services to be started.
Enter a variable that contains the objects, or type a command or expression
that gets the objects.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByValue)
Accept wildcard characters?  false

-Name <String[]>
Specifies the service names for the service to be started.

The parameter name is optional. You can use Name or its alias, ServiceName,
or you can omit the parameter name.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByPropertyName, ByValue)
Accept wildcard characters?  false
```

當您透過管線將物件傳送至時 `Start-Service` ，PowerShell 會嘗試將物件與 **InputObject** 和 **Name** 參數產生關聯。

### <a name="methods-of-accepting-pipeline-input"></a>接受管線輸入的方法

Cmdlet 參數可以透過下列兩種不同方式接受管線輸入：

- **ByValue** ：參數會接受符合預期 .net 類型或可轉換為該類型的值。

  例如，的 **Name** 參數會 `Start-Service` 接受以傳值方式輸入的管線。 它可以接受可轉換成字串的字串物件或物件。

- **ByPropertyName** ：參數只有在輸入物件具有與參數同名的屬性時，才會接受輸入。

  例如，的 Name 參數 `Start-Service` 可以接受具有 **Name** 屬性的物件。 若要列出物件的屬性，請使用管線將它傳送至 `Get-Member` 。

某些參數可以接受值或屬性名稱的物件，讓您更輕鬆地從管線取得輸入。

### <a name="parameter-binding"></a>參數繫結

當您使用管線將物件從一個命令傳送到另一個命令時，PowerShell 會嘗試將管道物件與接收 Cmdlet 的參數產生關聯。

PowerShell 的參數系結元件會根據下列準則，將輸入物件與 Cmdlet 參數產生關聯：

- 參數必須接受來自管線的輸入。
- 參數必須接受所傳送物件的型別，或是可以轉換成預期型別的型別。
- 命令中未使用參數。

例如， `Start-Service` Cmdlet 有許多參數，但只有兩個， **名稱** 和 **InputObject** 接受管線輸入。 **Name** 參數接受字串，而 **InputObject** 參數則接受服務物件。 因此，您可以使用可轉換成字串或服務物件的屬性，將字串、服務物件和物件輸送。

PowerShell 盡可能有效率地管理參數系結。 您無法建議或強制 PowerShell 系結至特定的參數。 如果 PowerShell 無法系結輸送的物件，則命令會失敗。

如需針對系結錯誤進行疑難排解的詳細資訊，請參閱本文稍後的 [調查管線錯誤](#investigating-pipeline-errors) 。

### <a name="one-at-a-time-processing"></a>一次性的處理

將物件傳送至命令很像是使用命令的參數來提交物件。 讓我們看看管線範例。 在此範例中，我們會使用管線來顯示服務物件的表格。

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

功能上，這就像是使用的 **InputObject** 參數 `Format-Table` 來提交物件集合。

例如，我們可以將服務集合儲存至使用 **InputObject** 參數傳遞的變數。

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

也可以將命令內嵌在 **InputObject** 參數中。

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

不過，有一個重要的差異。 當您使用管線將多個物件傳送至命令時，PowerShell 會一次將物件傳送至命令。 當您使用命令參數時，物件會以單一陣列物件的形式傳送。 這項微小差異有顯著的後果。

執行管線時，PowerShell 會自動列舉任何實作為介面的類型， `IEnumerable` 並一次透過管線傳送成員。 例外狀況是 `[hashtable]` ，需要呼叫 `GetEnumerator()` 方法。

在下列範例中，會使用管線將陣列和 hashtable 輸送至 `Measure-Object` Cmdlet，以計算從管線接收的物件數目。 陣列有多個成員，而雜湊表具有多個索引鍵/值組。 一次只列舉一個陣列。

```powershell
@(1,2,3) | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

```powershell
@{"One"=1;"Two"=2} | Measure-Object
```

```Output
Count    : 1
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

同樣地，如果您使用管線將多個處理常式物件從 `Get-Process` Cmdlet 傳送至 `Get-Member` Cmdlet，則 PowerShell 會將每個處理常式物件一次傳送至 `Get-Member` 。 `Get-Member` 顯示處理常式物件的 .NET 類別 (類型) ，以及其屬性和方法。

```powershell
Get-Process | Get-Member
```

```Output
TypeName: System.Diagnostics.Process

Name      MemberType     Definition
----      ----------     ----------
Handles   AliasProperty  Handles = Handlecount
Name      AliasProperty  Name = ProcessName
NPM       AliasProperty  NPM = NonpagedSystemMemorySize
...
```

> [!NOTE]
> `Get-Member` 排除重複專案，因此如果物件全都屬於相同類型，則只會顯示一個物件類型。

但是，如果您使用的 **InputObject** 參數 `Get-Member` ，則會 `Get-Member` 接收 system.string 的陣列，將物件 **處理** 為單一單位。 它會顯示物件陣列的屬性。  (記下陣列符號 (`[]`) 在 **system.object** 類型名稱之後。 ) 

例如，套用至物件的

```powershell
Get-Member -InputObject (Get-Process)
```

```Output
TypeName: System.Object[]

Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
Address            Method        System.Object& Address(Int32 )
Clone              Method        System.Object Clone()
...
```

這可能不是您想要的結果。 但是在您瞭解之後，就可以使用它。 例如，所有陣列物件都有 **Count** 屬性。 您可以使用它來計算電腦上執行的處理常式數目。

例如，套用至物件的

```powershell
(Get-Process).count
```

請務必記住，管線上傳送的物件會一次傳遞一個。

## <a name="investigating-pipeline-errors"></a>調查管線錯誤

當 PowerShell 無法使輸送的物件與接收 Cmdlet 的參數產生關聯時，命令會失敗。

在下列範例中，我們會嘗試將登錄專案從一個登錄機碼移至另一個登錄機碼。 此 `Get-Item` Cmdlet 會取得目的地路徑，然後以管線傳送至 `Move-ItemProperty` Cmdlet。 此 `Move-ItemProperty` 命令會指定要移動的登錄專案目前的路徑和名稱。

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

此命令會失敗，且 PowerShell 會顯示下列錯誤訊息：

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

若要調查，請使用 `Trace-Command` Cmdlet 來追蹤 PowerShell 的參數系結元件。 下列範例會在管線執行時追蹤參數系結。 **PSHost** 參數會在主控台中顯示追蹤結果，而 **FilePath** 參數會將追蹤結果傳送至檔案， `debug.txt` 以供稍後參考。

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

追蹤的結果很長，但它們會顯示系結至 Cmdlet 的值， `Get-Item` 然後再將命名值系結至 `Move-ItemProperty` Cmdlet。

```Output
...
BIND NAMED cmd line args [`Move-ItemProperty`]
BIND arg [HKLM:\Software\MyCompany\design] to parameter [Path]
...
BIND arg [product] to parameter [Name]
...
BIND POSITIONAL cmd line args [`Move-ItemProperty`]
...
```

最後，它會顯示嘗試將路徑系結至失敗的 **目的地** 參數 `Move-ItemProperty` 。

```Output
...
BIND PIPELINE object to parameters: [`Move-ItemProperty`]
PIPELINE object TYPE = [Microsoft.Win32.RegistryKey]
RESTORING pipeline parameter's original values
Parameter [Destination] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
Parameter [Credential] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
...
```

使用 `Get-Help` Cmdlet 來查看 **目的地** 參數的屬性。

```Output
Get-Help Move-ItemProperty -Parameter Destination

-Destination <String>
    Specifies the path to the destination location.

    Required?                    true
    Position?                    1
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  false
```

結果會顯示 **目的地** 只接受「依屬性名稱」的管線輸入。 因此，輸送的物件必須有一個名為 **Destination** 的屬性。

使用 `Get-Member` 以查看來自的物件屬性 `Get-Item` 。

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

輸出顯示此專案為不具有 **目的地** 屬性的 **Microsoft. RegistryKey** 物件。 這會說明命令失敗的原因。

**Path** 參數會依名稱或傳值方式接受管線輸入。

```Output
Get-Help Move-ItemProperty -Parameter Path

-Path <String[]>
    Specifies the path to the current location of the property. Wildcard
    characters are permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  true
```

若要修正此命令，我們必須在 Cmdlet 中指定目的地， `Move-ItemProperty` 並使用 `Get-Item` 來取得我們想要移動之專案的 **路徑** 。

例如，套用至物件的

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a>內建行接續符號

如先前所討論，管線是由管線運算子連接的一連串命令 (`|`) ，通常是以單一行寫入。 不過，為了方便閱讀，PowerShell 可讓您將管線分割成多行。
當管道運算子是該行上的最後一個 token 時，PowerShell 剖析器會將下一行加入至目前的命令，以繼續管線的結構。

例如，下列單行管線：

```powershell
Command-1 | Command-2 | Command-3
```

可以撰寫為：

```powershell
Command-1 |
  Command-2 |
    Command-3
```

後續幾行的前置空格並不重要。 縮排可增強可讀性。

PowerShell 7 以管線開頭的管線字元，新增管線接續的支援。 下列範例示範如何使用這項新功能。

```powershell
# Wrapping with a pipe at the beginning of a line (no backtick required)
Get-Process | Where-Object CPU | Where-Object Path
    | Get-Item | Where-Object FullName -match "AppData"
    | Sort-Object FullName -Unique

# Wrapping with a pipe on a line by itself
Get-Process | Where-Object CPU | Where-Object Path
    |
    Get-Item | Where-Object FullName -match "AppData"
    |
    Sort-Object FullName -Unique
```

> [!IMPORTANT]
> 以互動方式在 shell 中工作時，只有在使用<kbd>Ctrl</kbd> + <kbd>V</kbd>貼上時，才會在行首將程式碼與管線貼上。
> 以滑鼠右鍵按一下 [貼上作業]，一次插入一個行。 由於程式程式碼結尾不是管線字元，因此 PowerShell 會將輸入視為完成，並依照輸入執行該行。

## <a name="see-also"></a>另請參閱

[about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)

[about_Objects](about_objects.md)

[about_Parameters](about_parameters.md)

[about_Command_Syntax](about_command_syntax.md)

[about_ForEach](about_foreach.md)

