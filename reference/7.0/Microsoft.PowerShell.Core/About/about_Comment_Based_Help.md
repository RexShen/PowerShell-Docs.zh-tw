---
description: 說明如何撰寫函式和腳本的批註式說明主題。
keywords: powershell,cmdlet
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comment_based_help?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comment_Based_Help
ms.openlocfilehash: cb7ac6e7b4ec3afb95c9864665490633fdad6c5c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207851"
---
# <a name="about-comment-based-help"></a>關於以批註為基礎的說明

## <a name="short-description"></a>簡短描述
說明如何撰寫函式和腳本的批註式說明主題。

## <a name="long-description"></a>完整描述

您可以使用特殊的說明批註關鍵字來撰寫函數和腳本的批註式說明主題。

[Get-help](xref:Microsoft.PowerShell.Core.Get-Help) Cmdlet 會顯示以批註為基礎的說明，其格式會顯示從 XML 檔案產生的 Cmdlet 說明主題。 使用者可以使用的所有參數（ `Get-Help` 如 **詳細** 、 **完整** 、 **範例** 和 **線上** ）來顯示以批註為基礎的說明內容。

您也可以針對函式和腳本撰寫以 XML 為基礎的說明檔。 若要啟用 `Get-Help` Cmdlet 來尋找函式或腳本的 XML 型說明檔，請使用 `.ExternalHelp` 關鍵字。 如果沒有這個關鍵字，則找 `Get-Help` 不到函數或腳本的 XML 型說明主題。

本主題說明如何撰寫函數和腳本的說明主題。 如需有關如何顯示函式和腳本的說明主題的詳細資訊，請參閱 [get-help](xref:Microsoft.PowerShell.Core.Get-Help)。

[Update-help](xref:Microsoft.PowerShell.Core.Update-Help)和[Save help](xref:Microsoft.PowerShell.Core.Save-Help) CMDLET 只適用于 XML 檔案。 可更新的說明不支援以批註為基礎的說明主題。

## <a name="syntax-for-comment-based-help"></a>以批註為基礎的說明語法

以批註為基礎的說明語法如下所示：

```
# .<help keyword>
# <help content>
```

或

```
<#
.<help keyword>
<help content>
#>
```

以批註為基礎的說明會以一系列的批註撰寫。 您可以在 `#` 每一行批註之前輸入批註符號，也可以使用 `<#` 和 `#>` 符號來建立批註區塊。 批註區塊內的所有行都會轉譯為批註。

以批註為基礎的說明主題中的所有程式列都必須是連續的。 如果以批註為基礎的說明主題遵循的批註不在說明主題中，則最後一個非說明批註行和批註式說明的開頭至少必須有一個空白行。

關鍵字會定義以批註為基礎的說明的每個區段。 每個以批註為基礎的說明關鍵字之前都是點 `.` 。 關鍵字可以依任何順序出現。 關鍵字名稱不區分大小寫。

例如，關鍵字會在 `.Description` 函數或腳本的描述之前。

```
<#
.Description
Get-Function displays the name and syntax of all functions in the session.
#>
```

批註區塊必須至少包含一個關鍵字。 某些關鍵字（例如 `.EXAMPLE` ）可能會在相同的批註區塊中出現多次。 每個關鍵字的說明內容都是在關鍵字後面的那一行開始，而且可以橫跨多行。

## <a name="syntax-for-comment-based-help-in-functions"></a>函數中以批註為基礎的說明語法

以批註為基礎的函式說明可以出現在下列三個位置的其中一個位置：

- 在函數主體的開頭。
- 在函數主體的結尾。
- 關鍵字之前 `function` 。 函數說明和關鍵字的最後一行之間不能有一個以上的空白行 `function` 。

例如：

```powershell
function Get-Function
{
<#
.<help keyword>
<help content>
#>

  # function logic
}
```

或

```powershell
function Get-Function
{
   # function logic

<#
.<help keyword>
<help content>
#>
}
```

或

```powershell
<#
.<help keyword>
<help content>
#>
function Get-Function { }
```

