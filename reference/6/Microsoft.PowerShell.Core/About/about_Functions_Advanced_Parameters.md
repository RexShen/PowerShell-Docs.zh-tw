---
description: 說明如何將參數加入至 advanced 函數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: 1d33fcd6ccb665ceae1db91783542385fd49b9cc
ms.sourcegitcommit: 3b1779890f828130a9d73aebf17ebffae511728f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "93208915"
---
# <a name="about-functions-advanced-parameters"></a>關於函數的 Advanced 參數

## <a name="short-description"></a>簡短描述

說明如何將參數加入至 advanced 函數。

## <a name="long-description"></a>完整描述

您可以將參數加入至您所撰寫的 advanced 函數，並使用參數屬性和引數來限制函式使用者以參數提交的參數值。

除了 PowerShell 自動新增至所有 Cmdlet 和 advanced 函數的一般參數之外，您新增至函式的參數也可供使用者使用。 如需 PowerShell 一般參數的詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。

從 PowerShell 3.0 開始，您可以使用展開搭配 `@Args` 來代表命令中的參數。 展開適用于簡單和先進的函式。 如需詳細資訊，請參閱 [about_Functions](about_Functions.md) 和 [about_Splatting](about_Splatting.md)。

## <a name="type-conversion-of-parameter-values"></a>參數值的類型轉換

當您將字串作為引數提供給預期不同類型的參數時，PowerShell 會以隱含方式將字串轉換為參數目標型別。
Advanced 函式會執行參數值的文化特性不變剖析。

相反地，在編譯的 Cmdlet 的參數系結期間會執行區分文化特性的轉換。

在此範例中，我們會建立 Cmdlet，以及使用參數的腳本函式 `[datetime]` 。 目前的文化特性已變更為使用德文設定。
德文格式的日期會傳遞至參數。

```powershell
# Create a cmdlet that accepts a [datetime] argument.
Add-Type @'
  using System;
  using System.Management.Automation;
  [Cmdlet("Get", "Date_Cmdlet")]
  public class GetFooCmdlet : Cmdlet {

    [Parameter(Position=0)]
    public DateTime Date { get; set; }

    protected override void ProcessRecord() {
      WriteObject(Date);
    }
  }
'@ -PassThru | % Assembly | Import-Module

[cultureinfo]::CurrentCulture = 'de-DE'
$dateStr = '19-06-2018'

Get-Date_Cmdlet $dateStr
```

```Output
Dienstag, 19. Juni 2018 00:00:00
```

如上所示，Cmdlet 會使用區分文化特性的剖析來轉換字串。

```powershell
# Define an equivalent function.
function Get-Date_Func {
  param(
    [DateTime] $Date
  )
  process {
    $Date
  }
}

[cultureinfo]::CurrentCulture = 'de-DE'

# This German-format date string doesn't work with the invariant culture.
# E.g., [datetime] '19-06-2018' breaks.
$dateStr = '19-06-2018'

Get-Date_Func $dateStr
```

Advanced 函數使用文化特性非變異剖析，這會導致下列錯誤。

```Output
Get-Date_Func : Cannot process argument transformation on parameter 'Date'. Cannot convert
 value "19-06-2018" to type "System.DateTime". Error: "String was not recognized as a valid
 DateTime."
At line:13 char:15
+ Get-Date_Func $dateStr
+               ~~~~~~~~
    + CategoryInfo          : InvalidData: (:) [Get-Date_Func], ParameterBindingArgumentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Get-Date_Func
```

## <a name="static-parameters"></a>靜態參數

靜態參數是函數中永遠可用的參數。
PowerShell Cmdlet 和腳本中的大部分參數都是靜態參數。

下列範例顯示具有下列特性之 **ComputerName** 參數的宣告：

- 這是必要的 (需要) 。
- 它會接受來自管線的輸入。
- 它接受字串陣列做為輸入。

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a>參數的屬性

本節說明您可以新增至函式參數的屬性。

所有屬性都是選擇性的。 但是，如果您省略 **CmdletBinding** 屬性，然後將它辨識為 advanced 函數，則函式必須包含 **參數** 屬性。

