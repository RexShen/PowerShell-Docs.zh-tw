---
description: 說明 PowerShell 中的範圍概念，並示範如何設定和變更元素的範圍。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: 8517a5c077aa8c5b769bc74e13bc56ef6a6bb355
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207560"
---
# <a name="about-scopes"></a>關於範圍

## <a name="short-description"></a>簡短描述
說明 PowerShell 中的範圍概念，並示範如何設定和變更元素的範圍。

## <a name="long-description"></a>完整描述

PowerShell 會限制對變數、別名、函式和 PowerShell 磁片磁碟機的存取， (Psdrive) ，方法是限制可讀取和變更的位置。 PowerShell 會使用範圍規則，以確保您不會不慎變更不應該變更的專案。

以下是範圍的基本規則：

- 範圍可能會被嵌套。 外部範圍稱為父範圍。 任何嵌套的範圍都是該父系的子範圍。

- 除非您明確地將專案設為私用，否則專案會在其建立所在的範圍和任何子範圍中顯示。 您可以在一或多個範圍中放置變數、別名、函式或 PowerShell 磁片磁碟機。

- 除非您明確指定不同的範圍，否則您在範圍內建立的專案只能在建立它的範圍內變更。

如果您在範圍中建立專案，且該專案與不同範圍中的專案共用其名稱，則原始專案可能會隱藏在新的專案下，但不會覆寫或變更。

## <a name="powershell-scopes"></a>PowerShell 範圍

PowerShell 支援下列範圍：

- Global： PowerShell 啟動時作用中的範圍。 在全域範圍中建立 PowerShell 啟動時所出現的變數和函式，例如自動變數和喜好設定變數。 您 PowerShell 設定檔中的變數、別名和函式也會在全域範圍中建立。

- Local：目前的範圍。 區域範圍可以是全域範圍或任何其他範圍。

- 腳本：指令檔執行時所建立的範圍。 只有腳本中的命令會在腳本範圍中執行。 針對腳本中的命令，腳本範圍是區域範圍。

