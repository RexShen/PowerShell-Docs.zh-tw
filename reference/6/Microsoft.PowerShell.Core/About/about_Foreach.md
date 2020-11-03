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
# <a name="about-foreach"></a><span data-ttu-id="0f59f-104">關於 ForEach</span><span class="sxs-lookup"><span data-stu-id="0f59f-104">About ForEach</span></span>

## <a name="short-description"></a><span data-ttu-id="0f59f-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="0f59f-105">Short description</span></span>
<span data-ttu-id="0f59f-106">描述您可以用來跨越專案集合中所有專案的語言命令。</span><span class="sxs-lookup"><span data-stu-id="0f59f-106">Describes a language command you can use to traverse all the items in a collection of items.</span></span>

## <a name="long-description"></a><span data-ttu-id="0f59f-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="0f59f-107">Long description</span></span>

<span data-ttu-id="0f59f-108">`Foreach`語句 (也稱為 `Foreach` 迴圈) 是一種語言結構，可逐步執行)  (逐一查看專案集合中的一連串值。</span><span class="sxs-lookup"><span data-stu-id="0f59f-108">The `Foreach` statement (also known as a `Foreach` loop) is a language construct for stepping through (iterating) a series of values in a collection of items.</span></span>

<span data-ttu-id="0f59f-109">要進行往返的最簡單且最典型的集合類型是陣列。</span><span class="sxs-lookup"><span data-stu-id="0f59f-109">The simplest and most typical type of collection to traverse is an array.</span></span>
<span data-ttu-id="0f59f-110">在 `Foreach` 迴圈中，通常會針對陣列中的每個專案執行一或多個命令。</span><span class="sxs-lookup"><span data-stu-id="0f59f-110">Within a `Foreach` loop, it is common to run one or more commands against each item in an array.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f59f-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="0f59f-111">Syntax</span></span>

<span data-ttu-id="0f59f-112">以下顯示 `ForEach` 語法：</span><span class="sxs-lookup"><span data-stu-id="0f59f-112">The following shows the `ForEach` syntax:</span></span>

```
foreach ($<item> in $<collection>){<statement list>}
```

<span data-ttu-id="0f59f-113">以 `ForEach` 括弧括住的語句部分代表變數和要逐一查看的集合。</span><span class="sxs-lookup"><span data-stu-id="0f59f-113">The part of the `ForEach` statement enclosed in parenthesis represents a variable and a collection to iterate.</span></span> <span data-ttu-id="0f59f-114">`$<item>`當迴圈執行時，PowerShell 會自動建立變數 `Foreach` 。</span><span class="sxs-lookup"><span data-stu-id="0f59f-114">PowerShell creates the variable `$<item>` automatically when the `Foreach` loop runs.</span></span> <span data-ttu-id="0f59f-115">在迴圈之前的每個反復專案之前，變數會設定為集合中的值。</span><span class="sxs-lookup"><span data-stu-id="0f59f-115">Prior to each iteration through the loop, the variable is set to a value in the collection.</span></span>
<span data-ttu-id="0f59f-116">語句後面的區塊 `Foreach` `{<statement list>}` 包含一組命令，可針對集合中的每個專案執行。</span><span class="sxs-lookup"><span data-stu-id="0f59f-116">The block following a `Foreach` statement `{<statement list>}` contains a set of commands to execute against each item in a collection.</span></span>

### <a name="examples"></a><span data-ttu-id="0f59f-117">範例</span><span class="sxs-lookup"><span data-stu-id="0f59f-117">Examples</span></span>

<span data-ttu-id="0f59f-118">例如， `Foreach` 下列範例中的迴圈會顯示陣列中的值 `$letterArray` 。</span><span class="sxs-lookup"><span data-stu-id="0f59f-118">For example, the `Foreach` loop in the following example displays the values in the `$letterArray` array.</span></span>

```powershell
$letterArray = "a","b","c","d"
foreach ($letter in $letterArray)
{
  Write-Host $letter
}
```

<span data-ttu-id="0f59f-119">在此範例中， `$letterArray` 會使用字串值、、和來建立並初始化陣列 `"a"` `"b"` `"c"` `"d"` 。</span><span class="sxs-lookup"><span data-stu-id="0f59f-119">In this example, the `$letterArray` array is created and initialized with the string values `"a"`, `"b"`, `"c"`, and `"d"`.</span></span> <span data-ttu-id="0f59f-120">第一次 `Foreach` 執行語句時，它會將 `$letter` 變數設定為等於 () 中的第一個專案 `$letterArray` `"a"` 。</span><span class="sxs-lookup"><span data-stu-id="0f59f-120">The first time the `Foreach` statement runs, it sets the `$letter` variable equal to the first item in `$letterArray` (`"a"`).</span></span> <span data-ttu-id="0f59f-121">然後，它會使用 `Write-Host` Cmdlet 來顯示字母 a。</span><span class="sxs-lookup"><span data-stu-id="0f59f-121">Then, it uses the `Write-Host` cmdlet to display the letter a.</span></span> <span data-ttu-id="0f59f-122">下一次執行迴圈時， `$letter` 會設定為 `"b"` ，依此類推。</span><span class="sxs-lookup"><span data-stu-id="0f59f-122">The next time through the loop, `$letter` is set to `"b"`, and so on.</span></span> <span data-ttu-id="0f59f-123">在 `Foreach` 迴圈顯示字母 d 之後，PowerShell 就會結束迴圈。</span><span class="sxs-lookup"><span data-stu-id="0f59f-123">After the `Foreach` loop displays the letter d, PowerShell exits the loop.</span></span>

<span data-ttu-id="0f59f-124">整個 `Foreach` 語句必須出現在同一行上，才能在 PowerShell 命令提示字元中以命令的形式執行。</span><span class="sxs-lookup"><span data-stu-id="0f59f-124">The entire `Foreach` statement must appear on a single line to run it as a command at the PowerShell command prompt.</span></span> <span data-ttu-id="0f59f-125">`Foreach`如果您將命令放在 ps1 腳本檔案中，則整個語句不需要出現在同一行。</span><span class="sxs-lookup"><span data-stu-id="0f59f-125">The entire `Foreach` statement does not have to appear on a single line if you place the command in a .ps1 script file instead.</span></span>

<span data-ttu-id="0f59f-126">`Foreach` 語句也可以與傳回專案集合的 Cmdlet 一起使用。</span><span class="sxs-lookup"><span data-stu-id="0f59f-126">`Foreach` statements can also be used together with cmdlets that return a collection of items.</span></span> <span data-ttu-id="0f59f-127">在下列範例中，Foreach 語句會逐步執行 Cmdlet 所傳回的專案清單 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="0f59f-127">In the following example, the Foreach statement steps through the list of items that is returned by the `Get-ChildItem` cmdlet.</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  Write-Host $file
}
```

<span data-ttu-id="0f59f-128">您可以使用 `If` 語句來限制傳回的結果，以精簡範例。</span><span class="sxs-lookup"><span data-stu-id="0f59f-128">You can refine the example by using an `If` statement to limit the results that are returned.</span></span> <span data-ttu-id="0f59f-129">在下列範例中， `Foreach` 語句會執行與上一個範例相同的迴圈作業，但它會新增 `If` 語句，以將結果限制為大於 100 kb 的檔案 (KB) ：</span><span class="sxs-lookup"><span data-stu-id="0f59f-129">In the following example, the `Foreach` statement performs the same looping operation as the previous example, but it adds an `If` statement to limit the results to files that are greater than 100 kilobytes (KB):</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
  }
}
```