您可以在每個參數宣告中加入一個或多個屬性。 您可以加入至參數宣告的屬性數目沒有任何限制。

### <a name="parameter-attribute"></a>參數屬性

**Parameter** 屬性是用來宣告函數參數的屬性。

**參數** 屬性是選擇性的，如果函式的任何參數都不需要屬性，您就可以省略它。 但是，若要被辨識為 advanced 函式，而不是簡單的函式，則函式必須有 **CmdletBinding** 屬性或 **參數** 屬性，或兩者都是。

**Parameter** 屬性有定義參數特性的引數，例如參數是否為強制性或選擇性參數。

使用下列語法來宣告 **參數** 屬性、引數和引數值。 括住引數和其值的括弧必須緊接在無中間空間的 **參數** 。

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

使用逗號來分隔括弧內的引數。 使用下列語法來宣告 **參數** 屬性的兩個引數。

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

從 **參數** 屬性省略時， **參數** 屬性的布林引數類型預設為 **False** 。 將引數值設定為， `$true` 或只依名稱列出引數。 例如，下列 **參數** 屬性是相等的。

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

如果您使用不含引數的 **Parameter** 屬性（attribute）做為使用 **CmdletBinding** 屬性的替代方案，則仍然需要在屬性名稱後面加上括弧。

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a>強制引數

`Mandatory`引數表示需要參數。 如果未指定這個引數，則參數是選擇性的。

下列範例會宣告 **ComputerName** 參數。 它會使用 `Mandatory` 引數讓參數變成強制參數。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a>Position 引數

`Position`當命令中使用參數時，引數會決定是否需要參數名稱。 當參數宣告包含 `Position` 引數時，可以省略參數名稱，而 PowerShell 會依據命令中未具名引數值清單中的位置或順序來識別未命名的參數值。

如果 `Position` 未指定引數，參數名稱或參數名稱別名或縮寫在命令中使用參數時，必須在參數值之前。

依預設，所有函數參數都是位置。 PowerShell 會依照在函式中宣告參數的順序，將位置編號指派給參數。 若要停用此功能，請將 `PositionalBinding` **CmdletBinding** 屬性的引數值設定為 `$False` 。 `Position`引數優先于 `PositionalBinding` **CmdletBinding** 屬性的引數值。 如需詳細資訊，請參閱 `PositionalBinding` [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)中的。

引數的值 `Position` 會指定為整數。 位置值 **0** 代表命令中的第一個位置，位置值 **1** 代表命令中的第二個位置，依此類推。

如果函式沒有位置參數，則 PowerShell 會根據參數的宣告順序，將位置指派給每個參數。
不過，最佳作法是不要依賴此指派。 當您想要將參數設為位置時，請使用 `Position` 引數。

下列範例會宣告 **ComputerName** 參數。 它會使用 `Position` 值為 **0** 的引數。 因此，當 `-ComputerName` 從命令省略時，其值必須是命令中的第一個或唯一未命名的參數值。

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a>ParameterSetName 引數

`ParameterSetName`引數指定參數所屬的參數集。 如果未指定任何參數集，則參數屬於函式所定義的所有參數集。 因此，若要成為唯一的，每個參數集都必須至少有一個參數不是任何其他參數集的成員。

> [!NOTE]
> 針對 Cmdlet 或函式，有32個參數集的限制。

下列範例會宣告參數集中的 **ComputerName** 參數 `Computer` 、參數集中的使用者 **名稱** 參數 `User` ，以及兩個參數集中的 **摘要** 參數。

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false)]
    [Switch]
    $Summary
)
```

在 `ParameterSetName` 每個引數中只能指定一個值，而且 `ParameterSetName` 每個 **參數** 屬性只能指定一個引數。 若要指出參數出現在一個以上的參數集中，請新增其他 **參數** 屬性。

下列範例會明確地將 **Summary** 參數加入 `Computer` 和 `User` 參數集。 **摘要** 參數在參數集內是選擇性的 `Computer` ，且在參數集中為必要項 `User` 。

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false, ParameterSetName="Computer")]
    [Parameter(Mandatory=$true, ParameterSetName="User")]
    [Switch]
    $Summary
)
```

