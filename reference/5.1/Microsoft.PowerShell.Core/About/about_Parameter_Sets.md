---
description: 描述如何在 advanced 函數中定義和使用參數集。
title: about_Parameter_Sets
ms.date: 02/11/2020
ms.openlocfilehash: e4cfbc13f981bcc93c8a0a3c799851e83df7746c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207979"
---
# <a name="about-parameter-sets"></a>關於參數集

## <a name="short-description"></a>簡短描述
描述如何在 advanced 函數中定義和使用參數集。

## <a name="long-description"></a>詳細描述

PowerShell 會使用參數集，讓您撰寫可針對不同案例執行不同動作的單一函式。 參數集可讓您向使用者公開不同的參數。 和，根據使用者指定的參數傳回不同的資訊。

## <a name="parameter-set-requirements"></a>參數集需求

下列需求適用于所有參數集。

- 每個參數集都必須至少有一個唯一的參數。 可能的話，請將此參數設為必要參數。

- 包含多個位置參數的參數集必須定義每個參數的唯一位置。 沒有兩個位置參數可以指定相同的位置。

- 只有一個集合中的參數可以宣告 `ValueFromPipeline` 具有值的關鍵字 `true` 。 多個參數可以定義 `ValueFromPipelineByPropertyName` 具有值的關鍵字 `true` 。

- 如果未指定參數的參數集，參數將屬於所有參數集。

> [!NOTE]
> 有32參數集的限制。

## <a name="default-parameter-sets"></a>預設參數集

定義多個參數集時， `DefaultParameterSetName` **CmdletBinding** 屬性的關鍵字會指定預設參數集。
當 PowerShell 無法根據提供給命令的資訊判斷要使用的參數時，就會使用預設參數集。 如需 **CmdletBinding** 屬性的詳細資訊，請參閱 [about_functions_Cmdletbindingattribute](about_functions_cmdletbindingattribute.md)。

## <a name="declaring-parameter-sets"></a>宣告參數集

若要建立參數集，您必須 `ParameterSetName` 針對參數集內的每個參數，指定 **參數** 屬性的關鍵字。 對於屬於多個參數集的參數，請為每個參數集加入 **參數** 屬性。

**Parameter** 屬性可讓您針對每個參數集定義不同的參數。 例如，您可以在一個集合中將參數定義為強制，並在另一個集合中定義選擇性參數。 不過，每個參數集都必須包含至少一個唯一的參數。

未指派參數集名稱的參數，屬於所有參數集。

### <a name="example"></a>範例

下列範例函數會計算文字檔中的數位行、字元和單字。 您可以使用參數來指定要傳回的值，以及要測量的檔案。 有四個參數集已定義：

- 路徑
- PathAll
- LiteralPath
- LiteralPathAll

```powershell
function Measure-Lines {
    [CmdletBinding(DefaultParameterSetName = 'Path')]
    param (
        [Parameter(Mandatory = $true,
            ParameterSetName = 'Path',
            HelpMessage = 'Enter one or more filenames',
            Position = 0)]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'PathAll',
            Position = 0)]
        [string[]]$Path,

        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'LiteralPath',
            HelpMessage = 'Enter a single filename',
            ValueFromPipeline = $true)]
        [string]$LiteralPath,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Lines,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Words,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Characters,

        [Parameter(Mandatory = $true, ParameterSetName = 'PathAll')]
        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [switch]$All,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'PathAll')]
        [switch]$Recurse
    )

    begin {
        if ($All) {
            $Lines = $Words = $Characters = $true
        }
        elseif (($Words -eq $false) -and ($Characters -eq $false)) {
            $Lines = $true
        }

        if ($Path) {
            $Files = Get-ChildItem -Path $Path -Recurse:$Recurse
        }
        else {
            $Files = Get-ChildItem -LiteralPath $LiteralPath
        }
    }
    process {
        foreach ($file in $Files) {
            $result = [ordered]@{ }
            $result.Add('File', $file.fullname)

            $content = Get-Content -LiteralPath $file.fullname

            if ($Lines) { $result.Add('Lines', $content.Length) }

            if ($Words) {
                $wc = 0
                foreach ($line in $content) { $wc += $line.split(' ').Length }
                $result.Add('Words', $wc)
            }

            if ($Characters) {
                $cc = 0
                foreach ($line in $content) { $cc += $line.Length }
                $result.Add('Characters', $cc)
            }

            New-Object -TypeName psobject -Property $result
        }
    }
}
```

每個參數集都必須有唯一的參數或唯一的參數組合。 `Path`和 `PathAll` 參數集非常類似，但 **All** 參數對參數集而言是唯一的 `PathAll` 。 `LiteralPath`和參數集也是如此 `LiteralPathAll` 。 即使 `PathAll` 和 `LiteralPathAll` 參數設定都有 **All** 參數， **Path** 和 **LiteralPath** 參數還是會區分它們。

使用 `Get-Command -Syntax` 會顯示每個參數集的語法。 但是，它不會顯示參數集的名稱。 下列範例顯示每個參數集可使用的參數。

```powershell
(Get-Command Measure-Lines).ParameterSets |
  Select-Object -Property @{n='ParameterSetName';e={$_.name}},
    @{n='Parameters';e={$_.ToString()}}
```

```Output
ParameterSetName Parameters
---------------- ----------
Path             [-Path] <string[]> [-Lines] [-Words] [-Characters] [-Recurse] [<CommonParameters>]
PathAll          [-Path] <string[]> -All [-Recurse] [<CommonParameters>]
LiteralPath      -LiteralPath <string> [-Lines] [-Words] [-Characters] [<CommonParameters>]
LiteralPathAll   -LiteralPath <string> -All [<CommonParameters>]
```

### <a name="parameter-sets-in-action"></a>作用中的參數集

在此範例中，我們使用 `PathAll` 參數集。

```powershell
Measure-Lines test* -All
```

```Output
File                       Lines Words Characters
----                       ----- ----- ----------
C:\temp\test\test.help.txt    31   562       2059
C:\temp\test\test.md          30  1527       3224
C:\temp\test\test.ps1          3     3         79
C:\temp\test\test[1].txt      31   562       2059
```
