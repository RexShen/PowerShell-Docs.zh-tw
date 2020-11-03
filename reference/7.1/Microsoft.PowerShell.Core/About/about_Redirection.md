---
description: 說明如何將 PowerShell 的輸出重新導向至文字檔。
keywords: PowerShell，Cmdlet
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: 1a532aeacf6347023c95905c82aa1f221835a729
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208524"
---
# <a name="about-redirection"></a>關於重新導向

## <a name="short-description"></a>簡短描述
說明如何將 PowerShell 的輸出重新導向至文字檔。

## <a name="long-description"></a>完整描述

根據預設，PowerShell 會將輸出傳送至 PowerShell 主機。 這通常是主控台應用程式。 不過，您可以將輸出導向文字檔，也可以將錯誤輸出重新導向至一般輸出資料流程。

您可以使用下列方法來重新導向輸出：

- 使用 `Out-File` Cmdlet 將命令輸出傳送至文字檔。
  一般來說， `Out-File` 當您需要使用它的參數（例如 `Encoding` 、 `Force` 、 `Width` 或參數）時，您會使用 Cmdlet `NoClobber` 。

- 使用 `Tee-Object` Cmdlet，此 Cmdlet 會將命令輸出傳送至文字檔，然後將它傳送至管線。

- 使用 PowerShell 重新導向運算子。 搭配使用重新導向運算子與檔案目標，在功能上相當於傳送到 `Out-File` 無額外參數的管道。

如需資料流程的詳細資訊，請參閱 [about_Output_Streams](about_Output_Streams.md)。

### <a name="redirectable-output-streams"></a>可重新導向輸出資料流程

PowerShell 支援下列輸出資料流程的重新導向。

| 流# |      Description       | 引進于  |    Write Cmdlet     |
| -------- | ---------------------- | -------------- | ------------------- |
| 1        | **成功** 流     | PowerShell 2.0 | `Write-Output`      |
| 2        | **錯誤** 流       | PowerShell 2.0 | `Write-Error`       |
| 3        | **警告** 流     | PowerShell 3.0 | `Write-Warning`     |
| 4        | **詳細** 資訊流     | PowerShell 3.0 | `Write-Verbose`     |
| 5        | **Debug** 流       | PowerShell 3.0 | `Write-Debug`       |
| 6        | **資訊** 流 | PowerShell 5.0 | `Write-Information` |
| *        | 所有資料流程            | PowerShell 3.0 |                     |

> [!NOTE]
> PowerShell 中也有 **進度** 串流，但不支援重新導向。

### <a name="powershell-redirection-operators"></a>PowerShell 重新導向操作員

PowerShell 重新導向運算子如下所示，其中 `n` 代表資料流程號碼。 如果未指定任何資料流程，則 **成功** 的資料流程 ( `1` ) 為預設值。

| 運算子 |                         描述                         | Syntax |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | 將指定的資料流程傳送至檔案。                            | `n>`   |
| `>>`     | 將指定的資料流程 **附加** 至檔案。                      | `n>>`  |
| `>&1`    | 將指定的資料流程重新 _導向_ 至 **成功** 資料流程。 | `n>&1` |

> [!NOTE]
> 與某些 Unix shell 不同的是，您只能將其他資料流程重新導向至 **成功** 串流。

## <a name="examples"></a>範例

### <a name="example-1-redirect-errors-and-output-to-a-file"></a>範例1：將錯誤和輸出重新導向至檔案

此範例 `dir` 會在一個將成功的專案上執行，另一個則會發生錯誤。

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

它會使用 `2>&1` 將 **錯誤** 資料流程重新導向至 **成功** 資料流程，並將 `>` 結果 **成功** 資料流程傳送至名為 `dir.log`

### <a name="example-2-send-all-success-stream-data-to-a-file"></a>範例2：將所有成功的資料流程資料傳送至檔案

此範例會將所有 **成功** 的資料流程資料傳送至名為的檔案 `script.log` 。

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a>範例3：將成功、警告和錯誤資料流程傳送至檔案

