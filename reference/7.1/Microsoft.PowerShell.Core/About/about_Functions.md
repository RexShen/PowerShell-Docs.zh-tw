---
description: 說明如何在 PowerShell 中建立和使用函式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: bef1f9f0b672f45c30626a1bbe4f2c6a7dfa540b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208331"
---
# <a name="about-functions"></a>關於函式

## <a name="short-description"></a>簡短描述

說明如何在 PowerShell 中建立和使用函式。

## <a name="long-description"></a>完整描述

函式是具有您指派之名稱的 PowerShell 語句清單。 當您執行函式時，您會輸入函數名稱。 清單中的語句會以您在命令提示字元中輸入的方式執行。

函數可以簡單如下：

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

函數也可以像 Cmdlet 或應用程式一樣複雜。

如同 Cmdlet，函數可以有參數。 這些參數可以是命名、位置、切換或動態參數。 您可以從命令列或從管線讀取函數參數。

函數可以傳回可顯示、指派給變數或傳遞給其他函式或 Cmdlet 的值。 您也可以使用關鍵字來指定傳回值 `return` 。 `return`關鍵字不會影響或隱藏從函數傳回的其他輸出。 不過， `return` 關鍵字會結束該行的函式。 如需詳細資訊，請參閱 [about_Return](about_Return.md)。

函數的語句清單可以包含不同類型的語句清單，以及關鍵字 `Begin` 、 `Process` 和 `End` 。 這些語句清單會以不同的方式處理來自管線的輸入。

篩選是一種特殊的函式，使用 `Filter` 關鍵字。

函數也可以像 Cmdlet 一樣運作。 您可以建立函式，其運作方式就像 Cmdlet，而不需要使用程式 `C#` 設計。 如需詳細資訊，請參閱 [about_Functions_Advanced](about_Functions_Advanced.md)。

## <a name="syntax"></a>Syntax

以下是函數的語法：