如需參數集的詳細資訊，請參閱 [關於參數集](about_parameter_sets.md)。

#### <a name="valuefrompipeline-argument"></a>ValueFromPipeline 引數

`ValueFromPipeline`引數指出參數接受來自管線物件的輸入。 如果函式接受整個物件，而不只是物件的屬性，請指定此引數。

下列範例會宣告必要的 **ComputerName** 參數，並接受從管線傳遞至函式的物件。

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a>ValueFromPipelineByPropertyName 引數

`ValueFromPipelineByPropertyName`引數表示參數會接受來自管線物件之屬性的輸入。 物件屬性必須與參數具有相同的名稱或別名。

例如，如果函式具有 **computername** 參數，且管道物件具有 **computername** 屬性，則 **computername** 屬性的值會指派給函數的 **computername** 參數。

下列範例會宣告必要的 **ComputerName** 參數，並接受透過管線傳遞至函式的物件 **computername** 屬性的輸入。

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> 接受管線輸入 (`by Value`) 或 (`by PropertyName`) 可在參數上使用 _延遲_ 系結腳本區塊的型別參數。
>
> _延遲_ 系結腳本區塊會在 **ParameterBinding** 期間自動執行。 結果會系結至參數。 延遲系結對於定義為類型或的參數無法運作 `ScriptBlock` `System.Object` 。 腳本區塊會在未叫用的 _情況下_ 傳遞。
>
> 您可以在這裡閱讀 _延遲_ 系結腳本區塊 [about_Script_Blocks md](about_Script_Blocks.md)。

#### <a name="valuefromremainingarguments-argument"></a>ValueFromRemainingArguments 引數

`ValueFromRemainingArguments`引數表示參數會接受命令中所有未指派給函式之其他參數的參數值。

下列範例會宣告必要的 **值** 參數，以及接受已提交給函式之所有其餘參數值的 **剩餘** 參數。

```powershell
function Test-Remainder
{
     param(
         [string]
         [Parameter(Mandatory = $true, Position=0)]
         $Value,
         [string[]]
         [Parameter(Position=1, ValueFromRemainingArguments)]
         $Remaining)
     "Found $($Remaining.Count) elements"
     for ($i = 0; $i -lt $Remaining.Count; $i++)
     {
        "${i}: $($Remaining[$i])"
     }
}
Test-Remainder first one,two
```

```Output
Found 2 elements
0: one
1: two
```

> [!NOTE]
> 在 PowerShell 6.2 之前， **ValueFromRemainingArguments** 集合已聯結為索引 **0** 下的單一實體。

#### <a name="helpmessage-argument"></a>HelpMessage 引數

`HelpMessage`引數指定包含參數或其值之簡短描述的字串。 當命令缺少強制參數值時，PowerShell 會在出現的提示中顯示此訊息。 這個引數對選擇性參數沒有任何作用。

下列範例會宣告必要的 **ComputerName** 參數，以及說明預期參數值的說明訊息。

如果函式沒有其他以 [批註為基礎的說明](./about_comment_based_help.md) 語法 (例如， `.SYNOPSIS`) 則這則訊息也會顯示在 `Get-Help` 輸出中。

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a>Alias 屬性

**Alias** 屬性會建立參數的替代名稱。
您可以指派給參數的別名數目沒有任何限制。

下列範例顯示將 **CN** 和 **MachineName** 別名新增至必要 **ComputerName** 參數的參數宣告。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a>SupportsWildcards 屬性

**SupportsWildcards** 屬性是用來指出參數接受萬用字元值。 下列範例顯示支援萬用字元值的強制 **路徑** 參數的參數宣告。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

使用這個屬性不會自動啟用萬用字元支援。 Cmdlet 開發人員必須執行程式碼來處理萬用字元輸入。 支援的萬用字元會根據基礎 API 或 PowerShell 提供者而有所不同。 如需詳細資訊，請參閱 [about_Wildcards](about_Wildcards.md)。

### <a name="parameter-and-variable-validation-attributes"></a>參數和變數驗證屬性

