---
title: 如何撰寫 PowerShell 腳本模組 |Microsoft Docs
ms.date: 11/21/2019
ms.openlocfilehash: dc387909a9e55df9f1846b02755e284c408f7dc6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784889"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="de4a8-102">如何撰寫 PowerShell 指令碼模組</span><span class="sxs-lookup"><span data-stu-id="de4a8-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="de4a8-103">腳本模組是儲存在擴充功能中的任何有效 PowerShell 腳本 `.psm1` 。</span><span class="sxs-lookup"><span data-stu-id="de4a8-103">A script module is any valid PowerShell script saved in a `.psm1` extension.</span></span> <span data-ttu-id="de4a8-104">此延伸模組可讓 PowerShell 引擎在您的檔案上使用規則和模組 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="de4a8-104">This extension allows the PowerShell engine to use rules and module cmdlets on your file.</span></span> <span data-ttu-id="de4a8-105">其中大部分的功能都可協助您在其他系統上安裝程式碼，以及管理範圍。</span><span class="sxs-lookup"><span data-stu-id="de4a8-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="de4a8-106">您也可以使用模組資訊清單檔案，其中描述更複雜的安裝和解決方案。</span><span class="sxs-lookup"><span data-stu-id="de4a8-106">You can also use a module manifest file, which describes more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="de4a8-107">撰寫 PowerShell 腳本模組</span><span class="sxs-lookup"><span data-stu-id="de4a8-107">Writing a PowerShell script module</span></span>

<span data-ttu-id="de4a8-108">若要建立腳本模組，請將有效的 PowerShell 腳本儲存至檔案 `.psm1` 。</span><span class="sxs-lookup"><span data-stu-id="de4a8-108">To create a script module, save a valid PowerShell script to a `.psm1` file.</span></span> <span data-ttu-id="de4a8-109">腳本及其儲存所在的目錄必須使用相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="de4a8-109">The script and the directory where it's stored must use the same name.</span></span> <span data-ttu-id="de4a8-110">例如，名為的腳本 `MyPsScript.psm1` 會儲存在名為的目錄中 `MyPsScript` 。</span><span class="sxs-lookup"><span data-stu-id="de4a8-110">For example, a script named `MyPsScript.psm1` is stored in a directory named `MyPsScript`.</span></span>

