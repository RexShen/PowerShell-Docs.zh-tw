---
title: 如何撰寫 PowerShell 腳本模組 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360687"
---
# <a name="how-to-write-a-powershell-script-module"></a>如何撰寫 PowerShell 指令碼模組

腳本模組基本上是儲存在 .psm1 副檔名中的任何有效 PowerShell 腳本。 此延伸模組可讓 PowerShell 引擎在您的檔案上使用多個規則和 Cmdlet。 其中大部分的功能都可協助您在其他系統上安裝程式碼，以及管理範圍。 您也可以使用模組資訊清單檔案，它可以描述更複雜的安裝和解決方案。

## <a name="writing-a-powershell-script-module"></a>撰寫 PowerShell 腳本模組

若要建立腳本模組，請將有效的 PowerShell 腳本儲存至 .psm1 檔案，然後將該檔案儲存在 PowerShell 可以找到該檔案的目錄中。 在該資料夾中，您也可以放置執行腳本所需的任何資源，以及向 PowerShell 描述模組運作方式的資訊清單檔案。

#### <a name="to-create-a-basic-powershell-module"></a>建立基本 PowerShell 模組

1. 採用現有的 PowerShell 腳本，並以 .psm1 副檔名儲存腳本。

   儲存副檔名為 .psm1 的腳本，表示您可以在其上使用模組 Cmdlet，[例如 import-module。](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 這些 Cmdlet 主要是為了讓您可以輕鬆地將程式碼匯入和匯出至其他使用者的系統。 （替代方案是在其他系統上載入您的程式碼，然後將其指向使用中的記憶體，這不是特別可擴充的解決方案）。如需詳細資訊，請參閱[Windows PowerShell 模組](./understanding-a-windows-powershell-module.md)中的**模組 Cmdlet 和變數**一節，請注意，根據預設，匯入 .psm1 檔案的使用者可以存取腳本中的所有函式，但不會有屬性。

   本主題的結尾有提供 @no__t 為-0 的 PowerShell 腳本範例。

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

2. 若要控制使用者對特定函數或屬性的存取權，請在腳本結尾呼叫[export-modulemember 的匯出](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember)。

   頁面底部的範例程式碼只有一個函式，預設會公開此函式。 不過，建議您明確地呼叫您想要公開的函式，如下列程式碼所述：

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   您也可以使用模組資訊清單來限制匯入的內容。 如需詳細資訊，請參閱匯[入 Powershell 模組](./importing-a-powershell-module.md)和[如何撰寫 Powershell 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。

3. 如果您有自己模組需要載入的模組，您可以在自己模組的頂端呼叫 `Import-Module` 來使用它們。

   `Import-Module` 是將目的模組匯入系統上的 Cmdlet。 因此，在稍後的程式中也會使用它來安裝您自己的模組。 此頁面底部的範例程式碼不會使用任何匯入模組。 不過，如果已這麼做，則會列在檔案的頂端，如下列程式碼所述：

   ```powershell
   Import-Module GenericModule
   ```

4. 若要向 PowerShell 說明系統描述您的模組，您可以在檔案內使用標準說明批註，或建立額外的說明檔。

   本主題底部的程式碼範例包含批註中的說明資訊。 您也可以撰寫包含其他說明內容的擴充 XML 檔案。 如需詳細資訊，請參閱[撰寫 Windows PowerShell 模組的](./writing-help-for-windows-powershell-modules.md)說明。

5. 如果您有其他模組、XML 檔案或其他您想要使用模組封裝的內容，您可以使用模組資訊清單來執行此動作。

   模組資訊清單是一個檔案，其中包含其他模組的名稱、目錄配置、版本控制編號、作者資料和其他資訊片段。 PowerShell 會使用模組資訊清單檔案來組織和部署您的解決方案。 不過，由於此範例的本質相當簡單，因此不需要資訊清單檔案。 如需詳細資訊，請參閱[模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。

6. 若要安裝並執行您的模組，請將模組儲存到其中一個適當的 PowerShell 路徑，並對 `Import-Module` 進行呼叫。

   您可以安裝模組的路徑位於 `$env:PSModulePath` 全域變數中。 例如，在系統上儲存模組的一般路徑會 `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`。 請務必建立一個資料夾，讓您的模組存在於中，即使它只是一個 .psm1 檔案也一樣。 如果您未將模組儲存到其中一個路徑，您就必須在 `Import-Module` 的呼叫中傳入模組的位置。 （否則，PowerShell 就找不到它）。從 PowerShell 3.0 開始，如果您將模組放在其中一個 PowerShell 模組路徑中，則不需要明確地將它匯入。 當使用者呼叫您的函式時，系統會自動載入您的模組。
   如需模組路徑的詳細資訊，請參閱匯[入 PowerShell 模組](./importing-a-powershell-module.md)和[PSModulePath 環境變數](./modifying-the-psmodulepath-installation-path.md)。

7. 若要從作用中的服務移除模組，請呼叫[Remove 模組](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)。

   請注意，[移除模組](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)會從使用中記憶體中移除您的模組，而不會實際將它從您儲存模組檔案的位置刪除。

### <a name="show-calendar-code-example"></a>顯示行事歷程序代碼範例

下列範例是簡單的腳本模組，其中包含名為 `Show-Calendar` 的單一函數。
此函式會顯示行事曆的視覺標記法。 此外，此範例包含適用于概要、描述、參數值和範例的 PowerShell 說明字串。 請注意，程式碼的最後一行可確保在匯入模組時，會將 `Show-Calendar` 函數匯出為模組成員。

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