> [!NOTE]
> **私** 用不是範圍。 它是一種 [選項](#private-option) ，可變更專案定義範圍之外的專案可見度。

## <a name="parent-and-child-scopes"></a>父系和子範圍

您可以藉由執行腳本或函式、建立會話，或啟動新的 PowerShell 實例來建立新的範圍。 當您建立新的範圍時，結果會是 (原始範圍) 的父範圍，以及 () 建立之範圍的子範圍。

在 PowerShell 中，所有範圍都是全域範圍的子範圍，但您可以建立許多範圍和許多遞迴範圍。

除非您明確地將專案設為私用，否則父範圍中的專案可供子範圍使用。 不過，除非您在建立專案時明確指定範圍，否則您在子範圍中建立和變更的專案不會影響父範圍。

## <a name="inheritance"></a>繼承

子範圍不會繼承父範圍中的變數、別名和函式。 除非專案是私用的，否則子範圍可以查看父範圍中的專案。 而且，它可以藉由明確指定父範圍來變更專案，但是這些專案不是子範圍的一部分。

不過，會使用一組專案來建立子範圍。 通常，它會包含具有 **AllScope** 選項的所有別名。 本文稍後會討論這個選項。 它包含具有 **AllScope** 選項的所有變數，加上一些自動變數。

若要尋找特定範圍中的專案，請使用或的範圍 `Get-Variable` 參數 `Get-Alias` 。

例如，若要取得區域範圍中的所有變數，請輸入：

```powershell
Get-Variable -Scope local
```

若要取得全域範圍中的所有變數，請輸入：

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a>範圍修飾符

變數、別名或函式名稱可以包含下列任何一個選擇性範圍修飾詞：

- `global:` -指定名稱存在於 **全域** 範圍中。
- `local:` -指定名稱存在於 **區域** 範圍中。 目前的範圍一律是 **區域** 範圍。
- `private:` -指定名稱是 **私** 用的，而且只有目前的範圍可見。
- `script:` -指定名稱存在於 **腳本** 範圍中。
  如果沒有最接近的上階腳本檔案， **腳本** 範圍就是最接近的上階腳本檔案範圍或 **全域** 。
- `using:` -用來存取在另一個範圍中定義的變數，並透過如和的 Cmdlet 執行腳本 `Start-Job` `Invoke-Command` 。
- `workflow:` -指定名稱存在於工作流程中。 注意： PowerShell Core 中不支援工作流程。
- `<variable-namespace>` -PowerShell New-psdrive 提供者所建立的修飾詞。
  例如：

  |  命名空間  |                    描述                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | 目前範圍中定義的別名               |
  | `Env:`      | 目前範圍中定義的環境變數 |
  | `Function:` | 目前範圍中定義的函數             |
  | `Variable:` | 目前範圍中定義的變數             |

腳本的預設範圍是腳本範圍。 函數和別名的預設範圍是區域範圍，即使它們是在腳本中定義也一樣。

### <a name="using-scope-modifiers"></a>使用範圍修飾符

若要指定新變數、別名或函數的範圍，請使用範圍修飾符。

變數中範圍修飾詞的語法為：

```
$[<scope-modifier>:]<name> = <value>
```

函數中的範圍修飾詞語法為：

```
function [<scope-modifier>:]<name> {<function-body>}
```

下列不使用範圍修飾符的命令會在目前或 **區域** 範圍中建立變數：

```powershell
$a = "one"
```

若要在 **全域** 範圍中建立相同的變數，請使用範圍 `global:` 修飾符：

```powershell
$global:a = "one"
```

若要在 **腳本** 範圍中建立相同的變數，請使用 `script:` 範圍修飾符：

```powershell
$script:a = "one"
```

您也可以搭配函數使用範圍修飾符。 下列函式定義會在 **全域** 範圍中建立函數：

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

您也可以使用範圍修飾符來參考不同範圍中的變數。
下列命令會參考 `$test` 變數，先在本機範圍，然後在全域範圍內：

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a>`Using:`範圍修飾詞

使用是一種特殊的範圍修飾詞，用來識別遠端命令中的本機變數。 如果沒有修飾詞，PowerShell 就會在遠端會話中定義遠端命令中的變數。

`Using`範圍修飾詞是在 PowerShell 3.0 中引進。

針對任何執行的腳本或命令，您必須 `Using` 要有範圍修飾詞，才能從呼叫會話範圍內嵌變數值，讓會話外的程式碼可以存取它們。 `Using`下列內容支援範圍修飾符：

- 從遠端執行的命令，從 `Invoke-Command` 使用 **ComputerName** 或 **Session** 參數開始 (遠端會話) 
- 背景工作，以 `Start-Job` (跨進程會話開始) 
- 執行緒作業，透過 `Start-ThreadJob` 或 `ForEach-Object -Parallel` (個別的執行緒會話啟動) 

視內容而定，內嵌變數值是呼叫端範圍中資料的獨立複本，或是對它的參考。 在遠端和跨進程的會話中，它們一律是獨立的複本。

如需詳細資訊，請參閱 [about_Remote_Variables](about_Remote_Variables.md)。

線上程會話中，它們是以傳址方式傳遞。 這表示可以修改不同執行緒中的呼叫範圍變數。 若要安全地修改變數，需要執行緒同步處理。

如需詳細資訊，請參閱：

- [Start-ThreadJob](/powershell/module/ThreadJob/Start-ThreadJob)

#### <a name="serialization-of-variable-values"></a>變數值的序列化

遠端執行的命令和背景工作會跨進程執行。
跨進程會話使用以 XML 為基礎的序列化和還原序列化，讓變數的值可以跨進程界限使用。 序列化程式會將物件轉換為包含原始物件屬性但不包含其方法的 **PSObject** 。

針對一組有限的類型，還原序列化會將解除凍結物件回原始型別。 解除凍結物件是原始物件實例的複本。
它具有類型屬性和方法。 針對簡單類型（例如 **system.object** ），複本是精確的。 如果是複雜類型，則會完美複製。 例如，解除凍結憑證物件不包含私密金鑰。

所有其他類型的實例都是 **PSObject** 實例。 **PSTypeNames** 屬性包含 **前面加上** 還原序列化的原始型別名稱，例如 **Deserialized.System。Data DataTable**

### <a name="the-allscope-option"></a>AllScope 選項

變數和別名具有可採用 **AllScope** 值的 **選項** 屬性。 具有 **AllScope** 屬性的專案會成為您所建立之任何子範圍的一部分，不過父範圍不會追溯這些專案。

具有 **AllScope** 屬性的專案會顯示在子範圍中，而且屬於該範圍。 對任何範圍中的專案所做的變更，都會影響定義變數的所有範圍。

### <a name="managing-scope"></a>管理領域

有數個 Cmdlet 具有 **範圍** 參數，可讓您取得或設定 (建立和變更特定範圍中) 專案。 使用下列命令，在您的會話中尋找具有 **範圍** 參數的所有 Cmdlet：

```powershell
Get-Help * -Parameter scope
```

若要尋找在特定範圍中可見的變數，請使用的 `Scope` 參數 `Get-Variable` 。 可見的變數包括全域變數、父範圍中的變數，以及目前範圍中的變數。

例如，下列命令會取得在區域範圍中可見的變數：

```powershell
Get-Variable -Scope local
```

若要在特定範圍內建立變數，請使用範圍修飾符或的 **範圍** 參數 `Set-Variable` 。 下列命令會在全域範圍中建立變數：

```powershell
New-Variable -Scope global -Name a -Value "One"
```

您也可以使用 `New-Alias` 、或 Cmdlet 的 scope 參數 `Set-Alias` `Get-Alias` 來指定範圍。 下列命令會在全域範圍中建立別名：

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

若要取得特定範圍中的函式，請在範圍內使用 `Get-Item` Cmdlet。 `Get-Item`Cmdlet 沒有 **範圍** 參數。

> [!NOTE]
> 針對使用 **範圍** 參數的 Cmdlet，您也可以依編號參考範圍。 此數位會描述某範圍與另一個範圍之間的相對位置。 範圍0代表目前或區域範圍。 範圍1表示直屬父範圍。 範圍2表示父範圍的父系，依此類推。 如果您已建立許多遞迴範圍，則編號的範圍會很有用。

### <a name="using-dot-source-notation-with-scope"></a>使用點來源標記法搭配範圍

腳本和函式會遵循範圍的所有規則。 您可以在特定範圍中建立它們，除非您使用 Cmdlet 參數或範圍修飾符來變更該範圍，否則它們只會影響該範圍。

但是，您可以使用點來源標記法，將腳本或函式新增至目前的範圍。 然後，當腳本在目前的範圍中執行時，腳本所建立的任何函式、別名和變數都會出現在目前的範圍中。

若要將函式新增至目前的範圍，請在函式呼叫中輸入點 (. ) 和函式名稱之前的空格。

例如，若要從腳本範圍中的 C：\Scripts 目錄執行 Sample.ps1 腳本 (腳本) 的預設值，請使用下列命令：

```powershell
c:\scripts\sample.ps1
```

若要在本機範圍中執行 Sample.ps1 腳本，請使用下列命令：

```powershell
. c:\scripts.sample.ps1
```

當您使用呼叫運算子 ( # A0) 來執行函式或腳本時，不會將它新增至目前的範圍。 下列範例會使用呼叫運算子：

```powershell
& c:\scripts.sample.ps1
```

您可以在 [about_operators](about_operators.md)中閱讀呼叫運算子的詳細資訊。

在目前的範圍中，無法使用 Sample.ps1 腳本所建立的任何別名、函數或變數。

## <a name="restricting-without-scope"></a>不含範圍的限制

有些 PowerShell 概念類似于範圍或與範圍互動。 這些概念可能會與範圍或範圍行為混淆。

會話、模組和嵌套提示是獨立的環境，但它們不是會話中全域範圍的子範圍。

### <a name="sessions"></a>工作階段

會話是 PowerShell 執行所在的環境。 當您在遠端電腦上建立會話時，PowerShell 會建立與遠端電腦的持續連線。 持續性連接可讓您將會話用於多個相關的命令。

由於會話是內含的環境，它有自己的範圍，但會話不是建立它的會話的子範圍。 會話會以自己的全域範圍開始。 此範圍與會話的全域範圍無關。 您可以在會話中建立子範圍。 例如，您可以執行腳本，在會話中建立子範圍。

### <a name="modules"></a>單元

您可以使用 PowerShell 模組來共用和提供 PowerShell 工具。 模組是一個單位，可以包含 Cmdlet、腳本、函式、變數、別名和其他實用的專案。 除非明確定義，否則模組中的專案無法在模組之外存取。 因此，您可以將模組新增至您的會話，並使用公用專案，而不必擔心其他專案可能會覆寫會話中的 Cmdlet、腳本、函式和其他專案。

依預設，模組會載入目前 _會話狀態_ 的最上層，而不是目前的 _範圍_ 。 目前的會話狀態可能是模組會話狀態或全域會話狀態。 將模組新增至會話並不會變更範圍。 如果您在全域範圍內，則會將模組載入到全域會話狀態。 任何匯出都會放到全域資料表中。
如果您從 module1 _內_ 載入 module2，module2 就會載入至 [module1] 的會話狀態，而不是全域會話狀態。 任何來自 module2 的匯出都會放置在 [module1] 會話狀態的上方。 如果您使用 `Import-Module -Scope local` ，則匯出會放入目前的範圍物件中，而不是放在最上層。 如果您是 _在模組中_ ，並使用 `Import-Module -Scope global` (或 `Import-Module -Global`) 載入另一個模組，該模組和其匯出會載入到全域會話狀態，而不是模組的本機會話狀態。 這項功能是專為撰寫操作模組的模組所設計。 **WindowsCompatibility** 模組會執行此工作，以將 proxy 模組匯入到全域會話狀態。

在會話狀態中，模組會有自己的範圍。 請考慮下列模組 `C:\temp\mod1.psm1` ：

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

現在，我們要建立一個全域變數 `$a` ，為它指定值，然後呼叫函數 **foo** 。

```powershell
$a = "Goodbye"
foo
```

模組會宣告 `$a` 模組範圍中的變數，然後函式 **foo** 會輸出這兩個範圍中的變數值。

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a>嵌套提示

嵌套提示沒有自己的範圍。 當您輸入嵌套提示字元時，嵌套提示字元是環境的子集。 但是，您仍然在本機範圍內。

腳本有自己的範圍。 如果您要對腳本進行調試，而您到達腳本中的中斷點，請輸入腳本範圍。

### <a name="private-option"></a>私用選項

別名和變數具有可採用 **私** 用值的 **選項** 屬性。 具有 **私** 用選項的專案可以在建立這些專案的範圍內加以查看和變更，但無法在該範圍之外查看或變更。

例如，如果您在全域範圍中建立具有私用選項的變數，然後執行腳本， `Get-Variable` 則腳本中的命令不會顯示私用變數。 在這個實例中使用全域範圍修飾詞，並不會顯示私用變數。

您可以使用 `New-Variable` 、、和 Cmdlet 的 option 參數， `Set-Variable` `New-Alias` `Set-Alias` 將 option 屬性的值設定為 Private。

### <a name="visibility"></a>可見度

變數或別名的 **可見度** 屬性會決定您是否可以在建立容器的容器之外查看該專案。 容器可以是模組、腳本或嵌入式管理單元。 可見度是針對容器所設計，其方式與 **選項** 屬性的 **私** 用值是針對範圍所設計。

**可見度** 屬性會採用 **公用** 和 **私** 用值。 只有在建立私人可見度的容器中，才能查看並變更這些專案。 如果新增或匯入容器，則無法查看或變更具有私人可見度的專案。

由於可見度是針對容器而設計，因此在範圍內的運作方式不同。

- 如果您在全域範圍中建立具有私用可見度的專案，就無法在任何範圍中查看或變更專案。
- 如果您嘗試查看或變更具有私用可見度之變數的值，則 PowerShell 會傳回錯誤訊息。

您可以使用 `New-Variable` 和 `Set-Variable` Cmdlet 來建立具有私用可見度的變數。

## <a name="examples"></a>範例

### <a name="example-1-change-a-variable-value-only-in-a-script"></a>範例1：只變更腳本中的變數值

下列命令會變更 `$ConfirmPreference` 腳本中的變數值。 此變更不會影響全域領域。

首先，若要顯示 `$ConfirmPreference` 區域範圍中的變數值，請使用下列命令：

```
PS>  $ConfirmPreference
High
```

建立包含下列命令的 Scope.ps1 腳本：

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

執行指令碼。 腳本會變更變數的值 `$ConfirmPreference` ，然後報告其在腳本範圍中的值。 輸出應類似下列輸出：

```output
The value of $ConfirmPreference is Low.
```

接下來，測試 `$ConfirmPreference` 目前範圍中變數的目前值。

```
PS>  $ConfirmPreference
High
```

此範例顯示腳本範圍中變數值的變更，不會影響父範圍中的變數值。

### <a name="example-2-view-a-variable-value-in-different-scopes"></a>範例2：在不同範圍中查看變數值

您可以使用範圍修飾符來查看區域範圍和父範圍中的變數值。

首先， `$test` 在全域範圍中定義變數。

```powershell
$test = "Global"
```

接著，建立定義變數的 Sample.ps1 腳本 `$test` 。 在腳本中，使用範圍修飾符來參考變數的全域或本機版本 `$test` 。

在 Sample.ps1：

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

當您執行 Sample.ps1 時，輸出應該會與下列輸出類似：

```output
The local value of $test is Local.
The global value of $test is Global.
```

當腳本完成時，只 `$test` 會在會話中定義的全域值。

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a>範例3：變更父範圍中的變數值

除非您使用私用選項或另一個方法來保護專案，否則您可以在父範圍中查看和變更變數的值。

首先， `$test` 在全域範圍中定義變數。

```powershell
$test = "Global"
```

接著，建立定義變數的 Sample.ps1 腳本 `$test` 。 在腳本中，使用範圍修飾符來參考變數的全域或本機版本 `$test` 。

在 Sample.ps1：

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

當腳本完成時，的全域值 `$test` 會變更。

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a>範例4：建立私用變數

私用變數是具有 **Option** 屬性的變數，其值為 *private* 。 *私* 用變數會由子範圍繼承，但是只能在建立這些變數的範圍內加以查看或變更。

下列命令會建立 `$ptest` 在區域範圍中呼叫的私用變數。

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

您可以 `$ptest` 在區域範圍中顯示和變更的值。

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

接著，建立包含下列命令的 Sample.ps1 腳本。 此命令會嘗試顯示和變更的值 `$ptest` 。

在 Sample.ps1：

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

`$ptest`變數在腳本範圍中看不到，輸出是空的。

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a>範例5：在遠端命令中使用本機變數

針對在本機會話中建立之遠端命令中的變數，請使用 `Using` 範圍修飾符。 PowerShell 假設遠端命令中的變數是在遠端會話中建立的。

語法為：

```
$Using:<VariableName>
```

例如，下列命令會 `$Cred` 在本機會話中建立變數，然後 `$Cred` 在遠端命令中使用該變數：

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

使用範圍是在 PowerShell 3.0 中引進。 在 PowerShell 2.0 中，若要指示在本機會話中建立的變數，請使用下列命令格式。

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a>另請參閱

[about_Variables](about_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Functions](about_Functions.md)

[about_Script_Blocks](about_Script_Blocks.md)

[Start-ThreadJob](/powershell/module/ThreadJob/Start-ThreadJob)