## <a name="syntax-for-comment-based-help-in-scripts"></a>腳本中以批註為基礎的說明語法

腳本的批註式說明可以出現在腳本中的下列兩個位置的其中一個位置。

- 指令檔的開頭。 腳本說明可以在腳本中的前面加上批註和空白行。

  如果腳本主體中的第一個專案 (在 [說明]) 之後是函式宣告，則腳本說明和函式宣告的結尾必須至少有兩個空白行。 否則，說明會被視為函數的說明，而不是腳本的說明。

- 指令檔的結尾。 但是，如果腳本已簽署，請在腳本檔案的開頭放置批註式說明。 腳本的結尾是由簽章區塊所佔用。

例如：

```powershell
<#
.<help keyword>
<help content>
#>


function Get-Function { }
```

或

```powershell
function Get-Function { }

<#
.<help keyword>
<help content>
#>
```

## <a name="syntax-for-comment-based-help-in-script-modules"></a>腳本模組中以批註為基礎的說明語法

在腳本模組中 `.psm1` ，以批註為基礎的說明會使用函數的語法，而非腳本的語法。 您無法使用腳本語法為腳本模組中定義的所有函式提供說明。

例如，如果您使用 `.ExternalHelp` 關鍵字來識別腳本模組中函式的 XML 架構說明檔，則必須將 `.ExternalHelp` 批註加入至每個函數。

```powershell
# .ExternalHelp <XML-file-name>
function <function-name>
{
  ...
}
```

## <a name="comment-based-help-keywords"></a>以批註為基礎的說明關鍵字

以下是以批註為基礎的有效說明關鍵字。 這些清單會依照它們一般出現在說明主題中的順序列出，以及其預期的用途。 這些關鍵字在批註式說明中可依任何順序出現，而且不區分大小寫。

### <a name="synopsis"></a>.簡介

函數或腳本的簡短描述。 在每個主題中，這個關鍵字只能使用一次。

### <a name="description"></a>.描述

函數或腳本的詳細描述。 在每個主題中，這個關鍵字只能使用一次。

### <a name="parameter"></a>.參數

參數的描述。 針對函式 `.PARAMETER` 或腳本語法中的每個參數新增關鍵字。

在與關鍵字相同的行上輸入參數名稱 `.PARAMETER` 。 在關鍵字後面的行上輸入參數描述 `.PARAMETER` 。 Windows PowerShell 會將 `.PARAMETER` 行和下一個關鍵字之間的所有文字或批註區塊的結尾，視為參數描述的一部分來解讀。
描述可包含段落分隔。

```
.PARAMETER  <Parameter-Name>
```

參數關鍵字可以在批註區塊中以任何順序出現，但函數或腳本語法會決定參數 (的順序，而其描述) 出現在說明主題中。 若要變更順序，請變更語法。

您也可以將批註放在函數或腳本語法中，緊接在參數變數名稱之前，以指定參數描述。 若要這樣做，您也必須具有至少一個關鍵字的批註區塊。

如果您同時使用語法批註和 `.PARAMETER` 關鍵字，則會使用與關鍵字相關聯的描述 `.PARAMETER` ，而語法批註會被忽略。

```powershell
<#
.SYNOPSIS
    Short description here
#>
function Verb-Noun {
    [CmdletBinding()]
    param (
        # This is the same as .Parameter
        [string]$Computername
    )
    # Verb the Noun on the computer
}
```

### <a name="example"></a>.例子

使用函數或腳本的範例命令，選擇性地接著範例輸出和描述。 針對每個範例重複此關鍵字。

### <a name="inputs"></a>.輸入

可以輸送至函式或腳本之物件的 .NET 類型。 您也可以包含輸入物件的描述。

### <a name="outputs"></a>.輸出

Cmdlet 傳回之物件的 .NET 類型。 您也可以包含所傳回物件的描述。

### <a name="notes"></a>.筆記

函數或腳本的其他相關資訊。

### <a name="link"></a>.連結

