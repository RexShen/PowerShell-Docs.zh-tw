---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-String
ms.openlocfilehash: 665a0ca8332c4052b59362c7947e408ba811c5f2
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "93206184"
---
# ConvertFrom-String

## 概要
從字串內容中解壓縮和剖析結構化屬性。

## SYNTAX

### ByDelimiter (預設) 

```
ConvertFrom-String [-Delimiter <String>] [-PropertyNames <String[]>] [-InputObject] <String>
 [<CommonParameters>]
```

### TemplateParsing

```
ConvertFrom-String [-TemplateFile <String[]>] [-TemplateContent <String[]>] [-IncludeExtent] [-UpdateTemplate]
 [-InputObject] <String> [<CommonParameters>]
```

## DESCRIPTION

**Convertfrom-string-String** Cmdlet 會從字串內容中解壓縮和剖析結構化屬性。
此 Cmdlet 會藉由剖析傳統文字資料流程中的文字來產生物件。
針對管線中的每個字串，此 Cmdlet 會依分隔符號或剖析運算式來分割輸入，然後將屬性名稱指派給每個產生的分割元素。
您可以提供這些屬性名稱;如果不這麼做，系統會自動為您產生它們。

Cmdlet 的預設參數集（ **ByDelimiter** ）會完全在正則運算式分隔符號上進行分割。
當 Cmdlet 執行時，它不會執行引號比對或分隔符號的轉義 `Import-Csv` 。

Cmdlet 的替代參數集 **TemplateParsing** 會從正則運算式所捕捉的群組產生元素。 如需正則運算式的詳細資訊，請參閱 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)。

這個 Cmdlet 支援兩種模式：基本分隔剖析和自動產生的範例驅動剖析。

根據預設，分隔的剖析將輸入從空白字元位置分割，並將屬性名稱指派給產生的群組。

您可以使用管線將 `ConvertFrom-String` 結果傳送至其中一個 Cmdlet 來自訂分隔符號 `Format-*` ，也可以使用 **分隔符號** 參數。

此 Cmdlet 也支援根據 [FlashExtract、Microsoft research 的研究工作](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/)，自動產生的範例驅動剖析。

## 範例

### 範例1：產生具有預設屬性名稱的物件

```powershell
"Hello World" | ConvertFrom-String
```

```Output
P1    P2
--    --
Hello World
```

此命令會產生具有預設屬性名稱 **P1** 和 **P2** 的物件。

### 範例1A：瞭解產生的物件

此命令會產生一個具有 **P1** 、 **P2** 、屬性的物件。根據預設，這兩個屬性都是 **字串** 類型。

```powershell
"Hello World" | ConvertFrom-String | Get-Member
```

```Output

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
P1          NoteProperty string P1=Hello
P2          NoteProperty string P2=World
```

### 範例2：使用分隔符號產生具有預設屬性名稱的物件

此命令會使用反斜線 () 作為分隔符號，產生具有網域和使用者名稱的物件 `\` 。 使用正則運算式時，必須以另一個反斜線來換用反斜線字元。

```powershell
"Contoso\Administrator" | ConvertFrom-String -Delimiter "\\"
```

```Output
P1      P2
--      --
Contoso Administrator
```

### 範例3：產生包含兩個命名屬性的物件

下列範例會從 Windows 主機檔案專案建立物件。

```powershell
$content = Get-Content C:\Windows\System32\drivers\etc\hosts
$content = $content -match "^[^#]"
$content | ConvertFrom-String -PropertyNames IP, Server
```

```Output
IP             Server
--             ------
192.168.7.10   W2012R2
192.168.7.20   W2016
192.168.7.101  WIN8
192.168.7.102  WIN10
```

Cmdlet 會將 `Get-Content` Windows 主機檔案的內容儲存在中 `$content` 。 第二個命令會使用符合 () 開頭之任何一行的正則運算式，移除主機檔案開頭的任何批註 `#` 。 最後一個命令會將剩餘的文字轉換成具有 **伺服器** 和 **IP** 屬性的物件。

### 範例4：使用運算式作為 TemplateContent 參數的值，將結果儲存在變數中。

此命令會使用運算式做為 **TemplateContent** 參數的值。
為了簡單起見，運算式會儲存在變數中。
Windows PowerShell 瞭解管線上所使用的字串 `ConvertFrom-String` 有三個屬性：

- **名稱**
- **電話**
- **age**

