---
description: 描述您可以用來跨越專案集合中所有專案的語言命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach
ms.openlocfilehash: b5f09785fbf1fa8c3c14d287efc7cf5fed2d18eb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207100"
---
# <a name="about-foreach"></a>關於 ForEach

## <a name="short-description"></a>簡短描述
描述您可以用來跨越專案集合中所有專案的語言命令。

## <a name="long-description"></a>完整描述

`Foreach`語句 (也稱為 `Foreach` 迴圈) 是一種語言結構，可逐步執行)  (逐一查看專案集合中的一連串值。

要進行往返的最簡單且最典型的集合類型是陣列。
在 `Foreach` 迴圈中，通常會針對陣列中的每個專案執行一或多個命令。

## <a name="syntax"></a>Syntax

以下顯示 `ForEach` 語法：

```
foreach ($<item> in $<collection>){<statement list>}
```

以 `ForEach` 括弧括住的語句部分代表變數和要逐一查看的集合。 `$<item>`當迴圈執行時，PowerShell 會自動建立變數 `Foreach` 。 在迴圈之前的每個反復專案之前，變數會設定為集合中的值。
語句後面的區塊 `Foreach` `{<statement list>}` 包含一組命令，可針對集合中的每個專案執行。

### <a name="examples"></a>範例

例如， `Foreach` 下列範例中的迴圈會顯示陣列中的值 `$letterArray` 。

```powershell
$letterArray = "a","b","c","d"
foreach ($letter in $letterArray)
{
  Write-Host $letter
}
```

在此範例中， `$letterArray` 會使用字串值、、和來建立並初始化陣列 `"a"` `"b"` `"c"` `"d"` 。 第一次 `Foreach` 執行語句時，它會將 `$letter` 變數設定為等於 () 中的第一個專案 `$letterArray` `"a"` 。 然後，它會使用 `Write-Host` Cmdlet 來顯示字母 a。 下一次執行迴圈時， `$letter` 會設定為 `"b"` ，依此類推。 在 `Foreach` 迴圈顯示字母 d 之後，PowerShell 就會結束迴圈。

整個 `Foreach` 語句必須出現在同一行上，才能在 PowerShell 命令提示字元中以命令的形式執行。 `Foreach`如果您將命令放在 ps1 腳本檔案中，則整個語句不需要出現在同一行。

`Foreach` 語句也可以與傳回專案集合的 Cmdlet 一起使用。 在下列範例中，Foreach 語句會逐步執行 Cmdlet 所傳回的專案清單 `Get-ChildItem` 。

```powershell
foreach ($file in Get-ChildItem)
{
  Write-Host $file
}
```

您可以使用 `If` 語句來限制傳回的結果，以精簡範例。 在下列範例中， `Foreach` 語句會執行與上一個範例相同的迴圈作業，但它會新增 `If` 語句，以將結果限制為大於 100 kb 的檔案 (KB) ：

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
  }
}
```

在此範例中， `Foreach` 迴圈會使用變數的屬性 `$file` 來執行比較作業 (`$file.length -gt 100KB`) 。 `$file`變數包含 Cmdlet 所傳回之物件中的所有屬性 `Get-ChildItem` 。 因此，您不只可以傳回檔案名。
在下一個範例中，PowerShell 會傳回語句清單內的長度和最後一個存取時間：

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
    Write-Host $file.length
    Write-Host $file.lastaccesstime
  }
}
```

在此範例中，您不限於在語句清單中執行單一命令。

您也可以在迴圈外使用變數 `Foreach` ，並在迴圈內遞增變數。 下列範例會計算大小超過 100 KB 的檔案：

```powershell
$i = 0
foreach ($file in Get-ChildItem) {
  if ($file.length -gt 100KB) {
    Write-Host $file "file size:" ($file.length / 1024).ToString("F0") KB
    $i = $i + 1
  }
}

if ($i -ne 0) {
  Write-Host
  Write-Host $i " file(s) over 100 KB in the current directory."
}
else {
  Write-Host "No files greater than 100 KB in the current directory."
}
```

在上述範例中， `$i` 變數會設定為 `0` 迴圈外部，而變數會在每個找到大於 100 KB 之檔案的迴圈內遞增。 當迴圈結束時， `If` 語句會評估的值， `$i` 以顯示超過 100 KB 的所有檔案計數。 或者，它會顯示一則訊息，指出找不到超過 100 KB 的檔案。

上述範例也會示範如何格式化檔案長度結果：

```powershell
($file.length / 1024).ToString("F0")
```

值除以1024可顯示以 kb 為單位的結果，而不是以位元組為單位，而產生的值則會使用固定點格式規範來格式化，以移除結果中的任何十進位值。 0會使格式規範顯示沒有小數位數。

在下列範例中，函式定義了剖析 PowerShell 腳本和腳本模組，並傳回包含在內之函式的位置。 此範例示範如何使用 `MoveNext` 方法 (它的運作方式類似于 `skip X` `For` 迴圈) ，以及 `Current` `$foreach` foreach 腳本區塊內變數的屬性。 即使跨多行的函式定義有異常或不一致，範例函式仍可以在腳本中找到函式。

如需詳細資訊，請參閱 [使用枚舉](about_Automatic_Variables.md#using-enumerators)器。

```powershell
function Get-FunctionPosition {
  [CmdletBinding()]
  [OutputType('FunctionPosition')]
  param(
    [Parameter(Position = 0, Mandatory,
      ValueFromPipeline, ValueFromPipelineByPropertyName)]
    [ValidateNotNullOrEmpty()]
    [Alias('PSPath')]
    [System.String[]]
    $Path
  )

  process {
    try {
      $filesToProcess = if ($_ -is [System.IO.FileSystemInfo]) {
        $_
      } else {
        $filesToProcess = Get-Item -Path $Path
      }
      $parser = [System.Management.Automation.Language.Parser]
      foreach ($item in $filesToProcess) {
        if ($item.PSIsContainer -or
            $item.Extension -notin @('.ps1', '.psm1')) {
          continue
        }
        $tokens = $errors = $null
        $ast = $parser::ParseFile($item.FullName, ([REF]$tokens),
          ([REF]$errors))
        if ($errors) {
          $msg = "File '{0}' has {1} parser errors." -f $item.FullName,
            $errors.Count
          Write-Warning $msg
        }
        :tokenLoop foreach ($token in $tokens) {
          if ($token.Kind -ne 'Function') {
            continue
          }
          $position = $token.Extent.StartLineNumber
          do {
            if (-not $foreach.MoveNext()) {
              break tokenLoop
            }
            $token = $foreach.Current
          } until ($token.Kind -in @('Generic', 'Identifier'))
          $functionPosition = [pscustomobject]@{
            Name       = $token.Text
            LineNumber = $position
            Path       = $item.FullName
          }
          Add-Member -InputObject $functionPosition `
            -TypeName FunctionPosition -PassThru
        }
      }
    }
    catch {
      throw
    }
  }
}
```

## <a name="see-also"></a>另請參閱

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_If](about_If.md)

[ForEach-Object](xref:Microsoft.PowerShell.Core.ForEach-Object)
