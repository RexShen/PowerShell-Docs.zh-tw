---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: 584e36dbb6db251906dfbf4f700ced78f1cb6830
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203243"
---
# <span data-ttu-id="cbc0f-103">Get-Unique</span><span class="sxs-lookup"><span data-stu-id="cbc0f-103">Get-Unique</span></span>

## <span data-ttu-id="cbc0f-104">概要</span><span class="sxs-lookup"><span data-stu-id="cbc0f-104">SYNOPSIS</span></span>
<span data-ttu-id="cbc0f-105">從排序的清單中傳回唯一項目。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-105">Returns unique items from a sorted list.</span></span>

## <span data-ttu-id="cbc0f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cbc0f-106">SYNTAX</span></span>

### <span data-ttu-id="cbc0f-107">AsString (預設值)</span><span class="sxs-lookup"><span data-stu-id="cbc0f-107">AsString (Default)</span></span>

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### <span data-ttu-id="cbc0f-108">UniqueByType</span><span class="sxs-lookup"><span data-stu-id="cbc0f-108">UniqueByType</span></span>

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## <span data-ttu-id="cbc0f-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cbc0f-109">DESCRIPTION</span></span>

<span data-ttu-id="cbc0f-110">此 `Get-Unique` Cmdlet 會比較已排序清單中的每個專案與下一個專案、消除重複專案，並只傳回每個專案的一個實例。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-110">The `Get-Unique` cmdlet compares each item in a sorted list to the next item, eliminates duplicates, and returns only one instance of each item.</span></span> <span data-ttu-id="cbc0f-111">清單必須排序，此 Cmdlet 才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-111">The list must be sorted for the cmdlet to work properly.</span></span>

<span data-ttu-id="cbc0f-112">`Get-Unique` 會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-112">`Get-Unique` is case-sensitive.</span></span> <span data-ttu-id="cbc0f-113">因此，只有字元大小寫不同的字串會被視為唯一的字串。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-113">As a result, strings that differ only in character casing are considered to be unique.</span></span>

## <span data-ttu-id="cbc0f-114">範例</span><span class="sxs-lookup"><span data-stu-id="cbc0f-114">EXAMPLES</span></span>

### <span data-ttu-id="cbc0f-115">範例 1︰取得文字檔中的唯一文字</span><span class="sxs-lookup"><span data-stu-id="cbc0f-115">Example 1: Get unique words in a text file</span></span>

<span data-ttu-id="cbc0f-116">這些命令會尋找文字檔案中的唯一文字數目。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-116">These commands find the number of unique words in a text file.</span></span>

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

<span data-ttu-id="cbc0f-117">第一個命令會取得 File.txt 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-117">The first command gets the content of the File.txt file.</span></span> <span data-ttu-id="cbc0f-118">它會將每一行文字轉換成小寫字母，然後在空格 ("") 將每個字分割到不同行。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-118">It converts each line of text to lowercase letters and then splits each word onto a separate line at the space (" ").</span></span> <span data-ttu-id="cbc0f-119">然後，它會將產生的清單依字母順序排序 (預設) ，並使用 `Get-Unique` Cmdlet 來排除任何重複的字組。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-119">Then, it sorts the resulting list alphabetically (the default) and uses the `Get-Unique` cmdlet to eliminate any duplicate words.</span></span> <span data-ttu-id="cbc0f-120">結果會儲存在變數中 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-120">The results are stored in the `$A` variable.</span></span>

<span data-ttu-id="cbc0f-121">第二個命令會使用中字串集合的 **Count** 屬性 `$A` 來判斷中有多少個專案 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-121">The second command uses the **Count** property of the collection of strings in `$A` to determine how many items are in `$A`.</span></span>

### <span data-ttu-id="cbc0f-122">範例 2︰取得陣列中的唯一整數</span><span class="sxs-lookup"><span data-stu-id="cbc0f-122">Example 2: Get unique integers in an array</span></span>

<span data-ttu-id="cbc0f-123">此命令會尋找整數的集合的唯一成員。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-123">This command finds the unique members of the set of integers.</span></span>

```powershell
1,1,1,1,12,23,4,5,4643,5,3,3,3,3,3,3,3 | Sort-Object | Get-Unique
```

