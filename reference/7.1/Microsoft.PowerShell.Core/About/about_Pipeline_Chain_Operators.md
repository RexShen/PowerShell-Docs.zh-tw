---
description: 描述 `&&` PowerShell 中使用和運算子的連結管線 `||` 。
ms.date: 09/30/2019
schema: 2.0.0
Locale: en-US
keywords: powershell,cmdlet
title: about_Pipeline_Chain_Operators
ms.openlocfilehash: 38895ff9acda9ead031c9be58904ac132364a584
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207300"
---
# <a name="about-pipeline-chain-operators"></a>關於管線鏈運算子

## <a name="short-description"></a>簡短描述

描述 `&&` PowerShell 中使用和運算子的連結管線 `||` 。

## <a name="long-description"></a>完整描述

從 PowerShell 7 開始，PowerShell 會執行 `&&` 和 `||` 運算子，以有條件地鏈出管線。 這些運算子在 PowerShell 中已知為 *管線鏈運算子* ，類似于 POSIX shell （例如 bash、zsh 和 sh）中的 [和或清單](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) ，以及 Windows 命令介面中的 [條件式處理符號](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) ( # A0) 。

如果左側管線成功，`&&` 運算子就會執行右側管線。 反過來說，如果左側管線失敗，`||` 運算子就會執行右側管線。

這些運算子會使用 `$?` 和 `$LASTEXITCODE` 變數來判斷管線是否失敗。 這可讓您將其與原生命令搭配使用，而不只是與 Cmdlet 或函式搭配使用。 例如：

```powershell
# Create an SSH key pair - if successful copy the public key to clipboard
ssh-keygen -t rsa -b 2048 && Get-Content -Raw ~\.ssh\id_rsa.pub | clip
```

### <a name="examples"></a>範例

#### <a name="two-successful-commands"></a>兩個成功的命令

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

#### <a name="first-command-fails-causing-second-not-to-be-executed"></a>第一個命令失敗，導致第二個未執行

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

#### <a name="first-command-succeeds-so-the-second-command-is-not-executed"></a>第一個命令成功，因此不會執行第二個命令

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

#### <a name="first-command-fails-so-the-second-command-is-executed"></a>第一個命令失敗，所以會執行第二個命令

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error: Bad
Second
```

管線成功是由變數的值所定義 `$?` ，而 PowerShell 會根據其執行狀態，在執行管線之後自動設定。
這表示管線鏈運算子具有下列等價：

```powershell
Test-Command '1' && Test-Command '2'
```

的運作方式與

```powershell
Test-Command '1'; if ($?) { Test-Command '2' }
```

及

```powershell
Test-Command '1' || Test-Command '2'
```

的運作方式與

```powershell
Test-Command '1'; if (-not $?) { Test-Command '2' }
```

### <a name="assignment-from-pipeline-chains"></a>從管線鏈指派

從管線鏈指派變數，會將鏈中的所有管線串連：

```powershell
$result = Write-Output '1' && Write-Output '2'
$result
```

```Output
1
2
```

如果從管線鏈指派期間發生腳本終止錯誤，指派不會成功：

```powershell
try
{
    $result = Write-Output 'Value' && $(throw 'Bad')
}
catch
{
    # Do nothing, just squash the error
}

"Result: $result"
```

```Output
Result:
```

### <a name="operator-syntax-and-precedence"></a>運算子語法和優先順序

不同于其他運算子， `&&` 並 `||` 操作管線，例如或之類的運算式 `+` `-and` 。

`&&` 與 `||` 管線 () 或重新導向 () 具有較低的優先順序 `|` `>` ，但優先順序高於作業運算子 (`&`) 、指派 (`=`) 或分號 (`;`) 。 這表示管線鏈內的管線可以個別重新導向，而且整個管線鏈可以背景執行、指派給變數或分隔為語句。

若要在管線鏈中使用較低優先順序的語法，請考慮使用括弧 `(...)` 。
同樣地，若要在管線鏈內內嵌語句， `$(...)` 可以使用子運算式。
這有助於將原生命令與控制流程結合：

```powershell
foreach ($file in 'file1','file2','file3')
{
    # When find succeeds, the loop breaks
    find $file && Write-Output "Found $file" && $(break)
}
```

```Output
find: file1: No such file or directory
file2
Found file2
```

從 PowerShell 7 起，這些語法的行為已變更，因此 `$?` 當命令在括弧或子運算式內成功或失敗時，會如預期般設定。

與 PowerShell 中的大部分其他運算子相同， `&&` 而且 `||` 也是 *左關聯* 的，這表示它們是從左方群組。 例如：

```powershell
Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist" && Get-Content -Raw ./file.txt
```

將分組為：

```
[Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist"] && Get-Content -Raw ./file.txt
```

相當於：

```powershell
Get-ChildItem -Path ./file.txt

if (-not $?) { Write-Error "file.txt does not exist" }

if ($?) { Get-Content -Raw ./file.txt }
```

### <a name="error-interaction"></a>錯誤互動

管線鏈運算子不會吸收錯誤。 當管線鏈中的語句擲回腳本終止錯誤時，管線鏈就會終止。

例如：

```powershell
$(throw 'Bad') || Write-Output '2'
```

```Output
Exception: Bad
```

即使在攔截到錯誤時，管線鏈仍會終止：

```powershell
try
{
    $(throw 'Bad') || Write-Output '2'
}
catch
{
    Write-Output "Caught: $_"
}
Write-Output 'Done'
```

```Output
Caught: Bad
Done
```

如果錯誤為非終止，或只終止管線，管線鏈會繼續進行，並遵循 `$?` 下列值：

```powershell
function Test-NonTerminatingError
{
    [CmdletBinding()]
    param()

    $exception = [System.Exception]::new('BAD')
    $errorId = 'BAD'
    $errorCategory = 'NotSpecified'

    $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

    $PSCmdlet.WriteError($errorRecord)
}

Test-NonTerminatingError || Write-Output 'Second'
```

```Output
Test-NonTerminatingError: BAD
Second
```

### <a name="chaining-pipelines-rather-than-commands"></a>連結管線而非命令

管線鏈運算子的名稱可以用來串連管線，而不只是命令。 這符合其他 shell 的行為，但 *可讓您* 更難以判斷：

```powershell
function Test-NotTwo
{
    [CmdletBinding()]
    param(
      [Parameter(ValueFromPipeline)]
      $Input
    )

    process
    {
        if ($Input -ne 2)
        {
            return $Input
        }

        $exception = [System.Exception]::new('Input is 2')
        $errorId = 'InputTwo'
        $errorCategory = 'InvalidData'

        $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

        $PSCmdlet.WriteError($errorRecord)
    }
}

1,2,3 | Test-NotTwo && Write-Output 'All done!'
```

```Output
1
Test-NotTwo : Input is 2
3
```

請注意， `Write-Output 'All done!'` 因為在 `Test-NotTwo` 產生非終止錯誤之後被視為失敗，所以不會執行。

## <a name="see-also"></a>另請參閱

- [about_Operators](about_Operators.md)
- [about_Automatic_Variables](about_Automatic_Variables.md)
- [about_pipelines](about_pipelines.md)