相關主題的名稱。 值會出現在 ". 底下的行。LINK "關鍵字，且前面必須加上批註符號 `#` 或包含在批註區塊中。

`.LINK`針對每個相關主題重複關鍵字。

此內容會顯示在說明主題的 [相關連結] 區段中。

`.Link`關鍵字內容也可以包含統一資源識別項 (URI) 至相同說明主題的線上版本。 當您使用的 **online** 參數時，就會開啟線上版本 `Get-Help` 。 URI 的開頭必須是 "HTTP" 或 "HTTPs"。

### <a name="component"></a>.元件

函數或腳本所使用的技術或功能名稱，或其相關的名稱。 的 **元件** 參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。

### <a name="role"></a>.作用

說明主題的使用者角色名稱。 的 **Role** 參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。

### <a name="functionality"></a>.功能

描述函式用途的關鍵字。 的 **功能** 參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。

### <a name="forwardhelptargetname"></a>.FORWARDHELPTARGETNAME

重新導向至指定命令的說明主題。 您可以將使用者重新導向至任何說明主題，包括函數、腳本、Cmdlet 或提供者的說明主題。

```powershell
# .FORWARDHELPTARGETNAME <Command-Name>
```

### <a name="forwardhelpcategory"></a>.FORWARDHELPCATEGORY

指定中專案的 [說明] 類別 `.ForwardHelpTargetName` 。 有效的值為 `Alias` 、、、、、、、、、、 `Cmdlet` `HelpFile` `Function` `Provider` `General` `FAQ` `Glossary` `ScriptCommand` `ExternalScript` `Filter` 或 `All` 。 使用這個關鍵字可避免在具有相同名稱的命令時產生衝突。

```powershell
# .FORWARDHELPCATEGORY <Category>
```

### <a name="remotehelprunspace"></a>.REMOTEHELPRUNSPACE

指定包含說明主題的會話。 輸入包含 **PSSession** 物件的變數。 這個關鍵字是由 [匯出-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) Cmdlet 用來尋找匯出命令的說明主題。

```powershell
# .REMOTEHELPRUNSPACE <PSSession-variable>
```

### <a name="externalhelp"></a>..EXTERNALHELP

為腳本或函式指定以 XML 為基礎的說明檔。

```powershell
# .EXTERNALHELP <XML Help File>
```

在 `.ExternalHelp` XML 檔案中記載函式或腳本時，需要關鍵字。 如果沒有這個關鍵字，則找不到函 `Get-Help` 式或腳本的 XML 架構說明檔。

`.ExternalHelp`關鍵字優先于其他以批註為基礎的說明關鍵字。 如果 `.ExternalHelp` 存在， `Get-Help` 即使找不到符合關鍵字值的說明主題，也不會顯示以批註為基礎的說明 `.ExternalHelp` 。

如果函式是由模組匯出，請將關鍵字的值設定 `.ExternalHelp` 為沒有路徑的檔案名。 `Get-Help` 在模組目錄的特定語言子目錄中尋找指定的檔案名。 函式的 XML 說明檔名稱沒有任何需求，但最佳做法是使用下列格式：

```
<ScriptModule.psm1>-help.xml
```

如果函式不包含在模組中，請包含以 XML 為基礎的說明檔路徑。 如果值包含路徑，且路徑包含 UI 文化特性特定子目錄，則會以 `Get-Help` 遞迴方式在子目錄中搜尋具有腳本或函式名稱的 XML 檔案，就像在模組目錄中所建立的語言回溯標準一樣。