這個範例會示範如何結合重新導向運算子，以達成所需的結果。

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > P:\Temp\redirection.log
```

- `3>&1` 將 **警告** 資料流程重新導向至 **成功** 資料流程。
- `2>&1` 將 **錯誤** 資料流程重新導向至 **成功** 串流， (現在也包含所有 **警告** 資料流程資料) 
- `>` 重新導向 **成功** 資料流程 (現在包含 **警告** 和 **錯誤** 資料流程) 至名為的檔案 `C:\temp\redirection.log`) 

### <a name="example-4-redirect-all-streams-to-a-file"></a>範例4：將所有資料流程重新導向至檔案

此範例會將呼叫之腳本的所有資料流程輸出傳送 `script.ps1` 給稱為 `script.log`

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a>範例5：隱藏所有 Write-Host 和資訊串流資料

此範例會隱藏所有資訊串流資料。 若要閱讀 **資訊** 串流 Cmdlet 的詳細資訊，請參閱 [寫入主機](xref:Microsoft.PowerShell.Utility.Write-Host) 和 [寫入資訊](xref:Microsoft.PowerShell.Utility.Write-Information)

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a>範例6：顯示動作喜好設定的效果

動作喜好設定變數和參數可以變更寫入特定資料流程的內容。 此範例中的腳本會顯示的值 `$ErrorActionPreference` 會如何影響寫入至 **錯誤** 資料流程的內容。

```powershell
$ErrorActionPreference = 'Continue'
$ErrorActionPreference > log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'SilentlyContinue'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Stop'
$ErrorActionPreference >> log.txt
Try {
    get-item /not-here 2>&1 >> log.txt
}
catch {
    "`tError caught!" >> log.txt
}
$ErrorActionPreference = 'Ignore'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Inquire'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Continue'
```

當我們執行此腳本時，當設定為時，會出現提示 `$ErrorActionPreference` `Inquire` 。

```powershell
PS C:\temp> .\test.ps1

Confirm
Cannot find path 'C:\not-here' because it does not exist.
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): H
Get-Item: C:\temp\test.ps1:23
Line |
  23 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The running command stopped because the user selected the Stop option.
```

當我們檢查記錄檔時，會看到下列內容：

```
PS C:\temp> Get-Content .\log.txt
Continue

Get-Item: C:\temp\test.ps1:3
Line |
   3 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | Cannot find path 'C:\not-here' because it does not exist.

SilentlyContinue
Stop
    Error caught!
Ignore
Inquire
```

## <a name="notes"></a>備忘稿

未附加資料 (`>` 和 `n>`) 會覆寫指定檔案的目前內容而不會發出警告的重新導向運算子。

但是，如果檔案是唯讀、隱藏或系統檔案，則重新導向 **會失敗** 。 附加重新導向運算子 (`>>` 和 `n>>`) 不會寫入至唯讀檔案，但是會將內容附加至系統或隱藏的檔案。

若要強制將內容重新導向至唯讀、隱藏或系統檔案，請使用 `Out-File` Cmdlet 搭配其 `Force` 參數。

當您寫入檔案時，重新導向運算子會使用 `UTF8NoBOM` 編碼。 如果檔案具有不同的編碼方式，輸出的格式可能會不正確。 若要寫入具有不同編碼的檔案，請使用 `Out-File` Cmdlet 搭配其 `Encoding` 參數。

### <a name="potential-confusion-with-comparison-operators"></a>比較運算子的潛在混淆

`>`運算子不會與[大於](about_Comparison_Operators.md#-gt)比較運算子混淆 (通常表示為 `>` 其他程式設計語言) 。

根據所比較的物件而定，使用的輸出 `>` 可能會是正確的 (因為36不大於 42) 。

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

不過，檢查本機檔案系統可以看到 `42` 已寫入的檔案，以及內容 `36` 。

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

嘗試使用反向比較 `<` (小於) ，會產生系統錯誤：

```powershell
PS> if (36 < 42) { "true" } else { "false" }
At line:1 char:8
+ if (36 < 42) { "true" } else { "false" }
+        ~
The '<' operator is reserved for future use.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : RedirectionNotSupported
```

如果數值比較是必要的作業， `-lt` 則 `-gt` 應該使用。 請參閱： [ `-gt` 比較運算子](about_Comparison_Operators.md#-gt)

## <a name="see-also"></a>另請參閱

- [Out-File](xref:Microsoft.PowerShell.Utility.Out-File)
- [Tee-Object](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error)
- [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host)
- [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)
- [Write-Output](xref:Microsoft.PowerShell.Utility.Write-Output)
- [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [about_Output_Streams](about_Output_Streams.md)
- [about_Operators](about_Operators.md)
- [about_Command_Syntax](about_Command_Syntax.md)
- [about_Path_Syntax](about_Path_Syntax.md)