<span data-ttu-id="de4a8-111">模組的目錄必須位於所指定的路徑中 `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="de4a8-111">The module's directory needs to be in a path specified in `$env:PSModulePath`.</span></span> <span data-ttu-id="de4a8-112">模組的目錄可以包含執行腳本所需的任何資源，以及向 PowerShell 描述模組運作方式的模組資訊清單檔案。</span><span class="sxs-lookup"><span data-stu-id="de4a8-112">The module's directory can contain any resources that are needed to run the script, and a module manifest file that describes to PowerShell how your module works.</span></span>

## <a name="create-a-basic-powershell-module"></a><span data-ttu-id="de4a8-113">建立基本 PowerShell 模組</span><span class="sxs-lookup"><span data-stu-id="de4a8-113">Create a basic PowerShell module</span></span>

<span data-ttu-id="de4a8-114">下列步驟說明如何建立 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="de4a8-114">The following steps describe how to create a PowerShell module.</span></span>

1. <span data-ttu-id="de4a8-115">使用延伸模組來儲存 PowerShell 腳本 `.psm1` 。</span><span class="sxs-lookup"><span data-stu-id="de4a8-115">Save a PowerShell script with a `.psm1` extension.</span></span> <span data-ttu-id="de4a8-116">在腳本和儲存腳本的目錄中使用相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="de4a8-116">Use the same name for the script and the directory where the script is saved.</span></span>

   <span data-ttu-id="de4a8-117">使用延伸模組來儲存腳本 `.psm1` ，表示您可以使用模組 Cmdlet，例如[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)。</span><span class="sxs-lookup"><span data-stu-id="de4a8-117">Saving a script with the `.psm1` extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span> <span data-ttu-id="de4a8-118">模組 Cmdlet 主要存在，讓您可以將程式碼匯入和匯出至其他使用者的系統。</span><span class="sxs-lookup"><span data-stu-id="de4a8-118">The module cmdlets exist primarily so that you can import and export your code onto other user's systems.</span></span> <span data-ttu-id="de4a8-119">替代方案是在其他系統上載入您的程式碼，然後將其指向使用中的記憶體，而這並不是可調整的解決方案。</span><span class="sxs-lookup"><span data-stu-id="de4a8-119">The alternate solution would be to load your code on other systems and then dot-source it into active memory, which isn't a scalable solution.</span></span> <span data-ttu-id="de4a8-120">如需詳細資訊，請參閱[瞭解 Windows PowerShell 模組](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables)。</span><span class="sxs-lookup"><span data-stu-id="de4a8-120">For more information, see [Understanding a Windows PowerShell Module](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).</span></span>
   <span data-ttu-id="de4a8-121">根據預設，當使用者匯入您的檔案時 `.psm1` ，腳本中的所有函式都是可存取的，但變數則不是。</span><span class="sxs-lookup"><span data-stu-id="de4a8-121">By default, when users import your `.psm1` file, all functions in your script are accessible, but variables aren't.</span></span>

   <span data-ttu-id="de4a8-122">如需 PowerShell 腳本範例，請參閱 `Show-Calendar` 這篇文章的結尾。</span><span class="sxs-lookup"><span data-stu-id="de4a8-122">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this article.</span></span>

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

2. <span data-ttu-id="de4a8-123">若要控制使用者對特定函式或變數的存取權，請在腳本結尾呼叫[export-modulemember 的匯出](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember)。</span><span class="sxs-lookup"><span data-stu-id="de4a8-123">To control user access to certain functions or variables, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="de4a8-124">本文底部的範例程式碼只有一個函式，預設會公開此函式。</span><span class="sxs-lookup"><span data-stu-id="de4a8-124">The example code at the bottom of the article has only one function, which by default would be exposed.</span></span> <span data-ttu-id="de4a8-125">不過，建議您明確地呼叫您想要公開的函式，如下列程式碼所述：</span><span class="sxs-lookup"><span data-stu-id="de4a8-125">However, it's recommended you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="de4a8-126">您可以使用模組資訊清單來限制匯入的內容。</span><span class="sxs-lookup"><span data-stu-id="de4a8-126">You can restrict what's imported using a module manifest.</span></span> <span data-ttu-id="de4a8-127">如需詳細資訊，請參閱匯[入 Powershell 模組](./importing-a-powershell-module.md)和[如何撰寫 Powershell 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="de4a8-127">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="de4a8-128">如果您有需要載入自己模組的模組，您可以使用 `Import-Module` 模組頂端的。</span><span class="sxs-lookup"><span data-stu-id="de4a8-128">If you have modules that your own module needs to load, you can use `Import-Module`, at the top of your module.</span></span>

   <span data-ttu-id="de4a8-129">此 `Import-Module` Cmdlet 會將目的模組匯入系統，並可在稍後的程式中用來安裝您自己的模組。</span><span class="sxs-lookup"><span data-stu-id="de4a8-129">The `Import-Module` cmdlet imports a targeted module onto a system, and can be used at a later point in the procedure to install your own module.</span></span> <span data-ttu-id="de4a8-130">本文底部的範例程式碼不會使用任何匯入模組。</span><span class="sxs-lookup"><span data-stu-id="de4a8-130">The sample code at the bottom of this article doesn't use any import modules.</span></span> <span data-ttu-id="de4a8-131">但如果有，則會列在檔案的頂端，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="de4a8-131">But if it did, they would be listed at the top of the file, as shown in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="de4a8-132">若要向 PowerShell 說明系統描述您的模組，您可以在檔案內使用標準說明批註，或建立額外的說明檔。</span><span class="sxs-lookup"><span data-stu-id="de4a8-132">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="de4a8-133">本文底部的程式碼範例包含批註中的說明資訊。</span><span class="sxs-lookup"><span data-stu-id="de4a8-133">The code sample at the bottom of this article includes the help information in the comments.</span></span> <span data-ttu-id="de4a8-134">您也可以撰寫包含其他說明內容的擴充 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="de4a8-134">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="de4a8-135">如需詳細資訊，請參閱[撰寫 Windows PowerShell 模組的](./writing-help-for-windows-powershell-modules.md)說明。</span><span class="sxs-lookup"><span data-stu-id="de4a8-135">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="de4a8-136">如果您有其他模組、XML 檔案或您想要使用模組封裝的其他內容，您可以使用模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="de4a8-136">If you have additional modules, XML files, or other content you want to package with your module, you can use a module manifest.</span></span>

   <span data-ttu-id="de4a8-137">模組資訊清單是一個檔案，其中包含其他模組的名稱、目錄配置、版本控制編號、作者資料和其他資訊片段。</span><span class="sxs-lookup"><span data-stu-id="de4a8-137">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="de4a8-138">PowerShell 會使用模組資訊清單檔案來組織和部署您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="de4a8-138">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="de4a8-139">如需詳細資訊，請參閱[如何撰寫 PowerShell 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="de4a8-139">For more information, see [How to write a PowerShell module manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="de4a8-140">若要安裝並執行您的模組，請將模組儲存到其中一個適當的 PowerShell 路徑，然後使用 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="de4a8-140">To install and run your module, save the module to one of the appropriate PowerShell paths, and use `Import-Module`.</span></span>

   <span data-ttu-id="de4a8-141">您可以安裝模組的路徑位於 `$env:PSModulePath` 全域變數中。</span><span class="sxs-lookup"><span data-stu-id="de4a8-141">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="de4a8-142">例如，在系統上儲存模組的一般路徑會是 `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>` 。</span><span class="sxs-lookup"><span data-stu-id="de4a8-142">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="de4a8-143">請務必為您的模組建立一個目錄，其使用與腳本模組相同的名稱，即使它只是單一檔案 `.psm1` 。</span><span class="sxs-lookup"><span data-stu-id="de4a8-143">Be sure to create a directory for your module that uses the same name as the script module, even if it's only a single `.psm1` file.</span></span> <span data-ttu-id="de4a8-144">如果您未將模組儲存到其中一個路徑，您就必須在命令中指定模組的位置 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="de4a8-144">If you didn't save your module to one of these paths, you would have to specify the module's location in the `Import-Module` command.</span></span> <span data-ttu-id="de4a8-145">否則，PowerShell 將無法找到模組。</span><span class="sxs-lookup"><span data-stu-id="de4a8-145">Otherwise, PowerShell wouldn't be able to find the module.</span></span>

   <span data-ttu-id="de4a8-146">從 PowerShell 3.0 開始，如果您將模組放在其中一個 PowerShell 模組路徑中，則不需要明確地將它匯入。</span><span class="sxs-lookup"><span data-stu-id="de4a8-146">Starting with PowerShell 3.0, if you've placed your module in one of the PowerShell module paths, you don't need to explicitly import it.</span></span> <span data-ttu-id="de4a8-147">當使用者呼叫您的函式時，系統會自動載入您的模組。</span><span class="sxs-lookup"><span data-stu-id="de4a8-147">Your module is automatically loaded when a user calls your function.</span></span> <span data-ttu-id="de4a8-148">如需模組路徑的詳細資訊，請參閱匯[入 PowerShell 模組](./importing-a-powershell-module.md)和[修改 PSModulePath 安裝路徑](./modifying-the-psmodulepath-installation-path.md)。</span><span class="sxs-lookup"><span data-stu-id="de4a8-148">For more information about the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [Modifying the PSModulePath Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="de4a8-149">若要從目前的 PowerShell 會話中的作用中服務移除模組，請使用[移除模組](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)。</span><span class="sxs-lookup"><span data-stu-id="de4a8-149">To remove a module from active service in the current PowerShell session, use [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   > [!NOTE]
   > <span data-ttu-id="de4a8-150">`Remove-Module`從目前的 PowerShell 會話移除模組，但不卸載模組或刪除模組的檔案。</span><span class="sxs-lookup"><span data-stu-id="de4a8-150">`Remove-Module` removes a module from the current PowerShell session, but doesn't uninstall the module or delete the module's files.</span></span>

## <a name="show-calendar-code-example"></a><span data-ttu-id="de4a8-151">顯示行事歷程序代碼範例</span><span class="sxs-lookup"><span data-stu-id="de4a8-151">Show-Calendar code example</span></span>

<span data-ttu-id="de4a8-152">下列範例是包含名為之單一函數的腳本模組 `Show-Calendar` 。</span><span class="sxs-lookup"><span data-stu-id="de4a8-152">The following example is a script module that contains a single function named `Show-Calendar`.</span></span> <span data-ttu-id="de4a8-153">此函式會顯示行事曆的視覺標記法。</span><span class="sxs-lookup"><span data-stu-id="de4a8-153">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="de4a8-154">此範例包含適用于概要、描述、參數值和程式碼的 PowerShell 說明字串。</span><span class="sxs-lookup"><span data-stu-id="de4a8-154">The sample contains the PowerShell Help strings for the synopsis, description, parameter values, and code.</span></span> <span data-ttu-id="de4a8-155">匯入模組時， `Export-ModuleMember` 命令會確保函式 `Show-Calendar` 會匯出為模組成員。</span><span class="sxs-lookup"><span data-stu-id="de4a8-155">When the module is imported, the `Export-ModuleMember` command ensures that the `Show-Calendar` function is exported as a module member.</span></span>

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