```
function [<scope:>]<name> [([type]$parameter1[,[type]$parameter2])]
{
  param([type]$parameter1 [,[type]$parameter2])
  dynamicparam {<statement list>}
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

函數包含下列專案：

- `Function`關鍵字
- 範圍 (選擇性) 
- 您選取的名稱
- 任何數目的具名引數 (選擇性) 
- 以大括弧括住的一或多個 PowerShell 命令 `{}`

如需 `Dynamicparam` 函數中關鍵字和動態參數的詳細資訊，請參閱 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。

## <a name="simple-functions"></a>簡單函數

函數不需要太複雜，就很有用。 最簡單的函式具有下列格式：

```
function <function-name> {statements}
```

例如，下列函式會使用 [以系統管理員身分執行] 選項啟動 PowerShell。

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

若要使用函數，請輸入： `Start-PSAdmin`

若要將語句加入至函數，請在個別的行上輸入每個語句，或使用分號 `;` 來分隔語句。

例如，下列函式 `.jpg` 會在目前使用者的目錄中尋找在開始日期之後變更的所有檔案。

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

您可以建立有用小型函式的工具箱。 將這些函式新增至您的 PowerShell 設定檔，如本主題的 [about_Profiles](about_Profiles.md) 和稍後所述。

## <a name="function-names"></a>函數名稱

您可以將任何名稱指派給函式，但您與其他人共用的函式應遵循針對所有 PowerShell 命令所建立的命名規則。

函式名稱應該包含動詞-名片語，其中動詞會識別函式所執行的動作，而名詞會識別 Cmdlet 執行其動作的專案。

函式應使用已核准給所有 PowerShell 命令的標準動詞。 這些動詞命令可協助我們讓命令名稱保持簡單、一致且方便使用者瞭解。

如需標準 PowerShell 動詞命令的詳細資訊，請參閱 Microsoft Docs 中的 [已核准動詞](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) 。

## <a name="functions-with-parameters"></a>具有參數的函式

您可以搭配使用參數與函數，包括具名引數、位置參數、切換參數和動態參數。 如需函數中動態參數的詳細資訊，請參閱 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。

### <a name="named-parameters"></a>具名參數

您可以定義任何數目的具名引數。 您可以包含具名引數的預設值，如本主題稍後所述。

您可以使用關鍵字來定義大括弧內的參數 `Param` ，如下列範例語法所示：

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

您也可以在沒有關鍵詞的大括弧之外定義參數 `Param` ，如下列範例語法所示：

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

以下是此替代語法的範例。

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

雖然第一個方法是慣用的，但這兩種方法並沒有任何差異。

當您執行函式時，您為參數提供的值會指派給包含參數名稱的變數。 可以在函數中使用該變數的值。

下列範例是名為的函式 `Get-SmallFiles` 。 此函數有 `$Size` 參數。 此函式會顯示小於參數值的所有檔案 `$Size` ，並排除目錄：

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

在函數中，您可以使用 `$Size` 變數，也就是為參數定義的名稱。

若要使用此函式，請輸入下列命令：

```powershell
Get-SmallFiles -Size 50
```

您也可以輸入沒有參數名稱之具名引數的值。
例如，下列命令提供的結果與為 **Size** 參數命名的命令相同：

```powershell
Get-SmallFiles 50
```

若要定義參數的預設值，請在參數名稱之後輸入等號和值，如下列範例變化所示 `Get-SmallFiles` ：

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

如果您 `Get-SmallFiles` 不輸入值，函數會將100指派給 `$size` 。 如果您提供值，此函數會使用該值。

（選擇性）您可以藉由將 **PSDefaultValue** 屬性新增至參數的描述，並指定 **PSDefaultValue** 的 **help** 屬性，提供描述參數預設值的簡短說明字串。 若要提供說明字串來描述函式中 **Size** 參數 (100) 的預設值 `Get-SmallFiles` ，請新增 **PSDefaultValue** 屬性，如下列範例所示。

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

如需 **PSDefaultValue** 屬性類別的詳細資訊，請參閱 [PSDefaultValue 屬性成員](/dotnet/api/system.management.automation.psdefaultvalueattribute)。

### <a name="positional-parameters"></a>位置參數

位置參數是沒有參數名稱的參數。 PowerShell 使用參數值順序，將每個參數值與函數中的參數產生關聯。

當您使用位置參數時，請在函式名稱之後輸入一或多個值。 位置參數值會指派給 `$args` 陣列變數。
函數名稱後面的值會指派給陣列中的第一個位置 `$args` `$args[0]` 。

下列 `Get-Extension` 函數會將副檔名新增 `.txt` 至您提供的檔案名：

```powershell
function Get-Extension {
  $name = $args[0] + ".txt"
  $name
}
```

```powershell
Get-Extension myTextFile
```

```Output
myTextFile.txt
```

### <a name="switch-parameters"></a>切換參數

切換參數是不需要值的參數。 相反地，您必須輸入函式名稱，後面接著 switch 參數的名稱。

若要定義切換參數，請在 `[switch]` 參數名稱前面指定類型，如下列範例所示：

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

當您在函式 `On` 名稱之後輸入 switch 參數時，函數會顯示 "switch on"。 如果沒有切換參數，則會顯示 "Switch off"。

```powershell
Switch-Item -on
```

```Output
Switch on
```

```powershell
Switch-Item
```

```Output
Switch off
```

您也可以在執行函式時，將 **布林** 值指派給參數，如下列範例所示：

```powershell
Switch-Item -on:$true
```

```Output
Switch on
```

```powershell
Switch-Item -on:$false
```

```Output
Switch off
```

## <a name="using-splatting-to-represent-command-parameters"></a>使用展開來代表命令參數

您可以使用展開來代表命令的參數。 這項功能是在 Windows PowerShell 3.0 中引進。

在呼叫會話命令的函式中使用此技巧。 您不需要宣告或列舉命令參數，或在命令參數變更時變更函數。

下列範例函式會呼叫 `Get-Command` Cmdlet。 命令用 `@Args` 來表示的參數 `Get-Command` 。

```powershell
function Get-MyCommand { Get-Command @Args }
```

`Get-Command`當您呼叫函數時，可以使用的所有參數 `Get-MyCommand` 。 參數和參數值會使用傳遞至命令 `@Args` 。

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

此 `@Args` 功能使用 `$Args` 自動參數，這代表未宣告的 Cmdlet 參數和其餘引數的值。

如需展開的詳細資訊，請參閱 [about_Splatting](about_Splatting.md)。

## <a name="piping-objects-to-functions"></a>將物件輸送至函式

任何函數都可以從管線取得輸入。 您可以使用 `Begin` 、和關鍵字，控制函式處理管線輸入的方式 `Process` `End` 。 下列範例語法會顯示三個關鍵字：

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

`Begin`語句清單只會在函數的開頭執行一次。

> [!IMPORTANT]
> 如果您的函式 `Begin` 定義 `Process` 或 `End` 區塊，則您的所有程式碼都必須位於這些區塊內。 如果 *有定義任何* 區塊，則不會在區塊外辨識任何程式碼。

`Process`語句清單會針對管線中的每個物件執行一次。
當 `Process` 區塊正在執行時，每個管線物件一次都會指派給 `$_` 自動變數（一個管線物件）。

在函數接收管線中的所有物件之後， `End` 語句清單會執行一次。 如果未 `Begin` `Process` 使用、或 `End` 關鍵字，則會將所有語句視為 `End` 語句清單。

下列函數會使用 `Process` 關鍵字。 此函數會顯示管線的範例：

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

若要示範此函數，請輸入以逗號分隔的數位清單，如下列範例所示：

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

當您在管線中使用函式時，輸送至函式的物件會指派給 `$input` 自動變數。 函式會在 `Begin` 任何物件來自管線之前，以關鍵字執行語句。 `End`從管線接收所有物件之後，函數會使用關鍵字執行語句。

下列範例會顯示 `$input` 具有和關鍵字的自動變數 `Begin` `End` 。

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

如果此函式是使用管線執行，則會顯示下列結果：

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

當 `Begin` 語句執行時，該函式不會有來自管線的輸入。 當函式 `End` 具有值之後，就會執行此語句。

如果函式有 `Process` 關鍵字，則中的每個物件 `$input` 都會從移除 `$input` 並指派給 `$_` 。 下列範例有 `Process` 語句清單：

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

在此範例中，輸送至函式的每個物件都會傳送至 `Process` 語句清單。 `Process`語句會在每個物件上執行，一次一個物件。 `$input`當函數到達關鍵字時，自動變數是空的 `End` 。

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

如需詳細資訊，請參閱[使用枚舉](about_Automatic_Variables.md#using-enumerators)器

## <a name="filters"></a>篩選條件

篩選是在管線中的每個物件上執行的函式類型。 篩選準則類似于函式及其在區塊中的所有語句 `Process` 。

篩選準則的語法如下所示：

```
filter [<scope:>]<name> {<statement list>}
```

下列篩選器會從管線中取得記錄專案，然後顯示整個專案或僅顯示專案的訊息部分：

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a>函數範圍

函數存在於建立它的範圍中。

如果函式是腳本的一部分，則函式可用於該腳本內的語句。 根據預設，腳本中的函式無法在命令提示字元中使用。

您可以指定函數的範圍。 例如，在下列範例中，函式會新增至全域範圍：

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

當函式在全域範圍內時，您可以在腳本、函數和命令列中使用函數。

函數通常會建立範圍。 在函數中建立的專案（例如變數）只存在於函式範圍中。

如需 PowerShell 中之範圍的詳細資訊，請參閱 [about_Scopes](about_Scopes.md)。

## <a name="finding-and-managing-functions-using-the-function-drive"></a>使用 Function：磁片磁碟機尋找和管理函數

PowerShell 中的所有函式和篩選都會自動儲存在 `Function:` 磁片磁碟機中。 此磁片磁碟機是 **由 PowerShell 函** 式提供者所公開。

參考磁片磁碟機時，請在函式 `Function:` 後面 **Function** 輸入冒號，就像參考 `C` 電腦的或 `D` 磁片磁碟機一樣。

下列命令會顯示目前 PowerShell 會話中的所有函式：

```powershell
Get-ChildItem function:
```

函數中的命令會以腳本區塊的形式儲存在函式的 definition 屬性中。 例如，若要在 PowerShell 隨附的 Help 函式中顯示命令，請輸入：

```powershell
(Get-ChildItem function:help).Definition
```

您也可以使用下列語法。

```powershell
$function:help
```

如需有關磁片磁碟機的詳細資訊 `Function:` ，請參閱 **函數** 提供者的說明主題。 輸入 `Get-Help Function`。

## <a name="reusing-functions-in-new-sessions"></a>在新的會話中重複使用函數

當您在 PowerShell 命令提示字元中輸入函式時，該函式會成為目前會話的一部分。 它可供使用，直到會話結束為止。

若要在所有 PowerShell 會話中使用您的函式，請將函式新增至您的 PowerShell 設定檔。 如需設定檔的詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。

您也可以將函數儲存在 PowerShell 腳本檔案中。 在文字檔中輸入您的函式，然後使用副檔名儲存檔案 `.ps1` 。

## <a name="writing-help-for-functions"></a>撰寫函數的說明

此 Cmdlet 會取得函式的說明 `Get-Help` ，以及 Cmdlet、提供者和腳本的說明。 若要取得函式的說明，請輸入， `Get-Help` 後面接著函式名稱。

例如，若要取得函數的說明 `Get-MyDisks` ，請輸入：

```powershell
Get-Help Get-MyDisks
```

您可以使用下列兩種方法的其中一個來撰寫函數的說明：

- 函數的 Comment-Based 說明

  使用批註中的特殊關鍵字來建立說明主題。 若要為函式建立以批註為基礎的說明，必須將批註放在函式主體的開頭或結尾，或在 function 關鍵字前面的行上。 如需以批註為基礎的說明的詳細資訊，請參閱 [about_Comment_Based_Help](about_Comment_Based_Help.md)。

- 函數的 XML-Based 說明

  建立以 XML 為基礎的說明主題，例如通常為 Cmdlet 建立的類型。 如果您要將說明主題當地語系化為多種語言，則需要以 XML 為基礎的說明。

  若要將函式與以 XML 為基礎的說明主題產生關聯，請使用以 `.ExternalHelp` 批註為基礎的說明關鍵字。 如果沒有這個關鍵字，則找不到函式 `Get-Help` 說明主題，而且對 `Get-Help` 函數的呼叫只會傳回自動產生的說明。

  如需關鍵字的詳細資訊 `ExternalHelp` ，請參閱 [about_Comment_Based_Help](about_Comment_Based_Help.md)。 如需以 XML 為基礎之說明的詳細資訊，請參閱 MSDN library 中的 [如何撰寫 Cmdlet 說明](https://go.microsoft.com/fwlink/?LinkID=123415) 。

## <a name="see-also"></a>另請參閱

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Parameters](about_Parameters.md)

[about_Profiles](about_Profiles.md)

[about_Scopes](about_Scopes.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Function_provider](about_Function_provider.md)