```powershell
$template = @'
{Name*:Phoebe Cat}, {phone:425-123-6789}, {age:6}
{Name*:Lucky Shot}, {phone:(206) 987-4321}, {age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789    6
Lucky Shot    (206) 987-4321  12
Elephant Wise 425-888-7766    87
Wild Shrimp   (111)  222-3333 1
```

輸入中的每一行都是由樣本相符專案來評估。 如果行符合模式中提供的範例，則會將值解壓縮並傳遞至輸出變數。

範例資料 `$template` 提供兩種不同的電話格式：

- `425-123-6789`
- `(206) 987-4321`

範例資料也提供兩種不同的年齡格式：

- `6`
- `12`

這表示將無法辨識像這樣的電話 `(206) 987 4321` ，因為沒有任何符合該模式的範例資料，因為沒有連字號。

### 範例5：對產生的屬性指定資料類型

這是上述範例4的相同範例。
差別在於模式字串包含每個所需屬性的資料類型。

```powershell
$template = @'
{[string]Name*:Phoebe Cat}, {[string]phone:425-123-6789}, {[int]age:6}
{[string]Name*:Lucky Shot}, {[string]phone:(206) 987-4321}, {[int]age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789      6
Lucky Shot    (206) 987-4321   12
Elephant Wise 425-888-7766     87
Wild Shrimp   (111)  222-3333   1
```

```powershell
$PersonalData | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
age         NoteProperty int age=6
Name        NoteProperty string Name=Phoebe Cat
phone       NoteProperty string phone=425-123-6789
```

此 `Get-Member` Cmdlet 會用來顯示 **age** 屬性為整數。

## PARAMETERS

### -Delimiter

指定識別元素之間界限的正則運算式。
分割所建立的專案會成為所產生之物件中的屬性。
分隔符號最後會用於呼叫類型的 **Split** 方法 `[System.Text.RegularExpressions.RegularExpression]` 。

```yaml
Type: System.String
Parameter Sets: ByDelimiter
Aliases: DEL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeExtent

指出此 Cmdlet 包含預設會移除的範圍文字屬性。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: IE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定從管線接收的字串，或包含字串物件的變數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -之 propertynames

指定要在產生的物件中指派分割值之屬性名稱的陣列。
您分割或剖析的每一行文字都會產生代表屬性值的元素。
如果專案是 capture 群組的結果，而且該 capture 群組的名稱為 (例如 `(?<name>)` 或 `(?'name')` ) ，則該 capture 群組的名稱會指派給屬性。

如果您在 **PropertyName** 陣列中提供任何元素，這些名稱會指派給尚未命名的屬性。

如果您提供的屬性名稱比欄位更多，則 PowerShell 會忽略額外的屬性名稱。 如果您未指定足夠的屬性名稱來命名所有欄位，則 PowerShell 會自動將數值屬性名稱指派給任何未命名的屬性： **P1** 、 **P2** 等等。

```yaml
Type: System.String[]
Parameter Sets: ByDelimiter
Aliases: PN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateContent

指定運算式或儲存為變數的運算式，以描述此 Cmdlet 指派字串的屬性。 範本欄位規格的語法如下： `{[optional-typecast]<name>:<example-value>}` 。

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TemplateFile

以陣列的形式指定檔案，其中包含所要剖析之字串的範本。
在範本檔案中，屬性和其值會以括弧括住，如下所示。
如果屬性（例如 **Name** 屬性和其相關聯的其他屬性）出現多次，您可以 () 加入星號， `*` 表示這會產生多筆記錄。 這可避免將多個屬性解壓縮成單一記錄。

```
{Name*:David Chew}
{City:Redmond}, {State:WA}
{Name*:Evan Narvaez}    {Name*:Antonio Moreno}
{City:Issaquah}, {State:WA}
```

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UpdateTemplate

指出此 Cmdlet 會將學習演算法的結果儲存到範本檔案中的批註。
這可讓演算法學習程式更快。
若要使用此參數，您也必須使用 **TemplateFile** 參數指定範本檔案。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: UT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

## 輸出

## 注意

## 相關連結

[Convertfrom-string-字串：以範例為基礎的文字剖析](https://devblogs.microsoft.com/powershell/convertfrom-string-example-based-text-parsing/)

[ConvertFrom-StringData](ConvertFrom-StringData.md)

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[ConvertTo-Xml](ConvertTo-Xml.md)