<span data-ttu-id="0f59f-130">在此範例中， `Foreach` 迴圈會使用變數的屬性 `$file` 來執行比較作業 (`$file.length -gt 100KB`) 。</span><span class="sxs-lookup"><span data-stu-id="0f59f-130">In this example, the `Foreach` loop uses a property of the `$file` variable to perform a comparison operation (`$file.length -gt 100KB`).</span></span> <span data-ttu-id="0f59f-131">`$file`變數包含 Cmdlet 所傳回之物件中的所有屬性 `Get-ChildItem` 。</span><span class="sxs-lookup"><span data-stu-id="0f59f-131">The `$file` variable contains all the properties in the object that is returned by the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="0f59f-132">因此，您不只可以傳回檔案名。</span><span class="sxs-lookup"><span data-stu-id="0f59f-132">Therefore, you can return more than just a file name.</span></span>
<span data-ttu-id="0f59f-133">在下一個範例中，PowerShell 會傳回語句清單內的長度和最後一個存取時間：</span><span class="sxs-lookup"><span data-stu-id="0f59f-133">In the next example, PowerShell returns the length and the last access time inside the statement list:</span></span>

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

<span data-ttu-id="0f59f-134">在此範例中，您不限於在語句清單中執行單一命令。</span><span class="sxs-lookup"><span data-stu-id="0f59f-134">In this example, you are not limited to running a single command in a statement list.</span></span>