驗證屬性可指示 PowerShell 測試使用者在呼叫 advanced 函式時所提交的參數值。 如果參數值未通過測試，則會產生錯誤，而且不會呼叫函數。 參數驗證只會套用至提供的輸入，而且不會驗證任何其他值，例如預設值。

您也可以使用驗證屬性來限制使用者可為變數指定的值。 當您搭配使用類型轉換器與驗證屬性時，必須在屬性之前定義類型轉換器。

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a>AllowNull 驗證屬性

**AllowNull** 屬性可讓必要參數的值為 `$null` 。 下列範例會宣告一個可以有 **null** 值的 hashtable **get-computerinfo** 參數。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> 如果類型轉換器設定為 string， **AllowNull** 屬性就無法運作，因為字串型別不接受 null 值。 您可以在此案例中使用 **AllowEmptyString** 屬性。

### <a name="allowemptystring-validation-attribute"></a>AllowEmptyString 驗證屬性

**AllowEmptyString** 屬性可讓必要參數的值為空字串 (`""`) 。 下列範例會宣告可具有空字串值的 **ComputerName** 參數。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a>AllowEmptyCollection 驗證屬性

**AllowEmptyCollection** 屬性可讓必要參數的值為空集合 `@()` 。 下列範例宣告的 **ComputerName** 參數可以有空的集合值。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a>ValidateCount 驗證屬性

**ValidateCount** 屬性會指定參數所接受的參數值的最小和最大數目。 如果命令中呼叫函數的參數值數目超出該範圍，則 PowerShell 會產生錯誤。

下列參數宣告會建立 **ComputerName** 參數，該參數會採用一到五個參數值。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a>ValidateLength 驗證屬性

**ValidateLength** 屬性會指定參數或變數值中的最小和最大字元數。 如果為參數或變數指定的值長度超出範圍，則 PowerShell 會產生錯誤。

在下列範例中，每個電腦名稱稱都必須有一到十個字元。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

在下列範例中，變數的值 `$number` 必須是長度最少一個字元，最多10個字元。

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> 在此範例中，的值 `01` 會以單引號括住。 **ValidateLength** 屬性不會接受數位，而不會以引號括住。

### <a name="validatepattern-validation-attribute"></a>ValidatePattern 驗證屬性

**ValidatePattern** 屬性會指定與參數或變數值比較的正則運算式。 如果值不符合正則運算式模式，則 PowerShell 會產生錯誤。

在下列範例中，參數值必須包含四位數的數位，而且每個數位都必須是0到9的數位。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

在下列範例中，變數的值 `$number` 必須正好是四位數的數位，而且每個數位都必須是0到9的數位。

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a>ValidateRange 驗證屬性

**ValidateRange** 屬性會指定每個參數或變數值的數值範圍或 **ValidateRangeKind** 列舉值。
如果任何值超出該範圍，PowerShell 就會產生錯誤。

**ValidateRangeKind** 列舉允許下列值：

- **正數** -大於零的數位。
- **負** -小於零的數位。
- **NonPositive** -小於或等於零的數位。
- 非 **負值** -大於或等於零的數位。

在下列範例中， **嘗試** 參數的值必須介於0到10之間。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

在下列範例中，變數的值 `$number` 必須介於0到10之間。

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

在下列範例中，變數的值 `$number` 必須大於零。

```powershell
[Int32][ValidateRange("Positive")]$number = 1
```

### <a name="validatescript-validation-attribute"></a>ValidateScript 驗證屬性

**ValidateScript** 屬性會指定用來驗證參數或變數值的腳本。 PowerShell 會使用管線將值傳送至腳本，如果腳本傳回或腳本擲回例外狀況，則會產生錯誤 `$false` 。

當您使用 **ValidateScript** 屬性時，所驗證的值會對應至 `$_` 變數。 您可以使用 `$_` 變數來參考腳本中的值。

在下列範例中， **EventDate** 參數的值必須大於或等於目前的日期。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

在下列範例中，變數的值 `$date` 必須大於或等於目前的日期和時間。

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> 如果您使用 **ValidateScript** ，則無法將 `$null` 值傳遞給參數。 當您傳遞 null 值時 **ValidateScript** 無法驗證引數。