如需有關 Cmdlet 說明 XML 架構說明檔案格式的詳細資訊，請參閱 MSDN library 中的 [如何撰寫 Cmdlet 說明](https://go.microsoft.com/fwlink/?LinkID=123415) 。

## <a name="autogenerated-content"></a>自動產生的內容

Cmdlet 會自動產生名稱、語法、參數清單、參數屬性資料表、一般參數和備註 `Get-Help` 。

### <a name="name"></a>Name

函數說明主題的 **名稱** 區段取自函數語法中的函式名稱。 腳本說明主題的 **名稱** 取自指令檔名。 若要變更名稱或其大小寫，請變更函數語法或指令檔名。

### <a name="syntax"></a>Syntax

說明主題的 **語法** 區段是從函數或腳本語法產生的。 若要將詳細資料新增至說明主題語法，例如參數的 .NET 型別，請將詳細資料新增至語法。 如果您未指定參數類型，則會將 **物件** 類型插入為預設值。

### <a name="parameter-list"></a>參數清單

說明主題中的參數清單是從函式或腳本語法，以及您使用關鍵字加入的描述所產生 `.Parameter` 。 函數參數會出現在說明主題的 **parameters** 區段中，其順序與函式或腳本語法中的順序相同。 參數名稱的拼寫和大小寫也取自語法。 它不會受到關鍵字所指定之參數名稱的影響 `.Parameter` 。

### <a name="common-parameters"></a>一般參數

**一般參數** 會加入至說明主題的語法和參數清單中，即使它們沒有任何作用。 如需一般參數的詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。

### <a name="parameter-attribute-table"></a>參數屬性工作表

`Get-Help` 產生當您使用的 **Full** 或 **parameter** 參數時，所顯示的參數屬性資料表 `Get-Help` 。 **必要** 的、 **位置** 和 **預設** 值屬性的值取自函數或腳本語法。

預設值和 **接受萬用字元** 的值不會出現在參數屬性工作表中，即使它們是在函式或腳本中定義也一樣。 若要協助使用者，請在參數描述中提供這項資訊。

### <a name="remarks"></a>備註

[ **說明** ] 主題的 [備註] 區段會從函數或腳本名稱自動產生。 您無法變更或影響其內容。

## <a name="examples"></a>範例

### <a name="comment-based-help-for-a-function"></a>函式以批註為基礎的說明

下列範例函數包含以批註為基礎的說明：

```powershell
function Add-Extension
{
param ([string]$Name,[string]$Extension = "txt")
$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name.
Takes any strings for the file name or extension.

.PARAMETER Name
Specifies the file name.

.PARAMETER Extension
Specifies the extension. "Txt" is the default.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension
or file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

結果如下所示：

```powershell
Get-Help -Name "Add-Extension" -Full
```

```Output
NAME

Add-Extension

SYNOPSIS

Adds a file name extension to a supplied name.

SYNTAX

Add-Extension [[-Name] <String>] [[-Extension] <String>]
[<CommonParameters>]

DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

PARAMETERS

-Name
Specifies the file name.

Required?                    false
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-Extension
Specifies the extension. "Txt" is the default.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type
"get-help about_commonparameters".

INPUTS
None. You cannot pipe objects to Add-Extension.

OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

Example 1

PS> extension -name "File"
File.txt

Example 2

PS> extension -name "File" -extension "doc"
File.doc

Example 3

PS> extension "File" "doc"
File.doc

RELATED LINKS

http://www.fabrikam.com/extension.html
Set-Item
```

### <a name="parameter-descriptions-in-function-syntax"></a>函數語法中的參數描述

這個範例與上一個範例相同，不同之處在于參數描述會以函數語法插入。 當描述很簡單時，此格式最有用。

```powershell
function Add-Extension
{
param
(

[string]
#Specifies the file name.
$name,

[string]
#Specifies the file name extension. "Txt" is the default.
$extension = "txt"
)

$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

### <a name="comment-based-help-for-a-script"></a>以批註為基礎的腳本說明

下列範例腳本包含以批註為基礎的說明。 請注意結尾和語句之間的空白行 `#>` `Param` 。 在沒有語句的腳本中，[ `Param` 說明] 主題和第一個函式宣告中的最後一個批註之間必須至少有兩個空白行。 如果沒有這些空白行，請 `Get-Help` 將說明主題與函式相關聯，而不是腳本。

```powershell
<#
.SYNOPSIS

Performs monthly data updates.

.DESCRIPTION

The Update-Month.ps1 script updates the registry with new data generated
during the past month and generates a report.

.PARAMETER InputPath
Specifies the path to the CSV-based input file.

.PARAMETER OutputPath
Specifies the name and path for the CSV-based output file. By default,
MonthlyUpdates.ps1 generates a name from the date and time it runs, and
saves the output in the local directory.

.INPUTS

None. You cannot pipe objects to Update-Month.ps1.

.OUTPUTS

None. Update-Month.ps1 does not generate any output.

.EXAMPLE

PS> .\Update-Month.ps1

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath `
C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
...
```

下列命令會取得腳本說明。 因為腳本不在環境變數中所列的目錄中 `$env:Path` ，所以 `Get-Help` 取得腳本說明的命令必須指定腳本路徑。

```powershell
Get-Help -Path .\update-month.ps1 -Full
```

```Output
# NAME

C:\ps-test\Update-Month.ps1

# SYNOPSIS

Performs monthly data updates.

# SYNTAX

C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
<String>] [<CommonParameters>]

# DESCRIPTION

The Update-Month.ps1 script updates the registry with new data
generated during the past month and generates a report.

# PARAMETERS

-InputPath
Specifies the path to the CSV-based input file.

Required?                    true
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-OutputPath
Specifies the name and path for the CSV-based output file. By
default, MonthlyUpdates.ps1 generates a name from the date
and time it runs, and saves the output in the local directory.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type,
"get-help about_commonparameters".

# INPUTS

None. You cannot pipe objects to Update-Month.ps1.

# OUTPUTS

None. Update-Month.ps1 does not generate any output.

Example 1

PS> .\Update-Month.ps1

Example 2

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

Example 3

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
C:\Reports\2009\January.csv

# RELATED LINKS
```

### <a name="redirecting-to-an-xml-file"></a>重新導向至 XML 檔案

您可以撰寫函數和腳本的 XML 型說明主題。 雖然以批註為基礎的說明比較容易執行，但可更新的說明需要以 XML 為基礎的說明，並提供多種語言的說明主題。

下列範例顯示 Update-Month.ps1 腳本的前幾行。
腳本會使用 `.ExternalHelp` 關鍵字來指定腳本的 XML 型說明主題的路徑。

請注意，關鍵字的值 `.ExternalHelp` 會出現在與關鍵字相同的行上。 任何其他位置都是不正確。

```powershell
# .ExternalHelp C:\MyScripts\Update-Month-Help.xml

param ([string]$InputPath, [string]$OutPutPath)
function Get-Data { }
...
```

下列範例會顯示函式中關鍵字的三個有效 `.ExternalHelp` 位置。

```powershell
function Add-Extension
{
# .ExternalHelp C:\ps-test\Add-Extension.xml

param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

```powershell
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name

# .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

```powershell
# .ExternalHelp C:\ps-test\Add-Extension.xml
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

### <a name="redirecting-to-a-different-help-topic"></a>重新導向至不同的說明主題

下列程式碼是 PowerShell 中內建說明函式開頭的摘要，它會一次顯示一屏解說文字。
由於 Cmdlet 的說明主題會描述 help 函式，因此 help 函式會 `Get-Help` 使用 `.ForwardHelpTargetName` 和 `.ForwardHelpCategory` 關鍵字將使用者重新導向至 `Get-Help` Cmdlet 說明主題。

```powershell
function help
{

<#
.FORWARDHELPTARGETNAME Get-Help
.FORWARDHELPCATEGORY Cmdlet
#>
[CmdletBinding(DefaultParameterSetName='AllUsersView')]
param(
[Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
[System.String]
${Name},
...
```

下列命令會使用這項功能：

```powershell
Get-Help -Name help
```

```Output
NAME

Get-Help

SYNOPSIS

Displays information about PowerShell cmdlets and concepts.
...
```

## <a name="see-also"></a>另請參閱

[about_Functions](about_Functions.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Scripts](about_Scripts.md)

[如何撰寫 Cmdlet 說明](https://go.microsoft.com/fwlink/?LinkID=123415)