<span data-ttu-id="0f59f-135">您也可以在迴圈外使用變數 `Foreach` ，並在迴圈內遞增變數。</span><span class="sxs-lookup"><span data-stu-id="0f59f-135">You can also use a variable outside a `Foreach` loop and increment the variable inside the loop.</span></span> <span data-ttu-id="0f59f-136">下列範例會計算大小超過 100 KB 的檔案：</span><span class="sxs-lookup"><span data-stu-id="0f59f-136">The following example counts files over 100 KB in size:</span></span>

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

<span data-ttu-id="0f59f-137">在上述範例中， `$i` 變數會設定為 `0` 迴圈外部，而變數會在每個找到大於 100 KB 之檔案的迴圈內遞增。</span><span class="sxs-lookup"><span data-stu-id="0f59f-137">In the preceding example, the `$i` variable is set to `0` outside the loop, and the variable is incremented inside the loop for each file that is found that is larger than 100 KB.</span></span> <span data-ttu-id="0f59f-138">當迴圈結束時， `If` 語句會評估的值， `$i` 以顯示超過 100 KB 的所有檔案計數。</span><span class="sxs-lookup"><span data-stu-id="0f59f-138">When the loop exits, an `If` statement evaluates the value of `$i` to display a count of all the files over 100 KB.</span></span> <span data-ttu-id="0f59f-139">或者，它會顯示一則訊息，指出找不到超過 100 KB 的檔案。</span><span class="sxs-lookup"><span data-stu-id="0f59f-139">Or, it displays a message stating that no files over 100 KB were found.</span></span>

<span data-ttu-id="0f59f-140">上述範例也會示範如何格式化檔案長度結果：</span><span class="sxs-lookup"><span data-stu-id="0f59f-140">The previous example also demonstrates how to format the file length results:</span></span>

```powershell
($file.length / 1024).ToString("F0")
```

<span data-ttu-id="0f59f-141">值除以1024可顯示以 kb 為單位的結果，而不是以位元組為單位，而產生的值則會使用固定點格式規範來格式化，以移除結果中的任何十進位值。</span><span class="sxs-lookup"><span data-stu-id="0f59f-141">The value is divided by 1,024 to show the results in kilobytes rather than bytes, and the resulting value is then formatted using the fixed-point format specifier to remove any decimal values from the result.</span></span> <span data-ttu-id="0f59f-142">0會使格式規範顯示沒有小數位數。</span><span class="sxs-lookup"><span data-stu-id="0f59f-142">The 0 makes the format specifier show no decimal places.</span></span>

<span data-ttu-id="0f59f-143">在下列範例中，函式定義了剖析 PowerShell 腳本和腳本模組，並傳回包含在內之函式的位置。</span><span class="sxs-lookup"><span data-stu-id="0f59f-143">In the following example, the function defined parses PowerShell scripts and script modules and returns the location of functions contained within.</span></span> <span data-ttu-id="0f59f-144">此範例示範如何使用 `MoveNext` 方法 (它的運作方式類似于 `skip X` `For` 迴圈) ，以及 `Current` `$foreach` foreach 腳本區塊內變數的屬性。</span><span class="sxs-lookup"><span data-stu-id="0f59f-144">The example demonstrates how to use the `MoveNext` method (which works similarly to `skip X` on a `For` loop) and the `Current` property of the `$foreach` variable inside of a foreach script block.</span></span> <span data-ttu-id="0f59f-145">即使跨多行的函式定義有異常或不一致，範例函式仍可以在腳本中找到函式。</span><span class="sxs-lookup"><span data-stu-id="0f59f-145">The example function can find functions in a script even if there are unusually- or inconsistently-spaced function definitions that span multiple lines.</span></span>

<span data-ttu-id="0f59f-146">如需詳細資訊，請參閱 [使用枚舉](about_Automatic_Variables.md#using-enumerators)器。</span><span class="sxs-lookup"><span data-stu-id="0f59f-146">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0f59f-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f59f-147">SEE ALSO</span></span>

[<span data-ttu-id="0f59f-148">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="0f59f-148">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="0f59f-149">about_If</span><span class="sxs-lookup"><span data-stu-id="0f59f-149">about_If</span></span>](about_If.md)

[<span data-ttu-id="0f59f-150">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="0f59f-150">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