### <a name="validateset-attribute"></a>ValidateSet 屬性

**ValidateSet** 屬性會為參數或變數指定一組有效值，並啟用 tab 鍵自動完成。 如果參數或變數值不符合集合中的值，PowerShell 就會產生錯誤。 在下列範例中， **Detail** 參數的值只能是 Low、Average 或 High。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

在下列範例中，變數的值 `$flavor` 必須是巧克力、草莓或香草。

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

只要在腳本內指派該變數，就會發生驗證。 例如，下列程式會在執行時間產生錯誤：

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

#### <a name="dynamic-validateset-values"></a>動態 validateSet 值

您可以使用 **類別** ，在執行時間動態產生 **ValidateSet** 的值。 在下列範例中， `$Sound` 會透過名為 **SoundNames** 的 **類別** 產生變數的有效值，以檢查三個檔案系統路徑的可用音效檔案：

```powershell
Class SoundNames : System.Management.Automation.IValidateSetValuesGenerator {
    [String[]] GetValidValues() {
        $SoundPaths = '/System/Library/Sounds/',
            '/Library/Sounds','~/Library/Sounds'
        $SoundNames = ForEach ($SoundPath in $SoundPaths) {
            If (Test-Path $SoundPath) {
                (Get-ChildItem $SoundPath).BaseName
            }
        }
        return [String[]] $SoundNames
    }
}
```

`[SoundNames]`然後，類別會實作為動態 **ValidateSet** 值，如下所示：

```powershell
Param(
    [ValidateSet([SoundNames])]
    [String]$Sound
)
```

### <a name="validatenotnull-validation-attribute"></a>ValidateNotNull 驗證屬性

**ValidateNotNull** 屬性指定參數值不能是 `$null` 。 如果參數值為，PowerShell 會產生錯誤 `$null` 。

**ValidateNotNull** 屬性是設計用來在參數為選擇性且類型未定義或具有無法以隱含方式轉換 null 值（例如 **物件** ）的類型轉換器時使用。 如果您指定的型別會隱含地轉換 null 值（例如 **字串** ），即使使用 **ValidateNotNull** 屬性，也會將 null 值轉換為空字串。 針對此案例，請使用 **ValidateNotNullOrEmpty**

在下列範例中， **ID** 參數的值不能是 `$null` 。

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a>ValidateNotNullOrEmpty 驗證屬性

**ValidateNotNullOrEmpty** 屬性指定參數值不能是 `$null` ，也不能是 () 的空字串 `""` 。 如果在函式呼叫中使用參數，但其值為 `$null` 、空字串 (`""`) 或空陣列，則 PowerShell 會產生錯誤 `@()` 。

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a>ValidateDrive 驗證屬性

**ValidateDrive** 屬性指定參數值必須代表路徑，而這只是指允許的磁片磁碟機。 如果參數值參考了允許的磁片磁碟機，則 PowerShell 會產生錯誤。 除了磁片磁碟機本身以外，不會驗證路徑是否存在。

如果您使用相對路徑，則目前磁片磁碟機必須位於允許的磁片磁碟機清單中。

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a>ValidateUserDrive 驗證屬性

**ValidateUserDrive** 屬性指定參數值必須代表參考 `User` 磁片磁碟機的路徑。 如果路徑參考不同的磁片磁碟機，PowerShell 會產生錯誤。 驗證屬性只會測試路徑的磁片磁碟機部分是否存在。

如果您使用相對路徑，則目前磁片磁碟機必須是 `User` 。