```Output
1
3
4
5
12
23
4643
```

<span data-ttu-id="cbc0f-124">第一個命令會接受在命令列中輸入的整數陣列，使用管線將它們傳送至 `Sort-Object` Cmdlet 進行排序，然後使用管線將它們傳送至 `Get-Unique` ，以消除重複的專案。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-124">The first command takes an array of integers typed at the command line, pipes them to the `Sort-Object` cmdlet to be sorted, and then pipes them to `Get-Unique`, which eliminates duplicate entries.</span></span>

### <span data-ttu-id="cbc0f-125">範例 3︰取得目錄中唯一的物件類型</span><span class="sxs-lookup"><span data-stu-id="cbc0f-125">Example 3: Get unique object types in a directory</span></span>

<span data-ttu-id="cbc0f-126">此命令會使用 `Get-ChildItem` Cmdlet 來抓取本機目錄的內容，其中包括檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-126">This command uses the `Get-ChildItem` cmdlet to retrieve the contents of the local directory, which includes files and directories.</span></span>

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

<span data-ttu-id="cbc0f-127">管線運算子 (|) 將結果傳送至 `Sort-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-127">The pipeline operator (|) sends the results to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="cbc0f-128">`$_.GetType()`語句會將 **GetType** 方法套用到每個檔案或目錄。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-128">The `$_.GetType()` statement applies the **GetType** method to each file or directory.</span></span> <span data-ttu-id="cbc0f-129">然後， `Sort-Object` 依類型排序專案。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-129">Then, `Sort-Object` sorts the items by type.</span></span> <span data-ttu-id="cbc0f-130">另一個管線運算子會將結果傳送至 `Get-Unique` 。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-130">Another pipeline operator sends the results to `Get-Unique`.</span></span> <span data-ttu-id="cbc0f-131">**OnType** 參數會指示 `Get-Unique` 每個類型只傳回一個物件。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-131">The **OnType** parameter directs `Get-Unique` to return only one object of each type.</span></span>

### <span data-ttu-id="cbc0f-132">範例 4︰取得唯一的處理程序</span><span class="sxs-lookup"><span data-stu-id="cbc0f-132">Example 4: Get unique processes</span></span>

<span data-ttu-id="cbc0f-133">此命令會取得電腦上執行之處理程序的名稱，並排除重複項目。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-133">This command gets the names of processes running on the computer with duplicates eliminated.</span></span>

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

<span data-ttu-id="cbc0f-134">此 `Get-Process` 命令會取得電腦上的所有處理常式。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-134">The `Get-Process` command gets all of the processes on the computer.</span></span> <span data-ttu-id="cbc0f-135">管線運算子 (|) 會將結果傳遞給 `Sort-Object` ，根據預設，ProcessName 會依字母順序排序處理常式。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-135">The pipeline operator (|) passes the result to `Sort-Object`, which, by default, sorts the processes alphabetically by ProcessName.</span></span> <span data-ttu-id="cbc0f-136">結果會透過管道傳送至 `Select-Object` Cmdlet，此 Cmdlet 只會選取每個物件的 ProcessName 屬性值。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-136">The results are piped to the `Select-Object` cmdlet, which selects only the values of the ProcessName property of each object.</span></span> <span data-ttu-id="cbc0f-137">結果接著會以管道傳送至 `Get-Unique` 來消除重複專案。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-137">The results are then piped to `Get-Unique` to eliminate duplicates.</span></span>

<span data-ttu-id="cbc0f-138">**AsString** 參數會指示 `Get-Unique` 將 **ProcessName** 值視為字串。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-138">The **AsString** parameter tells `Get-Unique` to treat the **ProcessName** values as strings.</span></span>
<span data-ttu-id="cbc0f-139">如果沒有這個參數，會 `Get-Unique` 將 **ProcessName** 值視為物件，並且只傳回物件的一個實例，也就是清單中的第一個進程名稱。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-139">Without this parameter, `Get-Unique` treats the **ProcessName** values as objects and returns only one instance of the object, that is, the first process name in the list.</span></span>

## <span data-ttu-id="cbc0f-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cbc0f-140">PARAMETERS</span></span>

### <span data-ttu-id="cbc0f-141">-AsString</span><span class="sxs-lookup"><span data-stu-id="cbc0f-141">-AsString</span></span>

<span data-ttu-id="cbc0f-142">指出此 Cmdlet 會使用資料做為字串。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-142">Indicates that this cmdlet uses the data as a string.</span></span> <span data-ttu-id="cbc0f-143">如果沒有這個參數，資料會被視為物件，因此當您將相同類型的物件集合提交到時（ `Get-Unique` 例如檔案集合），它只會傳回一個 (第一個) 。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-143">Without this parameter, data is treated as an object, so when you submit a collection of objects of the same type to `Get-Unique`, such as a collection of files, it returns just one (the first).</span></span> <span data-ttu-id="cbc0f-144">您可以使用此參數來尋找物件屬性的唯一值，例如檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-144">You can use this parameter to find the unique values of object properties, such as the file names.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cbc0f-145">-InputObject</span><span class="sxs-lookup"><span data-stu-id="cbc0f-145">-InputObject</span></span>

<span data-ttu-id="cbc0f-146">指定的輸入 `Get-Unique` 。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-146">Specifies input for `Get-Unique`.</span></span> <span data-ttu-id="cbc0f-147">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-147">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="cbc0f-148">此 Cmdlet 會將使用 **InputObject** 提交的輸入視為集合。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-148">This cmdlet treats the input submitted by using **InputObject** as a collection.</span></span> <span data-ttu-id="cbc0f-149">它不會列舉集合中的個別專案。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-149">it does not enumerate individual items in the collection.</span></span> <span data-ttu-id="cbc0f-150">由於集合為單一項目，因此使用 **InputObject** 提交的輸入一律會依原樣傳回。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-150">Because the collection is a single item, input submitted by using **InputObject** is always returned unchanged.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="cbc0f-151">-OnType</span><span class="sxs-lookup"><span data-stu-id="cbc0f-151">-OnType</span></span>

<span data-ttu-id="cbc0f-152">指出此 Cmdlet 只會針對每個類型傳回一個物件。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-152">Indicates that this cmdlet returns only one object of each type.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UniqueByType
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cbc0f-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cbc0f-153">CommonParameters</span></span>

<span data-ttu-id="cbc0f-154">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cbc0f-155">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cbc0f-156">輸入</span><span class="sxs-lookup"><span data-stu-id="cbc0f-156">INPUTS</span></span>

### <span data-ttu-id="cbc0f-157">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="cbc0f-157">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="cbc0f-158">您可以透過管道將任何類型的物件傳送至 `Get-Unique` 。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-158">You can pipe any type of object to `Get-Unique`.</span></span>

## <span data-ttu-id="cbc0f-159">輸出</span><span class="sxs-lookup"><span data-stu-id="cbc0f-159">OUTPUTS</span></span>

### <span data-ttu-id="cbc0f-160">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="cbc0f-160">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="cbc0f-161">傳回的物件類型 `Get-Unique` 取決於輸入。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-161">The type of object that `Get-Unique` returns is determined by the input.</span></span>

## <span data-ttu-id="cbc0f-162">注意</span><span class="sxs-lookup"><span data-stu-id="cbc0f-162">NOTES</span></span>

<span data-ttu-id="cbc0f-163">您也可以 `Get-Unique` 使用內建的別名來參考 `gu` 。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-163">You can also refer to `Get-Unique` by its built-in alias, `gu`.</span></span> <span data-ttu-id="cbc0f-164">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-164">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="cbc0f-165">如果要排序清單，請使用 Sort-Object。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-165">To sort a list, use Sort-Object.</span></span> <span data-ttu-id="cbc0f-166">您也可以使用的 **unique** 參數 `Sort-Object` 來尋找清單中的唯一專案。</span><span class="sxs-lookup"><span data-stu-id="cbc0f-166">You can also use the **Unique** parameter of `Sort-Object` to find the unique items in a list.</span></span>

## <span data-ttu-id="cbc0f-167">相關連結</span><span class="sxs-lookup"><span data-stu-id="cbc0f-167">RELATED LINKS</span></span>

[<span data-ttu-id="cbc0f-168">Select-Object</span><span class="sxs-lookup"><span data-stu-id="cbc0f-168">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="cbc0f-169">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="cbc0f-169">Sort-Object</span></span>](Sort-Object.md)
