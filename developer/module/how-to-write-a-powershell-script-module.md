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
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="f8f36-102">如何撰寫 PowerShell 指令碼模組</span><span class="sxs-lookup"><span data-stu-id="f8f36-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="f8f36-103">指令碼模組是基本上是任何有效 PowerShell 指令碼儲存在副檔名為.psm1。</span><span class="sxs-lookup"><span data-stu-id="f8f36-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="f8f36-104">此延伸模組可讓您的檔案上使用幾個規則和指令程式的 PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="f8f36-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="f8f36-105">大部分的這些功能是為了協助您，以及管理範圍設定其他系統上安裝您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f8f36-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="f8f36-106">您也可以使用模組資訊清單檔案，可以描述更複雜的安裝和解決方案。</span><span class="sxs-lookup"><span data-stu-id="f8f36-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="f8f36-107">撰寫 PowerShell 指令碼模組</span><span class="sxs-lookup"><span data-stu-id="f8f36-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="f8f36-108">您可以建立指令碼模組將有效的 PowerShell 指令碼儲存至.psm1 檔案，並位於 PowerShell 可以找到的目錄中儲存該檔案。</span><span class="sxs-lookup"><span data-stu-id="f8f36-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="f8f36-109">在該資料夾中，您也可以將您要執行指令碼的任何資源，以及資訊清單檔案描述 powershell 模組的運作方式。</span><span class="sxs-lookup"><span data-stu-id="f8f36-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="f8f36-110">若要建立基本的 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="f8f36-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="f8f36-111">採用現有的 PowerShell 指令碼，並儲存指令碼，副檔名為.psm1。</span><span class="sxs-lookup"><span data-stu-id="f8f36-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="f8f36-112">儲存具有.psm1 的指令碼擴充功能表示您可以使用模組的 cmdlet，例如[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)，在其上。</span><span class="sxs-lookup"><span data-stu-id="f8f36-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="f8f36-113">這些 cmdlet 級主要，如此您就可以輕鬆地匯入和匯出您的程式碼，其他使用者的系統上。</span><span class="sxs-lookup"><span data-stu-id="f8f36-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="f8f36-114">（替代方案是其他系統，然後再點溯源的程式碼將其載入至使用中記憶體，這並不是特別可調整的解決方案。）如需詳細資訊，請參閱**Module Cmdlet 和變數**一節[Windows PowerShell 模組](./understanding-a-windows-powershell-module.md)請注意，根據預設，在您的指令碼中的所有函式將使用者匯入您的.psm1 都可以存取檔案，但屬性則不會。</span><span class="sxs-lookup"><span data-stu-id="f8f36-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script will be accessible to users who import your .psm1 file, but properties will not.</span></span>

   <span data-ttu-id="f8f36-115">使用本主題結尾處範例 PowerShell 指令碼中，名為顯示行事曆。</span><span class="sxs-lookup"><span data-stu-id="f8f36-115">An example PowerShell script, entitled Show-Calendar, is available at the end of this topic.</span></span>

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

