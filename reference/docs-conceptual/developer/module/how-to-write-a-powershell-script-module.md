---
ms.date: 11/21/2019
ms.topic: reference
title: 如何撰寫 PowerShell 指令碼模組
description: 如何撰寫 PowerShell 指令碼模組
ms.openlocfilehash: c44b09a915501fb10773ab11cf13136d5035ba69
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649150"
---
# <a name="how-to-write-a-powershell-script-module"></a>如何撰寫 PowerShell 指令碼模組

腳本模組是儲存在延伸模組中的任何有效的 PowerShell 腳本 `.psm1` 。 此延伸模組可讓 PowerShell 引擎在您的檔案上使用規則和模組 Cmdlet。 其中大部分功能都可協助您在其他系統上安裝程式碼，以及管理範圍。 您也可以使用模組資訊清單檔，它會說明更複雜的安裝和解決方案。

## <a name="writing-a-powershell-script-module"></a>撰寫 PowerShell 腳本模組

若要建立腳本模組，請將有效的 PowerShell 腳本儲存至檔案 `.psm1` 。 腳本及其儲存所在的目錄必須使用相同的名稱。 例如，名為的腳本 `MyPsScript.psm1` 會儲存在名為的目錄中 `MyPsScript` 。

模組的目錄必須位於指定的路徑中 `$env:PSModulePath` 。 模組的目錄可以包含執行腳本所需的任何資源，以及描述您的模組如何運作的模組資訊清單檔案。

## <a name="create-a-basic-powershell-module"></a>建立基本的 PowerShell 模組

下列步驟說明如何建立 PowerShell 模組。

1. 使用延伸模組儲存 PowerShell 腳本 `.psm1` 。 針對腳本和儲存腳本的目錄使用相同的名稱。

   以延伸模組儲存腳本 `.psm1` ，表示您可以使用模組 Cmdlet，例如 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)。 模組 Cmdlet 主要存在，如此您就可以將程式碼匯入和匯出至其他使用者的系統。 替代解決方案是在其他系統上載入您的程式碼，然後將它指向使用中記憶體，這不是可調整的解決方案。 如需詳細資訊，請參閱 [瞭解 Windows PowerShell 模組](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables)。
   根據預設，當使用者匯入您的檔案時 `.psm1` ，腳本中的所有函式都是可存取的，但變數則不是。

   如需範例 PowerShell 腳本，請參閱本文 `Show-Calendar` 結尾的。

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. 若要控制使用者對特定函式或變數的存取權，請在腳本結束時呼叫 [Export-export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) 。

   本文底部的範例程式碼只有一個函式，預設會公開此函數。 不過，建議您明確地呼叫要公開的函式，如下列程式碼所述：

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   您可以使用模組資訊清單來限制匯入的內容。 如需詳細資訊，請參閱匯 [入 Powershell 模組](./importing-a-powershell-module.md) 和 [如何寫入 Powershell 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。

3. 如果您有模組需要載入您自己的模組，您可以使用 `Import-Module` 模組頂端的。

   此 `Import-Module` Cmdlet 會將目的模組匯入系統，並可在稍後的程式中用來安裝您自己的模組。 本文底部的範例程式碼不會使用任何匯入模組。 但是，如果有的話，它們會列在檔案的頂端，如下列程式碼所示：

   ```powershell
   Import-Module GenericModule
   ```

4. 若要向 PowerShell 說明系統描述您的模組，您可以使用檔案內的標準說明批註，或建立額外的說明檔。

   本文底部的程式碼範例包含批註中的說明資訊。 您也可以撰寫擴充的 XML 檔案，其中包含其他說明內容。 如需詳細資訊，請參閱 [撰寫 Windows PowerShell 模組的](./writing-help-for-windows-powershell-modules.md)說明。

5. 如果您有其他模組、XML 檔案或您想要使用模組封裝的其他內容，您可以使用模組資訊清單。

   模組資訊清單是一個檔案，其中包含其他模組的名稱、目錄配置、版本號碼、作者資料和其他資訊片段。 PowerShell 會使用模組資訊清單檔案來組織和部署您的解決方案。 如需詳細資訊，請參閱 [如何撰寫 PowerShell 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。

6. 若要安裝並執行您的模組，請將模組儲存至其中一個適當的 PowerShell 路徑，然後使用 `Import-Module` 。

   您可以在其中安裝模組的路徑位於 `$env:PSModulePath` 全域變數中。 例如，在系統上儲存模組的常見路徑是 `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>` 。 請務必為您的模組建立與腳本模組使用相同名稱的目錄，即使它只是單一檔案 `.psm1` 。 如果您未將模組儲存至其中一個路徑，您就必須在命令中指定模組的位置 `Import-Module` 。 否則，PowerShell 將無法找到此模組。

   從 PowerShell 3.0 開始，如果您將模組放在其中一個 PowerShell 模組路徑中，就不需要明確地將其匯入。 當使用者呼叫您的函式時，系統會自動載入您的模組。 如需模組路徑的詳細資訊，請參閱匯 [入 PowerShell 模組](./importing-a-powershell-module.md) 和 [修改 PSModulePath 安裝路徑](./modifying-the-psmodulepath-installation-path.md)。

7. 若要從目前 PowerShell 會話中的作用中服務移除模組，請使用 [Remove 模組](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)。

   > [!NOTE]
   > `Remove-Module` 從目前的 PowerShell 會話移除模組，但不會卸載模組或刪除模組的檔案。

## <a name="show-calendar-code-example"></a>Show-Calendar 程式碼範例

下列範例是包含名為之單一函數的腳本模組 `Show-Calendar` 。 此函式會顯示行事曆的視覺標記法。 此範例包含適用于概要、描述、參數值和程式碼的 PowerShell 說明字串。 匯入模組時，此 `Export-ModuleMember` 命令可確保將 `Show-Calendar` 函數匯出為模組成員。

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("`n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " `n" + $padding + $header + "`n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
