---
title: 如何撰寫 PowerShell 指令碼模組 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: e8b7151538235cdf7183b78aa8df7e596d6bcfd9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859004"
---
# <a name="how-to-write-a-powershell-script-module"></a>如何撰寫 PowerShell 指令碼模組

指令碼模組是基本上是任何有效 PowerShell 指令碼儲存在副檔名為.psm1。 此延伸模組可讓您的檔案上使用幾個規則和指令程式的 PowerShell 引擎。 大部分的這些功能是為了協助您，以及管理範圍設定其他系統上安裝您的程式碼。 您也可以使用模組資訊清單檔案，可以描述更複雜的安裝和解決方案。

## <a name="writing-a-powershell-script-module"></a>撰寫 PowerShell 指令碼模組

您可以建立指令碼模組將有效的 PowerShell 指令碼儲存至.psm1 檔案，並位於 PowerShell 可以找到的目錄中儲存該檔案。 在該資料夾中，您也可以將您要執行指令碼的任何資源，以及資訊清單檔案描述 powershell 模組的運作方式。

#### <a name="to-create-a-basic-powershell-module"></a>若要建立基本的 PowerShell 模組

1. 採用現有的 PowerShell 指令碼，並儲存指令碼，副檔名為.psm1。

   儲存具有.psm1 的指令碼擴充功能表示您可以使用模組的 cmdlet，例如[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)，在其上。 這些 cmdlet 級主要，如此您就可以輕鬆地匯入和匯出您的程式碼，其他使用者的系統上。 （替代方案是其他系統，然後再點溯源的程式碼將其載入至使用中記憶體，這並不是特別可調整的解決方案。）如需詳細資訊，請參閱**Module Cmdlet 和變數**一節[Windows PowerShell 模組](./understanding-a-windows-powershell-module.md)請注意，根據預設，在您的指令碼中的所有函式將使用者匯入您的.psm1 都可以存取檔案，但屬性則不會。

   使用本主題結尾處範例 PowerShell 指令碼中，名為顯示行事曆。

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

2. 如果您想要控制使用者存取特定的函式或屬性，呼叫[Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember)在您的指令碼結尾。

   在頁面底部的範例程式碼有只有一個函式，會公開其預設值。 不過，我們建議您明確地呼叫出您想要公開，如下列程式碼中所述的函式：

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   您也可以限制項目使用 匯入的模組資訊清單。 如需詳細資訊，請參閱 <<c0> [ 匯入 PowerShell 模組](./importing-a-powershell-module.md)並[如何撰寫 PowerShell 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。

3. 如果您有自己的模組都必須已載入的模組，您可以使用這些呼叫`Import-Module`，在您自己的模組的頂端。

   `Import-Module` 是匯入到系統目標的模組的 cmdlet。 因此，它也會於稍後在程序來安裝您自己的模組，以及。 在此頁面底部的範例程式碼不使用任何匯入模組。 如果有，不過，它們會被列頂端的檔案，如下列程式碼中所述：

   ```powershell
   Import-Module GenericModule
   ```

4. 如果您想要描述您的模組以 PowerShell 說明系統，則可以使用標準說明註解內的檔案，或使用其他的說明檔。

   在本主題底端的程式碼範例包含註解中的 [說明] 資訊。 如果您選擇如此，您也可以撰寫擴充的 XML 檔案，其中包含其他說明內容。 如需詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell 模組的說明](./writing-help-for-windows-powershell-modules.md)。

5. 如果您有其他模組、 XML 檔案或您想要封裝您的模組與其他內容，則可以使用模組資訊清單。

   模組資訊清單是包含名稱的其他模組、 目錄配置、 版本控制編號、 作者資料和其他資訊的檔案。 PowerShell 會使用模組資訊清單檔案，來組織及部署您的解決方案。 不過，由於此範例相當簡單的資訊清單檔不需要。 如需詳細資訊，請參閱 <<c0> [ 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。

6. 若要安裝及執行您的模組，將模組儲存至其中一個適當的 PowerShell 路徑中，並呼叫`Import-Module`。

   您可以在其中安裝您的模組路徑位於`$env:PSModulePath`全域變數。 比方說，是常見的路徑，以在系統上儲存模組`%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`。 請務必建立您的模組中，存在的資料夾，即使它是單一.psm1 檔案。 如果沒有這些路徑來儲存您的模組，您必須在模組的呼叫中的位置傳遞`Import-Module`。 （否則 PowerShell 會無法找到它。）如果您已在其中一個 PowerShell 模組路徑上放置您的模組與 PowerShell 3.0 中，從開始，您不需要明確地將它匯入： 單純地呼叫您的函式的使用者將會自動將其載入。 如需有關模組路徑的詳細資訊，請參閱[匯入 PowerShell 模組](./importing-a-powershell-module.md)並[PSModulePath 環境變數](./modifying-the-psmodulepath-installation-path.md)。

7. 若要移除作用中的服務中的模組，請呼叫[Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)。

請注意， [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)移除您的模組從作用中的記憶體-它不會實際刪除它從儲存的模組檔案的位置。

### <a name="show-calendar-code-example"></a>顯示行事曆程式碼範例

下列範例是簡單的指令碼模組，其中包含名為 「 顯示日曆的單一函式。 此函式會顯示行事曆的視覺表示法。 此外，此範例包含概要、 描述、 參數值，與範例的 PowerShell 說明字串。 請注意程式碼的最後一行表示，顯示行事曆函式會匯出為模組成員匯入模組時。

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
    $width = ($calendar.Split("'n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " 'n" + $padding + $header + "'n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