2. <span data-ttu-id="f8f36-116">如果您想要控制使用者存取特定的函式或屬性，呼叫[Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember)在您的指令碼結尾。</span><span class="sxs-lookup"><span data-stu-id="f8f36-116">If you wish to control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="f8f36-117">在頁面底部的範例程式碼有只有一個函式，會公開其預設值。</span><span class="sxs-lookup"><span data-stu-id="f8f36-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="f8f36-118">不過，我們建議您明確地呼叫出您想要公開，如下列程式碼中所述的函式：</span><span class="sxs-lookup"><span data-stu-id="f8f36-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="f8f36-119">您也可以限制項目使用 匯入的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="f8f36-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="f8f36-120">如需詳細資訊，請參閱 <<c0> [ 匯入 PowerShell 模組](./importing-a-powershell-module.md)並[如何撰寫 PowerShell 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f36-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="f8f36-121">如果您有自己的模組都必須已載入的模組，您可以使用這些呼叫`Import-Module`，在您自己的模組的頂端。</span><span class="sxs-lookup"><span data-stu-id="f8f36-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="f8f36-122">`Import-Module` 是匯入到系統目標的模組的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f8f36-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="f8f36-123">因此，它也會於稍後在程序來安裝您自己的模組，以及。</span><span class="sxs-lookup"><span data-stu-id="f8f36-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="f8f36-124">在此頁面底部的範例程式碼不使用任何匯入模組。</span><span class="sxs-lookup"><span data-stu-id="f8f36-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="f8f36-125">如果有，不過，它們會被列頂端的檔案，如下列程式碼中所述：</span><span class="sxs-lookup"><span data-stu-id="f8f36-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="f8f36-126">如果您想要描述您的模組以 PowerShell 說明系統，則可以使用標準說明註解內的檔案，或使用其他的說明檔。</span><span class="sxs-lookup"><span data-stu-id="f8f36-126">If you want to describe your module to the PowerShell Help system, you can do so either with the standard help comments inside the file, or with an additional Help file.</span></span>

   <span data-ttu-id="f8f36-127">在本主題底端的程式碼範例包含註解中的 [說明] 資訊。</span><span class="sxs-lookup"><span data-stu-id="f8f36-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="f8f36-128">如果您選擇如此，您也可以撰寫擴充的 XML 檔案，其中包含其他說明內容。</span><span class="sxs-lookup"><span data-stu-id="f8f36-128">If you so choose, you could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="f8f36-129">如需詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell 模組的說明](./writing-help-for-windows-powershell-modules.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f36-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="f8f36-130">如果您有其他模組、 XML 檔案或您想要封裝您的模組與其他內容，則可以使用模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="f8f36-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="f8f36-131">模組資訊清單是包含名稱的其他模組、 目錄配置、 版本控制編號、 作者資料和其他資訊的檔案。</span><span class="sxs-lookup"><span data-stu-id="f8f36-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="f8f36-132">PowerShell 會使用模組資訊清單檔案，來組織及部署您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="f8f36-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="f8f36-133">不過，由於此範例相當簡單的資訊清單檔不需要。</span><span class="sxs-lookup"><span data-stu-id="f8f36-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="f8f36-134">如需詳細資訊，請參閱 <<c0> [ 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f36-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="f8f36-135">若要安裝及執行您的模組，將模組儲存至其中一個適當的 PowerShell 路徑中，並呼叫`Import-Module`。</span><span class="sxs-lookup"><span data-stu-id="f8f36-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="f8f36-136">您可以在其中安裝您的模組路徑位於`$env:PSModulePath`全域變數。</span><span class="sxs-lookup"><span data-stu-id="f8f36-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="f8f36-137">比方說，是常見的路徑，以在系統上儲存模組`%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`。</span><span class="sxs-lookup"><span data-stu-id="f8f36-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="f8f36-138">請務必建立您的模組中，存在的資料夾，即使它是單一.psm1 檔案。</span><span class="sxs-lookup"><span data-stu-id="f8f36-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="f8f36-139">如果沒有這些路徑來儲存您的模組，您必須在模組的呼叫中的位置傳遞`Import-Module`。</span><span class="sxs-lookup"><span data-stu-id="f8f36-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="f8f36-140">（否則 PowerShell 會無法找到它。）如果您已在其中一個 PowerShell 模組路徑上放置您的模組與 PowerShell 3.0 中，從開始，您不需要明確地將它匯入： 單純地呼叫您的函式的使用者將會自動將其載入。</span><span class="sxs-lookup"><span data-stu-id="f8f36-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module on one of the PowerShell module paths, you do not need to explicitly import it: simply having a user call your function will automatically load it.</span></span> <span data-ttu-id="f8f36-141">如需有關模組路徑的詳細資訊，請參閱[匯入 PowerShell 模組](./importing-a-powershell-module.md)並[PSModulePath 環境變數](./modifying-the-psmodulepath-installation-path.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f36-141">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="f8f36-142">若要移除作用中的服務中的模組，請呼叫[Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)。</span><span class="sxs-lookup"><span data-stu-id="f8f36-142">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

<span data-ttu-id="f8f36-143">請注意， [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)移除您的模組從作用中的記憶體-它不會實際刪除它從儲存的模組檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="f8f36-143">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="f8f36-144">顯示行事曆程式碼範例</span><span class="sxs-lookup"><span data-stu-id="f8f36-144">Show-Calendar code example</span></span>

<span data-ttu-id="f8f36-145">下列範例是簡單的指令碼模組，其中包含名為 「 顯示日曆的單一函式。</span><span class="sxs-lookup"><span data-stu-id="f8f36-145">The following example is a simple script module that contains a single function named Show-Calendar.</span></span> <span data-ttu-id="f8f36-146">此函式會顯示行事曆的視覺表示法。</span><span class="sxs-lookup"><span data-stu-id="f8f36-146">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="f8f36-147">此外，此範例包含概要、 描述、 參數值，與範例的 PowerShell 說明字串。</span><span class="sxs-lookup"><span data-stu-id="f8f36-147">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="f8f36-148">請注意程式碼的最後一行表示，顯示行事曆函式會匯出為模組成員匯入模組時。</span><span class="sxs-lookup"><span data-stu-id="f8f36-148">Note that the last line of code indicates that the Show-Calendar function will be exported as a module member when the module is imported.</span></span>

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