```powershell
function Test-UserDrivePath{
    [OutputType([bool])]
    Param(
      [Parameter(Mandatory=, Position=0)][ValidateUserDrive()][String]$Path
      )
    $True
}

Test-UserDrivePath -Path C:\
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. The path
argument drive C does not belong to the set of approved drives: User.
Supply a path argument with an approved drive.
```

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. Cannot
find drive. A drive with the name 'User' does not exist.
```

您可以 `User` 在 (JEA) 會話設定的足夠管理中定義磁片磁碟機。 在此範例中，我們會建立使用者：磁片磁碟機。

```powershell
New-PSDrive -Name 'User' -PSProvider FileSystem -Root $env:HOMEPATH
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
User               75.76         24.24 FileSystem    C:\Users\ExampleUser

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
True
```

### <a name="validatetrusteddata-validation-attribute"></a>ValidateTrustedData 驗證屬性

此屬性已新增至 PowerShell 6.1.1。

目前，此屬性是由 PowerShell 本身在內部使用，並非供外部使用。

## <a name="dynamic-parameters"></a>動態參數

動態參數是 Cmdlet、函式或腳本的參數，只有在特定條件下才能使用。

例如，只有在提供者磁片磁碟機或提供者磁片磁碟機的特定路徑中使用 Cmdlet 時，有數個提供者 Cmdlet 具有可用的參數。 例如，只有在 **Encoding** `Add-Content` `Get-Content` `Set-Content` 檔案系統磁片磁碟機中使用時，才可以在、和 Cmdlet 上使用 Encoding 參數。

您也可以建立只在函數命令中使用另一個參數時，或當另一個參數具有特定值時才會出現的參數。

動態參數可能很有用，但只在必要時才使用，因為使用者可能很難探索。 若要尋找動態參數，使用者必須在提供者路徑中，使用 Cmdlet 的 **ArgumentList** 參數 `Get-Command` ，或使用的 **path** 參數 `Get-Help` 。

若要建立函數或腳本的動態參數，請使用 `DynamicParam` 關鍵字。

語法如下：

`DynamicParam {<statement-list>}`

在語句清單中，使用 `If` 語句來指定函數中可用參數的條件。

使用 `New-Object` Cmdlet 來建立 **RuntimeDefinedParameter** 物件，以代表參數並指定其名稱。

您可以使用 `New-Object` 命令來建立 **ParameterAttribute** 物件，以代表參數的屬性，例如 **強制** 、 **位置** 或 **ValueFromPipeline** 或其參數集。

下列範例顯示範例函式，其中包含名為 **Name** 和 **Path** 的標準參數，以及一個名為 **DP1** 的選擇性動態參數。 **DP1** 參數位於 `PSet1` 參數集中，且具有類型 `Int32` 。
**DP1** `Get-Sample` 只有當 **Path** 參數的值以開頭 `HKLM:` ，表示在登錄磁片磁碟機中使用時，DP1 參數才可在函式中使用 `HKEY_LOCAL_MACHINE` 。

```powershell
function Get-Sample {
  [CmdletBinding()]
  Param([String]$Name, [String]$Path)

  DynamicParam
  {
    if ($Path.StartsWith("HKLM:"))
    {
      $attributes = New-Object -Type `
        System.Management.Automation.ParameterAttribute
      $attributes.ParameterSetName = "PSet1"
      $attributes.Mandatory = $false
      $attributeCollection = New-Object `
        -Type System.Collections.ObjectModel.Collection[System.Attribute]
      $attributeCollection.Add($attributes)

      $dynParam1 = New-Object -Type `
        System.Management.Automation.RuntimeDefinedParameter("DP1", [Int32],
          $attributeCollection)

      $paramDictionary = New-Object `
        -Type System.Management.Automation.RuntimeDefinedParameterDictionary
      $paramDictionary.Add("DP1", $dynParam1)
      return $paramDictionary
    }
  }
}
```

如需詳細資訊，請參閱 [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter)。

## <a name="switch-parameters"></a>切換參數

Switch 參數是沒有參數值的參數。 它們只有在使用時才有效，而且只有一個效果。

例如， **powershell.exe** 的 **NoProfile** 參數是切換參數。

若要在函數中建立切換參數，請 `Switch` 在參數定義中指定類型。

例如：

```powershell
Param([Switch]<ParameterName>)
```

或者，您可以使用另一種方法：

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

切換參數很容易使用，而且偏好使用布林值參數，而這些參數的語法比較困難。

例如，若要使用切換參數，使用者可以在命令中輸入參數。

`-IncludeAll`

若要使用布林值參數，使用者可以輸入參數和布林值。

`-IncludeAll:$true`

建立切換參數時，請謹慎選擇參數名稱。 請確定參數名稱會將參數的效果傳達給使用者。
避免不明確的詞彙（例如，可能代表需要值的 **篩選** 或 **最大** 值）。

## <a name="argumentcompleter-attribute"></a>ArgumentCompleter 屬性

**ArgumentCompleter** 屬性可讓您將 tab 鍵自動完成值新增至特定參數。 必須針對需要 tab 鍵自動完成的每個參數定義 **ArgumentCompleter** 屬性。 類似于 **get-dynamicparameters** ，當使用者按下 <kbd>Tab 鍵</kbd> 之後，可在執行時間計算可用的值。

若要加入 **ArgumentCompleter** 屬性，您需要定義判斷值的腳本區塊。 腳本區塊必須以下列指定的順序來採用下列參數。 參數的名稱並不重要，因為 positionally 會提供值。

語法如下：

```powershell
Param(
    [Parameter(Mandatory)]
    [ArgumentCompleter({
        param ( $commandName,
                $parameterName,
                $wordToComplete,
                $commandAst,
                $fakeBoundParameters )
        # Perform calculation of tab completed values here.
    })]
)
```

### <a name="argumentcompleter-script-block"></a>ArgumentCompleter 腳本區塊

腳本區塊參數會設定為下列值：

- `$commandName` (位置 0) -此參數會設定為腳本區塊提供 tab 鍵自動完成之命令的名稱。
- `$parameterName` (位置 1) -此參數會設定為其值需要 tab 鍵自動完成的參數。
- `$wordToComplete` (位置 2) -此參數會設定為使用者在按下 <kbd>Tab 鍵</kbd>之前所提供的值。您的腳本區塊應該使用此值來判斷 tab 鍵自動完成值。
- `$commandAst` (位置 3) -這個參數會設定為目前輸入行 (AST) 的抽象語法樹狀目錄。 如需詳細資訊，請參閱 [Ast 類別](/dotnet/api/system.management.automation.language.ast)。
- `$fakeBoundParameters` (位置 4) - `$PSBoundParameters` 在使用者按下索引標籤之前，此參數會設定為包含 Cmdlet 之<kbd>Tab</kbd>的雜湊表。如需詳細資訊，請參閱[about_Automatic_Variables](about_Automatic_Variables.md)。

**ArgumentCompleter** 腳本區塊必須使用管線來展開值，例如 `ForEach-Object` 、 `Where-Object` 或其他適合的方法。
傳回值陣列會導致 PowerShell 將整個陣列視為 **一個** tab 鍵自動完成值。

下列範例會將 tab 鍵自動完成新增至 **Value** 參數。 如果只指定 **值** 參數，則會顯示 **值** 的所有可能值或引數。 當指定 **型** 別參數時， **Value** 參數只會顯示該類型的可能值。

此外， `-like` 運算子可確保如果使用者輸入下列命令並使用 <kbd>Tab 鍵</kbd> 自動完成，則只會傳回 **Apple** 。

`Test-ArgumentCompleter -Type Fruits -Value A`

```powershell
function Test-ArgumentCompleter {
[CmdletBinding()]
 param (
        [Parameter(Mandatory=$true)]
        [ValidateSet('Fruits', 'Vegetables')]
        $Type,
        [Parameter(Mandatory=$true)]
        [ArgumentCompleter( {
            param ( $commandName,
                    $parameterName,
                    $wordToComplete,
                    $commandAst,
                    $fakeBoundParameters )

            $possibleValues = @{
                Fruits = @('Apple', 'Orange', 'Banana')
                Vegetables = @('Tomato', 'Squash', 'Corn')
            }
            if ($fakeBoundParameters.ContainsKey('Type'))
            {
                $possibleValues[$fakeBoundParameters.Type] | Where-Object {
                    $_ -like "$wordToComplete*"
                }
            }
            else
            {
                $possibleValues.Values | ForEach-Object {$_}
            }
        } )]
        $Value
      )
}
```

## <a name="see-also"></a>另請參閱

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
